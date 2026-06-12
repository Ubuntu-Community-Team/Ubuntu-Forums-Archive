---
title: "More webcam help needed"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by Redrebel54 on 2008-06-09
Hi people. New to Ubuntu, but not quite new to unix OS's, although very novice in them. However, Having had my windoze systems constantly crashing around my ears, and having made a very nice living supporting windoze system in all forms from v3.0 onwards, I finally decided that it was time to kick it out of my private life for good. Oh, I still think that windoze id gonna earn me more money over the next few years, and long may it continue to be such a heavily intensive admin system. The more work it takes to administer it, the more money I can make. Rock on.

BUT. In my own life I want an OS that is manageable. So, 3 weeks ago I took the plunge. Bye bye XP Pro. Hello Ubuntu. Now I call that a smart move. However, the one device I cannot get to work properly is a webcam. Yep, it's one made in Taiwan, China, Korea, someplace over there, specifically for the UK Argos shopping conglomorate. It's branded under the name Mikomi and the model is an 1.3mp (I think that means 1.3 Mpix for the photo quality) however a lsusb shows up with
root@Anfield:/home/les# lsusb
Bus 005 Device 005: ID 04f2:a133 Chicony Electronics Co., Ltd 

Anyone any idea for the driver for this. Cheese sort of works, so the device can be seen.Camorama doesn't recognise the device. Anyone any ideas (yeh, I know, get a new, "proper" webcam :) )

---

### Post by stalkier on 2008-06-09
> **Redrebel54 said:**
> Hi people. New to Ubuntu, but not quite new to unix OS's, although very novice in them. However, Having had my windoze systems constantly crashing around my ears, and having made a very nice living supporting windoze system in all forms from v3.0 onwards, I finally decided that it was time to kick it out of my private life for good. Oh, I still think that windoze id gonna earn me more money over the next few years, and long may it continue to be such a heavily intensive admin system. The more work it takes to administer it, the more money I can make. Rock on.

BUT. In my own life I want an OS that is manageable. So, 3 weeks ago I took the plunge. Bye bye XP Pro. Hello Ubuntu. Now I call that a smart move. However, the one device I cannot get to work properly is a webcam. Yep, it's one made in Taiwan, China, Korea, someplace over there, specifically for the UK Argos shopping conglomorate. It's branded under the name Mikomi and the model is an 1.3mp (I think that means 1.3 Mpix for the photo quality) however a lsusb shows up with
root@Anfield:/home/les# lsusb
Bus 005 Device 005: ID 04f2:a133 Chicony Electronics Co., Ltd 

Anyone any idea for the driver for this. Cheese sort of works, so the device can be seen.Camorama doesn't recognise the device. Anyone any ideas (yeh, I know, get a new, "proper" webcam :) )

The onl thing I can think of off hand is to force install the XP driver using ndiswrapper. There are a lot of Tutorials on how to install windows drivers in linux. Perhaps someone else will have a better idea than me. Personally I use a Logitech IM webcam. It work flawlessly in Ubuntu. It only cost me $15 so...

---

### Post by miss.magenta on 2008-06-09
uvcvideo should work for that cam

---

