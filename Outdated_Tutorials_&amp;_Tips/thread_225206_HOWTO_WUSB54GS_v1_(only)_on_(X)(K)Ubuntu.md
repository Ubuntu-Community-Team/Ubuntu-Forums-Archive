---
title: "HOWTO: WUSB54GS v1 (only?) on (X)(K?)Ubuntu"
date: 2006-07-29
forum: Outdated Tutorials &amp; Tips
---

### Post by javaJake on 2006-07-29
**_[SIZE="4"]Ubuntu 8.10 (Intrepid) Deprecates This HOWTO![/SIZE]_**
That's right! This HOWTO is officially deprecated as of Ubuntu Intrepid. ndiswrapper is no longer needed. As soon as you plug in the WUSB54GS while running Ubuntu Intrepid, it should immediately function!

_**[SIZE="4"]No Longer Maintained![/SIZE]**_
I can no longer maintain this HOWTO, as the WUSB54GS adapter I used kicked the bucket. It was slowly dying over time, and I'm pretty sure it's due to the faulty laptop I was using it on (which has also killed a hard-drive).

The HOWTO will remain here. If someone wants to take over, PM me and I'll send you the source to this HOWTO. I'll also link to your HOWTO thread when you've recreated it.

If anyone wants to notify me of additional steps that have to be completed or no longer need to be included for future versions of Ubuntu, I'll write those in.

**_Some Random Notes You Should Read**_
Don't go looking through this thread's posts unless you really want to. I've compiled all good suggestions, troubleshooting, error fixing, etc, into this HOWTO for your convenience. If you have any problems partway through, the best idea is to quickly look at the "Troubleshooting" section at the bottom of the HOWTO, and *then* post your question, along with /var/log/syslog output.

For ease-of-use, I've attached a compressed file that contains everything you need for this HOW-TO, which includes drivers.

**_First things First - Some Requirements/Recommendations_**
[LIST]
[*]This HOWTO has been confirmed to run on Ubuntu Dapper, Edgy, Feisty, and Gutsy. It should continue to function as long as ndiswrapper is supported in Ubuntu (i.e. forever).
[*]In fact, this should work in just about any Linux OS, but no guarantees beyond Ubuntu! Steps like step 1 may require a little research to figure out on other distributions.
[*]Remove any remains of any past versions of ndiswrapper. If you've really mashed your system trying to get this to work, a complete reinstall is highly recommended, since ndiswrapper's pieces and configurations are probably scattered throughout your system. _If you installed using apt-get_, then run "apt-get remove ndiswrapper-utils". _If you compiled ndiswrapper_, and installed it, then open a terminal, go into the directory where you ran "make" in the first place, and run "sudo make uninstall". _If you used Synaptic Package Manager_, find ndiswrapper-utils in Synaptic, right click it, and click on "Mark for COMPLETE Removal". Basically, use the reverse of the method you used to install ndiswrapper in the first place.
[*]This tutorial will only work with WUSB54GS **v1**, **v2**. (WUSB54GS v2.1 *may* or may *not* require different instructions, which can be found [here]("http://www.jooz.net/rndis/"). I've heard it works when this HOWTO doesn't.) If you get any other versions to work, then please let me know, along with any unique steps. However, keep in mind that the WUSB54GS is the only device I will support, since it is the only one I have.
[*]This tutorial **doesn't support 64-bit processors**. Not sure why, but the drivers don't seem to work, even the 64-bit ones.
[*]It's a good idea not to plug in the device 'till I say to do so in the tutorial.
[*]**You do not have to know how to use a terminal**, though knowledge beforehand might help. I guide you through step-by-step, so you shouldn't feel lost.
[*]This HOWTO requires some sort of internet access. The computer you're installing the WUSB54GS device at doesn't need internet, but you need internet somewhere to initially download some things.
[*]If you really really need help, and just can't get this to work, contact one of my IM accounts listed in my profile. I am usually on weekends, Eastern Time, usually, though I cannot guarantee that.[/LIST]

**_Step 1 - Install the essentials_**
If you've never used "make" or compiled something, then you probably don't have the necessary tools to get through this HOWTO. Thankfully, you can easily install them. Run the following command to be sure everything is ready.

```
sudo apt-get install cpp gcc build-essential linux-headers-$(uname -r)
```

If you are not online, apt-get will ask for the disk. Insert your install CD into the drive and hit the ENTER key.

**_Step 2 - Downloading necessary packages_**
First, get ndiswrapper from [SourceForge](http://sourceforge.net/project/showfiles.php?group_id=93482). (Be sure to hit the Download button next to stable, not testing).
[img]http://eagleswingscoop.org/junk/wusb54gs/2-1.png[/img]
[img]http://eagleswingscoop.org/junk/wusb54gs/2-2.png[/img]

Next, download the drivers. I've included them in the attachment (at the bottom) for convenience, and it's best if you get them there. Whatever you do, do not download the drivers from the Linksys CD or anywhere else besides Linksys.com or the attachment I've provided. Many problems are a result of corrupted or invalid drivers, even from the manufacturer CD itself.

[INDENT]**Advanced users:** If you decide you want to use your own set of drivers instead of the ones provided in the attachment, make sure you get the following files. You'll find the .sys files in a Windows XP 32-bit install. (Do not use Vista!)
[list][*]rndismp.sys[*]usb8023.sys[*]WUSB54GS.inf[/list]
If you are using a WUSB54GSv2 device, you'll want to use "wusb54gsv2.inf" instead of "WUSB54GS.inf".[/INDENT]

Once you've collected these necessities, get them on the computer you want to install on. This is all the downloading you'll have to do from here on.

**_Step 3 - Build ndiswrapper_**
Right click on the ndiswrapper archive and click "Extract Here". You'll see a folder appear.
[img]http://eagleswingscoop.org/junk/wusb54gs/3-1.png[/img]
[(click here to see what the new folder looks like.)](http://eagleswingscoop.org/junk/wusb54gs/3-2.png)

Now, get out a paper and pen, or open a text editor. You'll need to write down where exactly this folder is. Right-click the folder that appeared and click Properties. A new window appears. Note the location and the name of the folder.
[img]http://eagleswingscoop.org/junk/wusb54gs/3-3.png[/img]

Once you've got all this, you can open a terminal. Now, the point of the above was to help you construct the next command. This heavily depends on where ndiswrapper is, so follow closely. The command we're after is this:
```
cd <Location>/<Name>
```

As shown in the screenshot, Location is "/home/jacob/Desktop" and the name is "ndiswrapper-1.52". Thus, the command would look like this for me:
```
cd /home/jacob/Desktop/ndiswrapper-1.52
```

So, once you've got that figured out, hit the ENTER key. You'll see the terminal switch to the new folder.

Now that we're where we need to be, run the following command, which will remove any installed ndiswrapper modules:

```
sudo make uninstall
```
Keep running this until you no longer see any more "removing" messages. Note in the screenshot provided the two highlighted areas. Notice how the first time I ran it, it removed something. I ran it again, and this time there were no more "removing" messages. This means I can move on.

[img]http://eagleswingscoop.org/junk/wusb54gs/3-4.png[/img]

[INDENT]**Troubleshooting:** Some have reported that sudo make uninstall reports an error about a directory that was unable to be deleted. If the directory is "/lib/modules/<numbers>/kernel/drivers/net/ndiswrapper", then run this command:
```
sudo rm -fR /lib/modules/$(uname -r)/kernel/drivers/net/ndiswrapper
```
[/INDENT]

Next, run these two commands to compile and then install the new ndiswrapper:
```
make
sudo make install
```

To complete the task, and to tell the kernel to always load ndiswrapper at startup, run the following command:

```

sudo ndiswrapper -m

```

**_Step 4 - Getting the drivers_**
This will be easy. You should've already gotten the attachment. If you're an advanced user and you are blazing your own trail by getting three files I mentioned previously through other sources, you can skip this whole step.

So, just like before, right-click the attachment and click "Extract Here". A folder should appear yet again. And, just like before, I want you to get the Location and name of this folder by right-clicking the new folder and clicking "Properties".
[img]http://eagleswingscoop.org/junk/wusb54gs/4-1.png[/img]

Use the same command as before to move to wherever the folder is residing at present:
```
cd <Location>/<Name>
```

For me my Location and name, as seen in the screenshot, is written out as follows:
```
cd /home/jacob/Desktop/ndiswrapper-files
```

If you have a WUSB54GS device, run this: ```
cd v1
```
If you have a WUSB54GSv2 device, run this: ```
cd v2
```

**_Step 5 - Installing drivers_**

Now, if you have a WUSB54GS device, run this: ```
sudo ndiswrapper -i WUSB54GS.inf
```
If you have a WUSB54GSv2 device, run this: ```
sudo ndiswrapper -i WUSB54GSv2.inf
```

Now run this command:

```
ndiswrapper -l
```

My guess is that you'll come back to this tutorial wondering what went wrong, right? Ndiswrapper reports "invalid driver", right? Well, if I'm wrong, skip the rest of this step.

The last command says that the drivers are invalid. That's because it didn't install the sys files! We need to do this manually. Run these commands in the same terminal:

If you have a WUSB54GS device, run this: ```
sudo cp usb8023.sys rndismp.sys /etc/ndiswrapper/wusb54gs/
```
If you have a WUSB54GSv2 device, run this: ```
sudo cp usb8023.sys rndismp.sys /etc/ndiswrapper/wusb54gsv2/
```

*Now* run this command:

```
ndiswrapper -l
```

It should work. I've provided the screenshot of the results of this step.
[img]http://eagleswingscoop.org/junk/wusb54gs/5-1.png[/img]

**_Step 6 - Connecting up the device_**
Alright. Now you get to actually enjoy all this work. Run this command:

```
sudo modprobe ndiswrapper
```
[INDENT]If you get a "FATAL" error that says "/lib/<kernel>/misc/ndiswrapper.ko: invalid argument" then that means that you haven't gotten any drivers installed yet.[/INDENT]

Plug in your device. The Power light will come on, and, after at most 3 seconds, the Link light will blink slowly. If the Link light does blink slowly, sucess!

Now run this command:

```
cat /var/log/syslog
```

If the end of the output looks something like this:
```
usb 4-2: new high speed USB device using ehci_hcd and address 4
usb 4-2: no configuration chosen from 1 choice
ndiswrapper version 1.32 loaded (preempt=no,smp=yes)
usb 4-2: reset high speed USB device using ehci_hcd and address 4
ndiswrapper: driver wusb54gsv2 (Linksys,01/25/2005, 4.01.20.0) loaded
wlan0: ethernet device 00:18:39:03:99:5a using NDIS driver: wusb54gsv2, version: 0x4011405, NDIS version: 0x501, vendor: 'Linksys Wireless-G USB Network Adapter with SpeedBooster', 13B1:0014.F.conf
wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
usbcore: registered new driver ndiswrapper
ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
BUG: unable to handle kernel NULL pointer dereference at virtual address 00000000
 printing eip:
c6f1e488
*pde = 00000000
Oops: 0002 [#1]
SMP
Modules linked in: ndiswrapper radeon drm fuse via_rhine mii snd_seq_dummy snd_seq_oss snd_seq_midi_event snd_seq af_packet snd_pcm_oss snd_mixer_oss video snd_via82xx thermal gameport sbs snd_ac97_codec snd_ac97_bus i2c_ec snd_pcm snd_timer snd_page_alloc snd_mpu401_uart snd_rawmidi snd_seq_device fan snd soundcore container button battery ac ide_cd binfmt_misc loop nls_iso8859_1 nls_cp850 vfat fat dm_mod yenta_socket rsrc_nonstatic pcmcia pcmcia_core cpufreq_ondemand cpufreq_conservative cpufreq_powersave freq_table processor via_agp agpgart usbmouse evdev ohci1394 ieee1394 usbhid bttv video_buf firmware_class ir_common compat_ioctl32 i2c_algo_bit btcx_risc tveeprom i2c_core usbkbd videodev v4l1_compat v4l2_common floppy usb_storage ehci_hcd uhci_hcd usbcore sata_vsc sata_via sata_svw sata_sil sata_promise sata_nv sx8 sata_uli sata_sx4 sata_sis sata_qstor ahci BusLogic aic7xxx scsi_transport_spi sg sr_mod cdrom ata_piix sd_mod libata scsi_mod ext3 jbd
CPU:    0
EIP:    0060:[<c6f1e488>]    Tainted: P      VLI
EFLAGS: 00010246   (2.6.18.6.dev3.lgc #1)
EIP is at 0xc6f1e488
eax: 00000000   ebx: c71992c0   ecx: cebf6500   edx: c71996c0
esi: ce497800   edi: c89b97a0   ebp: c7db9df8   esp: c7db9de8
ds: 007b   es: 007b   ss: 0068
Process sh (pid: 3343, ti=c7db8000 task=cfd81250 task.ti=c7db8000)
Stack: d0837e28 c6f1e200 00000001 c89b95a0 d0837e0a d0d5828b ce497800 00000002
       00000000 00000000 00000002 00000000 00000297 d0d4e5c7 c89b9b80 00000000
       d0d5303d c89b9b80 00000000 c7db9e6c c89b97a0 d0d53147 c89b97a0 0000001b
Call Trace:
 [<d0d5828b>] NdisDispatchPnp+0x18b/0x7d0 [ndiswrapper]
 [<d0d4e5c7>] get_current_nt_thread+0xa7/0xd0 [ndiswrapper]
 [<d0d5303d>] IoQueueThreadIrp+0xd/0xe0 [ndiswrapper]
 [<d0d53147>] IoBuildSynchronousFsdRequest+0x37/0x40 [ndiswrapper]
 [<d0d5236d>] IofCallDriver+0x2d/0x50 [ndiswrapper]
 [<d0d54853>] IoSendIrpTopDev+0x73/0xb0 [ndiswrapper]
 [<d0d548c6>] pnp_remove_device+0x36/0x130 [ndiswrapper]
 [<d0e76ef4>] usb_unbind_interface+0x34/0x70 [usbcore]
 [<b0249460>] __device_release_driver+0x50/0x80
 [<b0249697>] device_release_driver+0x17/0x30
 [<b0248da9>] bus_remove_device+0x89/0xa0
 [<b0247bc1>] device_del+0xf1/0x130
 [<d0e753f8>] usb_disable_device+0x88/0xf0 [usbcore]
 [<d0e75d60>] usb_set_configuration+0xb0/0x470 [usbcore]
 [<d0e78c33>] set_bConfigurationValue+0x43/0x58 [usbcore]
 [<d0e78bf0>] set_bConfigurationValue+0x0/0x58 [usbcore]
 [<b024771a>] dev_attr_store+0x1a/0x20
 [<b01a7b8c>] sysfs_write_file+0x7c/0xd0
 [<b016b2b0>] vfs_write+0xa0/0x170
 [<b01a7b10>] sysfs_write_file+0x0/0xd0
 [<b016b96c>] sys_write+0x3c/0x70
 [<b0102fbd>] sysenter_past_esp+0x56/0x79
Code: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 <30> 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
EIP: [<c6f1e488>] 0xc6f1e488 SS:ESP 0068:c7db9de8
```
...then you have an old version of ndiswrapper, most likely from the online official repositories or from the CD. Basically the USB module of the kernel just crashed. If you attempt to restart, it will freeze at "Stopping Bluetooth services...". The new version (v1.21 and higher, *not 1.8!*) fixes this freeze.

If everything looks normal, you are good to go! Last but not least, check dmesg to be sure there aren't any errors.

**_Getting WUSB54GS to Work in Ubuntu 7.04 and higher_**
I've got some bad news and good news. You are going to have to configure your system to work with the WUSB54GS. The good news is that once this configuring is done, you'll never have to worry about it again (until you reinstall or upgrade).

The basics of the problem is that Ubuntu 7.04 and higher has a new "feature" that limits the power that goes to USB devices. This is all well and good to protect USB devices, except when a device wants more power then the kernel likes. The WUSB54GS is one of those devices.

This feature can be turned off. Here's how.

Open up a terminal, and punch in the following:
```
sudo gedit /etc/udev/rules.d/99-custom.rules
```

A new blank file opens up. Copy and paste the following text. Keep the text as one line - do *not* let it wrap over to the next line.
**WUSB54GS v1:**```
BUS=="usb", SYSFS{idProduct}=="000e", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"
```**WUSB54GS v2:**```
BUS=="usb", SYSFS{idProduct}=="0014", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"
```

Save and close it out. Unplug and plug your device, and it should work.

What did we just do? Well, the system that tracks for new devices is called udev. This system has a set of rules under /etc/udev/rules.d/. What we did was add a rule that said "If this device's product is 000e, and the idVendor is 13b1, run this command". The command forces Linux to use configuration choice #1 (which so happens to be ndiswrapper) for this device. The variable $devpath marks where the device's folder is. It took me months to figure this whole thing out, but it was worth every bit of it.

**_Troubleshooting - Read this even if you don't have issues_**
[list]
[*]*Upgrading Your Kernel*
Take notes, 'cause if you upgrade your kernel, you will find that your internet will no longer work. This is because you compiled ndiswrapper into the old kernel, and the new one doesn't have ndiswrapper. Here's the catch - you must also install the headers for that new kernel as well. Without internet access, how are you to do this?

First, reboot into the original kernel (if you have rebooted after updating), by pushing "ESC" on your keyboard when you see GRUB appear after you reboot. Select the older kernel version farther down the list (basically, anything Ubuntu but the recovery options), and then install the new kernel headers. (To install new kernel headers, type in "sudo apt-get install linux-headers-" and then whatever "uname -m" says, minus any "i"s that appear at the beginning. Example: "linux-headers-386") You should then be able to reboot back, and compile ndiswrapper into the new kernel (step 2). The drivers are already installed, but it is just a matter of getting ndiswrapper back into the kernel. If you are utterly confused, you can e-mail me, PM me, or use any other contact given in my profile for help.

[*]*Compiling NDisWrapper with gcc-4.1 or higher*
If you ran "sudo modprobe ndiswrapper" and it says ndiswrapper is an invalid module, and gcc -v says "gcc 4.1", then you need to go back to gcc 4.0. You cannot use gcc-4.1 or higher for some ndiswrapper versions, though newer versions should be fine. When you compile NDisWrapper, and then try to run "sudo modprobe ndiswrapper" with gcc-4.1, it'll say that ndiswrapper is an invalid module. Run "sudo apt-get install gcc-4.0". If it says you already have gcc-4.0 installed, run these commands:
```

(---FORCING USE OF GCC-4.0---)
cd /usr/bin
sudo rm gcc gccbug
sudo ln -s gcc-4.0 gcc
sudo ln -s gccbug-4.0 gccbug

(---COMPILE NDISWRAPPER AT STEP 2---)

(---UNDOING ABOVE CHANGES TO REVERT BACK TO GCC-4.1---)
cd /usr/bin
sudo rm gcc gccbug
sudo ln -s gcc-4.1 gcc
sudo ln -s gccbug-4.1 gccbug
```
This feels funky, but it's alright as long as you do the undo bit when you're done and "gcc -v" says "gcc 4.1" again.

[*]*Compiling NDisWrapper - "Can't find kernel build files in xxx"*
Simply put, ndiswrapper can't find your linux-kernel stuff. Be extra sure you installed this at step 1. If you have installed it, and you know where the kernel headers are, then run this "make" command instead of the one listed at Step 2:

```

make KBUILD=[INSERT KERNEL PATH HERE]

```

[*]*WUSB54GSC device not working?*
User kolyma says he has a method that works! See his post here for more info:
[http://ubuntuforums.org/showpost.php?p=2863623&postcount=184]("http://ubuntuforums.org/showpost.php?p=2863623&postcount=184")
[/list]

**_What To Do If Your Computer Freezes Up**_
If something went wrong, and your system is now frozen, restart using the following key combinations, waiting 3 seconds in between each one (the italicized letter helps you remember it):

```
Ctrl+Alt+SysRq+R *(aising)*
Ctrl+Alt+SysRq+S *(skinny)*
Ctrl+Alt+SysRq+E *(lephants)*
Ctrl+Alt+SysRq+I *(s)*
Ctrl+Alt+SysRq+U *(tterly)*
Ctrl+Alt+SysRq+B *(oring)*
```*(This safely reboots your computer, saving everything to disk before shutting down. You can use this almost any time your computer freezes, as long as your computer didn't freeze completely.)*

Unplug your device, and then turn on your computer. Grab /var/log/syslog and /etc/udev/rules.d/99-custom.rules, and make a post on this thread so we can help you out.

**_(OPTIONAL) Setting up NetworkManager_**
Alright, so you have this new nifty wireless device, and you've probably already connected to your network. If you have a laptop, as soon as you move around to other networks you'll instantly wish that you had some way to replicate Windows' ability to save passwords, and connect to the nearest one.

Well, there's an answer to this problem. The answer's called NetworkManager. It essentially does everything it can to keep the internet up and going for you. It also makes sure there's only one internet connection going at a time, so if you plug in ethernet, wireless is dropped, and if ethernet is unplugged, it goes for wireless or other sources.

Enough chat, let's get down to business. First we have to get the system ready for NetworkManager. Make a backup copy of /etc/network/interfaces file, and remove every interface except for lo. That's right. Remove every interface except for lo. NetworkManager (or the Ubuntu version, anyway) won't manage your network unless you remove it completely from the interfaces file.

Next, install NetworkManager, like so:
```
sudo apt-get install network-manager-gnome
```
It's alright if it is already installed, because newer versions already have it running.

Open up /etc/modules, like so:
```
sudo gedit /etc/modules
```
...and punch in "ndiswrapper" at the end of that file. Save and close that file.

Restart your computer. When you log back in, you should see a fella in your task bar that looks like a computer or signal bars. You can left click to bring  up all the wireless networks around you, and right click to view information about your current connection and set a few settings.

I've provided a screenshot below (I blanked the network names out for privacy):
[img]http://eagleswingscoop.org/junk/wusb54gs/nm.png[/img]


**_Credits and Revisions_**
I accept all feedback on this tutorial, so speak out!!!

October 30, 2008 - As of Ubuntu Intrepid, this HOWTO is deprecated.
August 10, 2008 - Added note about WUSB54GS v2.1 in the First things First section
April 30, 2008 - Clarified Step 2, specifically the bits for advanced users
April 30, 2008 - Fixed a typo (where it said /home/jacob/Desktop/drivers instead of /home/jacob/Desktop/ndiswrapper-files)
April 12, 2008 - Complete overhaul with screenshots
[color=grey]October 21, 2007 - _Thanks to interconnect_ Added Gutsy to supported Ubuntu versions.
June 24, 2007 - Minor edit
June 18, 2007 - Changed kernel crash check to be more accurate, since more people seem to be getting kernel crash issues in different ways, but they are all because of the same thing.
June 18, 2007 - _Thanks to kolyma_ WUSB54GSC added in "First things First" and "Troubleshooting"
June 7, 2007 - Changed some dead links. Gotta love dead links.
April 1, 2007 - Added information about latest ndiswrapper version under the section "Building Ndiswrapper".
December 14, 2006 - Feisty support added, and "this HOWTO doesn't follow regulations" note added at top.
December 11, 2006 - _Thanks to Jay-Jay_ Added the editing of /etc/modules to installation of NetworkManager, and then also changed the Troubleshooting sections that have to do with NetworkManager.
December 9, 2006 - Changed the structure of this HOWTO a bit to make it cleaner.
December 9, 2006 - _Thanks to Jay-Jay_ Some new Troubleshooting items - "On Edgy, device won't work, but ndiswrapper -l says it's there" and "NetworkManager isn't working".
December 9, 2006 - _Thanks to Jay-Jay_ WUSB54GS v_2_ has a different udev line in Edgy support then does WUSB54GS v_1_.
December 9, 2006 - _Thanks to jcda_ Fixed a typo in the udev entry line in the Edgy support.
November 25, 2006 - Added "Setting up NetworkManager" section.
November 25, 2006 - _One typo thanks to mrfoobar_ Fixed some typos, removed stale warnings that have been fixed.
November 25, 2006 - Finally got around to making WUSB54GS stable on Edgy. The "Getting the WUSB54GS to Work in Edgy" section has been redone.
November 5, 2006 - Updated attachment with new ndiswrapper.
October 28, 2006 - Added shaky Edgy support. Works for now... needs work, though.
October 21, 2006 - _Thanks to chefjames_ Fixed a few typos - changed "`uname -r'" to "$(uname -r)", and added force option (-F) to the Troubleshoot note in the "Building NDisWrapper" section.
October 9, 2006 - _Thanks to colleps1_ Added helpful information about how to install new kernel headers in "Upgrading Your Kernel" item under "Troubleshooting" section.
October 9, 2006 - _Thanks to colleps1_ Fixed typo in "Compiling NDisWrapper with gcc-4.1 or higher" under the "Troubleshooting" section - said "Forcing use of gcc 4.1", when it shoud've been gcc 4.0
October 3, 2006 - _Thanks to markopolo12_ Added "Compiling NDisWrapper - 'Can't find kernel build files in xxx'" resolution to the "Troubleshooting" section.
October 3, 2006 - _Thanks to Pitxoki_ Added warning about ndiswrapper v1.23 possibly not working.
September 24, 2006 - _Thanks to Pitxoki_ - Fixed a few typos.
September 24, 2006 - Added "Compiling NDisWrapper with gcc-4.1 or higher" resolution to the Troubleshooting section.
September 15, 2006 - _Thanks to Pitxoki_ - Added the "sudo ndiswrapper -m" command at the end of Step 2.
September 15, 2006 - _Thanks to Pitxoki_ - Added the new "Troubleshooting" section, and added the first item: upgrading the kernel.
September 13, 2006 - _Thanks to Otto-C_ - Added details to "Remove ndiswrapper" bullet in the section "First Things First".
September 3, 2006 - _Thanks to darklord_ - Added a note to the "First things First" section, saying that this tutorial doesn't support 64-bit processors yet.
August 26, 2006 - Changed "NOTE" in Step 2 to be more accurate, and less fuzzy.
August 25, 2006 - Formatting typo
August 17, 2006 - Changed Step 1 to be compatible with all machine types (amd64, powerpc, pentium, etc.)
August 12, 2006 - _Thanks to ChrisC098_ - Some major revisions.
August 2, 2006 - _Thanks to Emmanuel_uk_ - Made instructions for users without a Windows XP installation. Completely depended on Emmanuel_uk for this, and did not test it - let me know if something is wrong.
July 30, 2006 - _Thanks to Emmanuel_uk_ - Made it easier for newbies by giving them less "copy the drivers" and more "do these commands".
July 26, 2006 - Uploaded new attachment, and fixed large portions of the HOW-TO.
July 26, 2006 - Added WUSB54GS **v2** support to the tutorial, along with some minor spelling and wording fixes.[/color]

**A big thanks to Pitxoki and Emmanuel_uk for the superior help!**

---

### Post by darklord on 2006-09-03
Hi there,

Thanks for the howto.

One thing to note;- you have only cover 32bit installation. I successful followed your instructions on Ubuntu LTS k8 smp kernel version but dmesg has output the following messages 

[   43.113970] powernow-k8: Found 2 AMD Athlon 64 / Opteron processors (version 1.50.4)
[   43.114039] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0xa (1300 mV)
[   43.114044] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xc (1250 mV)
[   43.114047] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12 (1100 mV)
[   43.114051] cpu_init done, current fid 0xc, vid 0xa
[   44.204014] NET: Registered protocol family 10
[   44.204115] lo: Disabled Privacy Extensions
[   44.204454] IPv6 over IPv4 tunneling driver
[   45.402834] ppdev: user-space parallel port driver
[   48.092828] Bluetooth: Core ver 2.8
[   48.092833] NET: Registered protocol family 31
[   48.092835] Bluetooth: HCI device and connection manager initialized
[   48.092846] Bluetooth: HCI socket layer initialized
[   48.112994] Bluetooth: L2CAP ver 2.8
[   48.112998] Bluetooth: L2CAP socket layer initialized
[   48.160979] Bluetooth: RFCOMM socket layer initialized
[   48.160992] Bluetooth: RFCOMM TTY layer initialized
[   48.160994] Bluetooth: RFCOMM ver 1.7
[   52.543716] eth0: no IPv6 routers present
[ 1047.229285] ndiswrapper version 1.21 loaded (preempt=yes,smp=yes)
[ 1047.289080] usb 1-2: reset high speed USB device using ehci_hcd and address 2
[ 1047.362774] ndiswrapper (check_nt_hdr:149): kernel is 64-bit, but Windows dri ver is not 64-bit;bad magic: 010B
[ 1047.362782] ndiswrapper (load_sys_files:215): couldn't prepare driver 'wusb54 gsv2'
[ 1047.364341] ndiswrapper (load_wrap_driver:113): loadndiswrapper failed (65280 ); check system log for messages from 'loadndisdriver'
[ 1047.364348] ndiswrapper: probe of 1-2:1.0 failed with error -22
[ 1047.423318] usb 1-2: reset high speed USB device using ehci_hcd and address 2
[ 1047.490548] ndiswrapper (check_nt_hdr:149): kernel is 64-bit, but Windows dri ver is not 64-bit;bad magic: 010B
[ 1047.490557] ndiswrapper (load_sys_files:215): couldn't prepare driver 'wusb54 gsv2'
[ 1047.490856] ndiswrapper (load_wrap_driver:113): loadndiswrapper failed (65280 ); check system log for messages from 'loadndisdriver'
[ 1047.490861] ndiswrapper: probe of 1-2:1.1 failed with error -22
[ 1047.490870] usbcore: registered new driver ndiswrapper
[ 1063.336545] usb 1-2: USB disconnect, address 2
[ 1067.231441] usb 1-2: new high speed USB device using ehci_hcd and address 5
[ 1067.298351] usb 1-2: bad CDC descriptors
[ 1067.356862] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[ 1067.424495] ndiswrapper (check_nt_hdr:149): kernel is 64-bit, but Windows dri ver is not 64-bit;bad magic: 010B
[ 1067.424504] ndiswrapper (load_sys_files:215): couldn't prepare driver 'wusb54 gsv2'
[ 1067.424817] ndiswrapper (load_wrap_driver:113): loadndiswrapper failed (65280 ); check system log for messages from 'loadndisdriver'
[ 1067.424823] ndiswrapper: probe of 1-2:1.0 failed with error -22
[ 1067.480702] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[ 1067.548347] ndiswrapper (check_nt_hdr:149): kernel is 64-bit, but Windows dri ver is not 64-bit;bad magic: 010B
[ 1067.548356] ndiswrapper (load_sys_files:215): couldn't prepare driver 'wusb54 gsv2'
[ 1067.548680] ndiswrapper (load_wrap_driver:113): loadndiswrapper failed (65280 ); check system log for messages from 'loadndisdriver'
[ 1067.548687] ndiswrapper: probe of 1-2:1.1 failed with error -22
[ 1073.155715] usb 1-2: USB disconnect, address 5
[ 1078.183132] usb 1-1: new high speed USB device using ehci_hcd and address 6
[ 1078.248073] usb 1-1: bad CDC descriptors
[ 1078.304560] usb 1-1: reset high speed USB device using ehci_hcd and address 6
[ 1078.372238] ndiswrapper (check_nt_hdr:149): kernel is 64-bit, but Windows dri ver is not 64-bit;bad magic: 010B
[ 1078.372248] ndiswrapper (load_sys_files:215): couldn't prepare driver 'wusb54 gsv2'
[ 1078.372561] ndiswrapper (load_wrap_driver:113): loadndiswrapper failed (65280 ); check system log for messages from 'loadndisdriver'
[ 1078.372568] ndiswrapper: probe of 1-1:1.0 failed with error -22
[ 1078.428404] usb 1-1: reset high speed USB device using ehci_hcd and address 6
[ 1078.496103] ndiswrapper (check_nt_hdr:149): kernel is 64-bit, but Windows dri ver is not 64-bit;bad magic: 010B
[ 1078.496112] ndiswrapper (load_sys_files:215): couldn't prepare driver 'wusb54 gsv2'
[ 1078.496430] ndiswrapper (load_wrap_driver:113): loadndiswrapper failed (65280 ); check system log for messages from 'loadndisdriver'
[ 1078.496436] ndiswrapper: probe of 1-1:1.1 failed with error -22

so im guessing if i find a 64bit windows driver for ver2 and follow the same steps it will work?

If i have any succes i will let you know.

I suppose i could always use the standard 686 kernel.

---

### Post by javaJake on 2006-09-03
You are absolutely correct. If you have a 64-bit processor, the drivers included in the attachment WILL NOT work. You'll need different drivers specially made for 64-bit processors.

Unfortunately I do not have access, nor know how to get access, to 64-bit drivers. The trick is that Windows already has some drivers installed, so Linksys doesn't distrobute those. However, for it to work in Linux, you need to manually copy those drivers over. :( 

If you can gather the two 64-bit .sys files from a Windows 64-bit installation, or from a reliable source, please e-mail them to me, and I'll update the attachment accordingly.

Thanks for your input! :D 

> **darklord said:**
> Hi there,

Thanks for the howto.

One thing to note;- you have only cover 32bit installation. I successful followed your instructions on Ubuntu LTS k8 smp kernel version but dmesg has output the following messages 

[   43.113970] powernow-k8: Found 2 AMD Athlon 64 / Opteron processors (version 1.50.4)
[   43.114039] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0xa (1300 mV)
[   43.114044] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xc (1250 mV)
[   43.114047] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12 (1100 mV)
[   43.114051] cpu_init done, current fid 0xc, vid 0xa
[   44.204014] NET: Registered protocol family 10
[   44.204115] lo: Disabled Privacy Extensions
[   44.204454] IPv6 over IPv4 tunneling driver
[   45.402834] ppdev: user-space parallel port driver
[   48.092828] Bluetooth: Core ver 2.8
[   48.092833] NET: Registered protocol family 31
[   48.092835] Bluetooth: HCI device and connection manager initialized
[   48.092846] Bluetooth: HCI socket layer initialized
[   48.112994] Bluetooth: L2CAP ver 2.8
[   48.112998] Bluetooth: L2CAP socket layer initialized
[   48.160979] Bluetooth: RFCOMM socket layer initialized
[   48.160992] Bluetooth: RFCOMM TTY layer initialized
[   48.160994] Bluetooth: RFCOMM ver 1.7
[   52.543716] eth0: no IPv6 routers present
[ 1047.229285] ndiswrapper version 1.21 loaded (preempt=yes,smp=yes)
[ 1047.289080] usb 1-2: reset high speed USB device using ehci_hcd and address 2
[ 1047.362774] ndiswrapper (check_nt_hdr:149): kernel is 64-bit, but Windows dri ver is not 64-bit;bad magic: 010B
[ 1047.362782] ndiswrapper (load_sys_files:215): couldn't prepare driver 'wusb54 gsv2'
[ 1047.364341] ndiswrapper (load_wrap_driver:113): loadndiswrapper failed (65280 ); check system log for messages from 'loadndisdriver'
[ 1047.364348] ndiswrapper: probe of 1-2:1.0 failed with error -22
[ 1047.423318] usb 1-2: reset high speed USB device using ehci_hcd and address 2
[ 1047.490548] ndiswrapper (check_nt_hdr:149): kernel is 64-bit, but Windows dri ver is not 64-bit;bad magic: 010B
[ 1047.490557] ndiswrapper (load_sys_files:215): couldn't prepare driver 'wusb54 gsv2'
[ 1047.490856] ndiswrapper (load_wrap_driver:113): loadndiswrapper failed (65280 ); check system log for messages from 'loadndisdriver'
[ 1047.490861] ndiswrapper: probe of 1-2:1.1 failed with error -22
[ 1047.490870] usbcore: registered new driver ndiswrapper
[ 1063.336545] usb 1-2: USB disconnect, address 2
[ 1067.231441] usb 1-2: new high speed USB device using ehci_hcd and address 5
[ 1067.298351] usb 1-2: bad CDC descriptors
[ 1067.356862] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[ 1067.424495] ndiswrapper (check_nt_hdr:149): kernel is 64-bit, but Windows dri ver is not 64-bit;bad magic: 010B
[ 1067.424504] ndiswrapper (load_sys_files:215): couldn't prepare driver 'wusb54 gsv2'
[ 1067.424817] ndiswrapper (load_wrap_driver:113): loadndiswrapper failed (65280 ); check system log for messages from 'loadndisdriver'
[ 1067.424823] ndiswrapper: probe of 1-2:1.0 failed with error -22
[ 1067.480702] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[ 1067.548347] ndiswrapper (check_nt_hdr:149): kernel is 64-bit, but Windows dri ver is not 64-bit;bad magic: 010B
[ 1067.548356] ndiswrapper (load_sys_files:215): couldn't prepare driver 'wusb54 gsv2'
[ 1067.548680] ndiswrapper (load_wrap_driver:113): loadndiswrapper failed (65280 ); check system log for messages from 'loadndisdriver'
[ 1067.548687] ndiswrapper: probe of 1-2:1.1 failed with error -22
[ 1073.155715] usb 1-2: USB disconnect, address 5
[ 1078.183132] usb 1-1: new high speed USB device using ehci_hcd and address 6
[ 1078.248073] usb 1-1: bad CDC descriptors
[ 1078.304560] usb 1-1: reset high speed USB device using ehci_hcd and address 6
[ 1078.372238] ndiswrapper (check_nt_hdr:149): kernel is 64-bit, but Windows dri ver is not 64-bit;bad magic: 010B
[ 1078.372248] ndiswrapper (load_sys_files:215): couldn't prepare driver 'wusb54 gsv2'
[ 1078.372561] ndiswrapper (load_wrap_driver:113): loadndiswrapper failed (65280 ); check system log for messages from 'loadndisdriver'
[ 1078.372568] ndiswrapper: probe of 1-1:1.0 failed with error -22
[ 1078.428404] usb 1-1: reset high speed USB device using ehci_hcd and address 6
[ 1078.496103] ndiswrapper (check_nt_hdr:149): kernel is 64-bit, but Windows dri ver is not 64-bit;bad magic: 010B
[ 1078.496112] ndiswrapper (load_sys_files:215): couldn't prepare driver 'wusb54 gsv2'
[ 1078.496430] ndiswrapper (load_wrap_driver:113): loadndiswrapper failed (65280 ); check system log for messages from 'loadndisdriver'
[ 1078.496436] ndiswrapper: probe of 1-1:1.1 failed with error -22

so im guessing if i find a 64bit windows driver for ver2 and follow the same steps it will work?

If i have any succes i will let you know.

I suppose i could always use the standard 686 kernel.

---

### Post by darklord on 2006-09-03
hi Javajake

I found a link for the 64bit drivers (hopeful) i will test them. But before i test them how do i uninstall the 32bit driver.

[do i need to uninstall them or any other steps before installation of new driver]

planetAMD64 forum
[http://www.planetamd64.com/index.php?showtopic=19228&st=20](http://www.planetamd64.com/index.php?showtopic=19228&st=20)

Direct link to modified driver for 
Belkin F5D7051
Linksys WUSB54GS v2

modified for WUSB54GS ver 1 and 2 i believe.
[http://www.planetamd64.com/index.php?act=Attach&type=post&id=4290](http://www.planetamd64.com/index.php?act=Attach&type=post&id=4290)

With thanks!!!

---

### Post by darklord on 2006-09-03
im afraid, no luck with this set of drivers.

altered the downloaded driver so the amd64 section says
 code:


[LinksysDevices.NTamd64]

%LinksysDevice%     = RNDIS.NT.5.1, USB\VID_13B1&PID_000E
%LinksysDevice%     = RNDIS.NT.5.1, USB\VID_13B1&PID_0014

device manager (ubuntu dm)
usb.product_id    int   20    (0x14)
usb.vendor        int   5041  (0x13b1)

ndiswrapper -l says the following:-
wusb54gs                driver installed


dmesg states the following:-

[  319.437633] ndiswrapper version 1.21 loaded (preempt=yes,smp=yes)
[  319.443827] usbcore: registered new driver ndiswrapper
[ 1021.844387] usb 1-1: USB disconnect, address 2
[ 1025.487613] usb 1-1: new high speed USB device using ehci_hcd and address 5
[ 1025.555786] usb 1-1: bad CDC descriptors

Question 1:- whats CDC

Question 2:- is an AMD64 bit driver, going to wrk on AMD64 x2 chip? (DUal Core)

---

### Post by javaJake on 2006-09-03
Uninstalling drivers (which means manually removing - ndiswrapper doesn't keep track of them sys drivers) is a good idea, just to be safe.

> **darklord said:**
> hi Javajake

I found a link for the 64bit drivers (hopeful) i will test them. But before i test them how do i uninstall the 32bit driver.

[do i need to uninstall them or any other steps before installation of new driver]

planetAMD64 forum
[http://www.planetamd64.com/index.php?showtopic=19228&st=20](http://www.planetamd64.com/index.php?showtopic=19228&st=20)

Direct link to modified driver for 
Belkin F5D7051
Linksys WUSB54GS v2

modified for WUSB54GS ver 1 and 2 i believe.
[http://www.planetamd64.com/index.php?act=Attach&type=post&id=4290](http://www.planetamd64.com/index.php?act=Attach&type=post&id=4290)

With thanks!!!

---

### Post by javaJake on 2006-09-03
If the output from ndiswrapper was recorded AFTER inserting the device, then it is probably pointing to the wrong USB ID.

Try looking to see what ID the WUSB54GS driver is at, and set ndiswrapper to look for it there like this:

ndiswrapper -d XXXX:XXXX wusb54gs

If you want, tell me what lsusb says, and I'll fill in those X's for you.

*More comments below...*

> **darklord said:**
> im afraid, no luck with this set of drivers.

altered the downloaded driver so the amd64 section says
 code:


[LinksysDevices.NTamd64]

%LinksysDevice%     = RNDIS.NT.5.1, USB\VID_13B1&PID_000E
%LinksysDevice%     = RNDIS.NT.5.1, USB\VID_13B1&PID_0014

device manager (ubuntu dm)
usb.product_id    int   20    (0x14)
usb.vendor        int   5041  (0x13b1)

ndiswrapper -l says the following:-
wusb54gs                driver installed

Assuming NDiswrapper output was recorded after you plugged the device in, then ndiswrapper isn't pointing to the right USB ID.

> **darklord said:**
> 
dmesg states the following:-

[  319.437633] ndiswrapper version 1.21 loaded (preempt=yes,smp=yes)
[  319.443827] usbcore: registered new driver ndiswrapper
[ 1021.844387] usb 1-1: USB disconnect, address 2
[ 1025.487613] usb 1-1: new high speed USB device using ehci_hcd and address 5
[ 1025.555786] usb 1-1: bad CDC descriptors

Dmesg says this clearly. It only registeres the device. It doesn't assign the device to any drivers. Just registers the fact it exists.

> **darklord said:**
> 
Question 1:- whats CDC

I don't know. I get this error all the time, and it doesn't seem to affect anything. I wouldn't count on it for this issue.

> **darklord said:**
> 
Question 2:- is an AMD64 bit driver, going to wrk on AMD64 x2 chip? (DUal Core)
Hmmmm... good Q.... I'll look into this. Let's try to move on without this, since the output so far doesn't point to this issue.

---

### Post by cjbrunner on 2006-09-04
Thank you for all of the helpful information on ndiswrapper and driver installation.  I made it almost all of the way through with no problem, but when I got to the step where you said that the power LED would blink slowly, it did not.  According to dmesg the driver did not load correctly.  It states:

usbcore: registered new driver ndiswrapper
usb 1-3: USB disconnect, address 3
usb 1-3: new high speed USB device using ehci_hcd and address 4
usb 1-3: reset high speed USB device using ehci_hcd and address 4
ndiswrapper (import:241): unknown symbol: NDIS.SYS:'NdisIMNotifyPnPEvent'
ndiswrapper (load_sys_files:214): couldn't prepare driver 'wusb54gs'
ndiswrapper (load_wrap_driver:113): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'
ndiswrapper: probe of 1-3:1.0 failed with error -22
usb 1-3: reset high speed USB device using ehci_hcd and address 4
ndiswrapper (import:241): unknown symbol: NDIS.SYS:'NdisIMNotifyPnPEvent'
ndiswrapper (load_sys_files:214): couldn't prepare driver 'wusb54gs'
ndiswrapper (load_wrap_driver:113): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'
ndiswrapper: probe of 1-3:1.1 failed with error -22


Unfortunately, I have no Earthly idea what this means.  ndiswrapper -l reports that the driver is installed, so I don't get it.

Thanks in advance!

---

### Post by darklord on 2006-09-04
Javajake,

I followed your suggestions,

ndiswrapper -d XXXX:XXXX wusb54gs.

In terminal 

code:
lsusb

which outputted the following;

code:
Bus 001 Device 003: ID 0518:0002 EzKEY Corp.
Bus 001 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 005: ID 13b1:0014 Linksys
Bus 002 Device 001: ID 0000:0000

so if im corrected this are the values stored in wusb54gs as product id and vendor id.

anyway i tried your suggestion of 

code:
ndiswrapper -d 13b1:0014 wusb54gs

this spat out the following message.
code:
Driver 'wusb54gs' is used for '13B1:0014'

once the usb device is plugged in
code:
 ndiswrapper -l

reports
code:
Installed drivers:
wusb54gs                driver installed, hardware present


this had no effect, ie. no lightrs on device and didn't report anything in dmesg,

please note this is not an offical driver for WIndows 64, as the appear to be none available. 

SO I downloaded this driver from a forum where users have reported that they have got this driver to work under 64 bit window enviroment. 

Any suggestion would be most appreciated as i would like to help you get a working 64 bit driver. (i dont have a windows 64 enviroment to test the driver natively myself)




cjbruner, 


when ndiswrapper correctly loads the driver and the usb-nic is plugged n ndiswrapper will report the following 

wusb54gs driver installed  hardware present.

ndiswrapper -d XXXX:XXXX wusb54gs

---

### Post by javaJake on 2006-09-05
> **cjbrunner said:**
> Thank you for all of the helpful information on ndiswrapper and driver installation.  I made it almost all of the way through with no problem, but when I got to the step where you said that the power LED would blink slowly, it did not.  According to dmesg the driver did not load correctly.  It states:

usbcore: registered new driver ndiswrapper
usb 1-3: USB disconnect, address 3
usb 1-3: new high speed USB device using ehci_hcd and address 4
usb 1-3: reset high speed USB device using ehci_hcd and address 4
ndiswrapper (import:241): unknown symbol: NDIS.SYS:'NdisIMNotifyPnPEvent'
ndiswrapper (load_sys_files:214): couldn't prepare driver 'wusb54gs'
ndiswrapper (load_wrap_driver:113): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'
ndiswrapper: probe of 1-3:1.0 failed with error -22
usb 1-3: reset high speed USB device using ehci_hcd and address 4
ndiswrapper (import:241): unknown symbol: NDIS.SYS:'NdisIMNotifyPnPEvent'
ndiswrapper (load_sys_files:214): couldn't prepare driver 'wusb54gs'
ndiswrapper (load_wrap_driver:113): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'
ndiswrapper: probe of 1-3:1.1 failed with error -22


Unfortunately, I have no Earthly idea what this means.  ndiswrapper -l reports that the driver is installed, so I don't get it.

Thanks in advance!

Hmmm... the the trouble here is caused by this error:
ndiswrapper (import:241): unknown symbol: NDIS.SYS:'NdisIMNotifyPnPEvent'

Something happened as it tried to load the drivers to use with the card. Googling didn't produce any help... what OS are you using? What processor?

---

### Post by javaJake on 2006-09-05
> **darklord said:**
> Javajake,

I followed your suggestions,

ndiswrapper -d XXXX:XXXX wusb54gs.

In terminal 

code:
lsusb

which outputted the following;

code:
Bus 001 Device 003: ID 0518:0002 EzKEY Corp.
Bus 001 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 005: ID 13b1:0014 Linksys
Bus 002 Device 001: ID 0000:0000

so if im corrected this are the values stored in wusb54gs as product id and vendor id.

anyway i tried your suggestion of 

code:
ndiswrapper -d 13b1:0014 wusb54gs

this spat out the following message.
code:
Driver 'wusb54gs' is used for '13B1:0014'

once the usb device is plugged in
code:
 ndiswrapper -l

reports
code:
Installed drivers:
wusb54gs                driver installed, hardware present


this had no effect, ie. no lightrs on device and didn't report anything in dmesg,

please note this is not an offical driver for WIndows 64, as the appear to be none available. 

SO I downloaded this driver from a forum where users have reported that they have got this driver to work under 64 bit window enviroment. 

Any suggestion would be most appreciated as i would like to help you get a working 64 bit driver. (i dont have a windows 64 enviroment to test the driver natively myself) What does dmesg say after you plug the device in? The device will stop blinking after connecting to an access point.

I'll make a better reply tomorrow...

---

### Post by javaJake on 2006-09-12
[SIZE="1"]Ignore.[/SIZE]

---

### Post by javaJake on 2006-09-12
darklord, seems I've forgotten to "make a better reply"... anyway, here it is.

Did you run "sudo modprobe -m"? This will make ndiswrapper load on startup without you having to run "sudo modprobe ndiswrapper" all the time.

---

### Post by Otto-C on 2006-09-13
I was most interested in your How-To:

First things first:

Remove any remains of any past versions of ndiswrapper. 

Please outline how best to remove past versions.

tia
Otto-C

---

### Post by javaJake on 2006-09-13
> **Otto-C said:**
> I was most interested in your How-To:

First things first:

Remove any remains of any past versions of ndiswrapper. 

Please outline how best to remove past versions.

tia
Otto-C

Hmmm... it might be a good idea, however this can become slightly complicated, since some users use the debian package system for ndiswrapper, and others compile manually. Plus, if you installed ndiswrapper in the first place, shouldn't you know how to uninstall...?

Considering all this, here's my best shot at instructions:

> 
If you installed using apt-get, then run "apt-get remove ndiswrapper-utils". If you compiled ndiswrapper, and installed it, then open a terminal, go into the directory where you ran "make" in the first place, and run "sudo make uninstall". Basically, use the reverse of the method you used to install ndiswrapper in the first place.


This will be included in the HOWTO. Any suggestions are welcome.

---

### Post by Otto-C on 2006-09-13
I guess I'm dead in the water. 
Ubuntu was installed when I bought the machine
as was Ndiswrapper. How Ndis was installed is 
unknown to me. 
Can some alternative removal process be suggested?

tia
Otto-C

---

### Post by javaJake on 2006-09-13
Well, try skipping the "Build Ndiswrapper" section. You may not have to install ndswrapper again. Or you could compile anyway. It'll be really dirty, but it'll overwrite the previous version.

If you decide not to compile, then read this (which comes after installing and plugging in your device):

> 
Now run this command:

```

top
```

If khubd is at the top, and it is using up all remaining CPU, then you have an old version of ndiswrapper, most likely from the online repositories or from the CD. Basically the USB module of the kernel just crashed. If you attempt to restart, it will freeze at "Stopping Bluetooth services...". The new version (v1.21 and higher) fixes this freeze.

---

### Post by javaJake on 2006-09-13
Oh, I forgot to mention. If you run this command...

```

ndiswrapper -v

```

And the driver version is 1.21 or higher, your good to go. Otherwise, I recommend you compile over the current version (if you cannot/don't want to reinstall Ubuntu.)

---

### Post by Tangerined on 2006-09-27
Hi I have a wusb54gs v2 and i followed the steps in the guide and everything went ok until I plugged it in. The power light never comes on and when I typed "top" it showed that khubd is at using like 95% cpu. I've tried both ndiswrapper 1.8 and 1.9. Oh and I'm using ubuntu 6.06.1. So is it not working because its v2?

---

### Post by javaJake on 2006-09-27
> **Tangerined said:**
> Hi I have a wusb54gs v2 and i followed the steps in the guide and everything went ok until I plugged it in. The power light never comes on and when I typed "top" it showed that khubd is at using like 95% cpu. I've tried both ndiswrapper 1.8 and 1.9. Oh and I'm using ubuntu 6.06.1. So is it not working because its v2?

Did you read this part?

> 
Extract ndiswrapper from the attachment, or download it from ndiswrapper.sourceforge.net instead (be sure to get version 1.21 or higher). You absolutely cannot use ndiswrapper from apt-get (repositories)! It is really outdated, unfortunately! If this writing is really old, and the version in apt-get is actually higher then 1.21, then go ahead and skip Step 2. 


Or this part?

> 
Now run this command:

```
top
```

If khubd is at the top, and it is using up all remaining CPU, then you have an old version of ndiswrapper, most likely from the online repositories or from the CD. Basically the USB module of the kernel just crashed. If you attempt to restart, it will freeze at "Stopping Bluetooth services...". The new version (v1.21 and higher) fixes this freeze.

---

### Post by Tangerined on 2006-09-27
Oh oops, stupid mistake on my part, i was thinking it was 1.2.1 or something like that and that 1.9 was newer haha. It works great now thanks.

---

### Post by markopolo12 on 2006-10-03
When I try to compile ndiswrapper, here's what I get for output.

bockensm@threeve:~/Desktop/ndiswrapper-1.24$ make
make -C driver
make[1]: Entering directory `/home/bockensm/Desktop/ndiswrapper-1.24/driver'
Can't find kernel build files in /lib/modules/2.6.15-27-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/bockensm/Desktop/ndiswrapper-1.24/driver'
make: *** [all] Error 2
bockensm@threeve:~/Desktop/ndiswrapper-1.24$

any ideas on why?
I followed the first few steps about installing gcc, cpp, etc.

(I'm running Kubuntu kernel 2.6.15.27 freshly installed)

---

### Post by javaJake on 2006-10-03
> **markopolo12 said:**
> When I try to compile ndiswrapper, here's what I get for output.

bockensm@threeve:~/Desktop/ndiswrapper-1.24$ make
make -C driver
make[1]: Entering directory `/home/bockensm/Desktop/ndiswrapper-1.24/driver'
Can't find kernel build files in /lib/modules/2.6.15-27-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/bockensm/Desktop/ndiswrapper-1.24/driver'
make: *** [all] Error 2
bockensm@threeve:~/Desktop/ndiswrapper-1.24$

any ideas on why?
I followed the first few steps about installing gcc, cpp, etc.

(I'm running Kubuntu kernel 2.6.15.27 freshly installed)

Did you install the kernel headers? This error says you haven't. I'd try apt-get one more time.

If you have installed kernel headers, then they must be somewhere that ndiswrapper doesn't expect. Tell ndiswrapper where they are by running "ndiswrapper KBUILD=" with the path to your kernel at the end.

---

### Post by markopolo12 on 2006-10-03
i remember doing apt-get install linux-headers-2.6.15.27, so where would they have got installed to?

is that /lib/modules/2.6.15-27-386/build where they go?

---

### Post by markopolo12 on 2006-10-04
EDIT:
needed to install linux-kernel-headers-2.6.15-27-386...
I get all the way through the procedure and no complaints. nothing shows up after the procedure is done, and after a reboot the computer hangs on "Starting Network Interfaces" unless the USB adapter is not connected. anyone know anything about this?

---

### Post by javaJake on 2006-10-04
> **markopolo12 said:**
> EDIT:
needed to install linux-kernel-headers-2.6.15-27-386...
I get all the way through the procedure and no complaints. nothing shows up after the procedure is done, and after a reboot the computer hangs on "Starting Network Interfaces" unless the USB adapter is not connected. anyone know anything about this?

Try plugging in the device after the computer is on. If your CPU usage goes up to 100%, and khubd is at the top, you have an old version of ndiswrapper. If this does not happen, please post your /var/log/syslog file after plugging in the device. Having this file every time something new happens helps me respond to your questions right away, like you want me to. :D

---

### Post by markopolo12 on 2006-10-05
here's the contents of /var/log/syslog after i plug the device in. could the problem be that this is v2 of the device??

also, khubd is not at the top of 'top'. i installed ndiswrapper v 1.24 from ndiswrapper.sourceforge.net

```
Oct  5 17:05:42 threeve kernel: [17179756.192000] usb 2-2: new high speed USB device using ehci_hcd and address 5
Oct  5 17:05:42 threeve kernel: [17179756.444000] usb 2-2: reset high speed USB device using ehci_hcd and address 5
Oct  5 17:05:42 threeve kernel: [17179756.588000] ndiswrapper: driver wusb54gsv2 (Linksys,01/25/2005, 4.01.20.0) loaded
Oct  5 17:05:42 threeve kernel: [17179756.588000] Unable to handle kernel NULL pointer dereference at virtual address 00000000
Oct  5 17:05:42 threeve kernel: [17179756.588000]  printing eip:
Oct  5 17:05:42 threeve kernel: [17179756.588000] f8c20862
Oct  5 17:05:42 threeve kernel: [17179756.588000] *pde = 00000000
Oct  5 17:05:42 threeve kernel: [17179756.588000] Oops: 0002 [#1]
Oct  5 17:05:42 threeve kernel: [17179756.588000] PREEMPT 
Oct  5 17:05:42 threeve kernel: [17179756.588000] Modules linked in: nls_cp437 vfat fat isofs udf rfcomm l2cap bluetooth ppdev cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi container button acpi_sbs battery ac i2c_acpi_ec ndiswrapper nls_utf8 ntfs dm_mod md_mod lp irtty_sir sir_dev snd_ca0106 irda snd_rawmidi snd_seq_device snd_ac97_codec snd_pcm_oss parport_pc parport snd_mixer_oss snd_pcm snd_timer crc_ccitt floppy snd soundcore snd_ac97_bus i2c_nforce2 rtc psmouse serio_raw pcspkr i2c_core snd_page_alloc af_packet usblp shpchp pci_hotplug sg sd_mod evdev tsdev usbhid usb_storage ext3 jbd ide_generic forcedeth ehci_hcd ohci_hcd usbcore ide_disk ide_cd cdrom generic amd74xx sata_nv libata scsi_mod thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
Oct  5 17:05:42 threeve kernel: [17179756.588000] CPU:    0
Oct  5 17:05:42 threeve kernel: [17179756.588000] EIP:    0060:[pg0+947873890/1069368320]    Tainted: P      VLI
Oct  5 17:05:42 threeve kernel: [17179756.588000] EFLAGS: 00010246   (2.6.15-27-386) 
Oct  5 17:05:42 threeve kernel: [17179756.588000] EIP is at allocate_init_mdl+0x1a2/0x370 [ndiswrapper]
Oct  5 17:05:42 threeve kernel: [17179756.588000] eax: 00000000   ebx: 00000000   ecx: 0000000b   edx: 0000002c
Oct  5 17:05:42 threeve kernel: [17179756.588000] esi: 0000002c   edi: 00000000   ebp: 00000000   esp: dfb6bbe8
Oct  5 17:05:42 threeve kernel: [17179756.588000] ds: 007b   es: 007b   ss: 0068
Oct  5 17:05:42 threeve kernel: [17179756.588000] Process khubd (pid: 1948, threadinfo=dfb6a000 task=dfb0e030)
Oct  5 17:05:42 threeve kernel: [17179756.588000] Stack: 00000000 f765c6c0 00004000 dfb6bc30 f8c2244d f54c0000 00004000 004c0000 
Oct  5 17:05:42 threeve kernel: [17179756.588000]        00000000 f8c92566 f54c0000 00004000 00000000 00000000 00000000 f6bff650 
Oct  5 17:05:42 threeve kernel: [17179756.588000]        00000000 00000001 dfb6bc44 f8c93403 f73ede00 f73ede00 00000000 dfb6bc58 
Oct  5 17:05:42 threeve kernel: [17179756.588000] Call Trace:
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [pg0+947881037/1069368320] IoAllocateMdl+0x1d/0x60 [ndiswrapper]
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [pg0+947849040/1069368320] NdisInitializeTimer+0x0/0x30 [ndiswrapper]
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [schedule+790/1680] schedule+0x316/0x690
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [pg0+947902312/1069368320] miniport_init+0x88/0x110 [ndiswrapper]
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [pg0+947888709/1069368320] pdoDispatchPnp+0x55/0x110 [ndiswrapper]
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [pg0+947880025/1069368320] IofCallDriver+0x29/0x50 [ndiswrapper]
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [pg0+947910481/1069368320] ndis_start_device+0x11/0x5b0 [ndiswrapper]
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [pg0+947880586/1069368320] IoSyncForwardIrp+0x4a/0x80 [ndiswrapper]
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [pg0+947910229/1069368320] NdisDispatchPnp+0xf5/0x120 [ndiswrapper]
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [pg0+947880025/1069368320] IofCallDriver+0x29/0x50 [ndiswrapper]
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [pg0+947888488/1069368320] IoSendIrpTopDev+0x78/0xd0 [ndiswrapper]
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [pg0+947870022/1069368320] KeInitializeEvent+0x16/0x20 [ndiswrapper]
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [pg0+947889285/1069368320] pnp_start_device+0x35/0x90 [ndiswrapper]
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [pg0+947890318/1069368320] wrap_pnp_start_device+0xfe/0x140 [ndiswrapper]
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [pg0+947890755/1069368320] wrap_pnp_start_usb_device+0x93/0xc0 [ndiswrapper]
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [sysfs_new_dirent+24/96] sysfs_new_dirent+0x18/0x60
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [sysfs_make_dirent+26/128] sysfs_make_dirent+0x1a/0x80
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [sysfs_add_file+62/96] sysfs_add_file+0x3e/0x60
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [pg0+944685239/1069368320] usb_probe_interface+0x67/0x90 [usbcore]
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [driver_probe_device+59/192] driver_probe_device+0x3b/0xc0
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [__device_attach+0/16] __device_attach+0x0/0x10
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [bus_for_each_drv+72/128] bus_for_each_drv+0x48/0x80
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [device_attach+84/96] device_attach+0x54/0x60
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [__device_attach+0/16] __device_attach+0x0/0x10
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [bus_add_device+33/160] bus_add_device+0x21/0xa0
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [device_add+221/320] device_add+0xdd/0x140
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [pg0+944720893/1069368320] usb_set_configuration+0x21d/0x4b0 [usbcore]
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [pg0+944695915/1069368320] usb_new_device+0xfb/0x190 [usbcore]
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [pg0+944701382/1069368320] hub_port_connect_change+0x306/0x450 [usbcore]
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [pg0+944689910/1069368320] clear_port_feature+0x36/0x40 [usbcore]
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [pg0+944702382/1069368320] hub_events+0x29e/0x470 [usbcore]
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [pg0+944702848/1069368320] hub_thread+0x0/0x100 [usbcore]
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [pg0+944702869/1069368320] hub_thread+0x15/0x100 [usbcore]
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [autoremove_wake_function+0/64] autoremove_wake_function+0x0/0x40
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [kthread+147/160] kthread+0x93/0xa0
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [kthread+0/160] kthread+0x0/0xa0
Oct  5 17:05:42 threeve kernel: [17179756.588000]  [kernel_thread_helper+5/16] kernel_thread_helper+0x5/0x10
Oct  5 17:05:42 threeve kernel: [17179756.588000] Code: 50 14 f7 c2 00 00 ff 0f 75 0b 9c 58 f6 c4 02 0f 85 04 01 00 00 b0 03 80 f9 01 0f 86 65 01 00 00 89 f1 c1 e9 02 31 c0 89 df 89 f2 <f3> ab f6 c2 02 74 02 66 ab f6 c2 01 74 01 aa c7 03 00 00 00 00 
Oct  5 17:05:45 threeve udevd-event[5355]: wait_for_sysfs: waiting for '/sys/devices/pci0000:00/0000:00:02.1/usb2/2-2/2-2:1.0/bus' failed
 

```

---

### Post by javaJake on 2006-10-05
> **markopolo12 said:**
> i installed ndiswrapper v 1.24 from ndiswrapper.sourceforge.net

Hmmm... try ndiswrapper v1.23 (stable version). This looks like a bug, and I'd report it:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Bugs](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Bugs)

Unfortunately, I cannot help you any farther. Googling shows that others got this as well, and have decided on the fact that it is a bug. I am really sorry.

---

### Post by markopolo12 on 2006-10-05
FANTASTIC!
I tried v1.23 and it works perfectly. thanks for all your help javaJake.

---

### Post by javaJake on 2006-10-07
> **markopolo12 said:**
> FANTASTIC!
I tried v1.23 and it works perfectly. thanks for all your help javaJake.

Be warned - v1.23 may crash. If you suddenly lose internet connection, check to be sure that wrap_wq isn't taking up CPU. If it is, send me a copy of your /var/log/syslog file. I'm working on this bug.

---

### Post by janekw on 2006-10-13
It's been a great help - the solution worked flawlessly. Congratulations:)

---

### Post by chefjames on 2006-10-14
Finally got this to work.  It took four tries and I am not exactly sure why it woked this time and not the others.  The main different thing I did was to use the file browser to copy every file I could find from 
     the unzipped F5D7051.exe and 
     the unshielded .CAB files
     and the unzipped WUSB54GS_20050428.exe
into the MyDrivers folder.  If there was a sub-folder I moved the contents of that into the main MyDrivers folder too.  

This seemed to work excellently.  The first time I ran "ndiswrapper -l" I got a driver present message.  I did not even have to install the .sys files manually.  Hopefully this will not kill my system and maybe it will be helpfull for someone else having trouble like I was.

---

### Post by javaJake on 2006-10-14
> **chefjames said:**
> Finally got this to work.  It took four tries and I am not exactly sure why it woked this time and not the others.  The main different thing I did was to use the file browser to copy every file I could find from 
     the unzipped F5D7051.exe and 
     the unshielded .CAB files
     and the unzipped WUSB54GS_20050428.exe
into the MyDrivers folder.  If there was a sub-folder I moved the contents of that into the main MyDrivers folder too.  

This seemed to work excellently.  The first time I ran "ndiswrapper -l" I got a driver present message.  I did not even have to install the .sys files manually.  Hopefully this will not kill my system and maybe it will be helpfull for someone else having trouble like I was.

Can you explain this in more detail or in a step by step format, so I may integrate this into the HOWTO?

What device are you using?

---

### Post by chefjames on 2006-10-18
Here is a more in-depth explanation of what I did to get things working.  This is pretty long and there is probably a simpler way than what worked for me.  Maybe there is some helpful info burried in here somewhere.  I am using an old Micron Trek II laptop with a pentium II processor.  Ubuntu is the only OS on the machine.  A virus killed Windows and I refused to pay more for fixing the OS than I paid for the computer.  I am using wusb54gs v1.  

1) I started with a new install of Ubuntu from the Alternate Install CD.  I chose to partition the whole drive as linux and answered yes to all prompts during the process.

2) Step 1 of your howto foiled me.  I could not figure out the ‘uname -r’ part of the code.  What did work for me was going  into System>Administration>Synaptics Package Manager and selecting all the packages that are mentioned in the code.
cpp
gcc
build-essential
linux-headers (I chose two packages: linux-headers-2.6.15-26 and linux-headers-2.6.15-26-386)
I answered yes to any prompts and requests to add more packages.  Fortunately for me I had a pcmcia card that was allowing me internet access because some things had to be downloaded.
I can’t remember if rebooted the computer at this time or not, but I did whatever I was prompted to do.  I think I rebooted.

3) To get ndiswrapper I downloaded the attachment from your howto and let the Archive Manager extract it.  I had to use the File Browser to find the file.  I then switched into a terminal and changed into the ndiswrapper folder.  Running the code worked as stated in the howto.  Only one thing was different from your instructions.  To remove the invalid directory I had to use the code: sudo rm -Rf /........
not the code as written: sudo rm -r /........

4) Even though I had the attachment from the howto I proceeded as if I did not.  I followed the link to belkin.com and downloaded the F5D7051.exe file.  I allowed the Archive Manager to extract it to my home folder.

5) I followed the howto for getting unshield and unshielded the two .CAB files.  

6) I followed the link in the howto to get the Linksys files and let the Archive Manager extract the files for me into my home folder.

7) In the terminal I made the MyDrivers folder.  I don’t know if it matters, but I made it a sub-folder of the 2Kdriver folder.  So my final code for this step was
code: sudo mkdir /home/james/2Kdriver/MyDrivers

8) My next step was all done using the File Browser.  I opened two File Browser windows.  I started in Places>Home Folder and found all the files from my steps 4,5, and 6 and drag and dropped everything into the MyDrivers folder.  If there was a sub-folder of any of the files from steps 4,5,6, I opened them and dragged their contents to the MyDrivers folder too.  For example:
the folder WUSB54GS_20050428 had the sub-folders Drivers, Image, and Utility.  I opened the Drivers folder and dragged the files I found there into the MyDrivers folder.  I did the same with Image and Utility.  Here is a complete list of the files that ended up in the MyDrivers folder.  I am sure that some of them are unnecessary, but at the time I was not taking any chances on leaving anything out.

Folder WUSB54GS_20050428 
AUTORUN.INF
CHANGE.WAV
CLICK.WAV
data1.cab
data1.hdr
data2.cab
EXIT.WAV
GEMWEP.DLL
ikernel.ex_
layout.bin
libeay32.dll
License_EN.rtf
Linksys.ico
Quick Installation for Windows 2000 and XP.pdf
RNDISMPK.sys
Security.dll
SELECT.WAV
Setup.exe
Setup.ini
Setup.inx
SetupWUSB54GS_US.dll
SetupWUSB54GS_US.ini
ssleay32.dll
START.WAV
tmp.bmp
usb8023k.sys
Wlan.ini
WUSB54GS.cat
WUSB54GS.inf
WUSB54GS_20050428.exe
WUSB54GS ver.1 Release Note 20050428 .txt

9) Back in the terminal I got into MyDrivers where I stayed for the rest of the process.  Step 3 - Installing the drivers says to run the code
sudo ndiswrapper -i WUSB54GS.inf
which worked.  I got a lot of text on the screen about how it was working.

10) The next code: “ ndiswrapper -l ”   gave me the answer  
wusb54gs			driver installed
Because I got no error messages and the driver seemed to be valid, I ran “ ls /etc/ndiswrapper “
and got “wusb54gs”

11) Everything looked too good to be true, but I ran 
sudo modprobe ndiswrapper
and got a bunch of text that made it look like it was working.  At least I got no error messages.

12) I plugged in the device and ran the code “top” and couldn’t find khubd at all.  So I tried connecting to the internet without success.

13) The last thing I did was go to System>Administration>Networking and clicked on Wireless connection “wlan0" and clicked on the Properties button.  I selected the signal I wanted and clicked ‘OK’ and was then able to surf the web.

14) I have had no problems since then.  I can plug and unplug the device at will.:D

---

### Post by javaJake on 2006-10-18
OK, so you used the drivers from the CAB, not the attachment... I'll look into using those drivers instead. Thanks for your input!

Oh, BTW, you have yet to tell me what the Model your device is. :)

---

### Post by chefjames on 2006-10-19
Unless I am mistaken I am using the v1 device.  All I could find on the sticker on the bottom said "Model WUSB54GS".  If this is not what you are looking for let me know and I will try to find out for you.

---

### Post by javaJake on 2006-10-20
> **chefjames said:**
> Unless I am mistaken I am using the v1 device.  All I could find on the sticker on the bottom said "Model WUSB54GS".  If this is not what you are looking for let me know and I will try to find out for you.

That is it. Thanks.

**Edit:** Ah, I see that you mentioned the device in your long post. My bad. :)

Also, I put your post in my HOWTO, in the Troubleshooting section at the bottom, until I've fully parsed it out. Thanks for your time!!!

**Another Edit:** OK, never mind. I asked "what is your device" *before* you made your long post with your device in it. :D

---

### Post by javaJake on 2006-10-21
> **chefjames said:**
> 2) Step 1 of your howto foiled me.  I could not figure out the &#8216;uname -r&#8217; part of the code.  What did work for me was going  into System>Administration>Synaptics Package Manager and selecting all the packages that are mentioned in the code.
cpp
gcc
build-essential
linux-headers (I chose two packages: linux-headers-2.6.15-26 and linux-headers-2.6.15-26-386)Ah, yes, that's my fault. I'll fix that up...

> **chefjames said:**
> 3) To get ndiswrapper I downloaded the attachment from your howto and let the Archive Manager extract it.  I had to use the File Browser to find the file.  I then switched into a terminal and changed into the ndiswrapper folder.  Running the code worked as stated in the howto.  Only one thing was different from your instructions.  To remove the invalid directory I had to use the code: sudo rm -Rf /........
not the code as written: sudo rm -r /........I'll change this in the HOWTO as well.

> **chefjames said:**
> 4) Even though I had the attachment from the howto I proceeded as if I did not.  I followed the link to belkin.com and downloaded the F5D7051.exe file.  I allowed the Archive Manager to extract it to my home folder.I think this is the key to your success. In everything else you followed the HOWTO except for this one spot. What I'll do, then, is use the drivers from the EXE from the website instead of the disk I got. Once I've compiled a new attachment, I'd be really happy if you could test it for me to make sure all is well. :)


Thanks so much for your input! I really appreciate it!

---

### Post by javaJake on 2006-10-25
**_Attention Users Who Have Successfully Used this HOWTO_**

I will be upgrading to Edgy to get ahead of the official release, so I can work out any bugs that may pop up for this HOWTO. Unless you know how to use Ubuntu forum's and Google's search functions to your advantage, _do not upgrade_. According to my experiences so far, there will probably be one or two bugs to work out!

At the same time I upgrade this HOWTO to Edgy, I will also integrate chefjames' instructions and drivers.

I'll make another announcement here when the upgrade is complete.

---

### Post by javaJake on 2006-10-28
**_Edgy is now Supported!_**
That's right! Edgy has been tested, and will work with the WUSB54GS! Currently, however, you have to manually configure it at startup, but that'll soon change with a startup script.

So if you've been aching to upgrade, now's the time! :D

---

### Post by chefjames on 2006-10-29
Thanks for the credit but I think it was undue.  I think my method for getting this to work should be removed from the howto.  I have tried unsuccessfully to follow my own instructions several times now.  Most noteably the Archive Manager is not extracting the files like I remember it doing.  I can move the files around within the File Browser, but have had no luck actually getting the drivers even installed.  If I can't reproduce the results it is very doubtful that someone else can. :( :( 

I have used both the "with the attachment" and the "without the attachement" methods successfully several times now.:D 

I still find the Desktop File Browser very useful for keeping track of where the files are and what directory I am in. Dragging the file icon into the terminal rather that typing everything works fine for me.  That way all the relevent pathname info is there and I don't have remember it all so I can type it correctly.  I remain hopeful that there is still a non-terminal way to do most of this, but I am not going to cry if there is not.  I Like the Terminal.

---

### Post by javaJake on 2006-10-30
> **chefjames said:**
> Thanks for the credit but I think it was undue.  I think my method for getting this to work should be removed from the howto.  I have tried unsuccessfully to follow my own instructions several times now.  Most noteably the Archive Manager is not extracting the files like I remember it doing.  I can move the files around within the File Browser, but have had no luck actually getting the drivers even installed.  If I can't reproduce the results it is very doubtful that someone else can. :( :( 

I was wondering what happened... I was going to tell you before that I wasn't going to include your drivers, since I couldn't reproduce it myself. :D

I will update the attachment with the .sys files included, however, to make the WITHOUT ATTACHMENT part disappear forever. *muhahahaha*

---

### Post by javaJake on 2006-11-05
**_Updated Attachment with New NDisWrapper_**
I highly recommend everyone update their ndiswrapper version to v1.27 or higher, as it fixes a few bugs that you might encounter. The attachment's been updated with the new ndiswrapper.

Be sure to run "sudo make uninstall" while in the old version's folder that you were in when you compiled before installing the new one.

---

### Post by mrfoobar on 2006-11-25
Has anyone notified the developers about the side effects of the usb power limiting feature?

---

### Post by javaJake on 2006-11-25
> **mrfoobar said:**
> Has anyone notified the developers about the side effects of the usb power limiting feature?

I am fully planning on doing this, believe me! However, they won't remove this "feature" anytime soon, I fear. I don't think enough users are being affected.

What I'd like is some sort of filter where I could punch in udev-like rules that tell the kernel what USB modules shouldn't be limited on power.


I have found an excellent temporary solution that is really clean, simple, and works really really well. Bear with me as I get it posted - I got a job, so time is limited for me.


If you would like, open a bug for me, post the link here, and I'll add my comments. That would be great!

---

### Post by mrfoobar on 2006-11-25
I've been having problems with my computer randomly freezing up after connecting to the internet. 

But I think that might be related to the fact that I too made the stupid mistake of thinking ndiswrapper 1.8 was a newer version than the one you included. I'm going to try to use your version and see if it solves my problem.

---

### Post by javaJake on 2006-11-25
**_Edgy Support Complete, and NetworkManager added_**
I've added a NetworkManager section to help you set up NetworkManager. It isn't hard, and yes, HOWTOs have been set up elsewhere about this, but they never mention that you have to *completely* remove all interfaces but lo from the /etc/network/interfaces file.

Also, all Edgy users who used this HOWTO before today, please follow the new Edgy instructions I punched in. It'll make your life twice as easy. :)

---

### Post by jcda on 2006-12-06
Thank you so much for this thread.  I have a pretty old computer and was grateful when I could get the WUSB54GS working in M$ windows - this was a major obstacle for me in switching to Linux until I found this forum.  

Strangely, I am kind of on the bleeding edgy of this thread.  I am using Edgy with the previous solution that you posted.  For me, this means I run the following command every time I boot my computer:

```
echo -n 1 > /sys/devices/pci0000:00/0000:00:04.2/usb1/1-2/bConfigurationValue
```

I love the idea of adding the udev rules file, but it does nothing for me.  I've tried the following algorithm:
[LIST=1]
[*]unplug the WUSB54GS
[*]reboot
[*]add 99-custom.rules
[*]reboot
[*]plug in the WUSB54GS
[/LIST]
- no luck. I still have to run the previous script.  Here is the relevant output from lshal (after I run the previous script to make it work):

udi = '/org/freedesktop/Hal/devices/usb_device_13b1_e_1111'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_13b1_e_1111'  (string)
  linux.subsystem = 'usb'  (string)
  linux.hotplug_type = 1  (0x1)  (int)
  usb_device.bus_number = 1  (0x1)  (int)
  usb_device.can_wake_up = false  (bool)
  usb_device.is_self_powered = false  (bool)
  usb_device.version_bcd = 512  (0x200)  (int)
  usb_device.speed_bcd = 4608  (0x1200)  (int)
  usb_device.serial = '1111'  (string)
  usb_device.linux.device_number = 3  (0x3)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 6  (0x6)  (int)
  info.product = 'Linksys Wireless-G USB Network Adapter with SpeedBooster'  (string)
  usb_device.product = 'Linksys Wireless-G USB Network Adapter with SpeedBooster'  (string)
  info.vendor = 'Linksys'  (string)
  usb_device.vendor = 'Linksys'  (string)
  usb_device.product_id = 14  (0xe)  (int)
  usb_device.vendor_id = 5041  (0x13b1)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.device_class = 2  (0x2)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.2/usb1/1-2'  (string)
  info.linux.driver = 'usb'  (string)
  info.bus = 'usb_device'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_04_2'  (string)
  linux.sysfs_path_device = '/sys/devices/pci0000:00/0000:00:04.2/usb1/1-2'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.2/usb1/1-2'  (string)


I've notice that it looks like you have an extra single-quote at the end of the 99-custom.rules script:

```
BUS=="usb", SYSFS{idProduct}=="000e", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c echo 1 > /sys/$devpath/device/bConfigurationValue'"
```

(just before the last double-quote).  I don't think the extra single-quote should be there.  I did try this with and without that quote just to be sure.  What else am I missing to make this work?

Thanks again.

---

### Post by javaJake on 2006-12-09
> **jcda said:**
> I've notice that it looks like you have an extra single-quote at the end of the 99-custom.rules script:

```
BUS=="usb", SYSFS{idProduct}=="000e", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c echo 1 > /sys/$devpath/device/bConfigurationValue'"
```

(just before the last double-quote).  I don't think the extra single-quote should be there.  I did try this with and without that quote just to be sure.

Thank you so much for mentioning this! I realized I missed a single quote. Here's the correct line:

```
BUS=="usb", SYSFS{idProduct}=="000e", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"
```

I was having the same issue as you on my machine, but this did it. Thanks. :)

---

### Post by Jay-Jay on 2006-12-09
Works perfectly with a v2 adapter.

Somethings to point out. I use Edgy so I had to use your power limit fix. When I tried the first time, it didn't work so I unplugged the adapter and changed the product id (SYSFS{idProduct}=="000e" in the 99-custom.rules to (SYSFS{idProduct}=="0014" and it worked. Is that product id for v2 users only or is it something that you need to fix.

```
BUS=="usb", SYSFS{idProduct}=="000e", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"
```

to

```
BUS=="usb", SYSFS{idProduct}=="0014", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"
```

OK, before installing the Network Manager, I was hooked up to the internet,  but then after I installed the Network Manager, i was trying to browse but it didn't work so i restarted as you stated. After I restart, i see the network manager, and when i left click on it, all i see is a disabled grayed out "Wired Connection" or something like that. Nothing about Wireless. So I checked System>Admin>Networking. I now realized that my Wireless Connection wasn't even there. So i opened up a terminal and typed in
```
sudo depmod -a
sudo modprobe ndiswrapper
```

Now that brought back the Wireless Connection to System>Admin>Networking. but now the Network Manager seemed to have disappeared.

So I tried the command 
```
sudo ndiswrapper -m
```

which gave me "modprobe config already contains alias directive"


So I rebooted to see if it will load up at boot time, but the same problem was recreated. Network Manager in taskbar, no Wireless Connection in System>Admin>Networking.

I don't know what else to do. Any Suggestions???

---

### Post by javaJake on 2006-12-09
> **Jay-Jay said:**
> Works perfectly with a v2 adapter.

Somethings to point out. I use Edgy so I had to use your power limit fix. When I tried the first time, it didn't work so I unplugged the adapter and changed the product id (SYSFS{idProduct}=="000e" in the 99-custom.rules to (SYSFS{idProduct}=="0014" and it worked. Is that product id for v2 users only or is it something that you need to fix.

```
BUS=="usb", SYSFS{idProduct}=="000e", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"
```

to

```
BUS=="usb", SYSFS{idProduct}=="0014", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"
```OK, thank you very much! That makes total sense!

I've taken a look at what you've said, and there's multiple things going on here that make this slightly confusing. I've broken it down into each chunk.

> **Jay-Jay said:**
> OK, before installing the Network Manager, I was hooked up to the internet,  but then after I installed the Network Manager, i was trying to browse but it didn't work so i restarted as you stated. After I restart, i see the network manager, and when i left click on it, all i see is a disabled grayed out "Wired Connection" or something like that. Nothing about Wireless.OK, there are one of two issues going on here. Either you didn't *completely* remove every entry or the wireless device wasn't loaded.

> **Jay-Jay said:**
> So I checked System>Admin>Networking. I now realized that my Wireless Connection wasn't even there.That's because you removed it from your network configuration file. Ubuntu's Networking settings are useless once you use NetworkManager. This also eliminates one of the above problems - your NetworkManager is managing your wireless stuff, but there's no device to manage.

> **Jay-Jay said:**
> So i opened up a terminal and typed in
```
sudo depmod -a
sudo modprobe ndiswrapper
```This was the right thing to do, but I'll bet a million you had the device plugged in while you did this. I forgot to mention this in the HOWTO, but if you run modprobe ndiswrapper on Edgy with the device plugged in, your kernel crashes. A restart is necessary to get the system back to its normal state.

> **Jay-Jay said:**
> Now that brought back the Wireless Connection to System>Admin>Networking. but now the Network Manager seemed to have disappeared.The icon won't appear if the underlying program has crashed. This further tells me that you did crash your kernel and/or NetworkManager when you ran the modprobe ndiswrapper command.

> **Jay-Jay said:**
> So I tried the command 
```
sudo ndiswrapper -m
```

which gave me "modprobe config already contains alias directive"
OK... good good...

> **Jay-Jay said:**
> So I rebooted to see if it will load up at boot time, but the same problem was recreated. Network Manager in taskbar, no Wireless Connection in System>Admin>Networking.OK, so basically, nothing changed, right?

> **Jay-Jay said:**
> I don't know what else to do. Any Suggestions???You better believe I have some suggestions. :)

OK, here's a breakdown of what happened:
[list][*]You did all the installation steps correctly.[*]However, the drivers (ndiswrapper) weren't loaded, so NetworkManager didn't know you really had a wireless device plugged in, and thus, no wireless networks in NetworkManager's menu.[*]You ran "sudo modprobe ndiswrapper" with the device plugged in, I assume, and the NetworkManager icon disappeared. Basically, part of the computer crashed.[*]You rebooted your computer, which was exactly the right thing to do. Again the drivers were not loaded, so NetworkManager, just like you said, didn't seem to be managing your wireless device.[/list]

Here's what you are going to do to correctly load ndiswrapper:
[LIST=1][*]Restart your computer with the wireless device unplugged, and wait until you see your login screen before continuing.[*]Run the normal depmod and ndiswrapper commands you mentioned.[*]Now plug in your device, and watch NetworkManager take over.[/LIST]

Now, what helps me have ndiswrapper loaded on startup every time is to add "options ndiswrapper if_name=wlan0" at the end of the /etc/modprobe.d/options file, though you'd still have to keep your device unplugged until you see the login screen.

---

### Post by Jay-Jay on 2006-12-09
> 
Now, what helps me have ndiswrapper loaded on startup every time is to add "options ndiswrapper if_name=wlan0" at the end of the /etc/modprobe.d/options file, though you'd still have to keep your device unplugged until you see the login screen.

Is there any way around having to unplug the device before the login screen. Because I don't want to always be unplugging and plugging back in the adapter.

---

### Post by javaJake on 2006-12-10
> **Jay-Jay said:**
> Is there any way around having to unplug the device before the login screen. Because I don't want to always be unplugging and plugging back in the adapter.

As far as I know, no. I'm making a bug report to send to the ndiswrapper folks, so we'll hopefully get all this sorted out.


Hold on a second. You may not have this issue. I am not completely sure. The best way to tell is to...

[LIST=1][*]Remove the file /etc/modprobe.d/ndiswrapper[*]Remove the "options" line I mentioned from /etc/modprobe.d/options file if you added that.[*]Restart your computer, and login.[*]Plug in the device, then modprobe ndiswrapper.[*]If you see a kernel "oops" at the end of /var/log/syslog and NetworkManager disappears or won't work with wireless, then you've got this issue. Otherwise you don't have to worry about having your device unplugged.[/LIST]

To undo the changes you made above, restart your computer (to get your entire kernel running again), and run:
```
sudo ndiswrapper -m
```

...and punch in "options ndiswrapper if_name=wlan0" back into /etc/modprobe.d/options if you had that before.

---

### Post by Jay-Jay on 2006-12-10
> **javaJake said:**
> 
Now, what helps me have ndiswrapper loaded on startup every time is to add "options ndiswrapper if_name=wlan0" at the end of the /etc/modprobe.d/options file, though you'd still have to keep your device unplugged until you see the login screen.

I don't know about this, but I didn't do it. What i did, since ndiswrapper -m doesn't automatically load the ndiswrapper module at boot time, is

```
sudo gedit /etc/modules
```

and add this to the last line.

```
ndiswrapper
```

Now I restarted and left my device plugged in, not unplugging it at all. I logged in and the Network Manager was in the taskbar, which was connected automatically, so i guess you can test this and add it to the HOWTO.

---

### Post by jrickard on 2006-12-10
Jay-Jay

I just have to write a somewhat offtopic message here.  I have a second home in Naples Florida.  Unfortunatly, I don't get down as often as I'd like.  I do have a little Linksys network on cable with a Linksys Wireless-G USB Network Adapter version 2 on a PC.

The PC is a few years old and a little tired under the load of Windoze XP SP2.  But it connected to a wireless keyboard and the Internet via wireless quite well.

I came down last Tuesday and decided to try a dual boot with Ubuntu 6.10 which I've been having good success with up in Missouri.

It has been a nightmare just getting it up and running and working with the b luetooth keyboard and mouse.  And the Wireless G adapter has been so terrifically bad, that I have obsessed on it.  This HOWTO thread is so detailed, I was certain it had to work, but it hasn't worked at all for me.  

I got NDISWRAPPER 1.31 in source, did successfully compile it, got the drivers both from the disk and the HOWTO attachment.  I even partitioned a FAT32 to move the two .SYS files from Windows to Ubuntu.  NDISWRAPPER loaded and found the device quite early in the game.  But nothing in SYSTEM - ADMIN- NETWORKING and nothing using Network Manager.

The problem of course was the USB power issue under edgy.  Finally this morning your mod to 0014 from 000e got me a light on the adapter.  This is the kind of thing that is just KILLING LINUX.  000e IS 0014.  000e is hex for 0014 decimal.  It just shouldn't matter.  It does.  WIth 000e, no joy.
Same line with 0014 - big bright green light.

I'll give you another example.  I STILL couldn't link up with anything.  I just added "ndiswrapper" to the mod file per your instructions of 3 hours ago and restarted the machine.  Network Manager now lists the device and two wireless networks.  Mine is labelled 2725medallist and my neighbors is labelled NETGEAR (the default I'm sure).  Mine is my street address in case any of the war dialers are totally lost or confused.  Neither had any security.  Oddly, I still couldn't connect to my network.  So in confusion and just blindly trying stuff, I tried the neighbors NETGEAR network.  It hooked up immediately and I'm on the network.  (OK, the WRONG network, but whatever).

You guessed it didn't you.  I went to my router and removed the 2725 from the broadcast SSID.  Now I can hook up to "medallist" just fine even though "2725medallist" was just a bridge too far.

Bottom line is that I have actually been following you guys in very nearly REAL time as this how to has evolved from last Tuesday.  And my first joy is this Sunday morning.  I would have contributed, but I have no idea what I'm doing.  I'm just blindly entering what you two tell me into files you guys specify. 

I mostly find Linux and the associated forums hopelessly lost dazed and confused.  And while I love the concept of Linux, the incessant arcana (no leading digits in SSIDs????) is just brutally discouraging. This was a very positive experience in this forum.  You guys are good.

Thanks for the excellent and persistent work on what I consider an important feature.  Linux just HAS to be beaten into wireless connectivity if it is to be used at all.

With a little cleanup, this will be a GREAT HOWTO.

Jack Rickard

---

### Post by Jay-Jay on 2006-12-10
glad to help. and thanks for posting. ppl like you make other ppls lives easier by posting problems and solutions to them.

i guess that javajake can also put that the leading digits in the SSID won't work. 

Once everybody can finally just breeze thru the HOWTO, i guess javajake will stop adding fixes and bugs and then he will clean it up to the best of his ability.

As a matter of fact, i think this HOWTO may work with just almost any adapter. If you just get the correct drivers for your device, and just change up some of the HOWTO a bit it will work.

To get drivers for your device, just search for your device [here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List").

---

### Post by javaJake on 2006-12-10
> **jrickard said:**
> The problem of course was the USB power issue under edgy.  Finally this morning your mod to 0014 from 000e got me a light on the adapter.  This is the kind of thing that is just KILLING LINUX.  000e IS 0014.  000e is hex for 0014 decimal.  It just shouldn't matter.  It does.  WIth 000e, no joy.
Same line with 0014 - big bright green light.I fully agree with you on the fact that Linux isn't going anywhere fast. I think Linux is just way too complicated for its own good. The "0014" thing makes some sense, though. udev looks through its rules, sees our WUSB54GS rule and says "hey, does 000e match 0014?". Of course, it doesn't. What you can do to push Linux that one extra step is report this as a bug.

> **jrickard said:**
> I'll give you another example.  I STILL couldn't link up with anything.  I just added "ndiswrapper" to the mod file per your instructions of 3 hours ago and restarted the machine.  Network Manager now lists the device and two wireless networks.  Mine is labelled 2725medallist and my neighbors is labelled NETGEAR (the default I'm sure).  Mine is my street address in case any of the war dialers are totally lost or confused.  Neither had any security.  Oddly, I still couldn't connect to my network.  So in confusion and just blindly trying stuff, I tried the neighbors NETGEAR network.  It hooked up immediately and I'm on the network.  (OK, the WRONG network, but whatever).Again, push Linux forward and help us all by making a bug report, and posting a link here.

> **jrickard said:**
> I mostly find Linux and the associated forums hopelessly lost dazed and confused.  And while I love the concept of Linux, the incessant arcana (no leading digits in SSIDs????) is just brutally discouraging. This was a very positive experience in this forum.  You guys are good.Thanks. :D Oh, and about crappy support, don't touch the IRC channel #ubuntu.

> **jrickard said:**
> Thanks for the excellent and persistent work on what I consider an important feature.  Linux just HAS to be beaten into wireless connectivity if it is to be used at all.Agreed. Please realize though that, practically, Linux will always be around 1-2 years behind the rest of the world, because Linux gurus have to first find an interest in the new stuff, then make a driver for it.

> **jrickard said:**
> With a little cleanup, this will be a GREAT HOWTO.Ooo, you have any ideas? I'm _open_ to suggestions! In fact, if you want, I can PM you the entire HOWTO source so you can edit it directly and send me the changes. :)

---

### Post by javaJake on 2006-12-11
> **Jay-Jay said:**
> I don't know about this, but I didn't do it. What i did, since ndiswrapper -m doesn't automatically load the ndiswrapper module at boot time, is

```
sudo gedit /etc/modules
```

and add this to the last line.

```
ndiswrapper
```

Now I restarted and left my device plugged in, not unplugging it at all. I logged in and the Network Manager was in the taskbar, which was connected automatically, so i guess you can test this and add it to the HOWTO.

Holy smokes! This does work better! Thanks a million! I'll add this to the HOWTO when I have time. Then you won't even have to worry about kernel crashes. Yay. :D

---

### Post by javaJake on 2006-12-14
**_Feisty Is Now Support By This HOWTO_**
If you feel the urge to try the latest and greatest, know that at least your internet will work. :)

---

### Post by mrfoobar on 2006-12-19
It looks like somebody already reported this as a bug for another device:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/67848]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/67848")

---

### Post by javaJake on 2006-12-21
> **mrfoobar said:**
> It looks like somebody already reported this as a bug for another device:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/67848]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/67848")

I've added my comments. Thanks for posting this.

---

### Post by infol on 2006-12-29
thanks for this howto; after scourging th net for over 3 hours (! - believe me, i'm a restless sort of guy and was almost giving up..) 

i finally stumbled upon this one, and it worked (after some minor modifications..after all, i bought a belkin f5d7051 a couple of hours ago, not doing my homework beforehand thinking this one had a different chipset - the rt73...)

anyway, following this howto was pretty straight-forward, changing the wusb54g.inf for the bcmrndis.inf and then fiddling with the vendor/product-id's in the udev-rules mod to match my product.

however, i still have a small problem, which is the speed of my current setup (the f5d7051 together with an f5d7231); both are so-called 802.11g +...
albeight i don't give much for promises by manufacturers, these products basically slow down my internet experience to a halt - it's not that download-speeds are slow, but dns lookups take fooreeevveer, and on sites with ads from 15 different hosts it takes quite a while for the page to load

any ideas if there is a setting somewhere to tweak????

thanks again!! - much obliged   ;)

---

### Post by infol on 2006-12-29
duh;  sometimes you stare yourself blind so you don't see the obvious...
the router wanted to be my dhcp-server - of course it was slow to look up addresses..

thanks guys - now everything works as it should!

---

### Post by javaJake on 2006-12-30
> **infol said:**
> duh;  sometimes you stare yourself blind so you don't see the obvious...
the router wanted to be my dhcp-server - of course it was slow to look up addresses..

thanks guys - now everything works as it should!

Al-right! Glad to hear that! I was going to make a reply saying I didn't know a thing about what your problem, or what to check out first.

I'll probably post a new HOWTO or new "Tip" on these forums about the "no configuration chosen" message since this problem is so widespread.

---

### Post by orko3001 on 2007-01-01
Hi all,

I put in this code:

sudo apt-get install cpp gcc build-essential linux-headers-$(uname -r)

and get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
cpp is already the newest version.
gcc is already the newest version.
linux-headers-2.6.17-10-generic is already the newest version.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  debian-keyring gcc-4.1-doc lib64stdc++6 glibc-doc manpages-dev
  libstdc++6-4.1-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 7930kB of archives.
After unpacking 30.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main linux-libc-dev 2.6.17-10.33
  Temporary failure resolving 'gb.archive.ubuntu.com'
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main libc6-dev 2.4-1ubuntu12
  Temporary failure resolving 'gb.archive.ubuntu.com'
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main libstdc++6-4.1-dev 4.1.1-13ubuntu5
  Temporary failure resolving 'gb.archive.ubuntu.com'
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main g++-4.1 4.1.1-13ubuntu5
  Temporary failure resolving 'gb.archive.ubuntu.com'
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main g++ 4:4.1.1-6ubuntu3
  Temporary failure resolving 'gb.archive.ubuntu.com'
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main dpkg-dev 1.13.22ubuntu7
  Temporary failure resolving 'gb.archive.ubuntu.com'
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main build-essential 11.3
  Temporary failure resolving 'gb.archive.ubuntu.com'
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-libc-dev_2.6.17-10.33_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-libc-dev_2.6.17-10.33_i386.deb)  Temporary failure resolving 'gb.archive.ubuntu.com'
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12_i386.deb)  Temporary failure resolving 'gb.archive.ubuntu.com'
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.1-13ubuntu5_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.1-13ubuntu5_i386.deb)  Temporary failure resolving 'gb.archive.ubuntu.com'
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/g++-4.1_4.1.1-13ubuntu5_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/g++-4.1_4.1.1-13ubuntu5_i386.deb)  Temporary failure resolving 'gb.archive.ubuntu.com'
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.1.1-6ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.1.1-6ubuntu3_i386.deb)  Temporary failure resolving 'gb.archive.ubuntu.com'
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.22ubuntu7_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.22ubuntu7_all.deb)  Temporary failure resolving 'gb.archive.ubuntu.com'
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.3_i386.deb)  Temporary failure resolving 'gb.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@co-desktop:~# sudo apt-get install cpp gcc build-essential linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cpp is already the newest version.
gcc is already the newest version.
linux-headers-2.6.17-10-generic is already the newest version.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  debian-keyring gcc-4.1-doc lib64stdc++6 glibc-doc manpages-dev
  libstdc++6-4.1-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 7930kB of archives.
After unpacking 30.4MB of additional disk space will be used.

Do you want to continue [Y/n]? y
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main linux-libc-dev 2.6.17-10.33
  Temporary failure resolving 'gb.archive.ubuntu.com'
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main libc6-dev 2.4-1ubuntu12
  Temporary failure resolving 'gb.archive.ubuntu.com'
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main libstdc++6-4.1-dev 4.1.1-13ubuntu5
  Temporary failure resolving 'gb.archive.ubuntu.com'
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main g++-4.1 4.1.1-13ubuntu5
  Temporary failure resolving 'gb.archive.ubuntu.com'
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main g++ 4:4.1.1-6ubuntu3
  Temporary failure resolving 'gb.archive.ubuntu.com'
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main dpkg-dev 1.13.22ubuntu7
  Temporary failure resolving 'gb.archive.ubuntu.com'
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main build-essential 11.3
  Temporary failure resolving 'gb.archive.ubuntu.com'
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-libc-dev_2.6.17-10.33_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-libc-dev_2.6.17-10.33_i386.deb)  Temporary failure resolving 'gb.archive.ubuntu.com'
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12_i386.deb)  Temporary failure resolving 'gb.archive.ubuntu.com'
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.1-13ubuntu5_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.1-13ubuntu5_i386.deb)  Temporary failure resolving 'gb.archive.ubuntu.com'
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/g++-4.1_4.1.1-13ubuntu5_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/g++-4.1_4.1.1-13ubuntu5_i386.deb)  Temporary failure resolving 'gb.archive.ubuntu.com'
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.1.1-6ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.1.1-6ubuntu3_i386.deb)  Temporary failure resolving 'gb.archive.ubuntu.com'
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.22ubuntu7_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.22ubuntu7_all.deb)  Temporary failure resolving 'gb.archive.ubuntu.com'
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.3_i386.deb)  Temporary failure resolving 'gb.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?



I think this might have something to do with the fact I am not sure where to put the packages and if I should unzip them. :-k

---

### Post by orko3001 on 2007-01-01
Hang on - do I have to be online to install this? :confused:

---

### Post by Jake 2.0 on 2007-01-04
ok i think im an idiot. im new to linux and dont know much about anything of this OS. i download the attachment and save it to the desktop but when i try to run bunzip2 ndiswrapper-files.tar.bz2 it says the following

midnight@midnight-desktop:~$ bunzip2 ndiswrapper-files.tar.bz2
bunzip2: Can't open input file ndiswrapper-files.tar.bz2: No such file or directory.
so it feels like im lost before i begin.](*,) anyway if someone could point me inthe correct direction to go id greatly appreciate it.

---

### Post by javaJake on 2007-01-04
> **orko3001 said:**
> Hang on - do I have to be online to install this? :confused:

That's correct. Any packages it couldn't get you should download onto a CD or something like that, and transfer them to your computer.

---

### Post by javaJake on 2007-01-04
> **Jake 2.0 said:**
> ok i think im an idiot. im new to linux and dont know much about anything of this OS. i download the attachment and save it to the desktop but when i try to run bunzip2 ndiswrapper-files.tar.bz2 it says the following

midnight@midnight-desktop:~$ bunzip2 ndiswrapper-files.tar.bz2
bunzip2: Can't open input file ndiswrapper-files.tar.bz2: No such file or directory.
so it feels like im lost before i begin.](*,) anyway if someone could point me inthe correct direction to go id greatly appreciate it.

Do you know how to use the terminal? If not, visit this page: [http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal)

Move the ndiswrapper-files.tar.bz2 to your home directory, and that'll work. I'll be happy to lead you through the terminal errors like this one, but PM or IM me them instead for the sake of keeping the thread clean. :)

---

### Post by scottpledger on 2007-01-15
Has anyone gotten either of these to work on x86_64 machines??  I got this to work on my x86(just Fedora Core 6) and amd64 (Dual-boot Ubuntu 6.10 and Fedora Core 6 - worked on both using the files that darklord found with some tweaking) machine, but it seems to refuse to work on my x86_64 box.](*,)  Any help is greatly appreciated.  Also, I am relatively new to the Linux world (I've only been using it for about a year and a half) so if I have forgotten any relevant information, please don't hesitate to ask.  Oh, by the way...I'm not using the WUSB54GS.  Instead I'm using the WUSB54GSC, the same adapter that worked on the other two machines I tested.  Just exchange the '000e' or '0014' for '0026' and it works seamlessly (exept on my x86_64, of course).  Thanks for the wonderful how-to!!

---

### Post by Genotrius on 2007-01-15
After following through past Step 2 once, I encountered an error at the end of Step 3: after installing the two .sys files, ndiswrapper still told me that the wusb54gs driver was invalid. I looked in the troubleshooting, and the closest thing seemed to be the “Compiling ndiswrapper with gcc 4.1 or higher” part. Following your instructions, I forced the use of GCC 4.0, and got this:

GCC v4.0
```
user@ubuntu:~/ndiswrapper-files/ndiswrapper-1.28$ make
make -C driver
make[1]: Entering directory `/home/geno/ndiswrapper-files/ndiswrapper-1.28/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/geno/ndiswrapper-files/ndiswrapper-1.28/driver
/usr/src/linux-headers-2.6.17-10-generic/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-headers-2.6.17-10-generic/scripts/gcc-version.sh: line 12: gcc: command not found
make[2]: gcc: Command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/user/ndiswrapper-files/ndiswrapper-1.28/driver/crt.o
/bin/sh: gcc: not found
make[3]: *** [/home/user/ndiswrapper-files/ndiswrapper-1.28/driver/crt.o] Error 127
make[2]: *** [_module_/home/user/ndiswrapper-files/ndiswrapper-1.28/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/user/ndiswrapper-files/ndiswrapper-1.28/driver'
make: *** [all] Error 2

user@ubuntu:~/ndiswrapper-files/ndiswrapper-1.28$ sudo make install
make -C driver install
make[1]: Entering directory `/home/user/ndiswrapper-files/ndiswrapper-1.28/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/user/ndiswrapper-files/ndiswrapper-1.28/driver
/usr/src/linux-headers-2.6.17-10-generic/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-headers-2.6.17-10-generic/scripts/gcc-version.sh: line 12: gcc: command not found
make[2]: gcc: Command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/user/ndiswrapper-files/ndiswrapper-1.28/driver/crt.o
/bin/sh: gcc: not found
make[3]: *** [/home/user/ndiswrapper-files/ndiswrapper-1.28/driver/crt.o] Error 127
make[2]: *** [_module_/home/user/ndiswrapper-files/ndiswrapper-1.28/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/user/ndiswrapper-files/ndiswrapper-1.28/driver'
make: *** [install] Error 2
```
Ndiswrapper wasn't there when I went to the next step, not surprising. Then, I ran “sudo make uninstall,” just to make sure that there weren't any bits and peices left, reimplimented GCC 4.1, and ran the install again, for documentation:

GCC v4.1.2
```
user@ubuntu://home/geno/ndiswrapper-files/ndiswrapper-1.28$ make
make -C driver
make[1]: Entering directory `/home/user/ndiswrapper-files/ndiswrapper-1.28/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/geno/ndiswrapper-files/ndiswrapper-1.28/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: Leaving directory `/home/user/ndiswrapper-files/ndiswrapper-1.28/driver'
make -C utils
make[1]: Entering directory `/home/geno/ndiswrapper-files/ndiswrapper-1.28/utils'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/geno/ndiswrapper-files/ndiswrapper-1.28/utils'
user@ubuntu://home/user/ndiswrapper-files/ndiswrapper-1.28$ sudo make install
make -C driver install
make[1]: Entering directory `/home/user/ndiswrapper-files/ndiswrapper-1.28/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/geno/ndiswrapper-files/ndiswrapper-1.28/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
echo /lib/modules/2.6.17-10-generic/misc
/lib/modules/2.6.17-10-generic/misc
mkdir -p /lib/modules/2.6.17-10-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.17-10-generic/misc
/sbin/depmod -a 2.6.17-10-generic -b /
make[1]: Leaving directory `/home/user/ndiswrapper-files/ndiswrapper-1.28/driver'
make -C utils install
make[1]: Entering directory `/home/user/ndiswrapper-files/ndiswrapper-1.28/utils'
install -D -m 755 loadndisdriver /sbin/loadndisdriver
install -D -m 755 ndiswrapper /usr/sbin/ndiswrapper
install -D -m 755 ndiswrapper-buginfo /usr/sbin/ndiswrapper-buginfo

NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.
make[1]: Leaving directory `/home/user/ndiswrapper-files/ndiswrapper-1.28/utils'
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
user@ubuntu://home/user/ndiswrapper-files/ndiswrapper-1.28$ 
```
I've now undone all changes I made to my system from following this HOWTO (except for the “Getting device to work in Edgy” part, which I went ahead and did.)

---

### Post by javaJake on 2007-01-15
> **scottpledger said:**
> Has anyone gotten either of these to work on x86_64 machines??  I got this to work on my x86(just Fedora Core 6) and amd64 (Dual-boot Ubuntu 6.10 and Fedora Core 6 - worked on both using the files that darklord found with some tweaking) machine, but it seems to refuse to work on my x86_64 box.](*,)  Any help is greatly appreciated.  Also, I am relatively new to the Linux world (I've only been using it for about a year and a half) so if I have forgotten any relevant information, please don't hesitate to ask.  Oh, by the way...I'm not using the WUSB54GS.  Instead I'm using the WUSB54GSC, the same adapter that worked on the other two machines I tested.  Just exchange the '000e' or '0014' for '0026' and it works seamlessly (exept on my x86_64, of course).  Thanks for the wonderful how-to!!

x86_64 is not supported, as mentioned at the beginning of this HOWTO. It should be doable (the drivers for 64-bit exist), but people have been having issues with it (just like you). I think you should go to the ndiswrapper mailing list for this one.

Thanks for all the input - I enjoy it! :)

---

### Post by javaJake on 2007-01-15
> **Genotrius said:**
> After following through past Step 2 once, I encountered an error at the end of Step 3: after installing the two .sys files, ndiswrapper still told me that the wusb54gs driver was invalid.

Funny you should mention this - I was just debugging this with another guy with the same exact issue. I'll bet that when you attempted to install the drivers by running "ndiswrapper -i WUSB54GS.inf" you encountered an error. You did what the HOWTO said to do - copy over .sys files to the wusb54gs folder. However, ndiswrapper was probably still missing the WUSB54GS.inf file and an automatically-generated configuration file.


I still don't know what exactly is keeping ndiswrapper from installing the drivers, but a workaround is in progress. I'll keep you posted. In the mean-time, try downloading the latest _stable_ version of ndiswrapper here, and see if it'll work:
[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

To install this version, uninstall the v1.28 one you have installed now by running "make uninstall", and then follow Step 2 of the HOWTO, extracting the download from SourceForge instead of the attachment.

---

### Post by scottpledger on 2007-01-15
> **javaJake said:**
> x86_64 is not supported, as mentioned at the beginning of this HOWTO. It should be doable (the drivers for 64-bit exist), but people have been having issues with it (just like you). I think you should go to the ndiswrapper mailing list for this one.

Since they exist, is there anyone who knows where they can be found??  I think that if I can get the 64 bit drivers, I may be able to get it to work.  Right now, I am getting a 'bad magic' error stating that it can't use 32 bit drivers on a 64 bit system.  I am running a PentiumD.

---

### Post by javaJake on 2007-01-16
> **scottpledger said:**
> Since they exist, is there anyone who knows where they can be found??  I think that if I can get the 64 bit drivers, I may be able to get it to work.  Right now, I am getting a 'bad magic' error stating that it can't use 32 bit drivers on a 64 bit system.  I am running a PentiumD.
Hmmm, well, I was sure that someone posted here that they found drivers... can't seem to find that post now...

Oh, wait, here it is. Found it on the ndiswrapper wiki:
> Driver: For 64bit versions: get the usb8023.sys and rndismp.sys from a Windows XP / Vista 64bit installation. Also make sure you have the latest SVN version (or 1.20+). If you use this in combination with the .inf file from the official drivers as found on the LinkSys Support-site, it all works (even WEP and WPA)


Can you send me the drivers if you are able to extract them from a Windows 64-bit installation, so I can share them with other users?

---

### Post by phayke on 2007-01-18
I followed all of the instructions and using the attached drivers ndiswrapper now recognizes when my adapter is plugged in or not. The only problem is that the light for my adapter blinks once quickly and remains very dim immediately after connecting it.

My adapter is shown in my device manager and in ndisgtk as present, but not in my network connections. My network connections shows my two disabled ethernet cards and an unconfigured dialup modem.

I followed the instructions for fixing the voltage in edgy but nothing changed. Perhaps the rule isn't being executed, and the lack of voltage is causing the device to be recognized, but not seen as a working network adapter?

PS. I also tried setting up the (optional) network manager, but at the beginning I was unable to save the edited read-only file. I wasn't prompted for a password, and couldn't login as root when I tried that.

---

### Post by Ritchstorm on 2007-01-19
Phayke are you running 6.10? If you are if you read a little further down it says about problems in 6.10. Edgy prevents too much power to be used on USB devices and he gives two codes to bypass this restriction. I am totally new to linux, just installed it about an hour ago and have never even seen it in my life. I got my WUSB54GSv2 working 2nd time. First time I misread it and forgot to cd ~MyDrivers. Oh well working now!

THANKYOU SO MUCH JAVAJAKE!!!

---

### Post by javaJake on 2007-01-19
> **phayke said:**
> I followed all of the instructions and using the attached drivers ndiswrapper now recognizes when my adapter is plugged in or not. The only problem is that the light for my adapter blinks once quickly and remains very dim immediately after connecting it.Very dim? What do you mean? Do you mean that the light stop blinking, becomes a steady light, but then dims? If this is so, this is either not the WUSB54GS device, or it is malfunctioning.

> **phayke said:**
> My adapter is shown in my device manager and in ndisgtk as present, but not in my network connections. My network connections shows my two disabled ethernet cards and an unconfigured dialup modem.OK, what does "ndiswrapper -l" say after you've plugged in the device?

> **phayke said:**
> I followed the instructions for fixing the voltage in edgy but nothing changed. Perhaps the rule isn't being executed, and the lack of voltage is causing the device to be recognized, but not seen as a working network adapter?This won't work until ndiswrapper recognizes and loads the driver for it. First we need to confirm this is happening.

Also, Device Manager doesn't do anything but download information off of the device. Your device name and everything can be listed, but that doesn't mean Ubuntu will use it.

> **phayke said:**
> PS. I also tried setting up the (optional) network manager, but at the beginning I was unable to save the edited read-only file. I wasn't prompted for a password, and couldn't login as root when I tried that.NetworkManager will not work if ndiswrapper won't load the driver, so if ndiswrapper isn't seeing your device, nothing will.



Hopefully your device isn't malfunctioning.

---

### Post by javaJake on 2007-01-19
> **Ritchstorm said:**
> Phayke are you running 6.10? If you are if you read a little further down it says about problems in 6.10. Edgy prevents too much power to be used on USB devices and he gives two codes to bypass this restriction. I am totally new to linux, just installed it about an hour ago and have never even seen it in my life. I got my WUSB54GSv2 working 2nd time. First time I misread it and forgot to cd ~MyDrivers. Oh well working now!

THANKYOU SO MUCH JAVAJAKE!!!

I'm glad you were able to set the WUSB54GS device! If you have any ideas about how to change the HOWTO to make it easier to use, let me know. :)

---

### Post by Ritchstorm on 2007-01-20
Well like I said I am totally new to linux! In fact its the first thing I actually did on linux at all! I think you should include the fact you need the internet to actually do this in the first place, over a LAN. Also maybe post the code to cd~/MyDrivers/ as you do say to do it but I missed it as it wasn't in a box like the rest of the commands. Also maybe post a warning in the "Connecting up the device" section as I nearly plugged mine in before doing teh commands that are required for Edgy. Oh and when i use this command "sudo ndiswrapper -m" when you say to, it returns the error 
"ritchstorm@ritchstorm-desktop:~/ndiswrapper-1.28$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
couldn't add module alias:  at /usr/sbin/ndiswrapper line 717." I have no idea what this means but everything still works fine and teh device automatically starts up and connects as well. Sorry for being so picky however I have been using Windows since 95 and i also touched a bit on the older versions when I was really young and when i first ran linux i was clueless, and I found this guide very newbie friendly. Thankyou so much.

---

### Post by javaJake on 2007-01-20
I've reviewed all your changes, and they all are superb. I'll put them in at somepoint.

---

### Post by r+9 on 2007-01-28
Great thread but I'm still lost.

first I'm a recovering windows addict so EVERYTHING in linux seems upside down to me.

second, if you havn't guessed I'm a noob, even worse than any other noob reading this

third, I'm not actually on ubuntu but SUSE 10.2, however this thread has the best info I've found

fourth.  I don't have the exact linksys model, I have WUSB54GSC, the install files are very similar but so far I haven't found the right touch.

I've gotten so far as ndiswrapper -l tells me:

wusb54gsc               driver installed, hardware (13B1:0026) present (alternate driver: conflict)

however modprobe ndiswrapper appears to work fine

dmesg gives me some :

ndiswrapper version 1.25 loaded (preempt=no,smp=yes)
usbcore: registered new driver ndiswrapper
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:13:10:94:40:f8:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2
usb 2-5: new high speed USB device using ehci_hcd and address 7
usb 2-5: new device found, idVendor=13b1, idProduct=0026
usb 2-5: new device strings: Mfr=1, Product=2, SerialNumber=3
usb 2-5: Product: Compact Wireless-G USB Network Adapter with SpeedBooster
usb 2-5: Manufacturer: Broadcom
usb 2-5: SerialNumber: 8057
usb 2-5: no configuration chosen from 1 choice

i tried the special 99-custom.rules because I can't get any blinks on the device.

---

### Post by Guitar John on 2007-01-29
> Once you have extracted ndiswrapper from the attachment, go into the ndiswrapper folder in the terminal, and run:

I'm new but trying to learn.  This is the line where I get stuck.  I downloaded the attachment to the desktop.  On the desktop is a file called "ndiswrapper-files".   Open that file and I see 3 more files: Drivers_v1, Drivers_v2, and ndiswrapper-1.28.  So I think I'm good there.  

How do I go to the folder in the terminal?

-John

---

### Post by javaJake on 2007-01-31
r+9, you mentioned that this is a different device - it's a wusb54gsc. The ndiswrapper output...
> **r+9 said:**
> wusb54gsc               driver installed, hardware (13B1:0026) present (alternate driver: conflict)

...this line from dmesg...

> **r+9 said:**
> usb 2-5: no configuration chosen from 1 choice

...both tell me that the rule you punched in to udev actually won't work. What you need to do is change the idProduct variable in 99-custom.rules to "0026" to match what ndiswrapper showed you.


**_Please read! Do not skip this last bit!_** Ndiswrapper reports that you have a driver conflict. It says "(alternate driver: conflict)". To remove this conflict, you need to first find out what driver this would normally use. This is where I blank out. I don't know how to figure this out. Does dmesg say any more about drivers for a usb device besides ndiswrapper? Something like "usbcore: registered new driver <driver-name>"?

---

### Post by javaJake on 2007-01-31
> **Guitar John said:**
> I'm new but trying to learn.  This is the line where I get stuck.  I downloaded the attachment to the desktop.  On the desktop is a file called "ndiswrapper-files".   Open that file and I see 3 more files: Drivers_v1, Drivers_v2, and ndiswrapper-1.28.  So I think I'm good there.  

How do I go to the folder in the terminal?

-John

You use "cd <folder>", so in this case, you "cd Desktop/ndiswrapper-files" to jump down a few folders into the ndiswrapper-files directory.

---

### Post by r+9 on 2007-02-02
BUS=="usb", SYSFS{idProduct}=="0026", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue

that is what is in my 99-custom.rules file, I caught in your instruction and realized I had a diffrent product.

I'm thinking the conflict with the driver is my main problem.  I'm using the .inf file from the install cd (which happens to be the exact same as the one offered by linksys webpage) 

I followed the instructions from
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

which says my device should work.  however the two .sys files don't seem to... so very confused

there are other .sys files to choose from, I have tried a few combinations but so far no luck.

---

### Post by javaJake on 2007-02-03
> **r+9 said:**
> BUS=="usb", SYSFS{idProduct}=="0026", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue

that is what is in my 99-custom.rules file, I caught in your instruction and realized I had a diffrent product.

I'm thinking the conflict with the driver is my main problem.  I'm using the .inf file from the install cd (which happens to be the exact same as the one offered by linksys webpage) 

I followed the instructions from
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

which says my device should work.  however the two .sys files don't seem to... so very confused

there are other .sys files to choose from, I have tried a few combinations but so far no luck.

For anyone else reading this thread and wanting to know the answer, r+9 and I chatted on IM and found that the rule itself wasn't working, but everyhthing else appears fine. The workaround for him was to manually run the following commands:

1. sudo su (to get into a root terminal, which is required for the next command)
2.  echo 1 > /sys/bus/usb/devices/*<insert port number here>*/bConfigurationValue

Essentially, you run the command that was supposed to be run in 99-custom.rules file manually.

---

### Post by Genotrius on 2007-02-14
Hey! Me again.
After my version 2.1 got fried (long story), I got a version one off eBay with the help of my dad's laptop. The first time I plugged it in it didn't work, then a couple reboots later, it did, but the link light didn't flash once. Now, it doesn't again. Any idea what may be causing this erratic behavior?

---

### Post by javaJake on 2007-02-14
Actually, no, I don't. If you wouldn't mind, *after you plug in the device* could you post the /var/log/syslog file, the /etc/udev/rules.d/99-custom.rules file, and the output of "ndiswrapper -l"? That should tell me what's going on.

---

### Post by Genotrius on 2007-02-14
I can tell you now that "ndiswrapper -l" says that the driver for WUSB54GS is installed and the device is plugged in, and I copied and pasted both of the lines straight from the tutorial into the /etc/udev/rules.d/99-custom.rules file. 
How would I get the /var/log/syslog file?

Oh, and by the way, when I go to Administrative > Networking, my device isn't listed as a network device, but it was the time that it worked.

---

### Post by javaJake on 2007-02-14
To get the /var/log/syslog file, plug in your device (so that the right entries get written to syslog) and then just copy and paste that file, and upload it here. If you want, e-mail it to me.

---

### Post by Genotrius on 2007-02-15
It should be e-mailed, I think.

---

### Post by Genotrius on 2007-02-16
Yay, I figured it out for myself!
I don't really know what specifically was wrong, but I looked at dmesg ansd syslog and saw alot of errors from ndiswrapper and loadndiswrapper and such, so I just reinstalled ndiswrapper, and here I am, back on my beloved Ubuntu PC!

---

### Post by javaJake on 2007-02-17
> **Genotrius said:**
> Yay, I figured it out for myself!
I don't really know what specifically was wrong, but I looked at dmesg ansd syslog and saw alot of errors from ndiswrapper and loadndiswrapper and such, so I just reinstalled ndiswrapper, and here I am, back on my beloved Ubuntu PC!

ROFL! I was just coming here to suggest that! Congrats for figuring it out on your own! You're one step farther into the Linux world of troubleshooting. :)

---

### Post by javaJake on 2007-02-17
**_Anyone Waiting for a Reply - Please Read_**

My promised review of the last half of the thread is complete, but I couldn't find anyone that was waiting for a reply, so if you are waiting for a reply on this thread, let me know, because somehow you've been lost in the scramble.

---

### Post by theDaveTheRave on 2007-03-01
Jake.

Brilliant howto \\:D/ - I have some additions i would like to make to your document, but i will send those later.

I am using a belkin F5D7051 device (usb), and the instructions seem to work effectively enough :guitar:  .... but there is a snag! :confused: 

I have connected my device and the light comes on, but doesn't flash! I have used the network manager and the device is showing as present, the screen dump of the various commands are as follows:

> davem@Dartagnon:/etc/ndiswrapper-1.37$ route -n
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0

davem@Dartagnon:/etc/ndiswrapper-1.37$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Auto  Access Point: Not-Associated   Bit Rate:0 kb/s
          Link Quality:100  Signal level:0  Noise level:160
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
sit0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"belkin54g"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:17:3F:15:5D:43
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management: off
          Link Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

davem@Dartagnon:/etc/ndiswrapper-1.37$ ndiswrapper -l
bcmrndis : driver installed
        device (050D:7051) present

davem@Dartagnon:/etc/ndiswrapper-1.37$ lsusb
Bus 003 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 050d:7051 Belkin Components
Bus 001 Device 002: ID 046d:c401 Logitech, Inc. TrackMan Marble Wheel
Bus 001 Device 001: ID 0000:0000
davem@Dartagnon:/etc/ndiswrapper-1.37$



so the device is present and working,  but I can't connect to a network? any thoughts?? I have tried disconnecting my ethernet cable, so as it can't use this by default, I've set wlan1 to the default in the network settings, but still no luck?  When I try to connect to the wireless network the USB key doesn't even blink at me, I have the same problem if i connect the USB to device 001; but then I loose th information that is in < wlan1 >.

so questions;

How do i set the wlan0 to associate itself with an access point?? and why if i plug the usb key into another of the ports (id device 001)  do I not get a wlan1 showing up on in the < iwconfig >

Can I set the routing table to reflect the same information for wlan0 as it does for eth0? and if so how?

why does the wlan1 not appear in < route -n > information?
Why can I not do a scan on the device - it just doesn't seem to do anything?

I really want to get my desktop to run on Linux permanently, but I need it connected to the net. Also I am intending to set this up for a charity that a friend runs and I should at least be able to get it working at home first - or I will look a right twit!

I have thought about the idea of using a second modem/router (the same as the one currently hooked into the phone lin) but would how could I link the 2 devices together? Again I would need to associate the 2 devices - or could I do that from within the units setup?? i will do a search to see if that is possible.

Well that is about it for now. I hope that you are able to help in the fina push as i feel that i am so close to having everthing working. ](*,) 

thanks in advance for the help.

DaveM

1st Edit>

I just realised something else on the <route -n > output. the details of the destination and gateway do not match those for the working eth0 device, is it possible to edit this table manualy regarding this detail or not.... and if so what is the code, as I can't find successfull help on changing the ip tables (I assume that this is what they are?)

cheers

DaveM

2nd Edit

OK people... now I feel really stupid!

I've returned my desktop pc upstairs, so it is no longer hard wired into te internet.... started up, pluged in and hey presto... it works!

The usb gizmo is pluged into one of the USB 1.0 ports.... but who cares!!!!!! The only gripe I have now is to find an icon that tells me that the internet is connected because the little icon that appears in my panel obviously only refers to the hard wired connection!

I have recolections of there being stuff on Jake's howto to add an applet so I'm going to have another quick look.

Jake that howto is superb... I've obviously made some adjustments to get the belkin F5D7051 device to work as it should, would you like me to write a howto for that device or will you add it as an append / option set for yours?? I'll work on the details of it and I will post it here in a day or two..

Brilliant Jake you are a STAR

---

### Post by javaJake on 2007-03-02
> **theDaveTheRave said:**
> OK people... now I feel really stupid!

I've returned my desktop pc upstairs, so it is no longer hard wired into te internet.... started up, pluged in and hey presto... it works!

I'm assuming at this point you've solved the issue and don't need help anymore. If this isn't the case let me know. I've contacted you by e-mail also. Can't wait to see what you've got as far as modifications go. :)

---

### Post by theDaveTheRave on 2007-03-07
Hi again all.

I've just setup another pc (this time a laptop).

And the howto has worked a treat.

Jake once again, great howto.

I can now finalise all those little extra points into a file, and then I'll send it too you for addition into your excelent howto,

Also I have recently set up the Charities pc onto a network... I'm really getting into this linux thing.

Now to load up Netbeans and a load of other stuff...

Joy of Tux I say!

Dave M

---

### Post by javaJake on 2007-03-07
> **theDaveTheRave said:**
> I can now finalise all those little extra points into a file, and then I'll send it too you for addition into your excelent howto,

Please merge your additions into the Google Doc I sent you. It makes everything a lot easier for me. :)

---

### Post by oskarmat on 2007-03-08
:confused:  Hi! I'm reallly newbie and, moreover I'm not even using ubuntu right now because I'm not getting my internet connection to work. I'm currentlly using Mandriva 2007, and I cannot configure my Belkin f5d7051 Wireless USB. That's what i did:

with ndiswrapper 1.21 (the one that comes with the pack):

- ndiswrapper -i bcmrndis.inf

This copies all the needed files in /etc/ndiswrapper/bcmrndis folder

if I type ndiswrapper -l it gives me: dirver installed, hardware present

and after i run depmod -a 
and modprobe ndiswrapper

all goes ok

when i run dmesg, it says it detects a new usb installed by ndiswrapper

but on iwconfig it doesn't show any wlan0 or so....

Maybe is something about the rules thing...well I have to say I really putting my eyes on linux for the first time...

Thanks in advance.... I really want to get this thing working!

---

### Post by theDaveTheRave on 2007-03-08
Oskarmat.

Ok you need to check a few things for me first.

Can you run the commands 
<iwconfig>                   this will show all the potential wireless connections
<lsusb>                       lists all the devices that are plugged into usb ports.
<ndiswrapper -l>         will report the presence of the driver and the device.

Can you then either copy the output into another post or confirm that the information is the same as in my post [here](http://ubuntuforums.org/showpost.php?p=2230632&postcount=96)

also run the command

<iwlist wlan0 scan>     this will output details of the connections that are available, and will confirm that the USB key is working.

i can confirm that I have been able to get this key working twice now, once on a laptop and once on my desktop. I can also say that there is a difference between the "nettwork" icon that appears by deffault in the gnome taskbar and the wireless network icon (this one has a set of bars beside it that I assume change depending on the signal?).

Also you are using an old copy of ndiswrapper, this may also be causing you some problems, I would highly recomed Jake's advice of downoading the current one (I think they have recently gone onto 1.38 ).

have faith Oskarmat, i have been able to get the Belkin USB key F5D7050 and F5D7051 working using jake's howto details (the F5D7051 was on a SuSe 10.0 platform - running gnome).

Also the files that come with the official CD for the USB device are not as Jake mentions, they are in the location but the files are named in upper case (:confused: you will need to change them and remove the end characters to make the whole thing work).

I'm going to endeavour to put some changes into Jake's howto over the next couple of Days to cover these extra details, but untill I get it completed just write a post to here and we'll help if we can.

One last thing. Where are you plugging in the device?? if you are putting it into some spare USB ports that you have on a separate card that may be the problem, I found mine would only work if I had it hooked into the ports that are build into the mother board..... I bought an extension cable for mine as I am lazy and don't like crawling on the floor to get around the back of my pc :mad:

I hope this all helps.

get back if not.

I am generally on line most of the time, so we can talk by email if you wish. Send me a private message from your user login and I'll send you a copy of the adjustments that I have on my pc - that I need to add into jake's Howto.

Good Luck.

Dave

---

### Post by javaJake on 2007-03-10
**Edit:** Sorry, theDaveTheRave. I didn't realize you had already responded to oskarmat.

> **oskarmat said:**
> :confused:  Hi! I'm reallly newbie and, moreover I'm not even using ubuntu right now because I'm not getting my internet connection to work. I'm currentlly using Mandriva 2007, and I cannot configure my Belkin f5d7051 Wireless USB.Please realize this forum is for the WUSB54GS, so support for other devices will be limited to a certain point.

> **oskarmat said:**
> That's what i did:

with ndiswrapper 1.21 (the one that comes with the pack):

- ndiswrapper -i bcmrndis.inf

This copies all the needed files in /etc/ndiswrapper/bcmrndis folderOK, good good...

> **oskarmat said:**
> if I type ndiswrapper -l it gives me: dirver installed, hardware presentThis is a good sign.

> **oskarmat said:**
> and after i run depmod -a 
and modprobe ndiswrapper

all goes ok

when i run dmesg, it says it detects a new usb installed by ndiswrapperGreat...

> **oskarmat said:**
> but on iwconfig it doesn't show any wlan0 or so....

Maybe is something about the rules thing...well I have to say I really putting my eyes on linux for the first time...OK, the rule is only required if your device is getting a "no configuration chosen" every time it is plugged in.

In order for me to effectively help you out, I'll need the contents of the file /var/log/syslog after you've plugged in your device and waited for about 5-10 seconds.

---

### Post by leetcharmer on 2007-03-11
I need some assistance.  I'm using the WUSB54GSC(v1 as this is the only version available for this model).  I can get through all of it, but I never can get any scan results.

99-custom.rules:
```
BUS=="usb", SYSFS{idProduct}=="0026", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"

```

syslog:
```
Mar 11 14:54:47 testBox kernel: [17179577.476000] hub 4-0:1.0: USB hub found
Mar 11 14:54:47 testBox kernel: [17179577.476000] hub 4-0:1.0: 2 ports detected
Mar 11 14:54:47 testBox kernel: [17179577.712000] kjournald starting.  Commit interval 5 seconds
Mar 11 14:54:47 testBox kernel: [17179577.712000] EXT3-fs: mounted filesystem with ordered data mode.
Mar 11 14:54:47 testBox kernel: [17179577.724000] usb 1-3: new high speed USB device using ehci_hcd and address 3
Mar 11 14:54:47 testBox kernel: [17179577.880000] usb 1-3: no configuration chosen from 1 choice
Mar 11 14:54:47 testBox kernel: [17179578.140000] usb 2-1: new low speed USB device using uhci_hcd and address 2
Mar 11 14:54:47 testBox kernel: [17179578.332000] usb 2-1: configuration #1 chosen from 1 choice
Mar 11 14:54:47 testBox kernel: [17179578.428000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c009100ba70]
Mar 11 14:54:47 testBox kernel: [17179587.472000] orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
Mar 11 14:54:47 testBox kernel: [17179587.472000] orinoco_plx 0.15rc3 (Pavel Roskin <proski@gnu.org>, David Gibson <hermes@gibson.dropbear.id.au>, Daniel Barlow <dan@telent.net>)
Mar 11 14:54:47 testBox kernel: [17179587.472000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 18 (level, low) -> IRQ 193
Mar 11 14:54:47 testBox kernel: [17179587.472000] orinoco_plx: Detected Orinoco/Prism2 PLX device at 0000:00:0b.0 irq:193, io addr:0x9000
Mar 11 14:54:47 testBox kernel: [17179587.476000] orinoco_plx: CIS: 04:04:04:08:08:0C:0C:10:10:14:14:18:18:1C:1C:20:
Mar 11 14:54:47 testBox kernel: [17179587.476000] orinoco_plx: The CIS value of Prism2 PC card is unexpected
Mar 11 14:54:47 testBox kernel: [17179587.476000] ACPI: PCI interrupt for device 0000:00:0b.0 disabled
Mar 11 14:54:47 testBox kernel: [17179587.476000] orinoco_plx: probe of 0000:00:0b.0 failed with error -5
Mar 11 14:54:47 testBox kernel: [17179587.512000] Linux Tulip driver version 1.1.14 (May 6, 2006)
Mar 11 14:54:47 testBox kernel: [17179587.512000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 201
Mar 11 14:54:47 testBox kernel: [17179587.512000] tulip0:  MII transceiver #1 config 1000 status 7849 advertising 01e1.
Mar 11 14:54:47 testBox kernel: [17179587.520000] eth0: ADMtek Comet rev 17 at Port 0xd800, 00:20:78:0E:4A:2F, IRQ 201.
Mar 11 14:54:47 testBox kernel: [17179587.556000] gameport: EMU10K1 is pci0000:00:07.1/gameport0, io 0xec00, speed 1217kHz
Mar 11 14:54:47 testBox kernel: [17179587.624000] irda_init()
Mar 11 14:54:47 testBox kernel: [17179587.624000] NET: Registered protocol family 23
Mar 11 14:54:47 testBox kernel: [17179587.692000] prism2plx_init: prism2_plx.o: 0.2.5 Loaded
Mar 11 14:54:47 testBox kernel: [17179587.692000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 18 (level, low) -> IRQ 193
Mar 11 14:54:47 testBox kernel: [17179587.692000] A PLX PCI/PCMCIA interface device found, phymem:0xdfff9000, phyio=0x9000, irq:193, mem: 0xf89bc000
Mar 11 14:54:47 testBox kernel: [17179587.692000] prism2sta_probe_plx: Prism2 PC card CIS is invalid.
Mar 11 14:54:47 testBox kernel: [17179587.692000] prism2_plx: probe of 0000:00:0b.0 failed with error -5
Mar 11 14:54:47 testBox kernel: [17179587.708000] ieee80211_crypt: registered algorithm 'NULL'
Mar 11 14:54:47 testBox kernel: [17179587.748000] hostap_plx: 0.4.4-kernel (Jouni Malinen <jkmaline@cc.hut.fi>)
Mar 11 14:54:47 testBox kernel: [17179587.748000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 18 (level, low) -> IRQ 193
Mar 11 14:54:47 testBox kernel: [17179587.748000] PLX9052 PCI/PCMCIA adapter: mem=0xdfff9000, plx_io=0x9400, irq=193, pccard_io=0x9000
Mar 11 14:54:47 testBox kernel: [17179587.748000] hostap_plx: CIS: 04 04 04 08 08 0c ...
Mar 11 14:54:47 testBox kernel: [17179587.748000] hostap_plx: invalid CIS data
Mar 11 14:54:47 testBox kernel: [17179587.748000] Unknown PC Card CIS - not a Prism2/2.5 card?
Mar 11 14:54:47 testBox kernel: [17179587.748000] ACPI: PCI interrupt for device 0000:00:0b.0 disabled
Mar 11 14:54:47 testBox kernel: [17179587.764000] Linux agpgart interface v0.101 (c) Dave Jones
Mar 11 14:54:47 testBox kernel: [17179587.776000] agpgart: Detected VIA KT400/KT400A/KT600 chipset
Mar 11 14:54:47 testBox kernel: [17179587.784000] agpgart: AGP aperture is 128M @ 0xe0000000
Mar 11 14:54:47 testBox kernel: [17179588.524000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 11 14:54:47 testBox kernel: [17179588.620000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar 11 14:54:47 testBox kernel: [17179588.688000] Floppy drive(s): fd0 is 1.44M
Mar 11 14:54:47 testBox kernel: [17179588.712000] FDC 0 is a post-1991 82077
Mar 11 14:54:47 testBox kernel: [17179588.772000] input: PC Speaker as /class/input/input1
Mar 11 14:54:47 testBox kernel: [17179589.000000] parport: PnPBIOS parport detected.
Mar 11 14:54:47 testBox kernel: [17179589.000000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Mar 11 14:54:47 testBox kernel: [17179589.300000] sd 2:0:0:0: Attached scsi generic sg0 type 0
Mar 11 14:54:47 testBox kernel: [17179589.348000] usbcore: registered new driver hiddev
Mar 11 14:54:47 testBox kernel: [17179589.368000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input2
Mar 11 14:54:47 testBox kernel: [17179589.368000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.0-1
Mar 11 14:54:47 testBox kernel: [17179589.368000] usbcore: registered new driver usbhid
Mar 11 14:54:47 testBox kernel: [17179589.368000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Mar 11 14:54:47 testBox kernel: [17179589.484000] ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 19 (level, low) -> IRQ 169
Mar 11 14:54:47 testBox kernel: [17179589.484000] Installing spdif_bug patch: Audigy 2 Platinum [SB0240P]
Mar 11 14:54:47 testBox kernel: [17179589.572000] usbcore: registered new driver cdc_ether
Mar 11 14:54:47 testBox kernel: [17179589.572000] usb 1-3: bad CDC descriptors
Mar 11 14:54:47 testBox kernel: [17179589.572000] usbcore: registered new driver rndis_host
Mar 11 14:54:47 testBox kernel: [17179589.600000] ts: Compaq touchscreen protocol output
Mar 11 14:54:47 testBox kernel: [17179590.020000] lp0: using parport0 (interrupt-driven).
Mar 11 14:54:47 testBox kernel: [17179590.064000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
Mar 11 14:54:47 testBox kernel: [17179590.064000] ieee1394: sbp2: Try serialize_io=0 for better performance
Mar 11 14:54:47 testBox kernel: [17179590.332000] NET: Registered protocol family 17
Mar 11 14:54:47 testBox kernel: [17179590.336000] EXT3 FS on hda3, internal journal
Mar 11 14:54:47 testBox kernel: [17179590.764000] kjournald starting.  Commit interval 5 seconds
Mar 11 14:54:47 testBox kernel: [17179590.780000] EXT3 FS on hdb1, internal journal
Mar 11 14:54:47 testBox kernel: [17179590.780000] EXT3-fs: mounted filesystem with ordered data mode.
Mar 11 14:54:47 testBox kernel: [17179590.800000] kjournald starting.  Commit interval 5 seconds
Mar 11 14:54:47 testBox kernel: [17179590.808000] EXT3 FS on hda1, internal journal
Mar 11 14:54:47 testBox kernel: [17179590.808000] EXT3-fs: mounted filesystem with ordered data mode.
Mar 11 14:54:47 testBox kernel: [17179590.828000] kjournald starting.  Commit interval 5 seconds
Mar 11 14:54:47 testBox kernel: [17179590.840000] EXT3 FS on sda1, internal journal
Mar 11 14:54:47 testBox kernel: [17179590.840000] EXT3-fs: mounted filesystem with ordered data mode.
Mar 11 14:54:47 testBox kernel: [17179594.628000] ndiswrapper version 1.37 loaded (preempt=no,smp=yes)
Mar 11 14:54:47 testBox kernel: [17179594.792000] usb 1-3: reset high speed USB device using ehci_hcd and address 3
Mar 11 14:54:47 testBox kernel: [17179594.980000] ndiswrapper: driver wusb54gsc (Linksys,01/25/2005, 4.01.20.0) loaded
Mar 11 14:54:47 testBox kernel: [17179595.492000] wlan0: ethernet device 00:18:f8:b0:5d:8d using NDIS driver: wusb54gsc, version: 0x4011405, NDIS version: 0x501, vendor: 'Compact Wireless-G USB Network Adapter with SpeedBooster', 13B1:0026.F.conf
Mar 11 14:54:47 testBox kernel: [17179595.660000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Mar 11 14:54:47 testBox kernel: [17179595.668000] usbcore: registered new driver ndiswrapper
Mar 11 14:54:47 testBox kernel: [17179659.852000] ACPI: Power Button (FF) [PWRF]
Mar 11 14:54:47 testBox kernel: [17179659.852000] ACPI: Power Button (CM) [PWRB]
Mar 11 14:54:47 testBox kernel: [17179659.852000] ACPI: Sleep Button (CM) [SLPB]
Mar 11 14:54:47 testBox kernel: [17179659.996000] ibm_acpi: ec object not found
Mar 11 14:54:47 testBox kernel: [17179660.044000] pcc_acpi: loading...
Mar 11 14:54:48 testBox hpiod: 1.6.9 accepting connections at 2208... 
Mar 11 14:54:49 testBox kernel: [17179664.032000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Mar 11 14:54:49 testBox kernel: [17179664.032000] apm: overridden by ACPI.
Mar 11 14:54:54 testBox hcid[4453]: Bluetooth HCI daemon
Mar 11 14:54:54 testBox kernel: [17179669.148000] Bluetooth: Core ver 2.8
Mar 11 14:54:54 testBox kernel: [17179669.148000] NET: Registered protocol family 31
Mar 11 14:54:54 testBox kernel: [17179669.148000] Bluetooth: HCI device and connection manager initialized
Mar 11 14:54:54 testBox kernel: [17179669.148000] Bluetooth: HCI socket layer initialized
Mar 11 14:54:54 testBox hcid[4453]: Register path:/org/bluez fallback:1
Mar 11 14:54:54 testBox kernel: [17179669.184000] Bluetooth: L2CAP ver 2.8
Mar 11 14:54:54 testBox kernel: [17179669.184000] Bluetooth: L2CAP socket layer initialized
Mar 11 14:54:54 testBox sdpd[4460]: Bluetooth SDP daemon 
Mar 11 14:54:54 testBox kernel: [17179669.208000] Bluetooth: RFCOMM socket layer initialized
Mar 11 14:54:54 testBox kernel: [17179669.208000] Bluetooth: RFCOMM TTY layer initialized
Mar 11 14:54:54 testBox kernel: [17179669.208000] Bluetooth: RFCOMM ver 1.7
Mar 11 14:54:54 testBox anacron[4489]: Anacron 2.3 started on 2007-03-11
Mar 11 14:54:54 testBox anacron[4489]: Normal exit (0 jobs run)
Mar 11 14:54:54 testBox /usr/sbin/cron[4515]: (CRON) INFO (pidfile fd = 3)
Mar 11 14:54:54 testBox /usr/sbin/cron[4516]: (CRON) STARTUP (fork ok)
Mar 11 14:54:54 testBox /usr/sbin/cron[4516]: (CRON) INFO (Running @reboot jobs)
Mar 11 14:55:01 testBox gconfd (leetcharmer-4647): starting (version 2.16.0), pid 4647 user 'leetcharmer'
Mar 11 14:55:01 testBox gconfd (leetcharmer-4647): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar 11 14:55:01 testBox gconfd (leetcharmer-4647): Resolved address "xml:readwrite:/home/leetcharmer/.gconf" to a writable configuration source at position 1
Mar 11 14:55:01 testBox gconfd (leetcharmer-4647): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Mar 11 14:55:01 testBox gconfd (leetcharmer-4647): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Mar 11 14:55:01 testBox gconfd (leetcharmer-4647): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Mar 11 14:55:03 testBox kernel: [17179678.184000] NET: Registered protocol family 10
Mar 11 14:55:03 testBox kernel: [17179678.184000] lo: Disabled Privacy Extensions
Mar 11 14:55:03 testBox kernel: [17179678.184000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 11 14:55:03 testBox kernel: [17179678.184000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 11 14:55:03 testBox kernel: [17179678.184000] IPv6 over IPv4 tunneling driver
Mar 11 14:55:06 testBox gconfd (leetcharmer-4647): Resolved address "xml:readwrite:/home/leetcharmer/.gconf" to a writable configuration source at position 0
Mar 11 14:55:09 testBox bonobo-activation-server (leetcharmer-4686): Passing command-line arguments in .server files is deprecated: "/usr/bin/tomboy --panel-applet"
Mar 11 14:56:03 testBox dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 3620
Mar 11 14:56:03 testBox dhclient: killed old client process, removed PID file
Mar 11 14:56:03 testBox dhclient: Internet Systems Consortium DHCP Client V3.0.4
Mar 11 14:56:03 testBox dhclient: Copyright 2004-2006 Internet Systems Consortium.
Mar 11 14:56:03 testBox dhclient: All rights reserved.
Mar 11 14:56:03 testBox dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 11 14:56:03 testBox dhclient: 
Mar 11 14:56:03 testBox dhclient: Listening on LPF/wlan0/00:18:f8:b0:5d:8d
Mar 11 14:56:03 testBox dhclient: Sending on   LPF/wlan0/00:18:f8:b0:5d:8d
Mar 11 14:56:03 testBox dhclient: Sending on   Socket/fallback
Mar 11 14:56:03 testBox dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Mar 11 14:56:03 testBox dhclient: Internet Systems Consortium DHCP Client V3.0.4
Mar 11 14:56:03 testBox dhclient: Copyright 2004-2006 Internet Systems Consortium.
Mar 11 14:56:03 testBox dhclient: All rights reserved.
Mar 11 14:56:03 testBox dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 11 14:56:03 testBox dhclient: 
Mar 11 14:56:03 testBox kernel: [17179737.828000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 11 14:56:04 testBox dhclient: Listening on LPF/wlan0/00:18:f8:b0:5d:8d
Mar 11 14:56:04 testBox dhclient: Sending on   LPF/wlan0/00:18:f8:b0:5d:8d
Mar 11 14:56:04 testBox dhclient: Sending on   Socket/fallback
Mar 11 14:56:04 testBox dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Mar 11 14:56:11 testBox dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Mar 11 14:56:25 testBox dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Mar 11 14:56:35 testBox dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Mar 11 14:56:47 testBox dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Mar 11 14:56:55 testBox dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Mar 11 14:57:05 testBox dhclient: No DHCPOFFERS received.
Mar 11 14:57:05 testBox dhclient: No working leases in persistent database - sleeping.
Mar 11 14:57:05 testBox ntpdate[4966]: can't find host ntp.ubuntu.com 
Mar 11 14:57:05 testBox ntpdate[4966]: no servers can be used, exiting
Mar 11 14:59:25 testBox dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Mar 11 14:59:32 testBox dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
Mar 11 14:59:52 testBox dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Mar 11 15:00:08 testBox dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Mar 11 15:00:16 testBox dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Mar 11 15:00:26 testBox dhclient: No DHCPOFFERS received.
Mar 11 15:00:26 testBox dhclient: No working leases in persistent database - sleeping.
Mar 11 15:02:51 testBox dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Mar 11 15:02:54 testBox dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Mar 11 15:03:02 testBox dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Mar 11 15:03:08 testBox dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Mar 11 15:03:11 testBox dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Mar 11 15:03:18 testBox dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Mar 11 15:03:21 testBox dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Mar 11 15:03:26 testBox dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Mar 11 15:03:39 testBox dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Mar 11 15:03:41 testBox dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Mar 11 15:03:48 testBox dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Mar 11 15:03:49 testBox dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Mar 11 15:03:52 testBox dhclient: No DHCPOFFERS received.
Mar 11 15:03:52 testBox dhclient: No working leases in persistent database - sleeping.
Mar 11 15:04:00 testBox dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Mar 11 15:04:09 testBox dhclient: No DHCPOFFERS received.
Mar 11 15:04:09 testBox dhclient: No working leases in persistent database - sleeping.
Mar 11 15:04:22 testBox kernel: [17180236.976000] attempt to access beyond end of device
Mar 11 15:04:22 testBox kernel: [17180236.976000] fd0: rw=0, want=2884, limit=2880
Mar 11 15:04:22 testBox kernel: [17180236.976000] UDF-fs: No VRS found
Mar 11 15:05:09 testBox kernel: [17180284.600000] attempt to access beyond end of device
Mar 11 15:05:09 testBox kernel: [17180284.600000] fd0: rw=0, want=2884, limit=2880
Mar 11 15:05:09 testBox kernel: [17180284.600000] UDF-fs: No VRS found
Mar 11 15:05:16 testBox kernel: [17180291.176000] Unable to identify CD-ROM format.
Mar 11 15:05:22 testBox kernel: [17180297.356000] Unable to identify CD-ROM format.
Mar 11 15:05:22 testBox kernel: [17180297.492000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```

It shows up in iwconfig as wlan0, but with no IP address, so I type the stuff in network configuration to connect to my SSID with WEP information.  Like I said before, no scan results :(!  Also, I shortened the syslog so I could make this post.  I think I kept in all relevant material.

---

### Post by scottpledger on 2007-03-11
When I finally got that card working, the only way that I could connect was to manually set the IP configuration information (DNS, Router/Gateway device, Subnet, IP, etc.)  you appear to be using DHCP, which doesn't work with this card on Linux for some reason or another.  Also, make sure that you aren't using IPv6, as it won't work with this card either.

Does wlan0 show up when you run:
```
ifconfig
```
If not, try running
```
ifconfig wlan0 up
```
then run
```
ifconfig
```
and see if the IP shows up there.

Hope this helps!

---

### Post by leetcharmer on 2007-03-12
alright, I did everything Static rather than DHCP and it adds the IP address and subnet mask, etc. in ifconfig.

when I try to ping the Access Point though, it still does not connect, so obviously it didn't work.

---

### Post by scottpledger on 2007-03-12
> **leetcharmer said:**
> alright, I did everything Static rather than DHCP and it adds the IP address and subnet mask, etc. in ifconfig.

when I try to ping the Access Point though, it still does not connect, so obviously it didn't work.

What do your log files say?

---

### Post by leetcharmer on 2007-03-12
which log file do you want after making it static IP?

---

### Post by scottpledger on 2007-03-12
> **leetcharmer said:**
> which log file do you want after making it static IP?

What is the output when you run 'sudo dmesg' in comand line/prompt?

Also, what is your syslog?

---

### Post by leetcharmer on 2007-03-12
syslog is too big for me to put in a post, at what point should I cut/paste?

---

### Post by scottpledger on 2007-03-12
> **leetcharmer said:**
> syslog is too big for me to put in a post, at what point should I cut/paste?

First, copy your 'dmesg' output (its whats going to tell us the most).  Then, post as much of the system log (/var/log/system.log) as you can.

---

### Post by javaJake on 2007-03-14
> **scottpledger said:**
> First, copy your 'dmesg' output (its whats going to tell us the most).  Then, post as much of the system log (/var/log/system.log) as you can.

Actually, the most of /var/log/**syslog** is actually better. It seems to collect information from all the logs, though I could be wrong.

---

### Post by mwells on 2007-03-25
Hi,

Thanks for the brilliant HOWTO, its been a massive help. however I am still having issues getting my connection to work.

I have followed the HOWTO and have the adaptor working, (the power light, and it tries to access the station with the link light etc) however it will not connect to the router . .

When checking the output of dmesg it tells me "No IPv6 routers present" . .when attemptig to connect it will repeatedly tell me this . .

Any ideas would be greatly appreciated!!

Many thanks

/Matt

p.s this is the tail -f /var/log/syslog > output.txt from trying to connect through the network manager

```

Mar 25 16:39:42 server1 NetworkManager: <information>^Iwpa_supplicant(5446): 0: 00:18:4d:c4:40:c4 ssid='Home001' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Mar 25 16:39:42 server1 NetworkManager: <information>^Iwpa_supplicant(5446):    skip - no WPA/RSN IE 
Mar 25 16:39:42 server1 NetworkManager: <information>^Iwpa_supplicant(5446):    selected non-WPA AP 00:18:4d:c4:40:c4 ssid='Home001' 
Mar 25 16:39:42 server1 NetworkManager: <information>^Iwpa_supplicant(5446): Trying to associate with 00:18:4d:c4:40:c4 (SSID='Home001' freq=2462 MHz) 
Mar 25 16:40:03 server1 NetworkManager: <information>^IActivation (wlan0/wireless): association took too long (>60s), failing activation. 
Mar 25 16:40:03 server1 NetworkManager: <information>^IActivation (wlan0) failure scheduled... 
Mar 25 16:40:03 server1 NetworkManager: <information>^IActivation (wlan0) failed for access point (Home001) 
Mar 25 16:40:03 server1 NetworkManager: <information>^IActivation (wlan0) failed. 
Mar 25 16:40:03 server1 NetworkManager: <information>^IDeactivating device wlan0. 
Mar 25 16:40:03 server1 NetworkManager: <WARNING>^I nm_device_802_11_wireless_set_essid (): error setting ESSID to '' for device wlan0: Invalid argument 
Mar 25 16:40:39 server1 NetworkManager: <debug info>^I[1174837239.135820] nm_device_802_11_wireless_get_activation_ap (): Forcing AP 'Home001' 
Mar 25 16:40:39 server1 NetworkManager: <information>^IUser Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / Home001 
Mar 25 16:40:39 server1 NetworkManager: <information>^IDeactivating device wlan0. 
Mar 25 16:40:39 server1 NetworkManager: <WARNING>^I nm_device_802_11_wireless_set_essid (): error setting ESSID to '' for device wlan0: Invalid argument 
Mar 25 16:40:41 server1 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Mar 25 16:40:41 server1 NetworkManager: <information>^IDevice wlan0 activation scheduled... 
Mar 25 16:40:41 server1 NetworkManager: <information>^IActivation (wlan0) started... 
Mar 25 16:40:41 server1 NetworkManager: <information>^IActivation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 25 16:40:42 server1 NetworkManager: <information>^IOld device 'wlan0' activating, won't change. 
Mar 25 16:40:42 server1 NetworkManager: <information>^IActivation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Mar 25 16:40:42 server1 NetworkManager: <information>^IActivation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Mar 25 16:40:42 server1 NetworkManager: <information>^IActivation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Mar 25 16:40:42 server1 NetworkManager: <information>^IActivation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Mar 25 16:40:42 server1 NetworkManager: <information>^IActivation (wlan0/wireless): access point 'Home001' is unencrypted, no key needed. 
Mar 25 16:40:43 server1 NetworkManager: <information>^ISUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant^I' 
Mar 25 16:40:43 server1 NetworkManager: <information>^ISUP: response was 'OK' 
Mar 25 16:40:43 server1 NetworkManager: <information>^ISUP: sending command 'AP_SCAN 1' 
Mar 25 16:40:43 server1 NetworkManager: <information>^ISUP: response was 'OK' 
Mar 25 16:40:43 server1 NetworkManager: <information>^ISUP: sending command 'ADD_NETWORK' 
Mar 25 16:40:43 server1 NetworkManager: <information>^ISUP: response was '0' 
Mar 25 16:40:43 server1 NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 ssid 486f6d65303031' 
Mar 25 16:40:43 server1 NetworkManager: <information>^ISUP: response was 'OK' 
Mar 25 16:40:43 server1 NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Mar 25 16:40:43 server1 NetworkManager: <information>^ISUP: response was 'OK' 
Mar 25 16:40:43 server1 NetworkManager: <information>^ISUP: sending command 'ENABLE_NETWORK 0' 
Mar 25 16:40:43 server1 NetworkManager: <information>^ISUP: response was 'OK' 
Mar 25 16:40:43 server1 NetworkManager: <information>^IActivation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Global control interface '/var/run/wpa_supplicant-global' 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): RX global ctrl_iface - hexdump_ascii(len=50): 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528):      49 4e 54 45 52 46 41 43 45 5f 41 44 44 20 77 6c   INTERFACE_ADD wl 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528):      61 6e 30 09 09 77 65 78 74 09 2f 76 61 72 2f 72   an0__wext_/var/r 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528):      75 6e 2f 77 70 61 5f 73 75 70 70 6c 69 63 61 6e   un/wpa_supplican 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528):      74 09                                             t_               
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): CTRL_IFACE GLOBAL INTERFACE_ADD 'wlan0^I^Iwext^I/var/run/wpa_supplicant^I' 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Initializing interface 'wlan0' conf 'N/A' driver 'wext' ctrl_interface '/var/run/wpa_supplicant' bridge 'N/A' 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Initializing interface (2) 'wlan0' 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): EAPOL: SUPP_PAE entering state DISCONNECTED 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): EAPOL: KEY_RX entering state NO_KEY_RECEIVE 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): EAPOL: SUPP_BE entering state INITIALIZE 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): EAP: EAP entering state DISABLED 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): EAPOL: External notification - portEnabled=0 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): EAPOL: External notification - portValid=0 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): SIOCGIWRANGE: WE(compiled)=20 WE(source)=18 enc_capa=0xf 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528):   capabilities: key_mgmt 0xf enc 0xf 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): WEXT: Operstate: linkmode=1, operstate=5 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): e:88 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): wpa_driver_wext_set_wpa 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): wpa_driver_wext_set_countermeasures 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): wpa_driver_wext_set_drop_unencrypted 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Setting scan request: 0 sec 100000 usec 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Added interface wlan0 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Wireless event: cmd=0x8b06 len=8 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): RX ctrl_iface - hexdump_ascii(len=9): 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528):      41 50 5f 53 43 41 4e 20 31                        AP_SCAN 1        
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): RX ctrl_iface - hexdump_ascii(len=11): 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528):      41 44 44 5f 4e 45 54 57 4f 52 4b                  ADD_NETWORK      
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): CTRL_IFACE: ADD_NETWORK 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): RX ctrl_iface - hexdump_ascii(len=33): [REMOVED] 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): CTRL_IFACE: SET_NETWORK id=0 name='ssid' 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): CTRL_IFACE: value - hexdump_ascii(len=14): [REMOVED] 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): ssid - hexdump_ascii(len=7): 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528):      48 6f 6d 65 30 30 31                              Home001          
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): _iface - hexdump_ascii(len=27): [REMOVED] 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): CTRL_IFACE: SET_NETWORK id=0 name='key_mgmt' 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): CTRL_IFACE: value - hexdump_ascii(len=4): [REMOVED] 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): key_mgmt: 0x4 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): RX ctrl_iface - hexdump_ascii(len=16): 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528):      45 4e 41 42 4c 45 5f 4e 45 54 57 4f 52 4b 20 30   ENABLE_NETWORK 0 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): CTRL_IFACE: ENABLE_NETWORK id=0 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Setting scan request: 0 sec 0 usec 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): State: DISCONNECTED -> SCANNING 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Starting AP scan (broadcast SSID) 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Trying to get current scan results first without requesting a new scan to speed up initial association 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Received 224 bytes of scan results (1 BSSes) 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Scan results: 1 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Selecting BSS from priority group 0 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): 0: 00:18:4d:c4:40:c4 ssid='Home001' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528):    skip - no WPA/RSN IE 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528):    selected non-WPA AP 00:18:4d:c4:40:c4 ssid='Home001' 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Trying to associate with 00:18:4d:c4:40:c4 (SSID='Home001' freq=2462 MHz) 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Cancelling scan request 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): WPA: clearing own WPA/RSN IE 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Automatic auth_alg selection: 0x1 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): WPA: clearing AP WPA IE 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): WPA: clearing AP RSN IE 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): WPA: clearing own WPA/RSN IE 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): ey clearing 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): wpa_driver_wext_set_drop_unencrypted 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): State: SCANNING -> ASSOCIATING 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): WEXT: Operstate: linkmode=-1, operstate=5 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): wpa_driver_wext_associate 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Setting authentication timeout: 10 sec 0 usec 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): EAPOL: External notification - portControl=ForceAuthorized 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Wireless event: cmd=0x8b06 len=8 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): CTRL_IFACE monitor attached - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 34 33 33 2d 37 00 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Wireless event: cmd=0x8b04 len=12 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Wireless event: cmd=0x8b1a len=16 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Authentication with 00:00:00:00:00:00 timed out. 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 34 33 33 2d 37 00 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Added BSSID 00:18:4d:c4:40:c4 into blacklist 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): State: ASSOCIATING -> DISCONNECTED 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): WEXT: Operstate: linkmode=-1, operstate=5 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): No keys have been configured - skip key clearing 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): EAPOL: External notification - portEnabled=0 
Mar 25 16:40:53 server1 NetworkManager: <information>^Iwpa_supplicant(5528): EAPOL: External notification - portValid=0 
Mar 25 16:41:02 server1 NetworkManager: <information>^Iwpa_supplicant(5528): sec 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): State: DISCONNECTED -> SCANNING 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Starting AP scan (broadcast SSID) 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Scan timeout - try to get results 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Received 224 bytes of scan results (1 BSSes) 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Scan results: 1 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Selecting BSS from priority group 0 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): 0: 00:18:4d:c4:40:c4 ssid='Home001' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528):    skip - no WPA/RSN IE 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528):    selected non-WPA AP 00:18:4d:c4:40:c4 ssid='Home001' 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Trying to associate with 00:18:4d:c4:40:c4 (SSID='Home001' freq=2462 MHz) 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 34 33 33 2d 37 00 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Cancelling scan request 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): WPA: clearing own WPA/RSN IE 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Automatic auth_alg selection: 0x1 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): WPA: clearing AP WPA IE 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): WPA: clearing AP RSN IE 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): WPA: clearing own WPA/RSN IE 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): No keys have been configured - skip key clearing 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): wpa_driver_wext_set_drop_unencrypted 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): State: SCANNING -> ASSOCIATING 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): WEXT: Operstate: linkmode=-1, operstate=5 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): wpa_driver_wext_associate 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Setting authentication timeout: 10 sec 0 usec 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): ForceAuthorized 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Wireless event: cmd=0x8b06 len=8 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Wireless event: cmd=0x8b04 len=12 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Wireless event: cmd=0x8b1a len=16 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Authentication with 00:00:00:00:00:00 timed out. 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 34 33 33 2d 37 00 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): BSSID 00:18:4d:c4:40:c4 blacklist count incremented to 2 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): State: ASSOCIATING -> DISCONNECTED 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): WEXT: Operstate: linkmode=-1, operstate=5 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): No keys have been configured - skip key clearing 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): EAPOL: External notification - portEnabled=0 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): EAPOL: External notification - portValid=0 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Setting scan request: 0 sec 0 usec 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): State: DISCONNECTED -> SCANNING 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Starting AP scan (broadcast SSID) 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Scan timeout - try to get results 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Received 224 bytes of scan results (1 BSSes) 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Scan results: 1 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Selecting BSS from priority group 0 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): 0: 00:18:4d:c4:40:c4 ssid='Home001' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528):    skip - blacklisted 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): No APs found - clear blacklist and try again 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): ) 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Selecting BSS from priority group 0 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): 0: 00:18:4d:c4:40:c4 ssid='Home001' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528):    skip - no WPA/RSN IE 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528):    selected non-WPA AP 00:18:4d:c4:40:c4 ssid='Home001' 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Trying to associate with 00:18:4d:c4:40:c4 (SSID='Home001' freq=2462 MHz) 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 34 33 33 2d 37 00 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Cancelling scan request 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): WPA: clearing own WPA/RSN IE 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Automatic auth_alg selection: 0x1 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): WPA: clearing AP WPA IE 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): WPA: clearing AP RSN IE 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): WPA: clearing own WPA/RSN IE 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): No keys have been configured - skip key clearing 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): wpa_driver_wext_set_drop_unencrypted 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): State: SCANNING -> ASSOCIATING 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): WEXT: Operstate: linkmode=-1, operstate=5 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): wpa_driver_wext_associate 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Setting authentication timeout: 10 sec 0 usec 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): EAPOL: External notification - portControl=ForceAuthorized 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Wireless event: cmd=0x8b06 len=8 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Wireless event: cmd=0x8b04 len=12 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Wireless event: cmd=0x8b1a len=16 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): d out. 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 34 33 33 2d 37 00 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Added BSSID 00:18:4d:c4:40:c4 into blacklist 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): State: ASSOCIATING -> DISCONNECTED 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): WEXT: Operstate: linkmode=-1, operstate=5 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): No keys have been configured - skip key clearing 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): EAPOL: External notification - portEnabled=0 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): EAPOL: External notification - portValid=0 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Setting scan request: 0 sec 0 usec 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): State: DISCONNECTED -> SCANNING 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Starting AP scan (broadcast SSID) 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Scan timeout - try to get results 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Received 224 bytes of scan results (1 BSSes) 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Scan results: 1 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Selecting BSS from priority group 0 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): 0: 00:18:4d:c4:40:c4 ssid='Home001' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528):    skip - no WPA/RSN IE 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528):    selected non-WPA AP 00:18:4d:c4:40:c4 ssid='Home001' 
Mar 25 16:41:22 server1 NetworkManager: <information>^Iwpa_supplicant(5528): Trying to associate with 00:18:4d:c4:40:c4 (SSID='Home001' freq=2462 MHz) 
Mar 25 16:41:43 server1 NetworkManager: <information>^IActivation (wlan0/wireless): association took too long (>60s), failing activation. 
Mar 25 16:41:43 server1 NetworkManager: <information>^IActivation (wlan0) failure scheduled... 
Mar 25 16:41:43 server1 NetworkManager: <information>^IActivation (wlan0) failed for access point (Home001) 
Mar 25 16:41:43 server1 NetworkManager: <information>^IActivation (wlan0) failed. 
Mar 25 16:41:43 server1 NetworkManager: <information>^IDeactivating device wlan0. 
Mar 25 16:41:43 server1 NetworkManager: <WARNING>^I nm_device_802_11_wireless_set_essid (): error setting ESSID to '' for device wlan0: Invalid argument 

```

---

### Post by scottpledger on 2007-03-25
In your /etc/network/interfaces file, did you comment out (by putting a '#' in front) all interfaces other than 'lo'?

---

### Post by bingnet on 2007-03-26
This worked for me, after I did this: [http://www.ubuntuforums.org/showpost.php?p=2296818&postcount=11](http://www.ubuntuforums.org/showpost.php?p=2296818&postcount=11)

I'm running Edgy 2.6.17-11 and my device is a 13b1:0026 Linksys WUSB54GSC.

---

### Post by mwells on 2007-03-26
Hi,

many thanks for the reply.

In response to scottpledger, I did infact comment out all the entries in /etc/network/interfaces . .many thanks for the suggestion though.

Interestingly I managed to get the connection up by issuing a 'sudo ifup wlan0' which then had the connection activated, and would work each time I restarted the computer, however this had a number of side effects;

1) The netwrok managed constantly showed 'no connection' in the task bar
2) The connection would just die after about 10 minutes and I had to restart the computer to get it up again
3) It added entries for wlan0 into the /etc/network/interfaces file

Its really frustrating because I now know I can at least get it working, its just this last few niggles!

Any help would therefore be greatly appreciated!

/Matt

---

### Post by leetcharmer on 2007-03-26
> **scottpledger said:**
> First, copy your 'dmesg' output (its whats going to tell us the most).  Then, post as much of the system log (/var/log/system.log) as you can.

Alright, I'm posting a zip file with all the files, also -- I just redid the tutorial after installing Fiesty Beta.  The restricted Drivers Manager didn't recognize the USB device as anything.

I'm not getting any wlan0 or eth1 to show up in Fiesty :/

---

### Post by mwells on 2007-03-26
Ok some further information incase it helps (fingers crossed . .as im totally lost now!!)

If I go into the standard networking configuration utility and check the 'enable' box for the wlan0 interface THEN close that window and type 'sudo ifup wlan0' the card wil grab a connection.

However in doing this it will add the below lines to the /etc/networking/interfaces file

```

iface wlan0 inet dhcp
wireless-essid Home001

auto wlan0

```

This then means that the networking manager will not do anything and shows 'no network connection' when i am connected to the net!

I could probably live with this if it were the only issue, but with me being connected to the net in this fashion the connection will then just suddenly die for no apparent reason . .

(I have noticed though that sudo ifup wlan0 issues the below report)
```

Listening on LPF/wlan0/00:18:39:0e:9e:88
Sending on   LPF/wlan0/00:18:39:0e:9e:88
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.5 -- renewal in 42802 seconds.

```

But it dies before this point . .ARRGGG!!!

By commenting out the interfaces in the /etc/networking/interfaces file networking manager does nothing and sudo ifup wlan0 will complain of an unknown interface (presumably as I have disabled it in the interfaces file)

please, any help would now be greatly appreciated as I am drawing a total blank!

Many thanks

/Matt

---

### Post by javaJake on 2007-03-26
> **leetcharmer said:**
> Alright, I'm posting a zip file with all the files, also -- I just redid the tutorial after installing Fiesty Beta.  The restricted Drivers Manager didn't recognize the USB device as anything.

I'm not getting any wlan0 or eth1 to show up in Fiesty :/

Hmmm, do you have ndiswrapper installed? It doesn't look like it loads ndiswrapper.

---

### Post by javaJake on 2007-03-26
> **mwells said:**
> Ok some further information incase it helps (fingers crossed . .as im totally lost now!!)

I'm not sure, but it looks like you are getting mixed up.

NetworkManager will only manage your device if you don't have it punched into /etc/network/interfaces file. Because you had it punched in, NetworkManager won't manage your card. In order for NetworkManager to use your device again, you not only have to edit the device out of the /etc/network/interfaces file, but you also have to restart NetworkManager. The easiest way is to restart your computer.

As far as ifup dying, I'd need more information on that. What does it do? Does it repeatedly say "DHCPDISCOVER" over and over? Does it just suddenly stop without a word about being unsucessful?

---

### Post by javaJake on 2007-03-26
> **bingnet said:**
> This worked for me, after I did this: [http://www.ubuntuforums.org/showpost.php?p=2296818&postcount=11](http://www.ubuntuforums.org/showpost.php?p=2296818&postcount=11)

I'm running Edgy 2.6.17-11 and my device is a 13b1:0026 Linksys WUSB54GSC.

Hmmm... looks like a folder change... thanks for that link!

---

### Post by leetcharmer on 2007-03-26
> **javaJake said:**
> Hmmm, do you have ndiswrapper installed? It doesn't look like it loads ndiswrapper.

yes, I have ndiswrapper installed and running, that is how I was able to complete the tutorial.  It says driver is installed and working properly.  It's ndiswrapper 1.38 from the fiesty repositories w/ ndiswrapper-utils 1.1.  I also installed the correct USB .sys files to their respective /etc/ndiswrapper/wusb54gsc folder.

---

### Post by javaJake on 2007-03-26
> **leetcharmer said:**
> yes, I have ndiswrapper installed and running, that is how I was able to complete the tutorial.  It says driver is installed and working properly.  It's ndiswrapper 1.38 from the fiesty repositories w/ ndiswrapper-utils 1.1.  I also installed the correct USB .sys files to their respective /etc/ndiswrapper/wusb54gsc folder.

OK, can you punch your device into the /etc/network/interfaces file and keep NetworkManager from using it? It "muddies" the logs with its messages. :)

---

### Post by leetcharmer on 2007-03-26
> **javaJake said:**
> OK, can you punch your device into the /etc/network/interfaces file and keep NetworkManager from using it? It "muddies" the logs with its messages. :)

you mean comment stuff out???  wlan0 is already in there.  I can't ifup wlan0 though, it says no such device.  Which is really awkward, because ndiswrapper should've aliased to wlan0

---

### Post by mwells on 2007-03-27
Hi there,

Thanks for the continued help JavaJake! I have now un commented the interfaces from the /etc/networking/interfaces file so that Network manager is not involved to see if I can stop the connection just dying after 1-15 minutes.

I left a syslog running last night to catch when it died (the output is below).

```

Mar 26 19:09:35 server1 dhclient: DHCPREQUEST on wlan0 to 255.255.255.255 port 67
Mar 26 19:09:35 server1 dhclient: DHCPACK from 192.168.0.1
Mar 26 19:09:35 server1 dhclient: bound to 192.168.0.5 -- renewal in 42802 seconds.
Mar 26 19:09:40 server1 nmbd[4439]: [2007/03/26 19:09:40, 0] nmbd/nmbd.c:process(596) 
Mar 26 19:09:40 server1 nmbd[4439]:   Got SIGHUP dumping debug info. 
Mar 26 19:09:40 server1 nmbd[4439]: [2007/03/26 19:09:40, 0] nmbd/nmbd_workgroupdb.c:dump_workgroups(284) 
Mar 26 19:09:40 server1 nmbd[4439]:   dump_workgroups() 
Mar 26 19:09:40 server1 nmbd[4439]:    dump workgroup on subnet     192.168.0.5: netmask=  255.255.255.0: 
Mar 26 19:09:40 server1 nmbd[4439]:   ^IMSHOME(1) current master browser = UNKNOWN 
Mar 26 19:09:40 server1 nmbd[4439]:   ^I^ISERVER1 40019a03 () 
Mar 26 19:09:40 server1 nmbd[4439]: [2007/03/26 19:09:40, 0] nmbd/nmbd_workgroupdb.c:dump_workgroups(284) 
Mar 26 19:09:40 server1 nmbd[4439]:   dump_workgroups() 
Mar 26 19:09:40 server1 nmbd[4439]:    dump workgroup on subnet  UNICAST_SUBNET: netmask=    192.168.0.5: 
Mar 26 19:09:40 server1 nmbd[4439]:   ^IMSHOME(1) current master browser = UNKNOWN 
Mar 26 19:09:40 server1 nmbd[4439]:   ^I^ISERVER1 40019a03 () 
Mar 26 19:09:45 server1 ntpdate[7009]: can't find host ntp.ubuntu.com 
Mar 26 19:09:45 server1 ntpdate[7009]: no servers can be used, exiting
Mar 26 19:17:01 server1 /USR/SBIN/CRON[7227]: (root) CMD (   run-parts --report /etc/cron.hourly)
Mar 26 19:37:53 server1 -- MARK --
Mar 26 19:57:53 server1 -- MARK --
Mar 26 20:17:01 server1 /USR/SBIN/CRON[9299]: (root) CMD (   run-parts --report /etc/cron.hourly)
Mar 26 20:22:19 server1 kernel: [17188634.700000] usb 4-4: USB disconnect, address 3
Mar 26 20:23:34 server1 NetworkManager: <WARNING>^I nm_device_802_11_wireless_get_mode (): error getting card mode on wlan0: Operation not supported 
Mar 26 20:23:34 server1 NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device wlan0: Operation not support
ed 
Mar 26 20:23:34 server1 NetworkManager: <WARNING>^I nm_device_802_11_wireless_get_mode (): error getting card mode on wlan0: Operation not supported 
Mar 26 20:23:34 server1 kernel: [17188710.064000] ndiswrapper (iw_get_infra_mode:261): getting operating mode failed (C000009D)
Mar 26 20:23:34 server1 kernel: [17188710.064000] ndiswrapper (set_scan:1178): scanning failed (C000009D)
Mar 26 20:23:34 server1 kernel: [17188710.064000] ndiswrapper (iw_get_infra_mode:261): getting operating mode failed (C000009D)
Mar 26 20:25:34 server1 NetworkManager: <WARNING>^I nm_device_802_11_wireless_get_mode (): error getting card mode on wlan0: Operation not supported 
Mar 26 20:25:34 server1 NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device wlan0: Operation not support
ed 


```

Any suggestions?

Once again thanks for all the help!

---

### Post by dsb on 2007-03-27
I've tried following the guide as closely as possible and with the correct additions to the custom rules file for the wusb54gsc linked to another other threads. ndiswrapper reports device and driver, but logs say otherwise, in fact looks like some serious errors, and no blinky lights :( 

Using fresh install of feisty and compiled the latest ndiswrapper;

```
me@mycomp:~/Desktop$ ndiswrapper -v
utils version: 1.9
driver version:        1.39
vermagic:       2.6.20-13-generic SMP mod_unload 586 

```

dmesg:
```
[ 1453.505891]  <3>ndiswrapper (load_wrap_driver:118): couldn't load driver wusb54gsc; check system log for messages from 'loadndisdriver'

```

and here is the relevant log info I think?

```
Mar 27 18:29:46 Canis-major kernel: [ 1453.505388] Process loadndisdriver (pid: 6720, ti=e91ee000 task=eb649030 task.ti=e91ee
000)
Mar 27 18:29:46 Canis-major kernel: [ 1453.505390] Stack: 00000000 b7e26000 c02f05cf 00000000 c03a7900 f8d8f228 e9d323f4 e963
113c 
Mar 27 18:29:46 Canis-major kernel: [ 1453.505400]        00000002 00000002 c0364ac5 00000000 00003200 00000006 00010000 0000
0000 
Mar 27 18:29:46 Canis-major kernel: [ 1453.505408]        00000000 f8d8ef0c 0000005c f8d8f3a8 f8d8fa34 f8d8f388 e963113c e963

Mar 27 18:29:46 Canis-major kernel: [ 1453.505417] Call Trace:
Mar 27 18:29:46 Canis-major kernel: [ 1453.505426]  [do_page_fault+831/1520] do_page_fault+0x33f/0x5f0
Mar 27 18:29:46 Canis-major kernel: [ 1453.505497]  [xfrm_state_add+248/496] xfrm_state_add+0xf8/0x1f0
Mar 27 18:29:46 Canis-major kernel: [ 1453.505506]  [__copy_from_user_ll+58/224] __copy_from_user_ll+0x3a/0xe0
Mar 27 18:29:46 Canis-major kernel: [ 1453.505524]  [<f8def114>] wrapper_ioctl+0x5e4/0xbf0 [ndiswrapper]
Mar 27 18:29:46 Canis-major kernel: [ 1453.505593]  [do_path_lookup+131/448] do_path_lookup+0x83/0x1c0
Mar 27 18:29:46 Canis-major kernel: [ 1453.505605]  [getname+167/208] getname+0xa7/0xd0
Mar 27 18:29:46 Canis-major kernel: [ 1453.505613]  [copy_to_user+41/80] copy_to_user+0x29/0x50
Mar 27 18:29:46 Canis-major kernel: [ 1453.505625]  [cp_new_stat64+249/272] cp_new_stat64+0xf9/0x110
Mar 27 18:29:46 Canis-major kernel: [ 1453.505643]  [filldir64+0/224] filldir64+0x0/0xe0
Mar 27 18:29:46 Canis-major kernel: [ 1453.505685]  [current_fs_time+80/96] current_fs_time+0x50/0x60
Mar 27 18:29:46 Canis-major kernel: [ 1453.505713]  [do_ioctl+120/144] do_ioctl+0x78/0x90
Mar 27 18:29:46 Canis-major kernel: [ 1453.505730]  [vfs_ioctl+92/672] vfs_ioctl+0x5c/0x2a0
Mar 27 18:29:46 Canis-major kernel: [ 1453.505749]  [sys_ioctl+114/144] sys_ioctl+0x72/0x90
Mar 27 18:29:46 Canis-major kernel: [ 1453.505766]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9
Mar 27 18:29:46 Canis-major kernel: [ 1453.505791]  [do_timer+2059/2080] do_timer+0x80b/0x820
Mar 27 18:29:46 Canis-major kernel: [ 1453.505796]  [xfrm_state_add+83/496] xfrm_state_add+0x53/0x1f0

Mar 27 18:29:46 Canis-major kernel: [ 1453.505821]  =======================
Mar 27 18:29:46 Canis-major kernel: [ 1453.505822] Code: c0 0c 01 85 c0 0f 84 c2 01 00 00 83 c1 01 8b 34 cd 20 9b e1 f8 85 f6
 75 d8 8b 0d 60 a6 e1 f8 85 c9 7e 68 8b 35 84 a4 e1 f8 89 d7 <ac> ae 75 08 84 c0 75 f8 31 c0 eb 04 19 c0 0c 01 85 c0 c7 44 24
 
Mar 27 18:29:46 Canis-major kernel: [ 1453.505869] EIP: [<f8dfca96>] link_pe_images+0x736/0xa50 [ndiswrapper] SS:ESP 0068:e91
efde4
Mar 27 18:29:46 Canis-major kernel: [ 1453.505891]  <3>ndiswrapper (load_wrap_driver:118): couldn't load driver wusb54gsc; ch
eck system log for messages from 'loadndisdriver'
Mar 27 18:29:46 Canis-major NetworkManager: <debug info>^I[1175045386.219377] nm_hal_device_added (): New device added (hal u
di is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0'). 
Mar 27 18:29:46 Canis-major NetworkManager: <debug info>^I[1175045386.266393] nm_hal_device_added (): New device added (hal u
di is '/org/freedesktop/Hal/devices/usb_device_13b1_26_8057_if1'). 
Mar 27 18:29:46 Canis-major NetworkManager: <debug info>^I[1175045386.287060] nm_hal_device_added (): New device added (hal u
di is '/org/freedesktop/Hal/devices/usb_device_13b1_26_8057_usbraw'). 

```

---

### Post by Teegro on 2007-03-28
whenever i run the 

> sudo ndiswrapper -i wusb54gsv2.inf

command i get a response which says 

> installing wusb54gsv2
couldn't copy wusb54gsv2.inf at /usr/sbin/ndiswrapper line 135

whatever this is is stopping me form installing the damn adaptor. For the record i have a different hard drive with xp on that i cna swap with this that lets me run the adaptor no problem.

---

### Post by javaJake on 2007-03-28
> **leetcharmer said:**
> you mean comment stuff out???  wlan0 is already in there.  I can't ifup wlan0 though, it says no such device.  Which is really awkward, because ndiswrapper should've aliased to wlan0

No, I mean uncomment them out, which means don't put any "#" in front of the lines for wlan0. This way NetworkManager will think "oh, that's being managed by the system, won't touch that" and you can use ifup.

---

### Post by javaJake on 2007-03-28
> **mwells said:**
> Hi there,

Thanks for the continued help JavaJake! I have now un commented the interfaces from the /etc/networking/interfaces file so that Network manager is not involved to see if I can stop the connection just dying after 1-15 minutes.

I left a syslog running last night to catch when it died (the output is below).

```

Mar 26 19:09:35 server1 dhclient: DHCPREQUEST on wlan0 to 255.255.255.255 port 67
Mar 26 19:09:35 server1 dhclient: DHCPACK from 192.168.0.1
Mar 26 19:09:35 server1 dhclient: bound to 192.168.0.5 -- renewal in 42802 seconds.
Mar 26 19:09:40 server1 nmbd[4439]: [2007/03/26 19:09:40, 0] nmbd/nmbd.c:process(596) 
Mar 26 19:09:40 server1 nmbd[4439]:   Got SIGHUP dumping debug info. 
Mar 26 19:09:40 server1 nmbd[4439]: [2007/03/26 19:09:40, 0] nmbd/nmbd_workgroupdb.c:dump_workgroups(284) 
Mar 26 19:09:40 server1 nmbd[4439]:   dump_workgroups() 
Mar 26 19:09:40 server1 nmbd[4439]:    dump workgroup on subnet     192.168.0.5: netmask=  255.255.255.0: 
Mar 26 19:09:40 server1 nmbd[4439]:   ^IMSHOME(1) current master browser = UNKNOWN 
Mar 26 19:09:40 server1 nmbd[4439]:   ^I^ISERVER1 40019a03 () 
Mar 26 19:09:40 server1 nmbd[4439]: [2007/03/26 19:09:40, 0] nmbd/nmbd_workgroupdb.c:dump_workgroups(284) 
Mar 26 19:09:40 server1 nmbd[4439]:   dump_workgroups() 
Mar 26 19:09:40 server1 nmbd[4439]:    dump workgroup on subnet  UNICAST_SUBNET: netmask=    192.168.0.5: 
Mar 26 19:09:40 server1 nmbd[4439]:   ^IMSHOME(1) current master browser = UNKNOWN 
Mar 26 19:09:40 server1 nmbd[4439]:   ^I^ISERVER1 40019a03 () 
Mar 26 19:09:45 server1 ntpdate[7009]: can't find host ntp.ubuntu.com 
Mar 26 19:09:45 server1 ntpdate[7009]: no servers can be used, exiting
Mar 26 19:17:01 server1 /USR/SBIN/CRON[7227]: (root) CMD (   run-parts --report /etc/cron.hourly)
Mar 26 19:37:53 server1 -- MARK --
Mar 26 19:57:53 server1 -- MARK --
Mar 26 20:17:01 server1 /USR/SBIN/CRON[9299]: (root) CMD (   run-parts --report /etc/cron.hourly)
Mar 26 20:22:19 server1 kernel: [17188634.700000] usb 4-4: USB disconnect, address 3
Mar 26 20:23:34 server1 NetworkManager: <WARNING>^I nm_device_802_11_wireless_get_mode (): error getting card mode on wlan0: Operation not supported 
Mar 26 20:23:34 server1 NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device wlan0: Operation not support
ed 
Mar 26 20:23:34 server1 NetworkManager: <WARNING>^I nm_device_802_11_wireless_get_mode (): error getting card mode on wlan0: Operation not supported 
Mar 26 20:23:34 server1 kernel: [17188710.064000] ndiswrapper (iw_get_infra_mode:261): getting operating mode failed (C000009D)
Mar 26 20:23:34 server1 kernel: [17188710.064000] ndiswrapper (set_scan:1178): scanning failed (C000009D)
Mar 26 20:23:34 server1 kernel: [17188710.064000] ndiswrapper (iw_get_infra_mode:261): getting operating mode failed (C000009D)
Mar 26 20:25:34 server1 NetworkManager: <WARNING>^I nm_device_802_11_wireless_get_mode (): error getting card mode on wlan0: Operation not supported 
Mar 26 20:25:34 server1 NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device wlan0: Operation not support
ed 


```

Any suggestions?

Once again thanks for all the help!

According to the log you gave me, you either didn't properly uncomment the devices in your networks file, or you didn't restart your computer after uncommenting. NetworkManager is still seing the devices and attempting to manage them. If you can't seem to stop NetworkManager from making the output you gave me, goto System -> Preferences -> Session, click on the "Startup Programs" tab, click on "nm-applet", and click the Disable button. You can come back later and Enable nm-applet when you get the internet working without NetworkManager.

---

### Post by javaJake on 2007-03-28
> **dsb said:**
> I've tried following the guide as closely as possible and with the correct additions to the custom rules file for the wusb54gsc linked to another other threads. ndiswrapper reports device and driver, but logs say otherwise, in fact looks like some serious errors, and no blinky lights :( 

Using fresh install of feisty and compiled the latest ndiswrapper;

```
me@mycomp:~/Desktop$ ndiswrapper -v
utils version: 1.9
driver version:        1.39
vermagic:       2.6.20-13-generic SMP mod_unload 586 

```

dmesg:
```
[ 1453.505891]  <3>ndiswrapper (load_wrap_driver:118): couldn't load driver wusb54gsc; check system log for messages from 'loadndisdriver'

```

and here is the relevant log info I think?

```
Mar 27 18:29:46 Canis-major kernel: [ 1453.505388] Process loadndisdriver (pid: 6720, ti=e91ee000 task=eb649030 task.ti=e91ee
000)
Mar 27 18:29:46 Canis-major kernel: [ 1453.505390] Stack: 00000000 b7e26000 c02f05cf 00000000 c03a7900 f8d8f228 e9d323f4 e963
113c 
Mar 27 18:29:46 Canis-major kernel: [ 1453.505400]        00000002 00000002 c0364ac5 00000000 00003200 00000006 00010000 0000
0000 
Mar 27 18:29:46 Canis-major kernel: [ 1453.505408]        00000000 f8d8ef0c 0000005c f8d8f3a8 f8d8fa34 f8d8f388 e963113c e963

Mar 27 18:29:46 Canis-major kernel: [ 1453.505417] Call Trace:
Mar 27 18:29:46 Canis-major kernel: [ 1453.505426]  [do_page_fault+831/1520] do_page_fault+0x33f/0x5f0
Mar 27 18:29:46 Canis-major kernel: [ 1453.505497]  [xfrm_state_add+248/496] xfrm_state_add+0xf8/0x1f0
Mar 27 18:29:46 Canis-major kernel: [ 1453.505506]  [__copy_from_user_ll+58/224] __copy_from_user_ll+0x3a/0xe0
Mar 27 18:29:46 Canis-major kernel: [ 1453.505524]  [<f8def114>] wrapper_ioctl+0x5e4/0xbf0 [ndiswrapper]
Mar 27 18:29:46 Canis-major kernel: [ 1453.505593]  [do_path_lookup+131/448] do_path_lookup+0x83/0x1c0
Mar 27 18:29:46 Canis-major kernel: [ 1453.505605]  [getname+167/208] getname+0xa7/0xd0
Mar 27 18:29:46 Canis-major kernel: [ 1453.505613]  [copy_to_user+41/80] copy_to_user+0x29/0x50
Mar 27 18:29:46 Canis-major kernel: [ 1453.505625]  [cp_new_stat64+249/272] cp_new_stat64+0xf9/0x110
Mar 27 18:29:46 Canis-major kernel: [ 1453.505643]  [filldir64+0/224] filldir64+0x0/0xe0
Mar 27 18:29:46 Canis-major kernel: [ 1453.505685]  [current_fs_time+80/96] current_fs_time+0x50/0x60
Mar 27 18:29:46 Canis-major kernel: [ 1453.505713]  [do_ioctl+120/144] do_ioctl+0x78/0x90
Mar 27 18:29:46 Canis-major kernel: [ 1453.505730]  [vfs_ioctl+92/672] vfs_ioctl+0x5c/0x2a0
Mar 27 18:29:46 Canis-major kernel: [ 1453.505749]  [sys_ioctl+114/144] sys_ioctl+0x72/0x90
Mar 27 18:29:46 Canis-major kernel: [ 1453.505766]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9
Mar 27 18:29:46 Canis-major kernel: [ 1453.505791]  [do_timer+2059/2080] do_timer+0x80b/0x820
Mar 27 18:29:46 Canis-major kernel: [ 1453.505796]  [xfrm_state_add+83/496] xfrm_state_add+0x53/0x1f0

Mar 27 18:29:46 Canis-major kernel: [ 1453.505821]  =======================
Mar 27 18:29:46 Canis-major kernel: [ 1453.505822] Code: c0 0c 01 85 c0 0f 84 c2 01 00 00 83 c1 01 8b 34 cd 20 9b e1 f8 85 f6
 75 d8 8b 0d 60 a6 e1 f8 85 c9 7e 68 8b 35 84 a4 e1 f8 89 d7 <ac> ae 75 08 84 c0 75 f8 31 c0 eb 04 19 c0 0c 01 85 c0 c7 44 24
 
Mar 27 18:29:46 Canis-major kernel: [ 1453.505869] EIP: [<f8dfca96>] link_pe_images+0x736/0xa50 [ndiswrapper] SS:ESP 0068:e91
efde4
Mar 27 18:29:46 Canis-major kernel: [ 1453.505891]  <3>ndiswrapper (load_wrap_driver:118): couldn't load driver wusb54gsc; ch
eck system log for messages from 'loadndisdriver'
Mar 27 18:29:46 Canis-major NetworkManager: <debug info>^I[1175045386.219377] nm_hal_device_added (): New device added (hal u
di is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0'). 
Mar 27 18:29:46 Canis-major NetworkManager: <debug info>^I[1175045386.266393] nm_hal_device_added (): New device added (hal u
di is '/org/freedesktop/Hal/devices/usb_device_13b1_26_8057_if1'). 
Mar 27 18:29:46 Canis-major NetworkManager: <debug info>^I[1175045386.287060] nm_hal_device_added (): New device added (hal u
di is '/org/freedesktop/Hal/devices/usb_device_13b1_26_8057_usbraw'). 

```

Holy smoley, that's an ndiswrapper crash right there! I recommend that you head over to the ndiswrapper mailing lists and ask them about these crashes. I won't be any help here.

Ndiswrapper Mailing List:
[https://lists.sourceforge.net/lists/listinfo/ndiswrapper-general](https://lists.sourceforge.net/lists/listinfo/ndiswrapper-general)

I recommend you tell them basically what you told me, but link to this thread so they know what you tried to do. Essentially, tell them your system, ndiswrapper version, your device you tried to use, what you tried to do to get it to work, and what the crash log says.

Wishing you luck! :)

---

### Post by javaJake on 2007-03-28
> **Teegro said:**
> whatever this is is stopping me form installing the damn adaptor. For the record i have a different hard drive with xp on that i cna swap with this that lets me run the adaptor no problem.

Are you running the command with "sudo" in the front? That could cause the error. If you can't do it through ndiswrapper, you can also manually copy it into /etc/ndiswrapper/wusb54gsv2 folder, though I don't recommend this unless necessary.

---

### Post by mwells on 2007-03-29
Hi javaJake,

I disabled network manager as per your instructions;

Below is the dmesg output;

```

[17179578.236000] usb 4-6: new high speed USB device using ehci_hcd and address 3
[17179578.368000] usb 4-6: no configuration chosen from 1 choice
[17179578.608000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[17179578.784000] usb 2-1: configuration #1 chosen from 1 choice
[17179589.700000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179589.704000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179590.028000] irda_init()
[17179590.028000] NET: Registered protocol family 23
[17179590.272000] 8139too Fast Ethernet driver 0.9.27
[17179590.272000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179590.272000] eth0: RealTek RTL8139 at 0xe09dc000, 00:40:ca:4f:0e:31, IRQ 185
[17179590.272000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179590.328000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179590.568000] parport: PnPBIOS parport detected.
[17179590.568000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179590.668000] Floppy drive(s): fd0 is 1.44M
[17179590.684000] FDC 0 is a post-1991 82077
[17179590.776000] Linux agpgart interface v0.101 (c) Dave Jones
[17179590.820000] agpgart: Detected VIA PM266/KM266 chipset
[17179590.824000] agpgart: AGP aperture is 64M @ 0xe8000000
[17179590.916000] input: PC Speaker as /class/input/input1
[17179591.500000] usbcore: registered new driver hiddev
[17179591.520000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[17179591.520000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.1-1
[17179591.520000] usbcore: registered new driver usbhid
[17179591.520000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179591.580000] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[17179591.580000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[17179591.580000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 201
[17179591.580000] PCI: Via IRQ fixup for 0000:00:11.5, from 10 to 9
[17179591.580000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179591.628000] ts: Compaq touchscreen protocol output
[17179591.652000] usbcore: registered new driver cdc_ether
[17179591.656000] usb 4-6: bad CDC descriptors
[17179591.656000] usbcore: registered new driver rndis_host
[17179592.332000] lp0: using parport0 (interrupt-driven).
[17179592.356000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179592.356000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179592.388000] Bluetooth: Core ver 2.8
[17179592.388000] NET: Registered protocol family 31
[17179592.388000] Bluetooth: HCI device and connection manager initialized
[17179592.388000] Bluetooth: HCI socket layer initialized
[17179592.392000] Bluetooth: L2CAP ver 2.8
[17179592.392000] Bluetooth: L2CAP socket layer initialized
[17179592.396000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179592.424000] ndiswrapper version 1.39 loaded (smp=yes)
[17179592.576000] usb 4-6: reset high speed USB device using ehci_hcd and address 3
[17179592.732000] ndiswrapper: driver wusb54gsv2 (Linksys,01/25/2005, 4.01.20.0) loaded
[17179593.240000] wlan0: ethernet device 00:18:39:0e:9e:88 using NDIS driver: wusb54gsv2, version: 0x4011405, NDIS version: 0x501, vendor: 'Linksys Wireless-G USB Network Adapter with SpeedBooster', 13B1:0014.F.conf
[17179593.256000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179593.268000] usbcore: registered new driver ndiswrapper
[17179593.312000] Adding 1510068k swap on /dev/disk/by-uuid/bc418f06-6cd9-4507-8a2d-3f176761db46.  Priority:-1 extents:1 across:1510068k
[17179593.408000] EXT3 FS on hdb1, internal journal
[17179593.648000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179593.688000] NTFS volume version 3.1.
[17179593.724000] NTFS volume version 3.1.
[17179594.428000] NET: Registered protocol family 17
[17179594.976000] ACPI: Power Button (FF) [PWRF]
[17179594.976000] ACPI: Power Button (CM) [PWRB]
[17179595.104000] ibm_acpi: ec object not found
[17179595.136000] pcc_acpi: loading...
[17179597.376000] [drm] Initialized drm 1.0.1 20051102
[17179597.392000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 209
[17179597.396000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[17179598.048000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x4000000
[17179598.048000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x4000000
[17179598.048000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x4000000
[17179598.048000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179598.048000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[17179598.048000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[17179598.412000] [drm] Setting GART location based on new memory map
[17179598.412000] [drm] Loading R200 Microcode
[17179598.412000] [drm] writeback test succeeded in 1 usecs
[17179602.220000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179602.220000] apm: overridden by ACPI.
[17179605.704000] eth0: link down


```

This is all working fine now on startup, but all of a sudden it will just stop working :( and all I can see in the logs is;

```

Mar 28 21:23:34 server1 kernel: [17184416.804000] usb 4-6: USB disconnect, address 3
Mar 28 21:24:21 server1 kernel: [17184463.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:24:29 server1 kernel: [17184471.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:24:37 server1 kernel: [17184479.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:24:45 server1 kernel: [17184487.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:24:53 server1 kernel: [17184495.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:25:01 server1 kernel: [17184503.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:25:07 server1 nmbd[4481]: [2007/03/28 21:25:07, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396) 
Mar 28 21:25:07 server1 nmbd[4481]:   ***** 
Mar 28 21:25:07 server1 nmbd[4481]:    
Mar 28 21:25:07 server1 nmbd[4481]:   Samba name server SERVER1 is now a local master browser for workgroup MSHOME on subnet 192
.168.0.5 
Mar 28 21:25:07 server1 nmbd[4481]:    
Mar 28 21:25:07 server1 nmbd[4481]:   ***** 
Mar 28 21:25:07 server1 nmbd[4481]: [2007/03/28 21:25:07, 0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(353) 
Mar 28 21:25:07 server1 nmbd[4481]:   find_domain_master_name_query_fail: 
Mar 28 21:25:07 server1 nmbd[4481]:   Unable to find the Domain Master Browser name MSHOME<1b> for the workgroup MSHOME. 
Mar 28 21:25:07 server1 nmbd[4481]:   Unable to sync browse lists in this workgroup. 
Mar 28 21:25:09 server1 kernel: [17184511.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:25:17 server1 kernel: [17184519.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:25:25 server1 kernel: [17184527.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:25:33 server1 kernel: [17184535.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:25:41 server1 kernel: [17184543.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:25:49 server1 kernel: [17184551.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:25:57 server1 kernel: [17184559.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:26:05 server1 kernel: [17184567.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:26:13 server1 kernel: [17184575.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:26:21 server1 kernel: [17184583.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:26:29 server1 kernel: [17184591.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:26:37 server1 kernel: [17184599.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:26:45 server1 kernel: [17184607.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:26:53 server1 kernel: [17184615.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:27:01 server1 kernel: [17184623.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:27:09 server1 kernel: [17184631.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:27:17 server1 kernel: [17184639.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:27:25 server1 kernel: [17184647.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:27:33 server1 kernel: [17184655.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:27:41 server1 kernel: [17184663.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:27:49 server1 kernel: [17184671.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:27:57 server1 kernel: [17184679.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:28:05 server1 kernel: [17184687.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:28:13 server1 kernel: [17184695.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:28:21 server1 kernel: [17184703.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:28:29 server1 kernel: [17184711.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:28:37 server1 kernel: [17184719.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:28:45 server1 kernel: [17184727.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset


``` 

So for some reason the device is just suddenly being disconnected :(

Also just incase it helps here is the result of trying to restart networking once it has broken;

```

matthew@server1:/var/log$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                                                                          There is already a pid file /var/run/dhclient.wlan0.pid with pid 3523
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:18:39:0e:9e:88
Sending on   LPF/wlan0/00:18:39:0e:9e:88
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Invalid argument.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Invalid argument.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:18:39:0e:9e:88
Sending on   LPF/wlan0/00:18:39:0e:9e:88
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7

```

Any ideas?

Many many thanks for all the help, I'm desperate to get this working!

/Matt

---

### Post by Lost_Soldier on 2007-03-29
I looked through the other pages and found that other users don't get their lights to turn on either, but my circumstances seem to be different.

I have the wusbgsv2

> phillip@delta780:~$ ndiswrapper -l
wusb54gsv2 : driver installed
        device (13B1:0014) present

And the odd part...
> phillip@delta780:~$ ndiswrapper -a 13b1:0014 WUSB54GSv2.inf
ls: /etc/ndiswrapper/WUSB54GSv2.inf/: No such file or directory
driver 'WUSB54GSv2.inf' is not installed (properly)!

Wtf?

---

### Post by javaJake on 2007-03-29
> **Lost_Soldier said:**
> Wtf?

Well, for that second command you actually don't want to say what the driver is, but what the *device* is, which, in your case, is the WUSB54GSv2.

---

### Post by Lost_Soldier on 2007-03-29
So i would type in
> ndiswrapper -a 13b1:0014 wusbg54gsv2
instead?

That gives me an error 

> phillip@delta780:~$ ndiswrapper -a 13b1:0014 wusb54gsv2
couldn't create symlink for "13B1:0014.F.conf": File exists -
installation may be incomplete
driver 'wusb54gsv2' is not installed (properly)!


Do i need to try a different USB port or something?

---

### Post by javaJake on 2007-03-29
> **mwells said:**
> This is all working fine now on startup, but all of a sudden it will just stop working :( and all I can see in the logs is;

```

Mar 28 21:23:34 server1 kernel: [17184416.804000] usb 4-6: USB disconnect, address 3
Mar 28 21:24:21 server1 kernel: [17184463.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:24:29 server1 kernel: [17184471.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:24:37 server1 kernel: [17184479.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:24:45 server1 kernel: [17184487.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:24:53 server1 kernel: [17184495.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:25:01 server1 kernel: [17184503.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:25:07 server1 nmbd[4481]: [2007/03/28 21:25:07, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396) 
Mar 28 21:25:07 server1 nmbd[4481]:   ***** 
Mar 28 21:25:07 server1 nmbd[4481]:    
Mar 28 21:25:07 server1 nmbd[4481]:   Samba name server SERVER1 is now a local master browser for workgroup MSHOME on subnet 192
.168.0.5 
Mar 28 21:25:07 server1 nmbd[4481]:    
Mar 28 21:25:07 server1 nmbd[4481]:   ***** 
Mar 28 21:25:07 server1 nmbd[4481]: [2007/03/28 21:25:07, 0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(353) 
Mar 28 21:25:07 server1 nmbd[4481]:   find_domain_master_name_query_fail: 
Mar 28 21:25:07 server1 nmbd[4481]:   Unable to find the Domain Master Browser name MSHOME<1b> for the workgroup MSHOME. 
Mar 28 21:25:07 server1 nmbd[4481]:   Unable to sync browse lists in this workgroup. 
Mar 28 21:25:09 server1 kernel: [17184511.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:25:17 server1 kernel: [17184519.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:25:25 server1 kernel: [17184527.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:25:33 server1 kernel: [17184535.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:25:41 server1 kernel: [17184543.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:25:49 server1 kernel: [17184551.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:25:57 server1 kernel: [17184559.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:26:05 server1 kernel: [17184567.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:26:13 server1 kernel: [17184575.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:26:21 server1 kernel: [17184583.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:26:29 server1 kernel: [17184591.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:26:37 server1 kernel: [17184599.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:26:45 server1 kernel: [17184607.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:26:53 server1 kernel: [17184615.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:27:01 server1 kernel: [17184623.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:27:09 server1 kernel: [17184631.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:27:17 server1 kernel: [17184639.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:27:25 server1 kernel: [17184647.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:27:33 server1 kernel: [17184655.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:27:41 server1 kernel: [17184663.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:27:49 server1 kernel: [17184671.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:27:57 server1 kernel: [17184679.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:28:05 server1 kernel: [17184687.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:28:13 server1 kernel: [17184695.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:28:21 server1 kernel: [17184703.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:28:29 server1 kernel: [17184711.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:28:37 server1 kernel: [17184719.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 21:28:45 server1 kernel: [17184727.612000] ndiswrapper (miniport_reset:72): wlan0 is being reset
``` 

So for some reason the device is just suddenly being disconnected :(

Also just incase it helps here is the result of trying to restart networking once it has broken;

```

matthew@server1:/var/log$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                                                                          There is already a pid file /var/run/dhclient.wlan0.pid with pid 3523
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:18:39:0e:9e:88
Sending on   LPF/wlan0/00:18:39:0e:9e:88
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Invalid argument.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Invalid argument.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:18:39:0e:9e:88
Sending on   LPF/wlan0/00:18:39:0e:9e:88
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7

```

Any ideas?

Many many thanks for all the help, I'm desperate to get this working!

/Matt

Some Googling brings up a solution:
[http://lists.debian.org/debian-amd64/2005/12/msg00702.html](http://lists.debian.org/debian-amd64/2005/12/msg00702.html)

Not sure if this'll work, so if it doesn't I recommend you remove it since I don't know what it does myself. :P

Beyond the above, I recommend going to the ndiswrapper mailing list. You at least got it working for a little bit. :roll:

---

### Post by javaJake on 2007-03-29
> **Lost_Soldier said:**
> Do i need to try a different USB port or something?

No... can you give me the output of the following command? I'm not sure why it'd say it isn't installed properly just because it can't add the USB ID you punched in.

```
ls /etc/ndiswrapper/wusb54gsv2
```

---

### Post by Lost_Soldier on 2007-03-29
Here it is:
> phillip@delta780:~$ ls /etc/ndiswrapper/wusb54gsv2
13B1:0014.F.conf  rndismp.sys  usb8023.sys  wusb54gsv2.inf
phillip@delta780:~$ 


---

### Post by dsb on 2007-03-30
I figured as much, having seen a fair share of linux output that is not quite easily parsed...?

But, I'm suspecting a hardware problem with this particular little stick, since it has problems, even with the winders.

Nevertheless, outstanding howto guide and responses. 

After having read this quide, I am curious to once again retry my USR805422 ( for those wanting to test?) which works almost flawlessly in windows, and I'm beginning to suspect that its that 99 rules to turn on the power for the device to get for blinky lights? :confused: But I will leave for another thread and only here mention, because it seems to be a common problem for feisty users and wireless....

---

### Post by javaJake on 2007-03-30
> **dsb said:**
> it seems to be a common problem for feisty users and wireless....

It absolutely is. This has been addressed in a "bug" report, and they've decided on making the message easier to understand then "no configuration chosen". All we need now is to have Gnome pick this message up and let you know....

---

### Post by bobplano on 2007-04-01
im having a bit of trouble with making this work. i type in the first command and it updates everything i need but when i try to do make it comes up with:

```


make -C driver
make[1]: Entering directory `/home/keith/My Documents/ndiswrapper-files/ndiswrapper-1.28/driver'
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/home/keith/My Documents/ndiswrapper-files/ndiswrapper-1.28/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
make[2]: *** No rule to make target `Documents/ndiswrapper-files/ndiswrapper-1.28/driver'.  Stop.
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/keith/My Documents/ndiswrapper-files/ndiswrapper-1.28/driver'
make: *** [all] Error 2


```

could someone please help me figure this out? i dont understand any of this output.

edit: yayy i figured it out myself, it didnt like the place i put the files

---

### Post by javaJake on 2007-04-01
> **bobplano said:**
> edit: yayy i figured it out myself, it didnt like the place i put the files

Al-right! :)

Let me know if you get the rest of the way.

---

### Post by mwells on 2007-04-02
Hi all,

Well, after some serious playing around I think I have found a solution to the random disconnect and the kernal "usb:disconnect" error.

The problem seems to come up in a number of bug reports I have read and as such the following code has (seemingly) solved the issue (the macine has been online for 2 days now (though I havn't restarted and tried again!)

> sudo modprobe -r ehci_hcd 

I think what the code above is doing is removing the usb2 driver from the kernal forcing the use of )possibly) the usb1.0, though I havn't noticed any difference in network speed.

However I could be wrong, and will be reading up about this today

Many thanks for the excellent howto

/Matt

---

### Post by oskarmat on 2007-04-03
Hi Javajake, Oskarmat here. I just realized ( a month late) that I got an answer from you about the Belkin F5D7051, from which I understood i was on the right path, but that I definetely need addional help. I know this is not the device of the HowTo but, believe me, there is son many people looking around into the forums for the Belkin F5D7051, that if you found a solution for that you would become their hero! 
What can i tell you right now is that yes, the device gets a "no configuration chosen from 1 configuration" evytime I plug it in. 
I will provide you the content of the /var/log/syslog after I plug in the device and wait for 20 secs. 

I would really appreciate your help.

---

### Post by 92 GSR-4 on 2007-04-08
I need some help getting the wusb54GS version 2 working. I followed the tutorial to the best of my ability. Since I have no internet connection on that PC, other than using the USB wireless, I used a USB thumb drive to transfer files from my XP system to the linux system.

  First off, I obtained the latest ndiswrapper and extracted it into my home folder in it's own directory (ndiswrapper-1.41). Next, I saved rndismp.sys, usb8023.sys and WUSB54GSV2.inf into the home folder. In the terminal I followed the turtorial and everything went according to the plan. When I use the code: sudo ndiswrapper -l , I get the following:

Driver Installed
  Device (13B1:0014) present

  However, when plugged in no light comes on and theres only a "wired connection" showing up in System>Admin>networking.

Is there any advice on this? Thanks

Edit: I also followed the instructions for keeping the USB power for Edgy systems (which is what I'm using, Ubuntu Edgy 6.10 I believe)

---

### Post by javaJake on 2007-04-08
> **92 GSR-4 said:**
> Is there any advice on this?

Tell me if you see any "no configuration chosen" messages in /var/log/syslog after plugging in your device.

Also, if you see "no configuration chosen", tell me what the two below commands say with your device plugged in:
```

lsusb
cat /etc/udev/rules.d/99-custom.rules

```

---

### Post by 92 GSR-4 on 2007-04-08
ok yes in my syslog there were many instances of "No configuration chosen". Here are the commands and outcomes you told me to get:

topper348@topper348-desktop:~$ lsusb
Bus 005 Device 003: ID 13b1:0014 Linksys 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

topper348@topper348-desktop:~$ cat /etc/udev/rules.d/99-custom.rules
BUS=="usb", SYSFS{idProduct}=="0014", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"
topper348@topper348-desktop:~$

---

### Post by 92 GSR-4 on 2007-04-10
Not to be a squeaky wheel.... :-\" 

I wiped the hard drive again just to start from a clean slate. I reinstalled Ubuntu, ran through the directions, and ended up getting the exact same results as before. ndiswrapper -l still shows the driver installed and the device present.

Also the above commands and results are the same now, too. Thanks for the help. I hope to get this running soon!:)

---

### Post by javaJake on 2007-04-11
> **92 GSR-4 said:**
> ok yes in my syslog there were many instances of "No configuration chosen".

Can you give me the actual chunk that talks about the device? Believe it or not, there's some very useful numbers in there....

**Edit:** Almost forgot to say that everything looks good as long as you are using the WUSB54GS v1. If your chunk you will give me (I requested it above) reports the WUSB54GS v1 numbers, then I'd check iwconfig next for any wireless devices.

---

### Post by 92 GSR-4 on 2007-04-14
JavaJake,

  I went back into the syslog...and found a very short log with no occurences of "No configuration chosen". I looked at syslog0 next, and found that it contains events from previous dates. Due to the filesize limits of this site, I can only give you a small protion of syslog0. But it contains "No Configuration Chosen" and a little of the surrounding chunk I thought might be important. The attachment is included in this post.

> **javaJake said:**
>  Almost forgot to say that everything looks good as long as you are using the WUSB54GS v1. If your chunk you will give me (I requested it above) reports the WUSB54GS v1 numbers, then I'd check iwconfig next for any wireless devices.

In my case I'm using the WUSB54GS **V2**. Maybe that's the problem? I'll go back and look, but I could swear I put everything in for the Version 2 device. 

Lastly, I tried iwconfig and got "no wireless extensions" for all 3. 

Thanks for everything JavaJake!

---

### Post by scottpledger on 2007-04-14
> **mwells said:**
> Hi,

many thanks for the reply.

In response to scottpledger, I did infact comment out all the entries in /etc/network/interfaces . .many thanks for the suggestion though.

Interestingly I managed to get the connection up by issuing a 'sudo ifup wlan0' which then had the connection activated, and would work each time I restarted the computer, however this had a number of side effects;

1) The netwrok managed constantly showed 'no connection' in the task bar
2) The connection would just die after about 10 minutes and I had to restart the computer to get it up again
3) It added entries for wlan0 into the /etc/network/interfaces file

Its really frustrating because I now know I can at least get it working, its just this last few niggles!

Any help would therefore be greatly appreciated!

/Matt

Well, if the problem still is that by default, it is looking for IPv6 routers, then you may want to try this...

run:
```
sudo gedit /etc/modprobe.d/aliases
```
and modify that file such that what used to be:
```
alias net-pf-10 ipv6
```
is now:
```
alias net-pf-10 off ipv6
```
and see if that doesn't work for you.

---

### Post by javaJake on 2007-04-15
> **92 GSR-4 said:**
> In my case I'm using the WUSB54GS **V2**. Maybe that's the problem? I'll go back and look, but I could swear I put everything in for the Version 2 device. 

That's strange... your device is saying its a v1. Set everything like it's a v1, and see if that fixes it...

---

### Post by 92 GSR-4 on 2007-04-16
Update: It's a version **2.1**. I'll change everything to the version 1 just to see. That includes the driver file and the 99-rules, right?

---

### Post by javaJake on 2007-04-18
> **92 GSR-4 said:**
> Update: It's a version **2.1**. I'll change everything to the version 1 just to see. That includes the driver file and the 99-rules, right?

Try the 99-rules file first, then if that doesn't work, redo both. I'm not sure if it's the v1 redone, or if it's just a relabled v2.

---

### Post by Guitar John on 2007-04-23
Recently upgraded to Feisty.  All is well.  Installed NDISWRAPPER from repositories (it is now version 1.38 ).  So far, so good.  I have WUSB54GS v1.  This is the part where I get stuck.  

> My guess is that you'll come back to this tutorial wondering what went wrong, right? Ndiswrapper reports "invalid driver" instead of "driver present", right? Well, if I'm wrong, skip the rest of this step.

The last command says that the drivers are invalid. That's because it didn't install the sys files! We need to do this manually. Run these commands, assuming you haven't closed the terminal since the last few commands:

WUSB54GS v2:
Code:

sudo cp usb8023.sys /etc/ndiswrapper/wusb54gsv2/
sudo cp rndismp.sys /etc/ndiswrapper/wusb54gsv2/

WUSB54GS v1:
Code:

sudo cp usb8023.sys /etc/ndiswrapper/wusb54gs/
sudo cp rndismp.sys /etc/ndiswrapper/wusb54gs/

Now run this command:

Code:

ndiswrapper -l

It should work!




My output from > ndiswrapper -l  looks like this  > jcw@jcw-desktop:~$ ndiswrapper -l
lsbcmnds : invalid driver!
WARNING: Failed to open config file /etc/modprobe.d/alsa-base.save: Permission denied
wusb54gs : driver installed
        device (13B1:000E) present
jcw@jcw-desktop:~$ 



Help!

---

### Post by javaJake on 2007-04-23
> **Guitar John said:**
> Recently upgraded to Feisty.  All is well.  Installed NDISWRAPPER from repositories (it is now version 1.38 ).  So far, so good.  I have WUSB54GS v1.  This is the part where I get stuck.

OK, try running "sudo ndiswrapper -l" instead. That should work. Ndiswrapper should run just fine since the driver runs in sudo anyway.

Try going to the next step after telling me if the "sudo ndiswrapper -l" command runs and see if it'll work.

---

### Post by CanardoKeyser on 2007-04-25
(ok, don't shoot me just yet for not posting information: I am at work so I don't have the output from dmesg etc.... readily available.)

first off, great how-to :-)

However, I have a WUSB54GS v2 and it's not working...

running Ubuntu FF, ndiswrapper 1.38 and everything goes well actually, I follow the instructions and in the end my adapter is recognized.

but...

1) if it's plugged in while booting, boot will freeze (or hold for a long time) after three squares (of the progress bar).
when I let computer boot, then plug it in (before or after logging in), the adapter is recognized and the power light turns green, and the link one starts blinking (not constantly, but it will flicker for a while, then stop, then begin again)
2) after a few minutes, my computer freezes up if the adapter is hooked up
3) regardless of whether I use NM or /etc/network/interfaces, the adapter can't find any routers/access points
4) if I ask NM to scan, my computer freezes up too

Anybody know what is causing this or what I can do to prevent this from happening?

Let me know what information you want me to post.

[edit]the only thing I can say for sure (without being at the computer in question) is that in dmesg, there are entries for the wlan0 being hooked up, you know, the regular messages, and then later on: ndiswrapper: device wlan0 was removed (and after that, the same entries for plugging in/"finding"  the wireless adapter again (followed by ndiswrapper: device wlan0 was removed again), etc...)
[/edit]

[edit2]what I have done:
the usual steps, right up to "99-custom"
tried several versions of the drivers
tried it with /etc/network/interfaces as is (I did comment out the others, but just left the 2 lines for wlan0)
tried it with adding lines for the ssid, etc.... in /etc/network/interfaces
tried it with commenting everything out and doing ifconfig wlan0 up, etc...
everything leads to a freeze (and no network finding)
[/edit2]

Thanks in advance

PS: As for me, I am new to Ubuntu, not that new to Linux, I usually have a dual windows/linux boot on my computer, and do have some, albeit rusty, knowledge of linux :-) and even though I am at work, I could dash over to home to retrieve the information you want me to post

---

### Post by Guitar John on 2007-04-25
> **javaJake said:**
> OK, try running "sudo ndiswrapper -l" instead. That should work. Ndiswrapper should run just fine since the driver runs in sudo anyway.

Try going to the next step after telling me if the "sudo ndiswrapper -l" command runs and see if it'll work.

Here's what I got.  The drivers I used are part of the attachment from the original post.


> jcw@jcw-desktop:~$ sudo ndiswrapper -l
Password:
lsbcmnds : invalid driver!
wusb54gs : driver installed
        device (13B1:000E) present
jcw@jcw-desktop:~$ 




---

### Post by Guitar John on 2007-04-25
I did the following:  

> WITHOUT THE ATTACHMENT
If you don't have a Windows XP installation (scroll down if you do have XP) then you can get the files from F5D7051.exe here:
[http://www.belkin.com/support/downlo...ad=1871&lang=1](http://www.belkin.com/support/downlo...ad=1871&lang=1)

To unzip the EXE, run:

Code:

unzip F5D7051.exe



It looks like the same .sys files are there although rndismp.sys from the attachment that was originally posted is called RNDISMPK.SYS in the download from the Belkin website.   I await further instructions.

Thank you.
GJ

---

### Post by javaJake on 2007-04-27
> **CanardoKeyser said:**
> (ok, don't shoot me just yet for not posting information: I am at work so I don't have the output from dmesg etc.... readily available.)I won't shoot you, I'll just scream, stomp, run around in circles, rant unreasonably... ;)

> **CanardoKeyser said:**
> first off, great how-to :-)Thanks. :)

> **CanardoKeyser said:**
> but...

1) if it's plugged in while booting, boot will freeze (or hold for a long time) after three squares (of the progress bar).
when I let computer boot, then plug it in (before or after logging in), the adapter is recognized and the power light turns green, and the link one starts blinking (not constantly, but it will flicker for a while, then stop, then begin again)
2) after a few minutes, my computer freezes up if the adapter is hooked up
3) regardless of whether I use NM or /etc/network/interfaces, the adapter can't find any routers/access points
4) if I ask NM to scan, my computer freezes up too

Anybody know what is causing this or what I can do to prevent this from happening?Yes, but as you probably guessed, some output will confirm my suspisions.

This happened to me once, where my adapter was continually recognized and reinserted over and over and over. This can cause the kernel to crash, thus the appearance to freeze.

> **CanardoKeyser said:**
> Let me know what information you want me to post.I would like to have /var/log/syslog after about 2 minutes of having it plugged in. Please note that if my above suspicions are true, this might be tough, because the kernel's crash brings down a lot of stuff with it.

> **CanardoKeyser said:**
> the only thing I can say for sure (without being at the computer in question) is that in dmesg, there are entries for the wlan0 being hooked up, you know, the regular messages, and then later on: ndiswrapper: device wlan0 was removed (and after that, the same entries for plugging in/"finding"  the wireless adapter again (followed by ndiswrapper: device wlan0 was removed again), etc...)This further builds my above suspicion.

> **CanardoKeyser said:**
> what I have done:
the usual steps, right up to "99-custom"
tried several versions of the drivers
tried it with /etc/network/interfaces as is (I did comment out the others, but just left the 2 lines for wlan0)
tried it with adding lines for the ssid, etc.... in /etc/network/interfaces
tried it with commenting everything out and doing ifconfig wlan0 up, etc...
everything leads to a freeze (and no network finding)This neither adds nor removes from my suspicion, since they really don't affect your problem.

> **CanardoKeyser said:**
> PS: As for me, I am new to Ubuntu, not that new to Linux, I usually have a dual windows/linux boot on my computer, and do have some, albeit rusty, knowledge of linux :-) and even though I am at work, I could dash over to home to retrieve the information you want me to postYea, like I said, /var/log/syslog. The fact that your device is added is an excellent sign - it means the HOWTO worked, but for some reason you have this extra issue at the very end.

---

### Post by javaJake on 2007-04-27
> **Guitar John said:**
> Here's what I got.  The drivers I used are part of the attachment from the original post.

OK, so that error didn't really affect ndiswrapper. I really don't know what to say for a solution. I haven't seen any errors, and according to the information you've given me, nothing should be wrong. That's the first step in figuring these things out - getting an error that points to a problem.

Can you show me what you did exactly when you installed the drivers?

---

### Post by javaJake on 2007-04-27
> **Guitar John said:**
> It looks like the same .sys files are there although rndismp.sys from the attachment that was originally posted is called RNDISMPK.SYS in the download from the Belkin website.   I await further instructions.

Thank you.
GJ

OK, can you rename RNDISMPK.SYS to all lowercase? This may be the issue, but I'm not sure.

---

### Post by leetcharmer on 2007-05-11
Hey.  I got another computer to test out my WUSB54GSC.  I got Xubuntu 7.04 installed, ndiswrapper 1.43, and the driver is rt73.inf.

ndiswrapper -l says device installed.

no wlan0 detected though.

Can you check my logs?  I installed the usb .sys files into /etc/ndiswrapper/rt73/

Let me know if you need to see anything else.

---

### Post by scottpledger on 2007-05-11
> **leetcharmer said:**
> Hey.  I got another computer to test out my WUSB54GSC.  I got Xubuntu 7.04 installed, ndiswrapper 1.43, and the driver is rt73.inf.

ndiswrapper -l says device installed.

no wlan0 detected though.

Can you check my logs?  I installed the usb .sys files into /etc/ndiswrapper/rt73/

Let me know if you need to see anything else.


Could you post anything that says 'ndiswrapper' in it when you run 'dmesg'?? (your syslogs didn't contain hardly anything on ndiswrapper)

---

### Post by javaJake on 2007-05-11
> **leetcharmer said:**
> Hey.  I got another computer to test out my WUSB54GSC.  I got Xubuntu 7.04 installed, ndiswrapper 1.43, and the driver is rt73.inf.

ndiswrapper -l says device installed.

no wlan0 detected though.

Can you check my logs?  I installed the usb .sys files into /etc/ndiswrapper/rt73/

Let me know if you need to see anything else.

scottpledger is right. Your logs do not show you plugging in your WUSB54GSC device. The best thing to do is to make a copy of syslog after 5 seconds of plugging your device in.

---

### Post by butt200w on 2007-05-21
I moved on to this nifty little piece after I gave up on my D-link USB key (the rt73 device kept identifying itself as rt2500...)

Anyways, after following the tutorial (except for upgrading ndiswrapper, ndiswrapper -v returns version 1.9) and putting in the custom rules (as the power light was only coming on briefly), I am close to success. Unfortunately I get the following "problem" after hooking up the device:

```
usb 4-2: new high speed USB device using ehci_hcd and address 4
usb 4-2: no configuration chosen from 1 choice
ndiswrapper version 1.32 loaded (preempt=no,smp=yes)
usb 4-2: reset high speed USB device using ehci_hcd and address 4
ndiswrapper: driver wusb54gsv2 (Linksys,01/25/2005, 4.01.20.0) loaded
wlan0: ethernet device 00:18:39:03:99:5a using NDIS driver: wusb54gsv2, version: 0x4011405, NDIS version: 0x501, vendor: 'Linksys Wireless-G USB Network Adapter with SpeedBooster', 13B1:0014.F.conf
wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
usbcore: registered new driver ndiswrapper
ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
BUG: unable to handle kernel NULL pointer dereference at virtual address 00000000
 printing eip:
c6f1e488
*pde = 00000000
Oops: 0002 [#1]
SMP
Modules linked in: ndiswrapper radeon drm fuse via_rhine mii snd_seq_dummy snd_seq_oss snd_seq_midi_event snd_seq af_packet snd_pcm_oss snd_mixer_oss video snd_via82xx thermal gameport sbs snd_ac97_codec snd_ac97_bus i2c_ec snd_pcm snd_timer snd_page_alloc snd_mpu401_uart snd_rawmidi snd_seq_device fan snd soundcore container button battery ac ide_cd binfmt_misc loop nls_iso8859_1 nls_cp850 vfat fat dm_mod yenta_socket rsrc_nonstatic pcmcia pcmcia_core cpufreq_ondemand cpufreq_conservative cpufreq_powersave freq_table processor via_agp agpgart usbmouse evdev ohci1394 ieee1394 usbhid bttv video_buf firmware_class ir_common compat_ioctl32 i2c_algo_bit btcx_risc tveeprom i2c_core usbkbd videodev v4l1_compat v4l2_common floppy usb_storage ehci_hcd uhci_hcd usbcore sata_vsc sata_via sata_svw sata_sil sata_promise sata_nv sx8 sata_uli sata_sx4 sata_sis sata_qstor ahci BusLogic aic7xxx scsi_transport_spi sg sr_mod cdrom ata_piix sd_mod libata scsi_mod ext3 jbd
CPU:    0
EIP:    0060:[<c6f1e488>]    Tainted: P      VLI
EFLAGS: 00010246   (2.6.18.6.dev3.lgc #1)
EIP is at 0xc6f1e488
eax: 00000000   ebx: c71992c0   ecx: cebf6500   edx: c71996c0
esi: ce497800   edi: c89b97a0   ebp: c7db9df8   esp: c7db9de8
ds: 007b   es: 007b   ss: 0068
Process sh (pid: 3343, ti=c7db8000 task=cfd81250 task.ti=c7db8000)
Stack: d0837e28 c6f1e200 00000001 c89b95a0 d0837e0a d0d5828b ce497800 00000002
       00000000 00000000 00000002 00000000 00000297 d0d4e5c7 c89b9b80 00000000
       d0d5303d c89b9b80 00000000 c7db9e6c c89b97a0 d0d53147 c89b97a0 0000001b
Call Trace:
 [<d0d5828b>] NdisDispatchPnp+0x18b/0x7d0 [ndiswrapper]
 [<d0d4e5c7>] get_current_nt_thread+0xa7/0xd0 [ndiswrapper]
 [<d0d5303d>] IoQueueThreadIrp+0xd/0xe0 [ndiswrapper]
 [<d0d53147>] IoBuildSynchronousFsdRequest+0x37/0x40 [ndiswrapper]
 [<d0d5236d>] IofCallDriver+0x2d/0x50 [ndiswrapper]
 [<d0d54853>] IoSendIrpTopDev+0x73/0xb0 [ndiswrapper]
 [<d0d548c6>] pnp_remove_device+0x36/0x130 [ndiswrapper]
 [<d0e76ef4>] usb_unbind_interface+0x34/0x70 [usbcore]
 [<b0249460>] __device_release_driver+0x50/0x80
 [<b0249697>] device_release_driver+0x17/0x30
 [<b0248da9>] bus_remove_device+0x89/0xa0
 [<b0247bc1>] device_del+0xf1/0x130
 [<d0e753f8>] usb_disable_device+0x88/0xf0 [usbcore]
 [<d0e75d60>] usb_set_configuration+0xb0/0x470 [usbcore]
 [<d0e78c33>] set_bConfigurationValue+0x43/0x58 [usbcore]
 [<d0e78bf0>] set_bConfigurationValue+0x0/0x58 [usbcore]
 [<b024771a>] dev_attr_store+0x1a/0x20
 [<b01a7b8c>] sysfs_write_file+0x7c/0xd0
 [<b016b2b0>] vfs_write+0xa0/0x170
 [<b01a7b10>] sysfs_write_file+0x0/0xd0
 [<b016b96c>] sys_write+0x3c/0x70
 [<b0102fbd>] sysenter_past_esp+0x56/0x79
Code: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 <30> 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
EIP: [<c6f1e488>] 0xc6f1e488 SS:ESP 0068:c7db9de8

```

Now first of all, should ndiswrapper be trying to rename the device after it's been registered? Is this a problem with ndiswrapper, or with my system configuration. I'm running PCLinuxOS (yes I realize this is a ubuntu forum but damned if this isn't a good HowTo) and I put the code for Edgy in 99-fuse.rules (as I didn't have a 99-custom.rules file). The computer "almost" freezes, that is to say it works fine till you try and load anything do with the network drivers or modules (iwconfig, lsmod, etc.) at which point the command line stops accepting any input (or maybe just stops producing output) except for reboot, which causes the computer to freeze during the shutdown sequence.

I'm so close, I just want this to work. I'm using the drivers I got from your attachment.

---

### Post by javaJake on 2007-05-22
> **butt200w said:**
> Unfortunately I get the following "problem" after hooking up the device

You are getting this error because you are using an old version of ndiswrapper. Any version above 1.8 that is one-digit should be suspected as old.

I recommend you go to [http://sourceforge.net/projects/ndiswrapper]("http://sourceforge.net/projects/ndiswrapper") and download the latest *stable* version there. The attachment's version is now pretty old, and yours sounds like it has the bug.

---

### Post by Dreamsorcerer on 2007-06-07
Installed it as instructed, the power light turns on, but the link light doesn't turn on, will it flash even if it doesn't detect any signals?

I got this mesage:
wusb54gs : invalid driver!
wusb54gsv2 : driver installed

Is that right?

---

### Post by javaJake on 2007-06-07
> **Dreamsorcerer said:**
> Installed it as instructed, the power light turns on, but the link light doesn't turn on, will it flash even if it doesn't detect any signals?

I got this mesage:
wusb54gs : invalid driver!
wusb54gsv2 : driver installed

Is that right?

You've got multiple issues here. First of all, you have two drivers installed. You only need one unless you own both versions of the WUSB54GS. Second, the WUSB54GS driver is reporting itself as invalid. The reason for this particular issue could be because you ran through the HOWTO twice, trying either version (not recommended), or you accidentally mixed the instructions for the two versions.

In order for me to help you further, I'll need to know which version of the WUSB54GS device you really have. If there is no version (v2, v2.X, etc.) on the bottom of the device, you know it is a v1.

I could also use the output from the following command (optional):

```
ls -R /etc/ndiswrapper/
```

I could also use the log file called syslog (optional). In order to get the stuff I need from that file, plug in your device, wait for about 5 seconds (so that the USB device is recognized and registered and whatnot) and then copy the /var/log/syslog file here, or attach it.

---

### Post by Dreamsorcerer on 2007-06-07
> **javaJake said:**
> You've got multiple issues here. First of all, you have two drivers installed. You only need one unless you own both versions of the WUSB54GS. Second, the WUSB54GS driver is reporting itself as invalid. The reason for this particular issue could be because you ran through the HOWTO twice, trying either version (not recommended), or you accidentally mixed the instructions for the two versions.

In order for me to help you further, I'll need to know which version of the WUSB54GS device you really have. If there is no version (v2, v2.X, etc.) on the bottom of the device, you know it is a v1.

I could also use the output from the following command (optional):

```
ls -R /etc/ndiswrapper/
```

I could also use the log file called syslog (optional). In order to get the stuff I need from that file, plug in your device, wait for about 5 seconds (so that the USB device is recognized and registered and whatnot) and then copy the /var/log/syslog file here, or attach it.

Right, it's v.2.1

Command result:
> /etc/ndiswrapper/:
wusb54gs  wusb54gsv2

/etc/ndiswrapper/wusb54gs:

/etc/ndiswrapper/wusb54gsv2:
13B1:0014.F.conf  rndismp.sys  usb8023.sys  wusb54gsv2.inf

Won't let me attach a file, I'll edit and give a download link, in a minute.

Another problem is that all the programs on the computer froze when I finished installing it, after restarting, it happened again, when I had left it for half an hour!

---

### Post by Dreamsorcerer on 2007-06-07
Nope firefox won't let me load any page other than this forum, if it starts working again, I'll get the syslog hosted

---

### Post by Dreamsorcerer on 2007-06-07
OK, tried to restart computer, go stuck at 'stopping web server (apache2)', I've managed to upload the syslog to an old hosting account, you can access it here, [http://gamesvoid.co.uk/syslog]("http://gamesvoid.co.uk/syslog"), around 30 seconds after I plugged device in.

p.s. What command can I use in the terminal to delete a folder, that requires root to delete?

Edit: Froze again, got stuck at the same place when trying to reboot!

---

### Post by javaJake on 2007-06-07
> **Dreamsorcerer said:**
> OK, tried to restart computer, go stuck at 'stopping web server (apache2)', I've managed to upload the syslog to an old hosting account, you can access it here, [http://gamesvoid.co.uk/syslog]("http://gamesvoid.co.uk/syslog"), around 30 seconds after I plugged device in.

p.s. What command can I use in the terminal to delete a folder, that requires root to delete?

Edit: Froze again, got stuck at the same place when trying to reboot!

Apparently, your drivers are working. That's right. They're working. Yay! :)

But you noticed something else - you freeze up. Well, if you take a look at the output you sent me, you'll notice something fishy:
```
Jun  7 19:45:39 home kernel: [  717.719655] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000000
Jun  7 19:45:39 home kernel: [  717.719664]  printing eip:
Jun  7 19:45:39 home kernel: [  717.719666] c8f9d888
Jun  7 19:45:39 home kernel: [  717.719667] *pde = 00000000
Jun  7 19:45:39 home kernel: [  717.719672] Oops: 0002 [#1]
Jun  7 19:45:39 home kernel: [  717.719674] SMP 
Jun  7 19:45:39 home kernel: [  717.719677] Modules linked in: cdc_ether usbnet mii binfmt_misc rfcomm l2cap bluetooth xt_limit xt_tcpudp iptable_mangle ipt_LOG ipt_MASQUERADE nf_nat ipt_TOS ipt_REJECT nf_conntrack_irc nf_conntrack_ftp nf_conntrack_ipv4 xt_state nf_conntrack nfnetlink iptable_filter ip_tables x_tables ppdev i915 drm speedstep_lib cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative tc1100_wmi pcc_acpi dev_acpi sony_acpi video sbs i2c_ec dock button battery container ac asus_acpi backlight ndiswrapper ipv6 fuse lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event sg snd_seq snd_timer snd_seq_device sd_mod parport_pc parport snd soundcore snd_page_alloc pcspkr psmouse usblp serio_raw intel_agp agpgart iTCO_wdt iTCO_vendor_support shpchp pci_hotplug i2c_i810 i2c_algo_bit i2c_core af_packet tsdev evdev ext3 jbd mbcache ide_cd cdrom ide_disk ata_generic libata us
Jun  7 19:45:39 home kernel: _storage scsi_mod libusual piix floppy tulip generic ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
Jun  7 19:45:39 home kernel: [  717.719758] CPU:    0
Jun  7 19:45:39 home udevd-event[7147]: run_program: '/bin/sh' abnormal exit
Jun  7 19:45:40 home NetworkManager: <debug info>^I[1181241940.234114] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13b1_14_8057'). 
Jun  7 19:45:40 home kernel: [  717.719759] EIP:    0060:[<c8f9d888>]    Tainted: P      VLI
Jun  7 19:45:40 home kernel: [  717.719760] EFLAGS: 00010246   (2.6.20-16-generic #2)
Jun  7 19:45:40 home kernel: [  717.719768] EIP is at 0xc8f9d888
Jun  7 19:45:40 home kernel: [  717.719771] eax: 00000000   ebx: c88e5400   ecx: cacf10c0   edx: 00000002
Jun  7 19:45:40 home kernel: [  717.719774] esi: c579ec00   edi: cacf13cc   ebp: d09c3cd4   esp: d09c3cc4
Jun  7 19:45:40 home kernel: [  717.719776] ds: 007b   es: 007b   ss: 0068
Jun  7 19:45:40 home kernel: [  717.719779] Process sh (pid: 7158, ti=d09c2000 task=d6cf2030 task.ti=d09c2000)
Jun  7 19:45:40 home kernel: [  717.719781] Stack: e05e1e28 c43b3800 00000001 e05e1e0a c88e5400 e04ad26a c579ec00 00000002 
Jun  7 19:45:40 home kernel: [  717.719788]        00000000 00000000 00000000 cacf11e0 cacf14e0 d09c3e38 e04ae216 cacf11e0 
Jun  7 19:45:40 home kernel: [  717.719795]        cacf15c0 c14601c0 ded402b8 df2e6b64 df4f4d44 c0188415 c1de604c df4f4d44 
Jun  7 19:45:41 home kernel: [  717.719802] Call Trace:
Jun  7 19:45:41 home NetworkManager: <debug info>^I[1181241940.632923] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13b1_14_8057_usbraw'). 
Jun  7 19:45:41 home NetworkManager: <debug info>^I[1181241940.691120] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13b1_14_8057_if1'). 
Jun  7 19:45:41 home kernel: [  717.719822]  [<e04ad26a>] miniport_pnp_event+0xba/0x110 [ndiswrapper]
Jun  7 19:45:41 home kernel: [  717.719874]  [<e04ae216>] NdisDispatchPnp+0x126/0xd80 [ndiswrapper]
Jun  7 19:45:41 home kernel: [  717.719912]  [dput+181/320] dput+0xb5/0x140
Jun  7 19:45:41 home kernel: [  717.719927]  [__link_path_walk+2527/3696] __link_path_walk+0x9df/0xe70
Jun  7 19:45:41 home kernel: [  717.719993]  [__activate_task+33/64] __activate_task+0x21/0x40
Jun  7 19:45:41 home kernel: [  717.720019]  [__switch_to+198/496] __switch_to+0xc6/0x1f0
Jun  7 19:45:41 home kernel: [  717.720029]  [native_write_cr0+0/16] native_write_cr0+0x0/0x10
Jun  7 19:45:41 home kernel: [  717.720052]  [<e04a7488>] IoAllocateIrp+0x68/0xa0 [ndiswrapper]
Jun  7 19:45:41 home kernel: [  717.720092]  [<e04a7f95>] IoBuildAsynchronousFsdRequest+0x35/0x170 [ndiswrapper]
Jun  7 19:45:41 home kernel: [  717.720117]  [<e04a25c1>] get_current_nt_thread+0xc1/0xf0 [ndiswrapper]
Jun  7 19:45:41 home kernel: [  717.720145]  [<e04a80eb>] IoQueueThreadIrp+0x1b/0x130 [ndiswrapper]
Jun  7 19:45:41 home kernel: [  717.720179]  [<e04a712a>] IofCallDriver+0x3a/0xa0 [ndiswrapper]
Jun  7 19:45:41 home kernel: [  717.720222]  [<e04ac8ab>] IoSendIrpTopDev+0xbb/0x120 [ndiswrapper]
Jun  7 19:45:41 home kernel: [  717.720289]  [<e04ac983>] pnp_remove_device+0x73/0x1d0 [ndiswrapper]
Jun  7 19:45:41 home kernel: [  717.720338]  [<e007fd20>] usb_unbind_interface+0x50/0xa0 [usbcore]
Jun  7 19:45:41 home kernel: [  717.720375]  [__device_release_driver+104/160] __device_release_driver+0x68/0xa0
Jun  7 19:45:41 home kernel: [  717.720388]  [device_release_driver+35/64] device_release_driver+0x23/0x40
Jun  7 19:45:41 home kernel: [  717.720396]  [bus_remove_device+92/144] bus_remove_device+0x5c/0x90
Jun  7 19:45:41 home kernel: [  717.720407]  [device_del+338/432] device_del+0x152/0x1b0
Jun  7 19:45:41 home kernel: [  717.720427]  [<e007d1ee>] usb_disable_device+0x7e/0xe0 [usbcore]
Jun  7 19:45:41 home kernel: [  717.720458]  [<e007dc3c>] usb_set_configuration+0x9c/0x4d0 [usbcore]
Jun  7 19:45:41 home kernel: [  717.720475]  [__wake_up_locked+31/48] __wake_up_locked+0x1f/0x30
Jun  7 19:45:41 home kernel: [  717.720491]  [__down+229/244] __down+0xe5/0xf4
Jun  7 19:45:41 home kernel: [  717.720503]  [default_wake_function+0/16] default_wake_function+0x0/0x10
Jun  7 19:45:41 home kernel: [  717.720539]  [<e0081e4e>] set_bConfigurationValue+0x6e/0x90 [usbcore]
Jun  7 19:45:41 home kernel: [  717.720574]  [<e0081de0>] set_bConfigurationValue+0x0/0x90 [usbcore]
Jun  7 19:45:41 home kernel: [  717.720595]  [dev_attr_store+45/64] dev_attr_store+0x2d/0x40
Jun  7 19:45:41 home kernel: [  717.720612]  [sysfs_write_file+159/256] sysfs_write_file+0x9f/0x100
Jun  7 19:45:41 home kernel: [  717.720644]  [vfs_write+190/400] vfs_write+0xbe/0x190
Jun  7 19:45:41 home kernel: [  717.720654]  [sysfs_write_file+0/256] sysfs_write_file+0x0/0x100
Jun  7 19:45:41 home kernel: [  717.720671]  [sys_write+65/112] sys_write+0x41/0x70
Jun  7 19:45:41 home kernel: [  717.720694]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9
Jun  7 19:45:41 home kernel: [  717.720726]  [xfrm_state_find+1011/1392] xfrm_state_find+0x3f3/0x570
Jun  7 19:45:41 home kernel: [  717.720756]  =======================
Jun  7 19:45:41 home kernel: [  717.720758] Code: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 <30> 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
Jun  7 19:45:41 home kernel: [  717.720787] EIP: [<c8f9d888>] 0xc8f9d888 SS:ESP 0068:d09c3cc4
```

This is what people call a kernel crash. That's why your computer freezes when shutting down a network program - the software that should've shut down tries to access something that crashed earlier, and just freezes up.

The fix is easy. Don't use the ndiswrapper in the repositories. Instead, use the one at the ndiswrapper website (which will compile, I can 99.9% guarantee you, if you follow all the instructions). You can download the latest version here: [http://sourceforge.net/projects/ndiswrapper]("http://sourceforge.net/projects/ndiswrapper")

Be sure to run "sudo apt-get remove ndiswrapper" to remove the old version. As long as you don't write "--purge", your computer will save all your drivers.

You noticed that the wusb54gs driver is invalid because it does not have any files. As you guessed, the remedy is to remove the wusb54gs folder. To remove it as root, run...
```
sudo rm -R /etc/ndiswrapper/wusb54gs/
```


Once you have finished all of the above, you should have a working WUSB54GS v2 device! :D

---

### Post by Dreamsorcerer on 2007-06-08
Ermm, am I meant to get this message when removing it?

> s@home:~$ sudo apt-get remove ndiswrapper
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper

---

### Post by Dreamsorcerer on 2007-06-09
OK, I've installed ndiswrapper-1.46, but the link light is still not coming on! And, it's still freezing in the same way as it was before!

---

### Post by lunarmelody on 2007-06-09
How do I tell which version I have?  I can't find it in any of the documentation.  Am I just looking in the wrong place?

---

### Post by javaJake on 2007-06-10
> **lunarmelody said:**
> How do I tell which version I have?  I can't find it in any of the documentation.  Am I just looking in the wrong place?

You want to look at the bottom of the device. There'll be a label there with the version on it. If you cannot find anything anywhere on that label that says "v#", then you've got a v1.

Another way to tell is to plug it in, run lsusb in the terminal after waiting for a few seconds, and matching the numbers printed out with the ones in the HOWTO. (Post them here if you don't understand which numbers match what.)

---

### Post by TheSparkster on 2007-06-12
Hi, thanks for the great guide. I am now successfully up running.

However i was one of the mnay that has attempted and failed to get the WUSB54GSv2 to work on the x64 version of Ubuntu, I hope someone manages to get this working in the future. 

Thanks again.

Mark

---

### Post by kolyma on 2007-06-13
Great tutorial, javaJake, and thanks to everyone for your input. This has been immensely helpful.

Here's my dilemma. I'm running Feisty with a WUSB54GSC. I've followed all the steps, and seem to have installed the driver properly, but can't get a wlan0 or a green light. Here are my results:

```
meg@torpedo:~$ ndiswrapper -l
wusb54gsc : driver installed
        device (13B1:0020) present (alternate driver: rt73usb)

meg@torpedo:~$ lsusb
Bus 007 Device 002: ID 13b1:0020 Linksys 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 152d:2338  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 0510:0032 Sejin Electron, Inc. 
Bus 005 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse

meg@torpedo:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

meg@torpedo:~$ dmesg | grep -i usb
[    2.886657] usbcore: registered new interface driver usbfs
[    2.886675] usbcore: registered new interface driver hub
[    2.886691] usbcore: registered new device driver usb
[    2.906008] USB Universal Host Controller Interface driver v3.0
[    2.906164] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.906277] usb usb1: configuration #1 chosen from 1 choice
[    2.906294] hub 1-0:1.0: USB hub found
[    3.011105] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    3.011227] usb usb2: configuration #1 chosen from 1 choice
[    3.011243] hub 2-0:1.0: USB hub found
[    3.111445] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    3.111524] usb usb3: configuration #1 chosen from 1 choice
[    3.111541] hub 3-0:1.0: USB hub found
[    3.215934] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[    3.216040] usb usb4: configuration #1 chosen from 1 choice
[    3.216063] hub 4-0:1.0: USB hub found
[    3.320827] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[    3.320932] usb usb5: configuration #1 chosen from 1 choice
[    3.320956] hub 5-0:1.0: USB hub found
[    3.353015] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    3.434020] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[    3.437912] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.437963] usb usb6: configuration #1 chosen from 1 choice
[    3.437979] hub 6-0:1.0: USB hub found
[    3.542304] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    3.546211] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.546264] usb usb7: configuration #1 chosen from 1 choice
[    3.546283] hub 7-0:1.0: USB hub found
[    3.880270] usb 2-1: device not accepting address 2, error -71
[    4.564569] usb 6-3: new high speed USB device using ehci_hcd and address 2
[    4.698885] usb 6-3: configuration #1 chosen from 1 choice
[    4.950902] usb 7-3: new high speed USB device using ehci_hcd and address 2
[    5.285687] usb 7-3: configuration #1 chosen from 1 choice
[    5.653896] usbcore: registered new interface driver libusual
[    5.656908] Initializing USB Mass Storage driver...
[    5.893282] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    6.071648] usb 5-1: configuration #1 chosen from 1 choice
[    6.315838] usb 5-2: new low speed USB device using uhci_hcd and address 3
[    6.493985] usb 5-2: configuration #1 chosen from 1 choice
[    6.512996] scsi4 : SCSI emulation for USB Mass Storage devices
[    6.513039] usb-storage: device found at 2
[    6.513042] usb-storage: waiting for device to settle before scanning
[    6.513055] usbcore: registered new interface driver hiddev
[    6.513063] usbcore: registered new interface driver usb-storage
[    6.513066] USB Mass Storage support registered.
[    6.525928] input: Logitech USB Optical Mouse as /class/input/input1
[    6.525949] input: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.2-1
[    6.539931] input: SEJIN SEJIN USB joint Keyboard as /class/input/input2
[    6.539939] input: USB HID v1.10 Keyboard [SEJIN SEJIN USB joint Keyboard] on usb-0000:00:1d.2-2
[    6.539951] usbcore: registered new interface driver usbhid
[    6.539954] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   11.504552] usb-storage: device scan complete
[   21.243026] usb 7-3: reset high speed USB device using ehci_hcd and address 2
[   21.459999] ndiswrapper: driver wusb54gsc (Linksys,01/25/2005, 4.01.20.0) loaded
[   21.478635] usbcore: registered new interface driver ndiswrapper

meg@torpedo:~$  dmesg | grep -i ndiswrapper
[   21.073173] ndiswrapper version 1.46 loaded (smp=yes)
[   21.459999] ndiswrapper: driver wusb54gsc (Linksys,01/25/2005, 4.01.20.0) loaded
[   21.478598] ndiswrapper (mp_init:261): couldn't initialize device: 00010003
[   21.478602] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[   21.478611] ndiswrapper (mp_halt:303): device dfe8c400 is not initialized - not halting
[   21.478617] ndiswrapper: device eth%d removed
[   21.478627] ndiswrapper: probe of 7-3:1.0 failed with error -22
[   21.478635] usbcore: registered new interface driver ndiswrapper

meg@torpedo:~$ vi /etc/udev/rules.d/99-custom.rules
BUS=="usb", SYSFS{idVendor}=="13b1", SYSFS{idProduct}=="0020", RUN+="/bin/sh -c 'echo 1 > /sys/bus/usb/devices/%k/bConfigurationValue'"
BUS=="usb", SYSFS{idProduct}=="0026", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c 'echo 1 > /sys/bus/usb/devices/%k/bConfigurationValue'"
```

I've blacklisted the default driver, which is (I think) why I don't have a wlan0 anymore. The output above shows two combinations I've tried for my rules file. My question is, for your hardware and kernel, how do you know what the path should be?

Looks like ndiswrapper is having problems initializing the device with the windows driver. I compiled the most recent stable version of ndiswrapper. Anyone have any suggestions?

Thanks!

---

### Post by javaJake on 2007-06-13
> **kolyma said:**
> Great tutorial, javaJake, and thanks to everyone for your input. This has been immensely helpful.

Here's my dilemma. I'm running Feisty with a WUSB54GSC. I've followed all the steps, and seem to have installed the driver properly, but can't get a wlan0 or a green light. Here are my results:Hmmm... your output tells me it should've turned on. Would you mind posting /var/log/syslog as well? That's the only thing you missed in your otherwise beautiful post for help. :)

> **kolyma said:**
> I've blacklisted the default driver, which is (I think) why I don't have a wlan0 anymore. The output above shows two combinations I've tried for my rules file. My question is, for your hardware and kernel, how do you know what the path should be?You should be able to browse to the folder yourself and double check. The folders named with numbers are a little daunting, though.

> **kolyma said:**
> Looks like ndiswrapper is having problems initializing the device with the windows driver.It does look like that! This is very strange. Is your device visible in the System -> Preferences -> Hardware Information (or Device Manager for Edgy)?


I'm hoping that syslog will clear up the mystery.

---

### Post by kolyma on 2007-06-13
> mmm... your output tells me it should've turned on. Would you mind posting /var/log/syslog as well?

Here it is. Looks sort of wonky.

```
meg@torpedo:/var/log$ grep -i usb syslog
Jun 13 17:38:08 torpedo kernel: [  369.598591] usb 7-4: USB disconnect, address 5
Jun 13 17:38:08 torpedo NetworkManager: <debug info>^I[1181770688.480832] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_d7d_1300_073A196304C2_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Jun 13 17:38:08 torpedo NetworkManager: <debug info>^I[1181770688.484308] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial__USB_DISK_2_0_073A196304C2_0_0'). 
Jun 13 17:38:08 torpedo NetworkManager: <debug info>^I[1181770688.485603] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_d7d_1300_073A196304C2_if0_scsi_host_scsi_device_lun0'). 
Jun 13 17:38:08 torpedo NetworkManager: <debug info>^I[1181770688.486904] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_d7d_1300_073A196304C2_if0_scsi_host'). 
Jun 13 17:38:08 torpedo NetworkManager: <debug info>^I[1181770688.487741] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_d7d_1300_073A196304C2_if0'). 
Jun 13 17:38:08 torpedo NetworkManager: <debug info>^I[1181770688.488464] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_d7d_1300_073A196304C2'). 
Jun 13 17:38:08 torpedo NetworkManager: <debug info>^I[1181770688.490834] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_d7d_1300_073A196304C2_usbraw'). 
Jun 13 21:52:06 torpedo kernel: [    2.524386] usbcore: registered new interface driver usbfs
Jun 13 21:52:06 torpedo kernel: [    2.524405] usbcore: registered new interface driver hub
Jun 13 21:52:06 torpedo kernel: [    2.524420] usbcore: registered new device driver usb
Jun 13 21:52:06 torpedo kernel: [    2.525110] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Jun 13 21:52:06 torpedo kernel: [    2.529021] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jun 13 21:52:06 torpedo kernel: [    2.529076] usb usb1: configuration #1 chosen from 1 choice
Jun 13 21:52:06 torpedo kernel: [    2.529094] hub 1-0:1.0: USB hub found
Jun 13 21:52:06 torpedo kernel: [    2.535932] USB Universal Host Controller Interface driver v3.0
Jun 13 21:52:06 torpedo kernel: [    2.635823] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Jun 13 21:52:06 torpedo kernel: [    2.639726] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jun 13 21:52:06 torpedo kernel: [    2.639775] usb usb2: configuration #1 chosen from 1 choice
Jun 13 21:52:06 torpedo kernel: [    2.639792] hub 2-0:1.0: USB hub found
Jun 13 21:52:06 torpedo kernel: [    2.747904] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Jun 13 21:52:06 torpedo kernel: [    2.748000] usb usb3: configuration #1 chosen from 1 choice
Jun 13 21:52:06 torpedo kernel: [    2.748016] hub 3-0:1.0: USB hub found
Jun 13 21:52:06 torpedo kernel: [    2.852137] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Jun 13 21:52:06 torpedo kernel: [    2.852245] usb usb4: configuration #1 chosen from 1 choice
Jun 13 21:52:06 torpedo kernel: [    2.852268] hub 4-0:1.0: USB hub found
Jun 13 21:52:06 torpedo kernel: [    2.872158] usb 1-3: new high speed USB device using ehci_hcd and address 2
Jun 13 21:52:06 torpedo kernel: [    2.956970] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Jun 13 21:52:06 torpedo kernel: [    2.957072] usb usb5: configuration #1 chosen from 1 choice
Jun 13 21:52:06 torpedo kernel: [    2.957094] hub 5-0:1.0: USB hub found
Jun 13 21:52:06 torpedo kernel: [    3.007107] usb 1-3: configuration #1 chosen from 1 choice
Jun 13 21:52:06 torpedo kernel: [    3.061825] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Jun 13 21:52:06 torpedo kernel: [    3.061930] usb usb6: configuration #1 chosen from 1 choice
Jun 13 21:52:06 torpedo kernel: [    3.061953] hub 6-0:1.0: USB hub found
Jun 13 21:52:06 torpedo kernel: [    3.166682] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Jun 13 21:52:06 torpedo kernel: [    3.166783] usb usb7: configuration #1 chosen from 1 choice
Jun 13 21:52:06 torpedo kernel: [    3.166808] hub 7-0:1.0: USB hub found
Jun 13 21:52:06 torpedo kernel: [    3.250883] usb 2-3: new high speed USB device using ehci_hcd and address 2
Jun 13 21:52:06 torpedo kernel: [    3.572857] usb 2-3: configuration #1 chosen from 1 choice
Jun 13 21:52:06 torpedo kernel: [    3.830051] usbcore: registered new interface driver libusual
Jun 13 21:52:06 torpedo kernel: [    3.832787] Initializing USB Mass Storage driver...
Jun 13 21:52:06 torpedo kernel: [    3.832819] scsi4 : SCSI emulation for USB Mass Storage devices
Jun 13 21:52:06 torpedo kernel: [    3.832848] usbcore: registered new interface driver usb-storage
Jun 13 21:52:06 torpedo kernel: [    3.832850] USB Mass Storage support registered.
Jun 13 21:52:06 torpedo kernel: [    3.832885] usb-storage: device found at 2
Jun 13 21:52:06 torpedo kernel: [    3.832886] usb-storage: waiting for device to settle before scanning
Jun 13 21:52:06 torpedo kernel: [    8.822821] usb-storage: device scan complete
Jun 13 21:52:06 torpedo kernel: [   14.065051] usb 2-3: reset high speed USB device using ehci_hcd and address 2
Jun 13 21:52:06 torpedo kernel: [   14.282298] ndiswrapper: driver wusb54gsc (Linksys,01/25/2005, 4.01.20.0) loaded
Jun 13 21:52:06 torpedo kernel: [   14.300955] usbcore: registered new interface driver ndiswrapper
Jun 13 21:56:33 torpedo kernel: [  288.134006] usb 7-1: new low speed USB device using uhci_hcd and address 2
Jun 13 21:56:34 torpedo kernel: [  288.317804] usb 7-1: configuration #1 chosen from 1 choice
Jun 13 21:56:34 torpedo NetworkManager: <debug info>^I[1181786194.070634] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial'). 
Jun 13 21:56:34 torpedo kernel: [  288.415106] usbcore: registered new interface driver hiddev
Jun 13 21:56:34 torpedo kernel: [  288.427633] input: Logitech USB Optical Mouse as /class/input/input4
Jun 13 21:56:34 torpedo kernel: [  288.427830] input: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.2-1
Jun 13 21:56:34 torpedo kernel: [  288.428004] usbcore: registered new interface driver usbhid
Jun 13 21:56:34 torpedo kernel: [  288.428123] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Jun 13 21:56:34 torpedo NetworkManager: <debug info>^I[1181786194.172806] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_if0'). 
Jun 13 21:56:34 torpedo NetworkManager: <debug info>^I[1181786194.197266] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_usbraw'). 
Jun 13 21:56:34 torpedo NetworkManager: <debug info>^I[1181786194.254587] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_if0_logicaldev_input'). 
Jun 13 21:56:35 torpedo kernel: [  290.151495] usb 7-2: new low speed USB device using uhci_hcd and address 3
Jun 13 21:56:36 torpedo kernel: [  290.331647] usb 7-2: configuration #1 chosen from 1 choice
Jun 13 21:56:36 torpedo NetworkManager: <debug info>^I[1181786196.073735] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_510_32_noserial'). 
Jun 13 21:56:36 torpedo kernel: [  290.355660] input: SEJIN SEJIN USB joint Keyboard as /class/input/input5
Jun 13 21:56:36 torpedo kernel: [  290.355691] input: USB HID v1.10 Keyboard [SEJIN SEJIN USB joint Keyboard] on usb-0000:00:1d.2-2
Jun 13 21:56:36 torpedo NetworkManager: <debug info>^I[1181786196.141709] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_510_32_noserial_if0'). 
Jun 13 21:56:36 torpedo NetworkManager: <debug info>^I[1181786196.142182] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_510_32_noserial_usbraw'). 
Jun 13 21:56:36 torpedo NetworkManager: <debug info>^I[1181786196.181035] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_510_32_noserial_if0_logicaldev_input'). 
Jun 13 21:58:13 torpedo kernel: [    2.513893] usbcore: registered new interface driver usbfs
Jun 13 21:58:13 torpedo kernel: [    2.513911] usbcore: registered new interface driver hub
Jun 13 21:58:13 torpedo kernel: [    2.530569] usbcore: registered new device driver usb
Jun 13 21:58:13 torpedo kernel: [    2.531152] USB Universal Host Controller Interface driver v3.0
Jun 13 21:58:13 torpedo kernel: [    2.531282] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Jun 13 21:58:13 torpedo kernel: [    2.531379] usb usb1: configuration #1 chosen from 1 choice
Jun 13 21:58:13 torpedo kernel: [    2.531396] hub 1-0:1.0: USB hub found
Jun 13 21:58:13 torpedo kernel: [    2.641018] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 2
Jun 13 21:58:13 torpedo kernel: [    2.644936] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jun 13 21:58:13 torpedo kernel: [    2.645026] usb usb2: configuration #1 chosen from 1 choice
Jun 13 21:58:13 torpedo kernel: [    2.645043] hub 2-0:1.0: USB hub found
Jun 13 21:58:13 torpedo kernel: [    2.748290] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 3
Jun 13 21:58:13 torpedo kernel: [    2.752201] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jun 13 21:58:13 torpedo kernel: [    2.752252] usb usb3: configuration #1 chosen from 1 choice
Jun 13 21:58:13 torpedo kernel: [    2.752268] hub 3-0:1.0: USB hub found
Jun 13 21:58:13 torpedo kernel: [    2.861705] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Jun 13 21:58:13 torpedo kernel: [    2.861786] usb usb4: configuration #1 chosen from 1 choice
Jun 13 21:58:13 torpedo kernel: [    2.861804] hub 4-0:1.0: USB hub found
Jun 13 21:58:13 torpedo kernel: [    2.964414] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Jun 13 21:58:13 torpedo kernel: [    2.964522] usb usb5: configuration #1 chosen from 1 choice
Jun 13 21:58:13 torpedo kernel: [    2.964545] hub 5-0:1.0: USB hub found
Jun 13 21:58:13 torpedo kernel: [    2.992537] usb 2-3: new high speed USB device using ehci_hcd and address 2
Jun 13 21:58:13 torpedo kernel: [    3.071770] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Jun 13 21:58:13 torpedo kernel: [    3.071876] usb usb6: configuration #1 chosen from 1 choice
Jun 13 21:58:13 torpedo kernel: [    3.071899] hub 6-0:1.0: USB hub found
Jun 13 21:58:13 torpedo kernel: [    3.130007] usb 2-3: configuration #1 chosen from 1 choice
Jun 13 21:58:13 torpedo kernel: [    3.179082] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Jun 13 21:58:13 torpedo kernel: [    3.179187] usb usb7: configuration #1 chosen from 1 choice
Jun 13 21:58:13 torpedo kernel: [    3.179211] hub 7-0:1.0: USB hub found
Jun 13 21:58:13 torpedo kernel: [    3.379986] usb 3-3: new high speed USB device using ehci_hcd and address 2
Jun 13 21:58:13 torpedo kernel: [    3.703925] usb 3-3: configuration #1 chosen from 1 choice
Jun 13 21:58:13 torpedo kernel: [    4.624472] usb 7-1: new low speed USB device using uhci_hcd and address 2
Jun 13 21:58:13 torpedo kernel: [    4.805644] usb 7-1: configuration #1 chosen from 1 choice
Jun 13 21:58:13 torpedo kernel: [    5.060480] usb 7-2: new low speed USB device using uhci_hcd and address 3
Jun 13 21:58:13 torpedo kernel: [    5.241954] usb 7-2: configuration #1 chosen from 1 choice
Jun 13 21:58:13 torpedo kernel: [    5.260930] usbcore: registered new interface driver libusual
Jun 13 21:58:13 torpedo kernel: [    5.414029] Initializing USB Mass Storage driver...
Jun 13 21:58:13 torpedo kernel: [    5.414070] scsi4 : SCSI emulation for USB Mass Storage devices
Jun 13 21:58:13 torpedo kernel: [    5.414099] usb-storage: device found at 2
Jun 13 21:58:13 torpedo kernel: [    5.414101] usb-storage: waiting for device to settle before scanning
Jun 13 21:58:13 torpedo kernel: [    5.414108] usbcore: registered new interface driver usb-storage
Jun 13 21:58:13 torpedo kernel: [    5.414110] USB Mass Storage support registered.
Jun 13 21:58:13 torpedo kernel: [   10.405308] usb-storage: device scan complete
Jun 13 21:58:13 torpedo kernel: [   12.133730] usbcore: registered new interface driver hiddev
Jun 13 21:58:13 torpedo kernel: [   12.252796] input: Logitech USB Optical Mouse as /class/input/input2
Jun 13 21:58:13 torpedo kernel: [   12.252837] input: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.2-1
Jun 13 21:58:13 torpedo kernel: [   12.321747] input: SEJIN SEJIN USB joint Keyboard as /class/input/input3
Jun 13 21:58:13 torpedo kernel: [   12.321781] input: USB HID v1.10 Keyboard [SEJIN SEJIN USB joint Keyboard] on usb-0000:00:1d.2-2
Jun 13 21:58:13 torpedo kernel: [   12.321794] usbcore: registered new interface driver usbhid
Jun 13 21:58:13 torpedo kernel: [   12.321798] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Jun 13 21:58:13 torpedo kernel: [   14.274605] usb 3-3: reset high speed USB device using ehci_hcd and address 2
Jun 13 21:58:13 torpedo kernel: [   14.491311] ndiswrapper: driver wusb54gsc (Linksys,01/25/2005, 4.01.20.0) loaded
Jun 13 21:58:13 torpedo kernel: [   14.509953] usbcore: registered new interface driver ndiswrapper
Jun 13 21:59:16 torpedo kernel: [   84.997391] usb 7-2: USB disconnect, address 3
Jun 13 21:59:16 torpedo NetworkManager: <debug info>^I[1181786356.442254] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_510_32_noserial_if0_logicaldev_input'). 
Jun 13 21:59:16 torpedo NetworkManager: <debug info>^I[1181786356.443033] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_510_32_noserial_if0'). 
Jun 13 21:59:16 torpedo NetworkManager: <debug info>^I[1181786356.446305] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_510_32_noserial'). 
Jun 13 21:59:16 torpedo NetworkManager: <debug info>^I[1181786356.447395] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_510_32_noserial_usbraw'). 
Jun 13 21:59:17 torpedo kernel: [   86.266579] usb 7-2: new low speed USB device using uhci_hcd and address 4
Jun 13 21:59:17 torpedo kernel: [   86.446370] usb 7-2: configuration #1 chosen from 1 choice
Jun 13 21:59:17 torpedo NetworkManager: <debug info>^I[1181786357.908279] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_510_32_noserial'). 
Jun 13 21:59:17 torpedo kernel: [   86.470389] input: SEJIN SEJIN USB joint Keyboard as /class/input/input6
Jun 13 21:59:17 torpedo kernel: [   86.470419] input: USB HID v1.10 Keyboard [SEJIN SEJIN USB joint Keyboard] on usb-0000:00:1d.2-2
Jun 13 21:59:17 torpedo NetworkManager: <debug info>^I[1181786357.955422] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_510_32_noserial_if0'). 
Jun 13 21:59:17 torpedo NetworkManager: <debug info>^I[1181786357.980035] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_510_32_noserial_usbraw'). 
Jun 13 21:59:18 torpedo NetworkManager: <debug info>^I[1181786358.022555] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_510_32_noserial_if0_logicaldev_input').

meg@torpedo:/var/log$ grep -i ndiswrapper syslog
Jun 13 21:52:06 torpedo kernel: [   13.895573] ndiswrapper version 1.46 loaded (smp=yes)
Jun 13 21:52:06 torpedo kernel: [   14.282298] ndiswrapper: driver wusb54gsc (Linksys,01/25/2005, 4.01.20.0) loaded
Jun 13 21:52:06 torpedo kernel: [   14.300920] ndiswrapper (mp_init:261): couldn't initialize device: 00010003
Jun 13 21:52:06 torpedo kernel: [   14.300924] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
Jun 13 21:52:06 torpedo kernel: [   14.300931] ndiswrapper (mp_halt:303): device f7907c00 is not initialized - not halting
Jun 13 21:52:06 torpedo kernel: [   14.300937] ndiswrapper: device eth%%d removed
Jun 13 21:52:06 torpedo kernel: [   14.300947] ndiswrapper: probe of 2-3:1.0 failed with error -22
Jun 13 21:52:06 torpedo kernel: [   14.300955] usbcore: registered new interface driver ndiswrapper
Jun 13 21:58:13 torpedo kernel: [   14.053307] ndiswrapper version 1.46 loaded (smp=yes)
Jun 13 21:58:13 torpedo kernel: [   14.491311] ndiswrapper: driver wusb54gsc (Linksys,01/25/2005, 4.01.20.0) loaded
Jun 13 21:58:13 torpedo kernel: [   14.509917] ndiswrapper (mp_init:261): couldn't initialize device: 00010003
Jun 13 21:58:13 torpedo kernel: [   14.509921] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
Jun 13 21:58:13 torpedo kernel: [   14.509928] ndiswrapper (mp_halt:303): device f7f8ec00 is not initialized - not halting
Jun 13 21:58:13 torpedo kernel: [   14.509934] ndiswrapper: device eth%%d removed
Jun 13 21:58:13 torpedo kernel: [   14.509944] ndiswrapper: probe of 3-3:1.0 failed with error -22
Jun 13 21:58:13 torpedo kernel: [   14.509953] usbcore: registered new interface driver ndiswrapper

```

> You should be able to browse to the folder yourself and double check. The folders named with numbers are a little daunting, though.

I did, and it looked OK... the bConfigurationValue file had a "1" in it. I hope it's the right folder (was usb7).

> Is your device visible in the System -> Preferences -> Hardware Information?

Yes, it is. Which seems weird. It says:

```
82801H USB2 EHCI #1 Compact Wireless-G USB Adapter
usb_device.configuration_value = 1
usb_device.linux.sysfs_path = /sys/devices/pci0000:00/0000:00:1d.7/usb7/7-3
usbraw.device = linux.device_file = /dev/bus/usb/007/002
```

Not sure if any of that is important, but I wrote most of it down anyway. Also, I should mention that when I'm running the LiveCD, the light blinks a couple times and quits, but still no connection (wlan0 is there but not working).

Thanks again for your help!

---

### Post by javaJake on 2007-06-14
```
Jun 13 21:58:13 torpedo kernel: [   14.509917] ndiswrapper (mp_init:261): couldn't initialize device: 00010003
Jun 13 21:58:13 torpedo kernel: [   14.509921] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
Jun 13 21:58:13 torpedo kernel: [   14.509928] ndiswrapper (mp_halt:303): device f7f8ec00 is not initialized - not halting
Jun 13 21:58:13 torpedo kernel: [   14.509934] ndiswrapper: device eth%%d removed
```

This is suspicious. If you happen to be on an x64 (64-bit) processor machine, check out this thread
[http://www.linuxquestions.org/questions/showthread.php?t=344849](http://www.linuxquestions.org/questions/showthread.php?t=344849)

Googling "Windows driver couldn't initialize the device (C0000001)" brought up quite a few results. Try that, or try the (**_brand new!!!_**) ndiswrapper website and forum here:
[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

---

### Post by cloudstrife_uk on 2007-06-16
Hi I got ndiswrapper working, installed the drivers, plugged the WUSB54GS in and Power light came on!

Link did not blink :(

But then this happened when the terminal was still open (and nothing would open up):

Message from syslogd@ra at Sat Jun 16 14:16:38 2007 ...ra kernel: [  360.340000] Oops: 0002 [#1]

Message from syslogd@ra at Sat Jun 16 14:16:38 2007 ...ra kernel: [  360.340000] SMP

Message from syslogd@ra at Sat Jun 16 14:16:38 2007 ...ra kernel: [  360.340000] CPU:    0

Message from syslogd@ra at Sat Jun 16 14:16:38 2007 ...ra kernel: [  360.340000] EIP:    0060:[<cbd23c88>]    Tainted: PVLI

Message from syslogd@ra at Sat Jun 16 14:16:38 2007 ...ra kernel: [  360.340000] EFLAGS: 00010246   (2.6.20-15-generic #2)

Message from syslogd@ra at Sat Jun 16 14:16:38 2007 ...ra kernel: [  360.340000] EIP is at 0xcbd23c88

Message from syslogd@ra at Sat Jun 16 14:16:38 2007 ...ra kernel: [  360.340000] eax: 00000000   ebx: d1d28400   ecx: 

c65baae0   edx: 00000002

Message from syslogd@ra at Sat Jun 16 14:16:38 2007 ...ra kernel: [  360.340000] esi: c9527800   edi: c65ba4ec   ebp: 

cd203cd8   esp: cd203cc8

Message from syslogd@ra at Sat Jun 16 14:16:38 2007 ...ra kernel: [  360.340000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@ra at Sat Jun 16 14:16:38 2007 ...ra kernel: [  360.340000] Process sh (pid: 6861, ti=cd202000 

task=c5f8c560 task.ti=cd202000)

Message from syslogd@ra at Sat Jun 16 14:16:38 2007 ...ra kernel: [  360.340000] Stack: d2d70e28 cbd23a00 00000001 d2d70e0a 

d1d28400 d2ebecb8 c9527800 00000002 

Message from syslogd@ra at Sat Jun 16 14:16:38 2007 ...ra kernel: [  360.340000]        00000000 00000000 00000000 c65ba700 

c65ba400 cd203e38 d2ebf956 c65ba700

Message from syslogd@ra at Sat Jun 16 14:16:38 2007 ...ra kernel: [  360.340000]        c65ba2e0 c1244b40 d04f4030 cd203d24 

c011e341 d1aadf9c 00000001 00000086

Message from syslogd@ra at Sat Jun 16 14:16:38 2007 ...ra kernel: [  360.340000] Call Trace:

Message from syslogd@ra at Sat Jun 16 14:16:38 2007 ...ra kernel: [  360.340000]  [<d2ebecb8>] miniport_pnp_event+0xb8/0x110 

[ndiswrapper]

Message from syslogd@ra at Sat Jun 16 14:16:38 2007 ...ra kernel: [  360.340000]  [<d2ebf956>] NdisDispatchPnp+0x126/0xdb0 

[ndiswrapper]

Message from syslogd@ra at Sat Jun 16 14:16:38 2007 ...ra kernel: [  360.340000]  [__activate_task+33/64] 

__activate_task+0x21/0x40

Message from syslogd@ra at Sat Jun 16 14:16:38 2007 ...ra kernel: [  360.340000]  [try_to_wake_up+70/1152] 

try_to_wake_up+0x46/0x480

Message from syslogd@ra at Sat Jun 16 14:16:38 2007 ...ra kernel: [  360.340000]  [mntput_no_expire+36/160] 

mntput_no_expire+0x24/0xa0

Message from syslogd@ra at Sat Jun 16 14:16:38 2007 ...ra kernel: [  360.340000]  [__switch_to+198/496] 

__switch_to+0xc6/0x1f0

Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000]  [<d2eb97b8>] IoAllocateIrp+0x68/0xa0 

[ndiswrapper]

Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000]  [<d2eb9f45>] 

IoBuildAsynchronousFsdRequest+0x35/0x170 [ndiswrapper]
Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000]  [<d2eb93f5>] IofCallDriver+0x55/0xc0 

[ndiswrapper]

Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000]  [<d2ebb98b>] IoSendIrpTopDev+0xbb/0x120 

[ndiswrapper]

Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000]  [<d2ebba63>] pnp_remove_device+0x73/0x1d0 

[ndiswrapper]

Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000]  [<d28c7d20>] usb_unbind_interface+0x50/0xa0 

[usbcore]

Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000]  [__device_release_driver+104/160] 

__device_release_driver+0x68/0xa0

Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000]  [device_release_driver+35/64] 

device_release_driver+0x23/0x40

Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000]  [bus_remove_device+92/144] 

bus_remove_device+0x5c/0x90

Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000]  [device_del+338/432] device_del+0x152/0x1b0

Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000] [<d28c51ee>] usb_disable_device+0x7e/0xe0 

[usbcore]

Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000]  [<d28c5c3c>] 

usb_set_configuration+0x9c/0x4d0 [usbcore]

Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000]  [__wake_up_locked+31/48] 

__wake_up_locked+0x1f/0x30

Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000]  [__down+229/244] __down+0xe5/0xf

Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000]  [default_wake_function+0/16]  default_wake_function+0x0/0x10

Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000]  [<d28c9e4e>] 

set_bConfigurationValue+0x6e/0x90 [usbcore]

Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000]  [<d28c9de0>] 

set_bConfigurationValue+0x0/0x90 [usbcore]
Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000]  [dev_attr_store+45/64]  dev_attr_store+0x2d/0x40

Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000]  [sysfs_write_file+159/256] 

sysfs_write_file+0x9f/0x100

Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000]  [vfs_write+190/400] vfs_write+0xbe/0x190

Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000] [sysfs_write_file+0/256]  sysfs_write_file+0x0/0x100

Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000]  [sys_write+65/112] sys_write+0x41/0x70

Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000]  [sysenter_past_esp+105/169]  sysenter_past_esp+0x69/0xa9

Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000]  =======================

Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000] Code: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 <30> 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

Message from syslogd@ra at Sat Jun 16 14:16:39 2007 ...ra kernel: [  360.340000] EIP: [<cbd23c88>] 0xcbd23c88 SS:ESP 0068:cd203cc8

---

### Post by javaJake on 2007-06-17
> **cloudstrife_uk said:**
> Hi I got ndiswrapper working, installed the drivers, plugged the WUSB54GS in and Power light came on!

Link did not blink :(

But then this happened when the terminal was still open (and nothing would open up)

This is a kernel crash. Check to be sure you have ndiswrapper version less then 1.8 and greater then 1.2 by running the following command in the terminal:

```
ndiswrapper -v
```

If you have the wrong version, make sure you've removed ndiswrapper through apt-get, and reinstall using the compiled version.

---

### Post by kolyma on 2007-06-17
Hey, I finally got my WUSB54GSC working with Feisty! I'm not on a 64 bit machine, so I was running out of ideas.

[LIST]
[*]I dowloaded the latest ndiswrapper (1.47).
[*]I installed it and tried using the wusb54gsc.inf driver specified on the ndiswrapper wiki. "ndiswrapper -l" showed driver installed but no hardware.
[*]Because nothing else was working, I uninstalled everything and started over, but this time used the windows driver that came on the CD with the device. There were three files: rt73.inf, rt73.sys, and rt73.cat.
[*]I did "sudo ndiswrapper -i rt73.inf" and ndiswrapper installed the driver and moved the .inf and .sys files to /etc/ndiswrapper/rt73.
[*]"ndiswrapper -l" reported 
```
rt73 : driver installed
        device (13B1:0020) present (alternate driver: rt73usb)
```
[*]I restarted and the device light started blinking. After some config work with System > Admin > Network to get the WEP keys right, it works.
[/LIST]

So, I've heard using windows drivers right off the CD might not be a good idea... but it works so far... should I be concerned?

---

### Post by javaJake on 2007-06-18
> **kolyma said:**
> Hey, I finally got my WUSB54GSC working with Feisty! I'm not on a 64 bit machine, so I was running out of ideas.Excellent! I'll post this in the Troubleshooting section! Thanks a lot! :D

> **kolyma said:**
> So, I've heard using windows drivers right off the CD might not be a good idea... but it works so far... should I be concerned?I wouldn't worry myself, unless people tell you you'll lose data on your computer, or your computer will melt. :p
I believe those warnings say the drivers on the CD may not work as well as they ought to. I'd ask whoever said this for more info before taking my word for it, since I've never heard of this before.

---

### Post by javaJake on 2007-06-18
**_[COLOR="Red"]Help Needed![/COLOR]_**
Life's been very busy for me, leaving me just enough time to come here and answer people's questions. If anyone is willing to edit the HOWTO to comply to the latest rules and regulations posted [here]("http://ubuntuforums.org/showthread.php?t=316820"), let me know using my e-mail or one of my IM IDs in my profile (I'm usually on during the weekends, Eastern Time).

---

### Post by cloudstrife_uk on 2007-06-19
Kernel crash?! Oh dear!

Well I typed ndiswrapper -v and this was the response:

utils Error: no version specified!
driver modinfo: could not open ndiswrapper: No such device

So I panicked a bit and checked Package Manager to see if I had installed ndiswrapper correctly.

This is what I found:

ndsiwrapper-common version: 1.38-lubuntu1
ndiswrapper-utils-1.9 version: 1.38-lubuntu1

I downloaded a package from Ubuntu website to install it (something I read from a different forum on the net!).

I think I might need to uninstall and use your version of ndiswrapper from your zip file!

Thanks javaJake for your help!

---

### Post by javaJake on 2007-06-19
> **cloudstrife_uk said:**
> I think I might need to uninstall and use your version of ndiswrapper from your zip file!

You definitely need to. However, if you can, you could also get the latest version. The packaged version is old, but it's proven to work on Dapper (and I want to maintain backwards compatibility as long as possible).

This is the latest version as of June 19th:
[http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.47.tar.gz?modtime=1181699252](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.47.tar.gz?modtime=1181699252)

---

### Post by Footballkid4 on 2007-07-10
One thing I discovered was that when restarting, my WUSB54GS would frequently not connect.  I found a workaround to this somewhere by executing:

```
iwconfig <yourdevice> essid x mode managed
```

So for me, it ended up as:
```
iwconfig wlan0 essid x mode managed
```

Someone somewhere else (I forgot now) posted that ndiswrapper has an issue with dissociating with networks, so the workaround is to assign the router to a non existent network (in this case, that network is x) and then attempt to reconnect to your own network.  It has solved the trick for me on every boot with no adverse problems that are noticeable.

---

### Post by leetcharmer on 2007-07-13
> **kolyma said:**
> Hey, I finally got my WUSB54GSC working with Feisty! I'm not on a 64 bit machine, so I was running out of ideas.

[LIST]
[*]I dowloaded the latest ndiswrapper (1.47).
[*]I installed it and tried using the wusb54gsc.inf driver specified on the ndiswrapper wiki. "ndiswrapper -l" showed driver installed but no hardware.
[*]Because nothing else was working, I uninstalled everything and started over, but this time used the windows driver that came on the CD with the device. There were three files: rt73.inf, rt73.sys, and rt73.cat.
[*]I did "sudo ndiswrapper -i rt73.inf" and ndiswrapper installed the driver and moved the .inf and .sys files to /etc/ndiswrapper/rt73.
[*]"ndiswrapper -l" reported 
```
rt73 : driver installed
        device (13B1:0020) present (alternate driver: rt73usb)
```
[*]I restarted and the device light started blinking. After some config work with System > Admin > Network to get the WEP keys right, it works.
[/LIST]

So, I've heard using windows drivers right off the CD might not be a good idea... but it works so far... should I be concerned?

can you post your driver files?  The only ones on my CD for windows has WUSB54GSC.inf and WUSB54GSC.cat, no rt73.*

---

### Post by kolyma on 2007-08-04
Hey, sorry it took so long!

I have to use "enable roaming mode" to connect. The settings are touchy, but it does work.

---

### Post by jamiepgs on 2007-08-06
Gah, I get the freeze when I plug it in!

Version 2.1 (according to linksys, 2.0 drivers work with 2.1)

What should I do?

---

### Post by Gothy on 2007-08-08
i have downloaded the flies i needed to get this to work!
(using the first post)
However there is one file i cannot seem to get to download.
its from
[http://www.linksys.com/servlet/Satel...VisitorWrapper](http://www.linksys.com/servlet/Satel...VisitorWrapper)

its the WUSB54GS drivers.
does anyone have them i can't seem to get them off the site, it looks like this;

Caucho Servlet Engine

Configuration Cluster
blah blah blah

Default Virtual Host
blah blah blah

web-app         url-pattern

please help!

---

### Post by javaJake on 2007-08-08
> **jamiepgs said:**
> Gah, I get the freeze when I plug it in!

Version 2.1 (according to linksys, 2.0 drivers work with 2.1)

What should I do?

Boot into your computer without the device plugged in. Run the following command:

```
sudo fdisk -l
```

This will give you information on your hard drive. You want a line that looks something like mine here:

```

[COLOR="Silver"]   Device Boot      Start         End      Blocks   Id  System[/COLOR]
**/dev/sda1   *           1        9444    75858898+  83  Linux**
```

The line you want will have the boot flag "*" set, and will have an System called "Linux". Save the /dev device listed in that line, in my case it is "/dev/sda1". You'll need this later.

Read the "What To Do If Your Computer Freezes Up" section for instructions on how to reboot your computer safely when it freezes (just hit the power button if that doesn't work), and reboot into the CD. When it's all done booting up into the CD, load a terminal, and write in the following commands:

```

sudo mkdir /media/harddrive
sudo mount -t ext3 -o defaults <DeviceFoundBefore> /media/harddrive

```

Replace the "<DeviceFoundBefore>" with the /dev device we found before. In my case, I would end up writing this:

```
sudo mount -t ext3 -o defaults /dev/sda1 /media/harddrive
```

Now, make a copy of /var/log/syslog like so:

```

sudo cp /media/harddrive/var/log/syslog /media/harddrive/syslog-copy

```

Reboot back into your computer (device unplugged). You'll find a copy of syslog in your root directory (called "/", just hit the "Up" button in the folder browser until you can't go any farther). Attach that file here, along with the file /etc/udev/rules.d/99-custom.rules. (You might need to put these files into an archive first before you can attach. You can do this by right-clicking the file, and click "Create Archive".)

---

### Post by escouser on 2007-08-08
Hi,

Having problems getting wusb54gs v2 to work on 7.04. The lights never 'show' after plugging it in. Any suggestions?

Thanks

Nik

ndiswrapper -v
```
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-15-generic SMP mod_unload 586 

```

ndiswrapper -l
```
wusb54gsv2 : driver installed
```

syslog
```
Aug  8 22:28:09 nathan-desktop loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver wusb54gsv2 
Aug  8 22:28:09 nathan-desktop kernel: [  298.203497] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisIMNotifyPnPEvent'
Aug  8 22:28:09 nathan-desktop kernel: [  298.203558] ndiswrapper (load_sys_files:216): couldn't prepare driver 'wusb54gsv2'
Aug  8 22:28:09 nathan-desktop kernel: [  298.221417] ndiswrapper (load_wrap_driver:118): couldn't load driver wusb54gsv2; check system log for messages from 'loadndisdriver'
```

dmesg
```
[  386.371905] usb 5-8: new high speed USB device using ehci_hcd and address 8
[  386.506581] usb 5-8: no configuration chosen from 1 choice
[  386.756052] usb 5-8: reset high speed USB device using ehci_hcd and address 8
[  386.902517] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisIMNotifyPnPEvent'
[  386.902577] ndiswrapper (load_sys_files:216): couldn't prepare driver 'wusb54gsv2'
[  386.903536] ndiswrapper (load_wrap_driver:118): couldn't load driver wusb54gsv2; check system log for messages from 'loadndisdriver'
[  386.903850] usb 5-8: bad CDC descriptors
```

---

### Post by javaJake on 2007-08-16
> **escouser said:**
> Hi,

Having problems getting wusb54gs v2 to work on 7.04. The lights never 'show' after plugging it in. Any suggestions?

Thanks

Nik

ndiswrapper -v
```
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-15-generic SMP mod_unload 586 

```

ndiswrapper -l
```
wusb54gsv2 : driver installed
```

syslog
```
Aug  8 22:28:09 nathan-desktop loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver wusb54gsv2 
Aug  8 22:28:09 nathan-desktop kernel: [  298.203497] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisIMNotifyPnPEvent'
Aug  8 22:28:09 nathan-desktop kernel: [  298.203558] ndiswrapper (load_sys_files:216): couldn't prepare driver 'wusb54gsv2'
Aug  8 22:28:09 nathan-desktop kernel: [  298.221417] ndiswrapper (load_wrap_driver:118): couldn't load driver wusb54gsv2; check system log for messages from 'loadndisdriver'
```

dmesg
```
[  386.371905] usb 5-8: new high speed USB device using ehci_hcd and address 8
[  386.506581] usb 5-8: no configuration chosen from 1 choice
[  386.756052] usb 5-8: reset high speed USB device using ehci_hcd and address 8
[  386.902517] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisIMNotifyPnPEvent'
[  386.902577] ndiswrapper (load_sys_files:216): couldn't prepare driver 'wusb54gsv2'
[  386.903536] ndiswrapper (load_wrap_driver:118): couldn't load driver wusb54gsv2; check system log for messages from 'loadndisdriver'
[  386.903850] usb 5-8: bad CDC descriptors
```

Can you try the drivers included within the attachment? The ones you are using seem to be incorrect somehow. [COLOR="Silver"]Google does not pull up any results, which points to a unique situation (i.e. something got accidentally deleted).[/COLOR] **Edit:** A more general Google search provides results that point to bad or incompatible drivers.

---

### Post by pgar23 on 2007-08-22
I'v got as far as this point, power light is on, but no blinking light (no success, maybe failure? lol)
I've attached a few necessary things (actually alot because I am dual booting with xp and ubuntu, obviously my ubuntu wireless doesnt work and it is hassle to switch back and forth on OS)
> 
 	Code:
 	sudo modprobe ndiswrapper 
[INDENT]If you get a "FATAL" error that says "/lib/<kernel>/misc/ndiswrapper.ko: invalid argument" then that means that you haven't gotten any drivers installed yet.[/INDENT]Plug in your device. The Power light will come on, and, after at most 3 seconds, the Link light will blink slowly. If the Link light does blink slowly, sucess!


---

### Post by pgar23 on 2007-08-22
GOT wlan0 TO WORK NOW!!!
ran this ```

depmod -a
modprobe ndiswrapper
```

then```

ifconfig wlan0 up
```

then opened SYSTEM--->ADMINISTRATIONS--->NETWORK
opened my wireless properties
unchecked "Enable Roaming"(it enables me to edit my properties)
edited settings to my configurations (ie. essid: xxxxx ip adress: 192.168.0.12...etc.)

I feel I am at least one step closer to connecting to the ALMIGHTY WIRELESS INTERNET...hahaha (it will be such an accomplishment once I am able to connect :))

---

### Post by pgar23 on 2007-08-22
Got Wireless Working. Had to uncheck the wired connection. THANK YOU to all who assisted in the long painful process.

---

### Post by slashx on 2007-09-07
hi javaJake

thanks for the step by step HOWTO
finally i manage to get this wusb54gsv2.1 to work

---

### Post by javaJake on 2007-09-08
> **slashx said:**
> hi javaJake

thanks for the step by step HOWTO
finally i manage to get this wusb54gsv2.1 to work

Hey, no problem. I'm glad to see that people are gaining from my months of research and debugging! :D

---

### Post by rosh_joshua on 2007-09-09
Thank you all so much, I followed the instructions to a T and everything is working fine with my WUSBGSv2!  If I can post any log files of things please let me know and I can do so.

---

### Post by mastern200 on 2007-09-14
this is a great tutorial but i have one problem. when ever i try to install the sys files for wusb54gsv2, it just skips a line in the terminal. then i restart the comp, and still, ndiswrapper -l shows invalid driver

---

### Post by javaJake on 2007-09-15
> **mastern200 said:**
> this is a great tutorial but i have one problem. when ever i try to install the sys files for wusb54gsv2, it just skips a line in the terminal. then i restart the comp, and still, ndiswrapper -l shows invalid driver

To figure this out, I'll need you to run the following commands, and then tell me what they each say:

```

ndiswrapper -l
ls -R /etc/ndiswrapper/

```

You can copy from the terminal by selecting the text you want to copy, and hitting Ctrl+Shift+C. You can use the regular Ctrl+V to paste when you are making a reply.

---

### Post by devilmyarse on 2007-09-16
HELP!!

I've installed the Belkin broadcom usb wireless dongle using these instructions and it's worked perfectly for weeks. However i went to use the computer today and it's finding my wireless router fine, and all the settings are as they were but I cannot connect to any websites. 

Typing ifconfig says that my wlan0 is connected to my router. but is not displaying that it has an ip address anywhere...

ndiswrapper is working fine and the usb dongle has lights flashing, but i cannot connect to the internet at all. 

Please help 

(btw i have 99-custom.rules configured properly in udev for my device and everything has worked perfectly for weeks)


EDIT: Nevermind i fixed it by assigning a bogus essid through terminal and manually configuring again.

---

### Post by mastern200 on 2007-09-17
ok thanks

> 
sina@sina-desktop-ubuntu:~$ ndiswrapper -l
bcmrndis : invalid driver!
wusb54gsv2 : invalid driver!
sina@sina-desktop-ubuntu:~$ ls -R /etc/ndiswrapper/
/etc/ndiswrapper/:
[COLOR="Blue"]bcmrndis  wusb54gsv2[/COLOR]

/etc/ndiswrapper/bcmrndis:
050D:7051.F.conf     1799:7051.F.conf     bcmrndis.inf

/etc/ndiswrapper/wusb54gsv2:
rndismp.sys   usb8023.sys


by the way, i typed this. copying didnt work right

---

### Post by javaJake on 2007-09-17
OK, I see your problem right off. There are supposed to be three files within the /etc/ndiswrapper/wusb54gsv2 folder. According to what you gave me, there are only two files:

```

rndismp.sys usb8023.sys

```

Try running the following command again in the folder with the WUSB54GS v2 drivers:
```
sudo ndiswrapper -i wusb54gsv2.inf
```

---

### Post by mastern200 on 2007-09-17
thanks but it still says invalid driver even after the inf file was added
```

sina@sina-desktop-ubuntu:~$ ls -R /etc/ndiswrapper/
/etc/ndiswrapper/:[COLOR="Blue"]
bcmrndis wusb54gsv2
[/COLOR]
/etc/ndiswrapper/bcmrndis:
050D:7051.F.conf 1799:7051.F.conf bcmrndis.inf

/etc/ndiswrapper/wusb54gsv2:
rndismp.sys usb8023.sys wusb54gsv2.inf

sina@sina-desktop-ubuntu:~$ ndiswrapper -l
bcmrndis : invalid driver!
wusb54gsv2 : invalid driver!

```
I restarted the computer and everything

---

### Post by javaJake on 2007-09-18
Hmmm, this is indeed puzzling. Did you use the drivers from the attachment, or your own? Sometimes users get drivers from a different location than the official Linksys website or my attachment and they turn out to be bad.

Try completely removing all installed drivers...
```
sudo rm -R /etc/ndiswrapper/* **(The * is important! Do not drop that!)**
```

...and reinstalling them again. Tell me if there were any extra errors or messages. If all went well, the only messages you should be getting are the ones when you run "ndiswrapper -l".

*Right after* all this, copy /var/log/syslog to your Desktop and attach it here. (You'll find attachment options in the section "Additional Options" below the text box where you type a reply.)

---

### Post by mastern200 on 2007-09-19
nice idea! it installed, but still no internet. when i ndiswrapper -l, it shows its installed though...
btw, when i tried attaching the log, it was too large to upload

---

### Post by javaJake on 2007-09-19
> **mastern200 said:**
> nice idea! it installed, but still no internet. when i ndiswrapper -l, it shows its installed though...
btw, when i tried attaching the log, it was too large to upload

OK, "installed" is good - try rebooting without the device plugged in, and then when you are ready, plug it in. After around 10 seconds, make a new copy of /var/log/syslog. Don't delete the old one, though.

Just post the last, say, 50 or 100 lines of both files. Let me know which is which.

---

### Post by mastern200 on 2007-09-19
ok here. only got around 50 lines. tried to get the important stuff

---

### Post by javaJake on 2007-09-21
> **mastern200 said:**
> ok here. only got around 50 lines. tried to get the important stuff

Sorry, but this information isn't useful to me at all. After following the [instructions]("http://ubuntuforums.org/showpost.php?p=3392345&postcount=211") I gave you, please copy the last 50 or more lines at the _end_ of the /var/log/syslog file. Also, don't wait too long after plugging in the device (no more than a minute), or the messages I'm looking for might get buried farther up.

---

### Post by mastern200 on 2007-09-21
ok sorry. One file, i copied the information from when i turned my computer on to when i plugged it in. the other file is the messages that came up after i unplugged it. so, essentially, everything should be in there from when i logged in to ubuntu. hope this is what you wanted and it helps. thanks for everything though

---

### Post by javaJake on 2007-09-22
> **mastern200 said:**
> ok sorry. One file, i copied the information from when i turned my computer on to when i plugged it in. the other file is the messages that came up after i unplugged it. so, essentially, everything should be in there from when i logged in to ubuntu. hope this is what you wanted and it helps. thanks for everything though

OK, here we are... this is one of the things I was looking for:
```

Sep 21 23:04:13 sina-desktop-ubuntu kernel: [  118.616356] usb 5-6: new high speed USB device using ehci_hcd and address 7
Sep 21 23:04:13 sina-desktop-ubuntu kernel: [  118.751072] usb 5-6: no configuration chosen from 1 choice

```

What does this mean? Well, you can see it found a "new high speed USB device" when you connected it. But then it selected "no configuration chosen from 1 choice", or, in other words, it knew ndiswrapper had the drivers and all that, but it decided not to let ndiswrapper handle the device. In short, your computer decided it wouldn't let the device properly start up.

So, the stuff you entered when you followed the section "Getting WUSB54GS to Work in Edgy and Feisty" isn't working, for some reason. I recommend you check to be sure there are no typos, and that you punched in the right version.


Please accept my apologies for not being more patient earlier.

---

### Post by mastern200 on 2007-09-22
wow it worked! thanks a lot man! no apologies needed. you chose to help me when you could have just said no. thanks again!

---

### Post by javaJake on 2007-09-22
I'm curious - what fixed it? :)

---

### Post by mastern200 on 2007-09-22
i think it was the retyping of the getting wusb54gs to work with fiesty section. i copied and pasted it instead of typing it. guess it did something :)

---

### Post by javaJake on 2007-09-22
> **mastern200 said:**
> i think it was the retyping of the getting wusb54gs to work with fiesty section. i copied and pasted it instead of typing it. guess it did something :)

Yea, missing a single punctuation mark messes the whole thing up. The best part is is it doesn't even tell you what went wrong. :p

---

### Post by Jordan694 on 2007-09-22
Amazing tutorial... isn't working for me though YET... but this is the furthest I've got with it.

I've tried to get as much info for you as I could.

Basically... followed the tutorial but changed the inf file slightly as I am using the Belkin F5D7051 Wireless adapter (ProductId: 7051 and VendorId: 050d). Installed fine, however didn't connect. In the Network Tools dialog I have:

Loopback Interface (lo)
Ethernet Interface (eth0)
Wireless Interface (wlan0) - This had NO hardware address assigned to it, however allowed me to configure it and add Network Passwords etc.
Wireless Interface (wlan:avali) - This has the hardware address however didn't allow configure... if I clicked configure it would say "The interface doesn't exist".

So I restarted with the adapter plugged in and it was really lagging i.e. I would type my username and it would take a few seconds to actually display. I logged in and got an error message. See jpg attachment.

I was also unable to use lsusb.

NOTE: I used ndiswrapper 1.48.





Attached are the custom rules (99-custom.rules), the syslog and also the results of dmesg.


:)


Thank You.

---

### Post by javaJake on 2007-09-22
> **Jordan694 said:**
> I am using the Belkin F5D7051 Wireless adapter

This thread is for the WUSB54GS. I cannot accept other requests for help for other devices here. Sorry. :(

---

### Post by Jordan694 on 2007-09-22
Okay. Thanks Anyway.

---

### Post by TechCowboy on 2007-09-30
Okay...so I was following the discussion on how to get the 64 bit driver working but it looks like DarkLord dropped of the map.  I downloaded the same driver he referenced and made the changes but did not yet plug in the device (hoping to avoid the mismatch in where the system thought the device should be and where it really is.)  When I run ndiswrapper -l, I get back invalid driver! Can we get back to making the 64 bit version working?  I really don't want to go back to a 32 bit install.  Thanks!

---

### Post by javaJake on 2007-10-01
> **TechCowboy said:**
> Okay...so I was following the discussion on how to get the 64 bit driver working but it looks like DarkLord dropped of the map.  I downloaded the same driver he referenced and made the changes but did not yet plug in the device (hoping to avoid the mismatch in where the system thought the device should be and where it really is.)  When I run ndiswrapper -l, I get back invalid driver! Can we get back to making the 64 bit version working?  I really don't want to go back to a 32 bit install.  Thanks!

Last I heard, his device was giving him one or the other following errors:

> **darklord said:**
> [  319.437633] ndiswrapper version 1.21 loaded (preempt=yes,smp=yes)
[  319.443827] usbcore: registered new driver ndiswrapper
[ 1021.844387] usb 1-1: USB disconnect, address 2
[ 1025.487613] usb 1-1: new high speed USB device using ehci_hcd and address 5
[ 1025.555786] usb 1-1: bad CDC descriptors

...or...

> **cjbrunner said:**
> 
ndiswrapper (import:241): unknown symbol: NDIS.SYS:'NdisIMNotifyPnPEvent'
ndiswrapper (load_sys_files:214): couldn't prepare driver 'wusb54gs'
ndiswrapper (load_wrap_driver:113): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'
ndiswrapper: probe of 1-3:1.1 failed with error -22

The first error has yet to be explained, but we do know now it prohibits the loading of any drivers. It isn't harmless as I claimed months ago. The second error is worse - ndiswrapper was unable to load the 64-bit drivers the guy had.


As far as I know, there's two things you can try: grab 64-bit drivers from a 64-bit Windows installation, and/or contact the ndiswrapper mailing list with your issue.

Be sure to let me know how it all turns out if you do contact the mailing list!

---

### Post by desmondo on 2007-10-14
For those having trouble with the WUSB54GSC with the Broadcom chipset, see [this thread]("http://ubuntuforums.org/showthread.php?p=3533694#post3533694").

The drivers you'll need are in the 3rd post; the .inf is from Linksys, and the .sys's are from Belkin.

> **leetcharmer said:**
> can you post your driver files?  The only ones on my CD for windows has WUSB54GSC.inf and WUSB54GSC.cat, no rt73.*

---

### Post by javaJake on 2007-10-14
> **desmondo said:**
> For those having trouble with the WUSB54GSC with the Broadcom chipset, see [this thread]("http://ubuntuforums.org/showthread.php?p=3533694#post3533694").

The drivers you'll need are in the 3rd post; the .inf is from Linksys, and the .sys's are from Belkin.

[color=grey]Thanks for creating instructions, however I am not too particularly pleased that you copied my HOWTO almost to the letter without giving credit.

Please at least give a link at the top of your HOWTO. Once you do this, I will link to yours for anyone looking for the WUSB54GSC. I would also be happy to give you the source of my HOWTO so that you can have the formatting as well.

I do appreciate your work, and want to encourage other users to add their knowledge, not suppress them.[/color]

**Edit:** Never mind, see: [http://ubuntuforums.org/showthread.php?p=3545340#post3545340](http://ubuntuforums.org/showthread.php?p=3545340#post3545340)

---

### Post by desmondo on 2007-10-16
rdon included a link to this thread at the end of the original post, under "information sources bibliography:"

> **javaJake said:**
> Thanks for creating instructions, however I am not too particularly pleased that you copied my HOWTO almost to the letter without giving credit.

---

### Post by javaJake on 2007-10-16
> **desmondo said:**
> rdon included a link to this thread at the end of the original post, under "information sources bibliography:"

Ah, yes, I missed that. I thought I had reached the end when I hit the underscore seperation and stopped (admittedly speed-) reading.

I apologize, and have edited my original post.

---

### Post by interconnect on 2007-10-21
hi, thanks for the great instructions! i got my wusb54gs v1 working in ubuntu 7.10 by following your instructions and using ndiswrapper 1.48.. worked like a charm.

---

### Post by javaJake on 2007-10-21
> **interconnect said:**
> hi, thanks for the great instructions! i got my wusb54gs v1 working in ubuntu 7.10 by following your instructions and using ndiswrapper 1.48.. worked like a charm.

Great! I'll add Gutsy to the supported OSs then! :D

---

### Post by Keye239 on 2007-10-22
Hey guys whats goin on, im really new to unbuntu but I like open source.. Im just stuck on the part with installing my wireless adapter v2.. I cant figure how to install the .sys files

sudo cp usb8023.sys /etc/ndiswrapper/wusb54gsv2/
sudo cp rndismp.sys /etc/ndiswrapper/wusb54gsv2/

i type it in and it doesn't work, the only thing I can think of is I placed the files in he wrong place. I grab the files from my laptop and placed them on a cd, then on my desktop made a folder named driver and have everything in there, I just cant seem to get it to work or install, im sure its something dumb but, thats why I came here, thanks for the help..

---

### Post by manizzle on 2007-10-31
i have a question. So i followed all the directions and all, do everything and guess what? it works perfectly!!!! but now, whever i restart ubunut or w.e., i have to unplug my adapter, type 

sudo modprobe ndiswrapper

then plug my adapter back in

is this normal? its really annyoing...aight thanks

---

### Post by javaJake on 2007-11-01
> **manizzle said:**
> i have a question. So i followed all the directions and all, do everything and guess what? it works perfectly!!!! but now, whever i restart ubunut or w.e., i have to unplug my adapter, type 

sudo modprobe ndiswrapper

then plug my adapter back in

is this normal? its really annyoing...aight thanks

To fix this, run the below command. If you want to use NetworkManager, however, see the NetworkManager section in this HOWTO.
```
sudo ndiswrapper -m
```

Good luck! :)

---

### Post by Diggorydo on 2007-11-07
> **javaJake said:**
> 

**_Step 5 - Connecting up the device_**
Alright. Now you get to actually enjoy all this work. Run this command:

```
sudo modprobe ndiswrapper
```
[INDENT]If you get a "FATAL" error that says "/lib/<kernel>/misc/ndiswrapper.ko: invalid argument" then that means that you haven't gotten any drivers installed yet.[/INDENT]



Thanks for the great HOW-TO javaJake.  I'm a newb that's just had the umbilical cord cut, so it's good to have some clear advice on how to do this.  I had to do some swatting up on the terminal, but I'm getting there, and I've managed to find the answers to some problems.  I haven't got my Linksys WUSB54GSv2 working yet, but I think I'm getting there.  Bear in mind that as a newb, my work outside of this thread has been utter guesswork, so if I say something here that doesn't make sense, I'd welcome the feedback.

I did have a problem at step 5 of the HOW-TO (reproduced above).  In stead of ** Invalid Argument **, I got a **No such file or directory** (not the same as in the error in the below URL).

I couldn't find a corresponding post in this thread on the subject, so I'm posting a link to a Gutsy development forum where I found the answer (at least it solved my problem, and 'ndiswrapper -l' gave me installed drivers afterwards):

[http://ubuntuforums.org/archive/index.php/t-541384.html](http://ubuntuforums.org/archive/index.php/t-541384.html)

Briefly, **cro** says that Synaptic doesn't install the libraries in the correct places, so they have to be installed manually (as in the HOW-TO).  I used Synaptic cause I didn't know the first thing about Terminal at that stage.

I thought it might be a good idea (if my logic is watertight) to put a note on the HOW-TO mentioning this for anyone else with the same problem.  Also, would this be the sort of thing that Developers would be interested in knowing? 

FYI I'm running Feisty (fully updated yesterday).

---

### Post by javaJake on 2007-11-10
> **Diggorydo said:**
> Briefly, **cro** says that Synaptic doesn't install the libraries in the correct places, so they have to be installed manually (as in the HOW-TO).  I used Synaptic cause I didn't know the first thing about Terminal at that stage.Yes, Synaptic is fine. I need to update the HOWTO to use GUI alternatives, since the people who use the terminal usually know how to turn GUI instructions into Terminal ones. :)

> **Diggorydo said:**
> I thought it might be a good idea (if my logic is watertight) to put a note on the HOW-TO mentioning this for anyone else with the same problem.Of course, I'll add that to the Troubleshooting section.

> **Diggorydo said:**
> Also, would this be the sort of thing that Developers would be interested in knowing?Absolutely! launchpad.net is the place to go for that!

---

### Post by Sculay on 2007-11-14
Hello 
Im currently having problems getting the device to switch on
it shows up as its installed and plugged in but doesnt show the LED power up
im currently running uBuntu 7.10 gutsy
using wusb54gsv2
did everything the tutorial said even the power thing you mentioned near the end and i still cannot get the thing to work

Thanks in advance

fyi im just moving to ubuntu as im sick of windows lol
so i am a complete nub at linux


log:
[http://www.nomorepasting.com/getpaste.php?pasteid=6896](http://www.nomorepasting.com/getpaste.php?pasteid=6896)

ive gotten to the point ubuntu crashes when i plug the device in

---

### Post by rstaples01 on 2007-11-18
Hi JavaJake,
Thanks very much for the tutorial!  I just got it to work with the latest ndiswrapper.
I am new to forums, but if you are still looking for someone to reformat the tutorial I am willing and able.  Just need to get pointed in the right direction.
Thanks again,
Bob S

---

### Post by javaJake on 2007-11-24
> **Sculay said:**
> Hello 
Im currently having problems getting the device to switch on
it shows up as its installed and plugged in but doesnt show the LED power up
im currently running uBuntu 7.10 gutsy
using wusb54gsv2
did everything the tutorial said even the power thing you mentioned near the end and i still cannot get the thing to work

Thanks in advance

fyi im just moving to ubuntu as im sick of windows lol
so i am a complete nub at linux


log:
[http://www.nomorepasting.com/getpaste.php?pasteid=6896](http://www.nomorepasting.com/getpaste.php?pasteid=6896)

ive gotten to the point ubuntu crashes when i plug the device in

It looks like you have another driver named "bcmrndis" installed for this device. Please run the following commands to confirm this, and then I can give you instructions to clean it up and get your computer back on its feet:

```

ndiswrapper -l *(That's an L)*
ls -R /etc/ndiswrapper/

```

---

### Post by javaJake on 2007-11-24
> **rstaples01 said:**
> Hi JavaJake,
Thanks very much for the tutorial!  I just got it to work with the latest ndiswrapper.
I am new to forums, but if you are still looking for someone to reformat the tutorial I am willing and able.  Just need to get pointed in the right direction.
Thanks again,
Bob S

Thanks for volunteering! The guidelines are [here](http://ubuntuforums.org/showthread.php?t=316820), and as you can see, not everything they require is in my HOWTO. Of course, those apply to new HOWTOs, but I think they are really good guidelines, so I want to follow them as well.

Here are the rules I don't follow currently:
[LIST=1]
[*]Credit to the base of your info unless you wrote the guide from scratch.
[*]A detailed explanation of what the guide/script/etc does.
[*]A way of uninstalling or undoing any changes made
[*]Users who post guides are asked to retest the guide on the next Ubuntu release.
[/LIST]

The last one is easy enough, but the first one I should really do. What I'll do is PM you the guide's source, and you can edit it and then send it back.

Once you confirm you are ready, I'll go ahead and send it to you.

---

### Post by Envirotech on 2007-11-27
I have followed you tutorial when using the live cd on a wusb54gsc and it work flawlessly.  I then proceeded to install ubuntu 7.10 and I have had nothing but headache's.

the last step "ndiswrapper -l"

```

wusb54gsc : driver installed
        device (13B1:0026) present

```
when I go into the network manager the wireless never shows up.
i have done
sudo modprobe ndiswrapper
sudo nano -w /etc/udev/rules.d/99-custom.rules

```

BUS=="usb", SYSFS{idProduct}=="0026", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"

```
which is for my card.

Is there a diverence with the live-cd and the install? live-cd worked great.

---

### Post by Anacranom on 2007-12-07
I have a quick question, I have not bought a wireless NIC or USB adapter yet,,, Do you have a list of known brands/models that work right out of the box? or with little config'? if so, I'll buy that one.
Thanks

(I am using Gutsy, pent.D 3.4, 2Gb ram, Dual-booted with xp-pro~which I haven't needed to log into in almost 6 months! 8-) )

---

### Post by javaJake on 2007-12-07
> **Anacranom said:**
> I have a quick question, I have not bought a wireless NIC or USB adapter yet,,, Do you have a list of known brands/models that work right out of the box? or with little config'? if so, I'll buy that one.
Thanks

(I am using Gutsy, pent.D 3.4, 2Gb ram, Dual-booted with xp-pro~which I haven't needed to log into in almost 6 months! 8-) )

If you are looking for a PCMCIA card, the ASUS WL-107g card works beautifully for me. In one college I had to use System->Administration->Networking instead of NetworkManager (even though it was a regular ol' network) but I was fine once I figured that out.

Try looking through wiki.ubuntu.com, they have a lot of good information there about compatibility.

---

### Post by javaJake on 2007-12-07
> **Envirotech said:**
> I have followed you tutorial when using the live cd on a wusb54gsc and it work flawlessly.  I then proceeded to install ubuntu 7.10 and I have had nothing but headache's.

the last step "ndiswrapper -l"

```

wusb54gsc : driver installed
        device (13B1:0026) present

```
when I go into the network manager the wireless never shows up.
i have done
sudo modprobe ndiswrapper
sudo nano -w /etc/udev/rules.d/99-custom.rules

```

BUS=="usb", SYSFS{idProduct}=="0026", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"

```
which is for my card.

Is there a diverence with the live-cd and the install? live-cd worked great.

I'll need /var/log/syslog after you have plugged in the device. While you wait for my response, check to be sure you didn't mistype anything in /etc/udev/rules.d/99-custom.rules file. You won't be told if you did - in fact, nothing will happen.

---

### Post by Anacranom on 2007-12-08
Do you know of a PCI or usb for a desktop?

---

### Post by mLes-_- on 2007-12-22
I got to the "Without the attatchment" part and when I reload the sources I get:

[http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz:) Could not resolve 'archive.ubuntu.com'

I am assuming this is b/c of now Internet connection.  If I am trying to make my internet connection work, how do I get files from the Internet?  I went back into XP and typed the address into IE and it wouldnt start the d/l.  Please respond soon someone.  Thanks

---

### Post by javaJake on 2007-12-23
> **mLes-_- said:**
> I am assuming this is b/c of now Internet connection.  If I am trying to make my internet connection work, how do I get files from the Internet?  I went back into XP and typed the address into IE and it wouldnt start the d/l.  Please respond soon someone.  Thanks

You are correct: you need the internet for what you are doing. Please follow the HOWTO - it only requires you get one or two files onto your computer, possibly though some other computer.

---

### Post by timothy.stiffler on 2007-12-30
So, I have a problem.
I have my wireless driver installed for my Buffalo Turbo G USB wireless device...now I am trying to get the device to be recognized.

I followed the tutorial in the "Getting WUSB54GS to Work in Edgy, Feisty, and Gutsy" section, but my computer freezes each time. I also used two other variables that I found online for the Vendor and Product settings that matched my device, replacing values for idVendor with 0411 and idProduct with 00bc. 

I have the two files requested after the little "restating" section, and hope to get this figured out very soon, because it's been two days since I've had an internet connection using my WiFi, and it's an essential part of my web-design business that I have it.

Thanks!
Tim

---

### Post by paladaxar on 2008-02-18
[http://ubuntuforums.org/showthread.php?t=540942]("http://ubuntuforums.org/showthread.php?t=540942")

Could someone who knows what they are doing take a look at that thread and break it down into a simple tutorial like the one provided in this thread?  

I'm a complete newbie and I am trying to install the WUSB54GSv2 on the 64bit version of Gusty.

Is this possible?  Thanks

---

### Post by 0vermind on 2008-03-09
CRAP! Just my luck, I picked Ubuntu x64 after spending a night searching on what was the best choice. People here (not this topic but the forums) mentioned that x64 was faster, more secure, and could run 32-bit drivers if needed and wasn't hard. 

So I installed Ubuntu x64 and went all through this guide and everything worked flawlessly until you said to look for the slow light. At which I found my self  searching the topic after I plugged in the device and nothing happened. 

So I thought maybe I was suppose to install a certain x64 drivers, so grabbed then from a helpful user[ at the Linksys Forums]("http://forums.linksys.com/linksys/board/message?board.id=Wireless_Adapters&message.id=2699") (a bunch of Linksys 64-bit drivers are on this topic)

And reinstalled/copied the drivers to the etc/ndiswrapper/wusb54gs folder and now when I plugin the device the Link LED turns on then right back off (like in Windows when you don't have any drivers installed for it).

Then I saw your note about x64. Sigh....... I have the worst luck with Internet, first it was Vista and finding the write device to work with Vista, now it won't work in Ubuntu :'(

I haven't even gotten to the saddest part of the entire story...
**All of my devices worked fine in Ubuntu 7.04 no ndiswrapper or anything. Even Wireless worked flawlessly all I did was plug it in and it just worked NO DRIVERS has to be installed!**

So am I out of luck? Please help me!


Thanks,
-Mike

**Edit: I see that a few other people need guidance on this too. (See, replys before mine)**

---

### Post by javaJake on 2008-03-10
As far as I can tell, yes, you are out of luck. However, Linksys does provide x64 drivers. I was debugging these with another fellow but he mysteriously disappeared.

Try those with ndiswrapper.

---

### Post by 0vermind on 2008-03-10
Did the adapter nows turns on and back off quickly. I think that means I'm getting closer. Because in Windows that means you are missing something like a certain file or driver. But NDISWRAPPER tells me it's installed when I do NDISWRAPPER -L

---

### Post by javaJake on 2008-03-11
Can you post your /var/log/syslog file when this happens?

---

### Post by mikespike2 on 2008-03-14
javajake, great tutorial!  I think I am close.. but please help!!

I am getting an error in the syslogafter running sudo depmod -a and sudo modprobe ndiswrapper.

How can I upload it?  I lose the formatting if I open the file in notepad on my Windows machine that is online.

It is saying ndiswrapper (import:245): unknown symbol: NDIS.SYS: 'NdisIMNodifyPnPEvent'

and ndiswrapper (load_sys_files:216): couldn't prepare driver 'wusb54gs'.


I followed the instructions and it also has the two .sys files copied into the /etc/ndiswrapper/wusb54gs folder.  And when I run ndiswrapper -l I get wusb54gs : driver installed  (next line) device (13B1:000E) present

But I see no evidence of wireless appearing.

I am using 7.10 i386.


I tried this tutorial as well:
[http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547)

iwconfig:
lo     no wireless extensions
eth0     no wireless extensions

---

### Post by javaJake on 2008-03-15
Are you using the driver included in the attachment? It looks like you might have an invalid driver.

---

### Post by javaJake on 2008-04-12
**_HOWTO Overhaul_**
I just went through and redid the HOWTO, so it is easier to follow. Plus, I added screenshots, so hopefully new users can keep up. :)

---

### Post by 0vermind on 2008-04-14
> **javaJake said:**
> **_HOWTO Overhaul_**
I just went through and redid the HOWTO, so it is easier to follow. Plus, I added screenshots, so hopefully new users can keep up. :)

Great idea on the screenshots, especially for the newbies that have no idea what the heck they are doing. 

I much appreciated the further information you seem to have added near the bottom regarding WUSB54GS v2. I got it to work on Ubuntu 8.04 Beta x86.

Thanks Jake!
-Mike

[FONT=Franklin Gothic Medium][SIZE=1]
[COLOR=Sienna]Just a warning for future users: There is **no way** to get the WUSB54GS v2 to work on Ubuntu 64-bit. I already tried it's **not possible**.[/COLOR][/SIZE][/FONT]

---

### Post by tengobotas on 2008-04-22
OK I posted earlier and this is an edit because things seem to be coming together better now.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

My problem seems to be network manager, the interface is setup correctly as seen above. At the moment there are no networks populating the list and im at a loss about setting anything up manually.

Here is the last line in my /var/log/syslog after disabling and re-enabling the wireless networking with NetworkManager

Apr 22 22:36:08 Rangpoq NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 

Thanks and again, amazing howto.

---

### Post by thetechnaddict on 2008-04-27
Thanks for this how to - I feel I'm really close!

I'm trying to convert a friend to Linux and am being confounded by usb wireless devices on their desktop. The closest so far seems to be the WUSB54GSv2.

I have installed ndiswrapper and drivers using this How to and the ndiswrapper files from sourceforge, everything seemed just fine.

The Power light comes on and network-manager scans and finds wireless networks. It even finds the correct encryption, but refuses to connect. I enter password and go round the loop a few times.

The desktop has a wireless keyboard and mouse, which may or may  not be relevant to why the wifi is switching alias to wlan1.

I've been going through the this thread for several hours and have yet to work it out. Any help would be most appreciated.

Some info gathered:

<iwconfig>

lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

<ifconfig wlan0 up >

wlan0: ERROR while getting interface flags: No such device 
verity@verity-desktop:~$ sudo ifconfig wlan0 up 
wlan0: ERROR while getting interface flags: No such device 

<lsusb>

Bus 004 Device 003: ID 13b1:0014 Linksys 
Bus 004 Device 002: ID 1516:8628  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

<ndiswrapper -l>

wusb54gsv2 : driver installed 
	device (13B1:0014) present 

<ndiswrapper -v>
utils version: '1.9', utils version needed by module: '1.9' 
module details: 
filename:       /lib/modules/2.6.24-16-generic/misc/ndiswrapper.ko 
version:        1.52 
vermagic:       2.6.24-16-generic SMP mod_unload 586 

FILE /etc/modprobe.d/aliases

alias net-pf-10 off ipv6


<cat: var/log/dmesg>

[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)

[    0.000000] BIOS-provided physical RAM map:

[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)

[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)

[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)

[    0.000000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)

[    0.000000]  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)

[    0.000000]  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)

[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)

[    0.000000] 0MB HIGHMEM available.

[    0.000000] 767MB LOWMEM available.

[    0.000000] found SMP MP-table at 000f5240

[    0.000000] Entering add_active_range(0, 0, 196592) 0 entries of 256 used

[    0.000000] Zone PFN ranges:

[    0.000000]   DMA             0 ->     4096

[    0.000000]   Normal       4096 ->   196592

[    0.000000]   HighMem    196592 ->   196592

[    0.000000] Movable zone start PFN for each node

[    0.000000] early_node_map[1] active PFN ranges

[    0.000000]     0:        0 ->   196592

[    0.000000] On node 0 totalpages: 196592

[    0.000000]   DMA zone: 32 pages used for memmap

[    0.000000]   DMA zone: 0 pages reserved

[    0.000000]   DMA zone: 4064 pages, LIFO batch:0

[    0.000000]   Normal zone: 1503 pages used for memmap

[    0.000000]   Normal zone: 190993 pages, LIFO batch:31

[    0.000000]   HighMem zone: 0 pages used for memmap

[    0.000000]   Movable zone: 0 pages used for memmap

[    0.000000] DMI 2.3 present.

[    0.000000] ACPI: RSDP signature @ 0xC00F6D20 checksum 0

[    0.000000] ACPI: RSDP 000F6D20, 0014 (r0 AWARD )

[    0.000000] ACPI: RSDT 2FFF3040, 002C (r1 AWARD  AWRDACPI 42302E31 AWRD        0)

[    0.000000] ACPI: FACP 2FFF30C0, 0074 (r1 AWARD  AWRDACPI 42302E31 AWRD        0)

[    0.000000] ACPI: DSDT 2FFF3180, 3A78 (r1 AWARD  AWRDACPI     1000 MSFT  100000E)

[    0.000000] ACPI: FACS 2FFF0000, 0040

[    0.000000] ACPI: APIC 2FFF6C40, 0068 (r1 AWARD  AWRDACPI 42302E31 AWRD        0)

[    0.000000] ACPI: PM-Timer IO Port: 0x1008

[    0.000000] ACPI: Local APIC address 0xfee00000

[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)

[    0.000000] Processor #0 15:2 APIC version 20

[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)

[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])

[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])

[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])

[    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23

[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)

[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)

[    0.000000] ACPI: IRQ0 used by override.

[    0.000000] ACPI: IRQ2 used by override.

[    0.000000] ACPI: IRQ9 used by override.

[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs

[    0.000000] Using ACPI (MADT) for SMP configuration information

[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)

[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000

[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000

[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000

[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 195057

[    0.000000] Kernel command line: root=UUID=d7738bfd-704f-4650-986f-759457a5d05b ro quiet splash

[    0.000000] mapped APIC to ffffb000 (fee00000)

[    0.000000] mapped IOAPIC to ffffa000 (fec00000)

[    0.000000] Enabling fast FPU save and restore... done.

[    0.000000] Enabling unmasked SIMD FPU exception support... done.

[    0.000000] Initializing CPU#0

[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)

[    0.000000] Detected 2539.176 MHz processor.

[   16.639404] Console: colour VGA+ 80x25

[   16.639410] console [tty0] enabled

[   16.640151] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)

[   16.640925] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)

[   16.661428] Memory: 767012k/786368k available (2157k kernel code, 18748k reserved, 998k data, 364k init, 0k highmem)

[   16.661437] virtual kernel memory layout:

[   16.661438]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)

[   16.661439]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)

[   16.661441]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)

[   16.661442]     lowmem  : 0xc0000000 - 0xefff0000   ( 767 MB)

[   16.661443]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)

[   16.661444]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)

[   16.661445]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)

[   16.661449] Checking if this processor honours the WP bit even in supervisor mode... Ok.

[   16.661495] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1

[   16.741463] Calibrating delay using timer specific routine.. 5082.37 BogoMIPS (lpj=10164748)

[   16.741494] Security Framework initialized

[   16.741502] SELinux:  Disabled at boot.

[   16.741519] AppArmor: AppArmor initialized

[   16.741524] Failure registering capabilities with primary security module.

[   16.741533] Mount-cache hash table entries: 512

[   16.741697] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000

[   16.741712] CPU: Trace cache: 12K uops, L1 D cache: 8K

[   16.741715] CPU: L2 cache: 512K

[   16.741718] CPU: Hyper-Threading is disabled

[   16.741720] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000

[   16.741734] Compat vDSO mapped to ffffe000.

[   16.741750] Checking 'hlt' instruction... OK.

[   16.757891] SMP alternatives: switching to UP code

[   16.759683] Freeing SMP alternatives: 11k freed

[   16.759840] Early unpacking initramfs... done

[   17.114182] ACPI: Core revision 20070126

[   17.114262] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.

[   17.118019] CPU0: Intel(R) Pentium(R) 4 CPU 2.53GHz stepping 07

[   17.118067] Total of 1 processors activated (5082.37 BogoMIPS).

[   17.118177] ENABLING IO-APIC IRQs

[   17.118363] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1

[   17.265186] Brought up 1 CPUs

[   17.265214] CPU0 attaching sched-domain:

[   17.265218]  domain 0: span 01

[   17.265220]   groups: 01

[   17.265454] net_namespace: 64 bytes

[   17.265464] Booting paravirtualized kernel on bare hardware

[   17.266116] Time: 11:55:11  Date: 04/27/08

[   17.266154] NET: Registered protocol family 16

[   17.266414] EISA bus registered

[   17.266443] ACPI: bus type pci registered

[   17.305653] PCI: PCI BIOS revision 2.10 entry at 0xfbbf0, last bus=1

[   17.305655] PCI: Using configuration type 1

[   17.305657] Setting up standard PCI resources

[   17.319017] ACPI: EC: Look up EC in DSDT

[   17.322712] ACPI: Interpreter enabled

[   17.322717] ACPI: (supports S0 S1 S4 S5)

[   17.322734] ACPI: Using IOAPIC for interrupt routing

[   17.327522] ACPI: PCI Root Bridge [PCI0] (0000:00)

[   17.328519] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]

[   17.343859] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)

[   17.343968] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)

[   17.344072] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)

[   17.344178] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)

[   17.344284] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)

[   17.344389] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)

[   17.344500] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)

[   17.344609] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)

[   17.344757] Linux Plug and Play Support v0.97 (c) Adam Belay

[   17.344799] pnp: PnP ACPI init

[   17.344809] ACPI: bus type pnp registered

[   17.347740] pnp: PnP ACPI: found 13 devices

[   17.347743] ACPI: ACPI bus type pnp unregistered

[   17.347749] PnPBIOS: Disabled by ACPI PNP

[   17.348048] PCI: Using ACPI for IRQ routing

[   17.348054] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report

[   17.369067] NET: Registered protocol family 8

[   17.369069] NET: Registered protocol family 20

[   17.369161] AppArmor: AppArmor Filesystem Enabled

[   17.373054] Time: tsc clocksource has been installed.

[   17.381099] system 00:00: iomem range 0xf0000-0xf3fff could not be reserved

[   17.381102] system 00:00: iomem range 0xf4000-0xf7fff could not be reserved

[   17.381105] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved

[   17.381108] system 00:00: iomem range 0xfc000-0xfffff could not be reserved

[   17.381111] system 00:00: iomem range 0x2fff0000-0x2fffffff could not be reserved

[   17.381115] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved

[   17.381117] system 00:00: iomem range 0x0-0x9ffff could not be reserved

[   17.381120] system 00:00: iomem range 0x100000-0x2ffeffff could not be reserved

[   17.381123] system 00:00: iomem range 0xffee0000-0xffefffff could not be reserved

[   17.381126] system 00:00: iomem range 0xfffe0000-0xfffeffff could not be reserved

[   17.381129] system 00:00: iomem range 0xfec00000-0xfecfffff could not be reserved

[   17.381132] system 00:00: iomem range 0xfee00000-0xfeefffff could not be reserved

[   17.381140] system 00:02: ioport range 0x4d0-0x4d1 has been reserved

[   17.381143] system 00:02: ioport range 0x294-0x297 has been reserved

[   17.411648] PCI: Bridge: 0000:00:01.0

[   17.411650]   IO window: disabled.

[   17.411657]   MEM window: ec000000-edffffff

[   17.411662]   PREFETCH window: e0000000-e7ffffff

[   17.411689] NET: Registered protocol family 2

[   17.449112] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)

[   17.449544] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)

[   17.450829] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)

[   17.451561] TCP: Hash tables configured (established 131072 bind 65536)

[   17.451566] TCP reno registered

[   17.461242] checking if image is initramfs... it is

[   17.912709] Switched to high resolution mode on CPU 0

[   18.153181] Freeing initrd memory: 7699k freed

[   18.153903] audit: initializing netlink socket (disabled)

[   18.153925] audit(1209297311.388:1): initialized

[   18.156363] VFS: Disk quotas dquot_6.5.1

[   18.156482] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)

[   18.156665] io scheduler noop registered

[   18.156667] io scheduler anticipatory registered

[   18.156669] io scheduler deadline registered

[   18.156684] io scheduler cfq registered (default)

[   18.276390] Boot video device is 0000:01:00.0

[   18.276731] isapnp: Scanning for PnP cards...

[   18.630342] isapnp: No Plug & Play device found

[   18.665702] Real Time Clock Driver v1.12ac

[   18.665830] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled

[   18.665965] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

[   18.666137] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A

[   18.666966] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

[   18.667375] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A

[   18.668401] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize

[   18.668486] input: Macintosh mouse button emulation as /devices/virtual/input/input0

[   18.668621] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12

[   18.668931] serio: i8042 KBD port at 0x60,0x64 irq 1

[   18.668937] serio: i8042 AUX port at 0x60,0x64 irq 12

[   18.672375] mice: PS/2 mouse device common for all mice

[   18.672536] EISA: Probing bus 0 at eisa.0

[   18.672545] Cannot allocate resource for EISA slot 1

[   18.672556] Cannot allocate resource for EISA slot 4

[   18.672572] EISA: Detected 0 cards.

[   18.672576] cpuidle: using governor ladder

[   18.672578] cpuidle: using governor menu

[   18.672695] NET: Registered protocol family 1

[   18.672734] Using IPI No-Shortcut mode

[   18.672777] registered taskstats version 1

[   18.672885]   Magic number: 4:74:935

[   18.673049] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found

[   18.673051] EDD information not available.

[   18.673547] Freeing unused kernel memory: 364k freed

[   18.728077] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1

[   19.960261] fuse init (API version 7.9)

[   19.982470] ACPI: Fan [FAN] (on)

[   19.990223] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]

[   19.992313] ACPI: Thermal Zone [THRM] (43 C)

[   20.674914] SCSI subsystem initialized

[   20.762542] libata version 3.00 loaded.

[   20.770606] usbcore: registered new interface driver usbfs

[   20.770638] usbcore: registered new interface driver hub

[   20.790587] usbcore: registered new device driver usb

[   20.798627] sis900.c: v1.08.10 Apr. 2 2006

[   20.798722] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 16

[   20.799798] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.

[   20.810922] 0000:00:04.0: Using transceiver found at address 1 as default

[   20.814422] eth0: SiS 900 PCI Fast Ethernet at 0xe200, IRQ 16, 00:0c:76:cc:79:28

[   20.828165] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 17

[   20.828249] ACPI: PCI interrupt for device 0000:00:02.5 disabled

[   20.842515] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver

[   20.842592] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 18

[   20.842614] ohci_hcd 0000:00:03.0: OHCI Host Controller

[   20.843059] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1

[   20.843083] ohci_hcd 0000:00:03.0: irq 18, io mem 0xee025000

[   20.900589] usb usb1: configuration #1 chosen from 1 choice

[   20.900623] hub 1-0:1.0: USB hub found

[   20.900637] hub 1-0:1.0: 3 ports detected

[   20.952744] Floppy drive(s): fd0 is 1.44M

[   20.974107] FDC 0 is a post-1991 82077

[   21.002516] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 19

[   21.002540] ohci_hcd 0000:00:03.1: OHCI Host Controller

[   21.002573] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2

[   21.002593] ohci_hcd 0000:00:03.1: irq 19, io mem 0xee020000

[   21.060451] usb usb2: configuration #1 chosen from 1 choice

[   21.060484] hub 2-0:1.0: USB hub found

[   21.060495] hub 2-0:1.0: 3 ports detected

[   21.162418] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 20

[   21.162442] ohci_hcd 0000:00:03.2: OHCI Host Controller

[   21.162475] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3

[   21.162493] ohci_hcd 0000:00:03.2: irq 20, io mem 0xee021000

[   21.220331] usb usb3: configuration #1 chosen from 1 choice

[   21.220366] hub 3-0:1.0: USB hub found

[   21.220382] hub 3-0:1.0: 2 ports detected

[   21.306131] usb 1-3: new full speed USB device using ohci_hcd and address 2

[   21.322459] pata_sis 0000:00:02.5: version 0.5.2

[   21.322500] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 17

[   21.324446] scsi0 : pata_sis

[   21.325654] scsi1 : pata_sis

[   21.326381] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x4000 irq 14

[   21.326385] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x4008 irq 15

[   21.490447] ata1.00: ATA-7: Maxtor 6Y060L0, YAR41VW0, max UDMA/133

[   21.490453] ata1.00: 120103200 sectors, multi 16: LBA 

[   21.506413] ata1.00: configured for UDMA/133

[   21.522024] usb 1-3: configuration #1 chosen from 1 choice

[   21.825713] usb 2-3: new full speed USB device using ohci_hcd and address 2

[   21.825999] ata2.00: ATAPI: GIGABYTE GO-W1616A, J8S2, max UDMA/66

[   21.997839] ata2.00: configured for UDMA/66

[   21.998010] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y060L0   YAR4 PQ: 0 ANSI: 5

[   21.999280] scsi 1:0:0:0: CD-ROM            GIGABYTE GO-W1616A        J8S2 PQ: 0 ANSI: 5

[   22.001219] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 21

[   22.001237] ehci_hcd 0000:00:03.3: EHCI Host Controller

[   22.001277] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4

[   22.001313] PCI: cache line size of 128 is not supported by device 0000:00:03.3

[   22.001325] ehci_hcd 0000:00:03.3: irq 21, io mem 0xee022000

[   22.013566] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004

[   22.013739] usb usb4: configuration #1 chosen from 1 choice

[   22.013769] hub 4-0:1.0: USB hub found

[   22.013778] hub 4-0:1.0: 8 ports detected

[   22.118047] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 19 (level, low) -> IRQ 16

[   22.170857] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[ee024000-ee0247ff]  Max Packet=[2048]  IR/IT contexts=[4/8]

[   22.201497] sata_sis 0000:00:05.0: version 1.0

[   22.201542] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 22

[   22.201550] sata_sis 0000:00:05.0: Detected SiS 180/181/964 chipset in SATA mode

[   22.202854] scsi2 : sata_sis

[   22.203806] scsi3 : sata_sis

[   22.203886] ata3: SATA max UDMA/133 cmd 0xe300 ctl 0xe400 bmdma 0xe700 irq 22

[   22.203891] ata4: SATA max UDMA/133 cmd 0xe500 ctl 0xe600 bmdma 0xe708 irq 22

[   22.413261] usb 2-3: device not accepting address 2, error -62

[   22.469256] usb 1-3: USB disconnect, address 2

[   22.469492] usbcore: registered new interface driver libusual

[   22.669100] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)

[   22.678226] ata3.00: ATA-7: Maxtor 6L250S0, BANC1E00, max UDMA/133

[   22.678231] ata3.00: 490234752 sectors, multi 16: LBA48 NCQ (not used)

[   22.694249] ata3.00: configured for UDMA/133

[   22.964849] usb 4-7: new high speed USB device using ehci_hcd and address 2

[   23.004831] ata4: SATA link down (SStatus 0 SControl 300)

[   23.018239] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6L250S0   BANC PQ: 0 ANSI: 5

[   23.030637] Driver 'sd' needs updating - please use bus_type methods

[   23.030757] sd 0:0:0:0: [sda] 120103200 512-byte hardware sectors (61493 MB)

[   23.030775] sd 0:0:0:0: [sda] Write Protect is off

[   23.030778] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

[   23.030802] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[   23.030863] sd 0:0:0:0: [sda] 120103200 512-byte hardware sectors (61493 MB)

[   23.030876] sd 0:0:0:0: [sda] Write Protect is off

[   23.030879] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

[   23.030900] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[   23.030904]  sda:<4>Driver 'sr' needs updating - please use bus_type methods

[   23.045360]  sda1 sda2 sda3

[   23.056868] sd 0:0:0:0: [sda] Attached SCSI disk

[   23.057128] sd 2:0:0:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)

[   23.057145] sd 2:0:0:0: [sdb] Write Protect is off

[   23.057148] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00

[   23.057173] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[   23.057231] sd 2:0:0:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)

[   23.057244] sd 2:0:0:0: [sdb] Write Protect is off

[   23.057247] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00

[   23.057269] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[   23.057273]  sdb:sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray

[   23.062325] Uniform CD-ROM driver Revision: 3.20

[   23.062399] sr 1:0:0:0: Attached scsi CD-ROM sr0

[   23.078875]  sdb1

[   23.078955] sd 2:0:0:0: [sdb] Attached SCSI disk

[   23.088329] sd 0:0:0:0: Attached scsi generic sg0 type 0

[   23.088356] sr 1:0:0:0: Attached scsi generic sg1 type 5

[   23.088381] sd 2:0:0:0: Attached scsi generic sg2 type 0

[   23.099627] usb 4-7: configuration #1 chosen from 1 choice

[   23.136734] Initializing USB Mass Storage driver...

[   23.352591] usb 4-8: new high speed USB device using ehci_hcd and address 3

[   23.468712] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00010800370323e7]

[   23.484282] Attempting manual resume

[   23.484287] swsusp: Resume From Partition 8:2

[   23.484290] PM: Checking swsusp image.

[   23.484562] PM: Resume from disk failed.

[   23.487665] usb 4-8: configuration #1 chosen from 1 choice

[   23.504458] scsi4 : SCSI emulation for USB Mass Storage devices

[   23.523454] usbcore: registered new interface driver usb-storage

[   23.523462] USB Mass Storage support registered.

[   23.523469] usb-storage: device found at 2

[   23.523471] usb-storage: waiting for device to settle before scanning

[   23.541519] kjournald starting.  Commit interval 5 seconds

[   23.541545] EXT3-fs: mounted filesystem with ordered data mode.

[   28.516925] usb-storage: device scan complete

[   28.517409] scsi 4:0:0:0: Direct-Access      USB2.0  FlashDrive       1.00 PQ: 0 ANSI: 2

[   28.518755] sd 4:0:0:0: [sdc] 1019136 512-byte hardware sectors (522 MB)

[   28.519377] sd 4:0:0:0: [sdc] Write Protect is off

[   28.519382] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00

[   28.519386] sd 4:0:0:0: [sdc] Assuming drive cache: write through

[   28.521999] sd 4:0:0:0: [sdc] 1019136 512-byte hardware sectors (522 MB)

[   28.522623] sd 4:0:0:0: [sdc] Write Protect is off

[   28.522626] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00

[   28.522628] sd 4:0:0:0: [sdc] Assuming drive cache: write through

[   28.522632]  sdc: sdc1

[   28.523451] sd 4:0:0:0: [sdc] Attached SCSI removable disk

[   28.523495] sd 4:0:0:0: Attached scsi generic sg3 type 0

[   31.882215] Linux agpgart interface v0.102

[   31.942540] agpgart: Detected SiS chipset - id:1633

[   31.947376] agpgart: AGP aperture is 64M @ 0xe8000000

[   32.009315] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

[   32.059406] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

[   32.322069] input: Power Button (FF) as /devices/virtual/input/input2

[   32.333814] ACPI: Power Button (FF) [PWRF]

[   32.333945] input: Power Button (CM) as /devices/virtual/input/input3

[   32.349785] ACPI: Power Button (CM) [PWRB]

[   32.973526] input: PC Speaker as /devices/platform/pcspkr/input/input4

[   34.141599] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 23

[   34.464192] intel8x0_measure_ac97_clock: measured 54750 usecs

[   34.464198] intel8x0: clocking to 48000

[   34.775873] logips2pp: Detected unknown logitech mouse model 32

[   35.039429] usbcore: registered new interface driver cdc_ether

[   35.053154] usb 4-8: bad CDC descriptors

[   35.053179] usbcore: registered new interface driver rndis_host

[   35.098938] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input5

[   35.455978] parport_pc 00:0a: reported by Plug and Play ACPI

[   35.456085] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]

[   38.063480] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)

[   38.217362] usb 4-8: reset high speed USB device using ehci_hcd and address 3

[   38.359968] ndiswrapper: driver wusb54gsv2 (Linksys,01/25/2005, 4.01.20.0) loaded

[   38.574796] wlan1: ethernet device 00:18:39:0d:42:c6 using NDIS driver: wusb54gsv2, version: 0x4011405, NDIS version: 0x501, vendor: 'Linksys Wireless-G USB Network Adapter with SpeedBooster', 13B1:0014.F.conf

[   38.575109] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'

[   38.575219] udev: renamed network interface wlan0 to wlan1

[   38.611709] wlan1: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

[   38.619699] ndiswrapper (wrap_procfs_add_ndis_device:399): wlan1 already registered?

[   38.619751] usbcore: registered new interface driver ndiswrapper

[   38.650174] lp0: using parport0 (interrupt-driven).

[   38.750921] Adding 514072k swap on /dev/sda2.  Priority:-1 extents:1 across:514072k

[   39.308396] EXT3 FS on sda3, internal journal

[   40.602043] ip_tables: (C) 2000-2006 Netfilter Core Team

---

### Post by mrmerhai on 2008-04-29
All I can really is thank you and everybody that makes this community what it is! LFL (Linux4Life:)

                         Sincerely,
                                   MrMerhai

---

### Post by javaJake on 2008-05-01
> **thetechnaddict said:**
> 
[   38.575109] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'

[   38.575219] udev: renamed network interface wlan0 to wlan1

[   38.611709] wlan1: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

[   38.619699] ndiswrapper (wrap_procfs_add_ndis_device:399): wlan1 already registered?

[   38.619751] usbcore: registered new interface driver ndiswrapper

[   38.650174] lp0: using parport0 (interrupt-driven).

[   38.750921] Adding 514072k swap on /dev/sda2.  Priority:-1 extents:1 across:514072k

[   39.308396] EXT3 FS on sda3, internal journal

[   40.602043] ip_tables: (C) 2000-2006 Netfilter Core Team

It looks to me like you've got more than one wireless device. The errors I've seen are telling me that wlan0 device doesn't exist (???) and the syslog output is telling me wlan0 was renamed to wlan1 (???). That's one strangely configured system.

Perhaps a reinstall is in order? Otherwise, more information about what other tweaks you've done to get your wireless devices to work and/or the HOWTOs you've followed to date would be very useful.

---

### Post by ahmedh on 2008-05-04
I followed the instructions to a T and the USB (v1) adapter worked perfectly. However, when I restarted Ubuntu, it wouldn't work. The link light never came on again after the restart. I did ndiswrapper -l in terminal, and it said that the driver was installed and that the device was present (13b whatever present). Still, it wouldn't even let me configure wireless internet (only wired and point-to-point) and so obviously I couldn't use my adapter. I would love some help with this--it worked perfectly until I restarted my computer.

NEVERMIND: I ran sudo modprobe ndiswrapper and it started working again! Thank you! 

PS What does modprobe do?

---

### Post by javaJake on 2008-05-04
> **ahmedh said:**
> NEVERMIND: I ran sudo modprobe ndiswrapper and it started working again! Thank you! 

PS What does modprobe do?

It loads a kernel module, generally a driver.

Make sure you read the section on NetworkManager and make sure you've run the following command:```
sudo ndiswrapper -m
```

---

### Post by ahmedh on 2008-05-04
I performed that while I was following along with the tutorial. When I did it again afterwards, the terminal output was something to the effect of "alias already established."

I'm posting from Windows because suddenly Ubuntu lost its connection. After a restart and running modprobe ndiswrapper, Ubuntu will display the two wireless networks in our area. When I try to connect to our home network, the animation goes on for a while until it gives up with the little exclamation mark icon. *Sigh* it seems I can't get it to work right.

---

### Post by s0198362 on 2008-05-07
Can anyone help me please?

I am struggling through this tutorial, but hit a problem immediately.

I run the following command in the terminal:

sudo apt-get install cpp gcc build-essential linux-headers-$(uname -r)


and get the following messages:

Reading package lists... Done
Building dependency tree
Reading state information... Done
cpp is already the newest version
gcc is already the newest version
E: Couldn't find package build-essential


apt-get doesn't ask for the disk as the tutorial suggests.  If I trundle through the rest of the tutorial I can't get anywhere, so assume I am stuck at this first stage.

I am running the latest version of Ubuntu, 8.04 (clean install) - Hardy Heron I think.

Many thanks

---

### Post by crxrocks on 2008-05-09
> **s0198362 said:**
> Can anyone help me please?

I am struggling through this tutorial, but hit a problem immediately.

I run the following command in the terminal:

sudo apt-get install cpp gcc build-essential linux-headers-$(uname -r)


and get the following messages:

Reading package lists... Done
Building dependency tree
Reading state information... Done
cpp is already the newest version
gcc is already the newest version
E: Couldn't find package build-essential


apt-get doesn't ask for the disk as the tutorial suggests.  If I trundle through the rest of the tutorial I can't get anywhere, so assume I am stuck at this first stage.

I am running the latest version of Ubuntu, 8.04 (clean install) - Hardy Heron I think.

Many thanks

You have to add the CD as a repository.  You can do this in the repository manager - I was in Synaptic anyway so I did it there.

---

### Post by javaJake on 2008-05-10
You can also use System -> Administration -> Software Sources -> Third-Party. In there, you'll find an "Add CDROM" button.

---

### Post by javaJake on 2008-05-10
> **ahmedh said:**
> I performed that while I was following along with the tutorial. When I did it again afterwards, the terminal output was something to the effect of "alias already established."

I'm posting from Windows because suddenly Ubuntu lost its connection. After a restart and running modprobe ndiswrapper, Ubuntu will display the two wireless networks in our area. When I try to connect to our home network, the animation goes on for a while until it gives up with the little exclamation mark icon. *Sigh* it seems I can't get it to work right.

This is no longer a problem with the device. If you have a WUSB54GS v1, v2, or v2.1 device, and it is working this far, it is working perfectly. At this point you need to tell NetworkManager (the little icon that configures your networks) what to connect to and how. It sounds like you are connecting to an encrypted network with a bad key, or you aren't close enough to the router.

If none of this is working, then try System -> Administration -> Networking. Remove roaming mode from the wireless device and configure your device to connect to your network. (Re-enable roaming mode if you want to use NetworkManager, the icon in the corner, to configure your wireless instead.)

If you just can't get anything to work, post the /var/log/syslog file after an attempt to connect. Be sure to search in that file for any passwords or names you don't want to be public before posting.

---

### Post by Ky3r0z on 2008-05-10
I can't get this to work. My usb modules keep crashing.

---

### Post by javaJake on 2008-05-10
> **Ky3r0z said:**
> I can't get this to work. My usb modules keep crashing.

Can you show us /var/log/syslog after the crash? Are there any other errors you received?

---

### Post by Ky3r0z on 2008-05-10
> **javaJake said:**
> Can you show us /var/log/syslog after the crash? Are there any other errors you received?


I don't recieve any errors. How do I check the log?

---

### Post by javaJake on 2008-05-10
> **Ky3r0z said:**
> I don't recieve any errors. How do I check the log?

```
gedit /var/log/syslog
```
Enjoy! :)

---

### Post by wlk on 2008-05-11
This is great and has helped me out tremendously.  Thank you.

Now, with Ubuntu 8.04, I get this:

[INDENT]In Ubuntu 8.04, network-manager only manages interfaces that are marked for roaming. Thus, all interfaces that were previously managed by network-manager will be set to roaming mode during upgrade. Technically, this takes any interface stanzas using the dhcp method with no options and that are marked auto, and removes them from /etc/network/interfaces. If you rely on your interfaces being started by ifupdown when the system starts up, you need to re-enable them in /etc/network/interfaces manually, or disable roaming in System -> Administration -> Network[/INDENT]

Could you add some information about the "re-enable them in /etc/network/interfaces manually" part, or reference a link that does?  I'm kind of thick about these things.

---

### Post by Ky3r0z on 2008-05-11
> **javaJake said:**
> ```
gedit /var/log/syslog
```
Enjoy! :)
```
May 11 17:24:19 arturo-laptop kernel: [ 8985.590418] WARNING: at /build/buildd/linux-2.6.24/drivers/usb/host/ehci-hcd.c:869 ehci_urb_dequeue()
May 11 17:24:19 arturo-laptop kernel: [ 8985.590433] Pid: 8375, comm: modprobe Tainted: P        2.6.24-16-generic #1
May 11 17:24:19 arturo-laptop kernel: [ 8985.590475]  [<f888ab3d>] ehci_urb_dequeue+0x14d/0x160 [ehci_hcd]
May 11 17:24:19 arturo-laptop kernel: [ 8985.590567]  [<f88a296f>] unlink1+0x6f/0xe0 [usbcore]
May 11 17:24:19 arturo-laptop kernel: [ 8985.590652]  [<f88a3d42>] usb_hcd_unlink_urb+0x12/0x30 [usbcore]
May 11 17:24:19 arturo-laptop kernel: [ 8985.590702]  [<f9bf7527>] wrap_cancel_irp+0x77/0xb0 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.590799]  [<f9bf4688>] IoCancelIrp+0x38/0x70 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.591073]  [<f9bf9fe4>] mp_init+0xa4/0x1f0 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.591183]  [<f9bfa209>] NdisDispatchPnp+0xd9/0xfc0 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.591280]  [update_curr+0x87/0x110] update_curr+0x87/0x110
May 11 17:24:19 arturo-laptop kernel: [ 8985.591383]  [finish_task_switch+0x8d/0x90] finish_task_switch+0x8d/0x90
May 11 17:24:19 arturo-laptop kernel: [ 8985.591417]  [parport_pc:schedule+0x20a/0x650] schedule+0x20a/0x600
May 11 17:24:19 arturo-laptop kernel: [ 8985.591444]  [ide_core:kunmap_atomic+0x3d/0x29e0] kunmap_atomic+0x3d/0xb0
May 11 17:24:19 arturo-laptop kernel: [ 8985.591476]  [get_page_from_freelist+0x27d/0x410] get_page_from_freelist+0x27d/0x410
May 11 17:24:19 arturo-laptop kernel: [ 8985.591517]  [<f9bf3521>] IoAllocateIrp+0x61/0x80 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.591597]  [mac80211:_spin_lock_bh+0x8/0x40] _spin_lock_bh+0x8/0x20
May 11 17:24:19 arturo-laptop kernel: [ 8985.591612]  [<f9bef604>] get_current_nt_thread+0x44/0x50 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.591692]  [<f9bf3815>] IofCallDriver+0x55/0xc0 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.591784]  [<f9bf885b>] IoSendIrpTopDev+0xbb/0x120 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.591918]  [<f9bf8bb0>] pnp_start_device+0x50/0xb0 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.592064]  [<f9bf8e4f>] wrap_pnp_start_device+0x23f/0x290 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.592205]  [<f9bf9126>] wrap_pnp_start_usb_device+0xa6/0xd0 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.592246]  [find_inode+0x31/0x60] find_inode+0x31/0x60
May 11 17:24:19 arturo-laptop kernel: [ 8985.592255]  [sysfs_ilookup_test+0x0/0x10] sysfs_ilookup_test+0x0/0x10
May 11 17:24:19 arturo-laptop kernel: [ 8985.592314]  [sysfs_addrm_finish+0x4b/0x1c0] sysfs_addrm_finish+0x4b/0x1c0
May 11 17:24:19 arturo-laptop kernel: [ 8985.592328]  [sysfs_add_one+0x44/0xe0] sysfs_add_one+0x44/0xe0
May 11 17:24:19 arturo-laptop kernel: [ 8985.592348]  [sysfs_addrm_start+0x6d/0xb0] sysfs_addrm_start+0x6d/0xb0
May 11 17:24:19 arturo-laptop kernel: [ 8985.592361]  [snd_pcm:mutex_lock+0x8/0x290] mutex_lock+0x8/0x20
May 11 17:24:19 arturo-laptop kernel: [ 8985.592381]  [<f88a682b>] usb_autopm_do_device+0x7b/0x100 [usbcore]
May 11 17:24:19 arturo-laptop kernel: [ 8985.592437]  [<f88a6397>] usb_match_one_id+0x27/0xb0 [usbcore]
May 11 17:24:19 arturo-laptop kernel: [ 8985.592521]  [<f88a75d9>] usb_probe_interface+0xb9/0x140 [usbcore]
May 11 17:24:19 arturo-laptop kernel: [ 8985.592612]  [driver_probe_device+0x88/0x190] driver_probe_device+0x88/0x190
May 11 17:24:19 arturo-laptop kernel: [ 8985.592621]  [scsi_mod:kobject_uevent_env+0xf0/0x2610] kobject_uevent_env+0xf0/0x3d0
May 11 17:24:19 arturo-laptop kernel: [ 8985.592672]  [__driver_attach+0x9e/0xa0] __driver_attach+0x9e/0xa0
May 11 17:24:19 arturo-laptop kernel: [ 8985.592698]  [pcmcia:bus_for_each_dev+0x3b/0x60] bus_for_each_dev+0x3b/0x60
May 11 17:24:19 arturo-laptop kernel: [ 8985.592748]  [usbcore:driver_attach+0x16/0x2b0] driver_attach+0x16/0x20
May 11 17:24:19 arturo-laptop kernel: [ 8985.592755]  [__driver_attach+0x0/0xa0] __driver_attach+0x0/0xa0
May 11 17:24:19 arturo-laptop kernel: [ 8985.592762]  [bus_add_driver+0x8a/0x1e0] bus_add_driver+0x8a/0x1e0
May 11 17:24:19 arturo-laptop kernel: [ 8985.592824]  [<f88a711e>] usb_register_driver+0x8e/0x110 [usbcore]
May 11 17:24:19 arturo-laptop kernel: [ 8985.592915]  [<f9be840c>] loader_init+0x9c/0x140 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.592958]  [<f9bf523f>] wrap_procfs_init+0x3f/0xb0 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.592999]  [<f9bf92f5>] wrapndis_init+0x45/0x50 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.593053]  [<f8be30b7>] wrapper_init+0xb7/0xc2 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.593116]  [sys_init_module+0x126/0x19c0] sys_init_module+0x126/0x19c0
May 11 17:24:19 arturo-laptop kernel: [ 8985.593403]  [<c0164400>] disable_irq+0x0/0x30
May 11 17:24:19 arturo-laptop kernel: [ 8985.593504]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
May 11 17:24:19 arturo-laptop kernel: [ 8985.593622]  =======================
```

---

### Post by hookzilla on 2008-05-12
I have just installed HH on an old P2-450 system: 512mb ram, 3dFX Voodoo Banshee, WUSB54GS V1 USB NIC.  HH loaded quickly, about 20 min.  Add another 30 min to run the How-To for the WUSB54GS V1 USB NIC, and all is well.  The How-To is precise and it works!  Good Job! Thanks!

---

### Post by ahmedh on 2008-05-13
The same problem resurfaced again.

Thanks for the response, but the network is not encrypted and does not require a password (bad, I know). The Windows computer on the network have no problems, and my computer is the closest to the router. I need the internet right now, so I will post the syslog file later on. Thanks!

---

### Post by ahmedh on 2008-05-13
Here's the tail end of my syslog, where I see a lot of network  related disablings and errors.

```
May 13 21:24:40 ahmed-desktop avahi-daemon[5317]: Network interface enumeration completed.
May 13 21:24:40 ahmed-desktop avahi-daemon[5317]: Registering HINFO record with values 'I686'/'LINUX'.
May 13 21:24:40 ahmed-desktop avahi-daemon[5317]: Server startup complete. Host name is ahmed-desktop.local. Local service cookie is 2729947728.
May 13 21:24:40 ahmed-desktop kernel: [   64.268899] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
May 13 21:24:40 ahmed-desktop kernel: [   64.268906] apm: disabled - APM is not SMP safe.
May 13 21:24:40 ahmed-desktop kernel: [   64.404344] ppdev: user-space parallel port driver
May 13 21:24:40 ahmed-desktop kernel: [   64.547133] audit(1210731880.394:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5360 profile="/usr/sbin/cupsd" namespace="default"
May 13 21:24:40 ahmed-desktop dhcdbd: Started up.
May 13 21:24:41 ahmed-desktop kernel: [   66.007567] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
May 13 21:24:42 ahmed-desktop kernel: [   66.207634] ivtv0: Encoder revision: 0x02060039
May 13 21:24:43 ahmed-desktop hal_lpadmin: add
May 13 21:24:43 ahmed-desktop hal_lpadmin: URIs: ['hp:/usb/photosmart_7700_series?serial=MY41C211CMQ0', 'usb://hp/photosmart%207700%20series?serial=MY41C211CMQ0', 'hal:///org/freedesktop/Hal/devices/usb_device_3f0_b402_MY41C211CMQ0_if0_printer_MY41C211CMQ0']
May 13 21:24:44 ahmed-desktop python: hp-makeuri[5563]: error: Device does not support fax.
May 13 21:24:44 ahmed-desktop hal_lpadmin: HPLIP Fax URIs: None
May 13 21:24:44 ahmed-desktop hal_lpadmin: Not adding printer: photosmart_7700_series already exists
May 13 21:24:45 ahmed-desktop kernel: [   69.499111] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
May 13 21:24:46 ahmed-desktop kernel: [   70.221732] eth0: link down
May 13 21:24:46 ahmed-desktop NetworkManager: <info>  eth0: Device is fully-supported using driver '8139too'. 
May 13 21:24:46 ahmed-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
May 13 21:24:46 ahmed-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
May 13 21:24:46 ahmed-desktop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
May 13 21:24:46 ahmed-desktop NetworkManager: <info>  Deactivating device eth0. 
May 13 21:24:46 ahmed-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
May 13 21:24:46 ahmed-desktop NetworkManager: <debug> [1210731886.112137] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_E616P3H'). 
May 13 21:24:46 ahmed-desktop hcid[5635]: Bluetooth HCI daemon
May 13 21:24:46 ahmed-desktop kernel: [   70.322163] Bluetooth: Core ver 2.11
May 13 21:24:46 ahmed-desktop kernel: [   70.323036] NET: Registered protocol family 31
May 13 21:24:46 ahmed-desktop kernel: [   70.323042] Bluetooth: HCI device and connection manager initialized
May 13 21:24:46 ahmed-desktop kernel: [   70.323048] Bluetooth: HCI socket layer initialized
May 13 21:24:46 ahmed-desktop hcid[5635]: Starting SDP server
May 13 21:24:46 ahmed-desktop kernel: [   70.380046] Bluetooth: L2CAP ver 2.9
May 13 21:24:46 ahmed-desktop kernel: [   70.380053] Bluetooth: L2CAP socket layer initialized
May 13 21:24:46 ahmed-desktop hcid[5635]: Created local server at unix:abstract=/var/run/dbus-FTb9xB8xCz,guid=0671ddaee2619735ad00c897482a4d6e
May 13 21:24:46 ahmed-desktop NetworkManager: <debug> [1210731886.250861] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
May 13 21:24:46 ahmed-desktop audio[5666]: Bluetooth Audio daemon
May 13 21:24:46 ahmed-desktop input[5667]: Bluetooth Input daemon
May 13 21:24:46 ahmed-desktop audio[5666]: Unix socket created: 5
May 13 21:24:46 ahmed-desktop audio[5666]: audio.conf: Key file does not have key 'Enable'
May 13 21:24:46 ahmed-desktop audio[5666]: audio.conf: Key file does not have key 'Disable'
May 13 21:24:46 ahmed-desktop kernel: [   70.476443] Bluetooth: RFCOMM socket layer initialized
May 13 21:24:46 ahmed-desktop kernel: [   70.477249] Bluetooth: RFCOMM TTY layer initialized
May 13 21:24:46 ahmed-desktop kernel: [   70.477255] Bluetooth: RFCOMM ver 1.8
May 13 21:24:46 ahmed-desktop input[5667]: Registered input manager path:/org/bluez/input
May 13 21:24:46 ahmed-desktop audio[5666]: add_service_record: got record id 0x10000
May 13 21:24:46 ahmed-desktop audio[5666]: audio.conf: Key file does not have key 'Disable'
May 13 21:24:46 ahmed-desktop audio[5666]: audio.conf: Key file does not have group 'A2DP'
May 13 21:24:46 ahmed-desktop last message repeated 3 times
May 13 21:24:46 ahmed-desktop audio[5666]: SEP 0x806d758 registered: type:0 codec:0 seid:1
May 13 21:24:46 ahmed-desktop audio[5666]: add_service_record: got record id 0x10001
May 13 21:24:46 ahmed-desktop audio[5666]: add_service_record: got record id 0x10002
May 13 21:24:46 ahmed-desktop audio[5666]: add_service_record: got record id 0x10003
May 13 21:24:46 ahmed-desktop audio[5666]: Registered manager path:/org/bluez/audio
May 13 21:24:48 ahmed-desktop ntpd[5753]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
May 13 21:24:48 ahmed-desktop ntpd[5756]: precision = 1.000 usec
May 13 21:24:48 ahmed-desktop anacron[5779]: Anacron 2.3 started on 2008-05-13
May 13 21:24:48 ahmed-desktop anacron[5779]: Normal exit (0 jobs run)
May 13 21:24:48 ahmed-desktop kernel: [   72.917914] NET: Registered protocol family 10
May 13 21:24:48 ahmed-desktop kernel: [   72.918270] lo: Disabled Privacy Extensions
May 13 21:24:48 ahmed-desktop kernel: [   72.920505] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 13 21:24:48 ahmed-desktop /usr/sbin/cron[5813]: (CRON) INFO (pidfile fd = 3)
May 13 21:24:48 ahmed-desktop /usr/sbin/cron[5817]: (CRON) STARTUP (fork ok)
May 13 21:24:48 ahmed-desktop kernel: [   72.958979] [drm] Initialized drm 1.1.0 20060810
May 13 21:24:48 ahmed-desktop /usr/sbin/cron[5817]: (CRON) INFO (Running @reboot jobs)
May 13 21:24:48 ahmed-desktop ntpd[5756]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
May 13 21:24:48 ahmed-desktop ntpd[5756]: Listening on interface #1 wildcard, ::#123 Disabled
May 13 21:24:48 ahmed-desktop ntpd[5756]: Listening on interface #2 lo, ::1#123 Enabled
May 13 21:24:48 ahmed-desktop kernel: [   72.970745] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
May 13 21:24:48 ahmed-desktop ntpd[5756]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
May 13 21:24:48 ahmed-desktop ntpd[5756]: kernel time sync status 0040
May 13 21:24:48 ahmed-desktop kernel: [   72.970758] PCI: Setting latency timer of device 0000:00:02.0 to 64
May 13 21:24:48 ahmed-desktop kernel: [   72.970864] [drm] Initialized i915 1.6.0 20060119 on minor 0
May 13 21:24:48 ahmed-desktop NetworkManager: <debug> [1210731888.840590] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2582_drm_i915_card0'). 
May 13 21:24:48 ahmed-desktop ntpd[5756]: frequency initialized 26.287 PPM from /var/lib/ntp/ntp.drift
May 13 21:24:50 ahmed-desktop ntpd_initres[5863]: host name not found: ntp.ubuntu.com
May 13 21:24:50 ahmed-desktop ntpd_initres[5863]: couldn't resolve `ntp.ubuntu.com', giving up on it
May 13 21:24:50 ahmed-desktop ntpd_initres[5863]: host name not found: libra.rice.edu
May 13 21:24:50 ahmed-desktop ntpd_initres[5863]: couldn't resolve `libra.rice.edu', giving up on it
May 13 21:25:12 ahmed-desktop hcid[5635]: Default passkey agent (:1.24, /org/bluez/passkey) registered
May 13 21:25:12 ahmed-desktop hcid[5635]: Default authorization agent (:1.24, /org/bluez/auth) registered
May 13 21:25:20 ahmed-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
May 13 21:26:00 ahmed-desktop kernel: [  144.416744] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
May 13 21:26:00 ahmed-desktop kernel: [  144.554729] usb 5-4: reset high speed USB device using ehci_hcd and address 3
May 13 21:26:00 ahmed-desktop kernel: [  144.707306] ndiswrapper: driver wusb54gs (Linksys,06/18/2004, 3.60.9.0) loaded
May 13 21:26:00 ahmed-desktop NetworkManager: <debug> [1210731960.834750] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_12_17_a7_5f_ab'). 
May 13 21:26:00 ahmed-desktop kernel: [  144.922670] wlan0: ethernet device 00:12:17:a7:5f:ab using NDIS driver: wusb54gs, version: 0x33c0d03, NDIS version: 0x501, vendor: 'Linksys Wireless-G USB Network Adapter with SpeedBooster', 13B1:000E.F.conf
May 13 21:26:00 ahmed-desktop kernel: [  144.957260] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
May 13 21:26:00 ahmed-desktop kernel: [  144.969285] usbcore: registered new interface driver ndiswrapper
May 13 21:26:00 ahmed-desktop NetworkManager: <info>  wlan0: Device is fully-supported using driver 'ndiswrapper'. 
May 13 21:26:00 ahmed-desktop NetworkManager: <info>  wlan0: driver does not support SSID scans (scan_capa 0x00). 
May 13 21:26:00 ahmed-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
May 13 21:26:00 ahmed-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
May 13 21:26:00 ahmed-desktop NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
May 13 21:26:00 ahmed-desktop NetworkManager: <info>  Deactivating device wlan0. 
May 13 21:26:00 ahmed-desktop NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
May 13 21:26:11 ahmed-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'wlan0'. 
May 13 21:26:11 ahmed-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
May 13 21:26:11 ahmed-desktop NetworkManager: <info>  Will activate connection 'wlan0/linksys'. 
May 13 21:26:11 ahmed-desktop NetworkManager: <info>  Device wlan0 activation scheduled... 
May 13 21:26:11 ahmed-desktop NetworkManager: <info>  Activation (wlan0) started... 
May 13 21:26:11 ahmed-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
May 13 21:26:11 ahmed-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
May 13 21:26:11 ahmed-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
May 13 21:26:11 ahmed-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
May 13 21:26:11 ahmed-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
May 13 21:26:11 ahmed-desktop NetworkManager: <info>  Activation (wlan0/wireless): access point 'linksys' is unencrypted, no key needed. 
May 13 21:26:12 ahmed-desktop NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
May 13 21:26:13 ahmed-desktop kernel: [  157.196990] NET: Registered protocol family 17
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  SUP: response was 'OK' 
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  SUP: response was 'OK' 
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  SUP: response was '0' 
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 6c696e6b737973' 
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  SUP: response was 'OK' 
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  SUP: response was 'OK' 
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  SUP: response was 'OK' 
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
May 13 21:27:13 ahmed-desktop NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>60s), failing activation. 
May 13 21:27:13 ahmed-desktop NetworkManager: <info>  Activation (wlan0) failure scheduled... 
May 13 21:27:13 ahmed-desktop NetworkManager: <info>  Activation (wlan0) failed for access point (linksys) 
May 13 21:27:13 ahmed-desktop NetworkManager: <info>  Activation (wlan0) failed. 
May 13 21:27:13 ahmed-desktop NetworkManager: <info>  Deactivating device wlan0. 
May 13 21:27:13 ahmed-desktop NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
```

Thanks.

---

### Post by Zahirn on 2008-05-16
Would it be possible for someone who got this "how to" to work, to post a video of themselves demonstrating the process? That would be GODLY. I've been trying to get the damned thing to work for ages, but have had no luck at all.

---

### Post by Jonny_S on 2008-05-22
I got this working a long time ago when I was using v6.06 of ubuntu (I think). Anyway I just got ubuntu v8.04 dual booted with Vista after a while away from linux. Not only was the install painfully simple (Windows installer rocks :p) but this HOWTO has once again helped me out.

So I thought I'd post and say thanks to all who have contributed to this HOWTO, its a lifesaver :) (especially javaJake you get a magic star :KS).

---

### Post by javaJake on 2008-05-24
> **wlk said:**
> Could you add some information about the "re-enable them in /etc/network/interfaces manually" part, or reference a link that does?  I'm kind of thick about these things.

> **ahmedh said:**
> Here's the tail end of my syslog, where I see a lot of network  related disablings and errors.

> **Zahirn said:**
> Would it be possible for someone who got this "how to" to work, to post a video of themselves demonstrating the process? That would be GODLY. I've been trying to get the damned thing to work for ages, but have had no luck at all.

Hey guys, I've heard you, and I want to get around to helping you all. Time has been tight, but I wanted to at least let you know I haven't forgotten you. The video might take a while to set up, but I think it's a great idea.

Thanks for the positive feedback, too, Jonny_S! Every happy user makes the effort worthwhile. :)

---

### Post by chrisN_uk on 2008-06-04
Hello! Right, I've used this tutorial before and things have worked fine, but after a recent re-install, I'm having some trouble. Things seem to have been installed ok, but it didn't work so I tried this: [http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547)

And no luck.

```

$ ndiswrapper -l
wusb54g : driver installed
	device (5041:2234) present (alternate driver: p54usb)

/var/log/syslog
...
...
Jun  4 22:23:24 chris-desktop dhclient: Listening on LPF/wlan0/00:0f:66:73:26:bf
Jun  4 22:23:24 chris-desktop dhclient: Sending on   LPF/wlan0/00:0f:66:73:26:bf
Jun  4 22:23:24 chris-desktop dhclient: Sending on   Socket/fallback
Jun  4 22:23:24 chris-desktop avahi-daemon[4910]: Registering new address record for fe80::20f:66ff:fe73:26bf on wlan0.*.
Jun  4 22:23:28 chris-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jun  4 22:23:31 chris-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jun  4 22:23:33 chris-desktop kernel: [  274.486951] wlan0: no IPv6 routers present
Jun  4 22:23:34 chris-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jun  4 22:23:37 chris-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Jun  4 22:23:51 chris-desktop last message repeated 2 times
Jun  4 22:23:58 chris-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
Jun  4 22:23:59 chris-desktop dhclient: No DHCPOFFERS received.
Jun  4 22:23:59 chris-desktop dhclient: No working leases in persistent database - sleeping.
Jun  4 22:23:59 chris-desktop avahi-autoipd(wlan0)[5961]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Jun  4 22:23:59 chris-desktop avahi-autoipd(wlan0)[5961]: Successfully called chroot().
Jun  4 22:23:59 chris-desktop avahi-autoipd(wlan0)[5961]: Successfully dropped root privileges.
Jun  4 22:23:59 chris-desktop avahi-autoipd(wlan0)[5961]: Starting with address 169.254.6.136
Jun  4 22:24:04 chris-desktop avahi-autoipd(wlan0)[5961]: Callout BIND, address 169.254.6.136 on interface wlan0
Jun  4 22:24:04 chris-desktop avahi-daemon[4910]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.6.136.
Jun  4 22:24:04 chris-desktop avahi-daemon[4910]: New relevant interface wlan0.IPv4 for mDNS.
Jun  4 22:24:04 chris-desktop avahi-daemon[4910]: Registering new address record for 169.254.6.136 on wlan0.IPv4.
Jun  4 22:24:08 chris-desktop avahi-autoipd(wlan0)[5961]: Successfully claimed IP address 169.254.6.136
Jun  4 22:24:10 chris-desktop ntpdate[6022]: adjust time server 91.189.94.4 offset -0.001912 sec
Jun  4 22:26:58 chris-desktop kernel: [  582.868579] eth0: link down.
Jun  4 22:26:58 chris-desktop NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Jun  4 22:26:58 chris-desktop NetworkManager: <info>  Deactivating device eth0. 
Jun  4 22:26:58 chris-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5397
Jun  4 22:26:58 chris-desktop dhclient: killed old client process, removed PID file
Jun  4 22:26:58 chris-desktop dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Jun  4 22:26:58 chris-desktop avahi-daemon[4910]: Withdrawing address record for 192.168.1.15 on eth0.
Jun  4 22:26:58 chris-desktop avahi-daemon[4910]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.15.
Jun  4 22:26:58 chris-desktop avahi-daemon[4910]: Interface eth0.IPv4 no longer relevant for mDNS.
Jun  4 22:26:58 chris-desktop dhcdbd: dhco_parse_option_settings: bad option setting: old_server_name =  
Jun  4 22:26:59 chris-desktop avahi-daemon[4910]: Withdrawing address record for fe80::213:8fff:feac:f68c on eth0.
Jun  4 22:26:59 chris-desktop NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Jun  4 22:26:59 chris-desktop NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Jun  4 22:27:34 chris-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Jun  4 22:27:39 chris-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Jun  4 22:27:51 chris-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Jun  4 22:28:03 chris-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
Jun  4 22:28:05 chris-desktop dhclient: No DHCPOFFERS received.
Jun  4 22:28:05 chris-desktop dhclient: No working leases in persistent database - sleeping.
Jun  4 22:29:19 chris-desktop gdm[5245]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Jun  4 22:29:31 chris-desktop pulseaudio[6330]: pid.c: Stale PID file, overwriting.
Jun  4 22:29:34 chris-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Jun  4 22:29:34 chris-desktop NetworkManager: <info>  Updating VPN Connections... 


```

Cheers...

---

### Post by chrisN_uk on 2008-06-07
I'm now at the point that I get:

```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"43HelenRoad"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:9E:64:5F:93   
          Bit Rate=54 Mb/s   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:92/100  Signal level:-37 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

Which suggests things are working, but I can't actually use my wireless! Any help would be much appreciated, thanks in advance for anyone who can help...

---

### Post by tburns88 on 2008-06-14
...

---

### Post by Leadbelly on 2008-06-29
javaJake--

Your work on this thread was excellent and was extremely helpful to me. Thanks.

Leadbelly

---

### Post by javaJake on 2008-06-29
I've replied to a bunch of people in this message. I believe I answered everyone, but if I missed someone, don't hesitate to call out!


> **wlk said:**
> This is great and has helped me out tremendously.  Thank you.

Now, with Ubuntu 8.04, I get this:

[INDENT]In Ubuntu 8.04, network-manager only manages interfaces that are marked for roaming. Thus, all interfaces that were previously managed by network-manager will be set to roaming mode during upgrade. Technically, this takes any interface stanzas using the dhcp method with no options and that are marked auto, and removes them from /etc/network/interfaces. If you rely on your interfaces being started by ifupdown when the system starts up, you need to re-enable them in /etc/network/interfaces manually, or disable roaming in System -> Administration -> Network[/INDENT]

Could you add some information about the "re-enable them in /etc/network/interfaces manually" part, or reference a link that does?  I'm kind of thick about these things.

It's fairly simple, really. Just go into System -> Administration -> Network, (if you're in Ubuntu Hardy click the Unlock button), then select the device, click Properties, and uncheck "Enable roaming" at the top of the window that opens up.

> **Ky3r0z said:**
> ```
May 11 17:24:19 arturo-laptop kernel: [ 8985.590418] WARNING: at /build/buildd/linux-2.6.24/drivers/usb/host/ehci-hcd.c:869 ehci_urb_dequeue()
May 11 17:24:19 arturo-laptop kernel: [ 8985.590433] Pid: 8375, comm: modprobe Tainted: P        2.6.24-16-generic #1
May 11 17:24:19 arturo-laptop kernel: [ 8985.590475]  [<f888ab3d>] ehci_urb_dequeue+0x14d/0x160 [ehci_hcd]
May 11 17:24:19 arturo-laptop kernel: [ 8985.590567]  [<f88a296f>] unlink1+0x6f/0xe0 [usbcore]
May 11 17:24:19 arturo-laptop kernel: [ 8985.590652]  [<f88a3d42>] usb_hcd_unlink_urb+0x12/0x30 [usbcore]
May 11 17:24:19 arturo-laptop kernel: [ 8985.590702]  [<f9bf7527>] wrap_cancel_irp+0x77/0xb0 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.590799]  [<f9bf4688>] IoCancelIrp+0x38/0x70 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.591073]  [<f9bf9fe4>] mp_init+0xa4/0x1f0 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.591183]  [<f9bfa209>] NdisDispatchPnp+0xd9/0xfc0 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.591280]  [update_curr+0x87/0x110] update_curr+0x87/0x110
May 11 17:24:19 arturo-laptop kernel: [ 8985.591383]  [finish_task_switch+0x8d/0x90] finish_task_switch+0x8d/0x90
May 11 17:24:19 arturo-laptop kernel: [ 8985.591417]  [parport_pc:schedule+0x20a/0x650] schedule+0x20a/0x600
May 11 17:24:19 arturo-laptop kernel: [ 8985.591444]  [ide_core:kunmap_atomic+0x3d/0x29e0] kunmap_atomic+0x3d/0xb0
May 11 17:24:19 arturo-laptop kernel: [ 8985.591476]  [get_page_from_freelist+0x27d/0x410] get_page_from_freelist+0x27d/0x410
May 11 17:24:19 arturo-laptop kernel: [ 8985.591517]  [<f9bf3521>] IoAllocateIrp+0x61/0x80 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.591597]  [mac80211:_spin_lock_bh+0x8/0x40] _spin_lock_bh+0x8/0x20
May 11 17:24:19 arturo-laptop kernel: [ 8985.591612]  [<f9bef604>] get_current_nt_thread+0x44/0x50 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.591692]  [<f9bf3815>] IofCallDriver+0x55/0xc0 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.591784]  [<f9bf885b>] IoSendIrpTopDev+0xbb/0x120 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.591918]  [<f9bf8bb0>] pnp_start_device+0x50/0xb0 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.592064]  [<f9bf8e4f>] wrap_pnp_start_device+0x23f/0x290 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.592205]  [<f9bf9126>] wrap_pnp_start_usb_device+0xa6/0xd0 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.592246]  [find_inode+0x31/0x60] find_inode+0x31/0x60
May 11 17:24:19 arturo-laptop kernel: [ 8985.592255]  [sysfs_ilookup_test+0x0/0x10] sysfs_ilookup_test+0x0/0x10
May 11 17:24:19 arturo-laptop kernel: [ 8985.592314]  [sysfs_addrm_finish+0x4b/0x1c0] sysfs_addrm_finish+0x4b/0x1c0
May 11 17:24:19 arturo-laptop kernel: [ 8985.592328]  [sysfs_add_one+0x44/0xe0] sysfs_add_one+0x44/0xe0
May 11 17:24:19 arturo-laptop kernel: [ 8985.592348]  [sysfs_addrm_start+0x6d/0xb0] sysfs_addrm_start+0x6d/0xb0
May 11 17:24:19 arturo-laptop kernel: [ 8985.592361]  [snd_pcm:mutex_lock+0x8/0x290] mutex_lock+0x8/0x20
May 11 17:24:19 arturo-laptop kernel: [ 8985.592381]  [<f88a682b>] usb_autopm_do_device+0x7b/0x100 [usbcore]
May 11 17:24:19 arturo-laptop kernel: [ 8985.592437]  [<f88a6397>] usb_match_one_id+0x27/0xb0 [usbcore]
May 11 17:24:19 arturo-laptop kernel: [ 8985.592521]  [<f88a75d9>] usb_probe_interface+0xb9/0x140 [usbcore]
May 11 17:24:19 arturo-laptop kernel: [ 8985.592612]  [driver_probe_device+0x88/0x190] driver_probe_device+0x88/0x190
May 11 17:24:19 arturo-laptop kernel: [ 8985.592621]  [scsi_mod:kobject_uevent_env+0xf0/0x2610] kobject_uevent_env+0xf0/0x3d0
May 11 17:24:19 arturo-laptop kernel: [ 8985.592672]  [__driver_attach+0x9e/0xa0] __driver_attach+0x9e/0xa0
May 11 17:24:19 arturo-laptop kernel: [ 8985.592698]  [pcmcia:bus_for_each_dev+0x3b/0x60] bus_for_each_dev+0x3b/0x60
May 11 17:24:19 arturo-laptop kernel: [ 8985.592748]  [usbcore:driver_attach+0x16/0x2b0] driver_attach+0x16/0x20
May 11 17:24:19 arturo-laptop kernel: [ 8985.592755]  [__driver_attach+0x0/0xa0] __driver_attach+0x0/0xa0
May 11 17:24:19 arturo-laptop kernel: [ 8985.592762]  [bus_add_driver+0x8a/0x1e0] bus_add_driver+0x8a/0x1e0
May 11 17:24:19 arturo-laptop kernel: [ 8985.592824]  [<f88a711e>] usb_register_driver+0x8e/0x110 [usbcore]
May 11 17:24:19 arturo-laptop kernel: [ 8985.592915]  [<f9be840c>] loader_init+0x9c/0x140 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.592958]  [<f9bf523f>] wrap_procfs_init+0x3f/0xb0 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.592999]  [<f9bf92f5>] wrapndis_init+0x45/0x50 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.593053]  [<f8be30b7>] wrapper_init+0xb7/0xc2 [ndiswrapper]
May 11 17:24:19 arturo-laptop kernel: [ 8985.593116]  [sys_init_module+0x126/0x19c0] sys_init_module+0x126/0x19c0
May 11 17:24:19 arturo-laptop kernel: [ 8985.593403]  [<c0164400>] disable_irq+0x0/0x30
May 11 17:24:19 arturo-laptop kernel: [ 8985.593504]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
May 11 17:24:19 arturo-laptop kernel: [ 8985.593622]  =======================
```

This looks very nasty. I highly recommend a reinstall, since it looks like you botched up something real good. Also, I'd like to see "ndiswrapper -l" output if you can get that before you reinstall.

> **ahmedh said:**
> Here's the tail end of my syslog, where I see a lot of network  related disablings and errors.

```
May 13 21:24:40 ahmed-desktop avahi-daemon[5317]: Network interface enumeration completed.
May 13 21:24:40 ahmed-desktop avahi-daemon[5317]: Registering HINFO record with values 'I686'/'LINUX'.
May 13 21:24:40 ahmed-desktop avahi-daemon[5317]: Server startup complete. Host name is ahmed-desktop.local. Local service cookie is 2729947728.
May 13 21:24:40 ahmed-desktop kernel: [   64.268899] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
May 13 21:24:40 ahmed-desktop kernel: [   64.268906] apm: disabled - APM is not SMP safe.
May 13 21:24:40 ahmed-desktop kernel: [   64.404344] ppdev: user-space parallel port driver
May 13 21:24:40 ahmed-desktop kernel: [   64.547133] audit(1210731880.394:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5360 profile="/usr/sbin/cupsd" namespace="default"
May 13 21:24:40 ahmed-desktop dhcdbd: Started up.
May 13 21:24:41 ahmed-desktop kernel: [   66.007567] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
May 13 21:24:42 ahmed-desktop kernel: [   66.207634] ivtv0: Encoder revision: 0x02060039
May 13 21:24:43 ahmed-desktop hal_lpadmin: add
May 13 21:24:43 ahmed-desktop hal_lpadmin: URIs: ['hp:/usb/photosmart_7700_series?serial=MY41C211CMQ0', 'usb://hp/photosmart%207700%20series?serial=MY41C211CMQ0', 'hal:///org/freedesktop/Hal/devices/usb_device_3f0_b402_MY41C211CMQ0_if0_printer_MY41C211CMQ0']
May 13 21:24:44 ahmed-desktop python: hp-makeuri[5563]: error: Device does not support fax.
May 13 21:24:44 ahmed-desktop hal_lpadmin: HPLIP Fax URIs: None
May 13 21:24:44 ahmed-desktop hal_lpadmin: Not adding printer: photosmart_7700_series already exists
May 13 21:24:45 ahmed-desktop kernel: [   69.499111] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
May 13 21:24:46 ahmed-desktop kernel: [   70.221732] eth0: link down
May 13 21:24:46 ahmed-desktop NetworkManager: <info>  eth0: Device is fully-supported using driver '8139too'. 
May 13 21:24:46 ahmed-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
May 13 21:24:46 ahmed-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
May 13 21:24:46 ahmed-desktop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
May 13 21:24:46 ahmed-desktop NetworkManager: <info>  Deactivating device eth0. 
May 13 21:24:46 ahmed-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
May 13 21:24:46 ahmed-desktop NetworkManager: <debug> [1210731886.112137] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_E616P3H'). 
May 13 21:24:46 ahmed-desktop hcid[5635]: Bluetooth HCI daemon
May 13 21:24:46 ahmed-desktop kernel: [   70.322163] Bluetooth: Core ver 2.11
May 13 21:24:46 ahmed-desktop kernel: [   70.323036] NET: Registered protocol family 31
May 13 21:24:46 ahmed-desktop kernel: [   70.323042] Bluetooth: HCI device and connection manager initialized
May 13 21:24:46 ahmed-desktop kernel: [   70.323048] Bluetooth: HCI socket layer initialized
May 13 21:24:46 ahmed-desktop hcid[5635]: Starting SDP server
May 13 21:24:46 ahmed-desktop kernel: [   70.380046] Bluetooth: L2CAP ver 2.9
May 13 21:24:46 ahmed-desktop kernel: [   70.380053] Bluetooth: L2CAP socket layer initialized
May 13 21:24:46 ahmed-desktop hcid[5635]: Created local server at unix:abstract=/var/run/dbus-FTb9xB8xCz,guid=0671ddaee2619735ad00c897482a4d6e
May 13 21:24:46 ahmed-desktop NetworkManager: <debug> [1210731886.250861] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
May 13 21:24:46 ahmed-desktop audio[5666]: Bluetooth Audio daemon
May 13 21:24:46 ahmed-desktop input[5667]: Bluetooth Input daemon
May 13 21:24:46 ahmed-desktop audio[5666]: Unix socket created: 5
May 13 21:24:46 ahmed-desktop audio[5666]: audio.conf: Key file does not have key 'Enable'
May 13 21:24:46 ahmed-desktop audio[5666]: audio.conf: Key file does not have key 'Disable'
May 13 21:24:46 ahmed-desktop kernel: [   70.476443] Bluetooth: RFCOMM socket layer initialized
May 13 21:24:46 ahmed-desktop kernel: [   70.477249] Bluetooth: RFCOMM TTY layer initialized
May 13 21:24:46 ahmed-desktop kernel: [   70.477255] Bluetooth: RFCOMM ver 1.8
May 13 21:24:46 ahmed-desktop input[5667]: Registered input manager path:/org/bluez/input
May 13 21:24:46 ahmed-desktop audio[5666]: add_service_record: got record id 0x10000
May 13 21:24:46 ahmed-desktop audio[5666]: audio.conf: Key file does not have key 'Disable'
May 13 21:24:46 ahmed-desktop audio[5666]: audio.conf: Key file does not have group 'A2DP'
May 13 21:24:46 ahmed-desktop last message repeated 3 times
May 13 21:24:46 ahmed-desktop audio[5666]: SEP 0x806d758 registered: type:0 codec:0 seid:1
May 13 21:24:46 ahmed-desktop audio[5666]: add_service_record: got record id 0x10001
May 13 21:24:46 ahmed-desktop audio[5666]: add_service_record: got record id 0x10002
May 13 21:24:46 ahmed-desktop audio[5666]: add_service_record: got record id 0x10003
May 13 21:24:46 ahmed-desktop audio[5666]: Registered manager path:/org/bluez/audio
May 13 21:24:48 ahmed-desktop ntpd[5753]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
May 13 21:24:48 ahmed-desktop ntpd[5756]: precision = 1.000 usec
May 13 21:24:48 ahmed-desktop anacron[5779]: Anacron 2.3 started on 2008-05-13
May 13 21:24:48 ahmed-desktop anacron[5779]: Normal exit (0 jobs run)
May 13 21:24:48 ahmed-desktop kernel: [   72.917914] NET: Registered protocol family 10
May 13 21:24:48 ahmed-desktop kernel: [   72.918270] lo: Disabled Privacy Extensions
May 13 21:24:48 ahmed-desktop kernel: [   72.920505] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 13 21:24:48 ahmed-desktop /usr/sbin/cron[5813]: (CRON) INFO (pidfile fd = 3)
May 13 21:24:48 ahmed-desktop /usr/sbin/cron[5817]: (CRON) STARTUP (fork ok)
May 13 21:24:48 ahmed-desktop kernel: [   72.958979] [drm] Initialized drm 1.1.0 20060810
May 13 21:24:48 ahmed-desktop /usr/sbin/cron[5817]: (CRON) INFO (Running @reboot jobs)
May 13 21:24:48 ahmed-desktop ntpd[5756]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
May 13 21:24:48 ahmed-desktop ntpd[5756]: Listening on interface #1 wildcard, ::#123 Disabled
May 13 21:24:48 ahmed-desktop ntpd[5756]: Listening on interface #2 lo, ::1#123 Enabled
May 13 21:24:48 ahmed-desktop kernel: [   72.970745] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
May 13 21:24:48 ahmed-desktop ntpd[5756]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
May 13 21:24:48 ahmed-desktop ntpd[5756]: kernel time sync status 0040
May 13 21:24:48 ahmed-desktop kernel: [   72.970758] PCI: Setting latency timer of device 0000:00:02.0 to 64
May 13 21:24:48 ahmed-desktop kernel: [   72.970864] [drm] Initialized i915 1.6.0 20060119 on minor 0
May 13 21:24:48 ahmed-desktop NetworkManager: <debug> [1210731888.840590] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2582_drm_i915_card0'). 
May 13 21:24:48 ahmed-desktop ntpd[5756]: frequency initialized 26.287 PPM from /var/lib/ntp/ntp.drift
May 13 21:24:50 ahmed-desktop ntpd_initres[5863]: host name not found: ntp.ubuntu.com
May 13 21:24:50 ahmed-desktop ntpd_initres[5863]: couldn't resolve `ntp.ubuntu.com', giving up on it
May 13 21:24:50 ahmed-desktop ntpd_initres[5863]: host name not found: libra.rice.edu
May 13 21:24:50 ahmed-desktop ntpd_initres[5863]: couldn't resolve `libra.rice.edu', giving up on it
May 13 21:25:12 ahmed-desktop hcid[5635]: Default passkey agent (:1.24, /org/bluez/passkey) registered
May 13 21:25:12 ahmed-desktop hcid[5635]: Default authorization agent (:1.24, /org/bluez/auth) registered
May 13 21:25:20 ahmed-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
May 13 21:26:00 ahmed-desktop kernel: [  144.416744] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
May 13 21:26:00 ahmed-desktop kernel: [  144.554729] usb 5-4: reset high speed USB device using ehci_hcd and address 3
May 13 21:26:00 ahmed-desktop kernel: [  144.707306] ndiswrapper: driver wusb54gs (Linksys,06/18/2004, 3.60.9.0) loaded
May 13 21:26:00 ahmed-desktop NetworkManager: <debug> [1210731960.834750] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_12_17_a7_5f_ab'). 
May 13 21:26:00 ahmed-desktop kernel: [  144.922670] wlan0: ethernet device 00:12:17:a7:5f:ab using NDIS driver: wusb54gs, version: 0x33c0d03, NDIS version: 0x501, vendor: 'Linksys Wireless-G USB Network Adapter with SpeedBooster', 13B1:000E.F.conf
May 13 21:26:00 ahmed-desktop kernel: [  144.957260] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
May 13 21:26:00 ahmed-desktop kernel: [  144.969285] usbcore: registered new interface driver ndiswrapper
May 13 21:26:00 ahmed-desktop NetworkManager: <info>  wlan0: Device is fully-supported using driver 'ndiswrapper'. 
May 13 21:26:00 ahmed-desktop NetworkManager: <info>  wlan0: driver does not support SSID scans (scan_capa 0x00). 
May 13 21:26:00 ahmed-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
May 13 21:26:00 ahmed-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
May 13 21:26:00 ahmed-desktop NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
May 13 21:26:00 ahmed-desktop NetworkManager: <info>  Deactivating device wlan0. 
May 13 21:26:00 ahmed-desktop NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
May 13 21:26:11 ahmed-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'wlan0'. 
May 13 21:26:11 ahmed-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
May 13 21:26:11 ahmed-desktop NetworkManager: <info>  Will activate connection 'wlan0/linksys'. 
May 13 21:26:11 ahmed-desktop NetworkManager: <info>  Device wlan0 activation scheduled... 
May 13 21:26:11 ahmed-desktop NetworkManager: <info>  Activation (wlan0) started... 
May 13 21:26:11 ahmed-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
May 13 21:26:11 ahmed-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
May 13 21:26:11 ahmed-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
May 13 21:26:11 ahmed-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
May 13 21:26:11 ahmed-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
May 13 21:26:11 ahmed-desktop NetworkManager: <info>  Activation (wlan0/wireless): access point 'linksys' is unencrypted, no key needed. 
May 13 21:26:12 ahmed-desktop NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
May 13 21:26:13 ahmed-desktop kernel: [  157.196990] NET: Registered protocol family 17
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  SUP: response was 'OK' 
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  SUP: response was 'OK' 
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  SUP: response was '0' 
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 6c696e6b737973' 
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  SUP: response was 'OK' 
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  SUP: response was 'OK' 
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  SUP: response was 'OK' 
May 13 21:26:13 ahmed-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
May 13 21:27:13 ahmed-desktop NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>60s), failing activation. 
May 13 21:27:13 ahmed-desktop NetworkManager: <info>  Activation (wlan0) failure scheduled... 
May 13 21:27:13 ahmed-desktop NetworkManager: <info>  Activation (wlan0) failed for access point (linksys) 
May 13 21:27:13 ahmed-desktop NetworkManager: <info>  Activation (wlan0) failed. 
May 13 21:27:13 ahmed-desktop NetworkManager: <info>  Deactivating device wlan0. 
May 13 21:27:13 ahmed-desktop NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
```

Thanks.

Looks like you are experiencing an unresolved bug:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/89092](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/89092)

That's one possibility. Another person with the "error setting ESSID to '' for device wlan0: Invalid argument" error message said that upgrading to Hardy fixed it for them.

Another person said that using NetworkManager did not work, but once they used System -> Administration -> Network everything worked.

Try these out, leaving the reinstall for last if you want.

> **Zahirn said:**
> Would it be possible for someone who got this "how to" to work, to post a video of themselves demonstrating the process? That would be GODLY. I've been trying to get the damned thing to work for ages, but have had no luck at all.

This might take me a while, but I still want to get around to it. It's a great idea. :)

> **chrisN_uk said:**
> Hello! Right, I've used this tutorial before and things have worked fine, but after a recent re-install, I'm having some trouble. Things seem to have been installed ok, but it didn't work so I tried this: [http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547)

And no luck.

```

$ ndiswrapper -l
wusb54g : driver installed
	device (5041:2234) present (alternate driver: p54usb)

/var/log/syslog
...
...
Jun  4 22:23:24 chris-desktop dhclient: Listening on LPF/wlan0/00:0f:66:73:26:bf
Jun  4 22:23:24 chris-desktop dhclient: Sending on   LPF/wlan0/00:0f:66:73:26:bf
Jun  4 22:23:24 chris-desktop dhclient: Sending on   Socket/fallback
Jun  4 22:23:24 chris-desktop avahi-daemon[4910]: Registering new address record for fe80::20f:66ff:fe73:26bf on wlan0.*.
Jun  4 22:23:28 chris-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jun  4 22:23:31 chris-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jun  4 22:23:33 chris-desktop kernel: [  274.486951] wlan0: no IPv6 routers present
Jun  4 22:23:34 chris-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jun  4 22:23:37 chris-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Jun  4 22:23:51 chris-desktop last message repeated 2 times
Jun  4 22:23:58 chris-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
Jun  4 22:23:59 chris-desktop dhclient: No DHCPOFFERS received.
Jun  4 22:23:59 chris-desktop dhclient: No working leases in persistent database - sleeping.
Jun  4 22:23:59 chris-desktop avahi-autoipd(wlan0)[5961]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Jun  4 22:23:59 chris-desktop avahi-autoipd(wlan0)[5961]: Successfully called chroot().
Jun  4 22:23:59 chris-desktop avahi-autoipd(wlan0)[5961]: Successfully dropped root privileges.
Jun  4 22:23:59 chris-desktop avahi-autoipd(wlan0)[5961]: Starting with address 169.254.6.136
Jun  4 22:24:04 chris-desktop avahi-autoipd(wlan0)[5961]: Callout BIND, address 169.254.6.136 on interface wlan0
Jun  4 22:24:04 chris-desktop avahi-daemon[4910]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.6.136.
Jun  4 22:24:04 chris-desktop avahi-daemon[4910]: New relevant interface wlan0.IPv4 for mDNS.
Jun  4 22:24:04 chris-desktop avahi-daemon[4910]: Registering new address record for 169.254.6.136 on wlan0.IPv4.
Jun  4 22:24:08 chris-desktop avahi-autoipd(wlan0)[5961]: Successfully claimed IP address 169.254.6.136
Jun  4 22:24:10 chris-desktop ntpdate[6022]: adjust time server 91.189.94.4 offset -0.001912 sec
Jun  4 22:26:58 chris-desktop kernel: [  582.868579] eth0: link down.
Jun  4 22:26:58 chris-desktop NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Jun  4 22:26:58 chris-desktop NetworkManager: <info>  Deactivating device eth0. 
Jun  4 22:26:58 chris-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5397
Jun  4 22:26:58 chris-desktop dhclient: killed old client process, removed PID file
Jun  4 22:26:58 chris-desktop dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Jun  4 22:26:58 chris-desktop avahi-daemon[4910]: Withdrawing address record for 192.168.1.15 on eth0.
Jun  4 22:26:58 chris-desktop avahi-daemon[4910]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.15.
Jun  4 22:26:58 chris-desktop avahi-daemon[4910]: Interface eth0.IPv4 no longer relevant for mDNS.
Jun  4 22:26:58 chris-desktop dhcdbd: dhco_parse_option_settings: bad option setting: old_server_name =  
Jun  4 22:26:59 chris-desktop avahi-daemon[4910]: Withdrawing address record for fe80::213:8fff:feac:f68c on eth0.
Jun  4 22:26:59 chris-desktop NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Jun  4 22:26:59 chris-desktop NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Jun  4 22:27:34 chris-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Jun  4 22:27:39 chris-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Jun  4 22:27:51 chris-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Jun  4 22:28:03 chris-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
Jun  4 22:28:05 chris-desktop dhclient: No DHCPOFFERS received.
Jun  4 22:28:05 chris-desktop dhclient: No working leases in persistent database - sleeping.
Jun  4 22:29:19 chris-desktop gdm[5245]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Jun  4 22:29:31 chris-desktop pulseaudio[6330]: pid.c: Stale PID file, overwriting.
Jun  4 22:29:34 chris-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Jun  4 22:29:34 chris-desktop NetworkManager: <info>  Updating VPN Connections... 


```

Cheers...

You are using a different device here. Note the numbers ndiswrapper reports: "(5041:2234)". These do not match the numbers others normally get. These numbers represent the WUSB54G device, which is, believe it or not, different than the WUSB54GS. That might explain some of your issues.

This HOWTO should work a lot better for you:
[http://blog.eksfiles.net/2008/01/05/using-the-linksys-wusb54g-v1-or-v4-with-ubuntu-gutsy/](http://blog.eksfiles.net/2008/01/05/using-the-linksys-wusb54g-v1-or-v4-with-ubuntu-gutsy/)

It should easily work with Hardy as well. Not much changes that quickly in the wireless world. ;)

---

### Post by art_killer on 2008-07-20
[http://ubuntuforums.org/showthread.php?t=432001&page=2](http://ubuntuforums.org/showthread.php?t=432001&page=2)

Method 1
- [http://www.jooz.net/rndis/](http://www.jooz.net/rndis/)
- Download the rndis wlan snapshot and install it as it tells
you
restart and it works.
- You have to install it again if you either install any
kernel
updates.

try this one only way which works on my WUSB54GS ver 2.1 on Ubuntu 8.04 on the 2.6.24-19-generic:)

---

### Post by 44tr on 2008-07-20
I've been trying for days now, reading every thread I can find, to get my WUSB54GS running on Ubuntu 8.04.  Communicated briefly with javaJake; he was nice enough but couldn't devote the time to troubleshoot.  I have gotten all the way through the tutorial with 'ndiswrapper -l' saying driver is loaded and device is present.  Put in the custom udev rule perfectly, but still no power light on device (flickers on briefly when plugged in).  I did get some 'bad CDC descriptors' errors in syslog, but lots of posts in this thread say this is no big deal.  Can anybody walk me through the troubleshooting to get me up on the net? I'm setting up my son's machine and I'm just too much of a linux newbie to figure it out.  I saw the last post which suggests the below:

> [http://ubuntuforums.org/showthread.php?t=432001&page=2](http://ubuntuforums.org/showthread.php?t=432001&page=2)

Method 1
- [http://www.jooz.net/rndis/](http://www.jooz.net/rndis/)
- Download the rndis wlan snapshot and install it as it tells
you
restart and it works.
- You have to install it again if you either install any
kernel
updates.

try this one only way which works on my WUSB54GS ver 2.1 on Ubuntu 8.04 on the 2.6.24-19-generic

If this is a good thing to try, how do I undo all the stuff I already did?  Yet another clean install?  Is this the way to go?

Thanks in advance.:(

---

### Post by 44tr on 2008-07-21
OK, I went ahead and tried 'Method 1' from jooz.net and it worked perfectly.  Was up in half hour; would have been faster if I knew how to run a script. :-)

for the WUSB54GS v2.1, this is the way to go on mine.

Thanks.

---

### Post by xFLHCx on 2008-08-03
First time posting

I installed Ubuntu 8.04 about a week ago and immediately started trying to install my WUSB54G v1. I've read pages and pages of different information then found this.  I finally decided that I'm absolutely stuck after days of research and decided to post.

I have the 64 bit version, from what i read it says that this howto doesnt support the 64bit.  is that the same with the wireless adapter in general?  Am i pretty much screwed with the 64 bit version?

I tried following the steps in this howto, but using the 64 bit drivers i found for my adapter.  

i tried the initial command and it said build-essential wasnt found

I couldnt even get past the ndiswrapper installation even with a completely fresh install of ubuntu.  

after changing into the ndiswrapper directory and running make, it goes into the utils directory adn runs loadndisdriver.c, every command after this is practically an error message saying things arent found and commands arent allowed. its lines and lines of this

i tried ignoring it, did the sudo make install, then checked to see if ndiswrwapper was installed. it wasnt, it told me to run a command to get ndiswrapper-common which wasnt found in my packages.



ANY tips whatsoever?

---

### Post by julain124 on 2008-08-16
I tried installing using this guide, everything went flawlessly, till the last part.. for the output I get:

```
Aug 16 09:28:12 recklezz-desktop kernel: [   12.422090] Memory: 1480556k/1506240k available (2177k kernel code, 24464k reserved, 1006k data, 368k init, 588736k highmem)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.422097] virtual kernel memory layout:
Aug 16 09:28:12 recklezz-desktop kernel: [   12.422098]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.422099]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.422100]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.422101]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.422102]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.422103]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.422104]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.422107] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug 16 09:28:12 recklezz-desktop kernel: [   12.422144] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502090] Calibrating delay using timer specific routine.. 4413.22 BogoMIPS (lpj=8826458)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502115] Security Framework initialized
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502122] SELinux:  Disabled at boot.
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502136] AppArmor: AppArmor initialized
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502140] Failure registering capabilities with primary security module.
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502148] Mount-cache hash table entries: 512
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502259] Initializing cgroup subsys ns
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502263] Initializing cgroup subsys cpuacct
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502273] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001 00000000
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502280] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502282] CPU: L2 Cache: 512K (64 bytes/line)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502285] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001 00000000
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502293] Compat vDSO mapped to ffffe000.
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502304] Checking 'hlt' instruction... OK.
Aug 16 09:28:12 recklezz-desktop kernel: [   12.518357] SMP alternatives: switching to UP code
Aug 16 09:28:12 recklezz-desktop kernel: [   12.519373] Freeing SMP alternatives: 11k freed
Aug 16 09:28:12 recklezz-desktop kernel: [   12.519475] Early unpacking initramfs... done
Aug 16 09:28:12 recklezz-desktop kernel: [   12.810005] ACPI: Core revision 20070126
Aug 16 09:28:12 recklezz-desktop kernel: [   12.810071] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 16 09:28:12 recklezz-desktop kernel: [   12.814874] CPU0: AMD Athlon(tm) 64 Processor 3500+ stepping 02
Aug 16 09:28:12 recklezz-desktop kernel: [   12.814892] Total of 1 processors activated (4413.22 BogoMIPS).
Aug 16 09:28:12 recklezz-desktop kernel: [   12.815189] ENABLING IO-APIC IRQs
Aug 16 09:28:12 recklezz-desktop kernel: [   12.815420] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Aug 16 09:28:12 recklezz-desktop kernel: [   12.961687] Brought up 1 CPUs
Aug 16 09:28:12 recklezz-desktop kernel: [   12.961734] CPU0 attaching sched-domain:
Aug 16 09:28:12 recklezz-desktop kernel: [   12.961736]  domain 0: span 01
Aug 16 09:28:12 recklezz-desktop kernel: [   12.961738]   groups: 01
Aug 16 09:28:12 recklezz-desktop kernel: [   12.961871] net_namespace: 64 bytes
Aug 16 09:28:12 recklezz-desktop kernel: [   12.961877] Booting paravirtualized kernel on bare hardware
Aug 16 09:28:12 recklezz-desktop kernel: [   12.962258] Time: 16:27:48  Date: 08/16/08
Aug 16 09:28:12 recklezz-desktop kernel: [   12.962277] NET: Registered protocol family 16
Aug 16 09:28:12 recklezz-desktop kernel: [   12.962414] EISA bus registered
Aug 16 09:28:12 recklezz-desktop kernel: [   12.962440] ACPI: bus type pci registered
Aug 16 09:28:12 recklezz-desktop kernel: [   12.968885] PCI: PCI BIOS revision 3.00 entry at 0xf2060, last bus=3
Aug 16 09:28:12 recklezz-desktop kernel: [   12.968887] PCI: Using configuration type 1
Aug 16 09:28:12 recklezz-desktop kernel: [   12.968895] Setting up standard PCI resources
Aug 16 09:28:12 recklezz-desktop kernel: [   12.972636] ACPI: EC: Look up EC in DSDT
Aug 16 09:28:12 recklezz-desktop kernel: [   12.981227] ACPI: Interpreter enabled
Aug 16 09:28:12 recklezz-desktop kernel: [   12.981229] ACPI: (supports S0 S1 S3 S4 S5)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.981241] ACPI: Using IOAPIC for interrupt routing
Aug 16 09:28:12 recklezz-desktop kernel: [   12.991227] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.992143] PCI: Transparent bridge - 0000:00:10.0
Aug 16 09:28:12 recklezz-desktop kernel: [   12.992158] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 16 09:28:12 recklezz-desktop kernel: [   12.992472] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Aug 16 09:28:12 recklezz-desktop kernel: [   13.098102] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.098329] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.098551] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.098772] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.098993] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.099215] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.099437] ACPI: PCI Interrupt Link [LNK7] (IRQs *5 7 9 10 11 14 15)
Aug 16 09:28:12 recklezz-desktop kernel: [   13.099664] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.099885] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.100107] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.100329] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 *11 14 15)
Aug 16 09:28:12 recklezz-desktop kernel: [   13.100550] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.100773] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 *7 9 10 11 14 15)
Aug 16 09:28:12 recklezz-desktop kernel: [   13.100994] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.101216] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.101438] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.101663] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.101886] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.102109] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
Aug 16 09:28:12 recklezz-desktop kernel: [   13.102340] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
Aug 16 09:28:12 recklezz-desktop kernel: [   13.102592] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.102837] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.103079] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.103320] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.103562] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.103803] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.104045] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0
Aug 16 09:28:12 recklezz-desktop kernel: [   13.104286] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.104528] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.104770] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.105013] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
Aug 16 09:28:12 recklezz-desktop kernel: [   13.105254] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.105497] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.105744] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
Aug 16 09:28:12 recklezz-desktop kernel: [   13.105986] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.106229] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.106474] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.106717] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.106960] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.107202] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
Aug 16 09:28:12 recklezz-desktop kernel: [   13.107445] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
Aug 16 09:28:12 recklezz-desktop kernel: [   13.107570] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug 16 09:28:12 recklezz-desktop kernel: [   13.107593] pnp: PnP ACPI init
Aug 16 09:28:12 recklezz-desktop kernel: [   13.107599] ACPI: bus type pnp registered
Aug 16 09:28:12 recklezz-desktop kernel: [   13.112593] pnpacpi: exceeded the max number of mem resources: 12
Aug 16 09:28:12 recklezz-desktop kernel: [   13.112646] pnp: PnP ACPI: found 11 devices
Aug 16 09:28:12 recklezz-desktop kernel: [   13.112648] ACPI: ACPI bus type pnp unregistered
Aug 16 09:28:12 recklezz-desktop kernel: [   13.112651] PnPBIOS: Disabled by ACPI PNP
Aug 16 09:28:12 recklezz-desktop kernel: [   13.112824] PCI: Using ACPI for IRQ routing
Aug 16 09:28:12 recklezz-desktop kernel: [   13.112828] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug 16 09:28:12 recklezz-desktop kernel: [   13.189433] NET: Registered protocol family 8
Aug 16 09:28:12 recklezz-desktop kernel: [   13.189435] NET: Registered protocol family 20
Aug 16 09:28:12 recklezz-desktop kernel: [   13.189490] AppArmor: AppArmor Filesystem Enabled
Aug 16 09:28:12 recklezz-desktop kernel: [   13.193424] Time: tsc clocksource has been installed.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201442] system 00:01: ioport range 0x4000-0x407f has been reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201445] system 00:01: ioport range 0x4080-0x40ff has been reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201447] system 00:01: ioport range 0x4400-0x447f has been reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201450] system 00:01: ioport range 0x4480-0x44ff has been reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201452] system 00:01: ioport range 0x4800-0x487f has been reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201454] system 00:01: ioport range 0x4880-0x48ff has been reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201456] system 00:01: ioport range 0x2000-0x207f has been reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201459] system 00:01: ioport range 0x2080-0x20ff has been reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201461] system 00:01: iomem range 0x5c000000-0x5fffffff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201466] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201468] system 00:02: ioport range 0x800-0x87f has been reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201474] system 00:09: iomem range 0xf0000000-0xf3ffffff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201479] system 00:0a: iomem range 0xcec00-0xcffff has been reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201481] system 00:0a: iomem range 0xf0000-0xf7fff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201483] system 00:0a: iomem range 0xf8000-0xfbfff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201486] system 00:0a: iomem range 0xfc000-0xfffff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201488] system 00:0a: iomem range 0x5bef0000-0x5befffff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201490] system 00:0a: iomem range 0xffff0000-0xffffffff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201493] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201495] system 00:0a: iomem range 0x100000-0x5beeffff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201497] system 00:0a: iomem range 0x5bf00000-0x5fefffff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201500] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201502] system 00:0a: iomem range 0xfee00000-0xfeefffff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201505] system 00:0a: iomem range 0xfefff000-0xfeffffff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231785] PCI: Bridge: 0000:00:02.0
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231787]   IO window: e000-efff
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231790]   MEM window: fde00000-fdefffff
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231792]   PREFETCH window: fdb00000-fdbfffff
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231794] PCI: Bridge: 0000:00:04.0
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231795]   IO window: c000-cfff
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231798]   MEM window: fda00000-fdafffff
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231800]   PREFETCH window: fd900000-fd9fffff
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231802] PCI: Bridge: 0000:00:10.0
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231804]   IO window: d000-dfff
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231807]   MEM window: fdd00000-fddfffff
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231809]   PREFETCH window: fdc00000-fdcfffff
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231821] PCI: Setting latency timer of device 0000:00:02.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231827] PCI: Setting latency timer of device 0000:00:04.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231833] PCI: Setting latency timer of device 0000:00:10.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231842] NET: Registered protocol family 2
Aug 16 09:28:12 recklezz-desktop kernel: [   13.269417] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 16 09:28:12 recklezz-desktop kernel: [   13.269689] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 16 09:28:12 recklezz-desktop kernel: [   13.270658] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 16 09:28:12 recklezz-desktop kernel: [   13.271178] TCP: Hash tables configured (established 131072 bind 65536)
Aug 16 09:28:12 recklezz-desktop kernel: [   13.271180] TCP reno registered
Aug 16 09:28:12 recklezz-desktop kernel: [   13.281459] checking if image is initramfs... it is
Aug 16 09:28:12 recklezz-desktop kernel: [   13.732901] Switched to high resolution mode on CPU 0
Aug 16 09:28:12 recklezz-desktop kernel: [   13.840987] Freeing initrd memory: 7735k freed
Aug 16 09:28:12 recklezz-desktop kernel: [   13.841484] audit: initializing netlink socket (disabled)
Aug 16 09:28:12 recklezz-desktop kernel: [   13.841497] audit(1218904068.320:1): initialized
Aug 16 09:28:12 recklezz-desktop kernel: [   13.841632] highmem bounce pool size: 64 pages
Aug 16 09:28:12 recklezz-desktop kernel: [   13.842930] VFS: Disk quotas dquot_6.5.1
Aug 16 09:28:12 recklezz-desktop kernel: [   13.842978] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843081] io scheduler noop registered
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843083] io scheduler anticipatory registered
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843085] io scheduler deadline registered
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843092] io scheduler cfq registered (default)
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843105] pci 0000:00:00.0: Enabling HT MSI Mapping
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843131] pci 0000:00:02.0: Enabling HT MSI Mapping
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843138] pci 0000:00:04.0: Enabling HT MSI Mapping
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843145] Boot video device is 0000:00:05.0
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843165] pci 0000:00:09.0: Enabling HT MSI Mapping
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843214] pci 0000:00:0e.0: Enabling HT MSI Mapping
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843224] pci 0000:00:0f.0: Enabling HT MSI Mapping
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843231] pci 0000:00:10.0: Enabling HT MSI Mapping
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843242] pci 0000:00:10.1: Enabling HT MSI Mapping
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843334] PCI: Setting latency timer of device 0000:00:02.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843353] assign_interrupt_mode Found MSI capability
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843371] Allocate Port Service[0000:00:02.0:pcie00]
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843421] PCI: Setting latency timer of device 0000:00:04.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843439] assign_interrupt_mode Found MSI capability
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843453] Allocate Port Service[0000:00:04.0:pcie00]
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843610] isapnp: Scanning for PnP cards...
Aug 16 09:28:12 recklezz-desktop kernel: [   14.196382] isapnp: No Plug & Play device found
Aug 16 09:28:12 recklezz-desktop kernel: [   14.217790] Real Time Clock Driver v1.12ac
Aug 16 09:28:12 recklezz-desktop kernel: [   14.217880] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug 16 09:28:12 recklezz-desktop kernel: [   14.218688] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug 16 09:28:12 recklezz-desktop kernel: [   14.218742] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug 16 09:28:12 recklezz-desktop kernel: [   14.218808] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Aug 16 09:28:12 recklezz-desktop kernel: [   14.221423] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 16 09:28:12 recklezz-desktop kernel: [   14.221427] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228376] mice: PS/2 mouse device common for all mice
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228463] EISA: Probing bus 0 at eisa.0
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228471] Cannot allocate resource for EISA slot 2
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228475] Cannot allocate resource for EISA slot 4
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228487] EISA: Detected 0 cards.
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228490] cpuidle: using governor ladder
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228492] cpuidle: using governor menu
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228565] NET: Registered protocol family 1
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228585] Using IPI No-Shortcut mode
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228612] registered taskstats version 1
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228720]   Magic number: 4:836:489
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228897] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228899] EDD information not available.
Aug 16 09:28:12 recklezz-desktop kernel: [   14.229116] Freeing unused kernel memory: 368k freed
Aug 16 09:28:12 recklezz-desktop kernel: [   14.260259] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Aug 16 09:28:12 recklezz-desktop kernel: [   15.436803] fuse init (API version 7.9)
Aug 16 09:28:12 recklezz-desktop kernel: [   15.450899] ACPI: Fan [FAN] (on)
Aug 16 09:28:12 recklezz-desktop kernel: [   15.456061] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 16 09:28:12 recklezz-desktop kernel: [   15.459173] ACPI: Thermal Zone [THRM] (40 C)
Aug 16 09:28:12 recklezz-desktop kernel: [   16.385967] usbcore: registered new interface driver usbfs
Aug 16 09:28:12 recklezz-desktop kernel: [   16.385989] usbcore: registered new interface driver hub
Aug 16 09:28:12 recklezz-desktop kernel: [   16.393921] usbcore: registered new device driver usb
Aug 16 09:28:12 recklezz-desktop kernel: [   16.399779] SCSI subsystem initialized
Aug 16 09:28:12 recklezz-desktop kernel: [   16.425920] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 16 09:28:12 recklezz-desktop kernel: [   16.426377] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
Aug 16 09:28:12 recklezz-desktop kernel: [   16.426387] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
Aug 16 09:28:12 recklezz-desktop kernel: [   16.426399] PCI: Setting latency timer of device 0000:00:0b.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   16.426402] ohci_hcd 0000:00:0b.0: OHCI Host Controller
Aug 16 09:28:12 recklezz-desktop kernel: [   16.426659] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
Aug 16 09:28:12 recklezz-desktop kernel: [   16.426676] ohci_hcd 0000:00:0b.0: irq 16, io mem 0xfe02f000
Aug 16 09:28:12 recklezz-desktop kernel: [   16.457150] libata version 3.00 loaded.
Aug 16 09:28:12 recklezz-desktop kernel: [   16.483910] usb usb1: configuration #1 chosen from 1 choice
Aug 16 09:28:12 recklezz-desktop kernel: [   16.483930] hub 1-0:1.0: USB hub found
Aug 16 09:28:12 recklezz-desktop kernel: [   16.483938] hub 1-0:1.0: 8 ports detected
Aug 16 09:28:12 recklezz-desktop kernel: [   16.586285] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
Aug 16 09:28:12 recklezz-desktop kernel: [   16.586297] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 17
Aug 16 09:28:12 recklezz-desktop kernel: [   16.586307] PCI: Setting latency timer of device 0000:00:0b.1 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   16.586310] ehci_hcd 0000:00:0b.1: EHCI Host Controller
Aug 16 09:28:12 recklezz-desktop kernel: [   16.586331] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
Aug 16 09:28:12 recklezz-desktop kernel: [   16.586357] ehci_hcd 0000:00:0b.1: debug port 1
Aug 16 09:28:12 recklezz-desktop kernel: [   16.586361] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
Aug 16 09:28:12 recklezz-desktop kernel: [   16.586373] ehci_hcd 0000:00:0b.1: irq 17, io mem 0xfe02e000
Aug 16 09:28:12 recklezz-desktop kernel: [   16.597683] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 16 09:28:12 recklezz-desktop kernel: [   16.597786] usb usb2: configuration #1 chosen from 1 choice
Aug 16 09:28:12 recklezz-desktop kernel: [   16.597805] hub 2-0:1.0: USB hub found
Aug 16 09:28:12 recklezz-desktop kernel: [   16.597810] hub 2-0:1.0: 8 ports detected
Aug 16 09:28:12 recklezz-desktop kernel: [   16.701753] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Aug 16 09:28:12 recklezz-desktop kernel: [   16.702180] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
Aug 16 09:28:12 recklezz-desktop kernel: [   16.702189] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 21 (level, low) -> IRQ 18
Aug 16 09:28:12 recklezz-desktop kernel: [   16.702195] PCI: Setting latency timer of device 0000:00:14.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   17.113109] usb 2-2: new high speed USB device using ehci_hcd and address 2
Aug 16 09:28:12 recklezz-desktop kernel: [   17.221388] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x20 @ 13, addr 00:17:31:cd:61:90
Aug 16 09:28:12 recklezz-desktop kernel: [   17.221392] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
Aug 16 09:28:12 recklezz-desktop kernel: [   17.221704] PCI: Setting latency timer of device 0000:00:0d.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   17.222126] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
Aug 16 09:28:12 recklezz-desktop kernel: [   17.222136] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 19
Aug 16 09:28:12 recklezz-desktop kernel: [   17.222153] PCI: Setting latency timer of device 0000:00:0e.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   17.222159] ACPI: PCI interrupt for device 0000:00:0e.0 disabled
Aug 16 09:28:12 recklezz-desktop kernel: [   17.222515] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
Aug 16 09:28:12 recklezz-desktop kernel: [   17.222517] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 16
Aug 16 09:28:12 recklezz-desktop kernel: [   17.222533] PCI: Setting latency timer of device 0000:00:0f.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   17.222539] ACPI: PCI interrupt for device 0000:00:0f.0 disabled
Aug 16 09:28:12 recklezz-desktop kernel: [   17.225928] pata_amd 0000:00:0d.0: version 0.3.10
Aug 16 09:28:12 recklezz-desktop kernel: [   17.225976] PCI: Setting latency timer of device 0000:00:0d.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   17.229987] scsi0 : pata_amd
Aug 16 09:28:12 recklezz-desktop kernel: [   17.232370] scsi1 : pata_amd
Aug 16 09:28:12 recklezz-desktop kernel: [   17.233045] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfd00 irq 14
Aug 16 09:28:12 recklezz-desktop kernel: [   17.233048] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfd08 irq 15
Aug 16 09:28:12 recklezz-desktop kernel: [   17.246652] usb 2-2: configuration #1 chosen from 1 choice
Aug 16 09:28:12 recklezz-desktop kernel: [   17.788364] usb 1-8: new full speed USB device using ohci_hcd and address 2
Aug 16 09:28:12 recklezz-desktop kernel: [   17.920511] ata2.00: ATAPI: TSSTcorpCD/DVDW TS-H552L, 0614, max UDMA/33
Aug 16 09:28:12 recklezz-desktop kernel: [   17.920528] ata2.01: ATAPI: Hewlett-Packard DVD Writer 300, 1.25, max UDMA/33
Aug 16 09:28:12 recklezz-desktop kernel: [   18.003325] usb 1-8: configuration #1 chosen from 1 choice
Aug 16 09:28:12 recklezz-desktop kernel: [   18.017953] usbcore: registered new interface driver libusual
Aug 16 09:28:12 recklezz-desktop kernel: [   18.023093] Initializing USB Mass Storage driver...
Aug 16 09:28:12 recklezz-desktop kernel: [   18.023971] scsi2 : SCSI emulation for USB Mass Storage devices
Aug 16 09:28:12 recklezz-desktop kernel: [   18.024662] usbcore: registered new interface driver usb-storage
Aug 16 09:28:12 recklezz-desktop kernel: [   18.024666] USB Mass Storage support registered.
Aug 16 09:28:12 recklezz-desktop kernel: [   18.024751] usb-storage: device found at 2
Aug 16 09:28:12 recklezz-desktop kernel: [   18.024752] usb-storage: waiting for device to settle before scanning
Aug 16 09:28:12 recklezz-desktop kernel: [   18.132223] ata2.00: configured for UDMA/33
Aug 16 09:28:12 recklezz-desktop kernel: [   18.304144] ata2.01: configured for UDMA/33
Aug 16 09:28:12 recklezz-desktop kernel: [   18.305153] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-H552L 0614 PQ: 0 ANSI: 5
Aug 16 09:28:12 recklezz-desktop kernel: [   18.307665] scsi 1:0:1:0: CD-ROM            HP       DVD Writer 300n  1.25 PQ: 0 ANSI: 5
Aug 16 09:28:12 recklezz-desktop kernel: [   18.309996] sata_nv 0000:00:0e.0: version 3.5
Aug 16 09:28:12 recklezz-desktop kernel: [   18.310010] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 19
Aug 16 09:28:12 recklezz-desktop kernel: [   18.310049] PCI: Setting latency timer of device 0000:00:0e.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   18.311376] scsi3 : sata_nv
Aug 16 09:28:12 recklezz-desktop kernel: [   18.311566] scsi4 : sata_nv
Aug 16 09:28:12 recklezz-desktop kernel: [   18.311744] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xf800 irq 19
Aug 16 09:28:12 recklezz-desktop kernel: [   18.311747] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xf808 irq 19
Aug 16 09:28:12 recklezz-desktop kernel: [   18.775294] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Aug 16 09:28:12 recklezz-desktop kernel: [   18.783429] ata3.00: ATA-7: ST3200827AS, 3.AHH, max UDMA/100
Aug 16 09:28:12 recklezz-desktop kernel: [   18.783431] ata3.00: 390721968 sectors, multi 1: LBA48 NCQ (depth 0/32)
Aug 16 09:28:12 recklezz-desktop kernel: [   18.799411] ata3.00: configured for UDMA/100
Aug 16 09:28:12 recklezz-desktop kernel: [   19.110912] ata4: SATA link down (SStatus 0 SControl 310)
Aug 16 09:28:12 recklezz-desktop kernel: [   19.121426] scsi 3:0:0:0: Direct-Access     ATA      ST3200827AS      3.AH PQ: 0 ANSI: 5
Aug 16 09:28:12 recklezz-desktop kernel: [   19.121490] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 16
Aug 16 09:28:12 recklezz-desktop kernel: [   19.121529] PCI: Setting latency timer of device 0000:00:0f.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   19.121831] scsi5 : sata_nv
Aug 16 09:28:12 recklezz-desktop kernel: [   19.121949] scsi6 : sata_nv
Aug 16 09:28:12 recklezz-desktop kernel: [   19.122125] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xf300 irq 16
Aug 16 09:28:12 recklezz-desktop kernel: [   19.122128] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xf308 irq 16
Aug 16 09:28:12 recklezz-desktop kernel: [   19.430561] ata5: SATA link down (SStatus 0 SControl 310)
Aug 16 09:28:12 recklezz-desktop kernel: [   19.750209] ata6: SATA link down (SStatus 0 SControl 310)
Aug 16 09:28:12 recklezz-desktop kernel: [   19.772531] Driver 'sr' needs updating - please use bus_type methods
Aug 16 09:28:12 recklezz-desktop kernel: [   19.779661] Driver 'sd' needs updating - please use bus_type methods
Aug 16 09:28:12 recklezz-desktop kernel: [   19.784142] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Aug 16 09:28:12 recklezz-desktop kernel: [   19.784147] Uniform CD-ROM driver Revision: 3.20
Aug 16 09:28:12 recklezz-desktop kernel: [   19.784189] sr 1:0:0:0: Attached scsi CD-ROM sr0
Aug 16 09:28:12 recklezz-desktop kernel: [   19.789500] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Aug 16 09:28:12 recklezz-desktop kernel: [   19.789529] sr 1:0:1:0: Attached scsi CD-ROM sr1
Aug 16 09:28:12 recklezz-desktop kernel: [   19.789872] sd 3:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
Aug 16 09:28:12 recklezz-desktop kernel: [   19.793519] sd 3:0:0:0: [sda] Write Protect is off
Aug 16 09:28:12 recklezz-desktop kernel: [   19.793524] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 16 09:28:12 recklezz-desktop kernel: [   19.796087] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 16 09:28:12 recklezz-desktop kernel: [   19.796143] sd 3:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
Aug 16 09:28:12 recklezz-desktop kernel: [   19.796151] sd 3:0:0:0: [sda] Write Protect is off
Aug 16 09:28:12 recklezz-desktop kernel: [   19.796154] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 16 09:28:12 recklezz-desktop kernel: [   19.796165] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 16 09:28:12 recklezz-desktop kernel: [   19.796168]  sda:<5>sr 1:0:0:0: Attached scsi generic sg0 type 5
Aug 16 09:28:12 recklezz-desktop kernel: [   19.797095] sr 1:0:1:0: Attached scsi generic sg1 type 5
Aug 16 09:28:12 recklezz-desktop kernel: [   19.797109] sd 3:0:0:0: Attached scsi generic sg2 type 0
Aug 16 09:28:12 recklezz-desktop kernel: [   19.816736]  sda1 sda2 < sda5 >
Aug 16 09:28:12 recklezz-desktop kernel: [   19.841101] sd 3:0:0:0: [sda] Attached SCSI disk
Aug 16 09:28:12 recklezz-desktop kernel: [   20.113089] Attempting manual resume
Aug 16 09:28:12 recklezz-desktop kernel: [   20.113093] swsusp: Resume From Partition 8:5
Aug 16 09:28:12 recklezz-desktop kernel: [   20.113095] PM: Checking swsusp image.
Aug 16 09:28:12 recklezz-desktop kernel: [   20.113251] PM: Resume from disk failed.
Aug 16 09:28:12 recklezz-desktop kernel: [   20.156973] kjournald starting.  Commit interval 5 seconds
Aug 16 09:28:12 recklezz-desktop kernel: [   20.156986] EXT3-fs: mounted filesystem with ordered data mode.
Aug 16 09:28:12 recklezz-desktop kernel: [   23.020051] usb-storage: device scan complete
Aug 16 09:28:12 recklezz-desktop kernel: [   23.027028] scsi 2:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
Aug 16 09:28:12 recklezz-desktop kernel: [   23.034019] scsi 2:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
Aug 16 09:28:12 recklezz-desktop kernel: [   23.041012] scsi 2:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
Aug 16 09:28:12 recklezz-desktop kernel: [   23.048005] scsi 2:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
Aug 16 09:28:12 recklezz-desktop kernel: [   23.059013] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Aug 16 09:28:12 recklezz-desktop kernel: [   23.059036] sd 2:0:0:0: Attached scsi generic sg3 type 0
Aug 16 09:28:12 recklezz-desktop kernel: [   23.069994] sd 2:0:0:1: [sdc] Attached SCSI removable disk
Aug 16 09:28:12 recklezz-desktop kernel: [   23.070013] sd 2:0:0:1: Attached scsi generic sg4 type 0
Aug 16 09:28:12 recklezz-desktop kernel: [   23.080982] sd 2:0:0:2: [sdd] Attached SCSI removable disk
Aug 16 09:28:12 recklezz-desktop kernel: [   23.081001] sd 2:0:0:2: Attached scsi generic sg5 type 0
Aug 16 09:28:12 recklezz-desktop kernel: [   23.091970] sd 2:0:0:3: [sde] Attached SCSI removable disk
Aug 16 09:28:12 recklezz-desktop kernel: [   23.091990] sd 2:0:0:3: Attached scsi generic sg6 type 0
Aug 16 09:28:12 recklezz-desktop kernel: [   27.821380] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 16 09:28:12 recklezz-desktop kernel: [   27.856403] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 16 09:28:12 recklezz-desktop kernel: [   27.993171] Linux agpgart interface v0.102
Aug 16 09:28:12 recklezz-desktop kernel: [   28.098261] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
Aug 16 09:28:12 recklezz-desktop kernel: [   28.098300] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
Aug 16 09:28:12 recklezz-desktop kernel: [   28.225050] input: Power Button (FF) as /devices/virtual/input/input2
Aug 16 09:28:12 recklezz-desktop kernel: [   28.240909] ACPI: Power Button (FF) [PWRF]
Aug 16 09:28:12 recklezz-desktop kernel: [   28.241017] input: Power Button (CM) as /devices/virtual/input/input3
Aug 16 09:28:12 recklezz-desktop kernel: [   28.256879] ACPI: Power Button (CM) [PWRB]
Aug 16 09:28:12 recklezz-desktop kernel: [   30.821423] rndis_wlan: Unknown symbol rndis_tx_fixup
Aug 16 09:28:12 recklezz-desktop kernel: [   30.821476] rndis_wlan: Unknown symbol rndis_unbind
Aug 16 09:28:12 recklezz-desktop kernel: [   30.821619] rndis_wlan: Unknown symbol rndis_status
Aug 16 09:28:12 recklezz-desktop kernel: [   30.821688] rndis_wlan: Unknown symbol rndis_command
Aug 16 09:28:12 recklezz-desktop kernel: [   30.821735] rndis_wlan: Unknown symbol generic_rndis_bind
Aug 16 09:28:12 recklezz-desktop kernel: [   30.821829] rndis_wlan: Unknown symbol rndis_rx_fixup
Aug 16 09:28:12 recklezz-desktop kernel: [   30.825996] rndis_wlan: Unknown symbol rndis_tx_fixup
Aug 16 09:28:12 recklezz-desktop kernel: [   30.826064] rndis_wlan: Unknown symbol rndis_unbind
Aug 16 09:28:12 recklezz-desktop kernel: [   30.826205] rndis_wlan: Unknown symbol rndis_status
Aug 16 09:28:12 recklezz-desktop kernel: [   30.826273] rndis_wlan: Unknown symbol rndis_command
Aug 16 09:28:12 recklezz-desktop kernel: [   30.826320] rndis_wlan: Unknown symbol generic_rndis_bind
Aug 16 09:28:12 recklezz-desktop kernel: [   30.826412] rndis_wlan: Unknown symbol rndis_rx_fixup
Aug 16 09:28:12 recklezz-desktop kernel: [   30.921984] usbcore: registered new interface driver cdc_ether
Aug 16 09:28:12 recklezz-desktop kernel: [   30.945998] usb 2-2: bad CDC descriptors
Aug 16 09:28:12 recklezz-desktop kernel: [   30.946015] usbcore: registered new interface driver rndis_host
Aug 16 09:28:12 recklezz-desktop kernel: [   31.757214] input: PC Speaker as /devices/platform/pcspkr/input/input4
Aug 16 09:28:12 recklezz-desktop kernel: [   32.088583] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
Aug 16 09:28:12 recklezz-desktop kernel: [   32.088589] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [AAZA] -> GSI 22 (level, low) -> IRQ 17
Aug 16 09:28:12 recklezz-desktop kernel: [   32.088609] PCI: Setting latency timer of device 0000:00:10.1 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   32.119411] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
Aug 16 09:28:12 recklezz-desktop kernel: [   32.504350] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Aug 16 09:28:12 recklezz-desktop kernel: [   33.100267] rndis_wlan: Unknown symbol rndis_tx_fixup
Aug 16 09:28:12 recklezz-desktop kernel: [   33.100324] rndis_wlan: Unknown symbol rndis_unbind
Aug 16 09:28:12 recklezz-desktop kernel: [   33.100470] rndis_wlan: Unknown symbol rndis_status
Aug 16 09:28:12 recklezz-desktop kernel: [   33.100545] rndis_wlan: Unknown symbol rndis_command
Aug 16 09:28:12 recklezz-desktop kernel: [   33.100595] rndis_wlan: Unknown symbol generic_rndis_bind
Aug 16 09:28:12 recklezz-desktop kernel: [   33.100694] rndis_wlan: Unknown symbol rndis_rx_fixup
Aug 16 09:28:12 recklezz-desktop kernel: [   33.112870] rndis_wlan: Unknown symbol rndis_tx_fixup
Aug 16 09:28:12 recklezz-desktop kernel: [   33.112926] rndis_wlan: Unknown symbol rndis_unbind
Aug 16 09:28:12 recklezz-desktop kernel: [   33.113073] rndis_wlan: Unknown symbol rndis_status
Aug 16 09:28:12 recklezz-desktop kernel: [   33.113148] rndis_wlan: Unknown symbol rndis_command
Aug 16 09:28:12 recklezz-desktop kernel: [   33.113197] rndis_wlan: Unknown symbol generic_rndis_bind
Aug 16 09:28:12 recklezz-desktop kernel: [   33.113296] rndis_wlan: Unknown symbol rndis_rx_fixup
Aug 16 09:28:12 recklezz-desktop kernel: [   33.886923] lp: driver loaded but no devices found
Aug 16 09:28:12 recklezz-desktop kernel: [   34.058281] Adding 4361608k swap on /dev/sda5.  Priority:-1 extents:1 across:4361608k
Aug 16 09:28:12 recklezz-desktop kernel: [   34.614192] EXT3 FS on sda1, internal journal
Aug 16 09:28:12 recklezz-desktop kernel: [   34.755195] device-mapper: uevent: version 1.0.3
Aug 16 09:28:12 recklezz-desktop kernel: [   34.755221] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
Aug 16 09:28:12 recklezz-desktop kernel: [   36.029841] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 16 09:28:12 recklezz-desktop kernel: [   36.387616] No dock devices found.
Aug 16 09:28:12 recklezz-desktop kernel: [   36.732460] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors (1 cpu cores) (version 2.20.00)
Aug 16 09:28:12 recklezz-desktop kernel: [   36.732494] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x6
Aug 16 09:28:12 recklezz-desktop kernel: [   36.732496] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8
Aug 16 09:28:12 recklezz-desktop kernel: [   36.732498] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
Aug 16 09:28:12 recklezz-desktop kernel: [   36.732500] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
Aug 16 09:28:12 recklezz-desktop NetworkManager: <info>  starting...
Aug 16 09:28:13 recklezz-desktop avahi-daemon[5249]: Found user 'avahi' (UID 107) and group 'avahi' (GID 116).
Aug 16 09:28:13 recklezz-desktop avahi-daemon[5249]: Successfully dropped root privileges.
Aug 16 09:28:13 recklezz-desktop avahi-daemon[5249]: avahi-daemon 0.6.22 starting up.
Aug 16 09:28:13 recklezz-desktop avahi-daemon[5249]: Successfully called chroot().
Aug 16 09:28:13 recklezz-desktop avahi-daemon[5249]: Successfully dropped remaining capabilities.
Aug 16 09:28:13 recklezz-desktop avahi-daemon[5249]: No service file found in /etc/avahi/services.
Aug 16 09:28:13 recklezz-desktop avahi-daemon[5249]: Network interface enumeration completed.
Aug 16 09:28:13 recklezz-desktop avahi-daemon[5249]: Registering HINFO record with values 'I686'/'LINUX'.
Aug 16 09:28:13 recklezz-desktop avahi-daemon[5249]: Server startup complete. Host name is recklezz-desktop.local. Local service cookie is 3436240200.
Aug 16 09:28:14 recklezz-desktop kdm[5229]: StartServerSucces
Aug 16 09:28:14 recklezz-desktop kernel: [   38.877346] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Aug 16 09:28:14 recklezz-desktop kernel: [   38.877351] apm: overridden by ACPI.
Aug 16 09:28:14 recklezz-desktop kernel: [   39.174653] ppdev: user-space parallel port driver
Aug 16 09:28:14 recklezz-desktop kernel: [   39.459366] audit(1218904094.722:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5292 profile="/usr/sbin/cupsd" namespace="default"
Aug 16 09:28:15 recklezz-desktop dhcdbd: Started up.
Aug 16 09:28:15 recklezz-desktop kernel: [   89.485680] Marking TSC unstable due to: cpufreq changes.
Aug 16 09:28:15 recklezz-desktop kernel: [   89.494151] Time: acpi_pm clocksource has been installed.
Aug 16 09:28:16 recklezz-desktop kernel: [   90.021736] Clocksource tsc unstable (delta = -272748409 ns)
Aug 16 09:28:16 recklezz-desktop NetworkManager: <info>  eth0: Device is fully-supported using driver 'forcedeth'.
Aug 16 09:28:16 recklezz-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start
Aug 16 09:28:16 recklezz-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing.
Aug 16 09:28:16 recklezz-desktop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'.
Aug 16 09:28:16 recklezz-desktop NetworkManager: <info>  Deactivating device eth0.
Aug 16 09:28:16 recklezz-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link.
Aug 16 09:28:16 recklezz-desktop NetworkManager: <debug> [1218904096.957949] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_Writer_300n').
Aug 16 09:28:16 recklezz-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'.
Aug 16 09:28:17 recklezz-desktop hcid[5544]: Bluetooth HCI daemon
Aug 16 09:28:17 recklezz-desktop kernel: [   90.654759] Bluetooth: Core ver 2.11
Aug 16 09:28:17 recklezz-desktop kernel: [   90.655616] NET: Registered protocol family 31
Aug 16 09:28:17 recklezz-desktop kernel: [   90.655623] Bluetooth: HCI device and connection manager initialized
Aug 16 09:28:17 recklezz-desktop kernel: [   90.655628] Bluetooth: HCI socket layer initialized
Aug 16 09:28:17 recklezz-desktop hcid[5544]: Starting SDP server
Aug 16 09:28:17 recklezz-desktop kernel: [   41.274701] Bluetooth: L2CAP ver 2.9
Aug 16 09:28:17 recklezz-desktop kernel: [   41.274706] Bluetooth: L2CAP socket layer initialized
Aug 16 09:28:17 recklezz-desktop hcid[5544]: Created local server at unix:abstract=/var/run/dbus-EkQ0VYd1ZH,guid=126455b3235f0c2fb8f9e88248a70021
Aug 16 09:28:17 recklezz-desktop kernel: [   41.336363] Bluetooth: RFCOMM socket layer initialized
Aug 16 09:28:17 recklezz-desktop kernel: [   41.336380] Bluetooth: RFCOMM TTY layer initialized
Aug 16 09:28:17 recklezz-desktop kernel: [   41.336382] Bluetooth: RFCOMM ver 1.8
Aug 16 09:28:17 recklezz-desktop input[5587]: Bluetooth Input daemon
Aug 16 09:28:17 recklezz-desktop input[5587]: Registered input manager path:/org/bluez/input
Aug 16 09:28:17 recklezz-desktop anacron[5589]: Anacron 2.3 started on 2008-08-16
Aug 16 09:28:17 recklezz-desktop anacron[5589]: Normal exit (0 jobs run)
Aug 16 09:28:17 recklezz-desktop audio[5565]: Bluetooth Audio daemon
Aug 16 09:28:17 recklezz-desktop audio[5565]: Unix socket created: 5
Aug 16 09:28:17 recklezz-desktop audio[5565]: audio.conf: Key file does not have key 'Enable'
Aug 16 09:28:17 recklezz-desktop audio[5565]: audio.conf: Key file does not have key 'Disable'
Aug 16 09:28:17 recklezz-desktop audio[5565]: add_service_record: got record id 0x10000
Aug 16 09:28:17 recklezz-desktop audio[5565]: audio.conf: Key file does not have key 'Disable'
Aug 16 09:28:17 recklezz-desktop audio[5565]: audio.conf: Key file does not have group 'A2DP'
Aug 16 09:28:17 recklezz-desktop last message repeated 3 times
Aug 16 09:28:17 recklezz-desktop audio[5565]: SEP 0x806d648 registered: type:0 codec:0 seid:1
Aug 16 09:28:17 recklezz-desktop audio[5565]: add_service_record: got record id 0x10001
Aug 16 09:28:17 recklezz-desktop audio[5565]: add_service_record: got record id 0x10002
Aug 16 09:28:17 recklezz-desktop audio[5565]: add_service_record: got record id 0x10003
Aug 16 09:28:17 recklezz-desktop audio[5565]: Registered manager path:/org/bluez/audio
Aug 16 09:28:17 recklezz-desktop /usr/sbin/cron[5616]: (CRON) INFO (pidfile fd = 3)
Aug 16 09:28:17 recklezz-desktop /usr/sbin/cron[5617]: (CRON) STARTUP (fork ok)
Aug 16 09:28:17 recklezz-desktop /usr/sbin/cron[5617]: (CRON) INFO (Running @reboot jobs)
Aug 16 09:28:17 recklezz-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Aug 16 09:28:17 recklezz-desktop NetworkManager: <info>  Will activate connection 'eth0'.
Aug 16 09:28:17 recklezz-desktop NetworkManager: <info>  Device eth0 activation scheduled...
Aug 16 09:28:17 recklezz-desktop NetworkManager: <debug> [1218904097.967647] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth').
Aug 16 09:28:17 recklezz-desktop NetworkManager: <info>  Activation (eth0) started...
Aug 16 09:28:17 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 16 09:28:17 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Aug 16 09:28:17 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Aug 16 09:28:17 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Aug 16 09:28:17 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Aug 16 09:28:17 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Aug 16 09:28:17 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 16 09:28:17 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Aug 16 09:28:17 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Aug 16 09:28:18 recklezz-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction.
Aug 16 09:28:18 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Aug 16 09:28:18 recklezz-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0
Aug 16 09:28:20 recklezz-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0
Aug 16 09:28:20 recklezz-desktop kernel: [   95.553866] NET: Registered protocol family 17
Aug 16 09:28:22 recklezz-desktop dhclient: DHCPREQUEST of 192.168.1.103 on eth0 to 255.255.255.255 port 67
Aug 16 09:28:23 recklezz-desktop dhclient: DHCPACK of 192.168.1.103 from 192.168.1.1
Aug 16 09:28:23 recklezz-desktop avahi-daemon[5249]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.103.
Aug 16 09:28:23 recklezz-desktop avahi-daemon[5249]: New relevant interface eth0.IPv4 for mDNS.
Aug 16 09:28:23 recklezz-desktop avahi-daemon[5249]: Registering new address record for 192.168.1.103 on eth0.IPv4.
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth0
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled...
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started...
Aug 16 09:28:23 recklezz-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Aug 16 09:28:23 recklezz-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Aug 16 09:28:23 recklezz-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Aug 16 09:28:23 recklezz-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon:
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>    address 192.168.1.103
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>    netmask 255.255.255.0
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>    broadcast 192.168.1.255
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>    gateway 192.168.1.1
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>    nameserver 208.67.222.222
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>    nameserver 208.67.220.220
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>    nameserver 24.205.1.14
Aug 16 09:28:23 recklezz-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete.
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Aug 16 09:28:23 recklezz-desktop dhclient: bound to 192.168.1.103 -- renewal in 84542 seconds.
Aug 16 09:28:23 recklezz-desktop avahi-daemon[5249]: Withdrawing address record for 192.168.1.103 on eth0.
Aug 16 09:28:23 recklezz-desktop avahi-daemon[5249]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.103.
Aug 16 09:28:23 recklezz-desktop avahi-daemon[5249]: Interface eth0.IPv4 no longer relevant for mDNS.
Aug 16 09:28:23 recklezz-desktop avahi-daemon[5249]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.103.
Aug 16 09:28:23 recklezz-desktop avahi-daemon[5249]: New relevant interface eth0.IPv4 for mDNS.
Aug 16 09:28:23 recklezz-desktop avahi-daemon[5249]: Registering new address record for 192.168.1.103 on eth0.IPv4.
Aug 16 09:28:24 recklezz-desktop NetworkManager: <info>  Clearing nscd hosts cache.
Aug 16 09:28:24 recklezz-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))
Aug 16 09:28:24 recklezz-desktop NetworkManager: <info>  Activation (eth0) successful, device activated.
Aug 16 09:28:24 recklezz-desktop NetworkManager: <info>  Activation (eth0) Finish handler scheduled.
Aug 16 09:28:24 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Aug 16 09:28:24 recklezz-desktop kernel: [   56.528269] NET: Registered protocol family 10
Aug 16 09:28:24 recklezz-desktop kernel: [   56.528740] lo: Disabled Privacy Extensions
Aug 16 09:28:25 recklezz-desktop ntpdate[5781]: adjust time server 91.189.94.4 offset 0.000691 sec
Aug 16 09:28:25 recklezz-desktop avahi-daemon[5249]: Registering new address record for fe80::217:31ff:fecd:6190 on eth0.*.
Aug 16 09:28:34 recklezz-desktop kernel: [  112.655268] eth0: no IPv6 routers present
Aug 16 09:29:08 recklezz-desktop NetworkManager: <info>  Updating allowed wireless network lists.
Aug 16 09:29:08 recklezz-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - org.freedesktop.NetworkManagerInfo.NoNetworks.
Aug 16 09:36:05 recklezz-desktop kernel: [  583.969500] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
Aug 16 09:36:05 recklezz-desktop kernel: [  584.128271] usb 2-2: reset high speed USB device using ehci_hcd and address 2
Aug 16 09:36:05 recklezz-desktop kernel: [  584.269058] ndiswrapper: driver wusb54gs (Linksys,06/18/2004, 3.60.9.0) loaded
Aug 16 09:36:05 recklezz-desktop kernel: [  584.635310] wlan0: ethernet device 00:12:17:a0:db:7a using NDIS driver: wusb54gs, version: 0x33c0d03, NDIS version: 0x501, vendor: 'Linksys Wireless-G USB Network Adapter with SpeedBooster', 13B1:000E.F.conf
Aug 16 09:36:05 recklezz-desktop NetworkManager: <debug> [1218904565.836232] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_12_17_a0_db_7a').
Aug 16 09:36:05 recklezz-desktop kernel: [  584.674256] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Aug 16 09:36:05 recklezz-desktop kernel: [  584.684298] usbcore: registered new interface driver ndiswrapper
Aug 16 09:36:05 recklezz-desktop NetworkManager: <info>  wlan0: Device is fully-supported using driver 'ndiswrapper'.
Aug 16 09:36:05 recklezz-desktop NetworkManager: <info>  wlan0: driver does not support SSID scans (scan_capa 0x00).
Aug 16 09:36:05 recklezz-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start
Aug 16 09:36:05 recklezz-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing.
Aug 16 09:36:05 recklezz-desktop NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'.
Aug 16 09:36:05 recklezz-desktop NetworkManager: <info>  Deactivating device wlan0.
Aug 16 09:36:05 recklezz-desktop NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument
Aug 16 09:48:12 recklezz-desktop -- MARK --
Aug 16 10:08:12 recklezz-desktop -- MARK --
```

What did I do wrong? :(

---

### Post by javaJake on 2008-08-16
OK, syslog is great, but these extras are going to be useful:

```

*(all of these should be run while you have the adapter plugged in)*
sudo ndiswrapper -l
lsusb
iwconfig

```

---

### Post by xFLHCx on 2008-08-20
Okay everything went beautifully until the last part as well, using hardy heron

dmesg gave me this 
```

[  343.584369] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  343.590365] usbcore: registered new interface driver ndiswrapper
[  346.318820] usb 1-4: new high speed USB device using ehci_hcd and address 2
[  346.369803] usb 1-4: configuration #1 chosen from 1 choice
[  346.417207] usb 1-4: reset high speed USB device using ehci_hcd and address 2
[  346.469339] ndiswrapper: driver wusb54gs (Linksys,06/18/2004, 3.60.9.0) loaded
[  346.847067] irq 18: nobody cared (try booting with the "irqpoll" option)
```

what happens is, my GS blinks slowly
then go with this step

sudo gedit /etc/udev/rules.d/99-custom.rules

then copied 
BUS=="usb", SYSFS{idProduct}=="000e", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'" 
as one line

disconnected it, and reconnected it as told, and when i reconnect it the link isnt on at all. so it goes from slow blinky to no blinky.


any suggestions?

---

### Post by xFLHCx on 2008-08-21
heres the output of my syslog

```
Aug 19 18:43:03 xFLHCx syslogd 1.5.0#1ubuntu1: restart.
Aug 19 18:43:03 xFLHCx kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug 19 18:43:03 xFLHCx kernel: Loaded 27883 symbols from /boot/System.map-2.6.24-19-generic.
Aug 19 18:43:03 xFLHCx kernel: Symbols match kernel version 2.6.24.
Aug 19 18:43:04 xFLHCx kernel: Loaded 16814 symbols from 81 modules.
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 19 18:43:04 xFLHCx kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fee0000 (usable)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000]  BIOS-e820: 000000003fee0000 - 000000003fee3000 (ACPI NVS)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000]  BIOS-e820: 000000003fee3000 - 000000003fef0000 (ACPI data)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000]  BIOS-e820: 000000003fef0000 - 000000003ff00000 (reserved)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] 126MB HIGHMEM available.
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] 896MB LOWMEM available.
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] found SMP MP-table at 000f5740
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] Entering add_active_range(0, 0, 261856) 0 entries of 256 used
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] Zone PFN ranges:
Aug 19 18:43:04 xFLHCx kernel: [    0.000000]   DMA             0 ->     4096
Aug 19 18:43:04 xFLHCx kernel: [    0.000000]   Normal       4096 ->   229376
Aug 19 18:43:04 xFLHCx kernel: [    0.000000]   HighMem    229376 ->   261856
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] Movable zone start PFN for each node
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug 19 18:43:04 xFLHCx kernel: [    0.000000]     0:        0 ->   261856
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] On node 0 totalpages: 261856
Aug 19 18:43:04 xFLHCx kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 19 18:43:04 xFLHCx kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 19 18:43:04 xFLHCx kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 19 18:43:04 xFLHCx kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug 19 18:43:04 xFLHCx kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug 19 18:43:04 xFLHCx kernel: [    0.000000]   HighMem zone: 253 pages used for memmap
Aug 19 18:43:04 xFLHCx kernel: [    0.000000]   HighMem zone: 32227 pages, LIFO batch:7
Aug 19 18:43:04 xFLHCx kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] DMI 2.4 present.
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7090 checksum 0
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: RSDP 000F7090, 0014 (r0 GBT   )
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: RSDT 3FEE3000, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: FACP 3FEE3040, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: DSDT 3FEE30C0, 6550 (r1 GBT    GBTUACPI     1000 MSFT  3000000)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: FACS 3FEE0000, 0040
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: SSDT 3FEE9700, 028A (r1 PTLTD  POWERNOW        1  LTP        1)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: HPET 3FEE99C0, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: MCFG 3FEE9A00, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: APIC 3FEE9640, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] Processor #0 15:11 APIC version 16
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] Processor #1 15:11 APIC version 16
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:a0100000)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259811
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] Kernel command line: root=UUID=79a8b6c6-1071-4cd0-a524-6de22a814617 ro quiet splash
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] Initializing CPU#0
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug 19 18:43:04 xFLHCx kernel: [    0.000000] Detected 2605.673 MHz processor.
Aug 19 18:43:04 xFLHCx kernel: [   22.395804] Console: colour VGA+ 80x25
Aug 19 18:43:04 xFLHCx kernel: [   22.395807] console [tty0] enabled
Aug 19 18:43:04 xFLHCx kernel: [   22.396134] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 19 18:43:04 xFLHCx kernel: [   22.396452] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 19 18:43:04 xFLHCx kernel: [   22.415025] Memory: 1025912k/1047424k available (2177k kernel code, 20872k reserved, 1006k data, 368k init, 129920k highmem)
Aug 19 18:43:04 xFLHCx kernel: [   22.415031] virtual kernel memory layout:
Aug 19 18:43:04 xFLHCx kernel: [   22.415032]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Aug 19 18:43:04 xFLHCx kernel: [   22.415033]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 19 18:43:04 xFLHCx kernel: [   22.415034]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Aug 19 18:43:04 xFLHCx kernel: [   22.415035]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug 19 18:43:04 xFLHCx kernel: [   22.415035]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Aug 19 18:43:04 xFLHCx kernel: [   22.415036]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
Aug 19 18:43:04 xFLHCx kernel: [   22.415037]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
Aug 19 18:43:04 xFLHCx kernel: [   22.415039] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug 19 18:43:04 xFLHCx kernel: [   22.415068] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Aug 19 18:43:04 xFLHCx kernel: [   22.415182] hpet clockevent registered
Aug 19 18:43:04 xFLHCx kernel: [   22.494977] Calibrating delay using timer specific routine.. 5215.06 BogoMIPS (lpj=10430122)
Aug 19 18:43:04 xFLHCx kernel: [   22.494995] Security Framework initialized
Aug 19 18:43:04 xFLHCx kernel: [   22.495000] SELinux:  Disabled at boot.
Aug 19 18:43:04 xFLHCx kernel: [   22.495012] AppArmor: AppArmor initialized
Aug 19 18:43:04 xFLHCx kernel: [   22.495015] Failure registering capabilities with primary security module.
Aug 19 18:43:04 xFLHCx kernel: [   22.495021] Mount-cache hash table entries: 512
Aug 19 18:43:04 xFLHCx kernel: [   22.495114] Initializing cgroup subsys ns
Aug 19 18:43:04 xFLHCx kernel: [   22.495117] Initializing cgroup subsys cpuacct
Aug 19 18:43:04 xFLHCx kernel: [   22.495125] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
Aug 19 18:43:04 xFLHCx kernel: [   22.495132] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Aug 19 18:43:04 xFLHCx kernel: [   22.495133] CPU: L2 Cache: 512K (64 bytes/line)
Aug 19 18:43:04 xFLHCx kernel: [   22.495135] CPU 0(2) -> Core 0
Aug 19 18:43:04 xFLHCx kernel: [   22.495137] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f 00000000
Aug 19 18:43:04 xFLHCx kernel: [   22.495144] Compat vDSO mapped to ffffe000.
Aug 19 18:43:04 xFLHCx kernel: [   22.495153] Checking 'hlt' instruction... OK.
Aug 19 18:43:04 xFLHCx kernel: [   22.511169] SMP alternatives: switching to UP code
Aug 19 18:43:04 xFLHCx kernel: [   22.512147] Early unpacking initramfs... done
Aug 19 18:43:04 xFLHCx kernel: [   22.757499] ACPI: Core revision 20070126
Aug 19 18:43:04 xFLHCx kernel: [   22.757547] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 19 18:43:04 xFLHCx kernel: [   22.770632] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ stepping 02
Aug 19 18:43:04 xFLHCx kernel: [   22.770647] SMP alternatives: switching to SMP code
Aug 19 18:43:04 xFLHCx kernel: [   22.770978] Booting processor 1/1 eip 3000
Aug 19 18:43:04 xFLHCx kernel: [   22.780909] Initializing CPU#1
Aug 19 18:43:04 xFLHCx kernel: [   22.858004] Calibrating delay using timer specific routine.. 5211.08 BogoMIPS (lpj=10422177)
Aug 19 18:43:04 xFLHCx kernel: [   22.858010] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
Aug 19 18:43:04 xFLHCx kernel: [   22.858015] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Aug 19 18:43:04 xFLHCx kernel: [   22.858016] CPU: L2 Cache: 512K (64 bytes/line)
Aug 19 18:43:04 xFLHCx kernel: [   22.858018] CPU 1(2) -> Core 1
Aug 19 18:43:04 xFLHCx kernel: [   22.858019] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f 00000000
Aug 19 18:43:04 xFLHCx kernel: [   22.858245] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ stepping 02
Aug 19 18:43:04 xFLHCx kernel: [   22.858257] Total of 2 processors activated (10426.14 BogoMIPS).
Aug 19 18:43:04 xFLHCx kernel: [   22.858557] ENABLING IO-APIC IRQs
Aug 19 18:43:04 xFLHCx kernel: [   22.858776] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 19 18:43:04 xFLHCx kernel: [   23.005747] Brought up 2 CPUs
Aug 19 18:43:04 xFLHCx kernel: [   23.005798] CPU0 attaching sched-domain:
Aug 19 18:43:04 xFLHCx kernel: [   23.005800]  domain 0: span 03
Aug 19 18:43:04 xFLHCx kernel: [   23.005802]   groups: 01 02
Aug 19 18:43:04 xFLHCx kernel: [   23.005804] CPU1 attaching sched-domain:
Aug 19 18:43:04 xFLHCx kernel: [   23.005805]  domain 0: span 03
Aug 19 18:43:04 xFLHCx kernel: [   23.005807]   groups: 02 01
Aug 19 18:43:04 xFLHCx kernel: [   23.005958] net_namespace: 64 bytes
Aug 19 18:43:04 xFLHCx kernel: [   23.005964] Booting paravirtualized kernel on bare hardware
Aug 19 18:43:04 xFLHCx kernel: [   23.006293] Time: 18:42:42  Date: 08/19/08
Aug 19 18:43:04 xFLHCx kernel: [   23.006312] NET: Registered protocol family 16
Aug 19 18:43:04 xFLHCx kernel: [   23.006445] EISA bus registered
Aug 19 18:43:04 xFLHCx kernel: [   23.006449] ACPI: bus type pci registered
Aug 19 18:43:04 xFLHCx kernel: [   23.007415] PCI: PCI BIOS revision 3.00 entry at 0xfb3f0, last bus=3
Aug 19 18:43:04 xFLHCx kernel: [   23.007417] PCI: Using configuration type 1
Aug 19 18:43:04 xFLHCx kernel: [   23.007425] Setting up standard PCI resources
Aug 19 18:43:04 xFLHCx kernel: [   23.010903] ACPI: EC: Look up EC in DSDT
Aug 19 18:43:04 xFLHCx kernel: [   23.014732] ACPI: Interpreter enabled
Aug 19 18:43:04 xFLHCx kernel: [   23.014737] ACPI: (supports S0 S1 S4 S5)
Aug 19 18:43:04 xFLHCx kernel: [   23.014749] ACPI: Using IOAPIC for interrupt routing
Aug 19 18:43:04 xFLHCx kernel: [   23.018537] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 19 18:43:04 xFLHCx kernel: [   23.018722] pci 0000:00:11.0: set SATA to AHCI mode
Aug 19 18:43:04 xFLHCx kernel: [   23.019779] PCI: Transparent bridge - 0000:00:14.4
Aug 19 18:43:04 xFLHCx kernel: [   23.019802] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 19 18:43:04 xFLHCx kernel: [   23.020003] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
Aug 19 18:43:04 xFLHCx kernel: [   23.020084] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
Aug 19 18:43:04 xFLHCx kernel: [   23.020151] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
Aug 19 18:43:04 xFLHCx kernel: [   23.032413] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 19 18:43:04 xFLHCx kernel: [   23.032492] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 19 18:43:04 xFLHCx kernel: [   23.032569] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 19 18:43:04 xFLHCx kernel: [   23.032646] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 19 18:43:04 xFLHCx kernel: [   23.032725] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 19 18:43:04 xFLHCx kernel: [   23.032802] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 19 18:43:04 xFLHCx kernel: [   23.032880] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 19 18:43:04 xFLHCx kernel: [   23.032956] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 19 18:43:04 xFLHCx kernel: [   23.033048] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug 19 18:43:04 xFLHCx kernel: [   23.033069] pnp: PnP ACPI init
Aug 19 18:43:04 xFLHCx kernel: [   23.033075] ACPI: bus type pnp registered
Aug 19 18:43:04 xFLHCx kernel: [   23.035423] pnp: PnP ACPI: found 15 devices
Aug 19 18:43:04 xFLHCx kernel: [   23.035424] ACPI: ACPI bus type pnp unregistered
Aug 19 18:43:04 xFLHCx kernel: [   23.035427] PnPBIOS: Disabled by ACPI PNP
Aug 19 18:43:04 xFLHCx kernel: [   23.035581] PCI: Using ACPI for IRQ routing
Aug 19 18:43:04 xFLHCx kernel: [   23.035583] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug 19 18:43:04 xFLHCx kernel: [   23.035592] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
Aug 19 18:43:04 xFLHCx kernel: [   23.109401] NET: Registered protocol family 8
Aug 19 18:43:04 xFLHCx kernel: [   23.109403] NET: Registered protocol family 20
Aug 19 18:43:04 xFLHCx kernel: [   23.109430] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Aug 19 18:43:04 xFLHCx kernel: [   23.109434] hpet0: 4 32-bit timers, 14318180 Hz
Aug 19 18:43:04 xFLHCx kernel: [   23.110468] AppArmor: AppArmor Filesystem Enabled
Aug 19 18:43:04 xFLHCx kernel: [   23.113386] Time: hpet clocksource has been installed.
Aug 19 18:43:04 xFLHCx kernel: [   23.113398] Switched to high resolution mode on CPU 0
Aug 19 18:43:04 xFLHCx kernel: [   23.113447] Switched to high resolution mode on CPU 1
Aug 19 18:43:04 xFLHCx kernel: [   23.121362] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121365] system 00:01: ioport range 0x220-0x225 has been reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121367] system 00:01: ioport range 0x290-0x294 has been reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121371] system 00:02: ioport range 0x4100-0x411f has been reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121373] system 00:02: ioport range 0x228-0x22f has been reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121375] system 00:02: ioport range 0x238-0x23f has been reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121376] system 00:02: ioport range 0x40b-0x40b has been reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121378] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121380] system 00:02: ioport range 0xc00-0xc01 has been reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121382] system 00:02: ioport range 0xc14-0xc14 has been reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121384] system 00:02: ioport range 0xc50-0xc52 has been reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121386] system 00:02: ioport range 0xc6c-0xc6d has been reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121388] system 00:02: ioport range 0xc6f-0xc6f has been reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121390] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121392] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121394] system 00:02: ioport range 0xcd4-0xcdf has been reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121396] system 00:02: ioport range 0x4000-0x40fe has been reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121398] system 00:02: ioport range 0x4210-0x4217 has been reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121400] system 00:02: ioport range 0xb00-0xb0f has been reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121402] system 00:02: ioport range 0xb10-0xb1f has been reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121404] system 00:02: ioport range 0xb20-0xb3f has been reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121411] system 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121416] system 00:0e: iomem range 0xcf600-0xcffff has been reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121418] system 00:0e: iomem range 0xf0000-0xf7fff could not be reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121420] system 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121422] system 00:0e: iomem range 0xfc000-0xfffff could not be reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121424] system 00:0e: iomem range 0x3fee0000-0x3fefffff could not be reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121426] system 00:0e: iomem range 0xffff0000-0xffffffff could not be reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121428] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121430] system 00:0e: iomem range 0x100000-0x3fedffff could not be reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121432] system 00:0e: iomem range 0x0-0x0 could not be reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121434] system 00:0e: iomem range 0xfec00000-0xfec00fff could not be reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121436] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.121438] system 00:0e: iomem range 0xfff80000-0xfffeffff could not be reserved
Aug 19 18:43:04 xFLHCx kernel: [   23.151666] PCI: Bridge: 0000:00:02.0
Aug 19 18:43:04 xFLHCx kernel: [   23.151668]   IO window: e000-efff
Aug 19 18:43:04 xFLHCx kernel: [   23.151671]   MEM window: fdf00000-fdffffff
Aug 19 18:43:04 xFLHCx kernel: [   23.151673]   PREFETCH window: d0000000-dfffffff
Aug 19 18:43:04 xFLHCx kernel: [   23.151676] PCI: Bridge: 0000:00:0a.0
Aug 19 18:43:04 xFLHCx kernel: [   23.151677]   IO window: d000-dfff
Aug 19 18:43:04 xFLHCx kernel: [   23.151679]   MEM window: fde00000-fdefffff
Aug 19 18:43:04 xFLHCx kernel: [   23.151682]   PREFETCH window: fdb00000-fdbfffff
Aug 19 18:43:04 xFLHCx kernel: [   23.151684] PCI: Bridge: 0000:00:14.4
Aug 19 18:43:04 xFLHCx kernel: [   23.151686]   IO window: c000-cfff
Aug 19 18:43:04 xFLHCx kernel: [   23.151691]   MEM window: fdd00000-fddfffff
Aug 19 18:43:04 xFLHCx kernel: [   23.151694]   PREFETCH window: fdc00000-fdcfffff
Aug 19 18:43:04 xFLHCx kernel: [   23.151713] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 18 (level, low) -> IRQ 16
Aug 19 18:43:04 xFLHCx kernel: [   23.151717] PCI: Setting latency timer of device 0000:00:02.0 to 64
Aug 19 18:43:04 xFLHCx kernel: [   23.151725] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 16
Aug 19 18:43:04 xFLHCx kernel: [   23.151728] PCI: Setting latency timer of device 0000:00:0a.0 to 64
Aug 19 18:43:04 xFLHCx kernel: [   23.151742] NET: Registered protocol family 2
Aug 19 18:43:04 xFLHCx kernel: [   23.189219] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 19 18:43:04 xFLHCx kernel: [   23.189444] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 19 18:43:04 xFLHCx kernel: [   23.190161] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 19 18:43:04 xFLHCx kernel: [   23.190535] TCP: Hash tables configured (established 131072 bind 65536)
Aug 19 18:43:04 xFLHCx kernel: [   23.190537] TCP reno registered
Aug 19 18:43:04 xFLHCx kernel: [   23.201240] checking if image is initramfs... it is
Aug 19 18:43:04 xFLHCx kernel: [   23.678236] Freeing initrd memory: 7700k freed
Aug 19 18:43:04 xFLHCx kernel: [   23.678848] audit: initializing netlink socket (disabled)
Aug 19 18:43:04 xFLHCx kernel: [   23.678859] audit(1219171362.152:1): initialized
Aug 19 18:43:04 xFLHCx kernel: [   23.678983] highmem bounce pool size: 64 pages
Aug 19 18:43:04 xFLHCx kernel: [   23.680413] VFS: Disk quotas dquot_6.5.1
Aug 19 18:43:04 xFLHCx kernel: [   23.680465] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 19 18:43:04 xFLHCx kernel: [   23.680556] io scheduler noop registered
Aug 19 18:43:04 xFLHCx kernel: [   23.680557] io scheduler anticipatory registered
Aug 19 18:43:04 xFLHCx kernel: [   23.680559] io scheduler deadline registered
Aug 19 18:43:04 xFLHCx kernel: [   23.680565] io scheduler cfq registered (default)
Aug 19 18:43:04 xFLHCx kernel: [   23.819520] Boot video device is 0000:01:00.0
Aug 19 18:43:04 xFLHCx kernel: [   23.819643] PCI: Setting latency timer of device 0000:00:02.0 to 64
Aug 19 18:43:04 xFLHCx kernel: [   23.819664] assign_interrupt_mode Found MSI capability
Aug 19 18:43:04 xFLHCx kernel: [   23.819686] Allocate Port Service[0000:00:02.0:pcie00]
Aug 19 18:43:04 xFLHCx kernel: [   23.819743] PCI: Setting latency timer of device 0000:00:0a.0 to 64
Aug 19 18:43:04 xFLHCx kernel: [   23.819763] assign_interrupt_mode Found MSI capability
Aug 19 18:43:04 xFLHCx kernel: [   23.819782] Allocate Port Service[0000:00:0a.0:pcie00]
Aug 19 18:43:04 xFLHCx kernel: [   23.819957] isapnp: Scanning for PnP cards...
Aug 19 18:43:04 xFLHCx kernel: [   24.172870] isapnp: No Plug & Play device found
Aug 19 18:43:04 xFLHCx kernel: [   24.194328] Real Time Clock Driver v1.12ac
Aug 19 18:43:04 xFLHCx kernel: [   24.194482] hpet_resources: 0xfed00000 is busy
Aug 19 18:43:04 xFLHCx kernel: [   24.194510] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug 19 18:43:04 xFLHCx kernel: [   24.194884] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug 19 18:43:04 xFLHCx kernel: [   24.195399] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug 19 18:43:04 xFLHCx kernel: [   24.196021] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug 19 18:43:04 xFLHCx kernel: [   24.196071] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug 19 18:43:04 xFLHCx kernel: [   24.196146] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Aug 19 18:43:04 xFLHCx kernel: [   24.196497] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 19 18:43:04 xFLHCx kernel: [   24.196501] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 19 18:43:04 xFLHCx kernel: [   24.211528] mice: PS/2 mouse device common for all mice
Aug 19 18:43:04 xFLHCx kernel: [   24.211624] EISA: Probing bus 0 at eisa.0
Aug 19 18:43:04 xFLHCx kernel: [   24.211642] Cannot allocate resource for EISA slot 4
Aug 19 18:43:04 xFLHCx kernel: [   24.211659] EISA: Detected 0 cards.
Aug 19 18:43:04 xFLHCx kernel: [   24.211661] cpuidle: using governor ladder
Aug 19 18:43:04 xFLHCx kernel: [   24.211663] cpuidle: using governor menu
Aug 19 18:43:04 xFLHCx kernel: [   24.211729] NET: Registered protocol family 1
Aug 19 18:43:04 xFLHCx kernel: [   24.211751] Using IPI No-Shortcut mode
Aug 19 18:43:04 xFLHCx kernel: [   24.211778] registered taskstats version 1
Aug 19 18:43:04 xFLHCx kernel: [   24.211866]   Magic number: 4:35:747
Aug 19 18:43:04 xFLHCx kernel: [   24.211993] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 19 18:43:04 xFLHCx kernel: [   24.211995] EDD information not available.
Aug 19 18:43:04 xFLHCx kernel: [   24.212207] Freeing unused kernel memory: 368k freed
Aug 19 18:43:04 xFLHCx kernel: [   24.250408] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Aug 19 18:43:04 xFLHCx kernel: [   25.396212] fuse init (API version 7.9)
Aug 19 18:43:04 xFLHCx kernel: [   25.411838] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 19 18:43:04 xFLHCx kernel: [   25.411848] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 19 18:43:04 xFLHCx kernel: [   25.667326] SCSI subsystem initialized
Aug 19 18:43:04 xFLHCx kernel: [   25.688563] r8169 Gigabit Ethernet driver 2.2LK loaded
Aug 19 18:43:04 xFLHCx kernel: [   25.688584] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 16
Aug 19 18:43:04 xFLHCx kernel: [   25.688600] PCI: Setting latency timer of device 0000:02:00.0 to 64
Aug 19 18:43:04 xFLHCx kernel: [   25.688804] eth0: RTL8168c/8111c at 0xf8844000, 00:1f:d0:5a:fd:e7, XID 3c4000c0 IRQ 221
Aug 19 18:43:04 xFLHCx kernel: [   25.694520] usbcore: registered new interface driver usbfs
Aug 19 18:43:04 xFLHCx kernel: [   25.694538] usbcore: registered new interface driver hub
Aug 19 18:43:04 xFLHCx kernel: [   25.694550] libata version 3.00 loaded.
Aug 19 18:43:04 xFLHCx kernel: [   25.695940] usbcore: registered new device driver usb
Aug 19 18:43:04 xFLHCx kernel: [   25.695994] ahci 0000:00:11.0: version 3.0
Aug 19 18:43:04 xFLHCx kernel: [   25.696027] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 22 (level, low) -> IRQ 17
Aug 19 18:43:04 xFLHCx kernel: [   25.696076] ahci 0000:00:11.0: controller can't do PMP, turning off CAP_PMP
Aug 19 18:43:04 xFLHCx kernel: [   25.697748] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 19 18:43:04 xFLHCx kernel: [   25.820709] Floppy drive(s): fd0 is 1.44M
Aug 19 18:43:04 xFLHCx kernel: [   25.839000] FDC 0 is a post-1991 82077
Aug 19 18:43:04 xFLHCx kernel: [   26.696018] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Aug 19 18:43:04 xFLHCx kernel: [   26.696023] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pio slum part 
Aug 19 18:43:04 xFLHCx kernel: [   26.696350] scsi0 : ahci
Aug 19 18:43:04 xFLHCx kernel: [   26.696402] scsi1 : ahci
Aug 19 18:43:04 xFLHCx kernel: [   26.696429] scsi2 : ahci
Aug 19 18:43:04 xFLHCx kernel: [   26.696455] scsi3 : ahci
Aug 19 18:43:04 xFLHCx kernel: [   26.696512] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 220
Aug 19 18:43:04 xFLHCx kernel: [   26.696515] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 220
Aug 19 18:43:04 xFLHCx kernel: [   26.696518] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 220
Aug 19 18:43:04 xFLHCx kernel: [   26.696521] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 220
Aug 19 18:43:04 xFLHCx kernel: [   27.170740] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 19 18:43:04 xFLHCx kernel: [   27.339304] ata1.00: ATAPI: LITE-ON DVDRW LH-20A1L, BL06, max UDMA/100, ATAPI AN
Aug 19 18:43:04 xFLHCx kernel: [   27.506868] ata1.00: configured for UDMA/100
Aug 19 18:43:04 xFLHCx kernel: [   27.817042] ata2: SATA link down (SStatus 0 SControl 300)
Aug 19 18:43:04 xFLHCx kernel: [   28.128223] ata3: SATA link down (SStatus 0 SControl 300)
Aug 19 18:43:04 xFLHCx kernel: [   28.439405] ata4: SATA link down (SStatus 0 SControl 300)
Aug 19 18:43:04 xFLHCx kernel: [   28.440515] scsi 0:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1L   BL06 PQ: 0 ANSI: 5
Aug 19 18:43:04 xFLHCx kernel: [   28.440666] ACPI: PCI Interrupt 0000:00:12.2[B] -> GSI 17 (level, low) -> IRQ 18
Aug 19 18:43:04 xFLHCx kernel: [   28.440681] ehci_hcd 0000:00:12.2: EHCI Host Controller
Aug 19 18:43:04 xFLHCx kernel: [   28.440925] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Aug 19 18:43:04 xFLHCx kernel: [   28.440960] ehci_hcd 0000:00:12.2: debug port 1
Aug 19 18:43:04 xFLHCx kernel: [   28.440976] ehci_hcd 0000:00:12.2: irq 18, io mem 0xfe02c000
Aug 19 18:43:04 xFLHCx kernel: [   28.447711] Driver 'sr' needs updating - please use bus_type methods
Aug 19 18:43:04 xFLHCx kernel: [   28.451368] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 19 18:43:04 xFLHCx kernel: [   28.451452] usb usb1: configuration #1 chosen from 1 choice
Aug 19 18:43:04 xFLHCx kernel: [   28.451468] hub 1-0:1.0: USB hub found
Aug 19 18:43:04 xFLHCx kernel: [   28.451474] hub 1-0:1.0: 6 ports detected
Aug 19 18:43:04 xFLHCx kernel: [   28.464652] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Aug 19 18:43:04 xFLHCx kernel: [   28.464657] Uniform CD-ROM driver Revision: 3.20
Aug 19 18:43:04 xFLHCx kernel: [   28.464697] sr 0:0:0:0: Attached scsi CD-ROM sr0
Aug 19 18:43:04 xFLHCx kernel: [   28.469185] sr 0:0:0:0: Attached scsi generic sg0 type 5
Aug 19 18:43:04 xFLHCx kernel: [   28.555188] ACPI: PCI Interrupt 0000:00:13.2[B] -> GSI 19 (level, low) -> IRQ 19
Aug 19 18:43:04 xFLHCx kernel: [   28.555201] ehci_hcd 0000:00:13.2: EHCI Host Controller
Aug 19 18:43:04 xFLHCx kernel: [   28.555220] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Aug 19 18:43:04 xFLHCx kernel: [   28.555254] ehci_hcd 0000:00:13.2: debug port 1
Aug 19 18:43:04 xFLHCx kernel: [   28.555270] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
Aug 19 18:43:04 xFLHCx kernel: [   28.567059] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 19 18:43:04 xFLHCx kernel: [   28.567134] usb usb2: configuration #1 chosen from 1 choice
Aug 19 18:43:04 xFLHCx kernel: [   28.567150] hub 2-0:1.0: USB hub found
Aug 19 18:43:04 xFLHCx kernel: [   28.567154] hub 2-0:1.0: 6 ports detected
Aug 19 18:43:04 xFLHCx kernel: [   28.670952] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 20
Aug 19 18:43:04 xFLHCx kernel: [   28.670963] ohci_hcd 0000:00:12.0: OHCI Host Controller
Aug 19 18:43:04 xFLHCx kernel: [   28.670981] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
Aug 19 18:43:04 xFLHCx kernel: [   28.670998] ohci_hcd 0000:00:12.0: irq 20, io mem 0xfe02e000
Aug 19 18:43:04 xFLHCx kernel: [   28.730714] usb usb3: configuration #1 chosen from 1 choice
Aug 19 18:43:04 xFLHCx kernel: [   28.730732] hub 3-0:1.0: USB hub found
Aug 19 18:43:04 xFLHCx kernel: [   28.730740] hub 3-0:1.0: 3 ports detected
Aug 19 18:43:04 xFLHCx kernel: [   28.834418] ACPI: PCI Interrupt 0000:00:12.1[A] -> GSI 16 (level, low) -> IRQ 20
Aug 19 18:43:04 xFLHCx kernel: [   28.834431] ohci_hcd 0000:00:12.1: OHCI Host Controller
Aug 19 18:43:04 xFLHCx kernel: [   28.834448] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
Aug 19 18:43:04 xFLHCx kernel: [   28.834460] ohci_hcd 0000:00:12.1: irq 20, io mem 0xfe02d000
Aug 19 18:43:04 xFLHCx kernel: [   28.894261] usb usb4: configuration #1 chosen from 1 choice
Aug 19 18:43:04 xFLHCx kernel: [   28.894278] hub 4-0:1.0: USB hub found
Aug 19 18:43:04 xFLHCx kernel: [   28.894285] hub 4-0:1.0: 3 ports detected
Aug 19 18:43:04 xFLHCx kernel: [   28.997986] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 18 (level, low) -> IRQ 16
Aug 19 18:43:04 xFLHCx kernel: [   28.997997] ohci_hcd 0000:00:13.0: OHCI Host Controller
Aug 19 18:43:04 xFLHCx kernel: [   28.998013] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Aug 19 18:43:04 xFLHCx kernel: [   28.998032] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02b000
Aug 19 18:43:04 xFLHCx kernel: [   29.057822] usb usb5: configuration #1 chosen from 1 choice
Aug 19 18:43:04 xFLHCx kernel: [   29.057837] hub 5-0:1.0: USB hub found
Aug 19 18:43:04 xFLHCx kernel: [   29.057843] hub 5-0:1.0: 3 ports detected
Aug 19 18:43:04 xFLHCx kernel: [   29.161557] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 18 (level, low) -> IRQ 16
Aug 19 18:43:04 xFLHCx kernel: [   29.161567] ohci_hcd 0000:00:13.1: OHCI Host Controller
Aug 19 18:43:04 xFLHCx kernel: [   29.161587] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
Aug 19 18:43:04 xFLHCx kernel: [   29.161597] ohci_hcd 0000:00:13.1: irq 16, io mem 0xfe02a000
Aug 19 18:43:04 xFLHCx kernel: [   29.221401] usb usb6: configuration #1 chosen from 1 choice
Aug 19 18:43:04 xFLHCx kernel: [   29.221417] hub 6-0:1.0: USB hub found
Aug 19 18:43:04 xFLHCx kernel: [   29.221424] hub 6-0:1.0: 3 ports detected
Aug 19 18:43:04 xFLHCx kernel: [   29.325130] ACPI: PCI Interrupt 0000:00:14.5[C] -> GSI 18 (level, low) -> IRQ 16
Aug 19 18:43:04 xFLHCx kernel: [   29.325140] ohci_hcd 0000:00:14.5: OHCI Host Controller
Aug 19 18:43:04 xFLHCx kernel: [   29.325155] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
Aug 19 18:43:04 xFLHCx kernel: [   29.325167] ohci_hcd 0000:00:14.5: irq 16, io mem 0xfe028000
Aug 19 18:43:04 xFLHCx kernel: [   29.384965] usb usb7: configuration #1 chosen from 1 choice
Aug 19 18:43:04 xFLHCx kernel: [   29.384981] hub 7-0:1.0: USB hub found
Aug 19 18:43:04 xFLHCx kernel: [   29.384987] hub 7-0:1.0: 2 ports detected
Aug 19 18:43:04 xFLHCx kernel: [   29.488805] ACPI: PCI Interrupt 0000:03:0e.0[A] -> GSI 22 (level, low) -> IRQ 17
Aug 19 18:43:04 xFLHCx kernel: [   29.489439] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 20
Aug 19 18:43:04 xFLHCx kernel: [   29.489530] scsi4 : pata_atiixp
Aug 19 18:43:04 xFLHCx kernel: [   29.489569] scsi5 : pata_atiixp
Aug 19 18:43:04 xFLHCx kernel: [   29.490140] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
Aug 19 18:43:04 xFLHCx kernel: [   29.490143] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
Aug 19 18:43:04 xFLHCx kernel: [   29.538419] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[fddff000-fddff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Aug 19 18:43:04 xFLHCx kernel: [   29.668574] ata5.00: HPA unlocked: 117229295 -> 117231408, native 117231408
Aug 19 18:43:04 xFLHCx kernel: [   29.668579] ata5.00: ATA-5: WDC WD600BB-00CAA1, 17.07W17, max UDMA/100
Aug 19 18:43:04 xFLHCx kernel: [   29.668581] ata5.00: 117231408 sectors, multi 16: LBA 
Aug 19 18:43:04 xFLHCx kernel: [   29.669520] ata5.01: ATA-5: WDC WD200BB-60AUA1, 18.20D18, max UDMA/100
Aug 19 18:43:04 xFLHCx kernel: [   29.669522] ata5.01: 39102336 sectors, multi 16: LBA 
Aug 19 18:43:04 xFLHCx kernel: [   29.685445] ata5.00: configured for UDMA/100
Aug 19 18:43:04 xFLHCx kernel: [   29.702343] ata5.01: configured for UDMA/100
Aug 19 18:43:04 xFLHCx kernel: [   29.866864] scsi 4:0:0:0: Direct-Access     ATA      WDC WD600BB-00CA 17.0 PQ: 0 ANSI: 5
Aug 19 18:43:04 xFLHCx kernel: [   29.866919] scsi 4:0:0:0: Attached scsi generic sg1 type 0
Aug 19 18:43:04 xFLHCx kernel: [   29.867241] scsi 4:0:1:0: Direct-Access     ATA      WDC WD200BB-60AU 18.2 PQ: 0 ANSI: 5
Aug 19 18:43:04 xFLHCx kernel: [   29.867283] scsi 4:0:1:0: Attached scsi generic sg2 type 0
Aug 19 18:43:04 xFLHCx kernel: [   29.876188] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Aug 19 18:43:04 xFLHCx kernel: [   29.876192] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Aug 19 18:43:04 xFLHCx kernel: [   29.885392] Driver 'sd' needs updating - please use bus_type methods
Aug 19 18:43:04 xFLHCx kernel: [   29.885462] sd 4:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
Aug 19 18:43:04 xFLHCx kernel: [   29.885471] sd 4:0:0:0: [sda] Write Protect is off
Aug 19 18:43:04 xFLHCx kernel: [   29.885473] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 19 18:43:04 xFLHCx kernel: [   29.885484] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 19 18:43:04 xFLHCx kernel: [   29.885517] sd 4:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
Aug 19 18:43:04 xFLHCx kernel: [   29.885523] sd 4:0:0:0: [sda] Write Protect is off
Aug 19 18:43:04 xFLHCx kernel: [   29.885524] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 19 18:43:04 xFLHCx kernel: [   29.885534] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 19 18:43:04 xFLHCx kernel: [   29.885537]  sda: sda1 sda2 < sda5 >
Aug 19 18:43:04 xFLHCx kernel: [   29.918556] sd 4:0:0:0: [sda] Attached SCSI disk
Aug 19 18:43:04 xFLHCx kernel: [   29.918594] sd 4:0:1:0: [sdb] 39102336 512-byte hardware sectors (20020 MB)
Aug 19 18:43:04 xFLHCx kernel: [   29.918602] sd 4:0:1:0: [sdb] Write Protect is off
Aug 19 18:43:04 xFLHCx kernel: [   29.918604] sd 4:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Aug 19 18:43:04 xFLHCx kernel: [   29.918614] sd 4:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 19 18:43:04 xFLHCx kernel: [   29.918640] sd 4:0:1:0: [sdb] 39102336 512-byte hardware sectors (20020 MB)
Aug 19 18:43:04 xFLHCx kernel: [   29.918647] sd 4:0:1:0: [sdb] Write Protect is off
Aug 19 18:43:04 xFLHCx kernel: [   29.918648] sd 4:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Aug 19 18:43:04 xFLHCx kernel: [   29.918658] sd 4:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 19 18:43:04 xFLHCx kernel: [   29.918660]  sdb: sdb1 < sdb5 sdb6 >
Aug 19 18:43:04 xFLHCx kernel: [   29.959819] sd 4:0:1:0: [sdb] Attached SCSI disk
Aug 19 18:43:04 xFLHCx kernel: [   30.457519] kjournald starting.  Commit interval 5 seconds
Aug 19 18:43:04 xFLHCx kernel: [   30.457501] EXT3-fs: mounted filesystem with ordered data mode.
Aug 19 18:43:04 xFLHCx kernel: [   30.814255] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0072802500001fd0]
Aug 19 18:43:04 xFLHCx kernel: [   39.851586] input: PC Speaker as /devices/platform/pcspkr/input/input2
Aug 19 18:43:04 xFLHCx kernel: [   39.950280] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 19 18:43:04 xFLHCx kernel: [   40.096081] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 19 18:43:04 xFLHCx kernel: [   40.137867] ACPI: WMI-Acer: Mapper loaded
Aug 19 18:43:04 xFLHCx kernel: [   40.181662] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Aug 19 18:43:04 xFLHCx kernel: [   40.211323] input: Power Button (FF) as /devices/virtual/input/input3
Aug 19 18:43:04 xFLHCx kernel: [   40.272357] ACPI: Power Button (FF) [PWRF]
Aug 19 18:43:04 xFLHCx kernel: [   40.272413] input: Power Button (CM) as /devices/virtual/input/input4
Aug 19 18:43:04 xFLHCx kernel: [   40.340174] ACPI: Power Button (CM) [PWRB]
Aug 19 18:43:04 xFLHCx kernel: [   40.595531] Linux agpgart interface v0.102
Aug 19 18:43:04 xFLHCx kernel: [   40.785740] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Aug 19 18:43:04 xFLHCx kernel: [   40.835504] parport_pc 00:0a: reported by Plug and Play ACPI
Aug 19 18:43:04 xFLHCx kernel: [   40.835560] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Aug 19 18:43:04 xFLHCx kernel: [   41.168540] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 20
Aug 19 18:43:04 xFLHCx kernel: [   41.199906] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
Aug 19 18:43:04 xFLHCx kernel: [   41.930977] lp0: using parport0 (interrupt-driven).
Aug 19 18:43:04 xFLHCx kernel: [   42.661527] EXT3 FS on sdb6, internal journal
Aug 19 18:43:04 xFLHCx kernel: [   43.740225] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 19 18:43:04 xFLHCx kernel: [   44.108108] No dock devices found.
Aug 19 18:43:04 xFLHCx kernel: [   44.455966] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ processors (2 cpu cores) (version 2.20.00)
Aug 19 18:43:04 xFLHCx kernel: [   44.456037] powernow-k8:    0 : fid 0x12 (2600 MHz), vid 0x9
Aug 19 18:43:04 xFLHCx kernel: [   44.456041] powernow-k8:    1 : fid 0x10 (2400 MHz), vid 0xb
Aug 19 18:43:04 xFLHCx kernel: [   44.456042] powernow-k8:    2 : fid 0xe (2200 MHz), vid 0xd
Aug 19 18:43:04 xFLHCx kernel: [   44.456044] powernow-k8:    3 : fid 0xc (2000 MHz), vid 0xf
Aug 19 18:43:04 xFLHCx kernel: [   44.456046] powernow-k8:    4 : fid 0xa (1800 MHz), vid 0x11
Aug 19 18:43:04 xFLHCx kernel: [   44.456047] powernow-k8:    5 : fid 0x2 (1000 MHz), vid 0x12
Aug 19 18:43:04 xFLHCx NetworkManager: <info>  starting... 
Aug 19 18:43:04 xFLHCx avahi-daemon[5170]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Aug 19 18:43:04 xFLHCx avahi-daemon[5170]: Successfully dropped root privileges.
Aug 19 18:43:04 xFLHCx avahi-daemon[5170]: avahi-daemon 0.6.22 starting up.
Aug 19 18:43:04 xFLHCx avahi-daemon[5170]: Successfully called chroot().
Aug 19 18:43:04 xFLHCx avahi-daemon[5170]: Successfully dropped remaining capabilities.
Aug 19 18:43:04 xFLHCx avahi-daemon[5171]: chroot.c: open() failed: No such file or directory
Aug 19 18:43:04 xFLHCx avahi-daemon[5170]: Failed to open /etc/resolv.conf: Invalid argument
Aug 19 18:43:04 xFLHCx avahi-daemon[5170]: No service file found in /etc/avahi/services.
Aug 19 18:43:04 xFLHCx avahi-daemon[5170]: Network interface enumeration completed.
Aug 19 18:43:04 xFLHCx avahi-daemon[5170]: Registering HINFO record with values 'I686'/'LINUX'.
Aug 19 18:43:04 xFLHCx avahi-daemon[5170]: Server startup complete. Host name is xFLHCx.local. Local service cookie is 3362447416.
Aug 19 18:43:04 xFLHCx kernel: [   45.062677] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Aug 19 18:43:04 xFLHCx kernel: [   45.062684] apm: disabled - APM is not SMP safe.
Aug 19 18:43:04 xFLHCx kernel: [   45.191205] ppdev: user-space parallel port driver
Aug 19 18:43:04 xFLHCx kernel: [   45.355205] audit(1219185784.586:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5212 profile="/usr/sbin/cupsd" namespace="default"
Aug 19 18:43:04 xFLHCx dhcdbd: Started up.
Aug 19 18:43:05 xFLHCx kernel: [   45.793627] Clocksource tsc unstable (delta = -172213265 ns)
Aug 19 18:43:06 xFLHCx kernel: [   46.334816] r8169: eth0: link down
Aug 19 18:43:06 xFLHCx NetworkManager: <info>  eth0: Device is fully-supported using driver 'r8169'. 
Aug 19 18:43:06 xFLHCx NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Aug 19 18:43:06 xFLHCx NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Aug 19 18:43:06 xFLHCx NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Aug 19 18:43:06 xFLHCx NetworkManager: <info>  Deactivating device eth0. 
Aug 19 18:43:06 xFLHCx NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Aug 19 18:43:06 xFLHCx NetworkManager: <debug> [1219185786.647532] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVDRW_LH_20A1L'). 
Aug 19 18:43:06 xFLHCx hcid[5441]: Bluetooth HCI daemon
Aug 19 18:43:06 xFLHCx kernel: [   46.376252] Bluetooth: Core ver 2.11
Aug 19 18:43:06 xFLHCx kernel: [   46.376569] NET: Registered protocol family 31
Aug 19 18:43:06 xFLHCx kernel: [   46.376572] Bluetooth: HCI device and connection manager initialized
Aug 19 18:43:06 xFLHCx kernel: [   46.376575] Bluetooth: HCI socket layer initialized
Aug 19 18:43:06 xFLHCx hcid[5441]: Starting SDP server
Aug 19 18:43:06 xFLHCx kernel: [   46.386110] Bluetooth: L2CAP ver 2.9
Aug 19 18:43:06 xFLHCx kernel: [   46.386114] Bluetooth: L2CAP socket layer initialized
Aug 19 18:43:06 xFLHCx hcid[5441]: Created local server at unix:abstract=/var/run/dbus-dFx6yAS70B,guid=e0bef8dd9615ec95bd402ca548ab4c7a
Aug 19 18:43:06 xFLHCx audio[5461]: Bluetooth Audio daemon
Aug 19 18:43:06 xFLHCx input[5462]: Bluetooth Input daemon
Aug 19 18:43:06 xFLHCx audio[5461]: Unix socket created: 5
Aug 19 18:43:06 xFLHCx audio[5461]: audio.conf: Key file does not have key 'Enable'
Aug 19 18:43:06 xFLHCx audio[5461]: audio.conf: Key file does not have key 'Disable'
Aug 19 18:43:06 xFLHCx input[5462]: Registered input manager path:/org/bluez/input
Aug 19 18:43:06 xFLHCx kernel: [   46.416609] Bluetooth: RFCOMM socket layer initialized
Aug 19 18:43:06 xFLHCx kernel: [   46.416619] Bluetooth: RFCOMM TTY layer initialized
Aug 19 18:43:06 xFLHCx kernel: [   46.416621] Bluetooth: RFCOMM ver 1.8
Aug 19 18:43:06 xFLHCx NetworkManager: <debug> [1219185786.831172] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Aug 19 18:43:06 xFLHCx audio[5461]: add_service_record: got record id 0x10000
Aug 19 18:43:06 xFLHCx audio[5461]: audio.conf: Key file does not have key 'Disable'
Aug 19 18:43:06 xFLHCx audio[5461]: audio.conf: Key file does not have group 'A2DP'
Aug 19 18:43:06 xFLHCx last message repeated 3 times
Aug 19 18:43:06 xFLHCx audio[5461]: SEP 0x806d748 registered: type:0 codec:0 seid:1
Aug 19 18:43:06 xFLHCx audio[5461]: add_service_record: got record id 0x10001
Aug 19 18:43:06 xFLHCx audio[5461]: add_service_record: got record id 0x10002
Aug 19 18:43:06 xFLHCx audio[5461]: add_service_record: got record id 0x10003
Aug 19 18:43:06 xFLHCx audio[5461]: Registered manager path:/org/bluez/audio
Aug 19 18:43:09 xFLHCx kernel: [   47.364043] [drm] Initialized drm 1.1.0 20060810
Aug 19 18:43:09 xFLHCx anacron[5554]: Anacron 2.3 started on 2008-08-19
Aug 19 18:43:09 xFLHCx anacron[5554]: Will run job `cron.daily' in 5 min.
Aug 19 18:43:09 xFLHCx anacron[5554]: Will run job `cron.weekly' in 10 min.
Aug 19 18:43:09 xFLHCx anacron[5554]: Will run job `cron.monthly' in 15 min.
Aug 19 18:43:09 xFLHCx anacron[5554]: Jobs will be executed sequentially
Aug 19 18:43:09 xFLHCx /usr/sbin/cron[5581]: (CRON) INFO (pidfile fd = 3)
Aug 19 18:43:09 xFLHCx /usr/sbin/cron[5582]: (CRON) STARTUP (fork ok)
Aug 19 18:43:09 xFLHCx /usr/sbin/cron[5582]: (CRON) INFO (Running @reboot jobs)
Aug 19 18:43:16 xFLHCx kernel: [   49.960226] hda-intel: Invalid position buffer, using LPIB read method instead.
Aug 19 18:45:04 xFLHCx kernel: [   91.639521] NET: Registered protocol family 10
Aug 19 18:45:04 xFLHCx kernel: [   91.639699] lo: Disabled Privacy Extensions
Aug 19 18:45:04 xFLHCx kernel: [   91.639955] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 19 18:45:08 xFLHCx hcid[5441]: Default passkey agent (:1.20, /org/bluez/passkey) registered
Aug 19 18:45:08 xFLHCx hcid[5441]: Default authorization agent (:1.20, /org/bluez/auth) registered
Aug 19 18:45:12 xFLHCx NetworkManager: <info>  Updating allowed wireless network lists. 
Aug 19 18:45:12 xFLHCx NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Aug 19 18:47:14 xFLHCx ntfs-3g[6024]: Version 1.2216 external FUSE 27 
Aug 19 18:47:14 xFLHCx ntfs-3g[6024]: Mounted /dev/sda1 (Read-Write, label "", NTFS 3.1) 
Aug 19 18:47:14 xFLHCx ntfs-3g[6024]: Cmdline options: rw,nosuid,nodev,uhelper=hal,locale=en_US.UTF-8 
Aug 19 18:47:14 xFLHCx ntfs-3g[6024]: Mount options: rw,nosuid,nodev,uhelper=hal,silent,allow_other,nonempty,relatime,noatime,fsname=/dev/sda1,blkdev,blksize=4096 
Aug 19 18:47:14 xFLHCx hald: mounted /dev/sda1 on behalf of uid 1000
Aug 19 18:48:09 xFLHCx anacron[5554]: Job `cron.daily' started
Aug 19 18:48:09 xFLHCx anacron[6072]: Updated timestamp for job `cron.daily' to 2008-08-19
Aug 19 18:49:19 xFLHCx kernel: [  219.372835] UDF-fs: No VRS found
Aug 19 18:49:19 xFLHCx NetworkManager: <debug> [1219186159.420052] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Ubuntu_8_04_1_i386'). 
Aug 19 18:49:19 xFLHCx kernel: [  219.406807] ISO 9660 Extensions: Microsoft Joliet Level 3
Aug 19 18:49:19 xFLHCx kernel: [  219.407879] ISO 9660 Extensions: RRIP_1991A
Aug 19 18:49:34 xFLHCx kernel: [  226.207193] UDF-fs: No VRS found
Aug 19 18:49:34 xFLHCx kernel: [  226.217962] ISO 9660 Extensions: Microsoft Joliet Level 3
Aug 19 18:49:34 xFLHCx kernel: [  226.225749] ISO 9660 Extensions: RRIP_1991A
Aug 19 18:53:41 xFLHCx kernel: [  343.584369] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
Aug 19 18:53:41 xFLHCx kernel: [  343.590365] usbcore: registered new interface driver ndiswrapper
Aug 19 18:53:48 xFLHCx kernel: [  346.318820] usb 1-4: new high speed USB device using ehci_hcd and address 2
Aug 19 18:53:49 xFLHCx kernel: [  346.369803] usb 1-4: configuration #1 chosen from 1 choice
Aug 19 18:53:49 xFLHCx NetworkManager: <debug> [1219186429.051047] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13b1_e_1111'). 
Aug 19 18:53:49 xFLHCx kernel: [  346.417207] usb 1-4: reset high speed USB device using ehci_hcd and address 2
Aug 19 18:53:49 xFLHCx kernel: [  346.469339] ndiswrapper: driver wusb54gs (Linksys,06/18/2004, 3.60.9.0) loaded
Aug 19 18:53:50 xFLHCx kernel: [  346.847067] irq 18: nobody cared (try booting with the "irqpoll" option)
Aug 19 18:53:50 xFLHCx kernel: [  346.847074] Pid: 0, comm: swapper Tainted: P        2.6.24-19-generic #1
Aug 19 18:53:50 xFLHCx kernel: [  346.847087]  [__report_bad_irq+0x24/0x80] __report_bad_irq+0x24/0x80
Aug 19 18:53:50 xFLHCx kernel: [  346.847097]  [note_interrupt+0x27b/0x2c0] note_interrupt+0x27b/0x2c0
Aug 19 18:53:50 xFLHCx kernel: [  346.847105]  [snd_pcm:ktime_get_ts+0x1e/0x4f0] ktime_get_ts+0x1e/0x60
Aug 19 18:53:50 xFLHCx kernel: [  346.847111]  [handle_IRQ_event+0x30/0x60] handle_IRQ_event+0x30/0x60
Aug 19 18:53:50 xFLHCx kernel: [  346.847117]  [handle_fasteoi_irq+0x86/0xe0] handle_fasteoi_irq+0x86/0xe0
Aug 19 18:53:50 xFLHCx kernel: [  346.847122]  [do_IRQ+0x3b/0x70] do_IRQ+0x3b/0x70
Aug 19 18:53:50 xFLHCx kernel: [  346.847129]  [common_interrupt+0x23/0x30] common_interrupt+0x23/0x30
Aug 19 18:53:50 xFLHCx kernel: [  346.847138]  [finish_task_switch+0x24/0x90] finish_task_switch+0x24/0x90
Aug 19 18:53:50 xFLHCx kernel: [  346.847146]  [lp:schedule+0x20a/0x650] schedule+0x20a/0x600
Aug 19 18:53:50 xFLHCx kernel: [  346.847152]  [hrtimer_start+0xc7/0x140] hrtimer_start+0xc7/0x140
Aug 19 18:53:50 xFLHCx kernel: [  346.847162]  [tick_nohz_restart_sched_tick+0xf1/0x140] tick_nohz_restart_sched_tick+0xf1/0x140
Aug 19 18:53:50 xFLHCx kernel: [  346.847168]  [cpu_idle+0x8c/0xd0] cpu_idle+0x8c/0xd0
Aug 19 18:53:50 xFLHCx kernel: [  346.847181]  =======================
Aug 19 18:53:50 xFLHCx kernel: [  346.847184] handlers:
Aug 19 18:53:50 xFLHCx kernel: [  346.847185] [<f891eb80>] (usb_hcd_irq+0x0/0x60 [usbcore])
Aug 19 18:53:50 xFLHCx kernel: [  346.847202] Disabling IRQ #18
Aug 19 18:53:54 xFLHCx kernel: [  348.439208] WARNING: at /build/buildd/linux-2.6.24/drivers/usb/host/ehci-hcd.c:869 ehci_urb_dequeue()
Aug 19 18:53:54 xFLHCx kernel: [  348.439214] Pid: 1514, comm: khubd Tainted: P        2.6.24-19-generic #1
Aug 19 18:53:54 xFLHCx kernel: [  348.439228]  [<f8874b3d>] ehci_urb_dequeue+0x14d/0x160 [ehci_hcd]
Aug 19 18:53:54 xFLHCx kernel: [  348.439242]  [<f891e96f>] unlink1+0x6f/0xe0 [usbcore]
Aug 19 18:53:54 xFLHCx kernel: [  348.439262]  [<f891fd42>] usb_hcd_unlink_urb+0x12/0x30 [usbcore]
Aug 19 18:53:54 xFLHCx kernel: [  348.439278]  [<f8c32f77>] wrap_cancel_irp+0x77/0xb0 [ndiswrapper]
Aug 19 18:53:54 xFLHCx kernel: [  348.439300]  [<f8c29ba8>] IoCancelIrp+0x38/0x70 [ndiswrapper]
Aug 19 18:53:54 xFLHCx kernel: [  348.439332]  [<f8c2eef4>] mp_init+0xa4/0x1f0 [ndiswrapper]
Aug 19 18:53:54 xFLHCx kernel: [  348.439352]  [<f8c2f119>] NdisDispatchPnp+0xd9/0xfc0 [ndiswrapper]
Aug 19 18:53:54 xFLHCx kernel: [  348.439378]  [__switch_to+0x9e/0x150] __switch_to+0x9e/0x150
Aug 19 18:53:54 xFLHCx kernel: [  348.439387]  [lp:schedule+0x20a/0x650] schedule+0x20a/0x600
Aug 19 18:53:54 xFLHCx kernel: [  348.439393]  [ide_core:kunmap_atomic+0x3d/0x2f30] kunmap_atomic+0x3d/0xb0
Aug 19 18:53:54 xFLHCx kernel: [  348.439401]  [<f8c28a41>] IoAllocateIrp+0x61/0x80 [ndiswrapper]
Aug 19 18:53:54 xFLHCx kernel: [  348.439420]  [_spin_lock_bh+0x8/0x20] _spin_lock_bh+0x8/0x20
Aug 19 18:53:54 xFLHCx kernel: [  348.439426]  [<f8c24c24>] get_current_nt_thread+0x44/0x50 [ndiswrapper]
Aug 19 18:53:54 xFLHCx kernel: [  348.439445]  [<f8c28d35>] IofCallDriver+0x55/0xc0 [ndiswrapper]
Aug 19 18:53:54 xFLHCx kernel: [  348.439464]  [<f8c2a731>] IoSendIrpTopDev+0xc1/0x120 [ndiswrapper]
Aug 19 18:53:54 xFLHCx kernel: [  348.439487]  [<f8c2a972>] pnp_start_device+0x42/0xa0 [ndiswrapper]
Aug 19 18:53:54 xFLHCx kernel: [  348.439502]  [<f8c319f2>] NdisAddDevice+0x222/0x3e0 [ndiswrapper]
Aug 19 18:53:54 xFLHCx kernel: [  348.439524]  [<f8c2adbf>] wrap_pnp_start_device+0x23f/0x290 [ndiswrapper]
Aug 19 18:53:54 xFLHCx kernel: [  348.439547]  [<f8c2b4e6>] wrap_pnp_start_usb_device+0xa6/0xd0 [ndiswrapper]
Aug 19 18:53:54 xFLHCx kernel: [  348.439562]  [sysfs_ilookup_test+0x0/0x10] sysfs_ilookup_test+0x0/0x10
Aug 19 18:53:54 xFLHCx kernel: [  348.439571]  [sysfs_find_dirent+0x21/0x30] sysfs_find_dirent+0x21/0x30
Aug 19 18:53:54 xFLHCx kernel: [  348.439576]  [sysfs_addrm_finish+0x14/0x1c0] sysfs_addrm_finish+0x14/0x1c0
Aug 19 18:53:54 xFLHCx kernel: [  348.439579]  [sysfs_add_one+0x44/0xe0] sysfs_add_one+0x44/0xe0
Aug 19 18:53:54 xFLHCx kernel: [  348.439583]  [sysfs_addrm_start+0x3f/0xb0] sysfs_addrm_start+0x3f/0xb0
Aug 19 18:53:54 xFLHCx kernel: [  348.439587]  [snd_pcm:mutex_lock+0x8/0x290] mutex_lock+0x8/0x20
Aug 19 18:53:54 xFLHCx kernel: [  348.439591]  [<f892282b>] usb_autopm_do_device+0x7b/0x100 [usbcore]
Aug 19 18:53:54 xFLHCx kernel: [  348.439606]  [<f8922397>] usb_match_one_id+0x27/0xb0 [usbcore]
Aug 19 18:53:54 xFLHCx kernel: [  348.439624]  [<f89235d9>] usb_probe_interface+0xb9/0x140 [usbcore]
Aug 19 18:53:54 xFLHCx kernel: [  348.439643]  [driver_probe_device+0x88/0x190] driver_probe_device+0x88/0x190
Aug 19 18:53:54 xFLHCx kernel: [  348.439648]  [klist_next+0x55/0xb0] klist_next+0x55/0xb0
Aug 19 18:53:54 xFLHCx kernel: [  348.439654]  [ide_core:bus_for_each_drv+0x44/0x220] bus_for_each_drv+0x44/0x70
Aug 19 18:53:54 xFLHCx kernel: [  348.439661]  [ide_core:device_attach+0x86/0x130] device_attach+0x86/0x90
Aug 19 18:53:54 xFLHCx kernel: [  348.439664]  [__device_attach+0x0/0x10] __device_attach+0x0/0x10
Aug 19 18:53:54 xFLHCx kernel: [  348.439669]  [bus_attach_device+0x45/0x90] bus_attach_device+0x45/0x90
Aug 19 18:53:54 xFLHCx kernel: [  348.439676]  [usbcore:device_add+0x418/0x510] device_add+0x418/0x510
Aug 19 18:53:54 xFLHCx kernel: [  348.439687]  [<f8921522>] usb_set_configuration+0x392/0x5d0 [usbcore]
Aug 19 18:53:54 xFLHCx kernel: [  348.439712]  [<f8929b06>] generic_probe+0x76/0xb0 [usbcore]
Aug 19 18:53:54 xFLHCx kernel: [  348.439731]  [<f8923393>] usb_probe_device+0x33/0x40 [usbcore]
Aug 19 18:53:54 xFLHCx kernel: [  348.439744]  [driver_probe_device+0x88/0x190] driver_probe_device+0x88/0x190
Aug 19 18:53:54 xFLHCx kernel: [  348.439749]  [klist_next+0x55/0xb0] klist_next+0x55/0xb0
Aug 19 18:53:54 xFLHCx kernel: [  348.439756]  [ide_core:bus_for_each_drv+0x44/0x220] bus_for_each_drv+0x44/0x70
Aug 19 18:53:54 xFLHCx kernel: [  348.439764]  [ide_core:device_attach+0x86/0x130] device_attach+0x86/0x90
Aug 19 18:53:54 xFLHCx kernel: [  348.439767]  [__device_attach+0x0/0x10] __device_attach+0x0/0x10
Aug 19 18:53:54 xFLHCx kernel: [  348.439772]  [bus_attach_device+0x45/0x90] bus_attach_device+0x45/0x90
Aug 19 18:53:54 xFLHCx kernel: [  348.439779]  [usbcore:device_add+0x418/0x510] device_add+0x418/0x510
Aug 19 18:53:54 xFLHCx kernel: [  348.439789]  [<f891c2f6>] usb_new_device+0x56/0xa0 [usbcore]
Aug 19 18:53:54 xFLHCx kernel: [  348.439807]  [<f891da97>] hub_thread+0x687/0xcb0 [usbcore]
Aug 19 18:53:54 xFLHCx kernel: [  348.439834]  [<c0140c40>] autoremove_wake_function+0x0/0x40
Aug 19 18:53:54 xFLHCx kernel: [  348.439843]  [<f891d410>] hub_thread+0x0/0xcb0 [usbcore]
Aug 19 18:53:54 xFLHCx kernel: [  348.439858]  [kthread+0x42/0x70] kthread+0x42/0x70
Aug 19 18:53:54 xFLHCx kernel: [  348.439861]  [kthread+0x0/0x70] kthread+0x0/0x70
Aug 19 18:53:54 xFLHCx kernel: [  348.439865]  [kernel_thread_helper+0x7/0x10] kernel_thread_helper+0x7/0x10
Aug 19 18:53:54 xFLHCx kernel: [  348.439871]  =======================
Aug 19 18:56:38 xFLHCx NetworkManager: <info>  Disconnected. 
Aug 19 18:56:40 xFLHCx NetworkManager: <info>  Enabling networking. 
Aug 19 18:56:40 xFLHCx NetworkManager: <info>  Deactivating device eth0. 
Aug 19 18:56:40 xFLHCx kernel: [  416.285648] r8169: eth0: link down
Aug 19 18:56:40 xFLHCx kernel: [  416.286548] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 19 18:56:40 xFLHCx NetworkManager: <info>  eth0: Device is fully-supported using driver 'r8169'. 
Aug 19 18:56:40 xFLHCx NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Aug 19 18:56:40 xFLHCx NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Aug 19 18:56:40 xFLHCx NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Aug 19 18:56:40 xFLHCx NetworkManager: <info>  Deactivating device eth0. 
Aug 19 19:05:14 xFLHCx init: tty4 main process (4725) killed by TERM signal
Aug 19 19:05:14 xFLHCx init: tty5 main process (4726) killed by TERM signal
Aug 19 19:05:14 xFLHCx init: tty2 main process (4728) killed by TERM signal
Aug 19 19:05:14 xFLHCx init: tty3 main process (4731) killed by TERM signal
Aug 19 19:05:14 xFLHCx init: tty6 main process (4732) killed by TERM signal
Aug 19 19:05:14 xFLHCx init: tty1 main process (5663) killed by TERM signal
Aug 19 19:05:14 xFLHCx avahi-daemon[5170]: Got SIGTERM, quitting.
Aug 19 19:05:16 xFLHCx kernel: [  639.860718] ip6_tables: (C) 2000-2006 Netfilter Core Team
Aug 19 19:05:17 xFLHCx exiting on signal 15
Aug 21 00:43:45 xFLHCx syslogd 1.5.0#1ubuntu1: restart.
Aug 21 00:43:45 xFLHCx kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug 21 00:43:45 xFLHCx kernel: Loaded 27883 symbols from /boot/System.map-2.6.24-19-generic.
Aug 21 00:43:45 xFLHCx kernel: Symbols match kernel version 2.6.24.
Aug 21 00:43:45 xFLHCx kernel: Loaded 17139 symbols from 85 modules.
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 21 00:43:45 xFLHCx kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fee0000 (usable)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000]  BIOS-e820: 000000003fee0000 - 000000003fee3000 (ACPI NVS)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000]  BIOS-e820: 000000003fee3000 - 000000003fef0000 (ACPI data)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000]  BIOS-e820: 000000003fef0000 - 000000003ff00000 (reserved)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] 126MB HIGHMEM available.
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] 896MB LOWMEM available.
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] found SMP MP-table at 000f5740
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] Entering add_active_range(0, 0, 261856) 0 entries of 256 used
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] Zone PFN ranges:
Aug 21 00:43:45 xFLHCx kernel: [    0.000000]   DMA             0 ->     4096
Aug 21 00:43:45 xFLHCx kernel: [    0.000000]   Normal       4096 ->   229376
Aug 21 00:43:45 xFLHCx kernel: [    0.000000]   HighMem    229376 ->   261856
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] Movable zone start PFN for each node
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug 21 00:43:45 xFLHCx kernel: [    0.000000]     0:        0 ->   261856
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] On node 0 totalpages: 261856
Aug 21 00:43:45 xFLHCx kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 21 00:43:45 xFLHCx kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 21 00:43:45 xFLHCx kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 21 00:43:45 xFLHCx kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug 21 00:43:45 xFLHCx kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug 21 00:43:45 xFLHCx kernel: [    0.000000]   HighMem zone: 253 pages used for memmap
Aug 21 00:43:45 xFLHCx kernel: [    0.000000]   HighMem zone: 32227 pages, LIFO batch:7
Aug 21 00:43:45 xFLHCx kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] DMI 2.4 present.
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7090 checksum 0
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: RSDP 000F7090, 0014 (r0 GBT   )
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: RSDT 3FEE3000, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: FACP 3FEE3040, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: DSDT 3FEE30C0, 6550 (r1 GBT    GBTUACPI     1000 MSFT  3000000)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: FACS 3FEE0000, 0040
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: SSDT 3FEE9700, 028A (r1 PTLTD  POWERNOW        1  LTP        1)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: HPET 3FEE99C0, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: MCFG 3FEE9A00, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: APIC 3FEE9640, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] Processor #0 15:11 APIC version 16
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] Processor #1 15:11 APIC version 16
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:a0100000)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259811
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] Kernel command line: root=UUID=79a8b6c6-1071-4cd0-a524-6de22a814617 ro quiet splash
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] Initializing CPU#0
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug 21 00:43:45 xFLHCx kernel: [    0.000000] Detected 2605.737 MHz processor.
Aug 21 00:43:45 xFLHCx kernel: [   27.022142] Console: colour VGA+ 80x25
Aug 21 00:43:45 xFLHCx kernel: [   27.022144] console [tty0] enabled
Aug 21 00:43:45 xFLHCx kernel: [   27.022472] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 21 00:43:45 xFLHCx kernel: [   27.022791] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 21 00:43:45 xFLHCx kernel: [   27.041364] Memory: 1025912k/1047424k available (2177k kernel code, 20872k reserved, 1006k data, 368k init, 129920k highmem)
Aug 21 00:43:45 xFLHCx kernel: [   27.041370] virtual kernel memory layout:
Aug 21 00:43:45 xFLHCx kernel: [   27.041371]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Aug 21 00:43:45 xFLHCx kernel: [   27.041372]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 21 00:43:45 xFLHCx kernel: [   27.041373]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Aug 21 00:43:45 xFLHCx kernel: [   27.041374]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug 21 00:43:45 xFLHCx kernel: [   27.041374]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Aug 21 00:43:45 xFLHCx kernel: [   27.041375]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
Aug 21 00:43:45 xFLHCx kernel: [   27.041376]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
Aug 21 00:43:45 xFLHCx kernel: [   27.041378] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug 21 00:43:45 xFLHCx kernel: [   27.041407] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Aug 21 00:43:45 xFLHCx kernel: [   27.041521] hpet clockevent registered
Aug 21 00:43:45 xFLHCx kernel: [   27.121316] Calibrating delay using timer specific routine.. 5215.10 BogoMIPS (lpj=10430202)
Aug 21 00:43:45 xFLHCx kernel: [   27.121334] Security Framework initialized
Aug 21 00:43:45 xFLHCx kernel: [   27.121339] SELinux:  Disabled at boot.
Aug 21 00:43:45 xFLHCx kernel: [   27.121351] AppArmor: AppArmor initialized
Aug 21 00:43:45 xFLHCx kernel: [   27.121354] Failure registering capabilities with primary security module.
Aug 21 00:43:45 xFLHCx kernel: [   27.121360] Mount-cache hash table entries: 512
Aug 21 00:43:45 xFLHCx kernel: [   27.121454] Initializing cgroup subsys ns
Aug 21 00:43:45 xFLHCx kernel: [   27.121456] Initializing cgroup subsys cpuacct
Aug 21 00:43:45 xFLHCx kernel: [   27.121464] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
Aug 21 00:43:45 xFLHCx kernel: [   27.121471] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Aug 21 00:43:45 xFLHCx kernel: [   27.121473] CPU: L2 Cache: 512K (64 bytes/line)
Aug 21 00:43:45 xFLHCx kernel: [   27.121475] CPU 0(2) -> Core 0
Aug 21 00:43:45 xFLHCx kernel: [   27.121476] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f 00000000
Aug 21 00:43:45 xFLHCx kernel: [   27.121484] Compat vDSO mapped to ffffe000.
Aug 21 00:43:45 xFLHCx kernel: [   27.121493] Checking 'hlt' instruction... OK.
Aug 21 00:43:45 xFLHCx kernel: [   27.137509] SMP alternatives: switching to UP code
Aug 21 00:43:45 xFLHCx kernel: [   27.138487] Early unpacking initramfs... done
Aug 21 00:43:45 xFLHCx kernel: [   27.383839] ACPI: Core revision 20070126
Aug 21 00:43:45 xFLHCx kernel: [   27.383887] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 21 00:43:45 xFLHCx kernel: [   27.397026] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ stepping 02
Aug 21 00:43:45 xFLHCx kernel: [   27.397041] SMP alternatives: switching to SMP code
Aug 21 00:43:45 xFLHCx kernel: [   27.397372] Booting processor 1/1 eip 3000
Aug 21 00:43:45 xFLHCx kernel: [   27.407305] Initializing CPU#1
Aug 21 00:43:45 xFLHCx kernel: [   27.484346] Calibrating delay using timer specific routine.. 5211.17 BogoMIPS (lpj=10422347)
Aug 21 00:43:45 xFLHCx kernel: [   27.484351] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
Aug 21 00:43:45 xFLHCx kernel: [   27.484356] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Aug 21 00:43:45 xFLHCx kernel: [   27.484358] CPU: L2 Cache: 512K (64 bytes/line)
Aug 21 00:43:45 xFLHCx kernel: [   27.484360] CPU 1(2) -> Core 1
Aug 21 00:43:45 xFLHCx kernel: [   27.484361] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f 00000000
Aug 21 00:43:45 xFLHCx kernel: [   27.484548] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ stepping 02
Aug 21 00:43:45 xFLHCx kernel: [   27.484560] Total of 2 processors activated (10426.27 BogoMIPS).
Aug 21 00:43:45 xFLHCx kernel: [   27.484864] ENABLING IO-APIC IRQs
Aug 21 00:43:45 xFLHCx kernel: [   27.485083] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 21 00:43:45 xFLHCx kernel: [   27.632086] Brought up 2 CPUs
Aug 21 00:43:45 xFLHCx kernel: [   27.632137] CPU0 attaching sched-domain:
Aug 21 00:43:45 xFLHCx kernel: [   27.632139]  domain 0: span 03
Aug 21 00:43:45 xFLHCx kernel: [   27.632141]   groups: 01 02
Aug 21 00:43:45 xFLHCx kernel: [   27.632143] CPU1 attaching sched-domain:
Aug 21 00:43:45 xFLHCx kernel: [   27.632144]  domain 0: span 03
Aug 21 00:43:45 xFLHCx kernel: [   27.632146]   groups: 02 01
Aug 21 00:43:45 xFLHCx kernel: [   27.632298] net_namespace: 64 bytes
Aug 21 00:43:45 xFLHCx kernel: [   27.632304] Booting paravirtualized kernel on bare hardware
Aug 21 00:43:45 xFLHCx kernel: [   27.632632] Time:  0:43:12  Date: 08/21/08
Aug 21 00:43:45 xFLHCx kernel: [   27.632651] NET: Registered protocol family 16
Aug 21 00:43:45 xFLHCx kernel: [   27.632785] EISA bus registered
Aug 21 00:43:45 xFLHCx kernel: [   27.632788] ACPI: bus type pci registered
Aug 21 00:43:45 xFLHCx kernel: [   27.633755] PCI: PCI BIOS revision 3.00 entry at 0xfb3f0, last bus=3
Aug 21 00:43:45 xFLHCx kernel: [   27.633756] PCI: Using configuration type 1
Aug 21 00:43:45 xFLHCx kernel: [   27.633765] Setting up standard PCI resources
Aug 21 00:43:45 xFLHCx kernel: [   27.637243] ACPI: EC: Look up EC in DSDT
Aug 21 00:43:45 xFLHCx kernel: [   27.641075] ACPI: Interpreter enabled
Aug 21 00:43:45 xFLHCx kernel: [   27.641080] ACPI: (supports S0 S1 S4 S5)
Aug 21 00:43:45 xFLHCx kernel: [   27.641093] ACPI: Using IOAPIC for interrupt routing
Aug 21 00:43:45 xFLHCx kernel: [   27.644883] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 21 00:43:45 xFLHCx kernel: [   27.645069] pci 0000:00:11.0: set SATA to AHCI mode
Aug 21 00:43:45 xFLHCx kernel: [   27.646134] PCI: Transparent bridge - 0000:00:14.4
Aug 21 00:43:45 xFLHCx kernel: [   27.646156] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 21 00:43:45 xFLHCx kernel: [   27.646359] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
Aug 21 00:43:45 xFLHCx kernel: [   27.646440] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
Aug 21 00:43:45 xFLHCx kernel: [   27.646507] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
Aug 21 00:43:45 xFLHCx kernel: [   27.658780] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 21 00:43:45 xFLHCx kernel: [   27.658859] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 21 00:43:45 xFLHCx kernel: [   27.658936] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 21 00:43:45 xFLHCx kernel: [   27.659013] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 21 00:43:45 xFLHCx kernel: [   27.659092] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 21 00:43:45 xFLHCx kernel: [   27.659169] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 21 00:43:45 xFLHCx kernel: [   27.659247] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 21 00:43:45 xFLHCx kernel: [   27.659324] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 21 00:43:45 xFLHCx kernel: [   27.659416] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug 21 00:43:45 xFLHCx kernel: [   27.659437] pnp: PnP ACPI init
Aug 21 00:43:45 xFLHCx kernel: [   27.659442] ACPI: bus type pnp registered
Aug 21 00:43:45 xFLHCx kernel: [   27.661790] pnp: PnP ACPI: found 15 devices
Aug 21 00:43:45 xFLHCx kernel: [   27.661792] ACPI: ACPI bus type pnp unregistered
Aug 21 00:43:45 xFLHCx kernel: [   27.661795] PnPBIOS: Disabled by ACPI PNP
Aug 21 00:43:45 xFLHCx kernel: [   27.661949] PCI: Using ACPI for IRQ routing
Aug 21 00:43:45 xFLHCx kernel: [   27.661951] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug 21 00:43:45 xFLHCx kernel: [   27.661960] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
Aug 21 00:43:45 xFLHCx kernel: [   27.735742] NET: Registered protocol family 8
Aug 21 00:43:45 xFLHCx kernel: [   27.735744] NET: Registered protocol family 20
Aug 21 00:43:45 xFLHCx kernel: [   27.735771] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Aug 21 00:43:45 xFLHCx kernel: [   27.735775] hpet0: 4 32-bit timers, 14318180 Hz
Aug 21 00:43:45 xFLHCx kernel: [   27.736808] AppArmor: AppArmor Filesystem Enabled
Aug 21 00:43:45 xFLHCx kernel: [   27.739727] Time: hpet clocksource has been installed.
Aug 21 00:43:45 xFLHCx kernel: [   27.739740] Switched to high resolution mode on CPU 0
Aug 21 00:43:45 xFLHCx kernel: [   27.739790] Switched to high resolution mode on CPU 1
Aug 21 00:43:45 xFLHCx kernel: [   27.747703] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747706] system 00:01: ioport range 0x220-0x225 has been reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747708] system 00:01: ioport range 0x290-0x294 has been reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747712] system 00:02: ioport range 0x4100-0x411f has been reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747714] system 00:02: ioport range 0x228-0x22f has been reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747715] system 00:02: ioport range 0x238-0x23f has been reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747717] system 00:02: ioport range 0x40b-0x40b has been reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747719] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747721] system 00:02: ioport range 0xc00-0xc01 has been reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747723] system 00:02: ioport range 0xc14-0xc14 has been reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747725] system 00:02: ioport range 0xc50-0xc52 has been reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747727] system 00:02: ioport range 0xc6c-0xc6d has been reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747729] system 00:02: ioport range 0xc6f-0xc6f has been reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747731] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747733] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747735] system 00:02: ioport range 0xcd4-0xcdf has been reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747737] system 00:02: ioport range 0x4000-0x40fe has been reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747739] system 00:02: ioport range 0x4210-0x4217 has been reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747741] system 00:02: ioport range 0xb00-0xb0f has been reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747743] system 00:02: ioport range 0xb10-0xb1f has been reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747745] system 00:02: ioport range 0xb20-0xb3f has been reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747752] system 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747756] system 00:0e: iomem range 0xcf600-0xcffff has been reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747758] system 00:0e: iomem range 0xf0000-0xf7fff could not be reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747760] system 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747762] system 00:0e: iomem range 0xfc000-0xfffff could not be reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747764] system 00:0e: iomem range 0x3fee0000-0x3fefffff could not be reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747766] system 00:0e: iomem range 0xffff0000-0xffffffff could not be reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747769] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747770] system 00:0e: iomem range 0x100000-0x3fedffff could not be reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747772] system 00:0e: iomem range 0x0-0x0 could not be reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747774] system 00:0e: iomem range 0xfec00000-0xfec00fff could not be reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747777] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.747779] system 00:0e: iomem range 0xfff80000-0xfffeffff could not be reserved
Aug 21 00:43:45 xFLHCx kernel: [   27.778006] PCI: Bridge: 0000:00:02.0
Aug 21 00:43:45 xFLHCx kernel: [   27.778008]   IO window: e000-efff
Aug 21 00:43:45 xFLHCx kernel: [   27.778011]   MEM window: fdf00000-fdffffff
Aug 21 00:43:45 xFLHCx kernel: [   27.778013]   PREFETCH window: d0000000-dfffffff
Aug 21 00:43:45 xFLHCx kernel: [   27.778016] PCI: Bridge: 0000:00:0a.0
Aug 21 00:43:45 xFLHCx kernel: [   27.778017]   IO window: d000-dfff
Aug 21 00:43:45 xFLHCx kernel: [   27.778020]   MEM window: fde00000-fdefffff
Aug 21 00:43:45 xFLHCx kernel: [   27.778022]   PREFETCH window: fdb00000-fdbfffff
Aug 21 00:43:45 xFLHCx kernel: [   27.778024] PCI: Bridge: 0000:00:14.4
Aug 21 00:43:45 xFLHCx kernel: [   27.778026]   IO window: c000-cfff
Aug 21 00:43:45 xFLHCx kernel: [   27.778031]   MEM window: fdd00000-fddfffff
Aug 21 00:43:45 xFLHCx kernel: [   27.778035]   PREFETCH window: fdc00000-fdcfffff
Aug 21 00:43:45 xFLHCx kernel: [   27.778053] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 18 (level, low) -> IRQ 16
Aug 21 00:43:45 xFLHCx kernel: [   27.778057] PCI: Setting latency timer of device 0000:00:02.0 to 64
Aug 21 00:43:45 xFLHCx kernel: [   27.778065] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 16
Aug 21 00:43:45 xFLHCx kernel: [   27.778068] PCI: Setting latency timer of device 0000:00:0a.0 to 64
Aug 21 00:43:45 xFLHCx kernel: [   27.778082] NET: Registered protocol family 2
Aug 21 00:43:45 xFLHCx kernel: [   27.815561] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 21 00:43:45 xFLHCx kernel: [   27.815784] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 21 00:43:45 xFLHCx kernel: [   27.816502] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 21 00:43:45 xFLHCx kernel: [   27.816875] TCP: Hash tables configured (established 131072 bind 65536)
Aug 21 00:43:45 xFLHCx kernel: [   27.816877] TCP reno registered
Aug 21 00:43:45 xFLHCx kernel: [   27.827581] checking if image is initramfs... it is
Aug 21 00:43:45 xFLHCx kernel: [   28.304579] Freeing initrd memory: 7700k freed
Aug 21 00:43:45 xFLHCx kernel: [   28.305192] audit: initializing netlink socket (disabled)
Aug 21 00:43:45 xFLHCx kernel: [   28.305204] audit(1219279392.152:1): initialized
Aug 21 00:43:45 xFLHCx kernel: [   28.305328] highmem bounce pool size: 64 pages
Aug 21 00:43:45 xFLHCx kernel: [   28.306759] VFS: Disk quotas dquot_6.5.1
Aug 21 00:43:45 xFLHCx kernel: [   28.306811] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 21 00:43:45 xFLHCx kernel: [   28.306901] io scheduler noop registered
Aug 21 00:43:45 xFLHCx kernel: [   28.306903] io scheduler anticipatory registered
Aug 21 00:43:45 xFLHCx kernel: [   28.306904] io scheduler deadline registered
Aug 21 00:43:45 xFLHCx kernel: [   28.306911] io scheduler cfq registered (default)
Aug 21 00:43:45 xFLHCx kernel: [   29.132048] 0000:00:13.0 OHCI: BIOS handoff failed (BIOS bug ?) 00000184
Aug 21 00:43:45 xFLHCx kernel: [   29.215841] Boot video device is 0000:01:00.0
Aug 21 00:43:45 xFLHCx kernel: [   29.215964] PCI: Setting latency timer of device 0000:00:02.0 to 64
Aug 21 00:43:45 xFLHCx kernel: [   29.215985] assign_interrupt_mode Found MSI capability
Aug 21 00:43:45 xFLHCx kernel: [   29.216007] Allocate Port Service[0000:00:02.0:pcie00]
Aug 21 00:43:45 xFLHCx kernel: [   29.216064] PCI: Setting latency timer of device 0000:00:0a.0 to 64
Aug 21 00:43:45 xFLHCx kernel: [   29.216084] assign_interrupt_mode Found MSI capability
Aug 21 00:43:45 xFLHCx kernel: [   29.216102] Allocate Port Service[0000:00:0a.0:pcie00]
Aug 21 00:43:45 xFLHCx kernel: [   29.216277] isapnp: Scanning for PnP cards...
Aug 21 00:43:45 xFLHCx kernel: [   29.569210] isapnp: No Plug & Play device found
Aug 21 00:43:45 xFLHCx kernel: [   29.590619] Real Time Clock Driver v1.12ac
Aug 21 00:43:45 xFLHCx kernel: [   29.590773] hpet_resources: 0xfed00000 is busy
Aug 21 00:43:45 xFLHCx kernel: [   29.590802] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug 21 00:43:45 xFLHCx kernel: [   29.591202] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug 21 00:43:45 xFLHCx kernel: [   29.591719] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug 21 00:43:45 xFLHCx kernel: [   29.592340] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug 21 00:43:45 xFLHCx kernel: [   29.592390] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug 21 00:43:45 xFLHCx kernel: [   29.592465] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Aug 21 00:43:45 xFLHCx kernel: [   29.592823] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 21 00:43:45 xFLHCx kernel: [   29.592828] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 21 00:43:45 xFLHCx kernel: [   29.607849] mice: PS/2 mouse device common for all mice
Aug 21 00:43:45 xFLHCx kernel: [   29.607945] EISA: Probing bus 0 at eisa.0
Aug 21 00:43:45 xFLHCx kernel: [   29.607963] Cannot allocate resource for EISA slot 4
Aug 21 00:43:45 xFLHCx kernel: [   29.607980] EISA: Detected 0 cards.
Aug 21 00:43:45 xFLHCx kernel: [   29.607982] cpuidle: using governor ladder
Aug 21 00:43:45 xFLHCx kernel: [   29.607984] cpuidle: using governor menu
Aug 21 00:43:45 xFLHCx kernel: [   29.608049] NET: Registered protocol family 1
Aug 21 00:43:45 xFLHCx kernel: [   29.608071] Using IPI No-Shortcut mode
Aug 21 00:43:45 xFLHCx kernel: [   29.608100] registered taskstats version 1
Aug 21 00:43:45 xFLHCx kernel: [   29.608188]   Magic number: 4:271:709
Aug 21 00:43:45 xFLHCx kernel: [   29.608316] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 21 00:43:45 xFLHCx kernel: [   29.608317] EDD information not available.
Aug 21 00:43:45 xFLHCx kernel: [   29.608530] Freeing unused kernel memory: 368k freed
Aug 21 00:43:45 xFLHCx kernel: [   29.646728] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Aug 21 00:43:45 xFLHCx kernel: [   30.792621] fuse init (API version 7.9)
Aug 21 00:43:45 xFLHCx kernel: [   30.808141] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 21 00:43:45 xFLHCx kernel: [   30.808151] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 21 00:43:45 xFLHCx kernel: [   30.994740] SCSI subsystem initialized
Aug 21 00:43:45 xFLHCx kernel: [   31.017898] r8169 Gigabit Ethernet driver 2.2LK loaded
Aug 21 00:43:45 xFLHCx kernel: [   31.017923] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 16
Aug 21 00:43:45 xFLHCx kernel: [   31.017940] PCI: Setting latency timer of device 0000:02:00.0 to 64
Aug 21 00:43:45 xFLHCx kernel: [   31.018153] eth0: RTL8168c/8111c at 0xf8844000, 00:1f:d0:5a:fd:e7, XID 3c4000c0 IRQ 221
Aug 21 00:43:45 xFLHCx kernel: [   31.025321] libata version 3.00 loaded.
Aug 21 00:43:45 xFLHCx kernel: [   31.034458] ahci 0000:00:11.0: version 3.0
Aug 21 00:43:45 xFLHCx kernel: [   31.034494] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 22 (level, low) -> IRQ 17
Aug 21 00:43:45 xFLHCx kernel: [   31.034545] ahci 0000:00:11.0: controller can't do PMP, turning off CAP_PMP
Aug 21 00:43:45 xFLHCx kernel: [   31.102169] usbcore: registered new interface driver usbfs
Aug 21 00:43:45 xFLHCx kernel: [   31.102187] usbcore: registered new interface driver hub
Aug 21 00:43:45 xFLHCx kernel: [   31.102519] usbcore: registered new device driver usb
Aug 21 00:43:45 xFLHCx kernel: [   31.103300] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 21 00:43:45 xFLHCx kernel: [   31.202145] Floppy drive(s): fd0 is 1.44M
Aug 21 00:43:45 xFLHCx kernel: [   31.222383] FDC 0 is a post-1991 82077
Aug 21 00:43:45 xFLHCx kernel: [   32.032470] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Aug 21 00:43:45 xFLHCx kernel: [   32.032474] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pio slum part 
Aug 21 00:43:45 xFLHCx kernel: [   32.032807] scsi0 : ahci
Aug 21 00:43:45 xFLHCx kernel: [   32.033043] scsi1 : ahci
Aug 21 00:43:45 xFLHCx kernel: [   32.033147] scsi2 : ahci
Aug 21 00:43:45 xFLHCx kernel: [   32.033247] scsi3 : ahci
Aug 21 00:43:45 xFLHCx kernel: [   32.033303] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 220
Aug 21 00:43:45 xFLHCx kernel: [   32.033306] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 220
Aug 21 00:43:45 xFLHCx kernel: [   32.033309] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 220
Aug 21 00:43:45 xFLHCx kernel: [   32.033312] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 220
Aug 21 00:43:45 xFLHCx kernel: [   32.507195] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 21 00:43:45 xFLHCx kernel: [   32.676711] ata1.00: ATAPI: LITE-ON DVDRW LH-20A1L, BL06, max UDMA/100, ATAPI AN
Aug 21 00:43:45 xFLHCx kernel: [   32.843338] ata1.00: configured for UDMA/100
Aug 21 00:43:45 xFLHCx kernel: [   33.154487] ata2: SATA link down (SStatus 0 SControl 300)
Aug 21 00:43:45 xFLHCx kernel: [   33.465668] ata3: SATA link down (SStatus 0 SControl 300)
Aug 21 00:43:45 xFLHCx kernel: [   33.775859] ata4: SATA link down (SStatus 0 SControl 300)
Aug 21 00:43:45 xFLHCx kernel: [   33.776983] scsi 0:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1L   BL06 PQ: 0 ANSI: 5
Aug 21 00:43:45 xFLHCx kernel: [   33.777891] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18

Aug 21 00:43:45 xFLHCx kernel: [   33.778665] scsi4 : pata_atiixp
Aug 21 00:43:45 xFLHCx kernel: [   33.779076] scsi5 : pata_atiixp
Aug 21 00:43:45 xFLHCx kernel: [   33.779644] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
Aug 21 00:43:45 xFLHCx kernel: [   33.779646] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
Aug 21 00:43:45 xFLHCx kernel: [   33.785994] Driver 'sr' needs updating - please use bus_type methods
Aug 21 00:43:45 xFLHCx kernel: [   33.801128] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Aug 21 00:43:45 xFLHCx kernel: [   33.801133] Uniform CD-ROM driver Revision: 3.20
Aug 21 00:43:45 xFLHCx kernel: [   33.801174] sr 0:0:0:0: Attached scsi CD-ROM sr0
Aug 21 00:43:45 xFLHCx kernel: [   33.805821] sr 0:0:0:0: Attached scsi generic sg0 type 5
Aug 21 00:43:45 xFLHCx kernel: [   33.960787] ata5.00: HPA unlocked: 117229295 -> 117231408, native 117231408
Aug 21 00:43:45 xFLHCx kernel: [   33.960792] ata5.00: ATA-5: WDC WD600BB-00CAA1, 17.07W17, max UDMA/100
Aug 21 00:43:45 xFLHCx kernel: [   33.960794] ata5.00: 117231408 sectors, multi 16: LBA 
Aug 21 00:43:45 xFLHCx kernel: [   33.961707] ata5.01: ATA-5: WDC WD200BB-60AUA1, 18.20D18, max UDMA/100
Aug 21 00:43:45 xFLHCx kernel: [   33.961709] ata5.01: 39102336 sectors, multi 16: LBA 
Aug 21 00:43:45 xFLHCx kernel: [   33.976839] ata5.00: configured for UDMA/100
Aug 21 00:43:45 xFLHCx kernel: [   33.993598] ata5.01: configured for UDMA/100
Aug 21 00:43:45 xFLHCx kernel: [   34.158067] scsi 4:0:0:0: Direct-Access     ATA      WDC WD600BB-00CA 17.0 PQ: 0 ANSI: 5
Aug 21 00:43:45 xFLHCx kernel: [   34.158121] scsi 4:0:0:0: Attached scsi generic sg1 type 0
Aug 21 00:43:45 xFLHCx kernel: [   34.158448] scsi 4:0:1:0: Direct-Access     ATA      WDC WD200BB-60AU 18.2 PQ: 0 ANSI: 5
Aug 21 00:43:45 xFLHCx kernel: [   34.158488] scsi 4:0:1:0: Attached scsi generic sg2 type 0
Aug 21 00:43:45 xFLHCx kernel: [   34.159803] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 18
Aug 21 00:43:45 xFLHCx kernel: [   34.159814] ohci_hcd 0000:00:12.0: OHCI Host Controller
Aug 21 00:43:45 xFLHCx kernel: [   34.160060] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 1
Aug 21 00:43:45 xFLHCx kernel: [   34.160080] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfe02e000
Aug 21 00:43:45 xFLHCx kernel: [   34.218764] usb usb1: configuration #1 chosen from 1 choice
Aug 21 00:43:45 xFLHCx kernel: [   34.218782] hub 1-0:1.0: USB hub found
Aug 21 00:43:45 xFLHCx kernel: [   34.218790] hub 1-0:1.0: 3 ports detected
Aug 21 00:43:45 xFLHCx kernel: [   34.318499] ACPI: PCI Interrupt 0000:00:12.1[A] -> GSI 16 (level, low) -> IRQ 18
Aug 21 00:43:45 xFLHCx kernel: [   34.318513] ohci_hcd 0000:00:12.1: OHCI Host Controller
Aug 21 00:43:45 xFLHCx kernel: [   34.318528] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 2
Aug 21 00:43:45 xFLHCx kernel: [   34.318541] ohci_hcd 0000:00:12.1: irq 18, io mem 0xfe02d000
Aug 21 00:43:45 xFLHCx kernel: [   34.378327] usb usb2: configuration #1 chosen from 1 choice
Aug 21 00:43:45 xFLHCx kernel: [   34.378345] hub 2-0:1.0: USB hub found
Aug 21 00:43:45 xFLHCx kernel: [   34.378352] hub 2-0:1.0: 3 ports detected
Aug 21 00:43:45 xFLHCx kernel: [   34.478079] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 18 (level, low) -> IRQ 16
Aug 21 00:43:45 xFLHCx kernel: [   34.478090] ohci_hcd 0000:00:13.0: OHCI Host Controller
Aug 21 00:43:45 xFLHCx kernel: [   34.478110] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 3
Aug 21 00:43:45 xFLHCx kernel: [   34.478127] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02b000
Aug 21 00:43:45 xFLHCx kernel: [   34.537896] usb usb3: configuration #1 chosen from 1 choice
Aug 21 00:43:45 xFLHCx kernel: [   34.537912] hub 3-0:1.0: USB hub found
Aug 21 00:43:45 xFLHCx kernel: [   34.537919] hub 3-0:1.0: 3 ports detected
Aug 21 00:43:45 xFLHCx kernel: [   34.638638] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 18 (level, low) -> IRQ 16
Aug 21 00:43:45 xFLHCx kernel: [   34.638649] ohci_hcd 0000:00:13.1: OHCI Host Controller
Aug 21 00:43:45 xFLHCx kernel: [   34.638667] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 4
Aug 21 00:43:45 xFLHCx kernel: [   34.638678] ohci_hcd 0000:00:13.1: irq 16, io mem 0xfe02a000
Aug 21 00:43:45 xFLHCx kernel: [   34.697476] usb usb4: configuration #1 chosen from 1 choice
Aug 21 00:43:45 xFLHCx kernel: [   34.697494] hub 4-0:1.0: USB hub found
Aug 21 00:43:45 xFLHCx kernel: [   34.697501] hub 4-0:1.0: 3 ports detected
Aug 21 00:43:45 xFLHCx kernel: [   34.789197] usb 2-1: new full speed USB device using ohci_hcd and address 2
Aug 21 00:43:45 xFLHCx kernel: [   34.797226] ACPI: PCI Interrupt 0000:00:14.5[C] -> GSI 18 (level, low) -> IRQ 16
Aug 21 00:43:45 xFLHCx kernel: [   34.797236] ohci_hcd 0000:00:14.5: OHCI Host Controller
Aug 21 00:43:45 xFLHCx kernel: [   34.797251] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 5
Aug 21 00:43:45 xFLHCx kernel: [   34.797262] ohci_hcd 0000:00:14.5: irq 16, io mem 0xfe028000
Aug 21 00:43:45 xFLHCx kernel: [   34.858062] usb usb5: configuration #1 chosen from 1 choice
Aug 21 00:43:45 xFLHCx kernel: [   34.858077] hub 5-0:1.0: USB hub found
Aug 21 00:43:45 xFLHCx kernel: [   34.858084] hub 5-0:1.0: 2 ports detected
Aug 21 00:43:45 xFLHCx kernel: [   34.962076] ACPI: PCI Interrupt 0000:00:12.2[B] -> GSI 17 (level, low) -> IRQ 19
Aug 21 00:43:45 xFLHCx kernel: [   34.962090] ehci_hcd 0000:00:12.2: EHCI Host Controller
Aug 21 00:43:45 xFLHCx kernel: [   34.962111] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 6
Aug 21 00:43:45 xFLHCx kernel: [   34.962148] ehci_hcd 0000:00:12.2: debug port 1
Aug 21 00:43:45 xFLHCx kernel: [   34.962165] ehci_hcd 0000:00:12.2: irq 19, io mem 0xfe02c000
Aug 21 00:43:45 xFLHCx kernel: [   34.989661] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 21 00:43:45 xFLHCx kernel: [   34.989763] usb usb6: configuration #1 chosen from 1 choice
Aug 21 00:43:45 xFLHCx kernel: [   34.989781] hub 6-0:1.0: USB hub found
Aug 21 00:43:45 xFLHCx kernel: [   34.989786] hub 6-0:1.0: 6 ports detected
Aug 21 00:43:45 xFLHCx kernel: [   35.092483] ACPI: PCI Interrupt 0000:00:13.2[B] -> GSI 19 (level, low) -> IRQ 20
Aug 21 00:43:45 xFLHCx kernel: [   35.092497] ehci_hcd 0000:00:13.2: EHCI Host Controller
Aug 21 00:43:45 xFLHCx kernel: [   35.092516] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 7
Aug 21 00:43:45 xFLHCx kernel: [   35.092550] ehci_hcd 0000:00:13.2: debug port 1
Aug 21 00:43:45 xFLHCx kernel: [   35.092566] ehci_hcd 0000:00:13.2: irq 20, io mem 0xfe029000
Aug 21 00:43:45 xFLHCx kernel: [   35.105354] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 21 00:43:45 xFLHCx kernel: [   35.105419] usb usb7: configuration #1 chosen from 1 choice
Aug 21 00:43:45 xFLHCx kernel: [   35.105436] hub 7-0:1.0: USB hub found
Aug 21 00:43:45 xFLHCx kernel: [   35.105440] hub 7-0:1.0: 6 ports detected
Aug 21 00:43:45 xFLHCx kernel: [   35.208375] ACPI: PCI Interrupt 0000:03:0e.0[A] -> GSI 22 (level, low) -> IRQ 17
Aug 21 00:43:45 xFLHCx kernel: [   35.257973] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[fddff000-fddff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Aug 21 00:43:45 xFLHCx kernel: [   35.271819] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Aug 21 00:43:45 xFLHCx kernel: [   35.271824] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Aug 21 00:43:45 xFLHCx kernel: [   35.280555] Driver 'sd' needs updating - please use bus_type methods
Aug 21 00:43:45 xFLHCx kernel: [   35.280625] sd 4:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
Aug 21 00:43:45 xFLHCx kernel: [   35.280634] sd 4:0:0:0: [sda] Write Protect is off
Aug 21 00:43:45 xFLHCx kernel: [   35.280636] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 21 00:43:45 xFLHCx kernel: [   35.280647] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 21 00:43:45 xFLHCx kernel: [   35.280684] sd 4:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
Aug 21 00:43:45 xFLHCx kernel: [   35.280690] sd 4:0:0:0: [sda] Write Protect is off
Aug 21 00:43:45 xFLHCx kernel: [   35.280692] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 21 00:43:45 xFLHCx kernel: [   35.280701] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 21 00:43:45 xFLHCx kernel: [   35.280704]  sda: sda1 sda2 < sda5 >
Aug 21 00:43:45 xFLHCx kernel: [   35.314297] sd 4:0:0:0: [sda] Attached SCSI disk
Aug 21 00:43:45 xFLHCx kernel: [   35.314325] sd 4:0:1:0: [sdb] 39102336 512-byte hardware sectors (20020 MB)
Aug 21 00:43:45 xFLHCx kernel: [   35.314331] sd 4:0:1:0: [sdb] Write Protect is off
Aug 21 00:43:45 xFLHCx kernel: [   35.314333] sd 4:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Aug 21 00:43:45 xFLHCx kernel: [   35.314342] sd 4:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 21 00:43:45 xFLHCx kernel: [   35.314367] sd 4:0:1:0: [sdb] 39102336 512-byte hardware sectors (20020 MB)
Aug 21 00:43:45 xFLHCx kernel: [   35.314373] sd 4:0:1:0: [sdb] Write Protect is off
Aug 21 00:43:45 xFLHCx kernel: [   35.314375] sd 4:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Aug 21 00:43:45 xFLHCx kernel: [   35.314384] sd 4:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 21 00:43:45 xFLHCx kernel: [   35.314386]  sdb: sdb1 < sdb5 sdb6 >
Aug 21 00:43:45 xFLHCx kernel: [   35.365107] sd 4:0:1:0: [sdb] Attached SCSI disk
Aug 21 00:43:45 xFLHCx kernel: [   35.384631] usb 2-1: device not accepting address 2, error -62
Aug 21 00:43:45 xFLHCx kernel: [   35.807525] usb 6-4: new high speed USB device using ehci_hcd and address 2
Aug 21 00:43:45 xFLHCx kernel: [   35.848903] EXT3-fs: INFO: recovery required on readonly filesystem.
Aug 21 00:43:45 xFLHCx kernel: [   35.848906] EXT3-fs: write access will be enabled during recovery.
Aug 21 00:43:45 xFLHCx kernel: [   35.940519] usb 6-4: configuration #1 chosen from 1 choice
Aug 21 00:43:45 xFLHCx kernel: [   36.533681] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0072802500001fd0]
Aug 21 00:43:45 xFLHCx kernel: [   46.556531] kjournald starting.  Commit interval 5 seconds
Aug 21 00:43:45 xFLHCx kernel: [   46.556518] EXT3-fs: recovery complete.
Aug 21 00:43:45 xFLHCx kernel: [   46.557437] EXT3-fs: mounted filesystem with ordered data mode.
Aug 21 00:43:45 xFLHCx kernel: [   56.249192] input: PC Speaker as /devices/platform/pcspkr/input/input2
Aug 21 00:43:45 xFLHCx kernel: [   56.318869] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 21 00:43:45 xFLHCx kernel: [   56.332417] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 21 00:43:45 xFLHCx kernel: [   56.531807] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Aug 21 00:43:45 xFLHCx kernel: [   56.560145] input: Power Button (FF) as /devices/virtual/input/input3
Aug 21 00:43:45 xFLHCx kernel: [   56.615908] ACPI: Power Button (FF) [PWRF]
Aug 21 00:43:45 xFLHCx kernel: [   56.615962] input: Power Button (CM) as /devices/virtual/input/input4
Aug 21 00:43:45 xFLHCx kernel: [   56.679744] ACPI: Power Button (CM) [PWRB]
Aug 21 00:43:45 xFLHCx kernel: [   56.679929] ACPI: WMI-Acer: Mapper loaded
Aug 21 00:43:45 xFLHCx kernel: [   57.063170] Linux agpgart interface v0.102
Aug 21 00:43:45 xFLHCx kernel: [   57.213586] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Aug 21 00:43:45 xFLHCx kernel: [   57.274455] parport_pc 00:0a: reported by Plug and Play ACPI
Aug 21 00:43:45 xFLHCx kernel: [   57.274512] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Aug 21 00:43:45 xFLHCx kernel: [   57.492067] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 18
Aug 21 00:43:45 xFLHCx kernel: [   57.507448] usbcore: registered new interface driver cdc_ether
Aug 21 00:43:45 xFLHCx kernel: [   57.514614] usb 6-4: bad CDC descriptors
Aug 21 00:43:45 xFLHCx kernel: [   57.514629] usbcore: registered new interface driver rndis_host
Aug 21 00:43:45 xFLHCx kernel: [   57.524316] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
Aug 21 00:43:45 xFLHCx kernel: [   58.394153] lp0: using parport0 (interrupt-driven).
Aug 21 00:43:45 xFLHCx kernel: [   59.024401] EXT3 FS on sdb6, internal journal
Aug 21 00:43:45 xFLHCx kernel: [   59.996546] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 21 00:43:45 xFLHCx kernel: [   60.331918] No dock devices found.
Aug 21 00:43:45 xFLHCx kernel: [   60.637528] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ processors (2 cpu cores) (version 2.20.00)
Aug 21 00:43:45 xFLHCx kernel: [   60.637604] powernow-k8:    0 : fid 0x12 (2600 MHz), vid 0x9
Aug 21 00:43:45 xFLHCx kernel: [   60.637607] powernow-k8:    1 : fid 0x10 (2400 MHz), vid 0xb
Aug 21 00:43:45 xFLHCx kernel: [   60.637609] powernow-k8:    2 : fid 0xe (2200 MHz), vid 0xd
Aug 21 00:43:45 xFLHCx kernel: [   60.637611] powernow-k8:    3 : fid 0xc (2000 MHz), vid 0xf
Aug 21 00:43:45 xFLHCx kernel: [   60.637612] powernow-k8:    4 : fid 0xa (1800 MHz), vid 0x11
Aug 21 00:43:45 xFLHCx kernel: [   60.637614] powernow-k8:    5 : fid 0x2 (1000 MHz), vid 0x12
Aug 21 00:43:45 xFLHCx NetworkManager: <info>  starting... 
Aug 21 00:43:45 xFLHCx avahi-daemon[5130]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Aug 21 00:43:45 xFLHCx avahi-daemon[5130]: Successfully dropped root privileges.
Aug 21 00:43:45 xFLHCx avahi-daemon[5130]: avahi-daemon 0.6.22 starting up.
Aug 21 00:43:45 xFLHCx avahi-daemon[5130]: Successfully called chroot().
Aug 21 00:43:45 xFLHCx avahi-daemon[5130]: Successfully dropped remaining capabilities.
Aug 21 00:43:45 xFLHCx avahi-daemon[5130]: No service file found in /etc/avahi/services.
Aug 21 00:43:45 xFLHCx avahi-daemon[5130]: Network interface enumeration completed.
Aug 21 00:43:45 xFLHCx avahi-daemon[5130]: Registering HINFO record with values 'I686'/'LINUX'.
Aug 21 00:43:45 xFLHCx avahi-daemon[5130]: Server startup complete. Host name is xFLHCx.local. Local service cookie is 1868593661.
Aug 21 00:43:45 xFLHCx kernel: [   61.218861] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Aug 21 00:43:45 xFLHCx kernel: [   61.218866] apm: disabled - APM is not SMP safe.
Aug 21 00:43:46 xFLHCx kernel: [   61.330853] ppdev: user-space parallel port driver
Aug 21 00:43:46 xFLHCx kernel: [   61.512115] audit(1219293826.223:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5172 profile="/usr/sbin/cupsd" namespace="default"
Aug 21 00:43:46 xFLHCx dhcdbd: Started up.
Aug 21 00:43:47 xFLHCx kernel: [   62.440344] r8169: eth0: link down
Aug 21 00:43:47 xFLHCx NetworkManager: <info>  eth0: Device is fully-supported using driver 'r8169'. 
Aug 21 00:43:47 xFLHCx NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Aug 21 00:43:47 xFLHCx NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Aug 21 00:43:47 xFLHCx NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Aug 21 00:43:47 xFLHCx NetworkManager: <info>  Deactivating device eth0. 
Aug 21 00:43:47 xFLHCx NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Aug 21 00:43:47 xFLHCx NetworkManager: <debug> [1219293827.179635] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVDRW_LH_20A1L'). 
Aug 21 00:43:47 xFLHCx hcid[5402]: Bluetooth HCI daemon
Aug 21 00:43:47 xFLHCx kernel: [   62.530746] Bluetooth: Core ver 2.11
Aug 21 00:43:47 xFLHCx kernel: [   62.531044] NET: Registered protocol family 31
Aug 21 00:43:47 xFLHCx kernel: [   62.531046] Bluetooth: HCI device and connection manager initialized
Aug 21 00:43:47 xFLHCx kernel: [   62.531049] Bluetooth: HCI socket layer initialized
Aug 21 00:43:47 xFLHCx hcid[5402]: Starting SDP server
Aug 21 00:43:47 xFLHCx kernel: [   62.544813] Bluetooth: L2CAP ver 2.9
Aug 21 00:43:47 xFLHCx kernel: [   62.544818] Bluetooth: L2CAP socket layer initialized
Aug 21 00:43:47 xFLHCx hcid[5402]: Created local server at unix:abstract=/var/run/dbus-IuTpfqRbzu,guid=ee29df6953ff9fb13373ba7548acf283
Aug 21 00:43:47 xFLHCx NetworkManager: <debug> [1219293827.282694] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Aug 21 00:43:47 xFLHCx audio[5420]: Bluetooth Audio daemon
Aug 21 00:43:47 xFLHCx audio[5420]: Unix socket created: 5
Aug 21 00:43:47 xFLHCx audio[5420]: audio.conf: Key file does not have key 'Enable'
Aug 21 00:43:47 xFLHCx audio[5420]: audio.conf: Key file does not have key 'Disable'
Aug 21 00:43:47 xFLHCx kernel: [   62.604733] Bluetooth: RFCOMM socket layer initialized
Aug 21 00:43:47 xFLHCx kernel: [   62.604748] Bluetooth: RFCOMM TTY layer initialized
Aug 21 00:43:47 xFLHCx kernel: [   62.604749] Bluetooth: RFCOMM ver 1.8
Aug 21 00:43:47 xFLHCx input[5421]: Bluetooth Input daemon
Aug 21 00:43:47 xFLHCx input[5421]: Registered input manager path:/org/bluez/input
Aug 21 00:43:47 xFLHCx audio[5420]: add_service_record: got record id 0x10000
Aug 21 00:43:47 xFLHCx audio[5420]: audio.conf: Key file does not have key 'Disable'
Aug 21 00:43:47 xFLHCx audio[5420]: audio.conf: Key file does not have group 'A2DP'
Aug 21 00:43:47 xFLHCx last message repeated 3 times
Aug 21 00:43:47 xFLHCx audio[5420]: SEP 0x806d748 registered: type:0 codec:0 seid:1
Aug 21 00:43:47 xFLHCx audio[5420]: add_service_record: got record id 0x10001
Aug 21 00:43:47 xFLHCx audio[5420]: add_service_record: got record id 0x10002
Aug 21 00:43:47 xFLHCx audio[5420]: add_service_record: got record id 0x10003
Aug 21 00:43:47 xFLHCx audio[5420]: Registered manager path:/org/bluez/audio
Aug 21 00:43:47 xFLHCx kernel: [   62.956202] Clocksource tsc unstable (delta = -107064201 ns)
Aug 21 00:43:49 xFLHCx kernel: [   63.998750] [drm] Initialized drm 1.1.0 20060810
Aug 21 00:43:50 xFLHCx anacron[5513]: Anacron 2.3 started on 2008-08-21
Aug 21 00:43:50 xFLHCx anacron[5513]: Will run job `cron.daily' in 5 min.
Aug 21 00:43:50 xFLHCx anacron[5513]: Will run job `cron.weekly' in 10 min.
Aug 21 00:43:50 xFLHCx anacron[5513]: Will run job `cron.monthly' in 15 min.
Aug 21 00:43:50 xFLHCx anacron[5513]: Jobs will be executed sequentially
Aug 21 00:43:50 xFLHCx /usr/sbin/cron[5540]: (CRON) INFO (pidfile fd = 3)
Aug 21 00:43:50 xFLHCx /usr/sbin/cron[5541]: (CRON) STARTUP (fork ok)
Aug 21 00:43:50 xFLHCx /usr/sbin/cron[5541]: (CRON) INFO (Running @reboot jobs)
Aug 21 00:43:56 xFLHCx kernel: [   66.534106] hda-intel: Invalid position buffer, using LPIB read method instead.
Aug 21 00:44:25 xFLHCx kernel: [   78.519304] NET: Registered protocol family 10
Aug 21 00:44:25 xFLHCx kernel: [   78.519466] lo: Disabled Privacy Extensions
Aug 21 00:44:25 xFLHCx kernel: [   78.519718] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 21 00:44:28 xFLHCx hcid[5402]: Default passkey agent (:1.20, /org/bluez/passkey) registered
Aug 21 00:44:28 xFLHCx hcid[5402]: Default authorization agent (:1.20, /org/bluez/auth) registered
Aug 21 00:44:32 xFLHCx NetworkManager: <info>  Updating allowed wireless network lists. 
Aug 21 00:44:32 xFLHCx NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Aug 21 00:48:50 xFLHCx anacron[5513]: Job `cron.daily' started
Aug 21 00:48:50 xFLHCx anacron[5928]: Updated timestamp for job `cron.daily' to 2008-08-21

```



sorry. forgot to add the rest too.

```
christian@xFLHCx:~$ sudo ndiswrapper -l
[sudo] password for christian: 
wusb54gs : driver installed
	device (13B1:000E) present
christian@xFLHCx:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 13b1:000e Linksys 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
christian@xFLHCx:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



```

---

### Post by xFLHCx on 2008-08-27
is there anyone that can help me out?

This the only deterrent from me using ubuntu full on. I've been trying for about 2 months to get this to work now.

---

### Post by javaJake on 2008-08-29
Sorry, somehow I missed your messages in the busy shuffle of life. I've just happened to stumble on your messages right now.

Unfortunately, your system doesn't look healthy. Your experiencing kernel (the core of Linux) crashes whenever the device is plugged in. From my experience, this usually happens due to overzealous attempts to get things working. I highly recommend you reinstall Ubuntu to flush out any clogged drains in the system and try this HOWTO again.

A word to the wise, if someone tells you to run a command with "make" or "dpkg" in it, question whether or not you want to take the risks. (You'll notice this HOWTO actually uses "make", but in fact the changes it produces are very minor and very easy to reverse. Otherwise, I wouldn't have written that in the HOWTO.)

---

### Post by xFLHCx on 2008-08-29
Still nothing even with a fresh install.

after editing the custom rules file and unplugging and replugging the device, my light doesnt blink slowly anymore.

could it be because i have windows installed on a separate harddrive?  when I just started windows up, it said there was a address violation dealing with my linksys adapter.


```
Aug 29 18:49:18 xFLHCx syslogd 1.5.0#1ubuntu1: restart.
Aug 29 18:49:18 xFLHCx kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug 29 18:49:18 xFLHCx kernel: Loaded 27883 symbols from /boot/System.map-2.6.24-19-generic.
Aug 29 18:49:18 xFLHCx kernel: Symbols match kernel version 2.6.24.
Aug 29 18:49:18 xFLHCx kernel: Loaded 16772 symbols from 81 modules.
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 29 18:49:18 xFLHCx kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fee0000 (usable)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000]  BIOS-e820: 000000003fee0000 - 000000003fee3000 (ACPI NVS)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000]  BIOS-e820: 000000003fee3000 - 000000003fef0000 (ACPI data)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000]  BIOS-e820: 000000003fef0000 - 000000003ff00000 (reserved)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] 126MB HIGHMEM available.
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] 896MB LOWMEM available.
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] found SMP MP-table at 000f5740
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] Entering add_active_range(0, 0, 261856) 0 entries of 256 used
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] Zone PFN ranges:
Aug 29 18:49:18 xFLHCx kernel: [    0.000000]   DMA             0 ->     4096
Aug 29 18:49:18 xFLHCx kernel: [    0.000000]   Normal       4096 ->   229376
Aug 29 18:49:18 xFLHCx kernel: [    0.000000]   HighMem    229376 ->   261856
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] Movable zone start PFN for each node
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug 29 18:49:18 xFLHCx kernel: [    0.000000]     0:        0 ->   261856
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] On node 0 totalpages: 261856
Aug 29 18:49:18 xFLHCx kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 29 18:49:18 xFLHCx kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 29 18:49:18 xFLHCx kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 29 18:49:18 xFLHCx kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug 29 18:49:18 xFLHCx kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug 29 18:49:18 xFLHCx kernel: [    0.000000]   HighMem zone: 253 pages used for memmap
Aug 29 18:49:18 xFLHCx kernel: [    0.000000]   HighMem zone: 32227 pages, LIFO batch:7
Aug 29 18:49:18 xFLHCx kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] DMI 2.4 present.
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7090 checksum 0
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: RSDP 000F7090, 0014 (r0 GBT   )
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: RSDT 3FEE3000, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: FACP 3FEE3040, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: DSDT 3FEE30C0, 6550 (r1 GBT    GBTUACPI     1000 MSFT  3000000)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: FACS 3FEE0000, 0040
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: SSDT 3FEE9700, 028A (r1 PTLTD  POWERNOW        1  LTP        1)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: HPET 3FEE99C0, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: MCFG 3FEE9A00, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: APIC 3FEE9640, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] Processor #0 15:11 APIC version 16
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] Processor #1 15:11 APIC version 16
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:a0100000)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259811
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] Kernel command line: root=UUID=c3c999a3-8421-4838-aef5-25515436b58d ro quiet splash
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] Initializing CPU#0
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug 29 18:49:18 xFLHCx kernel: [    0.000000] Detected 2605.782 MHz processor.
Aug 29 18:49:18 xFLHCx kernel: [   20.053683] Console: colour VGA+ 80x25
Aug 29 18:49:18 xFLHCx kernel: [   20.053685] console [tty0] enabled
Aug 29 18:49:18 xFLHCx kernel: [   20.054014] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 29 18:49:18 xFLHCx kernel: [   20.054333] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 29 18:49:18 xFLHCx kernel: [   20.072904] Memory: 1025912k/1047424k available (2177k kernel code, 20876k reserved, 1006k data, 368k init, 129920k highmem)
Aug 29 18:49:18 xFLHCx kernel: [   20.072910] virtual kernel memory layout:
Aug 29 18:49:18 xFLHCx kernel: [   20.072911]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Aug 29 18:49:18 xFLHCx kernel: [   20.072911]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 29 18:49:18 xFLHCx kernel: [   20.072912]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Aug 29 18:49:18 xFLHCx kernel: [   20.072913]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug 29 18:49:18 xFLHCx kernel: [   20.072914]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Aug 29 18:49:18 xFLHCx kernel: [   20.072915]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
Aug 29 18:49:18 xFLHCx kernel: [   20.072915]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
Aug 29 18:49:18 xFLHCx kernel: [   20.072918] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug 29 18:49:18 xFLHCx kernel: [   20.072947] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Aug 29 18:49:18 xFLHCx kernel: [   20.073061] hpet clockevent registered
Aug 29 18:49:18 xFLHCx kernel: [   20.152856] Calibrating delay using timer specific routine.. 5215.05 BogoMIPS (lpj=10430100)
Aug 29 18:49:18 xFLHCx kernel: [   20.152874] Security Framework initialized
Aug 29 18:49:18 xFLHCx kernel: [   20.152879] SELinux:  Disabled at boot.
Aug 29 18:49:18 xFLHCx kernel: [   20.152891] AppArmor: AppArmor initialized
Aug 29 18:49:18 xFLHCx kernel: [   20.152894] Failure registering capabilities with primary security module.
Aug 29 18:49:18 xFLHCx kernel: [   20.152900] Mount-cache hash table entries: 512
Aug 29 18:49:18 xFLHCx kernel: [   20.152993] Initializing cgroup subsys ns
Aug 29 18:49:18 xFLHCx kernel: [   20.152996] Initializing cgroup subsys cpuacct
Aug 29 18:49:18 xFLHCx kernel: [   20.153004] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
Aug 29 18:49:18 xFLHCx kernel: [   20.153010] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Aug 29 18:49:18 xFLHCx kernel: [   20.153012] CPU: L2 Cache: 512K (64 bytes/line)
Aug 29 18:49:18 xFLHCx kernel: [   20.153014] CPU 0(2) -> Core 0
Aug 29 18:49:18 xFLHCx kernel: [   20.153015] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f 00000000
Aug 29 18:49:18 xFLHCx kernel: [   20.153023] Compat vDSO mapped to ffffe000.
Aug 29 18:49:18 xFLHCx kernel: [   20.153032] Checking 'hlt' instruction... OK.
Aug 29 18:49:18 xFLHCx kernel: [   20.169049] SMP alternatives: switching to UP code
Aug 29 18:49:18 xFLHCx kernel: [   20.170027] Early unpacking initramfs... done
Aug 29 18:49:18 xFLHCx kernel: [   20.414675] ACPI: Core revision 20070126
Aug 29 18:49:18 xFLHCx kernel: [   20.414722] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 29 18:49:18 xFLHCx kernel: [   20.427834] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ stepping 02
Aug 29 18:49:18 xFLHCx kernel: [   20.427849] SMP alternatives: switching to SMP code
Aug 29 18:49:18 xFLHCx kernel: [   20.428194] Booting processor 1/1 eip 3000
Aug 29 18:49:18 xFLHCx kernel: [   20.438123] Initializing CPU#1
Aug 29 18:49:18 xFLHCx kernel: [   20.515882] Calibrating delay using timer specific routine.. 5211.13 BogoMIPS (lpj=10422264)
Aug 29 18:49:18 xFLHCx kernel: [   20.515887] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
Aug 29 18:49:18 xFLHCx kernel: [   20.515893] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Aug 29 18:49:18 xFLHCx kernel: [   20.515894] CPU: L2 Cache: 512K (64 bytes/line)
Aug 29 18:49:18 xFLHCx kernel: [   20.515896] CPU 1(2) -> Core 1
Aug 29 18:49:18 xFLHCx kernel: [   20.515897] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f 00000000
Aug 29 18:49:18 xFLHCx kernel: [   20.516060] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ stepping 02
Aug 29 18:49:18 xFLHCx kernel: [   20.516072] Total of 2 processors activated (10426.18 BogoMIPS).
Aug 29 18:49:18 xFLHCx kernel: [   20.516373] ENABLING IO-APIC IRQs
Aug 29 18:49:18 xFLHCx kernel: [   20.516592] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 29 18:49:18 xFLHCx kernel: [   20.663626] Brought up 2 CPUs
Aug 29 18:49:18 xFLHCx kernel: [   20.663677] CPU0 attaching sched-domain:
Aug 29 18:49:18 xFLHCx kernel: [   20.663680]  domain 0: span 03
Aug 29 18:49:18 xFLHCx kernel: [   20.663681]   groups: 01 02
Aug 29 18:49:18 xFLHCx kernel: [   20.663683] CPU1 attaching sched-domain:
Aug 29 18:49:18 xFLHCx kernel: [   20.663685]  domain 0: span 03
Aug 29 18:49:18 xFLHCx kernel: [   20.663686]   groups: 02 01
Aug 29 18:49:18 xFLHCx kernel: [   20.663837] net_namespace: 64 bytes
Aug 29 18:49:18 xFLHCx kernel: [   20.663843] Booting paravirtualized kernel on bare hardware
Aug 29 18:49:18 xFLHCx kernel: [   20.664172] Time: 18:48:55  Date: 08/29/08
Aug 29 18:49:18 xFLHCx kernel: [   20.664192] NET: Registered protocol family 16
Aug 29 18:49:18 xFLHCx kernel: [   20.664324] EISA bus registered
Aug 29 18:49:18 xFLHCx kernel: [   20.664327] ACPI: bus type pci registered
Aug 29 18:49:18 xFLHCx kernel: [   20.665295] PCI: PCI BIOS revision 3.00 entry at 0xfb3f0, last bus=3
Aug 29 18:49:18 xFLHCx kernel: [   20.665297] PCI: Using configuration type 1
Aug 29 18:49:18 xFLHCx kernel: [   20.665305] Setting up standard PCI resources
Aug 29 18:49:18 xFLHCx kernel: [   20.668783] ACPI: EC: Look up EC in DSDT
Aug 29 18:49:18 xFLHCx kernel: [   20.672612] ACPI: Interpreter enabled
Aug 29 18:49:18 xFLHCx kernel: [   20.672617] ACPI: (supports S0 S1 S4 S5)
Aug 29 18:49:18 xFLHCx kernel: [   20.672630] ACPI: Using IOAPIC for interrupt routing
Aug 29 18:49:18 xFLHCx kernel: [   20.676415] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 29 18:49:18 xFLHCx kernel: [   20.676601] pci 0000:00:11.0: set SATA to AHCI mode
Aug 29 18:49:18 xFLHCx kernel: [   20.677660] PCI: Transparent bridge - 0000:00:14.4
Aug 29 18:49:18 xFLHCx kernel: [   20.677683] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 29 18:49:18 xFLHCx kernel: [   20.677884] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
Aug 29 18:49:18 xFLHCx kernel: [   20.677965] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
Aug 29 18:49:18 xFLHCx kernel: [   20.678031] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
Aug 29 18:49:18 xFLHCx kernel: [   20.690283] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 29 18:49:18 xFLHCx kernel: [   20.690362] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 29 18:49:18 xFLHCx kernel: [   20.690439] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 29 18:49:18 xFLHCx kernel: [   20.690516] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 29 18:49:18 xFLHCx kernel: [   20.690595] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 29 18:49:18 xFLHCx kernel: [   20.690672] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 29 18:49:18 xFLHCx kernel: [   20.690750] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 29 18:49:18 xFLHCx kernel: [   20.690827] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 29 18:49:18 xFLHCx kernel: [   20.690917] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug 29 18:49:18 xFLHCx kernel: [   20.690938] pnp: PnP ACPI init
Aug 29 18:49:18 xFLHCx kernel: [   20.690944] ACPI: bus type pnp registered
Aug 29 18:49:18 xFLHCx kernel: [   20.693283] pnp: PnP ACPI: found 15 devices
Aug 29 18:49:18 xFLHCx kernel: [   20.693285] ACPI: ACPI bus type pnp unregistered
Aug 29 18:49:18 xFLHCx kernel: [   20.693288] PnPBIOS: Disabled by ACPI PNP
Aug 29 18:49:18 xFLHCx kernel: [   20.693442] PCI: Using ACPI for IRQ routing
Aug 29 18:49:18 xFLHCx kernel: [   20.693445] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug 29 18:49:18 xFLHCx kernel: [   20.693453] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
Aug 29 18:49:18 xFLHCx kernel: [   20.767283] NET: Registered protocol family 8
Aug 29 18:49:18 xFLHCx kernel: [   20.767285] NET: Registered protocol family 20
Aug 29 18:49:18 xFLHCx kernel: [   20.767312] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Aug 29 18:49:18 xFLHCx kernel: [   20.767316] hpet0: 4 32-bit timers, 14318180 Hz
Aug 29 18:49:18 xFLHCx kernel: [   20.768352] AppArmor: AppArmor Filesystem Enabled
Aug 29 18:49:18 xFLHCx kernel: [   20.771267] Time: hpet clocksource has been installed.
Aug 29 18:49:18 xFLHCx kernel: [   20.771280] Switched to high resolution mode on CPU 0
Aug 29 18:49:18 xFLHCx kernel: [   20.771327] Switched to high resolution mode on CPU 1
Aug 29 18:49:18 xFLHCx kernel: [   20.779244] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779246] system 00:01: ioport range 0x220-0x225 has been reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779248] system 00:01: ioport range 0x290-0x294 has been reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779252] system 00:02: ioport range 0x4100-0x411f has been reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779254] system 00:02: ioport range 0x228-0x22f has been reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779256] system 00:02: ioport range 0x238-0x23f has been reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779258] system 00:02: ioport range 0x40b-0x40b has been reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779260] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779261] system 00:02: ioport range 0xc00-0xc01 has been reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779263] system 00:02: ioport range 0xc14-0xc14 has been reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779265] system 00:02: ioport range 0xc50-0xc52 has been reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779267] system 00:02: ioport range 0xc6c-0xc6d has been reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779269] system 00:02: ioport range 0xc6f-0xc6f has been reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779271] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779273] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779275] system 00:02: ioport range 0xcd4-0xcdf has been reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779277] system 00:02: ioport range 0x4000-0x40fe has been reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779279] system 00:02: ioport range 0x4210-0x4217 has been reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779281] system 00:02: ioport range 0xb00-0xb0f has been reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779283] system 00:02: ioport range 0xb10-0xb1f has been reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779285] system 00:02: ioport range 0xb20-0xb3f has been reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779292] system 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779297] system 00:0e: iomem range 0xcf600-0xcffff has been reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779299] system 00:0e: iomem range 0xf0000-0xf7fff could not be reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779301] system 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779303] system 00:0e: iomem range 0xfc000-0xfffff could not be reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779305] system 00:0e: iomem range 0x3fee0000-0x3fefffff could not be reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779307] system 00:0e: iomem range 0xffff0000-0xffffffff could not be reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779309] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779311] system 00:0e: iomem range 0x100000-0x3fedffff could not be reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779313] system 00:0e: iomem range 0x0-0x0 could not be reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779315] system 00:0e: iomem range 0xfec00000-0xfec00fff could not be reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779317] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.779320] system 00:0e: iomem range 0xfff80000-0xfffeffff could not be reserved
Aug 29 18:49:18 xFLHCx kernel: [   20.809544] PCI: Bridge: 0000:00:02.0
Aug 29 18:49:18 xFLHCx kernel: [   20.809546]   IO window: e000-efff
Aug 29 18:49:18 xFLHCx kernel: [   20.809549]   MEM window: fdf00000-fdffffff
Aug 29 18:49:18 xFLHCx kernel: [   20.809551]   PREFETCH window: d0000000-dfffffff
Aug 29 18:49:18 xFLHCx kernel: [   20.809554] PCI: Bridge: 0000:00:0a.0
Aug 29 18:49:18 xFLHCx kernel: [   20.809556]   IO window: d000-dfff
Aug 29 18:49:18 xFLHCx kernel: [   20.809558]   MEM window: fde00000-fdefffff
Aug 29 18:49:18 xFLHCx kernel: [   20.809560]   PREFETCH window: fdb00000-fdbfffff
Aug 29 18:49:18 xFLHCx kernel: [   20.809562] PCI: Bridge: 0000:00:14.4
Aug 29 18:49:18 xFLHCx kernel: [   20.809565]   IO window: c000-cfff
Aug 29 18:49:18 xFLHCx kernel: [   20.809569]   MEM window: fdd00000-fddfffff
Aug 29 18:49:18 xFLHCx kernel: [   20.809573]   PREFETCH window: fdc00000-fdcfffff
Aug 29 18:49:18 xFLHCx kernel: [   20.809592] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 18 (level, low) -> IRQ 16
Aug 29 18:49:18 xFLHCx kernel: [   20.809596] PCI: Setting latency timer of device 0000:00:02.0 to 64
Aug 29 18:49:18 xFLHCx kernel: [   20.809603] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 16
Aug 29 18:49:18 xFLHCx kernel: [   20.809606] PCI: Setting latency timer of device 0000:00:0a.0 to 64
Aug 29 18:49:18 xFLHCx kernel: [   20.809619] NET: Registered protocol family 2
Aug 29 18:49:18 xFLHCx kernel: [   20.847101] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 29 18:49:18 xFLHCx kernel: [   20.847326] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 29 18:49:18 xFLHCx kernel: [   20.848043] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 29 18:49:18 xFLHCx kernel: [   20.848416] TCP: Hash tables configured (established 131072 bind 65536)
Aug 29 18:49:18 xFLHCx kernel: [   20.848418] TCP reno registered
Aug 29 18:49:18 xFLHCx kernel: [   20.859121] checking if image is initramfs... it is
Aug 29 18:49:18 xFLHCx kernel: [   21.335289] Freeing initrd memory: 7705k freed
Aug 29 18:49:18 xFLHCx kernel: [   21.335898] audit: initializing netlink socket (disabled)
Aug 29 18:49:18 xFLHCx kernel: [   21.335910] audit(1220035736.156:1): initialized
Aug 29 18:49:18 xFLHCx kernel: [   21.336033] highmem bounce pool size: 64 pages
Aug 29 18:49:18 xFLHCx kernel: [   21.337450] VFS: Disk quotas dquot_6.5.1
Aug 29 18:49:18 xFLHCx kernel: [   21.337501] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 29 18:49:18 xFLHCx kernel: [   21.337591] io scheduler noop registered
Aug 29 18:49:18 xFLHCx kernel: [   21.337592] io scheduler anticipatory registered
Aug 29 18:49:18 xFLHCx kernel: [   21.337594] io scheduler deadline registered
Aug 29 18:49:18 xFLHCx kernel: [   21.337600] io scheduler cfq registered (default)
Aug 29 18:49:18 xFLHCx kernel: [   21.477400] Boot video device is 0000:01:00.0
Aug 29 18:49:18 xFLHCx kernel: [   21.477523] PCI: Setting latency timer of device 0000:00:02.0 to 64
Aug 29 18:49:18 xFLHCx kernel: [   21.477544] assign_interrupt_mode Found MSI capability
Aug 29 18:49:18 xFLHCx kernel: [   21.477567] Allocate Port Service[0000:00:02.0:pcie00]
Aug 29 18:49:18 xFLHCx kernel: [   21.477623] PCI: Setting latency timer of device 0000:00:0a.0 to 64
Aug 29 18:49:18 xFLHCx kernel: [   21.477643] assign_interrupt_mode Found MSI capability
Aug 29 18:49:18 xFLHCx kernel: [   21.477662] Allocate Port Service[0000:00:0a.0:pcie00]
Aug 29 18:49:18 xFLHCx kernel: [   21.477836] isapnp: Scanning for PnP cards...
Aug 29 18:49:18 xFLHCx kernel: [   21.830758] isapnp: No Plug & Play device found
Aug 29 18:49:18 xFLHCx kernel: [   21.852174] Real Time Clock Driver v1.12ac
Aug 29 18:49:18 xFLHCx kernel: [   21.852327] hpet_resources: 0xfed00000 is busy
Aug 29 18:49:18 xFLHCx kernel: [   21.852355] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug 29 18:49:18 xFLHCx kernel: [   21.852749] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug 29 18:49:18 xFLHCx kernel: [   21.853268] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug 29 18:49:18 xFLHCx kernel: [   21.853876] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug 29 18:49:18 xFLHCx kernel: [   21.853926] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug 29 18:49:18 xFLHCx kernel: [   21.854003] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Aug 29 18:49:18 xFLHCx kernel: [   21.854352] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 29 18:49:18 xFLHCx kernel: [   21.854356] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 29 18:49:18 xFLHCx kernel: [   21.869409] mice: PS/2 mouse device common for all mice
Aug 29 18:49:18 xFLHCx kernel: [   21.869507] EISA: Probing bus 0 at eisa.0
Aug 29 18:49:18 xFLHCx kernel: [   21.869525] Cannot allocate resource for EISA slot 4
Aug 29 18:49:18 xFLHCx kernel: [   21.869542] EISA: Detected 0 cards.
Aug 29 18:49:18 xFLHCx kernel: [   21.869544] cpuidle: using governor ladder
Aug 29 18:49:18 xFLHCx kernel: [   21.869546] cpuidle: using governor menu
Aug 29 18:49:18 xFLHCx kernel: [   21.869612] NET: Registered protocol family 1
Aug 29 18:49:18 xFLHCx kernel: [   21.869634] Using IPI No-Shortcut mode
Aug 29 18:49:18 xFLHCx kernel: [   21.869663] registered taskstats version 1
Aug 29 18:49:18 xFLHCx kernel: [   21.869750]   Magic number: 4:888:848
Aug 29 18:49:18 xFLHCx kernel: [   21.869823]   hash matches device ptyv0
Aug 29 18:49:18 xFLHCx kernel: [   21.869880] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 29 18:49:18 xFLHCx kernel: [   21.869882] EDD information not available.
Aug 29 18:49:18 xFLHCx kernel: [   21.870094] Freeing unused kernel memory: 368k freed
Aug 29 18:49:18 xFLHCx kernel: [   21.912281] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Aug 29 18:49:18 xFLHCx kernel: [   23.056669] fuse init (API version 7.9)
Aug 29 18:49:18 xFLHCx kernel: [   23.073711] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 29 18:49:18 xFLHCx kernel: [   23.073721] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 29 18:49:18 xFLHCx kernel: [   23.350105] usbcore: registered new interface driver usbfs
Aug 29 18:49:18 xFLHCx kernel: [   23.350124] usbcore: registered new interface driver hub
Aug 29 18:49:18 xFLHCx kernel: [   23.350189] r8169 Gigabit Ethernet driver 2.2LK loaded
Aug 29 18:49:18 xFLHCx kernel: [   23.350209] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 16
Aug 29 18:49:18 xFLHCx kernel: [   23.350225] PCI: Setting latency timer of device 0000:02:00.0 to 64
Aug 29 18:49:18 xFLHCx kernel: [   23.350433] eth0: RTL8168c/8111c at 0xf8844000, 00:1f:d0:5a:fd:e7, XID 3c4000c0 IRQ 221
Aug 29 18:49:18 xFLHCx kernel: [   23.356647] usbcore: registered new device driver usb
Aug 29 18:49:18 xFLHCx kernel: [   23.357741] SCSI subsystem initialized
Aug 29 18:49:18 xFLHCx kernel: [   23.357864] ACPI: PCI Interrupt 0000:00:12.2[B] -> GSI 17 (level, low) -> IRQ 17
Aug 29 18:49:18 xFLHCx kernel: [   23.357875] ehci_hcd 0000:00:12.2: EHCI Host Controller
Aug 29 18:49:18 xFLHCx kernel: [   23.358144] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Aug 29 18:49:18 xFLHCx kernel: [   23.358180] ehci_hcd 0000:00:12.2: debug port 1
Aug 29 18:49:18 xFLHCx kernel: [   23.358196] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
Aug 29 18:49:18 xFLHCx kernel: [   23.358986] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 29 18:49:18 xFLHCx kernel: [   23.363840] libata version 3.00 loaded.
Aug 29 18:49:18 xFLHCx kernel: [   23.368474] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 29 18:49:18 xFLHCx kernel: [   23.368576] usb usb1: configuration #1 chosen from 1 choice
Aug 29 18:49:18 xFLHCx kernel: [   23.368599] hub 1-0:1.0: USB hub found
Aug 29 18:49:18 xFLHCx kernel: [   23.368604] hub 1-0:1.0: 6 ports detected
Aug 29 18:49:18 xFLHCx kernel: [   23.426621] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Aug 29 18:49:18 xFLHCx kernel: [   23.426627] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Aug 29 18:49:18 xFLHCx kernel: [   23.469822] Floppy drive(s): fd0 is 1.44M
Aug 29 18:49:18 xFLHCx kernel: [   23.472306] ACPI: PCI Interrupt 0000:00:13.2[B] -> GSI 19 (level, low) -> IRQ 18
Aug 29 18:49:18 xFLHCx kernel: [   23.472319] ehci_hcd 0000:00:13.2: EHCI Host Controller
Aug 29 18:49:18 xFLHCx kernel: [   23.472336] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Aug 29 18:49:18 xFLHCx kernel: [   23.472371] ehci_hcd 0000:00:13.2: debug port 1
Aug 29 18:49:18 xFLHCx kernel: [   23.472386] ehci_hcd 0000:00:13.2: irq 18, io mem 0xfe029000
Aug 29 18:49:18 xFLHCx kernel: [   23.484171] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 29 18:49:18 xFLHCx kernel: [   23.484265] usb usb2: configuration #1 chosen from 1 choice
Aug 29 18:49:18 xFLHCx kernel: [   23.484282] hub 2-0:1.0: USB hub found
Aug 29 18:49:18 xFLHCx kernel: [   23.484287] hub 2-0:1.0: 6 ports detected
Aug 29 18:49:18 xFLHCx kernel: [   23.488170] FDC 0 is a post-1991 82077
Aug 29 18:49:18 xFLHCx kernel: [   23.588035] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 19
Aug 29 18:49:18 xFLHCx kernel: [   23.588050] ohci_hcd 0000:00:12.0: OHCI Host Controller
Aug 29 18:49:18 xFLHCx kernel: [   23.588072] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
Aug 29 18:49:18 xFLHCx kernel: [   23.588090] ohci_hcd 0000:00:12.0: irq 19, io mem 0xfe02e000
Aug 29 18:49:18 xFLHCx kernel: [   23.647820] usb usb3: configuration #1 chosen from 1 choice
Aug 29 18:49:18 xFLHCx kernel: [   23.647839] hub 3-0:1.0: USB hub found
Aug 29 18:49:18 xFLHCx kernel: [   23.647846] hub 3-0:1.0: 3 ports detected
Aug 29 18:49:18 xFLHCx kernel: [   23.711587] usb 1-4: new high speed USB device using ehci_hcd and address 2
Aug 29 18:49:18 xFLHCx kernel: [   23.751559] ACPI: PCI Interrupt 0000:00:12.1[A] -> GSI 16 (level, low) -> IRQ 19
Aug 29 18:49:18 xFLHCx kernel: [   23.751574] ohci_hcd 0000:00:12.1: OHCI Host Controller
Aug 29 18:49:18 xFLHCx kernel: [   23.751593] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
Aug 29 18:49:18 xFLHCx kernel: [   23.751606] ohci_hcd 0000:00:12.1: irq 19, io mem 0xfe02d000
Aug 29 18:49:18 xFLHCx kernel: [   23.811364] usb usb4: configuration #1 chosen from 1 choice
Aug 29 18:49:18 xFLHCx kernel: [   23.811383] hub 4-0:1.0: USB hub found
Aug 29 18:49:18 xFLHCx kernel: [   23.811391] hub 4-0:1.0: 3 ports detected
Aug 29 18:49:18 xFLHCx kernel: [   23.845205] usb 1-4: configuration #1 chosen from 1 choice
Aug 29 18:49:18 xFLHCx kernel: [   23.915294] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 18 (level, low) -> IRQ 16
Aug 29 18:49:18 xFLHCx kernel: [   23.915309] ohci_hcd 0000:00:13.0: OHCI Host Controller
Aug 29 18:49:18 xFLHCx kernel: [   23.915333] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Aug 29 18:49:18 xFLHCx kernel: [   23.915350] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02b000
Aug 29 18:49:18 xFLHCx kernel: [   23.974923] usb usb5: configuration #1 chosen from 1 choice
Aug 29 18:49:18 xFLHCx kernel: [   23.974943] hub 5-0:1.0: USB hub found
Aug 29 18:49:18 xFLHCx kernel: [   23.974950] hub 5-0:1.0: 3 ports detected
Aug 29 18:49:18 xFLHCx kernel: [   24.078654] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 18 (level, low) -> IRQ 16
Aug 29 18:49:18 xFLHCx kernel: [   24.078664] ohci_hcd 0000:00:13.1: OHCI Host Controller
Aug 29 18:49:18 xFLHCx kernel: [   24.078681] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
Aug 29 18:49:18 xFLHCx kernel: [   24.078691] ohci_hcd 0000:00:13.1: irq 16, io mem 0xfe02a000
Aug 29 18:49:18 xFLHCx kernel: [   24.138485] usb usb6: configuration #1 chosen from 1 choice
Aug 29 18:49:18 xFLHCx kernel: [   24.138502] hub 6-0:1.0: USB hub found
Aug 29 18:49:18 xFLHCx kernel: [   24.138509] hub 6-0:1.0: 3 ports detected
Aug 29 18:49:18 xFLHCx kernel: [   24.242211] ACPI: PCI Interrupt 0000:00:14.5[C] -> GSI 18 (level, low) -> IRQ 16
Aug 29 18:49:18 xFLHCx kernel: [   24.242221] ohci_hcd 0000:00:14.5: OHCI Host Controller
Aug 29 18:49:18 xFLHCx kernel: [   24.242241] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
Aug 29 18:49:18 xFLHCx kernel: [   24.242253] ohci_hcd 0000:00:14.5: irq 16, io mem 0xfe028000
Aug 29 18:49:18 xFLHCx kernel: [   24.302048] usb usb7: configuration #1 chosen from 1 choice
Aug 29 18:49:18 xFLHCx kernel: [   24.302062] hub 7-0:1.0: USB hub found
Aug 29 18:49:18 xFLHCx kernel: [   24.302068] hub 7-0:1.0: 2 ports detected
Aug 29 18:49:18 xFLHCx kernel: [   24.405864] ahci 0000:00:11.0: version 3.0
Aug 29 18:49:18 xFLHCx kernel: [   24.405898] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 22 (level, low) -> IRQ 20
Aug 29 18:49:18 xFLHCx kernel: [   24.405947] ahci 0000:00:11.0: controller can't do PMP, turning off CAP_PMP
Aug 29 18:49:18 xFLHCx kernel: [   24.759974] usb 1-4: USB disconnect, address 2
Aug 29 18:49:18 xFLHCx kernel: [   25.407105] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Aug 29 18:49:18 xFLHCx kernel: [   25.407108] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pio slum part 
Aug 29 18:49:18 xFLHCx kernel: [   25.407435] scsi0 : ahci
Aug 29 18:49:18 xFLHCx kernel: [   25.407622] scsi1 : ahci
Aug 29 18:49:18 xFLHCx kernel: [   25.407719] scsi2 : ahci
Aug 29 18:49:18 xFLHCx kernel: [   25.407813] scsi3 : ahci
Aug 29 18:49:18 xFLHCx kernel: [   25.407869] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 220
Aug 29 18:49:18 xFLHCx kernel: [   25.407872] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 220
Aug 29 18:49:18 xFLHCx kernel: [   25.407875] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 220
Aug 29 18:49:18 xFLHCx kernel: [   25.407878] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 220
Aug 29 18:49:18 xFLHCx kernel: [   25.881857] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 29 18:49:18 xFLHCx kernel: [   26.050432] ata1.00: ATAPI: LITE-ON DVDRW LH-20A1L, BL06, max UDMA/100, ATAPI AN
Aug 29 18:49:18 xFLHCx kernel: [   26.217986] ata1.00: configured for UDMA/100
Aug 29 18:49:18 xFLHCx kernel: [   26.528153] ata2: SATA link down (SStatus 0 SControl 300)
Aug 29 18:49:18 xFLHCx kernel: [   26.839338] ata3: SATA link down (SStatus 0 SControl 300)
Aug 29 18:49:18 xFLHCx kernel: [   27.150519] ata4: SATA link down (SStatus 0 SControl 300)
Aug 29 18:49:18 xFLHCx kernel: [   27.453325] scsi 0:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1L   BL06 PQ: 0 ANSI: 5
Aug 29 18:49:18 xFLHCx kernel: [   27.453672] ACPI: PCI Interrupt 0000:03:0e.0[A] -> GSI 22 (level, low) -> IRQ 20
Aug 29 18:49:18 xFLHCx kernel: [   27.454562] ATIIXP: IDE controller (0x1002:0x439c rev 0x00) at  PCI slot 0000:00:14.1
Aug 29 18:49:18 xFLHCx kernel: [   27.454577] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 19
Aug 29 18:49:18 xFLHCx kernel: [   27.454585] ATIIXP: not 100% native mode: will probe irqs later
Aug 29 18:49:18 xFLHCx kernel: [   27.454592]     ide0: BM-DMA at 0xfa00-0xfa07, BIOS settings: hda:DMA, hdb:DMA
Aug 29 18:49:18 xFLHCx kernel: [   27.454604]     ide1: BM-DMA at 0xfa08-0xfa0f, BIOS settings: hdc:pio, hdd:pio
Aug 29 18:49:18 xFLHCx kernel: [   27.454611] Probing IDE interface ide0...
Aug 29 18:49:18 xFLHCx kernel: [   27.503336] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[fddff000-fddff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Aug 29 18:49:18 xFLHCx kernel: [   27.504936] Driver 'sr' needs updating - please use bus_type methods
Aug 29 18:49:18 xFLHCx kernel: [   27.741274] hdb: WDC WD200BB-60AUA1, ATA DISK drive
Aug 29 18:49:18 xFLHCx kernel: [   28.077387] hda: WDC WD600BB-00CAA1, ATA DISK drive
Aug 29 18:49:18 xFLHCx kernel: [   28.077397] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
Aug 29 18:49:18 xFLHCx kernel: [   28.078267] hda: UDMA/100 mode selected
Aug 29 18:49:18 xFLHCx kernel: [   28.079143] hdb: host max PIO4 wanted PIO255(auto-tune) selected PIO4
Aug 29 18:49:18 xFLHCx kernel: [   28.080017] hdb: UDMA/100 mode selected
Aug 29 18:49:18 xFLHCx kernel: [   28.080938] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Aug 29 18:49:18 xFLHCx kernel: [   28.107901] Probing IDE interface ide1...
Aug 29 18:49:18 xFLHCx kernel: [   28.685362] hda: max request size: 128KiB
Aug 29 18:49:18 xFLHCx kernel: [   28.686425] hda: Host Protected Area detected.
Aug 29 18:49:18 xFLHCx kernel: [   28.686426] ^Icurrent capacity is 117229295 sectors (60021 MB)
Aug 29 18:49:18 xFLHCx kernel: [   28.686427] ^Inative  capacity is 117231408 sectors (60022 MB)
Aug 29 18:49:18 xFLHCx kernel: [   28.688969] hda: Host Protected Area disabled.
Aug 29 18:49:18 xFLHCx kernel: [   28.688971] hda: 117231408 sectors (60022 MB) w/2048KiB Cache, CHS=65535/16/63
Aug 29 18:49:18 xFLHCx kernel: [   28.688974] hda: cache flushes not supported
Aug 29 18:49:18 xFLHCx kernel: [   28.688999]  hda: hda1 hda2 < hda5 >
Aug 29 18:49:18 xFLHCx kernel: [   28.717043] hdb: max request size: 128KiB
Aug 29 18:49:18 xFLHCx kernel: [   28.717979] hdb: 39102336 sectors (20020 MB) w/2048KiB Cache, CHS=38792/16/63
Aug 29 18:49:18 xFLHCx kernel: [   28.717982] hdb: cache flushes not supported
Aug 29 18:49:18 xFLHCx kernel: [   28.717994]  hdb: hdb1 <sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Aug 29 18:49:18 xFLHCx kernel: [   28.730010] Uniform CD-ROM driver Revision: 3.20
Aug 29 18:49:18 xFLHCx kernel: [   28.730038] sr 0:0:0:0: Attached scsi CD-ROM sr0
Aug 29 18:49:18 xFLHCx kernel: [   28.730300]  hdb5<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
Aug 29 18:49:18 xFLHCx kernel: [   28.748615]  hdb6 >
Aug 29 18:49:18 xFLHCx kernel: [   28.771335] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0072802500001fd0]
Aug 29 18:49:18 xFLHCx kernel: [   29.329205] kjournald starting.  Commit interval 5 seconds
Aug 29 18:49:18 xFLHCx kernel: [   29.329185] EXT3-fs: mounted filesystem with ordered data mode.
Aug 29 18:49:18 xFLHCx kernel: [   38.940033] input: PC Speaker as /devices/platform/pcspkr/input/input2
Aug 29 18:49:18 xFLHCx kernel: [   39.102749] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 29 18:49:18 xFLHCx kernel: [   39.142383] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 29 18:49:18 xFLHCx kernel: [   39.291762] ACPI: WMI-Acer: Mapper loaded
Aug 29 18:49:18 xFLHCx kernel: [   39.331575] input: Power Button (FF) as /devices/virtual/input/input3
Aug 29 18:49:18 xFLHCx kernel: [   39.386411] ACPI: Power Button (FF) [PWRF]
Aug 29 18:49:18 xFLHCx kernel: [   39.386459] input: Power Button (CM) as /devices/virtual/input/input4
Aug 29 18:49:18 xFLHCx kernel: [   39.439315] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Aug 29 18:49:18 xFLHCx kernel: [   39.450244] ACPI: Power Button (CM) [PWRB]
Aug 29 18:49:18 xFLHCx kernel: [   39.815649] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Aug 29 18:49:18 xFLHCx kernel: [   39.869724] parport_pc 00:0a: reported by Plug and Play ACPI
Aug 29 18:49:18 xFLHCx kernel: [   39.869781] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Aug 29 18:49:18 xFLHCx kernel: [   39.906649] Linux agpgart interface v0.102
Aug 29 18:49:18 xFLHCx kernel: [   40.182126] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 19
Aug 29 18:49:18 xFLHCx kernel: [   40.215030] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
Aug 29 18:49:18 xFLHCx kernel: [   40.972490] lp0: using parport0 (interrupt-driven).
Aug 29 18:49:18 xFLHCx kernel: [   41.592939] EXT3 FS on hdb6, internal journal
Aug 29 18:49:18 xFLHCx kernel: [   42.685477] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 29 18:49:18 xFLHCx kernel: [   42.980527] No dock devices found.
Aug 29 18:49:18 xFLHCx kernel: [   43.339304] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ processors (2 cpu cores) (version 2.20.00)
Aug 29 18:49:18 xFLHCx kernel: [   43.339385] powernow-k8:    0 : fid 0x12 (2600 MHz), vid 0x9
Aug 29 18:49:18 xFLHCx kernel: [   43.339389] powernow-k8:    1 : fid 0x10 (2400 MHz), vid 0xb
Aug 29 18:49:18 xFLHCx kernel: [   43.339391] powernow-k8:    2 : fid 0xe (2200 MHz), vid 0xd
Aug 29 18:49:18 xFLHCx kernel: [   43.339393] powernow-k8:    3 : fid 0xc (2000 MHz), vid 0xf
Aug 29 18:49:18 xFLHCx kernel: [   43.339394] powernow-k8:    4 : fid 0xa (1800 MHz), vid 0x11
Aug 29 18:49:18 xFLHCx kernel: [   43.339396] powernow-k8:    5 : fid 0x2 (1000 MHz), vid 0x12
Aug 29 18:49:19 xFLHCx NetworkManager: <info>  starting... 
Aug 29 18:49:19 xFLHCx avahi-daemon[5175]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Aug 29 18:49:19 xFLHCx avahi-daemon[5175]: Successfully dropped root privileges.
Aug 29 18:49:19 xFLHCx avahi-daemon[5175]: avahi-daemon 0.6.22 starting up.
Aug 29 18:49:19 xFLHCx avahi-daemon[5175]: Successfully called chroot().
Aug 29 18:49:19 xFLHCx avahi-daemon[5175]: Successfully dropped remaining capabilities.
Aug 29 18:49:19 xFLHCx avahi-daemon[5176]: chroot.c: open() failed: No such file or directory
Aug 29 18:49:19 xFLHCx avahi-daemon[5175]: Failed to open /etc/resolv.conf: Invalid argument
Aug 29 18:49:19 xFLHCx avahi-daemon[5175]: No service file found in /etc/avahi/services.
Aug 29 18:49:19 xFLHCx avahi-daemon[5175]: Network interface enumeration completed.
Aug 29 18:49:19 xFLHCx avahi-daemon[5175]: Registering HINFO record with values 'I686'/'LINUX'.
Aug 29 18:49:19 xFLHCx avahi-daemon[5175]: Server startup complete. Host name is xFLHCx.local. Local service cookie is 1604352940.
Aug 29 18:49:19 xFLHCx kernel: [   43.952938] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Aug 29 18:49:19 xFLHCx kernel: [   43.952942] apm: disabled - APM is not SMP safe.
Aug 29 18:49:19 xFLHCx kernel: [   44.101195] ppdev: user-space parallel port driver
Aug 29 18:49:19 xFLHCx kernel: [   44.268352] audit(1220050159.465:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5217 profile="/usr/sbin/cupsd" namespace="default"
Aug 29 18:49:19 xFLHCx dhcdbd: Started up.
Aug 29 18:49:20 xFLHCx kernel: [   44.781554] Clocksource tsc unstable (delta = -305260029 ns)
Aug 29 18:49:24 xFLHCx kernel: [   48.066639] r8169: eth0: link down
Aug 29 18:49:24 xFLHCx NetworkManager: <info>  eth0: Device is fully-supported using driver 'r8169'. 
Aug 29 18:49:24 xFLHCx NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Aug 29 18:49:24 xFLHCx NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Aug 29 18:49:24 xFLHCx NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Aug 29 18:49:24 xFLHCx NetworkManager: <info>  Deactivating device eth0. 
Aug 29 18:49:24 xFLHCx NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Aug 29 18:49:24 xFLHCx hcid[5449]: Bluetooth HCI daemon
Aug 29 18:49:24 xFLHCx kernel: [   48.108844] Bluetooth: Core ver 2.11
Aug 29 18:49:24 xFLHCx kernel: [   48.109096] NET: Registered protocol family 31
Aug 29 18:49:24 xFLHCx kernel: [   48.109098] Bluetooth: HCI device and connection manager initialized
Aug 29 18:49:24 xFLHCx kernel: [   48.109101] Bluetooth: HCI socket layer initialized
Aug 29 18:49:24 xFLHCx hcid[5449]: Starting SDP server
Aug 29 18:49:24 xFLHCx kernel: [   48.115756] Bluetooth: L2CAP ver 2.9
Aug 29 18:49:24 xFLHCx kernel: [   48.115760] Bluetooth: L2CAP socket layer initialized
Aug 29 18:49:24 xFLHCx hcid[5449]: Created local server at unix:abstract=/var/run/dbus-CvVd0nf3Tw,guid=7cb84270135a22ef31b8d9b548b87cf4
Aug 29 18:49:24 xFLHCx input[5467]: Bluetooth Input daemon
Aug 29 18:49:24 xFLHCx input[5467]: Registered input manager path:/org/bluez/input
Aug 29 18:49:24 xFLHCx audio[5468]: Bluetooth Audio daemon
Aug 29 18:49:24 xFLHCx audio[5468]: Unix socket created: 5
Aug 29 18:49:24 xFLHCx audio[5468]: audio.conf: Key file does not have key 'Enable'
Aug 29 18:49:24 xFLHCx audio[5468]: audio.conf: Key file does not have key 'Disable'
Aug 29 18:49:24 xFLHCx NetworkManager: <debug> [1220050164.346391] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Aug 29 18:49:24 xFLHCx kernel: [   48.156937] Bluetooth: RFCOMM socket layer initialized
Aug 29 18:49:24 xFLHCx kernel: [   48.156949] Bluetooth: RFCOMM TTY layer initialized
Aug 29 18:49:24 xFLHCx kernel: [   48.156951] Bluetooth: RFCOMM ver 1.8
Aug 29 18:49:24 xFLHCx audio[5468]: add_service_record: got record id 0x10000
Aug 29 18:49:24 xFLHCx audio[5468]: audio.conf: Key file does not have key 'Disable'
Aug 29 18:49:24 xFLHCx audio[5468]: audio.conf: Key file does not have group 'A2DP'
Aug 29 18:49:24 xFLHCx last message repeated 3 times
Aug 29 18:49:24 xFLHCx audio[5468]: SEP 0x806d748 registered: type:0 codec:0 seid:1
Aug 29 18:49:24 xFLHCx audio[5468]: add_service_record: got record id 0x10001
Aug 29 18:49:24 xFLHCx audio[5468]: add_service_record: got record id 0x10002
Aug 29 18:49:24 xFLHCx audio[5468]: add_service_record: got record id 0x10003
Aug 29 18:49:24 xFLHCx audio[5468]: Registered manager path:/org/bluez/audio
Aug 29 18:49:26 xFLHCx kernel: [   49.110400] [drm] Initialized drm 1.1.0 20060810
Aug 29 18:49:27 xFLHCx anacron[5560]: Anacron 2.3 started on 2008-08-29
Aug 29 18:49:27 xFLHCx anacron[5560]: Will run job `cron.daily' in 5 min.
Aug 29 18:49:27 xFLHCx anacron[5560]: Will run job `cron.weekly' in 10 min.
Aug 29 18:49:27 xFLHCx anacron[5560]: Will run job `cron.monthly' in 15 min.
Aug 29 18:49:27 xFLHCx anacron[5560]: Jobs will be executed sequentially
Aug 29 18:49:27 xFLHCx /usr/sbin/cron[5587]: (CRON) INFO (pidfile fd = 3)
Aug 29 18:49:27 xFLHCx /usr/sbin/cron[5588]: (CRON) STARTUP (fork ok)
Aug 29 18:49:27 xFLHCx /usr/sbin/cron[5588]: (CRON) INFO (Running @reboot jobs)
Aug 29 18:49:33 xFLHCx kernel: [   51.652646] hda-intel: Invalid position buffer, using LPIB read method instead.
Aug 29 18:49:41 xFLHCx kernel: [   54.790944] NET: Registered protocol family 10
Aug 29 18:49:41 xFLHCx kernel: [   54.791116] lo: Disabled Privacy Extensions
Aug 29 18:49:41 xFLHCx kernel: [   54.791379] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 29 18:49:46 xFLHCx hcid[5449]: Default passkey agent (:1.20, /org/bluez/passkey) registered
Aug 29 18:49:46 xFLHCx hcid[5449]: Default authorization agent (:1.20, /org/bluez/auth) registered
Aug 29 18:49:50 xFLHCx NetworkManager: <info>  Updating allowed wireless network lists. 
Aug 29 18:49:50 xFLHCx NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Aug 29 18:49:54 xFLHCx kernel: [   62.335425] UDF-fs: No VRS found
Aug 29 18:49:54 xFLHCx kernel: [   62.364910] ISO 9660 Extensions: Microsoft Joliet Level 3
Aug 29 18:49:54 xFLHCx kernel: [   62.366833] ISO 9660 Extensions: RRIP_1991A
Aug 29 18:51:49 xFLHCx ntfs-3g[6056]: Version 1.2216 external FUSE 27 
Aug 29 18:51:49 xFLHCx ntfs-3g[6056]: Mounted /dev/hda1 (Read-Write, label "", NTFS 3.1) 
Aug 29 18:51:49 xFLHCx ntfs-3g[6056]: Cmdline options: rw,nosuid,nodev,uhelper=hal,locale=en_US.UTF-8 
Aug 29 18:51:49 xFLHCx ntfs-3g[6056]: Mount options: rw,nosuid,nodev,uhelper=hal,silent,allow_other,nonempty,relatime,noatime,fsname=/dev/hda1,blkdev,blksize=4096 
Aug 29 18:51:49 xFLHCx hald: mounted /dev/hda1 on behalf of uid 1000
Aug 29 18:54:05 xFLHCx kernel: [  180.763361] UDF-fs: No VRS found
Aug 29 18:54:06 xFLHCx kernel: [  181.103604] ISO 9660 Extensions: Microsoft Joliet Level 3
Aug 29 18:54:06 xFLHCx kernel: [  181.104391] ISO 9660 Extensions: RRIP_1991A
Aug 29 18:54:27 xFLHCx anacron[5560]: Job `cron.daily' started
Aug 29 18:54:27 xFLHCx anacron[6171]: Updated timestamp for job `cron.daily' to 2008-08-29
Aug 29 18:54:42 xFLHCx kernel: [  195.969416] UDF-fs: No VRS found
Aug 29 18:54:42 xFLHCx kernel: [  195.979822] ISO 9660 Extensions: Microsoft Joliet Level 3
Aug 29 18:54:42 xFLHCx kernel: [  195.985361] ISO 9660 Extensions: RRIP_1991A
Aug 29 18:59:51 xFLHCx kernel: [  330.123511] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
Aug 29 18:59:51 xFLHCx kernel: [  330.130506] usbcore: registered new interface driver ndiswrapper
Aug 29 19:00:14 xFLHCx kernel: [  339.003664] usb 1-4: new high speed USB device using ehci_hcd and address 3
Aug 29 19:00:14 xFLHCx kernel: [  339.054846] usb 1-4: configuration #1 chosen from 1 choice
Aug 29 19:00:14 xFLHCx NetworkManager: <debug> [1220050814.695216] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13b1_e_1111'). 
Aug 29 19:00:14 xFLHCx kernel: [  339.103529] usb 1-4: reset high speed USB device using ehci_hcd and address 3
Aug 29 19:00:14 xFLHCx kernel: [  339.155844] ndiswrapper: driver wusb54gs (Linksys,06/18/2004, 3.60.9.0) loaded
Aug 29 19:00:15 xFLHCx kernel: [  339.409161] irq 17: nobody cared (try booting with the "irqpoll" option)
Aug 29 19:00:15 xFLHCx kernel: [  339.409166] Pid: 0, comm: swapper Tainted: P        2.6.24-19-generic #1
Aug 29 19:00:15 xFLHCx kernel: [  339.409179]  [__report_bad_irq+0x24/0x80] __report_bad_irq+0x24/0x80
Aug 29 19:00:15 xFLHCx kernel: [  339.409191]  [note_interrupt+0x27b/0x2c0] note_interrupt+0x27b/0x2c0
Aug 29 19:00:15 xFLHCx kernel: [  339.409200]  [snd_pcm:ktime_get_ts+0x1e/0x4f0] ktime_get_ts+0x1e/0x60
Aug 29 19:00:15 xFLHCx kernel: [  339.409205]  [handle_IRQ_event+0x30/0x60] handle_IRQ_event+0x30/0x60
Aug 29 19:00:15 xFLHCx kernel: [  339.409213]  [handle_fasteoi_irq+0x86/0xe0] handle_fasteoi_irq+0x86/0xe0
Aug 29 19:00:15 xFLHCx kernel: [  339.409221]  [do_IRQ+0x3b/0x70] do_IRQ+0x3b/0x70
Aug 29 19:00:15 xFLHCx kernel: [  339.409227]  [__do_softirq+0x82/0x110] __do_softirq+0x82/0x110
Aug 29 19:00:15 xFLHCx kernel: [  339.409236]  [common_interrupt+0x23/0x30] common_interrupt+0x23/0x30
Aug 29 19:00:15 xFLHCx kernel: [  339.409254]  [hpet_readl+0x8/0x10] hpet_readl+0x8/0x10
Aug 29 19:00:15 xFLHCx kernel: [  339.409260]  [read_hpet+0xa/0x10] read_hpet+0xa/0x10
Aug 29 19:00:15 xFLHCx kernel: [  339.409262]  [snd_pcm:getnstimeofday+0x34/0x9830] getnstimeofday+0x34/0xe0
Aug 29 19:00:15 xFLHCx kernel: [  339.409272]  [snd_pcm:ktime_get_ts+0x1e/0x4f0] ktime_get_ts+0x1e/0x60
Aug 29 19:00:15 xFLHCx kernel: [  339.409279]  [ktime_get+0x18/0x40] ktime_get+0x18/0x40
Aug 29 19:00:15 xFLHCx kernel: [  339.409288]  [tick_nohz_restart_sched_tick+0x2e/0x140] tick_nohz_restart_sched_tick+0x2e/0x140
Aug 29 19:00:15 xFLHCx kernel: [  339.409300]  [cpu_idle+0x87/0xd0] cpu_idle+0x87/0xd0
Aug 29 19:00:15 xFLHCx kernel: [  339.409331]  =======================
Aug 29 19:00:15 xFLHCx kernel: [  339.409332] handlers:
Aug 29 19:00:15 xFLHCx kernel: [  339.409333] [<f88a0b80>] (usb_hcd_irq+0x0/0x60 [usbcore])
Aug 29 19:00:15 xFLHCx kernel: [  339.409349] Disabling IRQ #17
Aug 29 19:00:20 xFLHCx kernel: [  341.125790] WARNING: at /build/buildd/linux-2.6.24/drivers/usb/host/ehci-hcd.c:869 ehci_urb_dequeue()
Aug 29 19:00:20 xFLHCx kernel: [  341.125795] Pid: 1504, comm: khubd Tainted: P        2.6.24-19-generic #1
Aug 29 19:00:20 xFLHCx kernel: [  341.125808]  [<f8874b3d>] ehci_urb_dequeue+0x14d/0x160 [ehci_hcd]
Aug 29 19:00:20 xFLHCx kernel: [  341.125831]  [<f88a096f>] unlink1+0x6f/0xe0 [usbcore]
Aug 29 19:00:20 xFLHCx kernel: [  341.125854]  [<f88a1d42>] usb_hcd_unlink_urb+0x12/0x30 [usbcore]
Aug 29 19:00:20 xFLHCx kernel: [  341.125870]  [<f8c2af77>] wrap_cancel_irp+0x77/0xb0 [ndiswrapper]
Aug 29 19:00:20 xFLHCx kernel: [  341.125897]  [<f8c21ba8>] IoCancelIrp+0x38/0x70 [ndiswrapper]
Aug 29 19:00:20 xFLHCx kernel: [  341.125961]  [<f8c26ef4>] mp_init+0xa4/0x1f0 [ndiswrapper]
Aug 29 19:00:20 xFLHCx kernel: [  341.125989]  [<f8c27119>] NdisDispatchPnp+0xd9/0xfc0 [ndiswrapper]
Aug 29 19:00:20 xFLHCx kernel: [  341.126034]  [__switch_to+0x9e/0x150] __switch_to+0x9e/0x150
Aug 29 19:00:20 xFLHCx kernel: [  341.126048]  [lp:schedule+0x20a/0x650] schedule+0x20a/0x600
Aug 29 19:00:20 xFLHCx kernel: [  341.126056]  [ide_core:kunmap_atomic+0x3d/0x2f30] kunmap_atomic+0x3d/0xb0
Aug 29 19:00:20 xFLHCx kernel: [  341.126069]  [<f8c20a41>] IoAllocateIrp+0x61/0x80 [ndiswrapper]
Aug 29 19:00:20 xFLHCx kernel: [  341.126091]  [_spin_lock_bh+0x8/0x20] _spin_lock_bh+0x8/0x20
Aug 29 19:00:20 xFLHCx kernel: [  341.126096]  [<f8c1cc24>] get_current_nt_thread+0x44/0x50 [ndiswrapper]
Aug 29 19:00:20 xFLHCx kernel: [  341.126118]  [<f8c20d35>] IofCallDriver+0x55/0xc0 [ndiswrapper]
Aug 29 19:00:20 xFLHCx kernel: [  341.126143]  [<f8c22731>] IoSendIrpTopDev+0xc1/0x120 [ndiswrapper]
Aug 29 19:00:20 xFLHCx kernel: [  341.126179]  [<f8c22972>] pnp_start_device+0x42/0xa0 [ndiswrapper]
Aug 29 19:00:20 xFLHCx kernel: [  341.126195]  [<f8c299f2>] NdisAddDevice+0x222/0x3e0 [ndiswrapper]
Aug 29 19:00:20 xFLHCx kernel: [  341.126227]  [<f8c22dbf>] wrap_pnp_start_device+0x23f/0x290 [ndiswrapper]
Aug 29 19:00:20 xFLHCx kernel: [  341.126262]  [<f8c234e6>] wrap_pnp_start_usb_device+0xa6/0xd0 [ndiswrapper]
Aug 29 19:00:20 xFLHCx kernel: [  341.126277]  [sysfs_ilookup_test+0x0/0x10] sysfs_ilookup_test+0x0/0x10
Aug 29 19:00:20 xFLHCx kernel: [  341.126290]  [sysfs_find_dirent+0x21/0x30] sysfs_find_dirent+0x21/0x30
Aug 29 19:00:20 xFLHCx kernel: [  341.126292]  [sysfs_addrm_finish+0x14/0x1c0] sysfs_addrm_finish+0x14/0x1c0
Aug 29 19:00:20 xFLHCx kernel: [  341.126297]  [sysfs_add_one+0x44/0xe0] sysfs_add_one+0x44/0xe0
Aug 29 19:00:20 xFLHCx kernel: [  341.126302]  [sysfs_addrm_start+0x3f/0xb0] sysfs_addrm_start+0x3f/0xb0
Aug 29 19:00:20 xFLHCx kernel: [  341.126306]  [snd_pcm:mutex_lock+0x8/0x290] mutex_lock+0x8/0x20
Aug 29 19:00:20 xFLHCx kernel: [  341.126311]  [<f88a482b>] usb_autopm_do_device+0x7b/0x100 [usbcore]
Aug 29 19:00:20 xFLHCx kernel: [  341.126327]  [<f88a4397>] usb_match_one_id+0x27/0xb0 [usbcore]
Aug 29 19:00:20 xFLHCx kernel: [  341.126350]  [<f88a55d9>] usb_probe_interface+0xb9/0x140 [usbcore]
Aug 29 19:00:20 xFLHCx kernel: [  341.126373]  [driver_probe_device+0x88/0x190] driver_probe_device+0x88/0x190
Aug 29 19:00:20 xFLHCx kernel: [  341.126378]  [klist_next+0x55/0xb0] klist_next+0x55/0xb0
Aug 29 19:00:20 xFLHCx kernel: [  341.126389]  [ide_core:bus_for_each_drv+0x44/0x220] bus_for_each_drv+0x44/0x70
Aug 29 19:00:20 xFLHCx kernel: [  341.126401]  [ide_core:device_attach+0x86/0x130] device_attach+0x86/0x90
Aug 29 19:00:20 xFLHCx kernel: [  341.126404]  [__device_attach+0x0/0x10] __device_attach+0x0/0x10
Aug 29 19:00:20 xFLHCx kernel: [  341.126409]  [bus_attach_device+0x45/0x90] bus_attach_device+0x45/0x90
Aug 29 19:00:20 xFLHCx kernel: [  341.126420]  [usbcore:device_add+0x418/0x510] device_add+0x418/0x510
Aug 29 19:00:20 xFLHCx kernel: [  341.126441]  [<f88a3522>] usb_set_configuration+0x392/0x5d0 [usbcore]
Aug 29 19:00:20 xFLHCx kernel: [  341.126485]  [<f88abb06>] generic_probe+0x76/0xb0 [usbcore]
Aug 29 19:00:20 xFLHCx kernel: [  341.126511]  [<f88a5393>] usb_probe_device+0x33/0x40 [usbcore]
Aug 29 19:00:20 xFLHCx kernel: [  341.126524]  [driver_probe_device+0x88/0x190] driver_probe_device+0x88/0x190
Aug 29 19:00:20 xFLHCx kernel: [  341.126529]  [klist_next+0x55/0xb0] klist_next+0x55/0xb0
Aug 29 19:00:20 xFLHCx kernel: [  341.126540]  [ide_core:bus_for_each_drv+0x44/0x220] bus_for_each_drv+0x44/0x70
Aug 29 19:00:20 xFLHCx kernel: [  341.126552]  [ide_core:device_attach+0x86/0x130] device_attach+0x86/0x90
Aug 29 19:00:20 xFLHCx kernel: [  341.126554]  [__device_attach+0x0/0x10] __device_attach+0x0/0x10
Aug 29 19:00:20 xFLHCx kernel: [  341.126560]  [bus_attach_device+0x45/0x90] bus_attach_device+0x45/0x90
Aug 29 19:00:20 xFLHCx kernel: [  341.126570]  [usbcore:device_add+0x418/0x510] device_add+0x418/0x510
Aug 29 19:00:20 xFLHCx kernel: [  341.126591]  [<f889e2f6>] usb_new_device+0x56/0xa0 [usbcore]
Aug 29 19:00:20 xFLHCx kernel: [  341.126615]  [<f889fa97>] hub_thread+0x687/0xcb0 [usbcore]
Aug 29 19:00:20 xFLHCx kernel: [  341.126662]  [<c0140c40>] autoremove_wake_function+0x0/0x40
Aug 29 19:00:20 xFLHCx kernel: [  341.126676]  [<f889f410>] hub_thread+0x0/0xcb0 [usbcore]
Aug 29 19:00:20 xFLHCx kernel: [  341.126690]  [kthread+0x42/0x70] kthread+0x42/0x70
Aug 29 19:00:20 xFLHCx kernel: [  341.126692]  [kthread+0x0/0x70] kthread+0x0/0x70
Aug 29 19:00:20 xFLHCx kernel: [  341.126696]  [kernel_thread_helper+0x7/0x10] kernel_thread_helper+0x7/0x10
Aug 29 19:00:20 xFLHCx kernel: [  341.126707]  =======================

```

---

### Post by javaJake on 2008-08-30
I'm going to continue researching this. I couldn't find an answer today, but I have a small suspicion it's because the kernel developers are starting to crack down on modules like ndiswrapper with questionable legal status.

I may be wrong, though. We'll see.

---

### Post by xFLHCx on 2008-08-31
I guess ubuntu will have to wait til I get my laptop :[

well thank you for everything! you've been a great help.
oh adn I understand that youre busy so again thank you for taking the time out of your day.

---

### Post by JMac82 on 2008-09-02
I was able to get x64-bit drivers for WUSB54GSv2, including the windows .sys files from windows x64-64...works fine, except on reboot with the wireless usb adapter plugged-in.  using:

Hardy Heron, ndiswrapper-1.53, Intel Core2Duo (~2.13GHz), Dell dimension 9100 desktop, blacklisted bcm43xx and b43.
uname -a = Linux jmac 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux

some places say you have to add ndiswrapper to the /etc/modules file, I don't....only has to be aliased in /etc/modprobe.d/ folder.

the specific error i get with the dang thing plugged in only occurs on bootup and says BUG: soft lockup CPU#0 stuck for 11s! [loadndisdriver:4990]

wonder if anybody has found a solution to this!  like I said, I can work around it easy by unplugging the usb adapter until the login screen then replugging and everything works fine.  I haven't seen anybody list this as an alternative workaround to the problem, so I hope this can help SOME people boot into ubuntu to figure some stuff out.

it's interesting to note that if I add ndiswrapper to the /etc/modules file and keep the usb adapter plugged in at reboot, the error is much different...lines and lines of crap, looks like addresses, function/kernel-type stuff calls, etc.

---

### Post by bunuhdiri on 2008-09-03
hi jake
thanks for the guide.it was nicely done
however i couldnt get it working on my ubuntu 8.04 64bit
i'm using wusb54gsc version 1.0..
is it because i'm using 32bit driver?
this is the syslog after i inserted the device..pardon the filename..
```

Sep  4 02:06:14 tomz-desktop kernel: [ 1388.573538] usb 2-5: new high speed USB device using ehci_hcd and address 6
Sep  4 02:06:14 tomz-desktop kernel: [ 1388.707481] usb 2-5: configuration #1 chosen from 1 choice
Sep  4 02:06:14 tomz-desktop kernel: [ 1388.707541] usb 2-5: bad CDC descriptors
Sep  4 02:06:14 tomz-desktop NetworkManager: <debug> [1220465174.286879] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13b1_26_8057'). 
Sep  4 02:06:14 tomz-desktop NetworkManager: <debug> [1220465174.336257] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Sep  4 02:06:14 tomz-desktop kernel: [ 1388.824248] usb 2-5: reset high speed USB device using ehci_hcd and address 6
Sep  4 02:06:14 tomz-desktop loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver wusb54gsck 
Sep  4 02:06:14 tomz-desktop kernel: [ 1388.979240] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
Sep  4 02:06:14 tomz-desktop kernel: [ 1388.979248] ndiswrapper (load_sys_files:210): couldn't prepare driver 'wusb54gsck'
Sep  4 02:06:14 tomz-desktop kernel: [ 1388.979547] ndiswrapper (load_wrap_driver:112): couldn't load driver wusb54gsck; check system log for messages from 'loadndisdriver'
Sep  4 02:06:14 tomz-desktop NetworkManager: <debug> [1220465174.600390] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13b1_26_8057_if1'). 
tomz@tomz-desktop:~$ 

```

---

### Post by JMac82 on 2008-09-04
bunuhdiri - I can help you with that since I had the exact same error...."bad magic, 64-bit kernel, etc."  yep, you need 64-bit drivers.  you can manually edit the .inf file to make it 64-bit compatible (which is what I did), but you need 64-bit windows .sys files from a 64-bit windows operating system installation.  I got those 64-bit .sys files off of a planetamd forum site - saved the link:
[http://www.planetamd64.com/index.php?showtopic=19228](http://www.planetamd64.com/index.php?showtopic=19228)

had to sign up for a forum membership, but after downloading a few packages I found one that worked.  good luck!

---

### Post by JMac82 on 2008-09-04
javajake - I'm wondering if other people with ubuntu versions > 7.04 DIDN'T have to do the udev custom rule echo '1' to bConfigurationValue file step.  I'm running Hardy and this was already done for me (i haven't found anything in the udev rules doing what you said to do, and there was already a bConfigurationValue file with the value '1' in it at the appropriate /sys/$devpath location when I installed the driver and did the whole modprobe ndiswrapper thing (fresh install of ubuntu too!)).  I'm wondering if newer versions of ndiswrapper do this for you automatically, or if Hardy does it for you automatically.  thanks for the great tutorial!

---

### Post by bunuhdiri on 2008-09-08
> **JMac82 said:**
> bunuhdiri - I can help you with that since I had the exact same error...."bad magic, 64-bit kernel, etc."  yep, you need 64-bit drivers.  you can manually edit the .inf file to make it 64-bit compatible (which is what I did), but you need 64-bit windows .sys files from a 64-bit windows operating system installation.  I got those 64-bit .sys files off of a planetamd forum site - saved the link:
[http://www.planetamd64.com/index.php?showtopic=19228](http://www.planetamd64.com/index.php?showtopic=19228)

had to sign up for a forum membership, but after downloading a few packages I found one that worked.  good luck!

too bad that my adapter just dead yesterday. i will have to wait for rma process before i could follow your guide,:(

---

### Post by rsilva4 on 2008-09-10
Hi guys,

For those still struggling to get this working, here how I did it (no ndiswrapper):

1. Download [compat-wireless]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2").
2. Unpack it.
3. Go to the unpacked directory
4. ```
make
```
5. ```
sudo make install
```
6. ```
make unload
```
7. ```
make load
```

All done! Plug-in your device and check **iwconfig** for success conformation.

**I tried to use checkinstall and make a package but had some troubles**, also you well need some deps like build-essential.

This method is valid until Ubuntu provides a kernel >=2.6.25, after that you will not have to do any of this.

---

### Post by jamesclayden on 2008-09-16
i have ubuntu 8.04 and i have used the first method listed to get the driver installed and working with ndiswraper. My device still does not work. The drive recognizes that it is plugged in but not power lights come on. I have done the additional bit on the first post to allow more power to the usb. 

can anyone offer any help please.

PS i have v02 device and i am running ubuntu off the cd till i know i can get this working.

---

### Post by javaJake on 2008-09-28
> **jamesclayden said:**
> i have ubuntu 8.04 and i have used the first method listed to get the driver installed and working with ndiswraper. My device still does not work. The drive recognizes that it is plugged in but not power lights come on. I have done the additional bit on the first post to allow more power to the usb. 

can anyone offer any help please.

PS i have v02 device and i am running ubuntu off the cd till i know i can get this working.

Run the following after plugging in the device and post the output here:

```
sudo tail -n100 /var/log/messages
cat /etc/udev/rules.d/99-custom.rules
ls -R /etc/ndiswrapper/
ndiswrapper -l
```

---

### Post by jamesclayden on 2008-09-28
thank you for the help JJ

Have done that. Here is the output

i have attached them as txt files to save space on the page

---

### Post by Plasticjesus690 on 2008-09-29
Every time I use either the gui ndiswrapper or the command line it installs the driver and then says invaild driver I could really use some help I have WUSB54GSC and Ubuntu 8.04 also when i tried installing ndiswrapper  version 1.53 it said cannot install on this machine i386 not supported any help wouldbe great

---

### Post by javaJake on 2008-10-30
**_Ubuntu 8.10 (Intrepid) Deprecates This HOWTO!_**
That's right! This HOWTO is officially deprecated as of Ubuntu Intrepid. ndiswrapper is no longer needed. As soon as you plug in the WUSB54GS while running Ubuntu Intrepid, it should immediately function!

---

### Post by daniel_smith1984 on 2008-11-12
i get all the way to step 5 and i get 

daniel@daniel-laptop:~/Desktop/ndiswrapper-files/v1$ sudo ndiswrapper -i WUSB54GSv2.inf
sudo: ndiswrapper: command not found

if i go "ls" i can see WUSB54GSv2.inf

what do i do?

---

### Post by javaJake on 2008-11-13
> **daniel_smith1984 said:**
> i get all the way to step 5 and i get 

daniel@daniel-laptop:~/Desktop/ndiswrapper-files/v1$ sudo ndiswrapper -i WUSB54GSv2.inf
sudo: ndiswrapper: command not found

if i go "ls" i can see WUSB54GSv2.inf

what do i do?

It's telling you ndiswrapper isn't installed. Make sure you did steps 1 through 3 fully.

Also, consider upgrading to Ubuntu 8.10 Intrepid. It supports the WUSB54GS as soon as you plug it in. :)

---

### Post by JonathanCasey on 2009-02-14
Has anyone successfully got WUSB54GS v1 to work in the Intrepid 64-bit?

I originally tried just plugging it in but found:

the following commands hang with no output:
   sudo lsusb
   sudo ndiswarpper -l

When I boot up / shut down, the system hangs when it says:
 "*Initilise bluetooth devices..."
 /"*stopping bluetooth devices..."

If I unplug the wireless device it works fine.

When ever I plugin the device while in ubuntu and run "dmesg". I get a whole load of horrible errors starting with the first line saying: "kernel BUG at /build/buildd/linux-2.6.27/kernel/workqueue.c:188!"

When doing the step-by-step manual install (having completely removed all existence of ndiswrapper) i found it all seemed to go fine untill I did the last step about increasing the power-output to the device.

Then I got the same "kernel BUG at /build/buildd/linux-2.6.27/kernel/workqueue.c:188!" error when I plugged in the device (as well as lsusb and ndiswarpper -l both hanging without any output)

I am using a fresh, latest install of 64-bit Intrepid Ibex with everything full updated and the latest kernel.

I can only assume that I am having this problem because I'm running 64-bit and I'm trying to use the 32bit drivers you supplied.

Has anyone been able to find some v1 64-bit drivers that actually work?

I've looked far and wide and keep finding links to 64-bit v2 drivers, but nothing for WUSB54GS v1. :(

I've wasted a few days now trying to get this to work so I'de be very greatfull for some help.

Here is the ugly dmesg output:

```

[ 6047.633031] usb 3-8: new high speed USB device using ehci_hcd and address 3
[ 6047.776074] usb 3-8: configuration #1 chosen from 1 choice
[ 6047.896024] usb 3-8: reset high speed USB device using ehci_hcd and address 3
[ 6048.034902] ndiswrapper (import:242): unknown symbol: RNDISMPK.SYS:'RndisMSendComplete'
[ 6048.034923] ndiswrapper (import:242): unknown symbol: RNDISMPK.SYS:'RndisMInitializeWrapper'
[ 6048.034929] ndiswrapper (import:242): unknown symbol: RNDISMPK.SYS:'RndisMIndicateReceive'
[ 6048.034933] ndiswrapper (load_sys_files:206): couldn't prepare driver 'wusb54gs'
[ 6048.038341] ndiswrapper (load_wrap_driver:108): couldn't load driver wusb54gs; check system log for messages from 'loadndisdriver'
[ 6048.445463] rndis_wlan 3-8:1.0: rndis media disconnect
[ 6048.445495] ------------[ cut here ]------------
[ 6048.445499] kernel BUG at /build/buildd/linux-2.6.27/kernel/workqueue.c:188!
[ 6048.445502] invalid opcode: 0000 [#1] SMP 
[ 6048.445506] Modules linked in: rndis_wlan rndis_host cdc_ether usbnet ndiswrapper af_packet binfmt_misc radeon drm bridge stp rfcomm bnep sco l2cap bluetooth ipv6 ppdev cpufreq_powersave cpufreq_conservative cpufreq_stats cpufreq_ondemand freq_table cpufreq_userspace video output pci_slot wmi container sbs sbshc battery iptable_filter ip_tables x_tables ac sbp2 lp serio_raw evdev psmouse pcspkr k8temp shpchp pci_hotplug snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device button parport_pc parport i2c_nforce2 i2c_core snd soundcore snd_page_alloc amd64_agp agpgart isp1760 ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif sg pata_acpi pata_amd sata_nv r8169 ata_generic ohci1394 mii libata ieee1394 ohci_hcd scsi_mod dock ehci_hcd forcedeth usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[ 6048.445574] 
[ 6048.445577] Pid: 1321, comm: khubd Tainted: P          (2.6.27-11-generic #1)
[ 6048.445580] EIP: 0060:[<c0143ff6>] EFLAGS: 00010213 CPU: 1
[ 6048.445587] EIP is at queue_work_on+0x56/0x60
[ 6048.445589] EAX: f103e06c EBX: 00000000 ECX: f103e068 EDX: 00000000
[ 6048.445592] ESI: 00000001 EDI: f070a000 EBP: f6b69b00 ESP: f6b69af8
[ 6048.445594]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[ 6048.445597] Process khubd (pid: 1321, ti=f6b68000 task=f780b240 task.ti=f6b68000)
[ 6048.445600] Stack: 00000000 f103e1f8 f6b69b0c c01440fa f103e08c f6b69b18 f8e8813f e9480c80 
[ 6048.445607]        f6b69b6c f8e983cd f8e98bfc f8e8b530 f070a0b8 f8e98be8 00000401 00001388 
[ 6048.445613]        00000401 f8e98be8 e9480d50 00000000 00000000 80000005 0000000c 00000000 
[ 6048.445620] Call Trace:
[ 6048.445622]  [<c01440fa>] ? queue_work+0x1a/0x20
[ 6048.445627]  [<f8e8813f>] ? rndis_wext_link_change+0x2f/0x40 [rndis_wlan]
[ 6048.445635]  [<f8e983cd>] ? rndis_command+0x1bd/0x2d0 [rndis_host]
[ 6048.445652]  [<f8e883e4>] ? rndis_set_oid+0xa4/0x170 [rndis_wlan]
[ 6048.445657]  [<f8e8a9af>] ? rndis_wext_bind+0xaf/0x1f0 [rndis_wlan]
[ 6048.445663]  [<f8e92106>] ? usbnet_probe+0x226/0x480 [usbnet]
[ 6048.445669]  [<c01c7355>] ? iput+0x25/0x60
[ 6048.445683]  [<f88b0ea9>] ? usb_autopm_do_device+0x69/0xf0 [usbcore]
[ 6048.445710]  [<f88b1577>] ? usb_probe_interface+0xa7/0x140 [usbcore]
[ 6048.445723]  [<c0201707>] ? sysfs_create_link+0x17/0x20
[ 6048.445736]  [<c02c49be>] ? really_probe+0xee/0x190
[ 6048.445743]  [<f88b0939>] ? usb_match_id+0x49/0x60 [usbcore]
[ 6048.445764]  [<c02c4aa3>] ? driver_probe_device+0x43/0x60
[ 6048.445768]  [<c02c4b4d>] ? __device_attach+0xd/0x10
[ 6048.445772]  [<c02c3f1b>] ? bus_for_each_drv+0x5b/0x80
[ 6048.445778]  [<c02c4c06>] ? device_attach+0x76/0x80
[ 6048.445782]  [<c02c4b40>] ? __device_attach+0x0/0x10
[ 6048.445788]  [<c02c3d27>] ? bus_attach_device+0x47/0x70
[ 6048.445792]  [<c02c296b>] ? device_add+0x33b/0x400
[ 6048.445798]  [<f88af6bf>] ? usb_control_msg+0xcf/0xe0 [usbcore]
[ 6048.445814]  [<f88afed4>] ? usb_cache_string+0x14/0xa0 [usbcore]
[ 6048.445830]  [<f88b036f>] ? usb_set_configuration+0x40f/0x5e0 [usbcore]
[ 6048.445846]  [<f88b03af>] ? usb_set_configuration+0x44f/0x5e0 [usbcore]
[ 6048.445865]  [<f88b84d3>] ? generic_probe+0x33/0xa0 [usbcore]
[ 6048.445880]  [<c0201707>] ? sysfs_create_link+0x17/0x20
[ 6048.445889]  [<f88b0751>] ? usb_probe_device+0x41/0x50 [usbcore]
[ 6048.445903]  [<c02c49be>] ? really_probe+0xee/0x190
[ 6048.445912]  [<c02c4aa3>] ? driver_probe_device+0x43/0x60
[ 6048.445916]  [<c02c4b4d>] ? __device_attach+0xd/0x10
[ 6048.445920]  [<c02c3f1b>] ? bus_for_each_drv+0x5b/0x80
[ 6048.445927]  [<c02c4c06>] ? device_attach+0x76/0x80
[ 6048.445930]  [<c02c4b40>] ? __device_attach+0x0/0x10
[ 6048.445936]  [<c02c3d27>] ? bus_attach_device+0x47/0x70
[ 6048.445940]  [<c02c296b>] ? device_add+0x33b/0x400
[ 6048.445944]  [<c037e260>] ? mutex_lock+0x10/0x20
[ 6048.445950]  [<f88aa79b>] ? usb_new_device+0x5b/0xb0 [usbcore]
[ 6048.445968]  [<f88ab0f7>] ? hub_port_connect_change+0x457/0x9b0 [usbcore]
[ 6048.445984]  [<f88af6bf>] ? usb_control_msg+0xcf/0xe0 [usbcore]
[ 6048.445998]  [<c037e208>] ? mutex_unlock+0x8/0x20
[ 6048.446004]  [<f88ab94c>] ? hub_events+0x1fc/0x640 [usbcore]
[ 6048.446018]  [<c014765f>] ? finish_wait+0x4f/0x70
[ 6048.446024]  [<f88abdc5>] ? hub_thread+0x35/0x150 [usbcore]
[ 6048.446038]  [<c0147560>] ? autoremove_wake_function+0x0/0x50
[ 6048.446044]  [<f88abd90>] ? hub_thread+0x0/0x150 [usbcore]
[ 6048.446057]  [<c01471f1>] ? kthread+0x41/0x80
[ 6048.446061]  [<c01471b0>] ? kthread+0x0/0x80
[ 6048.446065]  [<c0105297>] ? kernel_thread_helper+0x7/0x10
[ 6048.446070]  =======================
[ 6048.446071] Code: 39 41 04 75 26 8b 43 10 85 c0 74 06 8b 35 70 54 4a c0 8b 03 89 ca f7 d0 8b 04 b0 e8 25 ff ff ff ba 01 00 00 00 89 d0 5b 5e 5d c3 <0f> 0b eb fe 8d b6 00 00 00 00 55 89 e5 e8 98 12 fc ff 89 d1 8b 
[ 6048.446104] EIP: [<c0143ff6>] queue_work_on+0x56/0x60 SS:ESP 0068:f6b69af8
[ 6048.446110] ---[ end trace 09f1e41f84666450 ]---

```

So... Anyone know how I can get my WUSB54GS v1 to work in 64-bit intrepid? :)

Jon.

---

### Post by JonathanCasey on 2009-02-23
Nobody had any success with this then?? :(

---

### Post by javaJake on 2009-03-01
No, 64-bit drivers are known not to work. They are not supported by this HOWTO.

However, this HOWTO is now out-dated, and no longer needed, since Ubuntu includes drivers for WUSB54GS by default. You should not have to use ndiswrapper any longer. I recommend you undo anything you've done in this HOWTO and just try plugging in the WUSB54GS device with no extra setup.

---

### Post by Laundry on 2009-03-17
Sorry to bump this, but I've been trying to get my WUSB54GS v1 to work for awhile, but haven't had any success.  I've tried several distros, but I get the same error in every one.  When I attempt to do the command "ifconfig wlan0 up", I get the error "SIOCSIFFLAGS: Cannot assign requested address."  The interface is actually working somewhat, though.  I can scan and find the wireless networks that are in my house.  I have no idea at all why it would be doing this, and I don't think I'm going to get anywhere soon.  I've tried configuring the network using other tools such as wicd, but they do not connect either.  Wicd hangs at "None: Obtaining IP address", or something similar, I can't remember the exact error message.

I've got a feeling this has something to do with the hardware, because I've never heard of anybody else having any problems similar to mine.  Does anybody have any advice that could help me get this working?

---

### Post by evilspy on 2009-04-22
Hello!

Could you test patch "Fix too late initialization of workqueue/work" 
at [http://bugzilla.kernel.org/show_bug.cgi?id=12794](http://bugzilla.kernel.org/show_bug.cgi?id=12794) and report if it works?

---

### Post by Pitxyoki on 2009-05-15
Hi,
I submitted this info to the kernel.org bugzilla, but as that bug has been closed, I'm sending a copy of it here too:


Using kernel 2.6.30-rc5, there is no segfault anymore.

However, my wireless adapter is still not connecting. It is shown on ifconfig and iwconfig, but ifupping it does not work.
Notice that the MAC address for the interface is still shown as 01:0a:00:00:00:00.

See below the output for ifconfig and iwconfig.

When I plug it in, /var/log/syslog shows:
```

May 15 18:10:15 C-5 kernel: [  101.576026] usb 2-2: new full speed USB device using uhci_hcd and address 3
May 15 18:10:15 C-5 kernel: [  101.751319] usb 2-2: New USB device found, idVendor=13b1, idProduct=000e
May 15 18:10:15 C-5 kernel: [  101.751324] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
May 15 18:10:15 C-5 kernel: [  101.751328] usb 2-2: Product: Linksys Wireless-G USB Network Adapter with SpeedBooster
May 15 18:10:15 C-5 kernel: [  101.751332] usb 2-2: Manufacturer: Cisco-Linksys
May 15 18:10:15 C-5 kernel: [  101.751335] usb 2-2: SerialNumber: 1111
May 15 18:10:15 C-5 kernel: [  101.751452] usb 2-2: configuration #1 chosen from 1 choice
May 15 18:10:15 C-5 kernel: [  101.886551] usbcore: registered new interface driver cdc_ether
May 15 18:10:16 C-5 kernel: [  102.046373] usbcore: registered new interface driver rndis_host
May 15 18:10:16 C-5 kernel: [  102.337315] rndis_wlan 2-2:1.0: rndis media disconnect
May 15 18:10:16 C-5 kernel: [  102.492425] wlan0: register 'rndis_wlan' at usb-0000:00:1d.1-2, Wireless RNDIS device, BCM4320a based, 01:0a:00:00:00:00
May 15 18:10:16 C-5 kernel: [  102.492461] usbcore: registered new interface driver rndis_wlan
```



```
[18:10:30] C-5:~# ifconfig -a
eth1      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)

wlan0     Link encap:Ethernet  HWaddr 01:0a:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

[18:10:34] C-5:~# iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[18:10:37] C-5:~# ifup wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
Listening on LPF/wlan0/01:0a:00:00:00:00
Sending on   LPF/wlan0/01:0a:00:00:00:00
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
No DHCPOFFERS received.
```




Also, I noticed that this gets written to /etc/udev/rules.d/70-persistent-net.rules :

```
[18:12:13] C-5:~# cat /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x11ab:0x4362 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="XX:XX:XX:XX:XX:XX", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# USB device 0x:0x (rndis_wlan)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="01:0a:00:00:00:00", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
```



Regards,
  Pitxyoki

---

### Post by panfyre on 2009-08-31
In the modprobe section I got a warning that I have not seen elsewhere.  


WARNING: All config files need .config : /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.


I noted that this folder doesnt even exist.  I also went through the Ubuntu 7.1 + configurations and the light does not come on.  The checks do say that the driver is installed.  Any ideas where I went wrong?  I do understand this is an old post, I hope someone will talk to me from the past I guess...lol.

Thank you in advance.

Panfyre

---

### Post by javaJake on 2009-09-03
> **panfyre said:**
>  Any ideas where I went wrong?  I do understand this is an old post, I hope someone will talk to me from the past I guess...lolThe device should work as soon as you plug it in now. Reinstall the latest Ubuntu (9.04 at the time of this writing) and just plug it in, without configuring anything.

---

### Post by BarkingPerci on 2009-09-29
Could anyone confirm that this device is fully supported under 9.04?

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833124126&cm_mmc=SNC-Twitter-_-na-_-na-_-na](http://www.newegg.com/Product/Product.aspx?Item=N82E16833124126&cm_mmc=SNC-Twitter-_-na-_-na-_-na)

It's a great deal, but I have no desire to purchase an unsupported device. Thanks.

* bah sale is over - was $25 for a time - I'll go with the EDIMAX EW-7128G instead

---

### Post by Pitxyoki on 2009-10-01
The device should work relatively well with a recent kernel. There were some "serious" problems with the module some time ago, but most were corrected by version 2.6.30, if I'm not mistaken.

The module still has some issues such as suddenly losing the connection and being unable to recover from it. If you use a static configuration based on /etc/network/interfaces there may also be some problems when trying to connect to the AP for the first time (on each reboot/adapter connection). If you use network-manager, it may be able to overcome *some* of those problems - IIRC Ubuntu uses network-manager by default.

---

### Post by Pitxyoki on 2010-05-10
Ubuntu 10.04 (Lucid Lynx) ships with Linux kernel version 2.6.32. The patches that correct the issues with this card were merged from the 2.6.32.10 release and as such this card is finally, fully supported.

I just tested it with the live CD and everything went well. There's no need for any configuration steps specific to the card anymore. :)

---

### Post by javaJake on 2010-05-10
> **Pitxyoki said:**
> Ubuntu 10.04 (Lucid Lynx) ships with Linux kernel version 2.6.32. The patches that correct the issues with this card were merged from the 2.6.32.10 release and as such this card is finally, fully supported.

I just tested it with the live CD and everything went well. There's no need for any configuration steps specific to the card anymore. :)

[COLOR="Silver"]Thanks for your input! The adapter has actually worked since 8.10. I'm guessing, given the versions you've missed in between, you stick to LTS releases, so you didn't discover that until now.

Linux hardware support is almost perfect, I've found. There are a few spots, but it's mostly superb. That says how big Linux finally has come to be. :)[/COLOR]

**Edit:** Nevermind, I get it. Your post was a followup to a bug found in earlier Ubuntu versions since 8.10. Ignore my reply.

---

### Post by Pitxyoki on 2010-10-22
Does any of you who are using NetworkManager notice that this card (mine is a "v1") takes a long time to detect your network's ESSID?
Something like 15 to 30 minutes since you boot your computer?

If you are using /etc/network/interfaces to configure the card you might not notice the delay in detecting the beacon.

Thanks in advance.

---

### Post by Dalem50 on 2010-12-23
Will this work on a 64-bit machine if you install ia32-libs?

---

### Post by Pitxyoki on 2010-12-23
Did you even read anything on this thread? You don't need to do anything anymore.

---

