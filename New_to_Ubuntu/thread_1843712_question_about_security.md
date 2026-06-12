---
title: "question about security"
date: 2011-09-13
forum: New to Ubuntu
---

### Post by VtecHonda on 2011-09-13
i have read the security sticky... and now i have a little bit of a better idea about Ubuntu and Linux security...

But i still have one question for all those experienced users of linux:

how secure will my machine be if i do the following:
1-enable the built-in Ubuntu firewall
2-install ClamAV
3-use safe browsing habits (and common sense, of course). 

Or if there are any other steps i can take to be even more secure...they are more than welcome. 

(i am new to ubuntu...and being a technician with a primarily Windows background, i want to make the swithch to Linux, since i hear nothing but good things about it). 

thanks so much. i appreciate any helpful feedback.

---

### Post by LowSky on 2011-09-13
1. Its already enabled by default
2. ClamAV should be in the software center, but you don't need it.
3. Go to the worst dark spot the internet has to offer. You will come away unscathed.

Ubuntu and Linux in general doesn't get sick like Windows can, so don't worry about those pesky bugs that look like virus detectors, or free iPads.

I'm not saying Linux is impervious, I'm just saying that Linux's use of administrative access makes getting a program to install malicious content only possible with your consent.

I have use Linux since 2006 not one piece of malware EVER!

Ubuntu will be as fast as the day you installed it, and 365 days from now.

---

### Post by VtecHonda on 2011-09-13
Thanks LowSky..appreciate it

so if i understood correctly... as long as i use common sense and safe computing ( which i have been doing for years in windows) my ubuntu machine should be safe and secure?

---

### Post by snip3r8 on 2011-09-13
> **VtecHonda said:**
> i have read the security sticky... and now i have a little bit of a better idea about Ubuntu and Linux security...

But i still have one question for all those experienced users of linux:

how secure will my machine be if i do the following:
1-enable the built-in Ubuntu firewall
2-install ClamAV
3-use safe browsing habits (and common sense, of course). 

Or if there are any other steps i can take to be even more secure...they are more than welcome. 

(i am new to ubuntu...and being a technician with a primarily Windows background, i want to make the swithch to Linux, since i hear nothing but good things about it). 

thanks so much. i appreciate any helpful feedback.
If you took any more steps to secure it ,either you are paranoid or a web server

---

### Post by bodhi.zazen on 2011-09-13
> **LowSky said:**
> 1. Its already enabled by default

iptables may be "enabled", but by default it allows all traffic.

This is usually not a problem as by default there are no listening servers of any significance.

However, if it makes you feel better:

```
sudo ufw enable
``` is all 99.99 % of all desktop users will need.

> 2. ClamAV should be in the software center, but you don't need it.

+1. There are no know active viruses for linux.
> 3. Go to the worst dark spot the internet has to offer. You will come away unscathed.

That is not true. It is not uncommon for malicious java script or flash to affect Linux users. It only has access to files in HOME.

Before you go to the deepest , darkest pit of the internet, secure your browser (disable cookies and noscript at a minimum) and enable apparmor with a profile that locks down $HOME as much as possible.

firefox has exploits discovered daily it seems:

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

I would highly suggest Apparmor =)

---

### Post by kaldor on 2011-09-13
> **VtecHonda said:**
> i have read the security sticky... and now i have a little bit of a better idea about Ubuntu and Linux security...

But i still have one question for all those experienced users of linux:

how secure will my machine be if i do the following:
1-enable the built-in Ubuntu firewall
2-install ClamAV
3-use safe browsing habits (and common sense, of course). 

Or if there are any other steps i can take to be even more secure...they are more than welcome. 

(i am new to ubuntu...and being a technician with a primarily Windows background, i want to make the swithch to Linux, since i hear nothing but good things about it). 

thanks so much. i appreciate any helpful feedback.

1- Same as any other Firewall; I recommend it.

2- You don't need any anti-virus application. You really don't. Trojans on Linux are easily possible, but are often in the form of scripts; your AV program won't likely find it. It'll be useless unless you want to scan for Windows viruses in a work environment or something.

3- Safe browsing habits should *always* be used no matter what you do.

All in all, if you install all of your software from trustworthy sources, then you'll most likely never have any encounter with malware of any sort. Use common sense. If you're required to run prettyscreensaver.deb, question it.

Also, if you have a technical background, I'd recommend you check out Scientific Linux also; it's a free clone of Red Hat Enterprise Linux ;)

---

### Post by Sef on 2011-09-14
> You don't need any anti-virus application. You really don't. Trojans on  Linux are easily possible, but are often in the form of scripts; your AV  program won't likely find it. It'll be useless unless you want to scan  for Windows viruses in a work environment or something.

If you had an email server that you would use to send messages out to others, then you would want a virus scanner as viruses could ride on top of Linux and be sent out with your email.

---

### Post by dfarrell07 on 2011-09-14
Now that you are booting Ubuntu, the main thing to avoid is making security mistakes that are unrelated to your OS. For example: 
- Use a WPA, not WEP or open wireless router.
- Try to browse with https as often as possible. The EFF makes a great extension to Firefox called HTTPS Everywhere. Check it out here: [https://www.eff.org/https-everywhere](https://www.eff.org/https-everywhere)
- Update regularly, mainly in reference to your browser. For example, if some Ubuntu user has not updated in the last few weeks and lives in some very narrow geographic regions, they might still be vulnerable to the fake DNS certificates generated by the DigiNotar CA hack. That is because Firefox or Chrome or whatever would still be accepting certificates signed by DigiNotar, which have not been shown to be safe post-hack.
- Maintain good password policies. Don't use the same password for many services. Use passwords of > 8 chars, including symbols, numbers and uppercase letters. Don't only replace letters with l33t, and don't only include numbers/symbols at the beginning and end of passwords. Don't use passwords that are related to you, like your phone number. Use as a diverse and strange of a character set as possible (bad: @$!&_ good: ~.|^<>). The password cracking method most often used, rainbow tables, will do much, much worse if you use strange characters.

In general, follow basic security protocols, and keep booting Linux. You will be very, very safe.

---

### Post by kaldor on 2011-09-14
> **Sef said:**
> If you had an email server that you would use to send messages out to others, then you would want a virus scanner as viruses could ride on top of Linux and be sent out with your email.

Hence the last bit of what I wrote on it :)

---

### Post by sweBers on 2011-09-14
I know that it seems counter-intuitive, but Linux security is very different than Windows security.  

1. By default, a Linux machine does not open a bunch of ports when it is first installed.  If you install a bunch of services, and run them, then you would want to install a firewall to enforce rules on the services.

2. Antivirus is a great option if you have a windows network or if you will be serving files of any kind.  If this will be a standalone machine, it's not really something you have to worry about.

3. Save browsing is always advised.  Although your computer could be impervious to all software attacks, there's no telling who's watching.

With any system, it's always necessary to manage risk.  If you don't have anything to protect, and you make regular backups, you don't really have to worry about a whole lot.

---

### Post by jtarin on 2011-09-14
The number one security problem in Linux is the "user".:P

---

### Post by 3rdalbum on 2011-09-14
Just to echo what others beat me to: Don't bother with the Ubuntu firewall. Ubuntu doesn't listen to any incoming ports by default anyway, which means that a firewall is completely redundant.

Besides, you're probably already behind a firewall in your modem or router.

Also, there's really no need for anti-virus. There's no Linux viruses. There haven't been any since I started using Linux, over five years ago. If you use common-sense when using the internet, you'll be absolutely fine.

Good luck! I'm glad you're taking security seriously enough to ask for advice. Sounds like you'll fit in here :-)

---

