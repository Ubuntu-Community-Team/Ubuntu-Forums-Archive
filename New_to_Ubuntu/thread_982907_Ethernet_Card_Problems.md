---
title: "Ethernet Card Problems"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by wabbit46 on 2008-11-15
I have re-installed ubuntu 8.04. 

I have set the static IP address details for my computer using System->Network. The interfaces file has the correct details in it.
I have also included the IP address in the hosts file. Using ifconfig eth0 in a terminal identifies the file.

Yet when I use Network Tools click on eth0 and select properties it says "The interface does not exist". I can ping the computer from a Windows computer but cannot ping anything from the ubuntu computer.

Have I missed some basic step ?

---

### Post by shredder12 on 2008-11-15
well i was having some similar problems regarding ethernet connections with the new kernel..
but i think you haven't yet downloaded the new kernel (24-21) you might still be using the default one provided initially ( 24-16 ) so it could be the drivers...for your ethernet card..
I was having issues with the drivers provided by Ubuntu for the ethernet card..so in order to connect to internet i had to restart the system a few times.. try it...may be it could help..to at least connect to internet once..
also give the output of the following command..
```
lspci
```

---

### Post by wabbit46 on 2008-11-15
Shredder the the strange thing is that I have had it working before using the default but my installation got corrupted.

The ispci command return the message "command not found"

---

### Post by shredder12 on 2008-11-15
its not ispci its "lspci"...
be carefull dude..

---

### Post by shredder12 on 2008-11-15
> **wabbit46 said:**
> Shredder the the strange thing is that I have had it working before using the default but my installation got corrupted.

so you mean after the fresh installation you were able to access net..but you had problems later on..
correct me if i m not able to get u??

---

### Post by SamNSane on 2008-11-15
I'm not certain from your description, but I think your main problem is the network-manager applet. It's difficult to use with fixed IP addresses, and it really, really wants to connect you to any network as a "roaming" client. With this manual editing of files you are trying to fight it, but I think it's winning. It certainly kicked my butt when I was fighting with it.

From my perspective, and I may be all wet, you could make some choices to make your life easier.

1. You could find a way to use dhcp to get your IP address assignment. (Obviously, not happening if you have no control over your network environment and are required to use a specific fixed IP address.)

2. You could use 8.10, assuming your hardware will support it. (If it runs 8.04 it will almost certainly run 8.10.) Intrepid still has some teething problems which made me decide to stick with 8.04, but it could be just the ticket for this problem. The network-manager in Intrepid is HUGELY improved over the same applet in Hardy. You will be able to configure your network locations right through the applet and not mess around with manual editing of the network configuration files.

3. If you save a fixed IP profile within the manager, and then just open network-manager each time you log on and use it to call up and use that profile, that may work -- sort of. I used this method myself until I got sick of spending the first five minutes of every session trying to get connected on the networks that used fixed IP addresses.

4. You can use wicd to replace the network-manager. If you're staying with 8.04, this is almost certainly the easiest way to go. It just works. Their Web site has instructions for installing it under Ubuntu. (You add their repository and cert under synaptic, reload, and then search for and install wicd.) It automatically removes network-manager and all of your headaches with networking in one fell swoop.

There is a proviso which should prevent you from using wicd under some circumstances. If that system is used by other users who shouldn't have admin access to any settings, wicd doesn't use the keyring, so anyone who's logged on can change network settings.

I hope you'll find a solution.

---

### Post by wabbit46 on 2008-11-15
lspci returns a whole screen full of information Host Bridge, RAM Memory etc and Ethernet controller: nVidia Corporation nForce2

---

### Post by shredder12 on 2008-11-15
that' what i want you to post...jst copy and paste it here..

---

### Post by wabbit46 on 2008-11-15
> **shredder12 said:**
> so you mean after the fresh installation you were able to access net..but you had problems later on..
correct me if i m not able to get u??

Before I re-installed ubuntu I was at least able to see the properties of the network card but not access the net. I was also able to ping my Windows box.

---

### Post by wabbit46 on 2008-11-15
> **shredder12 said:**
> that' what i want you to post...jst copy and paste it here..

Here it is :-

lspci 
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev a2) 
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2) 
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2) 
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2) 
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2) 
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2) 
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4) 
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2) 
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) 
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) 
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) 
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1) 
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1) 
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3) 
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2) 
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2) 
01:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) 
02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)

---

### Post by shredder12 on 2008-11-15
i don't think that there i any problem with the card..
well first of all after you have configured the static ip address setting in your network manager try to check whether the changes have actually taken place..
```
sudo ifconfig eth0
```
and check whether the changes have actually taken place or not..
well you may also try to install the drivers which might have been provided to you by the manufacturer in the form of a cd..there you might find a folder for linux drivers..If they are provided then try installing them and then try to connect to internet..
hope it works..

---

