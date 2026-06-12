---
title: "config sys networking folder missing"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by mnettrour on 2012-06-03
Hello and help please!
Ubuntu 10.0 did a system update. Now no network connection.
In configuration editor system, the networking folder is missing.
 
cat /etc/network/interfaces reveals:
auto lo
iface lo inet loop back
 
sudo lshw -C network shows the ethernet "card" (built into motherboard) is there and not disabled
 
My port on the router is not blinking (I suspect because networking folder and keys are missing so nothing to tell the hw what to do)
 
ifconfig -a shows:
eth0 and the correct mac address and all the usual stuff(sorry no thumb drive)
 
of course because of the above I cannot ping the router but loopback works so assuming the ethernet hardware is good.
 
I assume I need to restore the networking folder. How do I do this? I have the Ubuntu 6 disk that I did the original install with. If I need to make a live update disk (had a linux guru mention this) how do I do it.
 
First trouble in 3 years, but because of this, inability to connect to home windows network, about to have a illcit affair with Windows 7. :) 
 
 
Thank you for any assistance

---

### Post by steeldriver on 2012-06-03
the new way of doing things in desktop (non-server) configs is via Network Manager (actual service name is network-manager) and in that case the /etc/network/interfaces file *should* contain only the lo (loopback) definition - not sure when the changeover happened but that is certainly the way in 11.10 (with some futher changes in 12.04 regarding DNS and resolv.conf)

everything else gets moved over to /etc/NetworkManager/NetworkManager.conf and specific non-default interface defs in /etc/NetworkManager/system-connections

to see what NetworkManager is doing you can type

```
nm-tool
```

---

### Post by mnettrour on 2012-06-03
Okay, here is what nm-tool displays:
state disconnected
device eth0
wired
8169
unavailable
no
carrier detect yes
10MBS
wired properties carrier off
 
I did have a networking folder before this happened
 
I have tried several sudo commands from any forums to bring the eth0 up.
At the moment my system cannot see eth0.
 
Thanks. Appreciate any ideas on how to turn the wired back on.

---

### Post by steeldriver on 2012-06-03
well I don't really know what to suggest, it looks like you have a Realtek device (8169), if it was working before my guess would be a driver or firmware update has broken it (did you just update or actually upgrade to a new major version i.e. 11.xx or 12.xx?) since it doesn't even seem to be bringing the interface up (State: unavailable)

you could try something really quick, just remove and reinsert the kernel module

```
sudo rmmod r8169
sudo modprobe r8169 
```beyond that I guess it would be a matter of figuring out what version / firmware you have got and if there are any specific bug reports / fixes related to that 

```
modinfo r8169 | grep -v alias

```

---

### Post by mnettrour on 2012-06-04
This is version 10.4.0, it worked fine until I let it load updates. I tired the sudo rmod/Modprobe no change. I looked at a bunch of other similiar posts and stopped and restarted network-manager. Stopped fine had to restart the computer in order for restart network command to work. I still think the Network Folder now being gone out of configuration editor is my problem. The R8169 is there but wired connection not available. In windows if the network was missing from Device manager the network card would be unseen by the CPU.  Also noticing some unstableness, it now does not recongnize nm-tools and it worked yesterday.  I keep reading the horror stories about 12.04 release and the network connection problems many are having and wonder  I want to updgrade if I can get this thing working. Thinking that a reload is in order I have the orginal 6.0 disk should I use that or can I build a live disk on my windows machine? Thanks.

---

### Post by steeldriver on 2012-06-04
if this is a default wired connection running under the new network-manager service, then there will be no "networking folder" - really what happens under Windows is irrelevant

if it is a NON-default connection (i.e. you manually specified an IP address and/or DNS) then it would be under /etc/NetworkManager/system-connections

the /etc/network/interfaces file should contain only the lo (loopback) interface, as yours does - if

```
nm-tool
```doesn't work then you have problems with the whole network-manager package; I would reinstall *that* before going medieval and reinstalling the whole system (which may break other things)

---

### Post by mnettrour on 2012-06-05
A couple of things. nm-tool works again. When I replaced the auto lo and loop back in the interface folder with auto eth0 iface eth0 inet dhcp, it reestablished the network folder under configuration manager.But still  no wired network connection. Then it went away again and I deleted auto eth0, iface eth0 inet dhcp and put the auto lo and loop back back in.
Today when I restarted from hibernation I had a red square in my upper right to the left of the icon telling me I have no connection telling that something was wrong with update manager and try to manually reconfigure. Tried that it said the update are current, then it tried to access the web. I am open to anything but at this point cannot find what I can do that would start the wired network connection to work.
 
Appreciate any ideas, but medevial  or not, this thing does not work. I have mantained a NT network and after a certain amount of trouble shooting it is was much easier to wipe a system than spend time trying to find the problem. It is interesting   if you have the time but I have about 10 hours invested in this and about ready to build a live CD and see what happens on a reinstall. It is a simple problem I'm sure but I can't find it. Thanks.

---

### Post by steeldriver on 2012-06-05
sorry, I don't know how things work in 10.xx 

in 11/12 afaik the default behavior is that any interfaces defined in  /etc/network/interfaces are NOT managed by the network-manager service -  to make such interfaces appear you would need to edit  /etc/NetworkManager/NetworkManager.conf and change

```
[ifupdown]
managed=false
```

to

```
[ifupdown]
managed=true
```

it *may* be the same in 10.xx but I don't know - ymmv

---

### Post by mnettrour on 2012-06-06
Mine says false. I can see  it by going into the etc folder network, but when i use a sudo command and try to edit nothing there. To tired to play with it today. Worked on my motorcycle. Much more straight forward than Ubuntu. :).

---

### Post by mnettrour on 2012-06-12
I was able to get into: /etc/NetworkManager/NetworkManager.conf  and change
[ifupdown]
managed=false
 
to:  [ifupdown]
managed=true
 
Rebooted still the same the system does not see the network card as being there. the wired connection is grayed out in the upper right corner.
 
nm-tool still reports:
 
state disconnected
device eth0
wired
8169
unavailable
no
carrier detect yes
10MBS
wired properties carrier off
 
I really hate to wipe the machine and put XP on it. (I own a copy and certainly would not put Vista or pay $299.00 for Windows 7. From what I have seen on the forums lots of folks are having the networking problems with Ubuntu 12. 
 
Appreciate any ideas. I did notice that the system had a file in the NetworkManager folder called 

NetworkManager.conf.oldpkg (something like that) it was the same as the networkmanager.conf so I also changed it to true and rebooted. Same problem.

---

### Post by mnettrour on 2012-06-13
I tried sudo dhclient it could not get a lease, did sudo /etc/init.d/networking restart command worked but still no wired connection nm-tool same report
 
state disconnected
device eth0
wired
8169
unavailable
no
carrier detect yes
10MBS
wired properties carrier off
 
any ideas? tried everything  that has been suggested

---

### Post by stoat09 on 2012-07-02
steeldriver - New install of 12.04 on laptop with Realtek r8169 kernel module and had wireless but no wired connection, never seen that before! Your simple fix at #8 works a treat. Thanks.
Chris

---

