---
title: "paano i activate ang desktop effects sa hardy heron"
date: 2008-05-12
forum: Philippine Team
---

### Post by eryllex on 2008-05-12
gud day mga bro..newbie lang aq sa ubuntu..gusto q i activate ung desktop effects..pwde bang turuan nyo aq..tnx

---

### Post by hermes0710 on 2008-05-12
Do you speak english?

---

### Post by loell on 2008-05-12
alam mo ba kung anong graphics card ang gamit mo?

---

### Post by jepong on 2008-05-12
> **hermes0710 said:**
> Do you speak english?

Sorry man! This is the Philippine LoCo Team so we can speak our local language. :guitar:

---

### Post by hermes0710 on 2008-05-12
My bad, sorry. I thought i could help :)

---

### Post by jepong on 2008-05-12
kung ayos yung video card i think by naka-default na yun... 

anyway, Click from the Panel... Preference -> Appearance --> Visual Effects

---

### Post by eriolle on 2008-05-12
paano b malaman kung anu ang graphics card ng laptop q? ang alam q lang is intel celeron, 512mb ram, 60gb hd.. at saka na try q nrin ung Preference -> Appearance --> Visual Effects

---

### Post by loell on 2008-05-12
para malaman natin yung card mo, type mo sa terminal/console

```
lspci
``` 

copy paste mo dito.

---

### Post by eriolle on 2008-05-12
pacensia na pero were q itatype un?bago lang tlaga aq sa ubuntu eh

---

### Post by loell on 2008-05-12
sa **Applications** menu  --> **Accessories** menu 

click mo yung
 

**Terminal**

---

### Post by killer_d76 on 2008-05-12
bro dun sa upper portion ng screen mo look for terminal click mo yun, then type mo dun yung code na bigay na sir Loell.. and it will give you a list, copy and paste it here, they may be able to help you as far as they can ;) believe me they will, i had issues with "gutsy" looky here:[http://ubuntuforums.org/showthread.php?t=720340](http://ubuntuforums.org/showthread.php?t=720340)       and check out the result!.. all of this won't be possible without their help :popcorn:


[ [IMG]http://www.imagehosting.com/out.php/i1749819_Screenshot.png[/IMG]](http://www.imagehosting.com)

---

### Post by Nhatz on 2008-05-12
so heto pang newbie talaga...
sundan mo yung instruction ni loell then pag alam mo na yung brand ng graphics card mo (either nvidia,ati,intel lang yan)
kung intel graphics card mo walang problema pero kung nvidia or ati dapat install mo muna yung drivers nila... para madali download ka ng "envy" heto link ..[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) install moyan then install mo yung driver ng graphics card mo.....

then para sa effects type mo to sa terminal

```
sudo apt-get install compizconfig-settings-manager
```

then pag ok na...
punta ka System --> Preferences --> Advanced Desktop Effects Setting
then configure mo na kung ano gusto mong desktop effects...
hehehe:)

sana nakatulong yan.
Astig! :guitar:

---

### Post by ache109 on 2008-06-14
e2 ung graphics card ko:
S3 Inc. VT8375 [ProSavage8 KM266/KL266]
naitry ko na yung sa appearance prefrences kaya lang pag isiswitch ko na sa normal ganto lumalabas...

---

### Post by king leoric on 2008-06-14
> **ache109 said:**
> e2 ung graphics card ko:
S3 Inc. VT8375 [ProSavage8 KM266/KL266]
naitry ko na yung sa appearance prefrences kaya lang pag isiswitch ko na sa normal ganto lumalabas...

I don't think compiz is supporting S3 Prosavage at the moment. But try to ask Mr. Google :lolflag:

---

