---
title: "does USB work in linux or not?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by wec123 on 2008-04-28
new post, same old story. ubuntu doesnt recognize my usb. worked fine in windows. i have an msi motherboard which from what ive read should be supported in ubuntu. i really dont know what to do, it seems like everybody on these forums has this problem and ive spent weeks going through different threads trying different things and nothing works. i waited on 8.04 hoping it would start working but it dont. lsusb gives:

Bus 003 Device 001: 0000:0000
Bus 002 Device 001: 0000:0000
Bus 001 Device 001: 0000:0000

---

### Post by steve-shinn on 2008-04-28
What device are you connecting to the USB port ?

---

### Post by wec123 on 2008-04-28
a netgear WG111v2 wireless adapter is the only essential device i need to get working but no usb device works ive tried everything i got.

---

### Post by Michael.Godawski on 2008-04-28
Perhaps your device is just not supported by Ubuntu. For instance a wlan dongle. it would be good to know what you are trying to plug in.

---

### Post by Michael.Godawski on 2008-04-28
Perhaps you have to install the drivers via ndiswrapper for your wlan to work:
[https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111?highlight=%28WifiDocs%2FDevice%29)

---

### Post by Tatty on 2008-04-28
Im very surprised that your device is not showing up under lsusb.  Try plugging your device into another USB port, wait about 10 seconds then try lsusb again

**Edit: **Also try ```
lshw -C network
```

---

### Post by stalkingwolf on 2008-04-28
My WG 111v2 works fine out of the box.  as do my toshiba thumb drives and several Noname USB wifi adapters I have.  They all
work on all the Ubuntu systems I have tried them on.  My external
USB HDD cases also work.  I have never had a problem with USB in UBUNTU.:-k

---

### Post by wec123 on 2008-04-28
i dod the lshw -c network thing. not sure what to look for in the response. i cant exactly copy and paste cuz im on the forum here on my friends xp computer while working on my own computer that cant go on the internet cuz of this problem. ive tried the ndiswrapper thing before and it didnt work. i aprreciate all the help but i really dont think the problem is a network thing its has to be strictly a usb issue because nothing i plug in works at all but the devices do get power so it works. i should also mention that during bootup it says something like "over-current change on usb port"

---

### Post by Tatty on 2008-04-28
lshw lists the hardware in your computer, so it would be helpful if you could somehow copy the results and paste them in here.  It might not yeild any results but it is the next logical step.

---

### Post by JohnFH on 2008-04-28
That message means your motherboard is shutting down the USB ports.  What is your hardware configuration?  Or more to the point, how has it changed?  

Use 'lsusb -v' to get more detailed info.

Try unplugging all USB devices then reboot.  Do you get the same message?  What happens now when you plug in a USB device?

---

### Post by SlappyPappy on 2008-04-28
Sounds like a defective motherboard or a short, something touching that should not be touching.

---

### Post by wec123 on 2008-04-28
ok ive tried everything everybodys mentioned and still nothing

**lshw -c network gives me this:**

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

william@william-desktop:~$ lshw businfo
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

**lshw -businfo gives me this:**

WARNING: you should run this program as super-user.
Bus info          Device  Class          Description
====================================================
                          system         Computer
                          bus            Motherboard
                          memory         511MiB System memory
cpu@0                     processor      AMD Athlon(tm) XP 3000+
                          memory         128KiB L1 cache
                          memory         512KiB L2 cache
pci@0000:00:00.0          bridge         nForce2 IGP2
pci@0000:00:00.1          memory         RAM memory
pci@0000:00:00.2          memory         RAM memory
pci@0000:00:00.3          memory         RAM memory
pci@0000:00:00.4          memory         RAM memory
pci@0000:00:00.5          memory         RAM memory
pci@0000:00:01.0          bridge         nForce2 ISA Bridge
pci@0000:00:01.1          bus            nForce2 SMBus (MCP)
pci@0000:00:02.0          bus            nForce2 USB Controller
pci@0000:00:02.1          bus            nForce2 USB Controller
pci@0000:00:02.2          bus            nForce2 USB Controller
pci@0000:00:04.0  eth0    network        nForce2 Ethernet Controller
pci@0000:00:06.0          multimedia     nForce2 AC97 Audio Controler (MCP)
pci@0000:00:08.0          bridge         nForce2 External PCI Bridge
pci@0000:01:09.0          communication  HSF 56k HSFi Modem
pci@0000:00:09.0          storage        nForce2 IDE
pci@0000:00:1e.0          bridge         nForce2 AGP
pci@0000:02:00.0          display        NV34 [GeForce FX 5200]

**lsusb -v gives me this:**

Bus 003 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 002 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

---

### Post by Jeneral22 on 2008-05-03
I am having the same problem. I have four USB ports that connect my camera, WG111 (wireless stick), printer, and any usb sticks. I also have a card reader that claims it is connected via USB... The card reader works ok but the four other ports appear to be shut off. I was able to use these ports in 7.04 but they have gone away on 8.04. I am plugged directly into my router in order to connect to the internet. All ports worked fine in XP which I still have installed on a different hard drive. I believe that Hardy is turning off USB support on the motherboard.

Thanks for your thoughts and ideas. This isn't the only post on this issue so perhaps there are problems with certain motherboards.

---

