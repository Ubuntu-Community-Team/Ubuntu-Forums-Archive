---
title: "No Security Updates In Over A Week"
date: 2017-12-28
forum: New to Ubuntu
---

### Post by musiclover-mm on 2017-12-28
Hi,

I have Lubuntu Linus 4.4.104 Generic i686 running Ubuntu 16.04.3 LTS running on a 32 Bit Dell Inspiron 530S (hey - it is still running great. I know I know I know...yes I am looking into new hardware.)

As Title states, I have had no automatic security updates in about 10 days. My automatic updates are turned on to "Daily".
The last automatic update I downloaded was for the system not security. I have been trying to find a way to generate a report detailing last update so that I could uninstall it.

I have tried to generate an update report in Sys Pkg Mgr; "History" and get no results. Also tried :"Software Updater" in Sys Tools to try and get Security updates but also get no results.

Tried "Synaptic Pkg Mgr" ""Fix Broken Pkgs" also getting no results. 

What I did get from Syn Pkg Mgr are these two reports:

The repository 'cdrom://Lubuntu 16.04 LTS _Xenial Xerus_ -
Release i386 (20160420.1) xenial Release' does not have a Release file.
Data from such a repository can't be authenticated and is therefore potentially
dangerous to use.See apt-secure(8) manpage for repository creation and user
configuration details.
Failed to fetch cdrom://Lubuntu 16.04 LTS _Xenial Xerus_ - Release i386 
(20160420.1)/dists/xenial/main/binary-i386/Packages 
Please use apt-cdrom to make this CD-ROM recognized
 by APT. apt-get update cannot be used to add new CD-ROMsSome index files
failed to download. They have been ignored, or old ones used instead.

(I was not using the CD-Rom)

Also Ran IN Syn Pkg Mgr :

 (Reading database ... 373561 files and directories currently installed.)
Removing alarm-clock-applet (0.3.4-1) ...
Purging configuration files for alarm-clock-applet (0.3.4-1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
(Reading database ... 373492 files and directories currently installed.)
Removing bleachbit (1.10-1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...

(Yes I downloaded Bleach Bit! I have uninstalled it. This is the beginners forum!)

 I have done a lot of reading of forums and tutorials and have just gotten more confused. Correct me if I am wrong, I am trying to generate a report that shows the last download from Ubuntu so that I can uninstall it. Do you have a better idea of what I need to do, and how to do it.

Thank you very much.

---

### Post by Holger_Gehrke on 2017-12-28
There's a full log of all package management activities in /var/log/apt/history.log (and the older, compressed logfiles history.log.1.gz to history.log.10.gz. The newest entries are at the end of the history.log.

Holger

---

### Post by musiclover-mm on 2017-12-28
Thank you so much Holger. I'm on it!

---

### Post by musiclover-mm on 2017-12-28
Alright, so I entered into my Terminal:

/var/log/apt/history.log

The msg I received is: bash:  /var/log/apt/history.log; Permission denied. 

This is what I entered for the older compressed log files. (no period (.) after gz? I thought is was the end of your sentence punctuation. I'll try with a period. --- Nope, not that either.

-Inspiron-530s:~$ history.log.1.gz to history.log.10.gz
history.log.1.gz: command not found

Have I misunderstood something? Do I need to sudo first to establish root permission? (remember I am new.)

Thanks again.

---

### Post by deadflowr on 2017-12-28
The last security update was on the 18th of December.
You can keep abreast of security updates here: [https://usn.ubuntu.com/usn/]("https://usn.ubuntu.com/usn/")

> Alright, so I entered into my Terminal:

/var/log/apt/history.log

The msg I received is: bash: /var/log/apt/history.log; Permission denied. 

This is what I entered for the older compressed log files. (no period (.) after gz? I thought is was the end of your sentence punctuation. I'll try with a period. --- Nope, not that either.

-Inspiron-530s:~$ history.log.1.gz to history.log.10.gz
history.log.1.gz: command not found

Have I misunderstood something? Do I need to sudo first to establish root permission? (remember I am new.)


Use cat, tail head, or other like
```
cat /var/log/apt/history.log
tail /var/log/apt/history.log
head /var/log/apt/history.log
```
cat will output the whole file
tail will output just the last section, or end of the file
head will output  the first section, or beginning of the file

To do the same for .gz files use zcat.
Note that the .gz files are simply older archives of the history and won't show whatever the latest updates are.

---

### Post by musiclover-mm on 2017-12-28
Thanks so much Robot Pirate Ghost. The explanations for cat, tail, head make so much sense. 

I'm onto it.

Nope. bash: /var/log/apt/history.log: Permission denied

Did it properly:

Commandline: aptdaemon role='role-commit-packages' sender=':1.30'
Upgrade: ca-certificates-java:i386 (20160321, 20160321ubuntu1), libnm-glib4:i386 (1.2.6-0ubuntu0.16.04.1, 1.2.6-0ubuntu0.16.04.2), libgweather-3-6:i386 (3.18.2-0ubuntu0.1, 3.18.2-0ubuntu0.2), libnm0:i386 (1.2.6-0ubuntu0.16.04.1, 1.2.6-0ubuntu0.16.04.2), network-manager:i386 (1.2.6-0ubuntu0.16.04.1, 1.2.6-0ubuntu0.16.04.2), initramfs-tools-bin:i386 (0.122ubuntu8.9, 0.122ubuntu8.10), libnm-util2:i386 (1.2.6-0ubuntu0.16.04.1, 1.2.6-0ubuntu0.16.04.2), distro-info-data:i386 (0.28ubuntu0.5, 0.28ubuntu0.6), libgweather-common:i386 (3.18.2-0ubuntu0.1, 3.18.2-0ubuntu0.2), initramfs-tools-core:i386 (0.122ubuntu8.9, 0.122ubuntu8.10), initramfs-tools:i386 (0.122ubuntu8.9, 0.122ubuntu8.10)
End-Date: 2017-12-22  11:33:48

Start-Date: 2017-12-27  09:16:07
Commandline: /usr/sbin/synaptic
Requested-By: musiclover (1000)
Remove: bleachbit:i386 (1.10-1)
Purge: alarm-clock-applet:i386 (0.3.4-1)
End-Date: 2017-12-27  09:16:19

Now what do I have to fix. Someone wrote that they never ever download anything but security updates for Ubuntu. Is that wise? I had a funny feeling about the last one but went ahead anyway. What did I do to my sys bcse I don't understand the code I downloaded. 

Thanks.

---

### Post by mörgæs on 2017-12-28
> **musiclover-mm said:**
> 
I am looking into new hardware.

No need to hurry. I and many other people here run Lubuntu on less powerful gear than yours.

> **musiclover-mm said:**
> 
As Title states, I have had no automatic security updates in about 10 days. 

Happens every year around Christmas. Developers are less active now, both employed ones and volunteers. Point for being aware of the importance of daily updates.

---

### Post by musiclover-mm on 2017-12-28
There have been no security updates for Ubuntu LTS (Lubuntu 16.04 LTS) since Dec 15 so it looks like I have been worried over nothing.

I guess you are simply seeing the panic sweat of a former Windows user. 

If I am wrong, plse advise. Otherwise I wish nothing for you but the best New Year ever and also for the Ubuntu/freeware community.

---

### Post by musiclover-mm on 2017-12-28
The reason I want new gear is that I believe the hype that Ubuntu is better, easier. I love my Dell Inspiron dual core, but I also love British TV and am stuck on the North American Continent where the idea of BBC Canada is 10 hours of Holmes on Holmes every day which we used to watch for free on our local channels.
There are more options for a 64 bit sys, and more coming every day. It just seems prudent to upgrade. My motherboard is permanent so I can't upgrade this beautiful little sys.  I can buy a $160.00 mini running SSD and have new worlds open up to me. I'd like that. Being poor sucks but my integrity is pretty much intact, and my ability to create and innovate for myself is working just fine.

I love and appreciate Lubuntu/Ubuntu. I am fortunate that I am old enough to have had to learn advanced LOTUS 1-2-3 back in the day when you had to write your own macros. I really really resented MS supposed "intuitive" intrusion in my life when Corporations all went MS on the west coast. That learning curve I don't wish on anyone familiar with logic and basic DOS.

Anyhow, enough about me. Thanks Holger, Deadflowr and Morgaes. Really.

---

### Post by deadflowr on 2017-12-28
> Now what do I have to fix. Someone wrote that they never ever download anything but security updates for Ubuntu. Is that wise?
You can, but those updates will keep piling up.
In the event that you want to install some package that require an updated package that has been sitting in the update queue for a while might make you need to apply those updates, which can then becomes a rather long update process, as opposed to simply running the updates periodically (once a week or perhap once every two weeks, should suffice)

---

### Post by musiclover-mm on 2017-12-28
Okay. Got it.

I have been looking for the "Solved" option to flag my post as I am a stickler for rules. How do I do that? 
I am taking advantage of the fact you are a moderator.

Thanks.

---

### Post by deadflowr on 2017-12-28
click on  Thread Tools and then click on the Mark this thread as Solved
(Thread tools is right above the very first post, on the right side area)

---

### Post by mörgæs on 2017-12-28
> **musiclover-mm said:**
> There are more options for a 64 bit sys

You already have 64 bit.

---

### Post by oldos2er on 2017-12-28
Developers are people too; I'm sure they'll return once the holidays are over.

---

### Post by musiclover-mm on 2017-12-28
Oh. You mean that my Ubuntu "software" is um, 64 bit light, programmed for my 32 bit sys?

> **mörgæs said:**
> You already have 64 bit.

morgas

Oh.
Do you mean that my Ubuntu "software" is um, 64 bit light, programmed for my 32 bit sys? I had not considered that. if that is in fact what you are telling me.

oldos2er,

I had not considered the holiday situation. These are the cold detox sweats of an ex-Windows user.

Thanks for your reply. I hope all the programmers have a spectacular holiday.

---

### Post by mörgæs on 2017-12-28
I mean that your hardware is 64 bit, able to support a 32 or 64 bit operative system.

---

### Post by ajgreeny on 2017-12-28
> **musiclover-mm said:**
> I love and appreciate Lubuntu/Ubuntu. I am fortunate that I am old enough to have had to learn advanced LOTUS 1-2-3 back in the day when you had to write your own macros. I really really resented MS supposed "intuitive" intrusion in my life when Corporations all went MS on the west coast. That learning curve I don't wish on anyone familiar with logic and basic DOS.

Anyhow, enough about me. Thanks Holger, Deadflowr and Morgaes. Really.
Gosh. Lotus 1-2-3 is what I used from 1998 onwards until 2005 when I began using Ubuntu and OpenOffice; it was from a computer-magazine give-away version of Lotus-Smartsuite-97, and I loved it, along with all the other applications it provided, so I was rather lost when my work provided Microsoft Office-97 for me, and I could never get as comfortable using it as I was using Smartsuite.

I still have many of the old files from that Lotus office suite sitting on my hard disk, all of which still open with LibreOffice or gnumeric, but not abiword.

I really liked Smartsuite and often wondered why it did not do better than it did, but I suppose that is the ubiquity of Microsoft, meaning there is just no niche for the alternatives.  A real pity but that's life!

---

### Post by musiclover-mm on 2017-12-28
> **mörgæs said:**
> I mean that your hardware is 64 bit, able to support a 32 or 64 bit operative system.

I took your word for it and looked in my sys.

Inspiron-530s:~$ lscpu
**Architecture:          i686**
**CPU op-mode(s):        32-bit, 64-bit**
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 23
Model name:            Intel(R) Core(TM)2 Duo CPU     E7400  @ 2.80GHz

Still confused by the CPU op-mode info I googled "is intel i686 64 bit?" and got this:
> 
Today some systems have dropped support for processors without all the features covered by the **i686** term. AMD64 is the name of a **64 bit architecture** designed by AMD to succeed x86 . At the time AMD64 managed to be more successful than the **64 bit architecture** marketed by **Intel**.Jul 5, 2014



So all my worrying and stressing has been a simple lack of knowledge? Wow. When I asked "Properties" on my Win Vista I guess it told me it was 32 bit *software? *Wow again. That really makes me want to jump up and down and swear a lot.

---

### Post by musiclover-mm on 2017-12-30
Thanks again morgaes. Cripes!

The things that scare me most about being fully responsible for my own sys are the things that I do not know (how to do). 
I tried learning Linux from the edEx course and online videos. They should be used for insomniacs. I learn best by doing and don't want to blow up my sys by doing uninformed things. But hey...I'll throw my control issues to the wind and learn like everyone else.

Have a great day.

---

### Post by mörgæs on 2017-12-31
Here's something to get you started:

[https://ubuntuforums.org/showthread.php?t=2130640](https://ubuntuforums.org/showthread.php?t=2130640)

Good luck.

---

