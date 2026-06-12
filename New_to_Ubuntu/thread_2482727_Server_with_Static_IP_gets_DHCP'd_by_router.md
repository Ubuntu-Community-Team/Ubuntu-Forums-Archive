---
title: "Server with Static IP gets DHCP'd by router"
date: 2023-01-09
forum: New to Ubuntu
---

### Post by pikewerfer on 2023-01-09
Hi all - I am a "n00b" and just started with Ubuntu (and Linux in general). I wanted to build a little server for my home office. I had an old Mac mini, so I installed Ubuntu Server 22.04.1 LTS on it. Worked like a charm. I then installed XFCE because I like to have some color on my screen :-) 

The server has a static IP. I entered it during installation. It is 192.168.2.5. I definitely did not turn on DHCP.

My router (a Speedport 3 from German Telekom) however decided to give the machine 192.168.2.165. 

I checked netplan, there was no mention of DHCP in the config.yaml. It seems to be absolutely not turned on. ifconfig on the machine shows me *.5. Pinging the machine also works only when using *.5 - there is nothing at *.165. But the router insists. 

In order to make quite sure, I did "sudo apt-get remove isc-dhcp-client" and "sudo apt autoremove" to make sure DHCP was not only inactive, but physically not on the server. I rebooted the machine - and saw the *.5 show up in the router list. For a minute. It then vanished and was replaced by the *.165 once more.

The server as such works fine, I can connect to the server from within my network. The server is also able to connect to the outside world. However, I cannot reach the server from outside, because in order to do that, I would need to be able to tell my router to open a port to that server. Which is not possible, because the router insists the server is *.165 instead of *.5.

Can anyone help me with this? I now spent several hours trying to find out what might be wrong here.... there is nothing on the server except XFCE and apache2 (yet). What might be causing this?

---

### Post by TheFu on 2023-01-09
In the router, ensure your DHCP range is outside anywhere you want static IPs and you don't have DHCP reservations enabled for the MAC of the MacMini.

Rather than describing things, please "prove it" by showing config files and running commands.  Start with the config file in /etc/netplan/ ... I fear it has network-manager as the renderer.  You want
```
  renderer: networkd
```
Also, there's no need to have any network-manager* or nm-* packages on a system with static IPs, so I purge those.  For any lurkers, if you have a system that moves networks, say a laptop, then you probably don't want to purge all the network manager packages.

---

### Post by MAFoElffen on 2023-01-09
Please post the contents of your 00-*.yaml file from /etc/netplan/ within code tags. Seeing the file, we can make recommendations. There is more than one line that may need to be changed or added.

---

### Post by pikewerfer on 2023-01-10
Hi all - thanks for your willingness to help an old "n00b". I dabbled a lot with Linux, but that was 20 years ago. Now getting back in.

The DHCP range of my router is 192.168.2.100 to 192.168.2.230. So the static address of 192.168.2.5 should be well outside the range. The renderer is indeed "networkd" - I had installed nm-packages to help me debug, but de-installed them again after finding them unhelpful. This is not a laptop, it is an old Mac mini that will sit there and be a web server. It is a clean install of 22.04.1 LTS, I only then added tasksel, xfce, and then deinstalled dhcp-client. That is it.

Here is the contents of 00-installer-config.yaml:

[COLOR=#000000][FONT=Verdana]# This is the network config written by 'subiquity'
network:
  renderer: networkd
  ethernets:
    enp2s0f0:
      addresses:
      - 192.168.2.5/24
      nameservers:
        addresses:
        - 192.168.2.1
        search: []
      routes:
      - to: default
        via: 192.168.2.1
  version: 2[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana] 
I ran sudo netplan apply to make sure it IS applied. It ran through just fine. I am starting to believe that the problem might not be the Ubuntu server, but the Telekom router.[/FONT][/COLOR]

---

### Post by pikewerfer on 2023-01-10
Oh, I also ran ip address show:

[COLOR=#000000][FONT=Verdana]pikewerfer@pikeserver:/etc/netplan$ ip addr show[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]    inet 127.0.0.1/8 scope host lo[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]       valid_lft forever preferred_lft forever[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]    inet6 ::1/128 scope host[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]       valid_lft forever preferred_lft forever[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]2: enp2s0f0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]    link/ether c8:2a:14:58:0b:7b brd ff:ff:ff:ff:ff:ff[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]    inet 192.168.2.5/24 brd 192.168.2.255 scope global enp2s0f0[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]       valid_lft forever preferred_lft forever[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]    inet6 2003:f0:af0e:7688:ca2a:14ff:fe58:b7b/64 scope global dynamic mngtmpaddr noprefixroute[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]       valid_lft 172795sec preferred_lft 86395sec[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]    inet6 fe80::ca2a:14ff:fe58:b7b/64 scope link[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]       valid_lft forever preferred_lft forever


Am I correct in saying that this shows everything is configured correctly on Ubuntu? This looks like a static IP that ends in *.5. Sigh.... my router still tells me that the machine (mac-address [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]c8:2a:14:58:0b:7b) has the *.165 ... [/FONT][/COLOR]

---

### Post by pikewerfer on 2023-01-10
Aaaaand I solved it. It was the DHCP table of the router. For some reason, he had an entry stating that this mac-address had to get *.165. Once I purged the table and had him rebuild it all, it auto-corrected itself, and now my little server has the *.5 as should be. Phew...

Thanks for listening :-) I am SURE to run into new problems, so I will keep posting here. :-)

---

### Post by TheFu on 2023-01-10
> **pikewerfer said:**
>  
I ran sudo netplan apply to make sure it IS applied. It ran through just fine. I am starting to believe that the problem might not be the Ubuntu server, but the Telekom router.

BTW, both 
```
sudo netplan gnerate
```
and
```
sudo netplan apply
```
are required.

When posting config files and terminal commands, best to always use code tags, like I did above, so we don't get incorrect indentation like the netplan.yaml above.

Also, if this is SOLVED, help the community by using the Thread Tools button and marking it so.  Help others save time and find what they seek. Please.

---

