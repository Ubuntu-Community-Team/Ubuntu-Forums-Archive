---
title: "how do I find out where the problem is?"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by acoluthus on 2008-11-06
Hi-
I cannot get on-line via attempted new external dialup modem through serial port or existing RJ-45 connection from coaxial cable internet router (home-user).I have a few postings out there running but am still waiting for additional input from the volunteers after I followed their initial recommendations.

----but:
-how do I know/ how do I determine -where- the problem _is_?
is there a way to tell whether the cable got fried just after installing Heron, coincidentally?
-how do I know the preferred settings(or if i screwed them up trying to set up either the RJ45 connection and the external serial modem)?
-how do I determine if I fried some 'card' inside or not?
-Should I just keep re-loading Heron?
all I can really do now is raise scores on the few games I managed to download, or catch up on re-watching Babylon5 on dvd.

-suggestions?  

with appreciation,
`A.C.

---

### Post by LowSky on 2008-11-06
ok lets get down to your problem with your cable modem

can you tell us your service provider, and brand of the modem.
Also does your Cable company ned any kind of login password or use a static IP?

Also could you give the specs of the computer in question

opena terminal and use this command and paste the result here thanks 
```
lspci
```

also withthe ethernet cable  connected to the modem from the PC we will need this command to be run as well

```
ifconfig
```

---

### Post by acoluthus on 2008-11-08
Thank you for your reply!sorry for my delay:
Here's the following:
user@user-desktop:~$ lspci

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 0e)

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)

00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)

01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)

02:09.0 Mass storage controller: Silicon Image, Inc. PCI0680 Ultra ATA-133 Host Controller (rev 02)

02:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

user@user-desktop:~$ 


user@user-desktop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:30:1b:bb:6b:57  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:16 



eth0:avahi Link encap:Ethernet  HWaddr 00:30:1b:bb:6b:57  

          inet addr:169.254.5.247  Bcast:169.254.255.255  Mask:255.255.0.0

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          Interrupt:16 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:762 errors:0 dropped:0 overruns:0 frame:0

          TX packets:762 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:39664 (38.7 KB)  TX bytes:39664 (38.7 KB)
user@user-desktop:~$ 
-------------------------------
I have truly no idea what 90% of it means, and 99% of how the above info relates to anything else, so any and all info would be greatly appreciated.
Sincerely,
A.C.
---------------------------
ISP: RCN Cable/coaxial internet; 
Modem:
Router: Linksys
*wired connecton windows XP & wireless laptop running vista are able to connect from same router; tried different jack-connections didn't change my inability to connect. ok: details:
----------
Modem: (RCN/ISP's modem)
Scientific Atlanta 2100 MAC# 001CEAC9E0DA (i noticed some people talk about mac addresses; just in case it's helpful)*my internet access was down before ISP came & exchanged cable-phone modem for just cable modem(sci-atl)no change in accessibility
----------
Router: our own:
Netgear WGR614  v4
mac: 0095BFA0436
default address: http//192.168.0.1
--------*I bought a Linksys,---GL model, said by mfgr to be linux friendly; can't install the darn thing on any house computer; even the PC wizard didn't cooperate.
`hope these details help; I'll check back for your recommendations
Thank You!
A.C.

---

### Post by acoluthus on 2008-11-10
081110
Ok, further attempts to get dialup working. Our house has cable modem to router to RJ-45 cord into my CPU, but I'm killing the cable once I can get dialup working. 
I took a few people's advise and reloaded Heron. I did it unpartitioned as I'm not running a dual system and if I'm over-writing &#8220;everything&#8221; then I overwrote everything completely. Then I couldn't access the us.archive for any updates,(it was just as the new-newest edition was being released)and was limitedly on-line, but now I cannot get on-line at all, my PC will not connect. So, i'm carrying a 2gig camera chip of my Terminal experiences back & forth to a roommate's computer to try to get stuff to work. If I should/or am able to carry any sub-programs on this cam'chip, please instruct me how to do so; I've not been able to do so successfully thus far. Here goes:

Attempt :-  when I go to Network Settings and try to uncheck the Wired Connection and select the Modem, and have already loaded Preferences/etc., it &#8220;thinks&#8221; about it (little spinning circle) and un-selects Modem and re-selects the wired connection. It also goes from Serial Modem to PPPoE and un-checks the modem/dial up option. -What's up w/ that?
Elsewise: I've gone through the WIKI's and several-many instruction pages on this webpage and some other people's walk-through's and am not getting the results that others are getting.

The following pretty much confirms that I no longer have scanModem after reloading Heron, unpartitioned, over everything, since this is a Ubuntu-only ShuttleXpc.__
USER@USER-desktop:~$ sudo scanModem

sudo: scanModem: command not found

USER@USER-desktop:~$ scanModem

bash: scanModem: command not found

USER@USER-desktop:~$ gunzip scanModem.gz

gzip: scanModem.gz: No such file or directory

USER@USER-desktop:~$ chmod +x scanModem

chmod: cannot access `scanModem': No such file or directory

USER@USER-desktop:~$ ./scanModem

bash: ./scanModem: No such file or directory

USER@USER-desktop:~$ gedit Modem/ModemData.txt

___this, above, opened a blank page.___
Tried the next:
USER@USER-desktop:~$ wvdial

--> WvDial: Internet dialer version 1.60

--> Cannot open /dev/modem: No such file or directory

--> Cannot open /dev/modem: No such file or directory

--> Cannot open /dev/modem: No such file or directory

___which I assume means that wvdial exists but something else is missing__
USER@USER-desktop:~$ pppconfig


You must be root to run this program.

USER@USER-desktop:~$ 

USER@USER-desktop:~$ sudo wvdial

--> WvDial: Internet dialer version 1.60

--> Cannot open /dev/modem: No such file or directory

--> Cannot open /dev/modem: No such file or directory

--> Cannot open /dev/modem: No such file or directory

USER@USER-desktop:~$ sudo pppconfig

USER@USER-desktop:~$ sudo adduser USER dip

The user `USER' is already a member of `dip'.

USER@USER-desktop:~$ sudo adduser USER dialout

The user `USER' is already a member of `dialout'.

USER@USER-desktop:~$ 

USER@USER-desktop:~$ sudo ppconfig

sudo: ppconfig: command not found

USER@USER-desktop:~$ sudo pppconfig

USER@USER-desktop:~$ sudo pppconfig

USER@USER-desktop:~$ pon

USER@USER-desktop:~$ sudo pon

__nothing happened
 _____tried recommended Troubleshooting terminal commands, when I ran the dmesg, the whole thing is too big for the terminal to show all: here are ifconfig, iwconfig &  tail /var/log/messages, if  that info helps..
USER@USER-desktop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:30:1b:bb:6b:57  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:16 


eth0:avahi Link encap:Ethernet  HWaddr 00:30:1b:bb:6b:57  

          inet addr:169.254.5.247  Bcast:169.254.255.255  Mask:255.255.0.0

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          Interrupt:16 


lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:978 errors:0 dropped:0 overruns:0 frame:0

          TX packets:978 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:60862 (59.4 KB)  TX bytes:60862 (59.4 KB)


USER@USER-desktop:~$ iwconfig

lo        no wireless extensions.


eth0      no wireless extensions.


USER@USER-desktop:~$ tail /var/log/messages

Nov 10 09:20:21 USER-desktop kernel: [    8.634660] sky2 eth0: enabling interface

Nov 10 09:20:21 USER-desktop kernel: [    8.637270] ADDRCONF(NETDEV_UP): eth0: link is not ready

Nov 10 09:32:20 USER-desktop syslogd 1.5.0#1ubuntu1: restart.

Nov 10 09:47:23 USER-desktop -- MARK --

Nov 10 09:49:20 USER-desktop kernel: [ 1747.128082] PPP generic driver version 2.4.2

Nov 10 09:49:20 USER-desktop pppd[17105]: pppd 2.4.4 started by USER, uid 1000

Nov 10 09:49:22 USER-desktop pppd[17105]: Exit.

Nov 10 09:49:25 USER-desktop pppd[17113]: pppd 2.4.4 started by root, uid 0

Nov 10 09:49:27 USER-desktop pppd[17113]: Exit.

Nov 10 10:07:23 USER-desktop -- MARK --

USER@USER-desktop:~$

---

### Post by GeorgeVita on 2008-11-10
Hi, concerning your dialup external modem with serial (RS232?) interface:

After boot, connect it to the port (com1 or com2), and from a terminal window execute: **sudo wvdialconf** (give your password when prompted).

This is the 'auto configurator' for wvdial (dialler program). It will search for your modem and will fix  **/etc/wvdial.conf** (configuration file of wvdial).

Then execute the terminal command **cat /etc/wvdial.conf** (which "shows" the contents of the configuration file) and post the output here to follow up.

Regards,
George

---

### Post by acoluthus on 2008-11-12
I ran the recommended Terminal commands, and have run between 2 floors about 5times trying to convey the results on a camera chip;-the file info comes across corrupted from the cam-chip, I will try to post results again; it looks promising/ still need additional help, but for now, one more creaking staircase attempt and I'll wake up my household.. I WILL post as SOON as I can.. Thanks; please check back! 
A.C.

---

### Post by Crafty Kisses on 2008-11-12
Paste this command in the terminal and post the results here:
```
lshw -C network
```

---

### Post by acoluthus on 2008-11-12
081111-UbuntuHelpsTransfer steps FOR: GeorgeVita 
USER@USER-desktop:~$ sudo wvdialconf
[sudo] password for USER: 
Editing `/etc/wvdial.conf'.
Scanning your serial ports for a modem.
ttyS0<*1>: ATQ0 V1 E1 -- OK
ttyS0<*1>: ATQ0 V1 E1 Z -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS0<*1>: Modem Identifier: ATI -- Agere OCM V.92 Ver2.7a (Jun 14 2004) Voice Mercury DP2SH mode-ii SERIAL
ttyS0<*1>: Speed 4800: AT -- OK
ttyS0<*1>: Speed 9600: AT -- OK
ttyS0<*1>: Speed 19200: AT -- OK
ttyS0<*1>: Speed 38400: AT -- OK
ttyS0<*1>: Speed 57600: AT -- OK
ttyS0<*1>: Speed 115200: AT -- OK
ttyS0<*1>: Max speed is 115200; that should be safe.
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
Modem Port Scan<*1>: S2   S3   
Found a modem on /dev/ttyS0.
Modem configuration written to /etc/wvdial.conf.
ttyS0<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
USER@USER-desktop:~$ cat/etc/wvdial.conf        (without space)
bash: cat/etc/wvdial.conf: No such file or directory
USER@USER-desktop:~$ cat etc/wvdial.conf           (with space?)
cat: etc/wvdial.conf: No such file or directory
USER@USER-desktop:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
USER@USER-desktop:~$ cat/etc/wvdial.conf
bash: cat/etc/wvdial.conf: No such file or directory
USER@USER-desktop:~$ /etc/wvdial.conf
bash: /etc/wvdial.conf: Permission denied
USER@USER-desktop:~$ cat/etc/wvdial.conf
bash: cat/etc/wvdial.conf: No such file or directory
USER@USER-desktop:~$ /etc/wvdial.conf cat
bash: /etc/wvdial.conf: Permission denied
USER@USER-desktop:~$ 
**tried the &#8220;cat&#8221; command with &#8220;sudo&#8221; ahead of it and a space! (I try to take no chances in Terminal but am either getting &#8220;brave&#8221; or blindly ignorant & desperate- :)   
now, it &#8220;looks&#8221; &#8220;better&#8221;, but I already loaded phone/password/login in another Terminal program, plus in the Network Settings/GUI fields.
-Next step to loading Phone/Password/Login into WVDial in Terminal?
-also: (while you're here) how do I get the Network Settings to not &#8220;bounce back&#8221; and un-select the Wired connection option over the RJ-45/cable connection? 
Thank You for all thus far, and I'll look forward to 'next steps', as you're able!
A.C.

---

### Post by acoluthus on 2008-11-12
ATTN: CODENAME: as noted: here are the results.. 

USER@USER-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 19
       serial: 00:30:1b:bb:6b:57
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
USER@USER-desktop:~$ sudo lshw -C network
[sudo] password for USER: 
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 19
       serial: 00:30:1b:bb:6b:57
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
-------------------------------------
Thank you for your interest and support; `truly appreciated; I should be back on tomorrow pm..Again, Thank you both for your support..
A.C.

---

### Post by GeorgeVita on 2008-11-13
Hi again,
note that terminal commands are case sensitive and must have their 'spaces'. Also when talking about a file it is better to mention the full path name ex.: /etc/wvdial.conf than wvdial.conf

We have already found your modem on /dev/ttyS0 and wvdialconf made a first /etc/wvdial.conf which must be edited for the right telephone number, username and password. From a Terminal window execute the following command:

**sudo gedit /etc/wvdial.conf**
(give your password when prompted and press ENTER)

Placing **sudo** in front of the command **gedit** (text editor) makes you a "super-user" and you can edit some "protected" system files as **/etc/wvdial.conf**
 
Edit existing lines or replace them with:

Phone = 12345
Username = user
Password = pass

Replace 12345 with the phone number to be dialed, user with your username, pass with your password.

After editing SAVE the file.

Try connecting as a "super-user" with: **sudo wvdial**

We possibly need to trim or add some additional parameters so we need the output of any error message and the full /etc/wvdial.conf (type it in your screen with **cat /etc/wvdial.conf**).

**Note:** to disconnect when connected with wvdial you press CTRL-C at the terminal window which you made the connection. As references you can read the data given via the "man wvdial" and "man wvdial.conf" commands (from a terminal window).

Regards,
George

---

### Post by acoluthus on 2008-11-14
081113 configuration assist:GeorgeVita

wvdial.conf: sub-window:
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyS0
ISDN = 0
; Phone = <local number without area code>
; Password = <______entered________>
; Username = <____entered_____>

USER@USER-desktop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.

USER@USER-desktop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.

USER@USER-desktop:~$ sudo gedit /etc/wvdial.conf
  __________________((re-entered data in other open terminal field))
USER@USER-desktop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.

USER@USER-desktop:~$ cat /etc/wvdial.conf
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyS0
ISDN = 0
; Phone = <xxx-xxxx>
; Password = <PASSWORD for4USER>
; Username = <USER>

USER@USER-desktop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.

modem didn't even acknowledge/ go through light-cycle or sounds.
Tried with and without the local area code; no difference. I -did- gedit/etc/wvdial.conf and loaded and saved a few times.. and the message still says &#8220;does not specify&#8221;... 
I'll look forward to your direction, thank you for continuting with me on this, truly..
A.C.

---

### Post by GeorgeVita on 2008-11-14
Hi, you have to remove semicolons as these make the line a remark and not a parameter:

Make it like below:
[B]
Phone = <local number without area code>
Password = <______entered________>
Username = <____entered_____>
[/B]

> 
Edit existing lines or replace them with:

Phone = 12345
Username = user
Password = pass

Replace 12345 with the phone number to be dialed, user with your username, pass with your password.

After editing SAVE the file.


---

### Post by acoluthus on 2008-11-14
<**D-OUH**!!>  (homer simpson terminal command)lol.. will try, and will _reply. _[COLOR="DarkOrchid"]**THANK YOU!!**[/COLOR]

---

### Post by acoluthus on 2008-11-15
___*Tried another phone number from the ISP, took out spaces, etc. etc... still authentication error mssg I had saved a screenshot of my logon/password and a list of phone numbers from my dialup ISP; it's correct..I've called them and they didn't tell me that my password is followed by &#8220;@ISP&#8221;..(lovely people..) so I've retried that.. it's dialing... gives me a couple of DNS ADDRESSES!!
__**GOT IN! Logged into UbuntuForums!!  THANK YOU!!
__well, then it logged me out again.. Here's the Terminal conversation that I was trying to edit/upload; ___it killed after a few minutes or so..
___Further suggestions? 
--> Timed out while dialing.  Trying again.

--> Sending: ATDT3211289

--> Waiting for carrier.

ATDT3211289

CONNECT 52000 V44

--> Carrier detected.  Waiting for prompt.

GlobalPOPS

Username:/login:/Login:

--> Looks like a login prompt.

--> Sending: [email]USERNAME@copper.net[/email]

[email]USERNAME@copper.net[/email]

Password: 

--> Looks like a password prompt.

--> Sending: (password)

    Entering PPP Session.

    IP address is 208.100.195.96

    MTU is 1524.

--> Looks like a welcome message.

--> Starting pppd at Sat Nov 15 09:38:15 2008

--> Pid of pppd: 14566

--> Using interface ppp0

--> pppd: &#65533;[7f]

--> pppd: &#65533;[7f]

--> pppd: &#65533;[7f]

--> local  IP address 208.100.195.96

--> pppd: &#65533;[7f]

--> remote IP address 63.138.12.254

--> pppd: &#65533;[7f]

--> primary   DNS address 67.211.172.29

--> pppd: &#65533;[7f]

--> secondary DNS address 67.211.172.30

--> pppd: &#65533;[7f]

Caught signal 2:  Attempting to exit gracefully...

--> Terminating on signal 15

--> pppd: &#65533;[7f]

--> Connect time 5.8 minutes.

--> pppd: &#65533;[7f]

--> pppd: &#65533;[7f]

--> Disconnecting at Sat Nov 15 09:44:07 2008

redialed.. posted this message..

---

### Post by acoluthus on 2008-11-16
ok so i tried again with no changes and it "held" for quite a while, now I'm on again and I'm going to try and see if I can go through the night and download the Heron update packages from us.archive, if it's not swamped still. So far so good; and for the record, it's running faster and unbroken internet connections than RCN cable internet. at least "unbroken" is satisfactory. and more than 3 attempts does not a track record make, but just the feeling of Progress with this is enough for the moment.
Thank you and I'll keep this updated if any snafu's/fubar's/etc. should happen.
...

---

### Post by acoluthus on 2008-11-17
Hello GeorgeVita & all-
YES!! `have connectivity; left it on all night last night; disconnected after over 4 hours of downloading the 145 Heron updates; `took another 7 hours to do by dialup today and am in the process of updating with KPPP to hopefully also take care of the dialup assistance.  Is there any suggestion/recommendation of KPPP over WVdial? With wvdial i found it tough to get a prompt to close it when neccessary. honestly, playing on Terminal still makes me a tad uneasy. but I THANK YOU for all your assistance on this.. after so many weeks of attempts, plus months of frustration this is truly significant to me to be on-line again and start getting somewhere... at least I can get online to look up more tweaky things that i need to know/manage/correct from here on out. 
THANK YOU!! with so much appreciation!!
A.C.

---

### Post by GeorgeVita on 2008-11-17
> **acoluthus said:**
> ... With wvdial i found it tough to get a prompt to close it when neccessary.

To disconnect you have to press **ctrl-c** on the terminal window which you run the wvdial program.
You can see a small documantation for every terminal command or program by executing: **man abcd** (where abcd is the command). Examples:
**man wvdial**
**man ls**
**man find**

Keep trying, continue learning!

Regards
George

---

