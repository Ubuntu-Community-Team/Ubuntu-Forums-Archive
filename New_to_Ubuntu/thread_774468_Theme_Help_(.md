---
title: "Theme Help :("
date: 2008-04-29
forum: New to Ubuntu
---

### Post by feedmeh8 on 2008-04-29
so i installed this new theme "Ubuntusatanic" and it looks really nice and i configured it with compiz and my cube was roatating fine and my windows were nice and wobbly. BUT!! .... relog..and WTF! cube is gone, no wobbly windows .. and there all selected in advanced desktop settings. 

i find problem..Visual Effects are set to none. If i try to change it to normal or extra. i get : 

"Desktop Effects could not be enabled"

any help would be awesome :D ty

---

### Post by Saint Angeles on 2008-04-29
> **feedmeh8 said:**
> so i installed this new theme "Ubuntusatanic" and it looks really nice and i configured it with compiz and my cube was roatating fine and my windows were nice and wobbly. BUT!! .... relog..and WTF! cube is gone, no wobbly windows .. and there all selected in advanced desktop settings. 

i find problem..Visual Effects are set to none. If i try to change it to normal or extra. i get : 

"Desktop Effects could not be enabled"

any help would be awesome :D ty
in a terminal, type: compiz --replace

lets see the results

---

### Post by feedmeh8 on 2008-04-29
ty for help :) 

here it is : 

bob@Bato:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 0c) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: Segmentation fault
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present. 
aborting and using fallback: /usr/bin/metacity

---

