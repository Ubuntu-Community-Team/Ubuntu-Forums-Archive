---
title: "Trouble spoofing mac address"
date: 2016-10-11
forum: New to Ubuntu
---

### Post by chilltech on 2016-10-11
Hey guys, I'm having an issue when I try to spoof my wireless NIC. The problem is that once i try to connect to WAP the mac address reverts back to the original one. 
So fare I've tried this, but I keep having the same issue:( If you guys have any ideas please let me know.

```

ifconfig interface down
macchanger -r interface
ifconfig interface up

```
and 
```

ifconfig  interface down
ifconfig  interface hw ether 00:11:22:33:44:55
ifconfig  interface up

```

---

### Post by &amp;KyT$0P# on 2016-10-11
Use NetworkManager's "Cloned MAC address" option instead of macchanger.

---

### Post by chilltech on 2016-10-11
Thanks halogen2, that fixed the issue. Still wonder why the other methods don't work anymore. They worked on the older versions of Ubuntu just not *Xenial.*

---

### Post by &amp;KyT$0P# on 2016-10-11
You're welcome. :KS

How did you ever get macchanger working for you?  It didn't work for me at all when I tried it in trusty.

If there is a change in xenial it might be related to [this]("https://blogs.gnome.org/lkundrak/2016/01/18/networkmanger-and-tracking-protection-in-wi-fi-networks/")?  Just a guess.

---

### Post by chilltech on 2016-10-16
Thanks for the link halogen2, Unfortunately I never tried in it  trusty. It worked fine for me in 15.04 tho. If I run across a solution I will let you know. Thanks again for the help.

---

