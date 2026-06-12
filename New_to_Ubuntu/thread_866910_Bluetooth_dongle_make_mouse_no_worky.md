---
title: "Bluetooth dongle make mouse no worky"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by mancroft on 2008-07-22
I have been using an a4 tech nb30 Battery Free Wireless Optical Mouse successfully. [http://www.a4tech.com/en/media/thecrucible.htm](http://www.a4tech.com/en/media/thecrucible.htm)

Today, I got a new Bluetooth dongle, plugged it in and the mouse stopped working instantly.

Any ideas as to the cure?

Thanks.

---

### Post by northern lights on 2008-07-22
With both devices connected, can you run ```
lsusb
``` and post the output?

---

### Post by mancroft on 2008-07-22
Thanks, northern lights. Here is the output:

> 
john@john-desktop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 1131:1004 Integrated System Solution Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
john@john-desktop:~$ 


---

### Post by northern lights on 2008-07-22
Don't thank me too early, this seems rather weird.

I'd assume the "Integrated System Solution Corp." entry is the dongle.

If you do nothing but remove said dongle and run "lsusb" again, the mouse shows up?!

If so, that's wicked. Lemme ponder, I'll get back to you.

---

### Post by mancroft on 2008-07-22
Dongle removed. Mouse still connected. 

john@john-desktop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
john@john-desktop:~$ 

Strange thing is, the little lights on the mouse pad work OK and indicate the thing is alive but the cursor does not move.

---

### Post by mancroft on 2008-07-23
Here is the kern.log from the time of the incident: 

> Jul 22 10:37:53 john-desktop kernel: [12335.808336] usb 2-3: new full speed USB device using ohci_hcd and address 2
Jul 22 10:37:53 john-desktop kernel: [12336.035992] usb 2-3: configuration #1 chosen from 1 choice
Jul 22 10:37:53 john-desktop kernel: [12336.203742] Bluetooth: HCI USB driver ver 2.9
Jul 22 10:37:54 john-desktop kernel: [12336.410199] usb 1-3: reset low speed USB device using ohci_hcd and address 4
Jul 22 10:37:54 john-desktop kernel: [12336.737560] usb 1-3: device descriptor read/64, error -62
Jul 22 10:37:54 john-desktop kernel: [12337.168737] usb 1-3: device descriptor read/64, error -62
Jul 22 10:37:55 john-desktop kernel: [12337.595926] usb 1-3: reset low speed USB device using ohci_hcd and address 4
Jul 22 10:37:55 john-desktop kernel: [12337.923301] usb 1-3: device descriptor read/64, error -62
Jul 22 10:37:55 john-desktop kernel: [12338.354553] usb 1-3: device descriptor read/64, error -62
Jul 22 10:37:56 john-desktop kernel: [12338.781664] usb 1-3: reset low speed USB device using ohci_hcd and address 4
Jul 22 10:37:56 john-desktop kernel: [12339.192863] usb 1-3: device not accepting address 4, error -62
Jul 22 10:37:57 john-desktop kernel: [12339.500288] usb 1-3: reset low speed USB device using ohci_hcd and address 4
Jul 22 10:37:57 john-desktop kernel: [12339.911495] usb 1-3: device not accepting address 4, error -62
Jul 22 10:37:57 john-desktop kernel: [12339.911556] usb 1-3: USB disconnect, address 4
Jul 22 10:37:57 john-desktop kernel: [12340.115123] usb 1-3: new low speed USB device using ohci_hcd and address 5
Jul 22 10:37:57 john-desktop kernel: [12340.294769] usb 1-3: device descriptor read/64, error -62
Jul 22 10:37:58 john-desktop kernel: [12340.578234] usb 1-3: device descriptor read/64, error -62
Jul 22 10:37:58 john-desktop kernel: [12340.857738] usb 1-3: new low speed USB device using ohci_hcd and address 6
Jul 22 10:37:58 john-desktop kernel: [12341.037358] usb 1-3: device descriptor read/64, error -62
Jul 22 10:37:58 john-desktop kernel: [12341.320811] usb 1-3: device descriptor read/64, error -62
Jul 22 10:37:59 john-desktop kernel: [12341.600289] usb 1-3: new low speed USB device using ohci_hcd and address 7
Jul 22 10:37:59 john-desktop kernel: [12342.011432] usb 1-3: device not accepting address 7, error -62
Jul 22 10:37:59 john-desktop kernel: [12342.184170] usb 1-3: new low speed USB device using ohci_hcd and address 8
Jul 22 10:38:00 john-desktop kernel: [12342.590381] usb 1-3: device not accepting address 8, error -62
Jul 22 10:38:00 john-desktop kernel: [12342.592382] usbcore: registered new interface driver hci_usb
Jul 22 10:38:01 john-desktop kernel: [12343.554355] Inbound IN=eth0 OUT= MAC=00:30:05:8c:fe:3e:00:16:9c:26:34:01:08:00 SRC=60.222.224.133 DST=82.22.109.26 LEN=485 TOS=0x00 PREC=0x00 TTL=45 ID=0 DF PROTO=UDP SPT=59986 DPT=1026 LEN=465 
Jul 22 10:38:05 john-desktop kernel: [12347.635449] Inbound IN=eth0 OUT= MAC=00:30:05:8c:fe:3e:00:16:9c:26:34:01:08:00 SRC=125.65.165.139 DST=82.22.109.26 LEN=40 TOS=0x00 PREC=0x00 TTL=111 ID=256 DF PROTO=TCP SPT=12200 DPT=8000 WINDOW=8192 RES=0x00 SYN URGP=0 
Jul 22 10:38:47 john-desktop kernel: [12389.984727] Inbound IN=eth0 OUT= MAC=00:30:05:8c:fe:3e:00:16:9c:26:34:01:08:00 SRC=24.64.128.32 DST=82.22.109.26 LEN=512 TOS=0x00 PREC=0x00 TTL=68 ID=24042 PROTO=UDP SPT=33401 DPT=1027 LEN=492 
Jul 22 10:38:47 john-desktop kernel: [12389.984897] Inbound IN=eth0 OUT= MAC=00:30:05:8c:fe:3e:00:16:9c:26:34:01:08:00 SRC=24.64.128.32 DST=82.22.109.26 LEN=512 TOS=0x00 PREC=0x00 TTL=68 ID=24043 PROTO=UDP SPT=33401 DPT=1028 LEN=492 
Jul 22 10:38:47 john-desktop kernel: [12389.985020] Inbound IN=eth0 OUT= MAC=00:30:05:8c:fe:3e:00:16:9c:26:34:01:08:00 SRC=24.64.128.32 DST=82.22.109.26 LEN=512 TOS=0x00 PREC=0x00 TTL=68 ID=24041 PROTO=UDP SPT=33401 DPT=1026 LEN=492 
Jul 22 10:39:22 john-desktop kernel: [12424.526464] Inbound IN=eth0 OUT= MAC=00:30:05:8c:fe:3e:00:16:9c:26:34:01:08:00 SRC=125.65.165.139 DST=82.22.109.26 LEN=40 TOS=0x00 PREC=0x00 TTL=111 ID=256 DF PROTO=TCP SPT=12200 DPT=3128 WINDOW=8192 RES=0x00 SYN URGP=0 
Jul 22 10:40:39 john-desktop kernel: [12501.571901] Inbound IN=eth0 OUT= MAC=00:30:05:8c:fe:3e:00:16:9c:26:34:01:08:00 SRC=125.65.165.139 DST=82.22.109.26 LEN=40 TOS=0x00 PREC=0x00 TTL=111 ID=256 DF PROTO=TCP SPT=12200 DPT=8080 WINDOW=8192 RES=0x00 SYN URGP=0 

---

### Post by mancroft on 2008-08-01
Bump.

---

### Post by northern lights on 2008-08-01
mkey.

I think this is a USB 2.0 related bug. I remember reading of problems with simultaneous loading of 'ehci_hcd' and 'ohci_hcd'.

Run```
sudo modprobe -r ehci_hcd
```and the mouse should work. You will unfortunately lose all USB2 capability.

---

### Post by mancroft on 2008-08-01
Thanks, northern lights. If I do run that line of code you say "You will unfortunately lose all USB2 capability.".

How do I get the  USB2 capability back?

---

### Post by mancroft on 2008-08-01
Duplicate.

---

### Post by northern lights on 2008-08-01
> **mancroft said:**
> How do I get the  USB2 capability back?
Run it without the '-r', i.e.```
sudo modprobe ehci_hcd
```

Here's a breakdown of the command:

'sudo' - most likely you know, executes the command with root rights
'modprobe' - loads modules to the kernel, calls 'insmod'
'-r' - makes modprobe unload and call 'rmmod'
'ehci_hcd' - Extended Host Controller Interface, USB 2.0 driver module

---

### Post by mancroft on 2008-08-01
Brilliant, northern lights! Got it working. Much obliged.

---

### Post by northern lights on 2008-08-01
sweet. if that did indeed do the trick, this is how you'd make it permanent:

```
sudo echo "blacklist ehci_hcd" > /etc/modprobe.d/blacklist-ehci
```

So far you'd have to run unload the module manually every session...

---

### Post by mancroft on 2008-08-01
Excellent. I'll do that.

---

