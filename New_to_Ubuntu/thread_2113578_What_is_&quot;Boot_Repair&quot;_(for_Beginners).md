---
title: "What is &quot;Boot Repair&quot; (for Beginners)"
date: 2013-02-07
forum: New to Ubuntu
---

### Post by Slimey on 2013-02-07
I have been hearing a bit about the software "Boot Repair", but it's not really clear what its purpose is, whether it comes with the Ubuntu installation or must be separately downloaded, or which situations people might want to use it (or does it run all of the time?). 
Is it part of the same partition as the Ubuntu/Linux installation, or is it separate? Furthermore, if I don't have any current booting problems, how could I remove it? Should I remove it?

---

### Post by sudodus on 2013-02-07
It is described here

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

and I don't think it is dangerous at all. It is a tool to help people find and repair problems with booting. It does not run all the time, only when you start it.

I suggest that you keep it, but next time you need to use it, check if there is a new version to be downloaded before using it again.

---

### Post by GameX2 on 2013-02-07
It is actually really useful when GRUB get erased by Windows.
I use it quite often and make the process of fixing GRUB automatic.

---

### Post by deadflowr on 2013-02-07
> **Slimey said:**
> I have been hearing a bit about the software "Boot Repair", but it's not really clear what its purpose is, whether it comes with the Ubuntu installation or must be separately downloaded, or which situations people might want to use it (or does it run all of the time?). 
Is it part of the same partition as the Ubuntu/Linux installation, or is it separate? Furthermore, if I don't have any current booting problems, how could I remove it? Should I remove it?

No, boot-repair does not come with Ubuntu. In fact you need to add a PPA to get it.
So worrying about uninstalling it, or whether it's running is moot unless you added the PPA and installed it.
If you did install it, then it acts just like any other program only running when you call it to run.

> **GameX2 said:**
> It is actually really useful when GRUB get erased by Windows.
I use it quite often and make the process of fixing GRUB automatic.

It's also handy when grub borks grub.

---

