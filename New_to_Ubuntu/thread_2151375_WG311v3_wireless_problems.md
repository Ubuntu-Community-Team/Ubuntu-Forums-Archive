---
title: "WG311v3 wireless problems"
date: 2013-06-04
forum: New to Ubuntu
---

### Post by Jason Bourne 2 on 2013-06-04
Hello,

I just installed Ubuntu 13.04 x64 today.

I am having a painfull experience getting wireless internet connectivity to work.

I have followed the ubuntu guide with no errors:
[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

However I still cant connect to wireless networks

Here is some output that might be helpful in diagnosing the problem.
[PHP]
root@cc-Desktop:/home/cc# 
ndiswrapper -lwg311v3 : driver installed    
device (11AB:1FAA) present

root@cc-Desktop:/home/cc#
 iwconfigeth0      no wireless extensions.
eth1      no wireless extensions.
lo        no wireless extensions.

root@cc-Desktop:/home/cc#
 ifconfigeth0      Link encap:Ethernet  HWaddr 00:1d:7d:0b:3c:bb            UP BROADCAST MULTICAST  MTU:1500  Metric:1          RX packets:0 errors:0 dropped:0 overruns:0 frame:0          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0          collisions:0 txqueuelen:1000           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
eth1      Link encap:Ethernet  HWaddr 00:1d:7d:0b:3c:b9            UP BROADCAST MULTICAST  MTU:1500  Metric:1          RX packets:0 errors:0 dropped:0 overruns:0 frame:0          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0          collisions:0 txqueuelen:1000           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
lo        Link encap:Local Loopback            inet addr:127.0.0.1  Mask:255.0.0.0          inet6 addr: ::1/128 Scope:Host          UP LOOPBACK RUNNING  MTU:65536  Metric:1          RX packets:744 errors:0 dropped:0 overruns:0 frame:0          TX packets:744 errors:0 dropped:0 overruns:0 carrier:0          collisions:0 txqueuelen:0           RX bytes:60912 (60.9 KB)  TX bytes:60912 (60.9 KB)[/PHP]

---

### Post by gordintoronto on 2013-06-04
Unfortunately, the community documentation includes many very old documents which are no longer relevant. I don't know if that is true for the one you were looking at, but it is five years old. This one is much more recent: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Have you rebooted since setting it up?

Have you ever set up a wireless connection in Ubuntu?

It looks as if a step was missed somewhere.

---

### Post by Jason Bourne 2 on 2013-06-04
I've tried that method as well to no avail.

I have rebooted as well.

I'm new to Ubuntu basically I want to try it out and im having a nightmare experience. 

My mouse didn't work until i remapped all the buttons.

And since this is a network related problem it really hits hard. If it was any other issue I could still use my computer to research.

There are no error messages when I type in any of the commands,

This is a big jump from Windows for me where it just works out of the box :(

---

### Post by gordintoronto on 2013-06-04
I'm sorry to hear you are having such a hard time. Is there a network icon near the top-right of your screen, probably next to the speaker icon?

Most computer configurations "just work" in Ubuntu. I have never needed to even install a driver for my entire system, including video card, wireless, webcam, printer, scanner.

Could you post the output from lspci, please?

---

### Post by squakie on 2013-06-04
I see ndiswrapper mentioned here - not my first choice but it could work.  Here is what I would do:

If you are able to temporarily hard wire your pc to the router, then you could check additional drivers and see if there is one to install - this would avoid ndiswrapper.

If not, and you must use ndiswrapper, then do the following:

(1) completely back out anything you have installed to date for ndiswrapper
(2) via the installation media - use file explorer:
- navigate to /pool/main/n
- you should see a folder for ndiswrapper and a folder for ndisgtk
- navigate to the ndiswrapper folder
- double-click on the ndiswrapper common to begin it's installation, and wait for finish
- double-click on the ndiswrapper utils to begin it's installation, and wait for finish
- navigate back to the /pool/main/n folder
- navigate to the ndisgtk folder
- double click on the ndisgtk file to begin its' installation and wait for finish

- now you need the appropriate Windows XP driver files - the .inf and .sys files.  These files must come from a driver that matches your operating system architecture - 64 bit for 64 bit ubuntu, 32 bit for 32 bit ubuntu.  Place those files in a new folder in your home folder - something like mynetdrivers

- start ndisgtk - you can do this from the command line or look for windows drivers in the menus
- select new 
- point it to the .inf file in the ~/mynetdrivers folder
- add

This *should* do everything needed.  If it fails to restart ndiswrapper on a reboot, we'll need to add that to the modules file.

---

