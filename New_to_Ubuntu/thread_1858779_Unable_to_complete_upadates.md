---
title: "Unable to complete upadates"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by Saqib Amin on 2011-10-13
Hi
I am using Ubuntu 11.04 and i am encountering problems when i try to install any update.
this is the error:
[I]
Could not find boot/grub/menu.lst

[/I]Please help in getting out of this problem!
Thanks!

---

### Post by carl4926 on 2011-10-13
Are you sure you are using Ubuntu?

The file to which that refers is not in Ubuntu, it's the location of the grub menu for a distro that uses grub legacy

---

### Post by Saqib Amin on 2011-10-13
yeah i am using ubuntu and the problem is exactly cited above

---

### Post by WasMeHere on 2011-10-13
That is the old version of grub that was used for example in Ubuntu 8.04, Hardy Heron. Which version was your original Ubuntu installation?

---

### Post by Saqib Amin on 2011-10-13
[IMG]http://s3.postimage.org/giawzruw9/Screenshot.png[/IMG]

---

### Post by Saqib Amin on 2011-10-13
my original version was and is UBUNTU 11.04

---

### Post by WasMeHere on 2011-10-13
Is there another operating system installed on your computer?

By the way, what update are you trying to install? Please post the command and the output?

---

### Post by Saqib Amin on 2011-10-13
Looks like its working now
i pressed Y this time and it automatically generated that file. 

[Olle Wiklund]("http://ubuntuforums.org/member.php?u=571173") said that this is older version of grub. please tell me how to install newer version?

---

### Post by WasMeHere on 2011-10-13
I think that it is not very important, what grub version you have. It is only helping you during the boot process. The newer version is more complicated to handle but gives you more options and nicer graphics, if you want to install that. But it has no influence on the performance of the computer once it is running. Anyway, to find out what is your grub version, please post the output of the command
```
ls -l /boot/grub/grub* /boot/grub/menu.lst
```

I suggest that you view the content of the files found by that command and compare it to the menu that is displayed at very start when booting (the grub menu).

---

### Post by WasMeHere on 2011-10-13
Please post also the output of ```
update-grub -v
``` It should show the grub version.

---

