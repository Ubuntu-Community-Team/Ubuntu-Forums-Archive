---
title: "multiple boot and boot folder"
date: 2017-04-08
forum: New to Ubuntu
---

### Post by ulinuxuser on 2017-04-08
Dear Ubuntu users,

I would like to install Ubuntu-16.04.2 . As I have read in the past a hdd can be "separated" into 4 primary partitions. 

So I decided to create a section for a boot folder an other for Linux Mint and a third one (extended) for swap. 

Now I would like to add Ubuntu so I am going to create a fourth one. 

My questions are how will I be able to boot Ubuntu? Will I have an option/menu to choose from which System I want to boot and will the boot folder have a negative effect to the process of booting the desired OS?

I have attached a layout of the disk partitions.

Thank you for your time.

---

### Post by SeijiSensei on 2017-04-08
You'll be using the rest of the extended partition for Ubuntu, I take it?

Yes, you will have a menu of available operating systems at boot. And having a separate boot partition can work well in these multi-OS arrangements.

However I'm a bit concerned that the boot partition is only 239 MB.  It's not very full now, but once you install Ubuntu you may need to pay attention to its usage.  On my 14.04 machine, /boot is 110 MB in size.  If you upgrade the operating system kernel, it will need to install a new kernel before deleting stale ones.  (By default, Ubuntu keeps two kernel versions in /boot, the current one and the previous one. That's to protect against cases where the new kernel is somehow incompatible with your hardware or installation.)  Running the command "sudo apt-get autoremove" from time to time in a terminal window can help manage the number of kernel images.  If you install or upgrade packages from the terminal rather than a GUI software manager, you'll get prompted to run autoremove when needed.

---

### Post by ulinuxuser on 2017-04-08
Dear SeijiSensei,

Thank you for your swift reply. 

Yes I am considering to use the rest space for Ubuntu. 

Thank you for the advice on autoremove command.

---

### Post by oldfred on 2017-04-08
You already have swap inside an extended partition. 
Just expand the extended partition to include all of the unallocated and you can create an unlimited number of logical partitions.

Generally with most installs it is better not to use /boot as a separate partition. But you can. One more partition to manage and make sure its not full. Still should houseclean old kernels.
If using LVM or some other installs /boot as a partition may be required.
You should not share a /boot as you may get conflicts. You can share a swap as long as you do not hibernate nor encrypt.

       One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by ulinuxuser on 2017-04-08
Dear oldfred,

Thank you for your reply and for the useful information provided in your links. 

Initially I chose dev/sda1 under the "Device for boot loader installation" and after installation it would only load Linux Mint. Then I saw your message, reinstalled Ubuntu - this time using the option /dev/sda (Name of hdd) -  and as you advised me I expanded the extended partition. 

Now the menu works beautifully and I can choose between OS.

Thank you for your help.

---

