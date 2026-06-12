---
title: "Transfer Files to Nokia Phone"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by paulburman on 2008-06-22
Hello, 

I am very new with Ubuntu, so any easy to understand advice would be sincerely appreciated.

I just got a new cell phone, a Nokia 5310 with XpressMusic. I want to be able to transfer music files to the phone via a usb cable, but I can't seem to make that happen. I have everything plugged in, and the phone is recognized (I checked in the terminal by entering lsusb), I just can't get to a spot where I can drag files on to the phones sd drive. I also tried to open Rhythmbox to transfer music files.

Also, when I first plug the phone,the computer recognizes it as a camera and tries to import the image files.

Anyway, if you have experienced this before or know how I can transfer files via a USB cable, you can make my day by giving me some answers.

Thanks!

---

### Post by wolfen69 on 2008-06-22
try using wammu to transfer files. nokia phones are supported.
```
sudo apt-get install wammu
```

---

### Post by nothingspecial on 2008-06-22
This is not a solution. I`m still trying to get my wife`s samsung phone working over usb. 
 The only thing I could do was buy a very cheap usb dongle. It`s an Advent V2.0 + EDR.
Never had a problem with a Nokia though.

---

### Post by Biggy on 2008-06-22
Do you have bluetooth? if you have bluetooth install [Blueman]("http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56")

or try [Gnokii]("http://www.gnokii.org/")

from terminal :

> sudo apt-get install gnokii

---

### Post by paulburman on 2008-06-22
Thanks for the advice so far. I installed Wammu and it is not recognizing that a phone is attached when I work the wizard for it. I don't have blue tooth on this oldish dell laptop, so that is not an option for me.

Maybe I am getting this all wrong. Here is a new question: if the computer recognizes that the phone is connected (which it does), and everything was working as it is supposed to work, where would I be able to access the files on the phone and transfer files to the phone? Would that just be through the computer - file browser screen?

---

### Post by liquid circuit on 2008-07-09
It sounds as if you have the phone's USB connection set to "Printing & media".  It should be in "Data storage" mode, so that it functions as a USB Mass Storage device.

From the standby screen:
```
Press "Menu"
Select "Settings"
Select "Connectivity"
Select "USB data cable"
Select either "Data storage" or "Ask on conn."
```

If you choose "Ask on conn.", everytime you connect the device via USB you will be prompted on the phone to select either "PC Suite" (for use with Nokia PC Suite), "Printing & media" (emulate a digital camera), or "Data storage" (USB Mass Storage mode).

---

### Post by paulburman on 2008-07-09
YES YES YES YES!!!!!!!!!!!

That did it! You are a genius! I had totally given up, and then this person with knowledge of computers comes in fixes everything in our swoop!

This is a wonderful day for the computer illiterate and the gentle nerds who generously help them.

Thank you very very much. I am sincerely appreciative.

Paul

---

### Post by jidol on 2008-07-21
Hi all,
I think that there may be problem of usb cable or may be some software problem.So try again to install the software or just try other data cable.I hope so that your problem may be solved.

---

### Post by Cotopaxi on 2008-07-21
Sorry, Can anyone give me a helping hand about connecting a Sharp GX25 or Sharp GX29 via Data Cable to Wammu, Gnokii or any other software?

Thanks!

---

### Post by Shaunak on 2008-07-28
Found this link while searching:
[http://news.softpedia.com/news/Transfer-Files-To-And-From-Your-Nokia-Phone-63116.shtml](http://news.softpedia.com/news/Transfer-Files-To-And-From-Your-Nokia-Phone-63116.shtml)

---

### Post by niceguy123 on 2008-08-11
Hasn't worked for me with my new E71. I'm more than a little frustrated.

---

### Post by daariil on 2008-12-24
Hello.

You said that i should do this:

From the standbyscreen:
Press "Menu"
Select "Settings"
Select "Connectivity"
Select "USB data cable"
Select either "Data storage" or "Ask on conn."

And i cant really figure out what standby screen you are talking about.
Is it in Wammu or in the mobile or something else?

Cheers

---

