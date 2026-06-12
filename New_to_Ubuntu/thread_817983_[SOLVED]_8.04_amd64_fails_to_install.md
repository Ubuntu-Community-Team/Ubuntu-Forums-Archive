---
title: "[SOLVED] 8.04 amd64 fails to install"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by ednacalm on 2008-06-04
Firstly, I am new to Linux/Ubuntu, so please be gentle!
I am trying to install from the alternate CD as I would like to use my two HD's in a raid 0 array.
All goes well up to " select & install packages". At approx 85% get a failed installation message.
I have used the check disk integrity function on the cd, and all appears fine.
Any idea's...

---

### Post by ZabiGG on 2008-06-04
Could you provide the installation error message? That will help us help you.

You might also find information in the basic documentation. Click on the "Look here" link in my signature below. It's a good place to start.

Welcome to Ubuntu ;)

Z.

---

### Post by Sef on 2008-06-04
> Firstly, I am new to Linux/Ubuntu, so please be gentle!

If anyone is not gentle with you, please use the report button and a mod will deal with that person.

> I am trying to install from the alternate CD as I would like to use my two HD's in a raid 0 array.
All goes well up to " select & install packages". At approx 85% get a failed installation message.
I have used the check disk integrity function on the cd, and all appears fine.

Did you burn the iso at 4x or less?

---

### Post by ednacalm on 2008-06-05
I have burnt another cd at 4x and used an iso from a different source.
The result is the same.  The exact message is as follows:
"[!!] Select and install software
      Installation step failed

An installation step failed..."

The only option is continue, which brings the same message even when pressed repeatedly. The space bar returns you to the Ubuntu installer main menu.

---

### Post by chrisdugdale on 2008-06-05
Only thing I can think of is checking the file you downloaded. IE did you check the MD5SUM on the .iso files, and then make a cd then boot from the Live CD and run the cd check first? Sounds like you might have. Burning a cd should always be at the lowest speed as ednacalm says, but the MD5SUM needs to be right. I'm not sure if Ubuntu supports the RAID 0 array. You might need to switch it off in your Bios????

---

### Post by hyper_ch on 2008-06-05
did you check the cd for defects? You can do that at the boot up screen.

---

### Post by Efros on 2008-06-05
I encountered similar problems and found that using the alternate AMD64 CD solved it and allowed me to install faultlessly.

---

### Post by chrisdugdale on 2008-06-05
Efros has a good point. The desktop and server editions assume a decent internet connection. And the alternate edition does get onto more pc's easily. At about 85% it sounds like downloads may be happening or failing. Any chance your ISP blocks this? It may not go well on a dialup modem, Ubuntu assumes you have a broadband connection. Dialup modems can be installed later, or some of them anyway.

---

### Post by ednacalm on 2008-06-05
I have checked both cd's and they both come up ok.
Raid has being swicthed off in bios
I followed the "Installation/SoftwareRaid" docs from help.ubuntu.com/community.
These suggest raid0, raid1 and raid5 are ok
Following the screen, it appears to partition disks, install base system, atp,
then crash's. From memory, i think the next step is to install the bootloader.
I have successfully install from the live cd without raid, which suggest's the problem is either the alternate cd, or raid0.
I do alot of video editing & dvd authoring and back in the dark days of XP, raid0
did make a difference speed wise hence not giving up easily!

---

### Post by ednacalm on 2008-06-05
Have braodband which install programs finds oh

---

### Post by ednacalm on 2008-06-06
Problem solved - Installed Fedora 9

---

