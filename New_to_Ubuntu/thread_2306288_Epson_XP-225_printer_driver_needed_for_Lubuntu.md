---
title: "Epson XP-225 printer driver needed for Lubuntu"
date: 2015-12-14
forum: New to Ubuntu
---

### Post by rollerworld on 2015-12-14
Hello, Had to buy a new printer, I bought an Epson XP-225 printer, I could not find this printer driver listed. Epson do a generic Linux driver for their range of printers that has to be installed from the terminal, I entered all the correct code in to the terminal, this did not install this generic driver.

The O/S is Lubuntu.

Any Help with this problem will be appreciated. Thanks

---

### Post by rdb3 on 2015-12-14
You may want to try the other one (printer utility).

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

---

### Post by Mike_Walsh on 2015-12-14
Hi, rollerworld.

Now then; here we go.....again! :lol: If you go to the Epson download page:-

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

....you are going to find precisely nothing, I'm afraid. Your printer is one of the more modern 'home' (as opposed to 'business') models which doesn't have a dedicated driver under Linux; it's only supported by the generic one. This gives basic functionality, but not much else. Depends what you want to do with it, really.

I did the following, purely out of curiosity; I had a feeling that it might give us a result of sorts. On the download page, I entered the details for my own Stylus SX218. The 'dedicated' driver doesn't cover it - didn't expect it to - but the generic driver, when you click on the 'Download' button, unfolds to an enormous list of Epson printers; pretty much everything they've issued in the last 6-7 years.

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=42302&DSCCHK=024d5066299b0207071538f4566df8962e62c88d](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=42302&DSCCHK=024d5066299b0207071538f4566df8962e62c88d)

If you scroll down near the bottom, you should find your XP-225 listed. Click the 'Accept' button at the very bottom of the page, and the page will unfold further, giving you a short list of drivers. You don't say if you're using 32-bit or 64-bit, but both are offered. If 32-bit, you want number 2 (the i386), if 64-bit, number 4 (the amd_64). These are the .deb packages, not the .rpm ones. AFAIK, there is no terminal work needed to install an Epson driver in the 'buntus; I'm not certain where you got that from! Mind you, you look to have been using it for a lot longer than I have; I'm one of the more modern users. It's just like Windows or Mac; download & install the driver, then install the printer with the printer utility. (I haven't run Lubuntu for over a year, so I forget exactly where to find the specific Menu entries...)

Locate the driver in your Downloads directory, then, if you don't already have it, I would advise installing **gDebi** from the Software Centre; it's way better than the standard setup for installing standalone .deb packages....seems much more efficient at pulling in the dependencies ( and there's a LOT with Epson drivers, trust me!) After installing it, right-click the item in your Downloads directory, and choose 'Install with gDebi'.....and let it do its thing.

When it's installed, I [COLOR=#ff0000]*think*[/COLOR] you want 'System' in the main Menu, to bring up the Printer install utility. (Remember, I'm rusty on this.) However you find it, once it's opened, click on the big 'plus' sign (!), and the rest of the procedure is pretty straight-forward; just follow the prompts. You should have less trouble than I did, since the generic drivers seem to be more easily accepted by the system than the dedicated ones, for some daft reason.

If, at a later date, you manage to locate a more full-featured driver for your machine, rather than uninstall and re-installing, you can go into your browser and enter 'localhost:631'. This will bring you to the CUPS web interface, where you can 'modify' the printer without **un**-installing.

(I've been fortunate with the SX218. Quite unwittingly, I've bought a printer which was an early 'relative' of the business-class 'WorkForce' series; and has full compatibility with the WorkForce full-function drivers... Better than I expected!)

-----------------------------------------------------------------------------------------------------

If you want to get the scanner up-and-running, we'll go through that separately; it's a second install, anyway. Linux tends to treat Epson printers & scanners as separate devices, anyway.....even if they're on the same machine!

BTW; you may have problems getting the wireless connection to work. You might need to use a traditional cable connection. Mine doesn't have wireless, anyroad, so I can't comment.

Let me know if any of that helps at all.


Regards,

Mike. ;)

---

