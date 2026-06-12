---
title: "Dual boot with windows 10"
date: 2017-05-24
forum: New to Ubuntu
---

### Post by hamed53735 on 2017-05-24
I had windows 10 on my desktop. I decided to add ubuntu 16.04 on it. After installing with DVD, I noticed that it doesn't boot with ubuntu and goes directly to windows. There was on option on boot menu or BIOS to boot from ubuntu. Then I followed a page to use boot-repair when booting from the DVD on "try ubuntu". I used the recommended repair, and after restarting, I noticed that windows does not boot either and I have the black grub rescue page. The ls on grub rescue shows (hd0), (hd0,msdos1), (hd0,msdos2) and (hd0,msdos3). ls (hd0,X) with X=1,2,3 returns file system is unknown. Then I tried advanced options on the boot-repair again with booting from DVD. No luck. The screen that I get after running the last recommended command by boot-repair together with the output of "sudo fdisk -l" is pasted in
[https://paste2.org/Pg6YIj6w](https://paste2.org/Pg6YIj6w)


It seems that the sda4 has ubuntu and sda1 has windows and non of them work. Any help out there?

---

### Post by yancek on 2017-05-24
You should run boot repair and select the option to Create BootInfo Summary.  This will not make any changes but will do a detailed search of your drives and when it finishes, it will give you a link to post here and that will show all the necessary information.

If you had windows 10 installed and it was pre-installed, it was almost certainly installed UEFI.  You can install Ubuntu UEFI or the older MBR method.  If you mix the two, you get the problem you have.  Posting the boot repair link should show if that is the case or any other problem you might have.  The link below explains dual booting windows 10 and Ubuntu UEFI.  You might check that to see if it is what you did.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by hamed53735 on 2017-05-24
Ok, then how can I uninstall the current ubuntu 16.04 and rescue my windows 10?

---

### Post by RobGoss on 2017-05-24
Hello and welcome to the forum, if you are trying to remove Ubuntu you can do this using Windows disk management tool, keep in mind once this is done you will have to restore the Windows boot loader in order for your machine to boot correctly.

---

### Post by christianc123 on 2017-06-16
[B][U]Partitioning your Windows 10 disk drive
[/U][/B]Before installing Ubuntu, you need to partition the Windows 10 disk drive. There are two scenarios at this point, but first heck to see if you have a single partition dedicated to Windows 10 or multiple ones. In the first scenario you have a single partition that you need to shrink, but make sure you have enough free space to do that.In the second scenario, you have two or multiple partitions, and you need to decide which one to erase for your new Ubuntu OS. In both cases, right-click on the Windows Start Menu, and choose the "Disk Management" entry from the context menu. In the first scenario, right-click on the (C:) drive and select the "Shrink Volume" option.
Set the size of the new partition for Ubuntu, which depends on how big the disk drive is and how much free space is available

_**Getting Ubuntu and installing it**_

The latest Ubuntu release is available for download from the [ubuntu.com]("http://www.ubuntu.com/download/") website.Once the USB installation is complete, insert the USB stick with Ubuntu on a free USB port on your computer, reboot the system, and immediately access the built-in boot menu to choose the USB drive and boot from it. Do not select UEFI USB (it won't recognize Windows 10)! - read the update below for details. Once you do that, you need to follow the instructions provided by us on [how to install the latest Ubuntu Linux OS]("http://news.softpedia.com/news/installing-ubuntu-15-10-495215.shtml").
The only difference will be that when you arrive the screen where you have to choose where you want to install Ubuntu, you need to select the first option, "Install Ubuntu alongside Windows 10." Once the installation is complete, restart the computer. Choose between Ubuntu and Windows 10 via Ubuntu's bootloader (accessible with the Esc key).

Regards,
Christian
[https://www.clouddesktoponline.com/](https://www.clouddesktoponline.com/)

---

