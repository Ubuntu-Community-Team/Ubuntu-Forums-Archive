---
title: "Can't uninstall Crossover"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by BlackAce on 2008-11-05
First off I am a complete newbie when it comes to Linux. I am have tried it and installed it a few years ago, before Novell bought SuSE and before RedHat focused on server distros. I guess that was back in the mid 90's.

I decided since I have been tired of Windows for quite a while now it was time to make the change. Plus there is a lot more driver support then when I originally tried Linux.

Anyway I got a free copy of Crossover when they had the Lame Duck Presidential Challenge. I installed it without a problem but not realizing it I installed the standard edition. I want to uninstall it so I can install the professional edition. Whenever I uninstall it I get a message > Uninstall Complete "CrossOver Linux Standard has been removed from your account. To fully uninstall it, run '/opt/cxoffice/bin/cxuninstall' as root."

But it is still installed. 

Under user privileges I have the box checked "Administer the system".

---

### Post by taurus on 2008-11-05
Did you run that command to fully uninstall it?

Applications -> Accessories -> Terminal
```
sudo /opt/cxoffice/bin/cxuninstall
```

---

### Post by NickBtheITguy on 2008-11-05
Have you tried to run "sudo /opt/cxoffice/bin/cxuninstall" from a terminal window?

---

### Post by BlackAce on 2008-11-05
I didn't know about the terminal. I knew I had to do it from a command line but I wasn't sure how!


THANKS!!!

---

### Post by epopui on 2008-12-15
Yes, thank you - that worked for me too - still too new at this:guitar:

---

