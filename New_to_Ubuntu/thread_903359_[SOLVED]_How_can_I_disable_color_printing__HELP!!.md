---
title: "[SOLVED] How can I disable color printing?  HELP!!"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by crjackson on 2008-08-28
Okay, I've searched Ubuntu, googlubuntu, and google.  Here's the problem.  I need to disable color printing due to kids wasting toner in my house while I'm not home.  It's getting expensive and teenagers just won't listen or care.

I can't turn off printing for them due to school work, but they don't need to print out tons of bright colors from the internet.

I went to my printer settings and can't find an option to set it default as color or b/w.  I really only need this for certain user's but I'll take whatever I can get.

There has to be a way, please help...

Thanks

---

### Post by gimfred on 2008-08-28
Okay mate, what printer do you have?

---

### Post by crjackson on 2008-08-28
> **gimfred said:**
> Okay mate, what printer do you have?

Dell 5100cn Color / Laser / Networked

---

### Post by gimfred on 2008-08-28
I've got a HP 5740 and running Kubuntu 8.04, but to change the settings, I went to:
KMenu, System Settings, Printers. 

Make sure you are in admistrator mode (Kubuntu has a administrator button down the bottom of the window)

under the Printer settings window that opens, I right clicked on the printer, selected Configure. In the pop up window I selected 'Printout Mode', 'Resolution, Quality, Ink Type, Media Type, <Controlled by Printout Mode>'

then I select the option in the box below. This may give you enough info to find the option, probably before I finish installing.

You should be able to setup two printers, one b+W, one colour and set the users in the options. 

Give me a little while and I'll install Gnome and see if I can get the options you are most likely to have. I'm presuming that you will be running straight Ubuntu? (8.04? I'm not installing an older version for this; sorry mate.)

---

### Post by crjackson on 2008-08-28
> **gimfred said:**
> I've got a HP 5740 and running Kubuntu 8.04, but to change the settings, I went to:
KMenu, System Settings, Printers. 

Make sure you are in admistrator mode (Kubuntu has a administrator button down the bottom of the window)

under the Printer settings window that opens, I right clicked on the printer, selected Configure. In the pop up window I selected 'Printout Mode', 'Resolution, Quality, Ink Type, Media Type, <Controlled by Printout Mode>'

then I select the option in the box below. This may give you enough info to find the option, probably before I finish installing.

You should be able to setup two printers, one b+W, one colour and set the users in the options. 

Give me a little while and I'll install Gnome and see if I can get the options you are most likely to have. I'm presuming that you will be running straight Ubuntu? (8.04? I'm not installing an older version for this; sorry mate.)

I've been all through the settings and can't find anything for changing color / B/W or Grey scale.

Yes, it's Ubuntu Hardy - Gnome (32-bit) - Print driver is "**Dell M5200 Foomatic/Postscript**"

I can change the option in the application "Open Office & Firefox" print settings, but it's a PER-PRINT change.  Once the print is done, it reverts back to the previous settings.  It's interesting to note that the Open Office Writer defaults to B/W, and must be changed for color.  Firefox defaults to full color and must be changed to B/W.

I want a global setting of B/W so that when a kid clicks the print button on the menu bars without making any changes (usually in Firefox) it will print B/W.

---

### Post by gimfred on 2008-08-28
I'm searching, I'm searching. Ubuntu is up to 72% download, so should only be another half hour or so. Dell's help is so painful to wade through! Have you tried setting it directly on the printer(y'know, via the printer menu. I can't see the option, but it should be there. )

---

### Post by dRock1286 on 2008-08-28
Go to System > Administration > Printing and then choose your printer from the list on the left.  Then go to the Print Options tab.  Printout mode is what you want...or at least that is how I change it on mine.

---

### Post by philinux on 2008-08-28
Yes under the print options tab for my epson is colour mode where I can select rgb or grayscale etc.

---

### Post by crjackson on 2008-08-28
> **gimfred said:**
> I'm searching, I'm searching. Ubuntu is up to 72% download, so should only be another half hour or so. Dell's help is so painful to wade through! Have you tried setting it directly on the printer(y'know, via the printer menu. I can't see the option, but it should be there. )

No, I haven't done that.  I need color for work and the wife needs color sometimes for school.  The kids use the networked printer from different (different from me/wife) computers.  I need a global setting per computer or per user.

If I could make permanent changes to Office Writer & Firefox that would also work.

---

### Post by crjackson on 2008-08-28
> **dRock1286 said:**
> Go to System > Administration > Printing and then choose your printer from the list on the left.  Then go to the Print Options tab.  Printout mode is what you want...or at least that is how I change it on mine.

Been there many times.  There is no option to change color settings from that applet.

---

### Post by crjackson on 2008-08-28
> **philinux said:**
> Yes under the print options tab for my epson is colour mode where I can select rgb or grayscale etc.

Does not exist here.  I used to have the option under Gutsy.

---

### Post by dRock1286 on 2008-08-28
Sorry then...my only suggestion to you now is to just pull the color cartridge out and put it in when you need it.  :D

---

### Post by dRock1286 on 2008-08-28
thanks for letting me  play though...

---

### Post by crjackson on 2008-08-28
Marking it solved.  I found an RPM driver.  I installed alien, converted it to a deb. Installed, logged off and then back on.  Option is there now.  I haven't tested it yet, but it is there.  Thanks for the help, it seems that the default driver for the M5200 is different under Hardy than it was under Gutsy.  I didn't need the to install this package under Gutsy.

---

### Post by gimfred on 2008-08-28
Thats weird, I've got that option too for my HP in 8.04... This is why I detest Gnome, it is so much harder to find the options you need! Seriously, go KDE bloke! Each to their own though. 

Well, if they have disabled that option for Dell, one can only conclude that the setting must be in a config file. Will the printer work with cups? If I remember in Ubuntu wiki someone had written that the Dell 5200 would only work through cups. I've never used foomatic. Heh, its probably a frontend to cups :s oops no my system is a foomatic too apparently.

---

### Post by gimfred on 2008-08-28
aww, we are only just getting to the fun stuff!

I think if you were to type at the command line, foomatic-configure -o PrintoutMode High.grayscale it might change it to grayscale printing. I got that from [here]("https://lists.linux-foundation.org/pipermail/printing-foomatic/2002/001212.html"). Note I haven't tried it as mine works via gui.

Well, I guess alien is the way to go. Congratulations. Maybe this will help someone else.

---

### Post by crjackson on 2008-08-28
Okay, I tested it and it does work as needed.  Thanks for your input.

---

### Post by crjackson on 2008-08-28
Here's the deb driver if anyone else needs it.

---

### Post by acoliver on 2008-10-25
There is a possibility that it is under the incredibly un-user friendly title of  "Print Color as Grey"

---

