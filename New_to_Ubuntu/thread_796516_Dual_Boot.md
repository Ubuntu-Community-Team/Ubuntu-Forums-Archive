---
title: "Dual Boot"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Tex786 on 2008-05-16
How do I go in to change what is displayed in the window that comes up when i need to sellect witch OS I want to run?

How do i change the grub or is it even the grub i need to change?

I am still wet behind the ears so speak my language :).

---

### Post by hums07 on 2008-05-16
Open terminal and type
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Tex786 on 2008-05-16
> **hums07 said:**
> Open terminal and type
```
gksudo gedit /boot/grub/menu.lst
```

I have that open but I do not know how to change what is there. I am scared if i do anything I will only damage my system.

---

### Post by hums07 on 2008-05-16
I see the entries are well commented. Read the comments thoroughly. You should be able to figure out what to modify.
If you need more detailed info, then read the [manual for grub]("http://www.gnu.org/software/grub/manual/grub.html").

Plus if you messed your grub, you can reinstall it any time using your live CD:
```
sudo grub
find /boot/grub/stage1
root (hdX,Y)  # change X,Y with the result of the above command
setup (hdX)
```

Be brave!

---

### Post by CloudFX on 2008-05-16
This is my favourite guide for editing grub: 
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by Paqman on 2008-05-16
> **Tex786 said:**
> I have that open but I do not know how to change what is there. I am scared if i do anything I will only damage my system.

It's always good practice to make a backup of any system file before editing it anyway. If worst came to worst just boot up the LiveCD (or recovery mode) and replace your broken file with the backed-up version.

---

### Post by Falcorian on 2008-05-16
Well, what do you want to do?

---

### Post by Tex786 on 2008-05-16
> **Falcorian said:**
> Well, what do you want to do?

Okey Here is what i want to know.

When I have Xubuntu and Ubuntu installed onthe same machine there are always several things to pick when booting up the computer. 

what I want to know how to limit what is displayed in the bootloader. I want to be able to pick Xubuntu or ubuntu with out all this recovery stuff. I just want 2 things to choose from.

I hope you have got the idea of what i want to do.

---

### Post by alzie on 2008-05-16
One way is to use the startup manager

>  sudo apt-get install startupmanager

It is also available through Synaptic

This allows you to choose your default OS nad on the advanced tab you can deselect the memtest and recovery mode options.

After installing startup manager it will be in System>Administration

I hope this helps

---

