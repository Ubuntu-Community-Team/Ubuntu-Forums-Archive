---
title: "For those with the realtek 8187b wireless card"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by smile-its-smiley on 2008-05-01
after ages trying to get this wireless card to work i have managed to do so. using ndiswrapper and a windows 98 driver. if you would like to get the driver to work on Ubuntu you need to add 

%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200

underneath 

%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8187&REV_0200

%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8189&REV_0200

in both the sections labeled 

IDs for 98SE/ME/2K/XP and IDs for X64

if you require the windows 98 driver you can download it from [http://members.driverguide.com/driver/detail.php?driverid=1165168](http://members.driverguide.com/driver/detail.php?driverid=1165168) and unzip the file you download and navigate to the windows 98 file and edit the stated above in the .inf file

i hope this helps****

---

### Post by game_plan on 2008-05-04
First, Thank you! I've tried the Linux drivers and wasn't happy with them, and this fixed the other option for wireless, you rock!

But I still can't get wireless loaded. If I use the Win98, WinXP, Vista drivers the log files show it fails since the driver is 32bit and kernel is 64bit. 

So I tried the X64 and VistaX64 drivers. VistaX64 feeds alot of variables to ndiswrapper it doesn't understand and fails.

Heres what happens with X64...
```

laptop1 kernel: [   40.045996] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
laptop1 kernel: [   40.382683] ndiswrapper (link_pe_image:576): fixing KI_USER_SHARED_DATA address in driver
laptop1 kernel: [   40.383805] ndiswrapper: driver net8187b (Realtek Semiconductor Corp.,07/18/2007,5.1097.0718.2007) loaded
laptop1 kernel: [   43.894169] usbcore: registered new interface driver ndiswrapper
laptop1 kernel: [   43.930972] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
laptop1 kernel: [   46.114261] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
laptop1 kernel: [   46.450972] ndiswrapper (link_pe_image:576): fixing KI_USER_SHARED_DATA address in driver
laptop1 kernel: [   46.452103] ndiswrapper: driver net8187b (Realtek Semiconductor Corp.,07/18/2007,5.1097.0718.2007) loaded
laptop1 kernel: [   49.967046] usbcore: registered new interface driver ndiswrapper
laptop1 kernel: [   49.970081] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
laptop1 kernel: [   41.639997] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
laptop1 kernel: [   41.681334] usbcore: registered new interface driver ndiswrapper
laptop1 kernel: [   40.348915] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
laptop1 kernel: [   40.685695] ndiswrapper (link_pe_image:576): fixing KI_USER_SHARED_DATA address in driver
laptop1 kernel: [   40.686818] ndiswrapper: driver net8187b (Realtek Semiconductor Corp.,07/18/2007,5.1097.0718.2007) loaded
laptop1 kernel: [   44.197356] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
laptop1 kernel: [   44.200281] usbcore: registered new interface driver ndiswraper
laptop1 kernel: [   39.640667] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
laptop1 kernel: [   39.684583] usbcore: registered new interface driver ndiswrapper

```

And after logging in I get the login background and a message saying gnome couldn't load my settings, until I rescue my system and remove that driver from ndiswrapper.

Any ideas? Thanks again for your help

---

### Post by tjwoosta on 2008-05-04
here is a thread i made a couple of weeks ago, there is the ndiswrapper way that you could do it or you could use the patched driver from datanorth
(its all in this thread)
[http://ubuntuforums.org/showthread.php?t=765671]("http://ubuntuforums.org/showthread.php?t=765671")

---

### Post by game_plan on 2008-05-04
> **tjwoosta said:**
> here is a thread i made a couple of weeks ago, there is the ndiswrapper way that you could do it or you could use the patched driver from datanorth
(its all in this thread)
[http://ubuntuforums.org/showthread.php?t=765671]("http://ubuntuforums.org/showthread.php?t=765671")

Thanks, I've written in that thread to but I've never gotten any answers.

I have the patch and everything working but no one could tell me why iwlist scan works but iwconfig doesn't.

And thanks to this solution NDISWRAPPER finds the device now, but gnome freezes "loading my preferences" or fails to load the driver since there 32bit drivers.

---

### Post by tjwoosta on 2008-05-05
hmm... well i did the patched driver from datanorth and as far as i know it only works for wep also it is very glitchy  

i had a hard time to get it to connect to my home network at first then finally somehow i got it to work
(i did it by clicking the network icon after i did ./wlan0up an a list came up of networks in the area then i just clicked mine)

so i logged in an now everytime i start wlan0 it just automatically logs onto my home network no problem
(this computer doesnt usually log on to any other networks than my home )

i think if i had to switch networks often i would probably just get a new cheapo card or try the ndiswraper way, but from what ive heard the ndiswrapper way seems to work best for connecting to wpa wile the patched driver seems to work better for wep

---

### Post by game_plan on 2008-05-05
Ya, with the modified driver I can see some other guys WEP and an open network, but not mine, I suspect that would work but I'd rather not turn down the security just for one system.

I looked at the event logs and the .inf file and don't see a difference in the 32 and 64 bit drivers that would cause any issues. Hopefully someone will be able to find what's messing it up and let me know.:confused:

Thanks for your help :)

---

### Post by game_plan on 2008-05-06
Someone Please help. I really am in a jam here, I have to leave for business in a week and wireless would be really helpful. 

If I can't get this to work I'll have to put ***shudder*** Windows back on the empty partition (There no way I'd switch back totally :cool::cool:)


PLEASE help!

---

### Post by smile-its-smiley on 2008-05-06
ive noticed on my wpa2 network doesnt allways work if im using the roaming settings so i have to use the manual way and it will pick up the wireless network automaticly allthough it might take a few mins to connect but it does eventually.

---

### Post by game_plan on 2008-05-17
Thanks, I'll try that right after I try the new ndiswrapper, Hopefully it wont crash when I try to load the 64bit driver

---

### Post by game_plan on 2008-05-17
Alright I got wireless working (WPA and WPA2) in the 32 bit version, but in the 63 bit version (yes I have both installed right now) I get the same error.

The GDM crashes, the error says that "there was no reply" but it doesn't tell me what is waiting for the reply or what should have replied.

I would like to get this to work in the 64-bit version, the only difference I can see is that the X64 and Win98 inf files point to different .sys files.

If anyone could tell me what to change or what to install it would be greatly appreciated.

---

### Post by game_plan on 2008-05-24
Does anyone have this driver working in the 64bit version? I really cannot figure out what is causing the driver (or kernel) to crash or ignore the wireless card.

---

### Post by tjwoosta on 2008-05-24
mine works fine with Hardy 64bit and WEP (havn't tried WPA)

i used the patched drivers from the link in my post on the first page

---

### Post by game_plan on 2008-05-25
I unfortunately use a mixed WPA/WPA2 network and those drivers would lockup when I tied to connect. I would lower the security to WEP but I have information that requires highest security possible (or I'd loss my job).

Thats why I even bothered with the ndiswrapper method, I'm getting close to just installing the 32-bit version alone and be done with it.

---

### Post by rookie2008 on 2008-05-27
Hello everyone,

My wifi was working just fine using pjasnos' method ([http://ubuntuforums.org/showthread.p...light=rtl8187b](http://ubuntuforums.org/showthread.p...light=rtl8187b))
Also listed below -

wget [http://www.datanorth.net/~cuervo/rtl...ed-dist.tar.gz](http://www.datanorth.net/~cuervo/rtl...ed-dist.tar.gz)

wget [http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch](http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch)

tar -xzvf rtl8187b-modified-dist.tar.gz

cp 2.6.24.patch rtl8187b-modified/
cd rtl8187b-modified
patch -p1 < 2.6.24.patch
./makedrv
sudo ./wlan0up

until I installed the updates that GNOME recommended I download and install earlier today. I am using Ubuntu 8.04 64bit desktop edition. Now I am getting some of the same errors you all have mentioned -

notavailable@CENSORED:~$ cd rtl8187b-modified
notavailable@CENSORED:~/rtl8187b-modified$ sudo ./wlan0up
insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8187.ko': No such file or directory
notavailable@CENSORED:~/rtl8187b-modified$ dir

2.6.24.patch install ReadMe.txt wlan0dhcp wlan0up
ieee80211 makedrv release_note wlan0down wpa_supplicant-0.5.3
ifcfg-wlan0 README.FIRST rtl8187 wlan0rmv
notavailable@CENSORED:~/rtl8187b-modified$

Ok.  I applied the following commands again:

cp 2.6.24.patch rtl8187b-modified/
cd rtl8187b-modified
patch -p1 < 2.6.24.patch
./makedrv
sudo ./wlan0up

And my wifi is back online again.
 I thought the updates were supposed to fix problems, not create them. Maybe I should email the developers?

---

