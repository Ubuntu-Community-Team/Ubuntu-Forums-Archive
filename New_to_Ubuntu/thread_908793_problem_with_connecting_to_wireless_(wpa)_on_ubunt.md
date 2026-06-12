---
title: "problem with connecting to wireless (wpa) on ubuntu 8.04"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by andrep182 on 2008-09-02
I just recently upgraded ubuntu to 8.04. At home, I can connect to my router via wireless (using wpa personal security) and have no problem connecting to it. However, when I tried to connect to my friend's router (same setting, wpa-personal) I have a hard time connecting to it. When I switched to windows (i know, don't boo me please =) ) the wireless connect just fine, however ubuntu doesn't seem to be able to connect to it. Is there some kind of things i can do to check this? Is this because the password was too long (stupid question but thought I throw it out there). thank you

---

### Post by cwsnyder on 2008-09-03
You might want to check your workgroup setting under Ubuntu, unless your friend is running as a Wi-Fi hotspot.  Of course you will have to use the WPA password which matches your friend's router WPA password.

---

### Post by knattlhuber on 2008-09-03
Could that be related to having a WPA AES on one network vs. WPA TKIP key on the other?

---

### Post by solaceinsilence9 on 2008-09-03
it could be a number of things... on the Ubuntu side I would check to make sure your password settings are correct like mentioned above. That is a common problem if you have the same ssid. Alot of people will leave their network name set to the default. This is especially true with linksys routers. The wifi will show up as 'linksys' as the network name. Even though it is a different network your NIC will think it is the same since the name is the same.

Also it could be due to some security measures set up on the router itself. An, example would be like with my router... I have the WIFI set up to only accept my MAC address and disregard requests from any other wifi devices that dont have my MAC address.

---

