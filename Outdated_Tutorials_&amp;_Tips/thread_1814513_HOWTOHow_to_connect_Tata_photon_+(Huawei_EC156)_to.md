---
title: "HOWTO:How to connect Tata photon +(Huawei EC156) to ubuntu natty"
date: 2011-07-29
forum: Outdated Tutorials &amp; Tips
---

### Post by jayadeep on 2011-07-29
Please ensure that you have installed the following packages
 *  usb-modeswitch-data
 *  usb-modeswitch

Connect the device and see whether it is detected automatically in the network manager
if not do the following things.
.Open the terminal
.Type
```
sudo nautilus
```
A new window will be opened for root
.Go to filesystems ----/etc/usb_modeswitch.d
.Create a new config file named **12d1:1505**
 .Cut and Paste the following  
 ```
DefaultVendor= 0x12d1 
DefaultProduct=0x1505 

MessageContent="55534243123456780000000000000011062000000100000000000000000000" 
  
```
 .Save the file
 .Go to terminal  
 .Go to the path by the code  
 ```
cd /etc/usb_modeswitch.d
```
 .Type the command
 ```
sudo usb_modeswitch -I -W -c 12d1\:1505
```
 .It may connect automatically..
 .Just wait for one minute
 .The default network manager may detect your device and follow the instructions by it
 mark it to **connect automatically** in the **mobile broadband** **edit** options
 .If not open your **network mannager** go to **manage connection**
 open the **mobile broadband** and **add** a new connection
 if it detects installed **CDMA device** or **Huawei EC156** follow the instruction given by the network manager
 mark it to **connect automatically** in the **mobile broadband edit** options
 .Rebbot your system and  see it is connected automatically  
 .If not you have to type the two codes mentioned above all the times when you connect your device
 It will be very diffficult to type the codes all the time....so go for the following steps to run that commands automattically


STEPS
Script to run the modeswitch command in boot
steps
1.Open the gedit
2.Type the two commands which you want to run in two separate lines.
3.save the file with the extension **.sh** on the disk where ever you want and make this file **as executable** in the **properties**
4.Then **right click** on the desktop
5 Create **launcher**
6.Set **type** as **Run in terminal**
7.Give your desired name
8.Give the path of file with the extension **.sh** in the **command** box
9.Hit **ok**

Open the launcher.....
enter the password if required

You can change your icon in the properties of the new launcher file

Connect your device when ever required and  click the new icon on the desktop
 Hit the password.....
 enjoy...

---

