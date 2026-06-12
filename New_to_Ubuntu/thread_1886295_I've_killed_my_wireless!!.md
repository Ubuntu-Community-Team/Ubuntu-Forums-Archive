---
title: "I've killed my wireless!!"
date: 2011-11-24
forum: New to Ubuntu
---

### Post by dustanl on 2011-11-24
Hi all,

I'm a total noob running Kubuntu 11.10 for two and a half weeks now (total override from windows 7), and it has been mostly smooth-ish sailing up until this point, with the help of some semi-patient friends.

But now, out to thanksgiving with non-linux-acquainted family, I was trying to configure my wireless to be able to use a WPA2+TKIP connection, and honestly, I was just trying random things I found online (using an ethernet connection both then and now), which is something I'll obviously be a lot more careful about in the future.

I edited /etc/network/interfaces, and I didn't save the file contents beforehand. Right now it looks like this, which may be exactly my problem:

auto lo
iface lo inet loopback

I really have no idea what to do to fix this. Would it be appropriate to reinstall the wireless software altogether, and if so, how do I do that? Or should I be able to recover by just editing a few files? I will be happy to provide any more information as needed; I just really don't have any clue what I'm doing here.

And finally, as a follow-up question if I do manage to recover from this: I found this website [http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/](http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/) describing a way to connect from the command-line. It actually looks quite simple; am I correct in believing that I would have been able to connect much more quickly by this method, or is there a catch?

Dustan Levenstein

---

### Post by Sealbhach on 2011-11-24
You don't need to be messing about with config files unless it's something you really want to do. You can overwrite or add to the contents of /etc/network/interfaces by simply editing the connections in the network manager using the GUI.

Just make sure you have all the connection information done properly in the network manager then run

```
sudo service network-manager restart
```

I think maybe you're expecting it to be more complicated than it really is.

Just select the device you want to connect to from the list of available devices, then edit the connection and make sure you have the correct passphrase etc, and probably usually DHCP automatic. 

.

---

### Post by dustanl on 2011-11-25
> **Sealbhach said:**
> You don't need to be messing about with config files unless it's something you really want to do. You can overwrite or add to the contents of /etc/network/interfaces by simply editing the connections in the network manager using the GUI.

Just make sure you have all the connection information done properly in the network manager then run

```
sudo service network-manager restart
```I think maybe you're expecting it to be more complicated than it really is.

Just select the device you want to connect to from the list of available devices, then edit the connection and make sure you have the correct passphrase etc, and probably usually DHCP automatic. 

.

Thanks for your response; I wish I had noticed it last night. The trouble is that my wireless device is completely disabled; the "enable wireless" option of my network manager is grayed out. So unless you know of a way to recover from that from the gui, I'm pretty sure I'll have to mess with something.

---

### Post by dustanl on 2011-11-25
> **dustanl said:**
> Thanks for your response; I wish I had noticed it last night. The trouble is that my wireless device is completely disabled; the "enable wireless" option of my network manager is grayed out. So unless you know of a way to recover from that from the gui, I'm pretty sure I'll have to mess with something.

And one more thing: the reason I was messing with all this stuff was because I was having trouble connecting to the particular kind of wireless that my family had, and when I searched the security type of the wireless online, several websites suggested that some additional software would need to be installed.

---

### Post by gandaran on 2011-11-25
> The trouble is that my wireless device is completely disabled; the "enable wireless" option of my network manager is grayed out
does the wireless work with other networks or is it just this one?
and wireless drivers are installed?

---

### Post by dustanl on 2011-11-25
> **gandaran said:**
> does the wireless work with other networks or is it just this one?
and wireless drivers are installed?

It did work with other networks before I messed with it, but it won't work at all anymore.

Here's the card info via lspci -v. As I've said before, I'll be happy to provide more information; I just don't know exactly what will be useful to provide.

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: Lite-On Communications Inc Device 6613
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at c0400000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k
        Kernel modules: ath9k

thanks,
Dustan Levenstein

---

### Post by dustanl on 2011-11-25
card info using sudo:

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: Lite-On Communications Inc Device 6613
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at c0400000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 3
        Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
        Capabilities: [60] Express Legacy Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Virtual Channel
        Capabilities: [160] Device Serial Number 00-15-17-ff-ff-24-14-12
        Capabilities: [170] Power Budgeting <?>
        Kernel driver in use: ath9k
        Kernel modules: ath9k

---

### Post by roger_1960 on 2011-11-25
Hi

Could you run the following and post back the result?

> rfkill list

It may let us know if its hardware or software turning it off

---

### Post by dustanl on 2011-11-25
> **roger_1960 said:**
> Hi

Could you run the following and post back the result?



It may let us know if its hardware or software turning it off
 
Apparently it's the hardware turning it off.

dustan@dustan-Satellite-C655:~/Documents/school$ rfkill list 
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes
1: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no

---

### Post by roger_1960 on 2011-11-25
Hi

Sorry, but have to check the obvious, is there a FN + F? key combination or a physical switch which turns off the wireless, there usually is.

BTW the interfaces file in post #1 and the kernel driver look fine for that hardware.

---

### Post by dustanl on 2011-11-25
> **roger_1960 said:**
> Hi

Sorry, but have to check the obvious, is there a FN + F? key combination or a physical switch which turns off the wireless, there usually is.

BTW the interfaces file in post #1 and the kernel driver look fine for that hardware.

Crap, I can't believe I got tripped up by such a basic error. Thanks a lot for checking the obvious!
 :P

I'm still having trouble connecting this particular wireless, though, either through the gui or through the  method outlined in the website I linked to earlier ([http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/](http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/)). Here's the details of the wireless network I'm attempting to connect to, obtained by sudo iwlist wlan0 scan:

          Cell 01 - Address: 00:0D:3A:28:CB:9F
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"MSHOME"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000029da6145f6
                    Extra: Last beacon: 552ms ago
                    IE: Unknown: 00064D53484F4D45
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD050010180104
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

and here's the error I get when I try sudo iwconfig wlan0 essid ...:

Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.

Should I start a new thread for this problem?

I really appreciate your help. Thanks a lot,
Dustan Levenstein

---

### Post by roger_1960 on 2011-11-25
Hi again

Done it myself!

I think one of the following commands may solve the problem.  Try them one at a time.
(The first one is likely I think)

```
iwconfig eth0 mode auto
iwconfig eth0 power off
iwconfig eth0 rate auto
iwconfig eth0 channel auto
```

To see what this means type the following in terminal

```
man iwconfig
```

(Press "Q" to exit the listing)

---

### Post by dustanl on 2011-11-25
> **roger_1960 said:**
> Hi again

Done it myself!

I think one of the following commands may solve the problem.  Try them one at a time.
(The first one is likely I think)

```
iwconfig eth0 mode auto
iwconfig eth0 power off
iwconfig eth0 rate auto
iwconfig eth0 channel auto
```To see what this means type the following in terminal

```
man iwconfig
```(Press "Q" to exit the listing)

All of those gave an error using eth0; I'm guessing you meant to say wlan0? In that case, mode auto gave an error (below), and the rest ran without complaint. I tried connecting in between each, and failed each time, with the same error.

Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

---

### Post by roger_1960 on 2011-11-25
Hi

Going mad

Try the mode setting with with phy0 instead of eth0. (Going away for 1 hour as star trek is starting!)

---

### Post by dustanl on 2011-11-25
> **roger_1960 said:**
> Hi

Going mad

Try the mode setting with with phy0 instead of eth0. (Going away for 1 hour as star trek is starting!)

No good; phy0 doesn't exist. :/

Here's another piece of information that might be of interest: when I go to "manage connections" through the gui, and select this wireless and edit, it pops up  an error, titled "Error - KDE Control Module", with the message "No agents were available for this request.". Then it gives me the details of the current settings (for which nothing I've tried so far has worked...).

Thanks for trying, roger!

---

### Post by Sealbhach on 2011-11-25
You're using Kubuntu? I had trouble with wireless dropping in Kubuntu 11.10 so I install wicd and wicd-kde, then removed network-manager-kde and the plasma network thingy, since then I've had no trouble. Wicd is very easy to use and configure and is really robust.

.

---

### Post by dustanl on 2011-11-25
> **Sealbhach said:**
> You're using Kubuntu? I had trouble with wireless dropping in Kubuntu 11.10 so I install wicd and wicd-kde, then removed network-manager-kde and the plasma network thingy, since then I've had no trouble. Wicd is very easy to use and configure and is really robust.

.

Excellent, that works! =D

---

