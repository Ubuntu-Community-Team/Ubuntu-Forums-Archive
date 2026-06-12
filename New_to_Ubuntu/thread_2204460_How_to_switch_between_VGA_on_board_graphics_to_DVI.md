---
title: "How to switch between VGA on board graphics to DVI GPU"
date: 2014-02-08
forum: New to Ubuntu
---

### Post by maazmahmood on 2014-02-08
Is there a way to do that from ubuntu? Or does it have to be from the BIOS? I have yet to install drivers (Nvidia 9800 GTX+). But when I do, can I simply just unplug VGA and plug in DVI?

---

### Post by grahammechanical on 2014-02-08
If the graphics adapter has a port and the monitor has a port then all you need is the right cable. Just connect the DVI port on the graphic adapter to the DVI port on monitor and things will work. This is all I do. The same applies to HDMI. And this will also work with the Nouveau open source video driver.

Regards.

---

### Post by Vladlenin5000 on 2014-02-08
You usually need to select in BIOS and connect it accordingly. You can select the nVIDIA card from the start because it should work fine with the open source driver. You can then go Programs > Additional drivers and select and activate the recommended proprietary driver.

---

### Post by Mark Phelps on 2014-02-08
It actually depends on the BIOS on the motherboard.  I recently changed from onboard graphics to a video card -- and in the BIOS, I had to disable the onboard graphics before the card would work.  That's tricky because you have to disable the onboard graphics, shut down, insert the video card, and reboot.

With any recent AMD or Nvidia card, when you reboot, Ubuntu will setup the default drivers -- so you should get a desktop without any problems.

You can then use Additional Drivers to install restricted drivers.

---

### Post by maazmahmood on 2014-02-09
> **Vladlenin5000 said:**
> You usually need to select in BIOS and connect it accordingly. You can select the nVIDIA card from the start because it should work fine with the open source driver. You can then go Programs > Additional drivers and select and activate the recommended proprietary driver.


Hmm, will I have to install drivers before after?

---

### Post by Vladlenin5000 on 2014-02-09
No, that's what we've been telling you. You can, if you want, install proprietary drivers after but it'll work right away with the open source one.

---

### Post by maazmahmood on 2014-02-09
Well I selected in BIOS, and it's not loading up, keeps going back to the integrated, how do I DISABLE the integrated?

And how exactly do I get the open source drivers? Those should already be in there right?

---

### Post by maazmahmood on 2014-02-09
And i've tried to download the drivers from nvidia. And it keeps saying my GPU is not supported when it is a 9800 GTX+ and I found it THROUGH nvidia

---

### Post by Vladlenin5000 on 2014-02-09
How do you disable the integrated? Well, probably in BIOS in the same place you select which one the system starts with. Usually there's no need to disable but, as Mark commented above, sometimes you need to otherwise the add-on card won't work. Most motherboards/BIOS just look for a PCI-e card when that is select as the primary and when not finding one they just default for the onboard, no further configuration needed.

What is your motherboard, by the way? Knowing that might be useful for further troubleshooting.

---

### Post by Vladlenin5000 on 2014-02-09
> **maazmahmood said:**
> And i've tried to download the drivers from nvidia. And it keeps saying my GPU is not supported when it is a 9800 GTX+ and I found it THROUGH nvidia

DON'T do that. As explained before (and more than once) just boot the system normally - it'll work with the driver it already has - and then, only if you want/need
, you can go to system settings -> software&updates -> additional drivers where you can select the recommended nvidia proprietary driver, wait for the (automatic) download and (automatic) activation then reboot. That's it!

Follow the instructions of the chapter 2 here: [http://www.omgubuntu.co.uk/2013/10/10-things-installing-ubuntu-13-10](http://www.omgubuntu.co.uk/2013/10/10-things-installing-ubuntu-13-10)

---

### Post by maazmahmood on 2014-02-09
Ok, sorry. But for the record I am using xubuntu as this is an older system. And I tried going to Additional Drivers MULTIPLE times. And it says theres nothing there for me, is there any way to check which open source drivers for nvidia are on, and if not how to get open source driver?

And this is the motherboard **Intel (Schroeder Town) G33 Motherboard**

---

### Post by Vladlenin5000 on 2014-02-09
A few comments/questions:

1. Do you still have the VGA cable connected to the onboard VGA? If so, don't. That might be the reason why your BIOS keeps defaulting to the onboard one...
2. Ok, Xubuntu is fine, any other flavor is fine as well. But what version? Aren't you by any chance using an old already unsupported version? (regular non-LTS version are supported for up to 9 months only; LTS versions have support for up to 5 years...)
3. Intel G33 is the motherboard's chipset. I asked the brand/model. This is just to check its user's manual - assuming I can find it online - in order to give you precise instructions on how to properly select the nvida add-on card.

---

### Post by maazmahmood on 2014-02-09
Using the latest, 13.10. 
And yes, I just tried unplugging VGA cable, it worked. Sorry for the hard time, still getting used to the whole Windows--> Linux phase, and correct forum detail. 

But what's wrong with getting drivers from nvidia, wouldn't it be more efficient if I get those?

Like I just tried launching DOTA 2, and I kept getting screen flickers

---

### Post by Vladlenin5000 on 2014-02-09
For the record, your issue has little to nothing to do with operating systems ;) but I'm glad you figured it out in the end.

The major problem with getting the drivers from nvidia is you'll end up with a script that need to be run without any graphical interface. Surely you understand that's not, by far, the easiest to install something, especially for someone just beginning with Linux. The method I suggested, on the other hand, should get you the recommended (and tested) nvidia drivers for your card and your xUbuntu version in just a matter of minutes.

PS - Over the years I've noticed that one of the major roadblocks people in your situation feel is the (perfectly understandable) "Windows mentality", the urge to apply the philosophy, methods, routines, "how-to's...", whatever... they learned before in their new OS. Most of the times it doesn't work; sometimes it end up in really bad results.
You're used to just go to nvidia's website, download the drivers for Windows, run the installer like any other app, clicking "next" almost blindly a few times, reboot when asked to, right? Well, you no longer need to do all this. Ubuntu in this matter and many others makes life EASIER for users.

---

### Post by maazmahmood on 2014-02-09
Yeah, I've noticed to learn a new OS, you must forget EVERYTHING you know about OS pretty much. So how should I go about getting the recommended/tested drivers for the card?

---

### Post by Vladlenin5000 on 2014-02-09
Now that you're working with the nvidia card you can follow the procedure I already mentioned. Now some options will appear in the "additional drivers" and you probably should choose the recommended (tested) one, whatever that version might be.
The reason why there was nothing before is because you were using the onboard Intel graphics card and this doesn't need any additional drivers. The Intel drivers are open source and already included in the distro; nvidia's are proprietary therefore not included by default and the open source alternative 'nouveau' driver is included instead. It works but it still has many issues with HDMI output, issues recognizing certain monitors/resolutions and generally not recommended for gaming and even HD video.

---

### Post by maazmahmood on 2014-02-09
Thanks for all your help :)

---

### Post by Vladlenin5000 on 2014-02-09
Pleas mark the thread as solved. Use the thread tool in the first post. Thank you.

---

