---
title: "how  small  the Ubuntu  can  be?"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by nillgump on 2008-10-02
[SIZE="2"]while everyone want  to upgate of download the pakages with 
"apt-get",I do the against.

I&#12288;uninstalled the whole pakages.
At last I can only use the termial to loggin.
what I can see is a black  background.
what I can use is the command line.
Of course ,this situation is not what I want to see.
So,how to solve?
How to minimize the Ubuntu,but without losing  the essential
    toolkits?
Is there someone have done the job?
Or  give some advices?

If  Ubuntu can  do this,and this is the biggest differece between
     Linux and Windows ,I  think.


Thank you very much![/SIZE]

---

### Post by whizbaby on 2008-10-02
I dont know to which degree this is really helpful, but at first glance it looks like you could use it for the job:
[http://ubuntu-mini-remix.crealabs.it/](http://ubuntu-mini-remix.crealabs.it/)
You build your own livecd with the packages you desire and may install from that. Otherwise theres always the 'alternate install cd' you can use for minimal setups (like on a netbook with 128mb RAM).
Installing a small window manager would be a good idea, too.
There is XFCE4 (biggest of the little) enlightenment and fvwm that I have personally used and that I can recommend(fvwm is a bit tricky to configure, but thats the price you have to pay I guess).

---

### Post by kansasnoob on 2008-10-02
This may be of help:

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by KIAaze on 2008-10-02
Are you doing this for fun or because you are low on RAM or hard disk space?

Here's another pretty radical solution:
[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

> Building LFS produces a very compact Linux system
When you install a regular distribution, you often end up installing a lot of programs that you would probably never use. They're just sitting there taking up (precious) disk space. It's not hard to get an LFS system installed under 100 MB. Does that still sound like a lot? A few of us have been working on creating a very small embedded LFS system. We installed a system that was just enough to run the Apache web server; total disk space usage was approximately 8 MB. With further stripping, that can be brought down to **[SIZE="5"]5 MB or less[/SIZE]**. Try that with a regular distribution. 


Of course, if you still want a GUI, this is not the way to go. :)

I switched to openbox recently and I like it.
It's very light on resources and sufficiently user-friendly.
Here's a nice page which lists programs you might want if you use it (like a taskbar for example :rolleyes:)
[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

The list of window managers is extremely long.
Here's an incomplete list (does not contain [LXDE]("http://lxde.org/")):
[http://xwinman.org/](http://xwinman.org/)

Here's a list of what I have installed for example:
```
[116][~]$  ls /usr/share/xsessions/
aewm++.desktop         Fvwm.desktop     openbox-gnome.desktop
blackbox.desktop       gnome.desktop    openbox-kde.desktop
e-gnome.desktop        IceWM.desktop    pekwm.desktop
e-kde.desktop          jwm.desktop      ratpoison.desktop
enlightenment.desktop  kde.desktop      ssh.desktop
fluxbox.desktop        LXDE.desktop     twm.desktop
fvwm-crystal.desktop   openbox.desktop  xfce4.desktop


```

LXDE is also pretty nice with just the default settings.

---

### Post by Jose Catre-Vandis on 2008-10-02
I am an openbox fan too, but my concern for you would be your potential dependence on what Ubuntu-Gnome has to offer in the way of toolkits. You can build up your GUI quite easily, but then you may suddenly find you are having to install most of the "ubuntu-desktop" to get the experience you want. Try Xubuntu first, then if that is not light enough, do an F4 install (command line only) and build up from there, choosing slim as your display manager (login) and openbox as your window manager. I have tried to build up a system that gives me all the tools without using any "gnome-*" apps/libraries, but it's pretty difficult to acheive if you have a broad spread of requirements.

---

### Post by snowpine on 2008-10-02
Perhaps this might interest you:

[http://ubuntuforums.org/showthread.php?t=933720](http://ubuntuforums.org/showthread.php?t=933720)

---

### Post by karlmp on 2008-10-02
i'm using openbox with no desktop environment

---

### Post by nillgump on 2008-10-03
Thanks all!
By the way,my computer RAM is 1G.MY disk is 160G.
The reason for doing this is I&#12288;cann't stand the feeling that I cann't control the pakages which I have downloaded.
If I can builde the enviroment by myself ,I can chose the pakages which I like,and delete the pakages which I hate.

And ,what I seek for is its simpleness , high speed,and stabilization.

---

### Post by kansasnoob on 2008-10-03
> **nillgump said:**
> Thanks all!
By the way,my computer RAM is 1G.MY disk is 160G.
The reason for doing this is I&#12288;cann't stand the feeling that I cann't control the pakages which I have downloaded.
If I can builde the enviroment by myself ,I can chose the pakages which I like,and delete the pakages which I hate.

And ,what I seek for is its simpleness , high speed,and stabilization.

That's what synaptic is for!

---

### Post by kansasnoob on 2008-10-03
> **Jose Catre-Vandis said:**
> I am an openbox fan too, but my concern for you would be your potential dependence on what Ubuntu-Gnome has to offer in the way of toolkits. You can build up your GUI quite easily, but then you may suddenly find you are having to install most of the "ubuntu-desktop" to get the experience you want. Try Xubuntu first, then if that is not light enough, do an F4 install (command line only) and build up from there, choosing slim as your display manager (login) and openbox as your window manager. I have tried to build up a system that gives me all the tools without using any "gnome-*" apps/libraries, but it's pretty difficult to acheive if you have a broad spread of requirements.

Excellent answer!

---

