---
title: "A few quick questions"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Dark006 on 2008-06-08
1)Does the 'who' command show everyone thats on your wireless network? (kinda like "NET VIEW /NETWORK" in Windows, even if they're running Windows XP?)If not, anyone know of a way to check this out?

2)Is there a way to send messages to other people on your wireless (like NET SEND)? Again, also if I'm using Linux and they have XP?

3)Lastly, I was having problems with ndiswrapper. I decided just to have a direct connection rather than a wireless (because I couldn't figure ndiswrapper out). As far as I know, I had ndiswrapper at *least* extracted. Not sure if was really installed or not (still kinda new to linux). SO anyway, I just moved the whole folder that had the .tar.gz file, and the extracted files to the trash. Now when I try to remove them from the trash it won't let me. And my permissions say I can create and delete files. Any ideas?

---

### Post by quelx on 2008-06-08
> **Dark006 said:**
> 1)Does the 'who' command show everyone thats on your wireless network? (kinda like "NET VIEW /NETWORK" in Windows, even if they're running Windows XP?)If not, anyone know of a way to check this out?
**who** only shows users logged into the system where **who** was executed.  Your router or AP should show MAC addresses for computers attached to the wireless network.

> 2)Is there a way to send messages to other people on your wireless (like NET SEND)? Again, also if I'm using Linux and they have XP?

[http://www.yolinux.com/TUTORIALS/unix_for_dos_users.html](http://www.yolinux.com/TUTORIALS/unix_for_dos_users.html)

> 3)Lastly, I was having problems with ndiswrapper. I decided just to have a direct connection rather than a wireless (because I couldn't figure ndiswrapper out). As far as I know, I had ndiswrapper at *least* extracted. Not sure if was really installed or not (still kinda new to linux). SO anyway, I just moved the whole folder that had the .tar.gz file, and the extracted files to the trash. Now when I try to remove them from the trash it won't let me. And my permissions say I can create and delete files. Any ideas?

If you are using **gnome** as your window manager then try from the terminal ```
sudo rm -rf ~/.local/share/Trash/files/*
```

---

### Post by meindian523 on 2008-06-08
That's safe,it's only deleting files from your Trash.

---

