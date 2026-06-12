---
title: "Grub question"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by bestseclub on 2008-10-08
So i got windows and ubuntu dualboot.The problem is i dont want grub to wait 3 seconds and start ubuntu.
What i want it to do is to show the available OSs from the very beginning,even if i dont press anything.Any way to do that.
Oh,and by the way,is there any way to move the available OSs in the menu?

---

### Post by Forbees on 2008-10-08
QGRUBEditor

can be found in add/remove applications

---

### Post by oldos2er on 2008-10-08
You can edit /boot/grub/menu.lst by hand with the terminal command "gksu gedit /boot/grub/menu.lst". I like using gedit because it automatically creates a backup file for you in case you (or me, or anyone) mess things up.

 QGrubEditor is a good program too.

---

### Post by bestseclub on 2008-10-09
Sorry,been busy.
So can you post the code i need to write in grub.lst to make grub show the list without waiting me to press Escape?

---

### Post by drs305 on 2008-10-09
I am a big fan of StartUp-Manager, a gui grub editor. You can set the default menu timeout, kernel or OS to boot, how many kernels to display, etc. And it does it without having to manually edit menu.lst

Install:
```
sudo apt-get install startupmanager
```

To run:
System, Administration, StartUp-Manager

To display the menu, just set the timeout to a new value in the Boot Options tab. Increase it to a large value to keep the menu displayed for a long time, I'm not aware of a setting to freeze the menu indefinitely.

To change the list order you will have to edit menu.lst manually, which may change the default kernel/OS depending on how it's set. If you manually reorder the list I would recommend using StartUp-Manager afterword to set the default startup. It will figure out where it is in the pecking order.

You can read about all the things StartUp-Manager can do in this tutorial:
[http://http://ubuntuforums.org/showthread.php?t=818177]("http://http://ubuntuforums.org/showthread.php?t=818177")

If you need help with manual editing just let us know.

---

### Post by drowner on 2008-10-09
> **drs305 said:**
> I am a big fan of StartUp-Manager, a gui grub editor. You can set the default menu timeout, kernel or OS to boot, how many kernels to display, etc. And it does it without having to manually edit menu.lst

Install:
```
sudo apt-get startupmanager
```

To run:
System, Administration, StartUp-Manager

To display the menu, just set the timeout to a new value in the Boot Options tab. Increase it to a large value to keep the menu displayed for a long time, I'm not aware of a setting to freeze the menu indefinitely.

To change the list order you will have to edit menu.lst manually, which may change the default kernel/OS depending on how it's set. If you manually reorder the list I would recommend using StartUp-Manager afterword to set the default startup. It will figure out where it is in the pecking order.

You can read about all the things StartUp-Manager can do in this tutorial:
[http://http://ubuntuforums.org/showthread.php?t=818177]("http://http://ubuntuforums.org/showthread.php?t=818177")

If you need help with manual editing just let us know.

You should edit your post to show an 'install' after apt-get

---

### Post by matthewbrave on 2008-10-09
i had the same problem but i have forgotten what to do so i will have a look when i get home

---

### Post by matthewbrave on 2008-10-09
also when editing the file remember it starts from 0 not 1.

anything that is highlited you must count


eg

ubuntu ....
ubuntu recovery...
memtest
other operating systems
windows xp

to select xp it is no. 4

---

### Post by matthewbrave on 2008-10-09
[https://help.ubuntu.com/8.04/switching/dualboot-custom.html](https://help.ubuntu.com/8.04/switching/dualboot-custom.html)

go here this is the best option

---

