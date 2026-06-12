---
title: "Sorry, Ubuntu 12.04 has experienced an internal error"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by 4rings on 2012-12-27
Hi,

I have a Ubuntu Server that I don't use much but I built it from scratch so I keep it on my network.  I turned it on recently and installed all the upgrades, which resulted in version 12.04 LTS.  Ever since, I see the following error after booting and I'd like to know how to fix it or at least stop it from happening.  

Sorry, Ubuntu 12.04 has experienced an internal error.
If you notice further problems, try restarting the computer.
ExecutablePath
     /usr/lib/nux/unity_support_test

The available options at this point are:
Send an error report to help fix this problem
Ignore future problems of this type

I have tried both yet the error persists.  I have searched this forum  and have found some good information, but I would like some real time  guidance.

Another windows appears as well that is labeled Apport at the top.  It says, 'precise' is no longer under development, but technical support is still available and will give you quicker results than filing a bug here.  Also, if  you have a bug, we will give it higher priority if you've gone through technical support channels first.  My choices at this point are:

I don't know what to do.
Continue.  I already know of a patch to fix this problem.
Continue.  Yes, I have discussed this with technical support.
Continue.  I don't need technical support.
Please point me to where I can get technical support.

I do not know if this is related to the issue discussed above, but I'd like to stop this from appearing also.  This issue continues to persists, despite choosing any of the available options.

I received help here in the past (and found a solution) and I am hoping for a similar result for this as well.

Thank you!

---

### Post by 4rings on 2012-12-28
Hi, I could have mentioned that I run this machine headless but it didn't seem relavent, but what I did was just removed the nVidia video card.  That seems to have fixed both (error) messages.
 
Thanks.

---

### Post by MrSpike16 on 2012-12-28
This error reporting tool was for development/testing and should have been disabled
when the OS was released.  

To turn it off you need to edit the /etc/default/apport file.

I haven't run a headless OS, don't know which editors work, so use one you know or try nano as below:  

```
sudo nano /etc/default/apport
```

Change value of "enabled" from 1 to 0, save text file and reboot computer.

I wouldn't worry about the actual error it is seeing, probably not important, just turn off this uneeded reporting tool.

---

