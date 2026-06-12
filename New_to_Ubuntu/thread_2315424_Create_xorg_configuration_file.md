---
title: "Create xorg configuration file"
date: 2016-02-28
forum: New to Ubuntu
---

### Post by rafal10 on 2016-02-28
Hi.

I am totally new. I decided to move from Windows to Linux. But I think I'm gonna go back to Windows. I Lenovo z500 and a massive problem with a dimmed screen. I found some solution but don't know how to create a xorg configuration file.

I need to create xorg configuration file with such name and in:

Then create a xorg configuration file like this:
  /usr/share/X11/xorg.conf.d/80-backlight.conf


How can I do it?
I've already spent hours Googling. I'm quite sick of my laptop, so please help me. Ubuntu 15.10

---

### Post by coldraven on 2016-02-29
Hi, welcome to the forum and sorry that you've got problems already.

To create the file open a terminal (Ctrl+Alt+T) and paste this in with Shift+Ctrl+V (or use the Edit>Paste menu)
When asked for your password just type it and hit Enter, you will not see any asterisks. 
This command is running the nano text editor with root permission, that's the sudo part
```
sudo nano /usr/share/X11/xorg.conf.d/80-backlight.conf
```

Then copy whatever you need to make the backlight work and paste into the editor.
To save it press Ctrl+X, confirm save by pressing "Y" and then press Enter. You may need to reboot

Hope this helps. If you post the link to the fix someone else might be able to give more advice.

---

