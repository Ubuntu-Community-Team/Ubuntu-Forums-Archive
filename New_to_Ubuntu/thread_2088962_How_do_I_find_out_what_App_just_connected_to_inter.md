---
title: "How do I find out what App just connected to internet?"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by LABcqX on 2012-11-27
How do I tell the ubuntu to report what app connected to the internet?

I am learning of CLI programs that report connections but an App connected to the internet and the description of it disappeared from the Terminal window before I had a chance to examine it. 

I looked at the firewall log but it say nothing about what Apps are connecting to the internet. So how do I learn what App connected to the internet in the last 10 minutes or so?

Why is there no log report of what Apps are connecting to internet? How do I get this?

---

### Post by oldos2er on 2012-11-27
```
lsof -i -n -P
``` More info on that command in this old thread: [http://ubuntuforums.org/showthread.php?t=1659971](http://ubuntuforums.org/showthread.php?t=1659971)

---

### Post by StinkySQL on 2012-11-27
Hah! Learned something new!

---

### Post by LABcqX on 2012-11-28
> **oldos2er said:**
> ```
lsof -i -n -P
``` More info on that command in this old thread: [http://ubuntuforums.org/showthread.php?t=1659971](http://ubuntuforums.org/showthread.php?t=1659971)

You didn't answer my question. 

I am already using the CLI lsof.


[QUOTE=an App connected to the internet and the description of it disappeared  from the Terminal window before I had a chance to examine it.[/QUOTE]

How do I learn what app connected after it disappeared from the CLI? I looked at the Terminal and just saw the last second or so of a connected App before its entry disappeared. Is there a way to log the CLI reports? It's unrealistic to expect that I can monitor the CLI constantly. How do I find out about apps that connect that I don't see or that I missed?

---

### Post by oldos2er on 2012-11-28
There's no mention of lsof in your OP. If you're looking for something that continually monitors network activity, you might want to search in Software Center. I don't know of any tools that do so on a per-application basis though (that doesn't mean there aren't any).

---

### Post by haqking on 2012-11-28
> **LABcqX said:**
> How do I tell the ubuntu to report what app connected to the internet?

I am learning of CLI programs that report connections but an App connected to the internet and the description of it disappeared from the Terminal window before I had a chance to examine it. 

I looked at the firewall log but it say nothing about what Apps are connecting to the internet. So how do I learn what App connected to the internet in the last 10 minutes or so?

Why is there no log report of what Apps are connecting to internet? How do I get this?

what sort of logging is your firewall set to do ?

they will be in syslog generally other than your firewall specific log such as ufw.log

and wireshark and tcpdump are some of many you can use to monitor what is doing what on the network etc.

---

### Post by LABcqX on 2012-11-30
> **oldos2er said:**
> There's no mention of lsof in your OP. If you're looking for something that continually monitors network activity, you might want to search in Software Center. I don't know of any tools that do so on a per-application basis though (that doesn't mean there aren't any).

I tried a bunch of the different ones available. They all do basically the same thing. The CLI programs that report connections, like LSOF.



> **haqking said:**
> what sort of logging is your firewall set to do ?

they will be in syslog generally other than your firewall specific log such as ufw.log

and wireshark and tcpdump are some of many you can use to monitor what is doing what on the network etc.

I am using the ufw.log. Wireshark does not tell what applications are connecting. The lsof etc display the application. But if you miss the display and it disappears, how can I find out what it did display? It seems like there's got to be a way to record this. How do people keep track of what applications are making connections on the computer? You can't watch every connection in real time. I'm wanting to know how you guys record what applications make connections to the internet. Like if I want to find out what applications are requesting DNS lookups, how would I go about learning this information?

---

### Post by oldos2er on 2012-12-08
I stumbled across this today: [http://nethogs.sourceforge.net/](http://nethogs.sourceforge.net/)
Maybe it's what you're looking for?

---

