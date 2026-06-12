---
title: "HELP PO smartbro starter kit (HUAWEI E153) PANU PO PAGANAHIN SA UBUNTU 10.04"
date: 2011-08-23
forum: Philippine Team
---

### Post by kopin on 2011-08-23
pahelp po
tinry ko na po ibat ibang instructions na nabasa ko sa forums pero ayaw pa in po gumana ng smart bro sa ubuntu 10.04 ko.

ilang araw na po ako di pumapasok sa skul at di natutulog kaka search. 

maraming salamat po

---

### Post by tech-hero on 2011-08-23
> **kopin said:**
> pahelp po
tinry ko na po ibat ibang instructions na nabasa ko sa forums pero ayaw pa in po gumana ng smart bro sa ubuntu 10.04 ko.

ilang araw na po ako di pumapasok sa skul at di natutulog kaka search. 

maraming salamat po
Talaga nagsearch ka na sa lahat at hindi pa din gumagana? So far pinaka stable ngayon ang 10.04. I'm using the same modem for Sun Broadband. It works out of the box. Just configure your Access point.

If talagang ginawa mo na lahat, check natin baka naman hindi nadedetect ng PC mo
 
type mo sa terminal
 
lsusb
 
dapat lalabas jan yung modem mo na huawei. pag nadedetect yan, either signal or configuration settings lang ang problem mo. konting search pa. google is our friend.

---

### Post by jepong on 2011-08-24
yan ata yung version na need mo pa install yung usb-modeswitch?

---

### Post by kopin on 2011-08-24
May weird po na nangyari kanina.
kasi nadetect na sa network manager ung smart connection at nakapag internet na ako using my 10.04.

May pasok ako sa school kanina, kaya shut down ko muna.
But when I returned from skul and turn on my unit,
I was shocked because my 10.04 cannot detect the Smart connection again,

Bakit kaya nagkaganun, 

Nung time na nadetect ung Smart connection e2 ung lumalabas pag input ko lsusb:

kopin@kopin:~$ lsusb
Bus 005 Device 001 : ID 1d6b : 0001 Linux Foundation 1.1 root hub
Bus 004 Device 001 : ID 1d6b : 0001 Linux Foundation 1.1 root hub
Bus 003 Device 001 : ID 1d6b : 0001 Linux Foundation 1.1 root hub
Bus 002 Device 001 : ID 1d6b : 0001 Linux Foundation 1.1 root hub
Bus 001 Device 003 : ID 04e8 : 7043 Samsung Electronics Co., Ltd
Bus 001 Device 002 : ID 12d1 : **14ac** Huawei Tachnologies Co., Ltd
Bus 001 Device 001 : ID 1d6b : 0002 Linux Foundation 2.0 root hub
kopin@kopin:~$

Pero nung time na ayaw ng madetect e2 na lumalabas:

Bus 001 Device 003 : ID 12d1 : **1446** Huawei Tachnologies Co., Ltd

tapos may iba pang nagbago.

kung nid ang usb modeswitch, san po pede ma dl. salamat

---

### Post by jepong on 2011-08-24
mukhang yan na nga yun... try mo muna before mo ON, plug mo na muna yung dongle mo and check kung detected.

Anyway, install mo na lang using terminal

```
sudo apt-get install usb-modeswitch
```

---

### Post by kopin on 2011-08-24
ahhm sir jepong.
sir tech-hero

ang wirdo tlaga.
hehehe kasi ngaun nadetect nnmn ung smart.
actually kakareformat ko lng ne2ng 10.04, di pa ako ng modeswitch pero nadetect,
ewan ko lng kung bukas kung madedetect nnmn,
maraming salamat po sa inyo.
mag popost n lng po ulet ako pag nag kaproblema

iiwan ko na po kasi windows once na natapos ko subject ko na vb.

maraming salamat:)

---

### Post by tech-hero on 2011-08-24
normal yan bro! ganyan din ang sakin. nadedetect yan. unplug mo lang at iplug ulit. minsan may prob sya na pag nag boot ka at nakasaksak pa ang modem mo, hindi talaga sya madedetect sa network manager... ung USB mode switch makaktulong yun. pero sa part ko, hindi ko na ininstall yun, napagttyagaan ko naman yung tinatanggal muna. normal lang yan..

btw, i update mo yung 10.04 mo sa latest update sa update manager. nung ginawa ko yun, less frequent na yung mga ganyang issues.

---

### Post by jepong on 2011-08-26
actually ang problem nya is na-detect yung dongle sa USB instead of modem kaya ayun.

---

### Post by tech-hero on 2011-08-26
kaya need ng USB mode switch.

---

