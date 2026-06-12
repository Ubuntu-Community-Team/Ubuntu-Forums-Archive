---
title: "Can't change fonts"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by PLIACHAS PASCHALIS on 2008-10-13
I TRY TO CHANGE FONTS ON OPEN OFFICE USING GREEK LETTERS, BUT EXCEPT DEJAvU sERIF ALL OTHER FONTS SEEMS THE SAME, CORRECT ME IF I'M WRONG. IS THIS A BUG; HOW CAN I CORRECT THIS;
THANKS A LOT

---

### Post by Orange_and_Green on 2008-10-13
&#954;&#945;&#955;&#951;&#956;&#941;&#961;&#945; :)

Have you tried System->Administration->Language Support-> Adding support for Greek?

---

### Post by PLIACHAS PASCHALIS on 2008-10-14
&#915;&#949;&#953;&#945;:)
I tried but at lot fonts i don't see much differnce. Where can i find other fonts?

---

### Post by kostkon on 2008-10-14
> **PLIACHAS PASCHALIS said:**
> &#915;&#949;&#953;&#945;:)
I tried but at lot fonts i don't see much differnce. Where can i find other fonts?
First of all, you could install the Microsoft fonts package (it's called [*msttcorefonts*]("http://packages.ubuntu.com/hardy/msttcorefonts")).

Most of them have Greek support.

Also, you can search *Synaptic* for other fonts, e.g. the [*ttf-mgopen*]("http://packages.ubuntu.com/hardy/ttf-mgopen") fonts are a good option, if you don't have them already in your system.

---

### Post by Orange_and_Green on 2008-10-14
Oh I see, sorry for the misunderstanding :)

Try System->Applications->Synaptic package manager and download any (or all) of the following packages:

gsfonts-x11
msttcorefonts
xfonts-intl-european

I hope you find a font more pleasing to your eyes among these. If not, you can always create a directory called ".fonts" in your home folder, download a font of your choice from the Internet and extract it there. Then run
```
sudo fc-cache -fv
``` to rebuild the fonts cache.

Hope this helps, good luck:KS

---

### Post by PLIACHAS PASCHALIS on 2008-10-20
Thank you all

---

