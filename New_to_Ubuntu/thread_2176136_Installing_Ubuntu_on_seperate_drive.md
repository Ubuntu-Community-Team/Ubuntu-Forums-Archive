---
title: "Installing Ubuntu on seperate drive"
date: 2013-09-23
forum: New to Ubuntu
---

### Post by malcolm3 on 2013-09-23
I've got a 120 gb SSD coming and I want to install Ubuntu on it. Thing is I want to dual boot it with windows 7, which runs on my HDD. How would I dual boot operating systems on two separate drives? I want the system to prompt me on what drive to boot from.

---

### Post by Cbjaxx on 2013-09-23
Try this link...[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot"). It might appear daunting at first read, but with 7 already installed you are half the way there. If you read over the page and still have trouble let us know. I am using the 7 dual boot myself currently, although I have not logged into 7 in a while now. Good Luck!! If you get stuck on that page post back with where in the process and I am sure folks will be willing to answer questions.

---

### Post by malcolm3 on 2013-09-23
This teaches me how to dual boot even though windows 7 and ubuntu are on two seperate drives?

---

### Post by Cbjaxx on 2013-09-23
Here is an older post for 12.10 which is similar to your installation [http://askubuntu.com/questions/162588/how-do-i-install-ubuntu-and-windows-on-separate-hard-drives]("http://askubuntu.com/questions/162588/how-do-i-install-ubuntu-and-windows-on-separate-hard-drives"). You could start with step 2... you might question boot order and why...this post might help with that..[http://askubuntu.com/questions/184210/question-about-changing-the-boot-orderadvice-before-installing-ubuntu]("http://askubuntu.com/questions/184210/question-about-changing-the-boot-orderadvice-before-installing-ubuntu")

---

### Post by mastablasta on 2013-09-23
the easiest way = unplug the old drive, install ubuntu on new drive, plug in the old drive and run the update grub command or use the boot repair tool to update grub and BOOM you have dualboot.

---

### Post by 3rdalbum on 2013-09-23
You are overthinking this a bit.

Plug in the SSD, boot the Ubuntu CD and run the installer. When it asks you where you want to install Ubuntu, choose the "Erase disk and install Ubuntu" option, taking care that this is the SSD and not the hard disk. It's probably the second option in thr list. It will automatically create the boot menu for you.

If you don't get the choice of operating system when you reboot, try changing the BIOS to boot from the SSD instead of the hard disk. If that doesn't work, do a Google search for Boot Repair for Ubuntu and use that.

Philosophically: A second drive is but a partition stored elsewhere.

---

### Post by cmcanulty on 2013-09-23
I did it this week and had to do one additional step. the windows wouldn't boot but I put in the windows install DVD and clicked repair and now can easily boot to either

---

### Post by malcolm3 on 2013-09-23
Thanks for the input guys! My SSD comes in today so i'll make sure to try this

---

### Post by KamiKazeNH on 2013-09-23
Hi.

I've put secondary SATA drive in my home pc, but DON'T unplug windows drive one.

Only select "Something Else" in Install Options (as in [http://askubuntu.com/questions/162588/how-do-i-install-ubuntu-and-windows-on-separate-hard-drives](http://askubuntu.com/questions/162588/how-do-i-install-ubuntu-and-windows-on-separate-hard-drives) ), then grub recognizes Windows.

Change boot order in bios to boot from secondary drive, and works fine to me.

---

