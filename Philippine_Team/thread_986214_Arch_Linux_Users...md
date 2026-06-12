---
title: "Arch Linux Users.."
date: 2008-11-18
forum: Philippine Team
---

### Post by adredz on 2008-11-18
if you are an Arch linux user at the same time smartbro ang gamit nyo, pahelp namn ako configure sa system ko.:)

under DSL(PPPoE) ba ang SmartBro? if so, according sa arch wiki, i need to install my network card sa modprobe.conf, install rp-pppoe package, and run pppoe-setup... noss bled eh, help namn...

---

### Post by dodimar on 2008-11-18
smartbro is not PPoE. if your use Smartbro.. consider yourself on a wireless local area network.

so you should be setting it on DHCP (assuming you are directly connected to smartbro and not using a router).

---

### Post by adredz on 2008-11-18
> **dodimar said:**
> smartbro is not PPoE. if your use Smartbro.. consider yourself on a wireless local area network.

so you should be setting it on DHCP (assuming you are directly connected to smartbro and not using a router).


but ubuntu recognizes my connection as Wired?..

---

### Post by dodimar on 2008-11-19
Hehe.. medyo malabo pala yung explanation ko.. ngayon ko lang narealize..

Medyo mahirap kasi explain eh.. magulo kasi system nila.

Wired sya madetect.. tapos set mo lang sa DHCP... bahal na si smartbro mag bigay sa yo ng IP address, etc...

---

### Post by Script Warlock on 2008-11-19
hhhahahaha....baka smartbroKEN ang nakuha mo subscription....(joke lang ha)
bat mo naman naisipan magry ng arch di mo pa nga tapos ang pag-master ng ubuntu try mo agad arch?.. though parehas nga lang linux pero iba ang aproach ng arch....well if your fast enough to learn why not...ako din try ko yung redhat kc di pa ako nakatikim ng redhat/centos...pero pag namaster ko na ang ubuntu...lalo na tong cli:lolflag:

---

### Post by adredz on 2008-11-19
> **dodimar said:**
> Hehe.. medyo malabo pala yung explanation ko.. ngayon ko lang narealize..

Medyo mahirap kasi explain eh.. magulo kasi system nila.

Wired sya madetect.. tapos set mo lang sa DHCP... bahal na si smartbro mag bigay sa yo ng IP address, etc...

aw, hehe. thanks po.. im still getting through the wall..

---

### Post by adredz on 2008-11-19
> **boyet said:**
> hhhahahaha....baka smartbroKEN ang nakuha mo subscription....(joke lang ha)
bat mo naman naisipan magry ng arch di mo pa nga tapos ang pag-master ng ubuntu try mo agad arch?.. though parehas nga lang linux pero iba ang aproach ng arch....well if your fast enough to learn why not...ako din try ko yung redhat kc di pa ako nakatikim ng redhat/centos...pero pag namaster ko na ang ubuntu...lalo na tong cli:lolflag:

hehe, d nman smartbroken..

oo nga, super iba ang approach. you have to be super skilled para mapatakbo mo ang arch. pero okie lang, hinay2x lang.. :) actually, i am testing Debian Testing too. it's way easier compared sa Arch..

---

### Post by dodimar on 2008-11-19
Napagana mo ba?

---

### Post by adredz on 2008-11-19
d pah. maybe in a month or two? don't know, busy din ako sa school :)
im wishing someone pops in and provide me the howto? so i could save my energy.. but that would be a lesser learning experience though. hehe

---

### Post by dodimar on 2008-11-19
Never tried using Arch kasi eh.. If that's Ubuntu pwede ko bigay step by step configuration. Kasi smartbro gamit ko before.

---

### Post by adredz on 2008-11-19
> **dodimar said:**
> Never tried using Arch kasi eh.. If that's Ubuntu pwede ko bigay step by step configuration. Kasi smartbro gamit ko before.

okie lang poh,.:)

---

### Post by adredz on 2008-12-11
got my internet working hehehe. but the audio, it's dead.:(

---

### Post by dodimar on 2008-12-12
> **adredz said:**
> got my internet working hehehe. but the audio, it's dead.:(

Curious... how were you able to get smartbro working?

---

### Post by adredz on 2008-12-12
in the /etc/rc.conf just add 

> eth0="dhcp"
INTERFACES=(eth0)

mine is eth0, hence the entry.. madali lng pala, it's all in the wiki. now my next hurdle is the audio and then i'll be installing the X and the DE.:)

---

### Post by dodimar on 2008-12-12
:p Didn't I told you just set it to DHCP? :guitar:

Hope you could enjoy smartbro... 

I dropped my contract (one month before matapos lock in period ko). and filed a complaint with NTC.

---

### Post by adredz on 2008-12-12
> **dodimar said:**
> :p Didn't I told you just set it to DHCP? :guitar:
yup, but i was so disoriented then. this is my first techie experience..

> **dodimar said:**
> Hope you could enjoy smartbro... 

I dropped my contract (one month before matapos lock in period ko). and filed a complaint with NTC.

i am. my choice was globe broadband but they didn't accept my application 'cause i am only a border student. pero ok lang kc i found out globe loses connection most of the time. :)

---

### Post by dodimar on 2008-12-12
> **adredz said:**
> yup, but i was so disoriented then. this is my first techie experience..


Good job then.... :guitar:

> **adredz said:**
> 
i am. my choice was globe broadband but they didn't accept my application 'cause i am only a border student. pero ok lang kc i found out globe loses connection most of the time. :)

yup... I am on globe wireless broadband now and mag one month na din akong nag hihirap... planning to force them to give me a wired connection or I'll be dropping the contract and shift to PLDT. Bakit kaya ganito mga ISP natin dito sa Pinas?

---

### Post by adredz on 2008-12-13
got the audio working. it's fun to build software from source :)

@dodimar 
thanks :)
hehehe, mauubos mo na lahat ng ISP sa pinas ah hehe. if i were u, il have globe visibility kc mabilis daw. PLDT? i heard so many issues about it..

---

### Post by dodimar on 2008-12-14
> **adredz said:**
> 
thanks :)
hehehe, mauubos mo na lahat ng ISP sa pinas ah hehe. if i were u, il have globe visibility kc mabilis daw. PLDT? i heard so many issues about it..

Hehehe... ewan ko.. nakadalawang wireless na ako... try ko naman ang wired... pag wala pa din.. magtatayo ako sarili kong ISP... :lolflag:

---

### Post by adredz on 2008-12-14
> **dodimar said:**
> Hehehe... ewan ko.. nakadalawang wireless na ako... try ko naman ang wired... pag wala pa din.. magtatayo ako sarili kong ISP... :lolflag:
aw, pwede pahits pag me sariing ISP kana? para libre na ako :lolflag:

---

