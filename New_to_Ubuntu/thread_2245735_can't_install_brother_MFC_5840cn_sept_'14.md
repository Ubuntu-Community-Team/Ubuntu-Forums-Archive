---
title: "can't install brother MFC 5840cn sept '14"
date: 2014-09-25
forum: New to Ubuntu
---

### Post by cazza on 2014-09-25
Hi
I'm feeling really stupid and OLD! ive been going around in circles trying to get my trusty usb and network Brother MFC 5840cn to work with UBUNTU. 
There are old posts on this but the links have expired and Im really stuck. The printer is amazing. I can refill the inks without even removing them. I need to do loads of printing for my students which would cost me a packet if I didnt use this printer. 
I was not always totally hopeless at IT  ,I did A level computer science 25 years ago..but clearly my knowledge is now redundant....feeling past it...
can anyone please provide me with an idiots guide to getting the printer to work. I've had to delete windows XP and move to Ubuntu when my hard disk failed. I used a stick with 'try ubuntu' to recover my files and now have installed ubuntu instead and its amazing except for the fact I can't print. If only the model was listed in the printer list :-(   
Please please please can anyone help?

---

### Post by whitesmith on 2014-09-25
According to official Ubuntu documentation ([https://wiki.ubuntu.com/HardwareSupportComponentsPrintersBrother](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersBrother)) this printer should work. What happens when you try to print? Does the device try to come to life? Does it do anything at all? What happens if you try another USB port? Can you print a text document from gedit? These are just some ideas to kick around. I don't own this model. Matter of fact, I've never owned a Brother anything. I had a terrible experience with a Canon and had to give it away and switch to HP to get anything to print. Play around with my suggestions and see where they take you. Regards.

[edit] Final thought: Since the cost of ink is a consideration, why not scrap the inkjet for a laser printer? Up-front costs are a little higher, but you'll $ave because toner is so much cheaper than ink.

---

### Post by gifford on 2014-09-25
Go to this link on the Brother site which is for your printer. [http://support.brother.com/g/b/downloadlist.aspx?c=us_ot&lang=en&prod=mfc5840cn_all&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us_ot&lang=en&prod=mfc5840cn_all&os=128)
Follow the instructions there to download the drivers and to install.
Brother printers are great and for the most part easy to install and set up in Linux.
I have used them for years with Ubuntu and really would not use any other brand as they are robust and reliable.

---

### Post by pdc on 2014-09-28
so cazza ..........how is it going? Gifford pointed you to the Brother site that allows you to download the [COLOR="#0000FF"]install tool[/COLOR]: [http://support.brother.com/g/b/downloadend.aspx?c=us_ot&lang=en&prod=mfc5840cn_all&os=128&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadend.aspx?c=us_ot&lang=en&prod=mfc5840cn_all&os=128&dlid=dlf006893_000&flang=4&type3=625)

if you click on that link, and select SAVE when you download ..........and if I give you some commands to paste into a terminal............that will get the install script running for you ....... you happy to open a terminal?

[COLOR="#FF0000"]cd Downloads
gunzip linux-brprinter-installer-2.0.0-1.gz
sudo bash linux-brprinter-installer-2.0.0-1[/COLOR]

if you copy and paste each of the lines above; line by line .......hitting ENTER after each paste ......................

---

### Post by cazza on 2014-10-07
Don't know how to thank you guys. I really needed the step by step version. I thought I'd done this but clearly I was getting it wrong . Thanks again took me a while but would have never managed without you .

---

### Post by pdc on 2014-10-07
thanks for your post; delighted to know it is working well; enjoy

---

### Post by Vladlenin5000 on 2014-10-07
Please use the thread tools to mark this one as solved, so others may benefit.

---

### Post by cazza on 2014-10-08
Before I mark as solved I should add some of the errors for the benefit of others.When you're at almost the end of installation you are asked to input the brother model if you include the word 'brother' in the description it will not work ie. just enter MFC-5840CN You must put the hyphen in as well. Not sure why but it woudn't work without. 
Also although I set up as a network printer with IP address it wouldnt work on the network until I'd plugged in via USB, changed to USB in printer settings , printed test page, then put settings back to network. Ie. In effect same settings but wouldnt work until used USB method.

---

### Post by cazza on 2014-10-08
Mfc-5840cn

---

### Post by cazza on 2014-10-08
needs to be upper case MFC-5840CN

---

### Post by cazza on 2014-10-08
. I wish I hadnt already marked this as solved becaused when I tried to add printer to even older computer that teenage kids use I couldnt manage it. It worked on computer with INTEL celeron Duo but this even older one has Intel Centrino. Terminal text says  failed because csh/tcsh required any ideas. I tried both deb and rpm drivers. Can anyone help please maybe I need to start new thread?

---

### Post by Paulgirardin on 2014-10-08
In the distant past I had to install csh or tcsh for my MFC-3220.
It's available in the repos - search for csh in the software center

---

### Post by Li_Wu on 2015-09-17
The bro is an excellent hardware. I have an MFC too.

Linux driver install usually can be done. Except sometimes not. Archlinux for example is difficult since it does not handle .deb or .rpm.

Also the bro's from bro company for years have not fixed some package problem such as the one with /opt/brother/modem/src/brusbmfc.c

Though one has to rely on ~ 3 binaries, the modules build from source and stop working after kernel update.

It is very reassuring to have the bro MFC fully functional, say in mint Linux 17.2 which can be done. See [https://wiki.debian.org/Brother/MFC7440N](https://wiki.debian.org/Brother/MFC7440N) for inspiration from that model. The bro amongst each others have pretty similar install methods.

---

