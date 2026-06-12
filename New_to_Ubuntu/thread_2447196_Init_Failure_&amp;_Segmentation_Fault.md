---
title: "Init Failure &amp; Segmentation Fault"
date: 2020-07-14
forum: New to Ubuntu
---

### Post by expressobiker on 2020-07-14
Hi All,


  I have an Expresso HD exercise bike that runs on a Giada G300 mini-computer that has a GE Force GT 730 graphics card.  It runs on 32-bit Ubuntu 12.04.5


  I have an issue that started 2 months ago.  I bought the bike used and it worked fine until I connected it to the internet when I bought the subscription.  I left it on for a few hours to "find" the subscription, but when I came back it had a blue screen.  What's supposed to happen is I turn the bike on and it autostarts/launches into the bike software where you can pick a track and begin. 


  When I restarted after the blue screen, it boots to tty1 and I login there.  When I go to the startup folder equivalent and launch the program (home/expresso/scripts/start-launcher.sh) I get the following error:


  ```
Inca

   init kbd
  init mouse failed.
  segmentation fault (core dumped)
  
```
   
  I'm not even sure where to start with this error.  I googled around and it seems like the segmentation fault/core dump can be caused by just about anything.  Any insight would be greatly appreciated


  Thank you

---

### Post by ActionParsnip on 2020-07-14
Ubuntu 12.04 is no longer supported. It's support ended in 2017.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I suggest you wiped the install off and do a clean install of Focal (Ubuntu 20.04). Its the latest stable version of Ubuntu and supported until April 2025

---

### Post by expressobiker on 2020-07-14
If I uninstall 12.04 all the software will still remain, right?  And hopefully work...

---

### Post by Impavidus on 2020-07-14
No, the software won't remain and work, so that's not a very good option.

Segmentation faults typically indicate a bug in the software or a mismatch in the version of a dynamically loaded library. As your error comes after the message "init mouse failed", I think that the "init mouse failed" is the first error that happens and the segmentation fault is triggered by the error handler for that. But I doubt that that really matters.

Ubuntu 12.04 was a great release, but has been long dead now. As long as you keep the computer completely separate from the network, it should be safe to continue using it. Once connected to the web, it is open for attack. It's a constant problem for embedded devices running obsolete software.

20.04 is the current release, but only available as 64 bit, so it won't work (probably). And even if Ubuntu 20.04 runs, you still have to move the racing software over, which probably won't work as it was compiled and linked to versions of libraries no longer available.

If anyone has an idea how to make this work, tell us.

---

