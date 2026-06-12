---
title: "Guys, tulong! Karmic Koala on Acer  Aspire 4736"
date: 2010-03-10
forum: Philippine Team
---

### Post by jtweaker on 2010-03-10
hello, newb here. last few days lang ako ngtry mglinux and ang ginamit ko ay yung latest ng Ubuntu which is 9.10 karmic Koala. Ininstall ko sya gamit WUBI para madual boot ko with windows 7. Ok ang Ubuntu, maganda mga features iniisip ko pa nga na tanggalin na lang windows 7 and just stay with linux. Pero eto ang problem. 

1.   Hindi ko maadjust ung screen brightness ko. Kpg ginagamit ko ung hot keys sa keyboard may lumalabas nmn sa screen na ngaadjust ng brightness pero wlang nagbabago sa actual brightness. Ang lakas kasi sa battery kpg hindi nakadim.

2.   Yung system time ko laging mali kahit after ng restart. Kapag binabago ko pati yung time sa Windows 7 nababago. Nagbasa na ako ng ibang mga thread pero wala pa dn akong makitang solution para dito. 

help nmn guys...

---

### Post by badrra on 2010-03-10
hmmm, sa windows ba gumagana yung hotkeys? also ??? bakit nag babago yung time kahit sa windows. I doubt kung dahil sa ubuntu install yun.

---

### Post by wersdaluv on 2010-03-10
Try mo Right click panel > double click Brightness Applet. Subukan mo i-adjust yung brightness gamit yung applet na nasa panel. 

Yung system time naman, di yon Ubuntu issue. Kung i-uninstall mo rin naman ang windows, hindi na rin problema yon. Tama ba ang timezone na naka-set sa dalawang OS? Hindi ako nagkakaproblema sa system time pag magdual-boot.

---

### Post by Ravskie on 2010-03-11
> **wersdaluv said:**
> Try mo Right click panel > double click Brightness Applet. Subukan mo i-adjust yung brightness gamit yung applet na nasa panel. 

Yung system time naman, di yon Ubuntu issue. Kung i-uninstall mo rin naman ang windows, hindi na rin problema yon. Tama ba ang timezone na naka-set sa dalawang OS? Hindi ako nagkakaproblema sa system time pag magdual-boot.

Tama po si Sir Wers me wala din problem sa dual boot ( Win / KARMIC ). try to check the timezone of each OS....

---

### Post by jtweaker on 2010-03-11
Mga sir, thank you sa pgreply. Chneck ko po ung time zone ko then sinet ko sa Manila aun ayos na! Kaya pala ayaw maset dati kasi ndi ko nacli2ck ung "set" button sa tabi nung clock sa drop down menu ng locations. Hindi kc sya visible nung una. Nung tinapat ko lang ung mouse pointer dun sa area na un saka sya lumabas. Ok na po sya. Hindi na dn nababago time ko sa windows. Ung brightness na lang po tlga problem ko.

@badrra
Sir opo gumagana hotkeys sa windows.

@wersdaluv
Sir, thank you sa suggestion kaso ndi dn po gumana. Natry ko na dn iadjust sa power management ung brightness wala pa dn. Gumagana nmn po ung hot keys ko (Fn+right/left). May lumalabas na brightness adjustment sa screen kaso sa actual brightness ng monitor walang nagbabago.

---

### Post by jtweaker on 2010-03-11
Update po mga sir. I did some test kc may nabasa ako na kpg inadjust mo ung brightness sa Windows macarry over sya sa Ubuntu. Seems to work for me. Tried it on battery power. Booted sa Windows first then adjusted the brightness to the lowest value, restart, booted to Ubuntu then aun, nabawasan na dn screen brighness ko sa Ubuntu. Tumagal dn ung battery hours nya kc nga nabawasan na ang brightness. Pero sana may way para maadjust ung brightness sa Ubuntu mismo.

---

### Post by itagomo on 2010-03-25
Patulong din ako,
un ubuntu 9.10 ko pagshinutdown naghahang,
pahelp pls!

---

### Post by karekanu on 2010-03-30
Ma iiconfig ka sa grub para ma control yung brightness,
 
edit the file /etc/default/grub and change the following line from 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"
 
Pareha tayo ng laptop, problema ko lang yung internal Mic, parang di daw supported
ng kernel yung mic as of now.
 
Problema din if wala ng battery yung laptop, ng shutshutdown agad, ayaw mag auto hibernate.

---

### Post by jepong on 2010-03-30
same problem as my eMachines D725... wala pa out-of-the-box na solution as of now...

---

### Post by ptosiani on 2010-10-24
Hey! I don't understand everything you guys are saying, but configurations files are universal, I tried this on my Acer Aspire 4736 and worked:

 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

---

### Post by JCyberinux on 2010-10-26
> **ptosiani said:**
> Hey! I don't understand everything you guys are saying, but configurations files are universal, I tried this on my Acer Aspire 4736 and worked:

 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

sorry sir our bad, this is a filipino thread discussions, so they preferred to speak/discuss in filipino language. but anyways, the problem is the settings on brightness of the laptop. Cheers!

---

