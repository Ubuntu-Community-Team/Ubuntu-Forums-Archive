---
title: "Why Kernal Updates?"
date: 2013-03-27
forum: New to Ubuntu
---

### Post by kernalkorn on 2013-03-27
v12.10 on GbyteFM1 AMD A4 APU  My updater is showing multiple kernal images and generic kernal headers as security updates.  Is this risky?  Shouldn't there be just one of each?  Better still shouldn't this be reserved for major version releases?  Is my system going to "choose one" based on the chip set?     Where should I post notices for bug fixes?

---

### Post by ibjsb4 on 2013-03-27
Are you getting something like this?  If so, thats normal.

[ATTACH=CONFIG]240604[/ATTACH]

---

### Post by grahammechanical on 2013-03-27
What would you think of the developers if they knew about a security flaw and did not fix it but left you with an operating system that was vulnerable? Or, if they could fix a bug that relating to certain hardware such as wireless adapters but did not fix it and so left you with a partially broken OS? Perhaps you prefer to wait several months, even years, for Service Pack 1 and then Service Pack 2. By which time you are looking forward to OS 9. Or will it be better to wait for OS 10?

There are various parts to the "kernel." The Ubuntu developers pass on to us updates to the kernel as the kernel developers release them. In this way Linux/Ubuntu is kept up to date.

> [COLOR=#000000][FONT=sans-serif]In May 2012, a difference between the implementations of the SYSRET instruction in AMD and Intel processors was found to cause vulnerabilities in major systems such as Windows, FreeBSD, XenServer, and Solaris. The issue had been fixed in the Linux kernel since 2006.[/FONT][/COLOR]

[http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)

A kernel update would have brought in that fix.

Regards.

---

### Post by kernalkorn on 2013-03-27
I'm all for security patches.  come to think of it, my monthly patch tues updates from WinXP often have kernal vulnerabilities.  One of the reasons XP has had so many malware attacks are the sloppy way in which graphics and other IO functions were codedat kernal level.  How is the Java debacle afecting Ubuntu?  Does FF for Ubuntu have Java capabilities by default? Is Ubuntu safe from Java exploits, assuming a Java plug-in is not on the browser? Or are all Jave exploits aimed at winders?  What about apache servers etc?

---

### Post by DuckHook on 2013-03-28
> **kernalkorn said:**
> I'm all for security patches.

In Linux, it isn't just for security, although this is an excellent reason in and of itself. Unlike the case with lock-in OSes, in Linux, most mainstream drivers are also included in the kernel. Therefore, continuing patches are needed both to add new driver support and to prune obsolete drivers.

> One of the reasons XP has had so many malware attacks are the sloppy way in which graphics and other IO functions were coded at kernal level.

If only it were that simple. The main problem with XP (and Windows in general) is that the whole OS is designed with security only as a distasteful afterthought. Examples: NTFS still has no file permissions, the whole OS is practically based on absurd remote procedure calls, it is still necessary to run far too many services for the OS to even function, etc. The list is endless. For Windows to become as natively secure as Linux, it would have to be totally redesigned from the ground up under a culture that is the opposite of the one it has cultivated so far. Pigs will fly first.

> Does FF for Ubuntu have Java capabilities by default?

Only if you install restricted extras, but almost everyone does, so the practical answer is Java is present of (I'm guessing) 95% of Ubuntu installations.

> Is Ubuntu safe from Java exploits, assuming a Java plug-in is not on the browser?

Good question, which is more in the line of the security gurus over on the security forum. My very uneducated guess would be that Ubuntu is more resistant to Java exploits for the same reason that it is resistant to non-Java exploits--it's strict default insistence on passwords and similar default to restricted privileges for user accounts. But I am flying blind on this one. I don't have Java installed. Don't use it, so don't really know.

> ...are all Jave exploits aimed at winders?

Bad guys will go after anyone they can, and are quite agnostic about the OSes that their victims run. That said, there is (in my opinion) no worse browser than Internet Explorer, and its native insecurity is multiplied many times over by MS's decision to make it an inseparable part of their OSes. This migrates any browser flaw into the OS itself, and is simply a loopy dufus design driven by considerations of fending off competitors more than any considerations of security.

> What about apache servers etc?

Apache servers are likely a more prized target than any other target to the bad guys of the world. It's a testament to Linux that the vast majority of compromised web servers out there are Windows and not Apache.

I am very worried about leaving the impression that security in Linux is just hunky-dory. It isn't. It requires the right kind of knowledge and ongoing good practices. The vast majority of new users migrating from Windows brings with them the atrocious security practices that Windows has trained them to follow. And it should surprise no one that if you treat Linux like Windows, then it will end up with just as many security holes as Windows. Linux isn't a magic wand. If you have further curiosity about Linux security, then I recommend the following links:

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[https://sites.google.com/site/easylinuxtipsproject/security](https://sites.google.com/site/easylinuxtipsproject/security)

---

