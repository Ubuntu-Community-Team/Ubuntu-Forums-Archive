---
title: "Upgrade to 12.04, can't connect to Wireless Internet"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by namini67 on 2012-05-13
Hi.
I'm new to Ubuntu, and I just upgraded to 12.04 from 11.10. I tried following a few different thread about how to fix the problem, but I either can't seem to follow them correctly, or they do not address my specific problem. If anyone could help, it would be greatly appreciated! 

Thanks!

---

### Post by krytorii on 2012-05-13
Could you give us some more details?

Does your pc have wireless built in or are you using a USB device? What brand is it?
If you have a USB device, try using ndiswrapper.

---

### Post by Lisiano on 2012-05-13
Please open a terminal (Ctrl+Alt+T) and type in these commands
```
lspci
lsusb
```
Then copy paste the output here using Code tags (The Hash (#) button)

---

### Post by namini67 on 2012-05-13
Hi everyone!

Thank you guy for responding to my problem so quickly! I managed to wrangle a friend to help with the problem, I think there was something wrong with my kernel driver. I ended up wiping and reinstalling it. Everything works fine now, so I think I'll close the thread. 

Thanks again! :]

---

