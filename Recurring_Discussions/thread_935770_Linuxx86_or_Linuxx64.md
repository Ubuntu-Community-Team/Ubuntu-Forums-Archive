---
title: "Linux/x86 or Linux/x64"
date: 2008-10-02
forum: Recurring Discussions
---

### Post by Nuu on 2008-10-02
As I type this, I am running Ubuntu on an AMD Turion 64 X2 Dell Vostro 1000 laptop. Now, I wanted to download BOINC for this computer, and it comes in Linux/x86 and Linux/x64 versions. Now I'm thinking, 'obviously, I should get the x64 version, because I have a 64-bit microprocessor.' But then again, when I requested my free CD from Ubuntu, I thought I would be running it on a Pentium microprocessor. And yet, whatever I got, it seems to work fine on this. Do the free CDs determine cater for both versions, or is there something about Ubuntu which just works either way? Or did I select x64 somehow? Or am I just confusing myself and the whole x64\x86 thing has nothing to do with microprocessors?

In a nutshell, do I download the x86 version or the x64 version?

---

### Post by MindFlayer on 2008-10-02
Type "uname -m" in the terminal and look at the output. If you can see "x86_64", then you have the 64-bit version of Ubuntu installed and you should install the x64 version. If it's "i686", then you've got a 32-bit Ubuntu and need to install x86 which too is 32-bit.

---

### Post by felker2 on 2008-10-02
> **Nuu said:**
> Do the free CDs determine cater for both versions, or is there something about Ubuntu which just works either way? Or did I select x64 somehow?

It would be very nice if there were only one CD that would take care of x86 versus x86-64, and Ubuntu versus Kubuntu versus Xubuntu, and Desktop versus Server.

However, that is not the case: there are different CDs for each choice.

During the shipit order, you were offered the choice:

[INDENT]I would like:  	
Ubuntu 8.04 LTS Desktop Edition
Ubuntu 8.04 LTS Desktop Edition (64-bit)[/INDENT]


You have choosen one version. Maybe you can see the version on the CD. If not, type "uname -a" on a running instance and check the version: x86 or x86_64.

HTH

---

### Post by Nuu on 2008-10-02
Right, so I have i686, but if I may ask a follow-up question: would I be better off if I got the x64 version now or not? What difference would it make?

---

### Post by Sef on 2008-10-02
> Right, so I have i686, but if I may ask a follow-up question: would I be better off if I got the x64 version now or not? What difference would it make?
Unless you were doing movie editing, heavy gaming, or constantly downloading 600 pictures at a time, not a lot of difference to be seen.

---

### Post by t4thfavor on 2008-10-03
I actually notice the speed increase while doing general computing tasks such as running OpenOffice, or browsing with FireFox. The 64 bit isn't just for devs, gamers, and movie editors. I almost challenge you to find a game that is natively 64 bit. Most are still being compiled for 32 bit Windows XP.

Plus you can have more MEMORY, and we all know more of that is always better.

---

### Post by jespdj on 2008-10-03
> **Nuu said:**
> Right, so I have i686, but if I may ask a follow-up question: would I be better off if I got the x64 version now or not? What difference would it make?
Please [read the sticky](http://ubuntuforums.org/showthread.php?t=765428). The differences, advantages and disadvantages of 64-bit vs. 32-bit have been discussed here many, many times already.

---

### Post by Rocket2DMn on 2008-10-03
Moved to Recurring Discussions.

---

