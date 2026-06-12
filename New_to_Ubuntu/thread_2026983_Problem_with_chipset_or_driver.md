---
title: "Problem with chipset or driver"
date: 2012-07-16
forum: New to Ubuntu
---

### Post by kavi123 on 2012-07-16
why the Atheros chipset 5413 does not work in ubuntu 11.04?

---

### Post by NikTh on 2012-07-16
**Hello and Welcome to Ubuntu Forums !**

Please open a terminal (ctrl+alt+t) , copy-paste these commands one at time 
```
uname -r 
sudo lshw -C network 
lspci -nnk | grep -iA2 net
dmesg | grep -i -e wlan -e net
```post the results back here . 
**Put the results inside [CODE] tags , by highlighting the text an click at (#) symbol on top of message pane.**
Thanks

---

### Post by kavi123 on 2012-07-16
Hi,
       I have been trying with the Atheros Chipset AR5413, once in a  while the adapter would be recognized by the driver, the supported and  the loaded driver was ath5k  i guess, 

The problems I'm facing are

[LIST]
[*]the adapter wont be recognised and giving [COLOR=Blue]network UNCLAIMED[/COLOR] whenever i do "[COLOR=Blue]lshw -C network[/COLOR]" or it would be identified as and when and "[COLOR=Blue]lshw -C network[/COLOR]" command wont be displaying anything after[COLOR=Blue] network[/COLOR]..
[*]the driver ath5k is not being loaded automatically, as soon as i insert the adapter inside the slot.
[*]thats fine, i can use modprobe ath5k inorder to load the module manually, then also it fails to identify the adapter many times.
[*]If at all it recognizes, it get associates with the access point,  the association or the connection would be alive only for few seconds.
[*]After few seconds dissociation happens automatically, could not find  the reason, and not even the beacon frames were destined to this  Atheros wireless adapter.
[*]I have built in intel chipset for which even after disconnecting the  wireless interface from the access point, many of the broadcast beacon  frames would be observed on the wireshark, why not for this adapter  PCMCIA adapter..
[*]I'm having the doubt like, the driver or the hardware is not stable  enough to  handle the connection , the association process or the  connection between the wireless station and Access point can not be  alive even for few second, why dissociation happens.
[/LIST]
Looking forward to the reply. Please post  all your answer asap.

---

### Post by Bucky Ball on 2012-07-16
Try Madwifi ([http://madwifi-project.org/](http://madwifi-project.org/)) instead of Network Manager. Specifically for Atheros so might get some joy there. Could you post the result of your command, 'sudo lshw -C network' here and also: 

```
iwconfig
```Also, have you actually been online (with cable and with the wireless dongle/card in the machine) and gotten updates then checked 'Additional Drivers'? Cheers.

---

### Post by kavi123 on 2012-07-16
i did not get your point , "Try Madwifi instead of Network Manager", Could you please elaborate a little..

---

### Post by Elfy on 2012-07-16
Thread closed. Please do not post duplicates, it dilutes community effort.

Duplicate here - [http://ubuntuforums.org/showthread.php?t=2026944](http://ubuntuforums.org/showthread.php?t=2026944)

---

### Post by Elfy on 2012-07-16
merged

---

