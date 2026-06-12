---
title: "MS Office 200X Installation Guide for Ubuntu Users!"
date: 2009-11-14
forum: Philippine Team
---

### Post by jaceleon on 2009-11-14
May nagtanong po kasi sa akin kung paano to gawin so I prepared a how-to for anyone to read and learn.

Okay, nasubukan ko na to sa ganitong computer environment
1. OS - Ubuntu series from 9.04- 9.10
2. WINE - wala pa
3. May internet connection

Before installation, make sure po na:
1. Uninstall your WINE, as PlayonLinux will download everything for you.
2. Make sure that you have a serial to your installer

Ang ingredients:
1. PlayonLinux.deb (download the latest .deb . Ask google where to download)
2. Knowledge ng konti sa terminal
3. Knowledge ng konti sa synaptics
4. Your CD, DVD or .iso of the Office installer
5. serial key ng Microsoft Office

Ang gagawin:
1. Download ka po ng package ng PlayonLinux (i-google niyo na lang), yung .deb package.
2. Install niyo po ang PlayonLinux package using terminal as well as any other dependencies(I assume ko po na marunong kayo gumamit ng terminal at mag-install using terminal, kung hindi po, then ask po kayo ulit sa akin)
3. Then after installation, click PlayonLinux in your main menu.
4. Click niyo po sa dialog box ng PlayonLinux yung install>office>Microsoft Office 2007 (pwede ding mag-install ng any other Microsoft Office, as long as you have a cd, or mounted iso ng installer at serial key)
5. Follow instructions there. Yun lang po!

Installing PlayonLinux.deb using terminal (step 2 po sa guide)
1. Ilagay niyo po yung downloaded package sa /home/(nameofuser)
2. Open po ninyo terminal.
3. Type and press enter to execute:
sudo dpkg -i *.deb (assuming na ito lang ang .deb na file sa buong /home/(nameofuser)
4. Input your password. If prompted po kayo magtype ng Y/N, type Y then enter.
5. If you're told na hindi siya mainstall ng maayos, kindly uninstall PlayonLinux by typing 
sudo apt-get remove PlayonLinux
sudo apt-get autoremove

look on the terminal kung mayroon siyang dependencies na wala daw. Install those using synaptic, then repeat installation of PlayonLinux (ako nga e, inulit ko to like 4 times dahil sa dependency missing daw, sabi ni terminal).


Note:

1. Make sure na may internet connection kayo, as PlayonLinux will download necessary winetricks required prior po sa installation niyo.
2. Make sure na kung i-mount niyo lang po ang .iso, use G-mount iso.
3. Don't hesitate to ask other forumers po regarding the use of the terminal.
4. It works from  Microsoft Office 2000 and above, although syempre may mga hindi pwede na i-open (Like Microsoft Office Access 2007) but no Microsoft Office '98, okay?

I hope po nakatulong po ako. Medyo newbie po ako at medyo kon ti lang ang alam, pero I'll try my best po para makatulong regarding installation of this Office suite.

Sa mga advance users, feel free to add more on this! Or correct me if something's wrong.
At sa mga hate na hate ang Macros**t at lahat ng products, preferences lang po yan. So no flaming po, please ? (pero ako, I'll flame Macros**t every second in my head! Hehehehe!)

Thanks for reading!:p

---

### Post by pinoyskull on 2009-11-16
Why would I use MS Office when I can use OpenOffice?

---

### Post by ligs on 2009-11-18
bakit kapamag iinstal ng MS office eh pangpabigat lng yan s HDD....sayang pa ung space my openoffice naman......?:D

---

### Post by dodimar on 2009-11-18
Dahil may gusto pa ding gumamit ng MS Office?

---

### Post by badrra on 2009-11-19
Pwede mo din naman install MS Office without PlayOnLinux. wine pa din naman ang ginagamit mo even if you use CrossOver. 

Just click on the installer and wait medyo matagal mag install. heheheh

But ofcourse I am using Openoffice 3 yan kasi naka install sa ubuntu 9.10. Maganda tignan MS Office 2007 sana lang yung OO gumawa naman ng mail client like MS Outlook.

MS Access? This is one of the worst database I have ever seen.

---

### Post by killer_d76 on 2009-11-19
there is another way of installing MS Office 2007 with all the features functional... use Virtualbox! (just installed Windows on Virtualbox for the sake of testing and installing MS Office 2007, after this Windows will be deleted on Virtualbox!)

---

### Post by jaceleon on 2009-11-19
ang habol lang nmn kc ng karamihan is the WYSIWYG na paraan ng MS Office. Not to mention na hindi masyado maitranslate ng maayos ng OO ang documents created on word (lalo na pag may image na nakalagay.)

At saka admit it po. sa bansang ito, mas marami ang user ng MS office, at mas marami ang may preference. Like my family, binigyan ko OpenOffice, tapos after two weeks pagbalik ko sa Tondo, naka MS Office na cla, d baleng navirusan PC nila.

It's just a matter of convenience na pinainstall ko ang PlayonLinux, since it automates the configurations required for installing MS Office in Linux. This is very good for newbies.

It's just a matter of preferences, ika nga. So kung san ka masaya e. Ganon po ang policies natin in choosing.

---

### Post by gtechmyk on 2011-02-21
pahelp nmn po. im using ubuntu 10.04 and i install ms office 2007 using wine 1.3.14. everything is working good except ms office powerpoint and also print preview of any ms office application. it says i need to add pinter on the start menu then printer faxes. i successfully added print epson tx110 on ubuntu 
system->admininistration->printing but still everytime i click print preview or print, the error still keeps on popping up.

---

