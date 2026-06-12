---
title: "How to change dual-boot settings"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by Watchtow3r on 2008-10-11
I want to change it so that it first has Ubuntu primarily highlighted (so if I forget it won't load Windows) and also want to change the 10-second wait time to something like 3 or 2 seconds. How can I do this? Thanks!

---

### Post by sadman64 on 2008-10-11
Assuming you are using GRUB as your boot loader, edit the file /boot/grub/menu.list

you can change the value 'default' to the index of the menu choice you want to be selected (it should already be ubuntu)

you can change the value of 'timeout' to be the number of seconds you want, 3 or 2

---

### Post by Watchtow3r on 2008-10-11
Wow, probably one of the easiest fixes I've had for Ubuntu. Thx a lot!

Also, when I hit ESC at bootup, It displays 8 versions of Ubuntu (4 different Kernel versions and recovery modes) and 2 similar-looking Windows (the only difference it seems is that one says (hd0,0) for root, and the other says (hd0,1). What are the differences between these Windows, and can I delete one from the list? Also is there any reason to keep the other kernels on my computer? Thank you.

---

### Post by Watchtow3r on 2008-10-11
In addition, where is the "default" option? Is it "savedefault"? Also, what is the chainloader? Is that related to anything here? Thanks!

---

### Post by graphicmist on 2008-10-11
> **Watchtow3r said:**
> 
When I hit ESC at bootup, It displays 8 versions of Ubuntu (4 different Kernel versions and recovery modes) and 2 similar-looking Windows (the only difference it seems is that one says (hd0,0) for root, and the other says (hd0,1). What are the differences between these Windows

root(hd0,0) means that the windows is installed in the first partition (counting from 0) of your hard disk (hd0).

similarily root(hd0,1) means grub have to boot windows from the second partition.

check which one is working for you and u can delete the other entry which one is not working.

---

### Post by graphicmist on 2008-10-11
> **Watchtow3r said:**
>  Also is there any reason to keep the other kernels on my computer?

You can customize the grub menu as u want...keep the entry you uses for running ubuntu and can delete other entries.

---

### Post by graphicmist on 2008-10-11
> **Watchtow3r said:**
> In addition, where is the "default" option? Is it "savedefault"? Also, what is the chainloader? Is that related to anything here? Thanks!

the default option is at the top of the file menu.lst. u can change it to any value in grub menu starting from 0. that means if ur windows is the 4th entry in grub menu n u want to make it default u have to change the default value to 3.

chainloader is the technique used for booting other OS like windows. what it actually does is that it grabs the first sector of the current partition with `+1 which contains code for booting OS.

---

### Post by Watchtow3r on 2008-10-11
I'm sorry, I might not have made my original question clear. I want to change the default bootup (at the screen that automatically loads when you turn on your computer) so that it will automatically load Ubuntu when I turn on my computer without making me have to select it. How can I do this? Thanks.

---

### Post by louieb on 2008-10-11
> **Watchtow3r said:**
> ...I want to change the default bootup,  so that it will automatically load Ubuntu when I turn on my computer without making me have to select it. 

The installer should have set it up that way. 
Unless you have made changes to the grub configuration file /boot/grub/menu.lst.

What exactly does it do when you turn on the computer on and let it boot without doing any thing?

If you have more questions copy /boot/grub/menu.lst in your next post.

---

