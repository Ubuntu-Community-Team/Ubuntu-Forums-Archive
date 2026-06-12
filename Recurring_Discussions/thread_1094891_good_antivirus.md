---
title: "good antivirus?"
date: 2009-03-13
forum: Recurring Discussions
---

### Post by ave2 on 2009-03-13
what anti virus software / firewalls do you use with ubuntu

---

### Post by Ms_Angel_D on 2009-03-13
You should read this:[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by binbash on 2009-03-13
you don't need any.But you can use iptables and clamav

---

### Post by ave2 on 2009-03-13
thanks metalhellsangel thats an interesting article- explains a lot

---

### Post by SunnyRabbiera on 2009-03-13
Yeh antivirus is kind of silly in Linux, as linux has no real viruses or at least none that do any major harm.
Most viruses are made for windows, and windows viruses are rendered practically harmless in linux as the root of the system is well protected under linux unlike windows.

---

### Post by Jammy4041 on 2009-03-13
I have used AGV Free under Ubuntu Fiesty a while back, but under Linux, you don't really need it as it was designed from the ground up to be secure. Windows wasn't, which is why it needs anti-viruses.
 
As for other antivirus programs, check out ClamAV.
 
[http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl) ( click on .deb package)
 
```
sudo apt-get  clamav
``` will install clamav and its dependancies.

---

### Post by Sprut1 on 2009-03-13
> **Jammy4041 said:**
> I have used AGV Free under Ubuntu Fiesty a while back, but under Linux, you don't really need it as it was designed from the ground up to be secure. Windows wasn't, which is why it needs anti-viruses.

As Jammy is trying to say "AVG" is a great program. I only use it in Windows though.

---

### Post by madverb on 2009-03-13
> **bgrand said:**
> you can also use Symantec Antivirus for Ubuntu

Yes, but Symantec make horrible software.

---

### Post by s.fox on 2009-03-13
> **madverb said:**
> Yes, but Symantec make horrible software.


Hi,

Could you elaborate a little more?  I was considering using it.

Thank you.

---

### Post by humphreybc on 2009-03-13
> **Ash R said:**
> Hi,

Could you elaborate a little more?  I was considering using it.

Thank you.

Symantec, well, their Norton range I have had terrible encounters with. Their software is slow at scanning for viruses, very pricy, use up a LOT of resources, hardly finds things that are picked up in free alternatives, aren't customizable enough and also I have found (in Windows at least) that they embed themselves inside the root file system so deep that to remove them properly requires a special Norton removal software.

I once had a client who was using Norton and was having many problems with it, so I uninstalled it as you normally would and then the internet would not work anymore on their computer. I tried everything to fix it, and nothing worked, until I booted into safemode to check if it was some random drivers and then it worked. It turned out that Norton was the problem - remnant things left over in the registry, services and Windows core files were blocking internet access. I had to run a special tool from Norton themselves to rid it all!

Stay away from Symantec!

---

### Post by presence1960 on 2009-03-13
> **Ash R said:**
> Hi,

Could you elaborate a little more?  I was considering using it.

Thank you.

Click on the link in post #2 of this thread. The bottom line is you really don't need it.

---

### Post by s.fox on 2009-03-13
> **humphreybc said:**
> Symantec, well, their Norton range I have had terrible encounters with. Their software is slow at scanning for viruses, very pricy, use up a LOT of resources, hardly finds things that are picked up in free alternatives, aren't customizable enough and also I have found (in Windows at least) that they embed themselves inside the root file system so deep that to remove them properly requires a special Norton removal software.

I once had a client who was using Norton and was having many problems with it, so I uninstalled it as you normally would and then the internet would not work anymore on their computer. I tried everything to fix it, and nothing worked, until I booted into safemode to check if it was some random drivers and then it worked. It turned out that Norton was the problem - remnant things left over in the registry, services and Windows core files were blocking internet access. I had to run a special tool from Norton themselves to rid it all!

Stay away from Symantec!

Ah, that sounds quite bad.  I don't think I will use it then.  Thank you for the explanation.

> **presence1960 said:**
> Click on the link in post #2 of this thread. The bottom line is you really don't need it.

Well,  I know Linux is pretty secure,  but I think its just peace of mind more than anything else.

---

### Post by gandaran on 2009-03-13
> Well, I know Linux is pretty secure, but I think its just peace of mind more than anything else
all antivirus programs for linux only scan for windows virus, which you must know they won't run on linux systems, so it's no use to have them installed unless you are running a server and want to protect other windows computers.
for peace of mind install **rkhunter** or **chkrootkit** (find them in synaptic) these two really scan your computer for linux virus and rootkits.

---

### Post by s.fox on 2009-03-13
> **gandaran said:**
> for peace of mind install **rkhunter** or **chkrootkit** (find them in synaptic) these two really scan your computer for linux virus and rootkits.

Perfect.  Thank you.  I shall install them later when I am home :D

Once again,  thanks

---

### Post by bcbotha on 2009-03-13
> **gandaran said:**
> all antivirus programs for linux only scan for windows virus, which you must know they won't run on linux systems, so it's no use to have them installed unless you are running a server and want to protect other windows computers.
for peace of mind install **rkhunter** or **chkrootkit** (find them in synaptic) these two really scan your computer for linux virus and rootkits.
Thanks Gandaran. i knew that windows viruses cant work on linux but they can still be stored on a linux machine so i've been looking for a way to clean up my linux system.

---

### Post by presence1960 on 2009-03-13
> **gandaran said:**
> all antivirus programs for linux only scan for windows virus, which you must know they won't run on linux systems, so it's no use to have them installed unless you are running a server and want to protect other windows computers.
for peace of mind install **rkhunter** or **chkrootkit** (find them in synaptic) these two really scan your computer for linux virus and rootkits.

+1 they are on my machine

---

### Post by linuxisevolution on 2009-03-13
To get a virus in Ubuntu, you will have to first download it, then install it, which will ask for a password or even compile it.

You will not get a virus in Ubuntu.

---

### Post by Giant Speck on 2009-03-13
For now, Linux is safe from many types of malware.

However, if you are going to be sending files to Windows users, you may want an antivirus and only run it to check the specific files you are going to send.  Just to be safe and to be courteous to your Windows-using friends and family.

---

### Post by 67GTA on 2009-03-13
> **Ash R said:**
> Hi,

Could you elaborate a little more?  I was considering using it.

Thank you.

I bought Norton for my first XP machine before I started using Linux. It would always pop up and tell me I was infected, quarantine the file, and then tell me it couldn't fix it. I updated the subscription for two years, and had to reinstall 5 times because of viruses. The last one got through the email scanner and automatically opened the attachment as soon as I opened the email. The first thing it done was shutdown Norton, and proceeded to turn my PC into an expensive night light. The only thing that worked afterwards was the monitor. After all of that, I tried AVG free, and have not had a virus get through it for 5 years now. I use AVG free for Linux now to scan outgoing emails just to try and do my part not to spread crap to other people with Windows machines. As stated above, rootkits are equal opportunity destroyers (Linux and Windows). I use rkhunter weekly to check my Linux machines. Be sure to keep it updated. Run ```
rkhunter -h
``` in a terminal to see all of the options (arguments) to use with it. The only other sticking point is Firefox or other web browsers. Most malware is written for Windows as are most viruses, but some are cross platform. Check out the adblock and noscript add ons for Firefox, and you should be fine.

---

### Post by cardinals_fan on 2009-03-16
[http://www.happyassassin.net/2009/01/20/on-linux-security/](http://www.happyassassin.net/2009/01/20/on-linux-security/)

---

### Post by Jammy4041 on 2009-04-08
Also, you can use ClamAV with the "ClamTK" GUI.

A few notes though, you still need to go to the terminal and type in

```
sudo freshclam
```

to update the underlying clamav antivirus kernel.

I also have an option in the context menus called "Scan for viruses" which is handy. It was provided by a package called "nautilus-clamscan"
[I]
If you would like clamav, and its gui and do not have it yet installed, open a terminal and type:[/I]

```
sudo apt-get install clamav clamtk nautilus-clamscan
```

I know there is the cliché of Linux does not need any antivirus, but if you deal with a lot of mail, Linux can still be infected by mail. Although most home users will not need it.

---

