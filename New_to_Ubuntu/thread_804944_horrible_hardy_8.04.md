---
title: "horrible hardy 8.04"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by peterkeyani on 2008-05-23
Its an absolute nightmare trying to get nvidia drivers to work under 8.04. As soon as you enable them you get a insanely low desktop resolution of 640 x 480 going from a mediocre 800 x 600 without them. If that wasnt bad enough, the log on screen is massively off centre, sometimes so much that its impossible to log on!

I have tried using ENVY and that did not help at all.  

I know that many people have the same problem with this distro and I have tried to follow various posts advising what to do but most are contridictory and lack follow up when things dont work out.

I just dont know enough about linux to understand what to do and its driving me nuts!

Hardy: what a dissapointment!:confused:

Pete

---

### Post by philinux on 2008-05-23
> **peterkeyani said:**
> Its an absolute nightmare trying to get nvidia drivers to work under 8.04. As soon as you enable them you get a insanely low desktop resolution of 640 x 480 going from a mediocre 800 x 600 without them. If that wasnt bad enough, the log on screen is massively off centre, sometimes so much that its impossible to log on!

I have tried using ENVY and that did not help at all.  

I know that many people have the same problem with this distro and I have tried to follow various posts advising what to do but most are contridictory and lack follow up when things dont work out.

I just dont know enough about linux to understand what to do and its driving me nuts!

Hardy: what a dissapointment!:confused:

Pete

Yes some hardware configurations seem very hard to sort out. Mine was out the box but any other distro wont pick up by on board nic.

Anyway what are your full specs, that might help.

---

### Post by HotShotDJ on 2008-05-23
> **peterkeyani said:**
> Hardy: what a dissapointment!:confused:

PeteHi Pete -- I understand your frustration.  I am occasionally required to use Windows computers at the University, although I avoid doing it at all costs.  My Windows experience (other than incidental use) is limited to 1998 - 2001.  Other than that, it was Unix, DOS, OS/2 and Linux.  Of course, because of that varied background, I'm probably trained to accept and expect differences in the way various systems work, but still, Windows drives me up a tree -- I just don't know where things are and how to set things up.

Go ahead and re-read the multiple other threads regarding NVidia set-up, and be patient.  Things are going to be difficult for you until you've learned more about how things are done in Ubuntu.  That is natural, normal, and expected. :)

I know I didn't help your current problem, but I hope I've helped you to be less frustrated about it.

---

### Post by peterkeyani on 2008-05-23
> **philinux said:**
> Yes some hardware configurations seem very hard to sort out. Mine was out the box but any other distro wont pick up by on board nic.

Anyway what are your full specs, that might help.

Its a AMD 64 4400 dual core 2.3 MHz with Geforce 6100 integrated graphics. Samsung SyncMaster 900IFT monitor. Never had these problems with 7.10 so Im really confused

---

### Post by wolfen69 on 2008-05-23
try installing an older version of the nvidia driver.

---

### Post by HotShotDJ on 2008-05-23
> **peterkeyani said:**
> Never had these problems with 7.10 so Im really confusedAh.. I didn't realize from your previous post that your already had Ubuntu experience.  This revelation, of course, makes my previous post irrelevant.  Please feel free to ignore (other than the part about trying to help your feel better :) )

---

### Post by SunnyRabbiera on 2008-05-23
This is how it is sometimes with ubuntu, if its too troublesome try another distro.
Mandriva is looking to be good

---

### Post by philinux on 2008-05-23
Look in synaptic and try 

nvidia-glx-legacy

you might have to uninstall nvidia-glx-new

---

### Post by decoherence on 2008-05-23
I had some troubles with nvidia too. In the absence of more info, I'll suggest you take a look at my post here

[http://ubuntuforums.org/showthread.php?t=796322](http://ubuntuforums.org/showthread.php?t=796322)

Try what it says and see if it works. Just make sure you have the appropriate nvidia driver (i used the ones from the repository)

---

### Post by subzero316 on 2008-05-23
For the nvidia 7000m worked fine with envy in 7.10

IN hardy it did no good..But i downloaded the linux form nvidia site and it works like CHARM....:):)

This is wat i did,

 this is [<<-- the link -->>]("http://www.nvidia.com/object/linux_display_ia32_169.12.html") to download the nvidia driver


then go to the shell(CTRL+ALT+F1)

Enter the directory of the dowloaded file,

```
sudo killall gdm
sudo sh NVIDIA-Linux-x86-169.12-pkg1.run
sudo gdm start
```





ps:keep in mind the driver file it usually the same for most might differ for old cards

---

### Post by alienexplorers on 2008-05-23
I had a problem too with my nvidia card.  When I loaded 8.04 it told me to enable Restricted Drivers.  I did that and ended up with 800x600 resolution and the screen was shifted to the right.  I ended up unloading the Restricted driver and loaded the nvidia-glx driver.  I now am able to access all resolutions and the screen is back to the center and readable.

---

### Post by peterkeyani on 2008-05-23
Fixed it by fiddling with "Screens and Graphics" settings!

---

### Post by alienexplorers on 2008-05-23
Please mark your post solved if things are working OK.  Go to your first post and go to thread tools and select thread solved.  Thanks

---

