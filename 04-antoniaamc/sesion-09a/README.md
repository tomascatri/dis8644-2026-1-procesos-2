# sesion-09a  
12 de Mayo (online🔥)

🔵 = necesita apoyo visual

---

# Primer bloque

## Atajos / Comandos

### Asignar valor a componente

* `V` → asignar/editar valor de un componente

Ejemplos:

* resistencia → `10k`
* capacitor → `100nF`
* integrado → nombre/valor correspondiente

---

### Asignar huellas a símbolos

* Herramienta: **Asignar huellas a símbolos** (*Assign Footprints*)

Función:

* vincula el símbolo esquemático con la huella física PCB correspondiente

Ejemplo:

* símbolo resistencia → huella `R_0805`
* símbolo ESP32 → huella específica del módulo

Importancia:

* sin huella asignada no se puede pasar correctamente al PCB

> símbolo = representación lógica
> huella = representación física en la placa

---

### Propiedades del símbolo

#### Datasheet

**Hoja de datos del componente (data sheet)**: sirve para revisar especificaciones, pinout, voltajes, dimensiones, recomendaciones de uso

Atajo:

* `E` → editar/revisar hoja de vida del componente

---

#### Huella del componente

Atajo:

* `F` → asignar o editar huella del componente

---

### Guardar proyecto

* `Ctrl + S`
* `Cmd + S` (mac)

---

### Duplicar

* `Cmd + D` → duplicar elemento/componente

Útil para:

* repetir resistencias
* copiar bloques
* acelerar diagramas repetitivos

---

### Visor de render 🔵

* `Alt + 3` → abrir visor de render

Función:

* visualizar la PCB en una vista renderizada/3D

Permite:

* revisar apariencia física  
* observar componentes montados  
* verificar orientación y distribución  
* previsualizar resultado final de la placa  

> *maqueta digital de la PCB*

---

# Problemas / Observaciones

## Problema: no aparecía el editor de placas

Situación:

Se abrió directamente el editor del esquemático (archivo correspondiente al schematic) y no aparecía el editor de placas PCB.

Importante:

El editor de placas es otro software/herramienta dentro de KiCad. Esquemático y PCB son módulos distintos

* **Editor esquemático** → conexiones lógicas/circuito
* **Editor de placas (PCB Editor)** → diseño físico de la placa

---

## Tamaño aproximado de placas 

* las placas PCB suelen ser pequeñas
* referencia vista en clase:

  (entrega 2) -> `10 x 10 cm` máximo

---

## Origen del plano / coordenadas 🔵

Origen del plano en: `(50, 50)` (referencia que dio Matías)

* sistema de plano cartesiano
* medidas en `mm`
* milímetros como unidad base
* comentario:

  * *es un software europeo → uso natural del sistema métrico*

---

## Ventana: Actualizar placa desde el esquemático 🔵

Sincroniza los cambios entre el esquemático y la PCB

* revisa conexiones
* actualiza componentes
* detecta diferencias o conflictos (“atados”)
* incorpora cambios nuevos del esquemático al PCB

Ejemplos:

* componentes sin huella
* conexiones faltantes
* cambios de nombre/valor
* componentes agregados o eliminados

> funciona como una especie de puente de sincronización entre lógica y placa

---

# Dibujar contornos

## Configuración inicial

* siempre partir definiendo las dimensiones de la grilla (5mm de referencia)

---

## Dibujar líneas 🔵

* usar la herramienta:

  * **dibujar líneas**

Importante: no confundir con otras herramientas similares, existen varias opciones parecidas en la interfaz.

---

## Capa `Edge.Cuts` 🔵

* trabajar las líneas en la capa:

  * `Edge.Cuts`

Función:

* define el contorno físico de la PCB
* indica por dónde se recorta/fabrica la placa

Observación:

* “se usa una vez”
* va a ser importante principalmente durante la definición inicial de la placa

---

## Redondear esquinas (`Edge.Cuts`) 🔵

* usar la herramienta:

  * **arco**

* mejor terminación física
* menos riesgo de daños
* bordes más suaves y seguros

> para evitar puntas filudas auch auch

---

## Ajuste de grilla según medidas 🔵

Mientras Matías revisa radios o medidas específicas va modificando la grilla para llegar exactamente a los números/medidas que quiere

> la grilla no es fija, se adapta según la necesidad del diseño

---

## Mover componentes sin seguir la grilla 🔵

* mientras se mueve un componente en el editor de placas:

  * mantener apretado `Ctrl`
  * o `Cmd` en Mac

Para desactivar temporalmente el “forzado a la rejilla” o mover componentes de forma más fluida/libre.

---

# Segundo bloque: capas del diseño  
Capas del diseño de la PCB

---

# Configuración de pistas

## Qué son las pistas

En PCB, las conexiones no se hacen con cables, se usan **pistas**.

**Pistas**: caminos conductores de cobre sobre la placa. Reemplazan los cables de los primeros circuitos.

> *“en vez de cables van a haber pistas”*

---

## Ancho de pistas 

* referencia comentada en clase:

  * `0.3 mm – 0.4 mm`

Observación:

* más de `0.3 mm` se considera un buen límite/base en muchos casos

Se revisa en pestaña de configuración de pistas

>  Herramienta “pinceles”

---

# Tips: diseño de placas

## Orden recomendado

1. primero ubicar los componentes que se quiere destacar visualmente
2. después organizar el resto según funcionamiento

---

| Parte de la PCB       | Prioridad principal                            | Enfoque                                                                |
| --------------------- | ---------------------------------------------- | ---------------------------------------------------------------------- |
| **Frontal** (`Front`) | estética, visualidad, composición              | cara visible/presentable del proyecto                                  |
| **Trasera** (`Back`)  | funcionamiento, conexiones, resolución técnica | eficiencia del circuito, trazado de pistas, uso del espacio disponible |


---

## Referencia mostrada por Matías 🔵

Proyecto de referencia:

* repositorio “phoskoto” de Matías en GitHub

---

# Capas de la PCB 🥪:

---

## Capa frontal y trasera 

Nombres comunes:

* `F.Cu` → cobre frontal
* `B.Cu` → cobre trasero

* las pistas pueden existir en ambos lados de la placa

---

## Serigrafía 

En KiCad se pueden agregar gráficos/serigrafías a la PCB en varios formatos, pero los más usados son:

| Formato                 | Uso                                        | Observaciones                                                     |
| ----------------------- | ------------------------------------------ | ----------------------------------------------------------------- |
| `SVG`                   | logos, ilustraciones, gráficos vectoriales | uno de los más cómodos para importar desde Illustrator o Inkscape |
| `DXF`                   | contornos, formas mecánicas, cortes        | muy usado para `Edge.Cuts` y geometrías precisas                  |
| `Bitmap / PNG / JPG`    | imágenes rasterizadas                      | KiCad las convierte a polígonos/vector al importar                |
| `Gerber`                | capas PCB ya preparadas                    | más profesional/fabricación, menos común para principiantes       |

---

## Herramientas relacionadas 

En KiCad existe:

* **Import Graphics**
* **Bitmap to Component / Bitmap Converter**

Permiten convertir imágenes a gráficos PCB y pasarlas a:

  * `F.SilkS`
  * `B.SilkS`
  * `Edge.Cuts`
  * otras capas

---

## Vías

Permiten conectar pistas entre distintas capas y pasar una conexión desde la cara frontal a la trasera.

---

## Colores de capas 🔵

* cada capa tiene un color distinto dentro de KiCad

Objetivo:

* diferenciar información visualmente
* reconocer rápidamente qué tipo de elemento se está viendo

Ejemplos posibles:

* rojo → capa frontal
* azul → capa trasera

---

# Routing (trazado de pistas)

Conectar eléctricamente los componentes mediante pistas siguiendo las conexiones definidas antes en el esquemático.

-> ***una mala distribución hace más difícil el routing***

---

## Relación entre ubicación y facilidad de conexión

Mientras mejor estén ubicados los componentes más fácil será conectar las pistas.

-> ***gran parte del trabajo PCB consiste en ordenar bien antes de empezar a rutear***


