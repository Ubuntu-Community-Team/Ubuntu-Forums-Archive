---
title: "Ubuntu 8.04 no login - help change res ?"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by gcoats23 on 2008-10-25
So my problem is with a friends computer that i tried to put 8.04 64bit on- All i had was his tower so i used my I/O hardware and monitor- well everything went great- he came by to pick up the pc and i showed him how great it was.....then he took it home and pluged in his monitor and suddenly he had no login screen- it just says unsupported video resolution- So i need to know how to boot up his system into a terminal-(i had him try pressing ctrl+alt+f1 , he said it looked like a terminal but everytime he typed it would say unknown character-  and secondly How do i change the resoulution in the xorg file-
any help would be great
garrett

---

### Post by bpowell2005 on 2008-10-25
> **gcoats23 said:**
> So my problem is with a friends computer that i tried to put 8.04 64bit on- All i had was his tower so i used my I/O hardware and monitor- well everything went great- he came by to pick up the pc and i showed him how great it was.....then he took it home and pluged in his monitor and suddenly he had no login screen- it just says unsupported video resolution- So i need to know how to boot up his system into a terminal-(i had him try pressing ctrl+alt+f1 , he said it looked like a terminal but everytime he typed it would say unknown character-  and secondly How do i change the resoulution in the xorg file-
any help would be great
garrett

How about hitting ESC right when the computer starts to boot (in the Grub menu)...then select "Ubuntu - Kernel blah blah blah -- RECOVERY"

I've had to do this before, the Recovery console usually asks to reconfigure the x-server....just say "yes" and you're back in business...you can then boot normally after that.

---

### Post by gcoats23 on 2008-10-25
Wow thank you so much, I cant belive i didnt know about that, hun- well i get to talk to my friend tonight, Ill have him do that- thanks again-
garrett

---

