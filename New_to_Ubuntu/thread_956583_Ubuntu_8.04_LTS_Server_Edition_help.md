---
title: "Ubuntu 8.04 LTS Server Edition help"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by coojofresh on 2008-10-23
I AM a beginner with Ubuntu, but I have some understanding of how stuff works.  I am stuck on one thing though.  I have a AMD 64 something or other, I am not sure right now I will have to look when I go home, but I am able to run the Ubuntu 8.04 LTS Server Edition 64 bit version on it.  Anyway the installation went fine and takes like a few minutes.  When I get it up and running I find out that I can't connect to the internet.  I ran the command 'ifconfig' and got the loop back address, 127.0.0.1.  I tried to ping a couple sites, and things of that nature, but I figured that was pointless if I am getting a loop back address.  The box does have an ip address which I can see from my router's interface.  Oh, it is plugged up directly to the Belkin wireless router which is plugged up to the cable modem.  Prior to installing Ubuntu 8.04 LTS Server Edition I installed the desktop version on the same computer and I was able to surf the net using firefox that was on there.  I just need to see if there is a way to setting up the network card.

---

### Post by Sarmacid on 2008-10-23
I'm not sure how to configure dhcp in Ubuntu servers, but giving them a static ip address has worked for me so far

```
sudo ifconfig eth0 <ip> netmask 255.255.255.0
```

Try that with the ip you had before and see if it works.

---

### Post by coojofresh on 2008-10-23
That sounds like what I was looking for.  Thanks.

---

### Post by Sarmacid on 2008-10-23
There's a small problem with my last post, changes will be lost next time you boot, so to make it permanent, you have to modify the interfaces file

```
nano /etc/network/interfaces
```

Delete the lines with the interface you want to configure (usually it's eth0) and add these, making changes accordingly

```
auto <interface>
iface <interface> inet static
	address <ip address>
	netmask <netmask>
	network <network address>
	broadcast <broadcast address>
	gateway <default gateway>

```
Save and exit, then run
```
sudo /etc/init.d/networking restart
```

Should be working now :)

---

### Post by stickboy2642 on 2008-10-23
```
dhclient eth0
``` will tell the interface to grab a DHCP address.  Unfortunately you will have to run that command every single time you start your computer with this method.

You want to edit /etc/network/interfaces to actually configure the network for eth0.  The following file entries will tell eth0 to start automatically at boot and grab an address via DHCP:

```

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

Once entered into the configuration file, type 'ifup eth0'.
Let me know if there are any errors with this command.  If you get something along the lines of "No Such Device", then you may actually have a network card driver problem.

---

### Post by jerome1232 on 2008-10-23
It actually sounds like your network  card isn't being seen, do you have an 'eth0' interface when you type 'ifconfig', or do you just have a 'lo' interface?

---

### Post by coojofresh on 2008-10-23
yes, all i see is the 'lo' portion when i run 'ifconfig'. i have used this same box for the desktop version of Ubuntu and the network card work just fine.  i was able to get on the internet and all.

---

### Post by coojofresh on 2008-10-23
yeah, it does say no such device when i enter the code 'dhclient eth0'

---

### Post by jerome1232 on 2008-10-23
Okay I don't know much about getting that interface to work but I'm sure some more info would be helpful if you could post the output of these two commands i'm sure it'll help someone who knows this to help you.

```
lspci
sudo lshw -C network
```

makes sure to wrap the output in [noparse]```
output here
```[/noparse]tags

---

### Post by coojofresh on 2008-10-23
okay let me try them out.  thanks

---

### Post by bradmurmz on 2008-10-23
What brand of network card do you have?

---

### Post by coojofresh on 2008-10-24
i figure tonight i will try to put in an intel pro/100 s destop adapter and maybe Ubuntu server will have an easier time dealing with that network device rather than the one built in on my gigabyte motherboard.  we shall see.

---

### Post by Iowan on 2008-10-24
It's likely that the existing interface only needs a driver.  Also, if you add a different card, you may need to disable the onboard NIC in BIOS.

---

### Post by coojofresh on 2008-10-24
it is an on-board device. nVidia gigabyte motherboard type.

---

### Post by coojofresh on 2008-10-24
well i added the intel card and i re-installed it and during the installation i got the dhcp setup i was hoping for!  finally. the original problem was not solved but everything seems to be working fine now.

---

### Post by Iowan on 2008-10-25
At least with an operational system, you have a little breathing room to look for why the onboard NIC doesn't work. If it happens to be an nForce, [this]("http://ubuntuforums.org/showthread.php?t=941269") thread *may* help.

---

