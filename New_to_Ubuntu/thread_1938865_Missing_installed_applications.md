---
title: "Missing installed applications?"
date: 2012-03-10
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2012-03-10
If I open Applications/Ubuntu Software Center and search for a given applicaion, it might turn out to be installed by default, e.g. fancontrol. 

However when I click on the description it opens a larger description, but how do I actually start the program?

Or if it is already running, how do I see temperatures, etc

Or is the problem that my mobo doesn't provide sensor information? Is there a way to find that out without opening the case to get the mobo info?

Second issue is that I opened Places wanting to look at various directories to figure out where installed software resides in order to try to start fancontrol by clicking on it.

One of the things listed is > 454 GB Filesystem
All that it contains is lost+found. I clicked on this and it placed an icon on my desktop.

I think that this is an unused partition on my hdd. Does this sound correct, and if so, is there any reason not to right click and unmount it?

---

### Post by _0R10N on 2012-03-10
> **Odyssey1942 said:**
> If I open Applications/Ubuntu Software Center and search for a given applicaion, it might turn out to be installed by default, e.g. fancontrol. 

However when I click on the description it opens a larger description, but how do I actually start the program?

Or if it is already running, how do I see temperatures, etc

Or is the problem that my mobo doesn't provide sensor information? Is there a way to find that out without opening the case to get the mobo info?

Second issue is that I opened Places wanting to look at various directories to figure out where installed software resides in order to try to start fancontrol by clicking on it.

One of the things listed is 
All that it contains is lost+found. I clicked on this and it placed an icon on my desktop.

I think that this is an unused partition on my hdd. Does this sound correct, and if so, is there any reason not to right click and unmount it?

As you probably know, Ubuntu Software Center helps you install/uninstall applications, not to execute them.

Once an app is installed, the way you execute it depends entirely on the app itself. It might be a service, so it will be run automatically when the system starts up. It might be a desktop application (and you should be given an icon and/or a console alias to execute it), etc.

If you're experiencing problems to run a specific app, post its name.

---

### Post by stoneage on 2012-03-10
Maybe this will help:-
[http://ubuntuforums.org/showthread.php?t=1680730](http://ubuntuforums.org/showthread.php?t=1680730)

---

### Post by Odyssey1942 on 2012-03-10
Orion, thanks. For example, fancontrol. 

I have also installed computertemp (an applet) and put it on the panel. There is a big X through it, and if the mouse hoovers over it there is a message, "No thermal monitor support" That is why I asked about mobo support. Mine is a new mobo (MSI H67A-G43) and I would be very unpleasantly surprised it it does not have sensors. I have googled extensively, but the only thing I found was on the MSI website and it mentioned "Instant MB info monitor" but doesn't say what that is.

Stoneage,
thanks for the link. I ran the code shown
```
sudo apt-get install sensors-applet
``` and it asked if I wanted it to run at startup, but recommended to not do, so I said no. Apt-get finished its work and fancontrol remains in hiding.

It also said: 
> You might have to install lm-sensors. but what is an lm-sensor?

And > Fancontrol is a daemon that runs in the background and has no direct user interface.

All I want it to do is run in the background and maintain temps. Does he mean there is no visible instance of it and the user cannot set speeds?

---

### Post by wildmanne39 on 2012-03-10
Hi, yes you should install lm-sensors you can use the software center but then I believe you will have to use the terminal to set it up.
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

---

### Post by Odyssey1942 on 2012-03-11
Have been bashing away all day on the lm-sensors thing. It is incredibly complicated for something that worked right out of the box on my other 10.04 computer without needing any of this stuff I am wrestling with.

I have run so many commands I have completely lost track of where I am. Will someone give me some guidance on this?

Here is some output that might make some sense to someone:

> Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): 
Found unknown SMBus adapter 8086:1c22 at 0000:00:1f.3.
Sorry, no supported PCI bus adapters found.
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
Module i2c-dev loaded successfully.

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `lm78':
  * ISA bus, address 0x290
    Chip `National Semiconductor LM78' (confidence: 6)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
lm78
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)


I said yes, but still the computertemp applet on the panel shows a red cross through it.

After all this, I still don't understand whether or not there are sensors in my mobo, and if so, how to wake them up.

---

### Post by Odyssey1942 on 2012-03-12
Any ideas please?

---

### Post by Corvair on 2012-03-13
Try installing the following from Synaptic Package Manager.
It solved my problem


XSensor

---

