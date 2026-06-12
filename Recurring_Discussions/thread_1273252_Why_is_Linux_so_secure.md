---
title: "Why is Linux so secure"
date: 2009-09-23
forum: Recurring Discussions
---

### Post by vipulkelkar on 2009-09-23
Hi guys
I am new to linux.I would like to know why is linux said to be so secure than  windows w.r.t cracking the systems security and also the virus infections.
What makes it more powerful than the windows
To the linux experts out there

---

### Post by I WILL DO IT on 2009-09-23
b/c its a sexyer than mac and windows :lolflag:

---

### Post by overdrank on 2009-09-23
[Security]("http://ubuntuforums.org/showthread.php?t=510812") 
Moved to Recurring Discussions

---

### Post by jacksaff on 2009-09-23
This is very simplistic but should give you an idea...

Unix, the system on which linux is based, was designed for mainframe type computers which would have many people logged in at once and their programs going at the same time. It was thus made to ensure that each user's programs and data were kept separate and secret from the other users. ie. security is and always was built into the heart of the system.

Windows on the other hand was originally built for home machines on which only one user would be logged in at a time. Security was less important than performance on early home pcs.

As machines have become much more powerful and run many more programs at once than they used to it has become much more important to keep everything separate and secure. Windows changed it's core after win98 to a more 'industrial strength' design, but many of the flaws, user habits and program behaviors remained. Microsoft could not afford to lose compatibility with the programs it's users already had. Many security features were thus 'bolted on the top', as it were, with the problem that they can often be by-passed or just don't work as well as they might.

No operating system is perfectly secure and you can get reasonable levels of security with more recent windows systems if you are prepared to avoid certain practices such as logging in as administrator. Linux however has a much better security model by default.

---

### Post by 3rdalbum on 2009-09-23
The main thing is that Unix and Linux were always built to be multi-user operating systems, connected on networks and the Internet. DOS and Windows were built to be single-user operating systems to be run on a single isolated computer. The original Unix guys made sure that their systems couldn't be ruined by individual users or by people on other computers on the network. The Windows developers, up until 1997, never imagined that Windows computers would be running on networks or that there might be more than one user on a computer.

There is a "culture of security" around Unix and Linux, where developers on the platform think about how to write their software to minimise the possibility of being exploited. They also respect the security system and write their software so it can be run by regular users (rather than by root). Developers on Windows think about how to implement their software, and then if there's time left over until the deadline, they think about bolting on some security features. Until very recently, most Windows programs assumed they would be run by an administrator or with unlimited permissions.

Interestingly, Mac OS X's developers don't respect the security system either. I imagine this is because the classic Mac OS had very limited multi-user capabilities and very few people interested in cracking it, so the developers for Mac OS X also inherited the attitude of "If it runs, it's finished".

If you want a point-by-point dissection of Linux's specific security features and how they protect the system, then Google would be a better place to ask. But now you know why there is a big difference between Windows and Linux in terms of security, and you also know why many of us are horrified when people ask "How do I turn off the password prompts".

EDIT: Jacksaff also explained it the same way as me :-)

---

