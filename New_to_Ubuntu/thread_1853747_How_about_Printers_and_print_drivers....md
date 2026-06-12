---
title: "How about Printers and print drivers..."
date: 2011-10-02
forum: New to Ubuntu
---

### Post by TLARbb on 2011-10-02
I have tried Ubuntu 10.4.3 LTS on my Toshiba Laptop and the wireless was not automatically recognized, however, on the 11.04 version it was.  I am liking the 11.04 version and the Libre office package.
 
However, to be able to "kick Microsoft to the curb", I will have to have a viable printing solution.
 
Currently my OfficeJet 6110 is hooked up to my main desktop which I am typing on now (Windows XP) and is shared with the other computers in my Windows network.  
 
I don't know if Ubuntu has drivers for this printer or not, I haven't tried it yet from this desktop.  I've got a few more issues to work out before I try to take a computer to Linux only (a project to determine if I can live without Microsoft), but one of the big things is to get a multifunction machine such as the OfficeJet to work as a printer and hopefully a scanner.  I would be willing to purchase a wireless machine so that the linux machine(s) could talk directly to it and the windows machines could also.  
 
Am I missing something and off base?
 
Ed

---

### Post by dave01945 on 2011-10-02
not totally sure what you want are you leaving the printer connected to windows and want to print to it from ubuntu if so just go to apps menu (press windows key) type printing select it then select network then choose windows printer via samba

if your connecting to ubuntu just plug it in again go to printing if there is not a driver already built in then try the manufacturers website they may have a linux driver

---

### Post by 3rdalbum on 2011-10-02
OfficeJets are HP devices, so they should work fine.

Just go to the Printers panel (the menu on the top-right then System Settings then go to Printers) and click the Add button. Wait a few seconds and a new item will appear in the list on the left of the Window. It should be your HP printer. The rest of the process should pretty much "Add" and "Next, Next, Next" and then it will be set up for printing.

I can't advise on the scanning side of it, sorry; I don't know if XP shares the device as a scanner as well.

---

### Post by oldsoundguy on 2011-10-02
I have a 6110x hung off of a Windows box and have the box networked.  I print to it all the time from my main Linux box.  Just installed the cups printer driver. System> Administration> Printing.

---

### Post by fantab on 2011-10-03
HP has drivers for Linux. Install **hplip** and **hplip-gui** from synaptic for scanning install **xsane**.

---

### Post by TLARbb on 2011-10-03
Thanks guys.  Looks like this will work okay.  I'll give it a try and see what happens.  I was hoping that I could use the OfficeJet with Linux.  - Ed

---

### Post by donkyhotay on 2011-10-03
I've had good luck with HP's and epsons on linux. Trying to install a canon printer was a total nightmare though.

---

### Post by thatguruguy on 2011-10-03
> **fantab said:**
> HP has drivers for Linux. Install **hplip** and **hplip-gui** from synaptic for scanning install **xsane**.

xsane is unnecessary.  Simple Scan works just fine.  Also, I've never installed hplip-gui in order to use my HP Officejet 6500, because it isn't necessary, either.

---

### Post by mastablasta on 2011-10-03
just want to add that sometimes windows printer is not found by Ubuntu directly. But if you can somehow find the path to it (e.g. //MSnetwork/officejet2001 ) it can be entered manually and then printer is recognised and should work. I had this situation happen to me once. was using Kubuntu 10.10 though which was also missing an additional package as a bonus)

---

### Post by philinux on 2011-10-03
> **thatguruguy said:**
>   Also, I've never installed hplip-gui in order to use my HP Officejet 6500, because it isn't necessary, either.

How do you check ink levels without the gui?

---

### Post by thatguruguy on 2011-10-03
> **philinux said:**
> How do you check ink levels without the gui?

I have an Officejet 6500, which has its own display.  It tells me the ink levels.

The 6110, which the OP has, also has its own display.

---

### Post by philinux on 2011-10-03
> **thatguruguy said:**
> I have an Officejet 6500, which has its own display.  It tells me the ink levels.

The 6110, which the OP has, also has its own display.

The deskjet we have needs the hplip-gui. Does a good job too.

---

### Post by TLARbb on 2011-10-04
> **dave01945 said:**
> not totally sure what you want are you leaving the printer connected to windows and want to print to it from ubuntu if so just go to apps menu (press windows key) type printing select it then select network then choose windows printer via samba
 
if your connecting to ubuntu just plug it in again go to printing if there is not a driver already built in then try the manufacturers website they may have a linux driver
 
Okay, I ran Ubuntu from the live CD on the machine the 6110 is attached to.  The print test ran from Linux fine.  So, printing directly to an attached printer should work.
 
However, when running Ubuntu from another computer, it cannot find the 6110 when it is connected to the Windows computer even though it is "shared".  It seems that I need to hook a network printer up directly to the router. But that becomes a wiring problem unless I can find an ingenious way around running an ethernet cable.  I have to review my printer documentation to see if I can hook it up directly to the router and use it as a network printer.  Probably so, but then I have to come up with an alternate way to connect to the computer. (probably a wireless adapter for it)
 
I can't really afford to mess up the computer I am speaking of since it is my most critical machine, so I am doing my Linux experimenting on a "surplus" machine.  I think this will work out fine, but for the surplus machine I have to have a wireless adapter for it as well.  It is just a bit of "banjo work" I guess.
 
Ed

---

### Post by TLARbb on 2011-10-04
One more question.  How good is Ubuntu at plug and play?  If I set up Ubuntu on the machine now, am I going to get into trouble installing the wireless adapter later?  I'm hoping that I can go ahead and set up Ubuntu and add the wireless adapter later.  If that's going to give me issues with setting up the adapter, I can wait until I get it and make sure it works with XP before I install Linux.  If it doesn't matter, I'll go ahead with the Ubuntu install.
 
Forgive me for my ignorance, but I learn pretty quick.  I think.
 
Ed

---

### Post by wolfen69 on 2011-10-04
> **TLARbb said:**
> How good is Ubuntu at plug and play?

Very good, actually. HP printers require nothing to set up except plugging it in.

---

