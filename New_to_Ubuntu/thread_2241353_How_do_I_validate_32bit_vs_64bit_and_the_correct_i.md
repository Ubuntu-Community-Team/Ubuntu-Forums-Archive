---
title: "How do I validate 32bit vs 64bit and the correct iso to use with VM-WARE on install"
date: 2014-08-25
forum: New to Ubuntu
---

### Post by Light_Man on 2014-08-25
***Q1:*** I have installed the server edition of ubuntu for a development environment using the default website link and I would like to validate that I have the optimal version for my hardware.


ISO:  ubuntu-14.04.1-server-amd64.iso
Hardware: Macbook pro, intel i7
Software: VM-WARE fusion 6

Running "info" commands on the CLI gave me:
```
**admin@ubuntu:/$uname -a**
Linux ubuntu 3.13.0-32-generic B57-Ubuntu SMP Tue Jul 15 03:51:0B UTC 2014 xB6_64 xB6_64 xB6_64 GNU
Linux
**admin@ubuntu:/$uname -mrs**
Linux 3.13.0-32-generic xB6_64

```

I am new to ubuntu but not unix or linux.  I haven't used -nix in some years. 

I understand the "uname -m" to indicate the hardware as 64 bit as it is, but what _guarantees_ that the software is 64bit?  Unfortunately seeing the "0-32-generic" encourages me to think that it has something to do with a 32bit version that runs on 64 bit hardware.   I am wanting to run 64 bit OS on 64 bit hardware if that is available.  Also seeing as I have a Intel processor, would I be looking to use the x86 iso vs the amd64 iso?  If this is trivial on a vm-ware install and dev environment let me know, but I would like to be sure I know how to identify the OS I am working on.

Reading further about linux kernel numbering ( [http://en.wikipedia.org/wiki/Linux_kernel#Version_numbering](http://en.wikipedia.org/wiki/Linux_kernel#Version_numbering) ) Wikipedia only seems to define the first 3 numbers:
example: Linux 3.13.0 
3: the version number
13: the release number (based on time release process of 2.6.0 ?)
0: the bug fix and security patch increment

**Q2:** So what does "-32-generic" stand for?

-lightman

---

### Post by uRock on 2014-08-25
A1: The amd64 ISO is the best one for your system.

A2: 32-generic is part of the Kernel release number and has nothing to do with 32/64 bit.

---

### Post by grahammechanical on 2014-08-25
> [COLOR=#000000]Unfortunately seeing the "0-32-generic" encourages me to think that it has something to do with a 32bit version that runs on 64 bit hardware.[/COLOR]

No. Not at all. The Linux kernel is 3.13.0 series. The "-32" is there revision number used by the Ubuntu developers to trace back any bugs or regression bugs than happen after a kernel has been patched. I am using Utopic Unicorn (14.10) and these are the kernels that I have collected since I first started using Utopic back in May this year

> Found linux image: /boot/vmlinuz-3.16.0-6-generic
Found initrd image: /boot/initrd.img-3.16.0-6-generic
Found linux image: /boot/vmlinuz-3.16.0-5-generic
Found initrd image: /boot/initrd.img-3.16.0-5-generic
Found linux image: /boot/vmlinuz-3.16.0-4-generic
Found initrd image: /boot/initrd.img-3.16.0-4-generic
Found linux image: /boot/vmlinuz-3.16.0-3-generic
Found initrd image: /boot/initrd.img-3.16.0-3-generic
Found linux image: /boot/vmlinuz-3.15.0-6-generic
Found initrd image: /boot/initrd.img-3.15.0-6-generic
Found linux image: /boot/vmlinuz-3.15.0-5-generic
Found initrd image: /boot/initrd.img-3.15.0-5-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic


I got that list by running sudo update-grub. Note the revision numbers. There was a -24 revision before there was a -32. But Utopic skipped that revision by going to Linux 3.15.0-5. If I remember correctly kernels 3.15.0-1 through to 3.15.0-4 were broken for my system. The command uname -a gives me this

> Linux sdb8-Roll-Dev 3.16.0-6-generic #11-Ubuntu SMP Mon Jul 28 01:59:56 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

x86_64 = 64 bit.

The 64 bit Linux kernel is called amd64 because it was AMD that produced the first 64 bit CPU that was compatible with the Intel x86 line of CPUs. I have an Intel 64 bit CPU. I am running Ubuntu amd64. Likewise an i386 OS (i = intel) will be a 32 bit OS and it will run on both Intel and AMD 32 bit CPUs and also their 64 Bit CPUs. Backwards compatibility because Microsoft was slow producing a 64 bit version of Windows.

> The official version of an Ubuntu kernel tells you a number of things, including the base upstream version, the current Ubuntu ABI identifier and the kernel flavour. (See *How can we determine the version of the running kernel?* to find your current version number.)
Given a version like 2.6.35-6.9-generic this can be broken into four parts as below:

[LIST]
[*]<base kernel version>-<ABI number>.<upload number>-<flavour>
[/LIST]
The base kernel version represents the mainline version on which the Ubuntu kernel is based. The ABI number represents significant changes in the kernel Application Binary Interface. _The upload number is a monotonically increasing counter for each upload of this base version._ The flavour indicates which kernel configuration variant this is (See *What is a Kernel Flavour?*).


See, What does a specific Ubuntu kernel version number mean.

[https://wiki.ubuntu.com/Kernel/FAQ](https://wiki.ubuntu.com/Kernel/FAQ)

Regards.

---

### Post by mastablasta on 2014-08-26
also for "web development" and testing I find it easy to use virtual images from TurnkeyLinux (debian based) or Bitnami stack. just download and deploy to virtual machine... no need to go through installs. saves some time...

---

### Post by Impavidus on 2014-08-26
Good explanation above. Also, install the latest upgrades, reboot and see that the 32-generic has changed into 34-generic.

---

### Post by Light_Man on 2014-08-26
grahammechanical:[INDENT]Thank you I was looking for a help guide that specified the second half of the kernel string.  So why doesn't wikipedia simply add a note on their page about distributions? Does each handle the additional kernel identification differently?  Or would this be an opportunity to enhance the wikipedia site with some information linking back to some of the more popular linux distributions?  Adding to the description that the extra content in the kernel string would be part of the distributions release.  In real world situations I would think that one would be equally apt to be exposed to the extended string so it merits being included in that discussion.

([https://wiki.ubuntu.com -[COLOR=#222222] is now added to my bookmarks ) [/COLOR]]("https://wiki.ubuntu.com/Kernel/FAQ")
[/INDENT]

mastablasta:[INDENT][COLOR=#000000]TurnkeyLinux - wow just wow.  I am working on setting up an environment for the community version of the Sugar CRM for my company and Turnkey has a VM all ready to go.  I have gone from setting up a installation to just downloading and running a vm... [/COLOR]

[COLOR=#000000]Has TurnKey been reliable for Corporate solutions?  Would you trust them?  Also if its in the fortune 500+ level should I be comfortable with using such a solution.  Have you seen any implementations done that way?  I just hesitate to roll this out in a major organization unless scrutiny was applied first.

[/COLOR][/INDENT]
[COLOR=#000000]Impavidus:
[INDENT]After looking into the apt-get command I am guessing that I only need to do a:
```
apt-get [COLOR=#333333][FONT=monospace]upgrade[/FONT][/COLOR]
```
And life will be good?  It am assuming that it will install the next stable update for ubuntu and not a developer edition.
[/INDENT]

I want to thank you all for the quick reply.  I hope I can be useful to the community in the future.

-Lightman
[/COLOR][COLOR=#000000]

[/COLOR]

---

### Post by uRock on 2014-08-26
To get kernel upgrades you'll need to run ```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by mastablasta on 2014-08-27
> **Light_Man said:**
> mastablasta:
[COLOR=#000000]TurnkeyLinux - wow just wow.  I am working on setting up an environment for the community version of the Sugar CRM for my company and Turnkey has a VM all ready to go.  I have gone from setting up a installation to just downloading and running a vm... [/COLOR]

[COLOR=#000000]Has TurnKey been reliable for Corporate solutions?  Would you trust them?  Also if its in the fortune 500+ level should I be comfortable with using such a solution.  Have you seen any implementations done that way?  I just hesitate to roll this out in a major organization unless scrutiny was applied first.
[/COLOR][COLOR=#000000]
[/COLOR]

I am not sure how well they perform on big systems you can ask them that. I know Bitnami and Turnkey are ment for easy deploy. what you downloaded is basically a Debian stable server with your app preinstalled and preconfigured. Debian Stable is one of most reliable Linux distros on par with CentOS/RedHat and Ubuntu and for that reason often used on major systems. 

I only used these as testing grounds (which is why I though you need these to test and develop) , but you could ask them and how well their support is etc...

in any case you app is Suggar that can rest probably on any Linux distro. it only depends on how easy it is to install and configure it on that distro. usually once you have server up and running it is not difficult. and ubuntu server is one of the easiest to install. if you later know what you need exactly you can only install those components using ubuntu minimal install or debian net install or similar... e.g. if your app is using LAMP, just install minimal, slap on the lamp stack, create database, install sugar. that's it. you might need to explore firewall and various other protection if this will be on external network.
[INDENT]
[/INDENT]

---

