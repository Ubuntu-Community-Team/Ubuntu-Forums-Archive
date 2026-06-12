---
title: "Reliance netconnect on ubuntu 12.10"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by quarkhirad on 2013-01-14
I need to use my reliance netconnect usb modem to connect to the net on my laptop. Since i dint have a net connection i used my friends wifi connection to google search. I found a tutorial. The steps of the tutorial are given at the bottem of this post. I installed the required packages using synaptic. 

now the tutotrial (step 6) on how to connect my reliance netconnect it says open gnome-ppp and then open the settings tab and select your device for example /dev/ttyusb0. Now the problem is whenever i press detect. an error pops up no modem was found on your system. 

My question is how do i get my modem to be detected so that i can use it to connect to the net and not be dependent on my friends wifi. 

My dmesg output is given below 


> [ 4276.543621] usb 2-1.2: USB disconnect, device number 11
[ 4294.009786] usb 2-1.2: new full-speed USB device number 12 using ehci_hcd
[ 4294.103442] usb 2-1.2: New USB device found, idVendor=12d1, idProduct=1446
[ 4294.103452] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=4
[ 4294.103457] usb 2-1.2: Product: HUAWEI Mobile
[ 4294.103462] usb 2-1.2: Manufacturer: HUA\xffffffc3\xffffffbf\xffffffbfWEI TECHNOLOGIES
[ 4294.103466] usb 2-1.2: SerialNumber: \xffffffc3\xffffffbf\xffffffbf\xffffffc3\xffffffbf\xffffffbf\xffffffc3\xffffffbf\xffffffbf\xffffffc3\xffffffbf\xffffffbf\xffffffc3\xffffffbf\xffffffbf\xffffffc3\xffffffbf\xffffffbf\xffffffc3\xffffffbf\xffffffbf\xffffffc3\xffffffbf\xffffffbf\xffffffc3\xffffffbf\xffffffbf\xffffffc3\xffffffbf\xffffffbf\xffffffc3\xffffffbf\xffffffbf\xffffffc3\xffffffbf\xffffffbf\xffffffc3\xffffffbf\xffffffbf\xffffffc3\xffffffbf\xffffffbf\xffffffc3\xffffffbf\xffffffbf\xffffffc3\xffffffbf\xffffffbf\xffffffc3\xffffffbf\xffffffbf\xffffffc3\xffffffbf\xffffffbf\xffffffc3\xffffffbf\xffffffbf
[ 4294.104856] scsi17 : usb-storage 2-1.2:1.0
[ 4295.103433] scsi 17:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 0
[ 4295.114342] sr1: scsi-1 drive
[ 4295.114614] sr 17:0:0:0: Attached scsi CD-ROM sr1
[ 4295.114810] sr 17:0:0:0: Attached scsi generic sg2 type 5


The tutorial is given below 

> 
1 In order to manually connect with Reliance netconnect broadband we need two packages: wvdial (tool to make connections from a modem) and gnome-ppp (front end to the wvdial).

2 These two packages have few dependencies too. Means you need to install all of them. Since you do not have an active internet connection yet on your machine, you cant apt-get anything. So,  get a help from your friend who *might* be having an internet connection system and download the below packages.
        libwvstreams4.6-base_4.6.1-1_i386.deb
        libwvstreams4.6-extras_4.6.1-1_i386.deb
        libuniconf4.6_4.6.1-1_i386.deb
        wvdial_1.60.3_i386.deb
        gnome-ppp_0.3.23-1ubuntu2_i386.deb

3 Now bring the above downloaded files to your machine and install them (right click and select Open with GDebi package installer) in the above given order.

4 Now open terminal window and give the command lsusb which will list all USB devices attached to the laptop,. You must see the Hauwei device listed there. And then give the command dmesg to see which port our model actually using. It would be something like TTYUSB0, TTYUSB1, etc.
  
5 Now give the command sudo gnome-ppp to start the wvdial front end utility.

6 Now go to setup and in that window select the modem port (/dev/ttyUSB0 for example, which you must have seen in the 4th step using dmesg command) in the Device field and click detect. Your modem must be detected now. Then select Type as USB Modem and select the maximum available speed for the speed field.Screenshot-gnome-pp p-Setup
    
7 Click close and come back to the gnome-ppp front window. Enter the username and password (which is your device number), #777 for the number and click connect. Now you should be connected.
    
8 Here after, whenever you want to connect to internet, just open gnone-ppp and click connect. The settings must have been saved already.


---

### Post by igodspeed on 2013-08-17
Hi, 

Check out what i have done [here]("http://ubuntuforums.org/showthread.php?t=2168403&p=12760145#post12760145") which has yielded some sucess. May work for you too. Dont forget to make this post as solved.

---

