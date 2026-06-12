---
title: "Newbie problems"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by amz1 on 2013-03-10
Hi

I installed ubuntu 12.04 and i dont think my graphics card Nvidia GT 230 supports it as im having display problems. Ubuntu runs fine if i boot from USB but not as a a normal HDD boot.

---

### Post by LuisGMarine on 2013-03-10
> **amz1 said:**
> Hi

I installed ubuntu 12.04 and i dont think my graphics card Nvidia GT 230 supports it as im having display problems. Ubuntu runs fine if i boot from USB but not as a a normal HDD boot.

Could you please describe more in detail the exact problem(s) that you are encountering?  Nvidia GT 230 is most certantly supported in Ubuntu 12.04 ... you just need to install the correct propietery drivers.  When you boot the computer from the hard drive, what exactly happens?  Do you get a full working desktop, or are you stuck in a black screen .. maybe with a blinking cursor?

---

### Post by amz1 on 2013-03-10
I get up to the ubuntu logo and then 7 seconds later the screen just goes black when booting from HDD. i dont see the desktop or cursor unless im booting from USB

---

### Post by Bashing-om on 2013-03-10
amz1; Hi !

 graphics driver problem is a reasonable assumption.
Try this: Boot up ubuntu from cold boot, soon as the bios screen clears, depress the shift key -> grub menu>
Insure a "non recovery" kernel option is highlighted and press the "e"key for edit mode -> boot parameters; arrow down to the line similar to this "linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash"
; arrow across to the term "quiet splash" and insert the term "nomodeset" -without the quotes-; ctl+x to continue the boot process. GUI login -> user name and password -> desktop. Left side of screen is the launcher ->System Settings -> Additional Drivers [must have 'net connectivity ] Install the recommended driver.[INDENT=2]
Hope this helps

[/INDENT]

---

### Post by Lightning Dragon on 2013-03-10
Hello,

If Bashing-om's reply does not work (and I hope it does!), may I ask that when you installed Ubuntu did you click the option to install third-ware software during installation? If you need further instructions for Bashing's instructions instead, here is a nice link complete with *visuals*. 

[http://askubuntu.com/questions/147285/unable-to-boot-into-ubuntu-12-04](http://askubuntu.com/questions/147285/unable-to-boot-into-ubuntu-12-04)

Hopefully Bashing's advice works for you!

---

