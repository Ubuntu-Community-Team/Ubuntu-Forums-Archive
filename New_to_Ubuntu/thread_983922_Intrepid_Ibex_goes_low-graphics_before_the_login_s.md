---
title: "Intrepid Ibex goes low-graphics before the login screen"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by kdardio2415 on 2008-11-16
Hey guys, having a bit of a problem with Intrepid here.  When I boot up, things seem to go well through the Ubuntu loading screen.  Then everything goes black for a few seconds, and I get an error message

Ubuntu is running in low-graphics mode
The following error was encountered.  You may need to update your configuration to solve this.

(EE) GARTinit:  Unable to open /dev/agpgart (no such file or directory)
(EE) [drm] drmOpen failed.
(EE) intel(0):  [dri] DRIScreeninit failed.  Disabling DRI.
(EE) intel(0):  Failed to allocate framebuffer.  Is your VideoRAM set too low?
(EE) intel(0):  Couldn't allocate video memory

Additionally, both the mouse and keyboard cease to function.  I'm working from my notebook right now, so it's no emergency, and everything important is backed up, but if anyone has advice for a permanewb that would be spectacular.

Thanks for everything.

---

### Post by Peter09 on 2008-11-16
As a First Pass at configuring your Video Driver:
Boot into recovery mode and select 'xfix' from the menu, this may resolve it.

---

### Post by PmDematagoda on 2008-11-16
If possible, can you post the output of:-
```
cat /etc/X11/xorg.conf
```

---

### Post by kdardio2415 on 2008-11-16
> **Peter09 said:**
> As a First Pass at configuring your Video Driver:
Boot into recovery mode and select 'xfix' from the menu, this may resolve it.

xfix doesn't seem to have done anything, I got the same error message and couldn't work the mouse or keyboard.

> **PmDematagoda said:**
> If possible, can you post the output of:-
```
cat /etc/X11/xorg.conf
```

ran it in the root cli,and could only get the following back:  (note, the entire message was not displayed, this is exactly as it appears on my monitor)

```

#if it has not been modified since the last upgrade of the x
#package.
#
#Note that some configuration settings that could be done pr
#in this file, now are automatically configured by the serve
#here are ignored.
#
#If you have edited this file but would like it to be automa
#again, run the following command:
#     sudo dpkg-reconfigure -phigh xserver-xorg 

Section "Device"
     Identifier     "Configured Video Device"
Endsection

Section "Monitor"
     Identifier     "Configured Monitor"
Endsection

Section "Screen"
     Identifier     "Default Screen"
     Monitor        "Configured Monitor"
     Device         "Configured Video Device"
Endsection
```

---

### Post by Pezhead on 2008-11-16
This is almost the same thing that happened to me.  When you go to low graphics mode is it only text like terminal?

---

### Post by kdardio2415 on 2008-11-16
no, it's just that error message.  I've been tampering around with it, and can alt-f6 into a terminal, but no dice with startx or anything.

My error message is just a box with the cursor hanging over it.  It's got the message to in my first post and an "OK" button.

---

### Post by Pezhead on 2008-11-16
The reason I asked was because I have an nvidia graphics card and I got stuck in low graphics mode and had to re-format my machine (however I had no desktop.  I was stuck in terminal).

---

### Post by gjoellee on 2008-11-16
Have you tried running "xfix"? Read how here: [http://kshoster.net/node/18](http://kshoster.net/node/18)

---

### Post by kdardio2415 on 2008-11-16
> **gjoellee said:**
> Have you tried running "xfix"? Read how here: [http://kshoster.net/node/18](http://kshoster.net/node/18)

Still no luck with xfix.  It seems to do something, and returns to the recovery mode options, but resuming a normal boot just returns me to the error message.

---

### Post by alienexplorers on 2008-11-16
try running nvidia-xconfig.....

---

### Post by kdardio2415 on 2008-11-16
```

kdardio@kdardio-desktop:  sudo apt-get install nvidia-xconfig

```

it says it can't fetch some archives, suggests apt-get update.

apt-get update is unable to fetch some archive and suggests apt-get update.

ell oh ell.

---

### Post by PmDematagoda on 2008-11-16
> **kdardio2415 said:**
> ```

kdardio@kdardio-desktop:  sudo apt-get install nvidia-xconfig

```

it says it can't fetch some archives, suggests apt-get update.

apt-get update is unable to fetch some archive and suggests apt-get update.

ell oh ell.

You are using an Intel VGA card, aren't you?

---

### Post by kdardio2415 on 2008-11-17
I run a preassembled desktop running an integrated graphics solution.  Nothing fancy going on here.

---

### Post by Peter09 on 2008-11-17
Before going much further can you run the following terminal command and post its output here

```
lshw -C display
```

This should confirm the type of video chip you have.

---

### Post by kdardio2415 on 2008-11-17
> **Peter09 said:**
> Before going much further can you run the following terminal command and post its output here

```
lshw -C display
```

This should confirm the type of video chip you have.

```

 *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0

```

I reinstalled hardy on my main computer, and I'm installing Intrepid on a separate partition until this problem gets sorted out.

Edit:  Okay, I have installed Intrepid on a different partition and it works fine.  I guess there was a conflict with the old packages on my Hardy or something.  If anyone figures it out, that would be great, but it's no longer an immediate problem for me.

---

### Post by Tocci on 2008-11-18
> **PmDematagoda said:**
> You are using an Intel VGA card, aren't you?

I am having the same low graphics issue and it is on an Intel card.  Is there a known issue.  I can't find a solution anywhere.  The same machine is running Hardy with no issues.  Any help would be great! Thanks.

---

