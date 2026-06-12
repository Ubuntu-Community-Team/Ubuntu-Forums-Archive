---
title: "Wireless recognition has disappeared?"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by brianedwardjarvis on 2008-09-15
[ATTACH]85295[/ATTACH]

(ubuntu 8.04) After updating loads of software, i can longer see any thing about having wireless internet. In the network settings image above, it used to (a couple of hours ago) say something about wireless connections along with the wired connection and point to point that are still there. How do i go back to such a glorious time? Is there a way to set up my network settings back to the way they where when i first installed ubuntu 8.04, short of actually re-installing? Any help would be greatly appreciated!

-brian

---

### Post by Crafty Kisses on 2008-09-15
Post the results of this command:
```
lshw -C network
```

---

### Post by Nathan_M on 2008-09-15
Also, have you checked to see if you're wireless is actually switched on? It really confused me for a few hours a couple of days ago, then I realised that (on my Dell laptop) pressing Fn + F2 to toggle wireless did the job!

---

### Post by brianedwardjarvis on 2008-09-15
These are the results for lshw -C network:  
*-network               
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1d:60:e0:ca:42
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.2.0 firmware=0.9-2 ip=192.168.0.197 latency=0 module=e1000e multicast=yes

When I did this command yesterday it showed info about a wireless device as well, but as you can see, it doesn't show that anymore.

Nathan_M, the computer is a desktop and doesn't have a switch that I'm aware of, or an actual function key because of that as well. 

-brian

---

### Post by aloshbennett on 2008-09-15
It could be that its not displayed in the nm-applet area because of wicd. Lets see if we can get hold of the device in some other way.
Could you try out these:
1. iwconfig
2. System->Administration-> Hardware testing.

---

### Post by brianedwardjarvis on 2008-09-15
This is the output for iwconfig:

brian@brian-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

I did hardware testing and created an account with launchpad so that i could send the results. The testing didn't ask me anything about wireless though, only my wired device.

-brian

---

### Post by aloshbennett on 2008-09-16
Ubuntu doesnt recognize your card anymore.

There are a bunch of things you could try and get the card working. Can you go thru this manual?
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#Check%20Device](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#Check%20Device)

---

### Post by brianedwardjarvis on 2008-09-19
Well I tried to go through that manual but I am stumped at the "sudo pccardctl ident" command. Nothing happens when I type it in. Then the manual says to use this command "gksudo gedit /etc/pcmcia/config.opts" to edit that file. It shows me an example and then says to substitute my data instead of what's in their example. The trouble is that I don't know how to find my data that I'm supposed to be substituting. Yesterday I used the livecd on it and got wireless to work, but I couldn't get any info from the pccardctl ident command their either though. Livecd did give me this information with iwconfig(i think):
*-network
     Description:Wirelessinterface
     physical:3
     logical name:wlan0
     serial:00:16:44:71:8b:27
     capabilities:ethernet physical wireless
     configuration:broadcast=yes multicast=yes wireless=IEEE 802.11g

I don't know if it's useful, but just in case. Where do i go from here?

-brian

---

