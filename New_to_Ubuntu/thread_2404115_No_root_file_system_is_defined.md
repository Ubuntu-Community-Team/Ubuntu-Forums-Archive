---
title: "No root file system is defined"
date: 2018-10-20
forum: New to Ubuntu
---

### Post by nul2 on 2018-10-20
Hi All,

I am really new to Ubuntu. I am a first time user in fact. I am trying to install Ubuntu on a HP. I am able to boot from the flash drive, but it gives me an error when I try to install. I get "no root file system is defined." I don't see the local hard drive when I try to install. I am able to see it in the terminal when I am booted into Ubuntu on the flash. Has someone come across this problem before?

---

### Post by dino99 on 2018-10-20
When you get the partitioning step, you need to define the type of partition. Nowadays, when using 'something else' choice (= manual partitionning) you only need to set 'root' partition (for the system), and '/home' (for your data & settings); swap partition is now included into 'root' as a 'file' partition. So let enough room: ~15 gb.

 [https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

---

### Post by yancek on 2018-10-20
If you don't see the hard drive when you are trying to install it could be that the drive is bad or that you have another operating system on the drive which is hibernated.  You don't make any mention of another OS??  Using the manual method (Something Else in Ubuntu) as suggested is the best option and gives you control.  The message you report is because you have not selected a Mount point for the / root) filesystem.  You need to let us know if there is another OS already installed and if so what it is and if so whether you have space (unallocated) on which to install Ubuntu.

---

### Post by nul2 on 2018-10-20
I wiped the drive of the Windows 10. All I get is the windows 10 recovery partition when I try to boot from it. It is a 1TB. I really don't care about having Windows at this point. I get a window that pop up that says: No root file system is defined.

---

### Post by nul2 on 2018-10-20
It is very strange to me. I can see the drive when I am booted into Ubuntu on the USB, but as soon as I launch the installer the drive disappears from the desktop.

---

### Post by nul2 on 2018-10-22
I answered my own question. I finally got it to install on the hard drive. It turns out that I had to format it in the disks app and change the format to ext4. There was a lot of windows stuff left on it. After formating the drive it all worked out. I guess its the growing pains of learning a new OS.

---

### Post by oldos2er on 2018-10-23
> **nul2 said:**
> It is very strange to me. I can see the drive when I am booted into Ubuntu on the USB, but as soon as I launch the installer the drive disappears from the desktop.

That's because the partition can't be mounted if you use it for your new Ubuntu installation.

Since your problem is solved, would you please mark the thread "Solved" under Thread Tools at the top of the page? Thank you.

---

