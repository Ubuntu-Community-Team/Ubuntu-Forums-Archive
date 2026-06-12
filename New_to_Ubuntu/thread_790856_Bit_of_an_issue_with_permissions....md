---
title: "Bit of an issue with permissions..."
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Caram on 2008-05-11
Hello! I'm having a bit of an issue editing /boot/grub/menu.lst
I'm trying to change the default option on the boot menu and it won't let me change it unless I'm root. sudo edit menu.lst gives an error, so I'm not really sure how I should go about doing this. 

Thanks in advance.

---

### Post by macaholic on 2008-05-11
When launching a graphical applicaiton as sudo, always use gksu/gksudo, try that instead. If that doesn't work, you could always use a command line only editor like vii or nano.

---

### Post by jolx on 2008-05-11
it shud be: sudo gedit /boot/grub/menu.lst

sudo - gives root permissions, gksudo does the same thing but it will pop up with a box asking for your password
gedit - the program being used this is interchangeable with nano, vim, etc.
and when specifying the file you should type the full location (not just the file)

---

### Post by Caram on 2008-05-11
Doing this, I get "cannot open display:"

gksu didn't work either. got an error.

---

### Post by macaholic on 2008-05-11
Can you open gedit at all?

---

### Post by Caram on 2008-05-11
Yeah, it opens fine if I go to applications, Text Editor.

---

### Post by Caram on 2008-05-11
Heh, I got it working somehow. I tried opening a new terminal and sudo gedit worked :| Thanks for the help.

---

