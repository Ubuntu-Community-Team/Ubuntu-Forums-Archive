---
title: "editing the heart of linux"
date: 2008-12-29
forum: Programming Talk
---

### Post by jtech55 on 2008-12-29
How would I edit the "heart" of a linux-ubuntu **.iso**, so when the beginning installation process of ubuntu is complete, "so and so" packages would already be installed (marked green in the synaptic package manager)?? like firefox

---

### Post by catchmeifyoutry on 2008-12-29
Don't manually edit .iso files, but use a program to create a custom installation.
Quick google: [http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys](http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys)
Might be a better way, though.

---

### Post by jtech55 on 2008-12-30
thanks, but this is not exactly what I'm looking for though. 
what you gave me is basically a tutorial on copying my version of linux +it's packages onto a livecd. what my intention is, is to create a livecd with specific packages installed. ex: pidgin, awn, **not** thunderbird, **not** etc. Instead of creating a livecd with thunderbird and all the other packages i have on my main version of linux ubuntu. thank you though.

:-({|=

---

### Post by Sorivenul on 2008-12-30
*Actually*, Remastersys will take any setup you have and put it on a CD/DVD. If you remove things like Pidgin or Thunderbird, or replace GNOME with GNUstep, and add conky and AWN, the image you will have at the end will match your current setup. 

Download it, try it. If you don't want to copy your current setup or modify it just to use Remastersys, just install Ubuntu in a virtual machine (probably using VirtualBox), and customize that install, run Remastersys, burn your ISO and be done. :D

It's simple, and quite a few people around here use it, including myself.

If you decide against it after trying it, look at [this thread]("http://ubuntuforums.org/showthread.php?t=852868") on how to make your own custom Linux distribution based on Ubuntu (or another distribution).

Good luck! ;)

---

