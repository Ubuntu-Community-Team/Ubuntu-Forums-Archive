---
title: "[SOLVED] linux-image-2.6.22-1 deb packages"
date: 2007-07-30
forum: Programming Talk
---

### Post by Gremlinzzz on 2007-07-30
I was just wondering i found these linux-image deb packages  if i could use them too easy way update my kernel.if so using feisty which packages would work best?
[http://incoming.debian.org/](http://incoming.debian.org/)
:guitar:

---

### Post by walkerk on 2007-07-30
how i did my kernel upgrade. 2.6.20-16-generic to 2.6.22-8-generic...

i added the gutsy repo to my sources.list. apt-get update (of course)

synaptic linux-headers-2.6.22-8-generic, linux-image-****************, the modules.. etc

remove from sources.list, update

reboot ;)

very successful. i run 2.6.22-8-generic in feisty using the gutsy repos

---

### Post by Gremlinzzz on 2007-07-30
Questions did it improve your system and was or is there any bugs.
:guitar:

---

### Post by Gremlinzzz on 2007-07-30
Found updated package from ubuntu
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Frestricted%2Fl%2Flinux-restricted-modules-2.6.22%2Flinux-restricted-modules-2.6.22-8-generic_2.6.22.2-8.4_i386.deb&md5sum=03cc140e82db8c97e8c43f03bcffeeeb&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Frestricted%2Fl%2Flinux-restricted-modules-2.6.22%2Flinux-restricted-modules-2.6.22-8-generic_2.6.22.2-8.4_i386.deb&md5sum=03cc140e82db8c97e8c43f03bcffeeeb&arch=i386&type=main)
:guitar:
[http://packages.ubuntu.com/gutsy/misc/linux-restricted-modules-2.6.22-8-generic](http://packages.ubuntu.com/gutsy/misc/linux-restricted-modules-2.6.22-8-generic)

---

### Post by Gremlinzzz on 2007-07-30
> **Gremlinzzz said:**
> Found updated package from ubuntu
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Frestricted%2Fl%2Flinux-restricted-modules-2.6.22%2Flinux-restricted-modules-2.6.22-8-generic_2.6.22.2-8.4_i386.deb&md5sum=03cc140e82db8c97e8c43f03bcffeeeb&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Frestricted%2Fl%2Flinux-restricted-modules-2.6.22%2Flinux-restricted-modules-2.6.22-8-generic_2.6.22.2-8.4_i386.deb&md5sum=03cc140e82db8c97e8c43f03bcffeeeb&arch=i386&type=main)
:guitar:
[http://packages.ubuntu.com/gutsy/misc/linux-restricted-modules-2.6.22-8-generic](http://packages.ubuntu.com/gutsy/misc/linux-restricted-modules-2.6.22-8-generic)

never mind just gives me a dependency :( error

---

### Post by Gremlinzzz on 2007-07-30
OK found it and install the new kernel now ill check it out see if it floats.
got this package and it installed no problem.the new kernels on the grub boot list and so far boots no problem. be back later with a update report.oh heres the package i installed
[http://packages.ubuntu.com/gutsy/base/linux-image-2.6.22-8-generic](http://packages.ubuntu.com/gutsy/base/linux-image-2.6.22-8-generic)
:guitar:

---

### Post by Gremlinzzz on 2007-07-30
well so far so good did the uname -a thing and im running the new kernel checked most of my programs no problems to report.
:guitar:

---

### Post by Gremlinzzz on 2007-07-30
> **Gremlinzzz said:**
> well so far so good did the uname -a thing and im running the new kernel checked most of my programs no problems to report.
:guitar:

ok just added Package: linux-restricted-modules-common (2.6.22.2-8.4) [restricted
[http://packages.ubuntu.com/gutsy/misc/linux-restricted-modules-common](http://packages.ubuntu.com/gutsy/misc/linux-restricted-modules-common)
now im going to checkout other packages:guitar:
think this will be last package   Package: module-init-tools (3.3-pre4-2ubuntu2) cause the other packages seem to be drivers
[http://packages.ubuntu.com/gutsy/admin/module-init-tools](http://packages.ubuntu.com/gutsy/admin/module-init-tools)

---

### Post by Gremlinzzz on 2007-07-30
> **Gremlinzzz said:**
> ok just added Package: linux-restricted-modules-common (2.6.22.2-8.4) [restricted
[http://packages.ubuntu.com/gutsy/misc/linux-restricted-modules-common](http://packages.ubuntu.com/gutsy/misc/linux-restricted-modules-common)
now im going to checkout other packages:guitar:
think this will be last package   Package: module-init-tools (3.3-pre4-2ubuntu2) cause the other packages seem to be drivers
[http://packages.ubuntu.com/gutsy/admin/module-init-tools](http://packages.ubuntu.com/gutsy/admin/module-init-tools)

the last package didnt install say depen error so i guess i dont need it
:guitar: oh well got my new kernel if i have any problems ill be back.

---

### Post by Gremlinzzz on 2007-07-30
> **Gremlinzzz said:**
> the last package didnt install say depen error so i guess i dont need it
:guitar: oh well got my new kernel if i have any problems ill be back.

had too install this package too
[http://packages.ubuntu.com/gutsy/misc/linux-restricted-modules-2.6.22-8-generic](http://packages.ubuntu.com/gutsy/misc/linux-restricted-modules-2.6.22-8-generic)

---

### Post by Gremlinzzz on 2007-07-30
OK i installed 3 packages
[http://packages.ubuntu.com/gutsy/base/linux-image-2.6.22-8-generic](http://packages.ubuntu.com/gutsy/base/linux-image-2.6.22-8-generic)
[http://packages.ubuntu.com/gutsy/misc/linux-restricted-modules-2.6.22-8-generic](http://packages.ubuntu.com/gutsy/misc/linux-restricted-modules-2.6.22-8-generic)
seems that number 2 package and 3 were connected
[http://packages.ubuntu.com/gutsy/misc/linux-restricted-modules-common](http://packages.ubuntu.com/gutsy/misc/linux-restricted-modules-common)
so only 2 packages
so far so good:guitar:

---

### Post by Gremlinzzz on 2007-07-30
> **Gremlinzzz said:**
> OK i installed 3 packages
[http://packages.ubuntu.com/gutsy/base/linux-image-2.6.22-8-generic](http://packages.ubuntu.com/gutsy/base/linux-image-2.6.22-8-generic)
[http://packages.ubuntu.com/gutsy/misc/linux-restricted-modules-2.6.22-8-generic](http://packages.ubuntu.com/gutsy/misc/linux-restricted-modules-2.6.22-8-generic)
seems that number 2 package and 3 were connected
[http://packages.ubuntu.com/gutsy/misc/linux-restricted-modules-common](http://packages.ubuntu.com/gutsy/misc/linux-restricted-modules-common)
so only 2 packages
so far so good:guitar:

last post no problems so this is solved
desktop 2.6.22-8-generic #1 SMP 
:guitar:

---

### Post by walkerk on 2007-07-31
yep.. basically what i did.. only i added the repository and used apt to upgrade..

---

### Post by Gremlinzzz on 2007-08-01
> **Gremlinzzz said:**
> last post no problems so this is solved
desktop 2.6.22-8-generic #1 SMP 
:guitar:

i was right the first time you need to install all three one fixes dependences so you can install the other.so far no problems at all so i removed the other kernels:guitar:

---

### Post by walkerk on 2007-08-01
I wrote a thread on this for people look in now.. [Upgrade Feisty to use kernel 2.6.22-9-generic]("http://ubuntuforums.org/showthread.php?t=511974") .. I wrote a quick script that upgrades the kernel for you..

---

### Post by Gremlinzzz on 2007-08-02
Upgraded my kernel using your post was easy and worked like a charm.thxs and anyone wants to upgrade kernel ignore my post cause its most likely less efficient.good job. 
:guitar:

---

