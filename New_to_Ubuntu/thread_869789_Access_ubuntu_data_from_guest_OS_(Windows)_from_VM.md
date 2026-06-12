---
title: "Access ubuntu data from guest OS (Windows) from VMWARE"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by kramer65 on 2008-07-25
Hello,


I just installed vmware with windows on it and that works fine. Now I want to move a file from my ubuntu desktop to my vmware/windows desktop. But if I go to "my computer" in windows, it doesn't recognise the hard physical hard drive.

How would I do this?

---

### Post by aeiah on 2008-07-25
windows thinks its on its own computer, and isnt aware of ubuntu at all. what you need to do is set up a shared partition or folder on ubuntu, and connect to it in windows like you would if windows was on another computer on the network. 

for ubuntu to share with windows you need to set up samba. there should be a guide on these forums detailing this, and i think there's even a guide on here for detailing how to set up a samba share for a vmware guest specifically.

you'll also need to make sure your windows guest has a virtual ethernet (or ethernet passthrough or whatever its called). basically, if you can see the internet from windows, then its set up already.

---

