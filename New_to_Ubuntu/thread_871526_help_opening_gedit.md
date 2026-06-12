---
title: "help opening gedit"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by Armed Nuke on 2008-07-27
i need to open gedit from a terminal after logging in as root but when i type in gedit it complains about the display. how do i open gedit to edit a text file from the terminal?

---

### Post by Yuki_Nagato on 2008-07-27
1) Type "exit" now.  Never use the "su" command around the Ubuntu community.  We like to stay out of root account, using "sudo" instead.

2) Instead, type "gksudo gedit" for graphical sudo.

---

### Post by ktrnka on 2008-07-27
Or you could open and edit the file with 

```
nano filename
```

---

### Post by boblemur on 2008-07-27
or you can use pico if you are using commandline only... (for a server or whateva)

---

### Post by Armed Nuke on 2008-07-27
k, thanks. i really needed to know this because the file i'm trying to edit requires the root permissions

---

### Post by Oldsoldier2003 on 2008-07-27
> **boblemur said:**
> or you can use pico if you are using commandline only... (for a server or whateva)

nano = pico :)  Pico isn't installed in Ubuntu because of issues with pine's licensing. Strangely enough, I still type pico though. Old habits die hard!

---

### Post by kansasnoob on 2008-07-27
> **Armed Nuke said:**
> k, thanks. i really needed to know this because the file i'm trying to edit requires the root permissions

What file?

Edit: Since I may not be here to answer when you respond I thought an explanation was in order. I frequently have to edit the sudoers file so I have to follow the documentation to change editors for sudoers:

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

OTOH GRUB's menu list isn't like that, so it very much depends on what you want to edit.

---

### Post by barbedsaber on 2008-07-27
step 1: navigate to the directory the file is in
step 2: type gksudo filename gedit
step 3: type in your password
step 4: mark this thread as solved, by clicking thread tools, mark thread as solved. :)

you can also type

```
gksudo nautilus
```
and open the file from there. (you will be put into the root directory, THIS IS NOT YOUR HOME DIRECTORY (when I did it, I thought I was in my home dir, and that i had lost all my stuff)

---

