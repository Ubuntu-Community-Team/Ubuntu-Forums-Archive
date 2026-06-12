---
title: "Is it more stable using grub than wubi?"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by garyed on 2008-07-27
Forgive my ignorance but I've been reading so many threads about Wubi installs & didn't have any idea what it was. I finally did a little research & have a little understanding now so my question is:
Is Ubuntu more stable or more efficient installed with Grub than Wubi ?

---

### Post by Vakman on 2008-07-27
A Wubi install would be less stable. The performance is almost identical to a standard installation with Grub but for accessing files on the hard drive will be a bit slower than an installation to an actual partition.

---

### Post by scragar on 2008-07-27
the install to the HD with grub is a real partition, rather than an image, so file access is a little quicker, however other than that there are no differences as far as I know.

---

### Post by stevoo on 2008-07-27
YOu must have gotten something wrong here ... 

Grub is a Multiboot boot loader. so basically it does nothing on its own, you can choose Operatin System to load from there.

Most probably you mean from installing Ubuntu as an OS or using Wubi.

Wubi is an application that runs inside windows. Definetely that will be much more limited in power. It will be a little slower as a OS cannot fully run inside another OS. This is good if you want to test thinks out and you are afraid to install a new OS.

Installing it will on the other hand give you full access to the Linux world. You can dual boot it having both wind and linux installed and you can choose which one to load and run. This way is faster and most reccomended i think :) 

But in the end it is up to you. YOu can use Wubi for some time if you like make a dual boot installation and try it even more ;-)

---

### Post by RequinB4 on 2008-07-27
Well, the major thing is if your windows partition gets fried (somehow, can't have ANYTHING to do with the stability of the OS >.>) you lose the image file, and wubi goes bye bye.

---

### Post by alzie on 2008-07-27
I currently dual boot with XP.  I find that having Ubuntu on its own drive is "safer" for me so if I mess windows up (which I do on occasion) I won't lose my Ubuntu.

I started with a Wubi install originally and I was very pleased with it.  I did it this way so if I was unhappy it was easy to uninstall.

Wubi slightly slower in my opinion but not so bad as to be an issue.

So,  I'd dual boot for a more permanent install.  But if its a new computer and you're worried about warrantee or if its a family computer and they won`t let you, or you have concerns about dual booting, I'd go with Wubi.

I hope this helps

<edit> Wubi is a full install but on a virtual (I believe loop) drive,  not a virtual machine.  With Wubi you'll still get a grub menu with a choice of OS.

---

### Post by scragar on 2008-07-27
> **stevoo said:**
> YOu must have gotten something wrong here ... 

Grub is a Multiboot boot loader. so basically it does nothing on its own, you can choose Operatin System to load from there.

Most probably you mean from installing Ubuntu as an OS or using Wubi.

Wubi is an application that runs inside windows. Definetely that will be much more limited in power. It will be a little slower as a OS cannot fully run inside another OS. This is good if you want to test thinks out and you are afraid to install a new OS.

Installing it will on the other hand give you full access to the Linux world. You can dual boot it having both wind and linux installed and you can choose which one to load and run. This way is faster and most reccomended i think :) 

But in the end it is up to you. YOu can use Wubi for some time if you like make a dual boot installation and try it even more ;-)

actualy, wubi doesn't run inside of windows, it edits the windows boot loaded to add itself, windows hasn't loaded at that point, so the overhead is none.

---

### Post by jordanmthomas on 2008-07-27
> **stevoo said:**
> YOu must have gotten something wrong here ... 

Wubi is an application that runs inside windows. Definetely that will be much more limited in power. It will be a little slower as a OS cannot fully run inside another OS. 

I think you actually have it wrong.  Wubi installs as a full standalone OS, whose filesystem happens to be a file in another OS.  When it boots, Windows is not in the picture.  It's a little slower since files aren't on an actual partition and are just in an image, but aside from booting from Windows' bootloader, Wubi doesn't need Windows to work.

---

### Post by garyed on 2008-07-27
Thanks for the replies.
I should have explained that I have been dual booting with XP using grub for about a year now & am very happy. I was more curious as to whether it makes any sense to use Wubi if you plan on keeping Ubuntu on the machine permenantly. I understand that Grub wipes out the Windows MBR & installs Ubuntu on its own partition.

---

### Post by stevoo on 2008-07-27
> **jordanmthomas said:**
> I think you actually have it wrong.  Wubi installs as a full standalone OS, whose filesystem happens to be a file in another OS.  When it boots, Windows is not in the picture.  It's a little slower since files aren't on an actualy partition and are just in an image, but aside from booting from Windows' bootloader, Wubi doesn't need Windows to work.

i had no idea ... i though it was a simple application to run ubu on win

---

### Post by scragar on 2008-07-27
it's far from simple, the application is a pretty complexe script.

---

