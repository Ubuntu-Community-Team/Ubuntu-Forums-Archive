---
title: "python network traffic monitor program"
date: 2009-10-01
forum: Programming Talk
---

### Post by djsantani on 2009-10-01
I am a python beginner and I want to build a simple network monitor program that monitors the traffic of a specific port for example port 80 or port 25. When there is an activity on that specific port, it should show the transfer rate of the sending and receiving packet. Can I just do this through the /proc/net/ files, or do i need a library like pcap to do this?

Thanks.

---

### Post by j7%&lt;RmUg on 2009-10-01
Ok, i havent been able to find any code, but if you look in the python documentation on the python website, you can find all sorts of things on http requesting and FTP monitoring, i suspect there is something about port listening in their somewhere.

---

### Post by djsantani on 2009-10-01
I couldn't find what you ask me to look for but I managed to find that I can monitor the overall bandwidth of incoming packets by calculating the bytes received in the /proc/net/dev file on an interface like (eth1). But I still don't know how to get the bandwidth on a specified port only. Any help would be appreciated. Thanks.

---

