---
title: "Changing login screen resolution"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by saratchandra on 2008-06-26
Hello, how do I change my login resolution? It is too high for my liking.

---

### Post by bmac on 2008-06-26
Open file: file system/etc/X11/xorg.conf
Change: Section "Screen"/Virtual - From the existing resolution setting to the desired mode.
Save and close file. Then reboot....


Hope this helps....

---

### Post by philinux on 2008-06-26
In Hardy there is no resolution setting in xorg any more. If the OP is using gutsy then yes.

Install and run startupmanager. Choose your resolution once you've run it. It will need your password to run.

---

### Post by bmac on 2008-06-26
[philinux]("http://ubuntuforums.org/member.php?u=353083")

Appreciate the heads up. I recall performing the X11 procedure when first installing Hardy and haven't bother to keep abreast of any changes regarding that function, as my login res hasn't changed....

---

### Post by skribbulz on 2008-08-20
Sadly this didnt work for me...I have mine set on the startupmanager to 1024x768 and it's still way too big. I tried everything and still no results. Anyone have any suggestions????

---

### Post by unca.paka on 2008-08-21
Do you have the proper drivers installed for your video card? I had the same problem till I realized I was using an old version of the nvidia drivers.

---

