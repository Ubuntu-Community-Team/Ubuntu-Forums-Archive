---
title: "WiFi problem (realtek 8187b)"
date: 2009-06-23
forum: Philippine Team
---

### Post by Lila_IT_CMU on 2009-06-23
I still can't connect to Wifi...please help...
the problem is the network app will display "Connection Established" but no internet...

How to use the ndiswrapper? i have ndiswrapper but i have not installed it

---

### Post by loell on 2009-06-23
from [http://ubuntuforums.org/showthread.php?t=633446&page=2]("http://ubuntuforums.org/showthread.php?t=633446&page=2")

> 
This notebook contains the Realtek 8187b chipset. Crappy. NDISWRAPPER was the solution for me, sort of.

basic steps i took to get it working:

1.) disable wifi using hotkey (fn+F2).
2.) download latest NDISWRAPPER from repository
3.) download realtek 8187 drivers from realtek's site, or simply do
"wget ftp://202.65.194.212/cn/wlan/RTL8187B_driver_only.zip"
4.) extracted zip file
5.) opened terminal, changed to folder containing WinME driver (in this case it was /home/clay/Desktop/rtl8187b/WinME)
6.) input the following:
sudo ndiswrapper -i net8187b.inf
sudo ndiswrapper -m
sudo ndiswrapper -ma
sudo ndiswrapper -mi

7.) enable wifi using same hotkey sequence as step 1.
8.) restart machine
9.) left click on network manager at the top of my screen, chose manual configuration.
10.) selected wireless network adapter and clicked properties.
11.) uncheck "enable roaming"
12.) entered ESSID manually
13.) chose DHCP from drop down list in second section of window and click ok.
14.) you should see a little window pop up with a pretty flashing scrollbar that says "changing network adapter."

once that window disappeared, i was able to browse the web wirelessly. took me a month to figure out disabling the adapter upon using ndiswrapper, then configuring my network setup manually does the trick. pain in the *** if you travel a lot, but the good news is if you have it set to "enable roaming" it will find any access points around you, it just won't obtain an IP address from them for you automatically. Realtek is usually pretty good about releasing wireless drivers for linux for their products, but they are really lagging on this one.



---

### Post by prshah on 2009-06-23
> **Lila_IT_CMU said:**
> 
the problem is the network app will display "Connection Established" but no internet...

How to use the ndiswrapper? i have ndiswrapper but i have not installed it

If you are getting "Connection Established" then you need not use ndiswrapper.

If you are able to connect but not browse, you need to check (among other things) IP/DNS settings: Enter the below commands from the terminal (Applications-Accessories-Terminal) and post back the results here.
```

ifconfig
iwconfig
cat /etc/resolv.conf
ping 208.67.219.231 #google
ping www.google.com

```

---

### Post by Lila_IT_CMU on 2009-06-23
i have installed ndiswrapper on my previous ubuntu installtion but when i click on the network app in the upper right, there is no wireless connection. only wired... and it cannot detect any wireless network. (I just installed the inf file in my NEO Driver CD)
when i tried not to install ndiswrapper, as what I've said before, it can connect to the network but no internet. when i look at the  
network connection in the system>preferences> the transmission is  
fast but the received bytes is very very slow. is that the problem?? there is no problem when i used the wired connection   


by the way sir loell, where can i download the realtek 8187b driver?(the site)

salamat diay daan

---

### Post by loell on 2009-06-23
oh, it's  provided in the instruction on where to get the driver.

```
wget ftp://202.65.194.212/cn/wlan/RTL8187B_driver_only.zip
```

---

### Post by prshah on 2009-06-24
> **Lila_IT_CMU said:**
> i have installed ndiswrapper on my previous ubuntu installtion but when i click on the network app in the upper right, there is no wireless connection. only wired

I suggest that you are wasting your time with ndiswrapper in this case. From Ibex onwards the rtl8187 driver works better than the windows ndiswrapper'ed drivers.

The usual scenario of using ndiswrapper when the alternate rtl8187 driver present is that wireless disappears altogether.

If you want to still persist in using ndiswrapper (which, in my opinion, is a misguided attempt) then you need to first blacklist the rtl8187 driver. To do this, edit (or create) the file /etc/modprobe.d/blacklist (blacklist.conf if you are using Jaunty and above) and add a line to the end ```
blacklist rtl8187
```

Again, this is ill-advised. Attempting this will allow ndiswrapper to load and connect, but you will not be able to connect to WPA/WPA2 networks (At least, I have not been able to do so in my experience, neither from the command line, nor with NetworkManager).

Even in the case of an unsecured/WEP network, you may be able to "connect" but not use the wireless network, ie, browse,etc.

Feel free to try; but don't be surprised if it does not work.

---

### Post by loell on 2009-06-24
Wow, do I sense a little too much of assertion!?  

anyway, this might provide more info ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/293946](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/293946)).

and could help on whether the OP should use ndiswrapper or the native driver. actually any of the two that would work for the OP, would be great.

---

### Post by Lila_IT_CMU on 2009-06-24
prshah, heres my ifconfig, iwconfig, etc

lila@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:f5:8a:09:3c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5200 (5.2 KB)  TX bytes:5200 (5.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:d5:df:1c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-D5-DF-1C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lila@ubuntu:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

pan0      no wireless extensions.

lila@ubuntu:~$ cat /etc/resolv.conf
# Generated by NetworkManager
lila@ubuntu:~$ ping 208.67.219.231 #google
connect: Network is unreachable
lila@ubuntu:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
lila@ubuntu:~$

---

### Post by prshah on 2009-06-24
> **Lila_IT_CMU said:**
> 
lila@ubuntu:~$ cat /etc/resolv.conf
# Generated by NetworkManager
lila@ubuntu:~$ ping 208.67.219.231 #google
connect: Network is unreachable
lila@ubuntu:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
lila@ubuntu:~$

Please connect to your wireless network and repeat the above commands. (..network app will display "Connection Established"..)

Are you unable to connect to your wireless network? In that case, please issue this command and post the output ```
sudo iwlist wlan0 scan
lsmod | grep ieee
```

---

### Post by Lila_IT_CMU on 2009-06-24
ok ... I will try



thanks

---

### Post by julioipn on 2009-07-07
how about the original driver???
it works wonders with my netbook
[http://ubuntuforums.org/showthread.php?t=1065698](http://ubuntuforums.org/showthread.php?t=1065698)

---

### Post by gamels on 2009-07-07
any english conversion for that link? seems i dont understand...

---

### Post by julioipn on 2009-08-02
ok, sorry, here is in english, I have a netbook with realtek rtl8187b usb wireless card, as everybody else, when I tried to browse any page I couldn't , network app message was "conection established", however, nothing seemed to work, I tried several methods in order to make the card work, and what worked wonders to me was the original driver,  in realtek web page it is not available, anyway, I sent an email asking for the driver and they responded me with the driver, I just follow the instructions and have no problems any more, basically, you just have to "untar" the file, browse to the new directory and use this commands:

make

and then:

sudo make install

then you just reboot and that's all

hope this is usefull

PS:
sorry about the english if there is someting wrong

BTW, this is the email adress i wrote to: [email]wlanfae@realtek.com[/email]

---

### Post by indra163 on 2009-08-14
wget [ftp://202.65.194.212/cn/wlan/RTL8187B_driver_only.zip](ftp://202.65.194.212/cn/wlan/RTL8187B_driver_only.zip)

hai, i can't login in here...
what is username and password??
and i can't connect.
just can search the wifi and can't connect.
why and can you help me all??

---

### Post by Lila_IT_CMU on 2009-08-15
> **indra163 said:**
> wget [ftp://202.65.194.212/cn/wlan/RTL8187B_driver_only.zip](ftp://202.65.194.212/cn/wlan/RTL8187B_driver_only.zip)

hai, i can't login in here...
what is username and password??
and i can't connect.
just can search the wifi and can't connect.
why and can you help me all??



dont use that link

you can download the driver here

[http://burnthesorbonne.com/files/rtl8187B_linux_26.1052.0225.2009.release.tar.gz]("http://burnthesorbonne.com/files/rtl8187B_linux_26.1052.0225.2009.release.tar.gz")

---

### Post by perbiu on 2009-08-15
That's funny, my wireless realtek 8187b also cannot browse the internet even though it has connected to the router. But i can access the other computers(2) and laptop(3) along that network, i can even move files from pc to laptop.

---

### Post by perbiu on 2009-08-16
**[SOLVED]**
As of speaking, i am using the realtek 8187b wireless of my neo laptop. Thanks to the people here.

For documentation purpose i'll repost some steps our users did cleary, also as confirmation that it works:

Download the original driver and save it to your home folder:
[http://burnthesorbonne.com/files/rtl8187B_linux_26.1052.0225.2009.release.tar.gz](http://burnthesorbonne.com/files/rtl8187B_linux_26.1052.0225.2009.release.tar.gz)

Open terminal and go to where the downloaded file is (in this case your home folder, but by default when you open the terminal you are at your home folder)
then copy & paste the bolded lines:
**tar xvzf rtl8187B_linux_26.1052.0225.2009.release.tar.gz**
(this will uncompress the file)

**cd rtl8187B_linux_26.1052.0225.2009.release**
(you will go to the uncompressed file's folder)

**sudo make**

**sudo make install**

Then restart.
You will also noticed that the wlan0 will now be wlan1

---

### Post by d45h on 2009-08-19
> **perbiu said:**
> **[SOLVED]**
As of speaking, i am using the realtek 8187b wireless of my neo laptop. Thanks to the people here.

For documentation purpose i'll repost some steps our users did cleary, also as confirmation that it works:

Download the original driver and save it to your home folder:
[http://burnthesorbonne.com/files/rtl8187B_linux_26.1052.0225.2009.release.tar.gz](http://burnthesorbonne.com/files/rtl8187B_linux_26.1052.0225.2009.release.tar.gz)

Open terminal and go to where the downloaded file is (in this case your home folder, but by default when you open the terminal you are at your home folder)
then copy & paste the bolded lines:
**tar xvzf rtl8187B_linux_26.1052.0225.2009.release.tar.gz**
(this will uncompress the file)

**cd rtl8187B_linux_26.1052.0225.2009.release**
(you will go to the uncompressed file's folder)

**sudo make**

**sudo make install**

Then restart.
You will also noticed that the wlan0 will now be wlan1

i have downloaded and install that driver, it work for few minutes and after that i cant ping another node,,, fyi this problem only happen for ad-hoc connection...
help needed....

regard

---

### Post by mickeypop on 2009-08-27
A few years a go i was involved in developing a linux embeded Access Point.

That said my Dell Inspiron 6000 with Ubuntu 9.04 was having simular issues.  I remembered "**iwconfig**".  

RE;
Man page [http://linux.die.net/man/8/iwconfig]("http://linux.die.net/man/8/iwconfig")

The kernel often does not turn power on fully at boot so here you can change that.

At the end of the **rc.local** file (it is the last script exicuted at boot time) add this command to turn on max power to the WIFI card.

Double check what number your wireless uses eth1 might be eth0, if so adjust as called for.  Mine is eth1

[INDENT]**sudo vi /etc/rc.d/rc.local**
  add   **iwconfig eth1 power max**[/INDENT] 

On reboot the kernel will turn the card to max power.

If you need to save power occationally, you can open a terminal and turn it up or down as needed.

[INDENT]**sudo iwconfig eth1**
   This will display all settings of the wireless card.
   Look for the power setting, it will be in milliwatts(mW).[/INDENT] 

If say the power was set to 1000mW and you want half of that:

 [INDENT] **sudo iwconfig eth1 power 500m**[/INDENT]


Hope this helps some of you. 
M.

:):)

---

### Post by TraBruno on 2009-08-28
Hello,

I have the same wireless card and solved the same problem following instructions in this thread:
[http://ubuntuforums.org/showthread.php?p=7157415#post7157415](http://ubuntuforums.org/showthread.php?p=7157415#post7157415)

It has a link to a new driver for linux from Realtek. It worked splendidly for me, although a bit unstable at times. Following thread is mine, trying to solve the problem, if you would like to 
compare iwconfig outputs and other symptons.
[http://ubuntuforums.org/showthread.php?t=1250000&highlight=trabruno](http://ubuntuforums.org/showthread.php?t=1250000&highlight=trabruno)

Good luck!
TraBruno

---

### Post by WhoFlungChow on 2009-09-10
> **perbiu said:**
> **[SOLVED]**
As of speaking, i am using the realtek 8187b wireless of my neo laptop. Thanks to the people here.

For documentation purpose i'll repost some steps our users did cleary, also as confirmation that it works:

Download the original driver and save it to your home folder:
[http://burnthesorbonne.com/files/rtl8187B_linux_26.1052.0225.2009.release.tar.gz](http://burnthesorbonne.com/files/rtl8187B_linux_26.1052.0225.2009.release.tar.gz)

Open terminal and go to where the downloaded file is (in this case your home folder, but by default when you open the terminal you are at your home folder)
then copy & paste the bolded lines:
**tar xvzf rtl8187B_linux_26.1052.0225.2009.release.tar.gz**
(this will uncompress the file)

**cd rtl8187B_linux_26.1052.0225.2009.release**
(you will go to the uncompressed file's folder)

**sudo make**

**sudo make install**

Then restart.
You will also noticed that the wlan0 will now be wlan1

I bought a Toshiba L355-S7915 from Walmart.  I installed Ubuntu 9.04 and upon install it showed "connection established."  However, I was not able to surf the Internet.  I followed your advice and now I am.  

Does it matter that it's set at wlan1 instead of wlan0?  Also, the connection keeps timing out on me.  For example, a 10 minute YouTube video will only load part way and then it stops (sometimes a quarter, sometimes a third, and sometimes half of the video).  Similarly, when I'm DLing a 50mb file it will only DL for a few minutes and then it stops without picking back up.  Do any of you guys know why this is?  Thanks.

---

### Post by perbiu on 2009-09-10
Yes, its ok if its on wan1, its good because you know its working, since it will go back to wan0 and lose the internet connection again if you recieve update on a kernel level, so you have to do the installation again.

Is your signal strong? there could be several problems causing that, router signal distance/interference/obstruction, buggy firmware router, your isp or the youtube/download server is busy. Use a downloader software like an addon for firefox so it can be resumed when cut off when downloading large files.

---

### Post by eunuch on 2009-12-05
**Re: Realtek 8187b Driver Problems** 			
 			 			 		   		 		 		I read an article about the  RTL8187b  wireless chip set...

"You can choose to upgrade or install to this version in non stable release now. I can tell you that the RTL8187b WORKS OUT OF BOX!!!!"

[https://help.ubuntu.com/community/Wi...ealtekRTL8187b]("https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b")

I have a fresh installation of Ubuntu 9.10 (Karmic Koala?) and an USB device with the above chip set.

I don't know much about Linux internals - but, am I close to having it work?  (see below)

This is the syslog - any idea why it doesn't connect me?

It shows my removal and reconnection...

(This is an "out-of-the-box" set-up)

Dec  5 00:47:02 Ubuntu-desktop kernel: [  713.811733] usb 1-1: USB disconnect, address 2
Dec 5 00:47:02 Ubuntu-desktop NetworkManager: SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.2/usb1/1-1/1-1:1.0/net/wlan0, iface: wlan0)
Dec  5 00:47:02 Ubuntu-desktop NetworkManager: <info>  (wlan0): now unmanaged
Dec  5 00:47:02 Ubuntu-desktop NetworkManager: <info>  (wlan0): device state change: 3 -> 1 (reason 36)
Dec  5 00:47:02 Ubuntu-desktop NetworkManager: <info>  (wlan0): cleaning up...
Dec  5 00:47:02 Ubuntu-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Dec  5 00:47:02 Ubuntu-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Dec 5 00:47:02 Ubuntu-desktop NetworkManager: SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.2/usb1/1-1/1-1:1.0/net/wmaster0, iface: wmaster0)
Dec  5 00:47:02 Ubuntu-desktop wpa_supplicant[1150]: Failed to disable WPA in the driver.
Dec 5 00:47:02 Ubuntu-desktop NetworkManager: <info> Radio killswitch /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.2/usb1/1-1/1-1:1.0/ieee80211/phy0/rfkill0 disappeared
Dec  5 00:47:12 Ubuntu-desktop kernel: [  723.816020] usb 1-1: new high speed USB device using ehci_hcd and address 4
Dec  5 00:47:12 Ubuntu-desktop kernel: [  723.955777] usb 1-1: configuration #1 chosen from 1 choice
Dec  5 00:47:12 Ubuntu-desktop kernel: [  724.234548] phy1: Selected rate control algorithm 'minstrel'
Dec  5 00:47:12 Ubuntu-desktop kernel: [  724.235480] phy1: hwaddr 00:14:d1:5c:32:09, RTL8187BvE V0 + rtl8225z2
Dec 5 00:47:12 Ubuntu-desktop NetworkManager: <info> Found radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.2/usb1/1-1/1-1:1.0/ieee80211/phy1/rfkill1) (driver <unknown>)
Dec 5 00:47:12 Ubuntu-desktop NetworkManager: SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.2/usb1/1-1/1-1:1.0/net/wmaster0, iface: wmaster0)
Dec 5 00:47:12 Ubuntu-desktop NetworkManager: SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.2/usb1/1-1/1-1:1.0/net/wmaster0, iface: wmaster0): no ifupdown configuration found.
Dec 5 00:47:12 Ubuntu-desktop NetworkManager: SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.2/usb1/1-1/1-1:1.0/net/wlan0, iface: wlan0)
Dec 5 00:47:12 Ubuntu-desktop NetworkManager: SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.2/usb1/1-1/1-1:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Dec  5 00:47:12 Ubuntu-desktop NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Dec  5 00:47:12 Ubuntu-desktop NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'rtl8187')
Dec  5 00:47:12 Ubuntu-desktop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/2
Dec  5 00:47:12 Ubuntu-desktop NetworkManager: <info>  (wlan0): now managed
Dec  5 00:47:12 Ubuntu-desktop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Dec  5 00:47:12 Ubuntu-desktop NetworkManager: <info>  (wlan0): bringing up device.
Dec  5 00:47:12 Ubuntu-desktop kernel: [  724.303426] rtl8187: Customer ID is 0x00
Dec  5 00:47:12 Ubuntu-desktop kernel: [  724.303497] Registered led device: rtl8187-phy1::tx
Dec  5 00:47:12 Ubuntu-desktop kernel: [  724.303522] Registered led device: rtl8187-phy1::rx
Dec  5 00:47:16 Ubuntu-desktop kernel: [  728.086319] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec  5 00:47:16 Ubuntu-desktop NetworkManager: <info>  (wlan0): preparing device.
Dec  5 00:47:16 Ubuntu-desktop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Dec  5 00:47:16 Ubuntu-desktop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Dec  5 00:47:16 Ubuntu-desktop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Dec  5 00:47:19 Ubuntu-desktop wpa_supplicant[1150]: CTRL-EVENT-SCAN-RESULTS 
Dec  5 00:47:24 Ubuntu-desktop wpa_supplicant[1150]: CTRL-EVENT-SCAN-RESULTS 
Dec  5 00:47:44 Ubuntu-desktop wpa_supplicant[1150]: CTRL-EVENT-SCAN-RESULTS 
Dec  5 00:48:14 Ubuntu-desktop wpa_supplicant[1150]: CTRL-EVENT-SCAN-RESULTS 

Thanks,
 		                   		  		  		  		  		  	   	 		[IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]   		 		 		 		 		  	 	 	 	 		  		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=8445342")

---

