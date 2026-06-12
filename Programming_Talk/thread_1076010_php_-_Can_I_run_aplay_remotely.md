---
title: "php - Can I run aplay remotely?"
date: 2009-02-20
forum: Programming Talk
---

### Post by garyed on 2009-02-20
I'm running Apache server on Hardy.
My goal is to have someone click on one of my web pages & call a command
to play a beep.wav file on my server & not on their browser.
So I'm trying to use the php system(), exec(), or shell_exec() commands to no avail. Is it even possible to output a php command to the server instead of the browser? 
I've been searching the net for two solid days & I can't find the answer so if anyone has one I wish they would post a simple code.
If I do this in terminal:
```

aplay /var/www/beep.wav

``` it plays fine.
If I do this in a file:
```
<? php 
system ("aplay /var/www/beep.wav"); ?> 
```
I get nothing. If I substitute "ls" for "aplay" it will print to the remote browser screen but not the server so thats obviously where I'm missing the boat.

---

