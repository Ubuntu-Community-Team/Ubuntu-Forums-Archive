---
title: "Dell D400: Trying to upgrade from 11.04"
date: 2014-06-24
forum: New to Ubuntu
---

### Post by lukenukem2 on 2014-06-24
Hey there, I just recently got an old D400 from a friend and I decided I wanted to finally try linux. He had an ancient live cd of xubuntu and he installed it before hegave the laptop to me. Now I'm stuck without drivers for the wireless card, and trying to either upgrade or freshly install a newer version. I looked at the EOLUpgrade page, and I'm wasn't sure if I could just follow the 11.10 upgrade link, so I tried to freshly install 12.04 (14.04 requires me to get PAE working, and I'm not quite sure how to do that.). The new live cd will boot, get past the requirements page and then give me an error pointing to "usr/lib/ubiquity/bin/ubiquity". I tried using a larger flash drive, thinking that was the problem, and that solved nothing.

I'm running low on ideas here, and I'd greatly appreciate it if someone could point me in the right direction.

Laptop specs are:

Pentium  M 1.70  GHz

Intel  855GM

30gb Hard disc

1gb RAM

Thanks.

---

### Post by DuckHook on 2014-06-25
Welcome to the forums, lukenukem2.

I'm afraid that your D400 is grossly underpowered for Ubuntu. Without knowing more CPU details (it came with a variety of possible Pentium Ms), I would recommend Lubuntu 32-bit. Your graphical chipset is especially underpowered (64 MB of *shared* system memory, primitive 3D, slower than treacle) and will just choke on Unity.

What makes you think that your CPU is non-PAE? Some Pentium Ms do not have PAE. Others actually have it, but with the PAE flag turned off (a really stupid and irritating decision on Intel's part). However, to the delight of old hardware hounds, Ubuntu has reworked their kernel in 14.04 to enable PAE in the hobbled CPUs through the use of a special boot flag. There is also a more involved procedure for CPUs truly missing PAE support to install a non-PAE kernel and then proceed with a complete install. Details for both procedures are [here]("https://help.ubuntu.com/community/Lubuntu-fake-PAE").

I highly recommend a fresh install of 14.04. Upgrading from 11.04 is fraught with dragons, poison snakes and booby-traps.

---

### Post by lukenukem2 on 2014-06-25
Ah, I was just going with Xubuntu because it was supposed to be easier on old hardware, if Lubunutu is lighter, I'll give that a try. The only thing I know about the PAE is that 14.04 wouldn't boot off a live disc due to an issue with PAE. Sorry, I was dumb and didn't jot down the exact message.

Is there a speccy- or dxdiag-like program or function I could use to get some more detailed hardware info?

---

### Post by DuckHook on 2014-06-25
Xubuntu is pretty lightweight but not as lightweight as Lubuntu. Lubuntu was designed to run on the most underpowered HW, and your laptop qualifies as such.

You must follow the instructions in the link I provided to boot the LiveDVD. This requires you to hit <F6> during the install process and enter the option:```
forcepae
```after the "--" on the boot line.

The four ways I know to get HW info is to either:
1. successfully load Linux and use the tools therein,
2. read it off the manuals or the Dell website,
3. use Windows tools while Windows is still installed in the machine, or
4. physically disassemble the box to read the part numbers and then Google them.

However, further checking may not be necessary. You report your Pentium M to be 1.70 GHz which makes it a PAE-capable CPU but with the PAE flag turned off (the only truly PAE-missing processor was 1.2 GHz). Older versions of the kernel only queried this flag without conducting any further tests and refused to load if the flag was off. However, in 14.04, apparently the kernel will bypass this check if the *forcepae* option is added to the boot parameters (I haven't upgraded my old laptops to 14.04 yet so haven't tried this myself).

I am reasonably sure that your CPU is PAE-capable, but can't give you any guarantees. I would suggest that you follow the instructions in the link provided earlier and let us know how it goes.

---

### Post by mörgæs on 2014-06-25
Small addition: Lubuntu 14.04 fits to a CD. DVD is not necessary.

---

### Post by lukenukem2 on 2014-06-26
Got Lubuntu 14.04 running fine now, thanks for the help.

---

### Post by Hadaka on 2014-06-26
Hi, the attached is on a dell1300
runs great,no lag time and does what i want.
I do have a fiber optic connection so ...that helps
It's pretty much the same machine you have there.
[ATTACH=CONFIG]254270[/ATTACH]
if you are satisfied with your results
please mark your thread solved
How to-> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Tar_Ni on 2014-06-26
> **lukenukem2 said:**
> Got Lubuntu 14.04 running fine now, thanks for the help.

Last time I tried it, Lubuntu 14.04 had some bugs. No wifi or LAN icon, no volume icon, couldn't type anything in Chromium ect. It was pretty unusable for me.

Nice to hear that it works for you though. From my personal experience with Lubuntu 14.04 I dont recommend it to beginners. Xubuntu uses XFCE, a very stable desktop environment and free of these bugs. With 1GB of RAM one should be able run Xubuntu without any problem. I did so on xubuntu 13.10 with an aging desktop computer.

---

### Post by claracc on 2014-06-27
> **lukenukem2 said:**
> Got Lubuntu 14.04 running fine now, thanks for the help.

Please, mark the thread as solved with thread tools in the right upper part of the webpage.

Tnaks.

---

### Post by mörgæs on 2014-06-27
> **Tar_Ni said:**
> Last time I tried it, Lubuntu 14.04 had some bugs. No wifi or LAN icon, no volume icon, couldn't type anything in Chromium ect. It was pretty unusable for me.


The only of these bugs that I have seen is the missing network icon and it has an easy [solution]("http://ubuntuforums.org/showthread.php?t=2130640&p=12565189&viewfull=1#post12565189").

---

