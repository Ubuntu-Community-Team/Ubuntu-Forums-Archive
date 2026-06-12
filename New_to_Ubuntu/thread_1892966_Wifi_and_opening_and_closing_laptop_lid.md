---
title: "Wifi and opening and closing laptop lid"
date: 2011-12-09
forum: New to Ubuntu
---

### Post by resander on 2011-12-09
This is for a second-hand Fujitsu Biblo netbook obtained in Japan. It runs Windows Vista and for some reason the netbook had two partitions C 18GB and D 17GB with 38GB unallocated disk space at the end.

Drive C is small and when watching streaming videos the netbook usually ran out of space on drive C after about 5-10 minutes and displayed a 'buffering problem' message. It was not possible to continue watching any moving pictures and disk space had to be reclaimed.

I thought of using the gparted partition editor on an Ubuntu Live CD to move the D partition (Vista Diskmanager cannot move partitions) and then extend C into the gap, but was uncertain and checked with Vista Forums first. Several responses strongly indicated this should not be done, so I decided on a dual boot and added Ubuntu 10.04.03 LTS into the 38GB unallocated space. The dual-booting worked fine.

I use desktop PCs daily with a wired connection to a router but have no experience using laptops or netbooks so have a few questions...

The router is a Belkin with firmware version 9.01.05 connected to Virgin Broadband via a cable modem provided by Virgin.

Q1. The Wifi does not behave the same on Ubuntu and Vista. 
 Vista:  The wifi comes on automatically when opening the lid after having suspended/stopped by closing the lid. That is how I expected it to be.
 Ubuntu: The wifi is normally off when opening the lid or and the Belkin SSID has to be selected and clicked from the wifi router connect list. 
Programs suspended by closing the lid report 'cannot find web address so-and-so' when the lid is opened which is confusing to occasional users.
Is this the normal behaviour for Ubuntu?

Q2. Sometimes a rotating 'Connection pending' cursor/icon shows when opening the lid, but it never completes. Clicking the icon displays the name/ssid of of the pending connection. It shows names like BTFON (unprotected) or SkyXXXX (with password, not our router), but has never shown the Belkin name expected. Why is this happening?

Q3.  I googled on BTFON and found it is some kind wifi hotspot service offered by BT (British Telecom) and Fon. I don't know why BTFON would be on our router since we have broadband on tap from Virgin. We don't need or want this hotspot service. How to get rid of it?

Ken

---

### Post by SteveDee on 2011-12-09
Q2/3: BTFON is probably coming from a neighbours router. I suggest you open Synaptic, then search & install: wifi-radar

This application will show you all the wifi access points within range (including your own), the signal levels and the channels they are running on.

---

### Post by kc1di on 2011-12-09
> **resander said:**
> 

Q1. The Wifi does not behave the same on Ubuntu and Vista. 
 Vista:  The wifi comes on automatically when opening the lid after having suspended/stopped by closing the lid. That is how I expected it to be.
 Ubuntu: The wifi is normally off when opening the lid or and the Belkin SSID has to be selected and clicked from the wifi router connect list. 
Programs suspended by closing the lid report 'cannot find web address so-and-so' when the lid is opened which is confusing to occasional users.
Is this the normal behaviour for Ubuntu?


The answer is yes when you suspend or hibernate it disconnects the wireless or wired connection to the network.  when you open the lid it will take a few moments to reconnect.

---

### Post by resander on 2011-12-09
Thanks for letting me know about wifi-radar. It confirmed BTFON is coming from a neighbour.

I am still puzzled ....

1.  Closing laptop lid when wifi disconnected or connected to Belkin:
When reopening lid the system attempts to connect TalkTalkXYZ (or any named signal within reach) that comes from a neighbour and is password protected. This causes the wifi password entry to pop up which I cancel since I don't know the password. The system then attempts to connect to BTFON which is successful but the signal is weak. I have not seen the system trying to connect to Belkin.  

2.  closing by shutdown from the menu or pressing power button for 3 seconds when wifi connected or disconnected to Belkin:
Behaviour same as for 1 above.

This is surprising. I would have expected the system either to connect to Belkin or not to connect at all depending on the connect state when the lid or system was closed.

Any ideas what might be causing this? Anything I can try?

Ken

---

### Post by SteveDee on 2011-12-09
> **resander said:**
> ...Any ideas what might be causing this? Anything I can try?

Not sure if I can be much help on this one...but at least this will bump your thread!

1. When you start your computer from cold, does it auto connect to your router?
2. Is your router providing the strongest signal of all those detected by the system.
3. When you select "Edit Connections..." for network/wifi (sorry can't remember what 10.04 interface looks like) can you select "Connect Automatically" and "Available to all users" for your Belkin access point, and de-select these options for any other access point listed?
4. How does the Belkin channel compare with the one that your system wants to connect to? This is desperate, but try changing your Belkin channel, avoiding channels already used by strong access points if possible.

---

### Post by resander on 2011-12-09
SteveDee many thanks for your input.

My feedback to your questions: 

1. When you start your computer from cold, does it auto connect to your router?
It does not connect to my router i.e. the Belkin. Instead it tries a neighbour's router, first one with password (TalkTalk or a Sky) and when that times out waiting for a password (that I don't know) it then tries BTFON and succeeds. BTFON is not ours and is too weak. 

2. Is your router providing the strongest signal of all those detected by the system.
Yes

3. When you select "Edit Connections..." for network/wifi (sorry can't remember what 10.04 interface looks like) can you select "Connect Automatically" and "Available to all users" for your Belkin access point, and de-select these options for any other access point listed?
There is an 'Edit Connections' menu item coming up when I right-click the wifi icon in the topbar. Clicking Edit Connections brings up a 'Network Connections' dialog that lists the signals within reach, but does not have "Connect Automatically" and "Available to all users" toggle entries.

4. How does the Belkin channel compare with the one that your system wants to connect to? This is desperate, but try changing your Belkin channel, avoiding channels already used by strong access points if possible.
The Belkin is on channel 13 the other signals are using channels 1 and 6 according to wifi-radar.

Ken
P.S. I selected WEP mode wifi security for the router (uses a ten-character password containing letters a to f and digits 0 to 9).


__

---

### Post by coffeecat on 2011-12-09
> **resander said:**
> There is an 'Edit Connections' menu item coming up when I right-click the wifi icon in the topbar. Clicking Edit Connections brings up a 'Network Connections' dialog that lists the signals within reach, but does not have "Connect Automatically" and "Available to all users" toggle entries.

@resander, you didn't go quite far enough.

Left or right-click (it doesn't matter which) on the Network Manager icon and choose "Edit connections". Click on the "Wireless" tab. Highlight your Belkin network name and then click on the "Edit" button. A new windowlet opens. The "Connect Automatically" tickbox is near the top. Make sure it is ticked.

**EDIT**: Another thing to check when you have the edit connections window open. Apart from your Belkin network in the wireless tab, do you have any other named networks listed? In particular, BTFON? If you've accidentally clicked on another listed network at any time, an entry will be created here, and since BTFON networks are not password protected, the system may connect automatically. Delete BTFON in the wireless tab and any other networks that are not your own Belkin one.

---

### Post by SteveDee on 2011-12-10
> **resander said:**
> ..This is for a second-hand Fujitsu Biblo netbook obtained in Japan...The Belkin is on channel 13...

Aha! the magic channel 13...Something you should know about wifi channels is that they are not Global. There are 14 channels specified in the 2.4GHz band, but not all countries allow the use of all (or even the same) channels.

Channel 13 is interesting because we Brits can use it, but our cousins in North America can't. And I've found that some laptops only work on the US bands 1 to 11. On Windows this can be due to drivers or localisation settings, on Linux this can only be due to hardware/firmware.

So as channels 1 & 6 look a bit busy where you are, set your Belkin to channel 11 and try again.

Also look at coffeecat's note on editing connections.

---

### Post by SteveDee on 2011-12-10
> **resander said:**
> ...I selected WEP mode wifi security for the router (uses a ten-character password containing letters a to f and digits 0 to 9).


...and another thing, once you get wifi working, look at your Belkin security options. If WPA is listed, use this instead of WEP as this is more secure.

One word of caution. Many of the cheap USB wifi dongles available used to (this may possibly still be the case) only support WEP. So don't try changing security settings until all your devices are working.

---

### Post by coffeecat on 2011-12-10
> **SteveDee said:**
> Channel 13 is interesting because we Brits can use it, but our cousins in North America can't. And I've found that some laptops only work on the US bands 1 to 11. On Windows this can be due to drivers or localisation settings, on Linux this can only be due to hardware/firmware.

So as channels 1 & 6 look a bit busy where you are, set your Belkin to channel 11 and try again.

Good catch about channel 13 - I missed that! :)

---

### Post by resander on 2011-12-14
Many thanks SteveDee & Coffeecat,

Sorry for the delay, but I could not lay my hands on the netbook. It has been out of the house for some days.

Did what you suggested and the netbook now connects quickly and automatically following lid reopen and cold start. Great!

But wife who is using the netbook has observed buffering problems when watching overseas news streaming videos. She had this problem on Vista too but says it is worse on Ubuntu. I did not expect that, so need to understand why. Will start another thread when I have collected more data and experimented a bit.

Again, many thanks.

Ken

---

