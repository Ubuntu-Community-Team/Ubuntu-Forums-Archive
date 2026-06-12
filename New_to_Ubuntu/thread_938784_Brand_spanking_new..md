---
title: "Brand spanking new."
date: 2008-10-05
forum: New to Ubuntu
---

### Post by sksnyder on 2008-10-05
Complete newbie here! Windows user for years. Time to mix it up now. I installed Ubuntu on top of Windows. First attempt resulted in a Chinese language being installed. I did not know how to uninstall so I removed the Ubuntu folder from my C: Drive in Vista, and performed a system restore. I than reinstalled the CD for Ubuntu, correctly this time. Only problem i have now is; at the boot up logger I have 2 Ubuntu OS to boot from. Is there a way to eliminate the version I will not use?

---

### Post by Sef on 2008-10-05
So you used Wubi to install Ubuntu?

---

### Post by bodhi.zazen on 2008-10-05
I believe you need to edit 

edit C:\boot.ini 

And remove the line to the old Ubuntu.

You should be able to open the file with Notepad and I would back it up first in case you make a mistake ;)

---

### Post by Sinkingships7 on 2008-10-05
After you installed Ubuntu with Wubi, you probably updated, correct? In that case, there's a good chance that the other option is for an older kernel, 'cause you updated your old one. I would suggest keeping it there, in case one kernel fails you can fall back to the other.

If you really want to get rid of it, then boot up windows and open a Run prompt. Type 'msconfig' without the quotes and press enter. Go to the tab that says 'BOOT.INI' and delete the entries which contain the Ubuntu-related text you want gone.

Be sure to make a restore point before doing this, though I think Windows might do that automatically.

---

### Post by sksnyder on 2008-10-06
That is exactly how I installed it. I am not familiar with the code, i'll stick to gui for now. Any good sources for code and utilizing Ubuntu to its great potential?

---

