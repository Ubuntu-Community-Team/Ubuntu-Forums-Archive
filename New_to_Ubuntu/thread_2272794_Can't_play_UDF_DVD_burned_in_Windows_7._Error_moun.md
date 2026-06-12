---
title: "Can't play UDF DVD burned in Windows 7. Error mounting."
date: 2015-04-08
forum: New to Ubuntu
---

### Post by benawhile on 2015-04-08
I am trying to play a DVD on my system, it was burned in Windows 7 and given to me.
 I was told that the file system used was .mp4
 I get this error:
 

 Unable to mount UDF Volume
 

 Error mounting /dev/sr0 at /media/ben/UDF Volume: Command-line `mount -t "udf" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,umask=0077" "/dev/sr0" "/media/ben/UDF Volume"' exited with non-zero exit status 32: mount: block device /dev/sr0 is write-protected, mounting read-only 
 mount: /dev/sr0: can't read superblock 
 

 I have installed udf package
 sudo apt-get install libudf0
 according to a forum post relevant to karmic but that made no difference.

---

### Post by sudodus on 2015-04-08
I have not much experience of the UDF file system. But if I remember correctly, I flashed an OpenSuse iso file with UDF into a USB pendrive. I could not only read the file system, I could also boot computers from it.

So try by extracting everything from the DVD disk to a file and loop mount it, or maybe easier to a USB pendrive. You can do that with dd, but it is risky. It will be safer, and probably also easier to do it with mkusb 9.1.5, that you get from the 'unstable' PPA (the bleeding edge version).

```

sudo add-apt-repository ppa:mkusb/unstable
sudo apt-get update
sudo apt-get install mkusb

```

See this link [https://help.ubuntu.com/community/mkusb/v9#Installation](https://help.ubuntu.com/community/mkusb/v9#Installation)

---

### Post by benawhile on 2015-04-09
Thank you for replying. I am in deep water here.
First of all, I can't read the DVD disk at all, The full story is that a friend took a video of a birthday party with a video camera and burned the resulting video to a DVD, using windows 8, and gave it to me.This DVD was burned as a standard video .mp4 to play on a DVD player or a pc, and neither my XP systems nor Ubuntu 14.04 nor Lubuntu ould read it.  My own Ubuntu "Videos" program saw that it was an mp4 file, and detected the title and size, 3GB, but could not play it. The XP saw just an empty disc, and so did another friend&#8217;s Windows 7  sytem, (and that eventually proceeded to start to format it, rendering  it useless!)
 So the first guy had another try, and this time just created a 2nd DVD as a data disc with the .mp4 file on it. But XP didn't see that either, even after I downloaded the .mp4 codec, and in Ubuntu I get the mounting problems above. 
The other problem is that I do not have regular access to a Windows 7 or 8 system but I can try my g/f's Windows 7 system at the weekend. All this may explain why i seem to be doing all this fault finding in a roundabout way. The friend tested the DVD after burning on a Windows 7 and an 8 system so presumably I have a "known worker", but not in a sytem I have access to.

So to your suggestions: 
As I can't read the disk I don't see how I can extract anything from it myself. Can I do anything with it without mounting it, and how? As soon as I insert it I get the mounting error.
I do not understand what mkusb is and where that comes in to the picture, and am not familiar with the terms "loop" and "Bleeding edge".
 I am on a slow learnign curve. 3 years ago I cracked how to install a dual boot system, and modify fstab to get a shared partition to mount on boot up, but have missed loads of other important stuff on the way!

---

### Post by sudodus on 2015-04-09
I see your problem, and I see some alternatives:

1. Bring a USB pendrive to your friend and copy the mp4 file to the pendrive. That way you should be able to transfer it to your computer.

2. An alternative is that your friend uploads the mp4 file to a cloud service, for example Google Drive, which is free, and can host up to 15 GB. Then he 'shares the file' and give you the address to it, so that you can download it. I have shared video clips of my daughter's orchestra's concerts like that.

3. Try the DVD in your girl-friend's computer.

4. Try mkusb. It need not mount the DVD, but Ubuntu must be able to see it as a block device. The output (described in your opening post)

'block device /dev/sr0 is write-protected, mounting read-only'

indicates, that Ubuntu can see it as a block device (even mounting it), so mkusb should be able to clone it to a USB pendrive.

5. Try again to read the mp4 file from the DVD. If it is a data DVD, it should work. The output (described in your opening post)

'block device /dev/sr0 is write-protected, mounting read-only'

indicates, that Ubuntu mounts it read-only, which is enough to read it. So use the file browser and search for it. The command

```
df
```

will indicate where to look for the mp4 file (where /dev/sr0 is mounted). I got the **[COLOR=#006400]following output[/COLOR]** for a CD with pictures

```
$ df
Filsystem       1K-block    Använt Tillgängligt Anv% Monterat på
/dev/sdb5       53527044  27734080     23073940  55% /
udev             2052756        12      2052744   1% /dev
tmpfs             412728      1124       411604   1% /run
none                5120         0         5120   0% /run/lock
none             2063636       188      2063448   1% /run/shm
cgroup           2063636         0      2063636   0% /sys/fs/cgroup
/dev/sdc7      880870988 422543008    413582304  51% /media/multimed-2
[COLOR=#006400]/dev/sr0          704092    704092            0 100% **/media/p0002-0500**[/COLOR]
```

If it is a movie DVD (to be played in a DVD player) you need special non-free software to play it. I think you get it when you install a meta-package with the following command

```
sudo apt-get install ubuntu-restricted-extras
```

The software to decode the mp4 file comes with that meta-package too.

---

### Post by benawhile on 2015-04-09
I tried df but didn't get anything in the list for /dev/sr0, even though the error message, and also the command sudo mount -t udf /dev/sr0 /mnt says that it is mounted as read only. Could the last line in the error message, (and also by the way, the result of sudo mount -t udf /dev/sr0 /mnt,) :
"mount: /dev/sr0: **can't read superblock **"
 be significant? I wonder if my DVD reader is faulty, It is a 13 years old samsung SM 308B CD RW DVD. But It reads CDs fine. It is definitely supposed to read DVD-R, which is what this DVD is. It is not a DVD RW.

I will try a usb stick as you suggest. I have less trouble with usbs than with CDs.
What is the difference between a usb stick and a pen drive? And what is the advantage of mkusb over simply copying the .mp4 files to a stick?

I already have the ubuntu-restricted-extras

---

### Post by mc4man on 2015-04-09
There was a time in the past (vista?) where windows offered a bunch of methods to burn to dvd, at least one would cause an issue then with linux (udf 2.x, I forget the x
(- support for udf 2.x isn't an issue any more
In any event now Win 8 only has 2 options in it's burn program. The default is a 'live fs' that likely would be an issue in other Os's - the disk isn't finalized. It's descripted as 'like an usb'
The other option is a data disk, it uses udf 1.02 & should be fine virtually anywhere. So your 2nd disk should be ok, it may be more a matter of player support for the file type encoding. (codec

In windows I'd just use ImgBurn instead of windows built-in, then never an issue. But I did burn some h.264 mp4's to dvd in win 8 with it's program & the disk is fine in Ubuntu.

(- are you sure it's not that you're using Ubuntu on llvmpipe that's causing latest problem??

---

### Post by benawhile on 2015-04-09
I have been having problems with slow graphics since going from 12.04 to 14.04  but I never understood exactly why. Could you explain more and offer a suggestion? Could I put a better graphics card into a spare slot?

On the XP boot I installed the .mp4 codec for wmp but it seemed to make no difference. Didn't even see the disc in the drive.

---

### Post by sudodus on 2015-04-09
I suggest that you give up DVD and try the other alternatives suggested in post #4.

*mc4man*'s tips are worth considering.

In order to consider a new graphics card, we need to know more about the computer. Then we can discuss what alternatives that are feasible. Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

*Edit*:
1. USB stick alias pendrive alias flash drive alias thumb[drive]
2. If you can't mount the file system on the DVD, you can't copy a file in it. Otherwise, yes, that would work. I thought that it might work with mkusb even if you can't mount the file system. But if you can't read anything from the DVD (not even the raw data), mkusb won't help you.

---

### Post by benawhile on 2015-04-09
It's a home build made in 2007.  Most info is in my signature, hope it's not too condensed. 1.8 GB RAM. Graphics is VIA. No wifi. Have I missed anything? HDD is samsung SP0802N from previous PC. Only 80GB but I manage!

With regard to the graphics I have seen some posts here about using different drivers. Intel maybe? Looked complicated and may not have applied to me but I am for giving it a go with help.

---

### Post by Vladlenin5000 on 2015-04-09
Does the *openchrome* driver still works (in any post-2012 release)? That's the one you should be using (if it works) but you aren't, hence the *llvmpipe* (yes, obviously slow).

Well, suddenly the thought of a new graphics card seems a brilliant idea, considering anything you can trow in a PCIe x16 is way better than the VIA integrated graphics. Even the cheapest you can find is probably HD capable and has DVI/HDMI/DP ports.

---

### Post by sudodus on 2015-04-09
I think it can be difficult with VIA graphics and Ubuntu version 14.04 LTS. You might have better luck with 12.04 LTS, either a community re-spin like LXLE or *kansasnoob*'s [https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

-o-

In another current thread, Slax 6 works well with old VIA graphics. See this thread: [split Ubuntu installation HDD/USB]("http://ubuntuforums.org/showthread.php?t=2272777")

-o-

Maybe you are helped by the tip in the following link: [https://askubuntu.com/questions/183305/graphics-driver-being-reported-as-gallium-0-4-on-llvmpipe-llvm-0x300-instead-o](https://askubuntu.com/questions/183305/graphics-driver-being-reported-as-gallium-0-4-on-llvmpipe-llvm-0x300-instead-o)

but use ```
gksudo gedit
``` (do not use plain sudo with graphical application programs, it might cause permission problems with configuration files in your home directory). ***Backup*** you system before doing it, because you might get more problems: I'm not at all sure that it will work better with the VIA graphics.

---

### Post by sudodus on 2015-04-09
> **Vladlenin5000 said:**
> Does the *openchrome* driver still works (in any post-2012 release)? That's the one you should be using (if it works) but you aren't, hence the *llvmpipe* (yes, obviously slow).

Well, suddenly the thought of a new graphics card seems a brilliant idea, considering anything you can trow in a PCIe x16 is way better than the VIA integrated graphics. Even the cheapest you can find is probably HD capable and has DVI/HDMI/DP ports.

+1

I prefer nvidia cards, other people prefer ATI/AMD/Radeon. Before you buy anything, check what works well with linux. You can ask here or even better in a new thread in the [Hardware]("http://ubuntuforums.org/forumdisplay.php?f=332") forum.

---

### Post by benawhile on 2015-04-09
OK all food for thought and thank you all

---

