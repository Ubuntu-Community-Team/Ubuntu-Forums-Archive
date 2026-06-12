---
title: "Problems with 8.10 Installation"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by manuleka on 2008-12-02
I'm trying to install Ubuntu 8.10 on my PC and it keeps freezing on me... 

here's my machine spec:

CPU: AMD Athlon64 2000+ 754 (@2.0GHz)
RAM: 2.5GB (1GBx2+512MB)
M/B: Winfast NF4K8AB
VGA: Radeon X600 XT 256MB DDR PCI-e 16x 
HDD: 150GB

it freezes on different locations during installation process although i suspect it has something todo with my video card...

I have tried installing Ubuntu 8.04 and 7.10 with no luck :(

can anyone help me? cheers

---

### Post by Dj Melik on 2008-12-02
Are you installing the i386 or x64 version?

---

### Post by manuleka on 2008-12-02
Ubuntu 8.10 32bit, and i'm doing a fresh installation

---

### Post by dwasifar on 2008-12-02
If you think it's a video card issue, try installing from the[ alternate install CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") instead.  Text-based installer.  Should get you past any such issues.

---

### Post by maheshjr2000 on 2008-12-02
did you check the integrity of the installation disk?(I think thats what its called).

---

### Post by manuleka on 2008-12-02
> **maheshjr2000 said:**
> did you check the integrity of the installation disk?(I think thats what its called).

yeah... i did check, it's a requested CD from canonical (FREE)

i will try the text based installation and post!

---

### Post by dwasifar on 2008-12-02
I'll be interested to see how it goes.  In my experience the text-based installer usually works when the Live CD installer fails.

---

### Post by nhasian on 2008-12-02
> **dwasifar said:**
> I'll be interested to see how it goes.  In my experience the text-based installer usually works when the Live CD installer fails.

that may be true but what concerns me is:

[QUOTE=manuleka] it freezes on different locations during installation process[/QUOTE]

which leads me to believe its some kind of hardware problem.

---

### Post by prshah on 2008-12-02
> **manuleka said:**
> 
it freezes on different locations during installation process although i suspect it has something todo with my video card...


When it freezes, try switching to a diagnostic console, usually either Ctrl+Alt+F8 or Ctrl+Alt+F1. If it switches, then post back the last messages on the screen, or any messages that look suspicious / problematic.

If you can't switch to the diagnostic console (hard freeze), press Ctl+Alt+SysRq+R (Regain keyboard control) and try again.

Post back your results in any case.

---

### Post by manuleka on 2008-12-02
> **dwasifar said:**
> I'll be interested to see how it goes.  In my experience the text-based installer usually works when the Live CD installer fails.

how do i get to text-based installer on the Ubuntu 8.10 installer? is it under F6 other options?

---

### Post by dwasifar on 2008-12-02
It's a different CD.  Download it from the link in my earlier post, burn, and boot from it.  You will get the familiar Ubuntu-logo black menu screen, but the options will be different.  The first option in the list will be installation.

I've seen situations where the installer breaks the hardware support on the live CD, but if the system is installed from the alternate CD, the resulting installation is just fine.

---

### Post by manuleka on 2008-12-02
installation with alternate seems to work... i&#7743; running ubuntu 8.10 now :) i´ve been using it now for about 5 or so hours and it crashed 3 times... when i restarted it it comes up with driver loading errors and frozen reports with lines like
=========================================
[146.176xxx] ata1.01: status: {DRDY}
Exeption... Frozen... Timeout... etc etc
=========================================
I did enable Restricted Drivers for ATI (ATI CATALYST) so i can run special appearance effects and stuff... 

i´m trying to run updates but got another error
=========================================
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
=========================================
I&#7743; quite new to Ubuntu so i have no idea what to do next... i&#7743; hoping updates would help fix the issues or at least lessen the crashes :(

---

### Post by dwasifar on 2008-12-05
Open a terminal: Applications>Accessories>Terminal

In the terminal window, type:```
sudo dpkg --configure -a
```

Enter your system password when prompted.

See if that clears it up, and report back.

---

### Post by manuleka on 2008-12-06
done that... doesn't seem to fix the freezing... it runs fine but then after an hour or so it just freezes... i do a cold restart and same thing happens :( i'm going to give up... maybe get another video card! 

I tried disabling the ATI driver and it still freezes...

Update - did a full reinstallation with 8.04.1 alternate and same thing happens :( this sux... 

I'm thinking of just running Ubuntu from Windows...

---

### Post by dwasifar on 2008-12-06
That certainly is sounding like a hardware problem.

Can you borrow a video card from someone to test your hypothesis?

---

