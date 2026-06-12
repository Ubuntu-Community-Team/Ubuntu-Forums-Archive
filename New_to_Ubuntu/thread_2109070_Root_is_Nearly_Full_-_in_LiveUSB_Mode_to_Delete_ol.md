---
title: "Root is Nearly Full - in LiveUSB Mode to Delete old Kernels"
date: 2013-01-26
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-01-26
I don't have the GRUB Recovery Screen due to a video card exchange. I asked for help about fixing that over a year ago, but have never had a response.

This 12.04 LTS hangs at boot time. I've spent the last 3 days on LiveUSB mode trying to fix it. It's come down to this:

I saw the number of old kernels a few days ago and started deleting about half of them. I was very very careful to not delete my

3.2.0.36-generic-pae ( or very close to those numbers I cannot recall the numbers, _exactly_).

or any with matching those numbers.

After those 20 or so old kernels were manually deleted, the OS would no longer boot. So here I am in LiveUSB and need help in deleting the out-of-date kernels. I could not perform that in boot-repair-disk session; even though it said I should. Maybe I'm not familiar with how it operates. It's my first use of it. Meanwhile in Boot-Repair-Disk the number of old kernels looked to be around 50, even though I though I manually deleted about half of them. And in another section of the Boot-Repair-Disk, under the heading GRUB, the old kernels were still there, too. I cannot post the RESULTS.txt as this forum says 49Kb is too large.

Can you explain how I can mount the hard-drive and somehow delete the old kernels and then start working on repairing GRUB2?

Also, please tell me the name of the folder (directory) where all the kernles are kept. For example: is that / OR /Boot or Bin -- with / being root, obviously?

I found a command line tutorial about removing old kernels with one line here:

 [http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

---

### Post by prodigy_ on 2013-01-26
I'd suggest reinstalling on a bigger partition. Removing old kernels can yield some space but almost certainly not enough in the long run.

But if you really need to fix this installation, try to reinstall Grub (via chroot): [https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot](https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot) This should help unless you've deleted ALL kernels.

---

### Post by Mark_in_Hollywood on 2013-01-26
> **prodigy_ said:**
> I'd suggest reinstalling on a bigger partition. Removing old kernels can yield some space but almost certainly not enough in the long run.

But if you really need to fix this installation, try to reinstall Grub (via chroot): [https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot](https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot) This should help unless you've deleted ALL kernels.

My / (root partition) is about 16 gig. It's 14.5 gig full. Boot-Repair-Disk says delete them, as that fullness is preventing a boot. My /home is on a separate partiton. /sda3 and sda5 respectively.

I don't understand what you mean by: "But if you really need to fix this installation" - Please explain, briefly if possible, how a GRUB reinstall will fix the problem, but removing the old kernels won't? My theory here is: less is more.

---

### Post by Mark_in_Hollywood on 2013-01-26
If no error reported then /boot/grub is NOT mounted?

ubuntu@ubuntu:~$ sudo grub-install --boot-directory=/mnt/boot /dev/sda
[COLOR="Red"]Installation finished. No error reported.[/COLOR]

ubuntu@ubuntu:~$ sudo chroot /mnt

root@ubuntu:/# grub-install --recheck /dev/sda

[COLOR="Red"]/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).[/COLOR]

---

### Post by frank604 on 2013-01-26
Just some precursory investigations here, please copy paste the output for

```
dpkg -l | grep linux-image
```


```
uname -a
```

---

### Post by Mark_in_Hollywood on 2013-01-26
I'm not adept at this, but I believe this information is the LiveUSB filesystem and NOT my hard-disk (real) kernel. I'm more likely to be wrong than right, here, but I'm just double-checking.

ubuntu@ubuntu:~$ dpkg -l | grep linux-image
ii  linux-image-3.2.0-23-generic-pae       3.2.0-23.36                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-generic-pae                3.2.0.23.25                             Generic Linux kernel image
ubuntu@ubuntu:~$ uname -r
3.2.0-23-generic-pae
ubuntu@ubuntu:~$

---

### Post by prodigy_ on 2013-01-26
> **Mark_in_Hollywood said:**
> Please explain, briefly if possible, how a GRUB reinstall will fix the problem, but removing the old kernels won't? My theory here is: less is more.

Hm. If I understand correctly, the problem is that your Ubuntu no longer boots after some kernel cleanup. That's what you can fix with with the **update-grub** command (while chrooted into your installation as described in the HOWTO I linked).

And if you actually can boot into your installation, just use the one-liner from your OP. It'll do the job (remove old kernels) for you.

---

### Post by Mark_in_Hollywood on 2013-01-26
I want to do a little more than merely remove the old kernels. Some 18 months ago, my video card (EVGA 9500GT) was RMA'd to EVGA for a defect. During that time, I used the on-board video. That caused a GRUB resolution problem, with, if I'm recalling correctly, the GRUB boot time lines either scrolling off screen (right side) or some other problem. I got some help to reset the GRUB resolution or boot-time screen resolution. After re-installing the new vid card, GRUB had no video at any other screen that the selectable options, to wit: Ubuntu, Memory Test, and Windows 7. Trying Recover (or Rescue) or whatever it is called blanks the screen. I posted to IRC#GRUB (or some such) and posted about that problem, this Forum at that time, but never received an answer.

So what I want to accomplish in LiveUSB is to purge and re-install GRUB and all it's associated files, in hopes of restoring proper working order GRUB boot-time and then I'll remove the old kernels.

---

### Post by frank604 on 2013-01-26
[http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels](http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels)

Perhaps the top comment in the link + the grub-install you wish to do.  But the mounting in this post makes sense prior to chrooting in.

---

### Post by Mark_in_Hollywood on 2013-01-26
Per the post at AskUbuntu.com I did in a terminal via cut and paste, only:

Boot into a live CD (or live USB), mount some systems, chroot into it and install the kernel. After a successful installation of the kernel, unmount the filesystems.

    Open Terminal
    Mount the Ubuntu partition: sudo mount /dev/sdXY /mnt

    Mount some special partitions:

    sudo mount --bind /dev /mnt/dev
    sudo mount --bind /proc /mnt/proc
    sudo mount --bind /sys /mnt/sys

    Chroot into the /mnt: sudo chroot /mnt
    Install the Linux kernel: apt-get install linux-image-generic (no sudo required as you are root after a chroot)

    After a successful installation of the kernel, get out the chroot and unmount some filesystems:

    exit
    sudo umount /mnt/sys
    sudo umount /mnt/proc
    sudo umount /mnt/dev
    sudo umount /mnt

    Reboot and remove CD or USB: sudo reboot

apt-get reported that current (or latest) kernel is installed.

on reboot it hangs after about 10 to 15 seconds. It seems like the same place every time, but I can't be certain of that.

=========

I next again tried:

ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt/boot

ubuntu@ubuntu:~$ sudo chroot /mnt
chroot: failed to run command `/bin/bash': No such file or directory

=========

and I tried:


ubuntu@ubuntu:~$ sudo chroot /mnt/boot
root@ubuntu:/# update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

---

### Post by oldfred on 2013-01-26
Lets see exactly where everything is at. You can just install Boot-Repair to your current live install.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by frank604 on 2013-01-26
Can you try to update grub before the exit command?

---

### Post by Mark_in_Hollywood on 2013-01-26
Link requested per Old Fred:

[http://paste.ubuntu.com/1574506/](http://paste.ubuntu.com/1574506/)

and briefly what I saw following the instructions on the page:

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Terminal said, at various lines:

cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab

many line later

(glade2script:18690): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.0BPURW': No such file or directory

(glade2script:18690): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

---

### Post by frank604 on 2013-01-26
can you give output to ```
cat /etc/default/grub
```
edit: nevermind, it is in the output pastebin that you posted, I'll read them more in depth now

---

### Post by frank604 on 2013-01-26
Here is an easier to follow link [http://ssatish.wordpress.com/2013/01/11/how-to-re-install-grub-2-in-mbr-from-ubuntu-live-disk/](http://ssatish.wordpress.com/2013/01/11/how-to-re-install-grub-2-in-mbr-from-ubuntu-live-disk/)

Also for the new video card booting error that you posted over a year ago, perhaps modify 
```
 sudo gedit /etc/default/grub
```
change the line > GRUB_CMDLINE_LINUX=" vga=769" to > GRUB_CMDLINE_LINUX=""
Then update-grub 
If that doesn't work then try > GRUB_CMDLINE_LINUX=" gfxpayload=true gfxpayload=640x480x8"

---

### Post by Mark_in_Hollywood on 2013-01-26
In the grub.cfg, the line you suggested:

GRUB_CMDLINE_LINUX="" 

was already there. I have changed it to:

GRUB_CMDLINE_LINUX=" gfxpayload=true gfxpayload=640x480x8"

I'll know in a moment.

The commands at the new page worked without throwing out an error message.

I'm keeping my fingers crossed.

It will be about 10 minutes from 17:37 Pacific Time. As you are just North of me, we are on the same time. Or at least in the same time zone.

---

### Post by frank604 on 2013-01-26
strange, the grub_cmdline_linux in your config was set to vga=769.... give an update on each issue, I'm eager to see if both issues are resolved.

---

### Post by Mark_in_Hollywood on 2013-01-26
The Grub page, where I select boot into Ubuntu or boot into Grub Recovery is still non-functional. Using the cursor key to move down to Recovery and then pressing the Enter key I hear the disk spin up and the screen goes blank. The only allowable selections are the current (top) generic-xxxxx-pae
or Windows 7. They will call the OS. Even the Windows went down the other day. That why I have been in LiveUSB for 4 days in a row. No panicking, just saying. I was able to do a backup 4 days ago, just before the trouble got serious. I can do a clean install if worse comes to worse.

The message below is what grub throws up on the screen for about 3 seconds:

[COLOR="Red"]vga769 is deprecated. Use set gfxpayload=640x480x8, 600x400 before linux command instead[/COLOR]

The OS hangs in about the same place. There is some yellow text along with some white text. The white text is what I saw when the OS would boot.

I apologize for all the philosophy mixed into this post.

---

### Post by sandyd on 2013-01-26
nvm - ling/bilberry desync

---

### Post by Mark_in_Hollywood on 2013-01-26
Here is a link to the photo I took of the boot time progress or lack thereof

[http://www.flickr.com/photos/25024945@N00/8417862343/in/photostream](http://www.flickr.com/photos/25024945@N00/8417862343/in/photostream)

and

a pix of what happened on reboot immediately after grub-update


[http://www.flickr.com/photos/25024945@N00/8417859401/in/photostream](http://www.flickr.com/photos/25024945@N00/8417859401/in/photostream)


I cannot post them to this Forum. They are too big in bits.

---

### Post by frank604 on 2013-01-26
Let's ignore the vga deprecated error for now, it isn't an error that would stop your booting.

At the grub menu, press up/down key and highlight the ubuntu, can you press 'e' or whatever key to see the syntax for the booting.  I'm sure there is an easier way but this is the only way I know (I'm at work on windows atm).

What is the error message when you select boot to ubuntu?

EDIT: Try to update initramfs

---

### Post by Mark_in_Hollywood on 2013-01-26
I misrepresented that the grub options screen won't allow any but the current kernel, or the WindowsOS. In fact, I cursored down to Previous and selected the oldest one I could find. It still will not boot but seems to hang with more or less the same lines on the screen.

There is no error message upon grub selecting and passing off to linux-3.2.0-36-generic-pae or any other kernel.

The "e" command produces this when on the above named kernel.

GNU GRUB Version 1.99-21ubuntu3.7

isubksetparams 'Ubuntu, with Linux 3.2.0-36-generic-pae
recordfail
gfxmode $linux_gfx_mode
insmod gzio
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no floppy --fs-uuid --set-root a19439e8-8efd-460b-8014-4a442c19628c
linux /boot/vmlinuz-3.2.0-36-generic-pae root=uuid=a10439e-8efd-460b-4a442c1962c ro vga=769 quiet splash $vt_handoff
initrd /boot/initrd.img-3.2.0-36-generic-pae

I had copied this from a pix of the screen I had taken several days ago as the non-boot trouble began, so I hope this is current.

The grub recovery has a slightly different set of values and the Windows line now has 2 lines. Odd I never saw that before. One is for /sda1 the other for /sda2.

Do you want to see the complete set of lines from "e" of grub recovery? I have a photograph of it and can type it but it will take a few minutes, as I'm not a touch typist.

Meanwhile I'm off to see how to do the update you suggested.

UPDATE on:

root@ubuntu:~# sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic-pae
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab

Lastly, the "e" output from grub at the kernel selection screen is:

Grub as Recovery

getparams 'Ubuntu, with Linux 3.2.0-36-generic-pae (recovery mode)'
recordfail
insmod gzio
insmod part_msdos
insmos ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root a10439e-8efd-460b-4a442c1962c
echo "Loading Linux 3.2.0-36-generic-pae ...'
linux /boot/vmlinuz-3.2.0-36-generic-pae root=uuid=a10439e-8efd-460b-4a442c1962c ro recovery nomodeset vga=769
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-3.2.0-36-generic-pae

=======================

Grub as Windows

getparams 'Windows 7 (loader) (on /dev/sda1)'
insmod part_msdos
insmod ntfs
set root '(hd0, msdos3)'
search --no-floppy --fs-uuid --setroot A2CC0BA6CC0B7379 (this string A2CC may be in error. the pix is fuzzy. But the same loader on /sda2 reads: 12BCECA0BCEC7F99

---

### Post by frank604 on 2013-01-26
> **Mark_in_Hollywood said:**
> 




search --no floppy --fs-uuid --set-root a19439e8-8efd-460b-8014-4a442c19628c
linux /boot/vmlinuz-3.2.0-36-generic-pae root=uuid=a10439e-8efd-460b-4a442c1962c ro vga=769 quiet splash $vt_handoff
initrd /boot/initrd.img-3.2.0-36-generic-pae


Grub as Recovery

getparams 'Ubuntu, with Linux 3.2.0-36-generic-pae (recovery mode)'
recordfail
insmod gzio
insmod part_msdos
insmos ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root a10439e-8efd-460b-4a442c1962c
echo "Loading Linux 3.2.0-36-generic-pae ...'
linux /boot/vmlinuz-3.2.0-36-generic-pae root=uuid=a10439e-8efd-460b-4a442c1962c ro recovery nomodeset vga=769
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-3.2.0-36-generic-pae

=======================


The reason why it may not be booting up is that your grub is set to boot off UUID a10439e-8efd-460b-4a442c1962c for both normal and recovery.

According to your pastebin in page 2, your linux is on /dev/sda3 and the UUID for this is 
a19439e8-8efd-460b-8014-4a442c19628c

As a trial, try to change the uuid and see if it boots, if it does then you can do a perm fix.

---

### Post by Mark_in_Hollywood on 2013-01-26
> **frank604 said:**
> The reason why it may not be booting up is that your grub is set to boot off UUID a10439e-8efd-460b-4a442c1962c for both normal and recovery.

According to your pastebin in page 2, your linux is on /dev/sda3 and the UUID for this is 
a19439e8-8efd-460b-8014-4a442c19628c

As a trial, try to change the uuid and see if it boots, if it does then you can do a perm fix.

I would use the "e" command at boot and use:

a19439e8-8efd-460b-8014-4a442c19628c

or will I be editing fstab? or grub.cfg?

Again, thank you for all this help, and I hope I'm not being tedious. I'm rather than "it just works", I'm "just lost".

---

### Post by frank604 on 2013-01-26
change it in both 
/boot/grub/grub.cfg
/etc/fstab

to get the UUID so you can copy and paste it from ```
blkid
```Just remember one thing, your linux partition is /dev/sda3
the UUID should be a19439e8-8efd-460b-8014-4a442c19628c

Edit1:If it boots up, then run update-grub again and see if that perm fixes it for you.
Edit2:Create backups of both grub.cfg and fstab if possible.  That way if this doesn't work you can revert back to original and we can try a diff approach.

---

### Post by Mark_in_Hollywood on 2013-01-27
> **frank604 said:**
> change it in both 
/boot/grub/grub.cfg
/etc/fstab

to get the UUID so you can copy and paste it from ```
blkid
```Just remember one thing, your linux partition is /dev/sda3
the UUID should be a19439e8-8efd-460b-8014-4a442c19628c

Edit1:If it boots up, then run update-grub again and see if that perm fixes it for you.
Edit2:Create backups of both grub.cfg and fstab if possible.  That way if this doesn't work you can revert back to original and we can try a diff approach.

Nothing has changed. The boot time hangs and the recover mode shows a blank screen.

My apologies. I have been at this over 8 hours today. I'm getting punchy from staring at the screen. I was able to find the grub.cfg, but it was a struggle and that made me forget to make a backup. When I re-booted I see that the recovery has one uuid and the other a different uuid, when I "e" at boot time screen.

I could not find fstab or a way to edit it. And it's too late to continue this I cannot safely concentrate (I'm in my 60s). So, for now, thank you for your consideration and help. 

I'm going to try this again, around 10 am tomorrow, if you have any interest left.

good night.

---

### Post by oldfred on 2013-01-27
Boot script did not show as much as I had hoped. Maybe because of your encryption as script does not show any boot files anywhere, but grub has found them. So first part of script that shows boot files must not be able to parse encrypted data. Does script ask for passphrase later?

       vga=xxx is a deprecated boot option
Use this with your monitor size in /etc/default/grub:
GRUB_GFXMODE=1024x768
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993)
gksudo gedit /etc/default/grub
sudo update-grub
"VGA Deprecated" Message on Boot
[http://ubuntuforums.org/showthread.php?t=1453524](http://ubuntuforums.org/showthread.php?t=1453524)

    
Are you now booting with nVidia card? Do you have nvidia drivers installed or not. If not you need nomodeset, but not the vga= entry. 
If nVidia drivers are installed you should not need the nomodeset.

---

### Post by Mark_in_Hollywood on 2013-01-27
Dear Old Fred (I always wanted to say that).

As the OS started to balk at boot time, one of the error messages it thew on screen was /LEXAR not mounted to you want to Continue, Skip, Mount?

/LEXAR is a thumb (jump, flash, pen) drive that another poster, this Forum, helped me mount in fstab. The reason for that is /LEXAR had encrypted folders on it. Like hiding money under the mattress.

I tried 2 or 3 times to make the /LEXAR mount, each time the boot getting worse. One one occasion, seeing the OS say /LEXAR NOT mounted, I pulled the device from it's usb and re-booted. That may be what corrupted the whole thing, but I'm not sure.

Meanwhile, doing

gksudo gedit /etc/default/grub

Terminal output:

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in **real GRUB** with the command `vbeinfo'
#GRUB_GFXMODE=640x480

What??? The grub.cfg I'm trying to edit isn't the "real" grub.cfg?

Here is what I see in the not-real? grub. No line as you give: GRUB_GFXMODE=1024x768


[COLOR="Red"]GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="gfxpayload=true gfxpayload=640x480x8"[/COLOR]

I have to ask for the instructions on how to access the files necessary for editing. Does the /sda3 need mounting to do this? If, yes, then I'll have to know the commands for that as well. For example, looking at fstab bring up (I'm certain) the fstab for the LiveUSB session and not the file on my hard-drive.

---

### Post by oldfred on 2013-01-27
I never noticed it said real grub. :) maybe they think grub2 is now the real grub as grub legacy is not maintained anymore.

If sda3 you will need to mount it and edit that mount points files.
       sudo mount /dev/sda3 /mnt
       
 gksu gedit /mnt/etc/default/grub
    #and if editing fstab

           
 gksu gedit /mnt/etc/fstab

---

### Post by Mark_in_Hollywood on 2013-01-27
For reference, this is the fstab as it currently exists. I had commented out the lines concerning /LEXAR, about 4 days ago. I have copies of my current grub and fstab. So let's edit. When I modify system files, I refer to myself as mp, viz.: *mp added the ## on 24-jan-13*

Current fstab:

[COLOR="Red"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda3 :
UUID=a19439e8-8efd-460b-8014-4a442c19628c	/	ext3	errors=remount-ro	0	1
#Entry for /dev/sda5 :
UUID=36cdd55c-9079-4455-8627-c3b8bfda3a45	/home	ext3	defaults,user_xattr	0	2
#Entry for /dev/sda1 :
UUID=A2CC8BA6CC8B7379	/media/System_Reserved	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sda2 :
UUID=12BCECA0BCEC7F99	/media/sda2	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sda6 :
UUID=0ac46a28-6e61-4dc4-b144-a792803ff60b	none	swap	sw	0	0
[B]##Entry for /dev/sdb1 :
##UUID=8874-D051	/LEXAR	vfat	##uid=1000,gid=1000,umask=022	0	2
##above 3 lines start ##Entry and mp added the ## on 24-jan-13[/B][/COLOR]


**Here is the text of fstab.bak from 03-July-2012. It must be from the time I was working on mounting /LEXAR.**

[COLOR="Red"]proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda3 :
UUID=a19439e8-8efd-460b-8014-4a442c19628c	/	ext3	errors=remount-ro	0	1
#Entry for /dev/sda5 :
UUID=36cdd55c-9079-4455-8627-c3b8bfda3a45	/home	ext3	defaults	0	2
#Entry for /dev/sda1 :
UUID=A2CC8BA6CC8B7379	/media/System_Reserved	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda2 :
UUID=12BCECA0BCEC7F99	/media/sda2	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda6 :
UUID=0ac46a28-6e61-4dc4-b144-a792803ff60b	none	swap	sw	0	0
#Entry for /dev/sdc1
/dev/disk/by-uuid/8874-D051	/LEXAR vfat uid=1000,gid=1000,umask=022 0 2[/COLOR]

[B]OldFred - are you saying add the line: 

GRUB_GFXMODE=1024x768

as an additional line? [/B]

Also, while trying to understand what to do with that line, I saw a [post]("http://askubuntu.com/questions/79323/how-do-you-get-the-very-first-boot-messages-smaller") about it, and their the poster was using

sudo update-grub2

which I have not been doing. Is it update-grub or update-grub2 ?

---

### Post by oldfred on 2013-01-27
The gfxmode should be in etc/default/grub, you should have an existing one commented out with the #. You can uncomment it to use default 640x480 or change to whatever is you true size. Example was just shown.

Generally removable devices should not be mounted with fstab unless you will always have it plugged in.

I do not suggest mounting the Windows system partition sda1, as you should never need to get to it from Linux. 
I also prefer setting the Windows system partition as read-only and create a shared NTFS data partition for any data you may want to share between systems. The Linux NTFS drive exposes all the hidden Windows files & folders and it is too easy to accidentally damage something. In Windows I always turned on show the hidden files & often damaged something. :)

---

### Post by Mark_in_Hollywood on 2013-01-27
Does placement of that grub line matter?

From:

[GRUB 2, graphical boot tips to set the desired VGA console mode.]("http://www.intdblog.com/2009/09/grub-2-graphical-boot-tips-to-set.html")


[COLOR="Red"]4. What I tested and what I not: set gfxpayload=keep MUST be UNDER the set gfxmode=${GRUB_GFXMODE} statement, i tried to put it at the end of the grub.cfg file through other scripts that Debian explicitly define custom, like 40_custom (always in our GRUB 2 scripts dir /etc/grub.d), but nothing worked, so like any well made worker i found my way.[/COLOR]

LASTLY:

I want to delete all the Microsoft partitions. One is "System Reserved" /sda1 and the other is /sda2 (about 70 gig). 

Would deleting these partitions in any way simplify the job of fixing my boot time? I'ld be glad to do the deletion as I have intended it for a while, now.

I added the line to /etc/default/grub - saved and exited gedit

I ran update-grub 

said no such device

then I remembered:

and

ubuntu@ubuntu:/$ sudo chroot /mnt
root@ubuntu:/# update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

---

### Post by oldfred on 2013-01-27
You have to chroot into your install if you want to run the sudo update-grub. And that is more than just mounting one folder.

If you only changed one minor thing you can violate the rule and just edit grub.cfg. And edit will be lost on next grub update.

       #Normally we do not directly edit grub.cfg. Edit from live-CD/DVD/USB.

   mount /dev/sda3 /mnt
gksu gedit /mnt/boot/grub/grub.cfg
#May have to do this first as it is write protected also:
sudo chmod +w /mnt/boot/grub/grub.cfg
#Or even this first:
sudo chmod 777 /mnt/boot/grub/grub.cfg

Have you used Boot-Repair? It automates or semi-automates a lot of this.

When you say delete sda1 & sda2, you mean from fstab. Just put a # at the beginning of the line. I have had issues in the past where a NTFS partition needed chkdsk caused issues mounting partition and slowed boot.

---

### Post by Mark_in_Hollywood on 2013-01-27
I want to delete the partitions that Windows7 uses. I will then resize the linux partitons to make use of it. 

I tried boot-repair and it said (I'm paraphrasing)

delete files, partition is full

That is at Thread #3, this post. I'll run it again.

[http://paste.ubuntu.com/1577847/](http://paste.ubuntu.com/1577847/)

boot-repair reported: success

---

### Post by frank604 on 2013-01-27
@Oldfred: What do you think is the issue that is preventing boot up?  Considering that sda3 is 100% full and Mark wishes to delete his windows partition, couldn't he just boot liveusb -> delete partition /sda1 (windows reserved - deletable) and /sda2 (windows main partition - deletable) -> resize /sda3 to encompass the free space from sda1+sda2?

---

### Post by Mark_in_Hollywood on 2013-01-27
Ran boot repair disk twice, setting to REPAIR. Once in LiveUSB session and a 2nd time in boot-repair-disk CD. 

BIS for 2nd run

[http://paste.ubuntu.com/1578103/](http://paste.ubuntu.com/1578103/)

---

### Post by oldfred on 2013-01-27
Better to use pastebin link for BootInfo or at least use code tags to preserve formatting and make it easier to review.

You get grub menu. Does recovery not boot at all or do you get some loading on the screen? 
Does Windows boot? You should have boot flag on sda1, but grub does not care. If booting Windows from MBR you would have to have boot flag on sda1.

When trying to boot at grub menu use e and remove the vga=769 on the linux line.

You should be able to chroot into your install and run many commands to houseclean.

@frank604
Not sure he wants to delete sda1 & sda2.  I thought that was deleting from fstab?
I always hesitate to move a partition left as that often causes issues, but there is no easy way to move /home right to make more room for /. But / at 15GB should be plenty. With all the old kernels no housecleaning has been done for ages, so kernels, logs, debs and lots of old stuff is filling root. 
I think it should boot if it just has a little space.

---

### Post by frank604 on 2013-01-27
Then maybe he can install and run bleachbit to help him free up some space?

---

### Post by Mark_in_Hollywood on 2013-01-27
> **oldfred said:**
> Better to use pastebin link for BootInfo or at least use code tags to preserve formatting and make it easier to review.

Easier to do that I thought, it's

[http://paste.ubuntu.com/1578103/](http://paste.ubuntu.com/1578103/)



You get grub menu. Does recovery not boot at all or do you get some loading on the screen? 

Nothing is visible on the screen. I have looked and looked for the 5 or 6 options that show up at grub recovery mode, but have never found any. I know that I can cursor down and select something, but that does not bring text or gui or info to the screen.

I had a look at the Win Partition Mgr. "everything is healthy" - I would not like to see Dr. MS for a slight scratch!

Does Windows boot? You should have boot flag on sda1, but grub does not care. If booting Windows from MBR you would have to have boot flag on sda1.

I did not try to boot Windows, after running book-repair-disk. I did try ubuntu-3.2.0-36-generic-pae and grub recovery.

When trying to boot at grub menu use e and remove the vga=769 on the linux line.

Strangely, the grub screen to select the Ubuntu, previous Ubuntu, Recovery and Windows is now a nice size, correctly placed in the middle of the screen and easy to read. It's been years.

You should be able to chroot into your install and run many commands to houseclean.

@frank604
Not sure he wants to delete sda1 & sda2.  I thought that was deleting from fstab?

NO SIR, I am going to delete those Windows partitions. If it's not smart to expand / then /home, I will make one larger partition of the two windows partitions, set them as ext2 and use them for MythTV tv program storage. It was installing/configging MythTV that the boot time problems got so serious.

I always hesitate to move a partition left as that often causes issues, but there is no easy way to move /home right to make more room for /. But / at 15GB should be plenty. With all the old kernels no housecleaning has been done for ages, so kernels, logs, debs and lots of old stuff is filling root. 
I think it should boot if it just has a little space.

I will be back in a few minutes, after I see if something boots. I'll try the Windows line, too.

A Few Minutes Later:

Windows 7 will boot into safe mode.

Ubuntu "Main" will not boot past a certain point
Recover Mode boots, but puts nothing visible on-screen - I hear the disk spin up for a few seconds.

After the boot-repair-disk ran and reported success, I can no longer use the LiveUSB drive. LiveCD is where I am now.

I saw some boot-time screens and have pix of them as follows:

something about usb device descriptor error
[http://www.flickr.com/photos/25024945@N00/8422016762/in/photostream](http://www.flickr.com/photos/25024945@N00/8422016762/in/photostream)

What is on-screen as boot hangs
[http://www.flickr.com/photos/25024945@N00/8422016954/in/photostream](http://www.flickr.com/photos/25024945@N00/8422016954/in/photostream)

After a while the screen populates as follows:
[http://www.flickr.com/photos/25024945@N00/8422017124/in/photostream](http://www.flickr.com/photos/25024945@N00/8422017124/in/photostream)

---

### Post by frank604 on 2013-01-27
Maybe I didn't understand the situation before, I apologize.  So ubuntu is booting up but fails to show login screen yes?

---

### Post by Mark_in_Hollywood on 2013-01-27
NO login screen

---

### Post by frank604 on 2013-01-27
I'm not sure as I'm not experienced with all these errors but I doubt they are barring you from entering the login screen.  My assumption is that it is either 1) video driver issue or 2)xorg or lightdm issue

can you post /var/log/lightdm/lightdm.log ?

---

### Post by Mark_in_Hollywood on 2013-01-27
ubuntu@ubuntu:~$ sudo gedit /var/log/lightdm/lightdm.log


[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.2.1, UID=0 PID=6294
[+0.00s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Starting seat
[+0.00s] DEBUG: Starting new display for automatic login as user ubuntu
[+0.00s] DEBUG: Starting local X display
[+0.01s] DEBUG: Using VT 7
[+0.01s] DEBUG: Activating VT 7
[+0.01s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.01s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.01s] DEBUG: Launching X Server
[+0.01s] DEBUG: Launching process 6307: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.01s] DEBUG: Waiting for ready signal from X server :0
[+0.01s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.01s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.76s] DEBUG: Got signal 10 from process 6307
[+0.76s] DEBUG: Got signal from X server :0
[+0.76s] DEBUG: Connecting to XServer :0
[+0.76s] DEBUG: Automatically logging in user ubuntu
[+0.76s] DEBUG: Started session 6311 with service 'lightdm-autologin', username 'ubuntu'
[+0.80s] DEBUG: Session 6311 authentication complete with return value 0: Success
[+0.80s] DEBUG: Autologin user ubuntu authorized
[+0.89s] DEBUG: Dropping privileges to uid 999
[+0.89s] DEBUG: Restoring privileges
[+0.92s] DEBUG: Dropping privileges to uid 999
[+0.92s] DEBUG: Writing /home/ubuntu/.dmrc
[+0.92s] DEBUG: Restoring privileges
[+0.93s] DEBUG: Starting session ubuntu as user ubuntu
[+0.93s] DEBUG: Session 6311 running command /usr/sbin/lightdm-session gnome-session --session=ubuntu
[+0.96s] DEBUG: New display ready, switching to it
[+0.96s] DEBUG: Activating VT 7
[+0.96s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0

---

### Post by oldfred on 2013-01-27
Screens posted show only partial last shown lines are UPS power configuration error. That I have not seen but last thing shown is not always the issue. Almost always the video issue failure last posted task is battery state.

Do you have a UPS? And a driver for that?

Also have you looks in Disk Utility from liveCD and click on drive. On right side what does Smart Data show. Green is good and that is about all I know.

I was hoping we booted to command line so we did not have to do a full chroot.

I think Boot-Repair has a helper to chroot, but have never used it.

Otherwise. I like kansasnoobs version as he has added all the lines together into one line to copy & paste. But device /dev/sda3 has to be yours and if it does not work you then have to do the line by line version.
       o chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

    
then once chrooted.

None of my normal updates may work if no space so you need to houseclean first and just deleting does not make space, but you have to empty trash.
       HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does as upgrade only does existing packages, this adds new 
sudo apt-get dist-upgrade  #updates dependancies

            # remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

            
Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# kernels 
dpkg --list | grep linux-image

    
       cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version] linux-image-[version]
sudo apt-get purge linux-image-x.x.x.x-generic 
# example use all the one's listed that are not current in ls command.
sudo apt-get purge linux-image-3.2.0-29-generic 

    

        How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

            rm -rf ~/.local/share/Trash/*
# or
rm -ri so that it prompts for each file deletion.

    Normal updates in chroot:
#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
 #Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a

---

### Post by frank604 on 2013-01-27
is there no more? it seems in the log that you have logged in as username ubuntu....

Edit: while xubuntu is booting, can you press CTRL + ALT + F1, login and enter 'startx' ?

---

### Post by Mark_in_Hollywood on 2013-01-27
Reply to Old Fred:

> **oldfred said:**
> Screens posted show only partial last shown lines are UPS power configuration error. That I have not seen but last thing shown is not always the issue. Almost always the video issue failure last posted task is battery state.

Do you have a UPS? And a driver for that?

**Yes, and there is a Linux driver. It shows battery % remaining.** 

Also have you looks in Disk Utility from liveCD and click on drive. On right side what does Smart Data show. Green is good and that is about all I know.

**Disk Utility shows S.M.A.R.T. up and green lighted.** - The only problem that SMART ever showed was about an airflow problem. This device is enterprise (server) grade (1.2 million hours MTBF). Other than that there have been 0 errors with this disk drive.

I was hoping we booted to command line so we did not have to do a full chroot.

I think Boot-Repair has a helper to chroot, but have never used it.

**If it has a helper to chroot, I would load Boot-Repair-Disk and run the below commands from that session?**

Is what is below my line here do-able in LiveCD session? 

Otherwise. I like kansasnoobs version as he has added all the lines together into one line to copy & paste. But device /dev/sda3 has to be yours and if it does not work you then have to do the line by line version.
       o chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

    
then once chrooted.

None of my normal updates may work if no space so you need to houseclean first and just deleting does not make space, but you have to empty trash.
       HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does as upgrade only does existing packages, this adds new 
sudo apt-get dist-upgrade  #updates dependancies

            # remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

            
Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# kernels 
dpkg --list | grep linux-image

    
       cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version] linux-image-[version]
sudo apt-get purge linux-image-x.x.x.x-generic 
# example use all the one's listed that are not current in ls command.
sudo apt-get purge linux-image-3.2.0-29-generic 

    

        How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

            rm -rf ~/.local/share/Trash/*
# or
rm -ri so that it prompts for each file deletion.

    Normal updates in chroot:
#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
 #Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a

---

### Post by Mark_in_Hollywood on 2013-01-27
> **frank604 said:**
> is there no more? it seems in the log that you have logged in as username ubuntu....

Edit: while xubuntu is booting, can you press CTRL + ALT + F1, login and enter 'startx' ?

Its' 4:33 pm as I go to re-boot for CTRL ATL F1

back ASAP

[B]frank604:

At boot time, CTRL+ALT-F1 drops from startup time screen to unix (ascii like) text only. I was then able to enter user name and password and after issuing

startx

was returned to my desktop like screen.

I had no internet connection there and could not place a text file onto a thumbdrive for review here, but that can wait. Also, had to ATL+SysRq R E I S U B K to exit startx, as I could not call the terminal.[/B]

---

### Post by HiImTye on 2013-01-27
how are you chrooting before running update-grub? I noticed that to install the kernel you were doing it properly:
```
sudo mount --bind /dev /mnt/dev
    sudo mount --bind /proc /mnt/proc
    sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```but then later, you only mounted /mnt/boot
```
ubuntu@ubuntu:~$ sudo chroot /mnt/boot
root@ubuntu:/# update-grub
```try this:
```
sudo mount /dev/sdc1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
sudo apt-get install aptitude
while read -r _ p1 p2 _; do
if [ "$p2" = "-" ]; do
 sudo apt-get remove $p1
else
 sudo apt-get remove $p2
done < <(aptitude search ~ilinux-headers-[0-9] ~ilinux-image-[0-9] ~ilinux-image-extra-[0-9])
sudo apt-get install --reinstall linux-generic linux-headers-generic linux-image-generic
sudo apt-get dist-upgrade
sudo update-grub

```if it wants to remove a bunch of metapackages, etc, just hit n<enter>

---

### Post by Mark_in_Hollywood on 2013-01-27
HiImTye

ooopppsss I misunderstood your post. BRB

---

### Post by Mark_in_Hollywood on 2013-01-27
HiImTye

I dunno

ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
mount: mount point /mnt/dev does not exist

---

### Post by HiImTye on 2013-01-27
make sure you change */dev/sdc1* to whatever partition your hard drive is
edit: also, make sure that /mnt actually exists

---

### Post by Mark_in_Hollywood on 2013-01-27
HilmTye


root@ubuntu:/# while read -r _ p1 p2 _; do
> sudo apt-get remove $p1
> else
bash: syntax error near unexpected token `else'
root@ubuntu:/# while read -r _ p1 p2 _; do
> if [ "$p2" = "-" ]; do
bash: syntax error near unexpected token `do'
root@ubuntu:/#  sudo apt-get remove $p1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/# else
bash: syntax error near unexpected token `else'
root@ubuntu:/#  sudo apt-get remove $p2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/# sudo apt-get remove $p1 else
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package else

---

### Post by HiImTye on 2013-01-27
> **Mark_in_Hollywood said:**
> root@ubuntu:/# while read -r _ p1 p2 _; do
> sudo apt-get remove $p1
> else
bash: syntax error near unexpected token `else'
you forgot the IF line
best to paste it into a text file, then give it execute permissions with either:
right click > permissions > check 'allow executing as executable' or w/e
or 
```
chmod +x *filename*
```

or you could just highlight it all, then middle click into the terminal window. it will execute them all in order (you might have to hit enter on the last line)

---

### Post by Mark_in_Hollywood on 2013-01-27
> **HiImTye said:**
> you forgot the IF line
best to paste it into a text file, then give it execute permissions with either:
right click > permissions > check 'allow executing as executable' or w/e
or 
```
chmod +x *filename*
```

or you could just highlight it all, then middle click into the terminal window. it will execute them all in order (you might have to hit enter on the last line)

**I did NOTHING but cut and paste, my friend.**

---

### Post by Mark_in_Hollywood on 2013-01-27
> **HiImTye said:**
> you forgot the IF line
best to paste it into a text file, then give it execute permissions with either:
right click > permissions > check 'allow executing as executable' or w/e
or 
```
chmod +x *filename*
```

or you could just highlight it all, then middle click into the terminal window. it will execute them all in order (you might have to hit enter on the last line)

**I did NOTHING but cut and paste, my friend.**

and now I'm seeing:


ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount --bind /dev/pts /mnt/dev/pts
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
cp: not writing through dangling symlink `/mnt/etc/resolv.conf'
[B]ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
cp: not writing through dangling symlink `/mnt/etc/resolv.conf'[/B]
ubuntu@ubuntu:~$

---

### Post by HiImTye on 2013-01-27
> **Mark_in_Hollywood said:**
> [B]ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
cp: not writing through dangling symlink `/mnt/etc/resolv.conf'[/B]
let's just skip symlink troubles by doing:
```
sudo cat /etc/resolv.conf > /mnt/etc/resolv.conf
```

---

### Post by Mark_in_Hollywood on 2013-01-27
> **HiImTye said:**
> let's just skip symlink troubles by doing:
```
sudo cat /etc/resolv.conf > /mnt/etc/resolv.conf
```

Terminal:

ubuntu@ubuntu:~$ sudo cat /etc/resolv.conf > /mnt/etc/resolv.conf
bash: /mnt/etc/resolv.conf: No such file or directory

If I re-boot could I run that bunch of lines-in-a-box you gave?

---

### Post by HiImTye on 2013-01-27
you're sure you are mounting the correct partition to /mnt ? you should be able to see a bunch of stuff when you
```
ls /mnt/etc/
```

---

### Post by Mark_in_Hollywood on 2013-01-27
> **HiImTye said:**
> you're sure you are mounting the correct partition to /mnt ? you should be able to see a bunch of stuff when you
```
ls /mnt/etc/
```

I'm 100% certain that /sda3 is my / or booting partition while /sda5 is my /home. 

ls /mnt/etc made a list of a few hundred entries.

/sda1 is the 100 meg windows boot partition and /sda2 is the windows 'main' partition for windows of about 70 gig.

---

### Post by HiImTye on 2013-01-27
oh. I'm stupid. I was trying to pipe output to an un-escelated user

```
sudo sh -c 'cat /etc/resolv.conf > /mnt/etc/resolv.conf'
```

---

### Post by Mark_in_Hollywood on 2013-01-27
I did the command via cut & paste

ubuntu@ubuntu:~$ sudo sh -c 'cat /etc/resolv.conf > /mnt/etc/resolv.conf'
sh: 1: cannot create /mnt/etc/resolv.conf: Directory nonexistent

---

### Post by jdthood on 2013-01-28
> **Mark_in_Hollywood said:**
> ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
cp: not writing through dangling symlink `/mnt/etc/resolv.conf'

The error message indicates that the target, /mnt/etc/resolv.conf, is a symbolic link into a path with missing directory parents.

Normally /etc/resolv.conf is a symbolic link with value "../run/resolvconf/resolv.conf". If this link was copied to the chroot then you need to "sudo mkdir -p /mnt/run/resolvconf".

---

### Post by oldfred on 2013-01-28
Do you not have Internet connection? I am not sure the resolve then works as that is to enable the chroot Internet connection. But almost all of the chroot commands I have posted to fully repair your system require Internet connection. Difficult without and I am not 100% sure how without it. LiveCD may not have current versions of files.

You should be able to either chroot or  mount into your install and delete files and then houseclean trash.

---

### Post by Mark_in_Hollywood on 2013-01-28
> **oldfred said:**
> Do you not have Internet connection? I am not sure the resolve then works as that is to enable the chroot Internet connection. But almost all of the chroot commands I have posted to fully repair your system require Internet connection. Difficult without and I am not 100% sure how without it. LiveCD may not have current versions of files.

You should be able to either chroot or  mount into your install and delete files and then houseclean trash.

YES, I have a working internet connection. I ran Kansasnoob's 1-line and here is the terminal output:

ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
**cp: not writing through dangling symlink `/mnt/etc/resolv.conf'**

---

### Post by oldfred on 2013-01-28
Do not know about that error. Do you have a resolve.conf in your /mnt/etc? or in your install?

---

### Post by Mark_in_Hollywood on 2013-01-28
Following JDT Hood:

Re: Root is Nearly Full - in LiveUSB Mode to Delete old Kernels


ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
cp: not writing through dangling symlink `/mnt/etc/resolv.conf'
The error message indicates that the target, /mnt/etc/resolv.conf, is a symbolic link into a path with missing directory parents.

Normally /etc/resolv.conf is a symbolic link with value "../run/resolvconf/resolv.conf". If this link was copied to the chroot then you need to **"sudo mkdir -p /mnt/run/resolvconf".**

resolved this dangling dangthing. Thanks.

---

### Post by Mark_in_Hollywood on 2013-01-28
As of:

6:38 PM
Monday, January 28, 2013 (UTC)


My operating system, the video and grub screen are working. I'm marking this post as SOLVED.

I am too poor a writer to have words to properly express my gratitude for the support of everyone who helped me here. 

Never the less, thank you. Thank you all very much.

---

