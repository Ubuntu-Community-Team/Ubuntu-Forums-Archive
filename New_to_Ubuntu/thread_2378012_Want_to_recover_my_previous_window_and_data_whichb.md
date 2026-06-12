---
title: "Want to recover my previous window and data whichbis lost during ubuntu installation?"
date: 2017-11-19
forum: New to Ubuntu
---

### Post by muhammadahmad on 2017-11-19
, guys i am new here as well as to ubuntu... I am in big trouble..the problem i am facing is that i was installing a ubuntu from a bootable usb and meanwhile after two three setps i stuck so i decided to hard switch the laptop by long pressing the switched of button and i then try again by restatring the laptop but the same occur so i hard switch the laptop again and remove the usb without installing ubuntu...after that whenever i try to open my pc i just got black screen with a cursor blinking...i have win 8.1 already installed... Now when i decided to reinstall the windows 8.1. I just insert window cd and got an options of recovery.. I just click on it but it didnt work and i got a message which i will post below in fig 1. After that when i go further to remove the previous window partition and install the new window i was schocked by seeing that it show ne only one partition of 465gb in which 9mb was free although i was have three partition before it,one for window and other two for my personal data. I remove the cd without installing new window on it... KINDLY HELP ME IN RECOVERY OF THE PREVIOUS DATA.. Note: i have no access to previous window and i have no ubuntu installed.! [got during recover] ([https://i.stack.imgur.com/C9OYE.jpg)!*](https://i.stack.imgur.com/C9OYE.jpg)!*)

---

### Post by ian-weisser on 2017-11-19
Lesson #1: Always backup your data before installing a new Operating System.
Lesson #2: Installing a new Operating System is risky. Be prepared for problems.

If you want to recover your Windows data, STOP USING THAT HARD DRIVE immediately.

The basic procedure is this:
- Boot from a USB (Try Ubuntu).
- Mount the damaged Hard Drive - you must look up and learn how to do this.
- Copy all your data onto a different storage device. (NOT the same hard drive. NOT the same USB. Something else). You must look up and learn how to do this, too.
- Test your data on a different Windows machine to make sure you really, really have it.

It may be more complicated if you made unwise choices that have perhaps already erased some of your data. Difficult to tell from the limited information you have provided.

After you have recovered your data, then you are free to reformat your hard drive, reinstall Windows, and then restore the data from your backup.

---

### Post by yancek on 2017-11-19
You indicate in your post that you got an error when you tried to restart the computer after a failed installation attempt.  You neglected to post what that error was!!

The image you posted is nothing more than the standard screen when booting windows in recovery mode.  Not helpful at all.  Are you still able to boot the installation media of Ubuntu?  If you can do that, select the Try Ubuntu option to get to a Desktop.  Then open a terminal and run either/both of these commands and post the output so we have some information.

```
sudo fdisk -l
sudo parted -l
```

That's a Lower Case Letter L in both commands.  You might also get the boot repair software when booted into the Ubuntu install media (??) and select the option to Create BootInfo Summary and post a link to the output here.  Lots of potentially useful information with that.  Do NOT try to make any repairs.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

