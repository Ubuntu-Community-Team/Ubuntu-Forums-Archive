---
title: "Wireless Problems"
date: 2011-09-09
forum: New to Ubuntu
---

### Post by mameshiba on 2011-09-09
I'm using 10.04 (Lucid) on a Stylenote laptop, which is just a year old. When I first got it, it would automatically scan for wireless networks on startup. Then, for a while it would occasionally find them but have trouble staying connected to them. Now, it doesn't seem to scan for them at all.

Is this likely to be a system problem that can fixed without replacing the network card? I keep looking in System > Preferences > Network Connections over and over again, but the problem is that it just isn't picking up signals at all and I can't work out how to make it look for them :/

---

### Post by heyandy889 on 2011-09-09
Sounds to me like a problem with the driver for the wireless card. Some drivers are proprietary, notably Broadcomm. Here's what I would do if you brought your laptop to me.

[LIST]
[*]Connect to the Internet via a wired connection
[*]Run Update Manager. Found in System>Admin>Update Manager (if I recall correctly!)
[*]Run updates for drivers. Found in System>Admin>Additional Drivers (might be called "Hardware Drivers")
[/LIST]

Does that help?

edit: if that doesn't work, I'd suspect that either you need a proprietary driver, or that, as you suspect, something is wrong with your wireless card.

---

### Post by rolandrock on 2011-09-09
If you need more help, open a terminal and post the output of this command:

> lspci -k

---

### Post by anewguy on 2011-09-09
Since it is a laptop, and some laptops have their built-in wireless connected to an internal USB bus, please also post the output of:

lsusb

in addition to the lspci requested by rolandrock.  That way we should see the devices on the pci and usb busses.

Dave ;)

---

### Post by mameshiba on 2011-09-10
I have run Update Manager. All up to date.

I do not seem to have 'Additional Drivers' in System > Admin.

This is the output from lspci -k:

> carrie@carrie-laptop:~$ lspci -k
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
	Kernel modules: sis-agp
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
	Kernel driver in use: pata_sis
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
	Kernel driver in use: ohci_hcd
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
	Kernel driver in use: ohci_hcd
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
	Kernel driver in use: ehci_hcd
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
	Kernel driver in use: sis190
	Kernel modules: sis190
00:05.0 SATA controller: Silicon Integrated Systems [SiS] AHCI IDE Controller (0106) (rev 03)
	Kernel driver in use: ahci
	Kernel modules: ahci
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
01:00.0 VGA compatible controller: nVidia Corporation G98M [GeForce G 105M] (rev a1)
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidiafb, nouveau
03:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 20)
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci
03:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 20)
	Kernel modules: sdhci-pci
03:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 20)
	Kernel driver in use: jmb38x_ms
	Kernel modules: jmb38x_ms
carrie@carrie-laptop:~$ ^C
carrie@carrie-laptop:~$ ^C
carrie@carrie-laptop:~$ 


And from lsusb:

> carrie@carrie-laptop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 5986:0241 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
carrie@carrie-laptop:~$ 


---

### Post by anewguy on 2011-09-10
Do you actually have the wireless card in the laptop?  I don't see anything on the outputs you provided that indicate a wireless network controller.

dave ;)

---

### Post by westie457 on 2011-09-10
What is the output of ```
lshw -C network
``` and ```
rfkill list all
```

Thank You.

---

### Post by fdrake on 2011-09-10
you should update the kernel and install backports:
```

sudo gedit /etc/apt/sources.list 

```
and add this at the end
> 
url: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
distribution: lucid-backports
sections: main universe multiverse restricted

save, close, reboot. then run this commands. 
```

sudo apt-get install --reinstall linux-image-$(uname -r)
sudo apt-get upgrade -u -t $(less /etc/lsb-release | grep "DISTRIB_CODENAME" | cut -d "=" -f 2)-backports
sudo apt-get update && sudo apt-get upgrade

```
reboot and see if the wifi is working. if not, then post the results of these commands:

```

sudo lshw -c Network
lsmod
rfkill list all

```

---

### Post by mameshiba on 2011-09-10
As requested:

> carrie@carrie-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:90:f5:98:02:5f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis190 driverversion=1.3 ip=192.168.1.10 latency=0 multicast=yes
       resources: irq:19 memory:d3307000-d330707f ioport:1000(size=128)
carrie@carrie-laptop:~$ 


There is no output at all for > rfkill list all

Also:

> sudo /etc/apt/sources.list

'command not found'

:(

---

### Post by mameshiba on 2011-09-10
... Also... There is definitely a wireless network card in there, unless someone took the laptop apart and removed it when I wasn't looking, which is highly unlikely as I rarely allow anyone else near it! Heh.

---

### Post by anewguy on 2011-09-10
Please note there is still no hint of wireless hardware being known to Ubuntu.  Ubuntu will normally show the hardware even if there is no driver, etc., so it doesn't know how to use the hardware.

That being the case, please post back the model of your Style Note, so we can try to look up the specs and see what wireless it was supposed to have.

If there is a button to turn wireless on/off, try being sure it is on then retry the lspci and lsusb.

As far as editing the sources, you need to specify what you want to do with the file - in this case edit it.  So:

sudo _gedit_ /etc/apt/sources.list (you just left off the "gedit")

dave ;)

---

### Post by mameshiba on 2011-09-10
Switch it on using the button! Ha! There *is* a wireless button but I *totally* didn't realise it was there.

Anyway, new outputs:

> carrie@carrie-laptop:~$ lspci -k 
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
	Kernel modules: sis-agp
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
	Kernel driver in use: pata_sis
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
	Kernel driver in use: ohci_hcd
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
	Kernel driver in use: ohci_hcd
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
	Kernel driver in use: ehci_hcd
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
	Kernel driver in use: sis190
	Kernel modules: sis190
00:05.0 SATA controller: Silicon Integrated Systems [SiS] AHCI IDE Controller (0106) (rev 03)
	Kernel driver in use: ahci
	Kernel modules: ahci
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
01:00.0 VGA compatible controller: nVidia Corporation G98M [GeForce G 105M] (rev a1)
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidiafb, nouveau
03:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 20)
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci
03:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 20)
	Kernel modules: sdhci-pci
03:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 20)
	Kernel driver in use: jmb38x_ms
	Kernel modules: jmb38x_ms
carrie@carrie-laptop:~$ 


> carrie@carrie-laptop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 5986:0241 Acer, Inc 
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
carrie@carrie-laptop:~$ 


> carrie@carrie-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:90:f5:98:02:5f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis190 driverversion=1.3 ip=192.168.1.10 latency=0 multicast=yes
       resources: irq:19 memory:d3307000-d330707f ioport:1000(size=128)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:25:d3:96:a5:80
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.15 multicast=yes wireless=IEEE 802.11bg
carrie@carrie-laptop:~$ 


> carrie@carrie-laptop:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
carrie@carrie-laptop:~$ 


Then I followed the instructions posted by fdrake to the letter and got:

> carrie@carrie-laptop:~$ sudo apt-get install --reinstall linux-image-$(uname -r)[sudo] password for carrie: 
E: Type ‘url:’ is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
carrie@carrie-laptop:~$ 


In any case, it *does* seem to be picking up signals now as before, but it's a very a shaky connection even though I am sat next to the router...

---

### Post by gandaran on 2011-09-10
> carrie@carrie-laptop:~$ sudo apt-get install --reinstall linux-image-$(uname -r)[sudo] password for carrie: 
E: Type &#8216;url:&#8217; is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
carrie@carrie-laptop:~$
you got a problem here with a third party repository you have added incorrectly, either correct the entry or remove it completly from software sources.

---

### Post by gandaran on 2011-09-10
> Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps 
if I remember correctly I have read on some threads Ubuntu users are having problems with this wireless chipset RTL8187B, try searching the forum for RTL8187B threads, if I'm not wrong you just have to blacklist the RTL8187B driver so it can really work without any problem.

---

### Post by fdrake on 2011-09-10
it look like the source list is not accepting that kind of format. I tried on mine Lucid ,so you have to do:
1)
```
sudo gedit /etc/apt/sources.list
```
remove the line i suggested in my previous post and replace them with the following instead:
> 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports  restricted  main universe multiverse


2)
```

sudo apt-get install --reinstall linux-image-$(uname -r)
sudo apt-get upgrade -u -t $(less /etc/lsb-release | grep "DISTRIB_CODENAME" | cut -d "=" -f 2)-backports
sudo apt-get update && sudo apt-get upgrade
sudo aptitude install wireless-tools

```

3)
```

sudo gedit /etc/modprobe.d/blacklist.conf 

```
and look if there is a line "blacklist  rtl8187". if there is a line like that edit it to "# blacklist  rtl8187".

after that add these lines at the end
> 
# conflicts with rtl8187:
blacklist r8187se
blacklist rtl8187se
blacklist rtl8180
blacklist rtl8187B
 
save and close

4)
```

sudo modprobe rtl8187

```

5) reboot and test the wifi (make sure your switcher is ON!)
if you still have problem please post here:
```

lsmod
less /etc/modprobe.d/blacklist.conf
sudo iwlist scan
iwconfig

```

---

### Post by walt.smith1960 on 2011-09-10
I don't know why yours won't connect but I have a RealTek TEW-424UB which uses a RealTek 8187B chip.  It has been perfect, connects out of the box since 8.10.  Was there an 8187(no b) chip that was problematic?  I do remember something but don't recall details.  I wonder if it would be worth burning a liveCD and try using that.  I wonder if earlier efforts have caused problems.

Don't feel bad about not seeing the WiFi switch.  I just had the same thing happen with an Ebay purchase.  I had to download the manual to find the WiFi switch.

---

### Post by mameshiba on 2011-09-10
> **fdrake said:**
> it look like the source list is not accepting that kind of format. I tried on mine Lucid ,so you have to do:
 ```
sudo gedit /etc/apt/sources.list
```
remove the line i suggested in my previous post and replace them with the following instead:

I have done this and I now seem to have fully working lighting-fast wireless access! Thanks very much, for all your efforts and advice!

---

### Post by fdrake on 2011-09-10
> **mameshiba said:**
> I have done this and I now seem to have fully working lighting-fast wireless access! Thanks very much, for all your efforts and advice!

i am happy for you.! :D
just a tip: when you install/update/upgrade your kernel make sure backports are always enabled other wise you will always encounter this problem all the time. 
):P

---

