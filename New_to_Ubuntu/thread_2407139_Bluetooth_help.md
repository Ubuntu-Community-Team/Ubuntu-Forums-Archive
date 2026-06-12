---
title: "Bluetooth help"
date: 2018-11-30
forum: New to Ubuntu
---

### Post by packpariah on 2018-11-30
Good Morning Ubuntu people,

I am having issues with a couple of bluetooth devices I had connected that suddenly do not register anymore. 

A little background, I am about a month into learning command line and navigating Ubuntu. About 75% of the solutions I have tried with multiple problems, have not worked. But I am determined to learn linux (any resource suggestions is greatly appreciated).
I am currently running Mate 18.04 downloaded on a [eMMC]("https://ameridroid.com/products/emmc-5-1-module-xu3-xu4-linux-blue-dot")  mounted on a [Odroid XU4 ]("https://ameridroid.com/products/odroid-xu4") with their [USB Bluetooth Module 2]("https://ameridroid.com/products/usb-bluetooth-module-2") plugged into the only USB 2.0 port. Currently I have a logitech mx2 anywhere and a finitie keyboard, which so far have not had any problems.

I had a [GoNavate G11]("https://www.amazon.com/GoNovate-Bluetooth-Playtime-Magnetic-Handsfree/dp/B01MZ48A21") and a [Mpow EM1 ]("https://www.amazon.com/Mpow-Bluetooth-Headphones-Microphone-Invisible/dp/B075SZMP2N/ref=sr_1_20?s=wireless&ie=UTF8&qid=1543583081&sr=1-20&keywords=mpow+bluetooth+headphones") successfully connect using the GUI. However, in the past week the Mpow stopped connecting to the bluetooth. And about an hour ago the GoNavate has stopped connecting to. Since I have had this setup I have never been able to opent the Devices.. option in the bluetooth system tray or the Bluetooth Manager application, which were my first stops because I was hoping to unpair/remove the devices and plugins then reconnect. When trying to open Bluetooth Manager the menu system tray disappears and nothing opens. When trying to open Devices.. from the bluetooth icon in the tray on the top right of the screen a starting blueman pops (see attached "starting blueman" image) up on the task bar on the bottom of the screen, then disappears and nothing ever opens. 

I tried following this sites "[COLOR=#333333][FONT=Ubuntu]I cannot connect to an already paired device after reboot or long idle time" and get with no success (see attached "bluetooth attempt" image).

Does anybody have a way to fix the Bluetooth Manager app / Devices..? and/or any resources on how to remove a previously paired device/plugins via terminal would be even more greatly appreciated(I am trying to learn the command line after all)?

Thank you for any help ahead of time[/FONT][/COLOR]

---

### Post by packpariah on 2018-12-03
Well obviously I must of not correctly communicated my problems since I did not receive any feedback. 

I was able to get the Bluetooth manager to work (temporarily, more on that later), which allowed me to remove the two Bluetooth devices I was having issues with. I followed this [videos ]("https://youtu.be/z-K8IcS_nVw")advice accept for after ```
sudo apt-get install blueman
``` the terminal suggested that I run ```
sudo apt autoremove
```. Other than that I followed it verbatim. 

However, I lost the ability to search(in Bluetooth manager GUI) and set up new devices (in the Bluetooth system tray). I restarted the my computer and now I am back to square one (I have lost the ability to manage current devices but I can set up new devices). 

My problem has been resolved temporarily (until the next time a devices suddenly decides to stop connecting), but I imagine I will have to do the same thing over again to get it to work.

I welcome any feedback or help to permanently fix this issue.

---

