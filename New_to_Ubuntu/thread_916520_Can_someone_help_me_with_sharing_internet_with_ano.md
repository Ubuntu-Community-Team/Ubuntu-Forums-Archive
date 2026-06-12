---
title: "Can someone help me with sharing internet with another computer"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by akmchciken on 2008-09-11
Hello,
I am a new user that just installed Ubuntu today on my laptop and currently playing around with it.  I am having problems trying to set up internet connection sharing.  I have a desktop computer that is running windows xp that I would like to connect to the internet through my laptop.  My desktop is connected to my laptop through a crossover cable.  My laptop is connected to the internet through a wireless connection to my router.  Can anyone walk me through with how to set this up?  I have already tried searching on google for this, but couldn't figure it out.

Whenever my desktop is connected to my laptop it doesn't allow it to connect wirelessly to my router.  And it stays this way until I unplug the cable.  I wasn't able to locate the option to select my wireless connection as the default connection.

Thanks

---

### Post by skippuff54 on 2008-09-11
sounds like what u're tryin to do will require what's called a bridge. u need to bridge your network interfaces. search for documentation related to bridge, bridging connections etc.

if u have two network cards, wifi/wired whatever, u will need to tell one to catch the internet and send it over to the other, and the second one to take the internet from the first one and hook it up for your second comp.

you can use terminal to see your network interfaces. do ```
sudo ifconfig
``` for ur interfaces. another command, to look just at wifi, is ```
sudo iwconfig
```

what u'll be doin is bridging those two interfaces. look in the forums and the wiki and let us know if that's gonna help u

---

### Post by akmchciken on 2008-09-11
Hello again,
I found this page that is related to what I am trying to do.
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

I followed the guide exactly up to the part before the section on "Advanced Gateway Configuration" except I modified a bit since eth1 connects to the internet for me instead of eth0.  It is not working for me.  Once I connect the cables between my desktop and laptop, I can no longer access the internet on my laptop and neither does the internet work on my desktop.

thanks again

---

### Post by gvartser on 2008-09-11
The easy way to do this and this also allows you to connect to the internet from your XP machine without having your laptop online is to buy a router.

Another good thing about the routers are that you also have a built-in firewall.

Price for a router starts at: 20 Euros which is a fair price.

Best regz,
/g

---

### Post by akmchciken on 2008-09-11
I already have a wireless router.  That is how my laptop is connecting to the internet.  I am trying to use my laptop to share an internet connection with my desktop.  I am unable to move my router and my desktop computer is too far away from it.   I could buy a wireless adapter for my desktop, but I was hoping I can do this without spending any money.  I was able to share the connection when both of my computers were running windows xp so I was hoping that I could figure out how to do it using ubuntu as well.

---

### Post by gvartser on 2008-09-11
Why not buy a Ethernet cat 5/6 cable. Thats really cheap.

/g

---

### Post by akmchciken on 2008-09-11
my router is on a different floor from those 2 computers.  It's not convenient for me to set up such long cables.

---

### Post by gvartser on 2008-09-11
I understand, was more of a joke.. ;)

One question though, when you connect your 2 comps, are you then able to communicate between the 2 computers, what does you XP machine say while doin a ipconfig /all from the cmd prompt?

---

### Post by akmchciken on 2008-09-11
Good morning,
I tried typing ipconfig /all and this is what I got:

Connection-specific DNS Suffix . :
Description. . . . . . . . . . . :Realtek RTL8102E Family PCI-E Fast Ethernet NIC
Physical Address. . . . . . . . . :00-21-85-49-5A-4B
Dhcp Enabled. . . . . . . . . . . : Yes
Autoconfiguration Enabled . . . . : Yes
Autoconfiguration IP Address. . . : 169.254.61.39
Subnet Mask . . . . . . . . . . . : 255.255.0.0
Default Gateway . . . . . . . . . :

---

### Post by akmchciken on 2008-09-11
Can anyone tell me how to choose which connection I want to use to connect to the internet when I have a ethernet cable plugged into the laptop?

---

### Post by Iowan on 2008-09-11
> **akmchciken said:**
> H Once I connect the cables between my desktop and laptop, I can no longer access the internet on my laptop and neither does the internet work on my desktop.

thanks againUsing Network Manager? It only allows one connection at a time.  As many times as I've linked to the ICS help page, you'd think I'd have read it (but nooo).  Your solution *may* be as simple as editing **/etc/network/interfaces** file and verifying an "auto" line for ethernet and wireless.

---

### Post by Ntweat on 2008-09-11
Configure apache2 as a proxy... this how we share net in hostel... it works...

---

### Post by Perkins on 2008-09-11
Ok.  We're going to cheat, because I'm lazy, and you're new at this, and it should be really easy with the automated tools.

Step 1:  Go into the add/remove programs thing in the applications menu.
Step 2:  install Firestarter.
Step 3:  run Firestarter.

When it asks you which interface is your internet connection, point it at your wireless card.  When it starts asking about sharing the internet connection, turn it on.  Viola, should work.  No muss, no fuss, and you can configure your firewall too.

Of course, were I you, I would probably just go get one of those USB wireless adapters instead.  Then you're not dependent on your laptop being present, on, and plugged in to be able to use your desktop.  But hey, whatever floats your boat.

---

### Post by barney385 on 2008-09-11
You have a special use IP adddy. Yours is incapable of obtaining static IP's. 

Check your wireless settings. It could be as simple as setting it to roaming.


Good Luck

---

### Post by akmchciken on 2008-09-12
I just tried installing firestarter and it didn't work for me.  I still get no internet on both computers when they are connected.  In my network settings both my wireless connection and wired connection has roaming mode enabled.  

> **Iowan said:**
> Using Network Manager? It only allows one connection at a time.  As many times as I've linked to the ICS help page, you'd think I'd have read it (but nooo).  Your solution *may* be as simple as editing **/etc/network/interfaces** file and verifying an "auto" line for ethernet and wireless.
How do I verify an auto line for ethernet and wireless?  My /etc/network/interfaces file looks like this:

auto lo
iface lo inet loopback

---

### Post by Perkins on 2008-09-12
I've never tried to do this with a wireless card involved.  I've had issues in the past with trying to use both at the same time because when you plug in the cable, the machine is configured to prefer the wired interface.  (Makes sense normally, but not for this.)  So you might be getting no internet because your laptop is trying to use the wired interface, which only goes to your other machine.

Unfortunately, I'm not entirely sure how to change it.  It *might* work to put the two interfaces on separate subnets, and set your default route out through the wireless card.  I'm not entirely sure about the details of how to make it pass traffic through though.

The other option would be to bridge the two interfaces together.  I've never set that up on a Linux machine though, so I'm afraid I can't give detailed instructions about how to do it.  I just know it's possible.

---

### Post by skippuff54 on 2008-09-12
did u try bridging the connections? 

also in /etc/network/interfaces, u should see an entry for at least one of ur ethernet cards, like eth0. if u do in terminal ```
sudo ifconfig
``` u'll see wired interfaces, if u do in terminal ```
sudo iwconfig
``` u'll see wireless interfaces.

ur /etc/network/interfaces file should list at least one of those. somethin like "auto eth0 inet dhcp" the one that says "lo" is the local interface, which essentially allows u to connect to localhost (the machine ur on)

strange that neither of the others r listed.

---

### Post by skippuff54 on 2008-09-12
another tip FYI don't post ur whole IP address in these forums or anywhere else on the net.

---

