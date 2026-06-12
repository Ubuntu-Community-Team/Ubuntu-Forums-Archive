---
title: "Printing problem from a WindowsXP"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by Damned666 on 2008-08-25
Hi, 

i have ubuntu 8.04 installed and the printing was working well my ubuntu box(the printer is connected on this machine) as well as from another XP machine until recently. Now no XP machines can print anything but the linux one still works correctly. I don't know how to check this out.

In the CUPS web interface every time a job is send from the XP machine it's logged as completed without even being printed.

---

### Post by Gregmond on 2008-08-25
OK, so if I understand this, all PC's print via the UBUNTU box but recently that stopped.

Is the Ubuntu PC using DHCP ? did this change IP's ? How do the XP PC's connect ? via name or IP address ? It sounds like your IP address has changed or something.
To find out the IP address on the Ubuntu Pc go to a terminal and type: ifconfig

Other than that the services may have stopped, check the printer sharing on the Ubuntu PC.

Have you changed the firewall/IP tables settings on the Ubuntu PC ? (Firestarter etc)

---

### Post by Damned666 on 2008-08-26
Yeah you understand right, every PC print via the Ubuntu Box. i haven't installed any firewall on this machine (Unless an update did something to the iptables). 

Printer service is up in System - Administation - Services. Is there anything else to check ?

The ipaddress is always the same (assigne by the router to be static based on the mac address)

Thanks a lot,
Daniel

---

### Post by Gregmond on 2008-08-28
> **Damned666 said:**
> Yeah you understand right, every PC print via the Ubuntu Box. i haven't installed any firewall on this machine (Unless an update did something to the iptables). 

Not sure what to offer as advice here. Maybe someone else can suggest something ?

> **Damned666 said:**
> 
Printer service is up in System - Administation - Services. Is there anything else to check ?

Not an expert on printing with Linux so I don't know.

> **Damned666 said:**
> 
The ipaddress is always the same (assigne by the router to be static based on the mac address)

Don't assume that is the case. Check it. I do understand reserved IP's etc, doesn't mean it always works the way it is supposed to.

Nothing changed on the router ? No firmware updates ? Did the router reboot and remove any unsaved rules that allowed the printing to work ?

If you delete the printer on one of the PC's and create a new one, does it setup correctly ? If it does I would think it then sees the server correctly and it must be an issue with the print service/printer but I can't swear to it.

---

### Post by Damned666 on 2008-08-28
> Don't assume that is the case. Check it. I do understand reserved IP's etc, doesn't mean it always works the way it is supposed to.

Nothing changed on the router ? No firmware updates ? Did the router reboot and remove any unsaved rules that allowed the printing to work ?

If you delete the printer on one of the PC's and create a new one, does it setup correctly ? If it does I would think it then sees the server correctly and it must be an issue with the print service/printer but I can't swear to it.

The ip is correct. No change on the router for at least 6 months. I tried deleting the printer and creating it again and it works but still not able to print on it. Any idea anyone ?

---

### Post by Damned666 on 2008-08-30
Any idea anyone ... nobody has any answer for me. I really don't know what to search for ...

---

### Post by Damned666 on 2008-09-02
so nobody has any solution for me ??

---

### Post by crispy_420 on 2008-09-02
samba running?

Not sure if anyone asked yet.

---

### Post by Damned666 on 2008-09-07
i think samba is running, how can i be sure ?

---

### Post by alienexplorers on 2008-09-07
To check to see if Samba is running go to System -> Administration -> System Monitor.  Look under processes to see if it's listed.

---

### Post by Damned666 on 2008-09-08
Samba does not seems to be running. Nothing listed under system monitor. Isn't the printer shared by using something new (not samba) in the latest version ... i think i read that somewhere ??

What do i do next ?

---

