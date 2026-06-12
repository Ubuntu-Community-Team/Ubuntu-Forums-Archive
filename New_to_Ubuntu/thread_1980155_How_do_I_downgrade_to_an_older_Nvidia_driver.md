---
title: "How do I downgrade to an older Nvidia driver?"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by greenelf on 2012-05-14
I am currently using the latest nvidia driver, and I am finding that it is causing me a LOT of problems (3D desktop crashing). I read somewhere that downgrading to an older nvidia driver should do the trick.
Graphics card name:  AMD Sempron(tm) Processor LE-1300
I am currently running 12.04, on a 64bit machine. I want to install this driver:
[h]("https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/290.10-0ubuntu2")[ttps://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/290.10-0ubuntu2]("https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/290.10-0ubuntu2")
or this one: [https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/280.13-0ubuntu6.1](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/280.13-0ubuntu6.1)
How can I install this?

---

### Post by PhantomTurtle on 2012-05-14
That's your processor listed there. Do you have integrated AMD Graphics? Or do you have an NVidia video card. Either way if you want to downgrade a driver you remove the current one using the Additional Drivers utility(jockey-gtk) and then you remove your currently installed drivers. Then you restart, open the Additional drivers utility and install the correct driver and then restart again. Then Ubuntu should start using that driver.

---

### Post by greenelf on 2012-05-14
> **PhantomTurtle said:**
> That's your processor listed there. Do you have integrated AMD Graphics? Or do you have an NVidia video card. Either way if you want to downgrade a driver you remove the current one using the Additional Drivers utility(jockey-gtk) and then you remove your currently installed drivers. Then you restart, open the Additional drivers utility and install the correct driver and then restart again. Then Ubuntu should start using that driver.

Oops. My card is GeoForce 6150SE nForce 430. 
(Not on ubuntu at the moment) So I would type in jockey-gtk in terminal, and it would open up a list of drivers I can install? I'm having trouble *downloading* the driver.

---

### Post by PhantomTurtle on 2012-05-14
> **greenelf said:**
> Oops. My card is GeoForce 6150SE nForce 430. 
(Not on ubuntu at the moment) So I would type in jockey-gtk in terminal, and it would open up a list of drivers I can install? I'm having trouble *downloading* the driver.

You can search for additional drivers in the dash or open it in terminal with jockey-gtk. jockey will download and install or remove the driver for you. So all you have to do is select which version of the driver you want.

---

### Post by Jurjen de Vries on 2012-05-15
Which nvidia driver version are you using?
I have the same problem (x crashed randomly when I am using it within 5 till 30 minutes) since updated to nvidia version 295.49 at my 12.04 64 bit system.

Only topic that I could find about it is this one, so I reported a bug about it at [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/999984](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/999984) . If you think you have the same bug, please click the link that it affects you at that bug report page.

---

### Post by markbl on 2012-05-15
X has always been stable for me but crashes on all versions (295.40, 295.49, and 302.07) in ubuntu 12.04 as I described [here](https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/982485/comments/136).

At least try the free nouveau driver first. It is working well for me. Just open up "Additional Drivers" in settings (i.e. "jockey-gtk") and deactivate the proprietary driver. Nouveau should be used next reboot.

---

### Post by Jurjen de Vries on 2012-05-17
@markbl , last time I did a deinstallation of the nvidia driver, my screen resolution was 640x480, and could'nt change it to something else. Does that mean that the nouveau driver was not activated? How can I check this?

At this moment I am using the 2D desktop version.

---

### Post by markbl on 2012-05-17
> **Jurjen de Vries said:**
> @markbl , last time I did a deinstallation of the nvidia driver, my screen resolution was 640x480, and could'nt change it to something else. Does that mean that the nouveau driver was not activated? How can I check this?


I'm not an expert on this but you may have an nvidia tainted configuration stored in your /etc/X11/xorg.conf which is affecting the non-proprietary driver. Modern Xorg software doesn't really need that file anymore so start by deleting that file (or at least moving/renaming it away). Also delete or move ~/.config/monitors.xml and then reboot. After you system comes up then try configuring it via settings/displays.

If you only get a text screen and you want to put the nvidia driver back then you can run "sudo jockey-text --help".

---

### Post by Jurjen de Vries on 2012-05-19
@Markbl
I follow your instructions. But at this time no higher resolution then 1024x768. Normally I have 1920x1080.
Also my dual monitor setup is not working anymore.
The CRTL-ALT-F1 for a terminal is also not working anymore.
If I am going to system configuration > display, no options for a higher resolution or dual monitor. My monitor is seen as a laptop monitor, but it is not.

I decided to reinstall the latest NVIDIA driver, and from there I did a downgrade to an older driver.

Thank you anyway for your suggestions.

---

### Post by wildmanne39 on 2012-05-19
Hi, I have the same card and I found that ubuntu 12.04 installs the latest nividia driver by default if you have an intertnet connection and the 173 driver will not install in 12.04 so I uninstalled the current nvidia and switched to the open source nouveau driver and now it works good.
Thanks

---

### Post by Jurjen de Vries on 2012-05-19
@wildmanne39 . Did you do something special, or only deinstall the nvidia driver? When I remove the nvidia driver, I only get a low resolution desktop.
How to check of nouveau driver is active?

---

### Post by wildmanne39 on 2012-05-19
Hi, I uninstalled the nvidia driver then installed nouveau driver using synaptic but it is not installed by default in ubuntu either so you can use the software center, here is a screenshot that shows the packages I have installed.

If you want 3d effects I believe you have to install the first package that is highlighted in my screenshot in orange.

If you have the nvidia driver working well I would just leave it.
Thanks

---

### Post by Jurjen de Vries on 2012-05-19
Resolution is working fine now with the nouveau firmware, thanks!
Dual monitor still not working with nouveau driver. Only 1 screen (labeled 'laptop').

---

### Post by wildmanne39 on 2012-05-19
Hi, your welcome! I do not know anything about dual monitors so I am going to leave that to someone else.

---

### Post by Jurjen de Vries on 2012-05-19
I got it fixed, by reading [http://nouveau.freedesktop.org/wiki/Randr12](http://nouveau.freedesktop.org/wiki/Randr12)
I found a backup of the nvidia driver xorg.conf file, and used the information in there for the new xorg.conf file :-)
Hope it will stay stable now, will let you know.

---

