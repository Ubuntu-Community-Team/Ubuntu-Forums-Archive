---
title: "Installing Webcam..."
date: 2009-05-15
forum: Philippine Team
---

### Post by zilu54 on 2009-05-15
habang nag hihintay aku sa tinatanung ku,

ang mom ku kasi ay nagagalit na dahil hindi ku pa kasi na iinstall ang webcam hehehe tinry ku na ang lahat (easycam...blah blah~) hindi pa rin gumagana at nag e-error sana man lang isa sa mga webcam kong dalawa ay gumana. uu nga pala, parehas yata ay windows and mac ang support nila, may magandang tools ba dyan para gumana ang mga windows supported softwares?

intex Night Flick CAMERA (Model # IT309WC) at A4 TECH Webcam

sana'y matulungan nyo po aku ditu.

---

### Post by loell on 2009-05-15
plug mo ang webcam, tapos copy paste mo output ng command na ```
lsusb
```

just in case pwede mong mapalitan ang webcam mo, magrefer ka dito para sa specific na webcam model

[http://mxhaard.free.fr/spca5xx.html]("http://mxhaard.free.fr/spca5xx.html")

---

### Post by zilu54 on 2009-05-16
nakita ku sa dalawan webcam ku ay parehas na Z-Star Microelectronics Corp. ZC0303 WebCam kasu hindi ku mahanap yung specific na model yung ZC03X based webcams ba ay sakup sa model ng webcam ku?

wala pa rin akung idea panu pa rin tu ayusin :(

---

### Post by wersdaluv on 2009-05-16
Jaunty ba ang gamit mo? Nag-install ka ba ng custom kernel? 

It's fixed in Jaunty daw [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318061](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318061)

---

### Post by zilu54 on 2009-05-17
hindi ku alam kung kasama sa updates ang kernel.
sabi nga rin daw na mag install aku ng kernel then update ku para maayus ang graphics pati rin ang webcam.

---

### Post by wersdaluv on 2009-05-17
Anong graphics? Intel? Ano graphics card mo?

---

### Post by zilu54 on 2009-05-17
built-in na sa motherboard ku yung akin, kahit built-in ba ay may pangalan pa rin yun?

---

### Post by loell on 2009-05-17
importante yung output ng **lsusb** , baka makahanap tayo ng specific solution.

---

### Post by zilu54 on 2009-05-17
:( hala...kung may pangalan pala yun tsk hindi ku alam kung anu ang pangalan basta intel siya.
tiningnan ku yung box ng motherboard, anu tung chipset? kasama po ba tu sa graphic card?

---

### Post by loell on 2009-05-17
hindi, sa webcam lang to.

---

### Post by Samhain13 on 2009-05-17
Back to basics. Subukan mo munang isaksak yung camera sa iba't-ibang ports. Yung sakin kasi, ayaw niyang gumana kung sa hub/extension ko sinasaksak. Apparently, mapili siya. Tignan mo lang din kasi baka mag-edit ka nang mag-edit ng files tapos, yung saksakan lang pala ang problema. :)

---

### Post by zilu54 on 2009-05-17
@loell & smhain13
ay, ku ku agad na gets :P

sinaksak ko parehas ang webcam at parehas na ganitu ang lumabas.
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam
Bus 004 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
sa tingin ku ay walang prublema sa webcam kasu hindi nga lang gumagana.

---

### Post by loell on 2009-05-17
this is supposedly a supported webcam, what webcam applications have you tried so far?

---

### Post by zilu54 on 2009-05-17
> **loell said:**
> this is supposedly a supported webcam, what webcam applications have you tried so far?
i already tried camorama but it doesnt catch some images.
gustu ku sana gamitin tung webcam para sa YM [yun ang primary ginagamit ng mom ko sa PC]

---

### Post by loell on 2009-05-17
sigh, you need to have a kernel patch, or a newer kernel :(

they say, this used to work on hardy heron.

---

### Post by loell on 2009-05-17
oh, try installing this kernel

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc4/linux-image-2.6.30-020630rc4-generic_2.6.30-020630rc4_i386.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc4/linux-image-2.6.30-020630rc4-generic_2.6.30-020630rc4_i386.deb")

then restart.. use a webcam application.

---

### Post by zilu54 on 2009-05-17
na install ku na kasu sa camorama ay "cannot capture image" gustu ku sana alamin panu i-install ang YM to ubuntu para ma try ku webcam sa YM.

samalat :)

---

### Post by loell on 2009-05-17
:) /coughs,.. two ways,

isntall kopete or

install [This]("ubuntuforums.org/showthread.php?t=773802")

---

### Post by zilu54 on 2009-05-17
> **loell said:**
> :) /coughs,.. two ways,

isntall kopete or

install [This]("http://ubuntuforums.org/showthread.php?t=773802")
yes gumana nga siya.
salamat po sir.loell at sa mga nag response :)

---

### Post by loell on 2009-05-17
> **zilu54 said:**
> yes gumana nga siya.
salamat po sir.loell at sa mga nag response :)

gumana?!! :D

screenshot nga dyan..





heheh joke.. :biggrin:

---

### Post by Samhain13 on 2009-05-17
Tignan mo yung lsusb ko:

```
Bus 004 Device 004: ID 04d9:1603 Holtek Semiconductor, Inc. 
Bus 004 Device 002: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
**Bus 001 Device 003: ID 0ac8:305b Z-Star Microelectronics Corp. ZC0305 WebCam**
Bus 001 Device 001: ID 0000:0000
```

Saksak lang ako ng saksak niyan. :) Nga lang, Hardy ang gamit ko...

---[edit]---

Ngerk, gumana na pala! Congratulations. :)

---

### Post by dodimar on 2009-05-17
> **Samhain13 said:**
> Tignan mo yung lsusb ko:

```
Bus 004 Device 004: ID 04d9:1603 Holtek Semiconductor, Inc. 
Bus 004 Device 002: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
**Bus 001 Device 003: ID 0ac8:305b Z-Star Microelectronics Corp. ZC0305 WebCam**
Bus 001 Device 001: ID 0000:0000
```

Saksak lang ako ng saksak niyan. :) Nga lang, Hardy ang gamit ko...

---[edit]---

Ngerk, gumana na pala! Congratulations. :)

Hahaha... ganyan webcam ko.. plug and play lang sa Ubuntu... CDR king ko binili..

---

### Post by zilu54 on 2009-05-17
> **dodimar said:**
> Hahaha... ganyan webcam ko.. plug and play lang sa Ubuntu... CDR king ko binili..
panu ku naman po ma tanggal ung na download kong kernel? *past pages*
kasi may naka appear na ganyan na pala nung hindi ku pa nalalagyan ng kernel niyan? hindi ku mahanap yung pinag download sa synaptic package manager. matagal na pala ayus webcam ko [s]tanga ko talaga[/s]

---

### Post by wersdaluv on 2009-05-17
Tinatanong kita kung Intel ang video mo dahil may instructions dito [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) na nagpapainstall ng mas bagong kernel. Maari nitong maayos ang Intel video performance at webcam issue mo. Two birds with one stone. 

Para uninstall yung kernel na nilagay mo, search mo na lang linux-headers-2.6.30 sa synaptic. 

Ayos na ba yung webcam? Anong ibig mong sabihing ayos na dati pa?

---

### Post by zilu54 on 2009-05-17
> **wersdaluv said:**
> Tinatanong kita kung Intel ang video mo dahil may instructions dito [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) na nagpapainstall ng mas bagong kernel. Maari nitong maayos ang Intel video performance at webcam issue mo. Two birds with one stone. 

Para uninstall yung kernel na nilagay mo, search mo na lang linux-headers-2.6.30 sa synaptic. 

Ayos na ba yung webcam? Anong ibig mong sabihing ayos na dati pa?
ah...gustu ku sanang tanggalin at install ulit kasi may nakasulat na [failed] during scan nitu sa system at nakita ku yung "applarmor" ok lang ba yun? hindi ba yun prublema?

kasi bagu ku na install yung kernel ay naka detect naman ang webcam sa mga usb ports using lsusb then saka ku ninstall yung kernel.

---

### Post by daxumaming on 2009-05-20
got mine from cdr-king (during the release party), pero hindi ko pa napapagana. hindi pa sya supported. will wait for the next updated kernel that supports it. at least my built-in cam on my wind works perfectly.

---

### Post by ghreyzeus on 2009-05-20
):P hi!!! i'm very new to this technology...  i admit super buplaops n me here.. can anyone help me ot how can i install webcam.. primarily cheese ang specified usage ng camera. and as well d ko rin ma open ang speaker it shows gconfaudiosink.. at first gumagana ba't when i update to rhtymic box d xia gumana.. i tried to download elisa totally black screen lng ang show up.
i really appreciate somebody can help me..
thank you.

---

### Post by loell on 2009-05-20
working webcams on linux is chipset specific, so stay with known brands.

---

### Post by jsgotangco on 2009-05-20
Yeah its chipset specific. I have no use for a webcam though and the laptop I use with Ubuntu is a pretty old one with no cam so its no biggie for me, although I'm very aware that a lot of people, especially those with commercial interests, not having a working webcam is a big deal breaker.

---

### Post by ghreyzeus on 2009-05-20
> **ghreyzeus said:**
> ):P hi!!! i'm very new to this technology... i admit super buplaops n me here.. can anyone help me ot how can i install webcam.. primarily cheese ang specified usage ng camera. and as well d ko rin ma open ang speaker it shows gconfaudiosink.. at first gumagana ba't when i update to rhtymic box d xia gumana.. i tried to download elisa totally black screen lng ang show up.
i really appreciate somebody can help me..
thank you.
 
 
it 's in the package when i brought toshiba nb100 trying to learn p ung OS never heard about LINUX that why i need to learn pa. i already install eakiga for back up i'm not quite sure if it is going to work. any body....

---

### Post by codewalkz on 2009-05-24
I was quite confused with my webcam. I've been using ubuntu for quite sometime now but this is the time that I needed to get a webcam working on my system. I plugged in my CDR King webcam but to o avail. I the preferences of skype, I can see that the usb webcam's detected but when I press Test, it just gives me nothin but a white bar.](*,)

---

### Post by loell on 2009-05-24
well, your **lsusb** info is always welcome.

---

### Post by codewalkz on 2009-05-24
code@ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04fc:2001 Sunplus Technology Co., Ltd 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
code@ubuntu:~$

---

### Post by loell on 2009-05-24
[B]
Bus 001 Device 003: ID 04fc:2001 Sunplus Technology Co., Ltd [/B]

no linux module as of this writing.

---

### Post by codewalkz on 2009-05-24
But how come it's ok with Ekiga?

---

### Post by loell on 2009-05-24
what other webcam applications have you tried then?

---

### Post by codewalkz on 2009-05-24
> **loell said:**
> what other webcam applications have you tried then?

1 and only :D

---

### Post by loell on 2009-05-24
try executing skype like this instead,

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

---

