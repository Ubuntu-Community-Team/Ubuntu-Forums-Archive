---
title: "Best OS for servers"
date: 2008-07-18
forum: Other OS Talk
---

### Post by ryaxnb on 2008-07-18
What's your personal opinion on the best Linux distro for servers? BSDs are welcome too! Here's the sample server:
File/Web/Printer server
Small-medium business
Reasonably modern
Medium-range
x86 architecture

One rule is it has to be free, no paid server subscriptions or anything like that.

I've always thought in that market these would be best:
Debian stable
Slackware
CentOS

---

### Post by adam_kimber on 2008-07-18
Ubuntu server is supposed to be pretty good these days. I would recommend Debian or Ubuntu TBH. Debian stable is like a rock so if you are after long term uptime then that would be good. Debain unstable that has fancy features that you are not going to get in stable for ages might sway you in that direction.

---

### Post by zmjjmz on 2008-07-18
CentOS is good too.

---

### Post by mips on 2008-07-18
I would have to say FreeBSD!

---

### Post by Bachstelze on 2008-07-18
> **mips said:**
> I would have to say FreeBSD!

Agreed.

---

### Post by SunnyRabbiera on 2008-07-18
A BSD will blow linux out of the water for servers, its far more secure and stable in that respect.
But if you need working hardware, ubuntu server or debian might be better options.

---

### Post by kk0sse54 on 2008-07-18
FreeBSD definitely

---

### Post by LaRoza on 2008-07-18
> **ryaxnb said:**
> What's your personal opinion on the best Linux distro for servers? BSDs are welcome too! Here's the sample server:
File/Web/Printer server
Small-medium business
Reasonably modern
Medium-range
x86 architecture


Those requirements don't really demand a lot. For this, I would recommend a distro that you know well enough to use without much trouble.

---

### Post by myusername on 2008-07-18
debian stable ftw

---

### Post by Sporkman on 2008-07-18
Ubuntu Server. I run my website on it (see sig) & it's rock solid.

---

### Post by david_lynch on 2008-07-18
I vote for ubuntu - 

I ran redhat servers for years, then moved up to suse, but lately I've been quite impressed with ubuntu. I've run freebsd and netbsd too, and they are nice, but I find really no compelling reason to use a bsd instead of linux.

:KS

---

### Post by MisfitI38 on 2008-07-18
OpenBSD is far and away the most stable and secure server OS. [Nothing can touch it]("http://www.ibm.com/developerworks/aix/library/au-openbsd.html").



Anything else worth mentioning must take a distant second place. ;)

---

### Post by Twitch6000 on 2008-07-18
> **myusername said:**
> debian stable ftw

+1 to this.

---

### Post by Bachstelze on 2008-07-18
> **Twitch6000 said:**
> +1 to this.

Aye. Gotta love their PRNG ;)

Seriously, over the last six months, Linux in general and Debian-based distros in particular totally lost my confidence (who wasn't very high to begin with) as server OSes.

---

### Post by kaldor on 2008-07-19
I hear Gentoo works really well on servers.

---

### Post by Bachstelze on 2008-07-19
> **kaldor said:**
> I hear Gentoo works really well on servers.

Well, yes and no. Sure, if you can afford the compiling, it will work as well as any other Linux, but if your server is constantly under heavy load (like the one this forum runs on for example) and you need to compile somthing big, it can be troublesome.

---

### Post by MisfitI38 on 2008-07-19
> **kaldor said:**
> ..Gentoo works really well on servers.

Only a Gentoo fan would say this. ;)
OpenBSD ftw.

---

### Post by Svenstaro on 2008-07-20
Debian all the way!
Using it for two servers here and well, apart from the SSH incident (you know what I mean) there hasn't been any major security problem.

At home I use two Ubuntu servers abused to have a GUI :S.

---

### Post by ibutho on 2008-07-20
If I were setting up a server, I would use CentOS, Debian or FreeBSD.

---

### Post by regomodo on 2008-07-20
Debian Etch or a well configured Gentoo box

---

### Post by zipperback on 2008-07-20
Operating system: **Linux** 
Any current version of Linux using the current kernel.
Fully updated with all current security patches.
Command line only, do not install a gui interface for it.

Ubuntu Server and Debian are excellent choices.

Apache for Web services.

I prefer Proftpd for the ftp server.

If you don't mind running a BSD based operating system instead of Linux for your server, then I would go with **OpenBSD**.

Whatever you are going to run however, just make sure that all of your hardware meets the compatibility requirements of the operating system you are going to install on it.

And the most important factor to consider is the skill level of the administrator who is in charge of the system.

- zipperback
:popcorn:

---

### Post by Sorivenul on 2008-07-20
+1 to FreeBSD

---

### Post by mips on 2008-07-21
> **MisfitI38 said:**
> OpenBSD is far and away the most stable and secure server OS.

I really like OBSD. Depending on your needs however it might not suite your performance requirements as it lags between FBSD in this department.

For not to hectic requirements or persaonal use I would use OBSD over FBSD any day.

---

### Post by dca on 2008-07-21
BSD is a rock solid foundation for a web server.  However, you may run into issues during installation if you're using a hybrid PC as a server.  Could run into driver issues either with graphics or RAID controller.
 
I like the 'use what your comfortable with' ideology.  However, if that's non-existent you may want to choose something that has the most 'how-to(s)' avail for it, a'la: Ubuntu Server or CentOS or those that have a good forum community support:  Ubuntu, Fedora, openSUSE...

---

