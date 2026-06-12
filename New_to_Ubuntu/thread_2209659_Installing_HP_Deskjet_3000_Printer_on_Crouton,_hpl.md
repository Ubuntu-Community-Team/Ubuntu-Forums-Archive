---
title: "Installing HP Deskjet 3000 Printer on Crouton, hplip says CUPS is missing"
date: 2014-03-06
forum: New to Ubuntu
---

### Post by alan20 on 2014-03-06
I'm trying to get my HP Deskjet 3000 hooked up through crouton on my Toshiba Chromebook. I followed the instructions for installation from [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html) and I eventually ran into this:
```
DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --assume-yes libcups2'
Please wait, this may take several minutes...
error: A required dependency 'cups (CUPS - Common Unix Printing System)' is still missing.


RUNNING POST-PACKAGE COMMANDS
-----------------------------
OK


RE-CHECKING DEPENDENCIES
------------------------
error: A required dependency 'cups (CUPS - Common Unix Printing System)' is still missing.
error: Installation cannot continue without this dependency.
error: Please manually install this dependency and re-run this installer.
```

But then when I run
```
sudo apt-get install cups
```

I get
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cups is already the newest version.
The following package was automatically installed and is no longer required:
  libglade2-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
(precise)alan@localhost:~$ 
```

I'm kind of lost at this point. How do I get CUPS installed to where hplip recognizes it, and completes the installation?

---

### Post by r.stiltskin on 2014-03-06
I'm not familiar with Chromebook, but is there a reason why you can't install hplip from the Ubuntu repository?

e.g.
sudo apt-get install hplip

---

### Post by alan20 on 2014-03-07
> **r.stiltskin said:**
> I'm not familiar with Chromebook, but is there a reason why you can't install hplip from the Ubuntu repository?

e.g.
sudo apt-get install hplip

Thanks for the response. I was referred to the official website, where HP has their own installation instructions. I'm not sure why nobody suggested the repository, it seems much easier.

Trying that, I get
```
(precise)alan@localhost:~$ sudo apt-get install hplip
[sudo] password for alan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
hplip is already the newest version.
The following package was automatically installed and is no longer required:
  libglade2-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
(precise)alan@localhost:~$ 
```

I'm out of town right now. Tomorrow I'll try simply connecting it to the printer and seeing if it's worked and post here again.

---

### Post by r.stiltskin on 2014-03-08
I can't be certain from the info you posted, but it sounds like the HP installer script never got to the "Build and Install" stage (see the last 2 Konsole screens shown on HP's [Installer Walkthrough]("http://hplipopensource.com/hplip-web/install/install/index.html").

It also looks as if you already had installed HPLIP from Ubuntu's repo.  And if that's the case you can delete the file hplip-3.14.3.run you downloaded from HP as well as the folder (probably called "3.14.3") that was extracted from it.

But merely installing HPLIP isn't enough.  You have to _run it_ to set up your printer.  Open a terminal and run the command **hp-setup** and see what you get.

---

### Post by alan20 on 2014-03-09
> **r.stiltskin said:**
> I can't be certain from the info you posted, but it sounds like the HP installer script never got to the "Build and Install" stage (see the last 2 Konsole screens shown on HP's [Installer Walkthrough]("http://hplipopensource.com/hplip-web/install/install/index.html").

It also looks as if you already had installed HPLIP from Ubuntu's repo.  And if that's the case you can delete the file hplip-3.14.3.run you downloaded from HP as well as the folder (probably called "3.14.3") that was extracted from it.

But merely installing HPLIP isn't enough.  You have to _run it_ to set up your printer.  Open a terminal and run the command **hp-setup** and see what you get.

Well, that did get "HP Device Manager - Setup" to run, but the program always says that there are no devices found, regardless of what Connection Type I select on the "Device Discovery" page.

---

### Post by r.stiltskin on 2014-03-09
OK, but that's a completely different issue.  Now you know that hplip is installed and working.  Now you have to get the printer installed.

So, your printer is wifi-capable, so I assume that you want to connect via wifi.  Correct?  If so, the first thing you have to do is make sure that the printer is turned on and has logged into your wifi network.  Have you done that?

---

### Post by alan20 on 2014-03-10
> **r.stiltskin said:**
> OK, but that's a completely different issue.  Now you know that hplip is installed and working.  Now you have to get the printer installed.

So, your printer is wifi-capable, so I assume that you want to connect via wifi.  Correct?  If so, the first thing you have to do is make sure that the printer is turned on and has logged into your wifi network.  Have you done that?

Yes, thank you for the help. Should I create a new thread, then, since I'm dealing with a different issue now?

The printer has been set up for a while now, and works just fine with my old laptop. The Toshiba Chromebook is new.

---

### Post by r.stiltskin on 2014-03-10
Can you ping the printer from the Chromebook?

```
ping [ipaddress of the printer]
```

You should get output that looks like:
```

PING 192.168.[something].[something] (192.168.[something].[something]) 56(84) bytes of data.
64 bytes from 192.168.[something].[something]: icmp_seq=1 ttl=64 time=0.420 ms
64 bytes from 192.168.[something].[something]: icmp_seq=1 ttl=64 time=0.377 ms
64 bytes from 192.168.[something].[something]: icmp_seq=1 ttl=64 time=0.408 ms
and so on ...

```

Press Ctrl-c to stop it.
Then you should see output like:
--- [ipaddress] ping statistics ---
[number of pings] packets transmitted, [same number] received, 0% packet loss ...

---

### Post by alan20 on 2014-03-10
The ping worked

> 8 packets transmitted, 8 received, 0% packet loss, time 7011ms
rtt min/avg/max/mdev = 3.458/6.331/18.981/5.102 ms

I  tried running HPSetup again as sudo, and the printer did come up. Now,  though, when I try to set it up through "Wireless" with the printer connected using the USB cord, I get this:

> **An I/O error occurred.**
Please check the USB connection to your printer and try again.
(Device I/O Error)

When I try to set up the printer through "USB" or through "Network/Ethernet/Wireless network" using "Manual Discovery", I get a different error.

> PPD file: (Not found. Click browse button to select a PPD file.)

---

### Post by r.stiltskin on 2014-03-11
Disconnect the usb cable and, on the hp-setup "device discovery" screen select "Network/Ethernet/Wireless network" and click next and it should find your printer. (At least that's what works for me.)

---

