---
title: "Wireless speaker failed to connect"
date: 2016-01-03
forum: New to Ubuntu
---

### Post by Antonio_Pizarro on 2016-01-03
I installed lubuntu 14.04 in my Aspire One 725. Using bluetooth manager the device SRS-X33 appear in the screen then run the setup and choose Audio Sink then i got this messages "Device Added Sucessfully , but failed to connect.
I tried many thing following some link but still can't make this work

andres@andres-AO725:~$ pactl list short modules | grep blue
8    module-bluetooth-policy        
9    module-bluetooth-discover        
23    module-bluetooth-device    address="B8:69:C2:C6:F8:A2" path="/org/bluez/656/hci0/dev_B8_69_C2_C6_F8_A2"    
andres@andres-AO725:~$ lsusb 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 064e:d251 Suyin Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 192f:0416 Avago Technologies, Pte. ADNS-5700 Optical Mouse Controller (3-button)
Bus 005 Device 002: ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Please help me to make this work

---

### Post by kuckunniwi on 2016-01-04
Bluetooth audio in *buntu can be kind of tricky. I don't know exactly how the set-up goes in Lubuntu, but you need to make sure the connection mode is right (A2DP). I remember struggling a great deal in Kubuntu to get my working (Sony SRS-X5), and it involved changing bluetooth manager and installing some additional packages required for bluetooth audio streaming and audio management tools that weren't included in my distro (sudo apt-get install blueman bluex bluez-btsco bluez-COMPAT pulseaudio-* paprefs paman padevchooser). I don't know if this will work in Lubuntu, but here's a link to the source where I found the info: [http://www.tooleweb.ca/blog/?e=8](http://www.tooleweb.ca/blog/?e=8)

In my case though, the bluetooth connection was weak and audio quality somewhat mediocre (probably due to the quality of my wifi card's built-in bluetooth module), and I wasn't able to use it for movies because there was at least a second of delay between audio and video (thus, no lipsync). In the end, I went for a Sennheiser BTD500 (a USB bluetooth dongle that is recognized by your OS as a soundcard. All you have to do is plug it in, select it as your primary output source and put your speaker in paring mode--it does the rest). It's a bit pricey, but does a great job and ends up being worth every penny in the end. You have no idea how annoying it can get to have to reconnect, repair, delete after every reboot, as was my case. 

Having said that, maybe progress has been made in that field since then (it's been over a year), although Bluetooth has been a pending *buntu subject for quite q few years now. Nonetheless, if you have the time, it's probably worth fiddling with your system a bit to see if you can get it working. I'm sure there are also plenty of other users on these forums who are more savvy than myself who can point you in the right direction. 

Good luck! :D

---

### Post by Antonio_Pizarro on 2016-01-04
[COLOR=#000000]Hi kuckunniwi

Thank you very much for your reply and link. After I try the link I will posted the result.

Regards

Antonio


[/COLOR]

---

### Post by Antonio_Pizarro on 2016-01-05
Still having the same problem! anybody can help me?

---

### Post by James_Finigan on 2016-01-06
I had exactly this problem....I came across your post while looking for a solution. 
I have a Dell Latitude E6400 with cheap generic usb bluetooth dongle. 
Xubuntu 15.04
I wanted to listen to bluetooth through Creative Soundblaster Jam bluetooth headphones. 

I have been fully succesfull. None of this is my own work, it's a mix-up of lots of other peoples hard effort, but it's worked for me. Here's how. 

First, I made sure I had all the appropriate software & apps installed & fully up-dated. 
That's 
[COLOR=#000000]pulseaudio [/COLOR]
[COLOR=#000000]pulseaudio-module-bluetooth [/COLOR]
[COLOR=#000000]pavucontrol [/COLOR]
[COLOR=#000000]bluez[/COLOR]
[COLOR=#000000]Blueman[/COLOR]

[COLOR=#000000]Then re-booted. [/COLOR]

[COLOR=#000000]Then I took bluetooth manager out of the autostart list. This bit will be different in lubuntu from xubuntu, but it should be easily doable. [/COLOR]
[COLOR=#000000]then open bluetooth mananager. If your device is showing up as a paired device that blueman has remembered because of a previous failed connection, delete the device. 

[/COLOR]reboot

Open bluetooth manager. 
then find device using bluetooth manager 
set up new pairing, code is "0000". 
It wanted me to verify something on the bluetooth device, so I clicked a button on the headset. 


Then, once I'd done this, it paired and connected, but didn't show up as an audio option in my volume control. 
To get the volume control to manage you're bluetooth audio if it doesnt appear: 


sudo pactl load-module module-bluetooth-discover


When I entered this command, I was told:
Failure: Module initialization failed 

Someone else had also had this problem & recommended to unload the module first:


sudo pactl unload-module module-bluetooth-discover
and then load it again:


sudo pactl load-module module-bluetooth-discover
After that I was able to see the audio device in volume control.

Once I re-opened the volume controls, I needed to: 


- configuration tab: set bluetooth device to A2DP
- output device tab: ensure the bluetooth device is enabled & speakers are disabled. 
- playback tab: set browser (chrome) to bluetooth audio

Then it worked! 
And it's continued working tonight and auto-found and connected when I opened blueman and turned on my headset. 
Hope this helps.

---

### Post by Antonio_Pizarro on 2016-01-15
[SOLVED] Thank you for all the help and hint!  Finally I am able to listen music in my wireless speaker.
After multiples configurations and many tries everything is working O.K
This is what work for me:
My Bluetooth/Broadcomm Driver for my USB Dongle wasn't load into lubuntu 14:04

I got this drive for by USB Dongle
wget [https://s3.amazonaws.com/plugable/bin/fw-0a5c_21e8.hcd](https://s3.amazonaws.com/plugable/bin/fw-0a5c_21e8.hcd)

Then I copied to this library
sudo mv fw-0a5c_21e8.hcd /lib/firmware/brcm/BCM20702A0-0a5c-21e8.hcd

After that I follow the instruction from this link
[http://tuxdiary.com/2015/07/05/fix-stream-setup-failed-error-with-blueman/](http://tuxdiary.com/2015/07/05/fix-stream-setup-failed-error-with-blueman/)

Now I  am enjoying my music using my wireless speaker

---

### Post by kuckunniwi on 2016-01-18
Glad you were able to solve it! :D

---

### Post by Antonio_Pizarro on 2016-05-08
Hi all

I upgrade my "Acer Aspire One"  I installed Lubuntu 16.04 after totally removing lubuntu 14.04
The issue is that in lubuntu 14.04 my wireless speaker were working 100%.
Now in this new 16.04 environment I can't make my wireless speaker working.
Following many thread that advise to modify this file for example  /etc/bluetooth/audio.conf 
but I only have these files

rw-r--r-- 1 root root  258 Dec 24  2012 proximity.conf
-rw-r--r-- 1 root root  120 Dec 24  2012 network.conf
-rw-r--r-- 1 root root  397 May 19  2014 input.conf
-rw-r--r-- 1 root root 3874 Sep 28  2015 main.conf

what application create this audio.conf file?

these are the output for these command
aoplnx@lxn1:~$ pactl list short modules | grep blue
8    module-bluetooth-policy        
22    module-bluetooth-discover        
23    module-bluez5-discover        
aoplnx@lxn1:~$  lsusb 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:d251 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 002: ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Please any help or hint will be appreciated

Regards

Antonio

---

### Post by jeremy31 on 2016-05-09
Post the results from terminal for ```
dmesg | grep -i blue
```
I just used a bluetooth speaker on a fresh install of 16.04 so I doubt there is a need to edit anything in /etc/bluetooth

I was also able to connect and use a iHome iBT60 speaker on another laptop using 16.04 with a bluetooth dongle with the same ID as yours

---

### Post by Antonio_Pizarro on 2016-05-10
Hi All

I update my OS with lubuntu 16.04 since this will be supported unti 2021.
In my lubuntu 14.04 I found fixes for making my wireless speaker work.

Now my wireless speaker doesn't work in my lubuntu 16.04 I am trying to resolve this issue following what I did in the 14.04
Unfortunately I can't find this folder */etc/bluetooth/audio.conf*[COLOR=#333333][FONT=Source Sans Pro]  in 16.04
Do you know how can I fixed this issue.. bottom line I want to make my wireless speaker work again as before

regards

Antonio

[/FONT][/COLOR]

---

### Post by howefield on 2016-05-10
> **Antonio_Pizarro said:**
> I update my OS with lubuntu 16.04 since this will be supported unti 2021.

Just for info Lubuntu has a 3 year LTS support cycle, supported till April 2019.

> Unfortunately I can't find this folder [I]/etc/bluetooth/audio.conf

Perhaps all you have to do is create it..

```
sudo touch /etc/bluetooth/audio.conf
```

then edit it to include what you need.

---

### Post by jeremy31 on 2016-05-11
I don't think audio.conf is needed any more.  However the firmware you found might need to be renamed.  Please post result of ```
dmesg | egrep -i 'blue|firm'; pactl list short | grep blue
```

---

### Post by Antonio_Pizarro on 2016-05-13
Hi  Jeremy
This is the result of the command
	aoplnx@lxn1:~$ dmesg | egrep -i 'blue|firm'; pactl list short | grep blue

```
[    0.306932] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.330572] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    5.107399] psmouse serio2: elantech: assuming hardware version 3 (with firmware version 0x550f00)
[   17.340196] Bluetooth: Core ver 2.21
[   17.340265] Bluetooth: HCI device and connection manager initialized
[   17.340279] Bluetooth: HCI socket layer initialized
[   17.340289] Bluetooth: L2CAP socket layer initialized
[   17.340310] Bluetooth: SCO socket layer initialized
[   17.512661] Bluetooth: hci0: BCM: chip id 63
[   17.530621] Bluetooth: hci0: BCM20702A
[   17.532884] Bluetooth: hci0: BCM20702A1 (001.002.014) build 0000
[   18.314992] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-0a5c-21e8.hcd failed with error -2
[   18.315010] Bluetooth: hci0: BCM: Patch brcm/BCM20702A1-0a5c-21e8.hcd not found
[   26.587798] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.587809] Bluetooth: BNEP filters: protocol multicast
[   26.587821] Bluetooth: BNEP socket layer initialized
[  103.111309] Bluetooth: RFCOMM TTY layer initialized
[  103.111333] Bluetooth: RFCOMM socket layer initialized
[  103.111356] Bluetooth: RFCOMM ver 1.11
8	module-bluetooth-policy		
22	module-bluetooth-discover		
23	module-bluez5-discover
```		

Any help please

Regards
Antonio

---

### Post by Antonio_Pizarro on 2016-05-14
this is the result of the command

```
dmesg | grep -i blue
 16.700136] Bluetooth: Core ver 2.21
[   16.700231] Bluetooth: HCI device and connection manager initialized
[   16.700244] Bluetooth: HCI socket layer initialized
[   16.700254] Bluetooth: L2CAP socket layer initialized
[   16.700275] Bluetooth: SCO socket layer initialized
[   17.014765] Bluetooth: hci0: BCM: chip id 63
[   17.031818] Bluetooth: hci0: lxn1
[   17.033838] Bluetooth: hci0: BCM20702A1 (001.002.014) build 0000
[   17.412778] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-0a5c-21e8.hcd failed with error -2
[   17.412800] Bluetooth: hci0: BCM: Patch brcm/BCM20702A1-0a5c-21e8.hcd not found
[   27.005470] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.005484] Bluetooth: BNEP filters: protocol multicast
[   27.005502] Bluetooth: BNEP socket layer initialized
[   62.730759] Bluetooth: RFCOMM TTY layer initialized
[   62.730779] Bluetooth: RFCOMM socket layer initialized
[   62.730800] Bluetooth: RFCOMM ver 1.11
aoplnx@lxn1:/lib/firmware$ 

```
PLEASE any help or hint will be appreciated

---

### Post by Antonio_Pizarro on 2016-05-14
oplnx@lxn1:/lib/firmware$ dmesg | egrep -i 'blue|firm'; pactl list short | grep blue
```
[    0.306993] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.330488] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    5.123609] psmouse serio2: elantech: assuming hardware version 3 (with firmware version 0x550f00)
[   16.700136] Bluetooth: Core ver 2.21
[   16.700231] Bluetooth: HCI device and connection manager initialized
[   16.700244] Bluetooth: HCI socket layer initialized
[   16.700254] Bluetooth: L2CAP socket layer initialized
[   16.700275] Bluetooth: SCO socket layer initialized
[   17.014765] Bluetooth: hci0: BCM: chip id 63
[   17.031818] Bluetooth: hci0: lxn1
[   17.033838] Bluetooth: hci0: BCM20702A1 (001.002.014) build 0000
[   17.412778] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-0a5c-21e8.hcd failed with error -2
[   17.412800] Bluetooth: hci0: BCM: Patch brcm/BCM20702A1-0a5c-21e8.hcd not found
[   27.005470] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.005484] Bluetooth: BNEP filters: protocol multicast
[   27.005502] Bluetooth: BNEP socket layer initialized
[   62.730759] Bluetooth: RFCOMM TTY layer initialized
[   62.730779] Bluetooth: RFCOMM socket layer initialized
[   62.730800] Bluetooth: RFCOMM ver 1.11
8    module-bluetooth-policy        
22    module-bluetooth-discover        
23    module-bluez5-discover
```        

Any hint about this issue?

---

### Post by wildmanne39 on 2016-05-14
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by cariboo on 2016-05-14
Merged two similar threads.

---

### Post by Antonio_Pizarro on 2016-05-15
[SOLVED]
Using lubuntu 16.04 and my wireless speaker working very well!!
look like the original problem was related to the wrong drive that I installed
Because this command gave me the following information
aoplnx@lxn1:~$ lsusb
Bus 003 Device 002: ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0
I installed this drive first ....BCM20702A0-0a5c-21e8.hcd
but the failure  was pointing to different driver at the end I installed the correct one BCM20702A1-0a5c-21e8.hcd and everything is working O.K
Viva Lubuntu

Regards

Antonio

---

