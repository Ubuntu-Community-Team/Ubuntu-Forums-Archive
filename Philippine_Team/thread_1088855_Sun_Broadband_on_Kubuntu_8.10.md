---
title: "Sun Broadband on Kubuntu 8.10"
date: 2009-03-06
forum: Philippine Team
---

### Post by coolliioo on 2009-03-06
if tried
[http://ubuntuforums.org/showthread.php?t=1018922](http://ubuntuforums.org/showthread.php?t=1018922)

it didnt work, kace iba un knetworkmanager.

i also tried configuring wvdial to:

> [Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = *99#
Modem = /dev/ttyUSB0
Username = xxx
Password = xxx
Baud = 9600

[Dialer sun]
Init2 = ATZ
Init3 = ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
Init4 = AT+CGDCONT=1,”IP”,”fbband”
Modem Type = Analog Modem
ISDN = 0
Modem = /dev/ttyUSB0
Stupid Mode = 1
Baud = 460800

no luck pa rin.....

---

### Post by jepong on 2009-03-07
this works fine with me then using mobile broadband on knewtworkmanager... yung huawei e220 ha.

*99# na number and fbband na apn lang nilagay ko and ok na.

---

### Post by coolliioo on 2009-03-07
i alredi tried that... knetworkmanager wont dial...

---

### Post by jepong on 2009-03-13
i forgot to tell na may sun broadband pala di nag wwork sa linux and apple. better ask them sa sun shop. na-post ko na ata yung story dito before eh.

yung housemate ko may macbook pro and naka-bootcamp to windows xp. of couse gumana yung sun broadband sa xp but not sa mac nya. so she approach the sun shop sa galleria and ayun may inupgrade daw eh and ok na. nakikigamit din ako nun and working sa kubuntu 8.10.

yung boss ko may unang labas nung sun broadband and sa windows lang din nag-work. sister company namin kasi sun kaya sa mga bosing pinatest yung unang labas. di rin ito nag-work sa linux.

---

### Post by dodimar on 2009-03-13
> **jepong said:**
> i forgot to tell na may sun broadband pala di nag wwork sa linux and apple. better ask them sa sun shop. na-post ko na ata yung story dito before eh.

yung housemate ko may macbook pro and naka-bootcamp to windows xp. of couse gumana yung sun broadband sa xp but not sa mac nya. so she approach the sun shop sa galleria and ayun may inupgrade daw eh and ok na. nakikigamit din ako nun and working sa kubuntu 8.10.

yung boss ko may unang labas nung sun broadband and sa windows lang din nag-work. sister company namin kasi sun kaya sa mga bosing pinatest yung unang labas. di rin ito nag-work sa linux.

Ang alam ko mapapagana siya. Pero kailangan mo muna i-setup under windows xp tapos saka mo kabit sa mac or linux.

---

### Post by pinoyskull on 2009-03-15
> **jepong said:**
> i forgot to tell na may sun broadband pala di nag wwork sa linux and apple. better ask them sa sun shop. na-post ko na ata yung story dito before eh.

yung housemate ko may macbook pro and naka-bootcamp to windows xp. of couse gumana yung sun broadband sa xp but not sa mac nya. so she approach the sun shop sa galleria and ayun may inupgrade daw eh and ok na. nakikigamit din ako nun and working sa kubuntu 8.10.

yung boss ko may unang labas nung sun broadband and sa windows lang din nag-work. sister company namin kasi sun kaya sa mga bosing pinatest yung unang labas. di rin ito nag-work sa linux.
If you are using Huawei E220, no need to go to Sun Shop, you can configure it yourself it you're going to use it on MacBook, visit this site ([http://www.mobilebroadbandrocks.com/category/hardware/huawei-e220 ]("http://www.mobilebroadbandrocks.com/category/hardware/huawei-e220")
it will tell you what to do.

---

### Post by jepong on 2009-03-16
ahhhh... so yun pala ang ginawa nila. hmf! mau upgrade-upgrade pa cla nalalaman eh unlock pala ang term.

---

### Post by pinoyskull on 2009-03-16
> **jepong said:**
> ahhhh... so yun pala ang ginawa nila. hmf! mau upgrade-upgrade pa cla nalalaman eh unlock pala ang term.
Not that one. Look at the list below Unlocking, you will see Links for Linux Drivers and Mac OSX

---

### Post by genius24k on 2009-05-18
Huawei E220 and E160 both works sa ubuntu other linux, it just takes more work pag gamit mo is e160, I use this how to get it to work with my laptop running linux

Huawei E160 on Linux
[http://www.review-ninja.com/2009/05/huawei-e160-and-ubuntu-e160-linux-howto.html](http://www.review-ninja.com/2009/05/huawei-e160-and-ubuntu-e160-linux-howto.html)

---

