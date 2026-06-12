---
title: "Anti-virus or not"
date: 2009-03-21
forum: Recurring Discussions
---

### Post by SINNISTER on 2009-03-21
HEy

Do you need a Anti-virus or what coz i have never seen a Linux version of any anti-viruses or is linux not able to get viruses because most viruses are made in Linux to effect windows???

JUst had a random thought :D

---

### Post by InfectedWithDrew on 2009-03-21
Linux viruses are incredibly rare and you only really get them if you're being stupid and running scripts that strange people tell you to run.

Still, there is a nice scanner for Linux called ClamAV and you can use it by installing clamtk from Add/Remove.  Make sure that when you run it, you type:
```
gksudo clamtk
```
This way, you will run with admin privileges.

----------------
Now playing: [Jonah33 - Mystery](http://www.foxytunes.com/artist/jonah33/track/mystery)

---

### Post by jmszr on 2009-03-21
sinnister,
          This should explain it to you:[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by OrangeCrate on 2009-03-21
And, something else you can read on the subject...

[http://www.linuxclues.com/articles/21.htm](http://www.linuxclues.com/articles/21.htm)

---

### Post by lisati on 2009-03-21
It's up to you. 

It's not that [malware]("http://en.wikipedia.org/wiki/Malware") that can hurt your Linux system doesn't (or can't) exist, it's just unlikely that you will encounter it, and even if you did, you'd normally have to run it yourself and give it permission to do its mischief.

You're more likely to run into Windows-specific malware (which don't work on Ubuntu without help). 

Be aware, however, that it's still possible to pass on Windows malware by incautious forwarding of links and attachments. Yahoo takes a dim view of this, and I quote from their [terms of service]("http://info.yahoo.com/legal/us/yahoo/utos/"), section 6 (Member Conduct):
> You agree to not use the Yahoo! Services to:

   h.       upload, post, email, transmit or otherwise make available any material that contains software viruses or any other computer code, files or programs designed to interrupt, destroy or limit the functionality of any computer software or hardware or telecommunications equipment;
  



---

### Post by mb_webguy on 2009-03-22
You might want to read these links.

bodhi.zazen's comprehensive [Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812") thread
Psychocat's guide to [Security on Ubuntu]("http://www.psychocats.net/ubuntu/security")

Basically, the only reason to bother installing antivirus software in Linux is to protect Windows users.

---

### Post by RedSingularity on 2009-03-22
I have avast installed but as webguy said, its basically to scan files that i will be sending over to a windows system.

---

### Post by Peasantoid on 2009-03-22
My philosophy: Better safe than hacked. Install ClamAV (sudo apt-get install clamav) and run the occasional scan (sudo clamscan -r ~) on your home folder. Or anywhere else you may have installed third-party software.

---

### Post by Perfect Storm on 2009-03-22
> **Peasantoid said:**
> My philosophy: Better safe than hacked. Install ClamAV (sudo apt-get install clamav) and run the occasional scan (sudo clamscan -r ~) on your home folder. Or anywhere else you may have installed third-party software.

...waste of time IMHO. 


Instead;

1) Never run as root
2) Only install trusted sources
3) Clean your web browser once in a while
4) common sense


That should keep happy and clean and it worked for me over 8 years with Linux.

---

### Post by Giant Speck on 2009-03-22
There needs to be a sticky about AV software on Linux.

---

