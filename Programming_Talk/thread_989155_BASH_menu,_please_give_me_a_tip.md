---
title: "BASH menu, please give me a tip"
date: 2008-11-21
forum: Programming Talk
---

### Post by La muerte del DIos on 2008-11-21
Hello, i'm trying to create a menu in a script for BASH for selecting a customize Shell or the default one. Actually i've already got the menu, the thing is i want the changes to stick on the shell even after finishing the script (for it to actually work). Here's an example of the script:

```
#!/bin/bash

echo Por favor, seleccione una opción del menú

showMenu () {
echo "1) Utilizar la Shell personalizada"
echo "2) Nada"
echo "3) Salir"
}

while [ 1 ]

do

showMenu
read NUMERO
case "$NUMERO" in

"1")
PS1=prueba
alias crear=mkdir   
echo "MKDIR es ahora crear"
exit
;;

"2")
echo "Prueba"
exit
;;

"3")
exit
;;
esac
done
```

So when you select option one the prompt should change to "prueba" and mkdir should become "crear" but after selecting the option and quitting the script everything returns to default, so the script becomes useless. Maybe i need to change the bashrc file. Can you give me a hint? Thanks.

---

### Post by yota on 2008-11-21
Hi,

if you desire to retain the environment changes performed by the script you have to "source" it instead of executing it, i.e.:
```

source script.sh
or
. ./script.sh

```

hope this helps!

---

### Post by La muerte del DIos on 2008-11-21
Worked perfectly, thank you very much. I just added a final touch, instead of the exit i used return in each case.

---

