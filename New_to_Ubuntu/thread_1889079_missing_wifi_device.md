---
title: "missing wifi device"
date: 2011-11-30
forum: New to Ubuntu
---

### Post by PermNoob on 2011-11-30
just installed the latest 32 bit ubuntu desktop on my dell inspiron 6400 laptop. the laptop is new to me.  i can not connect to wifi because there is no wireless network option. lspci turns up
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

ifconfig only turns up eth1 and lo, nothing else. no idea what the next step is.  thanks for any help, excited to have a laptop for the first time in years

---

### Post by gandaran on 2011-11-30
have you checked additional drivers to enable the broadcom driver?

---

### Post by farrinux on 2011-11-30
> **PermNoob said:**
> just installed the latest 32 bit ubuntu desktop on my dell inspiron 6400 laptop. the laptop is new to me.  i can not connect to wifi because there is no wireless network option. lspci turns up
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

ifconfig only turns up eth1 and lo, nothing else. no idea what the next step is.  thanks for any help, excited to have a laptop for the first time in years

About the only thing I can suggest is trying the NDIS wrapper.

---

### Post by PermNoob on 2011-11-30
there is nothing listed under additional drivers

---

### Post by gandaran on 2011-11-30
> **PermNoob said:**
> there is nothing listed under additional drivers
which ubuntu version?
you have to connect with wired internet to get the driver in additional drivers and if need update the software package list first.
```
sudo apt-get update
```

---

### Post by gandaran on 2011-11-30
> **farrinux said:**
> About the only thing I can suggest is trying the NDIS wrapper.
not recommended for broadcom chipsets as Ubuntu provides all broadcom devices with linux drivers, they aren't enabled  by default due to broadcom drivers are propriety software.

---

### Post by bluexrider on 2011-11-30
> **PermNoob said:**
> just installed the latest 32 bit ubuntu desktop on my dell inspiron 6400 laptop. the laptop is new to me.  i can not connect to wifi because there is no wireless network option. lspci turns up
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

ifconfig only turns up eth1 and lo, nothing else. no idea what the next step is.  thanks for any help, excited to have a laptop for the first time in years

i realize this may be redundant but, I GOTTA ASK, did you flip the switch to on? laugh if you want but  it happens.

---

### Post by PermNoob on 2011-11-30
ok, plugged into ethernet (on the laptop now!) and ran the updates, now i have the proper driver listed in additional drivers for this broadcom device, however it still doesn't exist under the dropdown menu, and does not exist when i hit ifconfig or iwconfig.

also, can't find a hardware switch for it on the laptop anywhere, there is a function button on the keyboard(ie fn+f2), but it seems to do nothing.

---

### Post by PermNoob on 2011-11-30
oh! 11.10 desktop version

---

### Post by fdrake on 2011-11-30
can you post the output:
```

sudo -vvv -s 0b:00.0
sudo rfkill list all
iwconfig

```

---

### Post by bkratz on 2011-11-30
> **PermNoob said:**
> just installed the latest 32 bit ubuntu desktop on my dell inspiron 6400 laptop. the laptop is new to me.  i can not connect to wifi because there is no wireless network option. lspci turns up
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

ifconfig only turns up eth1 and lo, nothing else. no idea what the next step is.  thanks for any help, excited to have a laptop for the first time in years


This will work for you in 11.04 or 11.10

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---

### Post by PermNoob on 2011-12-01
the walkthrough worked, although for whatever reason, the last rm command was unneeded, neither file existed, the one in the 11.04 directions and the one in the 11.10 directions. seems to work fine, tested here and on [www.iamawesome.com](www.iamawesome.com)

---

### Post by bkratz on 2011-12-01
Glad it worked for you ( I knew it would!!), don't worry about the last two items, they are not always there. congratulations and enjoy!

---

