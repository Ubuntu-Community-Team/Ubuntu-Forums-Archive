---
title: "[SOLVED] printer driver"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by jimmy.on on 2008-10-04
hi
 i am totaly new to linux type o/s, just installed ubuntu last night for the first time. but have used the windows systems for many years now. when i want a driver in windows its normaly click a setup icon and your off. i am finding it hard to understand how to install a driver in ubuntu with the scripts i understand is necessary for same. where do you put the script? where do you save it to? i feel like a right thicko but once i crack this system i can look forward to a challanging time learning the rest of the system. my printer is a lexmark E120n connected to my router by lan cable on a network. i can see the printer on the system but can't get the driver in. greatful for any help but please remember you are talking to a novice on ubuntu.

---

### Post by gandaran on 2008-10-04
have you tried going to system » administration » printers, click on new printer, wait until the printer is located then just follow the procedure, choose the driver (I believe there won't be any problem with lexmark drivers, you should be able to find one there) name the printer setup, that's about all you have to do.

---

### Post by halitech on 2008-10-04
You are lucky, you have one of the few Lexmark printers that are supposed to work

[http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-E120n](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-E120n)

I believe gandaran is correct except when you click on new printer, you will probably need to select HP Jet Direct or IPP printing since it has an IP address and is connected direct to your router and not being shared (if I read your post correctly) then select Lexmark for the manufactorer and E120N for the printer and cross your fingers that it works

---

### Post by jimmy.on on 2008-10-04
thanks for your replies but i went through that procedure and the nearest driver is for a E210 and that doesn't work as i even tried that.i have the driver disk but don't know how to install the driver.

---

### Post by halitech on 2008-10-04
do you have the IP address for the printer? can you open a terminal and ping the printer?

---

### Post by gandaran on 2008-10-05
did you in the servers configuration tab tick the show other system shared printers box?
why not first try the printer connected to the computer, if it works then you just have to find out whats wrong with the server setup.

---

### Post by halitech on 2008-10-05
> **jimmy.on said:**
>  my printer is a lexmark E120n connected to my router by lan cable on a network. i can see the printer on the system but can't get the driver in. greatful for any help but please remember you are talking to a novice on ubuntu.

> **gandaran said:**
> did you in the servers configuration tab tick the show other system shared printers box?
why not first try the printer connected to the computer, if it works then you just have to find out whats wrong with the server setup.

by the sounds of the way he's got it hooked up, its connected to his router, not a computer (would be a waste of a network printer to not have it on the network) so I don't think its a matter of finding anything with the server as it doesn't sound like he has one

---

### Post by Sef on 2008-10-05
How have you connected your printer to the computer: 

1) direct

or

2) networked?

---

### Post by jimmy.on on 2008-10-05
my set up is an old HP Pavilion 461 with ubuntu as the only o/s, isp is virgin cable, Peak wireless router. the printer has static address 192.168.1.5 which i can see on a search and can ping ok but just don't know how to put the driver in. i have no server and everything goes through my router. i have tried connecting the printer direct to the HP via usb but the same problem, the printer is there but can't get the driver in.

---

### Post by halitech on 2008-10-05
ok, follow the first steps I posted above and when it gets to the manufactorer, select generic and click next, then select PCL 6/PCL XL Printer and use the Generic PCL 6/PCL XL Printer Foomatic/pxlmono. on the next page, fill in the info and click apply. The printer *should* work after that

---

### Post by jimmy.on on 2008-10-05
hey Halitech you know your stuff.thats it working fine now. i am affraid though this is the first of many enquiries until i master Ubuntu. thanks for all the replies from this nice friendly forum.

---

### Post by halitech on 2008-10-05
glad to hear its working for you :) and I don't know it all, google helps me out alot when it comes to drivers to use but a network printer is a network printer and they work pretty much the same :)

Since we have you working, please mark the thread as solved so others will know :)

---

