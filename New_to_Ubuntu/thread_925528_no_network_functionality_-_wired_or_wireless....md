---
title: "no network functionality - wired or wireless..."
date: 2008-09-20
forum: New to Ubuntu
---

### Post by Papa-san on 2008-09-20
Just the other day, I was having problems with my wireless. I connected a network cable to the router and was able to go online. I don't believe that I changed anything, but now I cannot even connect that way. I've never run into this before, so some help would be really appreciated!

EDIT:
OK... I managed to do something to make the wired connection work again. Now at least I don't have to type everything onto another computer... 

So... wireless?

---

### Post by halitech on 2008-09-20
what type of wireless card?

---

### Post by twitch2197 on 2008-09-20
what kind of wireless card do you have? 
open up the terminal, type
```
lspci -v | less
```
and scan through that.
example: mine says
```
Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```
if you have an atheros card, get the most recent distro of madwifi from the synaptic package manager and google for how to get that to work, as i don't recall the exact steps i went through to get mine working.
if it's not atheros, get ndiswrapper, search the forums for how to get that going, and that's all the input i have

---

### Post by willca on 2008-09-23
tried restarting your network stack?

sudo /etc/init.d/networking restart

---

### Post by Papa-san on 2008-09-27
I got it working temporarily.
Here is what I did:

I have an Intel Pro/wireless 3945ABG wireless card. It is evidently supported in Ubuntu.
The wired issue was pretty simple: once I was hooked up to the router with a network cable, I re-booted the machine. when it finished coming up, that particular function had been restored. It's the first time I have run into a wired issue on this system, and I went off (posted) too soon... I tend to do that.

Once that was done, I ran:```
sudo aptitude install network manager
```It ran into issues with WICD, so wasn't able to do it.
So:```
sudo aptitude remove wicd
``` Once completed, installing network manager worked. Then I installed WICD again. I ran it, and it connected without any problems.

That made it work for two days. Then my son showed up and hacked into my WEP security in about four minutes. He then proceeded to change it to WPA encryption. All of the Vista boxes were able to hook up right away, but my machine is in a bad way. (I'm editing this post via Vista) :-(

I have done the removing of the network manager and wicd things, (several times) but have had limited luck. The wired connection was troublesome. I had to configure it manually. (Trial and error a few times managed to get it to work for the current session. Re-boot requires me to do it over again.) I put the same information into the network manager for wireless, and it didn't work. when I go back into it, I find that the passphrase isn't what I entered. (The password is 11 characters) That box now contains something like 40 to 60 dots. I remove them all and put in my 11 again and save it. The wireless doesn't work, and if I go into the same GUI again, I find that huge string of passphrase dots again. 

I'll try to string a network cable out here and get back into Ubuntu so I can post terminal data for you.

---

### Post by Papa-san on 2008-09-30
OK,
Now I am online, so I can post the results from my terminal. I used WICD and managed to get it wirelessly, but it will not be saved through a re-boot.
```
john@john-1525n:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:41:fd:39
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:c9:92:1d
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.103 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
john@john-1525n:~$ 
```where did this logical name come from? It was 'eth1' previously. Either way, how do I get it to save it so I can have it come up with wireless turned on?

---

### Post by Papa-san on 2008-10-01
No thoughts or ideas?

---

