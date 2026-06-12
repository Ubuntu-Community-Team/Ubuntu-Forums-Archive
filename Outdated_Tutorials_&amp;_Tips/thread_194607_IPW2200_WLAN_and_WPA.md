---
title: "IPW2200 WLAN and WPA"
date: 2006-06-11
forum: Outdated Tutorials &amp; Tips
---

### Post by ronzo on 2006-06-11
After two days of trying to get the ipw2200 working under Dapper, I am able to present a solution (that worked for me and hopefully others) for people who are still experiencing problems with this issue:

Here's what I did (in short - detailed step-by-step howto will follow):

1) 
Installation of Ubuntu Dappper 6.06 from the alternate CD (should work with the classic one too)

2)
Install build-essentials (sudo apt-get build essentials)
Install kernel-headers (sudo apt-get linux-headers-$(uname -r))

3)
Remove the old firmware files (ipw*.fw) from /lib/firmware/$(uname -r)

4)
Download the 1.0.0-ipw2200-driver from ipw2200.sf.net al well as an appropriate firmware (2.4)

5)
Download the latest version of th ieee80211 subsystem from ieee80211.sf.net

6)
Copy the firmware-files to the same location where you deleted the olde ones in step 3

7)
unpack ieee80211- and ipw2200-files and do a "sudo sh ./remove-old" in both directories

8)
find out the running modules of ieee80211* and ipw* and remove them with rmmod (don't know if this step is really necessary)

8)
Do a "sudo make" and "sudo make install" in both directories (The ipw2200-project page says do use sudo for make as well)

9)
reboot

10)
Create the file /etc/wpa_supplicant.conf
Mine looks like that:
```
ctrl_interface=/var/run/wpa_supplicant
network={
    ssid="myssid"
    scan_ssid=1
    proto=WPA
    pairwise=TKIP
    key_mgmt=WPA-PSK
    psk="my_wpa_passphrase"
}
```

11)
Don't forget to check if eth1 is configured at startup. Otherwise you won't be able to use it. Look if you have a line like "auto eth1" and another one like "eth1 inet dhcp" in /etc/network/interfaces

12)
Try if everything works with:
sudo wpa_supplicant -D wext -i eth1 -c /etc/wpa_supplicant.conf -w -dd

The ipw driver does not work due to an IOCTL-Error. After doing some Google-Search, all I can say is that it might be a kernel issue. (Experienced the same problem in Breezy when I upgraded the kernel ... I think the last one which worked properly on my system was 2.6.9-s'thing)
So I used the wext driver which works fine for me. (Using the wext driver of WPA-Supplicant, you should not have to install the ipw2200-driver. Maybe this works after a clean Installation of Dapper - I haven't tested it yet.)

13)
If you're using dhcp, try "sudo dhclient eth1" and watch if you'll get an IP-Address.

14)
Create a start-script as described in other HowTo's. 
(like here: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623); be sure to locate wpa_supplicant ... in my case it's in /sbin and not in /usr/sbin)

---

### Post by d.h. on 2006-06-18
THANK YOU for this howto, it worked just perfectly for me. :-)

---

### Post by Chimes on 2006-06-20
I don't know, just installing network-manager (as is suggested rightfully [on this how-to]("http://ubuntuforums.org/showthread.php?t=125150") worked for me.) I guess for people who that doesn't work, along with the guide on that other thread not working, they should try this out. But I think the first thread pretty much covers it. Nice guide, though.

---

### Post by araz on 2006-06-22
After step 9) i did:

dmesg | grep ipw  and i got this:
> user@pc:~$ dmesg | grep ipw
[4294698.833000] ipw2200: disagrees about version of symbol ieee80211_wx_get_encodeext
[4294698.833000] ipw2200: Unknown symbol ieee80211_wx_get_encodeext
[4294698.833000] ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
[4294698.833000] ipw2200: Unknown symbol ieee80211_wx_set_encode
[4294698.833000] ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
[4294698.833000] ipw2200: Unknown symbol ieee80211_wx_get_encode
[4294698.833000] ipw2200: disagrees about version of symbol ieee80211_txb_free
[4294698.833000] ipw2200: Unknown symbol ieee80211_txb_free
[4294698.833000] ipw2200: disagrees about version of symbol ieee80211_wx_set_encodeext
[4294698.833000] ipw2200: Unknown symbol ieee80211_wx_set_encodeext
[4294698.833000] ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
[4294698.833000] ipw2200: Unknown symbol ieee80211_wx_get_scan
[4294698.833000] ipw2200: disagrees about version of symbol ieee80211_rx
[4294698.833000] ipw2200: Unknown symbol ieee80211_rx
[4294698.833000] ipw2200: disagrees about version of symbol ieee80211_rx_mgt
[4294698.833000] ipw2200: Unknown symbol ieee80211_rx_mgt
[4294698.833000] ipw2200: disagrees about version of symbol free_ieee80211
[4294698.833000] ipw2200: Unknown symbol free_ieee80211
[4294698.834000] ipw2200: disagrees about version of symbol alloc_ieee80211
[4294698.834000] ipw2200: Unknown symbol alloc_ieee80211



the modprobe ipw2200 result is:
> user@pc:~$ sudo modprobe ipw2200
WARNING: Error inserting ieee80211_crypt (/lib/modules/2.6.16-ck12/net/ieee80211/ieee80211_crypt.ko): Invalid module format
WARNING: Error inserting ieee80211 (/lib/modules/2.6.16-ck12/net/ieee80211/ieee80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ipw2200 (/lib/modules/2.6.16-ck12/kernel/drivers/net/wireless/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)



Can anyone help me to fix this?

thanks :D

---

### Post by njzillest on 2006-07-26
Thank you, im going to use this for Knoppix std.

---

### Post by RD1945 on 2006-07-26
> **araz said:**
> After step 9) i did:

dmesg | grep ipw  and i got this:



the modprobe ipw2200 result is:



Can anyone help me to fix this?

thanks :D

Did you rmmod **_all_** the ieee80211 and ipw modules ( check step 8 )? If you did not then do so ( check loaded modules by typing 'lsmod' ). After you unloaded **_all_** the modules type 'modprobe ipw2200'.

---

