---
title: "One out of two USB ports isn't working"
date: 2013-04-11
forum: New to Ubuntu
---

### Post by iamtristan on 2013-04-11
Hi there,

I am very new to Ubuntu, so please excuse if this a trivial question.

I installed Ubuntu 12.10 64Bit successfully (after fighting a great amount of time with uefi and win8...) on my Sony Vaio SVT1312XES.
I managed everything to work except for the second USB port.

This is the situation:

[IMG]http://oi47.tinypic.com/2j3ige0.jpg[/IMG]

I tested several pendrives, mices and other USB-equipment.


The working USB port, should be ready for USB 3, but i couldn't verify this because i don't own any USB 3 device.
But with USB 2 it works great.

I have no idea at all how to start to fix this issue.

I am very thankful for any help.
Thanks.

---

### Post by zrdc28 on 2013-04-12
The next time you start it up go into setup and make sure all usb ports are enabled .

---

### Post by iamtristan on 2013-04-12
allright thank you.
will try this.

but how do i enter the setup?

---

### Post by schragge on 2013-04-12
Have a look at [this answer]("http://superuser.com/a/503319").

---

### Post by iamtristan on 2013-04-12
ok, i thought he was talking about some kind of ubuntu setup.

in the sony-setup i can't find a option about usb ports.
and if i boot the win8 partition all my ports are working.

---

### Post by iamtristan on 2013-04-13
maybe this is helpfull for you to help me with this issue:

with the mouse pluged into the working port:
```
xxx@Garados:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f3:0018 Elan Microelectronics Corp. 
Bus 001 Device 004: ID 04f2:b328 Chicony Electronics Co., Ltd 



```

without the mouse:

```
xxx@Garados:~$ lsusbBus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f3:0018 Elan Microelectronics Corp. 
Bus 001 Device 004: ID 04f2:b328 Chicony Electronics Co., Ltd 



```

---

### Post by fantab on 2013-04-13
So you have a total of 4 USB ports? can you post the output of "***lsub***" with mouse plugged into "non-functional" usb port?

Also with your mouse plugged in the concerned usb-port, run: ***lsusb -v*** and report back.

---

### Post by iamtristan on 2013-04-13
> [COLOR=#000000]So you have a total of 4 USB ports?[/COLOR]
No, I have only 2 (like on the picture above).

Mouse pluged into _**working port**_:
```
lsusb -v
```

```
     Field 1 first: No          Field pattern: Field 1 only
          bCopyProtect                      0
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         1
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            640
        wHeight                           480
        dwMinBitRate                 73728000
        dwMaxBitRate                147456000
        dwMaxVideoFrameBufferSize      614400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         2
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            160
        wHeight                           120
        dwMinBitRate                  4608000
        dwMaxBitRate                  9216000
        dwMaxVideoFrameBufferSize       38400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         3
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            176
        wHeight                           144
        dwMinBitRate                  6082560
        dwMaxBitRate                 12165120
        dwMaxVideoFrameBufferSize       50688
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         4
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            320
        wHeight                           240
        dwMinBitRate                 18432000
        dwMaxBitRate                 36864000
        dwMaxVideoFrameBufferSize      153600
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         5
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                           720
        dwMinBitRate                117964800
        dwMaxBitRate                117964800
        dwMaxVideoFrameBufferSize     1843200
        dwDefaultFrameInterval        1250000
        bFrameIntervalType                  1
        dwFrameInterval( 0)           1250000
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         6
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                           800
        dwMinBitRate                131072000
        dwMaxBitRate                131072000
        dwMaxVideoFrameBufferSize     2048000
        dwDefaultFrameInterval        1250000
        bFrameIntervalType                  1
        dwFrameInterval( 0)           1250000
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         7
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                          1024
        dwMinBitRate                167772160
        dwMaxBitRate                167772160
        dwMaxVideoFrameBufferSize     2621440
        dwDefaultFrameInterval        1250000
        bFrameIntervalType                  1
        dwFrameInterval( 0)           1250000
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  3 (STILL_IMAGE_FRAME)
        bEndpointAddress                    0
        bNumImageSizePatterns               7
        wWidth( 0)                       1280
        wHeight( 0)                      1024
        wWidth( 1)                       1280
        wHeight( 1)                       800
        wWidth( 2)                       1280
        wHeight( 2)                       720
        wWidth( 3)                        160
        wHeight( 3)                       120
        wWidth( 4)                        320
        wHeight( 4)                       240
        wWidth( 5)                        176
        wHeight( 5)                       144
        wWidth( 6)                        640
        wHeight( 6)                       480
        bNumCompressionPatterns             7
      VideoStreaming Interface Descriptor:
        bLength                             6
        bDescriptorType                    36
        bDescriptorSubtype                 13 (COLORFORMAT)
        bColorPrimaries                     1 (BT.709,sRGB)
        bTransferCharacteristics            1 (BT.709)
        bMatrixCoefficients                 4 (SMPTE 170M (BT.601))
      VideoStreaming Interface Descriptor:
        bLength                            11
        bDescriptorType                    36
        bDescriptorSubtype                  6 (FORMAT_MJPEG)
        bFormatIndex                        2
        bNumFrameDescriptors                7
        bFlags                              1
          Fixed-size samples: Yes
        bDefaultFrameIndex                  1
        bAspectRatioX                       0
        bAspectRatioY                       0
        bmInterlaceFlags                 0x00
          Interlaced stream or variable: No
          Fields per frame: 1 fields
          Field 1 first: No
          Field pattern: Field 1 only
          bCopyProtect                      0
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         1
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            640
        wHeight                           480
        dwMinBitRate                 73728000
        dwMaxBitRate                147456000
        dwMaxVideoFrameBufferSize      614400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         2
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            160
        wHeight                           120
        dwMinBitRate                  4608000
        dwMaxBitRate                  9216000
        dwMaxVideoFrameBufferSize       38400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         3
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            176
        wHeight                           144
        dwMinBitRate                  6082560
        dwMaxBitRate                 12165120
        dwMaxVideoFrameBufferSize       50688
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         4
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            320
        wHeight                           240
        dwMinBitRate                 18432000
        dwMaxBitRate                 36864000
        dwMaxVideoFrameBufferSize      153600
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         5
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                           720
        dwMinBitRate                221184000
        dwMaxBitRate                442368000
        dwMaxVideoFrameBufferSize     1843200
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         6
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                           800
        dwMinBitRate                245760000
        dwMaxBitRate                491520000
        dwMaxVideoFrameBufferSize     2048000
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         7
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                          1024
        dwMinBitRate                314572800
        dwMaxBitRate                629145600
        dwMaxVideoFrameBufferSize     2621440
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  3 (STILL_IMAGE_FRAME)
        bEndpointAddress                    0
        bNumImageSizePatterns               7
        wWidth( 0)                       1280
        wHeight( 0)                      1024
        wWidth( 1)                       1280
        wHeight( 1)                       800
        wWidth( 2)                       1280
        wHeight( 2)                       720
        wWidth( 3)                        160
        wHeight( 3)                       120
        wWidth( 4)                        320
        wHeight( 4)                       240
        wWidth( 5)                        176
        wHeight( 5)                       144
        wWidth( 6)                        640
        wHeight( 6)                       480
        bNumCompressionPatterns             7
      VideoStreaming Interface Descriptor:
        bLength                             6
        bDescriptorType                    36
        bDescriptorSubtype                 13 (COLORFORMAT)
        bColorPrimaries                     1 (BT.709,sRGB)
        bTransferCharacteristics            1 (BT.709)
        bMatrixCoefficients                 4 (SMPTE 170M (BT.601))
      VideoStreaming Interface Descriptor:
        bLength                            56
        bDescriptorType                    36
        bDescriptorSubtype                 14         Invalid desc subtype: 03 07 4d 34 32 30 00 00 10 00 80 00 00 aa 00 38 9b 71 32 56 55 59 00 00 10 00 80 00 00 aa 00 38 9b 71 33 56 55 59 00 00 10 00 80 00 00 aa 00 38 9b 71 00 01 00
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                 15         Invalid desc subtype: 01 00 80 02 e0 01 00 00 65 04 00 00 ca 08 00 60 09 00 15 16 05 00 02 15 16 05 00 2a 2c 0a 00
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                 15         Invalid desc subtype: 02 00 a0 00 78 00 00 50 46 00 00 a0 8c 00 00 96 00 00 15 16 05 00 02 15 16 05 00 2a 2c 0a 00
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                 15         Invalid desc subtype: 03 00 b0 00 90 00 00 d0 5c 00 00 a0 b9 00 00 c6 00 00 15 16 05 00 02 15 16 05 00 2a 2c 0a 00
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                 15         Invalid desc subtype: 04 00 40 01 f0 00 00 40 19 01 00 80 32 02 00 58 02 00 15 16 05 00 02 15 16 05 00 2a 2c 0a 00
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                 15         Invalid desc subtype: 05 00 00 05 d0 02 00 00 65 04 00 00 ab 09 00 20 1c 00 22 df 0d 00 02 22 df 0d 00 80 84 1e 00
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                 15         Invalid desc subtype: 06 00 00 05 20 03 00 00 d0 07 00 00 d0 07 00 40 1f 00 d0 12 13 00 01 d0 12 13 00
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                 15         Invalid desc subtype: 07 00 00 05 00 04 00 00 00 0a 00 00 00 0a 00 00 28 00 d0 12 13 00 01 d0 12 13 00
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  3 (STILL_IMAGE_FRAME)
        bEndpointAddress                    0
        bNumImageSizePatterns               7
        wWidth( 0)                       1280
        wHeight( 0)                      1024
        wWidth( 1)                       1280
        wHeight( 1)                       800
        wWidth( 2)                       1280
        wHeight( 2)                       720
        wWidth( 3)                        160
        wHeight( 3)                       120
        wWidth( 4)                        320
        wHeight( 4)                       240
        wWidth( 5)                        176
        wHeight( 5)                       144
        wWidth( 6)                        640
        wHeight( 6)                       480
        bNumCompressionPatterns             7
      VideoStreaming Interface Descriptor:
        bLength                             6
        bDescriptorType                    36
        bDescriptorSubtype                 13 (COLORFORMAT)
        bColorPrimaries                     1 (BT.709,sRGB)
        bTransferCharacteristics            1 (BT.709)
        bMatrixCoefficients                 4 (SMPTE 170M (BT.601))
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0080  1x 128 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0b00  2x 768 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0c00  2x 1024 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       6
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x1380  3x 896 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       7
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x1400  3x 1024 bytes
        bInterval               1



```

Mouse pluged into **_non working port_**:
```
lsusb -v
```
```
guidFormat                            {59555932-0000-1000-8000-00aa00389b71}        bBitsPerPixel                      16
        bDefaultFrameIndex                  1
        bAspectRatioX                       0
        bAspectRatioY                       0
        bmInterlaceFlags                 0x00
          Interlaced stream or variable: No
          Fields per frame: 2 fields
          Field 1 first: No
          Field pattern: Field 1 only
          bCopyProtect                      0
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         1
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            640
        wHeight                           480
        dwMinBitRate                 73728000
        dwMaxBitRate                147456000
        dwMaxVideoFrameBufferSize      614400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         2
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            160
        wHeight                           120
        dwMinBitRate                  4608000
        dwMaxBitRate                  9216000
        dwMaxVideoFrameBufferSize       38400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         3
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            176
        wHeight                           144
        dwMinBitRate                  6082560
        dwMaxBitRate                 12165120
        dwMaxVideoFrameBufferSize       50688
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         4
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            320
        wHeight                           240
        dwMinBitRate                 18432000
        dwMaxBitRate                 36864000
        dwMaxVideoFrameBufferSize      153600
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         5
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                           720
        dwMinBitRate                117964800
        dwMaxBitRate                117964800
        dwMaxVideoFrameBufferSize     1843200
        dwDefaultFrameInterval        1250000
        bFrameIntervalType                  1
        dwFrameInterval( 0)           1250000
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         6
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                           800
        dwMinBitRate                131072000
        dwMaxBitRate                131072000
        dwMaxVideoFrameBufferSize     2048000
        dwDefaultFrameInterval        1250000
        bFrameIntervalType                  1
        dwFrameInterval( 0)           1250000
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         7
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                          1024
        dwMinBitRate                167772160
        dwMaxBitRate                167772160
        dwMaxVideoFrameBufferSize     2621440
        dwDefaultFrameInterval        1250000
        bFrameIntervalType                  1
        dwFrameInterval( 0)           1250000
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  3 (STILL_IMAGE_FRAME)
        bEndpointAddress                    0
        bNumImageSizePatterns               7
        wWidth( 0)                       1280
        wHeight( 0)                      1024
        wWidth( 1)                       1280
        wHeight( 1)                       800
        wWidth( 2)                       1280
        wHeight( 2)                       720
        wWidth( 3)                        160
        wHeight( 3)                       120
        wWidth( 4)                        320
        wHeight( 4)                       240
        wWidth( 5)                        176
        wHeight( 5)                       144
        wWidth( 6)                        640
        wHeight( 6)                       480
        bNumCompressionPatterns             7
      VideoStreaming Interface Descriptor:
        bLength                             6
        bDescriptorType                    36
        bDescriptorSubtype                 13 (COLORFORMAT)
        bColorPrimaries                     1 (BT.709,sRGB)
        bTransferCharacteristics            1 (BT.709)
        bMatrixCoefficients                 4 (SMPTE 170M (BT.601))
      VideoStreaming Interface Descriptor:
        bLength                            11
        bDescriptorType                    36
        bDescriptorSubtype                  6 (FORMAT_MJPEG)
        bFormatIndex                        2
        bNumFrameDescriptors                7
        bFlags                              1
          Fixed-size samples: Yes
        bDefaultFrameIndex                  1
        bAspectRatioX                       0
        bAspectRatioY                       0
        bmInterlaceFlags                 0x00
          Interlaced stream or variable: No
          Fields per frame: 1 fields
          Field 1 first: No
          Field pattern: Field 1 only
          bCopyProtect                      0
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         1
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            640
        wHeight                           480
        dwMinBitRate                 73728000
        dwMaxBitRate                147456000
        dwMaxVideoFrameBufferSize      614400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         2
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            160
        wHeight                           120
        dwMinBitRate                  4608000
        dwMaxBitRate                  9216000
        dwMaxVideoFrameBufferSize       38400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         3
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            176
        wHeight                           144
        dwMinBitRate                  6082560
        dwMaxBitRate                 12165120
        dwMaxVideoFrameBufferSize       50688
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         4
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            320
        wHeight                           240
        dwMinBitRate                 18432000
        dwMaxBitRate                 36864000
        dwMaxVideoFrameBufferSize      153600
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         5
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                           720
        dwMinBitRate                221184000
        dwMaxBitRate                442368000
        dwMaxVideoFrameBufferSize     1843200
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         6
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                           800
        dwMinBitRate                245760000
        dwMaxBitRate                491520000
        dwMaxVideoFrameBufferSize     2048000
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         7
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                          1024
        dwMinBitRate                314572800
        dwMaxBitRate                629145600
        dwMaxVideoFrameBufferSize     2621440
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  3 (STILL_IMAGE_FRAME)
        bEndpointAddress                    0
        bNumImageSizePatterns               7
        wWidth( 0)                       1280
        wHeight( 0)                      1024
        wWidth( 1)                       1280
        wHeight( 1)                       800
        wWidth( 2)                       1280
        wHeight( 2)                       720
        wWidth( 3)                        160
        wHeight( 3)                       120
        wWidth( 4)                        320
        wHeight( 4)                       240
        wWidth( 5)                        176
        wHeight( 5)                       144
        wWidth( 6)                        640
        wHeight( 6)                       480
        bNumCompressionPatterns             7
      VideoStreaming Interface Descriptor:
        bLength                             6
        bDescriptorType                    36
        bDescriptorSubtype                 13 (COLORFORMAT)
        bColorPrimaries                     1 (BT.709,sRGB)
        bTransferCharacteristics            1 (BT.709)
        bMatrixCoefficients                 4 (SMPTE 170M (BT.601))
      VideoStreaming Interface Descriptor:
        bLength                            56
        bDescriptorType                    36
        bDescriptorSubtype                 14         Invalid desc subtype: 03 07 4d 34 32 30 00 00 10 00 80 00 00 aa 00 38 9b 71 32 56 55 59 00 00 10 00 80 00 00 aa 00 38 9b 71 33 56 55 59 00 00 10 00 80 00 00 aa 00 38 9b 71 00 01 00
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                 15         Invalid desc subtype: 01 00 80 02 e0 01 00 00 65 04 00 00 ca 08 00 60 09 00 15 16 05 00 02 15 16 05 00 2a 2c 0a 00
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                 15         Invalid desc subtype: 02 00 a0 00 78 00 00 50 46 00 00 a0 8c 00 00 96 00 00 15 16 05 00 02 15 16 05 00 2a 2c 0a 00
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                 15         Invalid desc subtype: 03 00 b0 00 90 00 00 d0 5c 00 00 a0 b9 00 00 c6 00 00 15 16 05 00 02 15 16 05 00 2a 2c 0a 00
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                 15         Invalid desc subtype: 04 00 40 01 f0 00 00 40 19 01 00 80 32 02 00 58 02 00 15 16 05 00 02 15 16 05 00 2a 2c 0a 00
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                 15         Invalid desc subtype: 05 00 00 05 d0 02 00 00 65 04 00 00 ab 09 00 20 1c 00 22 df 0d 00 02 22 df 0d 00 80 84 1e 00
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                 15         Invalid desc subtype: 06 00 00 05 20 03 00 00 d0 07 00 00 d0 07 00 40 1f 00 d0 12 13 00 01 d0 12 13 00
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                 15         Invalid desc subtype: 07 00 00 05 00 04 00 00 00 0a 00 00 00 0a 00 00 28 00 d0 12 13 00 01 d0 12 13 00
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  3 (STILL_IMAGE_FRAME)
        bEndpointAddress                    0
        bNumImageSizePatterns               7
        wWidth( 0)                       1280
        wHeight( 0)                      1024
        wWidth( 1)                       1280
        wHeight( 1)                       800
        wWidth( 2)                       1280
        wHeight( 2)                       720
        wWidth( 3)                        160
        wHeight( 3)                       120
        wWidth( 4)                        320
        wHeight( 4)                       240
        wWidth( 5)                        176
        wHeight( 5)                       144
        wWidth( 6)                        640
        wHeight( 6)                       480
        bNumCompressionPatterns             7
      VideoStreaming Interface Descriptor:
        bLength                             6
        bDescriptorType                    36
        bDescriptorSubtype                 13 (COLORFORMAT)
        bColorPrimaries                     1 (BT.709,sRGB)
        bTransferCharacteristics            1 (BT.709)
        bMatrixCoefficients                 4 (SMPTE 170M (BT.601))
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0080  1x 128 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0b00  2x 768 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0c00  2x 1024 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       6
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x1380  3x 896 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       7
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x1400  3x 1024 bytes
        bInterval               1



```


Thank you for your time!

---

### Post by gordintoronto on 2013-04-13
The computer has two "internal" USB ports, one for the webcam and one for the card reader.

---

### Post by iamtristan on 2013-04-14
> **gordintoronto said:**
> The computer has two "internal" USB ports, one for the webcam and one for the card reader.

from the two internal ports works only the webcam.
but i'm ok with that because i dont need the cardreader.

> "lsub" with mouse plugged into "non-functional" usb port?

```
xxx@Garados:~$ lsusbBus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f3:0018 Elan Microelectronics Corp. 
Bus 001 Device 004: ID 04f2:b328 Chicony Electronics Co., Ltd 



```

---

### Post by iamtristan on 2013-04-14
I re-installed everything from scratch, but no change about the usb-port.

If someone has an idea how to fix this, i'll be very thankful

---

### Post by iamtristan on 2013-04-16
i've googled around but could not find something like a general how-to-use-all-your usb ports.

does someone have a link to a tutorial about that matter?

---

### Post by iamtristan on 2013-04-17
pump

---

### Post by fantab on 2013-04-17
> **iamtristan said:**
> I re-installed everything from scratch, but no change about the usb-port.

If someone has an idea how to fix this, i'll be very thankful

Which ubuntu version did you install? Have you updated it after installing? It is unusual for that port to not work. 

You can try [13.04]("http://cdimage.ubuntu.com/daily-live/current/"), though its still in beta its quite stable and will be released shortly. I recommend this because there could be some issue between the ubuntu version you installed and the hardware. Try installing a different version of Ubuntu.

Good Luck...

---

### Post by iamtristan on 2013-04-18
I installed again 12.10.

Should I simply update to 13.04 or make a full reinstall?

---

### Post by fantab on 2013-04-18
Preferably, do a Full reinstall. Because if you Upgrade from 12.10 then the issue you are having can be carried forward to 13.04. If it isn't too much for you, also keep Ubuntu [12.04.1]("http://www.ubuntu.com/download/desktop/alternative-downloads") ready. As this version of Ubuntu has support for older Hardware. Just in case.

---

### Post by iamtristan on 2013-04-18
I tried it with the update, but as you said the issue remained.

But I'll try it with a full reinstall this weeked and report back.

another issue (with 13.04) is this ubuntu-one-sync-icon in the menu bar.
does anyone know how to remove it?

---

### Post by fantab on 2013-04-18
Just right click on it and "remove from launcher". Or do you want to remove it from the topbar? Ubuntu or Xubuntu? But such minor things can be sorted out later. By the way, in case you are not aware, the Ubuntu One account comes with 5gb free space. It can be used to Sync Important DATA.

---

### Post by iamtristan on 2013-04-18
I want to remove it from the topbar, working with ubuntu 13.04.

I know about the 5gb but since i have nearly 100gb dropbox space i dont need it ;) and dont want it in my topbar :)

---

### Post by fantab on 2013-04-18
Ok. Its in your top bar because it is autostarting with the ubuntu. You can either unistall it completely or disable it from being autostarted.

You can uninstall it with either 'Software Center' or 'Synaptic Package Manager'.

---

### Post by iamtristan on 2013-04-18
tried both.
- clean install 12.04.2
- clean install 13.04

no success in both cases.

any other ideas how to get usb support on this second usb port?

---

### Post by sudodus on 2013-04-18
You need not install Ubuntu to try it. Run it live (booted from the install CD/DVD/USB drive)!

It is very unusual, that a USB port works in windows but not in linux. Have you tried it ***in both systems*** with some simple hardware, that is likely to work in both systems? For example a mouse, keyboard or 'flash pendrive'? Could it be a hardware problem, for example some connector, that is not connecting properly?

If  still no luck, try some other linux distro, for example Linux Mint or Knoppix.

---

### Post by fantab on 2013-04-18
Yes, like suggested try Another Disro, you can try [Fedora]("https://fedoraproject.org/") or [openSUSE]("http://www.opensuse.org/en/"). Linux Mint is based on Ubuntu so if you are having problems with one, the other won't help much. Knoppix is great to check hardware issues.

---

### Post by iamtristan on 2013-04-19
> **sudodus said:**
> Have you tried it ***in both systems*** with some simple hardware, that is likely to work in both systems? For example a mouse, keyboard or 'flash pendrive'? Could it be a hardware problem, for example some connector, that is not connecting properly?


Yes I have tested with mice, pendrive, keyboard and webcam.


does Fedora have this great boot repair application?



Edit:
tested Fedora - wont even boot...

---

### Post by iamtristan on 2013-04-19
i had a thought, i first installed ubuntu-12.10-desktop-amd64 because [http://www.ubuntu.com/download/desktop/questions?distro=desktop&bits=64&release=latest](http://www.ubuntu.com/download/desktop/questions?distro=desktop&bits=64&release=latest) gave me this.

but in my laptop i have a intel i7 cpu, is it possible that this causes the problem?

i tried to boot into live ubuntu i386 version but failed always...

---

### Post by fantab on 2013-04-19
No... your issue has nothing to do with intel i7. In fact intel, on the whole, supports Linux/Opensource quite well.

Yes, even I had this problem where I couldn't install 32bit on a 64bit machine. It happened with Ubuntu only. I couldn't figure out why though neither did the people who were trying to help in this forum. 

How did that Fedora install go? any luck with that port?

---

### Post by iamtristan on 2013-04-19
Fedora didn't boot - i stopped testing because i didn't want to mess with my dual boot configuration.

Its really weird,
I can boot from live-usb on the non-working port and it starts grub and let me choose between install ubuntu or try without installing, but both options result in 

```
[COLOR=#000000]BusyBox v1.19.3 (Ubuntu 1:1.19.3-7ubuntu1) built-in shell (ash)[/COLOR]
[COLOR=#000000]Enter 'help' for list of built-in commands.[/COLOR]

[COLOR=#000000](initramfs) Unable to find a medium containing a live file system[/COLOR]
```

---

### Post by fantab on 2013-04-19
I think you should try to boot another Distro just to confirm things.
Perhaps its time you consult your Laptop's Service and try to get your port replaced. 

Good Luck...

---

### Post by iamtristan on 2013-04-19
i thought about this - but it seems rather strange that the port works flawless on windows but not on ubuntu.

anyway - thanks very much for your time!

---

### Post by sudodus on 2013-04-19
> **iamtristan said:**
> Fedora didn't boot - i stopped testing because i didn't want to mess with my dual boot configuration.

Its really weird,
I can boot from live-usb on the non-working port and it starts grub and let me choose between install ubuntu or try without installing, but both options result in 

```
[COLOR=#000000]BusyBox v1.19.3 (Ubuntu 1:1.19.3-7ubuntu1) built-in shell (ash)[/COLOR]
[COLOR=#000000]Enter 'help' for list of built-in commands.[/COLOR]

[COLOR=#000000](initramfs) Unable to find a medium containing a live file system[/COLOR]
```
This is interesting. Obviously the usb port is working, but somehow it is disconnected electronically, when linux starts. Maybe some driver in the linux kernel cannot cooperate with your usb hardware or firmware.

Can you find any setting in your BIOS menus for USB? Some computers have a setting to enable/disable USB legacy emulation. I have a Toshiba laptop with InsydeH2O BIOS, where this feature is described like this,

> Enable or disable USB keyboard/mouse legacy emulation so that, even if your operating system does not support USB devices, you can still use a standard USB mouse and keyboard.


There is another menu item for USB 3,

> Enables the internal USB3.0 controller/ Disables the internal USB3.0 controller. If this setting is selected, the internal USB3.0 port(s) on the PC will work as USB2.0 port(s).

---

### Post by iamtristan on 2013-04-19
I have the [COLOR=#000000]InsydeH2O BIOS (3.7) too,
but [/COLOR]unfortunately did sony not unlock all options...

I read about bios flashes and stuff to get acces to this options - but it was all very [COLOR=#000000][FONT=arial]vaguely[/FONT][/COLOR] and sounded pretty unsafe...

---

### Post by sudodus on 2013-04-19
Try Knoppix! It is known to cooperate well with a lot of hardware.

---

### Post by sudodus on 2013-04-19
> **iamtristan said:**
> I have the [COLOR=#000000]InsydeH2O BIOS (3.7) too,
but [/COLOR]unfortunately did sony not unlock all options...

I read about bios flashes and stuff to get acces to this options - but it was all very [COLOR=#000000][FONT=arial]vaguely[/FONT][/COLOR] and sounded pretty unsafe...

If the BIOS is buggy, it will help a lot to get the latest stable version. But if there is a power outage when you are flashing the new version, it can be very hard to make a desktop computer run again. This is not a problem with a laptop with a good and fully charged battery.

So read very carefully the instructions and follow them in detail to get a new version of BIOS, if there is one for your computer.

---

### Post by iamtristan on 2013-04-19
I updated the bios with:
[http://www.sony.ch/support/de/product/SVT1312X1ES/downloads/EP0000295575_8582](http://www.sony.ch/support/de/product/SVT1312X1ES/downloads/EP0000295575_8582)

but no improvement.

and i'am (at the moment) not brave enough to flash the bios with some second hand moded maybe-working-bios.

---

### Post by sudodus on 2013-04-19
> **iamtristan said:**
> I updated the bios with:
[http://www.sony.ch/support/de/product/SVT1312X1ES/downloads/EP0000295575_8582](http://www.sony.ch/support/de/product/SVT1312X1ES/downloads/EP0000295575_8582)

but no improvement.

and i'am (at the moment) not brave enough to flash the bios with some second hand moded maybe-working-bios.

No, I wouldn't take that risk either. It is better to use an external USB hub if necessary ... and try some other linux distro.

---

### Post by iamtristan on 2013-04-19
its really a shame that sony dont trust its users and hides essential bios options.

---

