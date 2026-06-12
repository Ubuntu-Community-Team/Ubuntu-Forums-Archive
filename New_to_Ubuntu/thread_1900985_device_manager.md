---
title: "device manager"
date: 2011-12-27
forum: New to Ubuntu
---

### Post by JeremySchubert on 2011-12-27
Hello All, 
Using 11.10.  Initially downloaded CD and booted into test mode.  My dual monitors were recognized without issue.  Did some further testing and then made the leap to a fresh install.  Now my dual monitors are no longer recognized.  When I click on display settings (after clicking on the 'tiny gear' to the right of the time an my user name-is what's the proper name for that icon???) all I see is that my display cards are unrecognized.  I can go into something called restrictive drivers and it shows me that I need to download Nvida drivers, but that doesn't seem to be helping even after reboot.  

1.  How can I install a device manager like in Windoze so I can investigate further.
2.  If I use the 11.10 cd to reboot into test mode, how can I determine what drivers are being used for my card.
3.  How do I get to a command prompt (or whatever it's called in Ubuntu?

Thanks, Jeremy

---

### Post by TeoBigusGeekus on 2011-12-27
If you installed nvidia restricted drivers from Additional Drivers, press the Windows button on your keyboard and then type terminal.
Choose the terminal and start nvidia's app with
```
gksu nvidia-settings
```
Change your monitor configuration from there.

---

### Post by JeremySchubert on 2011-12-27
Wow, that was simple, thanks!

I take it that gksu stands for something like gnome kernal sudo?
How can I generate a list of other device settings I can access this way?

Jeremy

---

### Post by TeoBigusGeekus on 2011-12-27
> **JeremySchubert said:**
> 
I take it that gksu stands for something like gnome kernal sudo?


Something like this, yeah.

As for other settings, what did you have in mind?

---

### Post by grahammechanical on 2011-12-27
That icon in the top right-hand corner is called the power cog icon.

You can also install video drivers through a utility called Additional Drivers. You find it by opening the Dash by clicking on the Dash home icon (on top of the Launcher. It has also been called BFB = big funny button) and typing in the search panel ADD and you will see an icon for Additional Drivers.

As you have a Nvidia card and have installed a Nvidia driver for it then open the Dash and type Nvidia and you can get access to the Nvidia X-Server Settings Manager. That is a useful utility to be familiar with. The installation of the Nvidia X-Server Setting Manager disables the System Settings Displays utility. That is why it says Monitor Unknown.

One day we will have open source video drivers that do a better job than the proprietary drivers from Nvidia and others and then the Displays Utility will be useful.

Regards.

---

### Post by JeremySchubert on 2011-12-27
Graham - thanks for the further explanations.
Teo - specifically I'd like to know how to configure my NIC and audio devices (onboard sound and USB head set) and my Dazzle DVC 100 (a device that lets me connect VCR etc to the computer.

---

### Post by Mark Phelps on 2011-12-27
> **JeremySchubert said:**
> ...specifically I'd like to know how to configure my NIC and audio devices (onboard sound and USB head set) and my Dazzle DVC 100 (a device that lets me connect VCR etc to the computer.

Any devices that connect via USB are most likely NOT going to be configurable -- if you had to install special drivers in Windows to configure them. You need to understand that lack of specialized device drivers is a known weakness of using Linux distros.

Onboard sound will need drivers (supplied using ALSA or OSS) but once again, sound apps that came with the device in Windows are not going to be installable in Linux.

---

