---
title: "Scanimage / scan a document on a Print Office over Ethernet"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by honeybear on 2011-10-03
Hello,

My printer is located at 192.167.2.115. I would like to use it for scanning. This printer when you use the usb, you can fairly run scanimaage to scan. 

But over Ethernet and the IP number? 

the command ```
scanimage -L  192.167.2.115 
```detects  nothing

THank you for any help !

---

### Post by cjazz on 2011-10-03
I don't know if I'll be able to help, but knowing the printer make and model would be really helpful. Plus, you're saying the scanner works through USB? I assume you're able to print with it connected via ethernet?

---

### Post by honeybear on 2011-10-03
> **cjazz said:**
> I don't know if I'll be able to help, but knowing the printer make and model would be really helpful. Plus, you're saying the scanner works through USB? I assume you're able to print with it connected via ethernet?

Please find below the model of the printer:
HP Officejet 4500 All-in-One Printer

# nmap -sS -PN gives:
> 

Interesting ports on XXXX:
Not shown: 989 closed ports
PORT     STATE SERVICE
80/tcp   open  http
6839/tcp open  unknown
7435/tcp open  unknown
8080/tcp open  http-proxy
9100/tcp open  jetdirect
9101/tcp open  jetdirect
9102/tcp open  jetdirect
9110/tcp open  unknown
9220/tcp open  unknown
9290/tcp open  unknown
9500/tcp open  unknown
MAC Address: XXXX (Unknown)

XX
Not shown: 997 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
111/tcp   open  rpcbind
55055/tcp open  unknown
MAC Address: XXXXX (Unknown)

Nmap done: 30 IP addresses (25 hosts up) scanned in 22.95 seconds


The HP is 
device an hpaio: Officejet_4500_G510g-m?serial=XXXX' is a Hewlett-Packard Officejet_4500_G510g-m all-in-one

---

### Post by cjazz on 2011-10-05
Have you checked the contents of the file /etc/sane.d/dll.conf to make sure the line "hpaio" is uncommented?

---

### Post by honeybear on 2011-10-05
> **cjazz said:**
> Have you checked the contents of the file /etc/sane.d/dll.conf to make sure the line "hpaio" is uncommented?


I have no idea about much scanimage into /etc/sane.d

your knowledge would greatly help

Please find the content
```
# /etc/sane.d/dll.conf - Configuration file for the SANE dynamic backend loader
#
# Backends can also be enabled by configuration snippets under
# /etc/sane.d/dll.d directory -- packages providing backends should drop
# a config file similar to dll.conf in this directory, named after the package.
#

# The next line enables the network backend; comment it out if you don't need
# to use a remote SANE scanner over the network - see sane-net(5) and saned(8)
net
abaton
agfafocus
apple
avision
artec
artec_eplus48u
as6e
bh
canon
canon630u
canon_dr
#canon_pp
```

---

### Post by cjazz on 2011-10-05
Well, to recognize the scanner the line "hpaio" (wiuthout the quotes, of course) should be found uncommented in the dll.conf file. Normally that's taken care of when you install hplip so I'm a little confused.

Again, I have to ask: Are you able to print currently from your networked Officejet 4500?

Also, I'd be interested if the drivers are currently installed. Would you please type in a terminal the following line

```
sudo apt-get hplip libsane-hpaio
```

and report back with the output?

---

### Post by honeybear on 2011-10-06
> **cjazz said:**
> Well, to recognize the scanner the line "hpaio" (wiuthout the quotes, of course) should be found uncommented in the dll.conf file. Normally that's taken care of when you install hplip so I'm a little confused.

Again, I have to ask: Are you able to print currently from your networked Officejet 4500?

[COLOR="SeaGreen"]- yes yes. it worked over cups. For the moment I have no use of that, since I would like first to make scanimage work over ethernet/intranet.[/COLOR]

Also, I'd be interested if the drivers are currently installed. Would you please type in a terminal the following line

```
sudo apt-get hplip libsane-hpaio
```

and report back with the output?



here we go ! 
```
b#  apt-get install hplip libsane-hpaio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
hplip is already the newest version.
libsane-hpaio is already the newest version.
libsane-hpaio set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 22 not upgraded.
```

```
# ls  /etc/sane.d/
abaton.conf          canon_dr.conf   dell1600n_net.conf  geniusvp2.conf  ibm.conf         mustek_pp.conf   qcam.conf      sp15c.conf     umax1220u.conf
agfafocus.conf       canon_pp.conf   dll.conf            gphoto2.conf    kodak.conf       mustek_usb.conf  ricoh.conf     st400.conf     umax.conf
apple.conf           cardscan.conf   dll.d               gt68xx.conf     leo.conf         nec.conf         rts8891.conf   stv680.conf    umax_pp.conf
artec.conf           coolscan2.conf  dmc.conf            hp3900.conf     lexmark.conf     net.conf         s9036.conf     tamarack.conf  v4l.conf
artec_eplus48u.conf  coolscan3.conf  epjitsu.conf        hp4200.conf     ma1509.conf      p5.conf          saned.conf     teco1.conf     xerox_mfp.conf
avision.conf         coolscan.conf   epson2.conf         hp5400.conf     matsushita.conf  pie.conf         sceptre.conf   teco2.conf
bh.conf              dc210.conf      epson.conf          hp.conf         microtek2.conf   pixma.conf       sharp.conf     teco3.conf
canon630u.conf       dc240.conf      fujitsu.conf        hpsj5s.conf     microtek.conf    plustek.conf     sm3840.conf    test.conf
canon.conf           dc25.conf       genesys.conf        hs2p.conf       mustek.conf      plustek_pp.conf  snapscan.conf  u12.conf

```

snapscan.conf into /etc/sane.d tells us:
```

#------------------------------ General -----------------------------------

# Change to the fully qualified filename of your firmware file, if
# firmware upload is needed by the scanner
firmware /usr/share/sane/snapscan/your-firmwarefile.bin

# If not automatically found you may manually specify a device name.

# For USB scanners also specify bus=usb, e.g.
# /dev/usb/scanner0 bus=usb

# For SCSI scanners specify the generic device, e.g. /dev/sg0 on Linux.
# /dev/sg0

#---------------------------------------------------------------------------
# No changes should be necessary below this line
#---------------------------------------------------------------------------

#-------------------------- SCSI scanners ----------------------------------
# These SCSI devices will be probed automatically
scsi AGFA * Scanner
scsi COLOR * Scanner
scsi Color * Scanner
scsi ACERPERI * Scanner

#--------------------------- USB scanners -----------------------------------
# These USB devices will be probed automatically
# (This will currently work only on Linux)

# Benq/Acer/Vuego 310U
usb 0x04a5 0x1a20
usb 0x04a5 0x1a26

# Benq/Acer/Vuego 320U
usb 0x04a5 0x2022

# Benq/Acer/Vuego 620U / 620UT
usb 0x04a5 0x1a2a
usb 0x04a5 0x2040

# Benq/Acer/Vuego 640U
usb 0x04a5 0x2060

# Benq/Acer/Vuego 640BU
usb 0x04a5 0x207e

# Benq/Acer/Vuego 640BT
usb 0x04a5 0x20be

# Benq/Acer/Vuego 1240U
usb 0x04a5 0x20c0

# Benq/Acer/Vuego 3300 / 4300
usb 0x04a5 0x20b0

# Benq/Acer/Vuego 4300
usb 0x04a5 0x20de

# Benq 5000E / 5000U
usb 0x04a5 0x20f8

# Benq 5000
usb 0x04a5 0x20fc

# Benq/Acer 5300
usb 0x04a5 0x20fe

# Benq 5250C
usb 0x04a5 0x2137

# Agfa 1236U
usb 0x06bd 0x0002

# Agfa 1212U
usb 0x06bd 0x0001
usb 0x06bd 0x2061

# Agfa Snapscan e10
usb 0x06bd 0x2093

# Agfa Snapscan e20
usb 0x06bd 0x2091

# Agfa Snapscan e25
usb 0x06bd 0x2095

# Agfa Snapscan e26
usb 0x06bd 0x2097

# Agfa Snapscan e40
usb 0x06bd 0x208d

# Agfa Snapscan e42
usb 0x06bd 0x20ff

# Agfa Snapscan e50
usb 0x06bd 0x208f

# Agfa Snapscan e52
usb 0x06bd 0x20fd

# Epson Perfection 660
usb 0x04b8 0x0114

# Epson Perfection 1670
usb 0x04b8 0x011f

# Epson Perfection 2480
usb 0x04b8 0x0121

# Epson Perfection 3490
usb 0x04b8 0x0122

# Epson Stylus CX-1500
usb 0x04b8 0x080c


```

---

### Post by cjazz on 2011-10-07
I could guess at the next step, but your next best move (if you haven't tried it already) might be to visit [this troubleshooting page]("http://hplipopensource.com/node/333") and take your cues from there. Please report back if this doesn't help.

---

