---
title: "[SOLVED] Frequent boot failure"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by 2CV67 on 2008-05-19
A problem started a few months ago (I think just before I upgraded from Fiesty to Gutsy) and has been getting worse since.

At first, booting would usually be rapid and complete, but occasionally it would hang for a minute or so at "Configuring Network Interfaces" then proceed to normal login, but with no wi-fi available. Re-booting usually fixed it.

This got to be more frequent (50%) recently.

In the last few days it has also become more severe and sometimes after the hang at "Configuring Network Interfaces" it switches from the Ubuntu splash screen to a "Terminal type" screen, then progresses as far as "Starting NFS kernel daemon" before sticking totally.

From there I usually have to physically switch off to escape.

I have no idea where to start looking for the cause or a fix.

Any suggestions would be very welcome.

---

### Post by OffAxis on 2008-05-19
Try booting from the LiveCD a number of times; this'll have the effect of taking the hard drive (with it's installed operating system) out of the loop, so if it works without problems then it's probably a hard drive / software configuration issue.
If it still gives you problems then try running the Memtest program on the LiveCD to check the RAM.

Consistent hanging on the 'Configuring Network Devices' may also be indicative of problems with your wireless router. You could try turning it off (or plugging in) and boot a few times.

It could also be your power supply dying a slow death.

---

### Post by 2CV67 on 2008-05-20
Thanks for those suggestions.

I found my old Edgy 6.10 CD and booted 5 times from that.
All pretty slow (4min 6sec to 4min 16sec) but consistent and no obvious hang-up or failure.
I never did have wi-fi from that CD though, so not sure what that proves?

I ran memory test from that CD too.
I let it run 3 passes (does it go for ever or what?) with no errors found.

I tried booting Gutsy 7.10 with the router unplugged.
I got one clean boot, one failure that needed switching off and one that hung for a minute at "Configuring Network Interfaces" then proceeded to log-in.
Not sure that that is significantly different than with router.
In any case, I cannot get wi-fi connected if I bring the router on after booting.

I then went back to "normal" and recorded some bootcharts (I have hundreds...) of a good boot (gutsy-20080520-3.png) and a failure with hanging at "Configuring Network Interfaces" then sticking at "Starting NFS kernel daemon" which needed switching off (gutsy-20080520-2.png).
Do these provide any clues?
Can I run any other tests?

Thanks!

---

### Post by 2CV67 on 2008-05-21
Nobody?

---

### Post by OffAxis on 2008-05-26
```
I found my old Edgy 6.10 CD and booted 5 times from that.
All pretty slow (4min 6sec to 4min 16sec) but consistent and no obvious hang-up or failure.
I never did have wi-fi from that CD though, so not sure what that proves?
```
It'd be best to use the LiveCD from your current implementation so it's a more legitimate comparison. As you point out, the wi-fi driver isn't built-in, so it never fires up.
Coupled with your favorable memtest results (yes, it does run forever :) it would seem to not be a problem with the computer at large, but be a problem with either your wi-fi hardware or the software that runs it.
> In any case, I cannot get wi-fi connected if I bring the router on after booting.
Really? Where does it fail; on detecting available networks or on requesting an IP address from the DHCP server? Does it consistently do either?

Regardless, I think the prognosis is the same; download the Hardy  LiveCD and see how that works for you. If it works, you could perform a Distribution Upgrade from the upgrade manager, (backing up your data beforehand just to be safe). You'd probably want to do a clean install just to make sure the problem didn't carry over.
If the software 'solution' of the Hardy LiveCD doesn't work consistently, then it's probably a hardware problem with the wi-fi card or router; which means firmware upgrade or replacement.

> I then went back to "normal" and recorded some bootcharts (I have hundreds...) of a good boot (gutsy-20080520-3.png) and a failure with hanging at "Configuring Network Interfaces" then sticking at "Starting NFS kernel daemon" which needed switching off (gutsy-20080520-2.png).
Do these provide any clues?
My guess would be that you've run an 'apt-get upgrade' at some point that upgraded one of the networking packages and now when your wi-fi card errors out it's not trapping the error properly and is causing the NFS daemon to hang. Total speculation, but you may want to check the bug files on launchpad.

---

### Post by 2CV67 on 2008-05-28
Thanks for your continuing interest and help!
Much appreciated!

> **OffAxis said:**
> 
It'd be best to use the LiveCD from your current implementation 

I don't think I can go that way as I don't have a liveCD from Gutsy (upgraded Edgy>Feisty>Gutsy) and only have 256M RAM which is apparently not enough for the currently available 8.04 CD...

> 
Really? Where does it fail; on detecting available networks or on requesting an IP address from the DHCP server? Does it consistently do either?

Sorry, that may have been bad information.
Today I tested, after a good boot, shutting down & re-starting the router.
Wi-fi connection was automatically re-established OK.
I don't know how I would see where it was failing "on detecting available networks or on requesting an IP address".
Where should I be able to see that?
This morning I re-installed Wifi Radar (I removed it last year for some reason) so I don't know if that may help.

As you can see, I probably need some absolute beginner level help here!

Thanks for any further suggestions...

---

### Post by OffAxis on 2008-05-28
you can download a gutsy liveCD here:
[http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)


> ...and only have 256M RAM which is apparently not enough for the currently available 8.04 CD...

Bummer. 192 MB was the minimum recommended on gutsy. If you want to run the current release of 8.04 you could run the xubuntu version definitely and possibly the kubuntu version.

Alternatively, RAM has gotten very cheap over the last year; $20 to double or triple your RAM might be well worth it.

> I don't know how I would see where it was failing "on detecting available networks or on requesting an IP address".
Where should I be able to see that?
If I recall, with the gnome (ubuntu) desktop running the toolbar icon for the 'Network Manager' will reflect the different stages of the connection process; searching, connecting, established (I haven't used gnome in a while so I might be wrong on that). If there's a problem it'll reflect that as well.

From the command line you can type
```
ifconfig -a
```
to show all interfaces (active and inactive)
for just the wireless interfaces you can type
```
iwconfig
```
from the output **ESSID **will be your router's name, **inet addr** will be your network card's address.

you can also restart your networking from the command line with
```
sudo /etc/init.d/networking restart
```
which will run through the process again.

---

### Post by 2CV67 on 2008-05-28
Sorry I had not seen post #7 when I submitted this...

I have been playing around with Router and Wifi Radar and with Network Settings.

Booting with Router off does not seem to change much - results as before.
When I do manage to boot with Router off then bring it on, Wifi radar usually shows blue signal + "Master" + "b" (as it should) but when I try to connect it either switches to gray signal + "auto" + "g" or stays blue etc but fails to find IP address.

From a good connexion, if I use Wifi Radar to try to disconnect and reconnect then it usually fails to get an IP address.

More interesting is that if I go to Network Settings > Manual Configuration and Uncheck the Wireless Connexion before shutting down, then shut down & reboot are OK (5 out of 5 so far...) and if I then recheck the Wireless Connexion it reliably connects OK after a few seconds.

This seems to be an acceptable short-term work-around (so long as I remember...) but I would obviously like to get to the root cause & fix it!

It really seems that the problem is entirely in Ubuntu.
XP continues to (dual)-boot OK with Wifi.

Thanks for any further suggestions!

---

### Post by 2CV67 on 2008-05-29
Reply to post #7:

Thanks again for your patience!

I checked the link to the Gutsy CD but that also needs 320M RAM so not possible today.
Yes, I know I can get another 256M for about 24euro so will probably do that anyway, but one of the reasons for shifting to Ubuntu was to avoid the Microsoft arms race & live happily ever after with my 2004 PC which is adequate for all my needs!
Once I start upgrading, I will want USB2.0 capability, then a bigger screen, a better DVD writer etc  - only to find it would be cheaper to get a new PC - which would come with compulsory Vista!!
See where you are pushing me? ;)

I don't think the Network Manager ikon (now called Manual Network Configuration?) shows the stages of connexion. (I have better indicators in XP...).

I can see the stages in Wifi Radar, but that causes its own problems - see below.

Out of interest, I ran the terminal commands you mentioned, after I had established good connexion via Manual Network Configuration.

They are included below in case they offer any clues (not to me unfortunately).

Playing around a bit more (all I am good for!) I found that your "restart" command worked fine when Wifi Radar was not open, but failed if Wifi Radar was open (to watch the proceedings).
In this case, Wifi Radar shows the signal dropping from blue to grey, then picking up blue again, but never gets an IP address.
Using the "connect" button in Wifi radar at that stage also leads to no IP address.

Below are terminal listings for your suggested commands.
The first "restart" was OK without Wifi Radar and the second NG with Wifi radar.

Hope this means something to somebody!

Thanks for any suggestions   :)
....................................

chris@DESKTOP:~$ ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:11:5B:00:29:37  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

          Interrupt:17 Base address:0xa000 



eth0:avah Link encap:Ethernet  HWaddr 00:11:5B:00:29:37  

          inet addr:169.254.2.127  Bcast:169.254.255.255  Mask:255.255.0.0

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          Interrupt:17 Base address:0xa000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:76 errors:0 dropped:0 overruns:0 frame:0

          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:5964 (5.8 KB)  TX bytes:5964 (5.8 KB)



wlan0     Link encap:Ethernet  HWaddr 00:06:F4:07:DB:3C  

          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::206:f4ff:fe07:db3c/64 Scope:Link

          UP BROADCAST RUNNING  MTU:1500  Metric:1

          RX packets:710 errors:0 dropped:0 overruns:0 frame:0

          TX packets:740 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:815144 (796.0 KB)  TX bytes:85127 (83.1 KB)



chris@DESKTOP:~$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



wlan0     IEEE 802.11b  ESSID:"DW-B-200-3d555"  Nickname:"DW-B-200-3d555"

          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:90:4B:84:34:15   

          Bit Rate:11 Mb/s   Tx-Power=15 dBm   

          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   

          Power Management:off

          Link Quality=11/100  Signal level=23/100  

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



chris@DESKTOP:~$ sudo /etc/init.d/networking restart

[sudo] password for chris:

 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 8006

killed old client process, removed PID file

Internet Systems Consortium DHCP Client V3.0.5

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



Listening on LPF/eth0/00:11:5b:00:29:37

Sending on   LPF/eth0/00:11:5b:00:29:37

Sending on   Socket/fallback

DHCPRELEASE on eth0 to 192.168.1.1 port 67

RTNETLINK answers: No such process

There is already a pid file /var/run/dhclient.wlan0.pid with pid 8170

killed old client process, removed PID file

Internet Systems Consortium DHCP Client V3.0.5

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



Listening on LPF/wlan0/00:06:f4:07:db:3c

Sending on   LPF/wlan0/00:06:f4:07:db:3c

Sending on   Socket/fallback

DHCPRELEASE on wlan0 to 192.168.1.1 port 67

Ignoring unknown interface eth1=eth1.

Ignoring unknown interface eth2=eth2.

Ignoring unknown interface ath0=ath0.

There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120

Internet Systems Consortium DHCP Client V3.0.5

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



Listening on LPF/eth0/00:11:5b:00:29:37

Sending on   LPF/eth0/00:11:5b:00:29:37

Sending on   Socket/fallback

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6

No DHCPOFFERS received.

No working leases in persistent database - sleeping.

There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120

Internet Systems Consortium DHCP Client V3.0.5

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



Listening on LPF/wlan0/00:06:f4:07:db:3c

Sending on   LPF/wlan0/00:06:f4:07:db:3c

Sending on   Socket/fallback

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9

DHCPOFFER from 192.168.1.1

DHCPREQUEST on wlan0 to 255.255.255.255 port 67

DHCPACK from 192.168.1.1

bound to 192.168.1.9 -- renewal in 381940 seconds.

                                                                         [ OK ]

chris@DESKTOP:~$ 

................................................................

Failure with Wifi-Radar open:

chris@DESKTOP:~$ sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 8991

killed old client process, removed PID file

Internet Systems Consortium DHCP Client V3.0.5

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



Listening on LPF/eth0/00:11:5b:00:29:37

Sending on   LPF/eth0/00:11:5b:00:29:37

Sending on   Socket/fallback

DHCPRELEASE on eth0 to 192.168.1.1 port 67

RTNETLINK answers: No such process

There is already a pid file /var/run/dhclient.wlan0.pid with pid 9054

killed old client process, removed PID file

Internet Systems Consortium DHCP Client V3.0.5

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



Listening on LPF/wlan0/00:06:f4:07:db:3c

Sending on   LPF/wlan0/00:06:f4:07:db:3c

Sending on   Socket/fallback

DHCPRELEASE on wlan0 to 192.168.1.1 port 67

Ignoring unknown interface eth1=eth1.

Ignoring unknown interface eth2=eth2.

Ignoring unknown interface ath0=ath0.

There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120

Internet Systems Consortium DHCP Client V3.0.5

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



Listening on LPF/eth0/00:11:5b:00:29:37

Sending on   LPF/eth0/00:11:5b:00:29:37

Sending on   Socket/fallback

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2

No DHCPOFFERS received.

No working leases in persistent database - sleeping.

There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120

Internet Systems Consortium DHCP Client V3.0.5

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



Listening on LPF/wlan0/00:06:f4:07:db:3c

Sending on   LPF/wlan0/00:06:f4:07:db:3c

Sending on   Socket/fallback

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6

No DHCPOFFERS received.

No working leases in persistent database - sleeping.

                                                                         [ OK ]

chris@DESKTOP:~$

---

### Post by 2CV67 on 2008-05-29
Update & request:

I uninstalled Wifi Radar as it seemed to be more hinderance than help.

The workaround of using Manual Network Configuration (to uncheck Wireless Connexion before shutting down and to re-check it after boot & log-in) continues to work every time.

Is there some way I can rearrange things so Ubuntu does not try to "Configure Network Interfaces" during boot, but leaves it to me to check manually after log-in?
That way I would not need to remember to uncheck manually before shutting down.

Of course I would still like to fix things properly, but I can live with a simple workaround.

Thanks for any suggestions!

---

### Post by OffAxis on 2008-06-02
> would come with compulsory Vista!!
See where you are pushing me? ;)

Things are turning around...
[http://news.slashdot.org/article.pl?sid=08/05/19/0154224](http://news.slashdot.org/article.pl?sid=08/05/19/0154224)
:)

> Is there some way I can rearrange things so Ubuntu does not try to "Configure Network Interfaces" during boot, but leaves it to me to check manually after log-in?

I'm sure it's just a matter of a one line script added into the shutdown and startup processes, although there may be a more elegant way of doing it.
If you haven't already, you should start a new thread asking just that question. (Although this whole thing might just foreshadow the death of your network card or router.) 

Have you tried a static IP? It may not run into the same timeout issue as the DHCP request.

There's potentially two ways of defining a static (or manually assigned) IP address; one is at the computer, the other is at the router.
From the computer, you would need to set the connection up within the same subnet as your router lives;
according to your posted data your router is:
192.168.1.1
and your wireless network card is 
192.168.1.9
you could just set it manually to that with a subnet mask of:
255.255.255.0
using the network manager's GUI.

The other way is to assign your computer a static IP based on it's MAC address using your router.
So enter the router (192.168.1.1) and look for a section labeled 'Attached Devices' or 'Currently Connected Devices' or some such thing. This should list your computer's IP and MAC addresses. Maybe from this screen, maybe from another (depending on the manufacturer) you might be able to 'set' the IP.

---

### Post by dracayr on 2008-06-02
hi,

just a little hint about rebooting: you almost never have to switch off physically. once the linux kernel is loaded, the linux kernel magic keys can be used (google for "Raising Elephants Is So Utterly Boring"-no, this is not a joke). Just hold the following combinations quickly after each other:

Sys Req(normally alt+printscreen)+R
Sys Req(normally alt+printscreen)+E
Sys Req(normally alt+printscreen)+I
Sys Req(normally alt+printscreen)+S
Sys Req(normally alt+printscreen)+U
Sys Req(normally alt+printscreen)+B

to perform a safe reboot

dracayr

---

### Post by 2CV67 on 2008-06-02
Thanks guys!

Now I have lots of different things to play with!

I will try the elephant thing next time I get stuck - had never heard of it.
How near to disaster  does this procedure bring you (one shaky finger & everything wiped out??)

I installed another 256M RAM today, so could try the fresh CD approach if still worth doing.

My workaround still works (fingers crossed) so I will kick off another thread to see if it is reasonable to automate some of it.

I have bad memories of trying fixed IP addresses last time, but maybe if I take it slowly...

All that should keep me quiet for a bit!

Thanks again!

---

### Post by 2CV67 on 2008-06-03
OK!!!

Changing to fixed IP (exactly as you suggested) works perfectly!
Boots smoothly with internet up & running.

Many many thanks!  :D

Oh yes and: For sale, 256M RAM, hardly used...  ;)

---

