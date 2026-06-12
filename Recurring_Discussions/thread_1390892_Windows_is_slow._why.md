---
title: "Windows is slow. why?"
date: 2010-01-26
forum: Recurring Discussions
---

### Post by bobin on 2010-01-26
Yes we all know this fact , but why is it so? Also why does IT get slower with time?

---

### Post by SuperSonic4 on 2010-01-26
It's massively bloated to accodomate too many users.

I believe it gets slower because each new program writes to the registry and this must be looked up each time a program is run. Plus deleting a program through control panel does not remove the registry entry

---

### Post by Paqman on 2010-01-26
> **bobin said:**
> Yes we all know this fact

Er, no we don't. A default Windows install is pretty nippy, actually. Often what gives the impression that it's slow is the vast amount of rubbish OEMs install on machines, particularly laptops. Some of the antivirus suites also involve a hefty performance hit.

> Also why does IT get slower with time?

Generally with Windows this is because of the way it handles installing and removing software. Windows lacks an integrated package manager, so things tend to get into a bit of a mess after a while. Also NTFS is slightly more prone to fragmentation than more modern filesystems, although it's not as bad as some people make out. It was FAT that gave Windows a bad rep for fragmentation, and it seems to have stuck.

---

### Post by lisati on 2010-01-26
As you use Windows, there is a tendency for clutter (in the form of temporary files) to build up. In theory, a well-behaved program cleans up after itself, but the reality is that it doesn't always happen that way. Then when you figure in stuff like system restore information and file fragmentation.......

(Oh, this is beginning to sound like spam, see sig.....)

---

### Post by mikewhatever on 2010-01-26
> **bobin said:**
> Yes we all know this fact ,,,,,,

Please, do speak for yourself.

---

### Post by chewearn on 2010-01-26
It's a conspiracy.  Microsoft is in cahoot with the computer industry.  Making things run slower as time goes by ensure that the consumer wants to upgrade to the latest and greatest hardware and software forever.

P.S.
Woot! Finally got to use the phrase "in cahoot". :mrgreen:

---

### Post by bobin on 2010-01-26
then why does't MS fix this?

---

### Post by SuperSonic4 on 2010-01-26
Why should they? 90% of people use windows and pay for windows. It makes no economic sense at the moment

---

### Post by Paqman on 2010-01-26
> **bobin said:**
> then why does't MS fix this?

A large part of the problem is caused by the behaviour of OEMs and badly written software from 3rd parties, not Microsoft.

---

### Post by ajgreeny on 2010-01-26
Don't forget almost every application/program installed in windows, not only adds a lot of guff to the huge registry file, but also generally adds a utility for the program to automatically check every time you boot, or use the program, for updates.  That means you can have many many updating applications running together at boot time looking for updates to whatever it is.

Also the loading of firewall applications eg Zonealarm, and virus checker software takes a fair part of your resources all the time you are running windows.

---

### Post by warfacegod on 2010-01-26
> **Paqman said:**
> Er, no we don't. A default Windows install is pretty nippy, actually. Often what gives the impression that it's slow is the vast amount of rubbish OEMs install on machines, particularly laptops. Some of the antivirus suites also involve a hefty performance hit.



Generally with Windows this is because of the way it handles installing and removing software. Windows lacks an integrated package manager, so things tend to get into a bit of a mess after a while. Also NTFS is slightly more prone to fragmentation than more modern filesystems, although it's not as bad as some people make out. It was FAT that gave Windows a bad rep for fragmentation, and it seems to have stuck.

When I had XP on an NTFS drive, it would become horribly fragmented after only 1 month or so.

---

### Post by warfacegod on 2010-01-26
> **Paqman said:**
> A large part of the problem is caused by the behaviour of OEMs and badly written software from 3rd parties, not Microsoft.

That's because Windows lends itself to "sloppy" programming and not the other way around.

---

### Post by frodon on 2010-01-26
Moved to "Recurring Discussion"

---

### Post by Paqman on 2010-01-26
> **warfacegod said:**
> When I had XP on an NTFS drive, it would become horribly fragmented after only 1 month or so.

What do you call "horribly fragmented" though? And how were you using the drive? I use XP on an NTFS partition occasionally, and it was my main system for years. It only ever picks up a little fragmentation. Certainly never enough to noticeably affect performance.

> **warfacegod said:**
> That's because Windows lends itself to "sloppy" programming and not the other way around.

And other OSes don't? I'm sure there are plenty of badly written Linux apps. I'm no code monkey, but I know there have been some fairly high profile examples of horrific code like Automatix.

In what way would you say Windows particularly encourages sloppy programming?

---

### Post by rapidog on 2010-01-26
> **bobin said:**
> Also why does IT get slower with time?


There's a number of factors why this happens, not just a reg build up,

---

### Post by warfacegod on 2010-01-26
> **Paqman said:**
> What do you call "horribly fragmented" though? And how were you using the drive? I use XP on an NTFS partition occasionally, and it was my main system for years. It only ever picks up a little fragmentation. Certainly never enough to noticeably affect performance.



And other OSes don't? I'm sure there are plenty of badly written Linux apps. I'm no code monkey, but I know there have been some fairly high profile examples of horrific code like Automatix.

In what way would you say Windows particularly encourages sloppy programming?

Up until three years ago XP was my sole OS. After a month or so of daily use, Windows defragger, Auslogic, Defraggler, and Diskeeper would all report betwee 40 - 60% fragmentation on my 80 GB primary HDD that was never more than 30% used space.

I don't claim that other OS's don't have bad coding as well, just that Windows has a monopoly on it. MS writes bad code themselves. Using Internet Explorer in a Limited User Account is just a bad idea, at least in XP it is. The fact that things like Glary Utilities and Ccleaner are practically required to run Windows speaks boat loads about how software gets coded for Windows. Installing a program, let alone running it, potentially dire consequences for the registry. I just downloadwed the .exe files for Amarok and iTunes. Amarok's was 2 MB, iTunes was 90 MB. Not that I'm claiming that Amarok 2.2 is any good but you get the idea. I used Windows for six years and every two to four months it would become totally unbootable. I've used Ubuntu for three, two exclusively Linux, and I am just now having my first real, critical failure. I run a tight ship. Everything stays neat and orderly and I'm not prone the whole: ooh! that looks neat, click, idiocy that so many users are fond of.

---

### Post by Techsnap on 2010-01-26
What a load of rubbish, the OP has never installed Windows using proper installation media and has obviously only used OEM installs. Also Windows does not slow down over time, it's how people use it. 
 
A lot of applications like to install pointless "Helpers" on boot, Apple, Adobe, Cyberlink etc are common ones I find when I work on a customers PC. These can sometimes really slow down the Windows install though this is not Microsofts fault that companies are doing this with their software. A lot of people generally don't clean their systems up anyway, a few hours with a few tools can usually solve this problem. I have an XP install here which I did in 2005 which works just as good now as it did when I installed it. 
 
Learn to use Windows before posting made up stuff.
 
> I run a tight ship. Everything stays neat and orderly
 
Ubuntus package maintainers like to add a lot of dependencies you'll never need, as long as you're running Ubuntu I'd say it's far from neat and orderly :P.

---

### Post by Roasted on 2010-01-26
> **Paqman said:**
> What do you call "horribly fragmented" though? And how were you using the drive? I use XP on an NTFS partition occasionally, and it was my main system for years. It only ever picks up a little fragmentation. Certainly never enough to noticeably affect performance.



And other OSes don't? I'm sure there are plenty of badly written Linux apps. I'm no code monkey, but I know there have been some fairly high profile examples of horrific code like Automatix.

In what way would you say Windows particularly encourages sloppy programming?

As somebody who works in a large Windows environment, I feel like I can pose a relatively accurate opinion here.

There's absolutely no doubt that Windows begins to bow under the weight of its own registry in time. The programs are no doubt bloated in comparison to Linux comparable applications. While I do not have to defrag my systems at home that frequently, the systems here at work require monthly attention or they begin to slump along badly. It's an incredibly headache-infatuated job to be in a Windows network like this, because I'm constantly running. Re-image this lab, redo this, redo that. And for who? For what? Because Windows is barfing more errors? Because it's fragmented and running slow already? Because the profile is corrupt and users can't log in?

Again, as a home user, I have VERY little issues (and my Windows PC is Vista of all things). In fact, I probably have close to zero issues with Vista at home. Granted I only use it for minor testing and gaming, but I've ran it for about 2 years without issues. But at work, to say it's a headache is an understatement. 

If Windows is your thing, have at it. But at the end of the day I have to use what works. And that's exactly why I do not have Windows on my work laptop.

---

### Post by warfacegod on 2010-01-26
> **Techsnap said:**
> Ubuntus package maintainers like to add a lot of dependencies you'll never need, as long as you're running Ubuntu I'd say it's far from neat and orderly :P.

That's why I use synaptic to remove as many as I can find.

---

### Post by Ylon on 2010-01-26
I am sure that when XP did come out, there was some protest by Hardware resellers delivered to Microsft becouse XP's low requiment of 64~128megs (many RAM banks remain in stores).
Microsoft did "fix" this stuff with Vista (minim req was 1GiB ram).. and this time were the clients which protested about it (we all know how much public "loves" Vista perfomance+puls "sh1t to low perfomance" pre-installed by HWM).

Windows is slow or fast (resource requiment) not for some result of Microsoft works... but on "market need" basis.


All: IMHO

---

