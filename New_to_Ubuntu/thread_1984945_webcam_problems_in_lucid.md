---
title: "webcam problems in lucid"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by sreinert on 2012-05-22
I'm trying to get a Logitech C200 webcam to work in Lucid. Every time I activate the webcam whether with Cheese or guvcview, the system crashes (the light on the webcam does go on). This is the message in the log:
"bonobo-activation-server (sue-1902): could not associate with desktop session: Failed to connect to socket /tmp/dbus-PaNdhCdye0: Connection refused"
I tried it in an xcfe desktop and the same thing happened.
hdinfo shows the webcam with an active driver, ucv.

Any ideas? Thanks.

---

### Post by mörgæs on 2012-05-23
How does it work in a live boot of 12.04?

Webcam applications, especially in the guvcview-family, have improved a lot during the latest two years.

---

### Post by sreinert on 2012-05-23
My computer processor doesn't have PAE so can't use Ubuntu 12.04. I tried the webcam with a liveCD of Xubuntu 12.04 and there's no crash but there's no image with guvcview.

---

### Post by mörgæs on 2012-05-24
If the computer is pre-PAE, I would recommend Lubuntu 12.04 and begin troubleshooting from there.

---

### Post by sreinert on 2012-05-24
Thanks, I'll try it.

---

### Post by sreinert on 2012-05-24
Webcam and Skype work in Lubuntu 12.04; thanks for suggesting that option.

---

### Post by recap on 2012-05-24
updates maybe?

---

### Post by mörgæs on 2012-05-24
Good, please mark the thread 'solved' using 'thread tools'.

---

