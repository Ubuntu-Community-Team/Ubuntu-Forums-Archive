---
title: "ati driver setup"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Matt26 on 2008-04-29
i have just installed the newest ati catalyst proprietary driver for linux (v8.4) on ubuntu 8.04 and it doesn't seem to have made a difference.  i installed the driver without creating a distribution package first and just let it install as is- the installation was almost instant (no installation progress shown) but it said it completed successfully, however i am unable to find any sort of GUI for configuring the driver or enabling it, since it doesn't appear to have updated the video driver yet- i am still experiencing poor graphics performace as i was before the ati driver was installed, and i have rebooted just to be sure but still no difference.  what can i do to get this working?  thanks.

---

### Post by sir_napsalot on 2008-04-29
I've got a similar problem with my ATI card. Your best bet would be to go here [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) and see if the 7.10 commands give you any better results.

---

### Post by Matt26 on 2008-05-02
thanks for the suggestion- i tried the instructions in the link that you provided and i still get the same results.. i did find a way to restore my video config (sort of by accident). i downloaded and installed EnvyNG with the hope that it would solve the issue, which it didn't- just gave me the same results (blank, light blue screen after logging in) so i used xfix to restore my X window config then logged in and used EnvyNG to uninstall any video drivers that it did install, then rebooted when prompted, and when i logged back in after the reboot, my desktop was responding normally again! (windows rendering properly w/fade effects, no more vertical lines on screen etc), so now i have my video config back to the way it was before the upgrade to 8.04.. now i need to figure out how to get the proper restricted ATI drivers to work and i will be all set for compiz-fusion!

---

### Post by sir_napsalot on 2008-05-06
well unfortunately that was the only idea i had. but if you figure out how to get the card to work fully in 8.04 let me know. I just upgraded and my video games are......horrible.

---

