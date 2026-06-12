---
title: "New install of 12.10"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by kslimmer on 2013-03-09
Rebuilt my Compaq N610 with 12.10.  After install and reboot, I can login, but then just a blank splash screen.  Mouse works, did an update by CTRL-ALT-F1.  I'm sure the answer in somewhere in the forum, I just haven't found it yet

thanks

Ken

---

### Post by fiodev on 2013-03-09
do the ctrl alt f1 things again and type startx

---

### Post by kslimmer on 2013-03-10
Thanks, sorry didn't fix it.  I think its a video driver problem, but how do I fix it?

Ken

---

### Post by Bashing-om on 2013-03-10
kslimmer; Hi !
A graphics driver problem is a reasonable assumption.
Try this: Boot up ubuntu from cold boot, soon as the bios screen clears, depress the shift key -> grub menu>
Insure a "non recovery" kernel option is highlighted and press the "e"key for edit mode -> boot parameters; arrow down to the line similar to this "linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash"
; arrow across to the term "quiet splash" and insert the term "nomodeset" -without the quotes-; ctl+x to continue the boot process. GUI login -> user name and password -> desktop. Left side of screen is the launcher ->ubuntu Software Center ->Software Sources(menu option on top task bar) ->Additional Drivers (tab in Software Sources) [must have 'net connectivity ] Install the recommended driver.[INDENT=5]
Hope this helps

[/INDENT]

---

### Post by Frogs Hair on 2013-03-10
Attempt the commands from  the gnome terminal (CTR-ALT+T)  and if it doesn't open use tty ( CTR-ALT+F1)  

First try the Unity support test. ```
/usr/lib/nux/unity_support_test -p
```

If unity is supported  try the following ```
setsid unity
```

If not try Xubuntu or Lubuntu. 

 (CTR+ALT+F7 Returns to desktop GUI from tty)

---

