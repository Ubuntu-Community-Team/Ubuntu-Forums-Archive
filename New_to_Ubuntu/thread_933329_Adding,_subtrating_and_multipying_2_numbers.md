---
title: "Adding, subtrating and multipying 2 numbers"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by spidex on 2008-09-29
I wanna create a script in Ubuntu. The script will ask user to input two numbers and display a choice of either to add , subtract or multiply the numbers.

If user choose Add, the two numbers will added and show result.
Maybe have to use Switch statement: S = subtract   A = Add   M = Multiply 

Can anyone help on how to start the script ?

Thank you.   :confused:

---

### Post by namegame on 2008-09-29
Well, you have a lot of choices here.

You could do it in Python or a Bash script.

Something like this would also be relatively easy to do in C or C++.

What we really need to know is what is your end goal here?

Are you learning a scripting language or is this a script that you need for daily use?

---

### Post by roquefilipe on 2008-09-29
Is it necessary to be a shell script? It seems to me that another language, suchas as python, might be more suitable. If you are lerning a new thing go for something with a litle more kick, in my opinion :)

---

### Post by LowSky on 2008-09-29
there is this cool tool called a calculator that can do all that you need. It's install by default.  :-({|=  :guitar:  :-\"


In all seriousness
[http://www.wonderhowto.com/how-to/video/how-to-create-a-calculator-script-in-c-162203/](http://www.wonderhowto.com/how-to/video/how-to-create-a-calculator-script-in-c-162203/)

---

### Post by spidex on 2008-09-29
Actually I have to do it Ubuntu script since my studies requires me to do it.
I am in learning process. I would appreciate if you guys could guide me:)

  

> **namegame said:**
> Well, you have a lot of choices here.

You could do it in Python or a Bash script.

Something like this would also be relatively easy to do in C or C++.

What we really need to know is what is your end goal here?

Are you learning a scripting language or is this a script that you need for daily use?

---

### Post by lazyart on 2008-09-29
ok, so you're asking for someone to do your homework?

A good place to start would be here: [http://www.linuxconfig.org/Bash_scripting_Tutorial](http://www.linuxconfig.org/Bash_scripting_Tutorial)

As for the answer... well, I wouldn't feel right giving it to you.

---

### Post by lazyart on 2008-09-29
oops.. double post.

---

### Post by mali2297 on 2008-09-29
Another useful site:
[http://linuxcommand.org/writing_shell_scripts.php](http://linuxcommand.org/writing_shell_scripts.php)

---

### Post by namegame on 2008-09-29
> **spidex said:**
> Actually I have to do it Ubuntu script since my studies requires me to do it.

To my knowledge. There is no such thing as an "Ubuntu script." I really think you mean Bash. Bash scripting is generally "cross-platform" between most Linux Distributions and Macs. 

However, my knowledge of Bash scripting is limited, so I could be wrong here.

You really don't want us to give you the answer because if we do, you will have gained nothing from the process.

---

### Post by ibuclaw on 2008-09-29
Why not Perl? :P

Anyway, there is an app called bc.

Here is the general jist of how it works
```
echo "2+2" | bc
```

If you wish to use floats, include "scale"
```
echo "scale=3; 100-(97/0.8753)" | bc
```
scale = 3 means to that number of decimal places.

Regards
Iain

---

### Post by James Little on 2008-09-29
This doesn't take care of the switch, but is an example of how you would add the integers:

#!/bin/bash
SUM=$(( $1 + $2 ))
echo $SUM

where $1 and $2 are the supplied command-line arguments. So say you save the above to a file called add.sh:
./add.sh 2 + 3 
will return 5. 

Have a look here: [http://www.tldp.org/LDP/abs/html/internal.html#EX36](http://www.tldp.org/LDP/abs/html/internal.html#EX36)
for clues on how to prompt for user for input (the keyword is 'read').

---

### Post by spidex on 2008-10-11
> **James Little said:**
> This doesn't take care of the switch, but is an example of how you would add the integers:

#!/bin/bash
SUM=$(( $1 + $2 ))
echo $SUM

where $1 and $2 are the supplied command-line arguments. So say you save the above to a file called add.sh:
./add.sh 2 + 3 
will return 5. 

Have a look here: [http://www.tldp.org/LDP/abs/html/internal.html#EX36](http://www.tldp.org/LDP/abs/html/internal.html#EX36)
for clues on how to prompt for user for input (the keyword is 'read').
Hi there,
I manage to almost complete my assignment using the script which requires adding, subtracting and multiplication. But I wanna add the DO..WHILE command in my script. My script should run until user press Q (to quit) the program.

Where should I insert the DO..WHILE command ?

Thanks

---

### Post by aeiah on 2008-10-11
you'd want to encase all of your script in the do while structure, i would think. because you want everything to be performable while 'q' isnt entered.

once you get that sorted, you should look at how to handle errors. what if i use a letter instead of a number? you should put something in there that will say "you didnt enter two numbers blah blah blah" this will make the script more robust, but first you'll have to do your while loop and put your subtract and multiply pieces in.

---

