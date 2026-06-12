---
title: "Canon MP 150"
date: 2013-05-16
forum: New to Ubuntu
---

### Post by Gleen on 2013-05-16
Hi all
I'm new with Linux

Wondering if anyone can help me with MP150 driver for ubuntu?
I'm Using Lubuntu 13.04
What I don't understand is that why the program "Simple scan" Can detect my printer and I can even scan with it.
While when I go to System tools>Printers., there are no printers found?

Thanks in advance

---

### Post by pdc on 2013-05-17
so this is a 7yr old printer and Canon did not provide the linux driver support then in the way that they do now: so one can today for example buy a Canon MG2100series printer for about $US35 with linux support;

for your MP150, I have googled; as there are no canon linux drivers; others did report that the drivers for the MP140 series worked ...........

......so can I suggest we try that?

You don't tell us if you have 32bit ...........assuming you do............ go here.........

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100083403.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100083403.html) and download the [COLOR="#008000"]cnijfilter-common_2.80-1_i386.deb[/COLOR] ........you need to let ubuntu software center install this deb package so either save to Downloads folder; right-click on icon in that folder, and select "install with USC.."

then the specific package

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100083701.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100083701.html) and what you download is [COLOR="#008000"]cnijfilter-mp140series_2.80-1_i386.deb[/COLOR]

.........you should then have the MP140 as a printer option to print with .............any joy?

.......after installing the driver, re-start your system .............

____________________________________________________________________________________-

for scanning, Canon make a scanning programme called [COLOR="#0000FF"]ScanGearMP[/COLOR] ........................for your MP printer................

go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100084701.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100084701.html) and you will download the [COLOR="#008000"]scangearmp-common_1.10-1_i386.deb[/COLOR] and install it as above

then go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100084801.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100084801.html) and download [COLOR="#008000"]scangearmp-mp140series_1.10-1_i386.deb[/COLOR] and install it

run the programme [COLOR="#0000FF"]ScanGearMP[/COLOR] by opening a terminal and issuing the command

> [COLOR="#FF0000"]scangearmp[/COLOR] ............I don't know about creating launchers in lubuntu ............... a launcher would create an icon for you ........perhaps you are happy with the terminal

I think this post may help though [http://ubuntuforums.org/showthread.php?t=1935461](http://ubuntuforums.org/showthread.php?t=1935461)

.........has anything here been of help?

---

### Post by Gleen on 2013-05-19
pdc

well
I am actually using 64bit Lubuntu on Thinkpad x100e
Will the files needed be different?
I tried to install cnijfilter-common_2.80-1_i386.deb & cnijfilter-mp140series_2.80-1_i386.deb
and I got problems with dependencies of libcupsys2
I had it solved through
[http://ubuntuforums.org/showthread.php?t=1305248](http://ubuntuforums.org/showthread.php?t=1305248)

However it didn't work for cnijfilter-mp140series_2.80-1_i386.deb

Any Idea about it?

Thanks
:)

---

### Post by pdc on 2013-05-19
these are 32bit drivers; and you have a 64bit system

try some symbolic links

> [COLOR="#FF0000"]sudo ln -s /usr/lib /usr/lib64[/COLOR]

> [COLOR="#FF0000"]sudo ln -s /usr/local/lib /usr/local/lib64[/COLOR]

then restart cups

> [COLOR="#FF0000"]sudo service cups restart[/COLOR]

any joy?

---

### Post by Gleen on 2013-05-19
Great

=D>
It works
Just printed out a test page

Thanks a lot

---

### Post by pdc on 2013-05-19
great! Enjoy!

.........did you get the scanner going?

---

### Post by Gleen on 2013-05-20
Yeah

The scanner was just fine from the beginning

\\:D/

So I didn't do anything about it

---

### Post by pdc on 2013-05-20
oh good............did you use the scangear?

If you want to tweak the printer settings the command

> [COLOR="#FF0000"]cngpij -P [/COLOR]<[PRINTER NAME> will open a dialogue box and you can then create a launcher

so for my MG3100USB the command is cngpij -P MG3100USB

---

### Post by Gleen on 2013-05-23
Got that
:D

But I didn't use the scan gear.

---

