---
title: "Broadcom Wireless Not Working (BCM 57780)"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by tibor834 on 2013-01-10
Hi, I need help getting my wireless connection working. More specifically, the system seems to recognize my wireless connection (it shows as 'connected' from the task bar after inputting my password, with strong signal strength), but will not load pages unless I use a wired connection. I've spent many days trying to get this sorted out, but have found that most discussions by those with similar problems are of two types:

1. They pertain to BCM 43x cards, and do not work for me.
2. They are at a technical level that is beyond what I understand so far (I need the internet to learn Linux, but I need to know Linux to access the internet :/)

Wireless is important to me and I've tried everything I can find/research/think of,
so I'm about to pack it in and switch back to Windows, but figured I'd throw a hail mary out here first.

Here's some basic info that might help:

**Computer: **Acer Aspire 5733-6696

**Wireless card:** 01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)

**iwconfig:**

lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"BELL453"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 2C:E4:12:89:F7:2F   
          Bit Rate=150 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:31   Missed beacon:0

eth1      no wireless extensions.

**uname -a:**

Linux xubuntu 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:04:05 UTC 2012 i686 i686 i386 GNU/Linux

I should maybe mention that I first tried a Mint partition, but when I couldn't solve the problem tried live booting Xubuntu in the desperate hope that a different distribution might have patched the problem somehow. So I don't have Xubuntu fully installed, and would prefer to get this working before reformatting my hard drive again :)

It also seems that a common solution for some people is to run this or some variant in the terminal:

~$ sudo modprobe -r tg3
~$ sudo modprobe broadcom
~$ sudo modprobe tg3

I've tried this and several variations, to no avail.

So, if anyone could help me out, that would be very greatly appreciated. Otherwise, thanks for reading :)

---

### Post by bkratz on 2013-01-10
**Wireless card:** 01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)



The device you listed is the ethernet card, not the wireless.  In your lspci did you see one the was labeled   ( Network not ethernet)


or you could just post the results of



lspci -nn | grep 0280

---

### Post by tibor834 on 2013-01-10
Thanks for your reply, the results of that command are:

~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

---

### Post by squakie on 2013-01-10
Try:

lsmod

Do you see ath9k listed?  If not:

sudo modprobe ath9k

IF that helps (not sure if it will), then:

sudo echo ath9k >> /etc/modules

---

### Post by tibor834 on 2013-01-10
Yes, ath9k is listed:

~$ lsmod
Module                  Size  Used by

ath9k                 117425  0 
ath9k_common           13781  1 ath9k
ath9k_hw              391554  2 ath9k,ath9k_common
ath                    19387  3 ath9k,ath9k_common,ath9k_hw

---

### Post by bkratz on 2013-01-10
frequent disconnects sometimes happen with ath9k. Generally encryption (hard vrs software) takes care of a lot of issues

try


sudo rmmod ath9k
sudo modprobe ath9k nohwcrypt=1

If that helps then we will make it permanent with : 

echo "options ath9k nohwcrypt=1">>/etc/modprobe.d/ath9k.conf

if not we didn't hurt anything!

---

### Post by tibor834 on 2013-01-10
Hmm doesn't work, still no internet once I unplug my wire connection

---

### Post by bkratz on 2013-01-10
> **tibor834 said:**
> Hmm doesn't work, still no internet once I unplug my wire connection

I see you also have powermanagement turned on (in red) ; probably worth trying to turn it off with 

sudo iwconfig wlan0 power off

should have be sudo iwconfig wlan1 power off---sorry


wlan1 IEEE 802.11bgn ESSID:"BELL453" 
Mode:Managed Frequency:2.447 GHz Access Point: 2C:E4:12:89:F7:2F 
Bit Rate=150 Mb/s Tx-Power=15 dBm 
Retry long limit:7 RTS thrff Fragment thrff
[COLOR="Red"]Power Management:on[/COLOR]
Link Quality=63/70 Signal level=-47 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:31 Missed beacon:0

---

### Post by tibor834 on 2013-01-10
Thanks -- power management is now off using wlan1, but still no improvement in terms of the wireless connection

---

### Post by bkratz on 2013-01-10
> **tibor834 said:**
> Thanks -- power management is now off using wlan1, but still no improvement in terms of the wireless connection



At the moment I can't think of anything else, but in the meantime have you tried dropping to wireless G mode with no security or WPA2 mode only but not mixed (you know wpa/wpa2 ) mode on the wireless A/P. Sometimes these help to at least find out if their is some other problem.  Will continue to look though.

---

### Post by bkratz on 2013-01-10
Found this with google

Check to see if you have the module acer-wmi loaded with

lsmod

if so see this page

[http://askubuntu.com/questions/224619/how-to-resolve-wireless-disconnect-problem-in-atheros-ath9k](http://askubuntu.com/questions/224619/how-to-resolve-wireless-disconnect-problem-in-atheros-ath9k)

---

