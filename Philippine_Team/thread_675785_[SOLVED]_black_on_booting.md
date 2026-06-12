---
title: "[SOLVED] black on booting"
date: 2008-01-23
forum: Philippine Team
---

### Post by februarius on 2008-01-23
guys paano ba gawing verbose booting palage, blackout ung screen pag nag boboot eh, kya gngwa ko plage ctrl+alt+f1 ko nlng para may makita ako upon booting

pero pag gngmitan ko sya ng 21 inches na monitor ayun kita ko sya pero ang laki masyado ng resolution almost 2048x1024 ata yun. eh kaya nung 15 inches ng monitor ko 1024x768 lang.

kya help nyo ko disable ko nlng ung loading screen, verbose nlng okay pa

---

### Post by Samhain13 on 2008-01-23
Mag-login ka dun sa TTY terminal mo, (yung CTRL + ALT + F1). Tapos tignan mo yung file na **/etc/X11/xorg.conf**:

```

sudo nano /etc/X11/xorg.conf

```

Tapos, hanapin mo yung section na parang ganito (heto yung sakin):

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV34 [GeForce FX 5500]"
        Monitor         "SAMTRON"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1600x1200"     "1280x1024"     "1024x768"     "800x600"        "640x480"
        EndSubSection
EndSection

```

Pansinin mo yung **Modes... "1600x1200"....**, yan ang available resolutions ng monitor mo. Kung sigurado kang 1024x768 lang ang kaya niya, burahin mo yung ibang mas malalaking values. Kunwari, kung sa xorg.conf ko gagawin yun:

```

before:
Modes           "1600x1200"     "1280x1024"     "1024x768"     "800x600"        "640x480"

after:
Modes           "1024x768"     "800x600"        "640x480"

```

Tapos, reboot. Sa 15 inch monitor mo, dapat makapasok ka na niyan sa GUI. Dun mo na lang ayusin yung prefered resolution mo: Preferences > Screen Resolution.

---

### Post by februarius on 2008-01-23
yoh paps nagawa ko na sya before pero ang nag babago langsakanya ung pagdating na sa login, curious lang ako kasi same hardware lang naman pinag titestingan ko, pero sa dapper, feisty okay naman kita ko ung loading picture sa booting, pero sa gusty di ko makita, need to ctrl+alt+fn para malaman ko kng nag boboot nga sya

---

### Post by loell on 2008-01-23
this is the doing of gutsy's **bulletproofx** 

i haven't figure out how to really disable it  to keep it from overwiting my xorg.conf.

i tried this [step]("https://answers.launchpad.net/ubuntu/+question/14320") months ago, but it seems bulletproofx still runs during startup :(

---

### Post by Nhatz on 2008-01-23
Baka sa resolution ng monitor yan... :(

---

