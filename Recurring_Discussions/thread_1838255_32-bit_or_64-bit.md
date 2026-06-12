---
title: "32-bit or 64-bit?"
date: 2011-09-03
forum: Recurring Discussions
---

### Post by QuantumMonkey on 2011-09-03
Hi, for a while, I had no idea what 32 bit and 64 bit meant, but now I have a general idea.

My laptop came installed with Windows 7 64 bit, and it ran great, and when I switched to Ubuntu, I downloaded the 32 bit version because it was recommended.

Would things like Minecraft and just the OS in general run better if I got the 64 bit version?

---

### Post by pqwoerituytrueiwoq on 2011-09-03
there is a little performance boost for math calculations with 64bit
when i switched from 32bit to 64bit on my laptop i saw a drop in battery life

If you have a 64bit processor use 64bit
they recommend 32bit cause adobe air/flash are not available for 64bit (not counting 64bit flash beta that you can install with flash aid)

---

### Post by QuantumMonkey on 2011-09-03
> **pqwoerituytrueiwoq said:**
> there is a little performance boost for math calculations with 64bit
when i switched from 32bit to 64bit on my laptop i saw a drop in battery life

If you have a 64bit processor use 64bit
they recommend 32bit cause adobe air/flash are not available for 64bit (not counting 64bit flash beta that you can install with flash aid)

Hmm, I do have a 64 bit processor, but I do use YouTube a lot, would that break?

---

### Post by sum1nil on 2011-09-03
I would think so (although not all software utilizes it) and I'd like to mention that I have been running 64bit Natty on my cheap eMachine laptop for months now without a hitch. All the hardware was recognized right off from the wireless to the ATI card. I just put 64bit Oneiric alpha on my desktop and that was a smooth installation as well.
Take the plunge :)

---

### Post by NightwishFan on 2011-09-03
As I have said for fours years now. Yes, try 64-bit out, it rocks. :)

Oh I should clarify really. Well..

Downsides:
[LIST]
[*]Uses slightly more memory.
[*]Rare proprietary drivers do not work.
[/LIST]

Upsides:
[LIST]
[*]Faster performance on 64-bit optimized software. Basically you notice this on apps that like to churn 100% cpu like video converters.
[*]Can address more memory, faster. It can use more than 3gb for a single app (which more or less is a limitation of 32-bit).
[/LIST]

[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

---

### Post by QuantumMonkey on 2011-09-03
> **NightwishFan said:**
> As I have said for fours years now. Yes, try 64-bit out, it rocks. :)

Oh I should clarify really. Well..

Downsides:
[LIST]
[*]Uses slightly more memory.
[*]Rare proprietary drivers do not work.
[/LIST]

Upsides:
[LIST]
[*]Faster performance on 64-bit optimized software. Basically you notice this on apps that like to churn 100% cpu like video converters.
[*]Can address more memory, faster. It can use more than 3gb for a single app (which more or less is a limitation of 32-bit).
[/LIST]

[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

Wow, thanks for the detailed reply!

I play Minecaft a lot, java game, and I had to install some proprietary drivers before it would run normally. I just installed them from the Gnome menu. They will work, right? :D

Also, how would I go about changing to 64bit? Will I lose everything? I also run Windows 7 alongside Ubuntu. Do I need to download it, put it on a USB/CD and install it like a fresh install?

---

### Post by doobrie on 2011-09-03
On my laptop I have 64-bit Windows installed but can run 32-bit applications.  I presume this is the same in Ubuntu?

I've got 32-bit Ubuntu installed as I've never seen a particular need (for the things I do) to install 64-bit.

---

### Post by NightwishFan on 2011-09-03
> **QuantumMonkey said:**
> I play Minecaft a lot, java game, and I had to install some proprietary drivers before it would run normally. I just installed them from the Gnome menu. They will work, right? :D
Yes, if you mean graphics drivers its very likely they will work. Perhaps try the live cd out. :)

> Also, how would I go about changing to 64bit? Will I lose everything? I also run Windows 7 alongside Ubuntu. Do I need to download it, put it on a USB/CD and install it like a fresh install?
Yes, you will need to do a fresh install. Though please note hoping to get a sluggish program to work fast by using 64-bit is unlikely to happen. However 64-bit is the standard these days.

If everything works well enough and a reinstall would be inconvenient stick to 32-bit. If a reinstall is easy, definately reinstall it.

---

### Post by dardack on 2011-09-03
I love 64 bit, been using it for 5 years now.  

I use google chrome, which has flash prebuilt in, so that works fine.  Also, the 64 bit beta works nice for firefox.

I use 32bit wine in 64bit ubuntu, so you have to install some 32bit libraries, but it's pretty easy with apt-get.

Anything native to ubuntu/linux should have a 64bit equiv (or you can compile it yourself if not, but I haven't run into an issue where something native wasn't already compiled as 64bit) so never  have had to run 32bit linux programs in 64bit.

NVM I take that back, I think the amazon mp3 dl'r is 32bit only?  I can't remember, I know something is, but you just get the32 bit libs and it works.

---

### Post by oldfred on 2011-09-03
I converted from 32 to 64 about 2 or 3 years ago. Neither Desktop nor laptop seem to have any real issues. Laptop only has 1.5GB of RAM, but I wanted same version on both systems.

You will have to do clean install. Do you have 20GB available? If so you can just install the 64bit in a new / (root) partition using the same swap. That way you can test it.

If you have a separate /home then a new install is easier as you do not have to back it up but you should have good backups anyway as any system change can cause issues where a backup is the only solution.

I do new installs and have little data on a day to day basis that I cannot recover from. So my backups are to let me just do a new install and recover my data.

I modified this:
Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

and backup this which is what you would need for a new install.
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
backup the following:

1. /home (Users' personal files and settings)
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup
5. list of installed applications 

I include these also:
cp /etc/apt/sources.list ~/sources.list.backup
apt-key exportall > ~/repositories.key
Various hardware listings/configurations
dpkg --get-selections > ubuntu-files
bash ~/Documents/LinuxDocs/CurrentSys/boot_info_script055.sh
lshw -html > ~/hardware_info.html
udevadm info --export-db > file.txt
dmidecode > bios.txt

Other applications if data not separate
apache, any sqldb, tomcat 
Do

---

### Post by philinux on 2011-09-03
[http://tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

It's a bit old now but still worth a read. Flash is not an issue now at all.

Thread moved to Recurring Discussions.

---

### Post by 3rdalbum on 2011-09-05
64-bit is really a non-issue nowadays. If your computer supports it, use it; the 64-bit edition of Ubuntu has more optimization than the 32-bit edition so there will be a little bit of a speedup for certain operations. There's no problems with software or anything.

Ubuntu 11.10 can even install 32-bit packages on a 64-bit system and pull in the correct libraries automatically. FINALLY. With this I'm sure they'll drop the "recommended" label for the 32-bit edition.

---

### Post by ninjaaron on 2011-09-06
There are still flash issues.  I have newish, but low-end hardware without any acceleration.  Full-screen flash is jumpy with a 64-bit kernel, and 32-bit is not, even with the latest betas.  There is also a program called ZSNES, which is the best SNES emulator for Linux, and for some technical reasons, it cannot be compiled for 64-bit.  There are some other games and such things with similar problems.  As far as I know, there aren't any programs yet that only work on a 64-bit kernel, though it's sure to come along some time.

However, these things aren't really such a big issue for me, and 64-bit does seem to be getting faster all the time as more things are optimized for it, so I use it anyway.

---

### Post by KUU on 2011-09-06
I always say if you have 64bit option on the motherboard then go with a 64bit OS using ACHI.

---

### Post by _d_ on 2011-09-06
As has been stated in other threads similar to this one, if you have a 64-bit capable CPU then use 64-bit OS.

Why waste all that extra potential on your CPU?

---

### Post by PhillyPhil on 2011-09-06
> **ninjaaron said:**
> There are still flash issues.  I have newish, but low-end hardware without any acceleration.  Full-screen flash is jumpy with a 64-bit kernel, and 32-bit is not, even with the latest betas.  There is also a program called ZSNES, which is the best SNES emulator for Linux, and for some technical reasons, it cannot be compiled for 64-bit.  There are some other games and such things with similar problems.  As far as I know, there aren't any programs yet that only work on a 64-bit kernel, though it's sure to come along some time.

However, these things aren't really such a big issue for me, and 64-bit does seem to be getting faster all the time as more things are optimized for it, so I use it anyway.

64 bit Flash works great for me.

@OP
if you have 64 bit hardware it's EXTREMELY unlikely that 32 bit software would be the preferred choice.  I look forward to the inevitable 64 vs 128 bit threads...

---

### Post by sammiev on 2011-09-06
64 bit as all the newer computers are 64 bit. If your computer is with the times, then the OS should be as well. Good Luck! :) I love 64 bit Linux.

---

### Post by ninjaaron on 2011-09-07
> **PhillyPhil said:**
> 64 bit Flash works great for me.

Congratulations.

---

### Post by _d_ on 2011-09-07
> **PhillyPhil said:**
> 64 bit Flash works great for me.

Indeed it does for me too. Can now watch 1080p flash videos full screen without chop. :D

---

