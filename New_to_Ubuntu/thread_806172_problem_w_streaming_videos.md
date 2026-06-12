---
title: "problem w/ streaming videos"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by fignig on 2008-05-24
i'm having trouble w/ this mplayer, it will only have the tool bar at the bottom when it's buffered about 30%, in which sometimes takes a bit longer. is there anyway to have the toolbar to play videos right away or at a shorter buffer? and sometimes there's a blank screen where the video is suppose to be. and i have to close all instances of mozilla and open it back up to have the video play for me. is there anyway to help this problem?

---

### Post by fignig on 2008-05-27
does anyonek now how to fix the mplayer so it plays a little less choppy and better resolution?

---

### Post by fignig on 2008-05-30
anyone?

---

### Post by Mentem on 2008-05-30
You mean playing streaming(flash) content through browser?

edit: if yes, try installing ubuntu-restricted-extras

---

### Post by kwacka on 2008-05-30
As Mentem infers - what type of video are you having problems with?

Flash, DVD film, realplayer, windows media, etc?

Is there a particular site that you have problems with?

---

### Post by fignig on 2008-06-02
> **kwacka said:**
> As Mentem infers - what type of video are you having problems with?

Flash, DVD film, realplayer, windows media, etc?

Is there a particular site that you have problems with?

most of the time usually w/ the mplayer.

---

### Post by kwacka on 2008-06-02
Would that be .avi files under mplayer? Or Windows media files under mplayer.
Flash under mplayer? realplayer files under mplayer?

BTW I prefer vlc for multimedia use.

---

### Post by fignig on 2008-06-03
what's the way to remove the mplayer and run all videos through vlc?

---

### Post by fignig on 2008-06-07
> **fignig said:**
> what's the way to remove the mplayer and run all videos through vlc?

that means is there anyway to replace the mplayer w/ vlc w/ a command? or separate commands to remove the mplayer and then set default videos through the vlc player. anyone?

---

### Post by fignig on 2008-06-07
> **fignig said:**
> that means is there anyway to replace the mplayer w/ vlc w/ a command? or separate commands to remove the mplayer and then set default videos through the vlc player. anyone?

anyone?

---

### Post by wolfen69 on 2008-06-07
sometimes totem mozilla can conflict with mplayer try removing it.
```
sudo apt-get remove --purge totem-mozilla
```

---

### Post by cariboo on 2008-06-08
I think what the original poster was saying that he was have problems with the mplayer plugin to Firefox. If that what he is asking about, there is a **kaffeine-mozilla** plugin in the repositories give that a try. You can install it using synaptic, search for **xine**

Jim

---

### Post by fignig on 2008-06-08
> **wolfen69 said:**
> sometimes totem mozilla can conflict with mplayer try removing it.
```
sudo apt-get remove --purge totem-mozilla
```

so i want to remove totem? does it make the mplayer run slower?

---

### Post by fignig on 2008-06-09
can anyone hear me?

---

### Post by fignig on 2008-06-11
so should i remove totem player totally and that will make mplayer or vlc run more smooth?

---

