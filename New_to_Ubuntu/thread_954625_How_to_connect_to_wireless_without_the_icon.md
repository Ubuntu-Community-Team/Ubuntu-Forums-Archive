---
title: "How to connect to wireless without the icon?"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by Optimus_Jazz on 2008-10-21
I have my wireless set up so (i think) this is not the problem.
I deleted my top panel by mistake and the icons all went missing,but i never got the wireless one back.

Today i hooked the laptop up to a network cable in college and it was fine,but when i got home i cant connect to my wireless...because i cant find the icon.I know it sounds stupid but is there anyway of fixing this?

Thanks.

---

### Post by Titan8990 on 2008-10-21
Right click on the panel -> add to panel -> Network Monitor


That should be what you are looking for.

If you would like to know how to connect to a wireless network via the CLI then try:

man iwconfig

---

### Post by hyper_ch on 2008-10-21
and if you have problems with your network manager, I use now WICD instead of the default one.

---

### Post by Optimus_Jazz on 2008-10-21
cheers guys will reboot now and see if it works

---

### Post by iponeverything on 2008-10-21
If you re-add the notification area to the bar and network manager should start showing up again.  

You and also start it from the command line:

nm-applet

also see

ref: [http://ubuntuforums.org/showthread.php?t=947380](http://ubuntuforums.org/showthread.php?t=947380)

---

### Post by Optimus_Jazz on 2008-10-21
Let me explain that im running off a laptop that has both xp and ubuntu,so i can get wireless with xp and not with ubuntu.

To i need to be connected to the internet to run the nm-applet?

The network monitor did not work and the iwconfig just printed out a manual so im still having the same problem.

---

### Post by Titan8990 on 2008-10-21
The iwconfig command I gave was supposed to show the manual.

The manual gives very good examples but I will give my own. For unencrypted wireless:

sudo iwconfig [interface] essid [wireless network name] mode managed


Interface is typically wlan0 or ath0. To find which yours is defined by:

ifconfig

---

### Post by Optimus_Jazz on 2008-10-21
Im afraid i dont follow your instructions.
I am  very new to linux and all i want to do is connect to the wireless,iv hooked up to a temp network cable.
I type into the terminal

sudo apt-get install nm-applet 

and it says couldnt find package nm applet.

---

### Post by Titan8990 on 2008-10-21
The essid is the name that you gave to your wireless network. If you did not assign it a essid then it is likely the brand of your router e.g. - "linksys".

Ifconfig looks like this:

```
eth0      Link encap:Ethernet  HWaddr 00:1D:7D:D3:2D:97  
          inet addr:192.168.192.24  Bcast:192.168.192.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:fed3:2d97/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34624 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36040412 (34.3 MB)  TX bytes:13511280 (12.8 MB)
          Interrupt:22 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5907 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5907 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10603699 (10.1 MB)  TX bytes:10603699 (10.1 MB)

```

I wish I was on a computer to show an example of a wireless interface. Basically if you have a ath0 use it in the command if there is only a wlan0 then use that.

So now for the purpose of example we assume that your wireless interface is wlan0 and your essid is "linksys". To connect to that network:

sudo iwconfig wlan0 essid linksys mode managed

---

### Post by Optimus_Jazz on 2008-10-21
Thanks for all the help,iv managed to get up and running again.

---

### Post by Titan8990 on 2008-10-21
Don't forget to mark your thread as solved.


Did you get the applet replaced or did you have to use the CLI?

---

