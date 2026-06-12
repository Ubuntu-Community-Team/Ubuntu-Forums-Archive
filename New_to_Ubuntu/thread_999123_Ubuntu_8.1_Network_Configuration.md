---
title: "Ubuntu 8.1 Network Configuration"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by absolut1377 on 2008-12-01
I'm new to Ubuntu and only know a little in regards to CLI.  I am trying to setup my wireless info and have been unsuccessful in doing so via the CLI (WEP/WPA2) so I wanted to try via the Network Configuration GUI but it seems you can't "unlock" it from read only mode.  Am I missing something simple?

---

### Post by jgoguen on 2008-12-01
Are you getting there through System -> Administration -> Networking?  Try clicking the NetworkManager icon near the clock instead.  It probably looks like a small computer screen.  Do you see your network in the list that comes down?

Also, can you describe what you've already tried?

---

### Post by absolut1377 on 2008-12-01
In 8.1 that icon is not there (at least for me and yes this is a superuser acct)  The only thing next to the clock is the volume.  I was trying to get there from the system->administration drop downs but like i stated this is read only w/no option to unlock.

---

### Post by jgoguen on 2008-12-02
When you say superuser account, do you mean it's your own user (not root) that has full sudo access, or did you enable root?

Odd that it's not starting up automatically.  Can you provide details on what you tried on the CLI?  Only thing I can think of why that icon isn't there is that something you tried disabled NetworkManager.

---

### Post by absolut1377 on 2008-12-02
I've tried using the iwconfig commands to set ESSID and Key which don't seem to take.  I'm running a dell inspiron b130.  This all worked fine in 8.04.

---

### Post by jgoguen on 2008-12-02
Did you upgrade from 8.04 to 8.10, or reinstall?  What's the output of these commands?

```
iwconfig
```
```
ps aux | grep "nm-applet"
```
```
ps aux | grep NetworkManager
```

---

### Post by absolut1377 on 2008-12-02
eth0      Link encap:Ethernet  HWaddr 00:14:22:97:0e:45  
          inet addr:192.168.1.250  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fe97:e45/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:321 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66793 (66.7 KB)  TX bytes:4466 (4.4 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8683 (8.6 KB)  TX bytes:8683 (8.6 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.0.1  Bcast:172.16.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.51.1  Bcast:172.16.51.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:a4:63:cd:46  
          inet addr:192.168.1.251  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a4ff:fe63:cd46/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:157 errors:0 dropped:0 overruns:0 frame:0
          TX packets:257 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17741 (17.7 KB)  TX bytes:34242 (34.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A4-63-CD-46-64-34-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     IEEE 802.11bg  ESSID:"nethome"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:18:01:EF:41:A0   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=68/100  Signal level:-43 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

michael   6250  0.1  1.5  28280 11864 ?        S    09:39   0:00 nm-applet --sm-disable
michael   6684  0.0  0.1   3236   804 pts/0    S+   09:42   0:00 grep nm-applet
root      5720  0.0  0.3   6408  2332 ?        Ss   09:38   0:00 /usr/sbin/NetworkManager
root      5727  0.0  0.4   7696  3524 ?        S    09:38   0:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
michael   6696  0.0  0.1   3240   812 pts/0    S+   09:42   0:00 grep NetworkManager

---

### Post by jgoguen on 2008-12-02
It looks like your wireless is connected at least.  Could you try these commands and see if the icon comes back?

```

pkill nm-applet
sudo /etc/init.d/NetworkManager restart

```
Then press Alt+F2 and enter this:
```
nm-applet --sm-disable
```

---

### Post by hyper_ch on 2008-12-02
(1) when posting some output of a command or file use [noparse]```

```[/noparse] brackets around each individual part to make it more easily readable.

(2) I am unhappy with the ubuntu (or rather kubuntu) network manager and have been unhappy with them since I started using *buntu. I used to manually edit the network but now I use WICD as network manager. Maybe that's a solution for you also.

---

### Post by absolut1377 on 2008-12-02
Still nothing in the network manager.  Uploaded a screenshot.

---

### Post by jgoguen on 2008-12-02
That's the wired tab, and I would expect it to have only the one entry.  How did you get that with no NetworkManager icon?  Only way I know of to get that is to right-click the NetworkManager icon and choose Edit Connections, or Alt+F2 and enter nm-connections-editor.

I'd also like to make sure that your interface isn't defined in the interfaces file, which would prevent NetworkManager from handling it.  Please post the output of this command:
```
egrep 'auto|iface' /etc/network/interfaces
```You should only see these two lines in the output:
> auto lo
iface lo inet loopbackIf you see more than that, please edit /etc/network/interfaces and put a **#** at the start of every line except those two, save your changes, and then restart NetworkManager and nm-applet as I described in my last post and try again.

If you see only those two lines, go to the Wireless tab in the window you posted a screenshot of and see if your network is listed there.  If not, you can try this.  It won't work at all if you're not in the Wireless tab remember, and isn't necessary if your network is listed!

[LIST]
[*]Click the Add button
[*]In the window that appears, in the Connection Name box, enter any name you want.  This will identify your network and is purely for your convenience.
[*]In the SSID box, enter the name of your wireless network.  This will tell NetworkManager what network to connect to.
[*]Go to the Wireless Security tab, and choose the option from the Security drop-down that matches your network.  I'll assume you're using WPA or WPA2, in which case you only need to enter the network password.  If you choose WEP (either one of them) simply enter your key and you can most likely ignore the rest of the options.
[*]If you want Ubuntu to connect to the network before you log in, check the System Setting check box just underneath the Connection Name box.
[*]Click OK to save your settings.
[/LIST]

---

### Post by absolut1377 on 2008-12-02
I just took a shot of that window to show there was no "unlock" option.  I got to the window by going to System -> Pref -> Network Configuration.

When I go to the wireless configuration and try on the wireless security tab to enter my key for the WPA I can't save because its in "read only" mode.

auto lo
iface lo inet loopback
iface wlan0 inet static
iface eth0 inet static
auto wlan0
auto eth0

---

### Post by jgoguen on 2008-12-02
Please edit /etc/network/interfaces delete everything in it, and paste in these two lines:
```
auto lo
iface lo inet loopback
```Save your changes, and then restart NetworkManager and nm-applet as follows:
```
pkill nm-applet
sudo /etc/init.d/NetworkManager restart
```Then press Alt+F2, enter **nm-applet --sm-disable**

Then, hopefully the icon should appear.

That window doesn't have an Unlock button because it doesn't need one.  It changes personal settings, which doesn't require special privileges.

---

### Post by theozzlives on 2008-12-02
the network manager icon is the two computers by your clock

---

### Post by absolut1377 on 2008-12-02
> **theozzlives said:**
> the network manager icon is the two computers by your clock

This does not exist the same way in 8.1

---

### Post by jgoguen on 2008-12-02
Not the same way, or at all?  Did you upgrade from 8.04 or do a fresh install?  I'm just trying to get a handle on this.  Did my last post make any difference at all?

---

### Post by absolut1377 on 2008-12-02
> **jgoguen said:**
> Please edit /etc/network/interfaces delete everything in it, and paste in these two lines:
```
auto lo
iface lo inet loopback
```Save your changes, and then restart NetworkManager and nm-applet as follows:
```
pkill nm-applet
sudo /etc/init.d/NetworkManager restart
```Then press Alt+F2, enter **nm-applet --sm-disable**

Then, hopefully the icon should appear.

That window doesn't have an Unlock button because it doesn't need one.  It changes personal settings, which doesn't require special privileges.

Tried this, when I did the restart I got no messages like I have previously.

When I tried to run the cmd from alt+f2 I get an error saying it could not open up the location then saying /home/<username>/nm-applet --sm-disable No such file or directory.

---

### Post by jgoguen on 2008-12-02
That's not right, something else is wrong here.  Try this command in the Alt+F2 dialog:
```
/usr/bin/nm-applet --sm-disable
```

Also post the output of these commands, in separate [ code ] blocks for easier reading:

```
echo $PATH
```
```
ls -A ~/*nm-applet*
```

---

### Post by absolut1377 on 2008-12-02
> **jgoguen said:**
> That's not right, something else is wrong here.  Try this command in the Alt+F2 dialog:
```
/usr/bin/nm-applet --sm-disable
```

Also post the output of these commands, in separate [ code ] blocks for easier reading:

```
echo $PATH
```
```
ls -A ~/*nm-applet*
```

For the first one I got the same error

Echo
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

LS gave me this error
```

ls: cannot access /home/michael/*nm-applet*: No such file or directory

```

I installed WICD and got the network icon back in the tool bar and I am able to make changes.  I couldn't get a DHCP address on my wired connection but was able to for the wireless.  Very odd.  Doesn't seem to stick though and when I reboot I have to do it again.

---

### Post by jgoguen on 2008-12-02
Did you get exactly the same error, or slightly different?  That might be important.  Not sure why it's trying to look in your home directory at all though.  That's not at all how it's supposed to work.  Can you press Alt+F2 and enter **gedit**?  It should bring up the text editor.

As for the network side, I'm not at all familiar with WICD.  Sorry I couldn't get your problem solved :(

---

### Post by absolut1377 on 2008-12-03
gedit does come up when I do the ALT + F2.

---

### Post by drjimm on 2009-02-28
> **jgoguen said:**
> Did you get exactly the same error, or slightly different?  That might be important.  Not sure why it's trying to look in your home directory at all though.  That's not at all how it's supposed to work.  Can you press Alt+F2 and enter **gedit**?  It should bring up the text editor.

As for the network side, I'm not at all familiar with WICD.  Sorry I couldn't get your problem solved :(

I have followed ALL your directions, and you have gone beyond the call of duty with this, but I too still have no wireless connection with 8.1, which I've never liked, but when I load 8.04.2 all I get are patterns on the monitor.  Any ideas about that?  I'm running 8.04 on 2 machines, and the install disc works fine on my XP notebook and Vista desktop.  Not sure what's going on with this new Toshiba L305 notebook running Vista.
Your efforts and advice are sincerely appreciated.
Dr Jim Metcalf
Natchitoches, Louisiana

---

### Post by rajeeja on 2009-04-09
Hi I have a similar problem so i'm using the same thread. Wireless network worked well for me on a different network (my school) but at home it doesn't work.

I see the wireless network icon and also and entry of my network in "Wireless Networks"

When i try to connect it opens up Authentification window, i type in the key and it doesn't connect. 

I have a dual boot with vista, it connects fine on vista at home and school.

Please guide me how to fix this problem

Thanks

---

### Post by rajeeja on 2009-04-09
bump

i set WEP 40/128 
( but my  router is set to WEP - Manual and encryption key size # 1 40/64)

my key is a phone no...

index is 1 default

authentication is open system

this is what i have for windows vista too.

im using another pc now to post this.

Let me know if there is any other info required/?

---

### Post by rajeeja on 2009-04-09
bump 

i installed wisc but the wireless connection doesn't work :(

here are some outputs from cmds frm previous threads

lshw -C Network
lspci -nn | grep -i broadcom
ls /lib/firmware
sudo iwlist scan
dmesg | grep -e b43 -e wlan

FRM TERMINAL
--------------

rajeeev@rajeeev-laptop:~$ sudo iwconfig wlan0 mode managed channel 6 essid "JAIN"
[sudo] password for rajeeev: 
rajeeev@rajeeev-laptop:~$ sudo dhclient3 wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:3b:d3:7b:85
Sending on   LPF/wlan0/00:1f:3b:d3:7b:85
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
receive_packet failed on wlan0: Network is down
Terminated
rajeeev@rajeeev-laptop:~$ clear
rajeeev@rajeeev-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:d3:7b:85
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:61:d6:23
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 ip=192.168.0.84 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6a:f9:e6:eb:83:29
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
rajeeev@rajeeev-laptop:~$ lspci -nn | grep -i broadcom
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
rajeeev@rajeeev-laptop:~$ ls /lib/firmware
2.6.27-11-generic                   dvb-usb-umt-010-02.fw
2.6.27-7-generic                    dvb-usb-vp702x-01.fw
acx                                 dvb-usb-vp7045-01.fw
aic94xx-seq.fw                      dvb-usb-wt220u-02.fw
atmel_at76c502_3com.bin             dvb-usb-wt220u-fc03.fw
atmel_at76c502_3com-wpa.bin         dvb-usb-wt220u-zl0353-01.fw
atmel_at76c502.bin                  ipw2100-1.3.fw
atmel_at76c502d.bin                 ipw2100-1.3-i.fw
atmel_at76c502d-wpa.bin             ipw2100-1.3-p.fw
atmel_at76c502e.bin                 ipw2200-bss.fw
atmel_at76c502e-wpa.bin             ipw2200-ibss.fw
atmel_at76c502-wpa.bin              ipw2200-sniffer.fw
atmel_at76c503-i3861.bin            isl3877
atmel_at76c503-i3863.bin            isl3886
atmel_at76c503-rfmd-0.90.2-140.bin  isl3887usb_bare
atmel_at76c503-rfmd-acc.bin         isl3890
atmel_at76c503-rfmd.bin             isl3890usb
atmel_at76c504_2958-wpa.bin         iwlwifi-3945-1.ucode
atmel_at76c504a_2958-wpa.bin        iwlwifi-4965-1.ucode
atmel_at76c504.bin                  iwlwifi-4965-2.ucode
atmel_at76c504c-wpa.bin             iwlwifi-5000-1.ucode
atmel_at76c505a-rfmd2958.bin        ql2100_fw.bin
atmel_at76c505-rfmd2958.bin         ql2200_fw.bin
atmel_at76c505-rfmd.bin             ql2300_fw.bin
atmel_at76c506.bin                  ql2322_fw.bin
atmel_at76c506-wpa.bin              ql2400_fw.bin
b43                                 rt2561.bin
b43legacy                           rt2561s.bin
bcm2033-fw.bin                      rt2661.bin
bcm2033-md.bin                      rt73.bin
dvb-fe-or51132-qam.fw               v4l-cx23418-apu.fw
dvb-fe-or51132-vsb.fw               v4l-cx23418-cpu.fw
dvb-fe-or51211.fw                   v4l-cx23418-dig.fw
dvb-fe-tda10046.fw                  v4l-cx2341x-dec.fw
dvb-ttpci-01.fw                     v4l-cx2341x-enc.fw
dvb-usb-avertv-a800-02.fw           v4l-cx2341x-init.mpg
dvb-usb-bluebird-01.fw              v4l-cx25840.fw
dvb-usb-dib0700-1.10.fw             v4l-pvrusb2-24xxx-01.fw
dvb-usb-dibusb-5.0.0.11.fw          v4l-pvrusb2-29xxx-01.fw
dvb-usb-dibusb-6.0.0.8.fw           zd1201-ap.fw
dvb-usb-dtt200u-01.fw               zd1201.fw
dvb-usb-tvwalkert.fw                zd1211
rajeeev@rajeeev-laptop:~$ sudo iwlist scan
[sudo] password for rajeeev: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:00:00:00:00:00
                    ESSID:""
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/100  Signal level:-78 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000006a1cb0f292
                    Extra: Last beacon: 8ms ago
         .....

                    .....
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000002b89fd7995
                    Extra: Last beacon: 1728ms ago

pan0      Interface doesn't support scanning.

---

### Post by rajeeja on 2009-04-09
missed  the important cell:
----------------
  Cell 04 - Address: 00:22:10:B1:BE:F0
                    ESSID:"JAIN"
                    Mode:Master
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=83/100  Signal level:-51 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000002645d8701b6
                    Extra: Last beacon: 1552ms ago

---

### Post by rajeeja on 2009-04-09
Fixed Network Manager works like a charm now!

---

