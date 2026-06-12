---
title: "Help getting started"
date: 2012-01-13
forum: New to Ubuntu
---

### Post by selbs on 2012-01-13
Hi guys,

I wonder if you can help. I've recently installed ubuntu 11.10 alongside Vista (which was all breaking and going too slow).

I really like Ubuntu's functionality and simplicity (So nice to work at my computer without it whirring away and me having no idea what it's doing!) But I'm having a bit of trouble getting things working as I want.

First of all, I've installed wine and managed just about to get word, powerpoint and excel 2007 installed. When I use them though, the installations don't seem to be that robust. - They'll often crash, or not show all the menus etc. Is there a better way/more stable way for me to install these and use them? Would crossover add any more advantages?

Also, Ubuntu has detected and installed my Canon printer (pixma ip4300), but there is no software associated with it. When I used it in windows I could set up the defaults for how I wanted it to print (draft quality, double sided etc). Is there any way to do this in Ubuntu? 

Also, the colours are too dark when anything prints. Is there a way to fix this just by changing settings, or do I have to pay out to get an ICC done?

I'm completely new to Linux, so don't really understand how to do things other than simple things through the GUI. I'm not familiar with how to use terminal or what the different commands are.

Any help very much appreciated!

Thanks.

---

### Post by kc1di on 2012-01-13
> **selbs said:**
> Hi guys,

First of all, I've installed wine and managed just about to get word, powerpoint and excel 2007 installed. When I use them though, the installations don't seem to be that robust. - They'll often crash, or not show all the menus etc. Is there a better way/more stable way for me to install these and use them? Would crossover add any more advantages?



I can't help with your printer need but may I suggest that you give Libre Office a try as a replacement for M.S. Office.  It has all the power of the other but is open source and works very well with Ubuntu.  Wine is good but it has real problems with Office. If that is not an option for you then I would suggest you must bite the bullet and pay for one of the commercial programs that allow you to run office in Linux.  Cross over Office come to mind. But please do give Libreoffice a chance first. 
Just MHO. 
good Luck ,
:)

---

### Post by selbs on 2012-01-13
Hi Dave,

Thanks for your reply. I really need to have office installed, as that's what I need for my work. Is "cross over office" different to the standard  "cross over"?

Thanks,

Mark.

---

### Post by Matt__ on 2012-01-13
+1 for Libre, it does all you need, though formatting may be off when openining docx/and likewise OO format in windows. The only version of MS office that works well in wine is Office XP(2002).([info from WineHQ](http://appdb.winehq.org/appview.php?appId=31))

As for your printer, there is a long winded and old [modding guide](http://www.canon.co.uk/Support/Consumer_Products/products/printers/InkJet/PIXMA_iP_series/iP4300.aspx?DLtcmuri=tcm:14-742611&page=1&type=download) here.

And some sort of linux driver on [canons own website](http://www.canon.co.uk/Support/Consumer_Products/products/printers/InkJet/PIXMA_iP_series/iP4300.aspx?DLtcmuri=tcm:14-742611&page=1&type=download) (print filter??)

you may also have success using the 4200 install shown on [help.ubuntu](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview) (again this is ancient)


//edit: RE. MS Office, an article on page 37 of [Full Circle Magazine](http://dl.fullcirclemagazine.org/issue52_en.pdf) seems to indicate office 07 works well on ubuntu 10.04 with play on linux and wintricks installed.

---

### Post by Ms. Daisy on 2012-01-13
> **selbs said:**
> I've installed wine and  managed just about to get word, powerpoint and excel 2007 installed. When I use them though, the installations don't seem to be that robust. - They'll often crash, or not show all the menus etc. Is there a better way/more stable way for me to install these and use them? Would crossover add any more advantages?

I have never used wine so I can't say how that would go. But according to the [wine website]("http://www.winehq.org/about/"), it's under active development which means you may encounter bugs.  If you're not happy with wine there are some alternatives.

Consider VirtualBox.  You could install windows inside of a virtual machine, which would run inside of Ubuntu.  It's easy to switch back and forth. [https://www.virtualbox.org/](https://www.virtualbox.org/) will tell you more about it.  

I use ubuntu at home but my work uses windows.  I work from home sometimes, so I have decided to dual boot.  It's really the simplest solution for my situation, don't know if that's an option for you.

---

### Post by grahammechanical on 2012-01-13
With Microsoft Windows it is the responsibility of the printer maker to supply software to adjust the settings of the printer. These manufacturers do not accept responsibility for giving Linux users configuration software. The Linux developers have to do all the work and often with little or no cooperation from the maker.

I do not have a printer installed so I can not speak from personal experience but have you looked at the Color utility in System Settings? 

The Wine application is distributed without charge. Crossover is the commercial (paid for) version of Wine. As such it may be more efficient or have different features than wine .

Check this out.

[http://www.codeweavers.com/products/differences/]("http://www.codeweavers.com/products/differences/")

I am not recommending anything. I use wine but then I do not use MS Office.

Regards.

---

### Post by Mark Phelps on 2012-01-13
> **selbs said:**
> I really need to have office installed, as that's what I need for my work.

Then, you need to either run Windows in a virtual environment, or have Windows installed on the PC in dual-boot mode.

Linux distros do NOT fully implement MS Office using Wine, or any of its add-ons.  You will always run into limitations, especially if you use the new "default" XML-formatted Office documents.

Additionally, Office 2010 has nearly NO support in Linux.  So, if you attempt to use that, you are out of luck.

---

