---
title: "Repair windows vista (tried using boot repair"
date: 2013-09-24
forum: New to Ubuntu
---

### Post by lolful64 on 2013-09-24
[http://answers.yahoo.com/question/index?qid=20130923121728AA8olMH](http://answers.yahoo.com/question/index?qid=20130923121728AA8olMH)
I asked a question there but if you can be bothered to click on it this is what I basically asked

> When I turn on my computer it shows all the os's I can use to open my pc. I have windows vista and ubuntu BTW. 

Any ways trying to open windows sends the pc back to the "turn on screen" that I see after turning on my pc. I can use ubuntu perfectly fine but windows is in a endless boot sequence. I know that ubuntu can't be the problem because I installed that ages before this problem occured. 

How can I fix this? (bearing in mind all I have to work with is a computer that can only run ubuntu, no other access to another pc, spare rewritable disks each with only 700MB (totalling 15.72GB), two 14GB usb sticks and practically no knowledge how to do almost anything to do with disk burning etc. 

A user sent me to [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). I followed the instructions and instead of fixing my windows os it messed up ubuntu. Trying to open ubuntu gave a error (didn't get given a code or anything, just said error). After my 10 minute heart attack it started up again by some miracle. I remembered it said to keep a paste code or something like that and post on forum if you have a issue. ([http://paste.ubuntu.com/6150751/](http://paste.ubuntu.com/6150751/))

Now what? (I really suck at ubuntu, don't overcomplicate things for me. My brain was already frying just trying to wrap my head around the simple intructions of boot repair >_>)

Edit-Booting ubuntu shows the following error "errors were found while checking the disk drive for /"

---

### Post by Jonathan Precise on 2013-09-24
Boot ubuntu live CD. Run:

```
fsck
```

Wait...

Post any errors with [noparse]```

```[/noparse] tags.

---

### Post by lolful64 on 2013-09-24
I used the code you told me to. Nothing has been fixed. Now when I try to open my usb/sd/EVERYTHING it says

```
Error creating mount point `/media/martin/TDK': Read-only file system (udisks-error-quark, 0)
```

Now what?

---

### Post by Mark Phelps on 2013-09-24
I'm presuming you do NOT have Vista install or repair media because, if you did, you would have used it already -- and mentioned that.

If you're willing to spend a little money, and have access to a PC that can burn a CD, visit the linked site, download and burn the image of the appropriate Vista version: [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

Then, boot your PC from it and run startup repair three times -- that's right, three times.

---

### Post by oldfred on 2013-09-24
It looks like you have a wubi install. That is just a file inside the Windows NTFS partition and uses the Windows boot loader.
You may get two menus. First is the Vista menu with Windows & Ubuntu, then grub which may show a menu but is more just to be like a full install and cannot boot Windows.

When first starting to boot Windows, can you press f8 and get into a Vista repair console?

---

### Post by lolful64 on 2013-09-25
nope tried to enter startup repair and the computer fully ignores me >_>

---

### Post by oldfred on 2013-09-25
Most Windows issues cannot be fixed from Linux, you will need Windows repair tools. You can buy the version you need using link in Mark Phelps post above.

If you have access to another Windows Vista system that is the same 64 bit or 32 bit as yours any version of Vista then you can make your own repairCD or flash drive.

       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by lolful64 on 2013-09-25
Ok then, assuming I now have a legit copy of windows vista as a iso What instructions/steps would I need to follow to get the iso burned to my usb and make sure it is bootable. When I use "disks" on ubuntu (or what it calls itself) it has a "bootable" option when I format the usb. Will that work?

My mounting issue is getting very unusual and its starting to scare me. I used ```
[FONT=Ubuntu Mono]sudo fsck -Af -M[/FONT]
``` and it no longer showed me a ```
Errors were found while checking the disk drive for /
``` when I started my pc up. But here's the weird part. All usb/sd I own mount fine then when I open my pictures folder I notice my photos have the read only padlock on it. It turns read only all over again >_>. What the heck is going on with my pc?

---

### Post by oldfred on 2013-09-25
Is this still wubi. 
You may need to run chkdsk in Windows.

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by lolful64 on 2013-09-26
I had to use wubi, my computer wouldn't burn disks for a weird reason (not that I would anything exceptional about it if it would work)

And what is up with ```
fsck
``` I've used it twice over now and the message ```
"errors were found while checking the disk drive for /"
``` is still bugging me. Will only windows repair tools fix this?

---

### Post by oldfred on 2013-09-26
You cannot run fsck on the Linux file directly. 
You first need to run chkdsk in Windows.

Then from Ubuntu liveCD or flash drive have to mount the NTFS partition, then loop mount the wubi file and then run fsck on that. If you are trying to run  fsck on NTFS that will not work.

       How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)
[Script] Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu


 [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

---

### Post by lolful64 on 2013-10-01
My pc is in a read only file system I can't download or use practically anything. The only choice I have is to try and make a bootable usb from only using ubuntu >_>

---

### Post by oldfred on 2013-10-01
New versions are too large for CD, but instructions for DVD are the same.

 Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

---

### Post by lolful64 on 2013-10-02
I should close this little thread I fixed my pc by some miracle and now Im settling for using ubuntu from my usb to stop problems but thanks for trying :D

---

### Post by oldfred on 2013-10-02
Whatever works. :)

I would still make a Windows repair CD or flash drive.

---

### Post by Bucky Ball on 2013-10-02
Please mark thread as solved from thread tools at top right of page. Thanks.

---

