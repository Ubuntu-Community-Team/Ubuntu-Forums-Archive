---
title: "configuring network in ibex"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-10-31
hi,i just installed ibex,which now exists in triple boot with hardy and windows xp.the installation ran smooth,and the system was up and ready.but,it failed me when i tried configuring the network from system>preferences>network configuration.mine is a static IP connection(wired mode) with the following parameters:

IP address : 10.110.6.126
Subnet mask : 255.255.255.0
default gateway :10.110.6.2
i tried filling in the above in IPv4,after having chosen "manual",but the system does not accept these three,but any two of it,for example if i fill in the first two,the third one is not remembered.how do i configure the network?
with hardy,the network works fine,with the above parameters set through system>administration>network,with wired network and static IP chosen.

---

### Post by stonecoldjha on 2008-10-31
the problem let me down and i had to reinstall ubuntu hardy and keep it in triple boot with xp and hardy

---

### Post by stonecoldjha on 2008-10-31
help me out,as i have second thoughts about continuing with ibex(though i still have hardy).hardy was much better,i could always get the  network configured easily,after installing.an ubuntu installation without a network,i believe is of no use.thanks in advance.

---

### Post by stonecoldjha on 2008-10-31
no one responding?please help.

---

### Post by stonecoldjha on 2008-10-31
hi,more than 20 people viewed my thread,but it has so far been of no help,kindly help me out,please, i am stuck getting ibex up and running.

---

### Post by Sarmacid on 2008-10-31
There was a similar thread earlier

[http://ubuntuforums.org/showthread.php?t=965416](http://ubuntuforums.org/showthread.php?t=965416)

---

### Post by macogw on 2008-10-31
System -> Admin -> Networking is gone in Ibex.

Network Manager should let you setup static IP stuff just fine.

---

### Post by stonecoldjha on 2008-10-31
so,can i not configure from the gui?

---

### Post by stonecoldjha on 2008-10-31
i know that.i also know that i am supposed to configure using system>preferences>network configuration.but its not accepting my settings for IP address,netmask and gateway in IPv4.

---

### Post by cb951303 on 2008-10-31
it's a bug, and it will get fixed soon

---

### Post by stonecoldjha on 2008-10-31
so,at the moment how should i configure the network for the time until the bug is fixed?does that mean that if i download a new ubuntu .iso 2-3 weeks later,the bug would have disappeared?

---

### Post by stonecoldjha on 2008-10-31
i wonder if others have encountered this problem with ibex?

---

### Post by reg4c on 2008-10-31
I managed to get it working but using network manager.

Then right clicking, going to Edit Connections and then on the Wired tab making a new one that is autoconnect. Then select manual, click on add and add the thing that you want.

Cheers

---

### Post by cb951303 on 2008-11-01
like already said: create a new connection but everytime you reboot you need to reselect this new connection otherwise it just keeps selectin auto eth0 because of the bug

---

### Post by Healey on 2008-11-01
Hi
I have the same problem with the live CD

I understand from this thread that I need to set up a manual connection, I am happy to give this a go but where do I find the following information

Address
Netmask
Gateway
DNS server

Thanks

Healey

Discussion is going on here
[http://ubuntuforums.org/showthread.php?t=963335](http://ubuntuforums.org/showthread.php?t=963335)

Looks like its a big problem

---

### Post by reg4c on 2008-11-01
I marked it as System Settings and Connect Automatically so for me its alright.
Try that.

---

### Post by stonecoldjha on 2008-11-01
i got it working by replacing the file "interfaces"(/etc/network/interfaces) of ibex with the one obtained from hardy,and now everything works fine.but,it doesn't sound good that it can't be configured the way it is supposed to ,i.e system>preferences>network configuration.

---

### Post by phidia on 2008-11-01
> **cb951303 said:**
> like already said: create a new connection but everytime you reboot you need to reselect this new connection otherwise it just keeps selectin auto eth0 because of the bug

Could you provide a link?

---

### Post by stonecoldjha on 2008-11-01
yeah,this one did the job
[http://http://ubuntuforums.org/showthread.php?t=965416]("http://http://ubuntuforums.org/showthread.php?t=965416").


i am also attaching a copy of my /etc/network/interfaces herewith,of course the settings need to be changed.replacing the /etc/network/interfaces with this file works.make sure that the IP address,netmask,gateway are those applicable to you,before replacing.

---

### Post by stonecoldjha on 2008-11-01
sorry , forgot to attach the file.

---

### Post by stonecoldjha on 2008-11-01
one needs to copy the contents off this file into /etc/network/interfaces,and modify the parameters.

---

