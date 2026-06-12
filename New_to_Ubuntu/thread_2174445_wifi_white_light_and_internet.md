---
title: "wifi white light and internet"
date: 2013-09-14
forum: New to Ubuntu
---

### Post by salmendar on 2013-09-14
the problem is tht after working over two months on a ubuntu server. i installed ubuntu desktop on my laptop. and today i had an issue that when i turned my wifi off using fn+F9(wifi) keys i iturned off. but after that the yellow light wont turn white. and even when the laptop shows and connects to networks there isn't any actual communication. please tell me how to correct this. 
i have a HP probook 5220m ecostar .

i have even tried to restart with wifi on but it doesnt do anything.

---

### Post by grahammechanical on 2013-09-14
You can try running some commands to find out the state WiFi is in on Ubuntu

```
rfkill list
```

You need to see something like this

> 0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

If either of those show a yes, then the wireless adapter is either swtiched of by software (ubuntu) or by the the hardware (fn+F9).

```
mn-tool
```

That should show something like

> Type:              802.11 WiFi
  Driver:            rtl8187
  State:             connected
  Default:           no
  HW Address:        00:15:AF:0E:9B:E0

  Capabilities:
    Speed:           48 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

Followed by a list of wireless access points in range of your wireless adapter. If you do not see any wireless access points then the adapter is not transmitting or receiving wireless signals.

To fix things try

```
rfkill unblock wifi
```

or

```
 sudo ifconfig wlan0 down
```
followed by
```
ifconfig wlan0 up
```

give each of these two commands a few seconds to work. You can also use the Network Manager icon to disable and enable Wi-Fi. Something else to look at is the contents of the interfaces file.

```
cat /etc/network/interfaces
```

It should read

> auto lo
iface lo inet loopback


Anything else will cause a conflict with Network Manager and stop it working. Since Ubuntu started using Network Manager editing the interfaces file to include network connections has not been necessary. So, edit out any additional lines that are in the interfaces file and then reboot.

Regards.

---

### Post by varunendra on 2013-09-15
Please first check what grahammechanical suggested. It should most probably figure out what the problem is and probably even fix it. There is a slight correction though -
The second command he posted should be -
```
 nm-tool
```
..not "mn-tool". Obviously, it is a typo.

If however, the suggestions couldn't help you, then please follow the "Wireless Script" link in my signature, download and run the script as per instructions there and post back the report it generates.

---

### Post by salmendar on 2013-09-16
the internet has started working on wifi . its slow though but still something is better than nothing. the light is still yellow though, that might besome other issue.


thanking the ubuntu team and specially[URL="http://ubuntuforums.org/member.php?u=1087323"][B][COLOR=#000000]
grahammechanical[/COLOR][/B][/URL] 
for help
THANK YOU all

---

### Post by varunendra on 2013-09-16
> **salmendar said:**
> the internet has started working on wifi . its slow though but still something is better than nothing.

How slow? Satisfactory or less than satisfactory?

I'd still recommend you to post the script results so we can see if something can be done to make the connection any better. That is, of course if you are willing to try a few more suggestions.. :)

---

