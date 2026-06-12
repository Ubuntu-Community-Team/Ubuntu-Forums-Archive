---
title: "Unsure Package List for Downgrading Precise kernel to 3.2.x in Synaptic"
date: 2014-09-14
forum: New to Ubuntu
---

### Post by SciGuy1872 on 2014-09-14
Hi.  What all package names (Package List) in Synaptic do I need to mark for installation to get the kernel back to 3.2 (I guess the latest version of 3.2 is probably the best); I'm at vesion 3.5.0-54-generic currently.  When I type "kernel 3.2.0" in the search bar, I get a lot of package names (Package List) and do not want to corrupt the system by choosing wrong. Also, in the Package Details window, it reads like this:.

     You likely do not want to install this package directly. Instead, install
     the linux-generic-pae meta-package, which will ensure that upgrades work
     correctly, and that supporting packages are also installed.

This gives me pause so that I created this post for assistance.  I have a 32-bit, 1.2 GiBytes of RAM, and for the architecture, i386, I think.

Have a good day, and thanks for the help!

---

### Post by Bashing-om on 2014-09-14
SciGuy1872; Hi !

UHMM... one can not downgrade the kernel.
a) As "version 3.5.0-54-generic " is End-Of-Life, got to do something !
Upgrade to the 'trusty' HardWare Enablement stack:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --install-recommends linux-generic-lts-trusty libgl1-mesa-glx-lts-trusty xserver-xorg-lts-trusty linux-image-generic-lts-trusty

``` which will bring in the 3.13 kernel series.
 
b) in order to get the 3.2 series of the kernel one would have to install release 12.04.1:
[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)

If you explain the nature of the situation, then precise advise may be given.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by SciGuy1872 on 2014-09-14
Hi, thanks for the reply.  I should be able to get 3.2.x from the repositories through Synaptic--I just need the specific name/s for the Package List to install.  I need to do this because, as you mentrioned, 3.5 is EOL, the other reason is that the next upgrade to the kernel breaks the Nvidia installer so that I cannot run some programs.  Here is a post I read from back in 2013:

May 27th, 2013 
(From)  deadflowr   
Beans: 4,303

" Re: Precise has (unwanted) 3.5 kernel 
 On precise the 3.5 kernel series is called lts-quantal and should be an option, but not a mandatory install.
 If you run synaptic you should be able to remove and downgrade to the 3.2 series.
 I run precise and my kernel series is 3.2."

Thanks, again.

---

### Post by deadflowr on 2014-09-15
> **SciGuy1872 said:**
> Hi, thanks for the reply.  I should be able to get 3.2.x from the repositories through Synaptic--I just need the specific name/s for the Package List to install.  I need to do this because, as you mentrioned, 3.5 is EOL, the other reason is that the next upgrade to the kernel breaks the Nvidia installer so that I cannot run some programs.  Here is a post I read from back in 2013:

May 27th, 2013 
(From)  deadflowr   
Beans: 4,303

" Re: Precise has (unwanted) 3.5 kernel 
 On precise the 3.5 kernel series is called lts-quantal and should be an option, but not a mandatory install.
 If you run synaptic you should be able to remove and downgrade to the 3.2 series.
 I run precise and my kernel series is 3.2."

Thanks, again.

My post in that thread was from my own point of view as I had installed precise from the earliest release. The posters in that thread installed from the second point release 12.04.2 which did indeed include the 3.5 kernel series.
It also included the lts-quantal xserver graphics stack packages.
Like Sudodus stated, somewhat, downgrading, or installing the 3.2 kernel is only part of the problem, and is most likely the easier part to deal with.
The real problem would be, you need to also downgrade that graphics stack, which is will be a lot more problematic.

It would probably be best to know why you think the newer kernel, and graphics stack will break the nvidia install?

Edit: adding a link to the old (and now closed thread referenced)
[http://ubuntuforums.org/showthread.php?t=2149067](http://ubuntuforums.org/showthread.php?t=2149067)

---

### Post by SciGuy1872 on 2014-09-15
Hi, deadflowr.  After the HWE kernel update for Precise, I couldn't install the driver from Nvidia (173.14.39).  I contacted a representative and wrote about the problem and the error while the driver is trying to install:" Couldn't install nvidia.ko"; he wrote that the newer kernel breaks the installer (I have an Nvidia GeForce FX 5200, a legacy software).  The representative suggested that I downgrade to the kernel that works--that is why I still have 3.5.0-54-generic, but after reading the closed thread, I thought this was a way that I could have the programs run, and the 3.2 supported untill 2017.

So I used the clone hdd so that I had the OS before ever upgrading the kernel.

Thanks for your help and time!

---

### Post by SciGuy1872 on 2014-09-21
I've burned 12.04.3 to a DVD and can run Package Manager on the DVD while running 12.04 on the hdd--is there a way to use Package Manager to revert to the 3.2 on the DVD and get rid of the kernel the hdd runs?  How can I accomplish this, if so?  

I tried to boot from the DVD to make sure of the kernel version and to see if I would be given the option to update, but I get to choose a language, then when I select an option (Boot, Install, etc.) the process stalls after pressing enter.  I don't want to erase the program information; I have things just the way I want them, with the exception to the current kernel that is EOL.

Thanks!

---

### Post by ibjsb4 on 2014-09-21
> **SciGuy1872 said:**
> I've burned 12.04.3 to a DVD

If you would of burned 12.04.2, you would of had the 3.2 kernel by default.

---

### Post by SciGuy1872 on 2014-09-21
I was following Bashing-om's link--I was supposed to be directed to 12.04.1, but instead the link drected me to 12.04.3.  Anyway, am I going to have to wipe everything to run the 3.2, or am I merely going to have to boot from the DVD and have the machine update; what about the Package Manager if I can't boot from it?

---

### Post by deadflowr on 2014-09-21
The link is fine, however you need to scroll down the list of files to find the one for either 12.04, or 12.04.1.
Depending on which arch you use it'll be ubuntu-12.04-desktop(or 12.04.1)-some arch(amd64/64-bit or i386/32-bit).iso.

A helpful hint is the date, 12.04 should list the date as April something 2012, and 12.04.1 should list it as August something 2012.
Ignore the end of the lines that says something about 12.04.3.
Edited: I see that the links for 12.04 don't have that 12.04.3 stuff at the end, but 12.04.1 do...

---

### Post by Bashing-om on 2014-09-21
SciGuy1872; Hi !

The "better" most recommended method to get the kernel ( and the Xserver version) that you require is to do a clean fresh install of release 12.04.1.
I had not noticed there was a change in the releases available at the link;
Here is a different one with an even older 12.04 with the kernel and Xserver - Remember DO NOT opt in for the HWE as that upgrades the kernel and Xserver.
[http://old-releases.ubuntu.com/releases/precise/](http://old-releases.ubuntu.com/releases/precise/)
As in:
> 
 ubuntu-12.04-desktop-amd64.iso             25-Apr-2012 16:13  698M  Desktop CD for 64-bit PC (AMD64) computers (standard download


I Would think that this is still 12.04 with the original kernel 3.2 series, as I note the size of the image as "694 M" . Just updated from that original release of 12.04 ( point releases are already installed for you).
> 
ubuntu-12.04.1-desktop-amd64.iso           23-Aug-2012 17:13  694M  Ubuntu 12.04.3 (Precise Pangolin)


for the AMD/Intell 64 bit processors. These .iso's are listed toward the bottom of the listing. @
[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)
Back up your personal data and (RE-)install.

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

