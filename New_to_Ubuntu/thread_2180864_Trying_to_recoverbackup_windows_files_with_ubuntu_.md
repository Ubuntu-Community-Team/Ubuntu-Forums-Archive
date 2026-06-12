---
title: "Trying to recover/backup windows files with ubuntu 8.04 CD"
date: 2013-10-15
forum: New to Ubuntu
---

### Post by UKPA2006 on 2013-10-15
Long story short, windows will not load at all on my desktop due to massive master boot record issues. Not sure what happened, but I just want to get to and back up some of my files before I wipe my hard drive clean and reinstall windows. I found a good walk through of how to use ubuntu CD to get to my files and back them up the guide is here: [http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/). However, I can only get halfway through and encounter a problem not addressed on the guide. First let me say, I know nothing about ubuntu/linux; tonight was the first time I have ever even loaded it up on my computer. I have ubuntu 8.04, I loaded it in my cd drive and boot it up and chose "try ubuntu without any change to your computer" When Ubuntu loaded I was told by the guide I was using to go to "Places" then click on "computer". There I see all my drives. The guide tells me to double click on my media drive which for me says "34.4 GB Media"(which I find odd since the hard drive is a 256 GB drive. Is it only showing the used amount?) and the guide says if I'm lucky, the drive will open and I can get to my files, or if I'm unlucky, it will say there is a mount error. Well, when I double click my drive it opens and I get an icon that looks like a gray square on turned on it's point (and it had a picture of an orange lock on it which has now disappeared after running a few commands in the terminal that the guide listed) and the icon is labeled "ie÷22%03±[SIZE=2]&#8376;.)r)". When I double click this icon it originially said "couldn't display [file:///media/disk/ie÷22%03±&#8376;.)r)](file:///media/disk/ie÷22%03±&#8376;.)r))  no application installed for this file type" However after the lock on the icon disappeared when I tried to double click the icon it now says "couldn't display [file:///media/disk/ie÷22%03±&#8376;.)r)]("file:///media/disk/ie÷22%03±&#8376;.)r") the location is not a folder". I'm not sure where to go from here. I really need to get into this drive and backup some files. Please can anyone help me from this point? I would really appreciate it![/SIZE]

---

### Post by mastablasta on 2013-10-15
8.04 is an old and unsupported version from 2008. use 12.04 LTS at least (or if computer is old use Xubuntu 12.04 instead).

it doesn't seem to me like the master boot record is the only thing that is corrupted there. What windows are they? you can repair the master boot record (using the window install media) and for NTFS filesystem that windows uses it might be good to use it's chkdsk (check disk) to check the disk and repair the errors. normally to repair windows file errors it's best to use windows tools. if windows tools are absolutelly out of the quesiton you can try and recue with Ubuntu as much as you can.

---

### Post by barrings on 2013-10-15
Hello,
This is a wierd situation.  I am no expert, but I think that the problem may have something to do with Ubuntu not able to determine where your windows files are located due to your MBR problem.  The MBR tells the computer where Windows is stored, and if the computer doesn't know, how can Ubuntu?  I disagree with MastaBlasta here that a newer version of Ubuntu will somehow fix the problem where Hardy couldn't (since you're new to Ubuntu, that's what Ubuntu people colloquially call 8.04--Hardy Heron was it's code name during development, and people shorten it to Hardy as a kind of nick-name).  The operation we're dealing with (opening another drive) is such a basic operation that the version of Ubuntu is irrelevent.  Besides, Hardy is only 5.5 years old, after all (The version comes from the year and month 8.04=released in April, 2008) and by then we had pretty good HDD access protocols.  

Going along with what MastaBlasta said, if you have a copy of Windows (I assume its Windows 7?) try the process at [http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html") which may be of help.  Instead of backing up your files, wouldn't it be better to cure the heart of the problem?

I hope that helps somewhat.

barrings

---

### Post by Mark Phelps on 2013-10-15
A filename like that tends to indicate that either (1) the windows filesystem is corrupted (in which case, Ubuntu would not have mounted the partition), or (2) the hard drive is failing and your encountering bad clusters as a result.  My bet would be the latter.

If you have access to another Windows PC and are willing to spend some money to recover some files, read on ...

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from [http://getdata.com](http://getdata.com).
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to their website, you can compare versions and features.

Your data ... your money ... your choice.

---

### Post by mastablasta on 2013-10-15
windows 7 is from 2009 while hardy is from 2008 (developed even earleir) and it might not knwo all features of win7. i do not know. which is why i recomenbved laetst 12.04. 

anyway problem 1 filesystem corrupted described by Mark can possibly be solved by runnig chkdsk in repair console (from install disk). 
MBR can be repaired by runnig appropriate programme in windows 7 recovery console.


either way it seems linux can't help much unless you manage to repair and then you can access it from linux and move the data (if you do not trust windows)

---

### Post by UKPA2006 on 2013-10-19
I actually have Windows Vista on my PC. It's so wierd because I've never had a virus on my computer, I only go to safe sites on the net, and I also use several cleanup/anti malware programs, so not sure what has happened to cause my pc problem. (Really I would love to throw in the factory disk and start all over reinstalling windows. The only problem is there are just a few files that I do not have a backup copy of anywhere and they are important files and a few important pictures that I REALLY don't want to lose forever as they cannot be replaced.) 

Mostly my hubby has been working on fixing this issue, so I can't tell you every detail that has happened. I think he however is about to give up trying. He has talked to numerous people regarding windows/other types of fixes and each time we try something we seem to get a little closer so everyone tells us not to give up, but they also say I have a very bad problem and it's going to take a major expert to fix, which we can't seem to find anyone with that knowledge who can take the time to help as much as I need. We did however buy a sata hard drive enclosure, put my hard drive in there and plugged it into my husbands laptop (windows vista also) to try to open my drive and get those couple files to back them up. The hard drive was recognized on his computer, but it would never completely load in order to open up the drive and get to the files. While plugged into my hubby's pc he ran antivirus scan and some anti-malware scans (all came up clean, nothing found), he also ran chkdsk and scan disk which did not work correctly. He also tried to repair the master boot records using [COLOR=black][FONT="Verdana"]BOOTREC /REBUILDBCD[/FONT][/COLOR] at the command prompt before he removed the hard drive from my PC but it always says "that the total ammunt of windows installations found was: 0" People in other forums I've looked through have had this same problem and ended up fixing it, but I can't get a clear guide, that is trusted and makes sense enough to fix it. I am very good at minor computer repairs, but this stuff is getting to be over my knowledge base.

I did tonight make a boot cd, an ubuntu live cd, since it was suggested my ubuntu 8.04 may be too old. When I used the new boot cd I can get to the ubuntu screen and choose to "try ubuntu without any change to your computer" However after I choose that ubuntu tries to load up and I end up at a black dos-like screen that says 
"BusyBox V1.18.5 (Ubuntu 1:1.18.5-1ubuntu4.1) built in shell (ash)
Enter 'help' for a list of built in commands
(initramfs) Unable to find a medium containing a live file system"

This I find odd since 8.04 loaded up just fine. Although as I have stated, I know nothing about ubuntu. I think my next move will be to look into the trial version of RecoverMyFiles as suggested in one of the replies. Any further suggestions? Thanks for the help you've all given so far too!

---

### Post by Johan De Cauwer on 2013-10-19
Well, it may be that Ubuntu doesn't load because of graphical issues and in that case you could try Xubuntu as suggested. And there is a distribution called SystemRescueCD, see [http://www.sysresccd.org/SystemRescueCd_Homepage](http://www.sysresccd.org/SystemRescueCd_Homepage) that handles recovery but perhaps requires some expertise. And lastly - the labels you posted on the first post possibly point to the use of an encrypted file system. So don't 'repair' that or you risk losing data.

---

