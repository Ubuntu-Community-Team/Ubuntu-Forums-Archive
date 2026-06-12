---
title: "virus"
date: 2011-08-27
forum: Recurring Discussions
---

### Post by mail2ramesh on 2011-08-27
will  Ubuntu get effected with virus

---

### Post by Chronon on 2011-08-27
Try this page
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by lisati on 2011-08-27
*Thread moved to **Security Discussions**.*

[S]The[/S] A short answer: Although not completely impossible, it's not very likely.

Edit: A shorter answer: no.

---

### Post by kmsalex on 2011-08-27
though if your supper paranoyed there are options, all be them not very good once, they don't realy have to be ;)

[http://www.clamav.net/lang/en/](http://www.clamav.net/lang/en/)

---

### Post by haqking on 2011-08-27
Linux does not suffer from Viruses Like other OS, there are no known viruses in the wild, the main reason using AV on linux is to scan incase you share files with windows users.

It can still suffer from trojans, rootkits etc, but that comes down to vigilence and making sure you stick to the security model and not disabling passwords etc.

Common sense, dont tell your system you want it to do something unless you are sure etc.

In browsers you can still suffer from XSS or CSFR, other script related issues so use things like NoScript plugin for firefox etc.

Also look at apparmor for profiling your applications and there privelege

See below staring with Bodhi.Zazen overvie3w of Linux Security

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

then here for AV information:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by Firezap on 2011-08-27
If it helps make you feel any better I have personally used Ubuntu for at least 4 to 5 years and never had a problem with viruses and stuff lol.

---

### Post by scorp123 on 2011-08-27
What's a virus????

(Yes, I use Linux since 1996. How did you know? ...)
:lolflag:

---

### Post by Thewhistlingwind on 2011-08-27
I will go ahead and say:

Most programs are written and compiled to take advantage of windows exploits. This is because the program relies on vulnerabilities that are ONLY present in windows.

One type of attack that could effect Ubuntu is virus/malwaredesigned to exploit a browser. eg. Firefox Because firefox is cross-platform, if the payload effects the browser and not the host OS, you could be infected. 

OR

As cross-platform languages like python and html5/javascript become more and more popular for writing malware, you'll see a renaissance of powerful malware that Linux use very well may not protect you from.

At this current time though, theres no Linux malware in the wild.

Of course, thats no excuse to slack on security.

Things like firewalls, MAC (Mandatory Access Control), and other tools, are invaluable in protecting yourself from attackers.

tl;dr probably not right now, maybe in the future, go secure yourself anyway.

Oh, and don't run untrusted code without proper protection.

---

### Post by cariboo on 2011-08-28
Moved to Recurring, as this topic has been covered so many times, I've lost count.

---

### Post by BlacqWolf on 2011-08-29
Well, Ubuntu, or Linux in general, tends to have fewer exploits, and Linux and software available for it tends to have a more rapid update rate that security bugs are fixed more quickly.

While it certainly is very, very unlikely to get any, malware in Ubuntu is possible. Not as much as in Windows, but there is a small bit floating around. But as long as you take basic and simple precautions while running Ubuntu, you should be alright.

1: before looking up something, such as an app, use a package manager like Ubuntu Software Center or Synaptic, where you can download packages from the repository (if you don't know what that is, it's like Linux's version of the Apple App Store or Android Market) where apps are distributed directly, and where you're likely not going to get malware from. Do this instead of downloading and installing items from random websites, this way you will not have to worry about malware, and try to only download items from a website if it is not available from the Ubuntu repositories.

2: update software frequently. This way, you can receive updated  software which may patch security exploits found in previous versions

3: don't add untrustworthy repositories to your software sources, don't blindly install packages (like .deb, .rpm).


Also, if you're still concerned about malware on Ubuntu, or Linux in general, there are a few antivirus clients available for Linux, such as ClamAV or Avast. But until Linux becomes a big guy in the OS market, there isn't anything to worry about, as currently there isn't much malware, and Linux software, when kept up to date, is very secure. 

Also, because of the way Linux does permissions and how administrative tasks require confirmation, if you do get malware, it will not take down your system unless it tries to do so and you allow it by providing permission with the confirmation window. So, if something seems suspicious, please be sure to trace what may be asking to do the administrative event before confirming. If you don't know why it's asking for permission, don't allow it.

I've run Ubuntu for nearly two years and a half and I haven't gotten one piece of Linux-based malware, but one piece made for Windows. Those are quite common, but will NOT affect a Linux system. 

Also, as you are new to the forums, welcome. And, if you have questions, please don't hesitate to ask!

---

