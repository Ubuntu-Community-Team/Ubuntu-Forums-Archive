---
title: "Howto: mOOo OpenOffice Impress Controller in Intrepid"
date: 2009-02-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Baji on 2009-02-06
Using mOOo you can control your presentation from your mobile phone. Website: [https://mooo.dev.java.net]("https://mooo.dev.java.net/")

You need working bluetooth with your mobile

This guide is written for Intrepid Ibex

**Download the exension for openoffice**
*First install java for openoffice*
```
sudo apt-get install openoffice.org-java-common sun-java6-jre libbluetooth-dev
```
*Second make a symbolic link so Bluecove works with bluez 4*
```
sudo ln -s /usr/lib/libbluetooth.so /usr/lib/libbluetooth.so.2
```
*Download the openoffice extension from the [mOOo website]("https://mooo.dev.java.net/servlets/ProjectProcess?tab=1")*
```
[https://mooo.dev.java.net/files/documents/7339/113149/mooo-ic-desktop-0.6.oxt]("https://mooo.dev.java.net/files/documents/7339/113149/mooo-ic-desktop-0.6.oxt")
```

**Select the java version in openoffice**
In Impress, go to extra, options, and make sure you have the Java JRE 1.6.0_10 Selected


**Install the extension in openoffice**
Open impress, -> Tools -> Extensions Manager -> Add ...
Select the downloaded oxt file and install, restart impress.

**Install mOOo on your mobile phone**
*Download the mobile extension from the [mOOo website]("https://mooo.dev.java.net/servlets/ProjectProcess?tab=1")*
```
[https://mooo.dev.java.net/files/documents/7339/118336/mooo-impress-controller-mobile.jar]("https://mooo.dev.java.net/files/documents/7339/118336/mooo-impress-controller-mobile.jar")
```
Right click on mooo-impress-controller-mobile.jar, click send to... , and transfer it to your mobile phone, and install it on your mobile.


**Use mOOo in openoffice to control slides**
In impress, click mOOo IC -> Select Device ... 
Select your phone (make sure you have starte mOOo on your phone)
In impress, click mOOo IC -> On/Off
You can now control the slideshow using your mobile !

For this howto I used a N95, and tested on two PC's using Intrepid Ibex with all updates 

bluez 4.12-0ubuntu5 
obex-data-server 0.4.2-0ubuntu2 
sun-java6-jre 6-10-0ubuntu2
openoffice.org-impress 1:2.4.1-11ubuntu2.1

---

