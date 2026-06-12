---
title: "Boot Repair broken? No advanced options, means it is incapable of doing anything?"
date: 2014-02-28
forum: New to Ubuntu
---

### Post by emugod on 2014-02-28
I'm not sure if I'm understanding it right, but what options you see in Advanced Options for Boot Repair, are really all it is capable of? And so, it's really not doing anything for me (which is what it seems like, certainly not seeming to resolve any of my problems)? I've only ever tried running it from Recommended Repair, and have two of its reports to show for anyone capable of reading them. I'm not sure if it's normal behavior or not, but every time I open it it warns to backup data 'before this operation', and on closing gives a message 'operation aborted' (is there some errant operation prescheduled?).
[http://paste.ubuntu.com/7000454/](http://paste.ubuntu.com/7000454/) 
[http://paste.ubuntu.com/7006262/](http://paste.ubuntu.com/7006262/)

[ATTACH=CONFIG]250765[/ATTACH][ATTACH=CONFIG]250764[/ATTACH][ATTACH=CONFIG]250766[/ATTACH]
This is what my advanced options looks like. All the three greyed-out midle tabs are simply empty, leaving the only option (aside from the report creation options) of file system repair, nothing to do with boot.

Much older, earlier threads, from when I originally tried installing Ubuntu last year, which may or may not be of help. I gave up on it after that failure, afraid to keep trying and perhaps eventually damage my primary WIndows 8 installation, but in the meantime that installation has degraded to the point of near uselessnes so I am back. I'd still like to keep it if possible, just as a backup (it still does web browsing, if not much else).
[http://ubuntuforums.org/showthread.php?t=2121889](http://ubuntuforums.org/showthread.php?t=2121889)
[http://ubuntuforums.org/showthread.php?t=2121279](http://ubuntuforums.org/showthread.php?t=2121279)

The specific errors I can identify today; 
Two 'phantom' Ubuntu EFI entries left over from past installation attempts.
Ubuntu Installer (currently posting this from the Ubuntu liveUSB, which runs just fine) fails at stage of installing EFI entry and/or GRUB.
Extremely distorted GRUB boot menu graphics, possibly just plain corrupt GRUB. I wish I could screencap this somehow, it's a very strange thing, still clearly identifiable as a menu with three options, and even which option is currently selected, but absolutely no hope of reading any of the text. Not sure if this is a sign of actual corruption or just a harmless display bug.

Thanks in advance for any help.

edit: Had the thought that perhaps the spotty internet connection had effected the Boot Repair install, as I suspected it might have been what was  preventing succesfull Ubuntu install. Redownloaded and reinstalled it with no change. Also decided to give the Ubuntu installer one more try, but quickly aborted after it now no longer even recognizes the presence of a Windows installation. No idea what could have caused that. Ran boot repair again, just because, and now I'm pretty certain it is in fact not attempting anything but the file system repair, as indicated in advanced options. new report: [http://paste.ubuntu.com/7011446/](http://paste.ubuntu.com/7011446/) Tried Ubuntu installer again, it still no longer even detects Windows (I had hoped it might just be a weird 'mounting' thing, that might be fixed as a side ffect of Boot Repair unmounting and remounting everything for the file system repair, but apparently not).

---

### Post by whitesmith on 2014-02-28
This ([http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)) is what you should see.  If items are missing try redownloading and reburning the CD.  Since you say you've done this already, check CRCs. From your description, it sounds like you may have a hardware issue with your system, so get your third go-round copy from another computer, preferably with separate net connectivity. Advanced options are definitely on my copy. If they are missing on yours, you're looking at a (hopefully correctable) problem. Cheers.

---

### Post by emugod on 2014-02-28
> **whitesmith said:**
> This ([http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)) is what you should see.  If items are missing try redownloading and reburning the CD.  Since you say you've done this already, check CRCs. From your description, it sounds like you may have a hardware issue with your system, so get your third go-round copy from another computer, preferably with separate net connectivity. Advanced options are definitely on my copy. If they are missing on yours, you're looking at a (hopefully correctable) problem. Cheers.

Do you happen to know specifically which file or files I should check, and which command(s)? I must confess I'm not even really sure what an application (like Boot Repair) is actually composed of, in terms of files on the disk, in Linux. If it helps, I installed it following the instructions of [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) (copy-pasting those commands), on 1 12.04 liveUSB.

I've noticed another strange thing, not sure if it could be a potential cause of any problems or if it is a problem itself (I don't really think so), but still something I'd like to come to understand.
[ATTACH=CONFIG]250775[/ATTACH]
Drives are inaccessible because they're already secretly mounted, in hidden folders? Again, the concept of having to actively 'mount' connected drives is very new to me coming from Windows, is this normal? Is it just an efficiency/quirk of the liveUSB environment? It seems strange to have an entire drive inside a logical folder.

---

### Post by whitesmith on 2014-02-28
> **emugod said:**
> **[1]** Do you happen to know specifically which file or files I should check, and which command(s)? I must confess I'm not even really sure what an application (like Boot Repair) is actually composed of, in terms of files on the disk, in Linux. If it helps, I installed it following the instructions of [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) (copy-pasting those commands), on 1 12.04 liveUSB.

**[2]**I've noticed another strange thing, not sure if it could be a potential cause of any problems or if it is a problem itself (I don't really think so), but still something I'd like to come to understand.
[ATTACH=CONFIG]250775[/ATTACH]
Drives are inaccessible because they're already secretly mounted, in hidden folders? Again, the concept of having to actively 'mount' connected drives is very new to me coming from Windows, is this normal? Is it just an efficiency/quirk of the liveUSB environment? It seems strange to have an entire drive inside a logical folder.

[1] I have no idea.
[2] If your problem drive is seen by Ubuntu as removable, the OS mounts it for you. Do you have an explicit entry in /etc/fstab to mount it? If so, that might explain what you see. Linux is quite different from Windows in that it sees everything as a file. A folder (directory in *nix speak) can be inside another because the directory is just a file, even if a hard drive is mounted there. Yes, it can be confusing but the concept is powerful, partly because of its extensibility. Mount points can look very strange to someone with a Windows background. In fact I would argue that the more robust your Windows strengths, the more challenging Linux will be (see ref. 1 in my sig line). Unlike Windows, every drive in Linux must be mounted before it can be accessed. Mounting sounds strange but it's just a way of telling the OS that you want access to a particular filesystem under **the** root (/). Windows treats all drives as equal (**no supreme root /**) at the inverted base of the tree, making mount unnecessary. Perhaps someone with a stronger theoretical background could explain it more elegantly.

The boot repair tool warns about backing up data because it could, in principle, destroy it. Linux provides backup tools by the dozen. You might look at clonezilla before proceeding. Once you have a solid backup proceed with repairing -- but not before. I speak from experience. Oh, boy, do I ever!

---

### Post by oldfred on 2014-03-01
I think because Boot-Repair is having issues mounting partitions, it is not offering other repair options.
Have you already mounted all the partitions and then running Boot-Repair from your installed system. 
Better to try to run from a new reboot from a live USB Ubuntu installer or the Boot-Repair liveCD.

You have an UEFI install. Was Windows installed in UEFI boot mode? Windows 7 defaults to BIOS boot mode if you use DVD to install it, but can install in UEFI mode from a modfied flash drive.

---

