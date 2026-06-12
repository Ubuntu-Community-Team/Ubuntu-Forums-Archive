---
title: "Printer Canon MG2260 not printing"
date: 2014-06-29
forum: New to Ubuntu
---

### Post by Middo on 2014-06-29
Hi All,

I have installed Ubuntu 14.04 as a dual boot, and I can't print from Ubuntu.  The printer show up, and when I print from an email, it says it is printing, but it never gets beyond there.  The print queue shows the job as processing, for 5 days.  Any ideas?

---

### Post by pdc on 2014-06-29
Can I suggest you download the linux drivers that Canon makes available for your machine; and install those? They work well

if you go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100466201.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100466201.html) and click [COLOR="#FF0000"]DOWNLOAD[/COLOR] and select the **SAVE** option as download begins; the file will be [COLOR="#008000"]cnijfilter-mg2200series-3.80-1-deb.tar.gz[/COLOR] and will be saved to your Downloads folder

if you open a terminal; (please ask if you don't know how)... and **copy** and **paste** the commands below that are in red; *one line at a time*; and hit the **ENTER** key after each paste ...

[COLOR="#FF0000"]cd Downloads
tar -zxvf cnijfilter-mg2200series-3.80-1-deb.tar.gz
cd cnijfilter-mg2200series-3.80-1-deb
./install.sh[/COLOR]

you should follow the commands above exactly; (some folks instead like to add their own little flair.............)

(I assume the device is usb-connected)

---

