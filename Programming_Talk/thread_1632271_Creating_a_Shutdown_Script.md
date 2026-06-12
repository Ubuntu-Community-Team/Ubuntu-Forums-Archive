---
title: "Creating a Shutdown Script"
date: 2010-11-27
forum: Programming Talk
---

### Post by jamessimo on 2010-11-27
I want to create a script that will disconnect my "Eth1" from the internet every time I shutdown.

I did post in Networking here: [http://ubuntuforums.org/showthread.php?t=1628456](http://ubuntuforums.org/showthread.php?t=1628456)

But no ones talking.

I know how to program but I have never scripted for Ubuntu so I was wondering if anyone knew what commands I can use? 

Like:

Grep eth1 

eth1connected = false

or something along those lines. Also can I make a shutdown script file or can I lug it in with a pre-existing script?



Thanks!

---

### Post by Jlayman on 2010-11-27
why is it you want to write a script to disconnect when your computer shuts down.  wouldnt id disconnect anyway

---

### Post by jamessimo on 2010-11-27
> **Jlayman said:**
> why is it you want to write a script to disconnect when your computer shuts down.  wouldnt id disconnect anyway

Read the link in the thread I linked, My computer takes the whole network with it if it shuts down. I have spent many a month trying to fix it to no avail.

---

### Post by Jlayman on 2010-11-27
try using ```
$sudo ifdown eth1 
``` in your script and dont forget to make it executable with chmod example is ```
 % chmod +x myscript

```

also you have to put ```
#!/bin/bash
``` 
 at the begining of your script.  


i'm no expert but i will try and figure it out as well.

---

### Post by jamessimo on 2010-11-27
> **Jlayman said:**
> try using ```
$sudo ifdown eth1 
``` in your script and dont forget to make it executable with chmod example is ```
 % chmod +x myscript

```

also you have to put ```
#!/bin/bash
``` 
 at the begining of your script.  


i'm no expert but i will try and figure it out as well.


Thanks dude! ill try it now.

---

### Post by Jlayman on 2010-11-27
your welcome.  i hope it helps.  After you try please post your results.  As i am very intrested in writing scripts myself.

---

### Post by Jlayman on 2010-11-27
also you might have to replace eth1 with the name of your network.

 to find this type ```
ifconfig 
```   in the terminal    my results are 
\ ```
jason@jason-desktop:~$
eth0      Link encap:Ethernet  HWaddr 00:1d:09:3e:08:8e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:60:2e:43  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:e0ff:fe60:2e43/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:699755 errors:0 dropped:0 overruns:0 frame:0
          TX packets:369303 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1004116850 (1.0 GB)  TX bytes:33428437 (33.4 MB)

```


wlan0 being my wireless network and eth0 being a wired connection

---

### Post by jamessimo on 2010-11-28
Its not working, do I have to call the script some ware? right now its KShutDown in rc0

---

### Post by conradin on 2010-11-28
Ok, I wrote a script which does this task for me.
I used the scripting language "Expect" on the Tool Command Language "Tcl"

```

#!/usr/bin/expect
spawn sudo -i
expect ":"
send "My_Password\r"
expect "#"
puts "Shutting Down Ethernet connection 0 "
send "\r"
send "ifdown eth1\r"
expect "configured"
puts "Shutting down computer "
send "\r"
send "shutdown -h now\r"
interact

```

I used the word "configured" because of the result I get at the end of the command ifdown eth0
```

$ sudo ifdown eth0
ifdown: interface eth0 not configured

```

If you want a wait period, you can enter that into the shutdown line.

---

### Post by jamessimo on 2010-12-13
> **conradin said:**
> Ok, I wrote a script which does this task for me.
I used the scripting language "Expect" on the Tool Command Language "Tcl"

```

#!/usr/bin/expect
spawn sudo -i
expect ":"
send "My_Password\r"
expect "#"
puts "Shutting Down Ethernet connection 0 "
send "\r"
send "ifdown eth1\r"
expect "configured"
puts "Shutting down computer "
send "\r"
send "shutdown -h now\r"
interact

```

I used the word "configured" because of the result I get at the end of the command ifdown eth0
```

$ sudo ifdown eth0
ifdown: interface eth0 not configured

```

If you want a wait period, you can enter that into the shutdown line.


I have made this script but I simply cant get it to run, it keeps treating it like a text file. How do I get it to treat it like a script?

---

### Post by dwhitney67 on 2010-12-13
> **jamessimo said:**
> Read the link in the thread I linked, My computer takes the whole network with it if it shuts down. I have spent many a month trying to fix it to no avail.

> 
I am on an Ubuntu 10.04 computer, I dont have any problems with internet access or anything. However when this computer is left plugged into the network hub (WIFI ROUTER) all the computers on the network (Wired and Wireless) loses connection to the internet.

For now I simply leave my PC un-plugged from the network when I turn it off but I want it so It can be left in. I know Ubuntu is the problem because I duel boot a win7 system and when I power down in that the network is fine. 


It is definitely not Ubuntu that is causing the problem; it is perhaps how you have configured your system, which at this point, I have not a clue what you could have done to bring the entire network down (seems very odd).

I use Ubuntu at home with a similar setup to yours, and I do not have the problem you describe.  In fact, I would bet that 99.9% of Ubuntu users don't have this problem.

I would suggest that you refrain from seeking a workaround to the problem, and actually address the real problem head-on.  The first step would probably be to to determine if your other computers are using your Ubuntu system as a gateway to the internet (normally they shouldn't).

P.S.  Once any computer is shutdown, regardless of the OS it uses, it is not going to affect any other computer, unless these other computers depend on the computer that has been shutdown.

---

### Post by jamessimo on 2010-12-13
> **dwhitney67 said:**
> It is definitely not Ubuntu that is causing the problem; it is perhaps how you have configured your system, which at this point, I have not a clue what you could have done to bring the entire network down (seems very odd).

I use Ubuntu at home with a similar setup to yours, and I do not have the problem you describe.  In fact, I would bet that 99.9% of Ubuntu users don't have this problem.

I would suggest that you refrain from seeking a workaround to the problem, and actually address the real problem head-on.  The first step would probably be to to determine if your other computers are using your Ubuntu system as a gateway to the internet (normally they shouldn't).

P.S.  Once any computer is shutdown, regardless of the OS it uses, it is not going to affect any other computer, unless these other computers depend on the computer that has been shutdown.


I have investigated this problem to the bone, I have had 2 colleges (one a networking lecturer). I have determined that its not my computer issuing IP's, My computer is not a server. My guess is that the built in network card is remaining packet hungry on shut down due to the vernal not addressing it properly.

I am at my witts end with it and disconnecting at shutdown is the only way.

---

### Post by dwhitney67 on 2010-12-13
> **jamessimo said:**
> I have investigated this problem to the bone, I have had 2 colleges (one a networking lecturer). I have determined that its not my computer issuing IP's, My computer is not a server. My guess is that the built in network card is remaining packet hungry on shut down due to the vernal not addressing it properly.

I am at my witts end with it and disconnecting at shutdown is the only way.
A cow eats a lot of grass, but if I put a bullet in its head, then believe me when I tell you this, the cow will be dead and it will cease to eat anymore.

When you shut off your computer, your network card will be deprived of power, and it will no longer send or receive packets.  Do you agree?

Now, based on this information, can you please explain your theory that your computer, which has been shutdown, can possibly affect the network router?

Perhaps you have setup your network router incorrectly?  Btw, what kind do you have?

---

### Post by efflandt on 2010-12-14
In CMOS setup (BIOS splash screen before grub) try disabling "Wake on LAN".  Not sure if that is what is causing your issue, but it may have something to do with the card still being active when the computer is shut down.

Note that if you do **ls -l /etc/rc0.d**, what appear to be files are actually symlinks to scripts in /etc/init.d.  S35networking should automatically disable network devices when entering runlevel 0 (halt) or 6 (reboot), unless a network file system is still mounted on that interface. Are you doing anything with Windows like file and printer sharing (samba)?

Note that shutdown scripts run as root, so there is no need to use sudo in them.  Also note that the symlinks have numbers for the sequence they they are executed.  So if you wanted to make sure that eth1 was down after S35networking, you could call it K36killeth containing:

```
#!/bin/sh
/sbin/ifdown eth1
```

---

### Post by jamessimo on 2010-12-16
> **dwhitney67 said:**
> A cow eats a lot of grass, but if I put a bullet in its head, then believe me when I tell you this, the cow will be dead and it will cease to eat anymore.

When you shut off your computer, your network card will be deprived of power, and it will no longer send or receive packets.  Do you agree?

Now, based on this information, can you please explain your theory that your computer, which has been shutdown, can possibly affect the network router?

Perhaps you have setup your network router incorrectly?  Btw, what kind do you have?
The card is still lit up when the computer is off, also when I leave my etho cable pugged i on shut down the router light for my computer is flashing like its downloading something. 
> **efflandt said:**
> In CMOS setup (BIOS splash screen before grub) try disabling "Wake on LAN".  Not sure if that is what is causing your issue, but it may have something to do with the card still being active when the computer is shut down.

Note that if you do **ls -l /etc/rc0.d**, what appear to be files are actually symlinks to scripts in /etc/init.d.  S35networking should automatically disable network devices when entering runlevel 0 (halt) or 6 (reboot), unless a network file system is still mounted on that interface. Are you doing anything with Windows like file and printer sharing (samba)?

Note that shutdown scripts run as root, so there is no need to use sudo in them.  Also note that the symlinks have numbers for the sequence they they are executed.  So if you wanted to make sure that eth1 was down after S35networking, you could call it K36killeth containing:

```
#!/bin/sh
/sbin/ifdown eth1
```

This looks like the ticket! Ill try it when I back at home! (away on business)

---

### Post by jamessimo on 2010-12-18
I have made the script, it is exacutible and in the correct rc0 folder, I run it but it doesn't seem to shut down the connection..

---

### Post by jamessimo on 2010-12-20
Bump

---

### Post by pt123 on 2010-12-25
Ubuntu moved to using Upstart than init.d in Lucid, so this might afftect how scripts are run on boot and shutdown.

---

