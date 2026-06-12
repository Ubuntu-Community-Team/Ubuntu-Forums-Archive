---
title: "[SOLVED] could someone upload their /etc/fonts folder???"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by macvr on 2008-08-31
hi,
could someone using **_ubuntu 8.04_** upload their /etc/fonts folder?

i'm having font problems, i'v tried several solutions but my fonts config seems very badly messed up![dont know how this happened]

hinting doesnt work,[check attachments>1-hint none, 2-hint full, u can see that the full hint makes things worse] and when i view the web , a lot of bold fonts are too bold! 

so i thought that i'd rather replace my fonts config, with a config that works...


if u want to compare my config and find my erroneous files, pls check this post [http://ubuntuforums.org/showpost.php?p=5681106&postcount=41]("http://ubuntuforums.org/showpost.php?p=5681106&postcount=41")
i hav uploaded my font config files there[I]
the person who has uploaded his font files in that thread has ubuntu 7.10, and the 7.10 fonts config hint my fonts too much, so i have to set the font hinting to slight![/I]

pls run this 
```
cd /etc
tar cf ~/fonts.tar fonts
cd
bzip2 fonts.tar
```
and upload your 8.04 fonts config...


[COLOR="Blue"]also could someone tell me what fonts are used in this forum for bold letters?[arial bold?] those fonts are the most problematic!
may be i could narrow down my search to those fonts[/COLOR]

---

### Post by Jack M. on 2008-08-31
This should work, I have the default fonts on Hardy. Also, I'm not sure what font these forums use exactly, sorry...

---

### Post by Pro-reason on 2008-08-31
> **macvr said:**
> 

[COLOR="Blue"]also could someone tell me what fonts are used in this forum for bold letters?[arial bold?] those fonts are the most problematic!
may be i could narrow down my search to those fonts[/COLOR]
Here is the stylesheet for this website: [http://ubuntuforums.org/clientscript/vbulletin_css/style-7be2532f-00098.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-7be2532f-00098.css)  

You can see what font suggestions it contains.

---

### Post by macvr on 2008-09-01
> **Jack M. said:**
> This should work, I have the default fonts on Hardy. Also, I'm not sure what font these forums use exactly, sorry...


> **Pro-reason said:**
> Here is the stylesheet for this website: [http://ubuntuforums.org/clientscript/vbulletin_css/style-7be2532f-00098.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-7be2532f-00098.css)  

You can see what font suggestions it contains.

thanx guys, i'l c how these work

---

### Post by macvr on 2008-09-01
it worked .... :) thanx jack 

now my fonts are better[check the attached pic n compare the bold fonts!]

ready to take on the web :guitar:[SIZE="1"]with no sore eyes[/SIZE]

---

