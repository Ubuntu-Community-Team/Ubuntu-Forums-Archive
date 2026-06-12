---
title: "problems booting up - wubi"
date: 2013-04-09
forum: New to Ubuntu
---

### Post by lblsam on 2013-04-09
Hi,

I've got a laptop with both Windows 7 and Ubuntu 12.0 on it. I normally work in ubuntu, which is where all my work is stored. Today when I tried to open it all i got was a screen with this message:

"GNU Grub version 1.99-21ubuntu3.4

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>"

I've been trying to work out how to fix it and ran a boot repair using a Live USB. It gave me this url: [http://paste.ubuntu.com/5692690/](http://paste.ubuntu.com/5692690/) it didn't fix the problem though.

now i don't even seem to be able to get it to load using the usb.....

Any ideas? I'm now in a panic that I've lost all my work from the last four months (the computer is only 4 months old...)

thanks

Sam

---

### Post by oldfred on 2013-04-09
Edited title to include wubi. Which I know little about and only a few here really know.

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

    
Wubi uses the Windows boot loader and is just a file (root.disk) inside the NTFS Windows partition. So Windows issues will also prevent wubi from working. 

Script is not showing root.disk in your Windows but it may be there?

       Missing root.disk
[http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)
[http://askubuntu.com/questions/228709/ubuntu-12-04-wubi-not-starting-root-disk-corrupted](http://askubuntu.com/questions/228709/ubuntu-12-04-wubi-not-starting-root-disk-corrupted)

   How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)

---

### Post by lblsam on 2013-04-09
thanks, for some reason the live USB I created is no longer working. It goes to ubuntu but it simply doesn't load. Do I just need to create another one?

---

### Post by oldfred on 2013-04-09
You will need a liveCD/DVD/Flash and all the new versions are oversize and do not fit on CDs. I prefer flash drives.

       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[URL="https://help.ubuntu.com/community/Installation/FromUSBStick"]https://help.ubuntu.com/community/Installation/FromUSBStick

[/URL] 
Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

[URL="https://help.ubuntu.com/community/Installation/FromUSBStick"]
[/URL]

---

### Post by lblsam on 2013-04-09
thanks for all the info. It seems my root.disk is there, but it has been wiped (at least it is showing 0kb as the file size). I'm on to trying the recovering files one.... if this doesn't work and I reinstall ubuntu, will it wipe all my files?

---

### Post by oldfred on 2013-04-09
If you reinstall wubi, you will not have the old root.disk to go back to, so yes all you files will be gone. You can backup a working root.disk, reinstall if that is the issue and restore the root.disk to have old data. But you have to have made the back up first. 

New versions only install from inside Windows, not from liveCD/DVD/Flash.

If you find you like Ubuntu, it may be time to think about a full partitioned install.
 From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by lblsam on 2013-04-09
Yes, I understand there is basically no hope now.  I've used Ubuntu for years at home, but at work they only allowed me to use on their laptop it if I kept Windows as well. To be honest, I just did the install from Windows, I had no idea that there wasn't a full partition, or even what that means and this is the first time I've heard of Wubi. I suspect Ubuntu will now be banned from office computers (even though from what I can tell it was a Window's issue?) but just in case, what does it mean to do a full partition and how do you do it? 

And thanks again for all your help.

---

### Post by bcbc on 2013-04-09
I don't recommend running boot-repair with Wubi. Very often the reason for Wubi failing is that there is NTFS corruption - and the best approach to solving this is to run chkdsk /f from Windows. Unfortunately boot-repair will fsck the root.disk if it fails to mount it without considering this - and although I don't have definitive evidence - I've seen the 0KB root.disk in these circumstances.

The virtual disk Wubi uses is a virtual ext3 or ext4 file system contained within a file (root.disk) that sits on top of the NTFS file system. You can imagine that if the NTFS system is corrupted, and you try to repair the ext4 system that there could be some issues.

While I've mentioned this risk a number of times to the developer, boot-repair still does this. My suggestion is for boot-repair to ignore Wubi installs or to recommend running chkdsk instead of fsck'ing, or to get confirmation of chkdsk having run prior to fsck'ing.

But ideally Wubi users would maintain fully-synchronized data backups as it's recommended more to try Ubuntu rathern than a production system. And while some users never experience problems, there are continual reports of root.disk corruption.

If the root.disk is 0KB then apart from tools like photorec, I don't know of any way to recover this. But needless to say reinstalling will likely reuse some of the space from the previous root.disk and overwrite it making recovery impossible. So don't reinstall until you have exhausted your recovery options. I am not aware of photorec being successful in this case, but the absence of confirmation doesn't indicate that it's not possible.

---

### Post by oldfred on 2013-04-09
If a work computer I would not suggest repartitioning and installing Ubuntu unless you get specific approval.

Another alternative.
 HOW TO Avoid Wubi & Install Ubuntu on USB Drive -
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

I have a full install in my 16GB flash drive with 8GB for / (root) and 8GB for data. I do not use it a lot but keep it as an emergency boot drive, more for my laptop which only has one drive.
      
 Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by lblsam on 2013-04-10
thanks again to both of you for all your help. My impression is that it would take a long time to try to recover any files and most of the really important ones are contained in a dropbox or on email so I guess I will leave it at that. If I do get round to running a phorec or similar and it works I'll let you know. It would be great if the wubi or boot repair folks could include a warning re using boot repair to fix Wubi problems (with some info on how to recognise it is a wubi problem) as there was no mention that running it could make some problems worse and most of the responses to fixing unbuntu boot problems on a dual computer recommended this. But not sure how I can go about requesting this.....

I'll mark this "solved" for now though.

---

### Post by bcbc on 2013-04-10
> **lblsam said:**
> thanks again to both of you for all your help. My impression is that it would take a long time to try to recover any files and most of the really important ones are contained in a dropbox or on email so I guess I will leave it at that. If I do get round to running a phorec or similar and it works I'll let you know. It would be great if the wubi or boot repair folks could include a warning re using boot repair to fix Wubi problems (with some info on how to recognise it is a wubi problem) as there was no mention that running it could make some problems worse and most of the responses to fixing unbuntu boot problems on a dual computer recommended this. But not sure how I can go about requesting this.....

I'll mark this "solved" for now though.
I'm glad you had some backups.

Regarding boot-repair, this is maintained separately. You can file a bug on it here: [https://bugs.launchpad.net/boot-repair/+filebug](https://bugs.launchpad.net/boot-repair/+filebug)
You can file a bug on Wubi but it tends to have little development focus and right now it looks like it will no longer be supported from release 13.04. I have already added a bug regarding the root.disk corruption here: [https://bugs.launchpad.net/wubi/+bug/1078959](https://bugs.launchpad.net/wubi/+bug/1078959)

If there was some community maintained documentation that you read that led you to think it would fix your Wubi install, feel free to edit it and add a warning about needing to run chkdsk first. There is no special requirement to editing community documentation other than you follow the community code of conduct. There are some things boot-repair does very well, but it doesn't fix every error - it's mostly for the common Grub related errors on dual boots.

---

