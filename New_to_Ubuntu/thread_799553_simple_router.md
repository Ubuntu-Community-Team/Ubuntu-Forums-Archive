---
title: "simple router"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by fmpfmpf on 2008-05-19
i am using Ubuntu 7.10

i have 2 laptops, A and B, both with WLAN cards.
A is connected to the internet through an ethernet cable.
how can i make A function as an access point so that B can receive the signal from A and surf the internet?

i use "Create New Wireless Network", but it keeps failing. It just reverts back to itz wired connection.

thank you.

---

### Post by fmpfmpf on 2008-05-19
Additional niformation : you can say that i want to turn my laptop into a wireless hotspot

---

### Post by ugm6hr on 2008-05-19
Firestarter has this function.

[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

---

### Post by ivze on 2008-05-19
There is a package called "hostapd". Hostapd is a daemon. It deals with all related to wifi connectivity. To configure it you need to edit /etc/hostapd/hostapd.conf, but it needs understanding wifi principles to edit.
If you manage to setup hostapd, follow the instructions above related to firestarter. Firestarter + hostapd = AP.
Apart from that, if you have Atheros-based wifi card (see the output of "lspci" tool) and agree to have an open (unencrypted and public) wifi AP, there is a simpler solution, i know and can explain you.

---

### Post by fmpfmpf on 2008-05-19
any other methods?

---

### Post by Commander_Keen on 2008-05-19
Well I'm a Newbie too, but this can be done in MS.

for PC A (the hotspot) make sure its connected to the Lan.
then Assign the wireless IP address of 10.10.10.1 or something.
then on the Laptop B you could use 10.10.10.1 as your default Gateway.   
  The other thing you could do is get a wireless router and do the same thing.

---

### Post by ivze on 2008-05-19
The truth is that there is (yet) no high level gui in Ubuntu, that would let one create a wifi-inet-sharer. All, that can be done, needs system-level digging. =(

---

### Post by ugm6hr on 2008-05-19
> **ivze said:**
> The truth is that there is (yet) no high level gui in Ubuntu, that would let one create a wifi-inet-sharer. All, that can be done, needs system-level digging. =(

Eh?

Firestarter is a GUI.

I didn't have to edit anything, other than installing hostapd & firestarter.

---

### Post by fmpfmpf on 2008-05-20
i have 2 laptops and both have WLAN.
Laptop A has Ubuntu 7.10
Laptop B has Ubuntu 7.04

i am trying to link the 2 laptops using Ad-Hoc
Laptop A is the transmitter and B is the receiver

in A, i type "ifconfig eth2 10.10.10.1 netmask 255.255.255.0 broadcast 10.10.10.255 up"

B is now connected to "Test"
However, when i type "ping 10.10.10.254", it says:-
From xxx.xxx.x.xxx icmp_seq=2 Desination Host unreachable
From xxx.xxx.x.xxx icmp_seq=3 Desination Host unreachable
From xxx.xxx.x.xxx icmp_seq=4 Desination Host unreachable
and so on until i hot Ctrl + C

What is the problem?
pls help me

p/s :- i am used this website for instructions.
[http://www.wlug.org.nz/WirelessSetupNotes](http://www.wlug.org.nz/WirelessSetupNotes)

thank you

---

### Post by gnomikos on 2008-05-20
Your B card doesn't seem to have an IP adress.

sudo ifconfig eth2 10.10.10.2

to assign one(if eth2 is your interface)

Check this [guide]("https://help.ubuntu.com/community/WifiDocs/Adhoc")

---

### Post by fmpfmpf on 2008-05-20
after typing "sudo dhclient eth2" at the activation part, i get this message:-
(my WLAN is eth2)

DHCPDISCOVER on eht2 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eht2 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eht2 to 255.255.255.255 port 67 interval 20
No DHCPOFFERS received.
No worknig leases in persistent database - sleeping.

is this a problem?

tq

---

### Post by gnomikos on 2008-05-20
To use dhcp, you'll have to set up a dhcp server in one of your computers.

As you only have two pcs, it's easier to use static IP adresses.
For the first:
sudo ifconfig eth2 10.10.10.1
For the second:
sudo ifconfig eth2 10.10.10.2

---

### Post by fmpfmpf on 2008-05-20
about the Firestarter, website, i dont understand how to do it
can smoeone pls write me the commands?
i am very new to Linux
tq

[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

---

### Post by fmpfmpf on 2008-05-20
i still get the same problem
it is sleeping T_T

any other solutions?

---

### Post by gnomikos on 2008-05-20
So, you have followed the instructions of the site and created a wireless network "test" from computer A.Then you connected to "test" from computer B,correct?

Could you post the output of ifconfig and iwconfig from both computers?

---

### Post by fmpfmpf on 2008-05-20
i think i just succeeded

Laptop A
ifconfig eth2 10.10.10.1

Laptop B
ifconfig eth1 10.10.10.2

Laptop A
ping 10.10.10.2
(i receive packets)

Laptop B
ping 10.10.10.1
(i receive packets)

so, has a connection been established?

tq

---

### Post by ugm6hr on 2008-05-20
I was meaning to create a How-To when I did this...  unfortunately, I didn't :(  So this is from memory.

Let me know how it goes.

I am assuming that the 2 wifi cards both work with Ubuntu.  If you don't already know that, then this may be tricky.

Laptop A:

In System->Administration->Synaptic Package Manager
Search for and install *firestarter* and *dhcp3-server*

REbooting may be necessary here (unsure).

In System->Administration->Network (unlock it if necessary)
Wireless - disable roaming.
Configuration: Static IP
IP address: 192.168.0.1 (make sure this is different than your router - if the same, try 192.168.1.1)
Netmask: 255.255.255.0
Default gateway (IP): <leave empty>

In System->Administration->Firestarter
The Firestarter Wizard starts.
Click Forward
Select your Internet connection device (e.g. eth0 - most likely for wired)
(select "IP address is assigned by DHCP" if that is what you use - likely to be the case)
Select "Enable Internet connection sharing"
Select your wifi device (e.g. eth1, wlan0, ath0 for wifi) as Local area network device
Select "Enable area network device"
Start the Firewall.

Laptop B:

Enable wifi as you would expect, with DHCP / roaming.

Hopefully, that should work now.

I am going to give it a quick try to see how it works.

EDIT: Sorry - I see you have got it working already - didn't see page 2!!

---

### Post by gnomikos on 2008-05-20
Yes, your network is up and running!

---

### Post by fmpfmpf on 2008-05-20
ok, that is good
however, laptop B cannot surf the internet.
Laptop A is connected to the internet via Ethernet.
Both laptops A and B are connected through WLAN.

pls help
i need laptop B to be able to surf the internet

tq

---

