---
title: "Help For VOIP configuration!"
date: 2012-03-05
forum: Philippine Team
---

### Post by wilvyrux-naked on 2012-03-05
Good day Guys,

     theres anyone knows how to configure a Voip using centos 2.6 or asterisk 1.5 ?...or if you know the other way to configure it?.using novell or in ubuntu..Please guide me a step by step procedure if how to do that thing..Thanks a lot.....:).

---

### Post by pinoyskull on 2012-03-08
centos 2.6???

just one of the guides I saw in the interwebz
[http://www.voip-info.org/wiki/view/CentOS+5+and+Asterisk+1.4.x+installation](http://www.voip-info.org/wiki/view/CentOS+5+and+Asterisk+1.4.x+installation)

---

### Post by kiminaiseah on 2012-03-18
> **wilvyrux-naked said:**
> Good day Guys,

     theres anyone knows how to configure a Voip using centos 2.6 or asterisk 1.5 ?...or if you know the other way to configure it?.using novell or in ubuntu..Please guide me a step by step procedure if how to do that thing..Thanks a lot.....:).

1. download centos

2. yum groupinstall "Development Tools"

3. download asterisk

4. compile

4a. ./configure

4b. make menuselect

4c. make

4d. make install

4e. make samples

--

asterisk core is done, 

--

i rather prefer to install asterisk on Debian Base Distro, why?

centos hasnt library for openh323

---

### Post by ChyrillStucker on 2012-03-29
Nice discussion and good advice on VoIP installation. Although I use a Hosted PBX service with VoIP and they configure everything and provide a ready-to-use system, it was nice to know how it is done.

---

### Post by kiminaiseah on 2012-05-01
for me. dont use centos for pbx , because it dont have h323 library

---

### Post by ichi_730 on 2012-05-01
> **wilvyrux-naked said:**
> Good day Guys,

     theres anyone knows how to configure a Voip using centos 2.6 or asterisk 1.5 ?...or if you know the other way to configure it?.using novell or in ubuntu..Please guide me a step by step procedure if how to do that thing..Thanks a lot.....:).

Yam? Ikaw ba yan? Norman to chong :lolflag:

---

### Post by 6wires on 2012-06-05
...mas ma trabaho kung individual module ang ini-install mo pre, Mag-trixbox ka nalang, derecho, no problem, ang gagawin mo nalang is that co-configure mo nalang ang asterisk, that's all in one package na.

...follow this link to download trixbox, [http://fonality.com/trixbox/downloads](http://fonality.com/trixbox/downloads) 

> **wilvyrux-naked said:**
> Good day Guys,

     theres anyone knows how to configure a Voip using centos 2.6 or asterisk 1.5 ?...or if you know the other way to configure it?.using novell or in ubuntu..Please guide me a step by step procedure if how to do that thing..Thanks a lot.....:).

---

