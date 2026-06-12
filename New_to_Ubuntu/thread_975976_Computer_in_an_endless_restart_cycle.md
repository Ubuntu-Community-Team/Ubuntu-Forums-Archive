---
title: "Computer in an endless restart cycle"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by Gyrro on 2008-11-08
Hello I have decided this weekend to try and install ubuntu to replace windows xp.  I have been able to get up to the point where after it is done installing it needs to reboot.  

The problem begins after I reboot as its loading.  After my bios screen I get 2 messages; one that Grub 1.5 is loading and then I believe the second message is that it has loaded and then the computer restarts and it will continue doing this cycle until I turn it off.

I have tried to do some research, but most people seem to get an error message before it restarts on them.  

One person suggested editing /boot/grub/menu.lst but when i got to that point the file was empty.

---

### Post by ironwolfe on 2008-11-08
Can you write down the error message and post it here please?

It boots ok into windows?

Also, how did you install Ubuntu - did you do a dual boot?  In other words, did you leave the windows partition?

---

### Post by Gyrro on 2008-11-08
I decided not to dual boot and just try only ubuntu.  Another solution I found was to create a /root partion because the bios can't handle anything over 8gigs but i wasn't unsure about that.  I will go find out exactly what the 2nd message was but I am fairly sure it was not an error message.

update:  The exact messages I get are:
                         Grub Loading Stage 1.5
                         Grub Loading Please Wait...

---

### Post by handydan918 on 2008-11-08
Well, in the amount of time that's passed, you could have reinstalled already...

---

### Post by Gyrro on 2008-11-08
I have reinstalled 4 times one of the times wiping everything off my hard drive before trying to install again.  None of it helps I still get the same message

---

### Post by ironwolfe on 2008-11-09
It sounds like something is wrong with GRUB itself.  Usually GRUB will give an error (example: Error 25) so it is like a problem with teh MBR.  Likely the MBR (Master Boot Record is toast).  Do you have more than one HD in your machine (i.e. to hard disks)?

My advice: reinstall GRUB on the drive using the Live CD.

here is a link with a HOWTO:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

While you are in the Live CD, start up a terminal, and check the menu.lst file and fstab files.

Click the menus: [Applications]/[Accessories]/"Terminal"


at the prompt type:
```
ls /media
```

which will list all the drives that are mounted.  The reason for doing this is to figure out the name of the hard drive, as you are running off the CD.  Once you find yours note the name, which I will call disk1 in the following commands

```
gksudo gedit /media/disk1/boot/grub/menu.lst
```  replace the name of your disk instead of disk1.

you should be able to fire up firefox and copy and paste your menu.lst file contents to this forum.  Quit gedit without savings and go back to the terminal box.

Then type:
```
gksudo gedit /media/disk1/etc/fstab
```

and post that in the same forum reply

Lastly type:
```
ls /dev/disk/by-uuid -la
``` 

This will help us understand if the fstab matches the actual disks installed - sometimes this can get mixed up.

Based on some past forum replies on this subject - reinstalling your grub will likely fix it.  It may also be an issue with multiple disks... which is why I asked if you have more than 1 HD in the machine.

I have a feeling that you did not install GRUB properly in the MBR (may still have the windows bootloader there), or it got corrupted, in which case you will want use the live CD to completely format the drive (including the MBR) and start the install again.```

```

---

### Post by pablolie on 2008-11-09
can you afford to reinstall? if so i would go for the text guided installation cd, and take it step by step truly looking at the parameters.

---

### Post by Gyrro on 2008-11-09
Thanks for the responses I will try these things next time I go adventuring into linux, but I had to reinstall windows because I have work to do for the rest of the week :(

---

