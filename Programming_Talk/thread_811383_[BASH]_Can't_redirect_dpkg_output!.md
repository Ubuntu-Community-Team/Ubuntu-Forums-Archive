---
title: "[BASH] Can't redirect dpkg output?!?"
date: 2008-05-29
forum: Programming Talk
---

### Post by Vhann on 2008-05-29
Hi all,

Here's my problem:
I was writing a BASH script which would accept an input from the user and then would lists all unsatisfied dependencies for the package given as input. To do so, I used the `dpkg` command. Surprisingly, I haven't been able to redirect the output of the `dpkg` command. Here's what I tried so far:

l'utilisateur saisit un nom de paquetage pour s'avoir quels paquetages sont à installer (bref, toutes les dépendances du paquetage qui ne sont pas satisfaites). Le script fait appel à dpkg pour connaître l'état des paquetages (je fais ce script sous Debian-based).

Toutefois, les commandes suivantes ne fonctionnent pas (du moins, elles n'ont pas l'effet désiré):

test=`dpkg -s aaa` #This outputs the result and test is set to nothing :(
dpkg -s aaa > test.txt #This outputs the result and creates a test.txt... empty file :S
test=$( dpkg -s aaa ) #Same as the first one
dpkg -s aaa | grep aaa #The pipe is purely and simply ignored, all lines are output.

This is quite strange since I can do a
"test=`uname -r` && echo $test" which does what I expect...

Thank you for your attention.
Regards,
Vhann.

---

### Post by slavik on 2008-05-29
try this:

```

dpkg -s aaa 2> test.txt

```

---

### Post by geirha on 2008-05-29
There are two output streams a program can use; stdout and stderr. stdout is the default one and is the one that is caught when you do $(prog) or `prog`. stderr is usually used to print error messages, but programmers are free to use it to whatever they want. To catch stderr to a file you use 2> as slavik showed, or if you want to put it in a variable, you can redirect stderr(2) to stdout(1):
```

test=$(dpkg -s aaa 2>&1)

```

---

### Post by Vhann on 2008-05-29
<Sorry, double post>

---

### Post by Vhann on 2008-05-29
Thank you both guys.

The command geirha wrote does exactly what I wanted (although it is weird :lol: ).

Thank you for your attention.
Regards,
Vhann.

---

