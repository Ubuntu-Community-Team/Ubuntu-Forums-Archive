---
title: "Grub, Can it be disabled?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by stuart0742 on 2008-05-10
Hi

I am new to Linux so sorry if this is a dumb question.

Can I disable GRUB?

I have installed Ubuntu to dual boot with Windows XP therefore when GRUB loads you get the various options, fine

I have now installed Acronis OS selector which loads on bootup, if I choose to boot Linux, GRUB is loaded and I get the same choices again.

What I want is Linux to boot straight away with out GRUB.

Regards

Stuart

---

### Post by TeoBigusGeekus on 2008-05-10
I don't know if you can completely disable it, but you can fool it.
Type in terminal
```
gksudo gedit /boot/grub/menu.lst
```
and post us the contents of the file.

---

### Post by mgranet on 2008-05-10
Hrm. Not sure. If you remove GRUB, Linux will probably fail to boot, even with Acronis installed. You might try editing your grub file to remove mentions of WinXP, or using 0 second delay on the GRUB display. If Linux is already the default, then that last option might be easiest.

---

### Post by tjwoosta on 2008-05-10
i also dont know if it can be completely disabled but i do know that you can set it up to automatically login to ubuntu. just use a timeout of like 1 second or maybe 0 seconds (never actually tried)

---

### Post by nowshining on 2008-05-10
i use 1 for 1 second that way it gives me time incase something comes up.

example:

```


## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout	1

 
```

---

### Post by stuart0742 on 2008-05-10
I have set the timeout to 1 sec, that seems to have done the trick

Many thanks

Stuart

---

### Post by nowshining on 2008-05-10
ur welcome

---

### Post by skymera on 2008-05-10
If you dont need the menu you can set the timeout to 1 and adjust the "hidemenu" section.

---

