---
title: "Can this be done?????"
date: 2019-08-11
forum: New to Ubuntu
---

### Post by az64x on 2019-08-11
I am a retired LONG time Windows user (since DOS 2.1) but 100% new to Linux.

I want to setup several older computers in a lab for handicapped adults to be able to browse the web.   So I need to lock the computer down as much as possible.

I would like to setup Lubuntu to boot from a DVD without asking for a password.  It would then use the internal hard disk as a memory cache and place for temp files. 

When Lubuntu starts I would like it to erase any files on the hard disk.  So anything downloaded before would be erased.

When I initially setup the computer up I would like to just format the hard disk as a NTSF without a system.

[SIZE=4]**Is this possible???**[/SIZE]
 
Joel in Texas

---

### Post by guiverc on 2019-08-11
A 'live' creates a temporary / file system in memory by default and achieves much of what you want, there is no password but you still have to select 'try lubuntu' but it has no password.

It reads like you want a 'kiosk' mode (ie. session save only), but the mention of DVD makes me think of 'live' use, but NTSF?? 

If you mean NTFS (NT file-system) but it's a foreign *fs* for GNU/Linux so not ideal for the storage of files as not all information can be stored there, but 'live' mode won't need it anyway, so it need not be used.

---

### Post by TheFu on 2019-08-11
Anything is possible with some customization.  There are probably better answers, but try it your way.  See what works and see where things don't work the way you like.  Make a list of issues and work them 1 at a time.

I have no idea what a NTSF hard disk would mean, but if there are drivers for it, then it could work.  Unix systems need file systems that support Unix permissions. Using a file system that isn't fully compatible will break some things. HOME directories and /tmp/ must be Unix file systems.

You can make user accounts automatically login and you can wipe the personal data for any userid both at login or at logout or at reboot or all of those times. It takes just a little scripting.  Running off optical media will be slow, so I would avoid it or running off slow USB storage.  The best external storage option would be to use a USB3 SSD device, but really using the internal HDD would be faster.

If all you want is to run a web browser, then Ubuntu really is overkill and a security liability.  Something more like ChromeOS would be a better answer for a number of reasons.  There are versions of that OS called ChromiumOS.  These are effectively impossible to hack because the OS and applications are mounted read-only.  [https://www.howtogeek.com/217659/how-to-get-a-chrome-os-like-operating-system-on-any-pc/](https://www.howtogeek.com/217659/how-to-get-a-chrome-os-like-operating-system-on-any-pc/)  These OSes are designed to work on lower-end computers with limited RAM.  CloudReady is one that a friend uses rather than using a Chromebook for her college course work.  They are required to use Google Docs for their assignments. It integrates just like ChromeOS on a Chromebook would.
If you and your clients care about privacy, then the ChromiumOS option isn't so good.

There are very light Linux distros which can run from RAM only.  TinyCore is one.  [http://tinycorelinux.net/](http://tinycorelinux.net/) The hardest part for any Linux working is being compatible with the hardware available.  If the PCs are all identical in the normal corporate way, then you can make 1 custom distro just for that hardware. If they are not, supporting the different hardware might be a nightmare.  Running from RAM is very fast.

If you run off any external device that is read-only, you'll need to rebuild the distro every week or two for security reasons. That would be the only way to patch and patching is critical these days.

---

### Post by cruzer001 on 2019-08-12
An earlier discussion about a class lab

[https://ubuntuforums.org/showthread.php?t=2422977](https://ubuntuforums.org/showthread.php?t=2422977)

---

### Post by CatKiller on 2019-08-12
If you set the machines up as thin clients you don't need to worry about anyone messing them up by taking out the dvd or thumb drive, and they won't need any internal storage of their own.

---

