---
title: "Printer help"
date: 2013-10-19
forum: New to Ubuntu
---

### Post by 8nLkxdz on 2013-10-19
Help...cannot get printer to work.

I have a new HP Deskjet 2542.  The printer does work with a Windows7 computer.

Ubuntu version 12.04

When I try to install in on my Ubuntu computer the install appears to work correctly.  The printer finds the printer and correctly identifies it.  Says "a printer connected to usb".  Press forward and it searches for comes back and asks me to select printer from menu.  I choose HP and the the Deskjet 2500cm (recommended).  Forward again and then apply.  It asks for me to print a test page.  

I agree to the test page and absolutely no printing.  It says " Idle-Rendering completed".  I can watch the print queue and the job appears in the queue and then disappears as if it has printed.  But no printing took place.

Any suggestions.  I'd really hate to have to go back to Win8,  especially after I blew it away when I installed Ubuntu 12.04!!


:(


Larry

---

### Post by rburkartjo on 2013-10-19
open the ubuntu software center. in the search box type in hplip. that should bring up hplip toolbox.install it. then open up the applications and follow the instructions. i had to do it awhile ago to get ubuntu to recognize my printer. good luck

---

### Post by ajgreeny on 2013-10-19
The version of hplip in 12.04 is not recent enough for that printer so you will need to go to hplip website to get the new one which should work fine.

Download the **hplip-3.13.10.run **file
 [http://prdownloads.sourceforge.net/hplip/hplip-3.13.10.run](http://prdownloads.sourceforge.net/hplip/hplip-3.13.10.run)
and follow these instructions on how to install.[INDENT] 
[LIST]
[*]Download the file to a convenient location (e.g., home directory or desktop, etc). 
[*]Open a console/terminal and cd to the location where the installer was downloaded. (e.g., cd ~/Desktop) 
[*]Type in and run this command: 'sh hplip-3.13.10.run' 
[*]Follow the prompts to install. 
[/LIST]
 [/INDENT]

---

### Post by 8nLkxdz on 2013-10-19
I have hplib installed and have run it.  Setup Devise there doesn't find a printer.  Cups web interface does find the printer and I chose this:

Local Printers:   HP Deskjet 2540 series (HP Deskjet 2540 series)

I chose continue and it gives me the name of the printer, the description and asks for a location.  I input home.  Click Share this printer.  Don't know if I need to do this or not.

Click continue  and I get a series of printer drivers.  

Chose this one:

Local Printers:   HP Deskjet 2540 series (HP Deskjet 2540 series)

Click Add Printer

Get set default actions, successfully
Get this screen
[h=2][HP_Deskjet_2540_series]("http://localhost:631/printers/HP_Deskjet_2540_series") (Idle, Accepting Jobs, Not Shared)[/h]
Print test page...nothing no printing

The printer is on and connected.  I swear.  Else the hplip couldn't have found the printer.

Chose another driver????

Larry

---

### Post by 8nLkxdz on 2013-10-19
I got a driver to work.

HP 2500c hpijs, 3.12.2 (color, 2-sided printing)

Don't know if that was the problem or the fact that I explored and set myself as a user.  Didn't know about that.

Larry

---

