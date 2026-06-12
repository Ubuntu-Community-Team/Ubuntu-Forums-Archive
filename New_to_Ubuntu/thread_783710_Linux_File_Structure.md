---
title: "Linux File Structure"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by PoopyTheJ on 2008-05-06
Can someone explain to me or direct me to a resource that can explain to me the Linux directory structure? Coming from a Windows background the whole files structure makes no sense to me at all. I can find things, given a path but I don't understand why they are the way they are. The whole C:\ thing with windows makes sense to me, but I don;t understand how \ is root and what that means, how are things organized exactly and why? Most especially why in linux. This is brought on by this passage in a reading for my college course here that makes sense in a Windows environment, but I'm not sure it makes sense for what I know about Linux.

    "In addition, the OS must create and manage a directory structure to organize files. A directory
is a named area on the hard drive. This area can contain other named areas, just like a file cabinet
can contain files within files. In most computer systems and in personal computers, the file and
directory systems follow a tree format. There is a root directory, usually called “C” on most per-
sonal computers. The user may create subdirectories under the root directory. Some software
programs create their own subdirectories when users load them. In addition, these subdirectories
may have their own subdirectories, and so forth, as Figure 3.2 shows. Creating directories and
subdirectories and allowing users to place files within them is a major function of any OS."

---

### Post by Monicker on 2008-05-06
This came up in another thread earlier today.  I'll borrow a a link which someone posted there.

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/")

Hopefully that makes it clearer.

---

### Post by tacutu on 2008-05-06
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
[http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)

---

### Post by tjwoosta on 2008-05-06
so what dont you understand?


go to the terminal and start exploring (youl figure it all out)

this is root /     (like saying c: in windows)

do this to navigate to root
```

cd /

```
do this to list the files in the directory
```

ls

```
(or ls -a to list hidden files)

this is your user directory ~/  (or you could also do /home/"yourusername")

do this to navigate to your user directory
```

cd ~/

```
or (cd /home/yourusername)

---

### Post by PeterJS on 2008-05-06
That looks a bit stale, it still refers to the FSSTND, the wiki page appears to be more up to date:
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by starcannon on 2008-05-06
The Link PeterJS gave you is very good.

If your looking for some analogy, I will offer this:

C:\   would be similar to /

Johns Documents  would be similar to  /home/John

This is of course a simplified explanation, but equating it to Windows thinking thats about the best I can think of.

GL, and don't be afraid to poke around, as long as you don't run as root, you can look under the hood without damaging things.

Enjoy

---

### Post by love2learn on 2008-05-06
> **PeterJS said:**
> That looks a bit stale, it still refers to the FSSTND, the wiki page appears to be more up to date:
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
 
 
 
So I assume Ubuntu and the like use FHS standard? If so, who uses FSSTND and who uses GOBOLinux? I ask this cause the GOBOLinux standard makes much more sense to me.

---

### Post by scorp123 on 2008-05-06
> **love2learn said:**
>  I ask this cause the GOBOLinux standard makes much more sense to me. Only GoboLinux uses their brain-dead standard. Sorry to say so. With their standard they more or less break everything the FHS has achieved in the past 30+ years. And to old-seasoned users FHS makes a whole lot more sense than this chaos that people dare to call a "standard" on Windows, let alone the nonsense of Gobo.

Let me show you an example:

Let's suppose I have a GERMAN Windows and an English MS Office. Where will the programs end up? And before you answer: Let me add that on a GERMAN Windows the default folder for installed programs is "C:\Programme" (German plural for "programs") and not the English "C:\Program Files". So again: Where should an ENGLISH Office install itself? If you now said "Duh. Into the German folder then if that is the standard on a German Windows ... " then you guessed WRONG. English programs will insist that they be installed  into "C:\Program Files" and not the "C:\Programme" which would be normal for a German Windows installation. Now the funny part is this: Some very crucial libraries (DLL's) will nontheless end up in "C:\Programme\Gemeinsame Dateien" (English: "C:\Program Files\Common Data").

This is pure daft nonsense!

Such BS cannot happen on UNIX-like operating systems where the system-wide configuration files will go to /etc and the executable files will end up in e.g. /usr/bin/ (or e.g. /opt/openoffice/bin/ ) *REGARDLESS* of whether or not I use English or some other language.

The above example with a German Windows and an English MS Office package was a relatively simple one. I have seen cases where people had to install e.g. an English Windows (because of corporate policy: All OS have to be in English) and a German MS Office (because it's one of the local languages) and some additional software in French (because French is widely used in some parts of Europe) ... Result:  ==> Utter chaos on the filesystem!

So for me it's thanks but no thanks to that wannabe "standard" they have on Windows. I prefer the FHS any day of the week. Go and work for IT support in a country where they use more than one language and you will soon understand why anything but FHS is pure utter crap. Seriously. :)

---

### Post by bodhi.zazen on 2008-05-06
See also : [https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

---

### Post by 3rdalbum on 2008-05-06
There's not a lot that you need to know.

/ is basically, generally, the partition that your computer booted from.

/media is where drives get mounted - your optical drives and flash drives and such.

/home is where each user's home directory is. Each user's home directory contains the user preferences files for applications. If a program starts behaving strangely where it was working properly before, try deleting its preferences file or preferences directory (you need to enable "Show hidden files" in Nautilus).

/tmp is for temporary files

/dev is a directory containing files that represent actual physical devices, as well as imaginary devices (such as the random number generator). Your DVD drive itself will probably be located at /dev/dvd or /dev/scd0; but if you put in a disc and it appears on the desktop, you can get at the contents of the disc from /media.

Apart from specific file locations (/etc/fstab, /etc/X11/xorg.conf, /var/cache/apt/archives etc), that's all you really need to know; and some of what I've told you is what you might never need to know anyway!

---

### Post by SunnyRabbiera on 2008-05-06
For me I actually find the linux filesystem quite easy to understand, in fact I like it much better then windows.

Its very simple once you learn:
Home= My documents
Root= administrator directory
Bin= Binaries
Usr= user folders
lib= libraries
share= shared folders
opt= optional applications
sys= system
tmp= temporary
sbin= superuser (root) binaries
var= Variable data


this guide here is a good page to start, it is mainly for unix but linuz shares most of its directory structure:
[here]("http://burks.brighton.ac.uk/burks/linux/rute/node17.htm")

---

### Post by love2learn on 2008-05-06
> **scorp123 said:**
> Only GoboLinux uses their brain-dead standard.
 
Let me show you an example:
 
Let's suppose I have a GERMAN Windows and an English MS Office.  :)
 
 
okay stop right there. That is where you are messing up. Pick a program base language and go with it. :lolflag:
 
[COLOR=black][FONT=Verdana]No, in all reality I see your point but i don't like the redundancy in the FHS standard. Why have a /root/ a /usr/ then all the libs, bins, sbins, and shares that go behind them? then have the /var/ with the same behind them. THEN have the libs,bins, sbins, and shares in the home directory too? That seems like a "brain-dead standard" to me. I understand the security in the /root/ directory but there is no better way then to segregate all of those according to user and function of each PART of the program?[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Don't get me wrong. I am not trying to seem pro at this because I have no clue how Linux actually runs. I am just trying to understand the FHS so that I can utilize the OS of choice more efficiently.[/FONT][/COLOR]

---

### Post by tjwoosta on 2008-05-06
i switched to ubuntu about 6 months ago and at first i would have agreed with you about the linux filesystem not making much sense

but now that ive used ubuntu for a while and i actually understand how things work  it actually does make alot more sense to me than the windows filesystem used to

i think you should at least try it out for a while before you start making assumptions that it is not as good as windows just because things are arranged a little differenty


by the way i think   /home/username/Documents = My Documents

not  /home = MyDocuments


going to /home/username directory in ubuntu would be like going to C:/users/username directory in windows vista

---

### Post by jimv on 2008-05-06
I've been using Ubuntu for about a year now, and the thing that I've realized about the directory structure is that there are really only a few folders that I need to worry about.

/ for the root of the drive
/media for all my drive mounts
/home for all the user profiles
/dev for the devices
/etc for machine/program settings

I've never really had to deal with the other directories much.  The package manager takes care of all that stuff.

---

### Post by SunnyRabbiera on 2008-05-06
> **tjwoosta said:**
> 

by the way i think   /home/username/Documents = My Documents

not  /home = MyDocuments

No as initially the home directory has a music folder, a videos folder and a pictures folder.
But you can make the documents folder like the my doccuments folder in windows by just moving those folders into it.

---

### Post by tjwoosta on 2008-05-06
what windows version are you talking about?

in windows vista i have a music and a videos and a pictures and a documents folder all in my user directory (C:/users/tj/)

(there is no music and pictures and video inside the documents directory)
why would there be?

---

### Post by flyinraptr on 2008-05-06
> **3rdalbum said:**
> There's not a lot that you need to know.

/ is basically, generally, the partition that your computer booted from.

/media is where drives get mounted - your optical drives and flash drives and such.

/home is where each user's home directory is. Each user's home directory contains the user preferences files for applications. If a program starts behaving strangely where it was working properly before, try deleting its preferences file or preferences directory (you need to enable "Show hidden files" in Nautilus).

/tmp is for temporary files

/dev is a directory containing files that represent actual physical devices, as well as imaginary devices (such as the random number generator). Your DVD drive itself will probably be located at /dev/dvd or /dev/scd0; but if you put in a disc and it appears on the desktop, you can get at the contents of the disc from /media.

Apart from specific file locations (/etc/fstab, /etc/X11/xorg.conf, /var/cache/apt/archives etc), that's all you really need to know; and some of what I've told you is what you might never need to know anyway!

Is there a link or doc that covers what the default permissions should be for the corresponding folder structure?

Thanks -

---

### Post by SunnyRabbiera on 2008-05-06
> **tjwoosta said:**
> what windows version are you talking about?

in windows vista i have a music and a videos and a pictures and a documents folder all in my user directory (C:/users/tj/)

(there is no music and pictures and video inside the documents directory)
why would there be?

well that is how it was set up on XP, I know vista's directory tree is more unix like.

> **flyinraptr said:**
> Is there a link or doc that covers what the default permissions should be for the corresponding folder structure?

Thanks -

By default everything should be set to the administrator/ root account, but in ubuntu you are the administrator if you are the default user however you need to enter into root/superuser mode via sudo to edit any major core files and such...
Only your home directory should have different permissions and practically everything in it is permitted to you in non superuser mode.
Usually in linux the root account and the default user are separated, but in ubuntu the root account is disabled so instead it gives the default user access to administrative tasks but only under certain conditions like entering sudo mode in the terminal.
Mac OSX has a similar system.

---

### Post by scorp123 on 2008-05-06
> **love2learn said:**
>   i don't like the redundancy in the FHS standard.  Because you don't fully understand it yet. Don't worry. Give it some time and you will get to appreciate and love it. You think I was born loving the FHS? Nope. Some 12 years ago I was a newbie too. Did I understand it back in 1996? Nope. Heck, partitioning was a lot more complicated back then, you couldn't place all partitions where you wanted, you had to pay attention to the 1024 cylinder boundary size, to sector sizes, and resizing existing partitions was a lottery at best, half of the time it would ruin whatever you had on the disk. Usually thanks to MS-DOS's "ability" to fragment and corrupt its own filesystem in no time it could be that the Linux partitioner would not catch all fragments of the filesystem when it tried its best at resizing .... Why would one take this burden and even bother with this? Because once you understand FHS and the beauty behind it you will never ever want to return to a different partitioning scheme! See below after the next quote ...

> **love2learn said:**
>  Why have a /root/ a /usr/ then all the libs, bins, sbins, and shares that go behind them?  It's all very logic ... once you see the logic behind it.

Originally, some 30+ years ago when harddisks were small and expensive, **each** of those locations would reside **on their own harddisk** platter. So **/usr** would physically be on a different disk than **/var**, and **/home** would again physically be on a different disk, and so on.

The beauty here is that if one disk gets corrupted for some unexplainable reason (very common in those days) it would not affect the rest of the system. Chances were very very good that the system might even still boot although some 60% or more of its files were gone to Nirvana and not reachable at the moment!

This point is still valid today if you partition your harddisk "UNIX-style" and place **/boot**, **/**, **/usr**, **/opt**, **/var**, **/home** and maybe **/tmp** on different harddisk partitions (instead of just making one "/" and a swap as most people unfortunately do these days!).

> **love2learn said:**
>  then have the /var/ with the same behind them. THEN have the libs,bins, sbins, and shares in the home directory too?  Did you read the Wikipedia article someone already posted? It's all perfectly explained there and it makes perfect sense.

Whenever it says "/bin" then the contents are binary programs, stuff you could execute and launch. Therefore things that reside in e.g. "/usr/bin" are programs that are launchable for all users on a system. Things that reside in a "/sbin" directory should only be used by the superuser ('sbin' = **_S_**uperuser's **_Bin_**aries). So just knowing this little difference you already know which programs are potentially dangerous and where to look if you need to launch an administrative task from the shell. Chances are that's in /sbin or /usr/sbin  <== the slight difference here is that stuff in "/sbin" is *absolutely* needed during a system's boot and therefore may not reside on a different mount point. Just like /etc, /lib and /root (= the superuser's home directory) it must be present at boot time and thus be on the "/" platter. Stuff in "/usr/*" could in theory reside on its own platter and is not really needed during boot time. People like me still do this: I have /usr on its own partition.

Having stuff partitioned "UNIX-style" allows for some nice manipulations too. I could boot into single user mode, manipulate the other system folders such as /usr and /var without being at risk of losing one single bit of data, e.g. move those locations to new disks, and then reboot the system and it will react as if nothing had happened.

You can't do anything of this if you have all on one single "/" partition!

Stuff in "/var" is "variable" data. E.g. all the log files end up there in /var/log, all the cache files of e.g. print managers and the "apt" packet manager end up in /var/cache, /var/apt and /var/spool, and so on.

There is a lot of beauty here.

Also: I for example partition my disks in such a way that partitions with lots of read access but only few write accesses are up front on the beginning of the disk so the heads can find the data really really fast. So in this philosophy (which I adhere to) stuff like /boot, /usr and "/" belong to the beginning of a disk so it can be read really really fast. Locations that get lots of write accesses such as /var, /home and /tmp and the swap partition should go towards the end of the disk. This helps keeping fragmentation down to an absolute minimum and helps keeping the speed of the system up.

> **love2learn said:**
>  That seems like a "brain-dead standard" to me. Because you don't yet understand it. You are used to the braindead ways Windows used to operate. (Yes, that was sarcasm and not so much meant in earnest :)  Please.... nobody get upset here, ok?)

Let's look at some facts from an OS-neutral point of view:

- It's a physical fact that filesystems on a harddisk will fragment to some extent, sooner or later
- some filesystems fragment faster, some slower
- some filesystems do a really hard job trying to avoid fragmentation whenever and wherever they can
- there are files a computer constantly needs to read (e.g. programs)
- there are files a computer constantly needs to write to (e.g. logs, settings)
- there are files that should be kept away from the ordinary user
- it's hard to predict how much a computer will swap, right? So it would be wise to use a swap mechanism that avoids fragmentation, right?

**Windows gives you *NOTHING* of the above!** ... Except fragmentation and corrupt filesystems. Just by using the dang thing. :)

- it's filesystems will fragment fast as hell
- it doesn't even try to avoid fragmentation. Instead you're supposed to run "Defrag" from time to time

- there is no separation whatsoever between locations that get lots of read accesses and lots of write accesses, it's all on the same C:\ filesystem so fragmentation is *bound* to happen no matter what you try

- every user and every process can potentially touch every file on the same platter (the many viruses, trojans and self-propagating malware are testament to this!)

- Windows braindead design has the swap file on the same filesystem where the OS and the user data reside, so it's constantly growing, shrinking, growing, shrinking ... Again: Fragmentation is bound to happen!


With FHS however you have a decent chance of taking all of above problems apart and keeping them at a minimum!

- an elaborate "UNIX-style" partitioning scheme that keeps e.g. /boot, /, /usr, away from /var and /home will help to keep fragmentation at a minimum because with this scheme you have effectively separated the locations that need a lot to be read from from the locations that get a lot written to.

- all Linux (e.g. Ext3, ReiserFS, XFS, JFS) and UNIX (e.g. UFS, ZFS, VxFS, etc.) filesystems that are currently in wide use try their utmost to avoid fragmentation. Proper partitioning will help even more to keep the filesystems clean and fast at all times! (with Windows that would be a pointless exercise because it would sooner or later fragment anyway!)

- admin programs are usually separated from ordinary user's programs (e.g. /sbin vs. /bin, /usr/sbin vs. /usr/bin etc.)  <== those locations can be locked down without hampering the operation of a system. Try that with Windows, e.g. by locking down "C:\Programs" ... :D

- system configuration in /etc is separated from an ordinary user's personal configuration (which is in their /home) ... System-wide config files could too be locked from an ordinary user (e.g. guest accounts), e.g. by using ACL's and by denying the "guest" group read access to /etc ... this would have no negative effect on the system. Please try that with Windows, e.g. block access to the "System32" folder ... ;)

> **love2learn said:**
>  I understand the security in the /root/ directory but there is no better way then to segregate all of those according to user and function of each PART of the program? See above. Security is just one part of it. There are other aspects such as keeping stuff apart that needs to be read from stuff that needs to be written to all the time.

> **love2learn said:**
>  Don't get me wrong. I am not trying to seem pro at this because I have no clue how Linux actually runs. I am just trying to understand the FHS so that I can utilize the OS of choice more efficiently.  No problem here with that. And please dont get me and my sometimes sarcastic comments wrong either ;)

---

### Post by bodhi.zazen on 2008-05-06
@scorp123: Thank you for taking the time to write all that out. 

=D>

---

### Post by tjwoosta on 2008-05-06
thats awesome man...  i learned alot there that i probably never would have known

thanks

---

### Post by PeterJS on 2008-05-06
> **scorp123 said:**
> A bunch of awesome stuff

That's great. You cover in great detail that things can be on separate disks, and that's great and all, but you can take it one step further. It's entirely possible to mount the entire /usr/ hierarchy as a read only NFS partition, on an entirely separate machine, with /usr/local/ as a local partition if need be. The benefit of this is that you could have one /usr/ partition shared for every machine on a network. If you set up logins to authenticate with a network service like ldap, and NFS mount /home/ as well you can get a full installation down to requiring only a couple hundred megabytes of local disk space. This isn't as useful these days as disk space is cheap and plentiful, but as scorp pointed out, this was not the case back in the day.

---

