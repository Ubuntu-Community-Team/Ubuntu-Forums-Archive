---
title: "How can I get input from terminal?"
date: 2009-09-13
forum: Programming Talk
---

### Post by aytacd on 2009-09-13
hi,

I'm new to ubuntu, I have a freesurfer command which I run in terminal as bellow.

mkanalysis-sess.new -a rtopy -TR 2 -designtype retinotopy -paradigm rtopy.par -funcstem fmcsm5 -ncycles 16

My problem is the last number(16) is a variable. I want to ask user to enter this parameter and directly put this incoming variable at the end of the command and execute it. Any ideas about how canI do this in a script?

Thank you for your help...

---

### Post by linkmaster03 on 2009-09-13
You could add the following line to ~/.bashrc:
```
alias cycles='mkanalysis-sess.new -a rtopy -TR 2 -designtype retinotopy -paradigm rtopy.par -funcstem fmcsm5 -ncycles $1'

```

And then you could just type, in a bash session, "cycles 16" or however many you want, and it will run. (restart terminal or type `source ~/.bashrc` first)

---

### Post by jpkotta on 2009-09-14
> **linkmaster03 said:**
> You could add the following line to ~/.bashrc:
```
alias cycles='mkanalysis-sess.new -a rtopy -TR 2 -designtype retinotopy -paradigm rtopy.par -funcstem fmcsm5 -ncycles $1'

```

And then you could just type, in a bash session, "cycles 16" or however many you want, and it will run. (restart terminal or type `source ~/.bashrc` first)

You sure about that?  Aliases don't take arguments.  It will work, but only because -ncycles is the last option and $1 is unbound.  What aliases do is a strict substitution of whatever the alias is.  There isn't any shell expansion.

---

### Post by geirha on 2009-09-14
You could make a function (in ~/.bashrc)
```

cycles() {
  local ncycles=$1
  (($#)) || read -p "How many cycles? " ncycles
  mkanalysis-sess.new -a rtopy -TR 2 -designtype retinotopy -paradigm rtopy.par -funcstem fmcsm5 -ncycles $ncycles
}

```
You can run it with either the number of cycles as argument, or, if there's no arguments, it will ask the user to input it.
```
$ cycles 16
# or
$ cycles
How many cycles? 16

```

---

### Post by aytacd on 2009-09-14
I tried that algorithm, but terminal gave 

" Badly placed ()'s. "  error. I couldn't solve this problem, any ideas?

---

### Post by geirha on 2009-09-14
You are using tcsh? that shell has a completely different syntax than the default shell (bash) in Ubuntu. I'm afraid I can't help you with tcsh.

---

### Post by aytacd on 2009-09-14
Actually I'm using bash, but when I run the algorithm which you had written before, error message appear.. :(

---

### Post by geirha on 2009-09-14
Well, as far as I can tell, that is not an error message given by bash. What bash version are you running though?
```
echo $BASH_VERSION
```

---

### Post by aytacd on 2009-09-14
When I try the command you said,

meltem-laptop:~> echo $BASH_VERSION
BASH_VERSION: Undefined variable.
 
this message appeared.

I confused about that. Ithink it will be more understandable if I post the complete script. 


```

#!/bin/bash

setenv FREESURFER_HOME /usr/local/freesurfer
source $FREESURFER_HOME/SetUpFreeSurfer.csh


cd /usr/local/freesurfer/subjects/retinotopy

cycles() {
  local ncycles=$1
  (($#)) || read -p "How many cycles? " ncycles
  mkanalysis-sess.new -a rtopy -TR 2 -designtype retinotopy -paradigm rtopy.par -funcstem fmcsm5 -ncycles $ncycles
}


preproc-sess -s SUBJ1 -fwhm 5


```


By the way, I saw a command as argv. But I can't able to use it.

I seriously need help about this...
[B][URL="http://www.mail-archive.com/freebsd-questions@freebsd.org/msg00406.html"]
[/URL][/B]

---

### Post by geirha on 2009-09-14
All versions of bash sets the $BASH_VERSION variable, so you're definately not using bash as your interactive shell. The following may help you identify what shell you are using

```

# The SHELL variable may be set to the shell you're using
echo $SHELL

# In posix shells, $$ will expand to the shell's pid, so running this command in
# the interactive shell, will show process information about it, if it expands $$.
ps -fp $$ 

# This will show you the entry for your user in /etc/passwd. The last field of the
# line is your default shell.
getent passwd $USER

```

---

### Post by linkmaster03 on 2009-09-14
> **jpkotta said:**
> You sure about that?  Aliases don't take arguments.  It will work, but only because -ncycles is the last option and $1 is unbound.  What aliases do is a strict substitution of whatever the alias is.  There isn't any shell expansion.

Ah yes, you are correct. I always forget that.

---

### Post by falconindy on 2009-09-14
> **jpkotta said:**
> You sure about that?  Aliases don't take arguments.  It will work, but only because -ncycles is the last option and $1 is unbound.  What aliases do is a strict substitution of whatever the alias is.  There isn't any shell expansion.
Sorry but I don't buy that. I use the following alias (bash) and it works as intended:
```
man2pdf() {
    if [ -z $1 ]; then
        echo "USAGE: man2pdf [manpage]"
    else
        if [ `find /usr/share/man -name $1\* | wc -l` -gt 0 ]; then
            out=/tmp/$1.pdf
            if [ ! -e $out ]; then
                man -t $1 | ps2pdf - > $out
            fi
            if [ -e $out ]; then
                /usr/bin/evince $out
            fi
        else
            echo "ERROR: manpage \"$1\" not found."
        fi
    fi
}
```Omitting an argument prints the usage message. Maybe I'm misunderstanding your explanation.

---

### Post by linkmaster03 on 2009-09-14
falconindy: What you pasted is a function. jpkotta is referring to aliases, defined by "alias <name>='<command>'".

---

### Post by falconindy on 2009-09-14
> **linkmaster03 said:**
> falconindy: What you pasted is a function. jpkotta is referring to aliases, defined by "alias <name>='<command>'".
Silly me. I should have known that.

---

### Post by aytacd on 2009-09-15
I'm totally lost. Tried the last one but still getting bracket error's can someone explain the algorithm to me in a easy way maybe i can modify the code? 
By the way one of my friends send me something like this: 
```

#!/bin/bash

echo "First Number"
echo $1
echo "Second Number"
echo $2
echo "number of the totals"
let result=$1+$2
echo $result
echo
# -------------------------- #
echo -n "Enter another value: "
read var
echo "\"var\" = "$var""
# IS IT OK?
```

ubuntu doesnot take sonuc as a variable.. 
Is it possible to modify this code to enter the number to the end of a string?

---

