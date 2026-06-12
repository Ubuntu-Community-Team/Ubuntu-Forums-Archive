---
title: "DNS Cache"
date: 2012-09-28
forum: New to Ubuntu
---

### Post by expatCM on 2012-09-28
My router just failed,  Replaced and the Internet is back except my machine.  Perhaps there was some corruption when the router failed.

The problem is that I cannot access web addresses.  So Firefox will not load pages and Thunderbird will not load email.  However Skype works.

To eliminate possible causes I have installed a new network card but the problem remains.

So I thought clear the dns with
sudo /etc/init.d/dns-clean
but no change.

I have booted from the CD and can access websites from there so I know the hardware is good.

Other than reinstall ... what could I  do next?

---

### Post by HiImTye on 2012-09-28
sounds like maybe the DNS server is misconfigured. to check, go to network settings > options > IPv4 Settings
if the Method is set to 'Automatic (DHCP)' change it to 'Automatic (DHCP) addresses only' and set the DNS servers to OpenDNS and see if it helps:
```
208.67.222.222, 208.67.220.222, 208.67.222.220, 208.67.220.220
```
if it is set to either 'Manual' or 'Automatic (DHCP) addresses only' then change it to 'Automatic' and see if it helps

either way, let us know how it goes, and what steps you had to do

---

### Post by expatCM on 2012-09-28
I have tried both automatic and manual.  When I tried with manual I used the opendns IP 208.67.222.222 and 208.67.220.220.   The ISP uses the router / gateway address.

The other machines sharing this connection all use automatic and the router address appears as the DNS default.  They work ...   

I have also booted with the CD using the original eth0 and find that is working as well.

Whilst skype will connect I note that it drops the connection after a few minutes.

Nothing remarkable in ipconfig.  I think this has to be some cached DNS setting relating to the old connection / router but I cannnot figure out how to find / clear that ...

---

### Post by expatCM on 2012-09-28
I have also found that if I go to 'Connection Information' in the system tray it will either list the IP addresses or show a message 'No Valid Active Connections Found'.  That is interesting since skype always is active.   So it has to be DNS ..

---

### Post by HiImTye on 2012-09-28
if you use 'manual' you have to also specify your address/netmask/gateway. that's why 'Automatic (DHCP) addresses only' is the best/easiest option for testing

try this:
```
router=192.168.0.1; server=google.com; ping=$(ping -c 1 $server | grep -o '[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}' | tail -1); echo ping=$ping; dig @$router $server | grep $ping; dig @208.67.222.222 $server | grep $ping
```replace the address in 'router=' with your router's address

if you get a line that says 'ping=' and two lines that have google.com and an IP then change "server=" to another site (one that you know isn't working). if that gives all three lines then it isn't a DNS issue

---

### Post by expatCM on 2012-09-28
I waited for skype to load so that I knew the Internet was present.  I confirmed that the IP address of the router was changed to the actual address and then ran the script.

The result was nothing doing

```
ping: unknown host google.com
ping=
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
```


oh and the nic is set to Automatic (DHCP) but for some reason the connection information does not show.

---

### Post by HiImTye on 2012-09-28
definitely sounds like a DNS problem then. here's what I get when I use it, with a working DNS setup:
```
tye@T:~$ router=192.168.0.1; server=google.com; ping=$(ping -c 1 $server | grep -o '[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}' | tail -1); echo ping=$ping; dig @$router $server | grep $ping; dig @208.67.222.222 $server | grep $ping
ping=173.194.33.38
google.com.        200    IN    A    173.194.33.38
google.com.        300    IN    A    173.194.33.38
tye@T:~$ 
```
I'm not sure what to suggest at this point, other than maybe reinstalling network services from a liveCD/USB

---

### Post by Colo993 on 2012-09-28
If possible from a terminal window run the following commands and post the results:

1. nslookup [www.google.com](www.google.com)
2. nslookup [www.google.com](www.google.com) 8.8.8.8

This will help determine if this is a DNS issue.

Thanks,

Colo993

---

### Post by expatCM on 2012-09-28
Output from the two commands is as follows

```
nslookup www.google.com
;; connection timed out; no servers could be reached
```



```
nslookup www.google.com 8.8.8.8
Server:		8.8.8.8
Address:	8.8.8.8#53

Non-authoritative answer:
Name:	www.google.com
Address: 180.180.248.34
Name:	www.google.com
Address: 180.180.248.29
Name:	www.google.com
Address: 180.180.248.39
Name:	www.google.com
Address: 180.180.248.44
Name:	www.google.com
Address: 180.180.248.49
Name:	www.google.com
Address: 180.180.248.54
Name:	www.google.com
Address: 180.180.248.24
Name:	www.google.com
Address: 180.180.248.59
```


Earlier in the thread it is suggested to reinstall networking using the CD.  How do you do that?

---

### Post by expatCM on 2012-09-29
The situation has now changed.  The Internet has returned and both Firefox and Thunderbird are functioning.

So perhaps after a period of time passed something got reset ...  I do not know but if fixed itself which makes me wonder.

However ..  it is still not quite right, the networking icon in the top right status tray still reports for Connection Information "No Valid Active Connecitons Found" and the icon is not the two up/down arrows it is a blank outline of a 40 degree arc.  I am not sure that I really care about that since the Internet is now back ....

---

### Post by Colo993 on 2012-10-02
expatCM

Based on the results of the two NSLOOKUP commands you were having a DNS problem as your PC couldn't resolve [www.google.com](www.google.com) until you used 8.8.8.8 as your DNS server.  

Are you using DHCP or hard coding an IP to your PC?  I'm not familiar with how Ubuntu measures network connectivity via the Network Icon, but I suspect it does involve some type of DNS lookup and that might explain why you are seeing the "No valid connections found" message.

Hopefully the Ubuntu gurus can provide an answer as to how Ubuntu is measuring network connectivity via the Network icon.

Colo993

---

