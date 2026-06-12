---
title: "sh scripts problem"
date: 2008-12-02
forum: Programming Talk
---

### Post by mannylarson on 2008-12-02
I am trying to run a sh script on my laptop; however, I get a:```
manny@ubuntu:~/Code/ch05$ sh menu.sh
menu test program
menu.sh: 30: Syntax error: end of file unexpected (expecting "do")

``` the sh script is:```
#!/bin/sh

echo menu test program

stop=0                     # reset loop termination flag.

while test $stop -eq 0     # loop until done.

do

 cat << ENDOFMENU             # display menu.

 1   : print the date.

 2, 3: print the current working directory.

 4   : exit

ENDOFMENU

 echo

 echo 'your choice? \c'     # prompt.

 read reply                  # read response.

 echo

 case $reply in              # process response.

   "1")

     date                    # display date.

     ;;

   "2"|"3")

     pwd                     # display working directory.

     ;;

   "4")

     stop=1                  # set loop termination flag.

     ;;

   *)                        # default.

     echo illegal choice     # error.

     ;;

 esac

done
``` 

I did run this sh script with no problem on my Desktop
Can this be a problem with the laptop AMD chip?
(My Desktop is an Intel chip)

On chat, I was been told I did not have everything needed to
run the script;then I was told this was not true

Also, I was told to try "/j #Bash" which I am not familiar 
with nor could find in the Ubuntu Documentation


Manny

---

### Post by mssever on 2008-12-02
Your script works for me with both bash and sh. Your problem has nothing to do with the brand of your processor. Either you didn't copy it across accurately, or something is screwy with your system. I suspect the former.

---

### Post by Sorivenul on 2008-12-02
Works fine for me.
Copied it to a file named MenuTest on my desktop, opened a terminal, made it executable, ran it with "./MenuTest", no issues.
I agree with mssever.

---

### Post by geirha on 2008-12-02
> **mannylarson said:**
> I am trying to run a sh script on my laptop; however, I get a:```
manny@ubuntu:~/Code/ch05$ sh menu.sh
menu test program
menu.sh: 30: Syntax error: end of file unexpected (expecting "do")

```

Make sure that there's a "do" immediately following the while-line, and a corresponding done at the end. I'm guessing you might have accidentally commented out the do and done lines (because I get the exact same error message if I do that).

> **mannylarson said:**
> 
Also, I was told to try "/j #Bash" which I am not familiar 
with nor could find in the Ubuntu Documentation

That's an IRC command to join the channel called #bash.

---

