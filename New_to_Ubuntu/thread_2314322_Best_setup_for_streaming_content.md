---
title: "Best setup for streaming content"
date: 2016-02-20
forum: New to Ubuntu
---

### Post by craig52 on 2016-02-20
Hi,

I am new to Ubuntu and would appreciate advice.  I have a dedicated laptop and screen and stream all content.  I use to do this using Windows but had endless problems and so have now moved to Linux.  What setup (Ubuntu flavour) would best suit my need, which really is purely is a clean, easy to navigate desktop and access to a web browser?

Thanks in advance.

Craig

---

### Post by Bucky Ball on 2016-02-20
Welcome. Well, it is a massive learning curve if you know nothing about Linux and Ubuntu, but this can be done with a [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD"). That installs the Ubuntu kernel (which all flavours are built on anyway), you do the rest: desktop environment, web browser, whatever else you want/need is installed by you. Easier than it sounds if you know your way around.

An easier option might be to go for [Xubuntu]("http://xubuntu.org/") or [Xubuntu-core]("http://xubuntu.org/news/introducing-xubuntu-core/") (or Lubuntu-core lighter again but I'm not so keen on the lxde desktop environment it uses).

Any of the above (not the mini unless you install them) will give you an easy to navigate desktop and Firefox web browser (I think Lubuntu uses Midori or Catweasel actually).

Hope that helps.

(Just a note: You can select 'machine profiles' in the mini.iso using the 'tasksel' function. This will allow you to install any of the flavours by install their desktop - 'xubuntu-desktop' for Xubuntu for instance -  but it kind of defeats the purpose of doing a mini. 

For a desktop and browser, after you installed the mini (without selecting a machine profile) and rebooted  you'll be at a cursor. Log in and issue:

```
sudo apt-get install xfce4 synaptic firefox thunderbird
```

Hit return. When that's finished and you're back at a cursor:

```
sudo reboot -h now
```

When you reboot, you should arrive at a regular login screen, log in and you'll have a navigable desktop and a browser, email client and package manager (Synaptic Package Manager) where you can easily select other software to install if you want/need to.)

---

### Post by coldraven on 2016-02-20
It depends on the specs of the laptop. If it's old and was running XP your best bet is Xubuntu or Lubuntu. If it's newer you could try regular Ubuntu but the Unity desktop will be unfamiliar and might not be to your liking. If you want a distribution that is similar to Win 7 then maybe Linux Mint Cinnamon will suit you. Mint is based on Ubuntu but uses yet another DE. (Desktop Environment)
The best thing is that you can try all these out by booting a Live CD or memory stick and see if you like it without installing.


You can get all the 'Buntus here: (Tip: after selecting a version scroll down to see other download options, I use the Torrents as they are fast and also verified for integrity)
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

and Linux Mint here:
[http://www.linuxmint.com/](http://www.linuxmint.com/)

---

### Post by ajgreeny on 2016-02-20
I am uncertain if you want to stream to or from this laptop; if you are wanting to stream from it as a mediaserver, what are you going to use?

---

### Post by Rocky_Bennett on 2016-02-20
Are you streaming audio and video? If you plan on streaming both, then I highly recommend at least 16 GB of RAM and at least a quad core 3 GHZ CPU. Anything less than this and you might get a lot of stuttering in your stream. You know, drop outs in your video and stutters in your audio. If you are just streaming audio, then you might make due with 8 GB of RAM if you are only streaming 900 MBPS of audio data. The amount of data that you are streaming as measured in MBPS is the key to the type of system that you should set up.

---

### Post by Rocky_Bennett on 2016-02-21
> **craig52 said:**
> Hi,

I am new to Ubuntu and would appreciate advice.  I have a dedicated laptop and screen and stream all content.  I use to do this using Windows but had endless problems and so have now moved to Linux.  What setup (Ubuntu flavour) would best suit my need, which really is purely is a clean, easy to navigate desktop and access to a web browser?

Thanks in advance.

Craig



My advice to you is that since you were having problems setting up streaming using Microsoft Windows (What edition?) that you should use a general computer forum like Bleeping Computer in order to fix your issues. If you were having issues with this under Windows, changing over to Linux might not be the answer to your problem, you might have hardware issues. Either way, there are plenty of people here to help you.

---

