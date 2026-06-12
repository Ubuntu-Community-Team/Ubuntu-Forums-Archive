---
title: "A start job is running for raise network interfaces (5 mins 1 sec) in ubuntu16.04"
date: 2016-05-04
forum: New to Ubuntu
---

### Post by thaniyarasu-gmail on 2016-05-04
i have installed ubuntu 16.04 in my laptop.
starting ubuntu is fast when i have LAN cabled connected.

when LAN cable disconnected then it is taking around 5 minutes to get login screen.
it was showing this message with timer on screen at that long time.
***"A start job is running for raise network interfaces (2 minutes of 5 mins 1 sec)"***

1) how can i skip this delay (5 mins for waiting network).
like if there are some shortcut keys which i typed then the startup script should not wait for 5 mins, it should directly skip the network interface checking and go to login screen.

or 
2) how can i permanently stop network interface check only when LAN cable not connected.

Thanks
Thani

---

### Post by grahammechanical on 2016-05-04
Do you want my guess?

The system is set up to make a wired connection to the router and to do that automatically. But is cannot complete the task because the ethernet cable is disconnected. So, it tries again and again until finally some part of the OS gets the message.

There should be an icon on the top panel for the Network Manager. With the cable connected the icon will be two arrows going in the opposite direction. With the cable disconnected the icon will look like an upside down cone. Click on the icon; select Edit Connections; Select Wired Connection; Click Edit; Go to the General tab and untick the box labelled "Automatically connect to this network when it is available."

In future when you want to make a wired connection to the router, then Click on the Network Manager icon and untick & re-tick Enable Networking. That should prompt Network Manager to start making the wired connection to the router.

Regards.

---

### Post by thaniyarasu-gmail on 2016-05-05
there is no "[COLOR=#000000]Wired Connection" in that dialog panel. 
my ubuntu is 16.04 
[/COLOR][COLOR=#000000]
[/COLOR]

---

### Post by houstonbofh on 2016-05-05
Don't feel bad... I started testing Ubuntu Server 16.04 today and this bit me too.  And there is no Network Manager, so it is probably something in the new systemd network services.  Sorry, but I do not have a fix yet.

---

### Post by matt_symes on 2016-05-05
Hi

You may want to read this.

[https://www.freedesktop.org/wiki/Software/systemd/NetworkTarget/](https://www.freedesktop.org/wiki/Software/systemd/NetworkTarget/)

I would be looking to disable

```
systemd-networkd-wait-online.service
```

or

```
NetworkManager-wait-online.service
```

Look to see which ones are enabled with...

```
systemctl status systemd-networkd-wait-online.service
```
```
systemctl status NetworkManager-wait-online.service
```

Disable one and, if it does not fix it, re-enable it and disable the other one.

Here's an example

```
sudo systemctl disable systemd-networkd-wait-online.service
```

```
sudo systemctl enable systemd-networkd-wait-online.service
```

When enabled (and from the website above)

> This will ensure that all configured network devices are up and have an IP address assigned before boot continues. 

Please post back if either work and post which one does work.

Kind regards

---

### Post by senpai2 on 2016-05-13
You can reduce the timeout for the job that is trying to raise the network interfaces in the following file.

```
/etc/systemd/system/network-online.targets.wants/networking.service
```

Simply edit the file

```
sudo vi /etc/systemd/system/network-online.targets.wants/networking.service 
```

You can change the following line to your preference.

```
21:TimeoutStartSec=5min 
```

You will need to reload the daemon as well.

```
sudo systemctl daemon-reload
```


Note: If any of your specified network interfaces fail to respond in your new timeout, it will not be raised. This failure will be indicated at boot when this job is ran.

---

### Post by houstonbofh on 2016-05-15
> **senpai2 said:**
> You can reduce the timeout for the job that is trying to raise the network interfaces in the following file.

```
/etc/systemd/system/network-online.targets.wants/networking.service
```

Simply edit the file

```
sudo vi /etc/systemd/system/network-online.targets.wants/networking.service 
```


You are a wonderful person!  That worked!  Other then that path is actually a link to /lib/systemd/system/networking.service but that was the key!

```
21:TimeoutStartSec=30sec 
```

---

### Post by thaniyarasu-gmail on 2016-06-14
i am ok with 

21:TimeoutStartSec=30sec 

Thanks

---

### Post by physicist1616 on 2016-06-29
> **houstonbofh said:**
> Don't feel bad... I started testing Ubuntu Server 16.04 today and this bit me too.  And there is no Network Manager, so it is probably something in the new systemd network services.  Sorry, but I do not have a fix yet.

The fix for Ubuntu Server is pretty simple:  Change the line in /etc/network/interfaces that reads, "auto {Your ethernet adapter's name here}" to "allow-hotplug {Your ethernet adapter's name here}". 
It's waiting for a DHCP reply, if my Wireshark-Fu is correct.

In my case, that looks like:
```

#Original Line
auto ens34
iface ens34 inet dhcp

#New line
allow-hotplug ens34
iface ens34 inet dhcp

```
It's reasonable to suggest that setting a static IP would do it too.

I don't know the equivalent in the GUI stuff.  

If you are indeed rolling with a PC that is hotplugging ethernet (like a laptop), this is the most correct fix, as it informs the system that this network shouldn't be required on startup, and, if you wanted, you could still configure another network that is auto that *is* required on startup.

---

### Post by nielsduelund on 2016-07-08
That seems to be not just a workaround, but the actual solution. To me at least :-D
It seems to me that this is the way that network connections used to work when specifying auto.

---

### Post by poulad on 2016-09-06
I ran this command and it solved my problem. I guess I still need to compile and install my Ethernet driver.

```
sudo systemctl disable networking.service 
```

---

### Post by Tadaen_Sylvermane on 2016-09-06
In /etc/network/interfaces change auto to allow-hotplug for the appropriate interface.

This should only be an issue in server version

---

### Post by yerivan on 2017-02-04
This just work for me too!!
TimeoutStartSec=10sec
But I set it to 10 sec and when I reboot the system it shows me failed when look for network interfaces.:D

---

### Post by arpaham on 2017-03-03
> **physicist1616 said:**
> The fix for Ubuntu Server is pretty simple:  Change the line in /etc/network/interfaces that reads, "auto {Your ethernet adapter's name here}" to "allow-hotplug {Your ethernet adapter's name here}". 
It's waiting for a DHCP reply, if my Wireshark-Fu is correct.

In my case, that looks like:
```

#Original Line
auto ens34
iface ens34 inet dhcp

#New line
allow-hotplug ens34
iface ens34 inet dhcp

```
It's reasonable to suggest that setting a static IP would do it too.

I don't know the equivalent in the GUI stuff.  

If you are indeed rolling with a PC that is hotplugging ethernet (like a laptop), this is the most correct fix, as it informs the system that this network shouldn't be required on startup, and, if you wanted, you could still configure another network that is auto that *is* required on startup.


Thanks a lot!!  
A have a Acer Netbook AspireOne and this one was the best solution for me. 
Now everything works without that awful timeout countdown. :D

---

### Post by glebaron2 on 2017-04-05
> **physicist1616 said:**
> The fix for Ubuntu Server is pretty simple:  Change the line in /etc/network/interfaces that reads, "auto {Your ethernet adapter's name here}" to "allow-hotplug {Your ethernet adapter's name here}". 
It's waiting for a DHCP reply, if my Wireshark-Fu is correct.

In my case, that looks like:
```

#Original Line
auto ens34
iface ens34 inet dhcp

#New line
allow-hotplug ens34
iface ens34 inet dhcp

```
It's reasonable to suggest that setting a static IP would do it too.

I don't know the equivalent in the GUI stuff.  

If you are indeed rolling with a PC that is hotplugging ethernet (like a laptop), this is the most correct fix, as it informs the system that this network shouldn't be required on startup, and, if you wanted, you could still configure another network that is auto that *is* required on startup.

This was the correct answer for me! A rather small but critical difference if you are installing the server version and you want to run it using dhcp. 
I changed this setting and all the network flakiness disappeared.

---

### Post by whit-launchpad on 2017-04-06
Does anyone know the logic of wanting 5 minutes? That seems a crazy default -- especially when the default splash screen gives no indication of what's broken. What variety of network trouble would clear by itself after the first minute of waiting?

Thanks for the useful explanations here.

---

### Post by houstonbofh on 2017-04-26
> **whit-launchpad said:**
> Does anyone know the logic of wanting 5 minutes? That seems a crazy default -- especially when the default splash screen gives no indication of what's broken. What variety of network trouble would clear by itself after the first minute of waiting?

I have given up asking questions like that.  Usually there is no answer.  But sometimes there is an answer, and that is actually worse. (Like:  We did it so it boots faster!)

---

### Post by ramesh24 on 2017-06-27
To reduce the waiting time:
Edit the file /etc/dhcp/dhclient.conf 
to set timeout to a minimum time like: timeout 15

---

### Post by hawk291 on 2017-09-03
Thank you physicist1616, your solution helped me.

[COLOR=#000000]*/etc/network/interfaces*[/COLOR]

#Original Line
auto ens34
iface ens34 inet dhcp

#New line
allow-hotplug ens34
iface ens34 inet dhcp

---

### Post by chris.herman on 2018-01-06
> **grahammechanical said:**
> Do you want my guess?
The system is set up to make a wired connection to the router and to do that automatically. But is cannot complete the task because the ethernet cable is disconnected. 
Regards.

8 years later this comment helped me. Thanks.
(router power plug... bummer...)

---

