---
title: "Ubuntu Server help"
date: 2012-04-03
forum: New to Ubuntu
---

### Post by openx on 2012-04-03
Hello, I have setup a small Ubuntu file server (Samba) to be used in our Lab at work. I am running the latest version of Ubuntu Server, all is well with that. I have it setup on the network using DHCP; my question is should it be setup using a static IP or is having it on DHCP OK?

---

### Post by papibe on 2012-04-03
Hi openx.

This is how I see it: if the services are going to be provide only on your LAN, DHCP would be just fine. If you need to provide services beyond the router to other subnetworks or the Internet, you need an static IP (or better, DHCP reservation).

Just my thoughts. Tell us if you need more help.
Regards.

---

### Post by jerome1232 on 2012-04-03
static is the way to go. If you have access to the router dhcp reserved would work too (to avoid potential conflicts if you don't have room set aside for statics)

---

### Post by openx on 2012-04-03
This is only shared within between a couple of buildings, maybe twenty people using it. It is not used should be the same subnet, and not the internet.

---

### Post by papibe on 2012-04-03
Are the server's clients going to be Windows machines?

For local addresses they use broadcasting, you won't have problems of not finding the name of the server.

Anyway, the easiest solution is to leave the config of the server 'as is', and go to the router and reserve an IP address for it.

Regards.

---

### Post by openx on 2012-04-03
Yes they are all windows, mostly XP a few Windows 7. It has been up and running about three weeks now with no problems. I am so new to the server "game" i wanted to make sure I was not missing something. It was almost scary to work the first time I set it up Lol... I am loving Ubuntu.

---

### Post by papibe on 2012-04-03
I see that you are being very careful, kudos!

This is a great place to learn, come back often!

Regards.

---

