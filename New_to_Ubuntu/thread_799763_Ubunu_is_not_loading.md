---
title: "Ubunu is not loading"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by sholasys on 2008-05-19
I dual boot ubuntu and xp. Win xp was first install and later ubuntu.  The two duo are working fine and i can load any of the OS as i chooses. I install sm stuff in ubuntu and then discovered that i can load XP again. I try to reload Xp on its partition and now ubuntu is not loading again. it is not even giving me option to load any OS. Help pls

---

### Post by Gone fishing on 2008-05-19
Boot from the live CD then open a terminal and type:

    sudo grub

    > root (hd0,0)

    > setup (hd0)

    > exit

This is assuming your ubuntu partition is at hd0,0 the first hard drive and the first partition on that drive, If not, then adjust accordingly. 

This isn't quit how I do it I put grub on my Linux partition (hd0,0) (in this case) (> setup (hd0,0)) and then use the GAG boot loader gag.sourceforge.net

If you not sure how grub names disks have a look at:

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by jpoRS on 2008-05-19
Are you having trouble with selecting Ubuntu instead of XP, or once you select Ubuntu nothing happens, or am I completely misunderstanding you?

jim

---

### Post by ajgreeny on 2008-05-19
I think you mean that you have lost the grub menu that used to appeat and allow you to chose either Windows XP or Ubuntu.

If I'm correct follow the info given below:-

Boot into the ubuntu live CD
open a terminal and run :
    ```
sudo grub
```
This gets you to a simple grub command line.
Then:
   ```
 find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```
[like : root (hdo,1) ,probably]
then:
    ```
setup (hd0)
```
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working grub bootloader.

---

### Post by sholasys on 2008-05-19
Ajgreeny,
Thanks so much. i followed your steps and codes , it works fine.
perfectly.

---

