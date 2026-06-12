---
title: "RE: Linux equivalent software"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by Varsel on 2011-09-27
I'm looking for Linux software that does for Linux operating systems what the following software does for Windows operating systems:
EMCO MoveOnBoot 2.2.5
Unlocker 1.9.1
XPlite/2000Lite
nLite
Faronics Anti-Executable 3.40 (or) Faronics Deep Freeze 6.62
DriveShield Plus
Can anyone recommend Linux software equivalent to the above?

---

### Post by beew on 2011-09-27
Don't know about the others but I used unlocker in Windows. Since I have switched to Ubuntu I have had no need for something like that. It seems that only Windows has the problem of not letting go of external drives.

---

### Post by haqking on 2011-09-27
see here for alternative software:

[http://alternativeto.net/software](http://alternativeto.net/software)

[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)

and alot of what you mention is windows specific cause windows needs such things, this isnt Windows, Linux is different.

For browsing privacy you could look at [tor]("https://www.torproject.org/") though and [apparmor]("https://help.ubuntu.com/community/AppArmor") for restricting apps

---

### Post by btindie on 2011-09-27
As the others have said, a lot of that software is windows specific and redundant under Linux.

You can increase security with AppArmor and SELinux.

To automate the install process and control what packages are installed you can create a [preseed]("https://help.ubuntu.com/11.04/installation-guide/amd64/appendix-preseed.html") file. PXE boot the server/client, download boot config via TFTP and fetch kernel/initrd then download preseed file via http or from initrd.

---

### Post by Paqman on 2011-09-27
> **Varsel said:**
> 
XPlite/2000Lite
nLite


These are for stripping out unneeded services and such. Linux has this capability built-in, due to its highly modular nature. You can use the package manager to easily remove any parts of the system you don't want. Alternatively you can start with a very minimal system core and add only the packages for systems you do want. Check out the [minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") for the latter.

You can then use remastersys to create a custom install image for your optimised system. [Remastersys](apt:remastersys) is in the Ubuntu repos, so you can install it from the package manager.

---

