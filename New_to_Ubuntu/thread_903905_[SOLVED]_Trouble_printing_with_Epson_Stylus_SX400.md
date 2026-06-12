---
title: "[SOLVED] Trouble printing with Epson Stylus SX400"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by judytownshend on 2008-08-28
Hi there

I've recently purchased an Epson Stylus SX400 all-in-one printer, when I plug it into my laptop it is recognised but when I try to print, nothing happens. The document print stauts in the corner says that all of the documents I have tried to print are completed, but the printer hasn't done anything. Is there something I need to enable on my laptop? I'm currently using Ubuntu 7.10 Gutsy Gibbon, would it help if I upgraded to Hardy? Thanks in advance for your help.
:)

---

### Post by nicedude on 2008-08-28
You will need to go here [http://www.linuxfoundation.org/en/OpenPrinting](http://www.linuxfoundation.org/en/OpenPrinting) and see what linux support is available for your printer model.

I googled around and only see people asking the same question as you without any answers which is kinda a bad sign. Allot of printers are just big plastic bricks in Linux which is not any Linux developers fault but instead the manufacturers for not providing drivers or even driver code so someone else can do it. I would suggest you google around and see what you can find on using this printer model in Linux and if you find that it is not supported then be sure to send Epson a nice email about how satisfied you are :-)

---

### Post by alienexplorers on 2008-08-28
Try looking at these pages:
[http://avasys.jp/hp/page000001200/hpg000001149.htm]("http://avasys.jp/hp/page000001200/hpg000001149.htm")

[http://esupport.epson-europe.com/FileDetails.aspx?lng=de-DE&data=lkuCfcvA9cyNxXsYUo5VqPh04GTpE3SgPCpFvAUP1vIU003D&id=31411]("http://esupport.epson-europe.com/FileDetails.aspx?lng=de-DE&data=lkuCfcvA9cyNxXsYUo5VqPh04GTpE3SgPCpFvAUP1vIU003D&id=31411")

---

### Post by judytownshend on 2008-09-25
I visited this website: 
> Try looking at these pages:
[http://avasys.jp/hp/page000001200/hpg000001149.htm](http://avasys.jp/hp/page000001200/hpg000001149.htm)

And installed CUPS, SANE and the following package:

pipslite_1.2.0-0_i386.deb 

My printer is still not working! I'm not sure if I've missed something or if Epson has just been very nasty and created a printer that is totally incompatible with linux. Please help!

Thank you

Judy

---

### Post by josephitaly on 2008-09-30
> **judytownshend said:**
> I visited this website: 


And installed CUPS, SANE and the following package:

pipslite_1.2.0-0_i386.deb 

My printer is still not working! I'm not sure if I've missed something or if Epson has just been very nasty and created a printer that is totally incompatible with linux. Please help!

Thank you

Judy

i buyed this printer 2 years ago but after a few of problems i've done it.
I have Xubuntu 8.04 but it's the same with all ubuntu
i have followed these steps:
A) from console:[FONT="Arial Black"] apt-get install cups[/FONT]

B) download  pipslite_1.2.0-0_i386.deb

C)from console:[FONT="Arial Black"] sudo  dpkg -i pipslite_1.2.0-0_i386.deb [/FONT]
to install driver 

D) When it is installed,
from onsole:[FONT="Arial Black"]sudo pipslite-install[/FONT]
and follow instructions
then 

E) form console: [FONT="Arial Black"]sudo /etc/init.d/cupsys restart 
[/FONT]to restart cups

F) in the browser go to page  [FONT="Arial Black"]http://localhost:631/
[/FONT]
G) Select "Add Printer"
H )Enter a printer setting name in "Name", and select "Continue"
          (Other items are not mandatory)

I) In "Device", set "Epson Inkjet Printer #1 (Photo Image Print System Lite)", and select "Continue"

L) In "Make", set "Epson", and select "Continue"

I) In "Model", set "Photo Image Print System Lite (en)", and select "Continue"
     Example: With the PM-A950 printer, "Model" is displayed as follows.
             -----------------
 "EPSON PM-A950, Photo Image Print System Lite (en)"
             -----------------
 and thats all 
i hope you dominete your printer!

---

### Post by judytownshend on 2008-10-01
Hi

I've managed the first few steps, but when I ran *sudo pipslite-install* I got this message:

"PPD file need to be created for printer to be registered to CUPS. Please make sure that the printer is connected to your computer and have it turned on!"

My printer is indeed connected to my computer, I have tried turning it off and on again and have tried un-plugging it and re-plugging it in, but it is still bringing up the same message.

Any idea where I'm going wrong?

Thanks

Judy

---

### Post by josephitaly on 2008-10-01
> **judytownshend said:**
> Hi

I've managed the first few steps, but when I ran *sudo pipslite-install* I got this message:

"PPD file need to be created for printer to be registered to CUPS. Please make sure that the printer is connected to your computer and have it turned on!"

My printer is indeed connected to my computer, I have tried turning it off and on again and have tried un-plugging it and re-plugging it in, but it is still bringing up the same message.

Any idea where I'm going wrong?

Thanks

Judy

try to type sudo pipslite-install with the printer turned off and when the windows with the message appear turn on the printer 
let me know

---

### Post by judytownshend on 2008-10-01
> **josephitaly said:**
> try to type sudo pipslite-install with the printer turned off and when the windows with the message appear turn on the printer 
let me know

I've tried this and unfortunately it didn't work :(

---

### Post by judytownshend on 2008-10-02
I turned my computer on this morning and my printer is now working! Wooohoooo! Thanks for all your help :) 

Judy:guitar:

---

### Post by Jonky on 2008-12-28
I just wanna thank josephitaly for his amazing how-to.
I "simply" followed the steps he listed and got my brand new SX400 working!
OK, i had to go through some trial-and-error loops (for example, I forgot to restart cups after installing pipslite.. :oops:) but eventually I succeeded and was once again reassured by the helpfulness and power of the Ubuntu community!

---

### Post by gratefuljon on 2009-01-16
hi - thanks to josephitaly - used these directions to hook up an eeepc to an sx400 - (already had CUPS installed for a PDF printer) - when finally installing the printer in the CUPS browser window, i just had to put 'root' in the username, and my normal login password, and voila, perfect. Thanks josephitaly

---

### Post by completenovice on 2009-03-28
> **josephitaly said:**
> 

D) When it is installed,
from onsole:[FONT="Arial Black"]sudo pipslite-install[/FONT]
and follow instructions
then 


i got up to this step but when i try this:

user@user-desktop:~/Desktop$ sudo pipslite-install
/usr/lib/pipslite/pipslite-install: error while loading shared libraries: libltdl.so.3: cannot open shared object file: No such file or directory

also, i have not installed SANE dont know if that matters
and i coudltn find the version of pipslite mentioned, i had to get a new version - any help appreciated - 

thanks! :D

---

### Post by completenovice on 2009-03-28
never miind just got it working mysel

thanks joseph - that was a lot of help

:D

---

### Post by judytownshend on 2009-06-17
I've just upgraded to 9.04 and now my printer won't work again! I can scan things from it, but it won't print. Any suggestions? I've tried all of the above and none of it seems to work.

---

### Post by tazthecat on 2010-12-29
Update, after installing Ubuntu 10.10 the printer and the scanner! worked "out of the box" for me. scanner never worked before!

---

### Post by rowland on 2011-03-11
> **josephitaly said:**
> i buyed this printer 2 years ago but after a few of problems i've done it.
I have Xubuntu 8.04 but it's the same with all ubuntu
i have followed these steps:
A) from console:[FONT="Arial Black"] apt-get install cups[/FONT]

B) download  pipslite_1.2.0-0_i386.deb

C)from console:[FONT="Arial Black"] sudo  dpkg -i pipslite_1.2.0-0_i386.deb [/FONT]
to install driver 

D) When it is installed,
from onsole:[FONT="Arial Black"]sudo pipslite-install[/FONT]
and follow instructions
then 

E) form console: [FONT="Arial Black"]sudo /etc/init.d/cupsys restart 
[/FONT]to restart cups

F) in the browser go to page  [FONT="Arial Black"]http://localhost:631/
[/FONT]
G) Select "Add Printer"
H )Enter a printer setting name in "Name", and select "Continue"
          (Other items are not mandatory)

I) In "Device", set "Epson Inkjet Printer #1 (Photo Image Print System Lite)", and select "Continue"

L) In "Make", set "Epson", and select "Continue"

I) In "Model", set "Photo Image Print System Lite (en)", and select "Continue"
     Example: With the PM-A950 printer, "Model" is displayed as follows.
             -----------------
 "EPSON PM-A950, Photo Image Print System Lite (en)"
             -----------------
 and thats all 
i hope you dominete your printer!


i have downloaded the new pipslite_1.5.0-2_i386.deb
somehow i managed to enter to Downloads (cd /home/username/downloads)
and in terminal i wrote as you said: sudo  dpkg -i pipslite_1.2.0-0_i386.deb (but changed to pipslite_1.5.0-2_i386.deb, because thats the newer version i suppose)
the reply from terminal: 

user/user-desktop:~/Downloads$ sudo dpkg -i pipslite_1.5.0-2_i386.deb
Selecting previously deselected package pipslite.
(Reading database ... 238343 files and directories currently installed.)
Unpacking pipslite (from pipslite_1.5.0-2_i386.deb) ...
dpkg: dependency problems prevent configuration of pipslite:
 pipslite depends on libltdl3 (>= 1.5.2-2); however:
  Package libltdl3 is not installed.
dpkg: error processing pipslite (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pipslite

libltdl3 is not installed? checked synaptic libltdl7 is installed, also the -dev too

i tried another way:
sudo apt-get install pipslite
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pipslite is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  pipslite: Depends: libltdl3 (>= 1.5.2-2) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Should i use apt-get -f ?
Any help is apreciated.  
(for epson stylus sx 205)

---

### Post by gramoun_kal on 2011-05-27
> **tazthecat said:**
> Update, after installing Ubuntu 10.10 the printer and the scanner! worked "out of the box" for me. scanner never worked before!

Attention! Under Natty, printer and scanner work out of the box too.

---

