---
title: "How to make a bootable usb with memtest86 on it?"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by disappearedng on 2008-06-30
Hi everyone.
I am interested in knowing the steps to make a usb bootable disk with memtest86 on it. I have read a few tutorials online and I am kind of very overwhelmed with the installation process. Can anyone please tell me how i could do it?

---

### Post by hyper_ch on 2008-06-30
you know how to make a usb pendrive bootable?

---

### Post by bumanie on 2008-06-30
Use [this]("http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/") or one of the links down the bottom of the page.

---

### Post by disappearedng on 2008-06-30
# Type cp -rfv casper dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines install/mt86plus /media/ubuntu8
# Type cd /media/ubuntu8
# Type wget pendrivelinux.com/downloads/u8/syslinux.cfg
# Type cd casper
# Type rm initrd.gz
# Type wget pendrivelinux.com/downloads/u8/initrd.gz
# Reboot your computer and set your system BIOS boot priority to boot from the USB stick.

From the top onwards I am completely lost.

---

### Post by bumanie on 2008-06-30
Just follow the steps, in order as prescribed, ensuring that you are installing to the correct device. This will cause your usb to be formatted and allow booting of ubuntu OS. The instructions are overwhelming if you are new to linux, but they work if followed carefully and as said, being installed onto the correct device. If you don't know the device name, plug it in to the computer and then in terminal > sudo fdisk -l (lower case L) and someone will try and help identify the correct device name to use. I have used that tutorial on both an external hard drive and usbpendrive with 8.04 and it worked on both occassions. Alternatively, look at one of the links down the bottom of the page - unfortunately, the instructions will vary little. May be you should get a little bit more linux experience and then try in a month or two. If you want memtest only, without an OS, try [here]("http://www.memtest.org/#downiso")

---

