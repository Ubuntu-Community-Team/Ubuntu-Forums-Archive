---
title: "Dual Boot questions."
date: 2014-06-21
forum: New to Ubuntu
---

### Post by gordon99 on 2014-06-21
I have a couple of questions that prove I am an absolute beginner, if anyone has any doubt, but I would be very pleased to receive answers to increase my knowledge.
I have installed Ubuntu 14.04, dual booting with Windows 7. I notice that, in Ubuntu, folders etc. which are in Windows "C" drive are shown as being located in "/media/username". Why are they not shown in their correct Windows location when viewed in Uuntu?
My second question relates to my "/data" partition and it is this. Is it possible to move a program out of its location in WIndows and into "/data" partition so that it can be run from both Windows and Ubuntu? I know that many Windows programs will not run in Ubuntu but I was thinking of programs that can be run in both OSs.

---

### Post by oldos2er on 2014-06-21
The "correct" Windows' location doesn't exist in Linux, which uses a very different [file system hierarchy]("https://help.ubuntu.com/community/LinuxFilesystemTreeOverview").

No Windows programs will run natively in Linux, but a few may run with Wine, and as far as I know, such programs must be installed through Wine and can't be run from other partitions. I'm pretty far from being a Wine expert though.

---

### Post by Mark Phelps on 2014-06-21
>  Is it possible to move a program out of its location in WIndows and into "/data" partition so that it can be run from both Windows and Ubuntu? I

NO -- the same program can not be run BOTH in MS Windows and in Linux.  You have to reinstall any Windows app you want to run -- using Wine.

And, before you charge into doing that, save yourself some grief and look up the app and version on the WineHQ website.  Anything not listed, or rated lower than Gold, is going to be a waste of your time installing: [http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

---

### Post by oldfred on 2014-06-21
But you can share data.
Best to use a separate NTFS formatted data partition.

I share Firefox & Thunderbird profiles and use Windows Picasa in both systems, with Picasa in .wine. Not quite all of Picasa's on line features work.

---

### Post by gordon99 on 2014-06-21
Thanks everyone. That makes things a lot clearer. My "/data" partition is ntfs format. I am having trouble installing Wine but that is another question I have posted.

---

### Post by PondPuppy on 2014-06-21
Just a very brief note for clarity: Some programs are made to "run in Windows, Linux, or Mac" -- but usually that means they're offered in separate versions, each rewritten for the specific OS listed.

---

