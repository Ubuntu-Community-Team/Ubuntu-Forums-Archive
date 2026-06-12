---
title: "Ubuntu 13 automatic login"
date: 2013-09-23
forum: New to Ubuntu
---

### Post by electricman2 on 2013-09-23
Hello,

Awhile ago, I set my account to automatic login, but now I want to set it back.  I went in to user accounts and turned automatic login off, but it does not ask for my password.  It goes to the opening screen to select your user account. All I have to do is click on my account, and it will log into it.  It still requires a password to re-enter my account if the computer goes to sleep though.

---

### Post by Kirboosy on 2013-09-23
If no one has already said it let me be the first to welcome you to the forums! :D

Click the Gear (top right corner)--> System Settings-->User Accounts-->Unlock (top right corner)-->Automatic Login (Click to off)--> Lock Settings back

Hope that helps!
~Caboose

---

### Post by Frogs Hair on 2013-09-23
If open System Settings > Brightness & lock you can disable the password requirement .

---

### Post by electricman2 on 2013-09-24
thank you for replying! I tried doing what caboose said, but it still doesn't ask for the password.  Just in case something went wrong, I unlocked it, turned the auto login on and then off again and relocked it.  It still won't require a password to log in.

---

### Post by electricman2 on 2013-09-24
Thanks for replying!  I don't want to disable the password though, I want to re-enable it.  Its enabled under the brightness and lock setting if that's what your asking

---

### Post by Kirboosy on 2013-09-24
Go ahead and run ```
sudo gedit /etc/lightdm/lightdm.conf
``` You config should look similar. If you change the username that should stop the autologin. 
```

**Original**
[SeatDefaults]
autologin-guest=false
* autologin-user=caboose885*
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=ubuntu
greeter-session=unity-greeter
[B]
Modified[/B]
[SeatDefaults]
autologin-guest=false
* autologin-user=blank*
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=ubuntu
greeter-session=unity-greeter


```

Hope that helps!
~Caboose

---

