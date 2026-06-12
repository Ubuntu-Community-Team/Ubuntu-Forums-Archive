---
title: "wireless not working- help is greatly appreciated"
date: 2012-08-29
forum: New to Ubuntu
---

### Post by skeeter123 on 2012-08-29
Hello newbie here - i am running dual xp and ubuntu 12.04. my wireless  is not working. i have ethernet. tried to resolve by reading this forum  but am lost. see below info i thought might be helpful if someone is  kind enough.

14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 6400 [1028:01af]
    Kernel driver in use: b44
--
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge
steve@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 048d:1167 Integrated Technology Express, Inc. 
steve@ubuntu:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:eek:ff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:n
          
eth0      no wireless extensions.

steve@ubuntu:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by Finnicella on 2012-08-29
You have your wireless card blocked.
Try with this command:
```
sudo rfkill unblock all
```
If it doesn't work try with:
```
sudo rfkill unblock 0
```
Then give the command:
```
sudo rfkill list all
```
so we can see if the blocks have been removed.
Bye
Finny

---

### Post by irv on 2012-08-29
You have the same card I have the Broadcom Corporation BCM4311.
Make sure you have dkms installed.
```
sudo apt-get install dkms
```
Then follow everything in post #25 at this link.
[http://ubuntuforums.org/showthread.php?t=1742147&page=3]("http://ubuntuforums.org/showthread.php?t=1742147&page=3")

---

### Post by skeeter123 on 2012-08-29
steve@ubuntu:~$ sudo rfkill unblock all
steve@ubuntu:~$ sudo rfkill unblock 0
steve@ubuntu:~$ sudo rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by skeeter123 on 2012-08-29
did everything in #25 and rebooted. it shows wireless now but under the network tab it is showing unavailable and it won't turn on. I have my ethernet connection still.

any ideas?

---

### Post by Finnicella on 2012-08-29
Did you try to leave the swith of the wifi turned on in windows and then see if it works in Ubuntu? 
Otherwise try the command in my post again.
Bye

---

### Post by skeeter123 on 2012-08-29
i am using a dell inspiron 6400. it does not have a switch to turn wifi on or off like the newer laptops. Here is what i am getting. I appreciate your help.

steve@ubuntu:~$ sudo rfkill unblock all
[sudo] password for steve: 
steve@ubuntu:~$ sudo rfkill unblock 0
steve@ubuntu:~$ sudo rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by skeeter123 on 2012-08-29
well just typed in

rfkill list

and it unblocked everything. wifi up and running. not sure what i did i just hope i don't have to do this again upon restart.

Thanks for everyone's help. Any good recommendations on must have software on ubuntu?

---

### Post by kurt18947 on 2012-08-29
Did you unplug the ethernet cable when you rebooted?  Some WiFi adapters won't work if there's an ethernet connection present.

---

### Post by Finnicella on 2012-08-29
I recommend you for video VLC and for the graphic part GIMP.
For the audio editing I use Audacity and whatelse.
Bye
Finny

---

### Post by dj5and on 2012-09-04
Unplugging ethernet did the job for me, i.e. an ethernet connection kills wlan. (Found it a two years old post). Network-Manager shows "wireless disabled by hardware switch". Should be more detailed info. There are a lot of posts about it. Would be handy if one can configure this "feature" in general or as per wired network connection.

---

### Post by ramsharan065 on 2012-09-05
open system setting
click network option in hardware
click wireless
make wireless on by clicking on right side (off)
click on network name dropdown 
select other
give network name you want to connect for eg TP-LINK_AAB61C
select the wireless security
give the password
then click connect

---

### Post by anewguy on 2012-09-05
> **Finnicella said:**
> I recommend you for video VLC and for the graphic part GIMP.
For the audio editing I use Audacity and whatelse.
Bye
Finny

Are you posting in the correct thread????  This appears to have nothing to do with the subject of THIS thread.

---

