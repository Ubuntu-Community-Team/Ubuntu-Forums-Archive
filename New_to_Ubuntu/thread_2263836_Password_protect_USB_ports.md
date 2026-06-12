---
title: "Password protect USB ports"
date: 2015-02-03
forum: New to Ubuntu
---

### Post by kingdominsight on 2015-02-03
Greetings all.
 I am new to the linux world. I have tried both LinuxMint, Ubuntu and PCLinusOS
From this experience , the Ubuntu distro seems to work the best with my ATI hd4670 graphics card. Which is odd because supposedly the other distros used the same open source drivers.
Anyway. so i am now using Ubuntu 14.04.1
It's nice and speedy, maybe not as resource friendly as Mint was,, but the gaming graphics are much better.
     Ok getting to the issue at hand.
I will be setting up a Linux computer at "Church" mainly for the elders or "deacons" as some call them, to use for research.
I would like to password protect the USB ports so that only authorized users can load from USB or save to USB while still being able to use the USB printer. The usb password would of course need to be different than the login password.
This would prevent data from being put on the computer without proper authority
The web browser will also be restricted to only certain biblical research websites.
The goal is to prevent inappropriate material from being put on the church computer.
Have googled it a bit but haven't found useful information.
Any help or ideas?

---

### Post by Tadaen_Sylvermane on 2015-02-03
Create a general non privileged user. Be sure this user is not in the sudo or plugdev groups. I would make this user able to log in without a password. Then I would give each of the elders their own account with sudo access for your admins. That would do it. Maybe run the non privileged user in kiosk mode so that the user profile is fresh everytime it gets logged in, as if it was the first time.

*EDIT* I haven't a clue on properly setting up kiosk mode. I personally would probably have a script run at logout for the general user that wipes out everything in /home/$USER, and for my browser with it's shortcuts I would keep that folder somewhere else on the system and just have a script copy it into /home in the proper place on login. Sloppy, but it works.

---

### Post by kingdominsight on 2015-02-08
> **Tadaen_Sylvermane said:**
> Create a general non privileged user. Be sure this user is not in the sudo or plugdev groups. I would make this user able to log in without a password. Then I would give each of the elders their own account with sudo access for your admins. That would do it. Maybe run the non privileged user in kiosk mode so that the user profile is fresh everytime it gets logged in, as if it was the first time.

*EDIT* I haven't a clue on properly setting up kiosk mode. I personally would probably have a script run at logout for the general user that wipes out everything in /home/$USER, and for my browser with it's shortcuts I would keep that folder somewhere else on the system and just have a script copy it into /home in the proper place on login. Sloppy, but it works.

Been exploring the non privalaged guest user settings. Might just be what i am looking for. Very helpful. Thank You Tadaen.

---

