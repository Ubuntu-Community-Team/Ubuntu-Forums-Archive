---
title: "usb edge modem not detected in intrepid"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by Louis de Broglie on 2008-11-24
Just installed intrepid, then plugged in my mobidata usb edge modem. I checked in network manager and found nothing in mobile broadband section. Then I tried scanModem and wvdialconf too. None of them detected my modem. Any idea  ? :(

---

### Post by nhasian on 2008-11-24
can you post the output of:

```
lsusb
```

and

```
lshw -C network
```

---

### Post by Louis de Broglie on 2008-11-24
lsusb :

> 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 04fc:2140 Sunplus Technology Co., Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


lshw -C network :

> 
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 3c905B 100BaseTX [Cyclone]
       vendor: 3Com Corporation
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: eth0
       version: 30
       serial: 00:01:02:eb:0a:2f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x latency=64 maxlatency=10 mingnt=10 module=3c59x multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: aa:ca:81:98:e6:ba
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

And I am posting ls /dev too :

> 
adsp                ptyda  ptytf  ram12       tty62  ttyq0  ttyw1
agpgart             ptydb  ptyu0  ram13       tty63  ttyq1  ttyw2
audio               ptydc  ptyu1  ram14       tty7   ttyq2  ttyw3
block               ptydd  ptyu2  ram15       tty8   ttyq3  ttyw4
bus                 ptyde  ptyu3  ram2        tty9   ttyq4  ttyw5
cdrom               ptydf  ptyu4  ram3        ttya0  ttyq5  ttyw6
cdrom1              ptye0  ptyu5  ram4        ttya1  ttyq6  ttyw7
cdrw1               ptye1  ptyu6  ram5        ttya2  ttyq7  ttyw8
char                ptye2  ptyu7  ram6        ttya3  ttyq8  ttyw9
console             ptye3  ptyu8  ram7        ttya4  ttyq9  ttywa
core                ptye4  ptyu9  ram8        ttya5  ttyqa  ttywb
cpu_dma_latency     ptye5  ptyua  ram9        ttya6  ttyqb  ttywc
disk                ptye6  ptyub  random      ttya7  ttyqc  ttywd
dmmidi              ptye7  ptyuc  rtc         ttya8  ttyqd  ttywe
dri                 ptye8  ptyud  rtc0        ttya9  ttyqe  ttywf
dsp                 ptye9  ptyue  scd0        ttyaa  ttyqf  ttyx0
dvd                 ptyea  ptyuf  scd1        ttyab  ttyr0  ttyx1
fd                  ptyeb  ptyv0  sda         ttyac  ttyr1  ttyx2
full                ptyec  ptyv1  sda1        ttyad  ttyr2  ttyx3
fuse                ptyed  ptyv2  sda2        ttyae  ttyr3  ttyx4
hpet                ptyee  ptyv3  sda3        ttyaf  ttyr4  ttyx5
initctl             ptyef  ptyv4  sda4        ttyb0  ttyr5  ttyx6
input               ptyp0  ptyv5  sda5        ttyb1  ttyr6  ttyx7
kmem                ptyp1  ptyv6  sda6        ttyb2  ttyr7  ttyx8
kmsg                ptyp2  ptyv7  sda7        ttyb3  ttyr8  ttyx9
log                 ptyp3  ptyv8  sda8        ttyb4  ttyr9  ttyxa
loop0               ptyp4  ptyv9  sequencer   ttyb5  ttyra  ttyxb
lp0                 ptyp5  ptyva  sequencer2  ttyb6  ttyrb  ttyxc
MAKEDEV             ptyp6  ptyvb  sg0         ttyb7  ttyrc  ttyxd
mem                 ptyp7  ptyvc  sg1         ttyb8  ttyrd  ttyxe
midi                ptyp8  ptyvd  sg2         ttyb9  ttyre  ttyxf
mixer               ptyp9  ptyve  sg3         ttyba  ttyrf  ttyy0
net                 ptypa  ptyvf  shm         ttybb  ttys0  ttyy1
network_latency     ptypb  ptyw0  snapshot    ttybc  ttyS0  ttyy2
network_throughput  ptypc  ptyw1  snd         ttybd  ttys1  ttyy3
null                ptypd  ptyw2  sndstat     ttybe  ttyS1  ttyy4
oldmem              ptype  ptyw3  sr0         ttybf  ttys2  ttyy5
parport0            ptypf  ptyw4  sr1         ttyc0  ttyS2  ttyy6
port                ptyq0  ptyw5  stderr      ttyc1  ttys3  ttyy7
ppp                 ptyq1  ptyw6  stdin       ttyc2  ttyS3  ttyy8
psaux               ptyq2  ptyw7  stdout      ttyc3  ttys4  ttyy9
ptmx                ptyq3  ptyw8  tty         ttyc4  ttys5  ttyya
pts                 ptyq4  ptyw9  tty0        ttyc5  ttys6  ttyyb
ptya0               ptyq5  ptywa  tty1        ttyc6  ttys7  ttyyc
ptya1               ptyq6  ptywb  tty10       ttyc7  ttys8  ttyyd
ptya2               ptyq7  ptywc  tty11       ttyc8  ttys9  ttyye
ptya3               ptyq8  ptywd  tty12       ttyc9  ttysa  ttyyf
ptya4               ptyq9  ptywe  tty13       ttyca  ttysb  ttyz0
ptya5               ptyqa  ptywf  tty14       ttycb  ttysc  ttyz1
ptya6               ptyqb  ptyx0  tty15       ttycc  ttysd  ttyz2
ptya7               ptyqc  ptyx1  tty16       ttycd  ttyse  ttyz3
ptya8               ptyqd  ptyx2  tty17       ttyce  ttysf  ttyz4
ptya9               ptyqe  ptyx3  tty18       ttycf  ttyt0  ttyz5
ptyaa               ptyqf  ptyx4  tty19       ttyd0  ttyt1  ttyz6
ptyab               ptyr0  ptyx5  tty2        ttyd1  ttyt2  ttyz7
ptyac               ptyr1  ptyx6  tty20       ttyd2  ttyt3  ttyz8
ptyad               ptyr2  ptyx7  tty21       ttyd3  ttyt4  ttyz9
ptyae               ptyr3  ptyx8  tty22       ttyd4  ttyt5  ttyza
ptyaf               ptyr4  ptyx9  tty23       ttyd5  ttyt6  ttyzb
ptyb0               ptyr5  ptyxa  tty24       ttyd6  ttyt7  ttyzc
ptyb1               ptyr6  ptyxb  tty25       ttyd7  ttyt8  ttyzd
ptyb2               ptyr7  ptyxc  tty26       ttyd8  ttyt9  ttyze
ptyb3               ptyr8  ptyxd  tty27       ttyd9  ttyta  ttyzf
ptyb4               ptyr9  ptyxe  tty28       ttyda  ttytb  urandom
ptyb5               ptyra  ptyxf  tty29       ttydb  ttytc  usbdev1.1_ep00
ptyb6               ptyrb  ptyy0  tty3        ttydc  ttytd  usbdev1.1_ep81
ptyb7               ptyrc  ptyy1  tty30       ttydd  ttyte  usbdev2.1_ep00
ptyb8               ptyrd  ptyy2  tty31       ttyde  ttytf  usbdev2.1_ep81
ptyb9               ptyre  ptyy3  tty32       ttydf  ttyu0  usbdev3.1_ep00
ptyba               ptyrf  ptyy4  tty33       ttye0  ttyu1  usbdev3.1_ep81
ptybb               ptys0  ptyy5  tty34       ttye1  ttyu2  usbdev4.1_ep00
ptybc               ptys1  ptyy6  tty35       ttye2  ttyu3  usbdev4.1_ep81
ptybd               ptys2  ptyy7  tty36       ttye3  ttyu4  usbdev4.2_ep00
ptybe               ptys3  ptyy8  tty37       ttye4  ttyu5  usbdev4.2_ep03
ptybf               ptys4  ptyy9  tty38       ttye5  ttyu6  usbdev4.2_ep82
ptyc0               ptys5  ptyya  tty39       ttye6  ttyu7  usbdev5.1_ep00
ptyc1               ptys6  ptyyb  tty4        ttye7  ttyu8  usbdev5.1_ep81
ptyc2               ptys7  ptyyc  tty40       ttye8  ttyu9  vcs
ptyc3               ptys8  ptyyd  tty41       ttye9  ttyua  vcs1
ptyc4               ptys9  ptyye  tty42       ttyea  ttyub  vcs2
ptyc5               ptysa  ptyyf  tty43       ttyeb  ttyuc  vcs3
ptyc6               ptysb  ptyz0  tty44       ttyec  ttyud  vcs4
ptyc7               ptysc  ptyz1  tty45       ttyed  ttyue  vcs5
ptyc8               ptysd  ptyz2  tty46       ttyee  ttyuf  vcs6
ptyc9               ptyse  ptyz3  tty47       ttyef  ttyv0  vcs7
ptyca               ptysf  ptyz4  tty48       ttyp0  ttyv1  vcs8
ptycb               ptyt0  ptyz5  tty49       ttyp1  ttyv2  vcsa
ptycc               ptyt1  ptyz6  tty5        ttyp2  ttyv3  vcsa1
ptycd               ptyt2  ptyz7  tty50       ttyp3  ttyv4  vcsa2
ptyce               ptyt3  ptyz8  tty51       ttyp4  ttyv5  vcsa3
ptycf               ptyt4  ptyz9  tty52       ttyp5  ttyv6  vcsa4
ptyd0               ptyt5  ptyza  tty53       ttyp6  ttyv7  vcsa5
ptyd1               ptyt6  ptyzb  tty54       ttyp7  ttyv8  vcsa6
ptyd2               ptyt7  ptyzc  tty55       ttyp8  ttyv9  vcsa7
ptyd3               ptyt8  ptyzd  tty56       ttyp9  ttyva  vcsa8
ptyd4               ptyt9  ptyze  tty57       ttypa  ttyvb  watchdog
ptyd5               ptyta  ptyzf  tty58       ttypb  ttyvc  xconsole
ptyd6               ptytb  ram0   tty59       ttypc  ttyvd  zero
ptyd7               ptytc  ram1   tty6        ttypd  ttyve
ptyd8               ptytd  ram10  tty60       ttype  ttyvf
ptyd9               ptyte  ram11  tty61       ttypf  ttyw0

---

### Post by GeorgeVita on 2008-11-24
Hi, can you check the following?

Boot your computer without the modem.
Run the terminal command: **sudo modprobe usbserial vendor=0x04fc product=0x2140**
Plug in the modem, wait 10 seconds and run in terminal: **grep -e /dev/tty /var/log/messages**

Then post the above results (system activity on tty) to follow up.

Regards,
George

(P.S. **grep** command lists all lines containing **/dev/tty** into file **/var/log/messages** which is the system log)

---

### Post by Louis de Broglie on 2008-11-25
Sure, I checked. There were no output from the above command.

---

### Post by GeorgeVita on 2008-11-25
For the "sudo modprobe usbserial vendor=0x04fc product=0x2140" ok, there is no response.
What about **grep -e /dev/tty /var/log/messages**

---

### Post by Louis de Broglie on 2008-11-25
There are no output for that command too ](*,)

---

### Post by GeorgeVita on 2008-11-25
Be patient and try again:

Boot your computer without the modem.
Run the terminal command: **sudo modprobe usbserial vendor=0x04fc product=0x2140**
Write down the time (up right on the screen).
Plug in the modem.
Wait 10 seconds and run in terminal: **cat /var/log/messages**
Copy and post all lines with a time stamp same or after the above noted time.

Also post the description/model of the modem (or send a link with its commercial description).

](*,) I agree!

(I must go out for 1-2 hours)

---

### Post by Louis de Broglie on 2008-11-25
Ok, I am going to try it again :)

[Commercial Link]("http://www.mobidata.cn/en/products/veiw.asp?id=63")

---

### Post by Louis de Broglie on 2008-11-25
Please view the log file . The time I plug in the modem is 14:58 , the time I enter the modprobe command is 14:56 .

---

### Post by GeorgeVita on 2008-11-25
Sorry if I am repeating myself but are you sure that the listed device in the **lsusb** (Bus 004 Device 002: ID 04fc:2140 Sunplus Technology Co., Ltd) is the EDGE modem? Just to be sure you must boot without the modem, try lsusb, note the results, plug in the modem, wait 10-20 seconds and try again lsusb looking for new entries (you know the way but ... I am repeating myself!)

And a note for other readers that may help:
This USB EDGE modem is a **Shenzhen MobiData MBD-100EU** ([http://www.mobidata.com.cn](http://www.mobidata.com.cn))

Which when attached to the USB port it adds some of the following lines to /var/log/messages:

Nov 25 14:58:17 Nimbus2008 kernel: [  119.044936] type=1503 audit(1227603497.727:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5644/net/" pid=5644 profile="/usr/sbin/cupsd"

Nov 25 14:58:17 Nimbus2008 kernel: [  119.132445] NET: Registered protocol family 10

Nov 25 14:58:17 Nimbus2008 kernel: [  119.134385] lo: Disabled Privacy Extensions

Nov 25 14:58:17 Nimbus2008 kernel: [  119.136265] ADDRCONF(NETDEV_UP): eth0: link is not ready

Nov 25 14:58:17 Nimbus2008 kernel: [  119.137597] type=1503 audit(1227603497.819:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5644 profile="/usr/sbin/cupsd"

Nov 25 14:58:17 Nimbus2008 kernel: [  119.139880] type=1503 audit(1227603497.819:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5644 profile="/usr/sbin/cupsd"

Nov 25 14:58:17 Nimbus2008 kernel: [  119.142236] type=1503 audit(1227603497.823:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5644 profile="/usr/sbin/cupsd"

Nov 25 14:58:17 Nimbus2008 kernel: [  119.144512] type=1503 audit(1227603497.827:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5644 profile="/usr/sbin/cupsd"

Nov 25 14:58:17 Nimbus2008 kernel: [  119.146932] type=1503 audit(1227603497.827:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5644 profile="/usr/sbin/cupsd"

Nov 25 14:58:17 Nimbus2008 kernel: [  119.149278] type=1503 audit(1227603497.831:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5644 profile="/usr/sbin/cupsd"

Nov 25 14:58:17 Nimbus2008 kernel: [  119.151559] type=1503 audit(1227603497.831:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5644 profile="/usr/sbin/cupsd"

Nov 25 14:58:17 Nimbus2008 kernel: [  119.153831] type=1503 audit(1227603497.835:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5644 profile="/usr/sbin/cupsd"

Nov 25 14:58:17 Nimbus2008 kernel: [  119.153922] type=1503 audit(1227603497.835:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/5644/net/dev" pid=5644 profile="/usr/sbin/cupsd"

Nov 25 14:58:43 Nimbus2008 kernel: [  145.053196] usbcore: registered new interface driver usbserial

Nov 25 14:58:43 Nimbus2008 kernel: [  145.054526] usbserial: USB Serial support registered for generic

Nov 25 14:58:43 Nimbus2008 kernel: [  145.055857] usbcore: registered new interface driver usbserial_generic

Nov 25 14:58:43 Nimbus2008 kernel: [  145.055867] usbserial: USB Serial Driver core

Nov 25 14:59:13 Nimbus2008 kernel: [  174.704021] usb 4-2: new full speed USB device using uhci_hcd and address 2

Nov 25 14:59:13 Nimbus2008 kernel: [  174.944227] usb 4-2: configuration #1 chosen from 1 choice

Nov 25 14:59:13 Nimbus2008 kernel: [  174.947126] usbserial_generic 4-2:1.0: generic converter detected

Nov 25 14:59:13 Nimbus2008 kernel: [  174.947319] usb 4-2: generic converter now attached to ttyUSB0

Nov 25 14:59:13 Nimbus2008 kernel: [  175.007347] usbcore: registered new interface driver libusual

---

### Post by Louis de Broglie on 2008-11-25
If lsusb lists all devices attached to usb port, then the following information confirms the issue :)

lsusb before plugging in the modem :

> Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

After :

> Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 04fc:2140 Sunplus Technology Co., Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by GeorgeVita on 2008-11-26
As we have no other to help... try to do the following:

Boot your computer without the modem
Run the terminal command: **sudo modprobe usbserial vendor=0x04fc product=0x2140**
Plug in the modem
Wait 20 seconds and run: **lsusb**
You must see the **Sunplus Technology...** line
Then run: **ls /dev/ttyUSB***
You must see **/dev/ttyUSB0**
Run **wvdialconf** and post the output

I want to check if /dev/ttyUSB0 exists because was not in the full list of a previous post, and also the respond of /dev/ttyUSB0 to the wvdialconf program. Alternatively you could try Network Manager for connection to this port (as now exists).

---

### Post by Louis de Broglie on 2008-11-26
Yes, it exists now :D . But wvdialconf still does not find the modem even though it is checking ttyUSB0 . :confused:

> sudo wvdialconf /etc/wvdial.conf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- USBS [04]ï¿½
ttyUSB0<*1>: failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.



---

