---
title: "Installing software"
date: 2011-09-13
forum: New to Ubuntu
---

### Post by Thiefot35 on 2011-09-13
I have just downloaded avg antivirus soft ware but have no idea at all about how to install it.

---

### Post by howefield on 2011-09-13
Before you install, you are aware that it the linux version of AVG doesn't have gui ?

---

### Post by TeoBigusGeekus on 2011-09-13
If you're running Ubuntu (linux in general), are you sure you need an antivirus?

---

### Post by Thiefot35 on 2011-09-13
I have no idea.I am just setting this up for the first time.ive never used any other os than windows.So am just finding my feet as it were.

---

### Post by TeoBigusGeekus on 2011-09-13
I see.
If you don't run a windows server, then there's no need for an antivirus.
Viruses are created targeting windows; there is hardly any active virus written for linux.
Relax and enjoy the best OS out there!

---

### Post by howefield on 2011-09-13
Have a read here..

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

If you still want anti virus, get one with a GUI, unless you don't mind learning how to use the command line to do your scanning, eg bitdefender or avast, there are many others.

---

### Post by haqking on 2011-09-13
> **Thiefot35 said:**
> I have no idea.I am just setting this up for the first time.ive never used any other os than windows.So am just finding my feet as it were.


Linux does not suffer from Viruses like other OS, there are no known viruses in the wild, the main reason using AV on linux is to scan incase you share files with windows users.

It can still suffer from trojans, rootkits etc, but that comes down to vigilence and making sure you stick to the security model and not disabling passwords or enabling root etc.

Common sense, dont tell your system you want it to do something unless you are sure etc. Linux assumes you know what you are doing ;-)

In browsers you can still suffer from XSS or CSFR, other script related issues so use things like NoScript plugin for firefox, Ad-block etc.

[B]See here for Anti-Virus information:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)[/B]

See below for Bodhi.Zazen's overview of Linux Security

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Then these stickies:
security stickies (5 stickies)
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

Also see about sudo and why root account is disabled by default in Ubuntu:

sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

rootsudo
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You might also want to look at Tor for anonymizing your connection:
[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

Firewalls are not generally needed on a home desktop machine as that is taken care of by your router however there is a hardcoded firewall in Linux called Netfilter/IPTables and can be configured by reading here:

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Though most people if use anything use UFW/GUFW which is a interface for managing IPTables without the complicated command line. see here:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Also look at apparmor for profiling your applications and there privelege:

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)


Have fun

Regards

haqking

---

### Post by Thiefot35 on 2011-09-13
Thanks for the help guys.

---

### Post by TeoBigusGeekus on 2011-09-13
Just for the history:
[http://www.neowin.net/news/a-history-of-viruses-on-linux]("http://www.neowin.net/news/a-history-of-viruses-on-linux")
But don't let it panic you ;)

---

### Post by haqking on 2011-09-13
> **Thiefot35 said:**
> Thanks for the help guys.


No worries, in short AVG for Linux is pretty poor as it has no GUI for new people to linux use to Av software, it also the last time i looked didnt have on-access scanning.

You only really need AV if you share files with windows users.

for that ClamAV is fine and (ClamTK) the GUI for it. It is simple and does the job.

No known Viruses in Wild for Linux, those that exist are POC (proof of concept) and if a new one came out suddenly it would be patched quickly, not to mention your AV wouldnt have a definition for its signature anyways.

Peace

---

