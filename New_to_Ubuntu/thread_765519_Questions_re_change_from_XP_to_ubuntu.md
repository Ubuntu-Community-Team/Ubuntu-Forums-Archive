---
title: "Questions re change from XP to ubuntu"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by digf on 2008-04-24
Hello Forum
I've used XP for nearly four years now and been quite happy with it but I don't like the prospect of being forced into paying for microsofts newest operating system when support for XP finishes. I like the idea of Linux from what I have read about it and am considering installing ubuntu, initially as a dual boot with XP until I get more experienced and then probably use ubuntu as the only system. The reason I have chosen that is simply because it appears, from my limited knowledge to be the most used Linux system. 
I have several questions if someone would be good enough to give me answers to them.
1. I currently use Yahoo for email and for its calender, would I be able to continue that with ubuntu?
2. I have read that Linux is more secure than Windows. Is that correct and if so why? I do online banking and am wondering about the security with Ubuntu. I currently have Zone Alarm Security Suite and several anti spyware programs. Is good security available for Linux?
3. My hard disc is 120 Gig. I am thinking of making into three roughly equal partitions, if thats possible, with XP on one. UBuntu on anther, the third I would use for keeping photo's and files on from both systems, which would allow me to reformat and reload the two operating systems if I wanted to without losing photo's etc. Is that possible?

Thanks in advance
digf

---

### Post by 1440 on 2008-04-24
1. Depends. You can use webbased versions of Yahoo! mail and Calendar. You won't be able to run Windows applications on Linux without using programs like [Wine]("http://en.wikipedia.org/wiki/Wine_(software)") or [VMWare]("http://en.wikipedia.org/wiki/VMware_Workstation").

2. Linux is inherently more secure than Windows, even without special security software, for far more reasons than I can think of right now. There are virtually no viruses or spyware programs that you have to worry about when running Linux.

3. Yes, it's possible. Please consult the online documentation on how to do this. [This page]("https://help.ubuntu.com/community/Installation") and the pages it links too probably have all the information you need.

Good luck! :)

---

### Post by Mazza558 on 2008-04-24
> **digf said:**
> Hello Forum
I've used XP for nearly four years now and been quite happy with it but I don't like the prospect of being forced into paying for microsofts newest operating system when support for XP finishes. I like the idea of Linux from what I have read about it and am considering installing ubuntu, initially as a dual boot with XP until I get more experienced and then probably use ubuntu as the only system. The reason I have chosen that is simply because it appears, from my limited knowledge to be the most used Linux system. 
I have several questions if someone would be good enough to give me answers to them.
1. I currently use Yahoo for email and for its calender, would I be able to continue that with ubuntu?
2. I have read that Linux is more secure than Windows. Is that correct and if so why? I do online banking and am wondering about the security with Ubuntu. I currently have Zone Alarm Security Suite and several anti spyware programs. Is good security available for Linux?
3. My hard disc is 120 Gig. I am thinking of making into three roughly equal partitions, if thats possible, with XP on one. UBuntu on anther, the third I would use for keeping photo's and files on from both systems, which would allow me to reformat and reload the two operating systems if I wanted to without losing photo's etc. Is that possible?

Thanks in advance
digf

1. Yes (If you mean the web version)
2. For everyday use, you don't need any anti-spyware/antivirus on Ubuntu.
3. Easily.

---

### Post by digf on 2008-04-24
Wow what a quick response, thank you 1440 and Mazza558. I'm looking forward to being a part of this.

---

### Post by Mazza558 on 2008-04-24
> **digf said:**
> Wow what a quick response, thank you 1440 and Mazza558. I'm looking forward to being a part of this.

No problem. The experienced members here are being extra-helpful with people just starting out.

---

### Post by Paqman on 2008-04-24
Hi, welcome to the forums. I dual-boot Ubuntu and XP myself. Rest assured it isn't hard to do and works well. XP is good at some things (eg: games) and Ubuntu is fantastic at everything else. Best of both worlds.

> **digf said:**
> 
1. I currently use Yahoo for email and for its calender, would I be able to continue that with ubuntu?


Absolutely. Yahoo is web-based, so will work with any operating system. I use gmail and their calendar myself.

> 
2. I have read that Linux is more secure than Windows. Is that correct and if so why? I do online banking and am wondering about the security with Ubuntu. I currently have Zone Alarm Security Suite and several anti spyware programs. Is good security available for Linux?

What you've heard is true. Linux security is vastly superior to Windows. There's a reason why most of the internet's hardware runs Linux.
Ubuntu ships with (effectively) a full firewall. By default nothing can get in. It's also largely immune to viruses. There's no need to even install antivirus software on a desktop system. Spyware and adware is also unheard of, because we get all our software from trusted online libraries called repositories. Since all the software is open-source, anybody can inspect it to make sure there's nothing malicious in it.

> 
3. My hard disc is 120 Gig. I am thinking of making into three roughly equal partitions, if thats possible, with XP on one. UBuntu on anther, the third I would use for keeping photo's and files on from both systems, which would allow me to reformat and reload the two operating systems if I wanted to without losing photo's etc. Is that possible?
Absolutely.
You'll need to do some manual partitioning for that, since it's not the default setup that the Ubuntu installer would create. Do a bit of [research](http://www.psychocats.net/ubuntu/partitioning) about partitioning and it'll seem a lot less daunting. 

You don't necessarily need to create an extra partition to share data. Ubuntu can read your NTFS Windows partition quite happily, so you could just leave your shared data there. But if you do want a separate one then you would simply shrink your NTFS partition and create a news partition formatted as Ext3 for Ubuntu, then a small swap parition for Ubuntu, then your shared partition (presumably NTFS)

The installer can do this for you. Or you can use the Ubuntu LiveCD to get the partitions sorted, then just assign the "mount points" to them when you install.

In any case, back up any important data on your Windows partition before making any changes. Just in case.

---

### Post by Barrucadu on 2008-04-24
Welcome (soon) to Ubuntu! If you have any other problems, you can expect an equally quick response. The Ubuntu community is a great strength of the OS, and the reason I hang around here rather than the Arch forums (Arch is my distro of choice).

---

### Post by digf on 2008-04-24
Thank you also Paqman and Barrucadu Changing to ubuntu suddenly starts to look less daunting. I'm sure I'll soon be back with more questions.
Thanks again

---

### Post by digf on 2008-04-25
Hello Again Forum

I've a couple more questions I'd like to ask. 
My hard disc is currently partioned with XP on a partition which is NTFS and about 25 Gig in size. The remaining partion is FAT32 and about 86 Gig in size,
I intend to leave XP where it currently is and put another partion in the 86 Gig section so ubuntu could be installed on a partition of approx. 20 Gig leaving 66 Gig which I would use to keep photo's, music, documents etc.
My first question (today) is would the FAT32 partition have to be changed to NTFS. I don't know what the reason was but a friend changed it to FAT32 when he created the partion using Partition Magic. I have Partition Magic so I should be able to change it if it needs to be.
My second question is, I am still puzzled about not needing a anti virus. I am under the impression that attachments in emails can carry virus's, sometimes without the senders knowledge. If this is correct wouldn't the computer be exposed to them without a anti virus program? 
Thanks again for the help
digf

---

### Post by patrickaupperle on 2008-04-25
> **digf said:**
> Hello Again Forum

I've a couple more questions I'd like to ask. 
My hard disc is currently partioned with XP on a partition which is NTFS and about 25 Gig in size. The remaining partion is FAT32 and about 86 Gig in size,
I intend to leave XP where it currently is and put another partion in the 86 Gig section so ubuntu could be installed on a partition of approx. 20 Gig leaving 66 Gig which I would use to keep photo's, music, documents etc.
My first question (today) is would the FAT32 partition have to be changed to NTFS. I don't know what the reason was but a friend changed it to FAT32 when he created the partion using Partition Magic. I have Partition Magic so I should be able to change it if it needs to be.
My second question is, I am still puzzled about not needing a anti virus. I am under the impression that attachments in emails can carry virus's, sometimes without the senders knowledge. If this is correct wouldn't the computer be exposed to them without a anti virus program? 
Thanks again for the help
digf

First, I am not all that experienced, so I can't tell you about the partitions. I do know that anything designed to run on windows, eg. that virus in the email, only runs on windows. It can do nothing on linux. So unless you get a virus specially designed for linux, there are very very few of these, you are completely safe.

---

### Post by oedha on 2008-04-25
1. you can keep using FAT32 or NTFS in order to store your files and they can be read both from WIN abd LIN
2. Yes...email sometimes contains virus attachment....but virus/malware/spyware can only run on windows right ( since they are actually a program which designed for windows ) so...they will not run (even walk) in Linux.......:)

Here i dont have to scan any flashdisk since if the UFD contains viruses....it showed but can not be executed.......

add : here to read about partition
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
and search for partition on [http://help.ubuntu.com/community](http://help.ubuntu.com/community)

---

### Post by chogoria on 2008-04-25
> **digf said:**
> Hello Again Forum

I've a couple more questions I'd like to ask. 
My hard disc is currently partioned with XP on a partition which is NTFS and about 25 Gig in size. The remaining partion is FAT32 and about 86 Gig in size,
I intend to leave XP where it currently is and put another partion in the 86 Gig section so ubuntu could be installed on a partition of approx. 20 Gig leaving 66 Gig which I would use to keep photo's, music, documents etc.
My first question (today) is would the FAT32 partition have to be changed to NTFS. I don't know what the reason was but a friend changed it to FAT32 when he created the partion using Partition Magic. I have Partition Magic so I should be able to change it if it needs to be.
My second question is, I am still puzzled about not needing a anti virus. I am under the impression that attachments in emails can carry virus's, sometimes without the senders knowledge. If this is correct wouldn't the computer be exposed to them without a anti virus program? 
Thanks again for the help
digf

If XP is on its own partition, you can easily install Ubuntu without even touching the partition that XP is on (I did it yesterday and was my first full install). Ubuntu uses the "ext3" file system, not NTFS or FAT32 and as such, Ubuntu will need to be installed onto a partition formatted to ext3 (this can all be done manually during the installation process of Ubuntu). 

What is good to know is that both Windows and Ubuntu can read and write to a FAT32 file system, so you could have one partition of shared documents between the two systems if you (like it seems you will) decide to have a "dual boot" system.

Hope this helps a bit.

---EDIT---
More info on FAT32 file system. 
The max. file size is 4Gb.
You may notice that people are telling you that Ubuntu can read and write to an NTFS file system, so when you are using Ubuntu, you will have access to the data from your windows partition. Whilst this is 100% true, Windows is unable to access any of the data from the ext3 (Ubuntu) partition, so if you have a FAT32 file system for storage used by both operating systems you have the best of both worlds.

---

### Post by hyper_ch on 2008-04-25
> **digf said:**
> 1. I currently use Yahoo for email and for its calender, would I be able to continue that with ubuntu?
Do you access that with your browser? If so, then you will not have problems... otherwise I'd need to know more abuot it...

> **digf said:**
> 
2. I have read that Linux is more secure than Windows. Is that correct and if so why? I do online banking and am wondering about the security with Ubuntu. I currently have Zone Alarm Security Suite and several anti spyware programs. Is good security available for Linux?
There are several reasons why linux is inherently better
(1) Linux was designed as true multi-user system... VISTA hasn't reached that point even today
(2) By default you do run on a limited rights account - but you can gain superuser rights (admin rights) easily when you are required to (a lot less annoying than on VISTA)
(3) You normally get all your software from the "repos". Those are like huge software libraries - a lot of them are operated by the actual distro "owners" - and those are free of malware... on windows you will have to either pay huge amounts of money or you will use p2p/shady websites to get software and often it's infested with malware and stuff
(4) you don't need AV and you have a firewall (which is unconfigured and which you probably won't need to configure anyway). If you are behind a router, make sure the firewall on there runs fine ;)
(5) In Windows everything is really tightly clamped together. You can't really run XP or VISTA without MSIE. So if there is a security issue with MSIE the person can get access to your whole computer. In Linux there's a lot more separation between the core-OS and the programs.
(6)...

> **digf said:**
> 
3. My hard disc is 120 Gig. I am thinking of making into three roughly equal partitions, if thats possible, with XP on one. UBuntu on anther, the third I would use for keeping photo's and files on from both systems, which would allow me to reformat and reload the two operating systems if I wanted to without losing photo's etc. Is that possible?
It is, but Linux should have two partitions. One for the actual system and one for the SWAP. In windows the swap is stored in a file, on Linux it uses its own partition. A Swap partition is not required, but very much recommended.
As for sharing, linux can read and write to a NTFS drive just fine. So you would not really need a "transfer" partition.

---

### Post by SunnyRabbiera on 2008-04-25
> **digf said:**
> Hello Again Forum

I've a couple more questions I'd like to ask. 
My hard disc is currently partioned with XP on a partition which is NTFS and about 25 Gig in size. The remaining partion is FAT32 and about 86 Gig in size,
I intend to leave XP where it currently is and put another partion in the 86 Gig section so ubuntu could be installed on a partition of approx. 20 Gig leaving 66 Gig which I would use to keep photo's, music, documents etc.
My first question (today) is would the FAT32 partition have to be changed to NTFS. I don't know what the reason was but a friend changed it to FAT32 when he created the partion using Partition Magic. I have Partition Magic so I should be able to change it if it needs to be.
My second question is, I am still puzzled about not needing a anti virus. I am under the impression that attachments in emails can carry virus's, sometimes without the senders knowledge. If this is correct wouldn't the computer be exposed to them without a anti virus program? 
Thanks again for the help
digf


well you might want to back up your data if you already have more then one partition.
Its a good idea anyways, if you have an external hard drive or a bunch of disks use them, if not save up some money if possible... I only say this just in case you mess something up.
as for how and why ubuntu and linux is so secure is the way it is built.
You see its not impossible to get a virus in linux, however its very unlikely you will ever have one running amok on your system because all the viruses for linux are conceptual only or are only possible to run in a administrative account.
You see windows by default allows the primary user to be the system administrator, and if one does not know what one is doing the system can get messed up.
In windows everything is tied to the kernel, the core of the OS...
here in linux everything is separated, the web browser, the interface, everything.
Also in linux the first rule everyone learns is to never run as root, and lucky for you the root account is disabled.
Linux mostly is based on Unix, one of the toughest operating systems to crack, the administrator and the main user are cut off from oneanother making security much better.

---

### Post by stalkingwolf on 2008-04-25
The only reason to run an antivirus in Ubuntu would be if 
you correspond a great deal with windows users.  You could 
pass on a virus without knowing it.  However I would think
your webmail would have some kind of "washing" system on it
or available.

I think the third partition you want would be something akin to
a /home partition.

---

### Post by digf on 2008-04-25
Hello Forum

Thanks to everyone for the help so far. I have now downloaded 7.10 and have had a struggle to get the internet connection. When I put my Toucan broadband disc in I get the followimg message.
**Setup.exe cannot be opened. No application suitable for automatic installation is available for handling this kind of file**
   I then tried following one of the help pages which was headed  **ADSLPPPoE  This guide is for setting up an ADSL connection using an ethhernet PPPoE modem under Ubuntu 6.06 LTS (Dapper Drake) but newer versions of ubuntu will ne similar.**I tried configuring PPPoE with the command line but failed to get a connection. I've read quite alot of the help information but I'm struggling. I would appreciate and help.
Thanks
digf

---

### Post by SunnyRabbiera on 2008-04-25
windows executables cannot be run in linux by default, you have to install wine...
I hate isp's that force software on you...

---

### Post by Daniel591992 on 2008-04-25
One quick thing. Consider using the Wubi installer to test it out without risking ruining your system :)

Also, make sure you have a recovery disc somewhere. When I first installed Ubuntu, I didn't know what partitions were and made the dumb mistake of uninstalling windows.

---

### Post by Paqman on 2008-04-25
Edit: whoops looks like these questions have already been answered!

---

### Post by digf on 2008-04-26
Hello

Where can I download Wine from for ubuntu 7.10? I found one link that took me to a archive but when I tried to download what I thought may be the correct file I got a message telling me that Windows didn't reconise the file.
Thanks again

Dell Dimension 2400  120 Gig Hard Disc  768 Ram  Thomson Touchspeed 330 Modem

---

### Post by chogoria on 2008-04-26
> **digf said:**
> Hello

Where can I download Wine from for ubuntu 7.10? I found one link that took me to a archive but when I tried to download what I thought may be the correct file I got a message telling me that Windows didn't reconise the file.
Thanks again

Dell Dimension 2400  120 Gig Hard Disc  768 Ram  Thomson Touchspeed 330 Modem

Windows did not recognise the file because the Wine file is in the .deb format that is for linux OS's. You'll need to install the file when using Ubuntu, not Windows.

---EDIT---
I've just visited the download page for Wine. When downloading, make sure you click on the version you want, such as "Wine 0.9.59 i386" don't click on the "-dev" bit at the end. I'm sure you've done it the correct way anyway, but I thought it best to make sure.

---

### Post by digf on 2008-04-26
Hello 
I'm sorry to be a pain but I'm still struggling. I rebooted into ubuntu and went to Add/Remove. I found **Wine Windows Emulator**, am I correct up to now? but when I clicked on it to install it said that the list was out of date and needed to be updated before I could install, but I would need to be online to be able to do this. I'm starting to think about chickens and eggs now but I know it must be me doing something wrong
Thanks again for youe help

---

### Post by chogoria on 2008-04-26
> **digf said:**
> Hello 
I'm sorry to be a pain but I'm still struggling. I rebooted into ubuntu and went to Add/Remove. I found **Wine Windows Emulator**, am I correct up to now? but when I clicked on it to install it said that the list was out of date and needed to be updated before I could install, but I would need to be online to be able to do this. I'm starting to think about chickens and eggs now but I know it must be me doing something wrong
Thanks again for youe help

Do you have an ethernet cable to connect your computer to your router with? Using this method, you should not need any of the software provided by your isp (it is usually fairly straight forward even in Windows to avoid using any software provided by your isp). If you can connect this way, you should be able to download the updates you require. Have you visited the [**Ubuntu Community Wine Help**]("https://help.ubuntu.com/community/Wine") pages for finding out information as well?

If there is no way of getting a cabled connection to your computer, I'm not sure what else to suggest at this point. Some of the more experienced users will have to take over methinks.:confused:

---

### Post by digf on 2008-04-26
Hello chogoria
Thanks very much for your suggestions. I'm going to keep trying and will also investigate the possibility of using a ethernet cable. I didn't know there was a different method to the USB Modem that I currently use.

---

### Post by digf on 2008-04-26
Hello Forum

Yesterday I downloaded ubuntu 7.10 but have been ubable to set up a internet connection. Its been suggested by one member that if I changed my Speedtouch 330 modem for a ethernet connection that it may solve the problem. I don't know anything about this but is there anyone who can advise me.
Also I have just downloaded and burned to disc version 8.04. Would there be any advantage if I loaded that.Is it any easier to set up and get a internet connection.
I'm really looking forward to overcoming the connection problem as I'll feel I'm making some real progress with ubuntu
Thank you in advance

Dell Dimension  120G Hard Disc  768 Ram Thomson Speedtouch 330 modem

---

### Post by digf on 2008-04-28
> **chogoria said:**
> Do you have an ethernet cable to connect your computer to your router with? Using this method, you should not need any of the software provided by your isp (it is usually fairly straight forward even in Windows to avoid using any software provided by your isp). If you can connect this way, you should be able to download the updates you require. Have you visited the [**Ubuntu Community Wine Help**]("https://help.ubuntu.com/community/Wine") pages for finding out information as well?

If there is no way of getting a cabled connection to your computer, I'm not sure what else to suggest at this point. Some of the more experienced users will have to take over methinks.:confused:
Hello chogoria

Thanks very much for your last post to me. The only way I have ever connected my modem in the past has been with with what I now know to be a USB Modem. I have now purchased a modem router and as you said, as soon I had set it up in Windows I rebooted into ubuntu and I am online. I now feel that I've taken a big step forward with ubuntu. Once again thank you.

---

### Post by chogoria on 2008-04-28
> **digf said:**
> Hello chogoria

Thanks very much for your last post to me. The only way I have ever connected my modem in the past has been with with what I now know to be a USB Modem. I have now purchased a modem router and as you said, as soon I had set it up in Windows I rebooted into ubuntu and I am online. I now feel that I've taken a big step forward with ubuntu. Once again thank you.

No problem, glad I could help and hope things go well in Ubuntu :).

---

### Post by brewstermax on 2008-04-28
or you can just install virtual box at this link virtualbox.org and run it from a virtual machine to try it at full speed inside windows

---

