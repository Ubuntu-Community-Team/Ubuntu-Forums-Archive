---
title: "Problem with media players that use GStreamer."
date: 2008-06-09
forum: New to Ubuntu
---

### Post by MillDaKill on 2008-06-09
I have been having a very odd problem with media players that make use of GStreamer such as Rythmbox, totem and Songbird.  As soon as I log in everything works fine, but anywhere from 20 mins to an hour later the GStreamer based players will no longer play any of my files.  If I log out of my gnome session and log back in everything will work for another 20 mins to an hour.  Players like VLC will work fine while the GStreamer players are not functioning.

Specs.
8.04 64bit ubuntu desktop
Athlon 3200+ 64bit
1 gig ram


lspci output.
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
00:0c.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a2)

---

### Post by MillDaKill on 2008-06-09
bump

---

### Post by RomeReactor on 2008-06-09
Hi. Try launching Rhythmbox from the terminal (Applications->Accessories->Terminal) and start playing an audio file; when the problem occurs again, see if there's any output in the terminal that might indicate what the problem is and post that here so we can take a look at it.

Do you open other applications after Rhythmbox that might want to use the soundcard--like Firefox with a YouTube video?

---

### Post by MillDaKill on 2008-06-09
> **RomeReactor said:**
> Hi. Try launching Rhythmbox from the terminal (Applications->Accessories->Terminal) and start playing an audio file; when the problem occurs again, see if there's any output in the terminal that might indicate what the problem is and post that here so we can take a look at it.

Do you open other applications after Rhythmbox that might want to use the soundcard--like Firefox with a YouTube video?

matt@mattDesktop:~$ rhythmbox
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

<This entry appears when I try to play something>
(rhythmbox:18899): Rhythmbox-WARNING **: Unhandled error: Unknown playback error
</This entry appears when I try to play something>

I do have firefox open usually and I do check out youtube videos from time to time.

---

### Post by RomeReactor on 2008-06-09
Looks like it could be related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/80383"), which first appeared in Edgy.

Does this happen whether Firefox is open or not? Have you tried reinstalling the Gstreamer libraries?

```
sudo aptitude reinstall gstreamer0.10-alsa gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-x
```

or reinstalling Rhythmbox, Totem or Songbird?

---

