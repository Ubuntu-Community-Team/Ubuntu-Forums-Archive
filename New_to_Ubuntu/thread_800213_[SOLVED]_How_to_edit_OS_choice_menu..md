---
title: "[SOLVED] How to edit OS choice menu."
date: 2008-05-19
forum: New to Ubuntu
---

### Post by nerd0795 on 2008-05-19
I have just installed ubuntu today ^^.  I was just wondering how do I edit the OS launcher thing so I have vista highlighted first?  I was just wondering cuz this ain't my computer (my family).  So I was just wondering how to have Vista highlighted.

---

### Post by agim on 2008-05-19
# sudo gedit /boot/grub/menu.lst

This is the file that holds that info. 
Toward the bottom, will be the lines that you see when grub runs on your system.

Just switch the order. But keep the form the way it is, like this:

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=4fa55e1d-1832-4e96-8e$
initrd          /boot/initrd.img-2.6.24-16-generic
quiet


That was a little convoluted, but I think you should get it.
Good luck

---

### Post by sam_delta on 2008-05-19
another way to do it is changind the "default" option on the file mentioned above, (/boot/grub/menu.lst)

find a line where it says

default 0

and change it to "4" which is the windows line or the menu line you wish to be the default, (0=ubuntu, 1=ubuntu recovery, 2=ubuntu memtest, 3=other os line, 4=windows)
(example, if you wish to be ubuntu recovery the default, you type 1, etc)

it should look like this

default 4

sam

---

### Post by nerd0795 on 2008-05-19
[IMG]http://usera.imagecave.com/alex_the_great/Screenshot.png[/IMG]

Do I put that above the ubuntu part?

---

### Post by agim on 2008-05-19
I like that way a lot. Don't have to worry about making a mistake while copying and pasting.

Also, before you make _any_ change, backup your menu.lst file.

this is how I do it.

# sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

---

### Post by agim on 2008-05-19
Yes, that is how I did it, by putting that part over the ubuntu part, but the poster above listed a more elegant solution.

Feel free to use either.

And make backups whenever you change configuration files.

---

### Post by sam_delta on 2008-05-19
if you want to do it the way i told you , just scroll back up until you see a "default 0" line, and change it to "default 4", replace the 0 with a 4

sam

---

### Post by JC Cheloven on 2008-05-19
You have to edit the /boot/grub/menu.lst as super user. From a terminal type:```
gksudo gedit /boot/grub/menu.lst 
```
You'll be promtped for your password.

Then be careful. Change only the line which reads : default 0  (with no # sings at start)  to 
```
default 4  
```

Save and exit, that's it.
NOTES: Anyway, the default OS to boot starts counting from 0. So 0 should be ubuntu (first entry in your file), and the others follow in the order they appear in the file.

Greetings

---

### Post by Thirtysixway on 2008-05-19
If it's a wubi install, you can change the boot order in windows control panel.

---

### Post by sam_delta on 2008-05-19
> **JC Cheloven said:**
> You have to edit the /boot/grub/menu.lst as super user. From a terminal type:```
gksudo gedit /boot/grub/menu.lst 
```
You'll be promtped for your password.

Then be careful. Change only the line which reads : default 0  (with no # sings at start)  to 
```
default 2  
```

Save and exit, that's it.
NOTES: I assume you have installed ubuntu and vista only. Anyway, the default OS to boot starts counting from 0. So 0 should be ubuntu, 1 an empty entry, and 2 vista.

Greetings

remember you still have ubuntu recovery, and ubuntu memtest, so it should be 4, not 2

sam

---

### Post by nerd0795 on 2008-05-19
I set my default to 4 but the thing is it puts at windows 2000/XP when I don't have it.  So should I put default at 5?

---

### Post by sam_delta on 2008-05-19
yeah,, you put the line of the menu which you want to be the default , the first one being a 0, so if you want to have the next line as default, then put a 5 

sam

---

### Post by Kinst on 2008-05-19
Ubuntu gave you a boot loader called GRUB, and  the menu.lst file controls how GRUB works.

---

### Post by JC Cheloven on 2008-05-19
> **sam_delta said:**
> remember you still have ubuntu recovery, and ubuntu memtest, so it should be 4, not 2

sam

yes, you're right. I edited my post as soon as I saw the user's menu.lst ;-)

---

### Post by sam_delta on 2008-05-19
> **JC Cheloven said:**
> yes, you're right. I edited my post as soon as I saw the user's menu.lst ;-)

yeah, good, keep up the good work bro

sam

---

