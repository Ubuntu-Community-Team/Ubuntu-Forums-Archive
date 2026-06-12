---
title: "Problem with security updates which lag down my pc"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by Jazziejamez on 2012-02-17
Hello there :)

I post here to ask if there is any way in which I can see the last updates I made in my Ubuntu, and how to deactivate them. Let me explain. 
About 4 or 5 days ago, and having installed Ubuntu Natty Narwhal, and later updated to Oneiric Ocelot, the update window told me to install two last "security updates", which I did. The problem is that since then (since I rebooted the system), the pc remains working at the same speed, etc, but my internet has slowed down to almost nihil. I mean, it takes 2 or 3 minutes to load webs like Facebook, and that when it loads it instead of dropping due to timeout etc.

Is there a way I can see what updates I installed last, and how to deactivate them? Please, this is a hell, It's taken me like 20 minutes to register myself on Launchpad and Ubuntu forums, this works soooo slow :(

Thanks in advance!

---

### Post by Jazziejamez on 2012-02-19
Bump.

Doesn't anybody know how to fix this? :(

---

### Post by Dangertux on 2012-02-19
Generally speaking it is unlikely that a security update affected your bandwidth or latency. 

Do you have apparmor enforcing a profile for Firefox? This could have been changed by the update, though it is still unlikely to produce what you are experiencing.

I would recommend looking at any other changes you made to your system. Also it is quite possible that your internet service provider or a router between you and the sites you are visiting are having problems or experiencing unusually high load.

Hope this helps

---

### Post by wildmanne39 on 2012-02-19
Hi, welcome to the forum!, is this wireless internet? 

Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

