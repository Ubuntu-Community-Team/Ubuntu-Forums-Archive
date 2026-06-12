---
title: "[HOW-TO] Sagem V-55 &amp; irda"
date: 2007-02-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Sir_Yaro on 2007-02-18
connect device

```
[yaro][~]$ lsusb
Bus 004 Device 002: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 005: ID 066f:4200 SigmaTel, Inc. STIr4200 IrDA Bridge
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
[yaro][~]$              
```

```
[yaro][~]$ dmesg |tail -n 5
[17210339.960000] usb 3-2: new full speed USB device using uhci_hcd and address 5
[17210340.080000] usb 3-2: device descriptor read/64, error -71
[17210340.344000] usb 3-2: configuration #1 chosen from 1 choice
[17210340.352000] SigmaTel STIr4200 IRDA/USB found at address 5, Vendor: 66f, Product: 4200
[17210340.352000] drivers/net/irda/stir4200.c: IrDA: Registered SigmaTel device irda0
[yaro][~]$     
```

```

[yaro][~]$ lsmod|grep 4200
stir4200               14212  0
irda                  200892  3 irda_usb,stir4200,via_ircc
usbcore               130304  9 irda_usb,stir4200,wacom,rt73,usb_storage,libusual,ehci_hcd,uhci_hcd
[yaro][~]$   
```

If u haven't irda_usb and stir4200 modules loaded, do it now:

```
[yaro][~]$ sudo modprobe irda_usb stir4200
[yaro][~]$                                
```

Install software:
```
[yaro][~]$ sudo apt-get install irda-utils libopenobex1 openobex-apps obexftp 
```

```
[yaro][~]$ cd /tmp
[yaro][~]$ wget http://download.gro.clinux.org/ircp-tray/ircp-tray_0.6.1-1_i386.deb
[yaro][~]$ sudo dpkg -i ircp-tray_0.6.1-1_i386.deb
```
or
```
[yaro][~]$ cd /tmp
[yaro][~]$ wget http://yaro.gdi.pl/deb/edgy/ircp-tray_0.7.0-1_i386.deb
[yaro][~]$ sudo dpkg -i ircp-tray_0.7.0-1_i386.deb
```

turn it on and check:
```
[yaro][~]$ sudo irattach irda0 -s
[yaro][~]$  ifconfig irda0
irda0     Link encap:IrLAP  HWaddr 63:b3:bd:ef
          UP RUNNING NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8
          RX bytes:0 (0.0 b)  TX bytes:749 (749.0 b)

[yaro][~]$ cat /proc/net/irda/discovery
IrLMP: Discovery log:

nickname: SAGEM, hint: 0x9025, saddr: 0x63b3bdef, daddr: 0x428201a6


[yaro][~]$ sudo irdadump
18:25:19.759335 xid:cmd 63b3bdef > ffffffff S=6 s=0 (14)
18:25:19.859282 xid:cmd 63b3bdef > ffffffff S=6 s=1 (14)
18:25:19.959289 xid:cmd 63b3bdef > ffffffff S=6 s=2 (14)
18:25:20.059299 xid:cmd 63b3bdef > ffffffff S=6 s=3 (14)
18:25:20.132218 xid:rsp 63b3bdef < 428201a6 S=6 s=3 SAGEM hint=9025 [ Modem Telephony IrCOMM IrOBEX ] (22)
18:25:20.159317 xid:cmd 63b3bdef > ffffffff S=6 s=4 (14)
18:25:20.259308 xid:cmd 63b3bdef > ffffffff S=6 s=5 (14)
18:25:20.359318 xid:cmd 63b3bdef > ffffffff S=6 s=* siryaro hint=0400 [ Computer ] (23)
18:25:22.759472 xid:cmd 63b3bdef > ffffffff S=6 s=0 (14)
18:25:22.859469 xid:cmd 63b3bdef > ffffffff S=6 s=1 (14)
18:25:22.959477 xid:cmd 63b3bdef > ffffffff S=6 s=2 (14)
18:25:23.032746 xid:rsp 63b3bdef < 428201a6 S=6 s=2 SAGEM hint=9025 [ Modem Telephony IrCOMM IrOBEX ] (22)
18:25:23.059491 xid:cmd 63b3bdef > ffffffff S=6 s=3 (14)
18:25:23.159501 xid:cmd 63b3bdef > ffffffff S=6 s=4 (14)
18:25:23.259504 xid:cmd 63b3bdef > ffffffff S=6 s=5 (14)
18:25:23.359505 xid:cmd 63b3bdef > ffffffff S=6 s=* siryaro hint=0400 [ Computer ] (23)

16 packets received by filter
[yaro][~]$   
```
stop it by CTRL+C. Like u see my SAGEM answers:
```
18:25:20.132218 xid:rsp 63b3bdef < 428201a6 S=6 s=3 SAGEM hint=9025 [ Modem Telephony IrCOMM IrOBEX ] (22)
```

send file:
```
[yaro][~]$ irobex_palm3 /tmp/youtube.jpg
Send and receive files to Palm3

name=/tmp/youtube.jpg, size=673
.

PUT successful
[yaro][~]$    
```

receive file from phone:
```
[yaro][~]$ irobex_palm3
Send and receive files to Palm3
Waiting for files

Unknown event!
............HEADER_LENGTH = 5261
put_done() Skipped header 42
Filename = Ania IE.JPG
Wrote Ania IE.JPG (5261 bytes)


[yaro][~]$   
```

unfortunatelly i have no clue how to do something more - send a midlet, backup phone book or browse the phone. When I find an answer for that I'll update this thread.

Connection is very easy to lose :(. In my case any move of the phone was enough to disconnect. 
I had to disconnect and connect device again and run irattach once more.

---

### Post by avdzm on 2008-02-28
Hey, 
thanks for the tutorial,
I do have a problem with sudo modprobe irda_usb stir4200
i get this error
```

FATAL: Error inserting irda_usb (/lib/modules/2.6.22-14-generic/kernel/drivers/net/irda/irda-usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

I'm running Ubuntu 7.10
any ideas?
thanks

---

### Post by duncan.hawthorne on 2008-03-01
thanks for the guide, really really useful
as per usual, i look for ages for a way to do something, find nothing, think it's impossible, then find the perfect guide hiding away somewhere, and its as simple as a couple of commands.

to avdzm, 
although im unlikely to be able to help, the output of the command says see dmesg, so you should at least paste the output of that (straight after you have run the first command) if you want help.
im on 7.10 and didnt have to do the modprobe line. perhaps you've screwed something up some other way...
show us the output of the other commands too.

---

### Post by Darh on 2008-06-26
thx tutorial. work my sagem my400V

---

