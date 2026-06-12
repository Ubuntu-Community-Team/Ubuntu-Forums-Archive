---
title: "[SOLVED] Security, spyware etc"
date: 2008-06-28
forum: Recurring Discussions
---

### Post by Felicity_X on 2008-06-28
I have been busily reading up all I can find on the net about Linux and Firefox security.  I think I understand the concept of the operating system not being visible to the Internet, provided no user apart from the operating system is set up as a root, and why that renders it impervious to viruses and attacks which require a separate firewall for protection on, e.g. a Microsoft system.

Is this also the case for spyware?  I have not been able to get a definitive answer on that from what I have read.  I would like to do my internet banking on my Ubuntu system, but do not wish to take the risk of doing it without purchasing an anti-spyware package should that be necessary for safety.:mrgreen:

---

### Post by luisito on 2008-06-28
Most software in Linux is open source. There can be no spyware there or any other trap because anyone can see the programming code.

The only closed source software you may have could be skype, the nvidia drivers, googleearth, or maybe some other proprietary software you could have bought (ex. matlab). If you don't have any of this you are 100% safe. If you do have them, you are still quite safe since they seem to be trustable well known companies and it is extremely unlikely that they would put some spyware in their programs.

Doing your internet banking under linux is definitely a good idea.

---

### Post by gandaran on 2008-06-28
Felicity_X
if it makes you feel more secure, install **rkhunter** (find it in synaptic), rkhunter will scan your computer every day at start-up for every threat to linux, rootkits and trojans, all you have to do is check /var/mail/ folder for anything found or run rkhunter on command line.

any other commercial linux anti-virus/anti-spyware programs, paid or free, are completely useless protecting linux, as they only scan for windows virus.

---

### Post by shae on 2008-06-28
Spyware has to be installed just like viruses.  As such they are impeded just like viruses by Linux's access controls.  Furthermore, Firefox 3 by default has anti-phishing tools build in, but you can also add siteadvisor to firefox for an extra layer of protection.  About the only way into a linux system for a virus or spyware is through user intervention.  One thing to note is that Linux's access controls prevent moderations to the hosts file preventing someone from overriding your bank's site and sending you to their phishing site.

---

### Post by tyfius on 2008-06-28
Most viruses and other malware applications are developed for Windows. So that whole group (like 95%) is unable to affect your system. The other 5% are Mac and Linux, but is mostly outdated :)

If you want to be sure, you can always install a virus scanner on Linux (such as AVG).

---

### Post by fatality_uk on 2008-06-28
> **tyfius said:**
> Most viruses and other malware applications are developed for Windows. So that whole group (like 95%) is unable to affect your system. The other 5% are Mac and Linux, but is mostly outdated :)

If you want to be sure, you can always install a virus scanner on Linux (such as AVG).

This isn't right. The reason that there are no Linux viruses in the wild is that Linux is totally differently to Windows in every respect. Since the web is essentially built on Linux, it would be a huge benefit for a virus writer to be able to attack a Linux machine. There are a lot of posts on this forum stating why.

In addition, Linux has iptables, an effective firewal, built into the operating system. If you have to bank online, the safest way to do it is via Linux.

---

### Post by p_quarles on 2008-06-28
Moved to Recurring Discussions.

Yes, there is spyware for Linux, and some of it is available in the Ubuntu repositories (a keylogger, for instance, among other things). 

But, no: so long as you follow good security practices (and the default Ubuntu installation does), there is next-to-zero possibility of getting spyware installed without your knowing it.

---

### Post by brian_p on 2008-06-28
> **Felicity_X said:**
> Is this also the case for spyware?  I have not been able to get a definitive answer on that from what I have read.  I would like to do my internet banking on my Ubuntu system, but do not wish to take the risk of doing it without purchasing an anti-spyware package should that be necessary for safety.:mrgreen:

Here is a recent post which is, in my opinion, as definitive on the subject of spyware as you can get:

[https://lists.ubuntu.com/archives/ubuntu-users/2008-June/150376.html](https://lists.ubuntu.com/archives/ubuntu-users/2008-June/150376.html)

Do not waste your money on any anti-spyware software. Just follow good practice: make sure you go to authentic banking site, conduct the transaction from a computer you trust, check https is being used and do not accept a certificate if firefox gives you a warning.

Antivirus is most definitely not needed and I'd be inclined not to give rkhunter any disk space.

---

### Post by sub2007 on 2008-06-28
Unlike "classic" viruses (the distinction is getting blurrier now but the classic viruses were designed for mass destruction mainly) spyware is created for one reason and one reason only - for money. Most of the prolific spyware (CoolWebSearch and now Smitfraud) is created by organised criminal gangs with teams of experienced coders. There probably aren't enough desktop users using Linux at the moment to make it a financially viable target for spyware writers to target their energies on. Windows still has a greater than 90% market share of all the world's desktop PCs. Take the Smitfraud "fake antivirus" - even if you're only able to install that on 1% of PCs and you can only manage to get 1% of those people to cough up the $60, you've still had a good payload from that. Likewise if it's only possible to infect 1% of Linux users and only 1% of those pay up, how much money are you actually going to make from that? Not enough to cover your overheads. As, or if Linux's market share increases enough to make it profitable then there's no doubt in my mind that they'll start. However with Linux you still have the challenge of increased under the hood security over Windows. But they'll get round it, we underestimate how smart these people are. They evolve new techniques faster than the security researchers do: F-Secure said that MBR viruses were unworkable, and yet now they're out in the wild. With social engineering as well there's absolutely no problem - if you think you're getting a codec then you'll install it, give it your root password, anything because you don't suspect it's dangerous. I think it's a long way off before we see anything similar to the problem with malware we have on Windows, I'm certainly not worried. Even Mac spyware is few and far between (but it is more of a problem that it is on Linux).

Keyloggers are dicey territory. It's not illegal (although it is arguably unethical) to install a keylogger on your own computer but it is to install one on someone elses computer. So they don't fit the category of malicious spyware (although every antispyware program targets them) but they can be used for malicious purposes if someone else happens to control them.

---

### Post by brian_p on 2008-06-28
> **p_quarles said:**
> Yes, there is spyware for Linux, and some of it is available in the Ubuntu repositories (a keylogger, for instance, among other things).

netcat, wireshark and ngrep look suspiciously like spyware too.

---

