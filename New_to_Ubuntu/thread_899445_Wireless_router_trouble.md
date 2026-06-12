---
title: "Wireless router trouble"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by emogstad on 2008-08-24
Hey!

I've been trying to connect to my w-lan router for some days now from Ubuntu, with little success. Anyway, I was at a friends place where I easily got to connect with their wireless system.

So I took a look into the system log of the router, and it says:

```
Aug 24 16:02:29 (none) user.warn klogd: [0][12][3][342710] received Assoc req with unsupported rates from
Aug 24 16:02:29 (none) user.warn klogd: [0][12][3][342710] 0:13:2:D6:63:F
```

multiple times, and then switches to saying:

```
Aug 24 16:02:28 (none) user.warn klogd: [0][14][3][335930] schProcessRR : staId 0 for STA [0:13:2:d6:63:f]
Aug 24 16:02:28 (none) user.warn klogd: [0][14][3][335930] Sending deauth
```

a number times. And I guess that's where I turned the wireless off and went for the wired connection.

I guess the first one, "recieved Assoc req with unsupported rates from [my device]" has something to do with it. Does anyone have a clue what this means, and what I should configure to make it work?

Thanks for any answers!

 - Emil

---

### Post by phidia on 2008-08-24
Does Nework Manager show the wireless signal that you want to connect to and is there security (password protection) on the network you can't connect to?
When you are attempting connection to your router open a terminal and enter "iwconfig" post the output here.

---

### Post by emogstad on 2008-08-24
Hey! Yes, and yes. When I click on the network icon in the toolbar in the upper left, I can see the network. If I click it, it will try and connect, allthough the blue dots never turn green, and then it gives up after a while.

The output of iwconfig:

```
emil@emil-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:13:10:B3:1C:D8   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

emil@emil-laptop:~$ 

```

Thank you so much for your quick answer!

---

### Post by phidia on 2008-08-24
Are you using KDE or what desktop are you using? 
You don't appear to have a ESSID selected for your network. Your network has to have a name it goes by and that needs to be selected in Network Manager.
For further networking info you can look at the guides and troubleshooting Ubuntu wiki [here]("https://help.ubuntu.com/community/NetworkDevices"), but also feel free to post back with further questions.

---

### Post by emogstad on 2008-08-24
I'm using Gnome. Yeah, I think it's pretty weird that it dont get the ssid, since it shows up in the menu.

I've tried manual config without much luck.

---

