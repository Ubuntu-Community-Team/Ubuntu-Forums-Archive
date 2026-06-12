---
title: "apt portability"
date: 2006-08-17
forum: Programming Talk
---

### Post by illynova on 2006-08-17
Hey guys,

Has apt ever been ported to a windows enviroment? If not, how difficult would you think it'd be to port it? I have a decent amount of expierence in C++, but I've never worked on anything aproaching a porting of a major project that I didn't write.


Just wondering.... it'd be really nice to get an apt system going on windows, mostly for delivering game updates (think steam)

---

### Post by LordHunter317 on 2006-08-17
It would be pointless, because Windows already has a technically superior solution for this.  Look at the Microsoft Installer (MSI) stuff.

---

### Post by Warbo on 2006-08-18
Porting the programs apt-get and dpkg would not be too difficult, however you would then need to package every DLL and other things that might be needed on a Windows system, and catagorise them and set up dependencies. You would have to package every piece of software yourself before installing it with apt, since nobody else would do it for you, you would lose the source abilities for most libraries and things and it may even be illegal to package some things. Systems like APT are uniquie to Free Software systems since anybody is Free to redistribute and modify the components (like putting them in packages), and systems like Dpkg and RPM need to be supported officially by the OS, or else it would not garner much interest and the OS would be a moving target that didn't care how hard it was for you to sort out dependencies when they switch to a new version of something like Python.

---

### Post by LordHunter317 on 2006-08-18
> **Warbo said:**
> Porting the programs apt-get and dpkg would not be too difficult,Yes, it would, because they expect a whole bunch of UNIX constructs that have poor or nonexistent analogues on Windows.

> you would lose the source abilities for most libraries and things and it may even be illegal to package some things. That makes no sense.

> Systems like APT are uniquie to Free Software systemsNo, they are not.  Every commerical UNIX and just about every commerical OS has an APT work-a-like, though most are of inferior quality.

> and systems like Dpkg and RPM need to be supported officially by the OS,Not really.  MSI wasn't standard forever on Windows, it's still not an enforced standard, and people get along just fine.

---

