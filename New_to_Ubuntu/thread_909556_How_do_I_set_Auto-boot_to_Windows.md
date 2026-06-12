---
title: "How do I set Auto-boot to Windows"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by KeithA45 on 2008-09-03
Hey guys,

With a little bit of trouble here and there, I finally got my computer to dual-boot windows and Ubuntu. Now my next question is this: How do I set Windows to be at the top of the list in Grub so that it boots to that automatically instead of Ubuntu? I see the edit and savedefault option in Grub, but I have no idea where to start.

Thanks,
 - Keith

---

### Post by oilchangeguy on 2008-09-03
see this:
[http://ubuntuforums.org/showthread.php?t=847579&highlight=change+default+dual+boot+operating+system](http://ubuntuforums.org/showthread.php?t=847579&highlight=change+default+dual+boot+operating+system)

---

### Post by drs305 on 2008-09-03
The safe and easy method? Install StartUp-Manager: "sudo apt-get install startupmanager".

Run 'gksu startupmanager' in terminal or System, Admin, StartupManager. Boot Options, select Windows in the Default Operating selection area.

Full details in my signature line link.

---

### Post by Oldsoldier2003 on 2008-09-03
> **KeithA45 said:**
> Hey guys,

With a little bit of trouble here and there, I finally got my computer to dual-boot windows and Ubuntu. Now my next question is this: How do I set Windows to be at the top of the list in Grub so that it boots to that automatically instead of Ubuntu? I see the edit and savedefault option in Grub, but I have no idea where to start.

Thanks,
 - Keith

You need to edit /boot/grub/menu.lst and change the line default 0 to reflect the number windows is in your list. the first option is 0 the second is 1 etc...

in order for your changes to be saved you will need to use sudo when you edit the file.

```
sudo nano /boot/grub/menu.lst
``` will open it in nano

```
gksu gedit /boot/grub/menu.lst
``` will open it in gedit

---

### Post by rossjman1 on 2008-09-03
> **drs305 said:**
> The safe and easy method? Install StartUp-Manager: "sudo apt-get install startupmanager".

Run 'startupmanager' in terminal or System, Admin, StartupManager. Boot Options, select Windows in the Default Operating selection area.

Full details in my signature line link.

I agree. From this program you can easily change how many kernels are listed, as well as removing the Memtest from the menu. You can also add a background image and change the resolution of grub.

---

### Post by KeithA45 on 2008-09-03
> **drs305 said:**
> The safe and easy method? Install StartUp-Manager: "sudo apt-get install startupmanager".

Run 'startupmanager' in terminal or System, Admin, StartupManager. Boot Options, select Windows in the Default Operating selection area.

Full details in my signature line link.

Thank you! the code didn't work, but the explination from the link in your sig did the trick. Thanks =)

---

### Post by drs305 on 2008-09-03
> **KeithA45 said:**
> Thank you! the code didn't work, but the explination from the link in your sig did the trick. Thanks =)
The command would have to be preceded by "gksu" since StartUp-Manager edits a system file (/boot/grub/menu.lst). I've updated the original post. 

"gksu startupmanager"

Please mark the thread SOLVED with the "Thread Tools" link near the top right of the first post if your questions have been answered.

---

