---
title: "Network Manager can't enable wireless anymore"
date: 2012-04-20
forum: New to Ubuntu
---

### Post by sir.Evan on 2012-04-20
Yesterday I clickeed on **Enable Wireless** in the **Network Manager**. 
This caused the wireless to disappear as I wanted and the text in the **Network Manager** got dimmed.

My problem now is that I can't get the wireless to work again!! 
The **Network Manager** don't react on any sort of clicks.

Is there a way via the terminal that one can enable the wireless again?? 
Please help!

I am running Ubuntu 11.10 on a HP Compaq nc4200 laptop and have had no problems with the wireless before. 
The problem is not caused by the hardware switch which can switch the wireless off.

---

### Post by grahammechanical on 2012-04-20
Have you tried clicking Enable Networking? &#921;t should click to off and then click to on. This should happen with Enable Wireless but if there is not a tick mark against Enable Networking, then you cannot enable wireless.

Regards.

---

### Post by cortman on 2012-04-20
So it's not a hardware switch... is there a hotkey combination as well? Run

```
rfkill list all
```

to find out if it's soft blocked anywhere.

---

### Post by sir.Evan on 2012-04-21
The enable network is enabled and i can toggle it.
VPN connections and Edit connections is also working .
everything else is dimmed and seems not to react on any clicking.

---

### Post by sir.Evan on 2012-04-21
The rfkill gave this result:
evan@evan-HP-Compaq-nc4200-PY302AA-ACQ:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
evan@evan-HP-Compaq-nc4200-PY302AA-ACQ:~$

---

### Post by cortman on 2012-04-21
> **sir.Evan said:**
> 
1: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no 

It looks like it still is soft blocked. Double check to make sure there isn't a hotkey combination that needs to be toggled (FN + F3 on my acer, yours is probably similar). If you've toggled it and it makes no difference, run

```
sudo rfkill unblock all && list all
```

---

### Post by sir.Evan on 2012-04-21
**Thank you very much Cortman.**

I typed in your command line and got this response and my laptop straight away connected to my wireless network.

On the terminal it looks like it did not work but it did!! 
The unblock probably did the trick
 **Thanx a lot for your help**

evan@evan-HP-Compaq-nc4200-PY302AA-ACQ:~$ sudo rfkill unblock all && list all
[sudo] password for evan: 
No command 'list' found, did you mean:
 Command 'dist' from package 'nmh' (universe)
 Command 'lst' from package 'lustre-utils' (universe)
 Command 'slist' from package 'ncpfs' (universe)
 Command 'klist' from package 'heimdal-clients' (universe)
 Command 'klist' from package 'krb5-user' (universe)
 Command 'listg' from package 'nauty' (multiverse)
 Command 'hist' from package 'loki' (universe)
 Command 'flist' from package 'nmh' (universe)
 Command 'last' from package 'sysvinit-utils' (main)
 Command 'gist' from package 'yorick' (universe)
 Command 'bist' from package 'bist' (universe)
list: command not found
evan@evan-HP-Compaq-nc4200-PY302AA-ACQ:~$

---

### Post by cortman on 2012-04-21
The first rfkill command worked; the second one it didn't pick up on for some reason. I probably should have said 

```
&& rfkill list all
```

but no matter.
Glad it worked. Always glad to help a fellow Evan. :)

---

