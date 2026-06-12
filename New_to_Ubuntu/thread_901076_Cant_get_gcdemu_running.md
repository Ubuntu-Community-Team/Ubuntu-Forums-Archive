---
title: "Cant get gcdemu running"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by berencamlost on 2008-08-26
Hi I'm having issues getting the gcdemu applet to run. I've installed the cdemu daemon and gcdemu from here, [http://ppa.launchpad.net/cdemu/ubuntu](http://ppa.launchpad.net/cdemu/ubuntu) (added it to synaptic). Try as i might i can't get the applet to show up as active in the panel. I searched around and found that i had to start the daemon by using ```
sudo cdemud -d
``` when i do i get this message ```
Daemon returned 0.
``` and i still can't run gcdemu. I'm just wondering what I've done wrong and how i can fix it

-thanks for your help

---

### Post by berencamlost on 2008-08-26
./bump

---

### Post by MadsPB on 2008-08-26
If you check this post:
[http://ubuntuforums.org/showthread.php?t=845822&highlight=cdemu](http://ubuntuforums.org/showthread.php?t=845822&highlight=cdemu)
They suggest that you add to the gnome panel, the gcdemu applet, by right click on the gnome menu bar, and clicking add to panel. Then you can find the gcdemu applet and add it to the bar.
When you then start the daemon as you did and receive the '0' the icon of the applet will be activated.. 

Worked for me just now :D

---

### Post by berencamlost on 2008-08-27
That's exactly what I've done. In fact thats the thread i referenced in the first place to try and get it running, but i still cant get it to run. I don't know what the problem is...

---

### Post by MadsPB on 2008-08-27
Okay.. this comment is just to be sure..

What i noticed was, that in the help file of gcdemu it said that there were two icons for gcdemu, a greyed out, and a blue lit..

the difference isn't big though...

what i noticed when I did what you did.. (because I was learning from your thread..) was that the icon changed to the lit up icon..

So it didn't with you..

I did one more thing.. before it worked.. which was to follow the instructions here :
> **Partyboi2 said:**
> Try installing the python-gtk2-dev package[FONT=monospace]
[/FONT]```
sudo apt-get install python-gtk2-dev
```

---

### Post by hogzilla on 2008-09-21
I just input this in Terminal
```
sudo cdemud -d
```

it returned this

```
Daemon returned 0.
```

and gcdemu becomes active.....

---

### Post by Wickd on 2008-10-12
Hi there

I have exactly the same problem as you. I start up the daemon, but the gcdemu does not want to start. It seems that the daemon is running, but for some reason the client does not want to connect to it??

Please help

---

