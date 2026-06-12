---
title: "Reboot  Problems after trying Ubuntu"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by weatherguy01 on 2008-04-25
I'm running windows vista on my PC and decided to try Ubuntu. I downloaded the ISO file and infra-recorder and made my own installation disk. I decided I wanted to install it on a small parition of my hard disk but the options confused me and I aborted the install so I could find out what to do. When i aborted and restarted my boot order seems  to be messed up and it doesn't boot back to windows vista. I took the ubuntu cd out and I pressed F12  on the initial boot screen to change the order to boot from the hard disk and all I get is a little blinking cursor. How do I get windows back?

---

### Post by Rocket2DMn on 2008-04-26
Hey, if you haven't figured it out yet, have a look here: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Go through its 7 steps, I think you will need to run
```
bootrec /fixmbr
bootrec /fixboot
```
If you cancelled the install while it was resizing the hard drive, you may be in a little more trouble.

---

