---
title: "Bluetooth  connection problem"
date: 2015-12-27
forum: New to Ubuntu
---

### Post by slage63 on 2015-12-27
Hi. Im very new to ubuntu 15.10 in my hp Pavilion PC. After installing Ubuntu i cant share my files between PC and my Samsung phone. On ''Personal File Sharing Preferences" icon there is message "this feature cannot be enabled because the required packages are not installed on your system". i would be very thankfull if somebody give me step by step instruction how to fix it.

---

### Post by Vladlenin5000 on 2015-12-27
Hi and welcome.

Samsung model? OS version?
Connection? USB, Bluetooth, other?

---

### Post by slage63 on 2015-12-27
thank you to replay. Samsung ACE 2. Bluetooth connection

OC 64-bit

samsung model gt-18160
unfortunatelly dont know how to get system info in ubuntu about my PC. here is everyting do i remember from windows: HP-pavilion 4RAM,AMD processor,64-bit,realtek wlan rtl8723be driver. If you let me comand line I will give you more info

both devices worked perfectly before in windows

---

### Post by jeremy31 on 2015-12-27
```
dpkg -l | grep -i obex
```

Likely need to download some packages, also post results for ```
hciconfig -a
```

---

### Post by slage63 on 2015-12-27
i  bluez-obexd                                   5.35-0ubuntu2                              amd64        bluez obex daemon
ii  gnome-user-share                              3.0.4-0ubuntu2                             amd64        User level public file sharing via WebDAV or ObexFTP
ii  libopenobex1                                  1.5-3                                      amd64        OBEX protocol library
ii  obex-data-server                              0.4.6-0ubuntu2                             amd64        D-Bus service for OBEX client and server side functionality

hci0:    Type: BR/EDR  Bus: USB
    BD Address: 10:08:B1:CA:63:7A  ACL MTU: 820:8  SCO MTU: 255:16
    UP RUNNING PSCAN ISCAN 
    RX bytes:2933 acl:20 sco:0 events:213 errors:0
    TX bytes:28709 acl:20 sco:0 commands:175 errors:0
    Features: 0xff 0xff 0xff 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF PARK 
    Link mode: SLAVE ACCEPT 
    Name: 'slage63-HP'
    Class: 0x1c010c
    Service Classes: Rendering, Capturing, Object Transfer
    Device Class: Computer, Laptop
    HCI Version: 4.0 (0x6)  Revision: 0xe2f
    LMP Version: 4.0 (0x6)  Subversion: 0x9f73
    Manufacturer: Realtek Semiconductor Corporation (93)

---

### Post by jeremy31 on 2015-12-27
```
sudo apt-get install obexftp libobexftp0 obexfs
```

Then you should be able to transfer from computer to phone but I haven't been able to send from phone to computer

---

### Post by slage63 on 2015-12-27
Thank you for helping.
unfortunately it dont work.
 Bluetooth File Transfering process starting and then gives a message:
GDBuss.Error:org.bluez.obex.Error.Failed:Unable to find service record

Im still trying to send files from PC to Mobile. One of times sending process was  up to 80% at speed 60-70 kb/s  and then stopped with error

Any more ideas. Lad's?

---

### Post by jeremy31 on 2015-12-28
You could try the transfer with wifi blocked ```
rfkill block wifi
```

You can enable wifi again with ```
rfkill unblock wifi
```

---

### Post by slage63 on 2015-12-28
Before i try it -some info: i can watch tv thru the wifi. The problem only with Bluetooth conection. Here is screenshots[URL="http://ubuntuforums.org/home/slage63/Dropbox/&#1057;&#1082;&#1088;&#1080;&#1085;&#1096;&#1086;&#1090;&#1099;/Link to Screenshot from 2015-12-28 10-58-16.png /home/slage63/Dropbox/&#1057;&#1082;&#1088;&#1080;&#1085;&#1096;&#1086;&#1090;&#1099;/Link to Screenshot from 2015-12-28 10-59-26.png"]/home/slage63/Dropbox/&#1057;&#1082;&#1088;&#1080;&#1085;&#1096;&#1086;&#1090;&#1099;/Link to Screenshot from 2015-12-28 10-58-16.png /home/slage63/Dropbox/&#1057;&#1082;&#1088;&#1080;&#1085;&#1096;&#1086;&#1090;&#1099;/Link to Screenshot from 2015-12-28 10-59-26.png

Do i need to execote your codes?
[/URL]

---

### Post by jeremy31 on 2015-12-28
See if bluetooth can complete the transfer with wifi disabled.  The rtl8723be doesn't have a bluetooth coexistance parameter that can be changed so we are stuck with the default settings. 

 You will have to post dropbox links or upload the screenshots to Ubuntuforums for people to see them

---

### Post by slage63 on 2015-12-28
I have done like you say.   I can watch TV before it. So my WIFI  I think was unblocked . The problem with bluetooth conection only. Here is some screen shot's  [IMG]https://www.dropbox.com/s/k1fujydmoj2dg58/Screenshot%20from%202015-12-28%2010-58-16.png?dl=0[/IMG][IMG]https://www.dropbox.com/s/8qqa93lrc93pck7/Screenshot%20from%202015-12-28%2010-59-26.png?dl=0[/IMG]

[https://www.dropbox.com/s/8qqa93lrc93pck7/Screenshot%20from%202015-12-28%2010-59-26.png?dl=0](https://www.dropbox.com/s/8qqa93lrc93pck7/Screenshot%20from%202015-12-28%2010-59-26.png?dl=0)

[https://www.dropbox.com/s/k1fujydmoj2dg58/Screenshot%20from%202015-12-28%2010-58-16.png?dl=0](https://www.dropbox.com/s/k1fujydmoj2dg58/Screenshot%20from%202015-12-28%2010-58-16.png?dl=0)

---

### Post by jeremy31 on 2015-12-28
You might just need to install Bluetooth File Transfer software on the phone

---

### Post by slage63 on 2015-12-28
After installing Bluetooth File Transfer software on the phone still the same ,only error massage a bit different
[https://www.dropbox.com/s/pmz2luat285y4z5/Screenshot%20from%202015-12-28%2012-04-50.png?dl=0](https://www.dropbox.com/s/pmz2luat285y4z5/Screenshot%20from%202015-12-28%2012-04-50.png?dl=0)

with WIFI disabled still the same

loock at another try[https://www.dropbox.com/s/u634nqaj5toem61/Screenshot%20from%202015-12-28%2012-14-29.png?dl=0](https://www.dropbox.com/s/u634nqaj5toem61/Screenshot%20from%202015-12-28%2012-14-29.png?dl=0)
[https://www.dropbox.com/s/jsxow5503jdiq30/Screenshot%20from%202015-12-28%2012-15-37.png?dl=0](https://www.dropbox.com/s/jsxow5503jdiq30/Screenshot%20from%202015-12-28%2012-15-37.png?dl=0)

i think it could be the problem with installed packages. My phone and pd can see each other in both devices bluetooth is on and set to visible,only when i try to send picture from pc to phone -beside bluetooth sign in right upper corner is visible lock

---

### Post by jeremy31 on 2015-12-28
Delete the pairing then pair again and hopefully the services get updated

---

### Post by slage63 on 2015-12-28
here is how it look's[https://www.dropbox.com/s/jh1vx449pttvsvu/Screenshot%20from%202015-12-28%2012-28-12.png?dl=0](https://www.dropbox.com/s/jh1vx449pttvsvu/Screenshot%20from%202015-12-28%2012-28-12.png?dl=0)

both devices unpaired and restarted.here is the result[https://www.dropbox.com/s/e31rio7z4makbx2/Screenshot%20from%202015-12-28%2012-37-23.png?dl=0](https://www.dropbox.com/s/e31rio7z4makbx2/Screenshot%20from%202015-12-28%2012-37-23.png?dl=0)

when i try to pair my phone to pc it gives: unable to establish communication with PC

i have paired another Samsung phone to my PC. Still the same. After Both of phones paired to other PC(Windows OS ) and both have established Bluetooth connection.

---

