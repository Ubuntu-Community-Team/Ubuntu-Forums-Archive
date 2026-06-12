---
title: "Howto: Configure MX5000 advanced features over bluetooth."
date: 2010-08-21
forum: Outdated Tutorials &amp; Tips
---

### Post by modmadmike on 2010-08-21
I found out about MX5000 tools only to find it only works in emulation mode and not bluetooth mode. I played around untill I found out a fix which is steps 8 onwards.

0. Make sure you have the software requirements. ```
sudo apt-get install netpbm libnetpbm10-dev libglib2.0-dev build-essential
```
1. Download MX5000 tools from [http://download.gna.org/mx5000tools/mx5000tools-0.1.2.tar.gz]("http://download.gna.org/mx5000tools/mx5000tools-0.1.2.tar.gz").
2. Extract to a new directory. ```
tar -xzf mx5000tools-0.1.2.tar.gz
```
3. Change Directory into it ```
cd mx5000tools-0.1.2
```
4. Generate files for compilation ```
./configure
```
5. Compile ```
make -j4 #the j4 gives it 4 threads
```
6. Install ```
sudo make -j4 install
```
7. Configure libs ```
sudo ldconfig
```

#FIX FOR BLUETOOTH MODE
8. Open /lib/udev/rules.d/70-hid2hci.rules for editing ```
sudo gedit /lib/udev/rules.d/70-hid2hci.rules
```
9. Replace the "Logitech devices" section with ```
# Logitech devices
##KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[35e]", \
##  RUN+="hid2hci --method=logitech-hid --devpath=%p"
##KERNEL=="hidraw*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[4abc]|c71[34bc]", \
##  RUN+="hid2hci --method=logitech-hid --devpath=%p"

# Mx5000 reciever
KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="0b02", \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"
# MX5000 keyboard over bluetooth
KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="b305", \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"
```
10. Save && exit
11. Unplug receiver then plug receiver back in.

For usage see ```
mx5000-tool --help
``` but remember to specify the device as /dev/hiddev0.

---

