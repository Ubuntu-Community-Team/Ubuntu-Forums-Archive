---
title: "Network Printing / File Sharing Ubuntu - Windows help!"
date: 2009-09-09
forum: Philippine Team
---

### Post by ache109 on 2009-09-09
Sirs, 

im having this problem since last week. i cannot setup my  network printing and file sharing in my ubuntu laptop. Tried on other pcs (Windows ) and theyre working fine. 

Ubuntu can detect my windows server. But I cannot do any print jobs or file sharing. Windows detects the print jobs. But the printer doesnt print for an unkown reason. hayyy... :confused:  

Printer: hp deskjet d1560
Laptop : Dell Inspiron 1150 w/ Ubuntu Jaunty 
Wifi   : TP-Link Wifi Router TL-WR340g

@add. the option to connect the laptop on the laptop is not possible  because USB ports had fried up (overheated last january). So far all hardware is OK except USB ports.

---

### Post by Findarato on 2009-09-09
Wow, what have you been smoking ? :P

I just realized we were in the philipine sectino of the forums, sorry for that :)

---

### Post by minerbog on 2009-09-09
Don't know but I want some!!!!!

WOW MAN :popcorn::guitar:

---

### Post by perbiu on 2009-09-09
Try installing samba, it should be automatically detected at System>Administration>Printing

Select New, then network printer.

There was one time i nearly done a USB to USB connection, good thing i didnt. Yes but Ethernet to Ethernet works by using a customized wirings.

---

### Post by Ravskie on 2009-09-10
[quote=perbiu;7921487]Try installing samba, it should be automatically detected at System>Administration>Printing

after installing Samba install mo na rin winbind ....

---

### Post by ache109 on 2009-09-10
sir sige try ko samba.patulong nalang po on the setup process.
 
bale ung option na *hp printer (hplip) ung pinili ko. detected nya printer kaya lang ayaw nya mag print.

---

### Post by ache109 on 2009-09-10
> **perbiu said:**
>  Yes but Ethernet to Ethernet works by using a customized wirings.

sir do you mean the wirings can affect the connection? just noticed that when the windows print queue detects my ubuntu print job, its file size range to 13mb to 15mb quite big for  text based prints. Badly, it doesnt print anything even a single byte.

---

### Post by virilc on 2009-09-10
Always check if printer is working in Linux:

[http://www.openprinting.org/show_printer.cgi?recnum=HP-DeskJet_D1560](http://www.openprinting.org/show_printer.cgi?recnum=HP-DeskJet_D1560)

System > Printing > New > Network Printer > Windows Printer via SAMBA

Click the Browse button to check if you could see the printer share. Otherwise, type in the box that says, "smb:// ...."

Type the IP address of the Windows machine where the printer is connected then the share name. Ex:

smb://192.168.1.1/HPD1560

Then try the Verify button to check if you could connect. Good luck! (nosebleed ba? hehehe sorry antok nako e hehehe)

---

### Post by AlexanderDGreat on 2009-09-10
Hi, have you read this? [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

Also, pls. don't talk tagalog, so that other users can UNDERSTAND what you're saying, pls. pass to all Filipinos. =)

---

### Post by AlexanderDGreat on 2009-09-10
Ooops... Double post, sorry!

---

### Post by ache109 on 2009-09-11
> **AlexanderDGreat said:**
> Ooops... Double post, sorry!

ok understood. Im just getting used to of speaking tagalog in the forums. Ill speak in english for others to understand.

---

### Post by Ravskie on 2009-09-11
Also, pls. don't talk tagalog, so that other users can UNDERSTAND what you're saying, pls. pass to all Filipinos. =)[/quote]


just to remind you..... you we are in philippine team sir ......

---

### Post by ache109 on 2009-09-11
> **Ravskie said:**
> Also, pls. don't talk tagalog, so that other users can UNDERSTAND what you're saying, pls. pass to all Filipinos. =)


> just to remind you..... you we are in philippine team sir ......

well, lets just consider that others dont understand tagalog. lets be quite considerate to others...

---

### Post by AlexanderDGreat on 2009-09-11
Sayang po kasi magagaling at matiyaga tayong mga Pinoy, let's share our knowledge to the world.

Kung magtatagalog po tayo baka di maintindihan ng iba, just my 2 cents. Tagalog lang kung private messages siguro.

Or you can always translate what you say in English. =)

---

### Post by ragadanga63 on 2009-09-12
Argggh...I thought this language issue was already settled when this Philippine Team section started.

---

### Post by ache109 on 2009-09-12
sorry about This language mess... by the way my problem is now solved. thanks for all your help..

---

