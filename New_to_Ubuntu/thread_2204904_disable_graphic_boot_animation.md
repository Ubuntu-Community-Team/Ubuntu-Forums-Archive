---
title: "disable graphic boot animation"
date: 2014-02-10
forum: New to Ubuntu
---

### Post by opfeld on 2014-02-10
I am running lubuntu 12.04 for my xbmc box and would like nothing but a black screen when I boot up, right now I get this image upon boot up and shutdown (attached).  I have gone into /etc/default/grub and set "quiet splash" but it still appears.  Is it plymouth or something else that is responsible for the graphics?

PS the only image I could find quickly was a kubuntu, but it is the same idea with my lubuntu system

---

### Post by opfeld on 2014-02-10
doing some further digging apparently it is plymouth that is doing this fancy boot up and it is so ingained in linux you cant cleanly remove it from the system.  I guess I will just use mint xfce instead, it comes with a black boot screen by default

---

### Post by Dennis N on 2014-02-11
> **opfeld said:**
> I have gone into /etc/default/grub and set "quiet splash" but it still appears.  

You want to keep the word 'quiet' and remove the word 'splash'. Then you should not get the image (called a splash screen).

To test, at the grub menu press **e** for edit before the boot continues. Move down with cursor keys to the boot line with **quiet spash** in it, and delete the word **splash**. Ctrl+X will continue the boot up.

When you make changes in /etc/default/grub, be sure to run **sudo update-grub** afterwards.

---

