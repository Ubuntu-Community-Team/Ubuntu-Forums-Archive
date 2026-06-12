---
title: "visual effect problem"
date: 2009-02-23
forum: Philippine Team
---

### Post by guitar_man on 2009-02-23
Magandang Hapon mga Ginoo...
Patulong naman.Kanina ko pa iniisip tong problema ko.

Kapag in-enable ko yung visual effects ko yung button sa taas ng windows ay nawawala.Naging problema ko na to dati nakalimutan ko lang ang ginawa.

---

### Post by loell on 2009-02-23
what's your video card spec?

meron kasing video card na di pwede ang desktop effects, meron ding kailangan muna ng drivers bago ma-enable.

---

### Post by guitar_man on 2009-02-23
nvidia fx 5200....medyo naguguluhan nga po ako sir loell..enabled naman yung effects pero ayaw lang talga magpakita yung buttons sa taas.
ininstall ko yung compiz kala ko pwede ko iconfigure yun sa Compiz>effect>window decoration kasi dun ko lang sati yun ginagawa pag nawawala yung mga buttons..pero wala pa din sir:(

---

### Post by loell on 2009-02-23
ah i see, so enabled na yung effects, wala lang window borders?

in the command line, type

```
compiz-manager
```

post the output.

---

### Post by guitar_man on 2009-02-23
sir eto po output(sa screenshot)...blanc terminal...yung white part na malaki terminal po yun pang enabled ang effect


pag type ko po compiz-manager sa terminal ganun din po nangyayari

---

### Post by loell on 2009-02-23
ok lets try interchanging/reloading the window decorator,

first install **compizconfig-settings-manager**

```
sudo apt-get install compizconfig-settings-manager
```

then execute it by typing

```
ccsm
```

edit-- sorry i meant not ccsm directly
instead of ccsm, it's

**fusion-icon --no-start**

after launching **fusion-icon --no-start** , you will see a faded light blue icon in the system tray, right click it --> you will see a menu --> go to **select window decorator** --> choose **Gtk window decorator**

post back what happens

---

### Post by guitar_man on 2009-02-23
oto po output ng 
> Building dependency tree       
Reading state information... Done
compizconfig-settings-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 255 not upgraded.



tpos po pag type ko CCsm sa terminal lalabas ang compizconfig settings manager....


tama po ba yung ginawa ko? or yung compiz fusion icon yung sinasabi nyo sir?

---

### Post by loell on 2009-02-23
> **guitar_man said:**
> 
tama po ba yung ginawa ko? or yung compiz fusion icon yung sinasabi nyo sir?

enedit ko yung previous post ko pakibasa na lang ulit.. :oops:

---

### Post by guitar_man on 2009-02-23
sir ok na nung nirestart ko po...pero may mga problem pa e...
last na po.hehe

kapag disabled yung effects ko sir 4 yung workspace ko pag enable naman nagiging 2 workspace lang...bakit ganun?may mga nabago sa compiz?dati kasi sa heron ok lahat sa akin

---

### Post by loell on 2009-02-23
> **guitar_man said:**
> sir ok na nung nirestart ko po...pero may mga problem pa e...
last na po.hehe

kapag disabled yung effects ko sir 4 yung workspace ko pag enable naman nagiging 2 workspace lang...bakit ganun?may mga nabago sa compiz?dati kasi sa heron ok lahat sa akin

good to know na ok na :)

in compiz fusion, to set your workspace back to 4 again,

launch **ccsm** --> in general --> general options --> "Desktop size" tab --> set Horizantal size to 4.

---

### Post by guitar_man on 2009-02-23
haha...ayos...salamat ng marami.
Your the best sir loell.hahaha.
Buti nalang nakakapagreply ka agad kahit holyday ngayun.haha
.God bless :D

---

### Post by loell on 2009-02-23
no problem. :)

---

### Post by guitar_man on 2009-02-24
sir how can i save the setting for the resolution?
ayaw kasi masave...

---

### Post by loell on 2009-02-24
```
sudo nvidia-settings
```

then change and save the desired settings

---

### Post by guitar_man on 2009-02-24
ahhh.kailangan pala naka super user para masave...
salamat...gandang tanghali.

---

### Post by loell on 2009-02-24
yeah, it needs to have a super user privilege to write the settings.

walang anuman , gandang hapon din. :)

---

