---
title: "Epson Stylus TX100 Printer Drivers"
date: 2012-12-01
forum: New to Ubuntu
---

### Post by zee64 on 2012-12-01
Hi, overall I'm enjoying my Brave New Ubuntu experience, and have found most things easy to grasp (probably thanx to having to troubleshoot Windows crap for too many years - lol!), BUT:

I'm having trouble getting my Epson Stylus TX100 drivers to install, despite reading numerous other Epson-related forum posts. 

In a nutshell then: I'm able to print, but cannot get more than a paper choice in the printer preferences dialog. This means that not only am I unable to select the "Print with black ink only" option, but cannot see what my ink levels are, adjust the print head, etc etc.

I've downloaded both these files: 
pips-snx100-ubuntu8.04-3.5.0-CG.tgz
pips-common-3.3.0.tar.gz
from this website: [http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)

When extracted, I ended up with this file, which I have NO idea how to open or install (one of the forums mentioned gdeb, but no luck):

pips-snx100-ubuntu8.04-3.5.0-CG.install

I'm not even sure if these are the right files, as the most recent version listed on the website was Ubuntu 11 point whatever...

Really hoping someone can help me resolve this, as I'm on a limited income, and with ink costing more than your average Faberge egg, this is kind of a deal-breaker for me!

P.S: Please make any answers as idiot-proof as possible (i.e: plz don't leave out any pertinent info that may seem "obvious" to you - lol!)

Thanks in advance! :-)

---

### Post by Zill on 2012-12-02
> **zee64 said:**
> I'm having trouble getting my Epson Stylus TX100 drivers to install, despite reading numerous other Epson-related forum posts...
This might sound like a daft question but have you tried printing *without* installing any drivers manually?  The reason I ask is that Linux systems generally have drivers pre-installed or will find and install them automatically (as long as you are connected to the internet!).  There is often no need to search the web for drivers that then must be installed manually.
> **zee64 said:**
> ...Really hoping someone can help me resolve this, as I'm on a limited income, and with ink costing more than your average Faberge egg, this is kind of a deal-breaker for me!
If you have little use for a colour printer then I strongly recommend using a laser printer for your B&W printing.  These cost slightly more then an inkjet to buy but the running costs per page are far lower.  IMHO they are also far less hassle - never needing cleaning or getting blocked jets etc.

---

### Post by zee64 on 2012-12-02
Thanx for your reply Zill, and imho there's no such thing as a daft question (my post proves that - lol!). 

I have tried printing without the drivers (as I've had no luck installing them thus far). The printer works okay, but the problem is I only have preferences for paper size to choose from. I do print colour as well as black & white, but as I've said I need the "Print black ink only" option in order to prevent using all 4 inks to just print black.


Buying a new printer isn't an option at the mo either, cos I'm "in between jobs" at present (read: unemployed bum! lol).

So, to clarify my question: how do I install what I've downloaded (see original post), or is there some other program that will allow me to access the preferences I need?

Cheers,
Zee :-)

---

### Post by Zill on 2012-12-03
zee64:  As I gave up on inkjets years ago I can't really help you with this driver.  Hopefully, someone who uses the TX100 should soon be able to help with this particular problem.

If you do have a requirement for both colour *and* B&W printing then it is quite possible to connect multiple printers to your PC.  You could then simply select your inkjet for colour or the laser for B&W.

I do appreciate that "times are hard" (I am retired and living off a tiny pension!) but buying a cheap laser printer really would save you a fortune in running costs. ;-)

I bought a Brother HL-2130 recently and this just works straight out of the box.  Just plug in the USB and it installs itself automatically.  No manual driver downloads or installation required. :-)

This printer is still available in the UK for under £60:
[LIST]
[*][BROTHER HL2130 Compact Monochrome Laser Printer]("http://www.currys.co.uk/gbuk/brother-hl2130-compact-monochrome-laser-printer-13212956-pdt.html?srcid=867&cmpid=comp~Google~Computing+Accessories~13212956&istCompanyId=bec25c7e-cbcd-460d-81d5-a25372d2e3d7&istItemId=qtptatmm&istBid=t")
[/LIST]

---

### Post by pdc on 2012-12-03
Hi zee64

If I offer you the instructions that Epson offer for installing your printer, using the driver they offer?

[COLOR="Blue"]Epspn advice in blue[/COLOR]

[COLOR="Red"]Epson copy and paste the commands in red into a terminal (hit the ENTER key after each command is pasted...)
[/COLOR]
> [COLOR="Blue"]**Do not connect the printer yet.**[/COLOR]
   
[COLOR="Blue"]**Connect the printer after installing the software.**[/COLOR] 


> [COLOR="Red"]tar -zxvf pips-snx100-ubuntu8.04-3.5.0-CG.tgz[/COLOR]

> [COLOR="Red"]sudo ./pips-snx100-ubuntu8.04-3.5.0-CG.install[/COLOR]

> [COLOR="Blue"]When the files finish copying, the installer starts the communication setting tool (ekpd-tool) for connecting with the printer.
This is necessary for connecting with the USB printer[/COLOR]. 

.........if we see if that installs the Epson driver for you, and see what else you need after that?

---

### Post by zee64 on 2012-12-03
Hey thanx heaps for your help pdc. Followed your instructions and those drivers DID axually install - unfortunately, I still only have the 'Paper option' in the print dialog. Perhaps I need more recent drivers, so the quest goes on...and on..! lol

One extra question for you, though: I can't copy and paste command lines into the Terminal (using Ctrl C, Ctrl V). What am I doing wrong?

Cheers,
Zee :-)

---

### Post by pdc on 2012-12-03
well done to get the drivers installed........

the terminal uses Shift+Control+V

.....see thumbnail below

_______________________________________________

for ink levels...........is this of any use?

[http://forums.linuxmint.com/viewtopic.php?f=51&t=27806](http://forums.linuxmint.com/viewtopic.php?f=51&t=27806)

___________________________________________________________________________________

if you want to pursue ink levels etc

[http://www.turboprint.info/printers.html](http://www.turboprint.info/printers.html)

turboprint has supported linux for many years

......... there is a free to try version .........and if you like it ......a full version

your TX100 is not mentioned as supported .........whereas the TX110 and thereafter are all mentioned........ you could try it out ......it installs as a separate driver ...we used it for Canon printers for several years......it was excellent ........Canon now provide good linux drivers............

---

### Post by zee64 on 2012-12-03
D'oh! My flatmate just solved my Copy/Paste question: Cntrl P, not V! Now THAT'S gonna make life easier too! :-)

---

### Post by zee64 on 2012-12-03
Wow - that was fast! Cheers again, but I'm more concerned about getting the printer to only use black ink when I need it to, so the hunt goes on. 

Often it's a matter of lateral thinking when knowing what to search for, too. However, my family motto IS "Perseverens Vincit" (not kidding), which translates roughly as: "Perseverence will out"...:-)

---

### Post by pdc on 2012-12-03
.......I think Control+P pastes in the previous command issued in the terminal ...........

.......not what you are pasting in from .....a web browser ........

I always use the mouse.........go top line ....... Edit .....down to copy or paste .......I can't use 3 fingers at the same time .........

.......to find out the Keyboard Shortcuts ......

........go to EDIT ......... 5 down...Keyboard Shortcuts........

.......as in thumbnail.............

---

