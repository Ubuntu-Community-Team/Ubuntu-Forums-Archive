---
title: "Why Is Ubuntu More Secure?"
date: 2008-07-09
forum: Recurring Discussions
---

### Post by Bosconian on 2008-07-09
I keep reading about how Linux is more secure than Windows. How in Windows you need to install a firewall and anti virus software and spyware protectors etc but in Linux you don't.

Could someone please explain why this is? Why can't viruses be written for Linux and therefore require you to need anti-virus software? Why does Linux not need a firewall? Why no spyware protection? What is stopping someone from writing spyware for Linux?

---

### Post by damis648 on 2008-07-09
Try Google. Google knows all. :popcorn: I will say that the user permissions base is MUCH stronger than Windows, thus a virus cannot do any *real* damage without a password.

---

### Post by Sef on 2008-07-09
Moved to recurring discussions.

---

### Post by lisati on 2008-07-09
Plus many pieces of malware are designed for Windows systems, and thus won't even get running in Linux without serious help.

---

### Post by Bosconian on 2008-07-09
> **damis648 said:**
> Try Google. Google knows all. :popcorn: I will say that the user permissions base is MUCH stronger than Windows, thus a virus cannot do any *real* damage without a password.


The thing is when I use Google, I bring up articles like this:

[http://www.linux.com/articles/34992](http://www.linux.com/articles/34992)

that completely contradict what people are saying. I am only trying to understand, I am not saying it isn't better.

---

### Post by Bosconian on 2008-07-09
Let me put it a different way. Should I be running anti-virus software, spyware software and a firewall on Ubuntu or not? Yes or no, why is that?

---

### Post by underthechair on 2008-07-09
I'm pretty sure that the article is being sarcastic. It says that "the use of certificates, stickers, and serial numbers" give the impression of security while praising it for "quickly and without complaint running any software offered it from any Web site or email attachment as requested" which actually is a security risk.

---

### Post by Bosconian on 2008-07-09
Well wikipedia suggests that Linux is not as secure as people try and make out:

> One of the vulnerabilities of Linux is that many users do not think it is vulnerable to viruses. Tom Ferris a researcher with Mission Viejo, California-based Security Protocols said in 2006, "**In people's minds, if it's non-Windows, it's secure, and that's not the case. They think nobody writes malware for Linux or [Mac] OS X. But that's not necessarily true....**"[3]

Shane Coursen a senior technical consultant with Kaspersky Lab noted, "The growth in Linux malware is simply due to its increasing popularity, particularly as a desktop operating system...The use of an operating system is directly correlated to the interest by the malware writers to develop malware for that OS."[3]

---

### Post by lisati on 2008-07-09
It's up to you. 

A firewall is a good idea: they help prevent people getting in without your permission.
Antivirus and antispyware: opinions vary here in the forums. Others can explain things more eloquently than I can; in essence it's finding a balance between not worrying too much (because of being unlikely to encounter a virus that will hurt your Linux machine), and not knowingly passing on something that could hurt Windows machines that you're likely to be in contact with.

---

### Post by barbedsaber on 2008-07-09
In windows, your account defaults to an admisitrator account, giving you total control over your computer. IN linux, it doesn't, so when you try to do something that you need admin rights for, it asks for your password. This means, that if a program (virus) decides to wipe the usr (unix system resources) directory, it doesn't have the permissions to do so, and it cant do it. Its not a very good explanation, but I hope it helps.

---

### Post by Thanoulis on 2008-07-09
In Windows, an attacker could exploit and benefit from a security hole...the same applies to GNU/Linux...the huge difference is that the programs GNU/Linux uses, are open source, so they are constantly evolving...
It should be more easy for an attacker to exploit an open source program, but in reality, open source programs are more secure, due to a different style of programming, and the community support...

---

### Post by smartboyathome on 2008-07-09
> **Thanoulis said:**
> In Windows, an attacker could exploit and benefit from a security hole...the same applies to GNU/Linux...the huge difference is that the programs GNU/Linux uses, are open source, so they are constantly evolving...
It should be more easy for an attacker to exploit an open source program, but in reality, open source programs are more secure, due to a different style of programming, and the community support...

That basically brings up the statement:
The more eyes that are looking at the code, the more secure it will be.
Since all the programs on Ubuntu by default are open source, they have more people who look at them, and thus more security holes are found and patched up. Contrast this with Vista, and you see that open source is actually better.

Also, another reason why Ubuntu is more secure: permissions don't allow a script to even run unless it is made executable. The only other way around this is to package it in a tarball, but it can't unpackage itself from within the tarball.

Ubuntu can be infected using Flash (one person at a computer cracking competition said their flash exploit for OS X, I think it was, could be ported to Linux), so that is why there is increasing importance of an open source flash.

---

### Post by aysiu on 2008-07-09
Read [this](http://ubuntucat.wordpress.com/2008/07/03/does-ubuntu-need-antivirus/).

---

### Post by Bosconian on 2008-07-10
It is interesting that people say Ubuntu is more secure yet I read a thread on here about the First 10 applications that people install after first installing Ubuntu. The number who included Firestarter and Clam(whatever) anti virus was surprising.

So surpising that I decided I might as well stick with XP.

Thanks for all the explanations though.

---

### Post by aysiu on 2008-07-10
> **Bosconian said:**
> It is interesting that people say Ubuntu is more secure yet I read a thread on here about the First 10 applications that people install after first installing Ubuntu. The number who included Firestarter and Clam(whatever) anti virus was surprising.

So surpising that I decided I might as well stick with XP.

Thanks for all the explanations though.
Well, most Ubuntu users are ex-Windows users like yourself, and they're used to installing a lot of security programs.

Take a look at any thread (like this one, for example) that asks what programs people need to secure Ubuntu. When we tell new users they don't need to install antivirus, etc., they don't believe us and like to install such things "just to be safe," even though antivirus doesn't give you extra protection against non-existent Linux viruses, and Firestarter is just a GUI frontend for configuring the already-existing firewall in Ubuntu (iptables).

In most cases, those programs are installed from fear and not reason.

But if you do actually run listening services (which Ubuntu does not by default), then it makes sense to install Firestarter if you require a GUI frontend for configuring the firewall.

And if you're running Ubuntu as a mail server or file server for Windows computers, it does make sense to install antivirus to scan for Windows viruses.

---

### Post by Bosconian on 2008-07-10
> **aysiu said:**
> Well, most Ubuntu users are ex-Windows users like yourself, and they're used to installing a lot of security programs.

Take a look at any thread (like this one, for example) that asks what programs people need to secure Ubuntu. When we tell new users they don't need to install antivirus, etc., they don't believe us and like to install such things "just to be safe," even though antivirus doesn't give you extra protection against non-existent Linux viruses, and Firestarter is just a GUI frontend for configuring the already-existing firewall in Ubuntu (iptables).


But viruses do exist for Linux. I've been reading about them. I just confused thats all. Why does there EVEN exist an anti virus application for Linux if no Linux viruses exist? Seems a bit of a waste of development time doesn't it?

Don't get me wrong, I am not having a dig at Ubuntu or Linux. I am no Windows fanboy. I just need to understand because writing an anti virus application for an OS which has no viruses seems a little silly.

---

### Post by Barrucadu on 2008-07-10
I shall put it as simply as I can: You *can* install an antivirus if you want, but it won't do anything to keep *Linux* more secure. That is because Linux antiviruses only scan for Windows viruses, which cannot run on Linux. Thus, installing an antivirus on Linux is completely pointless unless you're going to be sharing files with multiple Windows computers and want to make sure you don't pass on an infected file.

---

### Post by MaxIBoy on 2008-07-10
It is easily possible to write viruses for Linux. A little harder than it is to write 'em for Windows, but it's by no means impossible.

However, there aren't many Linux computers out there. Therefore, only 40 or so Linux viruses have been written.


Come to think of it, there are a lot of Linux *servers.* Maybe it's time to get worried.

---

### Post by aysiu on 2008-07-10
> **Bosconian said:**
> But viruses do exist for Linux. I've been reading about them. I just confused thats all. It's a rather lengthy explanation, but since it sounds as if that's what you want, read [Does Ubuntu need antivirus?](http://ubuntucat.wordpress.com/2008/07/03/does-ubuntu-need-antivirus/)> Why does there EVEN exist an anti virus application for Linux if no Linux viruses exist? Seems a bit of a waste of development time doesn't it? This is a shorter answer. Linux isn't big on the desktop/laptop, but it is huge on the server, and many servers serve email to Windows computers or are file servers for Windows computers. Most antivirus programs designed for Linux are actually designed to scan for Windows viruses.

---

### Post by oldsoundguy on 2008-07-10
A firewall, yes.  Keeps people from the outside from utilizing your computer as a forwarder to mask their nefarious activities. (they can't actually get IN and get info from a Linux box without permissions.)
Same thing as protecting your wireless network by a password or specified computers only.  Keeps the war drivers from using your bandwidth (and IP addy) for downloading illegal porn and thus flagging you as a bad guy with the monitoring LEA!

Virus install ... not without YOUR permission
Ad-Bots/Ad-Ware/Malware of any kind ... not without YOUR permission.

The virus files written for Linux have, thus far, been aimed at Linux servers .. or office head end machines that also have WINDOWS boxes on the network.  Those virus files attack the Windows machines when they log on simply because of the stupidity of being able to SINGLE CLICK on something to install in into Windows. 

You really need to read up on what various malware files are.
Google again, is your friend.  Going off half cocked about something that really does not fit the description .. such as calling ad ware "virus" programs .. 
Here is just ONE source of information:
[http://en.wikipedia.org/wiki/Malware](http://en.wikipedia.org/wiki/Malware)

As to an anti-virus program to protect your Linux server:
Google F-Prot for Linux.  It is for work stations and servers and .......
IT IS FREE.

(I use their Windows version and have been using it for 6 years with NEVER a virus installed!!!!)

---

### Post by sp0nge on 2008-07-10
The beauty of Linux is the security by user permissions. 

A firewall is good just because the greatest threat isn't the bug you catch, but the individual on the other end. 

As for the AV and other security software, this is a great debate in the security world. While it is completely false to say there are *no* virii for Linux, the reality is they are no where near as harmful as what you'll see on a windows box. 

The article [The short life and hard times of a Linux virus]("http://librenix.com/?inode=21") will give some good insight on why it is so difficult for a Linux virus to do major damage. 

Nothing is impossible, but Linux makes it as hard as possible.

---

### Post by BUSHYBOB on 2008-07-10
> **Bosconian said:**
> The thing is when I use Google, I bring up articles like this:

[http://www.linux.com/articles/34992](http://www.linux.com/articles/34992)

that completely contradict what people are saying. I am only trying to understand, I am not saying it isn't better.

It was an attempt at humour, hence the "Feature:Humor" at the top of the page,

---

### Post by Bosconian on 2008-07-10
I am getting a better idea of this know and an understanding of why Linux is more secure.

This is very tempting. In fact if I can overcome my other obstacles to Ubuntu, then I would be very tempted to convert. However, I've been trying Ubuntu and finding a lot of issues. It's 6 of one and half a dozen of the other at the moment.

---

