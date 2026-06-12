---
title: "Low graphics, no solution?"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by joey-elijah on 2008-10-14
Hey all, i followed a [guide]("http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/") linked to in another thread to try and get my hibernation issues fixed.

SInce i did that, my computer will only start up in LGM. I've tried 

```
dpkg-reconfigure xserver-xorg 
``` 

suggested in many threads, but it doesn't do shiz for me. all i get when i run it is a configuration for my keyboard. =o \

My set up is in my sig, and everything was fine before i tried that tutorial. I "fixed" one or two bits of it, but when i went in to xorg.conf file, under "device" there was no longer the line i added.

TBH, i skipped straight to the tutorial bit of the article, mainly because i've been unable to hibernate/suspend for so long and not gotten an answer/solution that when it was posted in my thread... oops.

---

### Post by LowSky on 2008-10-14
you need to reconfigure xorg, two ways to do so

1 nvidia-setting -- if you installed the propreitary graphics driver by using envy then it installed, careful to make changes you need to be sudo

2 boot into recovery mode and resetup xorg from there

---

### Post by joey-elijah on 2008-10-14
how do i re-set up xorg from recovery? Isn't recovery just a command line thing?

---

### Post by phidia on 2008-10-14
That guide you linked is for gutsy-are you using 7.10? I don't think so because the situation you described sounds a lot like hardy and the new xorg that comes with hardy.

Just because the dpkg command doesn't go through all the steps it did before doesn't mean it isn't trying to reconfigure your video. xorg is changed in hardy look at the [Ubuntu wiki]("https://help.ubuntu.com/community/Video") on that.

You can try "sudo dpkg-reconfigure -phigh xserver-xorg" but if you are using hardy you might be better off installing the driver from the [nvidia site]("http://www.nvidia.com/object/unix.html") or using [envyng]("http://albertomilone.com/nvidia_scripts1.html").

---

### Post by phidia on 2008-10-14
> **joey-elijah said:**
> how do i re-set up xorg from recovery? Isn't recovery just a command line thing?

If you have an internet connection in recovery mode you can try:
> sudo apt-get install nvidia-glx-177

That's the best driver for your 8 series cards available from the repos.

---

### Post by WWSmith36 on 2008-10-14
You can use a simple tool to reset you video setting.

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install displayconfig-gtk
```

Then to configure your monitor resolution:

```
sudo displayconfig-gtk
```

You can select your monitor from the list or add it by using the .inf file from driver disk or download. If the screen is too large to access buttons at the bottom, ALT+ LEFT CLICK will allow you to move the window.

Hope this helps

---

### Post by LowSky on 2008-10-14
> **joey-elijah said:**
> how do i re-set up xorg from recovery? Isn't recovery just a command line thing?

not since gutsy, things have changed consideribly

---

### Post by joey-elijah on 2008-10-14
i do already have EnvyNG installed, and had used that before everything went ... 

EnvyNG atm returns an error whenever i try and install the driver

I can't seem to copy and paste it, but there are a few pulse.py errors and raise exceptions... 

I know the guide is for Gutsy, but the reply in my thread said it'd work for Hardy so... i was niave...

I will try and do stuff from recovery right now..

---

### Post by joey-elijah on 2008-10-14
> **WWSmith36 said:**
> You can use a simple tool to reset you video setting.

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install displayconfig-gtk
```

Then to configure your monitor resolution:

```
sudo displayconfig-gtk
```

You can select your monitor from the list or add it by using the .inf file from driver disk or download. If the screen is too large to access buttons at the bottom, ALT+ LEFT CLICK will allow you to move the window.

Hope this helps

I had already tried that, but thanks. 

The only options i get when i select my monitor (1440x900) are 800x600 and 640x480.. which is too EeePC for my display lol!

---

### Post by augur80 on 2008-10-14
> **LowSky said:**
> you need to reconfigure xorg, two ways to do so

1 nvidia-setting -- if you installed the propreitary graphics driver by using envy then it installed, careful to make changes you need to be sudo

Did you try LowSky's suggestion of booting into the Low Graphics Mode and running nvidia-settings?  The latest version of Ubuntu (Hardy 8.04) uses XRANDR to setup Xorg graphics, but nVidia cards do not report all of the proper information that XRANDR queries and uses for automated setup.  Therefore, using nvidia-settings to setup the Xorg config should work just fine.  I had a lot of trouble setting up a dual display on an nVidia card until I found this bit of information. :(

---

### Post by joey-elijah on 2008-10-14
all solved.

I LOVE the new recovery mode btw. Via recovery i uninstalled EnvyNG completely via synaptic then reinstalled it, restarted and apart from having to manually adjust the resolution (which was now supported) and the refresh rate, it's awesome!

Thanks for your help guys n' gals!

---

### Post by joey-elijah on 2008-10-14
EDIT:

whenever i restart i seem to have to go through it all again. Install via EnvyNG > Restart > Manually configure resoultion.

Is there a way to get it to "stick", cos this is, tbh, an unusable set up.

---

### Post by phidia on 2008-10-14
Can you look at or post your xorg.conf when this happens?
 "cp /etc/X11/xorg.conf > /home/youruser/xorg.txt" should give you a text file.

envyng isn't saving your xorg.conf correctly perhaps? 

You could try installing the nvidia driver with apt-get (see my previous post here if you decide to try that).

---

### Post by gjoellee on 2008-10-14
have you tried running xfix? Read more: [http://www.kshoster.net/node/18](http://www.kshoster.net/node/18)

---

### Post by phidia on 2008-10-14
> **gjoellee said:**
> have you tried running xfix? Read more: [http://www.kshoster.net/node/18](http://www.kshoster.net/node/18)
 Thanks that's an excellent link. It would be great if there were a sticky with all the updated commands and methods for the new xorg.

---

### Post by gjoellee on 2008-10-14
> **phidia said:**
> Thanks that's an excellent link. It would be great if there were a sticky with all the updated commands and methods for the new xorg.

I will check that out ;)

---

### Post by joey-elijah on 2008-10-15
> **gjoellee said:**
> have you tried running xfix? Read more: [http://www.kshoster.net/node/18](http://www.kshoster.net/node/18)

hi, yeah has already run that as stated earlier (via recovery mode) but thanks

---

