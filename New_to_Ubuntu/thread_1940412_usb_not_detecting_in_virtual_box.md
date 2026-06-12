---
title: "usb not detecting in virtual box"
date: 2012-03-13
forum: New to Ubuntu
---

### Post by maheshtatva on 2012-03-13
my usb is not detecting in virtual box while running windows7. any suggestion

---

### Post by maheshtatva on 2012-03-13
the version is 4.1.8 r75467

---

### Post by QIII on 2012-03-13
Did you install from the repositories or from virtualbox.org?  Did you install the extension pack?  Did you add yourself to the user group vboxusers?

See [https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

---

### Post by maheshtatva on 2012-03-13
installed from virtualbox.org,i didn't installed any extention package,  i didn't join the vbox user group

---

### Post by Ms. Daisy on 2012-03-13
> **maheshtatva said:**
> installed from virtualbox.org,i didn't installed any extention package,  i didn't join the vbox user group
Well you'll have to do that.  

[Configuring USB]("https://www.virtualbox.org/manual/ch03.html#idp11182912")

[Installing Guest Additions]("https://www.virtualbox.org/manual/ch04.html")

[Add yourself to the user group]("https://www.virtualbox.org/manual/ch02.html#idp5655936")

---

### Post by maheshtatva on 2012-03-13
ubuntu 11.10 cannot find the manage group in user account

---

### Post by QIII on 2012-03-13
It would be worthwhile to install the extension pack just in case.

You can follow the instructions on the web page Ms Daisy referred to and add yourself to vboxusers via the command line.

---

### Post by Ms. Daisy on 2012-03-13
> **maheshtatva said:**
> ubuntu 11.10 cannot find the manage group in user account
You add yourself to the user group in the guest, which would be in Windows 7.

---

### Post by maheshtatva on 2012-03-15
thanks guys for your participation,usb is now working in guest OS

---

