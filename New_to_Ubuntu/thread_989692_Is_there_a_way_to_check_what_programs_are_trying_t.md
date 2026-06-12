---
title: "Is there a way to check what programs are trying to access the internet?"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by Vunutus on 2008-11-21
I have dialup, and with a connection this slow it's really annoying when programs think it's OK to randomly connect to the internet and try to update themselves, therefor slowing whatever I'm doing to a complete halt. This happens a lot under Windows, and it seems to happen some under Ubuntu. 

I've noticed that for a while after I first connect in Ubuntu, some program is stealthily accessing the internet and making the internet painfully slow. My best guess is that some program is downloading or checking for updates, since my update notifier thing is grayed out and says "A package manager is working", even though I never started an update. After about 30 minutes, the package manager icon turns red again and the internet speeds (lol) back up to normal. 

Are there any handy commands that would let me see what programs are using the internet so I could decide how to deal with it? Under windows, I can use the netstat command to get an idea of what executables are trying to establish connections. Is there anything like that under Linux?

---

### Post by cmay on 2008-11-21
netstat works under linux also. but the updates you talk about should be unchecked in the adminstration menu. then just set it to only notify.
hope it helps.

---

### Post by rhcm123 on 2008-11-21
I've got firestarter on a gateway machine, so i see what kinds of traffic is going, what protocol is being used, when it was done, etc.
I block stuff I don't want, blacklist stuff for kids, etc. I also check to see when stuff is accessed (i.e. i would like to know if my daughter is on the internet at 0200) :)

---

### Post by 73ckn797 on 2008-11-21
Go to System/Administration/Software Sources and turn off automatic updates. Then, whenever you want to only have the computer do that, manually check via System/Administration/Update Manager and let it work while you sip a cold one or whatever.

---

### Post by Dr Small on 2008-11-21
```
netstat -tae
```

---

### Post by Shazaam on 2008-11-21
I use iptraf. Install it via Synaptic.


P.S. - it (iptraf) runs as root so to start it enter...
```
sudo iptraf
```
in terminal.


P.S.S- it won't tell you what programs are accessing the internet.

---

