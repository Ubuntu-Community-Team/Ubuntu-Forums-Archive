---
title: "Canon MX890 printer, wireless"
date: 2013-12-28
forum: New to Ubuntu
---

### Post by riverguy99 on 2013-12-28
Our office uses a Canon MX890 multi-function printer.  It is connected directly to one Windoze computer and available to other computers through our office wireless network. I would like to know if there is a standard procedure to get my Ubuntu 12.04 laptop to access this printer. The laptop is connected through this same wifi network.  I have the original install CD. I need only the "print" function on the Ubuntu laptop, so I would not need the Canon "dashboard" to access all its other functions.

---

### Post by donaldt on 2013-12-28
Why don't you check out turboprint.  This is a german company that makes a very good software package.  You can try it free.  If you buy, it is ~$30.00 US.  I've been using it on my MX512 and earlier on a MX860 wireless for 3 years.  It works great.  There are not a lot of other options to run on Ubuntu.  

DonaldT

---

### Post by riverguy99 on 2013-12-28
Thanx for the tip!  I checked out their Web site and there is no mention of being able to set up the printer as wifi.  I have no clue how these things work, but as long as the drivers are installed on the print server, do they also need to be installed on wifi-access computers?  Like can't the Ubuntu wifi laptop just talk to the print server (the desktop that's directly connected to the printer) and get it to apply the drivers?

I don't understand everything I know about this stuff . . .  :)

---

### Post by sammiev on 2013-12-28
This is what I used to setup my [wireless]("http://ubuntuforums.org/showthread.php?t=1676121") printer. Took me about 1 min.

---

### Post by riverguy99 on 2013-12-28
Thank you!  I'll give it a go!

---

### Post by kurt18947 on 2013-12-28
I'm not familiar with your Canon printer.  Can you use the USB connection and one network connection at the same time?  If so, I find it pretty easy to configure wireless connections in Ubuntu.  I use Gnome-shell but find the print app wanting, I think Unity uses the same wanting print.  I download 'system-config-printer' (I think).  That is the printer app used in Xubuntu, Lubuntu and I think Mint.  I find it much more informative and flexible.  There are typically a few wireless connection options available.  I've had the best luck assigning a static I.P. address to the printer then using the following device URI:  
socket://xxx.xxx.xxx.xxx:9100  where x=the assigned I.P. address.  There may be other better choices but this has worked reliably for me.

---

### Post by riverguy99 on 2014-01-01
[FONT=arial]Thanks everybody for your suggestions! I finally got brave enough to give it a go and decided just for laughs to try from "Settings."  I clicked on *SETTINGS, PRINTERS, ADD PRINTER, FIND NETWORK PRINTER*, and then after about 30 seconds of processing, I got [I]WOULD YOU LIKE TO PRINT A TEST PAGE? 

[/I]I printed the page!  It worked!!  I am blown away!!![/FONT] All I can say is that Ubuntu has come a long, long way in the last few years, and I'm one happy camper!

---

### Post by sammiev on 2014-01-01
> **riverguy99 said:**
> [FONT=arial]Thanks everybody for your suggestions! I finally got brave enough to give it a go and decided just for laughs to try from "Settings."  I clicked on *SETTINGS, PRINTERS, ADD PRINTER, FIND NETWORK PRINTER*, and then after about 30 seconds of processing, I got [I]WOULD YOU LIKE TO PRINT A TEST PAGE? 

[/I]I printed the page!  It worked!!  I am blown away!!![/FONT] All I can say is that Ubuntu has come a long, long way in the last few years, and I'm one happy camper!

LOL I'm hurt. It took me 1min.

---

### Post by Jonathan Precise on 2014-01-01
Please mark as solved by going to thread tools.

---

