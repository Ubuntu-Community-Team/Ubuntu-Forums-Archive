---
title: "Show drive letters?"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by FlindoJimbori on 2012-07-25
Is there a way to show the drive letters in nautilus or whatever the default file explorer is. for example... I want my hard drive to say C: and my flash drive to say D:  please help.

---

### Post by Paqman on 2012-07-25
Drive letters are a Windows thing, they aren't used in Linux.

Instead we talk about mount points. For example, the partition that Windows calls C: could be mounted to your Linux filesystem as something like /host or /media/Windows. This is pretty much infinitely flexible, you can assign any chunk of actual storage to any location in the filesystem you want. For example, Windows might insist on calling your external drive F:, but in Linux you might decide that you want to have it mount to a location called /my_external_drive or /I_Like_Bananas. The default for removable storage like your flash drive is to get given an automatically assigned mount point in /media.

If you really want it to look like it's using drive letters I suppose you could create a folder called /C and have that partition mount there.

---

### Post by Bufeu on 2012-07-25
Linux doesn't **have** drive letters. You can find every external drive (such as USB, Floppy, HDD) under */media*.
[http://peter.upfold.org.uk/blog/2006/07/18/a-guide-to-files-and-folders-on-linux/](http://peter.upfold.org.uk/blog/2006/07/18/a-guide-to-files-and-folders-on-linux/)
[http://grokdoc.net/index.php/Linux_concepts#Drive_letters](http://grokdoc.net/index.php/Linux_concepts#Drive_letters)
[http://linuxconfig.org/Filesystem_Basics](http://linuxconfig.org/Filesystem_Basics)
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html)
[http://www.debianadmin.com/linux-directory-structure-overview.html](http://www.debianadmin.com/linux-directory-structure-overview.html)

---

### Post by alan21276 on 2012-07-25
Have you tried simply renaming the drive using the built in disc utility program?

That might give you the effect of having a drive letter......even though Linux doesn't use them.

---

### Post by HiImTye on 2012-07-25
you could also mount it to a folder called /C: - there's no reason not to use ':' in your folder structure

---

### Post by Morbius1 on 2012-07-25
I'm not disagreeing with anyone who posted a response but I get the feeling from the original post that that he wants "/" to be "/C". 

Um ... I don't know if you can do that or not. I'm fairly certain that you cannot.

---

### Post by alan21276 on 2012-07-25
> **Morbius1 said:**
> I'm not disagreeing with anyone who posted a response but I get the feeling from the original post that that he wants "/" to be "/C". 

Um ... I don't know if you can do that or not. I'm fairly certain that you cannot.

As an ex-widows user I can understand that the original poster might be experiencing a touch of culture shock (assuming they are new to linux/ubuntu)
If this is the case then my advice would be to embrace your new file system and you will grow to like it and appreciate why it is the way it is.

---

### Post by Jay MC on 2012-07-25
> **Morbius1 said:**
> I'm not disagreeing with anyone who posted a response but I get the feeling from the original post that that he wants "/" to be "/C". 

Um ... I don't know if you can do that or not. I'm fairly certain that you cannot.

This is something that any non-Windows OS has to contend with...  people bringing expectations that are based on what they're used to with Windows.

This is also relevant to the "how easy are computers" discussion happening elsewhere.  A lot of "easy" is based on what you're used to.

Anyway, to bring this back on topic...  to the OP, yup, "C:" is just a Windows concept.

Does Ubuntu have a newbies' resource for people who are used to Windows?  It's pragmatic to assume a Windows background.  Wherever Linux does something differently, it would be good to take the bull of confusion by the horns and explain why it isn't relevant here and what you get instead.

Another example would be package management (you don't just run .exes you downloaded off the web).

If a newcomer is wondering how he can get his file explorer to show "drive letters", that feels like a bit of a failure for Ubuntu (insofar as it's trying to be "Linux for humans beings" - most of whom are used to Windows).

---

### Post by HiImTye on 2012-07-25
I dont think it's a failure at all, secondary mounted drives default to /media/ where it makes sense for them to go. it sounds more like a failure of expectations from the user.

it would be nice, however, if Ubuntu had an 'orientation' type deal when a new install first logs in (bringing up 'Help') - it might give the user more of an understanding of how things work and what to expect

edit: I think I remember older versions of Ubuntu doing that, or maybe I just opened help when I first logged in cause it was on the panel beside the launcher. who knows?

---

### Post by Jay MC on 2012-07-25
> **HiImTye said:**
> I dont think it's a failure at all, secondary mounted drives default to /media/ where it makes sense for them to go. it sounds more like a failure of expectations from the user.

it would be nice, however, if Ubuntu had an 'orientation' type deal when a new install first logs in (bringing up 'Help') - it might give the user more of an understanding of how things work and what to expect

edit: I think I remember older versions of Ubuntu doing that, or maybe I just opened help when I first logged in cause it was on the panel beside the launcher. who knows?

Sorry, I don't mean a failure of Ubuntu as an operating system - I mean a failure of the introductory experience, to cope with the fact that many newbies will come with Windows-based expectations.

The "orientation" thing you describe sounds exactly right.

---

### Post by oldfred on 2012-07-25
I much prefer the LInux way as you can assign anything you want to a partition. While / will be root, you can make a d: in Windows say Music in Linux or Data or anything that makes sense.

Also I like labels. Then any partition you do not automatically mount has a label that again has some meaning rather than just e:.
```

fred@fred-Precise:~$ sudo blkid -c /dev/null -o list
[sudo] password for fred: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs    WinXP    /mnt/cdrive    04B05B70B05B6768
/dev/sda2  ext3    backup   (not mounted)  13a684e4-2849-4566-9528-21cd07028a9a
/dev/sda4  vfat    SHARE    (not mounted)  46CD-C9B2
/dev/sdb2  ext4    Maverick (not mounted)  0eea4e95-ea0a-4745-80d4-57bf2bbc9d69

```

And when I add this flash I know it is my MicroCenter4GB flash drive.
/dev/sdf1  vfat    MC4GB    /media/MC4GB   E489-24AF

---

### Post by FlindoJimbori on 2012-07-26
Thanks everybody who helped! I am new to linux/ubuntu and this forum is great for transitioning from windows or another os to ubuntu. thanks everyone!

---

### Post by Lars Noodén on 2012-07-26
Actually the drive letters are even older than Windows or MS-DOS.  They are from CP/M and the first version of MS-DOS was lifted almost exactly from CP/M.  Back in the day, nearly all office machines ran CP/M if they weren't Apple II.  

As mentioned, in Linux and most other systems you have 'mount points', which can be named anything you can name a directory or file.  The 'file system' being mounted can be in nearly any format.  For the most part, Ubuntu takes care of mounting automatically for you.  If you want an overview of what goes where, look at the manual page for [hier](http://manpages.ubuntu.com/manpages/precise/en/man7/hier.7.html).  In general, all user data goes in /home, whether that is a separate 'partition' with its own mount point + filesystem or not.

---

