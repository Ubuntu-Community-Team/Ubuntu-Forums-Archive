---
title: "Supported Multi-Function Printer/Scanner/Fax?"
date: 2015-11-09
forum: New to Ubuntu
---

### Post by eddiefiggie on 2015-11-09
I've seen the list, but without knowing the functionality of each make/model it is difficult to decipher.

Can someone recommend a supported (official) device that does LASER printing/Faxing/Scanning?

Thanks!

---

### Post by SeijiSensei on 2015-11-09
Pretty much any Brother device will work with Linux.  Brother provides a "Driver Install Tool" on its web site that you can run, answer a few questions, and it will install whatever drivers are needed.

For specific models, you can see what's listed in [http://www.openprinting.org/printers](http://www.openprinting.org/printers).  Sometimes a specific model isn't listed, but an older or newer one in the same category is.  For instance, there's no entry for my Brother HL-3170CW, but the HL-3070CW is in the list.

---

### Post by DuckHook on 2015-11-10
Nothing wrong with SeijiSensei's advice. Treat the following as a companion piece:

I stick exclusively to HP. I found it a pain installing the scanner driver for an old Brother, but have never had issues with any HP machine. Moreover, HPLIP is now a standard part of an Ubuntu install, so almost all HP printers will work right out of the box with Ubuntu. HPLIP is actually a driver management/maintenance app. It will install the correct driver (or download it if necessary) and set your system up in a wizard-like fashion. Multifunction devices will also be automatically set up with fax and scanner support.

After years of struggling with all sorts of printers, from Canons to Lexmarks to Xeroxes to Samsungs, I've always found HP to be the most problem-free, installation-wise.

As for specific model recommendations, that gets asked often on these forums. And as usual, there is no answer because no one except you knows the specific uses you want. Do you need duplexing? Ledger-sized paper? Straight path? Multi-trays? Heavy duty cycles? Too many variables to juggle. You are approaching it backwards asking for specific models. Reverse the process. Shop for a model that suits your needs, then check it against the database. If it shows up, you're good to go. If it doesn't, then ask on this forum whether anyone has prior experience with that specific model and what to look out for.

Good luck!

---

### Post by mastablasta on 2015-11-10
HP first, then Samsung and Brother.

why do you need fax? you can set that up on computer. they tool al our faxes form the office and setup a virtual fax system. so if someone sends it (some still do) we get a PDF in email. and if we want to send it by fax we use the service. not that we want to ever....

---

### Post by eddiefiggie on 2015-11-10
> **DuckHook said:**
> 

As for specific model recommendations, that gets asked often on these  forums. And as usual, there is no answer because no one except you knows  the specific uses you want. Do you need duplexing? Ledger-sized paper?  Straight path? Multi-trays? Heavy duty cycles? Too many variables to  juggle. You are approaching it backwards asking for specific models.  Reverse the process. Shop for a model that suits your needs, then check  it against the database. If it shows up, you're good to go. If it  doesn't, then ask on this forum whether anyone has prior experience with  that specific model and what to look out for.

Good luck!

Thanks, yeah, just basic household printing.   Kids school papers, tax documents, etc...  Single tray, simplex... Lean  and mean letter size print jobs...but must be LASER!  :KS  But I also will need to scan content from time to time.  Simple stuff there as well.  For example, My kids play sports and I'll need to scan a birth certificate...  stuff along those lines.

> **mastablasta said:**
> HP first, then Samsung and Brother.

why do you need fax? you can set that up on computer. they tool al our faxes form the office and setup a virtual fax system. so if someone sends it (some still do) we get a PDF in email. and if we want to send it by fax we use the service. not that we want to ever....

Yep, agree on Fax...but scanning and printing are key.  Seems most printers that scan, can also fax....so I tossed that in there.

---

### Post by mastablasta on 2015-11-11
I took a Samsung with scanner and black&white laser printing only. wanted to get the HP at first but Samsung was smaller so I could fit it easily on the small cabinet. anyway it works quite well. also via network and from various systems. still I think HP has better support in general.

---

### Post by eddiefiggie on 2015-11-11
If you don't mind me asking.  Which Samsung model did you decide to use?

---

### Post by mastablasta on 2015-11-12
I believe it was SCX3200 or in that series. I am not sure if they make them anymore, but I am sure they make others that are similar.

you can read plenty news and information about their Linux drivers here: [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/)

at the time their linux drivers that came on CD had a small error, so this PPA fixed it as well as enabled some other features. However it seems Samsung now also fixed the issues.

---

