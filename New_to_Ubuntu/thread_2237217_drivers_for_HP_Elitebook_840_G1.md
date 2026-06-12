---
title: "drivers for HP Elitebook 840 G1"
date: 2014-07-31
forum: New to Ubuntu
---

### Post by AlexValex on 2014-07-31
Hello, the same old problem with drivers for linux.
I use a dualboot machine Win7 / Ubuntu 14.04. 
Some of the drivers that Ubuntu came up with work right with my machine, but some ... I have trouble with.
Here's the detailed specs of my machine: [http://www8.hp.com/emea_middle_east/en/products/laptops/product-detail.html?oid=5446818#!tab%3Dspecs](http://www8.hp.com/emea_middle_east/en/products/laptops/product-detail.html?oid=5446818#!tab%3Dspecs)

1. The most serious problem is with sound, which is an IDT High Definition Audio. 
Some people had a particular problem with the manufacturer (IDT Sound , but different, older laptops): they had sound on headphones, but not on the laptops' speakers.
It's not my problem: I don't have sound neither in headphones nor in speakers. And, when testing the sound in the System Settings, the applications blocks (it turns grey, and if I try to close it I get the message with the options Wait / Force close). 

2. The video: it's a dual video, like most laptops today. The Intel works fine, but the AMD Radeon HD 8750M (1 GB GDDR5 dedicated) woun't install. I've downloaded the latest driver from AMD website and tried to install it, it goes ok through the first steps, I get the wizard for installation, get the hole process, and at the end I'm informed that everything's allright. After closing the installation wizard, I've got a message from Ubuntu: "Do you want to install the generated package" (something like this) - I click yes and nothing happens. I don't have the Catalyst application in my start button. 

3. Other drivers required: fingerprint reader and HP HD webcam. These are: Biometrics: Validity Sensor (VSF495) , and Webcam: HP HD Webcam.

Everything else (USB, wireless, network) seems to work fine. I don't know about bluetooth.

---

### Post by do120free.fr on 2014-09-05
Hi[**[COLOR=#000000] AlexValex[/COLOR]**]("http://ubuntuforums.org/member.php?u=1333271"),

I want to buy the same laptop soon at work to use with Linux. Did you find solutions for your problems with this laptop ?

---

### Post by AlexValex on 2015-05-16
Sorry for the late reply.

No solution for my laptop except for the video, which I managed to fix. 
But, a few days ago my laptop crashed seriously - such a luck it's under guarantee. Linux works great on it, unless you want sound, camera & biometrics.

---

