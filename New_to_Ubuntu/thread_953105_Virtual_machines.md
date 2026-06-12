---
title: "Virtual machines"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by jj3502 on 2008-10-19
Hi all,

i use ubuntu 8.04 and need a VM to run video games and general software in win xp

what one shod i use?:confused:

---

### Post by M4rotku on 2008-10-19
I would suggest Virtual Box.  You can get it from their website at:

[http://www.virtualbox.org/]("http://www.virtualbox.org/")

Be sure to get the regular version instead of the open source version, it is much better and works with more things.

---

### Post by jj3502 on 2008-10-19
i heard that Virtual Box has its own "Virtual" graphics card that has no direct x support (is this true).

---

### Post by DGortze380 on 2008-10-19
> **jj3502 said:**
> i heard that Virtual Box has its own "Virtual" graphics card that has no direct x support (is this true).

You will not get any 3D support in a virtual machine. VMWare Fusion has beta support, but it's flaky at best. If you want to run games, dual boot.

---

### Post by chavon20 on 2008-10-19
Sorry to but in.  If I were to run MS Office 2003 in Virtual Box, would I be able to run updates?

---

### Post by jj3502 on 2008-10-19
> **DGortze380 said:**
>  If you want to run games, dual boot.

im my compuer i have a 160gb hdd and a 40gb hdd can i install windows to the 40gb one and dual boot?

---

### Post by DGortze380 on 2008-10-19
> **jj3502 said:**
> im my compuer i have a 160gb hdd and a 40gb hdd can i install windows to the 40gb one and dual boot?

Yes you should be able to.

---

### Post by jj3502 on 2008-10-19
umm... how do i dual boot????

---

### Post by DGortze380 on 2008-10-19
> **chavon20 said:**
> Sorry to but in.  If I were to run MS Office 2003 in Virtual Box, would I be able to run updates?

Please start a separate thread for all questions. This will help ensure everyone has a chance to get their questions answered and make the answer easier to search for future reference.

You can't just 'run a program in Virtual Box'. You would install Windows as a Virtual Machine using Virtual Box, then install MS Office in your Windows Virtual Machine. Yes, updates would work.

---

### Post by DGortze380 on 2008-10-19
> **jj3502 said:**
> umm... how do i dual boot????

Back up you files. Use the live cd to run gparted and delete any information on the second hard drive. format it to fat32. Use the windows install cd to format to ntfs and install. you'll then need to adjust the settings in grub to make everything boot as needed. Search please, there are a million threads and tutorials about dual booting.  It's typically easiest to install Windows first, then Ubuntu to avoid messing with grub.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[http://ubuntuforums.org/archive/index.php/t-333816.html](http://ubuntuforums.org/archive/index.php/t-333816.html)

---

