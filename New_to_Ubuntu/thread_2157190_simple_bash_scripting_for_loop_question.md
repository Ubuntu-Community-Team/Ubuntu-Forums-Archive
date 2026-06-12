---
title: "simple bash scripting for loop question"
date: 2013-06-24
forum: New to Ubuntu
---

### Post by amarumayo on 2013-06-24
[COLOR=#333333]Hi all,[/COLOR]

[COLOR=#333333]NOOB bash scripter here.[/COLOR]

[COLOR=#333333]I have the following loop in a bash shell script:[/COLOR]

[COLOR=#333333]COUNTER=0[/COLOR]
[COLOR=#333333]for file in $WORKING_DIRECTORY/*.ogg[/COLOR]
[COLOR=#333333]do[/COLOR]
[COLOR=#333333]let COUNTER=COUNTER+1 [/COLOR]
[COLOR=#333333]done[/COLOR]

[COLOR=#333333]echo $COUNTER[/COLOR]

[COLOR=#333333]My question is: When the directory does not contain any .ogg files it still returns a value of 1 for the $COUNTER. As soon as there is even one .ogg files it works as it is supposed to. What am I missing?[/COLOR]

[COLOR=#333333]Thanks in advance.[/COLOR]
[COLOR=#333333]Chris[/COLOR]

---

### Post by steeldriver on 2013-06-24
it's the shell's 'nullglob' behavior I think - see here for how to modify it (shopt -s nullglob) --> [http://mywiki.wooledge.org/NullGlob](http://mywiki.wooledge.org/NullGlob)

---

### Post by amarumayo on 2013-06-24
Yes, that was the problem.
Thanks.

---

