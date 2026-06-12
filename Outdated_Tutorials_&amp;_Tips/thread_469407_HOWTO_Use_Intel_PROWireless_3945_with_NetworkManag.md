---
title: "HOWTO: Use Intel PRO/Wireless 3945 with NetworkManager"
date: 2007-06-09
forum: Outdated Tutorials &amp; Tips
---

### Post by noamsml on 2007-06-09
Some people (myself included) seem to have problems using NetworkManager with their Intel 3945 Wireless card. Well, I have found solution that will end all of your woes. Here it is:

1. Edit /etc/dhcp3/dhclient.conf
```

sudo gedit /etc/dhcp3/dhclient.conf

```

2. Change the line that says "timout 30;" to "timeout 100;"

3. Save and close

Changes should take effect immediately. You **do** have to be patient with the connection (it can take a long time  to connect), but overall it works.

---

### Post by noamsml on 2007-06-15
Hmmm. Another solution that seemed to work better for me was disabling ipv6.

---

### Post by BC7333 on 2007-07-28
I've been battling with wireless for two days now with Feisty on a Flybook V5 with 3945 abg.

Totally resolved with [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

in a matter of minutes.

Wireless works now.. Yahoo~!

---

