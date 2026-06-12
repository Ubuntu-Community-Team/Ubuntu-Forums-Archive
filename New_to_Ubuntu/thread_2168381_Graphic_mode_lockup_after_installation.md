---
title: "Graphic mode lockup after installation"
date: 2013-08-17
forum: New to Ubuntu
---

### Post by robert_hill2 on 2013-08-17
I have just installed 13.04 on the following system:
Dell Dimension 8200 desktop 
Pentium 4 cpu  2.00 Ghz
500 Gb hard drive
Radeon 9200 PRO Family display adaptor

The installation seemed to be straightforward but when the  system was restarted, it is locked up and continuously changing graphic modes. How do I get out of this? I am a complete beginner with Linux.

---

### Post by ajgreeny on 2013-08-17
I think your graphics card is simply not powerful enough to run unity.

With that spec try Lubuntu or Xubuntu instead.  No need to reinstall everything, just add the appropriate **lubuntu-desktop** or **xubuntu-desktop** package using the command line if necessary ```
sudo apt-get install xubuntu-desktop
``` and also if you want remove the unwanted ubuntu packages following the info at [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php) in the **Pure *ubuntu** in the Playing around section in the left hand pane.

---

### Post by robert_hill2 on 2013-08-17
Some additional information: I had to use nomodeset to get installation going. Is this relevant?

---

### Post by robert_hill2 on 2013-08-18
Could someone tell me the specifications I should have in mind if I upgrade the graphics card shown at the start of this thread? I have no particularly severe graphics requirements (such as gaming).

Thanks

---

