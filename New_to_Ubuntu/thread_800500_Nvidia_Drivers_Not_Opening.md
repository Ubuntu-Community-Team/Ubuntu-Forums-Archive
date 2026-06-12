---
title: "Nvidia Drivers Not Opening"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Ninelivez on 2008-05-19
Hey there. I went to the Nvidia website, picked out my Card, downloaded the drivers for linux 32 bit. Then it says I need to type:

sh NVIDIA-Linux-x86-169.12-pkg1.run

In the Terminal. But when I do that, it says:

sh: Can't open NVIDIA-Linux-x86-169.12-pkg1.run

Any ideas as to what I need to do to install these?

---

### Post by Ninelivez on 2008-05-19
bump :]

---

### Post by dtrot55 on 2008-05-19
This is how I got the nvidia drivers installed.  

************************
HOW I SOLVED IT FOR YOU NOOBS LIKE ME!
************************

rebooted into safe mode  CTRL+ALT+F1

Code:
sudo telinit 3

Sudo /etc/init.d/gdm stop

PATH TO YOUR NVIDIA PKG

EX:
cd /home/dtrot/Desktop
sudo sh Nvidia-Linux-x86-169.12-pkg1.run

Sudo reboot

---

### Post by HotShotDJ on 2008-05-19
> **Ninelivez said:**
> Hey there. I went to the Nvidia website, picked out my Card, downloaded the drivers for linux 32 bit.Is there some reason you did that rather than use System --> Administration --> Hardware Drivers?

---

### Post by Ninelivez on 2008-05-19
> **HotShotDJ said:**
> Is there some reason you did that rather than use System --> Administration --> Hardware Drivers?

Oh, I did that. But I figured that was something different, as I couldn't find any menu to tweak my settings and whatnot.

Sorry, this is coming from a very new Ubuntu user.

---

### Post by HotShotDJ on 2008-05-19
> **Ninelivez said:**
> Oh, I did that. But I figured that was something different, as I couldn't find any menu to tweak my settings and whatnot.

Sorry, this is coming from a very new Ubuntu user.Oh, no reason to be sorry. :) I think what you want is the package nvidia-settings

It is in the repositories (System --> Administration --> Synaptic Package Manager)

---

### Post by Ninelivez on 2008-05-19
Ah ok thanks, just downloaded it. Any idea how I can open it and start configuring things? :)

---

### Post by RequinB4 on 2008-05-19
Hold on, what "Things" are you trying to configure?  May want to browse around system - preferences and system - admin a little bit.

Either way, to use that package, press alt + F2 and type "nvidia-settings."  Press enter.

Like i said, the default programs probably have what you need :)

---

### Post by HotShotDJ on 2008-05-19
> **Ninelivez said:**
> Ah ok thanks, just downloaded it. Any idea how I can open it and start configuring things? :)If it is not in any of your menus (check System --> Administration & System --> Preferences) then just run it from a terminal (Applications --> Accessories --> Terminal)... I believe the command is nvidia-settings, but I won't swear to it. :)  Its been awhile since I've dealt with NVidia cards.

---

### Post by Ninelivez on 2008-05-19
Heh I'm just trying to set up both my monitors to the right resolution. Something went wrong though and now my main monitor, which should be 1080x1050 is for some reason stuck in 460x480 and I have to move my cursor around the screen to see everything. Changing it back to 1680x1050 in the resolution manager does nothing either. Here's a picture to explain it a little better.

[img]http://xs127.xs.to/xs127/08212/what709.jpg[/img]

I've already made a seperate thread about this though.

---

