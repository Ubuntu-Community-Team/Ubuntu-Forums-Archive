---
title: "`sort` question"
date: 2006-12-27
forum: Programming Talk
---

### Post by cosmolee on 2006-12-27
I'm having a problem understanding the behavior of GNU `sort`.  I haven't used the command since AT&T SVR III Unix ages ago.  Perhaps someone can clear this up for me.

$ cat col1
h
g
f
e
d
c
b
a
H
G
F
E
D
C
B
A

$ sort col1
a
A
b
B
c
C
d
D
e
E
f
F
g
G
h
H


Aren't the all Upper Case letters supposed to come before the Lower Case?  Sort seems to be behaving as if I gave it the "-f" option to ignore case.  Did something change w/ ASCII ordering or has this got something to do with high-order bits being disgarded?  My LANG environment is set to "en_US.UTF-8".

I was expecting :

A
B
C
D
....
a
b
c
d
....


Is there something I'm not understanding here??

TIA.

---

### Post by ghostdog74 on 2006-12-27
this is what happens on my environment
```

neptune:/home/test # sort --version
sort (GNU coreutils) 5.93
Copyright (C) 2005 Free Software Foundation, Inc.
This is free software.  You may redistribute copies of it under the terms of
the GNU General Public License <http://www.gnu.org/licenses/gpl.html>.
There is NO WARRANTY, to the extent permitted by law.

Written by Mike Haertel and Paul Eggert.
neptune:/home/test # cat file
h
g
f
e
d
c
b
a
H
G
F
E
D
C
B
A
neptune:/home/test # sort file
A
B
C
D
E
F
G
H
a
b
c
d
e
f
g
h
neptune:/home/test # echo $LANG
POSIX
neptune:/home/test # export LANG=en_US.UTF-8
neptune:/home/test # sort file
a
A
b
B
c
C
d
D
e
E
f
F
g
G
h
H


```

---

### Post by cosmolee on 2006-12-27
Ah, yes, it's the character set.  I was able to replicate your results by setting LANG=POSIX and make `sort` "behave".  

Wow, these character sets behave really differently from a programmer's point of view.   But my guess is that the en_US.UTF-8 encoding is to have a character set that behaves more in a way that "humans" view letters, ie, not differentiating between "A" and "a" in collation terms.

That could be a real gotcha in the wrong situation.  One could have done all one's shell scripting in a portable manner only to be tripped up by a thing like this.  

Thanks!

---

### Post by cosmolee on 2006-12-27
Actually, it's LC_ALL.  Don't know about all this Locale stuff, but I found this note in the `sort` man page - duh!

"*** WARNING *** The locale specified by the environment affects sort order.  Set LC_ALL=C to get  the  traditional sort order that uses native byte values."


I found that even if LANG was set to "en_US.UTF-8", with LC_ALL set to "C", the sorting behaved as I traditionally expected.  

HTH.

---

