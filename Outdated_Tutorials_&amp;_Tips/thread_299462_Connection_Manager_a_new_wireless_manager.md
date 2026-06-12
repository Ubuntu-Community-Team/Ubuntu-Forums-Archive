---
title: "Connection Manager: a new wireless manager"
date: 2006-11-14
forum: Outdated Tutorials &amp; Tips
---

### Post by compwiz18 on 2006-11-14
[SIZE="6"][B]Connection Manager is now wicd.

See [[COLOR="Blue"]_http://wicd.net_[/COLOR]]("http://wicd.net") for more details and downloads, as well as features and forums for troubleshooting.[/B][/SIZE]

[SIZE="5"]A quick summary: support for wireless and wired networks, with individual settings for each network, autoconnect at boot, tray icons.  See [COLOR="Blue"]_[http://wicd.net/features.php](http://wicd.net/features.php)_[/COLOR] for a more complete list.[/SIZE]

We decided to move everything to the wicd website, so that we will have a single place for all communications regarding wicd.

I will leave the older info up for reference.

[COLOR="Silver"]
[SIZE="5"]Connection Manager[/SIZE]

[COLOR="DarkOrange"][SIZE="5"]Features[/SIZE][/COLOR]
[LIST]
[*]**[COLOR="Red"]New![/COLOR]** - Ability to configure wired networks with DHCP...the ability to use static IPs will come soon
[*]**[COLOR="Red"]New![/COLOR]** - Only for Edgy: System tray applet, displays signal strength - works in any window manager
[*]Connect to WPA 1&2 enabled networks using WPA supplicant automatically (see note below)
[*]Connect to WEP enabled networks
[*]Remembers network keys
[*]Ability to change the driver WPA supplicant uses
[*]Connect at boot (automatically, without entering password)
[*]Connect at resume from suspend
[*]View signal strengths (works with ndiswrapper too)
[*]Sorts networks in strength order, with strongest at the top
[*]Allow you to set and change the interface used
[*]Use network profiles...
[*]Have different static or dynamic IP settings for each network you connect to
[*]Specify static DNS servers for each network
[*]Choose whether to connect automatically on a per-network basis
[/LIST]

[COLOR="DarkOrange"][SIZE="5"]Screenshots[/SIZE][/COLOR]
[LIST]
[*][Main Window]("http://compwiz18.blackhole.cx/connection-manager/get.php?file=screenshot1.png")
[*][Network Preference Window]("http://compwiz18.blackhole.cx/connection-manager/get.php?file=screenshot2.png")
[/LIST]

[COLOR="DarkOrange"][SIZE="5"]Download[/SIZE][/COLOR]
This .deb contains only Connection Manager, it does NOT contain the systray app.  For that, please scroll down.

After you installation, a menu item will be in Applications / Internet / Connection Manager.

[SIZE="3"][**Download (.deb)**]("http://ubuntuforums.org/attachment.php?attachmentid=21071&stc=1&d=1166161595")[/SIZE]

[COLOR="DarkOrange"][SIZE="5"]Systray Download - For Edgy Only[/SIZE][/COLOR]
**[COLOR="Red"][COLOR="Red"]THE SYSTEM TRAY ICON MUST BE ENABLED BEFORE IT WILL APPEAR![/COLOR][/COLOR]**

This can be done by adding it to your window manager's session

in [COLOR="Blue"]GNOME[/COLOR]: go to System -> Preferences -> Sessions, and clicking Startup Programs, and adding *connection-manager-systray*
in [COLOR="Blue"]KDE[/COLOR]: create a symlink of /opt/connection-manager/systray in this folder: ~/.kde/autostart/

Everyone else: figure it out for yourself, and then post directions on this thread, and I'll add them here.

[SIZE="3"][**Download (.deb)**]("http://ubuntuforums.org/attachment.php?attachmentid=21072&stc=1&d=1166161595")[/SIZE]

[COLOR="DarkOrange"][SIZE="5"]Notes[/SIZE][/COLOR]

[SIZE="4"]WPA[/SIZE]
Most WPA networks will work easily with Connection Manager, but some may require additional work.  If you WPA network does not work with the default Connection Manager settings, edit /opt/connection-manager/data/wpa_supplicant.conf using normal wpa_supplicant syntax (see **man wpa_supplicant.conf** for more info).  This is the configuration file Connection Manager will use to launch wpa_supplicant.  If you need help, you can look at this tutorial: [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

[SIZE="4"]Updates[/SIZE]
The entire program will be updated constantly, so check back every once in a while for new updates.

Upcoming features:
[LIST]
[*]ability to connect to hidden networks
[/LIST]

[COLOR="DarkOrange"][SIZE="5"]Versions[/SIZE][/COLOR]

Current status: **Beta**
Current version: 1.3.2 (Bug fix)

All versions are on the server - if you want an old version, substitute the version number of the one you want with **version-number** in the link below.

```
http://compwiz18.blackhole.cx/connection-manager/get.php?file=connection-manager-**version-number**.deb
```

History:
1.3.1 - Bug fix
1.3.0 - Feature and bug fix
1.2.2 - Bug fix
1.2.1 - Bug fix
1.2.0 - Feature and bug fix
1.1.2 - Bug fix
1.1.1 - Bug fix
1.1.0 - Feature and bug fix
1.0.8 - Bug fix - [click here for download]("http://ubuntuforums.org/attachment.php?attachmentid=19527&d=1163755011")
1.0.7 - Bug fix
1.0.6 - Bug fix
1.0.5 - Bug fix
1.0.4 - Bug fix
1.0.3 - Bug fix
1.0.2 - Bug fix
1.0.1 - Bug fix
1.0.0 - Original release[/COLOR]

---

### Post by alchimera on 2006-11-14
I tried it...

(i) had to remove wi-fi radar + network-manager; used GDebi Package Installer; then

(ii) the panels on my desktop stopped working, nor would <alt>+<F2> give me a run dialog... so restarted gdm with <ctrl>+<alt>+<backspace> to find a dialog about "a panel is already open" and click ok to close when there were no panels!  [just like one of those happy helpful Windows balloons!!!] 
Had to go to tty1 and reboot the system.

(iii) came back up ok, everything working: wifi is up and running, and "Connection Manager" now appears in the Applications\Internet menu but *n*othing happens when i try to start it - either from the menu or the run dialog. System\Administration\Networking  appears to be unchanged, but i haven't tried to use it to do anything yet.

---

### Post by compwiz18 on 2006-11-14
> **alchimera said:**
> I tried it...

(i) had to remove wi-fi radar + network-manager; used GDebi Package Installer; then

(ii) the *panels on my desktop stopped working*, nor would <alt>+<F2> give me a run dialog... so restarted gdm with <ctrl>+<alt>+<backspace> to find a dialog about "a panel is already open" and click ok to close when *there were no panels*!  [just like one of those happy helpful Windows balloons!!!] 
Had to go to tty1 and reboot the system.

(iii) came back up ok, everything working: wifi is up and running, and "Connection Manager" now appears in the Applications\Internet menu but *nothing happens when i try to start it* - either from the menu or the run dialog. System\Administration\Networking  appears to be unchanged, but i haven't tried to use it to do anything yet.

Figure my next step is to remove the package and return the system to it's former state, is no good having something on board that won't talk to me!
Could you run it from a terminal by using the command **sudo /opt/connection-manager/manager** if you haven't uninstalled it already?  I'd be interesting in seeing the output.

---

### Post by wolfpakz on 2006-11-14
I setup connection-manager on my machine and initially I had the same problem described by alchimera. When I ran /opt/connection-manager/manager I got the following output:
Traceback (most recent call last):
  File "./manager", line 3, in ?
    import networking, ConfigParser, wx, math, threading, time, sys, thread, os, tempfile
ImportError: No module named wx


I figured the python module for wx wasn't installed, and after installing it, connection-manager does come up. At this point though it just sits there scanning. If I run manager from the cli I see this:

Traceback (most recent call last):
  File "./manager", line 522, in ?
    frame = Main(None)
  File "./manager", line 70, in __init__
    self.UpdateNetworkList()
  File "./manager", line 154, in UpdateNetworkList
    self.scan_data = self.wifi.scan()
  File "/opt/connection-manager/networking.py", line 44, in scan
    aps[ i ]['channel'] = channel
UnboundLocalError: local variable 'channel' referenced before assignment

I'm definitely interested in seeing if this will work. Get back to me and I'll be happy to guinea pig for you.

-WolfpakZ

---

### Post by wolfpakz on 2006-11-14
I noticed the package installed some init scripts, so I tried a reboot to see if that would help. No luck there.

I investigated the last traceback I posted, and it looks like running the command `iwlist wlan0 scan` is expecting an output it's not getting. When I run this I only get the output "wlan0     No scan results".

I'm getting the feeling my wireless setup isn't working. Actually that's part of what drew me to connection-manager in the first place. Anyhow, I'll see if I can work through getting my wireless setup working and check back when it's working.

-WolfpakZ

---

### Post by desmondo on 2006-11-14
Sounds nice, but any reason why you made a new application, rather than help fix NetworkManager?

Just curious.

---

### Post by wolfpakz on 2006-11-14
Okay, my wireless setup is fixed and working.

Going back to connection-manager, I'm still getting the python error regarding the 'channel' var. I tweak the regexp a bit to be capable of matching my iwlist output. I also had to change the hardcoded network device from wlan0 to ra0 in a couple of places. The regexp for signal strength wasn't working either. It generated the same error as 'channel'. So I hard coded the signal strength to '5', and that seems to have worked.

At this point I'm able to successfully configure my network and connect to it.

-WolfpakZ

---

### Post by compwiz18 on 2006-11-15
> **wolfpakz said:**
> Okay, my wireless setup is fixed and working.

Going back to connection-manager, I'm still getting the python error regarding the 'channel' var. I tweak the regexp a bit to be capable of matching my iwlist output. I also had to change the hardcoded network device from wlan0 to ra0 in a couple of places. The regexp for signal strength wasn't working either. It generated the same error as 'channel'. So I hard coded the signal strength to '5', and that seems to have worked.

At this point I'm able to successfully configure my network and connect to it.

-WolfpakZ
Could you post the regex you used?  I'll change the main package.

And also, could you tell me how you fixed the "no wx module found" error?  I'll edit the .deb dependencies to include the need library.

---

### Post by wolfpakz on 2006-11-15
> **compwiz18 said:**
> Could you post the regex you used?  I'll change the main package.

And also, could you tell me how you fixed the "no wx module found" error?  I'll edit the .deb dependencies to include the need library.

I first had to install the libwxgtk2.6-0 package before I could actually install connection-manager, then to fix the "no wx module found" error, I installed the python-wxgtk2.6 package.

Here's the regexp I used to fix the channel error: ```
'.*Channel:(.*?)\n'
```

-WolfpakZ

---

### Post by alchimera on 2006-11-15
> **compwiz18 said:**
> Could you run it from a terminal by using the command **sudo /opt/connection-manager/manager** if you haven't uninstalled it already?  I'd be interesting in seeing the output.

This is the output:
Traceback (most recent call last):
  File "/opt/connection-manager/manager", line 3, in ?
    import networking, ConfigParser, wx, math, threading, time, sys, thread, os, tempfile
ImportError: No module named wx

After reading above posts, i checked to find libwxgtk2.6-0 already installed; installed python-wxgtk2.6 (&, neccessarily via synaptic, python-wxversion) and reinstalled your .deb...

...fired up connection-manager from the Applications\Internet menu: a "Python Warning" dialogue appeared with the following log file entry:
08:56:56: Mailcap file /etc/mailcap, line 67: incomplete entry ignored.
08:56:56: Mailcap file /etc/mailcap, line 68: incomplete entry ignored.
08:56:56: Mailcap file /etc/mailcap, line 113: incomplete entry ignored.
After pressing "OK", Connection Manager appeared stating "No Networks Found".

The output of  "sudo /opt/connection-manager/manager" is now:
wlan0     Interface doesn't support scanning.

Rebooting did not change this behaviour.

Decided to keep it onboard for a while, happy to help!

---

### Post by compwiz18 on 2006-11-15
> **alchimera said:**
> This is the output:
Traceback (most recent call last):
  File "/opt/connection-manager/manager", line 3, in ?
    import networking, ConfigParser, wx, math, threading, time, sys, thread, os, tempfile
ImportError: No module named wx

Decided to keep it onboard for a while, hope to help!
Try downloading the new version - I fixed that problem :D

---

### Post by alchimera on 2006-11-15
Sorry to get out of sequence, but i just edited my last post with the results of my tweaking!

---

### Post by compwiz18 on 2006-11-15
> **alchimera said:**
> Sorry to get out of sequence, but i just edited my last post with the results of my tweaking!
Yep, I saw.

Try downloading the new version, it should solve your problem.

---

### Post by compwiz18 on 2006-11-15
> **compwiz18 said:**
> Yep, I saw.

Try downloading the new version, it should solve your problem.
I uploaded yet another new version, this one should fix the "wlan0 interface not found" error.

---

### Post by alchimera on 2006-11-15
> **compwiz18 said:**
> I uploaded yet another new version, this one should fix the "wlan0 interface not found" error.
It does... it now hangs up with a "Scanning" dialog, which is unresponsive and have to force quit.

The output of
```
 sudo /opt/connection-manager/manager
```
is
lo        no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

Traceback (most recent call last):
  File "/opt/connection-manager/manager", line 541, in ?
    frame = Main(None)
  File "/opt/connection-manager/manager", line 89, in __init__
    self.UpdateNetworkList()
  File "/opt/connection-manager/manager", line 173, in UpdateNetworkList
    self.scan_data = self.wifi.scan(self.interface)
TypeError: scan() takes exactly 1 argument (2 given)

(i) same python warnings as before
(ii) my wireless is on eth1

---

### Post by compwiz18 on 2006-11-15
OK, I think I know what your problem is.  Try running **sudo rm /opt/connection-manager/network***  I think this should fix your problem...if it doesn't post, and tell me.

---

### Post by onlainari on 2006-11-15
Hi. I installed the deb (1.0.2), and the dependencies succesfully.

ville@ville-laptop:~/files$ sudo /opt/connection-manager/manager 
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.



lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

Traceback (most recent call last):
  File "/opt/connection-manager/manager", line 541, in ?
    frame = Main(None)
  File "/opt/connection-manager/manager", line 89, in __init__
    self.UpdateNetworkList()
  File "/opt/connection-manager/manager", line 173, in UpdateNetworkList
    self.scan_data = self.wifi.scan(self.interface)
  File "/usr/lib/python2.4/networking.py", line 46, in scan
    aps[ i ]['signal'] = strength
UnboundLocalError: local variable 'strength' referenced before assignment


Scanning window opens along with the main window. Cannot do anything, freezed windows.


If I run the app from the Applications network menu, I get a pop-up window saying: mailcapfile /etc/mailcap line 54 incomplete entry ignored. After I press OK, I get the freezed scanning and main window.

---

### Post by compwiz18 on 2006-11-15
> **onlainari said:**
> Hi. I installed the deb (1.0.2), and the dependencies succesfully.

ville@ville-laptop:~/files$ sudo /opt/connection-manager/manager 
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.



lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

Traceback (most recent call last):
  File "/opt/connection-manager/manager", line 541, in ?
    frame = Main(None)
  File "/opt/connection-manager/manager", line 89, in __init__
    self.UpdateNetworkList()
  File "/opt/connection-manager/manager", line 173, in UpdateNetworkList
    self.scan_data = self.wifi.scan(self.interface)
  File "/usr/lib/python2.4/networking.py", line 46, in scan
    aps[ i ]['signal'] = strength
UnboundLocalError: local variable 'strength' referenced before assignment


Scanning window opens along with the main window. Cannot do anything, freezed windows.


If I run the app from the Applications network menu, I get a pop-up window saying: mailcapfile /etc/mailcap line 54 incomplete entry ignored. After I press OK, I get the freezed scanning and main window.
OK, can you run **iwlist scan** and post the output?  I'll fix your problem for you.

---

### Post by alchimera on 2006-11-15
> **compwiz18 said:**
> OK, I think I know what your problem is.  Try running **sudo rm /opt/connection-manager/network***  I think this should fix your problem...if it doesn't post, and tell me.

Sorry to say, external behaviour is the same, but the output in termminal now reads:

Traceback (most recent call last):
  File "/opt/connection-manager/manager", line 541, in ?
    frame = Main(None)
  File "/opt/connection-manager/manager", line 89, in __init__
    self.UpdateNetworkList()
  File "/opt/connection-manager/manager", line 173, in UpdateNetworkList
    self.scan_data = self.wifi.scan(self.interface)
  File "/usr/lib/python2.4/networking.py", line 46, in scan
    aps[ i ]['signal'] = strength
UnboundLocalError: local variable 'strength' referenced before assignment

This is the output from **iwlist scan**:
eth0      Scan completed :
          Cell 01 - Address: 00:11:95:96:27:26
                    ESSID:"G604T_WIRELESS"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=70/100  Signal level=-58 dBm  
                    Extra: Last beacon: 3724ms ago

---

### Post by wieman01 on 2006-11-15
Guys, 

Just to say that this is an excellent initiative. Seeing all the wireless configuration tools around, this could be a good approach. Just bear in mind: Keep is simple.

I'll test the tool as soon as it reaches BETA. Keep going!

---

### Post by onlainari on 2006-11-15
ville@ville-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:90:CC:C3:24:8A
                    ESSID:"Gifu"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:7
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-49 dBm  
                    Extra: Last beacon: 76ms ago

sit0      Interface doesn't support scanning.


Here is what I have got some times earlier in dmesg (with wifi-radar) in case it helps: 

This one only 2 times, it feels advancement: 

[17179673.736000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179673.920000] ISOFS: changing to secondary root
[17179737.340000] SoftMAC: Authentication response received from 00:16:01:0c:ac:67 but no queue item exists.
[17179737.340000] SoftMAC: Authentication response received from 00:90:cc:c3:24:8a but no queue item exists.
[17179737.344000] SoftMAC: Authentication response received from 00:16:01:0c:ac:67 but no queue item exists.
[17179737.344000] SoftMAC: Authentication response received from 00:90:cc:c3:24:8a but no queue item exists.
[17179737.348000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17179748.512000] eth1: no IPv6 routers present


This one is more common: 

[17179767.748000] ieee80211_crypt: registered algorithm 'WEP'
[17179768.156000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179771.856000] SoftMAC: Open Authentication with 00:90:cc:c3:24:8a failed, error code: 13
[17179836.524000] ADDRCONF(NETDEV_UP): eth1: link is not ready

---

### Post by alchimera on 2006-11-15
Thanks for the encouragement wieman01; i've never participated in a thread before and am enjoying being able to help in some small way - giving and receiving are the breath of life, and Ubuntu has given me much!

---

### Post by wieman01 on 2006-11-15
> **alchimera said:**
> Thanks for the encouragement wieman01; i've never participated in a thread before and am enjoying being able to help in some small way - giving and receiving are the breath of life, and Ubuntu has given me much!
That's the spirit, mate. You are doing fine. If this works out, we will one step further. :-)

---

### Post by compwiz18 on 2006-11-15
OK, new version, should fix the signal strength errors.

---

### Post by 0MG on 2006-11-15
It's not finding my ra0 interface:

# /opt/connection-manager/manager
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

no wireless interface...


Any advice?

---

### Post by onlainari on 2006-11-16
Hi. Now with 1.0.3 the program starts, although with the "mailcap file /etc/mailcap line54 incomplete entry ignored" pops up first.  

I set up my network and try connect. There were few suspicious looking error msg. Probably this program would work now if I didn't have the IP getting problem. 

Here my output:

```
ville@ville-laptop:~/files$ sudo /opt/connection-manager/manager 
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.



lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

0
1
2
link clicked: py:preferences(0)
link clicked: py:preferences(0)
link clicked: py:connect(0)
{'encryption': 'on', 'signal': '-54', 'ap_mac': '00:90:CC:C3:24:8A', 'mode': 'Master', 'channel': '7', 'essid': 'Gifu'}
killing previous wpa supps
wpa_supplicant: no process killed
iwconfig  mode Master
Error : unrecognised wireless request "Master"
iwconfig  essid "Gifu" channel 7 key xxxxxxxxxx ap 00:90:CC:C3:24:8A
Error : unrecognised wireless request "Gifu"
configuring dhcp
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:16:01:0c:ac:53
Sending on   LPF/eth1/00:16:01:0c:ac:53
Listening on LPF/eth0/00:16:ec:ef:d0:dd
Sending on   LPF/eth0/00:16:ec:ef:d0:dd
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
done

```

---

### Post by compwiz18 on 2006-11-16
> **0MG said:**
> It's not finding my ra0 interface:

# /opt/connection-manager/manager
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

no wireless interface...


Any advice?
Could you post the output of **iwlist scan** and I'll see if I can fix that problem?

---

### Post by compwiz18 on 2006-11-16
@**onlainari**: I put up a new version.  See if that fixes your problem.

---

### Post by alchimera on 2006-11-16
> **compwiz18 said:**
> OK, new version, should fix the signal strength errors.

:D yes, now working for me.

Has same issues with broken panels after installing 1.0.3 (all OK after reboot) and the same python warnings on launching Connection Manager:
```
08:14:08: Mailcap file /etc/mailcap, line 67: incomplete entry ignored.
08:14:08: Mailcap file /etc/mailcap, line 68: incomplete entry ignored.
08:14:08: Mailcap file /etc/mailcap, line 113: incomplete entry ignored.

```Have tried "Refresh", "Connect" and "Setup Network" and all seems fine; is pouring with rain today so may have time to play with encryption.

NIce one compwiz18!

---

### Post by compwiz18 on 2006-11-16
> **alchimera said:**
> :D yes, now working for me.

Has same issues with broken panels after installing 1.0.3 (all OK after reboot) and the same python warnings on launching Connection Manager:
```
08:14:08: Mailcap file /etc/mailcap, line 67: incomplete entry ignored.
08:14:08: Mailcap file /etc/mailcap, line 68: incomplete entry ignored.
08:14:08: Mailcap file /etc/mailcap, line 113: incomplete entry ignored.

```Have tried "Refresh", "Connect" and "Setup Network" and all seems fine; is pouring with rain today so may have time to play with encryption.

NIce one compwiz18!
I couldn't figure out for the life of me what the mailcap errors where (or at least how to get rid of them)  But it turns out that I if you edit the lines that have the errors, it will fix the problem.  I'm not sure if this is the best solution though.

---

### Post by onlainari on 2006-11-16
No change with 1.0.4. Tried after install and after reboot.

:-k

---

### Post by compwiz18 on 2006-11-16
Howdy.

I fixed the bug in the part that detects your wireless card, so **onlainari** and **0MG**, your problems should be fixed.

---

### Post by foxy123 on 2006-11-16
> **compwiz18 said:**
> I just finished a wireless connection manager, that, in my opinion, fixes most of the difficulties that I've had with other managers, such as wifi-radar and network-manager.

Features include:
[LIST]
[*]WPA support out of the box
[*]WEP support out of the box
[*]Connection to preferred network at boot
[*]Support for signal levels (including when you use ndiswrapper)
[*]Network profiles, for example you can set static IPs for one network and DHCP for another, same goes with static DNS
[/LIST]

Things that I fixed: it doesn't ask for your password to connect to an encrypted network at boot (unlike network-manager), supports WPA easily (unlike wifi-radar), looks nice

If you want to give it a try, I made a deb that you can download here: [.deb]("http://compwiz18.blackhole.cx/connection-manager/get.php?file=connection-manager.deb")

if you give it a try, leave me some feedback.  I'm looking for ways to improve it :D

I'll be updating it, so check back for new features :D

Current status: Pre-beta
Current version: 1.0.5 (bug fix)

Version History:
1.0.4 - Bug fix
1.0.3 - Bug fix
1.0.2 - Bug fix
1.0.1 - Bug fix
1.0.0 - Original release

I wonder if you could also include a version number in the name of your package as it is not sometimes clear if the package has been updated or not.

---

### Post by iki488 on 2006-11-16
the link for the .deb is dead :s

---

### Post by compwiz18 on 2006-11-16
> **foxy123 said:**
> I wonder if you could also include a version number in the name of your package as it is not sometimes clear if the package has been updated or not.

> **iki488 said:**
> the link for the .deb is dead :s

Fixed both of these.

---

### Post by foxy123 on 2006-11-16
> **compwiz18 said:**
> Fixed both of these.

thanks for that. I will definitely try the connection manager as soon as I am through with my current project which should be more or less over by the end of the week as I use my laptop as a main production machine.

---

### Post by iki488 on 2006-11-16
here is my output :

> lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

None
no wireless interface...


the problem is that my wireless card name is eth1 ! so how can I tell to connection manager to use eth1 instead of eth0 or sit0 ??

---

### Post by yopnono on 2006-11-16
Hi. Just like to add that it don't work on my machine, since the py script uses wlan0 and it's hard coded. And my interface is ath0 and the other machine is eth0

---

### Post by yopnono on 2006-11-16
Ah should add that I'm using WPA

---

### Post by iki488 on 2006-11-16
there is a probleme in /opt/connection-manager/manager

> 
f = os.popen( 'iwconfig', "r" )
		interface_data= f.read()
		f.close()
		wifi_interface_pattern	= re.compile('(\w*?)\s*(?=IEEE)',re.DOTALL | re.I | re.M  | re.S)
		m = wifi_interface_pattern.search( interface_data )
		print m
		if m:
			print "interface3: |" + m.groups()[0] + "|"
			self.interface = m.groups()[0]
			print "interface2: " + self.interface
		else:
			print "no wireless interface..."
			dlg = wx.MessageDialog(self, 'Connection Manager could not detect your wireless card.','Error',wx.ICON_ERROR)


especially here : 
> 
wifi_interface_pattern	= re.compile('(\w*?)\s*(?=IEEE)',re.DOTALL | re.I | re.M  | re.S)
m = wifi_interface_pattern.search( interface_data )


for me he enters in :

> 
else:
        print "no wireless interface..."
	dlg = wx.MessageDialog(self, 'Connection Manager could not detect your wireless card.','Error',wx.ICON_ERROR)


---

### Post by onlainari on 2006-11-16
```
 ville@ville-laptop:~/files$ sudo /opt/connection-manager/manager 
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

<_sre.SRE_Match object at 0xb7c98760>
interface3: |eth1|
interface2: eth1
eth1
0
1
2
link clicked: py:preferences(0)
link clicked: py:connect(0)
{'encryption': 'on', 'signal': '-57', 'ap_mac': '00:90:CC:C3:24:8A', 'mode': 'Master', 'channel': '7', 'essid': 'Gifu'}
interface1: eth1
interface: eth1
killing previous wpa supps
wpa_supplicant: no process killed
iwconfig eth1 mode Managed
iwconfig eth1 essid "Gifu" channel 7 key xxxxxxxxxx ap 00:90:CC:C3:24:8A
configuring dhcp
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:16:01:0c:ac:53
Sending on   LPF/eth1/00:16:01:0c:ac:53
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
done
ville@ville-laptop:~/files$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Gifu"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.442 GHz  Access Point: 00:90:CC:C3:24:8A   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ville@ville-laptop:~/files$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:EC:EF:D0:DD  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 Base address:0x4c00 

eth1      Link encap:Ethernet  HWaddr 00:16:01:0C:AC:53  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:30 errors:0 dropped:91 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10016 (9.7 KiB)  TX bytes:3726 (3.6 KiB)
          Interrupt:169 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

I also did try with static ip's having those I usually get on windows side. Connection manager quickly set me the ip's. I can ping my own ip. I can't ping the 192.168.1.1 which is dns,dhcp and gw.

---

### Post by compwiz18 on 2006-11-16
> **yopnono said:**
> Hi. Just like to add that it don't work on my machine, since the py script uses wlan0 and it's hard coded. And my interface is ath0 and the other machine is eth0
@**yopnono**: The script should automatically detect your interface and select the correct one...try downloading the newest version.

@**Everyone Else**: If you experience a problem, please post the output from the Terminal (run **sudo /opt/connection-manager/manager** in the Terminal to get the output), and the output from **iwlist scan** and the output from **iwconfig**

---

### Post by compwiz18 on 2006-11-16
Let me run this by people: should I make a config file that will let you specify the wireless interface instead of this whole "find-the-correct-interface" thing?  It seems like it would be simpler if that was the way it works...

---

### Post by compwiz18 on 2006-11-16
@**iki488**: can you run **iwlist scan** and post the output? I have a feeling the algorithm for detecting wireless cards is not working.

The problem is I only have my **iwlist scan** and **iwconfig** to test the regex on, so if it works on mine, that is as far as I can test.

---

### Post by 0MG on 2006-11-16
> **compwiz18 said:**
> Could you post the output of **iwlist scan** and I'll see if I can fix that problem?

Here's the program output again with 1.0.5:
```
p# /opt/connection-manager/manager
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

None
no wireless interface...

```

iwlist scan output:

```
# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:0F:66:F0:B8:E3
                    Mode:Managed
                    ESSID:"Quality Inn"
                    Encryption key:off
                    Channel:6
                    Quality:0/100  Signal level:-71 dBm  Noise level:-192 dBm
          Cell 02 - Address: E6:FF:F5:26:CE:0D
                    Mode:Ad-Hoc
                    ESSID:"hpsetup"
                    Encryption key:off
                    Channel:10
                    Quality:0/100  Signal level:-75 dBm  Noise level:-192 dBm

sit0      Interface doesn't support scanning.

```

iwconfig output:
```
# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"Quality Inn"
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:54 Mb/s   Tx-Power:0 dBm 
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=60/100  Signal level=-70 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

Thanks for your efforts!

---

### Post by 0MG on 2006-11-16
> **compwiz18 said:**
> Let me run this by people: should I make a config file that will let you specify the wireless interface instead of this whole "find-the-correct-interface" thing?  It seems like it would be simpler if that was the way it works...

That would be a good idea as I sometimes use more than one wireless interface.

---

### Post by iki488 on 2006-11-16
> **compwiz18 said:**
> @**iki488**: can you run **iwlist scan** and post the output? I have a feeling the algorithm for detecting wireless cards is not working.

The problem is I only have my **iwlist scan** and **iwconfig** to test the regex on, so if it works on mine, that is as far as I can test.

**here is the iwlist output : **

> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:14:A4:64:7A:ED
                    ESSID:"Mobistar-2F6E"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=50/100  Signal level=-71 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 224ms ago
          Cell 02 - Address: 00:14:A4:16:BD:D3
                    ESSID:"Mobistar-55EC"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=39/100  Signal level=-77 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 244ms ago
          Cell 03 - Address: 00:12:BF:07:C1:0F
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=86/100  Signal level=-43 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 44ms ago

sit0      Interface doesn't support scanning.


[B]
and the iwconfig output :[/B]

> 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


[B]
and when I run /opt/connection-manager/manager :[/B]

> lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

None
no wireless interface...


my wireless card is known as **eth1** and this is an **ipw2200bg**

---

### Post by iki488 on 2006-11-16
any solution ? because I really want to test this new manager :D

---

### Post by compwiz18 on 2006-11-16
OK, update, 1.0.6, now the interface is specified in the conf file /opt/connection-manager/data/manager-settings.conf.

You can specify the interface manually, or run the program once, and it will scan for the right one and add it to the conf file - but only the first run - after that it will read from the conf file.  Also, I updated the interface finding stuff so it now works with ra0 as well.

Example conf:
> 
[Settings]
interface = wlan0


---

### Post by iki488 on 2006-11-16
> **compwiz18 said:**
> OK, update, 1.0.6, now the interface is specified in the conf file /opt/connection-manager/data/manager-settings.conf.

You can specify the interface manually, or run the program once, and it will scan for the right one and add it to the conf file - but only the first run - after that it will read from the conf file.  Also, I updated the interface finding stuff so it now works with ra0 as well.

Example conf:

ok but where is the link ? the link in the first page is 1.0.5 .

---

### Post by 0MG on 2006-11-16
> **iki488 said:**
> ok but where is the link ? the link in the first page is 1.0.5 .

I copied the link, pasted it in the browser, changed it for 1.0.6. Works fine.


Btw, program b0rked on first run, but after that it looks great! Thanks again, I will use this now.

---

### Post by iki488 on 2006-11-16
with 1.0.6 I can see the wifi networks avalaible, but I can't connect. I use wpa.

here is the output of connection manager :

> 
ken@ken-laptop:~$ sudo /opt/connection-manager/manager 
interfacefromconf: eth1
eth1
0
1
2
link clicked: py:preferences(0)
link clicked: py:connect(0)
{'encryption': 'on', 'signal': '-43', 'ap_mac': '00:12:BF:07:C1:0F', 'mode': 'Master', 'channel': '6', 'essid': 'KenGabs'}
interface1: eth1
interface: eth1
killing previous wpa supps
wpa_supplicant: aucun processus tué
wrote new wpa key to wpa_supplicant config file
running wpa supp
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
ioctl[SIOCGIFFLAGS]: No such device
ioctl[SIOCGIWRANGE]: No such device
ioctl[SIOCGIFINDEX]: No such device
iwconfig eth1 mode Managed
iwconfig eth1 essid "KenGabs" channel 6 ap 00:12:BF:07:C1:0F
configuring dhcp
There is already a pid file /var/run/dhclient.pid with pid 11352
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWAUTH]: No such device
WEXT auth param 7 value 0x0 - ioctl[SIOCSIWAUTH]: No such device
WEXT auth param 5 value 0x0 - ioctl[SIOCSIWAUTH]: No such device
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAP]: No such device
ioctl[SIOCGIFFLAGS]: No such device
Listening on LPF/eth1/00:0e:35:48:0c:66
Sending on   LPF/eth1/00:0e:35:48:0c:66
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
done


eth1 is correct but I can't connect to my network

arff :s:s

---

### Post by compwiz18 on 2006-11-16
Oops.  Try the new version - 1.0.7 - this problem is fixed.

---

### Post by yopnono on 2006-11-17
> **compwiz18 said:**
> Oops.  Try the new version - 1.0.7 - this problem is fixed.

No I still don't get it to work.

So I did some modifications to your script, and now it works like it should.

I did change the auto-connect file line: 93 to this instead of *wlan0*
> (interface,essid,channel,mode,ap_mac,enctype,key,ip,gateway,subnet,dns1,dns2)

Also it don't connect after suspend, so I did add a resume script to bring it  back online.

In folder
> /etc/acpi/resume.d
I put a script called *40-auto-connect.sh* that executes at resume as root.
> #!/bin/sh
# Bring wifi network interface back online.

cd /etc/init.d/
./auto-connect

Also you should set the user permission to root and not user like the scripts are now. I also did change the size of the main dialog to 500 instead of 750, looks better (I think).

Thank for a great work.

---

### Post by compwiz18 on 2006-11-17
@**yopnono**: Cool.  I'll add the resume script when I get back about Sunday noon here in Tokyo...I don't know what time that is where you are.  I'll fix the file permissions too.  Can you run **iwlist scan** and **iwconfig** and post the output of the script?  I'd like to see what goes wrong when you try and run it...

Edit:sorry, I was rereading your post - can you post the version you modified to work?  I'd like to see what you changed.  Was the only thing you changed the autoconnect script?

---

### Post by yopnono on 2006-11-17
> **compwiz18 said:**
> @**yopnono**: Cool.  I'll add the resume script when I get back about Sunday noon here in Tokyo...I don't know what time that is where you are.  I'll fix the file permissions too.  Can you run **iwlist scan** and **iwconfig** and post the output of the script?  I'd like to see what goes wrong when you try and run it...

Edit:sorry, I was rereading your post - can you post the version you modified to work?  I'd like to see what you changed.  Was the only thing you changed the autoconnect script?

Ok attached some TXT files.

---

### Post by yopnono on 2006-11-17
deleted

---

### Post by yopnono on 2006-11-17
Sorry this one is like it should. The other one don't have the resume folder in the correct dir.

Attached a deb

---

### Post by iki488 on 2006-11-17
> **yopnono said:**
> Sorry this one is like it should. The other one don't have the resume folder in the correct dir.

Attached a deb

version 1.0.8-3 still doesn't work for me :s:s

here is the output :

> 
interfacefromconf: eth1

(python:5591): Gtk-WARNING **: Theme directory scalable/stock/svg of theme Sladf has no size field

eth1
0
1
link clicked: py:preferences(0)
link clicked: py:connect(0)
{'encryption': 'on', 'signal': '-41', 'ap_mac': '00:12:BF:07:C1:0F', 'mode': 'Master', 'channel': '6', 'essid': 'KenGabs'}
interface1: eth1
interface: eth1
killing previous wpa supps
running wpa supp
iwconfig eth1 mode Managed
iwconfig eth1 essid "KenGabs" channel 6 ap 00:12:BF:07:C1:0F
configuring dhcp
There is already a pid file /var/run/dhclient.pid with pid 5553
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0e:35:48:0c:66
Sending on   LPF/eth1/00:0e:35:48:0c:66
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
done


eth1 is the correct one but I can't connect :s
any solution ?

ps : with network manager it works... most of the time :p

---

### Post by yopnono on 2006-11-17
Found an other problem. If using atheros chip (ath0) then it don't connect because the wpa is using wext and atheros need madwifi in dapper.

Is it possible to add so you can from the gui select / choose if you like to use wext, madwifi etc,etc.

---

### Post by yopnono on 2006-11-17
> **iki488 said:**
> version 1.0.8-3 still doesn't work for me :s:s
ps : with network manager it works... most of the time :p

Question are you running dapper with original native driver for your intel card?

If so try to change this file 
> /usr/lib/python2.4/networking.py
change this string, line: 132
```

wpa_supplicant_daemon = os.popen( "wpa_supplicant -B -i " + interface + " -c /opt/connection-manager/data/wpa_supplicant.conf -D wext","r")
```
to
```
wpa_supplicant_daemon = os.popen( "wpa_supplicant -B -i " + interface + " -c /opt/connection-manager/data/wpa_supplicant.conf -D ipw","r")
```

---

### Post by iki488 on 2006-11-17
I'm running edgy and yes it is the native driver.

I'll try that this evening :)

---

### Post by yopnono on 2006-11-17
By the way. Maybe you could/should add some advanced settings for driver and wpa settings, so it's possible to set the kind of wpa you are using.

Driver settings
```
drivers:
  hostap = Host AP driver (Intersil Prism2/2.5/3)
  madwifi = MADWIFI 802.11 support (Atheros, etc.)
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  wext = Linux wireless extensions (generic)
  ndiswrapper = Linux ndiswrapper
  ipw = Intel ipw2100/2200 driver
  wired = wpa_supplicant wired Ethernet driver
  test = wpa_supplicant test driver
```

And WPA settings etc,etc There is alot of different settings have a look in
/usr/share/doc/wpasupplicant
```
#	key_mgmt=WPA-EAP
#	proto=RSN
#	proto=WPA
#	pairwise=CCMP TKIP
```

---

### Post by RD1945 on 2006-11-17
Works like a charm.:-D

---

### Post by McDuff on 2006-11-17
i've downloaded yopnono's 1.0.8. it will neither connect to wpa-encrypted nor to wep-encrypted networks.
output of $ sudo /opt/connection-manager/manager (with wpa network)

```
$ sudo /opt/connection-manager/manager 
Password:
interfacefromconf: ra0
ra0
0
link clicked: py:connect(0)
{'encryption': 'on', 'signal': '-67', 'ap_mac': '00:11:50:AF:27:84', 'mode': 'Managed', 'channel': '11', 'essid': 'breizh'}
interface1: ra0
interface: ra0
killing previous wpa supps
running wpa supp
iwconfig ra0 mode Managed
iwconfig ra0 essid "breizh" channel 11 ap 00:11:50:AF:27:84
configuring dhcp
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 7 value 0x1 - ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - There is already a pid file /var/run/dhclient.pid with pid 7768
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/00:10:60:27:34:a5
Sending on   LPF/ra0/00:10:60:27:34:a5
Sending on   Socket/fallback
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 21
No DHCPOFFERS received.
Trying recorded lease 192.168.2.10
No working leases in persistent database - sleeping.
done

```

output of iwconfig
```
$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"breizh"  
          Mode:Managed  Frequency=2.462 GHz  Bit Rate:11 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-69 dBm  Noise level:-214 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

and output of iwlistscan
```

$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:11:50:AF:27:84
                    Mode:Managed
                    ESSID:"breizh"
                    Encryption key:on
                    Channel:11
                    Quality:0/100  Signal level:-68 dBm  Noise level:-201 dBm

sit0      Interface doesn't support scanning.

```

i hope this helps developping your tool. i'm longing to see a working tool for my card, as none of the existing work with it.

---

### Post by wieman01 on 2006-11-17
> **yopnono said:**
> Driver settings
```
drivers:
  hostap = Host AP driver (Intersil Prism2/2.5/3)
  madwifi = MADWIFI 802.11 support (Atheros, etc.)
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  wext = Linux wireless extensions (generic)
  ndiswrapper = Linux ndiswrapper
  ipw = Intel ipw2100/2200 driver
  wired = wpa_supplicant wired Ethernet driver
  test = wpa_supplicant test driver
```[/CODE]

I think this is a bit outdated if I may say that: "wext" will replace "ipw" as well as "ndiswrapper"... I am using both. The latest wpa-supplicant says this:
> hostap = Host AP driver (Intersil Prism2/2.5/3)
atmel = ATMEL AT76C5XXx (USB, PCMCIA)
wext = Linux wireless extensions (generic)
madwifi = Atheros
wired = wpa_supplicant wired Ethernet driver

---

### Post by iki488 on 2006-11-17
don't understand why with network manager it works sometimes but with connection manager it never works :s:s (I use wpa-psk)

too bad...

---

### Post by gmanpsycho on 2006-11-18
Compiz you the man. I'm posting wirelessly now...  XD I rebooted after setting up the connection manager and I then had to run 
Code:
> sudo /opt/connection-manager/manager
and click on "Connect". I was able to get an IP and here I am. I am running KWLAN. Let me know if this would cause any problems with Connection-Manager.
Thanks for everyone's hard work to make wireless... uhmmm painless. :)

BTW: I'm running WPA-PSK TKIP and it seemes to be fine... I just have to reconnect by running the program after rebooting.

---

### Post by Ago12 on 2006-11-18
Hum, I'm waiting for a seem-to-work everywhere release, it sounds good! :)

Could anyone provide a screenshot please? :)

---

### Post by cwmaxson on 2006-11-18
You have no idea how much I am in love with you right now sir.

Thank You.

Thank You.

(bows head in reverence)

I use my laptop at home and school.  One is unsecured, the other isn't.  Network manager doesn't seem to like my ndiswrapper on an unsecured network, and wifi radar is horrible for wpa.  I was hoping someone would fix this whole mess, and here you are!

Thank You.

---

### Post by compwiz18 on 2006-11-18
> **McDuff said:**
> i've downloaded yopnono's 1.0.8. it will neither connect to wpa-encrypted nor to wep-encrypted networks.
output of $ sudo /opt/connection-manager/manager (with wpa network)

```
$ sudo /opt/connection-manager/manager 
Password:
interfacefromconf: ra0
ra0
0
link clicked: py:connect(0)
{'encryption': 'on', 'signal': '-67', 'ap_mac': '00:11:50:AF:27:84', 'mode': 'Managed', 'channel': '11', 'essid': 'breizh'}
interface1: ra0
interface: ra0
killing previous wpa supps
running wpa supp
iwconfig ra0 mode Managed
iwconfig ra0 essid "breizh" channel 11 ap 00:11:50:AF:27:84
configuring dhcp
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 7 value 0x1 - ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - There is already a pid file /var/run/dhclient.pid with pid 7768
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/00:10:60:27:34:a5
Sending on   LPF/ra0/00:10:60:27:34:a5
Sending on   Socket/fallback
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 21
No DHCPOFFERS received.
Trying recorded lease 192.168.2.10
No working leases in persistent database - sleeping.
done

```

output of iwconfig
```
$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"breizh"  
          Mode:Managed  Frequency=2.462 GHz  Bit Rate:11 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-69 dBm  Noise level:-214 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

and output of iwlistscan
```

$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:11:50:AF:27:84
                    Mode:Managed
                    ESSID:"breizh"
                    Encryption key:on
                    Channel:11
                    Quality:0/100  Signal level:-68 dBm  Noise level:-201 dBm

sit0      Interface doesn't support scanning.

```

i hope this helps developping your tool. i'm longing to see a working tool for my card, as none of the existing work with it.
Can anyone tell me if this interface (ra0) needs a special wpa_supplicant driver?  This could be the problem...I just don't know how to solve it.

---

### Post by compwiz18 on 2006-11-19
OK, you can now set the driver WPA uses, by clicking Preferences with version 1.1.0.

---

### Post by yopnono on 2006-11-19
> **compwiz18 said:**
> Can anyone tell me if this interface (ra0) needs a special wpa_supplicant driver?  This could be the problem...I just don't know how to solve it.


That's realtek and I have never tried that. But I think you need the wrapper.

---

### Post by compwiz18 on 2006-11-19
Can someone who has a working realtek card tell me how they configure it to use WPA via the Terminal?  If I know this, I can add it to the program.

---

### Post by wieman01 on 2006-11-19
Yes, you can take this as a reference. Don't want to hijack this thread, but perhaps it helps you extend your program. Very interested to see the results later on.

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

Use "wpa-drver wext". I know that the native (Linux) driver for Ralink has some drawbacks, so I am not entirely sure if it supports WPA1/WPA2. If you fail, try "ndiswrapper" instead, but this has nothing to do with your program.

---

### Post by yopnono on 2006-11-19
Yep. I have done some search and it's like wieman01 say some seems to work with the native driver, and some need ndiswrapper, and some don't support WPA.

---

### Post by compwiz18 on 2006-11-19
So the conclusion is that there is nothing I can do to make realtek chips work better, correct?

---

### Post by compwiz18 on 2006-11-19
@**McDuff**: Have you ever successfully connected to a WPA network using your card?

---

### Post by wieman01 on 2006-11-19
> **compwiz18 said:**
> So the conclusion is that there is nothing I can do to make realtek chips work better, correct?
That may be the result. I think this problem does not relate to your application, as far as I know there is nothing that you can do about it. I recommend to try "ndiswrapper" to resolve this issue, but I have said, this has nothing to do with your program anymore.

**_EDIT:_**
I also recommend that wireless devices be tested using a manual script first in order to confirm that WPA works at all.

---

### Post by compwiz18 on 2006-11-19
> **wieman01 said:**
> That may be the result. I think this problem does not relate to your application, as far as I know there is nothing that you can do about it. I recommend to try "ndiswrapper" to resolve this issue, but I have said, this has nothing to do with your program anymore.

**_EDIT:_**
I also recommend that wireless devices be tested using a manual script first in order to confirm that WPA works at all.
OK.

By the way, if anyone has any feature requests, I'd like to hear them.

and if you are having trouble making it work, post away.

---

### Post by yopnono on 2006-11-19
> By the way, if anyone has any feature requests, I'd like to hear them.
I do I do :)
Well if you could a dropdown menu for the different wpa drivers that can be used and also be able to type it yourself if needed.

Also if possible add some different WPA protocol, like 

/usr/share/doc/wpasupplicant

> 
# key_mgmt=WPA-EAP 
# proto=RSN 
# proto=WPA 
# pairwise=CCMP TKIP


Yes i know more work :( But I must say this application is brilliant. :)

---

### Post by compwiz18 on 2006-11-19
Part of my problem is I don't fully understand the WPA protocol, all I know is that it works on my computer...I'll have to research it a little bit, then I'll add some more features - I don't like programming stuff I don't understand.

I think that after this I'll pull it out of prebeta and in to beta, what do you think?

Oh and one more thing: I tried suspend on my computer, and when it came out, it did what it was supposed to and reconnected :D

---

### Post by yopnono on 2006-11-19
I think what you think :)
Nice to hear that the suspend worked like it should.

---

### Post by Ago12 on 2006-11-19
Just installed it:

1) Wow, it works nice! (after a reboot) :)
2) I can confirm that it works flawlessly with suspend2, unlike NM :)

3) Will you provide a tray icon? (not sure it would be necessary, since it autoconnects)
4) I get this error when I start it:

> Mailcap file /etc/mailcap, line 95: incomplete entry ignored.

But it works...

The incrimined line is:
> application/x-sc

Bah...

Thank you for your good work, keep it up! :)

---

### Post by compwiz18 on 2006-11-19
I need someone who knows more about Python then me to figure out how to smash that annoying little mailcap error.  The best way I have so far is to remove the offending line...

---

### Post by foxy123 on 2006-11-19
I tried connection-manager and borked my Internet connection competely, though I do not blame your programme at all. Now I cannot connect neither wired nor wireless. I removed connection-manager and install network-manager again but still no Internet.

Actually everything shows that the connection is established, IP address is assigned and all the stuff. I am connected to my network, but not to the Internet. It is so bizarre. I have no idea what to do.

Obviously I am writting from another PC but I need the Internet on my laptop as it is my main machine. This desktop uses the same router and is connected.

---

### Post by compwiz18 on 2006-11-19
Did/can you try rebooting?  If that doesn't help, check the routing table...if you need help with this, ask.

---

### Post by Ago12 on 2006-11-19
I haven't tried yet, but... How does it react with wired-connection?

Does it connect automatically/reconize it, or do we have to use network-manager?

---

### Post by wieman01 on 2006-11-19
> **compwiz18 said:**
> Part of my problem is I don't fully understand the WPA protocol, all I know is that it works on my computer...I'll have to research it a little bit, then I'll add some more features - I don't like programming stuff I don't understand.
Well, I do... at least most of it. So if you need a hand, just let me know. I'll support you where I can. Nice initiative I think this is, so I am ready to support it.

Other protocols would be nice as well... e.g. LEAP, PEAP, etc.

---

### Post by foxy123 on 2006-11-19
OK, the problem was with resolv.conf. I did something that borked it. Now it is fine.

Wow, this programme is amazing! It recognised my wireless connection and after I entered my WAP key, it connects without asking me to enter WAP key. It's a relief. Thanks a lot!

However I am also interested in wired connection. I use wireless only downstairs but most of the time I connected to my router via Ethernet cable. Network-manager automatically connected to wired if it was available. How it works with the connection-manager?

---

### Post by foxy123 on 2006-11-19
I tried to enable the wired interface using a Neworking tool. After that I could not use wireless any more. So I had to disable wired and reboot to get wireless up, which is not very convenient.

I would like to see wired interface as default. If it is not available, then the connection-manager should connect to the default wireless connection and if it is also unavailable then it should scan the available connections and open the dialogue box listing all available connections, like it does when you launch connection-manager from the menu. Also it would be nice to have an icon in systray.

Anyway, it is a great tool and I am looking forward to improvements and happy to test it.

---

### Post by foxy123 on 2006-11-19
Also if the connection-manager does not have any Gnome dependencies, it would be a good idea to include it in Xubuntu. I may post it on its mail-list.

---

### Post by yopnono on 2006-11-19
> **foxy123 said:**
> I tried to enable the wired interface using a Neworking tool. After that I could not use wireless any more. So I had to disable wired and reboot to get wireless up, which is not very convenient.

I would like to see wired interface as default. If it is not available, then the connection-manager should connect to the default wireless connection and if it is also unavailable then it should scan the available connections and open the dialogue box listing all available connections, like it does when you launch connection-manager from the menu. Also it would be nice to have an icon in systray.

Anyway, it is a great tool and I am looking forward to improvements and happy to test it.

I can switch between wifi and wire. But make sure the wired is enabled in the network settings. Also if you don't have any Static IP on the wired you may need to run * sudo ifup -a --force * in the terminal to get the DHCP address faster.

---

### Post by compuguy1088 on 2006-11-19
> **Ago12 said:**
> Just installed it:

1) Wow, it works nice! (after a reboot) :)
2) I can confirm that it works flawlessly with suspend2, unlike NM :)

3) Will you provide a tray icon? (not sure it would be necessary, since it autoconnects)
4) I get this error when I start it:



But it works...

The incrimined line is:


Bah...

Thank you for your good work, keep it up! :)

I get the same error as well, thoug hit works fine. Though the only issue with using this is that I have no real good meter to see signal strength in XFCE (xubuntu 6.10).

---

### Post by foxy123 on 2006-11-19
> **yopnono said:**
> I can switch between wifi and wire. But make sure the wired is enabled in the network settings. Also if you don't have any Static IP on the wired you may need to run * sudo ifup -a --force * in the terminal to get the DHCP address faster.

how do you actually switch? The only way I see at the moment is to go to Networking and activate Ethernet connection. To switch back to wireless is to deactivate it and wait until the connection-manager establishes it again?

---

### Post by compuguy1088 on 2006-11-19
On another note, this app I don't think specifically mentions WPA2 compatibility, but it does work with it :). The only feature I could think that is missing in this is the ability to connect manually to a wireless network (SSID broadcast disabled) and a signal meter to go with the program for xfce.

---

### Post by yopnono on 2006-11-19
> **foxy123 said:**
> how do you actually switch? The only way I see at the moment is to go to Networking and activate Ethernet connection. To switch back to wireless is to deactivate it and wait until the connection-manager establishes it again?

Well I'm on my laptop so I just disable the wifi Fn+F2, then I just plug in the Ethernet cable and wait till I get a DHCP address or I use ifup -a --force to get it faster. Make sure it's activated in the network settings.

Yes it would be nice to be able to use the connect manager gui to do this stuff.

---

### Post by yopnono on 2006-11-19
Question:
Is it possible to add to the manager so you can see if the encryption is WEP or WPA? Like now it only say encrypted.

---

### Post by compwiz18 on 2006-11-20
> **foxy123 said:**
> I tried to enable the wired interface using a Neworking tool. After that I could not use wireless any more. So I had to disable wired and reboot to get wireless up, which is not very convenient.

I would like to see wired interface as default. If it is not available, then the connection-manager should connect to the default wireless connection and if it is also unavailable then it should scan the available connections and open the dialogue box listing all available connections, like it does when you launch connection-manager from the menu. Also it would be nice to have an icon in systray.

Anyway, it is a great tool and I am looking forward to improvements and happy to test it.

OK, one systray icon coming up.  This was on my todo list, but I have a couple of questions about startup that I need to know, see bottom of post.

> **foxy123 said:**
> Also if the connection-manager does not have any Gnome dependencies, it would be a good idea to include it in Xubuntu. I may post it on its mail-list.

Cool.

> **compuguy1088 said:**
> I get the same error as well, thoug hit works fine. Though the only issue with using this is that I have no real good meter to see signal strength in XFCE (xubuntu 6.10).

Systray icon will include signal strength.

> **compuguy1088 said:**
> On another note, this app I don't think specifically mentions WPA2 compatibility, but it does work with it :). The only feature I could think that is missing in this is the ability to connect manually to a wireless network (SSID broadcast disabled) and a signal meter to go with the program for xfce.

systray, and will fix wpa2 compatibility info.

> **yopnono said:**
> Well I'm on my laptop so I just disable the wifi Fn+F2, then I just plug in the Ethernet cable and wait till I get a DHCP address or I use ifup -a --force to get it faster. Make sure it's activated in the network settings.

Yes it would be nice to be able to use the connect manager gui to do this stuff.

Ok, but I have questions about programming this. see bottom.

> **yopnono said:**
> Question:
Is it possible to add to the manager so you can see if the encryption is WEP or WPA? Like now it only say encrypted.

Can do this too.

OK, my questions:
[LIST=1]
[*]How do I tell if there is a cord plugged into the Ethernet port?
[*]How do I start a GUI at boot of the Desktop?  This needs to work in XFCE, KDE, Gnome.
[/LIST]

---

### Post by foxy123 on 2006-11-20
> **compwiz18 said:**
> OK, one systray icon coming up.  This was on my todo list, but I have a couple of questions about startup that I need to know, see bottom of post.

Thanks a lot.

> [*]How do I tell if there is a cord plugged into the Ethernet port?

There is a script whereami which uses a number of commands to do it. Here the thread about it on the forum
[http://www.ubuntuforums.org/showthread.php?t=24994](http://www.ubuntuforums.org/showthread.php?t=24994) Have a look, maybe it will help. I am not a programmer at all so I cannot be of more help, sorry.

> [*]How do I start a GUI at boot of the Desktop?  This needs to work in XFCE, KDE, Gnome.
[/LIST]
beats me :(

---

### Post by compwiz18 on 2006-11-20
Cool, I figured out how to check if you plug the cable in.  Now all I need to know is how to start a GUI program as root  at the Desktop startup, so it ends up in the systray.

---

### Post by h.aling on 2006-11-20
What about running a daemon as root and a client that can be put in the systray?

Or is this security-wise not a wise solution?

---

### Post by yopnono on 2006-11-20
> **compwiz18 said:**
> Cool, I figured out how to check if you plug the cable in.  Now all I need to know is how to start a GUI program as root  at the Desktop startup, so it ends up in the systray.

Don't know but.. It may help if you take look at the source of Gnome Network Monitor, since this starts at boot if added to the panel and it's run as root  I think. (gnome-netstatus-applet)

[ftp://ftp.gnome.org/pub/gnome/desktop/2.17/2.17.2/sources/gnome-netstatus-2.12.0.tar.bz2](ftp://ftp.gnome.org/pub/gnome/desktop/2.17/2.17.2/sources/gnome-netstatus-2.12.0.tar.bz2)

---

### Post by Ago12 on 2006-11-20
Feature request: have multiple "prefered networks": when the app finds on of them, it connects automaticaly (for instnce to the stronger if there are two).

My personnal experience: At home, I connect to PLF (don't laugh :p), wich is wap-ed, and at school I connect to EBS or EBS1 (depending on the classroom), wich are open.

I would like to be able to set all these three ESSIDs as prefered, so wireless configuration becomes totally transparent (no need to start or click anything).


Thanks :)

---

### Post by McDuff on 2006-11-20
> **compwiz18 said:**
> Can someone who has a working realtek card tell me how they configure it to use WPA via the Terminal?  If I know this, I can add it to the program.

havent been at home this weekend...

in a thread in this forum (cant remember which) i have read, that wpa is built in to the rt2500 driver used by my card. this seems to be the reason, why it wont work with networkmanager or wifiradar.
to use wpa, i have to edit /etc/network/interfaces to look like this:

```
auto ra0
iface ra0 inet dhcp

pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid "myessid"
pre-up iwconfig ra0 mode Managed
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="mykey"
pre-up ifconfig ra0 up

```

there's a wiki entry at [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

there are two tools around for rt2500 (raconfig and rutilt), but neither of them is in the repositories, the one bing outdated, the other not yet supporting wpa.

---

### Post by McDuff on 2006-11-20
one more thing: wep is working without a problem, i obviously didnt test correctly last time.

---

### Post by tube on 2006-11-20
> **compwiz18 said:**
> Now all I need to know is how to start a GUI program as root  at the Desktop startup, so it ends up in the systray.There's a freedesktop.org [autostart spec draft]("http://standards.freedesktop.org/autostart-spec/autostart-spec-0.5.html") that's supported by current versions of Xfce and GNOME (I think). I've no idea about KDE.

And as was suggested above, it would probably be a more robust and secure solution not to start the systray icon as root, but to implement this as an external program that communicates with the manager (via dbus?).

PS: Thanks a lot for working on this! I certainly won't miss network-manager...

---

### Post by Altrego on 2006-11-20
When I install the package, I get a dependancy not satisfied error. I'm not quite savy enough to understand what it means. See below:

Dependency is not satisfiable: libwxgtk2.6-0


fixed... 

Still having problems connecting to networks. just seems to time out. I'll update to the newest version and test again.

---

### Post by yopnono on 2006-11-20
> **Altrego said:**
> When I install the package, I get a dependancy not satisfied error. I'm not quite savy enough to understand what it means. See below:

Dependency is not satisfiable: libwxgtk2.6-0

Then you need to install it. Open terminal and..

```
sudo aptitude install libwxgtk2.6-0
```

---

### Post by compwiz18 on 2006-11-20
> **yopnono said:**
> Then you need to install it. Open terminal and..

```
sudo aptitude install libwxgtk2.6-0
```
I suspect he needs to enable uni/multiverse too...

---

### Post by compwiz18 on 2006-11-20
> **Ago12 said:**
> Feature request: have multiple "prefered networks": when the app finds on of them, it connects automaticaly (for instnce to the stronger if there are two).

My personnal experience: At home, I connect to PLF (don't laugh :p), wich is wap-ed, and at school I connect to EBS or EBS1 (depending on the classroom), wich are open.

I would like to be able to set all these three ESSIDs as prefered, so wireless configuration becomes totally transparent (no need to start or click anything).


Thanks :)
As far as I know, you can.  Just click setup network, and the check the preferred network box for each network you would like to connect to automatically.

---

### Post by n3Cre0 on 2006-11-20
Just installed it on Xubuntu.

I open it (any way to have it launching by default?) and select scan.

It finds my WPA protected network (jipi) I configure it (give password etc) and hit connect.. but nothing changes :confused:

---

### Post by yopnono on 2006-11-20
> **n3Cre0 said:**
> Just installed it on Xubuntu.

I open it (any way to have it launching by default?) and select scan.

It finds my WPA protected network (jipi) I configure it (give password etc) and hit connect.. but nothing changes :confused:

Did you configure the WPA driver for your card under preferences.

---

### Post by n3Cre0 on 2006-11-20
Yes.

It's an atheros card so I put madwifi (and when nothing changed - wext).
It can also work for dhcp right

---

### Post by yopnono on 2006-11-20
> **n3Cre0 said:**
> Yes.

It's an atheros card so I put madwifi (and when nothing changed - wext).
It can also work for dhcp right

set it to madwifi close the application and start it again.
There seems to be a bug in it, have also seen this, if you add the driver and click connect = nothing. So I did close and open the program and it works.

---

### Post by n3Cre0 on 2006-11-20
Ok thnx when I have the chance I will try it out.

If there isn't a version +1 by then :)

I saw this thread evolving. It really looks nicer now :KS

---

### Post by compwiz18 on 2006-11-20
> **n3Cre0 said:**
> Ok thnx when I have the chance I will try it out.

If there isn't a version +1 by then :)

I saw this thread evolving. It really looks nicer now :KS
OK fixed that bug.

---

### Post by davebed on 2006-11-21
HELP!!
I installed v. 1.1 of connection manager, after fist removing network manager and wifi-radar. It worked oK, but now my GNOME panel is messed up. The whole desktop environment locks up when clicked by the mouse and all sorts of things are not as they were...

How can I rescue my GNOME environment? Can I re-configure or reinstall GNOME?

Thanks.

---

### Post by alchimera on 2006-11-21
> **davebed said:**
> HELP!!
I installed v. 1.1 of connection manager, after fist removing network manager and wifi-radar. It worked oK, but now my GNOME panel is messed up. The whole desktop environment locks up when clicked by the mouse and all sorts of things are not as they were...

How can I rescue my GNOME environment? Can I re-configure or reinstall GNOME?

Thanks.
This happens every time i install an upgraded version of Connection Manager!

Try rebooting your machine: <ctrl> + <alt> + <F1> takes you to a screen where you can logon (username,password as prompted) and then enter
```
sudo reboot
```Hope this helps.

---

### Post by yopnono on 2006-11-21
? > This happens every time i install an upgraded version of Connection Manager!

That have never happend for me.. yet.

@compwiz18  

Maybe you should add some feature to check if networks are up and running.
Something like this maybe. ```
ifconfig +interface+ up
```

Also if possible have the script create the .conf files in the opt/connection manager/data folder if they are deleted/missing.

Also if you add a link to the *manager* file in the opt/connetion folder at install to /usr/local/bin or /usr/bin 

Then the user can run it from terminal by typing ```
sudo manager
``` instead of first browse to the opt/... directory

---

### Post by compwiz18 on 2006-11-21
> **yopnono said:**
> ? 

That have never happend for me.. yet.

@compwiz18  

Maybe you should add some feature to check if networks are up and running.
Something like this maybe. ```
ifconfig +interface+ up
```

Also if possible have the script create the .conf files in the opt/connection manager/data folder if they are deleted/missing.

Also if you add a link to the *manager* file in the opt/connetion folder at install to /usr/local/bin or /usr/bin 

Then the user can run it from terminal by typing ```
sudo manager
``` instead of first browse to the opt/... directory
Fixed all these.  They'll be in the next release, along with the systray hopefully.

Quick poll: Would you rather have the main GUI require root to run, or be running a daemon in the background as root, so that you can just connect away without needing to enter your password?

---

### Post by yopnono on 2006-11-21
> **compwiz18 said:**
> Fixed all these.  They'll be in the next release, along with the systray hopefully.

Quick poll: Would you rather have the main GUI require root to run, or be running a daemon in the background as root, so that you can just connect away without needing to enter your password?

Great to see that you can fix all stuff :)

What is the benefit of having a daemon running in the background. Is it only so you don't have to enter the password?

If so, I can live without the daemon. Well how much will it use of ram etc,etc.

---

### Post by Ago12 on 2006-11-21
> **yopnono said:**
> Great to see that you can fix all stuff :)

What is the benefit of having a daemon running in the background. Is it only so you don't have to enter the password?

If so, **I can live without the daemon**. Well how much will it use of ram etc,etc.

So do I :)

---

### Post by compwiz18 on 2006-11-21
Ditto.  The main purpose is to be able to switch networks if a cable is plugged in automatically.  Or do you just want to have a button that says "click to connect to wired network"?

EDIT: I'm thinking that maybe having a "connect to wired" button is better because it gives the user more control, and we can lose the daemon...I've never used dbus before so it is an interesting challenge.

---

### Post by yopnono on 2006-11-21
> **compwiz18 said:**
> Ditto.  The main purpose is to be able to switch networks if a cable is plugged in automatically.  Or do you just want to have a button that says "click to connect to wired network"?

EDIT: I'm thinking that maybe having a "connect to wired" button is better because it gives the user more control, and we can lose the daemon...I've never used dbus before so it is an interesting challenge.

Yep, drop the daemon if you really don't need it, it's only more problems, to have stuff running unless you are in need of it.

---

### Post by compwiz18 on 2006-11-21
OK, the daemon is history.  Glad I hadn't started it yet :D  No more releases till I get the systray done, should be tomorrow my time.  I think that the systray won't be connected to my program, so that it can be used by people using XFCE as a signal monitor with a different program.

---

### Post by compwiz18 on 2006-11-21
I could use a set of 5 signal strength icons - each need to be 22x22 px.  I'm not a great artist, so if someone would like to make a few and post them, I'd be happy to use them.  Thanks!

edit: stealing them from a GPL program is legal too :P

---

### Post by yopnono on 2006-11-21
> **compwiz18 said:**
> I could use a set of 5 signal strength icons - each need to be 22x22 px.  I'm not a great artist, so if someone would like to make a few and post them, I'd be happy to use them.  Thanks!

edit: stealing them from a GPL program is legal too :P

Here icon from ubuntu / gnome
Resize them after need.

---

### Post by serlex on 2006-11-21
just tried it on university's wireless, can detech it but not connect to it. Here my settings i use to connect through Windows (intel ProSet).

Auth:WPA2-enterprise
Data Encriyption:AES-CCMP
Authentication type:TTLS
Authentication Protocol:PAP

---

### Post by marhp on 2006-11-21
Hi everyone I am new to Ubuntu coming over from Suse 9.0-10.1. I love this project. My issue is after updating to 1.1.0 when I reboot I get this error message "Internal error" "could not start HAL!. I am still able to use connection manager but it takes about 5 tries to connect. I am on a IBM thinkpad T42 with Ubuntu 6.10.

---

### Post by Ago12 on 2006-11-21
Hey, I have this problem to, didn't thought it was related to this :)

Anyway, I get rid of it by launching gnome-power-manager at startup...

But it is a dirty work-around :/

---

### Post by groggyboy on 2006-11-21
oooh!  a systray icon!

that was the last hurdle in the way for me.  i'm none too pleased with knetworkmanager at the moment, because kwallet has been screwing up, causing some issues with knetworkmanager not appearing in the kde systray.  i ended up disabling kwallet, which also then meant that knetworkmanager wouldn't automatically connect to my default profile at startup.

sounds promising.  as soon as you release the next version, i'll switch over.  i swear.

---

### Post by marhp on 2006-11-21
Hi could you post the dirty workaround. I am willing to try it.
Thanks

---

### Post by Ago12 on 2006-11-21
> **marhp said:**
> Hi could you post the dirty workaround. I am willing to try it.
Thanks

System > preferences > sessions > startup tasks (or something similar)
Add:
gnome-power-manager

:)

---

### Post by JohnUK89 on 2006-11-21
Hiya all,
Can anyone post the dependencies for connection-manager for me please? I cannot install until I remove network-manager, and that exact program is keeping me online. As youc an probably guess that stops me from downloading the dependencies :-x
Thanks,
John

---

### Post by marhp on 2006-11-21
Checked the System > prefrences > session and gnome-power-manager was there. In the Current session tab it was also there but under status was a ?. I tried to changed the status but it did not change.

---

### Post by Altrego on 2006-11-21
Where is the newest versin located? What server were you referring to?

---

### Post by marhp on 2006-11-21
The latest version is on the first thread.

---

### Post by compwiz18 on 2006-11-21
> **yopnono said:**
> Here icon from ubuntu / gnome
Resize them after need.
Awesome, thanks :D

I need to know how to add a program to the startup list for Gnome, KDE, and XFCE with a deb (or a terminal command).  This program can run as a normal user.  Thank you :D

---

### Post by wieman01 on 2006-11-21
As for **KDE** this is the path for startup scripts:
> ~/.kde/Autostart
Simply place a script there that runs your applet, that's it.

---

### Post by compwiz18 on 2006-11-21
So I take it there isn't a universal place that runs programs on Desktop startup?

---

### Post by wieman01 on 2006-11-21
Not, if you run the stuff on a (single) user level. However, if you want to run it for all users (graphical mode) you would have to run the program from...
> /etc/init.d/rc[COLOR="Red"]**5**[/COLOR]
These are the run levels for "init"...
> *  0 - Halt the system
    * 1 - Single-user mode
    * 2 - Multi-user mode (without NFS)
    * 3 - Multi-user mode
    * 5 - Multi-user mode, graphical login
    * 6 - Reboot the system
However, the boot logic has changed in Edgy... This only applies to Dapper and earlier versions of Ubuntu. Not sure how you'd do it in Edgy.

That said, since I believe you would want to run your program on a user level (no root authority required), you would have to have 3 different paths for each Desktop environment.

---

### Post by serlex on 2006-11-21
> **serlex said:**
> just tried it on university's wireless, can detect it but not connect to it. Here my settings i use to connect through Windows (intel ProSet).

Auth:WPA2-enterprise
Data Encryption: AES-CCMP
Authentication type:TTLS
Authentication Protocol:PAP

any help would be appreciated

---

### Post by compwiz18 on 2006-11-21
> **serlex said:**
> any help would be appreciated
Try editing /opt/connection-manager/data/wpa-settings.conf.  It uses the same syntax as wpa_supplicant, so if you read the wpa_supplicant man page, this should give you enough info to set it up.

---

### Post by compwiz18 on 2006-11-21
I've almost got the systray done, and I'm trying to make it load on Gnome boot.  However, the panel loads to slowly and the icon doesn't end up in the system tray.  Look at the left side of the screenshot, and you see the icon.  My system tray is on the right side.  Does anyone have any ideas as to how I can force it to wait to load until the panel is done loading?

---

### Post by wieman01 on 2006-11-21
> **serlex said:**
> any help would be appreciated
This is WPA-EAP... Network Manager won't help you much I reckon. I think it only supports WPA-PSK... Can somebody confirm that?

---

### Post by Peepsalot on 2006-11-21
Hello, I have a question about this program.  I have a laptop where I am trying to use NetworkManager at work, but I have problems connecting.  I believe there is some problem with NetowrkManager connecting to WEP enabled networks with SSID broadcasting disabled.
Would Connection Manager support this sort of connection?

---

### Post by marhp on 2006-11-21
> **marhp said:**
> Hi everyone I am new to Ubuntu coming over from Suse 9.0-10.1. I love this project. My issue is after updating to 1.1.0 when I reboot I get this error message "Internal error" "could not start HAL!. I am still able to use connection manager but it takes about 5 tries to connect. I am on a IBM thinkpad T42 with Ubuntu 6.10.


Update after doing some searching I know that the HAL error is NOT caused by this program. I now know that the error is from my HP Photosmart 3210 which I will be trying to figure out next.

---

### Post by compwiz18 on 2006-11-21
As of right now, Connection Manager doesn't support networks with SSID broadcasting disabled.  Check in for a future release.

---

### Post by yopnono on 2006-11-22
> **compwiz18 said:**
> I've almost got the systray done, and I'm trying to make it load on Gnome boot.  However, the panel loads to slowly and the icon doesn't end up in the system tray.  Look at the left side of the screenshot, and you see the icon.  My system tray is on the right side.  Does anyone have any ideas as to how I can force it to wait to load until the panel is done loading?

But how are you going to load it to the tray with a icon without a daemon?
Maybe you should create it as a panel applet, like the gnome network monitor.

That way the user can add it if they like, also it run as root but if you access the settings you need to enter the user/sudo password

And it want use any resources if not added/loaded.

---

### Post by yopnono on 2006-11-22
> **compwiz18 said:**
> As of right now, Connection Manager doesn't support networks with SSID broadcasting disabled.  Check in for a future release.

How about a if you can have a checkbox (hidden SSID) and if checked it would create a empty SSID in the config, would that work?

Then you enter all the stuff you need to access the network manually and connect.

EDIT added some more..

---

### Post by Ago12 on 2006-11-22
> **marhp said:**
> Update after doing some searching I know that the HAL error is NOT caused by this program. I now know that the error is from my HP Photosmart 3210 which I will be trying to figure out next.

Weird.

And since I have this problem I can't suspend any
more :/

And when I restart dbus, I get this:

> fabien@laptop:~$ sudo /etc/init.d/dbus restart
Password:
 * Stopping System Tools Backends system-tools-backends                  [ ok ] 
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [fail] 
 * Stopping DBUS aware dhcp client: dhcdbd                               [ ok ] 
 * Stopping Hardware abstraction layer hald                              [ ok ] 
 * Stopping system message bus dbus                                      [ ok ] 
 * Starting system message bus dbus                                      [ ok ] 
 * Starting Hardware abstraction layer hald                              [ ok ] 
 * Starting DBUS aware dhcp client: dhcdbd                               [ ok ] 
 * Starting System Tools Backends system-tools-backends                         run-parts: /etc/dbus-1/event.d/70system-tools-backends exited with return code 1


Bah?

---

### Post by yopnono on 2006-11-22
> **Ago12 said:**
> Weird.

And since I have this problem I can't suspend any
more :/

And when I restart dbus, I get this:



Bah?

Please don't use this or any other thread to ask for problems that are not related to the thread.

Connection manager can't have anything to do with HAL. This application is only a GUI for a python script that uses iwlist, wpa_supplicant etc.

It don't use HAL in that manner, unless there is some hidden stuff that I don't find in the script.

---

### Post by yopnono on 2006-11-22
@compwiz18

It might be better/easier to have one version for each desktop
One for Gnome with tray icon
One for KDE with tray icon
One for XFCE with tray icon

And maybe one without the tray icon stuff, that will run on all, like today.

Since it's seems that KDE using different startup locations from Gnome etc,etc.

---

### Post by Ago12 on 2006-11-22
> **yopnono said:**
> Please don't use this or any other thread to ask for problems that are not related to the thread.

**Connection manager can't have anything to do with HAL**. This application is only a GUI for a python script that uses iwlist, wpa_supplicant etc.

It don't use HAL in that manner, unless there is some hidden stuff that I don't find in the script.

Ok, I'll see in an other place :)

---

### Post by compwiz18 on 2006-11-22
OK, I posted the version with the systray.  It doesn't start the systray automatically at boot, you must add **connection-manager-systray** to your list of startup programs.

---

### Post by Azathoth_ on 2006-11-22
Hi, I havge problems when i try to connect to a network is far or i have incorrect MAC. The program kills and i have to force quit.
Good program

---

### Post by compwiz18 on 2006-11-22
Tada! The systray is released!  Use 1.2.1 for the newest and bestest version.  You will have to manually add **connection-manager-systray** to your list of startup programs for your window manager, as there are far to many window managers for me to try and add it automatically.  If you are using Gnome, go to System -> Preferences -> Sessions, click the Startup Programs tab, and add **connection-manager-systray**. I don't use XFCE or KDE, so if someone else could post instructions for those...

PS: To all the programmers out there:
Version 1.2.0 and 1.2.1 are identical (functionality-wise), except that the systray in 1.2.1 uses pyGTK instead of wxPython.  wxPython has a bug in the systray that doesn't allow it to load well at boot, so I switched the language in it to pyGTK, which does not have the bug.

---

### Post by McDuff on 2006-11-22
i just installed v 1.2.1.
dialogues don't open, when clicking on "settings" and "setup network".

do you think it would be possible to include wpa support for ralink wireless devices? it would be great, as at the moment, there is no gui way to setup wpa with those.

Edit: nothing happens when clicking on the systray icon. is this intended to be?

---

### Post by alchimera on 2006-11-22
After installing 1.2.1 the systray works ok, but the "setup network" and "preferences" no longer work.  Outputs:
```
link clicked: py:preferences(0)
Traceback (most recent call last):
  File "/opt/connection-manager/manager", line 39, in OnLinkClicked
    self.parent.LinkClicked(linkinfo.GetHref())
  File "/opt/connection-manager/manager", line 222, in LinkClicked
    prefframe = NetworkPreferences(None,str(self.scan_data[int(href)]['essid']))
  File "/opt/connection-manager/manager", line 442, in __init__
    conf.readfp( open( self.network_conf,"r" ) )
AttributeError: 'NetworkPreferences' object has no attribute 'network_conf'
```and
```
Traceback (most recent call last):
  File "/opt/connection-manager/manager", line 146, in ShowAppPreferences
    confframe = AppPreferences(self)
  File "/opt/connection-manager/manager", line 312, in __init__
    conf.readfp( open( self.app_conf,"r" ) )
AttributeError: 'AppPreferences' object has no attribute 'app_conf'

```resp.

---

### Post by yopnono on 2006-11-22
yep ver 1.21 is a little broken :)

---

### Post by compwiz18 on 2006-11-22
> **yopnono said:**
> yep ver 1.21 is a little broken :)
and version 1.2.2 is a little fixed :D

---

### Post by yopnono on 2006-11-22
Nope it's even more broken. It want start, I did a clean install after I remove all old files. 

And running from terminal it only say not network interface in config file.

The tray icon, what will it do. Is it only to show the signal. If so then it's not needed in gnome, since you have the gnome network applet that shows the signal.

And the tray icon uses somewhere around 18-20mb of ram.

Also the ver 121 don't tell you if the network is encrypted or not.

That's it for now.. I guess ;) 

PS: nice work with the icons

---

### Post by alchimera on 2006-11-22
:-D Yup, 1.2.2 works fine.

---

### Post by yopnono on 2006-11-22
> **alchimera said:**
> :-D Yup, 1.2.2 works fine.

Does it work if you do I clean install? Make sure that you remove all files/folder from the connect-manager.

---

### Post by alchimera on 2006-11-22
Well, i select "completely remove" in synaptic before installing an updated version, but i guess that this doesn't get it all out as it retains the static IP/DNS settings that i set a while back.

Do you suggest that i go looking for any residual directories after removing the package? Am willing to have a go, but i would need to know where to look!

---

### Post by yopnono on 2006-11-22
> **alchimera said:**
> Well, i select "completely remove" in synaptic before installing an updated version, but i guess that this doesn't get it all out as it retains the static IP/DNS settings that i set a while back.

Do you suggest that i go looking for any residual directories after removing the package? Am willing to have a go, but i would need to know where to look!

No in the /opt folder you have the connection-manager folder, if you remove that after uninstall. 
Then more and less all files are gone except one from the py script in /usr/etc....

But leaving that last one is ok. So yes, if you can, then please remove the connection manager folder in /opt. And try again.

---

### Post by alchimera on 2006-11-22
> **yopnono said:**
> No in the /opt folder you have the connection-manager folder, if you remove that after uninstall. 
Then more and less all files are gone except one from the py script in /usr/etc....

But leaving that last one is ok. So yes, if you can, then please remove the connection manager folder in /opt. And try again.
Have done as you suggest: "sudo rm -r /opt/connection-manager" (after selecting "complete removal" in synaptic) and checked that it was gone...

After reinstall of 1.2.2, all in working order - in fact it has picked up a driver for WPA (in the "preferences" dialog) which was not there before :-D but still getting the python warnings  about incomplete entries in etc/mailcap :-?.

---

### Post by yopnono on 2006-11-22
> **alchimera said:**
> Have done as you suggest: "sudo rm -r /opt/connection-manager" (after selecting "complete removal" in synaptic) and checked that it was gone...

After reinstall of 1.2.2, all in working order - in fact it has picked up a driver for WPA (in the "preferences" dialog) which was not there before :-D but still getting the python warnings  about incomplete entries in etc/mailcap :-?.

Ok I did install it again. And this time it start, but... it don't connet to my WPA network, it don't create the wpasupplicant.conf file.

The problem before when it didn't not open the first time, was because I killed all dhclient and dhcdbd. This don't happen on ver 1.1.3.


Anyhow kan you please try this again and this time also ```
sudo killall wpa_supplicant
``` and try, also if you have time and all that :) try again after you have killed all dhclient and dhcdbd.

---

### Post by yopnono on 2006-11-22
Here is some more stuff. If I try to open the tray icon I get this.

```
connection-manager-systray
Traceback (most recent call last):
  File "/opt/connection-manager/systray", line 76, in ?
    systray = systray(app_conf)
  File "/opt/connection-manager/systray", line 39, in __init__
    self.statusicon = gtk.StatusIcon()
AttributeError: 'module' object has no attribute 'StatusIcon'
```

---

### Post by foxy123 on 2006-11-22
> **yopnono said:**
> Here is some more stuff. If I try to open the tray icon I get this.

```
connection-manager-systray
Traceback (most recent call last):
  File "/opt/connection-manager/systray", line 76, in ?
    systray = systray(app_conf)
  File "/opt/connection-manager/systray", line 39, in __init__
    self.statusicon = gtk.StatusIcon()
AttributeError: 'module' object has no attribute 'StatusIcon'
```

I've got the same error.

---

### Post by compwiz18 on 2006-11-22
I think it is a dependency problem...you need pyGTK installed.

Try **sudo apt-get install python-gtk2**.  If that doesn't work, also run **sudo apt-get install python-gtk2-dev**.  If that doesn't help, post me a message.

---

### Post by mssever on 2006-11-22
> **compwiz18 said:**
> I think it is a dependency problem...you need pyGTK installed.

Try **sudo apt-get install python-gtk2**.  If that doesn't work, also run **sudo apt-get install python-gtk2-dev**.  If that doesn't help, post me a message.
If its a deendency issue, shouldnt it be listed in the deb as a deendency

---

### Post by handaxe on 2006-11-22
Hi, good progress - so thanks.

Have same issue but gtk is installed

```
 royden@rylaptop:~$ connection-manager-systray
Traceback (most recent call last):
  File "/opt/connection-manager/systray", line 76, in ?
    systray = systray(app_conf)
  File "/opt/connection-manager/systray", line 39, in __init__
    self.statusicon = gtk.StatusIcon()
AttributeError: 'module' object has no attribute 'StatusIcon'
```HA

Edit: the gtk dev package is not installed - it should not ideally be a dependency??

Also, I can confirm groggyboy's account re wpa_supplicant.conf

---

### Post by groggyboy on 2006-11-22
in KDE, to get the systray applet to autoload at boot, create a symlink of /opt/connection-manager/systray in this folder: /home/<username>/.kde/autostart/

it works, but I can't say it looks very pretty - being a gtk app and all:p !
the icon has a white box around it, making it stick out on my black kicker panel.  also, the main window uses gtk-style buttons.  it's not something you should worry about - you've made a great app as is, but i hope someone decides to give this a kde-native interface some day!

i had one issue setting it up: at first, nothing happened when I tried to connect to my wireless network - the "connecting" progress bar would cycle infinitely, until I realized it was looking for /opt/connection-manager/data/wpa_supplicant.conf - i created a new blank file and it works fine.

---

### Post by compwiz18 on 2006-11-22
> **mssever said:**
> If its a deendency issue, shouldnt it be listed in the deb as a deendency
It will be as soon as I figure out what it needs to install...I don't know the name of the dependency.

If someone could help me out here...

---

### Post by compwiz18 on 2006-11-22
> **groggyboy said:**
> in KDE, to get the systray applet to autoload at boot, create a symlink of /opt/connection-manager/systray in this folder: /home/<username>/.kde/autostart/

Thanks, I added this to the front page.

> **groggyboy said:**
> 
it works, but I can't say it looks very pretty - being a gtk app and all:p !
the icon has a white box around it, making it stick out on my black kicker panel.

:-? I don't know about that...I'll install KDE and take a look at it.

> **groggyboy said:**
> 
also, the main window uses gtk-style buttons.  it's not something you should worry about - you've made a great app as is, but i hope someone decides to give this a kde-native interface some day!


I can't help you there other then to say use Gnome :P  Maybe one day if I'm bored I'll remake it with QT.

> **groggyboy said:**
> 
i had one issue setting it up: at first, nothing happened when I tried to connect to my wireless network - the "connecting" progress bar would cycle infinitely, until I realized it was looking for /opt/connection-manager/data/wpa_supplicant.conf - i created a new blank file and it works fine.

All fixed :D

---

### Post by compwiz18 on 2006-11-22
> **handaxe said:**
> Hi, good progress - so thanks.

Have same issue but gtk is installed

```
 royden@rylaptop:~$ connection-manager-systray
Traceback (most recent call last):
  File "/opt/connection-manager/systray", line 76, in ?
    systray = systray(app_conf)
  File "/opt/connection-manager/systray", line 39, in __init__
    self.statusicon = gtk.StatusIcon()
AttributeError: 'module' object has no attribute 'StatusIcon'
```HA

Edit: the gtk dev package is not installed - it should not ideally be a dependency??

Also, I can confirm groggyboy's account re wpa_supplicant.conf
Yeah, ideally this would not be a dependency.  However, I don't know the name of the package that is required for this to work...

---

### Post by compwiz18 on 2006-11-22
> **mssever said:**
> If its a deendency issue, shouldnt it be listed in the deb as a deendency
Try installing python-gnome2-desktop with apt or Synaptic, this may be the missing dependency.

---

### Post by handaxe on 2006-11-23
> **compwiz18 said:**
> Try installing python-gnome2-desktop with apt or Synaptic, this may be the missing dependency.


Done this as well as installed python-gtk2 and python-gtk2-dev. The error remains the same.

The error suggests something missing in the code, rather than a missing library. But I confess that is not an informed opinion...

Thanks for the work, this is already a very useful tool.

HA

---

### Post by compwiz18 on 2006-11-23
> **handaxe said:**
> Done this as well as installed python-gtk2 and python-gtk2-dev. The error remains the same.

The error suggests something missing in the code, rather than a missing library. But I confess that is not an informed opinion...

Thanks for the work, this is already a very useful tool.

HA
Hmm...cause it works fine on my computer...so something is missing on yours I guess...but again, I'm not great at this either...gah.  I hate dependencies.  What version of python-gtk2 do you have and are you running Dapper or Edgy?

---

### Post by handaxe on 2006-11-23
> **compwiz18 said:**
> Hmm...cause it works fine on my computer...so something is missing on yours I guess...but again, I'm not great at this either...gah.  I hate dependencies.  What version of python-gtk2 do you have and are you running Dapper or Edgy?

Well that settls the code issue.

I am on dapper, with the stock python2.4-gtk2 v2.8.6

HA

---

### Post by foxy123 on 2006-11-23
I've got also all python-gtk2 packages in stalled on Dapper and still got this error.

Regarding the decision not to go ahead with a daemon. Does it mean the the connection-manager will not be able to detect and connect to wired/wireless connections automatically? For example now if I unplug my Ethernet cable, nothing happens, the connection does not switch to wireless and vice versa.

I guess I missed the discussion.

---

### Post by compwiz18 on 2006-11-23
> **foxy123 said:**
> I've got also all python-gtk2 packages in stalled on Dapper and still got this error.

Regarding the decision not to go ahead with a daemon. Does it mean the the connection-manager will not be able to detect and connect to wired/wireless connections automatically? For example now if I unplug my Ethernet cable, nothing happens, the connection does not switch to wireless and vice versa.

I guess I missed the discussion.
Yep, you have to manually switch wired/wireless.  Next release will have the ability to configure a wired interface, but this will have to be done manually.  I suppose I could still rewrite it to use a daemon...if people want.

As for those dependencies...BLAH.  Has anyone running Edgy tried it yet?

---

### Post by yopnono on 2006-11-23
> **compwiz18 said:**
> Yep, you have to manually switch wired/wireless.  Next release will have the ability to configure a wired interface, but this will have to be done manually.  I suppose I could still rewrite it to use a daemon...if people want.

As for those dependencies...BLAH.  Has anyone running Edgy tried it yet?

If you truly need a tray icon, then in gnome go for an panel-applet.
But as I stated earlier, if it's only for the signal meter.. then you have the gnome-network-applet.

Also I do think you probably going to find it easier to create different packages for each desktop.

Just keep it simple. :)

---

### Post by foxy123 on 2006-11-23
> **compwiz18 said:**
> Yep, you have to manually switch wired/wireless.  Next release will have the ability to configure a wired interface, but this will have to be done manually.  I suppose I could still rewrite it to use a daemon...if people want.

As for those dependencies...BLAH.  Has anyone running Edgy tried it yet?

thanks a lot. What are you running? Dapper or Edgy? There were certain changes in python packages between them.

---

### Post by compwiz18 on 2006-11-23
I'm running Edgy...I suspect this is where the problem lies.  I tested it out on my other Edgy box, and didn't have this problem.

[QUOTE=the pyGTK Reference Manual]gtk.StatusIcon - display an icon in the system tray (new in PyGTK 2.10)[/QUOTE]

This is perhaps the problem?

edit:

[QUOTE=the Dapper package website]python-gtk2 (2.8.6-0ubuntu1)[/QUOTE]

We found our problem.  This doesn't work in Dapper.

---

### Post by compwiz18 on 2006-11-23
> **yopnono said:**
> If you truly need a tray icon, then in gnome go for an panel-applet.
But as I stated earlier, if it's only for the signal meter.. then you have the gnome-network-applet.

Also I do think you probably going to find it easier to create different packages for each desktop.

Just keep it simple. :)
Yeah, this is getting complicated...what do you think about making the systray a seperate deb.  This way we can keep one package for all, and maintain the systray deb seperately?

---

### Post by foxy123 on 2006-11-23
> **compwiz18 said:**
> I'm running Edgy...I suspect this is where the problem lies.  I tested it out on my other Edgy box, and didn't have this problem.



This is perhaps the problem?

edit:



We found our problem.  This doesn't work in Dapper.
is there any chance to have a Dapper version?

---

### Post by yopnono on 2006-11-23
> **compwiz18 said:**
> Yeah, this is getting complicated...what do you think about making the systray a seperate deb.  This way we can keep one package for all, and maintain the systray deb seperately?

Yep. Like you said, it getting complicated. 
Yes why not. Sounds like a good idea, to have them separated.

PS: Was it possible to ha a dropdown menu for different WPA drivers, like ipw,madwifi,wext,etc. 

I think that would be easier for the user if they can select the WPA drivers from a dropdown menu, and also if needed be able to type the driver manually.

---

### Post by compwiz18 on 2006-11-23
> **foxy123 said:**
> is there any chance to have a Dapper version?
um...maybe.  Maybe I'll write in QT to make all the KDE people out there happy.

And the fact that wxWidgets doesn't load tray icons right, pyGTK doesn't work in Dapper.  I'm running out of widget sets here...

---

### Post by compwiz18 on 2006-11-23
> **yopnono said:**
> Yep. Like you said, it getting complicated. 
Yes why not. Sounds like a good idea, to have them separated.

PS: Was it possible to ha a dropdown menu for different WPA drivers, like ipw,madwifi,wext,etc. 

I think that would be easier for the user if they can select the WPA drivers from a dropdown menu, and also if needed be able to type the driver manually.
Yeah, I'll add the dropdown.

> 
hostap
hermes
madwifi
atmel
wext
broadcom
ipw
wired
bsd
ndis


Will be the options available, plus a custom option with a text box for your own entry?

Also, I'm going to make this version able to configure wired interfaces.  However, there is no way to figure out what location we are at, so the user will be required to input static ips/static dns every time, am I correct?

---

### Post by yopnono on 2006-11-23
> Also, I'm going to make this version able to configure wired interfaces. However, there is no way to figure out what location we are at, so the user will be required to input static ips/static dns every time, am I correct?

Do you meen that the wired will not work with DHCP?

---

### Post by compwiz18 on 2006-11-23
No, wired will work with DHCP (it does now, in fact).  I'm going to add the option to use static ips to though, and I was just curious if there was a way to figure out what network you are plugged into.

---

### Post by yopnono on 2006-11-23
> **compwiz18 said:**
> No, wired will work with DHCP (it does now, in fact).  I'm going to add the option to use static ips to though, and I was just curious if there was a way to figure out what network you are plugged into.

Everything can be done but why make it harder then it need to be?
You can have some kind of profiles for different networks.

That the user setup, then they can just select the profile they like to use and connect to.

---

### Post by Ryanmt on 2006-11-23
I just installed it and it looks like it was working fine but said no networks found. 

I went to preferences and changed the driver to wlan0 and now it just freezes when trying to scan the network. Since it does this as soon as the app is loaded then i dont know what to do as i cant change it back. Im using zd1211 drivers if that makes any difference?

Traceback (most recent call last):
  File "/opt/connection-manager/manager", line 647, in ?
    frame = Main(None,app_conf,network_conf,wpa_conf)
  File "/opt/connection-manager/manager", line 143, in __init__
    self.UpdateNetworkList()
  File "/opt/connection-manager/manager", line 230, in UpdateNetworkList
    self.scan_data = self.wifi.scan(self.interface)
  File "/usr/lib/python2.4/networking.py", line 50, in scan
    aps[ i ]['signal'] = strength
UnboundLocalError: local variable 'strength' referenced before assignment

```
[CODE]ryanmt@penguin:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:24:C9:C2:20
                    ESSID:"ISD"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Extra:SignalStrength=78%,LinkQuality:28%
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:13:C3:44:FB:90
                    ESSID:"ISD"
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Extra:SignalStrength=61%,LinkQuality:28%
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:0F:24:FD:4F:00
                    ESSID:"ISD"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Extra:SignalStrength=47%,LinkQuality:28%
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

sit0      Interface doesn't support scanning.

ryanmt@penguin:~$ 

```=

---

### Post by foxy123 on 2006-11-23
> **compwiz18 said:**
> um...maybe.  Maybe I'll write in QT to make all the KDE people out there happy.

And the fact that wxWidgets doesn't load tray icons right, pyGTK doesn't work in Dapper.  I'm running out of widget sets here...

Do you really need to use a newer version of pyGTK?

I tried to backport pyGTK from Edgy but ran into too many dependencies.

---

### Post by yopnono on 2006-11-23
The WPA driver whould not be wlan0 that is the interface.
Should you not be using something like *zydas* as driver.

In /opt/connection-manager/data you have the settings

---

### Post by pkastro on 2006-11-23
1.2.2 download link is broken.. anyone have another location?

---

### Post by compwiz18 on 2006-11-23
> **pkastro said:**
> 1.2.2 download link is broken.. anyone have another location?
its back now...my server ran out of HDD space.

---

### Post by compwiz18 on 2006-11-23
> **Ryanmt said:**
> I just installed it and it looks like it was working fine but said no networks found. 

I went to preferences and changed the driver to wlan0 and now it just freezes when trying to scan the network. Since it does this as soon as the app is loaded then i dont know what to do as i cant change it back. Im using zd1211 drivers if that makes any difference?

Traceback (most recent call last):
  File "/opt/connection-manager/manager", line 647, in ?
    frame = Main(None,app_conf,network_conf,wpa_conf)
  File "/opt/connection-manager/manager", line 143, in __init__
    self.UpdateNetworkList()
  File "/opt/connection-manager/manager", line 230, in UpdateNetworkList
    self.scan_data = self.wifi.scan(self.interface)
  File "/usr/lib/python2.4/networking.py", line 50, in scan
    aps[ i ]['signal'] = strength
UnboundLocalError: local variable 'strength' referenced before assignment

```
[CODE]ryanmt@penguin:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:24:C9:C2:20
                    ESSID:"ISD"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Extra:SignalStrength=78%,LinkQuality:28%
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:13:C3:44:FB:90
                    ESSID:"ISD"
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Extra:SignalStrength=61%,LinkQuality:28%
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:0F:24:FD:4F:00
                    ESSID:"ISD"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Extra:SignalStrength=47%,LinkQuality:28%
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

sit0      Interface doesn't support scanning.

ryanmt@penguin:~$ 

```=
What model is your card?

edit: nvm, reread your post

---

### Post by compwiz18 on 2006-11-23
Can anyone tell me how I can remove an entry from route?  I can't quite seem to do it with **sudo route del [insert something here]**...probably just me.

---

### Post by Papa-san on 2006-11-23
I personally know absolutely NOTHING about coding and all the other background parts of this OS, but I can add a testimony here...

I have a Dell C-610 with the infamous bcm43XX.

I have had nothing but struggles with my wireless since I first formatted over my winXP. I tried every tutorial and how-to I could find, and finally managed to get it to work somewhat reliably in Breezy. Once I upgraded to Dapper, I had to go through the same thing all over again, but it was slightly different. Dapper never fully worked for me because of resolution issues causing hard crashes several times a day. When I went to edgy, I couldn't even get it to pretend to play nice!

So, I re-formatted and put Breezy back on. I have my bcmwl5.inf and .sys saved on my offsite server, so finding them isn't an issue. I used the most basic ndiswrapper install, and it worked, but would lose the lease after a few minutes, and I had to re-boot to be able to get it back.

Then I stumbled upon this thread...(@ 1.2.2)

Installed without a hitch! Found my dependencies with no hiccups. Then, when I ran the program, it worked exactly as it was supposed to, and kept my connection open for a day and a half! (This is when I turned my lappy off...) Upon re-starting it, I simply opened the 'Connection Manager GUI and clicked connect... Now I am writing on my wireless! That quick and easy...
Thank you, Thank you, THANK YOU!!!

:D

---

### Post by pkastro on 2006-11-23
> **compwiz18 said:**
> Can anyone tell me how I can remove an entry from route?  I can't quite seem to do it with **sudo route del [insert something here]**...probably just me.

its still down lol.

---

### Post by compwiz18 on 2006-11-23
> **pkastro said:**
> its still down lol.
it was up. but something went haywire and ate the entire disk up, so I'm gonna track it down, free some disk space, and then you will be able to use it again.

---

### Post by compwiz18 on 2006-11-23
> **compwiz18 said:**
> it was up. but something went haywire and ate the entire disk up, so I'm gonna track it down, free some disk space, and then you will be able to use it again.
OK, server is back.  For some reason cupsys went out of control and wrote 7.1GB of logs to my HDD (which is only 20GB) and filled it up...

---

### Post by compwiz18 on 2006-11-23
OK, I've fixed that.  The only problem will be that Connection Manager will not show the signal strength of your networks - it will always report -1.  Connection Manager needs the signal strength in dBm, and your card only reports the strength in percent - maybe in a future version I will convert Connection Manager to use percents, but for now it uses dBm to judge signal strength.

---

### Post by NetworkGuy on 2006-11-23
Hi CompWiz18

I'm trying your connection manager program out.  I hope it can do the trick since I can not get either wifi-radar or network manager to work. 

I'm using a ACX111 chipset card and the program freezes while scanning.  I did change the manager.conf file to use wlan0 interface since it was not detecting that earlier.  The output from the program is:

```
NetworkGuy@R40-laptop:/opt/connection-manager/data$ gksudo -S /opt/connection-manager/manager
wlan0
Traceback (most recent call last):
  File "/opt/connection-manager/manager", line 647, in ?
    frame = Main(None,app_conf,network_conf,wpa_conf)
  File "/opt/connection-manager/manager", line 143, in __init__
    self.UpdateNetworkList()
  File "/opt/connection-manager/manager", line 230, in UpdateNetworkList
    self.scan_data = self.wifi.scan(self.interface)
  File "/usr/lib/python2.4/networking.py", line 50, in scan
    aps[ i ]['signal'] = strength
UnboundLocalError: local variable 'strength' referenced before assignment
```

And the output from a iwlist scan is:
```
NetworkGuy@R40-laptop:/opt/connection-manager/data$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:16:B6:49:B7:DA
                    ESSID:"Imagination"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/100  Signal level=33/100  Noise level=0/100
                    Encryption key:off
                    Bit Rates:54 Mb/s
          Cell 02 - Address: 00:E0:98:F1:05:85
                    ESSID:"05B405331427"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/100  Signal level=3/100  Noise level=0/100
                    Encryption key:off
                    Bit Rates:54 Mb/s
          Cell 03 - Address: 00:E0:98:FF:13:63
                    ESSID:""
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/100  Signal level=4/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 04 - Address: 00:12:17:6F:F2:CE
                    ESSID:"myhouse"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/100  Signal level=3/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 05 - Address: 00:14:6C:3F:BE:12
                    ESSID:"suzi"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/100  Signal level=3/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 06 - Address: 00:18:39:48:A7:27
                    ESSID:"mshome"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/100  Signal level=4/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 07 - Address: 00:0F:66:77:3C:94
                    ESSID:"myhouse"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/100  Signal level=4/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:54 Mb/s

```

I am using the native driver with the 1.2.1.34 version of the firmware set in the kernel.  

BTW - I use cell 01

---

### Post by pkastro on 2006-11-23
Error :(

I have a broadcom card, followed every instruction and cant seem to get this POS card to work. :(


astro@laptop:~$ sudo connection-manager
eth1
0
1
2
3
4
link clicked: py:preferences(0)
link clicked: py:connect(0)
{'encryption': 'on', 'signal': '-57', 'ap_mac': '00:11:50:D4:7F:AC', 'mode': 'Managed', 'channel': '11', 'essid': 'lewis'}
interface1: eth1
interface: eth1
killing previous wpa supps
wpa_supplicant: no process killed
Exception in thread Thread-3:
Traceback (most recent call last):
  File "threading.py", line 442, in __bootstrap
    self.run()
  File "/opt/connection-manager/manager", line 592, in run
    self.wifi.connect(self.interface,self.essid,self.channel,self.mode,self.ap_mac,self.enctype,self.key,self.wpa_driver,self.ip,self.gateway,self.subnet,self.dns1,self.dns2)
  File "/usr/lib/python2.4/networking.py", line 105, in connect
    f = open ( "/opt/connection-manager/data/wpa_supplicant.conf")
IOError: [Errno 2] No such file or directory: '/opt/connection-manager/data/wpa_supplicant.conf'

---

### Post by compwiz18 on 2006-11-23
Run **touch /opt/connection-manager/data/wpa_supplicant.conf** in a Terminal, then try to start it.

---

### Post by pkastro on 2006-11-23
im a moron how the hell did I not remember to do that lol.

---

### Post by pkastro on 2006-11-23
OK So I Think I am having a problem with WPA or something. THe program SEEMS to work but I just cant get a connection. Perhaps I'm using the wrong driver for WPA or something, I'm unsure. I know hardly nothing about Linux and even less about WPA and such. Any ideas? or should I find a different place to post.

---

### Post by compwiz18 on 2006-11-23
This is the place.  Can you do what you did earlier and post the output from the program when you run it via the terminal?  I'll see if I can help you.

---

### Post by pkastro on 2006-11-23
Here is what happens when I try it via terminal.

> astro@laptop:~$ sudo /opt/connection-manager/manager 
eth1
0
1
2
3
link clicked: py:connect(0)
{'encryption': 'on', 'signal': '-59', 'ap_mac': '00:11:50:D4:7F:AC', 'mode': 'Managed', 'channel': '11', 'essid': 'lewis'}
interface1: eth1
interface: eth1
killing previous wpa supps
running wpa supp
wpa_supplicant -B -i eth1 -c /opt/connection-manager/data/wpa_supplicant.conf -D ndiswrapper
iwconfig eth1 mode Managed
iwconfig eth1 essid "lewis" channel 11 ap 00:11:50:D4:7F:AC
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; Invalid argument.
configuring dhcp
There is already a pid file /var/run/dhclient.pid with pid 16748
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:14:a5:1f:2f:fb
Sending on   LPF/eth1/00:14:a5:1f:2f:fb
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
Trying recorded lease 192.168.2.2
No working leases in persistent database - sleeping.
done




IT just hands and hangs and hangs. I don't know whats going on.

---

### Post by compwiz18 on 2006-11-24
Try using WPA drive "wext"...this might fix your problem.

---

### Post by compwiz18 on 2006-11-24
[SIZE="5"]Version 1.3.0 is released!  Now support for wired networks is included - but only DHCP for now.[/SIZE]

Fixed stuff is below:

> **Ryanmt said:**
> I just installed it and it looks like it was working fine but said no networks found. 

I went to preferences and changed the driver to wlan0 and now it just freezes when trying to scan the network. Since it does this as soon as the app is loaded then i dont know what to do as i cant change it back. Im using zd1211 drivers if that makes any difference?

Traceback (most recent call last):
  File "/opt/connection-manager/manager", line 647, in ?
    frame = Main(None,app_conf,network_conf,wpa_conf)
  File "/opt/connection-manager/manager", line 143, in __init__
    self.UpdateNetworkList()
  File "/opt/connection-manager/manager", line 230, in UpdateNetworkList
    self.scan_data = self.wifi.scan(self.interface)
  File "/usr/lib/python2.4/networking.py", line 50, in scan
    aps[ i ]['signal'] = strength
UnboundLocalError: local variable 'strength' referenced before assignment

```
[CODE]ryanmt@penguin:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:24:C9:C2:20
                    ESSID:"ISD"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Extra:SignalStrength=78%,LinkQuality:28%
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:13:C3:44:FB:90
                    ESSID:"ISD"
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Extra:SignalStrength=61%,LinkQuality:28%
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:0F:24:FD:4F:00
                    ESSID:"ISD"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Extra:SignalStrength=47%,LinkQuality:28%
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

sit0      Interface doesn't support scanning.

ryanmt@penguin:~$ 

```=

**Fixed.**

> **compwiz18 said:**
> OK, I've fixed that.  The only problem will be that Connection Manager will not show the signal strength of your networks - it will always report -1.  Connection Manager needs the signal strength in dBm, and your card only reports the strength in percent - maybe in a future version I will convert Connection Manager to use percents, but for now it uses dBm to judge signal strength.

**Never mind that, I switched it now, so it should play nicely with your card.**

> **NetworkGuy said:**
> Hi CompWiz18

I'm trying your connection manager program out.  I hope it can do the trick since I can not get either wifi-radar or network manager to work. 

I'm using a ACX111 chipset card and the program freezes while scanning.  I did change the manager.conf file to use wlan0 interface since it was not detecting that earlier.  The output from the program is:

```
NetworkGuy@R40-laptop:/opt/connection-manager/data$ gksudo -S /opt/connection-manager/manager
wlan0
Traceback (most recent call last):
  File "/opt/connection-manager/manager", line 647, in ?
    frame = Main(None,app_conf,network_conf,wpa_conf)
  File "/opt/connection-manager/manager", line 143, in __init__
    self.UpdateNetworkList()
  File "/opt/connection-manager/manager", line 230, in UpdateNetworkList
    self.scan_data = self.wifi.scan(self.interface)
  File "/usr/lib/python2.4/networking.py", line 50, in scan
    aps[ i ]['signal'] = strength
UnboundLocalError: local variable 'strength' referenced before assignment
```

And the output from a iwlist scan is:
```
NetworkGuy@R40-laptop:/opt/connection-manager/data$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:16:B6:49:B7:DA
                    ESSID:"Imagination"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/100  Signal level=33/100  Noise level=0/100
                    Encryption key:off
                    Bit Rates:54 Mb/s
          Cell 02 - Address: 00:E0:98:F1:05:85
                    ESSID:"05B405331427"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/100  Signal level=3/100  Noise level=0/100
                    Encryption key:off
                    Bit Rates:54 Mb/s
          Cell 03 - Address: 00:E0:98:FF:13:63
                    ESSID:""
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/100  Signal level=4/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 04 - Address: 00:12:17:6F:F2:CE
                    ESSID:"myhouse"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/100  Signal level=3/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 05 - Address: 00:14:6C:3F:BE:12
                    ESSID:"suzi"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/100  Signal level=3/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 06 - Address: 00:18:39:48:A7:27
                    ESSID:"mshome"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/100  Signal level=4/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 07 - Address: 00:0F:66:77:3C:94
                    ESSID:"myhouse"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/100  Signal level=4/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:54 Mb/s

```

I am using the native driver with the 1.2.1.34 version of the firmware set in the kernel.  

BTW - I use cell 01

**I fixed this too, your card now is supported.**

> **pkastro said:**
> Error :(

I have a broadcom card, followed every instruction and cant seem to get this POS card to work. :(


astro@laptop:~$ sudo connection-manager
eth1
0
1
2
3
4
link clicked: py:preferences(0)
link clicked: py:connect(0)
{'encryption': 'on', 'signal': '-57', 'ap_mac': '00:11:50:D4:7F:AC', 'mode': 'Managed', 'channel': '11', 'essid': 'lewis'}
interface1: eth1
interface: eth1
killing previous wpa supps
wpa_supplicant: no process killed
Exception in thread Thread-3:
Traceback (most recent call last):
  File "threading.py", line 442, in __bootstrap
    self.run()
  File "/opt/connection-manager/manager", line 592, in run
    self.wifi.connect(self.interface,self.essid,self.channel,self.mode,self.ap_mac,self.enctype,self.key,self.wpa_driver,self.ip,self.gateway,self.subnet,self.dns1,self.dns2)
  File "/usr/lib/python2.4/networking.py", line 105, in connect
    f = open ( "/opt/connection-manager/data/wpa_supplicant.conf")
IOError: [Errno 2] No such file or directory: '/opt/connection-manager/data/wpa_supplicant.conf'

**The .deb now takes care of fixing this on installation.**

---

### Post by pkastro on 2006-11-24
> **compwiz18 said:**
> Try using WPA drive "wext"...this might fix your problem.

no dice :( didn't give me an error but didn't connect

---

### Post by compwiz18 on 2006-11-24
OK, download 1.3.0.  And then try different drivers:

> hostap
hermes
madwifi
atmel
wext
broadcom
ipw
wired
bsd
ndis

maybe try broadcom if you have a broadcom card?

---

### Post by pkastro on 2006-11-24
Still doesn't work, I even tried every driver there, just in case. just hangs there trying to connect, but never receives a DHCP Offer

---

### Post by pkastro on 2006-11-24
Also, here is a *possible* bug:

All the "Signal" areas on the main screen's GUI show them at 0%, when they are, in fact, more than 0% :P

---

### Post by compwiz18 on 2006-11-24
> **pkastro said:**
> Also, here is a *possible* bug:

All the "Signal" areas on the main screen's GUI show them at 0%, when they are, in fact, more than 0% :P
You are using ndiswrapper aren't you?  This is an ndiswrapper bug, not my problem.  However, if you want it to work right, go to ndiswrapper.sourceforge.net, download and compile the newest version, and then the signal strengths will be correct.

---

### Post by compwiz18 on 2006-11-24
> **compwiz18 said:**
> You are using ndiswrapper aren't you?  This is an ndiswrapper bug, not my problem.  However, if you want it to work right, go to ndiswrapper.sourceforge.net, download and compile the newest version (1.29), and then the signal strengths will be correct.

What the heck, I'll upload it for you too, and give you directions: [http://ubuntuforums.org/showpost.php?p=1798811&postcount=773](http://ubuntuforums.org/showpost.php?p=1798811&postcount=773)

---

### Post by pkastro on 2006-11-24
> **compwiz18 said:**
> What the heck, I'll upload it for you too, and give you directions: [http://ubuntuforums.org/showpost.php?p=1798811&postcount=773](http://ubuntuforums.org/showpost.php?p=1798811&postcount=773)

I wasn't sure, sorry mate. I'm so close to getting connected, I Can feel it. I can actually see the networks, I just cant seem to make a darn connection. I don't know whats wrong. Maybe wpa wrapper isn't installed correctly or something. I don't know what to do, im just totally stumped here.](*,) ](*,) ](*,)

---

### Post by compwiz18 on 2006-11-24
> **pkastro said:**
> I wasn't sure, sorry mate. I'm so close to getting connected, I Can feel it. I can actually see the networks, I just cant seem to make a darn connection. I don't know whats wrong. Maybe wpa wrapper isn't installed correctly or something. I don't know what to do, im just totally stumped here.](*,) ](*,) ](*,)
Sorry if I sounded mad, I'm not at all.

Could you tell me what model your card is?

---

### Post by pkastro on 2006-11-24
> **compwiz18 said:**
> Sorry if I sounded mad, I'm not at all.

Could you tell me what model your card is?

Broadcom 4318 on an HP Pavilion zd8000 laptop.

---

### Post by pkastro on 2006-11-24
after installing the newer version of ndiswrapper, i get the following when i do an ndiswrapper -l

```

astro@laptop:~$ ndiswrapper -l
installed drivers:
bcmwl5          driver installed, hardware (14E4:4324) present (alternate driver: bcm43xx)
astro@laptop:~$ 


```


This is new, before all it said was bcmwl5 driver installed, hardware present.

Now I can't even see the wireless networks lol.

---

### Post by compwiz18 on 2006-11-24
> **pkastro said:**
> after installing the newer version of ndiswrapper, i get the following when i do an ndiswrapper -l

```

astro@laptop:~$ ndiswrapper -l
installed drivers:
bcmwl5          driver installed, hardware (14E4:4324) present (alternate driver: bcm43xx)
astro@laptop:~$ 


```


This is new, before all it said was bcmwl5 driver installed, hardware present.

Now I can't even see the wireless networks lol.
Same as mine.  I hate that card...may I suggest that you reinstall the version you had previously using Synaptic?  And while your at it, install everything starting with ndiswrapper, this helps people sometimes.

---

### Post by pkastro on 2006-11-24
> **compwiz18 said:**
> Same as mine.  I hate that card...may I suggest that you reinstall the version you had previously using Synaptic?  And while your at it, install everything starting with ndiswrapper, this helps people sometimes.

Reinstalled everything with Synaptic and it still doesn't work. Actually it changed my eth1 back to wlan0. I had wireless working a while back before I destroyed my Xorg beyond repair, now i finally got X working properly, and the way I Want it, I cant get damn wireless to work lol.](*,)

---

### Post by lonetree on 2006-11-24
does this wireless manager work for all wireless devices?

---

### Post by Ago12 on 2006-11-24
It looks like connection-manager is no more compliant with suspend2 since the introduction of the systray (well, the systray release).

Could you confirm?

---

### Post by compwiz18 on 2006-11-24
Isn't it?  I don't know why it wouldn't be compliant.  And plus, you don't _have_ to install the systray with 1.3.0...

@**lonetree**: As far as I know.

---

### Post by pkastro on 2006-11-24
**@Compwiz** any ideas? possibly a way to rip out EVERYTHING having to do with NDIS Wrapper and WPAsupplicant and possibly start over with your script from [This Post]("http://ubuntuforums.org/showthread.php?t=197102").

BTW: I origionally did all of this setup with that script from your other post. If this is the wrong place for this, let me know, I'm just unsure of what to do to get this all working. It's driving me insane.

---

### Post by compwiz18 on 2006-11-24
Yeah, try uninstalling everything, and then rerunning the script from my other post.  And if you need anymore help, use the Broadcom 4318 thread instead of this one :P It doesn't matter, as I read both of them daily.

---

### Post by yopnono on 2006-11-24
@compwiz18
It don't create the /opt/connection-manager/data/wpa_supplicant.conf if it's deleted or missing, the other .conf files get created.

Also can the connection process have a timeout, if it's not able to connect.
Now it try to connect and connect and... so on.

Also you really need to make sure that all installed files have the right permission root:root

simply run sudo chown -Rv root:root * for allt the files/folders that is going to be installed.

---

### Post by Ago12 on 2006-11-24
> **compwiz18 said:**
> Isn't it?  I don't know why it wouldn't be compliant.  And plus, you don't _have_ to install the systray with 1.3.0...

@**lonetree**: As far as I know.
Actually, it's ok if I don't have to change of network. But I can't change after suspend...

I have to restart autoconnect and log out/in from Gnome...

I used to have the same problem with network-manager, and restarting dbus was doing the trick :)

---

### Post by foxy123 on 2006-11-24
so far so good. I was able to switch my connection from wireless to wired and back manually. It's a pity that I cannot use a systray icon, but, well, I can live without it for a while. If you find a way to use a version of pyGTK, which is in Dapper, please let us know.

---

### Post by compwiz18 on 2006-11-24
> **foxy123 said:**
> so far so good. I was able to switch my connection from wireless to wired and back manually. It's a pity that I cannot use a systray icon, but, well, I can live without it for a while. If you find a way to use a version of pyGTK, which is in Dapper, please let us know.
The only thing the systray icon does is display the signal strength, so you aren't missing much.

---

### Post by foxy123 on 2006-11-24
Regarding feature requests, a VPN plugin or feature would be welcomed in future, though I guess it is not a top priority now.

---

### Post by foxy123 on 2006-11-24
> **compwiz18 said:**
> The only thing the systray icon does is display the signal strength, so you aren't missing much.

oh, well, then. I thought you can choose your connection from there, like in network-manager. Overall I am very happy with the connection-manager, which made my like a little bit easier. Why, it is much easier to switch manually from wired to wireless and back than to type a pass phrase when it is switched automatically by network-manager. Wifi-radar is anice programme too, but I did not manage to make with work with my WPA encryption, though it seems to have a such ability.

Thank you very much!

---

### Post by yopnono on 2006-11-24
@compwiz18

I think it will be better if you don't use 
```
update-rc.d -f auto-connect default
```
better to use
```
update-rc.d -f auto-connect start 40 S .
```
This way you don't get the shutdown script that will case in some computers a slown shutdown. Since the K script will then run on reboot and shoutdown and it will try to connect to network.

If you use *S* then it will only run at boot not at shutdown.

Also I did find that the signal don't show the % correct.
And in atheros (ath0) it don't activate the interface at boot. The init.d script don't put the interface online for some reason.

If it's not activated in network settings. But the opt/ manager script does.

---

### Post by handaxe on 2006-11-24
I get the following, after removing the prev version and deleting the /opt/connection-manager/ directory and contents and then installing.

ver 1.3.0 no systray ver, Dapper

```
royden@rylaptop:~$ sudo /opt/connection-manager/manager
Password:
eth1
0
Traceback (most recent call last):
  File "/opt/connection-manager/manager", line 694, in ?
    frame = Main(None,app_conf,network_conf,wpa_conf)
  File "/opt/connection-manager/manager", line 146, in __init__
    self.UpdateNetworkList()
  File "/opt/connection-manager/manager", line 263, in UpdateNetworkList
    print "wired: " + wired_enabled
TypeError: cannot concatenate 'str' and 'NoneType' objects
```Thanks,

HA

---

### Post by yopnono on 2006-11-24
This is the output from auto-connect ver 1.30, then it gets timeout.
```
./auto-connect
interfacefromconf: ath0
0
flushing the routing table
Cannot find device "505"
killing previous wpa supps
iwconfig ath0 mode 00:11:50:21:E8:49
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.
iwconfig ath0 essid "1" channel Master ap wpa
Error for wireless request "Set Frequency" (8B04) :
    invalid argument "Master".
configuring dhcp
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/ath0/00:11:95:91:95:12
Sending on   LPF/ath0/00:11:95:91:95:12
Sending on   Socket/fallback
DHCPREQUEST on ath0 to 255.255.255.255 port 67
```

---

### Post by compwiz18 on 2006-11-24
> **yopnono said:**
> This is the output from auto-connect ver 1.30, then it gets timeout.
```
./auto-connect
interfacefromconf: ath0
0
flushing the routing table
Cannot find device "505"
killing previous wpa supps
iwconfig ath0 mode 00:11:50:21:E8:49
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.
iwconfig ath0 essid "1" channel Master ap wpa
Error for wireless request "Set Frequency" (8B04) :
    invalid argument "Master".
configuring dhcp
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/ath0/00:11:95:91:95:12
Sending on   LPF/ath0/00:11:95:91:95:12
Sending on   Socket/fallback
DHCPREQUEST on ath0 to 255.255.255.255 port 67
```
Yeah, I forgot to update the auto-connect script to work with 1.3.0, I just did that, version 1.3.1 should be released in about 5 minutes.

---

### Post by foxy123 on 2006-11-24
> **handaxe said:**
> I get the following, after removing the prev version and deleting the /opt/connection-manager/ directory and contents and then installing.

ver 1.3.0 no systray ver, Dapper

```
royden@rylaptop:~$ sudo /opt/connection-manager/manager
Password:
eth1
0
Traceback (most recent call last):
  File "/opt/connection-manager/manager", line 694, in ?
    frame = Main(None,app_conf,network_conf,wpa_conf)
  File "/opt/connection-manager/manager", line 146, in __init__
    self.UpdateNetworkList()
  File "/opt/connection-manager/manager", line 263, in UpdateNetworkList
    print "wired: " + wired_enabled
TypeError: cannot concatenate 'str' and 'NoneType' objects
```Thanks,

HA

systray does not work on Dapper...

compwiz18, could you put dependencies in the systray package to prevent it to be installed on Dapper?

---

### Post by handaxe on 2006-11-24
I know that :) - I was reporting that I am on Dapper and am using the version of connection-manager without the  systray.

No-one else have the error I eported on Dapper/gnome?

HA

> **foxy123 said:**
> systray does not work on Dapper...

compwiz18, could you put dependencies in the systray package to prevent it to be installed on Dapper?

---

### Post by foxy123 on 2006-11-24
> **handaxe said:**
> I know that :) - I was reporting that I am on Dapper and am using the version of connection-manager without the  systray.

No-one else have the error I eported on Dapper/gnome?

HA

oh sorry, I misread your post..

---

### Post by pkastro on 2006-11-24
I'm just about at my wit's end. Anyone got want to recommend a good CHEAP Wireless card for a laptop? I'm about 2 seconds away from buying one at the Navy Exchange lol.

---

### Post by compwiz18 on 2006-11-24
Yep, all fixed :D

New in 1.3.1:
[LIST=1]
[*]Bug fixes.
[*]More bug fixes.
[*]Some more bug fixes.
[*]Ability to specify the name of the wired interface (defaults to eth0) - check the Preferences menu
[*]All files are now owned by root.
[*]Auto connect now works again
[*]Checks for missing WPA config file and creates if needed
[/LIST]

Check it out and start feeding me problems.

OK, also, can someone check and make sure that the systray deb won't install on Dapper?  I think I fixed it so it checks for the right dependencies.

---

### Post by handaxe on 2006-11-24
Indeed, the errors I reported are fixed in 1.3.1.

Thanks for the persistence here...

HA

---

### Post by compwiz18 on 2006-11-24
> **handaxe said:**
> Indeed, the errors I reported are fixed in 1.3.1.

Thanks for the persistence here...

HA
Glad it works again.

---

### Post by handaxe on 2006-11-24
Confirmed, the systray deb indicated an unsatisfied depend. on Dapper....

HA

---

### Post by compwiz18 on 2006-11-24
> **handaxe said:**
> Confirmed, the systray deb indicated an unsatisfied depend. on Dapper....

HA
Good.

---

### Post by handaxe on 2006-11-24
It is a pity about the systray icon in Dapper. On my laptop Network Monitor 2.12 shows a signal strength about twice that of connection-manager. The latter is prolly right. No show-stopper though.

I also have Netspeed 0.13 up as using HSDPA I watch if the transmission is stable.

This set me thinking (shudder..)

I would value a "one-stop shop" type connection-manager in as far as the display side goes. A sys-tray icon that generally shows signal strength with a balloon showing connected ESSID or network (wired) but can then be clicked to choose small drop-down and / or detachable applet windows showing, say "Throughput - up/down, byte ttls" "Hardware, IPs etc" and "visible ESSIDs".

Easy to write here, I know...

Whatever - thanks to compwiz18 for what is done so far. I for one wish I could code and give....

HA

---

### Post by alchimera on 2006-11-24
> **compwiz18 said:**
> Yep, all fixed :D

New in 1.3.1:[LIST=1]
[*]Bug fixes.
[*]More bug fixes.
[*]Some more bug fixes.
[*]Ability to specify the name of the wired interface (defaults to eth0) - check the Preferences menu
[*]All files are now owned by root.
[*]Auto connect now works again
[*]Checks for missing WPA config file and creates if needed[/LIST]Check it out and start feeding me problems.

1.3.1 seems to think that i am wired:
```
 sudo /opt/connection-manager/manager
eth0
0
wired: yes
```which is not the case, so no internet connection.
After setting my static IP/DNS and trying to connect:
```
link clicked: py:connect(0)
{'encryption': 'off', 'signal': '71', 'ap_mac': '00:11:95:96:27:26', 'mode': 'Master', 'channel': '6', 'essid': 'G604T_WIRELESS'}
interface: eth0
flushing the routing table
Nothing to flush.
Nothing to flush.
killing previous wpa supps
wpa_supplicant: no process killed
SIOCSIFNETMASK: Invalid argument
iwconfig eth0 mode Managed
iwconfig eth0 essid "G604T_WIRELESS" channel 6 ap 00:11:95:96:27:26
configuring static ip
ifconfig eth0 192.168.1.72
removing default stuff from routing table
SIOCDELRT: No such process
adding default gateway
route add default gw 192.168.1.1
SIOCADDRT: Network is unreachable
done
```so had to uninstall it...

---

### Post by compwiz18 on 2006-11-24
@**alchimera**: can you run **sudo ethtool name-of-wired-interface** with the cable plugged in and with the cable not in?  I suspect ethtool is giving false results...

EDIT: Never mind, the newest one should have it fixed...could you try if you have time and tell me?  I switch from ethtool to mii-tool to detect if the cable is plugged in.  I think ethtool is wrong a lot...or at least wifi-radar doesn't use it for this reason.

---

### Post by NetworkGuy on 2006-11-24
**@compwiz18** Your fix for the ACX111 chipset works.  Thanks.

---

### Post by compwiz18 on 2006-11-24
> **NetworkGuy said:**
> **@compwiz18** Your fix for the ACX111 chipset works.  Thanks.
Good.

---

### Post by Ago12 on 2006-11-24
It works fine here, good job :)

BUT (yes, there is a but :p ) I still have the 
Mailcap file /etc/mailcap, line 95: incomplete entry ignored.
error.

Maybe it has been corrected since, and I should remove/edit this file, then reinstall the package? Thanks :)

---

### Post by alchimera on 2006-11-24
> **compwiz18 said:**
> @**alchimera**: can you run **sudo ethtool name-of-wired-interface** with the cable plugged in and with the cable not in?  I suspect ethtool is giving false results...

EDIT: Never mind, the newest one should have it fixed...could you try if you have time and tell me?  I switch from ethtool to mii-tool to detect if the cable is plugged in.  I think ethtool is wrong a lot...or at least wifi-radar doesn't use it for this reason.

(i) ethtool worked fine here 
```
alchimera@PeaceSea:~$ sudo ethtool eth1
Settings for eth1:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes
```when plugged in, identical but for "Link detected: no" when unplugged.
(ii) mii-tool gave
```
sudo mii-tool eth1
SIOCGMIIPHY on 'eth1' failed: Operation not supported
```(iii) the option for wired was absent with 1.3.2

(iii) could not get a connection after reboot with 1.3.2, output
```
eth0
0
SIOCGMIIPHY on 'eth1' failed: Operation not supported
wired: False

link clicked: py:connect(0)
{'encryption': 'off', 'signal': '91', 'ap_mac': '00:11:95:96:27:26', 'mode': 'Master', 'channel': '6', 'essid': 'G604T_WIRELESS'}
interface: eth0
flushing the routing table
Nothing to flush.
Nothing to flush.
killing previous wpa supps
wpa_supplicant: no process killed
SIOCSIFNETMASK: Invalid argument
iwconfig eth0 mode Managed
iwconfig eth0 essid "G604T_WIRELESS" channel 6 ap 00:11:95:96:27:26
configuring static ip
ifconfig eth0 192.168.1.72
removing default stuff from routing table
SIOCDELRT: No such process
adding default gateway
route add default gw 192.168.1.1
SIOCADDRT: Network is unreachable
done

```

---

### Post by Ryanmt on 2006-11-24
Hey, your old bugfix worked fine I can now list all wifi networks.

Ive installed the new version but i cant connect. Ive disabled as much as i can in the normal network manager and tried to leave it all to the connection manager.

The systray icon says its connected but when i click connect it just says its thinkng for a while then never actually connects.

Heres the output

```

ryanmt@penguin:~$ sudo connection-manager
Password:
wlan0
0
wired: False
0
wired: False
link clicked: py:connect(0)
{'encryption': 'on', 'signal': '92', 'ap_mac': '00:0F:B5:B4:33:D6', 'mode': 'Master', 'channel': '11', 'essid': 'NETGEAR'}
interface: wlan0
flushing the routing table
Nothing to flush.
Nothing to flush.
killing previous wpa supps
wpa_supplicant: no process killed
iwconfig wlan0 mode Managed
iwconfig wlan0 essid "NETGEAR" channel 11 key ######## ap 00:0F:B5:B4:33:D6
[b]Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; Invalid argument.[/b]
configuring dhcp
There is already a pid file /var/run/dhclient.pid with pid 5318
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:0e:3b:06:88:3c
Sending on   LPF/wlan0/00:0e:3b:06:88:3c
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
Trying recorded lease 192.168.0.4
No working leases in persistent database - sleeping.

```

Have to say your softwares looking very good.

few suggestions 
- swap the subnet round with the gateway so its layed out like it is in xp.
- make tab work between the text boxs on the ip settings.
- make it so you can enter just one dns server

No biggy though everything else looks great, keep up the good work :D

---

### Post by MerZo on 2006-11-24
Is there someway to make this program autoconnect to a network at GNOME login without user interaction? Showing up the signal and so on. Right now I have to click the tray icon and then enter password, click connect, then everything works.

Will it be possible in the future to make this by auto or am I missing something? (Probably am, tired and read through the whole tread)

Thanks for the great program!

---

### Post by compwiz18 on 2006-11-24
> **MerZo said:**
> Is there someway to make this program autoconnect to a network at GNOME login without user interaction? Showing up the signal and so on. Right now I have to click the tray icon and then enter password, click connect, then everything works.

Will it be possible in the future to make this by auto or am I missing something? (Probably am, tired and read through the whole tread)

Thanks for the great program!
It should do that.  Did you click setup Network and check preferred network?  Then if this network is in range at boot, it will automatically connect.  Or it should, at least.

---

### Post by MerZo on 2006-11-25
Yes, I did check it to be a preferred network. Under "Network Setup" there is the WEP key for the network, and the checkbox for preferred. Still, when I boot the computer, the ath0 device goes up searching for a network but doesn't find one. And then when I am in the GNOME environment the network has no signal, but clicking the tray icon, enter the password, clicking connect on the network makes it connect.

I probably need to delete all the files from the first install I did (1.1.0), will look through the tread again to see which files to delete and delete those and then get back if it still doesnt work.

Still, now I know that it should work, which makes it more easy to fix. ;-)

---

### Post by compwiz18 on 2006-11-25
If you can't get that to work try running **sudo /etc/init.d/auto-connect** in a terminal and post the output.

---

### Post by serlex on 2006-11-25
> **compwiz18 said:**
> Try editing /opt/connection-manager/data/wpa-settings.conf.  It uses the same syntax as wpa_supplicant, so if you read the wpa_supplicant man page, this should give you enough info to set it up.

```
network={
        ssid="FreedomNetv2"
        mode=0
        proto=WPA
        key_mgmt=WPA-EAP
        eap=TTLS
        pairwise=TKIP
        group=TKIP
        identity="ece99999"
        password="yourpassword"
        ca_cert="/opt/UOP-b64.cer"
        phase2="auth=PAP"
        priority=2
} 
```

This is what i came up with, i put it inside wpa-settings.conf, havent tested it, will it start soon as i start connection-manager or through terminal?

---

### Post by compwiz18 on 2006-11-25
> **serlex said:**
> ```
network={
        ssid="FreedomNetv2"
        mode=0
        proto=WPA
        key_mgmt=WPA-EAP
        eap=TTLS
        pairwise=TKIP
        group=TKIP
        identity="ece99999"
        password="yourpassword"
        ca_cert="/opt/UOP-b64.cer"
        phase2="auth=PAP"
        priority=2
} 
```

This is what i came up with, i put it inside wpa-settings.conf, havent tested it, will it start soon as i start connection-manager or through terminal?
When you click and connect to FreedomNetv2, it will start and use this entry to connect, hence using your settings.

---

### Post by MerZo on 2006-11-25
> **compwiz18 said:**
> If you can't get that to work try running **sudo /etc/init.d/auto-connect** in a terminal and post the output.

Hi, I tired to uninstall the connection-manager, delete the files in /opt and then reinstall it, but still the same problem. Without it installed the lights on the network card are just constant meaning it is not trying to connect to a network, with the connection-manager installed, it tries to connect but fail.

This is the output from the /etc/init.d/auto-connect

```
wifiinterfacefromconf: ath0
0
1
flushing the routing table
Nothing to flush.
Nothing to flush.
killing previous wpa supps
wpa_supplicant: no process killed
iwconfig ath0 mode Managed
iwconfig ath0 essid "netdefault" channel 4 key [wep-key] ap 00:80:C8:07:A2:70
configuring dhcp
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0d:88:a5:0b:4e
Sending on   LPF/ath0/00:0d:88:a5:0b:4e
Sending on   Socket/fallback
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
Traceback (most recent call last):
  File "/etc/init.d/auto-connect", line 109, in ?
    wifi.connect(wifi_interface,wired_interface,essid,channel,mode,ap_mac,enctype,key,wpa_driver,ip,gateway,subnet,dns1,dns2)
  File "/usr/lib/python2.4/networking.py", line 180, in connect
    f.close()
KeyboardInterrupt

```

What I can get of it is that it is trying to connect but the dhcp times out. Why this is I do not know. When opening the Connection Manager in GNOME and clicking connect on the network it connects just fine and I can surf the web. Something is not working on the way, but I am running out of ideas. Can you get something out of the output or could I provide you more information?

Using dlink g650 that uses madwifi and using the madwifi driver in the connection manager setup. I wonder if the network card is trying to connect to a different network as I can see two from here. But the AP MAC adress is correct in the output provided.

Thanks in advance. Want this to work. :-)

---

### Post by compwiz18 on 2006-11-25
Yeah...can you run **cat /opt/connection-manager/data/*.conf** for me?  Make sure and comment out network keys ;)

---

### Post by yopnono on 2006-11-25
@compwiz18

For autostart of the trayicon in gnome you can put the connection-manager-tray in this dir at install.
```
/etc/xdg/autostart
```

It's a .desktop file

---

### Post by MerZo on 2006-11-25
> **compwiz18 said:**
> Yeah...can you run **cat /opt/connection-manager/data/*.conf** for me?  Make sure and comment out network keys ;)

Sure thing, here it comes. :-)

```
cat /opt/connection-manager/data/network-settings.conf 
[netdefault]
enc = WEP
favorite = True
key = *********

```

```
cat /opt/connection-manager/data/manager-settings.conf 
[Settings]
interface = ath0
wpa_driver = wext

```

wpa*.conf is empty.

Two things that comes to my mind, first is that maybe I am using the wrong driver? But still, clicking connect works. Should it be madwifi? And why would that help?
Second, when I first open the Connection Manager I just see the network I don't want to connect to, pressing "Refresh" makes me see the AP I want to accesss and the other. Isnt that kind of weird?

Well. Say if you need something more.

---

### Post by compwiz18 on 2006-11-25
Yep, can you do **sudo iwlist scan** and **sudo iwconfig** and **sudo ifconfig -a** and post outputs?  Thank you.

---

### Post by MerZo on 2006-11-26
> **compwiz18 said:**
> Yep, can you do **sudo iwlist scan** and **sudo iwconfig** and **sudo ifconfig -a** and post outputs?  Thank you.

I don't have access to the computer nor the network right now but I will do it in a few days when I have got it. :-)

---

### Post by serlex on 2006-11-26
just tried to connect to our home encrypted network, connection-manager tries to connect but times out.

---

### Post by serlex on 2006-11-26
sudo iwlist scan
```

sercan@sercan-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:12:17:07:72:A7
                    ESSID:"clementine"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:5
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=91/100  Signal level=-37 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 76ms ago
          Cell 02 - Address: EE:38:59:3B:2E:6B
                    ESSID:"hpsetup"
                    Protocol:IEEE 802.11b
                    Mode:Ad-Hoc
                    Channel:6
                    Encryption key:off
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11
                    Quality=39/100  Signal level=-77 dBm
                    Extra: Last beacon: 140ms ago
          Cell 03 - Address: 00:17:31:47:A9:55
                    ESSID:"HappyHouse"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=39/100  Signal level=-77 dBm
                    Extra: Last beacon: 1164ms ago
          Cell 04 - Address: 00:14:BF:93:4A:51
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=37/100  Signal level=-78 dBm
                    Extra: Last beacon: 420ms ago
          Cell 05 - Address: 00:11:F5:79:C8:4F
                    ESSID:"paul"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=87/100  Signal level=-77 dBm
                    Extra: Last beacon: 400ms ago
          Cell 06 - Address: 00:09:5B:87:FE:B0
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54
                    Quality=35/100  Signal level=-79 dBm
                    Extra: Last beacon: 724ms ago
          Cell 07 - Address: 00:50:18:49:CC:E2
                    ESSID:"default"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=39/100  Signal level=-77 dBm
                    Extra: Last beacon: 360ms ago

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.
```
iwconfig
```

eth1      unassociated  ESSID:"clementine"
          Mode:Managed  Frequency=2.432 GHz  Access Point: 00:11:F5:79:C8:4F
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.
```

---

### Post by compwiz18 on 2006-11-26
@**serlex**: can you post the output when you run **sudo connection-manager** in a terminal and try to connect to the network that times out?

---

### Post by iki488 on 2006-11-26
tested 1.3.2, still the same problem when trying to connect to any wireless network (with or without wpa encryption). Wired network works fine.

here is the output of connection-manager :
> 
ken@ken-laptop:~$ sudo /opt/connection-manager/manager 

(python:6808): Gtk-WARNING **: Theme directory scalable/stock/svg of theme Sladf has no size field

eth1
0
1
2
3
wired: True
link clicked: py:preferences(0)
link clicked: py:connect(0)
{'encryption': 'on', 'signal': '87', 'ap_mac': '00:12:BF:07:C1:0F', 'mode': 'Master', 'channel': '6', 'essid': 'KenGabs'}
interface: eth1
flushing the routing table
Nothing to flush.
Nothing to flush.
killing previous wpa supps
wpa_supplicant: aucun processus tué
running wpa supp
wpa_supplicant -B -i eth1 -c /opt/connection-manager/data/wpa_supplicant.conf -D wext
iwconfig eth1 mode Managed
iwconfig eth1 essid "KenGabs" channel 6 ap 00:12:BF:07:C1:0F
configuring dhcp
There is already a pid file /var/run/dhclient.pid with pid 6757
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0e:35:48:0c:66
Sending on   LPF/eth1/00:0e:35:48:0c:66
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
done


hope it will be solved soon :s

ps : my wireless card is an **ipw2200** and it works most of the time with network manager (with wpa too), but only with it ... wifi-radar etc. doesn't work with me (network scan ok but impossible to connect).

---

### Post by foxy123 on 2006-11-26
Hi compwiz18, you know, version of your connection-manager-1.3.2 file is actually 1.3.1. Could you bump it up for consistency?

---

### Post by serlex on 2006-11-26
> **compwiz18 said:**
> @**serlex**: can you post the output when you run **sudo connection-manager** in a terminal and try to connect to the network that times out?
sorry its not WEP, its WPA-personal. I tested it with network-manager to see it works, and it does. o

output of sudo connection-manager
```

eth1
0
1
2
3
wired: False
link clicked: py:preferences(0)
link clicked: py:connect(0)
{'encryption': 'on', 'signal': '93', 'ap_mac': '00:12:17:07:72:A7', 'mode': 'Mas ter', 'channel': '5', 'essid': 'clementine'}
interface: eth1
flushing the routing table
Nothing to flush.
killing previous wpa supps
wpa_supplicant: no process killed
running wpa supp
wpa_supplicant -B -i eth1 -c /opt/connection-manager/data/wpa_supplicant.conf -D  wext
iwconfig eth1 mode Managed
iwconfig eth1 essid "clementine" channel 5 ap 00:12:17:07:72:A7
configuring dhcp
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:12:f0:83:c8:b8
Sending on   LPF/eth1/00:12:f0:83:c8:b8
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
Trying recorded lease 10.0.0.97
No working leases in persistent database - sleeping.
done

```

i guess its not the package, I must be doing something wrong, i selected WPA then entered my key, still no luck

---

### Post by jessegillies on 2006-11-26
edit: never mind. there seems to have been a problem with my router.

---

### Post by garyincny on 2006-11-27
First I like to say I am a newbie at Linux and had a terrible time getting my laptop to connect wirelessly at home and at college. Then I stumbled on this awesome post that has saved me from going back to Windows...thanks a million **compwiz18**..this program you have written has saved me and I suspect countless others hours and hours of headaches. 

That all said...just one small tiny thing...in the newest release 1.3.2..systray seems to be absent now. I added it to session manager in gnome as you instructed at the beginning of the post, but on reboot it never comes up. When i click on the .deb file of version 1.3.2 and look at the files that are included...from what I can see, systray is missing in the list of things to install. Being new and all, I am probably missing something easy.

Once again **compwiz18** great job on writing this awesome program :)

---

### Post by yopnono on 2006-11-27
> **garyincny said:**
> I am probably missing something easy. :)

Yes you are missing something. Have a look at the first page and you will find that the systray are a separated package.

---

### Post by MerZo on 2006-11-27
> **compwiz18 said:**
> Yep, can you do **sudo iwlist scan** and **sudo iwconfig** and **sudo ifconfig -a** and post outputs?  Thank you.

Hello, I am back. Now I will give you the output and let you analyze. If you have the time :-)

```
sudo iwlist scan
Password:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:80:C8:07:A2:70
                    ESSID:"netdefault"
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Quality=5/94  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:13:46:49:9B:22
                    ESSID:""
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=8/94  Signal level=-87 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

irda0     Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

```

```
sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:1094  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.

sit0      no wireless extensions.

```

```
sudo ifconfig -a
ath0      Link encap:Ethernet  HWaddr 00:0D:88:A5:0B:4E  
          inet6 addr: fe80::20d:88ff:fea5:b4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:03:47:B6:5D:13  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-0D-88-A5-0B-4E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1463 errors:0 dropped:0 overruns:0 frame:463
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:138747 (135.4 KiB)  TX bytes:1334 (1.3 KiB)
          Interrupt:11 Memory:cca20000-cca30000 

```

I think that the network interface tries to connect to the "" network, and not the netdefault. The netdefault is my network and the other is some neighbour. 

I have checked so the netdefault is preferred and the other network is not selected in the Wireless Manager. What should I do to solve this? If I am on the right track which is that the network tries to connect to the wrong network.

---

### Post by garyincny on 2006-11-27
**yopnono** thank you very much :) It is amazing what you miss sometimes when its right under your nose.

---

### Post by yopnono on 2006-11-28
@compwiz18

Is it possible to set a lower timeout value for the connection process?
Also a disconnect button and an "auto update" so you can see if there is any new networks, and also you will be able to see if the signal changes for available networks.

Like in wifi-radar, also you can use code from that project if you like since it's GPL.

[http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/)

---

### Post by Ago12 on 2006-11-28
I'm still keeping three problems:

- mailcap error at startup
- doesn't automaticaly connects to prefered network at startup
- cannot connect to an OTHER network after suspend2

:)

---

### Post by yopnono on 2006-11-28
> **Ago12 said:**
> I'm still keeping three problems:

- mailcap error at startup
- doesn't automaticaly connects to prefered network at startup
- cannot connect to an OTHER network after suspend2

:)

After suspend do you have many wpa_supplicants or dhclient/dhclient3 running?
Check the system monitor or run ps -fe in terminal

---

### Post by yopnono on 2006-11-28
@compwiz18

Another thing it might be good to run killall dhclient and dhclient3 like you run the killall wpa_supplicant, it may cause problems if you have multiple clients running.

---

### Post by compwiz18 on 2006-11-29
> **yopnono said:**
> @compwiz18

Is it possible to set a lower timeout value for the connection process?
Also a disconnect button and an "auto update" so you can see if there is any new networks, and also you will be able to see if the signal changes for available networks.

Like in wifi-radar, also you can use code from that project if you like since it's GPL.

[http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/)

I can do a disconnect button, an probably an Abort button for the connection process.  I'm not sure about the autoupdate thing, but I'll work on it.  And yes, I stole some code from wifi-radar (namely the regex iwlist search patterns)

> **yopnono said:**
> @compwiz18

Another thing it might be good to run killall dhclient and dhclient3 like you run the killall wpa_supplicant, it may cause problems if you have multiple clients running.

Done.  Will be in the next release.

---

### Post by yopnono on 2006-11-29
@compwiz18
Cant you use something like reload(networkscan) and set it to reload every 2sec without the scanning progress dialog

---

### Post by compwiz18 on 2006-11-29
> **yopnono said:**
> @compwiz18
Cant you use something like reload(networkscan) and set it to reload every 2sec without the scanning progress dialog
@**yopnono**: I'll look into it.  Because of the way it works, I'm thinking that scrolling might be impossible then, which would be a Bad Thing.

---

### Post by serlex on 2006-11-29
any luck on my error?

---

### Post by MerZo on 2006-11-30
Is there a solution to the problem with getting the right preferred network I am having?

The damn neighbour doesnt have a essid for the network. :/

---

### Post by marhp on 2006-11-30
With the disconnect button will it allow you to use another applet to connect to the internet. Now my wish 
I am new to this so I don't know how difficult this would be but is there a way that you could use the "code" from network-selector as far as signal strength. I find that network-selector can connect to routers that connection-manager give a bad signal  and does not connect.

---

### Post by Thumper322 on 2006-12-01
Is support for hidden ESSIDs coming soon? That's the only thing keeping me from using this tool... :(

---

### Post by yopnono on 2006-12-01
I did play with hidden ESSID. And the only way I could make connect with wpa_supplicant was by typing this in the terminal first.
```
iwconfig <your_interface> essid "your_essid"
```
Then after that I can connect.

But not by using the connect-manager. I used wpa_supplicant directly.
This because I can't type the ESSID in the gui.

The ESSID in the config file is named <hidden> = not right :)

---

### Post by Thumper322 on 2006-12-01
> **yopnono said:**
> I did play with hidden ESSID. And the only way I could make connect with wpa_supplicant was by typing this in the terminal first.
```
iwconfig <your_interface> essid "your_essid"
```
Then after that I can connect.

But not by using the connect-manager. I used wpa_supplicant directly.
This because I can't type the ESSID in the gui.

The ESSID in the config file is named <hidden> = not right :)
Can I edit the configuration file that powers connect-manager to add this, or something like that?

Thing is, Network Manager doesn't work nicely either; I have to manually type in the ESSID and passphrase every time I connect. I want to make this as simple as possible...

---

### Post by compwiz18 on 2006-12-01
> **Thumper322 said:**
> Can I edit the configuration file that powers connect-manager to add this, or something like that?

Thing is, Network Manager doesn't work nicely either; I have to manually type in the ESSID and passphrase every time I connect. I want to make this as simple as possible...
Since you asked so nicely - hidden ESSIDs will be in the next release =D  My problem is I don't know how hidden ESSIDs work - so if some of you could answer a few questions:

[LIST]
[*]Can you use WEP?
[*]Can you use WPA?
[*]Does the user need to be able to specify the channel?
[/LIST]

---

### Post by compwiz18 on 2006-12-01
> **serlex said:**
> any luck on my error?
Could you tell me what type of wireless card you are using?

---

### Post by yopnono on 2006-12-01
> **compwiz18 said:**
> Since you asked so nicely - hidden ESSIDs will be in the next release =D  My problem is I don't know how hidden ESSIDs work - so if some of you could answer a few questions:

[LIST]
[*]Can you use WEP?
[*]Can you use WPA?
[*]Does the user need to be able to specify the channel?
[/LIST]


When I tried I did not need to enter the channel, only.
```
iwconfig <interface> essid "essid"
```
And I was using the WPA conf file that inc the ESSID for that network and psk key.

---

### Post by compwiz18 on 2006-12-01
So, no channel needs to be specified, and you can use WPA.  What about WEP and hidden ESSIDs?

---

### Post by Thumper322 on 2006-12-01
> **compwiz18 said:**
> So, no channel needs to be specified, and you can use WPA.  What about WEP and hidden ESSIDs?
Not sure what you mean.

Under Windows, I've always been able to connect to WEP-encrypted hidden networks, later upgraded to WPA; similar functionality would be nice.

For me, I need hidden ESSIDs and WPA. Sorry for not being much of a help...

---

### Post by yopnono on 2006-12-01
> Originally Posted by compwiz18  View Post
So, no channel needs to be specified, and you can use WPA. What about WEP and hidden ESSIDs?

Sorry can't help you with that, not right now.

---

### Post by yopnono on 2006-12-02
Arrgh. I can't connect to my AP using WEP. Don't know why.
Anyhow I did see that you already use 
```
iwconfig ' + interface + ' essid "' + essid + 
```
for WEP so I guess it should work the same as for WPA.

---

### Post by zpro on 2006-12-02
Compwiz18:
Did the final install of the connection manager systray...

FYI: in xubuntu you need to goto:
Setting AutoStart Apps, and add it in there, however, the "command" should be the full path:usr/bin/connection-manager-systray , and name it connection manager.

next: when rebooting saw the icon up top, when signal strength all green bar, good... now this is where you need some clarities on HOW TO.:p 

You have 2 places to enter the static ip address, ONE, in networking by selecting the wireless card, and click pref, and adding your network information there.

the next place is YOUR APP Connection Manager, under Setup Network....
"Which place GETS the Network info": Xubuntu Networking settings, OR YOUR Connection Manger ???? :confused: 

Right now, I am using Xubuntu Networking Setting with NO WEP as of yet.,
and using static IP and its working...( your app setting are blank )

But I want to use wep security, using linksys,
so, where? do I just use connection manager feature of wep security and turn it on, and add the "password" or "hexcode" into the box ???:confused:

next to last: does preferred network, mean it will connect all the time,
to that wireless (linksys) network...I selected? :rolleyes: 

LAST:
I keep getting a mailcap file line 54 ignored error message.....


Thanks ++
:mrgreen:

---

### Post by compwiz18 on 2006-12-02
> **zpro said:**
> Compwiz18:
Did the final install of the connection manager systray...

FYI: in xubuntu you need to goto:
Setting AutoStart Apps, and add it in there, however, the "command" should be the full path:usr/bin/connection-manager-systray , and name it connection manager.

next: when rebooting saw the icon up top, when signal strength all green bar, good... now this is where you need some clarities on HOW TO.:p 

You have 2 places to enter the static ip address, ONE, in networking by selecting the wireless card, and click pref, and adding your network information there.

the next place is YOUR APP Connection Manager, under Setup Network....
"Which place GETS the Network info": Xubuntu Networking settings, OR YOUR Connection Manger ???? :confused: 

Right now, I am using Xubuntu Networking Setting with NO WEP as of yet.,
and using static IP and its working...( your app setting are blank )

But I want to use wep security, using linksys,
so, where? do I just use connection manager feature of wep security and turn it on, and add the "password" or "hexcode" into the box ???:confused:

next to last: does preferred network, mean it will connect all the time,
to that wireless (linksys) network...I selected? :rolleyes: 

LAST:
I keep getting a mailcap file line 54 ignored error message.....


Thanks ++
:mrgreen:
Ok, you should enter the info into Connection Manager, not the XFCE Networking Settings.  If you want to use WEP, just click Network Settings and enter the password or hexcode into the box (I'm not 100% sure how this works - if the hexcode doesn't work, try the password or vice versa)  Preferred Network means that it will connect automatically at boot, so you don't have to do anything.  That mailcap error can be fixed by fixing the offending lines in your /etc/mailcap file - I don't know why it pops up.

---

### Post by mssever on 2006-12-03
> **compwiz18 said:**
> Ok, you should enter the info into Connection Manager, not the XFCE Networking Settings.  If you want to use WEP, just click Network Settings and enter the password or hexcode into the box (I'm not 100% sure how this works - if the hexcode doesn't work, try the password or vice versa)  Preferred Network means that it will connect automatically at boot, so you don't have to do anything.  That mailcap error can be fixed by fixing the offending lines in your /etc/mailcap file - I don't know why it pops up.
The mailcap error on my system was caused by Compiz doing Dumb Things in that file. Until I fixed mailcap, I got it from many programs that use wxWidgets (I think that's where it is...It might be Python, but one program that pops up that box is in C++).

Perhaps there's a flag you can set somewhere that will prevent that box? It doesn't serve any useful purpose.

---

### Post by compwiz18 on 2006-12-03
> **mssever said:**
> The mailcap error on my system was caused by Compiz doing Dumb Things in that file. Until I fixed mailcap, I got it from many programs that use wxWidgets (I think that's where it is...It might be Python, but one program that pops up that box is in C++).

Perhaps there's a flag you can set somewhere that will prevent that box? It doesn't serve any useful purpose.
Yeah, I get the mailcap error in Audacity as well.  The one thing I noticed is that in the wxPython demo, the error is hidden - but the message is written to the output... I looked, but I couldn't figure out how they did that, so I kinda gave up...

If anyone can shed some light here, that would be helpful.

---

### Post by Ago12 on 2006-12-03
Commenting the line make the error message go away, apparently without side-effect...

---

### Post by David Valentine on 2006-12-04
I'm having rather a different issue.  I got my Broadcom 4306 card working using fwcutter, then installed connection-manager.  Everything worked, but I noticed that connection manager did not automatically use my wired connection when I connected it up.  Network manager did that, so I decided to switch to network manager instead.  I uninstalled connection manager and the systray applet, and removed /opt/connection-manager, then installed knetwork-manager.  My system sees my Broadcom card and reports that it's enabled, but my attempts to use it fail (e.g., clicking on that connection w/in network manager stalls at 28%) ](*,).  If I uninstall network manager and re-install connection manager, everything works again.  Do I need to go through the whole fwcutter thing again, or am I simply missing some simple modprobe command that I need to do, or what?:confused:

Thanks!

---

### Post by H.E. Pennypacker on 2006-12-05
Sweet!  

Just a couple of recommendations:

1.  Add Connection Manager and the Systray icon to the same .Deb file.  Removes the unnecessary work of installing two things.

2. Have the Systray icon add itself to "Startup," rather than having to to "Sessions."

3.  After having connected to a network, could you have it say "Connected," to show that it is actually connected to that network?  Very useful. 

Thanks a lot!

---

### Post by foxy123 on 2006-12-05
> **H.E. Pennypacker said:**
> Sweet!  

Just a couple of recommendations:

1.  Add Connection Manager and the Systray icon to the same .Deb file.  Removes the unnecessary work of installing two things.


systray icon does not work with Dapper, so it will mean to make the connection manager incompatible with Dapper.

---

### Post by David Valentine on 2006-12-06
No answers, I guess.  Time for a clean reinstall...:(

---

### Post by yopnono on 2006-12-06
> **David Valentine said:**
> No answers, I guess.  Time for a clean reinstall...:(

Don't know what answer you want, but CM don't remove or install anything that can mess up you drivers.

---

### Post by foxy123 on 2006-12-06
> **David Valentine said:**
> I'm having rather a different issue.  I got my Broadcom 4306 card working using fwcutter, then installed connection-manager.  Everything worked, but I noticed that connection manager did not automatically use my wired connection when I connected it up.  Network manager did that, so I decided to switch to network manager instead.  I uninstalled connection manager and the systray applet, and removed /opt/connection-manager, then installed knetwork-manager.  My system sees my Broadcom card and reports that it's enabled, but my attempts to use it fail (e.g., clicking on that connection w/in network manager stalls at 28%) ](*,).  If I uninstall network manager and re-install connection manager, everything works again.  Do I need to go through the whole fwcutter thing again, or am I simply missing some simple modprobe command that I need to do, or what?:confused:

Thanks!
I experienced some problems with installing network manager after connection manager, though it was due to resolv.conf file. FOr some reasons the dns entries were gone and I had to put them there again. But it was more nm fault than cm.

---

### Post by javierfh on 2006-12-06
Hi I need help with that one, i am desperated.
I have a wlan card SMC2835W v3 EU

So i have first tried to install ndiswrapper following the instructions from that post [http://ubuntuforums.org/showthread.php?t=287485&highlight=SMC2835W](http://ubuntuforums.org/showthread.php?t=287485&highlight=SMC2835W)
At some point i got the lights flashing once, but then after that never again (funny thing is that using windows xp the card works just fine)
Then i tried to install both deb packages from that thread but still didnt work. 
I have tried also with Automatix to install ndiswrapper again and try to install the right driver from smc site.

Nothing works... the card doesnt want to work.

I add here the output of different commands, please i hope someone can give me some help here, this is really frustrating.

Thanks in advance,

Javi

> 

javier@laptoplinux:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
        Flags: bus master, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 96
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: d8000000-dfffffff

00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 01) (prog-if 00 [UHCI])
        Subsystem: Compaq Computer Corporation Unknown device 009c
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1840 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 01) (prog-if 00 [UHCI])
        Subsystem: Compaq Computer Corporation Unknown device 009c
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1860 [size=32]

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=06, sec-latency=64
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d0200000-d02fffff
        Prefetchable memory behind bridge: 20000000-21ffffff

00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Compaq Computer Corporation Unknown device 009c
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at 1800 [size=16]
        Memory at 22000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
        Subsystem: Compaq Computer Corporation Unknown device 009c
        Flags: medium devsel, IRQ 5
        I/O ports at 1820 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
        Subsystem: Compaq Computer Corporation Unknown device 005c
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at 1c00 [size=256]
        I/O ports at 1880 [size=64]

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY (prog-if 00 [VGA])
        Subsystem: Compaq Computer Corporation Unknown device b11b
        Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 11
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 2000 [size=256]
        Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at d0120000 [disabled] [size=128K]
        Capabilities: <access denied>

02:04.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
        Subsystem: Compaq Computer Corporation Unknown device 8d89
        Flags: medium devsel, IRQ 255
        Memory at d0210000 (32-bit, non-prefetchable) [disabled] [size=64K]
        I/O ports at 3040 [disabled] [size=8]
        Capabilities: <access denied>

02:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Compaq Computer Corporation Unknown device b1b1
        Flags: bus master, medium devsel, latency 64, IRQ 9
        Memory at d0201000 (32-bit, non-prefetchable) [size=2K]
        Memory at d0204000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
        Subsystem: Compaq Computer Corporation Unknown device b103
        Flags: bus master, medium devsel, latency 168, IRQ 10
        Memory at d0202000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 20000000-21fff000 (prefetchable)
        Memory window 1: 24000000-25fff000
        I/O window 0: 00003400-000034ff
        I/O window 1: 00003800-000038ff
        16-bit legacy interface ports at 0001

02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)
        Subsystem: Compaq Computer Corporation Unknown device 0093
        Flags: bus master, medium devsel, latency 66, IRQ 9
        Memory at d0200000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 3000 [size=64]
        Capabilities: <access denied>

03:00.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
        Subsystem: Accton Technology Corporation SMC2835W V3 EU Wireless Cardbus Adapter
        Flags: bus master, medium devsel, latency 80, IRQ 10
        Memory at 24000000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>





javier@laptoplinux:~$ ndiswrapper -l
Installed drivers:
smc2835w                driver installed, hardware present 




javier@laptoplinux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      NOT READY!  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=31 dBm   Sensitivity=0/200  
          Retry min limit:0   RTS thr=0 B   Fragment thr=0 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

javier@laptoplinux:~$ 




javier@laptoplinux:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
sit0      Interface doesn't support scanning.






---

### Post by compwiz18 on 2006-12-07
I'm thinking I'm gonna rewrite this from scratch sometime in the next week or so.  Does anyone have any feature requests?

What we have so far:
[LIST]
[*]Wired Profiles, similar to the wireless ones
[*]More info in status icon: ESSID, IP, maybe throughput?
[*]Maybe: fully-automatic connection (wired & wireless)
[/LIST]

---

### Post by compwiz18 on 2006-12-07
@**javierfh**: Looks like you have ndiswrapper configured incorrectly...this isn't the thread to ask for help for that...make a new thread, that way you'll get more help.

---

### Post by yopnono on 2006-12-07
> **compwiz18 said:**
> I'm thinking I'm gonna rewrite this from scratch sometime in the next week or so.  Does anyone have any feature requests?

What we have so far:
[LIST]
[*]Wired Profiles, similar to the wireless ones
[/LIST]

Have you had it :)
I don't have any request except the ones I already asked for.

---

### Post by javierfh on 2006-12-07
> **compwiz18 said:**
> @**javierfh**: Looks like you have ndiswrapper configured incorrectly...this isn't the thread to ask for help for that...make a new thread, that way you'll get more help.

hi,

thanks for your reply.
Well i guess i have the ndiswrapper wrong..that i can see it by the results, no connection. But i would like to ask you some questions...might be very basic, but hope you can give me some light.

I first tried with ndiswrapper but didnt work( in fact worked one second, since the lights flashed, but never again)
So then i read your post and then i uninstalled the ndiswrapper and  start with yours from scratch but didnt work either.

So are your method and ndiswrapper different things?
So can you configure the wlan card from scratch only using your tools? I dont mind if it is ndiswrapper or your tool, i just need to make it work and if i can do it with your tool, i would be pretty happy.

---

### Post by compwiz18 on 2006-12-07
> **javierfh said:**
> hi,

thanks for your reply.
Well i guess i have the ndiswrapper wrong..that i can see it by the results, no connection. But i would like to ask you some questions...might be very basic, but hope you can give me some light.

I first tried with ndiswrapper but didnt work( in fact worked one second, since the lights flashed, but never again)
So then i read your post and then i uninstalled the ndiswrapper and  start with yours from scratch but didnt work either.

So are your method and ndiswrapper different things?
So can you configure the wlan card from scratch only using your tools? I dont mind if it is ndiswrapper or your tool, i just need to make it work and if i can do it with your tool, i would be pretty happy.
I can help you there.

As you may of noticed, there are multiple wireless managers: mine, network-manager, wifi-radar, etc.  These are for configuring the wireless card, so that you can connect to a wireless network.

Then there is ndiswrapper: this is like a driver in Windows.  If makes the wireless card work (the light shine), but doesn't manage your wireless networks.

This program (connection-manager) is for managing wireless networks.  For this to work, you *first* need ndiswrapper to be working, then you can install this tool, or network-manager, or something else.

I hope I explained this clearly.  If you need more help, just ask :D

---

### Post by foxy123 on 2006-12-07
> **compwiz18 said:**
> I'm thinking I'm gonna rewrite this from scratch sometime in the next week or so.  Does anyone have any feature requests?

What we have so far:
[LIST]
[*]Wired Profiles, similar to the wireless ones
[/LIST]

As I've said before, automatic connection would be nice. If wired is present, it connects to wired, if not then to a preferred wireless. If wired is plugged, it automatically switches to it, if it is unplugged it automatically switches to wireless.

---

### Post by javierfh on 2006-12-07
> **compwiz18 said:**
> I can help you there.

As you may of noticed, there are multiple wireless managers: mine, network-manager, wifi-radar, etc.  These are for configuring the wireless card, so that you can connect to a wireless network.

Then there is ndiswrapper: this is like a driver in Windows.  If makes the wireless card work (the light shine), but doesn't manage your wireless networks.

This program (connection-manager) is for managing wireless networks.  For this to work, you *first* need ndiswrapper to be working, then you can install this tool, or network-manager, or something else.

I hope I explained this clearly.  If you need more help, just ask :D


Hi,

yes, thanks a lot. You now make it clear my suspicions.

So i guess first thing i need to do is to make the card to work and for that, i will use the windows driver that will be used by ndiswrapper :)

The reason why i was confused, it is because when i tried to install your packages, it opened that deb installer and complained that there was conflict with network- manager, so i went to synaptics, uninstall it and then install yours, but still didnt work so i guess i went back to try the ndiswrapper. I thought that yours will make it work and would be something similar to ndiswrapper, but now i see its at different level :D

But well now that i know, the first thing is to make the card work and for that i need to configure it then in ndiswrapper, then i might bother you again :)

Thanks for been that kind and thanks for making such tool,

Javi

---

### Post by handaxe on 2006-12-07
[LIST]
[*]Wired Profiles, similar to the wireless ones
[*]fully-automatic connection (wired & wireless)[/LIST]Would be good to get some info besides signal strength by right-clicking the icon or a touch balloon

IP number, attached / visible ESSIDs at a minimum

Using HSDPA, I also monitor throughput Kb/sec KB/sec - up/down, so that would be nice too (like the netspeed prog).

Thanks for all,

HA

---

### Post by compwiz18 on 2006-12-07
> As I've said before, automatic connection would be nice. If wired is present, it connects to wired, if not then to a preferred wireless. If wired is plugged, it automatically switches to it, if it is unplugged it automatically switches to wireless.

So we need to implement a design descision: do we want a daemon that will allow this type of behavior?

on the other hand, this will have to constantly run in the background, taking up system resources...

---

### Post by compwiz18 on 2006-12-07
> **handaxe said:**
> [LIST]
[*]Wired Profiles, similar to the wireless ones
[*]fully-automatic connection (wired & wireless)[/LIST]Would be good to get some info besides signal strength by right-clicking the icon or a touch balloon

IP number, attached / visible ESSIDs at a minimum

Using HSDPA, I also monitor throughput Kb/sec KB/sec - up/down, so that would be nice too (like the netspeed prog).

Thanks for all,

HA
Sounds good.  I'll add this to the feature request list.

---

### Post by Ago12 on 2006-12-07
I'm really waiting the day it will be compliant with suspend2... If it was, I would never have to reboot my lappy!

Sadly, most of the time, after a suspend, I can't change of ESSID...

Scanning does work, but I can't connect, it says that it is sleeping, with no more info :(

And I have to reboot. If I'm at the same place, it is ok, but if I change... I have to reboot each time I go home or school, so twice a day :(

I've tried to ifdown/up, restart the networking daemon, the init.d/autoconnect thing, etc...

At least, I would like to know wich process restart! :(

Thanks for reading :)

---

### Post by yopnono on 2006-12-07
> **Ago12 said:**
> I'm really waiting the day it will be compliant with suspend2... If it was, I would never have to reboot my lappy!

Sadly, most of the time, after a suspend, I can't change of ESSID...

Scanning does work, but I can't connect, it says that it is sleeping, with no more info :(

And I have to reboot. If I'm at the same place, it is ok, but if I change... I have to reboot each time I go home or school, so twice a day :(

I've tried to ifdown/up, restart the networking daemon, the init.d/autoconnect thing, etc...

At least, I would like to know wich process restart! :(

Thanks for reading :)

Never tried suspend2. But by running the auto-connect you restart wpa_supplicant, network interface etc,etc.

```
sudo /etc/init.d/./auto-connect 
```

Also try to killall dhclient and dhclient3 before the auto-connect

---

### Post by Ago12 on 2006-12-07
Ok, I'll try tomorow (I'm at home right now).

BTW, I had a doubt, and now I am sure: from school (open wifi) to home (wpa secured wifi), it works flawlessly.
But the contrary isn't true...

---

### Post by foxy123 on 2006-12-07
> **compwiz18 said:**
> So we need to implement a design descision: do we want a daemon that will allow this type of behavior?

on the other hand, this will have to constantly run in the background, taking up system resources...

Frankly speaking I do not think it will take much resources though I could be mistaken. I guess with daemon you will not need to do 'sudo' thing which a plus.

---

### Post by Thumper322 on 2006-12-07
> **compwiz18 said:**
> I'm thinking I'm gonna rewrite this from scratch sometime in the next week or so.  Does anyone have any feature requests?

What we have so far:
[LIST]
[*]Wired Profiles, similar to the wireless ones
[*]More info in status icon: ESSID, IP, maybe throughput?
[*]Maybe: fully-automatic connection (wired & wireless)
[/LIST]

I'd like:
[LIST]
[*]Automatic switching between wired and wireless connections, like NetworkManager
[*]Support for hidden ESSIDs
[*]Proper display of signal strength when using the ndiswrapper driver
[/LIST]

Not sure if it already does any of those... Also, if it doesn't already, automatic connection to preferred networks would be nice.

---

### Post by Thumper322 on 2006-12-07
> **foxy123 said:**
> Frankly speaking I do not think it will take much resources though I could be mistaken. I guess with daemon you will not need to do 'sudo' thing which a plus.

(Sorry for the double post.)

I didn't notice a system hit when running NetworkManager, which uses a daemon...

Another thought... Would this daemon still work after restoring from suspend/hibernate?

---

### Post by mbobak on 2006-12-07
I've installed the connection-manager and connection-manager-systray programs, and I've got everything working great, except.......

I can't figure how to get the connection-manager-systray program to start automatically.  I've tried System->Sessions->Startup Programs->Add
And I can see that it adds it to the list, but if I exit and restart, it's gone.  There doesn't seem to be any kind of 'Save' or 'Apply' button there.  I even tried hand-editing /usr/share/gnome/default.session, and no luck.

Help!  Any ideas/clues would be appreciated.

Other than not getting it to start in the systray, I *love* this app.  It makes network connectivity as seamless as it should be.  Great job!

-Mark

---

### Post by Frem on 2006-12-07
> **Thumper322 said:**
> I'd like:
[LIST]
[*]Automatic switching between wired and wireless connections, like NetworkManager
[*]Support for hidden ESSIDs
[*]Proper display of signal strength when using the ndiswrapper driver
[/LIST]

Not sure if it already does any of those... Also, if it doesn't already, automatic connection to preferred networks would be nice.

LEAP support! Even better, LEAP on hidden networks. ^_^
My university network uses LEAP and I never managed to get things working using the CVS version of NetworkManager.

---

### Post by mbobak on 2006-12-07
Ok, I figured it out.  After I edited /usr/share/gnome/session.default, I needed to remove $HOME/.gnome2/session cause it was overriding /usr/share/gnome/session.default.  I still don't know why editing via System->Preferences->Sessions didn't work.

-Mark

---

### Post by mbobak on 2006-12-08
I took the liberty of making a minor change....When you put the cursor over the systray icon, I changed the "High", "Good", "Low", "Bad" you see to read "xx% --" followed by "Excellent", " Good", "Fair", "Poor".

Here's the diff:
```
*** systray     2006-11-24 00:20:33.000000000 -0500
--- systray.new 2006-12-08 01:01:03.000000000 -0500
***************
*** 52,66 ****
        def SetIcon(self):
                strength = self.wifi.currentsignal(self.interface)
                if int(strength) >= 75:
!                       return ['/opt/connection-manager/images/high-signal.png', "High"]
                if int(strength) >= 50:
!                       return ['/opt/connection-manager/images/good-signal.png', "Good"]
                if int(strength) >= 25:
!                       return ['/opt/connection-manager/images/low-signal.png', "Low"]
                if int(strength) > 0:
!                       return ['/opt/connection-manager/images/bad-signal.png',"Bad"]
                if int(strength) <= 0:
!                       return ['/opt/connection-manager/images/no-signal.png', "No signal"]
  
        def OnDClick(self,event):
                f = os.popen( 'gksudo connection-manager &', "r" )
--- 52,66 ----
        def SetIcon(self):
                strength = self.wifi.currentsignal(self.interface)
                if int(strength) >= 75:
!                       return ['/opt/connection-manager/images/high-signal.png', str(strength)+"% -- Excellent"]
                if int(strength) >= 50:
!                       return ['/opt/connection-manager/images/good-signal.png', str(strength)+"% -- Good"]
                if int(strength) >= 25:
!                       return ['/opt/connection-manager/images/low-signal.png', str(strength)+"% -- Fair"]
                if int(strength) > 0:
!                       return ['/opt/connection-manager/images/bad-signal.png', str(strength)+"% -- Poor"]
                if int(strength) <= 0:
!                       return ['/opt/connection-manager/images/no-signal.png',  str(strength)+"% -- No Signal"]
  
        def OnDClick(self,event):
                f = os.popen( 'gksudo connection-manager &', "r" )
***************
*** 72,75 ****
  
  if __name__ == "__main__":
        systray = systray(app_conf)
!       systray.main()
\ No newline at end of file
--- 72,75 ----
  
  if __name__ == "__main__":
        systray = systray(app_conf)
!       systray.main()

```


Feel free to use it or not....

-Mark

---

### Post by compwiz18 on 2006-12-08
Cool.  I'll add it after I repair my Ubuntu.

---

### Post by mja on 2006-12-08
Hi all,
I really appreciate all the work put into this program! I did not manage to get Networkmanager to work with my IBM T43 (Kubuntu EDGY). Connection manager, on the other hand, works out of the box!

EDIT: I had to make a symbolic link sudo ln -s /usr/bin/kdesu /usr/bin/gksudo since gksudo does not exist in Kubuntu.

My /etc/network/interfaces looks like:
------------snip------------------
# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
-------------cut---------------------

Now I'm off to try pptpconfig for VPN..Don't know how to tell it to use eth1 and not eth0 when trying to get the VPN-connection. For eth0 (LAN) I managed to get the VPN connection through.

Cheers,
Miika

---

### Post by compwiz18 on 2006-12-08
Interesting note on the gksudo/kdesu thing...We can probably fix that somehow...

---

### Post by CBowers on 2006-12-08
Best Linux wireless app ever! Thanks so much!

---

### Post by tturrisi on 2006-12-08
Curious, will this app run on Etch? What are its dependencies?

---

### Post by foxy123 on 2006-12-08
> **tturrisi said:**
> Curious, will this app run on Etch? What are its dependencies?

I guess compwiz18 could release the source as well. Anyway it has to be done to comply with the GPL licence.

---

### Post by compwiz18 on 2006-12-09
It's Python.  The source **is** the file.

---

### Post by foxy123 on 2006-12-09
> **compwiz18 said:**
> It's Python.  The source **is** the file.

oh, sorry, I have not thought about it ](*,)

---

### Post by compwiz18 on 2006-12-09
No worries.  It's a common misunderstanding :D

---

### Post by tturrisi on 2006-12-09
> **tturrisi said:**
> Curious, will this app run on Etch? What are its dependencies?
I should have asked, "will it work on a debian etch system, what specific dependencies are there, i.e. what versions of what packages are required?"

---

### Post by yopnono on 2006-12-09
> **tturrisi said:**
> I should have asked, "will it work on a debian etch system, what specific dependencies are there, i.e. what versions of what packages are required?"

It's a python script. Python 2.4, don't know if you can use earlier versions.

Depends: libwxgtk2.6-0, python-wxgtk2.6, wpasupplicant

Try and install, and you will find out if it's running or not

---

### Post by yopnono on 2006-12-09
@compwiz18
Think you should set the permission on the .conf files to root only. Like now anyone can read them, and since they hold the WEP,WPA keys, it's better if root only can read them.

---

### Post by tturrisi on 2006-12-09
Thanks, I'll test it.
Very nice!
Works great in Etch, using kernel 2.6.17.2.
The systray applet won't install though because of an unmet dependency.  Etch uses python-GTK2 version 2.8.6-6 and the applet requires a higher ersion apparantly.

---

### Post by yopnono on 2006-12-09
> **tturrisi said:**
> Thanks, I'll test it.
Very nice!
Works great in Etch, using kernel 2.6.17.2.
The systray applet won't install though because of an unmet dependency.  Etch uses python-GTK2 version 2.8.6-6 and the applet requires a higher ersion apparantly.

Try to force it to install.
--ignore-depends=<package>

---

### Post by compwiz18 on 2006-12-09
It won't work though, it needs the version specified because the systray thing was first implemented in the version specified - this is why it doesn't work on Dapper either - but you can try force install just for the heck of it.

---

### Post by tturrisi on 2006-12-09
I didn't try --ignore-depends as I knew it wouldn't work or would possibly create other issues w/ other apps. I really don't need the applet, I can still use the gnome network monitor applet if I want to see the blinky net icon.  The important thing is that I can run the comection-manager via the menu, which I can.  Sometimes when launching it the scan just hangs so I must kill it & launch again.  It always completes a scan by the 3rd try when it does hang.   Sometimes it works the first time too.  The only other isue (can't really call it an issue) is that the signal % differs from the signal % shown by network monitor applet.  I suspect that is due to madwifi (latest version prior to recent security fix in madwifi).

---

### Post by compwiz18 on 2006-12-09
> **tturrisi said:**
> I didn't try --force as I knew it wouldn't work or would possibly create other isues w/ other apps. I really don't need to applet, I can still use the gnome network monitor applet if I want to see the blinky net icon.  The important thing is that I can run the comection-manager via the menu, which I can.  Sometimes when launching it the scan just hangs so I must kill it & launch again.  It always completes a scan by the 3rd try when it does hang.   Sometimes it works the first time too.
That's weird.  Could you try running it in a Terminal and posting the output when it hangs?

---

### Post by tturrisi on 2006-12-09
> **compwiz18 said:**
> That's weird.  Could you try running it in a Terminal and posting the output when it hangs?

well, so far so good, can't get it to hang at scan anymore.  Will try rebooting and see what happens.
```
v240:~# /opt/connection-manager/manager
ath1
0
1
wired: False
link clicked: py:connect(0)
{'encryption': 'on', 'signal': '55', 'ap_mac': '00:0F:B5:9F:DD:04', 'mode': 'Master', 'channel': '11', 'essid': '8724'}
interface: ath1
flushing the routing table
Nothing to flush.
killing previous wpa supps
wpa_supplicant: no process killed
iwconfig ath1 mode Managed
iwconfig ath1 essid "8724" channel 11 key 30B80xxxxx ap 00:0F:B5:9F:DD:04
configuring dhcp
There is already a pid file /var/run/dhclient.pid with pid 6009
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath1/00:11:95:69:94:f4
Sending on   LPF/ath1/00:11:95:69:94:f4
Sending on   Socket/fallback
DHCPREQUEST on ath1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.104 -- renewal in 33471 seconds.
done

```

---

### Post by tturrisi on 2006-12-09
OK, I managed to get it to hang again by rebooting.  I tried to run it 3 times via a terminal, the output is below.  But the 4th time I ran it from the menu & the scan completed and then I connected.

here's the output (as root):
```
v240:~# /opt/connection-manager/manager
ath1
0
1
wired: False
Xlib: unexpected async reply (sequence 0xbc8)!
Killed
v240:~# /opt/connection-manager/manager
ath1
0
1
wired: False
Xlib: unexpected async reply (sequence 0xc8c)!
Killed
v240:~# /opt/connection-manager/manager
ath1
0
1
wired: False
Xlib: unexpected async reply (sequence 0xbd2)!
Killed

```

---

### Post by compwiz18 on 2006-12-09
So it only locks if you run it via the terminal?

The problem looks to be something to do with threads - that is usually the xlib: unexpected async replay error.

---

### Post by tturrisi on 2006-12-09
> **compwiz18 said:**
> So it only locks if you run it via the terminal?

The problem looks to be something to do with threads - that is usually the xlib: unexpected async replay error.
No, it locked before when launching from the menu.  The error does refer to xlib, but I don't know what it refers to exactly nor do I understand it.  Versioning?  I realize this is sorta off track as I'm running Etch and not Ubuntu, but this could help to expedite getting connection-manager into the debian pools, which would be a godsend to all distros.

---

### Post by compwiz18 on 2006-12-09
Well, I don't know...I'm gonna rewrite the entire thing from scratch, should be released by January.  This should hopefully fix this problem...I don't wanna spend too much time if I'm gonna rewrite the entire program anyway.

---

### Post by tturrisi on 2006-12-09
Feature request:

Since the displayed data in the application is basically an htm file in the /tmp dir, it would be cool/useful to be able to select + copy the scan results from the application interface.

This could be useful/fun, esp for those folks whose wifi drivers do not support monitor mode/kismet or who do not wish to use a term + iwlist.  For example, when traveling, or at other locations, one could keep a dated record of the scan, for future reference when traveling to same locations.  Any way to get the current date-time into the htm file?

---

### Post by compwiz18 on 2006-12-09
> **tturrisi said:**
> Feature request:

Since the displayed data in the application is basically an htm file in the /tmp dir, it would be cool/useful to be able to select + copy the scan results from the application interface.

This could be useful/fun, esp for those folks whose wifi drivers do not support monitor mode/kismet or who do not wish to use a term + iwlist.  For example, when traveling, or at other locations, one could keep a dated record of the scan, for future reference when traveling to same locations.  Any way to get the current date-time into the htm file?
Hmm..so you want to keep something like a database of all scans?  I think that could work...and you want the ability to copy text out of the interface?

---

### Post by tturrisi on 2006-12-10
Yes, copy text from the interface since is just an html file in the left frame. (a rt click context menu would be best)  While I myself don't need copy as I can use kismet for scans & logging, others may find it useful.

Ideally, the app could duplicate the windows wireless zero config service.  It's almost there now.  The database could store the preferred wlans as well, or they could stay stored in the present text file.  The windows wifi zero is one of its best features, a no-brainer for users and intuitive-user friendly.

Another request is this:
Let's say one is already connected.  One launches the connection-manager and the scan completes and if one is already connected to a wlan the interface displays "connected" as the last line before the horiz rule separating wlans, and does not display "not connected" as that would be redundant.

Also, one of the neat features of windows wifi zero is this:  When booting, wifi zero loads and does its initial scan in the background.  If one opens the zero app, any subsequent scans must be manually executed.  In other words, only one scan is done automatically, at boot, rather than a scan done each time the app is launched.  I believe this could be duplicated in connection-manager at boot by executing a script that runs 'iwlist interface scan' and connects to the top preferred network in the text list of preferred networks.  And then when connection-manager is launched manually, no scan is done until user clicks 'refresh' button.

I hope I am not out of line suggesting to duplicate windows features.  my logic is that people are used to windows, and moving them over to linux is easier if they have familiar tasks.  I've read many threads in the networking forum here re wifi difficulties; the majority of troubles relate to drivers, and the second most frequent difficulties have to do w/ user friendly tasks and unfamiliarities w/ linux because folks are used to windows 1-2-3 wifi ease of use.

A real user friendly front end to wireless-tools would solve many isues and likely become the most popular wifi related download in all linux distros.  Connection-manager is about 80% there already!

---

### Post by compwiz18 on 2006-12-10
No, I totally agree with you - the Windows wifi tool is 300% better then anything we have.  I was actually attempting to copy it when I started - and I added a couple of things that bugged me - such as having to reset the IP settings manually when you changed networks.

As is, the computer should scan and connect at boot - but you're right, we shouldn't have to scan every time the app is opened... Hopefully, when I rewrite this, the daemon will be able to remember what happened, and then all scans will only be done on demand.

---

### Post by tturrisi on 2006-12-10
Thanks.
I've begun reading up on python in an attempt to doctor connection-manager & it looks interesting so far.  I have lots of exp w/ html & some exp w/php & it's very similar, except for the use of tabs in place of { }.  That may take some getting used to!  Too bad the html used won't support css.  I tried adding css to style the htm output but it does not work.  I changed the initial size of the application, changed some font sizes and changed the text for Encryption. Also, if the scan detects an unsecured wlan it will display Encryption: No (No = green text).  I did this because several morings during the week I sit in a parking lot in DC waiting for a jobsite to open up & there are about 22 wlans in range...:-) Here's what my connection-manager looks like now from my home:

---

### Post by Frem on 2006-12-10
> **compwiz18 said:**
> No, I totally agree with you - the Windows wifi tool is 300% better then anything we have.  I was actually attempting to copy it when I started - and I added a couple of things that bugged me - such as having to reset the IP settings manually when you changed networks.
When NetworkManager works correctly, it blows the Windows wifi tool out of the water. In fact, the windows wifi panel is one of the worst wifi tools around. Noone at the university here uses it, everyone has switched to one of a few third party connection managers that can actually connect to ResNet. I'm sure it's possible to get the default windows wifi to work with hidden WPA2 LEAP networks, but it's a severe pain in the neck.

---

### Post by tturrisi on 2006-12-10
> **Frem said:**
> When NetworkManager works correctly, it blows the Windows wifi tool out of the water. In fact, the windows wifi panel is one of the worst wifi tools around. Noone at the university here uses it, everyone has switched to one of a few third party connection managers that can actually connect to ResNet. I'm sure it's possible to get the default windows wifi to work with hidden WPA2 LEAP networks, but it's a severe pain in the neck.
To do that in windows you need to go to "change the order of preferred netgworks" and manually add the preferred wlan, ssid & passkey. All wlans w/ ssid broadcast 'off' must be added thusly in windows.

---

### Post by Frem on 2006-12-10
Sure, all that sounds fine in theory, but in practice the Windows Wifi manager appears to be incapable of connecting to this network.

It's a WPA2 enterprise network with TKIP and LEAP Auth. This means you need to enter a user name and password to log on to the wifi network. The Windows wifi manager doesn't even have the LEAP option or a space in the network settings to enter a user name. From what I see on the IT help-desk page, you pretty much *have* to use a 3rd party client to connect to this network from Windows. 
(Not that it's much better under Linux. WPA-Supplicant or CVS NetworkManager are pretty much the only ways to go. Lucky Apple users.)

---

### Post by lcohen999 on 2006-12-11
Hello All

I have a quesiton.

With conneciton-manager when I move from one WPA network to another, connection-manager does not seem to re-write the wpa_supplicant.conf file.  So it times out on connecting for that reason.

Any thoughts?

---

### Post by compwiz18 on 2006-12-11
> **Frem said:**
> Sure, all that sounds fine in theory, but in practice the Windows Wifi manager appears to be incapable of connecting to this network.

It's a WPA2 enterprise network with TKIP and LEAP Auth. This means you need to enter a user name and password to log on to the wifi network. The Windows wifi manager doesn't even have the LEAP option or a space in the network settings to enter a user name. From what I see on the IT help-desk page, you pretty much *have* to use a 3rd party client to connect to this network from Windows. 
(Not that it's much better under Linux. WPA-Supplicant or CVS NetworkManager are pretty much the only ways to go. Lucky Apple users.)

You can do this with connection-manager - just edit /opt/connection-manager/wpa_supplicant.conf (using normal WPA syntax), and set the encryption method in connection-manager to WPA.  It will use the custom settings instead of the normal WPA settings.

> **lcohen999 said:**
> Hello All

I have a quesiton.

With conneciton-manager when I move from one WPA network to another, connection-manager does not seem to re-write the wpa_supplicant.conf file.  So it times out on connecting for that reason.

Any thoughts?

I'll look into it...but I'm not quite sure why it wouldn't.

---

### Post by skinny on 2006-12-11
Hi all I have recently got a laptop with a netgear wg111v2 usb wireless connector. I've installed the wireless ok (using ndiswrapper etc) in that it appears in the Networking dialog, and using connection-manager I can see available networks.

However, I am trying to connect to a WPA secured network. I have entered the key, preferred network checked, and tried using a static IP or using a DHCP  referred one. I've tried each of the drivers for WPA as listed previously in this thread, but all to no avail. I can see the network, I just can't connect. I'm just wondering if there's something I've not done thats obvious. I haven't setup anything in any of the data folders of connection-manager, although on inspection my key for the wireless network and the networks ESSID were present in some files in there, so I presume I don't have to do anything in there, however I did see

> 
Quote:
Originally Posted by compwiz18 View Post
Try editing /opt/connection-manager/data/wpa-settings.conf. It uses the same syntax as wpa_supplicant, so if you read the wpa_supplicant man page, this should give you enough info to set it up.


...does this mean I have to setup my own config file there or is it all done for me already :-? 

Does ANY of the settings in Networking (System>Admin>Networking) affect connection-manager? I've tried enabling/disabling the wireless interface (wlan0) just in case but don't see a discernible difference.

Anyhow, I'm off to bed now but all suggestions are welcome

---

### Post by tturrisi on 2006-12-11
I think I found a bug in the Scanning window. This could explain why sometimes the scanning hangs.
This appears in my .xsession-errors
[COLOR="Red"]Window manager warning: Window 0x2200162 (Scanning) sets an MWM hint indicating it isn't resizable, but sets min size 132 x 104 and max size 187 x 104; this doesn't make much sense.[/COLOR]

---

### Post by compwiz18 on 2006-12-11
If you aren't using any fancy WPA encryption type like LEAP or something - if you are just using WPA-Personal or WPA2-Personal it should work fine.

---

### Post by lcohen999 on 2006-12-11
> **compwiz18 said:**
> You can do this with connection-manager - just edit /opt/connection-manager/wpa_supplicant.conf (using normal WPA syntax), and set the encryption method in connection-manager to WPA.  It will use the custom settings instead of the normal WPA settings.



I'll look into it...but I'm not quite sure why it wouldn't.


Thanks, it didn't seem to do it again.

---

### Post by lcohen999 on 2006-12-12
I'm totally lost and now cannot connect to anything

is it possible to re-set everything, set my interface file back to ubuntu scrach and start from the beginning, and if so how :)

---

### Post by compwiz18 on 2006-12-13
Yeah, it's possible: just open up /etc/network/interfaces and put a "#" sign in front of all lines that don't have the word lo in them.  Then reboot.

---

### Post by lcohen999 on 2006-12-13
> **compwiz18 said:**
> Yeah, it's possible: just open up /etc/network/interfaces and put a "#" sign in front of all lines that don't have the word lo in them.  Then reboot.


Thanks, now the $1,000 question.

I'm sure I will want to try connection-manager again.

What should my interfaces file be when I start?

my wireless card is eth1

---

### Post by compwiz18 on 2006-12-13
> **compwiz18 said:**
> Yeah, it's possible: just open up /etc/network/interfaces and put a "#" sign in front of all lines that don't have the word lo in them.  Then reboot.

Like this, at least this is how mine looks and connection-manager works on my computer.

---

### Post by tturrisi on 2006-12-13
Work on my laptop & this is my intefaces file:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
iface eth0 inet dhcp

# home
iface ath1 inet dhcp 
wireless-essid 8724
wireless-key xxxxxxxxxx

auto ath0
auto ath1
auto eth2
auto eth0
```

---

### Post by tsedlmeyer on 2006-12-14
I just installed connection-manager and it is working great.  Thanks for the wonderful contribution.  However there is one security issue that should be addressed.  The network-settings.conf file is created world readable.  WPA pass phrases and WEP keys are stored in the in the clear.  At a minimum the file should not be world readable and preferably the WPA pass phrases and WEP keys would also not be stored in the clear.

---

### Post by compwiz18 on 2006-12-14
Well, I will fix the permissions issue for the next release.  But if we encrypt the passwords, the user will be required to enter a password everytime they need a network key, which is a Bad Thing...network-manager does this, and that's one of the reasons I dislike it so much.

---

### Post by zedfrugnug on 2006-12-15
It doesn't seem to install at all on dapper, for me.
When trying to install everythig seems fine, but after that, connection manager is not in the internet-menu or synaptic. When trying to install again it does the same thing, without stating that it was installed already:confused:

---

### Post by foxy123 on 2006-12-15
> **zedfrugnug said:**
> It doesn't seem to install at all on dapper, for me.
When trying to install everythig seems fine, but after that, connection manager is not in the internet-menu or synaptic. When trying to install again it does the same thing, without stating that it was installed already:confused:

what does

```
dpkg -s connection-manager
```
give you?

---

### Post by zedfrugnug on 2006-12-15
Package "connection manager" not installed.

---

### Post by foxy123 on 2006-12-15
> **zedfrugnug said:**
> Package "connection manager" not installed.

could you then cd to the directory where the deb is and do 
```
sudo dpkg -i connection-manager-1.3.2.deb
```

or whatever version you are trying to install and post the output here

---

### Post by zedfrugnug on 2006-12-15
Thanks for helping.


tom@tom-desktop:~$ sudo dpkg -i /home/tom/connection-manager-1.3.2.deb
Selecteren van voorheen niet geselecteerd pakket connection-manager.
(Database inlezen ... 81575 bestanden en mappen geïnstalleerd.)
Uitpakken van connection-manager (uit .../connection-manager-1.3.2.deb) ...
dpkg: vereistenproblemen verhinderen de configuratie van connection-manager:
 connection-manager is afhankelijk van python-wxgtk2.6; maar:
  Pakket python-wxgtk2.6 is niet geïnstalleerd.
dpkg: fout bij afhandelen van connection-manager (--install):
 vereistenproblemen - blijft ongeconfigureerd
Fouten gevonden tijdens behandelen van:
 connection-manager

It's dutch, but as you probably see, it's missing python-wxgtk2.6

I thought wxgtk2.6 was not necessary, except for the tray icon?
python-wxgtk2.6 can't be installed in dapper, right?

---

### Post by compwiz18 on 2006-12-15
> **zedfrugnug said:**
> Thanks for helping.


tom@tom-desktop:~$ sudo dpkg -i /home/tom/connection-manager-1.3.2.deb
Selecteren van voorheen niet geselecteerd pakket connection-manager.
(Database inlezen ... 81575 bestanden en mappen geïnstalleerd.)
Uitpakken van connection-manager (uit .../connection-manager-1.3.2.deb) ...
dpkg: vereistenproblemen verhinderen de configuratie van connection-manager:
 connection-manager is afhankelijk van python-wxgtk2.6; maar:
  Pakket python-wxgtk2.6 is niet geïnstalleerd.
dpkg: fout bij afhandelen van connection-manager (--install):
 vereistenproblemen - blijft ongeconfigureerd
Fouten gevonden tijdens behandelen van:
 connection-manager

It's dutch, but as you probably see, it's missing python-wxgtk2.6

I thought wxgtk2.6 was not necessary, except for the tray icon?
python-wxgtk2.6 can't be installed in dapper, right?
Yep.

But you will need to enable multiverse/universe repositories: see [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

---

### Post by zedfrugnug on 2006-12-15
fixed python, this also intalled connection manager.

Thanks again:) 

tom@tom-desktop:~$ sudo apt-get install -f
E: Kon vergrendeling /var/lib/dpkg/lock niet verkrijgen - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
tom@tom-desktop:~$ sudo apt-get install -f
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
Vereisten worden verbeterd... Klaar
De volgende extra pakketten zullen geïnstalleerd worden:
  python-wxgtk2.6 python-wxversion
Voorgestelde pakketten:
  wx2.6-doc wx2.6-examples
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  python-wxgtk2.6 python-wxversion
0 pakketten opgewaardeerd, 2 nieuwe pakketten geïnstalleerd, 0 verwijderen en 0 niet opgewaardeerd.
1 pakketten niet volledig geïnstalleerd of verwijderd.
Er moeten 2660kB aan archieven opgehaald worden.
Na het uitpakken zal er 11,8MB extra schijfruimte gebruikt worden.
Wilt u doorgaan [J/n]? j
Ophalen:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe python-wxversion 2.6.1.2ubuntu2 [20,7kB]
Ophalen:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe python-wxgtk2.6 2.6.1.2ubuntu2 [2639kB]
2660kB opgehaald in 4s (586kB/s)
Selecteren van voorheen niet geselecteerd pakket python-wxversion.
(Database inlezen ... 81586 bestanden en mappen geïnstalleerd.)
Uitpakken van python-wxversion (uit .../python-wxversion_2.6.1.2ubuntu2_all.deb) ...
Selecteren van voorheen niet geselecteerd pakket python-wxgtk2.6.
Uitpakken van python-wxgtk2.6 (uit .../python-wxgtk2.6_2.6.1.2ubuntu2_i386.deb) ...
Instellen van python-wxversion (2.6.1.2ubuntu2) ...
Instellen van python-wxgtk2.6 (2.6.1.2ubuntu2) ...

Instellen van connection-manager (1.3.1) ...
 Adding system startup for /etc/init.d/auto-connect ...
   /etc/rcS.d/S40auto-connect -> ../init.d/auto-connect

---

### Post by zedfrugnug on 2006-12-16
Connection manager is now installed, but unfortunately it doesn't find any wireless networks.

My network has WPA. It's on wlan0.
I'm now connected to my neigbourghs network, wich doesn't have any encrytion8) 
I set this set up in the network manager.

iwlist scan now gives:

tom@tom-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:30:BD:FC:71:5E
                    ESSID:"belkin54g"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality:26  Signal level:0  Noise level:17
                    Extra: Last beacon: 3ms ago

sit0      Interface doesn't support scanning.


When I don't have my neibourgh's network set in network manager iwlist scan includes my network:

tom@tom-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:18:70:4A
                    ESSID:"@Home18022"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality:38  Signal level:0  Noise level:64
                    Extra: Last beacon: 1818ms ago
          Cell 02 - Address: 00:30:BD:FC:71:5E
                    ESSID:"belkin54g"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality:23  Signal level:0  Noise level:89
                    Extra: Last beacon: 136ms ago


Also tried sudo /opt/connection-manager/manager;

tom@tom-desktop:~$ sudo /opt/connection-manager/manager
Password:
g
g: ERROR while getting interface flags: No such device
g         Interface doesn't support scanning.

wired: False
tom@tom-desktop:~$

Anyone any idea?

---

### Post by compwiz18 on 2006-12-18
Looks like the interface is wrong...check and make sure the interface is set correctly in the Preferences menu.

---

### Post by tturrisi on 2006-12-19
> **tturrisi said:**
> I think I found a bug in the Scanning window. This could explain why sometimes the scanning hangs.
This appears in my .xsession-errors
[COLOR="Red"]Window manager warning: Window 0x2200162 (Scanning) sets an MWM hint indicating it isn't resizable, but sets min size 132 x 104 and max size 187 x 104; this doesn't make much sense.[/COLOR]

compwiz18 - not sure if you saw the above or not...

---

### Post by zedfrugnug on 2006-12-19
> **compwiz18 said:**
> Looks like the interface is wrong...check and make sure the interface is set correctly in the Preferences menu.

Thanks.

Now I understand; in preferences, for wireless, the default setting was "g".
I assumed this was correct, because the network is a G type.
It should be wlan0. Maybe the default setting in a new version could be changed?
Or do some people actually need this setting to be "g"?

Unfortunattely it still won't connect with WPA encrytion.
I tried all the WPA-drivers metioned earlier in the thread.
The wireless device (netgear WG111V2) works fine on unsecured networks; 
does this mean that, besides connection manager, I should not need any other seperate  drivers? (like ndiswrapper)

About the WPA drivers;
Will there be a pulldown menu for selecting a driver, in the next version?
Maybe you could even automate the selection of a driver on trying to connect; something like:
"the current WPA driver does not work. Would you like connection manager to try other WPA drivers for you?"  Offcourse then the driver that does work would be stored, so you wouldn't have to do this every time.
Maybe I'm asking to much;)  Just hope I might help..

---

### Post by compwiz18 on 2006-12-19
> **tturrisi said:**
> compwiz18 - not sure if you saw the above or not...
Oops, I didn't, thanks for pointing it out again.  That is a little weird, I'll see what I can do for the next version.

---

### Post by compwiz18 on 2006-12-19
> **zedfrugnug said:**
> Thanks.

Now I understand; in preferences, for wireless, the default setting was "g".
I assumed this was correct, because the network is a G type.
It should be wlan0. Maybe the default setting in a new version could be changed?
Or do some people actually need this setting to be "g"?

Unfortunattely it still won't connect with WPA encrytion.
I tried all the WPA-drivers metioned earlier in the thread.
The wireless device (netgear WG111V2) works fine on unsecured networks; 
does this mean that, besides connection manager, I should not need any other seperate  drivers? (like ndiswrapper)

About the WPA drivers;
Will there be a pulldown menu for selecting a driver, in the next version?
Maybe you could even automate the selection of a driver on trying to connect; something like:
"the current WPA driver does not work. Would you like connection manager to try other WPA drivers for you?"  Offcourse then the driver that does work would be stored, so you wouldn't have to do this every time.
Maybe I'm asking to much;)  Just hope I might help..
You're the second person to ask for a popup menu, so a popup menu we shall have.


As for the WPA: Did it work *before* you installed connection manager?  If so, then...we have a bug of some sort.  If not: [http://ubuntuforums.org/showthread.php?p=1634117#post1634117](http://ubuntuforums.org/showthread.php?p=1634117#post1634117) someone with the same card as you got their's work.

---

### Post by wieman01 on 2006-12-19
compwiz18, 

Perhaps I have missed that in your thread... But where exactly do you store the various network keys? In "/etc/network/interfaces"? or somewhere else? One of my concerns is that keys can be retrieved & seen by unprivileged users... Is that possible?

---

### Post by tturrisi on 2006-12-19
/opt/connection-manager/data/network-settings.conf

---

### Post by wieman01 on 2006-12-19
Is it encrypted? Please make sure that the passwords cannot be seen as plain-text ones. Access should be denied to unprivileged users. I assume that one only root can read the file, right?

---

### Post by compwiz18 on 2006-12-19
> **wieman01 said:**
> Is it encrypted? Please make sure that the passwords cannot be seen as plain-text ones. Access should be denied to unprivileged users. I assume that one only root can read the file, right?
On my computer, the keys can be seen by anyone.  But I'm not sure this reflects what is on everyone else's computer, because I **chmod 777**'d mine so I could edit it without being root.  But I will make sure in the next release that only root can view it.

---

### Post by wieman01 on 2006-12-19
That would be great. Just don't like the tought that anybody can get hold of my keys. Perhaps you find a nice method to encrypt/protect the file. I will be tricky to assign it to 'root' only if your network-manager is actually run by a unprivileged local user. But I'll leave it to you to resolve this problem. :-)

---

### Post by compwiz18 on 2006-12-19
My plan is, as of now, to have the daemon take care of everything.  All the unprivleged user (the GUI) does is send commands via DBUS.  Such as "connect to network x" and the daemon will look and load the proper settings.  Sorry I can't explain it well, but it's in my head, and that's where it matters, for now anyway.

edit: and one other question: what are the consequences of something actually getting a hold of your network keys?  if they're already on your computer, they already have access to secured networks, so I feel like I'm missing something...

---

### Post by wieman01 on 2006-12-19
Well, it's just a security thing... Imagine that another user logs on to your computer (after you have created an unprivileged account) and has access to all network keys. That person may simply use those keys for his/her own purposes.

So anybody unprivileged users gaining access to your computer is able to copy the keys & connect happily to all networks that you have ever had access to. I don't think that's secure... If you know what I mean.

---

### Post by compwiz18 on 2006-12-20
> **wieman01 said:**
> Well, it's just a security thing... Imagine that another user logs on to your computer (after you have created an unprivileged account) and has access to all network keys. That person may simply use those keys for his/her own purposes.

So anybody unprivileged users gaining access to your computer is able to copy the keys & connect happily to all networks that you have ever had access to. I don't think that's secure... If you know what I mean.
OK, will be fixed in the next release.

---

### Post by tturrisi on 2006-12-20
FYI - net-admin stores unencrypted keys in /etc/network/interfaces.  Not a really big deal. But it could be handled by storing the keys in a preferences file in the user's home dir, thus they can only be used-seen by the user & root.  An unprivledged user should not be able to even read another user's files or root's files unless he does sudo, but if he can do sudo or gksudo then he does NOT realy have an unprivledged account now does he!

---

### Post by yopnono on 2006-12-20
If you like you can change the permission on the .conf files to root only (read), the CM don't run as user only as root.

Files:
/opt/connection-manager/data/

---

### Post by zedfrugnug on 2006-12-20
> **compwiz18 said:**
> You're the second person to ask for a popup menu, so a popup menu we shall have.


As for the WPA: Did it work *before* you installed connection manager?  If so, then...we have a bug of some sort.  If not: [http://ubuntuforums.org/showthread.php?p=1634117#post1634117](http://ubuntuforums.org/showthread.php?p=1634117#post1634117) someone with the same card as you got their's work.

It only worked on an unsecured network. Guess I do need ndiswrapper.

Might this program go in a repo someday? 
It's a great program; it would be a shame not to expose it more.

Edit:
Connection manager does not actually tell me if it's connected or not, and to what to what network, if it's connected.
Would this be difficult to add?

---

### Post by computerwiz3491 on 2006-12-23
Connection Manager works great, and it seems to be the only thing that allows me to connect to secured wireless networks.
The problem is that at school, they have multiple access points on the same network, and with other OSes it's picked up as one network, but with connection manager, it's one network.
Are there any solutions?

---

### Post by compwiz18 on 2006-12-23
> **computerwiz3491 said:**
> ...The problem is that at school, they have multiple access points on the same network, and with other OSes it's picked up as one network, but with connection manager, it's one network...

Can you reformat that? It doesn't make sense to me...

---

### Post by lcohen999 on 2006-12-24
> **compwiz18 said:**
> Can you reformat that? It doesn't make sense to me...

I think what he means is something like WDS.

One SSID for multiple access points.  So probably it attaches to one MAC address, and can't move between them

---

### Post by lcohen999 on 2006-12-24
I uninstalled connection-manager as it just wasn't working to me.  I tried again, and I can enter in my information and it creates the network-settings.conf, however the wpa_supplicant.conf remains blank so it can never connect.

Any thoughts?

---

### Post by compwiz18 on 2006-12-24
> **lcohen999 said:**
> I uninstalled connection-manager as it just wasn't working to me.  I tried again, and I can enter in my information and it creates the network-settings.conf, however the wpa_supplicant.conf remains blank so it can never connect.

Any thoughts?
Make sure the wpa_supplicant.conf file is writable by root...it should be already though (I don't think it is possible to deny root access to a file)...You did press Save, not Close, in the Network Settings dialog, right?

---

### Post by lcohen999 on 2006-12-24
-rwxr-xr-x 1 root root 73 2006-11-12 00:34 blank.htm
-rw-r--r-- 1 root root 47 2006-12-24 12:49 manager-settings.conf
-rw-r--r-- 1 root root 69 2006-12-24 13:00 network-settings.conf
-rw-r--r-- 1 root root  2 2006-12-24 13:00 wpa_supplicant.conf

and yup, it says "Connecting"... but when I more wpa_supplicant.conf:
lcohen@lcohen-laptop:/opt/connection-manager/data$ more wpa*


lcohen@lcohen-laptop:/opt/connection-manager/data$ 

and network-settings:

lcohen@lcohen-laptop:/opt/connection-manager/data$ more network-settings.conf
[XX]
enc = WPA
favorite = True
key = XXXXXX

lcohen@lcohen-laptop:/opt/connection-manager/data$

---

### Post by robbie75 on 2006-12-26
Hi Compwiz18,
just tried your connection-manager: thanks to you
I finally got my intel centrino wifi connected by wpa ;)
Nice job!

I've previously tried several other tools for that purpose
including network-manager & wifi-radar but:
the former has no support for static IP's settings and
the latter simply doesn't work for me (do not understand why...).

Anyway, there's something that should be added (IMHO :) )
1)the ability to disconnect from previously connected lans
2)a better management of dns/domain (i.e. one shoulnd't be
obliged to enter just 2 dns or should be possible keep on using 
the predefined configuration or, at least, one should have
 the ability to enter the "domain" too)

So, since I'm a developer, I can help you developing ;)

I was also thinking about the integration of your code into
the gnome's network-admin so that we can have a full functional
gui to manage interfaces along with the ability to use wpa as well ;)

Thank you for your time and let me now ;)
Rob

---

### Post by Shack on 2006-12-27
When I double click CM.deb file I get error:
Error: Depency is not satifiable: libwxgtk2.6-0

When I searched about this file (libwxgtk2.6-0) I found out that this file depents on ~10 other files? (Yes I'm total newbie) 

So which packets should be installed before I can install CM?

Thanks already.

---

### Post by Patrick-Ruff on 2006-12-27
> When I double click CM.deb file I get error:
Error: Depency is not satifiable: libwxgtk2.6-0

When I searched about this file (libwxgtk2.6-0) I found out that this file depents on ~10 other files? (Yes I'm total newbie)

So which packets should be installed before I can install CM?

Thanks already.

install that libwxgtk, and all it's dependencies, and then install the connections manager.

---

### Post by Patrick-Ruff on 2006-12-27
also, the links to the screenshots don't work.

---

### Post by Shack on 2006-12-27
> **Patrick-Ruff said:**
> install that libwxgtk, and all it's dependencies, and then install the connections manager.

I was trying but I ran to the wall.

When I was installing one dependencie it said that I need to install dependencie libc6, ok I tried to install that one but I got error that I already have later version.

---

### Post by Patrick-Ruff on 2006-12-27
I'm pretty sure theres a command that installs all dependancies, it's in the apt-get command.

---

### Post by Shack on 2006-12-27
> **Patrick-Ruff said:**
> I'm pretty sure theres a command that installs all dependancies, it's in the apt-get command.

Haven't found out that yet. But it's strange I have those needes dependancies but I can't install them because I have wrong versions or something? More precise help would be very welcome. Maybe connection manager developers could help if they read this thread.

---

### Post by speedwell68 on 2006-12-27
Hi,  I'm a relative Linux noob and was having problems with WEP on my wireless network, every time I rebooted I no longer had access to the net until I manually reset my connection.  Installed this and the problem has gone away.  Ace, it seems to be stable, very happy.

---

### Post by folke on 2007-01-01
Arrh, I think I borked my wifi settings somhow :)

I had everything setup with the help of this tread: [http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)

Then I tried to install the network manager-manager and it didn't work so well for me.
So I thougt that I just removed the network manager with --purge and put back my old settings in /etc/network/interfaces.

```
auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid sumfink.nice
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk sumfink with nice numbers....
```
But no cigar, I can't get ip from my AP anymore.
Does the network-manager change anything other than files in /opt/network-manager ?

Soon, it looks like a full reinstall for me  :)

Any ideas?

--
Regards Folke

---

### Post by compwiz18 on 2007-01-01
Nope, doesn't change anything other then the stuff in the /opt/connection-manager folder...try rebooting a couple of times before you reformat - there is no reason this should be happening.  And make sure your /etc/network/interfaces file is correct - you may have entered the wrong key or something...(I'm not saying you did, but check anyways) :D

---

### Post by .tommie on 2007-01-02
Installed Connection Manager instead of NetworkManager on my personal workstation and it works great! No more annoying pop-up asking for a key-ring password. :mrgreen: 

The family computer is another story. Connecting manually with Connection Manager to the WLAN does work, but Connection Manager does not automagically connect to the WLAN like it does on my workstation (after a reboot for instance). Any idea on how to solve this little annoyance? :-k

---

### Post by compwiz18 on 2007-01-02
> **.tommie said:**
> Installed Connection Manager instead of NetworkManager on my personal workstation and it works great! No more annoying pop-up asking for a key-ring password. :mrgreen: 

The family computer is another story. Connecting manually with Connection Manager to the WLAN does work, but Connection Manager does not automagically connect to the WLAN like it does on my workstation (after a reboot for instance). Any idea on how to solve this little annoyance? :-k
Make sure that you have removed network-manager-gnome and that you don't have wifi-radar installed and your **/etc/network/interfaces** file has only information about the loopback interface (lo): it should look like
```
auto lo
iface lo inet loopback

```

---

### Post by yopnono on 2007-01-02
You can have the wifi interface set to DHCP as well. I have and it works well. Your script now check and enable the interface so it really don't make any different anymore

---

### Post by .tommie on 2007-01-03
Indeed, I already compared the two /etc/network/interfaces files and it appears my workstation had ```
auto ath0
iface ath0 inet dhcp
``` and the family computer did not have these lines. Added them to /etc/network/interfaces *et voila*, connection up after a reboot.

I'm kinda confused with your latest instructions compwiz18... should these lines be added or removed for Connection Manager to do it's work?

---

### Post by compwiz18 on 2007-01-03
> **.tommie said:**
> Indeed, I already compared the two /etc/network/interfaces files and it appears my workstation had ```
auto ath0
iface ath0 inet dhcp
``` and the family computer did not have these lines. Added them to /etc/network/interfaces *et voila*, connection up after a reboot.

I'm kinda confused with your latest instructions compwiz18... should these lines be added or removed for Connection Manager to do it's work?
if it works, just keep it that way :D

in theory, it shouldn't matter if the lines are there or not, but you know how computers can be sometimes...I was just having you change things around until it worked, sometimes the best way to fix it is just to change random settings that shouldn't matter.

---

### Post by .tommie on 2007-01-03
> **compwiz18 said:**
> if it works, just keep it that way :D

in theory, it shouldn't matter if the lines are there or not, but you know how computers can be sometimes...I was just having you change things around until it worked, sometimes the best way to fix it is just to change random settings that shouldn't matter.

Alright, and thank you for the rapid assistance (you too *yopnono)*! :cool:

---

### Post by compwiz18 on 2007-01-06
Howdy, a few questions for everyone:

**1.** I'm about to write the GUI for Connection Manager 2 - does anyone have any suggestions?

**2.** If anyone feels like designing a GUI in Python using the GUI language of choice (ie pyGTK, wxpython, ncurses [a terminal version would be awesome], tk, QT, etc), feel free, and I'll attempt to add the functionality to it for you - shouldn't be too hard because the daemon does all the work, all the GUI does is tell the daemon what needs to happen.

**3.** I'm also thinking that I'll make a website for it so it will have an official download place.  Good idea?

**4.** And as one last thing, I'm thinking the name should be changed.  People are getting it too confused with network-manager in my opinion.  Suggestions?

just so everyone knows, I will be using pyGTK this time, NOT wxpython as I did last time - this should led to less depedencies

---

### Post by tturrisi on 2007-01-06
> **compwiz18 said:**
> Howdy, a few questions for everyone:

**1.** I'm about to write the GUI for Connection Manager 2 - does anyone have any suggestions?

**2.** If anyone feels like designing a GUI in Python using the GUI language of choice (ie pyGTK, tk, QT, etc), feel free, and I'll attempt to add the functionality to it for you - shouldn't be too hard because the daemon does all the work, all the GUI does is tell the daemon what needs to happen.

**3.** I'm also thinking that I'll make a website for it so it will have an official download place.  Good idea?

**4.** And as one last thing, I'm thinking the name should be changed.  People are getting it too confused with network-manager in my opinion.  Suggestions?
1. many are already given in this thread:
a. encrypted password or root only access to it.
b. signal level display.
3. implement as many windows WZC as possible.

2. pass

3. good idea! 

4. agreed.
a. easy-wifi
b. wland (d for daemon)
c. wifid
d. wifiFE (FE for front end)
some puns:
e. wife (wireless internet front end, throw in a few nag screens!)
f. wicd (wicked -wireless interface connection daemon)

---

### Post by amonsul on 2007-01-06
4) Names:

- connect me
- wireless connector

---

### Post by yopnono on 2007-01-06
WCM = Wifi/Wireless/Wlan Connection Manager
ICM = Internet Connection Manager

---

### Post by compwiz18 on 2007-01-06
OK, Thanks for the names everyone :D I'll pick one sometime soon, so if anyone else has more, thats great :D

Also, version 2 has a new encryption system allowing the user to define "templates", which are then read by the program and turned into WPA supplicant config files - of course, it will ship with a few, such as WPA, WEP, EAP, LEAP, so the end user never has to know this even exists, but it would allow people that have encryption methods not supported originally to make a template so that they could use their method with this program.  This also makes it very easy for me to add more encryption types, so if someone has a working wpa_supplicant.conf file with a funky encyption type that they would like to see in version 2, post it here, and I'll see what I can do.

I finished the backend yesterday :D so now I just  have to write the GUI, which should be pretty easy.

---

### Post by amonsul on 2007-01-07
Ok you wanna more????

1) aero (or aereo)
2) aero (or aereo) connection
3) aero (or aereo) manager
4) aero (or aereo) wireless
5) aero (or aereo) connector
6) be wireless
7) stealth connector (ok its a joke)




I think my best choise is "connect me" because its personal and not so anonym.

---

### Post by d-E-a-D on 2007-01-08
Compwiz18 you're tha man! Thanks for your time doing so great things for our broadcom's.

I'm using Hp dv5xxx series and it works great! I've a broadcom 4319 adapter and for now I'm using a simple wireless connection without hidden ESSID and without KEY, just mac-address blocked. If I use some other in the future I'll report here!
Hope connection manager will soon be on the repos 4 all the community !! :D

Cumps

---

### Post by compwiz18 on 2007-01-08
> **d-E-a-D said:**
> Compwiz18 you're tha man! Thanks for your time doing so great things for our broadcom's.

I'm using Hp dv5xxx series and it works great! I've a broadcom 4319 adapter and for now I'm using a simple wireless connection without hidden ESSID and without KEY, just mac-address blocked. If I use some other in the future I'll report here!
Hope connection manager will soon be on the repos 4 all the community !! :D

Cumps
Thanks!  and thanks for your help with the graphics card, that is the best tutorial around for the ATI xpress 200m :D

---

### Post by mespork on 2007-01-10
Just wanted to thank you for connection-manager. It works great, exactly what I was looking for.

---

### Post by lcohen999 on 2007-01-10
some other suggestions for version 2.

a)  re-setting the interfaces file to 'stock' so connection-manager works
      I have never gotten connection-manager to work, it could be because i use wpa_supplicant manually, so  a backup/reset tool i'm sure could clear up a lot of problems for new installs
b)  include an upgrade path where people using wpa_supplicant on their own with multiple networks (like me) can import their .conf file into connection-manager
c)  better error reporting.  When I try and connect and nothing happens, it tries for a minute then dies, but I get no error of what happened, or what went wrong.  Some feedback so I can fix it would be great

Thanks! :)

---

### Post by compwiz18 on 2007-01-10
> **lcohen999 said:**
> some other suggestions for version 2.
a)  re-setting the interfaces file to 'stock' so connection-manager works
      I have never gotten connection-manager to work, it could be because i use wpa_supplicant manually, so  a backup/reset tool i'm sure could clear up a lot of problems for new installs
OK, I'll see if there is some way we can recreate the interfaces file...this seems to be a problem sometimes, even though it shouldn't be.
> b)  include an upgrade path where people using wpa_supplicant on their own with multiple networks (like me) can import their .conf file into connection-manager

Hmm...I see your point.  I'll look into it.  Just for kicks, could you post yours?  It gives me something to go by if I try and write that.

> c)  better error reporting.  When I try and connect and nothing happens, it tries for a minute then dies, but I get no error of what happened, or what went wrong.  Some feedback so I can fix it would be great

Hopefully I'll be able to do that - it is kind of tricky to implement, because you then have threads and stuff, but certainly possible

---

### Post by lcohen999 on 2007-01-10
> **compwiz18 said:**
> OK, I'll see if there is some way we can recreate the interfaces file...this seems to be a problem sometimes, even though it shouldn't be.


Hmm...I see your point.  I'll look into it.  Just for kicks, could you post yours?  It gives me something to go by if I try and write that.



Hopefully I'll be able to do that - it is kind of tricky to implement, because you then have threads and stuff, but certainly possible

here is my wpa_supplicant.conf file.  I cannot get it to work using connection-manager at all, again possibly because of the way this, and my interfaces file (which i have also included) are setup.

wpa_supplicant.conf

ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
        ssid="XX"
        scan_ssid=1
        proto=RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP
        group=CCMP
        #psk="*683vXXXSu4.D"
        psk=2e34f9e4b0f034e6XXXXf7fe2440b49dc3bea5
}


network={
       ssid="cfXXXe"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=CCMP
       group=CCMP
       #psk="*683voXXXXLSu4.D"
	psk=9d8a689f468acXXXXX1080f8e4d8dc8ecf579cebd34e

}

network={
        ssid="iybXXXs"
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
        #psk="T?dXXX5&<PKx%o"
        psk=be9a06819bXXXX93d74d86131239c28390a4ff4145
}

/etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

iface eth1 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

and my command line to start wpa_supplicant:

sudo wpa_supplicant -w -Dwext -i eth1 -c/etc/wpa_supplicant.conf

---

### Post by tturrisi on 2007-01-10
(c) above could possible hnadled by generating a log file in the event of failure to connect, and a gui button that loads the log in the system's default viewer, or greps that last 10 lines or so.

---

### Post by compwiz18 on 2007-01-10
> **tturrisi said:**
> (c) above could possible hnadled by generating a log file in the event of failure to connect, and a gui button that loads the log in the system's default viewer, or greps that last 10 lines or so.
Yeah, good idea.  Got to leave now, but I'll work on it later.

---

### Post by KHatfull on 2007-01-11
Hi, nice job here, found this just today.

One thing...I have two networks close to me with the SSID of linksys....mine and a neighbors.  In the settings file it appears that a SSID (and therefore settings) can only appear once since the header for the particular network's settings is the SSID.

You might consider appending the MAC of the AP to the SSID in the settings file to make network settings pretty much unique, or just use the AP MAC for that matter although SSID+MAC would be better for us humans.

You could then read the AP MAC on scan and know which settings CM should use should the user connect to that network since you can read the tailing 12 characters of the settings header in the config file.   This would allow one to have settings for two different networks with the same SSID but different, say, WEP keys.  Make sense?

Just  a thought.

-Keith

---

### Post by compwiz18 on 2007-01-11
Yeah, you have an excellent point.  I've thought a little bit about this before, and I think it will make it in to verson 2.  May I also suggest you change your essid?  It is incredibly tempting for hackers that see an essid of "linksys" - the default :D

My only concern was that some people apparently have networks with multiple access points, but one essid, and like to travel seamlessly between them - but I think that this doesn't work anyway, even with the current settings.

---

### Post by t_anjan on 2007-01-14
Hey compwiz18, good work. At least you have attempted to do something like this, which should have been a part of the OS itself.

I'm on Edgy.

I've got a Netgear WG111v2 USB dongle. My wireless network is originally WPA encrypted. But for testing purposes, I switched off all encryptions. 
My dongle is installed using ndiswrapper. 'iwlist scan' correctly shows the available wireless network. 
I didn't have network manager or wpa-supplicant installed. Your software automatically installed wpa-supplicant. All went well. On execution, your software also showed the available wireless network.

But on pressing 'Connect', a dialog saying 'Please wait' appears for about a minute and disappears without the connection being established.

What am I doing wrong?

---

### Post by lcohen999 on 2007-01-14
Can you connect with wpa_supplicant only?

---

### Post by t_anjan on 2007-01-15
I cannot connect at all, whatever I use. The max I'm able to achieve is detecting the wireless network. Network Manager, WPA-Supplicant, et al have all be unsuccessful.

---

### Post by lcohen999 on 2007-01-15
post your wpa_supplicant.conf so we can see, or look at mine for example....

---

### Post by t_anjan on 2007-01-15
My wpa_supplicant.conf

```
# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=2
fast_reauth=1

network={
        ssid="AnjanWireless"
	scan_ssid=1
       	key_mgmt=WPA-PSK
	proto=WPA
       	#pairwise=CCMP TKIP
       	#group=CCMP TKIP
        #psk="<hidden>"
        psk=<hidden>
}
```

---

### Post by lcohen999 on 2007-01-15
I am guessing you are using WPA with TPIK? 

if so, add back pairwise and group, but drop CCMP

CCMP = AES and/or WPA2

also post your connection result

ie:

lcohen@lcohen-laptop:~$ sudo wpa_supplicant -w -Dwext -i eth1 -c/etc/wpa_supplicant.cfhome
Password:
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:00:00:00:00:00 (SSID='sds' freq=0 MHz)
Associated with 00:00:00:00:00:00
WPA: Key negotiation completed with 00:00:00:00:00:00 [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to 00:00:00:00:00:00 completed (auth) [id=1 id_str=]

this connection is a WPA with AES

---

### Post by t_anjan on 2007-01-15
Yes, I'm using WPA-PSK with TKIP.I've made the change to the wpa_supplicant.conf file, as you suggested. Now it looks like:

```
# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=2
fast_reauth=1

network={
        ssid="AnjanWireless"
	scan_ssid=1
       	key_mgmt=WPA-PSK
	proto=WPA
       	pairwise=TKIP
       	group=TKIP
        #psk="<hidden>"
        psk=<hidden>
}
```

My connection output:

```
anjan@supernal:~$ **sudo wpa_supplicant -w -Dwext -i wlan0 -c/etc/wpa_supplicant.conf**
Password:
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 7 value 0x1 - ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/wlan0' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.

ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 7 value 0x0 - Failed to disable WPA in the driver.
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - anjan@supernal:~$ 
```

---

### Post by lcohen999 on 2007-01-15
at this point you got me, but wpa_supplicant seems to be setup OK.

I am wondering if you should try to re-setup or update your wireless driver.

Also do a sudo rm /var/run/wpa_supplicant and do a ps -ef | grep wpa_ and make sure nothing is running and try again

---

### Post by Mike_Longbow on 2007-01-15
compwiz18, you're great. I think I talk by everyone when I thank you for this great contribution to the community. It works flawlessly on the wep based networks I use around here (I haven't tried wpa since there're no wpa networks around this place). And also de autoconnect at boot and after resume feature works just fine.
The only thing I just want to ask (if not beg hehehe) is a systray icon for dapper. It would be perfect.

---

### Post by t_anjan on 2007-01-16
> **lcohen999 said:**
> at this point you got me, but wpa_supplicant seems to be setup OK.

I am wondering if you should try to re-setup or update your wireless driver.

Also do a sudo rm /var/run/wpa_supplicant and do a ps -ef | grep wpa_ and make sure nothing is running and try again

I get this as output for **ps -ef | grep wpa_**

```
root      3721     1  0 17:03 ?        00:00:00 /sbin/wpa_supplicant -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D wext -C /var/run/wpa_supplicant
anjan     6410  6250  0 17:36 pts/0    00:00:00 grep wpa_
```

I don't know what to make of it.........

---

### Post by t_anjan on 2007-01-16
To heck with WPA. I've temporarily disabled all security on my router. I want Edgy to connect to my unsecured router. 

My "interfaces" file:
```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid AnjanWireless
wireless-channel 2
wireless-mode managed
```

Output of **sudo /etc/init.d/networking restart**

```
anjan@supernal:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.wlan0.pid with pid 8963
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:18:4d:08:c7:0e
Sending on   LPF/wlan0/00:18:4d:08:c7:0e
Sending on   Socket/fallback
[B][COLOR="Red"]Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; Operation not supported.[/COLOR][/B]
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:18:4d:08:c7:0e
Sending on   LPF/wlan0/00:18:4d:08:c7:0e
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

I think these two lines are the most important:
```
[B][COLOR="Red"]Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; Operation not supported.[/COLOR][/B]
```

I have no idea why SET is not working. Any ideas? I can't even connect to an unsecured network!!!

---

### Post by compwiz18 on 2007-01-16
[QUOTE=the iwconfig man page]iwconfig eth0 freq 2422000000
iwconfig eth0 freq 2.422G
iwconfig eth0 channel 3
iwconfig eth0 channel auto[/QUOTE]

you could try setting the frequency manual, by doing **sudo iwconfig essid "youressid"** (set the essid) and then use one of the examples above to set the frequency?  You'll probably have to change the numbers.

---

### Post by Graham1 on 2007-01-16
Please delete this post. Problem solved.

:)

---

### Post by t_anjan on 2007-01-17
> **compwiz18 said:**
> you could try setting the frequency manual, by doing **sudo iwconfig essid "youressid"** (set the essid) and then use one of the examples above to set the frequency?  You'll probably have to change the numbers.

That doesn't make a difference. On executing the "iwconfig wlan0 freq <any freq>" command, I get the same error.

---

### Post by compwiz18 on 2007-01-17
Did you try "iwconfig wlan0 freq any" ?  I'm not sure if that will work either...

---

### Post by t_anjan on 2007-01-17
"any" is an invalid argument.

Do u know of ANY success story about  your program working on AMD64 Edgy? With Netgear WG111v2? Any driver?

---

### Post by compwiz18 on 2007-01-17
Can you get your card to work using iwconfig and wpa_supplicant?  If so, then this program should work with your computer, because it uses iwconfig and wpa_supplicant.  I use amd64 edgy, so that isn't an issue.  As for the wireless card, I've got a Broadcom 4318 (yay!) that uses ndiswrapper.

---

### Post by Graham1 on 2007-01-18
Hi

I'm using a static IP with WPA and although I'm connected, the notification area icon for connection manager is showing an exclaimation mark. As soon as I connect, it shows a high signal and then drops to the exclaimation mark. Btw, I'm using ipw2200.

:)

---

### Post by yopnono on 2007-01-18
> **Graham1 said:**
> Hi

I'm using a static IP with WPA and although I'm connected, the notification area icon for connection manager is showing an exclaimation mark. As soon as I connect, it shows a high signal and then drops to the exclaimation mark. Btw, I'm using ipw2200.

:)

Do you have any other wpa_supplicant connected? Do a ps -e in the terminal and check for any other wpa connection, it should only be 1 if more you get this behavior.

---

### Post by cartifex on 2007-01-18
When I try to download the attachment it says I am not authorised.

---

### Post by compwiz18 on 2007-01-18
> **cartifex said:**
> When I try to download the attachment it says I am not authorised.
Weird.

Can you give the link of the page you are trying to download from?  I need to know if it is Ubuntu Forums that is saying you aren't authorized, or if it is my website (compwiz18.blackhole.cx) that is saying you aren't authorized.

---

### Post by nsleiman on 2007-01-18
i downloaded 2 debs now, faced no prob

---

### Post by Graham1 on 2007-01-18
> **yopnono said:**
> Do you have any other wpa_supplicant connected? Do a ps -e in the terminal and check for any other wpa connection, it should only be 1 if more you get this behavior.

I don't think there are any other wpa_supplicant's connected but here is my output below:-

PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   10 ?        00:00:00 kacpid
   11 ?        00:00:00 kacpi_notify
  116 ?        00:00:00 kseriod
  147 ?        00:00:00 pdflush
  148 ?        00:00:00 pdflush
  149 ?        00:00:00 kswapd0
  150 ?        00:00:00 aio/0
 1690 ?        00:00:00 khubd
 1772 ?        00:00:00 kjournald
 1845 ?        00:00:00 logd
 1991 ?        00:00:00 udevd
 2741 ?        00:00:00 irda_sir_wq
 2757 ?        00:00:00 kpsmoused
 2763 ?        00:00:00 shpchpd
 2970 ?        00:00:00 pccardd
 3003 ?        00:00:00 pccardd
 3004 ?        00:00:00 ipw2200/0
 3335 ?        00:00:00 wpa_supplicant
 3527 tty1     00:00:00 getty
 3528 tty2     00:00:00 getty
 3529 tty3     00:00:00 getty
 3530 tty4     00:00:00 getty
 3531 tty5     00:00:00 getty
 3532 tty6     00:00:00 getty
 3754 ?        00:00:00 acpid
 3870 ?        00:00:00 dd
 3872 ?        00:00:00 klogd
 3953 ?        00:00:00 gdm
 3954 ?        00:00:00 gdm
 3973 tty7     00:00:26 Xorg
 4010 ?        00:00:00 hpiod
 4013 ?        00:00:00 python
 4061 ?        00:00:00 dbus-daemon
 4076 ?        00:00:02 hald
 4077 ?        00:00:00 hald-runner
 4083 ?        00:00:00 hald-addon-acpi
 4097 ?        00:00:00 hald-addon-keyb
 4101 ?        00:00:00 hald-addon-keyb
 4108 ?        00:00:00 hald-addon-keyb
 4133 ?        00:00:00 dhcdbd
 4149 ?        00:00:00 perl
 4197 ?        00:00:00 ondemand
 4257 ?        00:00:00 hcid
 4261 ?        00:00:00 sdpd
 4273 ?        00:00:00 krfcommd
 4297 ?        00:00:00 atd
 4310 ?        00:00:00 cron
 4406 ?        00:00:00 x-session-manag
 4441 ?        00:00:00 ssh-agent
 4444 ?        00:00:00 dbus-launch
 4445 ?        00:00:00 dbus-daemon
 4447 ?        00:00:00 gconfd-2
 4450 ?        00:00:00 gnome-keyring-d
 4453 ?        00:00:00 gnome-settings-
 4462 ?        00:00:00 sh
 4463 ?        00:00:00 esd
 4470 ?        00:00:03 metacity
 4475 ?        00:00:02 gnome-panel
 4477 ?        00:00:01 nautilus
 4481 ?        00:00:00 bonobo-activati
 4485 ?        00:00:00 gnome-vfs-daemo
 4486 ?        00:00:00 gnome-volume-ma
 4496 ?        00:00:00 update-notifier
 4498 ?        00:00:00 evolution-alarm
 4502 ?        00:00:00 connection-mana
 4508 ?        00:00:02 python
 4511 ?        00:00:00 gnome-cups-icon
 4519 ?        00:00:00 gnome-power-man
 4524 ?        00:00:00 notification-da
 4534 ?        00:00:00 evolution-data-
 4537 ?        00:00:00 mapping-daemon
 4541 ?        00:00:00 evolution-excha
 4576 ?        00:00:00 tomboy
 4606 ?        00:00:00 mixer_applet2
 4637 ?        00:00:00 gnome-screensav
 4897 ?        00:00:30 opera
 4921 ?        00:00:00 operapluginwrap <defunct>
 5785 ?        00:00:00 cupsd
 5976 ?        00:00:00 syslogd
 6207 ?        00:00:00 gnome-terminal
 6211 ?        00:00:00 gnome-pty-helpe
 6212 pts/0    00:00:00 bash
 6472 pts/0    00:00:00 ps

:)

---

### Post by yopnono on 2007-01-18
> **Graham1 said:**
> I don't think there are any other wpa_supplicant's connected but here is my output below:-

Ok. Then make sure you wifi card is enabled, then disable it, the enable it again.
And try to connect.

Use network-admin to do this.

---

### Post by Graham1 on 2007-01-18
> **yopnono said:**
> Ok. Then make sure you wifi card is enabled, then disable it, the enable it again.
And try to connect.

Use network-admin to do this.

Same thing :(. On selecting "Connect", full green bars, which drops and then the exclaimation mark. Strange thing is the internet works fine.

:)

---

### Post by yopnono on 2007-01-19
@compwiz18

Since you are rebuilding the application then you may like to change the icon aswell, maybe something like this one.

[http://www.gnome-look.org/content/show.php?content=50066](http://www.gnome-look.org/content/show.php?content=50066)

---

### Post by compwiz18 on 2007-01-19
Good idea.  I'll do that.

Status update: Very near completion, can connect to most normal networks (using wep/wpa/anything), need to add a dialog box so that a user can specify a hidden network to connect to, and the preferences box.  (these features already exist, just a matter of adding them to the gui)

except I have exams - so don't expect much this week

---

### Post by yopnono on 2007-01-19
> **compwiz18 said:**
> 
except I have exams

Good luck with it.

---

### Post by compwiz18 on 2007-01-19
> **yopnono said:**
> Good luck with it.
thanks :D

---

### Post by Ago12 on 2007-01-20
Yep, good luck ^^

Sorry, I won't pray for you, I have all week exams too :D

*goes to the library*

---

### Post by compwiz18 on 2007-01-21
Howdy

Just so you all don't think I've given up on this, I've attached some screens from the new version.  yes, I did remove the name from the title bar.  It's still a secret :biggrin:

Right now, we have a (much needed) cancel button and a nice little progress bar that bounces, along with all the features from the previous version.  The one you see there is exactly the same as the one we have now, feature wise, with the addition of the cancel button.

Yes, I still plan I adding your icon, yopono ;)  Just haven't done that yet.

Hopefully sometime within a week or so we shall have the finished version.  All that needs to be done is implement the connecting to hidden networks, wired networks, and Preferences.  These are already implemented in the backend, I just haven't gotten them into the GUI yet.

edit: one more thing: I will post it back here, and let the people who have been following this thread test it before I release it on the front post.  That way there won't be as many bugs ;) although I used some of the same python functions and regex from the old version, so hopefully it should be less buggy then the first one.

---

### Post by yopnono on 2007-01-21
Looks good, I truly like the cancel button. As you said much needed :)
"Yes, I still plan I adding your icon, yopono  Just haven't done that yet."
It's not a problem if you were to use it or not, just that if you are rebuilding it, then why not change from the wifi icon you are using from wifi-radar project ;)

Question? 
It's using a daemon, how much does it use for resources.

---

### Post by .tommie on 2007-01-21
Could you implement an info-box? This way people can check which version they are using (don't know what version I'm running currently). :-\"

---

### Post by compwiz18 on 2007-01-21
At the moment, the daemon is taking up 4.8 MB of RAM.  Not great, not terrible.

edit: the GUI takes about 12.1 MB of RAM, so between the two they use a total of 16.9 MB.

I'll see what I can do about an About box.

---

### Post by Graham1 on 2007-01-21
compwiz18

Any idea about my problem? I.e Showing "No Signal" icon even though I'm connected with 87 signal strength :confused:. Btw, using WPA if that helps.

:)

---

### Post by compwiz18 on 2007-01-21
> **Graham1 said:**
> compwiz18

Any idea about my problem? I.e Showing "No Signal" icon even though I'm connected with 87 signal strength :confused:. Btw, using WPA if that helps.

:)
Could you run iwconfig and give the output?  Thanks.

---

### Post by Graham1 on 2007-01-22
> **compwiz18 said:**
> Could you run iwconfig and give the output?  Thanks.

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"*<[COLOR="Blue"]essid[/COLOR]>*"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: *<[COLOR="Blue"]mac address[/COLOR]>*   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=0/100  Signal level=-44 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:98

sit0      no wireless extensions.

---

### Post by compwiz18 on 2007-01-22
> **Graham1 said:**
> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"*<[COLOR="Blue"]essid[/COLOR]>*"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: *<[COLOR="Blue"]mac address[/COLOR]>*   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=0/100  Signal level=-44 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:98

sit0      no wireless extensions.
If you notice - iwconfig is showing Link Quality=0/100, so that is as good as my program can do.  I would guess that you are using ndiswrapper?

---

### Post by Graham1 on 2007-01-22
> **compwiz18 said:**
> If you notice - iwconfig is showing Link Quality=0/100, so that is as good as my program can do.  I would guess that you are using ndiswrapper?

I see :). Not sure whether I am using ndiswrapper or not :confused:. Before installing Connection Manager, I manually had to edit /etc/network/interfaces and /etc/wpa_supplicant.conf to get my WPA connection to work (I didn't install anything ndiswrapper related beforehand). 

I haven't noticed any problems with my link but I can guess I can always rename the no signal png file to the full link png (and hope my connections doesn't break :wink: ). 

Btw, this package is excellent for me as I change between networks (dhcp and static) so this saves me having to keep editing my interfaces file each time. Is it possible for your program to detect and show the encryption used? 

:)

---

### Post by Alz on 2007-01-22
Does this work with other WMs? Im using Fluxbox, would it work?

---

### Post by Mike_Longbow on 2007-01-22
> **Alz said:**
> Does this work with other WMs? Im using Fluxbox, would it work?

It does (I use it in fluxbox, also). Tough I haven't tried the systray applet, since it's only designed for Edgy (I got Dapper)

---

### Post by Catsworth on 2007-01-23
I'm getting the following error message whenever I start Connection-Manager:

```

Mailcap file /etc/mailcap,line 42: incomplete entry ignored.

```

If I click 'Details' I get the following:

```

Mailcap file /etc/mailcap,line 41: incomplete entry ignored. 06:37:51 PM
Mailcap file /etc/mailcap,line 42: incomplete entry ignored. 06:37:51 PM

```

Anybody got any ideas what's up here?

Thanks.

---

### Post by compwiz18 on 2007-01-23
Open /etc/mailcap, and remove the offending lines (41 & 42) by putting a # in front of them.  It is a glitch with wxPython, and there isn't much I can do about it.  It won't be in the next version though :D

---

### Post by Catsworth on 2007-01-23
What does that file actually do?

I'm assuming that the lines in there must mean something, or is that the bug.....that the lines get included when they aren't needed and are completely meaningless?

Thanks for the help.

---

### Post by compwiz18 on 2007-01-24
To be honest, I'm not sure what the file does. I think it defines mimetypes for Python, but not sure.  Anyway, as I said, next version won't have that problem any more.

---

### Post by Peepsalot on 2007-01-24
Catsworth, do those lines say something about emerald?

There is a bug that is related to beryl/emerald that corrupts /etc/mailcap, so if you have that installed it could be your issue.

[http://bugs.beryl-project.org/ticket/546](http://bugs.beryl-project.org/ticket/546)

---

### Post by compwiz18 on 2007-01-25
Just thought I would tell you all that the wireless portion of the program is completely functional, with the ability to connect to any network (visible or hidden) with five different security options: eap, leap, peap, ttls, wep, and wpa.

If anyone else has wpa_supplicant configured with a type of encryption not mentioned there, please post it and I'll add it.  All encryption schemes are kept in text files, so it is very easy to add a new one.

TODO:
Finish the wired portion of the program.

I will be gone for a couple of days, so don't count on anything this weekend.

---

### Post by Catsworth on 2007-01-26
Just want to say thanks for this application.

I've deleted the two offending lines in mailcap and it seems to be working fine.  How can I tell if it is this application that is controlling my wireless connection, and not one of the others that I've been trying to use (or something built into Ubuntu)?

Does Connection Manager automatically override every other setting or will it defer to some other settings/application at all?

Thanks.

---

### Post by zymazyt on 2007-01-26
I'm afraid that I also have some problems with CM. I installed all required libraries and side apps (mostly python conected), but CM does not want to start.
I wanted to try it because of problems of disapearing wireless networks in kNetworkManager - there are some solutions, but CM looks better.
console output:
"Traceback (most recent call last):
  File "./manager", line 3, in <module>
    import networking, ConfigParser, wx, math, threading, time, sys, thread, os, tempfile, re
ImportError: No module named networking"

I've found that networking.py is missing from python-2.5 instalation. After copying that file from python-2.4 dir I got new errors:
"Traceback (most recent call last):
  File "./manager", line 724, in <module>
    app = wx.App()
  File "/usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7700, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7352, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
SystemError: wxEntryStart failed, unable to initialize wxWidgets!  (Is DISPLAY set properly?)
Segmentation fault"

Oh, I have almost forgot - I'm using Feisty Kubuntu.

---

### Post by Graham1 on 2007-01-26
> **compwiz18 said:**
> Just thought I would tell you all that the wireless portion of the program is completely functional, with the ability to connect to any network (visible or hidden) with five different security options: eap, leap, peap, ttls, wep, and wpa.

Thank you so much for this program :). CM makes it so easy to switch between different networks. Before, I had to keep editing "interfaces" and reboot :(. 

:)

---

### Post by m-kiler on 2007-01-26
i've got the same problem as **zymazyt**, and i'm also using feisty. has anyone found a solution yet?

---

### Post by lcohen999 on 2007-01-26
I am just wondering...as I am too lazy to search through the thread :)

I'm on my new laptop and connection manager is 100% perfect

except....how can I get connection-manager to connect to my network automatically on bootup.

I have connection-manager-systray in there, but have to manually hit connect on bootup,

thanks

---

### Post by compwiz18 on 2007-01-27
> **zymazyt said:**
> I'm afraid that I also have some problems with CM. I installed all required libraries and side apps (mostly python conected), but CM does not want to start.
I wanted to try it because of problems of disapearing wireless networks in kNetworkManager - there are some solutions, but CM looks better.
console output:
"Traceback (most recent call last):
  File "./manager", line 3, in <module>
    import networking, ConfigParser, wx, math, threading, time, sys, thread, os, tempfile, re
ImportError: No module named networking"

I've found that networking.py is missing from python-2.5 instalation. After copying that file from python-2.4 dir I got new errors:
"Traceback (most recent call last):
  File "./manager", line 724, in <module>
    app = wx.App()
  File "/usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7700, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7352, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
SystemError: wxEntryStart failed, unable to initialize wxWidgets!  (Is DISPLAY set properly?)
Segmentation fault"

Oh, I have almost forgot - I'm using Feisty Kubuntu.
Apparently not Feisty compatible...

Perhaps version 2 will be.  If not, I will certainly work on that.

---

### Post by compwiz18 on 2007-01-27
> **lcohen999 said:**
> I am just wondering...as I am too lazy to search through the thread :)

I'm on my new laptop and connection manager is 100% perfect

except....how can I get connection-manager to connect to my network automatically on bootup.

I have connection-manager-systray in there, but have to manually hit connect on bootup,

thanks
Should be doing that automatically, as long as you click Network Settings and check the Preferred Network box on the ones that it should automatically connect to.

---

### Post by zymazyt on 2007-01-28
> **compwiz18 said:**
> Apparently not Feisty compatible...

Perhaps version 2 will be.  If not, I will certainly work on that.

I was afraid, that this will be the issue. Only thing that is left is waiting for working ver...
Keep going, soft is worth it:)

---

### Post by lcohen999 on 2007-01-28
> **compwiz18 said:**
> Should be doing that automatically, as long as you click Network Settings and check the Preferred Network box on the ones that it should automatically connect to.

I think it may be my laptop m1210..

Doesn't always kick in the intel wireless nic at the right time....

---

### Post by .tommie on 2007-01-29
Iochen999: I've had a similar issue. Could you try [this]("http://www.ubuntuforums.org/showpost.php?p=1961340&postcount=422")? **Don't forget to change ath0 to the name of your NIC interface when adding a line in the etc/network/interfaces file.**

compwiz18: Any idea when the new version will be released?

---

### Post by songochain on 2007-01-29
Hello, knetwork-manager saves wep keys?? i've to enter always the wep key...

---

### Post by compwiz18 on 2007-01-29
> **.tommie said:**
> compwiz18: Any idea when the new version will be released?
In the next couple days, hopefully.  At least for beta testing.  I just have to add the wired connection stuff to the GUI, and I'm done :D

edit: that would be within the next hour, starting from the time of this edit.

---

### Post by compwiz18 on 2007-01-30
[SIZE="6"][COLOR="Orange"]VERSION 2![/COLOR][/SIZE]

get it here (new website :D): [http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)
and I setup a forum here, so all the bugs don't get jammed into this thread: [http://compwiz18.blackhole.cx/wicd/icebb](http://compwiz18.blackhole.cx/wicd/icebb)
and while I was at it, a wiki (I have no idea why this is even remotely useful, but I was having fun installing things :D): [http://compwiz18.blackhole.cx/wicd/wiki](http://compwiz18.blackhole.cx/wicd/wiki)

I will post it on the front thread as soon as I'm sure it isn't too buggy.

One other thing: if you are using the systray, keep using the systray from v1 with v2 - it should work, and I'll make a new fancy one sometime soon...

---

### Post by yopnono on 2007-01-30
Ok there is some stuff in the .DEB that should not be there. There is some old hidden backup files (file_name~) and also a .DEB in the .Deb file :)

Have not installed it yet. Also I'm unable to create a user in your forum > Word verification
What word do you see in the box? (+) there is no img. 
> - The word you entered does not match the one in the image, please try again

---

### Post by yopnono on 2007-01-30
Ok it don't work.
```
sudo /opt/wicd/daemon.py
Traceback (most recent call last):
  File "/opt/wicd/daemon.py", line 847, in ?
    bus_name = dbus.service.BusName('org.connectionmanager.daemon', bus=session_bus)
  File "/usr/lib/python2.4/site-packages/dbus/service.py", line 24, in __new__
    retval = dbus_bindings.bus_request_name(bus.get_connection(), name)
  File "dbus_bindings.pyx", line 1783, in dbus_bindings.bus_request_name
dbus_bindings.DBusException: Connection ":1.17" is not allowed to own the service "org.connectionmanager.daemon" due to security policies in the configuration file

```

Also all permissions are wrong, the files have user permission, it should be root.

---

### Post by liljoe76 on 2007-01-30
compwiz18, i wanted to join your forum. In creating an account there, the captcha image is 0px × 0px. thats just a weeeee bit to small for me to read.... :)

---

### Post by tvst on 2007-01-30
compwiz18, what's the changelog for 1.0.0? ([http://compwiz18.blackhole.cx/wicd/wb/pages/releases.php](http://compwiz18.blackhole.cx/wicd/wb/pages/releases.php))

does it support hidden essids yet?

also, as the people above have mentioned, your site's captcha is broken. maybe you don't have gd or imagemagick? (whichever it uses)

---

### Post by featherking on 2007-01-30
i get the same error as yopnono with the new version :/

---

### Post by compwiz18 on 2007-01-30
```

sudo /opt/wicd/daemon.py
Traceback (most recent call last):
  File "/opt/wicd/daemon.py", line 847, in ?
    bus_name = dbus.service.BusName('org.connectionmanager.daemon', bus=session_bus)
  File "/usr/lib/python2.4/site-packages/dbus/service.py", line 24, in __new__
    retval = dbus_bindings.bus_request_name(bus.get_connection(), name)
  File "dbus_bindings.pyx", line 1783, in dbus_bindings.bus_request_name
dbus_bindings.DBusException: Connection ":1.17" is not allowed to own the service "org.connectionmanager.daemon" due to security policies in the configuration file

```


Oops.  Totally forgot to package the dbus file.  My bad.

I'll get that fixed momentarily.
Same for the forum.

---

### Post by compwiz18 on 2007-01-31
> **compwiz18 said:**
> ```

sudo /opt/wicd/daemon.py
Traceback (most recent call last):
  File "/opt/wicd/daemon.py", line 847, in ?
    bus_name = dbus.service.BusName('org.connectionmanager.daemon', bus=session_bus)
  File "/usr/lib/python2.4/site-packages/dbus/service.py", line 24, in __new__
    retval = dbus_bindings.bus_request_name(bus.get_connection(), name)
  File "dbus_bindings.pyx", line 1783, in dbus_bindings.bus_request_name
dbus_bindings.DBusException: Connection ":1.17" is not allowed to own the service "org.connectionmanager.daemon" due to security policies in the configuration file

```


Oops.  Totally forgot to package the dbus file.  My bad.

I'll get that fixed momentarily.
Same for the forum.
Howdy, I'll have this fixed shortly

Also, new set of forums: [http://compwiz18.blackhole.cx/wicd/phpbb](http://compwiz18.blackhole.cx/wicd/phpbb)

---

### Post by tturrisi on 2007-01-31
hey hey
WICD
(do I get credit for the name?) :-)

---

### Post by compwiz18 on 2007-01-31
> hey hey
WICD
(do I get credit for the name?) 

You do - check the [about page]("http://adam.blackhole.cx/wicd/wb/pages/about.php")

For everyone else: get the new release that should work this time ;) [here]("http://adam.blackhole.cx/wicd/wb/")

and I'll say it again: [http://compwiz18.blackhole.cx/wicd/phpbb](http://compwiz18.blackhole.cx/wicd/phpbb) new forums :D

---

### Post by SVFUSiON on 2007-01-31
how do I remove this from my computer?

---

### Post by featherking on 2007-01-31
Using 'wicd_1.0.1-all.deb' I get this error when runnign /opt/wicd/gui.py

```
Introspect error: The name org.wicd.daemon was not provided by any .service files
Traceback (most recent call last):
  File "/opt/wicd/gui.py", line 837, in ?
    app = appGui()
  File "/opt/wicd/gui.py", line 78, in __init__
    self.refresh_networks(None,False)
  File "/opt/wicd/gui.py", line 258, in refresh_networks
    scan = self.wireless.StaleScan()
  File "/var/lib/python-support/python2.4/dbus/proxies.py", line 25, in __call__
    ret = self._proxy_method (*args, **keywords)
  File "/var/lib/python-support/python2.4/dbus/proxies.py", line 102, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)
  File "dbus_bindings.pyx", line 455, in dbus_bindings.Connection.send_with_reply_and_block
dbus_bindings.DBusException: The name org.wicd.daemon was not provided by any .service files
```

and this error when running 'sudo /opt/wicd/daemon.py'
```
found wireless interface in configuration... setting wireless interface... wlan0
found wired interface in configuration... setting wired interface... eth0
found wpa driver in configuration... setting wpa driver... wext
wireless configuration file found...
wired configuration file found...
chmoding configuration files 0600...
chowning configuration files root:root...
scanning...
wlan0: ERROR while getting interface flags: No such device
wlan0     Interface doesn't support scanning.

done scanning...found 0 networks
returning false...
Traceback (most recent call last):
  File "/opt/wicd/daemon.py", line 851, in ?
    log = open("/home/adam/Desktop/wicd.log","w")
IOError: [Errno 2] No such file or directory: '/home/adam/Desktop/wicd.log'
```

my wireless interface is not wlan0 in case that helps, it should be eth1...?

---

### Post by foxy123 on 2007-01-31
what version of python-dbus does wicd depends on? I've got 
```
python2.4-dbus - simple interprocess messaging system (Python interface)

``` but the dependency is still unsatisfied. Mind I am still on Dapper :)

---

### Post by tkjacobsen on 2007-01-31
Sounds really nice.. I would really much like to see the screenshots, but there are some permission errors on the server...

Will try it out asap

---

### Post by Mike_Longbow on 2007-01-31
I can't install it... I get this:

```
mike@longbow:~$ sudo dpkg -i wicd_1.0.1-all.deb
(Reading database ... 138531 files and directories currently installed.)
Preparing to replace wicd 1.0.1 (using wicd_1.0.1-all.deb) ...
Unpacking replacement wicd ...
dpkg: dependency problems prevent configuration of wicd:
 wicd depends on python-dbus; however:
  Package python-dbus is not installed.
dpkg: error processing wicd (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wicd

```
The same goes when I use Gdebi-gtk...
Seems that I need that python-dbus package... so... ????

(Oh, I use Dapper)

---

### Post by compwiz18 on 2007-01-31
New version, fixed the missing log file problems.

[http://adam.blackhole.cx/wicd/wb](http://adam.blackhole.cx/wicd/wb)

---

### Post by foxy123 on 2007-01-31
Gui fails:
```
~$ /opt/wicd/gui.py
requesting last scan...
Introspect error: The name org.wicd.daemon was not provided by any .service files
Traceback (most recent call last):
  File "/opt/wicd/gui.py", line 837, in ?
    app = appGui()
  File "/opt/wicd/gui.py", line 78, in __init__
    self.refresh_networks(None,False)
  File "/opt/wicd/gui.py", line 258, in refresh_networks
    scan = self.wireless.StaleScan()
  File "/usr/lib/python2.4/site-packages/dbus/proxies.py", line 79, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)  File "dbus_bindings.pyx", line 458, in dbus_bindings.Connection.send_with_reply_and_block
dbus_bindings.DBusException: The name org.wicd.daemon was not provided by any .service files

```

---

### Post by Mike_Longbow on 2007-01-31
:D It works on my WEP based network. I'll try it tomorrow at school's hidden network

---

### Post by tturrisi on 2007-01-31
> **compwiz18 said:**
> You do - check the [about page]("http://adam.blackhole.cx/wicd/wb/pages/about.php")

For everyone else: get the new release that should work this time ;) [here]("http://adam.blackhole.cx/wicd/wb/")

and I'll say it again: [http://compwiz18.blackhole.cx/wicd/phpbb](http://compwiz18.blackhole.cx/wicd/phpbb) new forums :D
Hey!
Thanks!
...onward to testing it.

---

### Post by qaball on 2007-02-01
I get this result as well on my brand new edgy install.  Any ideas to fix would be appreciated.  I REALLY need something that works.

> **foxy123 said:**
> Gui fails:
```
~$ /opt/wicd/gui.py
requesting last scan...
Introspect error: The name org.wicd.daemon was not provided by any .service files
Traceback (most recent call last):
  File "/opt/wicd/gui.py", line 837, in ?
    app = appGui()
  File "/opt/wicd/gui.py", line 78, in __init__
    self.refresh_networks(None,False)
  File "/opt/wicd/gui.py", line 258, in refresh_networks
    scan = self.wireless.StaleScan()
  File "/usr/lib/python2.4/site-packages/dbus/proxies.py", line 79, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)  File "dbus_bindings.pyx", line 458, in dbus_bindings.Connection.send_with_reply_and_block
dbus_bindings.DBusException: The name org.wicd.daemon was not provided by any .service files

```

---

### Post by compwiz18 on 2007-02-01
> **qaball said:**
> I get this result as well on my brand new edgy install.  Any ideas to fix would be appreciated.  I REALLY need something that works.
Try **sudo /etc/init.d/wicd start** and then run the GUI again.

---

### Post by compwiz18 on 2007-02-02
My server just died a terrible death (hopefully I'll have it fixed tomorrow - they had to turn the power off to install an aircon and now it doesn't turn on...)

anyways.

new version.

it now (I think) will connect to networks automatically on boot properly

give it a shot, tell me how it works. :D

---

### Post by yopnono on 2007-02-02
> **compwiz18 said:**
> My server just died a terrible death (hopefully I'll have it fixed tomorrow - they had to turn the power off to install an aircon and now it doesn't turn on...)

anyways.

new version.

it now (I think) will connect to networks automatically on boot properly

give it a shot, tell me how it works. :D

Are you use ubuntu as server?

And no it don't resume after suspend nor does it start after install, need to reboot or manually start the daemon. And it don't recognize the wifi interface in my case eth1 It set it to wlan0

---

### Post by Graham1 on 2007-02-02
> **yopnono said:**
> And it don't recognize the wifi interface in my case eth1 It set it to wlan0

Have you tried changing the Wireless Interface from wlan0 to eth1 (within preferences). That is what I did and now I'm connected.

:)

---

### Post by yopnono on 2007-02-02
> **Graham1 said:**
> Have you tried changing the Wireless Interface from wlan0 to eth1 (within preferences). That is what I did and now I'm connected.

:)

Yes I know. I just thought that this version was able to find the wifi interface.

---

### Post by Graham1 on 2007-02-02
I think I may have found a bug :(. 

Having updated to 1.0.3 and then restarted, Wicd is trying to connect to an AP that is no longer available (an AP that I connected to yesterday using a static IP). Wicd is showing two available AP's within the GUI (one of which is my own) but I am unable to select either as they are both greyed out. Wicd is trying to connect to yesterdays AP at 0%. If I select Cancel then all options are greyed out and I have to exit Wicd.

:)

---

### Post by Graham1 on 2007-02-02
.

---

### Post by Graham1 on 2007-02-02
please delete me

---

### Post by compwiz18 on 2007-02-02
> **yopnono said:**
> Are you use ubuntu as server?
Yep.  It didn't get powered down (it got a hard shutdown), the air conditioner install people just hit the power switch on the power coming into the house.  I wasn't here...

> And no it don't resume after suspend nor does it start after install, need to reboot or manually start the daemon. And it don't recognize the wifi interface in my case eth1 It set it to wlan0
OK - I'll work on suspend/resume, although I can't test it cause the ATI drivers hang up on resume.

Could you tell me where I need to put the script to have it reconnect on resume?

It doesn't autodetect the wireless interface, although I was planning to add that.

Does this mean you finally got it to run normally, just not with autostart after resume? :D

---

### Post by compwiz18 on 2007-02-02
> **Graham1 said:**
> I think I may have found a bug :(. 

Having updated to 1.0.3 and then restarted, Wicd is trying to connect to an AP that is no longer available (an AP that I connected to yesterday using a static IP). Wicd is showing two available AP's within the GUI (one of which is my own) but I am unable to select either as they are both greyed out. Wicd is trying to connect to yesterdays AP at 0%. If I select Cancel then all options are greyed out and I have to exit Wicd.

:)
I had the same problem - I checked it out and the computer was reporting that the network was still in range (**sudo iwlist scan** reported it) so I don't think it is wicd's fault.

---

### Post by Graham1 on 2007-02-02
> **compwiz18 said:**
> I had the same problem - I checked it out and the computer was reporting that the network was still in range (**sudo iwlist scan** reported it) so I don't think it is wicd's fault.

Ok, fair enough :). Actually, when I took my laptop upstairs, Wicd detected some extra AP's and I was able to select my AP again and connect.

On a different subject, I managed to get Wicd working in Kbuntu my adding python-glade2 (as mention on Wicd forum) yet in Ubuntu, I had the same package already installed plus python and python-dbus and I couldn't start Wicd :(. Once you've got the Wicd forum up and running again, I'll post the outpost.

:)

---

### Post by compwiz18 on 2007-02-02
It lives :D fixed the webserver.  Somehow I managed to remove upstart, which is responsible for turning the computer on...hence it wouldn't boot.  So logical once you have it figured out. (I had to chroot in from the livecd and apt-get install ubuntu-minimal to get it to work)

Anyway it is alive now.

---

### Post by compwiz18 on 2007-02-02
> **yopnono said:**
> Are you use ubuntu as server?

And no it don't resume after suspend nor does it start after install, need to reboot or manually start the daemon. And it don't recognize the wifi interface in my case eth1 It set it to wlan0
OK, fixed the autodetecting of the wireless interface.  I think it would probably be safe to default the wired interface to eth0?  Do you think that is safe?

also, ignore my question about the resume from suspend path, I found it.

---

### Post by bodhi.zazen on 2007-02-03
Nice How-to

This thread has been added to the UDSF wiki.

[Connection Manager](http://doc.gwos.org/index.php/Connection_Manager)

---

### Post by yopnono on 2007-02-03
> **compwiz18 said:**
> OK, fixed the autodetecting of the wireless interface.  I think it would probably be safe to default the wired interface to eth0?  Do you think that is safe?

also, ignore my question about the resume from suspend path, I found it.

I can't say for all machines, but eth0 sound safe for the wire :)
To the resume. It don't connect on *boot* or *resume* automatically. Need to connect manually using the gui script from shell or the gui from menu, which does the same so to speak ;) 

Except that it works like it should. Also the daemon don't take so much resources, well, less is better, but it not much.

Question:
Was it not possible to show if the encrypted network is using WEP/WPA/WPA2?
Also is it possible to have the connect button for each network on the same line as the name, or maybe have the first step expanded by default so you can connect to the network without expand the first step. Mind it's nothing major just questions.

---

### Post by compwiz18 on 2007-02-03
Yeah - I can have it tell you if it is wep/wpa/wpa2/not secured, but I need someone to post an **sudo iwlist scan** of a WEP network and a WPA1 network, then I can do that.

Also, I can probably do something about that connect button...

and a systray applet that actually works in dapper :D

---

### Post by yopnono on 2007-02-03
> **compwiz18 said:**
> Yeah - I can have it tell you if it is wep/wpa/wpa2/not secured, but I need someone to post an **sudo iwlist scan** of a WEP network and a WPA1 network, then I can do that.

Also, I can probably do something about that connect button...

and a systray applet that actually works in dapper :D

WPA (1)
```
eth1      Scan completed :
          Cell 01 - Address: 00:11:50:21:E8:49
                    ESSID:"505"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=100/100  Signal level=-25 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 212ms ago
```


Open
```
          Cell 02 - Address: 00:14:6C:9A:43:90
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=27/100  Signal level=-83 dBm
                    Extra: Last beacon: 2676ms ago
```


WEP
```
          Cell 03 - Address: 00:80:C8:AF:D5:42
                    ESSID:"default"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:22 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 22
                    Quality=25/100  Signal level=-84 dBm
                    Extra: Last beacon: 2940ms ago
```


WPA (2)
```
          Cell 01 - Address: 00:11:50:21:E8:49
                    ESSID:"505"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=98/100  Signal level=-24 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 52ms ago
```

EDIT:

WPA and WPA2
```
eth1      Scan completed :
          Cell 01 - Address: 00:11:50:21:E8:49
                    ESSID:"505"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=98/100  Signal level=-24 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 16ms ago
```

---

### Post by Graham1 on 2007-02-03
> **Graham1 said:**
> On a different subject, I managed to get Wicd working in Kbuntu my adding python-glade2 (as mention on Wicd forum) yet in Ubuntu, I had the same package already installed plus python and python-dbus and I couldn't start Wicd :(. Once you've got the Wicd forum up and running again, I'll post the outpost.

Seems to be working now, didn't change a thing :confused:.

:)

---

### Post by foxy123 on 2007-02-03
GUI still does not work for me:
```
/opt/wicd/gui.py
requesting last scan...
done getting scan...
plugged in... eth0
Traceback (most recent call last):
  File "/opt/wicd/gui.py", line 837, in ?
    app = appGui()
  File "/opt/wicd/gui.py", line 78, in __init__
    self.refresh_networks(None,False)
  File "/opt/wicd/gui.py", line 276, in refresh_networks
    profiles = self.config.GetWiredProfileList()
  File "/usr/lib/python2.4/site-packages/dbus/proxies.py", line 79, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)  File "dbus_bindings.pyx", line 458, in dbus_bindings.Connection.send_with_reply_and_block
dbus_bindings.DBusException: Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/dbus/service.py", line 341, in _message_cb
    _method_reply_return(connection, message, method_name, signature, *retval)
  File "/usr/lib/python2.4/site-packages/dbus/service.py", line 162, in _method_reply_return
    iter.append(value)
  File "dbus_bindings.pyx", line 1084, in dbus_bindings.MessageIter.append
  File "dbus_bindings.pyx", line 1308, in dbus_bindings.MessageIter.append_arrayIndexError: list index out of range


```

---

### Post by compwiz18 on 2007-02-03
Ok.  Try unplugging the computer and loading the GUI - I think that may fix it.  And I'll get on fixing it so you don't have to do that.

---

### Post by foxy123 on 2007-02-03
> **compwiz18 said:**
> Ok.  Try unplugging the computer and loading the GUI - I think that may fix it.  And I'll get on fixing it so you don't have to do that.

yes it works without wired connection. Though it butchered my firefox profile for some reason (it froze the laptop so I have to do hard reboot).

---

### Post by compwiz18 on 2007-02-03
> **foxy123 said:**
> yes it works without wired connection. Though it butchered my firefox profile for some reason (it froze the laptop so I have to do hard reboot).
Weird.  I'll get a fix out for that.

---

### Post by foxy123 on 2007-02-03
> **compwiz18 said:**
> Weird.  I'll get a fix out for that.
Thanks a lot! You are a star!

---

### Post by lcohen999 on 2007-02-03
I have a suggestion for an addition to connection manager v2.

pptp connections.  The gui pptp client, as we know doesn't work with edgy eft.  Gnome NetworkConnection (pptp) does work, but obviously we cannot use that.

What are the odds you add that?

Thanks!

---

### Post by featherking on 2007-02-03
wicd_1.0.3-all.deb doesnt connect automatically at boot for me, i posted more in your forum...?
But using the gui works fine..?

---

### Post by darrenm on 2007-02-07
Thank you, this works great for me and solved all my issues on my Lenovo 3000 C100 w/ bcm4319 (listed as dell 1470) using fwcutter and bcm43xx.

:D

---

### Post by handaxe on 2007-02-09
Hi,

Just made the switch from CM to wicd 1.0.5-all.deb. No joy in auto starting at boot.

"sudo /etc/init.d/wicd start" does the trick.

Edgy.

HA

> **featherking said:**
> wicd_1.0.3-all.deb doesnt connect automatically at boot for me, i posted more in your forum...?
But using the gui works fine..?

---

### Post by jernomer on 2007-02-09
Hi,

I have recently switched from Connection Manager to Wicd (1.0.5). I cannot get the system tray to load or Wicd to automatically connect to the last network at startup, which all worked under Connection Manager. I have added "wicd" and "wicd-systray" to Startup Programs.

I am using Edgy.

Any ideas? Thanks.

---

### Post by yopnono on 2007-02-09
> **jernomer said:**
> Hi,

I have recently switched from Connection Manager to Wicd (1.0.5). I cannot get the system tray to load or Wicd to automatically connect to the last network at startup, which all worked under Connection Manager. I have added "wicd" and "wicd-systray" to Startup Programs.

I am using Edgy.

Any ideas? Thanks.

You don't need to add them to the startup, is should start and connect automatic.
Anyhow post the problems in  [http://adam.blackhole.cx/wicd/phpbb/index.php](http://adam.blackhole.cx/wicd/phpbb/index.php)

---

### Post by jernomer on 2007-02-09
Thanks for the advice, I will cross-post this issue.

---

### Post by handaxe on 2007-02-09
Jernomer,

First off, as I am having problems my advice prolly sucks:)

Secondly, there may be a problem with wicd - documenting it will help.

wicd-systray is not the name of the python script - it is ```
/opt/wicd/tray.py
``` to give the full path.

wicd is a script in the /etc/init.d/ directory. It should get invoked automatically and that seems to be where my issue lies. I doubt it should be put in startup.

Try this, after bootup go the command prompt and 

```
sudo /etc/init.d.wicd start
```

Then run the wicd icon under Internet (this runs /opt/wicd/gui.py).

If this works, then you too have the problem I encountered on Edgy.

HA

---

### Post by compwiz18 on 2007-02-09
> **handaxe said:**
> Jernomer,

First off, as I am having problems my advice prolly sucks:)

Secondly, there may be a problem with wicd - documenting it will help.

wicd-systray is not the name of the python script - it is ```
/opt/wicd/tray.py
``` to give the full path.

wicd is a script in the /etc/init.d/ directory. It should get invoked automatically and that seems to be where my issue lies. I doubt it should be put in startup.

Try this, after bootup go the command prompt and 

```
sudo /etc/init.d.wicd start
```

Then run the wicd icon under Internet (this runs /opt/wicd/gui.py).

If this works, then you too have the problem I encountered on Edgy.

HA
And the weird thing is, it works fine on my computer (Edgy also)...if we can get this figured out, I think that would be helpful.

---

### Post by serlex on 2007-02-10
Compwiz, some how wicd saves your last connection and still shows up on GUI even when i turn off my wireless and click fresh. And it always says connected at the bottom. Was wondering if it would be good idea to have 'disconnect' or something

---

### Post by Catsworth on 2007-02-11
Ok, now here's interesting.

Connection Manager has been working fine on my laptop for a couple of weeks, not one glitch and everything doing what it should.

I've just got my own Broadband at home (no longer reliant on in-laws for Internet access) and have set up my wireless router.  Everything works ok, apart from the fact that the connection doesn't start when I boot the laptop up.  

The Connection Manager icon appears ok in the system tray, but to connect to the network I have to click the icon, type in my admin password, select the network, and then click connect.

Is there any way to automate/fix this behaviour.  I want to give my GF an account on this machine but it's going to be no good to her (or me) if she can only get access to the Internet if she's got the admin password.

Thanks guys.

---

### Post by lcohen999 on 2007-02-11
> **Catsworth said:**
> Ok, now here's interesting.

Connection Manager has been working fine on my laptop for a couple of weeks, not one glitch and everything doing what it should.

I've just got my own Broadband at home (no longer reliant on in-laws for Internet access) and have set up my wireless router.  Everything works ok, apart from the fact that the connection doesn't start when I boot the laptop up.  

The Connection Manager icon appears ok in the system tray, but to connect to the network I have to click the icon, type in my admin password, select the network, and then click connect.

Is there any way to automate/fix this behaviour.  I want to give my GF an account on this machine but it's going to be no good to her (or me) if she can only get access to the Internet if she's got the admin password.

Thanks guys.

I have the exact same problem.  And my main network is set as my preferred networked

---

### Post by kaede on 2007-02-13
hello are this program support for SMC2835W pcmcia card? i seems can't configure it too works :(

---

### Post by Catsworth on 2007-02-16
> **Catsworth said:**
> Ok, now here's interesting.

Connection Manager has been working fine on my laptop for a couple of weeks, not one glitch and everything doing what it should.

I've just got my own Broadband at home (no longer reliant on in-laws for Internet access) and have set up my wireless router.  Everything works ok, apart from the fact that the connection doesn't start when I boot the laptop up.  

The Connection Manager icon appears ok in the system tray, but to connect to the network I have to click the icon, type in my admin password, select the network, and then click connect.

Is there any way to automate/fix this behaviour.  I want to give my GF an account on this machine but it's going to be no good to her (or me) if she can only get access to the Internet if she's got the admin password.

Thanks guys.


Anybody?

---

### Post by handaxe on 2007-02-16
Hi,

Attention now is on the new re-written version of Connection Manager known now as WICD.

I am sure the developer wants to squash WICD bugs, so give it a spin and see if it replicates your problem with CM.

[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

There are bull. boards for Wicd too:

[http://adam.blackhole.cx/wicd/phpbb/index.php](http://adam.blackhole.cx/wicd/phpbb/index.php)

Post there methinks.

Compwiz18: if the Wicd board is where you want stuff, maybe announce so on this Ubuntu forum thread.

Cheers,

HA

---

### Post by foxy123 on 2007-02-18
I still have serious issues with wicd 1.05. It started to freeze my laptop so I decided to remove it a couple of weeks ago. Connection Manager works fine for me but it does not do auto connect with wireless for some reason. Yesterday I decided to reinstall wicd, but when I first launched it it hang the laptop. I had to do hot reboot and after that I wanted to remove it again. It turned out to be very difficult. It was some error in dpkg and I could neither install any package nor remove any. After prolonged googlng I found a solution (to delete some wicd related stuff manually). 

Then I decided to remove wicd from /opt and reinstall it again. After that wicd caused a corruption of my xfce4 config. I have to configure all my xfce4 panels, plugins and launchers manually. So I removed wicd for the last time.

I can imagine the issues could be Dapper related and maybe it works fine on Edgy and Feisty. I will switch on Feisty anyway in next few weeks and try wicd again then. Meanwhile I will use the Connection Manager.

---

### Post by compwiz18 on 2007-02-18
The freezing problem is related (I think) to wpa_supplicant and the tray icon.  I find that on an unsecured network, it never freezes, but on my home (wpa2) network it freezes randomly.

As for corrupting your xfce config...I can't help you there, but it shouldn't have touched that.

---

### Post by foxy123 on 2007-02-18
> **compwiz18 said:**
> As for corrupting your xfce config...I can't help you there, but it shouldn't have touched that.

No I do not think it corrupted it directly. It is something to do with the reboot after it.

---

### Post by compwiz18 on 2007-02-22
OK, wicd 1.0.6 is available, as is a new tray icon (which is now included with the main distribution)

get it at [http://compwiz18.blackhole.cx/wicd/wb](http://compwiz18.blackhole.cx/wicd/wb)

I (hopefully fixed the startup problems some people have been having, it now does **update-rc.d wicd start 99 2 3 4 5 . stop 20 0 1 6 .** so hopefully it will start after dbus which I think is some of the problem.  and I fixed the wired network problems, so now wired networks work too.  Complete with profiles!

yopnono, if this doesn't fix your problem, I will include the modifications you made to the /etc/init.d/wicd script on the other forum in the next release.

---

### Post by H.E. Pennypacker on 2007-02-23
Can we close this thread or something so that we can move over to Wicd's website?  It also should remove confusion over Wicd's name, because some people are still calling it Connection Manager.  The thread title here is not helping either.

Seriously, moving over to an indepedent messageboard sounds like a good idea, instead of a single thread for all possible problems.  Besides, moving could help in increasing Wicd's popularity, which is not doing too well in Google search listing.

---

### Post by compwiz18 on 2007-02-23
OK

*****MODS******
could we get a name change on this thread to **Wicd: a new (wireless) network manager** please? tyvm in advance

---

### Post by foxy123 on 2007-02-24
1.06 does not work for me at all.

```
$ /opt/wicd/gui.py
requesting last scan...
Introspect error: The name org.wicd.daemon was not provided by any .service files
Traceback (most recent call last):
  File "/opt/wicd/gui.py", line 873, in ?
    app = appGui()
  File "/opt/wicd/gui.py", line 78, in __init__
    self.refresh_networks(None,False)
  File "/opt/wicd/gui.py", line 258, in refresh_networks
    scan = self.wireless.StaleScan()
  File "/usr/lib/python2.4/site-packages/dbus/proxies.py", line 79, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)  File "dbus_bindings.pyx", line 458, in dbus_bindings.Connection.send_with_reply_and_block
dbus_bindings.DBusException: The name org.wicd.daemon was not provided by any .service files

```

---

### Post by compwiz18 on 2007-02-24
> **foxy123 said:**
> 1.06 does not work for me at all.

```
$ /opt/wicd/gui.py
requesting last scan...
Introspect error: The name org.wicd.daemon was not provided by any .service files
Traceback (most recent call last):
  File "/opt/wicd/gui.py", line 873, in ?
    app = appGui()
  File "/opt/wicd/gui.py", line 78, in __init__
    self.refresh_networks(None,False)
  File "/opt/wicd/gui.py", line 258, in refresh_networks
    scan = self.wireless.StaleScan()
  File "/usr/lib/python2.4/site-packages/dbus/proxies.py", line 79, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)  File "dbus_bindings.pyx", line 458, in dbus_bindings.Connection.send_with_reply_and_block
dbus_bindings.DBusException: The name org.wicd.daemon was not provided by any .service files

```
Try **sudo /etc/init.d/wicd start** then try it again.

---

### Post by foxy123 on 2007-02-26
> **compwiz18 said:**
> Try **sudo /etc/init.d/wicd start** then try it again.

```
 sudo /etc/init.d/wicd start
Password:
Starting wicd daemon...
wicd daemon: pid 8673
Introspect error: The name org.wicd.daemon was not provided by any .service files
Traceback (most recent call last):
  File "/opt/wicd/autoconnect.py", line 22, in ?
    print daemon.Hello()
  File "/usr/lib/python2.4/site-packages/dbus/proxies.py", line 79, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)  File "dbus_bindings.pyx", line 458, in dbus_bindings.Connection.send_with_reply_and_block
dbus_bindings.DBusException: The name org.wicd.daemon was not provided by any .service files

```

I tried to install 1.08 and got the following error:
```
Starting wicd daemon...
wicd daemon: pid 8721
Introspect error: The name org.wicd.daemon was not provided by any .service files
Traceback (most recent call last):
  File "/opt/wicd/autoconnect.py", line 22, in ?
    print daemon.Hello()
  File "/usr/lib/python2.4/site-packages/dbus/proxies.py", line 79, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)  File "dbus_bindings.pyx", line 458, in dbus_bindings.Connection.send_with_reply_and_block
dbus_bindings.DBusException: The name org.wicd.daemon was not provided by any .service files
```

---

### Post by compwiz18 on 2007-02-27
> **foxy123 said:**
> ```
 sudo /etc/init.d/wicd start
Password:
Starting wicd daemon...
wicd daemon: pid 8673
Introspect error: The name org.wicd.daemon was not provided by any .service files
Traceback (most recent call last):
  File "/opt/wicd/autoconnect.py", line 22, in ?
    print daemon.Hello()
  File "/usr/lib/python2.4/site-packages/dbus/proxies.py", line 79, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)  File "dbus_bindings.pyx", line 458, in dbus_bindings.Connection.send_with_reply_and_block
dbus_bindings.DBusException: The name org.wicd.daemon was not provided by any .service files

```

I tried to install 1.08 and got the following error:
```
Starting wicd daemon...
wicd daemon: pid 8721
Introspect error: The name org.wicd.daemon was not provided by any .service files
Traceback (most recent call last):
  File "/opt/wicd/autoconnect.py", line 22, in ?
    print daemon.Hello()
  File "/usr/lib/python2.4/site-packages/dbus/proxies.py", line 79, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)  File "dbus_bindings.pyx", line 458, in dbus_bindings.Connection.send_with_reply_and_block
dbus_bindings.DBusException: The name org.wicd.daemon was not provided by any .service files
```
Yep, appears to be a problem (it happened to me the other day too), although I don't know how it is/was caused.  If you could post /opt/wicd/data/wicd.log, that would be helpful in solving this problem.

---

### Post by pearlie on 2007-02-27
After thrashing around for uncounted hours trying to get my (expletive deleted) Broadcom 4318 card working, I finally got something to happen - light to come on[ using this method]("https://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=5") -  but was unable to connect using Network Manager or WiFi Radar.  

It came up first try with Wicd, as soon as I put in my key.

There is no systray icon but I don't effing care, because now I'm wireless and unbound.

Compwiz, I want to have your children.  :biggrin:

---

### Post by handaxe on 2007-02-28
The wicd deb installs a tray icon BUT does not put an entry is startup.

Do that by going to "System" "Preferences" "Sessions" "Startup Programs" and enter /opt/wicd/tray-edgy (if using Edgy) or /opt/wicd/tray-dapper (Dapper (Doh!)).

 Spread the word about wicd - some problems remain but it is a "wicd" litle application.

HA

---

### Post by foxy123 on 2007-02-28
> **compwiz18 said:**
> Yep, appears to be a problem (it happened to me the other day too), although I don't know how it is/was caused.  If you could post /opt/wicd/data/wicd.log, that would be helpful in solving this problem.
```
---------------------------
---------------------------
---------------------------
wicd initalizing...
---------------------------
---------------------------
---------------------------

```

---

### Post by compwiz18 on 2007-02-28
> **foxy123 said:**
> ```
---------------------------
---------------------------
---------------------------
wicd initalizing...
---------------------------
---------------------------
---------------------------

```
That's it?  It must be crashing then... don't know why, but I'll see if I can figure it out.

---

### Post by foxy123 on 2007-03-01
> **compwiz18 said:**
> That's it?  It must be crashing then... don't know why, but I'll see if I can figure it out.

if you need any other logs please let me know. Also I have 1.08 installed, so I can try a previous release to check it.

---

### Post by compwiz18 on 2007-03-01
If you have time, you might want to try 1.0.7, it seems to work better (at least for me) then 1.0.8 does, with the exception of not having a logging feature.  I think that 1.0.9 will be based on 1.0.7, as 108 was a regression.

---

### Post by foxy123 on 2007-03-01
> **compwiz18 said:**
> If you have time, you might want to try 1.0.7, it seems to work better (at least for me) then 1.0.8 does, with the exception of not having a logging feature.  I think that 1.0.9 will be based on 1.0.7, as 108 was a regression.

I tried 1.07 before without any luck. If it does not have a logging feature than there is no point to try it again. I will wait for 1.09 and will post the log file output then.

---

### Post by Ripfox on 2007-03-13
Is there a systray download for wicd? It says I can't use the old one with it.

AWESOME APP BTW.

Yea...rookie mistake, thats showin' my noobness....(note to self: read the posts first before asking dumb questions)

---

### Post by handaxe on 2007-03-14
Hi,  I can't fiugure out whether you solved this or not.

So, the tray icon is installed but not "activated". You do that by going to the top menu "system" then "preferences" "sessions" and entering /opt/wicd/tray-edgy.py (if on edgy) or /opt/wicd/tray-dapper.py in "Startup Programs" tab.

HA

---

### Post by Ripfox on 2007-03-17
Yes...solved, I was leaving off the "py" due to an earlier post in this thread. Wicd is the BEST tool I have used, and I want to thank the people who are working on it. Wireless is a cinch now. :guitar:

---

### Post by legzelda on 2007-03-19
After setting up my wireless card through ndiswrapper and using iwconfig to configure it, I got a bit tired of all the typing required in order to connect to each network.  I made a simple script to automatically connect to my home's network when my computer booted, but I needed something a bit easier to connect to wireless networks at school and my girlfriend's house.  This application did the trick!  It works amazingly well, and I extend my thanks to the developers.  Nicely done!

Just for verification, this works on my Dell Inspiron E1505 with built-in wireless.  If anyone wants help setting up wireless on this laptop model, I have the steps completely mastered using ndiswrapper and iwconfig; feel free to contact me.  I will possibly post a how-to, unless someone already beat me to it, if I get the chance.  This program makes wireless a cinch!

---

### Post by handaxe on 2007-03-19
To all,

if you use Wicd (the successor to CM) please could you take the time to fill out:

[http://adam.blackhole.cx/wicd/wiki/doku.php?id=testing](http://adam.blackhole.cx/wicd/wiki/doku.php?id=testing)

As the dev notes, this will aid development. Particularly interested in what does not work.

Thanks

HA

---

### Post by ppan76 on 2007-03-30
Connection Manager used to work fine (with WEP and WAP)

I tried the last 3 versions of WICD (Including Beta) and none of them worked.  The window will open and close immediately. ANybody figure out that problem??

Thanks

---

### Post by handaxe on 2007-03-30
[http://adam.blackhole.cx/wicd/phpbb/viewforum.php?f=4](http://adam.blackhole.cx/wicd/phpbb/viewforum.php?f=4)

Rather post in Wicd's own forum, or as well  - the dev is active there and others. Maybe you did?

The reason to do this is that the dev can ask you for certain outputs to troubleshoot the problem. The fact is, Wicd works on most setups just fine but hiccups on others (I know, mine was one of the troublesome ones for a while).

When you post, tar the log file found in /opt/wicd/data/wicd.log and attach it to the message.

Also, after a failed load of wicd from the menu or the tray_icon, type /opt/wicd/gui.py in a terminal and paste the resulting output in the message as well.  That will provide the dev with clues as to why the gui (SETTINGS/CONNECT INTERFACE) does not load.

HA

---

### Post by davegod75 on 2007-04-21
I cannot get to:

[http://compwiz18.blackhole.cx/wicd/wb](http://compwiz18.blackhole.cx/wicd/wb)

firefox just goes to about:blank.


Is the site down?

---

### Post by compwiz18 on 2007-04-21
I have a feeling it is an IP problem - try [http://218.46.125.189/wicd/wb](http://218.46.125.189/wicd/wb) to get there.

---

### Post by keith11 on 2007-04-21
Hi Compwiz:

I tried using wicd and it worked fine for wireless connections without encryptions but I am facing the following problem when I try to connect to a connection with 64-bit WEP encryption: [http://ubuntuforums.org/showthread.php?t=417736](http://ubuntuforums.org/showthread.php?t=417736) 

I will eagerly wait for your response as I have given up on knetworkmanager and liked wicd, at least with connections without encryption. Thanks.

Keith.

---

### Post by nightofnih on 2007-04-23
OK - this is so frustrating. The site [http://compwiz18.blackhole.cx/wicd/wb](http://compwiz18.blackhole.cx/wicd/wb) is down - maybe thats not the correct DNS name anyways. Cannot connect to [http://218.46.125.189/wicd/wb](http://218.46.125.189/wicd/wb) or [http://compwiz18.ig3.net/wicd/wb](http://compwiz18.ig3.net/wicd/wb) either - I don't know which one it is anymore. Anybody has a mirror to this site or the forums that are supposed to be on that site. Any help would be appreciated - I have been trying to figure out how to connect to my WPA secured router using my build in bcm4306 ever since I upgraded to feisty and I need to get the package from there and specially see the discussions on how to go about installing this on feisty.

---

### Post by Ripfox on 2007-04-23
Where has wicd gone!! Please fix the site folks...I'm jonesin!! :)

---

### Post by webdr on 2007-04-23
Check out this thread:
[http://ubuntuforums.org/showthread.php?t=420627&highlight=wireless](http://ubuntuforums.org/showthread.php?t=420627&highlight=wireless)

---

### Post by compwiz18 on 2007-04-24
ahh... the recent switch in DNS and I forgot to update the server...

Doing that now.


edit : fixed.

---

### Post by keith11 on 2007-04-24
> **compwiz18 said:**
> ahh... the recent switch in DNS and I forgot to update the server...

Doing that now.


edit : fixed.

[http://218.46.125.189/wicd/wb](http://218.46.125.189/wicd/wb)  is still down, so I couldn't check the forums. So I am posting my problem here.

Before I begin typing about the problem I am facing let me mention that I have tried too much to make Knetworkmanager work but it just doesn't work after coming alive from suspend mode on my laptop. Other problem I face with Knetworkmanager is that after coming back from suspend mode, if I try to choose the "go offline" option of Knetwokrmanage by right clicking on the taskbar icon, it just doesn't allow me to make that change. As a mater of fact, it seems stuck because it doesn't allow me to make any changes. If I quit it, and then restart it, it will not detect my wireless card. I have been having similar problems with networkmanager in Ubuntu too and I have filed a bug report on launchpad which is yet to be taken care of.

In order to get rid of the problem I tried wicd on my Kubuntu Fesity installtion. I can connect fine through wicd at my work place where there is no encryption. At my home though, where I have awireless connection with 64-bit WEP encryption, wicd gets stuck at "Generating PSK..." message as soon as I click on "connect" after providing the encyption key for my wireless connection. Wicd remains stuck and never connects. I am using Intel Pro 2200 wireless card so I am assuming I have to use "ipw" in my preferences of wpa_supplicant driver, which is what I did. I have tried choosing another driver, the one which is selected by default and it work too when there is no encryption, but with encryption, it just doesn't connect. Has anyone used wicd on Kubuntu/Ubuntu Feisty and actually got it to work without problems? Could someone tell me why wicd gets stuck with that "Generating PSK..." message and never connects and what's the work around for that? Any help/comments will be greatly sought after and appreciated. Thanks.

Keith.


I just found the following as a comment by someone on my other thread:

> **jtelling said:**
> I looked at the code, and it seems that whomever made WICD has WEP and WPA going through the same path for encryption -- meaning -- it tries to use the WEP key to generate a PSK, and then fails.

I think WICD needs to TLC in the encryption department.

Honestly, in my very uneducated opinion, I don't think WICD will work with a WEP network until it's fixed.

---

### Post by groggyboy on 2007-04-24
keith11 (and whoever else can't get to the website):

[http://compwiz18.ig3.net/wicd/wb/]("http://compwiz18.ig3.net/wicd/wb/") worked for me.

---

### Post by jiminycricket on 2007-04-28
> **nightofnih said:**
>  [http://compwiz18.ig3.net/wicd/wb](http://compwiz18.ig3.net/wicd/wb) either - I don't know which one it is anymore. Anybody has a mirror to this site or the forums that are supposed to be on that site. Any help would be appreciated - I have been trying to figure out how to connect to my WPA secured router using my build in bcm4306 ever since I upgraded to feisty and I need to get the package from there and specially see the discussions on how to go about installing this on feisty.

This site works for me, too

Unfortunately the google pagerank is low so you can't find it easily by search, "wicd", so hopefully more people discover his site by finding this thread..

---

### Post by skywarp04 on 2007-05-03
I have wicd installed and it works great, but what I need to know is how to get it set up so that it automatically connects to my network on start up.

---

### Post by handaxe on 2007-05-04
It should do that - you have "ticked" the automatically connect box, right?

For problems go to [http://wicd.sourceforge.net/phpbb/](http://wicd.sourceforge.net/phpbb/)

and post.

HA

---

### Post by skywarp04 on 2007-05-04
That was what I thought, but it doesn't connect until I load the program and click connect.  It might help if I mention that I'm using Feisty.  Any ideas?

---

### Post by handaxe on 2007-05-04
I am due to install Feisty this weekend so I reserve comment.  Try the forum - the author of Wicd uses Feisty so he might help.

I assume that N-M is un-installed... (apt should have seen to that...)

The other thing is to examine what the log in /opt/wicd/data might show right after you have booted up.

HA

---

### Post by skywarp04 on 2007-05-04
Good idea, checked the log after boot up and it does reveal some information.  It is trying to autoconnect, but it doesn't see my network on boot up.  Wicd doesn't see it either when I first start it until I hit the refresh button.  After that I click connect on my network and it works.  Any ideas why it wouldn't be seeing my network on boot up.  My ESSID is not hidden or anything.  I haven't to wicd's forums because as of the other day the website has been moved to Source Forge and the forums were empty.

---

### Post by handaxe on 2007-05-05
The forums are populated now.

You can only try there - at least one similar issue was posted and went unanswered but see..

Wicd uses other programmes to do its connecting, AP scanning, viz: wpa_supplicant, iwlist etc. If one of these does not work with your wireless card at wicd startup time for whatever reason, then the problem will be there still when the wicd gui loads to display "current state" info. Refresh then re-invokes the external programme (probably "iwlist [interface] scan") and in your case, it then plays nicely with your card.

What this means is that the wicd author can fiddle with things like run-levels to try and persuade matters to work, but any fundamental problem between an external programme and wireless card is beyond his control.

lets see wots wot,

HA

---

### Post by dtruesdale on 2007-05-10
Compwiz18, I am using this on 2 different laptops. One is a Dell E1705 Core 2 Duo. So it's 64 bit Kubuntu. Also running on a Toshiba Satellite Dual Core. The 32bit setup gives me the systray icon for Wicd, the 64 bit version runs but no systray icon no matter what I do. Is this a known issue? or have I done something wrong?

---

### Post by Fylk on 2007-05-10
This is working on Fawn, yes?

---

### Post by compwiz18 on 2007-05-11
> **Fylk said:**
> This is working on Fawn, yes?

Yes.

> **dtruesdale said:**
> Compwiz18, I am using this on 2 different laptops. One is a Dell E1705 Core 2 Duo. So it's 64 bit Kubuntu. Also running on a Toshiba Satellite Dual Core. The 32bit setup gives me the systray icon for Wicd, the 64 bit version runs but no systray icon no matter what I do. Is this a known issue? or have I done something wrong?

Works fine on my 64bit laptop.  What version(s) of Ubuntu do you have?

---

### Post by Fylk on 2007-05-11
Ok, then all I have to ask is if this is any better than the wireless manager that comes with gnome. i would really like to know before I go removing wireless manager just to install 

Also, it has a tray app, yes?

---

### Post by yopnono on 2007-05-11
> **Fylk said:**
> Ok, then all I have to ask is if this is any better than the wireless manager that comes with gnome. i would really like to know before I go removing wireless manager just to install 

Also, it has a tray app, yes?

Yes I think it's better but... it's up to you if you like it, and you can always remove it and reinstall the gnome network manager, yes it has a tray icon.

---

### Post by Fylk on 2007-05-11
Then I guess I will have to give it a try. Cause I'll be honest, this build in gnome one kinda...well, sucks.

---

### Post by compwiz18 on 2007-05-11
> **Fylk said:**
> Then I guess I will have to give it a try. Cause I'll be honest, this build in gnome one kinda...well, sucks.

Tell us how it goes :)

---

### Post by dtruesdale on 2007-05-11
Feisty Fawn 7.04 64bit and 32bit, 32bit works fine and has the systray icon. The 64bit version doesn't. I followed the install instructions of what I could remeber of removing networkmanager and then doing the install. I couldn't remember if I had to run anything from the wicd folder.

---

### Post by Fylk on 2007-05-12
Yeah, that didn't work very well....

---

### Post by thelost on 2007-06-01
hah, I gotta agree on that.... having problems since I installed wicd too.

---

### Post by thunkt on 2007-06-17
Arg,

I'm so close. Wicd finds the network, tries to connect says "obtaining ip address" then breaks.
Is there a log file I can look at to see what is happening?

Cheers

---

### Post by compwiz18 on 2007-06-17
Look in ```
/opt/wicd/data/wicd.log
``` If you need help, you can post it :D

---

### Post by imdano on 2007-06-23
Hi compwiz,

On initial install of version 1.2.9 I ran into a bug that prevented me from running gui.py.  It seemed that the ConnectionWizard.always_show_wired_interface variable in daemon.py wasn't getting initialized, causing it to return null in a call to GetAlwaysShowWiredInterface() in an if statement in gui.py.

It think that the problem is due to the wired-settings.conf file being empty, and with the way you parse config files right now, always_show_wired_interface never gets initialized. Here is the section of code I think is relevant:
```
			if config.has_section("Settings"):
				if config.has_option("Settings","wireless_interface"):
					print "found wireless interface in configuration...",
					self.SetWirelessInterface(config.get("Settings","wireless_interface"))
				if config.has_option("Settings","wired_interface"):
					print "found wired interface in configuration...",
					self.SetWiredInterface(config.get("Settings","wired_interface"))
				if config.has_option("Settings","wpa_driver"):
					print "found wpa driver in configuration...",
					self.SetWPADriver(config.get("Settings","wpa_driver"))
				if config.has_option("Settings","always_show_wired_interface"):
					self.always_show_wired_interface = config.get("Settings","always_show_wired_interface")
				else:
					config.set("Settings","always_show_wired_interface","False")
					self.always_show_wired_interface = False
			else:
				print "configuration file exists, no settings found, adding defaults..."
				configfile = open(self.app_conf,"w")
				config.add_section("Settings")
				config.set("Settings","wireless_interface","wlan0")
				config.set("Settings","wired_interface","eth0")
				config.set("Settings","wpa_driver","wext")
				config.set("Settings","always_show_wired_interface","False")
				self.SetWirelessInterface(config.get("Settings","wireless_interface"))
				self.SetWiredInterface(config.get("Settings","wired_interface"))
				self.SetWPADriver(config.get("Settings","wpa_driver"))
				config.write(configfile)

		else:
			#write some defaults maybe?
			print "configuration file not found, creating, adding defaults..."
			config = ConfigParser.ConfigParser()
			config.read(self.app_conf)
			config.add_section("Settings")
			config.set("Settings","wireless_interface","wlan0")
			config.set("Settings","wired_interface","eth0")
			iface = self.DetectWirelessInterface()
			if iface:
				config.set("Settings","wireless_interface",iface)
			else:
				print "couldn't detect a wireless interface..."
				config.set("Settings","wireless_interface","wlan0")
			config.set("Settings","wpa_driver","wext")
			config.write(open(self.app_conf,"w"))
			self.SetWirelessInterface(config.get("Settings","wireless_interface"))
			self.SetWiredInterface(config.get("Settings","wired_interface"))
			self.SetWPADriver(config.get("Settings","wpa_driver"))
```
It looks like always_show_wired_interface only gets initialized if a config file is found.  I didn't want to mess with the code in there (at your suggestion), and instead added the line
```
self.always_show_wired_interface = False
``` around line 77 in the daemon.py, which seems to have fixed the bug.  Although it might make more sense to add it as a default in the ReadConfig function.

I'm sorry I couldn't be a bit more specific with error messages and line numbers, but I can't seem to recreate it after a couple of uninstall/reinstalls, which is odd.  I 'm pretty sure that the trace pointed to line 351 of daemon.py which was being called by line 805 of gui.py (GetAlwaysShowWiredInterface in particular), but I can't give you much more than that.  Let me know if you think my logic here makes sense or if something else must have been causing the problem.

---

### Post by compwiz18 on 2007-06-23
> **imdano said:**
> Hi compwiz,

On initial install of version 1.2.9 I ran into a bug that prevented me from running gui.py.  It seemed that the ConnectionWizard.always_show_wired_interface variable in daemon.py wasn't getting initialized, causing it to return null in a call to GetAlwaysShowWiredInterface() in an if statement in gui.py.

It think that the problem is due to the wired-settings.conf file being empty, and with the way you parse config files right now, always_show_wired_interface never gets initialized. Here is the section of code I think is relevant:
```
			if config.has_section("Settings"):
				if config.has_option("Settings","wireless_interface"):
					print "found wireless interface in configuration...",
					self.SetWirelessInterface(config.get("Settings","wireless_interface"))
				if config.has_option("Settings","wired_interface"):
					print "found wired interface in configuration...",
					self.SetWiredInterface(config.get("Settings","wired_interface"))
				if config.has_option("Settings","wpa_driver"):
					print "found wpa driver in configuration...",
					self.SetWPADriver(config.get("Settings","wpa_driver"))
				if config.has_option("Settings","always_show_wired_interface"):
					self.always_show_wired_interface = config.get("Settings","always_show_wired_interface")
				else:
					config.set("Settings","always_show_wired_interface","False")
					self.always_show_wired_interface = False
			else:
				print "configuration file exists, no settings found, adding defaults..."
				configfile = open(self.app_conf,"w")
				config.add_section("Settings")
				config.set("Settings","wireless_interface","wlan0")
				config.set("Settings","wired_interface","eth0")
				config.set("Settings","wpa_driver","wext")
				config.set("Settings","always_show_wired_interface","False")
				self.SetWirelessInterface(config.get("Settings","wireless_interface"))
				self.SetWiredInterface(config.get("Settings","wired_interface"))
				self.SetWPADriver(config.get("Settings","wpa_driver"))
				config.write(configfile)

		else:
			#write some defaults maybe?
			print "configuration file not found, creating, adding defaults..."
			config = ConfigParser.ConfigParser()
			config.read(self.app_conf)
			config.add_section("Settings")
			config.set("Settings","wireless_interface","wlan0")
			config.set("Settings","wired_interface","eth0")
			iface = self.DetectWirelessInterface()
			if iface:
				config.set("Settings","wireless_interface",iface)
			else:
				print "couldn't detect a wireless interface..."
				config.set("Settings","wireless_interface","wlan0")
			config.set("Settings","wpa_driver","wext")
			config.write(open(self.app_conf,"w"))
			self.SetWirelessInterface(config.get("Settings","wireless_interface"))
			self.SetWiredInterface(config.get("Settings","wired_interface"))
			self.SetWPADriver(config.get("Settings","wpa_driver"))
```
It looks like always_show_wired_interface only gets initialized if a config file is found.  I didn't want to mess with the code in there (at your suggestion), and instead added the line
```
self.always_show_wired_interface = False
``` around line 77 in the daemon.py, which seems to have fixed the bug.  Although it might make more sense to add it as a default in the ReadConfig function.

I'm sorry I couldn't be a bit more specific with error messages and line numbers, but I can't seem to recreate it after a couple of uninstall/reinstalls, which is odd.  I 'm pretty sure that the trace pointed to line 351 of daemon.py which was being called by line 805 of gui.py (GetAlwaysShowWiredInterface in particular), but I can't give you much more than that.  Let me know if you think my logic here makes sense or if something else must have been causing the problem.
OK, I'll add that :D

---

### Post by lostthetrail on 2007-06-23
Hi all,

I am running a BCM4318 and I was hoping this will solve some of my issues.

When I attempt to connect to a wireless network I get to "Obtaining IP Address", sits there for a minutes, then goes to "Not Connected".

I watched the wicd.log and I see the following output in repeat over and over:

```
status... running_dhcp
status request
acqlock True
   ...lock acquired
   ...lock released
```

I can see my wireless network (which is running WPA-PSK).

A side note: I can connect to my wired network without any issues.

Any ideas? Am I not giving you enough of the picture to know whats up?

Thanks!
Lostthetrail

---

### Post by compwiz18 on 2007-06-23
> **lostthetrail said:**
> Hi all,

I am running a BCM4318 and I was hoping this will solve some of my issues.

When I attempt to connect to a wireless network I get to "Obtaining IP Address", sits there for a minutes, then goes to "Not Connected".

I watched the wicd.log and I see the following output in repeat over and over:

```
status... running_dhcp
status request
acqlock True
   ...lock acquired
   ...lock released
```

I can see my wireless network (which is running WPA-PSK).

A side note: I can connect to my wired network without any issues.

Any ideas? Am I not giving you enough of the picture to know whats up?

Thanks!
Lostthetrail
Make sure the key is typed correctly, and if it is, try putting quotes around it. (sometimes this fixes the problem)

---

### Post by lostthetrail on 2007-06-23
No such luck. I verified the key (it was correct) and put quotes around it.

Any other ways to diagnose what is going on?

-UPDATE-

My problems were solved by getting rid of the native drivers and running ndiswrapper. I am using Network Manager. Thanks for the help!
(Compaq V2000 BCM4318)

---

### Post by foxy123 on 2007-06-24
> **lostthetrail said:**
> No such luck. I verified the key (it was correct) and put quotes around it.

Any other ways to diagnose what is going on?

I've got BCM4306 and I also have a problem with connecting. I have to click on connect in wicd several times until it works.

---

### Post by Royle on 2007-06-27
I am having issues using this program and an acx 111 chipset with ndiswrapper.  I had this working with WPA a few months ago when Wicd was named Connection Manager and I think it was on Edgy.  I recently installed ubuntu Fiesty Fawn, atempted to install ndiswrapper to replace the built in driver as it does not support wpa.  The problem is I can use Wicd to connect to an unprotected network, but it can't connect to a wpa protected network.  I changed the preferences to the ndiswrapper wpa driver and that didn't change anything.

This could either be one of two problems, either there's something wrong with the ndiswrapper instal, or something wrong with my use of the program.

ndisrwapper -l lists the driver as installed but also shows something for an alternate driver which is acx (which doesn't support wpa)

Can someone help me with this problem? Any help is greatly appreciated.

---

### Post by compwiz18 on 2007-06-27
> **Royle said:**
> I am having issues using this program and an acx 111 chipset with ndiswrapper.  I had this working with WPA a few months ago when Wicd was named Connection Manager and I think it was on Edgy.  I recently installed ubuntu Fiesty Fawn, atempted to install ndiswrapper to replace the built in driver as it does not support wpa.  The problem is I can use Wicd to connect to an unprotected network, but it can't connect to a wpa protected network.  I changed the preferences to the ndiswrapper wpa driver and that didn't change anything.

This could either be one of two problems, either there's something wrong with the ndiswrapper instal, or something wrong with my use of the program.

ndisrwapper -l lists the driver as installed but also shows something for an alternate driver which is acx (which doesn't support wpa)

Can someone help me with this problem? Any help is greatly appreciated.
Try something like **sudo rmmod acx** and then **sudo modprobe ndiswrapper, then try Wicd.**

---

### Post by Royle on 2007-06-27
> **compwiz18 said:**
> Try something like **sudo rmmod acx** and then **sudo modprobe ndiswrapper, then try Wicd.**

I just tried that and sudo rmmod acx says that there is no module acx (probably becuase I have it black listed), and sudo modprobe ndiswrapper returns nothing.  Either way I still have the same problem of no wpa support.  Any other suggestions?

---

### Post by compwiz18 on 2007-06-27
> **Royle said:**
> I just tried that at sudo rmmod acx says that there is no module acx (probably becuase I have it black listed), and sudo modprobe ndiswrapper returns nothing.  Either way I still have the same problem of no wpa support.  Any other suggestions?
Oh yeah - the ndiswrapper that comes with Feisty doesn't work with WPA, so you have to compile your own.  Follow step 4 ONLY of this website: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) and then try wicd again.

---

### Post by Royle on 2007-06-28
> **compwiz18 said:**
> Oh yeah - the ndiswrapper that comes with Feisty doesn't work with WPA, so you have to compile your own.  Follow step 4 ONLY of this website: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) and then try wicd again.

I just installed ndiswrapper according to the link you posted, version 1.47.  It installed fine, and at some point along the way one of the outputs said the card supported wpa security.  It connected fine to my network unsecured, but as soon as I enabled wpa it couldn't connect.  It gets stuck at Obtaining IP if that makes any difference.  Thanks for your continued support.

---

### Post by WiseGuy1020 on 2009-06-15
I know this is an old thread but I was wondering when 1.6.0, now that it is stable, will into the repos. The official ubuntu repo would be nice but I would understand that might not happen, especially if it is slated to be included in 9.10 release.

However I have added the wicd repo to my sources.list and 1.60 is not included there. I was wondering why not, especially since it is wicd's own repository.

Anybody know why?

---

### Post by imdano on 2009-06-15
I think it's because our debian packager wanted us to wait until he built a package for us to use, and it's not ready yet.  I'm not 100% sure on that though, Adam (compwiz18) could say for sure.

---

### Post by slumbergod on 2009-06-15
The impression I got was that the Debian distro maintainer was blocking it, which had the spin-off effect of preventing ubuntu users from getting it also. As for it making it into the official ubuntu jaunty repos I doubt that will happen.

I was looking at just using the python installer to do it but there are just too many unknowns to risk it. That means relying on the wicd devs to give us a deb or trying it ourselves with their installer.

---

### Post by compwiz18 on 2009-06-15
He's not blocking it, by any means, but we are trying to use only the official packages. Unfortunately, this means that anyone not using Karmic or Debian experimental is cut off. We've built some packages for everyone else: get them at [http://downloads.wicd.net/pkgs](http://downloads.wicd.net/pkgs)

---

