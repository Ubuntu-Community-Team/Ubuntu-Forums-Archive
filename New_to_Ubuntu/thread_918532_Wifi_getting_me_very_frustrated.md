---
title: "Wifi getting me very frustrated"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by boomer0587 on 2008-09-13
Okay I am a complete noob to linux in general as long as ubuntu.  I came over to try something new.  I have been researching everything for the past two weeks and last night I decided to set up mu vista/ubunto dual boot system.  Everything went fine on the install and now I am stuck with no wifi.  I have probably invested around eight hours in this today.  I did not want to post up for help but as of now I feel I have no choice.  I cannot for my life get my wifi going.  I have already tried to go the route of ndiswrapper and madwifi.  But, because i have really no idea what is going on i don't even know what to do with the files.  I am using my desktop now to post this because I don't have a hard line in my apt and I have to keep transferring the files via flash drive. Please help!!!

I will be sitting here waiting so i will post right back.

here is a little info about my system:
nVidia Corporation MCP67 Ethernet (rev a2)
Atheros Communications Inc., AR242 x 802.11abg Wireless
PCI Express Adapter (rev 01)

EDIT : it is a compaq presario notebook F756nr if that means anything

I dunno if that helps but.....

Thanks to anyone that decides to lend a helping hand!

SOLVED!!!!

---

### Post by icyest on 2008-09-13
Here's an unusual unexplained trick I tried when I encountered insufficient WiFi signal strength connection. I took the ethernet connected to my desktop and plugged it into my laptop and surfed for a while, then unplugged it. The wifi somehow functions after that.

---

### Post by skippuff54 on 2008-09-13
can u post the output of ```
sudo iwconfig
``` and ```
sudo ifconfig
``` and ```
sudo modprobe ath_pci
```

i guess you looked here: [http://madwifi.org/wiki/UserDocs/Distro/Ubuntu]("http://madwifi.org/wiki/UserDocs/Distro/Ubuntu")

what is in your /etc/network/interfaces file?

---

### Post by boomer0587 on 2008-09-13
Thanks but it didn't work

---

### Post by skippuff54 on 2008-09-13
what didnt

---

### Post by Elephantman5 on 2008-09-13
Am I reading wrong? Maybe Ndiswrapper will help you?

Anyhow, that's what I did with my Belkin. Just install wireless drivers in the synaptic (search ndiswrapper) and go from there.

---

### Post by boomer0587 on 2008-09-13
> **skippuff54 said:**
> can u post the output of ```
sudo iwconfig
``` and ```
sudo ifconfig
``` and ```
sudo modprobe ath_pci
```

i guess you looked here: [http://madwifi.org/wiki/UserDocs/Distro/Ubuntu]("http://madwifi.org/wiki/UserDocs/Distro/Ubuntu")

what is in your /etc/network/interfaces file?


Yes here we go!

```
sudo iwconfig
[SUDO] password for nick:
lo        no wireless extensions.

eth0      no wireless extensions.
```

```
sudo if config
eth0      Link encap:Ethernet HWaddr 00:1b:24:dc:de:6d
          UP BROADCAST MULTICAST MTU:1500 Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x2000

lo        Link encap:local Loopback
          inet addr:127.0.0.1 Mask:225.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTU:16436 Metric:1
          RX packets:274 errors:0 dropped:0 overruns:0 frame:0
          TX packets:274 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:13700 (13.3 KB) TX bytes:13700 (13.3 KB) 
```

and nothing happens for the last one


Thank You!

EDIT:  sorry i was replying to the other post the whole ethernet cable thing

---

### Post by nothingspecial on 2008-09-13
I think madwifi fixes this.


```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz

```

```

tar -xvf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
```

```
cd madwifi-hal-0.10.5.6-r3835-20080801
```

```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

```
sudo make
```

```
sudo make install
```

** Edit ** I`ve corrected this post

---

### Post by boomer0587 on 2008-09-13
so do i go to that website on my desktop then save the files on my flash, then......what do i do

---

### Post by nothingspecial on 2008-09-13
If you`ve got a wired connection on your notebook, just open a terminal and copy and paste the code into it.

In your menu Accessories > Terminal.

---

### Post by skippuff54 on 2008-09-13
hmm well what's likely painfully obvious to you right now is that your drivers aren't installing properly...once they do, you can open with nano or gedit your /etc/network/interfaces file and see somethin like "auto ath0 inet dhcp". you will know your wireless is up when ifconfig and iwconfig list ath0 with an ip address

follow nothingspecial's advice and see what happens. do use that snapshot. use in terminal ```
wget <URL provided by nothingspecial
``` to grab that file if you can't do a point-n-click style download

then do those commands i listed again and see what you find, post back when u know somethin

---

### Post by Bucky Ball on 2008-09-13
Copy and paste the code, line by line, into your terminal. Downloads will be done in there. :)

! Of course, no connection! Sorry. :-?

---

### Post by skippuff54 on 2008-09-13
i think he's workin on two different machines...how can he get the file from one to the other, once he downloads it?

---

### Post by skippuff54 on 2008-09-13
also how is he gonna unzip, install and make from the flash drive? can he just use cp to copy the file over?

---

### Post by nothingspecial on 2008-09-13
Yes, and I`m sorry I forgot wget in the first line. If you can get a wired connection the first line should be

```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
```


I`ve corrected my original post

---

### Post by nothingspecial on 2008-09-13
If you can`t get a wired connection then first you will need build-essential, these are the tools that let you install stuff on your system.
The package is on the install cd.
Insert it and type
```

sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```
One line at a time pressing return after each.

Then you need the madwifi package. Go to this url on your connected machine -

[http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/)

Download the second from bottom package. The one with the numbers 3835-20080801. Use your flashdrive to copy it across to your home folder (Places-Home).
Then follow my original instructions without the first line or the 4th line (the one about build-essential because we`ve already done that)

I`ve never done it this way but it should work. If anyone knows better please correct me.

It`s much easier if you can get a wired connection

---

### Post by boomer0587 on 2008-09-14
I went through everything up until following your code on page one.  I started with the second one and it went like this:

```

nick@nick:~$ tar -xvf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
tar -xvf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

```

And I did put that folder that i extracted into my home folder

---

### Post by boomer0587 on 2008-09-14
oh man I got it thank you soooooooo  much you guys are life savers!!!!

---

### Post by nothingspecial on 2008-09-14
If yo u extracted it to your desktop you had already done the second command.
The tar command extracts.
I guess you started from line 3. 
Glad to help.
:guitar:

---

