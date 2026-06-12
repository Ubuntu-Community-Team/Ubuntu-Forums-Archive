---
title: "[SOLVED] Can't detect Wireless Network"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by Haruki-kun on 2008-10-06
I'm a new user. This morning, I was happily on my laptop in the library, talking to people and browsing the web when all of a sudden, the Computer shuts down. The battery ran out, and I hadn't fixed it so it would warn me or hibernate or anything else.

"No biggie," I thought. I simply plugged the computer in, restarted it, booted Ubuntu, went to the battery settings menu, and fixed that. But then, when I got on aMSN, I realized I couldn't log in, which was weird. I turned to the upper right hand corner and saw that I was offline.

"Again, no biggie," I thought. I went to the Wireless Network list to reconnect, but I was very surprised to find that there were no networks in the list. I looked around, and pretty much everyone still had the network fine, so I discarded it being a problem with the network. I moved, went to class, went to another classroom, and still, no detection of Wireless Networks.

So what problem is it? Can anyone help me fix this, please?

---

### Post by Titan8990 on 2008-10-06
Often times my first guess would be an easily hittable wireless on/off switch on the laptop. Otherwise I would check my interfaces with: ifconfig. If ath0 or wlan0 did not exist in the ifconfig list I would either do:

sudo ifconfig ath0 up

or

sudo ifconfig wlan0 up


depending on my wireless card.

---

### Post by superprash2003 on 2008-10-06
please post output of iwconfig and lshw -C network

---

### Post by Haruki-kun on 2008-10-06
Whoa... thanks! But... ehm... apparently it just fixed itself! :redface:

Thanks anyway. BTW, how do I change the title to read "Solved"?

---

### Post by Titan8990 on 2008-10-06
"Thread Tools" above your original post.

---

### Post by crossnt0 on 2010-06-10
Thanks!

---

