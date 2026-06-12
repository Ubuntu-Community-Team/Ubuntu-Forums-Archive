---
title: "Security / Viruses etc"
date: 2010-01-28
forum: Recurring Discussions
---

### Post by ub_beginner on 2010-01-28
I am downloading ubuntu 'as we speak' so I am not even a novice yet !!!
What are the virus/firewall implications of ubuntu - are virus checkers built-in , is ubuntu effected by virusues , if not built-in then are there 'free' proviers?
 
rgds

---

### Post by A&#11375;A on 2010-01-28
Ubuntu, like other Distros of linux are less likely to be infected by viruses because they have a much smaller market share. Less Exposure means they are less likely to be attacked.

Ubuntu ships with a basic firewall, this should suffice for most users.

---

### Post by ChemicalForce on 2010-01-28
Ubuntu is mostly secure and mostly virus free. they're are couple virus scanning tools in the package manager but you don't really need them. i don't use any anti-virus or virus scanning tools but only thing you would mostly see is rootkits
hopefully this helps :] take care.

---

### Post by Leppie on 2010-01-28
some free av's: clamav, fprot, avg, avira

---

### Post by juancarlospaco on 2010-01-28
> **A&#11375 said:**
> Ubuntu, are less likely to be infected by viruses because they have a much smaller market share.
.

***No!***

---

### Post by ub_beginner on 2010-01-28
But the source of most viruses are emails / downloaded files , and I will be receiving the same volume as under windows. Will ubuntu protect me from the potentail viruses that are in those sources

---

### Post by ChemicalForce on 2010-01-28
> **ub_beginner said:**
> But the source of most viruses are emails / downloaded files , and I will be receiving the same volume as under windows. Will ubuntu protect me from the potentail viruses that are in those sources
 yes, most viruses are design to target windows machines only so if you download a virus file you won't be infected because it can't activate on linux machines.

---

### Post by Leppie on 2010-01-28
> **ub_beginner said:**
> But the source of most viruses are emails / downloaded files , and I will be receiving the same volume as under windows. Will ubuntu protect me from the potentail viruses that are in those sources
as ChemicalForce stated, rootkits most probably are the biggest danger, but ubuntu has built in protection for that. scripts usually are aimed at windows systems, so won't do you much harm.

if you're so worried about viruses, you may want to check your sources instead...

---

### Post by Gazbuntu on 2010-01-28
Not a bad idea to use ClamAv to manually scan your downloaded files if you plan on sending/forwarding them to Windows friends.

---

### Post by lisati on 2010-01-28
Although there doesn't seem to be the same need for antivirus specifically for Ubuntu, some email providers and ISPs like you to have *something* on your system.

---

### Post by A&#11375;A on 2010-01-28
> **juancarlospaco said:**
> ***No!***
...yes

---

### Post by Paqman on 2010-01-28
> **ub_beginner said:**
> But the source of most viruses are emails / downloaded files , and I will be receiving the same volume as under windows. Will ubuntu protect me from the potentail viruses that are in those sources

Software that's written for Windows, be that apps or malware, won't run on Linux.

There's several other reasons why Linux is more secure, the main ones being: 
[LIST]
[*]We have package managers that can close a security loophole in anything on the system. As soon as a security update is released for any Linux software, everybody's system gets updated straight away. Windows or OS X just can't do this.
[*]Every part of the system has built-in permissions that prevent modification by unauthorised people or malware.
[*]Open source software allows a wide range of people to inspect the code and spot potential vulnerabilities.
[/LIST]

---

### Post by Saghaulor on 2010-01-28
you can use bitdefender as well.

It doesnt' have a realtime scanner, but yeah.

Ubuntu and most other linux distrobutions are built different than Windows. They're build with security in mind. So things work a lil different.

There is a firewall built right into Ubuntu called uncomplicated firewall (ufw). You can enable it from the command line very easily.

```
sudo ufw enable
```

But there are also gui tools found in the repositories that can help you tweak the settings. Firestarter and gfw are two programs that make firewall administration easy on Ubuntu.

Also, Ubuntu has something called Apparmor that profiles applications, so that if they are harder to modify maliciously. However, I don't know how well implemented apparmor is.

I hope that this helps a little.

---

### Post by bodhi.zazen on 2010-01-28
There is a big sticky on security in the security forums

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

Otherwise I am moving this thread to recurring discussions.

@ub_beginner if you have a specific question please ask, otherwise such a general question causes endless debates , lol

---

### Post by ub_beginner on 2010-01-29
yes - many thanks

---

### Post by ub_beginner on 2010-01-29
> **bodhi.zazen said:**
> There is a big sticky on security in the security forums

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

Otherwise I am moving this thread to recurring discussions.

@ub_beginner if you have a specific question please ask, otherwise such a general question causes endless debates , lol
It was a general question where I needed to get a feel for peoples experience rather than 'over my head' technical answers

---

### Post by juancarlospaco on 2010-01-29
> **A&#11375 said:**
> ...yes

OMG, read, learn something, but dont say non-sense reply...

Market Share dont make an OS Virus-proof or not.

*Go to Wikipedia and read about SELinux, AppArmor, UFW, IPTables, Unix File Permissions (...)*

---

