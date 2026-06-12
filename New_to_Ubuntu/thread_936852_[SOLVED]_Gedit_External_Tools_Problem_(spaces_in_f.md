---
title: "[SOLVED] Gedit External Tools Problem (spaces in file names)"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by JohnGalt131 on 2008-10-03
I write octave files in gedit and have a script where I press a few keys and it launches it in octave. However, I just found out that it doesn't work if there are spaces in the name.
The simple fix is to just name the files without spaces, but that's not what I want.
Here's my script:

#!/bin/sh
m=$GEDIT_CURRENT_DOCUMENT_NAME
gnome-terminal -x octave --persist $m

It says error: octave: unable to open file `Square%20Wave.m'

Any help is appreciated.

---

### Post by kosmiciatakuja on 2008-10-03
This is just a guess but did you try 
```
gnome-terminal -x octave --persist "$m"
```
?

---

### Post by JohnGalt131 on 2008-10-03
> **kosmiciatakuja said:**
> This is just a guess but did you try 
```
gnome-terminal -x octave --persist "$m"
```
?

Yeah, that gives:
#!/bin/sh
m=$GEDIT_CURRENT_DOCUMENT_NAME
gnome-terminal -x octave --persist "$m"



error: octave: unable to open file `Square%20Wave.m'

---

### Post by kosmiciatakuja on 2008-10-03
Okay, I think I know what this is about. It's about %20 - this is how some programs code spaces. I think it's similar to coding in URLs I believe. But your program (octave) might expect real spaces in the filename, like in "something somethingother". Or maybe backslashed, the way it usually works in bash, like something\ somethingother. 

So: my solution for you would be to exchange %20 to space character and put everything into "" just like you tried above, or change space to backslash space, like '\ '...

This way or another, you need something like sed along the way, I would guess. Unfortunately I use sed so rarely I don't remember the syntax, but it should be fairly easy in sed to do something like perl re 's/%20/ /g' or similar, that would exchange %20s to spaces. 

Check this out: [http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)
It's a long guide but you should only need the beginning. 

So, in your script, after assigning value to $m, you would run sed on it to change %20 to spaces and then run gnome terminal and octave on the resulting variable, passed in "" probably.

---

### Post by Kellemora on 2008-10-03
Hi JG

Put the document name in "quotes" if it has spaces in it when trying to access it from command interfaces.

```
gedit /home/user/"my old document"
```

TTUL
Gary

---

### Post by JohnGalt131 on 2008-10-03
If I use
```

m=$GEDIT_CURRENT_DOCUMENT_NAME;echo $m | sed 's/%20/ /'
```

It will print the correct name with spaces and not %20, but I don't know how to apply stdin/stdout to a variable.

---

### Post by JohnGalt131 on 2008-10-05
```
m=` echo $GEDIT_CURRENT_DOCUMENT_NAME | sed 's/%20/ /' | sed 's/ /\?/'`
gnome-terminal -x octave --persist $m
```

This Works.

I thought ` was a ' so my code wasn't working...

---

### Post by gebregl on 2011-01-22
I just had the same problem. As an alternative solution you can use the variable $GEDIT_CURRENT_DOCUMENT_PATH which retains empty space. But then the variable has to be put in quotes.

```

m=$GEDIT_CURRENT_DOCUMENT_PATH
gnome-terminal -x octave --persist "$m"

```

---

