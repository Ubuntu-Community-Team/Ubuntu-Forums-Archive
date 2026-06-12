---
title: "blank screen with white cursor blinking"
date: 2016-04-18
forum: New to Ubuntu
---

### Post by barbosadaniel on 2016-04-18
Hi all!

I've found a problem with my OS. Yesterday I found it with a blank screen and and white cursor blinking (pc was turned on). I restarted it and after BIOS, now I always see this screen, I don't see the grub and it stays there forever.

I followed instructions to recover the grub with the Boot-Repair, using the Live-version of Ubuntu with an USB stick, but it didn't work.

Here's the pastebin:
[http://paste.ubuntu.com/15920686/](http://paste.ubuntu.com/15920686/)

Can anyone help me please?

Thanks in advance!

---

### Post by westie457 on 2016-04-18
Hello, welcome to the Forum.
The very last line of your Boot Report has the answer for you.
> [COLOR=#000000]Please [/COLOR][COLOR=#AA22FF]**do **[/COLOR][COLOR=#000000]not forget to make your BIOS boot on sdb [/COLOR][COLOR=#666666]([/COLOR][COLOR=#000000]64.0GB[/COLOR][COLOR=#666666])[/COLOR][COLOR=#000000] disk!

Either try the one time boot-menu via the (usually) F12 key at computer power on or go to the boot page of the bios and change the boot order of the hard drives.[/COLOR]

---

### Post by barbosadaniel on 2016-04-18
Hi Westie,

Thanks for the welcome and for the quick reply.

Unfortunately I already have the sdb (64GB) disk the default boot (I haven't changed), so nothing is changed.
There's the option at Boot-repair to update the grub to Ubuntu 15.04 but I have the 14.04 installed... is it a good idea?

---

### Post by barbosadaniel on 2016-04-18
Hmmm now that I went to recheck it, somehow the default disk wasn't this one anymore.
Anyway, I changed it but now I only see memtest on the grub.

I tried to recover the grub with Boot-repair, but it freezes when it tries to update the kernel... 
I've followed these stpes, but it doesn't seem to fix it:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

This looks the same and it doesn't fix it also:
[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

Any ideas? :(

---

### Post by westie457 on 2016-04-18
The version of Grub installed is [COLOR=#BB4444] (GRUB) 2.02~beta2-9ubuntu1.7  

[/COLOR][COLOR=#000000]This is the correct version on a fully updated system.

Other than trying repairs manually through the 'Advanced options' window forcing grub onto the MBR area of the boot drive (/dev/sdb).

In the advanced window any tabs that are 'greyed' out means you cannot change things in that tab.

Look here for what to expect in the advanced window. [/COLOR]https://sourceforge.net/p/boot-repair/home/Home/
Check and double-check everything before applying the repairs.

Good luck

---

### Post by barbosadaniel on 2016-04-21
Thanks again for your reply westie. I've been trying to fix it but don't know whether I should update the kernel to the last version.
I was was able to get the pastebin I had it installed, but the correct disk wasn't being loaded. In the meanwhile I believe I purged the kernel and now I can't reinstall it again. With Boot repair it gets stuck when it says it is installing it and it might take a "few minutes"...

I know my OS is still there, my data is still there also, I can still access with a USB stick, but I can't manage to fix the grub...

---

### Post by leunam12 on 2016-04-22
A black screen with a white cursor blinking usually means that the computer cannot find a boot device. If boot-repair doesn't work and you have pointed the BIOS to the right  drive for booting, the first thing I would do is check the hard drive for errors. Boot from the live USB and use the "Disks" utility to check the S.M.A.R.T. data and see if there are any errors. If there are no errors try to re-install GRUB via chroot, sometimes that works when boot-repair doesn't.

---

### Post by leunam12 on 2016-04-22
Instructions to install GRUB via chroot: Boot from live USB, open terminal (now I'm assuming that the drive where you want to install GRUB is /dev/sdb). Now type:
```
sudo mount /dev/sdb1 /mnt

sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys 

sudo chroot /mnt

sudo grub-install /dev/sdb
update-grub


```

If the drive and partition are different than sdb1 you must enter the right drive letter and partition number in the first command.

---

### Post by barbosadaniel on 2016-04-22
[FONT=Verdana]Thanks leunan,[/FONT]

[FONT=Verdana]It should be exactly as you say (disk is sdb).[/FONT]

[FONT=Verdana]SMART Data test gives this result:[/FONT]
[IMG]http://oi63.tinypic.com/smt5j7.jpg[/IMG]

[FONT=Verdana]When I try that code, when I try the sudo grub-install /dev/sdb, it gives me this result:[/FONT]

```
root@ubuntu:/# update-grub
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
```


It cannot restore the normal boot, only the memtest... any ideas on how to restore what's missing?

Thanks so much!

---

### Post by barbosadaniel on 2016-04-23
Hi all!

Finally I fixed the problem, after I did a 

```
apt-get install linux-image-generic
```
 to install what was missing.

Thanks for your help and to lead me in the right direction!

Kind regards

---

