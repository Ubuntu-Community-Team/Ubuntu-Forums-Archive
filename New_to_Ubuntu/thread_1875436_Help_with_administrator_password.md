---
title: "Help with administrator password"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by ixtok on 2011-11-04
I am new to using ubuntu 11.10. I inadvertently changed my user status from administrator to standard. Now of course I cant do anything which requires the administrators password. How can I easily change myself back to administrator or should I reinstall?

---

### Post by wojox on 2011-11-04
Reboot, hold down the left shift kety and boot into recovery. You will log in to a root terminal and you can change it back.

---

### Post by ixtok on 2011-11-04
Thanks for the reply. I can reboot and through grub get to the recovery area. I assume I choose "root" which gives me a terminal type entry area. What do I type in to reset my user status from standard to administrator and then what do I type to close the shell and return to  normal?

---

### Post by kroq-gar78 on 2011-11-04
> **ixtok said:**
> Thanks for the reply. I can reboot and through grub get to the recovery area. I assume I choose "root" which gives me a terminal type entry area. What do I type in to reset my user status from standard to administrator and then what do I type to close the shell and return to  normal?
Want you want to type now is ```
passwd [account name]
```. So, if your account name was "ixtok", then you would type in ```
passwd ixtok
``` in the recovery console and set your new password. It won't show the characters so that nosy eyes (that sounds strange...) won't discover your password *too *easily.

---

### Post by ixtok on 2011-11-04
Thanks for the reply. I used the commands given and get a "Authentication token manipulation error" after typing my password after the prompts.

Is this easily fixed or would it be easier to reinstall or try a different distro?

---

### Post by themissinglinka on 2011-11-04
hi. i think i've done something wrong with my administrative privileges too, i seem to be the administrator but i cant download anything from the software center or updates -it says i dont have the privilege. i can get stuff of source forge, but im padawan not a fully SUDO jedi so i cant quite do binaries yet. is it something to do with the PUB license? also im running the plazma on kubuntu 10.11

---

### Post by ixtok on 2011-11-04
Thanks those of you attempting to help. The quickest and easiest solution to my problem was a reinstall which I just did.

---

### Post by themissinglinka on 2011-11-08
im going to do a complete re-install and download the updates/patches _after _i've got an OS. im running gnome now and i think because i gave my good 'ol cq-60 less stuff to think about while it was getting a mind transplant it may work for the new kde. thanks for the pointers guys. ):P

---

