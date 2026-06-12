---
title: "Antivirus is recommended or not"
date: 2008-05-18
forum: Recurring Discussions
---

### Post by anon23 on 2008-05-18
I want to know whether antivirus is recommended for ubuntu or not and if yes then which is best one.

---

### Post by paintba||er on 2008-05-18
No, it's unneeded.

---

### Post by anon23 on 2008-05-18
Then why antivirus are made for linux

---

### Post by paintba||er on 2008-05-18
If you're sharing files with Windows users then you could accidentally infect someone.  They only scan for Windows viruses, which will have no affect in Linux.

---

### Post by aysiu on 2008-05-18
> **anon23 said:**
> Then why antivirus are made for linux
If you're running a file server for Windows computers or a mail server, anti-virus applications can come in handy for scanning for Windows viruses.

If you're using Ubuntu as a home computer, anti-virus is useless and will just give you a false sense of security. Use strong passwords and don't enable extra services if you don't know how to secure them.

---

### Post by crashcoredump on 2008-05-18
This is the best explanation I have yet to see in this forum.

Check it out......:popcorn:

[http://ubuntuforums.org/showthread.php?t=694198](http://ubuntuforums.org/showthread.php?t=694198)

---

### Post by XedGeneral on 2008-05-19
I don't think it's needed. 

Just like Mac (Before), there are so less viruses and bad stuff can infect Ubuntu! This is also one of the best points of Ubuntu. Safe and secure!

---

### Post by Watchtow3r on 2008-05-19
What if you dual-boot Ubuntu and Windows, and exchange files between the two (like music)?

---

### Post by sharkey77 on 2008-05-20
That's why you have anitvirus in Windows.  To infect Windows from Ubuntu would be like this.  You download an infected music file while running Ubuntu and then transfer it to Windows.  Regardless of how the infected file made it's way to Windows to be executed your Windows AV is responsible for protecting it.

---

### Post by p_quarles on 2008-05-20
Moved to Recurring Discussions. Basically -- like aysiu said -- antivirus software doesn't protect against any potential attacks against a Linux system, and can be a distraction from the security issues that Linux operators should be paying attention to. 

There are several antivirus packages available for Linux and BSD systems -- these are by and large used on e-mail server machines to cut down on spam and phishing. No one (who understands what they are doing) uses an antivirus application to protect Linux itself against viruses. 

Dual-booting with Windows might make it sound like a good idea to run an antivirus scanner from the Linux partition -- but in practice this doesn't work out. You're likely to get a lot of false positives, and a Linux antivirus is not able to apply any kind of real-time protection. The better way to secure your Windows installation is to run it without administrator privileges -- except when you need them. If you're just surfing the net and checking e-mail, you don't need to be able to edit system configuration files. Disabling the admin privileges for the normal user makes it that much more difficult for viruses to attack your Windows system.

---

### Post by Hallvor on 2008-05-20
> **Watchtow3r said:**
> What if you dual-boot Ubuntu and Windows, and exchange files between the two (like music)?

It doesn`t matter if you transfer mp3 or avi files between the two. There are no mp3 or avi viruses out there.

---

### Post by Phenax on 2008-05-20
Even if you got a Windows virus on your Linux computer, I would highly doubt it would cause any harm. The only way I could think of is if it got into Wine or some odd virtualization situation.

Virus scanners for Linux were primarily made for servers. Think about it this way: All of these e-mail services both check for viruses in e-mail attachments as well as run Linux. There was a necessity for a Linux-based anti-virus to come up so things like these could exist.

---

