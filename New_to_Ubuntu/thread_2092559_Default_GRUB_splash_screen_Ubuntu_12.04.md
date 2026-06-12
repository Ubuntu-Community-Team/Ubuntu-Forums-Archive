---
title: "Default GRUB splash screen Ubuntu 12.04"
date: 2012-12-08
forum: New to Ubuntu
---

### Post by Aleksej on 2012-12-08
I tried the XFCE4 desktop manager for some reasons and decided to stick with Unity. The thing is, when I installed XFCE4 it changed the GRUB menu background from the plain purple splash screen into some spacey pic. I'd like to get the default plain purple GRUB menu. How can I do that?

---

### Post by cottfcfan on 2012-12-08
You need to edit the /etc/default/grub file.
```
sudo gedit /etc/default/grub
```
And edit the line that begins:
GRUB_BACKGROUND=/
Point it to the path of the background you want.
Then run update-grub & reboot.

---

### Post by mungatsuma on 2012-12-08
You can also try Grub Customizer which has a simple GUI for that. More info can be found here [http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html) and here for how it works [http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183). Hope this will help, the first suggestion though by @cottfcfan  is better if you are comfortable with the Command Line Interface and editing configuration files.

---

### Post by rburkartjo on 2012-12-08
or you might have to add the line as cott mentioned

also add "" here is an example form my grub

GRUB_BACKGROUND="/home/ray/121143.jpg"

also i put the .jpg i want to use in my home folder first.

---

