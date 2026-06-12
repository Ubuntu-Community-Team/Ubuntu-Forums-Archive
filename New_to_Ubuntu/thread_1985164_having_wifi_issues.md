---
title: "having wifi issues"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by sly4tehwin on 2012-05-22
i recently installed xubuntu 11.10. this is my first experience with an ubuntu and ive run into a slight problem. i cant get the wifi to work. i feel silly even asking for help with this but im a complete ubuntu noob and dont know where else to look. any help or suggestions would be greatly appreciated.

---

### Post by carl4926 on 2012-05-22
Open a terminal and post the result of

```
lspci -nnk
```

---

### Post by sly4tehwin on 2012-05-22
sly4tehwin@ubuntu:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
    Subsystem: Dell Inspiron 1420 [1028:01f3]
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c)
    Subsystem: Dell Inspiron 1420 [1028:01f3]
    Kernel driver in use: i915
    Kernel modules: intelfb, i915
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 0c)
    Subsystem: Dell Dell Inspiron 1420 [1028:01f3]
00:1a.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
    Subsystem: Dell Inspiron 1420 [1028:01f3]
    Kernel driver in use: uhci_hcd
00:1a.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
    Subsystem: Dell Inspiron 1420 [1028:01f3]
    Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
    Subsystem: Dell Inspiron 1420 [1028:01f3]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
    Subsystem: Dell Inspiron 1420 [1028:01f3]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
    Subsystem: Dell Inspiron 1420 [1028:01f3]
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
    Subsystem: Dell Inspiron 1420 [1028:01f3]
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
    Subsystem: Dell Inspiron 1420 [1028:01f3]
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
    Subsystem: Dell Inspiron 1420 [1028:01f3]
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
    Subsystem: Dell Inspiron 1420 [1028:01f3]
    Kernel modules: iTCO_wdt
00:1f.1 IDE interface [0101]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
    Subsystem: Dell Inspiron 1420 [1028:01f3]
    Kernel driver in use: ata_piix
00:1f.2 SATA controller [0106]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] [8086:2829] (rev 02)
    Subsystem: Dell Device [1028:01f3]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
    Subsystem: Dell Inspiron 1420 [1028:01f3]
    Kernel modules: i2c-i801
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
    Subsystem: Dell Inspiron 1420 [1028:01f3]
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
    Subsystem: Dell Inspiron 1420 [1028:01f3]
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
    Subsystem: Dell Inspiron 1420 [1028:01f3]
    Kernel driver in use: r592
    Kernel modules: r592
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
    Subsystem: Dell Inspiron 1420 [1028:01f3]
    Kernel driver in use: r852
    Kernel modules: r852
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
    Subsystem: Dell Inspiron 1420 [1028:01f3]
    Kernel driver in use: tg3
    Kernel modules: tg3
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel modules: wl, ssb
sly4tehwin@ubuntu:~$

---

### Post by carl4926 on 2012-05-22
This is your wireless device
```
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel modules: wl, ssb
```

I take it you ran the offer of addition drivers that would probably have been offered for you?
Your device should work perfectly and it looks like the proprietary broadcom driver is in place.
Don't you see any access points offered?
Is your system fully updated? (Have you rebooted)

FYI: I have a very similar device but I don't use the driver Ubuntu throws at you. But that's just me. And what you have should work.

---

### Post by sly4tehwin on 2012-05-22
yes I installed the driver that was suggested and I also rebooted. I will try to reboot again and see what i can do. I know I have wifi available because I am connected to it with another laptop. I really appreciate you looking thorough all that! at least now I know nothing is terribly wrong lol

---

### Post by sly4tehwin on 2012-05-22
also when I go to try and look for an access point it doesn't show that any are available. even though i know that there is.

---

### Post by carl4926 on 2012-05-22
Post the result of this

```
cat /etc/modprobe.d/blacklist.conf
```

---

### Post by sly4tehwin on 2012-05-23
sly4tehwin@ubuntu:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
sly4tehwin@ubuntu:~$

---

### Post by carl4926 on 2012-05-23
Please copy and paste this with your mouse in to a terminal

```
echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist
```

see if it helps

---

### Post by synapsys on 2012-05-23
Open up a terminal and run 

```
ifconfig
```

Does wlan0 show up? If not, run this

```
ifconfig wlan0 up
```

then run this one again

```
ifconfig
```

and see if wlan0 shows up.

As a side note, have you checked to make sure the "enable wireless" checkbox is checked in the network manager?

---

### Post by sly4tehwin on 2012-05-23
i put that is and still no dice

---

### Post by carl4926 on 2012-05-23
now try

```
sudo modprobe wl
```

---

### Post by sly4tehwin on 2012-05-23
synapsys : i did as you said and when i put in "ifconfig wlan0 up" i got this "wlan0: ERROR while getting interface flags: No such device"

---

### Post by sly4tehwin on 2012-05-23
carl: still nothing. what was that ment to do?

---

### Post by carl4926 on 2012-05-23
Make sure you have any wireless switches on your machine switched ON too

---

### Post by carl4926 on 2012-05-23
> **sly4tehwin said:**
> carl: still nothing. what was that ment to do?
module loading of the wl driver

---

### Post by carl4926 on 2012-05-23
Darn, I hate these proprietary drivers being forced on us.

Make a mental note for if you install 12.04, not to accept the additional wireless driver. And just ask about installing the b43 driver.

---

### Post by sly4tehwin on 2012-05-23
i believe it may have something to do with my wireless switch. this machine is new to me and i thought i had it switched on. but after takein a closer look i dont think that my wireless sweitch works at all. im still stying to find another way to turn on the wireless on a dell inspiron 1420 without useing the switch.

---

### Post by carl4926 on 2012-05-23
Is it a physical switch or a Fn combo?

Does your machine have a cd drive? We could try something...

---

### Post by sly4tehwin on 2012-05-23
its a physical switch and there is no fn combo that i can see 
[http://en.community.dell.com/support-forums/network-internet-wireless/f/3324/p/18752641/18875627.aspx](http://en.community.dell.com/support-forums/network-internet-wireless/f/3324/p/18752641/18875627.aspx) that is the switch

and yes i do have a cd drive. what are you thinking?

---

### Post by carl4926 on 2012-05-23
I'm going to PM you a file. Save it to a pen drive or something.

Then boot the Xubuntu cd
Open the file manager 
put the folder you extract from what I PM you in the location the file manager opens.
Now open a terminal and do

```
sudo mv b43 /lib/firmware
```

The wireless should come to life within a minute

---

### Post by sly4tehwin on 2012-05-23
boot the xbuntu cd? can you please clarify?

---

### Post by carl4926 on 2012-05-23
Boot it to a live desktop

---

### Post by sly4tehwin on 2012-05-23
? i still dont understnd :/

---

### Post by carl4926 on 2012-05-23
You can boot the cd and try xubuntu
just as if it was installed

just forget your actual installation for the moment

I want you to test the live cd and see if the b43 driver will work there

---

### Post by sly4tehwin on 2012-05-23
ok so restart and boot from my install cd? where do you want me to but that driver? or do i do something with it after i boot from the disk?

---

### Post by carl4926 on 2012-05-23
Yes

I told you. Copy the folder to the place where the file manager opens

then open a terminal and do

```
sudo mv b43 /lib/firmware
```

the wireless should become active soon after doing that

---

### Post by sly4tehwin on 2012-05-23
im sorry, i still cant figure out what you mean. you have been so patient with me and i appreciate it a lot. do you think you could walk me through what you're talking about?

---

### Post by sly4tehwin on 2012-05-23
i feel like this would be way easier if you could see what i see lol

---

### Post by carl4926 on 2012-05-23
OK

SO you have a xubuntu cd,
If you were planning to do a install, most people boot the cd and try it in what is called live mode, that is you get a real desktop but it's running from the cd. I want you to boot your cd as if you were just trying it in live mode. If you wanted to install it from there you will see there is a Install icon to click. So hopefully you understand I want you to boot the cd to a live desktop.

Now, I sent you a .zip archive which contains the folder b43
Which hopefully you have on a flash drive that you can connect to the laptop.
We need to copy that to the live session /home
So open the place where your b43 folder is, right click and copy. Now close that and from the menu open the file manager, and in the window right click and paste - this should copy over b43 folder

Now open a terminal and do

```
sudo mv b43 /lib/firmware
```
This will move the folder b43 to the live systems /lib/firmware
And you wireless should come to life

---

### Post by sly4tehwin on 2012-05-23
ok now I understand. also i think i get what you are trying to do. 

heres the problem now, the disk i have doesn't give me the option to try without installing. I cant find anything of that nature when i boot the disk.

---

### Post by carl4926 on 2012-05-23
When you boot the cd try pressing Esc, see if you get to the language option and then on to the choice for try or install

Maybe you have the alternate cd?

Could you download a new cd? Perhaps 12.04

---

### Post by sly4tehwin on 2012-05-23
yeah it dosent give me the option with my disk.

i think i will go and download the new version like you suggested and try booting in live mode off of that. from that new version i will follow the same steps correct?

i think i understand what you are trying to do.

---

### Post by carl4926 on 2012-05-23
> **sly4tehwin said:**
> yeah it dosent give me the option with my disk.

i think i will go and download the new version like you suggested and try booting in live mode off of that. from that new version i will follow the same steps correct?

i think i understand what you are trying to do.

correct

good

be patient if I'm not around 24/7

---

### Post by sly4tehwin on 2012-05-23
thank you so very much for all of your help! i leaned some stuff too!
im going to tackle this tomorrow and post my results on this thread. thank you again for everything

---

### Post by carl4926 on 2012-05-23
> **sly4tehwin said:**
> thank you so very much for all of your help! i leaned some stuff too!
im going to tackle this tomorrow and post my results on this thread. thank you again for everything
You are most welcome

---

### Post by sly4tehwin on 2012-05-23
i went ahead and booted ubuntu from a disk and did as you said. it gave me the option to enable the wireless but i still cant see any available networks. 
also the wireless indicator on the laptop does not show that the wifi is even turned on. im not sure what to do with this.

---

### Post by carl4926 on 2012-05-24
Go back to your installed system
Make sure rfkill is installed and do

```
rfkill list all
```Post result

---

### Post by josephmills on 2012-05-24
I wrote a little thing about this here 
[http://ubuntuforums.org/showthread.php?p=10796508](http://ubuntuforums.org/showthread.php?p=10796508)

Hope this helps

---

