---
title: "noob needs help plzz"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by c4n0fcorn on 2008-09-09
hello all

I am new to Linux and have a problem. I just updated my system with the update manger and now my kernel 19 thing wont boot it freezes at a black screen and it just says starting up... at the top of the screen,
thus i need some help please thanks.

---

### Post by c4n0fcorn on 2008-09-09
Hey all i am hoping someone can help me out with this i have a laptop running a dual boot vista and ubuntu hardy i would like to move deeper into my hardy system but I would like to keep vista for gaming so is it possible to make more room by deleting more windows apts?

---

### Post by overdrank on 2008-09-09
Hi and please do not make multiple threads on the same issue. I have merged and moved the thread to ABT. :)
Are you able to boot into recovery mode or any other kernel from the grub? Could you give us some system specs? that may help us.

---

### Post by c4n0fcorn on 2008-09-09
sorry i didn't mean to make multiples..

but it works if i boot it in kernel 16 thats what i am one right now  but not the kernel 19. I think its 2.6.24-19 or something??

---

### Post by c4n0fcorn on 2008-09-09
sorry i don't really know what kind of computer this. i run Ubuntu on my lap top and have not had any issues i am really new at this and am i little lost.

---

### Post by billgoldberg on 2008-09-09
If you installed your graphics card driver using Envy, you must remove it before upgrading to a new kernel and then reinstall it again.

I don't know if this applies to manual driver installs. 

If you installed it using "hardware drivers", this isn't an issue.

--

Just letting you know as this seems like an graphics card issue.

--

Edit: should have read it better. It most likely isn't an graphics card issue.

---

### Post by Gonz_91 on 2008-09-09
Huh.. Recovery mode, maybe?

---

### Post by c4n0fcorn on 2008-09-09
no recovery did the same i just sits there being mean..:( cant anyone help..

---

### Post by SteveNorman on 2008-09-09
please post the output of:
[HTML]$ lshw[/HTML]

---

### Post by Gonz_91 on 2008-09-09
In that case... beats me.
Maybe someone more experienced can help

Sry :(

---

### Post by c4n0fcorn on 2008-09-09
thats ok thnks for trying

---

### Post by hyper_ch on 2008-09-09
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by overdrank on 2008-09-09
> **hyper_ch said:**
> It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)


You are correct and I take full responsibility as I merged and moved the thread to the ABT and should have changed the title. :oops:

---

### Post by c4n0fcorn on 2008-09-10
well live and learn i guess.

speaking of myself.

---

### Post by hyper_ch on 2008-09-10
*edit*

---

### Post by c4n0fcorn on 2008-09-10
> **SteveNorman said:**
> please post the output of:
[HTML]$ lshw[/HTML]
this is what came up when i out in  $ lsgw


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
          product: Intel(R) Celeron(R) D CPU 3.33GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.6.5
          serial: 0000-0F65-0000-0000-0000-0000
          size: 18EHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc up pebs bts sync_rdtsc pni monitor ds_cpl cid cx16 xtpr lahf_lm
          configuration: id=0
     *-pci:0
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8237 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NV5 [RIVA TNT2/TNT2 Pro]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 11
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list
                configuration: latency=64 maxlatency=1 mingnt=5
        *-network:0
             description: Ethernet interface
             product: RTL-8169 Gigabit Ethernet
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 8
             bus info: pci@0000:00:08.0
             logical name: eth0
             version: 10
             serial: 00:80:5a:67:c6:e6
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes
        *-ide:0
             description: IDE interface
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_via latency=64 module=sata_via
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_via latency=32 module=pata_via
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-network:1
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth1
             version: 78
             serial: 00:16:ec:f2:14:5e
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.57.131 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
     *-pci:1
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: PT890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz

---

