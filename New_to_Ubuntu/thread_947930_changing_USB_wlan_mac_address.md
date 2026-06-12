---
title: "changing USB wlan mac address"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by akamigs on 2008-10-14
I was able to install my USB wireless-n adapter on Ubuntu but im having trouble changing its mac address.

1) ive tried:               sudo gedit /etc/network/interfaces

   then i get this:         auto lo
                            iface lo inet loopback

   added this:              hwaddress ether xx : xx : xx : xx : xx : xx

   then finished with this: sudo /etc/init.d/networking restart

still the original MAC.

2) also tried:  ifconfig wlan1 down

then:           ifconfig wlan1 hw ether xx : xx : xx : xx : xx : xx

then:           ifconfid wlan1 up

restarted the network and still got the original MAC.

3) ALSO TRIED: installing macchanger

then:          sudo /etc/init.d/networking stop

then:          macchanger wlan1 --mac=xx : xx : xx : xx : xx : xx

last:          sudo /etc/init.d/networking start

still the original MAC!

HELP ME OUT GUYS!!

---

### Post by Krupski on 2008-10-14
> **akamigs said:**
> I was able to install my USB wireless-n adapter on Ubuntu but im having trouble changing its mac address.

1) ive tried:               sudo gedit /etc/network/interfaces

   then i get this:         auto lo
                            iface lo inet loopback

   added this:              hwaddress ether xx : xx : xx : xx : xx : xx

   then finished with this: sudo /etc/init.d/networking restart

still the original MAC.

2) also tried:  ifconfig wlan1 down

then:           ifconfig wlan1 hw ether xx : xx : xx : xx : xx : xx

then:           ifconfid wlan1 up

restarted the network and still got the original MAC.

3) ALSO TRIED: installing macchanger

then:          sudo /etc/init.d/networking stop

then:          macchanger wlan1 --mac=xx : xx : xx : xx : xx : xx

last:          sudo /etc/init.d/networking start

still the original MAC!

HELP ME OUT GUYS!!

Are you trying to spoof a different MAC address, or are you trying to get Linux to recognize a new card after having used a different one?

---

### Post by akamigs on 2008-10-14
^^spoof

---

### Post by akamigs on 2008-10-15
Also tried:   ifconfig eth0 down hw ether xx : xx : xx : xx : xx : xx up

and still no results.

any suggestions?

---

### Post by akamigs on 2008-10-17
Any help plz?

---

### Post by blazingnikons on 2009-10-27
see below

---

### Post by blazingnikons on 2009-10-27
Found this on teh interwebz:

To change your current or existing MAC address in ubuntu 9.04 just follow the follwing steps.... hope yours will be changed..

1. Open The terminal [Application-->Accessories-->Terminal]
2. Write the quoted code or copy and paste it in terminal [without the "" symbols]
"[COLOR="Green"]sudo gedit /etc/init.d/bootmisc.sh[/COLOR]"
give sudo password when prompted.
3. A file will be opened. In that file after the last line write the following codes or paste it.

[COLOR="Green"]killall dhclient
killall dhclient3
ifconfig eth0 down
ifconfig eth0 hw ether 001CC019A888
ifconfig eth0 up
/sbin/dhclient
/sbin/dhclient3[/COLOR]

4. Now save the file and restart your machine.  You can choose any combo for 001CC019A888 as this will be you spoofed address.

You are done.

---

