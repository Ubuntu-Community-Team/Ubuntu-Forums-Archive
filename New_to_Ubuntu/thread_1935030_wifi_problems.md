---
title: "wifi problems"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by ligia elena on 2012-03-03
Hiya I'm an absolute new comer and really need help since installing ubuntu I can't get my wirless to work I've got a HP Pavillion dv6700 notebook pc and the light is just staying orange I've tried reading some other posts and even doing what they said but to no avail please help

---

### Post by Jake5 on 2012-03-03
are you running verision 11.10?

---

### Post by Jake5 on 2012-03-03
sorry, here's some more info, If you are running 11.10 there is a dropdown icon in the upper right hand corner that looks like a wireless connection icon or a piece of pie. In the menu there is an option to Enable Wireless, hit that and it should work. if the option is unselectable try rebooting and try again.

---

### Post by ligia elena on 2012-03-04
Hiya thanks for your reply yes I am running version 11.10 however the option is unselectable after reebooting several times

---

### Post by bkratz on 2012-03-04
> **ligia elena said:**
> Hiya thanks for your reply yes I am running version 11.10 however the option is unselectable after reebooting several times



Perhaps we should find out what your card is:  Enter the terminal (cntrl+alt+t) or however you normally get there and enter the following: paste the results back here.

```
lspci -nnk | grep -iA2 net
```

also the results of:

```
rfkill list all
```

---

### Post by ligia elena on 2012-03-04
ligia@ligia-HP-Pavilion-dv6700-Notebook-PC:~$ lspci -nnk | grep -iA2 net
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:30cf]
    Kernel driver in use: forcedeth
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1364]
    Kernel driver in use: b43-pci-bridge
ligia@ligia-HP-Pavilion-dv6700-Notebook-PC:~$

---

### Post by ligia elena on 2012-03-04
ligia@ligia-HP-Pavilion-dv6700-Notebook-PC:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
ligia@ligia-HP-Pavilion-dv6700-Notebook-PC:~$

---

### Post by bkratz on 2012-03-04
Here is a good description of what is needed in both 11.04 and 11.10 for the BCM4311 card.  The 11.10 section is towards the end.

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---

### Post by ligia elena on 2012-03-04
> **bkratz said:**
> Here is a good description of what is needed in both 11.04 and 11.10 for the BCM4311 card.  The 11.10 section is towards the end.

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

thankyou for your reply I followed exactly what it said on the page and still cannot get my wifi working

---

### Post by Jake5 on 2012-03-04
I was having the same issue with lubuntu on my laptop,
maybe this will help, worked for me:

```
sudo ifconfig wlan0 up
```

I've been told that this is not a command you run a lot. Once it brought up my wifi I rebooted and it still worked, I have yet to try to turn it off, and see no reason to, at least not for me. I had to run it a few times and open a browser really quickly before it worked.

heres a link to the thread:[http://ubuntuforums.org/showthread.php?t=1935029](http://ubuntuforums.org/showthread.php?t=1935029)

---

### Post by bkratz on 2012-03-05
> **ligia elena said:**
> thankyou for your reply I followed exactly what it said on the page and still cannot get my wifi working


Can you post the outputs of the following back here ?

```
cat /etc/modprobe.d/blacklist
iwconfig
lshw -C network
sudo iwlist scan

```use the code tags <> for readability. The last command will require your password which will not be echoed to the screen--just press enter when you put it in.

---

### Post by rocksmtu on 2012-03-05
I was able to get more detail about my problem when I used the dmesg command.
 
I was able to find that I was missing firmware files and particulaly which files. Then it was just a matter of copying the correct files to the location.
 
What is your dmesg output?

---

### Post by ligia elena on 2012-03-05
thanks jake 5 and bkratz I managed to get it working after downloading several drivers from additional drivers thanks again

---

