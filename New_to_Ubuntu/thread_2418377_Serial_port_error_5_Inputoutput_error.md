---
title: "Serial port error 5 Input/output error"
date: 2019-05-06
forum: New to Ubuntu
---

### Post by rzmd on 2019-05-06
I'm trying to use a TI CC2531 USB dongle for wireless sniffing.  Connecting it to my laptop did not initially create a ttyUSB interface, I  solved this by running 

```
   
sudo modprobe ftdi_sio
sudo sh -c "echo 0451 16ae > /sys/bus/usb-serial/drivers/ftdi_sio/new_id"
```

  where 0451 and 16ae are the vendor and product IDs respectively. When I try to flash it I get the following error:

  ```

sudo make PORT=/dev/ttyUSB2 sniff
[sudo] password for rzmd: 
TARGET not defined, using target srf06-cc26xx
python ../../tools/sensniff/sensniff.py -b 460800 -d /dev/ttyUSB2
Error opening port: /dev/ttyUSB2
The error was: (5, 'Input/output error')
Makefile:44: recipe for target 'sniff' failed
make: *** [sniff] Error 1

```

  setserial -g /dev/ttyUSB2 yields: 
```

/dev/ttyUSB2, UART: unknown, Port: 0x0000, IRQ: 0

```

  lsusb -v yields:
  ```

Bus 001 Device 022: ID 0451:16ae Texas Instruments, Inc. 
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        32
  idVendor           0x0451 Texas Instruments, Inc.
  idProduct          0x16ae 
  bcdDevice            2.10
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
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
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               5

```

  Running dmesg after connecting the device yields:
  ```

[ 7647.522673] usb 1-1: new full-speed USB device number 23 using xhci_hcd
[ 7647.674693] usb 1-1: New USB device found, idVendor=0451, idProduct=16ae
[ 7647.674702] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 7647.674709] usb 1-1: Product: CC2531 USB Dongle
[ 7647.674716] usb 1-1: Manufacturer: Texas Instruments
[ 7647.676183] ftdi_sio 1-1:1.0: FTDI USB Serial Device converter detected
[ 7647.676498] usb 1-1: Detected FT8U232AM
[ 7647.676724] usb 1-1: FTDI USB Serial Device converter now attached to ttyUSB2
[ 7649.257165] ftdi_sio ttyUSB2: ftdi_set_termios FAILED to set databits/stopbits/parity
[ 7649.257531] ftdi_sio ttyUSB2: ftdi_set_termios urb failed to set baudrate
[ 7649.257890] ftdi_sio ttyUSB2: urb failed to clear flow control
[ 7649.258570] ftdi_sio ttyUSB2: ftdi_set_termios urb failed to set baudrate
[ 7649.258819] ftdi_sio ttyUSB2: urb failed to set to xon/xoff flow control
[ 7649.259249] ftdi_sio ttyUSB2: ftdi_set_termios error from disable flowcontrol urb
[ 7649.259726] ftdi_sio ttyUSB2: urb failed to set to xon/xoff flow control
[ 7649.360365] ftdi_sio ttyUSB2: ftdi_set_termios urb failed to set baudrate
[ 7649.360888] ftdi_sio ttyUSB2: urb failed to set to xon/xoff flow control
[ 7649.361616] ftdi_sio ttyUSB2: failed to get modem status: -32
[ 7649.361863] ftdi_sio ttyUSB2: error from flowcontrol urb
[ 7649.363409] ftdi_sio ttyUSB2: ftdi_set_termios FAILED to set databits/stopbits/parity
[ 7649.363597] ftdi_sio ttyUSB2: ftdi_set_termios urb failed to set baudrate
[ 7649.363768] ftdi_sio ttyUSB2: urb failed to set to xon/xoff flow control
[ 7649.364154] ftdi_sio ttyUSB2: urb failed to set to xon/xoff flow control
[ 7649.364426] ftdi_sio ttyUSB2: ftdi_set_termios error from disable flowcontrol urb
[ 7649.364803] ftdi_sio ttyUSB2: urb failed to set to xon/xoff flow control
[ 7649.465368] ftdi_sio ttyUSB2: ftdi_set_termios urb failed to set baudrate
[ 7649.465828] ftdi_sio ttyUSB2: urb failed to set to xon/xoff flow control
[ 7649.466420] ftdi_sio ttyUSB2: failed to get modem status: -32
[ 7649.466766] ftdi_sio ttyUSB2: error from flowcontrol urb
[ 7649.467854] ftdi_sio ttyUSB2: ftdi_set_termios FAILED to set databits/stopbits/parity
[ 7649.468024] ftdi_sio ttyUSB2: ftdi_set_termios urb failed to set baudrate
[ 7649.468217] ftdi_sio ttyUSB2: urb failed to set to xon/xoff flow control
[ 7649.468746] ftdi_sio ttyUSB2: urb failed to set to xon/xoff flow control
[ 7649.469056] ftdi_sio ttyUSB2: ftdi_set_termios error from disable flowcontrol urb
[ 7649.469446] ftdi_sio ttyUSB2: urb failed to set to xon/xoff flow control
[ 7649.570003] ftdi_sio ttyUSB2: ftdi_set_termios urb failed to set baudrate
[ 7649.570388] ftdi_sio ttyUSB2: urb failed to set to xon/xoff flow control
[ 7649.571132] ftdi_sio ttyUSB2: failed to get modem status: -32
[ 7649.571338] ftdi_sio ttyUSB2: error from flowcontrol urb
[ 7649.572512] ftdi_sio ttyUSB2: ftdi_set_termios FAILED to set databits/stopbits/parity
[ 7649.572698] ftdi_sio ttyUSB2: ftdi_set_termios urb failed to set baudrate
[ 7649.572876] ftdi_sio ttyUSB2: urb failed to set to xon/xoff flow control
[ 7649.573253] ftdi_sio ttyUSB2: urb failed to set to xon/xoff flow control
[ 7649.573539] ftdi_sio ttyUSB2: ftdi_set_termios error from disable flowcontrol urb
[ 7649.573912] ftdi_sio ttyUSB2: urb failed to set to xon/xoff flow control
[ 7649.674416] ftdi_sio ttyUSB2: ftdi_set_termios urb failed to set baudrate
[ 7649.675126] ftdi_sio ttyUSB2: urb failed to set to xon/xoff flow control
[ 7649.675796] ftdi_sio ttyUSB2: failed to get modem status: -32
[ 7649.676033] ftdi_sio ttyUSB2: error from flowcontrol urb
[ 7649.677712] ftdi_sio ttyUSB2: ftdi_set_termios FAILED to set databits/stopbits/parity
[ 7649.677923] ftdi_sio ttyUSB2: ftdi_set_termios urb failed to set baudrate
[ 7649.678107] ftdi_sio ttyUSB2: urb failed to set to xon/xoff flow control
[ 7649.678617] ftdi_sio ttyUSB2: urb failed to set to xon/xoff flow control
[ 7649.678933] ftdi_sio ttyUSB2: ftdi_set_termios error from disable flowcontrol urb
[ 7649.679285] ftdi_sio ttyUSB2: urb failed to set to xon/xoff flow control
[ 7649.779918] ftdi_sio ttyUSB2: ftdi_set_termios urb failed to set baudrate
[ 7649.780469] ftdi_sio ttyUSB2: urb failed to set to xon/xoff flow control
[ 7649.781467] ftdi_sio ttyUSB2: failed to get modem status: -32
[ 7649.781659] ftdi_sio ttyUSB2: error from flowcontrol urb

```

  I've tried using setserial to set the UART, port, and IRQ values but it has no effect. What can I do?

---

### Post by dino99 on 2019-05-06
Which kernel are you using ? not sure actual kernel know/support that chip id.
[https://stackoverflow.com/questions/31071001/zigbee-kernel-driver](https://stackoverflow.com/questions/31071001/zigbee-kernel-driver)

---

### Post by rzmd on 2019-05-06
> **dino99 said:**
> Which kernel are you using ? not sure actual kernel know/support that chip id.
[https://stackoverflow.com/questions/31071001/zigbee-kernel-driver](https://stackoverflow.com/questions/31071001/zigbee-kernel-driver)

uname -a:
```

Linux rzmd 4.15.0-47-generic #50-Ubuntu SMP Wed Mar 13 10:44:52 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

```

---

