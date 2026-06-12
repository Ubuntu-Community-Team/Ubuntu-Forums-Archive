---
title: "Why are there no viruses for Linux?"
date: 2008-12-14
forum: Recurring Discussions
---

### Post by upapilot on 2008-12-14
Hi!
I was just wondering why there are'nt any viruses and trojans and all that stuff on Linux now that its getting so popular.....What's so special about Linux that stops these viruses?:confused:

---

### Post by Trinix on 2008-12-14
Popularity has nothing to do with virus/trojan creation.  That is a myth of uneducated PC users originally engineered to explain why OS X is so secure.  Ubuntu, like OS X, has UNIX ties and therefore inherits its inherent security.  That's the short explanation.

Happy holidays,
Trinix

---

### Post by Drezard on 2008-12-14
The long explanation is, Unix is open source, so its source code can be viewed by anyone. This basically means, any developer can download it and spot security errors with it early and fix them. Compared to windows in which security faults are found but can only be fixed by microsoft developers (who, like all .net developers, have major mental deficiencies). 

Also, it is partly to do with the fact that 90% of Linux users know how to correctly set up a firewall and backups, so its a lot harder to penetrate and hold access on a linux machine, compared to point and click windows users. 

Daniel

---

### Post by jrusso2 on 2008-12-14
The big reason I think is that you don't run with root privileges which will not allow the virus to spread.

---

### Post by Shwefty on 2008-12-14
+1 on jrusso2

---

### Post by bodhi.zazen on 2008-12-14
[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

[http://librenix.com/?inode=21](http://librenix.com/?inode=21)

[http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)

[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

So, in a nut shell, Linux is designed differently from windows.

BUT, this is not the same as saying Linux in invulnerable

[http://www.damnvulnerablelinux.org/](http://www.damnvulnerablelinux.org/)

It is just the vulnerabilities are different is all.

I suggest you look at the stickies at the top of this sub forum ;)

---

### Post by iponeverything on 2008-12-14
In the past there has been episodes of great fanfare where a vendor of virus software announces the discovery a Linux virus in the wild. More than likely, as method of trying to open new markets. There is an unhealthy relationship between anti-virus vendors, computer manufacturers, and MS. It does not seem to be in the best interest of any of the players to eliminate viruses.  

There are a number of reasons that viruses have not been able to take hold under Linux. 

- Its open source. This eliminates the need for "backward compatibility" with previous versions of application software and allows the kernel to evolve quite rapidly. This prevents one bug from being exploitable across a large part of an install base. -- It also quickly exposes design flaws.  The longer a design flaw is allow to exist, the more deeply it is in-bedded in an operating system the and more difficult it is to address.  Microsoft made a good effort to address major design flaws with Vista, but it quickly fell prey to the same problem where a design flaw goes unnoticed long enough to become in-bedded -- where it can't be fixed without breaking a large number of applications. 

Viruses are so difficult tackle in windows because the vendors fingerprint individual viruses -- and attempts are rarely made to address the deeply in-bedded design flaw in the operating system that the viruses are taking advantage of.

Linux is GNU/GPL where contributors are not rewarded based on code output or their ability to make big clients happy. Contributors are rewarded though quality code and elegance of design. As a result, when design flaws are found they are fixed -- And because of fundamental differences in OS design between Windows and Unix like systems -- Linux is extremely modular -- this makes it very hard for design flaws to get in-bedded in the first place.

---

### Post by pietjanjaap on 2008-12-14
Firts why are there virussen in windows.
Because windows is not safe, very big not safe, windows has a bad firewall, open to scipts, activex, java, etc.
Everything you start in windows can install anything, everywhere.
In windows you need firewall en virusscanner, and still you are not safe.
If you look at the things the firewall and virusscanner try's to stop, check the settings, they control/check java, stripts activex, etc.
In windows you install software from servers(website's) you do not know, so you get spyware and virusses.
Msn unsafe.
internet explorer is unsafe.
I need 3 hours to make xp a little safe.(with install).
Microsoft does not care!!!!!!!!!!!!!!!!!!!!!!

All software in linux is on the ubuntu server, so no virussen and spyware.
(if you install from a different server, this is unsafe).
If you install software, you need a password, so a virus can not install.
Update windows 1 a month, ubuntu within a few days, much faster.
In windows software/programs are not updated, in ubuntu it is updated, because it is from the ubuntu server, security updates get updated, so you also.

---

### Post by PmDematagoda on 2008-12-14
> **pietjanjaap said:**
> All software in linux is on the ubuntu server, so no virussen and spyware.
(if you install from a different server, this is unsafe).

This is not a reason to blindly trust the Ubuntu packages, if you look at what happened to Red Hat some time back, their servers were infiltrated and a few packages were even altered, fortunately the attack did not affect many(or perhaps any?) Red Hat/Fedora users. However that incident means that you cannot fully trust any source and you need to use all sources carefully.

---

### Post by bryanl on 2008-12-14
It is all about the users.

People who like the convenience of not keeping their doors locked and their property secured will suffer theft and loss, especially in a crowded community.

When Microsoft started locking doors by default (e.g. the UAC in Vista) just look at the complaints. Contrast that to the lockdown default in most linux distributions and the complaints about using sudo.

For someone trying something malicious, there are indeed odds at scale. You are more likely to succeed if your efforts attack 90% of the market, especially when that market has no interest in even find out about door locks. These are the folks that click on email links indiscriminately. 

Choosing Windows is a decision often delegated to a VAR while those who choose Linux or Apple had to make their own decision. That has implications on this issue as well.

You can run a Windows system and be as secure as running a Linux or Apple system and many businesses do so.

But the larger Windows community is quite crowded with very very many who pay no attention to security and that means ripe picking for the vandals, thieves, mischief makers, and other obnoxious sorts.

---

### Post by cardinals_fan on 2008-12-14
> **bryanl said:**
> It is all about the users.

People who like the convenience of not keeping their doors locked and their property secured will suffer theft and loss, especially in a crowded community.

When Microsoft started locking doors by default (e.g. the UAC in Vista) just look at the complaints. Contrast that to the lockdown default in most linux distributions and the complaints about using sudo.

For someone trying something malicious, there are indeed odds at scale. You are more likely to succeed if your efforts attack 90% of the market, especially when that market has no interest in even find out about door locks. These are the folks that click on email links indiscriminately. 

Choosing Windows is a decision often delegated to a VAR while those who choose Linux or Apple had to make their own decision. That has implications on this issue as well.

You can run a Windows system and be as secure as running a Linux or Apple system and many businesses do so.

But the larger Windows community is quite crowded with very very many who pay no attention to security and that means ripe picking for the vandals, thieves, mischief makers, and other obnoxious sorts.
+1

Superb post.

---

