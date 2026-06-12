---
title: "Security stuff"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-06-11
Hi all

I am new to linux, but I'm eager to learn.I'm been using Ubuntu for about 2 months and I love it.If I could make my favorite games to work on it (Heroes III, Heroes V and Warcraft III on BattleNet, I would trash windows for good).I was curios why there are so few (or non) linux viruses and hundreds of thousands Windows viruses.Why can linux viruses can not be created, and if it can, why nobody does it?And if the OS is open source, why nobody messes with the code so it will screw the system (a windows employ for example :lolflag:).What are the differences between the windows "recipe" and the linux "recipe"?What exactly is a kernel and how is different from the windows system?
Thx and excuse my noob-idity. :)

---

### Post by powerpleb on 2008-06-11
> **Troll_the_Great said:**
> Hi all

I am new to linux, but I'm eager to learn.I'm been using Ubuntu for about 2 months and I love it.If I could make my favorite games to work on it (Heroes III, Heroes V and Warcraft III on BattleNet, I would trash windows for good).I was curios why there are so few (or non) linux viruses and hundreds of thousands Windows viruses.Why can linux viruses can not be created, and if it can, why nobody does it?And if the OS is open source, why nobody messes with the code so it will screw the system (a windows employ for example :lolflag:).What are the differences between the windows "recipe" and the linux "recipe"?What exactly is a kernel and how is different from the windows system?
Thx and excuse my noob-idity. :)

Nice nick

---

### Post by Troll_the_Great on 2008-06-11
Thx.Troll is my nickname.I heard a internet troll is something bad (but I don't know what is it), but my nickname comes from old Norse mythology.

---

### Post by powerpleb on 2008-06-11
> **Troll_the_Great said:**
> Thx.Troll is my nickname.I heard a internet troll is something bad (but I don't know what is it), but my nickname comes from old Norse mythology.

A troll is someone who deliberately posts something contentious looking for a reaction rather than making a genuine contribution.

---

### Post by ibuclaw on 2008-06-11
How ironic... :)

I believe this is what you are looking for Troll.
It is entitled: "[**The short life and hard times of a Linux virus**]("http://librenix.com/?inode=21")"

Regards
Iain

---

### Post by decoherence on 2008-06-11
Well, Troll or no here are your answers.

There are two key reasons why linux has so few viruses. First, it's not the mainstream system. Virus writers want their viruses to affect as many computers as they can. The second reason is that Windows has had to maintain a huge amount of backward compatibility. They can't simply demand that everybody buy the latest upgrade. As a result there is a significant amount of 'cruft' in Windows that can be exploited by viruses. With Linux systems, on the other hand, it's no big deal to get people to upgrade since everything is free anyway. Plus the upgrade process (for ubuntu anyway) is years ahead of Windows and nearly effortless.

Note that with the more security-conscious Vista, a lot of the backward compatibility was lost. Getting rid of insecure code was one reason why.

As to your second question about it being open source and people messing with it... it may be open source, and you may be free to mess with it, but if you want your changes included in the official distribution, you still have to submit your code to the project who will review it and accept or reject it.

Still, sometimes I wonder, what with those hard freezes that were going on a while back (and thankfully have stopped for me!)

---

### Post by decoherence on 2008-06-11
On a lighter note, here's a more humorous take on why linux viruses don't do well (from the FSF email archives, credited to Charlie Harvey)

> evilmalware 0.6 (beta)

Copyright 2000, 2001, 2003, 2005
E\/17 |-|4><0|2z Software Foundation, Inc.

This is free software; see the source for copying conditions.  There is
NO warranty; not even for MERCHANTABILITY, COMPLETE DESTRUCTION OF IMPORTANT 
DATA or FITNESS FOR A PARTICULAR PURPOSE (eg. sending thousands of Viagra 
spams to people accross the world).

Basic Installation
==================

Before attempting to compile this virus make sure you have the correct
version of glibc installed, and that your firewall rules are set to `allow 
everything'.

1. Put the attachment into the appropriate directory eg. /usr/src

2. Type `tar xvzf evilmalware.tar.gz' to extract the source files for 
   this virus.

3. `cd' to the directory containing the virus's source code and type
   `./configure' to configure the virus for your system.  If you're
   using `csh' on an old version of System V, you might need to type
   `sh ./configure' instead to prevent `csh' from trying to execute
   `configure' itself.

4. Type `make' to compile the package. You may need to be logged in as 
   root to do this.

5. Optionally, type `make check_payable' to run any self-tests that come 
   with the virus, and send a large donation to an unnumbered Swiss bank 
   account.

6. Type `make install' to install the virus and any spyware, trojans
   pornography, penis enlargement adverts and DDoS attacks that 
   come with it.
  
7. You may now configure your preferred malware behaviour in 
   /etc/evilmalware.conf .

SEE ALSO
   evilmalware(1), evilmalware.conf(5), please_delete_all_my_files(1) 

---

### Post by Troll_the_Great on 2008-06-11
So I don't have to worry about viruses while running Ubuntu, no?

---

### Post by Troll_the_Great on 2008-06-11
And another thing.A virus can't come from a debian package?Or by clicking a link?

---

### Post by ladr0n on 2008-06-11
Someone could include some sort of virus in a debian package.  It's possible, but extremely unlikely.  Also, you don't have to worry about anything you get from the official Ubuntu repo's.  Just don't install a random .deb you stumble upon on the 'net unless you trust the site you get it from.

---

### Post by Het Irv on 2008-06-11
And if you are that worried about Links, check out the No-Script Extention for Firefox.

There are a few Anti-virus programs for Linux, but they are for scanning outgoing traffic, for example if you were sending mail to a Windows machine.  Of course, it doesn't matter what OS you use, if you arn't careful, any OS can be messed with.

---

### Post by bodhi.zazen on 2008-06-11
Welcome Troll

Ubuntu (Linux) security is a little different then other OS.

Please start with this thread :

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Troll_the_Great on 2008-06-12
Thank you all for your answers, thou I didn't fully understand all of them. I don't know what is "backward compatibility" that windows has to maintain, and what "cruft" means.Can someone detail a little bit more this subject?

---

### Post by SunnyRabbiera on 2008-06-12
> **ladr0n said:**
> Someone could include some sort of virus in a debian package.  It's possible, but extremely unlikely.  Also, you don't have to worry about anything you get from the official Ubuntu repo's.  Just don't install a random .deb you stumble upon on the 'net unless you trust the site you get it from.

correct, thats why most say stick to the repositories.
but even if a virus is included in a deb it will have a tough time operating unless it does something to the kernel.

---

### Post by decoherence on 2008-06-12
> I don't know what is "backward compatibility" that windows has to maintain, and what "cruft" means.Can someone detail a little bit more this subject?

Basically it means newer versions of Windows can run software written for much older versions of Windows. Microsoft essentially made it so that I can run my ancient copy of WordPerfect on Windows XP. That's backward compatibility and it's generally considered a Good Thing.

The problem with backward compatibility in Windows is simply a matter of degree. It has been 'on top' for so long now that there is a huge user-base that requires these old programs. When security issues are found in the code that supports these old programs, it is very tricky to fix without affecting the way the program runs. Software, including operating systems, that is too big and complicated to be easily fixed by the developers is considered 'crufty.'

That's basically how it is, anyway.

---

### Post by the_doc on 2008-06-12
> **Troll_the_Great said:**
> Thank you all for your answers, thou I didn't fully understand all of them. I don't know what is "backward compatibility" that windows has to maintain, and what "cruft" means.Can someone detail a little bit more this subject?


Backward compatibility means, for example, that Win XP has to run code that was written for Win98.  What this means is that newer versions of Windows can't totally remove legacy code from their code base otherwise older programs would fail.  This legacy code does/may contain vulnerabilities that virii may exploit.

Cruft is computer speak for code or software of poor quality.

---

### Post by Troll_the_Great on 2008-06-12
But this backward compatibility does not affect linux too?I mean, a new linux version can't run old programs?

---

### Post by the_doc on 2008-06-12
That's a good question, but I think it has to do with the attitude of the Linux user, namely that most users upgrade regularly to the latest version of whatever package.  The repos hold the latest versions of packages that are supported for a particular distro version, of course it is possible to stick with an older version but most users know that's a bad thing in terms of security.

Just my opinion!

---

### Post by Het Irv on 2008-06-12
> **Troll_the_Great said:**
> But this backward compatibility does not affect linux too?I mean, a new linux version can't run old programs?

I think part of the problem deals with Windows still doing things the same why the did them in the 90's.  They mad a few bad decisions then and now to ensure backwards compatibility, they have to stick to their guns.

---

### Post by aysiu on 2008-06-12
> **Troll_the_Great said:**
> But this backward compatibility does not affect linux too?I mean, a new linux version can't run old programs?
Not really, since the underlying structure is more or less the same as it was fifteen years ago in Linux.

Windows made a big shift when it moved to the NT kernel. Before that, there were no permissions and ownership - basically only one user who was the total administrator.

---

### Post by philinux on 2008-06-12
If you've not seen this before it explains a lot.

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

And there's some very good stuff on there.

---

### Post by bodhi.zazen on 2008-06-12
> **Troll_the_Great said:**
> But this backward compatibility does not affect linux too?I mean, a new linux version can't run old programs?

This is not as much an issue on linux.

Starting with Windows, why are people still using a program written for DOS or windows 95 on Vista ? Preference, choice, cost (windows apps have price tags).

On the Linux side "old versions" are updated. So it you have an application, say OpenOffice, the newest version is available.

Now, on Linux, you will (likely) run into backwards compatibility issues if you try to run OpenOffice version 1.0 on Ubuntu 8.04. Some applications merge or are no longer maintained, for example beryl (beryl split from and then re-merged with compiz).

In general people like to use the latest greatest, so most users will run the newest latest applications. If you do not want to run the latest greatest you can go for stability. Centos for example is still running firefox 1.5 as the default web browser (although not all packages on Centos are outdated that way). Most people who run Centos obviously are not looking for the latest greatest version of firefox.

Linux has many many more options ...

---

### Post by Troll_the_Great on 2008-06-12
I have seen it, but thx anyway.

---

### Post by decoherence on 2008-06-13
> But this backward compatibility does not affect linux too?I mean, a new linux version can't run old programs?

You got good answers to this, but I'd like to expand.

Because linux and most associated programs are open source, an ancient program can be compiled and packaged for a new version of Linux. This is actually complimentary to what bodhi.zazen said, rather than being contradictory. 

The OpenOffice 1.0 package you'd get from the repository likely won't run on Ubuntu 8.04, but I could certainly recompile it and repackage it and have it run just fine. 

The real question is why would I go to the effort of doing this when I can have the latest and greatest for free? There are reasons but they tend to be obscure, case specific things.

I hope that explains a little more of the 'recipe' as you so aptly put it :)

---

### Post by Troll_the_Great on 2008-06-13
Thx all for your answers.

---

