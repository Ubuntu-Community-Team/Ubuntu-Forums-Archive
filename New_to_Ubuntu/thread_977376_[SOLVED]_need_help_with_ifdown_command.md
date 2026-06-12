---
title: "[SOLVED] need help with ifdown command"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by newbee70 on 2008-11-10
I tried to use ifdown to close my internet interface with no luck. Can anyone tell me what I am doing wrong.

What is it telling me about eth1 not being configured?

waylon@desktop:~$ ifdown eth1
ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
waylon@desktop:~$ sudo ifdown eth1
[sudo] password for waylon: 
ifdown: interface eth1 not configured
waylon@desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0e:a6:72:b9:c8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:0e:a6:72:cb:2a  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fe72:cb2a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1699 (1.6 KB)  TX bytes:5266 (5.1 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:768 errors:0 dropped:0 overruns:0 frame:0
          TX packets:768 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:32256 (31.5 KB)  TX bytes:32256 (31.5 KB)

waylon@desktop:~$

---

### Post by The Cog on 2008-11-10
I wonder if your eht1 is under control of the network manager rather than the normal Ubuntu interface configuration file /etc/network/interfaces. This command should work though - it's at a lower level than the ifup/ifdown scripts:
> sudo ifconfig eth1 down

---

### Post by eder.apt-get on 2008-11-10
Which driver is yours? Maybe it´s not supported out of the box. Also, would you post the result of cat /etc/network/interfaces ?

---

### Post by newbee70 on 2008-11-10
waylon@desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

waylon@desktop:~$

---

### Post by newbee70 on 2008-11-10
> **The Cog said:**
> I wonder if your eht1 is under control of the network manager rather than the normal Ubuntu interface configuration file /etc/network/interfaces. This command should work though - it's at a lower level than the ifup/ifdown scripts:

You may be right, this is an full install from cd so the installer did set up my interfaces. I tried the sudo ifconfig eth1 down and my system seemed to freeze for a few moments

---

### Post by jpoRS on 2008-11-10
Have you tried ```
sudo ifdown -a
```

That will shut down all of your networking, but depending on what you are trying to do, it may do what you need.

Good luck.
jim

---

### Post by newbee70 on 2008-11-10
> **jpoRS said:**
> Have you tried ```
sudo ifdown -a
```

That will shut down all of your networking, but depending on what you are trying to do, it may do what you need.

Good luck.
jim

waylon@desktop:~$ sudo ifdown -a
[sudo] password for waylon: 
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...

I shut down firestarter and no luck

waylon@desktop:~$ sudo ifdown -a
waylon@desktop:~$ sudo ifdown -a
waylon@desktop:~$ 


   ...done.
waylon@desktop:~$

---

### Post by jpoRS on 2008-11-10
How about

```
sudo firestarter -p && sudo ifdown -a
```

?
jim

---

### Post by newbee70 on 2008-11-10
> **jpoRS said:**
> How about

```
sudo firestarter -p && sudo ifdown -a
```

?
jim

waylon@desktop:~$ sudo firestarter -p && sudo ifdown -a
[sudo] password for waylon: 
Firewall stopped
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
waylon@desktop:~$ 

this time the system did not even freeze for a moment.

thanks for trying to help me figure this out .

---

### Post by jpoRS on 2008-11-10
Hrmmm. . . 

How about we remove firestarter and see what happens?

```
sudo apt-get remove firestarter
```

and then

```
sudo ifdown eth1
```

?
jim

---

### Post by newbee70 on 2008-11-11
> **jpoRS said:**
> Hrmmm. . . 

How about we remove firestarter and see what happens?

```
sudo apt-get remove firestarter
```

and then

```
sudo ifdown eth1
```

?
jim

*Jim,  I think I am going to do a fresh install of heron "after the critical error".*

waylon@desktop:~/Desktop/recipes$ sudo apt-get remove firestarter
[sudo] password for waylon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libmono-cairo2.0-cil linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  firestarter
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1999kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 126393 files and directories currently installed.)
Removing firestarter ...

[B](gconftool-2:7843): GConf-CRITICAL **: Failed to load file "/var/lib/gconf/defaults/%gconf-tree-bs.xml": Error on line 2308 char 13: Invalid UTF-8 encoded text - not valid '
                                        </entry>
                                        <entry name="move_to_workspace_8">
                                                <local_schema short_desc="Premjesti prozor na radnu povr?inu 8">
                                                </local_schema>
            '[/B]
waylon@desktop:~/Desktop/recipes$ 
waylon@desktop:~/Desktop/recipes$ sudo ifdown eth1
ifdown: interface eth1 not configured
waylon@desktop:~/Desktop/recipes$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0e:a6:72:b9:c8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:0e:a6:72:cb:2a  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fe72:cb2a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:250501 errors:0 dropped:0 overruns:0 frame:0
          TX packets:176270 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:344172930 (328.2 MB)  TX bytes:11737188 (11.1 MB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1058 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1058 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:44436 (43.3 KB)  TX bytes:44436 (43.3 KB)

waylon@desktop:~/Desktop/recipes$

---

### Post by jpoRS on 2008-11-11
Hmm.  Well it is officially out of my league now.  Have you googled the error?

If doing a fresh install will be a great inconvenience to you, give people a little bit more time, maybe someone with more experience with this problem will be able to help.  But if it won't be an inconvenience, then go for it.  Fresh installs are like freshly laundered socks: clean, helpful, and good for your feet.

Ok, well I don't really see how a fresh install is good for your feet, but you get the point.

Good luck, and sorry I couldn't help you.
jim

---

### Post by pennacook on 2008-11-11
Have you tried just downing it with ifconfig?

```
sudo ifconfig eth1 down
```

---

### Post by newbee70 on 2008-11-11
> **jpoRS said:**
> Hmm.  Well it is officially out of my league now.  Have you googled the error?

If doing a fresh install will be a great inconvenience to you, give people a little bit more time, maybe someone with more experience with this problem will be able to help.  But if it won't be an inconvenience, then go for it.  Fresh installs are like freshly laundered socks: clean, helpful, and good for your feet.

Ok, well I don't really see how a fresh install is good for your feet, but you get the point.

Good luck, and sorry I couldn't help you.
jim

Thanks again Jim, I appreciate the time and thoughts. Linux is a great teacher of life, patience, persistence, and endurance. and then we will find it is operator error.::popcorn:

I think I will work on it for awhile longer though;

---

### Post by newbee70 on 2008-11-11
> **pennacook said:**
> Have you tried just downing it with ifconfig?

```
sudo ifconfig eth1 down
```



 Re: need help with ifdown command
Quote:
Originally Posted by jpoRS View Post
How about

Code:

sudo firestarter -p && sudo ifdown -a

?
jim
waylon@desktop:~$ sudo firestarter -p && sudo ifdown -a
[sudo] password for waylon:
Firewall stopped
* Stopping the Firestarter firewall...
...done.
* Starting the Firestarter firewall...
...done.
waylon@desktop:~$

this time the system did not even freeze for a moment.

thanks for trying to help me figure this out .


[B]waylon@desktop:~$ sudo ifconfig eth1 down
waylon@desktop:~$ 
[/B]

[I]Seemed to shut it down for a few moments, and then it came back up.
this may be a problem of my system auto connecting to stay online. I will have to look into this further.[/I]

thanks for the help.

---

### Post by newbee70 on 2008-11-11
> **The Cog said:**
> I wonder if your eht1 is under control of the network manager rather than the normal Ubuntu interface configuration file /etc/network/interfaces. This command should work though - it's at a lower level than the ifup/ifdown scripts:



Cog; thanks a mint friend. it does seem that network manager was auto reconnecting so fast that the ifdown command seemed not to work.

I finally figured out how to manually configure eth1 and everything seems to work ok now. 

Thanks for everyones help!!!!!:lolflag:

---

### Post by newbee70 on 2008-11-11
**[SIZE="4"]This problem seems to be solved now[/SIZE]**

Thanks to all that have added their thoughts in solving MY problem,

It was operator error,

---

