---
title: "Ubuntu 10.04 Home Server Setup"
date: 2011-02-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Red Kelly on 2011-02-28
[COLOR=#000000][FONT=Arial]This tutorial is to setup a home server with ubuntu 10.04 LTS.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]After  many hours trawling through different tutorials and manuals (many old  and out of date) I thought someone else might be in the same boat as me,  so I wrote everything down and thought I’d post here for anyone who  might wont it.  I hope it helps.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]My  main aim was to get the internet to pass through the server and to  share some media files over the network. Having the internet pass  through the server has a few advantages as well as drawbacks. The use of  nat and having a good firewall and filtering can give you a bit better  security and control but there are some down sides like needing the  computer on all the time and a little bit more hardware in another NIC  (Network Interface Card). There are many more arguments both for and  against so I wont try to sell you ether way this is just how I like it.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]The basic things your server will need for this tutorial[/FONT][/COLOR]
[LIST]
[*][COLOR=#000000][FONT=Arial]Freshly installed ubuntu 10.04 LTS 64-bit (I don’t think anything will be different for the 32-bit version but I used 64-bit.)[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]2x NIC (Ethernet ports)[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]Separate hard drive (2TB) for media files (this isn’t mandatory, you can use any folder one your computer instead.)[/FONT][/COLOR]
[/LIST]


[COLOR=#000000][FONT=Arial]Eth0 will be the Internet connection and eth1 will be the connection to the network switch.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]**Internet connection sharring**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]We need to set the IP address for the network port (eth1) so open Terminal and type:[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]sudo sbin/ifconfig eth1 192.168.1.1 netmask 255.255.255.0 broadcast 192.168.1.255[/FONT][/COLOR]

```[COLOR=#000000][FONT=Arial](enter  password when asked, sudo will be used in almost every comand you can  skip it by first typing “sudo su” and entering your pass word, this will  sign you in as root so you don’t have to put sudo before every command  (to sign out of root type “exit”). I don’t mind hiting the 5 extra keys  so I leave them in)[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]eth0 will be left as DHCP dependant (you internet router will give it an IP address)[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Then we need to flush the rules in filters and NAT tables.[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]sudo iptables --flush[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo iptables --table nat --flush[/FONT][/COLOR]
```[COLOR=#000000][FONT=Arial]And delete all chains that are not in default filter or NAT table.[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]sudo iptables --delete chain[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo iptables --table nat --delete-chain[/FONT][/COLOR]
```[COLOR=#000000][FONT=Arial]
Now to setup the IP forwarding and masquerading.[/FONT][/COLOR] (you can find out more about these commands by typeing "man iptables" in terminal.(Press "q" to quit))
```

[COLOR=#000000][FONT=Arial]sudo iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo iptables --appent FORWARD --in-interface eth1 -j ACCEPT[/FONT][/COLOR]
```[COLOR=#000000][FONT=Arial]
Enable packet forwarding by editing sysctl.conf[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]sudo nano /etc/sysctl.conf[/FONT][/COLOR]
```[COLOR=#000000][FONT=Arial]and un-comment (remove #)[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
```
 net.ipv4.ip_forward=1
```[/FONT][/COLOR][COLOR=#000000][FONT=Arial](To  exit nano press Ctrl + x and select yes to save file then yes again to  replace existing file, you will need to do this every time we finish using nano)[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]That has set it up temporary so to save a copy of the setup just type[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]sudo iptables-save | sudo tee /etc/iptables.save[/FONT][/COLOR]
```[COLOR=#000000][FONT=Arial]Then we edit rc.local to load at start-up[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]sudo nano /etc/rc.local[/FONT][/COLOR]
```[COLOR=#000000][FONT=Arial]add the following line at the bottom before “exit 0”[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]```
 iptables-restore < /etc/iptables.save 
```[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]**Setup DHCP server**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Install dhcp server[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]sudo apt-get install dhcp3-server[/FONT][/COLOR]
```[COLOR=#000000][FONT=Arial]Dont panic. It will try to start and fail because we have not set it up yet.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]To start we need to set dhcp to work on port eth1[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]sudo nano /etc/default/dhcp3-server[/FONT][/COLOR]

```[COLOR=#000000][FONT=Arial]Change INTERFACES=”” to[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]```
 INTERFACES=”eth1”
```[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Set routing[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]sudo nano /etc/network/interfaces[/FONT][/COLOR]

```[COLOR=#000000][FONT=Arial]add the following[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]auto eth1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    iface eth1 inet static[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       address 92.168.1.10[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]        netmask 255.255.255.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]        network 192.168.1.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]        broadcast 192.168.1.255[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]up route add -host 255.255.255.255 eth1[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]auto eth0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    iface eth0 inet dhcp[/FONT][/COLOR]

```[COLOR=#000000][FONT=Arial]Now to configure DHCP but first a good idea to backup existing config.[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]sudo cp /etc/dhcp3/dhcpd.conf /etc/dhcpd.conf_original[/FONT][/COLOR]

```[COLOR=#000000][FONT=Arial]With that done we can safely edit dhcpd.conf[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]sudo nano /etc/dhcp3/dhcpd.conf[/FONT][/COLOR]

```[COLOR=#000000][FONT=Arial]comment out the lines[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]```
default-lease-time 600;
```[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]and[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]```
max-lease-time 7200;
```[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]now uncomment and change the “# A slightly different configuration” section to something like[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]```

subnet 162168.1.0 netmask 255.255.255.0{
```[/FONT][/COLOR]```

[COLOR=#000000][FONT=Arial]    range 192.168.1.101 192.168.1.200;[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    option domain-name-server 10.0.0.138;[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    option routers 192.168.1.10;[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    option broadcast-address 192.168.1.255;[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    option subnet-mask 255.255.255.0;[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    default-lease-time 600;[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    max-lease-time 7200;[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]}[/FONT][/COLOR]

```(I can't get that to be one code block)[COLOR=#000000][FONT=Arial]
The domain-name-server should be changed to whatever your DNS is on your internet router/modem[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]There  is allot of different setups you can have, read through the file for  some ideas or try “man dhcp3” in the terminal.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]**Setup samba**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]First  I set the hard drive to mount at start up. This is not a part of samba  directly but I find it annoying to mount them every time you restart the  computer.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]To find the location (eg: /media/MEDIA)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]```
 mount 
```[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]To find the UUID (eg: UUID=”749C4D8244CD6E7F”) and file system type.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]```
sudo blkid
```[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Then edit fstab[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]sudo nano /etc/fstab[/FONT][/COLOR]

```[COLOR=#000000][FONT=Arial]add the line[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]```
 UUID=749C4D8244CD6E7F /media/MEDIA ntfs defaults 0 0
```[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The default and two 0s at the end are to set the mount opptions to find out more try “man fstab” in the terminal. This should be ok for most people.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Now to the actual setup of samba,[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]sudo apt-get install samba[/FONT][/COLOR]

```[COLOR=#000000][FONT=Arial]When asked to install packeges without verification select yes.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Backup the smb.conf[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_original[/FONT][/COLOR]

```[COLOR=#000000][FONT=Arial]Now to edit smb.conf[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]sudo nano /etc/samba/smb.conf[/FONT][/COLOR]

```[COLOR=#000000][FONT=Arial]Find the “; interfaces = 127.0.0.0/8 eth0”[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]remove the ; and change to read[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]```
interfaces = eth1
```[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]and find “; bind interfaces only = yes”[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]and remove ;[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]then move to the end of the file and add[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]```
[MEDIA]
```[/FONT][/COLOR]```

[COLOR=#000000][FONT=Arial]    comment = Music, Movies and TV Shows[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    path = /media/MEDIA[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    browsable = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    gest ok = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    read only = no[/FONT][/COLOR]

```[COLOR=#000000][FONT=Arial](again I can't figure out how to stop this moving into to code boxes, [MEDIA] should be at the top with the rest indented with spaces below it.)
This  setup will allow anyone who can connect to your network to be able to  read and right the share /media/MEDIA. There are many different ways to  setup samba there are lots of examples in the smb.conf and even more  information by “man smb”[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]**Now restart the computer and your all done!**[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I  you’d like to find out more you you can try as I have mentioned by  useing the “man” comand to get the manual for that program, also I found  these website helpful:[/FONT][/COLOR]
[[COLOR=#000099][FONT=Arial]_http://www.linuxhomenetworking.com/_[/FONT][/COLOR]]("http://www.linuxhomenetworking.com/")
[[COLOR=#000099][FONT=Arial]_https://help.ubuntu.com/community/Internet/ConnectionSharing_[/FONT][/COLOR]]("https://help.ubuntu.com/community/Internet/ConnectionSharing")
[COLOR=#000000][FONT=Arial]and don’t forget Google and the Ubuntu forums are your friends :) [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Feel  free to post a question I’ll try to help with any problems or if  something isn’t clear. It may take me a day or more to get back to you  but I shall do my best to help you.[/FONT][/COLOR]

---

