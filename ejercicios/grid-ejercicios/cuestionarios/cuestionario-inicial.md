1.

grid-template-columns: 1fr 1fr;
width: 200px;

Si una columna tiene contenido muy grande sin wrap, ¿qué pasa?

R/: para este caso, si el contenido de una de las 2 columnas con 1fr, supera los 200px de ancho, se desborda.



2. 
grid-template-columns: minmax(0, 1fr) 100px;
width: 100px;

¿Qué pasa con la primera columna?

R/: Colapsa y no tiene forma de crecer ni si quiera 1px de ancho,porque el total del espacio ya lo ocupó la segunda columna fija.


3. 
R/:
1fr siempre toma 1 parte, del total de espacio disponible. Si el total disponible que sobró son 100px, 1fr equivale a 10px;

En cambio minmax(0,1fr); en cierto modo puede colapsar. Esta medida se interpreta desde 0 hasta la fracción equivalente del espacio disponible. Tomando el mismo ejemplo anterior:
espacio disponible 100px, 1fr = 10px; por lo que el valor real que puede tomar la columna con minmax(0,1fr) es un número entre y 10px;


4. 
.grid {
  display: grid;
  grid-template-columns: auto 1fr auto;
  width: 300px;
}

primer auto = 250px
tercer auto = 100px


R/:
la segunda columna con 1fr quedaría con 0 de ancho. Porque ya ese el ancho total para las columnas del contendor grid, fue ocupado por el contenido de las 2 columnas auto. 250px + 100px = 350px. 
300px < 350px;



5:
B





👉 ¿Qué pasa aquí?

grid-template-columns: repeat(3, 1fr);
width: 300px;


Pero:

un item tiene una imagen de 500px sin max-width

¿Se respeta el 1fr o se rompe todo?



👉 qué pasa si metes 3 elementos en una fila pero solo defines 2 columnas 




👉 ¿qué diferencia hay entre overflow del item vs overflow del grid container?



-------------------------------------------


🧪 Ejercicio
.grid {
  display: grid;
  width: 300px;
  grid-template-columns: 100px 1fr 1fr;
}


El segundo item tiene contenido de 500px
No hay min-width: 0


❓ Preguntas

1.
¿Cuánto medirían idealmente las columnas?
R/: 100px;


2.
¿Qué columna se ve afectada por el contenido?
R/: La columna 2.






3.
¿Qué tipo de overflow ocurre y dónde?
R/: El overflow ocurre a nivel de contenido, se saldria del
flex-item, ya que el ancho total del contenedor grid es de 300px
 y el min-width auto de cada flex-item, haría que como mínimo la segunda 
 columna necesite 500px para colocar ahí el contenido. y la fracción
 es 100px. 100 pixelex < 500px.








4.
¿Se mantiene el reparto de fr o se rompe?
El reparto se mantiene porque al primer columna toma 100px de los 300px, quedando 
200px disponibles para asignaciones auto o fr. En este caso, se usan 2fr, y si suponemos
que solo hay 3 flex-items, entonces sería 100px de fr para la segunda y tercer columna, pero
 recordemos que hay overflow de contenido en la segunda columna por los 500px mínimos.


Promnt a ejecutar una vez se termine los pendientes
 ----------------------------


- Puedes explicarme el concepto de colapsar que aun no lo entiendo del todo en grid jajaja.


- Listo, vamos mejorando un poco. Explicame con detalle como funcionan estas 3 propiedades de grids:

grid-auto-columns
grid-auto-rows
grid-auto-flow
 


- Explicame el funcionamiento de auto-fill y auto-fit, hacen lo mismo? como se usa de manera profesiona y util?


Implementar una galeria de fotos aplicando correctamente auto-fill y atuo-fit
 
 
 -Entender como funciona:
    grid-row
    grid-row-start
    grid-row-end

    grid-columnsss
    grid-column-start
    grid-column-end
 
 ----------------------------


- Exlpicame como funciona la propiedad grid-auto-flow


- Como se comporta grid-template-columns: auto, cuando esa columna o el grid-item que irá en esa
columna ya tiene un ancho previamente definido?



---------------------------------
- Explicame como funciona el grid-area.

- Lo mismo que se hace con grid-column combinado con grid-row, se simplifica
con grid-area

---------------------------------


Luego revisemos esto que quedó pendiente:
Items que ocupan múltiples columnas (span)
min-content / max-content en conflictos reales
Grid dentro de Flexbox (y viceversa)



 - vale. Sigueme poniendo mas ejercicios. La idea es practicar, practicar y practicar hasta que me vuelva un crack. Vamos a ir desde casos puntuales para entender el concepto, sin importar como se vea el diseño y luego haremos un ejercicios avanzados implementando layouts de aplicaciones web reales.


---------------------
Terminar ejercicio del holy-grail-design del grid-area 


- Pedir explicación paso a paso del concepto grid-direction o dirección en grid-

- Pedir explicación del concepto subgrid

