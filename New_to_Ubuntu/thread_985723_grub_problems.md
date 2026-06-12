---
title: "grub problems"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by bno545 on 2008-11-17
I went to reformat and in order to back up my files I used my sisters hard drive from her windows box. After everything was finished I removed the hard drive with the windows install on it.  Now when I start my computer I get to the grub boot loader and it is still recognizing the windows install.  I can still boot into ubuntu but I would like to not have to select which install to boot into.

---

### Post by taurus on 2008-11-17
If you want to remove the entry for windows, you can delete it from /boot/grub/menu.lst.

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
It's at the end of the file.

---

### Post by bno545 on 2008-11-17
yes i have tried that many times but the menu is still there and it still wants me to choose what to boot

---

### Post by kansasnoob on 2008-11-17
Are you remembering to click "save" and then go to File > Quit after editing the menu.list?

---

### Post by meierfra. on 2008-11-18
Open "menu.lst" via "gksudo gedit /boot/grub/menu.lst" and change

"timeout 10"   to "timeout 3"

and 

"#hiddenmenu" to "hiddenmenu"

---

### Post by bno545 on 2008-11-18
ah thats the ticket... thanks ... i know it didnt hurt anything but i just didnt like it.

---

### Post by Rolcol on 2008-11-18
Although you got this working, there is a GUI that can edit /boot/grub/menu.lst

[http://packages.ubuntu.com/intrepid/startupmanager](http://packages.ubuntu.com/intrepid/startupmanager)

```
sudo apt-get install startupmanager
```

---

