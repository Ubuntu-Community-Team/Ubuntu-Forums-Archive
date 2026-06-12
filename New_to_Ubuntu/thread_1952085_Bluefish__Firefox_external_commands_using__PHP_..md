---
title: "Bluefish:  Firefox external commands using  PHP ."
date: 2012-04-03
forum: New to Ubuntu
---

### Post by moonsie on 2012-04-03
Greetings,
I am a programmer and very new to Ubuntu 11.10 and I'm having some difficulty with Bluefish executing php files in Firefox.
Bluefish works with html, but not with my php files. Example: <?php phpinfo();php?> Firefox opens with blank page and a dialogue box that says "What should Firefox do with  this file?"  

In Firefox External Commands the original label was Mozilla but I soon found Mozilla was not installed. I changed
the label to Firefox and  Command to;   Firefox %s which didn't work either so I did more searching and found
a few more command entries like:
firefox -remote 'openURL(%f, new-window)' || firefox '%f'&

firefox -new-window $(echo "%s" | sed "s/\/var\/www/http:\/\/localhost/")

firefox -remote 'openURL(%p)' || firefox '%p'& /var/www/http://localhost/ 

firefox -remote 'openURL(%s)' || firefox '%s'& /var/www/http://localhost/
etc etc. 

None of these commands work, at least not for me. 
I would like to get on with my life and continue learning much more about
Ubuntu and linux but I cannot until this dilemma is solved. On the edge.
Any help would be greatly appreciated.
RichM

---

### Post by andrew.46 on 2012-04-03
Hmmmmm..... not sure about php in general but latest Bluefish uses:

```
firefox -remote 'openURL(%p)' || firefox '%p'&
```

to open page in Firefox. Perhaps this will work for you?

---

### Post by Rhaedas on 2012-04-03
Are you running the php files remotely, on from your computer? If the latter, do you have PHP running on your computer? I just ask because it seems like some of the examples you gave are running from a local directory, so it could be something besides Firefox.

---

### Post by moonsie on 2012-04-04
> **Rhaedas said:**
> Are you running the php files remotely, on from your computer? If the latter, do you have PHP running on your computer? I just ask because it seems like some of the examples you gave are running from a local directory, so it could be something besides Firefox.

Hi, thank you for responding.
All my files are on my computer.
Php is running. All my php/mysql files will execute from the address bar
[http://localhost](http://localhost) etc but not when called from Bluefish.
html files will execute with no problem.
Path. /var/www/
moonsie

---

### Post by moonsie on 2012-04-04
Thanks Andrew but I've tried that piece of code and it doesn't work either.
moonsie.

---

### Post by Rhaedas on 2012-04-04
I duplicated your problem, and it's how Bluefish is calling up the file. I've never run into the problem because I typically go to Firefox and load it from there, and edit/save/refresh browser. I tried a few different modifications in the external command, but nothing worked for me.

---

### Post by moonsie on 2012-04-04
Thanks Digg for your stab at the problem.
moonsie

---

