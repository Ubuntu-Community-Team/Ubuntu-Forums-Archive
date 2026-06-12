---
title: "FireStarter configuration"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by Ntweat on 2008-09-12
hi... although firestarter is a great firewall and it has protected my comp fully but here somethings that are creating problem

1. I access my comp by SSH but when firestarter is on i cant connect to it

2. we use DC++ in college but for me to download i need to accept incoming UDP connection i can upload to other users as it allows out going connections....

well i do need to keep my ports masked and not to send any ping replies as on the college lan there are ppl eager to attack comps.... thanks

(PS if the ports are hidden but connections are allowed and ping on my comp does not work its good enough for me)

---

### Post by oilchangeguy on 2008-09-12
> **Ntweat said:**
> hi... although firestarter is a great firewall and it has protected my comp fully but here somethings that are creating problem

1. I access my comp by SSH but when firestarter is on i cant connect to it

2. we use DC++ in college but for me to download i need to accept incoming UDP connection i can upload to other users as it allows out going connections....

well i do need to keep my ports masked and not to send any ping replies as on the college lan there are ppl eager to attack comps.... thanks

(PS if the ports are hidden but connections are allowed and ping on my comp does not work its good enough for me)

this has been said before, you don't need firestarter. it's not a firewall, it's simply an un-needed user interface. ubuntu has a firewall called iptables, that in MOST cases requires NO user input.

---

### Post by Ntweat on 2008-09-12
hey i knw abt iptables but i jst turned to linux this jan so i dont knw that much can u explain to me how to configure the iptables......

---

### Post by oilchangeguy on 2008-09-12
> **Ntweat said:**
> hey i knw abt iptables but i jst turned to linux this jan so i dont knw that much can u explain to me how to configure the iptables......

You're a college student, right? Would it kill you to correctly spell all words? And did you read the part where I noted that iptables requires no user input?

---

### Post by Ntweat on 2008-09-12
Well sorry about the spelling before and that i forgot to mention with all the things running by default my computer is still vunerable to attacks..

---

### Post by crazypenguin2008 on 2008-09-12
as far as i know there is no viruses/threats that can attack linux like it does windows...but i could be wrong

---

### Post by oilchangeguy on 2008-09-12
> **Ntweat said:**
> Well sorry about the spelling before and that i forgot to mention with all the things running by default my computer is still vunerable to attacks..

from what? this is not windows.

---

### Post by 03impy on 2008-09-12
Arent the ports blocked my default in ubuntu so you arent vulnerable?

Pete

---

### Post by Ntweat on 2008-09-12
well.... port scan show my ports open and a person from my college had sent a mailbomb attack to my computer without me knowing he just did not enable it and send me the screenshot... so i am a little tensed....

---

### Post by Ntweat on 2008-09-12
***************bump***************

---

### Post by adult swim on 2008-09-12
the firewall is on with ports closed by default.  firestarter is a program that is used to change firewall settings, but it is not a firewall itself, and firestarter is no longer updated.  the new firewall "controller" is call ufw, it is a command line interface.  to use it, open up a terminal, and type in ```
sudo ufw enable
``` check and see which ports are open with ```
sudo ufw status
``` it will list all of the ports that are open.  if you want to open or close a port, type in the following, respectively ```
sudo ufw allow (whatever port # you want to open)
sudo ufw delete allow (whaterver port # you want to close)
```

---

