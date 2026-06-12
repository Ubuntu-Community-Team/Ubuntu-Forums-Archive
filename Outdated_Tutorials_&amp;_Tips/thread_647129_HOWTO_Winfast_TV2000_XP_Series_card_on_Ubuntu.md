---
title: "HOWTO: Winfast TV2000 XP Series card on Ubuntu"
date: 2007-12-22
forum: Outdated Tutorials &amp; Tips
---

### Post by nikoPSK on 2007-12-22
well here we go! This is designed for the winfast TV2000 XP series card but you can replace the tuner and card numbers. The only thing I can't seem to use is the infared remote... here:

you need to remove the "wrong" drivers:

```
 sudo rmmod bt878
sudo rmmod tuner
sudo rmmod bttv
```

then add the right ones. 

then you would do this:
```
 sudo modprobe bttv card=34 tuner=43
```

now install tvtime
```
sudo apt-get install tvtime
```
set it up and you might need to unmute a channel or two in
```
alsamixer
```

That should about do it! No remote fix found yet but this'll work with almost all cards.

---

### Post by LeDechaine on 2008-02-01
Not working for me. The tuner is not the right one, I can't even switch channels, and I get no sound.
Mine is (supposedly) with a CX23880/1/2/3 chipset.

Thanks for posting, though. Many people have problems with this card.

---

### Post by nikoPSK on 2008-02-01
> **LeDechaine said:**
> Not working for me. The tuner is not the right one, I can't even switch channels, and I get no sound.
Mine is (supposedly) with a CX23880/1/2/3 chipset.
 
Thanks for posting, though. Many people have problems with this card.
 
oh, well try findingn the right channel and such. You need to unmute things in alsamixer. :)

---

### Post by G00D_GUY on 2008-12-03
Wow. Thanks. This is almost great. Does anyone know how to unmute? i am sure that I am overlooking something simple, because it is doing so well with the video.

---

### Post by Deep Blue on 2008-12-06
> **G00D_GUY said:**
> Wow. Thanks. This is almost great. Does anyone know how to unmute? i am sure that I am overlooking something simple, because it is doing so well with the video.I'm sorry, unmute?

**EDIT**: Fool around in alsamixer (open up the Console and type "alsamixer") by muting and unmuting channels. :)

---

### Post by G00D_GUY on 2008-12-08
Thanks for the reply. I opened AlSaMixer, but I do not see an unmute button, or option anyplace in it.

Does it matter that my audio is built into my motherboard?

Thanks,

---

### Post by chongzi889 on 2008-12-08
sluice valve is **[gate valve](http://www.valvesupplier.net/index.htm)** also,as it is sometimes known, is a valve that opens by lifting a round or rectangular gate/wedge out of the path of the fluid. The distinct feature of a [gate valve]("http://www.valvesupplier.net/index.htm") is the sealing surfaces between the gate and seats are planar.

---

### Post by adrian.todireanu on 2008-12-25
Hello!
*First of all:*
=D> Thanks a lot for writing this post!!! Is the only thing that, finally, got my tvtuner working.
*Second:*
:-k Why doesn't it stay like that after a reboot? How can I make it keep these settings? After rebooting I was back to square one ](*,), except for the **stationlist.xml** file (which I edited, by the way, after running [COLOR="DarkGreen"]tvtime-scanner[/COLOR]), and I had to go through the removal of the drivers again :sad:. What should I do to make this permanent??? :?:
*Third:* 
It seems i can only get access to /dev/video0 if I run tvtime using [COLOR="DarkGreen"]sudo[/COLOR] in terminal, otherwise I get a "Permission Denied" message and a blue screen. :???:
Anyone can help me? I tried the HELP section about permissions and authorizations but I'm still lost. Please help!! :cry:

I solved the "Permission Denied" issue, by modifying the permissions for [COLOR="Blue"]/dev/video0[/COLOR] via "[COLOR="DarkRed"]gksudo nautilus[/COLOR]", also with the reading/saving of the config file [COLOR="Blue"]tvtime.xml[/COLOR]. Also found a thread somewhere that told me how to bind the built-in volume control of tvtime to the cd-audio input.=>> [[COLOR="Red"]Here![/COLOR]]("http://ubuntuforums.org/archive/index.php/t-964790.html"). It says there to modify a line in [COLOR="Blue"]tvtime.xml[/COLOR] file but I actually had to add it, cause it wasn't there at all.
As a piece of advice: _save_ your [COLOR="Blue"]stationlist.xml[/COLOR] file to a backup location, after configuring the channels, to avoid having to do it all over again, in the future. All you will have to do after an eventual re-install is to run [COLOR="DarkRed"]tvtime-scanner[/COLOR] just till it finds the first channel and creates this file, then CTRL+C, and overwrite it with the backed-up one. I had to do it yesterday, cause I managed to destroy the partition I had ubuntu installed in. :D
The remaining issue is not having to type the "sudo rmmod ...." every time I restart the system and the remote control usage. But that's worth a new topic, since I couldn't find anything to help me, yet.


29.Dec 19:16
Another one solved: I found this [topic]("http://ubuntuforums.org/showthread.php?t=953785&highlight=sudo+rmmod+tuner&page=2"). It's about a different tuner but I managed to work things out and made this alteration of drivers permanent by adding a line to the [COLOR="Blue"]/etc/modprobe.d/options[/COLOR], (using [COLOR="DarkRed"]sudo gedit /etc/modprobe.d/options[/COLOR]) like this:
[COLOR="Red"]options bttv card=34 tuner=43[/COLOR], releasing me from the trouble of typing the above lines of code, every time I start Ubuntu.

I'm still not able to properly configure [COLOR="Green"]**lirc**[/COLOR] and I'm not going to, cause I think it's weird to add another application to control an already working device (my remote control works _without LIRC_, except a few buttons, among which the up and down channel, which I really would like to have, for comfort reasons.)
So, I'll keep ... digging!!

---

### Post by G00D_GUY on 2009-02-18
OK. Thanks a whole bunch.

I finally got working after learning more about the alsamixer. You nail it.
:D:D:D:D:D:D:D

---

### Post by excbuntu on 2009-02-20
i have the 'expert' version of this card and i just happened to stumble on it. it's installed on my linux box but i have no idea how to activate it. i've never dealt with real hardware issues other then problems with standby/hibernate.

i didn't install any drivers or do anything to this card. all i know is that it is installed on my motherboard. how do i know if i have the wrong drivers installed in the first place? you also mention to add the correct drivers. how do i do that?

---

### Post by binbash on 2009-02-21
I just bought one, and the guide works perfect after tweaking a little.

---

### Post by G00D_GUY on 2009-02-22
I don't know if anyone is still looking at this topic, but I hope so.

Everything was working great, till I plugged in a web cam. If I unplug the web cam and reboot, all is OK. So, I think......Well, I am new, so let me not tell you about my rational, and spare myself some embarrassment. 

Just help me. If possible. ;)

Thanks

---

### Post by excbuntu on 2009-02-22
can i follow this guide just after installing the card on the motherboard and that's it? or do i have to do something else.

and, how do i "add the right drivers?"

---

### Post by G00D_GUY on 2009-02-23
Excbuntu,

        Yes, just install the card and follow the instructions in this topic. Those instructions cover the install of the drivers. I am still new to ubuntu, and even I got it to work ( after re-reading it a few times). And now......:popcorn: (it's movie time).

Still waiting on a reply about the webcam. I think I need to save the settings, so the software (TVtime) will not be tricked by the webcam.?

---

### Post by excbuntu on 2009-02-28
i'm attempting to get the card to work now. after some googling, i found [this]("http://www.linuxhelp.net/guides/tvtuner/") link that has some details regarding the installation of a winfast tv2000 card on linux, including how to fix the remote issue with tvtime. hope this helps.

---

### Post by excbuntu on 2009-02-28
i received the following errors after entering the respective commands:

sudo rmmod bt878
ERROR: Module bt878 does not exist in /proc/modules
sudo rmmod tuner
ERROR: Module tuner does not exist in /proc/modules

EDIT: i guess it didn't matter since rmmod is a command to remove the module from the kernel (man command!) but the "sudo modprobe bttv card=34 tuner=43" worked, but i still get no signal on tvtime.

how do i know that a certain piece of hardware is detected on ubuntu?

---

### Post by excbuntu on 2009-02-28
```
dmesg | grep Winfast
```

gives me the following

```
[   12.440663] cx88[0]: subsystem: 107d:6613, board: Leadtek Winfast 2000XP Expert [card=5,autodetected]
[   12.706653] cx88[0]: Leadtek Winfast 2000XP Expert config: tuner=43, eeprom[0]=0x01
[   12.742546] input: cx88 IR (Leadtek Winfast 2000XP as /devices/pci0000:00/0000:00:1e.0/0000:04:04.0/input/input6
```

so i believe it's being detected properly. tvtime does not show any channels. this is frustrating going to windows just to watch tv!!

---

### Post by AMSlider on 2010-01-28
> **excbuntu said:**
> ```
dmesg | grep Winfast
```

gives me the following

```
[   12.440663] cx88[0]: subsystem: 107d:6613, board: Leadtek Winfast 2000XP Expert [card=5,autodetected]
[   12.706653] cx88[0]: Leadtek Winfast 2000XP Expert config: tuner=43, eeprom[0]=0x01
[   12.742546] input: cx88 IR (Leadtek Winfast 2000XP as /devices/pci0000:00/0000:00:1e.0/0000:04:04.0/input/input6
```

so i believe it's being detected properly. tvtime does not show any channels. this is frustrating going to windows just to watch tv!!

Hey excbuntu, 
I've got the same card, and it used to work fine in previous versions, but in Karmic it didn't work.  Anyways, here's my working setup in Karmic 64bit (shouldn't matter):

Here's my /etc/modprobe.d/leadtek_winfast_2000xp_expert.conf
```

# i2c
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1

# bttv
alias char-major-81 cx8800
alias char-major-81 videodev
alias char-major-81-0 bttv

# Leadtek Winfast 2000XP Expert
options bttv card=5 tuner=43 radio=1 pll=1 adc_crush=0
options cx8800 vbi_debug=0
options cx88xx audio_debug=0 i2c_debug=10
options cx88-blackbird debug=0
options cx23885 debug=0

```

Then I added this to /etc/modules:
```

i2c-i801

# For tele
cx8800
cx88-blackbird
cx23885
cx88_alsa

```

I really didn't need the bttv as some of the other posts suggest.

Then reboot, and my lsmod looks like:

```

$ sudo lsmod | egrep "bt|cx|tuner" | sort
btcx_risc               5672  5 cx88_alsa,cx23885,cx8802,cx8800,cx88xx
cx2341x                15012  1 cx23885
cx23885               113572  0 
cx8800                 36660  0 
cx8802                 17956  0 
cx88_alsa              13192  0 
cx88xx                 86412  3 cx88_alsa,cx8802,cx8800
dvb_core              104528  2 cx23885,videobuf_dvb
i2c_algo_bit            7076  1 cx88xx
ir_common              52740  1 cx88xx
snd                    77096  20 cx88_alsa,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_pcm                93160  5 cx88_alsa,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss
tuner                  24520  2 
tuner_simple           16468  1 
tuner_types            18496  1 tuner_simple
tveeprom               14884  2 cx23885,cx88xx
v4l2_common            21024  5 cx23885,cx2341x,tuner,cx8800,cx88xx
videobuf_core          21188  6 cx23885,videobuf_dvb,cx8802,cx8800,cx88xx,videobuf_dma_sg
videobuf_dma_sg        14436  5 cx88_alsa,cx23885,cx8802,cx8800,cx88xx
videobuf_dvb            8452  1 cx23885
videodev               43360  6 cx23885,tuner,uvcvideo,cx8800,cx88xx,v4l2_common

```

And dmesg looks like:

```

$ dmesg | egrep "bt|cx|tuner"
cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
cx8800 0000:02:05.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
subsystem: 107d:6613, board: Leadtek Winfast 2000XP Expert [card=5,autodetected], frontend(s): 0
cx88[0]: TV tuner type 44, Radio tuner type -1
cx88[0]: Test OK
cx88[0]: i2c register ok
tuner 1-0060: chip found @ 0xc0 (cx88[0])
tuner 1-0043: chip found @ 0x86 (cx88[0])
cx88[0]: Leadtek Winfast 2000XP Expert config: tuner=43, eeprom[0]=0x01
tuner-simple 1-0060: creating new instance
tuner-simple 1-0060: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
input: cx88 IR (Leadtek Winfast 2000XP as /devices/pci0000:00/0000:00:1e.0/0000:02:05.0/input/input8
cx88[0]/0: found at 0000:02:05.0, rev: 5, irq: 22, latency: 20, mmio: 0xfb000000
IRQ 22/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
cx88[0]/0: registered device video1 [v4l2]
cx88[0]/0: registered device vbi0
cx88[0]/0: registered device radio0
cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
cx2388x blackbird driver version 0.0.7 loaded
cx88/2: registering cx8802 driver, type: blackbird access: shared
cx23885 driver version 0.0.2 loaded
cx2388x alsa driver version 0.0.7 loaded

```

Bonus Points:
My webcam was always competing for /dev/video0 or video1 with this card upon boot, so here's the udev rule for this card.  I've placed mine in /etc/udev/rules.d/99-duff.rules. This will make the card appear as /dev/tele. 

```

SUBSYSTEM=="video4linux", ATTRS{subsystem_vendor}=="0x107d", ATTRS{subsystem_device}=="0x6613", NAME="video%n", SYMLINK+="tele"

```

In theory, you can run ```
sudo udevadm trigger --action=change
```, but I had better success using ```
sudo restart udev
```

I have been using tvtime to watch tv, so in /etc/tvtime/tvtime.xml, I set it up to use /dev/tele

```

<option name="V4LDevice" value="/dev/tele"/>

```

My only issue is the FM radio, doesn't work but at least I have TV.  I get static sound, but no stations on gnomeradio.  If anyone has troubleshooting tips, I'd love to hear them.  In dmesg, it shows as radio=-1, so I know that's not "good"...

Cheers!
~AMSlider

---

### Post by sandu.lulu on 2010-03-18
did anyone got the remote to work properly with this card? this is my second week of searching and still no luck. i can't seem to configure (or install) lirc properly..

any help would be really appreciated

---

### Post by load.runner on 2010-03-20
> **excbuntu said:**
> 
```
[   12.742546] input: cx88 IR (Leadtek Winfast 2000XP as /devices/pci0000:00/0000:00:1e.0/0000:04:04.0/input/input6
```


this means that the remote control is working as a standard input device, right?

the remote works with no configuration but there are at least 4 buttons (KEY_PREVIOUS, KEY_NEXT, KEY_FASTFORWARD, KEY_REWIND) that are useful are not working

so my question would be if there is a way to configure how the buttons are mapped

---

### Post by Vlada_bgd on 2010-09-17
Hi, i have Leadtek TV2000xp-rm on my pc, but i can not get it working. I also have genius webcam Eye 312 installed, but upside down picture. Any idea what to do to get tv working?
I have tried:
```
vlada@vlada-desktop:~$ sudo rmmod bt878
[sudo] password for vlada: 
ERROR: Module bt878 does not exist in /proc/modules
vlada@vlada-desktop:~$ sudo rmmod tuner
ERROR: Module tuner does not exist in /proc/modules
vlada@vlada-desktop:~$ sudo rmmod bttv
ERROR: Module bttv does not exist in /proc/modules
vlada@vlada-desktop:~$  sudo modprobe bttv card=34 tuner=43
WARNING: All config files need .conf: /etc/modprobe.d/bttv, it will be ignored in a future release.
FATAL: Error inserting bttv (/lib/modules/2.6.32-24-generic/kernel/drivers/media/video/bt8xx/bttv.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```
Here is grep info:
```
dmesg | grep bttv
[   13.227375] bttv: Unknown symbol ir_codes_pixelview_table
[   13.228486] bttv: Unknown symbol ir_codes_avermedia_dvbt_table
[   13.228563] bttv: Unknown symbol ir_codes_encore_enltv2_table
[   13.228628] bttv: Unknown symbol ir_codes_winfast_table
[   13.228848] bttv: Unknown symbol ir_codes_pctv_sedna_table
[   13.228943] bttv: Unknown symbol ir_rc5_timer_keyup
[   13.229278] bttv: Unknown symbol ir_codes_apac_viewcomp_table
[   13.229337] bttv: Unknown symbol ir_extract_bits
[   13.229494] bttv: Unknown symbol ir_rc5_timer_end
[   13.230668] bttv: Unknown symbol ir_input_init
[   13.231364] bttv: Unknown symbol ir_input_nokey
[   13.231663] bttv: Unknown symbol ir_codes_avermedia_table
[   13.231722] bttv: Unknown symbol ir_codes_nebula_table
[   13.232293] bttv: Unknown symbol ir_input_keydown
[ 3834.221569] bttv: Unknown symbol ir_codes_pixelview_table
[ 3834.222723] bttv: Unknown symbol ir_codes_avermedia_dvbt_table
[ 3834.222786] bttv: Unknown symbol ir_codes_encore_enltv2_table
[ 3834.222854] bttv: Unknown symbol ir_codes_winfast_table
[ 3834.223084] bttv: Unknown symbol ir_codes_pctv_sedna_table
[ 3834.223183] bttv: Unknown symbol ir_rc5_timer_keyup
[ 3834.223536] bttv: Unknown symbol ir_codes_apac_viewcomp_table
[ 3834.223598] bttv: Unknown symbol ir_extract_bits
[ 3834.223763] bttv: Unknown symbol ir_rc5_timer_end
[ 3834.224289] bttv: Unknown symbol ir_input_init
[ 3834.225012] bttv: Unknown symbol ir_input_nokey
[ 3834.225321] bttv: Unknown symbol ir_codes_avermedia_table
[ 3834.225384] bttv: Unknown symbol ir_codes_nebula_table
[ 3834.225989] bttv: Unknown symbol ir_input_keydown
```

---

### Post by CGfrantic on 2011-01-31
Hello

The solution for this problem can be found on this [linuxtv site]("http://linuxtv.org/wiki/index.php/Xceive_XC3028/XC2028")


```

# In order to use, you need to:
#       1) Download the windows driver with something like:
#               wget [http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip]("http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip")
#               ( find here: [http://cdn.pinnaclesys.com/SupportFiles/PCTV%20Drivers/ReadmePCTV.htm]("http://cdn.pinnaclesys.com/SupportFiles/PCTV%20Drivers/ReadmePCTV.htm") )
#       2) Extract the file hcw85bda.sys from the zip into the current dir:
#               unzip -j HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip Driver85/hcw85bda.sys
#       3) Download the extract script
#               wget [http://linuxtv.org/hg/v4l-dvb/raw-file/3919b17dc88e/linux/Documentation/video4linux/extract_xc3028.pl]("http://linuxtv.org/hg/v4l-dvb/raw-file/3919b17dc88e/linux/Documentation/video4linux/extract_xc3028.pl")
#       3) run the script:
#               perl extract_xc3028.pl
#       4) copy the generated file:
#               sudo cp xc3028-v27.fw /lib/firmware

```

Or,if this seems to complicated for you ,just get this  [ firmware]("http://db.tt/lvVuV17") and copy it to ***lib/firmware/***.

You will have to do this as a root.

```
gksudo nautilus
```
or 
```
sudo nautilus
```

As I recently switched from Linux Mint 9 to the Ubuntu 10.10 all that I needed to do is just to put the firmware to its place and everything worked, well, almost everything because there was no sound.

In order to get sound, it is necessary to connect this card to to the line-in port which has been muted,so the easiest way to solve this is installation of alsa mixer and volume up line-in signal.

```
sudo apt-get install gnome-alsamixer
```

And that was it, best of all is that even though the remote does not work fully, it is possible to control the volume of the system, as well as video and audio players, and shut down or restart system.

For watching TV I will suggest [xawtv]("http://linux.bytesex.org/xawtv/") or [zapping]("http://zapping.sourceforge.net/Zapping/index.html")

---

### Post by DalaiDakkar on 2011-02-02
Hi everyone hope somebody can help me with this

I have a winfast 2000 tv tuner, which lspci detects as: 

02:01.0 Multimedia video controller: Brooktree Corporation Device 036a (rev 11)
02:01.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

but when I look into /dev/ there isn't neither /dev/video  /dev/video0  or /dev/radio

I already tried with modprobe bttv and nothing comes up, any help would be appreciated!

Regards
Tony

---

