---
title: "A newbie needs help writing/editing a script"
date: 2007-02-09
forum: Programming Talk
---

### Post by keith11 on 2007-02-09
Hi everyone, I am trying to connect to my university vpn through vpnc in ubuntu edgy. When I type vpnc in the console, it asks me to type in all the details one by one, like the group name, secret, etc. The problem I face here is that whenever I have to connect to the vpn of my university, I have to type in all the details again in the console. I was wondering if there is a way I can write a script (I have absolutely no experience writing a script) which would have all the details for my university account already fed in and I would just have an icon to click on to log in. Is it possible? If yes, could someone help me here? Thanks a lot.

---

### Post by cwaldbieser on 2007-02-09
> **keith11 said:**
> Hi everyone, I am trying to connect to my university vpn through vpnc in ubuntu edgy. When I type vpnc in the console, it asks me to type in all the details one by one, like the group name, secret, etc. The problem I face here is that whenever I have to connect to the vpn of my university, I have to type in all the details again in the console. I was wondering if there is a way I can write a script (I have absolutely no experience writing a script) which would have all the details for my university account already fed in and I would just have an icon to click on to log in. Is it possible? If yes, could someone help me here? Thanks a lot.

You should just be able to create a config file like:
```

IPSec gateway <...>
IPSec ID <...>
IPSec secret <...>
Xauth username <...>
Xauth password <...>

```

The <...> just mean fill in the blank with the appropriate info.

The you can just call vpnc with the path to the config file.
```

$ sudo vpnc ./university.conf

```

---

### Post by keith11 on 2007-02-09
Thanks for your help. 
1. I created a *.conf file and added all the required information. Unfortunately, it doesn't resolve the gateway address, which it does otherwise, when I try adding information through the console, one-by-one.
2. I also tried to create a launcher on the desktop and I put sudo vpnc ./pathtothe *.conf as the input in the "command" box of that launcher. I then made the launcher file executable. I created the launcher being a user, not su. The launcher didn't work. 

Any further help on these two issues? Thanks.

---

### Post by nereid on 2007-02-09
Use gksudo instead of sudo for your launcher. Sudo is a console application and your version won't start a new terminal, where sudo could run.

Isn't there a GTK vpnc frontend available (for KDE there is KVpnc)?

---

### Post by keith11 on 2007-02-11
Yes, I had tried Kvpnc but somehow it never worked for me. I entered all the information and even ran it as a superuser, but it always couldn't connect because after starting vpnc it always timed out.

I used gksudo in the command box and it did work. I clcked on it and it asked for the password. After entering the password there was no prompt or anything. So I assumed I was connected but then I tried to enter a network drive of my university and I couldn't. So I think I am still not able to connect. Any suggestions? Thanks.

---

### Post by keith11 on 2007-02-11
I figured out that I had to remove "<>" from all entries in the *.conf file I created. It seems to work fine now. Thanks for all the help. For someone having a similar problem there are options like gvpnc on [http://code.google.com/p/gvpnc/](http://code.google.com/p/gvpnc/).

---

