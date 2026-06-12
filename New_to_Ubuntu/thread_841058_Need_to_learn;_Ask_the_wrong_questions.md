---
title: "Need to learn; Ask the wrong questions"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by grewolf on 2008-06-26
Hello I am fairly new to Ubuntu.  I started out knowing nothing was only ok with windows.  I have read and read but often find that I either ask the wrong questions or look in the wrong places.  I am looking for information on how to become a Ubuntu administrator so that I can keep my family computer running smoothly.  I have just recently got the instructor and student Ubuntu guide.(Just got them haven't looked at them yet).  I am looking for other resources so that I can learn how to make my system run smoothly.  Just an example of one of my recent issues.  I have a sound blaster live 24 bit sound card and the 5.1 speaker system that was working.  I don't know what I did but now only the 2 front speakers and the sub are working.  The other speakers do function as I tested them by pluging them into the front speaker port on the sub.  (Front speaker 1 with power button connected to computer and Sub connected to Front speaker 1, other 4 speakers connected to sub)  I have searched here and in google under 5.1 surround sound and sound blaster live 24 bit and different variances of.  One of the sites that I went to [http://www.linuxquestions.org/questions/linux-newbie-8/my-sound-doesnt-work-on-a-soundblaster-live-24-bit-internal-card-633514/]("http://www.linuxquestions.org/questions/linux-newbie-8/my-sound-doesnt-work-on-a-soundblaster-live-24-bit-internal-card-633514/")
said to enter code 

```
sudo lspci -v
sudo lsmod
```

I did this and now have 5 pages of information that I have no Idea what it means and not sure what to ask to get the answer.  When I type in pasted text it gives me information that I don't understand any better than the original text.  

A little bit down it tells me to install asoundconf-gtk.  I do that and in the post it says under system>preferences>default sound card to select my card.  I don't see Sound Blaster Live.  I see pulse audio or CA0106.  

If any one can point me in the direction of books that I can buy or/and give me information on how to correct my speaker I would greatly appreciate it 

I have attatched the 5 pg. .odt file if any one is interested.

---

### Post by kesman on 2008-06-26
So you can't remember what happened that caused your Sound Blaster's back channels stop working?
Did you update something? Did you run the given commands and then it stopped, or did you run them after this? You know what the commands do right? You can easily find out with:
```

man lspci

```
and
```

man lsmod

```

Now first I'd make sure that no channels are muted. To do this the graphical way, doubleclick on the speaker icon on the top-right-corner of the screen, and browse trough the channels. If you somehow have disabled the speaker icon, you can do this in terminal too. Just run:
```

alsamixer

```
and hit TAB a few times to set ALL channels visible. Then browse trough them with arrow keys, and use M to mute/unmute channels. A letter M is displayed under a muted channel. Exit with ESC and try your sounds again.

---

### Post by DirtDawg on 2008-06-26
Hi. I don't know anything about sound cards, but you may want to check [this thread]("http://ubuntuforums.org/showthread.php?t=104704&highlight=sound+blaster") out. Reading all the posts is probably a good idea, but it looks to me like the last 3 or 4 posts may help you out.

When I need to find an answer to a problem, I usually use the Advanced Search page and change the Keyword option to "Search Titles Only". This narrows the results down considerably and usually pares out some less useful threads.

The Ubuntu Forums are like a giant, living users manual. Really impressive and more up to date than print books.

---

### Post by grewolf on 2008-06-26
A SPECIAL THANKS TO KESMAN.  

> **kesman said:**
> So you can't remember what happened that caused your Sound Blaster's back channels stop working?
Did you update something? Did you run the given commands and then it stopped, or did you run them after this? You know what the commands do right? You can easily find out with:
```

man lspci

```
and
```

man lsmod

```

Now first I'd make sure that no channels are muted. To do this the graphical way, doubleclick on the speaker icon on the top-right-corner of the screen, and browse trough the channels. If you somehow have disabled the speaker icon, you can do this in terminal too. Just run:
```

alsamixer

```
and hit TAB a few times to set ALL channels visible. Then browse trough them with arrow keys, and use M to mute/unmute channels. A letter M is displayed under a muted channel. Exit with ESC and try your sounds again.



I did what you said and didn't think to run the man on a command.  I thought it was only for programs.  Thank you for that

I tried to run the alsamixer in the terminal and this is what I got.  I then tried to run pulseaudio

```
jwilson@Crash-Burn:~$ alsamixer
*** PULSEAUDIO: Unable to connect: Connection refused

alsamixer: function snd_ctl_open failed for default: Connection refused
jwilson@Crash-Burn:~$ man lspci
jwilson@Crash-Burn:~$ alsamixer
*** PULSEAUDIO: Unable to connect: Connection refused

alsamixer: function snd_ctl_open failed for default: Connection refused
jwilson@Crash-Burn:~$ pulseaudio
W: main.c: WARNING: called SUID root, but not in group 'pulse-rt'.
E: module-alsa-sink.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device=hw:0 sink_name=alsa_output.pci_1102_7_alsa_playback_0"): initialization failed.
E: module-alsa-source.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-source" (argument: "device=hw:0 source_name=alsa_input.pci_1102_7_alsa_capture_0"): initialization failed.
E: module-protocol-stub.c: Failed to create socket directory '/tmp/.esd/socket': Operation not permitted
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: failed to initialize daemon.

```

---

### Post by Pjotr123 on 2008-06-26
You may find some easy tips, how-to's and background information here:
[http://ubuntutip.googlepages.com/](http://ubuntutip.googlepages.com/)

Especially aimed at beginners with Linux. :-)

---

### Post by grewolf on 2008-06-26
> **DirtDawg said:**
> Hi. I don't know anything about sound cards, but you may want to check [this thread]("http://ubuntuforums.org/showthread.php?t=104704&highlight=sound+blaster") out. Reading all the posts is probably a good idea, but it looks to me like the last 3 or 4 posts may help you out.

When I need to find an answer to a problem, I usually use the Advanced Search page and change the Keyword option to "Search Titles Only". This narrows the results down considerably and usually pares out some less useful threads.

The Ubuntu Forums are like a giant, living users manual. Really impressive and more up to date than print books.

Thank you. I'll try and read through all this and try whats in hear

---

### Post by kesman on 2008-06-26
Grewolf:

Try running pulseaudio with command
```

sudo pulseaudio

```
so it won't complain about permissions anymore. Anyhow, looks like there's something really messed up since even alsamixer won't start.

---

### Post by grewolf on 2008-06-26
> **kesman said:**
> Grewolf:

Try running pulseaudio with command
```

sudo pulseaudio

```
so it won't complain about permissions anymore. Anyhow, looks like there's something really messed up since even alsamixer won't start.

Have run sudo pulseaudio and here is the output

```
jwilson@Crash-Burn:~$ sudo pulseaudio
W: main.c: This program is not intended to be run as root (unless --system is specified).
E: pid.c: daemon already running.
E: main.c: pa_pid_file_create() failed.

```

---

### Post by kesman on 2008-06-26
Do you have multiple kernel options when you boot your PC? If you do, try an older kernel, maybe there's a bug in the kernels modules or something like that.

---

### Post by grewolf on 2008-06-27
I currently have sound out of front speakers. I pulled this code out of one of the links I was sent.  Not sure if it will work as it is for sound blaster 24 bit external and my card is internal 

[http://ubuntuforums.org/showthread.php?t=104704&highlight=sound+blaster]("http://ubuntuforums.org/showthread.php?t=104704&highlight=sound+blaster")

I used this code and ```
speaker-test -c6 -D plug:surround51 
```

and get this message 

```
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
```

What am I doing wrong.  I haven't changed anything yet as I don't want to make it worse.

---

### Post by Xiong Chiamiov on 2008-06-27
[Psychocats]("http://www.psychocats.net/ubuntu/index.php") is of course the premier guide-site for *buntu.
I find that most information can be found be searching either these forums or google with the keyword "linux" added.

The stickies at the top of each forum are also very useful (there's a reason they're stickied!), and you might try looking at [this one]("http://ubuntuforums.org/showthread.php?t=205449") specifically.

---

### Post by grewolf on 2008-06-27
> **Xiong Chiamiov said:**
> [Psychocats]("http://www.psychocats.net/ubuntu/index.php") is of course the premier guide-site for *buntu.
I find that most information can be found be searching either these forums or google with the keyword "linux" added.

The stickies at the top of each forum are also very useful (there's a reason they're stickied!), and you might try looking at [this one]("http://ubuntuforums.org/showthread.php?t=205449") specifically.

[COLOR="Red"]Thank you very much.  I think I'm on the right track.  I went to the pages that you provided the link for and made it to step 3.  [/COLOR]

S[COLOR="Red"]tep 1 was enter[/COLOR] ```
aplay -l
``` [COLOR="Red"]in terminal and I got this read out[/COLOR]
```

**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
[COLOR="Red"]
then I followed step 2 entering lspci -v and got this read out[/COLOR]

```
01:07.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs SB0410 SBLive! 24-bit
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at 9000 [size=32]
        Capabilities: [dc] Power Management version 2
```

[COLOR="Red"]Then I follewed step 3 and went to this web site to find my driver[/COLOR] [http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106]("http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106")
[COLOR="Red"]and follewed these instructions 
Most modern distros come with soundcore compiled as a module. You can check this in numerous ways. The easiest way is to type:[/COLOR]

       ```
modinfo soundcore
```

[COLOR="Red"]got this read out[/COLOR]

```
@Crash-Burn:~$ modinfo soundcore
filename:       /lib/modules/2.6.22-15-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     548AA54AF08207316C104F8
depends:        
vermagic:       2.6.22-15-generic SMP mod_unload 586 
```

[COLOR="Red"]
If this command returns that you have this module, then you don't need to recompile your kernel.[/COLOR] 




[COLOR="Red"]I found my driver which is this 
[/COLOR]
The module options for snd-ca0106
description:  	CA0106
author:  	James Courtier-Dutton
license: 	GPL 	
parm: 	index:Index value for the CA0106 soundcard. (array of int)
parm: 	id:ID string for the CA0106 soundcard. (array of charp)
parm: 	enable:Enable the CA0106 soundcard. (array of bool)
parm: 	subsystem:Force card subsystem model. (array of uint) 

[COLOR="Red"]
But I think I have it loaded already because I do have sound for somethings but not for others and not all my speakers.  I did a search in google but I used one of the read outs for my search criterea and found this page[/COLOR] [http://www.linuxquestions.org/questions/linux-hardware-18/creative-labs-sb-audigy-ls-alsa-no-sound-361619/]("http://www.linuxquestions.org/questions/linux-hardware-18/creative-labs-sb-audigy-ls-alsa-no-sound-361619/")

[COLOR="Red"]Which then sent me to this page [/COLOR][http://alsa.opensrc.org/DisableOss]("http://alsa.opensrc.org/DisableOss")
[COLOR="Red"]
which told me to do this 

Make sure you disable Oss in your Kernel configuration. If you don't, your system may try to use these drivers rather than the ALSA ones. If you see a message about...

Sound card not detected[/COLOR]
[COLOR="Red"]
and you are sure you have the correct ALSA driver, this is the reason. You have to go to /etc/modules.conf to disable (comment with a #) the lines that correspond to the plain Oss sound driver kernel modules. Check to see if you still have them by doing an...[/COLOR]

```
/sbin/lsmod
```
[COLOR="Red"]
I ran this code above and got a read out but not sure which step I should do next because I'm not sure what it is telling me in the readout, as well I'm not sure I understand their instructions eg go to /etc/modules.conf to disable.  I tried to go to that file location and I don't see one with that name.  

Here is the readout from the above command[/COLOR] 

 ```
n@Crash-Burn:~$ /sbin/lsmod
Module                  Size  Used by
binfmt_misc            12936  1 
radeon                125472  2 
drm                    83348  3 radeon
ppdev                  10244  0 
powernow_k8            16960  0 
cpufreq_ondemand        9612  1 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
freq_table              5792  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
container               5504  0 
sbs                    19592  0 
button                  8976  0 
dock                   10656  0 
ac                      6148  0 
video                  18060  0 
battery                11012  0 
ipv6                  273892  8 
xt_limit                3584  8 
xt_tcpudp               4224  10 
ipt_LOG                 7552  8 
ipt_MASQUERADE          4608  0 
ipt_TOS                 3200  0 
ipt_REJECT              5760  1 
nf_conntrack_irc        8088  0 
nf_conntrack_ftp       11136  0 
xt_state                3456  6 
lp                     12580  0 
snd_ca0106             34720  4 
snd_ac97_codec        100644  1 snd_ca0106
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  5 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
sg                     36764  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
snd_timer              24324  2 snd_pcm,snd_seq
serio_raw               8068  0 
sd_mod                 30336  0 
analog                 13344  0 
gameport               16776  1 analog
k8temp                  6656  0 
pcspkr                  4224  0 
psmouse                39952  0 
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  16 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
usblp                  15104  1 
ac97_bus                3200  1 snd_ac97_codec
snd_page_alloc         11400  2 snd_ca0106,snd_pcm
af_packet              24840  2 
i2c_nforce2             7040  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
i2c_core               26112  1 i2c_nforce2
amd64_agp              13700  1 
agpgart                35016  2 drm,amd64_agp
evdev                  11136  3 
iptable_nat             8708  0 
nf_nat                 20140  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19724  8 iptable_nat
nf_conntrack           65288  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nfnetlink               6936  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
iptable_mangle          3840  0 
iptable_filter          3968  1 
ip_tables              13924  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16260  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18560  5 
8139too                27776  0 
ata_generic             8452  0 
libata                125168  1 ata_generic
usb_storage            73152  0 
scsi_mod              147084  4 sg,sd_mod,libata,usb_storage
libusual               18448  1 usb_storage
floppy                 60004  0 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
amd74xx                15260  0 [permanent]
ide_core              116804  4 ide_cd,ide_disk,usb_storage,amd74xx
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  7 usblp,usb_storage,libusual,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  2 powernow_k8,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor



```

---

### Post by james_vanb on 2008-06-27
and you are sure you have the correct ALSA driver, this is the reason. You have to go to /etc/modules.conf to disable (comment with a #) the lines that correspond to the plain Oss sound driver kernel modules. 

To edit modules.conf:

```
sudo gedit /etc/modules.conf
```

This opens text editor.  Placing # in front of line (Commenting Out) causes that line to be skipped.

---

### Post by grewolf on 2008-06-27
> **james_vanb said:**
> and you are sure you have the correct ALSA driver, this is the reason. You have to go to /etc/modules.conf to disable (comment with a #) the lines that correspond to the plain Oss sound driver kernel modules. 

To edit modules.conf:

```
sudo gedit /etc/modules.conf
```

This opens text editor.  Placing # in front of line (Commenting Out) causes that line to be skipped.

I typed this command and the box came up blank.  Nothing in it.  ????  Does that mean that I don't have a driver?  

I also typed in the command ```
alsamixer
``` and it told me my card was pulse audio and my chip was pulse audio and all I can see is my master volume.  I am confused now.  Did the readouts before not tell me that I had the card selected properly and the right driver?

Also when I double click the sound icon in the menu bar and select change device I have 2 choices ca0106 alsa mixer or mixer 00 oss mixer 

I went back to the page[http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106]("http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106")
to make sure that I had the right driver this is what the page says

Most modern distros come with soundcore compiled as a module. You can check this in numerous ways. The easiest way is to type:

       ```
modinfo soundcore
```

If this command returns that you have this module, then you don't need to recompile your kernel. 

This is what I get when I enter that code 

```
@Crash-Burn:~$ modinfo soundcore
filename:       /lib/modules/2.6.22-15-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     548AA54AF08207316C104F8
depends:        
vermagic:       2.6.22-15-generic SMP mod_unload 586 
```

How do I tell if this is the right one?  And do I go to the filename in the  terminal read out to comment (disable) the settings?

---

### Post by kansasnoob on 2008-06-27
Well, I'm admittedly a bit lost, but I'd start by going to synaptic and installing:

> gnome-alsamixer

You'll then find the gui in the menu in Sound $ Video. I find if offers more options, here's mine:

Left most view: [ATTACH]75524[/ATTACH]

Right most view: [ATTACH]75525[/ATTACH]

Next I'd suggest adding:

> alsa-firmware

from synaptic. If it's not there you need to add the medibuntu repo:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

For Hardy:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

And add the GPG key:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

While in synaptic I'd also install:

> alsa-firmware-loaders


just because the two play well together.

I'd then restart the puter so it can play search and grab.

If that doesn't work we'll review some other stuff.

---

### Post by grewolf on 2008-06-27
> **kansasnoob said:**
> Well, I'm admittedly a bit lost, but I'd start by going to synaptic and installing:



You'll then find the gui in the menu in Sound $ Video. I find if offers more options, here's mine:

Left most view: [ATTACH]75524[/ATTACH]

Right most view: [ATTACH]75525[/ATTACH]

Next I'd suggest adding:



from synaptic. If it's not there you need to add the medibuntu repo:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

For Hardy:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

And add the GPG key:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

While in synaptic I'd also install:



just because the two play well together.

I'd then restart the puter so it can play search and grab.

If that doesn't work we'll review some other stuff.

Thank you I loaded the apps you said but was unable to load alsa-firmware.  I have the medabuntu repository but nothing in synaptic

I loaded what I was able to but when I went to applications>sound/video>gnome alsamixer I received this error 

```
Bad key or directory name: "/apps/gnome-alsamixer/display_mixers/": Key/directory may not end with a slash (/)
Bad key or directory name: "/apps/gnome-alsamixer/display_names/": Key/directory may not end with a slash (/)

```

I am also using Ubunty 7.10 Gutsy Gibbon.

---

### Post by james_vanb on 2008-06-27
Did a quick search for configuring 5.1 Sound Card found this:

[http://ubuntulinuxhelp.com/the-simple-way-to-get-51-surround-sound-audio-working-in-ubuntu/](http://ubuntulinuxhelp.com/the-simple-way-to-get-51-surround-sound-audio-working-in-ubuntu/)

Don't know if you tried this.

BTW - Although I'm running Hardy, just ran:

```
sudo gedit /etc/modules.conf
```

Mine is also blank.

---

### Post by kansasnoob on 2008-06-27
> **grewolf said:**
> Thank you I loaded the apps you said but was unable to load alsa-firmware.  I have the medabuntu repository but nothing in synaptic

I loaded what I was able to but when I went to applications>sound/video>gnome alsamixer I received this error 

```
Bad key or directory name: "/apps/gnome-alsamixer/display_mixers/": Key/directory may not end with a slash (/)
Bad key or directory name: "/apps/gnome-alsamixer/display_names/": Key/directory may not end with a slash (/)

```

I am also using Ubunty 7.10 Gutsy Gibbon.

OK, you're getting errors from synaptic or update manager. try this in terminal:

```
sudo apt-get update
```

There is no safer command to run, and I'm curious what kind of errors you'll get.

---

### Post by kansasnoob on 2008-06-27
I hope you didn't install Hardy version of Medibuntu, that's why I included the link to the website!

---

### Post by grewolf on 2008-06-27
> **kansasnoob said:**
> I hope you didn't install Hardy version of Medibuntu, that's why I included the link to the website!

No worries there I already had medibuntu installed no errors from 

```
sudo apt-get update
```

The errors that I posted were from when I went to applications>sound/video>gnome alsa mixer

Again no errors from synaptic or apt-get or update manager.  Only errors from trying to run Gnome Alsa Mixer

---

### Post by grewolf on 2008-06-28
I think I found the right information but I'm not sure how to interpret it.  I used ```
lsmod
``` in terminal and in newbie zine it says it lists every driver 

```

snd_ca0106             34720  3 
snd_ac97_codec        100644  1 snd_ca0106
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  4 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
sg                     36764  0 
analog                 13344  0 
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
snd                    54660  15 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
ac97_bus                3200  1 snd_ac97_codec
snd_page_alloc         11400  2 snd_ca0106,snd_pcm

```

I think these are all the drivers that I need to look at just not sure what its telling me.  The numbers are the size eg 11400 and the 2 snd_ca0106,snd_pcm would be "used by".  I don't understand what the used by means.  Any help with explaining this or where I can read about this would be helpful.  I tried ```
man lsmod
``` in the terminal but it didn't tell me much 

```
lsmod(8)                                                                                                         lsmod(8)

NAME
       lsmod — program to show the status of modules in the Linux Kernel

SYNOPSIS
       lsmod

DESCRIPTION
       lsmod is a trivial program which nicely formats the contents of the /proc/modules, showing what kernel modules are
       currently loaded.

BACKWARDS COMPATIBILITY
       This version of lsmod is for kernels 2.5.48 and above.  If it detects a kernel with support for old-style modules,
       it will attempt to run lsmod.modutils in its place, so it is completely transparent to the user.

COPYRIGHT
       This manual page Copyright 2002, Rusty Russell, IBM Corporation.

SEE ALSO
       modprobe(8), lsmod.modutils(8) 
```

---

### Post by grewolf on 2008-06-28
Wow I just think I had a major break through!  When I go to System>Preferences>Sound>Devices... I have the Sound Events, Music and Movies , and Audio Conferencing.

Under Sound Events>Sound playback; I have the drop down list which has the option of autodetect which when I click on the test button only plays sound from the front speakers.  

In the drop down menu under autodetect I have ca0106 listed 4 times.  If I select the ca0106 that is first in the list and press test I get no sound.  

If I select the ca0106 that is listed second and press test I get sound from my center speaker.  

If I select the ca0106 that is listed third and press test I get sound from my rear speakers

If I select the ca0106 that is listed fourth and press test I get and error message ```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.
```

I also have ALSA, ESD, and OSS listed.  From ALSA and ESD I get the same error message as above and from OSS I get sound from my front speakers.  

Is this normal?

---

### Post by grewolf on 2008-06-28
Can we mark this as solved.  I have sound working in all 5 speakers.  Audacity doesn't work for me.  EG no sound but amarok does and so does mplayer, gnome mplayer, vlc, music box and totem I only have sound from the rear speakers.  Thank you to every one for your help.  This is what I did:

I followed the hard way instructions from this post [http://ubuntuforums.org/showthread.php?t=795525]()

I commented out the lines that I had because I didn't have all of them and then I added ```
### Load manual channel config. Uncomment the above and recomment the below to go back to defaults.

load-module module-alsa-sink device_id=0 channels=6 channel_map=front-left,front-right,front-center, rear-left,rear-right,lfe

```

The speaker test doesn't work for me but the sound in Amarok, VLC and the Mplayers play sound from all 5 speakers

---

