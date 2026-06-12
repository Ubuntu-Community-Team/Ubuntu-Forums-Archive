---
title: "Ubuntu 11.04 antivirus"
date: 2011-07-06
forum: Recurring Discussions
---

### Post by sstextile on 2011-07-06
Please tell me anti-virus for Ubuntu 11.04.

---

### Post by dFlyer on 2011-07-06
Not really required for linux. Should you like to use, just start synaptic and search antivirus.

Antivirus for linux is only to protect your windows friends while exchanging files.

---

### Post by wildmanne39 on 2011-07-06
> **sstextile said:**
> Please tell me anti-virus for Ubuntu 11.04.
Hi, you can use clamav

[http://clamtk.sourceforge.net/index.html](http://clamtk.sourceforge.net/index.html)

update the virus database use the command 

**sudo freshclam**

this is run from the terminal.

---

### Post by mcduck on 2011-07-06
For what kind of system?

Ubuntu itself isn't vulnerable to viruses, and in general the only reason to run an antivirus on a Linux system is if you are running an e-mail server or gateway for lots of Widnows computers and wish to move the load of virus scanning to the server instead of running the scanner on each desktop machine.

---

### Post by nomko on 2011-07-06
There's no need to be afraid of virusses (and malware to) for Linux. Although there are some virusses around which are specifically "designed" for Linux, the change to get them are very small. The reason for not being afraid for infected is mainly due to the better security managament system of Linux compared to Windows. Each and every program which is getting installed on a linux-based system requires a root account or root priviliges, as in Ubuntu you need to enter your user password in oder to get root priviliges to install programs. This is the first obstruction a virus "designer" (better to say script kiddy's) to bypass which is more or less almost impractical due to the reason that the virus has to  figure out which password it requires to gain root priviliges itself. Then there has to be a way to figure out how to get access to certain folders in which a normal user doesn't have any access to it. I think you get an idea now of why linux is much more secure for virusses then Windows.
 
However, keep in mind that when yopu recieve an infected file by mail or from an external disc/drive, that the infected file will be saved in such way that the structure of that infected file will not altered. This means that if you pass on that infected file to a Windows user, the system of that user will get infected. Under Linux you won't experience any negavtive influences of that infected file.
 
So, if you exchange a lot of files with a Windows user, you might consider to use ClamAV. There are other program's available but the main advantage of ClamAV compared to the others is the fact that ClamAV can also scan drives/disc which are formatted with a Windows fileformat (like FAT16/32 or NTFS).

---

### Post by beew on 2011-07-06
Like other say you don't really need an AV but if you must get one get a real one like bitdefender or Avast. ClamAV is a joke, it is a complete waste of space and cpu cycles.

---

### Post by createdcreature on 2011-07-06
I have used Linux for a year now and have never got a virus.

---

### Post by alphacrucis2 on 2011-07-06
Even in Linux you still need to be careful. Recently the gnome-looks site which provides community produced themes for download had a malicious user upload a "theme" which was in the form of a deb installer. The deb had code embedded in it to erase the root file system. Just download and install this cool theme and it will bork your system. One of our forum members got caught out by this and posted about it in the community cafe to warn others. The gnome looks admins took the offending theme down fairly quickly and banned the user who uploaded it but just shows anybody can be vulnerable to what is a form of social engineering. Be vigilant.

---

### Post by nomko on 2011-07-06
> **beew said:**
> ClamAV is a joke
 
But it is the only "joke" who can also scan Window formatted drives/disks.

---

### Post by Swagman on 2011-07-06
> **nomko said:**
> But it is the only "joke" who can also scan Window formatted drives/disks.

I'm pretty sure Avast for Linux scans NTFS drives but a scan has to be manually started

---

### Post by nomko on 2011-07-06
> **Swagman said:**
> I'm pretty sure Avast for Linux scans NTFS drives but a scan has to be manually started
 
Just looking at the site and i can't see where it is stated that Avast also can scan Windows formatted drives: [http://www.avast.com/linux-home-edition#tab1](http://www.avast.com/linux-home-edition#tab1)

---

### Post by mikenev on 2011-07-06
There was a decent article about Linux antivirus in the Ubuntu Docs:
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by Jerry N on 2011-07-06
> **Robert Moyse said:**
> I have used Linux for a year now and have never got a virus.

I have used Windows since version 3.0 (20 years?) and have never gotten a virus.

Jerry

---

### Post by nomko on 2011-07-07
> **Jerry N said:**
> I have used Windows since version 3.0 (20 years?) and have never gotten a virus.
 
Jerry
 
20 years ago you didn't had internat at home, did you? ;)
In all these years i've used Windows (from WfW 3.11) till XP (up to 2007) i got 1 virus but a hundred times more malware. I recon that most problems on Windows systems aren't virusses but malware. And since most users aren't really that knownledgeable about Windows and the internet and computers, they easily point their fingers towards malware and claiming that it is a virus.

---

### Post by uRock on 2011-07-07
> **Jerry N said:**
> I have used Windows since version 3.0 (20 years?) and have never gotten a virus.

Jerry

The last Windows using friend I had make that claim wept when he broke down and installed an AV. It had a hay day and managed to ruin his system trying to remove them all.

BitDefender has a nice free AV, which can be found here [https://help.ubuntu.com/community/BitDefender](https://help.ubuntu.com/community/BitDefender)

Moved to recurring discussions.

---

### Post by haqking on 2011-07-07
> **nomko said:**
> 20 years ago you didn't had internat at home, did you? ;)
In all these years i've used Windows (from WfW 3.11) till XP (up to 2007) i got 1 virus but a hundred times more malware. I recon that most problems on Windows systems aren't virusses but malware. And since most users aren't really that knownledgeable about Windows and the internet and computers, they easily point their fingers towards malware and claiming that it is a virus.


oh i dunno, Compuserve was my ISP back in the early 90's, i think they started in late 80's....there first client was DOS based.....compuserve online forums with the infamous compuserve sysops ;-)

oh i feel old !

---

### Post by nomko on 2011-07-07
> **haqking said:**
> compuserve
 
Do they still exist? I haven't seen any advertisment of them lately.. I could be wrong.

---

### Post by handy on 2011-07-07
I haven't read the thread, so my apologies for restating what has already been said.

If you are NOT serving files to Windows machines, then you don't need to run antivirus software on Linux.

This is a good read on the topic:

[http://librenix.com/?inode=21](http://librenix.com/?inode=21)

---

### Post by Jerry N on 2011-07-07
> **uRock said:**
> The last Windows using friend I had make that claim wept when he broke down and installed an AV. It had a hay day and managed to ruin his system trying to remove them all.

BitDefender has a nice free AV, which can be found here [https://help.ubuntu.com/community/BitDefender](https://help.ubuntu.com/community/BitDefender)

Moved to recurring discussions.

I've been using antivirus and antimalware software for years.  Besides hiding behind a hardware firewall (router) I also use Zonealarm for my Windows firewall.  I'm also careful about what I open and I don't install just any old software on my computer.  

I help some elderly folks with their computer problems (some of those folks are older than I am!) and have seen and fixed quite a few malware problems.  My current approach is the "scorched earth" method, ie completely reinstall their operating system.  Of course I have to create backups when I do that because none of them understands the concept of backups.  (I assume that everyone on these forums is fully backed up at all times.  Yeah riiiiiight!)  I have offered to install Linux on a few of these computers and have even given Linux demonstrations but haven't had any takers.  I haven't been pushy about it.  And won't be!

Jerry

EDIT:  BTW, I hardly ever cry about reinstalling an operating system.  To me that comes under heading of "no big deal".

---

### Post by Ric_NYC on 2011-07-07
If you really need an antivirus install Windows.

---

### Post by nrundy on 2011-07-13
> **Swagman said:**
> I'm pretty sure Avast for Linux scans NTFS drives but a scan has to be manually started

I tried installing Avast on my ubuntu box. I could never get it to work.

I wrote to Avast asking them what is wrong. Their response made me laugh. 

I'm paraphrasing but essentially they said, "Linux has no viruses in the wild. So basically the linux version of avast receives no attention from us and hence doesn't really work."

---

### Post by wolfen69 on 2011-07-15
ClamAV is garbage.

---

### Post by rbowen1 on 2011-07-15
> **nomko said:**
> Just looking at the site and i can't see where it is stated that Avast also can scan Windows formatted drives: [http://www.avast.com/linux-home-edition#tab1](http://www.avast.com/linux-home-edition#tab1)


Avast for Lunix will definitely scan Windows formatted NTFS drives.   Personal history:   Being a careful person, I removed my hard drive that had Windows XP.  Installed a new hard drive and loaded Natty.    Reconnected the Windows drive that is an NTFS volume.      Since I do share files with windows users, I installed Avast for Lunix.     Avast has daily updates and scans the NTFS volume quite well.  Avast has a quick, standard or thorough selection.    Avast install fix available on this thread: [http://ubuntuforums.org/showpost.php?p=9512526&postcount=9](http://ubuntuforums.org/showpost.php?p=9512526&postcount=9)

---

