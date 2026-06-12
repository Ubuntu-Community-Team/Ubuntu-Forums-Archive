---
title: "Network Manager Problem"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by DrAlligator on 2008-06-13
First off, I'll admit I'm a noob and a pretty big noob. I'm still new to Ubuntu and barely know how to use the terminal, etc. I've been using Gutsy Gibbon until yesterday, when I updated to Hardy.

The first thing I did was accidentally remove the Network Manager from my task bar. The first thing I did, of course, was open the Add to Panel window - but it wasn't there, and even when I searched for 'Network Manager', I came up with nothing. I tried to follow the Help Center to no avail, and I really don't know what to do.

I'm certain it can't be that big a deal, and sorry in advance for this. :P

Thanks

---

### Post by sdennie on 2008-06-13
Getting it back depends on how you removed it.  First, I would try going to Add to Panel and adding a Notification Area.  If that doesn't work, go to System->Preferences->Session and make sure Network Manager is checked.

Edit:
If you have to use the latter, you may have to logout and login again to see the change.

---

### Post by iaculallad on 2008-06-13
"Add to Panel"-> under "System and Hardware", double click on "Network Monitor".

---

### Post by kdcoetzee on 2008-06-13
> **vor said:**
> Edit:
If you have to use the latter, you may have to logout and login again to see the change.

You can press crtl-alt-backspace to restart gnome.

And if you still don't get the panel fixed you can reset gnome settings to its default by:

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

but it reset everything connect to gnome i think.

if you just want to reset the panels i think this one is better.

```
rm -r ~/.gconf/apps/panel
```

You can backup these files first. if you are sacred by removing them. I know I was very skeptical about just deleting stuff.
Then just crtl-alt-backspace to restart gnome.

---

### Post by DrAlligator on 2008-06-13
Hm, thanks guys, I got it back. :D

Though, a new problem seems to have arisen now, in that I can't connect to my router. This wasn't ever a problem previously, though sometimes I needed to restart Ubuntu for it to connect, but it's not working *at all*. I've tried manually connecting, but it just isn't, and I'm unsure what the problem is.

---

### Post by kdcoetzee on 2008-06-13
thru wireless or Ethernet ?
and what does network-manager's icon do when you try to connect ?

---

### Post by DrAlligator on 2008-06-13
Through wireless.

The icon is two black screens with an exclamation mark inside a triangle by it.

---

### Post by kdcoetzee on 2008-06-13
Ok, 

Sad to say but I don't know if I will be able to help you.
At Home my wireless just connects sometimes and on some days never. (But I have to asked nicely for it to connect).

I presume you are on dhcp. and the wireless encryption is WPA.
When you try to connect to the wireless. does a dialog box keep popping up asking for the passkey for the wireless ?

---

### Post by DrAlligator on 2008-06-13
> I presume you are on dhcp. and the wireless encryption is WPA.
Is there a way to check?

But no, I don't get a dialogue box of any sort. It just plain doesn't connect. Could it be something the matter with my wireless card? It's an *Intel Corporation PRO/Wireless 3945ABG Network Connection*, I believe.

---

### Post by kdcoetzee on 2008-06-13
Well... When Ubuntu's network-manager picks up your wireless it auto detects the encryption type so that would not be the problem.

connect to your router. thru firefox. just brows to the IP of the router.
And check it's settings. there would be one setting where you can choose static IP or DHCP.  And you can check the encryption settings as well. 


if you are on DHCP:
And the other thing. click on the network icon , and go to the Manual Configuration , then unlock the network settings with the Unlock Button.

choose the wireless connection and click on properties.
on the top of the new window that opened . enable the roaming tick if it is not ticked.

---

### Post by DrAlligator on 2008-06-13
It was already on roaming from before, but it's not helping. I just can't connect to the router (I'm using a different computer to get on here).

---

### Post by kdcoetzee on 2008-06-13
> **DrAlligator said:**
> I just can't connect to the router (I'm using a different computer to get on here).

is the different computer connected to that router you can't connect to using your notebook'a wireless ?

what is the IP address of the different computer ? is it a windows or linux machine ?

And if you try to connect to the router with ethernet with your notebook does it work ?

---

### Post by DrAlligator on 2008-06-13
> is the different computer connected to that router you can't connect to using your notebook'a wireless ?
Yes, it is. There are four computers here, and they're all connected to the internet by the same router.

> what is the IP address of the different computer ? is it a windows or linux machine ?
It runs Windows XP, and the IP address is 192.168.1.10.

> And if you try to connect to the router with ethernet with your notebook does it work ?
Ah, it does actually. I'd tried earlier, before coming here for help, and it hadn't - but now it has.

Unfortunately, using the wire is unfeasable. The router only has space for two wires. Two of the computers are wired to the router and two (including my laptop) connect to it wirelessly. So at the moment, there are three computers that need connecting to the router through wire with only space for two.

---

### Post by bobnutfield on 2008-06-13
Open a terminal and type:

> iwconfig

Post the results

---

### Post by DrAlligator on 2008-06-13
> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Odd, my wireless was working up until the update...

---

### Post by bobnutfield on 2008-06-13
OK, your wireless is rcognized, but not receiving (no signal).  Try this:

> sudo ifconfig eth1 down

then:

> sudo ifconfig eth1 up

then:

> iwlist scan

If these do not bring up the wireless, if you have not already tried, reboot.

Bob

---

### Post by DrAlligator on 2008-06-13
I got this:

> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.
I've also already tried rebooting numerous times.

---

### Post by bobnutfield on 2008-06-13
It is eth1 that does the scanning.  Try these, one command after the other:

> sudo iwconfig eth1 mode managed

> sudo iwconfig eth1 essid any

> sudo iwconfig eth1 enc <your passphrase>

Then, just try to ping the IP address of another machine on the network.

> [QUOTE]ping <another machine's IP address>[/QUOTE]

If you get no errors, open Firefox and check if you are connected.

Post any errors you get.

Bob

---

### Post by DrAlligator on 2008-06-13
I got through without error, but when I entered the ping I got this:

> --- 192.168.1.10 ping statistics ---
51 packets transmitted, 0 received, +45 errors, 100% packet loss, time 50122ms


nd I also got this on one occasion:

> connect: Network is unreachable


---

### Post by bobnutfield on 2008-06-13
Hmmmm.....these commands should have worked because your wireless device is recognized.  Type:

> dmesg | grep eth1

just to determine that the interface is being set up at boot.  I am going to do a little research on this and unless someone else posts a solution first, I will get back to you.

Bob

---

### Post by DrAlligator on 2008-06-13
What I got is:

> dmesg | grep eth1
[   48.059896] udev: renamed network interface wlan0 to eth1
[   62.908192] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1562.207826] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1662.849860] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1796.756943] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1920.434984] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1947.258292] ADDRCONF(NETDEV_UP): eth1: link is not ready
Thanks for all this help, I really appreciate it. :)

---

### Post by bobnutfield on 2008-06-13
Do you have an "On/Off" switch on the laptop for your wireless?  Mine does, some don't.  Do you know exactly what wireless chip you have?

---

### Post by kdcoetzee on 2008-06-13
if you run ```
tail -f /var/log/messages
``` in a terminal then try to connect the wireless.

can you please post the results.

---

### Post by DrAlligator on 2008-06-13
Yeah, I have a button above my keyboard, and I rarely if ever turn it off. It's on right now. My wireless card is a *Intel Corporation PRO/Wireless 3945ABG Network Connection*.

---

### Post by DrAlligator on 2008-06-13
This is what I got, Juggernaut:
> Jun 13 15:10:46 BillyBob dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Jun 13 15:10:57 BillyBob kernel: [ 7001.174038] tg3: eth0: Link is down.
Jun 13 15:10:59 BillyBob kernel: [ 7002.789798] tg3: eth0: Link is up at 100 Mbps, full duplex.
Jun 13 15:10:59 BillyBob kernel: [ 7002.789804] tg3: eth0: Flow control is on for TX and on for RX.
Jun 13 15:10:59 BillyBob kernel: [ 7002.790096] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun 13 15:11:05 BillyBob dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jun 13 15:11:05 BillyBob dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jun 13 15:11:05 BillyBob dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun 13 15:11:05 BillyBob dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jun 13 15:11:05 BillyBob dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu


---

### Post by bobnutfield on 2008-06-13
Udev has changed the name of your wireless to eth1.  That chip uses the ipw3945 module and should usually work out of the box.  Type:

> sudo lsmod

to be sure it is loaded.  Look for the ipw3945 module associated with eth1 in the output.

---

### Post by bobnutfield on 2008-06-13
Here is another thread involving your wireless chipset.  This is some useful information for you:

[http://ubuntuforums.org/showthread.php?t=823366&highlight=ipw3945]("http://ubuntuforums.org/showthread.php?t=823366&highlight=ipw3945")

---

