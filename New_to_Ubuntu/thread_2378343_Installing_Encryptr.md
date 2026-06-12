---
title: "Installing Encryptr"
date: 2017-11-22
forum: New to Ubuntu
---

### Post by mail-wz6b3 on 2017-11-22
Hi good people of Ubuntu
 
 
 I have just installed Ubuntu 17.10 on a Dell Laptop.
 
 
 I have a strange problem – when trying to open a program I have installed called Encryptr, nothing happens?
 
 
 Here is what I have done;
 
 
 On Encryptr/Spideroaks homepage, I have downloaded the .deb file for Debian 64 bit.
 Then I have asked the Software Center to install it, and after getting a message of a successful install, I try to run the program, but nothing happens.
 
 
 I have tried to uninstall it, and do the process again but this time with Gdebi, but with the same result.

 
 
 Do any of you know what I have to do to run the program?
 
 
 I can add, that I have the same problem with the Synaptic packet manager. This I have installed from  the Software Center, but also here, nothing happens when I click on the program.

 
 
 Please excuse me, if I am a little hard to understand, but English is not my first language.
 
 
 Best Regards

---

### Post by rivasdom on 2017-11-22
What you have to do is launch it from the terminal to see if there are any errors reported. Post the output here. Maybe you are missing some dependencies.

---

### Post by mail-wz6b3 on 2017-11-23
Hi
Thanks for the answer.
I try to copy/paste the output of the terminal here;

sandersson@sandersson-Inspiron-5767:~$ encryptr
encryptr: kommando ikke fundet
sandersson@sandersson-Inspiron-5767:~$ synaptic
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Segmentfejl (smed kerne)
sandersson@sandersson-Inspiron-5767:~$ 


Kommando ikke fundet = Command not found.
Segmenrfejl = Segmentation error
(Smed Kerne) = Is hart to translate but "Kerne" is kernel.

Hopes this helps.

Have a nice day :-)

---

### Post by Geoffrey_Arndt on 2017-11-23
Suggest to try switching back to the xorg server.    Ubuntu 17.10 runs Wayland now as the default.    But not all programs like Wayland (yet).   On your login screen, there is an option to choose Xorg and it will be used instead of Wayland.   By next LTS release - this should be much improved.

---

### Post by mail-wz6b3 on 2017-11-25
Hi
Sorry for my late reply.
I tried the change you suggested, and it solved the problem with the Synaptic packet manager.
I thing mabye Encryptr is just not made for 17.10 or something like that.
I will just have to settle with KeePassX.
Thant&#7729; you for your time and help.

---

