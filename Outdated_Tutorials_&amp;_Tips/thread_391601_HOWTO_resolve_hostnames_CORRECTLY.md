---
title: "HOWTO: resolve hostnames CORRECTLY"
date: 2007-03-23
forum: Outdated Tutorials &amp; Tips
---

### Post by dannyboy79 on 2007-03-23
This how-to is basically trying to correct the guide that is out there now with a similar name. [http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)
Well that guide isn't per say wrong, but it is misleading and does NOT have all the info needed to make a choice and I think it's paramount to explain something and give the user a choice before just saying "this is how to do it"

One must first understand how Windows does name resolution. Please see here: [http://www.microsoft.com/technet/network/evaluate/technol/tcpipfund/tcpipfund_ch07.mspx#E5C](http://www.microsoft.com/technet/network/evaluate/technol/tcpipfund/tcpipfund_ch07.mspx#E5C)
The "default" for Windows XP is for it to use the NETBIOS setting from the DHCP server, if you assign a static ip or the dhcp server doesn't handle NETBIOS, then you need to use NETBIOS over TCP/IP. By default, a Windows XP Professional&#8211;based computer that is not configured as a WINS client or WINS server is configured as a b-node computer. A b-node computer is one that uses IP broadcasts for NetBIOS name resolution.
[http://www.microsoft.com/technet/prodtechnol/winxppro/reskit/c24621675.mspx](http://www.microsoft.com/technet/prodtechnol/winxppro/reskit/c24621675.mspx)

The guide I am trying to clarify and make correct is true if you have a wins server defined and you don't have a dns and you have not added hostnames and ip addresses into your Linux /etc/hosts file. Unix and Linux have a similar default Domain Name Resolution order as Windows. The operating system will first check its /etc/hosts file and if it does not find an entry for the queried domain, it will then query its configured DNS servers. In the default /etc/host.conf file you'll find:
order hosts, bind
so this is FIRST using the /etc/hosts file.

I have my Ubuntu box (within the smb.conf) overrid Winbloz strong desire to become a Local Master Browser because I don't always have my winbloz box on. So I use my hosts file for internal name resolution (i think) I also have the nmbd daemon running, which I believe broadcasts my machines name to the other machines. Windows does this broadcasting thing thru Netbios over TCP/IP I think. (some1 please correct me if I am wrong) I don't have a wins server defined and I don't have an internal DNS server. Also, according to recent documentation, winbind is in the Samba package so if you installed samba, winbind should already installed. You can find out by doing sudo aptitude show winbind. Anyway, according to man winbindd:

The service provided by winbindd is called `winbind' and can be used to
resolve user and group information from a Windows NT server. The ser-
vice can also provide authentication services via an associated PAM
module.

The following simple configuration in the/etc/nsswitch.conf file can be
used to initially resolve hostnames from /etc/hosts and then from the
WINS server.

hosts: files wins


So what this is saying is that resolving hostnames is done first by the hosts file (files) and then a wins server (wins). The guide I am correcting, the config line was files dns wins so that merely means that it would use the hosts file, then a dns server, then a wins server. So if you have a wins server and want to use winbind than do so but if you don't have a wins server than there is no need for you to add wins to the nsswitch.conf file (unless some1 can explian to me otherwise). Just add your hostnames and their ip's to your /etc/hosts file. Much easier! This will only work of course if you have all static ips. You can setup static ip's 2 different ways if your router or dhcp server has this setting. (this is so easy, I don't know why people are so scared to set static ip's) I mean maybe if it's a laptop but if it's a desktop, you dont go around attaching it to different routers do you, so there is no reason for dhcp. Either set the ip static thru the actual OS and it's mask and gateway etc etc or you can config your router or dhcp server so it'll always "reserve" that ip based on the interfaces MAC address. I can do this also thru my netgear, I turn on all computers, then log into my router, then I go LAN IP Setup and tell the dhcp to always give that MAC address the same IP. Also, if you make all your machines static by using the OS (you don't need to disable the dhcp server or router) and still want the dhcp server set so that when you introduce a new computer it gets an ip automatically (say some1 with a laptop comes in to visit) make sure you change your dhcp server ip's so that the range no longer includes the ones that you have statically assigned at the machine's.

For example: 
My router's DHCP server hands out ip's from 192.168.5.20 thru 192.168.5.254
and then I can use 192.168.5.2 thru 192.168.5.19 for static ips and there will never be a same ip problem.

---

### Post by DC@DR on 2007-04-11
I just wonder how this wonderful HOWTO got lost and left behind? Thanks for sharing this great info :-)

---

### Post by dmizer on 2007-05-20
courtesy bump.

---

### Post by PingerS on 2007-07-22
Thanks for making that clear the order in which things appear in nsswitch.conf is important and when you want to make that change to nsswitch.conf ;)

---

