---
title: "Dual boot windows 7 and Ubuntu 12.04"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by anilmarella on 2013-01-10
I am trying to install Ubuntu on my windows system. This is the first time I am installing any Linux version. So please pardon my naivety.
I searched for steps to install and I found this 2 page tutorial.
[http://www.linuxbsdos.com/2012/10/11/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-hardware/](http://www.linuxbsdos.com/2012/10/11/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-hardware/)

I followed the exact same steps. The only difference is I couldn't create primary partition for '/boot' it is a logical partition and the other two did not ask me for logical or primary.

After the installation I couldn't see Ubuntu option on boot. It directly booted to windows, then as mentioned in the above link I added it using EasyBCD, this time I see the Ubuntu option but when I select it I see this
[IMG]http://members.iinet.net.au/~herman546/p15/fig2grub.gif[/IMG]
Please help me solve this

I also tried doing

grub> find /boot/grub/menu.lst
grub> configfile /boot/grub/menu.lst

both of them showed 
Error 15: file not found.

---

### Post by mlentink on 2013-01-10
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
and:
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

---

### Post by rrich1974 on 2013-01-10
com'on....boot into live dvd/usb and choose "install alongside windows" 
it is very simple, dont mess around with partitioning while you are a newbie.

---

### Post by gurrunaki on 2013-01-10
I just did a couple of days ago, and more or less was like they said in other post above. Just download the distro you want, make an usb bootable with unetbooting and change the bios for start the computer from the usb, there will give to you the option to install alongside from windows 7, the only thing you need to do is follow the steps from the installation like choose the size on the hard disk you want for ubuntu.
As well, in the ubuntu download page you will find all the information step by step, try it and you will see how easy is :)

---

### Post by mastablasta on 2013-01-10
ofcourse it is as simple as that if you do not have UEFI. if you have UEFI you need a boot partition i believe. for example: [http://askubuntu.com/questions/219027/how-do-i-dual-boot-windows-8-uefi-and-ubuntu-12-10](http://askubuntu.com/questions/219027/how-do-i-dual-boot-windows-8-uefi-and-ubuntu-12-10)

---

