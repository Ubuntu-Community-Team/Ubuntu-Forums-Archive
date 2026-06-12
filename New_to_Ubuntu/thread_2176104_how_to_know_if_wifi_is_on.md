---
title: "how to know if wifi is on"
date: 2013-09-22
forum: New to Ubuntu
---

### Post by kom333 on 2013-09-22
Hello there :D

I bought Asus Eee PC 1015BX and I dont know when my wifi is on or off because there is no signalization light. So I am wondering is it possible to find out that from terminal and is there a way how to turn wifi on/off? :D

Regards.

---

### Post by arkan01d on 2013-09-22
[http://support.asus.com/Troubleshooting/detail.aspx?SLanguage=en&p=20&m=Eee%20PC%201015BX&s=1&hashedid=FD1aZOQQFDZYA0RB&os=&no=1006](http://support.asus.com/Troubleshooting/detail.aspx?SLanguage=en&p=20&m=Eee%20PC%201015BX&s=1&hashedid=FD1aZOQQFDZYA0RB&os=&no=1006)

Do you not see the signal showing a connection? [[FONT=arial]http://screencloud.net/v/9wSs[/FONT]]("http://screencloud.net/v/9wSs")

---

### Post by demisgc on 2013-09-22
If your wifi is enabled from shell you can type 

iwconfig wlan0 scanning

If it return the list o SSID from networks near you that means the Wireless is enable.

---

### Post by varunendra on 2013-09-23
By the way, if your laptop has a wifi led, and it does not reflect the status of the wifi, it may be a problem (led not being controlled, or wifi never turning on/off).

Usual way to see if wifi and it's led are on/off -
```
rfkill list all
```
Usually the above will show two wireless interfaces - one for the LED, the other for the wifi card. Hard blocked means turned off by hardware switch (or the "Fn+F2" switch in asus laptops), Soft blocked means turned off by the software (the network manager or a command).

---

### Post by kom333 on 2013-09-23
Well arcan01d, yes i can see the signal. 

Demisgc, my wifi is enabled and i typed that command and i have got this message back: 
scanning: Resolver internal error
ifconfig: `--help' gives usage information.

And varunendra, yes, my has a wifi led but it is always on and that is confusing me. I tried command that you gave me and here is the result: 
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no. What does that mean? Is it good or bad? :)

---

### Post by steeldriver on 2013-09-23
I think demisgc might have meant

```
**iwlist** wlan0 scanning
```

You can also use the nmcli tool e.g. for a simple 'enabled / disabled' wifi status

```
nmcli nm wifi
```

or to see the status of all interfaces (wired and wireless)

```
nmcli nm status
```

or for a particular interface e.g. wlan0

```
nmcli nm status iface wlan0
```

---

### Post by varunendra on 2013-09-23
> **kom333 said:**
> 
0: **phy0: Wireless LAN**
    Soft blocked: no
    Hard blocked: no
1: **brcmwl-0: Wireless LAN**
    Soft blocked: no
    Hard blocked: no
2: **asus-wlan: Wireless LAN**
    Soft blocked: no
    Hard blocked: no

Looks good to me in its current form (nothing is blocked, means wifi is active and so is the LED). LED always on = Wifi always on.

Since it is an asus, I believe the hot key to turn the wifi on/off would be Fn+F2. Is that combo not working? Try it once (or twice, or thrice.. I had to do it four times when there was a problem with its wmi driver) and check again -
```
rfkill list all
```
Does any of the above change its state to "Hard blocked: **yes**" ? If not, try disabling wifi from Network manage (remove the tick mark from "Enable Wireless") and check rfkill again. Any one changes to "Soft blocked: **yes**"? Which one?

---

### Post by kom333 on 2013-09-29
ok thank you all but i tried:
```
nmcli nm wifi
``` and it is working. :D

---

