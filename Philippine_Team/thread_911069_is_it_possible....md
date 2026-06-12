---
title: "is it possible?..."
date: 2008-09-05
forum: Philippine Team
---

### Post by killer_d76 on 2008-09-05
is it possible to install this app from DSL to ubuntu?.. see attached picture.

---

### Post by loell on 2008-09-05
yes,its **conky**, its available in ubuntu repo,

you could get the rc file from dsl if you want that exact look.

---

### Post by killer_d76 on 2008-09-05
thanks loell.. could you guide me on how to get the one from DSL?.. looks like that one don't eat a lot from ram!.

---

### Post by loell on 2008-09-05
np.. there should be  a **.conkyrc** in your dsl home directory just copy its content. then put it in **.conkyrc** in your ubuntu's home directory.

---

### Post by killer_d76 on 2008-09-05
can't seem to find any .conkyrc in the home directory of DSL?

---

### Post by loell on 2008-09-05
could it be because, they reverted back to **torsmo**?

you could ask at [DSL forum]("http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi") on where they put their **.conkyrc**

either they  put the rc file on a different directory other than home ,or they could be using torsmo the father of conky.

---

### Post by ronnielsen1 on 2008-09-05
You are clicking on show hidden files, aren't you?

---

### Post by killer_d76 on 2008-09-05
i was able to view all the hidden files but still no luck on .conkyrc.. i just downloaded torsmo-0.18.tar.gz now i don't know how to install this package on my desktop.

---

### Post by ronnielsen1 on 2008-09-05
>  i just downloaded torsmo-0.18.tar.gz now i don't know how to install this package on my desktop. 	

> I installed torsmo from the debian package here:
[http://packages.debian.org/unstable/x11/torsmo](http://packages.debian.org/unstable/x11/torsmo)

with 

dpkg --ignore-depends=libfontconfig1 -i torsmo_0.18-5_i386.deb

to stop it complaining about libfontconfig dependancies
seems to work ok.
[http://ubuntuforums.org/showthread.php?t=6504](http://ubuntuforums.org/showthread.php?t=6504)
Always check for a deb first - easier

---

### Post by killer_d76 on 2008-09-05
hehehe.. just installed conky anyways.. by using [COLOR="red"]sudo apt-get install conky[/COLOR], then on the terminal i just type [COLOR="Red"]conky[/COLOR]to activate it.. is it possible to configure conky to start or open up when i log-in?

---

### Post by killer_d76 on 2008-09-05
by the way, thanks for the help ronnielsen1!.. :KS:KS:KS

---

### Post by loell on 2008-09-05
> **killer_d76 said:**
> is it possible to configure conky to start or open up when i log-in?

have you already figured this out ?

anyhow, if you haven't yet..

just go to ** System** --> ** preferences ** --> **Sessions**

just add conky at startup.

---

### Post by killer_d76 on 2008-09-05
i'll try that later pag-uwi ko.. thanks Loell, i stil owe you my soul right?! :evil: :lolflag:

---

### Post by loell on 2008-09-05
> **killer_d76 said:**
>  i stil owe you my soul right?! :evil: :lolflag:

yes.. of course, don't forget that. :twisted:

but it will take years for your soul to ripen, so just enjoy  ubuntu life and real life as well.

no worries.. :lolflag:

---

### Post by pendletone on 2008-09-05
> **killer_d76 said:**
> i'll try that later pag-uwi ko.. thanks Loell, i stil owe you my soul right?! :evil: :lolflag:

haha natawa ako dun ah! :p

---

### Post by killer_d76 on 2008-09-06
haruh, pasensya ha, medyo ayaw gumana ng utak ko ngayon eh.. i found a good link about conky ([http://ubuntuforums.org/showthread.php?t=867076&highlight=conky](http://ubuntuforums.org/showthread.php?t=867076&highlight=conky))

medyo nakukulot na yung utak ko eh,

[SIZE="2"][COLOR="Red"]STEP 1 - Create a conky

Create a directory in /home called /Conky 
Create an empty file called; conkymain:

Code:
gedit ~/Conky/conkymain

Paste a conky file from one of the posts in the threads above that you like into that empty file and save it.[/COLOR] [/SIZE]

[COLOR="Blue"]- as i understand this.. punta ko ng Home Folder > create new folder "Conky" o ganito sudo ko  ```
make dir Conky chorva?
``` :confused: tapos anong empty file? at alin yun ipe-paste ko?, yung script ng gusto kong Conky look right? and saan ko ise-save daw?[/COLOR]


[COLOR="Red"]STEP 2 - Setting up conky to autostart on boot.
Create a hidden file ~/.startconky

Code:
gedit ~/.startconkyIn this empty file paste the following: 
Code:
#!/bin/bash
sleep 0 &&	# 0 good for Xfce - use 20 to 30 for Gnome
conky -c ~/Conky/conkymain &
#sleep 0 &&
#conky -c ~/Conky/conkyforecast &[/CODE][/COLOR]

- wow pare "Nose Bleed" ituuuuu! :lolflag: paki-tagalog nga! please!, sensya po bobo talaga ko sa Ingles eh.. hehehe

---

### Post by initial_m on 2008-09-07
[http://ubuntuforums.org/showthread.php?t=887242](http://ubuntuforums.org/showthread.php?t=887242)

-link yan bro dun sa dati ko pang thread, nag ask na rin ako dito sa forums about conky bro, ganyan na gamit ko ngyon, hehehe, daming helpful links dyan post ni rjmdomingo2003 and others..read mo na lang bro..:guitar:

---

### Post by killer_d76 on 2008-09-07
thanks bro.. if ever patulong na lang sa setting-up nito!.. nakakalbo na'ko dito eh.. :lolflag: napaka-simple ng set-up pero ayaw pa rin lumabas kasi ng gusto kong set-up eh.. hehehe :lolflag:

---

### Post by killer_d76 on 2008-09-08
okey after a couple of playing with terminal.. here's what i got!.. hehehe..

ei.. initial_m, i just burned you XP Super Light Edition (512MB) ;)

---

### Post by killer_d76 on 2008-09-09
ok i have it working now.. but i only got it on one of my 4 deskop.. sorry intial_m i forgot where you point me what to put or what to type on the script to have conky on all desktop! :(

---

### Post by initial_m on 2008-09-09
sa my "own_window_hints" lagay mo lang dun sa gilid sticky

-hehehe:popcorn:

---

### Post by killer_d76 on 2008-09-09
oki... thanks bro hehehe, nakalimutan ko eh. tanda na kasi eh :lolflag:

---

