---
title: "New ADSL connection on new PC necessary?"
date: 2014-03-30
forum: New to Ubuntu
---

### Post by jackson21 on 2014-03-30
Hi, all
Far two years I have collected several brands of Ubuntu and others on my Desktop PC.
Logging into Internet was always done automatically  with "dhcp"with any new distro.
I have aFritzbox router 7140SL and it always comes up smoothly with the blinking leds
when I boot up any new Linux I installed. The leds settle and I can always connect into internet.

But !!!!   Bought a new computer, ASROCK FM2A55, with GbLAN !! I plugged the network cable into the new PC
The router comes up with the leds ok exactly the same as with the former  desktop PC
I installed the new  Linux Mint 16. OK  But it doesn't find my network
I installed the new UBUNTU 14.04 (Beta) , but it doesn't find my router either

 "ifconfig"  doesn't show  my ethernet  eth0 on the new PC. 

My question , where to begin ???? with . Do I have to completely reinstall and set up my

router settings  

Thank you for your patience

jackson

---

### Post by steeldriver on 2014-03-30
Probably the first step would be to identify the particular network hardware

```

sudo lshw -C network -sanitize

lspci -nnv | grep '\[02.0\]'

```

Then we can search for any known hardware / firmware / driver issues

---

### Post by jackson21 on 2014-03-30
Thank you steel driver
Please be patient, because I have to  change the computers

jackson

---

### Post by jackson21 on 2014-03-30
To steeldriver,
the "sudo" suggestion provided PCI (sysfs)

The "lspci" suggestion provided no result 
The fact is that  on the new machine  in "ifconfig" or "netstat" produces only  the "lo" interface with 127.0.0.0  and nothing else.

Very strange, that the router is not recognized at all.


Thank you anyway steeldriver,

---

### Post by pqwoerituytrueiwoq on 2014-03-30
if you are only getting [FONT=courier new]lo[/FONT] the system is not seeing the gigabit lan on the pc let alone the router on the other end
post the output of [FONT=courier new]lspci -vv[/FONT] that will be a lot of text
make sure the gigabit lan is enabled in the bios (check motherboard manual)
is is possible the lan on the board is doa, but it is too early to know that for sure
the onboard lan on my system is not reliable and requires i cut power to the system to get it to work again

---

### Post by jackson21 on 2014-04-06
Thank you all, solved, A new network card PCI  Express Ethernet card.  Plugging in the router and everything is ok.

---

