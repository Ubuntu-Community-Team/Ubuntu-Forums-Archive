---
title: "no internet..."
date: 2008-05-13
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-05-13
I have just removed firestarter from ubuntu (via synaptic) as it would conflict with moblock but now i cant access the internet it says that the wirless connection is all up and running, so does this have something to o with my iptables?

please help

---

### Post by phidia on 2008-05-13
You/we probably need to know the card type you are using to troubleshoot the connection problem.

You can type in a terminal > lshw -C network and post the output here perhaps lspci -v and iwconfig will help too.

---

### Post by kamitsukai on 2008-05-13
ok it was definatley something to do with my iptyables as i tried this command

```
 sudo iptables -F
```

which i think disbales the iptables firewall? anyway my internet is now working :)

---

