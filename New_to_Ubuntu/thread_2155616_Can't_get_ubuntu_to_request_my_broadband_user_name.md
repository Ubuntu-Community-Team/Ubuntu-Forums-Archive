---
title: "Can't get ubuntu to request my broadband user name and password"
date: 2013-06-18
forum: New to Ubuntu
---

### Post by Radical_Dreamer on 2013-06-18
When I try to connect to my router, it request the password for that, but never asks for the broadband user name and password so I can't get on the internet.  What should I do?

---

### Post by Radical_Dreamer on 2013-06-18
Also, is there a way to configure the router to have this information (like enter it in router settings?) because my dad is having difficulty with getting cellphones and things to connect as well

---

### Post by gordonempire on 2013-06-18
What kind of internet service do you have (ie. Cable/DSL/Sat)? Is there a modem that the router connects to or does it contain the modem internally? Do you have anything connected directly to the router via ethernet cable? If so, does it connect to the internet?

---

### Post by HiImTye on 2013-06-18
do you need to connect using PPPoE (or similar)?[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by mansonfan78 on 2013-06-18
You can access your router's settings by entering "http://192.168.0.1" (without the quotes) in the address bar of your browser.  Look through it's settings for a place to enter a username and password for dns settings.  This will probably be buried in some submenu - if it's an easy to find username/password entry it is most likely for the router itself and not your isp.

---

### Post by HiImTye on 2013-06-18
> **mansonfan78 said:**
> You can access your router's settings by entering "http://192.168.0.1" (without the quotes) in the address bar of your browser.

the router can be located anywhere in the 192.x.x.x or even the 10.x.x.x ranges (or others, but these are typical). you can find the ip by```
ip route show | grep default
```and it will be listed as similar to```
default via **192.x.x.x** dev eth0 proto static
```

[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

