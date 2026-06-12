---
title: "What's the best mini linux for a slow computer?"
date: 2007-10-01
forum: Other OS Talk
---

### Post by jon.reeve on 2007-10-01
I love Ubuntu and have totally converted to using it on my desktop machine. For my tiny laptop, however, even Xubuntu is a little bit too slow for it (500MHz/128M RAM). Since I only really use this thing for typing and occasionally plugging into a wifi connection somewhere to check my email, I don't need OpenOffice, video players, the GIMP, CD burning utilities, or any of that extra stuff. I basically only need a fast browser and Abiword. I installed Puppy Linux for awhile, but it's a really ugly system. DSL, too, I found a little too ugly. I'm not a hacker or anything so I don't need a dozen network utilities whose functions I don't even understand. Vector seems too big, 

Is there a distro that's non-bloated, small (under 200M or so), built for slow computers, but above all pretty and elegant-looking like Ubuntu?

---

### Post by Medieval_Creations on 2007-10-01
My best suggestion would be Debian (Etch),  You can just install base system (no X-Server at first) and install only what you need.  If you want X though there really aren't that many windows mangers as light as Xfce or Fluxbox.

I'm personally waiting for Fluxbuntu's release, which is designed much like Xubuntu to run on low end systems.  It is based off Gutsy and will be available for download same time Gutsy is released.
I have newer rigs, but I don't care for all the flash.

---

### Post by jrusso2 on 2007-10-01
You know fluxbox is very customizable.  I have seen some flux box desktops that would blow your mind.

DSL has flux box as default and you can customize it if its not pretty enough.

---

### Post by D-EJ915 on 2007-10-01
I stuck Debian (via net-inst disc) on my old vaio c1 (400mhz, 192MB) and it's pretty decently well.  The video chip on that laptop sucks *** so the redrawing isn't really that great...but it works fine aside from that.

Just don't install gnome or kde and you should be fine, I hate desktop environments so I wouldn't put xfce on it either but you might not be as much as a command-line junkie as I am.

Basically with the net-install all you have to do is install Base & Laptop, then "xorg" and some window manager and you're ready to go plus whatever else you want to use. (it really doesn't come with anything, not even xterm, lol).  Of course you would have to configure your wireless card too, but that's pretty easy.

---

### Post by pondochris on 2007-10-01
Tinyme is a small efficient os. Its based on redhat, uses fluxbox and is quite elegant. I find it to be quite a bit better than dsl its about 200 MB and has a live CD.

---

### Post by Chilli Bob on 2007-10-02
Try Puppy Linux Community Edition 2.15.  All the benefits of Puppy, but it actually looks good.  Really good actually!! It uses IceWM instead of JWM by default, and has some excellent themes.

Just be aware that if you have saved a previous Puppy's settings to your hard drive, you will have to start the new one by typing......

puppy pfix=ram

...... when it starts to boot, or your previous JWM look will come up instead.

Long live Puppy!!

---

### Post by darrelljon on 2007-10-02
See [http://puppylinux.org/wikka/Distros](http://puppylinux.org/wikka/Distros)

---

### Post by RedSquirrel on 2007-10-02
Xubuntu isn't really that light. 

You could try a minimal installation of Ubuntu with Fluxbox and see if that's fast enough for you. It won't be less than 200 MB, but you get to stick with Ubuntu. ;)

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)
[http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/](http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/)

If you know the video driver you need, put that up front when you install xorg. When you do this, apt will only install that driver and not all the other ones you'll never use. For example:

sudo apt-get install xserver-xorg-video-ati xorg

Just replace the ati with the one you need.

---

### Post by KCPokes on 2007-10-02
You could also look into Zenwalk or Mepis.  I found Zenwalk to run decent on my slower laptop and would have kept it if it wasn't for the sound issues I ran into with the ancient ISA sound card.

---

### Post by fistfullofroses on 2007-10-02
Well, first you should know that there are quite a few lightweight distributions out there. You can try a few of the big names first: Slackware, Arch, Debian, Vector, and Gentoo. Next, you should know that there are a plethora of light window managers out there as well. Some of the more popular ones are Fluxbox, JWM, IceWM, MWM, TWM, CTWM, Ion, ratpoison, and evilwm. The fastest of the distributions listed are Slackware, Arch, and Vector. Your lightest of the windows managers are evilwm, and TWM. However, there a lot of things you can do without X. The only things that you cannot do are web browsing with Flash, and other such plugins, and heavy graphic/video editing. Gaming can be done, but obviously a lot of graphical gaming is impossible. Anyway, I wish you luck with your laptop.

---

### Post by K.Mandla on 2007-10-03
Arch plus Openbox. I use that on a 550Mhz Celeron laptop and my boot time is under 37 seconds. Sheer bliss (and I don't mean that dorky wallpaper :twisted: ).

---

### Post by ayenack on 2007-10-03
Arch +1....... and DSL.

---

### Post by shrimphead on 2007-10-05
another vote for zenwalk here, it blazes

---

