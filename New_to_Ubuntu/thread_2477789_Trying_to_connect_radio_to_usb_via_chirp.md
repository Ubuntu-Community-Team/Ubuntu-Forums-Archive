---
title: "Trying to connect radio to usb via chirp"
date: 2022-08-07
forum: New to Ubuntu
---

### Post by kc2dws2 on 2022-08-07
The issue is lsusb shows Bus 001 Device 004: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port / Mobile Action MA-8910P. The chirp software wants to know what tty to connect to.
 I am running Ubuntu 22.04 as a guest under windows 11. any  help would be appreciated.

---

### Post by him610 on 2022-08-10
You might want to take a look at this,....[https://chirp.danplanet.com/projects/chirp/wiki/Beginners_Guide]("https://chirp.danplanet.com/projects/chirp/wiki/Beginners_Guide")

It has been awhile since I did any work with serial ports, but I seem to recall that either serial ports 1 or 3 were the ones to use.

Good luck.

---

### Post by kc2dws2 on 2022-08-12
Thank you for reply. The link you sent led me to a page  that led me to another page   [https://chirp.danplanet.com/projects/chirp/wiki/Connection_Issues_using_Ubuntu](https://chirp.danplanet.com/projects/chirp/wiki/Connection_Issues_using_Ubuntu) This page had the correct way to set groups and permissions. chirp software now shows usb0 as an option. Once again thank you for your help Kevin

---

