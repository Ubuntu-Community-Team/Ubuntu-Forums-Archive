---
title: "live usb doesn't save user PW"
date: 2022-02-03
forum: New to Ubuntu
---

### Post by ra-white on 2022-02-03
I'm on a live usb running Ubuntu 20.04.
In settings -> Users, I've disabled Automatic Login and have set password.
However, after rebooting the machine I'm prompted to click my username but the password is gone, so it lets me in without the password.
When I go back to Settings -> Users the password is gone.

How do I permanently save the password and force Ubuntu to ask for it at startup?

---

### Post by grahammechanical on 2022-02-03
The Ubuntu live session does not retain any changes we make to Ubuntu when we exit the live session. This is because the live session runs in system memory (RAM) which is flushed when the session is ended. To do what you want to do you will need to install Ubuntu to the usb stick with persistence.. This how to shows you how.

[https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)

Regards

---

### Post by tea for one on 2022-02-03
Can you provide a little clarification because [COLOR="#0000FF"]live usb[/COLOR] is open to interpretation.

[LIST=1]
[*]Live Ubuntu (no user and no persistent storage)
[*]Live Ubuntu (no user but with persistent storage)
[*]Fully installed Ubuntu to an external USB drive (inc user name)
[/LIST]
Choice 3 would require two USB devices.
The first would be the Ubuntu live installer (i.e.source) and the second would be the target device.

---

### Post by guiverc on 2022-02-03
You can install a Ubuntu system to thumb-drive; then it acts like an installed system.

You can also have a *live* system on thumb-drive with persistence, meaning it's not a *fresh* system each time, but additional packages, configuration changes take place being stored in a different location on the same thumb-drive so it's there next session. There are a number of ways of creating "*live with persistence*", some have slightly different advantages/disadvantages, but it's still not the same as an installed system (*it's all run from RAM like a live system, just details are stored for next boot, but performance is still closer to a live system, ie. slower*)

By default *live*  does **not** have persistence; the ISO is written in a different way to enable persistence.

---

### Post by ra-white on 2022-02-03
Thanks for all your replies.

My Ubuntu USB has persistant allocated memory. 
I've installed plenty of apps and other Ubuntu system settings are indeed saved after shutdown.

I've had password protected usb sticks with Ubuntu before without this problem!

---

### Post by C.S.Cameron on 2022-02-03
Have you tried changing "user name"?

---

### Post by ra-white on 2022-02-03
Yes, and it still will not save my password. Everytime I restart it will just let me in without asking for any password, and the pw field is again blank when I go to settings.
If I add another user and set a password to that user, it works. But not for my main user profile...

---

