---
title: "Firewall question (Gufw)"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by sayofethos on 2013-01-03
Hi all,

I was wondering if my firewall is behaving the way it should. I am using Gufw to control the settings of my firewall. Basically my question is this; is there a way to determine if the firewall is always "on,", meaning that it is denying incoming traffic? This is the settings I have set it to, for now.

Why I'm asking is because the guwf is as shown in the first screenshot attached whenever I open the program and only upon typing the admin password will it change to be like in the second screenshot, where the bar has gone from "off" to "on." Does this mean that the firewall will be configured to be "on" only when the admin password is typed each time one logs in, or is it always on, as it ought to be anyway?

Thanks a lot to anyone who can clear this up!

---

### Post by haqking on 2013-01-03
> **sayofethos said:**
> Hi all,

I was wondering if my firewall is behaving the way it should. I am using Gufw to control the settings of my firewall. Basically my question is this; is there a way to determine if the firewall is always "on,", meaning that it is denying incoming traffic? This is the settings I have set it to, for now.

Why I'm asking is because the guwf is as shown in the first screenshot attached whenever I open the program and only upon typing the admin password will it change to be like in the second screenshot, where the bar has gone from "off" to "on." Does this mean that the firewall will be configured to be "on" only when the admin password is typed each time one logs in, or is it always on, as it ought to be anyway?

Thanks a lot to anyone who can clear this up!

```
sudo ufw status
```

---

### Post by deadflowr on 2013-01-03
gufw is just a graphical frontend for ufw(which is a frontend for iptables).

In a terminal:

```
sudo ufw status
```
will give you the state of your firewall and what rules you've allowed and such.

You can man ufw, or ufw --help for more info.

---

### Post by coldcritter64 on 2013-01-03
The above 2 posts give you a terminal method to test at any time. 

If, after entering your password to unlock,the interface shows as ON, then the firewall was on all the time. The interface itself (gufw) needs elevated privileges to even read the firewall state, hence the greyed out settings on initially starting.

The behaviour you're seeing is normal for gufw.

---

### Post by sammiev on 2013-01-03
Here is a really good [read]("http://ubuntuforums.org/showthread.php?t=1876124") if you want to play a little and tight your firewall a little more.

---

### Post by sayofethos on 2013-01-03
Alright, seems like the ufw is working just as it should. Doubts cleared, thanks for your help!

---

