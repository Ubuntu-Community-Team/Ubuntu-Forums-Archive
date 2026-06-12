---
title: "Lost network"
date: 2011-09-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by tajreed on 2011-09-02
Most recent updates to Beta 1 and my network is gone. Any thoughts. I had wireless and Lan after the install of B-1. Then the updates, 100+, and no network.

---

### Post by cariboo on 2011-09-03
What do you mean by no network? Is there no Network Manager Icon? Can you connect via a wired connection using:

```
sudo dhclient ethX
```

Where ethX is your wired network device.

What is the output of:

```
sudo lshw -C network
```

---

### Post by tajreed on 2011-09-03
The icons were there they but no wireless or wired available.
I did a clean reinstall and all is well, but I've been reluctant to upgrade to the latest network packages (4 out of about 167). I believe that is what killed my network. We'll have to see how things go. As for now, all is well. I'll probably try to avoid those network upgrades for a while.

Thanks for the reply.

---

