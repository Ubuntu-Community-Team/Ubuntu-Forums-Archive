---
title: "XBMC No Internet Connection"
date: 2013-11-22
forum: New to Ubuntu
---

### Post by daniellatu on 2013-11-22
So I've only ever used windows, but when I was setting up a HTPC my friend suggested wiping Windows and installing Ubuntu. I am an absolute novice, and finding it very difficult to get use to, but obviously forums like this are a great help.

So here is my current dilemma, I've installed XBMC, and my PC has wired internet connection, but I cannot get internet access on XBMC. From all the forums, I assume it has something to do with DNS settings in Ubuntu, but I've tried changing a few things without any luck.

I can access network files no problems, but not internet.

Really hope someone can help me out?

Thanks
Dan

---

### Post by papibe on 2013-11-22
Hi daniellatu. Welcome to the forums ):P

If I understand correctly, you installed Ubuntu, and then XBMC as an application. Is that right?

Do Ubuntu, say using Firefox, has Internet access?

Could you open a terminal, run these commands, and post back its results?
```
ifconfig

route -n

nslookup ubuntu.com

dig ubuntuforums.org
```
Regards.

---

### Post by daniellatu on 2013-11-22
Hi Papibe. Yes, installed Ubuntu, then XBMC as an application. Internet works fine on Ubuntu.

Following are results:

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:1d:88:36:33  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe88:3633/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:72215 errors:0 dropped:0 overruns:0 frame:0
          TX packets:404762 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9220631 (9.2 MB)  TX bytes:385482931 (385.4 MB)


ham0      Link encap:Ethernet  HWaddr 7a:79:00:00:00:00  
          inet6 addr: fe80::7879:ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1404  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:16134 (16.1 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:554616 errors:0 dropped:0 overruns:0 frame:0
          TX packets:554616 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:617297948 (617.2 MB)  TX bytes:617297948 (617.2 MB)


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 2245
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;ubuntuforums.org.		IN	A


;; ANSWER SECTION:
ubuntuforums.org.	477	IN	A	91.189.94.12


;; Query time: 22 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)
;; WHEN: Sat Nov 23 13:11:23 EST 2013
;; MSG SIZE  rcvd: 61


Thanks
Dan

---

### Post by papibe on 2013-11-22
Thanks.

Could you describe how you are experiencing the problem?

I imagine that you are not able to get metadata from the Internet? For instance, movie description, backdrops?

Or it is a plugin that is not working, like the weather, or youtube?

Regards.

---

### Post by daniellatu on 2013-11-22
In System information in XBMC it shows no internet connection, plus weather not working, and trying add ons with URL, not working either. Connected to network fine, as playing movies and music from other networked pc.

---

### Post by papibe on 2013-11-22
I've never experienced such a problem.

My current guess has to do with the presence of an ipv6 address on your other ethernet interface (ham0).

Let's try this:
[LIST]
[*]exit XBMC.
[*]create a file called advancedsettings.xml with this content:
```
<advancedsettings>
<network>
<disableipv6>true</disableipv6>
</network>
</advancedsettings>
```
[*]Move the file to xbmc directory:
```
mv -iv advancedsettings.xml ~/.xbmc/userdata/
```
[*]Open XBMC and check connectivity.
[/LIST]
Let us know how it goes.
Regards.

P.D.: The default weather provider (Weather Underground) hasn't been working for me either. Change it to Yahoo, and reset your location.

---

### Post by daniellatu on 2013-11-22
Thanks papibe, as I mentioned, this is literally the first time I have used Linux/Ubuntu, so sorry to be a pain, but any chance you can explain to me how to create the xml file?

Thanks
Dan

---

### Post by daniellatu on 2013-11-22
Hi papibe, 
I googled around, and found out how to do it. I've created the file you said, in the directory you said, but no change to connectivity in XBMC.

Could it have to do with the DNS settings in ipv4?

Rgds
Dan

---

### Post by papibe on 2013-11-22
No problem.

Open the text editor. You can either press the super key (windows key), or click the Ubuntu icon (first one), and then search either 'gedit' or just 'Text Editor' (no quotes).

Once the editor launches, copy and paste the previous text so that the file looks like this:
```
<advancedsettings>
<network>
<disableipv6>true</disableipv6>
</network>
</advancedsettings>
```
Save the file. To do that pres F10 to get to the menu, or hover the mouse over the desktop top bar:
```
File -> Save As
```
Save it as advancedsettings.xml

Exit the editor.

Open a terminal. Either search for terminal or press Ctrl+Alt+t then run this command:
```
mv -iv advancedsettings.xml ~/.xbmc/userdata/
```
A confirmation message should display. Something like:
```
'advancedsettings.xml'  ->  '.xbmc/userdata/advancedsettings.xml'
```
Let us know how it goes.
Regards.

---

