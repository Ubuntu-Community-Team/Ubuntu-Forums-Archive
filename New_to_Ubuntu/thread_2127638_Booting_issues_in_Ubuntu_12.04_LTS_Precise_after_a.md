---
title: "Booting issues in Ubuntu 12.04 LTS Precise after an update"
date: 2013-03-20
forum: New to Ubuntu
---

### Post by uberdoc on 2013-03-20
Hi,

I am fairly new to Ubuntu (and to this forum as well) so please allow me to be clueless.  I recently installed the precise 12.04 LTS (alongside windows) in one of my older desktops (asrock chipset mobo, P4 2.4GHz CPU, onboard intel graphics, 1 GHz ram).  I am using the Gnome classic DE and had set the OS to automatically update.  Yesterday the OS downloaded and installed updates as usual and asked for a reboot...and I complied...however ubuntu refused to boot since then...the grub menu would appear (without the timeout countdown which was earlier set at 5s) and on pressing enter a purple screen would appear momentarily followed by a black screen with a blinking cursor at the left upper corner of the screen.   I could boot to the windows installation though and could also boot using a live usb.  I googled without any luck...finally I partially solved the problem (serendipitously?) by finding that the linux version in the grub menu had changed to   3.5.0-26-generic from the previous 3.5.0-25-generic...I located the previous linux version in the "previous linux installations" item in the grub menu and booted to that without any issues.

My question now is this:  how can I make the 3.5.0-25-generic my default version? also can I safely remove the latest version of linux i.e., 3.5.0-26, if so how?  Also how can I prevent ubuntu from updating to this latest version during future automatic updates (as it seems that the latest version is not compatible with hardware (graphics etc) of my desktop and the 3.5.0-25 seems to be stable on my pc and is kind of working for me now)?

Thanks in advance

---

### Post by ibjsb4 on 2013-03-20
First just to be sure your running the kernel (3.5.0-25) you want to keep.

```
uname -r
```

To remove that one kernel:

```
sudo apt-get remove --purge linux-image-3.5.0-26-generic
```

There are ways to lock the kernel version, but the easy way is just to update/upgrade in terminal.

```
sudo apt-get update && sudo apt-get upgrade
```

This will upgrade your other packages, but will not upgrade the kernel.

And last, remove auto-update in software sources.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Updates_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Updates_Tab)

If you want full control over updates and just about everything else concerning package management (update/removal/depends/files installed ...).

You may want to start using Synaptic Package Manager.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

[ATTACH=CONFIG]240385[/ATTACH]

---

### Post by uberdoc on 2013-03-21
@ibjsb4 thanks a million for your suggestion...I'll try them and get back with the results.

---

### Post by tancrackers on 2013-03-21
Go to Software Sources and go to the Updates tab, you have an option at the bottom if you want to prevent future updates of Ubuntu. "Notify me of a new version of Ubuntu" with a dropdown menu.

---

### Post by mastablasta on 2013-03-21
but otherwise this shouldn't happen to users. so you could try removing the kernel and then updating it again.

---

### Post by deadflowr on 2013-03-21
> **tancrackers said:**
> Go to Software Sources and go to the Updates tab, you have an option at the bottom if you want to prevent future updates of Ubuntu. "Notify me of a new version of Ubuntu" with a dropdown menu.

Selecting this doesn't prevent updating, but rather prevents the version from upgrading.

To the op, it looks like your system is running the quantal kernel, so you either installed the quantal-LTS kernel or your system upgraded to the quantal release.
Either option would have been something you would have had to have been fully aware of.
But that is neither have nor there.
Look at this for how to set grub to use the last session used by default:
[http://www.dedoimedo.com/computers/grub-2.html#mozTocId624480](http://www.dedoimedo.com/computers/grub-2.html#mozTocId624480)

---

### Post by uberdoc on 2013-03-21
@ibjsb4 

Ok so I did all that...and now the grub is back to normal behavior...it waits for 5s and boots to the 3.5.0-25...so thats solved...thanks again

> And last, remove auto-update in software sources.

auto-update was never enabled since installation...software center offered updates and I installed them...only I did not know it was upgrading my kernel too...guess I'll have to be watchful henceforth.

> You may want to start using Synaptic Package Manager.

did that.

@others
thanks guys appreciate your taking time off to reply

---

### Post by ibjsb4 on 2013-03-21
Welcome :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

