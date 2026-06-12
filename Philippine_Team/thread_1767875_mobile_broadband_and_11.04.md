---
title: "mobile broadband and 11.04"
date: 2011-05-26
forum: Philippine Team
---

### Post by kstella on 2011-05-26
Hi, guys.

Di na ako masaya sa Smart Bro. Paputol-putol ang connection. :( For some reason, I can't just reconnect; I have to remove the modem, then put it back, wait for the computer to recognize it, then wait for it to connect. Sayang ang minutes.

Is there a solution? Or, which other modems (telecom and model number) work well w/ 11.04?

---

### Post by jepong on 2011-05-26
get the "pocket wifi" instead

---

### Post by tech-hero on 2011-05-26
> **kstella said:**
> Hi, guys.

Di na ako masaya sa Smart Bro. Paputol-putol ang connection. :( For some reason, I can't just reconnect; I have to remove the modem, then put it back, wait for the computer to recognize it, then wait for it to connect. Sayang ang minutes.

Is there a solution? Or, which other modems (telecom and model number) work well w/ 11.04?
What particular modem are you using? I have experienced this before using SUN. I think those issues are also related to modems/drivers.

---

### Post by jepong on 2011-05-26
hindi kaya based din sa location yun?

---

### Post by antoniomiguel on 2011-05-27
> **jepong said:**
> hindi kaya based din sa location yun?

On most cases depende talaga sa location ang 3G dongle, though dito sa metro halos seamless na ang 3G coverage.

Mas mataas ang chance na sa provider ang problema.  Take for example my case (Sun Cell), pag peak hour ako nagconnect talagang gapang sya pero pag off-peak naman (about midnight to 7am) pumapalo sya ng 1+ Mbps.  Although gapang sya pag peak hour, di naman sya nagdidisconnect so maaring may prob ka ring iba (perhaps loose na usb mating).

---

### Post by tech-hero on 2011-05-27
At some point location problem nga. pero Naexperience ko kasi. Especially yung after mawala ng connection hindi na magcoconnect not until you unplug and plug the modem again. Yung pag disconnect may kinalaman sa Location at sa network, pero yung yung after disconnection ay hindi na maka connect kahit may signal na, i think sa driver or sa modem yun. Before i've been using a ZTE modem for sun. madalas ang disconnection nya dahil mahina medyo signal sa amin, kahit ma regain na yung signal, nagloloko din sya at disconnect agad status nya kahit sa query ko ay may signal. I've tried using  a different modem, Huawei. same network pero no problems even encountered even mahina ang signal...

---

### Post by antoniomiguel on 2011-05-27
True, some products are inferior from others :)

---

### Post by jao_madn on 2011-05-27
When disconnect and need restart para makaconnect cya..try nyo install usb-modeswitch  thru apt-get..yah dati ko probs peru nung install kona cya..seamless na hindi na kailangan reboot para makaconnect ulit.

---

### Post by kstella on 2011-05-27
Feeling ko, nasa signal nga ang problema. ZTE MF627 yata ang gamit ko.

---

### Post by janno92 on 2011-05-29
i use huawei E1552 on 11.04 and everything is fine..
 reconnecting is no hassle.

---

### Post by tech-hero on 2011-05-30
> **kstella said:**
> Feeling ko, nasa signal nga ang problema. ZTE MF627 yata ang gamit ko.
 
 
Sakit sa ulo yan. Though maganda ang design nya at mas mahal, pero mahina sya sumagap ng signal. Yung configuration nya na set to 3G only, hindi pa nassave sa device mismo. so kailangan mo lagi sya i set to 3G only which i think is hassle sa Ubuntu. The script i made doesn't always work due to the connect and disconnect issue. Buti nalang nawala sya, at bumili ako ng bago, Huawei. Now satisfied ako so far.

---

