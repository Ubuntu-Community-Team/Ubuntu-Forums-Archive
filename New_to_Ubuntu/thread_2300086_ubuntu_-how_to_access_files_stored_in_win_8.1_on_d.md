---
title: "ubuntu -how to access files stored in win 8.1 on drive F:"
date: 2015-10-23
forum: New to Ubuntu
---

### Post by squibbs2 on 2015-10-23
I am a real newbie!!  I have just dual booted Ubuntu 15.04 with Win 8.1.  Under windosw I have stored all my data, music, photos and Thunderbird on Drive F:.  Is there a simple way that I can access all these files in both Ubuntu and Windows?  I've tried searching for an answer but have been confused by the methods shown.

---

### Post by oldfred on 2015-10-23
Windows does not let you unmount a partition. And Windows 8 and later have fast start up which is always on hibernation. So all partitions are hibernated.
You can force read only when hibernated, but would corrupt or lose data if you force read/write use when hibernated so the Linux NTFS driver will not mount hibernated or NTFS needing chkdsk to prevent damage.

       Fast Startup off/hibernation - Windows 8 or 10 UEFI or BIOS boot.
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

If internal drive, best to permanently mount with fstab.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

      
 For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

### Post by SeijiSensei on 2015-10-23
Every time I read something like this, my resolve to stick with Windows 7 stiffens.

---

### Post by col48 on 2015-10-23
@oldfred

So are you saying that even if you choose to boot into Linux (out of your dual boot choices) Windows has somehow still got hold of the partitions to some degree?

What if the drive is a removable drive?

Or a remote one on a server accessed by other machines (which may be a mixture of OS)?

(Don't spend too long on a reply - I'm just curious)

---

### Post by oldfred on 2015-10-23
I do not know about remote.

But have seen others with a separate drive and NTFS partition from a newer Windows and partition is still locked or hibernated. But may not have been a removable drive.

Not sure if it applies to removable drives or not.  You can try it an see. I do not have Windows and a removable drive to test it with.

---

### Post by Geoffrey_Arndt on 2015-10-24
Hmm, I only have two dual-boots, and both are Windows 7 and Ubuntu Unity and Ubuntu Mate.   No such issues there.    But IF you're dual booting and only starting Ubuntu (in other words, Windows is not running in any session), then are not the partitions and/or separate drives (sdb, sdc, etc.) available via standard Nautilus or other Linux file managers?   In other words, Windows can't hibernate if not started . . . Linux will see/read partition table for that scenario yes/no?    Will Win 8, 10 run without issues if hibernation disabled persistently?

---

### Post by mcduck on 2015-10-24
> **Geoffrey_Arndt said:**
> Hmm, I only have two dual-boots, and both are Windows 7 and Ubuntu Unity and Ubuntu Mate.   No such issues there.    But IF you're dual booting and only starting Ubuntu (in other words, Windows is not running in any session), then are not the partitions and/or separate drives (sdb, sdc, etc.) available via standard Nautilus or other Linux file managers?   In other words, Windows can't hibernate if not started . . . Linux will see/read partition table for that scenario yes/no?    Will Win 8, 10 run without issues if hibernation disabled persistently?

If you have ever started the Windows on that computer (and you have fastboot enabled) the result is same as if you were hibernating. Basically Windows from 8.1 onwards doesn't really fully shut down, but instead uses kind of a hybrid mode where parts of the running OS are stored on the hard drive like they would be when you hibernate the machine. Because of this, it doesn't fully sync disk writes, unmount the hard drive  mark it as clean. And this prevents Linux (or any other OS) from safely mounting it.

You *can* still safely mount the drive manually if you do it in read-only mode, but apart from that the only option is to disable fastboot in Windows. Which of course will make Windows boot slower as it'll have to go through full boot process.

Removable drives are of course unmounted normally by Windows, as long as you actually remove them before shutting Windows down. So those shouldn't have any issues.

What comes to network drives, that's completely different question, as Ubuntu (or whatever OS is accessing the drive through network) is not directly controlling the drive, as it's handled by the OS running on the server, NAS or whatever system the physical drive is actually installed in. Yor computer doesn't even need to understand or know what filesystem the server r NAS is using, as you only get access to the drive through the server OS, using SMB/CIFS or NFS or some other network file sharing protocol.

---

