---
title: "[SOLVED] Firewall, Antivirus Questions"
date: 2008-12-03
forum: Recurring Discussions
---

### Post by Valtiel on 2008-12-03
Now, I'm here to ask you two questions:

**1- What is the best Firewall for LINUX/Ubuntu?** I saw two on the add/Remove Software dialog window in Ubuntu, but it fails to  give me detailed information about them. I yet don't understand how installing and unistalling software in Ubuntu work, this is why I'm asking here instead of installing them and taking them for a test drive. 

**2- Do I need an Antivirus, if so which one is considered to be the best?** Maybe there are a couple on the Add/Remove dialog window, but I really didn't see any.

Thanks.

---

### Post by gn2 on 2008-12-03
1: it's already installed, it's called iptables

2: you don't need any, there isn't a single Linux virus in the wild.

Reading [this]("http://ubuntuforums.org/showthread.php?t=510812") will be useful.

---

### Post by mkvnmtr on 2008-12-03
As I understand it the apps you saw are just the front end to allow you to personally mess up the settings of the firewall that is already installed. At a later date when you have special needs for altering your firewall and understand exactly what you need to do then you might install a front end. Most probably if you understand what needs to be changed you will prefer to do it from the command line. I for one would not change anything and I love to mess up my system.

---

### Post by evilkastel on 2008-12-03
Thats roughly a lie. There are a few linux viruses, but you should not worry abiut them. Still, if you don't mind spreading viruses that can't hurt you but can hurt windows users... Clam is the AV i'll recommend. The default firewall works, but if you wanna protect your PC you should close ports... thats way to advanced atm. so for now you are good, remember , we still get spyware (in a lesser scale).And before getting to worry about this, you migh want to learn how GNU/linux and ubuntu works, how to install or uninstall apps and everything. Congrats on the switch.

---

### Post by handydan918 on 2008-12-03
> **evilkastel said:**
> Thats roughly a lie. There are a few linux viruses, but you should not worry abiut them. 
If there are in fact any Linux viruses in the wild, they should definitely be worried abiut (sic).

And I feel sure that you have a link to these "in-the-wild" linux viruses, right?

):P

---

### Post by cardinals_fan on 2008-12-03
1. I would recommend a firewall; here's a guide: [https://help.ubuntu.com/8.10/keeping-safe/C/firewall.html](https://help.ubuntu.com/8.10/keeping-safe/C/firewall.html)

2. I would never, ever, ever use an antivirus application on any platform.  Viruses are really quite rare nowadays - most infections come from malware such as trojans relying on social engineering (where you click something you shouldn't).  Practice good security (don't use IE, use NoScript or something similar, and don't visit shady sites or install stuff from outside the package manager) and you don't need an AV.

*Disclaimer: I strongly believe that everything said above is true, but I assume no responsibility for anything*

---

### Post by Valtiel on 2008-12-03
> **evilkastel said:**
> Thats roughly a lie. There are a few linux viruses, but you should not worry abiut them. Still, if you don't mind spreading viruses that can't hurt you but can hurt windows users... Clam is the AV i'll recommend. The default firewall works, but if you wanna protect your PC you should close ports... thats way to advanced atm. so for now you are good, remember , we still get spyware (in a lesser scale).And before getting to worry about this, you migh want to learn how GNU/linux and ubuntu works, how to install or uninstall apps and everything. Congrats on the switch.

That is where I'm right now, digesting all this info as well as I can since knowing isn't just enough. As you might imagine, when it comes to my now LINUX-PC, I'm completely lost. Well not so much in some areas, but still plenty on the several ways there are to install software, OS settings, UI setting and effects and 100% on the LINUX/Ubuntu Folder/File structure. 

I have some articles for Windows users moving to Linux but none that explain thing in a equivalent level. Is there documentation that talks about the equivalence of locations/terms/folder structure/etc of windows in LINUX/Ubuntu?

ex. In windows ______ the equivalent in Ubuntu is ______

---

### Post by Valtiel on 2008-12-03
> **cardinals_fan said:**
> 1. I would recommend a firewall; here's a guide: [https://help.ubuntu.com/8.10/keeping-safe/C/firewall.html](https://help.ubuntu.com/8.10/keeping-safe/C/firewall.html)

2. I would never, ever, ever use an antivirus application on any platform.  Viruses are really quite rare nowadays - most infections come from malware such as trojans relying on social engineering (where you click something you shouldn't).  Practice good security (don't use IE, use NoScript or something similar, and don't visit shady sites or install stuff from outside the package manager) and you don't need an AV.

*Disclaimer: I strongly believe that everything said above is true, but I assume no responsibility for anything*


Thanks for the link. By the way, that is some good advice there. If there is something you have to not learn but be a master at it in windows is in being able to detect those harmful sites, link, attachments, software, adware and such that smothers the Windows OS. Sadly we know that not everybody gets to this point.

---

### Post by oldos2er on 2008-12-03
Google can show you many websites that explain Linux filesystem structure; but I don't know of any that compare it to Windows. I think the two are too fundamentally different.

---

### Post by Grant A. on 2008-12-03
> **cardinals_fan said:**
> 1. I would recommend a firewall; here's a guide: [https://help.ubuntu.com/8.10/keeping-safe/C/firewall.html](https://help.ubuntu.com/8.10/keeping-safe/C/firewall.html)

2. I would never, ever, ever use an antivirus application on any platform.  Viruses are really quite rare nowadays - most infections come from malware such as trojans relying on social engineering (where you click something you shouldn't).  Practice good security (don't use IE, use NoScript or something similar, and don't visit shady sites or install stuff from outside the package manager) and you don't need an AV.

*Disclaimer: I strongly believe that everything said above is true, but I assume no responsibility for anything*

Firestarter development was discontinued.

---

### Post by cardinals_fan on 2008-12-03
> **Valtiel said:**
> Thanks for the link. By the way, that is some good advice there. If there is something you have to not learn but be a master at it in windows is in being able to detect those harmful sites, link, attachments, software, adware and such that smothers the Windows OS. Sadly we know that not everybody gets to this point.
The term "virus" is often misused.  Actual viruses (which install without user authorization, such as the infamous lovebug) have become quite rare thanks to screening by ISPs and email providers.  I never got anything on Windows because I was careful.  Though malware for Linux is much less likely thanks to smaller market share, good security makes surfing more pleasant anyway.
> **Grant A. said:**
> Firestarter development was discontinued.
Plenty of dead projects still work fine.  With that said, I only linked to the official Ubuntu documentation for Ibex.  I manage my iptables a bit more manually.

---

