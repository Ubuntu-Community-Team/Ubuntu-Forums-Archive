---
title: "Boot Into Ubuntu But Get Error About My Graphics Driver"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by StunnerAlpha on 2008-09-24
I try to boot into Ubuntu, and while it loads it slows down and shows up a screwed up screen with an error message saying that it doesn't have my graphics driver, or something to that effect and just gives me a black terminal screen. I installed version 7.04. Should I try installing the latest version or should I go ahead and install the driver via USB Stick? If I need to install it via USB Drive could you fill me in on how I would go about it? Thanks in advance!

---

### Post by StunnerAlpha on 2008-09-24
I have an ATI Mobility Radeon X1300 video card.

---

### Post by Orange_and_Green on 2008-09-24
Hi :)

If I were you, I'd install 8.04 as the management of ATI drivers has been simplified enormously, and the newer kernels may have better compatibility. Anyway, you can find instructions on installing ATI drivers here:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

And this is ATI's driver download page:

[http://ati.amd.com/support/driver.HTML]("http://ati.amd.com/support/driver.HTML")

I wish you the best of luck:KS

---

### Post by MattThLinuxNewb on 2008-09-24
I'd also recommend looking into EnvyNG ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)) After hours of frustration trying to get the Nvidia drivers working manually I gave it a try, and it worked perfectly. (It supports ATi drivers as well). Hope this is of some help.

---

### Post by StunnerAlpha on 2008-09-24
> **MattThLinuxNewb said:**
> I'd also recommend looking into EnvyNG ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)) After hours of frustration trying to get the Nvidia drivers working manually I gave it a try, and it worked perfectly. (It supports ATi drivers as well). Hope this is of some help.

Nice, that looks sweet. i am first going to try installing 8.04, if the video driver still doesn't work I will give your suggestion a shot for sure. But I have a question, how do I go about using that program when my Xserver doesn't start? Do I put it on a USB drive and navigate to the device and run it from there? Any commands I should know? I am very new to all of this. Thanks.

---

### Post by StunnerAlpha on 2008-09-24
Also just wanted to let you guys know that I am downloading:

Ubuntu Edition: Ubuntu 8.04.1 desktop
Computer Platform: i386

And I have Intel Centrino Duo. Not sure if it is 64-bit though. I know my Windows Professional is 32-bit, but not sure if the hardware is 64-bit compatible. You think I should be downloading the "64bit AMD and Intel computers" version? Thanks!

---

### Post by MattThLinuxNewb on 2008-09-24
No, definitely stick with the x86 Ubuntu you're already getting. If your CPU is 64bit it will still support it fine. If the XServer fails to start and you end up in the console, you can run the text version of Envy. Have a look here: [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)
From what I remember it was very straight-forward so it shouldn't be a problem.
You should have internet access even in the console if Ubuntu detected your hardware right, so to install it you just need to enter:
```
sudo apt-get install envyng-gtk
```
Once it's installed, to run the text version just enter:
```
sudo envyng -t
```

---

### Post by Liviu-Theodor on 2008-09-24
> **StunnerAlpha said:**
> And I have Intel Centrino Duo. Not sure if it is 64-bit though. I know my Windows Professional is 32-bit, but not sure if the hardware is 64-bit compatible. You think I should be downloading the "64bit AMD and Intel computers" version? Thanks!

As far as I know, any Intel [...] Duo processor is 64-bit.
And for using the 32-bit or the 64-bit ubuntu, you should read this [thread]("http://ubuntuforums.org/showthread.php?t=905061").

---

### Post by StunnerAlpha on 2008-09-24
Alright, well my system has 2GB of RAM, so it looks like I am sticking with the 32-bit version. Thanks for all the help.

---

### Post by StunnerAlpha on 2008-09-24
Yeah 8.04 did the trick. I am able to boot into it seamlessly. Another problem though. It is giving me an error message when I try installing the ATI driver for my system. This is when I should try envy as suggested above, right?

---

### Post by StunnerAlpha on 2008-09-25
Alright, well I installed an ATI Graphics Driver and restarted, and the Ubuntu loading screen just froze for a good half hour before I force shut down the system. Now how should I go about fixing my system? Uninstall that driver? If so, how do I go about uninstalling it if I can't even boot into Ubuntu? Thanks.

---

### Post by StunnerAlpha on 2008-09-25
Uhh, disregard my prior post. I was away doing things and it must have frozen while restarting and I thought it was booting up... my bad. Still... that is a bad sign, right? I just booted into Ubuntu with no problems, so there is nothing wrong... as far as I can tell. Also, I would really like to install my UltraNav drivers for my ThinkPad T60. How would I go about doing this? Thanks!

---

