---
title: "[SOLVED] I've lost sound after upgrade.. help"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by ecs_pf5 on 2008-04-24
[solved]







My install of Kubuntu prior to this was as per my sig.

I decided to click the green 'update' ball on the taskbar, and 163 updates later all seemed okay.

So then I decided to accept the distribution upgrade. It seemed to proceed okay, however I now have problems with sound. I've worked part-way through some fault-finding but am now at a loss as to how to proceed.

I can hear very faint sound when using the 'test' button but it's seriously quiet. Sound on a youtube video via firefox is minutely audible & heavily distorted.

Here is my fault-finding, any ideas gratefully received :confused:


```

root@kubuntu:/home/user# aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


root@kubuntu:/home/user# lspci -v
[truncated]
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at ffaf8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Unknown type IRQ 0


alsamixer ---------> everything up high


check the wire --------> wire's ok, amp is functioning, hear static through speakers


try a power-off reboot: no luck


checked kernel version on the way in (looked at grub): ubuntu 8.04, kernel 2.6.24-16-generic


user@kubuntu:~$ sudo modprobe snd- [tab]
Display all 115 possibilities? (y or n)
[truncated - list contained amongst others:]
snd-seq-oss
snd-pcm-oss
snd-intel8x0
snd-intel8x0m
snd-mixer-oss


okay it's an intel ICH7 chipset
listed at alsa project: http://www.alsa-project.org/main/index.php/Matrix: Module-intel8x0
(looks like we want snd-intel8x0 ) - yup it's in the modprobe snd- list :)


user@kubuntu:~$ sudo modprobe snd-intel8x0
[sudo] password for user:
user@kubuntu:~$


check for soundcore module as mentioned at intel/alsa page:
user@kubuntu:~$ modinfo soundcore
filename:       /lib/modules/2.6.24-16-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     548AA54AF08207316C104F8
depends:
vermagic:       2.6.24-16-generic SMP mod_unload


tried:
user@kubuntu:~$ sudo modprobe snd-intel8x0
user@kubuntu:~$ sudo modprobe snd-pcm-oss
user@kubuntu:~$ sudo modprobe snd-mixer-oss
user@kubuntu:~$ sudo modprobe snd-seq-oss


looked for an .asoundrc file in /home and / -------> not found.


edited boot-time file:
-------------------------------------------------------------------------------
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rtc
sbp2
fuse
snd-intel8x0
--------------------------------------------------------------------------------


power-off reboot:
ok noticed now, we are getting very very quiet, very heavily distorted sound if the speakers are whacked full up.


try rebooting into XP (it's a dualboot machine) & see if sound is ok in there (could it be the amp):
nope, sound is a-ok in XP


There's an snd-intel8x0m in the list up there. Should we be using that?


Tried 
user@kubuntu:~$ sudo modprobe snd-intel8x0m

didn't seem to make a difference. But then, changed 
'Sound System - System Settings'
Hardware tab - audio device
to 'threaded open sound system'
this caused an increase in volume - but still very quiet (massive amp, volume knob set to 3/4, still only a murmur)


Tried selecting 'network sound system' on a whim & played a youtube video
Started getting crashes from artsd:

(no debugging symbols found) - many instances
[Thread debugging using libthread_db enabled]
[New Thread 0x7fa53d264780 (LWP 8628)]
(no debugging symbols found) - many instances
(no debugging symbols found)user@kubuntu:~$ sudo modprobe snd-intel8x0
(no debugging symbols found) - many instances
[KCrash handler]
#3  0x00007fa53bd9e080 in strlen () from /lib/libc.so.6
#4  0x00007fa53cace635 in Arts::AudioIONAS::open ()
   from /usr/lib/libartsflow.so.1
#5  0x00007fa53cac8601 in Arts::AudioSubSystem::open ()
   from /usr/lib/libartsflow.so.1
#6  0x00007fa53cac87c6 in Arts::AudioSubSystem::check ()
   from /usr/lib/libartsflow.so.1
#7  0x000000000041c189 in ?? ()
#8  0x00007fa53bd411c4 in __libc_start_main () from /lib/libc.so.6
#9  0x000000000040fad9 in ?? ()
#10 0x00007fff45289c48 in ?? ()
#11 0x0000000000000000 in ?? ()


If I try to configure alsa as the output engine in amarok, 
'xine was unable to initialise any audio drivers.'

amarok will play, but extremely quietly, just the slightest whisper.

If I then go and select alsa as the audio device in 
'system settings'-'sound system'-'hardware'-'audio device', then amarok will accept alsa as 
the output engine without complaint. but still, extremely low volume.



output of lsmod (truncated list):

Module                  Size  Used by
snd_intel8x0m          22032  0
ac                      8328  0
snd_intel8x0           40872  0
snd_ac97_codec        123224  2 snd_intel8x0m,snd_intel8x0
ac97_bus                3840  1 snd_ac97_codec
snd_usb_audio         100384  1
snd_usb_lib            21120  1 snd_usb_audio
snd_hda_intel         440408  2
snd_pcm_oss            47648  0
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  6 snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  4 snd_intel8x0m,snd_intel8x0,snd_hda_intel,snd_pcm
snd_hwdep              12552  2 snd_usb_audio,snd_hda_intel
snd_seq_dummy           5764  0
snd_seq_oss            38912  0
snd_seq_midi           10688  0
snd_rawmidi            29856  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    70856  22 snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_usb_lib,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10400  1 snd
pcspkr                  4992  0



Tried these next two from a random webpage, no idea if they are (k)ubuntu-appropriate?
If they are they don't look good:

root@kubuntu:/home/user# /etc/rc.d/init.d/alsasound stop
bash: /etc/rc.d/init.d/alsasound: No such file or directory

root@kubuntu:/home/user# "/etc/rc.d/init.d/alsasound start"
bash: /etc/rc.d/init.d/alsasound start: No such file or directory

not sure where to look for 'alsasound'... hmm



finally, looks like some of the alsa-related files are 32 bit, but this is a 64-bit machine & was 
originally installed from a 64-bit kubuntu cd ??




http://packages.ubuntu.com/en/hardy/lib64asound2   ----> i386
http://packages.ubuntu.com/en/hardy/amd64/libasound2/download  ----> amd64

my processor's an intel



ok the amd64 one installed ok:

(Reading database ... 96319 files and directories currently installed.)
Preparing to replace libasound2 1.0.15-3ubuntu4 (using .../libasound2_1.0.15-3ubuntu4_amd64.deb) ...
Unpacking replacement libasound2 ...
Setting up libasound2 (1.0.15-3ubuntu4) ...
You may need to execute the asoundconf(1) set-default-card macro.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place



no joy, sound still broken


power-off reboot


.........working 


not sure tbh whether it was libasound2_1.0.15-3ubuntu4_amd64 that fixed it,

or the discovery of the mixer control down by the clock.
there is an outside chance of that.. 






```

---

