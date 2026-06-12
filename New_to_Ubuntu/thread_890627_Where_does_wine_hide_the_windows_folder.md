---
title: "Where does wine hide the windows folder?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by lwalper on 2008-08-15
I enabled Wine, installed a windows app (e-Sword). Everything seemed to go great, but now I can't find the installed application. Where does Wine put everything? I tried to create an icon on the desktop, but can't seem to locate the folder where the program files are stored??

---

### Post by sharks on 2008-08-15
in /home/.wine

---

### Post by lwalper on 2008-08-15
Thanks, but I don't see that path. Do I need enable "view hidden files" or something?--or is that a Windows snafu?

---

### Post by Diabolis on 2008-08-15
You are correct, press **<Ctrl>h** to see hidden files.

---

### Post by iaculallad on 2008-08-15
> **lwalper said:**
> Thanks, but I don't see that path. Do I need enable "view hidden files" or something?--or is that a Windows snafu?

While in your Home folder, press Ctrl+H to see your hidden files and folders. Look for **.wine** directory.

---

### Post by Too Late on 2008-08-15
Well, the path of the wine folder is /home/yourusername/.wine/

The windows "C drive" is probably in a subfolder called drive_c.

In Nautilus, click 'View' menu and check "Show Hidden Files". Or just press Ctrl+H.

---

### Post by lwalper on 2008-08-15
OK! Yeah, thanks, there it is.

---

