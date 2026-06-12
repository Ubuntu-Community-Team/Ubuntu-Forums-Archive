---
title: "Do I need clamav &gt;"
date: 2009-10-06
forum: Recurring Discussions
---

### Post by plutonium45 on 2009-10-06
Hi all.
do I need to install clamav ?
is it necessary ??
please tell me your opinions..
thanks !

---

### Post by SuperSonic4 on 2009-10-06
no

besides clamav gives far too many false positives

---

### Post by H4F on 2009-10-06
In case you have dual boot to windows yes.
And in case you bring infected pendrives to your pc and wanting to clean them .

---

### Post by plutonium45 on 2009-10-06
if I run a viral exe program through wine , what are the possibilities ?

---

### Post by wojox on 2009-10-06
> **plutonium45 said:**
> if I run a viral exe program through wine , what are the possibilities ?

None

---

### Post by XCan on 2009-10-06
Tbh, even if you dual boot windows having clamav or not shouldn't matter. I can't think of any Windows machine that can survive with antivirus software.

---

### Post by Anarci on 2009-10-06
The main reason for installing clamav on linux is to help stop the spread of viruses to more windoze boxes  through email etc.

---

### Post by cariboo on 2009-10-06
How is a virus going to spread, if all the windows computers have valid av software. Let the Windows users look after themselves, it's not your problem.

---

### Post by nickweavers on 2009-10-06
It's a problem if your Ubuntu box is a webserver since if you get infected and are used as a spam relay, your domain will get blacklisted.

---

### Post by hantechbl on 2009-10-06
No, since viruses are targeted at windows and the Linux os is not vulnerable to these viruses.

---

### Post by cariboo on 2009-10-06
> **nickweavers said:**
> It's a problem if your Ubuntu box is a webserver since if you get infected and are used as a spam relay, your domain will get blacklisted.

You are mixing up getting cracked and being used as a spambot, and the common Windows virus.

The definition of a computer virus:

> The term "virus" is also commonly but erroneously used to refer to other types of malware, adware, and spyware programs that do not have the reproductive ability. A true virus can only spread from one computer to another (in some form of executable code) when its host is taken to the target computer; for instance because a user sent it over a network or the Internet, or carried it on a removable medium such as a floppy disk, CD, DVD, or USB drive.

That being said, the reason most linux powered servers are cracked is due to poor passwords, runniing unneeded services, and lack of knowledge by the operator.

It is pretty easy to get a Linux powered server up and running, there plenty of guides available. The big problem is between the back of the chair and the keyboard. Just do a search of this forum and you will find many servers that were cracked due to the owner running vnc with a weak or no password at all.

That I fear is going to be a big problem as Linux gets more popular, Just like Windows was when they made it easy to set up a web server.

---

### Post by nickweavers on 2009-10-07
> **cariboo907 said:**
> You are mixing up getting cracked and being used as a spambot, and the common Windows virus.
 You are right that the types of infection (commonly worms or viruses) that are prevalent in the windows world are rarely a problem in linux, so if you are running ubuntu as your OS of choice on you desktop/laptop you probably have little to worry about. I guess the point I meant to make, but that you kindly made for me in the rest of your post, is that clamav protects against more that just viruses in the strict sense of the definition and since @plutonium45 asked for opinions on whether it was necessary or advisable to install clamav on ubuntu without saying what the platform was being used for I thought I would point out that that this is worth considering. Since my (relatively limited) experience has been with Linux on web servers, my opinion is that it is worth having it installed as it detects things like the C99Shell (good article here: [http://blog.stodge.org/486](http://blog.stodge.org/486)). Once a hacker finds a way of getting this file onto your server in a location he can find and use in a URL, it will give him a web page with a "control panel" that will allow him to attempt further hacks as he is now running with the userid of apache or nobody with the whatever privilages that confers. As far as I have been able to learn so far, the way this shell gets put on your server is often via a file uploader which may be part of a web application you have installed, such as Wordpress or Joomla. It may be that these apps do not rigorously check the type of file that is being uploaded. I am now learning about AppArmor which looks like another useful tool to have installed in the battle against hackers. There is a good "sticky" about it in this section of the forum.

Anyway, I hope that helps.

---

### Post by plutonium45 on 2009-10-07
Thanks for the replies..
I came to an inference that I dont need any av..because I dont dual boot..and I dont bother about windows users :lolflag:

---

### Post by __p1n__ on 2009-10-07
> **wojox said:**
> None

That's not exactly accurate.  Some CPU's that support SMM mode are vulnerable to direct shellcode-based attacks regardless of the running o/s.  You *could* run some windows malware in wine, in a type 2 PVM or even a type 1 HVM and still end up with a ring -1 rootkit installed in SMRAM.

edit: wrt the op I'm not certain whether or not clamav detects SMM attacks.  It's virtually certain that no av product could intercept a running process that is attempting the exploit (it's attacking the cpu directly) however it's possible that a data pattern corresponding to known exploit signatures could be detected at a file/stream level.

---

### Post by Jive Turkey on 2009-10-08
My opinion is to not bother with AV on any platform, but use backups and hardening everywhere you can.

---

### Post by dyingsun on 2009-10-16
Just because Linux is very unlikely to be infected, doesn't mean that viruses (virii?) can't pass through by piggybacking on a file you may send to other people, especially through email, etc. You may never be aware of it, but could unwittingly transmit it to the less fortunate (read: Windows users). Sure, it's not (directly) our problem , but I personally find malware offensive, and am basically opposed to it, so if I can stop it passing through my machine, that's one (extremely small) step. 

Most of the people whose machines are infected are going to be people with little technical knowledge; they just buy whatever software the local egghead tells them they need, and they assume they're protected. Probably with Norton. My point is we shouldn't thumb our noses at the Untouchables - we should be doing our part to stop malicious programs from spreading.

Or you could just say "Stuff you, deal with it yourselves", if you think that's the kind of image you want Linux to present to the world.

---

### Post by Grimhound on 2009-10-17
Unless you're living in a magical fantasy world where everything runs on Linux or viruses don't exist, I'd say having antivirus software is an important courtesy to hold if you ever interact with computers running Windows. Imagine running nonchalant and then inadvertently bringing down an entire computer network because a certain type of virus managed to get on a USB stick.

Edit: dyingsun beat me to it.

---

### Post by Tipped OuT on 2009-10-17
I consider anti viruses to be training wheels for the beginners. Soon my friends, you too will be wise enough not to double click that application you got from a random site. ;)

Of course for servers, it's an entirely different case.

---

### Post by BigSilly on 2009-10-17
> **__p1n__ said:**
> That's not exactly accurate.  Some CPU's that support SMM mode are vulnerable to direct shellcode-based attacks regardless of the running o/s.  You *could* run some windows malware in wine, in a type 2 PVM or even a type 1 HVM and still end up with a ring -1 rootkit installed in SMRAM.

edit: wrt the op I'm not certain whether or not clamav detects SMM attacks.  It's virtually certain that no av product could intercept a running process that is attempting the exploit (it's attacking the cpu directly) however it's possible that a data pattern corresponding to known exploit signatures could be detected at a file/stream level.

I'd love it if someone here could decipher this post for me! Just because I use Linux, it doesn't mean I'm necessarily *this* technically adept! :D

I've only ever run AV on Linux sporadically, and it's never found anything. It's not something I worry about too much on Ubuntu, for good or for ill.

---

### Post by itsols on 2010-08-09
This is a very interesting issue...

1. I'm about to REMOVE ClamAV from my laptop because it seems to interfere with my Graphics on Lucid. Not relevant...

2. The more important issue is this:

If I open an infected MS-WORD file or EXCEL file on Open Office, can my Ubuntu system get infected as well? I mean WITHOUT an AV program...

Thanks a lot!

---

### Post by ronnielsen1 on 2010-08-09
> If I open an infected MS-WORD file or EXCEL file on Open Office, can my  Ubuntu system get infected as well? I mean WITHOUT an AV program...
No, with or without an AV program.

---

### Post by itsols on 2010-08-09
Thank you for the feedback!

It somehow gets me worried to think how, if an Excel file with macros can be opened on Ubuntu, the system does NOT get infected. hmmm...

Anyway, the main thing is that if it doesn't infect, then that's sufficient - pretty smiles

---

