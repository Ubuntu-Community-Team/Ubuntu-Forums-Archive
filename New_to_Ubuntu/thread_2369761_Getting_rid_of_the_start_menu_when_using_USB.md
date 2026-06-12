---
title: "Getting rid of the start menu when using USB"
date: 2017-08-26
forum: New to Ubuntu
---

### Post by e1ndh on 2017-08-26
When I boot Ubuntu from USB the first thing I see is a menu asking if I want to: try Ubuntu without installing, or install Ubuntu on the system. Is there a way to make it not ask me this every time I boot from the USB and once I have selected the USB as the boot device just have it load Ubuntu as if it was the installed operating system?

Many thanks

---

### Post by Futant on 2017-08-26
You can install the full operating system on the USB - [this]("https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator?noredirect=1&lq=1") and [this]("https://askubuntu.com/questions/397481/how-to-make-a-persistent-live-ubuntu-usb-with-more-than-4gb/853839#853839") might be helpful. As it is you're running the live session - its whole purpose is to ask you that question :P

---

### Post by C.S.Cameron on 2017-08-27
Go to the root folder of your Live USB
Enter the syslinux directory, (or for UNetbootin the root directory).
Make the syslinux.cfg file writeable
Replace the contents of the file syslinux.cfg with:

```
    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

Shutdown, remove CD, reboot.

First time booting go to users and groups and create an account with yourself up as an Administrator, with password if desired.

---

