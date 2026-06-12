---
title: "freshly installed so, bad resolution"
date: 2015-10-02
forum: New to Ubuntu
---

### Post by gustavo19 on 2015-10-02
Hello everyone, i'm new here and i just installed ubuntu, i have a viewsonic monitor with hdmi conection on a nvidia 450 graphics card and it was working perfect, i was doing updates and i still need to do so some upgrades i think, but the system got halted a couple of times and when i restarted it wouldn't move past boot and give me a screen like nothing was conected, though sometimes a little bar would flash in the corner but nothing more (now i know i could have oppened a terminal there but i didn't i kept restarting it), since it has other output conections i plugged another cable a dvi and the screen works perfect there and i can access everything, but the hdmi took some time untill it let me see anything in it as it didn't recognise it, now i can use the hdmi but only at low resolution, i also have a windows installed on another disk, when i plug it with the hdmi cable it has low resolution too, and the dvi works perfect, can anyone help me fix this?

     let's see, 
-Installed ubuntu 14.04.1 
-installed the propietary nvidia drivers for the nvidia card, i think that's what got it to see the hdmi 
-tried but failed to use my surround sound 7.1 creative speakers (in case it has any relevance to this, only the left three speakers seem to work)
-even the motherboard's bios shows the low resolution, before a black space could be seen between the image of the different buttons i could press to mess with the bios and the actual resolution of the screen, now it takes the whole screen ... maybe a photo could show this better if you guys need it
-i have a photo of the error it showed when i hadn't installed the propietary drivers

...

if you need any type of info let me know and i'll post it right away

---

### Post by cariboo on 2015-10-02
If your system froze while doing updates, you may have quite a few dependency problems, start in recovery mode, enable networking, then select root. Once at the prompt type:

```
apt-get install -f
```

to finish the updates.

---

### Post by grahammechanical on 2015-10-02
Just a small point.

The video driver does not load until a little bit after Windows or Linux has started loading. So, if you are seeing this at the very start when you get the motherboard splash screen and messages about how to enter the BIOS and at the Grub boot menu, then it is a hardware problem.

Could be that the HDMI cable is faulty.

Regards.

---

### Post by gustavo19 on 2015-10-02
Hi, thx for answering, the cable is brand new, I tested it with another computer and it works, I will try that command as soon as I can

> **cariboo said:**
> If your system froze while doing updates, you may have quite a few dependency problems, start in recovery mode, enable networking, then select root. Once at the prompt type:

```
apt-get install -f
```

to finish the updates.

i used the code you said and i got this:


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  account-plugin-windows-live libupstart1 linux-headers-generic-lts-utopic
  linux-image-generic-lts-utopic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 45 not upgraded.


```

can i remove them like it suggests?

> **grahammechanical said:**
> Just a small point.

The video driver does not load until a little bit after Windows or Linux has started loading. So, if you are seeing this at the very start when you get the motherboard splash screen and messages about how to enter the BIOS and at the Grub boot menu, then it is a hardware problem.

Could be that the HDMI cable is faulty.

Regards.
hi again, having this in mind, i tried the pc with the cable on another monitor and they worked like a charm, now i wonder (because i read a bit about it), could it be that the edid got distorted when comming from the hdmi port of he monitor?, where i live, a lot of 'blackouts' happen, they basically take down the lights for 2 to 4 hours any given day, and i remember it did happen right after the updates i did, could it be the port? or maybe the information (the edid)?, how can i check this? or work around it?

---

### Post by sandyd on 2015-10-02
Please post the output of```
xrandr
```

---

### Post by gustavo19 on 2015-10-02
> **sandyd said:**
> Please post the output of```
xrandr
```

sure, this is what i got:
```
Screen 0: minimum 8 x 8, current 800 x 600, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
DVI-I-2 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3*+
DVI-I-3 disconnected (normal left inverted right x axis y axis)


```
also, when i input the password to unlock the disk and, just before it lets me put my account pasword it shows a greater resolution, i THINK it's the normal resolution of 1920x 1080 but i'm not sure, then it goes back to the lower resolution and continues 'normally' (as in the same low resolution)

---

### Post by sandyd on 2015-10-02
So your resolution can't be detected properly by X anymore...

Can you post the output of the following:
```

cat /var/log/dmesg | grep -i edid
```

We just need to determine whether its X/drivers that are acting up, or EDID not being received.

---

### Post by gustavo19 on 2015-10-02
> **sandyd said:**
> So your resolution can't be detected properly by X anymore...

Can you post the output of the following:
```

cat /var/log/dmesg | grep -i edid
```

We just need to determine whether its X/drivers that are acting up, or EDID not being received.

i would love to post it but it gives no output whatsoever, this is what i saw:

```
root@sayer:/home/guvic# cat /var/log/dmesg | grep -i edid
root@sayer:/home/guvic# 


```

---

### Post by sandyd on 2015-10-02
Ok, so it is not an EDID error.

Can you post the output of
```

dpkg -l | grep -i nvidia
cat /etc/X11/xorg.conf
```
I want to make sure that the nvidia driver is not partway installed/etc before continueing.

---

### Post by gustavo19 on 2015-10-02
> **sandyd said:**
> Ok, so it is not an EDID error.

Can you post the output of
```

dpkg -l | grep -i nvidia
cat /etc/X11/xorg.conf
```
I want to make sure that the nvidia driver is not partway installed/etc before continueing.

thank you for the help you are giving me, i was doing the steps and this came out 
```
root@sayer:/home/guvic# cvt 1920 1080
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
root@sayer:/home/guvic# ^C
root@sayer:/home/guvic# xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
root@sayer:/home/guvic# 
root@sayer:/home/guvic# xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  31
  Current serial number in output stream:  31


```
... ok

this is what i got from that
```

root@sayer:/home/guvic# dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                         0.7-2ubuntu1                                        i386         Interface for toggling the power on nVidia Optimus video cards
ii  libcuda1-346                                          346.96-0ubuntu0.0.1                                 i386         NVIDIA CUDA runtime library
ii  nvidia-346                                            346.96-0ubuntu0.0.1                                 i386         NVIDIA binary driver - version 346.96
ii  nvidia-libopencl1-346                                 346.96-0ubuntu0.0.1                                 i386         NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-346                                 346.96-0ubuntu0.0.1                                 i386         NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                               i386         Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       331.20-0ubuntu8                                     i386         Tool for configuring the NVIDIA graphics driver


```

---

### Post by gustavo19 on 2015-10-06
It appears sandyd has become too busy to help, can anyone else help me? i still can't use my hdmi imput and it's a brand new monitor x.x

---

### Post by sandyd on 2015-10-06
Sorry, forgot to check on this thread yesterday

So the propretary driver packages are installed properly, could be that the module is not configured properly or not loading
Can you post the output of
```

cat /etc/X11/xorg.conf
lsmod
```
as well?

Does the nvidia settings panel only show 800x600 as the only available resolution?

---

### Post by gustavo19 on 2015-10-06
> **sandyd said:**
> Sorry, forgot to check on this thread yesterday

So the propretary driver packages are installed properly, could be that the module is not configured properly or not loading
Can you post the output of
```

cat /etc/X11/xorg.conf
lsmod
```
as well?

Does the nvidia settings panel only show 800x600 as the only available resolution?

Hello again, i did that and i don't see where it says the resolutions, i'm gonna paste it here and look at it cuz it looks scrambled on the screen as it is
```
 cat /etc/X11/xorg.conf
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 331.20  (buildd@komainu)  Mon Feb  3 15:11:14 UTC 2014

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 346.96  (buildmeister@swio-display-x86-rhel47-06)  Sun Aug 23 22:59:12 PDT 2015

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VX2452 Series"
    HorizSync       24.0 - 82.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTS 450"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DVI-I-2: nvidia-auto-select +0+0, HDMI-0: nvidia-auto-select +1920+0 {viewportin=1920x1080}"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

root@sayer:/home/guvic# lsmod
Module                  Size  Used by
bnep                   18895  2 
rfcomm                 58045  0 
bluetooth             391253  10 bnep,rfcomm
6lowpan_iphc           18262  1 bluetooth
nvidia               7559850  43 
arc4                   12536  2 
rt73usb                26912  0 
rt2x00usb              20041  1 rt73usb
rt2x00lib              48886  2 rt73usb,rt2x00usb
mac80211              559049  2 rt2x00lib,rt2x00usb
cfg80211              418811  2 mac80211,rt2x00lib
crc_itu_t              12627  1 rt73usb
snd_hda_codec_hdmi     46396  4 
gpio_ich               13315  0 
snd_hda_intel          29285  2 
snd_ca0106             39374  2 
snd_ac97_codec        105860  1 snd_ca0106
snd_hda_controller     29944  1 snd_hda_intel
snd_hda_codec         120371  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_controller
ac97_bus               12642  1 snd_ac97_codec
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                87194  6 snd_ac97_codec,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_ca0106
lpc_ich                16877  0 
snd_seq_midi           13324  0 
coretemp               13201  0 
snd_seq_midi_event     14475  1 snd_seq_midi
kvm_intel             137114  0 
snd_rawmidi            25722  2 snd_ca0106,snd_seq_midi
kvm                   388518  1 kvm_intel
snd_seq                56592  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28648  2 snd_pcm,snd_seq
serio_raw              13251  0 
drm                   255469  3 nvidia
snd                    66670  19 snd_ac97_codec,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_ca0106
soundcore              14599  2 snd,snd_hda_codec
shpchp                 32143  0 
parport_pc             32021  1 
mac_hid                13059  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
xts                    12749  1 
gf128mul               14503  1 xts
dm_crypt               22653  1 
hid_generic            12503  0 
usbhid                 47035  0 
hid                    95946  2 hid_generic,usbhid
uas                    22631  0 
usb_storage            52721  1 uas
pata_acpi              12901  0 
atl1c                  40964  0 


```
it does seem to say 1920x1080 here 'Option         "metamodes" "DVI-I-2: nvidia-auto-select +0+0, HDMI-0: nvidia-auto-select +1920+0 {viewportin=1920x1080}' but i don't know why it doesn't do it, could i have damaged the output port on the monitor?, as i said before, it does show a higher resolution just before it lets me input the user password  but it changes back (i'm gonna try and make a video the next time i reboot it) i use the dvi port and it does give 1920x1080 resolution from the moment i turn on the pc

---

### Post by gustavo19 on 2015-10-06
it also gave me a bunch of updates, i'm gonna apply them, none of them say anithing about video, how do i see if i installed 32 or 64 bits? because this machine can handle 64 bits and the updates have 32 bits written all over them

---

### Post by sandyd on 2015-10-06
Its possible that the port is damaged, from what I can see:
[LIST]
[*]Proprietary Nvidia Drivers are installed properly and loaded
[*]dmesg does not show an error to indicate that it cannot fetch EDID
[*]Modes supported by screen do not show the correct resolutions (other than the lowest one)
[/LIST]

We can see if forcing the resolution will allow you to get a correct resolution even if hardware is malfunctioning:
Instructions adapted from [https://wiki.archlinux.org/index.php/Xrandr#Adding_undetected_resolutions](https://wiki.archlinux.org/index.php/Xrandr#Adding_undetected_resolutions)
What you will need in the below steps is your monitor resolution.

Run the following, and replace the [COLOR="#0000FF"]blue[/COLOR] text with your own resolution.

```

cvt [COLOR="#0000FF"]1280 1024[/COLOR]

```

It will output something like below:
```

# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline [COLOR="#FF0000"]"1280x1024_60.00" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync[/COLOR]
```

Paste the red section of your command output into the next command.
```

xrandr --newmode [COLOR="#FF0000"]"1280x1024_60.00" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync[/COLOR]

```

In the below command, replace "1280x1024_60.00" with the contents of the double quotes in the red output.
```
xrandr --addmode HDMI-0 *1280x1024_60.00*
```

Run the following to activate the config (replace same as above)
```

xrandr --output HDMI-0 --mode 1280x1024_60.00
```

---

### Post by gustavo19 on 2015-10-06
> **sandyd said:**
> Its possible that the port is damaged, from what I can see:
[LIST]
[*]Proprietary Nvidia Drivers are installed properly and loaded 
[*]dmesg does not show an error to indicate that it cannot fetch EDID 
[*]Modes supported by screen do not show the correct resolutions (other than the lowest one) 
[/LIST]

We can see if forcing the resolution will allow you to get a correct resolution even if hardware is malfunctioning:
Instructions adapted from [https://wiki.archlinux.org/index.php/Xrandr#Adding_undetected_resolutions](https://wiki.archlinux.org/index.php/Xrandr#Adding_undetected_resolutions)
What you will need in the below steps is your monitor resolution.

Run the following, and replace the [COLOR=#0000FF]blue[/COLOR] text with your own resolution.

```

cvt [COLOR=#0000FF]1280 1024[/COLOR]

```

It will output something like below:
```

# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline [COLOR=#FF0000]"1280x1024_60.00" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync[/COLOR]
```

Paste the red section of your command output into the next command.
```

xrandr --newmode [COLOR=#FF0000]"1280x1024_60.00" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync[/COLOR]

```

In the below command, replace "1280x1024_60.00" with the contents of the double quotes in the red output.
```
xrandr --addmode HDMI-0 *1280x1024_60.00*
```

ok, i did that and first i forgot to put the r on xrandr on the add command, didn't see it and did the create command again and came out an error, then noticed and the missing r and added it and came out with another error, this is what came out

```
root@sayer:/home/guvic# cvt 1920 1080
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

root@sayer:/home/guvic# xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

root@sayer:/home/guvic# xrand --addmode HDMI-0 1920x1080_60.00
No command 'xrand' found, did you mean:
 Command 'rand' from package 'rand' (universe)
 Command 'xrandr' from package 'x11-xserver-utils' (main)
xrand: command not found

root@sayer:/home/guvic# xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  31
  Current serial number in output stream:  31

root@sayer:/home/guvic# xrandr --addmode HDMI-0 1920x1080_60.00X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  31
  Current serial number in output stream:  32

root@sayer:/home/guvic# 


```

oh and the first time i did the newmode code i didn't hit enter, it just went on to another line so i think it didn't do it the first time
could we copy the info from the output of the dvi cable? because that works fine and it gives the 1920 x 1080 resolution it had with the hdmi

---

### Post by gustavo19 on 2015-10-06
ok i just had a mayor crash when i was rebooting from installing the updates, they were some libraries and firefox updates, it asked me to arrange the screen info because it couldn't detect it, and when i put it to load the generic info it did just fine, but when i tried to move to the terminal, it crashed, it got stuck on the black screen with the blinking dash, i hit ctrl alt f1 but it did nothing, then i noticed my keyboard was frozen, and i forced a shut down and turned it back on, this time it turned on and didn't show me the big resolution like before, it was trying to send a report of the issue to the developers but i think it has crashed ... it says i have a i386 system and that's for the 32 bit and i really think i installed this wrong and possibly damaged my hdmi port in the process

---

### Post by sandyd on 2015-10-06
> **gustavo19 said:**
> ok i just had a mayor crash when i was rebooting from installing the updates, they were some libraries and firefox updates, it asked me to arrange the screen info because it couldn't detect it, and when i put it to load the generic info it did just fine, but when i tried to move to the terminal, it crashed, it got stuck on the black screen with the blinking dash, i hit ctrl alt f1 but it did nothing, then i noticed my keyboard was frozen, and i forced a shut down and turned it back on, this time it turned on and didn't show me the big resolution like before, it was trying to send a report of the issue to the developers but i think it has crashed ... it says i have a i386 system and that's for the 32 bit and i really think i installed this wrong and possibly damaged my hdmi port in the process

Ok, lets have another try - installing 32bit vs 64bit on a system won't damage the HDMI port.

Grab the Ubuntu 14.04 x64 iso from [http://releases.ubuntu.com/trusty/ubuntu-14.04.3-desktop-amd64.iso](http://releases.ubuntu.com/trusty/ubuntu-14.04.3-desktop-amd64.iso) - you can use [http://releases.ubuntu.com/trusty/ubuntu-14.04.3-desktop-amd64.iso.torrent](http://releases.ubuntu.com/trusty/ubuntu-14.04.3-desktop-amd64.iso.torrent) if your torrenting.

Verify the MD5SUM through [https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows)

After that, write to USB/DVD, and boot up.

Is the resolution correct on HDMI now?

Side note: Will view thread tomorrow - its late

---

### Post by gustavo19 on 2015-10-07
> **sandyd said:**
> Ok, lets have another try - installing 32bit vs 64bit on a system won't damage the HDMI port.

Grab the Ubuntu 14.04 x64 iso from [http://releases.ubuntu.com/trusty/ubuntu-14.04.3-desktop-amd64.iso](http://releases.ubuntu.com/trusty/ubuntu-14.04.3-desktop-amd64.iso) - you can use [http://releases.ubuntu.com/trusty/ubuntu-14.04.3-desktop-amd64.iso.torrent](http://releases.ubuntu.com/trusty/ubuntu-14.04.3-desktop-amd64.iso.torrent) if your torrenting.

Verify the MD5SUM through [https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows)

After that, write to USB/DVD, and boot up.

Is the resolution correct on HDMI now?

Side note: Will view thread tomorrow - its late

ok i'm downloading the iso, already installed the md5sums, i'm not saying the installation damaged it, but me, i could have screwed up something, i rebooted it a lot!! and then a power surge happened, i don't know if it was me, also i think the port may be damaged, like i said i tried the cable and the pc on a samsung tv and it gave amazing graphics with its necessary resolution and everything, you think if i spray it with alcohol and clean the hdmi port it could work again? i don't want to have to open the monitor and replace the port and i was hoping a forcefull software could do the trick

---

### Post by sandyd on 2015-10-07
> **gustavo19 said:**
> ok i'm downloading the iso, already installed the md5sums, i'm not saying the installation damaged it, but me, i could have screwed up something, i rebooted it a lot!! and then a power surge happened, i don't know if it was me, also i think the port may be damaged, like i said i tried the cable and the pc on a samsung tv and it gave amazing graphics with its necessary resolution and everything, you think if i spray it with alcohol and clean the hdmi port it could work again? i don't want to have to open the monitor and replace the port and i was hoping a forcefull software could do the trick

Have you tried connecting something else via HDMI to the monitor by any chance?

---

### Post by gustavo19 on 2015-10-07
> **sandyd said:**
> Have you tried connecting something else via HDMI to the monitor by any chance?
no, all i have is a pc from an aunt that goes through a hammerhead to connect to the samsung tv i talked about earlier, but it keeps dying and i've fixed it way too many times and i won't know if it's not working because of the pc or my monitor :/

---

### Post by gustavo19 on 2015-10-14
> **sandyd said:**
> Ok, lets have another try - installing 32bit vs 64bit on a system won't damage the HDMI port.

Grab the Ubuntu 14.04 x64 iso from [http://releases.ubuntu.com/trusty/ubuntu-14.04.3-desktop-amd64.iso](http://releases.ubuntu.com/trusty/ubuntu-14.04.3-desktop-amd64.iso) - you can use [http://releases.ubuntu.com/trusty/ubuntu-14.04.3-desktop-amd64.iso.torrent](http://releases.ubuntu.com/trusty/ubuntu-14.04.3-desktop-amd64.iso.torrent) if your torrenting.

Verify the MD5SUM through [https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows)

After that, write to USB/DVD, and boot up.

Is the resolution correct on HDMI now?

Side note: Will view thread tomorrow - its late

Hi, and sorry for not posting for a while, i had some stuff to resolve irl but i tried the live usb and just like my ubuntu and my windows gives me low resolution, so that settles it, the port in the monitor is faulty, this thread should be put as 'solved' or deleted, i'll try to see how to do it or does an admin have to do it? i'm rusty on forum activity

Thank you so much for all your help sandyd, i really appreciate it.

oh and i believe the fault ocurred because of the blackout, not the install, i just keep getting blackouts and voltage spikes, and just recently my voltage protector exploded because of them, so ... anyway, that's in case someone reads this post in the future looking for something similar to their problem.

---

### Post by sandyd on 2015-10-15
You can mark it as solved via Thread Tools -> Mark Thread as Solved.

---

