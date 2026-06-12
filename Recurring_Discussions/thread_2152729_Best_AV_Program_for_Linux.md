---
title: "Best AV Program for Linux?"
date: 2013-06-08
forum: Recurring Discussions
---

### Post by altirisx on 2013-06-08
I understand you dont really "need" an AV program for linux, but what if you do get a virus, how will you know? You wont.

Anyways, I have ClamAV with the ClamTK GUI installed on my Ubuntu 13.04 PC however is it really an Anti virus program or does it just scan directories? If it only scan directories what is another COMPLETELY free AV program for ubuntu?

---

### Post by Sef on 2013-06-08
Check the link below.[URL="https://help.ubuntu.com/community/Antivirus"]

https://help.ubuntu.com/community/Antivirus[/URL]

---

### Post by HermanAB on 2013-06-09
Here is a scanner for you:

#! /bin/bash
echo Super Virus Scanner
echo Copyright Reserved GPL Version 2 or later, 2013.
sleep 1
echo Updating...
sleep 5
echo Thinking...
sleep 3 
echo Scanning...
sleep 30
echo Almost done...
sleep 30
echo Drum roll...
sleep 5
echo No viruses found!
sleep 1
echo Done.

---

### Post by mikodo on 2013-06-09
I haven't used it for a long time and had to go looking for an install of ClamTK virus scanner in other distos and releases.I found a copy of one installed in Ubuntu 10.04 that will look dated to you. To search inside of directories you have to tell it to scan recursively (everything in the directory and folders). 

See the provided Screeny below:

Edit: hmm. looks like I used it not that long ago. I didn't remember, but probably in preparation of backing up my data before removing Ubuntu 10.04, I guess.

---

### Post by deadflowr on 2013-06-09
> [COLOR=#000000]I have ClamAV with the ClamTK GUI installed on my Ubuntu 13.04 PC however is it really an Anti virus program or does it just scan directories?[/COLOR]

That's what all AV programs for linux do.
They just scan files,folders, and directories for viruses.

It doesn't provide firewall and shields and stuff like that, because those functions are already built into the system.

The real difference between AV programs in linux isn't their features or functions, but it is the accuracy of detection.
Some are good, like I've read about BitDefender, and some are not so good, like clamtk; which has a known history of false positives.

Anyway, the chances of a virus infecting your linux system are pretty remote.
And AV programs are built to read windows-built viruses, as there are so many, and not linux-based viruses which are so few.
It's probably something to be seen as to whether or not they could even read a linux virus.

---

### Post by 3rdalbum on 2013-06-09
> **altirisx said:**
> I understand you dont really "need" an AV program for linux, but what if you do get a virus, how will you know? You wont.

You won't even with an anti-virus program, squire.

Anti-virus companies don't keep a team of Linux virus experts on their payroll for the eventuality that there will be a Linux virus - they'd be paying $60,000 a person per year, for no return (there have been no Linux viruses for several years now). As a result, anti-virus programs don't detect Linux viruses, even when one comes out eventually.

Whenever a Linux virus comes out, it doesn't propogate very far. I doubt anyone on Ubuntu Forums has ever had a Linux virus.

You're just as safe without anti-virus, as with one*. Therefore, don't bother.

*I'd probably even say the same thing about Windows, but for a different reason: Even with anti-malware software, on Windows you'll never be able to get rid of all the malware except by erasing your hard disk. There's more malware written for Windows every day than there is detected by the world's anti-virus companies. Every day, the concept of "buy this anti-virus package and you'll be safe" gets more and more stupid.

---

### Post by Zill on 2013-06-09
HermanAB: The "Super Virus Scanner" sounds perfect.  Are there any volunteers who will package it up and put it in the Software Center? ;-)

---

### Post by Feathers McGraw on 2013-06-09
Hi all,

Isn't it worth mentioning that although there is relatively little risk to your own system, being able to scan files that you share with Windows users is useful so you don't inadvertently spread a virus, even if it can't affect you?

Also, a few viruses run with wine... [this thread](http://ubuntuforums.org/showthread.php?t=72598) is worth reading, even just for a laugh - someone ran a virus in wine just for the hell of it and filled his home folder with other viruses :rolleyes:.

So, I guess you won't mess up your whole system, but perhaps you could lose some data by being careless?

Anyone know whether opening a spreadsheet that contains a virus in Excel using wine would theoretically make your home directory vulnerable?

Feathers

---

### Post by DaveMcC on 2013-06-09
So, what AV would any one on here recommend ? I have a virus on this computer, think it came in via win8 on an auto update, which were turned off.................
Yes much and all as I hate win I need it for photo editing, gimp just ain't up to doing what I want, + ViewNX2 and CaptureNX2 don't run under ubuntu, see I NEED win , uh

Dave

---

### Post by Feathers McGraw on 2013-06-09
Try ClamAV, and if it doesn't work try something else!

This should get you started:

```

sudo mount /dev/sda2 /media/windows
sudo freshclam
sudo clamscan -r -i --bell --move=/home/<yourname>/infected /media/windows

```

Edit it so that your windows partition is in place of the "/dev/sda2" file path. Create the folders "/media/windows" and /home/<yourname>/infected" before you start.

It will mount your windows partition, scan it, and move any infected files from where they were into your home folder, where you can line them up like trophies :D.

Feathers

---

### Post by DaveMcC on 2013-06-09
Sooooooooo, after trying trying to install "ClamTK" I get the message Failed to download error no Internet  connection

---

### Post by DaveMcC on 2013-06-09
Wish I knew what all this means, but I don't
Tell you one thng, when I push or press on the - t min into panels, every thing disappears, firefox google earth, Terminal window etc
boss@Boss-desktop:~$ sudo mount /dev/sda2 /media/windows
[sudo] password for boss: 
mount: mount point /media/windows does not exist
boss@Boss-desktop:~$ sudo freshclm
sudo: freshclm: command not found
boss@Boss-desktop:~$ sudo clamscan -r -i --bell --move=/home/boss/infected /media/windows
sudo: clamscan: command not found
boss@Boss-desktop:~$ sudo mount /dev/sda2 /media/windows  sudo freshclam   sudo clamscan -r -i --bell --move=/home/boss/infected /media/windows
mount: unrecognised option '--bell'
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
boss@Boss-desktop:~$ 

Any help would be great

Dave

---

### Post by oldos2er on 2013-06-09
DaveMcC, I suggest you read post #11 again, particularly "Edit it so that your windows partition is in place of the "/dev/sda2"  file path. Create the folders "/media/windows" and  /home/<yourname>/infected" before you start." 

If you're still having trouble please start your own thread; "hijacking" someone else's thread is generally considered rude.

---

### Post by Feathers McGraw on 2013-06-09
You have to make the directories before or you'll be telling the computer to mount your windows partition somewhere that doesn't exist.

That's where your first error came from.

Also, take care when typing commands, I see you typed "sudo freshclm" instead of "sudo freshclam".

Feathers

---

### Post by DaveMcC on 2013-06-09
there in lays the problem with ubuntu, less than 1% of computer user's know what they are doing,
And who the hell allowed this crap computer to start auto-saving, it's just dam rude,

---

### Post by DaveMcC on 2013-06-09
Feathers McGraw
Thanks for your help,
Still don't know what I am doing, time to get ride of ubuntu, I suppose, all its been good for is reading my email, google, gumtree and little else
Dave

---

### Post by mastablasta on 2013-06-10
> **DaveMcC said:**
> Still don't know what I am doing, time to get ride of ubuntu, I suppose, all its been good for is reading my email, google, gumtree and little else


hehe if you knew what you were doing then you probably wouldn't get a virus in windows 8. ;-)

well if you realyl have a widnows virus and if it managed to evaide security you've put in place then clamtk likely won't find it. it's just not that good. try avira for linux maybe?

---

### Post by DaveMcC on 2013-06-10
hehehe, I use win8 for editing photo's in 64bit, as XP lay down due to the size of the photographs, one of them is 1gb in size
hehe dam win8 anto updated, hence the virus, never ever have been surfing the ww waste with win8
I am a photographer
Not a computer tech
Not a computer person, I hate computers
Not a world wide waster person
Not that other waste of time from the us-eh fluck-book or tweeter
As for avira, I see nothing here, just a blank stupid looking ubuntu software centre

---

### Post by Feathers McGraw on 2013-06-10
> **DaveMcC said:**
> there in lays the problem with ubuntu, less than 1% of computer user's know what they are doing


Actually, I'd say that Ubuntu is better for people who don't know what they're doing, because there's less scope for accidentally messing up the whole system.

I appreciate that you may need help setting things up initially, but after that... everything updates from one place and the software centre doesn't try and trick you into installing additional programs that spy on you and add themselves to your startup programs.

I switched my girlfriend from Windows 7 to Kubuntu because she has a habit of not actually reading on-screen messages and just clicking "yes"/"OK". I got fed up of cleaning her computer constantly, and guess what... since the switch I haven't had any hassle **at all**. Chrome no longer has a million toolbars, java and flash are always up to date and she can do everything she used to.

Chrome works.
Thunderbird works.
Dropbox works.
Libreoffice works.
GIMP works.

99% of computer users don't need or want anything more than this.

I very much doubt you got a virus **because** windows 8 automatically updated. If you had auto update turned off it's more likely that you got one because java/flash etc. weren't up to date and the virus used a known exploit.

Feathers

---

### Post by monkeybrain2012 on 2013-06-10
> **Feathers McGraw said:**
> Actually,


I very much doubt you got a virus **because** windows 8 automatically updated. If you had auto update turned off it's more likely that you got one because java/flash etc. weren't up to date and the virus used a known exploit.


Windows8 is the virus.:p

---

### Post by Bucky Ball on 2013-06-10
*Thread moved to **Security Discussions**.*

---

### Post by cariboo on 2013-06-10
I'm going to trump Bucky Ball, and move this thread where it belongs, Recurring Discussions, as this topic has been covered numerous times.

---

### Post by Bucky Ball on 2013-06-10
> **cariboo907 said:**
> I'm going to trump Bucky Ball, and move this thread where it belongs, Recurring Discussions, as this topic has been covered numerous times.

Happy with that. It was a toss up for me. ;)

---

