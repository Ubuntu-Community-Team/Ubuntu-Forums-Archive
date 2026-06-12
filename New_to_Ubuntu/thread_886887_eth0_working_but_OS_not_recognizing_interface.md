---
title: "eth0 working but OS not recognizing interface"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by mlamberg on 2008-08-11
Running 8.04 on a Compaq EVO N410c laptop.  I configured the wired ethernet interface for static IP.. Everything is working but Wireshark doesn't see the interface. Also when I go to System > Administration > Network Tools and bring up eth0 interface, clicking the configure button returns "interface not found"...  Lastly, right clicking on the network icon in the right top corner of the desktop provides a menu but the "connection information" item is grayed out.... This is very strange, I don't recall earlier versions of Ubuntu responding this way....

Thanks for your help

Mike

---

### Post by cgkades on 2008-08-11
issue the command and paste the output
```

ifconfig -a

```

---

### Post by mlamberg on 2008-08-11
eth0      Link encap:Ethernet  HWaddr 00:d0:59:c6:c6:b1  
          inet addr:192.168.1.51  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:59ff:fec6:c6b1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40359 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37383139 (35.6 MB)  TX bytes:10539069 (10.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2054 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2054 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:365150 (356.5 KB)  TX bytes:365150 (356.5 KB)

---

### Post by cgkades on 2008-08-11
did you try wireshark as root? 

```

sudo wireshark &

```

if that doesnt work, enter the following and paste the output (i'm trying to see if your computer recognizes the card properly)
```

lspci | grep Ether

```

---

### Post by mlamberg on 2008-08-11
response to :  lspci | grep Ether

02:04.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 09)


Also when I ran sudo wireshark & I got the following:

mlamberg@mlamberg-evon410c:~$ sudo wireshark &
[1] 6166
mlamberg@mlamberg-evon410c:~$ sudo: unable to resolve host mlamberg-evon410c


[1]+  Stopped                 sudo wireshark
mlamberg@mlamberg-evon410c:~$ 


If I run just wireshark at the command line the application comes up fine, but when I click on list capture devices I get in the terminal window:

mlamberg@mlamberg-evon410c:~$ wireshark
dumpcap: There are no interfaces on which a capture can be done
dumpcap: There are no interfaces on which a capture can be done
mlamberg@mlamberg-evon410c:~$ 



BTW,  I never set up a domain could that be the problem?  Thanks for your help so far.....


Mike

---

### Post by cgkades on 2008-08-11
So all you have set is the ip address and netmask? are you getting to this forum on that computer?

---

### Post by mlamberg on 2008-08-11
correct.

---

### Post by mlamberg on 2008-08-11
BTW,  Gateway address is pointing to my router, and DNS addresses are correctly pointing to my ISP.....

---

### Post by cgkades on 2008-08-11
```

cat /etc/resolv.conf

```

---

### Post by mlamberg on 2008-08-11
mlamberg@mlamberg-evon410c:~$ cat /etc/resolv.conf
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4844
#
### END INFO



nameserver 167.206.254.1
nameserver 167.206.254.2

---

### Post by cgkades on 2008-08-11
This is really strange. I'm not exactly sure whats goign on here, but I can offer some suggestions to try, and beyond that, this is past my level of knowledge.

Try bringing your network interface down "ifconfig eth0 down"
then try to access it's settings from the gnome menu
if that doesnt work, bring your interface back up "ifconfig eth0 up" 
try again from the menu.

you can try issuing the command "sudo gnome-nettool" and see if you can mess with the drop down menu for the interfaces.

if none of that works, try to reboot. if that doesnt work, you can try to boot from the live cd and see if you can access it from there (that'll check to see if your installed drivers are all set up)

---

### Post by louieb on 2008-08-11
> **mlamberg said:**
> Also when I go to System > Administration > Network Tools and bring up eth0 interface, clicking the configure button returns "interface not found"...
Get the same thing here. Its a known confirmed bug in package **gnome-nettool**
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/184711](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/184711)

---

### Post by mlamberg on 2008-08-11
cgkades, thanks for your help so far...  Unfortunately the problem still exists even going through your latest procedure...

Louieb, thanks for jumping in here. The bug you indicated looks to be strongly related to my problem..  I also noticed it was set as low priority which is concerning since its preventing me from using wireshark on my computer (as mentioned earlier it can't find any interfaces to capture on). 

Anyway thanks to both of you for trying to help me....  I'm going to leave the post open in case you or someone else has some additional things to try....

Mike

---

### Post by Dangerousdave26 on 2008-08-12
I have the same problem and I found this answer on the net but I can not test it until later.

[http://www.alloytm.com/2008/06/20/wireshark-with-no-capture-interface-under-ubuntu/](http://www.alloytm.com/2008/06/20/wireshark-with-no-capture-interface-under-ubuntu/)

---

### Post by Dangerousdave26 on 2008-08-12
That did the trick 

sudo wireshark

From the terminal starts wireshark and it now has the ethernet cards in the list.

---

### Post by mlamberg on 2008-08-12
Yes that worked!!!!  Thank you very much......

---

