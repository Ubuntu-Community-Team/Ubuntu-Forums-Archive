---
title: "Looking for general advice with"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by Ntopper on 2012-04-21
New Linux user here, just replaced my dated macbook with a acer 5733z, and just finished installing Ubuntu. Pretty big change but I love it so far. 

I bought this hardware knowing that I would love running Ubuntu on this device, but also knowing that the wireless card would be an issue. My connection is unstable and unusable, this seems to be a common problem. I know there are a few possable solutions, I am just not sure where to start. Should I look into ndiswrapper first? Or is there some other possible fixes that I should start with? I am even willing to purchase a supported wifi card, or even a USB or Ethernet dongle if I must. 

I am also willing to use this as a learning experience, to get my feet wet with the terminal commands. 

Thanks for the help!

---

### Post by wildmanne39 on 2012-04-21
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Ntopper on 2012-04-21
So those commands basically return all of the information gathered about the networking hardware?
edit: I'm researching those commands on google, thanks!
```
nick@ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
nick@ubuntu:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:0601]
    Kernel driver in use: tg3
--
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6617]
    Kernel driver in use: ath9k
nick@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
nick@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
nick@ubuntu:~$ lsmod

```

---

### Post by wildmanne39 on 2012-04-21
Hi, please copy and paste all commands for accuracy. This should get you going.

```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default power management behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off
```

above exit0, then save gedit, close and reboot.

Then

```
gksudo gedit /etc/modprobe.d/ath9k.conf
```

Add a single line:

```
options ath9k nohwcrypt=1
```

Proofread carefully, save and close gedit. Reboot.
Thanks

---

### Post by Ntopper on 2012-04-21
Hmm. Still does not want to connect to my networks.

---

### Post by wildmanne39 on 2012-04-21
Hi, I just relooked up your wireless card it is a new one, you need to install a new driver for it.

Here is a link the answer is in post 63.
[http://ubuntuforums.org/showthread.php?t=1857808&highlight=ar9485&page=7](http://ubuntuforums.org/showthread.php?t=1857808&highlight=ar9485&page=7)
Thanks

---

### Post by Ntopper on 2012-04-21
Thank you soo much! 

Im realy new to this, this is my first time using any form of linux. 

I entered that command, it seemed to download and install most of the files, but it gets stick here :

```
Preparing to replace build-essential 11.5ubuntu1 (using .../build-essential_11.5ubuntu1_amd64.deb) ...
Unpacking replacement build-essential ...
Preparing to replace linux-headers-3.0.0-12-generic 3.0.0-12.20 (using .../linux-headers-3.0.0-12-generic_3.0.0-12.20_amd64.deb) ...
Unpacking replacement linux-headers-3.0.0-12-generic ...
Setting up build-essential (11.5ubuntu1) ...
Setting up linux-headers-3.0.0-12-generic (3.0.0-12.20) ...
nick@Hrunting:~$ 

```

And it jumps out of the process after "Setting up linux-headers-3.0.0-12-generic (3.0.0-12.20) ..."

I'm not sure what to do.

---

### Post by 3rdalbum on 2012-04-22
Each new line given in that thread is a seperate command. The first line (the first command) you've put into your terminal has worked fine, because there were no error messages. Now you just have to put in the second line, then the third line, etc.

---

### Post by Ntopper on 2012-04-22
> **3rdalbum said:**
> Each new line given in that thread is a seperate command. The first line (the first command) you've put into your terminal has worked fine, because there were no error messages. Now you just have to put in the second line, then the third line, etc.

O wow. Ok, It all makes sense now. Tell me if I understand what this is doing:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential 
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2  
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-20*
./scripts/driver-select atheros 
make
sudo make install
```

The first line re-installs the Linux_headers build-essential, although I don't quite understand what that means. 

line 2 downloads a package of drivers and scripts to install them

line 3 unpacks the file

line 4 mounts the directory

line 5 runs a script at that location with the parameter atheros? 

line 6 makes a file at that location that the new driver will be written to? I'm not sure about that one

line 6 installs the driver that I specified when prompted.

This worked! And I am wireless now! I just like to fully understand the commands I use.

---

### Post by Ntopper on 2012-04-22
I'm Wireless!  

The Solution:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential 
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2  
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-20*
./scripts/driver-select atheros 
make
sudo make install
```

Thank you all so much!

---

### Post by JKyleOKC on 2012-04-22
> **Ntopper said:**
> line 4 mounts the directory

line 5 runs a script at that location with the parameter atheros? 

line 6 makes a file at that location that the new driver will be written to? I'm not sure about that one

line 6 installs the driver that I specified when prompted.

This worked! And I am wireless now! I just like to fully understand the commands I use.Your understanding is quite close. The only points I see that you missed (just a bit) were on Line 4, where it moved your working area into the named directory, not mounting it -- but you could consider "moving the working location" to be "mounting" so this is very close.

The major miss was on the "make" line. It actually runs a program named "make" that uses a script written by the developers of the driver, which compiles the actual driver and takes care of all the messy details. If you look in that directory you'll see a file named "makefile" which is plain text, and if you view this file with a text editor you'll see the instructions it gives to the system.

The "make install" line runs the same program, but only uses the portion of the "makefile" script that's headed "install" and again, it handles all the messy details so that you don't have to even be aware of them.

The make program and makefile script are quite powerful tools and can be used for many things. I've even seen them used to organize entire books, and automatically update them when any part of their content is changed...

---

### Post by wildmanne39 on 2012-04-22
Hi, I am glad it is work, please use thread tools at the top of the page to mark the thread solved.
Enjoy

---

