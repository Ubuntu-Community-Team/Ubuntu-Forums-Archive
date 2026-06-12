---
title: "Installing Bluez 5.x in Ubuntu(with Gnome 3.10)"
date: 2013-10-31
forum: New to Ubuntu
---

### Post by yehowraah on 2013-10-31
I recently upgraded to Gnome 3.10 in Ubuntu 13.10 at Unity's great expense(not that I mind). Everything's been going smoothly, but after snooping around a bit I noticed that I still appear to be  stuck with Bluez 4.101, while Gnome 3.10 supposedly made the jump to bluez 5.x...? Upon realizing this, I hopped over to the Bluez website, DLed the TAR, and in anticipation for the upgrade, I hopped into the Software Center and uninstalled Bluez...well, that didn't work out so well. For some some reason beyond my paltry understanding, removing bluez broke gdm, forcing me to do a reinstall, but that's kind of besides the point.

Anyways, after reinstalling GDM, I'm back in business. I compiled and installed the tarbal (seemingly)without a hitch, but I still appear to be stuck with the same old Bluez4.101. I feel like I followed the instructions to the letter, but by all appearances it didn't actually install? What have I done wrong here? I'm sure I've messed up somewhere, but where?

---

### Post by anton_bors on 2013-12-17
As I understood the plans of Ubuntu, bluez5 is in state of blueprint for ubuntu.
Bluez5 has a lot of API-Changes, so it isnt as easy as you expected. 
I dont know it exactly, but only the unchanged elements of the API can be used at this point of time. 

I also hope, that the next release contains bluez5 so my headphones can work correctly :)

Hope this helps a little bit ( but it doesnt improve the answer :( )

PS: Visit [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1162781](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1162781)

---

