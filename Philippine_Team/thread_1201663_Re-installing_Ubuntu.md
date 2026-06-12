---
title: "Re-installing Ubuntu"
date: 2009-07-01
forum: Philippine Team
---

### Post by zilu54 on 2009-07-01
hayan...kung hindi aku pinapansin sa pag rereply ku sa thread, mabuting gumawa aku ng sarili lols!

Iisa na lang naman ang sinasabi, patuluy na lang pa balik balik ang "GRUB Loading Stage 1.5."

```

terminal:
sudo grub
find /boot/grub/stage1
root (ang number na lumabas sa find "hd0,4")
setup (then palitan ng "hd0")
quit

```
yan ang madalas kong ginagamit kapag bumabalik ang error.

Naisipan ku na lang na i-reinstall na lang ulit at sabi raw ay yun na lang ang sulusyon, gustu ku sanang humingi ng tulung kung papaanu matanggal ang Ubuntu sa boot dahil dual boot po ito? pwede bang ma back up yung mga software na na download tulad ng scribus *kasi nakakatamad nang i-download ulit kasi ang tagal*

...pasensya na kung masyado na akung makulit, gustu ku lang matuto at matigil na tong lintik na paulit-ulit na "GRUB Loading Stage 1.5." na yan eh wala naman sumasagut kung paanu ayusin kaya i-reinstall na lang kaysa pa umasa sa mga mag rereply na hindi na nag paparamdam *tinatakasan ang kakulitan ko o sadyang wala talagang makaka sagot ng tanong ko*

---

### Post by kiminaiseah on 2009-07-01
na try mo na 

$sudo update-grub

baka kasi nag update ka ng kernel at wala naman yung linux-image, hindi talaga yan mag bo-boot

---

### Post by gamels on 2009-07-01
zilu54 matagal bah ang update nun?? naka DSL kaba??? o dial-up lang??? kung DSL ilang oras???

---

### Post by kiminaiseah on 2009-07-01
try practicing apt-cacher-ng para save sa bandwidth and time for download repo's kung nang hihinyang ka download ng repo

---

### Post by wersdaluv on 2009-07-01
> **zilu54 said:**
> hayan...kung hindi aku pinapansin sa pag rereply ku sa thread, mabuting gumawa aku ng sarili lols!

Iisa na lang naman ang sinasabi, patuluy na lang pa balik balik ang "GRUB Loading Stage 1.5."

```

terminal:
sudo grub
find /boot/grub/stage1
root (ang number na lumabas sa find "hd0,4")
setup (then palitan ng "hd0")
quit

```
yan ang madalas kong ginagamit kapag bumabalik ang error.

Naisipan ku na lang na i-reinstall na lang ulit at sabi raw ay yun na lang ang sulusyon, gustu ku sanang humingi ng tulung kung papaanu matanggal ang Ubuntu sa boot dahil dual boot po ito? pwede bang ma back up yung mga software na na download tulad ng scribus *kasi nakakatamad nang i-download ulit kasi ang tagal*

...pasensya na kung masyado na akung makulit, gustu ku lang matuto at matigil na tong lintik na paulit-ulit na "GRUB Loading Stage 1.5." na yan eh wala naman sumasagut kung paanu ayusin kaya i-reinstall na lang kaysa pa umasa sa mga mag rereply na hindi na nag paparamdam *tinatakasan ang kakulitan ko o sadyang wala talagang makaka sagot ng tanong ko*

Hindi ko sigurado kung tama ang pagkakaintindi ko sa problema mo pero kung kailangan mo lang i-reinstall ang grub
```
sudo grub
```
```
root (hd0,4)
```
```
setup (hd0)
```
```
quit
```

---

### Post by zilu54 on 2009-07-01
@kiminaseah: ginawa ku yung pag update ng grub at itu ang lumabas
> debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
Searching for GRUB installation directory ... found: /boot/grub
/dev/sda5: error opening volume
/dev/sda5: error opening volume
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
cp: cannot remove `/boot/grub/menu.lst~': Permission denied

paanu po i-apply ang apt-catcher?

@gamels: smartbro wifi (antenna) ang gamit ku at umaabut minsan ng oras din kasi may time talaga na bumabagal ng connection ku *ang dami kasing puno ditu*

@wersdaluv: hayun po, paulit ulit ku na lang ginagawa then after ng ilang boots ulit ay babalik at babalik yung pambihirang GRUB Loading na yan lols~

---

### Post by dodimar on 2009-07-01
> **zilu54 said:**
> @kiminaseah: ginawa ku yung pag update ng grub at itu ang lumabas

paanu po i-apply ang apt-catcher?

@gamels: smartbro wifi (antenna) ang gamit ku at umaabut minsan ng oras din kasi may time talaga na bumabagal ng connection ku *ang dami kasing puno ditu*

@wersdaluv: hayun po, paulit ulit ku na lang ginagawa then after ng ilang boots ulit ay babalik at babalik yung pambihirang GRUB Loading na yan lols~

do you have any usb drives or external hdd?

Wala bang lumalabas na error message from Grub?

---

### Post by kiminaiseah on 2009-07-01
nag sudo kaba? kasi permission denied eh

---

### Post by zilu54 on 2009-07-01
@sir. dodimar: yung mga sinasaksak kong Flash drives? wala naman pong lumalabas....

@kiminaiseah: sinundan ku lang po yung sinabi nyu "$sudo update-grub" :)

---

### Post by ragadanga63 on 2009-07-02
May nakasaksak bang mga USB drives habang nagboot ka?  Subukan mong i unplug.

---

### Post by gamels on 2009-07-02
KUNG WALA TALAGA TRY RE-INSTALL LANG.. PARA WALA NA SAKIT SA ULO.. HEHEH...:lolflag: JOKE LANG....

---

### Post by Script Warlock on 2009-07-02
dali lang naman reinstall ubuntu:guitar:

---

### Post by wersdaluv on 2009-07-02
Dito ka magtanong [http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

---

### Post by zilu54 on 2009-07-02
hmmm kung i-rereinstall ku tu eh di parang bagung format ulit itung ubuntu ku?

---

### Post by zeroseven0183 on 2009-07-03
I think reinstallation/reformat is the last option you have if everything else fails. But you still have options, just search the forums.
 
"Ask and you will receive. Seek and you will find..."
 
 
Help ka namin. Wait lang.. We're thinking pa eh.

---

### Post by dodimar on 2009-07-03
> **zilu54 said:**
> hmmm kung i-rereinstall ku tu eh di parang bagung format ulit itung ubuntu ku?

pag nag boot ka ba ay may mga naka saksak na USB drives?

kasi on some mobo it nagugulo nya yung drive mapping...

---

### Post by zilu54 on 2009-07-05
@zeroseven: ahaha maraming salamat ^^ sa tutuo lang eh hanap na aku ng hanap sa solution ng problem ku, sa ngayun ay busy sa school kaya hindi gaanung mahanapan ng paraan sa pag ayus nitu.

@sir.dodimar: wala naman pong naka saksak na kahit anu kundi ang CD ng ubuntu habang nag iinstall.

---

### Post by zeroseven0183 on 2009-07-06
Check out mhelios' advise in [http://forums.fedoraforum.org/archive/index.php/t-235.html](http://forums.fedoraforum.org/archive/index.php/t-235.html)

---

