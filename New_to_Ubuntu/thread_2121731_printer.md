---
title: "printer"
date: 2013-03-02
forum: New to Ubuntu
---

### Post by lenypl on 2013-03-02
hi 
i buy a new canon MG3170 printer. i want to know how can i install it in my ubuntu 12.04. it is a wifi printer. i want to use it wirelessly

---

### Post by pdc on 2013-03-04
yes indeed you can: go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100393702.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100393702.html)

.....I suggest SAVE as the option when you click to download......it should be saved to your Downloads directory

*LEAVE the printer OFF at this stage*...

if I suggest some commands that you should copy and paste into a terminal....

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf cnijfilter-mg3100series-3.60-1-deb.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd cnijfilter-mg3100series-3.60-1-deb[/COLOR]

> [COLOR="#FF0000"]install.sh[/COLOR]

.......the install script will run; at some stage it will ask you to turn the printer on; it will ask you if you want USB or wifi.......hopefully following all the instructions will allow you to get going

Canon also supply a programme called ScanGearMP ..........to run the scanner ..........

to install, go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100394102.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100394102.html)

the commands are the same as above, substituting the new file name.....

to run type

> [COLOR="#FF0000"]scangearmp[/COLOR] in a terminal...hit enter........and you will need to create a launcher for greater ease of use........

---

