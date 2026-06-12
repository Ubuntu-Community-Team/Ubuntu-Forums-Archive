---
title: "[SOLVED] Need Urgent Help: My screen freezes a few minutes after boot"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by mvalviar on 2008-11-28
Hi,

I really don't know where to start with this. It's just a normal installation of Ubuntu 8.04 from a Live CD. I have some compiz-fusion effects on. I can't tell what other information is related to this problem. It just happens every time I start my computer. A few minutes after the desktop, whether I start a few programs or not there will be a slight screen flicker and everything freezes. There is a response on the mouse but it skips or freezes sometimes. There really isn't anything I can do but to do a hard restart. After that everything runs fine. But it happens everyday. At the end of the day I turn it off. Then the next day I turn it on after a few minutes the screen flickers then freezes and I have to hard restart. Its frustrating because I don't know what to do. I looked at the system log but I can't see anything out of the ordinary. Or maybe because I don't know where to look or what to look for. Please help me.

---

### Post by Michael.Godawski on 2008-11-28
It would be helpful to know your specs. When you are in Ubuntu please run these commands in terminal and post the output:

```
lspci
sudo lshw
```

And you say after your system crashes once and you restart everything works fine without any problems?

---

### Post by mvalviar on 2008-11-28
Thanks,

I got the following output

lshw got:

```
mvalviar-desktop
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1010MiB
     *-cpu
          product: Intel(R) Pentium(R) D CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.6.5
          serial: 0000-0F65-0000-0000-0000-0000
          size: 3003MHz
          capacity: 3003MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc pebs bts pni monitor ds_cpl est cid cx16 xtpr lahf_lm cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82945G/GZ/P/PL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 7100 GS
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:02:05.0
                logical name: eth0
                version: 10
                serial: 00:1e:90:f4:20:72
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.101 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-ide:1
             description: IDE interface
             product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
```

lspci got:
```
mvalviar-desktop
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1010MiB
     *-cpu
          product: Intel(R) Pentium(R) D CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.6.5
          serial: 0000-0F65-0000-0000-0000-0000
          size: 3003MHz
          capacity: 3003MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc pebs bts pni monitor ds_cpl est cid cx16 xtpr lahf_lm cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82945G/GZ/P/PL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 7100 GS
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:02:05.0
                logical name: eth0
                version: 10
                serial: 00:1e:90:f4:20:72
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.101 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-ide:1
             description: IDE interface
             product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
```

Yes, it works fine after I hard restart.

---

### Post by taseedorf on 2008-11-28
instead of doing a hard reset are you able to get to a command prompt...either going to terminal...or ...ctrl+alt+f4?
if so type sudo /etc/init.d/gdm stop
than try
sudo /etc/init.d/gdm start

than type 
startx

does ur screen flicker or do u have to do a hard reset still?

have i tried reconfiguring your x server?

dpkg-reconfigure xserver-xorg
(might need an extra dash in there)

---

### Post by mvalviar on 2008-11-28
The keyboard isn't responding. But when I try to Ctrl-Alt-F1 the mouse pointer disappears and it's a complete lock down.

---

### Post by bwallum on 2008-11-28
> **mvalviar said:**
> The keyboard isn't responding. But when I try to Ctrl-Alt-F1 the mouse pointer disappears and it's a complete lock down.

Sounds like a hardware problem. Have you recently been changing anything inside the box?

---

### Post by mvalviar on 2008-11-28
There really is no way for me to access the console whenever this happens.

I don't know much when it comes to hardware. I try to keep my hands of the box as much as possible specially now than I'm running on GNU/Linux.

---

### Post by CatKiller on 2008-11-28
> **mvalviar said:**
> It just happens every time I start my computer. A few minutes after the desktop, whether I start a few programs or not there will be a slight screen flicker and everything freezes. There is a response on the mouse but it skips or freezes sometimes. There really isn't anything I can do but to do a hard restart. After that everything runs fine. But it happens everyday. At the end of the day I turn it off. Then the next day I turn it on after a few minutes the screen flickers then freezes and I have to hard restart.

It is cold overnight there?

---

### Post by mvalviar on 2008-11-28
Definitely not, its quite the opposite.

The big question is. Why does it screw up when I turn it on. But works fine after a hard restart??!!

---

### Post by lovinglinux on 2008-11-28
> **mvalviar said:**
> Definitely not, its quite the opposite.

The big question is. Why does I screw up when I turn it on. But works fine after a hard restart??!!

I will shoot in the dark, so please don't shoot me back.

Try checking if the fans are working correctly, including the one in the power supply, and if the computer is not overheating when it freezes. Also check system voltages.

I'm suggesting this because my machine makes a lot of noise when I turn it on, then if I reboot the noise stops. I discovered that is the power unit fan that get stuck or something when turning on from cold. Then If I reboot, the fan seems to get into place and the noise stops.

It's a long shot, but maybe your power supply is overheating and not providing the necessary amount of energy to the machine.

---

### Post by mvalviar on 2008-11-28
> **lovinglinux said:**
> I will shoot in the dark, so please don't shoot me back.

Try checking if the fans are working correctly, including the one in the power supply, and if the computer is not overheating when it freezes. Also check system voltages.

I'm suggesting this because my machine makes a lot of noise when I turn it on, then if I reboot the noise stops. I discovered that is the power unit fan that get stuck or something when turning on from cold. Then If I reboot, the fan seems to get into place and the noise stops.

It's a long shot, but maybe your power supply is overheating and not providing the necessary amount of energy to the machine.

The fans are working properly. Thanks for the suggestion.

I experimented with it a couple of times. When I start the day I usually launch Pidgin, Evolution, and Gedit. I also run Xampp on the Gedit console. Then after 2-3 minutes the screen flickers then the screen freezes. I remember that there is one case that I launched played an mp3 and it kept playing even though the screen is frozen. I tried to use the mouse to launch the terminal. Although the pointer moves its not responding to my clicks. Then I tried to reach the console by ctrl-alt-f1 then then the music died and the mouse pointer disappears. ](*,)

---

### Post by bwallum on 2008-11-28
It definitely seems to be hardware. You mention heat being a possibility where you are. You also say you get some functionality when the pc partially shuts down. It could be the motherboard overcooked. I rule out the cpu shutting down because of the limited functionality. When the cpu shuts down everything is dead. Similarly the gpu will have a cut out temp and when that goes all the screen goes. Most gpus have a slow running temp too so that may be something but it would manifest itself as just going very slow rather than going wrong.

The motherboard 'system' could cut out too if over heated. Equally your harddrives would get erratic when overheating. So how do you tell?

It's difficult but Ubuntu has a way of detecting sensors. This is what I would do to try and eliminate hardware issues.

Load lm-sensors and sensors-applet along with all dependencies. Use the terminal> sudo apt-get install lm-sensors sensors-applet hddtemp

If you get that far before the system plays up you may want to shut down and allow to cool before the next step.

Now you need to start the hardware monitor service so, using the gui, go System>Administration>Services.

When the window comes up check Hardware-monitor (lm-sensors) then close.
Find a space on the top panel right at the top of the screen and right click, then click Add to Panel. Scroll down and click on Hardware Sensors Monitor. When a load of icons and temps appear on the top panel right click on one of the icons. Click Preferences. In the Sensors tab you should now have a range of sensors to display. Choose something significant like system temp and check to see that it stays within manufacturers limits. (you may need to reboot to get these readouts running properly) Usually the manufacturers web site can lead you to a support section with this stuff in. Generally, a system temp over 35 degrees centigrade would be of concern (i.e. expected to play up), cpu over 65, harddrive over 45, gpu over 75. That's my guidelines only, using the manufacturers guidelines is always best. 

If you are convinced it is not an hardware issue then please come back.

---

### Post by mvalviar on 2008-11-28
It just did it again. When I turned it on earlier. I'm using it now after I did a hard restart.

---

### Post by mvalviar on 2008-11-29
@bwallum thanks for the suggestion. I've given it a try. 

Its warm but the temperature is still within the limit. The thing is this always happens in the coldest part of the day in my place. Around 8-9am its around 25-28 degrees. When I turn in on it will act up after 2-5mins then I'll restart and I will work flawlessly through out the entire day even on the hottest hours of 12nn-3pm where it soars to 30-33 degrees. I will end my day at around 10-12mn and will return to it in the morning. I has become a standard practice for me to turn it on log-in and hard restart on the spot because I expect it to act up.

Thanks for your suggestions and opinions. I know that all of your are more knowledgable than me. But in my own opinion maybe there is some daemon (no pun intended) that messing with my system. Or maybe its X. It wasnt like this a week ago. Perhaps it started when I installed postfix because I need it to test the Php/pear mail function/class. Maybe there is something I installed that messed up with the system settings somehow. 
I hope someone can figure this out.

---

### Post by mvalviar on 2008-11-29
I did exactly what bwallum said. I installed the sensors earlier turned off my pc completely and worked using another pc. I returned to it in a couple of hours. I was just putting the sensors on my panel when the screen froze. The sensors read 40 for the CPU and 37 for the hard drive (both in Celsius). I was playing an mp3 at that moment and I kept playing even though the screen is frozen and the mouse and keyboard are not responding. The temperature is well below the limit when it froze. I'm typing this on the dreaded ubuntu pc that is working well after I restarted it after it locked down. I even turned of compiz completely but to no avail.

Here's how the log goes when all this happened this is under syslog(none of the other logs shows information around 18:29--the time the system froze):

```

Nov 29 18:22:37 mvalviar-desktop dhcdbd: Started up.
Nov 29 18:22:39 mvalviar-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Nov 29 18:22:43 mvalviar-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Nov 29 18:22:43 mvalviar-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Nov 29 18:22:43 mvalviar-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Nov 29 18:22:43 mvalviar-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Nov 29 18:22:43 mvalviar-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Nov 29 18:31:27 mvalviar-desktop dhcdbd: Started up.
Nov 29 18:31:30 mvalviar-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Nov 29 18:31:33 mvalviar-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Nov 29 18:31:33 mvalviar-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Nov 29 18:31:33 mvalviar-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Nov 29 18:31:33 mvalviar-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Nov 29 18:31:33 mvalviar-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu 
```

The screen froze at 18:29:15 and it was back on at 18:31:27. #$%^&(($% ](*,) I don't know what to do.

---

### Post by bwallum on 2008-11-29
When you shut down at the end of the day, do you completely power down with all the power off, i.e. unplug or switch off from the mains? Then, when your system falls over first thing in the day, do you turn it off and on with the pc switch or do you completely power down as above?

I am trying to see if there is be a difference in starting from a reset scenario and starting from complete power down.

If there is a difference, trying powering down completely and then restart after say 1 minute and see if the system messes up again.

Also how old is the cmos store battery in your pc?

Could you also run ```
sudo sensors-detect
``` and follow the defaults (in upper case). You should get some power monitors as well, Check to see if the actual voltages are within manufacturers limits. Sometimes the limits in hardware monitor are not correct. You can set the limits for your specific machine. Again apologies for all the work.

Regards
Bob 

Bob

---

### Post by bwallum on 2008-11-29
One other environmental question please. Do you have high humidity there? If so you will get condensation on cooling down. Again there will be operational limits for the hardware to check against.

---

### Post by CatKiller on 2008-11-29
> **mvalviar said:**
> Its warm but the temperature is still within the limit. The thing is this always happens in the coldest part of the day in my place. Around 8-9am its around 25-28 degrees. When I turn in on it will act up after 2-5mins then I'll restart and I will work flawlessly through out the entire day even on the hottest hours of 12nn-3pm where it soars to 30-33 degrees.

Open the case. Check the capacitors (small vertical cylinders) for any signs of damage: any cracks or bulging, and especially if there's anything leaking from them. Check the graphics card too. Also check to make sure everything is seated properly. Capacitors can be replaced, but it's normally more worthwhile to replace the whole thing - the motherboard if the motherboard's capacitors have gone, or the graphics card if it's those that have gone.

I have seen it before that a computer wouldn't work on a cold boot but was fine when it had warmed up. Although 25 degrees isn't really what I'd call cold :)

You might find that in the BIOS there is a screen that will show you the voltages and temperatures of your computer. You could monitor these and see if the computer still locks up when it's just showing the BIOS information. You might find that there's a spike or drop in the voltages at the time that it locks up.

The capacitors can fail in the power supply too, but those are significantly harder to inspect. The functionality of the power supply is normally tested with a multimeter. Don't open the power supply.

Your computer doesn't seem especially old to me. Would you be able to get a replacement, or replacement parts, under warranty?

---

### Post by mvalviar on 2008-11-29
> **bwallum said:**
> When you shut down at the end of the day, do you completely power down with all the power off, i.e. unplug or switch off from the mains? Then, when your system falls over first thing in the day, do you turn it off and on with the pc switch or do you completely power down as above?

I am trying to see if there is be a difference in starting from a reset scenario and starting from complete power down.

If there is a difference, trying powering down completely and then restart after say 1 minute and see if the system messes up again.

Also how old is the cmos store battery in your pc?

Could you also run ```
sudo sensors-detect
``` and follow the defaults (in upper case). You should get some power monitors as well, Check to see if the actual voltages are within manufacturers limits. Sometimes the limits in hardware monitor are not correct. You can set the limits for your specific machine. Again apologies for all the work.

Regards
Bob 

Bob

@bwallum 
You need not apologize I appreciate all the help. I'm not on my ubuntu pc now. But yes I do turn it off completely at the end of the day. I turn off the AVR and sometimes I unplug it too (but that really doesn't matter, is it?). When it freezes is just press the power button for as long as it needs to be pressed to turn off the pc, then I let it go then press it again and it will run just fine. Regarding the battery I don't know how old it is but I guess its still ok since my clock is still running fine. I run those commands later and update you.

@CatKiller
I'll do what you mentioned about the BIOS later. Thanks. But I'm having second thoughts on opening the box. Still I'll try my best.

---

### Post by bwallum on 2008-11-29
I had a friend's machine a couple of weeks ago, an old Dell something 260 with a P4 processor. If you completely powered it down (switched off from mains) then started it up it would throw a keyboard error and refuse to boot. If I then pressed the pc's off switch until it died, then again to restart, it would not throw an error. This was repeatable every time I tried it. I checked out just about everything I could think of but couldn't find out why it was occurring. I thought it could be the bios. It was a dual boot XP and Intrepid so that complicated things a bit as well.

Could you just check if when you completely power down (switch off at wall), wait a minute, then you switch on, if you get the same problem happening as in the first start up of the morning (or not). If you do, try your normal fix routine then try to replicate the error again to establish if it is repeatable. 

Cat Killer's advice is ok, blown caps are lethal. However I would not open the box just yet if you are uncertain but you may need to later depending on what we find. The BIOS health readings are ok for a snapshot but I would keep the monitoring on the desktop panel as you can see this being updated every two seconds (default, you can change this if you like, right click on a monitoring item and choose preferences) as you use the machine. You will probably have to go into the BIOS at some stage so take a look at the health data as Cat Killer advises and while you are there just check that all the bits are as expected, in particular the memory, drives (hard and optical) and that the primary drive is the one you boot up on if IDE (doesn't apply to sata drives).

At this stage I would really like to establish if you can get the repeatable fall over error.

---

### Post by mvalviar on 2008-11-30
I talked to a friend about this and he mentioned that he experiencing the same problem on one pc he has on his net cafe. Its a P4 Dell running on xp. So you guys are right it is a hardware issue.

@bwallum
yes the problem is repeatable and consistent. Its not a few minutes but around an hour. I turn the whole thing off including the mains, wait for about an hour then turn it on, it will act up in a couple of mins then I'll restart and its good to go.

I decided start from scratch to see if there is any difference. So I decided to reinstall from a live hardy cd. I'll see tomorrow if the problem persists. If I does I guess I'll have to trash this box and buy a new one and install hardy.

---

### Post by CatKiller on 2008-11-30
> **mvalviar said:**
> I'll see tomorrow if the problem persists. If I does I guess I'll have to trash this box and buy a new one and install hardy.

Crikey, that's a bit extreme. It's possible that it's simply caused by something not being seated properly. Not likely, given the symptoms, but definitely possible. You'd expect to see some flakiness as the connection wasn't quite there, and then when the component had expanded slightly with the raised temperature the contact would be good and it would be fine.

If one of the components has failed, it's possible to replace just that component and continue using the rest of the computer. It's got to be worth a look, surely?

---

### Post by mvalviar on 2008-11-30
@CatKiller
Crickey! Kinda missed Steve Irwin (R.I.P.).

Well, I'm fixin' to buy a new one anyway since its the Christmas season. GNU/Linux rocks and I don't want it to run on this box while an my Xp runs on a better pc. I wanted to migrate that other one to ubuntu too but its just to much work for me. I have so many important files in there and I don't want it to get messed up. 

Still I wanted to have this issue sorted out because I'm encouraging my friend to move to ubuntu and this problem isn't helping.

Oh, when I say "trash a pc" I mean putting it somewhere in the house to gather dust.

---

### Post by bwallum on 2008-12-01
I'm with CatKiller, it sounds like a fixable problem and such a waste to just let it gather dust. 

The problem in my estimation is now narrowed down to the BIOS (or bios settings for the hardware). Have you managed to get into the BIOS setup screen yet? If so a very good place to start is to reset the BIOS to factory defaults. It is very easy to do and will not affect your working files at all. However, back up all the stuff you think is important first.

If you are not sure about how to access the bios it is generally a question of repeatedly tapping the appropriate key. That will be either 'del' or 'F1' or 'F2' or 'F10' normally. At start up your screen should say "Press (key) to enter Setup" but this may be lost to you if a proprietory splash screen gets in the way. Just keep trying the above keys before the OS boots.

It would be good to set the bios to factory defaults then test if the problem persists. Also, are you dual boot?

EDIT: Suggest to your friend with the P4 pc that he change the cmos battery. The type is CR2032 lithium. They are about 20mm diameter and 3mm thick and cheap. (beware a CR2016 that looks the same but is thinner and lower powered) You may need to get one as well so get him to buy a CR2032 for you for peace of mind. 

What happens is the cmos (volatile memory like ram) reads the bios chip (an eprom that the system cannot change easily) at start up (initial power up). If there are any major differences the cmos will reload the data from the bios chip. The cpu then reads the information from the cmos and off it goes to fetch the bootloader. If the information from the bios chip is defective the cmos can correct it to a degree and the system still runs. The cmos is powered by the CR2032 battery when all other power is off. So when you switch off at the mains, a tired battery can lose it's settings and the whole process of reading the bios, correcting for errors (causing instability) and then booting up afresh when you hard restart with the pc button, happens each time you start up from a complete power down. When you hard restart, the cmos stays alive for the relatively short time the restart takes, when you turn the pc off at the mains the cmos fades over time depending upon how weak the battery is, which appears to be around an hour in your case. The time staying good could be that it is syncing with an Internet time server before you get to see it.

While you are in the box just make sure all connections look good as CatKiller suggests.

This is just another step to take to eliminate possible problem areas. If having reset the bios and changed the battery the problem persists, then we should next look at the Xserver. It's good fun really if you can afford the learning curve time!:)

---

### Post by mvalviar on 2008-12-01
I opened up the box yesterday with the help of my friend. Basically we just dusted the box and pressed everything firm on their sockets. And my box worked flawlessly this morning.

Thank you very much to all of you. I'll observe my box in a couple more days before I tag this thread solved.

I really look forward to learning more about ubuntu and GNU/Linux. I actually want to set-up a computer lab for my high school alma mater running on GNU/Linux because I hate the idea of kids being taught that the whole computing world is about window$ and micro$oft. I'll appreciate it if you guys can tell things I need to learn and I need to prepare in order to accomplish this.

My sincerest thanks to all of you.

---

### Post by bwallum on 2008-12-02
Yahoooooo! Well done, and well called CatKiller.

Good luck with spreading the word!

---

