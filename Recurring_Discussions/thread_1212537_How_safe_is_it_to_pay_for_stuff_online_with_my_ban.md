---
title: "How safe is it to pay for stuff online with my bank?"
date: 2009-07-13
forum: Recurring Discussions
---

### Post by Mashuteichou on 2009-07-13
In Windows, I had it pretty much impossible for someone to get my information.  I was invisible to everyone, except where I was going, and all my information was encrypted and hidden.  It was also saved in a program that had a password on it so no one could really get into it.  

Linux, I have Firefox.  I keep getting mixed answers on firewall and antivirus stuff.  I have Firestarter loaded, Avast, and soon AVG, but some say its useless.  I am very paranoid with banking online, (My uncle lost $15,000 recently because he was hacked from someone in Australia) Granted he was on Windows, but it doesn't make it any better.  (Still a recovering Windows user)

Is Linux less, same, or more secure then a Window's XP with 10 programs on max?

---

### Post by Vunutus on 2009-07-13
Out of the box, Linux is hands down much more secure than Windows, but don't let that lull you into a false sense of security. Security ultimately comes down to the end user. The biggest thing you can do security wise is choose good passwords. If you have strong passwords for both your user account and your banking account, I don't see that you should be at all uncomfortable about online banking and such.

As for antiviruses, they are completely optional for standard home usage on Linux. The most common reason Linux users run antiviruses is to protect other people who are running Windows. Linux is completely immune to an overwhelming majority of all malware out there, so it's entirely possible for a Linux user to download an "infected" file and be unaffected but send it on to a Windows user, at which point the virus would run. There are a handful of Linux viruses out there, but none that are even noteworthy.

EDIT: One thing I forgot to emphasize is that Linux is not indestructible. Probably one of the largest causes of security holes in Linux is overconfident users. Use common sense and you'll be safe.

---

### Post by cariboo on 2009-07-14
If you are going to run antivirus software, why run two that only scan for windows viruses? The only av program I know of that claims to scan for Linux malware is clamav.

---

### Post by aysiu on 2009-07-14
Well it's possible that your bank's network administrators could be inept... but barring that, the best thing you can do for online banking is use WPA2 encryption with a strong password for wireless (or just use a wired connection) and make sure your bank's login password is also a strong password.

Or... don't bank online.

This is true, regardless of what operating system you use (Windows, Linux, Mac), and a firewall or antivirus wouldn't be relevant in this situation.

---

### Post by bodhi.zazen on 2009-07-14
> **Mashuteichou said:**
> In Windows, I had it pretty much impossible for someone to get my information.

:lolflag:

> I was invisible to everyone, except where I was going, and all my information was encrypted and hidden.  It was also saved in a program that had a password on it so no one could really get into it.  

Linux, I have Firefox.  I keep getting mixed answers on firewall and antivirus stuff.  I have Firestarter loaded, Avast, and soon AVG, but some say its useless.  I am very paranoid with banking online, (My uncle lost $15,000 recently because he was hacked from someone in Australia) Granted he was on Windows, but it doesn't make it any better.  (Still a recovering Windows user)

Is Linux less, same, or more secure then a Window's XP with 10 programs on max?

A default installation of Linux is more secure then most "hardened" installations of Windows.

I see you are interested in security, this is good. Check most of what you know about Windows security at the door.

Security is all about EDUCATION. Windows users need a firewall because a default installation of windows has open, unsecured ports. With a default install of Ubuntu there are no open ports.

The question is really, what do you want to use a firewall for ? If you can not answer any better then "because" or "to make myself safer" then you do not need a firewall, :lolflag: .

In terms of internet banking, most of the security risk is in phishing or social engineering and neither a firewall or antivirus scan will help with those will they ?

Internet banking comes down to :

1. Make sure your connection is ssl (https).

2. If you use wireless, use wpa. Better, do not perform internet banking on wireless or public internet cafe.

3. Confirm the url is correct in your browser.

4. Use strong passwords.

I bet your "uncle" was the victim of social engineering and not some kind of crack to the OS or virus.

Security is not blindly installing firewalls and antivirus, security is understanding and guarding against the threats. "Mixed answers" are the result of insufficient understanding on your part. You are listening to opinions when you should be learning a new OS.

I suggest you start here :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") - There is a reason this is a sticky :rolleyes:

[How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604")

---

### Post by 3rdalbum on 2009-07-15
> **Mashuteichou said:**
> I have Firestarter loaded, Avast, and soon AVG, but some say its useless.  I am very paranoid with banking online

I'm surprised you're getting mixed answers on anti-virus. There are NO Linux viruses in the wild today, therefore no need for anti-virus to protect your own system. If you want to run an anti-virus program to scan for Windows viruses, to prevent yourself from accidentally passing on files that have already been infected, then that's your own business.

A firewall is not necessary on any computer unless you have a program that is listening on incoming ports. By default, Windows ships with services that listen on incoming ports, hence the need for a firewall. By default, Ubuntu ships with nothing that listens on incoming ports.

It can be a good idea to set up your IPtables firewall to block all incoming connections anyway, just in case you install something that listens without you realising it. Firestarter can do this, but it's kinda like shooting a fly with a bazooka - overkill! Note that you don't need the Firestarter program open to be protected, as the firewall is actually running inside the kernel. Also, be aware that many ADSL/cable modem/routers already contain a firewall.

Anyway, onto your main problem. These are the reasons why people get their details stolen:

1. The remote site gets compromised
2. The connection is intercepted mid-way
3. Your computer has been compromised by a malicious program that is listening to your data
4. You give your data to a third party (usually through phishing)

Assuming you don't do dumb things, like turn on SSH with a weak password and allow access to it from remote locations, your Linux machine will not be compromised (3). Firefox has an anti-phishing function that checks all websites you visit against a database of known phishing pages (4). Number (1) you have control over, and number (2) is only an issue if you're doing online banking on an insecure wireless network (do NOT do this).

In short, you're safe.

---

