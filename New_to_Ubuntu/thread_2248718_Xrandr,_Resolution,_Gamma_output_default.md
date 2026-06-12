---
title: "Xrandr, Resolution, Gamma output default"
date: 2014-10-16
forum: New to Ubuntu
---

### Post by Weenshent on 2014-10-16
I am new to Ubuntu (previously running Windows 7). I am currently running Ubuntu 14.04 and trying to set my screen resolution to 1920x1080. I followed the instructions provided for changing your resolution to an undetected resolution. After typing in xrandr into the terminal, I get the message xrandr: Failed to get size of gamma for default output and prevents me from setting the appropriate resolution. I have been researching for a solution to this but I have been unable to. I am wondering if anyone has an updated solution or has encountered this issue and found a way to resolve this.

---

### Post by Vladlenin5000 on 2014-10-16
Hi, welcome.

Sorry, not enough information, not even close...

Graphics card/chip?
How is the monitor connected?

---

### Post by Weenshent on 2014-10-16
Ah, my apologies.
I am operating this on a Dell XPS-15Z laptop.

00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
    Subsystem: Dell Device [1028:0446]
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108M [GeForce GT 525M] [10de:0df5] (rev a1)
    Subsystem: Dell Device [1028:0446]
Is this what you were looking for? Is there anything else you need?

---

### Post by Vladlenin5000 on 2014-10-16
Yes, better, thank you :p

You need proprietary nvidia drivers... Assuming you're running standard Ubuntu, go to System Settings > Software&Updates, find and click in the righmost tab "Additional Drivers", wait a few seconds for results and select the recommended driver version. It will then download and install automatically. Reboot.
Considering you have hybrid (Intel + Nvidia) graphics you also need something else: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by Weenshent on 2014-10-16
Update: 
Yes I am using standard Ubuntu (sorry! didn't know there was a tag for this)
I downloaded and applied the recommended driver version that was given, "Using NVIDIA binary driver - version 331.38 from nvidia 331 (proprietary, tested)".
Upon the reboot I would be brought to the login screen and Unity would freeze after the login process and the screen would be stuck there (functional mouse and keyboard). I looked it up and followed the instructions here [http://itsfoss.com/fix-unity-freezes-after-login-ubuntu-14-04/](http://itsfoss.com/fix-unity-freezes-after-login-ubuntu-14-04/) . However, following these instructions, from my understanding, removes the download and installation of the drivers. Do I need the Bumblebee setup done beforehand?

UPDATE2 
I have successfully installed the driver, and setup Bumblebee and rebooted propely without freezing at Unity. Are there any further steps or can I begin setting the undetected resolution from this point?

---

### Post by Vladlenin5000 on 2014-10-16
It should be safe to try. Yes, it'll remove the nvidia drivers but the note below the procedure also mentions that you should install them again. I'm not sure whether or not such part of the procedure - uninstall/install nvidia drivers - is still necessary.
I suggest you try first just reinstalling ubuntu-desktop/unity first.

---

### Post by Weenshent on 2014-10-16
I've uninstalled and reinstalled the nvidia drivers and set up the Bumblee portion as well. After rebooting my laptop it seems as though nothing has changed and I continue to have the issue where I'm failing to obtain the gamma size for the output. 
Another question, when I installed Ubuntu, my research advised me to install with nomodeset enabled. So I found that [SIZE=2]
[B]
"nomodeset[/B][/SIZE]
The newest kernels have moved the video mode setting into the kernel.   So all the programming of the hardware specific clock rates and  registers on the video card happen in the kernel rather than in the X  driver when the X server starts.. This makes it possible to have high  resolution nice looking splash (boot) screens and flicker free  transitions from boot splash to login screen. Unfortunately, on some  cards this doesnt work properly and you end up with a **black screen**. Adding the_*** nomodeset parameter instructs the kernel to not load video drivers and use BIOS modes instead until X is loaded."***_

Is that last sentence my issue right now? If so, how do I change this in my installed Ubuntu kernel?

---

### Post by Vladlenin5000 on 2014-10-16
You shouldn't have to use xrandr now that you have the drivers working. Either at System Settings or at the "NVIDIA X Server Settings" the full HD resolution should be selectable.

---

### Post by Weenshent on 2014-10-16
[http://imgur.com/hacnPt5](http://imgur.com/hacnPt5)
I don't understand, they are in neither of the options and it is not possible for me to change the resolution appropriately? I don't know what the issue is..

---

### Post by Vladlenin5000 on 2014-10-16
I wouldn't expect it to work either **without **nvidia drivers... We already know the open source 'nouveau' driver isn't enough for your system.

---

### Post by tgalati4 on 2014-10-16
Are you using a DVI cable?

---

### Post by Weenshent on 2014-10-16
I'm sorry, I'm confused. Is the current binary driver that I have enabled not the correct nvidia driver you mentioned before?

---

### Post by Weenshent on 2014-10-16
I only have a laptop that I am using; if that answers your question (?)

---

