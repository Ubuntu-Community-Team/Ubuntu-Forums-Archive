---
title: "[SOLVED] Can not get Wireless internet to work"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by swaj38812 on 2008-07-16
I have an HP pavillion notebook dv6119us. I am running Ubuntu 8.04 and everything is working flawlessly even the internet when plugging directly into the router. The laptop has a wireless lan button on the front and a light to indicate whether or not it is enabled. When running xp it is in the on position and the light id blue indicating it is working. In ubuntu the button is in the on position and the light is orange indicating that the wireless lan is not working. I have tried to figure out how to turn it on I have used commands from the help menu and it says its disabled but have no clue how to enable it of course there is nothing in the help menus to instruct you on how to turn it on. If someone could help me I am absulutely new to linux but really want to learn. I greatly appreciate your help in advance. Thanks

---

### Post by Sealbhach on 2008-07-17
Type

```
iwconfig 
```

in the terminal and paste the results here.


.

---

### Post by swaj38812 on 2008-07-17
This is what it gave me when I typed the iwconfig comand





lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by swaj38812 on 2008-07-17
Sealbhach I greatly appreciate the help you may be able to offer I am at work today till 6 am on friday at the fire station so I will try and respond asap in between calls thanks for your help.

---

### Post by swaj38812 on 2008-07-17
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Sealbhach on 2008-07-17
> **swaj38812 said:**
> Sealbhach I greatly appreciate the help you may be able to offer I am at work today till 6 am on friday at the fire station so I will try and respond asap in between calls thanks for your help.

Hi,

I don't know a lot about this but these commands will provide information about you wireless network setup: 


```
lshw -C network
```

```
iwlist scan
``` 

Please paste the output in your next messsage.

Hopefully someone else can troubleshoot the rest for you.


Also, you mught find someone with a similar problem in this thread.. [url]

http://ubuntuforums.org/forumdisplay.php?f=336[/url]


.

---

### Post by Kevbert on 2008-07-17
It looks like you need to install some firmware on your PC.  If you go to /lib/firmware you should have some files ending in .fw  If not that's your problem and the output from the commands will help to identify how you need to proceed.

---

### Post by framinglory on 2008-07-17
I too, use an hp laptop with a similar kill switch for the wireless. Just to let you know, the light may not ever come on as blue to indicate it is on. Ubuntu does not seem to turn the light blue to indicate that the wireless card is on, but as long as the switch is in the on position, the physical connections for the wireless card and all will be fine, and you can ignore the fact that there is an orange light and get the firmware drivers and such working that people mentioned above.

---

### Post by swaj38812 on 2008-07-17
This is what it gave me when entering the comand lshw -c network






Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

---

### Post by swaj38812 on 2008-07-17
This is what I got when I typed the command iwlist scan



alo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

---

### Post by swaj38812 on 2008-07-17
Thanks guys I will go check the firmware i am at work with only wireless so I am having to go back and forth between xp and ubuntu. I greatly appreciate the help!!!

---

### Post by swaj38812 on 2008-07-17
I tried the command /lib/firmware and it says this is a directory but nothing else. not sure if there is a command i need to type before that or not. Is there a linux for dummies?? He He Thanks again for the help

---

### Post by Sealbhach on 2008-07-17
> **swaj38812 said:**
> This is what it gave me when entering the comand lshw -c network



That needs to be a capital C

```
lshw -C network
```

This should help identify what firmware or drivers you need.


.

---

### Post by Sealbhach on 2008-07-17
> **swaj38812 said:**
> I tried the command /lib/firmware and it says this is a directory but nothing else. not sure if there is a command i need to type before that or not. Is there a linux for dummies?? He He Thanks again for the help

You can go into it through Nautilus, your file manager and look at it visually.

Just go Places/Computer/File System/lib/Firmware/2.6.24.19/...and finally you get to the folder you need.

Or try typing this in the terminal:
```

ls /lib/firmware/2.6.24-19-generic
```

.

---

### Post by khayden39005 on 2008-07-17
im following this as well. i have a hp dv9428 w/ a broadcom 4311 rev 02. i followed these directions ([http://ubuntuforums.org/showthread.p...=broadcom+4311](http://ubuntuforums.org/showthread.p...=broadcom+4311)) step by step and the wireless light came on,but my wireless is not recognized. ive had more or less the same responses to all attempts made by the two of you. the last line, ls /lib/firmware/2.6.24-19-generic, outputs, ls: cannot access /lib/firmware/2.6.24-19-generic: No such file or directory
. what is my next step? by the way i am running ubustu hardy heron.

---

### Post by swaj38812 on 2008-07-17
Alright I think I got the info that is needed this is what I got when typing the command lshw -C network with a capitol C HE HE

WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:ee:25:22
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by swaj38812 on 2008-07-17
This is what I got for the firmware


acx                                 dvb-usb-vp7045-01.fw
aic94xx-seq.fw                      dvb-usb-wt220u-02.fw
atmel_at76c502_3com.bin             dvb-usb-wt220u-fc03.fw
atmel_at76c502_3com-wpa.bin         dvb-usb-wt220u-zl0353-01.fw
atmel_at76c502.bin                  ipw2100-1.3.fw
atmel_at76c502d.bin                 ipw2100-1.3-i.fw
atmel_at76c502d-wpa.bin             ipw2100-1.3-p.fw
atmel_at76c502e.bin                 ipw2200-bss.fw
atmel_at76c502e-wpa.bin             ipw2200-ibss.fw
atmel_at76c502-wpa.bin              ipw2200-sniffer.fw
atmel_at76c503-i3861.bin            isl3877
atmel_at76c503-i3863.bin            isl3886
atmel_at76c503-rfmd-0.90.2-140.bin  isl3887usb_bare
atmel_at76c503-rfmd-acc.bin         isl3890
atmel_at76c503-rfmd.bin             isl3890usb
atmel_at76c504_2958-wpa.bin         iwlwifi-3945-1.ucode
atmel_at76c504a_2958-wpa.bin        iwlwifi-3945.ucode
atmel_at76c504.bin                  iwlwifi-4965-1.ucode
atmel_at76c504c-wpa.bin             iwlwifi-4965.ucode
atmel_at76c505a-rfmd2958.bin        ql2100_fw.bin
atmel_at76c505-rfmd2958.bin         ql2200_fw.bin
atmel_at76c505-rfmd.bin             ql2300_fw.bin
atmel_at76c506.bin                  ql2322_fw.bin
atmel_at76c506-wpa.bin              ql2400_fw.bin
dvb-fe-or51132-qam.fw               rt2561.bin
dvb-fe-or51132-vsb.fw               rt2561s.bin
dvb-fe-or51211.fw                   rt2661.bin
dvb-fe-tda10046.fw                  rt73.bin
dvb-ttpci-01.fw                     v4l-cx2341x-dec.fw
dvb-usb-avertv-a800-02.fw           v4l-cx2341x-enc.fw
dvb-usb-bluebird-01.fw              v4l-cx2341x-init.mpg
dvb-usb-dib0700-1.10.fw             v4l-cx25840.fw
dvb-usb-dibusb-5.0.0.11.fw          v4l-pvrusb2-24xxx-01.fw
dvb-usb-dibusb-6.0.0.8.fw           v4l-pvrusb2-29xxx-01.fw
dvb-usb-dtt200u-01.fw               zd1201-ap.fw
dvb-usb-tvwalkert.fw                zd1201.fw
dvb-usb-umt-010-02.fw               zd1211
dvb-usb-vp702x-01.fw

Not sure what all this means but there it is.

---

### Post by Kevbert on 2008-07-18
Hi.  Thanks for the message.  Looking at the previous posts you do not have the wireless firmware files installed.  Your wireless in a Broadcom BCM94311MCG wlan mini-PCI Rev 01.  There's a [[COLOR="Red"]good guide here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=769990").  If you have any problems please do not hesitate to ask.

---

### Post by swaj38812 on 2008-07-18
You guys are great that fixed it the lil blue light came on and I am responding on the wireless now! I thank you so much for taking the time to read this follow up and give me the help I needed.

---

### Post by Sealbhach on 2008-07-18
That's great news!

It would help others if you select Thread Tools and mark this thread as solved.


.

---

