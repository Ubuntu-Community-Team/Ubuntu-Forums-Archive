---
title: "how to compile linux modules?"
date: 2005-07-28
forum: Programming Talk
---

### Post by mabuti on 2005-07-28
Hello!

Firstly, what is a kernel tree? After reading this documentation, [howto](http://tldp.org/LDP/lkmpg/2.6/html/index.html) , and buying a book on how to write linux device drivers. I still cannot compile a simple "hello world"  module.  My C is very good and I have been using linux for over a year now.
On [this](http://tldp.org/LDP/lkmpg/2.6/html/x181.html) documentation, they refer to this folder linux/Documentation/kbuild/ for detailed steps on howto compile modules. However, I could not find it on my Ubuntu .  ](*,) 

Please help me find my way around, ...can't wait 2 get my hands on the code.
bye

---

### Post by Juergen on 2005-07-28
The 'kernel-tree' is the complete source-code for the kernel and the 'tree' of (sub)directories it lives in.

You probably haven't installed the package 'linux-source-2.6.10' or just 'linux-tree'
It should normally go to /usr/src

And what good is a device-driver that outputs 'hello world'? (where? when?)
Ah, I see, it's an example ;-)

---

### Post by kamstrup on 2005-07-29
You can get the kernel tree from the Ubuntu repositories, but I find this a pain to work with. I'd recommend going to [www.kernel.org](www.kernel.org) and grabbing the latest stable release (2.6.12.3 at time of writing). Be aware that you need the FULL sources not the patch. You get these by clicking on the F link to the right of the release title.

NOTE: The danger of using the Ubuntu packages is also that it installs in /usr/src - a place where you need root priviledges to work. Furthermore, unless you change the EXTRAVERSION in the top lines of the Makefile, you can get yourself into BIG trouble. Therefore I again recommend the kernel.org sources , and unpacking them somewhere in you home directory. 

With the kernel tree somewhere in you home dir, I'd do something like the following. Compile them as ordinary user: "make menuconfig" to configure stuff... then "make" and finally do "sudo make modules_install". Then copy arch/i386/boot/bzImage and System.map to /boot (as root again - and maybe with sensible names such as vmlinuz-2.6.13.2 and System.map-2.6.13.2).

EDIT: Then add a new entry to /boot/grub/menu.lst, and reboot into your new kernel.

---

### Post by mabuti on 2005-07-29
Alright thanks, I got it. I simply needed to run this command first: sudo apt-get install build-essential linux-headers-`uname -r`.
cheers \\:D/

---

### Post by kamstrup on 2005-07-29
Ok, to make sure that your hacking does not bork up the working kernel+modules, edit /usr/src/linux/Makefile and set ```
EXTRAVERSION = -myversion
``` - substituting something in for myversion.

Or else you modules will be installed on top of the original modules causing a mess...

---

