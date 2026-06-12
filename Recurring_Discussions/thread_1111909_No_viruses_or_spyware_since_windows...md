---
title: "No viruses or spyware since windows.."
date: 2009-03-31
forum: Recurring Discussions
---

### Post by ginjninj on 2009-03-31
Just interested really I was always plagued with viruses/spyware/malware all that rubbish choking ms windows, how come linux/ubuntu etc doesn't seem to get effected like that? Is windows being so mainstream too easy a target?

Happily linuxing now..

---

### Post by SunnyRabbiera on 2009-03-31
Partly, but also how Linux manages itself.
Ubuntu in particular is a big help because of sudo, Ubuntu disables the root account by default and instead uses sudo.
Most other linux systems use root, but on them the root account is separated.
On windows if you are the default user you are root, rather if you like it or not.
By enabling total system access to make the system "easy", they sacrificed security for ease of use.

---

### Post by 3rdalbum on 2009-03-31
Microsoft takes the approach of "We'll write the software and then secure it later".

Linux-based developers take the approach of "We'll write secure software".

Security is something you have to be thinking about as you're writing the software; you have to think "Can an attacker take advantage of any features of this software? How can I design this software to minimise the chance of harm?". Microsoft is slowly starting to learn this, but their users are still in the old mindset and don't understand the need to add security features that require changes to the user interface.

Apple is yet to learn.

Most people will tell you "It's because Linux users don't run as root" or "It's because anyone can find security problems in the open-source code and fix them", and they're right, but there is a whole culture of secure design in Linux and Unix that originated with AT&T Unix in the 1960s.

The computers in the 1960s were not used exclusively by any one person or group; their computing time was hired out to anybody who needed to use them, and the need arose for an operating system that could be used by more than one person at a time, and keep the users from interfering with eachother as well as keep them from damaging the computer's configuration.

Multics, and then Unix, fulfilled those needs, and even today there are Unix systems that have computing time for-hire on a timeshare basis and need to keep multiple users' programs from interfering, whether by accident or by malicious intent. And, of course, Unix and Linux systems pretty much run the internet and must be designed securely to deal with remote threats. It also just so happens that the multiple-user concept works really well for keeping a desktop computer safe from viruses. In a manner of speaking.

Windows, on the other hand, started life as a single-user CLI system (MS-DOS) and then a single-user GUI system (Windows 95) before finally becoming mostly multiple-user (Windows 2000/XP). The problem is that Windows-based developers don't think about security and until recently had always assumed that every user of their software would be using it under an Administrator account on Windows XP! Software development companies take the attitude of "We'll write and release the software, and then if there is bad publicity from security problems we'll try and fix each problem as it arises". Not a good attitude.

A lot of non-Linux people say "The only reason Linux doesn't get viruses is because it's a smaller target; if as many people used Linux as used Windows, there would be just as many Linux viruses as Windows viruses". This makes absolutely no sense as the main reason these days for writing viruses is not to cause havoc, it's to steal personal information or use your computer to conduct illegal activities. Basically, viruses are used to turn a profit.

Linux and Unix servers hold the world's credit card numbers, the corporate world's industrial secrets, and every government's State secrets too; a virus that could infect those Linux and Unix servers and steal all this information would make the virus writer an instant billionaire. So there is much more financial incentive to write Linux viruses than there is even to write Conficker or Storm.

---

### Post by timcredible on 2009-03-31
what the previous poster said.  also, you have to look at the history - windows was made for a non-networked single-user computer, linux is based off unix that was made to be connected to a network and made for multiple users on the same machine.  that original design choice still haunts windows.  and it may be an interesting day tomorrow when the "conficker c" virus activates.

---

### Post by ginjninj on 2009-03-31
Thanks for that fullas, that was good reading. I should look at a bit a history on unix etc, see how it all started.

---

### Post by gkinney3203 on 2009-04-01
I too enjoyed the history lesson. Growing up in the Windows world,  I was always irritated with the endless service packs to protect against one virus after another... until now! Good luck to those Windows users tomorrow.

---

### Post by ranch hand on 2009-04-01
One thing that was not mentioned on TV or most articles I have read is thaat this I exploiting a security hole in MS SERVERS.  Networked computers are in the most danger.

Conficker also will self install on thumb drives and then can infect non MS server connected computers.

---

