---
title: "Ubuntu 12.10 Goes Purple, Blinking Cursor, then Black Screen"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by ajdrew06 on 2013-03-04
Hello All,

I recently did a fresh install of 12.10. It was working great. 12.04 was a bit buggy on my relatively new laptop, which was performing a lot better on 12.10. Like I said, it was doing great. However, I turned on my laptop today, and it didn't boot. I get the option to choose which version of the kernel, I picked the default version, I get a solid purple screen, then I get a blinking _ in the upper-left corner, and finally a black screen as if the monitor were turned off. Any ideas? I was able to boot in an earlier kernel version one time, but when I tried doing that a second time, it didn't boot and it does the same display sequence.

Please help! Thank you!
-Drew

---

### Post by ManamiVixen on 2013-03-04
What graphics does your laptop have? CPU too.

---

### Post by ManamiVixen on 2013-03-04
Currently, it sounds like X.Org is failling. Graphics type can help here.

---

### Post by ajdrew06 on 2013-03-04
I have Radeon HD 6620G. I did not install any proprietary drivers. The default was working fine, so I didn't change anything.

---

### Post by ManamiVixen on 2013-03-04
It's usually a good idea to install the Proprietary Drivers. Only people who don't are the hardcore FOSS people. 

But anyways, carry on. Did you update before the incident, as in upadted then turned off the PC for the night, or was it spontaneous?

---

### Post by ajdrew06 on 2013-03-04
I've had bad luck in the past installing proprietary drivers. Everytime I do, my OS never boots right after that. I usually have to go to the TTY & uninstall all the fglrx stuff. I tend to stay away from any driver that pops up on that additional drivers window. I installed the proprietary driver from the website in 12.04, but when ubuntu updated xorg, some settings got messed up & I ended up having to uninstall the proprietary driver.

I did install some updates this morning. I did not get a requirement to reboot, so I turned off my computer when I was finished. A few hours later, I turned it on, and that's when I had trouble.

---

### Post by ManamiVixen on 2013-03-04
From that, it sounds like X.Org is in fact broken. Specifically the ATI driver. I know it's the driver since X no longer stores a config file and does it on the fly upon boot and stores it in ram. Unfortuantly I'm not sure how to correct this since X errors and Kernel Panic's are pretty much "Blue Screens" on linux. So only option I know is to reinstall the PC. But that also means updating will break it again. So you are better off getting someone else here to help you. Sorry. Though you could try Xorg Xedgers which have updated X.Org files. They could help.

---

### Post by ajdrew06 on 2013-03-05
> **ManamiVixen said:**
> From that, it sounds like X.Org is in fact broken. Specifically the ATI driver. I know it's the driver since X no longer stores a config file and does it on the fly upon boot and stores it in ram. Unfortuantly I'm not sure how to correct this since X errors and Kernel Panic's are pretty much "Blue Screens" on linux. So only option I know is to reinstall the PC. But that also means updating will break it again. So you are better off getting someone else here to help you. Sorry. Though you could try Xorg Xedgers which have updated X.Org files. They could help.

Thanks ManamiVixen for trying. Can anyone else help me?

---

