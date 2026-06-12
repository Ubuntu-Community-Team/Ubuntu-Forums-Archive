---
title: "error installing ubunto 8.04"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by karan_sharma01 on 2008-08-10
hello all
my system config. is

intel p4,
2.00 ghz ,
512 mb ram
80 gb hd
sony dvd-wr 

i am very much new to the world of linux n this is the first time iam installing linux ubunto8.04...
after loading kernls and scroll bar screen it shows somthng like 

[164,565526] buffer I/O ERROR ON DEVICE FDO, LOGICAL BLOCK 0
[202,671278] buffer I/O ERROR ON DEVICE FDO, LOGICAL BLOCK 0
[176,692707] buffer I/O ERROR ON DEVICE FDO, LOGICAL BLOCK 0
[240,721556] buffer I/O ERROR ON DEVICE FDO, LOGICAL BLOCK 0 

i've desbled my floopy drv.....and my frnd has installed ubunto with this cd on his pc..

please help

---

### Post by karan_sharma01 on 2008-08-10
please help sumbdy

---

### Post by Ryadt on 2008-08-10
Try re-enabling your floppy drive and then retry the installation.

---

### Post by karan_sharma01 on 2008-08-10
still d same problem....:(

---

### Post by karan_sharma01 on 2008-08-10
i've set drive A to none in BIOS. its not showing "buffer I/O error..."
but now m getting the black screen with sumthing like
Busybox v1.1.3(debian 1:1.1.3-5ubuntu12)Build in shell(ash)
Enter 'help ' for a list of build-in command


please help

---

### Post by Daveski on 2008-08-31
Try this:

Press **F6** at the boot up screen.
You should see a line ending with *"--quiet splash."*
Delete --quiet splash, add the option **noapic** after **ro** so you have **ro noapic**

Hit enter to boot.

If this does not work, try **all_generic_ide** instead of **noapic**

---

