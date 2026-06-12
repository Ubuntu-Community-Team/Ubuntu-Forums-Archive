---
title: "File backup on network"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by Starbase 9525 on 2008-12-01
I have Ubuntu 8.4 up and running on a small network. It is hardwired into the router and the other 2 laptops are using wireless. Both laptops are running Vista. Is there a software program available that would go out from Ubuntu and backup files from those laptops? Or do I need to write a script file of some kind? I have no problem using the command line in a terminal but I am new to Linux. I would like this to be automated if possible but wouldn't mind if it had to be done manually. Any info appreciated.

Starbase 9525

---

### Post by halitech on 2008-12-01
if the laptops were running ubuntu as well I'd say mount the desktop drive on the laptops and use cron to rsync the drives. I know linux can read windows drives but not sure how it would go about figuring out what files to grab. you may have to figure out some way of making the backup on the laptops first then copying them to the desktop.

---

### Post by realgt on 2008-12-01
i run sbackup for this, and with network share support you could share folders on the vista laptops and use sbackup to back those up to another location. if you're looking for something with a decent GUI, sbackup should work for you.

**sudo apt-get install sbackup**
hth

---

### Post by Girya on 2008-12-01
> **Starbase 9525 said:**
> I have Ubuntu 8.4 up and running on a small network. It is hardwired into the router and the other 2 laptops are using wireless. Both laptops are running Vista. Is there a software program available that would go out from Ubuntu and backup files from those laptops? Or do I need to write a script file of some kind? I have no problem using the command line in a terminal but I am new to Linux. I would like this to be automated if possible but wouldn't mind if it had to be done manually. Any info appreciated.

Starbase 9525

I run backuppc on a ubuntu server to back up my home network of linux and windows machines. once you have it configured its automatic. 

Upside...It has a nice web based interface, doesn't require any client software if you choose samba for the back-up mechanism and uses file pooling for so you don't end up with redundant back-ups (It only makes one copy of identical files and links to them). active mailing list for support 

Now for the downside. I struggled to configure it. In ubuntu you have to manually add some things to apache2.conf for apache to find it. And occasionally It stops backing up windows and I have to change some settings to get it going again. The full backups on my wirelessly connected laptop takes upwards of 3 hours but that's a function of the wireless transfer speed. 

Here's the link. [http://backuppc.sourceforge.net/]("http://backuppc.sourceforge.net/")

---

### Post by Starbase 9525 on 2008-12-01
> **realgt said:**
> i run sbackup for this, and with network share support you could share folders on the vista laptops and use sbackup to back those up to another location. if you're looking for something with a decent GUI, sbackup should work for you.

**sudo apt-get install sbackup**
hth

Thank you for your help. I ran this but am not able to see the program anywhere and don't know how to get it started. Also I thought I had Samba running because I can see one of the laptops but it shows nothing in the windows shares even though I have the folder shared on the laptop that I want to back up. I am guessing that I don't have Samba configured correctly. New enough at Linux that I don't know much of the nuts and bolts stuff yet.

---

