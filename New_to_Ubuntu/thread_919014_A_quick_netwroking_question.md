---
title: "A quick netwroking question"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by jedat1 on 2008-09-13
Hi again guys, got a strange one for you.

Just installed a wireless network card : Atheros AR5BMB-44

Ubuntu detected and installed straight away, when asked for passwords input them and connected to the internet straight away.

As i'm dual booting with XP i switched over to windows and installed there after some fiddling around managed to connect.

Now whenever i try to connect wirelessly in unbuntu it just can't connect, it finds my network and asks for passwords but just won't connect.

ANy ideas anyone?

TIA

John

---

### Post by ChanServ on 2008-09-13
you may want to try changing the pass format setting, there should be a menu under the password entry box

---

### Post by Kevbert on 2008-09-13
When the wireless card tries to connect, do you get one or more green lights (an icon) shown in the top right-hand corner of the screen ?  If you get none it may be that the wireless is powered down.
If you enter
```
iwconfig
```
in terminal you should see the wireless card (wlan0 possibly).  The TX power should be xxdBm  (not zero) and link quality should be at least 60/100 for a good connection.  If either are 0 then this confirms that the card is powered down.  If the link quality is lower, move the wireless card closer to the source.
To power up use
```
ifconfig wlan0 up 
```
(wlan0 or whatever the card is).
To check for available networks you can use
```
iwlist scanning
```
Hope this is of some use.

---

### Post by jedat1 on 2008-09-13
thanks for the help
iwconfig gives me:lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:22525  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
So if i'm reading your post right the link quality 0/70 indicates the device is powered down. 
when trying to use ifconfig wlan0 up i have to sudo bash in order to run the comand, doing that seems to work, i can scan for available networks and it does find it but won't connect.

Prior to posting i had the ring going through the two dots that should turn green, however since running the comands i now have 4 bars asscending in height that when i hover over tell me i have a 98% connection to the network.

Any other ideas?

---

### Post by Kevbert on 2008-09-14
If you have some blue bars you should be connected and should be able to open and use your Firefox browser. Also now check with
```
iwconfig
``` 
that the Link quality is at least 30/70 (eg 35/70) and signal level is better than -70dBm (say -60dBm).  If not you need to reposition the source and your PC closer together.  If you place the cursor over the blue bars it should say connected and your router name (if you have one).

---

### Post by jedat1 on 2008-09-14
blue bars tell me my network name and a 98% connection level iwconfig tells me the link is 0/70 with a signal level of -98dB.

router is 2 feet away from the pc

---

### Post by Kevbert on 2008-09-15
Something must be corrupted as you should get a good signal quality and strong signal level especially seeing as you're connected.  I'm not sure how you'll get round this as you need to re-install firmware drivers and check to see whether the driver has been blacklisted.  Hopefully someone else can suggest something.:confused::confused::confused:

---

