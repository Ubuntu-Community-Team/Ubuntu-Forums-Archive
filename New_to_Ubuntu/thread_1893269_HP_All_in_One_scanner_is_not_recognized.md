---
title: "HP All in One scanner is not recognized"
date: 2011-12-09
forum: New to Ubuntu
---

### Post by joshswain123 on 2011-12-09
I have an HP psc-1300 series hooked up to my Lubuntu 11.10 installation, and printing works like a charm, without me even trying. But it won't recognize the scanner. Thoughts?

---

### Post by Rodney9 on 2011-12-09
Thanks to Orographic - 

> Just wanted to let Lubuntu users know of an issue when using Simple Scan. I just couldn't get it to detect my HP F2280 scanner although the print function on the same printer/scanner was fine.

For some reason Lubuntu 11.10 doesn&#8217;t install all of the packages needed for Simple Scan to detect a scanner. Make sure &#8216;libsane-hpaio&#8217; or similar is installed and this will usually also install 'sane-utils' and 'hplip' as well - these three were missing by default. Then, the scanner should be recognised. 

I worked this out by typing libsane into Mint 11 Synaptic and finding some of the packages that were missing in Lubuntu 11.10. Mint 11 (on this same machine, on another hard drive) recognised my printer/scanner no problems as did Ubuntu Unity. Not sure why Lubuntu didn't install these packages by default...
__________________



For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by joshswain123 on 2011-12-10
I tried that, and the only difference I noticed was that my printer stopped working also. :/ And in the process of trying to figure it out, I accidentally deleted the printer from Printing preferences...

---

### Post by joshswain123 on 2011-12-10
I just did a little desk reconfiguration (moved the printer so I could connect it without a USB extension cord. And that seemed to fix the printing problem!

---

### Post by joshswain123 on 2011-12-10
Scanner works too! The world has been saved! Huzzah!

@Rodney9, Thank you for the help :)

---

### Post by Dave813 on 2012-01-29
Thank you it worked first time

---

### Post by gordie69 on 2013-02-22
I just putLubuntu 12.10 32 bit on a friends desktop and they have a hp c4345 all in one printer and I got the printer configured but the simple scan won't detect scanner

---

### Post by wildmanne39 on 2013-02-22
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

