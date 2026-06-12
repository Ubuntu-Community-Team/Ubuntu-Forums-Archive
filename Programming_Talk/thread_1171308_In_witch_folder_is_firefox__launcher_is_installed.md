---
title: "In witch folder is firefox  launcher is installed ?"
date: 2009-05-27
forum: Programming Talk
---

### Post by hoboy on 2009-05-27
I have asked this question on installation/update forum then I tough that this forum will be appropriated, sorry if any confusion.

I have to launch Firefox from eclipse, that required that I point to "in windows term it will be .exe file that launch firefox"
where is file in ubuntu ?

---

### Post by konqueror7 on 2009-05-27
most programs reside in the **/usr/bin/** directory; so it would be **/usr/bin/firefox**, will launch firefox...

try using the 'whereis' command if you want to find where something is.```
man whereis
```

---

### Post by x33a on 2009-05-27
as konqueror said use whereis command.

my output
> 
whereis firefox
firefox: /usr/bin/firefox /usr/lib/firefox /usr/share/firefox

> **hoboy said:**
> I have to launch Firefox from eclipse, that required that I point to "in windows term it will be .exe file that launch firefox"
where is file in ubuntu ?

and in linux, there is no extension for the executable, so no need to get confused.

you can check a file type using "file" command.

---

### Post by Reiger on 2009-05-27
The true launcher (.desktop file) resides somewhere under /usr/share/applications or /usr/local/share/applications

But if you want to launch program: /usr/bin or /usr/local/bin

A failsafe way (as opposed to using whereis) is to use **which firefox** (gives you the `right' binary, or shell script). On my system: "which firefox" yields "/usr/bin/firefox".

---

### Post by sujoy on 2009-05-27
nah "whereis" will always point to the actual program, whereas "which" will just point to the alias if one is set. hence whereis is a kinda better :P

---

### Post by Tibuda on 2009-05-27
> **sujoy said:**
> nah "whereis" will always point to the actual program, whereas "which" will just point to the alias if one is set. hence whereis is a kinda better :P
Never knew the difference. Thanks for the info.

---

