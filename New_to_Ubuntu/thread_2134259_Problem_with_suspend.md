---
title: "Problem with suspend"
date: 2013-04-10
forum: New to Ubuntu
---

### Post by thatstheway on 2013-04-10
I can recover from Suspend just fine, as long as I issue the Suspend command from the menu. But if I close the lid, it "wakes" to the black screen mentioned by many others here, and I have to reboot. 

Does anyone else have this same problem? Any ideas? 

I've got a Toshiba Portege R100 laptop with a Trident CyberBlade XP4m32 graphics card. I'm using the most up-to-date version of the xorg Trident driver. 

[COLOR=#000000][FONT=Arial]/var/log/pm-suspend.log says the same thing, whether I use the menu (successful resume) or the lid (failed resume, needing to reboot): 

[/FONT][/COLOR]```
[COLOR=#000000][FONT=Arial]Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial][/FONT][/COLOR][COLOR=#000000][FONT=Arial]/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][/FONT][/COLOR][COLOR=#000000][FONT=Arial]/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][/FONT][/COLOR][COLOR=#000000][FONT=Arial]/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Wed Apr 10 09:25:30 PDT 2013: Finished.[/FONT][/COLOR]

```

[COLOR=#000000][FONT=Arial]cat /proc/cmdline[/FONT][/COLOR]: 

```
BOOT_IMAGE=/boot/vmlinuz-3.5.0-23-generic root=UUID=1ca79722-7698-4d8f-8fb1-dafeec4306ca ro quiet splash vt.handoff=7
```

[COLOR=#000000][FONT=Arial]lsmod[/FONT][/COLOR]:

```
Module                  Size  Used by
michael_mic            12541  8 
arc4                   12474  4 
lib80211_crypt_tkip    17276  2 
lib80211_crypt_ccmp    12790  1 
vesafb                 13518  1 
bnep                   17791  2 
bluetooth             189585  7 bnep
parport_pc             32115  0 
ppdev                  12850  0 
snd_intel8x0           33463  2 
snd_ac97_codec        106118  1 snd_intel8x0
ac97_bus               12671  1 snd_ac97_codec
snd_pcm                81124  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13133  0 
snd_rawmidi            25426  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
ipw2200               146213  0 
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
libipw                 46733  1 ipw2200
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39855  0 
joydev                 17394  0 
cfg80211              181041  2 ipw2200,libipw
snd                    62675  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27465  0 
soundcore              14636  1 snd
pcmcia_rsrc            18368  1 yenta_socket
lib80211               14041  4 lib80211_crypt_tkip,lib80211_crypt_ccmp,ipw2200,libipw
snd_page_alloc         14109  2 snd_intel8x0,snd_pcm
pcmcia_core            21512  3 pcmcia,yenta_socket,pcmcia_rsrc
lpc_ich                16993  0 
psmouse                91022  0 
microcode              18396  0 
shpchp                 32326  0 
serio_raw              13032  0 
video                  19070  0 
mac_hid                13078  0 
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
hid_generic            12485  0 
usbhid                 46054  0 
hid                    82511  2 hid_generic,usbhid
e100                   36324  0 


```

[COLOR=#000000][FONT=Arial]sudo lspci -vnn | grep -A10 VGA[/FONT][/COLOR]:

```
01:00.0 VGA compatible controller [0300]: Trident Microsystems CyberBlade XP4m32 [1023:2100] (rev 91) (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device [1179:0002]
    Flags: bus master, 66MHz, medium devsel, latency 8, IRQ 11
    Memory at f0000000 (32-bit, non-prefetchable) [size=128M]
    Memory at efc00000 (32-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (32-bit, non-prefetchable) [size=128M]
    Memory at dfff8000 (32-bit, non-prefetchable) [size=32K]
    [virtual] Expansion ROM at 54000000 [disabled] [size=256K]
    Capabilities: [80] AGP version 2.0
    Capabilities: [90] Power Management version 2
```

Millions of thanks for any insight into this!













[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by thatstheway on 2013-04-10
I'm having a problem with Suspend, which works fine if I issue the command using the gear menu or the terminal, but when I close the lid (I'm on a laptop) to Suspend, when I touch the power button to resume, it goes to a black screen and I have to reboot. 

 So I'm trying out s2ram, part of uswusp, and I tried to  make it the default action on "Suspend," with these steps (per [http://askubuntu.com/questions/75357/replacing-default-hibernate-method-to-s2disk](http://askubuntu.com/questions/75357/replacing-default-hibernate-method-to-s2disk)):

 Created a file /etc/pm/config.d/module
 containing:
 ```
SLEEP_MODULE=uswsusp


``` 
But how do I verify that s2ram is being used when I  close the lid? Are there any logs that can tell me this info?

 
Also, why would I get different results from issuing the Suspend  command from the menu or the terminal vs closing the laptop lid?

Thanks!

---

### Post by Toz on 2013-04-10
Post back the complete contents of your /var/log/pm-suspend.log file - it should say in there. 

In a terminal window:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

Is this the same issue as you posted [here]("http://ubuntuforums.org/showthread.php?t=1981650&p=12597244&viewfull=1#post12597244")? If so, I'll move that post here so that everything is in one place.

---

### Post by thatstheway on 2013-04-10
Hi, yes, it's the same issue. I was asking slightly different things, but yes, it makes sense to consolidate them, thanks much. Resulting link from pastebinit /var/log/pm-suspend.log:

[http://paste.ubuntu.com/5697086/](http://paste.ubuntu.com/5697086/)

Appreciate your help on this!

---

### Post by thatstheway on 2013-04-10
Much better data! Looking through this but much is over my head. At least I'm getting actual errors: 

Having NetworkManager wake interfaces back up...Failed

---

### Post by Toz on 2013-04-10
> **thatstheway said:**
> 
```
Module                  Size  Used by
michael_mic            12541  8 
arc4                   12474  4 
lib80211_crypt_tkip    17276  2 
lib80211_crypt_ccmp    12790  1 
vesafb                 13518  1 
bnep                   17791  2 
bluetooth             189585  7 bnep
parport_pc             32115  0 
ppdev                  12850  0 
snd_intel8x0           33463  2 
snd_ac97_codec        106118  1 snd_intel8x0
ac97_bus               12671  1 snd_ac97_codec
snd_pcm                81124  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13133  0 
snd_rawmidi            25426  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
ipw2200               146213  0 
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
libipw                 46733  1 ipw2200
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39855  0 
joydev                 17394  0 
cfg80211              181041  2 ipw2200,libipw
snd                    62675  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27465  0 
soundcore              14636  1 snd
pcmcia_rsrc            18368  1 yenta_socket
lib80211               14041  4 lib80211_crypt_tkip,lib80211_crypt_ccmp,ipw2200,libipw
snd_page_alloc         14109  2 snd_intel8x0,snd_pcm
pcmcia_core            21512  3 pcmcia,yenta_socket,pcmcia_rsrc
lpc_ich                16993  0 
psmouse                91022  0 
microcode              18396  0 
shpchp                 32326  0 
serio_raw              13032  0 
video                  19070  0 
mac_hid                13078  0 
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
hid_generic            12485  0 
usbhid                 46054  0 
hid                    82511  2 hid_generic,usbhid
e100                   36324  0 


```
I'm not seeing the trident driver loaded. Are you sure its being used? Can you post back your /var/log/Xorg.0.log file:
```
pastebinit /var/log/Xorg.0.log
```

> [COLOR=#000000][FONT=Arial]sudo lspci -vnn | grep -A10 VGA[/FONT][/COLOR]:

```
01:00.0 VGA compatible controller [0300]: Trident Microsystems CyberBlade XP4m32 [1023:2100] (rev 91) (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device [1179:0002]
    Flags: bus master, 66MHz, medium devsel, latency 8, IRQ 11
    Memory at f0000000 (32-bit, non-prefetchable) [size=128M]
    Memory at efc00000 (32-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (32-bit, non-prefetchable) [size=128M]
    Memory at dfff8000 (32-bit, non-prefetchable) [size=32K]
    [virtual] Expansion ROM at 54000000 [disabled] [size=256K]
    Capabilities: [80] AGP version 2.0
    Capabilities: [90] Power Management version 2
```
Some info was cut off. Try instead:
```
sudo lspci -vnn |grep -A15 VGA
```

---

### Post by thatstheway on 2013-04-10
This is suspicious:
```

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend: Function not supported
```

---

### Post by thatstheway on 2013-04-10
from sudo lspci -vnn |grep -A15 VGA:
```

01:00.0 VGA compatible controller [0300]: Trident Microsystems CyberBlade XP4m32 [1023:2100] (rev 91) (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device [1179:0002]
    Flags: bus master, 66MHz, medium devsel, latency 8, IRQ 11
    Memory at f0000000 (32-bit, non-prefetchable) [size=128M]
    Memory at efc00000 (32-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (32-bit, non-prefetchable) [size=128M]
    Memory at dfff8000 (32-bit, non-prefetchable) [size=32K]
    [virtual] Expansion ROM at 54000000 [disabled] [size=256K]
    Capabilities: [80] AGP version 2.0
    Capabilities: [90] Power Management version 2

02:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 83)
    Subsystem: Toshiba America Info Systems Device [1179:0001]
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at dfdff000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at cf40 [size=64]

```

---

### Post by Toz on 2013-04-10
Whats interesting about that log file is that in each instance, the log file is showing that the suspend/resume cycle was completed. Can you do the following:

1. Delete the existing log file (it will get recreated automatically).
```
sudo rm /var/log/pm-suspend.log
```

2. Suspend using the suspend menu item and resume.

3. Close the lid. Wait 5 minutes. Open the lid. 

At this point, does it sound like the computer has resumed? Are lights flashing again? Do you have brightness function keys? Can you try restoring brightness? Can you go to the first console (Ctrl+Alt+F1) and get a command prompt?

4. Once you've recovered, post back /var/log/pm-suspend.log and lets see what it says.

---

### Post by thatstheway on 2013-04-10
And Toz, re: the Trident driver being installed, in case you still wanted the /var/log/Xorg.0.log file, it's: 

[http://paste.ubuntu.com/5697112/](http://paste.ubuntu.com/5697112/)

---

### Post by thatstheway on 2013-04-10
Here are the results of the test in post #9: 

[http://paste.ubuntu.com/5697150/](http://paste.ubuntu.com/5697150/)

And Toz, after closing the lid and waiting for the computer to suspend, it "looks" like it's about to wake up after I hit the power key, but goes to a black screen. Brightness keys have no effect. Ctrl-Alt-F1 does not bring up the terminal. The sequence Ctl-Alt-T, sudo reboot does not reboot the machine. space bar, trackpad, trackpad clicks, mouse clicks, all have no effect.

---

### Post by thatstheway on 2013-04-10
The results of the test in post #9, that is. [sorry, I can't figure out how to delete posts. "Edit Post" says Edit/Delete in the rollover, but I can't see the Delete option.]

---

### Post by Toz on 2013-04-10
I think that suspend/resume is working in both instances. From your log file:
> 
Wed Apr 10 18:38:36 PDT 2013: Running hooks for suspend.
.....
Wed Apr 10 18:38:40 PDT 2013: performing suspend
Wed Apr 10 18:38:53 PDT 2013: Awake.
Wed Apr 10 18:38:53 PDT 2013: Running hooks for resume
.....
Wed Apr 10 18:38:55 PDT 2013: Finished.
.....
.....
Wed Apr 10 18:39:14 PDT 2013: Running hooks for suspend.
.....
Wed Apr 10 18:39:17 PDT 2013: performing suspend
Wed Apr 10 18:40:11 PDT 2013: Awake.
Wed Apr 10 18:40:11 PDT 2013: Running hooks for resume
.....
Wed Apr 10 18:40:13 PDT 2013: Finished.


I believe the issue is that when you close the lid and re-open it, the screen isn't coming back.

As a first step, lets get some brightness values. 
First, clear out the log file:
```
sudo rm /var/log/pm-suspend.log
```

Then, create the file /etc/pm/sleep.d/000brightness:
```
gksudo gedit /etc/pm/sleep.d/000brightness
```
...with the following content:
```

#!/bin/bash
case "$1" in
	hibernate|suspend)
		for file in /sys/class/backlight/*; do echo $file; cat $file/brightness; cat $file/max_brightness; done
		;;
	thaw|resume)
		for file in /sys/class/backlight/*; do echo $file; cat $file/brightness; cat $file/max_brightness; done
                ;;
        *)
                ;;
esac
```
...save the file and make the file executable:
```
sudo chmod +x /etc/pm/sleep.d/000brightness
```

Then, close the lid, recover the computer, and post back /var/log/pm-suspend.log.

---

### Post by thatstheway on 2013-04-10
Ok I'll try not to figure out why, but things have changed. When I closed the lid before, the power light would change from steady green to pulsing red, as it did when I issued the command from the menu. But after those changes, it remains steady green, and when I open the lid again and press any key, the xscreensaver log-on comes up, something I've never seen before. (possibly because it was too dark and I wasn't expecting this?) I can then log on, and resume! 

Here's the suspend log:

[http://paste.ubuntu.com/5697303/](http://paste.ubuntu.com/5697303/)

Did it really suspend? Hm, I just tried the suspend command from the menu and it didn't work. It looked like it was going to suspend, the wireless signal cleared out, but then the signal came back and it didn't suspend. I cleared the log, tried it from the menu, and this is what the log now says: 

[http://paste.ubuntu.com/5697315/](http://paste.ubuntu.com/5697315/)

---

### Post by Toz on 2013-04-11
Sorry, typo in the script. Try this version of the script instead:
```
#!/bin/bash
case "$1" in
	hibernate|suspend)
		for file in /sys/class/backlight/*; do echo $file; cat $file/brightness; cat $file/max_brightness; done
		;;
	thaw|resume)
		for file in /sys/class/backlight/*; do echo $file; cat $file/brightness; cat $file/max_brightness; done
                ;;
        *)
                ;;
esac
```

---

### Post by thatstheway on 2013-04-11
Thanks! Here it is: 

[http://paste.ubuntu.com/5698531/](http://paste.ubuntu.com/5698531/)

---

### Post by Toz on 2013-04-11
Can you go into the BIOS and if you have a VT-d virtualization setting, disable it by switching to "VT-x only".

EDIT: If that doesn't work, lets try some quirks.

First, delete /etc/pm/config.d/module so that we are using pm-suspend again.

Then, create a custom quirks file:
```
gksudo gedit /etc/pm/config.d/custom-quirks
```
...and add the following:
```
ADD_PARAMETERS="--quirk-s3-bios"
```

Finally, delete /var/log/pm-suspend.log and perform 2 suspends: one from the menu and one by closing the lid. Post back /var/log/pm-suspend.log.

---

### Post by thatstheway on 2013-04-11
Thanks again, Toz! The BIOS for my machine (Toshiba Portege R100) is very barebones, and doesn't have any virtualization options. The only option it has that has anything to do with graphics is Power on Display, which I have set to "LCD+AnalogRGB," and the other option is "Auto Selected." I can go into more detail about my barebones BIOS options if it seems useful. 

I tried your "quirk" test, and this time, Suspend-from-the-menu behaved exactly how Suspend-from-closed-lid has been behaving, a black screen and a reboot. Here is the log: 

[http://paste.ubuntu.com/5699214/](http://paste.ubuntu.com/5699214/)

---

### Post by Toz on 2013-04-11
> **thatstheway said:**
> Thanks again, Toz! The BIOS for my machine (Toshiba Portege R100) is very barebones, and doesn't have any virtualization options. The only option it has that has anything to do with graphics is Power on Display, which I have set to "LCD+AnalogRGB," and the other option is "Auto Selected." I can go into more detail about my barebones BIOS options if it seems useful. 

I tried your "quirk" test, and this time, Suspend-from-the-menu behaved exactly how Suspend-from-closed-lid has been behaving, a black screen and a reboot. Here is the log: 

[http://paste.ubuntu.com/5699214/](http://paste.ubuntu.com/5699214/)

Lets try a few more quirks. Edit /etc/pm/config.d/custom-quirks and change the quirk to:
```
--quirk-vbe-post
```
...and try again.

Other quirks to try would include:
--quirk-vbemode-restore
--quirk-vbestate-restore

Reference: [http://manpages.ubuntu.com/manpages/hardy/man8/pm-action.8.html]("http://manpages.ubuntu.com/manpages/hardy/man8/pm-action.8.html")

---

### Post by thatstheway on 2013-04-11
Results of 

```
--quirk-vbe-post
```:

Behavior: Suspend-by-menu and suspend-by-lid required reboots. 

Log: 

[http://paste.ubuntu.com/5699417/](http://paste.ubuntu.com/5699417/)

I'll try the others...

---

### Post by thatstheway on 2013-04-11
Results of --quirk-vbemode-restore:

This was interesting (and we might be getting warmer!)

Behavior, Suspend-by-menu:
Restores correctly after Suspend, however the screen image is "corrupted" (or something): It's split into 3 views, with the gear menu off-screen to the right. 

Behavior, Suspend-by-lid: 
Restores to black screen with screensaver message (Progress!): "xscreensaver:12:12:15: not launching hack (throttled)." AND screen is still split into 3. However, hitting (presumably) any key brings up screensaver log-on, and I can log on and resume (but of course screen is split) But, this is a real restore after closing the lid, which is progress!

Log: 

[http://paste.ubuntu.com/5699450/](http://paste.ubuntu.com/5699450/)

Trying (why not) --quirk-vbestate-restore...

Ok just have to edit this comment to give a hearty **THANK YOU TO TOZ**, who **ROCKS** (with his incredibly patient and detailed problem-solving), because really, this solved my problem. When I get the split screen, I just need to refresh things by hitting Ctrl-Alt-F1 to go to the terminal, and then Ctl-Alt-F7 to get back, and the screen is normal. This is a hassle, but it's not even remotely as bad as our 6-year-old closing the lid of the laptop when we're not looking (he does that) and loosing unsaved work. Googling around I see many people have this "screen splits in 3 after suspend" problem, and I'll try to fix that, but again, it's not critical. Toz, or anyone else, if you have any thoughts about that, of course, I'd love to hear 'em! : ) And Toz, let me know if you'd like me to start this 3-screen issue as a new topic or just leave it as is.

---

### Post by thatstheway on 2013-04-11
Results of --quirk-vbestate-restore:

Suspend-by-menu, all good; Suspend-by-lid, still required reboot. 

Log: 

[http://paste.ubuntu.com/5699547/](http://paste.ubuntu.com/5699547/)

---

### Post by thatstheway on 2013-04-11
The 3-screen issue is FIXED! Just reinstalled the trident driver. This baby's CLOSED. : ) Thanks again, Toz!

---

### Post by Toz on 2013-04-11
Glad to hear. I'll mark this thread as solved.

---

### Post by thatstheway on 2013-04-12
Minor Update: 
The 3-screen problem came back, and I wanted to avoid reinstalling the video drivers on a regular basis if I can, so I went back to Toz's [reference]("http://manpages.ubuntu.com/manpages/precise/man8/pm-action.8.html") in **post #19**, and tried out **--quirk-dpms-on**, which also works. Perhaps this will solve the 3-screen problem, or perhaps the 3-screen problem is completely unrelated to these quirks. Time will tell!

---

