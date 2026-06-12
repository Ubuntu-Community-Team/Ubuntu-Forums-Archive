---
title: "Desktop size and screen resolution differ"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by peterlauri on 2008-05-07
Hi,

I have a monitor that was working perfectly before, and then after a few weeks away, and a few different monitors used, I plugged in the old monitor.

Now the resolution is 1600x1200 that is detected perfectly, but the desktop only spans something like 1400x1050. Can I setup the span of the desktop it self somewhere? See how it looks like in the attached png file.

Note, I am using gnome.

/Peter

---

### Post by tjwoosta on 2008-05-07
i had this same issue with gutsy


in gutsy i had to add this to my xorg.conf
```

Section "Monitor"
	Identifier	"TVOutput"
	Option		"Ignore"	"true"

```

the thing is i tried this when i switched to hardy and it didn't work
(i ended up cheating and i just copied my entire xorg.conf from gutsy and put it in hardy)

what you need to do is configure your xorg, but unfortunatly im not sure exactly on how to do that with hardy
(from what i understand the process has changed since gutsy)

you could try searching the forums for how to configure xorg in hardy
(im sure somebodys gone over this problem by now)

---

### Post by peterlauri on 2008-05-07
> **tjwoosta said:**
> i had this same issue with gutsy


in gutsy i had to add this to my xorg.conf
```

Section "Monitor"
	Identifier	"TVOutput"
	Option		"Ignore"	"true"

```

the thing is i tried this when i switched to hardy and it didn't work
(i ended up cheating and i just copied my entire xorg.conf from gutsy and put it in hardy)

what you need to do is configure your xorg, but unfortunatly im not sure exactly on how to do that with hardy
(from what i understand the process has changed since gutsy)

you could try searching the forums for how to configure xorg in hardy
(im sure somebodys gone over this problem by now)

That didn't help me out. I tried to search for this problem, but couldn't find any post similar to it.

---

### Post by tjwoosta on 2008-05-07
hmm.. 

well i did find this 
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/207409]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/207409")

the dpkg-reconfigure is what i had to use to configure gutsy 

from what ive read they have updated xorg since gutsy and now everything is supposed to setup everything automatically (obviously it doesnt work very well)

what you should try first is going to 

/usr/share/applications/screen & graphics
here you choose your monitor and your graphics card

if that still doesnt solve things you will probably need to manualy edit your  /etc/X11/xorg.conf

---

