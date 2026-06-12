---
title: "'tput col' number changes in bash script"
date: 2014-06-19
forum: Programming Talk
---

### Post by octius4u on 2014-06-19
**Why is the "tput col" number changing while running bash script in terminal emulator?**

I seem to have run into new situation and I'm hoping someone can explain this to me please.

I know it can change if I increase or decrease the terminal emulator via mouse for example. 
However i notices that the number changes to 80 no matter if I'm in terminator or xfce4-terminal 
and only after a redirect to a file such as when i make copies of stderr.  Why exactly 80 and not 86, 107 etc.
I'm using Xubuntu 14.04 on a 1920x1080 resolution.

In the script I wish to output a space in the amount of "tput col" and it outputs only 80 which troughs of the beginning of a new line. 
like in this function

```

#!/bin/bash
function Check_AccuracYN {              # 06 - SIX                              ## 
##################################################################################
# Correct order is FIRST [$1 = Y/N Answer] and SECOND [ $2 = Question]
AccuracyAnswer=""; AccuracyAnswer="$1"
AccuracyQuestion=""; AccuracyQuestion="$2"

if  [[ "$AccuracyAnswer" != [y/n] ]]; then echo "a"; echo "b"; fi
while [[ "$AccuracyAnswer" != [y/n] ]]; do
    echo -e "\e[2A$WrongInput"
    MaxRowLengh=$(tput cols) && printf '%0.s ' $(seq 1 $MaxRowLengh)
    echo -en "\e[1A$AccuracyQuestion"; read AccuracyAnswer
done
##################################################################################
};


```
The goal would be not to create a endless amount of additional lines with repeated error messages.
By the way this code does work properly when tested by it self.

Thanks for your help.

---

### Post by octius4u on 2014-06-19
Before starting the script "tput col" does show the correct amount of columns, 
but in the script it changes at the point of the first redirect. And after exiting 
the script "tput col" shoes the correct number again. Could 80 columns be the 
standard amount in a (text) file?

---

### Post by Vaphell on 2014-06-19
[http://programmers.stackexchange.com/questions/148677/why-is-80-characters-the-standard-limit-for-code-width](http://programmers.stackexchange.com/questions/148677/why-is-80-characters-the-standard-limit-for-code-width)

punchcards had 80 cols, then teletypes went with the same number, then video terminals did the same, then terminal emulators we use today followed. Long story short you could say 80 is the default value because legacy. When you redirect, the physical window with modified dimensions is not the target so it's not in the picture and fallback to the default occurs.

---

### Post by octius4u on 2014-06-19
Thanks for the info Vaphell. I will take some time to get more familiar with the subject. 
And I will also have to find an different way to measure the windows width or column number.
Especially when one could maximize the windows while the script is active. 
In that case a variable value number could became incorrect.

---

### Post by Vaphell on 2014-06-19
what problem are you trying to solve exactly?

---

### Post by octius4u on 2014-06-19
It's good to know one can count on Vaphell/UbuntuForums. Thanks for the explanation and for your offer. 
However I am glad to inform that I've managed to solve my problem.
I guess a good nights rest, gives the brain ideas. 

This is the method I used to solve my problem, without using 'tput col' at all, and the result is
just right.
```
function Check_AccuracYN {              # 06 - SIX                              ##
##################################################################################
# Correct order is FIRST [$1 = Y/N Answer] and SECOND [ $2 = Question]
AccuracyAnswer=""; AccuracyAnswer="$1"
AccuracyQuestion=""; AccuracyQuestion="$2"
if  [[ "$AccuracyAnswer" != [y/n] ]]; then echo ""; echo ""; fi
while [[ "$AccuracyAnswer" != [y/n] ]]; do
    echo -e "\e[2A$WrongInput"
    MaxLengh=$((${#AccuracyAnswer}+${#AccuracyQuestion}+2)); printf '%0.s ' $(seq 1 $MaxLengh)
    echo -en "\r$AccuracyQuestion"; read AccuracyAnswer
done
##################################################################################
};
```

---

### Post by Vaphell on 2014-06-20
btw, instead of using lame *seq* you can go with

```
printf '%*s' $MaxLength 
```

---

