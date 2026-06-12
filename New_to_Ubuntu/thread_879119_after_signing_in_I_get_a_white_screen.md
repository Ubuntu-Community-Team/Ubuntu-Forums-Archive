---
title: "after signing in I get a white screen"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by MeTylerDurden on 2008-08-03
[SIZE="3"][/SIZE][COLOR="DimGray"][/COLOR]I had this same problem before and there is no ryhme or reason.. just happens . Had to reinstall.

---

### Post by MeTylerDurden on 2008-08-03
Boots fine in failsafe Gnome.. where I am now

---

### Post by dje on 2008-08-03
Reboot and after bios press escape to get to the grub menu. Select the recovery mode and press enter, let it boot and when a menu comes up select 'fix x' or something similar. let it do that and then when the menu reappears select 'resume normal boot'. try logging in normally after doing that

dje

---

### Post by MeTylerDurden on 2008-08-03
OK, tried that and I still get white screen ,  but my mp3 on my desktop play if my mouse is over them - even though I can't see them ..still a white screen

---

### Post by shad0w_walker on 2008-08-03
It sounds like something is going wrong with compiz. Try logging in and doing this, though you will have to work blind so to speak.

1. Login
2. Wait for it to finish loading up then press Alt + F2
3. Type this command and press enter:  ```
killall compiz.real
```
4. See if this sorts out the problem.

If it does sort out the problem, then you can make it stop loading compiz by going to System > Preferences > Appearance and selecting None from the Visual Effects tab.

---

### Post by MeTylerDurden on 2008-08-03
I did exactly as you said... and all went well .    one thing though: when I checked visual effects was on none and when restarted white screen again.
running a little strange 2..

---

### Post by MeTylerDurden on 2008-08-03
but can see the desktop and all - worked like a charm

---

### Post by MeTylerDurden on 2008-08-03
[SIZE="3"][COLOR="DimGray"]ok, 3rd reboot still going into white screen , then alt +f2  and type killall compiz.real  gets me into ubuntu regular screen with my desktop.   I have none selected under syst-pref-appearance-visual effects  ..    How can I get it to reboot to normal without typing the  kill code. .. 



the liberator who destroyed my property has realigned my perception[/COLOR][/SIZE]

---

### Post by kk0sse54 on 2008-08-03
You have to make sure that metacity becomes your default window manager everytime you boot up. The command to replace compiz with metacity would be ```
metacity --replace
```

---

### Post by MeTylerDurden on 2008-08-03
> **C!oud said:**
> You have to make sure that metacity becomes your default window manager everytime you boot up. The command to replace compiz with metacity would be ```
metacity --replace
```

Ok, I went to terminal and the metacity --replace didn't seem to go , but went to synaptic and manually removed all compiz then checked metacity and both were installed just added themes .. then restarted and wow. WOW back to normal.. home sweet home.. no more white screen .. 


I don't ever wanna come back down off this cloud

---

