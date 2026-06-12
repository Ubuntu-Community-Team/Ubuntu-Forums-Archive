---
title: "Firestarter Guide v1.0 for Ubuntu Breezy Badger 5.10 using Add Applicatons"
date: 2005-12-30
forum: Outdated Tutorials &amp; Tips
---

### Post by KrazyPenguin on 2005-12-30
Firestarter Guide v1.0 for Ubuntu Breezy Badger 5.10 using Add Applicatons
By KrazyPenguin
Created On: 12.30.05
This guide shows how to easily install Firestarter, and have your system start without the root password prompt with 		Firestarter minimized to the system tray.  
1) Install Firestarter using Add Applications
Open Applications (top left of screen) --> Click on “Add Applications” (bottom of menu)
After the password prompt the “Add Applications” GUI will open, then type in the search box “firestarter” and enter. 
After a few seconds the search brings up “Firestarter”, check the little box to the left of it, and then click “Apply” on the 		bottom right.  A “Changes Pending” box will appear saying that Firestarter is to be Added.  Click apply to install.
Note: Firestarter will be automatically added to Applications --> System Tools --> Firestarter
2) Giving the user permission to launch Firestarter without the root password.
Open a terminal and type: sudo gedit /etc/sudoers
Add this line to the bottom: username ALL=NOPASSWD:/usr/sbin/firestarter
Save the file and close the terminal.
Note: Make sure “username” is your actual username ;-)
3) Start Firestarter
Alt – F2 (to Run Application) or open a terminal and type:
sudo firestarter
The Wizard should open and will ask for some information.  Go here for more help:
 [http://www.fs-security.com/docs/wizard.php](http://www.fs-security.com/docs/wizard.php)
4) Minimize Firestarter to tray on window close.
With Firestarter already open click --> Preferences --> check “Minimize to tray on window close”
5) Launching Firestarter minimized to the tray on login.
System --> Preferences --> Sessions --> Startup Programs --> Add 
Enter this line:
sudo firestarter –start-hidden
.....and click Ok and you're done.
6) Stop Firestarter from loading on login.
System --> Preferences --> Sessions --> Startup Programs
Click on “sudo firestarter –start-hidden” and then choose “Delete”.
7) Remove Firestarter using Add Applications.
Open Applications --> Click on “Add Applications”
After the password prompt the “Add Applications” GUI will open, then type in the search box “firestarter” and enter.
After a few seconds the search brings up “Firestarter”, UNcheck the little box to the left of it, and then click “Apply” on the 	bottom right.  A “Changes Pending” box will appear saying that Firestarter is to be removed.  Click apply to remove.
8) Test the Firewall
[http://www.hackerwatch.org/probe/](http://www.hackerwatch.org/probe/) 
[http://www.pcflank.com](http://www.pcflank.com)
 Shields Up! >> [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by PsTJsT on 2006-02-22
Okay, I'm thoroughly frustrated now:  I've followed each and every step (and gone back and confirmed I did everything correctly more than once) but I get an "Insufficient Privileges" message every time I restart/reboot.  Firestarter starts fine, and minimizes itself to the task bar, but I'd really like to get rid of the error message.  Any ideas?

Thanks.

---

### Post by kaamos on 2006-02-22
Are you aware that you can make firestarter start at boot just by checking that option in firestarter preferences? The gui is only for changing settings and looking at logs, and the firewall daemon itself is running without it. If you are feeling insecure, just type 
```
sudo /etc/init.d/firestarter status
```
in a terminal to check if the firewall is running. It should return "Firestarter is running..."

---

### Post by PsTJsT on 2006-02-22
[QUOTE=kaamos]Are you aware that you can make firestarter start at boot just by checking that option in firestarter preferences? The gui is only for changing settings and looking at logs, and the firewall daemon itself is running without it.[/QUOTE]

Thanks for the quick response...

Unfortunately (?), I'm aware that firestarter can start/run without the GUI, but I like the GUI running for various reasons (e.g., I like being notified when a potential intrusion is detected).  And, for whatever its worth, the firewall daemon starts/runs fine (as does the GUI) on my system, I'm just annoyed that I have to click on the acknowledgment button in the "Insufficient Privileges" window every time I restart/reboot.

Also, although I can't say that I care too much, I'm confused as to why I receive the error message even though everything runs fine.  Based on the nature of the error message, I would think that it (the error message) is trying to tell me that the firewall daemon and/or the GUI can't start (which isn't the case).

---

### Post by LordMerlin on 2006-03-22
Ok, so I'm new to Ubuntu, and this helped me quite a bit. Only problem is, I keep on getting an error in Firestarter: 

Failed to start the firewall

An unknown error occured. 

Please check your network deviced settings and make sure your internet connection is active.

I have two network cards, one connection to a Netgear DG834GT ADSL router, and the other into my network hub. I can use the internet if I don't run the firewall, so my PC is communicating to the ADSL, and the to net. 

```

admin@linux-server:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:BF:B7:B4:E4
          inet addr:192.168.10.1  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::250:bfff:feb7:b4e4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18289 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:7 dropped:0 overruns:0 carrier:14
          collisions:0 txqueuelen:1000
          RX bytes:1184319 (1.1 MiB)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xa000

eth1      Link encap:Ethernet  HWaddr 00:0D:61:64:21:F9
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:61ff:fe64:21f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:192576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:148782 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:124820923 (119.0 MiB)  TX bytes:24961093 (23.8 MiB)
          Interrupt:20

admin@linux-server:~$ route -nv
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1


``` 
Can someone please assist me with this?

[EDIT]

I noticed that when I disable the internet connection sharing, that the firewall works, and I don't get an error. But the moment I enable it, I get the error message again.

---

