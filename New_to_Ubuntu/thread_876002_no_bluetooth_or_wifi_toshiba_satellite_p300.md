---
title: "no bluetooth or wifi toshiba satellite p300"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by dodge78 on 2008-07-31
Hi,

I don't know if this is the right place for this thread, but I'm in need of some help, I can't get the bluetooth or wifi to work on this satellite p300 (pretty sure US equivalent is an A300). I currently have Ubuntu 8.04 64 bit "linux-headers-2.6.24-19-generic"

I have been searching all over the net for 4 days now, but nothing really helpful. I have even tried the how to from here:

[http://ubuntuforums.org/showthread.php?t=316358&highlight=toshiba+satellite+bluetooth](http://ubuntuforums.org/showthread.php?t=316358&highlight=toshiba+satellite+bluetooth)

```

abcd@1234-laptop:/proc/omnibook$ ls
dmi  version

```

lspci:
```
abcd@1234-laptop:/proc/omnibook$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4355 (rev 12)
0a:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
```

and as you can see i have no bluetooth or wifi controllers detected

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:1e:68:35:40:49  
          inet addr:192.168.2.7  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe35:4049/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:58128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:70360769 (67.1 MB)  TX bytes:4117746 (3.9 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1370 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1370 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:68500 (66.8 KB)  TX bytes:68500 (66.8 KB)

```

I am some what of a beginner with Linux, so please give simple instructions if possible.:confused:

---

### Post by dodge78 on 2008-08-01
well i got the wifi to work now via this link:

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b]("https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b")

I would like to thank the author of the above "How To"

now the only thing that doesn't work is the bluetooth, if any one can give a hand your help will be truly appreciated.

thanks in advance

---

### Post by scotcella on 2008-08-01
I got my bluetooth working after a lot of cussing and cursing...

my issue was solved by downgrading the blue utiliz package to v3.19.

[http://technology-included.blogspot....buntu-804.html](http://technology-included.blogspot....buntu-804.html)

The link shows how you can do it.

---

### Post by kw0me on 2008-08-01
i had the same trouble with bluetooth on mine (satellite a200) i dual boot vista and linux. i found if i booted windows then turned the wireless switch off then restarted in linux and once loaded turned the switch back on and it worked perfectly. But when going back to windows you have to right click the bluetooth tray app and turn bluetooth radio off then back on to get it working in windows again. hope that helps :)

---

### Post by Tom--d on 2008-08-01
Try using my How to below. 

It uses the Windows Diver. A lot more stable than the buggy linux driver for the wireless card.

---

### Post by dodge78 on 2008-08-01
> **scotcella said:**
> I got my bluetooth working after a lot of cussing and cursing...

my issue was solved by downgrading the blue utiliz package to v3.19.

[http://technology-included.blogspot....buntu-804.html](http://technology-included.blogspot....buntu-804.html)

The link shows how you can do it.

Ok, well i downgraded the blue util and still not working. I tried to detected my laptop with both my phones (nokia 6131 and a HTC touch cruise), still no luck they both can't see the laptop. When i try from the laptop hcitool scan i get the below.
```

laptop:~$ hcitool scan
Device is not available: No such device
```

I don't know what to do, maybe its the phones. I'm going to try my wife's nokia N95 when she gets back home in a little while.

If you or any one has any advise, other than throwing this thing out the window, I'm almost willing to try any thing.

---

### Post by scotcella on 2008-08-04
Hi there,

Sorry I forgot to check back, but had a flat out weekend.

Okay, lets eliminate a few things first; 

You probably have already done some of these things, but I'm just eliminating somethings on the top of my head that I learnt the hard way!!

1. Have you switched on bluetooth thingy, on both your computer and your mobile?

2. When you force a downgrade, the update manager will detect that you have an old package and that there is an update available. Make sure you don't upgrade bluetooth, and always untick the boxes when you install updates relating to bluetooth, at least for now.

4. Make sure you have installed the gnome-bluetooth package as well. You can get this via the synapotic manager easily.

5. To set up your preferences, right click the Bluetooth icon and select "Preferences", then ensure the following:

1) On the first Tab, ensure "Mode of operation" is "Visible and connectable for other devices"
2) Your phone appears in "Bonded devices" at the bottom, and is trusted. (Lock and Star icon)
3) In the "General" tab, "Receive files from remote devices" is enabled
4) "Automatically authorise incoming requests" is enabled (checked).

To send files to your computer, you need to select the file to send in the phone and then search for available devices. If you have already paired your phone to the laptop and if you have saved it, it should also show up under My Devices in your phone.

Select your computer and then your laptop should receive the file.

6. Did you restart your computer/laptop? After a lot of cussing and cursing, I restarted and lo behold it was working, so it might do the trick.

Post back if it works or not..   we'll work it out.

Edited to add: 
I have a Nokia N95 so it should definately work, so try your wife's mobile and see if it works then work your way over to using your mobiles. :o)

It took me a while to understand all these simple instructions, and when the light bulb moment came- everything fell into place! I usually leave it for a while and get back to my issues. :o)

---

### Post by dodge78 on 2008-08-31
Hi There,

Sorry for the late replay, but I've been out of town and extremely busy. At any rate, I've tried what you suggested but still no go. And since I need the blue tooth to work, and I need to use both XP and Linux, i put XP and am running Ubuntu in VM.

I truly appreciate all the help you have given.
Thank you

---

