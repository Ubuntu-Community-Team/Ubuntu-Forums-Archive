---
title: "Connecting to the internet 12.10"
date: 2013-02-21
forum: New to Ubuntu
---

### Post by 12roby21 on 2013-02-21
I recently partitioned Ubuntu 12.10 with Windows 8 on my HP laptop . When I load Ubuntu, everything runs fine but no WiFi networks show up as found so I cannot connect to the internet. I think Ubuntu cannot find my NIC. is this why? If not, what am I doing wrong? Completely new user, any advice helpful

---

### Post by sandyd on 2013-02-21
> **12roby21 said:**
> I recently partitioned Ubuntu 12.10 with Windows 8 on my HP laptop . When I load Ubuntu, everything runs fine but no WiFi networks show up as found so I cannot connect to the internet. I think Ubuntu cannot find my NIC. is this why? If not, what am I doing wrong? Completely new user, any advice helpful

Do you have a Ethernet port on your laptop?

If you do, please plug it into the router.
Click on the Unity Dash (the Ubuntu Logo at the top-left of the screen) and type in "Hardware Drivers". Open the utility that appears.

If the utility is unable to find any drivers, Open a terminal (type in 'terminal'), and copy and paste the following (the password entry in the terminal does not show, but rest assured that it is being entered).

```

ifconfig
lspci | grep Network
```

thanks!

---

