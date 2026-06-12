---
title: "Command line to check drivers returns nothing"
date: 2015-01-05
forum: New to Ubuntu
---

### Post by jan_jan_64 on 2015-01-05
Hello. I recently made a fresh install of my system (running ubuntu 14.04) because of a lot of trouble I had updating my driver after installing a new graphics card. Now, everything is running almost fine, but still having some issues running Steam and some movies in VLC. So I wanted to check what drivers I have installed currently, and trying to see if I can make the upgrade to a new driver work this time. I ran the command:   
sudo ubuntu-drivers devices
But after putting in my password, it returns absolutely nothing. Am I doing something wrong? I have a strong suspicion I am running with nouveau right now but dont seem to be able to check..

---

### Post by grahammechanical on 2015-01-05
> [COLOR=#000000] I ran the command: [/COLOR]

What command? The Details page in About This Computer will say what driver you are using. If it says Gallium, then you are running the open source video driver. In System Settings>Software and Updates>Additional Drivers tab we get a list of all available video drivers. We need to be connected to the internet and we need to give the utility time to find the drivers. The driver that is activated will be marked.

Regards.

---

### Post by ibjsb4 on 2015-01-05
I think you looking for the "k" switch.
```
lspci -k
```
Should tell you the driver your running.
```
man lspci
```

---

### Post by jan_jan_64 on 2015-01-05
@grahammechanical:
Yes I just realised I missed the command line in my post originally - I edited it in afterwards, it is:

sudo ubuntu-drivers devices

which I took from an Ubuntu online help page (and was told to me in a previous post also). Im not sure of About This Computer, but I found the Details section in the System Settings. It does not list my graphics card or the driver currently installed, just my RAM, processor etc. I could not find the "About" section you referred to.

@ibjsb4:
I ran "lspci -k" - a kernel driver was listed for everything EXCEPT for my graphics card. Specifically:

"01:00.0 VGA compatible controller: NVIDIA Corporation GM107 [GeForce GTX 750 Ti] (rev a2)
    Subsystem: Device 196e:1380"

And thats all.

---

### Post by Bashing-om on 2015-01-05
jan_jan_64; Hello;

Now that last is useful info:
> 
"01:00.0 VGA compatible controller: NVIDIA Corporation GM107 [GeForce GTX 750 Ti] (rev a2)

And the situation is that the card is new and there are no drivers available to this time in the software repository.
There are options: see:
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)
[http://ubuntuforums.org/showthread.php?t=2257506](http://ubuntuforums.org/showthread.php?t=2257506)

The recommended 1st solution is to obtain the driver from an ubuntu PPA:
[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

