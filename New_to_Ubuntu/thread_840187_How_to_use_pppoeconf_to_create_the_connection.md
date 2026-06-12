---
title: "How to use pppoeconf to create the connection?"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by legolas_w on 2008-06-25
Hi
Thank you for reading my post.
I have an ethernet modem and I configured it to connect to internet from its control panel (using the browser and connecting to the modem web based administration cosnole). The connection type is PPPoE LLC, now I want to create the connection in my computer and use it to connect to internet instead of letting the modem to connect to internet.

what I can not figure out is the way that pppoeconf works, I tried to use it but it say that it can not find andy adsl provider or pppoe peovider on eth0.

Is there anything else which I should configure before I run pppoeconf?

Thanks

---

### Post by arochester on 2008-06-25
Have you seen [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE) ?

---

### Post by superprash2003 on 2008-06-25
yes.. you need to configure your modem in bridged mode.. is this dialing procedure working with another pc like windows ?

---

### Post by sharks on 2008-06-25
type sudo pppoeconf in terminal and configure.

---

