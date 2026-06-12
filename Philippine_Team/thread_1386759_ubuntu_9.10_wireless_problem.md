---
title: "ubuntu 9.10 wireless problem"
date: 2010-01-21
forum: Philippine Team
---

### Post by petmalu on 2010-01-21
hi there. im a newbie in ubuntu. i have just installed ubuntu 9.10 in my laptop. it works fine except for the internet. it can detect wireless networks and connect to it. the problem is, when i start using firefox, it cant load any site. i cant browse or surf. i am using a sony vaio laptop. vgn-cr305e. [SIZE="5"]i really need help here[/SIZE] :(

---

### Post by loell on 2010-01-21
can you ping any site? 

example,

**ping -c 4 [www.google.com](www.google.com)**

---

### Post by petmalu on 2010-01-21
hindi po. destination not reached.. parang ganun po yung message kanina. ol po ako sir. nag aabang ng tulong. maraming salamat po.

---

### Post by petmalu on 2010-01-21
> **loell said:**
> can you ping any site? 

example,

**ping -c 4 [www.google.com](www.google.com)**

sir tinry ko i-enter yung command nyo pero ang lumabas ay:
unknown host [www.google.com](www.google.com)

---

### Post by loell on 2010-01-21
can you post your wireless info?

**iwconfig**

---

### Post by petmalu on 2010-01-21
eto po sir::

eth0      no wireless extensions. 
 
wmaster0  no wireless extensions. 
 
wlan0     IEEE 802.11abgn  ESSID:"Payatas Wireless"   
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:58:85:FA:C7    
          Bit Rate=54 Mb/s   Tx-Power=14 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=70/70  Signal level=-33 dBm  Noise level=-93 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Ravskie on 2010-01-21
Sir ask ko lang pretend that you are using wireless ............  meron ka po bang nakikita na icon ng antenna na may signal sa panel mo sa may taas right side if wala maaring hindi makakuha ng signal or connection try to click it check if meron available na AP connection

---

### Post by petmalu on 2010-01-21
meron po sir Ravskie, 4 bars po ako dito sa bahay.

---

### Post by loell on 2010-01-21
baka di lang maka reverse-dns,

paki edit ang resolve.conf

```
sudo gedit /etc/resolv.conf 
```

paste mo ang dalawang dns server,

> 
nameserver 208.67.222.222
nameserver 208.67.220.220


at malamang restart ka lang, check mo kung makaka browse ka.

---

### Post by petmalu on 2010-01-21
sir loell ginawa ko na po yung sinabi mo. ayaw pa rin mag browse. bale pinaste ko yung 2 na nameserver doon sa resolv na may laman na ip rin.

---

### Post by Ravskie on 2010-01-21
> **petmalu said:**
> eto po sir::

eth0      no wireless extensions. 
 
wmaster0  no wireless extensions. 
 
wlan0     IEEE 802.11abgn  ESSID:"Payatas Wireless"   
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:58:85:FA:C7    
          Bit Rate=54 Mb/s   Tx-Power=14 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=70/70  Signal level=-33 dBm  Noise level=-93 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


just wondering sa power management why it is off kasi sa akin it is on if i'm connected nasa AP 
sa aking palagay may connection na po kayo have you try to ping using IP address like 209.131.36.158 for yahoo.com might be DNS has problem or you can even restart the AP router try lang po....

---

### Post by petmalu on 2010-01-21
> **Ravskie said:**
> just wondering sa power management why it is off kasi sa akin it is on if i'm connected nasa AP 
sa aking palagay may connection na po kayo have you try to ping using IP address like 209.131.36.158 for yahoo.com might be DNS has problem or you can even restart the AP router try lang po....

sir tinry ko na rin po pero d pa rin ako mkabrowse. grrr...

---

### Post by petmalu on 2010-01-21
kapag nag ping po ako ang lumalabas ay "Destination net unreachable" po..

---

### Post by loell on 2010-01-21
kung pati External IP addresses ay unreachable,  malamang baka may problema sa config ng router.

---

### Post by petmalu on 2010-01-21
> **loell said:**
> kung pati External IP addresses ay unreachable,  malamang baka may problema sa config ng router.

ay ganun po ba sir? bale ang setting po kase ng pc ko ay::

bayantel modem connected to linksys voip router
linksys voip to dlink (dir-300)
dlink to cpu

may voip phone po kase kami.

ok naman po dito sa desktop ko ang connection pati sa winxp ko dati sa laptop (wireless connection)

sir sa tingin nyo ano po yung problem sa router?

---

### Post by loell on 2010-01-21
sa dir-300, try mong enable ang dns relay.

---

### Post by petmalu on 2010-01-21
> **loell said:**
> sa dir-300, try mong enable ang dns relay.

sir naka-enable po yung dns relay. =)

---

### Post by loell on 2010-01-21
i'm out of idea. :(

---

### Post by petmalu on 2010-01-21
> **loell said:**
> i'm out of idea. :(
yun na alng talaga yung hindi working e. sayang naman. nag pci=noacpi rin pala ako na command before pa ako nag seek ng help kanina.

---

### Post by kilosan on 2010-01-21
is your 9.10 updated?
pci=noacpi why? is it not booting?

---

### Post by loell on 2010-01-21
ah, kaya pala nag **Power Management off ** yung wireless info.

---

### Post by petmalu on 2010-01-21
> **kilosan said:**
> is your 9.10 updated?
pci=noacpi why? is it not booting?

actually wala akong idea kung para saan yun. nakita ko lang doon sa help kaya ko tinry yun. pero kahit d ko nilagay yung command na yun, still d pa rin ako maka browse eventhough connected ako eh. =(

---

### Post by petmalu on 2010-01-21
> **loell said:**
> ah, kaya pala nag **Power Management off ** yung wireless info.

kailangan ko po ba i-undo yun?

---

### Post by badrra on 2010-01-21
Ano po ba IP Address na nakukuha nyo?

---

### Post by petmalu on 2010-01-21
> **badrra said:**
> Ano po ba IP Address na nakukuha nyo?

192.168.0.101 po sir

---

### Post by badrra on 2010-01-21
> **petmalu said:**
> 192.168.0.101 po sir

Default Gateway mo 192.168.0.1 tama ba?

Kung tama paki ping mo nga yang Default gateway?

---

### Post by petmalu on 2010-01-21
mga sir, nag install ulit ako ng ubuntu. same os version p rin po. naka power management off pa rin.. nakalagay sa iwconfig. 
ano pong next move ko?

---

### Post by badrra on 2010-01-21
Kung na piping mo yan tignan mo kung ma pull up mo yung gui ng 192.168.0.1

---

### Post by petmalu on 2010-01-21
> **badrra said:**
> Default Gateway mo 192.168.0.1 tama ba?

Kung tama paki ping mo nga yang Default gateway?

ahm.. not sure. pano ko po ba malalaman yun?
tinry ko i ping ito po ang lumabas::

64 bytes from 192.168.0.1 : icmp_seq1 ttl=64 time=3.73ms

at continuous pa rin ang pag ping..d sya tumitigil. hehe

---

### Post by petmalu on 2010-01-21
> **badrra said:**
> Kung na piping mo yan tignan mo kung ma pull up mo yung gui ng 192.168.0.1

pano ko po ippullup yun? ano pong ibig sabihin nun?

---

### Post by petmalu on 2010-01-21
tinry ko puntahan sa browser yung 192.168.0.1
yun pala yung address ng dir-300 ko (dlink wireless router)

mga sir, paalala ko lang po na may linksys voip router din ako dito connected yung modem, linksys at dlink at the same time.

---

### Post by badrra on 2010-01-21
Yung Windows mo ba san naka connect? AT panong connection ng widos sa system mo? Wirless din ba? or Hardwired?

---

### Post by petmalu on 2010-01-21
> **badrra said:**
> Yung Windows mo ba san naka connect? AT panong connection ng widos sa system mo? Wirless din ba? or Hardwired?

sir hardwired po. from dlink may ethernet cable po to lan ng cpu.

---

### Post by badrra on 2010-01-21
> **petmalu said:**
> sir hardwired po. from dlink may ethernet cable po to lan ng cpu.

A so from Windows to Dlink to modem ganun po ba? at gumagana po ito? Kung ganun, pwede nyo po bang i plug yung wireless ninyo directly sa dlink tapos tignan nyo kung gumana ang internet.

---

### Post by petmalu on 2010-01-21
mga sir, napagana ko na po yung internet sa wireless. ginawa kong AP yung dlink ko. pero d ko na matandaan kung paano. ok lang kaya yun? pero gumagana na yung net. im typing here in my laptop right now. ndi n s desktop. astig. sarap gamitin!

kaso d naman po ako nakaka-play ng music files at video files ngayon.. =(

---

### Post by petmalu on 2010-01-21
mga sir. maraming salamat po sa tulong ninyo. lalo na kay sir loell, napakatiyaga mag reply. maraming salamat po!

---

### Post by loell on 2010-01-21
no problem petmalu,  we try to help whenever we can. :)

---

### Post by johnarcews on 2010-01-24
sir sakin din ayaw gumana wifi sa ubuntu 9.10 
incompatible sya sa cdrking wireless router kasi sa ibang router gumagana naman
ilang beses nadin ako na config ng mga settings pero wala parin eh.

---

### Post by badrra on 2010-01-26
> **johnarcews said:**
> sir sakin din ayaw gumana wifi sa ubuntu 9.10 
incompatible sya sa cdrking wireless router kasi sa ibang router gumagana naman
ilang beses nadin ako na config ng mga settings pero wala parin eh.

meron bang ibang PC naka connect wirelessly? Ano po klaseng security yan? WEP o WPA?

---

### Post by ragadanga63 on 2010-01-26
> **petmalu said:**
> mga sir, napagana ko na po yung internet sa wireless. ginawa kong AP yung dlink ko. pero d ko na matandaan kung paano. ok lang kaya yun? pero gumagana na yung net. im typing here in my laptop right now. ndi n s desktop. astig. sarap gamitin!

kaso d naman po ako nakaka-play ng music files at video files ngayon.. =(

Bro, baka di mo pa nainstall yong Ubuntu-restricted-extras ( sudo apt-get install ubuntu-restricted-extras)

---

