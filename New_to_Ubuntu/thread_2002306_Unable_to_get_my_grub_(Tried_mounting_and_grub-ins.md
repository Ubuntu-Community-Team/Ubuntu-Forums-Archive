---
title: "Unable to get my grub (Tried mounting and grub-install)"
date: 2012-06-12
forum: New to Ubuntu
---

### Post by tubby_aftab on 2012-06-12
Hello,
I am unable to recover my grub even after trying out the following steps:

1)sudo fdisk -l     resulted in this

 /dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848    83888127    41840640    7  HPFS/NTFS/exFAT
/dev/sda3        83888128   104859647    10485760    7  HPFS/NTFS/exFAT
/dev/sda4       104861694   449335295   172236801    5  Extended
/dev/sda5       163454976   165406719      975872   83  Linux
/dev/sda6       165408768   171266047     2928640   82  Linux swap / Solaris
/dev/sda7       171268096   449335295   139033600   83  Linux
 
2)Then I did this
sudo mount /dev/sda5 /mnt

3)sudo grub-install --root-directory=/mnt /dev/sda

4)sudo umount /dev/sda5

5)sudo reboot


 Let me know if I'm doing mounting the correct sda.(ie, sda5)
Even after doing all these steps, when I reboot, what I get is, a plain black and white screen, which doesn't list any available OS.(As you can see from the fdisk, I have 2 Windows and an Ubuntu 11.10). This is what the black and white screen looks like. Please check out  [http://scrnsht.com/hbqlqi](http://scrnsht.com/hbqlqi) . I have copy pasted the text below.

                                         GNU GRUB version 1.99-12ubuntu5
Minimal BASH-like line editing is  supported. For the first word, TAB lists possible command completions.  Anywhere else TAB lists possible device or file completions.

---

### Post by drs305 on 2012-06-12
tubby_aftab

Welcome to the Ubuntu Forums!

Unless your Ubuntu was on sda7 rather than sda5 it looks like you ran the correct commands. For some reason it is not finding your grub.cfg file in /boot/grub.

I'd recommend using the LiveCD and installing Boot Repair and let it try to fix you boot problems. I am pretty sure it will repair your  problem.

If it can't, there is an option to run the boot info script. It will post the results and you can supply the URL so we can take a look.

The Boot Repair link is in my signature line.

---

### Post by tubby_aftab on 2012-06-12
Thanks for the reply, 
I just tried running the same commands with sda7. But doesn't work. Gives the same problem.
I shall try installing Boot Repair and get back to you in a couple of minutes

---

### Post by drs305 on 2012-06-12
> **tubby_aftab said:**
> Thanks for the reply, 
I just tried running the same commands with sda7. But doesn't work. Gives the same problem. 
I shall try installing Boot Repair and get back to you in a couple of minutes

It would normally be sda5 so this is not a surprise. The grub-install command works on the MBR info but doesn't generate a new grub menu. I think the menu is missing, 

Boot Repair should work - if not we can try manually booting from the grub prompt.

---

### Post by tubby_aftab on 2012-06-12
I tried installing BootRepair from terminal using the commands,
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
But this is the error message I get. Please check out the link. [http://ScrnSht.com/gjkqml](http://ScrnSht.com/gjkqml)
When I click on AdvancedSettings, this is the menu I get, [http://ScrnSht.com/comttu](http://ScrnSht.com/comttu)
As you can see, the GRUB options are disabled.

---

### Post by drs305 on 2012-06-12
You shouldn't need the Advanced Options. On the opening page there should be a "Recommended repair". Just run that and see if it fixes the problem. Boot Repair is pretty good at figuring out what's wrong.

---

### Post by tubby_aftab on 2012-06-12
It is when I click the Recommended Repair that I get the error message, 
Please install the [mbr] packages. Then try again, and presents me with the start screen.

---

### Post by drs305 on 2012-06-12
This is not a normal message, since most users don't have to install "mbr". Hopefully this is not an indication that other files are missing as well. Run this command to install it and try again.
```

sudo apt-get install mbr
```

---

### Post by tubby_aftab on 2012-06-12
This is what I get on running the command
ubuntu@ubuntu:~$ sudo apt-get install mbr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mbr is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'mbr' has no installation candidate
ubuntu@ubuntu:~$

---

### Post by drs305 on 2012-06-12
It is in the 'universe' repository. You can make sure that repository is enabled by running the following command:
```
gksu software-properties-gtk
```
On the main tab (Ubuntu software) make sure the universe repository is enabled. If it is already ticked, try unticking, wait a few seconds, then retick it. Then try installing again.

---

### Post by tubby_aftab on 2012-06-12
I installed mbr and ran the RecommendedRepair based on your feedback.
This is the message I got after I ran the RecommendedRepair.

Boot successfully repaired.

Please note the following URL: [http://paste.ubuntu.com/1037300/](http://paste.ubuntu.com/1037300/)

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] or to your favorite support forum.

You can now reboot your computer.


But when I reboot my computer, it automatically boots to windows and shows only the Windows Boot Loader.

---

### Post by tubby_aftab on 2012-06-12
As I said, I have 2 windows and the BootLoader shows that correctly, but then again that's not the GRUB.

---

### Post by zSeries on 2012-06-12
I cant recall if grub-install does an automatic update-grub. I would try

sudo update-grub

between step 3 and 4. At least it will show the OS's it discovered.

---

### Post by tubby_aftab on 2012-06-12
At the moment, it's still on the Windows screen and says, "Attempting Repairs". It's been going on for the last 5-10 minutes. I'll keep it going for another 5 minutes and if it doesn't give any response, I'll stop and do a sudo update grub between steps 3 and 4.

---

### Post by drs305 on 2012-06-12
There are still problems with your Grub, including UUIDs in the grub menu and that Grub doesn't seem to be installed on your MBR.

Let's try this:
Boot the LiveCd, then mount /dev/sda5 and install Grub 2 to the MBR. Do NOT use the partition number in the second command:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /dev/sda5

```
Reboot and hold down the SHIFT key to reveal the Grub menu. Then try running these commands:
```
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/boot/vmlinuz-3.0.0-14-generic root=/dev/sda5 ro
initrd (hd0,5)/boot/initrd.img-3.0.0-14-generic
boot
```
You can use the TAB key to help complete the vmlinuz and initrd versions.

NOTE: This is going to remove the Windows option, but we can get it back via the LiveCD if GRUB doesn't work.

---

### Post by tubby_aftab on 2012-06-12
[http://ScrnSht.com/spcopg](http://ScrnSht.com/spcopg)

---

### Post by drs305 on 2012-06-12
> **tubby_aftab said:**
> [http://ScrnSht.com/spcopg](http://ScrnSht.com/spcopg)

I don't understand the post. Did you try running those commands and you still end up with the above?

If so, I would return to Boot Repair, purge and reinstall Grub via the Advanced option.

---

### Post by tubby_aftab on 2012-06-12
No I'm sorry my previous post was submitted almost at the same time as your previous post and is not a reply.

I tried running the commands you said by pressing down shift and it gives me an error saying 
error:file not found when I run the command 
linux (hd0,5)/boot/vmlinuz-3.0.0-14-generic root=/dev/sda5 ro

I'm running Ubuntu 11.10.What are we doing here exactly, are we trying to run the kernel if it exists ? In that case,am I running the wrong kernel number ?

---

### Post by tubby_aftab on 2012-06-12
I did a uname -r and my kernel seems to be
3.0.0-12-generic

---

### Post by drs305 on 2012-06-12
> **tubby_aftab said:**
> I did a uname -r and my kernel seems to be
3.0.0-12-generic

Is that the results when running the LiveCD? That may or may not be the same kernel as what you now have installed.

At the grub prompt, if you run the following it should show the kernel and initrd versions on your real system:
```
ls (hd0,5)/boot
```
Use whatever version it finds in the above command.

Also, as you enter the command once you have typed "vmlinuz-" you should be able to TAB to get it to complete or semi-complete the version number.

What we are doing is manually loading the information that GRUB needs to transfer control to the system (ID'ing the locations and versions of the kernel and initrd image). The information is normally conveyed by the grub.cfg file.

---

### Post by zSeries on 2012-06-12
sda5: __________________________________________________________________________      File system:       ext4     Boot sector type:  -     Boot sector info:      Operating System:       Boot files:        /grub/grub.cfg /grub/core.img /boot/grub/core.img

Should that be /boot/grub/grub.cfg etc? That is where I have them in 10.04 and I have never messed with grub.

---

### Post by drs305 on 2012-06-12
> **zSeries said:**
> sda5: __________________________________________________________________________      File system:       ext4     Boot sector type:  -     Boot sector info:      Operating System:       Boot files:        /grub/grub.cfg /grub/core.img /boot/grub/core.img

Should that be /boot/grub/grub.cfg etc? That is where I have them in 10.04 and I have never messed with grub.

Yes, and that is a good observation. But since then the reinstalling grub should have put the grub files back in the correct location (/boot/grub). I looked for a separate /boot partition but didn't see one.

If the last set of instructions didn't work it's time to run the boot info script again to see where we are.

---

### Post by tubby_aftab on 2012-06-12
At the grub prompt, you mean after holding down the shift key. If so, even for the command, ls (hd0,5)/boot, it gives me the error
error:file not found

---

### Post by drs305 on 2012-06-12
> **tubby_aftab said:**
> At the grub prompt, you mean after holding down the shift key. If so, even for the command, ls (hd0,5)/boot, it gives me the error
error:file not found

No, the SHIFT key is just for displaying the menu, but that was a while ago.

I didn't see that you had a separate boot partition but maybe I missed it. Would you please run the boot info script again and post the contents or link?

---

### Post by tubby_aftab on 2012-06-12
Is this sufficient ?
[http://paste.ubuntu.com/1037468/](http://paste.ubuntu.com/1037468/)

---

### Post by drs305 on 2012-06-12
As *zSeries* noted, your folder structure is still nonstandard. Your kernels are on / and not in /boot


```

set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz-3.0.0-14-generic root=/dev/sda5 ro
initrd (hd0,5)/initrd.img-3.0.0-14-generic
boot
```

If it still doesn't boot, what files (generally) are in (hd0,7)?

---

### Post by tubby_aftab on 2012-06-12
Ok, I'll do that in a second.
But why are the GRUB options still disabled in the BootRepair when I select the Advanced Options. This is how the advanced options screen looks for me
ScrnSht.com/tfwokg

---

### Post by drs305 on 2012-06-12
> **tubby_aftab said:**
> Ok, I'll do that in a second.
But why are the GRUB options still disabled in the BootRepair when I select the Advanced Options. This is how the advanced options screen looks for me
ScrnSht.com/tfwokg

The link didn't show up, but the way the author designed BR the unticked items I believe are the default settings. They may reflect the 'current' settings. I am on Quantal at the moment and don't have BR installed on it yet so I can't immediately check.

Edit: I'm installing it. I added the repository and package via the command line in the BR link, and I see it automatically installs "mbr" during it's installation.

---

### Post by tubby_aftab on 2012-06-12
I tried running the commands but no luck.
linux (hd0,5)/vmlinuz-3.0.0-14-generic root=/dev/sda5 ro

Just wanted to clear 2 points
1)There is a space before vmlinuz, correct ?
2)The last word is ro

I tried with both of these. but no.

---

### Post by tubby_aftab on 2012-06-12
Still says error:file not found

---

### Post by drs305 on 2012-06-12
Although the BIS (script) shows the kernels in hd0,5 and none in sda7, do you see kernels in either (hd0,7)/ or (hd0,7)/boot?

Added: Studying the results of the script, there are all sorts of problems with your grub menu. In the 'set root' line it uses the swap partition, it looks like grub is not a subfolder of /boot, you have core.img files on both sda5 and sda7, etc. Did you try setting this up with sda5 as /boot and sda7 as the main partition?

If this is a new installation it would probably be easier and faster to reinstall than to try to put things right.

---

### Post by tubby_aftab on 2012-06-12
Will try and reply in a second

---

### Post by tubby_aftab on 2012-06-12
I tried repeating the same with (hd0,7) but I always get stuck at
linux (hd0,7)/vmlinuz-3.0.0-14-generic root=/dev/sda7 ro

Not working !

---

### Post by drs305 on 2012-06-12
For some reason, your grub menu ended  up with the swap partition listed for some of the entries and it also contains non-existent UUIDs; it appears your boot folder is sda5 and / is on sda7.

Try booting again from the grub prompt:
```

set root=(hd0,7)
set prefix=(hd0,5)/grub
linux (hd0,5)/vmlinuz-3.0.0-14-generic root=/dev/sda7 ro
initrd (hd0,5)/initrd-3.0.0-14-generic
boot

```

---

### Post by tubby_aftab on 2012-06-12
While mounting, how should it be ?
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /dev/sda5

Or should these be replaced with sda7 ?

---

### Post by tubby_aftab on 2012-06-12
This is what I get when I try a sudo update-grub. Does this provide a hint ?

ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

---

### Post by drs305 on 2012-06-12
> **tubby_aftab said:**
> This is what I get when I try a sudo update-grub. Does this provide a hint ?

ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

You can't update it from a LiveCD/rescue CD unless you have used the 'chroot' procedure. Did you try the commands from my last post at the grub prompt?

---

### Post by tubby_aftab on 2012-06-12
Yes I did. Gives the same error.
But the commands you listed in the previous post should be done after mounting , correct ?
So should the mounting be done with /sda5 or /sda7 ?

I tried after mounting with /sda5

---

### Post by drs305 on 2012-06-12
The commands to chroot need to include the /boot and / partitions, since we now know you have both. Give me a few minutes and I will string them together here for you. Ideally you will have booted a LiveCD of the same version you installed so the Grub versions are the same. 

I'll post back in a couple of minutes.

---

### Post by tubby_aftab on 2012-06-12
Sure I shall wait.
Meanwhile is there a solution involving making any changes to the
/etc/default/grub ?

---

### Post by oldfred on 2012-06-12
Just to add a monkey wrench into the install, the boot info is not showing a fstab? I was looking to see if sda7 was /boot or /home but could not find the entry. 

Without fstab it will not boot. And with all the grub entries errors, it may just be easier to backup whatever you need and reinstall.

---

### Post by drs305 on 2012-06-12
Ah yes. Another screw up. Thanks oldfred. I'd sure like to know how some of this happened. Other than cloning I don't have any idea.

Since I'd typed this up anyway:
But after you mount the partitions, look for an /etc/fstab file. I you don't find one in /mnt/etc you won't be able to boot so don't bother with the rest.


Chroot commands from a LiveCD terminal:

```
sudo mount /dev/sda7 /mnt
sudo mount /dev/sda5 /mnt/boot
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
```

This should put you at a root prompt. 'sudo' is no longer required.

Now we will purge and reinstall grub.
```
apt-get update # Updates the repositories. Don't continue unless this step works.
apt-get purge grub-common

```Should remove grub, grub-pc and grub-common, plus some other grub packages. Make sure it says grub and grub-pc will be removed. You will be warned that it will remove the bootloader. Tab to OK.

```
apt-get install grub-pc
```

When selecting the device, use the SPACEBAR to select only sda and TAB to OK. Tick only 'sda' , not sda5 or sda7.

Redo the installation and update of grub, just to be sure the files were updated:
```
grub-install /dev/sda
update-grub
exit # Leave chroot.

```
```
for i in /dev/pts /dev /proc /sys /run; do sudo umount /mnt$i; done
```
If it generates errors, don't worry about it.
Reboot.

---

### Post by drs305 on 2012-06-12
Update: We explored the OP's system and determined that too many system folders were corrupted or missing to recover the installation.

To regain use of Windows we installed lilo and pointed the MBR back to the Windows installation. Windows now boots and the OP is considering reinstalling Ubuntu.

---

### Post by tubby_aftab on 2012-06-12
Thank you drs305 for all the help.
Yes by installing lilo, I am able to get back my windows partitions. But I'm still not able to recover my Linux Os or grub. What I got to know is that my system is severly messed up, and several files are missing.
Before closing the thread, I would like to try the steps drs305 pointed out on a different system and try and recover the grub.

Once again, thanks a lot drs305. Shall be back tomorrow.

---

### Post by tubby_aftab on 2012-06-20
I formatted my hard-disk, installed linux, then windows.(Basically brought it back to the same state where the Windows boot loader doesn't recogize Linux).
And followed the steps you told me - ie, installed Boot Repair. And it worked ! :)

Just for my understanding, can you tell me what these 2 lines mean

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda   

I have a small idea, haven't understood what mounting is. Sir, please mark the thread as solved.

---

### Post by drs305 on 2012-06-20
> **tubby_aftab said:**
> Just for my understanding, can you tell me what these 2 lines mean

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda   

I have a small idea, haven't understood what mounting is. Sir, please mark the thread as solved.

The grub-install command writes information to the MBR directing the system where to look for the Grub files. Unless you tell it otherwise, it assumes you are in the operating system you want to control the boot. The LiveCD is not the system you want to control things.

You mount your real OS's partition (sda5) to gain access to *it's* system files. In the second command, you are telling Grub to write the information to the MBR and to assume the operating system files are located on sda5. Grub writes information to the MBR indicating to look at sda5 for the /boot/grub folder, and to write certain files such as the core.img file to sda5's /boot/grub folder and not the LiveCD's /boot/grub folder.

---

### Post by tubby_aftab on 2012-06-20
So, basically the grub-install command tells MBR that the grub information can be found in /boot/grub of sda5 and not of the liveCD. Correct? 

I have a couple of doubts, in that case :
1)sudo mount /dev/sda5 /mnt
Here what is /mnt . Is it a place on the local LiveCD ?

2)Why can't we write something of this sort ?
sudo grub-install --root-directory=/dev/sda5 /dev/sda

3)What is the significance of /dev/sda in the line,
sudo grub-install --root-directory=/dev/sda5 /dev/sda

4)Is it right if I say that, we are not exactly **INSTALLING** a new grub, but we are just changing the information in the MBR saying that it should use the same grub which came with the linux installation done previously ?

5)When we do a 'mount', are we transferring all the required /dev/sda5 files to the local LiveCD ?

Thanks.

---

### Post by drs305 on 2012-06-20
> **tubby_aftab said:**
> So, basically the grub-install command tells MBR that the grub information can be found in /boot/grub of sda5 and not of the liveCD. Correct? 

I have a couple of doubts, in that case :
1)sudo mount /dev/sda5 /mnt
Here what is /mnt . Is it a place on the local LiveCD ?

/mnt is a universally-found folder in Ubuntu systems. Normally it's not recommended to mount partitions directly on /mnt since there could be something else already mounted there. But we know this is a LiveCD so we know we can safely use /mnt rather than create a new folder under /mnt such as /mnt/temp...

> 
2)Why can't we write something of this sort ?
sudo grub-install --root-directory=/dev/sda5 /dev/sda

Because that's not the way the developers wrote it. The root-directory switch must point to a folder, and /dev/sda5 is not a folder.

> 
3)What is the significance of /dev/sda in the line,
sudo grub-install --root-directory=/dev/sda5 /dev/sda

/dev/sda is the *drive* on which GRUB is going to alter the MBR. It should be the drive BIOS boots first, so if BIOS booted your second drive, the command should be /dev/sdb to place the Grub pointer on the second drive. You can put it on both if desired.

> 
4)Is it right if I say that, we are not exactly **INSTALLING** a new grub, but we are just changing the information in the MBR saying that it should use the same grub which came with the linux installation done previously ?

Yes, mostly. It does write some files to /boot/grub/ and restores the module files, but it doesn't really 'install' grub the way the word implies.
> 
5)When we do a 'mount', are we transferring all the required /dev/sda5 files to the local LiveCD ?

Thanks.
No, nothing is transferred. Mounting merely allows your current system to *access* the folders and files on a partition. Until a partition is mounted (either automatically at boot or manually afterward) its files cannot be seen, used or modified.

Happy Ubuntu-ing.

---

### Post by tubby_aftab on 2012-06-20
Thanks a lot drs305. It's clear now. 1 last question, instead of mounting to /mnt, can I mount to any other folder ?

---

### Post by drs305 on 2012-06-20
> **tubby_aftab said:**
> Thanks a lot drs305. It's clear now. 1 last question, instead of mounting to /mnt, can I mount to any other folder ?

Yes, you can mount it to any folder you want.*

* When you mount a partition, it is mounted over any *existing* data on the same mount point/folder. 

Let's say you have a data partition (sda7) mounted on /mnt/data. You mount sda5 on /mnt/data. You will now see the contents of sda5 on /mnt/data, but you will not be able to see/access your *data* folders/files until you unmount sda5.

So you can mount a partition on almost any folder you want, but you should make sure it is empty first.

---

### Post by tubby_aftab on 2012-06-21
drs305, I was just trying to understand things better, and playing around.

This is the result of my sudo fdisk -l. I have 3 doubts
1)Why doesn't it show anything about my /dev/sdb ? I understand that sda is my PrimaryHD and sdc is the BootablePenDrive on which I'm running the OS.

2)And 1 block is 2 sectors ? That's what the math says.(Block size comes out to be 1024.something bytes)

3)Is there a way to find out which among sda5,sda6,sda7 is /, /boot and /home (apart from guessing through sizes)? Because unless you know that, you won't be able to mount.

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000826f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1         1955838   184571903    91308033    5  Extended
/dev/sda2   *   195311616   195516415      102400    7  HPFS/NTFS/exFAT
/dev/sda3       195516416   488394751   146439168    7  HPFS/NTFS/exFAT
/dev/sda5         1955840     3907583      975872   83  Linux
/dev/sda6         3909632   179689471    87889920   83  Linux
/dev/sda7       179691520   184571903     2440192   83  Linux

Disk /dev/sdc: 8103 MB, 8103395328 bytes
255 heads, 63 sectors/track, 985 cylinders, total 15826944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048    15826943     7912448    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sdb
ubuntu@ubuntu:~$ 

```

---

### Post by tubby_aftab on 2012-06-21
This is a bit weird, I just wanted to see if sdb is my DVD drive or something, so I inserted a DVD and then ran fdisk.

This is what I get. Now there is an sdb, (which is surely my pendrive again - 8GB it says), but now there is no mention of sdc

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000826f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2046   195309567    97653761    5  Extended
/dev/sda2   *   195311616   195516415      102400    7  HPFS/NTFS/exFAT
/dev/sda3       195516416   488394751   146439168    7  HPFS/NTFS/exFAT
/dev/sda5            2048    19531775     9764864   83  Linux
/dev/sda6        19533824   177733631    79099904   83  Linux
/dev/sda7       177735680   195309567     8786944   82  Linux swap / Solaris

Disk /dev/sdb: 8103 MB, 8103395328 bytes
255 heads, 63 sectors/track, 985 cylinders, total 15826944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    15826943     7912448    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 

```

---

### Post by drs305 on 2012-06-21
> **tubby_aftab said:**
> 
This is the result of my sudo fdisk -l. I have 3 doubts
1)Why doesn't it show anything about my /dev/sdb ? I understand that sda is my PrimaryHD and sdc is the BootablePenDrive on which I'm running the OS.

2)And 1 block is 2 sectors ? That's what the math says.(Block size comes out to be 1024.something bytes)

3)Is there a way to find out which among sda5,sda6,sda7 is /, /boot and /home (apart from guessing through sizes)? Because unless you know that, you won't be able to mount.


I don't know why your sdb drive is not displaying. If it's a Windows format you might boot Windows (if possible) or use a Windows recovery CD and run chkdsk. Sometimes disk errors prevent Linux from properly identifying partitions - not sure about the entire disk.

The small partition could have something to do with booting Windows but I don't use that OS so I can't say.

You can inspect the contents of a partition by mounting it. Since the /mnt folder is empty on an Ubuntu CD, you can use the following commands to look at the contents. Once you have unmounted (umount) the partition you can repeat it for the next one.

```
sudo mount /dev/sda5 /mnt
ls /mnt
sudo umount /dev/sda5
```

fdisk (edit: in your earlier post) shows your partitions not starting at the beginning of the drive. Curiously, unless you've done somethign to it, it starts much earlier in your last post (2046). You may have unallocated space which could be made into another  primary partition.

*gparted* is a great tool that can really help understand the partition structure of a drive. If your 'missing' drive is attached it will try to read that one as well.

---

