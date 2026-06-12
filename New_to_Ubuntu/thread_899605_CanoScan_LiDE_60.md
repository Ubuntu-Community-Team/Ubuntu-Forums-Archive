---
title: "CanoScan LiDE 60"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by Alan F on 2008-08-24
I have a CanoScan LiDE 60 USB flat bed scanner that I am try to get to work in Ubuntu 8.04. It works fine in XP.

Xsane is installed and on opening it (applications/graphics/xsane image scanner) the scanner is detected and is noted as LiDE 60 at the top of the Xsane windows

However when I attempt either a 'Aquire Preview' or 'Scan' the scan operates for a fraction of a second then an error message appears "Failed to start scanner: Document feeder jammed"

This is strange as there is no document feeder and the scanner is perfectly functional in XP. The same message appears if I try to aquire the image through Gimp.

This newbie would appreciate any help to resolve this.

---

### Post by phidia on 2008-08-24
Make sure you have the correct backend installed per the [sane site]("http://www.sane-project.org/cgi-bin/driver.pl?manu=canon&model=canoscan+lide60&bus=any&v=&p=") and your scanner. Plus take a look at the ubuntu wiki on your scanner [here]("https://wiki.ubuntu.com/HardwareSupportComponentsScannersCanon") There's a guide there for the lide 60 even if it is for a older version of ubuntu.

---

### Post by Alan F on 2008-08-25
Thanks for your interest.

I appear to have the correct Genesys backend loaded as reported in Xsane/file/info.

Looking at the wiki 'mini how to' article

sane-find-scanner command was OK 
dll.conf modified as shown
45-libsane.rules did not exist but I created it and added the lines as shown

system restarted, but scanner still would not scan. 

Any more advice?

---

### Post by phidia on 2008-08-25
Try a scan from the terminal/commandline > scanimage  >image.pnm
If that doesn't work it could at least provide more error reporting.

---

### Post by Alan F on 2008-08-25
Giving that command in terminal produced what appeared to be a correct scan but wwhere did the output go to? There was no information or errors generated in terminal.

However when I tried it in Xscan again it worked!! Not sure why but you are a star! Thanks.

OK, now found where file went.

---

### Post by Crafty Kisses on 2008-08-25
For scanners you can look through this list > [http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

[http://www.linuxfoundation.org/en/OpenPrinting/Database/SuggestedPrinters](http://www.linuxfoundation.org/en/OpenPrinting/Database/SuggestedPrinters)
[http://www.linuxfoundation.org/en/OpenPrinting/Database/LinuxSupportByPrinterVendors](http://www.linuxfoundation.org/en/OpenPrinting/Database/LinuxSupportByPrinterVendors)

---

### Post by Alan F on 2008-08-26
Update on situation.

As stated above system worked OK, but after a few scans the same problem intermittently re-appeared.

Tried with shorter USB/scanner cable with ferrites which seems to have cleared up the problem. Previous cable was about 2m long without ferrites but has been working OK with Win XP for about a year.

Currently I have std Xsane, Xsane-common, xsane-doc and libsane installed and a USB/scanner cable 1.5m long with ferrites. All working OK. (Lets hope it lasts!)

---

### Post by cecilx22 on 2008-11-10
I've emailed the Canoscan support team, and got the attached reply.  Basically, if we all email them, it'll increase the chance of getting something done!  Lets do it!

[Contact link here]("https://www.usa.canon.com/consumer/controller?act=SupportMailerAct&fcategoryid=235&modelid=9374")


> Dear Mr. Smith:

Thank you for contacting Canon product support.  We value you as a Canon
customer and appreciate the opportunity to assist you with your comments
about Linux drivers for our products.

I completely sympathize with you because I am a Linux user myself.  What
I have done is forwarded your comments to Canon USA through our Customer
Feedback process. This process allows us to capture important feedback
from our valued customers. As we constantly strive to improve our
products and services, your comments are vital to our continued success.
If we get enough requests, there is a chance that this will be
developed.

Please let us know if we can be of any further assistance with your
CanoScan LiDE 80.

Sincerely,

Devin
Technical Support Representative

Special Note: Certain issues are very difficult to resolve via email.
If your question remains unanswered after you have received this email,
you may call our special toll-free number for email customers with
unresolved issues and speak to a technician* by dialing 1-866-261-9362,
Monday - Friday 10:00 a.m. - 10:00 p.m. (excluding holidays).

If you prefer to continue to communicate via email, reply to this
message and we will respond as quickly as possible.

*Telephone support for products no longer covered under the
manufacturer's warranty may require a $9.99 fee for support.



Original Message Follows:
-------------------------

Email Support Form Message
Product Type: CanoScan LiDE 80
Product Model:
IslandData Session:
Product Serial Number:
Date of Purchase:
First Name: Harrison
Last Name: Smith
Address:
City:
State:
Zip: 43026
Phone Number:
Email Address: [email]smith.3738@osu.edu[/email]
EMAIL_ADDRESS_CONFIRM: [email]smith.3738@osu.edu[/email]
q01:
q02:
q04:
INQUIRY: I'm writing to ask you to please publish technical information
regarding your scanners to that the open source community can develop
driver support, particularly for Linux.
Even better, provide driver support yourselves.  I understand, however,
that that is not a very cost-effective activity, so I understand if that
is not viable.  It should not cost you anything, however, to provide a
basic programmers API to the device.
Thank you for your consideration!

---

### Post by SteveWin1 on 2009-04-24
I thought you were crazy about the cable being the problem.  I was having this exact same problem.  I had my ScanoScan LIDE 60 connected through a USB hub and was getting the document feeder jammed message every time I tried to scan anything.  I ran out of things to try, so I tried connecting the cable directly from my scanner to my computer's USB port.  It works flawlessly now!  

You're my hero!  Now I don't have to switch back to Vista just to scan some documents.  I wonder why Vista can use it through the hub, but Ubuntu can't.  Anyway...Thanks!

---

