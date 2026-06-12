---
title: "Can't log into Ubuntu 11.10 after upgrade."
date: 2011-11-06
forum: New to Ubuntu
---

### Post by hauschildt on 2011-11-06
I have been running 11.04 successfully for a couple months on my Asus Eee 1001px netbook. I upgraded 11.10 after receiving the notice. After the install I was able to maneuver around 11.10 until the next morning after putting my machine into Hibernate.
Issue:
When I power up my machine. It takes me as far as the login screen. At which point, after entering my password, it's not recognized.

Whats been done:
* Assuming that my password was wrong. Using the terminal I changed my password. (same thing happens)

* I have tried to boot up through GNU Grub (recovery mode)
* Boot up by using previous versions
Each of these options haven't worked.

After some reading about the changes from 11.04 to 11.10. I'm starting think that my video card won't support the upgrade. However after doing a google search. There doesn't appear to be any other users with netbooks experiencing the same issues.

At this point I would like to just downgrade back to 11.04. The only problem is, now when I try to install 11.04 via a bootable thumbstick, I immediately get, "boot error".

Anyone have any suggestions to get either 11.10 to work or downgrade?

---

### Post by pawanh on 2011-11-20
Kill gdm from the terminal using the killall command and try to run X11 directly using startx. If any errors occur you'll get the messages and be in a better position to solve the problem. Also you can check out .xsession-errors in your home folder for them.

---

### Post by Jack Brown on 2011-11-20
also since you did an upgrade from 11.04, you can try a fresh install of 11.10.

Fresh installs are often more stable than upgrades.

Basically you can:
backup your data in another hard drive or flash drive
Then Fresh install 11.10, then put your data back.


From experience 11.10 is a lot better than 11.04, which was a very transitional version.

also for older netbooks (single core atom), xubuntu is recommended.

---

### Post by alphacrucis2 on 2011-11-20
> **hauschildt said:**
> I have been running 11.04 successfully for a couple months on my Asus Eee 1001px netbook. I upgraded 11.10 after receiving the notice. After the install I was able to maneuver around 11.10 until the next morning after putting my machine into Hibernate.
Issue:
When I power up my machine. It takes me as far as the login screen. At which point, after entering my password, it's not recognized.

Whats been done:
* Assuming that my password was wrong. Using the terminal I changed my password. (same thing happens)

* I have tried to boot up through GNU Grub (recovery mode)
* Boot up by using previous versions
Each of these options haven't worked.

After some reading about the changes from 11.04 to 11.10. I'm starting think that my video card won't support the upgrade. However after doing a google search. There doesn't appear to be any other users with netbooks experiencing the same issues.

At this point I would like to just downgrade back to 11.04. The only problem is, now when I try to install 11.04 via a bootable thumbstick, I immediately get, "boot error".

Anyone have any suggestions to get either 11.10 to work or downgrade?

This seems to be a common problem caused by upgrade to 11.10 although it didn't affect me. Check this out:

[http://www.upubuntu.com/2011/10/how-to-fix-login-issues-on-ubuntu-1110.html](http://www.upubuntu.com/2011/10/how-to-fix-login-issues-on-ubuntu-1110.html)

---

### Post by LinuxFan999 on 2011-11-20
I thought the netbook remix was discontinued after 10.10:confused:.

---

