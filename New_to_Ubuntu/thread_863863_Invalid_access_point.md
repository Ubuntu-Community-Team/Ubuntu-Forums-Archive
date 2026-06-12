---
title: "Invalid access point?"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by Kolfinna on 2008-07-18
Hey, all.

It's been a long evening of trying to configure wireless. I figure the best thing to do is start from the beginning.

First, I had an address conflict between my new modem and my old wireless router. After unsuccessfully negotiating with the help desk for 1.5 hours, they said they would call me back (never did). I decided to take things into my own hands and try to fix the configuration from there.

For the modem, my IP address is 192.168.1.1 /16
For the router, my IP address is 192.168.2.1 /24 (it won't budge on configurations, otherwise I'd change it to /16 as well). 

I got the XP laptop to access wireless, but I'm having some issues getting wireless to acknowledge on my MEPIS laptop.
I'm sure I'm close to getting it right, but dhclient isn't negotiating an address from the router.

Here's my current configuration:

iwconfig:
lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11b/g ESSID:"Xena, Warrior Princess" Nickname:"default"
Mode:Managed Frequency:2.484 GHz Access Point: Invalid
Bit Rate=11 Mb/s Tx-Power=16 dBm
RTS thr:off Fragment thr:off
Encryption key:1234-1234-1234-1234-1234-1234-12 Security mode:open
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
------------------------------
lspci | grep -i network:
0000:06:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
------------------------------
ndiswrapper -l:
airplus : driver installed
bcmw15 : driver installed
device (14E4:4320) present (alternate driver: bcm43xx)
bcmw15a : driver installed
device (14E4:4320) present (alternate driver: bcm43xx)
lsbcmnds : driver installed
lsbcmnds6 : driver installed
device (14E4:4320) present (alternate driver: bcm43xx)
lstinds : driver installed
mrv8k51 : driver installed
netr33x : driver installed
prismnic : driver installed
wlanuig : driver installed
wlipnds : driver installed
-------------------------------

Help?

Thanks,

~Kolfinna

---

### Post by jamesrfla on 2008-07-18
Your modem IP should be 192.168.2.1 and your router IP should be 192.168.1.1

---

### Post by Kolfinna on 2008-07-18
I'll try it... but during that time I spent working with tech support, we tried changing the LAN address of the router, to no avail. It just...wouldn't accept the change. I'll try it in a mo and see what happens.

Then again, why would the addresses matter so much? Can't I just set the default gateway to the router's address, regardless of what it is? Or does the subnetting screw things up?

Thanks!

---

### Post by jamesrfla on 2008-07-18
Yeah I hate tech support. Good luck with getting it working. Maybe copying the old wireless router information like IP address and all the other good stuff might work. Good luck once again.

---

### Post by bab1 on 2008-07-19
For the modem, the IP address is 192.168.1.1/16 may be wrong.  The ```
/16
``` puts this in the network 192.168.x.x

I believe you can use either 192.168.1.x or 192.168.2.x as you 'inside' network.  Just so long as everything is *ON* the same network.  These would be 192.168.1.x/24 or 192.168.2.x/24

Or..Are you connecting this *together*?  if so; why?  What is your goal here?  I will try and help you out. :-)

---

### Post by Kolfinna on 2008-07-19
That's the thing--I tried changing the LAN address of the router to 192.168.2.2 /24, but it wouldn't take it after I kept applying the changes.
Therefore, that's why I changed the modem to 192.168.1.1 /16 with the DHCP pool starting at 192.168.2.2 /24--yes, opening up an ungodly amount of addresses within the /16, but hoping that in doing so it would at least recognize the router as being part of the network. 
On a side note, the modem does have RIP capabilities... perhaps I should just enable RIP between the devices instead.

...a big part of me wonders if I can crack into an IOS and just manually configure the interfaces from there. It'd be a heckuva lot easier...

---

### Post by Kolfinna on 2008-07-19
UPDATE:

Tech support is still incompetent.

Anyway...

I got fed up with the router and reset it to factory defaults. After doing so, I was finally able to change the IP address to: 
192.168.2.2

I released the IP addy of the modem and then enabled bridged mode, and so far it's working splendidly. 
So...that takes care of the XP machine. :P

Back to Linux, I got the interface to be recognized yesterday, but no such luck today. :( What am I missing?

Thanks!

<3 ~K

---

### Post by bab1 on 2008-07-19
I see that you have bridged your 2 networks together.  This is a lot of extra configuration.  I can't give you advice unless you give me  some spec's of the system.  So...

Are you using *both* the router and the modem?
Does it look sorta like this:
telephone line--->|modem|<--->|router|<--->xp and linux 'puters

If so, why?  Is one of these (XP or Linux) wireless?

BTW -- This is *not* a RIP problem.  It is an IP addressing problem.

---

### Post by Kolfinna on 2008-07-20
Yes, I knew RIP wasn't the problem. I was merely speculating using RIP to join the networks together in the event that I -couldn't- get the router to change IP addresses.

As I think I mentioned above, I reset the router to factory defaults and was able to change the address (finally). 

My current setup looks as such:

Modem: 192.168.2.1 /24
Router: 192.168.2.2 /24
DHCP pool: 192.168.2.2-192.168.2.15

My ISP suggested to set only the modem to bridge mode, and so far it's working swell...

Both machines are wireless.

I believe I have the IP addressing conflict solved by now... 
-----------------
The next task is getting Linux connected. I have a Fujitsu Lifebook C2110 notebok with a Dell pcmcia card for wireless. In the past, I have found that the native bcm43xx drivers within my distro (mepis) worked, but this time I've got some issues...

Here's a current readout of iwconfig:
```

eth1     IEEE 802.11b/g  ESSID:"Xena:  Nickname:"default"
         Mode:Managed  Frequency=2.462 GHz  Access Point: 00:11:22:33:44:55
         Bit Rate=11 Mb/s   Tx-Power=16 dBm
         RTS thr:off   Fragment thr:off
         Encryption key:11AA-22BB-33CC-44DD-55EE-66FF-77AA-88BB   Security mode:open
         Link Quality=100/100  Signal level=2/3  Noise level=187/100
         Rx invalid nwid:0  Rx invalid crypt:366 Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0 Missed beacon:0

```
I've removed all of the ndiswrapper drivers and have only the native bcm43xx driver running atm...

Thanks in advance!

<3 ~K

---

### Post by bab1 on 2008-07-20
First off i think you you can get rid of the bridge mode now.  it's for connecting 2 networks together (your have only 1 network now).  Second you do have an addressing problem.  The router should be a static address (192.168.2.2/24 is okay).  It should not be part of the pool.  See "DHCP pool: [COLOR="Magenta"]192.168.2.2[/COLOR]-192.168.2.15".  Make the pool [COLOR="Blue"]192.168.2.3[/COLOR]-192.168.2.15.

I assume the router is for wireless and you will use it in "AP mode".

Yes, you need to config the card to be "auto".  Then it will ask for an address and the dhcp server you are using will give it one from the pool.  Looks good so far. :)

---

### Post by Kolfinna on 2008-07-21
The router has a static address. I'd tried using it as an AP and it didn't seem to take well (probably on the fritz, with all the trouble I've had getting it to accept changes to configurations). 
I had actually tried that earlier with the DHCP pool and not bridging the modem, with no success of getting a connection. 
Essentially, I could generate ICMP traffic to the router, but not the modem.

Once I changed the pool start address range, I could ping both the router and the modem, but still couldn't access the Internet. That's when I called the ISP and they told me to bridge the modem. Once that was done, everything worked.

As for my laptop, I had a driver conflict between the native bcm43xx driver and ndiswrapper. Once I removed ndiswrapper, I found that I kept getting a ton of printk messages, which were the result of having WPA/WPA2 in place for encryption...and the card was unable to decrypt packets. I turned off the encryption/network key and everything ran smoothly.

Thanks for all your help!

<3 ~K

---

