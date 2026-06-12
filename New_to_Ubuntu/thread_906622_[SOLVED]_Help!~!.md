---
title: "[SOLVED] Help!~!"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Elephantman5 on 2008-08-31
I uninstalled glx nvidia driver in synaptic, thought what I was installing was newer but it wasn't.

When I went into Hardware Drivers and enabled the proprietary drivers again and restarted it didn't get better, I'm still in Very Low resolution mode!
I went to nvidia site and downloaded my driver: Geforce 8500 driver and it tells me to exit the X server or whatever
Last time I tried to do that it was a black screen and I had no idea what to do next.
Please help!

---

### Post by Elephantman5 on 2008-08-31
Let's see

[http://www.linuxforums.org/forum/redhat-fedora-linux-help/40769-exit-x-server.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/40769-exit-x-server.html)

[http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.12/README/chapter-04-section-02.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.12/README/chapter-04-section-02.html)

[http://www.nvidia.com/object/linux_display_amd64_173.14.12.html](http://www.nvidia.com/object/linux_display_amd64_173.14.12.html)

[http://img510.imageshack.us/my.php?image=img2959zx9.jpg](http://img510.imageshack.us/my.php?image=img2959zx9.jpg)
[http://img510.imageshack.us/img510/2825/img2959zx9.jpg](http://img510.imageshack.us/img510/2825/img2959zx9.jpg)
[http://img528.imageshack.us/img528/4008/img2960kx2.jpg](http://img528.imageshack.us/img528/4008/img2960kx2.jpg)
[http://img502.imageshack.us/my.php?image=img2961iz0.jpg](http://img502.imageshack.us/my.php?image=img2961iz0.jpg)
[http://img502.imageshack.us/img502/9237/img2961iz0.jpg](http://img502.imageshack.us/img502/9237/img2961iz0.jpg)
[http://img502.imageshack.us/img502/8541/img2964bn1.jpg](http://img502.imageshack.us/img502/8541/img2964bn1.jpg)

So, I supposedly exit the xserver but the installer says I'm not exited.
I can't login to root for some reason, or I'm doing the command wrong.
What's the command to login to root? I am the administrator, I have the password and everything.

---

### Post by Elephantman5 on 2008-08-31
Supposedly the command for logging into root is 
su root
When I do that after doing Ctrl Alt F1 it says I have the incorrect password, even though I can successfully login  as myself.

---

### Post by alienexplorers on 2008-08-31
You should not use su root, but sudo and use your own password.

---

### Post by Elephantman5 on 2008-08-31
So I found this:
[http://ubuntuforums.org/showthread.php?t=309787](http://ubuntuforums.org/showthread.php?t=309787)

Fine and dandy, not.
Yeh, sure installed supposedly, but take a look at this desktop:

[[IMG]http://img254.imageshack.us/img254/9651/screenshotam4.th.png[/IMG]](http://img254.imageshack.us/my.php?image=screenshotam4.png)

---

### Post by Elephantman5 on 2008-08-31
I've already done apt-get update, but there's supposedly nothing to update.

I've restarted.
I tried to get the config file for nvidia's great driver, but I don't know what to do with it.
Their tutorial didn't say very much of anything on how to install it, and even less on what to do with the config thing.

Right now I don't really care, how could it get worse? So I'm in synaptic and, I searched for nvidia, installed all the icons with the ubuntu symbol by it.
They look important, so why not?

---

### Post by Elephantman5 on 2008-08-31
[http://paste.ubuntu.com/42247/](http://paste.ubuntu.com/42247/)

---

### Post by Elephantman5 on 2008-08-31
See the real problem is, I don't understand why nothing is fixed when, 
After installing a driver that's obviously not newer, I , Take It Off and Reinstall what I had before.
But, in spite of this logical progression, nothing happens,
I'm still in low resolution mode.

I don't see any monitor settings anywhere,
[[IMG]http://img237.imageshack.us/img237/4333/img2973bi1.th.jpg[/IMG]](http://img237.imageshack.us/my.php?image=img2973bi1.jpg)

And this beautiful thing, doesn't help with its options, of which I configured the best I could, but wouldn't do anything at all.
I find it interesting I have the option to have better FPS on this one though, then on whatever other options I had in the standard options I had in UBuntu (Which I forgot where those are)

---

### Post by Elephantman5 on 2008-08-31
Don't worry guys
I've got it.

sudo dpkg-reconfigure xserver-xorg


I think it's because I titled it Help.

---

### Post by mastergunner on 2008-09-05
> **Elephantman5 said:**
> Don't worry guys
I've got it.

sudo dpkg-reconfigure xserver-xorg


I think it's because I titled it Help.


SO what worked? Do you have all your resolutions? I am having the same problem you are.

---

### Post by Elephantman5 on 2008-09-05
> **mastergunner said:**
> SO what worked? Do you have all your resolutions? I am having the same problem you are.
As I said,
sudo dpkg-reconfigure xserver-xorg

That should fix you up. Really, ubuntu is unforgiving, kind of hard to fix that graphics stuff.
SERIOUSLY DO NOT RECOMMEND ANYONE INSTALLING NVIDIA (Origional drivers)
Just stay with Ubuntu's stuff.

Don't mess with the drivers!

---

### Post by mastergunner on 2008-09-05
So you are saying if the card can do all sorts of rendering dont worry about installing the right drivers cause they will just break the OS?

---

### Post by Elephantman5 on 2008-09-05
> **mastergunner said:**
> So you are saying if the card can do all sorts of rendering dont worry about installing the right drivers cause they will just break the OS?

No, don't listen to me. I don't know anything about it. Other than, when I went through the process of installing the native drivers from the actual website (nvidia), and read about the  native drivers in some ubuntu help doc, it says the supported drivers are better.

Go for it dude, back up your stuff though.
I tried everything, all the drivers in the repos and the origionals, and nothing worked but what Ubuntu handed me on a silver platter.

---

