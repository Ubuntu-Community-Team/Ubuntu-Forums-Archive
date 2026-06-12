---
title: "tcsh help"
date: 2008-08-06
forum: Programming Talk
---

### Post by GammaPoint on 2008-08-06
Hey, so I'm working on some code that my research group has been using (I'm rewriting the example for new users). Anyway, the last person who wrote it has a tcsh script where they have lines like

```
set NA = `calc $SCALF * 3`
``` 

But 'calc' isn't defined for me. Presumably it's one of their aliases. I could simply edit my alias (I use BASH, not tcsh). But I want it to work for all users without them having to edit their .bashrc (or equivalent) file. 

I thought I might do something with python since I already have a python script running in that directory. To my python script I wanted to add the option that if the second command line argument was 'calc' then it would multiply the numbers following it together and give back the result. This is easy to program in python, but I don't know how to call it from within the tcsh script to set the variable.

I have tried the following:
```

set NION = `python mult.py calc 4 5`
echo $NION

```

as an example, but the variable is empty. Anyone know what I am doing wrong or how I can easily multiply numbers together within tcsh without using the python script?  Thanks for your help!

---

### Post by mssever on 2008-08-06
I don't use tcsh (I use a real shell :)), but this seems to be quite simple. Drop a script called calc in the user's path, and make that script do what's expected. You can write that script in any language you like, and it will work from all shells.

---

### Post by GammaPoint on 2008-08-06
Hmm, maybe I don't know what you're saying. I made the python script mult.py an executable (by adding '#! /usr/bin/python' to the front and changing the permissions). I then tried 

```
set NION = `./mult.py calc 4 5`
```

but still nothing.  Is there something else you meant?

---

### Post by mssever on 2008-08-06
> **GammaPoint said:**
> Hmm, maybe I don't know what you're saying. I made the python script mult.py an executable (by adding '#! /usr/bin/python' to the front and changing the permissions). I then tried 

```
set NION = `./mult.py calc 4 5`
```but still nothing.  Is there something else you meant?If you run mult.py calc 4 5 from the command line, does it print the correct result to stdout? If not, you have a bug in that script. If it prints correctly, check that you're calling it correctly from tcsh (i.e., is the script always in the current directory when you run your tcsh script? Your snippet is assuming that this is true.).

EDIT: If you put the script somewhere in your $PATH, then you can call it without having to specify a directory.

---

### Post by ghostdog74 on 2008-08-06
you can also rewrite the tcsh script with python(or others).

---

### Post by GammaPoint on 2008-08-06
> **mssever said:**
> If you run mult.py calc 4 5 from the command line, does it print the correct result to stdout? If not, you have a bug in that script. If it prints correctly, check that you're calling it correctly from tcsh (i.e., is the script always in the current directory when you run your tcsh script? Your snippet is assuming that this is true.).

EDIT: If you put the script somewhere in your $PATH, then you can call it without having to specify a directory.


Yeah, it works correctly from the command line and the script is always in the current directory... :confused:

[QUOTE=ghostdog74]you can also rewrite the tcsh script with python(or others).[/QUOTE]

Yeah, I could rewrite the tcsh script, except that it's fairly long and complicated and it interfaces with a code that I'm going to be upgrading in the next two months anyway. So I was hoping to just utilize this current tcsh script and rewrite the whole thing a couple months from now in python.

---

### Post by ghostdog74 on 2008-08-06
irregardless of what shell you are using, use bc or expr to do calculations
eg
```

echo "4 * 3" | bc

```

---

### Post by GammaPoint on 2008-08-11
> **ghostdog74 said:**
> irregardless of what shell you are using, use bc or expr to do calculations
eg
```

echo "4 * 3" | bc

```


Does anyone know the correct syntax to do this within a tcsh script though? It doesn't work for me. I simply created a file called 'test.tcsh' and the contents of the file are 


```

set VAR = `echo "3*4" | bc`
echo $VAR

```

I then tried 'tcsh test.tcsh' on the commandline, but nothing was echoed out. Am I doing something wrong?

And yes, running '"3*4" |bc' on the commandline does give me 12.

---

### Post by zamoran on 2010-07-19
My guess is that your first line looks like this

#/bin/tcsh

instead of the right way to do it

#!/bin/tcsh

Don't forget the exclamation point '!'

---

### Post by lkjoel on 2010-07-19
To make a file executable, you can also just do:
```
chmod +x yourfile
```

---

