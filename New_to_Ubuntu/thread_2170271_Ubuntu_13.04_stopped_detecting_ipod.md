---
title: "Ubuntu 13.04 stopped detecting ipod"
date: 2013-08-25
forum: New to Ubuntu
---

### Post by fiveeyed on 2013-08-25
I have a 5th gen 160gb Ipod classic and have been using it with banshee with no problems so far. However today when I pluged the ipod in it was not detected. I ran lsusb -v -s bus:device an got the following:

```
Bus 003 Device 010: ID 05ac:1261 Apple, Inc. iPod Classic
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x05ac Apple, Inc.
  idProduct          0x1261 iPod Classic
  bcdDevice            0.01
  iManufacturer           1 Apple Inc.
  iProduct                2 iPod
  iSerial                 3 000A2700213AE2A6
  bNumConfigurations      2
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
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
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          149
    bNumInterfaces          3
    bConfigurationValue     2
    iConfiguration          4 iPod USB Interface
    bmAttributes         0xc0
      Self Powered
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      1 Control Device
      bInterfaceProtocol      0 
      iInterface              0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdADC               1.00
        wTotalLength           30
        bInCollection           1
        baInterfaceNr( 0)       1
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Microphone
        bAssocTerminal          2
        bNrChannels             2
        wChannelConfig     0x0003
          Left Front (L)
          Right Front (R)
        iChannelNames           0 
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             2
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          1
        bSourceID               1
        iTerminal               0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           2
        bDelay                  1 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                35
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             2
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            9 Discrete
        tSamFreq[ 0]         8000
        tSamFreq[ 1]        11025
        tSamFreq[ 2]        12000
        tSamFreq[ 3]        16000
        tSamFreq[ 4]        22050
        tSamFreq[ 5]        24000
        tSamFreq[ 6]        32000
        tSamFreq[ 7]        44100
        tSamFreq[ 8]        48000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x00c0  1x 192 bytes
        bInterval               4
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x01
            Sampling Frequency
          bLockDelayUnits         0 Undefined
          wLockDelay              0 Undefined
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.01
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     208
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      2
Device Status:     0x0000
  (Bus Powered)
```
Any suggestions are greatly appreciated.

---

### Post by sddmrc on 2013-08-29
I also have a 5th gen iPod Classic 160gb and have been experiencing the same issue with 13.04 for about a week now. I have also noticed that if I leave the iPod plugged in, it eventually shows up after a few minutes. After that it works as normal. Does this workaround work for you?

---

### Post by tgalati4 on 2013-08-29
Open a terminal, plug in the iPod with a USB cable then:

```
dmesg | tail -50
```

Cut and paste the iPod stuff.

---

### Post by sicco1 on 2013-09-01
I think I have the same problem. On two 13.04 laptops my 3rd generation iPod Nano is only detected 6-7 minutes after it is plugged in. This problem didn't occur in 12.04, before upgrading.

Here is my output of syslog for the first laptop:

```
Sep  2 00:11:35 Lenovo-Ubuntu kernel: [  155.431706] usb 3-4: new high-speed USB device number 3 using xhci_hcd
Sep  2 00:11:35 Lenovo-Ubuntu kernel: [  155.448781] usb 3-4: New USB device found, idVendor=05ac, idProduct=1262
Sep  2 00:11:35 Lenovo-Ubuntu kernel: [  155.448788] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep  2 00:11:35 Lenovo-Ubuntu kernel: [  155.448792] usb 3-4: Product: iPod
Sep  2 00:11:35 Lenovo-Ubuntu kernel: [  155.448795] usb 3-4: Manufacturer: Apple Inc.
Sep  2 00:11:35 Lenovo-Ubuntu kernel: [  155.448798] usb 3-4: SerialNumber: 000A27001B274D2B
Sep  2 00:11:35 Lenovo-Ubuntu mtp-probe: checking bus 3, device 3: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-4"
Sep  2 00:11:35 Lenovo-Ubuntu mtp-probe: bus: 3, device: 3 was not an MTP device
Sep  2 00:11:35 Lenovo-Ubuntu kernel: [  155.490595] Initializing USB Mass Storage driver...
Sep  2 00:11:35 Lenovo-Ubuntu kernel: [  155.490882] scsi6 : usb-storage 3-4:1.0
Sep  2 00:11:35 Lenovo-Ubuntu kernel: [  155.491003] usbcore: registered new interface driver usb-storage
Sep  2 00:11:35 Lenovo-Ubuntu kernel: [  155.491006] USB Mass Storage support registered.
Sep  2 00:11:36 Lenovo-Ubuntu kernel: [  156.501908] scsi 6:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Sep  2 00:11:36 Lenovo-Ubuntu kernel: [  156.503564] sd 6:0:0:0: Attached scsi generic sg3 type 0
Sep  2 00:11:36 Lenovo-Ubuntu kernel: [  156.507116] sd 6:0:0:0: [sdc] Spinning up disk...
Sep  2 00:11:38 Lenovo-Ubuntu kernel: [  158.393313] .ready
Sep  2 00:11:38 Lenovo-Ubuntu kernel: [  158.394139] sd 6:0:0:0: [sdc] 950209 4096-byte logical blocks: (3.89 GB/3.62 GiB)
Sep  2 00:11:38 Lenovo-Ubuntu kernel: [  158.394648] sd 6:0:0:0: [sdc] Write Protect is off
Sep  2 00:11:38 Lenovo-Ubuntu kernel: [  158.394656] sd 6:0:0:0: [sdc] Mode Sense: 68 00 00 08
Sep  2 00:11:38 Lenovo-Ubuntu kernel: [  158.395099] sd 6:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Sep  2 00:12:02 Lenovo-Ubuntu dbus[952]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Sep  2 00:12:02 Lenovo-Ubuntu dbus[952]: [system] Successfully activated service 'org.freedesktop.hostname1'
Sep  2 00:12:09 Lenovo-Ubuntu kernel: [  188.801528] usb 3-4: reset high-speed USB device number 3 using xhci_hcd
Sep  2 00:12:09 Lenovo-Ubuntu kernel: [  188.818047] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c0de31c0
Sep  2 00:12:09 Lenovo-Ubuntu kernel: [  188.818055] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c0de3180
Sep  2 00:12:40 Lenovo-Ubuntu kernel: [  219.816899] usb 3-4: reset high-speed USB device number 3 using xhci_hcd
Sep  2 00:12:40 Lenovo-Ubuntu kernel: [  219.833413] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c0de31c0
Sep  2 00:12:40 Lenovo-Ubuntu kernel: [  219.833422] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c0de3180
Sep  2 00:13:11 Lenovo-Ubuntu kernel: [  250.768345] usb 3-4: reset high-speed USB device number 3 using xhci_hcd
Sep  2 00:13:11 Lenovo-Ubuntu kernel: [  250.785000] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c0de31c0
Sep  2 00:13:11 Lenovo-Ubuntu kernel: [  250.785008] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c0de3180
Sep  2 00:13:42 Lenovo-Ubuntu kernel: [  281.719808] usb 3-4: reset high-speed USB device number 3 using xhci_hcd
Sep  2 00:13:42 Lenovo-Ubuntu kernel: [  281.736369] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c0de31c0
Sep  2 00:13:42 Lenovo-Ubuntu kernel: [  281.736377] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c0de3180
Sep  2 00:13:42 Lenovo-Ubuntu kernel: [  281.765255] sd 6:0:0:0: [sdc] 950209 4096-byte logical blocks: (3.89 GB/3.62 GiB)
Sep  2 00:14:13 Lenovo-Ubuntu kernel: [  312.671256] usb 3-4: reset high-speed USB device number 3 using xhci_hcd
Sep  2 00:14:13 Lenovo-Ubuntu kernel: [  312.687733] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c0de31c0
Sep  2 00:14:13 Lenovo-Ubuntu kernel: [  312.687742] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c0de3180
Sep  2 00:14:44 Lenovo-Ubuntu kernel: [  343.686661] usb 3-4: reset high-speed USB device number 3 using xhci_hcd
Sep  2 00:14:44 Lenovo-Ubuntu kernel: [  343.703185] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c0de31c0
Sep  2 00:14:44 Lenovo-Ubuntu kernel: [  343.703194] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c0de3180
Sep  2 00:15:15 Lenovo-Ubuntu kernel: [  374.701985] usb 3-4: reset high-speed USB device number 3 using xhci_hcd
Sep  2 00:15:15 Lenovo-Ubuntu kernel: [  374.718577] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c0de31c0
Sep  2 00:15:15 Lenovo-Ubuntu kernel: [  374.718585] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c0de3180
Sep  2 00:15:46 Lenovo-Ubuntu kernel: [  405.653523] usb 3-4: reset high-speed USB device number 3 using xhci_hcd
Sep  2 00:15:46 Lenovo-Ubuntu kernel: [  405.669944] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c0de31c0
Sep  2 00:15:46 Lenovo-Ubuntu kernel: [  405.669953] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c0de3180
Sep  2 00:15:46 Lenovo-Ubuntu kernel: [  405.698974]  sdc: sdc1
Sep  2 00:15:46 Lenovo-Ubuntu kernel: [  405.700218] sd 6:0:0:0: [sdc] 950209 4096-byte logical blocks: (3.89 GB/3.62 GiB)
Sep  2 00:16:17 Lenovo-Ubuntu kernel: [  436.604947] usb 3-4: reset high-speed USB device number 3 using xhci_hcd
Sep  2 00:16:17 Lenovo-Ubuntu kernel: [  436.621462] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c0de31c0
Sep  2 00:16:17 Lenovo-Ubuntu kernel: [  436.621471] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c0de3180
Sep  2 00:16:47 Lenovo-Ubuntu udevd[2564]: timeout '/sbin/blkid -o udev -p /dev/sdc'
Sep  2 00:16:48 Lenovo-Ubuntu kernel: [  467.684322] usb 3-4: reset high-speed USB device number 3 using xhci_hcd
Sep  2 00:16:48 Lenovo-Ubuntu kernel: [  467.700800] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c0de31c0
Sep  2 00:16:48 Lenovo-Ubuntu kernel: [  467.700809] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c0de3180
Sep  2 00:16:48 Lenovo-Ubuntu udevd[2564]: timeout: killing '/sbin/blkid -o udev -p /dev/sdc' [2583]
Sep  2 00:17:01  udevd[2564]: last message repeated 13 times
Sep  2 00:17:01 Lenovo-Ubuntu CRON[2586]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  2 00:17:02 Lenovo-Ubuntu udevd[2564]: timeout: killing '/sbin/blkid -o udev -p /dev/sdc' [2583]
Sep  2 00:17:19  udevd[2564]: last message repeated 16 times
Sep  2 00:17:19 Lenovo-Ubuntu kernel: [  498.635754] usb 3-4: reset high-speed USB device number 3 using xhci_hcd
Sep  2 00:17:19 Lenovo-Ubuntu kernel: [  498.652252] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c0de31c0
Sep  2 00:17:19 Lenovo-Ubuntu kernel: [  498.652261] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c0de3180
Sep  2 00:17:19 Lenovo-Ubuntu udevd[2564]: timeout: killing '/sbin/blkid -o udev -p /dev/sdc' [2583]
Sep  2 00:17:50  udevd[2564]: last message repeated 30 times
Sep  2 00:17:50 Lenovo-Ubuntu kernel: [  529.587220] usb 3-4: reset high-speed USB device number 3 using xhci_hcd
Sep  2 00:17:50 Lenovo-Ubuntu kernel: [  529.603767] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c0de31c0
Sep  2 00:17:50 Lenovo-Ubuntu kernel: [  529.603776] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800c0de3180
Sep  2 00:17:50 Lenovo-Ubuntu udevd[2564]: '/sbin/blkid -o udev -p /dev/sdc' [2583] terminated by signal 9 (Killed)
Sep  2 00:17:50 Lenovo-Ubuntu udevd[2564]: timeout 'udisks-part-id /dev/sdc'
Sep  2 00:17:50 Lenovo-Ubuntu kernel: [  529.630951] sd 6:0:0:0: [sdc] Attached SCSI removable disk
Sep  2 00:17:51 Lenovo-Ubuntu udisksd[2074]: Mounted /dev/sdc1 at /media/laura/IPOD on behalf of uid 1000
```

And the output of syslog for the second laptop:

```
Sep  1 23:57:36 laptop-ubuntu kernel: [71723.988303] usb 3-1: new high-speed USB device number 4 using xhci_hcd
Sep  1 23:57:36 laptop-ubuntu kernel: [71724.074259] usb 3-1: New USB device found, idVendor=05ac, idProduct=1262
Sep  1 23:57:36 laptop-ubuntu kernel: [71724.074270] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep  1 23:57:36 laptop-ubuntu kernel: [71724.074276] usb 3-1: Product: iPod
Sep  1 23:57:36 laptop-ubuntu kernel: [71724.074282] usb 3-1: Manufacturer: Apple Inc.
Sep  1 23:57:36 laptop-ubuntu kernel: [71724.074286] usb 3-1: SerialNumber: 000A27001B274D2B
Sep  1 23:57:36 laptop-ubuntu kernel: [71724.117539] scsi31 : usb-storage 3-1:1.0
Sep  1 23:57:36 laptop-ubuntu mtp-probe: checking bus 3, device 4: "/sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.0/usb3/3-1"
Sep  1 23:57:36 laptop-ubuntu mtp-probe: bus: 3, device: 4 was not an MTP device
Sep  1 23:57:37 laptop-ubuntu kernel: [71725.162723] scsi 31:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Sep  1 23:57:37 laptop-ubuntu kernel: [71725.164567] sd 31:0:0:0: Attached scsi generic sg2 type 0
Sep  1 23:57:37 laptop-ubuntu kernel: [71725.165703] sd 31:0:0:0: [sdb] Spinning up disk...
Sep  1 23:57:39 laptop-ubuntu kernel: [71726.972953] .ready
Sep  1 23:57:39 laptop-ubuntu kernel: [71726.973834] sd 31:0:0:0: [sdb] 950209 4096-byte logical blocks: (3.89 GB/3.62 GiB)
Sep  1 23:57:39 laptop-ubuntu kernel: [71726.974413] sd 31:0:0:0: [sdb] Write Protect is off
Sep  1 23:57:39 laptop-ubuntu kernel: [71726.974424] sd 31:0:0:0: [sdb] Mode Sense: 68 00 00 08
Sep  1 23:57:39 laptop-ubuntu kernel: [71726.974968] sd 31:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Sep  1 23:58:10 laptop-ubuntu kernel: [71757.583617] usb 3-1: reset high-speed USB device number 4 using xhci_hcd
Sep  1 23:58:10 laptop-ubuntu kernel: [71757.600189] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88018edcde40
Sep  1 23:58:10 laptop-ubuntu kernel: [71757.600201] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88018edcde00
Sep  1 23:58:41 laptop-ubuntu kernel: [71788.589555] usb 3-1: reset high-speed USB device number 4 using xhci_hcd
Sep  1 23:58:41 laptop-ubuntu kernel: [71788.606142] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88018edcde40
Sep  1 23:58:41 laptop-ubuntu kernel: [71788.606154] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88018edcde00
Sep  1 23:59:12 laptop-ubuntu kernel: [71819.531506] usb 3-1: reset high-speed USB device number 4 using xhci_hcd
Sep  1 23:59:12 laptop-ubuntu kernel: [71819.548245] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88018edcde40
Sep  1 23:59:12 laptop-ubuntu kernel: [71819.548257] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88018edcde00
Sep  1 23:59:43 laptop-ubuntu kernel: [71850.473716] usb 3-1: reset high-speed USB device number 4 using xhci_hcd
Sep  1 23:59:43 laptop-ubuntu kernel: [71850.490108] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88018edcde40
Sep  1 23:59:43 laptop-ubuntu kernel: [71850.490119] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88018edcde00
Sep  1 23:59:43 laptop-ubuntu kernel: [71850.569485] sd 31:0:0:0: [sdb] 950209 4096-byte logical blocks: (3.89 GB/3.62 GiB)
Sep  2 00:00:14 laptop-ubuntu kernel: [71881.479660] usb 3-1: reset high-speed USB device number 4 using xhci_hcd
Sep  2 00:00:14 laptop-ubuntu kernel: [71881.496099] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88018edcde40
Sep  2 00:00:14 laptop-ubuntu kernel: [71881.496110] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88018edcde00
Sep  2 00:00:45 laptop-ubuntu kernel: [71912.485502] usb 3-1: reset high-speed USB device number 4 using xhci_hcd
Sep  2 00:00:45 laptop-ubuntu kernel: [71912.502097] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88018edcde40
Sep  2 00:00:45 laptop-ubuntu kernel: [71912.502109] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88018edcde00
Sep  2 00:01:16 laptop-ubuntu kernel: [71943.427628] usb 3-1: reset high-speed USB device number 4 using xhci_hcd
Sep  2 00:01:16 laptop-ubuntu kernel: [71943.444138] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88018edcde40
Sep  2 00:01:16 laptop-ubuntu kernel: [71943.444150] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88018edcde00
Sep  2 00:01:47 laptop-ubuntu kernel: [71974.369551] usb 3-1: reset high-speed USB device number 4 using xhci_hcd
Sep  2 00:01:47 laptop-ubuntu kernel: [71974.385936] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88018edcde40
Sep  2 00:01:47 laptop-ubuntu kernel: [71974.385953] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88018edcde00
Sep  2 00:01:47 laptop-ubuntu kernel: [71974.467120]  sdb: sdb1
Sep  2 00:01:47 laptop-ubuntu kernel: [71974.468634] sd 31:0:0:0: [sdb] 950209 4096-byte logical blocks: (3.89 GB/3.62 GiB)
Sep  2 00:02:18 laptop-ubuntu kernel: [72005.311546] usb 3-1: reset high-speed USB device number 4 using xhci_hcd
Sep  2 00:02:18 laptop-ubuntu kernel: [72005.328227] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88018edcde40
Sep  2 00:02:18 laptop-ubuntu kernel: [72005.328238] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88018edcde00
Sep  2 00:02:48 laptop-ubuntu udevd[12407]: timeout '/sbin/blkid -o udev -p /dev/sdb'
Sep  2 00:02:49 laptop-ubuntu kernel: [72036.381351] usb 3-1: reset high-speed USB device number 4 using xhci_hcd
Sep  2 00:02:49 laptop-ubuntu kernel: [72036.398100] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88018edcde40
Sep  2 00:02:49 laptop-ubuntu kernel: [72036.398112] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88018edcde00
Sep  2 00:02:49 laptop-ubuntu udevd[12407]: timeout: killing '/sbin/blkid -o udev -p /dev/sdb' [12414]
Sep  2 00:03:20  udevd[12407]: last message repeated 30 times
Sep  2 00:03:20 laptop-ubuntu kernel: [72067.323314] usb 3-1: reset high-speed USB device number 4 using xhci_hcd
Sep  2 00:03:20 laptop-ubuntu kernel: [72067.340020] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88018edcde40
Sep  2 00:03:20 laptop-ubuntu kernel: [72067.340032] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88018edcde00
Sep  2 00:03:20 laptop-ubuntu udevd[12407]: timeout: killing '/sbin/blkid -o udev -p /dev/sdb' [12414]
Sep  2 00:03:51  udevd[12407]: last message repeated 30 times
Sep  2 00:03:51 laptop-ubuntu kernel: [72098.265466] usb 3-1: reset high-speed USB device number 4 using xhci_hcd
Sep  2 00:03:51 laptop-ubuntu kernel: [72098.282061] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88018edcde40
Sep  2 00:03:51 laptop-ubuntu kernel: [72098.282073] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88018edcde00
Sep  2 00:03:51 laptop-ubuntu udevd[12407]: '/sbin/blkid -o udev -p /dev/sdb' [12414] terminated by signal 9 (Killed)
Sep  2 00:03:51 laptop-ubuntu udevd[12407]: timeout 'udisks-part-id /dev/sdb'
Sep  2 00:03:51 laptop-ubuntu kernel: [72098.353234] sd 31:0:0:0: [sdb] Attached SCSI removable disk

```

Should I file a bug? If so, where (libgpod?)?

---

### Post by Prodoc on 2013-09-04
I ran into the same problem. Apparently it's a linux kernel issue. It is fixed in 3.8.0-30.44+. The updated kernel should be available in the next few days as an update.

If you can't wait you can enable the pre-released updates channel by:
[LIST]
[*]Going to the "Software & Updates" application
[*]Go to the "Updates" tab
[*]Check "Pre-released updates (raring-proposed)"
[*]Launch the "Software Updater" application
[/LIST]
Either update all available updates (note that they might not be final), or uncheck all but the linux kernel update to version 3.8.0-30.48 (as of today).

You might want to uncheck the  "Pre-released updates (raring-proposed)" channel again afterwards to prevent getting premature updates in the future.

---

### Post by sicco1 on 2013-09-04
Excellent. The new kernel fixed the problem, thanks! Was there a launchpad report for this bug? If so, could you link to it?

---

### Post by Prodoc on 2013-09-04
> **sicco1 said:**
> Excellent. The new kernel fixed the problem, thanks! Was there a launchpad report for this bug? If so, could you link to it?
I don't know about a launchpad report. I got the fix [from a different forum post](http://ubuntuforums.org/showthread.php?t=2169849&p=12767259#post12767259) myself, but decided to reply here with some proper steps to fix it because this topic title is more appropriate and more likely to be found by others.

---

### Post by sicco1 on 2013-09-04
Thanks. The bug report is here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1215155](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1215155)

---

