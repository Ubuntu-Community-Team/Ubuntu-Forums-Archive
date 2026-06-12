---
title: "Wifi password problem"
date: 2013-09-10
forum: New to Ubuntu
---

### Post by thebergekorey on 2013-09-10
Hey im new to linux and i just got it on my laptop and during the install the wifi worked fine but now it keeps asking for the wifi password over and over again i have looked everywere google, youtube and i tired following some forums but i really dont understand the terminal, please have step by step instructions my laptop is a toshiba c855-s5133 and the wifi card is a Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

thanks

---

### Post by claracc on 2013-09-10
Perhaps your problem is related with this bug?: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/854833](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/854833)

---

### Post by PopsTheSailor on 2013-09-10
I'm not sure why you are referring to terminal. Is it a window that pops up asking for your password? My router password in on the bottom of my router. I have to do this so often that I have it memorized (sigh). I feel for you. I have the same wifi card and it stinks. I have intermittent problems with it all the time. My laptop is coming to its end of life so when I get a new one, I plan on getting one that doesn't use Realtek adapters.

---

### Post by grahammechanical on 2013-09-10
Once you make a wireless connection to the router/hub Network Manager should remember the authentication password-phrase-wireless key, whatever it is called. It is really simple and does not require use of the terminal. Click on the Network icon in the top panel. Select your Wireless access point and enter the passphrase when asked to do so. Network Manager will work out and set the encryption method.

From the Network Manager menu you can select Edit Connections. Then select your wireless connection and select Edit and under the General tab make sure that there is a tick mark against Automatically connect to this Network when it is available.

You can also get to these settings through System Settings>Network.

I am assuming that you are using Ubuuntu 13.04.

Regards.

---

### Post by thebergekorey on 2013-09-10
Thanks everyone for your replies im sorry if i wasnt clear but what its doing is it will attempt to connect to my wifi(which ubuntu 13.04 can detect my router) then itll ask for me to put in the password which i know is right and all my other devices in my home are connected to my network. Then after about 10 seconds ubuntu will ask for me to enter the password again i can connect with a ethernet cable

---

### Post by varunendra on 2013-09-10
> **thebergekorey said:**
> Thanks everyone for your replies im sorry if i wasnt clear but what its doing is it will attempt to connect to my wifi(which ubuntu 13.04 can detect my router) then itll ask for me to put in the password which i know is right and all my other devices in my home are connected to my network. Then after about 10 seconds ubuntu will ask for me to enter the password again i can connect with a ethernet cable

Welcome to the forums thebergekorey !

First, just to rule out the obvious, please try saving the correct passkey and encryption type in Network Manager for your connection *(NM applet drop-down menu > Edit Connections... > Wireless tab > double-click your connection > Wireless Security tab)*. Additionally, you may try adding your access-point's MAC address in the "BSSID" field under "Wireless" tab in the same setting box. Save and close it, then try to re-connect and see if it helps.

If it doesn't, please follow the "Wireless Script" link in my signature, follow the instructions in the linked post and post back the diagnostics report that the script generates. First we'll try to make the defaults work, if they don't we may try a couple of other drivers, including a newer opensource one, or a proprietary one.

---

### Post by thebergekorey on 2013-09-10
Sweet I'm now connected to my wifi. Adding my AP MAC address in the "BSSID" field worked! Thank you everyone! The only problem I see with this solution is that every time I'm traveling and I need wifi I'll need to MAC address of the hardware.

---

### Post by varunendra on 2013-09-10
> **thebergekorey said:**
> Thank you everyone! The only problem I see with this solution is that every time I'm traveling and I need wifi I'll need to MAC address of the hardware.
..which you can get with the command -
```
nm-tool
```
or a detailed info with -
```
sudo iwlist scan
```

But you shouldn't need this solution everywhere. I believe this workaround is needed only with few problematic access-points.

If you find the solution satisfactory enough, please consider marking it [SOLVED]. It helps others with similar problems by indicating that the thread contains a possible solution to their problem.

Thanks for your cooperation and feedback ! :)

---

