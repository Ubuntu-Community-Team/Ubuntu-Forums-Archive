---
title: "aptdaemon error"
date: 2012-06-15
forum: New to Ubuntu
---

### Post by phillipmaloney on 2012-06-15
I was in the ubuntu software center installing a package and the installation froze up. I waited about 30 minutes for it to resume but it never did. I shut down the computer and started it back up. went back to the software center to try to install the same package and got an error msg that there was a programming error in aptdaemon and attempt failed. tried to install a different package and received the same error.. apparently now I can't install any software. anybody have a clue how to repair aptdaemon? thanks

---

### Post by sikander3786 on 2012-06-15
Please open up a Terminal from the Xubuntu menu and post the output of these commands:

```
sudo apt-get install -f
sudo dpkg --configure -a
```

---

### Post by phillipmaloney on 2012-06-15
sikander3786,
I ran those commands and captured the output. then just on a whim i ran ubuntu software center and tried to install a package and it worked w/o any error msgs. just running your suggested commands cleared things up. thanks much for your help. my 11.10 system is back to running perfectly. still reluctant to upgrade to 12.04. too many horror stories. if it isn't broke don't fix it.

---

### Post by sikander3786 on 2012-06-17
> **phillipmaloney said:**
> sikander3786,
I ran those commands and captured the output. then just on a whim i ran ubuntu software center and tried to install a package and it worked w/o any error msgs. just running your suggested commands cleared things up. thanks much for your help. my 11.10 system is back to running perfectly. still reluctant to upgrade to 12.04. too many horror stories. if it isn't broke don't fix it.
Yeah, those commands were meants to repair the broken packages.

Happy Ubuntu-ing! ;)

---

