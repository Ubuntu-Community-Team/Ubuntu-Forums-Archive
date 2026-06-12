---
title: "MFC L2470DW scanner drivers"
date: 2019-05-12
forum: New to Ubuntu
---

### Post by giuliano1 on 2019-05-12
[COLOR=#242729][FONT=Arial]Fairly new to Ubuntu, back from 6.1 version 5 years ago. I am now using Ubuntu 18.04, I am installing the drivers for my Brother MFC l2740DW from the terminal, I already printed a test page and try to scan on the simple scan utility, I am anyway stuck in the terminal to this message and I do not know how to handle it form here:[/FONT][/COLOR]
dpkg -i --force-all brscan-skey-0.2.4-1.amd64.deb
Selecting previously unselected package brscan-skey.
(Reading database ... 164123 files and directories currently installed.)
Preparing to unpack brscan-skey-0.2.4-1.amd64.deb ...
Unpacking brscan-skey (0.2.4-1) ...
Setting up brscan-skey (0.2.4-1) ...
apt-get install libusb-0.1-4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libusb-0.1-4
0 upgraded, 1 newly installed, 0 to remove and 173 not upgraded.
Need to get 17.1 kB of archives.
After this operation, 57.3 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 libusb-0.1-4 amd64 2:0.1.12-31 [17.1 kB]
Fetched 17.1 kB in 1s (32.4 kB/s)       
Selecting previously unselected package libusb-0.1-4:amd64.
(Reading database ... 164129 files and directories currently installed.)
Preparing to unpack .../libusb-0.1-4_2%3a0.1.12-31_amd64.deb ...
Unpacking libusb-0.1-4:amd64 (2:0.1.12-31) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Setting up libusb-0.1-4:amd64 (2:0.1.12-31) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
 enter IP address ->192.168.1.73

brsaneconfig4 -a name=MFC-L2740DW model=MFC-L2740DW ip=192.168.1.73
root@giuliano-HP-Compaq-dc7900-Small-Form-Factor:/home/giuliano/Downloads# 
root@giuliano-HP-Compaq-dc7900-Small-Form-Factor:/home/giuliano/Downloads#

Please help, thank you!

---

### Post by him610 on 2019-05-12
Welcome to the Forums Giuliano1,

I have a Brother MFC-7360N that I have to reinstall each time I install an upgraded version of Xubuntu so I am familiar with what you are trying to do; however, I don't see anything that unusual in your post. It all looks pretty normal to me.

Is this the network address of the MFC-L2740DW?  ip=192.168.1.73

It shows that you are in the root terminal, to exit, type *exit *then press *Enter*
Please show the results of this command from the terminal, *scanimage -L* If it is installed it will look something similar to mine,
```

scanimage -L
device `brother4:net1;dev0' is a Brother MFC-7360N MFC-7360N

```

By the way, I wrote a tutorial on installing Brother drivers a few years ago. I just looked it over, and it is pretty much the same now as then. It can be found here, [https://ubuntuforums.org/showthread.php?t=2322192]("https://ubuntuforums.org/showthread.php?t=2322192")

---

### Post by giuliano1 on 2019-05-13
Thank you, it shows exactly like yours:

root@giuliano-HP-Compaq-dc7900-Small-Form-Factor:/home/giuliano/Downloads# scanimage -L
device `brother4:net1;dev0' is a Brother MFC-L2740DW MFC-L2740DW

So it looks everything is OK, I will just exit the terminal, sorry I was assuming I was missing something.

---

