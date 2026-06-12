---
title: "Screen Resolution"
date: 2009-11-06
forum: Philippine Team
---

### Post by Lila_IT_CMU on 2009-11-06
Hello, saan po ba makikita ang xorg.conf? maliit kasi maxado ang screen resolution ko kahit na install ko na ung VGA driver...SIS mirage 3 po ang card ko....

---

### Post by guitar_man on 2009-11-07
> /etc/X11/xorg.conf
eto sir

---

### Post by zilu54 on 2009-11-07
naku etu ang kinaasaran ku sa desktop pc ku eh.
hindi ku na matandaan kung panu lagyan ulit ng standard 4:3 1024x720
kala ku kasi wala na yung prublema pag upgrade ku ng 9.04 to Karmic.

---

### Post by wersdaluv on 2009-11-08
System-> Preferences -> Display? :)

---

### Post by Lila_IT_CMU on 2009-11-08
Wla ung xorg.conf sa /etc/X11/ ewan ko bakit...sa Display naman 800*600 at 640*500 lng ang available resolution eh...nainstall ko na rin ung sis driver...pero ganun pa rin wala pa ring pinagbago

---

### Post by pinoyskull on 2009-11-08
> **Lila_IT_CMU said:**
> Wla ung xorg.conf sa /etc/X11/ ewan ko bakit...sa Display naman 800*600 at 640*500 lng ang available resolution eh...nainstall ko na rin ung sis driver...pero ganun pa rin wala pa ring pinagbago
by default wala yan, naka auto configure

but if you need one, just run the command and it will generate a minimal config

> sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Lila_IT_CMU on 2009-11-08
> **pinoyskull said:**
> by default wala yan, naka auto configure

but if you need one, just run the command and it will generate a minimal config

ano po ba ung auto configure? kasi sa xorg.conf ko ine-edit ung resolution eh... ano naman po ang igegenerate ng command na yan? katulad din po ba sa xorg.conf?

---

### Post by pinoyskull on 2009-11-08
> **Lila_IT_CMU said:**
> ano po ba ung auto configure? kasi sa xorg.conf ko ine-edit ung resolution eh... ano naman po ang igegenerate ng command na yan? katulad din po ba sa xorg.conf?
by default kasi walang xorg.conf kasi namamanage kasi yan thru System-> Preferences -> Display? (courtesy of wersdaluv), if you need custom settings you need to have a xorg.conf in /etc/X11, the command I gave you will generate a minimum config based on your system, from there you can add options, etc.

---

### Post by Lila_IT_CMU on 2009-11-10
> **pinoyskull said:**
> by default kasi walang xorg.conf kasi namamanage kasi yan thru System-> Preferences -> Display? (courtesy of wersdaluv), if you need custom settings you need to have a xorg.conf in /etc/X11, the command I gave you will generate a minimum config based on your system, from there you can add options, etc.


eh tapos kong i execute ung command eh wala pong nagyari eh, walang kung anong lumabas...san ba makikita ung minimum config na nagenerate nya?

---

### Post by perbiu on 2009-11-10
Have you tried this driver on the spanish site?
[http://ubuntuway.wordpress.com/2009/07/13/drivers-de-sis-771671-para-jaunty/](http://ubuntuway.wordpress.com/2009/07/13/drivers-de-sis-771671-para-jaunty/)
[URL="http://go2.wordpress.com/?id=725X1342&site=ubuntuway.wordpress.com&url=http%3A%2F%2Fnacho.larrateguy.com.ar%2Fwp-content%2Fuploads%2F2009%2F07%2Fxorg-driver-sisimedia_0.9-1_i386.deb"]
direct link[/URL]

---

### Post by zilu54 on 2009-11-12
Naasar na aku talaga....kailangan ku na nga ng tulung.
Inayus ku ang xorg config at dinagdagan ng konting commands sa gedit para madagdagan ng 1024x768 na reso sa option ng display ko. then pag tapus ku i-save eh nirestar ku at hayun, gumana ang ginawa ku at ang nangyari lumabas na lang ay parang safe mode na ewan hindi ko alam kung anung tawag dun. can you guys please help me?

*attached some screenshots*

---

### Post by perbiu on 2009-11-12
What is your video card?
Unplug all USB sticks.

try to type gmd start after login in safemode
or **sudo /etc/init.d/gdm start**

---

### Post by zilu54 on 2009-11-12
> **perbiu said:**
> What is your video card?
Unplug all USB sticks.

try to type gmd start after login in safemode
or **sudo /etc/init.d/gdm start**

Rejected send message ang nakasabi.
nagawa ku naman siya nuon at hindi siya natulad nuon nung jaunty. balak ku nga lagyan na lang ng puppy eh ang nangyari yung disk ang nagka prublema ah ewan basta kailangan ku lang maayus lang ang reso ng desktop pc ku.

---

### Post by Lila_IT_CMU on 2009-11-13
> **zilu54 said:**
> Naasar na aku talaga....kailangan ku na nga ng tulung.
Inayus ku ang xorg config at dinagdagan ng konting commands sa gedit para madagdagan ng 1024x768 na reso sa option ng display ko. then pag tapus ku i-save eh nirestar ku at hayun, gumana ang ginawa ku at ang nangyari lumabas na lang ay parang safe mode na ewan hindi ko alam kung anung tawag dun. can you guys please help me?

*attached some screenshots*

try mo ctrl+alt+F7 or ctrl+alt+F1

---

### Post by zilu54 on 2009-11-13
> **Lila_IT_CMU said:**
> try mo ctrl+alt+F7 or ctrl+alt+F1
gagawin ku yan sa safe mode ng live cd no?

---

### Post by Lila_IT_CMU on 2009-11-14
> **zilu54 said:**
> gagawin ku yan sa safe mode ng live cd no?

try mo lng, yan ginawa ko noon sa laptop ko, bumalik naman sa dati ung desktop ko.

---

### Post by zilu54 on 2009-11-15
> **Lila_IT_CMU said:**
> try mo lng, yan ginawa ko noon sa laptop ko, bumalik naman sa dati ung desktop ko.

hays....walang nangyari sa ginawa ku, sige ok lang salamat na lang po :) try ku na lang ang Puppy (kasu kailangan pa i-configure ang internet connection para maka connect sa internet sheeesh~)

---

