---
title: "How to remove Ubuntu desktop envirenment and remplace it by kde?"
date: 2016-12-18
forum: New to Ubuntu
---

### Post by abdessamadel on 2016-12-18
Hi! brothers
i installed ubuntu 12.04 to my laptopm but i get it very slow, so i want to change the GUI from the default to other classic one.

---

### Post by wildmanne39 on 2016-12-18
Open the terminal and do:
```
sudo apt-get install gnome-session-fallback
``` 
Logout from the existing session. Once you are at the logon screen click the option to change your session then choose Gnome Classic to logon and enter your password.

Having said that, 12.04 reaches EOL in  few months so there will no longer be updates, no support of any kind so I recommend you up grade to a new version, and if you have an older computer you should try lubuntu or xubuntu.

---

### Post by Impavidus on 2016-12-18
As you mention kde in the title, you can also use Kubuntu. Converting Ubuntu to Kubuntu may give you a lot of duplicated software or stuff not nicely fitting in, and version 12.04 is almost end-of-life, so installing or at least trying in a live session of Kubuntu 16.04 may be a good idea too.

Note that Ubuntu LTS releases get 5 years of support, the other flavours (X/L/Kubuntu) 3 years, except Kubuntu 12.04 and 14.04, which also have 5 years.

---

