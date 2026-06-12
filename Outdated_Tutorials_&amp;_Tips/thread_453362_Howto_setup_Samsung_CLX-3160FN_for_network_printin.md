---
title: "Howto setup Samsung CLX-3160FN for network printing"
date: 2007-05-24
forum: Outdated Tutorials &amp; Tips
---

### Post by seetho on 2007-05-24
Hi all,

I bought myself a Samsung CLX-3160FN – a colour laser MFP.  I chose this printer because the brochure said that it supported Linux and the Samsung sales guy said that it does indeed support Linux – plus the price was quite reasonable for colour laser MFP.

Unfortunately when I tried setting it up I was deeply disappointed as the driver on the CD and the latest driver I downloaded from Samsung's web-site does not work.  I did manage to print the test page but nothing else would print.  It would be just garbage.  I looked around the Ubuntu forum and found several threads describing how to install the Grand Unified Driver, but they were all meant for mono models and mostly using direct connection via USB.  I needed to install my printer on the network.  Searching wider I found some threads on other forums describing this model as unusable under Linux and that it would only work on Windows :(.

Not one to give up so easily I spent the last 2 days searching the web for any information and trying different things... and finally I managed to get it to work today – both on Feisty and on Dapper (should work on Edgy I suppose).  It was actually quite simple.  So I hope the info here will help save you some time (and hair).

(I did not really figure out how to do all this myself.  It was just bits and pieces of information gathered from many sources on the net and just trying everything until something worked.  I'm not going list the link here as I don't really remember all of them.)

So here goes:

First setup your printer with a static ip address, e.g.  mine is 192.168.1.99.  I plugged mine into a 3COM wireless AP.  The PCs accessing the printer are all connected by wireless.

Download the latest driver from [www.samsungprinters.com](www.samsungprinters.com).  The latest version is 20070424152428968_UnifiedLinuxDriver.tar.gz.  Unpack into your home directory or wherever convenient.  (The instructions on the samsung web-site says you need to be root to do this but I found that it is unnecesssary).

Open up your favourite browser (Firefox for me) and type into the address bar: [http://localhost:631](http://localhost:631) – this will take you to the web admin page of your CUPS.

Click on the Administration tab.  On Feisty I see immediately my printer already detected on the network.  On Dapper the printer is not detected.  So on Feisty just click on the button to Add your detected printer, and on Dapper just click on Add Printer button.

Feisty: On my system it is detected as CLX-3160FN_Series_192.168.1.99; Dapper: Just type in the name of the printer (I just use CLX-3160FN).  Location and Description fields are optional.  Click on Continue.

Next select the device. Feisty your can select my printer is already listed in the device list as 'CLX Series 192.168.1.99 (CLX-3160 Series)'.  I just select this.  On Dapper I just select 'Internet Printing Protocol (ipp)'.  Click Continue.

Next enter URI.  On Feisty this step was not necessary since it is already detected.  On Dapper just enter the ip adress of your printer.  (I entered 192.168.1.99).  Click Continue.

Next is driver installation.  Don't select the printer model listed, instead use the second option (Provide a PPD File).  Click on browse and look for ~/cdroot/Linux/noarch/at_opt/share/ppd/CLX-3160splc.ppd.  Click on Modify Printer.  An authentication dialog box will appear.  Key in your regular username and password here.  For Dapper this does not work – you have to goto System->Administration->User and Groups and add 'cupsys' user to the 'shadow' group.

Now it says your printer has been successfully modified.  Almost done.  Now click on the Printers tab.  You will see your printer, but there's a warning message saying 'rastertosamsungsplc is not found in /usr/lib/cups/filter/' or something like that.  This file is found in: ~/cdroot/Linux/i386/at_root/usr/lib/cups/filter/.  There are actually 4 files in this directory: pscms, rastertosamsungpcl, rastertosamsungspl, rastertosamsungsplc.  I copied all them (for good measure) to /usr/lib/cups/filter/.  You must use the sudo command for this.

Now you have to do something very windows – restart your system!

After restarting you can then print!  My printout seems to be rather dark and the cups printer option settings are rather limited so I'm now trying to figure out how fine tune it more.

At least it is printing now.  Enjoy!

---

### Post by gabri75 on 2007-08-31
HI i am a new user [COLOR="Red"]to[/COLOR] Linux

Can I get sum help please , how  to add cupsys user for shadow group
i did not find a shadow in the group list

witch command do i need to use in sudo

thanks

---

### Post by filiep on 2007-09-03
Hi,

the Unified Linux Driver from Samsung works, but the print quality is not great.
Beter is to follow the instructions on [http://foo2qpdl.rkkda.com/](http://foo2qpdl.rkkda.com/) 
Print quality is much, much beter.

F.

---

### Post by seetho on 2007-09-04
> **filiep said:**
> Hi,

the Unified Linux Driver from Samsung works, but the print quality is not great.
Beter is to follow the instructions on [http://foo2qpdl.rkkda.com/](http://foo2qpdl.rkkda.com/) 
Print quality is much, much beter.

F.

You are right.  I have a Canon IP4000 and this samsung CLX.  The print quality on both of these are very poor indeed.

I still need to start up my Windows machine just to do high quality printing.

I'll give the driver you mentioned a try when I have the time (away from work and family).

I wonder if Epson color printers are any better at print quality, since they do have native linux drivers?

---

### Post by seetho on 2007-09-04
> **gabri75 said:**
> HI i am a new user [COLOR="Red"]to[/COLOR] Linux

Can I get sum help please , how  to add cupsys user for shadow group
i did not find a shadow in the group list

witch command do i need to use in sudo

thanks

Perhaps you can post this question in the Absolute Beginner forum.  I'm sure someone will be willing to help you there.

---

### Post by rs2bugzilla on 2007-10-29
Hello seetho,

Your discribtion helped me well. Thanks a lot.
I installed it right the way You told us, but took the files from the CD.
Fine.
Then I installed the Samsung on an Gentoo of my wife.
Fine.
Then I installed it on my Gentoo Thinkpad with the above mentioned drivers.
QUALITY: what a mess.
The quality was - like filiep mentioned - poor.
Well, I removed the "drivers" (thank good midnight commander was helping) and took the same drivers from the original CD. They were dated form Jun 26, 2006 (yes LAST year !!!).
The print result was perfect.

So take the OLD drivers (*.ppd and pscms, rastertosamsungpcl, rastertosamsungspl, rastertosamsungsplc)

Greets

---

### Post by seetho on 2007-10-30
If I read your post correct, you are saying the old driver files work better than the latest ones?

Actually I download and installed the latest drivers from Samsung again since I upgraded to Gutsy, but the print quality remains poor.  I must try your files.

---

### Post by seetho on 2007-10-30
Well I dug out my old printer driver CD.  It was marked version 1.14.  The files were dated 29th June 2006.  3 days later than your files???

The print results were exactly the same.  It's not nearly as good as the print quality when I do the same printing from WinXP.  The colours are too dark and tend to be yellowish.

At least it worked for you!

---

### Post by pe3no on 2008-01-10
> **rs2bugzilla said:**
> [...]
Your discribtion helped me well.
 [...]

Hello, rs2bugzilla

I'm going to buy Samsung CLX-3160FN  :)
Could you, please, tell me how this "All-in-one" works at Linuks?

1. Are you able to managed good quality of printing? (colour and B/W)
2. Does scanning work ok under Linuks? (flatbed and ADF)

Big thanks in advance and
BestRegards~~Piotrek~~pe3no.

---

