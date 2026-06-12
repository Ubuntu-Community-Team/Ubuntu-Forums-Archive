---
title: "[SOLVED] Atheros wireless Problem"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by nnjond on 2008-08-15
Hi, can anyone help me please?

I now know, my new Laptop has the “dreaded Atheros wireless...“ which requires the installation of:

“ndiswrapper-common
ndiswrapper-utils-1.9 (or whatever version is displayed)
ndisgtk”.

And

net5211.inf

Which I seem to have done successfully. But my panel icon still claims no network connection. What should I do Now?

---

### Post by phidia on 2008-08-15
Have you used Network Manager from System > Administration to configure/enable your network, and is this an open or password protected network?
> iwconfig What does that output?

---

### Post by bobnutfield on 2008-08-15
If the driver successfully installed with ndiswrapper, the last step is:

> sudo modprobe ndiswrapper

You may have done that, but many leave that step out and that is what will start your wireless working.

---

### Post by nnjond on 2008-08-15
thanks for your help. things have moved on and I get a swirling icon on my panel. Does that mean everthings ok and i should move to a hotspot?

nnjond@nnjond-laptop:~$ sudo modprobe ndiswrapper 
[sudo] password for nnjond: 
nnjond@nnjond-laptop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

nnjond@nnjond-laptop:~$

---

### Post by bobnutfield on 2008-08-15
Not quite yet, but your wireless should now be showing up in your network config GUI.  You could also set it up on the command line, but try the GUI first.  Your wireless is recognized, but it is not associated with your router yet

---

### Post by nnjond on 2008-08-15
I don't think it can connect to my router. I dont havve wifi at home. I want to use this laptop at various other places

---

### Post by bobnutfield on 2008-08-15
Oh, I see, I misunderstood, thought you trying to connect at home.  In this case, you can just go to a hot spot, open the network gui, and set up the network, or you may be able to just click on the swirling icon and choose the network.  When you did sudo modprobe, you were loading the module for this session.  When you reboot, you will need to do modprobe again.  To make ndiswrapper load at boot time, do this:

> echo 'ndiswrapper' | sudo tee -a /etc/modules

That will load ndiswrapper automatically at boot.

---

### Post by nnjond on 2008-08-15
Thanks alot. won't mark this as solved yet. Am off to a Hotspot.

---

