---
title: "Canon ip4600 some success"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by islandstone on 2008-11-08
I have a Canon Pixma 4600 , which I'm trying to set up to as full funcionality as possible.

So far I have the following config working quite well.
[IMG]http://lh6.ggpht.com/_j3_FbfYEV9U/SRYUrhZ5YbI/AAAAAAAAANM/qemHkka8zZc/s912/Screenshot-Printer%20configuration%20-%20localhost.png[/IMG]
[IMG]http://lh3.ggpht.com/_j3_FbfYEV9U/SRYUrhtaQ9I/AAAAAAAAANU/HOtOXsXtM9E/s912/Screenshot-Printer%20configuration%20-%20localhost-1.png[/IMG]
I downloaded a Cups ppd from canon at [http://software.canon-europe.com/software/0028476.asp](http://software.canon-europe.com/software/0028476.asp) there are two deb packages , downloaded them both and let the package manager install them.
ppd fil(s) now in /usr/share/cups/model .

I have tried editing the ppd to include the Advanced settings suggested here [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200) , to get a higher dpi , but when I select the edited ppd in printer config , settings , make and model , change . the test page doesn't print? I only get a successful test page withe the original ppd , dpi 600.
Is editing the file corrupting something? How can I test the dpi against that specified in printer config? As the printout looks good , better than I expected for 600.

---

### Post by Hilarity on 2008-11-25
hi,

ubuntu autoadded my new pixma pi4600 but i was unable to print. in the properties it says printer status is idle. in printer status it says printer may not be connected even though the printer was installed just a few minutes ago.

i tried to install the above debian packages. however they are for i386 (intel) architecture and i have a athlon 64.

what can i do to make the printer work with ubuntu?

---

### Post by islnd on 2008-12-01
[SIZE="2"]I only just noticed your post..........had any luck?

I gave up with cups and the ppd , I've now downloaded Turboprint from [http://www.turboprint.info/](http://www.turboprint.info/) , it has been upgraded to include the ip4600. It works a treat 100%, and for the removal of hassle I reckon worth the 30 euros.But you get a month to try it out.[/SIZE]

---

### Post by flawedprefect on 2008-12-07
FOlks - go here:

[http://software.canon-europe.com/products/0010649.asp](http://software.canon-europe.com/products/0010649.asp)

It includes a printer driver to let linux talk to the 4600 series. Printed test page - all's well.

---

### Post by metol on 2008-12-09
Thank you very much for posting this - works great.  With a little work in Guttenprint, I even got it to print 4x6 borderless prints.

> **flawedprefect said:**
> FOlks - go here:

[http://software.canon-europe.com/products/0010649.asp](http://software.canon-europe.com/products/0010649.asp)

It includes a printer driver to let linux talk to the 4600 series. Printed test page - all's well.

---

### Post by metol on 2008-12-09
> **metol said:**
> Thank you very much for posting this - works great.  With a little work in Guttenprint, I even got it to print 4x6 borderless prints.

After a successful install on my 32bit system, I was able to get these drivers to work on my 64bit system as well - I made a few notes in case anyone else is interested:

Unpack the tar file that you downloaded from Canon (see flawedprefects post above - Thanks!) into some temporary directory and then open a terminal and change to that directory.

first install libcupsys2 (there is a dependency needed later on)

```
sudo apt-get install libcupsys2
```

install cnijfilter-common_3.00-1_i386.deb with forced architecture
```

sudo dpkg -i --force-architecture cnijfilter-common_3.00-1_i386.deb
```

and now, install the second package...
```

sudo dpkg -i --force-architecture cnijfilter-ip4600series_3.00-1_i386.deb
```

Connect your printer via the USB port and it should be recognized automatically.

---

### Post by Velociraptor on 2009-01-10
Works great (even duplex!), thanks metol and flawedprefects! (Ubuntu 8.10, 64bit)

I had to delete the previous (bad) configuration from System -> Administration -> Printing. And then turn on the printer, so that it was newly discovered.

---

### Post by karesz on 2009-01-10
> **Velociraptor said:**
> Works great (even duplex!), thanks metol and flawedprefects! (Ubuntu 8.10, 64bit)


So, this new (3.0) version of the official driver knows higher resolutions? Does it use less ink? If it does, maybe i should try it...worth a try

BTW does anybody know, if this driver will work with my ip4500? By the official comparsion, the only difference is the inks (IMHO it will work, at least i hope it will) If anyone tried it comment it in a few words :) Thx

---

### Post by phenest on 2009-02-08
My mum just bought one of these after I recommended it due to reading this thread. After installing the 2 deb files, I setup the printer. It was auto detected as an ip4000 (ip4600 is not the the driver list). I cannot get the printer to print. I've been trying to get the test page to print with no success. The job is sent and there are no errors. But the printer simply does nothing.

I'm experienced in Ubuntu, but know nothing about CUPS or Guttenprint.

What could be wrong?

---

### Post by phenest on 2009-02-09
Ignore my last post. I hadn't installed one of the deb files properly. The printer now works but why can I only use it at 600dpi? Does anyone know why? The ppd supplied with the Canon driver isn't complete so as to allow printing at 9600dpi. How can I fix this?

---

### Post by phenest on 2009-02-11
Now my mum complains of not producing 5x7 prints properly. I'm suspecting this driver is not a fully featured driver. Nice one Canon! My mum has contacted them and is awaiting an answer.

---

### Post by islandstone on 2009-02-12
Strewth your Mum must be savvy, min ehas trouble printing from XP.........
I hate to repeat myself , and I hate to pay for something that should be provided with the device , Canon?!?! But for full featured printing and ease of use the Turboprint drivers/software is error free (so far).

NB: I won't bother with another Canon printer until they decide that Linux users are worthy of their attention.

---

### Post by stoppage on 2009-02-28
Hi folks
I'm considering purchase of same ip4600 but I`m not intereested in paying for "TurboPrint" software. Most important issue for me is printing direcly  to CD/DVD facility. Has anybody tested this with "Glabels"? and will it give as many problems as installation of the Canon-supplied software? I'm running good ol`"Gutsy" and would appreciate any help on the issues before I decide. Many thanks.

---

### Post by neigun on 2009-03-13
Hi 

I've tried Metol's sudo command lines but just get error messages returned:


neil@neil-desktop:~$ sudo dpkg -i --force-architecture cnijfilter-common_3.00-1_i386.deb
dpkg: error processing cnijfilter-common_3.00-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 cnijfilter-common_3.00-1_i386.deb

The Deb file is saved to Home and has been unpacked from the tar file.

I'm probably missing the obvious as I am a bit of a noob to say the least!

TTFN Neil

Ubuntu 8.10 64 bit
Kernel 2.6.27-9-generic
AMD 64 3200
ATI Radeon HD 3650 AGP
3Gb Ram
SB Audigy 5.1 PCI

---

### Post by Paul T. on 2009-03-16
> **flawedprefect said:**
> FOlks - go here:

[http://software.canon-europe.com/products/0010649.asp](http://software.canon-europe.com/products/0010649.asp)

It includes a printer driver to let linux talk to the 4600 series. Printed test page - all's well.


There are two drivers listed for this, Debian_driver.tar & RPM_driver.tar, which one do I use?

---

### Post by metol on 2009-03-21
> **Paul T. said:**
> There are two drivers listed for this, Debian_driver.tar & RPM_driver.tar, which one do I use?

You will want the Debian driver for Ubuntu.

---

### Post by metol on 2009-03-21
> **neigun said:**
> Hi 

I've tried Metol's sudo command lines but just get error messages returned:


neil@neil-desktop:~$ sudo dpkg -i --force-architecture cnijfilter-common_3.00-1_i386.deb
dpkg: error processing cnijfilter-common_3.00-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 cnijfilter-common_3.00-1_i386.deb

The Deb file is saved to Home and has been unpacked from the tar file.

I'm probably missing the obvious as I am a bit of a noob to say the least!

TTFN Neil



It is acting like the deb file is not in the directory where you are trying to execute the command.  Make sure the file is in the directory that you are executing from... tar may have placed the deb file in a sub-directory.

Hope this helps,
Metol

---

### Post by orgiutas on 2009-05-18
Hello evryone,

I'd like to ask, if the IP4600 was fully working for anyone _without_ the TurboPrint drivers. 

I plan to buy this printer, and have Jaunty installed on my PC, with AMD64, and would like to use it for CD/DVD printing, Photo printing, and documents printing (basically for everithing, it is suitable for :).

Taking my CPU architecture in consideration:
- Is it working with the current Canon provided drivers (3.0), above 600 dpi (e.g. with extending the ppd file)

- Is it working (better?) with the Guteprint drivers?

- Does  it by any means have drawbacks printing under Linux, compared to Windows XP?

Thank you very much in advance!

---

### Post by pbowler on 2009-08-23
Have just bought and installed an iP4600 and found this thread very useful.

Have installed the drivers and the system recognises the printer OK.  Installation gave the message 
 dpkg - warning, overriding problem because --force enabled:
   package architecture (i386) does not match system (amd64)
which is odd because I have a 64-bit Intel chip (x86_64).  However, it seems to accept it.

Unfortunately when I do a test print, I get:
   /usr/lib/cups/filter/pstocanonij failed

Is this a problem with the printer or CUPS?  I have attached a CUPS debug output in case that helps.

Can anyone help?????????????

---

### Post by neigun on 2009-09-18
Hi

I would delete the drivers installed and reinstall them as per Metol's instructions. 

If you are used to XP download the Debian tar from the Canon webiste. Double click on it to unpack it and then drag and drop the appropriate files into your Home folder.

Then go to Applications/ Accessories and click on Terminal. Just cut and paste Metol's command lines in and when prompted key in your password.

Hope this sorts your problem out.

Neil

---

### Post by pbowler on 2009-09-26
> **neigun said:**
> Hi

I would delete the drivers installed and reinstall them as per Metol's instructions. 

If you are used to XP download the Debian tar from the Canon webiste. Double click on it to unpack it and then drag and drop the appropriate files into your Home folder.

Then go to Applications/ Accessories and click on Terminal. Just cut and paste Metol's command lines in and when prompted key in your password.

Hope this sorts your problem out.

Neil

Thanks Neil.  I went on to sort the printer and tried "one last time" and it worked :):):)  No idea why!:confused:

---

### Post by djcarrad on 2009-10-17
This may be an unusual request, but i'm looking to print at less than 600 dpi with this printer very regularly. i want to print out lots of notes that only need to be 'draft' quality (~300dpi), and so not use large volumes of ink. The turboprint driver offers this, but obviously the free trail isn't going to last forever, and neither gutenprint nor the Canon driver seem to have any way of changing this. Anyone have any ideas?

Cheers
DC

---

### Post by BlaY0 on 2010-01-07
I managed to extend the quality and resolution options to some extent. I don't know for sure which one of those options is actually being used but I definitely can print in "draft" mode and also in mode that has more detail than that of "stock" 600 dpi.

Edit file **/usr/share/cups/model/canonip4600.ppd** and find block that begins with:
```
*OpenUI *Resolution/Output Resolution: PickOne
```
...and add something like:
```
*Resolution 1200dpi/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400dpi/2400 dpi: "<</HWResolution[2400 2400]>>setpagedevice"
```
...to this block (after 600 dpi statement). After this block add another block:
```
*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality
```
...save file, restart cups. Now reaquire this ppd in printer configuration GUI by changing make and model and once again select **Canon iP4600 series Ver.3.00** driver. This operation will regenerate ppd in **/etc/cups/ppd** directory.

---

### Post by alextacy on 2011-01-08
Hi there, if anyone is still on this thread it would be lovely to get some help!

I have tried following the advice from Metol, however I keep getting the same message as described by neigun (14th march '09) - that the file does not exist.

I have extracted the .tar to /home/aliale (no permission to drag files directly into 'home'), such that I have /home/aliale/cnijfilter-common-3.00 

Metol, when you say that > It is acting like the deb file is not in the directory where you are  trying to execute the command.  Make sure the file is in the directory  that you are executing from... tar may have placed the deb file in a  sub-directory.

which file exactly are you referring to?

I have tried opening the cnijfilter-common-3.00 folder & copying all of the subfolders into /home/aliale however it still does not work.  Is there a specific file that I need to ensure is available in this directory?

Additionally regarding the dependency:  libcupsys2  I get:

aliale@aliale-laptop:~$ sudo apt-get install libcupsys2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libcups2 instead of libcupsys2
libcups2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I can imagine that things have moved on since your original posts (its now 2011!) however I am wondering if this affects the rest of the process?

Any help would be much appreciated as we really need to print off some photos!!

---

### Post by hackeron on 2011-05-27
Anyone managed to get this printer working in 2011?

---

### Post by demonipuch on 2011-05-27
Hi

You shoudl add [this ppa]("https://launchpad.net/%7Emichael-gruz/+archive/canon") to your source list. It provides drivers for many Canon PIXMA printer.

```
sudo add-apt-repository ppa://michael-gruz/canon
sudo apt-get update
sudo apt-get install cnijfilter-common cnijfilter-ip4600series
```Add your printer and you're done.
You can try to print a test page

---

### Post by sol77 on 2011-06-05
The above worked nicely. I did have to remove the printer first and re-add it but that was all (except for some fine tuning in the settings). 

Thank you very much, demonipuch.

---

### Post by chinner459 on 2011-09-08
> **islnd said:**
> [SIZE=2]I only just noticed your post..........had any luck?

I gave up with cups and the ppd , I've now downloaded Turboprint from [http://www.turboprint.info/](http://www.turboprint.info/) , it has been upgraded to include the ip4600. It works a treat 100%, and for the removal of hassle I reckon worth the 30 euros.But you get a month to try it out.[/SIZE]


Many thanks for your info.  After several attempts to install the Canon driver and being told that the file I was looking could not be found, I gave up and installed Turboprint which worked first time. Thanks again

---

### Post by chinner459 on 2011-09-08
> **flawedprefect said:**
> FOlks - go here:

[http://software.canon-europe.com/products/0010649.asp](http://software.canon-europe.com/products/0010649.asp)

It includes a printer driver to let linux talk to the 4600 series. Printed test page - all's well.


Having got the driver as I did, how did you install it?  Are you using Ubuntu 11.04?

---

