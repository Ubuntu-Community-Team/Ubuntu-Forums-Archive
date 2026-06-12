---
title: "installed but having a few issues"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by TimmyR41 on 2008-06-09
ok, i got xubuntu installed and running.  my computer seems to run much much better than it did with xp.  i have run into 2 problems though.

my first problem is xubuntu seems to on recognize the hard drive i installed the operating system on.  i have a second hard drive that i had all my pictures, music and files on that is not showing up anymore.  

my second problem is that it will not detect my wireless internet.  i currently have a linksys wireless router with a linksys usb wireless reciever on my desktop.  it does have a proxy server.  

any help i could get would be great.  thanks alot.

---

### Post by TeoBigusGeekus on 2008-06-09
About the hd:
Post us the output of 
```
sudo fdisk -l
```

---

### Post by hyper_ch on 2008-06-09
(1) Posting a descriptiv thread title instead of a generic "noob here" or "help needed" is better

(2) for unrelated questions, open separat threads, so that you can mark each one as "solved" individually.

(3) what filesystem is that second harddrive? Ntfs? If so, you may want to install ntfs-3g and enable read/write support

(4) is the wifi card recognized at all? Post the output of the following commands:
```

lsusb

```

```

iwconfig

```

```

ifconfig

```

```

cat /etc/network/interfaces

```

```

cat /etc/resolv.conf

```

---

### Post by TimmyR41 on 2008-06-09
sorry for the generic thread post.  i'll change that next time.  when you say post the output from the following commands, where do i type the commands.  i'm definatly really new to this.  also i'm not sure what file system the hard disk is.  ntfs sounds familiar but is there a way to be sure?  

as far as the wifi is concerned its kinda strange.  i have installed the operating system 3 times now.  i know this was probably stupid but here's my reasoning.  initially when i installed i clicked on advanced on the page right before it acctually installs.  there is an option for proxy server but i figured i could input that information once i got into the operating system so i left it blank.  it detected my network supposedly but would never go above 50% and would not allow me to log onto the internet through firefox.  even when i input the proxy server info in firefox.  so i tried the install a second time with inputing the proxy server info on the install but i left the port defaulted as it was.  i believe it was 8800.  i got the same results.  so i tried it one more time with the proxy server port as 3128 which is what was given to me by my isp and now it does not detect the wireless connection at all.  thanks for the quick responses.

---

### Post by hyper_ch on 2008-06-09
for the output:

(1) open a terminal

(2) copy and paste the commands (or type them)

(3) you will get some output, post that here and enclose the output in [noparse]```

```[/noparse] brackets (makes it easier to read)

---

### Post by TimmyR41 on 2008-06-09
ok, i'll do that when i get home.  i'm at work now so i don't have access to my computer at home.  thanks for the help.

---

### Post by TimmyR41 on 2008-06-10
ok here are the command outputs.  as a status update i was able to get to a website last night.  i entered the proxy info in firefox and attempted to go to msn.com. It took me to a text only version of msn.com.  Also it took about 20 minutes for that text only version to load.  i never took anywhere close to that long with xp and then i was getting full webpages so something must be set up wrong.  i attempted to get to another website after that and i got a web page could not be found error again.  ok heres the command outputs.

lsusb```
Bus 001 Device 005: ID 13b1:000d Linksys 
Bus 001 Device 004: ID 413c:3200 Dell Computer Corp. 
Bus 001 Device 003: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 001 Device 002: ID 050d:0234 Belkin Components F5U234 USB 2.0 4-Port Hub
Bus 001 Device 001: ID 0000:0000  

```

iwconfig```
lo        no wireless extensions.

eth0      no wireless extensions.

```

ifconfig```
eth0      Link encap:Ethernet  HWaddr 00:04:76:37:35:23  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:3 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17472 (17.0 KB)  TX bytes:17472 (17.0 KB)

```

cat /etc/network/interfaces```
auto lo
iface lo inet loopback

```

cat /etc/resolv.conf```
cat: /etc/resolv.conf: No such file or directory
```

sudo fdisk -1```
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

```

thanks for all the help guys.

---

