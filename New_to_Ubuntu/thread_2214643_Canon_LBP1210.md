---
title: "Canon LBP1210"
date: 2014-04-02
forum: New to Ubuntu
---

### Post by Roland_Larsson on 2014-04-02
I am an absolute beginner in Linux. 
I am trying to install said printer manually.  The packages below installd OK.
cndrvcups-capt.deb 

cndrvcups-common.deb[TABLE]
[TR]
[TD][/TD]
[TD][/TD]
[TD]But then in the terminal I get a "Bad device-uri scheme "ccp"" 
when I tried the following sequence from the documentation here:
[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]
sudo /etc/init.d/cups restart       (seemed to work OK)
sudo lpadmin -p LBP1210 -m CNCUPSLBP1210CAPTK.ppd -v ccp://localhost:59687 -E 

I don't understand the command language - just copying from the documentation 
and changing out LBP3050 with LBP1210.
Is the printer uncompatible with Ubuntu 1310 or what?

---

### Post by Rex Bouwense on 2014-04-02
Does this help?
[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)

---

### Post by Roland_Larsson on 2014-04-03
That is the link where I found the instruktion and commands I used

---

### Post by pdc on 2014-04-04
Hi Roland; welcome to the forums; if we can say *bonjour*, it may help you with the guide I recommend below ..

I was wondering if had a 32bit system? ........ that makes things easier

I have thought the guide by Sivella, who maintains the french CAPT support; is very thorough

[http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp) ........ google translate will let you read it in your favourite language: the only trick is google translate mucks up the spacings in commands:

__________________________________________-


.....firstly check what you have installed with > [COLOR="#FF0000"]dpkg -l | grep Canon[/COLOR] .if you copy and paste that into a terminal; and copy and paste back what you get;

(I have reservations about the way the ubuntu guide is written for driver install: Canon always specify: common driver first, then the specific driver ............the Canon guide rather skips over that point ...........)

___________________________________

but if I go over some commands that I think you should have used; using Sivella as our guide .............

.....having installed printer driver............(assuming 32bit system): ......then .........

1)[COLOR="#008000"]**_ install in CUPS_**[/COLOR]  > [COLOR="#FF0000"]sudo /usr/sbin/lpadmin -p LBP1210 -m CNCUPSLBP12100CAPTK.ppd -v ccp://localhost:59787 -E[/COLOR]

......... you will see in the midst of the above command > ccp://localhost:[COLOR="#EE82EE"]59787[/COLOR] -E ..........I had understood in ubuntu one should use that (instead of 59687)

2) [COLOR="#008000"]**_register printer daemon in ccpd_**[/COLOR] > [COLOR="#FF0000"]sudo /usr/sbin/ccpdadmin -p LBP1210 -o /dev/usb/lp0[/COLOR]  .........assuming the LBP1210 is your sole printer and is connected by usb to your computer ............

3) [COLOR="#008000"]**_restart ccpd_**[/COLOR] > [COLOR="#FF0000"]sudo service ccpd start[/COLOR]

4) **_[COLOR="#008000"]check its operation[/COLOR]_** > [COLOR="#FF0000"]sudo service ccpd status[/COLOR] ..................Sivella spells out what you should see ......

......... the printer should now work ...............try it .............................

____________________

he has a through Part 2 where you automate the recognition of the printer: 

___________________-

having read this, can I suggest you delete the printer setup you have installed; and paste in the above commands [COLOR="#FF0000"]detailed in red[/COLOR] one by one as detailed above.........linux is for adults, so have a think........it is only settings in the printer settings; (the plan would then be to paste in the new commands I suggest above:

if agreeable to deleting the printer settings, the commands are:

1) **_[COLOR="#008000"]Delete the registered printer from the ccpd daemon setup file[/COLOR]_**. > [COLOR="#FF0000"]sudo /usr/sbin/lpadmin -x LBP1210[/COLOR]

2) [COLOR="#008000"]**_Delete the printer's spooler registration._**[/COLOR] > [COLOR="#FF0000"]sudo /usr/sbin/lpadmin -x LBP1210[/COLOR]

(I have quoted the above from Canon's instructions)

_____________

that should give a relatively clean slate to start again from .............assuming you are 32bit and the common and capt drivers are sitting fine ...........

---

### Post by Roland_Larsson on 2014-04-05
Thanks pdc for your detailed reply. I have two follow-up questions:
1 .........assuming the LBP1210 is your sole printer and is connected by usb to your computer ............
It is not, there is also an Epson printer on usb. The installation worked for that printer.
2 **_[COLOR=#008000]Delete the registered printer from the ccpd daemon setup file[/COLOR]_**.  	 		 			 			 				[COLOR=#FF0000]sudo /usr/sbin/lpadmin -x LBP1210[/COLOR] 			 		
 	
 
2) [COLOR=#008000]**_Delete the printer's spooler registration._**[/COLOR]  	 		 			 			 				[COLOR=#FF0000]sudo /usr/sbin/lpadmin -x LBP1210[/COLOR] 			 		
 	
 
These 2 commands seem identical to me. Should the be identical?

---

### Post by pdc on 2014-04-05
my apologies: in reply to your second question:

**_[COLOR="#008000"]Delete the registered printer from the ccpd daemon setup file[/COLOR]_**. the command is > [COLOR="#FF0000"]sudo /usr/sbin/ccpdadmin -x LBP1210[/COLOR]


for registering the printer; we too have two printers; our LBP is imagined as printer 2; so registered as /dev/usb/lp1 in the command so your command would be *sudo /usr/sbin/ccpdadmin -p LBP1210 -o /dev/usb/lp1*

....when using the LBP, I press the power button on no1 printer first; to confirm it as lp0; then the LBP so things start up right; there is a fix: I just need to do it [http://hintshop.ludvig.co.nz/show/persistent-names-usb-serial-devices/](http://hintshop.ludvig.co.nz/show/persistent-names-usb-serial-devices/)

---

### Post by Roland_Larsson on 2014-04-05
Thanks again. I'll try that.

---

