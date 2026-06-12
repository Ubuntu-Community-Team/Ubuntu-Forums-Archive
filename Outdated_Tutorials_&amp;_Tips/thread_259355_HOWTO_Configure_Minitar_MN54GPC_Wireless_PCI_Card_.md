---
title: "HOWTO: Configure Minitar MN54GPC Wireless PCI Card with WPA"
date: 2006-09-17
forum: Outdated Tutorials &amp; Tips
---

### Post by unco on 2006-09-17
Forget this post/howto and just go straight [here]("http://www.ubuntuforums.org/showthread.php?t=197102"), worked for me first time, only 2 minutes to complete.  Also go [here]("http://www.ubuntuforums.org/showthread.php?t=354212") for WPA. 

Things to be careful about are if using wlan0 then need that everywhere or if using eth1 then use that everywhere and also make sure your references to wpasupplicant.conf matches the file name being used (e.g. beware of the underscore in wpa_supplicant.conf mentioned in some how-tos.)

the following is OLD and out of date but has most of the commands and file needed to implement wireless with WPA.

**HOWTO Summary**
A complete set of steps for configuring a Minitar MN54GPC Wireless PCI Card (but could be ported to any card i guess) on Ubuntu 6.06 LTS using ndiswrapper and also configuring to use WPA encryption.

**References** *(can skip this)*
Thanks goes to their respective authors:
[LIST]
[*][Configuring wireless connection with ndispwrapper]("http://www.ubuntuforums.org/showthread.php?t=201902") *(Post #1) *
[*][Configuring wpa_supplicant]("http://www.ubuntuforums.org/showthread.php?t=253028") *(Post #1) *
[*][My first (semi-success) but good reference howto from 2 years ago]("http://ubuntuforums.org/showthread.php?t=22312&page=2") *(Post #13)*
[/LIST]

**HOWTO Instructions**
[LIST=1]
[*]Install Ubuntu 6.06 ...
[*]Update Ubuntu .... (need internet connection)
[*]Update following files, Change any *eth1* references to *wlan0*
```
sudo gedit /etc/modprobe.d/ndiswrapper
sudo gedit /etc/network/interfaces
sudo gedit /etc/iftab
```
[*]Restart ubuntu to bind wlan0 in place of eth1
[*]Open System\Administration\Networking from the main menu and close by clicking 'OK' to populate the /etc/network/inferfaces file .  This should have shown wireless connection as wlan0.  If not need to repeat step 3 and 4.
[*]For broadcom cards:
```
sudo rmmod bcm43xx
```
*if yours is different then need to find the appropriate driver reference being used (refer to first reference link above for how to do this ...)*
[*]```
sudo gedit /etc/modprobe.d/blacklist
```
And add following to the bottom and save
```
# custom wireless card setup ...
blacklist bcm43xx
```
[*]```
sudo apt-get install ndiswrapper-utils
```
*Need internet connection or get off cd.*
[*]Goto card makers site and download the driver zip file to the Desktop, In this case I got *802.11g USB, PCI & CardBus Updated Drivers (4.1.19.29)* from the Minitar download page.
[*]This code unzips the file, creates /drivers/wireless folder to hold driver files, move appropriate drive files and backs up zip to wireless folder.
```
unzip ~/Desktop/4.1.19.29.zip -d ~/Desktop/
mkdir ~/Desktop/wireless
sudo mkdir /drivers
cp ~/Desktop/4.1.19.29/driver/Windows_2000/ms68bm.* ~/Desktop/wireless
cp ~/Desktop/4.1.19.29.zip ~/Desktop/wireless
sudo mv ~/Desktop/wireless /drivers/wireless
sudo rm -rf ~/Desktop/4.1.19.29.*
sudo rm -rf ~/Desktop/4.1.19.29
```
[*]```
sudo ndiswrapper -i /drivers/wireless/ms68bm.inf
```
*Your driver folder can be anywhere, and your driver .inf file may have different name if not using same driver.*
[*]```
ndiswrapper -l
```
Check that hardware is present.
[*]```
sudo ndiswrapper -m
```
[*]```
sudo modprobe ndiswrapper
```
[*]```
sudo apt-get install wpasupplicant
```
[*]```
sudo gedit /etc/wpa_supplicant.conf
```
To create/edit the WPA settings file.  And add the following to the file.
```
ctrl_interface=/var/run/wpa_supplicant

network={
  proto=WPA
  key_mgmt=WPA-PSK
  ssid="MyEssid"
  psk="TopSecret"
}
```
These are all the settings I needed. But you may need more so check out reference link 2 above and also /usr/share/doc/wpa_supplicant/examples.

The psk can also be encrypted using passphrase (but I haven't been able to get this to work yet, will update if I can work it out):
```
# which wpa_passphrase
/sbin/wpa_passphrase

# sudo /sbin/wpa_passphrase MyEssid TopSecret
network={
         ssid="MyEssid"
        #psk="TopSecret"
         psk=e46827d16672b883657307d7e8e12823c63cbfa7a6d5a8364f5d8aa8bbbeacb2
}
```
[*]```
sudo gedit /etc/network/interfaces
```
and add at the bottom of the file
```
pre-up modprobe ndiswrapper
pre-up iwconfig wlan0 essid MyEssid
pre-up iwconfig wlan0 mode Managed
pre-up ifconfig wlan0 up
pre-up wpa_supplicant -D ndiswrapper -i wlan0 -c /etc/wpa_supplicant.conf -B w
post-down killall -q wpa_supplicant
```
[*]```
sudo /etc/init.d/networking restart
```
To restart your networking.
[/LIST]

## Please note this worked 100% initially but after trying to install something like a scanner it started to crap out.  I found that I needed to create a /etc/default/wpasupplicant file and updated as follows:
```
# /etc/default/wpasupplicant

# WARNING! Make sure you have a configuration file

ENABLED=1

# Useful flags:
# -D <driver> Wireless Driver
# -i <ifname> interface (required, unless specified in config)
# -c <config file> Configuration file
# -d Debugging (-dd for more)
# -w Wait for interface to come up

OPTIONS="-Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -Bw"
```

## I also moved the wlan0 settings above the eth0 settings in my /etc/network/interfaces, as I generally don't have my eth0 plugged-in and this is causing a route problem for my wlan0.  I am presently having to restart the network each time I boot using a shortcut to run in terminal with command
```
sudo /etc/init.d/networking restart
```
this makes the LAN ip addresses visible.  And when settings were the other way around even restart didn't fix problem.  I am still investigating this.

**Troubleshooting**
[LIST]
[*]Show the network configuration.
```
iwconfig
```
[*]Show wireless access points that you card is picking up.
```
iwlist wlan0 scan
```
[*]Start the wireless connection.
```
ifconfig wlan0 up
```
[*]Stop the wireless connection.
```
ifconfig wlan0 down
```
[*]Useful debugging/error details shown using -dd.
```
wpa_supplicant -D ndiswrapper -i wlan0 -c /etc/wpa_supplicant.conf -B w -dd
```
[/LIST]

---

### Post by medium on 2007-01-09
I have some problems with a Minitar MN54GPC Wireless PCI Card working with WPA on a Black-Track linux distro. I've made all the setings founded in Internet with google and the final message was: " Driver does not support WPA " and I used ms68bm.inf driver (with ndiswrapper and wpa_supplicant of course ... 
I don't know how to handle anymore ... you said that it works with Ubuntu ... 


please help me ...

---

### Post by unco on 2007-02-19
Bad news, have just upgraded to edge and wireless network no longer works, will have to run thru these steps tomorrow to see if they works.

---

### Post by unco on 2007-02-22
having to try and workout how to get it going on edgy problems doing above instructions...

---

