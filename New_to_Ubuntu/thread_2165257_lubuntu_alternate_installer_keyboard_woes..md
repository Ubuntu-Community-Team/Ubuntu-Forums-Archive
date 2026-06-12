---
title: "lubuntu alternate installer keyboard woes."
date: 2013-08-04
forum: New to Ubuntu
---

### Post by slaps2 on 2013-08-04
I have a fairly low end laptop that I'm trying to instal lubuntu on. Because of the small amount of ram that it has (256mb) I'm using the alternate installer. 

Problem is, the installer doesn't recognise my laptop's keyboard, it just hangs as soon as the language selection screen pops up. Even an external usb keyboard doesn't get picked up. Can anyone give me a push in the right direction? I can access the bios with both the usb and onboard keyboards, if that's any help on figuring out what's going on.

---

### Post by ibjsb4 on 2013-08-04
What make of laptop is this?

---

### Post by slaps2 on 2013-08-04
It's a Compaq NX9000.

---

### Post by ibjsb4 on 2013-08-04
I been looking [here]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Compaq+NX9000&sa=Search&cof=FORID:9") and not getting any good hits.  So heres a suggestion.

On the alt install cd there is the option to do a terminal only install.  I think it was either F4 or F6 at the start of the installation.  Try doing that and if you succeed, install Lubuntu with this command:

```
sudo apt-get install lubuntu-desktop
```

---

### Post by slaps2 on 2013-08-04
Sadly the instal doesn't respond to any input at all, so using any keys at all isn't something I can do.

---

### Post by ibjsb4 on 2013-08-04
I really have no idea why this is happening.  My last suggestion would be to try the mini iso.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

---

