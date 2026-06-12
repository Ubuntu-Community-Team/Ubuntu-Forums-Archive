---
title: "64-bit Natty Seems Laggy"
date: 2011-09-11
forum: New to Ubuntu
---

### Post by wkswedenburg on 2011-09-11
Long time lurker fist time poster.

I'm have an Acer Aspire 7551-7422
Dual booting windows 7 64bit and ubuntu 11.04 64-bit

I have been using Ubuntu for a year now and learning alot. 

I recently picked up a laptop and installed 8gb of ram. It seems to lag alot. I had 32-bit on a much older system and it ran much better.

I was wondering if someone could point me in the right direction to begin on getting this cleaned up. Should i go back to 32-bit? Maybe wait for Oneiric?  I'm not sure.

Also it's my first time posting what should i begin with in the future.

---

### Post by _d_ on 2011-09-11
Are you using ATI Catalyst drivers by chance?

---

### Post by wkswedenburg on 2011-09-11
I do have the ATI drivers.

---

### Post by _d_ on 2011-09-11
Ahh ok then, there's a bug relating to ATI drivers and Unity in regards to the OpenGL option Sync to VBLANK.

Download the Compiz Config Settings Manager via Software Center, Synaptic or terminal:

```
sudo apt-get install compizconfig-settings-manager
```

And then run it (ALT-F2 -> compizconfig-settings-manager), navigate to the OpenGL plugin and then uncheck the box for Sync to VBLANK. Reboot if you wish afterwards.

---

### Post by wkswedenburg on 2011-09-12
Thank you very much for the concise(sp) directions. I followed and then rebooted. Things are certainly better. Still not as smooth as i feel they should be. (When i click my home folder in the Unity bar it takes 6-8 seconds to load each time, and i have very few files there)

While exploring my ati drivers i found that they were not the latest versions (though im not sure i need that if im using the open source drivers)

I downloaded that latest drivers for ubuntu 64-bit but when i try to install them i get this error message.

[I]gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.[/I]

Any ideas or am i screwing things up?

Thank you again. It's embarassing cause ive always been the computer guy for my friends i don't often ask for help.

---

