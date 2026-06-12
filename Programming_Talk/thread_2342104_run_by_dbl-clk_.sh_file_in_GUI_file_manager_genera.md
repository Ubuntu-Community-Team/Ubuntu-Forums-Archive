---
title: "run by dbl-clk .sh file in GUI file manager generates weird errors"
date: 2016-11-03
forum: Programming Talk
---

### Post by pablogener on 2016-11-03
I have this script I've been working on for a while and when running it from command line, it works like a charm.
BUT...!
when I double-click it on the GUI file manager (as I would advice anyone I give the script to, to do), some errors arise.

I repeat: these errors never come up when I run from CLI with the "./<my-script-name>.sh" command.

for example, this code:
```

        ((cntImagenes++))

```

throws this error:
> 
/home/pablo/sh-scripts/monwha/monwha1.1.sh: 38: /home/pablo/sh-scripts/monwha/monwha1.1.sh: cntImagenes++: not found


this is easily worked around with:
```

cntImagenes=$((cntImagenes+1))

```

BUTTTTTTT!!!!
after I did that, further down the code, this:
```

while [ "$keepAdding" -eq 1 ]
    do
        cntImagenes=$((cntImagenes+1))

        nTitulo="Imagen n°$cntImagenes"
        filNarchivo=$(zenity --file-selection --title="$nTitulo")

        if [ "$filNarchivo" == "" ]; then         #THIS IS LINE 43
            keepAdding=0
        else
            echo "Cantidad de imagenes, hasta ahora:$cntImagenes"
            lstImagenes="$lstImagenes TRUE \"$filNarchivo\""        

#            lstImgsTotal[$cntImagenes]=$filNarchivo
#            echo "Imagen n°$cntImagenes:$filNarchivo"

        fi    
    done


```

throws this other error:
> 
/home/pablo/sh-scripts/monwha/monwha1.1.sh: 43: [: /home/pablo/sh-scripts/monwha/7D6.jpg: unexpected operator


I have no idea, if I keep trying 'workarounds' for every error I stumble upon, how far will all this come. I mean, I have a feeling that this will lead to more and more errors in an endless error-ridden spiral. I also feel there's some conceptual mistake that arouse that first error, and I should aim at fixing that 'conceptual' error which, in turn, may set everything "the right way" so that it runs just as smooth even from 'double-clicking' from the GUI file browser.

Any idea of what the #$%#$% is going on here?
Thanks in advance to the community for your dedication and time.

---

### Post by spjackson on 2016-11-04
It looks like you are missing the following as the first line of your script:
```

#!/bin/bash

```
because the errors you are getting suggest that sh (dash) not bash is interpreting your script.

---

### Post by pablogener on 2016-11-04
not quite. here, I'll past the complete code, you'll see I had included that:

```

#################################
#        MONWHA 1.1                #
#                                #
#        creado por Pablo Gener    #
#        (cc) 2016                #
#        pablogener@hotmail.com    #
#                                #
#################################

#!/bin/bash

cntImagenes=0
lstImagenes=""
lstImgsDefn=""
keepAdding=1

GREEN='\033[1;32m'
CELESTE='\033[1;34m'
RED='\033[1;31m'
NC='\033[0m' # No Color

printf "{$CELESTE}";

clear
echo "--------------------------------------------------------"
echo "MonWha 1.1"
echo ""
echo " creado por: Pablo Gener (cc) 2016. free software"
echo " pablogener@hotmail.com"
echo ""
echo "--------------------------------------------------------"
echo ""
echo "llamando al dialogo de selección de archivos. espere..."
#echo "keepAdding:" $keepAdding

while [ "$keepAdding" -eq 1 ]
    do
        ((cntImagenes++))

        nTitulo="Imagen n°$cntImagenes"
        filNarchivo=$(zenity --file-selection --title="$nTitulo")

        if [ "$filNarchivo" == "" ]; then
            keepAdding=0
        else
            echo "Cantidad de imagenes, hasta ahora:$cntImagenes"
            lstImagenes="$lstImagenes TRUE \"$filNarchivo\""        

#            lstImgsTotal[$cntImagenes]=$filNarchivo
#            echo "Imagen n°$cntImagenes:$filNarchivo"

        fi    
    done

((cntImagenes--))

if [ $cntImagenes -eq 0 ]; then
    printf "${RED}";    
    echo "MonWha panic! - no se seleccionó ninguna imagen para procesar"
    echo "Abortando el procedimiento"
    printf "${NC}";    
    echo "-------------------------------------------------------------"
    echo "fin."
    exit 99
fi

echo "--------------------------------------------"
echo "Se procesarán: $cntImagenes imagenes."

lstImgsDefn=$(zenity --list --text "Imágenes incluidas:" --checklist --column "Incluir" --column "Imagen" $lstImagenes --separator " ")

lstImgsDefn=$(echo $lstImgsDefn | tr -d \")

montage $lstImgsDefn -geometry 360x -tile 1x1 -border 5 result_360_%d.jpg

echo "--------------------------------------------"
echo "Se crearon todos los mosaicos"
echo ""
echo "--------------------------------------------"
echo "Se solicitan datos adicionales"
echo ""

txtTitulo=$(zenity --entry --title "Titulo descriptivo" --text "Ingrese un titulo para la imagen final:")
txtDesc=$(zenity --entry --title "Texto descriptivo" --text "Ingrese una breve descripción de la imagen final:")

echo $txtTitulo | convert -font FreeSans-Regular -pointsize 24 \
        -size 360x  -gravity Center  caption:@- \
        titulo.jpg
echo $txtDesc | convert -font FreeSans-Regular -pointsize 12 \
        -size 360x  -gravity West  caption:@- \
        descrip.jpg

convert titulo.jpg descrip.jpg result_360* -append final_result.jpg

printf "{$GREEN}";
echo "Exito!"
echo "--------------------------------------------"
echo "Procesamiento completo. Resultado en: final_result.jpg"

printf "{$CELESTE}";
zenity --question --text "Quiere abrir ahora el archivo de resultado?"
abrir=$?

if [ $abrir -ne 1 ]; then    
    echo "intenta abrir: final_result.jpg"    
    xdg-open final_result.jpg
fi

echo "--------------------------------------------"
echo "Intentando limpiar archivos temporales..."
rm titulo.jpg descrip.jpg
rm result_360*

echo "fin."
echo ;
echo "free software (cc) 2016 Pablo Gener pablogener@hotmail.com"
echo "----------------------------------------------------------"
printf "{$NC}";

```

keep up the good spirit!!

---

### Post by spjackson on 2016-11-04
```

#!/bin/bash

```
is on line 10. It needs to be the **first** line, as I said earlier.

---

### Post by pablogener on 2016-11-04
ooooooh ****!! ok.
I'll see to it that I never again make that mistake.

thanks so much!!

---

