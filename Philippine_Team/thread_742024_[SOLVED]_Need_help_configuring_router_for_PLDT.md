---
title: "[SOLVED] Need help configuring router for PLDT"
date: 2008-04-01
forum: Philippine Team
---

### Post by yssida on 2008-04-01
Hi again po, si isda na naman po. Gusto ko po sana magamit ang router namin, kaso wala akong alam sa mga ganito. sabi nila madali lang daw sa cd based na pagconfigure, eh kaso sira ata cdrom drive namin. Na-temptasyon ako na magbayad ng propesyonal pero ang sinisingil ay tumataginting na P1500, masisiraan yata ako ng ulo noon. Wala ako income na ganoon eh, mag-aaral lang. 

How do I configure my linksys wireless router to share a pldt dsl connection with a laptop (wireless) and desktop (wired)? I tried the cd based thing in windows to configure stuff. I stopped in the middle so i tried the manual based configuring. So I went to a browser typed the default  192.168.1.1 (changed it to 192.168.1.2 which was mentioned as an  important step to make it different from the modem's ip) and did the manual config from there.

I followed the instructions but all it said when I tried connecting to the internet was that it couldn't find the ip address of the provider which left me confused. I tried to do that in Windows, but I suspect it would be the same in linux since it's web based. I don't know much about this stuff, sadly.

---

### Post by dodimar on 2008-04-01
Linksys din gamit ko.. pero smartbro kasi ISP ko kaya medyo magkaiba tayo ng setup... 

anong model ng linksys router gamit mo...?


I believe you have to set your PLDT modem to bridge and setup your linksys router to PPPoE and use your pldtdsl usename and password....

sorry not really sure...

pero for sure meron dyan na marunong...

---

### Post by yssida on 2008-04-01
Ang model? Yun ba yung WRT54G? Saan po ba may forum na nagspecialize ng ganito?

---

### Post by dodimar on 2008-04-01
Yung forums, ang hirap makakuha ng exact work around.. 

try this link...

[http://max.limpag.com/2007/11/23/wi-fi-linksys-wrt54g-pldt-mydsl/](http://max.limpag.com/2007/11/23/wi-fi-linksys-wrt54g-pldt-mydsl/)

pareho kayo ng router and ISP.

---

### Post by yssida on 2008-04-01
natry ko na po ang sa kanya, eh kaso hindi specific yung intructions sa ibang config.

---

### Post by xtrm_redbull on 2008-04-02
Hi yssida, naka pldt-dsl din ako, kaya lang ang modem/router ko ay PL-DSL1 (from PLDT), gumagana yung wireless ko using d-link wireless router connected to the PL-DSL1. Ang config ko is:
set mode to Routing
encapsulation is PPPoE
leave the rest of the settings LLC,VPI,VCI as is ( I think this is location specific.)
connection: select nailed-up connection


Primary DNS: 	58.69.254.3
Secondary DNS: 	58.69.254.4
DHCP:	Server

Sana gumana na :)

Try mo nalang dito sa forums na [PinoyDSL.net]("http://www.pinoydsl.net/viewforum.php?f=3")

---

### Post by yssida on 2008-04-02
Okay lang din naman po na sa Ubuntu ko isetup ang modem at router niya po diba? Hindi yata siya nakadepende sa plataporma ng ginagamit? kung ganoon po ay subukan ko ito sa Ubuntu laptop na meron dito.

---

### Post by yssida on 2008-04-02
di bale po, sa pagbubutingtingay nasolba na po ang problema. ngayon wala nang kable sa laptop dito (liban sa kuryente!) :)

---

### Post by c2hamm on 2008-04-06
> **dodimar said:**
> Linksys din gamit ko.. pero smartbro kasi ISP ko kaya medyo magkaiba tayo ng setup... 

anong model ng linksys router gamit mo...?


I believe you have to set your PLDT modem to bridge and setup your linksys router to PPPoE and use your pldtdsl usename and password....

sorry not really sure...

pero for sure meron dyan na marunong...

hi!  i was searching on the net for help to configure my wag54g linksys wireless router.  my ISP is smartbro as well.  i came across your post.  appreciate it if you can help me.  i called smartbro to ask for some information.  all they told me is they use dynamic ip.  so i set up the router with RFC 1483 Bridged as its encapsulation.  smartbro wouldn't tell me what the vpi and vci are.  so i haven't really gotten anywhere yet.  i tried using the default which is 8 and 35, respectively.  also tried 0 and 35, 0 and 100.  i even tried selecting to  detect them automatically.  please help.  i really don't know what to do :c

---

### Post by dodimar on 2008-04-07
[QUOTE=c2hamm]hi!  i was searching on the net for help to configure my wag54g linksys wireless router.  my ISP is smartbro as well.  i came across your post.  appreciate it if you can help me.  i called smartbro to ask for some information.  all they told me is they use dynamic ip.  so i set up the router with RFC 1483 Bridged as its encapsulation.  smartbro wouldn't tell me what the vpi and vci are.  so i haven't really gotten anywhere yet.  i tried using the default which is 8 and 35, respectively.  also tried 0 and 35, 0 and 100.  i even tried selecting to  detect them automatically.  please help.  i really don't know what to do :c[/QUOTE]

you don't need a modem if you are using smartbro for your isp. linksys wag54g is an ADSL (or simply DSL) Modem which is used for DSL connections. Smartbro is not ADSL. Smartbro is actually a wireless network, wherein you connect your pc into an existing network. better use a "ROUTER" for sharing Smartbro. Or you can use the "4 post switch" of your wag54g ADSL modem, but if you are going to share internet connection for multiple PC, you have to login to smartbro portal everytime you use a different computer. and you won't be able to use the internet at the same time with multiple pc.

get a router for smartbro. Smartbro is not DSL/ADSL.

I am using linksys wrt54gc wireless router to share internet for my desktop and wifi for a laptop.

all you have to do is set the router's internet connection type to DHCP, clone the MAC address of your PC (the one you used to activate Smartbro), and, alas, your internet is shared. (for wireless you have to secure it with WPA to be secured).

---

### Post by xxbabonxx on 2009-10-06
hi guys. pldt my dsl user ko. gamit kong router linksys din. dati ok ung internet connnection ko pero last week nasira na lng bigla nung nahugot ng frend ko ung power ng router ko sa outlet. triny ko gawin ung router. minsan naggawa ko xa pero pag pinatay mo na ung router, paginopen mo ayaw nanaman nia magconnect. ngayon di ko na magwa ule ung router. and another problem, sa tuwing kinakabit ko ung dsl cable sa acer laptop ko may nadedetect na virus ung anti virus ko. xp ung os nia. ung sa vista naman wla nadedetect. help naman guys.

---

