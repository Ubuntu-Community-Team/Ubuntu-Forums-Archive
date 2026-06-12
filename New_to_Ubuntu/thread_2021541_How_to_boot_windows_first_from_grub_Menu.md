---
title: "How to boot windows first from grub Menu"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by prohank on 2012-07-09
I am really sorry if this has been posted earlier but i checked it and I couldn't find it.
So the problem is..
I want to boot windows first from the grub menu rather than ubuntu and also want to change the boot time.
I googled it and found some results but they are not working as they are supposed to.

In one of the commands "sudo gedit /boot/grub/menu.lst"
the menu.lst file opens without any text.
and 
in this method "sudo vi /etc/default/grub"
the file opens but i can't edit it.

I am completely new to linux so don't anyhing about this.Please help.
Using ubuntu 12.04.

---

### Post by prohank on 2012-07-09
I forgot to say I used sudo su too.

---

### Post by mastablasta on 2012-07-09
easiest way i know is to install ubuntu tweak and then change the boot order in it.

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by NikTh on 2012-07-09
> **prohank said:**
> 

In one of the commands "sudo gedit /boot/grub/menu.lst"
the menu.lst file opens without any text.
and 
in this method "sudo vi /etc/default/grub"
the file opens but i can't edit it.

I am completely new to linux so don't anyhing about this.Please help.
Using ubuntu 12.04.

menu.lst was on grub legacy. Grub2 has /boot/grub/grub.cfg 

If you want to do your job easy and change more things and not only boot order or boot time , install grub-customizer. Its an excellent program and this is an excellent tutorial--> [http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by mastablasta on 2012-07-09
woops sorry it's actually with grub customizer, but its from the same person as Ubuntu tweak i believe:

PPA: [http://ubuntu-tweak.com/source/danielrichter2007-grub-customizer/](http://ubuntu-tweak.com/source/danielrichter2007-grub-customizer/)
video showing how to use it: [http://www.youtube.com/watch?v=In0-_VF5Pe8&feature=related](http://www.youtube.com/watch?v=In0-_VF5Pe8&feature=related)
and how to (here on forums): [http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

just in case you want to change something else aside form the boot order ;-)

---

### Post by prohank on 2012-07-11
Thanks a lot mates.
That was really very helpful

---

### Post by black veils on 2012-07-11
and for anyone else looking to do this, **startupmanager** can be used. though Ubuntu seems to add extra lines which upsets the actual system you choose as default, its usually about 2 off.

---

### Post by Mark Phelps on 2012-07-11
> **black veils said:**
> and for anyone else looking to do this, **startupmanager** can be used. though Ubuntu seems to add extra lines which upsets the actual system you choose as default, its usually about 2 off.

Startupmanager has problems handling recent updates to GRUB.

You're better off using Grub-Customizer.

---

### Post by NikTh on 2012-07-11
> **black veils said:**
> and for anyone else looking to do this, **startupmanager** can be used. though Ubuntu seems to add extra lines which upsets the actual system you choose as default, its usually about 2 off.

If you mean this startup-manager ... i think is dead project --> [https://launchpad.net/startup-manager](https://launchpad.net/startup-manager)

---

