---
title: "Does not display OS choice screen with XP dual boot"
date: 2014-03-07
forum: New to Ubuntu
---

### Post by Derek_Hughes on 2014-03-07
Hi
I just installed ubuntu 12 from a DVD  for the first time on  a Dell D620 laptop, alongside XP. 
The install said it was finished Ok, but when I rebooted there was no OS choice screen, it just went straight into XP.

Any ideas what I did wrong?
Has anyone else had success on the D620?

Thanks

Derek

---

### Post by nunecas123 on 2014-03-07
Did you install Ubuntu on the same disk? Are you sure? Did you select "Install Ubuntu alongside Windows XP?"

---

### Post by Derek_Hughes on 2014-03-07
Just one disk in the laptop, definitely selected, 'alongside windows'

---

### Post by nunecas123 on 2014-03-07
OK. Try download one of these ISOs: [LINK]("http://sourceforge.net/projects/boot-repair-cd/files/")

Then, make a bootable USB or DVD using Unetbootin.

Boot from the USB/DVD and run it.

Choose Recommended Repair from this screen:

[IMG]http://pix.toile-libre.org/upload/original/1335260967.png[/IMG]

It should update grub, allowing you to choose the OS you want after it.

Give us news.

---

### Post by newb85 on 2014-03-07
Most likely, you installed Grub in the wrong place. Boot repair will likely fix it.

---

