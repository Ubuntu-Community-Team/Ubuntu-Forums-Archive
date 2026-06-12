---
title: "Sound problems... so frustrated!"
date: 2012-10-04
forum: New to Ubuntu
---

### Post by Wolfram23 on 2012-10-04
Hi guys, newbie in need of help here. 

Ok, so I set up my little HTPC with Ubuntu 12.04. Everything worked great for a while. I could watch movies with surround sound in VLC for example.

Then I decided I want to try XBMC.

Getting the sound to work in that was a pain. My PC currently has an MSI G210 GPU using HDMI output to my Onkyo TX-SA705 receiver which has DTS and DD decoders. 

I was testing with an mkv file, 1080p with DTS.

In the options I set passthrough on and tried a huge variety of options without success. I then started searching and found guides telling me to install ALSA, so I did. 

At best, I was able to get a very loud static sound through the speakers when set to 5.1 with passthrough on, otherwise there was no sound. 2.0 worked though (don't remember if that was with passthrough off as well, though). I also installed the pulse audio mixer pavucontrol and set the passthrough options on there as well.

Ok, so then I was reading about removing PulseAudio altogether. Figured I'd give that a try. I followed a guide and removed it, then installed the alsa files it told me to as well as gnome-alsamixer. 

After a reboot, no sound. No sound icon up by the time in desktop, but also when I go to my default sound options (System Settings>Sound), no sound device comes up anymore. Additionally, gnome-alsamixer is empty (it shows a tab with "Nvidia GPU 0b HDMI/DP" and then a blank box, and on the bottom are 4 identical checkboxes showing "IEC958").

Additional info:
I'm trying stuff from these sources without success (and more than a little confusion):
[http://wiki.xbmc.org/index.php?title=HOW-TO:Setup_HDMI_audio_on_GeForce_GT210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO:Setup_HDMI_audio_on_GeForce_GT210,_GT220,_or_GT240)
[http://howto.blbosti.com/2010/04/ubuntu-make-alsa-default-instead-of-pulseaudio/](http://howto.blbosti.com/2010/04/ubuntu-make-alsa-default-instead-of-pulseaudio/)
[http://askubuntu.com/questions/130809/sound-not-working-after-12-04-install](http://askubuntu.com/questions/130809/sound-not-working-after-12-04-install)

Finally one more thing that is probably important. When I run a sudo apt-get update I get these errors:

W: Failed to fetch [http://ppa.launchpad.net/team-iquik/alsa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/team-iquik/alsa/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-iquik/alsa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/team-iquik/alsa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

I've tried to revert back to pusleaudio but no success with that either. So I'm stuck with a useless HTPC at this time.

Please help :(

(EDIT: Just going through this guide, will report back:
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) )

---

### Post by Wolfram23 on 2012-10-04
An update to the outputs of what I'm told to run in the troubleshooting guide because I can't really tell what I'm seeing here. First of all, I can now see my devices in the sound menus, but still can't get sound output and still no sound icon on the desktop bar near the clock.

wget -O alsa-info.sh [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) && chmod +x ./alsa-info.sh && ./alsa-info.sh```

--2012-10-04 21:08:20--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org (www.alsa-project.org)... 77.48.224.243
Connecting to www.alsa-project.org (www.alsa-project.org)|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;hb=refs/heads/build;f=alsa/utils/alsa-info.sh [following]
--2012-10-04 21:08:21--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;hb=refs/heads/build;f=alsa/utils/alsa-info.sh
Resolving git.alsa-project.org (git.alsa-project.org)... 77.48.224.243
Connecting to git.alsa-project.org (git.alsa-project.org)|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/x-sh]
Saving to: `alsa-info.sh'

    [  <=>                                  ] 27,785       114K/s   in 0.2s    

2012-10-04 21:08:22 (114 KB/s) - `alsa-info.sh' saved [27785]

ALSA Information Script v 0.4.61
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See './alsa-info.sh --help' for command line options.

```bash alsa-info.sh --stdout

```
Simple mixer control 'IEC958',2
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',3
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!--------------

--startcollapse--
state.NVidia {
    control.1 {
        iface CARD
        name 'HDMI/DP,pcm=3 Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.2 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.3 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.4 {
        iface MIXER
        name 'IEC958 Playback Default'
        value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.5 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.6 {
        iface PCM
        device 3
        name ELD
        value ''
        comment {
            access read
            type BYTES
            count 0
        }
    }
    control.7 {
        iface CARD
        name 'HDMI/DP,pcm=7 Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.8 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        index 1
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.9 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        index 1
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.10 {
        iface MIXER
        name 'IEC958 Playback Default'
        index 1
        value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write locked'
            type IEC958
            count 1
        }
    }
    control.11 {
        iface MIXER
        name 'IEC958 Playback Switch'
        index 1
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.12 {
        iface PCM
        device 7
        name ELD
        value '10000e006d80004f00000200000000003dcb710754582d53523730350a20202020097f070f7f071707503f06c05706005f7e01675e004d02000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type BYTES
            count 95
        }
    }
    control.13 {
        iface CARD
        name 'HDMI/DP,pcm=8 Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.14 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        index 2
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.15 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        index 2
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.16 {
        iface MIXER
        name 'IEC958 Playback Default'
        index 2
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.17 {
        iface MIXER
        name 'IEC958 Playback Switch'
        index 2
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.18 {
        iface PCM
        device 8
        name ELD
        value ''
        comment {
            access read
            type BYTES
            count 0
        }
    }
    control.19 {
        iface CARD
        name 'HDMI/DP,pcm=9 Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.20 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        index 3
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.21 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        index 3
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.22 {
        iface MIXER
        name 'IEC958 Playback Default'
        index 3
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.23 {
        iface MIXER
        name 'IEC958 Playback Switch'
        index 3
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.24 {
        iface PCM
        device 9
        name ELD
        value ''
        comment {
            access read
            type BYTES
            count 0
        }
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
joydev
bnep
rfcomm
bluetooth
parport_pc
ppdev
binfmt_misc
vesafb
snd_hda_codec_hdmi
k8temp
snd_hda_intel
snd_hda_codec
serio_raw
hid_logitech_dj
lp
mac_hid
nvidia
i2c_nforce2
snd_hwdep
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
snd
soundcore
snd_page_alloc
parport
usbhid
hid
sata_nv
forcedeth


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D1/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC0D1/driver_pin_configs:

/sys/class/sound/hwC0D1/user_pin_configs:

/sys/class/sound/hwC0D1/init_verbs:

/sys/class/sound/hwC0D2/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC0D2/driver_pin_configs:

/sys/class/sound/hwC0D2/user_pin_configs:

/sys/class/sound/hwC0D2/init_verbs:

/sys/class/sound/hwC0D3/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC0D3/driver_pin_configs:

/sys/class/sound/hwC0D3/user_pin_configs:

/sys/class/sound/hwC0D3/init_verbs:


!!ALSA/HDA dmesg
!!--------------

[    6.157610] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[    6.157618] snd_hda_intel 0000:02:00.1: PCI INT B -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
[    6.157622] hda_intel: Disabling MSI
[    6.157665] snd_hda_intel 0000:02:00.1: setting latency timer to 64
[    6.164780] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
--
[    6.792656] EXT3-fs (sda2): using internal journal
[    6.972026] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
[    6.996034] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
[    7.020019] HDMI status: Codec=2 Pin=5 Presence_Detect=0 ELD_Valid=0
[    7.044080] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[    7.044269] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:09.0/0000:02:00.1/sound/card0/input2
[    7.044367] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:09.0/0000:02:00.1/sound/card0/input3
[    7.044443] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:09.0/0000:02:00.1/sound/card0/input4
[    7.044512] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:09.0/0000:02:00.1/sound/card0/input5
[    7.598843] vesafb: mode is 640x480x32, linelength=2560, pages=0
--
[   11.567689] init: gdm main process (972) killed by TERM signal
[   14.934861] HDMI hot plug event: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=0
[   14.940048] HDMI status: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=0
[   14.956451] HDMI hot plug event: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=1
[   14.965317] HDMI status: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=1
[   15.553932] init: plymouth-stop pre-start process (1325) terminated with status 1
[   15.732066] HDMI: detected monitor TX-SR705
[   15.732067]      at connection type HDMI
[   15.732072] HDMI: available speakers: FL/FR LFE FC RL/RR RLC/RRC
[   15.732077] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000 88200 96000 176400 192000, bits = 16 20 24
[   15.732081] HDMI: supports coding type LPCM: channels = 8, rates = 32000 44100 48000 88200 96000 176400 192000, bits = 16 20 24
[   15.732085] HDMI: supports coding type AC-3: channels = 8, rates = 32000 44100 48000, max bitrate = 640000
[   15.732088] HDMI: supports coding type DTS: channels = 8, rates = 44100 48000, max bitrate = 1536000
[   15.732091] HDMI: supports coding type E-AC-3/DD+ (Dolby Digital Plus): channels = 8, rates = 44100 48000
[   15.732094] HDMI: supports coding type DTS-HD: channels = 8, rates = 44100 48000 88200 96000 176400 192000
[   15.732097] HDMI: supports coding type MLP (Dolby TrueHD): channels = 8, rates = 44100 48000 88200 96000 192000
[   15.732100] HDMI: supports coding type DSD (One Bit Audio): channels = 6, rates = 44100
[   18.501987] HDMI hot plug event: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=0
[   18.508029] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
[   18.508038] HDMI hot plug event: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=0
[   18.516035] HDMI status: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=0
[   18.523146] HDMI hot plug event: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=1
[   18.528016] HDMI status: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=1
[   19.300028] HDMI: detected monitor TX-SR705
[   19.300031]      at connection type HDMI
[   19.300035] HDMI: available speakers: FL/FR LFE FC RL/RR RLC/RRC
[   19.300040] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000 88200 96000 176400 192000, bits = 16 20 24
[   19.300045] HDMI: supports coding type LPCM: channels = 8, rates = 32000 44100 48000 88200 96000 176400 192000, bits = 16 20 24
[   19.300048] HDMI: supports coding type AC-3: channels = 8, rates = 32000 44100 48000, max bitrate = 640000
[   19.300051] HDMI: supports coding type DTS: channels = 8, rates = 44100 48000, max bitrate = 1536000
[   19.300054] HDMI: supports coding type E-AC-3/DD+ (Dolby Digital Plus): channels = 8, rates = 44100 48000
[   19.300057] HDMI: supports coding type DTS-HD: channels = 8, rates = 44100 48000 88200 96000 176400 192000
[   19.300061] HDMI: supports coding type MLP (Dolby TrueHD): channels = 8, rates = 44100 48000 88200 96000 192000
[   19.300063] HDMI: supports coding type DSD (One Bit Audio): channels = 6, rates = 44100
[   21.242925] HDMI hot plug event: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=0
[   21.276019] HDMI status: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=0
[   21.276026] HDMI hot plug event: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=0
[   21.284018] HDMI status: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=0
[   21.324426] HDMI hot plug event: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=1
[   21.332030] HDMI status: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=1
[   22.100021] HDMI: detected monitor TX-SR705
[   22.100024]      at connection type HDMI
[   22.100028] HDMI: available speakers: FL/FR LFE FC RL/RR RLC/RRC
[   22.100034] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000 88200 96000 176400 192000, bits = 16 20 24
[   22.100038] HDMI: supports coding type LPCM: channels = 8, rates = 32000 44100 48000 88200 96000 176400 192000, bits = 16 20 24
[   22.100042] HDMI: supports coding type AC-3: channels = 8, rates = 32000 44100 48000, max bitrate = 640000
[   22.100045] HDMI: supports coding type DTS: channels = 8, rates = 44100 48000, max bitrate = 1536000
[   22.100047] HDMI: supports coding type E-AC-3/DD+ (Dolby Digital Plus): channels = 8, rates = 44100 48000
[   22.100051] HDMI: supports coding type DTS-HD: channels = 8, rates = 44100 48000 88200 96000 176400 192000
[   22.100054] HDMI: supports coding type MLP (Dolby TrueHD): channels = 8, rates = 44100 48000 88200 96000 192000
[   22.100057] HDMI: supports coding type DSD (One Bit Audio): channels = 6, rates = 44100
[   22.368017] eth0: no IPv6 routers present

```

---

### Post by pqwoerituytrueiwoq on 2012-10-04
this command(s) will print some commands, run each till you find out which one makes sound come from your speakers then post the command that made sound here
```
aplay -l | grep card | sed 's/://g' | awk '{print "speaker-test -Dplughw:"$2","$7" -c2"}'

```

---

### Post by Wolfram23 on 2012-10-04
Unfortunately nothing happened. Before all this stuff happened the default sound test for 5.1 worked and the channels were right.

But yeah, just ran that code and nothing happens. This is the output:
speaker-test -Dplughw:0,3 -c2
speaker-test -Dplughw:0,7 -c2
speaker-test -Dplughw:0,8 -c2
speaker-test -Dplughw:0,9 -c2

---

### Post by pqwoerituytrueiwoq on 2012-10-04
did you run each of the 4 commands it printed? or did none work?
edit:
rm -rf ~/.pulse
logout and login if you don't have sound edit your sound settings accordantly

---

### Post by Wolfram23 on 2012-10-05
Sorry, I didn't understand that output before was what I was supposed to run!

I got stereo static sounds running hw:0,7 :D

not sure what you just told me to do but I'll type it into terminal and see what happens.

EDIT: Ok so I don't know if I did it right but according to the XBMC wiki instructions, I added a file called /etc/asound.conf with the following code (using nano):
pcm.!default {    type plug    slave {        pcm "hw:0,7"        rate 48000    } }

Was that right?

---

### Post by pqwoerituytrueiwoq on 2012-10-05
make sure it is not muted in **alsamixer** before doing this, it may not be needed (notice the F6 key)

if you still don't have sound working, this will create a new sound device
[FONT=Courier New]sudo sh -c "echo 'load-module module-alsa-sink device=hw:0,7' >> /etc/pulse/default.pa"[/FONT]
to readers look where the 0,7 came from then this will make sense to you

if some apps dont play sound (looking at you adobe flash)
[FONT=Courier New]gksu gedit /etc/asound.conf[/FONT]
```
pcm.pulse {
type pulse
}
ctl.pulse {
type pulse
}
pcm.!default {
type pulse
}
ctl.!default {
type pulse
}
```reboot or at least a logout will be needed

---

### Post by Wolfram23 on 2012-10-05
Thanks for all the help so far.

In Alsamixer I can't do anything. The device chosen is Nvidia HDA. Other options are default and custom. On the bottom of the screen there's  S/PDIF 0 through 3 with 00 listed. I've tried using the arrow keys and +/- but they can't be chanted. I can mute them with M, though, so I left them at 00.

Then I tried running your code and got an error:
sh: 1: load-module: not found

I did make the sound.conf, though.

EDIT: something of note. When I open Pavuconrol and select one of the HDMI outputs under the Configure tab, presumeably it corresponds to hw:0,7, my receiver changes to multichannel input. As soon as I close pavucontrol, it disappears like it's not getting sound again. Additionally, this does not happen in alsamixer at all.

---

### Post by pqwoerituytrueiwoq on 2012-10-05
fixed the command
[FONT=Courier New]sudo sh -c "echo 'load-module module-alsa-sink device=hw:0,7' >> /etc/pulse/default.pa"[/FONT]
if your sound device is in pavucontrol the above should not help
that trick is for when the device is not in there

---

### Post by Wolfram23 on 2012-10-05
Ok, so my device is coming up as it should. And everything "looks" the same as it did before I removed pulseaudio - I even got the sound applet back up. But no sound. When I'm in the pavucontrol, my receiver does temporarily receive the sound signal as noted by it clicking and showing "Multichannel" but once I close the program, it goes away. Also, in the default sound management window, if I switch to stereo my receiver will change to ProLogic IIx, and then if I go back to Digital Surround 5.1, it shows Multichannel but only for about 2 seconds again before going back to no audio input.

Seems like Ubuntu just can't save the setting.

---

### Post by pqwoerituytrueiwoq on 2012-10-05
rm -rf ~/.pulse
logout and login
make sure alsa is running

---

### Post by Wolfram23 on 2012-10-05
Thanks for all the help.

The sound is generally working again, but the speaker test in the Settings window don't work for whatever reason, and still no luck on XBMC. I'll look into those things, but for now just want to say thanks a lot for the help!

EDIT: This might not be the best place for it but I do really need help getting XBMC to work. I've tried all the passthrough settings and right now the only two things have maybe sort of worked. First, setting to pulseaudio defaults makes a very loud white noise come through. The second one is going with Custom and setting "hdmi:CARD=NVidia" which doesn't allow sound, but at least I don't get the error on screen about not being able to setup the audio device or something.

Additionally, gnome-alsamixer doesn't give me any options. It's just a blank box and on the bottom it shows 4 checkboxes for iec985, but there's no volume settings or anything like that which should apparently be there.

A final note, in terminal I get these errors from xbmc:

```
Running DIL (3.22.0) Version
DtsDeviceOpen: Opening HW in mode 0
DtsDeviceOpen: Create File Failed
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.HDA-Intel.pcm.hdmi.7:CARD=NVidia,AES0=6,AES1=130,AES2=0,AES3=2'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM hdmi:CARD=NVidia,DEV=7,AES0=0x6,AES1=0x82,AES2=0x0,AES3=0x2
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.HDA-Intel.pcm.hdmi.7:CARD=NVidia,AES0=4,AES1=130,AES2=0,AES3=2'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM hdmi:CARD=NVidia,DEV=7
ALSA lib pcm_pulse.c:750:(pulse_prepare) PulseAudio: Unable to create stream: Device or resource busy

ALSA lib pcm_pulse.c:750:(pulse_prepare) PulseAudio: Unable to create stream: Device or resource busy

ALSA lib pcm_pulse.c:750:(pulse_prepare) PulseAudio: Unable to create stream: Device or resource busy

ALSA lib pcm_pulse.c:750:(pulse_prepare) PulseAudio: Unable to create stream: Device or resource busy

ALSA lib pcm_pulse.c:750:(pulse_prepare) PulseAudio: Unable to create stream: Device or resource busy

ALSA lib pcm_pulse.c:750:(pulse_prepare) PulseAudio: Unable to create stream: Device or resource busy


```

EDIT: Another small update. Some sounds do work, for example I can listen to internet radio over Rythmbox. I then tried booting up some movies with VLC and they are not working; my receiver just incessantly goes *click, click, click* as it switches input/outputs looking for a source. Additionally, running aplay /urs/share/sounds/alsa/Front_Center.wave does not create a sound output and I do hear my receiver click like it is receiving a signal.

---

### Post by Wolfram23 on 2012-10-06
I went ahead and reinstalled Ubuntu, start from scratch. Generally, so far so good, but still a problem with audio passthrough. I tried loading a movie up in the default movie player included with Ubuntu, and when I enable the passthrough option it simply gives me a static sound over the speakers. Same thing that happens in XBMC. There must be something I'm missing.

Also, a lot of the guides suggest installing a ppa from team-iquik/alsa, but that doesn't work on 12.04.

Any suggestions?

---

### Post by JohnnyC35 on 2013-03-26
not sure if you're still following this thread or not but I also had this issue of static during playback, specifically of mkv files. after various troubleshooting of 'the system' I looked again at the software, XBMC.  Under System> System> Audio Output> I was able to remove the static by changing the Speaker Configuration to 2.0 not 2.1. Also, I disabled the various 'capable reciever's ... AC3, DTS, AAC, LPCM, and TrueHD. After that I was able to play my mkv videos without issue. I hope that helps some

---

