---
title: "Virus protection and system clean-up"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by SirRoverofIvories on 2012-08-21
Howdyrroooooooo...
I have been told that I do not need a virus protection program with Lubunto, nor do I need a system clean-up program.   I have previously used AVG Free and  Fix-Cleaner.

I'm somewhat nervous without virus protection.

---

### Post by Bashing-om on 2012-08-21
sir---
  The short of it is NO // for once no is a good thing.
Ubuntu is a closed system on install .... unless you open ports on your system to outside contact, no additional control is required (not withsaying enabling
ufw is a bad idea for what might get generated from your system, you be the judge) [I don't and have never experience a problem] .
As to clean up: none for the time being ... ubuntu is a very smart operating system and for the most part self maintaining // at a later time you will want to run a couple of light commands to clean up perhaps orphaned and no longer needed config files // as of now no worry!

[INDENT]Does this suffice ? <==BDQ
[/INDENT]

---

### Post by Paqman on 2012-08-21
> **SirRoverofIvories said:**
> 
I'm somewhat nervous without virus protection.

Most Linux users don't use an antivirus package, and the AV packages for Linux generally only scan for Windows viruses anyway. There aren't currently any known virus threats to Linux. There have been some in the past but they've been patched. Systems like Ubuntu are able to update any package on the system, so you could say that security is a built-in feature, not something you add on later like on Windows.

Generally, if your system is up-to-date and you stick to getting your software from the repos (or other reputable sources) you've got little to worry about. If you're running a web-facing server or run server packages you need to pay more attention to security.

As for maintenance, all systems require this, although I find Linux much less labour-intensive than Windows systems. The main difference is that maintenance on a Linux system is mostly about keeping organised and getting rid of superfluous stuff that's taking up space, whereas on Windows it's about preventing performance from degrading.

Check out [Bleachbit]("apt:bleachbit") if you want a nice tool that can help out with tidying your system up, but doing so is unlikely to make it run any better.

---

### Post by Buntu Bunny on 2012-08-21
You might want to consider a firewall - [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by Buntu Bunny on 2012-08-21
I just remembered that there is an antivirus program in the Ubuntu Software Center; ClamTk. I assume it's the same for Lubuntu(?)

---

### Post by BDNiner on 2012-08-21
Viruses on Ubuntu are rare but the exits. The main thing you have to worry about is copying a windows virus from your ubuntu machine to your windows computer (if you have one). That is why I have a virus scanner on my ubuntu computer.

---

### Post by bodhi.zazen on 2012-08-21
I've never seen a virus on Linux, just false positives.

If you wish, you can read:

[https://help.ubuntu.com/community/Antivirus/](https://help.ubuntu.com/community/Antivirus/)

I do not feel any need for antivirus on Ubuntu, any windows machine I use has antivirus on it already, so running on Ubuntu adds little.

In terms of clean up, you can look at bleachbit

[http://www.ubuntugeek.com/bleachbit-cleans-unnecessary-files-to-free-disk-space-and-maintain-privacy.html](http://www.ubuntugeek.com/bleachbit-cleans-unnecessary-files-to-free-disk-space-and-maintain-privacy.html)

Just take care, if you randomly delete things with bleachbit you will have problems. If you do not understand what you are removing, leave it alone.

---

### Post by Paqman on 2012-08-21
> **Buntu Bunny said:**
> You might want to consider a firewall - [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Whoa there, diving into iptables may not be the right level for the Absolute Beginners forum!

Ubuntu's default settings are fairly good. Unlike some other operating systems it doesn't ship with a ton of services listening on ports. So there's nothing for an attacker to connect to unless you've installed something that is listening for connections from the internet. 

If you're behind a router then you're already protected by a firewall, but if you want to also enable Ubuntu's built in firewall you can use [ufw]("https://help.ubuntu.com/community/UFW"). There's a nice desktop admin tool for it called [GUFW]("apt:gufw").

---

