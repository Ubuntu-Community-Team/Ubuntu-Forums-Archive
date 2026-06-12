---
title: "Error on booting."
date: 2013-07-01
forum: New to Ubuntu
---

### Post by AADAS on 2013-07-01
When I try to boot ubuntu with dual boot (win 7 and ubuntu 13.04) the following line appears :
error: premature end of file /boot/vmlinuz-3.8.9-19-generic
error: you need to load the kernel first.

---

### Post by dino99 on 2013-07-01
check that you have all the 3.8.9-19 packages installed : 2 headers + 2 images ; and build-essential too

it should be fine if the generic meta package is installed : linux-image

---

### Post by AADAS on 2013-07-01
And how to do this?

---

### Post by Impavidus on 2013-07-01
Can you boot an older kernel version? From the grub menu you should be able to select an older kernel (unless you uninstalled it). Boot that and then reinstall the 3.8.9-19 packages.

---

### Post by AADAS on 2013-07-02
No.I cant.And this is a fresh install of ubuntu 13.04 never booted.

---

### Post by su:bhatta on 2013-07-02
Then u might hav to re-install ubuntu again... 
get a fresh download of the iso...just in case there is something wrong with the iso u hav...

---

### Post by Impavidus on 2013-07-02
If it's a new install you have nothing to lose. Check the integrity of the live disk, if it's damaged download it again an try again.

---

