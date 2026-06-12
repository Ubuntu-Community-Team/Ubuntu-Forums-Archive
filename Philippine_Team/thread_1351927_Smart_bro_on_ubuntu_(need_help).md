---
title: "Smart bro on ubuntu (need help)"
date: 2009-12-11
forum: Philippine Team
---

### Post by stormsurge on 2009-12-11
Guys!
 
I'm a newbie user of Ubuntu. I'm using Ubuntu 9.10. Do you have any idea on how to install and configure SMART Bro Prepaid Plug-it (USB Type). Please lang. Hope you could give me simple steps on how to do it kasi bago pa lang ako. Thanks!

---

### Post by pinoyskull on 2009-12-11
Network Manager should be able to detect it and will show a wizard on configuring your plug-it

---

### Post by stormsurge on 2009-12-16
> **pinoyskull said:**
> Network Manager should be able to detect it and will show a wizard on configuring your plug-it

Sorry but this did not helped me to set-up my Plug-it... Any ideas??? Anyone???

---

### Post by loell on 2009-12-16
me  wonders why your plug in modem woudn't show the network manager wizard.

in any case, your modem must be identified before any further steps are suggested.

attach the modem and post the output of **lsusb**

---

### Post by pepe machine on 2009-12-27
> attach the modem and post the output of **lsusb**thread starter ganito po ito..

plug your smartbro then go to 

applications >> accessories >> terminal 

type 
```

lsusb
```you should see something like this

> Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 19d2:**2000**
Bus 001 Device 002: ID 5986:0241 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 15d9:0a4c Unknown 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hubkung pareho tau na my 2000, perfect!! matutulungan kita.. kung hindi naman.. gagawan natin ng paraan yan..

- pepe

---

### Post by stormsurge on 2009-12-28
Thank you very much Sirs. I'll give you the output once I have my friend's plug-it again.

---

### Post by stormsurge on 2009-12-28
After typing lsusb, please see output below from my Terminal.

Bus 005 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 19d2:2000 ONDA Communication S.p.A. 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Thanks!

---

### Post by pepe machine on 2009-12-28
download [usb_modeswitch-1.0.6.tar.bz2]("http://www.draisberghof.de/usb_modeswitch/usb_modeswitch-1.0.6.tar.bz2")

extract mo, then copy usb_modeswitch sa home folder mo
go to terminal then type

```
sudo cp -i /home/[COLOR=Red]usernamemo[/COLOR]/usb_modeswitch   /usr/sbin
```copy and paste this to a textfile and save it as usb_modeswitch.conf

```

# 
# Configuration for usb_modeswitch, a mode switching tool for controlling 
# flip flop (multiple device) USB gear 
# 
# Main purpose is to trigger the switching of several known UMTS modems 
# from storage device mode ("ZeroCD TM" for use with MS Windows) to modem 
# (serial) device mode 
# 
# Detailed instructions and a friendly forum on the homepage: 
# http://www.draisberghof.de/usb_modeswitch 
# 
# News update: you want to read the paragraph about troubleshooting there 
# if you run into problems !!! 
 
 
# Just set or remove the comment signs (# and ;) in order to activate 
# your device. (Actual entries are further down, after the reference.) 
# 
# For custom settings: 
# Numbers can be decimal or hexadecimal, MessageStrings MUST be 
# hexadecimal without prepended "0x". Digits 9-16 in the known 
# MessageStrings are arbitrary; I set them to "12345678" 
 
 
# What it all means (short command line flags appended): 
# 
# 
# * DefaultVendor            -v <hex number> 
# * DefaultProduct           -p <hex number> 
# 
# This is the ID the USB device shows after having been plugged in. 
# The program needs this; if not found -> no action. 
# 
# 
# * TargetVendor             -V <hex number> 
# * TargetProduct            -P <hex number> 
# 
# These are the IDs of the USB device after successful mode switching. 
# They are optional, but I recommend to provide them for better analysis. 
# You definitely need them if you enable CheckSuccess (see below) 
# 
# 
# * TargetProductList        (file only) <comma separated hex strings> 
# 
# Like TargetProduct, but more than one possibility. Only used in automated 
# config files (in /etc/usb_modeswitch.d).  
# 
# 
# * TargetClass              -C <hex number> 
# 
# Some weird devices don't change IDs. They only switch the device class. 
# If the device has the target class -> no action (and vice versa) 
# 
# 
# * MessageEndpoint          -m <hex number> 
#  
# A kind of address inside the interface to which the "message" 
# (the sequence that does the actual switching) is directed. 
# Starting from version 0.9.7 the MessageEndpoint is autodetected 
# if not given 
# 
# 
# * MessageContent           -M <hex string> 
# 
# A hex string containing the "message" sequence; it will be 
# sent as a USB bulk transfer. 
#  
# 
# * ResponseEndpoint         -r <hex number> 
# * NeedResponse <0/1>       -n 
# 
# Some devices were reported to require receiving the response of the 
# bulk transfer to do the switching properly. Usually not needed. 
# Starting from version 1.0.0 the ResponseEndpoint is autodetected 
# if not given 
# 
# 
# * DetachStorageOnly <0/1>  -d 
# 
# Some devices just need to be detached from the usb-storage 
# driver to initiate the mode switching. Using this feature 
# instead of removing the whole usbstorage module keeps other 
# storage devices working. 
# 
# 
# * HuaweiMode <0/1>         -H 
# 
# Some Huawei devices can be switched by a special control 
# message. 
# 
# 
# * SierraMode <0/1>         -S 
# 
# Some Sierra devices can be switched by a special control 
# message. 
# 
# 
# * SonyMode <0/1>           -O 
# 
# Some Sony-Ericsson devices can be switched by a special control 
# message. This is experimental and might not have a stable result 
# 
# 
# * ResetUSB <0/1>           -R 
# 
# Some devices need a rougher treatment. If the switching seems 
# to do something (run udevmonitor), but your system does not reflect 
# it, try this somewhat brutal method to do a reset after switching. 
# Mind that if your device switched OK before, this will probably set 
# it back to storage mode ... 
# 
# 
# * Interface                -i <hex number> 
# * Configuration            -u <hex number> 
# * AltSetting               -a <hex number> 
# 
# More USB parameter to help with tricky devices and for doing lots 
# of cruel experiments ... 
# 
## Note: 
## AltSetting/Configuration changes and ResetUSB are executed after all 
## other steps and can be combined or used on their own (e.g. a reset 
## might have the same effect as a manual replug) 
# 
# 
# * InquireDevice <0|1>      -I (disables inquiry) 
# 
# The standard since 1.0.0 is to do a SCSI inquiry on the default device 
# before other actions. This might be a future way to identify a device 
# without ambiguities. If it causes trouble with your device, just disable. 
# 
# 
# * CheckSuccess             -s <number> 
# 
# Check continuously if the switch succeeded for max <number> seconds. 
# First, an interface access test: most devices vanish after 
# switching and can't be accessed anymore. 
# Second, a recount of target devices: one more than at the initial 
# count, at the same bus with a higher device number -> device 
# switched fine. 
# It's safe to give a higher value than needed; checking stops as 
# soon as the target device is found 
# 
# 
# -> All other entries are just ignored <- 
 
# Additional command line flags: 
#  
# Verbose output             -W 
# No output at all           -q 
# Other config file          -c <file> 
 
# For filling in all this information for an unknown device, 
# see instructions and links on the homepage: 
# http://www.draisberghof.de/usb_modeswitch 
# 
# If you find working codes and configurations, please contribute 
# them! 
 
 
;CheckSuccess=2 
 
######################################################## 
# ONDA MT503HS (most likely a ZTE model) 
# 
# Contributor: Lucio Asnaghi a.k.a. kRAkEn/gORe 
 
DefaultVendor=  0x19d2 
DefaultProduct= 0x2000 
 
TargetVendor=   0x19d2 
TargetProduct=  0x0002 
 
# only for reference and 0.x versions 
# MessageEndpoint=0x08 
 
MessageContent="55534243b0c8dc812000000080000a85010101180101010101000000000000" 
 
 
######################################################## 
# ONDA MT505UP (most likely a ZTE model) 
# 
# Contributor: Alex Scortegagna 
 
#;DefaultVendor=  0x19d2 
#;DefaultProduct= 0x2000 
 
#;TargetVendor=   0x19d2 
#;TargetProduct=  0x0002 
 
# only for reference and 0.x versions 
# MessageEndpoint=0x03 
 
#;MessageContent="55534243123456780000010080000a28000000001c00002000000000000000" 
 
```save mo ulit sa home folder mo

issue this code

```
sudo cp -i /home/username mo/usb_modeswitch.conf   /etc
``````
sudo /usr/sbin/usb_modeswitch
```tapos lsusb ulit dapat ung 2000 eh maging 031 onda communication blah blah

then go to

system >> preferences >> network connection

click mobile broadband then add
dapat madetect nya na ZTE na ung usb mo.

next next na lang yan bro. tapos magkakaron ka na ng smartbro default connection under mobile broadband. select it then internet na.

---

### Post by stormsurge on 2009-12-28
Thanks a lot Sir! I'll keep you posted for more updates or concerns. Thanks again!

---

### Post by pepe machine on 2009-12-28
> **stormsurge said:**
> Thanks a lot Sir! I'll keep you posted if I'll will still have some queries or concerns. Thanks again!

sure no prob.. :P

---

### Post by stormsurge on 2009-12-28
Sirs,

I have some newbie issues on this.

1. What should be the output of sudo cp -i /home/myusername/usb_modeswitch /usr/sbin?
Mine is : cp: omitting directory `/home/myusername/usb_modeswitch'

2. What should I use to save usb_modeswitch.conf? I tried using gedit Text Editor. I saved my file with the file name "usb_modeswitch.conf". 

Thank you very much!

---

### Post by pepe machine on 2009-12-28
> 1. What should be the output of sudo cp -i /home/myusername/usb_modeswitch /usr/sbin?
Mine is : cp: omitting directory `/home/myusername/usb_modeswitch'bro diba may pina download ako sayo.

extract it, open it, and just copy the "**usb_modeswitch**" na file sa loob ng folder. un lang not the whole folder..

actually walang  output na papakita yan. it will copy itself to /usr/sbin directory
check mo na lang puntahan mo ung folder na /usr/sbin

> 2. What should I use to save usb_modeswitch.conf? I tried using gedit Text Editor. I saved my file with the file name "usb_modeswitch.conf".yup, gedit po. then copy mo din sa home mo.

issue the code 

```
sudo cp -i /home/username/usb_modeswitch.conf  /etc
```it will copy usb_modeswitch.conf sa /etc directory

you can delete the usb_modeswitch and usb_modeswitch.conf sa home mo after this. kasi nailipat na natin sa tamang directory. pinalagay ko lang dun para mas maigsi ang commands sa terminal.

gudluck sana gumana na. ^_^

---

### Post by stormsurge on 2009-12-29
Still have that 2000 ONDA thing... I followed the steps correctly. Does overwriting the old files interfere with the process? 

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 19d2:2000 ONDA Communication S.p.A. 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by loell on 2009-12-29
the working   **usb_modeswitch.conf ** for  19d2:2000 ONDA Communication is in this thread,

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=202]("http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=202")

usb_modeswitch.conf is actually a configuration file hence the ".conf" extension, what you actually needed to chmod is just the  usb_modeswitch script, ie chmod +x /home_path_blah_blah/usb_modeswitch

anyhow, another way to install usb_modeswitch if you are in ubuntu Karmic is 

```
sudo apt-get install usb-modeswitch
```

after installing, just edit usb_modeswitch.conf located at /etc/usb_modeswitch.conf

ie **sudo gedit /etc/usb_modeswitch.conf**

and copy paste the working conf.

---

### Post by pepe machine on 2009-12-29
> **stormsurge said:**
> Still have that 2000 ONDA thing... I followed the steps correctly. Does overwriting the old files interfere with the process? 

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 19d2:2000 ONDA Communication S.p.A. 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


sorry i forgot. type this in terminal, whenever you plug your smartbro usb you should issue this command

```
sudo /usr/sbin/usb_modeswitch
```that should change the 2000 to 031 onda communications blah blah
and detect the usb as zte modem

---

### Post by stormsurge on 2009-12-29
Sirs!!!!

SMART BRO is working already!!!! Many thanks Sirs!!!! This will help a lot of Smart Bro subscribers! BTW, are we allowed to disseminate this info to all Smart Bro subscribers??? Like distributing the code, sharing the tar file. MANY MANY THANKS!!!!

---

### Post by pepe machine on 2009-12-29
> **stormsurge said:**
> Sirs!!!!

SMART BRO is working already!!!! Many thanks Sirs!!!! This will help a lot of Smart Bro subscribers! BTW, are we allowed to disseminate this info to all Smart Bro subscribers??? Like distributing the code, sharing the tar file. MANY MANY THANKS!!!!


hehe enjoy! yup, pwede mo ishare yan. encourage your friends to use linux..

---

### Post by stormsurge on 2009-12-29
Just to close this thread, here are the step-by-step procedures that I did.
 
I opened my Terminal and typed lsusb, I had this output:
 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 19d2:2000 ONDA Communication S.p.A. 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
 
 
In line 2 of the output, I have 2000 ONDA Communication S.p.A. For Ubuntu to detect Smart Bro ZTE Plug-it, follow this.
 
1. Download [usb_modeswitch-1.0.6.tar.bz2]("http://www.draisberghof.de/usb_modeswitch/usb_modeswitch-1.0.6.tar.bz2").
 
2. Extract the file. Now you have the usb_modeswitch-1.0.6 folder, open that folder and copy paste the usb_modeswitch file to your home folder.
 
3. Go to Applications>Accessories>Terminal. Type the code below
 
```

sudo cp -i /home/[COLOR=red]yourusername[/COLOR]/usb_modeswitch /usr/sbin 

```
 
DO NOT CLOSE THE TERMINAL!!!
 
4. Now open Applications>Accessories>gedit TextEditor. 
 
5. Copy paste the code below
 
```

# 
# Configuration for usb_modeswitch, a mode switching tool for controlling 
# flip flop (multiple device) USB gear 
# 
# Main purpose is to trigger the switching of several known UMTS modems 
# from storage device mode ("ZeroCD TM" for use with MS Windows) to modem 
# (serial) device mode 
# 
# Detailed instructions and a friendly forum on the homepage: 
# [http://www.draisberghof.de/usb_modeswitch](http://www.draisberghof.de/usb_modeswitch) 
# 
# News update: you want to read the paragraph about troubleshooting there 
# if you run into problems !!! 
 
 
# Just set or remove the comment signs (# and ;) in order to activate 
# your device. (Actual entries are further down, after the reference.) 
# 
# For custom settings: 
# Numbers can be decimal or hexadecimal, MessageStrings MUST be 
# hexadecimal without prepended "0x". Digits 9-16 in the known 
# MessageStrings are arbitrary; I set them to "12345678" 
 
 
# What it all means (short command line flags appended): 
# 
# 
# * DefaultVendor -v <hex number> 
# * DefaultProduct -p <hex number> 
# 
# This is the ID the USB device shows after having been plugged in. 
# The program needs this; if not found -> no action. 
# 
# 
# * TargetVendor -V <hex number> 
# * TargetProduct -P <hex number> 
# 
# These are the IDs of the USB device after successful mode switching. 
# They are optional, but I recommend to provide them for better analysis. 
# You definitely need them if you enable CheckSuccess (see below) 
# 
# 
# * TargetProductList (file only) <comma separated hex strings> 
# 
# Like TargetProduct, but more than one possibility. Only used in automated 
# config files (in /etc/usb_modeswitch.d). 
# 
# 
# * TargetClass -C <hex number> 
# 
# Some weird devices don't change IDs. They only switch the device class. 
# If the device has the target class -> no action (and vice versa) 
# 
# 
# * MessageEndpoint -m <hex number> 
# 
# A kind of address inside the interface to which the "message" 
# (the sequence that does the actual switching) is directed. 
# Starting from version 0.9.7 the MessageEndpoint is autodetected 
# if not given 
# 
# 
# * MessageContent -M <hex string> 
# 
# A hex string containing the "message" sequence; it will be 
# sent as a USB bulk transfer. 
# 
# 
# * ResponseEndpoint -r <hex number> 
# * NeedResponse <0/1> -n 
# 
# Some devices were reported to require receiving the response of the 
# bulk transfer to do the switching properly. Usually not needed. 
# Starting from version 1.0.0 the ResponseEndpoint is autodetected 
# if not given 
# 
# 
# * DetachStorageOnly <0/1> -d 
# 
# Some devices just need to be detached from the usb-storage 
# driver to initiate the mode switching. Using this feature 
# instead of removing the whole usbstorage module keeps other 
# storage devices working. 
# 
# 
# * HuaweiMode <0/1> -H 
# 
# Some Huawei devices can be switched by a special control 
# message. 
# 
# 
# * SierraMode <0/1> -S 
# 
# Some Sierra devices can be switched by a special control 
# message. 
# 
# 
# * SonyMode <0/1> -O 
# 
# Some Sony-Ericsson devices can be switched by a special control 
# message. This is experimental and might not have a stable result 
# 
# 
# * ResetUSB <0/1> -R 
# 
# Some devices need a rougher treatment. If the switching seems 
# to do something (run udevmonitor), but your system does not reflect 
# it, try this somewhat brutal method to do a reset after switching. 
# Mind that if your device switched OK before, this will probably set 
# it back to storage mode ... 
# 
# 
# * Interface -i <hex number> 
# * Configuration -u <hex number> 
# * AltSetting -a <hex number> 
# 
# More USB parameter to help with tricky devices and for doing lots 
# of cruel experiments ... 
# 
## Note: 
## AltSetting/Configuration changes and ResetUSB are executed after all 
## other steps and can be combined or used on their own (e.g. a reset 
## might have the same effect as a manual replug) 
# 
# 
# * InquireDevice <0|1> -I (disables inquiry) 
# 
# The standard since 1.0.0 is to do a SCSI inquiry on the default device 
# before other actions. This might be a future way to identify a device 
# without ambiguities. If it causes trouble with your device, just disable. 
# 
# 
# * CheckSuccess -s <number> 
# 
# Check continuously if the switch succeeded for max <number> seconds. 
# First, an interface access test: most devices vanish after 
# switching and can't be accessed anymore. 
# Second, a recount of target devices: one more than at the initial 
# count, at the same bus with a higher device number -> device 
# switched fine. 
# It's safe to give a higher value than needed; checking stops as 
# soon as the target device is found 
# 
# 
# -> All other entries are just ignored <- 
 
# Additional command line flags: 
# 
# Verbose output -W 
# No output at all -q 
# Other config file -c <file> 
 
# For filling in all this information for an unknown device, 
# see instructions and links on the homepage: 
# [http://www.draisberghof.de/usb_modeswitch](http://www.draisberghof.de/usb_modeswitch) 
# 
# If you find working codes and configurations, please contribute 
# them! 
 
 
;CheckSuccess=2 
 
######################################################## 
# ONDA MT503HS (most likely a ZTE model) 
# 
# Contributor: Lucio Asnaghi a.k.a. kRAkEn/gORe 
 
DefaultVendor= 0x19d2 
DefaultProduct= 0x2000 
 
TargetVendor= 0x19d2 
TargetProduct= 0x0002 
 
# only for reference and 0.x versions 
# MessageEndpoint=0x08 
 
MessageContent="55534243b0c8dc812000000080000a85010101180101010101000000000000" 
 
 
######################################################## 
# ONDA MT505UP (most likely a ZTE model) 
# 
# Contributor: Alex Scortegagna 
 
#;DefaultVendor= 0x19d2 
#;DefaultProduct= 0x2000 
 
#;TargetVendor= 0x19d2 
#;TargetProduct= 0x0002 
 
# only for reference and 0.x versions 
# MessageEndpoint=0x03 
 
#;MessageContent="55534243123456780000010080000a28000000001c00002000000000000000"

```
 
6. Save it using the file name "usb_modeswitch.conf" to your home folder.
 
7. Go back to the Terminal and issue code below:
 
```

sudo cp -i /home/[COLOR=red]yourusername[/COLOR]/usb_modeswitch.conf /etc 

```
 
8. Now, please ensure that your Smart Bro plug-it is plugged in the USB port. Type the code below:
 
```

sudo /usr/sbin/usb_modeswitch 

```
 
Then, type lsusb to the terminal and now you will see something like this:
 
Bus 001 Device 006: ID 19d2:0031 ONDA Communication S.p.A. 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
*As you notice, I have 0031 ONDA Communication S.p.A. from 2000 which more ikely means that my device is recognizable as ZTE Modem.
 
9. Go to System>Preferences>Network Connection.
 
10. Make sure you encode the following details
 
Country: Philippines
Provider: Smart
*Enter Smart manually (Do not choose Smart from the given provider list)
Selected Plan APN: Smartbro
Access Number: *99#
*NO USERNAME AND PASSWORD MUST BE ENCODED.
 
Now you can connect via Mobile Broadband!!!!
 
If you decided to disconnect and re-use your Plug-it for other sessions, connect your plug-it, open the Terminal and type the code in number 8. Now you should be able to connect again.

---

### Post by loell on 2009-12-29
sorry to be insistent but,

```
sudo chmod +x /home/yourusername/usb_modeswitch.conf 
```

is wrong, you really don't need to do that with a configuration file.

---

### Post by stormsurge on 2009-12-29
Already edited it Sir. Thanks for your inputs.

---

### Post by pepe machine on 2009-12-29
> **loell said:**
> sorry to be insistent but,

```
sudo chmod +x /home/yourusername/usb_modeswitch.conf 
```is wrong, you really don't need to do that with a configuration file.

ay ganun ba hehe sorry, edit ko na lang.. base lang kasi sa mga nakalikot ko ung tinuturo ko. pasensya na

---

### Post by loell on 2009-12-29
no probs naman. :)

---

### Post by stormsurge on 2009-12-29
> **pepe machine said:**
> hehe enjoy! yup, pwede mo ishare yan. encourage your friends to use linux..

Thanks! This will really help Smart Bro subscribers to use Linux. Happy New Year to all!

---

### Post by Samhain13 on 2009-12-29
It would be nice if this thread was marked as "SOLVED". It bet that would encourage others to look here when they see the thread in their search results for "ubuntu smart bro help".

**Happy New Year!**

---

### Post by remkarl on 2010-01-01
Thanks a lot it works...:D

---

### Post by stormsurge on 2010-01-01
> **remkarl said:**
> Thanks a lot it works...:D


Thanks to our good Sirs! :D

---

### Post by pepe machine on 2010-01-01
> **remkarl said:**
> Thanks a lot it works...:D

hehe enjoy your ubuntu!

---

### Post by aljoriz on 2010-01-07
2kinds ang smartbro prepaid plug-it.  The New black usb or the old white usb, Am I correct to assume that this is for the white one?

---

### Post by stormsurge on 2010-01-07
> **aljoriz said:**
> 2kinds ang smartbro prepaid plug-it. The New black usb or the old white usb, Am I correct to assume that this is for the white one?
 
 
This is for the latest model (ZTE), the black one. As per our testing, the white plug-it (Huwawei) can be auto detected by Ubuntu.

---

### Post by justoxdizaola on 2010-01-12
[http://knightlust.blogspot.com/2009/06/smartbro-zte-mf627-on-ubuntu-jaunty.html](http://knightlust.blogspot.com/2009/06/smartbro-zte-mf627-on-ubuntu-jaunty.html)

mga sir, sinundan ko po ang procedure na ito sa karmic. tumatalab po siya, connected daw po, tapos ung led light ng stick is blinking, so may connection talaga. HINDI LANG PO AKO MAKAPAG-INTERNET sa FIREFOX! :( *ung allcaps po for emphasis, di po for screaming* 

anyone can help me? un lang po kc ung net access ko sa dorm ko sa UP Diliman.

Salamat ng marami.

---

### Post by stormsurge on 2010-01-12
Have you tried using Google Chrome or other Browser?

---

### Post by justoxdizaola on 2010-01-12
sir will try konqueror mamayang gabi.

uhm, may wifi card din po kc aq e, does that cause conflicts? parang me nabasa po kc akong gnyan s webpage.

if ever, i hope to meet members near diliman para mapagtulungan 'to and maevaluate ng personalan.

---

### Post by stormsurge on 2010-01-12
Try to follow the procedures provided in page 2 of this forum. I use Karmic and find this process very effective. Please keep me posted. Thanks!

---

### Post by justoxdizaola on 2010-01-12
Noted sir, will report on friday. Waiting for free time.

---

### Post by topsykretts on 2010-01-13
hello po..sinunod ko na po lahat ng nsa instructions but it still doesnt detect my smartbro..pwedend patulong?eto yun lumalabas pag tnype ko sa terminal yun 
sudo /usr/sbin/usb_modeswitch(note:nkasaksak na po yun smartbro):


Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 003 on bus 001 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
 Could not get INQUIRY response (error -16)

USB description data (for identification)
-------------------------
Manufacturer: ZTE,Incorporated
     Product: ZTE CDMA Technologies MSM
  Serial No.: 1234567890ABCDEF
-------------------------
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 Sending the message returned error -110. Trying to continue
-> Run lsusb to note any changes. Bye.

tapos eto naman po ang lumalabas pag tnype ko lsusb sa terminal:

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 19d2:2000 ONDA Communication S.p.A. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

ayun..sa tingin nyo ano po ang gnagwa ko mali?salamat po!!

---

### Post by topsykretts on 2010-01-13
oh and if its any help..im running karmic koala 9.10 32bit with generic pae kernel 2.6.31-15

---

### Post by stormsurge on 2010-01-13
Sir,
 
Did you see the "ZTE modem has been mounted" (something like that) pop-up? Try to encode the code in number 8. Type lsusb after 2 minutes. Then, provide us the output again. Thanks!

---

### Post by topsykretts on 2010-01-13
like i said in my last post i did type in sudo /usr/sbin/usb_modeswitch with the smartbro usb plugged in and this is what came out:

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 003 on bus 001 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
 Could not get INQUIRY response (error -16)

USB description data (for identification)
-------------------------
Manufacturer: ZTE,Incorporated
     Product: ZTE CDMA Technologies MSM
  Serial No.: 1234567890ABCDEF
-------------------------
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 Sending the message returned error -110. Trying to continue
-> Run lsusb to note any changes. Bye.

no "ZTE MODEM HAS BEEN MOUNTED" or something like that didnt pop up..then when i type in "lsusb" on the terminal i get this output:
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 19d2:2000 ONDA Communication S.p.A. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by loell on 2010-01-13
probably show us your **usb_modeswitch.conf**

cat /etc/usb_modeswitch.conf

---

### Post by topsykretts on 2010-01-13
> **loell said:**
> probably show us your **usb_modeswitch.conf**

cat /etc/usb_modeswitch.conf

this is the output after putting in cat /etc/usb_modeswitch.conf in the terminal:

marc@marc-laptop:~$ cat /etc/usb_modeswitch.conf
# 
# Configuration for usb_modeswitch, a mode switching tool for controlling 
# flip flop (multiple device) USB gear 
# 
# Main purpose is to trigger the switching of several known UMTS modems 
# from storage device mode ("ZeroCD TM" for use with MS Windows) to modem 
# (serial) device mode 
# 
# Detailed instructions and a friendly forum on the homepage: 
# [http://www.draisberghof.de/usb_modeswitch](http://www.draisberghof.de/usb_modeswitch) 
# 
# News update: you want to read the paragraph about troubleshooting there 
# if you run into problems !!! 
 
 
# Just set or remove the comment signs (# and ;) in order to activate 
# your device. (Actual entries are further down, after the reference.) 
# 
# For custom settings: 
# Numbers can be decimal or hexadecimal, MessageStrings MUST be 
# hexadecimal without prepended "0x". Digits 9-16 in the known 
# MessageStrings are arbitrary; I set them to "12345678" 
 
 
# What it all means (short command line flags appended): 
# 
# 
# * DefaultVendor -v <hex number> 
# * DefaultProduct -p <hex number> 
# 
# This is the ID the USB device shows after having been plugged in. 
# The program needs this; if not found -> no action. 
# 
# 
# * TargetVendor -V <hex number> 
# * TargetProduct -P <hex number> 
# 
# These are the IDs of the USB device after successful mode switching. 
# They are optional, but I recommend to provide them for better analysis. 
# You definitely need them if you enable CheckSuccess (see below) 
# 
# 
# * TargetProductList (file only) <comma separated hex strings> 
# 
# Like TargetProduct, but more than one possibility. Only used in automated 
# config files (in /etc/usb_modeswitch.d). 
# 
# 
# * TargetClass -C <hex number> 
# 
# Some weird devices don't change IDs. They only switch the device class. 
# If the device has the target class -> no action (and vice versa) 
# 
# 
# * MessageEndpoint -m <hex number> 
# 
# A kind of address inside the interface to which the "message" 
# (the sequence that does the actual switching) is directed. 
# Starting from version 0.9.7 the MessageEndpoint is autodetected 
# if not given 
# 
# 
# * MessageContent -M <hex string> 
# 
# A hex string containing the "message" sequence; it will be 
# sent as a USB bulk transfer. 
# 
# 
# * ResponseEndpoint -r <hex number> 
# * NeedResponse <0/1> -n 
# 
# Some devices were reported to require receiving the response of the 
# bulk transfer to do the switching properly. Usually not needed. 
# Starting from version 1.0.0 the ResponseEndpoint is autodetected 
# if not given 
# 
# 
# * DetachStorageOnly <0/1> -d 
# 
# Some devices just need to be detached from the usb-storage 
# driver to initiate the mode switching. Using this feature 
# instead of removing the whole usbstorage module keeps other 
# storage devices working. 
# 
# 
# * HuaweiMode <0/1> -H 
# 
# Some Huawei devices can be switched by a special control 
# message. 
# 
# 
# * SierraMode <0/1> -S 
# 
# Some Sierra devices can be switched by a special control 
# message. 
# 
# 
# * SonyMode <0/1> -O 
# 
# Some Sony-Ericsson devices can be switched by a special control 
# message. This is experimental and might not have a stable result 
# 
# 
# * ResetUSB <0/1> -R 
# 
# Some devices need a rougher treatment. If the switching seems 
# to do something (run udevmonitor), but your system does not reflect 
# it, try this somewhat brutal method to do a reset after switching. 
# Mind that if your device switched OK before, this will probably set 
# it back to storage mode ... 
# 
# 
# * Interface -i <hex number> 
# * Configuration -u <hex number> 
# * AltSetting -a <hex number> 
# 
# More USB parameter to help with tricky devices and for doing lots 
# of cruel experiments ... 
# 
## Note: 
## AltSetting/Configuration changes and ResetUSB are executed after all 
## other steps and can be combined or used on their own (e.g. a reset 
## might have the same effect as a manual replug) 
# 
# 
# * InquireDevice <0|1> -I (disables inquiry) 
# 
# The standard since 1.0.0 is to do a SCSI inquiry on the default device 
# before other actions. This might be a future way to identify a device 
# without ambiguities. If it causes trouble with your device, just disable. 
# 
# 
# * CheckSuccess -s <number> 
# 
# Check continuously if the switch succeeded for max <number> seconds. 
# First, an interface access test: most devices vanish after 
# switching and can't be accessed anymore. 
# Second, a recount of target devices: one more than at the initial 
# count, at the same bus with a higher device number -> device 
# switched fine. 
# It's safe to give a higher value than needed; checking stops as 
# soon as the target device is found 
# 
# 
# -> All other entries are just ignored <- 
 
# Additional command line flags: 
# 
# Verbose output -W 
# No output at all -q 
# Other config file -c <file> 
 
# For filling in all this information for an unknown device, 
# see instructions and links on the homepage: 
# [http://www.draisberghof.de/usb_modeswitch](http://www.draisberghof.de/usb_modeswitch) 
# 
# If you find working codes and configurations, please contribute 
# them! 
 
 
;CheckSuccess=2 
 
######################################################## 
# ONDA MT503HS (most likely a ZTE model) 
# 
# Contributor: Lucio Asnaghi a.k.a. kRAkEn/gORe 
 
DefaultVendor= 0x19d2 
DefaultProduct= 0x2000 
 
TargetVendor= 0x19d2 
TargetProduct= 0x0002 
 
# only for reference and 0.x versions 
# MessageEndpoint=0x08 
 
MessageContent="55534243b0c8dc812000000080000a85010101180101010101000000000000" 
 
 
######################################################## 
# ONDA MT505UP (most likely a ZTE model) 
# 
# Contributor: Alex Scortegagna 
 
#;DefaultVendor= 0x19d2 
#;DefaultProduct= 0x2000 
 
#;TargetVendor= 0x19d2 
#;TargetProduct= 0x0002 
 
# only for reference and 0.x versions 
# MessageEndpoint=0x03 
 
#;MessageContent="55534243123456780000010080000a28000000001c00002000000000000000"

---

### Post by loell on 2010-01-13
try this command, see if the modem can be recognized.


```
sudo usb_modeswitch -v 0x19d2 -p 0x2000 -M 55534243123456782400000080000C85000000240000000000000000000000 -R 1
```

---

### Post by topsykretts on 2010-01-13
> **loell said:**
> try this command, see if the modem can be recognized.


```
sudo usb_modeswitch -v 0x19d2 -p 0x2000 -M 55534243123456782400000080000C85000000240000000000000000000000 -R 1
```


hindi pa din ma recognize e..this is what came out when i nput the code:

marc@marc-laptop:~$ sudo usb_modeswitch -v 0x19d2 -p 0x2000 -M 55534243123456782400000080000C85000000240000000000000000000000 -R 1

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for default devices ...
 Found default devices (1)
Accessing device 003 on bus 001 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
 Could not get INQUIRY response (error -16)

Device description data (identification)
-------------------------
Manufacturer: ZTE,Incorporated
     Product: ZTE CDMA Technologies MSM
  Serial No.: 1234567890ABCDEF
-------------------------
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 Sending the message returned error -110. Trying to continue
Resetting usb device .
 OK, device was reset
-> Run lsusb to note any changes. Bye.


tapos eto naman pag lsusb:

marc@marc-laptop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 19d2:2000 ONDA Communication S.p.A. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

hay sana sun broadband nalang binili ko..haha

---

### Post by loell on 2010-01-13
talagang ayaw nyang mag-transform, heheh

ok naman ba sa windows?

---

### Post by manilaph on 2010-01-13
Based on all these "hardships" seen installing and using the Smarbro ZTE modem stick... I strongly suggest that if you do not yet have the ZTE Black modem of Smartbro... to either:

1) Look for the white Huawei E156C model which was the model right before Smartbro switched to the ZTE model (most likely because the Huawei is "open-linable").

or

2) Get a Globe Tattoo Huawei E1552 model.

Both these Huawei models work out of the box. All you need to do is to do is to change the APN (default APNs are wrong) and just choose PAP.

This is very easily done using the Graphical User Interface and no need to do "codes" which newbies have so much difficulty to use.

---

### Post by topsykretts on 2010-01-13
> **loell said:**
> talagang ayaw nyang mag-transform, heheh

ok naman ba sa windows?


ng transform na!!hahaha..sometimes it take 2 tries in the terminal for it to work...now i dont mind kung evertime na mg llog in ako sa ubuntu at gusto ko gamitin yun smartbro ko i iinput ko yun code..but for the sake of making life easier..is there a way that i can do this with one click of a button??like a shortcut on the desktop..i plug in my smartbro i click the shortcut and it works??or like a dock in awn(its my current dock)when i click it it works??naiintindihan m ba ibg ko sbhn??hahah..im sorry

---

### Post by stormsurge on 2010-01-14
Bro,
 
Try to enable the "Auto Connect" in the startup. Make sure that the modem is plugged in your USB port before opening your computer. Most of the time Ubuntu will automatically connects you to the net via Smart Bro.

---

### Post by loell on 2010-01-14
> **topsykretts said:**
> ng transform na!!hahaha..sometimes it take 2 tries in the terminal for it to work...now i dont mind kung evertime na mg llog in ako sa ubuntu at gusto ko gamitin yun smartbro ko i iinput ko yun code..but for the sake of making life easier..is there a way that i can do this with one click of a button??like a shortcut on the desktop..i plug in my smartbro i click the shortcut and it works??or like a dock in awn(its my current dock)when i click it it works??naiintindihan m ba ibg ko sbhn??hahah..im sorry

it might be better what stormsurge did with the autoconnect method,

pero kung gusto mo ng icon,

right click --> create shortcut --> (optional) choose an icon of your liking ==> Select Type: Application in terminal  ==> at the command field put,  **sudo usb_modeswitch -v 0x19d2 -p 0x2000 -M 55534243123456782400000080000C85000000240000000000000000000000 -R I **

---

### Post by topsykretts on 2010-01-14
hey guys..ok na i used an icon instead kasi i want to be able to manually connect to smartbro..thanks guys sa tulong!!

---

### Post by justoxdizaola on 2010-01-28
I can do this in gnome, but what about KDE? d ako makakonek pag KDE. d q alam ung style e. *DUMB* thanks.

*ADDED info: Did as you asked me to, ung page 2. worked perfectly. kaso, di ko magawa sa KDE kaya sa gnome lng aq nkkpag-net. HUHUHU. patulong nmn po pr s mga kubuntu natin... gaya ko. slamat po.

---

### Post by aljoriz on 2010-01-29
someone must update this guide kasi wala na yung l
Here's what I did I followed what sir Loell said on page 2
Since this is so simple it might work on KUBUNTU

make sure ur lapy has an existing net connection (via wi-fi or ethernet)
go to the terminal 
type: sudo apt-get install usb-modeswitch
go to page 2 of this thread and make the usb_modeswitch.conf with the  recommended settings

tapos go to system>net connections>mobile broadband>add>Philippines>Manually write Smartbro>APN:Smartbro tapos sa terminal
sudo /usr/sbin/usb_modeswitch
sa gilid ng date time click sa connection and select Smart Connection1

ang tanong ko lang sa connection information ang interface eh GSM so how do I use the HSDPA something?

---

### Post by aljoriz on 2010-01-29
Talk about weirdness.  I bought a Smartbro, since I was so hardheaded.  It worked well on the laptop once but when I tried the same technique with the smartbro on my pc, I get the following error after using the command:  sudo /usr/sbin/usb_modeswitch

* usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 010 on bus 001 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
 Could not get INQUIRY response (error -16)

Device description data (identification)
-------------------------
Manufacturer: ZTE,Incorporated
     Product: ZTE CDMA Technologies MSM
  Serial No.: 1234567890ABCDEF
-------------------------
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 Sending the message returned error -110. Trying to continue
-> Run lsusb to note any changes. Bye.

Mas malala pa pag nasaksak ang smartbro dongle it would crash my GUI, at pag na reboot the bios would say something like resetting the CPU.

Pag nilipat ko sa netbook, the same error but I noticed that the dongle would reset kasi yung led nagiging red (meaning initializing) and if it resets and sudo usb_modswitch umaandar siya

---

### Post by ariscanete on 2010-01-30
wow...is this method applies to Ubuntu versions 8.04, 8.10 and 9.40?  thanks....

i really thought it isn't possible to connect Smartbro Prepaid to Ubuntu Linux..at least Pag-ASA

---

### Post by aljoriz on 2010-02-01
> **ariscanete said:**
> wow...is this method applies to Ubuntu versions 8.04, 8.10 and 9.40?  thanks....

i really thought it isn't possible to connect Smartbro Prepaid to Ubuntu Linux..at least Pag-ASA

 FOR INTERPID: Goto Software Sources>others (add the following) ```
deb http://ppa.launchpad.net/liamgh/ppa/ubuntu intrepid main
``` PRESS add again ```
deb-src http://ppa.launchpad.net/liamgh/ppa/ubuntu intrepid main
``` Don't close the Software Sources  go to this link: look for the signing key SAVE AS and save it to your home directory, it will be saved as lghppa-public.key  go back to software sources>Authentication>Import Key, go to your home directory and look for lghppa-public.key use it and then close the software sources   Go to Terminal ```
sudo gedit /etc/usb_modeswitch.conf
```  Go to page 2 of this thread and copy, past the working usb_modeswitch.conf and save the file.   Plug smartbro, at network manager copy the APN settings found on page 2

---

### Post by mikedats on 2010-02-04
smart on ubuntu was simple. found out by mistake actually, after configuring it, and inserting the stick in the usb, notice you will see an icon appear on the desktop. 

right click it and eject it. do not remove the stick. leave it plugged in. notice the light on the stick will turn off after a few seconds, then will turn back on red i believe. then depending where you are, green or blue, the light will be steady. a few seconds later, it will start blinking, and it does, you have established connection.

---

### Post by lod2 on 2010-03-02
> **stormsurge said:**
> Guys!
 
I'm a newbie user of Ubuntu. I'm using Ubuntu 9.10. Do you have any idea on how to install and configure SMART Bro Prepaid Plug-it (USB Type). Please lang. Hope you could give me simple steps on how to do it kasi bago pa lang ako. Thanks!

What modem type are you using? if it is ZTE MF627, you can follow this link:

[http://ubuntuforums.org/showthread.php?t=1419799&highlight=zte+mf627](http://ubuntuforums.org/showthread.php?t=1419799&highlight=zte+mf627)

---

### Post by bx2gp1 on 2010-04-08
guys its running, thanks to you all, neway, how bout the interface? so that i can use the SMS feature of the smartbro usb, and how can i use the 3G or HSDPA? it only display GSM.

---

### Post by aljoriz on 2010-04-09
Depende sa color ng modem yan.  

for ZTE modems:
blinking green means hsdpa otherwise its 3g or that other lower signal whose name I forgot

for Huawei modems:
blinking blue is hspda, steady blue means 3g.  

Read the user manual for more details.  AFAIK you can not tell linux to set this modem to work for only one signal.

---

### Post by bx2gp1 on 2010-04-09
ic, so how bout the SMS feature? can we still use that in ubuntu? sending and reading sms directly to your computer.

---

### Post by kstella on 2010-04-24
Gagana din ba ang page 2 solution pag wicd ang gamit ko, or do I need to switch back?

---

### Post by apolloltiujr on 2010-09-15
Sun Broadband on Ubuntu 10.04

If you are using Sun Broadband Wireless (tested on Huawei E1550) and want it to work on Ubuntu 10.04 (Lucid Lynx), just install the linux-backports-modules-headers-lucid-generic package and the usb-modeswitch package.
view plain
print?
    $ sudo apt-get install linux-backports-modules-headers-lucid-generic usb-modeswitch

After installing, reboot.

Plug in the Sun Broadband. Then, a notification &#8220;New Mobile Broadband Connection&#8221; should appear. Follow the wizard dialog (you can just click next since the default values should be alright). Then, you should be connected now. 

Connection Name: Digitel (Sun Cellular) Connection

Mobile: *99#
Username:
Password:

Advance
APN: fbband
Network:
Pin:

Just Try It. Iyon $ Sudo gagawin mo iyan sa Terminal nasa applications + accessories + Terminal.... Copy paste and enter mo lang then pag humingi ng Password lagay  mo password mo
Then YM mo ako kung meron hindi gumana [email]h2opluswtc@yahoo.com[/email]

---

### Post by bedroomCod3r on 2011-04-05
> **stormsurge said:**
> Just to close this thread, here are the step-by-step procedures that I did.
 
I opened my Terminal and typed lsusb, I had this output:
 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 19d2:2000 ONDA Communication S.p.A. 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
 
 
In line 2 of the output, I have 2000 ONDA Communication S.p.A. For Ubuntu to detect Smart Bro ZTE Plug-it, follow this.
 
1. Download [usb_modeswitch-1.0.6.tar.bz2]("http://www.draisberghof.de/usb_modeswitch/usb_modeswitch-1.0.6.tar.bz2").
 
2. Extract the file. Now you have the usb_modeswitch-1.0.6 folder, open that folder and copy paste the usb_modeswitch file to your home folder.
 
3. Go to Applications>Accessories>Terminal. Type the code below
 
```

sudo cp -i /home/[COLOR=red]yourusername[/COLOR]/usb_modeswitch /usr/sbin 

```DO NOT CLOSE THE TERMINAL!!!
 
4. Now open Applications>Accessories>gedit TextEditor. 
 
5. Copy paste the code below
 
```

# 
# Configuration for usb_modeswitch, a mode switching tool for controlling 
# flip flop (multiple device) USB gear 
# 
# Main purpose is to trigger the switching of several known UMTS modems 
# from storage device mode ("ZeroCD TM" for use with MS Windows) to modem 
# (serial) device mode 
# 
# Detailed instructions and a friendly forum on the homepage: 
# [http://www.draisberghof.de/usb_modeswitch](http://www.draisberghof.de/usb_modeswitch) 
# 
# News update: you want to read the paragraph about troubleshooting there 
# if you run into problems !!! 
 
 
# Just set or remove the comment signs (# and ;) in order to activate 
# your device. (Actual entries are further down, after the reference.) 
# 
# For custom settings: 
# Numbers can be decimal or hexadecimal, MessageStrings MUST be 
# hexadecimal without prepended "0x". Digits 9-16 in the known 
# MessageStrings are arbitrary; I set them to "12345678" 
 
 
# What it all means (short command line flags appended): 
# 
# 
# * DefaultVendor -v <hex number> 
# * DefaultProduct -p <hex number> 
# 
# This is the ID the USB device shows after having been plugged in. 
# The program needs this; if not found -> no action. 
# 
# 
# * TargetVendor -V <hex number> 
# * TargetProduct -P <hex number> 
# 
# These are the IDs of the USB device after successful mode switching. 
# They are optional, but I recommend to provide them for better analysis. 
# You definitely need them if you enable CheckSuccess (see below) 
# 
# 
# * TargetProductList (file only) <comma separated hex strings> 
# 
# Like TargetProduct, but more than one possibility. Only used in automated 
# config files (in /etc/usb_modeswitch.d). 
# 
# 
# * TargetClass -C <hex number> 
# 
# Some weird devices don't change IDs. They only switch the device class. 
# If the device has the target class -> no action (and vice versa) 
# 
# 
# * MessageEndpoint -m <hex number> 
# 
# A kind of address inside the interface to which the "message" 
# (the sequence that does the actual switching) is directed. 
# Starting from version 0.9.7 the MessageEndpoint is autodetected 
# if not given 
# 
# 
# * MessageContent -M <hex string> 
# 
# A hex string containing the "message" sequence; it will be 
# sent as a USB bulk transfer. 
# 
# 
# * ResponseEndpoint -r <hex number> 
# * NeedResponse <0/1> -n 
# 
# Some devices were reported to require receiving the response of the 
# bulk transfer to do the switching properly. Usually not needed. 
# Starting from version 1.0.0 the ResponseEndpoint is autodetected 
# if not given 
# 
# 
# * DetachStorageOnly <0/1> -d 
# 
# Some devices just need to be detached from the usb-storage 
# driver to initiate the mode switching. Using this feature 
# instead of removing the whole usbstorage module keeps other 
# storage devices working. 
# 
# 
# * HuaweiMode <0/1> -H 
# 
# Some Huawei devices can be switched by a special control 
# message. 
# 
# 
# * SierraMode <0/1> -S 
# 
# Some Sierra devices can be switched by a special control 
# message. 
# 
# 
# * SonyMode <0/1> -O 
# 
# Some Sony-Ericsson devices can be switched by a special control 
# message. This is experimental and might not have a stable result 
# 
# 
# * ResetUSB <0/1> -R 
# 
# Some devices need a rougher treatment. If the switching seems 
# to do something (run udevmonitor), but your system does not reflect 
# it, try this somewhat brutal method to do a reset after switching. 
# Mind that if your device switched OK before, this will probably set 
# it back to storage mode ... 
# 
# 
# * Interface -i <hex number> 
# * Configuration -u <hex number> 
# * AltSetting -a <hex number> 
# 
# More USB parameter to help with tricky devices and for doing lots 
# of cruel experiments ... 
# 
## Note: 
## AltSetting/Configuration changes and ResetUSB are executed after all 
## other steps and can be combined or used on their own (e.g. a reset 
## might have the same effect as a manual replug) 
# 
# 
# * InquireDevice <0|1> -I (disables inquiry) 
# 
# The standard since 1.0.0 is to do a SCSI inquiry on the default device 
# before other actions. This might be a future way to identify a device 
# without ambiguities. If it causes trouble with your device, just disable. 
# 
# 
# * CheckSuccess -s <number> 
# 
# Check continuously if the switch succeeded for max <number> seconds. 
# First, an interface access test: most devices vanish after 
# switching and can't be accessed anymore. 
# Second, a recount of target devices: one more than at the initial 
# count, at the same bus with a higher device number -> device 
# switched fine. 
# It's safe to give a higher value than needed; checking stops as 
# soon as the target device is found 
# 
# 
# -> All other entries are just ignored <- 
 
# Additional command line flags: 
# 
# Verbose output -W 
# No output at all -q 
# Other config file -c <file> 
 
# For filling in all this information for an unknown device, 
# see instructions and links on the homepage: 
# [http://www.draisberghof.de/usb_modeswitch](http://www.draisberghof.de/usb_modeswitch) 
# 
# If you find working codes and configurations, please contribute 
# them! 
 
 
;CheckSuccess=2 
 
######################################################## 
# ONDA MT503HS (most likely a ZTE model) 
# 
# Contributor: Lucio Asnaghi a.k.a. kRAkEn/gORe 
 
DefaultVendor= 0x19d2 
DefaultProduct= 0x2000 
 
TargetVendor= 0x19d2 
TargetProduct= 0x0002 
 
# only for reference and 0.x versions 
# MessageEndpoint=0x08 
 
MessageContent="55534243b0c8dc812000000080000a85010101180101010101000000000000" 
 
 
######################################################## 
# ONDA MT505UP (most likely a ZTE model) 
# 
# Contributor: Alex Scortegagna 
 
#;DefaultVendor= 0x19d2 
#;DefaultProduct= 0x2000 
 
#;TargetVendor= 0x19d2 
#;TargetProduct= 0x0002 
 
# only for reference and 0.x versions 
# MessageEndpoint=0x03 
 
#;MessageContent="55534243123456780000010080000a28000000001c00002000000000000000"

```6. Save it using the file name "usb_modeswitch.conf" to your home folder.
 
7. Go back to the Terminal and issue code below:
 
```

sudo cp -i /home/[COLOR=red]yourusername[/COLOR]/usb_modeswitch.conf /etc 

```8. Now, please ensure that your Smart Bro plug-it is plugged in the USB port. Type the code below:
 
```

sudo /usr/sbin/usb_modeswitch 

```Then, type lsusb to the terminal and now you will see something like this:
 
Bus 001 Device 006: ID 19d2:0031 ONDA Communication S.p.A. 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
*As you notice, I have 0031 ONDA Communication S.p.A. from 2000 which more ikely means that my device is recognizable as ZTE Modem.
 
9. Go to System>Preferences>Network Connection.
 
10. Make sure you encode the following details
 
Country: Philippines
Provider: Smart
*Enter Smart manually (Do not choose Smart from the given provider list)
Selected Plan APN: Smartbro
Access Number: *99#
*NO USERNAME AND PASSWORD MUST BE ENCODED.
 
Now you can connect via Mobile Broadband!!!!
 
If you decided to disconnect and re-use your Plug-it for other sessions, connect your plug-it, open the Terminal and type the code in number 8. Now you should be able to connect again.

I'm going to try your steps hopefully it'll work on my PC. Kaso lang globe tatoo hindi smart ang usb modem.

---

