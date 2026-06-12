---
title: "Can I decode this?"
date: 2011-11-01
forum: Programming Talk
---

### Post by Jose Catre-Vandis on 2011-11-01
Just a wild shot, but I have a text file full of numbers and "computer code", wondering if it possible to feed it into or through something to get readable text (I know it is readable text in the program it came from, but can't extract it from the program. It is from a Windows program.

Here is a screenshot of the first few entries (there are @ 9000 of them!) when the file is opened up in Leafpad/Geany

[ATTACH]206091[/ATTACH]

Thanks

---

### Post by papibe on 2011-11-01
Not sure what you want, but may be 'od' can help you?
```
$ od -x new_acer.bin 
0000000 ff00 ffff ffff 00ff a34c 324c 0000 0000
0000020 1200 0301 2380 7814 870a 94f5 4f57 278c
0000040 5027 0054 0000 0101 0101 0101 0101 0101
0000060 0101 0101 0101 1c41 a056 0050 3016 2030
0000100 0025 c661 0010 1900 0000 0f00 0000 0000
0000120 0000 0000 1e00 02b4 0074 0000 fe00 5300
0000140 4d41 5553 474e 200a 2020 2020 0000 fe00
0000160 3100 3036 5441 3130 412d 3530 200a b300
0000200

$ od -a new_acer.bin 
0000000 nul del del del del del del nul   L   #   L   2 nul nul nul nul
0000020 nul dc2 soh etx nul   # dc4   x  nl bel   u dc4   W   O  ff   '
0000040   '   P   T nul nul nul soh soh soh soh soh soh soh soh soh soh
0000060 soh soh soh soh soh soh   A  fs   V  sp   P nul syn   0   0  sp
0000100   % nul   a   F dle nul nul  em nul nul nul  si nul nul nul nul
0000120 nul nul nul nul nul  rs   4 stx   t nul nul nul nul   ~ nul   S
0000140   A   M   S   U   N   G  nl  sp  sp  sp  sp  sp nul nul nul   ~
0000160 nul   1   6   0   A   T   0   1   -   A   0   5  nl  sp nul   3
0000200

```
Does that help?
Regards.

---

### Post by Jose Catre-Vandis on 2011-11-01
Well, it's a step in the right direction but not really a full translation ;) :

Original
```
000000 Òž÷é¤”Â†Û‘ÿÌç

000001 ìÉäëÆ½«¸ž½Í›ÌèÍÕÇ—

000002 ú¦ÉØ–ÜÊÐ›®éÔëŸñ‹ß¹ï«“ßÇìü

000003 €ˆÛ¹·é°ü³é’éÓ

000004 •ò*ÝÇ÷ÏòÂÙëÈÌóÏÈÏÙêõ×Îæ÷¯«¥Öžù–ÚÆ±€»*Ç»Æ–Íû•šÝî
```
After od
```
0000000   0   0   0   0   0   0  sp   R  rs   w   i   $ dc4   B ack   [
0000020 dc1 del   L   g  cr  nl   0   0   0   0   0   1  sp   l   I   d
0000040   k   F   =   +   8  rs   =   M esc   L   h   M   U   G etb  cr
0000060  nl   0   0   0   0   0   2  sp   z   &   I   X syn   \   J   P
0000100 esc   .   i   T   k  us   q  vt   _   9   o   + dc3   _   G   l
```

Thanks

---

### Post by Bachstelze on 2011-11-01
Where does the file come from exactly and how is it normally used? We're shooting in the dark if we don't know that.

---

### Post by Jose Catre-Vandis on 2011-11-02
It's a list of ODB II Vehicle Fault Codes. The code number on the left is the code, the gobbledegook on the right is the English explanation of the code.

From the program VCDS-Lite by Ross Tech

I just wanted to see if I could get the list of fault codes out using linux.

Full list of the codes is available [here]("http://www.gerritspeek.nl/vag-com_foutcodeslijst-en.html") so the info is in the public domain, so this is now an exercise in the art of the possible ;)

---

### Post by ofnuts on 2011-11-02
Don't get fooled by linefeeds. This file probably encodes the length of things and linefeeds may just be the indication that there is a field with a length of 10 coming.

The big question is whether the file is:

[list]
[*]trivially re-encoded (base64 or else)
[*]trivially encrypted/obfuscated (XOR)
[*]compressed
[*]encrypted
[/list]

My gut feeling is that it's obfuscated because it's an "asset" of the program.

---

### Post by Jose Catre-Vandis on 2011-11-02
This "obfuscated" sounds terminal! :)

---

