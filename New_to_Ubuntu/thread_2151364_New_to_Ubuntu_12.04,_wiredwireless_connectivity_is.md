---
title: "New to Ubuntu 12.04, wired/wireless connectivity issues"
date: 2013-06-04
forum: New to Ubuntu
---

### Post by mabz1121 on 2013-06-04
I just purchased a Toshiba Satellite laptop that had Windows 8 on it. I burned Ubuntu 12.04 onto disk and wiped Windows 8 and installed Ubuntu. Now I have no internet connection. Wired or wireless says there is no network detected. I tried looking for drivers and it says there are no proprietary drivers  or additional drivers. I looked on the command line to see what I have installed and it shows that I have wired and wireless but it is disconnected.
Help!

---

### Post by MidnightGrey on 2013-06-04
Well lets get the obvious questions out of the way.
Is your WIFI turned on? (theres generally a button on the keyboard).
I'm assuming you have tried plugging in an ethernet cable to a working router?

---

### Post by sanderj on 2013-06-04
> **mabz1121 said:**
> I just purchased a Toshiba Satellite laptop that had Windows 8 on it. I burned Ubuntu 12.04 onto disk and wiped Windows 8 and installed Ubuntu. Now I have no internet connection. Wired or wireless says there is no network detected. I tried looking for drivers and it says there are no proprietary drivers  or additional drivers. I looked on the command line to see what I have installed and it shows that I have wired and wireless but it is disconnected.
Help!

As usual, do the first step 

```
lspci -nnk | grep -i -A2 net
```

and post the output here

---

### Post by mabz1121 on 2013-06-04
Wifi is turned on 
tried plugging in the cable and nothing
Went to System Setting, and checked the network and switched to on for wired cable, still nothing. Click on options and nothing happens.

---

### Post by mabz1121 on 2013-06-04
> **sanderj said:**
> As usual, do the first step 

```
lspci -nnk | grep -i -A2 net
```

and post the output here



mabz@BELL:~$ lspci -nnk | grep -i -A2 net
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)

      Subsystem: Toshiba America Info Systems Device [1179:ff1e]

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]

      Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0723]

mabz@BELL:~$

---

### Post by varunendra on 2013-06-06
> **mabz1121 said:**
> 01:00.0 Ethernet controller [0200]: Atheros Communications Inc. **[COLOR="#FF0000"]AR8162[/COLOR]** Fast Ethernet [**1969:1090**] (rev 10)

      Subsystem: Toshiba America Info Systems Device [1179:ff1e]

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [**[COLOR="#FF0000"]10ec:8723[/COLOR]**]


Both your wired and wireless adapters are rather new to Linux.

The driver "alx" for your Ethernet adapter is already included in 13.04, so you should be able to get it working out-of-box on 13.04.

Alternatively, you may choose to manually download and compile the driver on your existing 12.04 setup. You may follow this post if you choose to compile the driver manually : [http://ubuntuforums.org/showthread.php?t=2050126&p=12206393#post12206393](http://ubuntuforums.org/showthread.php?t=2050126&p=12206393#post12206393)

As for your wireless interface, you must download and compile the driver manually. Follow this thread to see if it helps : [http://ubuntuforums.org/showthread.php?t=2139074&p=12619685#post12619685](http://ubuntuforums.org/showthread.php?t=2139074&p=12619685#post12619685) (and the subsequent posts there if you get "&#8216;IEEE80211_HW_BEACON_FILTER&#8217; undeclared" error while compiling the driver)

Take a look at these posts, try what is suggested there and let us know if you have any difficulties getting it done.

---

### Post by mabz1121 on 2013-06-06
here's what I got when I attempted to manually install:

mabz@BELL:~$ cd Desktop
mabz@BELL:~/Desktop$ sudo dpkg -i *.deb
[sudo] password for mabz:
(Reading database ... 141256 files and directories currently installed.)
Preparing to replace build-essential 11.5ubuntu2 (using build-essential_11.5ubuntu2_amd64.deb) ...
Unpacking replacement build-essential ...
Preparing to replace g++ 4:4.6.3-1ubuntu5 (using g++_4.6.3-1ubuntu5_amd64.deb) ...
Unpacking replacement g++ ...
Preparing to replace libc6-dev 2.15-0ubuntu10.2 (using libc6-dev_2.15-0ubuntu10.2_amd64.deb) ...
Unpacking replacement libc6-dev ...
Preparing to replace make 3.81-8.1ubuntu1 (using make_3.81-8.1ubuntu1_amd64.deb) ...
Unpacking replacement make ...
dpkg: dependency problems prevent configuration of build-essential:
 build-essential depends on dpkg-dev (>= 1.13.5); however:
  Package dpkg-dev is not installed.
dpkg: error processing build-essential (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of g++:
 g++ depends on g++-4.6 (>= 4.6.3-1~); however:
  Package g++-4.6 is not installed.
dpkg: error processing g++ (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.15-0ubuntu10.2); however:
  Version of libc6 on system is 2.15-0ubuntu10.3.
 libc6-dev depends on libc-dev-bin (= 2.15-0ubuntu10.2); however:
  Version of libc-dev-bin on system is 2.15-0ubuntu10.3.
dpkg: error processing libc6-dev (--install):
 dependency problems - leaving unconfigured
Setting up make (3.81-8.1ubuntu1) ...
Processing triggers for man-db ...
Errors were encountered while processing:
 build-essential
 g++
 libc6-dev
mabz@BELL:~/Desktop$ tar -xf compat-wireless-3.5_1-1-snpc.tar.bz2
tar: compat-wireless-3.5_1-1-snpc.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
mabz@BELL:~/Desktop$

---

### Post by mabz1121 on 2013-06-06
mabz@BELL:~$ cd Desktop
mabz@BELL:~/Desktop$ sudo dpkg -i *.deb
(Reading database ... 141460 files and directories currently installed.)
Preparing to replace build-essential 11.5ubuntu2 (using build-essential_11.5ubuntu2_amd64.deb) ...
Unpacking replacement build-essential ...
Preparing to replace cpp 4:4.6.3-1ubuntu5 (using cpp_4.6.3-1ubuntu5_amd64.deb) ...
Unpacking replacement cpp ...
Preparing to replace deb-gview 0.2.8ubuntu3 (using deb-gview_0.2.8ubuntu3_amd64.deb) ...
Unpacking replacement deb-gview ...
Preparing to replace dpkg-dev 1.16.1.2ubuntu7 (using dpkg-dev_1.16.1.2ubuntu7_all.deb) ...
Unpacking replacement dpkg-dev ...
Preparing to replace g++ 4:4.6.3-1ubuntu5 (using g++_4.6.3-1ubuntu5_amd64.deb) ...
Unpacking replacement g++ ...
Preparing to replace gcc 4:4.6.3-1ubuntu5 (using gcc_4.6.3-1ubuntu5_amd64.deb) ...
Removing old gcc doc directory.
Unpacking replacement gcc ...
Preparing to replace libc6-dev 2.15-0ubuntu10.2 (using libc6-dev_2.15-0ubuntu10.2_amd64.deb) ...
Unpacking replacement libc6-dev ...
Preparing to replace make 3.81-8.1ubuntu1 (using make_3.81-8.1ubuntu1_amd64.deb) ...
Unpacking replacement make ...
Preparing to replace manpages-dev 3.35-0.1ubuntu1 (using manpages-dev_3.35-0.1ubuntu1_all.deb) ...
Unpacking replacement manpages-dev ...
Setting up cpp (4:4.6.3-1ubuntu5) ...
Setting up deb-gview (0.2.8ubuntu3) ...
dpkg: dependency problems prevent configuration of dpkg-dev:
 dpkg-dev depends on libdpkg-perl (= 1.16.1.2ubuntu7); however:
  Package libdpkg-perl is not installed.
dpkg: error processing dpkg-dev (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of g++:
 g++ depends on g++-4.6 (>= 4.6.3-1~); however:
  Package g++-4.6 is not installed.
dpkg: error processing g++ (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.15-0ubuntu10.2); however:
  Version of libc6 on system is 2.15-0ubuntu10.3.
 libc6-dev depends on libc-dev-bin (= 2.15-0ubuntu10.2); however:
  Version of libc-dev-bin on system is 2.15-0ubuntu10.3.
dpkg: error processing libc6-dev (--install):
 dependency problems - leaving unconfigured
Setting up make (3.81-8.1ubuntu1) ...
Setting up manpages-dev (3.35-0.1ubuntu1) ...
dpkg: dependency problems prevent configuration of build-essential:
 build-essential depends on libc6-dev | libc-dev; however:
  Package libc6-dev is not configured yet.
  Package libc-dev is not installed.
  Package libc6-dev which provides libc-dev is not configured yet.
 build-essential depends on g++ (>= 4:4.4.3); however:
  Package g++ is not configured yet.
 build-essential depends on dpkg-dev (>= 1.13.5); however:
  Package dpkg-dev is not configured yet.
dpkg: error processing build-essential (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Setting up gcc (4:4.6.3-1ubuntu5) ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 dpkg-dev
 g++
 libc6-dev
 build-essential
mabz@BELL:~/Desktop$

---

### Post by varunendra on 2013-06-06
> **mabz1121 said:**
> 
mabz@BELL:~/Desktop$ tar -xf compat-wireless-3.5_1-1-snpc.tar.bz2
**[COLOR="#FF0000"]tar: compat-wireless-3.5_1-1-snpc.tar.bz2: Cannot open: No such file or directory[/COLOR]**

That's because the file is no more there, the link is dead :(

I may not be able to stay online much longer today (or even for a few days, depending upon how soon the power failure in my village gets fixed), so you may try posting in the linked thread itself to get direct help from my senior dr. chilli555. But take a look at the last few pages on the thread and you should be able to find an updated fix.


**PS:**
The second last post on the thread seems to have the updated link to the compat driver package : [http://ubuntuforums.org/showthread.php?t=2050126&p=12659134#post12659134](http://ubuntuforums.org/showthread.php?t=2050126&p=12659134#post12659134)

---

### Post by mabz1121 on 2013-06-07
Everything I needed to work was within Ubuntu 13.04. I am up and running :) thanks for those who replied!

---

