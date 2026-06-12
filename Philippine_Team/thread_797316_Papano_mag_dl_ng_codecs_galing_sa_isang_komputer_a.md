---
title: "Papano mag dl ng codecs galing sa isang komputer at i intsall sa isa pang komputer?"
date: 2008-05-17
forum: Philippine Team
---

### Post by vantrigger on 2008-05-17
Puwede nyo po ba akong tulungan sa aking problema dahil baguhan lang po ako sa Ubuntu. :confused:

---

### Post by loell on 2008-05-17
yo, connected ba yung dalawang computer? naka LAN ba sila?

---

### Post by yssida on 2008-05-17
hala, pano nga yun...di ko rin po alam:popcorn:

useful to kung walang internet, and all you have is a USB flash disk:)

---

### Post by loell on 2008-05-17
siguro gagamit tayo nang w32codecs.deb kung ganun.

---

### Post by vantrigger on 2008-05-17
kasi ang problema ko, ung windows na komputer lng ang may wifi. ung ubuntu ko, wala. kaya kailangan ko mag dl ng codecs from another computer. and install is to my ubuntu. yep, pde sila iconnect through lan.

---

### Post by loell on 2008-05-17
so walang internet connection yung ubuntu mo?

kung gusto mo lang nag individual package para sa codecs na wala masyado inaalala sa dependency

download mo yung w32codecs 

 [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20071007-0.0_i386.deb]("http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20071007-0.0_i386.deb")

 at  [libdvdcss2_1.2.9-0.0_i386.deb]("http://www.debian-multimedia.org/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0.0_i386.deb") for DVD playback

---

### Post by vantrigger on 2008-05-18
> **loell said:**
> so walang internet connection yung ubuntu mo?

kung gusto mo lang nag individual package para sa codecs na wala masyado inaalala sa dependency

download mo yung w32codecs 

 [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20071007-0.0_i386.deb]("http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20071007-0.0_i386.deb")

 at  [libdvdcss2_1.2.9-0.0_i386.deb]("http://www.debian-multimedia.org/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0.0_i386.deb") for DVD playback


ung [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20071007-0.0_i386.deb]("http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20071007-0.0_i386.deb") 
page not found... tapos ung pang dvd naman na install ko successfully kaso hindi parin gumagana dvds.. bakit kaya? totem movie player gamit ko.:confused:

---

### Post by loell on 2008-05-18
no go yata siguro tong procedure na ito, kasi mag-iinstall ka pa pala nang totem-xine which depends on xine and xine depends on many other packages, its very difficult to track them and download those packages individually.


kung pwedeng mag lan sa xp to ubuntu mag internet connection sharing na lang kaya tayo para maka download ka nang codecs sa ubuntu repository


o di kaya naman , since sinira na ni wers yung windows partition mo ;) and you have nothing to loose on this setup yet?  gumamit ka na lang kaya nang [Linux Mint]("http://www.linuxmint.com/") may codecs na kasi yun at ubuntu based din yun :)

---

### Post by yssida on 2008-05-20
May nakita ako. NoNetDebs yata ang tawag doon. Ma-install mo lahat ng proprietary extras na kailangan mo thru ubuntu-restricted-extras.

---

### Post by Nhatz on 2008-05-20
ang alam ko pwede ka maginstall ng aptoncd then gawa k anga .iso ng mga downloaded stuffs mo then restore mo sa kabilang box.. hehehe :) tama ba?
Astig! :guitar:

---

### Post by loell on 2008-05-20
yeah, pwede yun, pero kay OP kasi, windows lang yung may internet connection.

---

### Post by Nhatz on 2008-05-20
[QUOTE=loell]yeah, pwede yun, pero kay OP kasi, windows lang yung may internet connection.[/QUOTE] 

baka pwede boot sya sa live cd then install nga aptonccd dun then kunun nya yung .iso saka nya ilipat sa ubuntu box nya... hehehe :)
Astig! :guitar:

---

### Post by loell on 2008-05-20
hmm.. paano kaya yun, download nya yung codecs sa livecd mode via apt, of course yung downloaded packages nya nasa memory by default, kaya kailangan nya malaking RAM para di sya magkulang. plus aptoncd pa, na dapat install muna on the fly. then dapat dalawa yung cd drive nya ang isa writable.  possible yun..

---

### Post by loell on 2008-05-20
ahhhh :idea:  now you just gave an idea :KS  , ngaun ko lang naisip yung sa livecd..

yung cached debs sa livecd mode , 


install the codecs sa livecd, and it will also download the dependencies doon sa deb cache. 

pupunta ka sa **/var/cache/apt/archives**

copyahin lahat nang deb packages nan nandoon via usb stick o kahit anong media.

then transfer sa ubuntu na walang internet then invoke 

```
sudo dpkg -i *
```

yunn... may proprieatry codecs ka na :guitar:

---

### Post by wersdaluv on 2008-05-20
> **loell said:**
> ahhhh :idea:  now you just gave an idea :KS  , ngaun ko lang naisip yung sa livecd..

yung cached debs sa livecd mode , 


install the codecs sa livecd, and it will also download the dependencies doon sa deb cache. 

pupunta ka sa **/var/cache/apt/archives**

copyahin lahat nang deb packages nan nandoon via usb stick o kahit anong media.

then transfer sa ubuntu na walang internet then invoke 

```
sudo dpkg -i *
```

yunn... may proprieatry codecs ka na :guitar:
Ah pocha! Gifted child! hahahahaha!

---

### Post by loell on 2008-05-20
:lolflag: hindi sa akin yan kay nhatz yan  :lolflag:

---

### Post by wersdaluv on 2008-05-20
Ay mali! Di pala pwede. 

Ganto kasi. Windows computer lang niya ang may connection kasi sa Windows lang gumagana ang Axesstel usb Wireless Internet niya. Di pwede siya mag-live CD kasi 'di gagana ang Axesstel modem niya.

Moral of the story: have a good internet connection when installing and configuring Ubuntu. hehe

---

### Post by loell on 2008-05-20
pwede din mag wubi sa windows, then install the codecs :lolflag:

---

### Post by wersdaluv on 2008-05-20
Ah gifted child nga :D

Di pa ko familiar sa wubi.

---

### Post by Nhatz on 2008-05-20
Yup yun nga....!!! hehehe :)
Astig! :guitar:

---

### Post by Samhain13 on 2008-05-21
Loell, nag-Promil ka nung bata ano?! :D

---

### Post by loell on 2008-05-21
hindi eh, pero naabutan nyo ba yung time, na namimigay nang powdered milk ang gobyerno? yun isang malaking tupperware everyweek, kumakain ako noon everyday  :lolflag:

---

### Post by Nhatz on 2008-05-21
Ako laking "am" lang ako kaya slow learner... hehehehe :) ..pero gusto ko yung nutribun dati nung grade 1 ako. hehehehehe :) at masarap yung powdered milk na bininenta sa quiapo nun (yung per kilo na naka sako)
Astig! :guitar:

---

### Post by kenweill on 2008-05-23
if you downloaded from the repos, then that is possible.

copy all .deb files from /var/cache/apt/archives of the main computer to the same directory in the other computer. and install every deb files present there.

its not just the codecs that will be copied but also all the updates you have made from the main computer. everytime you download files or update your ubuntu system, all files are downloaded first in that directory, then install it. that is automatic. so if you have multiple computers and you don't want to manually update every computers, just update one computer then copy the deb files to the other computers then run update. and you're done. no need to redownload the files from the repos.

thats what i do. install Ubuntu to 6 computers. Update 1 computer. Then copy all the updates to the other 5 computers.  :D

---

