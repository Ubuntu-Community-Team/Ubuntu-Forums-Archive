---
title: "HP Deskjet 930c prints purple instead of blue"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by Peter71 on 2012-02-17
Hello,
After testing Ubuntu 11.10 via the Live CD (_didn't install it_) on Windows XP laptop and printer, my HP 930c printer now (back in XP) prints odd colours as if its in CMYK - blues are purple etc. Strange thing is it only does this when printing from programs, eg Microsoft Word, GIMP, PDF viewer, Firefox etc. It doesn't do it when printing a cartridge alignment page or doing a Windows test page - blue prints fine in these cases. The printer has never had this problem before, only started after the Ubuntu CD.

I've tried reinstalling the printer drivers (latest ones from HP), software and cartridges.

Thanks for any help you can give, regards

Peter.

---

### Post by pqwoerituytrueiwoq on 2012-02-17
clean printer heads (unless it works on windows)
bet way to install the drivers for HP is like this

[FONT=Courier New]sudo add-apt-repository ppa:hplip-isv/ppa;sudo apt-get update;sudo apt-get intall hplip;[/FONT]

if there are any updates they will be installed automatically

make sure you selected the right printer when settings up sometimes the recommend one is not the best option (learned that one from experience)

---

### Post by Peter71 on 2012-02-17
Thanks [pqwoerituytrueiwoq]("http://ubuntuforums.org/member.php?u=865458"),

The problem has been occuring while in Windows environment. I don't use the live CD anymore. It seems the CD has caused some kind of permanent change in XP. 

RE:
[FONT=Courier New][COLOR=Blue]sudo add-apt-repository ppa:hplip-isv/ppa;sudo apt-get update;sudo apt-get intall hplip;[/COLOR][/FONT]

Not sure how this helps if I'm back in XP, I'm guessing these are instructions for installing printer while in Ubuntu. 

Peter.

---

### Post by pqwoerituytrueiwoq on 2012-02-18
try using the clean printer heads feature

---

### Post by Peter71 on 2012-02-18
The print heads are very clean, as is the rest of the printer, cleaned it all out not long ago. As mentioned: "when printing a cartridge alignment page or doing a Windows test page - blue prints fine"

The color management settings in the printer properties are all okay too.

---

