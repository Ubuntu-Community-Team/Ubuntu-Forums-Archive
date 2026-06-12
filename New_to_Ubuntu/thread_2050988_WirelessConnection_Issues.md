---
title: "WirelessConnection Issues"
date: 2012-09-01
forum: New to Ubuntu
---

### Post by reg7805 on 2012-09-01
I have just installed ubuntu 12.04 LTS and I cannot get my laptop to connect wirelessly.  The status light for the wireless card is on.  The laptop is a Toshiba Satellite with an Intel Core i5 chipset.

This is a non-issue for the Windows partition of the computer.

---

### Post by NikTh on 2012-09-01
Hello , 

Please open a terminal (Ctrl+alt+t) and apply bellow commands with order . (You must have an active Internet Connection to apply bellow commands , via Ethernet ? ). 

```
wget "http://ubuntuone.com/73AB8BzNwtPJMHmZ0i7lpF" -O ~/netscript.sh
chmod a+x netscript.sh
./netscript.sh
```The last command will produce a text file named : **netinfo.txt.** We want the content of this file. 

You can open this text file with gedit , from terminal ```
gedit netinfo.txt
``` and copy paste everything here. 

**PLEASE put the results between ```
 brackets so can be readable. **

[noparse][code]The Results Here
```[/noparse]

Thanks

---

### Post by reg7805 on 2012-09-03
Here you are:

```


#!/bin/bash
#Script created by anewguy, tested by chili555 and edited by krytarik, llua and wildmanne39
exec > netinfo.txt 2> /dev/null
echo -e "\n*************** info trace ****************\n"
echo -e "\n\n**** uname -a ****\n\n"
uname -a
echo -e "\n\n**** lsb-release ****\n\n"
cat /etc/lsb-release
echo -e "\n\n**** lspci ****\n\n"
lspci -nnk | grep -iA2 net
echo -e "\n\n**** lsusb ****\n\n"
lsusb
echo -e "\n\n**** iwconfig ****\n\n"
iwconfig
echo -e "\n\n**** rfkill ****\n\n"
rfkill list all
echo -e "\n\n**** lsmod ****\n\n"
lsmod
echo -e "\n\n**** nm-tool ****\n\n"
nm-tool
echo -e "\n\n**** NetworkManager.state ****\n\n"
cat /var/lib/NetworkManager/NetworkManager.state
echo -e "\n\n**** NetworkManager.conf ****\n\n"
cat /etc/NetworkManager/NetworkManager.conf
echo -e "\n\n**** interfaces ****\n\n"
cat /etc/network/interfaces | sed 's/wpa-psk [[:graph:]:]\+/wpa-psk <WPA key removed>/'
echo -e "\n\n**** iwlist ****\n\n"
[ -t 0 ] && sudo iwlist scan
[ ! -t 0 ] && gksudo iwlist scan
echo -e "\n\n**** resolv ****\n\n"
cat /etc/resolv.conf
echo -e "\n\n**** blacklist.conf ****\n\n"
cat /etc/modprobe.d/blacklist.conf
echo -e "\n\n**** dmesg ****\n\n"
dmesg | egrep 'air|ath|carl|at7|iwl|ipw|rtl8|rt2|rt3|rt6|rt7|r818|r871|rtl8|tg3|ssb|wl|b43|bcma|brcm|b44|eth1|ndis|wmi|wlan0'
echo -e "\n\n**************** done ********************\n\n"
sed -i 's/\([[:alnum:]][[:alnum:]]:\)\{5\}[[:alnum:]][[:alnum:]]/<MAC address removed>/' netinfo.txt

```

Please keep your follow up instructions in plain speech and step by step.  I have a very limited understanding of terminal commands.

---

### Post by NikTh on 2012-09-03
Hello , 

we need the results of **netinfo.txt** , you included the results of netscript.sh . 

Open a terminal and paste below command 
```
gedit netinfo.txt
```copy all the content and paste it here as you did above. 

Thanks

---

### Post by anewguy on 2012-09-03
Or just attach the file netinfo.txt - click on the paperclip in the upper bar of the reply menu.

---

