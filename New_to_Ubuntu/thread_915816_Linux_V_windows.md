---
title: "Linux V windows"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by testLED on 2008-09-10
Hi All 

I have been trying to get this to work for 2 days to no avail. So this is the last attempt at fixing it before I sadly have to revert back to XP because my kids are bugging me to fix this. I decided to completely remove XP and install Ubuntu. All went ok except now I come to the D link usb g 122 key for the internet connection. 

I have read lots about installing drivers using ndiswrapper for the windows drivers and installing the linux driver instead. I have also read that Ubuntu 8 already has these drivers on. Great!!

However I dont dispute that as without me doing anything when I installed it my link light on the key came on and the system can see it. I think because of this I must be close to getting connected. Not so by the seems of things as when I open Mozilla it wont connect. 

I know I am probably doing something stupid or missing something vital but what??? 

Any help fom you guys would be great. I really do not want to go back to XP but fear for my life if I dont get this working. 

Cheers Guys and Girls.

---

### Post by billgoldberg on 2008-09-10
Google has lots of guides on ndiswrapper.

If you really don't want to revert to XP, buy a wireless usb dongle that is supported OOTB (out of the box) in Ubuntu.

A list of those can be found here:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#Wireless%20USB%20Adapters](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#Wireless%20USB%20Adapters)

---

### Post by WRDN on 2008-09-10
For the adapter, i've heard you can use ndiswrapper or [this]("http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page") driver.

---

### Post by testLED on 2008-09-10
Well I have gone down the driver road for the last two days installing ndiswrapper and removing it to use linux drivers etc and it ended up with my link light constantly going on and off. 

I reloaded the OS and right now I am in a better position. I have the link light on all the time so thats got to be good. If I run the iwconfig it tells me my essid and the access point MAC address. I have configured my WAP key in the network section. 

However no connection I cant even ping my router. 

Weird!!

---

### Post by halitech on 2008-09-10
> **testLED said:**
> Hi All 

I have been trying to get this to work for 2 days to no avail. So this is the last attempt at fixing it before I sadly have to revert back to XP because my kids are bugging me to fix this. I decided to completely remove XP and install Ubuntu. All went ok except now I come to the D link usb g 122 key for the internet connection. 

I have read lots about installing drivers using ndiswrapper for the windows drivers and installing the linux driver instead. I have also read that Ubuntu 8 already has these drivers on. Great!!

However I dont dispute that as without me doing anything when I installed it my link light on the key came on and the system can see it. I think because of this I must be close to getting connected. Not so by the seems of things as when I open Mozilla it wont connect. 

I know I am probably doing something stupid or missing something vital but what??? 

Any help fom you guys would be great. I really do not want to go back to XP but fear for my life if I dont get this working. 

Cheers Guys and Girls.

since the light came on, that is a good sign. On your wireless router, do you have any kind of encryption? also, if you open a terminal, what is the output of```
iwconfig scan
```you could also just try```
iwconfig
``` to see what info it gives

---

### Post by testLED on 2008-09-10
Ok iwconfig scan returns 

" scan    No such device"

iwconfig returns

wlan0 IEEE 802.11G ESSID "I can see you!!" 

it also give me the MAC address for the access point. 

I cant copy and paste as I am on here with a different computer for obvious reasons.

---

### Post by halitech on 2008-09-10
> **testLED said:**
> Ok iwconfig scan returns 

" scan    No such device"

iwconfig returns

wlan0 IEEE 802.11G ESSID "I can see you!!" 

it also give me the MAC address for the access point. 

I cant copy and paste as I am on here with a different computer for obvious reasons.

crap, sorry that should have been```
iwconfig scan wlan0
```

---

### Post by testLED on 2008-09-10
with iwconfig scan wlan0 

it now says "iwconfig: unknown command "wlan0"

---

### Post by halitech on 2008-09-10
that makes no sense cause it shows it in iwconfig. are you putting that in as a 0 (zero) or a capital o?

---

### Post by Sorivenul on 2008-09-10
> **halitech said:**
> crap, sorry that should have been```
iwconfig scan wlan0
```
I've never had my scans work that way, mine has always shown with ```
iwlist scan
```

Since you're using WPA, you may want to check out [this]("http://ubuntuforums.org/showthread.php?t=202834") thread and print the necessary bits, as I'm not sure of your exact setup.

---

### Post by halitech on 2008-09-10
> **Sorivenul said:**
> I've never had my scans work that way, mine has always shown with ```
iwlist scan
```

Since you're using WPA, you may want to check out [this]("http://ubuntuforums.org/showthread.php?t=202834") thread and print the necessary bits, as I'm not sure of your exact setup.

maybe I'm mixing them up, I dont use wireless consistently so hopefully your command will work for him

---

### Post by testLED on 2008-09-10
Ok iwlist scan gives me this

lo    Interface does not support scanning.

wmaster0 Interface does not support scanning.

wlan0 No scan results. 

Also might be normal if I do iwconfig it tells me the essid as I entered it on the network GUI, it also gives me the MAC of the machine. 

If I enter ifconfig it tells me this.....

wlan0  and tells me the MAC of the USB key 

and then it says 

wlan0:avahi and the mack address of the usb key 

it also gives me an ipaddress of 169.254.3.55 ( I dont know what this is)

---

### Post by halitech on 2008-09-10
169.254 is an ip that most systems will enter when it wasn't able to get an IP from a router or DHCP server

---

### Post by testLED on 2008-09-10
iwlist scan shows wlan0 no scan results?

---

### Post by mrsteveman1 on 2008-09-10
I believe you have to use sudo or the program can't read the results out of the kernel:

```
sudo iwlist scan wlan0
```

It appears to be working anyway, so does networkmanager (in the corner) show your network?

---

### Post by testLED on 2008-09-10
that comes back with unknown command

---

### Post by testLED on 2008-09-10
I Just had a thought!!!

My wireless router is micronet but my usb key is d link left over from my Dlink router that sadly got a size 11 shoe on it for annoying me. However it used to work with that set up when running XP. 

could this be an issue?

---

### Post by halitech on 2008-09-10
shouldn't matter, I have a Dlink router and have successfully connected to it using an Airlink pcmcia card and a trednet usb adapter. Granted some seem to work a little better together but a network device should be a network device

have you tried rebooting everything to see if it will link up?

---

### Post by linuxlizard on 2008-09-10
how's the security on your router set? Mine for example has a mac list I configure and only allows those on the list access...

---

### Post by testLED on 2008-09-10
yep mine is configured using MAC lists and mine is in there aswell as the USB dongle. 

I have noticed something that might be useful or not. 

In devices> network tools if I look at devices I can see an option for wlan0 and an option for wlan0:avahi 

if I look at wlan0 and press configure it tells me that the interface does not exist. 

If I select the other one it also tells me that the interface does not exist.

---

### Post by dmizer on 2008-09-10
> **mrsteveman1 said:**
> I believe you have to use sudo or the program can't read the results out of the kernel:

```
sudo iwlist scan wlan0
```

It appears to be working anyway, so does networkmanager (in the corner) show your network?

The proper command is:
```
sudo iwlist wlan0 scan
```

Here is an excellent guide on troubleshooting ndiswrapper: [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

---

### Post by testLED on 2008-09-10
ok now this tells me the following I have to type it though..


Scan completed 

cell 01 - Address: xx:xx:xx:xx (MAC)
          ESSID "I can see you!!" ( my Router)
          Mode: Master 
          Channel 11
          Frequency:2.462 GHz Channel 11
          Quality=51/100 Signal Level=51dBm
          Encryption Key: on
          IE WPA Version 1 ( dont know what this should be 1 or2)
          Group Ciphers (1):TKIP
          Authentication Suites 1 : PSK
          
          and then all the bit rate. 

Does this tell me that it must be talking to my router but I cant ping it??

---

### Post by testLED on 2008-09-10
Ok Guys 

I have managed to get the wireless signal icon up in the right hand corner. 

I am so close to this working I know it..... Only thing is I still cant ping from it or anything. It must be connected to the device.....

---

### Post by testLED on 2008-09-10
Oh well....

sadly after three long days trying to resolve this I am further forward but no there. Which can only mean a revert back to the world of XP.. Shame I like linux and what I can learn technically from it. Unfortunalty I can get my wireless key to work. I have tried the lot I think everything I have read I have carried out. I have even got the signal bar in the top right hand corner I have logged on to my router and turned off everything security wise but still cannot get internet access. My router can see the MAC of the Linux box but thats it. Thats why I know I am close. 

Even though I would like to move away from windows I feel I can live with the crashes and freezes and encountered problems over painful installations. 

They do say little knowledge is dangerous. 

Maybe one day I will conquer my man over machine dilema.

---

### Post by jimv on 2008-09-10
Try this:

Click here to download WICD:
[http://downloads.sourceforge.net/wicd/wicd_1.5.1_all.deb?modtime=1217852338&big_mirror=0](http://downloads.sourceforge.net/wicd/wicd_1.5.1_all.deb?modtime=1217852338&big_mirror=0)

Double click the file you downloaded.  This will replace NetworkManager with the much superior WICD Network Manager.

Reboot.

Once you are back up, double click the WICD icon on your task bar (looks like a computer).  You should see your network and be able to connect to it.

---

