---
title: "Linux Headers 13.3.0-37 problems?"
date: 2015-01-15
forum: New to Ubuntu
---

### Post by Thechromester420 on 2015-01-15
Hello people! I am running a Ubuntu "Hybrid" (Mixed files/data between XUbuntu, Ubuntu, Ubuntu Server, and Kubuntu which I am working on getting rid of) and I think I accidentally screwed up the Linux 13.3.0-37 packages.
If I do GRUB Menu --> Advanced Ubuntu --> Linux 13.3.0-35, Ubuntu runs fine (although some programs start to crash) but I can't re-install the 13.3.0-37 packages.
If I try to boot into Linux 13.3.0-37 data, Text appears (Not the regular XUbuntu Loading Screen) about the loading, and of course the usual "Cryptswap1 isn't loaded, continue waiting, S to skip, or M for manual fix" (If you wait it loads eventually) appears in text (also appears in the graphic XUbuntu Loading Screen, but as nicer text) and then the "Login" screen pops up. The resolution is off (I usually have it set to 1280x1024, this is definitely not that.) and the cursor is frozen, but appears as the standard text cursor.  Any help on how to fix this?

---

### Post by DuckHook on 2015-01-15
It is difficult making out what your problem is and since, by your own account, you have turned your install into something of a vegetable stew, I don't know if it makes sense trying to untangle it. You will probably spend more time doing so than doing a fresh install. Of course, if you are doing this as a learning excercise, then feel free to go nuts with it. But if what you want is a working production box, then best bet at this point is to back up your data and reinstall, but taking care this time not to jumble everything up. Do that on a separate partition, or better yet, on a VM where you can experiment all you want with no impact on your base install.

As for your current problems? It sounds like a combination of dpkg issues, GRUB issues and Xconfig/.profile issues. Not surprising when you have three separate DEs installed all fighting to reconfigure your OS for their own use and requirements. There may be other gurus here who have the chops to help you untangle this, but I don't.

The idea behind a distro (or a flavour for that matter) is to present a unified ecology where configuration parameters and apps have all been pretested to coexist with each other. When you jumble up distros (or flavours), you break this unification and configs, app behaviour, and coexistence all go out the window. "Hybridization" is best left to cars.

---

### Post by Thechromester420 on 2015-01-15
Okay, let me explain this "better" since I clearly confused people ( sorry :( )
what was originally installed is Ubuntu, but the visuals are XUbuntu, but there's also a topping of Ubuntu Server, while the selected display flavor is XUbuntu. This means that the operating system OPERATES AS NORMAL, and no bugs and/oror errors should occur. At least, this was the case until about two days ago.
It was about a few months since I ran Ubuntu, and DPKG wanted me to fix something upon opening the Synaptic Package Manager. I accidentally re-installed the Linux-headers-13.3.0-37 package, and.. I'm guessing I accidentally had focus set to the DPKG terminal instead of the other terminal when I pressed Control Z to force-close something, and upon starting up Ubuntu yesterday (or tomorrow if we're imagining this is present-tense) the XUbuntu loading screen was in text, not the usual graphic loading screen.
The Cryptswap1 loading issue has been occuring for several months now, and nothing fatal has seemed to occur from waiting for it to load (I never skipped or did manual recovery)
Fast-forward back to yesterday (again, if present-tense this would be to tomorrow) I discovered  that loading advanced ubuntu 13.3.0-35 allows everything to run perfectly, but I cant re-install the 13.3.0-37 package.

---

### Post by Thechromester420 on 2015-01-16
Update: As it turned out, DPKG needed something to be configured, but I couldn't do this from Synaptic, so this is what I'm assuming resulted in the required hard reboots. DPKG is now fixed and I am working on re-installing the 13.3.0-37 packages. (Discovery: Isn't this the Kernal?)

---

### Post by DuckHook on 2015-01-16
While using kernel 13.3.0-35 running a working OS, post results of:```
dpkg-query -l linux-headers*
``````
getconf LONG_BIT
```Case and spelling must be exact in Linux, so copy and paste into terminal instead of typing. Post back enclosing your output in [COLOR=#ff0000][noparse]```
[/noparse][/COLOR]stuff_outputted[COLOR=#ff0000][noparse]
```[/noparse][/COLOR] tags for easier reading.

**EDIT**
Looks like you fixed *dpkg* all by your lonesome.

---

### Post by Thechromester420 on 2015-01-20
I never fixed the exact 13.3.0-37 kernal, but a newer kernal updateed and DPKG configured it to boot by default
/Solved

---

