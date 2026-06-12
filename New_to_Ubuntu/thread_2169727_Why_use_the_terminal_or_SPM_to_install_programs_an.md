---
title: "Why use the terminal or SPM to install programs and packages?"
date: 2013-08-23
forum: New to Ubuntu
---

### Post by Frysen on 2013-08-23
Ive recently switched from windows to ubuntu, and i try to learn as well as i can.

The way of aquiring programs in ubuntu is puzzling me. In windows it was simple - you just downloaded some installation file and installed the program. In ubuntu ive been learned to use the terminal or a program "Synaptic Package Manager" (SPM) to download and install new programs.

The ubuntu way seems to limit the possibilities, since i guess you seach through an isolated database instead of the whole internet. Am i wrong on this point?

Is it also possible to download programs from anywhere on the internet? Are there some disadvantages to do so?

---

### Post by ibjsb4 on 2013-08-23
The packages in synaptic (software center) have a ubuntu maintainer.  Third party packages (also launchpad) are better left alone until you get a better feel for linux.  Not always (there are many good ones), but they can be buggie and create system problems.

If you have an idea of what your looking for you can search launchpad.

[https://launchpad.net/ubuntu/+search](https://launchpad.net/ubuntu/+search)

---

### Post by Buntu Bunny on 2013-08-23
> **ibjsb4 said:**
> The packages in synaptic (software center) have a ubuntu maintainer.  

This is a good point. However, there are software out there that is not in the Software Centre nor Synaptic, and many of them offer a download for Ubuntu, or at least Debian. For help installing these, you can use GDebi.

---

### Post by Impavidus on 2013-08-23
Synaptic, the software centre and apt-get install programs from an isolated database, which is very large (39455 packages available on my version 12.04). This offers one-click installation, automatic updates and the guarantee that it won't contain malware or damage your system in any way (well, usually. On rare occasions there may be nasty bugs). Manually installing something you downloaded from a random website is possible, but should be your last resort. That way often has more complicated installation procedures, won't offer automatic updates, will make it difficult to check compatibility with your system and won't protect you from malware.

---

### Post by newb85 on 2013-08-23
Lots of good info so far.  I will add that all apt-based package managers (apt-get, synaptic, and software center--they all do the same things under-the-hood) can install additional packages by adding more sources to the list.

Two tech blogs that often recommend good sources are webupd8.org and omgubuntu.co.uk

---

### Post by jocheem67 on 2013-08-23
The use of package management has the advantage of safety for the end-user. A better view on uninstalls of applications, uniform management for outside developers of apps through launchpad/ppa's, these are bonusses. Shady exe_like installers from shady websites are not necessary to use a fully equipped linux distro.
And the terminal is just quicker and lighter after a period of getting used to. And more fun.

---

### Post by ian-weisser on 2013-08-23
> **Frysen said:**
> The ubuntu way seems to limit the possibilities, since i guess you seach through an isolated database instead of the whole internet. Am i wrong on this point?

It's a question of risk and effort...and perspective
On Mac or Windows, you are responsible for determining if what you downloaded is both compatible and trusted enough to give it access to your system. You are responsible for installing dependencies. You may (or may not) have a greater selection, but you also assume greater risk.

The Ubuntu repositories are tested for compatibility, and only trusted uploaders are permitted, so you don't (currently) need to run antivirus. Developers know that specific versions of shared libraries are available, so the software can be much smaller and the system can handle dependencies automatically.

Your question assumes that more = better. Sometimes that is true, sometimes not.


> **Frysen said:**
> Is it also possible to download programs from anywhere on the internet? Are there some disadvantages to do so?

Yes, it's possible and easy. The disadvantages are that you assume more risk, and that internet software is unsupported by this community.

---

### Post by ibjsb4 on 2013-08-23
> **newb85 said:**
> can install additional packages by adding more sources to the list.

You also have a couple built in.  Open your software-sources.

[ATTACH=CONFIG]245633[/ATTACH]

You do not need 'source code'.

---

### Post by Quackers on 2013-08-23
Using SPM guarantees that any dependency issues can be resolved/installed at the same time. That's a big bonus for newer users.

---

### Post by Frysen on 2013-08-26
I am positively surprised that so many people want to help a newbe like me. Thank you all!

You all seem to agree that using "apt-get package managers" (a new phrase for me) is the best, so i guess i will go with these!

Just one follow up question:

> **ian-weisser said:**
> 
The Ubuntu repositories are tested for compatibility, and only trusted uploaders are permitted, so you don't (currently) need to run antivirus. Developers know that specific versions of shared libraries are available, so the software can be much smaller and the system can handle dependencies automatically.


Who performes these tests? It seems like a huge amount of work to do that! Who decides what can be found when i seach for software in the terminal?

---

### Post by Frogs Hair on 2013-08-26
See the link .  [https://wiki.ubuntu.com/AppReviewBoard](https://wiki.ubuntu.com/AppReviewBoard)

---

