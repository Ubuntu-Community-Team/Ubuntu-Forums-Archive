---
title: "Anti-Virus - is it necessary?"
date: 2010-01-13
forum: Recurring Discussions
---

### Post by NiGhtMarEs0nWax on 2010-01-13
I wouldn't ever consider running Window$ without an anti-virus, but is it necessary on Linux? i mean, a lot of people say there are NO virus' in the wild for Linux; but i find that hard to believe.

Avast on Windows was as good as it got for a free product; it was awesome. if it's really necessary, which would you suggest? i heard many people say ClamAV is good, but does it cut the beef? an AV is only as good as its signatures, AVG is an example of complete misconception when it comes to protection, a lot of people really liked it; but i couldn't have rated it lower if the developers likes to torture small kittens.

if so, which one and why?

Thanks!

---

### Post by FuturePilot on 2010-01-13
Please read though the [Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812") sticky. There's a good section about anti-virus there.

---

### Post by Bucky Ball on 2010-01-13
[QUOTE=NiGhtMarEs0nWax]
Anti-Virus - is it necessary[/QUOTE]

no. Good money has been offered to create on that works.

---

### Post by howefield on 2010-01-13
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by Grenage on 2010-01-13
ClamAV is handy for scanning files on behalf of Windows users/machines, but other than that you don't need AV.

Not yet, anyhow.

---

### Post by ajgreeny on 2010-01-13
The only viruses out there are windows viruses, so you could ask, "why bother to guard against them?"  I tend to go with that thought.  I know a lot of people like to try to avoid sending viruses to other people via emails and shared files etc etc, but again, you could easily ask, "why bother to try and keep other people free of viruses; if they can not take their own precautions, why should we worry?"

Having said all that, however, if you do send a lot of files to windows users, and certainly if you act as a server to other windows systems, it does make sense to check every so often.  Just bare in mind, it will not make any difference to your setup, and at the moment, unlike windows, there are no virus checkers that continuously run in the background as resident checks using up system resources, other than some of the email server daemons, eg clamd.

Your choice!  Personally, I haven't had a virus checker on my Ubuntu system for about three years now and have had no problems at all.

---

### Post by NiGhtMarEs0nWax on 2010-01-13
Thanks for the replies! i thought as much. i'm reading through that security post now. some interesting stuff.


Cheers!

---

### Post by bit mad on 2010-01-13
There are possible vectors for infection...
[http://ubuntuforums.org/showthread.php?t=1349678](http://ubuntuforums.org/showthread.php?t=1349678)
:)

---

### Post by ajgreeny on 2010-01-13
> **bit mad said:**
> There are possible vectors for infection...
[http://ubuntuforums.org/showthread.php?t=1349678](http://ubuntuforums.org/showthread.php?t=1349678)
:)
Agreed, but would a standard, ie windows virus checker have found that "screensaver"?  I doubt it.

---

### Post by bit mad on 2010-01-13
If something like that works, with a real payload, then it would become a problem and the AV progs would eventually look for it, but that wouldn't be much help for the initial victims.

---

### Post by running_rabbit07 on 2010-01-13
> **bit mad said:**
> There are possible vectors for infection...
[http://ubuntuforums.org/showthread.php?t=1349678](http://ubuntuforums.org/showthread.php?t=1349678)
:)

That isn't a virus, but a socially engineered malware. A virus has the ability to work on its own. If you send the corrupted .deb to another user it can't install itself when they open the email.

---

### Post by cariboo on 2010-01-13
This has been discussed more time than I can count. Moved to Recurring.

---

### Post by MasterNetra on 2010-01-13
If i remember correctly the last virus there was for linux existed i think back in the 80's and linux or unix, whatever was rebuilt from the ground up to prevent viruses. However I suppose it is possible to have a Linux virus but would require help from the infected user in order to do any real damage to a system, like say purposely giving it root access. Otherwise if you exercise basic caution and use common sense you should be fine. A firewall on the other hand...well its really needed for servers I suppose otherwise Ubuntu itself has a great built in firewall...not active by default i think, but there are GUI based tools to manage it. (otherwise you can manage it from terminal if you know how.)

---

