---
title: "localhost and hostname"
date: 2014-08-27
forum: New to Ubuntu
---

### Post by engineer2 on 2014-08-27
Hello guys ..well i'm having a problem with localhost and hostname i don't need my hostname to be the localhost .. how do i make sure of that?

---

### Post by theDaveTheRave on 2014-08-27
Hi,

We have a nice question but without any idea of how to help.

What exactly are you trying to do ?? ... however, in an attempt to help...

_If you are running a local web server (apache / nginx etc)_

then in your web browser you should be able to put either 
[http://localhost](http://localhost)
[http://127.0.0.1](http://127.0.0.1)

If you have a server somewhere, that has a specific hostname, and this tallies up with the hostname of the computer, then you should also be the name of this computer in your browser to get the basic web page.

If you are on a pc at home, you may not be able to use the name of your computer to connect to it unless you have it in a local DNS.


____________
give us some more info, and we may be able to be more specific.

David

---

### Post by fantab on 2014-08-27
You will have to add it yourself, read the link for more: [http://askubuntu.com/questions/87665/how-do-i-change-the-hostname-without-a-restart](http://askubuntu.com/questions/87665/how-do-i-change-the-hostname-without-a-restart)

---

### Post by JKyleOKC on 2014-08-27
> **engineer2 said:**
> Hello guys ..well i'm having a problem with localhost and hostname i don't need my hostname to be the localhost .. how do i make sure of that?
They are **not** the same, although in anyone's case they certainly appear to be. Think of the difference between your "legal name" by which the world knows you, and the simple word "me." Everyone refers to themselves as "me" but for the world, your name is not "me."

Similarly, the hostname of a machine is the name by which it's known to the world at large (at least, if it lets the world know its hostname). However, "localhost" is the machine's equivalent of "me" and always refers to the machine on which it's used. When **I** use "localhost" here it means the machine on which **I'm** typing. When **you** use it, it's the machine on which **you** are typing. My hostname on this machine is "mehitabel" and if you were to refer to "mehitabel" (and if I had made the hostname globally known) it would refer to **my** machine, not yours.

Thus the two names are already always different to the outside world, although they do refer to the same machine on the inside.

---

### Post by engineer2 on 2014-08-27
i'm trying to install a software (grid engine) and of the points i need  to be aware to successfull installation is that "change the hostname so  that it wouldn't be the local host" so i didn't understand what is this  exactly or how to do it ... 
here is /etc/hosts :

```
root@gridmaster:/home/gmaster# cat /etc/hosts
172.0.0.1    localhost
192.168.88.235    gridmaster

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


```


and the other thing is that whenever i try to ping <hostname> i've got this :
```
root@gridmaster:/home/gmaster# ping gridmaster
PING gridmaster (192.168.88.235) 56(84) bytes of data.
From 10.10.10.1 icmp_seq=1 Packet filtered
From 10.10.10.1 icmp_seq=2 Packet filtered
From 10.10.10.1 icmp_seq=3 Packet filtered
From 10.10.10.1 icmp_seq=4 Packet filtered
^CFrom 10.10.10.1 icmp_seq=5 Packet filtered

--- gridmaster ping statistics ---
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 20052ms

```

i have to write hostname.local :
```

root@gridmaster:/home/gmaster# ping gridmaster.local
PING gridmaster.local (192.168.2.4) 56(84) bytes of data.
64 bytes from gridmaster.local (192.168.2.4): icmp_req=1 ttl=64 time=0.047 ms
64 bytes from gridmaster.local (192.168.2.4): icmp_req=2 ttl=64 time=0.047 ms
64 bytes from gridmaster.local (192.168.2.4): icmp_req=3 ttl=64 time=0.038 ms
^C
--- gridmaster.local ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 0.038/0.044/0.047/0.004 ms

```

but i need to remove that .local

---

### Post by nerdtron on 2014-08-27
What is the output of "ifconfig"? It seems this is not a hostname issue but a network issue.

---

### Post by sandyd on 2014-08-27
> **engineer2 said:**
> i'm trying to install a software (grid engine) and of the points i need  to be aware to successfull installation is that "change the hostname so  that it wouldn't be the local host" so i didn't understand what is this  exactly or how to do it ... 
here is /etc/hosts :

```
root@gridmaster:/home/gmaster# cat /etc/hosts
172.0.0.1    localhost
192.168.88.235    gridmaster

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


```


and the other thing is that whenever i try to ping <hostname> i've got this :
```
root@gridmaster:/home/gmaster# ping gridmaster
PING gridmaster (192.168.88.235) 56(84) bytes of data.
From 10.10.10.1 icmp_seq=1 Packet filtered
From 10.10.10.1 icmp_seq=2 Packet filtered
From 10.10.10.1 icmp_seq=3 Packet filtered
From 10.10.10.1 icmp_seq=4 Packet filtered
^CFrom 10.10.10.1 icmp_seq=5 Packet filtered

--- gridmaster ping statistics ---
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 20052ms

```

i have to write hostname.local :
```

root@gridmaster:/home/gmaster# ping gridmaster.local
PING gridmaster.local (192.168.2.4) 56(84) bytes of data.
64 bytes from gridmaster.local (192.168.2.4): icmp_req=1 ttl=64 time=0.047 ms
64 bytes from gridmaster.local (192.168.2.4): icmp_req=2 ttl=64 time=0.047 ms
64 bytes from gridmaster.local (192.168.2.4): icmp_req=3 ttl=64 time=0.038 ms
^C
--- gridmaster.local ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 0.038/0.044/0.047/0.004 ms

```

but i need to remove that .local
What is the IP Address of the computer on the network? You can find that by running *ifconfig*(Note, I dont know what this is, so in the below info, it will be shown as <ipaddress>)

Is it static? (It should be).

In /etc/hosts, remove
```

192.168.88.235    gridmaster
```
add
```

<ipaddress> gridmaster
```

---

### Post by JKyleOKC on 2014-08-27
> **engineer2 said:**
> i'm trying to install a software (grid engine) and of the points i need  to be aware to successfull installation is that "change the hostname so  that it wouldn't be the local host" so i didn't understand what is this  exactly or how to do it ... 
here is /etc/hosts :

```
root@gridmaster:/home/gmaster# cat /etc/hosts
172.0.0.1    localhost
**192.168.88.235    gridmaster**

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


```


and the other thing is that whenever i try to ping <hostname> i've got this :
```
root@gridmaster:/home/gmaster# ping gridmaster
PING **gridmaster (192.168.88.235)** 56(84) bytes of data.
From 10.10.10.1 icmp_seq=1 Packet filtered
From 10.10.10.1 icmp_seq=2 Packet filtered
From 10.10.10.1 icmp_seq=3 Packet filtered
From 10.10.10.1 icmp_seq=4 Packet filtered
^CFrom 10.10.10.1 icmp_seq=5 Packet filtered

--- gridmaster ping statistics ---
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 20052ms

```

i have to write hostname.local :
```

root@gridmaster:/home/gmaster# ping gridmaster.local
PING **gridmaster.local (192.168.2.4)** 56(84) bytes of data.
64 bytes from gridmaster.local (192.168.2.4): icmp_req=1 ttl=64 time=0.047 ms
64 bytes from gridmaster.local (192.168.2.4): icmp_req=2 ttl=64 time=0.047 ms
64 bytes from gridmaster.local (192.168.2.4): icmp_req=3 ttl=64 time=0.038 ms
^C
--- gridmaster.local ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 0.038/0.044/0.047/0.004 ms

```

but i need to remove that .localIf you change the line in /etc/hosts that I emphasized above so that the address of 88.235 becomes 2.4 as in the final ping example, that should do the trick for you.

The ".local" is added by the search algorithm and really has no connection to the "localhost" name. It comes from "avahi" which is invoked by the name-lookup process if the higher-priority searches fail. Once you correct the entry in the /etc/hosts file, it should take precedence and everything should work as you expect.

I'm assuming, from your examples, that the second ping example actually does show the correct address. The request by nerdtron for the result of "sudo ifconfig -a" will show the actual address...

[COLOR="#FF0000"]EDIT: Incidentally, the first line of the hosts file should begin with "127" rather than "172" or many other programs will go crazy. This could be a typo if you manually re-typed the output, but if it's a screen capture you need to be sure and correct it![/COLOR]

---

### Post by engineer2 on 2014-08-27
the ip address is static 
and this is the ifconfig output :
```

eth0      Link encap:Ethernet  HWaddr 20:1a:06:5e:b9:e8  
          inet addr:192.168.88.235  Bcast:192.168.88.255  Mask:255.255.255.0
          inet6 addr: fe80::221a:6ff:fe5e:b9e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13859 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2841117 (2.8 MB)  TX bytes:8712291 (8.7 MB)

eth1      Link encap:Ethernet  HWaddr 80:56:f2:fa:08:c9  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::8256:f2ff:fefa:8c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12832 errors:7 dropped:0 overruns:0 frame:21575
          TX packets:15900 errors:101 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6436256 (6.4 MB)  TX bytes:6288493 (6.2 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5344 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:528302 (528.3 KB)  TX bytes:528302 (528.3 KB)


```


where did 192.168.2.4 came from???
can i get rid of it and keep 192.168.88.235 only??

---

### Post by JKyleOKC on 2014-08-27
Well, you definitely have a network problem here. Most systems have only one network adapter but you have two. My own has four, although two are unused -- one of the two active ones is connected to the router furnished by my ISP, while the other connects to the switch for my little LAN. I suspect from your report that your setup might be somewhat similar, but we can't give much help until you tell us a bit more about the setup.

The 192.168.2.4 address may have been assigned automatically by some program at the other end of the cable plugged into the RJ-45 jack of eth1, if you did not assign it manually. That's a different subnet from the one that includes 192.168.88.235; the first two numbers in these addresses indicate a local network (including all addresses from 192.168.0.0 to 192.168.255.255) and the third number (2 or 88) indicates a subnet of that network. The network software normally prevents subnets from communicating with each other, so it's necessary to know what's at the other end of the wire when trying to troubleshoot the situation.

My best guess at this point is that your 88.235 address is connected to a router or modem and is getting that address from your ISP, while the 2.4 address is the address of your specific machine on the LAN. However that's only a guess in the absence of more detailed information...

I'm not familiar with the term "grid engine" but it could be something like my setup, which I call a "software router" in which all traffic from the WAN comes into this machine, and software in this one then forwards it through the other adapter to the rest of my LAN. This lets me implement all security needs in just one machine, where things connect to the outside world, and keeps it all under my control rather than being handled by somebody else's design and rules in a hardware router...

---

### Post by nerdtron on 2014-08-27
> where did 192.168.2.4 came from???
can i get rid of it and keep 192.168.88.235 only??

Let's see your network config file to determine where did you get the address. Or you can ask your network administrator about it.
```
cat /etc/network/interfaces
```

Also post your current routing table to determine how ping/connection requests are done.
```
route -n
```

Might as well post the current DNS setting just to be sure.
```
cat /etc/resolv.conf
```

---

### Post by engineer2 on 2014-08-28
the 192.168.88.235 is the one that i manually set ... the other end is other pc i connect them directly through a lan cable and set the ip to 192.168.88.236
although .2.4 i have no idea about and i didn't set that ..

this is the output of 
cat /etc/network/interfaces
```
root@mastergrid:~# cat /etc/network/interfaces
auto lo
iface lo inet loopback


```

this is the routing table:
```
root@mastergrid:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
192.168.2.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1

```

and this is the DNS part :
```
root@mastergrid:~# cat /etc/resolv.conf
cat: /etc/resolv.conf: No such file or directory


```

and i go to /etc but i didn'nt find some file called resolf.conf   but i found a ditrctory calld resolvconf  as shown in bold:
```
root@mastergrid:/home/gmaster# cd /etc
root@mastergrid:/etc# ls
acpi                           gshadow-             pkcs11
adduser.conf                   gssapi_mech.conf     pm
adjtime                        gtk-2.0              pnm2ppa.conf
alternatives                   gtk-3.0              polkit-1
anacrontab                     hdparm.conf          popularity-contest.conf
apg.conf                       host.conf            ppp
apm                            hostname             prime-discrete
apparmor                       hosts                profile
apparmor.d                     hosts.allow          profile.d
apport                         hosts.deny           protocols
apt                            hp                   pulse
at.deny                        idmapd.conf          python
at-spi2                        ifplugd              python2.7
avahi                          init                 rc0.d
bash.bashrc                    init.d               rc1.d
bash_completion                initramfs-tools      rc2.d
bash_completion.d              inputrc              rc3.d
bindresvport.blacklist         insserv              rc4.d
blkid.conf                     insserv.conf         rc5.d
blkid.tab                      insserv.conf.d       rc6.d
bluetooth                      iproute2             rc.local
bonobo-activation              issue                rcS.d
brlapi.key                     issue.net            **resolvconf**
brltty                         java-7-openjdk       rmt
brltty.conf                    kbd                  rpc
ca-certificates                kernel               rsyslog.conf
ca-certificates.conf           kernel-img.conf      rsyslog.d
ca-certificates.conf.dpkg-old  kerneloops.conf      samba
calendar                       ldap                 sane.d
chatscripts                    ld.so.cache          securetty
checkbox.d                     ld.so.conf           security
colord.conf                    ld.so.conf.d         sensors3.conf
compizconfig                   legal                sensors.d
ConsoleKit                     libnl-3              services
console-setup                  libpaper.d           sgml
cron.d                         libreoffice          shadow
cron.daily                     lightdm              shadow-
cron.hourly                    locale.alias         shells
cron.monthly                   localtime            skel
crontab                        logcheck             snmp
cron.weekly                    login.defs           sound
cups                           logrotate.conf       speech-dispatcher
cupshelpers                    logrotate.d          ssh
dbus-1                         lsb-base             ssl
debconf.conf                   lsb-base-logging.sh  sudoers
debian_version                 lsb-release          sudoers.d
default                        ltrace.conf          sysctl.conf
defaultdomain                  magic                sysctl.d
deluser.conf                   magic.mime           systemd
depmod.d                       mailcap              terminfo
dhcp                           mailcap.order        thunderbird
dhcp3                          manpath.config       timezone
dictionaries-common            mime.types           timidity
dkms                           mke2fs.conf          ts.conf
doc-base                       modprobe.d           ucf.conf
dpkg                           modules              udev
drirc                          motd                 ufw
emacs                          mtab                 updatedb.conf
environment                    mtab.fuselock        update-manager
exports                        mtools.conf          update-motd.d
firefox                        nanorc               update-notifier
fonts                          netconfig            UPower
foomatic                       netgroup             usb_modeswitch.conf
fstab                          netscsid.conf        usb_modeswitch.d
fstab.d                        network              vim
fuse.conf                      NetworkManager       vtrgb
gai.conf                       networks             wgetrc
gconf                          newt                 wildmidi
gdb                            nsswitch.conf        wodim.conf
ghostscript                    obex-data-server     wpa_supplicant
ginn                           openal               X11
gnome                          opt                  xdg
gnome-app-install              os-release           xml
gnome-settings-daemon          pam.conf             xul-ext
gnome-vfs-2.0                  pam.d                yp.conf
groff                          papersize            ypserv.conf
group                          passwd               ypserv.securenets
group-                         passwd-              zsh_command_not_found
grub.d                         pcmcia
gshadow                        perl

```

and finally i cd to the directory and this is its content:

```
root@mastergrid:/etc# cd resolvconf
root@mastergrid:/etc/resolvconf# ls
interface-order  resolv.conf.d  update.d  update-libc.d

```


if you want i can post the output of  the both pc's  that i have.

---

### Post by JKyleOKC on 2014-08-28
What version of Ubuntu are you using? And what other software have you installed?

The prompts shown in your replies indicate that you are logged in as the super-user "root" and this user ID is normally disabled in all current flavors of *buntu, because it's extremely dangerous to use.

Your routing table shows that only the eth1 interface has any (software-enabled) connection to the outside world, and the content of /etc/network/interfaces indicates that your network adapters are being controlled by the Network Manager service.

It's possible that your machine has a built-in network adapter on the motherboard and you have added a separate network adapter card. That's the most likely reason for you to have two "eth*" network interfaces showing in the "ifconfig" output. If this is the case, either disable the built-in one via BIOS settings, or remove the separate card. That should eliminate this source of confusion. It may, however, make it impossible to get on-line, if the RJ-45 jack **NOT** connected to the other computer **IS** connected to your router or modem -- the route table indicates that the 2.4 address is the only interface connecting to the outside world.

---

### Post by engineer2 on 2014-08-28
this one has ubuntu 12.04LTS  and the orther has ubuntu 14.04 LTS 
i don't know what do you mean by other software i don't have any software (except the usual i mean) 
and about the built in adapter they are both laptops not desktops so i'm not using an external adapter and i never had .

---

### Post by nerdtron on 2014-08-28
```
root@mastergrid:~# cat /etc/network/interfaces
auto lo
iface lo inet loopback
```
Since this file is empty, clearly this is a desktop and you used the network manager GUI to set the Static IP address. Post the screenshot of your network settings in the GUI.

```
root@mastergrid:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
[COLOR=#ff0000]**192.168.2.0 **[/COLOR]    0.0.0.0         255.255.255.0   U     2      0        0 eth1
```
You are saying that you have the IP address 192.168.88.235 as static IP address but the server don't have any routing tables for this specific IP block.
**Does your computer have 2 network cards? Maybe you have plugged the cable into the wrong port.**
```
root@mastergrid:~# cat /etc/resolv.conf
cat: /etc/resolv.conf: No such file or directory
```
This is really odd. But I think the problem lies on the "route -n". So you need to solve that first.

---

### Post by engineer2 on 2014-08-29
these are both laptops there is no desktop and i don't have two network  cards or two ports it's only one port in the laptop that i'm connecting  to besides when first set up the wired connection i mean giving the ip  address i used (Edit connection) and add the ip 
this is the snapshot  for the wired network settings :

[IMG]http://i62.tinypic.com/2vv6qyw.png[/IMG]



and this one for wireless ... the ip adress 192.168.2.4 that apreard earlier!! but it's for the wireless connection what this has to do with wired ?? 
this ip is from the DHCP range of my router 

[IMG]http://s2.postimg.org/ocfvxle55/Screenshot_from_2014_08_29_11_53_14.png[/IMG]
and this one for proxy as you see i don't have one 

[IMG]http://s29.postimg.org/q9z6kwjmv/Screenshot_from_2014_08_29_11_53_45.png[/IMG]

---

### Post by JKyleOKC on 2014-08-29
It's beginning to make sense to me now (although I'm still puzzled by you being logged in as "root"). Your wired connection on 88.235 is the only one using your network adapter, while the 2.4 address is coming through the wireless feature of the notebook -- note the totally different hardware address in the two captures.

I think the root of your original problem is simply that you are trying to mix two incompatible methods for connecting multiple computers together, and the two methods are tripping over each other. You need the entry in /etc/hosts on both machines in order to address your machine by name, and you need the wireless capability set up to contact the outside world. However, the routing table looks as if it's being set up for the exclusive benefit of the wireless interface and that's making your wired interface effectively unusable.

I've had problems setting up the routing table in the past so I'm probably not the right person to try to tell you how to fix it. However you definitely need a line in that table (on both machines, not just the one) that tells your system how to handle packets addressed to 192.168.88.* destinations, and that the line applies only to the eth0 interface. Hopefully someone more knowledgable than myself will jump in here with details of how to achieve this!

---

### Post by nerdtron on 2014-08-31
Disable your wireless first before using wired connection. Your default gateway's are messing with the routes.

---

