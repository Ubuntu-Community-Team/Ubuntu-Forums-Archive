---
title: "Webcam Installation"
date: 2009-08-09
forum: Philippine Team
---

### Post by Extra Rice on 2009-08-09
Guys, paturo naman po kung paano mag-install ng Webcam using Ubuntu. INTEX IT-305WC po ang model ng webcam ko. Saka pwede po bang gamitin ang webcam sa Pidgin Internet Messenger? Kasi YM user po ako.

Maraming Salamat po!!!

Mabuhay!

---

### Post by loell on 2009-08-10
hi Extra Rice, :)

ang webcam mo ay parang detected na sa ubuntu, ang mga pwede mong gamitin na mga _kadalasang programa_, ay ang mga sumusunod..

* [GYachI - YM]("http://ubuntuforums.org/showthread.php?t=773802&highlight=gyachi")

* kopete - YM at MSN

* aMsn - Msn

* skype for linux

__________________________
ang iyong lingkod: Ang sariling hinirang bilang experto ng webcam-linux ng kupunan ng Ubuntu Pilipinas! :biggrin:  (oo, ang yabang ko daw :guitar: )

---

### Post by wersdaluv on 2009-08-10
Wala pa pong webcam support sa Pidgin. Sundin niyo lang po si loell =)

---

### Post by Extra Rice on 2009-08-10
> **loell said:**
> hi Extra Rice, :)

ang webcam mo ay parang detected na sa ubuntu, ang mga pwede mong gamitin na mga _kadalasang programa_, ay ang mga sumusunod..

* [GYachI - YM]("http://ubuntuforums.org/showthread.php?t=773802&highlight=gyachi")

* kopete - YM at MSN

* aMsn - Msn

* skype for linux

__________________________
ang iyong lingkod: Ang sariling hinirang bilang experto ng webcam-linux ng kupunan ng Ubuntu Pilipinas! :biggrin:  (oo, ang yabang ko daw :guitar: )
Sir Paano ko po malalaman kung detected sya ng OS? San ko po sya pwedeng tignan? Like Device Manager...

Thanks a lot!

Mabuhay!

---

### Post by loell on 2009-08-10
pagsaksak mo nang webcam, at i-invoke mo ang command na, **lsmod | grep video** sa terminal, makikita mo ang  "zc0301", ang   "zc0301" ay driver ng webcam.

kung hindi o wala, paki post na lang  sa output ng command.

---

### Post by Extra Rice on 2009-08-13
> **loell said:**
> pagsaksak mo nang webcam, at i-invoke mo ang command na, **lsmod | grep video** sa terminal, makikita mo ang  "zc0301", ang   "zc0301" ay driver ng webcam.

kung hindi o wala, paki post na lang  sa output ng command.

Chief loell,

eto po yung output command regarding sa webcam.

[B]uvcvideo               63368  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
video                  25360  0 
output                 11008  1 video[/B]

tingin ko po wala dito yung sinasabi nyo na driver ng webcam.

Ano na po ang susunod kong gagawin? Salamat po! Mabuhay!!!

---

### Post by loell on 2009-08-13
ahh.. ok, di na pala zc* ang driver ng webcam mo, baka fix na yan.

```
uvcvideo
```
yan ang driver na ginagamit ng webcam mo.

gumamit ka na ng mga webcam application para masubukan mo talaga kung may output ang webcam mo.

isang well known na webcam application ng linux ay **cheese**. pwede mo ring subukan sa mga messenger application na na-mention sa taas.

---

### Post by Script Warlock on 2009-08-13
or luvcview....

sudo apt-get install luvcview

---

### Post by rjmdomingo2003 on 2009-08-13
> **loell said:**
> isang well known na webcam application ng linux ay **cheese**. pwede mo ring subukan sa mga messenger application na na-mention sa taas.
Uyy, talaga?! Masubukan nga. Cheese came pre-installed in Crunchbang, and my webcam worked out-of-the-box. Salamat ginoong loell :KS

---

### Post by Script Warlock on 2009-08-13
now i know crunchbang pala is linux and ubuntu-based hehehe kala ko talaga chocolate..crunchbar pala yun..

matry nga....

---

### Post by rjmdomingo2003 on 2009-08-13
> **Script Warlock said:**
> now i know crunchbang pala is linux and ubuntu-based hehehe kala ko talaga chocolate..crunchbar pala yun..

matry nga....
#! is worth trying, at least for me. Minimal Ubuntu install tapos openbox WM pa, w/o any DE. Cool..

---

### Post by loell on 2009-08-13
> **rjmdomingo2003 said:**
> Uyy, talaga?! Masubukan nga. Cheese came pre-installed in Crunchbang, and my webcam worked out-of-the-box. Salamat ginoong loell :KS

Ingat lang daw, [http://ubuntuforums.org/showthread.php?t=1197451]("http://ubuntuforums.org/showthread.php?t=1197451")

heheh, ewan ko kung anong nangyari sa kanya, pero talagang paniwalang paniwala sya na na hack or na punk siya. or baka na lasing lang one time. :lolflag:

---

### Post by dodimar on 2009-08-13
> **loell said:**
> Ingat lang daw, [http://ubuntuforums.org/showthread.php?t=1197451]("http://ubuntuforums.org/showthread.php?t=1197451")

heheh, ewan ko kung anong nangyari sa kanya, pero talagang paniwalang paniwala sya na na hack or na punk siya. or baka na lasing lang one time. :lolflag:

May easter egg nga ba sa cheese???

or since nasa remote location sya.. di kaya mumo yung nag salita?

---

### Post by loell on 2009-08-13
> **dodimar said:**
> May easter egg nga ba sa cheese??? 

I highly doubt it, kung meron, di sana nalaman na ng karamihan. :)


> **dodimar said:**
> 
or since nasa remote location sya.. di kaya mumo yung nag salita?

heheh, pwedeh rin, french accented na mumo! :D

---

### Post by rjmdomingo2003 on 2009-08-14
> **loell said:**
> Ingat lang daw, [http://ubuntuforums.org/showthread.php?t=1197451]("http://ubuntuforums.org/showthread.php?t=1197451")

heheh, ewan ko kung anong nangyari sa kanya, pero talagang paniwalang paniwala sya na na hack or na punk siya. or baka na lasing lang one time. :lolflag:
malamang 'di "I am Watching." ang narinig nun kundi "Cheeeeese!"...sorry, just woke up :P

---

### Post by Extra Rice on 2009-08-14
> **Script Warlock said:**
> or luvcview....

sudo apt-get install luvcview

Ok Chief! Nagawa ko na po sya. Tapos po??? What should I do next? Sorry po kung medyo "igno" ako pagdating sa ganito.. newbie po kasi. :)

> **loell said:**
> ahh.. ok, di na pala zc* ang driver ng webcam mo, baka fix na yan.

```
uvcvideo
```yan ang driver na ginagamit ng webcam mo.

gumamit ka na ng mga webcam application para masubukan mo talaga kung may output ang webcam mo.

isang well known na webcam application ng linux ay **cheese**. pwede mo ring subukan sa mga messenger application na na-mention sa taas.

Thanks Chief! Nga po pala, nakapag-install na po ako ng KOPETE. Pero pag kino-connect ko na po sya thru YM by my Yahoo ID eh ang tagal pumasok. Lagi lang syang "connecting" ang status nya. Ano po kaya ang problema regarding dun? Susubukan ko na po sana yung cam ko kaso ganun naman po ang nangyari. Nakapag-preview na po pala ako ng cam ko. Aksidenteng nahagilap ko sya sa Settings ng Kopete. :) Dun ko na nakita yung mukha ko! :lolflag:

---

### Post by loell on 2009-08-14
> **Extra Rice said:**
> 
Thanks Chief! Nga po pala, nakapag-install na po ako ng KOPETE. 

may ginawa kasi ang yahoo nung isang buwan, ginawan  na siguro ng kopete team ng paraan nyan para maka-connect uli.

ang kaso, yung kopete version na ginagamit mo, sa ubuntu repository galing, kaya di na yan ginagalaw para maka connect uli.

---

### Post by Script Warlock on 2009-08-14
> **Extra Rice said:**
> Ok Chief! Nagawa ko na po sya. Tapos po??? What should I do next? Sorry po kung medyo "igno" ako pagdating sa ganito.. newbie po kasi. :)



Thanks Chief! Nga po pala, nakapag-install na po ako ng KOPETE. Pero pag kino-connect ko na po sya thru YM by my Yahoo ID eh ang tagal pumasok. Lagi lang syang "connecting" ang status nya. Ano po kaya ang problema regarding dun? Susubukan ko na po sana yung cam ko kaso ganun naman po ang nangyari. Nakapag-preview na po pala ako ng cam ko. Aksidenteng nahagilap ko sya sa Settings ng Kopete. :) Dun ko na nakita yung mukha ko! :lolflag:

type ka lang sa terminal ng luvcview

for more info luvcview -h

---

### Post by Extra Rice on 2009-08-16
> **loell said:**
> may ginawa kasi ang yahoo nung isang buwan, ginawan  na siguro ng kopete team ng paraan nyan para maka-connect uli.

ang kaso, yung kopete version na ginagamit mo, sa ubuntu repository galing, kaya di na yan ginagalaw para maka connect uli.

So, ano po ang pwede kong gawin chief para makapagre-install ng bagong version ng Kopete? Kaya naman pala ayaw nyang mag-connect.

> **Script Warlock said:**
> type ka lang sa terminal ng luvcview

for more info luvcview -h

Ok Chief! Thanks a lot!

---

### Post by loell on 2009-08-16
> **Extra Rice said:**
> So, ano po ang pwede kong gawin chief para makapagre-install ng bagong version ng Kopete? Kaya naman pala ayaw nyang mag-connect.


I'm not really a kopete user, so i have no idea on where to get a fixed version.

---

### Post by Extra Rice on 2009-08-16
> **loell said:**
> I'm not really a kopete user, so i have no idea on where to get a fixed version.

Ganun po ba Chief? Anyways, nag-try din po ako sa GYachI. Tapos nagawa ko na po yung about sa PPA. Ask ko na lang po kung paano ko ma-iinstall yung GYachI? Wala po bang command yun para sa terminal? Baka sakali po kasing dun ako mag-online sa GYachI. Thanks po!

ALREADY SOLVED!!!

Thanks Chief! It helps a lot!

Mabuhay!

---

