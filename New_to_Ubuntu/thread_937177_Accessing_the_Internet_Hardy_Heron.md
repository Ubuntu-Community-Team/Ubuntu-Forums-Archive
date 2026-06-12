---
title: "Accessing the Internet Hardy Heron"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by R Tanner on 2008-10-03
Hi,

I'm trying to pull up the internet on my laptop. I think my wlan0 is configured (not sure what it means though).  In my /etc/network/interfaces file it says the following: 

auto lo
iface lo inet loopback



iface wlan0 inet dhcp
wpa-psk 0c06f24de59f8300268f56cab3392c6c93200081971d5982c22b8295bc181bd1
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid MyHotBox

auto wlan0

iface eth0 inet dhcp

auto eth0


uname -mr returns the following:

2.6.24-19-generic i686

What should I do so I can get wifi...I'm still just really learning...

Thanks in advance

---

### Post by R Tanner on 2008-10-03
I should also mention the following I'm thinking...

When I type this:

```
sudo ifup wlan0
```

It gives me this...

```
ifup: interface wlan0 already configured
```

I don't necessarily need to use eth0 to access wifi right?  I can use wlan0...

---

### Post by hyper_ch on 2008-10-03
I had troubles with the network manager in Ibex... then I found WICD and like it quite well...  you might want to have a look at it:  [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

