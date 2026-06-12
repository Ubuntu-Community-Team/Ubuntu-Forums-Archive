---
title: "How to install older packages on Ubuntu 19.04?"
date: 2019-04-21
forum: New to Ubuntu
---

### Post by robertzaku1 on 2019-04-21
Hello! I just installed Ubuntu 19.04 today. I wanted to download and install Audacity, Blender, Steam and some other apps by using Ubuntu Terminal but i get errors. 
I tried:
sudo apt-get install blender
Failed
Then:
sudo apt install blender
Failed
Then:
sudo apt-get install blender -y
Failed
Then:
sudo apt install blender -y
Failed

Why so? Or maybe Ubuntu 19.04 is just out and few packages are upgraded? 
What to do? is it possible to install packages that are old and supported by older versions of Ubuntu on Ubuntu 19.04? 
Thanks!

---

### Post by howefield on 2019-04-21
What is the name of the Blender package have you downloaded ?

Steam and Audacity are both in the 19.04 repositories so should be fine for installing as above.

---

### Post by robertzaku1 on 2019-04-21
[ATTACH=CONFIG]283069[/ATTACH]

---

### Post by howefield on 2019-04-21
Then..

```
sudo apt install /home/USERNAME/Downloads/blender_2.79.b+dfsg0-4_amd64.deb
```

should work, assuming that you change USERNAME for your actual username, the package is in your Downloads folder and I've deciphered the package name from your poor image correctly. If not, amend the command accordingly.

The blender package downloadable from the Blender website works simply by unpacking the archive and running the executable.

PS. It's usually safer to install packages built specifically for the matching distribution version, packages built for 18.10 most likely will work in 19.04 but you get to keep all the pieces if they don't. ;)

---

### Post by Holger_Gehrke on 2019-04-21
According to [packages.ubuntu.com]("https://packages.ubuntu.com/search?keywords=blender&searchon=names&suite=disco&section=all") there is a package blender in Disco Dingo (19.04). Instead of just telling us that the installation failed, it would be nice to have the **exact** message apt or apt-get gave you. Installing older packages is a crap-shoot; old packages depend on old packages, so you end up with a strange mixture of old and new which might break some completely unrelated other part of the system.

Holger

---

### Post by robertzaku1 on 2019-04-21
thanks for the replies! it is helpful

---

### Post by monkeybrain20122 on 2019-04-21
Just download the bundle from blender, extract the tarball, click blender to start, that's it. Always up to date and you don't need to install anything.[https://www.blender.org/](https://www.blender.org/)

---

