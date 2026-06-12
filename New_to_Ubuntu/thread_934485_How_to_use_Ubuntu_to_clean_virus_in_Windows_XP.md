---
title: "How to use Ubuntu to clean virus in Windows XP"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by md isa on 2008-09-30
I'm using Ubuntu and Windows XP as OS on my computer. Ubuntu is running well but my Windows could not start ( suspected infected by virus). Can anyone out there, help me fixing this problems using Ubuntu.

---

### Post by drubin on 2008-09-30
[http://sudan.ubuntuforums.com/showthread.php?t=906067](http://sudan.ubuntuforums.com/showthread.php?t=906067) 

take a look at Old_Soldier's post for a reply.

---

### Post by lisati on 2008-09-30
There is also a Linux-friendly version of "AVG free". Some people, however, have had a problem with the updates - a simple solution is described [here]("http://ubuntuforums.org/showpost.php?p=5586774&postcount=1")

---

### Post by md isa on 2008-10-02
I have downloaded the AVG, and installed it.  When I tried to run it by clicking the icon as being told, I saw nothing happened. What should I do?

---

### Post by superprash2003 on 2008-10-02
clamAV is another such application

---

### Post by md isa on 2008-10-04
I have install clamav. I saw nothing happened. Where can I search sign or icon for that clamav, or do the installation went wrong somewhere? Please guide me to that

---

### Post by Ryadt on 2008-10-04
Install 'clamtk' in synaptic.

---

### Post by Paqman on 2008-10-04
> **md isa said:**
> my Windows could not start ( suspected infected by virus)

What makes you think virus? It wouldn't be a very good virus if it stopped Windows from booting. It'd never be able to spread.

---

### Post by Old_Grey_Wolf on 2008-10-04
> **Paqman said:**
> What makes you think virus? It wouldn't be a very good virus if it stopped Windows from booting. It'd never be able to spread.

I was thinking something similar. It sounds like it could be the disk has developed some bad sectors. Unfortunately, sectors holding modules that Windows needs to boot. I keep a CD of UBCD4Win (Google on it) handy for repairing my friends and families Windows PCs. I use it to copy their data to a thumb drive. Then use it to repair and restore Windows XP. Unless the OP has a working Windows PC or a friend with one, this will not help. The "Ultimate Boot CD" needs to be built on a Windows machine using a set of XP CDs.

---

### Post by md isa on 2008-10-05
> What makes you think virus?

Its happened while I'm surfing my avast detected malicious program running, and I had tried several times to delete using avast and I failed doing so. I then used Malware cleaner to do the job. While the program is running and detected 9 infected files, I've cancelled the job due to I'm leaving my house  and since that I cannot get my windows start. It just start untill displaying  the windows logon and be there.

---

### Post by handydan918 on 2008-10-05
> **md isa said:**
> Its happened while I'm surfing my avast detected malicious program running, and I had tried several times to delete using avast and I failed doing so. I then used Malware cleaner to do the job. While the program is running and detected 9 infected files, I've cancelled the job due to I'm leaving my house  and since that I cannot get my windows start. It just start untill displaying  the windows logon and be there.

One easy thing to try is to simly delete the infected files on the windows partition. This assumes that you know which files are responsible, of course. I have done this occasionally when an anti-virus program could not delete a "protected" file.

---

### Post by timjohn7 on 2008-10-05
I had a similar virus infection in Jan 2008 (rmvirut) which rebooted my laptop after completing the WinXP login screen.
After a hugely frustrating week and hours of research, I used Knoppix LiveCD to recover my data, found out about Ubuntu, have evaluated it for 10 months and have just deleted my XP dualboot partition.
Best antivirus solution I have ever used.

---

### Post by eignemhs on 2008-10-05
> **Paqman said:**
> What makes you think virus? It wouldn't be a very good virus if it stopped Windows from booting. It'd never be able to spread.

I agree, but virus don't always take in account for the cpu being AMD vs. Intel.  Go figure.

---

### Post by Old_Grey_Wolf on 2008-10-05
> **md isa said:**
> Its happened while I'm surfing my avast detected malicious program running, and I had tried several times to delete using avast and I failed doing so. I then used Malware cleaner to do the job. While the program is running and detected 9 infected files, I've cancelled the job due to I'm leaving my house  and since that I cannot get my windows start. It just start untill displaying  the windows logon and be there.

Use Ubuntu to save your data from the Windows disk. Save it to an external disk. Then you will have your data if you have to reinstall XP.

---

