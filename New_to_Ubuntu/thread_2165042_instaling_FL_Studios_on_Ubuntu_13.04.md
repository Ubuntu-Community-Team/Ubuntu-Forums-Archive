---
title: "instaling FL Studios on Ubuntu 13.04"
date: 2013-08-03
forum: New to Ubuntu
---

### Post by marlon2 on 2013-08-03
FL Studios is a music producing software that i use but my pc is a windows 8 got rid of that garbage and installed ubuntu instead. i like ubuntu but im new so how can i get this windows prgram to run here on ubuntu? and is it possible. if not i got no choice but to go to windows 7.

---

### Post by zombifier25 on 2013-08-03
FL Studios is a Windows program. To use it, you need to install [Wine](http://www.winehq.org/), which allows you to install Windows programs on Linux (with varying degrees of success). After a quick look on AppDB, it seems that FL Studios generally work well with Wine, but if it doesn't, I'm afraid you have no choice but to run Windows, either by dual-booting or in a virtual machine.

---

### Post by Vladlenin5000 on 2013-08-03
You can *probably* install that software using Wine, a sort of Windows emulator. However, that would be the worse solution. There are many free alternatives. If you're into production you should have a look at Ubuntu Studio and check what software it has bundled.

---

### Post by MirrorUniverse on 2013-08-03
Here is a tutorial I'm cutting and pasting from the FL studio forums so that FL Studios can be used with Wine:
"alright. codeweavers have a better tutorial, but there are only a few simple things u need to know. 
install wine, and wine-dev packages 
install jackd, libjack, qjackctl, and jack dev packages 
make sure u have your build essentials installed (if you plan to  compile the latest WineASIO. not needed if ur just downloading the .deb  file for WineASIO) 
if you are on ubuntu(im on ubuntu 10.04), download the WineASIO driver install package here:  [http://ubuntuforums.org/showthread.php?t=1241187](http://ubuntuforums.org/showthread.php?t=1241187) 
register WineASIO with regsvr32 wineasio.dll (open terminal to do that) 
open wine control pannel, and set the sound system to only use alsa 
start jack 
start fl 10 
make music 
[IMG]http://forum.image-line.com/images/smilies/icon_biggrin.gif[/IMG] 

from past experience as well, midi keyboards work great. my keystation 61 ES has no issues what so ever with FL on linux. 

more detailed, as i dont have time to do it fully: [http://www.codeweavers.com/compatibilit ... 405;tips=1]("http://www.codeweavers.com/compatibility/browse/name/?app_id=6405;tips=1") "

*********************

But you may want to give open source versions a try.  There is LMMS, Ardour, Qtractor, maybe others.
[http://ardour.org/](http://ardour.org/)
[http://lmms.sourceforge.net/](http://lmms.sourceforge.net/)
[http://qtractor.sourceforge.net/qtractor-index.html](http://qtractor.sourceforge.net/qtractor-index.html)

---

### Post by jahrasta6 on 2013-08-14
When I try to install the ASIO bit, I get "This driver is of bad quality. Installing this could seriously harm your computer. Please contact the distributor/developer." <-- something to that effect, anyway. Any ideas why? 

I've had FL Studio installed completely, but nothing shows properly. I'm using Ubuntu 13.04 and FL Studio 11 - but all of my menus (options, file, etc) don't have text, they drop down like normal - but there's nothing in them. I'm not sure what it is that I'm missing.

---

