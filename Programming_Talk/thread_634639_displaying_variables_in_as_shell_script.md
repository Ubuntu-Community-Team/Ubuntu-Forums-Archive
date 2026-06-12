---
title: "displaying variables in as shell script"
date: 2007-12-07
forum: Programming Talk
---

### Post by nickoli on 2007-12-07
I need to accept input for a program using read. The input prompted for is a pre-existing variable. The prompt asks for a variable to be inserted so that the program would then display the variables value. I need help. I can't figure out how to get the program to echo the value of the original variable instead of the value of the variable I used to capture input with the read command. The following is my script any help appreciated.
until [ "$*" = stop ]

do

echo "Enter 1 if you would you like to set a variable"

echo "Enter 2 if you would you like to check a variables value"

echo "Enter 3 if you would like to exit"

read dogbite

case $dogbite in

1 )



    echo "what variable would you like to set?"



    read var1



    echo "what would you like to set $var1 to?"



    read vars1



    echo "This is the variable you just created $var1 value is ${var1:=$vars1}";
;



2)



    echo "What variables value would you like displayed?"



    read input



    echo The value of $input is echo ${input} ;;



3)

   echo "GOODBYE"

   exit 0   



esac

done

---

### Post by mouseboyx on 2007-12-07
read changes the variable I don't think you can echo it in a previous state after it has been changed.

---

### Post by ghostdog74 on 2007-12-08
what you need is arrays
```

#!/bin/sh

c=0
while true
do
    clear
    cat << EOF
    1) set variable
    2) retrieve variable
    3) exit
EOF
    read choice
    case $choice in
    1)         
        printf "Enter value to set variable: " 
        read var1        
        echo "var1 is $var1"
        store[$c]=$var1
        c=$(( c + 1 ))
    ;;
    2) echo "I leave the retrieval of array values in store to you" ;;
    3) break;;
    *) continue
    esac
    echo "press to continue"
    read

done


```

---

