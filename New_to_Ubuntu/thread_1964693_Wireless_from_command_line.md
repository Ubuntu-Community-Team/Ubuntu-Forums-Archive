---
title: "Wireless from command line"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by darkeale on 2012-04-24
Hi,

I am trying to connect to the wireless from the command line.  It works from doing it the graphical way, so I know the wireless works.  I put in the following commands:-

sudo iwlist scan
sudo iwconfig wlan0 essid "essid"
sudo dhclient wlan0

then nothing happens.  No text comes up in the terminal.  I wonder if it might be because of my /etc/network/interfaces file because it only has:-

auto lo
iface lo inet loopback

any suggestions?

Thanks,
Alex

---

### Post by haqking on 2012-04-24
> **darkeale said:**
> Hi,

I am trying to connect to the wireless from the command line.  It works from doing it the graphical way, so I know the wireless works.  I put in the following commands:-

sudo iwlist scan
sudo iwconfig wlan0 essid "essid"
sudo dhclient wlan0

then nothing happens.  No text comes up in the terminal.  I wonder if it might be because of my ```
/etc/network/interfaces
``` file because it only has:-

auto lo
iface lo inet loopback

any suggestions?

Thanks,
Alex

there are a few ways you can do it.

You can edit your /etc/network/interfaces to have something like the following

```
# my wireless
auto wlan0
iface wlan0 inet dhcp
wireless-essid [ESSID]
wireless-mode [MODE] 
```

or for static

```
# my wireless
auto wlan0
iface wlan0 inet static
address x.x.x.x
netmask x.x.x.x
gateway x.x.x.x
wireless-essid [ESSID]
wireless-mode [MODE] 
```

assuming WPA is being used then with wpasupplicant

```
# my wireless
auto wlan0
iface wlan0 inet dhcp
wpa-ssid yourssid
wpa-psk yourkey
```

or you could use wicd and wicd-curses.

peace

---

### Post by darkeale on 2012-04-24
ok, what are the options for mode?  Under the iwlist scan results there is a setting mode = master, is that it?

---

### Post by haqking on 2012-04-24
> **darkeale said:**
> ok, what are the options for mode?  Under the iwlist scan results there is a setting mode = master, is that it?

managed or ad-hoc.

likely managed/infrastructure

But i dont know your setup

---

### Post by darkeale on 2012-04-24
ok.  It is a library internet connection so I have no idea about the setup, apart from there is no key required

---

### Post by haqking on 2012-04-24
> **darkeale said:**
> ok.  It is a library internet connection so I have no idea about the setup, apart from there is no key required

well if its a library and you are authorised to use it then ask them the information you need ;)

It is probably managed.

---

### Post by darkeale on 2012-04-24
Ok, it's working now.  I needed to disable the grapical gui program, then I was able to enter those commands I did originally without any problems.  Thanks for your help

---

### Post by haqking on 2012-04-24
> **darkeale said:**
> Ok, it's working now.  I needed to disable the grapical gui program, then I was able to enter those commands I did originally without any problems.  Thanks for your help

ahh i assumed you had no GUI hence you asking for CLI wireless.

Anyways glad you got it sorted.

Peace

---

