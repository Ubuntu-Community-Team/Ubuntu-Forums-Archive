---
title: "Wiring a 5 port workgroup switch for sharing."
date: 2012-05-02
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-05-02
My situation is 2 desktops back to back on a table, a Comcast modem, a Wifi router, and a Brother MFC-440 printer (Lan/USB).

I have 11.10 running great off a 16 GB USB flash and the Brother USB connected to its PC.

(It is very easy to dual boot XP/11.10 from the USB flash and I see no reason to install Ubuntu on the hard drive)

Ubuntu can see the other PC's files, and vice versa, but the XP machine cannot see or print on MShome.  

I have a 5 port workgroup switch.

I have zero experience using a switch.

My thinking is that if I connect to the 5-Port Workgroup Switch properly, I will always have internet connectivity and printer access even if there is only one PC running. 

Before I switch LAN wires, please consider my plan:

Connect the Comcast modem to the WIFI router.

Connect the first PC to the WIFI router.

Connect the WIFI router to the  5-Port Workgroup Switch

Connect the 2nd PC to the  5-Port Workgroup Switch

Connect the MFC-440 printer (LAN) to the 5-Port Workgroup Switch

If this works, all components will be hard wired and easily shared.

BTW I bought a Dell Optiflex 330 tower with the Intel E2180 2 GHz dual processor and 2 GB or memory for $85. It is a screamer and it runs much faster than the P4 2.8 Ghz PC that it replaces.

---

### Post by kimda on 2012-05-02
I would connect the WIFI router(firewall) to your modem via the wan port on the router and connect the WIFI router (lan port - probably one of the four available ports), pc's and printer to the switch. Thats how I have it configured here. You can usually configure the wifi router via a internal ipadress (ex. 192.168.1.1) in the browser and the modem will have to be in bridging mode. Also make sure that the workgroup is the same on Linux and Windows (ex. HOMEGROUP or make up a better name for your workgroup_.

---

