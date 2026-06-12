---
title: "can't boot into ubuntu. ( black screen without flashing cursor )"
date: 2015-09-13
forum: New to Ubuntu
---

### Post by kendinh8 on 2015-09-13
i got ubuntu 15. running along side with windows 10. it was running fine until yesterday. i just can't get into ubuntu. it shows the gnome boot screen then just black without any cursor flashing, nowhere to type in. even i tried reinstall from cd, it only show a ubuntu background pic with the status bar on top. Hope you can help me out of this. ( the windows 10 still works, )

---

### Post by dino99 on 2015-09-13
This is probably a graphic driver issue. Wich card/chipset is used and with which driver ?
When you get the black screen, try ctrl+alt+F2 to get a newer session via terminal. Then you can update/upgrade and makes some changes

---

### Post by kendinh8 on 2015-09-13
ctrl alt f2 doesn't work in my case. i press it and nothing happened.

---

### Post by Matty_Smith on 2015-09-15
What happens if you try to boot with the [nomodeset]("http://askubuntu.com/a/38834") parameter?

---

### Post by kendinh8 on 2015-09-16
its show the same black screen with nomodeset.

---

### Post by Geoffrey_Arndt on 2015-09-16
It's "extremely" unusual to get a black screen IF nomodeset is done correctly.     Did you replace the default text shown in Matty's link and then press ctrl + x to reboot?   The text has to be exact . . . suggest you try again very carefully.

---

### Post by kendinh8 on 2015-09-17
yeah, i followed the instruction carefully, it's really weird in my case cause i got problem with the graphic card before, but at least i can get the command line to solve it. this time is just black.

---

### Post by Geoffrey_Arndt on 2015-09-17
Well, unless I missed it . . we know nothing about your hardware.     Please provide hardware specs especially video system/chipset.   Also, do you recall any "changes" to system (installing significant software such as virtual machines, changing video drivers, etc.)?

---

### Post by sandyd on 2015-09-17
> **kendinh8 said:**
> i got ubuntu 15. running along side with windows 10. it was running fine until yesterday. i just can't get into ubuntu. it shows the gnome boot screen then just black without any cursor flashing, nowhere to type in. even i tried reinstall from cd, it only show a ubuntu background pic with the status bar on top. Hope you can help me out of this. ( the windows 10 still works, )

When you encounter the Ubuntu background pic with the status bar on top, is that when you have booted from the livecd, or after you have reinstalled?

Can you press Control + Alt + F2 then?

---

### Post by kendinh8 on 2015-09-18
i have intel core i5 4th gen , graphic card ati readon hd7770. 
i didn't make any changes to the system or install anything new. 
hopefully we can fix this cause I'm sick of using Windows now.

---

### Post by kendinh8 on 2015-09-18
i can boot from the dvd, but if i try to reinstall then ubuntu get stuck at the blank background. let me try Ctrl alt f2 from there

---

