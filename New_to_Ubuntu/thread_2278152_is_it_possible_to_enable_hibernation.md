---
title: "is it possible to enable hibernation"
date: 2015-05-14
forum: New to Ubuntu
---

### Post by kaitlin3 on 2015-05-14
hello im new to linux and Lubuntu im wondering is it possible to enable hibernation so that when i close the screen on my laptop it will hibernate i know windows 7 has this option but idk if ubuntu does if so how do i do this?

---

### Post by dino99 on 2015-05-14
Think to check the community wikis (click on the links below to learn more)
[https://help.ubuntu.com/community/PowerManagement/Hibernate](https://help.ubuntu.com/community/PowerManagement/Hibernate)

---

### Post by ajgreeny on 2015-05-14
I will not comment on dino99's link as I have no idea about what it is suggesting, but I can assure you that going to the forum thread shown below will give you an answer, and a way to check that hibernate will work on your hardware; it is not totally successful on all machines.
[http://ubuntuforums.org/showthread.php?t=2219403](http://ubuntuforums.org/showthread.php?t=2219403)

You must have at least as much swap space as you have ram for hibernation to work at all, but whether you have Ubuntu, Kubuntu, Xubuntu or Lubuntu they should all work the same way.  My Xubuntu 14.04 hibernates without a problem on my old netbook and a Compaq CQ70 laptop.

---

### Post by Geoffrey_Arndt on 2015-05-14
More here from Ubuntu Official documentation:

You can use the command line to test if hibernate works on your computer.


 
[LIST]
[*]Open the Terminal by pressing **Ctrl+Alt+t** or by searching for terminal         in the Dash. 
[*] Type _sudo pm-hibernate_ into the terminal and press **Enter**.

 Enter your password when prompted. 
[*] After you computer turns off, switch it back on. Did your open applications        re-open?
 [U]If hibernate doesn't work, check if your swap partition is at least as large as your        available RAM.
[/U] 
[/LIST]

---

### Post by Vladlenin5000 on 2015-05-14
Additional note:

The default for Windows is to suspend when the lid closes, not hibernate. The same default applies to Ubuntu.
In a modern fast machine hibernating as no point.

---

### Post by ajgreeny on 2015-05-14
> **Vladlenin5000 said:**
> Additional note:

The default for Windows is to suspend when the lid closes, not hibernate. The same default applies to Ubuntu.
In a modern fast machine hibernating as no point.
Unless it is a laptop with a dead battery!
Otherwise I totally agree.

---

