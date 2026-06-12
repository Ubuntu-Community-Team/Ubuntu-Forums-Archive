---
title: "bash script to print"
date: 2012-09-20
forum: Programming Talk
---

### Post by conradin on 2012-09-20
Hi Everyone!
I want to print from the command line to a network printer. Ive bee trying to use the lp command with an IP or hostname but it doesnt seem to be working.  Is lp the right command to use? Whats wrong here? Help?
```

$ lp -h  lucky.um.maine.edu:9100 fileName


```

---

### Post by 1clue on 2012-09-20
Try **lpr**, but the -h should be a -H

---

### Post by codemaniac on 2012-09-21
> **conradin said:**
> Hi Everyone!
I want to print from the command line to a network printer. Ive bee trying to use the lp command with an IP or hostname but it doesnt seem to be working.  Is lp the right command to use? Whats wrong here? Help?
```

$ lp -h  lucky.um.maine.edu:9100 fileName


```

After you have successfully setup your default printer in Linux, Open up the terminal and use the command to print in Linux is &#8217;lpr&#8217;.

---

### Post by Deepak A on 2012-09-21
> **conradin said:**
> Hi Everyone!
I want to print from the command line to a network printer. Ive bee trying to use the lp command with an IP or hostname but it doesnt seem to be working.  Is lp the right command to use? Whats wrong here? Help?
```

$ lp -h  lucky.um.maine.edu:9100 fileName


```

What error message is coming?
Is CUPS configured properly? Have you added Network printer?
Are you able to ping?

*lpstat -p -d *

will list all the available printers.

---

### Post by conradin on 2012-09-21
I guess I have to set up the printer? (This confuses me because I would think networking standard would define the type of data sent to the printer.)
So I have to install the printer. Ok. Im looking to make my script take care of the entire printing process. How so i set up a printer with terminal commands?

---

### Post by 1clue on 2012-09-21
> **conradin said:**
> I guess I have to set up the printer? (This confuses me because I would think networking standard would define the type of data sent to the printer.)
So I have to install the printer. Ok. Im looking to make my script take care of the entire printing process. How so i set up a printer with terminal commands?

Yes, you need to set up the printer.  Don't set it up with terminal commands unless you have no gui.  You need a driver for your printer, which may be recognized by the printing system that comes with Ubuntu or you may need to find one, possibly a proprietary driver from the manufacturer or a third party.

With regards to what gets sent over the wire being standard, well there is more than one standard.  Every manufacturer has at least one "language" for controlling their printers, and sometimes they also adhere to a more widely used standard.

However, there's a significant difference between the software used to run a USB-connected inkjet or a full enterprise high-speed printer that can print, collate and bind 1,000 copies of a 400 page book unattended.  Anywhere in between, you have selection of paper trays, paper type, resolution, double-sided or single-sided, and countless other things.  Sometimes the printer handles some of that, and other times the driver needs to.  Sending a 300 dpi image to a 1200 dpi printer gets you a crappy image on the page, but sending a 1200 dpi image to a 300 dpi printer causes a different kind of mayhem.

For one thing, some printers come with their own "print server" software and can handle queuing, paper tray selection and all sorts of things.

---

