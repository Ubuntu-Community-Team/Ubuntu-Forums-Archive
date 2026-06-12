---
title: "Wireless: Unsecure, WEP or WPA"
date: 2008-03-09
forum: Outdated Tutorials &amp; Tips
---

### Post by ruiruas on 2008-03-09
I assume here that you have a wireless card already working. If not, I suggest using "ndiswrapper" for most cards, and the native linux drivers where available. The focus of this article is on the access of different networks (unsecured, WEP or WPA).

I'm not an expert, but I've been trying different security setups with ubuntu and I found that there was no easy to follow "howto". The other problem was that most articles rely on specific programs like "wifi", "wicd", "network-manager", etc. 
I tried all of them and found that neither could work well with all the security protocols used (at least with my cards: an EDIMAX 7318usg and an internal usb Realtek 8197b). 

Since I wanted a solution to cover all options, I started to try editing the file "/etc/network/interfaces" manually and I finally succeded in making my network cards work with every network I can find (at least until now :-D).

And now to work:
In this article I assume that the network card is already installed and that it is named "wlan0".

1.Unsecured Network - write this in "interfaces" (of course that x.x.x.x are all to replace with the adequate numbers and "unsecure" is just a name...):  

```
iface unsecure inet static
address x.x.x.x
netmask x.x.x.x
gateway x.x.x.x
wireless-mode Managed
wireless-essid network_name
dns-nameservers x.x.x.x x.x.x.x

```

Don't forget that the gateway is the modem/router IP or the proxy IP, not the access point IP. dns-nameservers are optional, depending on your LAN setup (if you have a direct connection, you don't need it)
If you connect with dhcp, change the first line to:

```
iface unsecure inet dhcp
```

And delete the lines "address", "netmask" and "gateway"
Either way, after saving the file "interfaces" you only need to issue the command:

```
$sudo ifup wlan0=unsecure
```

and its done! If you receive an error the first time, you may need to restart your network (also after reboot) with:

```
$sudo /etc/init.d/networking restart
```

2.If you have another network wich is a secured WEP network, you will have to append the following to "interfaces":

```
iface wepsecure inet static
address x.x.x.x
netmask x.x.x.x
gateway x.x.x.x
wireless-mode Managed
wireless-essid network_name
wireless-key your_wireless_key
dns-nameservers x.x.x.x x.x.x.x

```

Again, the static option can be dhcp, dns-nameservers are optional and about the wireless_key: you can enter the key in hex digits like "xxxx-xxxx-xxxx-xxxx" or "xxxxxxxx" or as an ASCII string, using the "s:your_wireless_key" (attention to the "s:" prefix). After that, issue the command:

```
$sudo ifup wlan0=wepsecure
```

And that's it!(you may also need to restart the network first...)

3.Now for the WPA network:
First of all you'll have to use the essid and passwd to issue the following command:

```
$wpa_pasphrase your_network_essid your_wpa_password

```

You'll get the following result:

```
network={
        ssid="your_network_essid"
        #psk="your_wpa_password"
        psk=akokdokvf4ok5o6ko7kgbnmfjdkjdskjfmfmr45jk5kj67798384jfnf
}

```
then, use the result to write the following to the "interfaces" file:
 ```

iface wpanetwork inet dhcp
wpa-driver wext
wpa-ssid your_network_essid
wpa-ap-scan 2
wpa-proto TKIP
wpa-pairwise TKIP
wpa-key-mgmt WPA-PSK
wpa-psk akokdokvf4ok5o6ko7kgbnmfjdkjdskjfmfmr45jk5kj67798384jfnf
```

Again, you can use static IP addressing instead of dhcp and you can include the dns-nameservers if you need to. Now, its the "usual":

```
$sudo ifup wlan0=wpanetwork
```

And you're done!!!
This way, you named each network with a name of your choice (like "unsecure", "wepsecure", "wpanetwork", "myhome", etc.)and then you only associate the device "wlan0" with the desired network (wlan0=myhome).
Every time you need to access another network, you add the setup to "interfaces" (you can save as many as you like there) and call it whenever you like.

Of course there are several other options usable in "interfaces" and if you want, you can find out more about them using:

```
$man iwconfig
```
 or
```
$man ifconfig
```

The wpa options are very well explained by "Wieman01" in:

[http://ubuntuforums.org/showthread.php?t=202834]("http://ubuntuforums.org/showthread.php?t=202834")

Final note: if you have a frequently accessed network, you can create a small script to connect like this:
Create a file with 

```
$nano myhome.sh
```

write this:

```
#!/bin/bash
/etc/init.d/networking restart
ifup wlan0=myhome

```
then save it and run it as root from the command line or with a "custom application launcher" added to your panel with "gksudo /path/to/script/myhome.sh".

I found out that "interfaces" can't handle dns-nameservers. So in DHCP there's no problem but if you have a static IP, you wont get the correct DNS.
To solve this problem, add the following to your wireless script (or issue the command in the console):
```

echo 'nameserver x.x.x.x' | tee /etc/resolv.conf
```

I hope this will help someone! Have fun with your wireless access.

---

### Post by bhavi on 2008-03-21
Yes mate.. But I believe WEP is more insecure than WPA...

Ref this link for a discussion (as an example)

[http://forums.pcworld.co.nz/showthread.php?t=77606](http://forums.pcworld.co.nz/showthread.php?t=77606)

---

### Post by ruiruas on 2008-03-22
Hi Bhavi,
of course WEP is less secure... unsecure networks are even less secure! ;-)
the point of my post is just to help anyone who has to connect to wireless networks, nothing else.
Anyway, your remark is true and it's allways good to remind people about the dangers of wireless connections, so the best choice is obviously the WPA with PSK (it's what I use at home!). 
Best regards,

---

