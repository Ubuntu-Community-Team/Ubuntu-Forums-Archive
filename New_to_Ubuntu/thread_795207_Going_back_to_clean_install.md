---
title: "Going back to clean install"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by docamo on 2008-05-15
Ok, this is a problem that I have been trying to figure out without success. I installed Hardy 8.04 and everything was fine. Compiz seemed to be working (I could get the extra visual effects to work) and I could use that fireworks screen saver. Either I did something or something changed after a restart because after two days of everything going fine, the visual effects got turned off and I have been unable to get them back since.

I have looked at the install cd and when I boot from that, everything on the cd works like it did after I first installed it. After looking at different threads which I am unsure apply to me, I have tried a few several things from using the terminal to uninstall and reinstall compiz to the synaptic package manager uninstall and reinstall of compiz/intel drivers...

However, I think I may have dug myself into a hole and not more things don't work, like Amarok and dvd support (I tried reinstalling lots of stuff). So I think I need to take things back to how they were without wiping out all my data (email specifically, I had just resorted all my mail into folders.)

Is there a way to take everything back to how it was after I first installed Ubuntu?

When I run terminal and type $ sudo lspci i get
> 00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation 82915G Integrated Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
03:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)

when I input $ compiz
> Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2582 (rev 04) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

Can someone please tell me where I am going wrong?

---

### Post by cmnorton on 2008-05-15
You are not alone. I had KUbuntu 8.04 running nearly fine, and then performed an update and Firefox and Evolution (both Gnome?) would not run. I performed back-grade to 7.10.

As to going back to when you just installed 8.04, I know of know way to to this accurately, unless you imaged the disk right after the install. Given you have updated or installed using the official tools and then things went wrong, why would you want to be on 8.04 if this has happened?

Going back to a more stable release makes sense.for now. If the 8.04 release were to do this a few months from now, I'd have to consider using another distro, because neither my equipment nor my configurations are way out of the norm.

---

### Post by docamo on 2008-05-15
> **cmnorton said:**
> You are not alone. I had KUbuntu 8.04 running nearly fine, and then performed an update and Firefox and Evolution (both Gnome?) would not run. I performed back-grade to 7.10.

I've seen many people mention they are running 7.10 as well. I never had 7.10 to begin with. I'm coming over from XP. Am I able to back-grade to 7.10 if I never had it to begin with and can it be done without loosing my data?

---

### Post by cmnorton on 2008-05-15
You need to backup anything important. In my case, I needed to backup anything important in /home, and take configuration notes. 

It does not sound like you need to take notes on special tweaks that had to be made to 7.10 to get CDs playing on a Thinkpad T61, fixed in 8.04 by the way, or special sendmail configuration changes.

Download the 7.10 torrrent. The following page has everything listed.

[http://releases.ubuntu.com/7.10](http://releases.ubuntu.com/7.10)

A lot of people have had success downloading an iso directly. I haven't and use torrents. Bittorrent is easy to get for Windows. You should also be able to find it for Linux. If this is a laptop, suggest that you save yourself some grief and try the alternate install. "alternate" is in the file name.

Burn the CD or DVD. I've never worried about burn speed. If you are unsure about your "burner", the select the verify option.

---

### Post by billgoldberg on 2008-05-15
It seems it can't find "xgl", did you try to re-install it?

---

### Post by docamo on 2008-05-15
> **billgoldberg said:**
> It seems it can't find "xgl", did you try to re-install it?

I don't think so. How would you do that?

---

### Post by docamo on 2008-05-18
So because I have an Intel 910 chipset I installed the patch from [http://ubuntuforums.org/showthread.php?t=766381](http://ubuntuforums.org/showthread.php?t=766381)

This seems to have helped some. However I am still having difficulties with the direct rendering.

```
mole03@mole03-desktop:~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
```

and

```
mole03@mole03-desktop:~$ skip_checks=yes compiz 
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
```
```
mole03@mole03-desktop:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
```
Any help?

---

### Post by docamo on 2008-05-18
I Did It! Hahaha!! All I Had To Do Was Take Out Xserv After Installing The Patch!! Everything Works!!

---

