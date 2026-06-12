---
title: "No sound! Tried everything..."
date: 2008-06-24
forum: New to Ubuntu
---

### Post by apartfromthedirt on 2008-06-24
I've been trying to get my sound working, since I installed 8.04 Hardy the other day. Running Intel(R)Pentium(R)4 CPU 2.40GHZ with Audigy[Audigy 1 [SB0090]] snd-emu10k1 sound card. Think the driver isn't installed, because the system can find the sound card but no sound from any apt or even from login. I've tried quite a few threads from the different forums and from the alsa webpage. Can anyone help? Can't function without sound for much longer....

---

### Post by JMGM123456 on 2008-06-24
I know this is gonna sound silly but try turning your speakers volume on full then play some music

---

### Post by apartfromthedirt on 2008-06-24
volume up all the way, still nada

---

### Post by bobnutfield on 2008-06-24
Open a terminal and type:

> sudo alsaconf

follow the instructions and see if it finds the driver and card OK.  If it does, type in the terminal:

> alsamixer

and make sure the master speaker is unmuted.

Bob

---

### Post by apartfromthedirt on 2008-06-24
following error:

sudo: alsaconf: command not found

---

### Post by apartfromthedirt on 2008-06-24
aplay -l renders this:

**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy [Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by webofunni on 2008-06-24
Hello,

  You need to install alsa-utils to get alsaconf. 

```
apt-get install alsa-utils
```

---

### Post by bobnutfield on 2008-06-24
Also open a terminal and type:

> sudo lsmod

look for the sound modules to be sure they are loaded.

---

### Post by apartfromthedirt on 2008-06-24
Error:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by Nepherte on 2008-06-24
```
sudo apt-get install alsa-utils
```

---

### Post by apartfromthedirt on 2008-06-24
sudo lsmod came back with this:

Module                  Size  Used by
ipv6                  267780  8 
af_packet              23812  2 
radeon                124192  2 
drm                    82452  3 radeon
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_ondemand        9740  0 
cpufreq_userspace       5284  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
sbs                    15112  0 
video                  19856  0 
output                  4736  1 video
container               5632  0 
sbshc                   7680  1 sbs
dock                   11280  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
snd_sb16               16360  0 
snd_opl3_lib           12928  1 snd_sb16
snd_sb16_dsp           12032  1 snd_sb16
snd_sb16_csp           20480  1 snd_sb16
snd_sb_common          18048  3 snd_sb16,snd_sb16_dsp,snd_sb16_csp
snd_mpu401_uart         9728  1 snd_sb16
sbp2                   24072  0 
lp                     12324  0 
snd_emu10k1_synth       8064  0 
snd_emux_synth         36224  1 snd_emu10k1_synth
snd_seq_virmidi         8192  1 snd_emux_synth
snd_seq_midi_emul       7552  1 snd_emux_synth
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
snd_emu10k1           146880  4 snd_emu10k1_synth
snd_ac97_codec        101028  1 snd_emu10k1
analog                 13600  0 
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
pcspkr                  4224  0 
evdev                  13056  3 
snd_pcm                78596  5 snd_sb16,snd_sb16_dsp,snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_emu10k1,snd_pcm
snd_util_mem            5632  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10500  4 snd_opl3_lib,snd_sb16_csp,snd_emux_synth,snd_emu10k1
snd_seq_dummy           4868  0 
usblp                  15872  0 
i2c_viapro              9876  0 
i2c_core               24832  1 i2c_viapro
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  4 snd_mpu401_uart,snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8320  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                54224  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  4 snd_opl3_lib,snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9612  9 snd_opl3_lib,snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
emu10k1_gp              4608  0 
snd                    56996  26 snd_sb16,snd_opl3_lib,snd_sb16_dsp,snd_sb16_csp,snd_sb_common,snd_mpu401_uart,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
gameport               16008  3 analog,emu10k1_gp
soundcore               8800  1 snd
button                  9232  0 
via_agp                11136  1 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
agpgart                34760  2 drm,via_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
usbhid                 31872  0 
hid                    38784  1 usbhid
sata_via               12420  0 
pata_via               13316  2 
ata_generic             8324  0 
8139cp                 24704  0 
floppy                 59588  0 
pata_acpi               8320  0 
via_rhine              26632  0 
ohci1394               33584  0 
uhci_hcd               27024  0 
libata                159344  4 sata_via,pata_via,ata_generic,pata_acpi
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
8139too                27520  0 
mii                     6400  3 8139cp,via_rhine,8139too
ieee1394               93752  2 sbp2,ohci1394
ehci_hcd               37900  0 
ohci_hcd               25348  0 
usbcore               146028  6 usblp,usbhid,uhci_hcd,ehci_hcd,ohci_hcd
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3

---

### Post by apartfromthedirt on 2008-06-24
alsa-utils came back with this:

alsa-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by satauros on 2008-06-24
Are you installed through windows or straight from LiveCD

---

### Post by apartfromthedirt on 2008-06-24
LiveCD

---

### Post by satauros on 2008-06-24
you might want to try installing ubuntu through windows. it fixed all of my friend's sound problems for some reason...

---

### Post by webofunni on 2008-06-24
Yes, you need to add sudo to get root privilege :-) . Forgot to mension in the previous post.

---

### Post by apartfromthedirt on 2008-06-24
I know this sounds kinda sad, but I really don't think I can go back to windows. Any suggestions or workarounds for getting snd-emu10k1 creative labs Audigy 1 sound cards?

---

### Post by apartfromthedirt on 2008-06-24
Okay, got that installed, alsa-utils came back with this:

alsa-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

What now?

---

### Post by 3ain_2eyy on 2008-06-24
3ain 3ain 3ain 2eyyyyyyyyyyy JMGM123456 is 2eyy
he is 3ain 3aiin and 3ain for ever
you should go to command line and type: sound_d

for more info contact me: 3ain (underscore) 2eyy (at) freemail (dot) com
NO SPAM EVERY BODY :d

---

### Post by apartfromthedirt on 2008-06-24
Sorry still getting my head around all of this, command line? is that typed in a shell or somewhere else?

---

### Post by 3ain_2eyy on 2008-06-24
please keep it clean bala msabbet...
keep it together and try to keep and staying aliiiiiiiiiiiiiiiiiiiiiive
3ain! 3ain 3ain 3ain3 ain3 ia! 3ain 3ian3 ain 2eyyyyyyyy 3i3 i3 i3 3iiiiiiiiiiiiiiii
tip of the day:
[http://www.google.com](http://www.google.com)

---

### Post by apartfromthedirt on 2008-06-24
Tried 
# cat /usr/lib/openoffice/share/gallery/sounds/train.wav > /dev/dsp#

to see if I could hear anything- nope. Does anyone have a solution for getting snd-emu10k1 to work?

---

### Post by satauros on 2008-06-24
maybe this helps 
[https://bugs.launchpad.net/ubuntu/+bug/25632](https://bugs.launchpad.net/ubuntu/+bug/25632)

---

### Post by webofunni on 2008-06-24
Hello,

  Are you getting anything from "speaker-test" command.

---

### Post by apartfromthedirt on 2008-06-24
no, ran for a while, then nothing

---

### Post by webofunni on 2008-06-24
Can you please post the out put of that command.

---

### Post by apartfromthedirt on 2008-06-24
I should clearify, the test ran for awhile without any sound, this is really annoying. I've installed Hardy 8.04 off the LiveCD on my old Dell laptop, and not a problem with the sound or anything.

---

### Post by Corrupt3d on 2008-06-24
I had the same problem yesterday when I intsalled Hardy on a Desktop,
If you haven't already, try this:

Double click your sound icon, 
A windows called 'Volume Control' will pop up,
Go to Edit>preferences, 
Another window will pop-up (navigate towards the bottom) 
Make sure that 'External Amplifier is checked,
Now you should see a Switches Pane in the first window, 
click on it and disable External Amplifier.

Retry sound test and it should work.

---

### Post by Bright Hammer on 2008-06-24
[IMG]http://linux.dsplabs.com.au/files/p31-audio/screenshot-volume-control-nvidia-ck804-alsa-mixer.png[/IMG]

I don’t know if this will help but it worked for me with another card.

Right click on the sound icon in the menubar you should get a screen like the pic above. Got to edit properties and on your sound device look for front speaker and select it and make sure it is all the way up.

---

### Post by Tea4all on 2008-06-24
Go to System, Preferences, Sound. Try setting the three "sound playback"s from "autodetect", to "PulseAudio". Then press test.

---

### Post by apartfromthedirt on 2008-06-24
When I do, this is the warning error that I get: 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Failed to connect: Connection refused

This is truly killing me, no sound and the total lock-up/freezing that requires a reboot everytime... what must a man do to get an OS that works?!?

---

### Post by Bright Hammer on 2008-06-24
Try here.

[http://ge.ubuntuforums.com/showthread.php?t=787082](http://ge.ubuntuforums.com/showthread.php?t=787082)



Don't blame Ubuntu. Blame creative for not supporting Linux. Call them ask for some Linux drivers , if more people did that they would support it.

---

### Post by webofunni on 2008-06-24
Ty this :

Goto System->Preferences->Sound and set everything to autodetect.

Run:

```
1) sudo /etc/init.d/alsa-utils restart
2) sudo chmod 666 /dev/snd/*
```

Then go back to System->Preferences->Sound and hit TEST. You should hear a beep.

Hope this helps.

---

### Post by skymedic on 2008-06-24
I've just made the (happy) transition from XP to Ubunto. Had some problems with my sound card as well. running ASUS m2n-mx MB with onboard AnalogDevices audio chip. I know this is not the same chipset as you guys have battled with, but try this:
1. forget about trying to download and install alsa drivers from their site.
2. go to the repository and get the GNOME ALSA mixer.
3. install, and all changes. When you dbl click on the volume tab, now you can go in and modify all options.

You might have to fiddle around a bit, but it worked for me!

Good luck!

---

### Post by kansasnoob on 2008-06-24
Try installing gnome-alsamixer from synaptic. It'll then show up in "Sound and Video". Pay special attention to the three toggles furthest to the left and the four furthest to the right!

---

### Post by apartfromthedirt on 2008-06-27
Thanx everyone for all the advice, tried a numerous amount of different combinations, and in the end within sound preferences after trying out different settings, OSS worked finally. Thanx for all the help!!

---

