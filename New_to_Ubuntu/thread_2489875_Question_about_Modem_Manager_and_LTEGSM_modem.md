---
title: "Question about Modem Manager and LTE/GSM modem"
date: 2023-08-12
forum: New to Ubuntu
---

### Post by bhubunt on 2023-08-12
Hi, 
I own a Lenovo x230i and recently detected a reference to a Nokia GSM  modem being activated on this computer in the system logs.  If someone is familiar with this GSM modem, can you explain  what is going on in this log? 

 Thanks.

```


 Snippet from Lenovo 230i system log of August 5, 2023:

 ModemManager reporting a change in the modem state to initializing.\par
16:10:33 ModemManager:  [1638492633.7695] [devices/nokia] modem state changed (initializing -> registered)\par
\par
ModemManager reporting a change in the modem state to registered.\par
16:10:33 ModemManager:  [1638492633.7855] [devices/nokia] modem state changed (registered -> connecting)\par
\par
ModemManager reporting a change in the modem state to connecting.\par
16:10:33 ModemManager:  [1638492633.7893] [devices/nokia] modem state changed (connecting -> connected)\par
\par
ModemManager reporting a change in the modem state to connected.\par
16:10:33 ModemManager:  [devices/nokia] modem state changed (connected -> disconnecting)\par
\par
ModemManager reporting a change in the modem state to disconnecting.\par
16:10:33 ModemManager:  [1638492633.7909] [devices/nokia] modem state changed (disconnecting -> registered)\par
\par
ModemManager reporting a change in the modem state to registered.\par
16:10:33 ModemManager:  [1638492633.7969] [devices/nokia] modem state changed (registered -> disabling)\par
\par
ModemManager reporting a change in the modem state to disabling.\par
16:10:33 ModemManager:  [1638492633.8006] [devices/nokia] modem state changed (disabling -> disabled)\par
\par
ModemManager reporting a change in the modem state to disabled.\par
16:10:33 ModemManager:  [1638492633.8022] [devices/nokia] modem state changed (disabled -> enabling)\par
\par
ModemManager reporting a change in the modem state to enabling.\par
16:10:33 ModemManager:  [1638492633.8057] [devices/nokia] modem state changed (enabling -> enabled)\par
\par
ModemManager reporting a change in the modem state to enabled.\par
16:10:33 ModemManager:  [1638492633.8072] [devices/nokia] modem state changed (enabled -> registered)\par
\par
ModemManager reporting a change in the modem state to registered.\par
16:10:33 ModemManager:  [1638492633.8156] [devices/nokia] modem state changed (registered -> connecting)\par
\par
ModemManager reporting a change in the modem state to connecting.\par
16:10:33 ModemManager:  [1638492633.8196] [devices/nokia] modem state changed (connecting -> connected)\par
\par
ModemManager reporting a change in the modem state to connected.\par
16:10:33 ModemManager:  [devices/nokia] modem state changed (connected -> disconnecting)\par
\par
ModemManager reporting a change in the modem state to disconnecting.\par
16:10:33 ModemManager:  [1638492633.8212] [devices/nokia] modem state changed (disconnecting -> registered)\par
\par
ModemManager reporting a change in the modem state to registered.\par
16:10:33 ModemManager:  [1638492633.8272] [devices/nokia] modem state changed (registered -> disabling)\par
\par
ModemManager reporting a change in the modem state to disabling.\par
16:10:33 ModemManager:  [1638492633.8291] [devices/nokia] modem state changed (disabling -> disabled)\par
\par
ModemManager reporting a change in the modem state to disabled.\par
16:10:33 ModemManager:  [1638492633.8307] [devices/nokia] modem state changed (disabled -> enabling)\par
\par
ModemManager reporting a change in the modem state to enabling.\par
16:10:33 ModemManager:  [1638492633.8343] [devices/nokia] modem state changed (enabling -> enabled)\par
\par
ModemManager reporting a change in the modem state to enabled.\par
16:10:33 ModemManager:  [1638492633.8359] [devices/nokia] modem state changed (enabled -> registered)\par
\par 
```

---

### Post by MAFoElffen on 2023-08-12
ModemManager is there to be able to make a connection via WWAN.

Does your machine have a WWAN card? It sounds like you do not get your internet connection through WWAN, so I would be safe to say that you can safely disable ModemManager.service.

It is doing what it was designed to do, check for a WWAN connection. But if one is not conigured or setup, then it sees that and ends the check. It does cause a delay in the boot process. To skip that, do: 
```

sudo systemctl disable ModemManager.service
sudo systemctl mask ModemManager.service

```

EDIT: 
Note that I used the WWAN port on my Lenovo laptop to install a 2TB mSATA SSD storage card... "That" is an option open to you.

---

### Post by bhubunt on 2023-08-12
I believe the log says my Lenovo x230i has a Nokia modem. It's unclear to me why the Nokia modem was initiated and I have not seen it activated before in other logs of mine. The machine made an attempt to start an LTE connection.

---

### Post by MAFoElffen on 2023-08-12
The Lenovo X230i, at least for the US market, uses WWAN Card Sierra Wireless P/N #MC7750... Not sure for other countries, as that card only works in the US. 

He could confirm what he has by doing:
```

sudo lspci

```
But the make and model of the WWAN card would be a distraction, as he is not using a WWAN connection.

---

### Post by bhubunt on 2023-08-13
The log snippet I posted from the Lenovo x230i of August 5, 2023 refers to a Nokia modem, see post#1, but when I type in the command to list pci devices, I get 12 results, none of which refer to a Nokia modem. 11 results are from the Intel Corporation 7 series. 1 of them refers to a SATA controller, not mSATA.

```
 00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) 
```

So why is there a reference to a Nokia modem in the log, but no mention of it in the list of pci? 

In the manual for the Lenovo x230 it says that the computer either comes with a 1090 PCI Express Mini Card for wireless WAN or mSATA solid-state drive. "If the computer is equipped with an mSATA solid-state drive, it is installed in the wireless WAN card slot."

Any other terminal commands I can use to find out more about the Nokia modem and mSata?

---

### Post by MAFoElffen on 2023-08-13
I mentioned mSATA as an option, instead of WWAN. It uses the same mini PCI slot. I did not say you had, one. But rather that you could use that slot for one. For example, the Lenovo I am writing this from:
```

mafoelffen@Mikes-ThinkPad-T520:~$ lsblk -e7 -o name,label,size,fstype,fsused,fsuse%,model,mountpoint
NAME     LABEL       SIZE FSTYPE     FSUSED FSUSE% MODEL                   MOUNTPOINT
sda                  1.8T                          Samsung SSD 870 QVO 2TB 
&#9500;&#9472;sda1   {SYSTEM}    550M vfat        39.6M     7%                         /boot/efi
&#9500;&#9472;sda2               128M                                                  
&#9500;&#9472;sda3   {Windows}   900G ntfs                                             
&#9500;&#9472;sda4               983M                                                  
&#9500;&#9472;sda5                30G                                                  
&#9500;&#9472;sda6                32G                                                  
&#9474; &#9492;&#9472;swap swap         32G swap                                             [SWAP]
&#9500;&#9472;sda7   bpool         2G zfs_member                                       
&#9500;&#9472;sda8   rpool       500G zfs_member                                       
&#9492;&#9472;sda9   hpool     397.4G zfs_member                                       
sdb                  1.8T                          Samsung SSD 870 QVO 2TB 
&#9500;&#9472;sdb1   kpool      1000G zfs_member                                       
&#9492;&#9472;sdb2   dpool       863G zfs_member                                       
sdc                  1.8T                          Dogfish SSD 2TB         
&#9492;&#9472;sdc1   backups     1.5T zfs_member                                       

```
In that output, /dev/sdb is an mSATA drive. That is 6TB of internal storage.

If you have a WWAN modem, the ModemManager service would control it, and the mmcli utility, which stands for Modemmanager Command Line interface would be what you used to get information from it. For example
```

mmcli -v --modem 0

```
...would either return information on the WWAN card, or tell you that no modem was found. If you do have a WWAN modem, that would show that. If it doesn't, not sure where that is coming from.

---

### Post by bhubunt on 2023-08-13
Thanks for the helpful comments.
 Today, I inspected this Lenovo x230i, opened it up, and there is no Nokia WWAN modem installed. 
Nonetheless, the log I retrieved from this Lenovo x230i on Aug 5, 2023, referred to a Nokia modem, see post #1 
Also, in the meantime, the long system log of Aug 5, which I originally retrieved from that laptop and from which the above log snippet in post #1  stems, is no longer on the laptop. Instead, there's a log version that has been tampered with, from which numerous code lines were removed, including the code lines for the time slot 16:10:33, referring to the Nokia modem.  Most of the removed code lines concern the kernel, systemd, and gnome shell. The system log is full of sudden time leaps, indicative of tampering. Luckily, I saved a copy of the long original system log, before it was altered.

---

### Post by MAFoElffen on 2023-08-13
That is just "strange." I don't know what to say.

You can still disable ModemManager or leave it as is. It is something not used by you. As for discrepancies on your logs(?)

Check your computer for active connections. You can use the `netstat` command to view active connections and their status. Open a terminal and run the command 
```

sudo netstat -antp

```
Look at the list of active connections. Look for any connections that you don't recognize, especially on ports commonly used for remote access, such as VNC (port 5900) or SSH (port 22).

Check your log files: Ubuntu logs all remote access attempts in various log files. You can view these logs by running this command in a terminal session
```

sudo grep sshd /var/log/auth.log

```
This will display the list of all SSH connections to your computer. Similarly, you can run this command to see all VNC connections. 
```

sudo grep vnc /var/log/syslog` to see VNC connections.

Check your active processes: You can use the `ps` command to see a list of running processes on your Ubuntu computer. Run this command in a terminal to see all processes, and look for any processes that you don't recognize or that are related to remote access.
[code]
ps aux | less

```

Install monitoring software: You can install monitoring software, such as `iftop`, `nethogs`, or `tcpdump`, to monitor network traffic in real-time and detect any suspicious activity. Note that they will generate lots of output.

---

### Post by bhubunt on 2023-08-27
Hi,
Thanks for the feedback. However, as I have mentioned in other posts on this platform, my Lenovo x230i is an airgapped device. I had the wifi; bluetooth and wwan modules removed, which is why I was surprised to see a reference to a Nokia modem. There is no network traffic to check as the laptop is physically isolated from the network.  For a minute I thought there might be a Nokia WWAN modem on it, however improbable that seemed, but as mentioned in post #7, when I opened the laptop, this was not the case.

---

