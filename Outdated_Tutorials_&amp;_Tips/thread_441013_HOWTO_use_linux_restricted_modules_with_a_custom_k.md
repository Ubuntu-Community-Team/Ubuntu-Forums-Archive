---
title: "HOWTO: use linux restricted modules with a custom kernel"
date: 2007-05-12
forum: Outdated Tutorials &amp; Tips
---

### Post by kilou on 2007-05-12
**[COLOR="Red"]IMPORTANT: MANY PEOPLE REPORT PROBLEMS TO HAVE THIS WORKING. FOR NOW IT'S VERY LIKELY IT'S NOT GOING TO WORK FOR YOU AS IS!!!!!!![/COLOR]**


This HowTo propose a trick to use linux restricted modules and use the restricted driver manager in Feisty with a custom kernel (like a Vanilla kernel or a patched Ubuntu kernel etc). 

Why do this?
----------------
Sometime you need to use a custom compiled kernel for various reasons if you need specific hardware to work, if you want the very latest Linux kernel or if you want to use some patches like the popular undervolting patch (linux PHC). When you compile a kernel it has its own specific name and is thus no more "associated" to the linux restricted modules that came with the Ubuntu distrbution. So usually people compiling a new kernel couldn't use the restricted modules and had to use workarounds to have their specific hardware working (like Nvidia or ATI cards). This HowTo is made to propose a way to use those restricted modules with custom kernels.

How does this work?
-------------------------
Nothing fancy here. It's all about symlinking! Basically when you compile a kernel it gets a specific name/version that doesn't match those of the restricted modules that came with Ubuntu. So if you create symlinks or all references to restricted modules under the new name of the kernel, Ubuntu may think that there exist restricted modules for our specific kernel and will use them. So for all files/folders containing restricted modules for the original kernel, you have to create a symlink with the new kernel name/version. 

Which Ubuntu version does it apply to?
-----------------------------------------------
This trick has been tested on Feisty Fawn and the user who kindly tested that was able to install/uninstall Nvidia restricted drivers from the Restricted driver manager while using a custom compiled Vanilla kernel patched with Con Kolivas performance patch. It must be mentionned that the Vanilla kernel was the same version (2.6.20) as the linux-restricted-module that come with Ubuntu. However it's quite possible that this would work if you use a newer/older kernel as well. It just hasn't been tested yet.

Is it dangerous?
-------------------
Honestly I don't think so but obviously do a backup before messing with this, just in case something get screwed. You can easily revert the modification applied by this trick simply by removing the symlinks created. If you have any problem you should still be able to reboot the computer under the old kernel version to remove the changes.





OK so what should I do to have this work (on Feisty)?
-----------------------------------------------------------------

***** PLEASE BACKUP FIRST *****

Here we will assume that you new custom kernel is **2.6.20-ck1**. Just adapt the blue text to your own kernel if it different.

1) We first need to trick Ubuntu into thinking that there exist a linux-restricted-modules package specific to your custom kernel. This is required to allow the restricted drivers manager in Feisty to work.

**sudo gedit /var/lib/dpkg/status** and copy the following at the end of the file then save it:

```

Package: linux-restricted-modules-[COLOR="Blue"]2.6.20-ck1[/COLOR]
Status: install ok installed
Priority: optional
Section: restricted/misc
Installed-Size: 41328
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-restricted-modules-2.6.20
Version: [COLOR="Blue"]2.6.20-ck1[/COLOR]
Provides: nvidia-kernel-1.0.9631, nvidia-kernel-1.0.7184, nvidia-kernel-1.0.9755
Depends: linux-image-2.6.20-15-generic, linux-restricted-modules-common (>= 2.6.20), module-init-tools, nvidia-kernel-common
Suggests: nvidia-glx | nvidia-glx-legacy | nvidia-glx-new, avm-fritz-firmware-2.6.20-15
Description: Non-free Linux 2.6.20 modules on x86/x86_64
 This package provides restricted modules for Linux version 2.6.20 on
 x86/x86_64.
 .
 Currently the following modules are included:
 - madwifi (Atheros)
 - fglrx (ATI)
 - nvidia
 - fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcpci (AVM ISDN)
 .
 These modules are "restricted" because they are not available under a
 completely Free licence.

```

2) **sudo gedit /var/lib/dpkg/available** and copy the following at the end of the file then save it:

```

Package: linux-restricted-modules-[COLOR="Blue"]2.6.20-ck1[/COLOR]
Priority: optional
Section: restricted/misc
Installed-Size: 41328
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-restricted-modules-2.6.20
Version: [COLOR="Blue"]2.6.20-ck1[/COLOR]
Provides: nvidia-kernel-1.0.9631, nvidia-kernel-1.0.7184, nvidia-kernel-1.0.9755
Depends: linux-image-2.6.20-15-generic, linux-restricted-modules-common (>= 2.6.20), module-init-tools, nvidia-kernel-common
Suggests: nvidia-glx | nvidia-glx-legacy | nvidia-glx-new, avm-fritz-firmware-2.6.20-15
Size: 16096180
Description: Non-free Linux 2.6.20 modules on x86/x86_64
 This package provides restricted modules for Linux version 2.6.20 on
 x86/x86_64.
 .
 Currently the following modules are included:
 - madwifi (Atheros)
 - fglrx (ATI)
 - nvidia
 - fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcpci (AVM ISDN)
 .
 These modules are "restricted" because they are not available under a
 completely Free licence.

```

3) Now we will create all the symlinks so that the new kernel can use the restricted modules that originally came with Ubuntu. 2.6.20-15 is the kernel version that comes with Feisty. If you don't use Feisty you need to adjust this version number to whatever your distribution is.

In the terminal copy/paste these lines one at a time and run them:

[B]cd /lib/firmware
sudo ln -s 2.6.20-15-generic [COLOR="Blue"]2.6.20-ck1[/COLOR]

cd /lib/linux-restricted-modules
sudo ln -s 2.6.20-15-generic [COLOR="Blue"]2.6.20-ck1[/COLOR]

cd /usr/share/linux-restricted-modules
sudo ln -s 2.6.20-15-generic [COLOR="Blue"]2.6.20-ck1[/COLOR]

cd /var/lib/dpkg/info
sudo ln -s linux-restricted-modules-2.6.20-15-generic.md5sums linux-restricted-modules-[COLOR="Blue"]2.6.20-ck1[/COLOR].md5sums
sudo ln -s linux-restricted-modules-2.6.20-15-generic.postinst linux-restricted-modules-[COLOR="Blue"]2.6.20-ck1[/COLOR].postinst
sudo ln -s linux-restricted-modules-2.6.20-15-generic.postrm linux-restricted-modules-[COLOR="Blue"]2.6.20-ck1[/COLOR].postrm
sudo ln -s linux-restricted-modules-2.6.20-15-generic.list linux-restricted-modules-[COLOR="Blue"]2.6.20-ck1[/COLOR].list[/B]

4) Try to open the restricted drivers manager and see if it works. You should now be able to install/uninstall restricted drivers!

---

### Post by Eddi3 on 2007-05-20
First of all, When you paste those two blocks of text, you need to put a space before each of the following lines of text, for both blocks:

```
This package provides restricted modules for Linux version 2.6.20 on
x86/x86_64.
.
Currently the following modules are included:
- madwifi (Atheros)
- fglrx (ATI)
- nvidia
- fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcpci (AVM ISDN)
.
These modules are "restricted" because they are not available under a
completely Free licence.
```

Then, I had to reinstall all of the packages that were related to the restricted drivers manager (Except the fake one we added), and reboot. But I'd been having trouble with this and just manually installed the madwifi drivers I needed in the end, although the Restricted Drivers Manager does work, and does recognize that I do indeed need the Atheros drivers.

Thanks,

Eddie

---

### Post by kilou on 2007-05-20
> **Eddi3 said:**
> But I'd been having trouble with this and just manually installed the madwifi drivers I needed in the end, although the Restricted Drivers Manager does work, and does recognize that I do indeed need the Atheros drivers.

Hi Eddy,

thanks for the precisions. I have modified the first post so that the spaces are properly registred when doing a copy/paste. What kind of troubles did you experience? Was the restricted driver manager not able to install the Atheros drivers for your madwifi?

---

### Post by kilou on 2007-05-29
If you want to use the updated restricted modules that came with kernel update 2.6.20-16, you need to replace the 2.6.20-15 with 2.6.20-16 everywhere.

---

### Post by dcherryholmes on 2007-05-31
When I try this procedure and I click on the restricted drivers manager, I get the following text box:

You need to install the package

  linux-restricted-modules-2.6.21.3-custom

for this program to work.

Any ideas what could be wrong?  I checked for simple transcription errors (modified for 16-generic and also the name of my custom kernel).

---

### Post by kilou on 2007-05-31
The example above is for a kernel that is called 2.6.20-ck1. Yours is called 2.6.21.3-custom so you have to use that name instead. 

So first remove all the symlinks you created with the first trial: 

sudo rm /lib/firmware/2.6.20-ck1
sudo rm  /lib/linux-restricted-modules/2.6.20-ck1
sudo rm /usr/share/linux-restricted-modules/2.6.20-ck1
sudo rm /var/lib/dpkg/info/linux-restricted-modules-2.6.20-ck1.md5sums
sudo rm /var/lib/dpkg/info/linux-restricted-modules-2.6.20-ck1.postinst
sudo rm /var/lib/dpkg/info/linux-restricted-modules-2.6.20-ck1.postrm
sudo rm /var/lib/dpkg/info/linux-restricted-modules-2.6.20-ck1.list

and then redo the process but replace all the blue texts with 2.6.21.3-custom. Don't forget there is blue text in the /var/lib/dpkg/status and /var/lib/dpkg/available file as well! Let me know if that works for you.

Hope this helps

---

### Post by dcherryholmes on 2007-05-31
I did substitute the name of my kernel for the one used in your examples.  I'll recheck it, though.

---

### Post by kilou on 2007-05-31
Did you really change the kernel version in /var/lib/dpkg/status and /var/lib/dpkg/available?? Please post a copy of what you pasted inside to make sure.

---

### Post by dcherryholmes on 2007-05-31
Here's some info on what I've got.  The problem still persists:

root@valar:/lib/firmware# ls -l
drwxr-xr-x 4 root root 4096 2007-04-15 07:53 2.6.20-15-generic/
drwxr-xr-x 4 root root 4096 2007-05-29 08:10 2.6.20-16-generic/
lrwxrwxrwx 1 root root   17 2007-05-31 10:57 2.6.21.3-custom -> 2.6.20-16-generic/

root@valar:/lib/linux-restricted-modules# ls -l
drwxr-xr-x 17 root root 4096 2007-04-15 07:53 2.6.20-15-generic/
drwxr-xr-x 17 root root 4096 2007-05-29 08:10 2.6.20-16-generic/
lrwxrwxrwx  1 root root   17 2007-05-31 10:58 2.6.21.3-custom -> 2.6.20-16-generic/

root@valar:/lib/linux-restricted-modules# ls -l /usr/share/linux-restricted-modules/
drwxr-xr-x 3 root root 4096 2007-04-15 07:53 2.6.20-15-generic/
drwxr-xr-x 3 root root 4096 2007-05-29 08:10 2.6.20-16-generic/
lrwxrwxrwx 1 root root   17 2007-05-31 10:58 2.6.21.3-custom -> 2.6.20-16-generic/

root@valar:/var/lib/dpkg/info# ls -l *custom*
-rw-r--r-- 1 root root  827980 2007-05-31 10:36 linux-headers-2.6.21.3-custom.list
-rw-r--r-- 1 root root 1045395 2007-05-31 09:56 linux-headers-2.6.21.3-custom.md5sums
-rwxr-xr-x 1 root root    7126 2007-05-31 09:54 linux-headers-2.6.21.3-custom.postinst*
-rwxr-xr-x 1 root root   11846 2007-05-31 09:45 linux-image-2.6.21.3-custom.config*
-rw-r--r-- 1 root root  141727 2007-05-31 10:31 linux-image-2.6.21.3-custom.list
-rw-r--r-- 1 root root  185519 2007-05-31 09:45 linux-image-2.6.21.3-custom.md5sums
-rwxr-xr-x 1 root root   49480 2007-05-31 09:45 linux-image-2.6.21.3-custom.postinst*
-rwxr-xr-x 1 root root   15176 2007-05-31 09:45 linux-image-2.6.21.3-custom.postrm*
-rwxr-xr-x 1 root root   20962 2007-05-31 09:45 linux-image-2.6.21.3-custom.preinst*
-rwxr-xr-x 1 root root   13266 2007-05-31 09:45 linux-image-2.6.21.3-custom.prerm*
-rw-r--r-- 1 root root   14282 2007-05-31 09:45 linux-image-2.6.21.3-custom.templates
lrwxrwxrwx 1 root root      47 2007-05-31 10:55 linux-restricted-modules-2.6.21.3-custom.list -> linux-restricted-modules-2.6.20-16-generic.list
lrwxrwxrwx 1 root root      50 2007-05-31 10:54 linux-restricted-modules-2.6.21.3-custom.md5sums -> linux-restricted-modules-2.6.20-16-generic.md5sums
lrwxrwxrwx 1 root root      51 2007-05-31 10:54 linux-restricted-modules-2.6.21.3-custom.postinst -> linux-restricted-modules-2.6.20-16-generic.postinst*
lrwxrwxrwx 1 root root      49 2007-05-31 10:54 linux-restricted-modules-2.6.21.3-custom.postrm -> linux-restricted-modules-2.6.20-16-generic.postrm*

tail of /var/lib/dpkg/status:

Package: linux-restricted-modules-2.6.21.3-custom
Status: install ok installed
Priority: optional
Section: restricted/misc
Installed-Size: 41328
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-restricted-modules-2.6.20
Version: 2.6.21.3-custom
Provides: nvidia-kernel-1.0.9631, nvidia-kernel-1.0.7184, nvidia-kernel-1.0.9755
Depends: linux-image-2.6.20-16-generic, linux-restricted-modules-common (>= 2.6.20), module-init-tools, nvidia-kernel-common
Suggests: nvidia-glx | nvidia-glx-legacy | nvidia-glx-new, avm-fritz-firmware-2.6.20-15
Description: Non-free Linux 2.6.20 modules on x86/x86_64
 This package provides restricted modules for Linux version 2.6.20 on
 x86/x86_64.
 .
 Currently the following modules are included:
 - madwifi (Atheros)
 - fglrx (ATI)
 - nvidia
 - fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcpci (AVM ISDN)
 .
 These modules are "restricted" because they are not available under a
 completely Free licence.


tail of /var/lib/dpkg/available:

Package: linux-restricted-modules-2.6.21.3-custom
Priority: optional
Section: restricted/misc
Installed-Size: 41328
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-restricted-modules-2.6.20
Version: 2.6.21.3-custom
Provides: nvidia-kernel-1.0.9631, nvidia-kernel-1.0.7184, nvidia-kernel-1.0.9755
Depends: linux-image-2.6.20-16-generic, linux-restricted-modules-common (>= 2.6.20), module-init-tools, nvidia-kernel-common
Suggests: nvidia-glx | nvidia-glx-legacy | nvidia-glx-new, avm-fritz-firmware-2.6.20-15
Size: 16096180
Description: Non-free Linux 2.6.20 modules on x86/x86_64
 This package provides restricted modules for Linux version 2.6.20 on
 x86/x86_64.
 .
 Currently the following modules are included:
 - madwifi (Atheros)
 - fglrx (ATI)
 - nvidia
 - fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcpci (AVM ISDN)
 .
 These modules are "restricted" because they are not available under a
 completely Free licence.

---

### Post by kilou on 2007-05-31
Weird. Could you please post the output of **uname -a** ?

I'll try to compile the 2.6.21.3 Vanilla kernel and see if this works on my system.

---

### Post by kilou on 2007-05-31
OK I compiled the Vanilla kernel 2.6.21.3 from [www.kernel.org](www.kernel.org) and installed it on my system (the kernel name is also 2.6.21.3-custom). Then I only modified the /var/lib/dpkg/status and /var/lib/dpkg/available files and copied the paragraphs given in first post after replacing the kernel name with 2.6.21.3-custom (just like what you seem to have done...) and for me it seems to work correctly. Before doing the mod, the restricted driver manager tells "You need to install the package linux-restricted-modules-2.6.21.3-custom". After applzing the above mods (even without having to create all the symlinks) the restricted manager says "Your hardware does not need any restricted drivers"...which is true because I do not need any of them but at least the error in restricted manager is gone and it "thinks" that the package linux-restricted-modules-2.6.21.3-custom is installed.

So it should work for your kernel as well. The problem most probably lies in the /var/lib/dpkg/status and/or /var/lib/dpkg/available files. Please check one more time if these are OK. Maybe try not to paste the lines ########### start copy here ########### and ########### end copy here ########### in the files if you did. Only leave one blank line between the end of the file and the paragraph you paste.
Also, as Eddi3 mentionned, make sure that there is a space before the following lines in the text you pasted:

```

This package provides restricted modules for Linux version 2.6.20 on
x86/x86_64.
.
Currently the following modules are included:
- madwifi (Atheros)
- fglrx (ATI)
- nvidia
- fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcpci (AVM ISDN)
.
These modules are "restricted" because they are not available under a
completely Free licence.
```

These lines must have an offset of 1 space compared to the other ones (but if you copy the text from post#1 it should have been OK...). If this is OK then you shouldn't have any problem as this is working OK with the same kernel here. Let me know.

---

### Post by adam0509 on 2007-05-31
Seems VERY VERY NICE !!


Link's added to french wiki, that's a great HOW-TO my friend !!!

---

### Post by kilou on 2007-05-31
> **adam0509 said:**
> Seems VERY VERY NICE !!


Link's added to french wiki, that's a great HOW-TO my friend !!!

Merci! Pas beaucoup testé mais ça à l'air de marcher!

---

### Post by dcherryholmes on 2007-06-01
Linux valar 2.6.21.3-custom #1 SMP Thu May 31 08:45:41 EDT 2007 i686 GNU/Linux

BTW, the message box I get when I try to run restricted drivers manager now says (paraphrased): No hardware on your system requires restricted drivers. 

lsmod | grep fglrx returns nothing. 

dmc@valar:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

Thanks for the help.....

---

### Post by kilou on 2007-06-01
Hi,

well this trick is not yet finalized I guess and it still needs a bit more work. Unfortunately I can't test this further because my system doesn't need restricted drivers but the trick is known to work for Nvidia drivers at least. You can get some more info on the thread that started it all:
[http://ubuntuforums.org/showthread.php?t=435799&page=2](http://ubuntuforums.org/showthread.php?t=435799&page=2)

You seem to have the same problem as rjwboys and he got it working after uninstalling the old nvidia drivers. You should try to uninstall everything related to ATI first and then reinstall the restricted drivers packages/reapply the trick and at last run the restricted driver manager. But for now please backup first!

---

### Post by kilou on 2007-06-02
dcherryholmes, doesn't your problem look like this one? :

[http://ubuntuforums.org/showthread.php?t=434201](http://ubuntuforums.org/showthread.php?t=434201)

I think you still have instances of the old driver installed and this may be what prevents the restricted driver manager from doing its job.

---

### Post by CorporateGoth on 2007-06-08
I have done all this, no dice.

I finally got the restricted device manager to see my devices (using a bit of constructive copying of modules from one kernel /lib/modules/X directory to another), but still no dice.

I compiled a custom kernel (to apply a patch that is already in 2.6.21, but I don't want to wait 4 months for with GG), its called 2.6.20.3-ubuntu1-custom.  I did all of the above and made the links, synaptic sees it and so on.

But even doing a modprobe fglrx does not work - it complains about version magic (even though my custom kernel specifically disable kernel module versioning).  Additionally, even though the restricted device manager is loading my wireless driver (ipw3945), I don't see a wireless option in my network setup options (and my network applet drop-down doesn't have the wireless networks in the area like it does booting 2.6.20-16-generic.

I guess for now the only thing I can do is boot to my custom kernel to make it enable my sierra wireless card (which is what the parch does), and then reboot into the generic once it has been enabled and actually use it.  This is very hacky and ugly.

What I would REALLY like is the ability to use my custom kernel to develop a REAL restricted modules package.  Hell, even just the instructions on how the DEV's create a restricted modules package would work - I'm not a kernel compilation newbie - hell, I was a Gentoo dev for a long time.  But there seems some kind of black magic at work in how restricted modules are compiled in Debian/Ubuntu.

PreZ

---

### Post by kilou on 2007-06-09
Have you tried reinstalling all the packages related to restricted drivers and manager as suggested in post #2?

---

### Post by CorporateGoth on 2007-06-11
Yeah, I did - which is why I said I did **all** of the above.  It still required manual steps.  Oh, and btw, trying to uninstall and re-install the restricted drivers themselves doesn't work too well with these hacks in place.

Either way, even if it DID work without me copying files, it still remains that the drivers themselves were not recompiled - which means that the fglrx module would NOT load on the new kernel because of the kernel versioning stuff enabled when that driver was compiled (even though I disabled it in my kernel).  Its just compiled with the wrong version of the kernel to be loaded.

---

### Post by namelessone on 2007-06-21
hey guys, I'm not an expert, but I'm pretty sure none of this will ever work. The restricted drivers all require a module that is custom compiled for your own kernel. This means that as long as you use the generic kernel, someone can precompile the modules for you and all you have to do is put the module in the right place, which is what the restricted drivers manager does for you.

If you need restricted drivers for a custom compiled kernel, you need to compile the drivers yourself from source. since you custom compiled your own kernel, this shouldn't be a problem.

I was able to compile the ipw3945 driver from source with almost no difficulty, and with a [little diffuculty]("http://ubuntuforums.org/showthread.php?t=472909"), I was able to compile the nvidia drivers.

So, I guess what I'm saying is that you should give up on this bizarre  hack and just compile the drivers from source. You'll be happier that way.

---

### Post by androloog on 2008-01-08
Is it possible to get the ipw3945 driver from you? Somehow it stopped working with my new kernel.

---

