---
title: "How to use loop with if statement"
date: 2013-10-28
forum: New to Ubuntu
---

### Post by Taati_Barao on 2013-10-28
Hi expert

I had successfully wrote simple script that calculate some values

```
shirt=15
black=13.50


echo "how many shirt you want"
read num
echo
echo "Please enter a choice"
echo "1 ---> normal shirt"
echo "2 ---> black shirt"
read choice
echo


if [ $choice = "1" ]; then
    price=`expr $num1 \* $shirt`
    echo "$num1 * $shirt = $price"


elif [ $choice = "2" ]; then
    answer=$(bc <<< "scale=2;$num*$black")
    echo "$num * $black = $answer"
else 
    echo "Invalid option"
fi
```

My Questions is how can i use loop to repeat the code five times when excute in the terminal, or any other way to do this is much more appreciated

Sorry for my poor english

---

### Post by sudodus on 2013-10-28
You can use a for-loop

from man bash:

       ```
for name [ in word ] ; do list ; done
              The list of words following in is expanded, generating a list of
              items.  The variable name is set to each element of this list in
              turn,  and  list is executed each time.  If the in word is omit&#8208;
              ted, the for command executes  list  once  for  each  positional
              parameter that is set (see PARAMETERS below).  The return status
              is the exit status of the last command that  executes.   If  the
              expansion of the items following in results in an empty list, no
              commands are executed, and the return status is 0.

       for (( expr1 ; expr2 ; expr3 )) ; do list ; done
              First, the arithmetic expression expr1 is evaluated according to
              the  rules  described  below  under  ARITHMETIC EVALUATION.  The
              arithmetic expression expr2 is then evaluated  repeatedly  until
              it  evaluates  to zero.  Each time expr2 evaluates to a non-zero
              value, list is executed and the arithmetic expression  expr3  is
              evaluated.   If  any  expression is omitted, it behaves as if it
              evaluates to 1.  The return value is the exit status of the last
              command in list that is executed, or false if any of the expres&#8208;
              sions is invalid.

```
ex.
```
for i in *.txt;do echo textfiler: $i;done

for (( i=1; i<=20 ; i++ )) ; do echo $i;done

for i in *.TXT;do mv $i ${i/\.TXT/}.txt; done  # "move *.TXT *.txt"
```

You can also use a while-loop.
```

help while
```
```
while: while COMMANDS; do COMMANDS; done
    Execute commands as long as a test succeeds.
    
    Expand and execute COMMANDS as long as the final command in the
    `while' COMMANDS has an exit status of zero.
    
    Exit Status:
    Returns the status of the last command executed.

```

---

### Post by Taati_Barao on 2013-10-28
Thanks for the quick reply, as im a beginer in linux could you please help me to explain in details or give examples on where to start on using "for loop"  to make my script repeated to excuted five times (5x) or more.

Thanks 

Taati

---

### Post by sudodus on 2013-10-28
If you know the number to repeat (have a variable[FONT=courier new]** iloop**[/FONT] with the value), use it like this
```
for (( i=1; i<=iloop ; i++ )) ; do echo $i;done
```

---

### Post by Taati_Barao on 2013-10-28
Hi Sudodus

Thank you for giving me the idea, it really helped

Taati

---

