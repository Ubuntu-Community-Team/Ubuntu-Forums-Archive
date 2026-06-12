---
title: "Cannot Mount Volume"
date: 2009-09-09
forum: Philippine Team
---

### Post by Extra Rice on 2009-09-09
Guys! Patulong naman po regarding sa pag-browse ko sa isang Hard drive ko. Ganito kasi ang error na lumalabas pag bubuksan ko na yung drive (see attachment). Ano pong pwedeng gawin para maayos po ito at para ma-browse ko na din po yung isang hard drive ko. Thanks in advance!

---

### Post by ache109 on 2009-09-09
> **Extra Rice said:**
> Guys! Patulong naman po regarding sa pag-browse ko sa isang Hard drive ko. Ganito kasi ang error na lumalabas pag bubuksan ko na yung drive (see attachment). Ano pong pwedeng gawin para maayos po ito at para ma-browse ko na din po yung isang hard drive ko. Thanks in advance!

sir check nyo po ung connection nung hard drive. baka may konting abnormalities. or kung partition lang yan ng hd mo, cguro ung format nung hard drive ung cause.  NTFS ba? oR FAT?

---

### Post by Extra Rice on 2009-09-09
> **ache109 said:**
> sir check nyo po ung connection nung hard drive. baka may konting abnormalities. or kung partition lang yan ng hd mo, cguro ung format nung hard drive ung cause.  NTFS ba? oR FAT?

Ok naman po sya chief. Actually, naka-dual boot ako sa WinXP. Sa XP, nade-detect naman yung hard drive ko, pero pag sa Ubuntu na yun na yung lumalabas na error nya. Cannot amount volume na daw. Sa pagkaka-alam ko, NTFS yung format nung isang hard drive ko. At hindi po sya naka-partition. Hiwalay po syang hard drive. Pang-back up ko po sya. Paano po kaya to?

---

### Post by ache109 on 2009-09-09
> **Extra Rice said:**
> Ok naman po sya chief. Actually, naka-dual boot ako sa WinXP. Sa XP, nade-detect naman yung hard drive ko, pero pag sa Ubuntu na yun na yung lumalabas na error nya. Cannot amount volume na daw. Sa pagkaka-alam ko, NTFS yung format nung isang hard drive ko. At hindi po sya naka-partition. Hiwalay po syang hard drive. Pang-back up ko po sya. Paano po kaya to?

di ko kasi masyado sure... pero just asked Mr.google about this matter. and mayroon ding similar problem sa iyo. May pagka issue din sya sa linux(ubuntu). I suggest to try googling a bit more, and ask natin ung mga pros. Laptop ko is using both  FAT partition. And so far ok naman... Try mo kaya reformat to FAT?

---

### Post by Extra Rice on 2009-09-09
> **ache109 said:**
> di ko kasi masyado sure... pero just asked Mr.google about this matter. and mayroon ding similar problem sa iyo. May pagka issue din sya sa linux(ubuntu). I suggest to try googling a bit more, and ask natin ung mga pros. Laptop ko is using both  FAT partition. And so far ok naman... Try mo kaya reformat to FAT?

Ang hirap kasing magre-format ulit chief! Buong back-up system ko na kasi yun e. Pero sige. Try ko syang i-format into FAT. Tignan ko kung ano ang changes. Thanks Chief! Ur the MAN!

---

### Post by kiminaiseah on 2009-09-09
try the FF:

sudo aptitude install ntfs-3g -y

then

mkdir -p ~/Desktop/ntfs-disk 
chmod 777 ~/Desktop/ntfs-disk

mount -o ntfs /dev/sda1 ~/Desktop/ntfs-disk

# palitan mo nalang yung sda1 with your correspdent partition specially pag 1st partion sda1, since kernel 2.6.2x yan kya sda pero kung 2.6.18 kernel mo baka hda1 pa yan.. hehehe

---

### Post by ache109 on 2009-09-09
> **kiminaiseah said:**
> try the FF:

sudo aptitude install ntfs-3g -y

then

mkdir -p ~/Desktop/ntfs-disk 
chmod 777 ~/Desktop/ntfs-disk

mount -o ntfs /dev/sda1 ~/Desktop/ntfs-disk

# palitan mo nalang yung sda1 with your correspdent partition specially pag 1st partion sda1, since kernel 2.6.2x yan kya sda pero kung 2.6.18 kernel mo baka hda1 pa yan.. hehehe

nice yan a...

---

### Post by ache109 on 2009-09-10
> **Extra Rice said:**
> Ang hirap kasing magre-format ulit chief! Buong back-up system ko na kasi yun e. Pero sige. Try ko syang i-format into FAT. Tignan ko kung ano ang changes. Thanks Chief! Ur the MAN!

Sir ok na hDD mo?

---

### Post by virilc on 2009-09-10
mas ok sana kung click mo yung Details no? hehehe

---

### Post by Extra Rice on 2009-09-10
> **kiminaiseah said:**
> try the FF:

sudo aptitude install ntfs-3g -y

then

mkdir -p ~/Desktop/ntfs-disk 
chmod 777 ~/Desktop/ntfs-disk

mount -o ntfs /dev/sda1 ~/Desktop/ntfs-disk

# palitan mo nalang yung sda1 with your correspdent partition specially pag 1st partion sda1, since kernel 2.6.2x yan kya sda pero kung 2.6.18 kernel mo baka hda1 pa yan.. hehehe

Sir. Medyo nagugulahan po ako sa "sda1" eh.

Ganito po kasi ginawa ko, dalawa po ang HDD ko. Parehong 40GB, so yung isang HDD ginawa kong primary at dun po ako ng install ng dual boot (Win xp and Ubuntu). Una ko pong in-install yung windows bago Ubuntu. Bali, 10GB sa Windows at 30GB sa Ubuntu. Then as usual, yung isang HDD ko (which is secondary), ginawa kong back-up para sa mga files, etc..

Ang problema ngayon, pag naglo-log in ako using Ubuntu hindi nya ma-detect yung back-up ko at lumalabas nga yung error na yun. Pero pag naglo-log in ako gamit naman ang windows, ok naman yung back-up ko at nagagamit ko naman sya. Sa pagkaka-alam ko po, finormat ko po sya sa windows with NTFS.

Eto po ang tanong ko, ano po sa tingin nyo ang SDAx ng secondary HDD ko para ma-unmount po sya at magamit ko din po as a back-up sa Ubuntu? :confused:

**@ ache109**
Sir, as of now hindi pa po ok yung HDD ko.

**@ virilc**
Sige po Sir! Attach po ako ng bagong screenshots.

Maghihintay po ako ng comments and suggestions nyo po!

Maraming Salamat po! Mabuhay!!! :guitar:

---

