---
title: "Network Printers"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by fady_a on 2008-11-04
Hey,

Ive just switched to ubuntu over the weekend and im at school, need soem help connecting to some of the printers on  our networrrk... with windows i could just add printer, from printer, find now ... does ubuntu support networks like this and will i be able to print from ubuntu? (im running 8.10 if it makes a difference) 

Much appreciated!

---

### Post by oldsoundguy on 2008-11-04
if the printers are already set up for network sharing on their home computers, and YOU are on that network, it is really easy.  Go to System> Administration> Printing>  Sign in and go to add new printer. It will go searching for any available printers and all you have to do is add the ones you want.
I have a home network consisting of 4 Linux boxes and 2 XP boxes.  I have printers installed in each of the work area stations and they are on both XP boxes and Linux boxes. All but a label printer and a Raster (mac) based printer can be accessed by every computer on the net (including a pair of PDA's) and a print file can be sent to them.  
The above was all I had to do to get such to happen!

---

### Post by scott_g on 2008-11-04
I believe the printers he was talking about are not connected to a computer, but directly to the network.  Does this change the steps for adding a printer?

---

### Post by oldsoundguy on 2008-11-04
never have dealt with that.  A real "networking" person would have to answer that one!

---

### Post by candtalan on 2008-11-04
> **scott_g said:**
> I believe the printers he was talking about are not connected to a computer, but directly to the network.  Does this change the steps for adding a printer?

I am not a 'real' networking person.....  :-) but I have a couple of network connected printers here and they are easily managed....

I loaded Ubuntu 8.10 live CD, and

System>Administration>Printing
(see printer configuration window - local host)
Click for New Printer
(it searches, mine shows nothing but offers a window)
New Printer window
(I am not looking for a printer connected to a windows PC, I am looking for a printer which is connected to th enetwork via a 'printer server box' [a 'print server' can be anything from a mouse sized unit to a part of a function of a full PC]

A Print Server has an identity which is an IP address. I know mine it is
192.168.1.10

In the New Printer window, I select
App/Socket/HP JetDirect
and enter 192.168.1.10 into the  Host field
(port number 9100 is default)
(click Forward)

(next window) 'Select Printer from database'
(make the window larger for convenience)
I know that one of the printers, th eone with th eprint server 192.168.1.10 is a Brother
(Forward)

of type HL1230
(driver is offered as recommended)

(Forward)

Printer Name - I call it 
Brother

(apply)

(it completes)
I see a printer icon in the window

hth

---

