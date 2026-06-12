---
title: "Internet/network intermittent"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by cdmjjp on 2012-06-11
I have been using ubuntu for about 9 months and like everything new it takes getting used to, especially if you are just a user. The computer has both version 11.10 and windows vista. Recently the internet/network, (I have a home server), connection would come on for about 10 seconds and then drop out for 2 or 3 secs, connect again for 10 seconds and then drop out again for 2 or 3 seconds. This is a repetitive pattern the whole time the computer is connected to Ubuntu. Whenever I try to update and/upgrade the intermittent connection causes a failure and the computer tells me that it cannot complete the service. However when I boot up into Vista the connection is absolutely stable. Can anyone help?

---

### Post by spikoley on 2012-06-11
How are you connected?  Is it wireless or ethernet?

---

### Post by cdmjjp on 2012-06-12
Ethernet

---

### Post by cdmjjp on 2012-06-16
This post has been here for three days. Does this mean No one can help me?

---

### Post by steeldriver on 2012-06-16
> **cdmjjp said:**
> This post has been here for three days. Does this mean No one can help me?

I think it's more to do with intermittent problems often being hard to diagnose - plus you're not really giving us any information

In what way exactly is it dropping? packet loss? computer loses its ip address (dhcp lease)? ethX becoming not ready / not available?

What ethernet adapter / chipset do you have? (something like 'lspci -vnn' should tell you)

What kind of router are you using and how are IP addresses managed (pure DHCP? pure static? DHCP with some kind of reservation?)

---

