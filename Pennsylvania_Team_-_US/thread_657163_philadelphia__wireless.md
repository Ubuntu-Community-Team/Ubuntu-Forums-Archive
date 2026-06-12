---
title: "philadelphia  wireless"
date: 2008-01-03
forum: Pennsylvania Team - US
---

### Post by unisol on 2008-01-03
any of you philly ubuntu guys encounter any problems with philadelphia wireless?

---

### Post by lamalex on 2008-01-03
I've heard the service is riddled with problems regardless of OS. I've never used it though, just what friends tell me.

---

### Post by unisol on 2008-01-03
i havent had any problems (with my ubuntu box) with my wireless network  until about 2 weeks ago, when they installed the wireless in my neighborhood.  when i boot up ubuntu it connects to earthlink, and not my wireless router. i suppose  philly wireless  has a stronger signal.

---

### Post by lamalex on 2008-01-04
Ah I misunderstood your question. Sorry about that. You should be able to tell ubuntu that your home router is your preferred network.

---

### Post by unisol on 2008-01-05
maybe im doing something wrong. how would you do that? you mean edit /etc/resolv.conf?

---

### Post by jedijf on 2008-01-05
If you are using network manager, which i'll presume based on the fact that you are using gutsy; click on the applet in the the panel bar and select YOUR essid as the wireless to connect to.

If you are using nm, do not edit any networking config files; interfaces in particular, or it will break nm.

See : [https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-d2b310228dc887b6cddf4465b6a53cdc4dc9be28](https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-d2b310228dc887b6cddf4465b6a53cdc4dc9be28)

for more info, and specifically:

[https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-d2b310228dc887b6cddf4465b6a53cdc4dc9be28](https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-d2b310228dc887b6cddf4465b6a53cdc4dc9be28)

for removing the earthlink connection.

---

### Post by unisol on 2008-01-06
thanks for your reply. ill get on it.

---

### Post by unisol on 2008-01-07
thanks jedijf. it worked!

---

### Post by tailsfan on 2008-04-21
When i use Ubuntu myself, I can't connect to the internet there either, it just cuts off, usually with the bcm43xx-cutter package installed

---

