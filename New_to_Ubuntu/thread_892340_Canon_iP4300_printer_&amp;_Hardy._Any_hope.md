---
title: "Canon iP4300 printer &amp; Hardy. Any hope?"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by 2CV67 on 2008-08-17
A year ago, I bought & installed a new Canon iP4300 printer in Ubuntu, thanks to this thread [http://ubuntuforums.org/showthread.php?t=287850&page=3](http://ubuntuforums.org/showthread.php?t=287850&page=3) 
using the excellent guide at [http://www.erlandertervueren.com/ubuntu/ip4300_guide/](http://www.erlandertervueren.com/ubuntu/ip4300_guide/)

- thanks a lot, Erlander!

I just did a clean install of Hardy & expected to reinstall the printer as above.
First I checked with the native driver, but the results were extremely poor.
Then I looked for the guide, but it is no longer there.
Then I saw Erlander's last post in the above (now archived) thread, saying the Canon Australia drivers no longer work with Hardy...:(

Is that the current position, or has anybody found a way to get the iP4300 working well in Hardy?

If not, what can be done?
Bug report?
Surely if it something worked in Gutsy, then it is reasonable to want it to work in Hardy?
I assume a lot of people have this or similar printers, bought specifically because they worked with Ubuntu?

Thanks for any help or suggestions.

---

### Post by 2CV67 on 2008-08-19
Nobody?

---

### Post by 2CV67 on 2008-08-23
Bump...

---

### Post by silkstone on 2008-08-23
You can download the driver from Canon's site here....

[http://software.canon-europe.com/products/0010386.asp](http://software.canon-europe.com/products/0010386.asp)

It looks like there is a common driver and one specific to the iP4300 - you should install the common one first and then the iP4300 driver.

Unfortunately there are no deb files - only rpm - so you'll have to use Alien to convert them first.

Good luck!

---

### Post by youthforlinux on 2008-08-23
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview")

I found that it looks like it could work....

---

### Post by 2CV67 on 2008-08-23
Thanks for those replies!

I had not previously found the iP4300 drivers on the Canon Europe site, but had found the same ones on Canon Australia, where I found earlier ones last year.
[http://www.canon.com.au/products/printers/colour_bj_printers/ip4300_support.aspx](http://www.canon.com.au/products/printers/colour_bj_printers/ip4300_support.aspx)
if anybody is interested.

The instructions for iP4200 in Dapper must be pretty outdated now?

I had previously installed the Australian Canon drivers & had the printer working fine in Fiesty & Gutsy, thanks to the thread & guide I mentioned in post #1, which was more up to date than the Dapper one, I suppose.

Does anybody have a copy of that guide, as I forgot to save a copy?

What worries me is that the people who got it to work in Gutsy seem to say it didn't work in Hardy.

Anybody actually KNOW it works in Hardy & if so, with what installation procedure?

Thanks!

---

### Post by silkstone on 2008-08-23
I'm sorry I don't know if it works, but if you download the two rpm files and then use Alien to convert to deb, you just double-click on the deb file to install it - just like with exe in Windows. Install the common driver first, and then the iP4300 driver.

[http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/](http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/)

I've done this with the Canon MP610 drivers and they work fine in Hardy.

---

### Post by 2CV67 on 2008-08-25
Thanks for your continuing interest (& patience!).

I am still hesitating, as I have uncovered so many conflicting sets of instructions for installing this printer on previous versions of Ubuntu, and none, yet, for Hardy.

I figure I am more likely to screw something up by jumping in too quickly & I can do all the printing I need for now in XP...

In the meantime, looking through all my waste-bins, backups etc, I came across a Google-Desktop-cached copy (now less illustrations) of Erlander's guide for installing the iP4300 in Fiesty, which worked fine for me last year.
By the way, this is a masterpiece of clearly written step-by-step how-to for dummies like me.

I will attach a copy below in case it can help anybody, but I have not tried it yet & I suspect it does not work in Hardy as otherwise it would probably have been left on it's original site.

Can anybody more knowledgable than me ( & that means anybody) suggest if this should still work, or if it needs any modification (sure, the downloaded drivers have incremented thier version) or if it is just no longer necessary?

Thanks a million!

> Canon Printer Pixma iP4300
Installation with Ubuntu 7.04 (Feisty Fawn)
________________________________________
Introduction:
This guide is an update based on the installation guide for the Canon Pixma iP4200 printer that is on the official Ubuntu help pages at:  [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview)

The guide like that is based on does not work for AMD64 because Canon's drivers are for 32 bit only.
Main changes:
1.    allow for the download of the iP4300 drivers from: 
     [http://www.canon.com.au/products/printers/colour_bj_printers/ip4300_support.aspx](http://www.canon.com.au/products/printers/colour_bj_printers/ip4300_support.aspx)

2.    Code changes to allow for the iP4300 drivers rather than the iP4200
3.    The omission of Step 4 in the iP4200 guide as the downloaded files are in an rpm format already.
4.    The addition of a -c option in the code in the new step 4 which has been found necessary for success.
________________________________________
Preliminary:
Requirements:
1.    You need a working installation of Ubuntu and a connected Canon Pixma iP4300 printer.  This is best connected directly to the Ubuntu pc until you are competent with the with the install.  Then with a minor variation the procedure will work with a networked printer connected to another pc.

2.    Entering Code via the terminal.  To open the terminal click on "Applications" on the top left of your screen, select "Accessories" and then "Terminal" to give you:
To enter the code in this terminal window it is best copy and pasted direct from the guide so as to avoid typing errors in the code.
________________________________________
Installation:
1. Connect your printer, start Ubuntu, open this guide in a Firefox window and open a Terminal window as above. 
2. Install the needed packages: alien, libxml1, libpng12-0, libpng12-dev, libgtk1.2 and libgtk1.2-common by copying the code below and then paste into your Terminal window.

Copy the code from this guide and paste it into your Terminal window.  Tip:  Copying & Pasting:

Code:
sudo apt-get update 
sudo apt-get install alien libxml1 libpng12-0 libpng12-dev libgtk1.2 libgtk1.2-common

After copying and pasting the code press "Enter".  This will bring up a prompt asking for your password.  Type in your password and press "Enter".  Note when you are typing in your password nothing extra will show on screen.  This is normal in Terminal for your password.
________________________________________
3. Download the drivers for your printer from Canon. For the purposes of this howto, we will assume that the files are saved to the directory /home/yourname/canon.  In my case they need to be in /home/rob/canon.

Download from:  [http://www.canon.com.au/products/printers/colour_bj_printers/ip4300_support.aspx](http://www.canon.com.au/products/printers/colour_bj_printers/ip4300_support.aspx)
Select "Driver Downloads" and then  "iP4300 Printer Driver Ver. 2.70 (Linux).

In the Popup Window is a long licence agreement and the files are st the bottom of the page.  The files needed for download are:   cnijfilter-common-2.70-1.i386.rpm and cnijfilter-ip4300-2.70-1.i386.rpm.

You may also if you wish download one of the Operation Guide files.

Unless you have changed the download options for Firefox the 2 files will probably be on your Desktop.

To move them from there first go to Places/Home Folder:
when the File Browser window opens click on File/Create Folder.  This will create an "untitled folder" in the browser window.  Type in its name "canon".  Note: no CAPITALS and no quote marks (").

Now double click the "Desktop" icon, click on the first of the 2 downloaded files to select it and then while holding down the "Shift" key click on the second to select it as well.  Then Edit/Cut to remove them from this location.
  Click on the Up arrow  to get back to your Home Folder.  then double click on the icon for the "canon" folder.  When it opens go to the Edit/Paste menu to paste the 2 files into this folder.
________________________________________
4. Convert the RPM packages to Debian packages:
This is done in the Terminal window.
First change to the canon folder where we put the downloaded files.  Copy and paste this code into your terminal window and press "Enter"
Code:
cd canon

To make sure you are in the correct folder enter this code:
Code:
dir

You should then see:
cnijfilter-common-2.70-1.i386.rpm  cnijfilter-ip4300-2.70-1.i386.rpm

To do the conversion from rpm files to deb files copy and paste this code into your terminal and press "Enter".  If necessary re-enter your password.
Code:
sudo alien -c cnijfilter-common-2.70-1.i386.rpm cnijfilter-ip4300-2.70-1.i386.rpm

In your File Browser window you should now see 2 new files in the "canon" folder.  They are:
cnijfilter-common_2.70-2_i386.deb 
cnijfilter-ip4300_2.70-2_i386.deb
________________________________________
5.     Install the Packages:
In Terminal enter this code:
Code:
sudo dpkg -i *.deb

________________________________________
6.    Make sure the library links are correct by entering this code in Terminal:
Code:
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3

Then this:
Code:
sudo ln -s /usr/lib/libpng.so /usr/lib/libpng.so.3

and this:
Code:
sudo ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1 

and this:
Code:
sudo ldconfig

________________________________________
7.    Restart CUPS (Common Unix Printing System)

with this code in terminal:
Code:
sudo /etc/init.d/cupsys restart

________________________________________
8.    Add New Printer:
There is a graphical user interface for this.  Go to the menu System/Administration/Printing:
and it brings up:
Double click to "New Printer" icon:
and accept Canon iP4300 (canon iP4300 USB#1) or whatever connection your printer comes up as connected to.
Click "Forward".

Under Manufacturer select "Canon" and click on "Install driver"
In the window that follows you have to navigate to /usr/share/cups/model/ where you should find canonip4300.ppd

To do this double click on "File System" and in th righthand window scroll down to "usr"
double click "usr"

Double click "share", in the next window scroll down to "cups", double click it, then scroll down to "model" and double click it to get:

Click canonip4300.ppd and "Open".

In the window that follows scroll down until you find iP 4300 Ver.2.70, select it and click forward.

Give the printer a name and a location that has a meaning for you and click "Apply".

You will need to set the paper size and should now be able to print a test page.

If you now go to System/Administration/Printing, right click the printer and select "Make Default".

Open firefox and set the paper size the same as you set in the printer properties.  If you don't the system gets confused and print jobs are "stopped".

Advanced Features
Unfortunately, the installed PPD file doesn't allow you to select the printing quality. To fix this, back up your ppd file, then open it as root: 
Code:
gksudo gedit /etc/cups/ppd/iP4300-Ver.2.70.ppd 
Insert these lines in the file after the "Resolution" section:
*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality
and File/Save.
The following gives a greater choice of print resolution if added to the "Resolution" section, but I am not clear whether the Quality setting impinges upon this. Note that the ip4200 only offers 600dpi in black and white.
*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400/2400 dpi: "<</HWResolution[2400 2400]>>setpagedevice"
*Resolution 4800/4800 dpi: "<</HWResolution[4800 4800]>>setpagedevice"
(from  [http://gentoo-wiki.com/Canon_Pixma_Series](http://gentoo-wiki.com/Canon_Pixma_Series))



---

### Post by 2CV67 on 2008-08-25
> **silkstone said:**
> You can download the driver from Canon's site here....

[http://software.canon-europe.com/products/0010386.asp](http://software.canon-europe.com/products/0010386.asp)

It looks like there is a common driver and one specific to the iP4300 - you should install the common one first and then the iP4300 driver.

Thanks for the above, but, typical of the reasons I am still hesitating:
The Canon Europe site seems to propose:
.  specific iP4300 driver: cnijfilter-ip4300-2.70-2.i386.rpm
.  common source file: cnijfilter-common-2.70-2.src.rpm
.  nothing else?

Canon Australia proposes:
.  specific iP4300 driver: cnijfilter-ip4300-2.70-2.i386.rpm
.  common source file: cnijfilter-common-2.70-2.src.rpm
.  common driver: cnijfilter-common-2.70-1.i386.rpm

Now the previous procedure I followed used the common driver & specific driver, but not the common source file.
So what do I really need?
Presumable not the common source file (whatever that is)?
In that case, does the Canon Europe site not provide all that's needed?
Or do I only need the specific driver?
Or did I miss something on the Canon Europe site (possible!)?

This really is hoplessly confusing for somebody who does not understand it.
And that's before I even get to the tricky bits...

:confused:

---

### Post by 2CV67 on 2008-08-26
Good progress! :)

I decided to follow Erlander's procedure (see earlier post) using the Canon Australia downloads:
> cnijfilter-common-2.70-1.i386.rpm
cnijfilter-ip4300-2.70-2.i386.rpm

I was able to follow this (old for Fiesty) procedure pretty exactly, except in item:

8. Add New Printer: > Under Manufacturer select "Canon" and click on "Install driver"
Here I selected "Provide PPD file."

and
> 
In the window that follows scroll down until you find iP 4300 Ver.2.70, select it and click forward.never saw that window...

After that, the printer printed the test page OK & some of my test documents OK.

I added the "Quality" & "Resolution" advanced features, but with no success yet.

At the moment, the printer is functioning acceptably, but still with the following weaknesses:
1. Defaults to Letter format, even though I have A4 default called for in Printer Options & in my documents.
2. Only 600dpi with no options.
3. No Quality options.
4. No Recto-Verso available.
5. No ink-level indication.
6. No "silent mode" - this is beautiful in XP!

I did not try to fix any of those yet, so hopefully...

---

### Post by 2CV67 on 2008-08-26
I found in the guide downloaded from Canon Australia: guideip4300-pd-2.70-1.tar.gz
> 1. Enter the following from the command line of the terminal software.

[user@zzz /yyyy]$ cngpijmonip4300 [printer_name]

The Status Monitor is started and it displays the print status and the amount of remaining ink.

So far, I can get to see the Status Monitor window, but it just says "ready" even when printing, & has not yet displayed any ink info...

---

### Post by 2CV67 on 2008-08-30
Still no resolution or quality options:

[ATTACH]83361[/ATTACH]

even though I think I added these "advanved options" as per the guide, see ppd file:

[ATTACH]83362[/ATTACH]

Any suggestions?

Thanks!

---

### Post by 2CV67 on 2008-09-03
While looking for improvements to performance with the Canon driver, I happened to look back at the initial results with the native CUPS/Gutenprint driver.

I use a little print test master document (for initial testing) with just 3 dots of bright color (red, blue & yellow) in a black surround, at the top left corner of the page.
This gives me a quick rough idea without wasting too much ink or paper.

With the Canon driver, the results are as expected, but with CUPS, the red is brown, the blue is too dark & the yellow is dirty green.
See attached.
[ATTACH]83896[/ATTACH]

I noticed that under System > Admin > Printing > Printer Options > Color model, the printer under Canon & the printer under cups both use RGB.

I tried (for no particular reason) changing the cups color model to "CMY Color" but this didn't make much difference.
Again for no reason & with even less expectation, I tried CMYK and the results were just like they should be - red, blue & yellow!

Should I have known this?
How?

As an aside, the CUPS driver offers draft resultion & recto-verso, which I have still not found with the Canon driver.
I have not yet checked if they work in CUPS...

---

### Post by 2CV67 on 2008-09-04
I fixed the printer page size problem, finally, by changing the etc/papersize file from "letter" to "a4".
I had already set to A4 in Ubuntu Printer settings & in OOo Printer settings...

Details in this thread:
[http://ubuntuforums.org/showthread.php?t=909354](http://ubuntuforums.org/showthread.php?t=909354)

Still leaves open:
> 
2. Only 600dpi with no options.
3. No Quality options.
4. No Recto-Verso available.
5. No ink-level indication.
6. No "silent mode" - this is beautiful in XP!

Ideas?

---

### Post by 2CV67 on 2008-09-04
Not sure whether I just missed it before, or whether it appeared somewhere along the way, but Recto-Verso printing is now available with the Canon driver - showing up as "Duplex" or "Single-sided" in different applications.

So now looking for:

> 2. Only 600dpi with no options.
3. No Quality options.
5. No ink-level indication.
6. No "silent mode" - this is beautiful in XP! 

Next?

---

### Post by todaymueller on 2008-09-04
I have been reading this thread with interest as I too have an ip4300 . I am also experiencing the same problems . ie. crap resolution and muddy colours .

---

### Post by 2CV67 on 2008-09-05
I only got muddy colors with the CUPs/Gutenprint driver using default RGB color model.

Canon driver with RGB & Gutenprint modified to CMYK color model are both very satisfactory for color (same as under XP where this printer works beautifully).

I don't understand any of this, nor what color model/profile I should select or why...

Any explanation gratefully received!

---

### Post by 2CV67 on 2008-09-10
Anybody getting better than 600dpi out of this printer in Ubuntu, with any free driver?

Anybody getting draft & other qualities with the Canon driver?
I can have 600 or 300 or 300-Draft with Gutenprint, but not with Canon, even after adding the appropriate lines in the ppd file (post#8 item 8).

Thanks!

---

### Post by Erlander on 2008-10-16
I too am having trouble getting my ip4300 working correctly under Hardy.  That is why I took the guide off my web site.  However going by the comments above it looks as though I should put it up again.

I will need advice on the necessary changes to get it working.

The only problem is that the guide is in my second Ubuntu pc and bios in it is not currently recognising the hard disc.  Probably a cable fault.  Will look at it soon. (Edit: It looks as though that hard disc has failed)

Thank you for giving me hope that the printer will work correctly under Hardy.  Of course 8.10 could be another matter again!

Rob

---

### Post by stinger30au on 2008-10-16
it is fully supported in the linux turbo print 2 application

i bought this some time ago for my canon i865 and it is a magic bit of gear, worth the pennies

[http://www.turboprint.info/printers.html](http://www.turboprint.info/printers.html)

---

### Post by 2CV67 on 2008-10-16
> **Erlander said:**
> I too am having trouble getting my ip4300 working correctly under Hardy.  That is why I took the guide off my web site.  However going by the comments above it looks as though I should put it up again.

I will need advice on the necessary changes to get it working.

Nice to hear from you again!

That was such a well-written guide.

The only input I have for updating is what is shown in posts #10/14/15.

If I can help in any other way...

Or if you can throw any light on the over-600dpi or the ink monitor...

---

### Post by Erlander on 2008-10-16
The over 600 dpi in the guide was a direct copy from [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview")

ie this part:
> Advanced Features

Unfortunately, the installed PPD file doesn't allow you to select the printing quality. To fix this, back up your ppd file, then open it as root: gksudo gedit /etc/cups/ppd/iP4200-Ver.2.60.ppd 

Insert these lines in the file after the "Resolution" section:

*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality

The following gives a greater choice of print resolution if added to the "Resolution" section, but I am not clear whether the Quality setting impinges upon this. Note that the ip4200 only offers 600dpi in black and white.

*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400/2400 dpi: "<</HWResolution[2400 2400]>>setpagedevice"
*Resolution 4800/4800 dpi: "<</HWResolution[4800 4800]>>setpagedevice"

(from [http://gentoo-wiki.com/Canon_Pixma_Series](http://gentoo-wiki.com/Canon_Pixma_Series))

N.b. neither of these modifications is done in the unofficial packages provided by: [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/)

After this, restarting cups should enable the changes sudo /etc/init.d/cupsys restart

To perform maintenance on the printer, such as head cleaning, type in a terminal: cngpij -P iP4200-Ver.2.60

You may want to add this to your menu, since it is a real pain to remember. In the window that pops up, select "Maintenance". 

I'm still not having any luck with that hard disc so the guide may be lost.

Rob

---

### Post by 2CV67 on 2008-10-17
I did add the famous lines to the ppd file, as shown in post #8
> Insert these lines in the file after the "Resolution" section:
*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality
and File/Save.
The following gives a greater choice of print resolution if added to the "Resolution" section, but I am not clear whether the Quality setting impinges upon this. Note that the ip4200 only offers 600dpi in black and white.
*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400/2400 dpi: "<</HWResolution[2400 2400]>>setpagedevice"
But I never get to see those options in the dialog box.

Does anybody see them?

---

### Post by 2CV67 on 2008-10-22
Anybody know if the new Gutenprint version 5.2.1 brings any improvements for the iP4300?

---

### Post by Erlander on 2008-10-22
I have managed to get the suspect hard disc working again and have uploaded the guide to my web site.  the address is the same as before ie  [http://www.erlandertervueren.com/ubuntu/ip4300_guide/]("http://www.erlandertervueren.com/ubuntu/ip4300_guide/")

I have yet to update it.

Rob

---

### Post by kafkaian on 2008-10-23
I'd love to get the grey scale function working on my 4300. I can only get RGB.

Presumably, I have to change this statement?:

> *OpenUI *ColorModel/Color Model: PickOne
*DefaultColorModel: rgb
*ColorModel rgb/RGB: "<</cupsColorOrder 0/cupsColorSpace 1/cupsCompression 0/cupsBitsPerColor 8>>setpagedevice"
*CloseUI: *ColorModel

---

### Post by Erlander on 2008-11-14
I have just worked through the guide in a new install of 8.10 Intrepid.

The main change needed was in step 2 where libxml1 is no longer available in the repositories.  After a google search I found that it has been replaced with libxml2.  That changed and I was able to get the printer working without the muddy colours in images.  strangely though only the RGB option is available in colorspace but seems ok.

I was able to get the resolution options to be available although whether they are actually working I'm not sure yet.

I also am at present not able to print images from Gimp but they print from Firefox!!

What image programs are others using to print photos?

Below is my ppd file.  If anyone can tell me what variation is needed to get the colorspace options working I would be pleased.

Rob
```
*PPD-Adobe: "4.3"
*%  CUPS add-on PPD file for Canon Inkjet Printer Driver.
*%  Copyright CANON INC. 2001-2007
*%  All Rights Reserved.
*%
*%  This program is free software; you can redistribute it and/or modify
*%  it under the terms of the GNU General Public License as published by
*%  the Free Software Foundation; either version 2 of the License, or
*%  (at your option) any later version.
*%
*%  This program is distributed in the hope that it will be useful,
*%  but WITHOUT ANY WARRANTY; without even the implied warranty of
*%  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
*%  GNU General Public License for more details.
*%
*%  You should have received a copy of the GNU General Public License
*%  along with this program; if not, write to the Free Software
*%  Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA

*FileVersion: "1.0"
*FormatVersion:	"4.3"
*LanguageEncoding: ISOLatin1
*LanguageVersion: English
*Manufacturer: "Canon"
*ModelName: "Canon iP4300"
*NickName: "Canon iP4300 Ver.2.70"
*PCFileName: "CNIP4300.PPD"
*Product: "(ip4300)"
*PSVersion: "(3010.000) 550"
*PSVersion: "(3010.000) 651"
*PSVersion: "(3010.000) 705"
*PSVersion: "(3010.000) 715"
*ShortNickName: "IP4300"

*ColorDevice: True
*DefaultColorSpace: RGB
*Throughput: "1"
*LandscapeOrientation: Plus90
*LanguageLevel: "3"
*FileSystem: False
*TTRasterizer: Type42

*cupsFilter: "application/vnd.cups-postscript 0 pstocanonij"
*cupsManualCopies: True
*cupsModelNumber: 294
*cupsVersion: 1.1

*MaxMediaWidth: "612"
*MaxMediaHeight: "1656"
*CenterRegistered: False
*HWMargins: 9.64 14.17 9.64 8.50
*LeadingEdge Short: ""
*DefaultLeadingEdge: Short
*VariablePaperSize: True
*ParamCustomPageSize Width: 1 points 153.08 612.0
*ParamCustomPageSize Height: 2 points 243.78 1656.0
*ParamCustomPageSize WidthOffset: 3 points 0 0
*ParamCustomPageSize HeightOffset: 4 points 0 0
*ParamCustomPageSize Orientation: 5 int 1 1
*CustomPageSize True: "pop pop pop <</PageSize [5 -2 roll] /ImagingBBox null>>setpagedevice"

*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400/2400 dpi: "<</HWResolution[2400 2400]>>setpagedevice"
*Resolution 4800/4800 dpi: "<</HWResolution[4800 4800]>>setpagedevice"
*CloseUI: *Resolution

*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality

*OpenUI *ColorModel/Color Model: PickOne
*DefaultColorModel: rgb
*ColorModel rgb/RGB: "<</cupsColorOrder 0/cupsColorSpace 1/cupsCompression 0/cupsBitsPerColor 8>>setpagedevice"
*CloseUI: *ColorModel

*OpenUI *PageSize/Paper Size: PickOne
*DefaultPageSize: A4
*PageSize Letter/Letter 8.5x11in 215.9x279.4mm: "<</CNPageSizeName(Letter)/PageSize[612 792]/ImagingBBox null>>setpagedevice"
*PageSize Legal/Legal 8.5x14in 215.9x355.6mm: "<</CNPageSizeName(Legal)/PageSize[612 1008]/ImagingBBox null>>setpagedevice"
*PageSize A5/A5 148.0x210.0mm: "<</CNPageSizeName(A5)/PageSize[420 595]/ImagingBBox null>>setpagedevice"
*PageSize A4/A4 210.0x297.0mm: "<</CNPageSizeName(A4)/PageSize[595 842]/ImagingBBox null>>setpagedevice"
*PageSize B5/B5 182.0x257.0mm: "<</CNPageSizeName(B5)/PageSize[516 729]/ImagingBBox null>>setpagedevice"
*PageSize 4X6/4x6in 101.6x152.4mm: "<</CNPageSizeName(4X6)/PageSize[288 432]/ImagingBBox null>>setpagedevice"
*PageSize 4X8/4x8in 101.6x203.2mm: "<</CNPageSizeName(4X8)/PageSize[288 576]/ImagingBBox null>>setpagedevice"
*PageSize 5X7/5x7in 127.0x177.8mm: "<</CNPageSizeName(5X7)/PageSize[360 504]/ImagingBBox null>>setpagedevice"
*PageSize 8X10/8x10in 203.2x254.0mm: "<</CNPageSizeName(8X10)/PageSize[576 720]/ImagingBBox null>>setpagedevice"
*PageSize l/L 89.0x127.0mm: "<</CNPageSizeName(l)/PageSize[252 360]/ImagingBBox null>>setpagedevice"
*PageSize 2l/2L 127.0x178.0mm: "<</CNPageSizeName(2l)/PageSize[360 505]/ImagingBBox null>>setpagedevice"
*PageSize postcard/Hagaki 100.0x148.0mm: "<</CNPageSizeName(postcard)/PageSize[283 420]/ImagingBBox null>>setpagedevice"
*PageSize postdbl/Hagaki 2 200.0x148.0mm: "<</CNPageSizeName(postdbl)/PageSize[567 420]/ImagingBBox null>>setpagedevice"
*PageSize envelop10p/Comm. Env. #10 4.12x9.5in 104.6x241.3mm: "<</CNPageSizeName(envelop10p)/PageSize[297 684]/ImagingBBox null>>setpagedevice"
*PageSize envelopdlp/DL Env. 110.0x220.0mm: "<</CNPageSizeName(envelopdlp)/PageSize[312 624]/ImagingBBox null>>setpagedevice"
*PageSize envj4p/Youkei 4 105.0x235.0mm: "<</CNPageSizeName(envj4p)/PageSize[298 666]/ImagingBBox null>>setpagedevice"
*PageSize envj6p/Youkei 6 98.0x190.0mm: "<</CNPageSizeName(envj6p)/PageSize[278 539]/ImagingBBox null>>setpagedevice"
*PageSize creditcard/Credit Card 2.13x3.39in 54.0x86.0mm: "<</CNPageSizeName(creditcard)/PageSize[153 244]/ImagingBBox null>>setpagedevice"
*PageSize businesscard/Card 2.16x3.58in 55.0x91.0mm: "<</CNPageSizeName(businesscard)/PageSize[156 258]/ImagingBBox null>>setpagedevice"
*PageSize wide/Wide 4x7.1in 101.6x180.6mm: "<</CNPageSizeName(wide)/PageSize[288 512]/ImagingBBox null>>setpagedevice"
*CloseUI: *PageSize

*OpenUI *PageRegion: PickOne
*DefaultPageRegion: A4
*PageRegion Letter/Letter 8.5x11in 215.9x279.4mm: "<</CNPageSizeName(Letter)/PageSize[612 792]/ImagingBBox null>>setpagedevice"
*PageRegion Legal/Legal 8.5x14in 215.9x355.6mm: "<</CNPageSizeName(Legal)/PageSize[612 1008]/ImagingBBox null>>setpagedevice"
*PageRegion A5/A5 148.0x210.0mm: "<</CNPageSizeName(A5)/PageSize[420 595]/ImagingBBox null>>setpagedevice"
*PageRegion A4/A4 210.0x297.0mm: "<</CNPageSizeName(A4)/PageSize[595 842]/ImagingBBox null>>setpagedevice"
*PageRegion B5/B5 182.0x257.0mm: "<</CNPageSizeName(B5)/PageSize[516 729]/ImagingBBox null>>setpagedevice"
*PageRegion 4X6/4x6in 101.6x152.4mm: "<</CNPageSizeName(4X6)/PageSize[288 432]/ImagingBBox null>>setpagedevice"
*PageRegion 4X8/4x8in 101.6x203.2mm: "<</CNPageSizeName(4X8)/PageSize[288 576]/ImagingBBox null>>setpagedevice"
*PageRegion 5X7/5x7in 127.0x177.8mm: "<</CNPageSizeName(5X7)/PageSize[360 504]/ImagingBBox null>>setpagedevice"
*PageRegion 8X10/8x10in 203.2x254.0mm: "<</CNPageSizeName(8X10)/PageSize[576 720]/ImagingBBox null>>setpagedevice"
*PageRegion l/L 89.0x127.0mm: "<</CNPageSizeName(l)/PageSize[252 360]/ImagingBBox null>>setpagedevice"
*PageRegion 2l/2L 127.0x178.0mm: "<</CNPageSizeName(2l)/PageSize[360 505]/ImagingBBox null>>setpagedevice"
*PageRegion postcard/Hagaki 100.0x148.0mm: "<</CNPageSizeName(postcard)/PageSize[283 420]/ImagingBBox null>>setpagedevice"
*PageRegion postdbl/Hagaki 2 200.0x148.0mm: "<</CNPageSizeName(postdbl)/PageSize[567 420]/ImagingBBox null>>setpagedevice"
*PageRegion envelop10p/Comm. Env. #10 4.12x9.5in 104.6x241.3mm: "<</CNPageSizeName(envelop10p)/PageSize[297 684]/ImagingBBox null>>setpagedevice"
*PageRegion envelopdlp/DL Env. 110.0x220.0mm: "<</CNPageSizeName(envelopdlp)/PageSize[312 624]/ImagingBBox null>>setpagedevice"
*PageRegion envj4p/Youkei 4 105.0x235.0mm: "<</CNPageSizeName(envj4p)/PageSize[298 666]/ImagingBBox null>>setpagedevice"
*PageRegion envj6p/Youkei 6 98.0x190.0mm: "<</CNPageSizeName(envj6p)/PageSize[278 539]/ImagingBBox null>>setpagedevice"
*PageRegion creditcard/Credit Card 2.13x3.39in 54.0x86.0mm: "<</CNPageSizeName(creditcard)/PageSize[153 244]/ImagingBBox null>>setpagedevice"
*PageRegion businesscard/Card 2.16x3.58in 55.0x91.0mm: "<</CNPageSizeName(businesscard)/PageSize[156 258]/ImagingBBox null>>setpagedevice"
*PageRegion wide/Wide 4x7.1in 101.6x180.6mm: "<</CNPageSizeName(wide)/PageSize[288 512]/ImagingBBox null>>setpagedevice"
*CloseUI: *PageRegion

*OpenUI *MediaType/Media Type: PickOne
*DefaultMediaType: plain
*MediaType plain/Plain Paper: "<</MediaType(plain)>>setpagedevice"
*MediaType prophoto/Photo Paper Pro: "<</MediaType(prophoto)>>setpagedevice"
*MediaType superphoto/Photo Paper Plus Glossy: "<</MediaType(superphoto)>>setpagedevice"
*MediaType doublesidephoto/Photo Paper Plus Double Sided: "<</MediaType(doublesidephoto)>>setpagedevice"
*MediaType matte/Matte Photo Paper: "<</MediaType(matte)>>setpagedevice"
*MediaType glossypaper/Glossy Photo Paper: "<</MediaType(glossypaper)>>setpagedevice"
*MediaType highres/High Resolution Paper: "<</MediaType(highres)>>setpagedevice"
*MediaType ijpostcard/Ink Jet Hagaki: "<</MediaType(ijpostcard)>>setpagedevice"
*MediaType postcard/Hagaki: "<</MediaType(postcard)>>setpagedevice"
*MediaType tshirt/T-Shirt Transfers: "<</MediaType(tshirt)>>setpagedevice"
*MediaType envelope/Envelope: "<</MediaType(envelope)>>setpagedevice"
*MediaType otherphoto/Other Photo Paper: "<</MediaType(otherphoto)>>setpagedevice"
*CloseUI: *MediaType

*OpenUI *InputSlot/Paper Feed: PickOne
*DefaultInputSlot: switch
*InputSlot switch/Paper Feed Switch: "<</MediaPosition 2>>setpagedevice"
*InputSlot asf/Auto Sheet Feeder: "<</MediaPosition 0>>setpagedevice"
*InputSlot cassette/Cassette: "<</MediaPosition 1>>setpagedevice"
*CloseUI: *InputSlot

*DefaultImageableArea: A4
*ImageableArea Letter: "18.14 14.17 594.14 783.50"
*ImageableArea Legal: "18.14 14.17 594.14 999.50"
*ImageableArea A5: "9.64 14.17 409.89 586.77"
*ImageableArea A4: "9.64 14.17 585.64 833.39"
*ImageableArea B5: "9.64 14.17 506.27 720.00"
*ImageableArea 4X6: "9.64 14.17 278.36 423.50"
*ImageableArea 4X8: "9.64 14.17 278.36 567.50"
*ImageableArea 5X7: "9.64 14.17 350.36 495.50"
*ImageableArea 8X10: "9.64 14.17 566.36 711.50"
*ImageableArea l: "9.64 14.17 242.65 351.50"
*ImageableArea 2l: "9.64 14.17 350.36 496.06"
*ImageableArea postcard: "9.64 14.17 273.83 411.02"
*ImageableArea postdbl: "9.64 14.17 557.29 411.02"
*ImageableArea envelop10p: "9.64 75.12 287.35 675.50"
*ImageableArea envelopdlp: "9.64 75.12 302.17 615.12"
*ImageableArea envj4p: "9.64 75.12 288.00 657.64"
*ImageableArea envj6p: "9.64 75.12 268.16 530.08"
*ImageableArea creditcard: "9.64 14.17 143.43 235.28"
*ImageableArea businesscard: "9.64 14.17 146.27 249.45"
*ImageableArea wide: "9.64 14.17 278.36 503.49"

*DefaultPaperDimension: A4
*PaperDimension Letter: "612 792"
*PaperDimension Legal: "612 1008"
*PaperDimension A5: "420 595"
*PaperDimension A4: "595 842"
*PaperDimension B5: "516 729"
*PaperDimension 4X6: "288 432"
*PaperDimension 4X8: "288 576"
*PaperDimension 5X7: "360 504"
*PaperDimension 8X10: "576 720"
*PaperDimension l: "252 360"
*PaperDimension 2l: "360 505"
*PaperDimension postcard: "283 420"
*PaperDimension postdbl: "567 420"
*PaperDimension envelop10p: "297 684"
*PaperDimension envelopdlp: "312 624"
*PaperDimension envj4p: "298 666"
*PaperDimension envj6p: "278 539"
*PaperDimension creditcard: "153 244"
*PaperDimension businesscard: "156 258"
*PaperDimension wide: "288 512"

*OpenUI *Duplex/Duplex: PickOne
*DefaultDuplex: None
*Duplex None/OFF: "<</Duplex false>>setpagedevice"
*Duplex DuplexNoTumble/ON (Long Side Stapling): "<</Duplex true/Tumble false>>setpagedevice"
*Duplex DuplexTumble/ON (Short Side Stapling): "<</Duplex true/Tumble true>>setpagedevice"
*CloseUI: *Duplex

*UIConstraints: *InputSlot switch *PageSize Legal
*UIConstraints: *PageSize Legal *InputSlot switch
*UIConstraints: *InputSlot switch *PageSize creditcard
*UIConstraints: *PageSize creditcard *InputSlot switch
*UIConstraints: *InputSlot switch *PageSize businesscard
*UIConstraints: *PageSize businesscard *InputSlot switch
*UIConstraints: *InputSlot cassette *PageSize Legal
*UIConstraints: *PageSize Legal *InputSlot cassette
*UIConstraints: *InputSlot cassette *PageSize creditcard
*UIConstraints: *PageSize creditcard *InputSlot cassette
*UIConstraints: *InputSlot cassette *PageSize businesscard
*UIConstraints: *PageSize businesscard *InputSlot cassette

*UIConstraints: *Duplex *MediaType prophoto
*UIConstraints: *MediaType prophoto *Duplex
*UIConstraints: *Duplex *MediaType superphoto
*UIConstraints: *MediaType superphoto *Duplex
*UIConstraints: *Duplex *MediaType matte
*UIConstraints: *MediaType matte *Duplex
*UIConstraints: *Duplex *MediaType glossypaper
*UIConstraints: *MediaType glossypaper *Duplex
*UIConstraints: *Duplex *MediaType highres
*UIConstraints: *MediaType highres *Duplex
*UIConstraints: *Duplex *MediaType ijpostcard
*UIConstraints: *MediaType ijpostcard *Duplex
*UIConstraints: *Duplex *MediaType tshirt
*UIConstraints: *MediaType tshirt *Duplex
*UIConstraints: *Duplex *MediaType envelope
*UIConstraints: *MediaType envelope *Duplex
*UIConstraints: *Duplex *MediaType otherphoto
*UIConstraints: *MediaType otherphoto *Duplex

*UIConstraints: *Duplex *PageSize Legal
*UIConstraints: *PageSize Legal *Duplex
*UIConstraints: *Duplex *PageSize 4X6
*UIConstraints: *PageSize 4X6 *Duplex
*UIConstraints: *Duplex *PageSize 4X8
*UIConstraints: *PageSize 4X8 *Duplex
*UIConstraints: *Duplex *PageSize 8X10
*UIConstraints: *PageSize 8X10 *Duplex
*UIConstraints: *Duplex *PageSize l
*UIConstraints: *PageSize l *Duplex
*UIConstraints: *Duplex *PageSize envelop10p
*UIConstraints: *PageSize envelop10p *Duplex
*UIConstraints: *Duplex *PageSize envelopdlp
*UIConstraints: *PageSize envelopdlp *Duplex
*UIConstraints: *Duplex *PageSize envj4p
*UIConstraints: *PageSize envj4p *Duplex
*UIConstraints: *Duplex *PageSize envj6p
*UIConstraints: *PageSize envj6p *Duplex
*UIConstraints: *Duplex *PageSize creditcard
*UIConstraints: *PageSize creditcard *Duplex
*UIConstraints: *Duplex *PageSize businesscard
*UIConstraints: *PageSize businesscard *Duplex
*UIConstraints: *Duplex *PageSize wide
*UIConstraints: *PageSize wide *Duplex

*DefaultFont: Courier
*Font Courier: Standard "(001.001)" Standard ROM

*%CNPpdToOptKey PageSize --papersize
*%CNPpdToOptKey MediaType --media
*%CNPpdToOptKey InputSlot --paperload
*%CNPpdToOptKey CNCartridge --cartridge
*%CNPpdToOptKey CNQuality --quality
*%CNPpdToOptKey CNHalftoning --halftoning
*%CNPpdToOptKey CNRenderIntent --renderintent
*%CNPpdToOptKey CNGamma --gamma
*%CNPpdToOptKey CNBalanceC --balance_c
*%CNPpdToOptKey CNBalanceM --balance_m
*%CNPpdToOptKey CNBalanceY --balance_y
*%CNPpdToOptKey CNDensity --density
*%CNPpdToOptKey CNGrayscale --grayscale
*%CNPpdToOptKey CNLocation --location
*%CNPpdToOptKey CNPercent --percent
*%CNPpdToOptKey CNCopies --copies
*%CNPpdToOptKey Duplex --duplex
*%CNPpdToOptKey CNStapleSide --stapleside
*%CNPpdToOptKey CNContrast --contrast


*% 
*% internalversion : 2.70.01.010
*%
```

---

### Post by 2CV67 on 2008-11-14
Thanks Erlander for your good work on this printer!

I will not be trying Intrepid any time soon, as I am one of the thousands having kernel-panic hard freezes with Hardy & apparently they continue in Intrepid...
So I am back in XP for what may be a long time. 

You ask what image programs people use to print photos:
My method is probably terribly inefficient, but I generally use Picasa for my day to day photo trimming, straightening, brightening, organizing etc (only resorting to Gimp or Paint.net for tricky stuff). Then I export what I want to print from Picasa to desktop.
Then insert from desktop to an OpenOrg.draw master I keep for that purpose, with the right printer settings.
This allows me to completely fill an A4 sheet with however many images of whatever size & shape I want.
So I can print A4 sheets with no waste.

I am sure everybody else will show me how to do it better, but that's my way so far.

Thanks again & I look forward to trying Ubuntu again once these kernel panics are fixed (but it's been a year now...).

---

### Post by imaca on 2008-11-19
2CV67 -Thanks for the tip about changing colour space to CMYK.
And thanks to you Erlander for your guide, will have to try this.

---

### Post by Erlander on 2008-11-19
I have it working using the latest drivers from Canon but they don't give the CMYK option and as a result the reds are a muddy colour on the test print but I have printed digital photos with better results.

Unfortunately I have lost the earlier copies of the drivers I had downloaded and so can't try them.

Edit:  Found the earlier copies.  See post#32.

However I do have the drop-down menus for Resolution and Quality working.

The biggest problem I have with printing photos is that there just doesn't seem to be any Linux software that gives enough flexibility and control over the printing.

Result I still have to keep Windows XP going to use the Canon software to print photos and also for my scanner.

Remember if following my guide that libxml1 is no longer available and that that line needs to be changed to libxml2.  I will at some time change it in the guide but at present am not sure whether this applies to all Ubuntu versions or just 8.10.  Can anyone help with this?

Rob

---

### Post by 2CV67 on 2008-11-19
I still have copies of the following Canon drivers from August if that can be of any help:
cnijfilter-common-2.70-1.i386.rpm
cnijfilter-common-2.70-1.src.rpm
cnijfilter-ip4300-2.70-1.i386.rpm

---

### Post by Erlander on 2008-11-19
Many thanks 2CV67.  since writing that I've had a look around my PC and found the 2.70-1 drivers and even some 2.60's.  Just shows that I need to check that old hard disc more often.

Now I just need some time to try them all and find which is the best!

I'm also going to try the print settings a bit more as I stumbled across this site [http://shamis.org/info/s900-linux.html]("http://shamis.org/info/s900-linux.html") while looking for photo printing software.

Rob

---

### Post by luceerose on 2008-12-03
My only success with Canon printers has been with the Gutenprint drivers.
But you also need to install some hal packages, or it won't work at all, because canon printers communicate through a hal id.(or something to that effect).
If you install the following list of packages and restart, almost any canon printer/multi-function should show up & work automagically;
```

cupsys-driver-gutenprint
foomatic-db-gutenprint
ijsgutenprint
libgutenprint2
libgutenprintui2-1
hal
hal-info
hal-cups-utils

```

---

