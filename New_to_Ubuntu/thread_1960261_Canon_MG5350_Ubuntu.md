---
title: "Canon MG5350 Ubuntu"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by cray5656 on 2012-04-17
SOLVED

Hi

I have a new Canon PixmaMG5350 and when I go to print a Libre document in Ubuntu 11.10 it seems to accept it is a Canon 5300 series printer, but when you press print it appears to be printing on the computer but it does not actually print.

Any advice would be great!

---

### Post by callmemahavir on 2012-04-17
Have you tried installing CUPS...

It is standard for printing in UNIX.

Try in prompt...

sudo apt-get install cups

TRY CONFIGURE AND EXPLORE IT!!!

---

### Post by ixtok on 2012-04-17
I have a Canon MG5250 which is probably similar. You can find the driver on the Canon-Asia site in the support area. There are drivers for printing and for scanning. Use the debian versions, de-compress and run the install in the terminal. This set up my wireless printer with no problems. If you need more help with the drivers let me know.

---

### Post by cray5656 on 2012-04-17
sorry noob questiopn but how do I run the installer in Terminal. I know what terminal is. Will the installer just open in Terminal?

Thanks

---

### Post by ixtok on 2012-04-17
I am a bit of a novice myself, but what I do is open the terminal and navigate to the directory where the decompressed files are using  "cd" and "dir" commands. You should find a file called install.sh  so you enter ```
sudo ./install.sh
```

---

### Post by cray5656 on 2012-04-17
Hi
nearly there I realised I was trying to access the zipped folder


All working thanks!

---

### Post by mikeashelby on 2012-06-01
I've managed to get this printer working (surprisingly easily actually) - but I can't see any option at all for printing in draft quality...

Any ideas? This would be a real pain if I'm forced to use copious amounts of ink each time!

Thanks in advance!

Mike

---

### Post by cruxfilm on 2013-01-20
Can somebody here explain to me in detail how they got the MG5350 to work via network in Ubuntu 12.04 LTS?

I installed mine using [**these drivers**]("http://support-sg.canon-asia.com/contents/SG/EN/0100395402.html") but only detects the printer when connected via USB.

Trying to run the driver installer again using *Network* gives me this:
```
==================================================

Canon Inkjet Printer Driver
Version 3.60
Copyright CANON INC. 2001-2011
All Rights Reserved.

==================================================
Command executed = sudo dpkg -iG /home/cruxfilm/Downloads/cnijfilter-mg5300series-3.60-1-deb/packages/cnijfilter-common_3.60-1_amd64.deb
(Reading database ... 275817 files and directories currently installed.)
Preparing to replace cnijfilter-common 3.60-1 (using .../cnijfilter-common_3.60-1_amd64.deb) ...
Unpacking replacement cnijfilter-common ...
Setting up cnijfilter-common (3.60-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Command executed = sudo dpkg -iG /home/cruxfilm/Downloads/cnijfilter-mg5300series-3.60-1-deb/packages/cnijfilter-mg5300series_3.60-1_amd64.deb
(Reading database ... 275817 files and directories currently installed.)
Preparing to replace cnijfilter-mg5300series 3.60-1 (using .../cnijfilter-mg5300series_3.60-1_amd64.deb) ...
Unpacking replacement cnijfilter-mg5300series ...
Setting up cnijfilter-mg5300series (3.60-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

#=========================================================#
#  Register Printer
#=========================================================#
Next, register the printer to the computer.
Connect the printer, and then turn on the power.
To use the printer on the network, connect the printer to the network.
When the printer is ready, press the Enter key.
> 

#=========================================================#
#  Connection Method
#=========================================================#
 1) USB
 2) Network
Select the connection method.[1]2

Searching for printers...


#=========================================================#
#  Select Printer
#=========================================================#
Select the printer.
If the printer you want to use is not listed, select Update [0] to search again.
To cancel the process, enter [Q].
-----------------------------------------------------------
 0) Update
-----------------------------------------------------------
Could not detect the target printer.
-----------------------------------------------------------
Currently selected:[0] Update
Enter the value. [0]

```

Any idea how to properly install it so that it works via network?

**EDIT:**
Never mind, I'm an idiot. The printer wasn't connected to my network, so obviously my Ubuntu ulrabook couldn't detect it.

---

### Post by d_t_s2 on 2013-08-03
Hi all. 
I too have recently bought the canon mg5350 printer. After much trouble fetling and trawling 1000s of pages I finally managed to get it working sort of! I can print documents PDFs etc. but when trying to print photo via gimp it processes but no output. I also tried using photoprint but that gave me an error of no filter? I am confused. 

Has anybody managed to use this printer fully, if so please advise. Many thanks.

---

### Post by EBWQNHD on 2013-08-04
have you installed the Canon drivers? You would install the MG5300 series drivers...............as it covers the 5310, the 5320, the 5330 ........ you get the picture ..............

If you have, 

> [COLOR=#ff0000]sudo dpkg -l | grep cnijfilter[/COLOR]

...... can you copy and paste what this gives please.......if you copy and paste this into a terminal

_________________________________________________________________________________________________

If you don't have the Canon drivers installed, I would recommend that you do, and I would be happy to give detailed advice how to do this

---

