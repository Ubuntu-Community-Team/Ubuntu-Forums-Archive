---
title: "Trying to dual boot Windows 10 and Ubuntu, running into a problem"
date: 2015-10-31
forum: New to Ubuntu
---

### Post by K_P on 2015-10-31
Hello,

I am trying to dual boot Ubuntu and Windows 10, but Ubuntu has very little disk space (not enough to install gparted.) How can I take some away from Windows 10 and give it to Ubuntu, I have 200 GB free of Windows 10, and around 250 MB in Ubuntu.

EDIT:
64 bit operating system.
I'm still a beginner at this, so if  you need more info, ask.

---

### Post by Mark Phelps on 2015-10-31
K_P:  You have to run Disk Management in Win10 and shrink down the OS partition to make some room for Ubuntu.  Then, when you boot into the Ubuntu installer, use the Something Else option to create the partitions.

---

### Post by yancek on 2015-10-31
It isn't clear to me whether you are just trying to install Ubuntu or whether you already have it installed and want to decrease space for windows and increase space for Ubuntu.  As suggested above, you should use the windows Disk Management to do that.  If you have problems, you should post some partition info either by running :  sudo fdisk -l  or by running GParted from the Ubuntu install medium and posting the image here.

---

### Post by K_P on 2015-10-31
> **Mark Phelps said:**
> K_P:  You have to run Disk Management in Win10 and shrink down the OS partition to make some room for Ubuntu.  Then, when you boot into the Ubuntu installer, use the Something Else option to create the partitions.

Thanks, worked.

Now how do I get my nvidia graphics card working with Ubuntu 15.10 (I have tried the Ctrl Alt F1 method with the .run, didn't work, as it said the Nouveau driver wasn't disabled completely.)

---

### Post by grahammechanical on 2015-10-31
When you installed Ubuntu did you tick the box "install third party software?" If you did then you have a proprietary video driver already installed. You can go to System Settings>Software & Updates>Additional Drivers tab and you will see a selection of 4 proprietary video drivers and 1 open source video driver.

Or perhaps you are trying to install a driver downloaded from the Nvidia web site. You, of course, know what you are doing. We are having to guess.

---

### Post by Bucky Ball on 2015-11-01
> **K_P said:**
> Now how do I get my nvidia graphics card working with Ubuntu 15.10 (I have tried the Ctrl Alt F1 method with the .run, didn't work, as it said the Nouveau driver wasn't disabled completely.)

You mark this thread as solved and create a new one with a descriptive title and describe the issue you're having as fully as possible. Your new problem has nothing to do with the topic or title of this thread so a new one will greatly improve your chances of support.

---

