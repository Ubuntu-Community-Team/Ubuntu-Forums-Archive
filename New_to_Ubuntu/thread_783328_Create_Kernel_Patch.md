---
title: "Create Kernel Patch"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by EarloftheWest on 2008-05-05
The drivers for my Thinkpad T61 do not yet control the LED.

A patch has been created:
[http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1209](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1209)
but the versions seem to be for the release candidate of the current Hardy kernel.

It appears that the source files are here:
[http://git.kernel.org/?p=linux/kernel/git/rchatre/iwlwifi-2.6.git;a=commit;h=ec2ce7fc7890b37d564a274513d8d99ed4edb9ac](http://git.kernel.org/?p=linux/kernel/git/rchatre/iwlwifi-2.6.git;a=commit;h=ec2ce7fc7890b37d564a274513d8d99ed4edb9ac)

How do I take the source files and create a patch so I can patch my kernel and rebuild it?

Thanks.

---

### Post by nowshining on 2008-05-05
u need to install the kernel sources from the repos, but first u'll have to enable the sources repos, also why not just comile a vanilla kernel from kernel.org :) and if need be patch it with 

sudo patch -p1 < pathtopatchfile


u must be in the /usr/src/folderoflinuxsrc

for it to work.

---

### Post by EarloftheWest on 2008-05-05
nowshining,
Thanks for your reply.
I'm with you on installing a new kernel. I've read the howto's and I think I can do that.
At this link:
[http://git.kernel.org/?p=linux/kernel/git/rchatre/iwlwifi-2.6.git;a=commit;h=ec2ce7fc7890b37d564a274513d8d99ed4edb9ac](http://git.kernel.org/?p=linux/kernel/git/rchatre/iwlwifi-2.6.git;a=commit;h=ec2ce7fc7890b37d564a274513d8d99ed4edb9ac)
The patch that I need appears to be source files. I don't know how to take the source files for the patch and create a patch. There appears to be a header file and a c file and a make file and other driver files. 
How do I take those files and bundle them into a patch so I can patch the kernel?
Thanks again for your help.
UPDATE:
I see a bunch of files here:
[http://git.kernel.org/?p=linux/kernel/git/rchatre/iwlwifi-2.6.git;a=commitdiff;h=ec2ce7fc7890b37d564a274513d8d99ed4edb9ac;hp=89d14f764371b45909c12f8f448371f225a0ada3](http://git.kernel.org/?p=linux/kernel/git/rchatre/iwlwifi-2.6.git;a=commitdiff;h=ec2ce7fc7890b37d564a274513d8d99ed4edb9ac;hp=89d14f764371b45909c12f8f448371f225a0ada3)
with a 'patch' download. Which one do I use?

---

### Post by nowshining on 2008-05-06
it's quite easy to do :)

also try just compiling and installing the 2.6.25.1 kernel as that patch might already be included, also go thru the options to customize ur kernel to ur specific computer.

once ur ready to compile issue the following:

make-kpkg --initrd --append-to-version=-botnetgodalphamale kernel_image kernel_headers

change botnetgodalphamale to whatever u want, :) it shows after the kernel version ex:
2.6.25.1-botnetgodalphamale

also give it some time as the compile will need some time to do its' work :) about 1hr on my P4 machine, or less if using a newer computer.

Okay once the compile is finished it will take u back to a command line from there u can eitehr use the command line to dpkg -i nameofdeb.deb

for both the linux headers deb and linux image deb or if u prefer the GUI, sudo nautilus /usr/src/
and then double-click the .deb files.

If u have a Nvidia & or ATI card the boot-up will stop as u'll need to re-install the drivers for ur new kernel thru the CLI/Terminal/Command line, but first stopping gdm with sudo /etc/init.d/gdm stop - dong a install and then issuing a sudo /etc/init.d/gdm stop.

if u get stuck & need more help or forgot to download the drivers, just stop the gdm and use lynx to get here on the forums, sign in & ask for help.

lynx is a TXT ONLY CLI browser so any java elements won't apply of which the quick reply box, just go down and remove the default typing and then doing a submit.

to use lynx type:

lynx url

then press the enter key, change url to the one u want to visit.

If on dial-up then one will have to invode wvdial to dial in, then switch to another terminal via ctrl+alt+f1-f6 as once it dials in, it won't take u back to a prompt. However u'll need to set-up wvdial first for this to work.

---

### Post by EarloftheWest on 2008-05-06
nowshining,
Thanks. I'm looking forward to doing a recompile.
The patch isn't in the 25 kernel but might be in the 26 which is still RC.
I think the patch is located here:
[http://git.kernel.org/?p=linux/kernel/git/rchatre/iwlwifi-2.6.git;a=commit;h=ec2ce7fc7890b37d564a274513d8d99ed4edb9ac](http://git.kernel.org/?p=linux/kernel/git/rchatre/iwlwifi-2.6.git;a=commit;h=ec2ce7fc7890b37d564a274513d8d99ed4edb9ac)
When I click on commit next to the tree, it downloads a tar.gz but I cannot open it with Archive Manager. Should I be using a different tool to open it? I'm concerned that since I cannot open it, it may not be a valid file.

---

### Post by nowshining on 2008-05-06
which kernel ver. are u wanting to download?

on the main page of u click the kernel version number u'll get a patch to update to that kernel version instead of re-downloading a huge 40-60mb file over the net.

if in the USA:
for ftp:
[ftp://ftp.kernel.org/pub/linux/kernel/v2.6/](ftp://ftp.kernel.org/pub/linux/kernel/v2.6/)
for http:
[http://www.kernel.org/pub/linux/kernel/v2.6/](http://www.kernel.org/pub/linux/kernel/v2.6/)


in firefox do a search for 2.6.25.1 or which kernel u want.

also bz2 file use better compression than tar.gz :)

ex:

File: linux-2.6.25.1.tar.bz2  	47445 KB  	05/01/2008  	09:50:00 PM
File: linux-2.6.25.1.tar.gz 	60077 KB 	05/01/2008 	09:50:00 PM

47445 KB = about 48-48mb
60077 KB = about 60mb

- if the gui don't work u'll have to use the CLI :) - 

So if u download the 2.6.26 kernel and it updates - then next time all u'll have to do is download the small patch to patch it up and then re-compile. :)

if u need help with that or have trouble in the future installing a patch, etc.. u can either IM me or ask on th forums & if i'm available i'll answer ur post if no-one correctly troubleshooted ur problem. :)

---

