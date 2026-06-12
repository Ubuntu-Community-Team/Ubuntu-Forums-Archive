---
title: "Wireless connection problems"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by Spops on 2008-07-31
Hi everyone,

I have a Dell computer that has a Dell Wireless 1450 USB Adapter.  About half of the time when I start up Ubuntu my wireless connects and works fine.  The other half it will not connect at all.  

When I click on the Network Icon it lists my network and when I click on it, it asks me to enter in the WEP key again.  I go ahead and do that, the network icon starts to spin and than it does not connect.  Than sometimes when I click on the network again it will connect.  Once I do finally get it connected it will constantly disconnect from the network.  Is there maybe a specific driver that I need to get this to work properly for Linux?  I did a google search but I did not find anything specific to Ubuntu.  

I need to make sure that it connects every time with out any problems.  If you want to laugh, I have Ubuntu on this computer for my stepfather.  He screws up windows every chance he gets by downloading crap he should not.  We have a 2 year subscription for Mcafee virus scan for windows.  He once saw something on a website that said free virus scan software.  So he clicked on it and got us a few virus's.  Let's just say it was not a pretty picture.

All he uses is Firefox and Youtube so I put him on Ubuntu so he really can not mess anything up.  He will have no clue how to install anything on here, and I want to keep it like that :)  Hell if he does screw anything up I can just delete Ubuntu and reinstall it lol

Anyways please help me out...Thanks!!!

---

### Post by Spops on 2008-07-31
Just an update.

I put the instalation CD in.  When I open it up it has a folder for Linux.  Once in the Linux folder I click on the folder that says 1450ENG.  Inside are 3 files

Linux.htm
Prism-modules-2.4.20-8.dkms 1.07.i686.rpm
Prism-modules-2.4.21-4.EL.dkms 1.07.i686.rpm

When I click on the Prism-modules packages and hit run in terminal, it tells me:  "Archive type not supported"

---

### Post by jualin on 2008-07-31
RPM (Red Hat Package) cannot be use with Ubuntu. Ubuntu uses (.deb) packages. Since the linux drivers are available try searching for them online. If you find a source (.tar) or (.bin) you can make it work under Ubuntu.

---

### Post by Spops on 2008-07-31
> **jualin said:**
> RPM (Red Hat Package) cannot be use with Ubuntu. Ubuntu uses (.deb) packages. Since the linux drivers are available try searching for them online. If you find a source (.tar) or (.bin) you can make it work under Ubuntu.

Any clue on what is the best way to search for them?  I am fairly new to Linux

---

### Post by jualin on 2008-07-31
You can also try using Ndiswrapper which lets you use the Windows driver in Linux. You can install ndiswrapper using Synaptic or using the terminal > sudo apt-get install ndiswrapper-common ndisgtk And then just look for the "Windows Wireless Drivers" under System, Administration and just select the Windows driver. Hope this help

---

### Post by tashmooclam on 2008-07-31
Check if the wireless card is supported by Ubuntu/Linux. There are posts here about: terminal command to list equipment. Then, my suggestion (not the usual one) is get a wireless card that works "out of the box" in Ubuntu/Linux. Intel is an example, there must be others. Sorry for not making a great answer, but I'm no expert. I just swapped out my Dell laptop wireless card when I had problems.

---

### Post by jualin on 2008-07-31
Write this in the terminal and post the results > lspci
lsusb

---

### Post by Spops on 2008-07-31
> **jualin said:**
> Write this in the terminal and post the results

lspci:

administrator@administrator-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:01.0 Communication controller: Conexant HSF 56k Data/Fax Modem
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
administrator@administrator-desktop:~$ 


lsusb:

administrator@administrator-desktop:~$ lsusb
Bus 004 Device 003: ID 413c:5601 Dell Computer Corp. 
Bus 004 Device 002: ID 413c:8104 Dell Computer Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
administrator@administrator-desktop:~$

---

### Post by jualin on 2008-07-31
Apparently Ndiswrapper [supports your card]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/"). Install Ndiswrapper and try installing the Windows XP driver found on the CD that the Adapter brought.

---

### Post by Spops on 2008-07-31
> **jualin said:**
> Apparently Ndiswrapper [supports your card]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/"). Install Ndiswrapper and try installing the Windows XP driver found on the CD that the Adapter brought.

Would it just be any of the .inf files?  I kept looking around for a .inf file, and I think I set it up.  I didn't get any thing that showed it was installing or anything.  But now under the Ndiswrapper windows it shows:

Wireless Network Drivers:

dellnic
Hardware present:  Yes

So is it installed properly now?  How can I check?

---

### Post by jualin on 2008-07-31
Ok, it seems like it installed correctly now you need to check in the terminal that the driver is installed and then load the ndiswrapper module every time your computer boots up. type > ndiswrapper -l to list the status of the ndiswrapper module and if you see the "Driver Installed" comment then just load the module using > modprobe ndiswrapper Then try to connect to a network, hope this helps!

---

### Post by jualin on 2008-07-31
You can also follow [this tutorial]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Load%20the%20new%20driver%20module") which you can pretty much skip some steps since you already installed the driver and you are only missing connecting to the network and loading Ndiswrapper every time the computer starts.

---

### Post by Spops on 2008-07-31
> **jualin said:**
> Ok, it seems like it installed correctly now you need to check in the terminal that the driver is installed and then load the ndiswrapper module every time your computer boots up. type  to list the status of the ndiswrapper module and if you see the "Driver Installed" comment then just load the module using  Then try to connect to a network, hope this helps!

Nidswrapper -l
Dellnic :  driver installed
device 413C:8104) present (alternate driver: p54usb)

When I type in modprobe ndiswrapper nothing happens, it just brings me to another command line.

Is it necessary to type these commands in every single time Ubuntu boots up?  I am trying to make this very simple for my stepfather who is very computer illiterate.

---

### Post by jualin on 2008-07-31
When you typed modprobe ndiswrapper you told your computer to start the Ndiswrapper module so no receiving an output is totally normal. You can check that the module loaded by typing > lsmod and looking for Ndiswrapper on the list. Follow the link I gave you on my last post to make ndiswrapper load automatically. You can follow everything from [step 3.5]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Load%20the%20new%20driver%20module"). Hope this helps!

---

### Post by Spops on 2008-07-31
> **jualin said:**
> When you typed modprobe ndiswrapper you told your computer to start the Ndiswrapper module so no receiving an output is totally normal. You can check that the module loaded by typing  and looking for Ndiswrapper on the list. Follow the link I gave you on my last post to make ndiswrapper load automatically. You can follow everything from [step 3.5]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Load%20the%20new%20driver%20module"). Hope this helps!

Ah, loading automatically will be awesome.  Like I said I need to keep everything very very simple for him.  i.e. start computer, pick Ubuntu, click on firefox lol

Thanks again, I'll let you know if I run into any trouble with that tutorial on setting it up automatically

---

### Post by jualin on 2008-07-31
Feel free to ask anything. Greetings from Miami, Florida

---

### Post by Spops on 2008-07-31
I just tried to do this step:

> 3.7. Automatically loading at start-up

If everything works, you need to tell your system to load the module when the system starts-up. Depending on the method of network manager you are using, will require a different setup

    * Configure ndiswrapper for use with the Network Admin settings - this adds an Alias to associate wlan0 to ndiswrapper in modprobe.d
          

              sudo ndiswrapper -m

When I do, I get the following message:

> module configuration already contains alias directive

Does that mean it is already setup to run at startup?

---

### Post by jualin on 2008-07-31
I think so. You can always check if the module was loaded by running > lsmod when you turn on the computer again. The **lsmod** command will list (**ls**) all of the modules (**mod** part) that the computer is running right now.

---

### Post by Spops on 2008-07-31
> **jualin said:**
> I think so. You can always check if the module was loaded by running  when you turn on the computer again. The **lsmod** command will list (**ls**) all of the modules (**mod** part) that the computer is running right now.

Not sure what I am looking for so here is a copy and paste:

> administrator@administrator-desktop:~$ lsmod
Module                  Size  Used by
af_packet              23812  4 
ipv6                  267780  8 
i915                   32512  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  0 
cpufreq_stats           7104  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
video                  19856  0 
output                  4736  1 video
dock                   11280  0 
container               5632  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
lp                     12324  0 
usblp                  15872  0 
ndiswrapper           192920  0 
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
evdev                  13056  3 
dcdbas                  9504  0 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
serio_raw               7940  0 
snd_seq_dummy           4868  0 
psmouse                40336  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
button                  9232  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
pcspkr                  4224  0 
intel_agp              25492  1 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
agpgart                34760  3 drm,intel_agp
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
loop                   18948  2 
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  2 
ata_piix               19588  1 
ata_generic             8324  0 
floppy                 59588  0 
pata_acpi               8320  0 
e100                   37388  0 
mii                     6400  1 e100
libata                159344  3 ata_piix,ata_generic,pata_acpi
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  5 usblp,ndiswrapper,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  5 
administrator@administrator-desktop:~$ 


---

### Post by jualin on 2008-07-31
You are looking for **Ndiswrapper** so I am guessing that it's working cause you have it on the list **ndiswrapper 192920**.

---

### Post by Spops on 2008-07-31
> **jualin said:**
> You are looking for **Ndiswrapper** so I am guessing that it's working cause you have it on the list **ndiswrapper 192920**.

Thanks so much, you have been a huge help :)

---

### Post by jualin on 2008-07-31
Anytime dude!

---

