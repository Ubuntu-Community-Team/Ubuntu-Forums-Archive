---
title: "[Solved] Lubuntu 16.04 - restart and shutdown dont work"
date: 2016-10-04
forum: New to Ubuntu
---

### Post by johnstons on 2016-10-04
Hi,
I am a Linux beginner who switched from Mint to Lubuntu. Even if it is not that pretty I really like it :)
Almost everything works fine. Almost... I cant restart or shutdown. Have googled this problem and saw that many have this bug. To be honest I dont want to try all 100 possibile solutions for this bug and end up with a crashed Lubuntu because I have no idea what i am doing,
Can anybody please help me? Without shutdown/restart I cant use Lubuntu properly ;(

```
System:    Host: Aspire-E3-112 Kernel: 4.4.0-38-generic x86_64 (64 bit gcc: 5.4.0)           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 16.04 xenial
Machine:   System: Acer product: Aspire E3-112 v: V1.10
           Mobo: Acer model: R2 v: Type2 - A01 Board Version
           Bios: Insyde v: V1.10 date: 08/20/2014
CPU:       Dual core Intel Celeron N2840 (-MCP-) cache: 1024 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 8652
           clock speeds: max: 2582 MHz 1: 1301 MHz 2: 647 MHz
Graphics:  Card: Intel Atom Processor Z36xxx/Z37xxx Series Graphics & Display
           bus-ID: 00:02.0
           Display Server: X.Org 1.18.3 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.11hz
           GLX Renderer: Mesa DRI Intel Bay Trail
           GLX Version: 3.0 Mesa 11.2.0 Direct Rendering: Yes
Audio:     Card Intel Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.4.0-38-generic
Network:   Card-1: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter
           driver: ath9k bus-ID: 02:00.0
           IF: wlp2s0 state: up mac: <filter>
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: 1000 bus-ID: 03:00.0
           IF: enp3s0 state: down mac: <filter>
Drives:    HDD Total Size: 504.2GB (73.2% used)
           ID-1: /dev/sda model: ST500LT012 size: 500.1GB temp: 26C
           ID-2: USB /dev/sdb model: Flash_Disk size: 4.1GB temp: 0C
Partition: ID-1: / size: 457G used: 339G (79%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 2.03GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 45.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 160 Uptime: 14 min Memory: 1061.3/1885.9MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.3.461) inxi: 2.2.35 



```

Thank you!

---

### Post by #&amp;thj^% on 2016-10-04
Dose this do anything?
In terminal run:
```
sudo  shutdown  -P  now

```
-P  Requests that the system be powered off after it has been brought down.

From the MAN PAGES:

> Shutdown - "shutdown arranges for the system to be brought down in a safe way. All logged-in users are notified that the system is going down and, within the last five minutes of TIME, new logins are prevented." Time mentioned here is an amount specify by the user that is shutting down.
-r  Requests that the system be rebooted after it has been brought down
-h  Requests that the system be either halted or powered off after it has been brought down, with the choice as to which left up to the system
-H  Requests that the system be halted after it has been brought down
-P  Requests that the system be powered off after it has been brought down
-c  Cancels a running shutdown. TIME is not specified with this option, the first argument is MESSAGE
-k  Only send out the warning messages and disable logins, do not actually bring the system down
Did Mint Shutdown and Reboot properly?

---

### Post by johnstons on 2016-10-05
Thanks for your help!
But this doesnt work - it freezes at a screen like this:
[http://landoflinux.com/images/lubuntu_lxle_12.png](http://landoflinux.com/images/lubuntu_lxle_12.png)

---

### Post by colmax on 2016-10-05
maybe try in terminal (ctrl+alt+t) to invoke terminal
shutdown -r now
for reboot
or
shutdown -h now
to halt the system
cheers

---

### Post by johnstons on 2016-10-05
Doesnt work neither :(
On Mint I can remeber I had this problem also with some releases. But cant remeber what I did.

---

### Post by Rex Bouwense on 2016-10-05
There is the old standby when everything else fails.  Instead of mashing down on the power button which is never a good idea.
Hold down the Alt and SysRq (Print Screen) keys.
While holding those down, type the following in order. Nothing will appear to happen until the last letter is pressed: REISUB
Watch your computer reboot magically.

---

### Post by #&amp;thj^% on 2016-10-05
> **johnstons said:**
> Thanks for your help!
But this doesnt work - it freezes at a screen like this:
[http://landoflinux.com/images/lubuntu_lxle_12.png](http://landoflinux.com/images/lubuntu_lxle_12.png)
Ok this worked for me when that happened...but your mileage may vary. (So make sure you have backup's in place)

You will need to edit your "/etc/default/grub" file
I made the following changes to my grub file:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic irqpoll"
```
Then update grub
```
sudo update-grub
```
Now if it dose not reboot after this you will have to power it down the way you have been doing (Although that is not safe or recommended)
**I make no Promise this will work for you**...so make sure you have a good back-up in place.

---

### Post by johnstons on 2016-10-05
> **Rex Bouwense said:**
> There is the old standby when everything else fails.  Instead of mashing down on the power button which is never a good idea.
Hold down the Alt and SysRq (Print Screen) keys.
While holding those down, type the following in order. Nothing will appear to happen until the last letter is pressed: REISUB
Watch your computer reboot magically.

This works! 
But I would rather prefer a magic trick for shutdown :)
@1fallen: Thanks but sounds quite "risky", isnt it? Is there no easier possibility?

---

### Post by #&amp;thj^% on 2016-10-05
As I said it worked for my Acer 5750
And you can always... with the Live Installer you used to do your install with... re-edit back to what you had.
If I had an easier suggestion I surely would have offered that first.:D
Besides Back-ups are just a must have. (Old Wisdom here)

---

### Post by johnstons on 2016-10-05
Yes I know - on my netbook is nothing that it is not backuped somewhere else. But before risking to crush my system I hope someone has a easier possibility. If no one can help - I will attack my grub file :)
I read that disabling USB 3.0 in BIOS worked for some people - unfortunately I dont have this choice :(

---

### Post by johnstons on 2016-10-08
Has really no one any ideas how to fix?

---

### Post by nginmu on 2016-10-10
I noticed this happening on my new install of Lubuntu 16.04.1 - the problem seemed to disappear after I'd run sudo apt-get update and the software updater had popped up & done it's stuff. Hope it doesn't reappear..

No solution for you I'm afraid but I did notice, when it froze at the screen like you posted earlier in the thread, if I pressed the esc key the screen would change from the blank screen with Lubuntu logo, to a terminal style listing of what the system had been doing in the final few moments, terminating in a line something like 'reached system shutdown' or 'arrived at module shutdown' or something along those lines. It looked like it had hung immediately after that line.

I noticed that not only the esc key would toggle back and forth between logo screen and listing, many other keys would do it too like the function keys etc.

---

### Post by johnstons on 2016-10-10
Ok thanks! I will try this. If it fails i will try updating my grub file. How do I do this? Entering the 2 lines in the console?
If my system crushes I will try Fedora :)

---

### Post by #&amp;thj^% on 2016-10-11
> **johnstons said:**
>  If it fails i will try updating my grub file. How do I do this? Entering the 2 lines in the console?

If you are still wondering how to edit your grub file.
Open your fovorite text editor with elevated privliages IE:
```
sudo -H leafpad /etc/default/grub
```
Find the line that looks like the below...and copy and paste what you had before the change and save it like on thumb drive or any other external media.(this way you will have a copy of the oringinal text)
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet
```
Now change that to look exactly like this. (And Save and Close)
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic irqpoll"
```
Now tell grub about the change made with,
```
sudo update-grub
```
Now reboot...and this may not take effect til after you have booted up with a fresh grub change.
Regards

---

### Post by johnstons on 2016-10-13
Thank you very much - yes I was still wondering.
Unfortunatelly it didnt solve my problem :(

Tried Fedora 24 - same problem. Maybe this bug referes to LXDE or 64bit. Or Maybe my Acer. Same bug on several distros.

---

### Post by mörgæs on 2016-10-14
Have you tried Lubuntu 16.10?

---

### Post by johnstons on 2016-10-14
Same bug on Lubuntu 16.10. But all others distros also fail, mostly ubuntu derivates. Seems really to be a Acer bug. No I am quite confused because I dont know how to handle this. Dont want to back to Windows :D

---

### Post by mörgæs on 2016-10-14
If you see it on many distros then a BIOS update is worth considering.

---

### Post by johnstons on 2016-10-14
How do I do this? First I go back to Lubuntu 16.04 and try this: [http://askubuntu.com/questions/524894/boot-and-shutdown-issues-on-aspire-e-11-model-e3-111-c0wa](http://askubuntu.com/questions/524894/boot-and-shutdown-issues-on-aspire-e-11-model-e3-111-c0wa)

---

### Post by #&amp;thj^% on 2016-10-14
> **johnstons said:**
> How do I do this? First I go back to Lubuntu 16.04 and try this: [http://askubuntu.com/questions/524894/boot-and-shutdown-issues-on-aspire-e-11-model-e3-111-c0wa](http://askubuntu.com/questions/524894/boot-and-shutdown-issues-on-aspire-e-11-model-e3-111-c0wa)

I think there might be a big enough difference between your model Acer and the one you are trying to follow on Ask Ubuntu.
Lets take a look at that file first.
```
leafpad /etc/modprobe.d/blacklist.conf
```
And maybe there won't be anything listed there...but copy and paste the content of this file (if there is anything) back here using code tags.

---

### Post by johnstons on 2016-10-15
Thanks for your help! With one distro failed to go to standby I got some error message which said something with dw_dmac...

```
# This file lists those modules which we don't want to be loaded by# alias expansion, usually so some other driver will be loaded for the
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



```

---

### Post by mörgæs on 2016-10-18
If you want to upgrade the BIOS then you could try to download the BIOS executable, create a bootable USB stick with Freedos and copy the executable to the stick. Now boot from it.

---

### Post by johnstons on 2016-10-18
Seems to be easy. But as I go on a long travel in some days I think I wait until my return :)
Could anyone please tell me step by step (or better with copy/paste) how to do this? [http://askubuntu.com/questions/524894/boot-and-shutdown-issues-on-aspire-e-11-model-e3-111-c0wa](http://askubuntu.com/questions/524894/boot-and-shutdown-issues-on-aspire-e-11-model-e3-111-c0wa)

Thank you!

---

### Post by johnstons on 2016-10-28
No one? I would be really glad if someone could help me step by step how to blacklist dw_dmac. Dont want to make an misstake there...

---

### Post by mörgæs on 2016-10-28
I don't think it can be explained otherwise than in the link you posted. Edit the file using sudo rights and add the two *blacklist* statements to the end.

If it fails you can just remove them again.

---

### Post by johnstons on 2016-10-28
Expected something like
```
sudo leafpad ...
```

I didnt know that I have to type leafpad in command line.
Anyway, didnt solve my problem :(

---

### Post by johnstons on 2016-10-29
I think i solved the problem in earlier times with switching in BIOS from Legacy to UEFI like mentioned in some Forums. I installed Lubuntu again - now I cant boot anymore. "No bootable device" . :confused:

edit: no idea what I did but this solved my problem: [http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi)

---

