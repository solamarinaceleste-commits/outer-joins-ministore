¿Por qué usaste LEFT JOIN para la Consulta 1 y no INNER JOIN? ¿Qué se perdería si usaras INNER JOIN?
Si hubiese usado INNER JOIN solo me traeria solo aquellas transacciones que estan en ambas tablas y no hubiese traido los productos sin ventas. Identificamos los productos con ID **108** ("Hub USB-C 7p") y **109** ("Parlante Bluetooth").

¿Por qué usaste RIGHT JOIN para la Consulta 2? ¿Qué tabla está a la izquierda y cuál a la derecha en tu consulta?
Usamos RIGHT JOIN porque queriamos ver todas las ventas (TABLA DERECHA) sin importar si tenia productos asociados o no (productos - TABLA IZQUIERDA) y detectamos la venta número **10**, la cual registra el `producto_id = 999`. Este ID de producto no existe en nuestra tabla de productos.

¿Qué representan los valores NULL en cada resultado? Explicá con un ejemplo concreto de los datos qué significa que venta_id sea NULL en la Consulta 1 y que producto_id de productos sea NULL en la Consulta 2.
¿Cuándo usarías FULL OUTER JOIN en un caso real de negocio?

NULL significa la ausencia de coincidencia entre la tabla de la izquierda y la tabla de la derecha. Que la venta_id sea NULL en la consulta 1 significa que no hay ventas para ese producto (Ejemplo concreto: El producto ID 108 ("Hub USB-C 7p") existe en el catálogo, pero al buscar sus ventas asociadas, el resultado arroja venta_id = NULL. Esto le indica al negocio que se trata de inventario estancado o sin demanda.) , y que el producto_id sea NULL quiere decir que no hay productos para esa venta (Ejemplo concreto: La venta ID 10 registra la compra del producto_id = 999. Como el código 999 no figura en la tabla de productos, las columnas del catálogo quedan en NULL. Esto alerta sobre un error de tipeo en la caja o una falla de integridad en la base de datos.)
FULL OUTER JOIN lo usuaria para ver todos los datos de dos tablas, por ejemplo para una auditoria. 
