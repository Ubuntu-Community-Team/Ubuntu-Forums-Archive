---
title: "Will reinstallation erase all updates?"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by Rodney2 on 2008-09-12
I lost my wireless access for some reason. I posted the problem here a week or so ago and have received no suggestions.  In short, I had a Zonet ZWE2500P USB adapter working fine for a month then all of a sudden no more wireless.  I thought it might be a bad adapter so tried a new one, same results.  Is it possible that if I reinstalled 8.04 (Hardy Heron) that the problem might be fixed or is it possible to just install part of the system dealing with the wireless??  as you can tell, I'm not very hep on any Linux so am grasping for straws in the dark.  There have been so many updates since the original installation in July but I guess that if that is a necessary loss, I'll have to accept it. I do have the ethernet (wired network) working okay so have access to the internet.  Here is some of my results in trying to chase down the problem:

---

### Post by SunnyRabbiera on 2008-09-12
That is one issue I know about with ubuntu, sometimes when the kernel is updated the hardware stops working.
Thats why its better to pick and choose updates.
Thats why i use Mint personally.

---

### Post by halitech on 2008-09-12
> **Rodney2 said:**
> I lost my wireless access for some reason. I posted the problem here a week or so ago and have received no suggestions.  In short, I had a Zonet ZWE2500P USB adapter working fine for a month then all of a sudden no more wireless.  I thought it might be a bad adapter so tried a new one, same results.  Is it possible that if I reinstalled 8.04 (Hardy Heron) that the problem might be fixed or is it possible to just install part of the system dealing with the wireless??  as you can tell, I'm not very hep on any Linux so am grasping for straws in the dark.  There have been so many updates since the original installation in July but I guess that if that is a necessary loss, I'll have to accept it. I do have the ethernet (wired network) working okay so have access to the internet.  Here is some of my results in trying to chase down the problem:

short answer: yes, updates will be gone

in regards to the USB adapater not working, whats the output of```
lsusb
```

---

### Post by Rodney2 on 2008-09-12
I am trying to include that info but have not  been successful in posting it.  I'll try again here

---

### Post by halitech on 2008-09-12
ok, the system is only showing your wired connection. Your usb adapter is using the RaLink chipset. It should work but may need to reinstall the drivers.

---

### Post by Rodney2 on 2008-09-12
Another dumb question, how do I reinstall the drivers?  The disk that came with adapter will not read in Linux, appears to only work with Windows XP.

---

### Post by halitech on 2008-09-12
you will need ndiswrapper to do that I think although I seem to remember something about RaLink chips will work with madwifi

---

