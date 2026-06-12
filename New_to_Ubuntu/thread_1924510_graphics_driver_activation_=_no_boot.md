---
title: "graphics driver activation = no boot"
date: 2012-02-12
forum: New to Ubuntu
---

### Post by DGINSD on 2012-02-12
I activated the proprietary graphics driver for my system which said it required a reboot but after the reboot I get a bunch of text and a hang after grub. How can I boot using the default driver from grub?

Just out of curiosity shouldn't there be a graphical recovery mode that boots to the vesa driver or something?

---

### Post by 3Miro on 2012-02-12
Grub should give you a recovery option that should allow you to boot in "low graphics mod". If you don't see the Grub menu, then hold Shift while booting.

---

### Post by josephmills on 2012-02-12
if you can get to the copmmand line there is a file called blacklist.conf you can add things to it so they will not be there on boot 

exsample 

```

sudo nano /etc/modprobe.d/blacklist.conf 


```

now at the bottom of the page put in 

backlist <name of driver you want to blacklist> 

do not use the <> 


save exit reboot. let us know how it goes.

---

### Post by ajukilibodin on 2012-02-12
> **josephmills said:**
> if you can get to the copmmand line there is a file called blacklist.conf you can add things to it so they will not be there on boot 

exsample 

```

sudo nano /etc/modprobe.d/blacklist.conf 


```now at the bottom of the page put in 

backlist <name of driver you want to blacklist> 

do not use the <> 


save exit reboot. let us know how it goes.

He means > blacklist

Everyone makes typos (:

Are you using AMD graphics on a laptop? Or your graphics are hybrid by any chance?

---

### Post by DGINSD on 2012-02-12
> **3Miro said:**
> Grub should give you a recovery option that should allow you to boot in "low graphics mod". If you don't see the Grub menu, then hold Shift while booting.

This sounds like the better option to me then I can get into additional drivers and disable the goof.

The blacklist would be a great idea too if I remembered what the driver was called, that and I get confused a lot when navigating with the command line.

---

### Post by DGINSD on 2012-02-12
OK can't find a low graphics mode in grub but can get to a command line. That's all the recovery mode will let me do is access a command line.

---

### Post by DGINSD on 2012-02-12
> **ajukilibodin said:**
> He means 

Everyone makes typos (:

Are you using AMD graphics on a laptop? Or your graphics are hybrid by any chance?

Yes AMD graphics on a laptop. By hybrid do you mean Radeon?

The driver listed in additional drivers was ATI/AMD.

---

### Post by josephmills on 2012-02-12
> **DGINSD said:**
> OK can't find a low graphics mode in grub but can get to a command line. [COLOR="Red"]That's all the recovery mode will let me do is access a command line[/COLOR].


ok there are a couple of options that I can think of here. first I /We need to see ```
lsmod
``` also ```
lspci -nn | grep VGA 
``` would also be nice but is not needed. 

Here is a exsample 

I have a nvidia card and need nvidia-current or the 209.10 driver. 
Or I could try to use a opensource driver. 
Lets say that I try to install the 209.10 or (nvidia) and  something goes wrong and I now have no gui. 

I would get to the command line and do a 
```
lsmod
``` 

This is a exsample of what I have

```

$ lsmod
Module                  Size  Used by
snd_seq_dummy            987  0 
aes_i586                6816  1 
aes_generic            25738  1 aes_i586
pci_stub                 889  1 
vboxpci                11533  0 
vboxnetadp              5595  0 
vboxnetflt             13837  0 
vboxdrv               163736  3 vboxpci,vboxnetadp,vboxnetflt
powernow_k8             9832  0 
cpufreq_powersave        602  0 
cpufreq_stats           1997  0 
cpufreq_userspace       1480  0 
cpufreq_conservative     4018  0 
parport_pc             15799  0 
ppdev                   4058  0 
lp                      5570  0 
parport                22554  3 parport_pc,ppdev,lp
rfcomm                 25199  0 
sco                     5885  2 
bridge                 33031  0 
stp                      996  1 bridge
bnep                    7452  2 
l2cap                  21721  6 rfcomm,bnep
crc16                   1027  1 l2cap
bluetooth              36319  6 rfcomm,sco,bnep,l2cap
binfmt_misc             4907  1 
uinput                  4796  1 
fuse                   44268  1 
loop                    9769  0 
snd_hda_codec_nvhdmi     2567  1 
arc4                     974  2 
snd_hda_codec_conexant    16381  1 
ecb                     1405  2 
snd_hda_intel          16823  4 
snd_hda_codec          46002  3 snd_hda_codec_nvhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               4054  1 snd_hda_codec
snd_pcm                47226  3 snd_hda_intel,snd_hda_codec
snd_seq                35463  1 snd_seq_dummy
ath5k                 104058  0 
mac80211              123586  1 ath5k
ath                     6018  1 ath5k
uvcvideo               45574  0 
hid_microsoft           1987  0 
videodev               25605  1 uvcvideo
snd_timer              12270  3 snd_pcm,snd_seq
usbhid                 28016  0 
hid                    50909  2 hid_microsoft,usbhid
v4l1_compat            10250  2 uvcvideo,videodev
joydev                  6739  0 
snd_seq_device          3673  2 snd_seq_dummy,snd_seq
cfg80211               87645  3 ath5k,mac80211,ath
nvidia              10720877  42 
i2c_nforce2             4464  0 
snd                    34423  14 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore               3450  1 snd
rfkill                 10264  4 bluetooth,cfg80211
snd_page_alloc          5045  2 snd_hda_intel,snd_pcm
shpchp                 21200  0 
processor              26327  1 powernow_k8
pci_hotplug            18545  1 shpchp
i2c_core               12787  3 videodev,nvidia,i2c_nforce2
psmouse                44809  0 
pcspkr                  1207  0 
led_class               1757  1 ath5k
evdev                   5609  31 
serio_raw               2916  0 
wmi                     3575  0 
k10temp                 1979  0 
battery                 3782  0 
ac                      1640  0 
ext3                   94396  1 
jbd                    32401  1 ext3
mbcache                 3762  1 ext3
sg                     19937  0 
sd_mod                 26013  3 
crc_t10dif              1012  1 sd_mod
sr_mod                 10770  0 
cdrom                  26487  1 sr_mod
ata_generic             2247  0 
usb_storage            31033  0 
ohci_hcd               16999  0 
ehci_hcd               28689  0 
pata_amd                6625  0 
ahci                   27750  2 
video                  14605  0 
output                  1204  1 video
thermal                 9206  0 
button                  3598  0 
thermal_sys             9378  3 processor,video,thermal
libata                115889  3 ata_generic,pata_amd,ahci
usbcore                99329  6 uvcvideo,usbhid,usb_storage,ohci_hcd,ehci_hcd
forcedeth              40785  0 
nls_base                4541  1 usbcore
scsi_mod              105001  5 sg,sd_mod,sr_mod,usb_storage,libata



```


these are all the drivers that are installed on your system 

I now look to see what driver (209.10 or the nvidia)

there it is 
```
nvidia              10720877  42
```


so now that I found the driver that is messing things up I can do a couple of things 
1) I can remove the modual/driver with the command 
```
sudo rmmod <name of mod>
```

replace <name of mod> 
with your modual in my exssample 
```
sudo rmmod nvidia 
```

then reboot 

2) you can also add things to a blacklist if you look above I kinda explain how to do that. (minus bad spelling :) )

I hope that this helps out in some way let us know how it goes.

---

### Post by mastablasta on 2012-02-13
> **DGINSD said:**
> Yes AMD graphics on a laptop. By hybrid do you mean Radeon?
 
The driver listed in additional drivers was ATI/AMD.
 
 
no by hybrid he means one graphics chip on CPU and another one separatelly. this is a new feature and supported well by manufacturers in Windows7.
 
what happens is that computer uses the low power chip that is embeded in processor for doing simple graphics tasks, but when you start soemthing more demanding it uses the propper/separated GPU chip. what this does is it saves the energy and extends battery life. it's called switchable graphics or hybrid graphics. 
however this feature is not well supported for manufacturers to work in linux. in fact it is not supported at all. however some people made hacks and reverse engineered some functions. i believe the project is called bumblebee.
 
have a look here:[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

---

### Post by DGINSD on 2012-02-20
Sorry guys I'm kinda ADD and got side tracked into other things and forgot about this thread. 

Because it was a relatively new install I got frustrated and just reinstalled, obviously that fixed my problem. I have been doing a bit more research into the ATI Radeon drivers and found this [http://ubuntucomputing.posterous.com/amd-catalyst-121-driver-on-hp-pavilion-dv6t-q]("http://ubuntucomputing.posterous.com/amd-catalyst-121-driver-on-hp-pavilion-dv6t-q") which also points to this [http://askubuntu.com/questions/98827/ati-driver-re-install-fail/98851#98851]("http://askubuntu.com/questions/98827/ati-driver-re-install-fail/98851#98851") if you run into a brick wall like me. I haven't tried any of this cause as I said I got side tracked on some other things.

I do have a question though how can I tell if this applies to my  graphics chip/chips hedres my output from lsmod 

```
david@david-HP-Pavilion-g6-Notebook-PC:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
binfmt_misc            17540  1 
joydev                 17693  0 
wl                   2568210  0 
lib80211               14991  1 wl
bcma                   20219  0 
arc4                   12529  2 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
brcmsmac              631693  0 
snd_hda_codec_idt      70553  1 
brcmutil               17837  1 brcmsmac
snd_seq_midi           13324  0 
uvcvideo               72711  0 
snd_rawmidi            30547  1 snd_seq_midi
videodev               92992  1 uvcvideo
mac80211              462046  1 brcmsmac
v4l2_compat_ioctl32    17083  1 videodev
rts_pstor             445246  1 
cfg80211              199630  2 brcmsmac,mac80211
psmouse                73882  0 
snd_hda_codec_hdmi     32040  1 
crc_ccitt              12667  1 brcmsmac
snd_seq_midi_event     14899  1 snd_seq_midi
serio_raw              13166  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
k10temp                13166  0 
snd_hda_intel          33390  2 
snd_hda_codec         104931  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  19412  0 
snd_timer              29991  2 snd_seq,snd_pcm
fglrx                3101156  153 
wmi                    19256  1 hp_wmi
i2c_piix4              13301  0 
snd                    68266  14 snd_hda_codec_idt,snd_rawmidi,snd_hda_codec_hdmi,snd_seq,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_device,snd_timer
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   26002  3 
libahci                26861  1 ahci
r8169                  52788  0
```

and also from lspci -nn | grep VGA
 
```
david@david-HP-Pavilion-g6-Notebook-PC:~$ lspci -nn | grep VGA
00:01.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9649]
```

I think I've gotten up the courage to give the proprietary drivers a whirl again, any precautions I can take before diving in? I'm going to follow the instructions in the first link I posted.

One thing that's kinda bothered me these proprietary drivers that fudged my machine up were in jockey, lots of people could mess up their machines using those without doing a lot of prior research, this could turn off new users to Ubuntu, just a thought.

---

### Post by DGINSD on 2012-02-25
Just an update I went through the process taken from here [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx")

Which is the same instructions that got me in trouble the first time. This time same result, instead of a re-install like last time I followed the instructions on the wiki for "Removing Catalyst/fglrx" which got my machine up and runnin' again. So in short the uninstall instructions work great.  

I gave it one more shot after I got everything working again, mainly because the section labeled "Errors were encountered while processing: fglrx-amdcccle" (on 64-bit systems) matched the errors I saw during the second run through.

Oddly enough the third run through had no errors and worked perfectly,the reason; "Removing Catalyst/fglrx". Somehow without me doing it myself a version of Catalyst/fglrx was being installed and activated on my freshly installed and updated system, and as stated in the beginning of the "Installing Catalyst Manually (from AMD/ATI's site)" section you have to remove any previous versions before beginning.

So the lesson; even if you haven't installed the Catalyst/fglrx go through the removal procedure prior to beginning. I would imagine this holds true for using the GUI method as well as I had issues with it too (errors and what not). 

Hopefully this can save someone else some trouble and frustration.

---

