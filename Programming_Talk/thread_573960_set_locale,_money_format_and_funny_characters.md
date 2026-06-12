---
title: "set locale, money format and funny characters"
date: 2007-10-12
forum: Programming Talk
---

### Post by ntom-taylor on 2007-10-12
Hello

I have been trying to use setlocale( ) in my php to set the correct currency for a website. Unfortunately its producing odd looking characters, i've googled and aren't quite sure what todo next. 

Please have a look @ the following:


ntom@TheatonsServer:~/www/Simulator/MWD$ locale
LANG=en_GB.UTF-8
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC="en_GB.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY="en_GB.UTF-8"
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"
LC_IDENTIFICATION="en_GB.UTF-8"
LC_ALL=
ntom@TheatonsServer:~/www/Simulator/MWD$ locale -a
C
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX


doing.. 
setlocale(LC_ALL, 'en_GB.utf8');

then doing .. 
 money_format('%.2n', $price) 

and getting the following results

Setting to 
	en_US.utf8 = $5.00 - $10.00

Setting to 
        en_IE.utf8 = â&#65533;¬5.00 - â&#65533;¬10.00

Setting to 
	en_GB.utf8 = Â£5.00 - Â£10.00


Please help

---

### Post by ntom-taylor on 2007-10-18
Issue solved, simply reinstalled the locale's

---

