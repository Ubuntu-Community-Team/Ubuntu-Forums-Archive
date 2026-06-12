---
title: "Can I transfer my XP desktop to Ubuntu?"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by wolfmoses on 2012-08-21
Hi,

A friend has set up my XP Pro 250G hard drive as master, 80G hard drive as slave and installed Ubuntu on the master as a dual boot. I would like to easily access my XP Pro data on Ubuntu. Can I transfer the XP desktop icons to the Ubuntu desktop?

---

### Post by walker195 on 2012-08-21
im fairly shure you could access data like that but you cant run windows apps on ubuntu without wine so in theory its possible but not worth the trouble and time

---

### Post by mastablasta on 2012-08-21
> **wolfmoses said:**
> Can I transfer the XP desktop icons to the Ubuntu desktop?
 
 
no, you need to automount the windows disk/partition in Ubuntu first.
then you need to create shortcuts in ubuntu to it.

---

### Post by coldraven on 2012-08-21
Try using Nautilus to browse to your folder on the windows drive then use the "Add bookmark" function.

---

### Post by Mark Phelps on 2012-08-21
> **wolfmoses said:**
> Hi,

A friend has set up my XP Pro 250G hard drive as master, 80G hard drive as slave and installed Ubuntu on the master as a dual boot. I would like to easily access my XP Pro data on Ubuntu. Can I transfer the XP desktop icons to the Ubuntu desktop?

IF your purpose for transferring the icons is to easily launch Windows apps, that's not a simple as merely creating a shortcut.

Lots of Windows apps run poorly, or don't run at all, in Wine.  Before you go to all the trouble of installing Wine, you should check the Application Compatibility database at the WineHQ site to see how well your apps will work.  Anything you are going to rely on, that has a rating less than Gold, is going to be a frustrating experience using Wine.

---

