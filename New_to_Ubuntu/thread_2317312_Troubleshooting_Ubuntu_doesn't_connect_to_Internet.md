---
title: "Troubleshooting: Ubuntu doesn't connect to Internet, dual boot Windows does."
date: 2016-03-15
forum: New to Ubuntu
---

### Post by arturo18 on 2016-03-15
Hello you all,

I'm a completely new user of Linux; I've just got Ubuntu 15.10 installed in a dual boot setup with Windows 10 in a new computer. Wifi connection works without problems in Windows, but when I boot with Linux it doesn't work. What should I look for first for troubleshooting? Thank you!

---

### Post by grahammechanical on 2016-03-15
A little explanation of what "doesn't connect to the internet" means, would help.

Did you install Ubuntu using a wired (ethernet) connection to the router? Is Ubuntu connecting to the router but not connecting to the internet? Is it WiFi that you want to set up and is not working? Is WiFi deactivated in Windows 10? Does the machine require a keyboard combination to be pressed to activate WiFi?

There is a command that you can run. Post the out in your thread.

```
nmcli general status
```

This is what I get on my machine
graham@sdb7-Dev:~$ nmcli general status
  STATE         CONNECTIVITY  WIFI-HW          WIFI               WWAN-HW      WWAN    
connected             full                                              enabled         disabled            enabled             enabled

As you can see my WiFi adapter is switched on (WiFi-HW enabled). But my WiFi is disabled. That is because I am not using WiFi to connect to the router. My ethernet adapters are switched on (WWAN-HW enabled). I have two ehternet adapters but only one has a connection to the router. 

Another command to run

```
nmcli connection
```

graham@sdb7-Dev:~$ nmcli connection
NAME                                        UUID                                       TYPE             DEVICE 
Wired connection 2  57c9c642-e90f-49af-a428-0c75fe66ccc9  802-3-ethernet   --     
Wired connection 1  56b038b1-e28f-4c0e-90ba-9c95a324036d  802-3-ethernet   enp2s0 
PlusnetWireless     8791dc04-d0b3-4f0a-98cc-b6c1deb9e6ce  802-11-wireless  --     

This shows that I have 2 ethernet adapters & one WiFI adapter but only one device is active. Wired connection 1.

A third command

```
nmcli device
```

graham@sdb7-Dev:~$ nmcli device
DEVICE           TYPE      STATE        CONNECTION         
enp2s0           ethernet  connected    Wired connection 1 
enp6s4           ethernet  unavailable  --                 
wlx0015af0e9be0  wifi      unavailable  --                 
lo               loopback  unmanaged    --       


Regards.

---

### Post by jondog154 on 2016-03-16
First easy step would be open Additional Drivers and see if your wifi card is listed.... next thing I would do is open a terminal run sudo lshw then post the output of that back to me :)


[IMG]http://i.stack.imgur.com/lNmbc.png[/IMG]

---

### Post by Edward_Fish on 2016-03-16
Sorry, I can't really help you here. I believe *lspci* could tell you which card you have, which you can then just look up - I expect someone else will have had the same problem.
I do remember that I had a very old computer where Vista could connect to WiFi, but Ubuntu did not detect an wireless card. I managed to fix it by using *apt-get purge* on some driver package, but I can't remember which one. It believe it was a BCM4311 card, which a quick search let me fix.
I installed Ubuntu on a newer computer and WiFi worked straight away.

---

### Post by arturo18 on 2016-03-16
Thank you to you all for the help being provided, it is really useful given that I am totally new to Ubuntu/Linux. I'm using an Asus USB-AC56 adapter and a likely explanation for what happens is that the adapter drivers are installed in Windows but not in Linux. I'll check that and report here what I find out to close this thread or ask for further help!

---

### Post by arturo18 on 2016-03-16
Hi again, I confirm that the "problem" was due to not having installed the WiFi adapter drivers in Ubuntu. Thank you all!

---

