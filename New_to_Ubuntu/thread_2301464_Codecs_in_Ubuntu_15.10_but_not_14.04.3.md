---
title: "Codecs in Ubuntu 15.10 but not 14.04.3?"
date: 2015-11-02
forum: New to Ubuntu
---

### Post by windwalker2 on 2015-11-02
I'm new and hope this is in the right place. I am trying Ubuntu 15.10 after not having messed with Ubuntu for a while. 15.10 "just seems to work". When attempting to play an mp3 or mpeg etc if it doesn't have the codec it seems to look for, find, and ask if you want to install it. 

14.04 on the other hand seems to just stop and you have to scour the internet trying to get it to get the right repositories, then finding and installing them is a nightmare with all sorts of issues. Why is this. I would like to stay with 15.10 for it's ease of use, but fear at the end of support I will be back to square one with having to upgrade to something else and all these issues crop up once again.

 Do you think newer versions of Ubuntu will operate as easily and nicely as 15.10 seems to. It has a couple of quirks like a problem with the log off screen hanging on "Plymouth" error but other than that it is great.

Advice?

---

### Post by egeezer on 2015-11-02
If you open a terminal and type
```
sudo apt-get install ubuntu-restricted-extras
```
you will get all the codecs you need in advance.

But if you do a clean install when 16.04 comes out, check the box on the first page of the installer that offers to download the codecs during installation.

FWIW, a lot of us do clean installs each time rather than update.

---

### Post by Geoffrey_Arndt on 2015-11-02
Good advice from the geezer . . . . so . . . . as in most cases, it's not an OS issue, but rather it's just that the user is simply unaware of the procedures and options that are available.    That's why forums like this are invaluable.  

BTW, there are quite a few well written articles online that offer great tips on what to do after an install, to optimize your Ubuntu.  Note there are reasons why some or all of these modifications are not done during initial installs (but that's beyond scop of this short reply).

They're titled something like "14 key tweaks to do after installing Ubuntu" . . . . these helper articles are posted on the web shortly after any Ubuntu new release . . . for example:

[http://www.webupd8.org/2014/04/10-things-to-do-after-installing-ubuntu.html](http://www.webupd8.org/2014/04/10-things-to-do-after-installing-ubuntu.html)

---

### Post by grahammechanical on 2015-11-02
If you are curious about the next version of Ubuntu (16.04) then follow some of the sessions of the Ubuntu Online Summit. That is where future development plans for Ubuntu are openly discussed.

[http://summit.ubuntu.com/](http://summit.ubuntu.com/)

Regards

---

### Post by windwalker2 on 2015-11-02
Thanks everyone for the replies. I will check into them I have seen those but when I attempted they would give errors and I thought I was updating the repositories right but maybe not. Maybe it was because I was doing it on a USB live environment too. If someone would kindly direct me to where to get more information on if and will I be able to upgrade later after 15.10 runs out I would appreciate it, I don't think this is the right thread for me to ask questions in.

---

### Post by Geoffrey_Arndt on 2015-11-03
Live "environments" are not - repeat, not conducive to updating anything . . . . . the update process from 15.10 to 16.04 (on a normal hard drive install) is quite easy.   You'll see a button and notice in the updater window (when you do your regular updates) . . . so, you just click the button.    

The more "vanilla" your system is, the easier and error-free your upgrade is.   Plus, if you have any extra software sources enabled (for example, PPA's - personal package archives), those should be unchecked (disabled) using the package manager tools (ubuntu software center or synaptic).

---

### Post by windwalker2 on 2015-11-03
Thanks for the information I appreciate it.

---

