---
title: "How to: install 2500 fonts Free (as in beer)"
date: 2005-06-09
forum: Outdated Tutorials &amp; Tips
---

### Post by notos on 2005-06-09
whell i was bored ... so i opened the gimp to make a logo and ... yay i dont have "cool" fonts :( so i go too google and googled for free fonts and started to download files yay! too much files to install manually ... yay! 

so with a bit of PHP-Cli i got every font in that web page (1001freefonts.com) so now you too can download 2500+ fonts to your desktop with this :)

First of download Atached File (font.txt.gz ) un gz it with

```
$ gunzip font.txt.gz
```

now you ave two options one is use d4x and other is wget

** Download these in a folder like ~/fonts cause you will be downloading 2500 zip files you dont want them in ~/ :P **

for d4x select: file-> Find Links In File  and select of course font.txt
then click will apear a list of links simply click ok ;)

if you are a linux guru ... :P or want to use wget 

just type

```
$ wget -i font.txt
```

now you ve got like 2500 zip files if you dont want to unzip them one by one you can do this

```
$ for i in *; do unzip -n "$i"; done
```

after a bit of time you be got tons of files so now you can 

```
$ mv *.ttf ~/.fonts 
$ mv *.TTF ~/.fonts
```

or move them to **/usr/share/fonts** to install the system wide :)

well i think thats all :)

---

### Post by bored2k on 2005-06-09
I would go nuts if I had to scroll through 2500 fonts.. thanks for the option though :? .

---

### Post by poofyhairguy on 2005-06-09
They all fit in 16kb!!!!

---

### Post by skoal on 2005-06-09
2500 fonts?? wow! I like the cut of your jib.  I gotta have more cowbells, and this font collection comes close.

\\//_

---

### Post by UbuWu on 2005-06-09
That's nothing, I have 6760 fonts installed  \\:D/   ;-) 
[http://www.gnome-look.org/content/show.php?content=9883](http://www.gnome-look.org/content/show.php?content=9883)

---

### Post by notos on 2005-06-09
[QUOTE=poofyhairguy]They all fit in 16kb!!!![/QUOTE]

actualy the 16kb file is a list of urls to download :) i had to Gzip it because it was like 200kb

> That's nothing, I have 6760 fonts installed
[http://www.gnome-look.org/content/show.php?content=9883](http://www.gnome-look.org/content/show.php?content=9883)

Wow i didnt know about this ... *Downloads it*

---

### Post by RastaMahata on 2005-06-09
both sets combined make a wonderful collection.. /me downloads

but I still think that ~/.fonts is not the right path to move these files... :S Any suggestions?

---

### Post by skoal on 2005-06-09
[QUOTE=UbuWu]That's nothing, I have 6760 fonts installed  \\:D/   ;-) [/QUOTE]

Whoa! That's a lot of cowbells.  But still, I need more cowbells...

\\//_

---

### Post by notos on 2005-06-10
[QUOTE=RastaMahata]both sets combined make a wonderful collection.. /me downloads

but I still think that ~/.fonts is not the right path to move these files... :S Any suggestions?[/QUOTE]

in my first post you can see **/usr/share/fonts**

---

### Post by Bramme on 2005-06-12
installed all 2500 fonts too, but when i want to startup Word (crossover office) it takes a while  :neutral: ...
So, install them only if you use them!

---

### Post by Xian on 2005-06-12
Heh. Somehow I think I wouldn't use about 2,450 of those. :)

---

### Post by zaxer on 2005-06-12
Great tip!

Thanks!

---

### Post by carney1979 on 2005-06-18
My only problem is it now takes Firefox (1.0.4) 90 seconds to boot, but if I move or rename the ~/.fonts folder, it boots in 13 seconds.

Any suggested fixes?

David

---

### Post by notos on 2005-06-18
hi about FIREFOX 13 Secs are too much time even ... what system are you runing?  i am runing FireFox 1.0.4 with 2500 font and it loads in 1~3 secs also i have a PIII 533Mhz 256mb ram so it a bit out-of-date but runs ok

also may be i installed forn on system wide dir... but .. i dont think so :(

---

