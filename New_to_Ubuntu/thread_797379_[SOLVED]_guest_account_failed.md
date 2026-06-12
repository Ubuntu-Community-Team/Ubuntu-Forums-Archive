---
title: "[SOLVED] guest account failed"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by Zopiac on 2008-05-17
i did what was told on [this thread]("http://ubuntuforums.org/showthread.php?t=513820"), and i didnt seem to notice this first step:

"Step 1
Make sure you have created a user. For the sake of this example, let's say you called the account username guest. You can give it any temporary password you want. We're going to change that password shortly anyway. I'm assuming you know how to do this already. If you don't, I can assure you that this HowTo is not one you should be following, and you would be very likely to screw up the next step."

i just added a new line, named it 'guest', put in the next few sequences, yet corresponding to my other accs., but now i cannot log into any accounts, even though i deleted that line from the ubuntu disk. and yes, i saved the changes after deleting it.

---

### Post by warbread on 2008-05-17
So... you changed more than just the guest line?  Am I understanding that right?

Yeesh.  That's harsh. You can try [this link.]("http://www.debuntu.org/recover-root-password-single-user-mode-and-grub")  I hate to say it, but you may be boned here.  Start planning to back up important information and then reinstall.

---

### Post by bodhi.zazen on 2008-05-17
Become root with :

```
sudo -i
```If that does not work, boot to recovery mode. You will have a command line only system.

If that fails, boot the Ubuntu live, desktop CD and mount your ubuntu partition at mnt (I will assume Ubuntu is at /dev/sda1, make adjustments accordingly):

```
sudo -i  #This give a root shell

mount /dev/sda1 /mnt
chroot /mnt /bin/bash
```The chroot enters your Ubuntu install.

So, one way or another, you have a root shell. See if you can restore from backup. The -B flag with nano makes a backup.

```
cp /etc/shadow~ /etc/shadow
```Either way, make a new account :

Now :

```
adduser guest
```Give the guest account a password.

Then, finally,

```
nano -B /etc/shadow
```Re-edit the shadow account.

Check it is working with

```
su guest
```su to other users as well.

When done, reboot.

---

### Post by Zopiac on 2008-05-17
@bodhi: do you mean to mount the hard drive/partition? when i go to places>computer>hard disk, it says i am at /media/disk. so, instead of /dev/sda1, i said:

root@ubuntu:~# mount /media/disk /mnt

and it replied:

mount: /media/disk is not a block device

. . .

@warbread: all i did was add a line, then later, deleted it, yes.

---

### Post by bodhi.zazen on 2008-05-17
> **Zopiac said:**
> @bodhi: do you mean to mount the hard drive/partition? when i go to places>computer>hard disk, it says i am at /media/disk. so, instead of /dev/sda1, i said:

root@ubuntu:~# mount /media/disk /mnt

and it replied:

mount: /media/disk is not a block device

. . .

@warbread: all i did was add a line, then later, deleted it, yes.

Not sure we are on the same wavelength here ....

Are you running from the live CD ? 

do you know your Ubuntu partition ? /dev/sda1 ?

If not , list your partitions with :

```
sudo fdisk -l
```

Now , assuming /dev/sda1, you will need to adjust accordingly,

1. Boot to live CD

2. ```
sudo -i
umount /dev/sda1 #it is OK if you get a warning message that sda1 is not mounted.
mount /dev/sda1 /mnt
```

---

### Post by Zopiac on 2008-05-17
@bodhi: is that all i am supposed to do? remount the device?

---

### Post by bodhi.zazen on 2008-05-17
Well, I am wanting you to gain root access by the easiest and shortest means. You can :

1. If you are running from hard drive : sudo -i
2. boot to recovery mode
3. boot the desktop CD, mount ubuntu, and chroot into it.

However you gain root access, continue my instructions with :

```
cp /etc/shadow~ /etc/shadow
```
and continuing with the rest of my advice ...

---

### Post by Zopiac on 2008-05-17
i went root, then mounted, but then:

root@ubuntu:~# chroot /mnt /bin/bash
chroot: cannot run command `/bin/bash': Exec format error

---

### Post by bodhi.zazen on 2008-05-17
Can you be more specific please. Are you running from hard drive , live CD, or did you re-boot to the desktop CD ? Do you know your Ubuntu partition and is it mounted ?

Can you list the output of :

```
sudo fdisk -l

mount

ls -l /mnt
```

Also from the Gentoo wiki :

> 
If the chroot command returns with the error "[COLOR=#000000]chroot: cannot run command `/bin/bash': Exec format error[/COLOR]", this usually indicates that the livecd environment is not compatible with that of the installed system. 
For example, the error is most frequently seen when trying to chroot to a 64-bit system (eg. **[COLOR=magenta]amd64[/COLOR]**) from a 32-bit livecd (eg. **[COLOR=magenta]x86[/COLOR]**). 
The solution is to use a livecd which is using the same architecture as the installed system.

---

### Post by Zopiac on 2008-05-17
sorry, i tried to reple with the facts, but forgot...
i am running the cd by restarting
/dev/sda2
is that it?

---

### Post by bodhi.zazen on 2008-05-17
What is the output of 

fdisk -l

And are you running 32 bit Live CD with a 64 bit install (or visa versa)

---

### Post by Zopiac on 2008-05-18
> **bodhi.zazen said:**
> What is the output of 

fdisk -l

And are you running 32 bit Live CD with a 64 bit install (or visa versa)

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc85a3fbe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       19457   156288321   83  Linux
ubuntu@ubuntu:~$ 


and yes, i was using the 32bit for my 64bit version....does it make a difference? i just couldnt find the 64bit disk at the moment...i have it now

if that is all, could you/someone list all steps at once? it gets confusing :P

then again, i am using hardy with the gutsy CD....problematic?

---

### Post by Zopiac on 2008-05-19
bump

---

### Post by bodhi.zazen on 2008-05-19
Once you have root access see post #3

---

### Post by Zopiac on 2008-05-19
uhm is that supposed to make me able to edit my original shadow file? because when it actually shows the file. near the end of your steps, it just shows two lines....i had quite a few...

then, in another terminal window, i put in su guest, and it says:

ubuntu@ubuntu:~$ su guest
Unknown id: guest

---

### Post by Zopiac on 2008-05-20
bump (again)

---

### Post by bodhi.zazen on 2008-05-20
I suggest we go one step at a time.

First you need root access. Please either :

1. Boot to hard drive and select recovery mode.

2. Boot a live CD, mount your ubuntu partition at /media/ubuntu. Become root in a terminal and enter : ```
sudo -i
```

Post back with a more detailed description such as "I booted to recovery mode" or "I booted the desktop CD and mounted my ubuntu partition at ____ " (fill in the blank). You can also try I followed post #3 up to the command .... when I did not understand how to ___ or got this error message ____ .

posting su guest failed or bump has not provided much information for us to help you with.

---

### Post by Zopiac on 2008-05-21
well i tried my custom fix. i installed ubuntu 8.04 onto another hard drive, then copied the shadow file from it to my broken one. it WORKS except some settings are off. for instance, my resolution is 800x600 again, and it scrolls through 1024x768 (res is actually 1024x768, but shows only 800x600 of it at a time) and i dont have access the my nvidia settings manager anymore. it is gone from my list of settings apps, and when i try gksudo nvidia-settings it does nothing, not even prompt for a password.

my emerald theme is not showing up, even though i say emerald --replace

AWN will not open

my mouse pack, ecliz, is gone (oh well, i was going to download the full size soon anyways)

and probably other bugs

edit: nvidia fixed, the drivers got disabled.
edit2:nvidia driver enabling fixed everything!

---

