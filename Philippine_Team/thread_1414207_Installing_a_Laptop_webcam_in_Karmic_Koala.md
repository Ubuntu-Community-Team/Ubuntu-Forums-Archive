---
title: "Installing a Laptop webcam in Karmic Koala"
date: 2010-02-23
forum: Philippine Team
---

### Post by Dyimz on 2010-02-23
Hi guys...noob lang po ako sa ubuntu linux, kakainstall ko lang po siya within this month...

ask ko lang po kung pano mainstall yung webcam ng laptop ko sa karmic koala... yung laptop ko po is neo, na may built in/integrated webcam...

dati kasi vista gamit ko, nakainstall na kagad siya..ngaun natry ko na po gamitin yung aMSN tska skype, kaso wala pong naviview pag ino-on ko yung webcam...

ano po kaya pdeng gawin sa webcam na yun?

thanks in advance!

*PS - naginstall na din ako ng camorama webcam viewer, every time na inoopen ko siya, palageng sinasabe na unable to capture image...

ito po result ng lsusb baka sakaling makatulong po

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 003: ID 0402:5602 ALi Corp. Video Camera Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 1005:b113 Apacer Technology, Inc. Handy Steno 2.0/HT203


thanks po ulit in advance

---

### Post by Script Warlock on 2010-02-23
have you tried guvcview? works great for me sa neo elan ko......

[http://guvcview.berlios.de/downloads.html](http://guvcview.berlios.de/downloads.html)

---

### Post by Dyimz on 2010-02-24
hi bro, nainstall ko na yung guvcview pero black lang yung nakikita ko dun sa parang webcam window... :(

---

### Post by loell on 2010-02-24
can you

```
lsmod | grep video 
```

see if something comes up?

---

### Post by jepong on 2010-02-24
> **Dyimz said:**
> hi bro, nainstall ko na yung guvcview pero black lang yung nakikita ko dun sa parang webcam window... :(

try mo na install yung CHEESE?

---

### Post by Dyimz on 2010-02-25
videodev               36736  2 gspca_main
v4l1_compat            14496  1 videodev
video                  19380  0 
output                  2780  1 video

yan po yung lumalabas...try ko din po yung cheese..saka po pala..kumuha nako ng a4tech pk 7mar model kaso ayaw pa din gumana...triny ko install yung driver via wine, ayaw pa din po :(

---

### Post by zeroseven0183 on 2010-02-25
How's Cheese? Did it work?

---

### Post by Script Warlock on 2010-02-26
> **Dyimz said:**
> videodev               36736  2 gspca_main
v4l1_compat            14496  1 videodev
video                  19380  0 
output                  2780  1 video

yan po yung lumalabas...try ko din po yung cheese..saka po pala..kumuha nako ng a4tech pk 7mar model kaso ayaw pa din gumana...triny ko install yung driver via wine, ayaw pa din po :(

di pala uvc driver gamit.....

---

### Post by Dyimz on 2010-02-26
> **zeroseven0183 said:**
> How's Cheese? Did it work?
Black lang po yung lumalabas e...:(

---

### Post by Dyimz on 2010-02-26
> **Script Warlock said:**
> di pala uvc driver gamit.....
pano po ba install yung uvc driver?

---

### Post by Script Warlock on 2010-02-27
try xawtv.... nandyan lang sa ubuntu software center (applications)

tapos run the command sa terminal:

xawtv -c /dev/video0        <-------- parang may kulang? :( try lang.

lets ask sa mga guru kung tama ba to kasi tagal ko na rin di nagamit ang live webcam. some workround for bison(hope bison yan sayo): pls note eto ay isang guide lamang kung paano ko napagana ang webcam using uvc... no need to gaya if your not sure.... uvc: [http://linuxtv.org/hg/~pinchartl/uvcvideo/]("http://linuxtv.org/hg/%7Epinchartl/uvcvideo/")  download the bz2 put it inside the home. and launch the terminal then type:

tar xvjf uvcvideo-553dfd853cba.tar.bz2
cd uvcvideo-553dfd853cba
make
sudo make install
cd..

kung successful, install mo na lang guvcview [http://guvcview.berlios.de/downloads.html](http://guvcview.berlios.de/downloads.html)

---

### Post by Dyimz on 2010-03-02
Okay thanks po ng marami! Will try this po!

---

### Post by Dyimz on 2010-03-03
HI po..nung tinype ko na po yung cd.. command not found daw po...tapos triny ko run yung guvcview, black screen pa rin po :(

---

### Post by Script Warlock on 2010-03-04
:confused: after untar what is the output file usually uvcvideo-blahblah and thats what you cd:
$ cd uvcvideo-blahblah

ubos na options ko hintay lang magising mga guru dito at may paparating na tulong..

---

### Post by Tuna Caserole on 2010-07-20
Same problem on my end.  I'm using a NEO ELAN laptop.  [My thread on the topic.]("http://www.http://ubuntuforums.org/showthread.php?t=1528044")

Cheese and luvcview didn't work on it.

Will also be checking this thread for updates in case someone posts answers.  =]

---

### Post by Script Warlock on 2010-07-20
sir parehas lang tayo ng laptop neo elan wala naman pong problema sa akin lahat gumana 100% pero sa lucid to.. i use guvcview para sa webcam.

---

### Post by Samhain13 on 2010-07-20
Almost bought a NEO Elan last year too. Buti na lang lumakad pa ako ng konti... :D

---

### Post by Script Warlock on 2010-07-20
paalala ulit na before bumili ng laptop or netbook dapat may dala talaga kayong live usb kung ubuntu ang plano nyong gamitin. kung di lang to utang di ako kumuha ng neo eh walang choice payable when able at walang interest gusto ko nga sana yung dell studio.

---

### Post by Samhain13 on 2010-07-20
^ Oo naman! May bitbit talaga akong LiveCD nun para pangtest. :D

---

### Post by zeroseven0183 on 2010-07-21
> **Samhain13 said:**
> ^ Oo naman! May bitbit talaga akong LiveCD nun para pangtest. :D

Same here. Mabuti na ang sigurado. Laptop na lang ang dala paguwi, yung LiveCD iniwan ko na sa computer store para gamitin nila because you already had a short demo how Ubuntu/Linux works.

---

### Post by Tuna Caserole on 2010-08-16
> **Script Warlock said:**
> sir parehas lang tayo ng laptop neo elan wala naman pong problema sa akin lahat gumana 100% pero sa lucid to.. i use guvcview para sa webcam.

Tried installing guvcview, still doesn't work for me.  =[

---

### Post by Samhain13 on 2010-08-16
^ I just checked your other thread. Have you tried repeating the steps you took that got your webcam to work before the last Kernel update? I suspect the latest update just wrote over whatever you were able to change the last time.

---

