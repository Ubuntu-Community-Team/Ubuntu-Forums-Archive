---
title: "wifi usb adapter installation on Ubuntu"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by tijak on 2012-05-10
I tried to install a WIFI USB ADAPTER (WIRE-N-USB-150) on Ubuntu.
 
Using "set up" for LINUX in the package did not help as nothing happened. 
And once again I do not know which software should be used or step taken. 
 
Help anyone?
 
Thanks.

---

### Post by anewguy on 2012-05-10
With the device plugged in, open a terminal window and type:

lsusb <press enter>

Copy/paste the output back in a reply here.  We need to know what chipset is being used.

Dave ;)

---

### Post by tijak on 2012-05-11
Hello Anewguy and thanks again!

Below is the information I got after following your advice. I don't know if what you need is really there, though...

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 03f0:7611 Hewlett-Packard DeskJet F2492 All-in-One
Bus 003 Device 002: ID 046d:c52e Logitech, Inc. 
Bus 003 Device 003: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN

---

### Post by chamber on 2012-05-11
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true#2772](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true#2772)

Download linux drivers to desktop.

Extract the zip file

Open a terminal

```
cd ~/Desktop/RTL8188C_8192C_8192D_USB_linux_v3.4.2_3727.20120404
sudo bash install.sh

```

You will be prompted for the root password.

More information in the attached pdf file.

Edit

If that does not work then do the following.

```
cd ~/Desktop/RTL8188C_8192C_8192D_USB_linux_v3.4.2_3727.20120404/driver
```

Extract the driver
```
tar zxvf rtl8188C_8192C_8192D_usb_linux_v3.4.2_3727.20120404.tar.gz
cd rtl8188C_8192C_8192D_usb_linux_v3.4.2_3727.20120404
```

make 8192C USB driver module
```
make
sudo make install

```

clean the operation environment
```
./clean
```

insert 8192C USB modules
```
sudo modprobe 8192cu 
```

---

