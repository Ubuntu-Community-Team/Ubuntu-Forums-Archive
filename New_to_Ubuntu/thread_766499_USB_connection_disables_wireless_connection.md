---
title: "USB connection disables wireless connection"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Stefanie on 2008-04-25
I charge my mobile phone's battery using an USB cable. Every time i plug it in, it disables my wireless connection. Instead there is made a connection with "wired network (unknown USB interface)" and I have to switch back to the wireless connection. My OS is Ubuntu Gutsy. The wireless connection itself works without any problems.

How can I stop the USB connection from disabling the wireless connection?

---

### Post by dark_harmonics on 2008-05-21
> **Stefanie said:**
> I charge my mobile phone's battery using an USB cable. Every time i plug it in, it disables my wireless connection. Instead there is made a connection with "wired network (unknown USB interface)" and I have to switch back to the wireless connection. My OS is Ubuntu Gutsy. The wireless connection itself works without any problems.

How can I stop the USB connection from disabling the wireless connection?

can you post the last few lines of the command dmesg just after you plug in the device? It is defintely possible to blacklist the module so that it doesnt load. Also, you can manually tell it to use your wireless instead of that USB device.

---

### Post by Stefanie on 2008-05-22
```
[39670.220000] Unknown OutputIN= OUT=eth2 SRC=169.254.2.2 DST=169.254.2.1 LEN=29 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32996 DPT=5679 LEN=9 
[39670.272000] Unknown OutputIN= OUT=eth2 SRC=169.254.2.2 DST=169.254.2.1 LEN=29 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32996 DPT=5679 LEN=9 
[39670.324000] Unknown OutputIN= OUT=eth2 SRC=169.254.2.2 DST=169.254.2.1 LEN=29 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32996 DPT=5679 LEN=9 
[39670.376000] Unknown OutputIN= OUT=eth2 SRC=169.254.2.2 DST=169.254.2.1 LEN=29 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32996 DPT=5679 LEN=9 

```

i managed to set up opensync and i discovered that syncing only works when the connection is set to this "wired network (usb interface)". it's annoying that it disables my wireless every time i plug it in, but of course i don't want to mess up my opensync setup.

---

### Post by dark_harmonics on 2008-05-22
Yea blacklisting the module would disable your opensync for sure. Ubuntu by default prefers a wired internet connection over a wireless connection (which makes sense). I think the angle to go at this here is to see if we can change that behaviour for you. If you right click your connection icon and uncheck the wired connection it should disable it. If you need your wired connection you will need to re-enable though.

---

### Post by Stefanie on 2008-05-22
thanks for your help. right-clicking on the network icon only gives the options "disable 
networking" (which disables everything) and "disable wireless". 

i know it makes sense to prefer wired connections over wireless, but it's weird to have my downloads interrupted or aborted when i plug in my phone.

is the output of dmesg normal (see post above)? the list goes on and on like that.

---

### Post by starcannon on 2008-05-22
I had similar issue with my phone, in my case going into settings and turning it off as a modem, and setting it as a usb storage device did the trick. Your phone may or may not have similar features, but it may be worth looking through your phones preferences.

---

### Post by Stefanie on 2008-05-22
> **starcannon said:**
> I had similar issue with my phone, in my case going into settings and turning it off as a modem, and setting it as a usb storage device did the trick. Your phone may or may not have similar features, but it may be worth looking through your phones preferences.

thanks, but i tried that already.

---

### Post by dark_harmonics on 2008-05-22
Not that output does seem odd. I was kind of hoping for maybe something that pointed at your device name a little more specifically but it looks like that error kind of took over. That error is basically the one saying that its trying to use your phone as an ethernet connection. Is there a modem feature in your phone that you could turn off?

Edit: just read that you already checked the phone for that. 

I think if you left-click the connection icon and go to manual configuration you should be able to turn off roaming mode for your wired connection. That might prevent the booting. Really it would be nice if you could stop the function on the phone so that hardy doesnt even see that part of it because just blacklisting the module might stop your other functionality that you want. I'll do some quick searches and post back.

Edit: the line in your dmesg that happens before that repeating error might help. Anything that refers to the module that is loaded when you plug it in. I think we might be able to disable the ethernet module without effecting your syncing.

---

### Post by Stefanie on 2008-05-23
the output of dmesg only repeats this line on and on (with different numbers): 
```
[ 1841.752000] Unknown OutputIN= OUT=eth2 SRC=169.254.2.2 DST=169.254.2.1 LEN=29 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32775 DPT=5679 LEN=9 
```
even when i scroll all the way up in the terminal i can't see anything else.

my phone is a samsung sgh i-320s. i have this "modem link" feature, but it is deactivated. the other settings are set up to use active sync. i'll check the manual to make sure. 

i tried to disable the roaming mode for eth2, but as a result the "wired network: usb interface" entry disapeared from the list, and i need it to use opensync.

isn't there an option to stop connections from disabling each other, and to have wireless and usb at the same time? 

thank you for helping me!

---

### Post by Stefanie on 2008-05-23
oh by the way i don't know if this may help you but i'm still using gutsy. i will upgrade in summer when i have a new external HDD to make backups.

---

### Post by dark_harmonics on 2008-05-26
I do apologize for the delay here. Just made it from Pittsburgh to Florida (ahh sunny state). If you can replug the device and then like the next second you plug it in run the dmesg command, then you should get output that is different right before the repeating error message.  That output could really help figure out which module is loading here. If not then try this:

run sudo lsmod>before.txt
then connect the device
then run sudo lsmod>after.txt
then run diff before.txt after.txt
that should output the loaded module (hopefully).

---

### Post by Stefanie on 2008-05-28
ok thanks for the tip.
this is a part of the output before the error message:
```
[   32.896000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   38.120000] usb 4-1: new full speed USB device using uhci_hcd and address 3
[   38.288000] usb 4-1: configuration #1 chosen from 1 choice
[   39.308000] usbcore: registered new interface driver cdc_ether
[   41.236000] rndis0: register 'rndis_host' at usb-0000:00:1d.3-1, RNDIS device (SynCE patched), 80:00:60:0f:e8:00
[   41.236000] usbcore: registered new interface driver rndis_host
[   43.576000] NET: Registered protocol family 17
[   51.248000] kjournald starting.  Commit interval 5 seconds
[   51.256000] EXT3 FS on sdb3, internal journal
[   51.256000] EXT3-fs: mounted filesystem with ordered data mode.
[   55.184000] eth2: no IPv6 routers present
[   99.484000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   99.716000] ieee80211_crypt: registered algorithm 'CCMP'
[   99.800000] ieee80211_crypt: registered algorithm 'TKIP'
[  118.536000] eth1: no IPv6 routers present
[ 4144.308000] usb 4-1: USB disconnect, address 3
[ 4144.308000] eth2: unregister 'rndis_host' usb-0000:00:1d.3-1, RNDIS device (SynCE patched)
[ 4151.100000] usb 4-1: new full speed USB device using uhci_hcd and address 4
[ 4151.268000] usb 4-1: configuration #1 chosen from 1 choice
[ 4153.020000] rndis0: register 'rndis_host' at usb-0000:00:1d.3-1, RNDIS device (SynCE patched), 80:00:60:0f:e8:00

```

---

### Post by dark_harmonics on 2008-05-29
Hmmm You could try blacklisting cdc_ether to see if you can keep that rdnis_host enacted (I think that is the device that does the syncing). The problem here is that your phone is advertising a network connection to your computer. Ubuntu is just picking up on what is there. 


```

sudo gedit /etc/modprobe.d/blacklist

```

add cdc_ether to the list and reboot. then connect your phone to test. If that doesnt work you may have to remove that line and try the other listed module (something like rdnis_host from your output)

---

### Post by Stefanie on 2008-05-29
i tried, but it didn't work. strange...

---

### Post by dark_harmonics on 2008-05-30
neither worked after a reboot?

---

### Post by Stefanie on 2008-05-30
nope...

---

