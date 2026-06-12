---
title: "Slow Wireless"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Ionosphere on 2008-04-25
So I have Sony VAIO VGN-N250E. I installed a driver for Intel PRO/Wireless 3945ABG through NDISwrapper. I have a D-Link WBR-2310 router and a 7mb cable connection. My wireless network connection ranges from 80% to 95% most of the time and yet it is extremely slow even when I'm the only one using it (wired connection works fine).
I was just wondering what might be the cause of the problem.

---

### Post by dark_harmonics on 2008-05-18
> **Ionosphere said:**
> So I have Sony VAIO VGN-N250E. I installed a driver for Intel PRO/Wireless 3945ABG through NDISwrapper. I have a D-Link WBR-2310 router and a 7mb cable connection. My wireless network connection ranges from 80% to 95% most of the time and yet it is extremely slow even when I'm the only one using it (wired connection works fine).
I was just wondering what might be the cause of the problem.

ndiswrapper is slow for me too. I think its made more for compatibility rather than speed. My broadcom wireless (in a macbook pro) only runs at like 100kbps max. Can you get a speed test result to see if anything else might be in the way?

---

### Post by sdennie on 2008-05-18
Are you sure that you have a 3945ABG card?  If so, ndiswrapper shouldn't be needed because Ubuntu 8.04 will use the iwl3945 driver for the card.  Using that driver I've seen no performance issues even while setting the card to maximum power savings.

---

### Post by Andre-D on 2008-11-03
even intripid ibex's iwl3945 drivers have same poor performance as other Ubuntus before, the ndis-drivers should have been standard.

File copy , 700MB over 54Mbit WLAN using iwl3945, = ubutu 8.10 = 7minutes21sec, windows, same hardware, same file=5minutes:7sec.

---

