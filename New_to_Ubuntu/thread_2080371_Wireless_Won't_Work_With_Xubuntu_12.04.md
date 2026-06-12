---
title: "Wireless Won't Work With Xubuntu 12.04"
date: 2012-11-03
forum: New to Ubuntu
---

### Post by kenizl86 on 2012-11-03
Hey,

   I have a Dell Latitude D600 laptop that I just installed Xubuntu 12.04 on. For some reason, Xubuntu won't recognize my built-in wireless. It connects just fine to Ethernet, but other than that, it doesn't. I tried some of the other stuff suggested on likewise forums, but to no avail (things like installing the b43 thing).

Any help would be appreciated! Thanks!

---

### Post by Hadaka on 2012-11-03
Hi, please post the output of..

```
rfkill list all 
```

```
lspci -nn | grep 0280 
```

thanks

---

### Post by crispy_420 on 2012-11-03
Based on Dell's support and drivers downloads there are several options for the wireless card. Any clue which you have?

---

### Post by newb85 on 2012-11-03
A good way to determine the details of your wireless card is to run
```
sudo lshw -C network
```

However, there's a script created by Wildman (one of the most experienced network troubleshooters on the forums) that pulls a lot of useful information.  Rather than attaching the file and rewording his directions, I'll do this:
[http://ubuntuforums.org/showpost.php?p=12177285&postcount=12](http://ubuntuforums.org/showpost.php?p=12177285&postcount=12)
Follow his directions, but reply back to this thread.

---

### Post by kenizl86 on 2012-11-04
> **Hadaka said:**
> Hi, please post the output of..

```
rfkill list all 
```

```
lspci -nn | grep 0280 
```

thanks


"rfkill" didn't bring up anything, but "lspci" brought up:

```
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11a/b/g [14e4:4324] (rev 03)
```

And, to you, newb85, the output was:

```
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:b5:ef:15
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 firmware=5705-v3.16 latency=32 link=no mingnt=64 multicast=yes port=twisted pair
       resources: irq:11 memory:faff0000-faffffff
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=32
       resources: memory:fafee000-fafeffff
```

Thanks for the replies!

---

### Post by westie457 on 2012-11-04
```
sudo apt-get install firmware-b43-installer
```

The above command should get your wireless up and running without needing to reboot. If it does not start within about 2 minutes then run ```
sudo modprobe b43
``` again wait to see if it comes up. Still no luck then reboot.

If after the reboot it is still not working we will try something else.

Thank you

---

### Post by newb85 on 2012-11-04
Your Broadcom 4306 has no functioning drivers installed.

Try this:
Download and extract the attached file to your Desktop.
Then run the following commands:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo apt-get update
sudo apt-get install firmware-b43-installer
sudo apt-get remove bcmwl-kernel-source
sudo modprobe -r b43
sudo modprobe b43
```

Edit: follow Westie's advice first.

---

### Post by kenizl86 on 2012-11-04
Hey,

  I tried what you suggested, westie457, and ran the two commands. After the second one, it connected to the internet. But then I rebooted, and now it won't connect again. Do I just need to run that command every time I turn the computer on? If so, is there a way to get Xubuntu to run commands automatically on startup (like AUTOEXEC.bat on windows)?

Thanks for the help, by the way.

---

### Post by westie457 on 2012-11-04
Now hopefully for the final step ```
sudo su 
 echo b43 >> /etc/modules 
 exit
```
The above is three separate commands. These will make the changes permanent.

---

### Post by kenizl86 on 2012-11-04
Thanks westie457! That solved my problem! I rebboted it twice (just to be sure) and both times it connected to wireless. Thanks!

---

### Post by westie457 on 2012-11-04
You're welcome, glad its working.

Now could you mark this as 'Solved' please, using 'Thread Tools' near the top right of the page.

Thank you

---

### Post by Ben Swell on 2013-02-14
```
sudo su 
 echo b43 >> /etc/modules 
 exit
```

I'm sorry but what do you mean three separate commands?

---

