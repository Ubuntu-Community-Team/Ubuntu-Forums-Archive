---
title: "Command explanation"
date: 2018-06-19
forum: New to Ubuntu
---

### Post by flogad0b on 2018-06-19
Hi guys!

As you have probably guessed I'm new to Ubuntu, I'm currently getting used to using Linux by setting up a web server (Nginx) for a web based asset management system. So far the project is going great and I'm learning loads! 

Basically i have just typed the following command to find the IP address of my server to test that the web server has installed correctly (I'm following a guide) which worked, but i don't understand what each part of the command does in order to produce the result, so was wondering if someone could just explain it to me.  I get the first part of the command, however everything after grep, im not sure about, id like to understand exactly what this command is doing

ip addr show eth0 | grep inet | awk '{ print $2; }' | sed 's/\/.*$//'

thanks guys!

---

### Post by Doug S on 2018-06-19
Hi, and welcome to Ubuntu forums.
I am not an "awk" and "sed" expert, but I'll try to answer. First, the first command only (modified for the computer I am using):
```
$ ip addr show ens5
2: ens5: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:23:32:9f:a3:cb brd ff:ff:ff:ff:ff:ff
    inet 192.168.111.31/24 brd 192.168.111.255 scope global dynamic noprefixroute ens5
       valid_lft 74762sec preferred_lft 74762sec
```O.K. seems simple enough, information about the interface of interest. Now add the next command:
```
$ ip addr show ens5 | grep inet
    inet 192.168.111.31/24 brd 192.168.111.255 scope global dynamic noprefixroute ens5
```Extract the network information line. Now add the third command:
```
$ ip addr show ens5 | grep inet | awk '{ print $2; }'
192.168.111.31/24
```Extract the IP address (field 2), however includes netmask. Now add the fourth command:
```
$ ip addr show ens5 | grep inet | awk '{ print $2; }' | sed 's/\/.*$//'
192.168.111.31
```Chop off the netmask, and only the actual ip address is left.

Hope this helps

How did I know that my interface name was "ens5"? I did this (which is all I would have in the first place, because the IP address is there):
```
~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: [COLOR="#FF0000"]ens5[/COLOR]: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:23:32:9f:a3:cb brd ff:ff:ff:ff:ff:ff
    inet 192.168.111.31/24 brd 192.168.111.255 scope global dynamic noprefixroute ens5
       valid_lft 74309sec preferred_lft 74309sec

```

EDIT: My answer differs from Rocket2DMn's because I always run with ipv6 disabled. i.e. in /etc/default/grub:
```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1"
```

---

### Post by Rocket2DMn on 2018-06-19
You can always try building up the command yourself by dropping off the latter parts that you don't understand to see what the original output looks like before it is filtered further.
So you understand that 
```

ip addr show eth0 | grep inet

```
is filtering the output of the first part by lines that contain the the text "inet".  You can run just that part to see the whole line.
The next part,
```

 | awk '{ print $2; }'

```
filters the output further by only printing the second column of text, which for the "inet" line is the IP address information.  Awk is a scripting language that is commonly used in shell commands.  However, there is additional information attached to the bit of text produced here that you don't want.  For example, my current wifi connection looks like:
```

$ ip addr show wlan0 | grep inet | awk '{ print $2; }'
192.168.1.106/24
fe80::3602:86ff:fe08:797e/64

```
So the last part,
```

 | sed 's/\/.*$//'

```
will drop off everything after the '/' character.  Sed is a stream editor for modifying text, often using regular expressions like you see in this example (you'd need to learn regex to understand the structure of this command snipped).
So finally, you get a result like
```

192.168.1.106
fe80::3602:86ff:fe08:797e

```
which is the IPv4 and IPv6 addresses for my network card.

---

### Post by steeldriver on 2018-06-19
FYI you could skip the grep and sed - just do everything in awk

```

ip addr show enp0s3 | awk '/inet/ {sub("/.*$","",$2); print $2}'

```

---

