---
title: "Missing Important System Tools"
date: 2015-07-18
forum: New to Ubuntu
---

### Post by zander2 on 2015-07-18
Hello, all!

I am finding that my install of Ubuntu is missing some tools referenced in various tutorials I am trying to follow. For instance, nm-tool isn't available, and modprobe is missing the ndiswrapper module. Rather than go through and install each package that pops up on my radar incrementally, is there any way to grab all the system tools I need in one go? 

I just ran

```
sudo apt-get update
```

Will that cover me, or is there another package or list of packages I need to get to make my install fully functional?

---

### Post by sudodus on 2015-07-18
I think it is hard to make a tool that will grab all the system tools you need in one go. I think you have to go the incremental way, finding out by yourself, or asking here to get tips about good tools. Specific questions will often get better answers than general questions.

```
sudo apt-get update
```

'only' updates the lists and makes it possible for the following command to upgrade the program packages, that need upgrading:

```
sudo apt-get upgrade
``` or
```
sudo apt-get dist-upgrade
```

See ```
man apt-get
``` for more details.

---

### Post by v3.xx on 2015-07-18
A dist-upgrade will also upgrade the kernel.

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by Geoffrey_Arndt on 2015-07-18
Basically, what are your "Use Cases" . . ?   Are you trying your hand at development (web, client, snappy, etc.), building packages and modules (drivers), website development, etc. etc??

For basic development, did you install build-essentials?

---

### Post by grahammechanical on 2015-07-18
There is always progress in Linux and it seems that in the latest versions of Ubuntu nm-tool is no longer installed and it is not even in the repositories, as far as I can tell. It does not show up in Synaptic Package Manager, any way.

What we now have is nmcli. In a terminal type

```
nm,cli help
```

Or go to this web site

[http://linux.de.net/man/1/nmcli](http://linux.de.net/man/1/nmcli)

nmcli has a new set of commands for us to learn

```
nmcli dev wifi list
```

Gives this response
> 
*  SSID                 MODE   CHAN  RATE       SIGNAL  BARS  SECURITY         
   BTHub3-5QXS          Infra  1     54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA1 WPA2        
   BTWifi-X             Infra  1     54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA1 WPA2 802.1X 
   BTHub3-63R9          Infra  11    54 Mbit/s  52      &#9602;&#9604;__  WPA1 WPA2        
   EE-BrightBox-t3bndf  Infra  1     54 Mbit/s  45      &#9602;&#9604;__  WPA1 WPA2        
   BTHub5-TQT5          Infra  1     54 Mbit/s  44      &#9602;&#9604;__  WPA2             
   VM343388-2G          Infra  6     54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2        
   BTWifi-X             Infra  1     54 Mbit/s  42      &#9602;&#9604;__  WPA1 WPA2 802.1X 
   BTWifi-with-FON      Infra  1     54 Mbit/s  74      &#9602;&#9604;&#9606;_  --               
   BTOpenzone-B         Infra  11    54 Mbit/s  54      &#9602;&#9604;__  --               
   BTWiFi               Infra  11    54 Mbit/s  52      &#9602;&#9604;__  --               
   BTWifi-with-FON      Infra  1     54 Mbit/s  37      &#9602;&#9604;__  --               
*  PlusnetWireless      Infra  6     54 Mbit/s  73      &#9602;&#9604;&#9606;_  WPA1 WPA2   

```
nmcli dev
```

> DEVICE  TYPE      STATE        CONNECTION         
eth0    ethernet  connected    Wired connection 1 
wlan0   wifi      connected    PlusnetWireless    
eth1    ethernet  unavailable  --                 
lo      loopback  unmanaged    --                 

And so on. Which all goes to confirm, in my opinion, the importance of giving the Ubuntu version number when asking for help on this forum because what may work in 14.04 may not necessarily work in 15.04 and onwards.

It is back to school in the Networking and Wireless section of the forum. :)

Regards.

---

### Post by zander2 on 2015-07-18
I do Java and C/C++ development, as well as some AVR microcontroller stuff. No, I have not gotten build-essentials. I'll look that up. 


Thanks for the tips, I'll be sure to include a version number in future posts(I have Ubuntu 15.04 Desktop)! I'll mark this as solved. I guess I'll just install whatever packages I need as I go. That should actually help keep things lean. :D

---

