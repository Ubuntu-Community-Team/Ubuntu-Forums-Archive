---
title: "How to set up Ubuntu 6.06 on AOL [UK] Broadband with a BT Voyager 105 Modem"
date: 2006-11-03
forum: Outdated Tutorials &amp; Tips
---

### Post by pilgrim-online on 2006-11-03
[SIZE="4"]Modem needs to be unplugged from USB before booting into Ubuntu.

Copy to Home Folder:[/SIZE] [I downloaded in Windows and transferred by Pen Drive.]
pppoe_3.5-4ubuntu1_i386.deb
eciadsl-usermode_0.11-1_i386.deb
eciadsl-synch_bin.tar.bz2

[SIZE="4"]Install:[/SIZE]
Enter in terminal: [One at a time. As each installs several lines of text appear.]
1]  sudo dpkg -i pppoe_3.5-4ubuntu1_i386.deb
2]  sudo dpkg -i eciadsl-usermode_0.11-1_i386.deb
3]  sudo tar -xjvf eciadsl-synch_bin.tar.bz2 -C  /etc/eciadsl/

[SIZE="4"]Reboot.

Plug in modem.

Enter in terminal:[/SIZE]
sudo eciadsl-config-text

Enter as follows:
user name:  *******@aol.com
password:  ******
Provider:  other
DNS1:  205.188.146.145
DNS2:  205.188.146.145
VPI:  0
VCI:  38
Modem:  BT Voyager 105
VID1/PID1/VID2/PID2:  accept defaults
Modem Chipset:  GS7470
Synch File:  /etc/eciadsl/gs7470_synch03.bin
PPP Mode:  accept default
is DCHP used?  No
is a static ip used?  No

Mode:  VCM_RFC2364

Click Create Config.
Close terminal.

[SIZE="4"]To Start.[/SIZE] [See [SIZE="3"]*[/SIZE] below.]
Enter in terminal:  sudo eciadsl-start
[SIZE="4"]
To Stop:[/SIZE]
Enter in terminal:  sudo eciadsl-stop

_[SIZE="3"]*[/SIZE]May need to enter 'start' then 'stop' then 'start' again in different terminals?_

[Having now been using this for some time I type sudo eciadsl-start into a terminal, leave for about 30 seconds by which time it has reached 4 out of 5 stages. I then open a second terminal and type eciadsl-stop, this is usually denied but it triggers the first terminal to connect.]

For origins of this post see [http://tinyurl.com/yzmogv]("http://tinyurl.com/yzmogv")

---

