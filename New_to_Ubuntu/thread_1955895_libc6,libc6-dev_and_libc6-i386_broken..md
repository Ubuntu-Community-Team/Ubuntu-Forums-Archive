---
title: "libc6,libc6-dev and libc6-i386 broken."
date: 2012-04-10
forum: New to Ubuntu
---

### Post by cmundy on 2012-04-10
hi, im very new to ubuntu, only been on a few days and ive encountered this problem. Everything was working fine until i shut down one night and restarted in the morning. Wheni logged on i found that i had no internet connection and when i visited the network manager it said "The system network service is not compatible with this version". After some other looking around i found that the libc6, libc6-dev and the libc6-i386 packages were broken. The only thing that i have done on ubuntu was install the java, synaptic manager and tried to install skype. However this failed and it told me it would be dangerous to install. So if anyone could help to shed some light on this situation as i could not find much info on the internet. Remeber, im a total noob on ubuntu.

---

### Post by flurospar on 2012-04-10
I'd suggest a reinstall of Ubuntu, but how you got it so much screwed up is something beyond me.

---

### Post by cortman on 2012-04-10
A reinstallation may be the only fix, but first try running the following in a terminal-

```
sudo apt-get install -f
sudo apt-get autoremove
sudo apt-get autoclean
```

See if that will resolve anything.

---

