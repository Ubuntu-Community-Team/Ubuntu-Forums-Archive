---
title: "[SOLVED] boot first from ubuntu..."
date: 2008-11-27
forum: New to Ubuntu
---

### Post by abrax on 2008-11-27
Hello:

     I've been using Ubuntu for a little while and i'm happy with it, but still i have a question:

    I installed version 8.10 from windows with the wubi installer and it works perfectly fine. When i turn on my pc it shows me a start menu thar i think its windows', where it tells me to choose between Vista(in first place), and Ubuntu (in second place), and it has a 10 second timer so if no activity is made, it boots into vista. Is there a way to change that menu (i dont know for sure if it is in the mbr) so the first option is ubuntu instead of vista?

Hope i made myself clear.

Thanks in advance for your help. :D

---

### Post by nakama85 on 2008-11-27
> **abrax said:**
> Hello:

     I've been using Ubuntu for a little while and i'm happy with it, but still i have a question:

    I installed version 8.10 from windows with the wubi installer and it works perfectly fine. When i turn on my pc it shows me a start menu thar i think its windows', where it tells me to choose between Vista(in first place), and Ubuntu (in second place), and it has a 10 second timer so if no activity is made, it boots into vista. Is there a way to change that menu (i dont know for sure if it is in the mbr) so the first option is ubuntu instead of vista?

Hope i made myself clear.

Thanks in advance for your help. :D

Sure you can change it via grub

```
sudo gedit /boot/grub/menu.lst
```

Find where the boot order is and switch the teo

---

### Post by nakama85 on 2008-11-27
You can use this for an example

Original
> ## ## End Default Options ##

title		Windows, Vista
uuid		(hd0,0)
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		7b201560-607e-43b9-9a98-5e87d8783071
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7b201560-607e-43b9-9a98-5e87d8783071 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		7b201560-607e-43b9-9a98-5e87d8783071
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


You would simply change the order by doing this

> ## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		7b201560-607e-43b9-9a98-5e87d8783071
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7b201560-607e-43b9-9a98-5e87d8783071 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Windows, Vista
uuid		(hd0.0)

title		Ubuntu 8.10, memtest86+
uuid		7b201560-607e-43b9-9a98-5e87d8783071
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

*Note: there are other ways simply to change the default without reordering the menu list.*

---

### Post by abrax on 2008-11-27
@nakama85

thanks for the help, but the problem is not in grub, because i've already downloaded an aplication called startup manager and i can also edit grub from there, the problem is that kind of windows bootloader...i really dont want to make grub my default bootloader because in the past i had problems with grub and my laptop...

i'll explain better:
i turn on the laptop, bios loads, and then the windows bootloader starts up asking me to choose between ubuntu and vista. i choose ubuntu AND THEN grub loads (like ive said before, i dont have problems with that because ive modified it so it automatically boots U-8.10).

my question is, can i modify THE FIRST bootloader? the windows one?

thanks!!

---

### Post by nakama85 on 2008-11-27
Ahh. I got it..... ok in windows you will want to edit the boot.ini file to the order that you would like

you can get there by going to c:drive and opting to show hidden files and system files
When you see the boot.ini the first thing you will want to do is back it up before Backing any changes.

I hope this works for you...I don't remember so much of vista as it was the main reason I switched to Ubunut. That being said I remember XP like the back of my hand

---

### Post by smarks on 2008-11-27
Thanks nakama85,

what you said about  sudo gedit /boot/grub/menu.lst Actually helped me out with an issue ive been having with a ton of updates in the grub menu that i was too lazy to figure out.

Thanks

---

### Post by abrax on 2008-11-27
> **nakama85 said:**
> Ahh. I got it..... ok in windows you will want to edit the boot.ini file to the order that you would like

you can get there by going to c:drive and opting to show hidden files and system files
When you see the boot.ini the first thing you will want to do is back it up before Backing any changes.

I hope this works for you...I don't remember so much of vista as it was the main reason I switched to Ubunut. That being said I remember XP like the back of my hand

oh that was the very first thing i thought but i couldn't find that boot.ini.

But i've solved it, in system properties>>advanced settings>>startup recovery or something like that you can chose the default OS.

Thanks!!

---

### Post by nakama85 on 2008-11-27
> **abrax said:**
> oh that was the very first thing i thought but i couldn't find that boot.ini.

But i've solved it, in system properties>>advanced settings>>startup recovery or something like that you can chose the default OS.

Thanks!!

Glad to hear you solved the problem!!!:popcorn:

Don't forget to mark your thread as solved

---

### Post by caljohnsmith on 2008-11-27
Abrax, you might want to check out [EasyBCD]("http://neosmart.net/dl.php?id=1"); it is a really easy to use program for modifying your Vista's boot menu. Anyway, cheers and glad you fixed your problem.

---

