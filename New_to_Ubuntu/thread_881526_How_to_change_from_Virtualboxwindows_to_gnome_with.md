---
title: "How to change from Virtualbox/windows to gnome with one key?"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by kramer65 on 2008-08-06
Hi,


I have Virtualbox installed now and just have one question. I normally have it on a different virtual desktop (or how do you call the optioin on the bottom right corner of gnome?), and I would like to be able to switch quick. I only use windows still of using the photomerge of Photoshop CS3 (there's nothing comparable) and sometimes I just need to see how far it is.

When I use ctrl+alt+right it works fine. But when I then do ctrl+alt+left it doesn't work. This is because it is then a function "in Windows" in photoshop actually (moving something in the image), which messes with my image, AND doesn't get me to the left desktop view in gnome.

Is there a way to easily to switch between windows and ubuntu in this case?

---

### Post by AdamWood on 2008-08-06
I use KVM for virtual machines instead of Virtualbox so my experience might not apply but in KVM the CTRL+ALT+F# keys are not grabbed by the virtual machine and still cause an action on the hosting machine. If you think about it this is what you want most of the time as Windows has no clue it is running in a virtual environment and when you press a key, any key, it rightly assumes that key was intended for Windows.

Since the CTRL+ALT+F# keys work though you can change between Virtual Terminals, not the same as the Virtual Desktops you see in the bottom corner. You might already know that your Gnome interface is running on VT7. With a bit of effort it should be possible to add a second gnome display on VT8 and then you can swap between them with CTRL+ALT+F7 and CTRL+ALT+F8. I've never had to set that up on Ubuntu though so hopefully someone else can fill in the Ubuntu specific details.

---

### Post by AdamWood on 2008-08-06
I found this page which looks like it has all the details.
[http://ubuntuforums.org/showthread.php?t=185555]("http://ubuntuforums.org/showthread.php?t=185555")

---

### Post by AdamWood on 2008-08-06
I found this page which looks like it has all the details.
[http://ubuntuforums.org/showthread.php?t=185555]("http://ubuntuforums.org/showthread.php?t=185555")

---

