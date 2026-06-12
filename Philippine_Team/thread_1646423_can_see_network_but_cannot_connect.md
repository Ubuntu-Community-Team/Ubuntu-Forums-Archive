---
title: "can see network but cannot connect"
date: 2010-12-15
forum: Philippine Team
---

### Post by Noob-buntu on 2010-12-15
mga sir patulong naman po dito sa bagong problem ko.
last time i used ubuntu with internet connection, i had it wired directly on my router. now i am having difficulties trying to connect it on my wireless router.
please help mga sir.. thanks

---

### Post by pinoyskull on 2010-12-15
paano ka namin matutulongan kung wala ka namang binigay na detalye ng iyong problema :) (logs, error messages, etc)

---

### Post by Noob-buntu on 2010-12-15
oo nga naman.. hehe.. sorry sir pinoyskull. hmm, pano ba to? actually sir, 
walang error message e. pag pinindot ko yung network manager icon, nakikita ko yung network na gusto ko kumonek. Pero pag pinindot ko na yung network para i-connect yung pc ko, makikita ko yung icon na gumagalaw, nag-aattempt kumonek. ganun lang sir yung nangyayari for 1minute tapos may lalabas na notification, wireless network disconnected. ano pa po bang info kelangan mo sir? para maibigay ko sayo.

---

### Post by pinoyskull on 2010-12-16
subukan mo i tail ang messages log habang nag coconnect ka sa wireless network mo, dun mo makikita kung merong kakaibang nangyayari

> sudo tailf /var/log/messagesat i post mo dito ang nakita mo, yung relevant lang sa wireless network mo ah :)

at tsaka, ano pala ang wireless network mo?

> lspci |grep Network

paste mo rin dito

---

### Post by kraddark on 2010-12-29
Sakin ang ginawa ko lang is i-click ung wifi icon tapos >edit to connections>click wireless>add>lagay mo name ng connection mo (ito ung SSID)
tapos ung password.. kusa n cyang kokonek.. in short, configure mo manually.. not sure pero yan gnawa ko para gumana ung sakin..:)

---

### Post by tech-hero on 2010-12-29
> **Noob-buntu said:**
> oo nga naman.. hehe.. sorry sir pinoyskull. hmm, pano ba to? actually sir, 
walang error message e. pag pinindot ko yung network manager icon, nakikita ko yung network na gusto ko kumonek. Pero pag pinindot ko na yung network para i-connect yung pc ko, makikita ko yung icon na gumagalaw, nag-aattempt kumonek. ganun lang sir yung nangyayari for 1minute tapos may lalabas na notification, wireless network disconnected. ano pa po bang info kelangan mo sir? para maibigay ko sayo.
 
hmmm... siguro dahil mahina ung signal? may ganyan din ako naexperience dati... im not so sure. pero kung mahina ang signal at hindi masyado maganda, although nadedetect nya, pero nahihirapan sya mag establish ng connection.

---

### Post by wazorie on 2011-01-09
may ganito plang problema.. manual config lang 'to

---

### Post by lianne_john07 on 2011-01-12
Double-check lang po, baka po naka static naman si router.
Double check din yung WEP/WPA key.
Ano po Chipset ni Hardware? At kung ano pong Brand?

---

