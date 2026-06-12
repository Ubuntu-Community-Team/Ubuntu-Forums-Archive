---
title: "ubuntu 9.04 jaunty on acer aspire one d150 (using ALC272 driver)"
date: 2009-05-08
forum: Philippine Team
---

### Post by vynnie14 on 2009-05-08
hello everybody,

i've been trying to sleuth over ubuntuforums for a month now and so far, i haven't seen the solution i need. i need to have the mic (internal-front) working. i'm posting here coz most likely the filipino community would have the same hardware as i have. the ones that have been posted so far are for the previous versions of aao (9").

anybody, help!

tia.

vynnie

---

### Post by vynnie14 on 2009-05-08
just this in... looking through my dmesg i found these. maybe this might help you help me :) 

[   13.249911] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...

tia.

vynnie

---

### Post by loell on 2009-05-08
googling the error eventually lead to some driver links

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=24&Level=4&Conn=3&DownTypeID=3#2]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=24&Level=4&Conn=3&DownTypeID=3#2")

---

### Post by vynnie14 on 2009-05-09
tnx for the assist loell. the package didn't work form me though. but i think it helped via the alsa-base.conf entries. i eventually plugged alsa-drivers 1.0.20 and voila! i can skype now!

---

