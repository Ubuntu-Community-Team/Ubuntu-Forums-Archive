---
title: "sos mac and ip question"
date: 2012-12-03
forum: New to Ubuntu
---

### Post by gominan on 2012-12-03
hi.i would like to ask if someone knows my mac adress of my wireless usb adapter can they find to whitch computer or whitch ip it was connected in the past?

---

### Post by Cheesemill on 2012-12-03
There is a small chance that this would be possible by doing a forensic analysis of log files, but to find out someone would need full access to ***all*** of the computers and ***all*** of the network devices that the adapter ***may*** have been attached to.

---

### Post by gominan on 2012-12-03
thanks for answering but what you mean is than even if the adapter is not connected anymore.if they have the nymber they can find the ip?i am from a country tha free launching is not allowed...

---

### Post by Mark Phelps on 2012-12-03
IF you're asking, if someone obtains your USB Wireless adapter, can they find out WHERE you've been visiting on the Web?

The answer is ... possibly ... depending on what logs are retained.

For example, say I do the following:
1) use the USB adapter to connect to my router which connects to a cable modem which connects to my ISP, 
2) that ISP uses MacAddress filtering to validate account access,
3) that ISP then assigns me a dynamic IP address (this associates an IP address with an ISP account userid)
4) I then visit a website
5) My ISP captures that website address and retains it in a session log

Since the ISP logs may contain MacAddress (of my device), IP Address (assigned to me), and Website addresses (that I visited) -- then yes, if you have access to the ISP log, you can find out, based on my MacAddress, what sites I visited.

I do know that SOME ISPs use MacAddress validation because, when I have changed network hardware (thus changing the MacAddress), I then  had to contact the ISP Admins and provide the new MacAddress.

Also understand that ISPs generally validate demographic information when creating user accounts -- so they typically have your real name, address, and other information.

There are ways to surf the Web anonymously, of course, but this requires using proxies that send you THROUGH service providers/access points that do NOT do logging.

---

