---
title: "[SOLVED] wifi drivers"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by bosun1000 on 2008-11-28
Sorry if I have posted this twice I think I was in the wrong forum the first time around as I had no replies.
 
I am trying to install wifi drivers on my laptop using Hardy Heron. wifi card is Intel(R) Pro/Wireless 3945ABG. I have downloaded compat-wireless-2.6. tar.bz2 which covers the drivers for my card but how do I actually install them? would someone please write me the code, including opening of the tarball?
Thanks
Bosun

---

### Post by skymera on 2008-11-28
ok im guessing you downloaded the source files for that driver.

Are you sure that your Pro/Wireless doesn't work out of the box? Just to be sure type "iwconfig" into the terminal without the quotes.

Post the output here and we can go from there.

---

### Post by bosun1000 on 2008-11-28
Tanks for your reply. I downloaded the driver at:-
[http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers](http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers)

iwconfig in terminal gives these results:-

john@john-laptop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11g  ESSID:""  Nickname:"" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

 Thanks Bosun




> **skymera said:**
> ok im guessing you downloaded the source files for that driver.

Are you sure that your Pro/Wireless doesn't work out of the box? Just to be sure type "iwconfig" into the terminal without the quotes.

Post the output here and we can go from there.

---

### Post by bosun1000 on 2008-11-28
sorry url for downloaded driver should read:-
[http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers](http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers)


> **bosun1000 said:**
> Tanks for your reply. I downloaded the driver at:-
[http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers](http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers)

iwconfig in terminal gives these results:-

john@john-laptop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11g  ESSID:""  Nickname:"" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

 Thanks Bosun

---

### Post by Michael.Godawski on 2008-11-28
Can you please also post the result of

```
sudo lshw -C network
```

---

### Post by nothingspecial on 2008-11-28
> **bosun1000 said:**
> sorry url for downloaded driver should read:-
[http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers](http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers)

The install instructions are at the bottom of the page. Open a terminal and copy and paste them. If you would like them explaining first I would be happy to do so.

---

### Post by bosun1000 on 2008-11-28
john@john-laptop:~$ sudo lshw -C network 
[sudo] password for john: 
  *-network               
       description: Wireless interface 
       product: PRO/Wireless 3945ABG Network Connection 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:05:00.0 
       logical name: wmaster0 
       version: 02 
       serial: 00:18:de:a1:68:3f 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g 
  *-network 
       description: Ethernet interface 
       product: BCM4401-B0 100Base-TX 
       vendor: Broadcom Corporation 
       physical id: 1 
       bus info: pci@0000:06:01.0 
       logical name: eth0 
       version: 02 
       serial: 00:16:d4:a9:6e:34 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s 
john@john-laptop:~$ 




> **Michael.Godawski said:**
> Can you please also post the result of

```
sudo lshw -C network
```

---

### Post by tarps87 on 2008-11-28
Unless I'm wrong your wireless card is already working. If you have go a wireless network close by and it is broadcasting its 'name' try
```

sudo iwlist wlan0 scan

```
This should list the access point

---

### Post by bosun1000 on 2008-11-28
result of sudo iwlist wlan0 scan:-

john@john-laptop:~$ sudo iwlist wlan0 scan 
[sudo] password for john: 
wlan0     Scan completed : 
          Cell 01 - Address: 00:1D:68:7E:53:4F 
                    ESSID:"BTHomeHub-0E28" 
                    Mode:Master 
                    Channel:11 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality=92/100  Signal level=-38 dBm  Noise level=-127 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 
                              12 Mb/s; 48 Mb/s 
                    Extra:tsf=000003002cbec8c8 

john@john-laptop:~$ 

If I open my Firefox browser and google for google I get the message:-


Address Not Found          

[www.google.com](www.google.com) could not be found. Please check the name and try again.

The browser could not find the host server for the provided address.

    *  Did you make a mistake when typing the domain? (e.g. "ww.mozilla.org" instead of

        "www.mozilla.org")


    *  Are you certain this domain address exists?  Its registration may have expired.


    *  Are you unable to browse other sites?  Check your network connection and DNS server settings.


    *  Is your computer or network protected by a firewall or proxy?  Incorrect settings can interfere with Web browsing.

I therefore presume that I have no network connection please help!
Thanks
Bosun


> **tarps87 said:**
> Unless I'm wrong your wireless card is already working. If you have go a wireless network close by and it is broadcasting its 'name' try
```

sudo iwlist wlan0 scan

```
This should list the access point

---

### Post by nothingspecial on 2008-11-28
*edit* Trying to help you install the package. You don`t need to.

---

### Post by nothingspecial on 2008-11-28
Hang on a minute.

---

### Post by tarps87 on 2008-11-28
Is that your bt homehub? If so all you need to do is connect to it.
Amusing you are using Ubuntu/Gome, in the right of the top panel(menubar) there is a area called the notification area, on of these icons will look like ether one computer or two computers. If you click on it a drop down list of all wireless networks will show up, click on your one and type your wireless password it.
Unlike with windows the driver is already there, all you need to do is connect

Should look like this:

---

### Post by tarps87 on 2008-11-28
> **nothingspecial said:**
> Below are the web pages instructions for installing the package. I don`t know what the package is and so couldn`t recommend it. However if this is a fairly new install of Ubuntu and you back up all your data first. It`s worth a shot.
...

No need to do this you already have the driver working

---

### Post by nothingspecial on 2008-11-28
Yes no need.

---

### Post by bosun1000 on 2008-11-28
Thanks all you guys yes it is my BT homehub I feel so stupid now! being a silver surfer I shall put it down to a "senior moment"!

My next problem will be to find my passphrase!
Thanks again
Bosun

> **tarps87 said:**
> Is that your bt homehub? If so all you need to do is connect to it.
Amusing you are using Ubuntu/Gome, in the right of the top panel(menubar) there is a area called the notification area, on of these icons will look like ether one computer or two computers. If you click on it a drop down list of all wireless networks will show up, click on your one and type your wireless password it.
Unlike with windows the driver is already there, all you need to do is connect

Should look like this:

---

### Post by tarps87 on 2008-11-28
No problem, it's all experience.
I bet your passphrase is in the last place you look :)

---

