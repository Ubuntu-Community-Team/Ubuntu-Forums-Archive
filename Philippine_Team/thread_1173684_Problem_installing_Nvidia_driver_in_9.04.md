---
title: "Problem installing Nvidia driver in 9.04"
date: 2009-05-30
forum: Philippine Team
---

### Post by Nhatz on 2009-05-30
Hindi ko parin talaga ma-install Nvidia drivers sa 8.10 at 9.04. kaya heto balik 8.04 parin ako. may nakapag install na ba ng Nvidia Drivers for 8500GT sa inyo? 

ASTIG!!! :guitar:

---

### Post by loell on 2009-05-30
nasubukan mong maginstall ng envy?

---

### Post by pinoyskull on 2009-05-30
I've been hearing a lot of NVIDIA related problems with 9.04 hmmm...

---

### Post by badrra on 2009-05-31
di kasi open source kaya ganun. Wala akong experience sa 8500GT kaya di ako maka contribute dito pero mag research din ako baka meron akong makitang significant.

---

### Post by tagabukid on 2009-05-31
when i installed Jaunty, bad trip nga ang nvidia driver.. i used envy-ng to get the 180 driver, ayun gumana naman.. btw, di po to 8500 9400gt ang sa akon.. on hardy which i am on right now, i use the 173 driver naman via envy din.. tilawi lang bro, basi mag andar man sa imo.

---

### Post by vivatsemiramis on 2009-06-01
> **Nhatz said:**
> Hindi ko parin talaga ma-install Nvidia drivers sa 8.10 at 9.04. kaya heto balik 8.04 parin ako. may nakapag install na ba ng Nvidia Drivers for 8500GT sa inyo? 

ASTIG!!! :guitar:

haha that was totally my problem a few weeks ago with my desktop pc. i left it as it was, without compiz. haha i really couldn't make it work despite all our ubuntu loco friends' suggestions. regards

---

### Post by leipogs23 on 2009-06-01
> **vivatsemiramis said:**
> haha that was totally my problem a few weeks ago with my desktop pc. i left it as it was, without compiz. haha i really couldn't make it work despite all our ubuntu loco friends' suggestions. regards

Hehehe. Oo nga eto din problem mo diba?

[http://ubuntuforums.org/showthread.php?t=1156213](http://ubuntuforums.org/showthread.php?t=1156213)

Kaso mas general tong post na to,mukang di lang yung envidia model mo ang me problem.hehehe

---

### Post by vivatsemiramis on 2009-06-01
@leipogs23, haha yeah

@nhatz: you may try those suggestions other loco friends have recommended in the older thread [http://ubuntuforums.org/showthread.php?t=1156213](http://ubuntuforums.org/showthread.php?t=1156213). it might help you, although i couldn't make it work :)

> **leipogs23 said:**
> Hehehe. Oo nga eto din problem mo diba?

[http://ubuntuforums.org/showthread.php?t=1156213](http://ubuntuforums.org/showthread.php?t=1156213)

Kaso mas general tong post na to,mukang di lang yung envidia model mo ang me problem.hehehe

---

### Post by Nhatz on 2009-06-01
[QUOTE=loell]nasubukan mong maginstall ng envy?[/QUOTE]

yeah may topak ata yung 180 na driver ng Nvidia. nainstall ko sya then pagreboot ko ayun ayaw nang tumulo sa desktop. prblema ko yun since 8.10 kaya balik hardy ako stable sya. BTW naka 8500GT ako na SLI.

[[IMG]http://img141.imageshack.us/img141/7595/dsc00016khy.th.jpg[/IMG]](http://img141.imageshack.us/my.php?image=dsc00016khy.jpg)

ASTIG!!! :guitar:

---

### Post by guitar_man on 2009-06-02
> **Nhatz said:**
> yeah may topak ata yung 180 na driver ng Nvidia. nainstall ko sya then pagreboot ko ayun ayaw nang tumulo sa desktop. prblema ko yun since 8.10 kaya balik hardy ako stable sya. BTW naka 8500GT ako na SLI.

ASTIG!!! :guitar:

grabe naman kasi mga card mo boss nhatz,card mo palang baka price na ng kompyuter ko.:lolflag:


Good thing to know na gumagana pala SLI sa linux...yun nga lang may topak.

---

### Post by Nhatz on 2009-06-02
> **guitar_man said:**
> grabe naman kasi mga card mo boss nhatz,card mo palang baka price na ng kompyuter ko.:lolflag:


Good thing to know na gumagana pala SLI sa linux...yun nga lang may topak.

HIndi naman... mura lang yan. gumgana naman SLI pero ginagamit ko sya for Gaming dun sa isang HDD ko. hehehe :D

ASTIG!!! :guitar:

---

### Post by guitar_man on 2009-06-02
suggest lang.


Nasubukan nyo na ba to??

[http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us")


may support na pala yung Nvidia website para sa mga linux users at pwede ka na magdownload ng driver from the website mismo.

---

### Post by Nhatz on 2009-06-02
> **guitar_man said:**
> suggest lang.


Nasubukan nyo na ba to??

[http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us")


may support na pala yung Nvidia website para sa mga linux users at pwede ka na magdownload ng driver from the website mismo.

Yeah. mukang yung 180 may problema. pero yung 173 ok.

ASTIG!!! :guitar:

---

### Post by So*nix on 2009-06-02
> **Nhatz said:**
> Hindi ko parin talaga ma-install Nvidia drivers sa 8.10 at 9.04. kaya heto balik 8.04 parin ako. may nakapag install na ba ng Nvidia Drivers for 8500GT sa inyo? 

ASTIG!!! :guitar:

Well i am new to linux but may be i can help you out on this one 

Download latest NVIDIA-Linux Drivers

then press ctrl+alt+F1 

Login as root

killall gdm (if using gnome Or kdm if using Kde)

cd (directory which has nvidia driver in it)

sh (name of the driver file)

Accept confirmations

Reboot

& Bingo , yor are done

It's as simple as this .

---

### Post by dodimar on 2009-06-02
> **Nhatz said:**
> yeah may topak ata yung 180 na driver ng Nvidia. nainstall ko sya then pagreboot ko ayun ayaw nang tumulo sa desktop. prblema ko yun since 8.10 kaya balik hardy ako stable sya. BTW naka 8500GT ako na SLI.

[[IMG]http://img141.imageshack.us/img141/7595/dsc00016khy.th.jpg[/IMG]](http://img141.imageshack.us/my.php?image=dsc00016khy.jpg)

ASTIG!!! :guitar:

nagana ba SLI sa linux?

---

### Post by Nhatz on 2009-06-02
> **dodimar said:**
> nagana ba SLI sa linux?

Yup... hehehe

ASTIG!!! :guitar:

---

