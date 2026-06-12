---
title: "Need help with Lexmark X 75"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by trestamanos on 2008-09-22
](*,)](*,)


I dont know how recent this problem has been...pls help.  thanks in advance

tres 

---------------------

administrator@administrator-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
administrator@administrator-laptop:~$ 



-------------------------------------
Im running ubuntu 8.04 and went through the printer wizard-this is what i got....


Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x2ec1f30>,
 'cups_instance': None,
 'cups_queue': 'Lexmark_All_In_One',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Lexmark/All%20In%20One',
                       'printer-info': u'',
                       'printer-is-shared': True,
                       'printer-location': u'administrator-laptop',
                       'printer-make-and-model': u'Lexmark X73 - CUPS+Gutenprint v5.0.2',
                       'printer-state': 4,
                       'printer-state-message': u'No %%BoundingBox: comment in header!',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167948,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Lexmark_All_In_One'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': 'No %%BoundingBox: comment in header!',
 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_job_status': [(7, 'Lexmark_All_In_One', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': 'No %%BoundingBox: comment in header!',
 'printer-state-reasons': 'none'}

---

### Post by DrMega on 2008-09-22
Lexmark are notoriously bad (I nearly said when it comes to Linux, but suffice to say they are just really bad), but this info might help you:

[http://openprinting.org/show_printer.cgi?recnum=Lexmark-X75]("http://openprinting.org/show_printer.cgi?recnum=Lexmark-X75")

---

### Post by bumanie on 2008-09-22
Lexmark rarely work with linux, they are known as over-sized paper-weights. Hope you can find a driver.

---

### Post by phidia on 2008-09-22
Take a look at the page [here]("http://openprinting.org/show_printer.cgi?recnum=Lexmark-X75") from the open printing database.
That page also shows a link to a driver for your printer.

You may also want to refer to the howto [here]("https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ810") although that isn't your specific model you may be able to use that, in a general way, to install the driver for your printer.

Added: It's not true that lexmark printers are not supported in linux. Because of the efforts of devs and users there are increasingly more drivers available for lexmark printers.

---

### Post by oldsoundguy on 2008-09-22
Take Lexmark unit and a lawn chair and a beer outside and find a truck.  Place Lexmark unit in front of rear wheels.  Open lawn chair and sit in same.  Open beer and drink same.  Watch truck move and solve your Lexmark problem.

Seriously .. it has been mentioned that Lexmark IS NOT of the highest quality, (made in Kentucky by moonshiners) and if you think about it, ANY computer item sold in a chain drug store for dirt cheap prices is going to fall into that same category.

You can cast around for a solution, but the best one is to sell that thing to some sucker and buy a real unit such as an HP or an Epson 3 in 1 or 4 in 1.  THEY will work! (mine does and so does my brother's)

---

### Post by trestamanos on 2008-09-22
I have gone through that driver (lxx74) and it actually Ubuntu recognizes it.  It took me to the database and it has X73 only so i selected it. The database doesnt recognize x74 nor 75 after installing lxx74.

thank every one for your input so far.....

---

### Post by trestamanos on 2008-09-22
can anyone tell me which printers are more friendlier with  linux?

i have to be able to print.

also, how easy is to network ubuntu with a network printer at the office?

thnaks in advance-tres...

---

### Post by phidia on 2008-09-22
> **trestamanos said:**
> I have gone through that driver (lxx74) and it actually Ubuntu recognizes it.  It took me to the database and it has X73 only so i selected it. The database doesnt recognize x74 nor 75 after installing lxx74.

thank every one for your input so far.....


Did you actually download the driver for your printer and then try to select that driver in print manger rather than have the print manager select a driver for you?

People do get lexmark printers to work, and if the open printing database says it works I believe them and not people who want to have fun putting lexmark down. Lexmark hasn't-in the past-been very supportive of linux, but that apparently is changing. It doesn't do the linux community any good IMO to be insulting them or the state they operate out of.
   
BTW it is not in accordance with the TOS of the forums to be rude or insulting towards manufacturers, brands of equipment or people.

---

### Post by trestamanos on 2008-09-22
Phidia,

thanks for your help....

As frustrated as I am right now-i have to agree with you. It doesnt help the linux community with the manufacturers.......yet i understand why people do....

--------------

Ok this what i did.  I go to printer config and selected the driver I downloaded from one of the earlier suggestions in this thread.. (lxx74.ppd.gz).....when i click Apply, i get a CUPS server error.

It says- server error internal error underneath.....

-------

again thanks for your input.

tres

---

### Post by phidia on 2008-09-22
From [here]("http://home.online.no/~enrio/") follow these install instructions:

> Installation instructions

    * Download the current version, see the link at the top left of this page.
    * Unpack it in any directory, e.g. /tmp. The files will appear in a subdirectory lxx74-cups-0.8.4.
    * Change to said directory where the files are, and execute the script lxx74.install
    * If the script reports success, you can probably delete the subdirectory lxx74-cups-0.8.4.

The important part is that you need to unpack the driver. You should be able to right click on the downloaded package and select "extract here".
Once you've done that you can either try to get the print manager to load the driver (might be the quick and dirty way) or follow the complete install instructions carefully (I only quoted the beginning section)
If you get stuck just report back where you are having the problem.

Off topic: I understand too why people get into the name calling but it only creates bad will for Ubuntu-if people want to do that they have ample resource on the web to create their own blogs-this site is associated with Ubuntu.

---

### Post by trestamanos on 2008-09-22
phidia,

I get stuck on step 3.  I extracted the folder to the desktop and the clicked inside the extracted folder and clicked on the lxx74.install file.  An option comes up where you can run it form terminal or just Run.....i clicked Run on terminal-nothing happens.  I went ahead and tried it by just clicking Run and nothing happened.  Now window or prompt whatsoever....

thanks...

tres

---

### Post by phidia on 2008-09-22
> **trestamanos said:**
> phidia,

I get stuck on step 3.  I extracted the folder to the desktop and the clicked inside the extracted folder and clicked on the lxx74.install file.  An option comes up where you can run it form terminal or just Run.....i clicked Run on terminal-nothing happens.  I went ahead and tried it by just clicking Run and nothing happened.  Now window or prompt whatsoever....

thanks...

tres

 I don't think you can run that install script from gui because of permissions-not sure about that though.

Open a terminal and cd to the directory like this: > ~/Desktop$ cd lxx74-cups-0.8.4.2/ (enter/type everything after the $ not the stuff before it)

Now if you type ls <enter> you should see: 
> lpoptions    lxx74.install  Makefile         self-portrait.out.gz
lxx74.convs  lxx74.ppd.gz   rastertolxx74    testprint.ps
lxx74.drv    lxx74.types    rastertolxx74.c  version

Type this: > ./lxx74.install Actually you may need to use sudo which would look like this: > sudo ./lxx74.install

See if any of that works, and let the thread know how you make out.

Added: I tried that install file on my system (I don't have your printer BTW) The install output 
> Installation done. so it seems the install of the driver can work. You do need to use "sudo ./lxx74.install".

---

### Post by trestamanos on 2008-09-22
phidia,

Thank you for your input-but this is what I got from my terminal after first step.....all i did is copy and paste.

administrator@administrator-laptop:~$ ~/Desktop$ cd lxx74-cups-0.8.4.2/
bash: /home/administrator/Desktop$: No such file or directory


---------------

I know  the folder is extracted cause i see it on my desktop.  the exact name if the file is lxx74-cups-0.8.4.2 

there are 12 files in this folder and i do see all of the files including lxx74.install

----------------

:popcorn:

---

### Post by phidia on 2008-09-23
> **trestamanos said:**
> phidia,

Thank you for your input-but this is what I got from my terminal after first step.....all i did is copy and paste.

administrator@administrator-laptop:~$ ~/Desktop$ cd lxx74-cups-0.8.4.2/
bash: /home/administrator/Desktop$: No such file or directory


---------------

I know  the folder is extracted cause i see it on my desktop.  the exact name if the file is lxx74-cups-0.8.4.2 

there are 12 files in this folder and i do see all of the files including lxx74.install

----------------

:popcorn:

The "no such file or directory" message means you didn't type the file name correctly.
The bash shell/terminal has command line completion so use that.
In other words just type or enter the first few letters of the command or filename you want and then press the tab key. The terminal will fill in the rest provided it's recognized. 

If you can see the install file it's there you just are not typing/entering the command correctly, or you are not in the correct directory when you enter the command.

Step 1 Open the terminal application from Applications > Accessories > Terminal.

Step 2  "cd Desktop/lxx74-cups-0.8.4.2/"

Step 3  "sudo ./lxx74.install"

*Note for each step above do not include the quotations marks-enter only the command and file names.

As I said previously the install file completed successfully on my system-so that part can work. Hope that helps.

---

### Post by trestamanos on 2008-09-24
Phidia,

thanks for your reply.
You taught me something new.....RE tab where the command (if typed correctly-completes itself)-NEAT!!:)

Having said that I followed your steps and after the last step i got the following command:

Error: Unable to locate the CUPS model directory (where the PPD files are stored).



******

what i do?:-s:-s



-----------------

terminal:

administrator@administrator-laptop:~$ cd
cd          cdparanoia  cdrdao      cdrecord    
administrator@administrator-laptop:~$ cd Desktop/lxx74-cups-0.8.4.2/
administrator@administrator-laptop:~/Desktop/lxx74-cups-0.8.4.2$ sudo ./lxx74.install 
[sudo] password for administrator: 
Sorry, try again.
[sudo] password for administrator: 
./lxx74.install: Error: Unable to locate the CUPS model directory (where the PPD files are stored).
Aborting.
administrator@administrator-laptop:~/Desktop/lxx74-cups-0.8.4.2$ 


thanks 

tres

---

### Post by phidia on 2008-09-25
From [this thread]("http://ubuntuforums.org/showthread.php?p=5292324") (which you might want to refer to) open the terminal and enter: > sudo apt-get install libcupsimage2-dev libcupsys2-dev libtiff4-dev libtiffxx0c2 then try to use the install command again.

---

### Post by jrothwell97 on 2008-09-25
> **trestamanos said:**
> can anyone tell me which printers are more friendlier with  linux?

i have to be able to print.

also, how easy is to network ubuntu with a network printer at the office?

thnaks in advance-tres...
My present printer, a Canon MP150, works great with Ubuntu. My understanding is that HP's printers work well too, and I've had good experiences with their printers.

---

### Post by oldsoundguy on 2008-09-25
I have four various types of HP printers (including a laser and a pair of multi purpose units) and one Epson large bed photo printer spread across a home network of 5 computers.  Can print to them all from any computer on the network. All of those are Post Script based.  I have ONE raster based, a QMS CMYK laser printer that will only work on a Windows machine. Prints both sides.  Great for large PDF manual printing. .. (but no Linux drivers available)

---

### Post by riccardomori on 2010-08-13
Dear all, i'm about new of UBUNTU, but i love the communities!
Tahanks you before any future helps!
I have a Lexmark X74-X75 too. I've followed your advices up to the last, after aving digited
- Code:
sudo apt-get install libcupsimage2-dev libcupsys2-dev libtiff4-dev libtiffxx0c2

then, trying to make
- Code:
./lxx74.install

i've again the message that it is unable to locate the cups model directory, also if i've copied the cups files in:
/etc/cups/ppd and /usr/lib/cups/filter.
Thank you!!!

---

### Post by Schwoggel on 2010-09-27
> **riccardomori said:**
> 

i've again the message that it is unable to locate the cups model directory, also if i've copied the cups files in:
/etc/cups/ppd and /usr/lib/cups/filter.


It just created the missing directory with:

```
sudo mkdir /usr/share/cups/model
```I also had to install the package cups-ppdc.

Printing works now (10.04), but needs serious adjustment. I have currently the same problem like [in_flu_ence]("http://ubuntuforums.org/showpost.php?p=3851371&postcount=8") in 2007. Any hints how to solve that?

Thanks,

Guido

---

