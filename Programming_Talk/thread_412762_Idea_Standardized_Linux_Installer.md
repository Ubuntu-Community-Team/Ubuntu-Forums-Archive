---
title: "Idea: Standardized Linux Installer"
date: 2007-04-18
forum: Programming Talk
---

### Post by ninjabob7 on 2007-04-18
Why is there no standard way to install Linux? Every distro I've tried has a completely different installer. The Debian installer is one of my favorites because it has so many options: netinst, standard CD install, HD based, straight from existing linux... The Ubuntu alternate installer looks almost exactly the same.
At least Debian-based systems should have some standard method since they all use debootstrap. You could also have smaller CD images if you didn't have an installer on every one. Basically it could work like this:
[LIST=1]
[*]Launch the installer from CD, HD, Linux, etc.
[*]Give it a script for your distro (this could be downloaded or on a CD)
[*]The script would tell it where to get packages: CD, website, or already downloaded
[/LIST]
This way we wouldn't have to reinvent the wheel every time someone made a new distro.

Any thoughts?

---

### Post by duff on 2007-04-18
[http://klik.atekon.de/](http://klik.atekon.de/)

[http://autopackage.org/](http://autopackage.org/)

---

### Post by AdamG on 2007-04-18
We don't reinvent the wheel with every distro... you're right in thinking Ubuntu's installer is similar to Debian's; they are the same installer! Admittedly, Ubuntu's has been modified so there are fewer steps (user-friendliness and all) but I actually think that software packaging on Linux (installers included) is our trump card. Dpkg makes .msi files pale in comparison. I work at a community college helpdesk, and you couldn't imagine the money & effort they put into "packaging" windows software. Even when they get it done, it's a buggy, expensive system that makes me feel warm and fuzzy about my Ubuntu & Debian boxes.

Software packaging is Linux's strong point... if there's anything we do better, hands-down, than other OS's, it's that. (Oh, and webserving.)

---

### Post by ninjabob7 on 2007-04-20
Sorry, I guess I wasn't clear enough. I wasn't referring to software installation, I meant installing the actual base system. Normally it's done with a bootable CD that contains the installer and basic packages, but I think it would make more sense to have a separate installer.

---

### Post by H.E. Pennypacker on 2007-05-09
> Dpkg makes .msi files pale in comparison. I work at a community college helpdesk, and you couldn't imagine the money & effort they put into "packaging" windows software. Even when they get it done, it's a buggy, expensive system that makes me feel warm and fuzzy about my Ubuntu & Debian boxes.

Would you mind talking about this a little more?  I am interested in knowing what your college is doing, and how their packaging is worse than what Linux has to offer.

---

### Post by siiib on 2007-05-09
i agree with you pennypacker.. in fact its why i and many others use ubuntu cos you just go apt-get and it does it mostly.. but to be honest its a shambles.. .i haven't had a windows installer fail for years so i don't know what this other guy is using.. every time i install something on linux i hold my breath. it usually fails for some reason.. i've been bitching about it for years and getting my head bitten off by 'advocates' (fascists)

---

### Post by H.E. Pennypacker on 2007-05-09
> **siiib said:**
> i agree with you pennypacker.. in fact its why i and many others use ubuntu cos you just go apt-get and it does it mostly.. but to be honest its a shambles.. .i haven't had a windows installer fail for years so i don't know what this other guy is using.. every time i install something on linux i hold my breath. it usually fails for some reason.. i've been bitching about it for years and getting my head bitten off by 'advocates' (fascists)


siib, this thread is actually about something else (the operating system installer, not application installers), but you are right.  Don't worry about people getting upset with you.  Continue to complain, and there will be change one day.  Put up with the pain of complaining for as long as it is needed.

You're absolutely right about never knowing whether things will go right or wrong.

---

### Post by siiib on 2007-05-10
heh so it is.. sorry i have a bee in my bonnet about it:)

---

