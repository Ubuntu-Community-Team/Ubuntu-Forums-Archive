---
title: "error installing"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by coffee708 on 2013-03-10
hey so i got this error trying to install ubuntu 

[http://imageshack.us/photo/my-images/11/39355071.png/](http://imageshack.us/photo/my-images/11/39355071.png/) 

any ideas?

---

### Post by lisati on 2013-03-10
*Thread moved to **Absolute Beginners Section**.*

---

### Post by ViliX64 on 2013-03-10
Don't install it from Windows, it will just mess things up. Boot linux from DVD/Flash Drive/HDD.
Here is link for creating bootable USB:
[http://www.instructables.com/id/How-to-make-your-own-Ubuntu-LiveUSB/](http://www.instructables.com/id/How-to-make-your-own-Ubuntu-LiveUSB/)

---

### Post by 3rdalbum on 2013-03-10
I'm not familiar with Wubi (the Windows installer for Ubuntu) so I don't know if there's a reason you're getting that error message. It looks like a bug, actually. Sorry, I don't know more about the error message you've been getting.

Generally, I recommend not using the Wubi installer as there are several limitations:

1. Limited size of the Ubuntu installation
2. Some slowdown in operation
3. It's a less-tested way of installing Ubuntu
4. If you want to remove Windows entirely, you need to use a complicated process to transfer the Ubuntu onto a real partition
5. If Windows stops working and won't boot, then you won't be able to get into Ubuntu either.

I recommend you burn the Ubuntu ISO to CD and then boot your computer from the CD. Select the "Try Ubuntu" option and then double-click the installer icon, or just select the "Install Ubuntu" option from the menu. Follow the prompts and install Ubuntu to a partition - you won't lose any data or Windows if you tell it to install side-by-side with Windows.

---

### Post by bcbc on 2013-03-10
> **coffee708 said:**
> hey so i got this error trying to install ubuntu 

[http://imageshack.us/photo/my-images/11/39355071.png/](http://imageshack.us/photo/my-images/11/39355071.png/) 

any ideas?

Please post the log file or pastebin it. You can find it in the %TEMP% folder called wubi-12.10-rev273.log. Thanks

It's possible that the diskimage download was interrupted but no way to tell without the contents of the log.

---

