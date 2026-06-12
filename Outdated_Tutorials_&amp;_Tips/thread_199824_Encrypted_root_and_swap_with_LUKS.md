---
title: "Encrypted root and swap with LUKS"
date: 2006-06-19
forum: Outdated Tutorials &amp; Tips
---

### Post by uptimebox on 2006-06-19
**The most recent version may be found at [https://wiki.ubuntu.com/EncryptedFilesystemHowto4](https://wiki.ubuntu.com/EncryptedFilesystemHowto4)**

---

### Post by kaamos on 2006-06-19
Very useful howto, I will be testing this when I move my lifebook from breezy to dapper. Thank you very much.

---

### Post by Somenoob on 2006-06-19
Great "howto", thanks.

---

### Post by kaamos on 2006-06-21
Ok, here we go! Used the one in the wiki.

Instead of
> cp -avx / /mnt/target
had to use
```
sudo cp -avx / /mnt/target
sudo chown $(whoami):$(whoami) /mnt/target/home/$(whoami)
```

and instead of 
> 
title           Cryptotest
root            (hd0,0)
kernel          /boot/vmlinuz-<your kernel version here> root=/dev/mapper/cryptoroot ro
initrd          /boot/initrd.img-<your kernel version here>
savedefault
boot

had to use
```

title           Cryptotest
root            (hd0,0)
kernel          /vmlinuz-<your kernel version here> root=/dev/mapper/cryptoroot ro
initrd          /initrd.img-<your kernel version here>
savedefault
boot
```
otherwise the result was error 15 - file not found.

---

### Post by uptimebox on 2006-06-22
Thanks, kaamos. I have already included your corrections in wiki.

---

### Post by Witty Name on 2006-06-30
Hi, I've tried this out and have a few points.

**1)** There is no mention of one having to have a separate boot-partition. 
I suppose it stands to reason that this would have to be the case in order for the unencrypted kernel to be read, but I think this issue should be addressed for two reasons:
**1.1** Software security.
With the requirement of a separate, readable boot-partition, a malicious party could install a modified kernel. 
**1.2** Multi-boot.
With one boot-partition, one swap-partition, and one linux-partition, having windows installed as well (which to my knowledge requires a primary-partition), one runs out of partitions. 
Four primary partitions are allowed, *or* three primary partitions and one extended.
This should be clarified initially. 

**2)** Other keyboard-layouts than US-ENG.
Some people use different layouts than US English / QWERTY; hence with the requirement of having to type the keyphrase in US English, there may be an issue.
At least this should be pointed out, at best a short explanation of how to either recompile the kernel or load a different keyboard-driver should be added.

Apart from this, it is a short and functional guide. Though not complete.

---

### Post by uptimebox on 2006-07-01
Information in the first post of this thread is outdated.

- Additions have been made to mkinitramfs scripts to load keymap at boot time (thanks to Luc Maisonobe).
- Some typos have been corrected.

Once again. The most up to date version is in wiki, not here.

[https://wiki.ubuntu.com/EncryptedFilesystemHowto4](https://wiki.ubuntu.com/EncryptedFilesystemHowto4)

---

### Post by dgh on 2006-07-03
There is no part where you fill the disk with random data like in other HOWTOs. Is it a security problem? This is from another howto:

> fill the disk with random data (and wait many more minutes...); /dev/urandom won't be as random as /dev/random, but it is the best practical solution available:

# sudo dd if=/dev/urandom of=/dev/hda3



Also there is no part where you choose the encryption algorithm. Is it AES256 by default?

These may be stupid questions, but I just want to be sure :-?

---

### Post by uptimebox on 2006-07-03
Filing partition with random data is needed if two cases:

 * you had some crucial info on the HDD before installation
 * you are totally paranoid ;)

---

### Post by uptimebox on 2006-07-03
Several additions have been made:

[LIST]
[*]some corrections to initramfs scripts to bypass confusion with bootsplash
[*]some clerifications about server/desktop installation profile
[/LIST]

Howto moved to Ubuntu Comunity Documentation:
[https://help.ubuntu.com/community/EncryptedFilesystem](https://help.ubuntu.com/community/EncryptedFilesystem)

---

### Post by ~art on 2006-07-07
Great guide for a linux noob..thanks.

Wiki still says....

kernel /boot/vmlinuz-<your kernel version here> root=/dev/mapper/cryptoroot ro
initrd /boot/initrd.img-<your kernel version here>

so I got error 15- file not found

Followed kaamos's tip and it worked (removed the /boot ).

The '$ uname -r' tip saved me some time. That definately would have taken me a while to find.

Two small noob problems I had, I couldn't find the 'server profile option' when installing ubuntu so just installed regular ubuntu...or should I have downloaded and installed the seperate server version of ubuntu ?
..and I had problems saving my edited files cos of permissions so for real noobs like me, perhaps instead of saying 'edit ' you could give the command '$ sudo gedit '.

Once again a great guide that a real linux noob can follow. Thanks.

---

### Post by ~art on 2006-07-09
Not sure if this is a problem or not, but when booting I get the message..
unable to find volume group "cryptoloop".
This happens after entering the luks password.
Ubuntu boots fine however.

Also, can someone please explain the boot process to me.
Does ubuntu use the unencrypted files on hda1 to boot to where you enter your Luks password, then transfer to the encrypted boot files on hda3 ?
Watching the boot I see....
 
root (hd0,0)
filesystem type is ext2fs,partition type 0x83
kernel /vmlinuz-2.6.15-23-386 root=/dev/mapper/cryptoroot ro quiet splash

..is that where ubuntu switches to the encrypted root ?

Thanks.

---

### Post by uptimebox on 2006-07-09
> **~art said:**
> Not sure if this is a problem or not, but when booting I get the message..
unable to find volume group "cryptoloop".
This happens after entering the luks password.
Ubuntu boots fine however.

As far as I could investigate it's not a problem. At boot time LVM tries to create this VG, but fails. Though, I don't know whuy it happens.

> 
Also, can someone please explain the boot process to me.
Does ubuntu use the unencrypted files on hda1 to boot to where you enter your Luks password, then transfer to the encrypted boot files on hda3 ?
Watching the boot I see....
 
root (hd0,0)
filesystem type is ext2fs,partition type 0x83
kernel /vmlinuz-2.6.15-23-386 root=/dev/mapper/cryptoroot ro quiet splash

..is that where ubuntu switches to the encrypted root ?

Thanks.

Not exactly. /dev/hda1 - is the only unencrypted partition. It holds kernel image, init RAM disk and GRUB configuration. When process comes to mounting filesystems, this partition is mounted as /boot.

Theoreticaly, this is the weak place of all encryption system. One could place malicios initrd image containing keylogger to /dev/hda1 for example. That's whuy i'm thinking about some technique to check MD5 hash of unencrypted partition after mount.

---

### Post by honeydew on 2006-07-11
very cool howto uptime, everything apears to be running properly to the naked eye... however on boot right after Im asked to enter my luks password, the terminal spits out "unable to find volume group cryptoroot",  what does this mean? I set this all up around 3 in the mornin or so.. so there is definatly the possibility of personal err.  Like I said everything seems to be working fine, let me know if you have any ideas of what I should look at to remove this message.

-thanks.


I guess I should read all the posts *points up* surry.. just woke =]

---

### Post by Zarin on 2006-07-11
Very helpful HOWTO.
I created an encrypted [FONT="Courier New"]/home[/FONT] partition in the same way as the [FONT="Courier New"]/[/FONT] partition and added a line for it at the end of the [FONT="Courier New"]/etc/mkinitramfs/scripts/local-top/cryptoroot[/FONT] script:
[FONT="Courier New"]/sbin/cryptsetup luksOpen /dev/hda4 cryptohome[/FONT]

This works fine but now I have to write the passphrase twice (both partitions have the same passphrase). Is there a simple way to change the scrips so that it only need to read the passphrase once?

---

### Post by FLeiXiuS on 2006-07-11
Correct me if I'm wrong, but is the AES Key only required to MOUNT the filesystem.  Afterwards you don't need to key anymore?  I'm thinking of installing a keyfile on my thumbdrive to serve as the authentication method on boot.

---

### Post by FLeiXiuS on 2006-07-11
Let me add on to what I want to do.  

My thumbdrive will have an encrypted partition with the priv-key stored on my laptop.  Inside the encypted filesystem on the thumbdrive will be a priv-key to mount my root partitions on my laptop.  The laptops /boot partition holds the priv-key to dencrypt the thumbdrive.

The boot process will hopefully go as follows.
1.) Laptop boots with thumbdrive inserted
2.) Laptop mounts the thumbdrive before it's own partitions.
3.) Laptop decrypts thumbdrives encrypted file system to reveal root's priv-key inside.
4.) The laptop uses the thumbdrives key to mount it's root partition.
5.) Pull the thumbdrive out and the system is booted properly.

This is what I hope the process looks like.  I'll give it a shot...I've never  done a full root encryption.

If I can get this method to work,  I'll be sure to post a HOW-TO.

---

### Post by dmroberson on 2006-07-11
I have one question, which I could not seem to find the answer to, anywhere.

My root and swap partitions are encrypted, according to this howto.  

I've just upgraded the kernel from 2.6.15-25-386 to 2.6.15-26-386, now I cannot boot into the system with the new kernel.  Grub updated, and called the root partition correctly, entry in menu.lst matches the entry for the previous kernel.  Does not prompt for LUKS password.  If splash is enabled, it says waiting on root filesystem.  if I take off splash, it says unable to locate volume "cryptoroot".  

What do I do?  In the mean time I have booted into the previous kernel version.

Thanks.

---

### Post by antic on 2006-07-15
So, I've followed this HowTo, step by step, several times and I'm getting the same problem.

when I reboot the system after creating the root crypto system,
I get the 

"Enter LUKS passphrase:" 

prompt. When I enter the passphrase (and I know I'm typing the right one), it says 

"Can't open device: /dev/hda3"

if I boot the old root and try 

# sudo cryptsetup luksOpen /dev/hda3 cryptoroot

 I get the passphrase prompt and when I enter it, it says 

"key slot 0 unlocked. 
Command successful."

I can then

# sudo mount /dev/mapper/cryptoroot /mnt/target

and everything is there, decrypted.

Anyone have an idea why it can't open the device on boot?

---

### Post by uptimebox on 2006-07-15
> **antic said:**
> So, I've followed this HowTo, step by step, several times and I'm getting the same problem.

when I reboot the system after creating the root crypto system,
I get the 

"Enter LUKS passphrase:" 

prompt. When I enter the passphrase (and I know I'm typing the right one), it says 

"Can't open device: /dev/hda3"

if I boot the old root and try 

# sudo cryptsetup luksOpen /dev/hda3 cryptoroot

 I get the passphrase prompt and when I enter it, it says 

"key slot 0 unlocked. 
Command successful."

I can then

# sudo mount /dev/mapper/cryptoroot /mnt/target

and everything is there, decrypted.

Anyone have an idea why it can't open the device on boot?

You need to find out what specific module is responcible for your (S)ATA chipset and include this module in /etc/mkinitramfs/modules

Dont' forget to update your initrd image:

update-initramfs -u ALL

---

### Post by antic on 2006-07-15
Thanks for the quick response.

I'm not a noob but I'm not a guru either--and not a very good linux admin...

so, could you tell me where to find that info?
I'm checking dmesg but I don't see it offhand.

thanks

--also, I'm atomantic on Skype (since it's encrypted)

---

### Post by antic on 2006-07-15
ah, I think I found it in lsmod (it must be the ide_disk mod)

I suspect I'll need to add it to the modprobe in the cryptoroot scripts as well.

I'll let you know how it goes

thanks

---

### Post by antic on 2006-07-15
I totally worked.

Thanks for the HowTo.

I'll keep an eye out for an md5 check of /boot HowTo in the future :)

---

### Post by Witty Name on 2006-07-19
> **Zarin said:**
> 
This works fine but now I have to write the passphrase twice (both partitions have the same passphrase). *Is there a simple way to change the scrips so that it only need to **read the passphrase once?***

I would also be interested in the answer to this.

When you create an encrypted root partition, you can't "shave off" any unused space with an external partition-imaging tool - for the purpose of backup - and so you want to make the root-partition no larger than it needs to be. This is of course also good for simply dd'ing it.

Hence, for purposes external to the issue of encryption, a single user would want to have at least two "user" partitions - root and "data", for example.
I imagine other setups would want to separate the /var, /tmp, /usr, and /home partitions.

**So is there a quick way to mount any number of partitions using the same passphrase, at boot?**

EDIT: I am assuming one could go by the way of giving a passphrase for the first encrypted partition, and then rely on keyfiles stored on that partition to mount the others, correct?

---

### Post by uptimebox on 2006-07-19
> **Witty Name said:**
> EDIT: I am assuming one could go by the way of giving a passphrase for the first encrypted partition, and then rely on keyfiles stored on that partition to mount the others, correct?

It is correct. At the same time it is security weekness. If system were compromised at runtime, one could steal these keyfiles.

More secure way would be creating script which asks passphrase and mounts several partitions transfering this passphrarase to each of partitions.

---

### Post by Witty Name on 2006-07-19
> **uptimebox said:**
> 
More secure way would be creating script which asks passphrase and mounts several partitions transfering this passphrarase to each of partitions.

Good point. 
Having messed around with it a little, I have come to the following simple solution for mounting multiple LUKS-encrypted partitions at boot, with a common passphrase, using the example of /dev/sda7 as "cryptodata" mounted at /mnt/data:

1. Format your other partition(s).
/sbin/cryptsetup luksFormat /dev/sda7

2. Edit the startup-script to configure this partition at boot (from /dev/hda1)
Change /etc/mkinitramfs/scripts/local-top/cryptoroot from:
```

...
if grep -q splash /proc/cmdline; then
        /bin/chvt 1
fi

/sbin/cryptsetup luksOpen /dev/sda3 cryptoroot

```

, to:
```

...
if grep -q splash /proc/cmdline; then
        /bin/chvt 1
fi

echo "Enter your LUKS passphrase for multiboot (MOLTAIPAZZ LOL):"
read -s PASSPHRASE
echo $PASSPHRASE | /sbin/cryptsetup luksOpen /dev/sda3 cryptoroot
echo $PASSPHRASE | /sbin/cryptsetup luksOpen /dev/sda7 cryptodata 

```

3. Update your initrd (from /dev/hda1)
sudo update-initramfs -u ALL

4. Update your /etc/fstab (from /dev/hda3) to mount it at boot
Add the line:
```

/dev/mapper/cryptodata  /mnt/data       ext3    nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid   0       2

```

5. Reboot and profit

---

### Post by Zarin on 2006-07-21
> **Witty Name said:**
> 
2. Edit the startup-script to configure this partition at boot (from /dev/hda1)
Change /etc/mkinitramfs/scripts/local-top/cryptoroot from:
```

...
if grep -q splash /proc/cmdline; then
        /bin/chvt 1
fi

/sbin/cryptsetup luksOpen /dev/sda3 cryptoroot

```

, to:
```

...
if grep -q splash /proc/cmdline; then
        /bin/chvt 1
fi

echo "Enter your LUKS passphrase for multiboot (MOLTAIPAZZ LOL):"
read -s PASSPHRASE
echo $PASSPHRASE | /sbin/cryptsetup luksOpen /dev/sda3 cryptoroot
echo $PASSPHRASE | /sbin/cryptsetup luksOpen /dev/sda7 cryptodata 

```

I get "Illegal option -s" when I try this. I also tried  "stty -echo" but that didnt work either. 
It works fine without the -s exept that the password is visible when I type it :(

---

### Post by BA53 on 2006-07-21
Does this Howto also work with the new Kernel: 2.6.15-25-386 ?

On a different forum they are reporting problems with this kernel version, but they are using a slightly different approach.

Thank you for your efforts.

---

### Post by uptimebox on 2006-07-21
> **BA53 said:**
> Does this Howto also work with the new Kernel: 2.6.15-25-386 ?

On a different forum they are reporting problems with this kernel version, but they are using a slightly different approach.

Thank you for your efforts.

I have written this howto when kernel version was 2.6.15-23 (as far as I can remember). I use this method on my workstation and survived several kernel upgrades without any problem.

```

$ uname -a
$ Linux bet 2.6.15-26-686 #1 SMP PREEMPT Mon Jul 17 20:14:14 UTC 2006 i686 GNU/Linux

```

---

### Post by auajax on 2006-08-04
Quote:
Originally Posted by antic View Post
So, I've followed this HowTo, step by step, several times and I'm getting the same problem.

when I reboot the system after creating the root crypto system,
I get the

"Enter LUKS passphrase:"

prompt. When I enter the passphrase (and I know I'm typing the right one), it says

"Can't open device: /dev/hda3"

if I boot the old root and try

# sudo cryptsetup luksOpen /dev/hda3 cryptoroot

I get the passphrase prompt and when I enter it, it says

"key slot 0 unlocked.
Command successful."

I can then

# sudo mount /dev/mapper/cryptoroot /mnt/target

and everything is there, decrypted.

Anyone have an idea why it can't open the device on boot?

You need to find out what specific module is responcible for your (S)ATA chipset and include this module in /etc/mkinitramfs/modules

Dont' forget to update your initrd image:

update-initramfs -u ALL


I'm having this same problem on an IBM Thinkpad T43p...   I am loading libata, ata_piix, and ahci in my /etc/mkinitramfs/modules file and I ran the update-initramfs -u ALL as directed.    I'm still having the problem.  A caveat to this, I also formatted my partition as xfs instead of ext3.   I didn't think it would really made a difference, but I added xfs and exportfs to the /etc/mkinitramfs/modules files as well.   update-initramfs -u ALL, a reboot, and I'm still having the same issue.  Any thoughts?

Thnx.

---

### Post by uptimebox on 2006-08-10
If you want your bootsplash to return after you have entered LUKS password, you need to add following code at the end of /etc/mkinitramfs/scripts/local-top/cryptoroot

```

...
if grep -q splash /proc/cmdline; then
       /sbin/usplash -c &
       sleep 1
fi

```

(Proposed by Eugene A. Brin)

---

### Post by misse- on 2006-08-22
Hi, I've followed the howto to the letter using breezy.

The first problem I ran into was when running sudo update-initramfs -u ALL

It says that my image "was been altered, will not update". The first time I apt-getted a new image and started over, this time it worked, but when trying to boot the crypted partition. It says mounting root, and then running local-top scripts. Thereafter it says something abouta circular dependency right before the kernel panics.

what gives?

---

### Post by uptimebox on 2006-08-22
> **misse- said:**
> Hi, I've followed the howto to the letter using breezy.
This method was developed and tested only for Dapper. Most certanly, it needs some modification to be used on Breezy. Thogh I am sure it is possible to make an adaptation, I suggest upgrading to Dapper.

---

### Post by misse- on 2006-08-22
Great! Thanks for the quick response.

I guess I assumed it was for breezy since you can't select a server profile in a regular dapper install. At least I haven't found it. So tell me, how can I install the server profile, do I need the server cd?

---

### Post by uptimebox on 2006-08-22
> **misse- said:**
> Great! Thanks for the quick response.

I guess I assumed it was for breezy since you can't select a server profile in a regular dapper install. At least I haven't found it. So tell me, how can I install the server profile, do I need the server cd?

There's no strict necessity to install server profile. You could install normaly, but in the end you would get 4+ Gb swap partition, which you most probably do not need.

---

### Post by misse- on 2006-08-22
But I want to follow the guide, Space is of the essence and I won't have a 2Gb swap space. Furthermore I don't want to use gnome or kde. 

So, Do I need to install from a server .iso? Is there someway of doing just that without burning it on a cd? Like on breezy where you could load an .iso from the harddrive.

---

### Post by uptimebox on 2006-08-23
> **misse- said:**
> But I want to follow the guide, Space is of the essence and I won't have a 2Gb swap space. Furthermore I don't want to use gnome or kde. 

So, Do I need to install from a server .iso? Is there someway of doing just that without burning it on a cd? Like on breezy where you could load an .iso from the harddrive.

It'll be offtopic, but I must notice, that IMHO Ubuntu is not ready for production server systems. Look at Debian. It is far more mature.

---

### Post by misse- on 2006-08-23
Hey, All I want to know is how to install the server profile. The server-cd-install just stops after loading the kernel. No error, just nothing.

---

### Post by misse- on 2006-08-23
> **uptimebox said:**
> It'll be offtopic, but I must notice, that IMHO Ubuntu is not ready for production server systems. Look at Debian. It is far more mature.

I _mean_ that I'm going to use Openbox or fluxbox instead, and choose the apps myself, stupid ;).

So, HOWTO, install the server-profile. 'Cause I tried, and the kernel froze right after booting it. You know, right after the text "booting the kernel"

---

### Post by macubergeek on 2006-08-29
This dosn't work for me
It fails at this point
$ sudo luksformat -t ext3 /dev/hda3

I get Device lookup failed
Failed to setup dm-crypt key mapping
Check kernel for support fo the aes-cbc-essiv:sha256 cipher and verify that /dev/hda3 contains at least 133 sectors
Failed to write key storage
Command failed Could not create Luks device /dev/hda3 at /sbin/luksformat line 53

---

### Post by LongLife on 2006-08-30
thanks for this useful howto

To make this howto work with my SATA hard disk on my Dell Inspiron 6400 laptop, I added the following line in /etc/mkinitramfs/scripts/local-top/cryptoroot
modprobe -Qb ata_piix
modprobe -Qb libata
modprobe -Qb dg
modprobe -Qb sd_mod
modprobe -Qb scsi_mod

And I also manually "modprobed" them manually just before the "luksformat"

I don't know if all of them are useful to make Sata work at boot, but at least it worked!

I managed to install the desktop and xorg-driver-fglrx to make my ATI X1400 work with 1650x1080

But when I installed linux-686-SMP (2.6.15.24 - for my Intel Core Duo) there was a dependancy problem because I made a special initramfs configuration!

I removed this kernel image but now I can't make any change or update on the old kernel (linux-image-686, 2.6.15-26-686), it always complains about dependancies problems :
----
E: linux-image-2.6.15-26-686: le sous-processus post-installation script a retourné une erreur de sortie d'état 2
E: linux-image-686: problèmes de dépendances - laissé non configuré
E: linux-restricted-modules-2.6.15-26-686: problèmes de dépendances - laissé non configuré
E: linux-restricted-modules-686: problèmes de dépendances - laissé non configuré
E: linux-686-smp: problèmes de dépendances - laissé non configuré
E: linux-image-2.6.15-26-server: le sous-processus post-installation script a retourné une erreur de sortie d'état 2
E: linux-image-server: problèmes de dépendances - laissé non configuré
E: linux-server: problèmes de dépendances - laissé non configuré

-----

Did I do something wrong? How can I solve the problem? Can I make this howto work with a Core Duo (SMP) kernel?

---

### Post by flight553 on 2006-09-05
> **Zarin said:**
> I get "Illegal option -s" when I try this. I also tried  "stty -echo" but that didnt work either. 
It works fine without the -s exept that the password is visible when I type it :(

This happened to me and I reinstalled the whole OS from scratch, following these instructions exactly and the Illegal option problem with 'read' went away. Everything worked for me after that.

A week later, after I updated a bunch of packages in Synaptic, it came back. I tracked down what seemed to cause it by looking at /var/log/dpkg.log to get a list of packages that were updated just before the "read: illegal option -s" error started happening. 

I found this happened after upgrading these packages:

2006-09-15 17:48:46 upgrade linux-headers-2.6.15-26 2.6.15-26.46 2.6.15-26.47
2006-09-15 17:49:03 upgrade linux-headers-2.6.15-26-686 2.6.15-26.46 2.6.15-26.47
2006-09-15 17:49:25 upgrade linux-image-2.6.15-26-686 2.6.15-26.46 2.6.15-26.47
2006-09-15 17:49:36 upgrade linux-restricted-modules-common 2.6.15.11-3 2.6.15.11-4
2006-09-15 17:49:39 upgrade linux-restricted-modules-2.6.15-26-686 2.6.15.11-3 2.6.15.11-4

My solution was to uninstall all of those packages with Synaptic (including the one with the major warning about removing the kernel image of the currently running kernel -- just make sure you do not turn off your computer before you get a replacement linux-image package installed).

Then I went into /var/cache/apt/archives and re-installed older versions of the same packages, effectively downgrading them below the level at which they broke the boot process' ability to "read -s"

I suspect that "read -s" is broken in the /bin/sh that is included in the initrd image because it is missing from busybox or whatever lightweight shell is included in that image. 

Google has precious few accounts of "read -s" not working in a shell. One of the solutions was to replace #!/bin/sh with #!/bin/bash at the top of the shell script. That will not work for the local-top/cryptoroot script in this HOWTO because "bash" is not included in the initrd image. 

One could try to compile it statically (so it did not require any libs that were not also included in the image) and stuff it into the initrd image, or use another "sh" replacement shell like "sash" that does understand the builtin command  read with the -s option for not echoing input onto the screen.

Since I don't know how to do that, I will just "lock" these linux-* packages at the current version (2.6.15-23-686) that works, where the initrd image that is made from them using "update-initramfs -v -u ALL" gets a shell interpreter that can do the -s.

Hopefully, the developers will fix whatever change caused "read -s" not to work in the initrd hook scripts, and it will all be good again in the next release.

---

### Post by Sine-Wave on 2006-10-09
I have tried three times to install and use the encrypted system and am getting very frustrated.

The error appears just before Enter LUKS passphrase.

Begin: Mounting root filesystem....
Begin: Running /scripts/local-top...
/scripts/local-top/cryptoroot:19:prereqs:not found
find keymap: no such file or directory
cannot open file /etc/console.kmap.gz

Enter LUKS passphrase  *****************

cant open device /dev/hda3

I'm unable to mount /dev/hda3 using a rescue disk.

Can you suggest where I'm messing up?

Close but no cigar

tia, George

---

### Post by Sine-Wave on 2006-10-09
I have tried three times to install and use the encrypted system and am getting very frustrated.

The error appears just before Enter LUKS passphrase.

Begin: Mounting root filesystem....
Begin: Running /scripts/local-top...
/scripts/local-top/cryptoroot:19 : prereqs:not found
find keymap: no such file or directory
cannot open file /etc/console.kmap.gz

Enter LUKS passphrase  *****************

cant open device /dev/hda3

I'm unable to mount /dev/hda3 using a rescue disk.

Can you suggest where I'm messing up?

Close but no cigar

tia, George

---

### Post by Sine-Wave on 2006-10-09
Sorry for all the wasted bandwidth. Please ignore the first two posts.

I have tried three times to install and use the encrypted system and am getting very frustrated.

The error appears just before Enter LUKS passphrase.

Begin: Mounting root filesystem....
Begin: Running /scripts/local-top...
/scripts/local-top/cryptoroot:19 : prereqs:not found
find keymap: no such file or directory

cannot open file /etc/console/boottime.kmap.gz


Enter LUKS passphrase *****************

cant open device /dev/hda3

I'm unable to mount /dev/hda3 using a rescue disk.

Can you suggest where I'm messing up?

What is /etc/console/boottime.kmap.gz supposed to do?

Close but no cigar

tia, George
Reply With Quote

---

### Post by master2001 on 2006-10-27
Hi all,

first of all thanks to Mikhail for his wonderfull Howto. I work this for about 3 Months now and it used to work great. Now to my question:
I updated one of my machines that are fully encrypted (according to this howto) to edgy eft (with update-manager).
Now I can't start boot to the new kernel (2.6.17-generic). I am asked for the Password to decrypt the root partition, but after that really nothing happens. I already recreated the ramdisk a dozen times and disabled the bootsplash without any success.
If I but to the old kernel (2.6.15-26) everything works (I just can't start X, because the nvidia modules don't mach the kernel anymore, but that's another problem).
Has anybody else experienced this problems with cryptsetup ? Has someone an Idea how this can be fixed.

Your help is greatly appreciated.

Thanks in advance
Michael

P.s.: Im running Ubuntu for AMD64

---

### Post by master2001 on 2006-10-27
Hi all,

sorry, but it seems that I gave an false description of my problem. In fact I can start with the new kernel, I was just to impatient. With the old kernels (2.6.xx), after typing my password to decrypt the root partition the boot-sequence started immideatly. Now with edgy it lasts about 5 Minutes before the boot-process starts. Right before the boot-process starts I see "unable to find volume group "cryptoroot"". This message is shown with the older kernels as well, but after a signifcant shorter time.

Maybe somebody knows a solution for *this* problem ?

Thank you very much, and sorry again for spamming...
Michael

---

### Post by uptimebox on 2006-10-28
The howto is not useful on Edgy. If you want to upgrade your system you should read /usr/share/doc/cryptsetup/CryptoRoot.HowTo (installed with Edgy version of cryptsetup). And first of all you should remove "ramdisk = /usr/sbin/mkinitramfs" from /etc/kernel-img.conf

---

### Post by zetetic on 2006-10-29
Hi, I'm an ubuntu nob and this is my first post here, so please forgime my lack of knowledge.

I'm running Ubuntu dapper LTS and I'm very pleased with the system. I'm finally feeeling windows free and that is a great sensation!

I have followed the "EncryptedFilesystem" (by Mikhail Lukyanchenko) and "EncryptedFilesystemHowto5" (by John Bindel) HOWTOs and I managed to get a perfectly working encrypted system.

My system (a Pentium 4 desktop, 120 GB hard drive with just Ubuntu on it) has the following partitions:
a) hda1 (unencrypted -> /boot)
b) hda2 (encrypted -> /)
c) hda3 (encrypted -> /home)
d) hda5 (encrypted -> swap)
e) hda6 (encrypted -> /cryptokeys)

I have both desktop environments: GNOME and KDE.

Everything is working perfectly but now I want to upgrade to Edgy, using the internet method described on "EdgyUpgrades" (I mean using the <gksu "update-manager -c"> method).

When rebooting for the first time after upgrading to Edgy, I want to keep the perfectly working encrypted system I have now.

So it would be nice if someone could please describe here how can this be accomplished.
If you don't mind please post the commands one must enter on terminal in order to keep the perfectly working encrypted system when upgrading to Edgy.

---

### Post by RichJacot on 2006-10-30
Hello, I am also wanting to upgrade or install Edgy with encrypted root and swap.

---

### Post by srf21c on 2006-11-08
Just got encrypted root and data (/home) working on fresh Edgy 6.10 installation.  You need to update some of the cryptoroot script file paths to the keyboard map, but other than that, not much difference.  

Disk partitioning setup is as follows

/dev/hda1   20MB     ext2     /boot
/dev/hda2   10GB     jfs      /
/dev/hda3   40GB     jfs      /home
/dev/hda4            Extended
/dev/hda5   1.5GB    Linux swap

Still having an issue with swap.  Getting the following error when trying to restart the cryptdisks

```
$ sudo invoke-rc.d cryptdisks restart
 * Stopping remaining crypto disks..   [ok ]
 * Starting remaining crypto disks...    -e 
 - The device /dev/hda5 contains a valid filesystem type swap. -e 
 - the precheck for '/dev/hda5' failed, skipping
```
Here's my fstab

```
# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 ext 20MB boot partition
UUID=edf91354-b92e-489d-aab9-a5a263431cf3 /boot           ext2    defaults        0       2

# encrypted LUKS root partition
/dev/mapper/cryptoroot  /       jfs     defaults,errors=remount-ro 0       1

# encrypted LUKS data partition
/dev/mapper/cryptodata /home    jfs     nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid   0       2
# encrypted swap partition
/dev/mapper/cryptoswap  none    swap    sw              0       0

# cdrom
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```
And crypttab

```
# <target name> <source device>         <key file>      <options>
cryptoswap      /dev/hda5       /dev/urandom    swap

```

Please savor the following attached config files which have been updated for use with Edgy.  

CAVEAT: the local-top/cryptoroot file has been modified to mount additional encrypted partitions as per "witty Names" excellent [contribution here]("http://www.ubuntuforums.org/showpost.php?p=1276393&postcount=26")

-Seth

---

### Post by RichJacot on 2006-11-08
Hello,

For your swap issue, I had the same thing this past weekend when I was trying to get my /, swap and /home encrypted on a fresh install of edgy.

I hope I can remember it clearly enough....

1) sudo swapoff -a
2) delete your swap partition and create a new one but don't format it to anything yet. (I'm sure of this step)
3) now the fuzzy part.  I think I formatted it with luksformat.
4) sudo swapon -a OR after you've updated your fstab and crypttab files try: sudo /etc/init.d/cryptdisks start .  Sorry but I can't exactly recall what I did after I deleted and recreated the partition...  Maybe this is enough to get you going in the right direction though.

The howto I went from and had the same issue with swap as you are is:
[http://help.ubuntu.com/community/EncryptedFilesystemHowtoEdgy]("http://help.ubuntu.com/community/EncryptedFilesystemHowtoEdgy")

I also notice you have /dev/urandom in your /etc/crypttab file.  I have /dev/random.  Both seem to work for me but I don't know what the difference is.  Does anyone know what the difference is?

If you still have trouble with your swap, let me know and I can go back through my bash history, or do mine over from scratch and document it as I go.  The reason I can't look at my bash history now is, I unhooked all my other drives and installed edgy from scratch on a new drive, which isn't hooked up right now.

I will try to get my /home working per your post and let you know how I make out.  Right now I have swap and root working just fine, but my /home won't work on boot as I would like or via login as the above link suggest.  I can mount it up encrypted by hand though (but that's not what I'm looking for).

---

### Post by srf21c on 2006-11-08
alright, I'm going to try disabling the swap partition and then blasting it with the dd command.

```

sudo swapoff -a

dd if=/dev/urandom of=/dev/hda5
```

and typing ```
kill -USR1 `pidof dd`
``` to check on the progress. 

Thanks to b0rsten for [that cool trick]("http://www.ubuntuforums.org/showpost.php?p=1003257&postcount=2")

Then I'll try firing up the cryptdisks again

```
sudo /etc/init.d/cryptdisks start
```

Yeah babay!  no errors now...

```
desktop:~$ sudo /etc/init.d/cryptdisks start
 * Starting remaining crypto disks...              [ ok ]
desktop:~$ sudo swapon -a
desktop:~$ 
```

Running a mount command does not show any mounted swap partitions however....should that be of concern?

---

### Post by RichJacot on 2006-11-08
Did your dd ever finish?  I ran the dd random command line on my 1.5GB swap and it never came back.  After about 40 minutes I broke it with ctrl-C and continued on.

---

### Post by srf21c on 2006-11-08
> **RichJacot said:**
> Did your dd ever finish?  I ran the dd random command line on my 1.5GB swap and it never came back.  After about 40 minutes I broke it with ctrl-C and continued on.

Mine took 5-10 minutes for 1.5G, I was able to check the progress using the kill -USR1 command as described in the earlier post and verify how much data had been overwritten.  

I also used /dev/urandom if that makes any difference.

---

### Post by RichJacot on 2006-11-08
I didn't know about the command to check the progress until you mentioned it (thank you btw).  I will check it next time.  I did use random not urandom so I will also change that next time, or try both.

So did you get your swap encrypted?

---

### Post by srf21c on 2006-11-11
Swap is now encrypted.   

```
~$ cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/mapper/cryptoswap                  partition       755012  0       -1

```
I could have sworn that I already posted about this a few days ago...wonder if it got erased when the site was having database problems recently.

It may be worth noting that I've had nothing but problems using aptitude to upgrade command line installations of Edgy 6.10 to the xubuntu-desktop metapackage, (or whatever the technical term for the desktop suite packages are.)     

I have been able to repeat the "sudo aptitude install xubuntu-desktop" problem on two separate command-line xubuntu 6.10 installations.  Usually there are about 5-6 packages that it complains about, and it fails to download at least half of what's needed to complete the xubuntu desktop suite.  

For whatever reason, apt-get installs of xubuntu-desktop seem to be much more reliable.  Even though aptitude is supposedly a superior tool with better dependency handling, in this particular case I'd recommend using apt-get instead as per the original howto doc.

---

### Post by gnomeza on 2006-11-12
> **RichJacot said:**
> I also notice you have /dev/urandom in your /etc/crypttab file.  I have /dev/random.  Both seem to work for me but I don't know what the difference is.  Does anyone know what the difference is?

/dev/random generates random bytes from movements of the mouse, typing on the keyboard, fluctuations in CPU temperature etc.  /dev/urandom is a pseudo-random-number-generator. ([http://en.wikipedia.org/wiki/PRNG](http://en.wikipedia.org/wiki/PRNG))

/dev/random is a *lot* slower than /dev/urandom. /dev/random will quickly use up the kernel entropy pool and block until more entropy bytes become available. For mounting /swap it's fair to use /dev/random. For writing random data over a disk you *definitely* want to use /dev/urandom.

---

### Post by gnomeza on 2006-11-12
> **uptimebox said:**
> The howto is not useful on Edgy. If you want to upgrade your system you should read /usr/share/doc/cryptsetup/CryptoRoot.HowTo (installed with Edgy version of cryptsetup). And first of all you should remove "ramdisk = /usr/sbin/mkinitramfs" from /etc/kernel-img.conf

Thanks uptimebox. I actually used your howto to get full disk encryption working with Edgy before I read your comment. ;)

I have /dev/hda14 LUKS encrypted.
I had some problems on the luksOpen call. It seems udev hadn't finished creating all the /dev nodes. (Adding ls /dev/hda* to the script just above the cryptsetup call only showed *some* of the hda partitions). I solved this by adding a delay loop that waited for /dev/hda14 to appear.

Since I have LVM within the encrypted /dev/hda14, I also added cryptoroot as a dependency for the local-top/lvm script. Don't know if this actually made any difference though...

Thanks for a great howto!

---

### Post by srf21c on 2006-11-21
One last issue I'd like to raise is how to best backup an encrypted root filesystem.   I'd prefer image backups and have been investigating the pros and cons of dd vs. partimage.   I imagine that the encryption however, pretty much negates any advantages partimage has over dd.

What would be the best way to backup and restore a complete operating system that is located on an encrypted / partition?  Let's assume /home is mounted on another partition, backed up separately and can be left out of the equation.

Update:  A little google-magic revealed a [previous discussion of this topic]("http://www.ubuntuforums.org/showthread.php?t=120091&page=4").

I'm trying this command for starters.  Note the leading sudo sh -c syntax and quotation marks which allow for proper shell redirection while using the sudo command. 

```
sudo sh -c "dd if=/dev/hda2 | gzip > /mnt/exthd/testbak.gz"
```

Previously I did a straight "dd" disk dump of the 10GB encrypted / (root) partition to an external USB 2.0 hard drive, and it took approx 40 minutes, averaging 4.3MB/sec.    I'm curious to find out what difference the gzip compression will make, if any.

Another update:  Ok, WOW.  The command above cut the backup time in half to approx 21 minutes.  Throughput climbed to 7.9MB/sec.  Backup file size was 8GB, and the root partition contained 3.7GB of actual data.

---

### Post by optevo on 2006-11-21
> **srf21c said:**
> One last issue I'd like to raise is how to best backup an encrypted root filesystem.

I'm considering having an external USB/firewire disk that has the same configuration as my laptop (including an encrypted root). When I want to backup, I'll mount it and do an rsync to it which should be pretty efficient. The data is backed up to a secure destination and the bonus is that if anything goes wrong with my laptop, I can just boot to the external drive and my backup is "live" so I can get to work straight away. I can also take the backup image to work, use it there and "reverse backup" onto my hard drive to synchronise any changes.

Cheers,
R/

---

### Post by optevo on 2006-11-21
Hi all,

I got Edgy working with an encrypted root using LUKS mostly by following the instructions for Dapper [here]("https://help.ubuntu.com/community/EncryptedFilesystem")
However, there were a few things I needed to change:

In **/etc/initramfs-tools/hooks/cryptoroot**, I had to change

```
cp /etc/console/boottime.kmap.gz ${DESTDIR}/etc/console
```

to

```
cp /etc/console-setup/boottime.kmap.gz ${DESTDIR}/etc/console
```


Also, in **/etc/initramfs-tools/local-top/cryptoroot** I got rid of
```
if grep -q splash /proc/cmdline; then
       /sbin/usplash -c &
       sleep 1
fi
```

As it complained that usplash wansn't found and when I installed it, the boot screen came up blank...
*(Why?)*

**$ sudo update-initramfs -u ALL**
produces an error "Command failed" but this already seem to be noted [here]("https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/61122") and it doesn't seem to be fatal

Finally, before mounting the (formerly root) partition as a swap, I used a hint from [here]("https://help.ubuntu.com/community/EncryptedFilesystemHowto5") to run
**$ sudo dd if=/dev/urandom of=/dev/???**
before running
**$ sudo invoke-rc.d cryptdisks restart**
otherwise it complained that my swap partition was ext3 (which it was of course...)

One last thing, when I boot and after I enter my passphrase, my root partition mounts sucessfully but I still get a message:
**No cryptroot configured, skipping**
*(Why?)*

If anyone would like to see my config files, tell me and I'll post them.

If anyone has any answers/suggestions to my (minor) questions, I'd appreciate any feedback...

Cheers,
R/

---

### Post by kbarrett on 2006-11-21
Just some guesses re your "why?"s

> Also, in /etc/initramfs-tools/local-top/cryptoroot I got rid of
Code:

if grep -q splash /proc/cmdline; then /sbin/usplash -c & sleep 1 fi

As it complained that usplash wansn't found and when I installed it, the boot screen came up blank...
(Why?)

Because /sbin/usplash is in your root directory ... it ain't mounted yet, maybe?

> One last thing, when I boot and after I enter my passphrase, my root partition mounts sucessfully but I still get a message:
No cryptroot configured, skipping
(Why?)

Were you calling root "cryptoroot" or cryptroot"? Or both, maybe?

---

### Post by qiet72 on 2006-11-26
scripts/local-top/cryptroot is automatically installed when you install the deb package cryptsetup.  It is currently not used yet.  Ignore the message.

---

### Post by gnomeza on 2006-11-27
> **optevo said:**
> One last thing, when I boot and after I enter my passphrase, my root partition mounts sucessfully but I still get a message:
**No cryptroot configured, skipping**
*(Why?)*


Your script (/etc/initramfs-tools/.../local-top/cryptoroot) is being installed alongside the default one (/usr/initramfs-tools/.../local-top/cryptroot). Rename your cryptoroot scripts to cryptroot and the default won't be installed.

The best way to check this is to run mkinitramfs manually like so:
```
mkinitromfs -k -o /boot/initrd.img-`uname -r` `uname -r`

```
 and have a look at the temporary directory tree it leaves behind. (This will update the image for the currently running kernel only)

---

### Post by hardskinone on 2006-12-06
I installed Dapper following tutorial in first post. After the release I upgraded to Edgy with standard way. 

I [recorded]("http://hardskinone.planetweblog.net/luksedgy.tar.bz2")  what happens. I choose the edgy kernel, 2.6.17-10 (one.mov), insert passphrase but nothing happens( two.mov), ctrl+F1 shows the message (three.mov):

[INDENT]/scripts/local-top/cryptoroot: /scripts/local-top/cryptoroot/: 30: sleep: not found[/INDENT]

When booting with an old (2.6.15-26) kernel everything runs fine. Any help?

Thanks.

---

### Post by lprofil on 2006-12-12
> **hardskinone said:**
> I installed Dapper following tutorial in first post. After the release I upgraded to Edgy with standard way. 

I [recorded]("http://hardskinone.planetweblog.net/luksedgy.tar.bz2")  what happens. I choose the edgy kernel, 2.6.17-10 (one.mov), insert passphrase but nothing happens( two.mov), ctrl+F1 shows the message (three.mov):

[INDENT]/scripts/local-top/cryptoroot: /scripts/local-top/cryptoroot/: 30: sleep: not found[/INDENT]

When booting with an old (2.6.15-26) kernel everything runs fine. Any help?

Thanks.

The kernel is the reason if i am not misstaken. A new initram.fs is created when you install cyptsetup which imho means that this feature is activated in the new created kernel.

Please corect me if i am wrong.

A simple 

```
apt-get install cryptsetup
```

might do the trick. Give it a trial and post your feedback.

/lprofil

ps: cool idea to record your screen-output, but there might be another
    way to see the boot-dump: 
```
cat /var/log/boot
```
;)

---

### Post by pornasterXRW on 2006-12-25
[anime girl teen](http://anime-girl-teen.strazacy.pl) 
[girl next door anime](http://girl-next-door-anime.strazacy.pl) 
[gothic anime picture](http://gothic-anime-picture.strazacy.pl) 
[cool anime picture](http://cool-anime-picture.strazacy.pl) 
[dark anime picture](http://dark-anime-picture.strazacy.pl) 
[adult anime picture](http://adult-anime-picture.strazacy.pl) 
[anime display picture](http://anime-display-picture.strazacy.pl) 
[anime dvd review](http://anime-dvd-review.strazacy.pl) 
[anime de dessin disney dvd en walt](http://anime-de-dessin-disney-dvd-en-walt.strazacy.pl) 
[anime dvd torrent](http://anime-dvd-torrent.strazacy.pl) 
[anime dvd release](http://anime-dvd-release.strazacy.pl) 
[anime clip free hentai lesbian porn](http://anime-clip-free-hentai-lesbian-porn.strazacy.pl) 
[anime girl groupsmsncom hot site](http://anime-girl-groupsmsncom-hot-site.strazacy.pl) 
[free xxx anime movie](http://free-xxx-anime-movie.strazacy.pl) 
[free xxx anime video](http://free-xxx-anime-video.strazacy.pl) 
[anime xxx trailer](http://anime-xxx-trailer.strazacy.pl) 
[anime y hentai xxx](http://anime-y-hentai-xxx.strazacy.pl) 
[anime galore layout x3](http://anime-galore-layout-x3.strazacy.pl) 
[anime layout myspace web](http://anime-layout-myspace-web.strazacy.pl) 
[anime free iframe layout](http://anime-free-iframe-layout.strazacy.pl) 
[anime guitar music sheet](http://anime-guitar-music-sheet.strazacy.pl) 
[anime joshs music](http://anime-joshs-music.strazacy.pl) 
[free sexy anime](http://free-sexy-anime.strazacy.pl) 
[anime foxs sexy](http://anime-foxs-sexy.strazacy.pl) 
[3d adult anime game](http://3d-adult-anime-game.strazacy.pl) 
[big russian tit woman](http://big-russian-tit-woman.acb.pl) 
[*** big round tit vanessa](http://***-big-round-tit-vanessa.acb.pl) 
[big tit round *** jessica](http://big-tit-round-***-jessica.acb.pl) 
[big tit round *** porn](http://big-tit-round-***-porn.acb.pl) 
[*** big brandy round tit](http://***-big-brandy-round-tit.acb.pl) 
[*** big pic round tit](http://***-big-pic-round-tit.acb.pl) 
[*** big match tit](http://***-big-match-tit.acb.pl) 
[big tit sex clip](http://big-tit-sex-clip.acb.pl) 
[free big tit sex pic](http://free-big-tit-sex-pic.acb.pl)

---

### Post by bankervzer on 2006-12-26
[http://pnope.com/mwn](http://pnope.com/mwn) 
zqtbo rb eock975 bi0 6 0 hf9t

---

### Post by linux101 on 2006-12-26
I read through the HowTo. Good to see that something like that exists for Linux. But do I understand correctly that the /boot partition will still exist unencrypt? So the Kernel itself is on a non encrypted partition but everything else is encrypted

---

### Post by uptimebox on 2006-12-27
> **linux101 said:**
> I read through the HowTo. Good to see that something like that exists for Linux. But do I understand correctly that the /boot partition will still exist unencrypt? So the Kernel itself is on a non encrypted partition but everything else is encrypted

Yes, that is correct.

---

### Post by linux101 on 2006-12-27
I guess there is no way to also have the /boot partition encrypted. Also is there any way to get conclude from the information on the boot partition about the data on the other partitions. More curious than that its real importatent. But as I'm running of a laptop I think harddisk encryptrion is important.

---

### Post by uptimebox on 2006-12-27
> **linux101 said:**
> I guess there is no way to also have the /boot partition encrypted. Also is there any way to get conclude from the information on the boot partition about the data on the other partitions. More curious than that its real importatent. But as I'm running of a laptop I think harddisk encryptrion is important.

Atacker can make guess about your OS and kernel version, but beside this, encrypted data is inaccessible.

As I wrote before in this thread, atacker could theoretically inject keylogger in your initramfs and get your password later and only after you typed it on compromised system. This is strongest vurnability of encrypted root FS method.

---

### Post by practowrx on 2006-12-30
spam...

---

### Post by longdead on 2006-12-30
> **uptimebox said:**
> Atacker can make guess about your OS and kernel version, but beside this, encrypted data is inaccessible.

As I wrote before in this thread, atacker could theoretically inject keylogger in your initramfs and get your password later and only after you typed it on compromised system. This is strongest vurnability of encrypted root FS method.

Can't you just store a md5sum or even a separate copy of everything for comparison later, and say store on an encrypted removable drive?  Then just periodically check it.


Also, if anyone is having trouble using an alternate keymap in edgy, like dvorak I figured out how to get it to work.

I had to install the console-data package to get the file (i386 even on an amd64 machine)
```
/usr/share/keymaps/i386/dvorak/dvorak.kmap.gz
```
and then I had to copy it to
```
/etc/console-setup/dvorak.kmap.gz
```

also the following files had to be copied

```
/usr/share/keymaps/i386/include/linux-with-alt-and-altgr.inc.gz
/usr/share/keymaps/i386/include/linux-keys-bare.inc.gz
```
to
```
/etc/console-setup/linux-with-alt-and-altgr.inc.gz
/etc/console-setup/linux-keys-bare.inc.gz
```

those will change based on what keymap you want to use though, and I don't know how to tell which ones any given keymap will need, the only way I know to figure it out is through trial and error, you'll get an error following the message about loading the keymap, just before it prompts you for the passphrase

then I had to add the following lines along with everything else from the howtos

```
mkdir ${DESTDIR}/etc/console-setup
cp /etc/console-setup/dvorak.kmap.gz ${DESTDIR}/etc/console-setup
cp /etc/console-setup/linux-keys-bare.inc.gz ${DESTDIR}/etc/console-setup
cp /etc/console-setup/linux-with-alt-and-altgr.inc.gz ${DESTDIR}/etc/console-setup
copy_exec /bin/loadkeys /bin
```

to 

```
/etc/initramfs-tools/hooks/cryptoroot
```

---

### Post by NobodySpecial on 2006-12-31
Some points from *Linux Magazine*, Issue 72, November 2006, "Secret Candidates" by Peter Gutmann and Christian Ney.  They write that the default settings are for DM-Crypt insecure.  They propose a better way:
> The *-c aes-cbc-essiv:sha256* parameter tells DM-Crypt to write data in CBC (Cipher Block Chaining) mode and supply a SHA-256 hashed initialization vector.  Without these parameters, the data would be susceptible to watermarking, a hack that involves the attackerpreparing files and proving that the files reside within the contianer despite encryption.  If you do not trust the default key length of 128 bits, you can double this by specifying -s 256.

Now one point of my own.  Instead of using the "dd" command to write random data, you can use the "badblocks" command to both check for bad block and write random data.  An additional advantage is that the program keeps a running status report of its progress.  It takes an hour or so per 100 gigabytes.

So instead of:
```
sudo luksformat -t ext3 /dev/hda3
```

Consider the following:
```
sudo /sbin/badblocks -c 10240 -s -w -t random -v /dev/hda3
sudo cryptsetup --verbose --verify-passphrase --cipher aes-cbc-essiv:sha256 --key-size 256 luksFormat /dev/hda3
sudo /sbin/mkfs.ext3 -j -m 1 -O dir_index,filetype,sparse_super /dev/mapper/hda3

```
Happy encrypting!  :-D

---

### Post by IntuitiveNipple on 2007-01-03
Are there any performance-hit or installation/configuration issues in using this on a softRAID system, especially for a mirror ?

---

### Post by garmonbwx on 2007-01-03
[hardcore public sex](http://fm7.biz/qji) 
[free hardcore porn](http://fm7.biz/qjj) 
[mature hardcore porn](http://fm7.biz/qjk) 
[hardcore indian porn](http://fm7.biz/qjl) 
[party hardcore video](http://fm7.biz/qjm) 
[party hardcore movie free](http://fm7.biz/qjn) 
[drunk hardcore party slut](http://fm7.biz/qjo) 
[free hardcore junky](http://fm7.biz/qjp) 
[max hardcore video](http://fm7.biz/qjq) 
[download max hardcore](http://fm7.biz/qjr) 
[max hardcore taylor rain](http://fm7.biz/qjs) 
[gay man ******* hardcore](http://fm7.biz/qjt) 
[******* hardcore wmv](http://fm7.biz/qju) 
[teen hardcore movie](http://fm7.biz/qjv) 
[free teen hardcore](http://fm7.biz/qjw) 
[hardcore partying video](http://fm7.biz/qjx) 
[hardcore partying wet](http://fm7.biz/qjy) 
[hardcore partying password](http://fm7.biz/qjz) 
[free hardcore porn sample](http://fm7.biz/qk0) 
[daily free gallery hardcore porn](http://fm7.biz/qk1) 
[free teen hardcore porn gallery](http://miniurl.pl/20522) 
[free hardcore porn movie](http://miniurl.pl/20523) 
[black hardcore sex movie](http://miniurl.pl/20524) 
[free long hardcore movie](http://miniurl.pl/20525) 
[free black hardcore movie](http://miniurl.pl/20526) 
[hardcore asian anal](http://miniurl.pl/20527) 
[young asian hardcore](http://miniurl.pl/20528) 
[asian hardcore sex picture](http://miniurl.pl/20529) 
[hardcore lesbian sex teen](http://miniurl.pl/20530) 
[free hardcore ****](http://miniurl.pl/20531) 
[hardcore gay male sex](http://miniurl.pl/20532) 
[free hardcore gay sex video](http://miniurl.pl/20533) 
[anal hardcore party](http://miniurl.pl/20534) 
[extreme anal hardcore](http://miniurl.pl/20535) 
[hardcore anal bitch](http://miniurl.pl/20536) 
[anal hardcore mellons](http://skocz.pl/cuai) 
[free hardcore picture](http://skocz.pl/cuaj) 
[free gay hardcore picture](http://skocz.pl/cuak) 
[hardcore picture pure](http://skocz.pl/cual) 
[hardcore max picture](http://skocz.pl/cuam) 
[hardcore picture sex video](http://skocz.pl/cuan) 
[party hardcore movie free](http://skocz.pl/cuao) 
[asian hardcore sex picture](http://skocz.pl/cuap) 
[free hardcore porn](http://skocz.pl/cuaq) 
[teen hardcore movie](http://skocz.pl/cuar) 
[free black hardcore movie](http://skocz.pl/cuas) 
[black hardcore sex movie](http://skocz.pl/cuat) 
[mature hardcore porn](http://skocz.pl/cuau) 
[young asian hardcore](http://skocz.pl/cuav) 
[download max hardcore](http://skocz.pl/cuaw)

---

### Post by flaviarezx on 2007-01-04
[hardcore public sex](http://skiltechurl.com/PC8T7Ud) 
[free hardcore porn](http://skiltechurl.com/fQKk35a) 
[mature hardcore porn](http://skiltechurl.com/U4hIkfq) 
[hardcore indian porn](http://skiltechurl.com/cskGBKX) 
[party hardcore video](http://skiltechurl.com/KR+ln4U) 
[party hardcore movie free](http://skiltechurl.com/4skRvdU) 
[drunk hardcore party slut](http://skiltechurl.com/yCvdcvD) 
[free hardcore junky](http://skiltechurl.com/G9lk8KB) 
[max hardcore video](http://skiltechurl.com/1WSl99J) 
[download max hardcore](http://skiltechurl.com/2yVJoXA) 
[max hardcore taylor rain](http://skiltechurl.com/lEtpJKP) 
[gay man ******* hardcore](http://skiltechurl.com/Zy4F9ld) 
[******* hardcore wmv](http://skiltechurl.com/XIcRdgP) 
[teen hardcore movie](http://skiltechurl.com/GCmui9V) 
[free teen hardcore](http://skiltechurl.com/ADuWqeQ) 
[hardcore public sex](http://hardcore-public-sex.da.cx) 
[free hardcore porn](http://free-hardcore-porn.da.cx) 
[mature hardcore porn](http://mature-hardcore-porn.da.cx) 
[hardcore indian porn](http://hardcore-indian-porn.da.cx) 
[party hardcore video](http://party-hardcore-video.da.cx) 
[party hardcore movie free](http://party-hardcore-movie-free.da.cx) 
[drunk hardcore party slut](http://drunk-hardcore-party-slut.da.cx) 
[free hardcore junky](http://free-hardcore-junky.da.cx)

---

### Post by RichJacot on 2007-01-04
Very good question.  

I'm just trying/using an encrypted root and swap with LUKS for the first time and didn't what to over complicate things the first time through with trying to mirror it.  I have always used sofware RAID in the past, so I would also be interested this.

---

### Post by shalemonsx on 2007-01-04
[hardcore picture pure](http://www.mcturl.com/?r=955) 
[hardcore max picture](http://www.mcturl.com/?r=956) 
[hardcore picture sex video](http://www.mcturl.com/?r=957) 
[party hardcore movie free](http://www.mcturl.com/?r=958) 
[asian hardcore sex picture](http://www.mcturl.com/?r=959) 
[free hardcore porn](http://www.mcturl.com/?r=960) 
[teen hardcore movie](http://www.mcturl.com/?r=961) 
[free black hardcore movie](http://www.mcturl.com/?r=962) 
[black hardcore sex movie](http://www.mcturl.com/?r=963) 
[mature hardcore porn](http://www.mcturl.com/?r=964) 
[young asian hardcore](http://www.mcturl.com/?r=965) 
[download max hardcore](http://www.mcturl.com/?r=966)

---

### Post by uptimebox on 2007-01-05
> **RichJacot said:**
> Very good question.  

I'm just trying/using an encrypted root and swap with LUKS for the first time and didn't what to over complicate things the first time through with trying to mirror it.  I have always used sofware RAID in the past, so I would also be interested this.
I can confirm, that I run several LUKS + RAID + LVM production systems successfully over one year at this moment. Though, I use Debian on those systems, but I don't think this makes much difference. Can't tell you anything about performance, because I haven't made any tests. Encryption was the first priority condition on those installations.

---

### Post by korralblerm on 2007-01-10
hello guys! this forum is good, but i am a newbie in this thema. 
Please, tell me where i can read more about this problema. 
^^ many thanks, korra#@%@*^#@!  ^^

---

### Post by kostroslpa on 2007-01-12
[free porn vids](http://urlzip.de/643) 
[hentai porn](http://urlzip.de/644) 
[hairy *****](http://urlzip.de/645) 
[celeb sex](http://urlzip.de/646) 
[swinger porn](http://urlzip.de/647) 
[lesbian sex](http://urlzip.de/648) 
[pissing](http://urlzip.de/649) 
[nylon](http://urlzip.de/64a) 
[ebony porn](http://urlzip.de/64b) 
[porn star](http://urlzip.de/64c) 
[gay porn](http://urlzip.de/64d) 
[gay hardcore porn](http://www.mcturl.com/?r=1502) 
[ebony hardcore](http://www.mcturl.com/?r=1503) 
[hardcore porn teen](http://www.mcturl.com/?r=1504) 
[hardcore shemale](http://www.mcturl.com/?r=1505) 
[lesbian group sex](http://www.mcturl.com/?r=1506) 
[lesbian anal sex](http://www.mcturl.com/?r=1507) 
[asian lesbian sex](http://www.mcturl.com/?r=1508) 
[anal free porn sex](http://www.mcturl.com/?r=1509) 
[mature interracial](http://www.mcturl.com/?r=1510) 
[free mature porn](http://www.mcturl.com/?r=1511) 
[buy a house in toronto](http://fm7.biz/sjd) 
[condo for sale in toronto](http://fm7.biz/sje) 
[home for sale in toronto](http://fm7.biz/sjf) 
[buy new home in toronto](http://fm7.biz/sjg) 
[new condo in toronto](http://fm7.biz/sjh) 
[house toronto buy](http://fm7.biz/sji)

---

### Post by IamAcoconut on 2007-01-12
Nice howto, **uptimebox**! I've got a question though.

How to set it all up If I'm not installing Ubuntu from scratch, but I already have a desktop version installed, and don't wanna lose it, just swich to encrypted filesystem. What should be done differently?
For instance, there's no boot partition on my HDD - is that a problem?

Thanks in advance! :)

---

### Post by uptimebox on 2007-01-13
> **IamAcoconut said:**
> Nice howto, **uptimebox**! I've got a question though.

How to set it all up If I'm not installing Ubuntu from scratch, but I already have a desktop version installed, and don't wanna lose it, just swich to encrypted filesystem. What should be done differently?
For instance, there's no boot partition on my HDD - is that a problem?

Thanks in advance! :)

I'm afraid it is not possible to implement this method without boot partition. Though, you can use some partition voodoo to create it.

---

### Post by IamAcoconut on 2007-01-13
Voodoo?
Where can I find some info on how to create boot partition, so that I don't mess up my current configuration?

---

### Post by honeydew on 2007-01-21
Does anyone know of a way that the cryptosetup could handle more then 1 login? or more than one password?  and more then 1 encrypted disk?  I see many possible reasons for this, and I hope others do as well.  I havnt dived writing code, however I have started to think of ways I could piece this together.  If anyone has any experience with this please give me a heads up.  I have heard of something like this called rubberhoseFS but I havnt been able to find much on this except dead links.

Thanks.

---

### Post by NobodySpecial on 2007-01-21
honeydew - its easy to have more than one passphrase:
```

sudo cryptsetup luksAddKey --verify-passphrase /dev/hda3
```

---

### Post by IamAcoconut on 2007-01-22
BTW I was using an already installed desktop ubuntu. What does LUKS care if it's server or desktop?

**!Edit**:

While booting the **Cryptotest** I get```
Error 24: Attempt to acces block outside partition 
```

What could this mean?

---

### Post by uptimebox on 2007-01-23
> **IamAcoconut said:**
> BTW I was using an already installed desktop ubuntu. What does LUKS care if it's server or desktop?

It doesn't matter.

---

### Post by daricusjn on 2007-01-24
Hello, guys i have some questions about this thema. 
Can anyone help me? 
Many thanks.

---

### Post by misty soul on 2007-01-30
> **master2001 said:**
> 
With the old kernels (2.6.xx), after typing my password to decrypt the root partition the boot-sequence started immideatly. Now with edgy it lasts about 5 Minutes before the boot-process starts. 


I have exactly the same problem on a laptop after upgrading from dapper to edgy.
Following all hints from the last version allowed me to get rid of the *unable to find volume group "cryptoroot"* message.
However, the timeout is still there. :confused:
This is really annoying, 5 minutes it is loooong looking at a frozen black screen

---

### Post by misty soul on 2007-02-06
> **misty soul said:**
> I have exactly the same problem on a laptop after upgrading from dapper to edgy.
Following all hints from the last version allowed me to get rid of the *unable to find volume group "cryptoroot"* message.
However, the timeout is still there. :confused:
This is really annoying, 5 minutes it is loooong looking at a frozen black screen

After having fought with that bug and found it was due to a waiting loop in a script installed by lvm-common, I finally found it was a well known bug :(. Here are the links to the two bugs threads : [bug #69217]("https://launchpad.net/ubuntu/+source/lvm-common/+bug/69217") and [bug #21878]("https://launchpad.net/ubuntu/+source/cryptsetup/+bug/21878").

Also the method described in this tutorial is now integrated in Edgy, so there is no more need to set up the cryptoroot scripts for initramfs, they already exist. The only point is to add a line for root in /etc/crypttab, it will be used by the new initramfs scripts from edgy.

---

### Post by IamAcoconut on 2007-02-06
Can someone tell me, how should the **fstab** and crypttab **entries** refer to "**cryptoswap**" in **Edgy**? Any examples?

---

### Post by misty soul on 2007-02-07
> **IamAcoconut said:**
> Can someone tell me, how should the **fstab** and crypttab **entries** refer to "**cryptoswap**" in **Edgy**? Any examples?

here is the entry I use in my /etc/fstab:
[FONT="Courier New"]# <file system>        <mount point>   <type>      <options>     <dump>  <pass>
/dev/mapper/cryptoswap none            swap        sw            0       0[/FONT]

and here is the entry I use in /etc/crypttab:
[FONT="Courier New"]# <target name> <source device>     <key file>      <options>
cryptoswap  /dev/mapper/vg00-swap   /dev/random     swap
[/FONT]
In my case, the raw encrypted device for swap is a logical volume handled by LVM, this explains the /dev/mapper/vg00-swap item.

---

### Post by IamAcoconut on 2007-02-10
Thanks, Misty!
How can I verify if my swap is encrypted and working?

---

### Post by misty soul on 2007-02-10
You can check how swapping is configured by running the following command in a terminal window:
```
cat /proc/swaps
```
This would show you the device used for swapping. For example if you have used cryptoswap in the /etc/crypttab entry, you should see /dev/mapper/cryptoswap in the output of the command.

You can check the device mapper status for the device by running the following command in a terminal window:
```
sudo dmsetup cryptoswap
```
you should see if state is ACTIVE

You can also use a graphical system monitoring application, look in the System->Administration menu if you are running Gnome, there should be something equivalent in KDE too. This should show you how swap is currently used. You may try to load your system (launching many demanding applications like browsers, image file editors ...) to see how memory usage changes.

---

### Post by IamAcoconut on 2007-02-10
It's not active :/
Here's my entry for swap in fstab:```
# /dev/hda3
/dev/mapper/cryptoswap none            swap    sw              0       0
```
and in crypttab: ```
cryptoswap      /dev/mapper/cryptoswap      /dev/urandom    swap
```
How can I make it work? Or perhaps I should use UUID's instead of /dev/mapper/...?

---

### Post by misty soul on 2007-02-11
> **IamAcoconut said:**
> It's not active :/
Here's my entry for swap in fstab:```
# /dev/hda3
/dev/mapper/cryptoswap none            swap    sw              0       0
```
and in crypttab: ```
cryptoswap      /dev/mapper/cryptoswap      /dev/urandom    swap
```
How can I make it work? Or perhaps I should use UUID's instead of /dev/mapper/...?

The /etc/crypttab entry looks weird to me. If you look at the man page for this file (man crypttab in a terminal window), you will see the first field is a <target device> while the second field is a <source device>.

Encryption can be seen as a filtering layer between the disk and the applications. The <source device> (second field) is the raw device on the disk side. If you use directly a disk partition, it should be something like /dev/hda1 or /dev/hda2 or ... This is the device on which the crypto layers reads and writes encrypted bytes. The crypto layer is the **only one** to use this device as it is completely scrambled for other applications which do not know the encryption key. The <target device> (first field) is the meaningful part on the applications side. This device is used to read and write decrypted bytes. It is a single name you can choose as you want. If you choose someName the crypto layer will build a new mapped device called /dev/mapper/someName. This is the device that should appear in the /etc/fstab entry which will be used by the swapping code which is on the application side of the crypto layer. Note that the first field only uses the file name part of the device (/dev/mapper/ will be prepended automatically) whereas the second fields is a fully qualified path.

In your /etc/crypttab file, both fields refer to the same device /dev/mapper/cryptoswap, which is most probably wrong.

I suggest to replace the second field by the fully qualified path of some existing device. If you use a hard disk partition, it should be something like /dev/hdai for IDE disks or /dev/sdai for SCSI or SATA disks if I remember correctly. In the example I showed in a previous message in this thread, I used /dev/mapper/vg00-swap because I did not use a hard disk partition but another filtering layer which provides logical volume features (this is a sort of dynamics partitioning mechanism unrelated to crypto but using the same layering mechanism provided by the device mapper).

---

### Post by IamAcoconut on 2007-02-21
Sure it works!
I just tried to be too clever, it turns out. Thaks.

BTW, how to set up another encrypted partition, that would get mounted on boot (same psswd as for cryptoroot)? Same as with cryptoswap?

---

### Post by misty soul on 2007-02-21
You should not do it exactly the same way as root or swap because :
[LIST=1]
[*]root is special because it should be mounted from the early init ramfs stage
[*]swap is special because it uses a random key which is different at each boot
[/LIST]

Suppose for example you want /home and /var to be encrypted. These two partitions will be mounted after root, so you can rely on the configuration files in /etc (namely /etc/fstab and /etc/crypttab), but you will **not** use a random key. So you should end up with something like that:

/etc/fstab:
[FONT="Courier New"]/dev/mapper/cryptohome /home ext3 defaults 0 2
/dev/mapper/cryptovar /var ext3 defaults 0 2[/FONT]

/etc/crypttab:
[FONT="Courier New"]cryptohome /dev/hda5 none luks
cryptovar /dev/hda6 none luks[/FONT]

In this case, I used *none* for the key to specify the the user should be asked interactively for the key. It may be cumbersome to be asked three times for a key at each boot: once for root, once for /home and once for /var.

If you consider your root encrypted root partition is safe enough with its own encryption, you can instead use some files (say /etc/home.key and /etc/var.key) so that you enter only the root key. There are scripts lying around to change the initramfs behavior and reuse the key for several partitions, but they don't seem to be reliable with busybox (which is used in initramfs). If you choose to store the keys in /etc, I would **strongly** suggest *against* using the same key for root and the other partitions. You should also remember that once your system has boot up, /etc is mounted unencrypted. If someone breaks access into this machine while it is running, the key files are there and could be read. So they **must** be protected in addition to be stored in an encrypted root.

If you don't want to have key files stored on disk and want to enter only one password and don't want to hack initramfs boot scripts, then you should try something more complex like using LVM for providing different partitions on top of the crypto layer. I don't know it this is supported by the current boot process. The underlying principle is to have a big raw disk partition, to encrypt it using one password, and once this partition is mapped to a decrypted device to use this device as the container for a volume group which can be splitted into several logical volumes representing the partitions you want to use at application level (/, /home, /var ...).

---

### Post by brandt on 2007-02-24
Hi,
I'm trying to setup an encrypted feisty install using luks.  I think I have everything just about configured correctly, but when I try to boot up and the system tries to activate my cryptroot, I get the error message (to the effect of):

```

cryptsetup: source device /dev/sda3 not found.

```

the modules in my etc/initramfs-tools/modules are

```

scsi_mod
ata_piix
libata
sd_mod

dm-crypt
sha256
aes_i586

```

also, when I take the 'quiet' flag out of the grub boot options, I can see that the system is activating the sata drive and recognizing the partitions.  Does anyone have any suggestions as to how I could fix this problem?  Thanks.
-Brandt

---

### Post by Skrot on 2007-02-24
Hi. I'm actually trying to use this howto (version 4) on KUbuntu Feisty. The reason why I'm using Feisty is that the Edgy kernel does not support my P-ATA chipset, so I can't install it using any of my optical drives. Anyway; when I boot the Cryptotest, it doesn't ask for he LUKS password. After detecting USB-stuff, I get this error:

```
Done.
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/1f68a0eb-0d85-4524-b825-cac063f2a7bd does not exist. Dropping to a shell!

```

I'm dropped to the initramfs shell.

The two scripts are the same as for Edgy, but I'm modprobing for some extra modules that are used by my S-ATA controller:

> 
modprobe -Qb ata_piix
modprobe -Qb libata
modprobe -Qb dg
modprobe -Qb sd_mod
modprobe -Qb scsi_mod


In /boot/grub/menu.lst I've got root=UUID=1f68a0eb-0d85-4524-b825-cac063f2a7bd on the Crypttest entry.
In /mnt/target/etc/fstab I've got UUID=1f68a0eb-0d85-4524-b825-cac063f2a7bd / ext3 defaults,errors=remount-ro 0 1 on the root (/) entry.

The UUID is the one I get from:
sudo vol_id -u /dev/mapper/cryptoroot

When I boot the regular entry from grub, I get a question about LUKS-passphrace, but it mounts the unencrypted root partition (the one which will later be used for swap) as root. Something clearly gets messed up along the way here.  :(

---

### Post by Skrot on 2007-02-24
Okay, about my last post. If I press return/enter after the USB-stuff and before I get dropped to a shell (seems like it takes about 2mins before it drops), I get this: 

```

Command failed.
/dev/mapper/cryptoroot: error open volume
Done.
Begin: Waiting for root file system... ...

```

I've also tried entering my key instead of just enter, but it didn't seem to work either.

---

### Post by RichJacot on 2007-02-24
I used the following link to encrypt my filesystems(I didn't follow it to encrypt my /home though):
[https://help.ubuntu.com/community/EncryptedFilesystemHowto5]("https://help.ubuntu.com/community/EncryptedFilesystemHowto5")

My question is now there are kernel updates that should be applied.  Can this be done just as before without encrypted filesystems or do I need to apply them and make modification?  For example modify /dev/mapper/ or update-initramfs -u ALL.

TIA

---

### Post by misty soul on 2007-02-24
> **RichJacot said:**
> My question is now there are kernel updates that should be applied.  Can this be done just as before without encrypted filesystems or do I need to apply them and make modification?

If you update a standard kernel using tools like apt-get or synaptic, they take care to rebuild the initramfs for you.

I had problems with Edgy because update-initramfs did call /usr/sbin/mkinitramfs instead of /usr/sbin/mkinitramfs-kpkg so some options were not handled. I renamed  /usr/sbin/mkinitramfs into /usr/sbin/mkinitramfs.orig, copied /usr/sbin/mkinitramfs-kpkg into /usr/sbin/mkinitramfs and changed one line in this script to have it call /usr/sbin/mkinitramfs.orig after having handled these options. Now everytime update-initramfs is called, either by me or as a side effect of updating my kernel, everything is fine.

---

### Post by RichJacot on 2007-02-24
I have dapper, should I still do what you have listed?

---

### Post by misty soul on 2007-02-24
You can just try to update your kernel without any modification first. If you don't get any error message, it's OK. You can check the date of the image file in the /boot directory to see if it has been updated.

What I explained is only a way to solve one type of problem I encountered myself when updating. I got error messages saying that the initramfs image could not be updated. I had no problems booting after that, but I knew I was still using the old kernel.

---

### Post by cookfromfrozen on 2007-02-25
I am using dm_crypt/cryptsetup for an encrypted home dir that mounts when I log in. It works fine under 2.6.17-10 (the kernel Ubuntu ships with), but only partially works with vanilla 2.6.19 which I compiled (though I have also tried 2.6.18 and a few others).

The dm_crypt module is loaded and I can log in from a console and the encrypted image mounts (so I know dm_crypt is working under the new kernel), but I cannot log in graphically.

It appears to log in, then the screen goes black and takes me back to the login screen.  If I check logs, the encrypted volume definitely mounts, but gdm crashes and goes back to the login screen.

Note that cryptsetup is definitely working because if I login at a virtual console, it mounts the volume and everything works.  Only graphic login doesn't.

Has anyone else experienced this or how can I go about diagnosing the problem?

---

### Post by IamAcoconut on 2007-02-28
Can I change size of encrypted partition just as if it was an ordinary one, or does it require more complex operations?

---

### Post by misty soul on 2007-02-28
You need at least to enlarge the raw partition used by the encryption layer first.
I think (but cannot guarantee) that once this is done is can enlarge the encrypted file system as usual. You should test it first on some small throw away file system, for example using a file mounted using a loopback (dd if=/dev/null of=/tmp/rawfile bs=1024 count=10240 ; losetup /dev/loop0 /tmp/rawfile ; and use /dev/loop0 as a 10 megabytes disk from which you would first use only 5 megabytes and later extend it to use 10 megabytes). You probably need several layers of loopback mounts to achieve this.

---

### Post by rwsjbmug on 2007-04-12
> **brandt said:**
> Hi,
I'm trying to setup an encrypted feisty install using luks.  I think I have everything just about configured correctly, but when I try to boot up and the system tries to activate my cryptroot, I get the error message (to the effect of):

```

cryptsetup: source device /dev/sda3 not found.

```


I had the same problem, and I fixed it the following way (in fact, I'm just typing this from my shiny new ThinkPad with root, home and swap on an encrypted LVM partition  :D ):

I copied /usr/share/initramfs-tools/scripts/init-premount/udev to /etc/initramfs-tools/scripts/init-premount and appended the following line at the end:

```
/sbin/udevsettle
```

Then, after a "update-initramfs -u" and a reboot, it worked. Maybe you want to try that, too.

How I came up with this: After making sure that all relevant modules are in /etc/initramfs-tools/modules, it still didn't work, although I saw (when removing "quiet" from the kernel command line) that the partitions are recognized by the kernel. So I figured that maybe the problem was that actually just the device nodes are missing, because udev hasn't created them yet. The above command makes the boot process wait until udev has processed all the initial events and created the corresponding device nodes, so that they are present when the cryptroot script is started.

**Edit:** I don't think this is needed anymore for Feisty. When I recently reinstalled Feisty from scratch, it worked without that hack. The call to udevsettle now seems to be included in the official cryptroot script.

---

### Post by brandt on 2007-04-22
> **rwsjbmug said:**
> I had the same problem, and I fixed it the following way (in fact, I'm just typing this from my shiny new ThinkPad with root, home and swap on an encrypted LVM partition  :D ):


Can you post a copy of your crypttab?  I'm trying to do lvm over the encrypted partition but when the system boots up and I type in my passphare I get something to the effect of "unknown filesystem".

---

### Post by rwsjbmug on 2007-04-22
> **brandt said:**
> Can you post a copy of your crypttab?  I'm trying to do lvm over the encrypted partition but when the system boots up and I type in my passphare I get something to the effect of "unknown filesystem".

Sure, here's my crypttab:

```
pvcrypt /dev/sda6 none luks
```

Although I think that in my case, that file isn't really needed. I just created it to get rid of some warning messages about invalid crypttab at startup, but it worked even before I created that file.

On my system, the LVM volumes are mounted when the cryptroot script is run, so I think the entries in /etc/initramfs-tools/conf.d/cryptroot might be more relevant (notice the "lvm=..." entries):

```
target=pvcrypt,source=/dev/sda6,key=none,lvm=vgcrypt-lvroot
target=pvcrypt,source=/dev/sda6,key=none,lvm=vgcrypt-lvswap
```

But actually, I don't think even that file is really needed for encrypted LVM to work on my system (I get a warning "cryptroot: failed to setup lvm device" every boot, anyway, so maybe this isn't even configured correctly). I noticed that, when the whole thing didn't work yet and I was put on a rescue shell at boot, my LVM device nodes in /dev/mapper appeared automagically as soon as I opened the encrypted partition with cryptsetup. I think the LVM volumes are set up by udev and the LVM code in the kernel as soon as the encrypted partition containing them is opened (by the way, I've set the partition type of the encrypted partition containing the LVM volumes to 0x8e ("Linux LVM"), maybe that helps, too). Have you tried mounting your volumes manually, e.g. from a rescue shell or from another crypt- and lvm-enabled Linux on a live-CD? Maybe that could give you some clues.

PS: After I recently reinstalled Feisty from scratch, my encryption setup worked without my udevsettle-hack from above, I think the cryptroot script now automatically waits for udev to settle, if necessary.

---

### Post by paninero on 2007-07-30
First, thank you for the tip.  Second, yes it is needed in Feisty, it solved my boot problem, and I was able to login.

[QUOTE=rwsjbmug;2444119]I had the same problem, and I fixed it the following way (in fact, I'm just typing this from my shiny new ThinkPad with root, home and swap on an encrypted LVM partiti

---

### Post by squarebug on 2007-08-26
Hello,

I have read through the many EncryptedFilesystemHowtoXYZ and the various  Encrypted root and swap with LUKS  in  Tutorials & Tips, but to no avail.

I am fighting with a luks encrypted root filesystem that should read its key from an usb stick. Briefly, my setup is as follows:
[INDENT]/dev/md0  unencrypted software RAID1 boot partition, ext2
/dev/md1  encrypted software RAID1 boot partition
/dev/sdc1  usb stick containing key file, vfat[/INDENT]

For testing purposes, I assigned a second key to my encrypted partition, so that I at least have a chance to boot if reading the key from the usb stick fails.

Everything works so far, with the exception of reading the key from the  usb stick. I.e. during boot, the system falls back to the luks password prompt and when I enter my password manually, it boots just fine.

My observations:
[LIST=1]
[*]/etc/crypttab seems to be ignored for the **root** partition. Instead, the entries of the initramfs, as specified in /etc/initramfs-tools/conf.d/cryptroot seem to be used.
[*]Browsing through the /etc/initramfs-tools/scripts/local-top/cryptroot script indicates that kernel line options in /boot/grub/menu.lst should be taken into account. But the following line, which works in a similar system set up with Arch Linux, fails:
[/LIST]
```
kernel  /vmlinuz-<version> root=/dev/md1 ro cryptfile=/dev/sdc1:vfat:<key file name>
```

Surely there must be a way to get this working without hacking the initramfs-tools scripts?

Any help is greatly appreciated.

---

### Post by snaildarter on 2007-09-06
Hello. I have installed fully encrypted (except /boot) Feisty to my laptop successfully. I used the instructions at

[https://help.ubuntu.com/community/FeistyEncryptedRootWithInstaller]("https://help.ubuntu.com/community/FeistyEncryptedRootWithInstaller")

Unfortunately, when booting, it always asks for me to "Enter Luks Passphrase" twice. At first I thought this was because I had both the swap partition and the / partition encrypted, so I reinstalled using only / and a swap file (no swap partition). No change.

Can anyone tell me if it is possible to install a fully encrypted Feisty (except /boot) and only have to enter a passphrase once? If so, how? I've searched the Ubuntu forums and Googled it and can't find an answer. If someone helps me with this, I will gladly contribute back to the community with a hopefully clear guide to installing an encrypted Ubuntu OS for Newbies.

Much thanks

---

### Post by martini2 on 2007-09-15
how do i use mount --bind in fstab?

i have only one crypted partition '/dev/hda3' that stores the following directories

home
usr
var

and want to mount the directories on boottime at the right places in /
when testing mount --bind /xxx/var /yyy/var on the comandline everything works but mount -a with 
/xxx/var /yyy/var in fstab gives me '/xxx/var is not a block device'
So how should fstab look like to make it work?

---

### Post by misty soul on 2007-09-15
I don't understand, you have ONE partition that holds SEVERAL directories ?
Mount is designed to attach one directory only at some place in a directories hierarchy.

---

### Post by snaildarter on 2007-09-15
Thought I would give this one more try, as I don't know where else to turn with this question.  It must be a very hard question.

> **snaildarter said:**
> Hello. I have installed fully encrypted (except /boot) Feisty to my laptop successfully. I used the instructions at

[https://help.ubuntu.com/community/FeistyEncryptedRootWithInstaller]("https://help.ubuntu.com/community/FeistyEncryptedRootWithInstaller")

Unfortunately, when booting, it always asks for me to "Enter Luks Passphrase" twice. At first I thought this was because I had both the swap partition and the / partition encrypted, so I reinstalled using only / and a swap file (no swap partition). No change.

Can anyone tell me if it is possible to install a fully encrypted Feisty (except /boot) and only have to enter a passphrase once? If so, how? I've searched the Ubuntu forums and Googled it and can't find an answer. If someone helps me with this, I will gladly contribute back to the community with a hopefully clear guide to installing an encrypted Ubuntu OS for Newbies.

Much thanks

---

### Post by quark_77 on 2007-09-16
Hi Snaildarter,

I have done exactly that. You'll have to do it in two stages, however. First set up your encrypted partition as per normal, then encrypt the swap as a second stage.

I followed this guide which is frankly very useful: [http://ubuntuforums.org/showthread.php?t=420182](http://ubuntuforums.org/showthread.php?t=420182). 

Just to check, is this how you've set things up?

Next question then: you have 8 LUKS key slots. One of these will be your swap passphrase. Have you added a key file to this and specified this key file as part of /etc/crypttab?

When your system boots it'll run the command /etc/init.d/cryptsetup start which runs through everything in crypttab and mounts it. If you haven't specified a key in crypttab it'll ask you for one i.e. give you a second prompt "Enter LUKS passphrase".

Obviously this raises the question "where do I store the key?" I've put mine in /etc/luks-keys/*.key and set the permissions so only root has access. This way they are stored on your encrypted root and sufficiently secure so that other users can't get access unless they have sudo permissions.

Hope this helps, if not post back I'll see what I can do. I'd be interested in the guide if you wrote it, I meant to do one myself but I've been very busy recently with A-level results (UK).

Quark_77

---

### Post by snaildarter on 2007-09-16
Hello quark_77,

Thank you much for the reply!  I've been hoping for some help for a while.

> **quark_77 said:**
> Just to check, is this how you've set things up?

No.  I have it set up with only 2 partitions - /boot and /.  I read that since the 2.6 kernels, a swap file is just as fast as a swap partition, so long as you keep the swap file relatively unfragmented, which isn't hard since you usually create it at the beginning of an install while the / partition is still mostly empty.  Using a swap file seems to be so much more flexible to me.

I'll try out the rest of your advice when I get time in the next few days.  I'll post back here with my reslults.  I'll say that the link to the guide you posted seems a bit over my head, and I see that it is for encrypting in place (rather than installing), but I'll try to make sense of it.

If I can get this working, I'll be happy to write the Newbie's Guide for this.  It seems to me that so many more laptops should be encrypted than are, partly because of the difficulty of doing so.

---

### Post by martini2 on 2007-09-17
i managed to install an encrypted ubuntu-7.04-server after reading many howtos. So i had this multiple-phrase-entrance problem too. It occured because i used the scripts from this howto and an entry in cryptab. As i learned from another howto this scripts are not necessary, at last not for 7.04, as they are allready installed with cryptsetup. Too bad i had to pay for this with 4 wasted hours.
But then i used this howto ([http://news.softpedia.com/news/Encrypted-Ubuntu-7-04-61312.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-7-04-61312.shtml)) it worked in half an hour. It even survieved 'apt-get dist-upgrade'!  =D> Unfortunately it uses a livecd and a spare partition but i guess you can make it work without a later swap partition if you have some space on your home network to backup your instalation.
I'm still curious if there is a solution to my question above

---

### Post by snaildarter on 2007-09-17
Hi martini2,

The link you provided looks like a good one.  It looks essentially similar to the howto I ended up using (see post 113) except, of course, mine only works for a fresh install.

Regarding your above question, I am not knowledgeable enough to understand what's going on there.  Sorry!

quark77,

> When your system boots it'll run the command /etc/init.d/cryptsetup start which runs through everything in crypttab and mounts it. If you haven't specified a key in crypttab it'll ask you for one i.e. give you a second prompt "Enter LUKS passphrase".

That makes sense to me.  So I tried all kinds of things here, taken mainly from the 3 howtos quark77, martini2, and I have mentioned.  Still no luck.  I'm about to give up on this, as it is only my obsessive nature that has made me spend the 20 hours or so I have already lost.  I'll just live with unlocking slot 0 twice, I guess.

Thank you both for your help.

---

### Post by martini2 on 2007-09-17
maybe you could remove the quiet option from /boot/grub/menu.lst in grub and check what gets started during boot.
I ended with one phrase question after deleting the scripts in /etc/initramfs-tools/hooks and /etc/initramfs-tools/scripts/l??-top. Anyway, to get it working i had to start from scratch with the howto mentioned above. I only installed the minimum system so it booted fast and there was not much to copy around.
Maybe this will be faster than trying to bugfix the current installation for you too?

---

### Post by snaildarter on 2007-09-17
> **martini2 said:**
> maybe you could remove the quiet option from /boot/grub/menu.lst in grub and check what gets started during boot.

Tried that again.  Didn't tell me anything.

> **martini2 said:**
> I ended with one phrase question after deleting the scripts in /etc/initramfs-tools/hooks and /etc/initramfs-tools/scripts/l??-top. 

Good idea.  Didn't work, though.

> **martini2 said:**
> Anyway, to get it working i had to start from scratch with the howto mentioned above. I only installed the minimum system so it booted fast and there was not much to copy around.
Maybe this will be faster than trying to bugfix the current installation for you too?

You are probably right.  But I've decided not to let this consume me any more.  I have already reinstalled 4 times.  Again, thank you for your help.

---

### Post by say2sky on 2008-02-17
Now I can use luks to encrypt my root/home/swap partition of my internal hard drive. I can also use luks to encrypt my home partition of my USB external hard drive. But when I try to encrypt root partition of my USB external hard drive using the same process, my pc cannot boot, I feel it is related to some drivers.

Now my initrd.img already include following drivers 
dm_mod 
dm_crypt
sha256
aes_i586
ehci-hcd
usb-storage
scsi_mod
sd_mod 
Anyone would help me with this completed root encryption for my external hard driver. Thanks!

---

### Post by say2sky on 2008-02-17
Because I often need to bring my USB external hard drive and USB flash drive which have system on with me, so the encrypted root and home all are important security procedure. I had tried to encrypt root as the same way as that for internal hard drive, internal hard drive work excellent but external USB stop during boot. 

I hope to know if it is possible to encrypt root for USB external hard drive or USB flash drive and how. 

Anyone have experience with this, please give me some idea. Your suggestions are appreciated.

---

### Post by uptimebox on 2008-02-18
> **say2sky said:**
> Because I often need to bring my USB external hard drive and USB flash drive which have system on with me, so the encrypted root and home all are important security procedure. I had tried to encrypt root as the same way as that for internal hard drive, internal hard drive work excellent but external USB stop during boot. 

I hope to know if it is possible to encrypt root for USB external hard drive or USB flash drive and how. 

Anyone have experience with this, please give me some idea. Your suggestions are appreciated.

I doubt that root partition encryption and LUKS is what you realy need. You'd better have a look at this project: [http://www.truecrypt.org/](http://www.truecrypt.org/)

---

### Post by say2sky on 2008-02-18
> **uptimebox said:**
> I doubt that root partition encryption and LUKS is what you realy need. You'd better have a look at this project: [http://www.truecrypt.org/](http://www.truecrypt.org/)

Did you mean it is not possible to have a LUKS encryption root partition for system on USB flash drive which can be used to boot any PC with USB port?:confused:

I have tried truecrypt for docs encryption on USB key and it is a very good software but after I use LUKS to encrypt all partition except the boot partition I feel LUKS for root encryption is more suitable and convenient which let me keep all my document encrypted on hard drive.

So now I hope to have same root LUKS encryption for Ubuntu on my USB flash drive.

---

### Post by snaildarter on 2008-02-18
Hi,

Got a few ideas.  What error messages are you getting?

Also, are you trying to encrypt your /boot partition as well?  Remember that that has to stay unencrypted.

I know of no reason why it shouldn't work on usb.

---

### Post by say2sky on 2008-02-18
> **snaildarter said:**
> Hi,

Got a few ideas.  What error messages are you getting?

Also, are you trying to encrypt your /boot partition as well?  Remember that that has to stay unencrypted.

I know of no reason why it shouldn't work on usb.

I use the same hard drive as internal hard drive, it boot OK with encrypted root and swap. 
Then I put this same hard drive in a external hard drive enclosure, it can not boot. 


The boot process show:

```

.........
cryptsetup: Source device /dev/sda2 not found

```

then after one or two minutes, it show complaining message like

```

Done
check root= bootarg cat /proc/cmdline
or missing modules, device: cat /proc/modules ls /dev

ALERT! /dev/mapper/sda2 does not exist. dropping to a shell!

```

/dev/sda2 is my encrypted root

So I think it is because when boot process try to map root partition from /dev/sda2 to /dev/mapper/sda2, the partition has not recognized by system.

Anyone can give any idea about how to let hard drive ready before  cryptsetup try to use it during boot process? and what file in initrd.img is used to control the order of hardware recognization and its usage.

---

### Post by IamAcoconut on 2008-02-19
> **uptimebox said:**
> I doubt that root partition encryption and LUKS is what you realy need. You'd better have a look at this project: [http://www.truecrypt.org/](http://www.truecrypt.org/)Then how does one boot from a Truecrypt-encrypted USB device? Is there any how-to on '**/**' encryption?

---

### Post by say2sky on 2008-02-19
> **IamAcoconut said:**
> Then how does one boot from a Truecrypt-encrypted USB device? Is there any how-to on '**/**' encryption?

 Truecrypt cannot be used for root encryption.

---

### Post by snaildarter on 2008-02-19
> **say2sky said:**
> I use the same hard drive as internal hard drive, it boot OK with encrypted root and swap. 
Then I put this same hard drive in a external hard drive enclosure, it can not boot. 

Well I think that's your problem right there.  That will cause all kinds of problems, not just with encryption.  You really can't do that (well, you could, if you knew all the places you would need to go fixing the /dev/sda2 to /dev/sdb2 or whatever, which is beyond me).  This isn't an encryption problem, it's a mapping problem.  

I think the easiest way is going to be to install it while it is hooked up externally (without encryption).  That way, all the auto detected mappings should work.  Once you know you can do that, then try again with the encryption.  

I haven't actually done this myself, though.

And, once you get it working, if you take it out of the external enclosure and put it back into the PC, everything will break again.  In fact, even if you leave it the USB enclosure, it may not work on other computers, since the mapping may happen differently on those systems.  I'm just guessing.

Also, I'm no expert, but this is what I believe to be true.  Hopefully someone smarter than me can correct me if I'm wrong.

---

### Post by say2sky on 2008-02-19
> **snaildarter said:**
> Well I think that's your problem right there.  That will cause all kinds of problems, not just with encryption.  You really can't do that (well, you could, if you knew all the places you would need to go fixing the /dev/sda2 to /dev/sdb2 or whatever, which is beyond me).  This isn't an encryption problem, it's a mapping problem.  

I think the easiest way is going to be to install it while it is hooked up externally (without encryption).  That way, all the auto detected mappings should work.  Once you know you can do that, then try again with the encryption.  

I haven't actually done this myself, though.

And, once you get it working, if you take it out of the external enclosure and put it back into the PC, everything will break again.  In fact, even if you leave it the USB enclosure, it may not work on other computers, since the mapping may happen differently on those systems.  I'm just guessing.

Also, I'm no expert, but this is what I believe to be true.  Hopefully someone smarter than me can correct me if I'm wrong.

Thanks for your response.

But about my question, when taking out internal hard drive and using it as external drive, if no any other internal hard drive, it is still recognized as sda for 7.10 version.  I always use it as this way and no problem if root partition is unencrypted. 

When there is one internal hard drive inside, I just change the external drive as sdb and also boot OK if no root encryption.

So it is not because the external drive be recognized as a different device name, in fact the kernal  in external hard drive boot but cryptsetup inside initrd.img mapping external USB hard drive before hard drive is ready. see my early post about boot message.  
 .

---

### Post by say2sky on 2008-02-19
I need more help about this root encryption in external hard drive, and I here post more info about what I do and what problem happen.

I have tried to put all driver in 7.10 ubuntu total 2056 into initrd.img which is a about 38MB file, but same boot info showed, so I think it exclude the problem that necessary drivers is not included in initrd.img.

I have tried to find what control the mapping of encryption source to encryption target inside initrd.img. it is scripts/local-top/cryptroot

```

#!/bin/sh

#
# Standard initramfs preamble
#
prereqs()
{
        # Make sure that cryptroot is run last in local-top
        for req in /scripts/local-top/*; do
                script=$(basename $req)
                if [ $script != cryptroot ]; then
                        echo $script
                fi
        done
}

case $1 in
prereqs)
        prereqs
        exit 0
        ;;
esac


#
# Helper functions
#
parse_options()
{
        local cryptopts
        cryptopts="$1"

        if [ -z "$cryptopts" ]; then
                return 1
        fi

        # Defaults
        cryptcipher=aes-cbc-essiv:sha256
        cryptsize=256
        crypthash=sha256
        crypttarget=cryptroot
        cryptsource=""
        cryptlvm=""
        cryptkeyscript=""
        cryptkey="" # This is only used as an argument to an eventual keyscript

        local IFS=" ,"
        for x in $cryptopts; do
                case $x in
                hash=*)
                        crypthash=${x#hash=}
                        ;;
                size=*)
                        cryptsize=${x#size=}
                        ;;
                cipher=*)
                        cryptcipher=${x#cipher=}
                        ;;
                target=*)
                        crypttarget=${x#target=}
                        ;;
                source=*)
                        cryptsource=${x#source=}
                        ;;
                lvm=*)
                        cryptlvm=${x#lvm=}
                        ;;
                keyscript=*)
                        cryptkeyscript=${x#keyscript=}
                        ;;
                key=*)
                        if [ "${x#key=}" != "none" ]; then
                                cryptkey=${x#key=}
                        fi
                        ;;
                esac
        done

        if [ -z "$cryptsource" ]; then
                echo "cryptsetup: source parameter missing"
                return 1
        fi
        return 0
}

activate_vg()
{
        local vg
        vg="${1#/dev/mapper/}"

        # Sanity checks
        if [ ! -x /sbin/vgchange ] || [ "$vg" = "$1" ]; then
                return 1
        fi

        # Make sure that the device contains at least one dash
        if [ "${vg%%-*}" = "$vg" ]; then
                return 1
        fi

        # Split volume group from logical volume.
        vg=$(echo ${vg} | sed -e 's#\(.*\)\([^-]\)-[^-].*#\1\2#')

        # Reduce padded --'s to -'s
        vg=$(echo ${vg} | sed -e 's#--#-#g')

        vgchange -ay ${vg}
        return $?
}

activate_evms()
{
        local dev module
        dev="${1#/dev/evms/}"

        # Sanity checks
        if [ ! -x /sbin/evms_activate ] || [ "$dev" = "$1" ]; then
                return 1
        fi

        # Load modules used by evms
        for module in dm-mod linear raid0 raid1 raid10 raid5 raid6; do
                modprobe -q $module
        done

        # Activate it
        /sbin/evms_activate
        return $?
}

setup_mapping()
{
        local opts count cryptcreate cryptremove NEWROOT
        opts="$1"

        if [ -z "$opts" ]; then
                return 0
        fi

        parse_options "$opts" || return 1

        # The same target can be specified multiple times
        # e.g. root and resume lvs-on-lvm-on-crypto
        if [ -e "/dev/mapper/$crypttarget" ]; then
                return 0
        fi

        modprobe -q dm_crypt
        echo "Setting up cryptographic volume $crypttarget (based on $cryptsource)"

        # Make sure the cryptsource device is available
        if [ ! -e $cryptsource ]; then
                activate_vg $cryptsource
                activate_evms $cryptsource
        fi
        # Wait for udev to be ready, see https://launchpad.net/bugs/85640
        if [ -x /sbin/udevsettle ]; then
                /sbin/udevsettle --timeout=30
        fi

        if [ ! -e $cryptsource ]; then
                echo "cryptsetup: Source device $cryptsource not found"
                return 1
        fi

        # Prepare commands
        if /sbin/cryptsetup isLuks $cryptsource > /dev/null 2>&1; then
                cryptcreate="/sbin/cryptsetup luksOpen $cryptsource $crypttarget"
        else
                cryptcreate="/sbin/cryptsetup -c $cryptcipher -s $cryptsize -h $crypthash create $crypttarget $cryptsource"
        fi
        cryptremove="/sbin/cryptsetup remove $crypttarget"
        NEWROOT="/dev/mapper/$crypttarget"

        # Try to get a satisfactory password three times
        count=0
        while [ $count -lt 3 ]; do
                count=$(( $count + 1 ))

                if [ -n "$cryptkeyscript" ]; then
                        if [ ! -x "$cryptkeyscript" ]; then
                                echo "cryptsetup: error - $cryptkeyscript missing"
                                return 1
                        fi
                        crypttarget="$crypttarget" cryptsource="$cryptsource" \
                        $cryptkeyscript $cryptkey < /dev/console 2> /dev/console | \
                        $cryptcreate --key-file=- > /dev/console 2>&1
                elif [ -p /dev/.initramfs/usplash_outfifo ] && [ -x /sbin/usplash_write ]; then
                        usplash_write "INPUTQUIET Enter password for $crypttarget: "
                        PASS="$(cat /dev/.initramfs/usplash_outfifo)"
                        echo -n "$PASS" | $cryptcreate > /dev/null 2>&1
                else
                        $cryptcreate < /dev/console > /dev/console 2>&1
                fi

                if [ $? -ne 0 ]; then
                        echo "cryptsetup: cryptsetup failed, bad password or options?"
                        sleep 3
                        continue
                elif [ ! -e "$NEWROOT" ]; then
                        echo "cryptsetup: unknown error setting up device mapping"
                        return 1
                elif [ -p /dev/.initramfs/usplash_outfifo ] && [ -x /sbin/usplash_write ]; then
                        # clean the text, to give feedback that it worked
                        usplash_write "TEXT-URGENT "
                fi

                FSTYPE=''
                eval $(fstype < "$NEWROOT")

                # See if we need to setup lvm on the crypto device
                if [ "$FSTYPE" = "lvm" ] || [ "$FSTYPE" = "lvm2" ]; then
                        if [ -z "$cryptlvm" ]; then
                                echo "cryptsetup: lvm fs found but no lvm configured"
                                return 1
                        elif ! activate_vg "/dev/mapper/$cryptlvm"; then
                                echo "cryptsetup: failed to setup lvm device"
                                return 1
                        fi

                        NEWROOT="/dev/mapper/$cryptlvm"
                        eval $(fstype < "$NEWROOT")
                fi

                if [ -z "$FSTYPE" ] || [ "$FSTYPE" = "unknown" ]; then
                        echo "cryptsetup: unknown fstype, bad password or options?"
                        $cryptremove
                        sleep 3
                        continue
                fi

                break
        done

        if [ $count -lt 3 ]; then
                # Wait for udev to be ready, see https://launchpad.net/bugs/85640
                if [ -x /sbin/udevsettle ]; then
                        /sbin/udevsettle --timeout=30
                fi
                return 0
        else
                echo "cryptsetup: maximum number of tries exceeded"
                return 1
        fi
}

#
# Begin real processing
#

# Do we have any kernel boot arguments?
found=''
for opt in $(cat /proc/cmdline); do
        case $opt in
        cryptopts=*)
                found=yes
                setup_mapping "${opt#cryptopts=}"
                ;;
        esac
done

if [ -n "$found" ]; then
        exit 0
fi

# Do we have any settings from the /conf/conf.d/cryptroot file?
if [ -r /conf/conf.d/cryptroot ]; then
        while read mapping; do
                setup_mapping "$mapping"
        done < /conf/conf.d/cryptroot
fi

exit 0

```

---

### Post by snaildarter on 2008-02-19
> see my early post about boot message.

Oh I see, I misunderstood.  I should have read your post more carefully!

This problem is over my head.  I'm sorry I can't be of more help.

---

### Post by say2sky on 2008-02-20
Thanks for everybody! Now it works with root encryption on external USB hdd.

---

