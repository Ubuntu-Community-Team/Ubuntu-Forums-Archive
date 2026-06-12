---
title: "[SOLVED] Screen resolution"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by Bigbob22 on 2008-07-18
I installed an update than shutdown my computer. When I turned my computer back on the screen resolution 800 x 600 which is not my screen resolution and my ATI Radeon Mobility x1400 driver isnt working so I enabled it but it still isnt working and it wont let me change my screen resolution back to 1280 x 800. This happened before when i was messing with xorg but i just went bck to a back up file of xorg. this time there is no back up that is correct. How do i fix this? I'm new to linux and i am not that good with the terminal so please put it in non technical terms.  Sorry for the horrible grammer and short hand and spelling. Im just in a hurry and really nervous and scared that my computer cant be fixed.

---

### Post by Canis familiaris on 2008-07-18
Reboot.
Boot into Recovery Mode.
It will boot on and give you the list of choices.
Choose the option to fix your X-server.

Hopefully you'll get back your resolution.

Install ATi drivers again.

Hope this helps.

---

### Post by Bigbob22 on 2008-07-18
uh can u tell me how to do all of that?

---

### Post by alienexplorers on 2008-07-18
Reboot your computer as you normally would.
When it starts up it will get to the grub loader.
At that point you have 3 seconds to hit <ESC> key.
Select Recovery mode to boot into.
during the boot tyou will get an option to fix your x-server using xfix.
select xfix and hit enter or yes (don't remember which).
Let the system run xfix.
when you get to your screen see if you have the correct resolution and your video card is loaded.
If all is fine, reboot in normal mode (DO NOT HIT THE <ESC> KEY).
Let the machine boot and see what happens.

---

### Post by Bigbob22 on 2008-07-18
Thank you guys so much. The screen resolution is back to normal and it says the ATI Graphics card is in use. However, none of the compiz effects are working and other programs that need the graphics card are working (ex: avant window manager). Please help and thanks so much for the previous help.

---

### Post by LittleLORDevil on 2008-07-18
How did you install your driver?  I have the exact same graphics card as you. If you used the default then it won't work, you have to go to restricted drivers option and enable it through there.

---

### Post by Bigbob22 on 2008-07-18
When i installed ubuntu it just worked.

---

### Post by LittleLORDevil on 2008-07-18
To get compiz go to System>Administration>Hardware Drivers enable the driver for your card install then reboot.  Then you will have compiz

---

### Post by Bigbob22 on 2008-07-18
It is already enabled but it isnt working. I'll try to reboot again to see what happens.

---

### Post by LittleLORDevil on 2008-07-18
Make sure the box is checked it will say in use but not by the driver you want it to.  Make sure the box is checked then reboot.

---

### Post by Bigbob22 on 2008-07-18
Okay. So I reinstalled the ati driver (fgrlx or some thing like that, I forgot the name) and then rebooted. Then it said it was not in use so I enabled it and then rebooted again and everything is working. Thanks for all the help!

---

### Post by LittleLORDevil on 2008-07-18
No problem, this card gave me a lot of trouble before so I learned a lot through all of the versions of Ubuntu for it, 8.04 is by far the easiest for it.

---

