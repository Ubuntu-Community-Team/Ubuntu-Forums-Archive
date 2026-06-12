---
title: "T10 sa Ubuntu?"
date: 2008-09-25
forum: Philippine Team
---

### Post by JazonEsti on 2008-09-25
May nakasubok na ba na paganahin ang kanyang T10 (Epson Stylus T10) sa Ubuntu/Kubuntu? Kailangan ko nang magpalit ng printer eh. Salamat!

---

### Post by jsgotangco on 2008-09-25
I guess this is the new entry level Epson Printer. What I have is the Epson C90 which works great on Linux.

---

### Post by JazonEsti on 2008-09-25
Yes, it is. I have a C67 but inks are becoming harder to find and I fear on of the ink heads is permanently clogged.

---

### Post by mennn on 2008-09-27
I'm using hp deskjet d2460 and it work great with ubuntu 8.04, color and bw.

---

### Post by JazonEsti on 2008-09-27
Thanks! I was initially considering Epson because I want to attach a CIS someday, but looks like the HP also has a CIS system available.

---

### Post by dynastywarrior on 2008-09-29
I'm using Epson Stylus Photo RX430 in Ubuntu and it got detected automatically....**Ubuntu** have a ready software printer manager for **Epson** printers, complete with maintenance tab......

---

### Post by JazonEsti on 2008-09-29
For some reason, checking ink levels doesn't work with my C67. Thanks for the input, though.

---

### Post by taboga on 2008-10-10
do you know how to install epson stylus t10 on kubuntu.......please help..thanks in advance....

---

### Post by gimmejimmy on 2008-10-10
> do you know how to install epson stylus t10 on kubuntu.......please help..thanks in advance.... 

[https://help.ubuntu.com/8.04/printing/C/printing.html]("https://help.ubuntu.com/8.04/printing/C/printing.html")

Kubuntu pala:

[http://www.kubuntu.org/docs/kquickguide/C/ch02s05.html]("http://www.kubuntu.org/docs/kquickguide/C/ch02s05.html")

---

### Post by loell on 2008-10-11
CUPS can't detect T10 at the momment, there is no known work-around yet.

---

### Post by ragadanga63 on 2009-01-10
[http://ubuntuforums.org/showthread.php?t=964784&highlight=T10](http://ubuntuforums.org/showthread.php?t=964784&highlight=T10)

---

### Post by JazonEsti on 2009-01-16
Bought an HP 2560. No hassle driver installation.

---

### Post by royfmont13 on 2010-05-18
Guys pa help naman.

I have a Epson T10 and tried to install sa Ubuntu 10.04.   Na detect naman at na install pero pagdating sa test page... nag blink ang LED at gumalaw ang print heads pero di na print ang test page. Hindi gumana ang sheet feed. 

Any advice and solutions will be much appreciated! TIA!

---

### Post by Script Warlock on 2010-05-19
i'm using T10 sa shop eto gamit ko make and model - Epson Stylus T20 - CUPS+Gutenprint (OpenPrinting LSB 3.2) v5.2.4 Simplified

---

### Post by royfmont13 on 2010-05-19
sir pano na lang ibalik sa version 5.2.4 ang cups-driver-gutenprint?  Mukhang gumagana sa version na yan ang epson T10?  Newbie pa po ako sa ubuntu.

---

### Post by Script Warlock on 2010-05-19
sorry nakalimutan kong sabihin sayo na eto ay sa 9.04 pala, pwede mo bang hintayin feedback ko bukas upgrade ko na server sa shop from 9.04 to 10.04 at t10 pa rin ang gagamitin kong printer.

---

### Post by Script Warlock on 2010-05-20
di ko pa napagan ics ng ubuntu lucid any links? at epson t10 di rin gumana... eh kung ayaw talaga then balik ko na lang muna sa 9.04 ang server ko pero sa clients eto na gagamitin ko.

---

### Post by nugencs on 2010-05-20
> Guys pa help naman.

I have a Epson T10 and tried to install sa Ubuntu 10.04. Na detect naman at na install pero pagdating sa test page... nag blink ang LED at gumalaw ang print heads pero di na print ang test page. Hindi gumana ang sheet feed. 

Any advice and solutions will be much appreciated! TIA!

[Bug #576278]("https://bugs.launchpad.net/ubuntu/+source/gutenprint/+bug/576278")

para mapagana yung epson t10 sa 10.04 lucid, kelangan i-downgrade ang mga sumusunod na packages sa v5.2.4:

cups-driver-gutenprint v5.2.5
libgutenprint2 v5.2.5

para ma-downgrade, uninstall nyo muna ang mga packages na yan gamit ang synaptic o terminal. Tapos i-download at i-install nyo ang mga to (unahing i-install ang libgutenprint2 dahil nakadepende ang cups-driver-gutenprint dito):

[libgutenprint2 v5.2.4]("http://launchpadlibrarian.net/32019466/libgutenprint2_5.2.4-0ubuntu2_i386.deb") (for 32-bit)
[libgutenprint2 v5.2.4]("http://launchpadlibrarian.net/32020345/libgutenprint2_5.2.4-0ubuntu2_amd64.deb") (for 64-bit)

[cups-driver-gutenprint v.5.2.4]("http://launchpadlibrarian.net/32019464/cups-driver-gutenprint_5.2.4-0ubuntu2_i386.deb") (for 32-bit)
[cups-driver-gutenprint v.5.2.4]("http://launchpadlibrarian.net/32020343/cups-driver-gutenprint_5.2.4-0ubuntu2_amd64.deb") (for 64-bit)

---

### Post by echo2knight on 2010-05-21
> **nugencs said:**
> [Bug #576278]("https://bugs.launchpad.net/ubuntu/+source/gutenprint/+bug/576278")

para mapagana yung epson t10 sa 10.04 lucid, kelangan i-downgrade ang mga sumusunod na packages sa v5.2.4:

cups-driver-gutenprint v5.2.5
libgutenprint2 v5.2.5

para ma-downgrade, uninstall nyo muna ang mga packages na yan gamit ang synaptic o terminal. Tapos i-download at i-install nyo ang mga to (unahing i-install ang libgutenprint2 dahil nakadepende ang cups-driver-gutenprint dito):

[libgutenprint2 v5.2.4]("http://launchpadlibrarian.net/32019466/libgutenprint2_5.2.4-0ubuntu2_i386.deb") (for 32-bit)
[libgutenprint2 v5.2.4]("http://launchpadlibrarian.net/32020345/libgutenprint2_5.2.4-0ubuntu2_amd64.deb") (for 64-bit)

[cups-driver-gutenprint v.5.2.4]("http://launchpadlibrarian.net/32019464/cups-driver-gutenprint_5.2.4-0ubuntu2_i386.deb") (for 32-bit)
[cups-driver-gutenprint v.5.2.4]("http://launchpadlibrarian.net/32020343/cups-driver-gutenprint_5.2.4-0ubuntu2_amd64.deb") (for 64-bit)

Got the same problem. Already downgraded to the working version and locked it under synaptic.

Hope in the next version, the problem is already fixed.

---

### Post by royfmont13 on 2010-05-21
> **nugencs said:**
> [Bug #576278]("https://bugs.launchpad.net/ubuntu/+source/gutenprint/+bug/576278")

para mapagana yung epson t10 sa 10.04 lucid, kelangan i-downgrade ang mga sumusunod na packages sa v5.2.4:

cups-driver-gutenprint v5.2.5
libgutenprint2 v5.2.5

para ma-downgrade, uninstall nyo muna ang mga packages na yan gamit ang synaptic o terminal. Tapos i-download at i-install nyo ang mga to (unahing i-install ang libgutenprint2 dahil nakadepende ang cups-driver-gutenprint dito):

[libgutenprint2 v5.2.4]("http://launchpadlibrarian.net/32019466/libgutenprint2_5.2.4-0ubuntu2_i386.deb") (for 32-bit)
[libgutenprint2 v5.2.4]("http://launchpadlibrarian.net/32020345/libgutenprint2_5.2.4-0ubuntu2_amd64.deb") (for 64-bit)

[cups-driver-gutenprint v.5.2.4]("http://launchpadlibrarian.net/32019464/cups-driver-gutenprint_5.2.4-0ubuntu2_i386.deb") (for 32-bit)
[cups-driver-gutenprint v.5.2.4]("http://launchpadlibrarian.net/32020343/cups-driver-gutenprint_5.2.4-0ubuntu2_amd64.deb") (for 64-bit)


Sir thanks!  Baka pwede po step by step procedures and command syntax.  Newbie pa 
po kasi di ko po alam kung paano po yun sa synaptic.

Thanks!

---

### Post by echo2knight on 2010-05-22
> **royfmont13 said:**
> Sir thanks!  Baka pwede po step by step procedures and command syntax.  Newbie pa 
po kasi di ko po alam kung paano po yun sa synaptic.

Thanks!

Brod, here are the steps.

1. Download the above packages depending on your system (32bit or 64bit);

2. Look for the 2 packages in synaptic then uncheck them. This will uninstall the packages from your system;

3. Proceed to the folder where you downloaded the above 2 packages, then double click first on libgutenprint2_5.2.4-0ubuntu2_(i386/amd64).deb, this will now install the package to your system, then double click on cups-driver-gutenprint_5.2.4-0ubuntu2_(i386/amd64).deb;

4. Now run synaptic and search for the 2 packages, highlight the package, then from the menu choose PACKAGE>LOCK VERSION.

Thats it, you're ready to go. Hope this helps!!!!

---

### Post by royfmont13 on 2010-05-24
> **echo2knight said:**
> Brod, here are the steps.

1. Download the above packages depending on your system (32bit or 64bit);

2. Look for the 2 packages in synaptic then uncheck them. This will uninstall the packages from your system;

3. Proceed to the folder where you downloaded the above 2 packages, then double click first on libgutenprint2_5.2.4-0ubuntu2_(i386/amd64).deb, this will now install the package to your system, then double click on cups-driver-gutenprint_5.2.4-0ubuntu2_(i386/amd64).deb;

4. Now run synaptic and search for the 2 packages, highlight the package, then from the menu choose PACKAGE>LOCK VERSION.

Thats it, you're ready to go. Hope this helps!!!!


Thanks Sir!  +1 Karma po sa inyo! at sa lahat ng ng reply!

---

### Post by Script Warlock on 2010-10-17
Epson t10 is now working on meerkat using the t20 driver...

---

### Post by echo2knight on 2010-10-26
> **Script Warlock said:**
> Epson t10 is now working on meerkat using the t20 driver...

Well, thats good news!

I am yet to fresh install meerkat in my lappy. Corrupted na kasi installation ng lucid ko.

---

