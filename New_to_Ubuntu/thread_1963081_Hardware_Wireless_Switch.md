---
title: "Hardware Wireless Switch"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by metzy85 on 2012-04-21
I am really at a loss on this one. I just installed Ubuntu 12.04 on my new laptop. Get it all booted up and it says that my wireless is turned off at the hardware level. So I hit the f2 on my keyboard which doubles as turning the wireless on. Funny enough it turns the blue tooth on and off. How can I get my wireless turned on. 

Dell Vostro 3450

---

### Post by williejones on 2012-04-21
Please run the following command in a terminal and post the output.  It may give some clue.

```
rfkill list all
```

---

### Post by metzy85 on 2012-04-22
******@Ubuntu****** :~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

