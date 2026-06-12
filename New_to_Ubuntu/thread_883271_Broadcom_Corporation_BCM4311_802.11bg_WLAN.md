---
title: "Broadcom Corporation BCM4311 802.11b/g WLAN"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by thepio on 2008-08-07
I just started Linux today. I need help getting my wireless going. I have Broadcom Corporation BCM4311 802.11b/g WLAN

---

### Post by drs305 on 2008-08-07
You CAN get the broadcom card to work! Here is a link that I used to get it working in hardy. Same version as you I believe:
[URL="http://ubuntuforums.org/showthread.php?t=779754&highlight=wireless+work+hardy"]http://ubuntuforums.org/showthread.php?t=779754&highlight=wireless+work+hardy
[/URL]

Here's another one, shorter:
[URL="http://ubuntuforums.org/showthread.php?t=767372"]http://ubuntuforums.org/showthread.php?t=767372
[/URL]

Look through the entire thread before proceeding so you know what you are getting into. Good luck. ;-)

---

### Post by niyonk on 2008-08-07
Hello :)
go to applications->add or remove then search for 'ndiswrapper' 
Install that program,
What program will allow you to use a windows driver for your card.

read h[ere]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by st33med on 2008-08-07
As the above person stated, you want ndiswrapper. However, you need to follow [this guide]("http://ubuntuforums.org/showthread.php?t=760568") to enable it.

---

### Post by sam_delta on 2008-08-07
id say try b43-fwcutter first as drs sayd, if you are not satisfied with the results , go for ndiswrapper,

sam

---

### Post by st33med on 2008-08-07
> **sam_delta said:**
> id say try b43-fwcutter first as drs sayd, if you are not satisfied with the results , go for ndiswrapper,

sam

b43-fwcutter don't work properly for the 4311 series of Dell wireless cards.

---

### Post by eightmillion on 2008-08-07
I've got this card too. b43-fwcutter doesn't work. Ndiswrapper is the way to go.

---

