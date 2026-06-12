---
title: "AR242x/542x not working Acer aspireone ZG5"
date: 2014-06-07
forum: New to Ubuntu
---

### Post by Kody_Ross on 2014-06-07
This is my first ever install of Linux on an Acer Aspire One ZG5 formerly running XP. I did a clean install without checking everything and the wireless doesn't work, but ethernet does. 

I have already removed the hard block and reinstalled the driver but I can't seem to get it to work. This is a secondary laptop and I'm just doing this to learn more about linux so no rush.  

All work I have done is with ath5k, no madwifi or ndiswrapper. I tried but it was over my head. Here is what I have:

**1. lspci, **

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Qualcomm Atheros AR242x / AR542x Wireless Network A

**2. rfkill list all, **

0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

#fixed hard block with
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k**3. iwconfig,**

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.

lsmod |grep -e ath -e 80211
ath5k                 134977  0 
ath                    23922  1 ath5k
mac80211              545990  1 ath5k
cfg80211              409394  3 ath,ath5k,mac80211

**4.~$ dmesg | grep -i -e warn -e error**

[    0.205225] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20131115/dsfield-211)
[    0.205240] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f5826ca8), AE_ALREADY_EXISTS (20131115/psparse-536)
[    0.205259] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    1.312386] i8042: Warning: Keylock active
[   14.496249] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   15.199505] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \PMBA 1 (20131115/utaddress-251)
[   15.199537] ACPI Warning: 0x00000530-0x0000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   15.199557] ACPI Warning: 0x00000500-0x0000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
kody@kody-AOA150:~$ 




I probably screwed something up digging through forums trying to find answers before I came here.  Any help would be appreciated.

---

### Post by squakie on 2014-06-07
This link is from last year, but you may want to check it out - it shows a couple of different ways people got it to work:

[http://ubuntuforums.org/showthread.php?t=2160177](http://ubuntuforums.org/showthread.php?t=2160177)

---

### Post by Kody_Ross on 2014-06-08
Thanks. I have gone through all the steps but I'm not sure how to uninstall and reinstall a driver in lubuntu? , the one in the thread didn't work.  I also have downloaded Wicd since then and the manager recognizes the router if that gives you any clues as to whats wrong.  Sorry if this is menial.

---

### Post by squakie on 2014-06-08
Do you mean it can see wireless networks but you can't connect?  I have to assume that's what you mean by "recognizes the router".  Can you connect to the router?  Perhaps you have mixed-mode running on the router - set it to just one encryption type, like WPA2 AES and use a strong password/passkey/passphrase.  Then try connecting to the router again, specifying the network password/passkey/passphrase you just set up on the router.

EDIT:  It also sometimes helps to set the router to a single channel and to just one type - preferably one that matches the capabilities of your adapter - just G if your adapter only goes to G (or if the router only supports up to G) or perhaps N if your router and adapter support it.  You obviously want the fastest connection both support.

---

### Post by Kody_Ross on 2014-06-09
yes, that is what i mean.  Thank you Ive been trying everything on the command line and it doesn't seem to work. Glad I put this in the absolute beginners section. Thanks!

---

### Post by squakie on 2014-06-09
If you try to connect to your router - using the normal GUI and wicd (I think you said you installed that) - does it return any error messages?  Does it connect to the router?  Does it ask for a password/passphrase/passkey?  If it can see the router, I would think that would mean the adapter itself and its driver are working.  There may be an incompatibility between the router and the adapter/driver - hence what I noted above.  Also, if you try to connect, does anything show when you do dmesg | tail -n 30?  (I *think* that's the syntax).

---

### Post by squakie on 2014-06-10
Didn't notice you marked this as solved.  Guess that means it must be working now, which is great!  If you wouldn't mind, please post back which steps you took to fix things.  If I was of any help that's great also, but the main thing is that it is working for you now! ;)

---

### Post by Kody_Ross on 2014-06-15
Sorry for the long response, I've been trying to figure out how to change my router settings.  Wicd doesn't ask for a password or do anything out of the ordinary, just spends a long time connecting.  Every once in awhile it will say that it is connected but it is momentary.  I haven't connected yet but what you suggested makes sense as everyone else has solved their problem with the existing forum threads. I put in the code you suggested and got this:
kody@kody-AOA150:~$ dmesg | tail -n 30
[  366.117105] ath5k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  366.117123] wlan0: associating with AP with corrupt beacon
[  366.120217] wlan0: associate with 00:18:e7:30:59:0c (try 1/3)
[  366.122263] wlan0: RX AssocResp from 00:18:e7:30:59:0c (capab=0x421 status=0 aid=26)
[  366.123357] wlan0: associated
[  366.123460] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  366.124251] wlan0: deauthenticating from 00:18:e7:30:59:0c by local choice (reason=3)
[  366.129172] cfg80211: Calling CRDA to update world regulatory domain
[  366.160610] cfg80211: World regulatory domain updated:
[  366.160623] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  366.160632] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  366.160640] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  366.160647] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  366.160655] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  366.160662] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  668.410146] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  668.789374] r8169 0000:02:00.0 eth0: link down
[  668.789507] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  668.789824] r8169 0000:02:00.0 eth0: link down
[  669.061378] r8169 0000:02:00.0 eth0: link down
[  669.062093] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  670.620569] r8169 0000:02:00.0 eth0: link up
[  670.620602] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  670.721662] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  671.101353] r8169 0000:02:00.0 eth0: link down
[  671.101390] r8169 0000:02:00.0 eth0: link down
[  671.101882] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  672.749087] r8169 0000:02:00.0 eth0: link up
[  672.749123] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  682.365308] perf samples too long (5006 > 5000), lowering kernel.perf_event_max_sample_rate to 25000

If this helps any help would be appreciated, but again its likely the router as you mentioned before.

---

