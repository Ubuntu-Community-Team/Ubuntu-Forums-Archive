---
title: "Wireless problem"
date: 2008-04-21
forum: New to Ubuntu
---

### Post by duff_bluff on 2008-04-21
I posted this in the Hardy development section, but I think it might belong here instead since I am an absolute beginner.

My wireless light isn't on, I have no wireless in network manager and am just getting started with linux.  However, I have searched and searched EVERYWHERE to get this fixed, and no solutions have worked.  If you can find the solution on Google, I've seen it... and it does not work.  Here's some info for you guys:

lshw gives me this:

 >        *-network
             description: Network controller
             product: BCM94311MCG wlan mini-PCI
             vendor: Broadcom Corporation
             physical id: 0
             bus info: pci@0000:03:00.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list

lsmod gives me this

> Module                  Size  Used by
b43                   126760  0 
rfkill                 10128  1 b43
mac80211              192532  1 b43
cfg80211               17680  1 mac80211
led_class               7176  1 b43
input_polldev           6928  1 b43
ipv6                  311720  10 
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
ppdev                  11400  0 
powernow_k8            16608  1 
cpufreq_userspace       6180  0 
cpufreq_stats           8416  0 
cpufreq_powersave       3200  0 
cpufreq_conservative    10632  0 
cpufreq_ondemand       11152  1 
freq_table              6464  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
sbs                    17808  0 
sbshc                   8960  1 sbs
bay                     8064  0 
dock                   12960  1 bay
container               6656  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
ndiswrapper           243872  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
joydev                 15488  0 
snd_hda_intel         440408  3 
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
snd_rawmidi            29856  1 snd_seq_midi
evdev                  14976  8 
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
psmouse                46236  0 
serio_raw               9092  0 
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    70856  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                  4992  0 
k8temp                  7680  0 
soundcore              10400  1 snd
uvcvideo               62084  0 
compat_ioctl32         11136  1 uvcvideo
videodev               30720  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
video                  23444  8 
output                  5632  1 video
wmi_acer               11076  0 
nvidia               8858052  36 
battery                16776  0 
ac                      8328  0 
button                 10912  0 
shpchp                 38172  0 
i2c_nforce2             8704  0 
pci_hotplug            34608  1 shpchp
i2c_core               28544  2 nvidia,i2c_nforce2
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
loop                   21508  2 
sg                     41880  0 
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
sd_mod                 33280  2 
ata_generic             9988  0 
pata_amd               16772  0 
pata_acpi               9856  0 
sata_nv                31624  1 
ohci_hcd               27524  0 
ehci_hcd               41996  0 
libata                176304  4 ata_generic,pata_amd,pata_acpi,sata_nv
forcedeth              55564  0 
usbcore               169904  5 ndiswrapper,uvcvideo,ohci_hcd,ehci_hcd
scsi_mod              178488  4 sg,sr_mod,sd_mod,libata
ssb                    37252  1 b43
thermal                19744  0 
processor              41448  2 powernow_k8,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  7 
> 
iwconfig gives me this:
> lo        no wireless extensions.

eth0      no wireless extensions.

iwlist gives me this

> Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 

/etc/udev/rules.d/70-persistent-net.rules has this in it (I just took out the entire PCI device line as this was a solution for someone with a similar problem to mine, but I'll list it here to show you guys what I had originally):
> # This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10de:0x0269 (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTR{address}=="00:12:17:b6:8d:e5", ATTR{type}=="1", NAME="eth2"

/etc/modules has this in it:
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc
ndiswrapper

And lastly, I have gone to /etc/modprobe.d/blacklist and
blacklisted bcm43xx



I know that might be overkill with information, but maybe with this stuff present you can help me solve my issue.

---

### Post by sam_delta on 2008-04-21
try reinstalling fwcutter with aptitude (not synaptic)
worked with friend's broadcom

you need a internet conection to do this, so , plug a cable or something

go to a terminal and type to remove

sudo aptitude purge b43-fwcutter

update your repos with

sudo aptitude update

to reinstall type 

sudo aptitude install b43-fwcutter

then restart pc, goto somewhere in system>hardware drivers drivers, and activate broadcom driver


tell us how it goes
sam

---

### Post by terto on 2008-04-21
I believe you don't have the driver for your card.

What I did is download the windows version of the driver, and install it using ndiswrapper (which makes windows wireless lan drivers work for linux)

I used this [http://www.tuxmagazine.com/node/1000167](http://www.tuxmagazine.com/node/1000167) to learn how to do it.

Its written for SuSE, but the part you care about is there.

Cheers.

---

### Post by canthus13 on 2008-04-21
Here's a [thread]("http://ubuntuforums.org/showthread.php?t=649038") that may help.

--Me

---

### Post by sam_delta on 2008-04-21
im reading right now that thats a known bug of hardy

heres the bug report
[https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/197819](https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/197819)

the solution given was to completely remove and install b43-fwcutter as mentioned in my previous post #2

the problem seems to be that the b4-fwcutter driver does not come with boradcom propietary firmware installed by default, so you have to remove, and reinstall using Aptitude and it should automaticly fetch and install the firmware. then you should be able to activate broadcom propetary driver under system>administraror?>hardware drivers

---

### Post by duff_bluff on 2008-04-22
I uninstalled then reinstalled it, everything worked fine.  But when I restarted and went to Hardware Drivers, it wasn't there and wireless still isn't working.

I guess i could try again.  Right now some updates are downloading (63 updates, in fact), if I retry after updates might it work or should I try something else?

---

### Post by sam_delta on 2008-04-22
did it asked to fetch the firmware when you did the sudo aptitude install b43-fwcutter?

---

### Post by duff_bluff on 2008-04-22
Yes it did, and I selected yes.

---

### Post by sam_delta on 2008-04-22
nvm you did rebooted

as you already blacklilsted bcm

last thing i can sugest is to try again after the updates
running manually the firmware installer might also help 
manually run
 sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

if it does not work, i would suggest using ndiswrapper with windows drivers

---

### Post by duff_bluff on 2008-04-22
Yup.

---

### Post by duff_bluff on 2008-04-22
NEVERMIND! It worked! I retried the exact steps after I downloaded those updates, and I am glad to say that I am currently responding to you via my wireless router.  

TYVM

---

### Post by sam_delta on 2008-04-22
as you already blacklilsted bcm

last thing i can sugest is to try again after the updates
running manually the firmware installer might also help
manually run
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

if it does not work, i would suggest using ndiswrapper with windows drivers

---

### Post by sam_delta on 2008-04-22
alright bro, im glad its working :) enjoy ubuntu

---

### Post by PlayGod on 2008-04-27
> **sam_delta said:**
>  sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh


:guitar:

---

