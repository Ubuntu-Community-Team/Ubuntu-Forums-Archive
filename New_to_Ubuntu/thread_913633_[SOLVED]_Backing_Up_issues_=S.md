---
title: "[SOLVED] Backing Up issues =S"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by xreaper on 2008-09-07
Hey all, just me (yet again) wondering about a couple of things.

Before I get into the actual question(s) I'd like to share a bit about the situation, incase any future users have the same issue as me.

I use Ubuntu 8.04 ( and it is awesome!!) which i put on 100gb of a 160gb hard drive, but the thing is, I think the boot sector of it is stuffed, so I've recently set it up so that the boot files are on a 4gb hard drive and it boots TO the 100gb partion.

Now, my questions are,
1: Is it possible to back up all of the programs that I use on ubuntu? Such as just being able to drag and drop the files into a new ubuntu installation and then 'SHAZZAM' its like the one I used to have?

and 2:
Is it possible to fix the boot sector of my hard drive? (I have a windows xp disk that i would greatly like to use on the spare 55gb partion so I can put games etc onto it, but it will not detect the hard drive)


any help on either of the two questions will be very much appreciated.
Thank you for your time.

---

### Post by Pro-reason on 2008-09-07
There are a couple of ways of backing up all your programs.

Firstly, you could make a backup of the whole damn partition on which Ubuntu is sitting, and dump it somewhere else.  Everything will be the same, to the byte.

That might not be what you want though.  If you want to do a fresh installation of Ubuntu, but have the same software packages, then you need to make a list of the packages you currently have installed.  You can do this from Synaptic (with *Save Markings As*).  Copy that list somewhere else, and use it to reinstall the packages on your new Ubuntu installation.

To reduce download times, it's best to also make a backup of the contents of */var/cache/apt/archives*.  That directory is full of .deb packages (the equivalent of Windows *Setup.exe* files which will have to downloaded again if you don't transfer them to the new Ubuntu installation.

---

### Post by xreaper on 2008-09-08
wow thanks heaps for that =] il not that one down. Now, can I copy them without having to use the ubuntu live cd?

---

### Post by Pro-reason on 2008-09-08
> **xreaper said:**
> wow thanks heaps for that =] il not that one down. Now, can I copy them without having to use the ubuntu live cd?

Copy what?  The DEBs?  Yeah, you can copy them from whatever.  If you had ext2/3 drivers installed, you could even do it from Windows.  They are just a bunch of files in a directory.

---

### Post by xreaper on 2008-09-08
cool =] and if i just wanted to copy every single ubuntu file onto a seperate shared folder to another computer then I'd be ok without the cd?

---

### Post by Pro-reason on 2008-09-08
As for the MBR (boot sector of your drive), there's isn't really any special way of fixing it other than writing a bootloader to it.  By running the GRUB MBR installer, you'll be doing so.  A Windows XP CD will also do so (by installing NTLDR on it).

If it still doesn't work, then physical damage to the drive is possible, but it's more likely that you just made a mistake somewhere.  Booting is complicated.

---

### Post by xreaper on 2008-09-08
Yeah, about the boot sector... I bought it like that =S but for the time being I was happy with ubuntu.. So i've lost all benefits for a warranty lol. so is it possible to just put boot files onto the 160gb hard drive?

---

### Post by Pro-reason on 2008-09-08
> **xreaper said:**
> cool =] and if i just wanted to copy every single ubuntu file onto a seperate shared folder to another computer then I'd be ok without the cd?

Let me understand what you want to do...

You want to boot into Ubuntu, then open up a shared folder on another computer on a network, and copy *all* the Ubuntu system files across.

Yeah, that would kinda work, but there are two things to bear in mind:
[LIST]
[*]The operating system will be running, so files could be being altered in the background as you copy them over.  It's probably best to boot into another operating system (e.g. any live CD) and do it from there, to avoid screw-ups.
[*]If you want to back up the entire system, don't just drag files.  Important stuff like &#8220;permissions&#8221; may get left out.  Instead, the &#8220;tar&#8221; command should be used to preserve the contents exactly.  It will create an archive file (like a .zip) that contains all the files you're backing up.   Alternatively, you can use the &#8220;dd&#8221; command to make a file that exactly mirrors not just all the files, but even the filesystem itself.
[/LIST]

If you're just copying the DEBs, you don't have to worry about this.

---

### Post by xreaper on 2008-09-08
Okay, I'll note that down. I'll try to make a backup of everything sometime tonight. Are you sure that just copying and pasting through the live CD will work? What about all system settings etc, such themes?

---

### Post by xreaper on 2008-09-08
Hey, what was that you were saying about a tar command? and something about dd?

---

### Post by Pro-reason on 2008-09-08
> **xreaper said:**
> Hey, what was that you were saying about a tar command? and something about dd?

To make an archive of a directory, use *tar*.  For example, if you want to back up all your DEBs and your home directory, and you have an external drive mounted at /media/myMP3player, you could do this:

```

tar -cvf  /media/myMP3player/DEB-backup.tar    /var/cache/apt/archives
tar -jcvf /media/myMP3player/home-backup.tbz2  ~

```

To back up an entire parition, use *dd*.  For example, if your Ubuntu root partition was /dev/sda1, you could back it all up with this:

```
sudo dd if=/dev/sda1 | lzop > /media/myMP3player/Full-backup.dd.lzo
```

See [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) for more info.

---

### Post by xreaper on 2008-09-08
okay =] thanks heaps =D
now I'll be able to continue trying to fix this boot sector without worrying about losing my precious data lol

---

