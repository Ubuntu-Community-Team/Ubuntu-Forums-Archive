---
title: "DPKG and &quot;Depencies&quot; woes"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by nofare on 2008-09-12
Hello,

(Disclaimer: I spent the last few days reading notes on various Ubuntu and Linux forums, to try and figure out if I could deal with the issues I'm facing now on my own, but none of the things I've applied to the problem seem to have done anything to fix it. Hence my posting this today).

I'm totally new to Linux and Ubuntu. But I figured I'd try it on an old laptop of mine, to explore it on my off-hours (the laptop in question is a Dell Latitude C400.)

Since I don't have a CD Drive in it, and since I can't install Ubuntu from an external drive either (the computer is that primitive), I decided to do everything via the Internet.
I think everything was going smoothly until the system started to upgrade to the current Ubuntu version: since the whole thing took a little while to start rolling (the upgrading that is), and since the process itself is CPU intensive, the computer became really hot, which got it to shut down ... right in the middle of the upgrading. I am not certain that the problems I am encountering now are linked to that initial shut down, but I had to mention it.

So here's what I get now: the system is giving me the following, common error message: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."
I did run the 'dpkg --configure -a' command to realize that I have loads of broken dependencies.
I did find a handful of forums dealing with just that issue (such as this one: [http://ubuntuforums.org/showthread.php?t=186672](http://ubuntuforums.org/showthread.php?t=186672)), and I applied myself to using the information those threads give out: tried to purge the tainted packages, etc. To no avail unfortunately, as none of the packages I tried to purge and/remove were purged and/or removed. 

So I'm stuck, still facing the DPKG problem and the message that I should deal with it manually. It feels like an endless loop of misery at this point.

Any suggestion on how I should deal with this problem (these problems) would be welcome.

Thanks,
Nofare

---

### Post by oilchangeguy on 2008-09-12
computer specs, and ubuntu version, please.

---

### Post by nofare on 2008-09-12
> **oilchangeguy said:**
> computer specs, and ubuntu version, please.
Here's the tech info:

Ubuntu Version:
Ubuntu 8.04.1 \n \1

Laptop: DELL Latitude C400:
vendor_id: GenuineIntel
cpu family: 6
model: 11
model name: Mobile Intel(R) Pentium(R) III CPU - M 1200MHz
cpu MHz: 798.000
cache size: 512 KB
fdiv_bug: no
hlt_bug: no
f00f_bug: no
coma_bug: no
fpu: yes
fpu_exception: yes
cpuid level: 2
wp: 2
bogomips: 596.43
clflush: 32

             total used  free  shared  buffers  cached
Mem:          629   239   389     0        5       147
-/+ buffers cache:   86   543
Swap:         839     0   839


Host bridge: Intel Corporation 82830 830 Chipset Host Bridge

VGA compatible controller: Intel Corporation 82830 CGC

Display controller: Intel Corporation 82830

USB controller: Intel Corporation 82801CA/CAM USB Controller #1

PCI bridge: Intel Corporation 82801 Mobile PCI Bridge

ISA bridge: Intel Corporation 82801CAM ISA Bridge

IDE Interface: Intel Corporation 82801CAM IDE U100 Controller

Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller

Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller

Ethernet controller: 3Com Corporation 3c905C-TX/TX-M

CardBus bridge: Texas Instrument PCI1410 PC card Cardbus Controller

Thanks.

---

### Post by ibuclaw on 2008-09-12
```
sudo apt-get install -f
```

Also, what sources do you have enabled in your **/etc/sources.list** file and **/etc/sources.list.d** folder?

Regards
Iain

---

### Post by nofare on 2008-09-12
With 'sudo apt-get install -f' I get: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a'."


As for the sources:

deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) hardy main restricted
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) hardy-security main restricted
#See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
#newer versions of the distribution.

deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the 
## distribution.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the follwoing two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://fr.archive.canonical.com/ubuntu/](http://fr.archive.canonical.com/ubuntu/) hardy-partner
# deb-src [http://fr.archive.canonical.com/ubuntu/](http://fr.archive.canonical.com/ubuntu/) hardy-partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

Well, two things I already see.
(1) I seem to have missed two # signs, that I should have removed.
(2) Maybe I could get a new repository list,as the ones I'm using now might be corrupted.

Suggestions, please, with command codes!!
Thanks all for your help.

---

### Post by nofare on 2008-09-13
All right, it looks like I fixed the problem I was facing, as I don't see any dependency problems anymore, or unconfigured problems either -- for packages I couldn't configure in the first place!

Here's what I did:

(1) Change my Source List, by switching to U.S. based servers.
I found that list here: [http://ubuntuforums.org/showpost.php?p=1090438&postcount=2](http://ubuntuforums.org/showpost.php?p=1090438&postcount=2)
I simply wrote Hardy instead of Dapper. 

(2) Updated the Source List : $sudo apt-get update

(3) ... and after a couple of more tweaks found myself facing the following error code: cannot access `/var/run/dbus': No such file or directory
I found a solution to fix that problem here: [http://ubuntuforums.org/showthread.php?t=771381](http://ubuntuforums.org/showthread.php?t=771381)

I entered the command: $sudo mkdir /var/run/dbus
And all my dependency and unconfigured problems vanished. A beautiful thing to see.

(4) Then, using the end part of this thread: [http://ubuntuforums.org/showthread.php?t=186672](http://ubuntuforums.org/showthread.php?t=186672)
I went on to fix and clean up everything, and all seems to be functioning now ... although I still have to get the GUI up.

---

