---
title: "[SOLVED] How can I disable the boot screen that lets me choose Vista or Ubuntu?"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by GumpTron on 2008-11-02
Hellom

new Ubuntu user here again. I have just installed Ubuntu on my HD's other partition and things work great. However, when I turn on my PC i get a black screen asking me to choose Ubuntu or Vista and this is a problem becasue others use this comp.

Is there a way to set the computer so it boots Vista as teh default OS? Thank you. 

p.s. If i cant solve this issue I will have to delete Ubuntu :cry:[-(

thank you for your help.

---

### Post by Paqman on 2008-11-02
Install startupmanager. It'll let you choose which system Grub defaults to, as well as a ton of other things.

---

### Post by GumpTron on 2008-11-02
> **Paqman said:**
> Install startupmanager. It'll let you choose which system Grub defaults to, as well as a ton of other things.

can you expand on that please? 

do I install it on vista to use it?
is it free?


is it possible to do this another way without downloading third party software?

---

### Post by Nepherte on 2008-11-02
Open up /boot/grub/menu.lst
```
gksudo gedit /boot/grub/menu.lst
```
look up "default" and change the number that accompanies it to the number of the entry vista is. Originally it looks like this:
```
default **0**
```
So if vista is your fourth entry, change it to 3 (we start counting at 0).

---

### Post by Zalbor on 2008-11-02
Do the above, but also find this line:
```
# updatedefaultentry=false
```
and change it to:
```
# updatedefaultentry=true
```
**(be sure to keep the #)**.

That way it will stay correct if an Ubuntu update adds more kernels.

Keep in mind that all this won't disable the screen, it will only make Vista the option that's selected. So if whoever uses the computer presses nothing on this screen, Vista will boot. If you actually disabled the screen there would be no way to use Ubuntu anymore.

---

### Post by Paqman on 2008-11-02
> **GumpTron said:**
> can you expand on that please? 

do I install it on vista to use it?
is it free?

is it possible to do this another way without downloading third party software?

It's not 3rd-party software, it's in the Ubuntu repos. Just open up Applications > Add/Remove and search for it.

The other way is to edit /boot/grub/menu.lst manually, as Nepherte mentioned, but I recommend using startupmanager myself. It's a handy little package.

---

### Post by kansasnoob on 2008-11-02
```
sudo apt-get install startupmanager
```

You'll then find it in System > Administration > Startup Manager.
There you can select the Default OS, change length of timeout, and hide the Bootloader Menu just by "unticking" Show Bootloader Menu:

[ATTACH]90701[/ATTACH]

I should add that you can then get to the bootloader menu by pressing the Esc key just as your computer passes the BIOS screen and begins the boot process.

---

