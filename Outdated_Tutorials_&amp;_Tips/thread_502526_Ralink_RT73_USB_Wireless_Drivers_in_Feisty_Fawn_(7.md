---
title: "Ralink RT73 USB Wireless Drivers in Feisty Fawn (7.04)"
date: 2007-07-16
forum: Outdated Tutorials &amp; Tips
---

### Post by webcrawler42 on 2007-07-16
This guide uses p_larbigs's drivers instead of the serialmonkey drivers because p_larbigs's are based off of the serialmonkey drivers, but have been already patched for Fragmentation Attacks and Injection, so you can utilize more features in Aircrack.

The wireless card I tested this on is an Alfa AWUS036S, the system I tested this on is a clean install of Ubuntu Feisty Fawn 7.04 with all updates as of 7/4/07.
[B]
Remove the old drivers[/B]
```
cd /lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/
sudo rm -r rt2x00
sudo rm -r rt2x00-legacy/
```**Get the new drivers and install them**
Download [http://homepages.tu-darmstadt.de/~p_larbig/wlan/rt73-k2wrlz-1.1.0.tar.bz2]("http://homepages.tu-darmstadt.de/%7Ep_larbig/wlan/rt73-k2wrlz-1.1.0.tar.bz2") and extract it to your desktop.
```
cd Desktop/rt73-k2wrlz-1.1.0/Module/
sudo make
sudo strip -S rt73.ko
    (before 2.7MB after 242k)
sudo make install
```**Bring the device up**```

sudo ifconfig rausb0 up
```The RT73 drivers do not support the network manager, so you need to remove it and install RutilT, which I like better anyways.

**Download and install RutilT**
Download [http://cbbk.free.fr/bonrom/?download=RutilTv0.15.tar.gz](http://cbbk.free.fr/bonrom/?download=RutilTv0.15.tar.gz) and extract it to your desktop.
```
sudo apt-get install libgtk2.0-dev g++
cd Desktop/RutilTv0.15/
./configure.sh --launcher=external
sudo make
sudo make install

```

[B]
Remove network-manager[/B]```

sudo apt-get remove network-manager
```

**If you want rausb0 brought up when you start ubuntu**

```
sudo gedit /etc/network/interfaces
     auto rausb0
     iface rausb0 inet dhcp
```

**If you want RutilT to start with Ubuntu**

System>Preferences>Sessions>New>
[INDENT]Name:rutilt, Command:rutilt[/INDENT]

If you don't want to see RutilT window every time Ubuntu starts up, inside RutilT check the box next to "Start hidden in tray".

*Just a note, you click on tray icon to show/hide the RutilT window.

**Getting Kismet Configured**
```
sudo gedit /etc/kismet/kismet.conf
     #suiduser=(your user name)
     source=rt2500,rausb0,RT73
```

---

### Post by bmartin on 2007-07-19
This almost worked for me. The driver is detected and the wireless works... for a short while. I started downloading my Ubuntu updates (from a new install) and the wireless suddenly stopped working altogether. Even during normal browsing, the wireless abruptly ceases to function. Do you know what might cause this to happen? ifconfig shows that all packets are being dropped after a certain point and using any program to attempt to reconnect to the wireless network fails.

---

### Post by webcrawler42 on 2007-07-19
Are you using Network-Manager or RutilT?

---

### Post by bmartin on 2007-07-19
I fixed it. It had something to do with the ehci_hcd module; I simply removed it.

I was using RutilT and Edgy. RutilT is pretty cool; I like it better than any other WiFi program I've seen. Thanks for the help!

---

### Post by webcrawler42 on 2007-07-20
No problem, glad I could help.

---

### Post by Delirious on 2007-08-09
thanks for the tutorial!

I had the serial monkey drivers install previously followed the instructions to remove them and install the new ones and they work great, except when doing an arp inject i get: 

Read 5842 packets (got 0 ARP requests), sent 0 packets...(0 pps)

so it seems injection still isnt working :(

any suggestions?

---

### Post by webcrawler42 on 2007-08-09
Are you fakeauth with the network? and are you sure that a arp request has been captured?(pretty sure its needed before you start injecting)

---

### Post by larynx on 2007-09-16
I went through the instructions without getting any error messages but when I run aireplay-ng to do an injection test on my wireless I get "No Answer..." in response.

What is the problem?

Thanks in advance...

---

### Post by kzu on 2007-09-25
I'll get an "rausb0: ERROR while getting interface flags: No such device" when trying to bring rausb0 up :( What to do ? One another thing, what is that Kismet thing? Can't configure it anyways...

---

### Post by Bachstelze on 2007-09-25
Are you sure your interface is called rausb0 ? What does *sudo iwconfig* tell you ?

---

### Post by dan_hurst on 2007-10-02
Hi, 
thanks for the guide, I've been messing around for ages trying to get my Sitecom WL-113 usb wifi working.  I tried for ages but couldn't get the DHCP to give me an IP address even though iwconfig reported the correct mac address of the router I was trying to connect to.  

Anyway, following your guide worked wonders and now everything seems to be working but I still have one question.  I put the command "rutilt -tp MY_ROUTER" in the startup programs list (System->Preferences->sessions) to bring up the connection automatically, but when I log on and the command is executed I have to put in my root/sudo/admin (whatever its called) password.  Is there a way of making it not ask me for my password every time I log on?

Thanks again, great guide, although it may be worth pointing out that once I removed network-manager I couldn't go online to download RutilT without manually bringing up the wired connection again.  It may be better download RutilT before removing network-manager :-)

---

### Post by webcrawler42 on 2007-10-02
You can, it involves visudo, I've done it before, google a guide.

Good call on the order of operations, thanks.

---

### Post by panchofmx on 2007-10-12
Fist post.

i just got my  new ALFA AWUS036s USB Wireless.
my laptop is an Apple iBook G3/300 (Original/Clamshell).
at the moment im updateing my Ubuntu 7.04 (Feisty Fawn PowerPC) to run my NEW USB CARD JUST FINE ( I HOPE :)  )

i try to use the usb wireless with  the non update ubuntu the system stop runing,
after updateing it will be fine i hope again and
next step is install the wireless drives.

some one have try to do this on a powerpc system?

---

### Post by panchofmx on 2007-10-13
Hi again.

i need some help 2 configure.


#: iwconfig wlan0

wlan0     RT73 WLAN  ESSID:""  
          Mode:Monitor  Frequency=2.447 GHz  Bit Rate:54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Thats ok???

also 
 
~$ lsmod

Module                  Size  Used by
rt73usb                37984  0 
rt2x00lib              13088  1 rt73usb
mac80211              202404  2 rt73usb,rt2x00lib
cfg80211               25840  1 mac80211
crc_itu_t               2080  1 rt73usb
rt2570                205672  0 
rt73                  343444  0 
ppp_deflate             7296  0 
zlib_deflate           21768  1 ppp_deflate
bsd_comp                6752  0 
ppp_async              13824  1 
crc_ccitt               2048  1 ppp_async
ppp_generic            33300  7 ppp_deflate,bsd_comp,ppp_async
slhc                    6848  1 ppp_generic
isofs                  40888  1 
udf                    96164  0 
binfmt_misc            13672  1 
uinput                 11264  2 
ipv6                  307884  10 
cpufreq_userspace       5332  0 
cpufreq_ondemand        9160  0 
cpufreq_conservative     8096  0 
cpufreq_stats           6436  0 
cpufreq_powersave       2048  0 
snd_powermac           49984  1 
apm_emu                 8012  1 
snd_aoa_i2sbus         24292  0 
snd_pcm_oss            53984  0 
snd_mixer_oss          20960  1 snd_pcm_oss
snd_pcm                95812  3 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss
snd_page_alloc         11368  1 snd_pcm
snd_seq_dummy           4004  0 
snd_seq_oss            40660  0 
snd_seq_midi           10016  0 
snd_rawmidi            29632  1 snd_seq_midi
snd_seq_midi_event      8192  2 snd_seq_oss,snd_seq_midi
snd_seq                61888  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26404  2 snd_pcm,snd_seq
snd_seq_device          9388  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    69812  12 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8996  1 snd
pmac_zilog             21140  2 
serial_core            24384  1 pmac_zilog
snd_aoa_soundbus        7812  1 snd_aoa_i2sbus
uninorth_agp           12012  1 
agpgart                41308  1 uninorth_agp
af_packet              24936  4 
tsdev                   9056  0 
evdev                  12800  16 
ext3                  159048  2 
jbd                    68488  1 ext3
mbcache                 9572  1 ext3
ide_cd                 36900  1 
cdrom                  47580  1 ide_cd
ide_disk               18880  3 
sungem                 35460  0 
sungem_phy             12128  1 sungem
ohci_hcd               36100  0 
usbcore               158228  5 rt73usb,rt2570,rt73,ohci_hcd
dm_mod                 67468  5 
capability              5256  0 
commoncap               7968  1 capability


i have to delete some rt73usb ??? are the old ones??

---

### Post by Scotty562 on 2007-11-02
Does this work with gutsy? Or is there an easier way to get it to work with gutsy? I don't want to remove the network-manager if I don't have to.

---

### Post by Bachstelze on 2007-11-02
My RT73 wifi stick works perfectly out of the box in Gutsy with the rt73usb driver. Don't know about NetworkManager though, I never use it.

---

### Post by panchofmx on 2007-11-03
i got it i delate the old rt* modules and install the new drivers.
it work.  but a cant get packets with aircrack.

i got a ibook g3 300 ppc. wireless USB  AWUSO36s.

trying to get the corret drives for a ppc machines.

ENY IDEAS?

---

### Post by n00bek on 2007-11-05
plz update driver for gusty

---

### Post by panchofmx on 2007-11-06
Downloading ubuntu 7.10 ppc. for my ibook 300

i hoppe  rt73usb on ubuntu 7.10 it work fine on my AWUSO36s.

---

### Post by Bachstelze on 2007-11-06
> **n00bek said:**
> plz update driver for gusty

You don't need this driver for Gutsy, your stick will work just out of the box.

---

### Post by Scotty562 on 2007-11-08
> **HymnToLife said:**
> You don't need this driver for Gutsy, your stick will work just out of the box.

When you say "work out of the box" do you mean work with Network Manager, or just be recognized in gutsy? Gutsy recognizes my card and I can use it with aircrack-ng, but it doesn't work with network manager. I'm not about to remove it either :).

---

### Post by Bachstelze on 2007-11-08
Well, I never use NetworkManager but I can tell you for certain that it works for connecting to networks...

---

### Post by UncoElite on 2007-12-05
My D-Link DWL-G122 Rev. C1 works out of the box for Gutsy using it's rt73usb drivers. Works with NetworkManager too. The drivers naturally aren't patched for injection though. So you may still want to follow this tutorial if you require injection abilities

---

### Post by UncoElite on 2007-12-05
after that posting the device seems rather temperamental with gutsy's stock drivers. Speed/signal fluctuations and even signal drop outs/disconnection

EDIT:  ignore me. Found a fix on the forums [http://ubuntuforums.org/showthread.php?p=3671699#post3671699](http://ubuntuforums.org/showthread.php?p=3671699#post3671699)

---

### Post by ekko1976 on 2007-12-17
Thanks for this guide. I've successfully got my RT73 card to work on Gutsy Gibbon:

Dell Inspiron 1501 laptop
(K)Ubuntu 7.10 (Gutsy Gibbon)
Linksys WUSB54GC wireless USB stick
p_larbigs' 2.0.1 driver
RutilT 0.16 WLAN manager

Notes:

[LIST]
[*]Model WUSB54G**S** can only be used with ndiswrapper driver since it has a Broadcom chipset.
[*]Model WUSB54G **v4** has a Ralink chipset, but not previous versions!
[*]I didn't try the rt73usb driver coming with (K)Ubuntu, since I eventually want to use injection.
[*]I didn't have to remove the network manager coming with Kubuntu (KNetworkManager).
[*]The link quality is better now that what I've experienced with my laptop's built-in wiresless card (Broadcom bcm43xx), passing from 50% to 80% for a given network.

[/LIST]

---

### Post by johnaaronrose on 2007-12-22
Hi HymnToLife,

I have same problem as kzu. I have Edimax EW-7318USg. rt73.ko created of approx 246k after strip.

Terminal 'log' is shown below:
administrator@JohnLaptop:~/Temporary/rt73-k2wrlz-1.1.0/Module$ sudo strip -S rt73.ko
administrator@JohnLaptop:~/Temporary/rt73-k2wrlz-1.1.0/Module$ sudo make install
*** Install module in /lib/modules/2.6.20-16-generic/extra ...
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/administrator/Temporary/rt73-k2wrlz-1.1.0/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  INSTALL /home/administrator/Temporary/rt73-k2wrlz-1.1.0/Module/rt73.ko
  DEPMOD  2.6.20-16-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
/sbin/depmod -a
*** Update /etc/modprobe.conf alias for rausb*
grep: /etc/modprobe.conf: No such file or directory
*** Install firmware in /lib/firmware ...
*** Check config ...
administrator@JohnLaptop:~/Temporary/rt73-k2wrlz-1.1.0/Module$ 

/etc/modprobe.conf has 1 line: alias rausb* rt73

iwconfig shows lo, eth0 & eth1 (which is the inbuilt Broadcom 1390 wireless card in Dell Inspiron 1501).
 /etc/iftab shows eth0 & eth1 with their mac addresses & arp 1.


Help please!

---

### Post by toxic8 on 2008-03-28
Help! Why do I get this when I try to make?! :[

dino@dintoplinx:~/Desktop/rt73-k2wrlz-1.1.0/Module$ sudo make
[sudo] password for dino: 
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-12-generic'
  CC [M]  /home/dino/Desktop/rt73-k2wrlz-1.1.0/Module/rtmp_main.o
/home/dino/Desktop/rt73-k2wrlz-1.1.0/Module/rtmp_main.c: In function &#8216;usb_rtusb_probe&#8217;:
/home/dino/Desktop/rt73-k2wrlz-1.1.0/Module/rtmp_main.c:2142: error: implicit declaration of function &#8216;SET_MODULE_OWNER&#8217;
/home/dino/Desktop/rt73-k2wrlz-1.1.0/Module/rtmp_main.c:2162: error: &#8216;struct net_device&#8217; has no member named &#8216;weight&#8217;
/home/dino/Desktop/rt73-k2wrlz-1.1.0/Module/rtmp_main.c:2184: warning: passing argument 1 of &#8216;dev_get_by_name&#8217; from incompatible pointer type
/home/dino/Desktop/rt73-k2wrlz-1.1.0/Module/rtmp_main.c:2184: error: too few arguments to function &#8216;dev_get_by_name&#8217;
make[2]: *** [/home/dino/Desktop/rt73-k2wrlz-1.1.0/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/dino/Desktop/rt73-k2wrlz-1.1.0/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-12-generic'
rt73.ko failed to build!
make: *** [module] Error 1
dino@dintoplinx:~/Desktop/rt73-k2wrlz-1.1.0/Module$ 


I have tried with the 2.0 drivers as well ... and I have tried removing the 'old drivers' ala the rt73 wiki.  

BTW Im using UBUNTU 8.04 BETA
Help!!

---

### Post by Scotty562 on 2008-03-28
I'm getting the same error. Doesn't look like this guide works for gutsy anymore.

---

### Post by cleverest on 2008-04-14
Thanks to this guide (modified by me only via the links...for later version of the software/drivers) I was able to get my hawking USB (ralink) device working and browsing my WPA2 wireless network!  THANK YOU....

...now if injection works...I'm set!!!

ONE QUESTION:  When I type airmon-ng and his enter...is it supposed to list my rausb0 as Driver:  RT2500

even though I'm using RT73??


- Brett

---

### Post by mavi_yelkenler on 2008-04-21
> **toxic8 said:**
> Help! Why do I get this when I try to make?! :[

dino@dintoplinx:~/Desktop/rt73-k2wrlz-1.1.0/Module$ sudo make
[sudo] password for dino: 
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-12-generic'
  CC [M]  /home/dino/Desktop/rt73-k2wrlz-1.1.0/Module/rtmp_main.o
/home/dino/Desktop/rt73-k2wrlz-1.1.0/Module/rtmp_main.c: In function &#8216;usb_rtusb_probe&#8217;:
/home/dino/Desktop/rt73-k2wrlz-1.1.0/Module/rtmp_main.c:2142: error: implicit declaration of function &#8216;SET_MODULE_OWNER&#8217;
/home/dino/Desktop/rt73-k2wrlz-1.1.0/Module/rtmp_main.c:2162: error: &#8216;struct net_device&#8217; has no member named &#8216;weight&#8217;
/home/dino/Desktop/rt73-k2wrlz-1.1.0/Module/rtmp_main.c:2184: warning: passing argument 1 of &#8216;dev_get_by_name&#8217; from incompatible pointer type
/home/dino/Desktop/rt73-k2wrlz-1.1.0/Module/rtmp_main.c:2184: error: too few arguments to function &#8216;dev_get_by_name&#8217;
make[2]: *** [/home/dino/Desktop/rt73-k2wrlz-1.1.0/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/dino/Desktop/rt73-k2wrlz-1.1.0/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-12-generic'
rt73.ko failed to build!
make: *** [module] Error 1
dino@dintoplinx:~/Desktop/rt73-k2wrlz-1.1.0/Module$ 


I have tried with the 2.0 drivers as well ... and I have tried removing the 'old drivers' ala the rt73 wiki.  

BTW Im using UBUNTU 8.04 BETA
Help!!

i am also using Beta and the same problem..
anyone to help?
i want to use this driver and not the one that comes with Heron..
btw where is the rt2x00 directory in Heron?:confused:

update: i found rt2x00 directory under /lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/rt2x00

---

### Post by SysStream on 2008-04-23
this wont compile in ubuntu hardy. i tried it a couple of times over several fresh pcs with hardy.

prove me that im wrong xD

---

### Post by ubulap on 2008-04-24
It seems that this modified rt73 driver isn't working anymore with kernel 2.6.24 (which is the one Hardy uses).

The problem is known and it seems a new driver version is on its way:
[http://tinyshell.be/aircrackng/forum/index.php?topic=1824.msg18276#msg18276](http://tinyshell.be/aircrackng/forum/index.php?topic=1824.msg18276#msg18276)

A pity that Hardy isn't allowing me to connect to a WPA network out of the box. :/

---

### Post by ac7ss on 2008-05-10
> **ubulap said:**
> 
The problem is known and it seems a new driver version is on its way:
[http://tinyshell.be/aircrackng/forum/index.php?topic=1824.msg18276#msg18276](http://tinyshell.be/aircrackng/forum/index.php?topic=1824.msg18276#msg18276)/

He says 3.0.0 is out on his web site, but doesn't mention where that would be.

---

### Post by ubulap on 2008-05-10
Right here ac7ss:
[http://homepages.tu-darmstadt.de/~p_larbig/wlan/](http://homepages.tu-darmstadt.de/~p_larbig/wlan/)

---

### Post by Alfred_McGee on 2008-05-12
Is there a howto page for using these drivers from Darmstadt in 
Ubuntu Hardy? I used an earlier version from the same location in Feisty and was thrilled.

---

### Post by mavi_yelkenler on 2008-05-26
> Right here ac7ss:
[http://homepages.tu-darmstadt.de/~p_larbig/wlan/](http://homepages.tu-darmstadt.de/~p_larbig/wlan/)

thanks ubulap,

I installed the driver 3.0 and it works great.

---

### Post by Alfred_McGee on 2008-05-26
Yeah, I downloaded version 3.0 a couple of days ago and followed the instructions in the README file. My Atheros wifi card (ar5007eg) seems to have been disabled by this operation, but my RT73 card now works perfectly.:) I'm gonna experiment with some different Madwifi drivers for my Atheros card, following the howto posted by nicedude, and see if perhaps they're more compatible than the old ones.

---

### Post by mavi_yelkenler on 2008-05-26
hi Alfred,

glad to hear your rt73 is working

My laptop has a Atheros ar5007eg based wifi card and i am using the driver from that link -->> [http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz)

both my Atheros and Rt73 work great with Aircrack-ng. but it takes some time for my rt73 to make a fake auth attack with that 3.0 driver. anyway all is ok

regards

---

### Post by Alfred_McGee on 2008-05-28
Hi Mavi

Thanks for the info about ar5007 and rt73. My two cards worked perfectly together when I set them up, but after a reboot, my ar5007eg card seems to be dead again. I've tried all sorts of tricks to wake it up, but no matter what I do, *sudo iwlist scanning* always gives back "ath0 No scan results." Anybody have any ideas?

---

### Post by mavi_yelkenler on 2008-05-28
> **Alfred_McGee said:**
> Hi Mavi

Thanks for the info about ar5007 and rt73. My two cards worked perfectly together when I set them up, but after a reboot, my ar5007eg card seems to be dead again. I've tried all sorts of tricks to wake it up, but no matter what I do, *sudo iwlist scanning* always gives back "ath0 No scan results." Anybody have any ideas?

hi Alfred

unfornunately NOW i have the same problem about ar5007eg:confused:
I use 7.10. I have not upgraded Hardy. I see that people using Hardy have also the same problem after they received some updates. I also received several updates from 7.10 repos. after that my atheros died:) I think this about those updates not about new 3.0 RT73 drives.

I tired the previous patched Atheros drives ( madwifi-ng-r2756+ar5007.tar.gz) but it failed...

within several days I shall install Hardy and try again..

one more thing.. iwlist scan ath0 returns nothing.. BUT when I use "airodump-ng ath0" I can see all the networks around me!! strange :)

regards

---

### Post by Alfred_McGee on 2008-06-10
Yeah, looks like the easiest way to use these two wifi cards at once is just to make a bootable USB drive with Backtrack. It would be nice if both cards worked together under Hardy, as they did under Feisty. There's probably some way to do it, but I got tired of so much tinkering.

---

