---
title: "cannot print since updating to 12.04"
date: 2012-07-21
forum: New to Ubuntu
---

### Post by standell on 2012-07-21
hello,

i still cannot print since updating to 12.04. i could print in 11.10.

i'm running 64-bit 12.04. cups 1.5.3 and hplip 3.12.6. the HP OfficeJet G85 printer is directly connected to the the linux box via usb. i read that i should comment out the blacklist usblp line in:
/etc/modprobe.d/blacklist-cups-usblp.conf

and i've done that. i've run hp-check and no errors are detected. 

when i try to print, the light on the printer flashes, but i never get output. SimpleScan works successfully and will scan an image on the glass.

i've purged and re-installed a few times... still no success. 

very frustrated, i'm not at all a linux expert. please!!! help!!!
thanks.

---

### Post by levlaz on 2012-08-01
What happens when you run hp-setup

```
 hp-setup -i 
```

Or try the GUI 

```
 sudo apt-get install hplip-gui 
```

Maybe you can use these two tools to fix your problem.

---

### Post by standell on 2012-08-25
thanks for the response.

when i execute hp-setup -i 
i get this:

HP Linux Imaging and Printing System (ver. 3.12.6)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

(Note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.)

--------------------------------
| SELECT CONNECTION (I/O) TYPE |
--------------------------------

  Num       Connection  Description                                               
            Type                                                                  
  --------  ----------  ----------------------------------------------------------
  0*        usb         Universal Serial Bus (USB)                                
  1         net         Network/Ethernet/Wireless (direct connection or JetDirect)

Enter number 0...1 for connection type (q=quit, enter=usb*) ? 

Using connection type: usb

Using device: hp:/usb/OfficeJet_G85?serial=SGG22E15MHVL

Setting up device: hp:/usb/OfficeJet_G85?serial=SGG22E15MHVL

---------------------
| PRINT QUEUE SETUP |
---------------------

warning: One or more print queues already exist for this device: OfficeJet_G85.

Would you like to install another print queue for this device (y=yes, n=no*, q=quit) ? n

Done.

i entered 'n', indicating that i don't want to set up another print queue for the printer.

so, mostly, i'm disappointed and frustrated with linux. i can't print and haven't been able to, except for a short period of time,  since i upgraded to 12.04. linux stinks. ok, please forgive the rant, but until i can print with regularity, i say linux stinks. 

thanks for your help and flames that i anticipate getting,
mike

---

### Post by Geffers on 2012-09-02
> **standell said:**
> hello,

i still cannot print since updating to 12.04. i could print in 11.10.



Me too, I am presently using a LiveCD 10.10 just for printing. I get missing filter error.

The printer utility doesn't seem to give any option to alter drivers etc.

Geffers

---

### Post by Geffers on 2012-09-02
> **standell said:**
> 
so, mostly, i'm disappointed and frustrated with linux. i can't print and haven't been able to, except for a short period of time,  since i upgraded to 12.04. linux stinks. ok, please forgive the rant, but until i can print with regularity, i say linux stinks. 

mike

Stay with Linux, there are still issues when there are problems, not quite as easy to resolve as Windows but, very there are advantages.

When it is working it is stable, not so many security issues as Windows and the satisfaction of not contributing towards the profits of MS or Apple.

Geffers

---

### Post by Pharaoh1 on 2012-09-04
Hi,
       I think it must be something with 64 bit over 32 bit. My 32 bit installation of 12.04 prints just fine. My test page shows hpcups 3.12.2. I am running an HP F2200 series printer,scanner,copier also.  I am sorry I do not know of a fix for your problem but thought maybe the info could help someone create one.  ;)

---

### Post by Geffers on 2012-09-04
> **Pharaoh1 said:**
> Hi,
       I think it must be something with 64 bit over 32 bit. My 32 bit installation of 12.04 prints just fine. My test page shows hpcups 3.12.2. I am running an HP F2200 series printer,scanner,copier also.  I am sorry I do not know of a fix for your problem but thought maybe the info could help someone create one.  ;)

Mibe is 32 bit and don't work :(

Geffers

---

### Post by standell on 2012-09-06
thanks for the help/comments - i do appreciate them. 

yes, i'm running 64-bit. 

i'm not going to give up on linux. well, a more accurate statement might be i have no plans to give up linux yet. i'm just frustrated. i've wanted a linux system for a while and waited for a long time before taking the plunge. i was waiting for all the horrible details to be worked out before i committed. unrealistic, i know, but still - i could hope. 

anyway, the fact is, i don't really enjoy tinkering with my computer at home. i really just want it to be a tool that i can power up and it works. and right now, it's not. it's requiring time and effort from me to get it working properly. i understand most tools don't work flawlessly and all tools needs attention now and then. so... i guess i'm just whining. sorry about that. 

in any case, my printer is old and i've been intending to upgrade to a wireless unit. i want and intend to do that, but now i'm very concerned that i'll drop money on a wireless printer and it won't work. i'm considering buying a laser printer, so that's much more of a financial commitment than an inkjet, which i realize are pretty cheap now-a-days. 

so... i've started a new thread requesting input from folks who successfully use a wireless printer with 64-bit 12.04.
[http://ubuntuforums.org/showthread.php?p=12222427#post12222427](http://ubuntuforums.org/showthread.php?p=12222427#post12222427)

again, thanks for your comments & help.

---

### Post by nicolagiacobbe on 2012-09-21
I was in the same situation. Now it is working but I am not really sure about why.
I just entered in cups (browser pointing at: localhost:631) and deleted the G85 printer already there.
Then I gave the command:
hp-setup -i
and HPLIP told me that it found a G85 printer on USB port and asked if it should load the correct PPD file, after having answered 'yes' to the majority of questions I finally asked for printing a test page, at this point hp-setup stopped with an error but some noises were coming from the printer.
I waited a minute perhaps then quitted HPLIP from the top panel, the printer started to print an incomplete test page.
After waiting maybe five minutes I started a print and it worked without any hiccup.
The computer still tell me that there is a 'connection error' with the printer but the printing is done correctly.
YMMV.

---

### Post by Geffers on 2012-09-23
> **nicolagiacobbe said:**
> I was in the same situation. Now it is working but I am not really sure about why.



Same here, mine is now working, I didn't do anything to fix it.

Perhaps it got the hump as I logged on to Vista to print a couple of letters ;)

Geffers

---

### Post by Orez96 on 2012-10-05
Mine is the reverse of that.
I have Windows 7 64bit on a HP desktop with a HP printer.
I've been trying for days to print from a 32 bit Dell with Ubuntu.
It appears to go thru the motions but the error light on the printer flashes and never prints.
The Ubuntu machine knows the damn HP printer is out there but never prints.

Any advice?

---

