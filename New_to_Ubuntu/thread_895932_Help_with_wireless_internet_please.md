---
title: "Help with wireless internet please"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by AnonUK on 2008-08-20
Hey, I can't get my wireless internet to work on ubuntu

network manager does not recognise the wireless internet at all.

I downloaded build-essential_11.1_i386.deb on vista, transfered it to ubuntu and installed it there. I then typed the command 'sudo dpkg -i *.deb' into the terminal and recieved this message 

root@anonymous-desktop:~# sudo dpkg -i *.deb 
dpkg: error processing *.deb (--install): 
 cannot access archive: No such file or directory 
Errors were encountered while processing: 
 *.deb 


running  iwconfig produced no positive results either. 

Please help

---

### Post by caljohnsmith on 2008-08-20
> **AnonUK said:**
> 
root@anonymous-desktop:~# sudo dpkg -i *.deb 
dpkg: error processing *.deb (--install): 
[COLOR="Blue"] cannot access archive: No such file or directory [/COLOR]
Errors were encountered while processing: 
 *.deb 

When you run the dpkg command, you have to either be in the same directory as the package you want to install, or you need to give the path to the package:
```
sudo dpkg -i /path/*.deb
```
You ran that command while you were logged in as root, so it looks like you were in the /root directory at the time; I doubt that's where you put the .deb package you want to install. :)

---

### Post by spiderbatdad on 2008-08-20
build-essential is in synaptic package manager. Open the package manager to install, or```
sudo apt-get install build-essential
```

If the *.deb you were trying to install was on your desktop, there is a chance it failed to find the package because you were not working from the desktop. First change directory to the desktop:```
cd Desktop
```note the capital "D." Then run commands.

Edit: if you have already installed a version of build-essential no need to change...I misunderstood. Thought build-essential was the .deb you were having trouble installing.

---

### Post by caljohnsmith on 2008-08-20
With all due respect, spiderbatdad, I think AnonUK is trying to install that package manually because he mentioned that:
> I can't get my wireless internet to work on ubuntu
network manager does not recognise the wireless internet at all.
I don't think he has internet access in Ubuntu yet. :)

---

### Post by AnonUK on 2008-08-20
hey guys.

I tried typing the command again and it worked (...i think)

anonymous@anonymous-desktop:~/Desktop$ sudo dpkg -i *.deb 
(Reading database ... 110409 files and directories currently installed.) 
Preparing to replace build-essential 11.1 (using build-essential_11.1_i386.deb) ... 
Unpacking replacement build-essential ... 
Setting up build-essential (11.1) ... 

What do i do now?

thanks for the help

---

### Post by cdtech on 2008-08-20
What procedures are you using to get the wireless to work?

---

### Post by AnonUK on 2008-08-20
I have only tried what i've wrote about so far in this thread. I found out about the .deb package from reading threads written by other people concerning their troubles with wireless.

---

### Post by spiderbatdad on 2008-08-20
we need to know what wireless card you have. ```
sudo lshw -C net
```and post the output here. Do you have a wired connection for internet on Ubuntu?

---

### Post by AnonUK on 2008-08-20
anonymous@anonymous-desktop:~$ sudo lshw -C net 
[sudo] password for anonymous: 
  *-network               
       description: Ethernet interface 
       product: VT6102 [Rhine-II] 
       vendor: VIA Technologies, Inc. 
       physical id: 12 
       bus info: pci@0000:00:12.0 
       logical name: eth0 
       version: 7c 
       serial: 00:19:db:43:22:de 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s



edit: Nope, i don't have a wired connection

---

### Post by spiderbatdad on 2008-08-20
so what kind of wirelss interface are we talking about? That hardware list only shows the ethernet card...no wireless card. Was there more, like: ```
 *-network:0 DISABLED    
       description: Wireless interface

```or *-network:1...?
According to the above, you don't have a wireless card.

---

### Post by caljohnsmith on 2008-08-20
Do you have a wireless USB device instead of PCI card? If so run:
```
lsusb
```
But if you have a wireless PCI card, post the output of:
```
lspci
```

---

### Post by AnonUK on 2008-08-20
hey i did both because i'm not sure -

anonymous@anonymous-desktop:~$ lsusb 
Bus 005 Device 003: ID 050d:815c Belkin Components 
Bus 005 Device 002: ID 04e8:0111 Samsung Electronics Co., Ltd Connect3D Flash Drive 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

anonymous@anonymous-desktop:~$ lspci 
00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge 
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge 
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge 
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge 
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge 
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller 
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device 
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge 
00:01.0 PCI bridge: VIA Technologies, Inc. [K8T890 North / VT8237 South] PCI Bridge 
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller 
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller 
00:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) 
00:0a.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1) 
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80) 
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07) 
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) 
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) 
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) 
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) 
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) 
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge 
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller 
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c) 
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge 
02:00.0 VGA compatible controller: ATI Technologies Inc RV516 XT Radeon X1600 Series (Primary) 
02:00.1 Display controller: ATI Technologies Inc RV516 XT Radeon X1600 Series (Secondary) 
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10) 
anonymous@anonymous-desktop:~$ 

and then i tried this command again and got the same result -


anonymous@anonymous-desktop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions.

---

### Post by caljohnsmith on 2008-08-20
From your lspci output it doesn't look like you have a wireless card. The lsusb output shows "Belkin Components", so is that your wireless device? If you have a wireless card, it is located inside your computer. Or do you have a Belkin wireless adapter plugged into one of your USB ports?

---

### Post by AnonUK on 2008-08-20
> **caljohnsmith said:**
> From your lspci output it doesn't look like you have a wireless card. The lsusb output shows "Belkin Components", so is that your wireless device? If you have a wireless card, it is located inside your computer. Or do you have a Belkin wireless adapter plugged into one of your USB ports?

Oh right, I have a belkin wireless adapter yeh

---

### Post by caljohnsmith on 2008-08-20
Try:
```
lsusb -v
```
And post the results.

---

### Post by cdtech on 2008-08-20
"lshw" will show all of the hardware installed on your computer but I don't see a PCI device for wireless. The only thing I see that remotely resembles a wireless device is the USB belkin.

What wireless device are you using (name and model would help)?

---

### Post by spiderbatdad on 2008-08-20
Install ndiswrapper

Open terminal.

Remove the following drivers using these commands:

```


sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb
```

Blacklist rt2500usb and rt73usb by opening text editor as follows:

```


gksu gedit /etc/modprobe.d/blacklist

```
add "blacklist rt2500usb" and "blacklist rt73usb" (Without the quotes) to end of list, save and close.

REBOOT

Blacklist doesn't work until you reboot. If you don't, the wrong driver will be assigned.

From your desktop, open your home directory.  Right click in home folder and create a file called Belkin. Insert the belkin cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following (If the .inf file you copied is not the rt73, replace as appropriate below) :

```


sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf

```
Insert the wireless adapter.

Now issue the following commands:

```


sudo depmod -a
sudo modprobe ndiswrapper

```
I think these create the module. Now edit modules to load ndiswrapper when you boot as follows:

```


gksu gedit /etc/modules
```

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

```


sudo ndiswrapper -m

```
Reboot

[http://ubuntuforums.org/showthread.php?t=872368](http://ubuntuforums.org/showthread.php?t=872368)

---

### Post by AnonUK on 2008-08-20
anonymous@anonymous-desktop:~$ lsusb -v 

Bus 005 Device 003: ID 050d:815c Belkin Components 
Device Descriptor: 
  bLength                18 
  bDescriptorType         1 
  bcdUSB               2.00 
  bDeviceClass            0 (Defined at Interface level) 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64 
  idVendor           0x050d Belkin Components 
  idProduct          0x815c 
  bcdDevice            1.01 
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1 
  Configuration Descriptor: 
    bLength                 9 
    bDescriptorType         2 
    wTotalLength           53 
    bNumInterfaces          1 
    bConfigurationValue     1 
    iConfiguration          0 
    bmAttributes         0x80 
      (Bus Powered) 
    MaxPower              450mA 
    Interface Descriptor: 
      bLength                 9 
      bDescriptorType         4 
      bInterfaceNumber        0 
      bAlternateSetting       0 
      bNumEndpoints           5 
      bInterfaceClass       255 Vendor Specific Class 
      bInterfaceSubClass    255 Vendor Specific Subclass 
      bInterfaceProtocol    255 Vendor Specific Protocol 
      iInterface              5 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x81  EP 1 IN 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0200  1x 512 bytes 
        bInterval               0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x01  EP 1 OUT 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0200  1x 512 bytes 
        bInterval               0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x02  EP 2 OUT 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0200  1x 512 bytes 
        bInterval               0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x03  EP 3 OUT 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0200  1x 512 bytes 
        bInterval               0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x04  EP 4 OUT 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0200  1x 512 bytes 
        bInterval               0 
can't get device qualifier: Operation not permitted 
can't get debug descriptor: Operation not permitted 
cannot read device status, Operation not permitted (1) 

Bus 005 Device 002: ID 04e8:0111 Samsung Electronics Co., Ltd Connect3D Flash Drive 
Device Descriptor: 
  bLength                18 
  bDescriptorType         1 
  bcdUSB               2.00 
  bDeviceClass            0 (Defined at Interface level) 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64 
  idVendor           0x04e8 Samsung Electronics Co., Ltd 
  idProduct          0x0111 Connect3D Flash Drive 
  bcdDevice            2.00 
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1 
  Configuration Descriptor: 
    bLength                 9 
    bDescriptorType         2 
    wTotalLength           39 
    bNumInterfaces          1 
    bConfigurationValue     1 
    iConfiguration          0 
    bmAttributes         0x80 
      (Bus Powered) 
    MaxPower              200mA 
    Interface Descriptor: 
      bLength                 9 
      bDescriptorType         4 
      bInterfaceNumber        0 
      bAlternateSetting       0 
      bNumEndpoints           3 
      bInterfaceClass         8 Mass Storage 
      bInterfaceSubClass      6 SCSI 
      bInterfaceProtocol     80 Bulk (Zip) 
      iInterface              0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x81  EP 1 IN 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0200  1x 512 bytes 
        bInterval               0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x02  EP 2 OUT 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0200  1x 512 bytes 
        bInterval               0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x83  EP 3 IN 
        bmAttributes            3 
          Transfer Type            Interrupt 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0002  1x 2 bytes 
        bInterval               1 
can't get device qualifier: Operation not permitted 
can't get debug descriptor: Operation not permitted 
cannot read device status, Operation not permitted (1) 

Bus 005 Device 001: ID 0000:0000  
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

Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader 
Device Descriptor: 
  bLength                18 
  bDescriptorType         1 
  bcdUSB               1.10 
  bDeviceClass            0 (Defined at Interface level) 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8 
  idVendor           0x058f Alcor Micro Corp. 
  idProduct          0x9360 8-in-1 Media Card Reader 
  bcdDevice            1.00 
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1 
  Configuration Descriptor: 
    bLength                 9 
    bDescriptorType         2 
    wTotalLength           32 
    bNumInterfaces          1 
    bConfigurationValue     1 
    iConfiguration          0 
    bmAttributes         0x80 
      (Bus Powered) 
    MaxPower              100mA 
    Interface Descriptor: 
      bLength                 9 
      bDescriptorType         4 
      bInterfaceNumber        0 
      bAlternateSetting       0 
      bNumEndpoints           2 
      bInterfaceClass         8 Mass Storage 
      bInterfaceSubClass      6 SCSI 
      bInterfaceProtocol     80 Bulk (Zip) 
      iInterface              0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x01  EP 1 OUT 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0040  1x 64 bytes 
        bInterval               0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x82  EP 2 IN 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0040  1x 64 bytes 
        bInterval               0 
cannot read device status, Operation not permitted (1) 

Bus 004 Device 001: ID 0000:0000  
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

Bus 003 Device 001: ID 0000:0000  
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

