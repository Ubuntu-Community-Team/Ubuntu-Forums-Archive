---
title: "Epson printers don't suppost ubuntu"
date: 2012-09-14
forum: New to Ubuntu
---

### Post by malcolmminasian on 2012-09-14
Epson says they don't support their printers for ubuntu.  Can't help me with attaching my  Epson stylus NX110 printer.

Is there a way to make the connection?

I.D. malcolmminasian

---

### Post by Cheesemill on 2012-09-14
According to the Linux printer compatibility database it works perfectly, just install the correct (32-bit or 64-bit) .deb file from this page and you're good to go.

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=16842&DSCCHK=f70a63f4f57d1d651f05d8f32c7be16ff5999393](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=16842&DSCCHK=f70a63f4f57d1d651f05d8f32c7be16ff5999393)

I don't know who you spoke to at Epson but the Linux drivers are from their website.

---

### Post by Mark Phelps on 2012-09-14
I have an Epson R220 and I was able to attach it using CUPS -- and there was a driver available there which I selected and it works fine.

However, to monitor the Ink levels, you can search for and install mtink.

The CUPS driver does not monitor the ink levels.

---

### Post by QIII on 2012-09-14
My NX400 works fine.  Driver was listed for me to select.

---

### Post by itolf on 2012-09-14
I plugged my Epsom DX8400 in via a USB hub, Ubuntu recognized it and installed the drivers without me doing anything more than that, true "Plug 'N Play" style. Maybe that model that has an issue. Sorry I can't be of any more help.

---

### Post by pdc on 2012-09-19
for anyone wanting printer drivers for Epson printers, 

Epson publish them under the Avasys corporation banner

[http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/)

so .........for example ......if one wants the NX...........one then selects multifunctional for the NX110

....and gets this page

[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/)

*there are many drivers for differing clusters of printers*..

.........so for each printer, one uses the **control-f** (FIND) function of the browser.......so for nx110 one enters that in the control-f window of the browser; and clicks **_NEXT_**......ie *you need to click nx110 twice to get to the right bit of page*...........

.......and comes to this section of the page

> Models	

    Epson Stylus NX110
    Epson Stylus NX115
    Epson Stylus SX110
    Epson Stylus SX115
    Epson Stylus TX110
    Epson Stylus TX111
    Epson Stylus TX112
    Epson Stylus TX113
    Epson Stylus TX115
    Epson Stylus TX117
    Epson Stylus TX119

Packages 	Size 	Manual	

    epson-inkjet-printer-stylus-nx110-series-1.0.0-1lsb3.2.i486.rpm
    epson-inkjet-printer-stylus-nx110-series_1.0.0-1lsb3.2_i386.deb
    epson-inkjet-printer-stylus-nx110-series-1.0.0-1lsb3.2.x86_64.rpm
    epson-inkjet-printer-stylus-nx110-series_1.0.0-1lsb3.2_amd64.deb
    epson-inkjet-printer-stylus-nx110-series-1.0.0-1lsb3.2.src.rpm


so for a 32bit ubuntu, that uses .deb packages ........

......one would download.......

> epson-inkjet-printer-stylus-nx110-series_1.0.0-1lsb3.2_i386.deb

and for 64bit ubuntu, one would download

> epson-inkjet-printer-stylus-nx110-series_1.0.0-1lsb3.2_amd64.deb

.........there you are now......................

.......perhaps you change the title of your thread !!!!!

If you subscribe to a thread, you can follow it; top-right; thread tools

---

