---
title: "Install Wireshark"
date: 2011-11-21
forum: New to Ubuntu
---

### Post by CaroleB on 2011-11-21
Hello everyone:)
I have recently installed Ubuntu 11.04 and I'm kinda new to it!
I just need the right commands to install Wireshark on it.
Regards,
Carol

---

### Post by mutley89 on 2011-11-22
```
sudo apt-get install wireshark
```

---

### Post by audiomick on 2011-11-22
Or use the software centre (or synaptic package manager, if it is installed).

The search function in the software centre on mine found it immediately. If it doesn't show up on your machine, go to the menu with the package sources and enable them all.

---

### Post by moody_mark on 2011-11-22
Note once installed you'll need to run it as a user with root privileges to be able to capture packets on your interface. Open up a terminal session:

Applications --> Accessories --> terminal

If you run as a regular user you'll see this, but you'll still be able to open up capture files

```
$ wireshark 
dumpcap: There are no interfaces on which a capture can be done

```
Run as a sudo user and you can then capture on your machine's interfaces:

```
$ sudo wireshark 
[sudo] password for moody: 
```

You'll get a warning about running as root in the UI when it opens up, its just a warning though :) Happy packet tracing!

---

### Post by audiomick on 2011-11-22
Just had a look at the program. It has a graphical interface, so you should by rights start it with
```
gksudo wireshark
```
to run it as root.

There is a how to here
[http://openubuntu.com/index.php/topic,1661.0.html](http://openubuntu.com/index.php/topic,1661.0.html)
regarding setting it up to run with limited root privileges. I haven't tried this, so I can't vouch for it's effectivity.

---

### Post by rocklobster217 on 2011-11-27
[FONT=Tahoma]## WARNING ## Wireshark does not require  root  privileges to capture packets and should not be run this way; only  dumpcap requires root  privileges [[1]]("http://wiki.wireshark.org/Security").

The documented method [[2]]("http://wiki.wireshark.org/CaptureSetup/CapturePrivileges") is summarized below and can be run via command line:[/FONT]
```
[FONT=Courier New]sudo chgrp wireshark /usr/bin/dumpcap  
sudo chmod 754 /usr/bin/dumpcap
sudo setcap 'CAP_NET_RAW+eip CAP_NET_ADMIN+eip' /usr/bin/dumpcap[/FONT]
```[FONT=Tahoma]
This command is extra but required; adds your username to the wireshark group.[/FONT][FONT=Courier New][FONT=Tahoma]
[/FONT]```
sudo usermod -a -G wireshark *<your-username-here>*
```[/FONT][FONT=Tahoma]
Log Out or Reboot for changes to take affect. 

Please ensure Wireshark works only from root and from a user in the "wireshark" group.[/FONT]
[FONT=Tahoma]
Regards, David Chute.
[U]
Sources:[/U]
[I][[1]]("http://wiki.wireshark.org/Security") [http://wiki.wireshark.org/Security](http://wiki.wireshark.org/Security)
[[2]]("http://wiki.wireshark.org/CaptureSetup/CapturePrivileges") [http://wiki.wireshark.org/CaptureSetup/CapturePrivileges](http://wiki.wireshark.org/CaptureSetup/CapturePrivileges)[/I][/FONT]

---

