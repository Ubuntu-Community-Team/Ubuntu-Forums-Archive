---
title: "[SOLVED] Version 8.10 and Brother HL-2140 printer"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by bennachie on 2008-11-20
This printer is auto-detected by 8.10, which recommends that the driver for the HL-2170W be used. That aligns with the advice on the Brother web-site, which specifies driver version 2.0.1-1 for printers in the 2040-2050-2060 series, and version 2.0.2-1 for printers in the 2140-2150-2170 series.

However, I was unable to get the printer to work with the HL-2170W driver, either on my laptop or my desktop computer. Everything seemed to proceed normally until the very last moment, but no actual printing took place (although the job was recorded as having been completed). 

I therefore returned to an option previously recommended in this forum for use with Ubuntu 8.04, and selected the HL-2060 driver, which presumably corresponds to Brother version 2.0.1-1. That cured the problem, and the printer now seems to function normally at all resolutions.

YMMV, but I thought it might be worth posting the solution in case somebody else experiences the same problem.

---

### Post by NewJack on 2008-11-21
If you check [http://openprinting.org](http://openprinting.org) (make sure to bookmark), you will find this:

[http://openprinting.org/show_printer.cgi?recnum=Brother-HL-2140](http://openprinting.org/show_printer.cgi?recnum=Brother-HL-2140)

It states that your printer works (Mostly) and that the [FONT=ms sans serif, helvetica]**Brother 2140LPR Driver** is the one that is recommended.  There is a link to the driver on your printer's page.

Good luck, hope this helped!


[/FONT]

---

### Post by bennachie on 2008-11-21
Thanks, NewJack, but I think we're going round in circles. I have already got the printer working (with the help of the site that you - and others - have recommended), and was simply warning anyone who found themselves in my situation not to rely on the default driver offered by Ubuntu 8.10. 

I will mark this as solved (as I should have done in the first place) to avoid any further messing around.

---

### Post by SeePU on 2008-11-21
Hello, OP.  Are you saying it would not work in Intrepid using the LPR driver for that specific printer?  

It should work using the Brother 2140LPR Driver NewJack pointed out.

I was curious because I am looking for a cheap laser printer that's highly portable and this Brother printer was on the list.  I don't want one that is an ordeal to set up, though.  It also has to work in Intrepid because I'll be using that.

The only cheap lasers I've found are:  Brother HL-2140, HP P1005 and Samsung ML-2510 (all $60 new).

However, the Brother has the best specs but all need some tweaking (i.e. downloading of drivers) to set up.  

I found these links for the Brother HL-2140:

[http://solutions.brother.com/linux/en_us/download_prn.html#HL-2140](http://solutions.brother.com/linux/en_us/download_prn.html#HL-2140)

[http://solutions.brother.com/linux/en_us/instruction_prn1a.html](http://solutions.brother.com/linux/en_us/instruction_prn1a.html)

[http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install5.html](http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install5.html)

---

### Post by bennachie on 2008-11-21
The printer doesn't work properly if you just let Intrepid do its thing (the automatic selection mechanism which comes into effect when Intrepid detects the printer defaults to a driver that is different from - being a slightly later version than - the one recommended on the linux printing website).

However, there is no real hassle - you just have to go into the printer setup dialogue (under "system") and choose the HN-2060 driver rather than the HN-2170W driver selected by Intrepid. 

The printer then works very well indeed under Intrepid (and, for what it is worth, under several other Linux distros that I have tried, including the default Xandros on the eeePC). In general terms, I can certainly recommend it as a robust, low-cost mono laser, and now have two of them around the place.

---

### Post by SeePU on 2008-11-21
Did you download and install the LPR and CUPS wrapper drivers for that printer (choosing the HL-2140 drivers)?  Then chose a HL-2060 driver?  I'm confused what worked.

I found the entry on the OpenPrinting webpage for the HL-2140 to be somewhat confusing.

It sounded like the HL-2060 driver only allowed 600dpi resolution and that trying 1200dpi gave a blank page.  

It seems like the issue will eventually get solved unless the true driver works but requires tweaking.

I want a light-weight portable laser that's cheap but doesn't require much of a hassle to set up in Intrepid.  

I'm comparing the Brother to a Samsung ML-2510 which apparently has open source drivers.  But, the Brother looks more compact and lighter.

---

### Post by kraymore on 2008-12-04
i don't believe the HL-2140 will print, at least, as of yet at 1200dpi.  

600 works ok though.  

i use the 2060 driver.  i will try not going to the Brother website and using their LPR and Cups driver.  I seem to remember that when i used them, I still had to use the 2060 driver to get it work. seeing as that is included, i dont want to go through the redundancy.

---

### Post by freemath on 2008-12-28
I confirm the followings:

1. Ubuntu Intrepid automatically chooses HL-2170W driver when the printer is first plugged in. This is a wrong choice and the printer gives no output.

2. Choosing HL-2060 driver works fine. For this driver the highest resolution is given by "High Quality". This seems to give 600dpi resolution.

3. The drivers provided by Brother on its website, HL2140, also works. I'm using 64bit Intrepid. There is an option for HQ1200dpi resolution, but I could only print text, not image with it. I could not be certain whether I really got 1200dpi.

I bought the printer yesterday, my initial impression is that it is an excellent printer, especially for the quality of text.

---

### Post by barney_1 on 2009-01-29
I purchased this printer yesterday (HL-2140).  I am running Ubuntu 8.10 Intrepid Ibex.  I can also confirm:

[LIST=1]
[*]Initially recognized as the HL-2070W and will not print with that driver.  Changing driver to HL-2060 does allow the printer to work.
[*]Installing drivers from Brother opens up more printing options such as HQ1200 printing quality as well as paper type (thin, thick, transparency, envelope, etc).
[/LIST]

I followed these instructions to install the driver from Brother:
[http://solutions.brother.com/linux/en_us/instruction_prn1a.html](http://solutions.brother.com/linux/en_us/instruction_prn1a.html)

I do believe that with these drivers you can print at the HQ1200 setting but I don't have a way to tell for sure.  Looking at the difference between 600dpi and HQ1200 the latter looks much much smoother.

---

### Post by pwnst*r on 2009-03-28
> **bennachie said:**
> This printer is auto-detected by 8.10, which recommends that the driver for the HL-2170W be used. That aligns with the advice on the Brother web-site, which specifies driver version 2.0.1-1 for printers in the 2040-2050-2060 series, and version 2.0.2-1 for printers in the 2140-2150-2170 series.

However, I was unable to get the printer to work with the HL-2170W driver, either on my laptop or my desktop computer. Everything seemed to proceed normally until the very last moment, but no actual printing took place (although the job was recorded as having been completed). 

I therefore returned to an option previously recommended in this forum for use with Ubuntu 8.04, and selected the HL-2060 driver, which presumably corresponds to Brother version 2.0.1-1. That cured the problem, and the printer now seems to function normally at all resolutions.

YMMV, but I thought it might be worth posting the solution in case somebody else experiences the same problem.

This was the case for me under Jaunty Alpha 6 also.  thx!

---

### Post by elphaba on 2009-04-01
I'm able to get the HL-2170W working fine with the driver that comes with Intrepid 8.10 (at least that came on my system76 laptop).
 I have been successful for printing when I connect printer hardwired to my router via ethernet cable. 
 What I learned - DON'T use the cups printer web admin interface. Even when I used correct URI, it didn't work. (I'm referring to [http://localhost:631/](http://localhost:631/))
  When I used correct URI when adding new printer via the System Admin pull down menu, Printing option, NEW, worked great.
 URI that works with ethernet hardwired to router and print command entered from my laptop connected via wireless interface (I.E. without ethernet cable):
  ipp://localhost/ipp/
  
  Next problem to solve, how to disconnect my printer from router and still have printing work. I think it is supposed to but haven't figured out how to invoke wireless setup command for printer (so I can enter passphrase, etc). I've just tried wifi-radar and don't think it will work for printers but haven't totally given up yet.

---

### Post by jmax on 2009-04-28
I had the same problem ... a brother 2140 that DOESNT work with the brother 2140 driver ... put in the hl 2160 driver ... works like a charm.

---

### Post by charlesfmoreira on 2009-08-04
Thanks for the tip on the HL-2060 driver.

I had exactly the same problem with the Brother HL-2140 with Ubuntu 9.04. The debian driver provided on Brother's website failed to install. I can give you the details later.

Ubunto 9.04 detected the printer as a 2170W and while it all went well as far as installation and the print process go, there was no actual printout.

I'll try the HL-2060 driver and see how it works.

Thanks once again.

---

### Post by Theferg on 2009-08-06
Hi Guys, 

I am looking to buy a cheaper print scan (brother) is there a list of compatiblity for this one?
**BROTHER DCP-145C MultiFunction 3 in 1**

many thanks 

Fergus

---

### Post by Theferg on 2009-08-06
> **Theferg said:**
> Hi Guys, 

I am looking to buy a cheaper print scan (brother) is there a list of compatiblity for this one?
**BROTHER DCP-145C MultiFunction 3 in 1**

many thanks 

Fergus


ps if this one is OK I will go and purchase it, does anyone recommded good cheap online stores?

---

### Post by NewJack on 2009-10-03
I just installed this printer today.  Tried following the instructions on Open Printing and on Brother's site, no go.  All that happened was endless feeding of paper with no printing happening.  

I then followed the advice of using the HL-2060 driver and it prints fine, but I can only print up to 600 dpi (high quality).  

If anyone can break it down on how to install the correct drivers in order to be able to print at 1200 dpi, it would be much appreciated.

---

### Post by tubbygweilo on 2009-10-13
Am using HL-2140 with 9.04 plus Brother HL-2060 driver and it works. I have set the printing to high quality and to be honest on a printed page of text I can not seem to tell if it is 600 or 1200 dots per inch, it looks to me good quality whatever the setting.

Thanks for the advice.

---

