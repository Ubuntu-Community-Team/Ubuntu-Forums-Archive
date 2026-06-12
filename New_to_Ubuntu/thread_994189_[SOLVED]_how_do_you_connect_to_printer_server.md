---
title: "[SOLVED] how do you connect to printer server"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by corkscrew on 2008-11-26
I have two laptops and 2 desktops in my network. I have added a dlink dpr 1260 printer server. On the dual boot machines i can connect to the server through win xp and set up the printer no problem.

How do i do it ubuntu? If i open system - administration printers, then select new then lpd/lpr host or printer fill in the ip address and select probe, it just freezes the same happens from any pc with ubuntu?

---

### Post by Peter09 on 2008-11-26
try the following address

[http://localhost:631/](http://localhost:631/)

---

### Post by corkscrew on 2008-11-26
that gives me a web browser of the printers attached locally. I want to connect to a printer which is attached to a print server

---

### Post by Peter09 on 2008-11-26
Cups should see remote printers. Are you sharing the printers in Windows?

---

### Post by bobnutfield on 2008-11-26
When you set the printer up as a new printer, your entry should have looked something like this:

> lpd://192.168.1.X/name of queue

And, I know you are aware that you must have the correct driver installed.
This has worked for me in the past when using a printer connected via a server drirectly to the router.

---

### Post by corkscrew on 2008-11-26
sorry about this i'm real newb on linux, want to get rid of windows though!
where do you mean to add the printer? through the web based interface of cups is that what you mean?
The printer in question does have the right driver because when i had it plugged straight into my ubuntu desktop and shared there every other machine on the network could access. It's only now that i have plugged it into printer server i cant set it up

---

### Post by corkscrew on 2008-11-26
Peter09,
how do i navigate to printer server in cups web based interface

---

### Post by bobnutfield on 2008-11-26
If you open your routers home page (the setup page), there should be a section which tells you the attached IP addresses.  One of them will be your print server.  This is the address you would put ( as described in my previous post ) under Device URI when you click on "Add Printer" in the printer set up dialogue.

You may be able to find the IP address of the print server by typing sudo ifconfig in a terminal.

---

### Post by Peter09 on 2008-11-26
I need some more details:

Is the printer connected to a Windows Machine?
Is the printer on a different machine (print server) to the one you are configuring?
Are there other machines on the network that can see the printer?

---

### Post by corkscrew on 2008-11-27
Bob,
Thankyou very much for taking the time to help me out!! one step closer to getting rid of Gates!!
Worked a treat, all i had to do was find the name of the "queue" i did that by opening the printer server configuration program in a web page where all the details of attached prnters are.
Pity that gui printer menu in ubuntu did'nt work wasted a lot of time with that thing!!
Just for my education where is this //localhost:631 in the file system

---

### Post by corkscrew on 2008-11-27
Pete,
thanks for the localhost:631 tip as you can see Bob helped me the rest of the way

---

### Post by Peter09 on 2008-11-27
Hi,
just to complete this, localhost is the machine that you are on. Its just a web address and port (631) that your local CUPS application is running on.

---

### Post by bobnutfield on 2008-11-27
> **corkscrew said:**
> Bob,
Thankyou very much for taking the time to help me out!! one step closer to getting rid of Gates!!
Worked a treat, all i had to do was find the name of the "queue" i did that by opening the printer server configuration program in a web page where all the details of attached prnters are.
Pity that gui printer menu in ubuntu did'nt work wasted a lot of time with that thing!!
Just for my education where is this //localhost:631 in the file system

Glad you got it woring.  Localhost is your machine from the network's point of view (the same as 127.0.0), and :631 is port 631, the default print port on most Linux systems.

---

