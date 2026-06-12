---
title: "In to deep, So many questions! 8.10"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Alexpants on 2008-11-02
I just switched from windows vista to Ubuntu 8.10 and I've got to be honest I have NO IDEA what on earth is going on. 
I have a bunch of questions, I hope someone can help me!
First question is;
1. I transferred a bunch of files onto another computer before I wiped the laptop I have installed Ubuntu on. The computer uses Windows XP and I transferred via my wireless router (both machines plugged into the router via ethernet cable then run -> \\ipofotherpc ) How can I transfer the files back using the same method? 
2. How in the name of blue hell do I connect to my Wireless? All I've got is this VPN wierdness and seriously now I have NO IDEA what I'm doing. I've looked in the documentation but that's all geared towards 8.04 LTS so it hasn't been any help yet. 

Help!! I'm so completely useless at this, but hey, at least my laptop loads a bit faster eh?
Any help is very much appreciated.

---

### Post by melojo on 2008-11-02
in order to transfer files between window pc's and linux use samba
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

As far as your wireless does ubuntu recognize it?

open a terminal
Applications>Accessories>Terminal
type this below

```
sudo lshw -C network 
```

post the output

---

### Post by ad_267 on 2008-11-02
For accessing your files, you can install smbfs and smbclient from System - Administration - Synaptic Package Manager (you need an internet connection) then you should be able to browse to the network share from the file browser. If it is password protected you can go to File - Connect to server to connect.

---

### Post by Alexpants on 2008-11-02
It prompts me to enter a password, but then will not allow me to type in the terminal :\
Is there any way I can downgrade to 8.04? I downloaded it and burnt it to a disk but it kept saying there was an error and it'd reboot...

---

### Post by coolkid5 on 2008-11-02
When it prompts you for a password in the terminal, just type your password and hit enter.  No characters are supposed to appear as you are typing.

---

### Post by melojo on 2008-11-02
> **Alexpants said:**
> It prompts me to enter a password, but then will not allow me to type in the terminal :\
Is there any way I can downgrade to 8.04? I downloaded it and burnt it to a disk but it kept saying there was an error and it'd reboot...

Go ahead and type your password.
You just can't see what you type for the password!

The only way to install 8.04 is to do a fresh install.  
Are you booting from the live cd?

You should just be able to follow the same procedure to install 8.04.  If you are getting an error something must be wrong with the disk.

---

### Post by Alexpants on 2008-11-02
I get this... 
[I]SCSI                      
  *-network        
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:38:4d:4e:fa
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.2.2 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c2:02:3a:97:d2:75
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes[/I]

---

### Post by Alexpants on 2008-11-02
> **melojo said:**
> Go ahead and type your password.
You just can't see what you type for the password!

The only way to install 8.04 is to do a fresh install.  
Are you booting from the live cd?

You should just be able to follow the same procedure to install 8.04.  If you are getting an error something must be wrong with the disk.

Is a live CD one you've made from a download? If so, yes! (sorry I'm such a newbie) 
I'm now re-writing another disk at the slowest speed, so hopefully that'll make it work! Is the install the same as 8.10?
I can't help but feel maybe I needed a bit more technical knowledge before I did this :lol:

---

### Post by lisati on 2008-11-02
> **melojo said:**
> in order to transfer files between window pc's and linux use samba
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

As far as your wireless does ubuntu recognize it?

open a terminal
Applications>Accessories>Terminal
type this below

```
sudo lshw -C network 
```

post the output
There's also a tutorial at [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

> **Alexpants said:**
> It prompts me to enter a password, but then will not allow me to type in the terminal :\

This is normal when entering your password using the terminal, it's part of Ubuntu's security precautions. Just type in your password and press "Enter"


Good luck, and don't be afraid to ask questions.

---

### Post by ad_267 on 2008-11-02
Looks like there's been a few issues with your wireless adapter. Linux support for wireless isn't that great from some vendors.

This thread might help: [http://ph.ubuntuforums.com/showthread.php?t=940048](http://ph.ubuntuforums.com/showthread.php?t=940048)

There's also a bug here: [https://bugs.launchpad.net/ubuntu/+bug/228548](https://bugs.launchpad.net/ubuntu/+bug/228548)

---

### Post by Alexpants on 2008-11-02
Oh my, it's all a bit greek to me! I've just downgraded to 8.04 so at least there will be more documentation but still having problems with my wireless :( It's just not in the Network menu at all!

---

### Post by sudo_chop on 2008-11-02
> **Alexpants said:**
> Oh my, it's all a bit greek to me! I've just downgraded to 8.04 so at least there will be more documentation but still having problems with my wireless :( It's just not in the Network menu at all!
 
Downgrading is a little counter-productive if you are trying to get your hardware working. There is a better chance of it being supported in the newer kernel.
 
*Most* support info you find related to 8.04 should still be applicable to 8.10.

---

