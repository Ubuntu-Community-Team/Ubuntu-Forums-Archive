---
title: "Help With First Install..."
date: 2008-09-21
forum: New to Ubuntu
---

### Post by mrstimpson on 2008-09-21
:confused:

Hey Everyone! Thanks in adavance for any-help. 

=My Problem=

*No Internet

I am very new to ubuntu and have just installed it using "Wubi - Ubuntu Installer for Windows".

The installation went great but I think no graphics card drivers nor wireless card drivers installed.

I just want some help locating the right drivers and a quick 101 on how to install them.

If anyone has the same setup as me, any information on "how to" set my laptop up properly would be appreciated. Thank you!

=System=

DELL Studio 1535

Wireless Dell 370 Bluetooth Card ROW
Wireless Dell1397 (802.11 b/g) mini card**
Graphics: 256MB ATI Mobility RADEON HD 3450**

---

### Post by mikewhatever on 2008-09-21
Can you post the output of the following command from Applications->Accessories->Terminal:

> sudo lshw -C network

Unfortunately, Dell often uses those horrible broadcom cards with crappy Linux drivers, which I suspect may be in your case.

Have you tried connecting the cable yet? If you have access to any kind of wired internet, get connected and check the Restricted Drivers under System ->Admin->Hardware Drivers.

---

### Post by Tatty on 2008-09-21
A quick howto for proprietry Graphics card driver install:

First go to "System->Administration->Hardware Drivers", see if it lists a driver for your card in there, if so then click to install.


If that does not work then try using envyng.  First install envyng-gtk from the repos:
```
sudo apt-get install envyng-gtk
```

then run envy (its in one of the applications menus), and install your driver that way.

If both of those fail then you will have to install the driver manually, which can be a little tricky with ATI, but definately do-able.

---

### Post by mrstimpson on 2008-09-21
Thank you for your replies, I am now rebooting in to ubuntu to try them out. be back in a bit to reply. Thanks

---

### Post by mrstimpson on 2008-09-21
mikewhatever: I tired this in the terminal "sudo -c network" and it listed "format as html, xml etc" that where I got stuck....

and

Tatty: after trying envyng it said that it could not find it!

this is not going well...its strange being completely in the dark in this OS after years of using windows and osx..

---

### Post by mikewhatever on 2008-09-21
> **mrstimpson said:**
> mikewhatever: I tired this in the terminal "sudo -c network" and it listed "format as html, xml etc" that where I got stuck....

The 'C' in the command I posted is capital, in other words, -C, not -c, also the lshw is missing in your quote. Can you simply paste it and post the output.

Tatty, the things you suggested are good, but require an internet connection. Actually reading the OP in not a capital offense.

---

### Post by mrstimpson on 2008-09-25
would it be much easier because i have the dreaded internal wireless card to buy one of the those cheap usb ones for internet in ubuntu, if so does anyone recommend one that's highly compatible?

[http://www.play.com/Search.aspx?searchtype=allproducts&searchstring=usb+wireless&page=search&pa=search&go.x=0&go.y=0](http://www.play.com/Search.aspx?searchtype=allproducts&searchstring=usb+wireless&page=search&pa=search&go.x=0&go.y=0)

this one maybe?

Edimax EW-7318USG WiFi USB Turbo Wireless Adaptor 4Dbi

---

### Post by pelle.k on 2008-09-28
It would seem this usb dongle is supported out of the box;
[http://www.pricerunner.co.uk/f/483/Office-supplies?search=bn-wd54g&other_hits=199%3Abn-wd54g%3B%3B%3B&q=bn-wd54g&ref=redirect](http://www.pricerunner.co.uk/f/483/Office-supplies?search=bn-wd54g&other_hits=199%3Abn-wd54g%3B%3B%3B&q=bn-wd54g&ref=redirect)

According this post;
[http://ubuntuforums.org/showthread.php?p=4837466&highlight=wireless+usb#post4837466](http://ubuntuforums.org/showthread.php?p=4837466&highlight=wireless+usb#post4837466)

---

