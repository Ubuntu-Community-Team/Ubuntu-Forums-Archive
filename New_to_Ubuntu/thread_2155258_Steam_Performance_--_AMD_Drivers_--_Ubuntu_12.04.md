---
title: "Steam Performance -- AMD Drivers -- Ubuntu 12.04"
date: 2013-06-17
forum: New to Ubuntu
---

### Post by Gnawnsense on 2013-06-17
Greetings,

So I've recently decided to migrate completely over from Windows 8 to Ubuntu 12.04 for the sake of the LTS. Mind you, I have zero real experience with Linux before this, and am switching due to a friend informing me something about, "strides being made in the way of proprietary software coming to it" and "better driver support" and all these other exciting things. So, needless to say, after reading about all the PRISM nonsense, I figured I might as well give it a shot. And that's what I've been doing, and I've loved it so far. But on to my problems and the resulting question I have for all the gurus out there..

During use of the Live CD, everything went absolutely wonderful. Once the installation was completed and I was prompted to reboot, things started looking like they could get complicated in a hurry when I booted up initially after install and my screen did not but flash a purple screen off and on. A quick Google turned up that I could but into Recovery Mode and restore a broken package to hopefully fix the issue, which seemed a little too good to be true, but it worked. And voila, I had an Ubuntu desktop in native resolution and everything seemed to be going a-OK!

After going through my new desktop, I received a popup indicating software updates were available. After completing these, I rebooted and was informed that there were additional drivers available for my graphics card, which is a **Radeon HD 6800**. I know, I know, everyone has better luck with Nvidia drivers and Linux, but don't blame the purchaser for faults pre-linux, I suppose. Anyways, I noticed on the list of available drivers there were three choices, which from my previous quick (and I mean quick) goes at Ubuntu, I was used to two. So I read the descriptions for the three and chose the one on the list that was titled *"ATI/AMD proprietary FGLRX graphics driver (post-release updates)"*.

I activated and installed the drivers, rebooted, and still had my display when I came back (which just for the record, is where things completely broke and I went back to Windows on all my previous Linux efforts years ago). Everything looked to be fine, so I was excited and installed Steam immediately to test these bad boys out. I downloaded Team Fortress 2 immediately, and upon launching the game, was swiftly told that my drivers were out of date. I ignored the warning and joined a server and was happy to see that upon first connecting, the graphics looked as good as they did on Windows. And then I spawned and saw the performance. The frames were smooth in general and not low, but there was an insane amount of random stuttering and input lag. I glanced over the settings and they were all on system recommended. 

So I closed out, went back to the additional drivers tool and selected another option on the tool, which had a much shorter name. I clicked on activate, and it installed the drivers. I rebooted, came back, still had display and went back into steam and Team Fortress 2 and.. was shocked to see I still had the exact same performance. 

I was dinking around later and went into Big Picture Mode and was informed that I only had 256mb of video ram available (my card has a gig), and I got concerned, looked at my additional drivers tool again, and noticed that the*"ATI FireGL"* driver that I'm currently using says* "This driver is activated but not currently in use"* which is an extremely confusing statement to me. Below is a screenshot of the current state of my drivers (to my knowledge), and what I am describing above:

[IMG]http://screencloud.net//img/screenshots/302f659cf43520bab850e7e0aad8f968.png[/IMG]


Before coming to the forums to try to seek assistance, I figured it might be as simple as no actual AMD driver being in use, and maybe a generic or something like that? So I went into terminal and checked the *flgrxinfo* and got the response below:

[IMG]http://screencloud.net//img/screenshots/88b7bbb6897fbf0475c9670dfbcd8bf9.png[/IMG]

Which, all I can see is that it's referring to an AMD driver or piece of hardware. What I can't tell is if a working driver is in use, or which one? I'm almost a bit concerned that the original driver I set to use (*"ATI/AMD proprietary FGLRX graphics driver (post-release updates)*) should of been deactivated somehow before attempting to activate a new one and maybe that caused some sort of conflict. 

Should I be concerned that the current driver I have selected says it's activated but not in use? Is the fact that I didn't deactivate the proprietary driver before selecting the current causing a conflict?

I'm sorry if I sound ignorant, but at this point, any help would be appreciated. I've managed to figure a few things out since switching manually, but when it comes to display drivers, I get worried because typically it can result it my screen going black during boot and refusing to show anything again. I'd like to prevent that if possible this time.

---

### Post by user_of_gnomes on 2013-06-17
What does ```
sudo lspci -v
``` tell you when it comes to driver in use for the videocard?

---

### Post by Gnawnsense on 2013-06-17
> **UbuntuRaptor said:**
> What does ```
sudo lspci -v
``` tell you when it comes to driver in use for the videocard?

There are a lot of entries there and I'm having a hard time sorting through the information to find which one is referring specifically to the driver in use for the graphics card. Let me know if below is what you were looking for.

```
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Barts PRO [ATI Radeon HD 6800 Series] (prog-if 00 [VGA controller])    
    Subsystem: ASUSTeK Computer Inc. Device 03aa
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at feae0000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at e000 [size=256]
    Expansion ROM at feac0000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150] Advanced Error Reporting
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx_experimental_12, radeon

```


Thanks!

---

### Post by deadflowr on 2013-06-17
Not sure how it works with the firegl drivers, but normally when I install fglrx drivers, I run
```
sudo amdconfig --initial
```

which creates an xorg file, and I think blacklists the radeon driver(not sure).

Again, not sure about the firegl drivers.

Look over this for anything that might help

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by QIII on 2013-06-17
Hello!

You don't want to be using the Fire GL driver.  You want fglrx.

Deactivate the Fire GL driver.

Is this an integrated or dedicated GPU?  Do you have both integrated and dedicated?

If you only have one (and not both), when you go to the URL cited (also find it in my signature), follow the directions in section "2.1. Installing via the command line"

Best wishes!

---

### Post by NikTh on 2013-06-17
The truth here is that I didn't read the full version of your first post. As I saw the picture, I remembered [this]("http://ubuntuforums.org/showthread.php?t=1829971") old post but seems has been returned (the problem). 

If you want to see what driver you use , apply the following command in terminal 
```
lspci -nnk | grep -iA2 vga
``` 
if you see **kernel driver in use: fglrx** , then the AMD driver is installed correctly and is in use. And simply ignore the Jockey's message. Also the above command will show if you have hybrid graphics or not. 

As for the performance in Steam.. well, do not expect much from AMD cards in Linux. (my opinion, based on the recently action of AMD to drop the support for 2xxx-4xxx cards in Linux). 

Regards
 NikTh

---

### Post by user_of_gnomes on 2013-06-17
> Kernel driver in use: fglrx_pci

I'd say that's the driver that's loaded. Did you have the beta drivers selected before?

At some point I switched from Radeon to Catalyst and then back again. That didn't take properly, I had to switch once more to Radeon using the additional drivers menu and *then* it worked. I probably should have handled that through the terminal but hey, it worked and still works.

---

### Post by Mark Phelps on 2013-06-17
My guess, since it does show that you are using the fglrx drivers, is that when you first installed the post-release drivers, that's when things got broken.  Those drivers nearly always fail or otherwise hose up your system.  Since you may have remnants of those lying around, I would use the link below to purge the fglrx drivers and start over again (using Qiii's suggestion):  [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")

---

### Post by Gnawnsense on 2013-06-17
> **UbuntuRaptor said:**
> I probably should have handled that through the terminal but hey, it worked and still works.

*ATI/AMD proprietary FGLRX graphics driver (post-release updates)* is what I was originally using.

> **NikTh said:**
> The truth here is that I didn't read the full version of your first post. As I saw the picture, I remembered [this]("http://ubuntuforums.org/showthread.php?t=1829971") old post but seems has been returned (the problem). 

If you want to see what driver you use , apply the following command in terminal 
```
lspci -nnk | grep -iA2 vga
``` 
if you see **kernel driver in use: fglrx** , then the AMD driver is installed correctly and is in use. And simply ignore the Jockey's message. Also the above command will show if you have hybrid graphics or not. 

When I run that command this is what I get: [B][I]Kernel driver in use: fglrx_pci

[/I][/B]> **QIII said:**
> Hello!

You don't want to be using the Fire GL driver. You want fglrx.

Deactivate the Fire GL driver.

Is this an integrated or dedicated GPU? Do you have both integrated and dedicated?

If you only have one (and not both), when you go to the URL cited (also find it in my signature), follow the directions in section "2.1. Installing via the command line"

Best wishes!

The AMD HD 6800 is a dedicated card. I do have an integrated, as well, that I do not use, so yes, I do have both integrated and dedicated cards.

If I deactivate the Fire GL driver, will there be anything I need to manually go in and remove/uninstall/purge?

---

### Post by Gnawnsense on 2013-06-17
Alright, I am currently in the process of purging my fglrx drivers.

When I go to start over on the drivers, with the link Qiii posted, does it matter which method I go about reacquiring the fglrx drivers? Ubuntu repositories, command line, AMD website?

---

### Post by QIII on 2013-06-17
If you have both an integrated and dedicated card, use your BIOS/EFI to be sure that the integrated GPU is deactivated.

You should be able to use the additional drivers GUI to simply deactivate the Fire GL driver.  The module is most not in your kernel at present.

If you follow either the directions Mark Phelps gave or those in the wiki I suggested, at one point you will have a clean system using the open source Radeon driver before moving on to installing the fglrx driver properly.

Using the GUI or the terminal will pull from the repo.  They are just different methods of doing the same thing.  With the terminal approach, you can be sure to get the fglrx rather than fglrx-updates.

I would recommend against going to the AMD website for the moment, since the driver in the repo works.

---

### Post by Gnawnsense on 2013-06-17
> **QIII said:**
> If you have both an integrated and dedicated card, use your BIOS/EFI to be sure that the integrated GPU is deactivated.

You should be able to use the additional drivers GUI to simply deactivate the Fire GL driver.  The module is most not in your kernel at present.

If you follow either the directions Mark Phelps gave or those in the wiki I suggested, at one point you will have a clean system using the open source Radeon driver before moving on to installing the fglrx driver properly.

Using the GUI or the terminal will pull from the repo.  They are just different methods of doing the same thing.  With the terminal approach, you can be sure to get the fglrx rather than fglrx-updates.

I would recommend against going to the AMD website for the moment, since the driver in the repo works.

I followed the directions in the link you provided in the wiki and purged the drivers. After doing that, I went into the additional drivers tool and selected the fglrx driver and went through the installation to where I was prompted to reboot the PC. I rebooted and came back to a display, but this is currently what the additional drivers tool says:

[IMG]http://screencloud.net//img/screenshots/a8390e6cae2990f775627c433038bb94.png[/IMG]

Basically, the same thing. That the driver is activated but not currently in use. Here is what my *lspci -v* brought up:

```
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Barts PRO [ATI Radeon HD 6800 Series] (prog-if 00 [VGA controller])    Subsystem: ASUSTeK Computer Inc. Device 03aa
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at feae0000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at e000 [size=256]
    Expansion ROM at feac0000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150] Advanced Error Reporting
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx_updates, radeon
```

So I'm assuming somewhere there is a random driver being used that was not purged that's causing all the drivers I activate to stay out of use?  I noticed the Kernel modules section changed between my two *lspci -v *posts, but I'm not sure that's really too relevant in the grand scheme of things or if it means anything significant.

---

### Post by QIII on 2013-06-17
OK.

Let's blacklist fglrx_pci and go through the process of purging/installing again.

You will need to purge fglrx-updates, and again I suggest installing fglrx rather than fglrx-updates.

```
 sudo echo "blacklist fglrx_pci" >> /etc/modprobe.d/blacklist-fglrx_pci.conf
```

If you get a permissions warning, we'll have to directly add the line.

---

### Post by Gnawnsense on 2013-06-17
> **QIII said:**
> 
If you get a permissions warning, we'll have to directly add the line.

I am inside the /etc/modprobe.d/ directory and do not see that specific file. Should I create it, or add this line that needs to be added to one of the existing files?

[IMG]http://screencloud.net//img/screenshots/b88f21ccb3994e6b8cf12ec3fb458fbc.png[/IMG]

---

### Post by QIII on 2013-06-17
Actually, let's not, I guess.  I was going to have you de-blacklist it in a bit anyway.

Could you post the results of 

```
lsmod
```

?

---

### Post by Gnawnsense on 2013-06-17
```
Module                  Size  Used by
rfcomm                 47562  0 
vesafb                 13846  1 
bnep                   18240  2 
bluetooth             211812  10 rfcomm,bnep
parport_pc             32867  0 
ppdev                  17114  0 
snd_hda_codec_hdmi     32476  1 
snd_hda_codec_realtek    79855  1 
snd_hda_intel          34063  7 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
kvm_amd                56136  0 
kvm                   422160  1 kvm_amd
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
fglrx                4715455  184 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse               102506  0 
snd                    83674  23 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
edac_core              53053  0 
soundcore              15092  1 snd
sp5100_tco             13792  0 
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
k10temp                13174  0 
serio_raw              13216  0 
dcdbas                 14491  0 
i2c_piix4              13302  0 
microcode              23030  0 
edac_mce_amd           23548  0 
amd_iommu_v2           19228  1 fglrx
mac_hid                13254  0 
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
usb_storage            49288  0 
hid_generic            12541  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid
tg3                   156646  0 
ahci                   25869  2 
libahci                27338  1 ahci
```

---

### Post by QIII on 2013-06-17
OK.

The fglrx module is loaded.

Blacklisting fglrx_pci would have kept it from loading, which might have been diagnostic, but is unnecessary from what I see now.

So we know that NikTh's suggestion to just ignore Jockey was right.  I'm going to see if there is a bug report like this on Launchpad.

I still recommend fglrx instead of fglrx-updates, as the latter is often problematic.  That may be what is causing this.

As for TF2, I'm not sure what sort of hardware acceleration it may require.  The ATi driver doesn't have as much to offer as NVIDIA, but there is some available.

If you look at the wiki, I've included a section on how to get some hardware acceleration.  That may or may not help your performance.

---

### Post by Gnawnsense on 2013-06-17
Thank you for the continued assistance. I can already imagine the performance issues then are caused by the lack of hardware acceleration. I assumed it was automatic. I'll go look at the wiki now and take a gander. 

As far as the driver issue, if you are confirming that the proper driver is currently in use, then I suppose this issue is closed.

---

### Post by Gnawnsense on 2013-06-17
Just enabled hardware acceleration and rebooted just because I felt like I needed to.

When I launched back into Ubuntu, I opened up Steam and got the out-of-date driver message. I'm assuming this is the message everyone said to ignore? 

[IMG]http://screencloud.net//img/screenshots/8d7fd2365f55d8a2f1f0416cdba0f8e4.png[/IMG]

However, now when I go to launch any game that I have currently installed, it prepares to launch, I get the black full-screen like the game process is loading to my monitor, and then it disappears and I'm back to my desktop. So it's like the game launches and closes immediately. But, it's only for Source Engine games. Killing Floor will load and play perfectly now. But Team Fortress 2, Counter-Strike Source, Half-Life 2, and Left4Dead 2, all do the immediate open and close.

**Edit:** Found a YouTube video of another user suffering the exact same problem with the Source games launching and closing immediately: [http://www.youtube.com/watch?feature=player_embedded&v=BSO7TAVleb0](http://www.youtube.com/watch?feature=player_embedded&v=BSO7TAVleb0)

---

### Post by Gnawnsense on 2013-06-17
I opened up terminal and entered in just *'"steam"* in to try and see if I could log what was happening in terminal when I clicked on one of the games that would not launch now.

```
steamRunning Steam on ubuntu 12.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1370553818_client)
Installing breakpad exception handler for appid(steam)/version(1370553818_client)
Installing breakpad exception handler for appid(steam)/version(1370553818_client)
unlinked 0 orphaned pipes
Installing breakpad exception handler for appid(steam)/version(1370553818_client)
[0617/155039:WARNING:proxy_service.cc(646)] PAC support disabled because there is no system implementation
Installing breakpad exception handler for appid(steam)/version(1370553818_client)
Installing breakpad exception handler for appid(steam)/version(1370553818_client)
Installing breakpad exception handler for appid(steam)/version(1370553818_client)


(steam:2294): GLib-GIO-WARNING **: g_simple_async_result_complete() called from wrong context!
Installing breakpad exception handler for appid(steam)/version(1370553818_client)
Generating new string page texture 7: 128x256, total string texture memory is 131.07 KB
Generating new string page texture 8: 64x256, total string texture memory is 196.61 KB
Generating new string page texture 9: 48x256, total string texture memory is 245.76 KB
Generating new string page texture 10: 256x256, total string texture memory is 507.90 KB
Generating new string page texture 11: 16x256, total string texture memory is 524.29 KB
Generating new string page texture 12: 24x256, total string texture memory is 548.86 KB
Generating new string page texture 13: 32x256, total string texture memory is 581.63 KB
Process 2294 created /ricky-ValveIPCSharedObjects3
Installing breakpad exception handler for appid(steam)/version(1370553818_client)
Installing breakpad exception handler for appid(steam)/version(1370553818_client)
Installing breakpad exception handler for appid(steam)/version(1370553818_client)
roaming config store loaded successfully - 2811 bytes.
migrating temporary roaming config store
`menu_proxy_module_load': /home/ricky/.local/share/Steam/ubuntu12_32/steam: undefined symbol: menu_proxy_module_load


(steam:2294): Gtk-WARNING **: Failed to load type module: (null)




(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.
Installing breakpad exception handler for appid(steam)/version(1370553818_client)
Adding license for package 0
Adding license for package 1
Adding license for package 9
Adding license for package 469
Adding license for package 969
Adding license for package 1495
Adding license for package 1559
Adding license for package 1565
Adding license for package 1579
Adding license for package 1679
Adding license for package 1886
Adding license for package 1943
Adding license for package 2481
Adding license for package 2630
Adding license for package 4155
Adding license for package 4315
Adding license for package 8183
Adding license for package 8709
Adding license for package 11858
Adding license for package 13054
Adding license for package 14186
Adding license for package 16863
Adding license for package 17644
Adding license for package 28305
Installing breakpad exception handler for appid(steam)/version(1370553818_client)
ExecCommandLine: "/home/ricky/.local/share/Steam/ubuntu12_32/steam"
Generating new string page texture 82: 128x256, total string texture memory is 131.07 KB


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:2294): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.
Installing breakpad exception handler for appid(steam)/version(1370553818_client)
System startup time: 18.65 seconds
Generating new string page texture 112: 256x256, total string texture memory is 843.78 KB
Generating new string page texture 113: 128x256, total string texture memory is 974.85 KB
Generating new string page texture 114: 384x256, total string texture memory is 1.37 MB
Generating new string page texture 115: 128x256, total string texture memory is 1.50 MB
Game update: AppID 440 "Team Fortress 2", ProcID 2679, IP 0.0.0.0:0
ERROR: ld.so: object 'gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded: ignored.
SDL video target is 'x11'
SDL video target is 'x11'
Installing breakpad exception handler for appid(gameoverlayui)/version(20130606134858_client)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0_client)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0_client)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0_client)
[0617/155100:WARNING:proxy_service.cc(646)] PAC support disabled because there is no system implementation
Running Steam on ubuntu 12.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/ricky/.local/share/Steam/ubuntu12_32/steam-runtime
ExecCommandLine: "/home/ricky/.steam/root/ubuntu12_32/steam steam://open/driverhelperready"
Using breakpad crash handler
ExecSteamURL: "steam://open/driverhelperready"
Generating new string page texture 146: 1024x256, total string texture memory is 2.55 MB
Setting breakpad minidump AppID = 440
Forcing breakpad minidump interfaces to load
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561197965825470 [API loaded yes]
Steam_SetMinidumpSteamID:  Setting Steam ID:  76561197965825470
Did not detect any valid joysticks.
[0617/155105:ERROR:resource_bundle.cc(411)] Failed to load /home/ricky/.local/share/Steam/SteamApps/common/Team Fortress 2/cef_gtk.pak
Some features may not be available.
[0617/155105:WARNING:proxy_service.cc(646)] PAC support disabled because there is no system implementation
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20130617155105_1.dmp
/home/ricky/.local/share/Steam/SteamApps/common/Team Fortress 2/hl2.sh: line 67:  2683 Segmentation fault      (core dumped) ${GAME_DEBUGGER} "${GAMEROOT}"/${GAMEEXE} "$@"
Game removed: AppID 440 "Team Fortress 2", ProcID 2683 
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-aabaffaa-df52-4a8b-b61f-7ea2b2130617
Generating new string page texture 138: 256x256, total string texture memory is 2.81 MB

```

---

### Post by user_of_gnomes on 2013-06-17
> 
As for TF2, I'm not sure what sort of hardware acceleration it may require. The ATi driver doesn't have as much to offer as NVIDIA, but there is some available.

I run Garry's Mod natively with Radeon drivers on my HD5770 and it runs pretty well. Highest settings @ 1280x1024
Also ran it through Wine with the highest settings

Performance isn't as high as it is under Windows but it's quite do-able.

Why not give the Radeon drivers a shot as well? Just make sure you get the ATI power profile extension if you're using Gnome.

---

### Post by Gnawnsense on 2013-06-17
[IMG]http://screencloud.net//img/screenshots/f446deba66f1d00b6b7d849f4648bdf1.png[/IMG]

Alright guys, it looks like I was able to completely get this situated, and boy, am I a HAPPY camper!

I'm assuming the Source Engine just absolutely did not like the "updates" drivers that I had selected because I went back to the additional drivers tool, selected the "experimental" and installed it. When I restarted, I was able to launch all my games again and they are actually playing with the graphics completely maxed and running perfect, without a flaw. Actually running better than my Windows 8 install! I just wish I would of known that hardware acceleration was installed separately from drivers.

I am so super excited right now to be using an AMD driver, doing minimal work, and being able to play my Steam games on Ubuntu even better than my Windows install. My gosh. Thank you everyone!

For anyone in the future, all that was needed to be done here was:

[LIST]
[*]Purging leftovers and yuckies from previous driver installations for safety.
[*]Using the additional drivers tool to select the AMD experimental driver.
[*]Installing the hardware acceleration via steps provided on the Wiki.
[/LIST]

Please consider this thread and issue completely solved.

---

### Post by NikTh on 2013-06-18
> **Gnawnsense said:**
> 
Please consider this thread and issue completely solved.

[s]Please mark the thread as solved. Take a look at my signature on How To.. [/s]

Also it would be better to change the title of this thread in something like.. **"Steam performance - AMD driver - Ubuntu 12.04" **

Glad you solved it, my next suggestion would be exactly this.. to purge everything and install the experimental driver from a terminal. 

Regards
 NikTh

---

