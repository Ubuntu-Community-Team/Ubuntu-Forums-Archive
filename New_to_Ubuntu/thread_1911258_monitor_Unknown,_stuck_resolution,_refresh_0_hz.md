---
title: "monitor Unknown, stuck resolution, refresh 0 hz"
date: 2012-01-18
forum: New to Ubuntu
---

### Post by bogdarnet on 2012-01-18
> **MrSpike16 said:**
> Its weird, but Nvidia drivers getting installed too for Intel graphics sometimes happens.
The Nvidia stuff needs to be purged and the Intel drivers, 3D (mesa) and Xorg need to be reinstalled.

These are the commands:

[FONT=monospace]```
sudo apt-get purge nvidia*
sudo apt-get install --reinstall xserver-xorg-video-intel  libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-alternatives --remove gl_conf /usr/lib/nvidia-current/ld.so.conf
```

Restart the computer then try glxgears again and it should work.
[/FONT]

I don't know if it was trying this suggestion from another thread on OpenGL, or some other combination of stuff (was following advice in a number of posts on this forum), but I seem to have messed up my configuration trying to get glx 1.3 working on my Intel 945GM card...

Although it does now say the glx server is 1.4, I'm now experiencing the following:

The monitor says Unknown, resolution is set to 1600x1200, refresh rate of 0.  Tried changing to a lower resoltion, and got a grey screen until it reset back to 1600x1200.

/etc/X11/xorg.conf

seems to be empty... I assume that's not right?

I'm on Lucid 10.04 ...

(Any help appreciated!)

---

### Post by bogdarnet on 2012-01-18
This being a really unpleasant state, I'm planning on reinstalling or switching OS... if there's some way to troubleshoot the problem without going that far, please advise, thank you.

---

### Post by QIII on 2012-01-18
By default, 10.04 does not use xorg.conf.  It will try to if it's there.  Since there is one and there are no instructions, that may be your problem.

Unfortunately, without knowing everything you did, it would be hard to tell you just how to undo it.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

That will rename xorg.conf first to see if that stops the confusion.

If not, a reinstall might be considered.  But ask for some guidance before you go too far afield next time.

Nobody can fault you for trying a different distro.  That's the beauty of Linux.

---

### Post by bogdarnet on 2012-01-18
My mistake, looking at the /etc/X11/ folder, it appears there is no xorg.conf at all, which I take it from your response is normal...

So, it sounds like your recommendation is to reinstall at this time?

---

### Post by QIII on 2012-01-18
I hate the "reinstall as a solution" answer.  But if your need is urgent, you might want to.  But it might be worth an hour's wait to see if someone more brilliant than this poor old man comes along with a better answer.

---

### Post by bogdarnet on 2012-01-18
Oh, I'll wait more than an hour, but probably not more than a day. 

One thing that I did leading up to the morass was to enable two PPAs, one is the xorg-edgers, and the other is glasen intel... I thought I might have some luck if I could turn them off... it looks like ppa-purge is the way to do this?

Yet, my system can't seem to find ppa-purge... what's the "correct" way to install it?

---

### Post by bogdarnet on 2012-01-18
Forgot to mention this symptom (not sure if its relevant or extraneous):

Between working and getting to the state it's at now, the system was stuck in a completely unusuable state in which it would get to the logon screen and freeze... the usernames would appear, but the mouse wouldn't move or respond to a click, and you couldn't enter a password.

Gotta love computers.

---

### Post by bogdarnet on 2012-01-19
Unfortunately, I'm not sure exactly what fixed this problem.

One thing that I tried was the following three commands from this website:
[http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html](http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html)

sudo apt-get remove --purge xserver-xorg
sudo apt-get install xserver-xorg
sudo dpkg-reconfigure xserver-xorg

I did look at monitors immediately after that and still saw unknown, so I'm not sure it was these commands that solved the problem.

I'm marking solved, although if anyone knows what exactly to do in this situation, it's probably helpful to anyone else facing this situation.

---

