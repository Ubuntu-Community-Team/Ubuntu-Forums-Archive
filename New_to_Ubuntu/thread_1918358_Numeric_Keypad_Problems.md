---
title: "Numeric Keypad Problems"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by mameshiba on 2012-01-31
Hey all,

I'm having a minor, but maddening problem with my Stylenote laptop. It came with a numeric keypad, which periodically just stops working and no amount of pressing the 'Num Lk' key will make it work.

It went through a spate of not working about a year ago, but then miraculously started working again one day before I got around to looking into why and what to do about it. Only now it's stopped functioning again and I can't for the life of me work out why.

When I boot up, it works at the login screen, but once I am logged in it doesn't work at all. I've looked in System > Preferences > Keyboard; the layout is set to Evedev-managed keyboard, which I believe is correct, although I have tried changing this to other models but it does nothing.

I'm running Ubuntu 11.04, if that helps.

Help?...

---

### Post by mameshiba on 2012-02-21
Sorry to bump this, but I'm still having problems with it :(

Interestingly, when I first posted this I was still using 10.04. I've since upgraded to 11.10 using an installer disk I ordered from Canonical. While I was booting from the disk to check that it worked okay, my numeric keys worked again as normal, but once the upgrade completed the problem resumed, so it must be a problem with my keyboard settings although I can't figure out what...

Again, at the login screen on booting up the numeric keys work, but not once I'm logged in. However, when my screen is idle and powers off and I try to log back in again the login window *is* telling me that Number Lock is on, so it must be able to see them...

---

### Post by WthIteh on 2012-02-21
> **mameshiba said:**
> Interestingly, when I first posted this I was still using 10.04. I've since upgraded to 11.10 using an installer disk I ordered from Canonical. While I was booting from the disk to check that it worked okay, my numeric keys worked again as normal, but once the upgrade completed the problem resumed, so it must be a problem with my keyboard settings although I can't figure out what.
So first login with another user (for example using guest user or create a new user).
If it solved your problem, then we can conclude that the problem is really from user specific settings.

If it was your case, then you can remove your settings by deleting hidden folders in the home folder (which start with 'dot') so they get reset. NOTE to not remove all of them (for example .mozilla contains all of your browsing history, etc.). Each folder is for some application. See the names and delete related names one by one.

---

### Post by mameshiba on 2012-02-21
That would appear to be it, as I could use the numeric keys in the guest session. Thank you!

How do I view the hidden folders in Home in order to delete them?

---

### Post by WthIteh on 2012-02-21
> **mameshiba said:**
> That would appear to be it, as I could use the numeric keys in the guest session. Thank you!

How do I view the hidden folders in Home in order to delete them?
Open nautilus and press Ctrl+H to see hidden file and folders.
You can also open a terminal (press Ctrl+Alt+T) and then type 'ls -a'.

---

### Post by mameshiba on 2012-02-21
That's sorted it. Thanks so much! :)

---

