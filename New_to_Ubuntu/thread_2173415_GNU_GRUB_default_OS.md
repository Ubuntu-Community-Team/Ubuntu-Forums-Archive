---
title: "GNU GRUB default OS"
date: 2013-09-09
forum: New to Ubuntu
---

### Post by deleyd-y on 2013-09-09
OK I have grub-install -v says: 2.00-13ubuntu3

 I've tried editing /etc/default/grub, changing the line GRU_DEFAULT=0
tried setting that to 1, didn't do anything. 
Tried 4, didn't do anything. 
Tried 'Windows 7 (loader) (on /dev/sda2)'
Tried "Windows 7 (loader) (on /dev/sda2)"

now I'm just irked nothing changes the default it boots to. How do I change the default?

---

### Post by Frogs Hair on 2013-09-09
Hello and Welcome

I take you are referring to boot order and if not please clarify. You may have seen the following links, but I cant be sure of what tutorial you were following. Methods may vary depending on Ubuntu version.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://askubuntu.com/questions/199129/dual-booted-ubuntu-12-04-with-windows-7-question-about-boot-order-and-where-exa](http://askubuntu.com/questions/199129/dual-booted-ubuntu-12-04-with-windows-7-question-about-boot-order-and-where-exa)
[http://ubuntuhandbook.org/index.php/2013/08/change-boot-order-in-ubuntu-13-10-13-04/](http://ubuntuhandbook.org/index.php/2013/08/change-boot-order-in-ubuntu-13-10-13-04/)

---

### Post by deleyd-y on 2013-09-09
The missing step was I needed to do "update-grub" after editing /etc/default/grub and changing the line GRUB_DEFAULT=0

---

### Post by Patrick_Denson on 2013-09-17
> **Frogs Hair said:**
> Hello and Welcome

I take you are referring to boot order and if not please clarify. You may have seen the following links, but I cant be sure of what tutorial you were following. Methods may vary depending on Ubuntu version.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://askubuntu.com/questions/199129/dual-booted-ubuntu-12-04-with-windows-7-question-about-boot-order-and-where-exa](http://askubuntu.com/questions/199129/dual-booted-ubuntu-12-04-with-windows-7-question-about-boot-order-and-where-exa)
[http://ubuntuhandbook.org/index.php/2013/08/change-boot-order-in-ubuntu-13-10-13-04/](http://ubuntuhandbook.org/index.php/2013/08/change-boot-order-in-ubuntu-13-10-13-04/)

By using the search, I believe this is what I was looking for to change my boot order. Thanks for posting

---

### Post by Patrick_Denson on 2013-09-17
That worked, once again thanks

---

