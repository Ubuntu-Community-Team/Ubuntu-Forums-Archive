---
title: "ubuntu 8.04 no internet connection"
date: 2008-08-28
forum: Philippine Team
---

### Post by nad4 on 2008-08-28
nag install ako ng ubuntu 8.04, nagamit ko nmn agad, may internet connection nmn, nung naka 1 day siya, nagrestart ako, ngyn dna mkabrowse sa firefox, nakakapag ping nmn ako sa yahoo. pero tagal magopen ng yahoo. sa mga updates dna rin makapag update.

---

### Post by king leoric on 2008-08-28
Pwedeng ang isang factor mo jan bro eh ang ISP provider mo. Or kung may server ka or router eh isang factor din yan.

Try mo check din ang speed ng internet connection mo [http://www.speedtest.net/](http://www.speedtest.net/) 

Kung nagamit mo naman yan yesterday at wala ka naman binago eh I'm sure mabagal lang ang server ng yahoo. Try mo surf sa ibang webpages. Kung mabagal pa rin eh pwedeng ISP provider mo na :)

---

### Post by rjmdomingo2003 on 2008-08-28
> **nad4 said:**
> ...ngyn dna mkabrowse sa firefox...
Baka naka-check lang yung Work Offline sa File drop-down menu ng Firefox.

---

### Post by nad4 on 2008-08-28
kahit ung site ayaw din eh,, wla nmn ako binabago sa connection nya.. ung error nlang sa ipdate ung check ko,

---

### Post by jepong on 2008-08-28
check mo rin yung network-manager infos mo kung may ip address ka from your ISP.

Ganyan din minsan problem ko ms PLDT MyDSL ko and laptop.

---

### Post by nad4 on 2008-08-28
boss jepong pano ginagawa mo pag gnun ung problem, naisip ko tuloy magreinstall kaso, dko masosolve ung problem pag plagi gnun. salamat sa mga nag suggest. :)

---

### Post by jepong on 2008-08-28
dati ginagawa ko eh restart ng laptop...

try to click or double click or right click your network-manager (sorry di rin ako sure and naka-windows me right now sa office)... makikita mo dun yung connection information mo. ccehck mo rin kung ano ip address mo.

---

### Post by wersdaluv on 2008-08-28
Di ako sigurado kung may effect to dyan pero gumagana to minsan. 

Use [OpenDNS]("https://www.opendns.com/start/ubuntu.php")

---

### Post by nad4 on 2008-08-31
maga boss. eto k na ulit wala pa naman ako binabago, nakakapag bwrowse na ulit sa internet. pero ung mga upadates hindi lahat nauupdate.

---

### Post by jemate18 on 2008-09-01
> **nad4 said:**
> maga boss. eto k na ulit wala pa naman ako binabago, nakakapag bwrowse na ulit sa internet. pero ung mga upadates hindi lahat nauupdate.

For the error in updates
Try to open a terminal

type 
> sudo apt-get update

If there are problems regarding the connections to the repository servers it should be displayed..


If you don't have internet connection,, may be try this

> sudo /etc/init.d/networking restart


To view your newly assigned IPAddress by the DHCP server
Open a terminal, type
> ifconfig eth0
assuming you have 1 LAN card

to view all, type
> ifconfig -a

Did you edit /etc/apt/sources.list ?

---

### Post by nad4 on 2008-09-02
boss wala pa po ako binabago dun sa
" /etc/apt/sources.list "
nagamit ko na rin to
" sudo apt-get update "
pero ung lumalabas sa terminal ung "Hit"
boss pag hit ba di nadownload ung upadates nun?
saka pala ung messenger di ako makaconnect..

---

### Post by jepong on 2008-09-04
di kaya may problem lan mo?

---

### Post by nad4 on 2008-09-04
ganito kasi setup ng pc ko
2 HDD
1 SATA HDD Windows(80G)
1 IDE HDD Ubuntu(40G)
pag ng boot up ako, plagi press 
ung F8 para masearch ko kung what 
HDD ung boot ko, pag sa windows 
ok nmn ung connection nya.
pag sa ubuntu, may time na mero may 
time na wala, gaya ngyon meron ulit 
ewan ko bukas kung meron pa ulit 
internet connection,,

---

### Post by loell on 2008-09-05
ca you try booting in the livecd (several times)? see if you can get persistent internet connections?

---

