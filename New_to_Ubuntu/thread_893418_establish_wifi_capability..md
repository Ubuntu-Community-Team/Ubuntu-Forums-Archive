---
title: "establish wifi capability."
date: 2008-08-18
forum: New to Ubuntu
---

### Post by nnjond on 2008-08-18
Hi, I would like to establish the wifi capability on my new Laptop although *I* dont have the option at this address.

I have installed Hardy and there is a tick by "Wireless enabled".  However my network icon has a little red/orange triangle on it and it claims "No Network Connection" even when I'm in the presence of a router.

What should I do next?

Thanks.

---

### Post by porchrat on 2008-08-18
Do you know which wireless module/card you're running?

Please type this to see which card you're running:

```
sudo lshw -C network
```

I used the madwifi driver recently on an Acer and it worked first time.


you can then either go to the madwifi website and check if your card is supported (it should be) or if you're unsure then copy and paste the ouput of that command in here.

you can take a look at the madwifi site here:

[http://madwifi.org/]("http://madwifi.org/")

hope this helps

---

### Post by nnjond on 2008-08-18
nnjond@nnjond-laptop:~$ sudo lshw -c network 
[sudo] password for nnjond: 
Hardware Lister (lshw) - B.02.12.01 
usage: lshw [-format] [-options ...] 
       lshw -version 

	-version        print program version (B.02.12.01) 

format can be 
	-html           output hardware tree as HTML 
	-xml            output hardware tree as XML 
	-short          output hardware paths 
	-businfo        output bus information 

options can be 
	-class CLASS    only show a certain class of hardware 
	-C CLASS        same as '-class CLASS' 
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. ) 
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. ) 
	-quiet          don't display status 
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.) 

nnjond@nnjond-laptop:~$

---

### Post by porchrat on 2008-08-18
> **nnjond said:**
> nnjond@nnjond-laptop:~$ sudo lshw -c network 
[sudo] password for nnjond:

You have a typo there.

You have to use a capital C.

Copy and paste this into the terminal

```
sudo lshw -C network
```

---

### Post by nnjond on 2008-08-18
nnjond@nnjond-laptop:~$ sudo lshw -C network 
  *-network               
       description: Ethernet interface 
       product: RTL8101E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 01 
       serial: 00:0a:e4:ce:78:00 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair 
  *-network 
       description: Wireless interface 
       product: AR242x 802.11abg Wireless PCI Express Adapter 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:08:00.0 
       logical name: wlan0 
       version: 04 
       serial: 00:16:44:c3:71:d2 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.52+,11/15/2006,5.1.1.9 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g 
nnjond@nnjond-laptop:~$

---

### Post by porchrat on 2008-08-18
OK that is an Atheros card meaning that the madwifi driver should work.  As I used this driver on the same card. :)


move to a directory in which you want to keep the downloaded driver (i normally keep these sort of things in my /home/my_user_name/downloads/ but you can move to whereever you want.

If you haven't already installed these then do so now:

```
sudo apt-get install build-essential linux-headers-generic 
```


Then go and get the file of the net:

```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz 
```


then uncompress it:

```
tar zxvf madwifi-hal-0.10.5.6-current.tar.gz 
```


now navigate into the directory that should've been created when you uncompressed that file:

```
cd madwifi-hal-0.10.5.6-r3835-20080801/
```


That name may change as the version changes, but I doubt it has changed yet.

Then run these commands to build it for your kernel:

```
make
sudo make install
sudo modprobe ath_pci

```

You should then restart your machine and it should work.

One more thing though.  Whenever you update your kernel you will have to navigate to that madwifi-hal-0.10.5.6-r3835-20080801 directory again and run this in order to build it for the new kernel:

```
make clean
make
sudo make install
sudo modprobe ath_pci
```

I hope it helps you.

---

### Post by nnjond on 2008-08-18
Thanks for your help but I seem to have a prob.


nnjond@nnjond-laptop:~$ wget [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz)
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
nnjond@nnjond-laptop:~$

---

### Post by porchrat on 2008-08-18
This may seem like a silly question but do you have an internet connection on the machine you are installing this driver on?

If you are running a direct connection then you should try disable any proxy settings you may have.

Or you can just go to that URL with a browser and download it that way if you're experiencing a problem with wget.

---

### Post by nnjond on 2008-08-18
i do now.

How do i disable?

---

### Post by porchrat on 2008-08-18
Try clicking on this URL then:

[http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz]("http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz")

It should then ask you to download it and you can then just drag and drop it into the location you want to store it under.

---

### Post by nnjond on 2008-08-18
It's decompressed in DOWNLOADS. What should I do next?

---

### Post by porchrat on 2008-08-18
I've got to go for now but I'll get back to you as soon as I am able.

cheers for now

Should be a couple of hours...sorry

---

### Post by nnjond on 2008-08-18
I seem to have followed your instructs properly, but the little red triangle is still there when i disconnect the land line?  I'm not sure if there's a router in my vicinity now.

---

### Post by porchrat on 2008-08-18
So you have done the whole guide including building the package into the kernel?

---

### Post by porchrat on 2008-08-18
Sorry I forgot that you need to disable your old wifi drivers.

You'll find this under 'System' -->  'Administration' --> 'Hardware Drivers'


You'll then have to restart your system

Then you need to navigate into your ~/DOWNLOADS/madwifi-hal-0.10.5.6-r3835-20080801/ 

Then run this in console:


```
make clean
make
sudo make install
sudo modprobe ath_pci
```

restart and you should be able to see the wireless in your network configuration area under 'System' --> 'Administration' --> 'Network'

After a few brief settings you should be good to go

Let me know if you have any more trouble.  I'll check back in again tomorrow :guitar:

---

### Post by nnjond on 2008-08-18
Still with the red triangle. And now I've lost the tick by the Wireless enabled.

---

### Post by porchrat on 2008-08-19
Are you running 64bit or 32bit hardy?

---

### Post by porchrat on 2008-08-19
I found a guide that seems to be working for a lot of people, it's an alternative to this method and it is very easy to follow.

It has a version for 32bit and 64bit users and you can check it out here:

[http://bhatt.findtechblogs.com/default.asp?item=2202124]("http://bhatt.findtechblogs.com/default.asp?item=2202124")

It should do the trick and seems to run a little faster on some systems than the way I got it running.  It will also disable the new driver you installed now.

Although you should just recheck the check boxes next to those atheros drivers under 'System' --> 'Administration' --> 'Hardware Drivers'  and then restart.  I would recommend doing this before you try using that guide I told you about.

I've just noticed something though.  You said:

> I seem to have followed your instructs properly, but the little red triangle is still there when i disconnect the land line? I'm not sure if there's a router in my vicinity now.

What do you mean you're not sure there is a router in your vicinity?

Could you explain a little more about how you are trying to connect to the internet via wireless?  Generally you need a wireless router in your home that is somehow connected to the internet (via DSL cable or whatever).  That router needs to be setup with your username and password given to you by your ISP.

---

### Post by nnjond on 2008-08-19
I have no "wifi" of my own at this address. Nevertheless Ibelive it should registers the existence of others in the vicinity.  If there are none at present, I wish to enable my laptop so as it will connect in hotspots that i travel to.

---

### Post by nnjond on 2008-08-19
Your advice seems to apply to someone with an Atheros AR5007 wireless network adapter. Wheras I believe I have an

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
08:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 04)

---

### Post by porchrat on 2008-08-19
That particular card has various names.

The actual card is called the AR5007EG, however in gutsy gibbon ubuntu it was called the AR5006EG, now under hardy heron it is called the AR242x

They're actually the same card...strange but true

---

### Post by porchrat on 2008-08-19
I don't know how prolific wireless networks are where you live, but around here I pick up 3 other networks including my own so you should be able to pick up at least one.

However that isn't really a reliable way to test it.  My suggestion would be to take the laptop to a hotspot and try these guides out (after downloading everything you need to set it up so that you don't need the internet while you work on it).

To scan for wireless networks (although I've never tried it myself as I just plugged in my network settings and was good to go) you type:

sudo iwlist scan

---

