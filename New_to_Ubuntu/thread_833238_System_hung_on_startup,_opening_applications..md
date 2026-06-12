---
title: "System hung on startup, opening applications."
date: 2008-06-18
forum: New to Ubuntu
---

### Post by melrokz on 2008-06-18
[FONT="Comic Sans MS"][SIZE="4"]Hi! I'm Melvin from Kerala,India. I installed Ubuntu 7.10 gutsy gibbon and figured out to surf the net through Ethernet on it. I used synaptic package manager to update the list of packages through the net, but the net got disconnected soon after.
      Now, Ubuntu takes a long time to boot up. the graphical display dissapears and a message is displayed thus:'starting cupsd' 
After logon also, it takes a long time to load and messages popped up telling that some of my panel applets are not working (network monitor, volume control)! well, all applications take a long time to start!
       What should I do apart from formatting, to get Ubuntu working normally again?
       Also will someone be kind enough to mail me common problems and solutions in ubuntu?[/SIZE][/FONT]

---

### Post by steve101101 on 2008-06-18
you post likely need to fix the broken packages.

---

### Post by YaroMan86 on 2008-06-18
You say that this problem happens when you log into GNOME?

---

### Post by steve101101 on 2008-06-18
```


sudo apt-get check


```

---

### Post by steve101101 on 2008-06-18
also before login if you need to get to the terminal press ctrl,alt,F1 all at the same time. you will have to login like normally, but this may allow you to run commands.

---

### Post by melrokz on 2008-06-18
Yes, I tried changing the session to GNOME. Doesn't help.

---

### Post by steve101101 on 2008-06-18
what about checking for broken packages.

---

### Post by bijeeshvs on 2008-06-18
melvin you have to fix those broken packages first and do it from command prompt (login to command prompt from the login screen)

where are you in kerala...................

---

### Post by steve101101 on 2008-06-18
> **bijeeshvs said:**
> melvin you have to fix those broken packages first and do it from command prompt (login to command prompt from the login screen)

where are you in kerala...................

yes. log into the terminal ... then use my command from above to fix broken packages.

---

### Post by melrokz on 2008-06-18
I'm in Kakkanad, Kochi. I'll try to fix broken packges using the code and will come back after some time. (right now, I'm in windows)

---

### Post by bijeeshvs on 2008-06-19
me from kottarakkara, kollam

---

