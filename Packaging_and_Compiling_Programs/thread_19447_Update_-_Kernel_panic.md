---
title: "Update - Kernel panic"
date: 2005-03-11
forum: Packaging and Compiling Programs
---

### Post by jMack on 2005-03-11
OK, fairly new at Linux, but not a complete boner.

I got Warty all going well for me, then looked at what files could be updated; quite a few.  So I updated through Synaptec (sp?) and got everything loaded except for the latest firefox (wouldn't install).

So now I'm at kernel 2.6.8.1-5-386, and I get this spitout before it crashes:
> 
root  (hd0,1)
Filesystem type is ext2fs, partition type 0x83
kernel  /boot vmlinuz-2.6.8.1-5-386 root=/dev/hda2 ro quiet splash
   [Linux-bzImage, setup=0x1400, size=0x10b003]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.
Kernel panic: VFS: unable to mount root fs on unknown-block(0,0)


I'm guessing that the error could be due to the fact that I still have WinXP on the first partition (hda1?), and the kernel is defaulted to this?  Then again, i see the line where it declaires that root is hda2, so I'm not sure.

If its a matter of fixing Grub, please walk me through the process.  I see that at the beginning of Grub I can hit "c" and go to a command prompt.  I'm just not familiar with the commands here.

I tried loading the old kernel, but it can't find it; no doubt deleted and overwritten.

help me please,

jMack

---

### Post by jMack on 2005-03-12
Should I have posted this in another location?  Curious...

Just about to do a full reinstall!  Dang....and it took me forever to get VLC working well too...

---

### Post by Xian on 2005-03-12
[QUOTE=jMack]I tried loading the old kernel, but it can't find it; no doubt deleted and overwritten.[/QUOTE]
Maybe not, unless you selected it to be deleted. What are the contents of your /boot directory?

---

### Post by Xian on 2005-03-12
[QUOTE=jMack]I'm guessing that the error could be due to the fact that I still have WinXP on the first partition (hda1?), and the kernel is defaulted to this?  Then again, i see the line where it declaires that root is hda2, so I'm not sure.[/QUOTE]
Nah, (hd0,1) is the same as /dev/hda2. That's fine.

I think the problem might just be in your grub config.
Post the contents of your /boot/grub/menu.lst.

---

### Post by jMack on 2005-03-12
Well, its not  a problem anymore; I reinstalled.

I'm not sure where the prob was.

My procedure was this with the old one:
1.  Install Ubuntu-warty as dual-partition, fresh install.
2.  Installed misc programs
3.  Ran Update (2 weeks later) where kernel updated
4.  Problem booting.

Today, I:
1.  Install Ubuntu-warty as dual-partition, fresh install.
2.  Ran update RIGHT AWAY where kernel updated
3.  No probs rebooting.

I must've had an issue the first time with a conflict or something.  I WAS trying to install some non-supported bits-o-software, which may have been the culprit???  2 big pieces of software was Crossover Office and Transgaming-Cedega.

thanks anyway.

---

### Post by tarasbulba on 2005-04-05
> root (hd0,2)
Filesystem type is ext2fs, partition type 0x83
kernel /boot vmlinuz-2.6.10 root=/dev/hda3 ro quiet splash
[Linux-bzImage, setup=0x1600, size=0x11ab03]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.
Kernel panic-not syncing:VFS: unable to mount root fs on unknown-block(0,0) 
Hello,today i have tried to re-compile and install my kernel on Hoary 5.04 prewiev .everything was well.when i rebooted it gave me same thing above.Like in wiki pages told,New kernel didn't make an intrd.img.In menu.lst it seems to be ok.It likes my old kernel.Just vmlinuz different.Here is menu.lst:
> title		Linux.old 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-4-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.10-4-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-4-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-4-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.10-4-386
savedefault
boot

title		Ubuntu, kernel 2.6.10 
root		(hd0,2)
kernel		/vmlinuz-2.6.10 root=/dev/hda3 ro quiet splash
savedefault
boot

title		Ubuntu, kernel 2.6.10 (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.10 root=/dev/hda3 ro single
savedefault
boot


title		Ubuntu, kernel memtest86+ 
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot
but i can't understand why it made so?Pls help.(i can booting with my old kernel)

---

### Post by tarasbulba on 2005-04-10
i have found a wiki in ubuntu site for this thread.It works for me:

> $ sudo mkdir /lib/modules/`uname -r`/boot/
$ sudo cp -a \
/lib/modules/`uname -r`/kernel/security/capability.ko \
/lib/modules/`uname -r`/boot/ && \
sudo mkinitrd -o /boot/initrd.img-`uname -r` `uname -r`
i have just put my new kernels' name instead of uname -r like 2.6.10-ati 
i hope this is helpful.thanks

---

### Post by domo on 2005-05-04
[QUOTE=tarasbulba]i have found a wiki in ubuntu site for this thread.It works for me:


i have just put my new kernels' name instead of uname -r like 2.6.10-ati 
i hope this is helpful.thanks[/QUOTE]

That's work for me, thanks a lot.

---

### Post by xshiosak on 2005-05-19
I had  the same problem after I recompile my kernel. I added ramdisk support on my kernel config and it woks, let me know if you have more problems with it...

---

