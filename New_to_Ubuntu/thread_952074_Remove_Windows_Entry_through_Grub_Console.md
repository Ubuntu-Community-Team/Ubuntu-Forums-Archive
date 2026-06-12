---
title: "Remove Windows Entry through Grub Console?"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by Belerophon on 2008-10-18
Hi.

I recently deleted my windows partition from my hard disk. Now I just have Ubuntu running on my machine.

Now I want to remove the windows entry from my grub menu. I know I just have to delete the entry from the grub menu.lst

What I want to know is if this can be done through a grub console, if there is an automated way to remove entries that do not exist any more on the disk. 

Can anyone help me?

Thanks.

---

### Post by jimmy the saint on 2008-10-18
the grub menu list is a text file at
/boot/grub/menu.list

If you delet the relevant entries in that file, they will not show up.  Rather than delet them, though, I would just comment them out first.  That means add a # before all the lines in that entry.  MAKE SURE YOU COPY THE FILE FIRST TO ANOTHER NAME TO MAKE A BACKUP!!

Good Luck

---

### Post by caljohnsmith on 2008-10-18
To my knowledge there is no automated way of removing entries from the menu.lst when OSes are deleted, nor is there a way to do it through the Grub console; you simply have to edit your menu.lst. :)

---

### Post by stephanvaningen on 2008-10-18
You can start editing this file using command
 ```
sudo gedit /boot/grub/menu.list
```

---

### Post by Belerophon on 2008-10-19
Hum...thanks you all for your replies.

I just think it is strange that there is no automated way to verify if the entries on the menu.lst are valid...after all, update-grub does verify the ubuntu kernels and delete the entries that have no corresponding kernel in the /boot folder....I was looking for something similar for windows installations...

But ok, I will probably delete the entries from menu.lst myself.

Thanks.

---

