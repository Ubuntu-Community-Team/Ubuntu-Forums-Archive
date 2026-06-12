---
title: "Mouse pointer and wireless card problems"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by number7 on 2008-07-22
Hello
I have just installed ubuntu 8.04, its my first go at linux and have two problems, probably more I dont know yet.
1)The mouse on my dell latitude c510 seems to float around not in my controll.
2) I cant get the wireless pccard to work even following  a how to file. Is there a way in ubuntu to see what devices you have installed and what drivers are installed.
Any help appreciated
Thanks
number7

---

### Post by northern lights on 2008-07-22
Can you post the output of ```
sudo lshw -C network
```

As for the mouse, do you have the package "xserver-xorg-input-synaptics" installed?

If not, run ```
sudo apt-get install xserver-xorg-input-synaptics
```

Also run "sudo apt-get install gsynaptics" and tinker with the settings in gsynaptics.

---

### Post by number7 on 2008-07-23
northern lights m8, where do I find sudo. Is it like command line in windows. Sorry but I am learning from dos,win3.1,95,98,2000,me.xp and it is different.

---

### Post by northern lights on 2008-07-23
mkey.

Start a terminal (konsole in KDE). There should be an entry in your "applications" menu. If not, hit "Alt+F2" and enter "gnome-terminal".

Paste the the first line from the last post into the terminal (keyboard shortcut "Shift+Ctrl+V"), hit enter. There's some detail on your network devices. Copy it here ("Edit" menu or "Shift+Ctrl+C").

Run ```
aptitude search xserver-xorg-input-synaptics
``` the same way and see whether there's an "i" flag next to "xserver-xorg-input-synaptics" (to the left). If not run, ```
sudo apt-get install xserver-xorg-input-synaptics
```

---

### Post by number7 on 2008-07-23
*-network
          description: Wireless interface
          product: AR5212/AR5213 Multiprotocol MAC/baseband processor
          vendor: Atheros Communications Inc.
          physical id: 1
          bus info: pci@0000:07:00.0
          logical name: wifi0
          version: 01
          serial: 00:0f:3d:84:ad:0c
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list logical ethernet physical wireless
          configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

Is this what you want for the wireless card

sudo for the mouse pointer downloaded one thing and it seems to have done it. Thank you if it has and if not I may be back.

Ubuntu is getting much more interesting

---

### Post by northern lights on 2008-07-23
Crap. The Atheros AR5212/AR5213 is seriously troublesome and seems to fail to work often.

What happens if you run ```
sudo ifconfig eth0 down

sudo ifconfig ath0 up

iwlist scan
```

---

### Post by number7 on 2008-07-23
it stops the internet working on the ethernet connection so I have to reboot the laptop. Is there a way to repair the ethernet connection, if so I can copy what sudo says with command :sudo ifconfig eth0 down

sudo ifconfig ath0 up

iwlist scan

---

### Post by northern lights on 2008-07-23
Of course it'll stop the internet connection. You don't have to reboot, though, to get it back.

```
sudo ifconfig eth0 down

```
disables the ethernet interface, replacing down by up respectively enables it again.

```
iwlist scan
```scans for wireless networks in range. What does it return?

Can you also run```
aptitude search linux-restricted-modules madwifi-tools 
``` and check "linux-restricted-modules" and "madwifi-tools" are installed?

---

### Post by match002001 on 2008-07-23
Atheros is a pain in the butt, I had to use ndiswrapper in order to get it to install and run properly. 

Click on Applications at the top and click on Add/Remove.

Select All on the left side and then search for ndiswrapper.

Once it pops up on the right side place a check in it and that will install it.

After install go find the Windows driver for that card and make sure that the .inf file is available.

next open the terminal (similar to DOS prompt) and enter this:

```
sudo ndiswrapper -i PATH TO .INF FILE
```

You can then verify that it was installed by typing:

```
ndiswrapper -l
```

At which point if it shows up then enter:

```
modprobe wlan0
```

Then Set it up by going to Settings, Prefrances, and Network to setup your wireless network.


This is what i had to do anyways i hope it helps you out.

-Match

---

### Post by number7 on 2008-07-23
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:1B:2F:EC:12:12
                    ESSID:""
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-74 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101800003a4000027a4000042435e0062322f00

---

### Post by number7 on 2008-07-23
I have the installation disk that came with the wireless card but I think its only for windows, can I use it

---

### Post by northern lights on 2008-07-23
> **number7 said:**
> I have the installation disk that came with the wireless card but I think its only for windows, can I use it

You can use the windows driver with "ndiswrapper". Refer to match's post.

---

### Post by match002001 on 2008-07-23
look on the disk and you should have a dedicated folder for WindowsXP or Vista, make sure it is 64 bit or 32 bit. 

look in that folder for the INF file and that is all you need. then follow the instructions i posted on page 1

---

### Post by number7 on 2008-07-24
Im going round in circles now. The atheros driver seems to be installed and the synaptics driver but wireless network doesnt work yet.
How do I show a list of all devices on the laptop.

---

### Post by northern lights on 2008-07-24
> **number7 said:**
> the atheros driver seems to be installed
That it was from the very beginning. Check
> **number7 said:**
> *-network
          description: Wireless interface
          product: AR5212/AR5213 Multiprotocol MAC/baseband processor
          vendor: Atheros Communications Inc.
          physical id: 1
          bus info: pci@0000:07:00.0
          logical name: wifi0
          version: 01
          serial: 00:0f:3d:84:ad:0c
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list logical ethernet physical wireless
          configuration: broadcast=yes [COLOR="Red"]driver=ath_pci[/COLOR] latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

Is this what you want for the wireless card

sudo for the mouse pointer downloaded one thing and it seems to have done it. Thank you if it has and if not I may be back.

Ubuntu is getting much more interesting





> **number7 said:**
> How do I show a list of all devices on the laptop?
```
sudo lshw
```



Could you please report back after having tried "ndiswrapper"? I've got another guy with a very similar issue...

---

### Post by northern lights on 2008-07-24
Okay. Try this:

Edit "/etc/network/interfaces"
```
sudo gedit /etc/network/interfaces
```
Delete most, leave only the loopback interfaces lo (the first 2 lines). They should look like this
```
auto lo
iface to inet loopback
```
save and close the file.

Run
```
sudo /etc/init.d/networking restart
```

Check the network manager and try to connect to a wireless network.

If it fails first try, reboot and try again.

---

### Post by number7 on 2008-07-25
Still no wireless network

---

### Post by northern lights on 2008-07-25
At the end of my wits, sorry.

Post further developments should they change the situation, yet not fix it completely - maybe then you and me will figure it out.

Otherwise bump once in a while and hope for more expertise.

Over & out.

---

### Post by number7 on 2008-07-26
Thanks for your help

---

### Post by northern lights on 2008-07-26
One more idea to get some more expert advice -

Post a new thread concerning the wireless issues only in the "Networking & Wireless" forum. Post the latest "lshw -C network" right away and describe you're problem and what you've tried so far...

---

