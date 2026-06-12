---
title: "nm-applet not getting wireless key from keyring"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by MegaJim on 2008-04-27
When I login to ubuntu gnome the wireless network key is taken from my keyring by nm-applet and it connects immediately, however under xubuntu the nm-applet does not request the key from my keyring and I must enter it manually each time - this includes every subsequent reconnect in the same session.

Does anyone have an idea how to get the nm-applet to take the key from the keyring, or at least another solution to this problem?

Thanks.

---

### Post by MegaJim on 2008-04-28
Shameless bump

---

### Post by Michael.Godawski on 2008-04-28
Bah, try to connect with the application WiCD. I know it is not direct solution for the nm issue...

WiCD:
[https://help.ubuntu.com/community/WICD?highlight=%28wicd%29](https://help.ubuntu.com/community/WICD?highlight=%28wicd%29)

---

### Post by OffHand on 2008-04-28
You could have something similar to my problem: [http://ubuntuforums.org/showthread.php?t=753900](http://ubuntuforums.org/showthread.php?t=753900) (post 4 explains what actually happened)

---

### Post by MegaJim on 2008-04-28
Thanks, I think there is some problem with my passwords and encryption keys.  When I open up passwords and encryption there are no passwords listed, and furthermore it says access is denied.  When I try to change the keyring password I also get access denied.

---

### Post by OffHand on 2008-04-28
> **MegaJim said:**
> Thanks, I think there is some problem with my passwords and encryption keys.  When I open up passwords and encryption there are no passwords listed, and furthermore it says access is denied.  When I try to change the keyring password I also get access denied.

Try this: [http://ubuntuforums.org/showpost.php?p=4707962&postcount=6](http://ubuntuforums.org/showpost.php?p=4707962&postcount=6)

---

### Post by MegaJim on 2008-04-28
Like I said, I am denied access to the keyring for some reason so I am not able to perform any actions on stored passwords.  Attempting to change the keyring password is also not possible through the passwords and encryption GUI.  How can I regain control of my keyring?

---

### Post by OffHand on 2008-04-28
> **MegaJim said:**
> Like I said, I am denied access to the keyring for some reason so I am not able to perform any actions on stored passwords.  Attempting to change the keyring password is also not possible through the passwords and encryption GUI.  How can I regain control of my keyring?

try: ```
sudo apt-get remove seahorse --purge && sudo apt-get install seahorse
```

---

### Post by MegaJim on 2008-04-28
Good suggestion OffHand, however reinstalling and purging config files has not made any difference to the situation.  Perhaps there is another application involved?

---

### Post by gardara on 2008-04-28
> **Michael.Godawski said:**
> Bah, try to connect with the application WiCD. I know it is not direct solution for the nm issue...

WiCD:
[https://help.ubuntu.com/community/WICD?highlight=%28wicd%29](https://help.ubuntu.com/community/WICD?highlight=%28wicd%29)

I agree, I had a problem with nm-applet letting me enter my wep key about 5 times before it would connect. WiCD has no such problem and is really nice in every way

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by MegaJim on 2008-04-28
I have used WICD in the past, however I need the VPN support offered by Network Manager

---

### Post by OffHand on 2008-04-28
I suggest making a new thread for the new problem (seahorse)

---

### Post by MegaJim on 2008-04-28
Agreed, I have found that this is an old issue although I never experienced it in 7.10

Installing WICD for my home network for the moment.

---

