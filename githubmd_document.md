## Actividades

### Estilo y apariencia de Documentos HTML

“There are several options that control the appearance of HTML
documents:

`theme` specifies the Bootstrap theme to use for the page (themes are
drawn from the Bootswatch theme library). Valid themes include:
**default, bootstrap, cerulean, cosmo, darkly, flatly, journal, lumen,
paper, readable, sandstone, simplex, spacelab, united, and yeti**.
*(Pass null for no theme (in this case you can use the css parameter to
add your own styles))*.

`highlight` specifies the syntax highlighting style. Supported styles
include `default`, `tango`, `pygments`, `kate`, `monochrome`,
`espresso`, `zenburn`, `haddock`, `breezedark`, and `textmate`. *Pass
null to prevent syntax highlighting*.

`smart` indicates whether to produce typographically correct output,
converting straight quotes to curly quotes, `---` to em-dashes, `--` to
en-dashes, and `...` to ellipses. Note that `smart` is enabled by
default [^1].”

> “Otra forma de cambiar el aspecto y estilo del documento HTML es
> usando **cascading style sheets** *((hojas de estilo en cascada))*, o
> `CSS`”

### Crear un archivo CSS

Para crear un archivo CSS, ir a `File` → `New File` → `Text File`

> “Es un archivo simple con comandos de texto”

Se estarán creando **definiciones CSS**:

-   Se copia el texto indicado en la lección

<!-- -->

    #nextsteps{
      color: blue
    }

    .emphasized{
      font-size: 1.2em
    }

La opción `emphasized` hace el tamaño de la fuente más grande, en éste
caso la hace 1.2 veces más grande que la fuente estándar.

Se guarda el archivo dando un nombre, seguido de `.css`, en este caso
`micss.css`.

Regresando al archivo `Rmd`, se cambian las opciones de la cabecera YAML
quitando `theme` y `hightlight`, y se agrega la opción para el `CSS`:

    css: micss.css
    "recordando que se dejan 2 espacios"

Se aplican a las propiedades al encabezado agregando llaves seguido de
las opciones creadas en el CSS:
`### Estilo y apariencia de Documentos HTML {#nextsteps .emphisized}` y
se observa que toda la sección cambia de color y tamaño de letra.

### Definir tamaño de figuras para todo el documento HTML

Se elimina `CSS`en el encabezado YAML, y se agrega `fig_widht: 5` y
`fig_height: 5`.

``` r
plot(cars)
```

![](githubmd_document_files/figure-markdown_github/cars-1.png)

Las medidas estándar de las figuras son 7 de ancho y 5 de alto, medidas
están indicadas en pulgadas.

``` r
plot(airquality$Temp, airquality$Ozone,  
        main="Airquality: Ozone by Temperature") 
```

![](githubmd_document_files/figure-markdown_github/unnamed-chunk-1-1.png)

También se puede acceder a éstas opciones directamente dentro de
`Output Options...` a la derecha del engrane de `Knit`.

## Añadir Índice

-   Se agregan dos secciones más para verlas listadas en el índice.

-   Se puede agregar directamente en el encabezado YAML agregando la
    palabra clave `toc`, o en `Output Options...` dando click a la
    casilla de `Include table of contents`.

-   El encabezado se actualiza de forma automática agregando `toc: true`
    *(nótese que en el curso la salida es `toc: yes`)*

-   Para que el índice aparezca flotando a la izquierda, se agrega en
    YAML: `toc_float: true`

## Summary of Air Quality Dataset

This exercise will be working with the built-in `air quality`
dataset.[^2] This dataset contains 154 daily air quality measurements in
New York from May 1, 1973 (a Tuesday) to September 30, 1973. The dataset
contains 6 variables:

-   **Ozone**: *(Mean ozone in parts per billion (ppb) from 1300 to 1500
    hours at Roosevelt Island)*
-   **Solar.R**: *(Solar radiation in Langleys (lang) in the frequency
    band 4000–7700 Angstroms from 0800 to 1200 hours at Central Park)*
-   **Wind**: *(Average wind speed in miles per hour (mph) at 0700 and
    1000 hours at LaGuardia Airport)*
-   **Temp**: *(Maximum daily temperature in degrees Fahrenheit (oF) at
    LaGuardia Airport)*
-   **Month**: *(numeric month (1-12))*
-   **Day**: *(numeric Day of the month (1-31))*

### Table of Top of the Air Quality Dataset

``` r
knitr::kable(head(airquality), 
                      caption = "Top of the Air Quality Dataset") 
```

| Ozone | Solar.R | Wind | Temp | Month | Day |
|------:|--------:|-----:|-----:|------:|----:|
|    41 |     190 |  7.4 |   67 |     5 |   1 |
|    36 |     118 |  8.0 |   72 |     5 |   2 |
|    12 |     149 | 12.6 |   74 |     5 |   3 |
|    18 |     313 | 11.5 |   62 |     5 |   4 |
|    NA |      NA | 14.3 |   56 |     5 |   5 |
|    28 |      NA | 14.9 |   66 |     5 |   6 |

Top of the Air Quality Dataset

### Plot of Ozone by Temperature –Air Quality Dataset

``` r
plot(airquality$Temp, airquality$Ozone,  
        main="Airquality: Ozone by Temperature") 
```

![](githubmd_document_files/figure-markdown_github/unnamed-chunk-3-1.png)

## Plegado de código

Opción para ocultar o mostrar código en el documento, a menos que el
lector de click al botón resultante para mostrar el código. En la parte
superior de la página, aparece un botón `Code`, que indica si se desea
**Show All Code ** o **Hide All Code**.

***NOTA***: Si dentro de la sección de código aparece `echo=FALSE`, la
sección de código nunca se mostrará, aunque se utilice la opción de
plegado de código.

### Mantener un documento Markdown

Mantener un documento R Markdown se agrega en la cabecera YAML
`keep_md: true`

En los documentos obtenidos al compilar, además del llamado
*html_document.Rmd* y *el html_document.html*, se obtiene uno llamado
**html_document.md**. *“GitHub fue construído de forma nativa para
mostrar documentos Markdown”*

### Guardar el documento actual HTML en otro nombre de archivo

Dar click en `File` → `Save As..` → Cambiar nombre del documento a
`githubmd_document.Rmd` *(Se está creando un documento GitHub Markdown)*
→ `Guardar`.

Se regresa a la cabecera YAML: En vez de un documento HTML se va a
utilizar un documento md, para un documento markdown y específicamente
crear una variante de GitHub.

      md_document: 
        variant: markdown_github

[^1]: Texto tomado de:
    <https://bookdown.org/yihui/rmarkdown/html-document.html#appearance-and-style>

[^2]:  Chambers, J. M., Cleveland, W. S., Kleiner, B. and Tukey, P. A.
    (1983) Graphical Methods for Data Analysis. Belmont, CA: Wadsworth.
