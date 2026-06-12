---
title: "[SOLVED] Wireless!!"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by burnetbj on 2008-10-31
This is what i was afraid of, IBEX no wireless. I know i read all the post of other people having issues in 7.04 and 7.10, 8.04 but I never had any issues. Come to find out my IBM r40 just had hardware that just had great support from what i read. Somewhere in mid IBEX beta updates my wireless broke was working perfect but now it doesnt.

 So i figure I will just wait for the actual release of IBEX surely it will be fixed. Unfortunately it isnt fixed which is wierd i installed OpenSUSE 11 and it works perfect, install Fedora works perfect. They all look like they are using the same application for wireless

Any ideas?

---

### Post by nhasian on 2008-10-31
can you tell us the make/model of your wireless adaptor?  Is it external USB, or PCMCIA, or internal?

please post the output of:

```
sudo lshw | grep -i net
```

and

> iwconfig

---

### Post by burnetbj on 2008-11-01
Sorry took so long to get back 

Was at work then Halloween 

anyhow 

 *-network:0
                capabilities: pm bus_master cap_list ethernet physical wireless
           *-network:1
                description: Ethernet interface
                product: 82801DB PRO/100 VE (MOB) Ethernet Controller
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
  *-network DISABLED
       description: Ethernet interface
       capabilities: ethernet physical


then the next one is 

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.

pan0      no wireless extensions.

thanks for helping

Seems like its detecting it as a different nic then before think it was intel 9345 or something like that in 8.04

That was with a hardwire .....if this needs to be done without hardwire please let me know

---

### Post by lH)4~mK0e on 2008-11-01
Double check the wireless switch and/or function key combination.  I had one distro that I used with that card and I had to turn it off and turn it back on sometimes to get it to use the wireless properly.  It had the ipw2000bg card in it.  Looks like the card is loaded according to "iwconfig" but it isn't getting your SSID from your wireless network. The area "*-network DISABLED" from your lshw command leads me to believe that it is probably just turned off.

---

### Post by burnetbj on 2008-11-01
OK im back 

So i looked up all the function keys on the IMB R40 and there is no key function to enable or disable wireless or nic for that matter. 

I am giving a rooky shot here but when I ifconfig it shows eth0 and eth1 

I can ifconfig eth1 up and down so it must be working right ? heh sorry 

When I try and connect after creating a connection I never get a green light on the upper radio button

This has worked fine from 7.04, 7.10, 8.04 and all 8.10 alphas....mid 8.10 beta it no longer works, even after complete 8.10 release install

Strange thing is it works in other distros such as OpenSUSE and Fedora

Any more ideas or help would greatly be appreciated

Thanks

---

### Post by burnetbj on 2008-11-03
OK People

Still need help, I am making some progress I guess though. I am able now to gain wireless access as long as there is no security. If the connection has WEP or WPA I cannot get anything back. 

I guess my question is now, should I wait or will there be a fix for this or should I be asking for help to uninstall network manager and reinstalling an earlier ver as this has work perfect from Feisty, Gutsy, Hardy and through Ibex alphas? 

Thanks for the help and or Ideas

Also I see 140 people have looked at this thread if you have a IBM R40 please verify if you are working in IBEX or not

---

### Post by burnetbj on 2008-11-12
OK peeps

I still cant connect to my wireless network with WPA personal with IBEX works with other distros and works with multiple devices in the house such as PSP and PS3. This is a IBM laptop R40 

Anymore ideas would be greatly appreaciated 

Wireless works fine without encryption 
Wireless times out with encryption

---

### Post by MockY on 2008-11-12
I think that NetworkManager is worth just as much as a pile of horse manure. I am not saying NM is the cause this time, but I would try out Wicd if I were you, just to make sure. I have had terrible luck with NM throughout the years, and I have completely dumped it.

Get it from [HERE]("http://wicd.sourceforge.net/download.php"). Upon install, it will automatically remove Network Manager. Very smooth install method.

---

### Post by digitaldamaru on 2008-11-13
Hi i'm a noob and having trouble with Network manager/settings Ubuntu 8.04.  I've installed ndiswrapper with the win98 driver for WG111 v2 (ID 0846:6a00).  When i have roaming active i can see my wireless network, 50% strength, but when i try to connect it keeps asking for the network key (WPA Personal).  I fill in the password - the search icon activates - 30 seconds or so goes by then it comes back with the prompt asking for the password again.  If i edit the network settings/connections dialoge box and disable roaming (it finds the network in the Network name ESSID drop down box) and fill in the password and use DHCP - i end up with the icon at the top telling me 'No Network Connection'.

The thing is when i run Ubuntu 8.10 Live i can connect no problem.  Any help would be appriciated as i'm at my wits end!


Digitaldamaru

---

### Post by igknighted on 2008-11-13
> **digitaldamaru said:**
> Hi i'm a noob and having trouble with Network manager/settings Ubuntu 8.04.  I've installed ndiswrapper with the win98 driver for WG111 v2 (ID 0846:6a00).  When i have roaming active i can see my wireless network, 50% strength, but when i try to connect it keeps asking for the network key (WPA Personal).  I fill in the password - the search icon activates - 30 seconds or so goes by then it comes back with the prompt asking for the password again.  If i edit the network settings/connections dialoge box and disable roaming (it finds the network in the Network name ESSID drop down box) and fill in the password and use DHCP - i end up with the icon at the top telling me 'No Network Connection'.

The thing is when i run Ubuntu 8.10 Live i can connect no problem.  Any help would be appriciated as i'm at my wits end!


Digitaldamaru

Start your own thread.  Your wifi card is different and will have different solutions than the OP's, so in order to make sure you both get the help you need, separate subjects should be dealt with separately.  I've got some ideas for you when you (like why are you using ndiswrapper? Almost all wireless cards have native drivers that work better/easier than ndiswrapper)

---

### Post by burnetbj on 2008-11-13
Hmmmm

I have installed Wicd and as the application seems pretty cool and all I still am unable to connect. Must be a driver issue or something. So thanks for all the help but I think I need to just fall back to Hardy. My new question is if I fall back to Hardy isnt it going to upgrade to the current Network Manager or the newest Kernal and this will put me back to a none working wireless setup? This is really starting to put tears in my beer here. I was working perfectly till Intrepid beta...alpha was fine but now its hosed 

Thanks again for all the help

---

### Post by burnetbj on 2008-11-14
Hi Everyone

Just wanted to give an update: Reinstalled Hardy and the IBM R40 works perfect again. Running 179 updates hope this doesnt hose the wireless 

Looks like Ibex is the first ver I have to skip since 6.10 my starting point

---

### Post by burnetbj on 2009-01-05
UPDATE: Wireless works great again in 8.10....not sure what they did but they apparently fixed it....

Thanks people

---

