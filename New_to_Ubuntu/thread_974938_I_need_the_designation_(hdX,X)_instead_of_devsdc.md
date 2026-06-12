---
title: "I need the designation (hdX,X) instead of /dev/sdc"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by michaeljeshurun on 2008-11-08
I'm trying to install GRUB and at the GRUB prompt my instructions say to type 

[INDENT]grub>setup (XXX,X)[/INDENT] 

but the only designations I know for the drive are /dev/sdc, /dev/sdc0, and /dev/sdc1.  

From all my searching in this forum, google.com/linux, and at Ubuntu documentation, etc., the form in the parenthesis is probably only needed rarely, but I'm getting error messages when I try without it. I tried dmesg, and saw my CD as fd0, but it didn't identify the drive I need.

I realize this is probably specific to GRUB, but it must be the simplest terminal command that's excellent to learn.

Thanks in advance.

---

### Post by jolx on 2008-11-08
wow

sda1 = hd0,0
sdc2 = hd2,1

can you work it out

---

### Post by YaroMan86 on 2008-11-08
> **michaeljeshurun said:**
> I'm trying to install GRUB and at the GRUB prompt my instructions say to type 

[INDENT]grub>setup (XXX,X)[/INDENT] 

but the only designations I know for the drive are /dev/sdc, /dev/sdc0, and /dev/sdc1.  

From all my searching in this forum, google.com/linux, and at Ubuntu documentation, etc., the form in the parenthesis is probably only needed rarely, but I'm getting error messages when I try without it. I tried dmesg, and saw my CD as fd0, but it didn't identify the drive I need.

I realize this is probably specific to GRUB, but it must be the simplest terminal command that's excellent to learn.

Thanks in advance.

Go into GRUB and type:

```

find /boot/grub/stage1

```

I think that's the command.

---

### Post by michaeljeshurun on 2008-11-08
That's done thanks. 

I'd already done the:

> grub>find /boot/grub/stage1 

and that just confirmed that the USB that should be booting by now *DIDN'T* have GRUB.  The existing stage1 became my root, and jolx's detailed reply:

> sda1 = hd0,0
sdc2 = hd2,1

can you work it out
 after obviosly intense research got the setup done for me.

Thanks.

---

### Post by bumanie on 2008-11-08
Grub counts from zero and still uses the designation (hdx,x), therefore as noted above, sda = (hd0); sda1 = (hd0,0) meaning first partition on the first hard drive, thus sdb1 = (hd1,0) meaning the first partition on the second hard drive.

If you post the output of > sudo fdisk - luSomeone can help you with reinstalling grub, if the above does not make it clear.

---

