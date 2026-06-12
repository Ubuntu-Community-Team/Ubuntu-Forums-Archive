---
title: "squashfs error HELP PLZ!!"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by uhhuh on 2008-05-12
i'm trying to install ubuntu on a pc with no os but during the install i get a squashfs error is there anyway to get ubuntu running w/o reburning/redownloading [cant redownload for a while and want this on my pc soon. i read somewhere that the error can be fixed by making ide=nodma how exactly do i do that???

---

### Post by uhhuh on 2008-05-12
[bump] plz guys i really need some help

---

### Post by Monicker on 2008-05-12
Press the Escape key while Ubuntu is booting, before the splash screen comes up.  A text menu will come up.  Press 'e' on the keyboard.  The menu will change. Arrow down so that the line starting with kernel is highlighted.  Press 'e' again.  At the end of the line put the ide=nodma option. Press Enter.  Press 'b' to continue booting.

I have attached some screenshots of the text menus, which should help you.

---

### Post by uhhuh on 2008-05-13
i press escape b4 the cd boots but i dont get a text screen...

---

### Post by llamakc on 2008-05-13
Press the escape key WHILE it is booting.

---

### Post by Monicker on 2008-05-13
You are trying to boot from the live cd when you get the error?  When the menu comes up that asks for if you want install, select F6, and then put ide=nodma at the end of the line.

---

### Post by uhhuh on 2008-05-13
i believe i tried that too

---

### Post by Monicker on 2008-05-13
> **uhhuh said:**
> i believe i tried that too

You believe you tried what too?  You need to be a lot more specific about what you are doing.

---

### Post by uhhuh on 2008-05-13
sorry i'm typing on wii so i try to be brief. i've tried all methods with no luck :-[

---

### Post by mlentink on 2008-05-13
uhhuh,

Would you please either continue with this thread or with [the other one]("http://ubuntuforums.org/showthread.php?t=793205")?

---

