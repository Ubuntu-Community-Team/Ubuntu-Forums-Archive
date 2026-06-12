---
title: "How can I use init.d (or some other method) to run a screen script on boot up?"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by ATLChris on 2013-02-19
I have a shell script that runs inside of a screen session and loops the script continuously every 10 minutes (never ends). I was wondering how I might initiate the screen session, run the shell script, then detach from it on boot.

I like being able to attach to the screen session to see the output of the script from time to time.

Right now I run this:

```
screen
sh /var/www/scripts/screen.sh
ctrl+ad (to detach)
```

---

### Post by ATLChris on 2013-02-22
I still have not had any luck figuring this out. Can anyone in the community help me out?

---

