---
title: "is linux safe from viruses?"
date: 2008-01-13
forum: Recurring Discussions
---

### Post by neratokio on 2008-01-13
What about viruses and other bad stuff?  Someone told me, that they just dont "work" on linux. So whats the truth?

---

### Post by perlluver on 2008-01-13
They indeed do not.  However if you transfer between Linux, and Windows, you may want to scan them files.

---

### Post by timbounceback on 2008-01-13
In a nutshell: Technically, no, Linux is not safe from viruses. However, at the moment, there aren't any except for proof-of-concept viruses, and developing one would be more difficult than developing one for Windows because of the presence of a root account.

---

### Post by Dr Small on 2008-01-13
Anyone can make a simple virus for Linux, and be destructive, but there are not many big circulated viruses out there that you should worry about.

If you are installing from the repositories, then everything is checked and scanned on their end, and you will be installing safe applications.

Dr Small

---

### Post by xpod on 2008-01-13
2 years come July we`ll have been using Linux....*buntu mainly but we`ve never had a problem like that,never used AV either of course.....not in Linux anyway.Only used Windows for a few months prior to that of course so what do i know about Windows viruses:)

I used to use a desktop as router/firewall/gateway but thats handled by the proper router now.........(i do miss my firestarter though):)

I somehow dont think we`d be having *those* types of problem tooooo much even if we were all using Windows.It`s all just a matter of education & common sense......just:-\"

---

### Post by skymera on 2008-01-13
Viruses will come one day.
probsbly soon.

once linux goes full mainstream it will be a virus magnet.

but still, they cant do much unless thet are sudo'd

---

### Post by p_quarles on 2008-01-13
> **skymera said:**
> but still, they cant do much unless thet are sudo'd
Exactly, which is why Linux *won't* become a "virus magnet." 

There are much more efficient ways of attacking an unsecured *nix system. Self-replicating viruses don't even make the top ten list.

---

### Post by limac on 2008-01-13
no operating system is safe from virus once internet comes into play. they all are vulnerable, but campared to Apple and windows (in my opinion) Linux is safeER. Let jsut look at it this way: Linux is 75% secure abd 25% vulnerable...

Best Regards,
limac

---

### Post by Darkhack on 2008-01-13
People seem to misunderstand the meaning of a virus.  A virus (like a biological one, where it gets its name) is self-replicating meaning that it attaches itself to other programs and can be spread when people share executables for which the virus has attached itself to.  A worm is even more destructive because it can self-replicate through a network without the user needing to share any specific file.  It just travels on its own.  Linux is designed in such a way that self-replicating code doesn't work properly.  Of course, it's possible to create a virus for Linux by finding an exploit which allows for this, but such exploits are usually patched at the kernel level.  *Any* OS is suspetible to destructive code if a user downloads and runs a binary.  That's not the same thing as a virus which self-replicates or malware which sneaks its way onto the system without the users knowledge.

---

### Post by vexorian on 2008-01-13
Yes, viruses can run in Linux.

You just need to use "sudo wine" before calling the virus file.

Then the virus will "run" it will proceed to infect your WINE installation.

Of course, it will not harm you unless the virus likes to delete "my documents" and you set up WINE to use /home/name as "my documents" , even if it does so you probably have a backup...

So, things you need to make a windows virus destroy your ubuntu life:

- Avoid making backups of your home folder.
- Manually run the virus with WINE and sudo.
- Let it be a virus that targets "my documents" (most viruses lately just like to spy your messenger to get email addresses instead of removing files...)

Btw, if your WINE is ever infected, you can make winecfg or something like that recreate a windows folder and all is fixed once again...

---

### Post by Dimitriid on 2008-01-13
Linux is build to be more secure, the damage a virus could do if widespread enough would be minimal and patched fast enough so it would almost be a non-issue for most popular distros.

So you won't get virus infections anytime soon, take the sky is falling arguments about the increasing popularity with a grain of salt ( 1% to 2% market share? Yea wow explosive growth :rolleyes: ) you probably wont need to worry about it for years.

---

