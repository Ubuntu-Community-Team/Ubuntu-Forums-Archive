---
title: "Virus attack"
date: 2018-10-04
forum: New to Ubuntu
---

### Post by dave6 on 2018-10-04
Hi guys
I was just starting to write a letter using Libreoffice here in ubuntu mate, I had to check on a letter which I wrote maybe 8 weeks back and in front of my eyes every thing just started to disappear, lost all of my files on the backup drive and all the photographs on there as well  Every thing that I had backed from before I installed Ubuntu Mate 

Strange eh ?

Dave

---

### Post by QIII on 2018-10-04
In a general context, "virus" is a concept foreign to Linux.

You may have unwittingly allowed some form of malware to be installed.  There is ransomware that can attack Linux now (particularly if your network has Windows machines attached), but that is not, strictly speaking, a "virus".

I would disconnect from the web right now, back up your system in its present state -- saving what data you can.  If you have, indeed, been compromised, you can never trust that system again and should reinstall afresh. Start searching logs -- on the backed up system and off line -- for some indication of what has happened.

---

### Post by TheFu on 2018-10-04
> **dave6 said:**
> Hi guys
I was just starting to write a letter using Libreoffice here in ubuntu mate, I had to check on a letter which I wrote maybe 8 weeks back and in front of my eyes every thing just started to disappear, lost all of my files on the backup drive and all the photographs on there as well  Every thing that I had backed from before I installed Ubuntu Mate 

Strange eh ?

Dave

My first question would be, "have you done anything stupid?"   You know what I mean.  
Did you enable VNC or RDP remote connections without requiring a VPN or other secured tunnel?   
Do you use PPTP (worthless)?  
Do you allow any remote access using passwords?  
Did you download any 3rd party software directly with an "install" or "setup.exe"?  That is an anti-pattern on Ubuntu.

These are all security failures.

And do you have daily, automatic, versioned, disconnected, backups?  If the "backups" are always connected to the machine actually being backed up like storage, that is a problem.

---

### Post by dave6 on 2018-10-04
Hi guys thanks for your reply's and help. QIII, by the time you had written your good advice I had unplugged from the internet and started to search about.
TheFu, Never have done VPN, oddly I know what that stands for, as for the other letters er, No: don't know what they would be, nor am I interested....("have you done anything stupid?"   You know what I mean.)  I am doing well to do an update, never mind any thing else, I don't like change..

Do you allow any remote access using passwords?  ,,,, this computer does not even have wifi nor any thing else..

Did you download any 3rd party software directly with an "install" or "setup.exe"?  That is an anti-pattern on Ubuntu. 3rd party software, I once downloaded and updated to ubuntu 16 from version 12, that were a bad'un err, No...to any thing else

Returning to QIII and his advice

Start searching logs -- on the backed up system and off line -- for some indication of what has happened. 		I think I found the little bit of rouge data (the little B)  What should I do with it ??

Dave

---

### Post by dave6 on 2018-10-04
And, I forgot to tell you all... I found all the missing 15 000 files close to 200gb and have it reinstalled, after I done a backup to a separate drive which is now turned off

Dave

---

### Post by mastablasta on 2018-10-05
> **dave6 said:**
> Hi guys thanks for your reply's and help. QIII, by the time you had written your good advice I had unplugged from the internet and started to search about.
TheFu, Never have done VPN, oddly I know what that stands for, as for the other letters er, No: don't know what they would be, nor am I interested....("have you done anything stupid?"   You know what I mean.)  I am doing well to do an update, never mind any thing else, I don't like change..

Do you allow any remote access using passwords?  ,,,, this computer does not even have wifi nor any thing else..



if it is access to internet, then it can be accessed from internet. and if it has access to internet it can be hacked remotely particularly if user unwittingly enabled (e.g. if you followed any instructions on internet to install something or set up something) remote access to the machine.


logs are in /var/log

or you can use log viewer. but various network and access logs are of particular interest.

the process of securing your pc comes under the name "hardening". there are a couple of guides online. most aimed at server but they help desktop as well. for example:

Ubuntu security documentation: [https://help.ubuntu.com/lts/serverguide/security.html.en](https://help.ubuntu.com/lts/serverguide/security.html.en)

hardening guide: [https://linux-audit.com/ubuntu-server-hardening-guide-quick-and-secure/](https://linux-audit.com/ubuntu-server-hardening-guide-quick-and-secure/)

guide by digital ocean (a company that rents server space but also provides some awesome guides and manuals): [https://www.digitalocean.com/community/questions/best-practices-for-hardening-new-sever-in-2017](https://www.digitalocean.com/community/questions/best-practices-for-hardening-new-sever-in-2017)

a list of things to harden: [https://gist.github.com/lokhman/cc716d2e2d373dd696b2d9264c0287a3](https://gist.github.com/lokhman/cc716d2e2d373dd696b2d9264c0287a3)

and many others.

---

### Post by TheFu on 2018-10-05
If the computer isn't networked, then the only attack vector for a virus would be connecting portable storage to it.  If you didn't do that, then you do not have a virus.  A hardware failure is most likely.

---

