---
title: "pano makuha ang &quot;exact&quot; model ng video card"
date: 2008-09-16
forum: Philippine Team
---

### Post by dodimar on 2008-09-16
Naka score ako ng AGP video card from a friend. Maker is ATI, may DVI, VGA and S-Video out siya. 256mb.

Under WinXP, it shows ATI Radeon 9600 XT series. searched about it pero na-confuse lang ako. Wala namang nakalagay sa video card kung anong model siya.

I tried running Xubuntu 8.04 Live CD, pero pag nag load ng yung xfce, wala ng nag appear sa screen (maybe since it is ATI, I tried it using my old nvidia VC, and it's working properly).

I want to get the proper model for the card so i can properly use it (under XP and Ubuntu)/(I need the functionality for dual monitor and also the S-video).

Meron po bang certian command (using terminal) para makuha ko yung proper model ng video card?

Also during boot up, supposedly lalabas yung video card info before mag load yung BIOS, pero di po lumalabas eh, dahil siguro sa mobo.

Thanks po..

---

### Post by pendletone on 2008-09-16
dodimar, type this in terminal:

```
lspci | grep vga
```

this will give you your video card's manufacturer and model.

with regards to boot up, merong ibang mobo na hindi na pinapakita ang boot up sequence (usually this is replaced by the manufacturer's logo) kaya nde mo na nakikita yung video card info upon startup. if this is the case, try to disable it inside the BIOS setup.

uy kung meron ka pang na-score na video card dyan...paarbor naman! hehe :)

---

### Post by jsgotangco on 2008-09-16
what does *lspci* tell you?

---

### Post by dodimar on 2008-09-16
Haven't tried it (nasa work po kasi ako ngayun)..

Will try it when I get home..

With regards sa Video card... hehe,, naka jackpot lang.. actually pati mobo and processor yun.. Mobo nya is samsung, processor is Pentium III 800 mhz (256kb cache)... nakita ko lang nakatambak dun sa office ng tropa ko, dapat binibili ko nga ng 1500, binigay na lang sakin ng libre... yun lang, wala ng iba.. baka pag nag-upgrade uli siya... hehehe

i tried disabling yung logo ng samsung, pero siguro pinapakita nya pero sobrang bilis (o mabagal lang mag update , from sleep mode, yung monitor ko).

I'll try po at home and will post the result..

Tnx.

---

### Post by dodimar on 2008-09-19
Posting results in new thread...

---

