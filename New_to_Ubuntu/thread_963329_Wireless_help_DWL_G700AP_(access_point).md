---
title: "Wireless help DWL G700AP (access point)"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by Mick8882003 on 2008-10-30
I am trying to get a access point up and running, its an Ethernet wireless access point. 
I am using it to try and receive from my wireless router from my network.

It says it is connecting to the eth0, but I cannot access the ap's log in page.

Oh yes I upgraded to the beta five days ago.

Help, I have been five days without the net.

---

### Post by Mick8882003 on 2008-10-31
Bump

---

### Post by serfcx on 2008-10-31
Sounds like you have not assigned the ubuntu box to the correct network.
DWL-G700AP uses 192.168.0.50 as its default address so your ubuntu box needs to be in the same address range - for example 192.168.0.51.
Set your ubuntu box to that address as a static address then you should be able to get to your router using its default.

If you know all this then sorry to have waisted your time.

---

