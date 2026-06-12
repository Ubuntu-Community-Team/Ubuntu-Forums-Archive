---
title: "Linux file system hierarchy"
date: 2008-07-03
forum: Recurring Discussions
---

### Post by Sir Nose on 2008-07-03
Hello fellow Ubuntu users.

Each new Ubuntu release have brought many technical improvements. 8.04 added PulseAudio, 7.10 added Compiz etc. One crucial area that hasn't been tackled yet - but hopefully will be - is the filesystem hierarchy. The standard unix FSH has served its purpose, and is simply too confusing for modern non-unix-guru user. There's no technical reason for not adopting simpler, more intuitive standard. Gobo Linux is a proof that. I hope Ubuntu and other big distros would also embrace this idea. What do you think?

---

### Post by Daishiman on 2008-07-03
While the intention is good, I don't see why it should be altered. It has been over a year since I've had to access any filesystem that's not for personal data. On the other hand, as an experienced Unix user I find the layout to make a lot of sense and it's useful for administration purposes as it is.
      I don't see any significant benefit to new users, and a fairly inconvenient detraction for old timers. If you've done anything that needs you to access /usr or /var or /tmp, you can certainly take the 2 minutes you need to learn what they do (seriously, it's a no-brainer), because whatever you were doing wasn't that easy in the first place.
      I dunno, it's not like I'm intensely zealous about this position, but in the wake of me seeing that it doesn't harm anybody and would take a fair bit of re-engineering, I think there's bigger issues to look at.

---

### Post by celsdogg on 2008-07-03
i can somewhat agree with this, but at the same time if they change it, will they not be so POSIX compliant anymore?

---

### Post by Sir Nose on 2008-07-03
Gobo Linux basically allows you to have either the old fashioned Unix structure or the modern one. They do not exclude each other, since the new hierarchy is created with symlinks. I've heard Mac OS also does it this way. No reason why Ubuntu or some other mainstream distro didn't adopt this great idea. :)

---

### Post by LaRoza on 2008-07-03
> **Sir Nose said:**
> 
One crucial area that hasn't been tackled yet - but hopefully will be - is the filesystem hierarchy. The standard unix FSH has served its purpose, and is simply too confusing for modern non-unix-guru user. There's no technical reason for not adopting simpler, more intuitive standard. Gobo Linux is a proof that. I hope Ubuntu and other big distros would also embrace this idea. What do you think?

That doesn't make sense. There is a long lived and long followed standard and you are saying it is too confusing for a "modern non-unix guru". 

I am not sure what you are trying to say. Any file organization will be confusing to "non-$OS guru's", and just as pointless for them to know. People don't need to know it inside and out, and few do. Look at Windows. A mess of files, yet no one cares and those who do, know it. Same in Linux.

There is no such thing as "more intuitive" when it comes to computers, only what one is used to. 

Linux is primary supposed to be used by...Linux users, who know the system.

---

### Post by LaRoza on 2008-07-03
> **Sir Nose said:**
> Gobo Linux basically allows you to have either the old fashioned Unix structure or the modern one. They do not exclude each other, since the new hierarchy is created with symlinks. I've heard Mac OS also does it this way. No reason why Ubuntu or some other mainstream distro didn't adopt this great idea. :)

"old fashioned"? It is widely used, understood, standardized and easy to follow.

---

### Post by Choad on 2008-07-03
are you saying that "/usr/bin" is at the same level of intuitiveness as "/program files"

i'd say it's pretty obvious the self explanatory one is more intuitive.

---

### Post by smbm on 2008-07-03
Here is a link to another thread (one of many I've no doubt, I just couldn't be bothered to look for any more) discussing this subject in much more detail:

[http://ubuntuforums.org/showthread.php?t=823419](http://ubuntuforums.org/showthread.php?t=823419)

It makes for an interesting read. Both sides of the discussion are represented pretty comprehensively.

For what it's worth, I'm of the opinion that the file structure definitely should not change. The main reason against it (for me anyway) being; haven't we got more important stuff we could be doing? For example; better power management on laptops.

With the old adage "if it ain't broke don't fix it" getting an honorable mention for being pretty spot on too.

---

### Post by Choad on 2008-07-03
> **smbm said:**
> Here is a link to another thread (one of many I've no doubt, I just couldn't be bothered to look for any more) discussing this subject in much more detail:

[http://ubuntuforums.org/showthread.php?t=823419](http://ubuntuforums.org/showthread.php?t=823419)

It makes for an interesting read. Both sides of the discussion are represented pretty comprehensively.

For what it's worth, I'm of the opinion that the file structure definitely should not change. The main reason against it (for me anyway) being; haven't we got more important stuff we could be doing? For example; better power management on laptops.

With the old adage "if it ain't broke don't fix it" getting an honorable mention for being pretty spot on too.
i definitely agree with this sentiment. it could be improved but it is certainly not a high priority.

---

### Post by LaRoza on 2008-07-03
> **Choad said:**
> are you saying that "/usr/bin" is at the same level of intuitiveness as "/program files"

i'd say it's pretty obvious the self explanatory one is more intuitive.

First of all, spaces shouldn't exist in directory names.

And I will play this game a bit.

What is in "program files"? Shared libraries? Individual programs? Configuratin files of programs?

The Linux directory structure is easy to follow:

Here, the mystery is ended: [http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

---

### Post by cardinals_fan on 2008-07-03
Read [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

The file system hierarchy works fine if you know how it's organized - if not, then you shouldn't be screwing around with it :)  Worry about bug fixing instead.

---

### Post by LaRoza on 2008-07-03
> **cardinals_fan said:**
> Read [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

The file system hierarchy works fine if you know how it's organized - if not, then you shouldn't be screwing around with it :)  Worry about bug fixing instead.

Exactly :-)

The people complaining about it probably don't know the Windows structure beyond "program files"

---

### Post by ryaxnb on 2008-07-07
The Windows hierachy played around with moving everything and it really screwed stuff up
Programs:
Windows 3.1 C:\, Windows 95 C:\Program Files
16, 32, 64: on a 64-bit system:
C:\windows\system, C:\windows\syswow64, C:\system32.
Yes, 32-bit files in syswow64. No sense whatsoever.:lolflag:
Appdata:
C:\WinNT\Profiles\User\Application Data
C:\Windows\AppData\ (yes they actually stuffed it into the windows directory at one point.)
C:\Users\User\Application Data
C:\Windows
C:\Documents and Settings\User\Application Data
What a lot of folders!
Documents:
C:\Documents and Settings\User\My Documents\
C:\Users\Documents
C:\My Documents
C:\WinNT\Profiles\User\My Documents
C:\WinNT\Profiles\User\(no standard in WinNT 3.5 and earlier, I believe)
Again, WTF?
User "Home":
C:\Users\User
C:\Documents And Settings\User\My Documents, although some was stored at C:\Documents And Settings\User\ but this was just stuff for the OS
C:\WinNT\Profiles\User
C:\WinNT\Profiles\User\My Documents
C:\My Documents
C:\
Hmmm...

Windows itself:
C:\Windows
C:\WinNT

and the profiles folder:
C:\Users
C:\Documents and Settings
C:\WinNT\Profiles
C:\ (none on Win9x, C:\ was their "home")

whereas on Linux:
system:
/bin, /sbin for essential system utilities
/boot for boot-up help and kernel
/proc - virtual directory
/root - most important home folder

Users go here:
/home/User
Documents can go wherever in your home, but ~/Documents is typical.

Appdata goes in .files in /home/User aka ~

Applications by importance (very handy for multi-user OSes):
/bin, /sbin; essential
/usr/bin; /usr/sbin; important, sometimes on network.
/opt: seperate hierachy, propietary packages etc. go here; low importance, sometimes on a network
/usr/local/bin more, medium important binaries (sometimes)

Handy stuff not found on Windows:
/etc: Central for config; Windows uses Registry (ach!) and INI.
/lib, /usr/lib, sometimes /usr/local/lib, and sometimes even /opt/lib: Libraries of decreasing importance.
/mnt, /media: the mountpoints of course! Confusing to Windows users at first, but FAR superior to C:, D: crap.
/sys: system drivers
/usr/games: Yay! Games! 
/usr/share, /usr/local/share: Program files that aren't executables or libraries, of decreasing importance. 
/var: Volitaile, always changing data. Good for backup priorities.  
/tmp: Temporary files and more!

---

### Post by xArv3nx on 2008-07-08
I have a better idea, why don't we just use Symlinks and hide the "bad" directories?

I've never bothered to learn the filesystem hierarchy, for the most part. It is quite confusing, though (especially with all those different directories in those directories, etc etc..).

---

### Post by smartboyathome on 2008-07-08
Symlinks doesn't hide anything. The problem with hiding files in linux is that traditionally you need to add a . in front of the name, and you can't do this because Linux is very exacting when it comes to letter case and file names etc.

Gobolinux solves this with a patch to the kernel and a userspace program.

---

### Post by LaRoza on 2008-07-08
> **xArv3nx said:**
> I have a better idea, why don't we just use Symlinks and hide the "bad" directories?

I've never bothered to learn the filesystem hierarchy, for the most part. It is quite confusing, though (especially with all those different directories in those directories, etc etc..).

It is simple. [http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

---

### Post by smartboyathome on 2008-07-08
Yes, you can read that, or make the file system "easy to read". Or, at least, admit Gobohide to the kernel so that you can hide stuff and can customize your filesystem yourself.

---

