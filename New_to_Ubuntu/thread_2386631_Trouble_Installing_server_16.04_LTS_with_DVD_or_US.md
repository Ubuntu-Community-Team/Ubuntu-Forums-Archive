---
title: "Trouble Installing server 16.04 LTS with DVD or USB"
date: 2018-03-08
forum: New to Ubuntu
---

### Post by f4ll3ned on 2018-03-08
Good morning all,

I am having some trouble trying to install Ubuntu Server 16.04 LTS on my PC. I first tried it with a USB stick and when the installation section goes to start it fails. When checking the USB I get an md5 checksum error. I have tried creating the USB using Etcher in MacOS and using the startup disk creator on a Ubuntu Desktop machine that I have. I get the same error.

I decided to try and burn the DVD instead. I used TOAST on MacOS at best speed and got various errors when loading components. I then created another DVD at 4x speed (the lowest it will go) and still get various errors. I am pretty sure it is not the DVD-ROM as prior to this I had installed Windows 2008 Server with no problems.

Please note that I am very new to Linux. I would like to use Ubuntu Server instead of Windows 2008 as I would also like to learn more about using and administrating Linux, but my current knowledge of it is very limited.

Many thanks in advance.

---

### Post by kerry_s on 2018-03-08
sounds like a bad iso, try downloading again

---

### Post by sudodus on 2018-03-08
> **kerry_s said:**
> sounds like a bad iso, try downloading again

+1

If you can use the torrent method, the download process will be checked automatically (that the checksum matches). Otherwise you can check the md5sum (after the download, but before creating the USB boot system) according to this link,

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by f4ll3ned on 2018-03-08
Many thanks, I will try that and get back with my findings. I am going away today for 3 weeks so I will update as soon as I can.

Appreciate the help.

---

### Post by f4ll3ned on 2018-03-19
Hi all,

Just to let you know I have downloaded the ISO via torrent today. I will try and create the USB again when I get back from my travels. I read the link for checking the torrent, but can't figure out how to do this on OS X?

Many thanks.

---

### Post by f4ll3ned on 2018-04-01
Hi all I have an update. I got home yesterday and tried to install Ubuntu Server via the USB drive on my normal Ubuntu PC. This installed without a hitch. I am still getting issues trying to install on the PC that I need it installed on though with the same USB drive. I am now getting a "No Caching Mode Found" error and then the screen goes black with a cursor and every now and then throws up a text string (which is going too fast for me to read, but appears to be a different message each time).

The USB drive is plugged into an onboard USB port.

Any further advice greatly appreciated.


Edit: I should also add that the "No Caching Mode Found" error is appearing prior to the Install Ubuntu Server page.

Edit 2: Black screen has finally stopped and says unimplemented function

---

### Post by sudodus on 2018-04-01
Please tell us about the computer, where you want to install Ubuntu Server: Brand name and model, RAM size, graphics chip/card (also brand name and model), wifi chip/card (also brand name and model. Knowing these details will help us help you.

---

### Post by f4ll3ned on 2018-04-03
> **sudodus said:**
> Please tell us about the computer, where you want to install Ubuntu Server: Brand name and model, RAM size, graphics chip/card (also brand name and model), wifi chip/card (also brand name and model. Knowing these details will help us help you.

Hi. It is an Asus nForce board with with integrated GPU (I can't get chipset/model at the mo) with an AMD Phenom II 3.10 Ghz processor. RAM is 4GB and NIC is onboard. I hope that helps somewhat.

---

### Post by Tadaen_Sylvermane on 2018-04-06
I cant recall any phenom 2 chips at 3.1 ghz. Are you overclocking? Linux doesnt tolerate overclocking like windows. Can cause all sorts of issues.

*edit* nevermind. Found some dualies that were stock at 3.1

---

