---
title: "I installed Jinzora Music thing on my ubuntu..but"
date: 2012-07-07
forum: New to Ubuntu
---

### Post by mg2012 on 2012-07-07
I Installed Jinzora Music thing on my ubuntu box, but when I log in, and try to play music it gives this error:

                                         We had a problem connecting to the player, sorry this is a fatal error!

Player Settings:
server - localhost
port - 6600
description - Manatee Box
password - 
type - mpd
prefix - http

Please check these with your player's settings

---

### Post by whitediver on 2013-01-28
Hey! 

I have just experienced the same problem. Apparently you are trying to play audio on the server side, while you haven't installed a player. You need to install "mpd" to fix this. So, type :
```
sudo ap-get install mpg
```
in a terminal to install the required player. 

Cheers!

---

### Post by dolphin194 on 2013-01-28
EDIT: Removed since I looked at the date of the OP

---

