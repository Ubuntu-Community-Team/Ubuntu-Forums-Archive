---
title: "IP address has been saved in bootlocal.sh file but no effect on ip of server"
date: 2014-09-06
forum: New to Ubuntu
---

### Post by mia3 on 2014-09-06
Hello,

I have a problem with setting IP address and default gateway for a server permanently.
I've saved them in bootlocal.sh file but after reboot server, the changes no effect in IP address and gateway.
Although once I check bootlocal.sh file after reboot, the settings are in it.
The bootlocal.sh file is include:
ifconfig eth0 10.0.0.3 netmask 255.255.255.0 up
route add default gw 10.0.0.1

Is anyone that help me to set it permanently?


Thanks in advanced,

---

### Post by Doug S on 2014-09-06
Hi and welcome to Ubuntu forums.

the file /etc/network/interfaces is the place to do what you want.
First, make a backup copy so that you can go back to the original file if needed:```
cd /etc/network
sudo cp interfaces interfaces.original
```Then edit the file as root (I use nano, you use your preferred editor):```
sudo nano interfaces
```you will want to end up with something like this:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Local network interface
auto eth0
iface eth0 inet static
  address 10.0.0.3
  network 10.0.0.0
  netmask 255.255.255.0
  gateway 10.0.0.2
  broadcast 10.0.0.255
```After saving your edited file, re-boot.

---

### Post by mia3 on 2014-09-06
Hi,

Thank you for your reply.
I've used following command
sudo jed /etc/network/interfaces 
then add that setting and save it but it gives this error for saving: Error writing file /etc/network/interfaces
as I've searched in google, I've used this command as well   [COLOR=#000000][FONT=Consolas][/FONT][/COLOR][COLOR=#000000][FONT=Consolas][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]s[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]udo[/FONT][/COLOR][COLOR=#000000][FONT=Consolas][/FONT][/COLOR][COLOR=#000000][FONT=Consolas] gedit /etc/network/interfaces  but command not found
How can I save them?

Thanks,[/FONT][/COLOR]

---

### Post by Doug S on 2014-09-06
you could copy the file to your local directory, edit it there and then use "sudo cp" to copy it back.
Or just use the nano editor or vi or whatever. I think gedit is a GUI based editor, and if you are using a true server you have no GUI. I do not have gedit on my servers.
Hope this helps.

---

### Post by mia3 on 2014-09-06
Yes there isn't GUI on my server as well.
I can't go to directory /etc/network it can't cd  to /etc/network it seems there isn't network directory

---

### Post by Doug S on 2014-09-06
What version of Ubuntu Server are you running? Examples:```
doug@s15:/etc/libvirt/qemu$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"

doug@doug-64:~/config/bind$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.5 LTS"

```

---

### Post by bab1 on 2014-09-06
> **mia3 said:**
> Yes there isn't GUI on my server as well.
I can't go to directory /etc/network it can't cd  to /etc/network it seems there isn't network directory

Tell us what distro you are using.  It doesn't seem to be Ubuntu or Debian based.

---

### Post by mia3 on 2014-09-06
I've installed Ubuntu 12.04 Server (x86) iso-image on a machine named VM and Implement a server (S1) as a Virtual Machine and installed MicroCore Linux 4.0 on it.
I want to change the ip address in server.

---

### Post by mia3 on 2014-09-06
It is fixed :) 
It was needed to add "sleep 2" at the first line of bootlocal.sh file.
Thank you for your guidance.

---

