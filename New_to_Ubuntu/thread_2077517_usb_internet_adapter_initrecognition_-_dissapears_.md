---
title: "usb internet adapter init/recognition - dissapears after shutdown/reboot"
date: 2012-10-28
forum: New to Ubuntu
---

### Post by halex56 on 2012-10-28
Hello!

I am new to Ubuntu, just installed it.

I like it so far, the more I look at it it looks and feels better and I hope to stick to it, feel really enthusiastic.

I would like to get help with this as frankly I think the problem is over my head at the moment.

I have the broadband internet usb adapter by Wind in Italy. It worked just fine, I was surprised. Plug and play on first boot. But, after I shut down my laptop and booted again it was nowhere to be found. The thing just blinks red, which is I think bad. I don't have the option to connect in the system menu in the top right corner, and that's where it was. The network profile is still available for editing in the settings/network configuration window under broadband connections but doesn't show up in the system menu. I am thinking that the device is missing, which would be indicated by the red blinking.

Then, I boot Windows and the red blinking turns to blue and I can connect. After I boot back to Ubuntu, voila it works. So for now I boot into Win, the driver gets initialized, and I boot back to Ubuntu and it works.

I am running 12.10 and installed it through Windows. I didn't really want a dual boot, but my F2 key is not working so I can't enter bios to change boot priority :D

Hope I'll get some help. This seems like an interesting problem. I will try to google how to device manage, maybe figure out how to mount the device, but I am not sure if this is the problem or the device itself needs some special wake up command after power up that the Windows driver gives it. Or, when shutting down, Ubuntu deinitializes it in some way. Maybe if I could get some directions on how to explore this issue.

Thank you!

Best regards,
Alex

---

### Post by newb85 on 2012-10-28
Welcome to Ubuntu!  Glad to hear you're liking it so far.

First, you should know that if you used the Windows installer (Wubi), you don't really have a dual-boot system.  What you really have is Ubuntu booting inside Windows, even though it may not look like it.  Wubi essentially creates a VM that preempts the Windows enviroment, but it's still running on Windows.

Second, many machines allow you to make a one-time boot device selection without changing the BIOS.  For example, on my Satellite, I can hit F12 at the Toshiba splash screen and it brings up a list of devices I can boot from.  (F2 is the key I would hit to enter the BIOS Setup.)  You might want to make sure you don't have a similar option before giving up on installing from CD or USB.

Third, I will finally get to the actual subject of the thread.  I'm afraid I have zero experience with USB modems, but my first thought would be to see if Ubuntu is recognizing the device.  Create the scenario where the modem blinks red and doesn't work and then run the command
```
lsusb
```
from the terminal.  Post the output to this thread.  Please put the input inside code tags, like this:

[noparse]```
Output
Here
```[/noparse]

---

### Post by squakie on 2012-10-28
Are we talking about a modem or a USB wireless adapter?

It's quite possible that the first time some kernel module (like a driver, in this case) was loaded that after that is not being loaded.  So, along with the output that newb85 could you please also include the output of:

lsmod

---

### Post by halex56 on 2012-10-29
Thank you for the help.
It is a usb modem, it dials up. Sorry about that.

I will post the outputs here tonight when I am home.

So I am running a vm. Congratulations on a masterful job of not making it look so to the Ubuntu developers :cool:
Thanks for the boot advice, will try it.

---

### Post by newb85 on 2012-10-29
> **halex56 said:**
> So I am running a vm. Congratulations on a masterful job of not making it look so to the Ubuntu developers :cool:

Yeah, let me apologize on behalf of Canonical for that, as they're not likely to apologize themselves.  They've recently been on a kick of trying too hard not to overwhelm new users with technical information, and it sometimes results in people not having enough technical information.  This is one example of where they took it too far.  I wish I knew a good way to petition them to add that point to their website, but alas, I don't, and I don't think my petitions would necessarily be heeded, anyways.  (I could go on, but I'll get off my soapbox, now, as this isn't a discussion thread.)

---

### Post by halex56 on 2012-10-29
They did do a very good job implementing this. I would like to see how it works. Will be looking for some article/blogpost/paper on this. It is very impressive. I see your point though. They should have said it. I was actually looking forward to some hacking to remove Windows with Ubuntu after install. Obviously will not be doing this :-) I wonder what the benefits of running on a vm are. Mazbe Win exposes some devices xD But then this would have to feed into the krenel, agh. Stop, Alex.

So, this is from when it does not work:

```
alex@lilith:~$ sudo lsusb
sudo: unable to resolve host lilith
[sudo] password for alex: 
Bus 002 Device 002: ID 1ee8:0054 ONDA COMMUNICATION S.p.a. 
Bus 002 Device 003: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314]
Bus 003 Device 002: ID 0a5c:2151 Broadcom Corp. Bluetooth
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
alex@lilith:~$ sudo lsmod
sudo: unable to resolve host lilith
Module                  Size  Used by
snd_hda_codec_hdmi     32007  1 
btusb                  18334  0 
joydev                 17457  0 
coretemp               13400  0 
rfcomm                 46619  12 
parport_pc             32688  0 
bnep                   18140  2 
ppdev                  17073  0 
acer_wmi               32453  0 
bluetooth             209199  22 btusb,rfcomm,bnep
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
sparse_keymap          13890  1 acer_wmi
arc4                   12529  2 
microcode              22803  0 
psmouse                95552  0 
serio_raw              13215  0 
snd_hda_codec_realtek    77876  1 
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
video                  19335  1 acer_wmi
snd_hda_intel          33491  5 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
wmi                    19070  1 acer_wmi
snd_timer              29425  2 snd_pcm,snd_seq
mac_hid                13205  0 
ath9k                 131308  0 
lpc_ich                17061  0 
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              539908  1 ath9k
radeon                895653  3 
ath9k_common           14055  1 ath9k
ath9k_hw              395218  2 ath9k,ath9k_common
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
cfg80211              206566  3 ath9k,mac80211,ath
ttm                    83595  1 radeon
snd                    78734  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         46784  1 radeon
drm                   275528  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13413  1 radeon
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
tg3                   148780  0 
usb_storage            48838  0 
```This is when it does:

```
alex@lilith:~$ sudo lsusb
sudo: unable to resolve host lilith
[sudo] password for alex: 
Bus 002 Device 002: ID 1ee8:0053 ONDA COMMUNICATION S.p.a. 
Bus 002 Device 003: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314]
Bus 003 Device 002: ID 0a5c:2151 Broadcom Corp. Bluetooth
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
alex@lilith:~$ sudo lsmod
sudo: unable to resolve host lilith
Module                  Size  Used by
ppp_deflate            12950  0 
zlib_deflate           26914  1 ppp_deflate
bsd_comp               12921  0 
ppp_async              17413  1 
crc_ccitt              12667  1 ppp_async
snd_hda_codec_hdmi     32007  1 
btusb                  18334  0 
coretemp               13400  0 
joydev                 17457  0 
acer_wmi               32453  0 
sparse_keymap          13890  1 acer_wmi
rfcomm                 46619  12 
parport_pc             32688  0 
bnep                   18140  2 
bluetooth             209199  22 btusb,rfcomm,bnep
ppdev                  17073  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
microcode              22803  0 
snd_hda_codec_realtek    77876  1 
psmouse                95552  0 
serio_raw              13215  0 
snd_hda_intel          33491  7 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
arc4                   12529  2 
video                  19335  1 acer_wmi
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k                 131308  0 
wmi                    19070  1 acer_wmi
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
radeon                895653  3 
mac80211              539908  1 ath9k
videobuf2_memops       13368  1 videobuf2_vmalloc
cdc_ether              13494  0 
usbnet                 26159  1 cdc_ether
ath9k_common           14055  1 ath9k
ath9k_hw              395218  2 ath9k,ath9k_common
mac_hid                13205  0 
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
cdc_acm                26935  5 
snd                    78734  23 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    83595  1 radeon
drm_kms_helper         46784  1 radeon
lpc_ich                17061  0 
drm                   275528  5 radeon,ttm,drm_kms_helper
cfg80211              206566  3 ath9k,mac80211,ath
i2c_algo_bit           13413  1 radeon
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
tg3                   148780  0 
usb_storage            48838  0 
```Some stuff is missing in lsmod, I think.

If I pull the stick out and then put it back in it does not reinitialize. So if it was working it stops, and if it wasn't it still doesn't. xD

When it is working, if I pull it out, all the modules stay loaded, but when I put it back in the connection is not present in the network menu in the top right, exactly the same as when I do a fresh power-up.

So, problem is: fresh power-up into ubuntu -> no broadband modem connection available; boot windows and after that ubuntu: connection available.  Running Wubi installed 12.10.

---

### Post by newb85 on 2012-10-29
```
Bus 002 Device 002: ID 1ee8:0053 ONDA COMMUNICATION S.p.a. 
```

That's the device.

I did a little googling around, it looks like the issue is the way usb_modeswitch is handling the device.  More specifically, it's treating it like a storage device instead of a modem.

There are some instructions at [http://wiki.freegeek.org/index.php/3G_Mobile_Broadband_Internet]("http://wiki.freegeek.org/index.php/3G_Mobile_Broadband_Internet") under the heading "T-Mobile webConnect Rocket 2.0".  

I don't know if that's your specific model.  I can't say for sure that those directions apply to you.  And I don't know that those directions aren't outdated.  I would be a lot more comfortable if someone who knew more on the subject could chime in.

---

### Post by bra|10n on 2012-10-29
You could look at my post on setting up a similar device. 
I take no credit for the info contained as I found the 'fix' online in bits n pieces...

[http://ubuntuforums.org/showthread.php?p=12312407#post12312407](http://ubuntuforums.org/showthread.php?p=12312407#post12312407)

I'll draw your attention to the fact that my device does not require a 'switching fix' as it is always in modem mode...
In the file **19d2:0257 **I created, (yours will contain different vendor and product id's of course)**, **you'll notice the 'default' and 'target' id's are the same.
[B]Your file however will contain the default id (when not working) and the target id (when it is).
[/B] 
The rest should be the same process IMO. Edit the remainder of the file accordingly, brand, carrier etc.
**Note: the Message Content value also will be different!**
You can find yours in /usr/share/usb_modeswitch/configPack.tar.gz. Extract the contents to your /home/new folder and search for the closest driver in the list.
You will be searching for files named 1ee8:*. To try and pick the 'best' file contents that suit your device, look at the various device codes in the files and try to match up what's on the device (under the cover?) perhaps...
HTH

---

