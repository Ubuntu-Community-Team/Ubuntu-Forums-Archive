---
title: "Continuous NIC-Internet access outage. Ubuntu 15.04"
date: 2016-02-20
forum: New to Ubuntu
---

### Post by jeffery3 on 2016-02-20
Today I decided to abandon windows 10 and migrate to Ubuntu. I have been  tackling issue after issue all day to get this box exactly how I want  it.

Upon completion of installation, I've had this very aggravating annoyance.

Symptom:
I am connected to the Internet, browsing just fine and suddenly, "Pages cannot be displayed". 

Steps Taken:
1) I pull up the terminal and attempt to ping and URL. No success.

2) I ping my local gateway. This is successful.

3) Using the Network-manager icon at the top I click disconnect & then reconnected. (Internet access is now restored)

5 minutes later, symptom returns & I repeat steps 1 through 3.

With  windows installed, this issue does not occur which leaves me with doubt  that it is my gateway. Also, all other systems connected to the (WIRED)  network have no problems.

I have also tried changing the  physical switch port that I am plugged into. (Symptom persist) I have  tried using my secondary NIC on my computer. (Problem persist).

SYSTEM INFORMATION:
lspci of NIC's
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5708 Gigabit Ethernet (rev 12)
04:00.0 PCI bridge: Broadcom EPB PCI-Express to PCI-X Bridge (rev c3)
05:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5708 Gigabit Ethernet (rev 12)

Any help will be mush appreciated. 

P.S. As a result of this symptom, it took me 3 attempts to post this issue. :-(

---

### Post by HermanAB on 2016-02-20
I think that NetworkManager is confused by the second NIC.

Have you got both ports wired to the router?

Either unplug one ethernet cable, or disable the second NIC in the BIOS.

---

### Post by sammiev on 2016-02-20
15.04 reached (EOL) End of Life on Feb 04/16. Just saying

---

### Post by sandyd on 2016-02-20
Check the contents of /var/log/dmesg.
```

nano /var/log/dmesg
```

Are there any errors there?

---

