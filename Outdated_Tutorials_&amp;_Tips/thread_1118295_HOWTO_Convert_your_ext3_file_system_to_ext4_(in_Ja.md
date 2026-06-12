---
title: "HOWTO: Convert your ext3 file system to ext4 (in Jaunty)"
date: 2009-04-06
forum: Outdated Tutorials &amp; Tips
---

### Post by whoop on 2009-04-06
With the release of Jaunty allot of people will be doing an upgrade from Intrepid (if they did not do it already) to Jaunty. If you are one of those people and you don't want to miss out using the new ext4 file system, there is a way to convert your existing ext2 and/or ext3 file system to ext4.

Please note that converting-to/using ext4 is by no means necessary, you are not missing out if you are using ext3 (hell, ext2 is still widely in use). So only do this if you like to hack and get your hands dirty. I did however convert my production machine from ext3 to ext4 just because I wanted to :guitar:


[COLOR="Red"]Step one:[/COLOR]
Upgrade to Jaunty. You now have a working Jaunty install running the ext3 file system.
Make sure you are running kernel 2.6.28-11-generic or higher. 
To check which kernel you are running:
```

uname -a

```

[COLOR="Red"]Step two:[/COLOR]
Make a backup of all your (important) data.

[COLOR="Red"]Step three:[/COLOR]
*EDIT: Some extra info on how to convert from ext2 to ext4 (thanks, groggyboy)*

Boot from a (Jaunty) live-cd and run the following code (in this example the partition to convert is on /dev/sda1) to convert the partition:
To convert from ext3 to ext4:
```

sudo bash
tune2fs -O extents,uninit_bg,dir_index /dev/sda1
e2fsck -pf /dev/sda1

```
To convert from ext2 to ext4:
```

sudo bash
tune2fs -O extents,uninit_bg,dir_index,has_journal /dev/sda1
e2fsck -pf /dev/sda1

```

[COLOR="Red"]Step four:[/COLOR]
Mount the partition and change the type of the converted partition in fstab:
```

sudo bash
mount -t ext4 /dev/sda1 /mnt
nano /mnt/etc/fstab

```

change "ext3" to "ext4" like in the example below:
```

# /dev/sda1
UUID=XXXXXXXXXXXXXXXXXXXXXXXXXX /               ext3    relatime,errors=remount-ro 0       1

```
change it to:
```

# /dev/sda1
UUID=XXXXXXXXXXXXXXXXXXXXXXXXXX /               ext4    relatime,errors=remount-ro 0       1

```
and save the changes.

[COLOR="Red"]Step five:[/COLOR]
*EDIT: Some extra info on how to refresh grub when you have a separate /boot partition (thanks, utkjamie)*

This step might be optional but when I upgraded from Intrepid to Jaunty the upgrade process did not install/update the new grub stage. So if you don't run either of the following code examples you might get an (fatal) error 13 when booting the machine.
Use this code to refresh grub when you do **not** have a separate /boot partition (in this example the root partition is sda1)
```

sudo bash
mount /dev/sda1 /mnt
grub-install /dev/sda --root-directory=/mnt --recheck

```
Use this code to refresh grub when you **do** have a separate /boot partition (in this example the /boot partition is sda1)
```

sudo bash
mkdir /mnt/boot
mount /dev/sda1 /mnt/boot
grub-install /dev/sda --root-directory=/mnt --recheck

``` 

That's it, after you reboot you you will be running from an ext4 file system. 
As a side note, all the files that where present before the conversion will not benefit from the conversion as they were written to disk using ext3 technology. Only newly created or overwritten files will be using the true ext4 technology (so now, using update-manager will be extra beneficial :lolflag:). As ext3 and ext4 are compatible with each other having files written to disk in ext3 mode on your ext4 file system do not impose any risks (and most if not all ext3 sectors could eventually disappear even without defragging).

There is currently a online-defragging tool in development (e4defrag) which should be available with the next kernel release.

---

### Post by groggyboy on 2009-04-18
Thanks for the howto! Worked like a charm for me.

However, I upgraded from ext**2** to ext4.  I made one modification to step three in order to make the upgrade, and I thought I'd share it:

Step three (when upgrading from ext2 to ext4):
```
sudo bash
tune2fs -O extents,uninit_bg,dir_index,has_journal /dev/sda1
e2fsck -pf /dev/sda1
```

The extra flag, "has_journal", is nescessary because ext2 is not a journalling filesystem, unlike the later ext filesystems.

---

### Post by jarede on 2009-04-19
works perfectly thanks for the info

---

### Post by meeples on 2009-04-22
THANKS ;D

i'll use this tomorow when 9.04 is released on my netbook because it dowsnt have a cd drive and i dont have a flash drive around i cant do a clean install.

i love you ;)

---

### Post by Onesimus on 2009-04-23
Is there away of doing this that doesn't rely on booting from the live CD ?  

(I have to install Ubuntu using the alternative CD because my computer spec doesn't meet the requirements to boot from live CD.)

---

### Post by Kralizec on 2009-04-23
Thank you very much for this! I was worried I'd have to backup my data and scrap my install to get ext4.

---

### Post by Polizei on 2009-04-24
So, when newly written and rewritten files became ext4 beneficial, this should mean if I `touch' all my downloads/ (for example), they will benefit the ext4 fs too?

PS: Nice post, and thanks.. Just replaced Intrepid with Jaunty and I saw ext4 support. Awesome!

---

### Post by lastrite on 2009-04-24
Thank you, worked perfectly! 

Boot times now blow Windows 7 RC out of the water!

---

### Post by whoop on 2009-04-24
> **Onesimus said:**
> Is there away of doing this that doesn't rely on booting from the live CD ?  

(I have to install Ubuntu using the alternative CD because my computer spec doesn't meet the requirements to boot from live CD.)

Well I have only tried it with a jaunty live-cd and a jaunty live-usb but technically you could use any lightweight boot that has the same version of the tools that are used in this how to, you don't need a window manager to do this.
Maybe you could even do it from a second temporary jaunty install (although that might be a hassle)

---

### Post by whoop on 2009-04-24
> **Polizei said:**
> So, when newly written and rewritten files became ext4 beneficial, this should mean if I `touch' all my downloads/ (for example), they will benefit the ext4 fs too?

PS: Nice post, and thanks.. Just replaced Intrepid with Jaunty and I saw ext4 support. Awesome!

Well if I am not mistaken touch only changes the files time-stamp and doesn't rewrite the file completely. So if that is the case the only thing should be defragging (which is not available yet) or moving the files (and optionally moving them back to create an identical directory tree).

---

### Post by Istvan D on 2009-05-01
works like charm, step five wasn't even needed (ok, I use Jaunty since a week). thanks a lot ):P
(I only had to figure out what the "^" symbol in nano means: "Ctrl"-button. I know, I am a n00b)

---

### Post by davideotape on 2009-05-02
Thanks a lot for that guide, worked a treat :D

Although I haven't written any new files yet, I'm on karmic so I should see and increase in performance and new updates are released.

---

### Post by dwasifar on 2009-05-03
Worked for me, except the last step to refresh grub.  That step hit an error, saying unable to read device map, and left me with a system that hung on boot.  But not to worry, a manual grub reinstall from live CD fixed it and all is now hunky dory.

---

### Post by utkjamie on 2009-05-04
> **dwasifar said:**
> Worked for me, except the last step to refresh grub.  That step hit an error, saying unable to read device map, and left me with a system that hung on boot.  But not to worry, a manual grub reinstall from live CD fixed it and all is now hunky dory.

Exact same problem. I followed the directions exactly but got an error on the last step telling me that it couldn't read the device map. Now when I reboot I am dropped to a grub prompt. I've wasted hours on this problem and have not been able to find a useful solution.

What do I do now?

---

### Post by utkjamie on 2009-05-04
Part of my problem is that these instructions assume that /boot is *not* on its own partition (this should have been specified). Grub is located on a separate boot partition on my computer located at /dev/sda2 so following these directions was causing grub-install to write to /boot/boot/grub. To resolve this I used:

```
mkdir /mnt/boot
mount -t ext4 /dev/sda2 /mnt/boot
grub-install /dev/sda --root-directory=/mnt --recheck
```I had to tweak the resulting device.map file to match my actual hardware (Grub adds an extra entry to the top of the file).

Now I'm getting this problem:

> mounting /dev/disk/by-uuid/... on /root failed: No such device
mounting /dev on /root/dev failed: No such file or directory
mounting /sys on /root/sys failed: No such file or directory
mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.

I'm then dropped to a BusyBox/initramfs prompt with no idea what to do next. I cannot boot into recovery mode for the same reason.

I can mount my Ext4 partitions from the live CD, so I know they are okay.

Does anyone know what's going on here? I cannot imagine that upgrading from Ext3 to Ext4 is supposed to be this difficult.

---

### Post by utkjamie on 2009-05-04
Problem solved. Finally. When I look a closer look at menu.lst, I saw that Grub was loading the 2.6.27-11-generic kernel instead of 2.6.28-11. I have no idea why my menu.lst file wasn't reflecting 9.04 boot options.

Here's what I did from start to finish. Keep in mind that I have a dual-boot system and my /boot is on its own partition at /dev/sda2.

First, I followed the instructions at the beginning of this thread up to step 5. From there...

```

sudo -i #easier to work without having to type 'sudo' for each command
mkdir /mnt/boot #since my /boot is on its own partition, otherwise grub-install will write to /boot/boot/grub instead of /boot grub
mount -t ext4 /dev/sda2 /mnt/boot
grub-install /dev/sda --root-directory=/mnt --recheck

```I added *rootfstype=ext4* to each of the kernal commands in menu.lst, though I believe this is no longer necessary.

The following may not have been necessary either, but it was something I did in trying to get this all to work:

```

# for reasons unknown, chroot won't work off the live CD for me, telling me that /bin/bash doesn't exist even though it does.
# as a workaround, I created symbolic links to my grub directory in the live CD's Grub directory
mkdir /boot/grub
ln -s /mnt/boot/grub/device.map /boot/grub/device.map
ln -s /mnt/boot/grub/menu.lst /boot/grub/menu.lst
update-grub

```

---

### Post by whoop on 2009-05-04
> **utkjamie said:**
> Problem solved. Finally. When I look a closer look at menu.lst, I saw that Grub was loading the 2.6.27-11-generic kernel instead of 2.6.28-11. I have no idea why my menu.lst file wasn't reflecting 9.04 boot options.

Here's what I did from start to finish. Keep in mind that I have a dual-boot system and my /boot is on its own partition at /dev/sda2.

First, I followed the instructions at the beginning of this thread up to step 5. From there...

```

sudo -i #easier to work without having to type 'sudo' for each command
mkdir /mnt/boot #since my /boot is on its own partition, otherwise grub-install will write to /boot/boot/grub instead of /boot grub
mount -t ext4 /dev/sda2 /mnt/boot
grub-install /dev/sda --root-directory=/mnt --recheck

```I added *rootfstype=ext4* to each of the kernal commands in menu.lst, though I believe this is no longer necessary.

The following may not have been necessary either, but it was something I did in trying to get this all to work:

```

# for reasons unknown, chroot won't work off the live CD for me, telling me that /bin/bash doesn't exist even though it does.
# as a workaround, I created symbolic links to my grub directory in the live CD's Grub directory
mkdir /boot/grub
ln -s /mnt/boot/grub/device.map /boot/grub/device.map
ln -s /mnt/boot/grub/menu.lst /boot/grub/menu.lst
update-grub

```

Sorry, utkjamie, I couldn't reply sooner because I had to replicate your setup before I could try to solve it. I checked your solution and it worked for me, so I added it to the howto. Thanks.

---

### Post by iheartubuntu on 2009-05-07
Just for the sake of mentioning, Ive got a 250gb main hard drive and it took probably 5 minutes for step 3 to finish processing.

---

### Post by iheartubuntu on 2009-05-07
Unfortunately this didnt work for me. I followed all instructions up until finishing step 4. Rebooted and it didnt work. Then, I proceeded to step 5, but accidentally did the second part of step 5 first, then did the first part of step 5. I am now getting an error...

"assuming drive cache write through"

upon booting. I then reinstalled grub from my live disc just to get the grub menu to boot up. I do get a grub menu now, but still get this error...

> [9.328187] sd 4:0:0:0: [sdc] Assuming drive cache write through

Anyone have any recommendations to fix this?

I notice my drive is still there with all the data on it. So nothing has been erased. My hard drive is (hd0,0)

---

### Post by whoop on 2009-05-07
> **shirteesdotnet said:**
> Unfortunately this didnt work for me. I followed all instructions up until finishing step 4. Rebooted and it didnt work. 

What error did you get?

> **shirteesdotnet said:**
> 
Then, I proceeded to step 5, but accidentally did the second part of step 5 first, 

There is only one step in part five that you actually take, the first one is if you do not have a /boot partition and the second one is if you do have a /boot partition. Do you have a separate /boot partition?

> **shirteesdotnet said:**
> 
then did the first part of step 5. I am now getting an error...

"assuming drive cache write through"

upon booting. I then reinstalled grub from my live disc just to get the grub menu to boot up. I do get a grub menu now, but still get this error...

I not sure "assuming drive cache write through" is actually an error. I think it has something to do with the firmware of the device not reporting back if it is write-through or not.

> **shirteesdotnet said:**
> 
```

[9.328187] sd 4:0:0:0: [sdc] Assuming drive cache write through 

```
Anyone have any recommendations to fix this?

I notice my drive is still there with all the data on it. So nothing has been erased. My hard drive is (hd0,0)

Does it stop after this message? Is that the only message on screen? The message seems to be about a sdc device. Do you have any extra hard-disks or usb-devices connected to your machine? I would expect it to say [sda] or something. Maybe you can run the live-cd and check if the partition(s) are actually converted to ext4 (maybe with gparted so you can get a good view of how your hard-disk is partitioned) and what the path of the partition is (like /dev/sda1 for example). If you have extra non crucial devices connected to your machine you could try to temporarily disconnect them and see what happens when you boot.

---

### Post by iheartubuntu on 2009-05-07
First, thanks for the reply!

I'll try to answer here what I can...

> **whoop said:**
> What error did you get?

I dont recall. The system would not boot up. I think it said the "no bootable device" message. It was 3am :)

> **whoop said:**
> There is only one step in part five that you actually take, the first one is if you do not have a /boot partition and the second one is if you do have a /boot partition. Do you have a separate /boot partition?

I dont, but at 3am I unwisely choose the second option of #5. After realizing this, I did the first option.

> **whoop said:**
> I not sure "assuming drive cache write through" is actually an error. I think it has something to do with the firmware of the device not reporting back if it is write-through or not.

You are probably right after all the digging I did last night trying to solve the issue. The closest thing I found to a fix was that someone recommended I get into the menu.lst file on my system and fix it. I couldnt figure it out and using a livecd then "gksudo nautilus" still would not let me access my menu.lst on my hard drive. So I did fix the grub menu and got that far. No longer was I getting a no bootable disc error. I now get my grub menu, then that 'assuming drive cache error' and then the system hangs.

I get a few assuming drive cache errors. Each one with a little bit different number at the front of the error message.

No I do not have any extra hard disks hooked up to this. Ohhh wait! I do. Its a 1TB USB drive. Maybe I should unplug it?

I did used gparted in the livecd and it shows the SDA1 is now EXT4.

OK, this is where it gets a bit tricky.... I was having no luck last night (ehem, with the computer) and decided to delete my XP partition since I never use it. I then regrew the first partition (my main sda1 ubuntu partition) to full size again and now my computer looks like a typical fresh Ubuntu partition setup. The Ubuntu partition and then the swap space. I also marked sda1 as bootable.

In the LiveCD I can see my drive no problems and all my data. I just cant boot into it and thats where I am now with this error and then the system hangs...

> [9.328187] sd 4:0:0:0: [sdc] Assuming drive cache write through 

---

### Post by blade1950 on 2009-05-07
Note of caution. I have seen a few posts speaking of lose of data when using the new Ext4 file system. I have experienced this myself when I did my initial install of Jaunty. The install went very well with no complications however, when I booted a few days later I was greeted with numerous error messages and "can't find…" notices. I re-installed using Ext3. Needless to say I will be looking much deeper into this BEFORE I covert. In my zeal to use Ubuntu I broke one of my cardinal rules "Don't upgrade unless you need to and then wait even longer before you do". Bleeding edge technology strikes again.

---

### Post by utkjamie on 2009-05-07
> **blade1950 said:**
> Note of caution. I have seen a few posts speaking of lose of data when using the new Ext4 file system. I have experienced this myself when I did my initial install of Jaunty.

This seems to occur when files are in use during a crash. I had a 180 MB file disappear while being moved to a thumb drive when my laptop froze up. Kind of a scary thought and I can't help but wonder what would happen to my files if a freeze or crash happened while I was backing my files up. Would they be safer if not accessed by a backup program...

> **blade1950 said:**
> In my zeal to use Ubuntu I broke one of my cardinal rules "Don't upgrade unless you need to and then wait even longer before you do". Bleeding edge technology strikes again.

That's the frustrating part: this isn't bleeding edge technology. Ext4 is supposedly stable and is part of the Ubuntu distribution presumably because it is stable and reliable. I'm not sure how that is defined, though, considering that there is such a risk of data loss. Generally, crashes and feezes have been extremely rare for me with Ubuntu (Kubuntu, actually) but in the past week I have had more freezes than I've seem probably in the past year -- so something is definitely broken somewhere, but it seems to be something other than Ext4 since people using Ext3 have been experiencing these same freezes lately.

---

### Post by blade1950 on 2009-05-07
Utkjamie comments sparked my thinking, I know...DANGER! Anyway, I wonder if how much of this could be related to cross technologies in file systems. I am using HDD's with both NTFS and Ext3 now. How many of those who've experienced non-file moving data loss issues have more than one file system in use on the same PC? Data loss during file transfers is not uncommon regardless of OS. As a general rule I wait for six months to a year before I "upgrade" if I can. Let others do the "Charlie" testing for me.

---

### Post by utkjamie on 2009-05-07
> **blade1950 said:**
>  Anyway, I wonder if how much of this could be related to cross technologies in file systems. I am using HDD's with both NTFS and Ext3 now. How many of those who've experienced non-file moving data loss issues have more than one file system in use on the same PC?

I have a dual-boot system with NTFS on one partition and I don't recall ever losing data that I moved from Linux (Ext3/Ext4) to NTFS. However, when I first started using Linux about 2.5 years ago, I tried some drivers that would allow me to access Ext3 partitions from inside Windows. While I don't know for sure, I am reasonably certain that was the cause of data loss I experienced back then.

I use Windows on very rare ocassions, so there is barely a need for me to have a dual-boot system, but that's a whole other matter for another thread...

---

### Post by iheartubuntu on 2009-05-07
I never lost any data. That isnt my concern at all. My grub or something is screwed up. Tonite when I get home, I will unplug my USB drive and see what happens on a reboot. So, whatever is happening to me, could potentially happen to other people, even if they were to wait 6 extra months. It would have been nice for Jaunty to include an EXT3 to EXT4 conversion as an option when upgrading. One that isnt checkmarked for upgrade, but at least give an option to do it.

Ive not experienced any data loss on the other two computers I use that now have Jaunty installed fresh with EXT4. I notice one of them, my laptop will lock up maybe once a week if I do some really odd multi-tasking like using photoshop in Wine, then doing an update manager update, while deleting files, closing out Firefox (with 15 tabs) and also running a search in my home directory. Again, its extremely odd and rare to get a crash like that, but I never experienced it before in Intrepid (or previous releases). Then again maybe I was just trying to do waaay too many things at once.

In any event, my current situation I have not lost any data. Im not worried at all. If a fix doesnt come I could copy the 50GB to my USB using the liveCD and then reinstall Ubuntu on my drive. I'll refrain from that if possible and hope someone has some suggestions first!

---

### Post by utkjamie on 2009-05-07
It doesn't sound like this is your problem, but make sure you are booting with the 2.6.28-11 kernel. If I try to boot with 2.6.27-11, my boot will bomb out. Apparently the 2.6.27-11 kernel cannot read Ext4.

---

### Post by iheartubuntu on 2009-05-07
> **utkjamie said:**
> It doesn't sound like this is your problem, but make sure you are booting with the 2.6.28-11 kernel. If I try to boot with 2.6.27-11, my boot will bomb out. Apparently the 2.6.27-11 kernel cannot read Ext4.

Maybe it is a prob. Im running 2.6.27-10. How do I go about upgrading it at a prompt??

---

### Post by iheartubuntu on 2009-05-07
Im also unable to go into recovery mode :(

---

### Post by whoop on 2009-05-07
> **shirteesdotnet said:**
> Maybe it is a prob. Im running 2.6.27-10. How do I go about upgrading it at a prompt??

Oh man, I think we are getting somewhere now. 2.6.27 can't read ext4. Are you sure you upgraded to jaunty (I expect you did). Maybe your menu.lst wasn't updated during the upgrade. Check if /boot/grub/vmlinuz-2.6.28-11-generic exists on your current install. If it does try: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

If all else fails you can even try to add the 2.6.28 kernel to your menu.lst manually
Add something like (do not copy exactly as root and UUID will not match)
```

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,x)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=xxxxxxxxxxx ro 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,x)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=xxxxxxxxxxx ro  single
initrd		/boot/initrd.img-2.6.28-11-generic


```

It could be even possible to install the latest kernel (if you haven't got it installed) via the live-cd through some chrooting but I never tried that.

---

### Post by iheartubuntu on 2009-05-08
You know what.. I remember when I upgraded to Jaunty I chose to keep my old menu.lst. I guess thats the prob then!

But, how do I edit it? Im not so sure it will let me edit from the livecd...



> **whoop said:**
> Oh man, I think we are getting somewhere now. 2.6.27 can't read ext4. Are you sure you upgraded to jaunty (I expect you did). Maybe your menu.lst wasn't updated during the upgrade. Check if /boot/grub/vmlinuz-2.6.28-11-generic exists on your current install.

---

### Post by whoop on 2009-05-08
> **shirteesdotnet said:**
> You know what.. I remember when I upgraded to Jaunty I chose to keep my old menu.lst. I guess thats the prob then!

But, how do I edit it? Im not so sure it will let me edit from the livecd...

Boot from live-cd and edit menu.lst on hard-disk.
something like this should work (assuming root partition is sda1 and there is no separate boot partition):
```

sudo mount -t ext4 /dev/sda1 /mnt
gksudo gedit /mnt/boot/grub/menu.lst

```

BTW, did you check if the 2.6.28-11 kernel is installed on your machine?
```

sudo mount -t ext4 /dev/sda1 /mnt
ls /mnt/boot

```
and see if the 2.6.28-11 kernel pops up, it's called something like: vmlinuz-2.6.28-11-generic

---

### Post by blade1950 on 2009-05-08
It would seem the kernel rev. is at least part of the trouble when dealing with ext4 file systems. 

[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4).

[http://ext4.wiki.kernel.org/index.php/Main_Page](http://ext4.wiki.kernel.org/index.php/Main_Page)

---

### Post by deepclutch on 2009-05-12
I have upgraded from Intrepid to Jaunty 64-bit.Is there any livecd with ext4 support and 2.6.29 kernel.please let me know.I will use that distro to convert the current installation :D

Can I use Sysrsccd or Parted Magic to convert to ext4?Both of them got 2.6.29 kernel. :o
EDIT: downloaded,baked cd of partedmagic(latest).going out now.will come back and try converting to ext4 via livecd.

---

### Post by whoop on 2009-05-12
> **deepclutch said:**
> I have upgraded from Intrepid to Jaunty 64-bit.Is there any livecd with ext4 support and 2.6.29 kernel.please let me know.I will use that distro to convert the current installation :D

Can I use Sysrsccd or Parted Magic to convert to ext4?Both of them got 2.6.29 kernel. :o
EDIT: downloaded,baked cd of partedmagic(latest).going out now.will come back and try converting to ext4 via livecd.

I haven't tried it with partedmagic (only with jaunty live-cd and live-usb) but if partedmagic has the same packages (with the same or higher version number) that are used in this howto it could/should work. If your 'scared' ;) you can always try to do it on a virtual machine first.

---

### Post by deepclutch on 2009-05-12
Let me try.BTW ,I hate VM.I use GNU/Linux for Real ;)

---

### Post by deepclutch on 2009-05-12
I would like to tell that the Howto is Excellent and it converted to ext4 fine via gparted(2.6.29 kernel) live cd.But ,when it comes to grub ,it showed fails to read stage1/stage2 grub.so,I tried chrooting to ext4 Jaunty partition.it showed some execution error(mine is a 64-bit jaunty installation btw).I have a fedora10 64-bit also installed(hardly uses).so I rescued the grub of Fedora and booted into Jaunty 64-bit ext4 and it went Fine. ;) inside jaunty ,I reinstalled grub and rechecked.
```
1)a@bcd:~# grub
2)grub> root (hd0,4) <---- for my /dev/sda5 ubuntu partition
3)grub> setup (hd0) 

```Then :
```
grub-install /dev/sda --recheck
```Hope this helps someone :P
**[COLOR=Red]EDIT[/COLOR]:**
Here is the link to latest gparted live cd ,which I used to convert(88MB):
[http://nchc.dl.sourceforge.net/sourceforge/partedmagic/pmagic-4.1.iso.zip](http://nchc.dl.sourceforge.net/sourceforge/partedmagic/pmagic-4.1.iso.zip)

---

### Post by whoop on 2009-05-12
> **deepclutch said:**
> I would like to tell that the Howto is Excellent and it converted to ext4 fine via gparted(2.6.29 kernel) live cd.But ,when it comes to grub ,it showed fails to read stage1/stage2 grub.so,I tried chrooting to ext4 Jaunty partition.it showed some execution error(mine is a 64-bit jaunty installation btw).I have a fedora10 64-bit also installed(hardly uses).so I rescued the grub of Fedora and booted into Jaunty 64-bit ext4 and it went Fine. ;) inside jaunty ,I reinstalled grub and rechecked.
```
1)a@bcd:~# grub
2)grub> root (hd0,4) <---- for my /dev/sda5 ubuntu partition
3)grub> setup (hd0) 

```Then :
```
grub-install /dev/sda --recheck
```Hope this helps someone :P
**[COLOR=Red]EDIT[/COLOR]:**
Here is the link to latest gparted live cd ,which I used to convert(88MB):
[http://nchc.dl.sourceforge.net/sourceforge/partedmagic/pmagic-4.1.iso.zip](http://nchc.dl.sourceforge.net/sourceforge/partedmagic/pmagic-4.1.iso.zip)

Wouldn't the grub recheck have solved your grub problems when booting? Something like:
```

sudo bash
mount /dev/sda1 /mnt
grub-install /dev/sda --root-directory=/mnt --recheck

```
instead of what you did? Just like step 5 in the howto.

---

### Post by deepclutch on 2009-05-12
> **whoop said:**
> Wouldn't the grub recheck have solved your grub problems when booting? Something like:
```

sudo bash
mount /dev/sda1 /mnt
grub-install /dev/sda --root-directory=/mnt --recheck

```instead of what you did? Just like step 5 in the howto.
No.it complained that stage1/stage2 grub not accessible.

---

### Post by heroidi on 2009-05-12
I've messed it up :S:S i didn't do it from the live cd but I've done it as I was running ubuntu on my hard drive :S:S how can I repair it plz help

---

### Post by whoop on 2009-05-12
> **heroidi said:**
> I've messed it up :S:S i didn't do it from the live cd but I've done it as I was running ubuntu on my hard drive :S:S how can I repair it plz help

Oops, you are not supposed to do that. You need to provide more detailed information so people can help you. We know what you where trying to do but:
*What did you do exactly?
*What happened?
*What is the current situation, what seems to be wrong with your system?

---

### Post by heroidi on 2009-05-12
i've followed those steps but not in the live cd but in my root filesystem it mounted it as an ext4 system but it starts loading and displays a kind of command line in fullscreen mode i tried it with the livecd those steps but it didn't work so i messed up

---

### Post by whoop on 2009-05-12
> **heroidi said:**
> i've followed those steps but not in the live cd but in my root filesystem it mounted it as an ext4 system but it starts loading and displays a kind of command line in fullscreen mode i tried it with the livecd those steps but it didn't work so i messed up

That's not enough information to determine what your situation is. What does "it didn't work" mean?
Can you boot from a live-cd and post the output of
```

sudo parted

```
and then
```

print all

```
type quit to exit parted.

Or post a screenshot of the partition editor window
```

gksudo gparted

```
so we can see what your harddisk status is.

---

### Post by dozch on 2009-05-19
Thanks everyone - To step things up a notch, I can report that I just did a successful upgrade from ext3 to ext4 on my (software) RAID partitions. I have a RAID0 (/) as well as a couple of RAID1 partitions.

The process is the same as described in the Howto, but first you have to get the Live CD to recognise your RAID partitions. This is described in more detail elsewhere, but basically you

- back up your important stuff

- start Jaunty using your Live CD, open a terminal.

- install mdadm:

```
sudo apt-get update
sudo apt-get install mdadm
```

- assemble your RAID partitions:

```
mdadm --assemble --scan
```

This makes mdadm look for your RAID partitions and assign them to /dev/mdX (X=0,1 etc). After running this command, mdadm should now list your RAID partitions.

- (after this, I performed a e2fsck on my RAID partitions first to make sure they were ok)

- follow the steps in the Howto using /dev/mdX instead of /dev/sdaX

---

### Post by Mickeysofine1972 on 2009-05-19
Hi

Last time I looked on the net this wasnt stable, is it ok to use as a filesystem now?

Mike

---

### Post by dozch on 2009-05-19
As far as I understand it ext4 is stable, but developers have been relying too much on a feature of ext3 (and perhaps other contemporary file systems) that ensures that files are committed to disk quickly and therefore safely. Ext4 takes the liberty to postpone committing files as it sees fit to increase performance (it is faster to wait writing to disk until you have a large chunk of data). This assumes that if a developer needs to ensure something gets written to disk 'now' he/she will have to explicitly specify this - an example is a change to a settings file. 

There has been a lot a discussion on whether this is a bug in the ext4 file system or a problem with developers relying on particular behaviour of a file system, which years ago was a commonly accepted no-no.

In practice there is a risk that you can lose a file on a system crash (a file that wasn't committed) but I believe that for Ubuntu ext4 has been modified so that it commits files faster - this obviously comes with a performance penalty but it is less likely that you lose stuff.

---

### Post by deepclutch on 2009-05-19
Ext4 is Fine working. :)

---

### Post by yaztromo on 2009-11-16
For those that are feeling brave I did the following between step 4 and 5.

Assuming your /boot is not on a separate partition and you have enough drive space:

```

cd /mnt
sudo mkdir temp
sudo cp -a bin boot etc lib opt sbin usr var home temp/
sudo rm -rf bin boot etc lib opt sbin usr var home
sudo mv temp/* ./
ls #to check the move worked!
sudo rm -r temp

```

Now all your files will benefit from ext4. This worked okay for me, **it may not for you**.

---

### Post by sasagundul on 2010-07-16
hi, nice tutorial you got here.

i'm currently running Maverick Alpha2 with kernel 2.6.35-7-generic.
i got karmic livecd too since i can't boot to lucid livecd.
my question is

1. can i use the step above to convert my ext3 filesystem to ext4? (i installed my system with Jaunty and using ext3 as the filesystem.)

2. is there any side effect or possibility of data loss by converting my ext3 filesystem to ext4 filesystem? 

thanks

---

### Post by whoop on 2010-07-26
> **sasagundul said:**
> hi, nice tutorial you got here.

i'm currently running Maverick Alpha2 with kernel 2.6.35-7-generic.
i got karmic livecd too since i can't boot to lucid livecd.
my question is

1. can i use the step above to convert my ext3 filesystem to ext4? (i installed my system with Jaunty and using ext3 as the filesystem.)

2. is there any side effect or possibility of data loss by converting my ext3 filesystem to ext4 filesystem? 

thanks
If you mean can I do this tutorial with karmic livecd, then yes...

There is always a possibility of data loss when reading/writing to a harddisk. I can't give you percentages about that...

---

