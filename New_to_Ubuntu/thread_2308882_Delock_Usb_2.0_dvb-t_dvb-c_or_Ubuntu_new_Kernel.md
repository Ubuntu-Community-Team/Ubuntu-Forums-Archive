---
title: "Delock Usb 2.0 dvb-t dvb-c or Ubuntu new Kernel"
date: 2016-01-06
forum: New to Ubuntu
---

### Post by whynot on 2016-01-06
Hi everyone

I have Ubuntu working system. Is it possible with outof any trouble to update 15.04(Vivid Vervet) or 15.10(Wily Werewolf) ?I think I need a new Kernel for my tv stick.
Actually I have problem with dvb stick.I have Delock Usb 2.0 dvb-t dvb-c receiver with ID ```
ID 1b80:e1cc Afatech
```.I think my system identifies it but there is no device such as 
```

/dev/video
/dev/video0
/dev/v4l/video0
/dev/v4l/video
/dev/video1
/dev/video2
/dev/video3
/dev/v4l/video1
/dev/v4l/video2
/dev/v4l/video3

```

there are only those devices
```
$ ls /dev/dvb/adapter0/
demux0  dvr0  frontend0  net0

```
But with those devices Im not able watch tv.Even I used device parameter --device=/dev/dvb/adapter0/frontend0 or dvr0 etc.

My Ubuntu System
```
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty
Linux version 3.19.0-43-generic (buildd@lgw01-16) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #49~14.04.1-Ubuntu SMP

```

Thanks.

---

### Post by grahammechanical on 2016-01-06
You have Linux kernel 3.19.0 and that is the same kernel that came with Ubuntu 15.04. On the other hand Ubuntu 15.10 comes with kernel 4.2. On February 4th 2016 we are scheduled to get Ubuntu 14.04.4. That will have kernel 4.2. You should get an offer to upgrade from 14.04.3 to 14.04.4 at the beginning of February.

Regards.

---

### Post by whynot on 2016-01-06
> **grahammechanical said:**
> You have Linux kernel 3.19.0 and that is the same kernel that came with Ubuntu 15.04. On the other hand Ubuntu 15.10 comes with kernel 4.2. On February 4th 2016 we are scheduled to get Ubuntu 14.04.4. That will have kernel 4.2. You should get an offer to upgrade from 14.04.3 to 14.04.4 at the beginning of February.

Regards.

Thanks.

Now Im geting this error during the boot process
```

...[   18.145525] drxk: Could not load firmware file dvb-demod-drxk-01.fw.

```

---

### Post by whynot on 2016-01-06
I found this but no hope
```

wget http://www.palosaari.fi/linux/v4l-dvb/firmware/DRX39xyK/dvb-demod-drxk-01.fw
sudo cp dvb-demod-drxk-01.fw /lib/firmware/
sudo depmod -a

```
There are also other files
[http://www.palosaari.fi/linux/v4l-dvb/firmware/DRX39xyK/dvb-demod-drxk-pctv.fw](http://www.palosaari.fi/linux/v4l-dvb/firmware/DRX39xyK/dvb-demod-drxk-pctv.fw) 
[http://www.palosaari.fi/linux/v4l-dvb/firmware/DRX39xyK/dvb-usb-hauppauge-hvr930c-drxk.fw](http://www.palosaari.fi/linux/v4l-dvb/firmware/DRX39xyK/dvb-usb-hauppauge-hvr930c-drxk.fw)
one more script
 ```
wget https://raw.github.com/torvalds/linux/master/Documentation/dvb/get_dvb_firmware
```

---

### Post by Vladlenin5000 on 2016-01-06
Although the plan outlined in the previous post should work, there's probably an easier way. If I remember correctly the Afatech tuners needed only additional drivers/firmware that could be obtained directly from Ubuntu repositories (preferable).
System Settings > Software & Updates > Additional Drivers (tab) - with the dongle connected - check what's offered and install accordingly. Reboot & test.

---

### Post by whynot on 2016-01-06
There is only one suggestion for nvidia with different versions 340.96 304.131 and xorg  but I think I already installed my video card.I tried with old [Kernel 3.11.6]("http://linuxg.net/how-to-install-kernel-3-11-6-on-ubuntu-linux-mint-debian-pear-os-and-elementary-os/") and reinstalled v4l-dvb
Kernel
```

$ wget -c kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.6-saucy/linux-headers-3.11.6-031106_3.11.6-031106.201310181453_all.deb
$ wget -c kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.6-saucy/linux-headers-3.11.6-031106-generic_3.11.6-031106.201310181453_amd64.deb
$ wget -c kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.6-saucy/linux-image-3.11.6-031106-generic_3.11.6-031106.201310181453_amd64.deb
$ sudo dpkg -i linux-headers-3.11.6*.deb linux-image-3.11.6*.deb

```
v4l-dvb
```

sudo apt-get install build-essential libdigest-sha-perl patchutils libproc-processtable-perl git-core  # I allready have them
sudo apt-get install linux-headers-$(uname -r)  # I allready have them
sudo apt-get install linux-firmware-nonfree # ""
git clone git://linuxtv.org/media_build.git 
cd media_build
./build 
sudo make install 

```

 and Im getting

```
$ ls /dev/video0
/dev/video0

device and 

$ ls /dev/dvb/adapter0/
demux0  dvr0  frontend0  net0

$ ls /dev/v4l/by-path/
pci-0000:00:1a.0-usb-0:1.1:1.0-video-index0

$ ls /dev/v4l/by-id/
usb-1b80_USB_2875_Device-video-index0

```
but Tv softwares doesnt work with this video drive :( but Im working on it.

---

### Post by whynot on 2016-01-06
Ok I have to use w_scan
```

 w_scan -ft -c XX >> channels.conf #  XX such as GB US DE AT etc. where do you live

```
Now I could able to watch TV with Kaffeine and ME TV
I need functional tv software.Do you guys have any suggestion? 
Thanks.

---

### Post by howefield on 2016-01-07
> **whynot said:**
> Now I could able to watch TV with Kaffeine and ME TV
I need functional tv software.Do you guys have any suggestion? 
Thanks.

My preference is for Kaffeine and/or VLC. Kaffeine makes the tuning easy, VLC needs the channel.conf file generated by your command above.

---

### Post by whynot on 2016-01-07
Ok but for Vlc What we do? We just load or open channel.conf file?Thats it! By the way Im now using old Kernel 3.11.6-031106-generic .I changed default boot selection with grub-customizer
```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
```

with this way it didnt do anything.Anyway customizer did the job.
```

sudo nano /etc/default/grub
GRUB_DEFAULT="0" --> "5"
sudo update-grub

```

---

### Post by howefield on 2016-01-07
> **whynot said:**
> Ok but for Vlc What we do? We just load or open channel.conf file?

Yes, once you have created the channel.conf file just drag and drop it into the VLC window (or vlc application icon) or open it via the menu.

---

### Post by Bucky Ball on 2016-01-07
Me-tv is my tool of choice for tele. In the repositories. Will do an autoscan the first time you launch it and that's it. You don't need to do anything but select your country, wait for the scan to finish, select a station and enjoy. :D

---

