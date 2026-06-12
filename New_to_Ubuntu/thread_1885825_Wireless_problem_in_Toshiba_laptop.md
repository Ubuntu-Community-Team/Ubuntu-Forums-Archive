---
title: "Wireless problem in Toshiba laptop"
date: 2011-11-23
forum: New to Ubuntu
---

### Post by Inodoro Pereyra on 2011-11-23
Ok, so I installed Lucid in my Toshiba C655D-S5300, and, oh surprise, the wireless is not working.
Now, I tried the "sudo lshw -c" instruction (that used to work beautifully on 9.10), but it won't work now.
To make it even worse, I only have this computer, so, every time I need to look up something online, I have to restart on W7. :(

Can anybody tell me which instruction I need to use to see which wireless card I have, or does anybody know which driver I need, and how should I install it?

Thanks in advance. :)

---

### Post by wolfen69 on 2011-11-23
Post the output of
```
lspci
```

---

### Post by Inodoro Pereyra on 2011-11-24
Thank you Wolfen. Here it is:

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1510 
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9802 
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] 
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42) 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40) 
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40) 
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) 
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0 
00:15.1 PCI bridge: ATI Technologies Inc Device 43a1 
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
00:18.0 Host bridge: Advanced Micro Devices [AMD] Device 1700 (rev 43) 
00:18.1 Host bridge: Advanced Micro Devices [AMD] Device 1701 
00:18.2 Host bridge: Advanced Micro Devices [AMD] Device 1702 
00:18.3 Host bridge: Advanced Micro Devices [AMD] Device 1703 
00:18.4 Host bridge: Advanced Micro Devices [AMD] Device 1704 
00:18.5 Host bridge: Advanced Micro Devices [AMD] Device 1718 
00:18.6 Host bridge: Advanced Micro Devices [AMD] Device 1716 
00:18.7 Host bridge: Advanced Micro Devices [AMD] Device 1719 
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01) 
06:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1) 
```

So I'm assuming the driver would be the Realtek 8176? I'm gonna start looking for it. :)

---

### Post by Inodoro Pereyra on 2011-11-24
Ok, I've been reading, and all I find are ways to install the driver using the ethernet connection. Unfortunately, that's not an option for me. 

Is there a tutorial on how to install the Realtek driver without a connection?

---

### Post by wolfen69 on 2011-11-24
I found [this]("http://ubuntuforums.org/showpost.php?p=10019180&postcount=6"). But you will still need build-essential.

---

### Post by Inodoro Pereyra on 2011-11-24
Will try it. Thanks again.

---

### Post by Inodoro Pereyra on 2011-11-24
It worked! Thanks again Wolfen, you da man...! :D

For those that may have the same problem(s), here's what I did:

I couldn't get build essential, because the CD I downloaded seems to be missing the files.
So I copied the Tar-gz package to my "Documents" folder, then extracted it, and moved the extracted files to /Home.
then, in the terminal, I typed 

```
sudo su
```

...and then

```
 ./compat/script/compat-install.sh
```

...and let it rip. Finally, I typed "reboot", and, upon restarting, everything was working perfectly. I don't know if it's the right way to do it (it probably isn't), but it worked like a charm! :D

---

