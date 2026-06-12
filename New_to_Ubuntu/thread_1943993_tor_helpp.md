---
title: "tor helpp"
date: 2012-03-20
forum: New to Ubuntu
---

### Post by Aya13 on 2012-03-20
Hello new friends! I am new to the ubuntu community and to Linux! If anyone could help me properly install tor, and give me some suggestions and tips on how to run it well,id be very grateful:) or if so,redirect me to the solution. Hope to become of some use in the future as I learn more, thank you:) I'm running Unbuntu 11.10

---

### Post by lechien73 on 2012-03-20
Hello & Welcome to the forums,

You can download TOR from [www.torproject.org](www.torproject.org).

Once you have downloaded it, open a terminal window and type the following:

```
tar -xvzf ~/Downloads/tor-browser-gnu-linux-x86_64-2.2.35-9-dev-en-US.tar.gz
cd tor-browser_en-US
./start-tor-browser
```

This is presuming you have downloaded the US English 64-bit edition. If not, then change the **en-US** for your language and **x86_64** to **i686**

---

### Post by Aya13 on 2012-03-20
What if I'm using 32 bit Ubuntu D:

---

### Post by aromo on 2012-03-20
> **Aya13 said:**
> What if I'm using 32 bit Ubuntu D:

That means that you are NOT using the 64-bit edition, therefore:

> **lechien73 said:**
> ... If not, then change ... **x86_64** to **i686**

---

### Post by muppet317 on 2012-03-20
alternatively, (especially for basic tor users) you can just add tor and vidalia, a simple gui for tor, through synaptic package manager

---

