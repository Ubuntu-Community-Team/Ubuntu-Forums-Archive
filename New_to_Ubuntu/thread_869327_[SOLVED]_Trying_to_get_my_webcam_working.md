---
title: "[SOLVED] Trying to get my webcam working"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by ChocolateChip_Wookie on 2008-07-24
Hello People,

I am absolutely new to Linux (no really?) as of about 2 hours ago although I have been in the IT industry for years. I am hoping someone can give me some pointers and help. I have a Sony Vaio SZ4VWN/X laptop which has a built in webcam/microphone. I dont know what make these are because they are built into the chassis. Anyway, they dont seem to be working? Can someone advise me on the correct drivers that will work with Ubunto 8.04.1 x86 (the Heron one).

More importantly, could someone advise me how to actually install these drivers because so far, I am having problems making the jump from Vista to Linux. I am willing to learn but I gather that I cannot just click on the driver and it will install? Is this the case? What do I do?

Any help will be gratefully received. Thanks in advance.

Kind Regards

---

### Post by rburkartjo on 2008-07-24
choc, ubuntu still has problems with webcams but this might enable you camera to work but wont 
guarantee the sound will work. i still cant get the sound to work on my logitech webcam. okay go to applications in the top left hand corner. then scroll down to add/remove. click it. then when it opens (note it might ask for your password first) go to search field and type in cheese. install cheese. it will be located in applciations/graphics after you install. make sure your webcam is plugged in. open cheese and see if it recongizes you webcam./cheesemaker

---

### Post by ChocolateChip_Wookie on 2008-07-25
I have completed the instructions. All I get is snow. No picture!

Very disappointed. Can anyone suggest a distro that does support web cams pretty well and behaves as nicely as Ubuntu. What about Kubuntu? I dont mind taking this distro out and putting in another.

---

### Post by steveneddy on 2008-07-25
> **ChocolateChip_Wookie said:**
> I have completed the instructions. All I get is snow. No picture!

Very disappointed. Can anyone suggest a distro that does support web cams pretty well and behaves as nicely as Ubuntu. What about Kubuntu? I dont mind taking this distro out and putting in another.

The Linux kernel is about the same is all distros.

You will probably have to find the web cam kernel module and insert it yourself into the kernel.

Inserting it is not hard, it's only a small command in terminal.

Finding the kernel module, well, have you tried Google?

I'll come back to this tonight and help you search if you need help. 

I'm at work at the moment.

Good luck.

---

### Post by BGFG on 2008-07-25
Hey, 
as far as i'm aware there are two drivers included with the kernel. you can load them using
```

sudo modprobe gspca
and 
sudo modprobe ov511 
```

it won't give you any output so then,use :
```

lsmod

```
to ensure that they loaded.

also, something to look at; [http://www.linux-drivers.org/usb_webcams.html](http://www.linux-drivers.org/usb_webcams.html)
(this is all info passed on to me by other forum users, hope it helps you)

My MSI starcam still isn't working so i hope you have better luck than i do :)
good luck.

---

### Post by LowSky on 2008-07-25
[https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)

---

### Post by cam381 on 2008-07-25
I don't recommend switching distros for two reasons: 1. All distros are based off pretty much the same kernel. Like popcorn, it's based off the same kernel, but the outside may be different. 2. Your an *ahem* newbie, so you probably best staying on Ububtu. I mean you can switch later but Ubuntu is good to start with. I mean, I'm a highly experienced Linux user who uses Unix, Red Hat, Debian, Gentoo, any distro you can think of, but love Ubuntu because of it's simplicity. Well I got quite a bit off track, there, from webcams to different distros, but I don't feel like changing it. LOL I'm out.

---

### Post by Nepherte on 2008-07-25
Sony most of the times (if not always?) uses webcams of Ricoh in its laptops. Does the command lsusb gives you an output something like this?
Bus 006 Device 003: ID 05ca:183a **Ricoh Co., Ltd**

If so, you could try this driver: [http://ubuntuforums.org/showpost.php?p=3708885&postcount=32](http://ubuntuforums.org/showpost.php?p=3708885&postcount=32)
It worked for my Sony Vaio SZ6.

---

### Post by ChocolateChip_Wookie on 2008-07-26
This is the content of the output

Module                  Size  Used by
ov511                  80672  0 
gspca                 643920  0 
af_packet              23812  4 
ipv6                  267780  10 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
sonypi                 23192  0 
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5284  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
snd_hda_intel         344728  3 
pcmcia                 40876  0 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
joydev                 13120  0 
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
uvcvideo               58116  0 
hci_usb                16540  2 
iwl3945                89844  0 
snd_rawmidi            25760  1 snd_seq_midi
compat_ioctl32          2304  1 uvcvideo
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
iwlwifi_mac80211      219108  1 iwl3945
bluetooth              61156  7 rfcomm,l2cap,hci_usb
videodev               29440  3 ov511,gspca,uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
sky2                   47492  0 
nvidia               7825536  36 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
battery                14212  0 
cfg80211               15112  1 iwlwifi_mac80211
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_core               24832  1 nvidia
ac                      6916  0 
serio_raw               7940  0 
sony_laptop            35292  0 
video                  19856  0 
output                  4736  1 video
tifm_7xx1               8576  0 
evdev                  13056  7 
tpm_infineon           10152  0 
tpm                    16544  1 tpm_infineon
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
intel_agp              25492  0 
button                  9232  0 
tifm_core              11012  1 tifm_7xx1
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
tpm_bios                8320  1 tpm
pcspkr                  4224  0 
psmouse                40336  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
agpgart                34760  2 nvidia,intel_agp
soundcore               8800  1 snd
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
sd_mod                 30720  3 
cdrom                  37408  1 sr_mod
ata_generic             8324  0 
pata_acpi               8320  0 
ata_piix               19588  2 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
libata                159344  3 ata_generic,pata_acpi,ata_piix
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  7 ov511,gspca,uvcvideo,hci_usb,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 


No problems. I am an absolute newbie. I know 'jack' about Linux but I have a deep seated and abiding hatred of Windows nurtured over many years of 'blue screens', 'please restart now' and 'security updates. I agree that Ubuntu just seems to work and that it is almost the number one distro which I why I chose it as my first on the basis that it would probably be the most stable although I have been playing with Puppy and DSL for the last few days as well.

I have downloaded and installed Skype using the instructions here:
[http://www.funnestra.org/ubuntu/hardy/#nvidia-driver](http://www.funnestra.org/ubuntu/hardy/#nvidia-driver)

I have tested the video cam but still nothing. Skype says, not detected. Now, if this were windows (yeah I know, it aint) I would do an autodetect, have disk and install the apropriate drivers, but this being Linux, I'm stuck. I'm having problems saving files, it keeps telling me 'access denied' but I cannot figure out how to give it the admin passwords. Can anyone help me further?

Kind Regards

---

### Post by ChocolateChip_Wookie on 2008-07-26
> **Nepherte said:**
> Sony most of the times (if not always?) uses webcams of Ricoh in its laptops. Does the command lsusb gives you an output something like this?
Bus 006 Device 003: ID 05ca:183a **Ricoh Co., Ltd**

If so, you could try this driver: [http://ubuntuforums.org/showpost.php?p=3708885&postcount=32](http://ubuntuforums.org/showpost.php?p=3708885&postcount=32)
It worked for my Sony Vaio SZ6.

OK. Willing to give it a try. Mine is a SZ4 so it 'should' work. But can anyone advise me how to install the drivers? Told you I was new....

---

### Post by k3lt01 on 2008-07-26
Go to synaptic and install Camorama, then open Camorama and see what happens.

I had this same problem, external webcam though and on 7.04 Fiesty, and after installing Camorama the cam worked and I have never looked back since.

---

### Post by ChocolateChip_Wookie on 2008-07-27
Thank you for your reply. I did as you suggest and got the following error :

Could not connect to video device (dev/video0), Please check connection.

I DO have a video camera (honestly) because I was using it last week in Vista to have a chat over MSN. Please could anyone advise me how to 'force' linux to acknowledge the hardware? Would installing the drivers achieve this? If so, please could you advise 'HOW' to install the drivers.

---

### Post by ChocolateChip_Wookie on 2008-07-27
OK. I found this page : [http://www.palmix.org/r5u870-en.html](http://www.palmix.org/r5u870-en.html)

However, I do not understand the instructions. I think the person who wrote it did a fair job of the translation but there just isnt enough explanation for a newbie. Could someone please translate it into a set of instructions for a poor newbie?

Kind Regards

---

### Post by ChocolateChip_Wookie on 2008-07-27
OK. According to the Synaptic Package Manager, I have managed to install the driver properly (although I have no idea how. I just copied the code here...[http://ubuntuforums.org/showthread.php?t=289836&highlight=Install+Ricoh+Driver&page=22](http://ubuntuforums.org/showthread.php?t=289836&highlight=Install+Ricoh+Driver&page=22)


I went and checked Skype and Camorama, but still no joy? What else do I have to do?

---

### Post by ChocolateChip_Wookie on 2008-07-28
Anyone?

I have installed the drivers and confirmed that they are being used, but the webcam is still not recognised. Can anyone tell me how to force Linux to acknowledge the hardware and use the drivers. If not, this is a bit of a deal breaker for me and I am going to have to go back to (ack) Vista. I dont want to, I really like Ubuntu, what I've seen of it...but if I cannot get the webcam working, I am going to have to rollback vista. I just dont know enough about Ubuntu to fix this on my own....

Kind Regards

---

### Post by Methuselah on 2008-07-28
What is the output of your lsusb?

```

lsusb

```

That might give a better idea of what kind of webcam you have.
Then we can see if there are linux drivers for the it that haven't been included in ubuntu by default.

Most cams that support UVC (usb video class), like my particular logitech, should work 'out of the box' but there are some cam makers that still use custom protocols and don't provide linux drivers.
Some such cams still have drivers out there but I'd imagine a large number don't.

So, unfortunately, if the webcam is a must-use for you, there is a distinct possibility you might have to reload vista to use it.

---

### Post by Methuselah on 2008-07-28
> **ChocolateChip_Wookie said:**
> Anyone?

I have installed the drivers and confirmed that they are being used, but the webcam is still not recognised. Can anyone tell me how to force Linux to acknowledge the hardware and use the drivers. If not, this is a bit of a deal breaker for me and I am going to have to go back to (ack) Vista. I dont want to, I really like Ubuntu, what I've seen of it...but if I cannot get the webcam working, I am going to have to rollback vista. I just dont know enough about Ubuntu to fix this on my own....

Kind Regards

OK, I just noticed there's a chance the Ricoh driver might work.
What did you do to install it?
Did you follow the site's instructions?

Even if you have downloaded and installed the driver you'll still need to load it into the running kernel with modprobe, as the site says.

Also, note this instruction from the site:

> 
IMPORTANT: the module r5u870 goes in conflict with the uvcvideo module, therefore it is necessary to uninstall or to unload the uvcvideo module!!


In your lsmod output I saw that uvcvideo was listed.
Remove it with:

> 
sudo rmmod uvcvideo


in a terminal.

I guess you should do this before modprobe-ing r5u870.

---

### Post by ChocolateChip_Wookie on 2008-07-28
Thanks so much for your help Methuselah. I will try this as soon as I get home. I'm chained to a Windows desk at the moment. There is a good chance I didnt understand some or all of the instructions but I will try the last line of code you provided in your second post first. If this doesnt fix it then I'll take the whole install out (it's a bit flakey anyway with compiz although heaven knows why I cant use it very well with all the power I have on my vaio) and try again from scratch. I will let you know the results of my testing and the exact steps I have followed.

I am sure there is a way to get the driver working because people all over the net are reporting they can use the webcam installed on their Vaio SZ3 - 7. I am sure the SZ4 is covered. I will post the output of the 'ls' command asap. I did do this but didnt understand what I was seeing very well.

---

### Post by ChocolateChip_Wookie on 2008-07-28
Right. I have tried the last command you advised. No joy. Here is the output of the Lsusb command :

Bus 005 Device 003: ID 05ca:1835 Ricoh Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 044e:300d Alps Electric Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

I did the sudo modprobe thing and here is the output of lsmod :

Module                  Size  Used by
ov511                  80672  0 
gspca                 643920  0 
af_packet              23812  4 
ipv6                  267780  10 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
sonypi                 23192  0 
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5284  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
compat_ioctl32          2304  0 
joydev                 13120  0 
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
pcmcia                 40876  0 
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
hci_usb                16540  2 
snd_seq_midi            9376  0 
r5u870                 27460  0 
usbcam                 48256  1 r5u870
iwl3945                89844  0 
snd_rawmidi            25760  1 snd_seq_midi
videodev               29440  3 ov511,gspca,usbcam
v4l2_common            18304  1 videodev
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
iwlwifi_mac80211      219108  1 iwl3945
bluetooth              61156  7 rfcomm,l2cap,hci_usb
nvidia               7825536  36 
v4l1_compat            15492  1 videodev
videobuf_dma_sg        14980  1 usbcam
videobuf_core          18820  2 usbcam,videobuf_dma_sg
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
serio_raw               7940  0 
i2c_core               24832  1 nvidia
battery                14212  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sky2                   47492  0 
cfg80211               15112  1 iwlwifi_mac80211
ac                      6916  0 
tifm_7xx1               8576  0 
psmouse                40336  0 
sony_laptop            35292  0 
video                  19856  0 
output                  4736  1 video
tifm_core              11012  1 tifm_7xx1
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
evdev                  13056  7 
intel_agp              25492  0 
button                  9232  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
pcspkr                  4224  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
tpm_infineon           10152  0 
tpm                    16544  1 tpm_infineon
tpm_bios                8320  1 tpm
agpgart                34760  2 nvidia,intel_agp
soundcore               8800  1 snd
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sd_mod                 30720  3 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
ata_generic             8324  0 
pata_acpi               8320  0 
ohci1394               33584  0 
ata_piix               19588  2 
ieee1394               93752  2 sbp2,ohci1394
ehci_hcd               37900  0 
libata                159344  3 ata_generic,pata_acpi,ata_piix
scsi_mod              151436  5 sbp2,sg,sd_mod,sr_mod,libata
uhci_hcd               27024  0 
usbcore               146028  8 ov511,gspca,hci_usb,r5u870,usbcam,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 


Notice that the uvcvideo entry is now missing...

What else can I do?

---

### Post by Methuselah on 2008-07-28
Well according to the site below, you should be able to get this cam wsorking.

[http://www.arakhne.org/spip.php?rubrique31](http://www.arakhne.org/spip.php?rubrique31)

One of the models that's supposed to be supported has your usb id:

> 
    * 05ca:1810 HP Pavilion Webcam - UVC
    * 05ca:1830 Sony Visual Communication Camera VGP-VCC2 (for VAIO SZ)
    * 05ca:1832 Sony Visual Communication Camera VGP-VCC3 (for VAIO UX)
    * 05ca:1833 Sony Visual Communication Camera VGP-VCC2 (for VAIO AR1)
    * 05ca:1834 Sony Visual Communication Camera VGP-VCC2 (for VAIO AR2)
    *** 05ca:1835 Sony Visual Communication Camera VGP-VCC5 (for VAIO SZ)**
    * 05ca:1836 Sony Visual Communication Camera VGP-VCC4 (for VAIO FE)
    * 05ca:1870 HP Pavilion Webcam / HP Webcam 1000


I see the r5u870 module in your lsmod.
Are you sure it isn't working>
Did you select the right dev/video device in your application?

If it really isn't working, what did you do to install the driver modules and what is your kernel version?

```

uname -r

```

---

### Post by Methuselah on 2008-07-28
BTW, here's a thread with someone installing the same driver.
A poster gave a nice walkthrough.

[http://ubuntuforums.org/showthread.php?t=721257](http://ubuntuforums.org/showthread.php?t=721257)

---

### Post by ChocolateChip_Wookie on 2008-07-28
Thanks Methuselah, 

I have installed a completely clean version of Linux Mint (based on Ubuntu I understand) I am going to walk through the steps again. Perhaps I just broke the other install before it had a chance (I was messing with bash without understanding a whole lot). If this works in Mint, then I think I'll go back to Heron since I prefer it. I am really just killing two birds with one stone a) trying out new distro's hoping that one will support my webcam and b) just trying out a new distro to see the difference.

Keep you posted through the evening. At least I have a working internet connection which was step one with Mint.

---

### Post by no-1-uno on 2008-07-28
how do I uninstall the drivers you listed?

I had the cam running with the cheese thing but loaded your suggestions to see if I could get it to work with Yahoo Messanger.

After installing the drivers I lost the picture.

ThankX for your help

---

### Post by ChocolateChip_Wookie on 2008-07-28
OK. Followed the instructions at the following address :

[http://ubuntuforums.org/showthread.php?t=289836&highlight=Install+Ricoh+Driver&Page=22](http://ubuntuforums.org/showthread.php?t=289836&highlight=Install+Ricoh+Driver&Page=22)

(See Post #216)

Then

Just for good measure, I took out the uvcvideo using your code :

```
sudo rmmod uvcvideo 
```

Here is the output of the lsmod request :

```
Module                  Size  Used by
r5u870                 27460  0 
usbcam                 48256  1 r5u870
videobuf_dma_sg        14980  1 usbcam
videobuf_core          18820  2 usbcam,videobuf_dma_sg
af_packet              23812  4 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
sonypi                 23192  0 
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
joydev                 13120  0 
snd_hda_intel         344728  5 
pcmcia                 40876  0 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
compat_ioctl32          2304  0 
snd_rawmidi            25760  1 snd_seq_midi
videodev               29440  1 usbcam
iwl3945                89844  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
hci_usb                16540  2 
iwlwifi_mac80211      219108  1 iwl3945
v4l1_compat            15492  1 videodev
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
v4l2_common            18304  1 videodev
bluetooth              61156  7 rfcomm,l2cap,hci_usb
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211               15112  1 iwlwifi_mac80211
sky2                   47492  0 
serio_raw               7940  0 
battery                14212  0 
ac                      6916  0 
i2c_core               24832  0 
sony_laptop            35292  0 
tifm_7xx1               8576  0 
video                  19856  0 
output                  4736  1 video
psmouse                40336  0 
tifm_core              11012  1 tifm_7xx1
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
button                  9232  0 
snd                    56996  21 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
intel_agp              25492  0 
agpgart                34760  1 intel_agp
tpm_infineon           10152  0 
tpm                    16544  1 tpm_infineon
tpm_bios                8320  1 tpm
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
pcspkr                  4224  0 
soundcore               8800  1 snd
evdev                  13056  13 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
sd_mod                 30720  3 
cdrom                  37408  1 sr_mod
ata_piix               19588  2 
ata_generic             8324  0 
ehci_hcd               37900  0 
pata_acpi               8320  0 
libata                159344  3 ata_piix,ata_generic,pata_acpi
ohci1394               33584  0 
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ieee1394               93752  2 sbp2,ohci1394
uhci_hcd               27024  0 
usbcore               146028  6 r5u870,usbcam,hci_usb,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 



```

Now, I checked the driver was installed by going to Administration --> Hardware Drivers. The driver was ticked and had a green light against it.

I have installed both Skype and Camorama using Synaptic.

Rebooting now....

---

### Post by ChocolateChip_Wookie on 2008-07-28
OK.

Rebooted. Tried Camorama...

This is the message :

Could not connect to video device (/dev/video0). Please check connection...

OK. What did I miss or what did I do wrong?

---

### Post by Methuselah on 2008-07-28
> **ChocolateChip_Wookie said:**
> OK. Followed the instructions at the following address :

[http://ubuntuforums.org/showthread.php?t=289836&highlight=Install+Ricoh+Driver&Page=22](http://ubuntuforums.org/showthread.php?t=289836&highlight=Install+Ricoh+Driver&Page=22)

(See Post #216)

Then

Just for good measure, I took out the uvcvideo using your code :

```
sudo rmmod uvcvideo 
```

Here is the output of the lsmod request :

```
Module                  Size  Used by
r5u870                 27460  0 
usbcam                 48256  1 r5u870
videobuf_dma_sg        14980  1 usbcam
videobuf_core          18820  2 usbcam,videobuf_dma_sg
af_packet              23812  4 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
sonypi                 23192  0 
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
joydev                 13120  0 
snd_hda_intel         344728  5 
pcmcia                 40876  0 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
compat_ioctl32          2304  0 
snd_rawmidi            25760  1 snd_seq_midi
videodev               29440  1 usbcam
iwl3945                89844  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
hci_usb                16540  2 
iwlwifi_mac80211      219108  1 iwl3945
v4l1_compat            15492  1 videodev
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
v4l2_common            18304  1 videodev
bluetooth              61156  7 rfcomm,l2cap,hci_usb
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211               15112  1 iwlwifi_mac80211
sky2                   47492  0 
serio_raw               7940  0 
battery                14212  0 
ac                      6916  0 
i2c_core               24832  0 
sony_laptop            35292  0 
tifm_7xx1               8576  0 
video                  19856  0 
output                  4736  1 video
psmouse                40336  0 
tifm_core              11012  1 tifm_7xx1
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
button                  9232  0 
snd                    56996  21 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
intel_agp              25492  0 
agpgart                34760  1 intel_agp
tpm_infineon           10152  0 
tpm                    16544  1 tpm_infineon
tpm_bios                8320  1 tpm
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
pcspkr                  4224  0 
soundcore               8800  1 snd
evdev                  13056  13 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
sd_mod                 30720  3 
cdrom                  37408  1 sr_mod
ata_piix               19588  2 
ata_generic             8324  0 
ehci_hcd               37900  0 
pata_acpi               8320  0 
libata                159344  3 ata_piix,ata_generic,pata_acpi
ohci1394               33584  0 
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ieee1394               93752  2 sbp2,ohci1394
uhci_hcd               27024  0 
usbcore               146028  6 r5u870,usbcam,hci_usb,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 



```

Now, I checked the driver was installed by going to Administration --> Hardware Drivers. The driver was ticked and had a green light against it.

I have installed both Skype and Camorama using Synaptic.

**Rebooting now**....

Oh..oh, this may be frustrating your efforts.
The drivers in linux are implemented as loadable kernel modules.
modprobe <modulename> actually loads the module into the running kernel. 
It does NOT configure the kernel to load it after all subsequent reboots. 
rmmod behaves the same way.

There is a file that tells the kernel what modules to load at boot.
While experimenting, it is typical to not bother to edit that file/reboot but to just issue the modprobe/rmmod command directly.

So in this case, whenever you reboot the configuration will be reset to whichever modules are set to load on boot. 
I fear that you may be undoing your work everytime you reboot and testing the webcam with the OS in a state that does not reflect the changes you made.

This is why [http://www.palmix.org/r5u870-en.html](http://www.palmix.org/r5u870-en.html) says:

> 
If you want to make permanent the module loading on each boot, edit the file /etc/modules with your favourite text editor and add, if there aren't, these lines:

r5u870
videodev
video-buf
v4l1-compat
v4l2-common


Anyway, I hope that made some semblance of sense.
Basically, DON'T reboot after rmmod-ing/modprobre-ing the driver module. Test the camera first!
It goes totally against any Windows-based intuition doesn't it? :)

---

### Post by ChocolateChip_Wookie on 2008-07-28
I dont understand? Do you mean I can never reboot? This doesnt make any sense?

What do I have to do to fix this now? Have I lost all the changes I just made? The driver is still showing in the Hardware Drivers file?

---

### Post by ChocolateChip_Wookie on 2008-07-28
OK. new problem. I've tried to modify the text file under etc/modules, but it wont let me! It says I dont have the permissions? How do I give it the permissions?

---

### Post by Methuselah on 2008-07-28
> **ChocolateChip_Wookie said:**
> I dont understand? Do you mean I can never reboot? This doesnt make any sense?

What do I have to do to fix this now? Have I lost all the changes I just made? The driver is still showing in the Hardware Drivers file?

Oh, the driver is showing there?
I've only ever seen restricted drivers in that window.
I'm not 100% what you did so maybe you've already configured it to load the driver at boot.

Do lsmod now (after the reboot) to see if your changes are still in place. (post it too)
If so, I'm out of ideas for the moment.

---

### Post by ChocolateChip_Wookie on 2008-07-28
Here is the output of the lsmod :

```
Module                  Size  Used by
af_packet              23812  4 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
sonypi                 23192  0 
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
pcmcia                 40876  0 
joydev                 13120  0 
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
r5u870                 27460  0 
usbcam                 48256  1 r5u870
snd_seq_dummy           4868  0 
videobuf_dma_sg        14980  1 usbcam
snd_seq_oss            35584  0 
videobuf_core          18820  2 usbcam,videobuf_dma_sg
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
hci_usb                16540  2 
iwl3945                89844  0 
uvcvideo               58116  0 
nvidia               7825536  36 
compat_ioctl32          2304  1 uvcvideo
iwlwifi_mac80211      219108  1 iwl3945
bluetooth              61156  7 rfcomm,l2cap,hci_usb
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
videodev               29440  2 usbcam,uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
i2c_core               24832  1 nvidia
tifm_7xx1               8576  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
battery                14212  0 
sky2                   47492  0 
cfg80211               15112  1 iwlwifi_mac80211
tifm_core              11012  1 tifm_7xx1
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ac                      6916  0 
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
sony_laptop            35292  0 
serio_raw               7940  0 
video                  19856  0 
output                  4736  1 video
tpm_infineon           10152  0 
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                40336  0 
tpm                    16544  1 tpm_infineon
intel_agp              25492  0 
agpgart                34760  2 nvidia,intel_agp
pcspkr                  4224  0 
tpm_bios                8320  1 tpm
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
button                  9232  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
soundcore               8800  1 snd
evdev                  13056  7 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
sd_mod                 30720  3 
cdrom                  37408  1 sr_mod
ata_piix               19588  2 
ata_generic             8324  0 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
pata_acpi               8320  0 
libata                159344  3 ata_piix,ata_generic,pata_acpi
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  7 r5u870,usbcam,hci_usb,uvcvideo,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 

```

Now, checked the Administration ---> Hardware Drivers screen and found the driver is there.

I changed the 'modules' file in Nautilus (google really is your friend) so all references are now in there...

Now what?

---

### Post by ChocolateChip_Wookie on 2008-07-28
Oops. Forgot to remove uvc video using your code.

Done.

Still no joy!

What am I doing wrong?

---

### Post by ChocolateChip_Wookie on 2008-07-28
Here is the output of lsmod now (no reboots I promise)
```

Module                  Size  Used by
af_packet              23812  4 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
sonypi                 23192  0 
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
pcmcia                 40876  0 
joydev                 13120  0 
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
[B][COLOR="Red"]r5u870                 27460  0 
[/COLOR][/B]**[COLOR="Red"]usbcam                 48256  1 r5u870[/COLOR]**
snd_seq_dummy           4868  0 
videobuf_dma_sg        14980  1 usbcam
snd_seq_oss            35584  0 
videobuf_core          18820  2 usbcam,videobuf_dma_sg
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
hci_usb                16540  2 
iwl3945                89844  0 
nvidia               7825536  36 
compat_ioctl32          2304  0 
iwlwifi_mac80211      219108  1 iwl3945
bluetooth              61156  7 rfcomm,l2cap,hci_usb
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
[B][COLOR="Red"]videodev               29440  1 usbcam
v4l1_compat            15492  1 videodev
v4l2_common            18304  1 videodev
[/COLOR][/B]i2c_core               24832  1 nvidia
tifm_7xx1               8576  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
battery                14212  0 
sky2                   47492  0 
cfg80211               15112  1 iwlwifi_mac80211
tifm_core              11012  1 tifm_7xx1
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ac                      6916  0 
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
sony_laptop            35292  0 
serio_raw               7940  0 
[B][COLOR="Red"]video                  19856  0 
output                  4736  1 video
[/COLOR][/B]tpm_infineon           10152  0 
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                40336  0 
tpm                    16544  1 tpm_infineon
intel_agp              25492  0 
agpgart                34760  2 nvidia,intel_agp
pcspkr                  4224  0 
tpm_bios                8320  1 tpm
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
button                  9232  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
soundcore               8800  1 snd
evdev                  13056  7 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
sd_mod                 30720  3 
cdrom                  37408  1 sr_mod
ata_piix               19588  2 
ata_generic             8324  0 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
pata_acpi               8320  0 
libata                159344  3 ata_piix,ata_generic,pata_acpi
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  6 r5u870,usbcam,hci_usb,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3
``` 

I have highlighted the interesting bits...

---

### Post by Methuselah on 2008-07-28
And with the set of modules you tried the camera in the skype video options page and it didn't work?

---

### Post by ChocolateChip_Wookie on 2008-07-28
Neither Skype, Camorama nor Amsn work...

It keeps insisting that no cam is connected!

---

### Post by Methuselah on 2008-07-28
> **ChocolateChip_Wookie said:**
> Neither Skype, Camorama nor Amsn work...

It keeps insisting that no cam is connected!

Oi...

I'm fast running out of ideas.

Try posting the output of

```

dmesg | grep -i usb

```

to see if there is any interesting message from the system.

---

### Post by ChocolateChip_Wookie on 2008-07-28
That code doesnt return anything except a new prompt?

---

### Post by Methuselah on 2008-07-28
dmesg by itself should return a bunch of text from the system log.
The grep just filters out lines that don't have usb in them.
I didn't expect the output to be nothing at all.

---

### Post by ChocolateChip_Wookie on 2008-07-28
Nope. Nothing at all, just a new prompt.

These are the first couple of lines of the dmesg (all output is the same)

[ 3678.597973] wmaster0: RX non-WEP frame, but expected encryption
[ 3679.197251] wlan0: RX non-WEP frame, but expected encryption
[ 3679.197262] wmaster0: RX non-WEP frame, but expected encryption
[ 3679.796488] wlan0: RX non-WEP frame, but expected encryption

---

### Post by ChocolateChip_Wookie on 2008-07-28
Found a log file...perhaps this will shed some light... (I know it's long, but it;s the log from the minute I loaded Mint to the minute I gave up ;-)

It's not really a tar, but it was the only way I could get the forum to accept a text file of that size...

---

### Post by Methuselah on 2008-07-28
I'll look at it to see if I can figure anything out.

---

### Post by Methuselah on 2008-07-28
Part of that files says:

> 
Jul 28 19:58:46 sabrecat-laptop kernel: [ 1145.519199] usbcam: registering driver r5u870 0.11.1SVN
Jul 28 19:58:46 sabrecat-laptop kernel: [ 1145.519596] r5u870-0: Detected Sony VGP-VCC5
Jul 28 19:58:46 sabrecat-laptop kernel: [ 1146.976541] r5u870: probe of 5-6:1.0 failed with error -2
Jul 28 19:58:46 sabrecat-laptop kernel: [ 1146.976560] usbcore: registered new interface driver r5u870


So it seems the driver did try to attach to the cam but it failed.
I've seen that happen when the firmware to load wasn't found.

Look around under /lib/firmware
If you see folders with a kernel version name, choose the one that matches your 'uname -r'.
Look for files like:

> 
r5u870_1810.fw  r5u870_1833.fw  r5u870_1836.fw    r5u870_1870.fw
r5u870_1830.fw  r5u870_1834.fw  r5u870_183b.fw
r5u870_1832.fw  r5u870_1835.fw  r5u870_1870_1.fw


Are they present?

---

### Post by k3lt01 on 2008-07-28
I'll apologise now for not being around to help, Methuselah is doing a great job.

After reading through the thread just now it looks to me as though there is a heap of confusion about what is actually being done and what needs to be done. I may be being slow here but I can't actually figure out what your up to in this process. You have switched to Mint, have you gone through the threads Methuselah has linked to? How long have you had Mint in the machine for? What else have you done to it?

I can't help but think the issue is something simple. Sorry if this post isn't helpful, I'm just trying to figure out where your up to and what has been "modified" on this current installation so I can offer advice that is useful.

---

### Post by k3lt01 on 2008-07-28
Here are a couple of links that may be of interest to you.

[http://www.arakhne.org/spip.php?rubrique31](http://www.arakhne.org/spip.php?rubrique31)
[http://wiki.mediati.org/Installation](http://wiki.mediati.org/Installation)
[https://answers.launchpad.net/ubuntu/+question/8416](https://answers.launchpad.net/ubuntu/+question/8416)

Have you got build-essentials installed?

---

### Post by halex on 2008-07-29
Sam forwarded me the message you sent him, so I'll attempt to help you here. :)

Here's the lines that are of value to us from your kernel log (specifically, the second line):
```
Jul 28 20:22:00 sabrecat-laptop kernel: [   29.192200] r5u870-0: Detected Sony VGP-VCC5
Jul 28 20:22:00 sabrecat-laptop kernel: [   29.651584] r5u870: probe of 5-6:1.0 failed with error -2
Jul 28 20:22:00 sabrecat-laptop kernel: [   29.651602] usbcore: registered new interface driver r5u870
```

Honestly, I haven't seen a bug report with this issue before.
-2 means ENOENT, or "no such file or directory". Could you make sure you've got the firmware files in the right place? (should be /lib/firmware)

---

### Post by halex on 2008-07-29
Heh, looks like Methuselah figured it out just before I did. :)

---

### Post by ChocolateChip_Wookie on 2008-07-29
Hello people,

First of all, thank you all very much for the time and effort you are investing in this problem for me. Some explanations, so you understand where I am comming from...

I bought the Vaio with Vista installed. I didnt have a choice in this and ever since I saw that the 'factory' install took up 65 gigs and 1gig of RAM, it's annoyed me. I just havnt had the courage to switch to Linux. I did try Linux years ago (about 8) but gave up with Redhat, I just wasnt good enough or had a big enough need to make the switch back to the command line. So, I have laboured at the Microsoft coal face for years and I think I am pretty expert with it. However, that doesnt amount to a hill of beans when it comes to Linux. Anyway, my Vista installation was becomming increasingly unstable so I decided to make the jump after doing some research online. I picked Ubuntu because it was the biggest and (I figured) probably the best supported and most complete with drivers, which equals the least amount of trouble. I dont mind trouble, but one thing at a time huh. So, I installed Ubuntu (Heron) and immediately liked it. There are some idiosycracies that I still havnt figured out but I am very willing to learn. 

So, with my shiny new install of Ubuntu 8, I set about 'learning' about the operating system. I did various things in Bash, learned how to change the colours etc. Nothing big. Just fooling really. Then I discovered that the cam didnt work. No problems, I started doing some research guessing (correctly) that it just needed some drivers. The instructions were a little confusing (especially to someone totally unfamiliar with the system) but I tried various things. That takes us up to last night. Deciding that perhaps I had messed something up in the current installation (I had as it turned out because it wouldnt boot last night, but that's another story) I decided to re-install a totally virgin (absolutely no messing around) copy of Mint. I know that Mint is based on the Ubuntu kernel so figured it would behave the same with the same file structure etc. I wanted to try Mint anyway and have found it to be very nice indeed. So, I installed it and all that I did was make a wireless connection so I could get online to this thread. No messing with Bash other than to follow (cookbook style) the instructions we had already established. That way, I thought that I would cut out the posibility of any user introduced wierdness interfering in the fault finding process. Does this all make sense?

Now, I detailed (in the previous posts) all my steps and what exactly I did. There is no way you can help me if I didnt follow your instructions to the letter.

However, final tests (just before bed) last night confirmed tha the cam still wasnt working, so I went looking for the log files that might offer some insight. I didnt understand all of it but hoped that someone here might spot what I am doing wrong and put me right. It was very possible I was missing some nuance of the operating system that was obvious to everyone else such as how to edit a file and save it with root permissions (figured it out by the way using Nautilus) I will go home again tonight and look for these new files that you have advised and report my findings to this thread.

Once again, thank you all very much for you help and time.

---

### Post by ChocolateChip_Wookie on 2008-07-29
> **halex said:**
> Sam forwarded me the message you sent him, so I'll attempt to help you here. :)



Is 'Sam' the gentleman I emailed with the request for his expertise and would you be Mr Hixon? I did get his email and he told me that HP have stopped him making any further changes to the drivers on the pretext that any further developments would be their intellectual property? I think that is thoroughly outragous myself. HP are trying to force people into using Windows by blocking development of third party drivers for Linux. Ordinary people are not going to use Linux if they hit the kinds of problems that I have experienced. I have allot of patience when it comes to this, but I cannot see a corporate entity sitting still for these kinds of difficulties. Plus, I WANT to learn, most ordinary people are challenged by the concept of attachments in emails and consider any change from Windows to be very frightening. I must admit that it has taken some years for me to actually pluck up the courage to do this myself. At the moment (even among IT professionals) Linux is still viewed as a geeky hobby, Windows is bad, Bill Gates owns the world, but at least it's the devil you know kind of thing. I'm disgusted by the behaviour of HP. I wish I could tell them that, or that they would give a damn anyway.

---

### Post by ChocolateChip_Wookie on 2008-07-29
OK. Here I am. I have just booted and just out of interest, I tried the webcam with Camorama just on the offchance. No joy. So that out of the way, lets get down to business...

Results of command uname -r :

2.6.24-16-generic

Results of command ls /lib/firmware :
2.6.24-16-generic (as above?)

Results of command ls /lib/firmware/<generic> :
```

acx                                 dvb-usb-vp7045-01.fw
aic94xx-seq.fw                      dvb-usb-wt220u-02.fw
atmel_at76c502_3com.bin             dvb-usb-wt220u-fc03.fw
atmel_at76c502_3com-wpa.bin         dvb-usb-wt220u-zl0353-01.fw
atmel_at76c502.bin                  ipw2100-1.3.fw
atmel_at76c502d.bin                 ipw2100-1.3-i.fw
atmel_at76c502d-wpa.bin             ipw2100-1.3-p.fw
atmel_at76c502e.bin                 ipw2200-bss.fw
atmel_at76c502e-wpa.bin             ipw2200-ibss.fw
atmel_at76c502-wpa.bin              ipw2200-sniffer.fw
atmel_at76c503-i3861.bin            isl3877
atmel_at76c503-i3863.bin            isl3886
atmel_at76c503-rfmd-0.90.2-140.bin  isl3887usb_bare
atmel_at76c503-rfmd-acc.bin         isl3890
atmel_at76c503-rfmd.bin             isl3890usb
atmel_at76c504_2958-wpa.bin         iwlwifi-3945-1.ucode
atmel_at76c504a_2958-wpa.bin        iwlwifi-3945.ucode
atmel_at76c504.bin                  iwlwifi-4965-1.ucode
atmel_at76c504c-wpa.bin             iwlwifi-4965.ucode
atmel_at76c505a-rfmd2958.bin        ql2100_fw.bin
atmel_at76c505-rfmd2958.bin         ql2200_fw.bin
atmel_at76c505-rfmd.bin             ql2300_fw.bin
atmel_at76c506.bin                  ql2322_fw.bin
atmel_at76c506-wpa.bin              ql2400_fw.bin
dvb-fe-or51132-qam.fw               rt2561.bin
dvb-fe-or51132-vsb.fw               rt2561s.bin
dvb-fe-or51211.fw                   rt2661.bin
dvb-fe-tda10046.fw                  rt73.bin
dvb-ttpci-01.fw                     v4l-cx2341x-dec.fw
dvb-usb-avertv-a800-02.fw           v4l-cx2341x-enc.fw
dvb-usb-bluebird-01.fw              v4l-cx2341x-init.mpg
dvb-usb-dib0700-1.10.fw             v4l-cx25840.fw
dvb-usb-dibusb-5.0.0.11.fw          v4l-pvrusb2-24xxx-01.fw
dvb-usb-dibusb-6.0.0.8.fw           v4l-pvrusb2-29xxx-01.fw
dvb-usb-dtt200u-01.fw               zd1201-ap.fw
dvb-usb-tvwalkert.fw                zd1201.fw
dvb-usb-umt-010-02.fw               zd1211
dvb-usb-vp702x-01.fw
```

So, it would seem that there are no files that look like the ones Methuselah has listed as needing to be present. If that is the case, what do I do to get them? Can anyone advise please?

When I followed the original instructions at [http://ubuntuforums.org/showthread.p...Driver&Page=22](http://ubuntuforums.org/showthread.p...Driver&Page=22) (Post 216), there was no mention of adding any firmware files. I sort of assumed that the installer would do that for you if necessary.

---

### Post by ChocolateChip_Wookie on 2008-07-29
Follow-up :

Having read the links in the previous posts, I downloaded the apropriate driver pack, unpacked it, extracted the files from the /lib/firmware directory and copied them into my own /lib/firmware/2.6.24-16-generic directory. Rebooted. Still no joy.

Here is the file list...

```
acx                                 ipw2100-1.3-p.fw
aic94xx-seq.fw                      ipw2200-bss.fw
atmel_at76c502_3com.bin             ipw2200-ibss.fw
atmel_at76c502_3com-wpa.bin         ipw2200-sniffer.fw
atmel_at76c502.bin                  isl3877
atmel_at76c502d.bin                 isl3886
atmel_at76c502d-wpa.bin             isl3887usb_bare
atmel_at76c502e.bin                 isl3890
atmel_at76c502e-wpa.bin             isl3890usb
atmel_at76c502-wpa.bin              iwlwifi-3945-1.ucode
atmel_at76c503-i3861.bin            iwlwifi-3945.ucode
atmel_at76c503-i3863.bin            iwlwifi-4965-1.ucode
atmel_at76c503-rfmd-0.90.2-140.bin  iwlwifi-4965.ucode
atmel_at76c503-rfmd-acc.bin         ql2100_fw.bin
atmel_at76c503-rfmd.bin             ql2200_fw.bin
atmel_at76c504_2958-wpa.bin         ql2300_fw.bin
atmel_at76c504a_2958-wpa.bin        ql2322_fw.bin
atmel_at76c504.bin                  ql2400_fw.bin
atmel_at76c504c-wpa.bin             r5u870_1810.fw
atmel_at76c505a-rfmd2958.bin        r5u870_1830.fw
atmel_at76c505-rfmd2958.bin         r5u870_1832.fw
atmel_at76c505-rfmd.bin             r5u870_1833.fw
atmel_at76c506.bin                  r5u870_1834.fw
atmel_at76c506-wpa.bin              r5u870_1835.fw
dvb-fe-or51132-qam.fw               r5u870_1836.fw
dvb-fe-or51132-vsb.fw               r5u870_1839.fw
dvb-fe-or51211.fw                   r5u870_183a.fw
dvb-fe-tda10046.fw                  r5u870_183b.fw
dvb-ttpci-01.fw                     r5u870_1870_1.fw
dvb-usb-avertv-a800-02.fw           r5u870_1870.fw
dvb-usb-bluebird-01.fw              rt2561.bin
dvb-usb-dib0700-1.10.fw             rt2561s.bin
dvb-usb-dibusb-5.0.0.11.fw          rt2661.bin
dvb-usb-dibusb-6.0.0.8.fw           rt73.bin
dvb-usb-dtt200u-01.fw               v4l-cx2341x-dec.fw
dvb-usb-tvwalkert.fw                v4l-cx2341x-enc.fw
dvb-usb-umt-010-02.fw               v4l-cx2341x-init.mpg
dvb-usb-vp702x-01.fw                v4l-cx25840.fw
dvb-usb-vp7045-01.fw                v4l-pvrusb2-24xxx-01.fw
dvb-usb-wt220u-02.fw                v4l-pvrusb2-29xxx-01.fw
dvb-usb-wt220u-fc03.fw              zd1201-ap.fw
dvb-usb-wt220u-zl0353-01.fw         zd1201.fw
ipw2100-1.3.fw                      zd1211
ipw2100-1.3-i.fw
```

I'm stuck. What else do I do now?

---

### Post by ChocolateChip_Wookie on 2008-07-29
Further update...

After messing around for a bit, I decided to install the package again but via [http://wiki.mediati.org/Installation](http://wiki.mediati.org/Installation) instead.

SUCCESS! DELIGHT!

However, Camorama doesnt work and neither does aMSN. Wierdly, Skype does. Anyway, I have SOME video so I guess beggers cant be choosers. Anyone have any ideas? Should I re-install sMSN?

---

### Post by ChocolateChip_Wookie on 2008-07-29
More updates...

MSN Video chat now working (sort of, going light and dark and very pixellated) but no sound?

---

### Post by ChocolateChip_Wookie on 2008-07-29
Update :

After a reboot:

Skype reports the webcam is a UVC Camera (05ca:1835), the picture is grainy and black and white. So near and yet so far! I seem to have lost the Ricoh drivers (again!). What is going on!

---

### Post by ChocolateChip_Wookie on 2008-07-29
Update :

I tried reloading the driver from the package and now I've lost the bloody web cam again!

Why wont the drivers stay in memory? It's really not practical to re-install the package every time I want to use the webcam? What am I doing wrong? I had it working!

---

### Post by ChocolateChip_Wookie on 2008-07-29
Update :

After another reboot, I get the UVC cam back again in Skype which is black and white/grainy. So, at least I have a camera. I know that Skype was recognising a colour camera (although it was going light and dark) but now it isnt (again!). Can anyone advise me? How do I get the drivers to 'stick'!

---

### Post by Methuselah on 2008-07-29
[Sorry I was away for a while]

Great, you've made much progress!
I applaud your persistence. =D>
I think you're a latent 'hacker'...heh
[In this sense: [http://www.catb.org/jargon/html/H/hacker.html]](http://www.catb.org/jargon/html/H/hacker.html])

So, as suspected, the firmware was part of the problem.
It was missing from the location the driver expected.

Why the changes might not be sticking after reboot goes back to what I was telling you in an earlier post.
The modprobe and rmmod commands insert the driver modules into the running operating system so that when you reboot it reverts to the default configuration.

Check your /etc/modules file.
This file instructs the OS which modules to load at boot.
It'll execute the modprobe commands on the modules in that file automatically at boot up.

Mine looks like:

> 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc


Now that you know the driver works, you can set your system to always load the r5u870  modules and its dependencies.

So add the following lines to etc/modules if you haven't already done so:

r5u870
videodev
video-buf
v4l1-compat
v4l2-common 

It's just a module name on each line.

The site [http://wiki.mediati.org/Installation](http://wiki.mediati.org/Installation) also mentions the compat_ioctl32 module if you're running 64bit but I'd hold off on that unless there are issues.
[I mean, whatever you did at post 50 obviously worked so whatever modules you had set up then were right]

Additionally, you DON'T want to load uvcvideo and it seems to be loaded automatically so you'll have to **blacklist** it.
[This might be the biggest issue you're facing since uvcvideo seems to be grabbing the camera instead of r5u870 and not doing a very good job with it]
To blacklist uvcvideo, edit /etc/modprobe.d/blacklist and add the line:
blacklist uvcvideo

We avoided doing all this when you were testing the drivers because it would be a pain to keep changing these files and rebooting to see if it worked.

Now reboot and see if everything's OK.
Right after reboot, lsmod shouldn't list uvcvideo but the r5u870 should be listed and the cam should work.
You should be on autopilot now.

---

### Post by k3lt01 on 2008-07-30
Choc, Sorry about Camorama it wont work with that camera or driver setup, I found that out this morning but got called to work before I could post it here for you.

There seems to be quite a few programs that don't work with that setup for some reason or another, so trial and error is the only way you'll find what programs work and what ones don't. Having said that you know Skype works to a certain extent.

---

### Post by ChocolateChip_Wookie on 2008-07-30
Thanks for the information k3lt01. The good news is that Skype works perfectly but I wouldnt use MSN if you are epileptic because it keeps flickering light and dark for some reason. I think this is to do with the driver not playing nicely but who knows for sure. The bottom line I have learned from all of this is to download the package myself and put the drivers in the apropriate directory by hand because the installer I used doesnt appear to put things in the right place - hence the reason the fw files were missing. Video is problematic at best so we have done very well to get it working at all. Kudos all round for creating the drivers in the first place.

---

### Post by ChocolateChip_Wookie on 2008-07-30
> **Methuselah said:**
> Sorry I was away for a while

Not a problem. You gave me a shove in the right direction and I was able to figure it out from there.

> **Methuselah said:**
> Great, you've made much progress!

But boy have I learned some new stuff in the last few days

> **Methuselah said:**
> I applaud your persistence. =D> 

"Oh GOD! Not her again, hasnt she fixed the bloody cam yet!" :-)

> **Methuselah said:**
> I think you're a latent 'hacker'...heh
[In this sense: [http://www.catb.org/jargon/html/H/hacker.html]](http://www.catb.org/jargon/html/H/hacker.html])


So buying [http://www.amazon.co.uk/Hacking-Ubuntu-Serious-Customizations-ExtremeTech/dp/047010872X/ref=sr_1_1?ie=UTF8&s=books&qid=1217426588&sr=8-1]("http://www.amazon.co.uk/Hacking-Ubuntu-Serious-Customizations-ExtremeTech/dp/047010872X/ref=sr_1_1?ie=UTF8&s=books&qid=1217426588&sr=8-1") book last night would be in keeping then...

But seriously that's probably the nicest thing anyone has ever said to me. Yes, I do love to learn and play. I am a programmer by trade and in my younger days, I may have done one or two slightly illegal things to other people's computers but that's how I learned all that I know. Back in the early days of 3.11, I used to break my computer at least once a week. Unfortuntely, whilst Linux behaves in a similar manner to Windows, it is not the same (thank god) so all my experience is for nothing when it comes to trying to solve this little problem.

> **Methuselah said:**
> So, as suspected, the firmware was part of the problem.
Yeah! It was missing from the installer! Once I unpacked the files and saved them to the apropriate directory, Bob's your mothers brother. It works.
> **Methuselah said:**
> It was missing from the location the driver expected. 
Yep. For anyone reading this...dont use this link (.[http://ubuntuforums.org/showthread.p...Driver&page=22](http://ubuntuforums.org/showthread.p...Driver&page=22)) Use this one instead...([http://www.arakhne.org/spip.php?rubrique31](http://www.arakhne.org/spip.php?rubrique31))

> **Methuselah said:**
> Why the changes might not be sticking after reboot goes back to what I was telling you in an earlier post.
The modprobe and rmmod commands insert the driver modules into the running operating system so that when you reboot it reverts to the default configuration.

Check your /etc/modules file.
This file instructs the OS which modules to load at boot.
It'll execute the modprobe commands on the modules in that file automatically at boot up.

Ah ha! Got it now.


> **Methuselah said:**
> Additionally, you DON'T want to load uvcvideo and it seems to be loaded automatically so you'll have to **blacklist** it.
[This might be the biggest issue you're facing since uvcvideo seems to be grabbing the camera instead of r5u870 and not doing a very good job with it]
To blacklist uvcvideo, edit /etc/modprobe.d/blacklist and add the line:
blacklist uvcvideo

I knew about the white list and had added the drivers to that (a couple of pages ago) but the blacklist is new. Thanks for letting me know about that. The file has been updated as per your advice.


> **Methuselah said:**
> Now reboot and see if everything's OK.
Right after reboot, lsmod shouldn't list uvcvideo but the r5u870 should be listed and the cam should work.
You should be on autopilot now.

MSN keeps going light and dark but Skype seems to be working. Additionally, I even managed to get the internal mic working as well!

Well, I guess this is it. Thanks for all your help Methuselah. Hope to see you around. I'm sure I'll break this installation and have to ask another question or two before I get it working again...

---

### Post by ChocolateChip_Wookie on 2008-07-30
So, for anyone finding this thread, this is how you install the correct drivers for the built in Ricoh Web Cam

1) Find out what camera version you are using
	type : lsusb


2) Get these files...

[http://www.arakhne.org/spip.php?rubrique31](http://www.arakhne.org/spip.php?rubrique31)
[http://wiki.mediati.org/Installation](http://wiki.mediati.org/Installation)
[https://answers.launchpad.net/ubuntu/+question/8416](https://answers.launchpad.net/ubuntu/+question/8416)

3) Find the correct driver for the installation :

	type : uname -r


4) Unpack the correct driver and save the .fw (firmware) files to the correct directory /lib/firmware/<genericname>
	type : Alt+F2
	type : gksudo nautilus /lib/firmware (this opens the correct directory)

5) Add the drivers to the white list (loaded at boot)
	type : Alt+F2
	type : gksudo nautilus /etc/modules
	Add these files : r5u870
			videodev
			video-buf
			v4l1-compat
			v4l2-common

6) Type the following to load the drivers into memory
	type : sudo modprobe r5u870 

7) Remove the usb cam from the driver list
	type : sudo rmmod uvcvideo

8) Add this line to the blacklist (killed at boot)
	type : Alt+f2
	type : gksudo nautilus /etc/modprobe.d/blacklist
	Add this line : blacklist uvcvideo

9) After reboot, type the following. You should see the correct video drivers listed and not see the uvcvideo listed
	type : lsmod

---

### Post by Methuselah on 2008-07-30
Congrats ChocolateChip_Wookie!
I'm glad it's working to some reasonable extent now!

I read through your new posts:
I could tell you were someone who doesn't give up easily so I bookmarked this thread and always checked back to see how you were doing.
You'll definitely have a lot to learn and a lot of playing to do on Linux.
Furthermore, with the OS designed as it is, you can avoid hurting yourself too badly most of the time.

By the way, there is a program named 'Cheese' that I have played with before (which seems similar to camorama which I heard about the first time here) that also allows you to add little effects to the webcam output. 
Cheese is actually part of the newer Gnome Desktops.
It's not installed in Hardy but available in Add/Remove.

Anyway, enjoy your laptop and hopefully the drivers continue to improve!

---

### Post by ChocolateChip_Wookie on 2008-07-30
Thanks for your time and efforts.

By the way, I think that this thread might be useful to other vaio users. Is there any way to make this part of a FAQ or a Sticky? I have also noticed (reading the forum) that the same questions are asked over and over, particularly about themes, icons etc. Perhaps a quick FAQ on these subjects along with some basic BASH might be in order, such as saving files, moving files etc? Most of us are ex-windows users and are new to the concept of being locked out of our own systems unless we use an easoteric command line code to access it. Does this already exist? I understand the purpose of the security, but sometimes it really is a pain. It cost me the best part of an hour to figure out how to edit the whitelist file the first time...

---

