---
title: "System will not boot past logon screen"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by trooperchix on 2012-07-23
My laptop is driving me nuts.  I turn the bugger on, it boots to the logon screen fine.  I enter my logon id and password, then the upper right quadrant of the screen turns black (looks like terminal screen) and I get to a command prompt and there it stays.  I'm running 12.04, and this occured right after an update.  Help!!

---

### Post by Bufeu on 2012-07-23
A screenshot would be nice.

---

### Post by khelben1979 on 2012-07-23
You said that this happened after you applied the system update. How long have your present Ubuntu system been working before this issue?

---

### Post by trooperchix on 2012-07-23
Ug, would love to give you one, but I'm operating under a LiveCD.  I found another thread that seems to discuss this issue and for a relative noob, it makes no sense.  Would someone be willing to hold my hand in this?  Thanks again.  :)

---

### Post by trooperchix on 2012-07-23
Let me add that I can logon fine through the guest account.  Could this be a graphics issue?  The difference between the two is my main logon account I use a background image whereas the guest account is the default background.  I could be grasping at straws..

---

### Post by khelben1979 on 2012-07-23
> **trooperchix said:**
> Let me add that I can logon fine through the guest account.  Could this be a graphics issue?

I doubt that it's a graphics issue, that would affect all user accounts except the root account, I think.

How does it looks like when you make the command: ```
df -h
``` Could be interesting if it's an issue with your disc partitons get too filled up, but most likely I would guess it's some configuration file which mess up something. Hmm... I'm mostly guessing, and as the previous poster wrote, a screenshot would help out.

---

### Post by trooperchix on 2012-07-23
Figured out a workaround.  I was able to login under ubuntu 2d, oddly.  I started with the gdm vs lightgdm workaround.  I'm in for a change.

---

