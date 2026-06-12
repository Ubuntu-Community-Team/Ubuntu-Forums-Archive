---
title: "Ubuntu = needing anti virus ??"
date: 2009-01-22
forum: Recurring Discussions
---

### Post by Taz. on 2009-01-22
So i have a partition for ubuntu and one for windows.

Should i install an anti virus on ubuntu? Or no needed? If yes, which? I want a light one. Thanks.

---

### Post by 73ckn797 on 2009-01-22
> **Taz. said:**
> So i have a partition for ubuntu and one for windows.

Should i install an anti virus on ubuntu? Or no needed? If yes, which? I want a light one. Thanks.


Not needed.

Plenty of other posts on the topic.

---

### Post by donkyhotay on 2009-01-22
As mentioned above, not needed. The only virus scanners really available for linux are designed to search for windows viruses so that you can download a suspect windows executable to linux, scan it, then decide if you want to pass the file along to your windows box. Yes it seems a little unnerving not having a virus scanner if you've used windows for any length of time but just sit back and remember that you have an OS thats designed to help you the user, not increase someone elses profit margin.

---

### Post by Taz. on 2009-01-22
cant the windows virus go into linux then go to the windows partition and affect it?

---

### Post by MikeBrown on 2009-01-22
Here are two excellent sources of information regardng that very topic. It's written in a way that is easy for people who have switched from Windows (like me) to understand: 

[http://librenix.com/?inode=21]("http://librenix.com/?inode=21")

[One guide written on this very forum]("http://ubuntuforums.org/showthread.php?t=510812")

Hope that helps!

---

### Post by donkyhotay on 2009-01-22
> **Taz. said:**
> cant the windows virus go into linux then go to the windows partition and affect it?

If you dual-boot (or use wubi), and windows can see the linux partition, and access the file from windows then yes, you're infected. Be aware though thats the same thing as downloading directly from windows since you didn't scan for anything. Even if this happened though, your linux wouldn't be infected only the windows side. I don't have a virus scanner on any of my computers but then again I don't use anything besides linux (mostly ubuntu). If you actually start using them you will notice they focus heavily on CLI and are really designed for servers dedicated to the job. Since a server like this wouldn't be part of a dual-boot or wubi install it's not something really planned for. Basically, unless you're the sysadmin for a large company... don't worry about virus scanners with linux.

---

### Post by Taz. on 2009-01-22
So i decided to put an anti virus, since the virus will infect windows not ubuntu. Which one u recommend?

---

### Post by OsuSurfRat on 2009-01-22
What if you have a Linux OS with no partition on the hard drive that is on a home network where other computers have Windows OS for those resistant to or unable to change?

what cracking?

I'm new to this forum and it is my first time registering for any forum.  I just recently decided to free my self from the corporate tyranny and does not seem that open source communities could survive with out well informed forums!

---

### Post by Taz. on 2009-01-22
umm ok.. lol..


Im just asking what would be a good AV for my ubuntu, to protect my windows partition and other pc's in my network what work on windows.. ?

---

### Post by Aralhach on 2009-01-22
I would reccomend avast!, since it's free and is excellent.  However, the best protection from viruses is having good internet habits.  This is much more reliable.  Don't download files from anywhere, download only from trusted sources and you should be safe ;)

---

### Post by OrangeCrate on 2009-01-22
> If you dual boot Linux and Windows and get a virus-infected mail in Linux, it can NOT jump to your Windows partition. Nor can it spread over the local network to other systems. You can even store the attachment in your /home directory and open the zip or click the file, and it will be dead in the water. Windows executables won't run under Linux. Linux files need to be granted permission to become executable. And even then, it can't spread beyond the home folder. (This is also why Linux AV programs do not have a "live guard" module in them — the virus does not execute or move.) You could even leave a virus executable there as long as you wanted to without risk. Windows will not get infected, unless you deliberately copy the virus to your Windows partition.

If you dual boot, however, you better get a good antivirus program for Windows. Microsoft's operating system and its bundled applications, Outlook and Internet Explorer, offer users powerful functionality in their attempts to be easy to use and easy to update. As a result, it's all too easy for virus writers to exploit the same functionality in a malicious way. Don't leave them an opening. Install an antivirus program and keep it updated.

The only time you'll need a Linux antivirus program is if you're running a mail server. And that's just good social behavior. It's not to protect your Linux server or client computer so much as to make sure you don't pass a virus on to a Windows system.

[http://www.linuxclues.com/articles/21.htm](http://www.linuxclues.com/articles/21.htm)

---

### Post by albinootje on 2009-01-22
> **Taz. said:**
>  Im just asking what would be a good AV for my ubuntu, to protect my windows partition and other pc's in my network what work on windows.. ?

If you are worried about giving viruses to your MS-Windows friends or MS-Windows relatives, install clamtk :
```

sudo apt-get install clamtk

```

Or if you're using Firefox on Ubuntu 8.10 with the Ubuntufox addon type this in the url field of Firefox :
```

apt://clamtk

```

---

### Post by 2hot6ft2 on 2009-01-22
ubuntu comes with clamav. If you want a gui for it use this in a terminal
Applications>Accessories>Terminal
```
sudo apt-get install clamtk
``` then it will be in
Applications>System Tools>Virus Scanner

---

### Post by sp0nge on 2009-01-22
[This]("http://librenix.com/?inode=21") is why you're pretty safe. 

Not that it can't happen. The point is that if you're doing something you shouldn't be or if someone wants your data badly enough, the chances are slim and none that you can stop them.

---

### Post by Taz. on 2009-01-22
And to install avast on ubuntu??? Wine?

---

### Post by albinootje on 2009-01-22
> **OrangeCrate said:**
> [http://www.linuxclues.com/articles/21.htm](http://www.linuxclues.com/articles/21.htm)

I would not recommend F-prot for Linux machines because :
- it is closed source software
- it has no installation instructions on the download webpage
- it offers a .tar.gz file, which is not cool for Linux beginners imho
- the install instructions are also not very "user friendly" 
  for Linux beginners

---

### Post by 2hot6ft2 on 2009-01-22
> **Taz. said:**
> And to install avast on ubuntu??? Wine?
To install avast, the linux version look here. [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

Avast and AVG only have 32 bit versions.

And to add avast to the menu the instructions are here. [http://forum.avast.com/index.php?topic=34748.0](http://forum.avast.com/index.php?topic=34748.0)

---

### Post by Taz. on 2009-01-22
Ahh ty, ill read it . And ill edit.

---

### Post by cariboo on 2009-01-22
If you have a well setup Windows installation in a  dual boot system, why worry about passing a virus to your windows partition. THe big thing to worry about is where those infected files arte coming from. Remember good security starts with the being between the back of the chair and the keyboard.

Jim

---

### Post by Taz. on 2009-01-22
thanks all for feedback. Now, i decided to put AVG theres a linux installer. When i run it, it says the following

error: wrong architecture '1386'


im losttttttt :(help.

---

### Post by cardinals_fan on 2009-01-22
I strongly recommend against signature-based antivirus apps on any platform.  If you have an infection, by all means scan every file on your computer with instantly-outdated definitions.  You have nothing to lose anymore.  However, running one day-to-day is absurd.

On Windows, I use ThreatFire in conjunction with a limited user account, NoScript, and common sense.  ThreatFire is an awesome heuristics-based AV that watches for nefarious behavior.  No need for definitions or manual scans.  On my Linux and BSD systems, I just use the limited accounts (default) and NoScript (well, common sense too ;)).  ThreatFire is Windows-only

The moral: a limited account, NoScript, and common sense are the keys to good security regardless of your OS.  Don't eat the free lunch and think before you act.  You'll be fine.

If you want to ignore me and install AVG anyway, you might need a 64-bit version if the i386 installer doesn't work.

---

### Post by OrangeCrate on 2009-01-23
> **albinootje said:**
> I would not recommend **F-prot for Linux** machines because :
- it is closed source software
- it has no installation instructions on the download webpage
- it offers a .tar.gz file, which is not cool for Linux beginners imho
- the install instructions are also not very "user friendly" 
  for Linux beginners

No, I wouldn't recommend it either. The article is just a well written, concise discussion on the need of an antivirus program for Linux, and that's my only reason for passing it along.

---

### Post by Taz. on 2009-01-23
Hey, guys, thanks fort he advices. But imma try AVG see what it can do to me. Now i need the 64x version, any idea would i be able to get it?

---

