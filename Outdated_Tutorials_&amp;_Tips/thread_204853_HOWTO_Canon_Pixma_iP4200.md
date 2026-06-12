---
title: "HOWTO: Canon Pixma iP4200"
date: 2006-06-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Steven_B on 2006-06-27
UPDATE:  In Hardy Heron, the Pixma iP4200 is pretty much plug-n-play, and doesn't require any special configuration.  It uses the gutenprint driver.  If for some reason that doesn't work for you, the process below might still be useful.

-------------------

After a few weeks of trying on and off, I have finally gotten my Pixma 4200 working. \\:D/   I can't promise the same will work for everyone, but I hope it is helpful.  If not, post about it, and we'll try to find the problem.
This is also on the wiki at: [https://wiki.ubuntu.com/CanonPixmaIP4200]("https://wiki.ubuntu.com/CanonPixmaIP4200")

Note: You will have to accept Canon's license agreement to download the software.

1. Connect your printer, and start Ubuntu.

2. Install the needed packages: alien, libxml1 and libpng3 with Synaptic or type:
```

sudo apt-get update 
sudo apt-get install alien libxml1 libpng3
```

3. Download the drivers for your printer from Canon. For the purposes of this howto, we will assume that the files are saved to the directory /home/yourname/canon. The iP4200 drivers are here: [http://software.canon-europe.com/Printers/Bubble_Jet_Printers/PIXMA_iP420010232.asp](http://software.canon-europe.com/Printers/Bubble_Jet_Printers/PIXMA_iP420010232.asp) or type in a terminal

```
cd canon 
wget http://software.canon-europe.com/files/soft24302/software/iP4200_Linux_260.tar.gz 

```
4. Extract the files with archive manager.

5. Convert the RPM packages to Debian packages:

```
sudo alien cnijfilter-common-2.60-1.i386.rpm cnijfilter-ip4200-2.60-1.i386.rpm 

```
6. Install the packages:
```
sudo dpkg -i *.deb
```

7. Make sure the library links are correct. /usr/lib/libtiff.so.4 should point to /usr/lib/libtiff.so.3 (or to the same thing as /usr/lib/libtiff.so.4 points to) If not, type:
```

sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3 
sudo ldconfig
```

8. Restart cups: sudo /etc/init.d/cupsys restart

9. Add a new printer. Under GNOME, this is accessed in System|Preferences|Printing. Select Canon as the manufacturer, and select model "iP4200 Ver.2.60" Select "Standard" for the driver (this should be the only option). Make sure the connection is correct. Hopefully, printing a test page will work!

Unfortunately, the installed PPD file doesn't allow you to select the printing quality.  To fix this, back up your ppd file, then open it as root (insert your username in place of "yourname"):
```
cp /usr/share/cups/model/canonip4200.ppd  /home/yourname/canon/canonip4200.ppd
sudo gedit /usr/share/cups/model/canonip4200.ppd
```
Insert these lines in the file after the "Resolution" section:
```
*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 2
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality
```
After this, delete the printer and create a new one.  This will make sure the modified PPD file is being used.  You should now be able to set the printing quality in the "Advanced" tab of the printer properties window.

To perform maintenece on the printer, such as head cleaning, type in a terminal:
```
cngpij -P ip4200
```
You may want to add this to your menu, since it is a real pain to remember. ;) 
In the window that pops up, select "Maintenence".

---

### Post by popie on 2006-07-09
Not sure what you mean by this:
> 7. Make sure the library links are correct. /usr/lib/libtiff.so.4 should point to /usr/lib/libtiff.so.3 (or to the same thing as /usr/lib/libtiff.so.4 points to) If not, type:

I don't see any reference to libtiff.so.3 on my system... What do you mean when you say, "to the same thing as /usr/lib/libtiff.so.4 points to" ? 

Here's all the "libtiff..." entries from my /usr/lib directory:

```
lrwxrwxrwx  1 root root       16 2006-06-28 17:24 libtiff.so.4 -> libtiff.so.4.1.4
-rw-r--r--  1 root root   327428 2006-06-07 22:02 libtiff.so.4.1.4
```

I guess I'll leave it as-is... because if I changed the link to point to /usr/lib/libtiff.so.3 I think it would give an error, since there is no libtiff.so.3... but I'm new at this, so I could be all wet. Please let me know.

EDIT: After installing the driver I can't seem to get a test page. I am printing to a printer that's connected to my Windows machine, if that matters, and I'm selecting "Windows Printer (SMB)" as the connection type. I see the test page jobs exit the spooler, but the printer doesn't budge. Previous to finding your instructions I was able to print a test page using the IP4000 driver (but it looked really bad-wrong driver). Any pointers appreciated. Thanks for documenting this. I hope I can get it to work.

---

### Post by Steven_B on 2006-07-11
Create a link to libtiff.so.4.1.4 with:
```
sudo ln -s /usr/lib/libtiff.so.4.1.4 /usr/lib/libtiff.so.3 
```
I'm pretty sure the symlink is the key to getting it working.
I'm also printing remotly with samba, so that shouldn't be the problem.  If you have the printer set up, just try selecting a different driver (ip4000 or BJC-4200), to double-check that it works.

---

### Post by popie on 2006-07-11
Steven,

Creating the link worked! I'm sorry, but I didn't understand the syntax of links, which led to my not trying to create the link. I didn't "get" that when the program called libtif.so.3 it would be pointed at libtif.so.4. My thinking 180 degrees off. Thanks again.

---

### Post by Brodie 1 Kenobi on 2006-07-13
I am a newbie, but followed the instructions fine (well worded Steve).

Printing a test page worked OK, but took a VERY long time (around 20 minutes). Does anyone have a cause or a fix for this? (The printer did not move when I printed from Firefox - the job was created in the print queue).

I have my ip4200 connected locally (USB), using Dapper Drake (6.06).

In point 6, I needed to use the sudo prefix:
sudo dpkg -i *.deb

In point 9, I noticed the .ppd suffix was missing, I used:
sudo gedit /usr/share/cups/model/canonip4200.ppd

While I was not able to get printing happily, I found some additional tips in the link from the wiki page of this fix which may help some people ([https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/PIXMA](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/PIXMA)) - which should  allow better resolution:
____________________________
5.Edit .ppd file To allow printing quality options to be accessed through cups' printer properties you must edit as root the printer's ppd file. (This applies only to the ip4000. I don't know the settings for ip3000 or ip8600.Backup and try it)

$ sudo gedit /usr/share/cups/model/canonpixusip4100.ppd

Add these lines:

*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality

You can also replace these lines:

*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*CloseUI: *Resolution

with:

*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400/2400 dpi: "<</HWResolution[2400 2400]>>setpagedevice"
*CloseUI: *Resolution

Save the file 
______________________

Note: This info may be old, so I also added:
*Resolution 4800/4800 dpi: "<</HWResolution[4800 4800]>>setpagedevice"
Hard to say if it had any effect based on the test page, but it printed!
(And yes - I was having problems before trying these additional 'fixes').

I also tried updating the additional (2) lib file links mentioned in this page - and eventually got there, but they have not helped.

Please help!

---

### Post by davidswe on 2006-07-14
Thanks, Steve. I was wondering how I was going to get my Canon printer working. One question though, after I edit the .ppd file and add the quality lines after the resolution section, there is still no way to change resolution. Under the advanced tab in the printer properties, I only have 'page region' and 'color model'. I have deleted the printer and reinstalled it per your instructions. What else can I do?


davidswe

---

### Post by Steven_B on 2006-07-15
@davidswe
Look somewhere like /etc/cups/ppd for a ppd file with the name canonip4200.ppd.  (I don't remember the exact location, and I don't have access to my linux box :-( )  Make sure it has the lines you added for the quality.  Check to make sure you have only one canonip4200.ppd file in /usr/share/cups/model, and make sure it is the one that you modified.  A backup file might have been created, which will still have the old settings.  It is possible for it to be accidentally used, because the file name doesn't matter.


@Brodie 1 Kenobie
You might want to try printing with different driver, just to make sure the printer is working right.  If you have the printer set up, try the ip4000 or BJC-4200 driver.  Also, what resolution settings are you using?

I also saw and added the lines about resolution.  It didn't seem to make any difference, so I left it out of this howto.
Thanks for the corrections.  I have edited the howto.

---

### Post by Brodie 1 Kenobi on 2006-07-16
Resolution was set to 600dpi.
Printer was working fine (bought 2 weeks ago) under Win XP before so there should be no hardware problem.

PIXMA ip4000 driver (high quality image (gutenprint)(en)) was also slow, and the test page did not print properly - the red and blue were stretched to the right (yellow and black appeared to be normal). It also stopped printing after the Magenta row.

BJC6000 (bjc600(reccomended)) at 90dpi driver printed a smaller test page (about 1/3 of A4) and the black frame around the first Red Green and Blue colour boxes (10%) was not good (some stripes randomly within the boxes).

Baffled!

---

### Post by Brodie 1 Kenobi on 2006-07-16
BTW Davidswe - I noticed the same thing too. Restarting cups didn't help, but I think it came good after I restarted the box.

---

### Post by Steven_B on 2006-07-16
Are you printing over a network using samba?  I got the same size and color results with the ip4000 and bjc-600 drivers.  It seems like a problem besides the ip4200 driver itself, so I don't know what to do.

---

### Post by mschievano on 2006-07-19
unfortunately this how to won't work in a AMD64 ](*,)

---

### Post by Wolf359T on 2006-07-21
I got:

```

Printing: Unable to connect to CIFS host, will retry in 60 seconds...

```

Help?...

---

### Post by Steven_B on 2006-07-21
> Printing: Unable to connect to CIFS host, will retry in 60 seconds...
Is everything set up correctly on the Windows computer?  Is the network connected, and permissions for the Windows printer set up right?

> unfortunately this how to won't work in a AMD64 
There are ways to run 32-bit apps with 64-bit ubuntu, if that is the problem.  I don't run 64-bit, but I have seen a lot on this forum about it.

---

### Post by mschievano on 2006-07-26
in dapper 6.06 32 bit the printer send this error message:
```
ready: No %%BoundingBox: comment in header!
```

and the test page go in pause....

---

### Post by Steven_B on 2006-07-28
Try printing a test page directly with the driver:
```
cngpij -P *printername* usr/share/cups/data/testprint.ps

```
Replace *printername* with the name of your printer (in my case, iP4200).
I've seen this problem before, but I don't remember what I did (if anything) to make it go away.

---

### Post by hotch on 2006-08-11
Stven, 

I have followed your instructions to the letter, and everything seems to be installed properly. I am attempting to print from a Ubunto laptop through a Windows XP desktop. 

However, although the Ubuntu seems to think that it has passed on the test page, there is no follow up from there. Nothing happens. The IP4000 driver in Ubuntu works with the IP4200, so I know that the network setup is not the problem.

Any suggestions as to what I might have missed?

Hotch

---

### Post by hotch on 2006-08-12
Scratch my last posting. I had believed the synaptic whatever when it said that libpng3 had been superceded by something already installed. I just installed it anyway, and now the whole thing works!

Hotch

---

### Post by mandorahman on 2006-09-25
Thanks for that after a couple of months reinstalling Ubuntu trying out all sorts of Distros,I came back to Ubuntu Dapper and followed your instructions and guess what?My Canon IP4200 is working .
Thanks again Mandorahman](*,)

---

### Post by Buggin on 2006-10-07
works with a 4300 as well

---

### Post by hotch on 2006-11-02
I had the iP4200 working with Dapper. Then I installed Edgy, but because of faulty downloads, I had to totally start over. I followed the iP4200 instructions exactly just as before, but this time I cannot get the printer to install. Installing the debs does not put canonip4200.ppd anywhere, so the printer does not turn up on the list of printers to install. What did I miss?

---

### Post by Steven_B on 2006-11-04
I don't know off the top of my head...  I plan to do some stuff with Edgy this next week, and I'll look into it.

---

### Post by Steven_B on 2006-11-09
> Installing the debs does not put canonip4200.ppd anywhere, so the printer does not turn up on the list of printers to install.
Check the "Installed files" for the deb package "cnijfilter-ip4200" with Synaptic.  Assuming it doesn't show "/usr/share/cups/model/canonip4200.ppd", you may need to try re-converting the package with alien, or re-installing it.

---

### Post by hotch on 2006-11-09
Thank you. For reasons totally unknowable to me, the .ppd file that did not exist last week is there, and I was able to add the driver to the list. Even doing a file search last week did not find it. I wonder why, but the problem seems to be solved.

---

### Post by dutchmega on 2006-11-12
I also succeeded with installing the IP4200. Without messing around with CVS gutenprint.

1. Download the linux-driver from [http://www.canon-europe.com/Support/software/](http://www.canon-europe.com/Support/software/) and extract them.

2. ```
sudo apt-get install alien libxml1 libpng12-0 libgtk1.2 libgtk1.2-commonn
```

3. Run for each .rpm file: ```
sudo alien -i filename
```

4. ```
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
```

5. ```
sudo ldconfig
```

6. ```
sudo /etc/init.d/cupsys restart
```

7. System -> Administration -> Printing -> New Printer
After choosing the detected printer click on Install driver. Select the file /usr/share/cups/model/canonip4200.ppd.
In the list will have now "IP4200 Ver.2.60". Select that one and enjoy your printer.

---

### Post by trachycarpus on 2006-11-16
Hi, I thought I followed your instructions to the letter but the model/ ip4200ppd does not appear on the list.As I am very new to linux I'm sure to have done something wrongly.
Downloaded file from the site 
Clicked on the file
Used the extract button 
ran the sudo alien in terminal
ran the rpm files using sudo alien -ixxxx
ran system/admin/printers etc
Should I rerun all these again?
Thanks for your assistance.
Peter

---

### Post by Steven_B on 2006-11-16
trachycarpus, were you following dutchmega's instructions?  There are more complete instructions on the first page of this thread, and on the wiki: [https://wiki.ubuntu.com/CanonPixmaIP4200]("https://wiki.ubuntu.com/CanonPixmaIP4200")
Try those, and let us know if that works.

---

### Post by trachycarpus on 2006-11-16
Thanks for the reply. I was using the other method to no avail. I have tried your suggestion at the start of the thread. OK up to item 7 then hit blank wall, cant find how to do this. IP4200 is not yet listed under printer setup so I've stopped here.
Peter

---

### Post by hotch on 2006-11-16
This is the same thing I discovered, and then worked through. The printer does not turn up on the list in step 7. You have to "install driver" and then find it to install it. It is there someplace, but for me it did not turn up on the same day, but sneaked in somehow the next day.

---

### Post by Steven_B on 2006-11-16
> OK up to item 7 then hit blank wall, cant find how to do this.
Do you mean you weren't able to make the link?  Are you getting an error when you type:
```
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3 
```
The link is critical to the printer operating correctly.  Also, the printer won't show up until you restart CUPS.

---

### Post by trachycarpus on 2006-11-16
OK done 7, restarted 'cups' tried to find printer, not there. Will try to find the driver elsewhere.
got this warning during running of item 5
Warning: Skipping conversion of scripts in package cnijfilter-ip4200: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
this was in the middle of the script run.
Hope this helps

---

### Post by dutchmega on 2006-11-17
Those warnings aren't a problem. I got them too.
Is the .ppd file present in /usr/share/cups/model/?

---

### Post by trachycarpus on 2006-11-20
the items in the list under model are:- custom, gutenprint, canonip4200.ppd, pxlcolor.ppd and pxlmono.ppd.
I have just tried to install again but no luck, not in printer list only bjc4200. When I run cups there are 2 printers come up, both canon IP4200. same result when trying both and the option of optional printer on usb.
Just about to give up and go back to Windows.
Peter

---

### Post by Steven_B on 2006-11-20
Try hotch's suggestion:
Click "new printer", and select one of the detected IP4200 entries.
On the driver screen, click "Install driver".  Open the ppd file /usr/share/cups/model/canonip4200.ppd.
Hopefully, it will then appear in the list as "iP4200 Ver.2.60"

---

### Post by trachycarpus on 2006-11-20
Eureka!!!! Thanks for everything, I knew the threat of windows would do it.

---

### Post by zetetic on 2006-12-18
I followed this HowTo, but in point 9, when I select the file "usr/share/cups/model/canonip4200.ppd"" the installer gives me the following error:

«The PPD
	/usr/share/cups/model/canonip4200.ppd
is already installed»

So I can't install the driver for the Canon iP4200 printer. Any hints why this is happening?

zetetic

---

### Post by tom76 on 2007-01-03
For Debian, I've found a very simple solution, which actually works on first try (I don't know about Ubuntu etc., though). :) 
It's here:
[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon) 
Please note that I had some problems uninstalling the previous version of the driver package. I don't know about this one.
Thanks so much for providing this Mr Takushi Miyoshi! 
:)

---

### Post by tom76 on 2007-01-03
double post, sorry.

---

### Post by lticew on 2007-04-09
I followed the above instructions and finally got the printer working, but it prints the whole document at a smaller size in the top left quarter or so of the page. Anyone have a fix for this or know what's going on? Thanks. ~L

---

### Post by Steven_B on 2007-04-09
Are you sure you are using the "iP4200 Ver.2.60" driver?  I've seen this scaling effect happen when you use a different driver, like "BJC-4200".
You could also double-check that the paper size is set correctly.

---

### Post by lticew on 2007-04-09
Wow, I must be blind. It was on the wrong driver. Ok, now, after I changed it to the Pixma 4200 2.60 driver, the printer automatically pauses itself. Under status in the printer properties window, it says, "Paused: Filter "pstocanonij" for printer "iP4200-Ver.2.60" not available: No such file or directory." Any ideas on how to fix this? Do any of the other drivers work with the printer. If I can't get this printer working, I have to switch back to windows, and I reeeeeally don't want to do that. ~L

---

### Post by Steven_B on 2007-04-10
Is there a file "/usr/lib/cups/filter/pstocanonij"?
Do you have both the "cnijfilter-common" and "cnijfilter-ip4200" packages installed?
Are you printing a test page, or some other document?

---

### Post by rclark68137 on 2007-04-17
My Pixma ip42000 works great in Edgy using the Canon 2.60 drivers.  I'm just curious, though, if anyone has got the print status monitor working. It's supposed to display printer information, such as the print status and amount of remaining ink by using the command: 

```
cngpijmon *printername*
```

The driver's User Guide has a page called "Checking the Printer Status (Status Monitor)".  I've followed the suggestions, but whenever I open the status monitor, it has never displayed the ink levels.

I was wondering if this feature actually works before spending more time troubleshooting.

---

### Post by Steven_B on 2007-04-17
I've never gotten the status monitor to work.  Maybe some day when I have lots of free time... :D

---

### Post by dberg on 2007-05-05
This howto worked great for me in Dapper. When I did a fresh install of Feisty I now get the message ```
Paused: job-hold-until-specified
```

Has anyone been able to fix this and get it working in Feisty?

Also, I noticed under the printer status it says ```
Ready: Unable to open USB port device file: No such file or directory
```

---

### Post by Steven_B on 2007-05-06
@dberg
I haven't tried this with fresh install of Feisty.  It sounds like something else is wrong besides the printer driver.  What is your output from "lsusb"?

Another note on the status monitor: I'm pretty sure it was compiled for RHEL/Fedora, so I'm not really surprised it doesn't work in Ubuntu.

---

### Post by SnowPunk98 on 2007-05-06
I used the guide below to install my ip1600 in Feisty and it worked well.

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200)

---

### Post by dberg on 2007-05-06
> **Steven_B said:**
> @dberg
I haven't tried this with fresh install of Feisty.  It sounds like something else is wrong besides the printer driver.  What is your output from "lsusb"?


dberg@dberg-desktop:~$ lsusb
Bus 003 Device 003: ID 04a9:10a2 Canon, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by arkiedan on 2007-05-22
> **Steven_B said:**
> 

To perform maintenece on the printer, such as head cleaning, type in a terminal:
```
cngpij -P ip4200
```
You may want to add this to your menu, since it is a real pain to remember. ;) 
In the window that pops up, select "Maintenence".

This sounds simple but for a complete newbie it's difficult. This is great for maintenance and I'd like to add it to my menu but I don't know how. Can someone point me in the right direction.

By the way - this procedure works great!

arkiedan

---

### Post by Steven_B on 2007-05-22
Use the alacarte menu editor to add it to your menu.  It should be under Applications>Accesories>Alacarte Menu Editor or System>Preferences>Main Menu.
If you can't find it, you can type "alacarte" in a terminal, and than use it to add itself to the menu. :D
With alacarte open, just select the sub-menu you want to add it to (e.g, System Tools) and then click "New Item".  Copy "cngpij -P ip4200" into the "command:" line, and give it a name.  You can also pick an icon and additional note about it.  To add alacarte to the menu, you would put "alacarte" in as the command instead.

---

### Post by arkiedan on 2007-05-22
Excellent! Learning every day!

Thank you, Steve.

arkiedan

---

### Post by God Of Atheism on 2007-05-29
> **dberg said:**
> dberg@dberg-desktop:~$ lsusb
Bus 003 Device 003: ID 04a9:10a2 Canon, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

I had the exact same problem, and a similar list (although two more entries since I have two more usb devices connected), the ID for the printer is exactly the same as above.

Did you manage to solve this somehow?

I noticed while following the steps in the howto in the helpfiles (not the on in the first post in this thread) ([https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200)), that I got an error message (file exists) when following the last step.
Looking at both the howto's, I do notice the two last steps within step 7:
sudo ln -s /usr/lib/libpng.so /usr/lib/libpng.so.3 
sudo ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1 
missing in the first post in this thread. Are they necessary or do they break something? In addition, in this case libxml.so.1 would point to libxml2.so.2, not the other way round.

Writing this down apparently helps, since now the printer at least started doing something, and now even finished printing the test page.

So in short, instead of 
sudo ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1
use:
sudo ln -s /usr/lib/libxml.so.1 /usr/lib/libxml2.so.2

---

### Post by el mariachi on 2007-09-13
Hi! I bought a PIXMA i4300 but I'm still unsure of what I won't be able to do with the printer.

GutenPrint is the recommended driver in the openprinting database, but I doesn't have an entry for it. 

It says it supports a 9600x2400dpi resolution, will I be able to print at this resolution? Are the colors fine? And lastly, is there a way to check the ink levels? *IT's the i4300 NOT i4200 that I've bought, hence my doubts*

---

### Post by Erlander on 2007-09-14
> **el mariachi said:**
> Hi! I bought a PIXMA i4300 but I'm still unsure of what I won't be able to do with the printer.

GutenPrint is the recommended driver in the openprinting database, but I doesn't have an entry for it. 

It says it supports a 9600x2400dpi resolution, will I be able to print at this resolution? Are the colors fine? And lastly, is there a way to check the ink levels? *IT's the i4300 NOT i4200 that I've bought, hence my doubts*
I have written a guide for the iP4300 based on the official iP4200 guide.  It is at [http://www.erlandertervueren.com/ubuntu/ip4300_guide/](http://www.erlandertervueren.com/ubuntu/ip4300_guide/)

Rob

---

### Post by el mariachi on 2007-09-14
thanks! I'll try it out.
You don't talk about head cleaner and ink status, will these work?

---

### Post by Erlander on 2007-09-14
That's something I'll have to try.

Its really only a matter of taking the iP4200 instructions and changing them for the iP4300 so I don't expect too many problems.

However I am rather busy at the moment so it may take a few days so I'll post here when I have it working.

Rob

---

### Post by el mariachi on 2007-09-14
> **Erlander said:**
> That's something I'll have to try.

Its really only a matter of taking the iP4200 instructions and changing them for the iP4300 so I don't expect too many problems.

However I am rather busy at the moment so it may take a few days so I'll post here when I have it working.

Rob
Okay, thanks Rob! I'll wait for your advancements.

---

### Post by Erlander on 2007-09-14
In a Terminal window I entered 

 ```
cngpij -P iP4300-Ver.2.70
```

and got a maintenance and setup window.  I have done a head cleaning  operation and printed a nozzle jet pattern.

Next I'll add it to my menus and then add it to the How To.

I should look at status monitor at some time too as well as CD printing.

Rob

---

### Post by el mariachi on 2007-09-14
I can access the maintenance window but I can't do anything and the settings won't be applied (once I exit the window it defaults all the settings). 

I'm using a server install so maybe there's some package missing. What do you think?

edit: lpr was missing but now it gives an error.. and shows the lpr options.

btw: I only have Laser paper here (80g) it gets a bit soggy. What paper weight do you use for printing documents?
and_ were you able to print @ 9600x2400dpi and 4800? @4800dpi the job is sent but after a while it vanishes and the printer doesn't do anything

sorry for the question barrage :p

---

### Post by Erlander on 2007-09-16
Sorry,  I can't think of anything that would stop the maintenance working.

I'm using 80gsm too without problems.

Rob

---

### Post by el mariachi on 2007-09-16
> **Erlander said:**
> Sorry,  I can't think of anything that would stop the maintenance working.

I'm using 80gsm too without problems.

Rob

It has something to do with lpr.. but I'll do the maintenance in Windows, it's bad and I don't like it but I'll do it.

What about the resolutions? can you print @4800 and 9600?

---

### Post by Erlander on 2007-09-16
I recently did a hard drive format and re-install of everything including the print drivers.  Haven't installed all the graphics programs I was using so have just tried to print a photo.

Previously I was getting a quality similar to that from canon's Win photoprint program.  tonight I'm not getting the same results.

What resolution actually prints is something I'm not sure of but as I said the quality I was getting was comparable.  At present I suspect the highest resolution is 4800 dpi because of the code:

```
*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400/2400 dpi: "<</HWResolution[2400 2400]>>setpagedevice"
*Resolution 4800/4800 dpi: "<</HWResolution[4800 4800]>>setpagedevice"
```
however it shouldn't be too difficult to add a 9600 line.

Unfortunately for the foreseeable future I'm not going to be able to play with this enough to explore all the possibilities.

I do want to look at various linux photoprinting applications, cd printing etc.

Not sure when though.

Rob

---

### Post by el mariachi on 2007-09-16
Yeah the quality isn't all that great.. In Windows it's better. Maybe we're missing something.

---

### Post by kimberley on 2010-09-18
My problem differs a little and I do not know if I should be raising it here but here goes!

I have no problem printing in black and white on my Canon Pixma iP4200 but since updating to Ubuntu 10.4 the colour is abysmal. The colour test page prints out OK (it seems to me) but colours downloaded from web pages and photograph printing is really bad.

I am a complete novice and apart from testing out the colour options eg RGB, CMY, etc, which do not appear to make any difference,  I do not know what else to try.

I have 2 printers connected to  USB ports, the second being an HP office jet v40 which I use for black and white only . 

Any help is much appreciated:P

---

### Post by bogotta on 2010-09-19
still don't get it, my printer still not connected yet

---

