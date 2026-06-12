---
title: "live usb password xubuntu"
date: 2015-03-11
forum: New to Ubuntu
---

### Post by chris357 on 2015-03-11
I wanted to give x ubuntu a try today so i made a live usb boot drive. it started up ok, but its asking for a log in name an password.  but the problem is i never set one up. I was never asked to create a new user or anything, this is the first thing i see after booting. there is a blueish screen the the date at the top and a box that says other... and under that is user name and password. i tried various generic things but it always says the password is wrong. not a very encouraging first go at xubuntu so i hope there's a simple fix.

---

### Post by coffeecat on 2015-03-11
Welcome to the forum!

If it is asking you for a password on initial bootup, then there is almost certainly something wrong with either the ISO or the prepared flash drive. Live sessions of the Ubuntu family, including Xubuntu, do not present you with an initial login. For the record the username for the live xubuntu session is xubuntu, and the password is null - that is nothing at all. But you shouldn't need to respond to a password prompt. Except perhaps if you log out of the live desktop session, if that's even possible in the live Xubuntu session - it's been a long time since I used Xubuntu.

So...

I suggest you check the md5sum of the downloaded ISO to make sure the file isn't corrupted, and also tell us how you prepared the live USB. If you don't know how to test the md5sum, this is a useful start:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Post back if you need help with that.

---

### Post by The Cog on 2015-03-11
Just to confirm what coffeecat says: I just booted the 15.04 (development) xubuntu live CD and it behaves the same as it has been for years. When it boots you should see a screen with a chioce of languages on the left, and two buttons marked Try Xubuntu and Install Xubuntu. If you choose to try Xubnuntu it brings you straight to a working desktop, no login needed. Although again to confirm what coffeecat says, the username is xubuntu and the password is empty.

---

