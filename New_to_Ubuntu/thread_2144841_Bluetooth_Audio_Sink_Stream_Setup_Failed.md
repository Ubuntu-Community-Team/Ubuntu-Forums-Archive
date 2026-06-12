---
title: "Bluetooth Audio Sink: Stream Setup Failed"
date: 2013-05-13
forum: New to Ubuntu
---

### Post by linuxJozi on 2013-05-13
Hi Ive been struggling with this problem for a while, any help would be great

Info:

Running Xubuntu 13.04
Bluetooth: blueZ and blueman installed
Bluetooth Audio reciever: Belkin X43
PulseAudio installed

I have been trying to connect and stream music to my Belkin bluetooth reciever with no success. I have tried the following:

1.
- Using blueman I go to Devices... find the device and ADD it
- It appears to connect succesfully
- I right click on the device and click on "Connect To: Audio Sink"
- Notification pops up to enter PIN (now in the past I have never been asked for a pin whether im connecting from Linux Mint, Windows or Android)
- So I enter 0000
- Result: Connection Failed: Stream Setup Failed

2. 
- Use bluetooth assistant (click on blueman > Setup New Device)
- Find device connect to it without pairing option
- Connect dialogue shown: select Connect to A2DP sink, click forward
- Prompted for pin, enter pin
-Result: Device added succesfully but failed to connect.

3.
-Same as 2 above but use custom pin 0000 for pairing option
-Result: Device added succesfully but failed to connect.

4. 
-same a 3 above but for custom key use an incorrect key 3344
-Result: Failed to connect device (assume key is correct then)

Other attempts:

I have tried to update blueZ, result: latest version
Tried to update blueman, result: latest version
I have connected to the device from other OS's so its not the device
I had no problems with this in Linux Mint

Note:
Device doesnt require a pin, but in blueman your forced to enter one

--
Any feedback would be great, I look forward to hearing from you.

---

### Post by linuxJozi on 2013-05-14
Update: I have also enabled Advanced Audio Reciever in the local service setting, but does not help unfortunatley.

--

---

### Post by freeman00 on 2013-05-15
same problem here, can't connect to my bluetooth headset, in xubuntu 13.04, was working fine with same bluez in 12.10. i hope someone find a fix soon, i forgot to mention that my xubuntu is up to date.

---

### Post by linuxJozi on 2013-05-16
I have now experienced the exact same issue in Xubuntu, Lubuntu and Manjaro.

They all use blueman....

---

### Post by Merrattic on 2013-05-16
Does this help?

[http://metricrat.co.uk/xubuntu-bluetooth-blueman-automatic-device-connection-audioheadset/](http://metricrat.co.uk/xubuntu-bluetooth-blueman-automatic-device-connection-audioheadset/)

---

### Post by linuxJozi on 2013-05-17
Thanks for the reply.

I have just tried enabling auto-connect in the bluetooth audio.conf file but unfortunately I get the same results.

I also tried installing gnome-bluetooth but with that installed I couldnt even pair with the device... :confused:

---

### Post by Cuppa-Chino on 2013-06-30
Anybody have any luck ?

---

### Post by Phandaman on 2013-07-04
I was struggling with the same issue and decided to switch to Linux Mint 13 Maya Xcfe, an LTS version based on Ubuntu which reportedly provides better hardware support. Problem solved!

---

### Post by linuxJozi on 2013-07-11
> **Phandaman said:**
> I was struggling with the same issue and decided to switch to Linux Mint 13 Maya Xcfe, an LTS version based on Ubuntu which reportedly provides better hardware support. Problem solved!

Yup still not working ---> busy downloading Mint 13 Xfce will give that a try

---

### Post by monkeybrain2012 on 2013-07-12
I have the same problem with Ubuntu 13.04. I am not able to connect to my bluetooth speaker with Blueman with same error "Stream setup failed". However I am able to connect very reliably with the default gnome bluetooth applet on the panel! The issue with bluetooth applet is that it cannot find my device reliable.--or may just take a very long time to scan. To workaround it, before click "setting up new device", first run in the terminal "hcitool scan", which will find my device, and then run "setting up new device" in the bluetooth applet, then it will discover the device, once the device shows up then follow the steps and it connects successfully. After the device is paired, just need to switch on the connection to use the device (you may need to switch the output in sound settings to the bluetooth device manually if it doesn't do so automatically)

I have repeated this many times and it always works, but Blueman always fails, so it seems to be a bug in Blueman.

---

### Post by monkeybrain2012 on 2013-07-12
Here is a bug report against Blueman, Login to Launchpad and add an "affect me too"

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1179801](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1179801)

---

### Post by linuxJozi on 2013-07-17
Thanks I will have a look that bluetooth applet.

It definatley seems to be a Blueman issue.

I have now tried Linux Mint xfce 13 and the bluetooth issues remain. Linux Mint 15 Cinnamon fixes the bluetooth issue but its just too sluggish on my laptop, I just prefer lightweight stuff, no bloat.

Im going to switch back to Lubuntu and try your solution. Lubuntu seems to be the slickest lightweight distro Ive tried so far.

---

### Post by Dayvson_Reis on 2013-08-15
I have same problem, but when i unistall blueman the a2dp works, but only fist paring (I can send music to device), but if I disconnect and connect again i get this in dmesg: "Bluetooth: re-auth of legacy device is not possible." is the same "error" in dmesg to blueman (error in screan: Stream Setup Failed) and I cant play nothing (even fist time with blueman), this way I have that remove the device and to discover again to works.

peforming a hcitool cc 00:AA:44:C5:CD:AA
i get in hcidump:
> HCI Event: Command Status (0x0f) plen 4
    Create Connection (0x01|0x0005) status 0x00 ncmd 1
> HCI Event: Command Complete (0x0e) plen 10
    Link Key Request Reply (0x01|0x000b) ncmd 1
    status 0x00 bdaddr 00:AA:44:C5:CD:AA
> HCI Event: Connect Complete (0x03) plen 11
    status 0x00 handle 12 bdaddr 00:AA:44:C5:CD:AA type ACL encrypt 0x01
> HCI Event: Command Status (0x0f) plen 4
    Read Remote Supported Features (0x01|0x001b) status 0x00 ncmd 1
> HCI Event: Read Remote Supported Features (0x0b) plen 11
    status 0x00 handle 12
    Features: 0xff 0xff 0x8f 0xf8 0x18 0x18 0x00 0x80
> HCI Event: Command Status (0x0f) plen 4
    Remote Name Request (0x01|0x0019) status 0x00 ncmd 1
> HCI Event: Remote Name Req Complete (0x07) plen 255
    status 0x00 bdaddr 00:AA:44:C5:CD:AA name 'Motorola DC800'
> HCI Event: Command Status (0x0f) plen 4
    Disconnect (0x01|0x0006) status 0x00 ncmd 1
> HCI Event: Disconn Complete (0x05) plen 4
    status 0x00 handle 12 reason 0x16
    Reason: Connection Terminated by Local Host

---

### Post by amgmagician on 2013-12-03
I had this problem. I fixed it by adding the below line to [General] section of */etc/bluetooth/audio.conf*:

```
Enable=Socket
```

Worked for me! I found this solution from [here]("https://bbs.archlinux.org/viewtopic.php?id=133460#p1046304").

---

### Post by ct2034 on 2014-03-10
Hi guys,

I know this is a bit of an old post. But as I recently had the same problem I came across a rather simple solution: just install pulseaudio-module-bluetooth
```
sudo apt-get install pulseaudio-module-bluetooth
```
found it here: [http://ubuntuforums.org/showthread.php?t=1909957](http://ubuntuforums.org/showthread.php?t=1909957)

good luck with that :D

---

### Post by Arthur_Fincham on 2014-06-04
[http://forum.kde.org/viewtopic.php?f=9&t=95838](http://forum.kde.org/viewtopic.php?f=9&t=95838) worked for me.

---

### Post by jan-koid on 2014-06-23
this shellcommand worked for me: pactl load-module module-bluetooth-discover
(found it here: [http://forum.kde.org/viewtopic.php?f=9&t=95838](http://forum.kde.org/viewtopic.php?f=9&t=95838))

gonna try to implement it to the autostart...

---

### Post by abel6 on 2014-08-18
Thanks, jan-koid!
That's worked for me too. Did you be able to implement an auto-start?
Thanks!

---

### Post by maggaknet on 2014-08-28
searched for a solution for this problem since months. after installing tons of crap really. the simple

pactl load-module module-bluetooth-discover

did the trick. just nice. i am the biggest linux fan on earth, but honestly things like that draws people away from it. i would never recommend it to anyone. kind of sad.
Thanks jan-koid !!

---

### Post by garvint on 2014-12-14
> **abel6 said:**
> Thanks, jan-koid!
That's worked for me too. Did you be able to implement an auto-start?
Thanks!

i need a way to add this to autostart, i really tried loading:

pactl load-module module-bluetooth-discover

then

pactl list | grep -i module-bluetooth-discover

but only works when just typed into terminal

---

### Post by Evil Wayz on 2014-12-17
I'm not familiar with xubuntu but do you have just the regular bluetooth assistant?  I found that blueman doesn't work, but as soon as I remove/purge it, everything works just fine.  I have to re-add the device every time, but it's better than no bluetooth audio at all.

---

### Post by Tommy_Chang on 2015-02-15
> **garvint said:**
> i need a way to add this to autostart, i really tried loading:

pactl load-module module-bluetooth-discover

then

pactl list | grep -i module-bluetooth-discover

but only works when just typed into terminal

You can try inserting the command into the autostart file below:

   /usr/bin/start-pulseaudio-x11
Or 
   /usr/bin/start-pulseaudio-kde

By the way,  I had to insert an extra "sleep 1" statement before the command, like below:
    sleep 1
    /usr/bin/pactl load-module module-bluetooth-discover || true

---

### Post by engineerarun on 2015-07-05
Here's a probable solution to this: [http://tuxdiary.com/2015/07/05/fix-stream-setup-failed-error-with-blueman/](http://tuxdiary.com/2015/07/05/fix-stream-setup-failed-error-with-blueman/)

---

### Post by squashpup2 on 2015-08-21
> **engineerarun said:**
> Here's a probable solution to this: [http://tuxdiary.com/2015/07/05/fix-stream-setup-failed-error-with-blueman/](http://tuxdiary.com/2015/07/05/fix-stream-setup-failed-error-with-blueman/)

I installed the new PPA and after updating Blueman, I can confirm that it solves the problem for me.

---

### Post by nordik_14 on 2015-08-26
Try this
[https://linuxparaorcos.wordpress.com/2014/12/24/conectar-altavoces-bluetooth-a-kubuntu/](https://linuxparaorcos.wordpress.com/2014/12/24/conectar-altavoces-bluetooth-a-kubuntu/)

---

### Post by beregon87 on 2015-11-30
> **engineerarun said:**
> Here's a probable solution to this: [http://tuxdiary.com/2015/07/05/fix-stream-setup-failed-error-with-blueman/](http://tuxdiary.com/2015/07/05/fix-stream-setup-failed-error-with-blueman/)

This worked for me too! With Sennheiser MM450-X headphones on Xubuntu 14.04.3 LTS.  Thanks!

---

