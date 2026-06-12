---
title: "Brasero wont open"
date: 2011-12-31
forum: New to Ubuntu
---

### Post by ianma on 2011-12-31
I am trying to copy a CD using Brasero so I am right clicking on the mp3 file and selecting open with Brasero disc burner and for a few seconds the icone for it appears in the toolbar on the left side of the screen but then it goes and nothing appears to open on the desktop.

I also tried to open it from the dash menu but the same happens here also.
I am using Ubuntu 11:10 have done a restart so now I am out of ideas, does anyone know anything I can try to make this work.

Thanks

Ian

---

### Post by westie457 on 2011-12-31
Hi try opening in a terminal ```
brasero
``` post any errors and we will have a look at them.

Thank you

---

### Post by ianma on 2011-12-31
> **westie457 said:**
> Hi try opening in a terminal ```
brasero
``` post any errors and we will have a look at them.

Thank you

OK here comes the error message, in fact everything seems to just be running a little slow a bit like an old windoze machine, everything was ok, I dont know if it makes a difference but I have just installed Ubuntu 11:10 a few days back with the windows xp pro still on the system which I use for a cctv program most of the time unless I restart and let it boot up in Ubuntu for my use as I am trying to get used to the system I am quite new to Linux.

Anyway here are the results of the terminal window
```

bradudley@dudley:~$ brasero 
ERROR: Could not load classifier cascade  /usr/share/opencv/haarcascades/haarcascade_frontalface_alt2.xml
```Thanks again

---

### Post by westie457 on 2012-01-04
> **ianma said:**
> OK here comes the error message, in fact everything seems to just be running a little slow a bit like an old windoze machine, everything was ok, I dont know if it makes a difference but I have just installed Ubuntu 11:10 a few days back with the windows xp pro still on the system which I use for a cctv program most of the time unless I restart and let it boot up in Ubuntu for my use as I am trying to get used to the system I am quite new to Linux.

Anyway here are the results of the terminal window
```

bradudley@dudley:~$ brasero 
ERROR: Could not load classifier cascade  /usr/share/opencv/haarcascades/haarcascade_frontalface_alt2.xml
```Thanks again

Hello and apologies for not getting back sooner.

Unfortunately I know nothing about what could be causing the error. Have done a bit of research and somehow 'brasero' is trying to open something to do with facial recognition software.

If you can find out what steps you took before the error started you could back-track through them until brasero runs properly.

Basically this is a 'bump' in the hope that someone more knowledgable than me can help you.

---

### Post by crazy bird on 2012-01-04
Brasero is well known for causing any kinds of issues and problems. Brasero is the default burning tool, but not stable enough and still full with bugs. Best to do is skip Brasero and install K3B or Xfburn. You can read [here]("https://sites.google.com/site/tipsandtricksforubuntu/multimedia/burning-tools") more about it.

---

