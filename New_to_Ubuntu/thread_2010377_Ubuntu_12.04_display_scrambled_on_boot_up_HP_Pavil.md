---
title: "Ubuntu 12.04 display scrambled on boot up HP Pavilion dv9010 Laptop"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by dymensia3d on 2012-06-25
[INDENT]Greetings [IMG]http://www.linuxforums.org/forum/images/smilies/icon_smile.gif[/IMG]
I've downloaded Ubuntu 12.04 ( 3 different flavors so far )
( 12.04 desktop amd64 iso & Kubunto i386 & ubuntu 12.04 i386 ) and used universal usb installer ver 1.9.0.2 to install either versions with persistance on 16gb usb, and each time I restart with usb to boot linux it does display all the screens with text ( while loading ), detects and used my wireless mouse when it gets to the ubuntu desktop with the dots loading etc, the when it's finished loading the desktop, gui is all scrambled. [IMG]http://www.linuxforums.org/forum/images/smilies/icon_sad.gif[/IMG]. the mouse still working and I can tell there are icon areas and box areas to click on but the graphics are just lines of statically colors ( sorry about description - I can't really describe it ). Anyhow I have to hold down pwr button to get out / shut off laptop. I did try searching the forums for HP Pavilion dv9000 or dv9010 for issues relating and have come up empty. Searching elsewhere did offer a vga=7700 which i tried but same result. My laptop is a HP Pavilion Entertainment PC dv9010 with AMD Turion64 dual core with nVidia graphics ( Geforce Go 6150 ) 17" display, 2 gb ram.
I have installed Ubuntu on other sys's before and run it for long time but never on a laptop, so i am a noob [IMG]http://www.linuxforums.org/forum/images/smilies/confused.png[/IMG].
Sorry this so long, I need help please.
Thanks,
jt[/INDENT]

---

### Post by Arlough on 2012-07-08
I had this exact same problem with my dv9000 series laptop.
This is appearantly a problem with the latest NVidia Linux drivers.
If you install and choose ***_not_*** to autologin, you can start in 2d mode (why would I need a 3d desktop?) and then you can go into your divers and roll back to a previous on, or just keep using 2d mode until a fix comes out.

Hope this helps.

---

### Post by sudo smith on 2012-07-11
Same problem occurs for me when I start Libre Office. Ubuntu 2d seems to fix this.

---

