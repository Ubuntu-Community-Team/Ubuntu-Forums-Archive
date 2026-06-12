---
title: "ifconfig info"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by Matt26 on 2008-07-10
where does the command ifconfig retrieve it's information from?  right now the command shows my ethernet interface as eth1 and i would like to change to eth0.

thanks.

---

### Post by Dr Small on 2008-07-10
ifconfig is showing you your network interfaces that are configured in /etc/network/interfaces .

---

### Post by Matt26 on 2008-07-10
i thought that might be the case... i have been trying to configure the interfaces file the way i want it but when i bring up ifconfig it won't show the proper information... for example- i have my ethernet adapter set up as eth0 with a static IP in the interfaces file, but ifconfig shows the ethernet adapter as eth1 with a different IP address.

my Internet works ok, but i can't get the config button work under the Network Tools in System/Administration- says The interface does not exist Check that it is correctly typed and that it is correctly supported by your system.

i replaced my motherboard recently and i wonder if that had any bearing on this issue.

any ideas?

---

### Post by Matt26 on 2008-07-11
i also just discovered that my ethernet adapter shows up as eth0 under the ubuntu 8.04 live cd in System/Administration/Network Tools- when logged into ubuntu normally is shows up as eth1 now... i still get the same error message as below when i click on the Configure button though- any idea why the ethernet adapter might be coming up as eth1 normally and eth0 under the live cd?

thanks.

---

### Post by hyper_ch on 2008-07-11
you need to restart the network interfaces after altering the interfaces file:

```

sudo /etc/init.d/networking restart

```

---

### Post by Matt26 on 2008-07-11
i have updated my /etc/network/interfaces file as follows:
[B]auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1[/B]


when i use sudo /etc/init.d/networking restart i get this:
[B]* Reconfiguring network interfaces... eth0: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.
[/B]

however under Network tools and using the command ifconfig -a show the ethernet adapter as eth1.

---

### Post by hyper_ch on 2008-07-11
then you should use eth1

or you could try to bridge it...

---

### Post by plucky on 2008-07-11
See your other post for the answer,I think

[http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)

Good Luck

:)

---

### Post by The Cog on 2008-07-11
Look at the file /etc/udev/rules.d/70-persistent-net.rules. You will probably find the answer there.

---

### Post by Matt26 on 2008-07-12
> **The Cog said:**
> Look at the file /etc/udev/rules.d/70-persistent-net.rules. You will probably find the answer there.

thanks that seemed to do the trick- i have my ethernet adapter configured properly now (static IP and eth0 instead of eth1) however i still can't get into the Configure button under the Network Tools for my ethernet adapter- still gives me the same error message interface doesn't exist- could this be a problem with the /etc/udev/rules.d/70-persistent-net.rules file?

---

### Post by The Cog on 2008-07-12
Did you edit that rules file? 
After a mummy-board change in my lappy, I had to delete the old eth0 rule and edit my eth1 rule to eth0. Reboot and everything was fine again.

---

### Post by Matt26 on 2008-07-13
> **The Cog said:**
> Did you edit that rules file? 
After a mummy-board change in my lappy, I had to delete the old eth0 rule and edit my eth1 rule to eth0. Reboot and everything was fine again.

yes i edited my rules file the exact same way and rebooted- everything appears to be fine now except that i still receive the same interface does not exist error message whenever i click on the Configure button under Network Tools for my ethernet adapter... what am is missing here?

---

### Post by The Cog on 2008-07-13
I have no idea. Does it show up as eth0 in ifconfig now?

---

### Post by Matt26 on 2008-07-13
yes it does... it shows up correctly under Network Tools as well- which it didn't before i changed the rules file..

---

