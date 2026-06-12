---
title: "Broadcom B43 wireless configuration problems"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by hnarwan on 2008-10-10
Hi Guys,

I've just installed my first Linux distro...Kubuntu 8.04 on my Dell Inspiron 1300. Everything works except wireless internet (which i see is a common problem).

I go into Hardware drivers and see the Broadcom B43 wireless driver has been recognised as its listed (it also has a status of 'In Use' and the Enabled column has a black check mark. 

In Network interfaces i see both the Ethernet interface (eth0) and Wireless interface (WLAN0) listed. The Ethernet adaptor allows me to access my internet via cable but the wireless adaptor does not get assigned an ip address even though i've configured my ESSID and my WEP key. Both interfaces are showing as enabled in network settings too but as soon as I unplug my network cable and need to the wireless connection to kick in i'm unable to access the internet as it wont connect.

Does anyone have any suggestions?

thanks
Hardeep

---

### Post by nickpaton on 2008-10-10
Welcome to Ubuntu and the forums!

In a Terminal (Applications > Accessories > Terminal)  can you post the output of

```
iwconfig
```

Also 

```
lspci
```

---

### Post by shifty_powers on 2008-10-10
heh, yeah post the output of that.

i am finding that kubuntu's network manager is pretty damn poor with the broadcom chips.

if the adapter is working from the command line, then you can change the network managers to gnome's or wicd...

---

### Post by hnarwan on 2008-10-10
Thanks Nick and Shifty for your poasts.

As requested heres the output you asked for:

hardeep@uklap1:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




hardeep@uklap1:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I guess this means Kubuntu has picked up the wirless card but its not associated to an access point?

As i say i've configured the interface with my SSId and WEP key but still no joy.

Any further assistance you guys could give would e be much appreciated.

thanks again
Hardeep

---

### Post by Scott-271 on 2008-10-10
Howdy Hnarwan,

Welcome to Linux/*buntu!!!!

Here are a few links that may help you out:

[http://ubuntuforums.org/showthread.php?t=870086&highlight=bcm4318]("http://ubuntuforums.org/showthread.php?t=870086&highlight=bcm4318")

[http://ubuntuforums.org/showthread.php?t=766560&highlight=bcm4318]("http://ubuntuforums.org/showthread.php?t=766560&highlight=bcm4318")

I have the same chipset as you bcm4318, and the second link is the one I used; it worked like a charm.

Scott

---

### Post by shifty_powers on 2008-10-10
ok, whats the output of

```
sudo iwlist scan
```
?

---

### Post by hnarwan on 2008-10-11
Hi Shifty, 

[sudo] password for hardeep:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:11:50:C6:EC:B8
                    ESSID:"belkin"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/100  Signal level=-83 dBm  Noise level=-73 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000136e6950bd


Scott thanks very much for your post, i'll give it a go and get back to you guys as soon as i can.

thanks
Hardeep

---

### Post by hnarwan on 2008-10-11
Hi Scott, 

Thanks again for your reply. Unfortunatly i'm hitting a snag when trying to complete the instructions from the link from one of your pages: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

Step 1: All BCM43xx - Install NDISWrapper and Blacklist Native Driver
echo -e 'blacklist bcm43xx\nblacklist wl' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx

This completes fine...


Step 2 Driver download/Extraction <for Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)>
sudo apt-get install cabextract 
wget [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe) 
cabextract sp34152.exe

Although sp34152.exe appears to have downloaded successfully after the 'wget' command when I try to cabextract I get an error telling me no valid cabinets are found....i assume I've screwed up somewhere along the way?

hardeep@uklap1:~/bcm43xx$ wget [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)
--07:50:31--  [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)
           => `sp34152.exe.1'
Resolving ftp.compaq.com... 161.114.23.171
Connecting to ftp.compaq.com|161.114.23.171|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/softpaq/sp34001-34500 ... done.
==> PASV ... done.    ==> RETR sp34152.exe ... done.

    [                        <=>          ] 4,494,456     18.71K/s

07:54:48 (17.26 KB/s) - `sp34152.exe.1' saved [4494456]

hardeep@uklap1:~/bcm43xx$ cabextract sp34152.exe
sp34152.exe: no valid cabinets found

All done, errors in processing 1 file(s)
hardeep@uklap1:~/bcm43xx$       

Scott do you have any ideas on this?

thanks
Hardeep

---

### Post by shifty_powers on 2008-10-11
well it seems that your network card is finding and scanning networks ok. as i said, in my experience, the kde network manager can be cack with broadcom chips.

you might want to use wicd instead of knetwork manager. it's what i used and it worked perfectly.

if you do want to follow these instructions.

```
gksudo kate /etc/apt/sources.list
```

and add

```
deb http://apt.wicd.net hardy extras
```

to the end of the file. save and close kate.

then

```
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
```
```
sudo apt-get update && sudo apt-get install wicd
```

this will remove knetwork manager and install wicd. you'll need to restart afterwards. hopefully you'll then be able to use your wireless...

---

### Post by hnarwan on 2008-10-11
Hi Shifty,

I followed your instructions but even after the restart the wireless connection isnt working (and now the ethernet connection is also down).

Any ideas?

thanks
Hardeep

---

### Post by Sava8420 on 2008-10-11
Hey there man like you have heard prior wireless can be tricky in *buntu but you have came to the right place to ultimately solve the problem.  So I don't know where you are in the process as of right now but as you've been told the network manager is pretty worthless.  So here is a link to go through as for configuring connection from the terminal for any encryption type plus alot more useful commands for config and troubleshooting.   [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by Scott-271 on 2008-10-11
The file you need to get, using cabextract, is *bcmwl5.inf*. You can probably find it using Google; I also sent you a pm concerning it. Once you have that file, you can just continue with the guide after the *cabextarct* part.

Scott

---

### Post by REDace0 on 2008-10-11
I've got the exact same chipset and GNOME's Network Manager (package nm-applet) worked fine with the B43 driver that Hardy fetches. If you can't get any of the above sophisticated solutions to work, since it seems kde's network manager is different, you could give nm-applet a try.

I'm still pretty new, so someone please correct me if I'm off here.

Good luck!

---

### Post by hnarwan on 2008-10-11
Hi Guys, 

Thanks so much for all your posts...

Looks like removing knetwork manager and installing wicd from Shifty did the trick. I just went into the wicd utility and my wireless connection was listed.

The only remaining problem is that i had to remove wireless security from my router because when i tried to connect in wicd i get a message stating this connection is encrypted. I couldnt see anywhere to enter my WEP key so i'm not sure how to get around this.

thanks again fellas.

thanks
Hardeep

---

