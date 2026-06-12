---
title: "How to change desktop, start file sharing, and upgrade"
date: 2013-04-15
forum: New to Ubuntu
---

### Post by rccharles on 2013-04-15
I am running 2011 - 10. 

I'd like to:
-- change my desktop.  I have forgotten all my Ubuntu terminology. I want the one with applications places system on the upper right.

-- start file sharing.  I looked around the current desktop and could not find the gui for this.  I rather do this from the gui.  

-- how to upgrade to the most current Ubuntu from this desktop. I guess I could wait to change desktop so I can find things easier.

I do not know what desktop I am using nor where to find it.  I used Ubuntu in 2006, but the details have slipped away.

Robert

---

### Post by nerdtron on 2013-04-15
> **rccharles said:**
> I am running 2011 - 10. 

I'd like to:
-- change my desktop.  I have forgotten all my Ubuntu terminology. I want the one with applications places system on the upper right.

-- start file sharing.  I looked around the current desktop and could not find the gui for this.  I rather do this from the gui.  

-- how to upgrade to the most current Ubuntu from this desktop. I guess I could wait to change desktop so I can find things easier.

I do not know what desktop I am using nor where to find it.  I used Ubuntu in 2006, but the details have slipped away.

Robert


If you used Ubuntu back in 2006, you're familiar with the old GNOME 2 interface. A lot has changed since 2006.
1. Are you using Ubuntu 11.10? Look at this tutorial to bring back the old the old interface [http://www.webupd8.org/2011/08/installing-using-classic-gnome-desktop.html](http://www.webupd8.org/2011/08/installing-using-classic-gnome-desktop.html). 
But if you really want GNOME 2 experience you should look at distributions other than Ubuntu which offers MATE, a GNOME 2 fork.
Or better yet, try Xubuntu or Lubuntu. You'll easily find your way around the OS.

2. File sharing via network for Ubuntu Systems only or with Windows computers? And what do you want to share, the local files on your computer?

3. I strongly suggest that you upgrade to a newer release because 11.10 is nearing it End-of-Life. You can do a clean install of 12.10 now or at least wait for a few more days for Ubuntu 13.04.

---

### Post by ibjsb4 on 2013-04-15
Just my two cents:

You could upgrade to 12.04 that has long term support and will be supported until 2017.

Then you can add the old gnome2 desktop (a modern day knock-off) by adding the "Gnome Classic Desktop" to it.  You will be able to choose the desktop at boot (login) by clicking on the icon in the login window.

To install the classic desktop, open a terminal (Ctrl + Alt + t) and enter:

```
sudo apt-get install gnome-session-fallback
```

---

### Post by npagan on 2013-04-16
Yeah I'm a new user as well, and kinda get lost looking for games.  I downloaded an ungodly amount of games for my kid, and I don't like it not being in a particular spot like in gnome under games, having to use the dash didn't seem to appealing.  I tried the Zorin distro(which is based on ubuntu) and let me just say its pretty sweet, comes with a ui changer already, with unity, xp, win 7, gnome 2, so you can pick whichever you want. and all the games fall under the games tab nicely.  So on my desktop I have ubuntu so I can get use to it and on my laptop using zorin, cause ts a lot easier for my 10y/o to find all the games for her to play.

---

### Post by mastablasta on 2013-04-16
> **rccharles said:**
> -- start file sharing. I looked around the current desktop and could not find the gui for this. I rather do this from the gui. 


open file browser nautilus and right click on the folder -> properties to set it up for sharing.

> **npagan said:**
>  I tried the Zorin distro(which is based on ubuntu) and let me just say its pretty sweet, comes with a ui changer already, with unity, xp, win 7, gnome 2, so you can pick whichever you want. and all the games fall under the games tab nicely. So on my desktop I have ubuntu so I can get use to it and on my laptop using zorin, cause ts a lot easier for my 10y/o to find all the games for her to play.

i think zorin just uses Gnome 2. it's more of theme switched than desktop switcher. anyway the closes to windows style is KDE and the easiest to modify it to look like windows is in my opinion XFCE (appart from the lighter ones LXDE and IceWM that already look like old windows).

---

