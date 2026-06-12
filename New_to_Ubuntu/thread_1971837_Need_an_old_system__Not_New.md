---
title: "Need an old system ???? Not New"
date: 2012-05-02
forum: New to Ubuntu
---

### Post by frankjeffries on 2012-05-02
I have tried everything to get Ubuntu 12.04 working on my Pc and I have finally realised why it will not work!! My PC is too new  
below are its Specs.                                                   
Gigabyte H77M-D3H motherboard
i5 2500k cpu
32gbit g skill 1600 ripjaws ram
1x500 gbit sata H/D 6gbs
saphire ATI 7770 o/c graphics card Plus other older H/ds.
Windows 7 Ultimate
After looking up these pages I have realised that probably non of these are supported by Ubuntu 12.04 and this is why it will not boot I'll just have to try it on my old PC. Ta for now.

---

### Post by bodhi.zazen on 2012-05-03
all of that should work perhaps with the exception of your ATI card.

---

### Post by mikewhatever on 2012-05-03
Sounds like an excuse to flash the hardware.

---

### Post by jerome1232 on 2012-05-03
What specific issues are you having, my 2 minutes of googling tells me your ati card should work once you install catalyst. Without a knowledge of your specific issues it's hard to suggest ways to get Ubuntu working on your setup.

edit: List of supported hardware for Catalyst, your card is listed as supported
[http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware)


As an aside, *very* new graphics cards are almost a guarantee your going to run into issues with Linux, the drivers tend to be a bit behind the Windows ones.

---

### Post by frankjeffries on 2012-05-03
> **jerome1232 said:**
> What specific issues are you having, my 2 minutes of googling tells me your ati card should work once you install catalyst. Without a knowledge of your specific issues it's hard to suggest ways to get Ubuntu working on your setup.

edit: List of supported hardware for Catalyst, your card is listed as supported
[http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware)


As an aside, *very* new graphics cards are almost a guarantee your going to run into issues with Linux, the drivers tend to be a bit behind the Windows ones.The issues I'm having is I install ubuntu 12.04 and it appears to install and says remove the cd and reboot but when it reboots there is nothing there it just goes black screen for a few seconds ( no graphics ) and then boots into windows when I look the drive that I install to is not visible in windows but by using acronis disc image I see that 11.6 gigs have been installed to the H/D which means its there just will not boot

---

### Post by bodhi.zazen on 2012-05-03
> **frankjeffries said:**
> The issues I'm having is I install ubuntu 12.04 and it appears to install and says remove the cd and reboot but when it reboots there is nothing there it just goes black screen for a few seconds ( no graphics ) and then boots into windows when I look the drive that I install to is not visible in windows but by using acronis disc image I see that 11.6 gigs have been installed to the H/D which means its there just will not boot



Hold down the shift key as you boot. You should get a menu.

/me thinks the grub hidden menu by default is a bad idea.

---

