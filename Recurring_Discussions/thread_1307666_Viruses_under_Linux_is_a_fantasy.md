---
title: "Viruses under Linux is a fantasy?"
date: 2009-10-31
forum: Recurring Discussions
---

### Post by mers_10 on 2009-10-31
Viruses under Linux is a fantasy?
 Whether there are viruses under Linux and whether it is necessary to put an antivirus?:(

---

### Post by pi4r0n on 2009-10-31
You do not need to install any antivirus software on your linux system :)

Remember that LINUX OS's are virus free

Ta

pi4r0n

---

### Post by mers_10 on 2009-10-31
All the same it is necessary to put Anti-viruses (personally my opinion) for SAFETY!!

---

### Post by NCLI on 2009-10-31
...why? I mean, there are currently no known Linux viruses in the wild, so all your anti virus program would do is protect your Windows friends from viruses you might accidentially send them, and waste system resources.

---

### Post by pi4r0n on 2009-10-31
If you are thinking to do FTP server or simular things then yes I would sugest to have one as people might stick some dogy software on your server, but if its a single OS just for you then no

I have been working on linux for the last 10 years and to the honest with you I have not have not a single virus :)

Cheers

pi4r0n

---

### Post by cascade9 on 2009-10-31
Theres linux viruses, but its nothign major to worry about...IMO anyway. I would only run anti-virus on linux if I was running a mailserver. 

> There has not yet been a single widespread Linux malware threat of the type that [Microsoft Windows]("http://en.wikipedia.org/wiki/Microsoft_Windows") software currently faces; this is commonly attributed to the malware's lack of root access and fast updates to most Linux vulnerabilities.[]("http://en.wikipedia.org/wiki/Linux_malware#cite_note-Yeargin-1")

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

---

### Post by 23meg on 2009-10-31
Moved to Recurring Discussions.

---

### Post by sdowney717 on 2009-10-31
you know someone could write a script in an install program that needs sudo privileges and insert some malicious code and almost no one would know, unless someone examines the code in detail.
 I think the only reason we dont see this is simply because linux has such a small part of the desktop market.

---

### Post by NoaHall on 2009-10-31
> **sdowney717 said:**
> you know someone could write a script in an install program that needs sudo privileges and insert some malicious code and almost no one would know, unless someone examines the code in detail.
 I think the only reason we dont see this is simply because linux has such a small part of the desktop market.

No. It's due to the way the system works. To cause damage, you'd have to run the file as root/sudo, which requires your input.

---

### Post by NCLI on 2009-10-31
> **sdowney717 said:**
> you know someone could write a script in an install program that needs sudo privileges and insert some malicious code and almost no one would know, unless someone examines the code in detail.
 I think the only reason we dont see this is simply because linux has such a small part of the desktop market.
I think this would be discovered pretty quickly.... Besides, most of the software we use is installed from the official repos, where both the uploader and the programmers are easy to identify, or from a PPA, which can only be created by people who have signed the Ubuntu cod of conduct, and can be identified. Installing some unknown .deb file is probably the only way this could occur.

---

### Post by MrNatewood on 2009-10-31
> **NoaHall said:**
> No. It's due to the way the system works. To cause damage, you'd have to run the file as root/sudo, which requires your input.

Hacking to a package in the ubuntu repository and compiling it with malicious code would do the trick.

---

### Post by NoaHall on 2009-10-31
> **MrNatewood said:**
> Hacking to a package in the ubuntu repository and compiling it with malicious code would do the trick.

That's not very likely. And should it happen, it will be reported, and dealt with within minutes.

---

### Post by NCLI on 2009-10-31
Not to mention that the uploader would be easily identified. Not a good idea.

---

### Post by steveneddy on 2009-10-31
I don't install virus scanners to protect my Windows using friends.

If I happen to unknowingly send a virus in a forwarded attachment to a Windows using friend, then I believe it is their responsibility to scan their system and mail attachments for issues.

I have never in the last five years had any virus related issues on any machine running Linux that I administer.

---

### Post by DonaldJ on 2009-11-01
> **sdowney717 said:**
> you know someone could write a script in an install program that needs sudo privileges and insert some malicious code and almost no one would know, unless someone examines the code in detail.



I think there are thousands of good genius folks, globally, who examine everything new for Linux, in fine detail, so "fiddledee-dee jerks" don't give Linux a bad rep...  Linux is based upon love..  there are those who defend Linux with all they've got...  Me thinks were safe from that ever happening...  but there are the occasional bad one who  does  damage to an individual's hd..  like yesterday someone somehow got into my hd's 910, and made it slow down a lot, and made it so it couldn't find an OS on reboot...  
I fixed it by installing another hd, booted, then shutdown after the desktop came up, then reinstalled the hd which wouldn't bootup.. and the problem was cured... Obviously someone changed something in the Bios...
In the light of that incident, I thinks Ubuntu needs some sort of fine security software that doesn't permit whatever was done to make changes in a PC's bios...  Obviously the Router, and FW, and Clam, weren't enough to keep the bully out...  The bully really knew what it was doing...

---

### Post by fiklein on 2009-11-04
Like any operating system, it is better to do everything using  a non-privileged user account except downloading upgrades from known sites. There are not many Linux viruses, but no software is invulnerable.

---

### Post by Bios Element on 2009-11-04
> **fiklein said:**
> Like any operating system, it is better to do everything using  a non-privileged user account except downloading upgrades from known sites. There are not many Linux viruses, but no software is invulnerable.

Which ya know, ubuntu does by default. So it's a non-issue.

---

### Post by lisati on 2009-11-04
> **steveneddy said:**
> 
If I happen to unknowingly send a virus in a forwarded attachment to a Windows using friend, then I believe it is their responsibility to scan their system and mail attachments for issues.


Agreed, the recipient of emails probably has the major portion of responsibility for checking what they put on their system. 

**But:** you might be interested in clause 6.h [here]("http://info.yahoo.com/legal/us/yahoo/utos/utos-173.html"): 

> You agree to not use the Yahoo! Services to:
upload, post, email, transmit or otherwise make available any material that contains software viruses or any other computer code, files or programs designed to interrupt, destroy or limit the functionality of any computer software or hardware or telecommunications equipment;

---

### Post by kyuubi777 on 2009-11-04
my main problem with buying stupid antivirus software is ... who do you think makes the viruses in the first place??. i'd be prepared to put money down that when the guys at norton find some spare time they go out for a cup of coffee and think of the next generation of malware to deliver to the world... that's what i'd do.. makes coming up w/ the solution a lot easier.

---

### Post by aysiu on 2009-11-05
> **kyuubi777 said:**
> my main problem with buying stupid antivirus software is ... who do you think makes the viruses in the first place?? My main problem with it is that antivirus does **nothing** to protect you from security threats. You're better off properly locking down your computer and also learning about social engineering than relying on placebos (aka antivirus) to "protect" you. And that's true for Windows, too.

---

### Post by Eddie Wilson on 2009-11-05
> **DonaldJ said:**
> I think there are thousands of good genius folks, globally, who examine everything new for Linux, in fine detail, so "fiddledee-dee jerks" don't give Linux a bad rep...  Linux is based upon love..  there are those who defend Linux with all they've got...  Me thinks were safe from that ever happening...  but there are the occasional bad one who  does  damage to an individual's hd..  like yesterday someone somehow got into my hd's 910, and made it slow down a lot, and made it so it couldn't find an OS on reboot...  
I fixed it by installing another hd, booted, then shutdown after the desktop came up, then reinstalled the hd which wouldn't bootup.. and the problem was cured... Obviously someone changed something in the Bios...
In the light of that incident, I thinks Ubuntu needs some sort of fine security software that doesn't permit whatever was done to make changes in a PC's bios...  Obviously the Router, and FW, and Clam, weren't enough to keep the bully out...  The bully really knew what it was doing...

So you don't really know what happened or why. Why do you think someone changed something in the BIOS? Sorry but this just doesn't make any sense.

---

### Post by Calmatory on 2009-11-05
> **pi4r0n said:**
> 
I have been working on linux for the last 10 years and to the honest with you I have not have not a single virus :)

Cheers

pi4r0n

You know this how?

---

### Post by aysiu on 2009-11-05
> **Calmatory said:**
> You know this how?
You never know it **even if you have "antivirus" installed**.

Antivirus is not perfect detection. It is very imperfect as a matter of fact. So it doesn't matter if someone without antivirus proclaims she has never had a single virus. It's about as credible as someone with antivirus making the same proclamation.

---

### Post by Roasted on 2009-11-05
Although Linux is really secure, it's a piece of software, and all software can be vulnerable to viruses. At the same token, I'm a realist - and there's so few Linux viruses out there it's unreal.

Do I run antivirus software on my Linux computer? Yes, I do.

Why?

Because my Windows systems in the house back up to my Linux computer, so I run ClamAV to make sure my backups are clean so if I ever need to pull a backup, I don't pull a virus-infected backup. 

So it's kind of ironic I run AV software on my Linux box for the sake of my Windows boxes... :lolflag:

---

### Post by Sporkman on 2009-11-05
> **NoaHall said:**
> No. It's due to the way the system works. To cause damage, you'd have to run the file as root/sudo, which requires your input.

No - you could steal data or set up services as a user (services which get started when the user logs in).

---

### Post by jward3010 on 2009-11-05
This I think is essentially correct. Be skeptical, don't even trust Ubuntu apps, I somehow have way more trust in open source coding in that it usually just does what it says on the tin and no more (no uploading of user stats, geolocation info etc. which was technically in the 10 page legalese EULA that a barrister has difficulty understanding). But at the same time, if open source apps begin to move in the direction of doing a little more than whats on the tin then the community gets very skeptical and will fight it undoubtedly. Thats the beauty of open source and a great way of showing how it's culture specifically churns out good principals.

---

### Post by jward3010 on 2009-11-05
> **Roasted said:**
> So it's kind of ironic I run AV software on my Linux box for the sake of my Windows boxes... :lolflag:
Thats about the only reason it's done especially on Linux servers serving e-mail to Windows clients. ClamAV will be there to check incoming and outgoing messages for crap that shoudln't be there - for the Windows community. Not the Linux one funnily enough.

---

### Post by Zimmer on 2009-11-05
Smile...
[http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)

---

### Post by Supersquirrel on 2009-11-05
Nah viruss are elimanted by the lymphocytes in computers.

---

### Post by Sporkman on 2009-11-05
> **Zimmer said:**
> Smile...
[http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)

I don't get it...?

---

### Post by cariboo on 2009-11-05
Obviously you didn't download **evilmalware.tar.gz** :)

---

### Post by Calmatory on 2009-11-06
> **aysiu said:**
> You never know it **even if you have "antivirus" installed**.

Antivirus is not perfect detection. It is very imperfect as a matter of fact. So it doesn't matter if someone without antivirus proclaims she has never had a single virus. It's about as credible as someone with antivirus making the same proclamation.

My question stands. ):P

---

### Post by Exodist on 2009-11-06
> **pi4r0n said:**
> You do not need to install any antivirus software on your linux system :)

Remember that LINUX OS's are virus free

Ta

pi4r0n

FUD

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

---

### Post by jward3010 on 2009-11-06
Is it funny - is it an actual virus. Or is it something to do with the work you have to do to actually install a virus.

---

### Post by DonaldJ on 2010-03-16
In Linux viruses, it's the hack-you attacker acting out most of the virus whilst messing in your hd...  It may seem like a virus.. and essentially it is..  It's just that most of the virus is personal hateful human activity, in short "bullying"...  Seems there's a bully in every box of good...

---

