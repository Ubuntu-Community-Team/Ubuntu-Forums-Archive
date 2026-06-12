---
title: "Glitchy graphics/Black Screen on startup."
date: 2013-03-01
forum: New to Ubuntu
---

### Post by Vafele on 2013-03-01
First time I'm using Linux, so pardon me if this turns out to be too obvious. I also rarely post on any kinds of forums but I've tried googling the hell out of my problem to no avail.

Alright, now about the issue I'm having.

At first, after I installed ubuntu (12.10) for the very first time, I had all kinds of weird graphics artifacts and glitches. Sometimes I couldn't login, it would just loop me back to the login screen all the time. If I somehow managed to log in (Don't ask, I can't replice the log in thing now, no idea how I got it), what I got was a completely corrupted screen. It's like the desktop started loading - I could see the whole sidebar thing, but clicking anything did nothing at all, and then it just went corrupt. The top side was all covered in black squares through which, I think, I could read the words login and password. Well, anyways, using the nomodeset option in GRUB seemed to help, it was slow, but I managed to get in and successfully (or so I thought) download the proprietary drivers.

After doing that, I got a new type of issue. On boot the screen flashed purple and then went black with the command-cursor thing blinking on the left side constantly. This is what has so far happened with any Nvidia drivers that I've tried using. The nouveau drivers on the other hand give me the corrupted screen thing and only work with nomodeset (or classic mode in 12.04, which I also tried installing). The nomodeset mode doesn't work when I'm using the Nvidia drivers.

I'm not at the computer that is experiencing the problem right now, so I don't really remember the specs in details, but I just had to post this before I go to bed or I'll go insane, so here are the specs:
Videocard - 8800gtx
Processor - Core2Duo, don't really remember the exact model
4 gigs of ddr2 ram

I'd greatly appreciate any ideas. I'll try everything out, even though I've tried many of the suggestions that I've found through google, most of the time I had only a very approximate idea of what I was actually doing, so I'll try out any possible solution.
Thanks.

---

### Post by carl4926 on 2013-03-01
Normally, all that is required for nvidia drivers is

```
sudo apt-get install nvidia-current
```

---

### Post by squakie on 2013-03-01
With NVidia cards, it also VERY common to need to add the nomodeset option on the boot line.  If you search you will find lots of posts for this in the forum.  If you need help, post back.  There may also be some other settings that need to change.

---

### Post by Vafele on 2013-03-04
On my 12.04 installation, when I try downloading drivers through the terminal by using sudo apt-get install nvidia-current, I get this:

The following packages have unmet dependencies:  nvidia-current : Depends: xorg-video-abi-11                   Depends: xserver-xorg-core (>= 2:1.10.99.901)

After that I tried updating my drivers through the Additional drivers updater and selecting the nvidia accelerated graphics driver (post release updates) (version 173-updates). It downloads the drivers, I restart the PC and after that, just as before, I get the black screen with the command cursor and that's it.

About the nomodeset - I'd love to avoid that, since I think that I get quite the performance hit when using it.

---

### Post by carl4926 on 2013-03-04
> [COLOR=#000000]version 173-[/COLOR]
Is the wrong driver for your device

For me it's install > ```
sudo apt-get update && upgrade
```
reboot

```
sudo apt-get install nvidia-current
```

---

### Post by Vafele on 2013-03-04
Did that, I still get this:
The following packages have unmet dependencies:  nvidia-current :  Depends: xorg-video-abi-11                   Depends: xserver-xorg-core  (>= 2:1.10.99.901)

---

### Post by carl4926 on 2013-03-04
> **Vafele said:**
> Did that, I still get this:
The following packages have unmet dependencies:  nvidia-current :  Depends: xorg-video-abi-11                   Depends: xserver-xorg-core  (>= 2:1.10.99.901)
I can't check this ATM as I'm on a Laptop with Intel
But I can't think what must be wrong? I have not noticed any funny business.

Perhaps someone else will chirp up

---

### Post by squakie on 2013-03-05
Since it's a new install, you don't have much to lose.  I would try to collect the dependencies for NVidia-current via:  sudo apt-get build-dep nvidia-current (I *think* it's build-dep, it might be build-dependencies, but I don't think so).  The re-try your sudo apt-get install nvidia-current.  While I know you want to avoid it, nomodeset is often used on NVidia adapters.  It is basically telling the kernel not to set the video config automatically.  This seems to work fine with me and many others with no visible performance hit.

---

### Post by Vafele on 2013-03-06
Alright, that worked, I managed to install the drivers. On restart though I got a purple screen this time, not the black one with the cursor. Also, I actually managed access the terminal with the ctrl-alt-f1, which I couldn't do before. But that's all I got, still unable to fully boot into the system with the nvidia drivers.

---

