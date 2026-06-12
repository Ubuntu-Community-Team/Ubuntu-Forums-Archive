---
title: "Why isn't Linux finding my wireless network?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by groudyogre on 2008-08-15
I got a RT2500 wifi card because it seems pretty hassle-free.

I installed it fine and booted into Ubuntu Hardy.

Then i tried to search/connect to my wireless network that i used when I had windows.

:(

Not there. Doesn't connect to anything.

So i boot back into windows and install the Wifi card in XP and it works fine...



I can post the outputs of iwconfig and ifconfig if that would help :)

---

### Post by ajmorris on 2008-08-15
> **groudyogre said:**
> I got a RT2500 wifi card because it seems pretty hassle-free.

I installed it fine and booted into Ubuntu Hardy.

Then i tried to search/connect to my wireless network that i used when I had windows.

:(

Not there. Doesn't connect to anything.

So i boot back into windows and install the Wifi card in XP and it works fine...



I can post the outputs of iwconfig and ifconfig if that would help :)

hi there,
so a network interface is displayed in iwconfig is it?
Also, does ```
sudo iwlist scanning
``` reveal anything when you are in range of the access point you want to connect to?

AJ

---

### Post by groudyogre on 2008-08-15
```
**Output of iwconfig**

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[B]
Output of ifconfig:[/B]

eth0      Link encap:Ethernet  HWaddr 00:19:db:29:f2:c7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2062 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2062 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:103100 (100.6 KB)  TX bytes:103100 (100.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:1f:01:8c:7d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-1F-01-8C-7D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

[B]
Output of iwlist scanning[/B]

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:17:3F:7C:89:8B
                    ESSID:"MSN-MACH-2000"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/100  Signal level=-82 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000003e34b71c79

```




Thanks for helping :p

---

### Post by groudyogre on 2008-08-15
By the way, "MSN-MACH-2000" is not my wireless network :P

Mine is called "Wilkinson Home" ¬_¬

---

### Post by gandalf2000 on 2008-08-15
You don't have it hidden do you?  I have mine hidden and a scan won't pick it up unless I tell it the name and password.  There is a very good tutorial for cards with Broadcom chips, I'll see if I can find it and post it here.

---

### Post by ingeva on 2008-08-15
> **groudyogre said:**
> By the way, "MSN-MACH-2000" is not my wireless network :P

Mine is called "Wilkinson Home" ¬_¬

Run the NetWorkManager which is a very easy program to use.
Configure your network manually and see if it connects.

If looks like you have no cable connected, which is fine because
I have never made a WiFi connect with an active wired connection.

If you don't find the NetworkManager on the Panel, open a
terminal window and type "gksudo NetworkManager".

---

### Post by groudyogre on 2008-08-15
> **gandalf2000 said:**
> You don't have it hidden do you?  I have mine hidden and a scan won't pick it up unless I tell it the name and password.  There is a very good tutorial for cards with Broadcom chips, I'll see if I can find it and post it here.

Nah, there is no encryption on my router. I know cause my mobile can still connect to it with no password...

I'll try some of the stuff people mentioned, thanks.

---

### Post by ooobuntooo on 2008-08-15
Try cold-booting. Shutdown the computer from Windows and then turn it back on and boot into Linux. Without restarting.

It worked for me!

---

### Post by groudyogre on 2008-08-15
K... None of that worked... Network manager did nothing and i still cant see my network on the list.. :(

---

### Post by groudyogre on 2008-08-15
K, i'll try that one, but, i did cold boot to start with and that didnt do anything.

---

### Post by durand on 2008-08-15
Would there be a way to manually type in the SSID and stuff into Network Manager? You can get that by going into windows and it should say it somewhere in its networking settings...

Sorry for being a bit vague here but I don't have a wifi card..

---

### Post by ingeva on 2008-08-15
> **durand said:**
> Would there be a way to manually type in the SSID and stuff into Network Manager? You can get that by going into windows and it should say it somewhere in its networking settings...

Sorry for being a bit vague here but I don't have a wifi card..

Yes, you're quite right. There is, but if he still can't see the card the problem lies deeper.
Not all WiFi cards have Linux drivers. To use the Windows drivers a program called ndiswrapper is used. I don't have time to check if this has been mentioned before in this thread, but if not make a search for it.

---

### Post by durand on 2008-08-15
Well, I think it is scanning for wifi networks fine as in #3 so it must be working...

---

### Post by groudyogre on 2008-08-15
Okay so now I've written everything down shall I just type it all in in the manual connection manager and see if it works?

Also, it's not a driver problem because this card is built specifically to be plug & play with Hardy 8.04...

---

### Post by durand on 2008-08-15
Yes and hope that it works.

---

### Post by halitech on 2008-08-15
try the steps in this thread for the unencrypted section since you say you don't have any passwords

[http://ubuntuforums.org/showthread.php?t=571188&highlight=manual+wireless](http://ubuntuforums.org/showthread.php?t=571188&highlight=manual+wireless)

---

### Post by groudyogre on 2008-08-15
Lmao, I did it manually and got a big fat fail. It's still not detecting my wireless network i Linux, even though I know its in range etc. I'm using the same wifi card in XP now and it fine ¬_¬

---

### Post by halitech on 2008-08-15
did you try the steps in the thread I suggested?

---

### Post by groudyogre on 2008-08-15
> **halitech said:**
> did you try the steps in the thread I suggested?

Yeah I followed the steps. No results though. My card is still only detecting every other wireless network apart from my own.:(

---

### Post by tangibleorange on 2008-08-15
how far away are you from the router? is the connection weak in XP? it's possible that the linux driver is simply not capable of connecting to networks as far away as your one...

---

### Post by groudyogre on 2008-08-15
> **tangibleorange said:**
> how far away are you from the router? is the connection weak in XP? it's possible that the linux driver is simply not capable of connecting to networks as far away as your one...

Okay that is possible although it could cause problems if thats the case... Looks like its a trip downstairs for me:sad:

---

### Post by tangibleorange on 2008-08-15
sorry mate! if you're desperate, you could take a look at installing ndiswrapper - it might have a longer range. there is a very good guide about it here:
[http://ubuntuforums.org/showthread.php?t=564419]("http://ubuntuforums.org/showthread.php?t=564419")
for the RT2500 series (I used it to get my RT2561 working!) you can use your windows driver as the ndiswrapper one.

---

### Post by groudyogre on 2008-08-15
Okay so I've taken my pc to my router and plugged it it, which works, so now im downloading ndiswrapper to see if i can switch the drivers...

---

### Post by groudyogre on 2008-08-15
I think I'm going to cry. Nothing I'm doing is working, I'm followin all the tutorials I can find. None work.

I think I might format my Linux Partition and start again... There's nothing on it yet anyway...

---

### Post by Vadi on 2008-08-15
I have a similar card as you. In 8.04, you do need to use ndiswrapper to get wireless, but in 8.10 (which will be out in october) it works fine.

So ndiswrapper is the way to go atm.

---

### Post by ingeva on 2008-08-15
> **groudyogre said:**
> I think I'm going to cry. Nothing I'm doing is working, I'm followin all the tutorials I can find. None work.

I think I might format my Linux Partition and start again... There's nothing on it yet anyway...

I think that's not a bad idea. Just make sure that you do NOT have a cable connection to the Internet or router when you start the new system.
When I tried that, it wouldn't connect using the wireless.

I also recomment that you make an install command file so you can install all packages without having to use the Package Manager every time. After all it's a repetitive process, and by makeing notes of everything you install releives you of the job to remember all the details.

Here's a piece of my install file:

```
#! /bin/bash
# Needs to be called with "sudo bash installs"

#Remove orca
apt-get purge gnome-orca

# Hosts file
cp /home/Ubackup/etc/my.hosts /etc/hosts

#ntp
apt-get install ntp ntpdate

#epiphany browser
apt-get install epiphany-browser epiphany-browser-data epiphany-gecko epiphany-gobject0

#thunderbird
apt-get install mozilla-thunderbird thunderbird-locale-en-gb

#Sun Java
apt-get install sun-java-jre sun-java6-bin sun-java6-plugin

#php5 and apache2
apt-get install libapache2-mod-php5 php5-common php5
apt-get install libmysqlclient15off mysql-common
apt-get install apache2 apache2.2-common apache2-mpm-prefork apache2-utils

#samba
apt-get install samba samba-common
cp /home/Ubackup/etc/samba/my.smb.conf /etc/samba/smb.conf


```

etc.
Hope you understand that. Maybe you can do something similar.

---

### Post by groudyogre on 2008-08-15
Ok so i did a system reset and it still doesnt work. I'll try one more time to follow the guide and then I'll just wait until 8.10 comes out if it still wont work.

---

### Post by tangibleorange on 2008-08-15
> **groudyogre said:**
> Ok so i did a system reset and it still doesnt work. I'll try one more time to follow the guide and then I'll just wait until 8.10 comes out if it still wont work.

wait the RT2500 is a USB one right? is it ASUS by any chance?

---

### Post by groudyogre on 2008-08-15
> **tangibleorange said:**
> wait the RT2500 is a USB one right? is it ASUS by any chance?

Nope, its the PCI card :( It's by Edimax...

---

### Post by Gone fishing on 2008-08-15
I use a rt2500 pci card (Gigabyte) and have no problems, I think its worked since Breezy - I have to say that I usually the manual setup works better than roaming.

---

### Post by Kadrus on 2008-08-15
```
iwconfig wlan0 essid XXX key XXX
```
```
ifconfig wlan0 up
```
```
dhcpcd wlan0
```
try this,it might work.

---

