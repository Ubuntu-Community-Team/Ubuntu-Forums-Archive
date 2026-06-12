---
title: "HOWTO: Install HP Printers for Beginners"
date: 2006-05-30
forum: Outdated Tutorials &amp; Tips
---

### Post by user1397 on 2006-05-30
This is a little guide on how to correctly install an HP printer, since so many people seem to have trouble with this. I have also provided a very basic scanner start up guide.  Here are the steps:

**Printing:**

First of all, connect your printer to your computer, and turn it on.

See if your printer gets autodetected by Ubuntu.  If it does, something will pop up saying it is configured for use and is ready.  

If nothing happens, simply go to  System > Administration > Printing > New.

If it doesn't find any or doesn't recognize your printer, try the [official hplip website]("http://hplipopensource.com/hplip-web/install_wizard/index.html") to try to download the correct drivers for your printer.

If even that doesn't work, then post here with your printer name and configuration, and maybe I or someone else can help you.

**Scanning:**

For HP all-in-ones (such as the PSC series), after you have followed the above steps, put the paper you want to scan in the scanner and then go to Applications > Graphics > XSane Image scanning program. In XSane, click "scan" and then when it's done, click save as and save it wherever you want.

If you have a sole HP scanner, then you could try to just plug it in, turn it on, and try to scan it with XSane, but I don't gurantee that it will work.

***NOTE:  If you want to send a scan that you made on your linux box to a windows computer, it won't open it up (I don't know why, it just wouldn't for me). You have to right-click on the image, and go to "open with GIMP Image Editor". Then go to save as and click on "select file type (by extension)". Then scroll down to JPEG format and click ok as many times so that it saves. It'll then be readable in windows.

---

### Post by klytu on 2006-06-23
I recently had a problem with an HP DeskJet 722C parallel port printer. Installed and worked perfectly following the steps above for both Hoary (5.04) and Breezy (5.10). In Dapper (6.06) the printer was detected and installed but would not print. Print jobs would spool and then just stop without printing. Checking the error logs indicated something was going wrong just before the output page generated, but no specific error was listed at that point. 

Solved the problem by editing /etc/pnm2ppa.conf (pnm2ppa is the recommended driver for several HP DeskJet parallel port printers). I did: 

sudo gedit /etc/pnm2ppa.conf

In the section beginning with version, changed from this:

version
#version 710 # 710, 712, 722 also acceptable
#version 820
#version 1000

to this:

version 722 

Saved change and now could print normally. Obviously one would substitute one's own actual HP DeskJet model number above. Appears this would probably work for the 710C, 712C, 722C, 820C, and 1000C.

---

### Post by user1397 on 2006-06-23
[QUOTE=klytu]I recently had a problem with an HP DeskJet 722C parallel port printer. Installed and worked perfectly following the steps above for both Hoary (5.04) and Breezy (5.10). In Dapper (6.06) the printer was detected and installed but would not print. Print jobs would spool and then just stop without printing. Checking the error logs indicated something was going wrong just before the output page generated, but no specific error was listed at that point. 

Solved the problem by editing /etc/pnm2ppa.conf (pnm2ppa is the recommended driver for several HP DeskJet parallel port printers). I did: 

sudo gedit /etc/pnm2ppa.conf

In the section beginning with version, changed from this:

version
#version 710 # 710, 712, 722 also acceptable
#version 820
#version 1000

to this:

version 722 

Saved change and now could print normally. Obviously one would substitute one's own actual HP DeskJet model number above. Appears this would probably work for the 710C, 712C, 722C, 820C, and 1000C.[/QUOTE]thank you for that info, i'm sure it'll help a lot of people with their deskjet printers.

---

### Post by El Guapo on 2006-07-20
A few more tricks for those installing OfficeJet printers.  From synaptic also download the hpoj package as well.  Then after all is said and done you should have a configuration of your OfficeJet printer appear and walk you through the details.

If not, go to the command line and type:
```
sudo /etc/init.d/hpoj setup
```

From here you just follow the directions.  Then when you enter the System -> Administration -> Printing -> New Printer your OfficeJet should be seen as a local printer (even if it is on a network!).

---

### Post by 11hjpphty76lkjj on 2006-07-21
Actually you will not want to install hpoj and hplip together as they will cause conflicts.  We have a good step by step for ubuntu on our website.

[http://hplip.sourceforge.net](http://hplip.sourceforge.net)

hpoj is very old and does not have any support for any products for the last 2 years as well as no fax support or status support, *insert long list here*,etc.

The best thing to do is NOT install hpoj and work with hplip as it as extended support and functionality.

I've tested over 500 hp printers with HPLIP and have tested with ubuntu very frequently.  The step by step on our website is straight forward and I should hope will help users install and configure their printer easily.  As well I'm open to any suggestions on making our instructions easier and more straight forward so feel free to give me ideas!

---

### Post by BatteryCell on 2006-07-28
> **klytu said:**
> I recently had a problem with an HP DeskJet 722C parallel port printer. Installed and worked perfectly following the steps above for both Hoary (5.04) and Breezy (5.10). In Dapper (6.06) the printer was detected and installed but would not print. Print jobs would spool and then just stop without printing. Checking the error logs indicated something was going wrong just before the output page generated, but no specific error was listed at that point. 

Solved the problem by editing /etc/pnm2ppa.conf (pnm2ppa is the recommended driver for several HP DeskJet parallel port printers). I did: 

sudo gedit /etc/pnm2ppa.conf

In the section beginning with version, changed from this:

version
#version 710 # 710, 712, 722 also acceptable
#version 820
#version 1000

to this:

version 722 

Saved change and now could print normally. Obviously one would substitute one's own actual HP DeskJet model number above. Appears this would probably work for the 710C, 712C, 722C, 820C, and 1000C.

Yea everyone keeps saying that changing this to version 7xx or version 0 or just commenting it out fixes the problem but I still cant print :sad: My printer says that its processing then after a few second it says that it completed the job, but it really didnt :sad:

---

### Post by Nosferatu on 2006-08-24
THANK YOU!! a thousand times.  I've been trying to get my HP Deskjet 990C printing since January, (ok, I wasn't constantly at it since then).  I've finally seen a test page printed successfully.  Usually when I printed a test page the job would be sent and the printer would pause. I followed your instruction to install all the HPIJS packages.  All of them were already installed except the very last one libijs-dev.  So I Marked that one and followed the rest of the steps and voila...a test page.
Thanks again.
:KS

---

### Post by user1397 on 2006-08-24
> **Nosferatu said:**
> THANK YOU!! a thousand times.  I've been trying to get my HP Deskjet 990C printing since January, (ok, I wasn't constantly at it since then).  I've finally seen a test page printed successfully.  Usually when I printed a test page the job would be sent and the printer would pause. I followed your instruction to install all the HPIJS packages.  All of them were already installed except the very last one libijs-dev.  So I Marked that one and followed the rest of the steps and voila...a test page.
Thanks again.
:KSyou're quite welcome!

---

### Post by bknutt on 2006-08-24
> Actually you will not want to install hpoj and hplip together as they will cause conflicts. We have a good step by step for ubuntu on our website.

[http://hplip.sourceforge.net](http://hplip.sourceforge.net)

hpoj is very old and does not have any support for any products for the last 2 years as well as no fax support or status support, *insert long list here*,etc.

The best thing to do is NOT install hpoj and work with hplip as it as extended support and functionality.

I've tested over 500 hp printers with HPLIP and have tested with ubuntu very frequently. The step by step on our website is straight forward and I should hope will help users install and configure their printer easily. As well I'm open to any suggestions on making our instructions easier and more straight forward so feel free to give me ideas!


So I tried these instructions since I'm brand new to linux and have a hp 7310xi printer on my network.  I keep getting the following error when I try to execute the configure command

> checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... none
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.


I've installed gcc 4.0 using the synaptic installer with no change in the error message.  Any suggestions?  Could it be looking for an earlier version of gcc?

---

### Post by bknutt on 2006-08-24
> hpoj is very old and does not have any support for any products for the last 2 years as well as no fax support or status support, *insert long list here*,etc.

I saw "hplip" in synaptic (ubuntu 6.06).  Should it be used instead?

---

### Post by user1397 on 2006-08-24
> **bknutt said:**
> I saw "hplip" in synaptic (ubuntu 6.06).  Should it be used instead?yes, that's the driver for all hp printers except for the officejet series.

---

### Post by user1397 on 2006-08-24
> **bknutt said:**
> So I tried these instructions since I'm brand new to linux and have a hp 7310xi printer on my network.  I keep getting the following error when I try to execute the configure command




I've installed gcc 4.0 using the synaptic installer with no change in the error message.  Any suggestions?  Could it be looking for an earlier version of gcc?hmmmm....maybe you don't need to ./configure, sometimes you don't have to.  does it say to do that command or did you just try it?

---

### Post by jamesstansell on 2006-08-25
> [QUOTE]I saw "hplip" in synaptic (ubuntu 6.06). Should it be used instead?
yes, that's the driver for all hp printers except for the officejet series.[/QUOTE]
hplip supports OfficeJet printers:
[http://hplip.sourceforge.net/supported_devices/inkjet_aio.html](http://hplip.sourceforge.net/supported_devices/inkjet_aio.html)

---

### Post by jamesstansell on 2006-08-25
> **bknutt said:**
> So I tried these instructions since I'm brand new to linux and have a hp 7310xi printer on my network.  I keep getting the following error when I try to execute the configure command

...
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
...

I've installed gcc 4.0 using the synaptic installer with no change in the error message.  Any suggestions?  Could it be looking for an earlier version of gcc?

Two thoughts for you.  1) be sure build-essential is installed; 2) verify your $PATH.  Does 'type gcc' show /usr/bin/gcc?  What does 'gcc --version' show?

-james.

---

### Post by user1397 on 2006-08-25
> **jamesstansell said:**
> hplip supports OfficeJet printers:
[http://hplip.sourceforge.net/supported_devices/inkjet_aio.html](http://hplip.sourceforge.net/supported_devices/inkjet_aio.html)hmmm interesting,  thats news to me.  well, thats awesome i guess!

---

### Post by bknutt on 2006-08-25
It works!  That's what I like about computers!  Where else can you get such a sense of accomplishment for doing something that's so simple (once you know how)  :D 

I used the procedure from sourceforge for installing hplip.  The website has a very simple 5 step procedure - but each step is a link to a set of substeps.  I failed to review each of those subsets and managed to skip some key parts.

I did not have the 'build-essential' installed and that was giving me the 'compiler' error message.

The only feedback I can provide for others using sourceforge would be to check each of those links embedded in each step.

Thanks for the help!  It pointed me in the right direction.
:D

---

### Post by flyingbrass on 2006-08-26
I want to install the newest version of hplip.  The (outdated) Dapper package is already installed.  Removing it would take out ubuntu-desktop.

The instructions at Sourceforge mention checking to see if hplip is already installed, but I didn't see anything addressing what to do if it is before installing from the tarball. Should I first uninstall the Ubuntu package?

In a similar vein, if I later update do I need to make uninstall before installing the latest and greatest?

Is the newest version of hplip working with checkinstall? [Recent discussion about possibly making it compatible](http://www.mail-archive.com/hplip-help@lists.sourceforge.net/msg00768.html).

---

### Post by brucevangeorge on 2006-08-29
I have hpijs and hplip both installed, but the printer will not do anything. Not even a test page. The job just stops after a few secs.

Maybe it's:

HP Deskjet 712C
PPA printer, does not work with PCL drivers (as "hpijs", "gimp-print", "cdjXXX", "pcl3", ...) 

from: [http://www.linuxprinting.org./printer_list.cgi](http://www.linuxprinting.org./printer_list.cgi)

Has anyone here got a 710 or 712 working?

---

### Post by user1397 on 2006-08-29
> **flyingbrass said:**
> I want to install the newest version of hplip.  The (outdated) Dapper package is already installed.  Removing it would take out ubuntu-desktop.

The instructions at Sourceforge mention checking to see if hplip is already installed, but I didn't see anything addressing what to do if it is before installing from the tarball. Should I first uninstall the Ubuntu package?

In a similar vein, if I later update do I need to make uninstall before installing the latest and greatest?

Is the newest version of hplip working with checkinstall? [Recent discussion about possibly making it compatible]("http://www.mail-archive.com/hplip-help@lists.sourceforge.net/msg00768.html").removing the ubuntu-desktop package does nothing, as it is a *meta-package*, meaning its a pointer to other packages.  as far as i understand, its alrite to install the newest version over the older one without having to remove the older one.

---

### Post by galv on 2006-08-31
> **erik1397 said:**
> removing the ubuntu-desktop package does nothing, as it is a *meta-package*, meaning its a pointer to other packages.  as far as i understand, its alrite to install the newest version over the older one without having to remove the older one.

Let's hope so, I will try to do it!

---

### Post by galv on 2006-08-31
> **galv said:**
> Let's hope so, I will try to do it!

It work, just fallow the steps from the HPLIP website and now I have Printer/Scanner (HP Photosmarth C3180) working!

Yuppei! :)

---

### Post by user1397 on 2006-08-31
> **galv said:**
> It work, just fallow the steps from the HPLIP website and now I have Printer/Scanner (HP Photosmarth C3180) working!

Yuppei! :)awesome!

---

### Post by moontan on 2006-08-31
Worked like a charm on my networked Hp Photosmart 2710.
I used the [http://hplip.sourceforge.net/]("http://hplip.sourceforge.net/") link and installed from the tarball.

Now if only I can find some thing similar for my canon s520. Oh well I will keep looking.

---

### Post by user1397 on 2006-10-23
Okay, I have finally edited this guide.  It includes the hplip website now, for maximum compatability.  Thanks for all those who have contributed to this guide.

---

### Post by voided3 on 2006-11-19
Hello. I am running Edgy with an HP Officejet all-in-one 4215 connected via USB and it refuses to work. It isn't detected by either the administration/printing setup or the XSane scanner. I've tried using both hplips and CUPS but to no avail. I had the exact same setup work under Dapper 6.06 just fine, which is why I am so perplexed. Do I need to downgrade some software, or are there any other methods out there I should try? Thanks!

---

### Post by user1397 on 2006-11-19
> **voided3 said:**
> Hello. I am running Edgy with an HP Officejet all-in-one 4215 connected via USB and it refuses to work. It isn't detected by either the administration/printing setup or the XSane scanner. I've tried using both hplips and CUPS but to no avail. I had the exact same setup work under Dapper 6.06 just fine, which is why I am so perplexed. Do I need to downgrade some software, or are there any other methods out there I should try? Thanks!so u tried the latest hplip drivers from the site i showed in the guide?

---

### Post by voided3 on 2006-11-19
Yeah, I have hplip 1.6.9 installed

---

### Post by user1397 on 2006-11-19
> **voided3 said:**
> Yeah, I have hplip 1.6.9 installed
that's really weird then.  if you followed my guide to the letter, and it still doesn't work, i don't know what to say...maybe just bad luck? :(

---

### Post by voided3 on 2006-11-19
If this helps, when I run the hplip 1.6.10 installer in the automatic mode, I get this at the end:


INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------

warning: There are 6 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
note: You may be prompted for a password. Please enter the appropriate password for your system for 'sudo'
warning: Missing REQUIRED dependency: gcc (gcc - GNU Project C and C++ Compiler)
error: This installer cannot install this dependency for your distro/OS and/or version.
error: Installation cannot continue without this dependency. Please manually install this dependency and re-run this installer.



According to synaptic, I have gcc installed too... perhaps it's the wrong version. Any thoughts? Thanks!

---

### Post by user1397 on 2006-11-19
> **voided3 said:**
> If this helps, when I run the hplip 1.6.10 installer in the automatic mode, I get this at the end:


INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------

warning: There are 6 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
note: You may be prompted for a password. Please enter the appropriate password for your system for 'sudo'
warning: Missing REQUIRED dependency: gcc (gcc - GNU Project C and C++ Compiler)
error: This installer cannot install this dependency for your distro/OS and/or version.
error: Installation cannot continue without this dependency. Please manually install this dependency and re-run this installer.



According to synaptic, I have gcc installed too... perhaps it's the wrong version. Any thoughts? Thanks!hmm....even weirder...gcc is one of the basic programs included with all of the different distros of linux.

o well.  

try this in a terminal: ```
sudo aptitude update && sudo aptitude dist-upgrade
```then you might want to try: ```
sudo apt-get update && sudo apt-get install -f
```

and then try the installer again.

---

### Post by voided3 on 2006-11-20
Hello again. I ran both codes, but no luck. I also downloaded the 1.6.9 installer to try that instead of the 1.6.10 I was using, but it resulted in much of the same.I remember the site said the earliest driver supported was 0.9.5, perhaps I should start there and see what happens? Thanks!

---

### Post by voided3 on 2006-11-20
Alright, I got it to work, but first I must plea to insanity for not checking the most obvious thing: the usb connection on the printer..... I recently reorganized my desk and I guess I accidentally pulled the cable out a little bit.... I think I might go hide in the corner for the rest of the day ](*,) :oops: Thanks for the help, at least now I know what to do in case something actually doesn't work!

---

### Post by user1397 on 2006-11-20
> **voided3 said:**
> Alright, I got it to work, but first I must plea to insanity for not checking the most obvious thing: the usb connection on the printer..... I recently reorganized my desk and I guess I accidentally pulled the cable out a little bit.... I think I might go hide in the corner for the rest of the day ](*,) :oops: Thanks for the help, at least now I know what to do in case something actually doesn't work!lol, we all learn something new every day...

---

### Post by cbratteli on 2006-11-22
> **erik1397 said:**
> hmm....even weirder...gcc is one of the basic programs included with all of the different distros of linux.

o well.  

try this in a terminal: ```
sudo aptitude update && sudo aptitude dist-upgrade
```then you might want to try: ```
sudo apt-get update && sudo apt-get install -f
```

and then try the installer again.

I am having the same problem and applied your solution but without effect.  Any other ideas?  Specifically, I have an OfficeJet 7400 series connected to a router with WiFi (no cables).  MS Windows works without flaw, but then HP supplied windows installation software on CD-ROM.  No such convenience with Ubuntu.  I am hoping version x.10 will solve the problem over the x.9 which is already installed.

---

### Post by user1397 on 2006-11-23
> **cbratteli said:**
> I am having the same problem and applied your solution but without effect.  Any other ideas?  Specifically, I have an OfficeJet 7400 series connected to a router with WiFi (no cables).  MS Windows works without flaw, but then HP supplied windows installation software on CD-ROM.  No such convenience with Ubuntu.  I am hoping version x.10 will solve the problem over the x.9 which is already installed.i am not sure if ubuntu supports wireless printers at all.  can anyone else confirm this?

---

### Post by 11hjpphty76lkjj on 2006-11-27
Ubuntu does support wireless printing.  As does HPLIP.  It's like using a standard network configuration.  If the printer has an IP address and your computer has an IP address and you can ping the printer it should work.

And the officejet 7400 as well as 1000's other models are supported by hplip.

[http://hplip.sf.net](http://hplip.sf.net) for more info.

Hope this helps.

Aaron

---

### Post by user1397 on 2006-11-27
> **kalosaurusrex said:**
> Ubuntu does support wireless printing.  As does HPLIP.  It's like using a standard network configuration.  If the printer has an IP address and your computer has an IP address and you can ping the printer it should work.

And the officejet 7400 as well as 1000's other models are supported by hplip.

[http://hplip.sf.net](http://hplip.sf.net) for more info.

Hope this helps.

Aaronwow, i did not know this, very cool indeed.  i hope that helps you, cbratteli.

just curious (since i do not have a wireless printer), how do you find out your printer's IP address?

---

### Post by 11hjpphty76lkjj on 2006-11-27
Usually the printer will have a network configuration setting from which you can print or display the IP address.

---

### Post by user1397 on 2006-11-27
> **kalosaurusrex said:**
> Usually the printer will have a network configuration setting from which you can print or display the IP address.ah, ok. thanks for helping out in this thread.

---

### Post by ryn0 on 2006-12-15
Hi guys. During the ./configure --prefix=/usr i get this message:
configure: error: cannot find net-snmp support (or --disable-network-build)
Any ideas how i could fix it? thx

---

### Post by 11hjpphty76lkjj on 2006-12-15
Please go to:

[http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

and follow the instructions for Ubuntu.

Aaron

---

### Post by matchstich on 2006-12-16
i used hpijis
thanks

---

### Post by ryn0 on 2006-12-17
what do you mean? i was, there is no salvation to my problem at the troubleshooting section. During the install several similar errors appeared, i fixed them by installing components. but this time it didn't work, even though i've installed net-smtp component from Synaptic. I'm sorry to bother, but i'm a newbee and there is nobody around i could ask

---

### Post by 11hjpphty76lkjj on 2006-12-18
If you are trying to install HPLIP on ubuntu start with the instructions here:

[http://hplip.sf.net](http://hplip.sf.net)

However the instructions for Edgy haven't been updated yet. (should be today I hope).

but you will need to run this for the dependencies for edgy:

sudo apt-get install build-essential python2.4-dev python2.4-qt3 libcupsys2-dev libsnmp9-dev libjpeg62-dev lsb libtool automake1.9 libusb-dev

A

---

### Post by AlanRogers on 2006-12-18
> **erik1397 said:**
> i am not sure if ubuntu supports wireless printers at all.  can anyone else confirm this?6.06 ran my 7410 just fine and my whole network was wireless. All I did was get a configuration page out of the printer and use the IP address to connect HPLIP to it. Et voila, Robert est le frere de ta mere! :cool:

---

### Post by joecomstock on 2006-12-22
Hi,

I am running into dependency hell with apt and the directions from the HP website

when i try and fix them i get this

joe@gladius:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  postfix
Suggested packages:
  postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin
Recommended packages:
  resolvconf
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B/923kB of archives.
After unpacking 2224kB of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
(Reading database ... 157806 files and directories currently installed.)
Unpacking postfix (from .../postfix_2.2.10-1ubuntu0.1_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
dpkg: error processing /var/cache/apt/archives/postfix_2.2.10-1ubuntu0.1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/postfix_2.2.10-1ubuntu0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by joecomstock on 2006-12-22
Got it working.....................


rebooted and retried it and postfix went ok and the hpoj uninstall worked from there


thanks for the guide, maybe i posted the problem a little prematurely

thanks again

---

### Post by user1397 on 2006-12-23
> **joecomstock said:**
> Got it working.....................


rebooted and retried it and postfix went ok and the hpoj uninstall worked from there


thanks for the guide, maybe i posted the problem a little prematurely

thanks againby the way, the error you got from apt was probably caused by having the terminal open while synaptic was open or the add/remove program was open.  you can only use apt one program at a time.

---

### Post by Nda on 2007-02-16
I've recently acquired a HP LaserJet 4 printer, and want to use it with this PC.  Yesterday, I went to the hplip.sourceforge.net link in the OP's guide to download and install the HPLIP driver for Dapper.  

Because the only available connection on the printer is by parallel port, I had to do a manual install rather than the automatic one.

The first stage is:

[html]sudo apt-get install build-essential python2.4-dev python2.4-qt3 libcupsys2-dev libsnmp9-dev libjpeg62-dev lsb libtool automake1.9 libusb-dev[/html]I did this and watched the downloads happen, but then immediately got a caption in the terminal about 'Postfix Configuration', saying I had several choices, one of which would break my mail system (see attached image).

I had no idea what Postfix is, or how or why I should configure it.  I clicked on 'OK' and the next screen offered me 4 configuration options, none of which I understood, so I chose 'Cancel'.

This took me back to the terminal, but after watching the cursor blink for a few minutes, I decided nothing more was going to happen and closed the terminal.  I searched for 'Postfix' but it isn't installed on this machine.

So I've got several questions:

What is Postfix and what has it got to do with a printer driver?

Did anyone else who followed the guide get this caption and if so, what did they do?

How do I get round this so that I can install the driver?

I sent an email to the site, as I was following their instructions, but they haven't responded.

Nda

---

### Post by 11hjpphty76lkjj on 2007-02-16
Odd--I'm the moderator for the HPLIP mailing list and I haven't seen your email come in.

Regardless, postfix is required by LSB, LSB is required by HPLIP.

Even if your printer us using parallel you can still do an automatic install, just choose custom install during the process.

If you want to do a manual install that's still fine, just run the:

```
sudo apt-get install build-essential python2.4-dev python2.4-qt3 libcupsys2-dev libsnmp9-dev libjpeg62-dev lsb libtool automake1.9 libusb-dev
```

and when postfix comes up just select no configuration.  Really it wont make any difference to HPLIP.  But it does need to be installed. Then just follow the manual process as documented.

Although I'm unclear as to:

> but after watching the cursor blink for a few minutes, I decided nothing more was going to happen and closed the terminal

Depending on your system sometimes it takes a few min for apt to finish installing applications, it's usually not advised to close shutdown apt in the middle of a install as this could cause broken packages and other problems. (just for future reference.)

Hope this helps.

---

### Post by Nda on 2007-02-16
Thanks for the prompt response kalosaurusrex.

I was doing the manual install because the instructions on the site specifically advised me to do so if using a parallel port connection.  And I closed the terminal because there were no messages about installing or configuring at all, just the cursor sat there blinking.  I assumed selecting 'Cancel' had stopped the process.

A point I made in my email was to ask why there was no advice on what to do when this caption came up.  As I said, I had no idea what Postfix was so I didn't know what to do with it.  Of the options offered, I wasn't going to select 'No configuration' after the caption said that would break my mail system, because that seemed a fairly clear warning to me.  That's why I opted to cancel.

As a lot of us are still learning about Linux, perhaps it would be helpful to future users like me to include some advice in the guide about the Postfix configuration message so that they can select the correct option.

I shall try to install HPLIP again soon and hope that yesterday's aborted installation hasn't buggered things up.

Nda

---

### Post by 11hjpphty76lkjj on 2007-02-16
Where does it say that if using parallel you must use the manual?  I'll update that.

I've also added a note to the ubuntu manual install instructions about postfix. Although it wont show up until the next release.

Any other feedback you have is appreciated. :)

A

---

### Post by Nda on 2007-02-16
Thanks for modifying the instructions.  

The comment about the automatic installer is on this page (see image):

[http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

And one I forgot from the first post was the image from my Sent items in Thunderbird (I clicked on Contact Site Maintainer at the bottom of the page).  Times are GMT.

I will be attempting to install again tomorrow and will pass on the outcome here.  I have my fingers crossed.

Nda

---

### Post by Nda on 2007-02-17
I've just tried the manual install again and everything went well up to the 'restart cupsys and hplip' stage.  The message was that only cupsd had restarted so I ran 

```
sudo /etc/init.d/hplip restart
```again and that worked.  With the printer on and connected, I entered

```
sudo hp-setup
```which opened the Setup Wizard, selected parallel port LPT1, but then got the 'No devices found' message.

After much investigation all I can come up with is this: the printer is connected from the parallel port (_[COLOR=Orange][25-pin in two rows]("http://en.wikipedia.org/wiki/Parallel_port")[/COLOR]_) on the PC to the same connection on the printer.  However, on the printer this port is labelled as 'Serial Port', and the one labelled 'Parallel Port' looks more like _[COLOR=Orange][this]("http://pinouts.ru/ParallelPorts/Centronics_pinout.shtml")[/COLOR]_.

It's possible therefore, that I need a cable with a different connector type at each end.  I don't have that much knowledge of older components so I'm not certain about this, but would I appreciate any advice from those who do know.

Nda

---

### Post by Nda on 2007-02-23
I now have the correct cable connecting parallel port to parallel port, but running hp-setup and selecting 'parallel port connection' gives me the 'No Device Found' message again.

The terminal says this:

```
nda@mesh:~$ sudo hp-setup
Password:

HP Linux Imaging and Printing System (ver. 1.7.1)
Printer/Fax Setup Utility ver. 4.3

Copyright (c) 2003-6 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
error: No devices found.Please make sure your printer is properly connected and powered-on.

```The printer is switched on and connected, the driver is installed.  I know the printer works because I made it do a self-test to print out a page.

I don't understand why trying to make a printer work should give an 'X Error', which surely relates to the display?  Anyway, I'm off to spend a few hours searching to see if I can find something.  

In the meantime, if anyone knows what this message means I'd be grateful if you could pass it on!

Nda

---

### Post by Nda on 2007-02-23
Thanks to Hawkwind on this kubuntu forum _[COLOR=Orange][post]("http://translate.google.com/translate?hl=en&sl=it&u=http://pollycoke.wordpress.com/chat/&sa=X&oi=translate&resnum=3&ct=result&prev=/search%3Fq%3DX%2BError:%2BBadDevice,%2Binvalid%2Bor%2Buninitialized%2Binput%2Bdevice%2B171%26start%3D10%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-GB:official%26sa%3DN")[/COLOR]_ I have been able to remove the X Error messages.

However, after restarting X and running hp-setup again I still get the 'No Devices Found' message.  :confused:

The HP device manager gives me the option to manually enter the filesystem device node for the printer, e.g /dev/parportX.  Can anyone suggest where I might look to find mine, as there is nothing like that in my /dev folder.

Nda

---

### Post by 11hjpphty76lkjj on 2007-02-23
Nda,

Can you run:

/usr/lib/cups/backend/hp

and post the output?

---

### Post by Nda on 2007-02-23
Hello again kalosaurusrex,

I ran what you suggested and got this:

```
nda@mesh:~$ /usr/lib/cups/backend/hp
direct hp:/no_device_found "Unknown" "hp no_device_found"
```As a last desperate fling before I got out the big hammer I returned to Ubuntu's System/Admin/Printing/Add printer, put in the Laserjet 4 and it worked!  I had tried this before I attempted to install the HPLIP driver and it wouldn't work at all, but now it does.

Logical conclusion: the printer works, the HPLIP driver works, the hp-setup command *doesn't* work, at least not here.

Nda

---

### Post by 11hjpphty76lkjj on 2007-02-23
Nda,

The hp-setup command line should work, I've tested it a lot on ubuntu.

If you used the ubuntu add printer tool then I'm curious if the printer is configured using the hp backend. 

in other words if your printer isn't displayed with the:

/usr/lib/cups/backend/hp

then it will not work with HPLIP.

If you run hp-toolbox does the printer show up?

---

### Post by Nda on 2007-02-23
kalosaurusrex,

It doesn't show in hp-toolbox (see image).  

Something appears not to be working as it should but I've no idea what.  If you want me to test any more commands to try to find out what's happening then ask away and I'll send you the results.

I'm ok now with a working printer, but if there is something going wrong that may give other people difficulties then I'll gladly assist in attempting to resolve those difficulties.

Nda

---

### Post by 11hjpphty76lkjj on 2007-02-23
You can try:

sudo /etc/init.d/hplip restart
sudo /etc/init.d/cupsys restart

disconnect the printer, reconnect, then run:

sudo hp-setup

hp-setup  'should' detect the printer..

---

### Post by Nda on 2007-02-23
I did those and got this:

```
nda@mesh:~$ sudo /etc/init.d/hplip restart
Password:
Stopping hpiod:                                            [  OK  ]
Stopping hpssd:                                            [  OK  ]
Starting hpiod:                                            [  OK  ]
Starting hpssd:                                            [  OK  ]
nda@mesh:~$ sudo /etc/init.d/cupsys restart
 * Restarting Common Unix Printing System: cupsd                         [ ok ]
nda@mesh:~$ sudo hp-setup

HP Linux Imaging and Printing System (ver. 1.7.1)
Printer/Fax Setup Utility ver. 4.3

Copyright (c) 2003-6 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: No devices found.Please make sure your printer is properly connected and powered-on.
```I also got the 'No devices found' message when I asked the device manager to connect to a parallel port.

Nda

---

### Post by 11hjpphty76lkjj on 2007-02-23
ahh.  sorry for not asking earlier.

run 

```
lsmod | grep ppdev
```

and post the output.

---

### Post by Nda on 2007-02-24
Are these what you're looking for kalosaurusrex?

```
nda@mesh:~$ lsmod | grep ppdev
ppdev                  10052  0
parport                39560  3 ppdev,lp,parport_pc
```What is this saying?

Nda

---

### Post by steven8 on 2007-02-25
I can use my hp psc 1210 all-in-one printer to print from any program, as well as scan from xsane with no problems, and yet the hplip toolbox says no device found.  It also gives me NO option to set up a device.

Here is the output from you last few suggestions:

> steven8@steven8-desktop:~$ /usr/lib/cups/backend/hp
direct hp:/usb/psc_1200_series?serial=MY3CBG81S25H "HP psc_1200_series" "hp:/usb/psc_1200_series?serial=MY3CBG81S25H"
steven8@steven8-desktop:~$ hp-toolbox

 HP Linux Imaging and Printing System (ver. 0.9.7)
 HP Device Manager ver. 6.0

 Copyright (c) 2003-5 Hewlett-Packard Development Company, LP
 This software comes with ABSOLUTELY NO WARRANTY.
 This is free software, and you are welcome to distribute it
 under certain conditions. See COPYING file for more details.

X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
steven8@steven8-desktop:~$

> steven8@steven8-desktop:~$ lsmod | grep ppdev
ppdev                   9220  0
parport                36296  3 ppdev,lp,parport_pc

I too would like to use the hplip toolbox, but cannot access it.

---

### Post by bedake on 2007-02-27
I just ran hplip and got my printer working fine though it created a locked folder on my desktop named hplip-1.7.1, is it possible to move this to another directory?

---

### Post by 11hjpphty76lkjj on 2007-02-27
The HPLIP directory should not be locked unless you ran it as root. 

Regardless, do chmod 777 hplip-1.7.1 and then rm -rf hplip-1.7.1 or move it to a location of your choice.  but you can just delete the directory once the install is completed.

---

### Post by 11hjpphty76lkjj on 2007-02-27
steven8:

try removing the printers and re-running hp-setup.  You can remove the printers from [http://localhost:631](http://localhost:631).

Or you can try re-running hp-setup. 

sudo hp-setup

Hope this helps.

---

### Post by bedake on 2007-02-27
Ahh got it, thanks

---

### Post by 11hjpphty76lkjj on 2007-02-27
Sorry..

try:

sudo chmod 777 <directory.name.here>

---

### Post by bedake on 2007-02-27
> **kalosaurusrex said:**
> Sorry..

try:

sudo chmod 777 <directory.name.here>


sorry, I realized that right after posting haha, I'm still not used to using a terminal :)

---

### Post by 11hjpphty76lkjj on 2007-02-27
No worries. :)

Thanks for using Ubuntu and HPLIP!

A

---

### Post by user1397 on 2007-02-27
> **kalosaurusrex said:**
> No worries. :)

Thanks for using Ubuntu and HPLIP!

Aso you're the lead developer on the hplip project?

I think that you should have control over this thread, since you obviously know more than me. (after all this was meant as a simple tutorial for beginners, and that's what i was and (still am now) when i made this guide)

maybe we can talk to a mod about switching owners of this thread (unless of course you dont want to, thats cool too)

---

### Post by steven8 on 2007-02-27
sudo hp-setup says the command is not found.  I am running Dapper.  Does that make a difference?  I didn't remove my printer yet as suggested, because if running Dapper changes these instructions, I don't want to ruin a printer which seems to be working okay otherwise.

What is the difference between delete printer and unpublish printer at localhost?

Thanks.

---

### Post by 11hjpphty76lkjj on 2007-02-28
> **ubuntuman001 said:**
> so you're the lead developer on the hplip project?

I think that you should have control over this thread, since you obviously know more than me. (after all this was meant as a simple tutorial for beginners, and that's what i was and (still am now) when i made this guide)

maybe we can talk to a mod about switching owners of this thread (unless of course you dont want to, thats cool too)

I'm not the lead, but I am the primary support person.  I work with the engineers that develop the tools.

I'd be honored, but it's really up to you.  You did make the how to--I'm just trying to help out. :)

---

### Post by 11hjpphty76lkjj on 2007-02-28
> **steven8 said:**
> sudo hp-setup says the command is not found.  I am running Dapper.  Does that make a difference?  I didn't remove my printer yet as suggested, because if running Dapper changes these instructions, I don't want to ruin a printer which seems to be working okay otherwise.

What is the difference between delete printer and unpublish printer at localhost?

Thanks.


Sounds like you are using an older version of hplip.  You may want to install the latest from: [http://hplip.sf.net](http://hplip.sf.net)

---

### Post by user1397 on 2007-02-28
> **kalosaurusrex said:**
> I'm not the lead, but I am the primary support person.  I work with the engineers that develop the tools.

I'd be honored, but it's really up to you.  You did make the how to--I'm just trying to help out. :)hmmm, i think I'll talk to a mod soon.  you obviously deserve to be the OP, because half of the questions you answer, i have no answer to!  yea i made a how-to, but that doesnt mean im proficient with it :)

well i'll talk to the mods, and see what they can do, and then i'll forward those PM's to you.

thanks for your support in the hplip project

---

### Post by steven8 on 2007-02-28
> **kalosaurusrex said:**
> Sounds like you are using an older version of hplip.  You may want to install the latest from: [http://hplip.sf.net](http://hplip.sf.net)

That got it!  I was using version 0.9.7!! :rolleyes: 

Thanks!!

---

### Post by user1397 on 2007-03-21
[FONT=Verdana]hey, kalosaurusrex, did you ever receive my private message?  i sent it to you a while ago, please check it.  by the way, you can enable the option so that PM's become pop-ups when you sign in to the forums, its in preferences in your control panel i think.
[/FONT]

---

### Post by 11hjpphty76lkjj on 2007-03-23
ubuntuman001:  Sorry, we're right in the middle of a release so I haven't had a chance to take a look at my PM's.  I'll check it out.  I'll work on getting the topic switched over early next week.

Sorry about the delay.

---

### Post by outhouse on 2007-04-30
Hope I'm not covering old ground. I've installed my 7410 w/ hplip 3 times now. each time the install goes well, every thing looks good, and I print a test page. BUT once I shut down or reboot no more printing. it says it is printing but nothing happens. other than that I'm really liking fiesty a lot.  I'm an old newbie so you will have to keep it simple for me.   Thank you.

---

### Post by 11hjpphty76lkjj on 2007-04-30
Can you run in a terminal:

```
sudo /etc/init.d/hplip restart
```

and 

```
sudo /etc/init.d/cupsys restart
```

and try printing again what happens?

---

### Post by user1397 on 2007-04-30
yo, kalosaurusrex, I had forgotten about the idea we had to make a 3rd party project sub-forum for HPLIP, it was so long ago, and I did send 2 PM's to ubuntu-geek, but he never responded...maybe if you try he'll listen to you!

---

### Post by outhouse on 2007-05-01
Thank you for your prompt reply. I ran both strings, one at a time, got OK's on every thing but still can't print. As near as I can tell, in my ignorance, every thing looks good. printer shows up in tool box, icon shows up in tool bar w/ print job #, etc. I just realized I  don't know how to cut & paste into an email in Ubuntu yet,  so I can't show terminal. sorry about that. I'm learning as fast as my poor old brain can go.

Thanks again.

jah43@mymachine:~$ sudo /etc/init.d/hplip restart

Password:
Stopping hpiod:                                            [  OK  ]
Stopping hpssd:                                            [  OK  ]
Starting hpiod:                                            [  OK  ]
Starting hpssd:                                            [  OK  ]
jah43@mymachine:~$ sudo /etc/init.d/cupsys restart
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
jah43@mymachine:~$

---

### Post by steven8 on 2007-05-01
> **outhouse said:**
> Thank you for your prompt reply. I ran both strings, one at a time, got OK's on every thing but still can't print. As near as I can tell, in my ignorance, every thing looks good. printer shows up in tool box, icon shows up in tool bar w/ print job #, etc. I just realized I  don't know how to cut & paste into an email in Ubuntu yet,  so I can't show terminal. sorry about that. I'm learning as fast as my poor old brain can go.

Thanks again.

No need to 'cut and paste'.  Highlight the text you want to copy, go to where you want it to be copied to, and center click.  The highlighted text will copy over.  Doesn't matter how much text.  I've copied some pretty long docs that way!

---

### Post by outhouse on 2007-05-01
Thank you, Steven8,

That was really one of those slap your forehead things. I don't know how long it would have taken me to figure that out

Thanks a lot

---

### Post by steven8 on 2007-05-01
You're welcome.  :)

---

### Post by j_evenstar on 2007-05-26
waah what seems to be the problem with my installation? i've tried it a second time but still the error remains. it says here:

```
DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --yes --force-yes xsane'
Please wait, this may take several minutes...
warning: A previous install of HPLIP is installed and/or running.
Running 'sudo /etc/init.d/hplip stop'
Please wait, this may take several minutes...

Running 'sudo apt-get remove --yes --force-yes hplip hpijs'
Please wait, this may take several minutes...
error: HPLIP removal failed. The previous install may have been installed using a tarball or this installer.
error: Continuing to run installer - this installation should overwrite the previous one.
warning: An optional dependency 'xsane' is still missing.
warning: Some features may not function as expected.


BUILD AND INSTALL
-----------------

Running './configure --enable-network-build --disable-pp-build --enable-fax-build --enable-gui-build --enable-scan-build --prefix=/usr'
Please wait, this may take several minutes...

Command completed successfully.

Running 'make clean'
Please wait, this may take several minutes...

Command completed successfully.

Running 'make'
Please wait, this may take several minutes...

error: 'make' command failed with status code 2
jillian@jillian-desktop:~
```$

---

### Post by alligoodw on 2007-05-29
When installing HPLIP, understanding that I have a network (home network) printer (DeskJet F4100), where do I obtain the network setting that are necessary to complete the HPLIP installation?  Where on the Windows XP machine do I find the IP address or whatever this installation needs?


> **kalosaurusrex said:**
> Actually you will not want to install hpoj and hplip together as they will cause conflicts.  We have a good step by step for ubuntu on our website.

[http://hplip.sourceforge.net](http://hplip.sourceforge.net)

hpoj is very old and does not have any support for any products for the last 2 years as well as no fax support or status support, *insert long list here*,etc.

The best thing to do is NOT install hpoj and work with hplip as it as extended support and functionality.

I've tested over 500 hp printers with HPLIP and have tested with ubuntu very frequently.  The step by step on our website is straight forward and I should hope will help users install and configure their printer easily.  As well I'm open to any suggestions on making our instructions easier and more straight forward so feel free to give me ideas!

---

### Post by Thanatos10 on 2007-06-02
It worked great for me.  As a matter of fact, since first starting this Ubuntu "experience" this is one of the few things that actually worked as advertised.  Thanks to everyone for this, me and my printer (HP5180) are getting along much better now.....

Scott....

---

### Post by bliffle on 2007-06-07
Thank you guys!

I got my old HP5850 working thru the USB, thanks to you.  Now maybe I'll try getting it going thru the RJ45 connected to an extra WiFi router. A few more days and I'll be totally free of XP.

---

### Post by matthewartz on 2007-06-28
Seems like a knowledgeable bunch.  Could one of you take a look at my related post on xsane io error with hplip (printing is working, scanner is recognized, but constant io errors)?

[http://ubuntuforums.org/showthread.php?t=486113](http://ubuntuforums.org/showthread.php?t=486113)

---

### Post by dsmturbo on 2007-07-02
I am a real newbie here so bear with me. I have sucessfully installed (I think) my networked HP LAserjet 4 Plus, but even after changing the paper size to US Letter in both places in the printer properties, it still askes for A4 paper.

---

### Post by 11hjpphty76lkjj on 2007-07-02
Run hp-toolbox and verify that the paper size is correct under print settings.  Then also make sure your paper size is correct in the application.  Also make sure that the document is not formated for A4, ie sometimes people will make pdf's that are A4 size rather than Letter.

Hope this helps.

---

### Post by dsmturbo on 2007-07-02
Thanks for reply, but where is the HP Toolbox, I can not locate it anywhere.

---

### Post by 11hjpphty76lkjj on 2007-07-02
Applications > Accessories > Terminal

run:
```

hp-toolbox

```

---

### Post by user1397 on 2007-07-04
if there is some error while trying to open HP toolbox, just install this package: **python-qt4  **(I think that is the right package)

if hp toolbox does not appear under the system > administration, then it is probably not enabled.

just right click on system, and go to edit menus, you'll figure it out.

---

### Post by AlexFoster on 2007-08-05
I have an HP6800 and am having a devil of a time installing it.

I do not have "administration" under System in my application menu (I'm running Xubuntu). Where else would I look? I've poked around and I see nothing obvious.

---

### Post by user1397 on 2007-08-05
> **AlexFoster said:**
> I have an HP6800 and am having a devil of a time installing it.

I do not have "administration" under System in my application menu (I'm running Xubuntu). Where else would I look? I've poked around and I see nothing obvious.Hmmm, I really don't know where the printing preferences are in xubuntu, though I imagine there should be one somewhere.  I would advise you to just look again (thoroughly), or else I don't really know what to tell you :(

---

### Post by johnraff on 2007-08-07
> **AlexFoster said:**
> I do not have "administration" under System in my application menu (I'm running Xubuntu). Where else would I look?Xubuntu's printer setup's at Settings>Printing.

HP's toolbox doesn't appear on my xubuntu menu but the Debian Menu will find it if you install it, or you can use the command "hp-toolbox".

That said, printing certainly seems to be one area where Linux can get to you a bit...

---

### Post by AlexFoster on 2007-08-08
Joy! the hp-toolbox recommendation worked!

Now I just have to figure out how to get my box to communicate wirelessly with my printer... but at least it works fine when they're physically connected now.

---

### Post by MeNoKnow on 2007-09-23
Help I'm pulling my hair out! Another stuck newbie.  Everything looks ok but all print jobs stop with no output.  My system: omnibook 900b 192K p3 450 4 port usb hub,unbuntu 7.04, hp officejet 5510

POSSIBLY IMPORTANT: sprint pantech px 500 pcmcia wireless internet, needing usb serial driver modification! ?

from Synaptic:
hplip 1.7.3
hpijs 2.7.2+ 1.7.3

from GUI Administrstion -> Printing:

   hp:/usb/officejet_5500_series?serial=MY49TG096

FROM THE TERMINAL:

 /usr/lib/cups/backend/hp

direct hp:/usb/offic.2+.ejet_5500_series?serial=MY49TG20Z096 "HP officejet 5500 series" "HP officejet 5500 series USB MY49TG20Z096 HPLIP" "MFG:HP;MDL:officejet 5500 series;CLS:PRINTER;DES:officejet 5500 series;SN:MY49TG20Z096;"

Some messages:

cups admin error log:

E [23/Sep/2007:17:12:11 -0400] Creating missing directory "/var/run/cups/certs"
E [23/Sep/2007:17:22:42 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [23/Sep/2007:17:23:26 -0400] cupsdAuthorize: Local authentication certificate not found!
E [23/Sep/2007:17:23:26 -0400] cupsdAuthorize: Local authentication certificate not found!
E [23/Sep/2007:17:23:26 -0400] cupsdAuthorize: Local authentication certificate not found!
E [23/Sep/2007:17:23:28 -0400] cupsdAuthorize: Local authentication certificate not found!
E [23/Sep/2007:17:23:28 -0400] cupsdAuthorize: Local authentication certificate not found!
E [23/Sep/2007:17:23:28 -0400] cupsdAuthorize: Local authentication certificate not found!
E [23/Sep/2007:17:23:31 -0400] cupsdAuthorize: Local authentication certificate not found!
E [23/Sep/2007:17:23:42 -0400] cupsdAuthorize: Local authentication certificate not found!
E [23/Sep/2007:17:23:42 -0400] CUPS-Delete-Printer: Unauthorized
E [23/Sep/2007:17:26:33 -0400] PID 6160 (/usr/lib/cups/daemon/cups-driverd) crashed on signal 9!
E [23/Sep/2007:17:27:06 -0400] [Job 20] No %%BoundingBox: comment in header!
E [23/Sep/2007:17:27:19 -0400] PID 6273 (/usr/lib/cups/filter/pstoraster) crashed on signal 11!
E [23/Sep/2007:17:57:16 -0400] Creating missing directory "/var/run/cups/certs"
E [23/Sep/2007:17:59:55 -0400] [Job 21] No %%BoundingBox: comment in header!
E [23/Sep/2007:18:00:04 -0400] PID 5405 (/usr/lib/cups/filter/pstoraster) crashed on signal 11!
E [23/Sep/2007:18:12:01 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [23/Sep/2007:18:14:03 -0400] cupsdAuthorize: Local authentication certificate not found!
E [23/Sep/2007:18:14:03 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [23/Sep/2007:18:41:46 -0400] PID 8533 (/usr/lib/cups/filter/pstoraster) crashed on signal 11!
E [23/Sep/2007:18:42:36 -0400] [CGI] Unable to scan "@LOCAL"!


HP Linux Imaging and Printing System (ver. 1.7.3)
HP Device Manager ver. 9.0:

X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Any ideas where to look?  What to do?  Thanks in advance.

---

### Post by aceofbirds on 2007-10-23
Gutsy has reduced my HPDeskjet 712C to a paperweight.
I had it printing ok in feisty, but now it shows up on hplip's (admittedly very short) "unsupported" list.
When I go to the hpoj site, however, it's on the "works perfectly" list.
Following the advice in this thread of not having hpoj and hplip installed together, I added the one and removed the other, and now the system doesn't even detect the printer.  I have installed the pnm2ppa.ppd and configured it for 712C instead of 710, but to no avail.
Is there any hope?  I really can't afford another printer right now.

---

### Post by user1397 on 2007-10-24
> **aceofbirds said:**
> Gutsy has reduced my HPDeskjet 712C to a paperweight.
I had it printing ok in feisty, but now it shows up on hplip's (admittedly very short) "unsupported" list.
When I go to the hpoj site, however, it's on the "works perfectly" list.
Following the advice in this thread of not having hpoj and hplip installed together, I added the one and removed the other, and now the system doesn't even detect the printer.  I have installed the pnm2ppa.ppd and configured it for 712C instead of 710, but to no avail.
Is there any hope?  I really can't afford another printer right now.did you restart the computer between the uninstalling/installing phases? even though that sounds like an ancient windows habit, it does wonderful things sometimes :)

you might also want to try installing the latest version of hplip following the guide for the self-extracting installer in this link: [http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)

---

### Post by user1397 on 2007-10-24
> **MeNoKnow said:**
> 

Any ideas where to look?  What to do?  Thanks in advance.try installing the latest version of hplip following the guide for the self-extracting installer in this link: [http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)

---

### Post by Blankman on 2007-10-25
I have read the How to install HP Printrers for Beginners thread.  Unfortunately being a newbie I am obviously not getting it - I'm on Ubuntu 6.06 LTS (Dapper Drake).  My journey to getting where I am now has been pretty painful (and expensive) when it comes to printers.  Before I bought this one (HP Photosmart C5280) I phoned HP to make sure it was supported in Linux, having burnt myself in the past, and was informed that it is supported in Linux - this is also clear from the thread.  Now I can't get the thing loaded. 

I downloaded 'hplip-2.7.10 run' (from [http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)) so appear to have got step 1 right, I couldn't get past step 2 though, in that I got as far as opening the terminal but, obviously due to a lack of knowledge/understanding with Linux, couldn't (and still can't) understand the instruction "... and cd to the download directory".  I tried the path cd/directory but  got the following

russell@russell-laptop:~$ cd/home/russell/HP 
bash: cd/home/russell/HP: No such file or directory
russell@russell-laptop:~$

I also tried sh hplip-2.7.10.run in the terminal and got:

russell@russell-laptop:~$ sh hplip-2.7.10.run
sh: hplip-2.7.10.run: No such file or directory
russell@russell-laptop:~$

I then tried the System > Administration > Printing route where the set up detected "HP Photosmart C5200 series".  When you go to step 2, the C5280 (or C5200 series) is not in the drop down menu for HP but the recommended driver was hpijs - HPLIP 0.9.7, which, clearly from the commentary, is dated.  So, having downloaded hplip-2.7.10, I clicked on 'install driver' driver option and tried to open/run 'hplip-2.7.10 run'.  The following error message appeared:

Only files ending with .ppd or .ppd.gz will be installed

I'm really at my wits end when it comes to setting up printers.  I bought this because it is an All-in-One printer, scanner, copier.  I just want it to work.  PLEASE HELP!

---

### Post by Blankman on 2007-10-25
Right, sorted out the problem by installing .ppd (by following the instructions at [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_C5200](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_C5200) - a boit of trial and error on my part but got the C5200 series identified as a printer in the drop down).  I am now able to print.  

HOWEVER, what I am now trying to resolve is the scanning feature.  I have tried Ubuntuman001's suggestion, i.e.: 

For HP all-in-ones (such as the PSC series), after you have followed the above steps, put the paper you want to scan in the scanner and then go to Applications > Graphics > XSane Image scanning program. In XSane, click "scan" and then when it's done, click save as and save it wherever you want.

But w:confused:hen I try to run XSane Image Scanner I get the following pop ups:
1. Scanning for devices
2. No devices available.

Any thoughts on how I can get the scanning function to work?

Thanks

---

### Post by johnraff on 2007-10-26
Hi Blankman, I was in the same place a couple of months ago, so, till a Printing Guru shows up, might be able to help a little bit...
> the instruction "... and cd to the download directory". I tried the path cd/directory:

russell@russell-laptop:~$ cd/home/russell/HP 
OK this is a terminal use problem, not printing as such.
"cd" is a command meaning "change directory" and needs to be separated by a space from the path you want to change to, so in your case:
```
cd /home/russel/HP
``` (if "HP" is where you downloaded hplip-2.7.10.run)
The terminal should come back with "russell@russell-laptop:~/home/russel/HP$" so if you enter ```
sh hplip-2.7.10.run
``` this time it should be able to find and run the file.
Here's an introduction to using the terminal:
[Terminal for Beginners](http://ubuntuforums.org/showthread.php?t=73885)

I don't know, but if you get that new hplip driver installed it might just fix the scanner problem too...

---

### Post by Blankman on 2007-10-26
Johnraff you're an officer and a gentleman - thanks.  Although I must admit I was a bit of a muppet!  I spelt my own name wrong that's why I couldn't get the directory path to work in the terminal.  After many hours of trying this and that it came down to leaving out one letter in my name! :rolleyes: For the first time in a very long time I have a functional printer.  Thanks also to  Ubuntuman001and K-rex for all their input on the threads.

---

### Post by Daveth on 2007-11-02
does anyone know whether this is still the state of affairs?

"Current border-less (full bleed) support is 3-sided for paper sizes Oufuku-Hagaki or smaller. The HPIJS team is currently evaluating 4-sided large paper size (A4/Letter) or smaller full bleed support and expect to address this issue in a future release. "

On A4 on my HP5150 I can get quite small borders (3 - 4mm on 2 sides) but still not "borderless" at that paper size (typically the one I want!). Checked out the changelogs but cannot spot the answer.

---

### Post by TheThinker on 2007-11-02
For those of you using Gutsy and found that the Printer setup Window does not seem to get the printer working (even though it detects it), try this. Type and enter in the terminal:

sudo aa-complain cupsd


I found this worked for my HP 720C Deskjet right away. Just a Gutsy bug, I guess. I don't know if it'll work for wireless-printer setups but it may be worth a try.

P.S. Thanks to AKoine and others for posting similar suggestions!

---

### Post by john262 on 2007-11-02
> **aceofbirds said:**
> Gutsy has reduced my HPDeskjet 712C to a paperweight.
I had it printing ok in feisty, but now it shows up on hplip's (admittedly very short) "unsupported" list.
When I go to the hpoj site, however, it's on the "works perfectly" list.
Following the advice in this thread of not having hpoj and hplip installed together, I added the one and removed the other, and now the system doesn't even detect the printer.  I have installed the pnm2ppa.ppd and configured it for 712C instead of 710, but to no avail.
Is there any hope?  I really can't afford another printer right now.
I also have a  Deskjet 712C and I haven't been able to get it to work either. It's too bad because even though it's old it's a good printer and I want to keep using it. But I have tried all of the suggestions in this thread and it's a no go. And what's more, it worked fine with Fiesty.

So my question is, if it worked OK before why doesn't it work now? I thought that these upgrades were supposed to be improvements but this one seems more like a regression.

BTW, for what it's worth I just set up a dual boot system with OpenSuse 10.3 and I was able to print right out of the box with OpenSuse.

---

### Post by Tulsapoke on 2007-11-23
Type and enter in the terminal:

sudo aa-complain cupsd

This fixed my 712c on the parallel port.  Hopefully this fix isn't some command I have to run any time I print though... I will be testing.  But for now I am fixed.

Thanks.

---

### Post by hydeychan on 2008-05-04
> **ubuntuman001 said:**
> I have come up with a pretty complete list on how to correctly install an HP printer (I think) for beginners, since so many people seem to have trouble with this. I have also provided a very basic scanner start up guide.

I'm a complete newbie to linux (I just installed it today), and I just want to thank you for posting this.  It made it SO easy for me to configure my printer!

You rock! :KS

~hydeychan

---

### Post by Darrious on 2008-05-11
> **Tulsapoke said:**
> Type and enter in the terminal:

sudo aa-complain cupsd

This fixed my 712c on the parallel port.  Hopefully this fix isn't some command I have to run any time I print though... I will be testing.  But for now I am fixed.

Thanks.

> **TheThinker said:**
> For those of you using Gutsy and found that the Printer setup Window does not seem to get the printer working (even though it detects it), try this. Type and enter in the terminal:

sudo aa-complain cupsd


I found this worked for my HP 720C Deskjet right away. Just a Gutsy bug, I guess. I don't know if it'll work for wireless-printer setups but it may be worth a try.

P.S. Thanks to AKoine and others for posting similar suggestions!

You both are probably right, but I'm trying to get y HP DeskJet 722c working and what am I supposed to do after typing
```
 sudo aa-complain cupsd

```

When I do that it does this
```

darrious@ubuntu:~$ sudo aa-complain cupsd
Setting /etc/apparmor.d/usr.sbin.cupsd to complain mode.
darrious@ubuntu:~$ 

```
Now what?

P.S. I'm running Gutsy Gibbon 7.10
The printer worked fine in Edgy, but I just recently downloaded Gutsy, and that has been having problems.

---

### Post by PatricioLearner on 2008-06-06
Everything looks ok (hp4215 installed) but when I print nothing happens.
I think output of hp-check -r can be the key.  here is part of it. I should also mention that the hp4215 scanner does work!
Patricio

Initializing. Please wait...
warning: Invalid ppd_dir value: /usr/share/ppd/hpijs/HP
warning: Invalid drv_dir value: /usr/share/cups/drv/hp/

---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux patricio-desktop 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 i686 GNU/Linux

Distribution:
ubuntu 8.04

HPOJ running?
No, HPOJ is not running (OK).

Checking Python version...
OK, version 2.5.2 installed

Checking PyQt version...
OK, version 3.17 installed.

Checking SIP version...
error: SIP not installed or version not found.

Checking for CUPS...
Status: scheduler is running
Version: 1.3.7
.
.
.
----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/usb/officejet_4200_series?serial=CN5CJGI3BT' is a Hewlett-Packard officejet_4200_series all-in-one
device `avision:libusb:001:002' is a Hewlett-Packard ScanJet 5300C flatbed scanner
.
.
.

---

### Post by 11hjpphty76lkjj on 2008-06-06
Please run hp-check -t and post the entire output.

Thanks!

A

---

### Post by PatricioLearner on 2008-06-06
Here it the complete output of hp-check -r
Maybe it helps the troubleshoot.
thanks!

---

### Post by PatricioLearner on 2008-06-06
Here it is

---

### Post by yengamatic on 2008-08-24
Hi, I'm having some trouble installing the lastest version of HPLIP (2.8.7).

Basically it cannot install python2.5-dev package, because of its version. I have python2.5 installed, but version is 2.5.2-2ubuntu5, and python2.5-dev spects version 2.5.2-2ubuntu4.1. I know i could force the earlier version (ubuntu4.1), but from what i've seen in synaptic menu i should first uninstall current version and reinstall earlier one. Having maaaaaany packages already installed that depend on it, it's not an option... How can i install the requiered package?

Thanks.

---

### Post by gonkyouka on 2009-04-09
this guide rocks even to those totally noob to linux. i manage to install hp 900 inkjet printer on my xp and ubuntu workstations. thanks so much~

---

### Post by cctaber on 2009-04-16
I am using Ubuntu 8.10. Two of my HP printers do not print anything off of the web correctly (DeskJet 9800 and PhotoSmart 6280) and one does not print at all. My LaserJet 3700dn will not do anything. I have downloaded the hplip without success. I have tried un-installing and reinstalling as well as all of the things listed at the beginning of this HOWTO post. I have also tried different USB cables as well as an Ethernet cable, nothing works. Can anyone help?

---

### Post by sadicote on 2009-04-16
Thanks, i had been alarmed by the "If you do not install the plugins, your printer will not work" message, and was stupid enough to omit the step of setting up the printer--i actually thought "install missing plug-ins" would take care of the problem, by itself.

---

### Post by majagray on 2009-06-29
This worked great, especially for a noob like me. Just one thing - if you're installing a LaserJet 1020 and can't get it to work, try changing the default printer to LaserJet 1020**-2**. Turns out **that** was the printer I have, despite that not being what it says on the casing. After installing HPLIP off Synaptics, then the more up-to-date version straight from the site, I was amazed to find something as innocuous as that was the problem! 

So, if when it's checking your usb it "finds" a LaserJet 1020, but you can't get it to work, just see if switching to 1020-2 makes any difference.

---

### Post by BrittanyB on 2009-07-05
That's a great HOWTO. Worked like greased magic. Mucho thanks

---

### Post by dipinkrishna on 2009-07-18
**[Install HP printers in Linux ( ubuntu 9.04 jaunty, fedora, debian, redhat, Mandrake/Manrivi, openSUSE, Solaris, FREEBSD)]("http://blog.dipinkrishna.info/2009/07/install-hp-printers-in-linux-ubuntu.html")**


See [http://blog.dipinkrishna.info/2009/07/install-hp-printers-in-linux-ubuntu.html](http://blog.dipinkrishna.info/2009/07/install-hp-printers-in-linux-ubuntu.html)

---

### Post by colin.p on 2009-08-16
I am able to print with this printer,using a wireless connection to my router and so far seems to work ok, but the HP Toolbox will not detect my printer. It keeps saying that it is not installed using the CUPS backend.
"HP-Officejet-6500-e709n
-----------------------
Type: Unknown
Installed in HPLIP?: No, not using the hp: or hpfax: CUPS backend.
Device URI: socket://192.168.1.106:9100
PPD: /etc/cups/ppd/HP-Officejet-6500-e709n.ppd
PPD Description: HP Officejet 6500 e709n hpijs, 3.9.2
Printer status: printer HP-Officejet-6500-e709n is idle.  enabled since Sun 16 Aug 2009 09:55:25 AM EDT
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

The complete hp-check -t is attached.

The only reason I am going through this is I am a perfectionist freak and want to use all the features that the printer has.

edit: found the answer at [http://ubuntuforums.org/showthread.php?t=1146724&highlight=hplip+doesn%27t+detect+printer](http://ubuntuforums.org/showthread.php?t=1146724&highlight=hplip+doesn%27t+detect+printer)

I installed the python GTK2 dev (I think that was what is was) from synaptic and got the newest version of hplip (3.9.6) to install and now the printer is listed properly. It took a couple of hours and several searches but I found the answer.

---

### Post by dipinkrishna on 2009-09-03
:KS See [HP printer Installation Wizard for your Linux ( Boss,Debian,Fedora, ubuntu, suse .. )]("http://blog.dipinkrishna.info/2009/08/hp-printer-installation-wizard-for-your.html")... for an easy and more successful installation of your hp printers in linux..:KS

---

### Post by soheilsh on 2009-11-09
Hi,

I've just started using UBUNTU on my new dell mini9 laptop.
I tried to connect my printer (hp laserjet 6L) to my netbook but it does not detect it. and it asks for device URI which I don't know what it is.

I have only USB port on my laptop and I'm using the latest version of UBUNTU 9.10

I'll appreciate if somebody helps me.

Thank you

---

### Post by user1397 on 2009-11-09
> **soheilsh said:**
> Hi,

I've just started using UBUNTU on my new dell mini9 laptop.
I tried to connect my printer (hp laserjet 6L) to my netbook but it does not detect it. and it asks for device URI which I don't know what it is.

I have only USB port on my laptop and I'm using the latest version of UBUNTU 9.10

I'll appreciate if somebody helps me.

Thank you
Have you tried all of the steps in the first post?

---

### Post by soheilsh on 2009-11-11
> **ubuntuman001 said:**
> Have you tried all of the steps in the first post?

yes, I have installed hp device manager but it cannot find my printer either.
I tried all my USB ports but no luck. ((

---

### Post by user1397 on 2009-11-12
> **soheilsh said:**
> yes, I have installed hp device manager but it cannot find my printer either.
I tried all my USB ports but no luck. ((
what's your printer model?

---

### Post by soheilsh on 2009-11-12
> **ubuntuman001 said:**
> what's your printer model?

hp Laserjet L6

---

### Post by soheilsh on 2009-11-13
> **soheilsh said:**
> hp Laserjet L6

sorry, hp Laserjet 6L

---

### Post by user1397 on 2009-11-20
> **soheilsh said:**
> sorry, hp Laserjet 6L
Have you tried printing a test page?

---

### Post by Flopsy1923 on 2009-11-22
> **ubuntuman001 said:**
> This is a little guide on how to correctly install an HP printer (I think) for beginners, since so many people seem to have trouble with this. I have also provided a very basic scanner start up guide.  Here are the steps:

First of all, Connect your printer to your computer, and turn it on.

See if your printer gets autodetected by Ubuntu.  Simply go to  System > Administration > Printing > New.

If it doesn't find any or doesn't recognize your printer, try the following:

First check on _[this]("http://hplip.sourceforge.net/supported_devices/index.html")_ website if your printer is compatible with linux.

If it is compatible, then follow the instructions on [this]("http://hplipopensource.com/hplip-web/index.html") page to install and configure the drivers.

If even that doesn't work, then post here with your printer name and configuration.

Scanning:

For HP all-in-ones (such as the PSC series), after you have followed the above steps, put the paper you want to scan in the scanner and then go to Applications > Graphics > XSane Image scanning program. In XSane, click "scan" and then when it's done, click save as and save it wherever you want.

If you have a sole HP scanner, then you could try to just plug it in, turn it on, and try to scan it with XSane, but I don't gurantee that it will work.

***NOTE:  If you want to send a scan that you made on your linux box to a windows computer, it won't open it up. You have to right-click on the image, and go to "open with GIMP Image Editor". Then go to save as and click on "select file type (by extension)". Then scroll down to JPEG format and click ok as many times so that it saves. And then it's readable in windows.

Thank you, thank you, thank you. With your help, I installed my new HP printer on my Unbuntu system on my desktop computer in about 2 minutes! When I installed it yesterday on my Windows laptop, it took about 45 minutes because it hung up midway and required a lengthy call to HP tech support. My Linux mentor son was out of town for the weekend, so thank you so much for making it possible for me to proceed without my usual mentor.

---

### Post by frenchn00b on 2009-11-22
If I recall well this 
> ### printconf is the greatest for USB
# I permit to remove hplip
apt-get -f -y  remove   hplip

apt-get     install     [COLOR="Magenta"]printconf[/COLOR]


 is helping when the hp printer is USB.

---

### Post by frenchn00b on 2009-11-22
with what do  we configure the printer for hte command line? 

```
export ... 
```

---

### Post by mbeenham on 2009-12-02
Has anybody got a HP Deskjet 690 series printer working - if so I would appreciate a steer as I have spent quite a lot of time trying to get mine going.

I still have to boot Windows XP to print and would like to cut this final reliance. I know its an old printer, but I have two of them and don't see why I should throw out perfectly serviceable printers.

OK - the facts:
I am using jaunty (9.04)
HP697C on motherboard parallel port.

First I tried HPLIP v3.9.2 from the package since HP697C is supposedly supported. This finds my printer and configures it into CUPS. However if I try to print or get a status the green and yellow lamps on the printer blink (communication error) and I get error 5012 message (communication error). Switching the printer off and back on clears it until the next time I try to print or get status.
HPLIP 3.9.10 is no better so after digging for clues and finding a raft of issues surrounding HPLIP and parallel printers I gave up HPLIP as a dead parrot and deinstalled it.

Using cups 1.3.9 web interface I installled the Gutenprint v5.2.3 driver. This works with no communication errors but I cannot seem to find how to get an acceptable quality photo output - as good as that I get from the Windows XP driver.

Is there a dummies guide to tweaking the Gutenprint driver that doesn't assume you know how to use it in the first place?

I want to cut out MS Windows entirely so any thoughts/advice welcome.

Thanks
Martin

---

### Post by milea on 2009-12-03
I am new here and i really found it helpful... thanks guys

---

### Post by gotanothergrot on 2009-12-05
I would like to get my HP 1020 working again since upgrading to Karmic my printer is detected, I have downloaded HPLIP but have missing ppd files that are not listed, I would like some help walking me through this if anyone is willing.

---

### Post by raygj on 2009-12-16
> **gotanothergrot said:**
> I would like to get my HP 1020 working again since upgrading to Karmic my printer is detected, I have downloaded HPLIP but have missing ppd files that are not listed, I would like some help walking me through this if anyone is willing.

read this post
[http://ubuntuforums.org/showpost.php?p=7537983&postcount=124]("http://ubuntuforums.org/showpost.php?p=7537983&postcount=124")

---

### Post by exup1000 on 2009-12-19
Hi 
I have a working printer HP OfficeJet 6210 All in one. This was after following the install guide at hplipopensoure.

But my Scanner does not work. I launch Xsane and get failed to create file: Permission denied. If I click close it goes throug a detection and then pops up another error "Failed to open device 'hpaio:/usb/officejet_6200..."

If I run hp-check I get one error

[INDENT]Summary of needed commands to run to satisfy missing dependencies:
sudo aptitude install --assume-yes cupsddk cupsddk-drivers[/INDENT]

I have tried running that command a few times and it states its already loaded.


[INDENT]No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
[/INDENT]

There is also another error in the HP-check

[INDENT]----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
device `hpaio:/usb/Officejet_6200_series?serial=CN617EG2TY0454' is a Hewlett-Packard Officejet_6200_series all-in-one

[/INDENT]

I have tried running it as sudo and read the hplip scanning troubleshooting guide, everything checks out ok but not sure what they mean by ensuring sane is configure to hpiao-run. I checked that the dll.conf file contains an hpaio entry. Not sure what the -run means.

finally this is the tail of syslog when running xsane

[INDENT]Dec 20 00:02:16 TESTW100 xsane: io/hpmud/mlc.c 643: invalid MlcOpenChannelReply: cmd=81, result=1
Dec 20 00:02:16 TESTW100 xsane: failed to open pml channel: scan/sane/hpaio.c 666
Dec 20 00:02:19 TESTW100 xsane: io/hpmud/hpmud.c 327: device_cleanup: device uri=hp:/usb/Officejet_6200_series?serial=CN617EG2TY0454
Dec 20 00:02:19 TESTW100 xsane: io/hpmud/hpmud.c 339: device_cleanup: close device dd=1...
Dec 20 00:02:19 TESTW100 xsane: io/hpmud/hpmud.c 341: device_cleanup: done closing device dd=1
[/INDENT]

I am running ubuntu 9.10

Cheers

---

### Post by exup1000 on 2009-12-19
After some more digging around, I found some references to the .sane/xsane under the user profile not having normal permissions. The tip was to delete the files and let xsane recreate them.
This has fixed the first pop up error but I still get the second error, "Failed to open device 'hpaio:/usb/officejet...."

I have unistalled deleted the .sane folder and reinstalled it. No change.
I have also installed strace and monitored the output in a grep file i see alot of permission denied messages. See below.

open("/sys/bus/scsi/devices/6:0:1:0/vendor", O_RDONLY) = 11
open("/sys/bus/scsi/devices/6:0:1:0/model", O_RDONLY) = 11
open("/sys/bus/scsi/devices/6:0:1:0/type", O_RDONLY) = 11
open("/dev/scanner", O_RDWR|O_EXCL|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("/usr/lib/sane/libsane-net.so.1", O_RDONLY) = 9
open("/usr/lib/sane/libsane-net.so.1", O_RDONLY) = 9
open("./net.conf", O_RDONLYWARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
)            = -1 ENOENT (No such file or directory)
open("/etc/sane.d/net.conf", O_RDONLY)  = 12
open("/usr/share/hplip/data/models/models.dat", O_RDONLY) = 12
open("/dev/bus/usb", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 12
open("/dev/bus/usb/002", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 12
open("/dev/bus/usb/002/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/002/001", O_RDONLY)  = 13
open("/dev/bus/usb/002/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/002/001", O_RDONLY)  = 12
open("/dev/bus/usb/005", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 12
open("/dev/bus/usb/005/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/005/001", O_RDONLY)  = 13
open("/dev/bus/usb/005/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/005/001", O_RDONLY)  = 12
open("/dev/bus/usb/004", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 12
open("/dev/bus/usb/004/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/004/001", O_RDONLY)  = 13
open("/dev/bus/usb/004/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/004/001", O_RDONLY)  = 12
open("/dev/bus/usb/006", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 12
open("/dev/bus/usb/006/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/006/001", O_RDONLY)  = 13
open("/dev/bus/usb/006/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/006/001", O_RDONLY)  = 12
open("/dev/bus/usb/003", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 12
open("/dev/bus/usb/003/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/003/001", O_RDONLY)  = 13
open("/dev/bus/usb/003/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/003/001", O_RDONLY)  = 12
open("/dev/bus/usb/007", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 12
open("/dev/bus/usb/007/005", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/007/005", O_RDONLY)  = 13
open("/dev/bus/usb/007/004", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/007/004", O_RDONLY)  = 13
open("/dev/bus/usb/007/003", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/007/003", O_RDONLY)  = 13
open("/dev/bus/usb/007/002", O_RDWR)    = 13
open("/dev/bus/usb/007/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/007/001", O_RDONLY)  = 13
open("/dev/bus/usb/007/005", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/007/005", O_RDONLY)  = 12
open("/dev/bus/usb/007/004", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/007/004", O_RDONLY)  = 12
open("/dev/bus/usb/007/003", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/007/003", O_RDONLY)  = 12
open("/dev/bus/usb/007/002", O_RDWR)    = 12
open("/dev/bus/usb/007/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/007/001", O_RDONLY)  = 12
open("/dev/bus/usb/001", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 12
open("/dev/bus/usb/001/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/001/001", O_RDONLY)  = 13
open("/dev/bus/usb/001/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/001/001", O_RDONLY)  = 12
open("/dev/bus/usb/002/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/002/001", O_RDONLY)  = 12
open("/dev/bus/usb/005/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/005/001", O_RDONLY)  = 12
open("/dev/bus/usb/004/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/004/001", O_RDONLY)  = 12
open("/dev/bus/usb/006/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/006/001", O_RDONLY)  = 12
open("/dev/bus/usb/003/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/003/001", O_RDONLY)  = 12
open("/dev/bus/usb/007/005", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/007/005", O_RDONLY)  = 12
open("/dev/bus/usb/007/004", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/007/004", O_RDONLY)  = 12
open("/dev/bus/usb/007/003", O_RDWR)    = -1 EACCES (Permission denied)



cheers.

---

### Post by exup1000 on 2009-12-26
Any ideas or help on this scanning issue?

---

### Post by user1397 on 2009-12-26
> **exup1000 said:**
> Any ideas or help on this scanning issue?
I'm sorry if you thought that me being the OP I would know how to resolve your issue...the only reason I haven't replied is because I don't know how to help you.:(

---

### Post by exup1000 on 2009-12-26
No worries ubuntuman, hopefully somebody might in the forums.
I have posted a question on the hplip knowledge base, fingers crossed someone there might know.

Cheers

---

### Post by clandrummond on 2010-01-20
[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG] 				**HP Psc 1300 5012 communication error** 			
 			 			 		   		 		 		Hi, in desperate need of help I am afraid,
Just installed Ubuntu 9.10 after vista I never want to go near windows again, I want to make it clear I am a complete novice at this, wouldn't know what a command line was if it jumped up and bit me on the bum, let alone how to edit one.

Installed an HP PSC 1300 all in one printer via USB, system sees it, installs it without any trouble, as soon as I try to print it just hangs there in pending till it defaults and I get communication error 5012, also the message  /usr/lib/cups/backend/ hp failed.

I have removed and re-installed the printer and the latest version of hplip more than once but am getting nowhere, the printer and cable work fine when attached to my laptop which is running xp until i learn more about Linux.

Can anyone help me as my printer is essential

---

### Post by user1397 on 2010-01-20
> **clandrummond said:**
> [IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG]                 **HP Psc 1300 5012 communication error**             
                                                                Hi, in desperate need of help I am afraid,
Just installed Ubuntu 9.10 after vista I never want to go near windows again, I want to make it clear I am a complete novice at this, wouldn't know what a command line was if it jumped up and bit me on the bum, let alone how to edit one.

Installed an HP PSC 1300 all in one printer via USB, system sees it, installs it without any trouble, as soon as I try to print it just hangs there in pending till it defaults and I get communication error 5012, also the message  /usr/lib/cups/backend/ hp failed.

I have removed and re-installed the printer and the latest version of hplip more than once but am getting nowhere, the printer and cable work fine when attached to my laptop which is running xp until i learn more about Linux.

Can anyone help me as my printer is essential
K go to a terminal (applications > accessories > terminal) type:

```
gksudo gedit /etc/udev/rules.d/55-hpmud.rules
```Type your password and edit **GROUP** in the line:

 SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="??17", OWNER="lp", **GROUP**="lp", MODE="660", ENV{sane_hpaio}="yes"


to


**GROUP**="lpadmin"


Then save it and exit the text editor.


Now go back to the terminal and type:


```
sudo /etc/init.d/udev restart
```and try printing.

---

### Post by finlost on 2010-02-13
> **majagray said:**
> This worked great, especially for a noob like me. Just one thing - if you're installing a LaserJet 1020 and can't get it to work, try changing the default printer to LaserJet 1020**-2**. Turns out **that** was the printer I have, despite that not being what it says on the casing. After installing HPLIP off Synaptics, then the more up-to-date version straight from the site, I was amazed to find something as innocuous as that was the problem! 

So, if when it's checking your usb it "finds" a LaserJet 1020, but you can't get it to work, just see if switching to 1020-2 makes any difference.
I was able to print one test page when I appended "-2" to the printer name.  My HP 1020 is now dead again.  So frustrating...

```
This is my printer.conf file.  
# Printer configuration file for CUPS v1.4.1
# Written by cupsd on 2010-02-13 20:41
<DefaultPrinter HP-LaserJet-1020-2>
Info Hewlett-Packard HP LaserJet 1020
Location Carnivean
MakeModel HP LaserJet 1020 Foomatic/foo2zjs (recommended)
DeviceURI hp:/usb/HP_LaserJet_1020?serial=JL234K5
State Idle
StateTime 1266114271
Type 8388612
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
```

---

### Post by breimer273 on 2010-05-12
So I followed this tutorial yet my printer still is not showing up I have a HP Deskjet All-in-one F4280. I am not really sure what to say. It just isn't recognized even after manually installing the HPLIP. I am running Lucid. Anyone else been having this problem?

---

### Post by cheezeangel on 2010-05-14
I would just like to say thank you for this thread. I have followed the instructions on the HP site and here, and have successfully managed to get my Deskjet F4500 series printer working perfectly!

---

### Post by avinegar on 2010-06-28
I have installed Ubuntu Linux using WUBI on a second drive on my computer. I am trying to install an HP Laserjet 1300 printer. My computer is networked using a Linksys WRT54G router. The printer is plugged into a USB port of a Hawking HPS12U print server which is plugged into one port of the router. How do I get Ubuntu set up to print under these circumstances. 
 
Thank you.
 
avinegar

---

### Post by 11hjpphty76lkjj on 2010-06-28
Assuming you are trying to configure the printer using hp-setup and using HPLIP (HP Linux Imaging and Printing).  HPLIP does not support third party printer network sharing devices.  HPLIP does support the HP Jetdirect however.

This is because devices other than Jetdirect do not let HPLIP communicate with the printer.

In most cases, this is because port 9100 is not open on the device.

A

---

### Post by techunit on 2010-06-30
I have a HP Photosmart B8550 and the default don't give the correct controls. Because it isn't a normal printer (near professional quality dual tray printer that is prints a maximum of 13x19inch photos. It doesn't configure correctly.

---

### Post by gribbsy on 2010-07-07
Is anyone else having problems with HP LaserJets and Ubuntu 10.04?
I have a HP LaserJet 3015 and am running a dual boot with Windows 7.

Printer is automatically detected and works fine on:  Windows 7, Windows XP, LinuxMint, and older versions of Ubuntu.

But when I'm running Ubuntu 10.04, when I try to print it just adds the job to the print queue and it never prints.  After awhile I get a message saying that Ubuntu is unable to communicate with my printer.  (or something to that effect).  I can't even print a test page.

I have tried installing HPLIP following the directions given, but get the same behavior (can't communicate with the printer).  I have tried unplugging the power cord and usb cable and plugging them back in (as per the directions I am following).  But still not communicating.

Thanks in advance for the help.

---

### Post by MUY_Belgium on 2010-07-10
Please send the response of the commands

  cat /var/log/cups/error_log

---

### Post by yanivmomo on 2010-07-13
i'm using hp deskjet d1663 inject printer with os ubuntu 10.4 but i still cant print. the printer is kind of auto detected (instead of  ' hp deskjet d1663' there is  'hp deskjet d1600 series' but when i try to print there is nothing.even when i try to print a test page i see in the print status 'processing' but it still doesn't print

---

### Post by Nectaria on 2010-07-14
> **yanivmomo said:**
> i'm using hp deskjet d1663 inject printer with os ubuntu 10.4 but i still cant print. the printer is kind of auto detected (instead of  ' hp deskjet d1663' there is  'hp deskjet d1600 series' but when i try to print there is nothing.even when i try to print a test page i see in the print status 'processing' but it still doesn't print

Same here with an HP PhotoSmart C3180. I downloaded the HPLIP and installed the printer (using the driver for HP 3100 series) but I get no response when I try to print (even the test page).
Can anyone help please?

---

### Post by tsucol11 on 2010-07-14
Printing using a SMC7004ABR router & HP deskjet932C colour printer (connected to the routers parallel port)

To add deskjet 932C via SMC router using ubuntu 10.04 LTS

-system/administration/printing
- add
- network printer
- host = 192.168.2.1 (the router's IP address)
continue
- results will be --- host = 192.168.2.1, Queue = LPT1
continue
- highlight = HP & deskjet 932C
- chose recommended driver ie HP deskjet 932c hpijs,3.10.2(en)(recommended)
- installation concluded

you can now print in colour.

---

### Post by Cyclonate on 2010-07-15
Hi there

Sorry for re-hashing old issues nut I'm having trouble installing an HP Deskjet F2483. I've downloaded the hplip-3.10.05.run but when I type the install command in terminal I get:
" angelo@angelo-desktop:~$ cd Desktop
angelo@angelo-desktop:~/Desktop$ sh hplip-3.10.5.run
Creating directory hplip-3.10.5
Verifying archive integrity...Error in MD5 checksums: 229f7298a99ba86153cad12fbc11b8a3 is different from 7c966612d669ecd8ec29df44dda0ae1f
angelo@angelo-desktop:~/Desktop$ "

Q: what is MD5 checksums and how do we correct their errors?

Many Thanks

UBUNTU 9.10 Karmic Koala

---

### Post by dogbitedavehumphreys on 2010-07-19
Yellow.  All I print is yellow.  I followed the tutorial and successfully installed hplip 3.10.5 with HP Deskjet 3845

Any suggestions?  Thanks.

---

### Post by shelbyvision on 2010-07-30
I have an HP Deskjet 940c, which was detected automatically in the first two versions of Ubuntu I used. Now with 10.04, it acts like the printer doesn't exist. I've installed all the recommended drivers, gone to the HP site, nothing has worked. I searched every page of this thread for "940" and nothing came up, so am I the first one with this problem? Any help would be appreciated.
Thanks,
Steve

---

### Post by shelbyvision on 2010-07-30
[SOLVED] I went back to HP's download website. The first time I was there, I was advised to use the version in the repositories (hplip 3.10.2), so I installed that, and it didn't work. I went back and downloaded their current version (hplip 3.10.6). It was a long involved installation, but after it was all done, I had a working printer! :D

---

### Post by poodoopealeoaph on 2010-10-09
Ok, so I don't have the printer right here with me to work on but I am working on a desktop for someone and they need their hp s4235 AIO to work with ubuntu lucid. So, if I were to follow these steps on the spot when I show up to their house to fix the issue, will it work? if not, are there any special steps to take to make sure that I get it, instead of looking like an idiot in front of someone?

---

### Post by richlyn9 on 2010-12-02
I bought a deskjet 1050 and installed the hplip 3.10.9 but am not able to configure it on Lucid 64 bit.
Somehow the pdd for my printer does not show up
kindly take a look at my thread here [http://ubuntuforums.org/showthread.php?t=1616353&page=3](http://ubuntuforums.org/showthread.php?t=1616353&page=3)

---

### Post by antl on 2010-12-10
I have been working on this for a couple of days now and have tried several things already to get the auto install going.

To start with, I have already checked the compatibility and its good, this is ubuntu 10.04 and its on a laptop.

now when im in the terminal trying to get it started, I have as follow -

johndoe@johndoe-laptop:- $

The normal start up, but I have tried several paths, including the supposed  cd desktop.

I wonder if anyone has come across this problem and know how to correct me in my misfortune.

Thank you.

---

### Post by MIKE666 on 2010-12-23
Hello,

     I have to printers HP Deskjet D1660 and Lexmark X2670 , new out of the box, and can't get either of them to work. What can I say? Do not even know where to start.


Cheers


Mike

[email]oneidamj@hotmail.com[/email]

---

### Post by Patsfriend on 2011-01-08
Hello All,
I have trying for a couple of days to access the HP site for Linux drivers. It is down
and does not look like it will be up anytime soon.
Anyone have other solutions for my PSC-2350, using Ubuntu 9.10
Thanks,
togg

---

### Post by kokoshmusun on 2011-01-13
Is it possible to install HP drivers in a Windows XP virtual machine running inside Ubuntu and to use the printer that way?

---

### Post by nomko on 2011-01-13
> **kokoshmusun said:**
> Is it possible to install HP drivers in a Windows XP virtual machine running inside Ubuntu and to use the printer that way?
 
Of course that's possible.
Running Windows XP inside a virtual machine has no relationship to each other in terms of installing drivers. Inside a virtual machine you install a stand alone Windows XP with all its features. To use devices under Windows XP you have to install the proper driver for it to ensure the proper use of that device under Windows XP.
 
In fact, you're running XP not Ubuntu when you're using XP inside a virtual machine.

---

### Post by gmason on 2011-02-05
I am brand new to Ubuntu.  I am trying to get my HP PSC 500 to scan.  I got it to print but I cannot access the scan function (I get an error message saying, "scanner not connected").

For the record, the reason I am on Ubuntu is that my Dell Dimension E510 computer's operating system crashed (blue screen of death) while I was trying to connect the printer to the computer using a USB 2.0 to parallel printer cable I had just purchased.  A friend told me about Ubuntu, so here I am.

Furthermore, I wonder if anyone knows how I might possible get back to the other operating system to fix the BSOD problem,

Thanks for any help you can give me.

---

### Post by nomko on 2011-03-03
> **rachelstevens said:**
> HP LaserJet 1022 on Windows Vista installed and it worked fine for a year. From next (USB) connection to my laptop with Windows Vista does not recognize the printer. There was no way the driver to remove it, or I would just the HP folder in Program Files.
 
And what does this has to do with Ubuntu? You're talking Windows now...

---

### Post by nomko on 2011-03-03
> **gmason said:**
> I am brand new to Ubuntu. I am trying to get my HP PSC 500 to scan. I got it to print but I cannot access the scan function (I get an error message saying, "scanner not connected").
 
For the record, the reason I am on Ubuntu is that my Dell Dimension E510 computer's operating system crashed (blue screen of death) while I was trying to connect the printer to the computer using a USB 2.0 to parallel printer cable I had just purchased. A friend told me about Ubuntu, so here I am.
 
Furthermore, I wonder if anyone knows how I might possible get back to the other operating system to fix the BSOD problem,
 
Thanks for any help you can give me.
 
There's a short how-to on my site for a HP b110a printer. The best part is, it can also be used for other models of HP printers. Try that and see if that helped you ;)

---

### Post by krishnitdgp on 2011-03-03
I have problem with my HP Laserjet 1018. The printer get detected automatically. when i turn it on a HP Device Manager window pops up for plugin installation. I checked the recommended installation option and click next but few moment later a window pops up with massage "network connection not detected" I checked internet connection its ok. I think the website from where the plugin will be downloaded is offline.
  
    I tried the advance option " install an existing local copy of plugin file". I browsed the plugin file and selected it but the next button in the window get disabled and I can not install the plugin. I can not use my printer without that hplip plugin.

    I am new about ubuntu. please someone help me to get install the plugin. I have attached some screenshots.

---

### Post by imasynper on 2011-04-05
Bought a HP photosmart C4780. Ubuntu does automatically recognize it and I can print, but the printer has wireless capabilities but cannot hook it up because the disk they sent with it doesnt work for ubuntu. 
Any help would be awesome! 
Thanks

---

### Post by user1397 on 2011-04-06
> **imasynper said:**
> Bought a HP photosmart C4780. Ubuntu does automatically recognize it and I can print, but the printer has wireless capabilities but cannot hook it up because the disk they sent with it doesnt work for ubuntu. 
Any help would be awesome! 
Thanks
perhaps this thread can help: [http://ubuntuforums.org/showthread.php?t=1314886](http://ubuntuforums.org/showthread.php?t=1314886)

---

### Post by oscarthearsenalplayer on 2011-08-28
hey,
my printer is an hp deskjet 5500 series and when i print it does that noise, which usually means its printing but nothing appears on the paper!

---

### Post by mikebravo on 2011-10-19
HP LaserJet M1212nf MFP  and   Ubuntu 11.10  HPLIP-3.11.7-1ubuntu3 

I have been down this road before, and now I would like to know what is going on.  I went to HP's support site and entered my information and got a reply that Ubuntu has HPLIP built in and that I should really use it. They were right, my installed programs include HPLIP-3.11.7, wherever it is. While I was looking around, I installed HPToolBox. When in HPTOOLBOX I thought Install "PLUG IN" would be just the thing. **Nope**. I went with the default to download but it came back with "ERROR: Plug-in file does not match its digital signature. ... Error code 2". The other choice is to navigate to the HPLIP file. I do not know where it is or how to find it or what to do with it when I get there. Will the ToolBox handle it, or will I have to run it? install it? Pray to the printer gods? Why does Ubuntu get all its ducks in a row and not take the final step to make it work, or at least tell the user what he needs to do?  Is it a secret? Please tell me how to use the tools HP and Ubuntu have provided, or tell me they are worthless.

---

### Post by EvilCasper on 2011-11-25
I can't get my printer to install on network

---

### Post by andrea10 on 2013-09-03
how can i get my hp deskjet 3510 e-all-in-one to install on my two linux computers?

---

### Post by Bucky Ball on 2013-09-03
[B][I]Thread Closed

Reason:[/I][/B] To prevent necromancy! Please start a new thread for your printer problems as this one is ancient and info may be redundant. Thanks. ;)

---

### Post by coffeecat on 2013-09-03
And moved to Outdated Tutorials & Tips.

---

