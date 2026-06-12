---
title: "Media Server Set Up"
date: 2012-02-12
forum: New to Ubuntu
---

### Post by glenak1911 on 2012-02-12
Hi guys, I'm pretty new to Linux/Unix but I've always respected it.

I just set up a media server running on Ubuntu Server Edition 11.1 and I've installed MediaTomb to stream my media to my Playstation 3 and also forked-daapd so I can stream with iTunes.

So far so good, but I noticed that on iTunes I'm not able to drag and drop music files from iTunes to my iPhone. I'm not sure if anyone can give me a remedy to this, or if the media files need to be on the local computer.

---

### Post by androssofer on 2012-02-13
> **glenak1911 said:**
> Hi guys, I'm pretty new to Linux/Unix but I've always respected it.

I just set up a media server running on Ubuntu Server Edition 11.1 and I've installed MediaTomb to stream my media to my Playstation 3 and also forked-daapd so I can stream with iTunes.

So far so good, but I noticed that on iTunes I'm not able to drag and drop music files from iTunes to my iPhone. I'm not sure if anyone can give me a remedy to this, or if the media files need to be on the local computer.

not sure how you could go about this.. you could perhaps create a samba share or NFS directory on your server and mount it on the client machine, then your itunes would see them as local, but really they stream over the network ;-)

---

### Post by glenak1911 on 2012-02-14
Thanks I just mapped the drive, I'm transferring my media to the server now! We'll see if it works!

---

