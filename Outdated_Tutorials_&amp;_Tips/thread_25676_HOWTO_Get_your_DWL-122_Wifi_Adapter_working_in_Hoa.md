---
title: "HOWTO: Get your DWL-122 Wifi Adapter working in Hoary"
date: 2005-04-10
forum: Outdated Tutorials &amp; Tips
---

### Post by tidalwav1 on 2005-04-10
Right. I bought the DWL-122 hoping it would work with Linux, because it supported MacOS. After a LOT of research, I was able to actually get this thing working in Hoary (without ndiswrapper. Ndiswrapper would probably be a better solution, if it worked.)

So right, here's the steps I took to get the adapter working in Hoary:

1) In a terminal, type:```
sudo apt-get install linux-wlan-ng
```This package should already be on the hard drive of a default Hoary install...the package just isn't actually installed by default. This package acts as a driver of sorts for the DWL-122.

2) In a terminal, type:```
sudo nano /etc/network/if-pre-up.d/linux-wlan-ng-pre-up

``` Hit CTRL+W, type the word 'result', and hit enter. The cursor should be focused on a line that says ```
result=`$WLANCTL $IFACE lnxreq_ifstate ifstate=enable`
```Copy this line out of the file (NOT out of this HOWTO,) and paste it back into the file, right underneath itself. In essence, this line should appear twice instead of once. Hit CTRL+O, then Enter, then CTRL+X to save the file. Doing this may make your eventual internet connection (it'll happen!) less flaky.

3) In a terminal, type:```
cd /etc/hotplug/usb
sudo nano prism2_usb

```You should now be presented with an empty Nano screen. Type (substituting YOUR_ESSID for your SSID):```
sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="YOUR_ESSID" authtype="opensystem"
sudo dhclient wlan0
```Hit CTRL+O, then Enter, then CTRL+X to save the file.

What you have essentially done is made a small shell script that will connect your computer to the internet using linux-wlan-ng every time the prism2_usb module is loaded (this module is loaded when the DWL-122 is plugged into the computer.) Putting the script into the 'usb' directory and naming it 'prism2_usb' as described *should* run it on boot if the DWL-122 is present, and connect your computer to the internet.

Restart your machine. Your internet connection should be up. If you're not connected, try running the shell script manually by typing```
sudo sh /etc/hotplug/usb/prism2_usb
```into a terminal. Note that I don't use WEP (I just use MAC filtering on my network,) so I guess if you have WEP you'll have to either disable it or find a different HOWTO to get the adapter working.

That's it. This was my first HOWTO...how'd you like it? :)

---

### Post by az on 2005-04-10
You shoudl cut and paste this to the ubuntuguide thread.

---

### Post by parktownprawn on 2005-04-11
I  don't have access to a WEP encoded access point at the moment to test this out but looking at an old script i have i guess if you want to access a one you could modify the script as follows
----------------------------------------------

sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="YOUR_ESSID" authtype="sharedkey"

sudo wlanctl-ng wlan0 lnxreq_hostWEPEncrypt=true     
sudo wlanctl-ng wlan0 lnxreq_hostWEPDecrypt=true    
sudo wlanctl-ng wlan0 dot11PrivacyInvoked=true        
sudo wlanctl-ng wlan0 dot11WEPDefaultKeyID=0        
sudo wlanctl-ng wlan0 dot11ExcludeUnencrypted=false   
sudo wlanctl-ng wlan0 dot11WEPDefaultKey0=            "YOUR_KEY_0"
sudo wlanctl-ng wlan0 dot11WEPDefaultKey1=            "YOUR_KEY_1"
sudo wlanctl-ng wlan0 dot11WEPDefaultKey2=            "YOUR_KEY_2"
sudo wlanctl-ng wlan0 dot11WEPDefaultKey3=            "YOUR_KEY_3"
sudo dhcpclient wlan0

-------------------------------------------
or something like that

---

### Post by tidalwav1 on 2005-04-11
Just rewrote the entire HOWTO...it should be much easier to understand, now. :p

---

### Post by kuleali on 2005-04-13
nice, :)

---

### Post by puelly on 2005-04-14
[QUOTE=kuleali]nice, :)[/QUOTE]
 thank you for your HOWTO.  because of it I am almost ready to make the total switch to linux.

I have one prob however.  I am able to get the adapter work with the shell script after i boot but not automatically upon load.  

Does anyone know how this can be done.  It looks like the hotplug is not running the script when the machine starts.

---

### Post by tidalwav1 on 2005-04-14
[QUOTE=puelly]thank you for your HOWTO.  because of it I am almost ready to make the total switch to linux.

I have one prob however.  I am able to get the adapter work with the shell script after i boot but not automatically upon load.  

Does anyone know how this can be done.  It looks like the hotplug is not running the script when the machine starts.[/QUOTE]

Did you name the shell script 'prism2_usb' (without a filename extension) and place it in the /etc/hotplug/usb directory, as the HOWTO describes?

---

### Post by puelly on 2005-04-14
[QUOTE=tidalwav1]Did you name the shell script 'prism2_usb' (without a filename extension) and place it in the /etc/hotplug/usb directory, as the HOWTO describes?[/QUOTE]
 yep. I named it as you said. does yours load on boot without anything extra?

---

### Post by tidalwav1 on 2005-04-14
[QUOTE=puelly]yep. I named it as you said. does yours load on boot without anything extra?[/QUOTE]
 Yep. :p

You could try renaming it to 'p80211' instead of 'prism2_usb'.

---

### Post by aussieoddsocks on 2005-04-18
Just an update for those who are trying to get this working using wep. Here is what my /etc/hotplug/usb/prism2_usb file looks like :-

sudo modprobe prism2_usb prism2_doreset
sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sudo wlanctl-ng wlan0 lnxreq_hostwep decrypt=true encrypt=true
sudo wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11PrivacyInvoked=true
sudo wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKeyID=0
sudo wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKey0="<your_key>"
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="<your_ssid>" authtype="sharedkey"
sudo ifconfig wlan0
sudo sleep 2
sudo dhclient wlan0

A couple of things to note. The first modprobe - I'm not sure if it is needed, but it just resets the module to a known state. My past script had this and I just copied it accross. Secondly, the ifconfig wlan0 is just for diagnostic purposes (by the way where does the output of this script get logged to when run by hotplug?). Thirdly, the 'sleep 2' just gives the adaptor a chance to associate with the AP. Finally ubuntu uses dhclient not dhcpclient as shown in parktownprawn's script.

Hope this helps others in the future. The original post has made using wireless on my home network that much simpler (no messy scripts to run) so thanks to tidalwav1 for a great first howto.

My next project is to work out a way to get hotplug/this script to ask me for a choice of network so that I don't have to modify the file/copy another script over) when I am using my college network. Any ideas as to a possible solution?

P.S. I changed the permissions on the file to 755 in line with othe scripts in the same directory. Not sure if that was needed but the file was not executable before that.

---

### Post by omni_Z on 2005-05-08
I did these steps in the first post, on my Hoary with DWL-122, wlan0 interface appears, but I acnt get dhcp address on it neither get any signal from my AP

is this howto really works?

what I have wrong then?

this is what my iwconfig shows:

-----------------------------------------------------------------
root@zubu:/etc/wlan # iwconfig
lo        no wireless extensions.

ath0      IEEE 802.11g  ESSID:"vake_Omni_Z"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:66:53:26:72
          Bit Rate:54 Mb/s   Tx-Power:50 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=46/94  Signal level=-49 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:1   Missed beacon:1

eth0      no wireless extensions.

wlan0     IEEE 802.11-DS  ESSID:""
          Mode:Auto  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:2 Mb/s   Tx-Power:2346 dBm
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/92  Signal level=-69 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
----------------------------------------------------------------------------------------------------------------

---

### Post by tidalwav1 on 2005-05-08
[QUOTE=omni_Z]I did these steps in the first post, on my Hoary with DWL-122, wlan0 interface appears, but I acnt get dhcp address on it neither get any signal from my AP

is this howto really works?

what I have wrong then?

this is what my iwconfig shows:

-----------------------------------------------------------------
root@zubu:/etc/wlan # iwconfig
lo        no wireless extensions.

ath0      IEEE 802.11g  ESSID:"vake_Omni_Z"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:66:53:26:72
          Bit Rate:54 Mb/s   Tx-Power:50 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=46/94  Signal level=-49 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:1   Missed beacon:1

eth0      no wireless extensions.

wlan0     IEEE 802.11-DS  ESSID:""
          Mode:Auto  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:2 Mb/s   Tx-Power:2346 dBm
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/92  Signal level=-69 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
----------------------------------------------------------------------------------------------------------------[/QUOTE]

In the script, with the line
```
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="YOUR_ESSID" authtype="opensystem"
```...did you replace the YOUR_ESSID with the actual SSID of your wireless network?

---

### Post by omni_Z on 2005-05-09
yes I did, I did also ="" which should mean any essid, is it my ath0  affect somehow on my wlan0?  I am trying to get working it on the same AP, where ath0 is already hooked up. I'll try to make it on pc without other wlan cards later today. Let's see what will happen.

---

### Post by The Producer on 2005-05-09
I have the DWL-122 USB and it runs just fine on my machine using the ndiswrapper that comes with Hoary.  

All I have to do is install ndiswrapper, install the drivers, and it's working almost instantly.

I guess it's just my machine...

---

### Post by az on 2005-05-09
It does depend on the machine.  I lent my dwl122 to a friend at work and could never get it to work on his two machines (WindowsXP) at home.  It half-worked on my real machine at home.

It works fine on a pentium one I have sitting on the floor by my feet...

---

### Post by tidalwav1 on 2005-05-26
[QUOTE=azz]It does depend on the machine.  I lent my dwl122 to a friend at work and could never get it to work on his two machines (WindowsXP) at home.  It half-worked on my real machine at home.

It works fine on a pentium one I have sitting on the floor by my feet...[/QUOTE]
 If that's true than that's very odd...how could computers running the same software, looking for the same piece of hardware (the DWL-122, obviously,) respond differently? Weird.

---

### Post by janit on 2005-06-04
[QUOTE=omni_Z]yes I did, I did also ="" which should mean any essid, is it my ath0  affect somehow on my wlan0?  I am trying to get working it on the same AP, where ath0 is already hooked up. I'll try to make it on pc without other wlan cards later today. Let's see what will happen.[/QUOTE]

I'm also having some problems connecting to the AP (naturally DHCP does not work for me, either). I'm using the WEP script by aussieoddsocks. The result is as follows:

```
janit@charles:~$ sudo sh /etc/hotplug/usb/prism2_usb
message=lnxreq_ifstate
  ifstate=enable
  resultcode=success
message=lnxreq_hostwep
  resultcode=no_value
  decrypt=true
  encrypt=true
message=dot11req_mibset
  mibattribute=dot11PrivacyInvoked=true
  resultcode=success
message=dot11req_mibset
  mibattribute=dot11WEPDefaultKeyID=0
  resultcode=success
mibattribute="data_string_too_short"
message=dot11req_mibset
  mibattribute=data_string_too_short
  resultcode=no_value
message=lnxreq_autojoin
  ssid='dihome'
  authtype=sharedkey
  resultcode=success
wlan0     Link encap:UNSPEC  HWaddr 00-0D-88-7F-6D-D8-B0-F8-00-00-00-00-00-00-00-00  
          inet6 addr: fe80::20d:88ff:fe7f:6dd8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21416 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:82 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32831663 (31.3 MiB)  TX bytes:0 (0.0 b)
```

The "data_string_too_short" part seems a bit suspicious, but I've no idea why it's like that when my password definitely is 5 chars long. The AP is running 40bit ASCII WEP. This is what iwconfig says:

```
janit@charles:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11-DS  ESSID:"dihome"  Nickname:"dihome"
          Mode:Auto  Frequency:2.467 GHz  Access Point: 00:00:00:00:00:00   
          Bit Rate:2 Mb/s   Tx-Power:2346 dBm   
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Link Quality=0/92  Signal level=-69 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
``` 

I can use airsnort to pick up the access point, but that's it... Any ideas?

---

### Post by bobyorke on 2005-06-09
Just got mine working. Thanks for the help here guys.
I had the mattribute too short fault. My fix was the WEPkey with no "s and interspersed with a colon every two bytes, e.g 01:02:03:04:06:07:08:09:0A:0B:0C:0D... however long it is.

Now I'm up and running and about to unleash the Ubuntu!

---

### Post by Pheonicks on 2005-08-15
**Ok I was reffered here by Azz and have followed every step but still am having some problems. heres the output.**

sudo:wlanctl-ng: command not found
wlanctl-ng: no such device
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium
All rights reserved.
For info, please isit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFFLAGS: No such device
SIOCSIFFLAGS: No such device
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:00:00:00:00:00
Sending on   LPF/wlan0/00:00:00:00:00:00
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.25.255.255 port 67 interval 6
send_packet: Network is down

[B]Now Im not using a DWL-122 Wifi adapter but it is a prism based device and prism2_usb should work from what I've read. It seems obvious to me that it won't find the network if it can't find the device. The device is listed in my Device manager but it still doesn't know what it is besides that it is a melco device. And it is plugged in (I've tried both USB sockets). Am I missing something?

Thanks for your assistance
John[/B]

---

### Post by az on 2005-08-15
[QUOTE=Pheonicks]sudo:wlanctl-ng: command not found
[/QUOTE]


Are you sure that you have linux-wlan-ng installed?   Look in synaptic and search for that package.  It is on the cd, so you do not have to be on the net to instal it.

Also, show the last few line of 
dmesg

after you plug in the device and wait for a few seconds.  Boot into ubuntu, wait until the desktop is ready, plug in the device and wait for five seconds, then open up a terminal and type 
dmesg


The last lines should show whan module is loaded by hotplug after the thing is plugged in.

---

### Post by Pheonicks on 2005-08-15
[QUOTE=azz]Are you sure that you have linux-wlan-ng installed?   Look in synaptic and search for that package.  It is on the cd, so you do not have to be on the net to instal it.

Also, show the last few line of 
dmesg

after you plug in the device and wait for a few seconds.  Boot into ubuntu, wait until the desktop is ready, plug in the device and wait for five seconds, then open up a terminal and type 
dmesg


The last lines should show whan module is loaded by hotplug after the thing is plugged in.[/QUOTE]
 linux-wlan-ng was installed and dmesg does show something...

prism2usb_init: prism2_usb.o: 0.2.1-pre25 loaded
prism2usb_init dev_info is: prism2_usb
usbcore: registered new driver prism2_usb

However these are lines 23,24 and 25 from the bottom respectively

Also when I double checked synaptic it said in the description:

"This package is useless without the appropriate linux-wlan-ng-modules-x.yy.zz
package for the kernel you are running. You may have to build that by hand;
see the README.Debian for instructions"

Could this be the problem? I wouldn't think so since it wasn't mentioned in the initial how-to.

Thanks again..

John

---

### Post by az on 2005-08-15
[QUOTE=Pheonicks]linux-wlan-ng was installed and dmesg does show something...

prism2usb_init: prism2_usb.o: 0.2.1-pre25 loaded
prism2usb_init dev_info is: prism2_usb
usbcore: registered new driver prism2_usb

However these are lines 23,24 and 25 from the bottom respectively

Also when I double checked synaptic it said in the description:

"This package is useless without the appropriate linux-wlan-ng-modules-x.yy.zz
package for the kernel you are running. You may have to build that by hand;
see the README.Debian for instructions"

Could this be the problem? I wouldn't think so since it wasn't mentioned in the initial how-to.

Thanks again..

John[/QUOTE]

No.  The messages you see are the driver being loaded.  It is part of the stock kernel.  Do not worry.   23 lines after those messages???  Are you getting error messages and stuff?

Do you have any other usb devices plugged in?

---

### Post by Pheonicks on 2005-08-15
[QUOTE=azz]No.  The messages you see are the driver being loaded.  It is part of the stock kernel.  Do not worry.   23 lines after those messages???  Are you getting error messages and stuff?

Do you have any other usb devices plugged in?[/QUOTE]
 linux-wlan-ng-module

s-x.yy.zz is the stock kernel?

Yes 23 lines of things loaded afterwards, including my nic card.

No error messages that I recall. I look again though.

No other usb devices plugged in.

---

### Post by derekr44 on 2005-11-02
Bringing up an old post here... but my problem is linked to it.  Check out my problem thread here: [http://ubuntuforums.org/showthread.php?t=84802](http://ubuntuforums.org/showthread.php?t=84802)

---

### Post by thenoobest1 on 2005-11-21
I just want to say good job... you are the only person who has been able to cure the hemeroid of wireless networking for me and linux lol.

---

### Post by WileE on 2005-12-02
[QUOTE=tidalwav1]Yep. :p

You could try renaming it to 'p80211' instead of 'prism2_usb'.[/QUOTE]
I had the same problem.  I put the prism2_usb file under hotplug.d/usb and that seemed to do the trick.

[QUOTE=aussieoddsocks]Just an update for those who are trying to get this working using wep. Here is what my /etc/hotplug/usb/prism2_usb file looks like :-

mibattribute=dot11WEPDefaultKey0="<your_key>"
[/QUOTE]
This was mentioned in another thread, but your key should have a colon between every two chars:  AA:11:BC:14:

---

### Post by linmu on 2005-12-12
Type (substituting YOUR_ESSID for your SSID):
```

sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="YOUR_ESSID" authtype="opensystem"
sudo dhclient wlan0
```Hit CTRL+O, then Enter, then CTRL+X to save the file.

Lin here:
ok, this is great. But I am missing how to find my "ssid" or "essid". This is differant than MAC address, corect? 
Is this just the name I stuck on the network?

I am trying to run a DWL-122, on a iMac G3 DV SE, (10.3.9), connecting to an "Actiontec" router. Ubuntu 5.10 loads, boots, and runs great. But no connection through dwl-122.
I would run the above "how-to" but where do I find this "ESSID" string to plug into the script?

---

### Post by tidalwav1 on 2005-12-19
The SSID is indeed the name you gave the network. Usually the default SSID for a Linksys router, for example, is "Linksys".

---

### Post by scottt106 on 2006-05-21
[QUOTE=tidalwav1]You could try renaming it to 'p80211' instead of 'prism2_usb'.[/QUOTE]


I was having this same issue, and renaming my hotscript p80211 did the trick.  Thanks for the tip  :)

---

### Post by eSeong on 2006-11-01
> **Pheonicks said:**
> linux-wlan-ng-module

s-x.yy.zz is the stock kernel?

Yes 23 lines of things loaded afterwards, including my nic card.

No error messages that I recall. I look again though.

No other usb devices plugged in.

I get this error too, could anyone help us ?

As for the usb devies, i got mouse and keyboard being plugged in.

( sorry for my bad english )

---

