---
title: "wireless network not saving settings"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by scotcella on 2008-05-20
Hi,

Lucky I had almost everything working "just like that" when installing the latest version of Ubuntu.

I've noticed when I log out/shut down Ubuntu the wireless WPA keys are never saved, and I have to manually retype in the password. I want the laptop to connect automatically rather having to retype.

How can I fix this?

Thanks in advance!

---

### Post by Myglaren on 2008-05-20
Mine saves all the keys etc but defaults to the (non-existant) wired network and has to be told to use the wireless network.
I'm sure ther will be a fix for this but it isn't that much of a problem for me, the other user will be a bit baffled by it when she returns.

---

### Post by scotcella on 2008-05-20
Anyone?

---

### Post by jerrallan on 2008-05-21
Same Problem here. I use WEP. I could not get it to connect at all. I can get wireless to work if I manually enter the settings from the terminal, ignoring System>Administration>Network totally. 


Try this thread for a start:

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

It has helped some people to get their wireless to be automatic on reboot.  As for me, I have set up my manual start in a script.  Takes a few seconds to start wireless. Not automatic, but better than nothing.

---

### Post by scotcella on 2008-05-23
Hi everyone,

I thought it might have only been me. It's good to know i'm not the only one. Maybe a later update or version will see this issue fixed.

---

### Post by SoloSalsa on 2008-05-23
> **scotcella said:**
> I've noticed when I log out/shut down Ubuntu the wireless WPA keys are never saved, and I have to manually retype in the password.
Same here, but I never bothered taking action.

---

### Post by jerrallan on 2008-05-24
Hi again,

I think that for a lot people using Network Manager is buggy.  That how to thread I gave above will give you a start.  I got mine so wireless would activate on reboot. I use WEP 128 bit encryption, and did not have any driver problems.  When I installed Hardy I noticed that whatever I put in Network Manager wouldn't stay, plus I couldn't get a connection.

So I do not use Network Manager. I learned that when I had 
Dapper.

Good luck!

---

### Post by beefcurry on 2008-07-27
Its July 27th and there is still an open bug request in launchpad. Im considering getting rid of network manager for wcid since I installed ubuntu for other people that actually have no idea how to input my complex abnormally long wpa password.

---

