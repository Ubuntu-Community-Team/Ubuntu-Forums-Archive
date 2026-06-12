---
title: "[SOLVED] ethernet stopped working"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by ibznorange on 2008-10-02
I was working online today when my power blacked out for a fraction of a second, just long enough to turn of my computer, TV etc. When i powered back up, i have no internet. I shut down, rebooted into XP (safety blanket lol) and i have internet, so my card is not fried. I loaded sysinfo and it doesn't show my Ethernet card, but when i run Ubuntu's hardware test it picks up my Ethernet just fine. 

Somebody suggested that the driver got deleted during the blackout, but couldnt tell me how to fix it. I went into the network manager thing, and turned roaming on, then off (and back into dhcp like before) and nothing. When roaming is enabled, all pages/attempts to access the web just go to server not found immediately, but when i disable it and go to dhcp it takes a minute trying to search before saying it couldnt find the server. i cant even log in to my router 

running hardy with all the latest updates (as far as ubuntu tells me anyways)

---

### Post by Kellemora on 2008-10-02
Hi IBZ

We had a couple of older computers that did that quite often to us.  One little hiccup in the power and we would lose internet and LAN both.

Doing a soft restart didn't help, we had to physically power down the computers and do a COLD restart, often TWICE in Succession to get things back to normal again.  Something to do with pointers or stack in the kernel is what we were told, but that's above my head.

Just try two COLD boots in a row, not restarts, COLD BOOTS after normal shut-downs.  If that don't do it, maybe one of the many Guru's here will have an idea for you to try.

TTUL
Gary

---

### Post by ibznorange on 2008-10-03
That didnt work. I tried booting into xp again to make sure it works and its workign flawlessly, so the chip is fine

Any other ideas guys??

---

### Post by bcom on 2008-10-03
Go to Terminal and type ifconfig to see what IP address (if any) your router is assigning to the computer.

Perhaps you could also power everything down, including the router.  After a minute or two, power up the router first, wait a few seconds and then power up the computers on the network one at a time.

---

### Post by cariboo on 2008-10-03
Have you tried in a terminal:

```
sudo dhclient eth0
```

Substitute your your network adapter for eth0 if it is different

To see if your nic will pick up an ip address. If that doesn't work, try:

```
sudo /etc/init.d/networking restart
```

Jim

---

### Post by ibznorange on 2008-10-08
deleted etc/network/interfaces and it started working again. 

how do i mark a thread solved?

---

### Post by Iowan on 2008-10-08
Look under Thread Tools - on the menu line above the posts (beside View First Unread... it's in red letters on my system.)

---

### Post by ibznorange on 2008-10-08
thank you much

---

