---
title: "ubuntu 12.04.3 - touchpad not working"
date: 2013-09-24
forum: New to Ubuntu
---

### Post by plan425 on 2013-09-24
I recently got an Acer laptop that had linpus Linux loaded on it, I found out that's not a very popular distribution so I am trying to install Ubuntu 12.04.3. I booted from flash drive and I get to the language selection screen but the mouse does nothing; however, the keyboard works fine and I can continue through the prompts with they keyboard.  I also tried a USB mouse and nothing. 

Anybody have any idea why?  I am extremely new to Linux and am unsure of what to do.  Any help is greatly appreciated.

Thanks

---

### Post by varunendra on 2013-09-25
Hello plan425, Welcome to the forums. :)

Touchpad and USB mouse failing at the same time is not normal. Have you verified the integrity of the downloaded ISO ([How To MD5Sum]("https://help.ubuntu.com/community/HowToMD5SUM")) or the flash drive (Check disk for defects option)? Please ensure these are okay first.

If both the ISO and the flash drive are okay, please post the following outputs while the USB mouse is plugged in -
```
xinput
cat /proc/bus/input/devices
lsmod
```

---

### Post by plan425 on 2013-09-25
Thanks for the help Varun!

So i re-downloaded ubunutu, checked the md5 sum, and they matched.  Re-installed it on the usb drive, and then tried to boot ubuntu, no touch pad functionality.  So i tried the usb mouse again, and it worked this time.  I must have got a bad download last night or something.  I did have some download issues but who knows, i have a clearer head today.  

So, now i have installed ubuntu and my usb mouse works, but still no touchpad.  Any advice to solve this issue?

---

### Post by varunendra on 2013-09-25
> **plan425 said:**
> So, now i have installed ubuntu and my usb mouse works, but still no touchpad.  Any advice to solve this issue?
Maybe, please post the same outputs I asked before. :)

---

### Post by plan425 on 2013-09-25
Sorry, here is the output:

```
TravelMate-X483:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft Wireless Optical Mouse® 1.00    id=10    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HD WebCam                                   id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                            id=14    [slave  keyboard (3)]

TravelMate-X483:~$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
U: Uniq=
H: Handlers=event2 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=sysrq kbd event4 
B: PROP=0
B: EV=120013
B: KEY=10000 c020000000000 0 0 700f02000003 3803078f830f401 febfffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=045e Product=00e1 Version=0111
N: Name="Microsoft Microsoft Wireless Optical Mouse® 1.00"
P: Phys=usb-0000:00:14.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/input/input5
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=0
B: EV=17
B: KEY=1f0000 0 0 0 0
B: REL=1c3
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Acer WMI hotkeys"
P: Phys=wmi/input0
S: Sysfs=/devices/virtual/input/input6
U: Uniq=
H: Handlers=rfkill kbd event6 
B: PROP=0
B: EV=13
B: KEY=1c0000 0 0 0 0 1600800000c00 8000000000300000 0 0
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Acer BMA150 accelerometer"
P: Phys=wmi/input1
S: Sysfs=/devices/virtual/input/input7
U: Uniq=
H: Handlers=event7 js0 
B: PROP=0
B: EV=9
B: ABS=7

I: Bus=0003 Vendor=1bcf Product=2c32 Version=0629
N: Name="HD WebCam"
P: Phys=usb-0000:00:1a.0-1.1/button
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0011 Vendor=0002 Product=000e Version=0000
N: Name="ETPS/2 Elantech Touchpad"
P: Phys=isa0060/serio2/input0
S: Sysfs=/devices/platform/i8042/serio2/input/input9
U: Uniq=
H: Handlers=mouse1 event9 
B: PROP=5
B: EV=b
B: KEY=e420 10000 0 0 0 0
B: ABS=661800011000003

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input10
U: Uniq=
H: Handlers=kbd event10 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input11
U: Uniq=
H: Handlers=event11 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input12
U: Uniq=
H: Handlers=event12 
B: PROP=0
B: EV=21
B: SW=4

TravelMate-X483:~$ lsmod
Module                  Size  Used by
parport_pc             28152  0 
ppdev                  17073  0 
bnep                   18036  2 
rfcomm                 42641  12 
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_realtek    78399  1 
joydev                 17377  0 
coretemp               13355  0 
uvcvideo               80847  0 
kvm_intel             132891  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
kvm                   443165  1 kvm_intel
snd_hda_intel          39619  3 
videodev              129260  2 uvcvideo,videobuf2_core
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ghash_clmulni_intel    13259  0 
cryptd                 20373  1 ghash_clmulni_intel
acer_wmi               32467  0 
arc4                   12615  2 
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
sparse_keymap          13890  1 acer_wmi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
ath9k                 149924  0 
ath9k_common           14055  1 ath9k
ath9k_hw              413680  2 ath9k_common,ath9k
snd_timer              29425  2 snd_pcm,snd_seq
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
i915                  600351  3 
mac80211              606457  1 ath9k
wmi                    19070  1 acer_wmi
video                  19390  2 i915,acer_wmi
drm_kms_helper         49394  1 i915
mac_hid                13205  0 
drm                   286313  4 i915,drm_kms_helper
snd                    68876  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
lpc_ich                17061  0 
cfg80211              510937  3 ath,ath9k,mac80211
ath3k                  12918  0 
i2c_algo_bit           13413  1 i915
microcode              22881  0 
btusb                  22474  0 
psmouse                95870  0 
bluetooth             228619  23 bnep,ath3k,btusb,rfcomm
lp                     17759  0 
soundcore              12680  1 snd
mei                    41158  0 
parport                46345  3 lp,ppdev,parport_pc
serio_raw              13215  0 
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
tg3                   153796  0 
ptp                    18621  1 tg3
pps_core               14080  1 ptp
ahci                   25731  2 
libahci                31364  1 ahci

```

---

### Post by varunendra on 2013-09-25
The touchpad is obviously detected and registered -
> **plan425 said:**
> 
```
TravelMate-X483:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft Wireless Optical Mouse® 1.00    **[COLOR="#FF0000"]id=10[/COLOR]**    [slave  pointer  (2)]
&#9116;   &#8627; **ETPS/2 Elantech Touchpad                    id=13**    [slave  pointer  (2)]
....
....
I: Bus=0011 Vendor=0002 Product=000e Version=0000
N: Name=**"ETPS/2 Elantech Touchpad"**
P: Phys=isa0060/serio2/input0
S: **Sysfs=/devices/platform/i8042/serio2/input/input9**
U: Uniq=
H: **Handlers=mouse1 event9 **
B: PROP=5
B: EV=b
B: KEY=e420 10000 0 0 0 0
B: ABS=661800011000003

```

However, it is interesting that its XID is greater than the external mouse, indicating that the external one was registered BEFORE the touchpad. Shouldn't be a problem though, just interesting. Can you try rebooting without the external one plugged in (plug it in again when the OS is fully loaded and ready to work) and see if it still receives a higher XID (currently the external one's xid is 10, while the touchpad's 13)?

Also, perhaps there is a hardware switch or Fn+ key combo to enable/disable the touchpad. Are you aware of that? Does it work? If not, please try -
```
sudo modprobe -rv psmouse
sudo modprobe -v psmouse
```
Any change?

---

### Post by plan425 on 2013-09-25
When i reboot without the usb mouse, the usb has a higher XID than the touchpad.  I tried to use the touchpad before connecting the usb mouse and it didn't work before or after.
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=12    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft Wireless Optical Mouse® 1.00    id=14    [slave  pointer  (2)]
```

The laptop does control the touchpad with FN-F7, however, i have toggled it on and off and the touchpad still does not work.

When i enter the last 2 commands i get the following:
```
TravelMate-X483:~$ sudo modprobe -rv psmouse
[sudo] password for : 
rmmod psmouse
TravelMate-X483:~$ sudo modprobe -v psmouse
insmod /lib/modules/3.8.0-19-generic/kernel/drivers/input/mouse/psmouse.ko 

```

---

### Post by varunendra on 2013-09-26
And reloading psmouse didn't make any difference to touchpad? One possibility ruled out then. Now -
> **plan425 said:**
> The laptop does control the touchpad with FN-F7, however, i have toggled it on and off and the touchpad still does not work.

..suggests to me that the module 'acer_wmi' is unable to do properly what it is supposed to do. Let's try blacklisting it and see if the touchpad can do any better without it. Please do -
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
..then reboot. Does it make the difference we want? Any bad side effects?

If it doesn't help, please try -
```
xinput --float "ETPS/2 Elantech Touchpad"
xinput --reattach "ETPS/2 Elantech Touchpad" "Virtual core pointer"
```
Any difference? If not, please post the outputs of the three commands in post #2 again, from the current state.

And the most important question that I should have asked earlier - Does the touchpad work in the Live session (booted from the live cd/usb)? Have you tried updating the system yet?
Which kernel are you running currently (output of "uname -mr")?

**EDIT: **Ugh, forget that, looks like you are running on a live session already, haven't installed it yet. Please just confirm that if so.

---

### Post by plan425 on 2013-09-26
> If it doesn't help, please try -
```
xinput --float "ETPS/2 Elantech Touchpad"
xinput --reattach "ETPS/2 Elantech Touchpad" "Virtual core pointer"
```
Any difference? If not, please post the outputs of the three commands in post #2 again, from the current state.

That did it!  Touchpad is working now.

> And the most important question that I should have asked earlier - Does the touchpad work in the Live session (booted from the live cd/usb)? Have you tried updating the system yet?
Which kernel are you running currently (output of "uname -mr")?

**EDIT: **Ugh, forget that, looks like you are running on a live session already, haven't installed it yet. Please just confirm that if so.
 The kernel i am running is "3.8.0-19-generic x86_64".  I thought that it is installed, since i am booting from the HD

Thank you so much for your help!

---

### Post by varunendra on 2013-09-26
Hmm... time for a little celebration then. :)

So assuming it is installed indeed, the system does not seem up to date. Because the current kernel version should be higher than 3.8.0-19. While being connected to internet, please try updating the system -
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Post back if there are any errors in the update process. If finished successfully, it will probably ask you to reboot. Please do so and see if the touchpad works automatically. If not, we can cook up a workaround that should make it automatic.

And let's take a look at the blacklist file to see if the change we made is there -
```
cat /etc/modprobe.d/blacklist.conf | grep acer
```
If it is there but didn't help, I think we should let the poor innocent module be free from blacklisting :P

---

### Post by plan425 on 2013-09-26
Everything seems to be working great at this point.  I made the update per the command you provided me and it went smoothly.  The version now is: 3.8.0-30-generic x86_64, which i believe is correct.
It looks like the mouse is still blacklisted and i do not think it helped. ```
TravelMate-X483:~$ cat /etc/modprobe.d/blacklist.conf | grep acer
blacklist acer_wmi
```

Again, everything is working great, the float and reattach commands fixed everything.  I cannot be happy with how the computer and ubuntu are running, and am excited to start exploring now that everything is functioning correctly!  Thanks so much for your help again!!

---

### Post by varunendra on 2013-09-26
Awesome!

Let's first release acer_wmi from blacklist. I like the commandline way -
```
sudo sed -i '/blacklist acer_wmi/ d' /etc/modprobe.d/blacklist.conf
```
Then check it back -
```
cat /etc/modprobe.d/blacklist.conf
```
..make sure the "blacklist acer_wmi" line is gone from the bottom (it is currently at the bottom line).

Now, just to make sure I'm not taking unnecessary steps, please confirm -
Do you still need the "float" and "reattach" commands to make it work ? If yes, please also post the output of -
```
lsb_release -cd
```

---

### Post by plan425 on 2013-09-27
Touchpad is not blacklisted anymore.  The touchpad has worked ever since the float/reattach, i have shutdown the computer several times and on every reboot, the touchpad works without me doing anything.  The touchpad/computer/ubuntu are all working great!

Thanks again for guiding me through this, your help is greatly appreciated!!

---

### Post by Jonathan Precise on 2013-09-27
Please mark as solved by going to thread tools.

---

### Post by plan425 on 2013-09-27
Solved, thanks again.

---

### Post by varunendra on 2013-09-28
> **plan425 said:**
> Touchpad is not blacklisted anymore.  The touchpad has worked ever since the float/reattach, i have shutdown the computer several times and on every reboot, the touchpad works without me doing anything.  The touchpad/computer/ubuntu are all working great!

Thanks again for guiding me through this, your help is greatly appreciated!!
You're most welcome :)

It was probably the update that fixed some bug the system had.
Just for your info, what we blacklisted was not touchpad or mouse, but a driver that is supposed to control some special key actions (usually the Fn+ combos), but *sometimes* gets confused. Evidently, it was not the problem in your case.

> **plan425 said:**
> Solved, thanks again.
This is how to mark the thread as [SOLVED] (so it appears in a search result with [SOLVED] prefix) : [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

It helps others by indicating that the thread contains a possible solution to the topic.

Thanks for your feedback ! Was a good experience for me too. :)

---

### Post by plan425 on 2013-09-28
I think that driver was the issue.  Once i un-blacklisted it. the touchpad still worked.  Until i rebooted the computer, then it did not work.  So i re-blacklisted the driver, ran the float & reattach commands and it worked again.

---

