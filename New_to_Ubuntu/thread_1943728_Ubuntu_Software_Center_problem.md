---
title: "Ubuntu Software Center problem"
date: 2012-03-20
forum: New to Ubuntu
---

### Post by guber90 on 2012-03-20
[B][COLOR="Red"]EDIT: This is not only USC problem, I can't install with terminal, so help if u can :D, don't want to lose time on ubuntu reinstall and saving data if it is posible anyway :)
[/COLOR][/B]
Hello guys, I'm new user of Ubuntu 11.10 (using it for about one month). It is really nice OS, but yesterday I had problem with installing apps, and still have it. When I go to ubuntu software center and want to install app I have only option "Use this source" and there is no option "Install". I guess that this is not that big problem but I have no idea how to fix it cus I'm not expirienced with this OS, thx for any help guys :D.

EDIT: Okey I don't want to open new topic and spam forum so I will ask you here :), I just tryed to check out drivers for my laptop in "Additional Drivers" because I have problem with network card, sometimes I have to refresh pages for few times to open it (even this forum I had to refres few times till it worked). But after staying for about one minute and saying "Downloading and updating package indexes" and then i get error: "Downloading package indexes failed,please check your network status. Most drivers will not be available.". I guess I have some problems with network card cus sometimes i have to restart my laptop (satelite c660 Toshiba) in order to connect on network, cus it is only connecting and disconnecting from internet.

If you can help me with any of this problems thanks a lot. Sry for confusing post :D.

---

### Post by Gone fishing on 2012-03-20
Looks to me like the repository lists have got out dated.

Firstly open up the software centre go to edit > software sources and make sure all the repositories are ticked. Then close down software centre and

try openning a terminal running ```
sudo apt-get update
```

---

### Post by computerandu on 2012-03-20
try ```
sudo apt-get update
``` in terminal
img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

### Post by raja.genupula on 2012-03-20
```
sudo apt-get install --reinstall software-center
``` do this in your terminal.

---

### Post by guber90 on 2012-03-20
> **Gone fishing said:**
> Looks to me like the repository lists have got out dated.

Firstly open up the software centre go to edit > software sources and make sure all the repositories are ticked. Then close down software centre and

try openning a terminal running ```
sudo apt-get update
```
That didn't help, thanks for trying to help.

> **raja.genupula said:**
> ```
sudo apt-get install --reinstall software-center
``` do this in your terminal.

I get this error when I try to run that command:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of software-center is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by guber90 on 2012-03-20
Bump!

Anyone got idea :)?

---

### Post by Cheesemill on 2012-03-20
Type in the command:
```
cat /etc/apt/sources.list
```
And post the results back

---

### Post by Miljet on 2012-03-20
Looks like a problem with wireless card is preventing apt-get from downloading packages, or package information.

Open terminal and type ```
lspci
```
Post the results here so we can see what wireless chipset you have.

---

### Post by guber90 on 2012-03-20
> **Cheesemill said:**
> Type in the command:
```
cat /etc/apt/sources.list
```
And post the results back

This is what I get:


```
deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-backports main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-proposed restricted main multiverse universe
```

---

### Post by guber90 on 2012-03-20
> **Miljet said:**
> Looks like a problem with wireless card is preventing apt-get from downloading packages, or package information.

Open terminal and type ```
lspci
```
Post the results here so we can see what wireless chipset you have.

When I use that command i get:

```

armin@armin-Satellite-C660:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
06:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

```

---

### Post by guber90 on 2012-03-21
Bump.

---

### Post by Gone fishing on 2012-03-21
OK lets jst make sure of a few things.

firstly when you sudo apt-get update I'm assuming it is not connecting to the internet? What error do you get.

How are you connecting to the net? is it through a proxy for example? are you at a university or work where the repositories may have been blocked for some reason?

If  the above are problems what happens if you change the repository server?

Software centre > Edit > software sources and in Download from pick a different server near you. 

I'm assuming you cant install synaptic sudo apt-get install synaptic just check that isn't the case.

---

### Post by guber90 on 2012-03-21
> **Gone fishing said:**
> OK lets jst make sure of a few things.

firstly when you sudo apt-get update I'm assuming it is not connecting to the internet? What error do you get.

How are you connecting to the net? is it through a proxy for example? are you at a university or work where the repositories may have been blocked for some reason?

If  the above are problems what happens if you change the repository server?

Software centre > Edit > software sources and in Download from pick a different server near you. 

I'm assuming you cant install synaptic sudo apt-get install synaptic just check that isn't the case.

I get next when I use sudo apt-get update code:

```
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en
Err http://ppa.launchpad.net oneiric InRelease                                 
  
Err http://ppa.launchpad.net oneiric InRelease                                 
  
Err http://ppa.launchpad.net oneiric InRelease                                 
  
Err http://ppa.launchpad.net oneiric Release.gpg                               
  Unable to connect to 172.16.23.25:3128:
Err http://ppa.launchpad.net oneiric Release.gpg                               
  Unable to connect to 172.16.23.25:3128:
Err http://ppa.launchpad.net oneiric Release.gpg                               
  Unable to connect to 172.16.23.25:3128:
Err http://archive.ubuntu.com oneiric InRelease                                
  
Err http://archive.ubuntu.com oneiric-updates InRelease                        
  
Err http://archive.ubuntu.com oneiric-backports InRelease                      
  
Err http://archive.ubuntu.com oneiric-security InRelease                       
  
Err http://archive.ubuntu.com oneiric-proposed InRelease                       
  
Err http://archive.ubuntu.com oneiric Release.gpg                              
  Unable to connect to 172.16.23.25:3128:
Err http://archive.ubuntu.com oneiric-updates Release.gpg                      
  Unable to connect to 172.16.23.25:3128:
Err http://archive.ubuntu.com oneiric-backports Release.gpg                    
  Unable to connect to 172.16.23.25:3128:
Err http://archive.ubuntu.com oneiric-security Release.gpg                     
  Unable to connect to 172.16.23.25:3128:
Err http://archive.ubuntu.com oneiric-proposed Release.gpg                     
  Unable to connect to 172.16.23.25:3128:
Err http://extras.ubuntu.com oneiric InRelease                                 
  
Err http://extras.ubuntu.com oneiric Release.gpg                               
  Unable to connect to 172.16.23.25:3128:
Err http://archive.canonical.com oneiric InRelease
  
Err http://archive.canonical.com oneiric Release.gpg
  Unable to connect to 172.16.23.25:3128:
Reading package lists... Done
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/oneiric/InRelease  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/oneiric-backports/InRelease  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/oneiric-security/InRelease  

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/oneiric/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/InRelease  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/oneiric-proposed/InRelease  

W: Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/InRelease  

W: Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/oneiric/InRelease  

W: Failed to fetch http://ppa.launchpad.net/ubuntuwine/ppa/ubuntu/dists/oneiric/InRelease  

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/Release.gpg  Unable to connect to 172.16.23.25:3128:

W: Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/oneiric/Release.gpg  Unable to connect to 172.16.23.25:3128:

W: Failed to fetch http://ppa.launchpad.net/ubuntuwine/ppa/ubuntu/dists/oneiric/Release.gpg  Unable to connect to 172.16.23.25:3128:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg  Unable to connect to 172.16.23.25:3128:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg  Unable to connect to 172.16.23.25:3128:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg  Unable to connect to 172.16.23.25:3128:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg  Unable to connect to 172.16.23.25:3128:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/oneiric-proposed/Release.gpg  Unable to connect to 172.16.23.25:3128:

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg  Unable to connect to 172.16.23.25:3128:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/oneiric/Release.gpg  Unable to connect to 172.16.23.25:3128:

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

I use my home network wich works fine on Win7 (same laptop).

Changing my repository server doesn't help.

And I can't download synaptic.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'synaptic' has no installation candidate

```

---

### Post by matt_symes on 2012-03-21
Hi

> Unable to connect to **172.16.23.25**:3128:

This is a private IP address. When did this start happening ? Has it always happened since you installed ?

Kind regards

---

### Post by guber90 on 2012-03-22
> **matt_symes said:**
> Hi



This is a private IP address. When did this start happening ? Has it always happened since you installed ?

Kind regards

No it hasn't it was working fine I didn't had any problems but suddenly it started happening. I can use my browser to download anything, to watch anything, to read anything, but can't do it with USC or terminal.

---

### Post by Gone fishing on 2012-03-22
You are connecting through a proxy

IP address 172.16.23.25 
Port 3128

Why? 

Is Windows working through a proxy?

Open the Dash type network open the network application and open the proxy settings if you are not using a proxy remove the settings by selecting none also check if in /etc/apt/apt.conf.d there is any file named proxy

---

### Post by guber90 on 2012-03-22
> **Gone fishing said:**
> You are connecting through a proxy

IP address 172.16.23.25 
Port 3128

Why? 

Is Windows working through a proxy?

Open the Dash type network open the network application and open the proxy settings if you are not using a proxy remove the settings by selecting none also check if in /etc/apt/apt.conf.d there is any file named proxy

It is already turned off I don't use proxy on Windows, cus I don't need it. Only I use proxy on my college and I didn't use it a long time ago.

In /etc/apt/apt.conf.d t here is none file called proxy or something like that.

---

### Post by Gone fishing on 2012-03-22
OK so have you 

followed this advice
> 
Open the Dash type network open the network application and open the proxy settings if you are not using a proxy remove the settings by selecting none also check if in /etc/apt/apt.conf.d there is any file named proxy

Somewhere there is a proxy setting /root/.bashrc perhaps if not lets try and find the reference using sudo grep -lir "172.16.23.25 " /etc/ and sudo grep -lir "172.16.23.25 " /root/

---

### Post by guber90 on 2012-03-23
> **Gone fishing said:**
> OK so have you 

followed this advice


Somewhere there is a proxy setting /root/.bashrc perhaps if not lets try and find the reference using sudo grep -lir "172.16.23.25 " /etc/ and sudo grep -lir "172.16.23.25 " /root/

For first command I get:

```
grep: /etc/blkid.tab: No such file or directory

```

For the second one:

```
grep: /root/: Permission denied

```

---

### Post by Gone fishing on 2012-03-23
for the second command I think you didn't sudo

> **sudo** grep -lir "172.16.23.25 " /root/ I think you may have proxy settings in the /root/.bashrc file. it is possible if you have this file /etc/apt/apt.conf it may have proxy settings if either of this file make reference to proxy remove them or better # them out (i.e. put a # in front of the line)

gksudo gedit /etc/apt/apt.conf and gksudo gedit /root/.bashrc

Did you college use 172.16.23.25:3128 for it's proxy settings?

---

### Post by guber90 on 2012-03-27
> **Gone fishing said:**
> for the second command I think you didn't sudo

 I think you may have proxy settings in the /root/.bashrc file. it is possible if you have this file /etc/apt/apt.conf it may have proxy settings if either of this file make reference to proxy remove them or better # them out (i.e. put a # in front of the line)

gksudo gedit /etc/apt/apt.conf and gksudo gedit /root/.bashrc

Did you college use 172.16.23.25:3128 for it's proxy settings?
I had to restart ubuntu and then do that command and now everything works. 

I reinstalled USC and now I can download.

Thank a lot for your time and help :).

---

### Post by Gone fishing on 2012-03-27
Thanks but could you mark as solved

---

### Post by guber90 on 2012-03-27
> **Gone fishing said:**
> Thanks but could you mark as solved

Like u can see I'm new on forum and didn't know for that option :D, thx again :D.

---

