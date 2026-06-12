---
title: "Nvidia Problems With Hardy"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by RAJESHKSV on 2008-04-26
I Enabled Nvidia Graphic Card(8400 Model;dell Vostro 1500 Model) In Ubuntu 8.04 Thr Hardware Drivers(system->administartion).it Asked Me To Restart .as I Restarted The System , Ubuntu Logo Came But Then A Screen With White Stripes Came Insead Of Login Screen.i Am Unable To Continue Further:(

So I Went Thr Recovery Mode And Then It Gave Me 3 Options
Use Normal Boot
Go To Root Thr Terminal 
 Fix Xserver 

When I Clicked  Fix Xserver ,it Overwriten The Present Xfile(some Sort Of That File) With Old Known Good Configuration File And Started My System .its Working Fine But Without Nvidia Graphic Card Enabled:(so Plz Temme How 2 Enable Nvidia Graphic Card??

I Am Unable To Enable Any Desktop Effects..plz Help Me...

My System Specifications:

Dell Vostro 1500 Model
2gb Ram ,1.6ghz Core2duo Processor,
Nvidia 8400 Model.

---

### Post by dokdoom on 2008-04-26
Did you try going in to Restricted Driver again? Is the nvidia driver in use? If so try disabling it and renabling it again. If it is not enabled then do so. If you try all of this and still can't get rendering to work check the "Device Section" in your /etc/X11/xorg.conf and make sure the driver is correct. I think it's just nvidia but if it says vesa you will need to change that. Hope this helps.

---

### Post by hotdog003 on 2008-04-26
There's a bug about this, try checking here: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/208718](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/208718)

I have the same laptop and the same problem. Reinstalling through the restricted drivers manager does not help.

---

### Post by edajai on 2008-04-27
this might be of help
[http://ubuntuforums.org/showthread.php?t=712479&page=5]("http://ubuntuforums.org/showthread.php?t=712479&page=5")

---

### Post by RAJESHKSV on 2008-04-27
THANK YOU guys....It worked.I downloaded the driver and installed it.Now NVIDIA graphic card is enabled and all desktop effects were working...TQ ubuntu forums.:guitar:

---

