---
title: "Flashplayer choppy"
date: 2009-06-28
forum: Philippine Team
---

### Post by vidgen13 on 2009-06-28
Guys tanong ko lng baka matulungan nyo ko, choppy ba videos nyo sa youtube pag fullscreen? I need help. Here's what I have:

Debian lenny + Iceweasel 3.06 + Adobe flash version 10,0,22,87

Pag hindi choppy ang youtube nyo pag fullscreen, favor naman baka pede papost ng xorg.conf nyo chka version ng flash.

Maraming salamat!!!
more power to pinoy linuxers

---

### Post by badrra on 2009-06-28
Same version of Flash

My xorg.conf

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "WSE86K"
    HorizSync       30.0 - 86.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5500"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "1280x600" "1024x600"
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "1280x960 +0+0"
# Removed Option "metamodes" "1440x900 +0+0; 1024x768 +0+0"
# Removed Option "metamodes" "1360x768 +0+0"
# Removed Option "metamodes" "1280x960 +0+0"
# Removed Option "metamodes" "1024x768 +0+0"
# Removed Option "metamodes" "1280x960 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


btw choppy di sakin hehehehhe. 

Sa windows ko ganun din e so I assumed na medyo mabagal PC ko.

---

### Post by vidgen13 on 2009-06-29
Hehe salamat kasi cinonfigure ko lng ung sakin ng
dpkg-reconfigure -phigh xserver-xorg tapos parang kulang kulang lumabas sa xorg, try ko ung ibang settings kung gagana. Di ako makapanood ng maayos choppy mag fullscreen lol.

---

### Post by loell on 2009-06-29
hindi kaya vesa driver ang ginamit ng xorg mo? kaya naging choppy ang movie rendering?

---

### Post by zilu54 on 2009-06-29
kahit ditu sa desktop ku masyadung choppy...
kahit hindi siya naka full screen ay naku lumalaktaw ang video eh lalu na pag naka full na siya tsk~

kala ku kasi naka vid card ku eh nung nasa windows aku ayus na ayus naman siya?

---

### Post by vidgen13 on 2009-07-01
hinde vess ginamit ko, "openchrome" ung driver na nilagay ko, kc built in ung video card, pero pag nanunuod naman ako ng movie kahit fullscreen ok lng e,flash lng talaga. Dual boot din ako e, windows ko pang games at pag may di ako mapagana sa linux tapos nagmaamdali ako para kumpunihin. Salamat sa inyo.

---

### Post by loell on 2009-07-01
ah i see, yeah that symptoms is more or less the same with the others

try adding the vbemodes though, might see some improvement.

```
Section "InputDevice"
    Driver "openchrome"
    Option "VBEModes"  "boolean"
EndSection
```

---

### Post by vidgen13 on 2009-07-02
hehe ayaw p rin e bulokers monitor ko nagfflicker naman pero ok lng thanks magrereasearch aku marami pala pede kasama na options ito bukod sa vbe

---

### Post by badrra on 2009-12-03
you will find a solution to this problem on [this]("http://badrra.wordpress.com/category/firefox/") site. 

I just solved this problem and right now I am enjoying youtube. 

Have fun.

---

### Post by jaceleon on 2009-12-03
@baddra

Yung ipinayo mo na user script, e nagdidisable ng ibang addons ko for youtube, like my youtube2mp3.

Lag nga pag flash, at okay yung performance under vlc, pero sana ma-refine pa nila yung script para di makadisable ng ibang addons.

Also, hindi ko alam mag fullscreen sa youtube with that user script. Know how?

---

### Post by badrra on 2009-12-03
double click to fullscreen.

You can probably try disabling VLC w/o Flash or double click on the greasemonkey icon to disable it and see if the other plugins will work.

---

### Post by sixrodriguez on 2009-12-05
> **vidgen13 said:**
> hinde vess ginamit ko, "openchrome" ung driver na nilagay ko, kc built in ung video card, pero pag nanunuod naman ako ng movie kahit fullscreen ok lng e,flash lng talaga. Dual boot din ako e, windows ko pang games at pag may di ako mapagana sa linux tapos nagmaamdali ako para kumpunihin. Salamat sa inyo.

buit in yung video card mo......

activated ba effects ng linux mo......

---

