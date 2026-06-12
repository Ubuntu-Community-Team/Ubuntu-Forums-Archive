---
title: "Hardy not seeing mp3"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by jtclicker on 2008-05-11
Just tried to plug my mp3 into the usb slot of the pc for the first time since the hardy upgrade, and it doesn't 'see' the player. Any ideas?

---

### Post by SunnyRabbiera on 2008-05-11
well you can give us the model for starters, I am no expert in MP3's but you can at least give others the information they will need.

---

### Post by Yannick Le Saint kyncani on 2008-05-11
You could start checking the logs with "dmesg" and see what happens when you plug the player in.

---

### Post by WBL on 2008-05-11
> **jtclicker said:**
> Just tried to plug my mp3 into the usb slot of the pc for the first time since the hardy upgrade, and it doesn't 'see' the player. Any ideas?

Did you enable restricted formats?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

-WBL

---

### Post by jtclicker on 2008-05-11
sorry for the lack of info but I'm really pissed when I find something else that worked in Gutsy that doesn't work in Hardy. The wierd thing is that when I boot up with the player sansa sandik clip attached to the usb port it is recognised. When I just plug it in it won't even charge the player up. I forgot to reenable the restricted formats after the upgrade. That did it! Thanks

---

### Post by WBL on 2008-05-11
> **jtclicker said:**
> sorry for the lack of info but I'm really pissed when I find something else that worked in Gutsy that doesn't work in Hardy. The wierd thing is that when I boot up with the player sansa sandik clip attached to the usb port it is recognised. When I just plug it in it won't even charge the player up. I forgot to reenable the restricted formats after the upgrade. That did it! Thanks

No problem man.  Thanks for the "thanks."  :)

-WBL

---

### Post by jtclicker on 2008-05-11
Actually that didn't solve. It did for a while, then I rebooted and had the same problem again. Kinda weird it fixed it first time around and now not. Logs show this..

[   59.683231] usb 5-8: new high speed USB device using ehci_hcd and address 4
[   63.153322] ehci_hcd 0000:00:1d.7: port 8 reset error -110
[   63.153331] hub 5-0:1.0: hub_port_status failed (err = -32)
[   64.097768] eth0: no IPv6 routers present
[   98.516043] usb 5-8: new high speed USB device using ehci_hcd and address 5
[  101.846418] ehci_hcd 0000:00:1d.7: port 8 reset error -110
[  101.846427] hub 5-0:1.0: hub_port_status failed (err = -32)
[  247.536810] usb 5-7: new high speed USB device using ehci_hcd and address 6
[  247.729912] ehci_hcd 0000:00:1d.7: port 7 reset error -110
[  247.729920] hub 5-0:1.0: hub_port_status failed (err = -32)
[  370.301819] usb 5-7: new high speed USB device using ehci_hcd and address 7
[  370.808733] usb 5-7: new high speed USB device using ehci_hcd and address 8
[  370.954228] usb 5-7: configuration #1 chosen from 1 choice
[  370.982121] scsi5 : SCSI emulation for USB Mass Storage devices
[  370.988384] usb-storage: device found at 8
[  370.988390] usb-storage: waiting for device to settle before scanning
[  375.979541] usb-storage: device scan complete
[  375.980665] scsi 5:0:0:0: Direct-Access     SanDisk  Sansa Clip 2GB   v01. PQ: 0 ANSI: 0
[  375.992629] sd 5:0:0:0: [sdd] 3992576 512-byte hardware sectors (2044 MB)
[  376.000243] sd 5:0:0:0: [sdd] Write Protect is off
[  376.000249] sd 5:0:0:0: [sdd] Mode Sense: 04 00 00 00
[  376.000251] sd 5:0:0:0: [sdd] Assuming drive cache: write through
[  376.002842] sd 5:0:0:0: [sdd] 3992576 512-byte hardware sectors (2044 MB)
[  376.003721] sd 5:0:0:0: [sdd] Write Protect is off
[  376.003726] sd 5:0:0:0: [sdd] Mode Sense: 04 00 00 00
[  376.003728] sd 5:0:0:0: [sdd] Assuming drive cache: write through
[  376.003734]  sdd: unknown partition table
[  376.010371] sd 5:0:0:0: [sdd] Attached SCSI removable disk
[  376.010420] sd 5:0:0:0: Attached scsi generic sg5 type 0
[  378.601804] scsi 5:0:0:0: rejecting I/O to dead device

But while doing this command in terminal the mp3 came alive... it is now charging and has triggered the audio player but it isn't present in the file system, and there is no icon to 'mount' or 'unmount' the drive

---

### Post by Yannick Le Saint kyncani on 2008-05-11
> **jtclicker said:**
> [  378.601804] scsi 5:0:0:0: rejecting I/O to dead device

Looks like a bad contact, try removing the device, clean the connectors and attach it while looking at the logs.

---

### Post by jtclicker on 2008-05-12
> **Yannick Le Saint kyncani said:**
> Looks like a bad contact, try removing the device, clean the connectors and attach it while looking at the logs.

Thanks. I tried that and no luck. It works in windows, and it works if I have the mp3 in during boot up. Here is the latest log

  59.683231] usb 5-8: new high speed USB device using ehci_hcd and address 4
[   63.153322] ehci_hcd 0000:00:1d.7: port 8 reset error -110
[   63.153331] hub 5-0:1.0: hub_port_status failed (err = -32)
[   64.097768] eth0: no IPv6 routers present
[   98.516043] usb 5-8: new high speed USB device using ehci_hcd and address 5
[  101.846418] ehci_hcd 0000:00:1d.7: port 8 reset error -110
[  101.846427] hub 5-0:1.0: hub_port_status failed (err = -32)
[  247.536810] usb 5-7: new high speed USB device using ehci_hcd and address 6
[  247.729912] ehci_hcd 0000:00:1d.7: port 7 reset error -110
[  247.729920] hub 5-0:1.0: hub_port_status failed (err = -32)
[  370.301819] usb 5-7: new high speed USB device using ehci_hcd and address 7
[  370.808733] usb 5-7: new high speed USB device using ehci_hcd and address 8
[  370.954228] usb 5-7: configuration #1 chosen from 1 choice
[  370.982121] scsi5 : SCSI emulation for USB Mass Storage devices
[  370.988384] usb-storage: device found at 8
[  370.988390] usb-storage: waiting for device to settle before scanning
[  375.979541] usb-storage: device scan complete
[  375.980665] scsi 5:0:0:0: Direct-Access     SanDisk  Sansa Clip 2GB   v01. PQ: 0 ANSI: 0
[  375.992629] sd 5:0:0:0: [sdd] 3992576 512-byte hardware sectors (2044 MB)
[  376.000243] sd 5:0:0:0: [sdd] Write Protect is off
[  376.000249] sd 5:0:0:0: [sdd] Mode Sense: 04 00 00 00
[  376.000251] sd 5:0:0:0: [sdd] Assuming drive cache: write through
[  376.002842] sd 5:0:0:0: [sdd] 3992576 512-byte hardware sectors (2044 MB)
[  376.003721] sd 5:0:0:0: [sdd] Write Protect is off
[  376.003726] sd 5:0:0:0: [sdd] Mode Sense: 04 00 00 00
[  376.003728] sd 5:0:0:0: [sdd] Assuming drive cache: write through
[  376.003734]  sdd: unknown partition table
[  376.010371] sd 5:0:0:0: [sdd] Attached SCSI removable disk
[  376.010420] sd 5:0:0:0: Attached scsi generic sg5 type 0
[  378.601804] scsi 5:0:0:0: rejecting I/O to dead device
[  388.650573] usb 5-7: reset high speed USB device using ehci_hcd and address 8
[  623.607185] usb 5-7: reset high speed USB device using ehci_hcd and address 8
[  930.150523] usb 5-7: USB disconnect, address 8
[  963.319459] usb 5-8: new high speed USB device using ehci_hcd and address 9
[  966.586364] ehci_hcd 0000:00:1d.7: port 8 reset error -110
[  966.586373] hub 5-0:1.0: hub_port_status failed (err = -32)
[ 1005.580914] usb 5-8: new high speed USB device using ehci_hcd and address 10
[ 1008.873872] usb 5-8: device descriptor read/64, error -71
[ 1068.546042] usb 5-8: new high speed USB device using ehci_hcd and address 11
[ 1071.868432] ehci_hcd 0000:00:1d.7: port 8 reset error -110
[ 1071.868441] hub 5-0:1.0: hub_port_status failed (err = -32)
[ 1244.101951] usb 5-8: new high speed USB device using ehci_hcd and address 12
[ 1247.603956] ehci_hcd 0000:00:1d.7: port 8 reset error -110
[ 1247.603965] hub 5-0:1.0: hub_port_status failed (err = -32)
[ 3429.404556] usb 5-7: new high speed USB device using ehci_hcd and address 13
[ 3432.790809] ehci_hcd 0000:00:1d.7: port 7 reset error -110
[ 3432.790817] hub 5-0:1.0: hub_port_status failed (err = -32)
[ 9281.384346] usb 5-8: new high speed USB device using ehci_hcd and address 14
[ 9284.786566] ehci_hcd 0000:00:1d.7: port 8 reset error -110
[ 9284.786575] hub 5-0:1.0: hub_port_status failed (err = -32)
[13405.637287] usb 5-8: new high speed USB device using ehci_hcd and address 15
[13408.991610] ehci_hcd 0000:00:1d.7: port 8 reset error -110
[13408.991619] hub 5-0:1.0: hub_port_status failed (err = -32)
[50827.571346] usb 5-8: new high speed USB device using ehci_hcd and address 16
[50830.961590] ehci_hcd 0000:00:1d.7: port 8 reset error -110
[50830.961600] hub 5-0:1.0: hub_port_status failed (err = -32)
[50838.471989] usb 5-8: new high speed USB device using ehci_hcd and address 17
[50838.625734] usb 5-8: configuration #1 chosen from 1 choice
[50838.654576] scsi6 : SCSI emulation for USB Mass Storage devices
[50838.655927] usb-storage: device found at 17
[50838.655932] usb-storage: waiting for device to settle before scanning
[50838.727783] usb 5-8: USB disconnect, address 17
[50838.970923] usb 5-8: new high speed USB device using ehci_hcd and address 18
[50839.124976] usb 5-8: configuration #1 chosen from 1 choice
[50839.131580] scsi7 : SCSI emulation for USB Mass Storage devices
[50839.132065] usb-storage: device found at 18
[50839.132070] usb-storage: waiting for device to settle before scanning
[50840.319529] usb 5-8: USB disconnect, address 18
[50841.349820] usb 5-8: new high speed USB device using ehci_hcd and address 19
[50841.492430] usb 5-8: configuration #1 chosen from 1 choice
[50841.525460] scsi8 : SCSI emulation for USB Mass Storage devices
[50841.529508] usb-storage: device found at 19
[50841.529513] usb-storage: waiting for device to settle before scanning
[50844.280239] usb 5-8: USB disconnect, address 19
[50848.135283] usb 5-8: new high speed USB device using ehci_hcd and address 20
[50848.281189] usb 5-8: configuration #1 chosen from 1 choice
[50848.309240] scsi9 : SCSI emulation for USB Mass Storage devices
[50848.314938] usb-storage: device found at 20
[50848.314943] usb-storage: waiting for device to settle before scanning
[50853.305508] usb-storage: device scan complete
[50853.306635] scsi 9:0:0:0: Direct-Access     SanDisk  Sansa Clip 2GB   v01. PQ: 0 ANSI: 0
[50853.318838] sd 9:0:0:0: [sdd] 3992576 512-byte hardware sectors (2044 MB)
[50853.319483] sd 9:0:0:0: [sdd] Write Protect is off
[50853.319488] sd 9:0:0:0: [sdd] Mode Sense: 04 00 00 00
[50853.319491] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[50853.322079] sd 9:0:0:0: [sdd] 3992576 512-byte hardware sectors (2044 MB)
[50853.322955] sd 9:0:0:0: [sdd] Write Protect is off
[50853.322960] sd 9:0:0:0: [sdd] Mode Sense: 04 00 00 00
[50853.322963] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[50853.322968]  sdd:
[50853.325734] sd 9:0:0:0: [sdd] Attached SCSI removable disk
[50853.325785] sd 9:0:0:0: Attached scsi generic sg5 type 0
[50855.405324] scsi 9:0:0:0: rejecting I/O to dead device
[50855.479573] usb 5-8: reset high speed USB device using ehci_hcd and address 20
[50866.436455] usb 5-8: USB disconnect, address 20
[50867.270310] usb 5-8: new high speed USB device using ehci_hcd and address 21
[50869.479073] ehci_hcd 0000:00:1d.7: port 8 reset error -110
[50869.479083] hub 5-0:1.0: hub_port_status failed (err = -32)
[50895.441945] usb 5-8: new high speed USB device using ehci_hcd and address 22
[50895.770753] ehci_hcd 0000:00:1d.7: port 8 reset error -110
[50895.770762] hub 5-0:1.0: hub_port_status failed (err = -32)
[50939.774972] usb 5-8: new high speed USB device using ehci_hcd and address 23
[50940.083820] ehci_hcd 0000:00:1d.7: port 8 reset error -110
[50940.083828] hub 5-0:1.0: hub_port_status failed (err = -32)
[51048.797422] usb 5-7: new high speed USB device using ehci_hcd and address 24
[51048.986525] ehci_hcd 0000:00:1d.7: port 7 reset error -110
[51048.986533] hub 5-0:1.0: hub_port_status failed (err = -32)

---

### Post by jtclicker on 2008-05-12
anyone any ideas on this?

---

### Post by foulbeast on 2008-05-16
I am seeing the exact same problem with my Sansa Clip.

From /var/log/kern.log:
[INDENT]May 16 21:30:27 laptop-ubuntu kernel: [  323.478185] usb 5-1: new high speed USB device using ehci_hcd and address 5
May 16 21:30:27 laptop-ubuntu kernel: [  323.839968] ehci_hcd 0000:00:1d.7: port 1 reset error -110
May 16 21:30:27 laptop-ubuntu kernel: [  323.839994] hub 5-0:1.0: hub_port_status failed (err = -32)[/INDENT]

From dmesg:
[INDENT][  323.478185] usb 5-1: new high speed USB device using ehci_hcd and address 5
[  323.839968] ehci_hcd 0000:00:1d.7: port 1 reset error -110
[  323.839994] hub 5-0:1.0: hub_port_status failed (err = -32)
[/INDENT]

If I "modprobe -r ehci_hcd" and reconnect, the mp3 player is mounted in /media/SANSA CLIP.  I can see the directories, but none of the files.  The mp3 player was originally formatted on Windows and the mp3 files were also transferred from Windows.

This bug is holding me back from dumping Windows all together -- any ideas???

Thanks.

---

### Post by lswest on 2008-05-16
now i have to admit i haven't read the whole thread, but have you tried changing the USB mode (on your MP3 player) so that it's on Auto?  i'm not 100% sure (doing it from memory) but if it's on MTP i believe it won't be recognized.  Worked for my sandisk esansa

---

### Post by foulbeast on 2008-05-16
> **lswest said:**
> now i have to admit i haven't read the whole thread, but have you tried changing the USB mode (on your MP3 player) so that it's on Auto?  i'm not 100% sure (doing it from memory) but if it's on MTP i believe it won't be recognized.  Worked for my sandisk esansa


I've tried all 3 settings, Auto Detect, MTP, and MSC with no luck.  Same error regardless of the settings.

Also, I tried the trick of rebooting with the player plugged and got the same result.

Thanks for the suggestion.

---

### Post by jtclicker on 2008-05-17
Just downloaded all the latest system updates and this is now fixed for me...

---

### Post by jtclicker on 2008-05-17
> **jtclicker said:**
> Just downloaded all the latest system updates and this is now fixed for me...
 actually not true. Downloaded the updates and it worked. Rebooted as the updates requested and the mp3 DOESN'T now work. What the hell is that about???

---

### Post by ravalox on 2008-05-18
I have a rockboxed sansa e280 and when I plug it in it mounts but I cannot "see" any of the files in the gui.  When I got into the directory in the CLI I can see the files; however they dissappear periodically!  It doesn't unmount, they just vanish!  It's very, very odd and clearly not a misunderstood feature; it's a bug.  I'm entering it on launchpad.

---

### Post by jtclicker on 2008-05-18
I still have to go into windows just to charge the player up! Hardy has been a bummer for me, I'm spending much more time in windows than I want to. No cinepaint, so I need windows for a 16bit image editing app, nvidia driver won't work and the bug report is still open, and now a coupla hours a day just to charge the mp3 and move the files around... next time someone remind me NOT to upgrade for a coupla months

---

### Post by meborc on 2008-05-18
with usb externals i also have encountered some problems... usually unstick-stick-unstick-stick helps :)

---

### Post by jtclicker on 2008-05-19
> **meborc said:**
> with usb externals i also have encountered some problems... usually unstick-stick-unstick-stick helps :)

yeah I try that too! sometimes I can get it to charge the device for a few seconds but it won't mount. Dunno why it worked in gutsy and not hardy, and why doing the system updates caused it to work and the fail after rebooting...

---

### Post by dark_harmonics on 2008-05-19
A random guess:

Sometimes the updates will run a sudo depmod -a command. That might be why its working. It almost seems like once the correct module is loaded into your kernel it works.Try this:

Take a copy of your current modules with : lsmod>notworking.txt
If it starts to work again run this: lsmod>working.txt
Then run: diff notworking.txt working.txt and post the results.

---

### Post by jtclicker on 2008-05-19
> **dark_harmonics said:**
> A random guess:

Sometimes the updates will run a sudo depmod -a command. That might be why its working. It almost seems like once the correct module is loaded into your kernel it works.Try this:

Take a copy of your current modules with : lsmod>notworking.txt
If it starts to work again run this: lsmod>working.txt
Then run: diff notworking.txt working.txt and post the results.

Can you explain that a bit more please?? I type lsmod>notworking.txt into terminal and got an error - I'm very much fumbling around still in linux

---

### Post by dark_harmonics on 2008-05-19
I apologize. it does work for me. Are you in a folder you have permissions to like your home folder? you could put sudo on it too but it shouldnt be needed for this. Remember im just doing this to troubleshoot a little:
```

cd ~
lsmod>notworking.txt

```

did that command ```
 sudo depmod -a
``` not do anything?

I dont know much about your specific problem, but that is how i would go about trying to figure it out on my own.

The reason i did this is that it sounds like your computer is loading the module for your device once (maybe when you update) but it doesnt load it on reboot. If we can figure out which module to load (plugs the hardware into the kernel) then maybe we can just put that in your /etc/modules and then every time you boot it will load it. 

lsmod prints the currently loaded modules. Comparing the difference between which ones are loaded when it doesnt work to when it does work should expose the module that we need... Hopefully. Well its my best idea anyhow.

---

### Post by jtclicker on 2008-05-20
no, sudo depmod -a didn't do anything.

I'll try your idea next time I can get it to work an compare the two lists. Thanks!

---

### Post by G@B0 on 2008-05-20
Well if you have a Sansa Clip then you have to do this.

I have the same problem but after accidentally pressing the center button I discover something.

The USB mode is set on automatically and you just have to press the center button after connecting the device to the computer and it will suddenly appear as a removable drive.

I hope this works for you.

---

### Post by dark_harmonics on 2008-05-21
> **G@B0 said:**
> Well if you have a Sansa Clip then you have to do this.

I have the same problem but after accidentally pressing the center button I discover something.

The USB mode is set on automatically and you just have to press the center button after connecting the device to the computer and it will suddenly appear as a removable drive.

I hope this works for you.

Yes this also sounds like a definite possibility. It just seems like this is a hardware recognition issue and what you said fits that exactly. Its not seeing it all the time because he doesnt hit that button. All my mp3 players just work by default.

---

### Post by jtclicker on 2008-05-21
> **G@B0 said:**
> Well if you have a Sansa Clip then you have to do this.

I have the same problem but after accidentally pressing the center button I discover something.

The USB mode is set on automatically and you just have to press the center button after connecting the device to the computer and it will suddenly appear as a removable drive.

I hope this works for you.

Thanks but no luck for me. I've been using my wife's no name mp3 and it works fine! But my sandisk, no way

---

### Post by G@B0 on 2008-05-21
Ok here is the correct procedure.
First, turn on the mp3 player(sansa clip),
go to Settings > USB Mode > and change Auto Detect to MSC

Now connect the device to the computer.
It will not show as a removable drive unless you run this command:
```
lsusb
```

After running that command on the terminal, wait 5 seconds and it will be shown in the desktop as a removable drive.

Hope this works for you

---

### Post by jtclicker on 2008-05-21
> **G@B0 said:**
> Ok here is the correct procedure.
First, turn on the mp3 player(sansa clip),
go to Settings > USB Mode > and change Auto Detect to MSC

Now connect the device to the computer.
It will not show as a removable drive unless you run this command:
```
lsusb
```

After running that command on the terminal, wait 5 seconds and it will be shown in the desktop as a removable drive.

Hope this works for you

****, you are a GENIUS!!!! works for me... off for a brandy to calm down

---

### Post by jtclicker on 2008-05-21
actually worked once. I unmounted it, disconnected the device then repeated everything and it didn't work, But now I have something to work with

---

### Post by jtclicker on 2008-05-22
Here is what I have to do to make sure this works every time.

Turn the device on, change the usb settings from what they were to anything else. 
Turn the machine off.
Turn on again and move to MSC.
Plug the device in and type lsusb in terminal.
The device will now be mountable.

You will not be able to see any music you have put on from windows, so you need to format the device and only put files on from ubuntu.

Note: none of this was necessary with Gutsy...

---

