---
title: "Wireless Not Working"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by vabthegr81 on 2008-10-12
Hey guys,

I installed Ubuntu 8.04, Hardy Heron on my laptop (HP 520 notebook) yesterday. Everything else seems to be working fine, except the wireless.

I have a switch for activating the wireless adapter, that indicates a blue light when its on (button is pressed once). The problem I'm facing is the blue light just doesn't show up, inspite of pressing the button again and again. I'm unable to find the root of this problem. Earlier I had Win XP installed and it was working fine. Now the blue light just doesn't switch on. I tried all measures for activating the adapter yesterday but to no avail(including installing ndiswrapper).

Can somebody please help me out with this?
I have an Intel PRO Wireless Driver.

---

### Post by itix on 2008-10-13
Ndiswrapper should work according to [http://www.google.com](http://www.google.com)

This should get you going: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I'm sure there are native drivers as well, but NDISwrapper is usually the easier way to do things and since I figured you were new to ubuntu, lets stick with NDISwrapper.

EDIT: oops, I'm an idiot. I didn't read your post. How far do you get with NDISwrapper??

---

### Post by superprash2003 on 2008-10-13
please post output of iwconfig and lshw -C network

---

