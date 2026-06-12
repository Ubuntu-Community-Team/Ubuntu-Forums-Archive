---
title: "Cant make printer work"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by arthur34 on 2011-11-01
Hello everyone. I have just bought a new Brother Printer HL-3040CN and can't install it.I am using Ubuntu 11.10.  This printer is not on the list to select from. I have searched for a DPP file for it without success. The brother help site [http://solutions.brother.com](http://solutions.brother.com) seems to suggest I download hl3040cnlpr-1.1.1-4.i386.rpm and hl3040cnlpr-1.1.1-4.i386.deb (both for Linux users), which I have done. Neither of these files will open - I get an error msg "wrong achitecture 'i386'. To sum up; With the printer on and connected, Linux finds the printer using the Add Printer thingo, but can't find a driver when it searches. Any help would be most appreciated. PS; I've been using Ubuntu 10.10 for nearly a year and found it great, but I am finding 11.10 very confusing indeed - so many changes- too many, it uses up too much time. Cheers from Ballarat, Australia.

---

### Post by DapperMe17 on 2011-11-02
Even though this isn't a direct answer to your question, my experiences with Ubuntu have proven that HP printers are greatly supported with native drivers, and normally are auto-configured for you! HPLIP-gui is a nice GUI utility as well.

If Ubuntu has changed a bit much for you recently, you can always give Xubuntu a try. Xubuntu/XFCE has really come to age over the last couple of years and looks really great in recent releases.

Good luck with your Brother, as I'm sure you will receive the help your looking for shortly.

:popcorn:

---

### Post by DapperMe17 on 2011-11-02
Just looking at your post again.........with Ubuntu, you will download the .deb file only, and it has to be the 64-bit version, if you're running the 64-bit version of Ubuntu. 

You can install package gdebi from Synaptic Package Manager, then, once you download the 64bit version of that .deb file from Brother, go to the downloaded file, right click, and open with gdebi. That will install the file for you. 

Just restart your system then, and see if you can select the correct driver during your printer configuration.

****Note, this thread should help you.....[http://ubuntuforums.org/showthread.php?t=1553341](http://ubuntuforums.org/showthread.php?t=1553341)

---

### Post by fantab on 2011-11-02
> **arthur34 said:**
> Hello everyone. I have just bought a new Brother Printer HL-3040CN and can't install it.I am using Ubuntu 11.10.  This printer is not on the list to select from. I have searched for a DPP file for it without success. The brother help site [http://solutions.brother.com](http://solutions.brother.com) seems to suggest I download hl3040cnlpr-1.1.1-4.i386.rpm and hl3040cnlpr-1.1.1-4.i386.deb (both for Linux users), which I have done. Neither of these files will open - I get an error msg "wrong achitecture 'i386'. To sum up; With the printer on and connected, Linux finds the printer using the Add Printer thingo, but can't find a driver when it searches. Any help would be most appreciated. PS; I've been using Ubuntu 10.10 for nearly a year and found it great, but I am finding 11.10 very confusing indeed - so many changes- too many, it uses up too much time. Cheers from Ballarat, Australia.

The link you have above gives detailed instructions on how to on [this webpage]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#004"). 

Since you are using 64bit architecture you will need to install: (you can copy paste the following commands in the TERMINAL) 

```
sudo apt-get install ia32-libs
OR
sudo apt-get install lib32stdc++
```Download **.deb** packages for both [B]lpr and cupswrapper driver.
Plugin and connect your Printer[/B] 
**Install** downloaded .deb packages with Software Center- if there is problem with Software Center install then do this:
```
sudo dpkg  -i  --force-all  hl3040cnlpr-1.1.1-4.i386.deb
sudo dpkg  -i  --force-all  hl3040cncupswrapper-1.1.1-4.i386.deb

```To confirm the installation do this
```
$ dpkg -l | grep Brother
```If the driver installed correctly then you should see:
 [COLOR=Black]ii  dcp540cnlpr                                1.0.1-1       Brother lpr Inkjet Printer Definitions[/COLOR]

---

### Post by kurt18947 on 2011-11-02
> **DapperMe17 said:**
> Just looking at your post again.........with Ubuntu, you will download the .deb file only, and it has to be the 64-bit version, if you're running the 64-bit version of Ubuntu. 

You can install package gdebi from Synaptic Package Manager, then, once you download the 64bit version of that .deb file from Brother, go to the downloaded file, right click, and open with gdebi. That will install the file for you. 

Just restart your system then, and see if you can select the correct driver during your printer configuration.

****Note, this thread should help you.....[http://ubuntuforums.org/showthread.php?t=1553341](http://ubuntuforums.org/showthread.php?t=1553341)

Will Gdebi install the 32 bit drivers on a 64 bit system?  I did not know that.  I know Gdebi works great on 32 bit systems. I think lib32stdc++ might be installed in Ubuntu by default and you just need one or the other not both.  It's easy enough to check in Synaptic.  Otherwise it's not too painful to download the .deb file(s), open a terminal, cd to that directory and do the ol' copy/paste thing.  Installing a Brother printer not included in the foomatic database on a 64 bit system isn't as simple as a printer that is included but it's not too painful once you do it once or twice.

On other tip I found with an older Brother MFD MFC-7820N.  Using the default drivers printing the second and subsequent pages were **s   l   o   w **like 3 or 4 pages/min. slow. I downloaded from the Ubuntu Repos  a CUPS driver for brother lasers after doing the automatic install.  I can't check the exact file name now but when clicking on package  it it mentions the models supported.  I used that driver instead of the default and throughput was much much improved.

---

### Post by fantab on 2011-11-02
> **kurt18947 said:**
> **I think lib32stdc++ might be installed in Ubuntu by default and you just need one or the other not both.  It's easy enough to check in Synaptic. **

 Installing a Brother printer not included in the foomatic database on a 64 bit system isn't as simple as a printer that is included but it's not too painful once you do it once or twice.

On other tip I found with an older Brother MFD MFC-7820N.  Using the default drivers printing the second and subsequent pages were **s   l   o   w **like 3 or 4 pages/min. slow. I downloaded from the Ubuntu Repos  a CUPS driver for brother lasers after doing the automatic install.  I can't check the exact file name now but when clicking on package  it it mentions the models supported.  I used that driver instead of the default and throughput was much much improved.

Thanks, I edited my previous post accordingly.

I Suggest people consult here on this forum before they buy new hardware to use on Linux. It will save so much time and workarounds if the hardware is known to work easily and sufficiently compatible.

---

### Post by arthur34 on 2011-11-03
Thanks to those who offered help. I was getting lost so I did a search and found http://ubuntuforums.org/archive/index.php/t-590793.html - which worked. I was able to follow this even though the others had maybe said the same thing. I note it is important to change the directory to where the driver files are !!!!!
Heres my amended text based on the above forum post, and many thanks to the Poster;
                                 HOW TO INSTALL BROTHER HL3040CN PRINTER ON LINUX UBUNTU 11.10
  from;   [http://ubuntuforums.org/archive/index.php/t-590793.html](http://ubuntuforums.org/archive/index.php/t-590793.html) and ammended to suit my HL3040CN printer.  
 Many thanks to BoardDWorld for this. Arthur34.
 
BoardDWorld
 October 25th, 2007, 02:33 AM
 Please note this is my first How-To, if there is an error please let me know. I have comprised this simply from how I went about doing it which worked perfectly. Printing tested in Firefox, Gimp & OpenOffice. Scanning tested in Xsane.

FIRST MAKE SURE YOUR SYSTEM HAS ALL UPDATES INSTALLED IF YOU HAVE A FRESH INSTALLATION OF UBUNTU.

64bit printing:
Works fine but with a little more fine tuning. HERE'S REFERENCE TO ALL PRINTERS INSTALLED SUCCESSFULLY ON UBUNTU 64BIT IN THIS THREAD: HERE (http://ubuntuforums.org/showpost.php?p=4014274&postcount=98), HERE (http://ubuntuforums.org/showpost.php?p=3748048&postcount=40) and HERE (http://ubuntuforums.org/showpost.php?p=3835451&postcount=61) 

Printer:
I'm quite a newbie to Linux and I found it really easy to install my Printer with the help of the official Brother Linux Driver WEBSITE (http://solutions.brother.com/linux/en_us/index.html). The site is a little outdated but the installation still remains simple thanks to Ubuntu & not to forget Debian (http://upload.wikimedia.org/wikipedia/commons/e/ed/LinuxDistroTimeline.png).

Step 1:
Open Terminal by selecting Applications ---- Terminal from the task bar. 

Step 2:
Type or Copy & Paste the following into Terminal and press enter: 
sudo apt-get install tcsh

Step 3: (don't know if it matters but I did it anyway)
From the task bar go to: System ---- Administration ---- Printing, select your printer that's not working then select edit and click delete.

Step 4:
Download the LPR Driver and CUPS Wrapper. Locate your model & download your "Debian" LPR printer driver from HERE (http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html).
Locate your model & download your "Debian" CUPS wrapper from HERE (http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html).

Step 5:
Now change to the directory where the drivers are. Presuming you downloaded the driver to your desktop Type or Copy & Paste the following into Terminal:
cd /Downloads              NB; Case Sensitive!!!!        NB2; This step very important!

Step 6:
Create the lpd directory. This is the first I have encountered this but in Hardy the directory had to be created. Skip this and move on to Step 7 if you're using Gutsy or below. In terminal Type or Copy & Paste the following command:

sudo mkdir /var/spool/lpd

Step 7:
Install the LPR Driver. In terminal Type or Copy & Paste the following command changing filename.deb to match the driver you've downloaded. The following line is for the HL3040CN  printer.

sudo dpkg -i --force-all hl3040cnlpr-1.1.1-4.i386.deb

Step 8:
Create the model directory. As with the lpd directory this is the first I have encountered this but in Hardy the directory had to be created. Skip this and move on to Step 9 if you're using Gutsy or below. In terminal Type or Copy & Paste the following command:

sudo mkdir /usr/share/cups/model

Step 9:
Now to install the CUPS wrapper driver. In terminal Type or Copy & Paste the following command changing cupswrapperMFC210C-1.0.2-3.i386.deb to match the driver you've downloaded. The following line is for the HL3040CN  printer.
 
sudo dpkg -i --force-all cupswrapper hl3040cncupswrapper-1.1.1-4.i386.deb

It's installed and ready for use.
  
- - - fin - - -
Cheers all:guitar:Yes, I play guitar and banjo!:P

---

### Post by DapperMe17 on 2011-11-05
Great job, Arthur.

Maybe you can post that in tutorials.

:grin:

---

### Post by drdisk on 2011-12-03
> **arthur34 said:**
> Thanks to those who offered help. I was getting lost so I did a search and found [http://ubuntuforums.org/archive/index.php/t-590793.html](http://ubuntuforums.org/archive/index.php/t-590793.html) - which worked. I was able to follow this even though the others had maybe said the same thing. I note it is important to change the directory to where the driver files are !!!!!
Heres my amended text based on the above forum post, and many thanks to the Poster;
                                 HOW TO INSTALL BROTHER HL3040CN PRINTER ON LINUX UBUNTU 11.10
  from;   [http://ubuntuforums.org/archive/index.php/t-590793.html](http://ubuntuforums.org/archive/index.php/t-590793.html) and ammended to suit my HL3040CN printer.  
 Many thanks to BoardDWorld for this. Arthur34.
 
BoardDWorld
 October 25th, 2007, 02:33 AM
 Please note this is my first How-To, if there is an error please let me know. I have comprised this simply from how I went about doing it which worked perfectly. Printing tested in Firefox, Gimp & OpenOffice. Scanning tested in Xsane.

FIRST MAKE SURE YOUR SYSTEM HAS ALL UPDATES INSTALLED IF YOU HAVE A FRESH INSTALLATION OF UBUNTU.

64bit printing:
Works fine but with a little more fine tuning. HERE'S REFERENCE TO ALL PRINTERS INSTALLED SUCCESSFULLY ON UBUNTU 64BIT IN THIS THREAD: HERE ([http://ubuntuforums.org/showpost.php?p=4014274&postcount=98](http://ubuntuforums.org/showpost.php?p=4014274&postcount=98)), HERE ([http://ubuntuforums.org/showpost.php?p=3748048&postcount=40](http://ubuntuforums.org/showpost.php?p=3748048&postcount=40)) and HERE ([http://ubuntuforums.org/showpost.php?p=3835451&postcount=61](http://ubuntuforums.org/showpost.php?p=3835451&postcount=61)) 

Printer:
I'm quite a newbie to Linux and I found it really easy to install my Printer with the help of the official Brother Linux Driver WEBSITE ([http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)). The site is a little outdated but the installation still remains simple thanks to Ubuntu & not to forget Debian ([http://upload.wikimedia.org/wikipedia/commons/e/ed/LinuxDistroTimeline.png](http://upload.wikimedia.org/wikipedia/commons/e/ed/LinuxDistroTimeline.png)).

Step 1:
Open Terminal by selecting Applications ---- Terminal from the task bar. 

Step 2:
Type or Copy & Paste the following into Terminal and press enter: 
sudo apt-get install tcsh

Step 3: (don't know if it matters but I did it anyway)
From the task bar go to: System ---- Administration ---- Printing, select your printer that's not working then select edit and click delete.

Step 4:
Download the LPR Driver and CUPS Wrapper. Locate your model & download your "Debian" LPR printer driver from HERE ([http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)).
Locate your model & download your "Debian" CUPS wrapper from HERE ([http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html)).

Step 5:
Now change to the directory where the drivers are. Presuming you downloaded the driver to your desktop Type or Copy & Paste the following into Terminal:
cd /Downloads              NB; Case Sensitive!!!!        NB2; This step very important!

Step 6:
Create the lpd directory. This is the first I have encountered this but in Hardy the directory had to be created. Skip this and move on to Step 7 if you're using Gutsy or below. In terminal Type or Copy & Paste the following command:

sudo mkdir /var/spool/lpd

Step 7:
Install the LPR Driver. In terminal Type or Copy & Paste the following command changing filename.deb to match the driver you've downloaded. The following line is for the HL3040CN  printer.

sudo dpkg -i --force-all hl3040cnlpr-1.1.1-4.i386.deb

Step 8:
Create the model directory. As with the lpd directory this is the first I have encountered this but in Hardy the directory had to be created. Skip this and move on to Step 9 if you're using Gutsy or below. In terminal Type or Copy & Paste the following command:

sudo mkdir /usr/share/cups/model

Step 9:
Now to install the CUPS wrapper driver. In terminal Type or Copy & Paste the following command changing cupswrapperMFC210C-1.0.2-3.i386.deb to match the driver you've downloaded. The following line is for the HL3040CN  printer.
 
sudo dpkg -i --force-all cupswrapper hl3040cncupswrapper-1.1.1-4.i386.deb

It's installed and ready for use.
  
- - - fin - - -
Cheers all:guitar:Yes, I play guitar and banjo!:PA thousand thank-yous for posting the above step-by-step list!
I am new to ubuntu (installed it yesterday) and had hours of frustration trying to install the DPC165C printer.
Following the above steps solved the problem at the first attempt.
I had to vary the command to cd to Downloads, since it did not need the / before it.
The linux drivers had moved on the brother website, but I found them okay!
Thanks again.

---

### Post by drdisk on 2011-12-03
Oh, I should have mentioned:
I have installed Ubuntu 10.4 using a bootable USB stick onto an Asus eee-pc 701SD.
My background since mid-eighties has been CDC-ITOS -> UNIX (but no hands-on since 1989) -> CP/M -> DOS -> PC-DOS -> IBM-OS2 -> MS-DOS -> Windows (2.0 -> 3.0 -> 3.1 -> 95 -> 98 -> me -> XP) with various versions of MacOS chucked in while helping others.
I also enjoyed re-visiting my almost-forgotten UNIX commands once I found the terminal.

---

### Post by doddel on 2012-01-21
Following the instruction of the thread I did not get the printer to operate. What worked was after having installed the .deb packages as described in the earlier post, including mkdir of the required folders in /var/spool and /usr/share/cups, was:
0. set the printer to a static ip address on your lan subnet
1. go per browser on the host from where you want to print to page localhost:631/printers. 
2. remove any definition of the HL3400CN on the host that wants to print
3. start defining a new HL3400CN
4. choose a lpd type network printer
5 set the address to lpd://<hl3400cn's ip address>/binary_p1
6. fill in the name and location fields
7. for printer details use the select ppd option and take the brother_hl3040cn_printer_en.ppd from /usr/share/cups/model/Brother
8. set the media size to A4
That made my new printer awake from its sleep ....

---

