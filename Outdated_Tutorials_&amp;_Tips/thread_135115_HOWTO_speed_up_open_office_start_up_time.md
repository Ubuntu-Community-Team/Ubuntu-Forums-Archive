---
title: "HOWTO: speed up open office start up time"
date: 2006-02-23
forum: Outdated Tutorials &amp; Tips
---

### Post by Karlos on 2006-02-23
As you may know open office takes about 4 days to start up.
To fix this open up open office.
go Tools > Options > Memory
There you will find a section labelled graphics cache
I changed my 'use for open office.org' to 32mb
and my 'memory per object' to 2.0
and now it opens in about a quarter of the time it did before (1 day .. lol)
give it a go see if it works 
you could always change it back if it don't
or ...
try some settings of your own (you might find a better one .. if you do let me know .. and everybody else)
ciaow .. Karlos\\:D/

---

### Post by welsh_spud on 2006-02-24
Works well. Good find!

---

### Post by majikstreet on 2006-02-24
try prelink too :D

---

### Post by funxgentoo on 2006-02-24
from gentoo forums...

---

### Post by bfonseca on 2006-02-24
When I first start up my computer it gets past the kernel and then looks like it freezes, but then goes stright to the splash screen.  It starts up fine but I think I am having issues with drivers also. Does anyone know the problem with the bootup process.  It is driving me bonkers, I have tried alot of different things but none seem to work.
When I do a lsmod I get:

[PHP]Module                  Size  Used by
radeon                108832  1
drm                    72852  2 radeon
ipt_TCPMSS              4608  1
ipt_limit               2432  8
ip_nat_irc              2688  0
ip_nat_ftp              3328  0
iptable_nat             7812  1
iptable_mangle          2944  0
ipt_LOG                 6912  8
ipt_MASQUERADE          3456  1
ip_nat                 19628  4 ip_nat_irc,ip_nat_ftp,iptable_nat,ipt_MASQUERADEipt_TOS                 2560  0
ipt_REJECT              5632  1
ip_conntrack_irc        6768  1 ip_nat_irc
ip_conntrack_ftp        7792  1 ip_nat_ftp
ipt_state               2048  8
ip_conntrack           51500  8 ip_nat_irc,ip_nat_ftp,iptable_nat,ipt_MASQUERADE,ip_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
nfnetlink               6552  2 ip_nat,ip_conntrack
iptable_filter          3072  1
ip_tables              22400  10 ipt_TCPMSS,ipt_limit,iptable_nat,iptable_mangle,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
speedstep_lib           4484  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
ipv6                  265600  10
reiserfs              268144  1
af_packet              22920  2
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51984  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25220  1 snd_seq
lp                     11844  0
rsrc_nonstatic         13440  0
pcmcia_core            42640  1 rsrc_nonstatic
tsdev                   8000  0
snd_mpu401              6728  0
snd_mpu401_uart         7680  1 snd_mpu401
snd_rawmidi            25504  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8716  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
analog                 12320  0
gameport               15496  1 analog
floppy                 62148  0
snd                    55268  7 snd_seq_oss,snd_seq,snd_timer,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device
parport_pc             35780  1
parport                36296  2 lp,parport_pc
rtc                    13492  0
pcspkr                  2180  0
via_rhine              23940  0
mii                     5888  1 via_rhine
i2c_viapro              8980  0
psmouse                36100  0
serio_raw               7300  0
em8300                 57152  0
i2c_algo_bit            9608  1 em8300
i2c_core               21904  2 i2c_viapro,i2c_algo_bit
soundcore              10208  2 snd,em8300
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
via_agp                 9856  1
agpgart                34888  2 drm,via_agp
sg                     37920  0
evdev                   9856  1
ext3                  135688  1
jbd                    58772  1 ext3
ehci_hcd               32520  0
uhci_hcd               33680  0
ohci_hcd               21892  0
usbcore               129668  4 ehci_hcd,uhci_hcd,ohci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  0
via82cxxx               9988  0 [permanent]
sd_mod                 19984  4
generic                 5124  0
sata_via                9092  3
libata                 61704  1 sata_via
scsi_mod              138856  3 sg,sd_mod,libata
processor              23360  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13448  1
cfbcopyarea             3968  1 vga16fb
vgastate               10368  1 vga16fb
cfbimgblt               3200  1 vga16fb
cfbfillrect             4352  1 vga16fb
fbcon                  42784  70
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit
[/PHP]
Is there something booting up that is preventing my bootup process to act the way it is acting.  I get a modprobe Error running install command for snd_via 82xx error.  Could this have something to do with my bootup process? My computer seems like it is going to freeze also when I shutdown too. When I run linuxinfo i get:

[PHP]Linux goofy33 2.6.15-16-386 #1 PREEMPT Mon Feb 20 16:38:26 UTC 2006
One Intel Unknown 2983MHz processor, 5972.58 total bogomips, 511M RAM
System library 2.3.6[/PHP]

and when I run X -version I get:

[PHP]
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux goofy33 2.6.15-16-386 #1 PREEMPT Mon Feb 20 16:38:26 UTC 2006 i686
Build Date: 21 December 2005
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
[/PHP]

Can someone please help me. I know that dapper is still in its beginning stages and that problems come with it but as anyone been where I am at before and fixed it or does anyone have any idea of what I can try. Oh and for some odd reason the X server is not recognizing my video card. I have to manually tell it what to use. I have a PowerColor Radeon 9250 128mb and for some reason my refresh rate stinks. Could this be the problem with my bootup and shut down process? The specs say it should support 2048x1536 @ 85 Hz but corrently I am running 1280x1024 @ 60Hz. Does anyone know how I can improve this. 
As you all can see I have it bad, but other then these things my computer is running fine, oh and if I didn't mention this before my computer doesnt recognize my sound card either. Could dapper have some problem with drivers?

Brian

---

### Post by bfonseca on 2006-02-24
oops sorry didnt mean to put it here. meant to start my own thread. :D

---

### Post by aktiwers on 2008-02-07
Also Tools => Options => Java
And then Disable "_U_se Java runtime environment" 

Helps a lot.

---

### Post by jesusfreak107 on 2008-02-07
How is this done in Xubuntu?

---

### Post by BobLand on 2008-02-07
Aktiwers,
That trick works great!

Thanks,
bobland

---

### Post by Ptero-4 on 2008-02-07
Jesusfreak. In Xubuntu you don't get openoffice by default (that's IIRC). But if you installed it the steps are the same explained a few posts above me.

---

