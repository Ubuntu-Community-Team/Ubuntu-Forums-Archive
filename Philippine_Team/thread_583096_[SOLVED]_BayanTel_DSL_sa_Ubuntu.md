---
title: "[SOLVED] BayanTel DSL sa Ubuntu"
date: 2007-10-20
forum: Philippine Team
---

### Post by eilu on 2007-10-20
Nasisiraan na ako...

Currently online via Windows 98; may "EnterNet 300" na ininstall yung Bayantel technician since Win98 doesn't support PPPoE. Modem is Huawei SmartAX MT880. Bumili ako ng router kanina; D-Link DI-604 (ethernet broadband router; 4 ports)

Anyway, na-configure ko naman ng maayos yung router via Dapper laptop (hindi makita ng Win98 yung router): select PPPoE in the wizard, input user name, pword, etc. Naka-connect naman ako, I recall logging into iGoogle. Bumagal yung page at ~90% load; may images na hindi nag-load.

Inayos ko yung mga cables; hinila ng pusa yung naka-connect sa laptop from router. Re-connect. Wla na, hindi na ako maka-connect. Kahit 'ping' wala.

Anyone using BayanTel DSL on an Ubuntu machine? Can you give a quick walkthrough? Plano ko na alisin ang Win98 pag ok na ang internet; papalitan ko ng Puppy Linux, since medyo matanda na yung box na to (PIII)

Additional info: yes, kaya nung laptop mag-connect sa DSL. Nagagawa ko yun sa bahay ng pinsan ko (PLDTmyDSL, wired modem/router) at sa trabaho (PLDTmyDSL, wireless router)

Update: naka-connect ako ulit kanina, mga 5 minutes or less. Tapos nawala ulit, same problem. Sa win98 box tuloy-tuloy ang connection.

---

### Post by perbiu on 2007-10-21
Baka sira na yang kable mo? ano yan gamit mo RJ45? Sa pagkakaalam ko kasi pag naka Ubuntu ka, plug n play nalang yan wala na ako kinalikot lalo na pag naka Router ka. Luma na yang Win98 mo, nabubuhay nalang yan sa Driver kaya pag nawala pa yon alang kwenta na. Maganda din yung Xubuntu at Puppy.

---

### Post by eilu on 2007-10-21
weirdly enough, ayos na siya nung sinubukan ko kanina. I'm now on my ubuntu box; online din yung puppy. hmmm... baka sa end ng bayantel nagkaproblema pero resolved na. oh well. babay na sa win98 for good!

---

### Post by carlexpc on 2007-10-23
this may not be related to your problem eilu, but i would like to comment on bayantel's service - super poor. sobrang tagal nila mag-troubleshoot ng problem ng client. ganun din ba experience mo?

---

### Post by jsgotangco on 2007-10-27
I have Bayantel DSL for 2 years already and its pretty good on my side. The modem is a ZTE then connected with a Linksys WRT configured with WPA2. Ubuntu, CentOS, Mac OS X, Nokia E61 and iPhone all connect flawlessly.

---

### Post by eilu on 2007-10-28
no idea. I don't ever use customer service if I can help it. In my experence, sasagot lang sayo e call center agent na bangag. :lol:

---

### Post by dimsum_linux on 2007-10-28
i'm using ubuntu gutsy,
pppoeconf in terminal, this is how i connect my bayandsl.
internet sharing na lang di ko maconfigured. mahirap pag noob sa linux.

---

### Post by kopinux on 2007-10-28
ang experience ko kasi sa mga isp na yan ay depende sa area, may mga area na hindi maganda meron maganda.

> i'm using ubuntu gutsy,
pppoeconf in terminal, this is how i connect my bayandsl.
internet sharing na lang di ko maconfigured. mahirap pag noob sa linux.

noong windows din ang gamit ko nahihirapan din ako mag setup ng network at internet sharing, kaya bumili nalang kami ng router, 1,500 lang naman.

---

### Post by GutsyNoypi on 2007-11-02
My Bayantel pppoe connection drops when I'm using Ubuntu. I tried calling customer service but they just gave me pppoeconf instructions and it doesn't fix the problem. Does anyone know how to work this out? My connection works fine when I'm using Windows. I have the same ZTE dsl modem.

---

### Post by eilu on 2007-11-03
I haven't had a problem since I got online. It used to drop in windows, now I'm online 24/7 no interrutions.

I found this via google, if you have the ZTE (Bayantel gave me a Huawei,plus  I am using a dlink router) it maqy be of help: [http://www.pinoydsl.net/viewtopic.php?t=4754](http://www.pinoydsl.net/viewtopic.php?t=4754)

---

### Post by ederic on 2007-11-10
Kaka-install ko lang ng Ubuntu kanina. Madali lang pala ang paglipat. Pati pag-configure ng Internet connection, okay lang. 

Noong una, okay naman ang connection, pero sandali lang yun kasi kumain muna ako. Pero pagbalik ko, nagkaroon ako ng paputol-putol na connection. Ang error message ay may sinasabing "PADS: System-Error: Duplicate Session Request."  Di ko pa nadidiskubre kung ano ang ibig sabihin niyan, pero ang ginawa ko ay ni-reconfig ko ang PPPOE at nag-restart ng dalawang ulit.

Okay na ulit ang connection ngayon.

Abangan ang susunod na mga kabanata sa blog o Twitter ko. Hehe. :p

---

### Post by md5hash on 2007-11-11
may problem din ako regarding sa internet connection.. using PLDT DSL okay namn yung network pero problem yung internet sharing

---

### Post by ayanph on 2008-01-08
I'm connected using Bayan DSL sa house. Ok naman sila. :) used pppoeconf to configure the connection. actually yung technician na nagsetup hindi alam pano gawin sa ubuntu...

buti na lang may forum ang ubuntu same lang naman with mint. :)

---

### Post by daxumaming on 2008-01-09
> **md5hash said:**
> may problem din ako regarding sa internet connection.. using PLDT DSL okay namn yung network pero problem yung internet sharing

If you have two NICs, then use either Guidedog or Firestarter to start Masquerading. Your PC would become a DHCP server and you can share your connection to another PC using either a direct connection or via Switch.

But as always, mura lang naman router. I got my TP-Link for 1,400 and i've been using it for almost a year now without problems... I'm not even powercycling it.

---

### Post by spike_naples on 2009-03-12
I use UbUntu 8.10 Interpid Ibex. A few days ago I totally erased my Windows and installed Ubuntu together with full versions of Crossover Linux and Crossover Games.

For my BayanTel, all i did was just enter my username and password when I set up my DSL connection. So far so good and so far I have not had any problems whatosever.

I'm no expert in theis new OS but everything is just so easy!

No need for good luck to those who plan to transfer... It's just that easy.

---

### Post by spike_naples on 2009-03-23
I never had any problems getting online with Bayantel and Ubuntu. All I did was enter my username and password.

I don't have a home network though...Just a direct connection.

---

