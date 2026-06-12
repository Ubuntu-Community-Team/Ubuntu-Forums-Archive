---
title: "webcam question"
date: 2008-11-29
forum: Philippine Team
---

### Post by kiminaiseah on 2008-11-29
im glad gumgmana na lahat ng webcam from cdrking or any chinamade webcams sa kernel 2.6.24+ ang problem ko pag na install pag gnome desktop then skype yung mga ma view sa webcam lahat nemic lahat kulay green so able to fix this mag iinstall pa ako ng kopete.. pero pag kde desktop manager gamit ko wla problem about this

---

### Post by Script Warlock on 2008-11-29
anu gamit mo webcam a4tech is good

---

### Post by kiminaiseah on 2008-11-29
wla naman night vision yung a4tech eh.. pag sa madilim ka nag webcam bulag din yung webcam sa a4tech hahaha

---

### Post by loell on 2008-12-01
```
lsusb
```

---

### Post by kiminaiseah on 2008-12-03
#lsusb
Bus 005 Device 002: ID 0ac8:332d Z-Star Microelectronics Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by kikoman on 2008-12-03
Almost all china products works on Linux because they use generic chipsets. It looks like china might be the one to push Linux into the mainstream once they managed to create cheap computers and laptops. Especially that Intel is moving to China. Years later we would be buying cheap pentium clone processors, motherboards with integrated video.

---

### Post by dodimar on 2008-12-03
> **kikoman said:**
> Almost all china products works on Linux because they use generic chipsets. It looks like china might be the one to push Linux into the mainstream once they managed to create cheap computers and laptops. Especially that Intel is moving to China. Years later we would be buying cheap pentium clone processors, motherboards with integrated video.

Di kaya mahaluan ng melamine?):P

---

### Post by kiminaiseah on 2008-12-04
> **kikoman said:**
> Almost all china products works on Linux because they use generic chipsets. It looks like china might be the one to push Linux into the mainstream once they managed to create cheap computers and laptops. Especially that Intel is moving to China. Years later we would be buying cheap pentium clone processors, motherboards with integrated video.

actually it worx in kernel 2.6.24 and above... the problem is the gnome.. kulay green lahat ng makita ng webcam haha.. pero sa kde/kopete messenger ok nman sya

---

### Post by kiminaiseah on 2008-12-04
> **dodimar said:**
> Di kaya mahaluan ng melamine?):P

yung una kong webcam na made in china kinagat ng daga pero namatay din cguro namelamine

---

### Post by loell on 2008-12-04
this is a **UVC** type webcam, kopete may have added some workaround for this webcam. while other apps may not have. is this on hardy or in Intrepid?

---

### Post by kiminaiseah on 2008-12-04
> **loell said:**
> this is a **UVC** type webcam, kopete may have added some workaround for this webcam. while other apps may not have. is this on hardy or in Intrepid?

Ubuntu Jaunty gamit ko para mag fit sakanya ang manual installation ng KDE4 from kde4.debian.net, well pag nka KDE ako sempre as default IM ng KDE is Kopete, install ako camorama or camstream.. me display sya agad :d hehhehe galing nga miski madilim kita nung webcam... ayaw ko lang sa KDE naliligaw ako.. kya i rather degrade into GNOME :d

---

### Post by loell on 2008-12-04
try Ekiga 3.0 , it should be on jaunty. i think it can also detect you webcam properly.

---

### Post by kiminaiseah on 2008-12-04
btw

salamat hehehe

---

### Post by riclags on 2008-12-04
hi all, i have a neo laptop and i am wondering how to use the webcam on it. not sure kung na-detect siya o na-install ang drivers ng maayos, pero di ko makita kung saan iparun/i-try ang webcam. i'm using 8.10 (intrepid).

---

### Post by Script Warlock on 2008-12-04
yes i have neo elan konting tweak lang para sa webcam gumana, yun lang 

take note: NEO ELAN

install cheese or try it sa ekiga

---

### Post by crouchdash on 2008-12-08
ako din di pa rin gumagana yung webcam ko na nabili ko sa cdr king. dati sa xp gumagana, dito sa itrepid ayaw :confused:

I tried ekiga, skype and cheese ayaw pa din. I also tried the drivers sa repository no luck pa din. Alcor Micro yung webcam. Patulong naman po. parang awa nyo na.

---

### Post by otniuqyrreg on 2008-12-11
Meron din akong webcam galing sa cdr-king, hindi ko alam kung paano paganahin dito sa Ubuntu. Paano nga ba :confused:

---

### Post by kiminaiseah on 2008-12-14
hehe prob ko sumtimes yan sa ubuntu from 8.04LTS na dedetect yung webcams galing kay cdrking with any tools, sa intrepid medyo yung iba di na dedect kay jaunty na dedetect problem nemic lahat ng tao.. hehe kaya balik parin ako debian lenny / sid, everything works well :d

---

### Post by crouchdash on 2008-12-16
Di ba yung byanihan linux based sa debian distro? gumagana ba yung webcam ng cdr king dun?

Tulong po tulong![-o<

---

### Post by kiminaiseah on 2008-12-16
no..

Bayanihan Redhat Base

---

### Post by dodimar on 2008-12-16
> **kiminaiseah said:**
> no..

Bayanihan Redhat Base

Actually, they already transition to Debian base when they released Bayanihan linux version 4 ([http://distrowatch.com/table.php?distribution=bayanihan](http://distrowatch.com/table.php?distribution=bayanihan))

:guitar:

---

### Post by crouchdash on 2008-12-17
> **dodimar said:**
> Actually, they already transition to Debian base when they released Bayanihan linux version 4 ([http://distrowatch.com/table.php?distribution=bayanihan](http://distrowatch.com/table.php?distribution=bayanihan))

:guitar:

yep yung version 4 nila.

Kaya lang balik topic tayo, baka po me mabuting loob diyan na alam paganahin yung mga webcam na nabibili sa cdr king, dito sa intrepid.

Salamat po!

---

### Post by loell on 2008-12-17
> **crouchdash said:**
> yep yung version 4 nila.

Kaya lang balik topic tayo, baka po me mabuting loob diyan na alam paganahin yung mga webcam na nabibili sa cdr king, dito sa intrepid.

Salamat po!

post mo lang ang necessary info

```
lsusb
```

pagka made in taiwan or made in china, parang dun tayo nagkakaproblema kasi halos kalahati nun walang linux driver.

---

### Post by crouchdash on 2008-12-19
eto ser yung lumabas

jalkenzoe@jalkenzoe:~$ lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jalkenzoe@jalkenzoe:~$

---

### Post by loell on 2008-12-19
> **crouchdash said:**
> eto ser yung lumabas

jalkenzoe@jalkenzoe:~$ lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jalkenzoe@jalkenzoe:~$

naka-saksak ba yung usb ng webcam? nung ginawa mo ito? para kasing wala.

---

### Post by crouchdash on 2008-12-19
oo ser, naka-ilaw pa ng yung cam eh.

:confused:

---

### Post by loell on 2008-12-19
> **crouchdash said:**
> oo ser, naka-ilaw pa ng yung cam eh.

:confused:

ah ok, paki-tingnan mo na lang yung webcam model at brand ng webcam.

---

