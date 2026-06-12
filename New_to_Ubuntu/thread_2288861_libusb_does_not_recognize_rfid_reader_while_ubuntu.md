---
title: "libusb does not recognize rfid reader while ubuntu does"
date: 2015-07-30
forum: New to Ubuntu
---

### Post by biedubbeljoe2 on 2015-07-30
Hello,

I am running Ubuntu Unity 14.04.2 LTS desktop on a x64 system, kernel 3.16.0-45-generic (x86_64) and try to get my Ehuoyan RFID reader, model: YHY638A up and running. As I type dmesg | tail I can see:
[ 9728.940691] cp210x ttyUSB0: cp210x converter now disconnected from ttyUSB0
[ 9728.940728] cp210x 3-1:1.0: device disconnected
[10058.440126] usb 3-1: new full-speed USB device number 4 using uhci_hcd
[10058.602130] usb 3-1: New USB device found, idVendor=10c4, idProduct=ea60
[10058.602138] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[10058.602145] usb 3-1: Product: CP2102 USB to UART Bridge Controller
[10058.602150] usb 3-1: Manufacturer: Silicon Labs
[10058.602155] usb 3-1: SerialNumber: 0001
[10058.608198] cp210x 3-1:1.0: cp210x converter detected
[10058.610309] usb 3-1: cp210x converter now attached to ttyUSB0

that the reader is connected and attached to ttyUSB0. Apparently the file system does recognize the reader. However after installing libusb and running the command: nfc-list, libusb can't seems to find my RFID reader:
nfc-list uses libnfc 1.7.0-rc7
No NFC device found.

Looking up the specs of libusb I see that my reader is not in the list. I think that I need to compile the CP210x device driver into libusb, but I have no idea how to go from here. Does anyone have this knowledge and is willing to help me out?

Thx, Biedubbeljoe.

---

### Post by Vis.Lee on 2015-08-24
Hi Biedubbeljoe:

 I had the same issue and I solved by following steps:

 1. update cp210x.ko

    1.1 please download the cp210x.c from corresponding  kernel tree, ex: 
      wget [https://git.kernel.org/cgit/linux/kernel/git/stable/linux-stable.git/plain/drivers/usb/serial/cp210x.c?h=linux-3.16.y](https://git.kernel.org/cgit/linux/kernel/git/stable/linux-stable.git/plain/drivers/usb/serial/cp210x.c?h=linux-3.16.y) -O

  1.2 compile and replace the cp210x.ko, please ref here: [Linux_CP210x_VCP_3.x.x_Release_Notes.txt]("http://www.silabs.com/Support%20Documents/Software/Linux_CP210x_VCP_3.x.x_Release_Notes.txt")

2. update the device list in /etc/nfc/libnfc.conf, ex:
    device.name = "nfcreader"
    device.connstring = "pn532_uart:/dev/ttyUSB0:115200"

3. set the permission of /dev/ttyUSB0 to 666, ex:
    sudo chmod 666 /dev/ttyUSB0

 my nfc reader works well with the libnfc after I done these steps. hope it could help you to solve your problem.

Sincerely,
Vis

---

