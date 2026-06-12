---
title: "HOWTO Install Samsung Unified Printer Driver"
date: 2007-01-18
forum: Outdated Tutorials &amp; Tips
---

### Post by tweedledee on 2007-01-18
Guide to installing Samsung printers & the Unified Linux Driver:

**[color=blue]4 May 2013:  This thread is now completely out of date.  I no longer plan to update or maintain any aspect of it, or to reply to future posts.  Go to [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) to get current repository information and support, including forums which I do monitor.[/color]**

**[color=blue]NEW 9 June 2012!  I have configured forums directly on the [SULDR website](http://www.bchemnet.com/suldr/forum/) that are intended to replace this thread.  I will continue to monitor this thread, but future updates and time will be focused on the website and associated forums.[/color]**

8 March 2011: Simplified the guide posted here to provide only the repository option, all other details pushed off onto the repository website (which has been extensively revised and updated).
28 May 2012: Various minor revisions and updated for newest package versions; extensive website updates.
9 June 2012: More revisions, another new set of packages, new forums, and more website updates.

The packages released on 28 May 2012 (4.00.35-1) include several "fix" packages that should only be used in specific circumstances, but do explicitly address many problems encountered over the last six months or so (and that are not addressed in other packages).  You can read about these in your package manager or on the website, under the printing and scanning troubleshooting sections.  I have also updated the troubleshooting and questions on the website to be easier to navigate and more current, hopefully simplifying the process of getting everything running for those who aren't fortunate enough to have it all work immediately.

**Introduction**
This guide presents my recommended approach to installing a working driver for your Samsung printer (for all Debian-based distributions).  If you are looking for alternatives, [look here](http://www.bchemnet.com/suldr/alternatives.html).  Much more information and technical details are available on the [my dedicated website for the driver](http://www.bchemnet.com/suldr/), such as removal of the manually installed drivers and why I do not recommend that you ever install the drivers directly from Samsung.

***When posting to ask for assistance***, you must provide (at a minimum) your printer model, how it is connected, the specific problem, any error messages you see, which driver you are using (and version if the Unified Driver), and how you installed the driver.  (And if you aren't using the repository, you are welcome to post but my default response will be to at least try using the repository, and then to help only if that doesn't solve the problem.)  Without this information, it is unlikely anyone will be able to help you, and your question may well be entirely ignored.  I monitor this thread and will respond to public posts (although it may take a few days or occasionally weeks); do not attempt to send me a private message or email.  On the other hand, I don't always know how to solve the problem, which is why I insist on public posts, and other readers are welcome to jump in and help out.

**Using the Samsung Unified Linux Driver repository**
This method installs the proprietary Samsung drives while avoiding all the problems associated with the manual installation and allowing you to retain control over exactly what gets installed.  **For full information, go the repository:** [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/).  The *short* version (meaning that if you run into problems, check the website before posting for assistance) to getting it up and running is:

1. Add the following line to your /etc/apt/sources.list, by editing the file as root (or using sudo, for example "sudo gedit /etc/apt/sources.list"), or by using Synaptic or other GUI to add a repository.  (Be aware that this is a binary-only repository, although an empty source repository is provided to avoid occasional errors from configurations expecting it to exist.) ```
deb http://www.bchemnet.com/suldr/ debian extra
```

2. Install the GPG key for the repository.  You can either (i) execute (as root or using sudo in a terminal): ```
wget -O - http://www.bchemnet.com/suldr/suldr.gpg | sudo apt-key add -
``` or (ii) download it ([http://www.bchemnet.com/suldr/suldr.gpg](http://www.bchemnet.com/suldr/suldr.gpg)) and add it to your keys via Synaptic, other GUI, or by (as root or using sudo, in a terminal): ```
apt-key add suldr.gpg
```  (If you skip this step, you will get warnings about installing unauthenticated packages.)

3. Refresh your repository listings (apt-get update or in a GUI), and then you should see the samsungmfp-* packages corresponding to the Samsung Unified Linux Driver.

**Very important:** you **must** have completely removed all prior installations of the Unified Linux Driver before using the .debs (i.e., installations from downloading and using the installer directly from Samsung); see [the appropriate uninstallation instructions for your driver version for more details](http://www.bchemnet.com/suldr/).

Just installing the samsungmfp-driver package should enable full printing support; for USB scanning, install the samsungmfp-scanner package; for network scanning, install the samsungmfp-configurator-qt4 package.  (The driver package contains all the binary bits, the data package has all the ppd files so CUPS can figure out how to talk to the printers.)  The Configurator and other packages are really only necessary in a subset of cases (such as if you need network scanning), or if you happen to like the Configurator interface.

**Problems printing?**  See the [repository website printing troubleshooting page](http://www.bchemnet.com/suldr/printing.html) *before* posting for help; many common questions are addressed there.

**Using a scanner:** if you are trying to use your printer as a scanner, you will usually need to add yourself to the "lp" group after installing the appropriate packages.  You will then to log out and back in for the change to take effect.  (You should be reminded of this when installing the package by the package manager, but it doesn't always work.)  If you still have trouble scanning, see the [repository website scanning troubleshooting page](http://www.bchemnet.com/suldr/scanning.html) *before* posting for help; many common questions are addressed there.  Also make sure that you can print before worrying about scanning.

**The Samsung Smart Panel and Printer Utilities**
Samsung also provides additional utilities for certain printers.  Since they are printer specific (unlike the Unified Driver, downloading the Smart Panel for a different printer model than your own will often not work), and not available for the CLP-550N, I have never tested these.  *These utilities pose a security risk to your system.*  See the repository main page for details on these, and why you should consider the implications of installing them.  *The page also explains why I will not be producing .debs for these programs, so please do not ask me to.*

**Reading this thread**
This thread is huge and has been running a long time, which is why I've moved as much as I can off this forum and into my website.  As new details get posted, problems fixed, etc., I track them and update packages, this post, and the website accordingly.  Therefore, if you have a particular problem, start reading from the most recent posts backward.  I've also restructed this guide twice and the driver has undergone major changes since the original post, which could lead to confusion if you start at the beginning.  As of May 2012, essentially everything through approximately post 960 that seems generally useful to multiple users has been incorporated into the packages and/or the website, so chances are you can skip everything prior to about that region when looking for assistance.

**A request: contact Samsung**.  Please look at the [first question here](http://www.bchemnet.com/suldr/questions.html) and then contact Samsung about the issues raised.  I've spent hundreds of hours (as of have other users) trying to create workarounds for issues that Samsung should be able to address.  However, no change in the drivers or installation process is likely unless many of the *thousands* of users of this repository and forum make their voices heard.

**Acknowledgments**
First, thanks to many posters who have provided feedback and helped with testing over the years.  I don't even know how many are still using this driver, but thanks to all of you.  Particular users who have contributed solutions that I've incorporated into the repository packages or alternative solutions include hokiejp (eglibc 64-bit solution, for network scanning); gaboro (eglibc 32-bit solution testing for the same problem); Rodolfo Medina on the Debian forums (ppd-only solution guide); tapanit (work-around for scanning across complex networks); n3ck and ezekiel_quacks (USB scanning work-around solutions); rlar (network scanning broadcast solution); vyvee (usblp fix); b1b1 (pdf to ps printing problems fix).  All these individuals are linked to for specific solutions if you investigate the website for solutions to problems, although fortunately most of the problems solved by these individuals are either no longer an issue or automatically resolved by repository packages.

---

### Post by dav3c on 2007-02-13
Hi tweedledee,

First of all, thanks for your installation guide, I was near to become crazy with my CLP 550...
I have done all points with success, but my printer still doesn't work.
When I print it goes always on pause, and nothing appens..

Do you know what it could be?

ps. this printer is on a network

Thanks,

dav3c

---

### Post by tweedledee on 2007-02-15
> **dav3c said:**
> When I print it goes always on pause, and nothing appens..

When you say "pause," what do you mean?  I have encountered a few files that seem unable to print (my printer simply sits there "processing" forever, or in one case actually threw an error).  I haven't figured out yet what common feature they have that does it.  However, most documents print without any trouble, from any program.  I plan to run some more tests on this issue, but it will probably take me a few days.

Samsung also released a newer driver since I posted this guide, 20070125...., so I will experiment with that as well to see if there is some significant difference between the two.

---

### Post by dav3c on 2007-02-16
I'm talking about a little red line that appears when printing which says my printer is in pause.
See the image below:
[IMG]http://www.ngiuliani.com/images/Schermata.png[/IMG]

---

### Post by myke on 2007-02-16
gg

---

### Post by tweedledee on 2007-02-18
> **dav3c said:**
> I'm talking about a little red line that appears when printing which says my printer is in pause.


Okay, a few more questions.
1. Do you have the network configured to use a static ip on your network, or are you using a host name?
2. Can you succesfully ping the printer and/or access it via a web browser?
3. Have you previously (or currently) had this same setup working in another operating system?
4. Can you print a test page?
5. Are you using the 2006 or 2007 drivers?
6. Are you running any sort of firewall?  (If yes, does the printer work if you temporarily disable the firewall?)

Naturally, my printer is workly perfectly today, even on documents it previously didn't like, so I can't easily reproduce your problem without some of the above information.

---

### Post by dav3c on 2007-02-18
I have a printer IP and I can access by the browser ([http://192.168.2.114)](http://192.168.2.114)).
I have the same printer on XP on two different PC and it works greatly.
It does not print the test page. The only thing I could print it was when I put IPP instead of Jet Direct, don't ask me why, I just tried... [http://ubuntuforums.org/images/icons/icon10.gif](http://ubuntuforums.org/images/icons/icon10.gif)
I downloaded the last drivers on samsung.com (I think are the lastest).
Hi, 
thanks for the help man, but I'll understand if you are bored...

I do have a firewall. I tried to disable it, but nothing change...

The only paper * which I could print was using the foomatic-gui 0.7.6.

* in this paper is written : 

POST / HTTP/1.1
Content-Length: 262
Content-Type: application/ipp
Host: 192.168.2.114
User-Agent: CUPS/1.2.4
Expect: 100-continue

and then some thing unreadable between:

printer-........-natural-language it-itE print

Those are all information I've got.

Thanks again,

Ciao ciao

---

### Post by dav3c on 2007-02-18
:lolflag:  I did it!!!!!!!
Finally is just like every time.... Just read....
I read the Unified Driver Help
 >Troubleshooting>If printer doesn't print> 

9. I can't print on IPP printer.
If your printer or MFP is one of the following models: 
Mono Laser Printers
ML-1450, ML-1510, ML-1520, ML-1610, ML-1710, ML-1740, ML-1750, ML-2010, ML-2150, ML-2150, ML-2250, ML-2550S, ML-2550, ML-2560, ML-3560, ML-6060, ML-7300 
Color Laser Printers
CLP-500, CLP-510, CLP-550, CLP-600, CLP-650 
Laser MFP
SCX-4100, SCX-4200, SCX-4x16, SCX-4x20, SCX-4x21, SCX-6x20, MFP-560, MFP-750 
you cannot use IPP protocol for network printing because of a known incompatibilty of the models with IPP implementation in CUPS. Please, use socket or LPD ports instead to connect to these models. 

I just change the socket from IPP to LPD (without "http://") and it prints!!!!

Thank you anyway for your help.
Regards

---

### Post by tweedledee on 2007-02-18
I'm glad it's working.  I will update my original post to reflect the problems (and solution) you have had.

---

### Post by Marcelo Fernández on 2007-02-20
If somebody is getting "I/O Error" when trying to scan with a Samsung SCX 4200 MFP in Ubuntu Edgy 6.10 (AMD64), take a look at this:

[http://www.ubuntuforums.org/showthread.php?t=245545&page=2eh](http://www.ubuntuforums.org/showthread.php?t=245545&page=2eh)

Regards,
Marcelo

---

### Post by bektom on 2007-02-23
Dear tweedledee,

Thanks a lot for the howto, it worked for my network printer,

Samsung SCX-4521F

Additional comments:
during the Unified Linux Driver Installer gui one should select "manual select", then click on lpd:// (in the Network field) and write the IP address of the printer after ldp:// 
For the driver one should select Samsung SCX-4x21 Series

Thanks again

bektom

---

### Post by Goliath! on 2007-03-17
tweedledee, Thank You!!  Thank you for debugging Samsung's code and sharing it.

btw, my ML-2571n installed fine with their installer once YOU fixed it.

btw2, Samsung's web site doesn't work with Firefox (can't see some things, can't download at all), so I had to install IEs4Linux.  Warning: installing IEs4Linux will pollute your machine with downloads from the evil empire M$.  Samsung's website doesn't work great with IEs3Linux but at least I was able to download.

---

### Post by tweedledee on 2007-03-18
> **Goliath! said:**
> tweedledee, Thank You!!  Thank you for debugging Samsung's code and sharing it.

btw, my ML-2571n installed fine with their installer once YOU fixed it.

btw2, Samsung's web site doesn't work with Firefox (can't see some things, can't download at all), so I had to install IEs4Linux.  Warning: installing IEs4Linux will pollute your machine with downloads from the evil empire M$.  Samsung's website doesn't work great with IEs3Linux but at least I was able to download.

Glad it worked.

Firefox should work with the Samsung website - provided you have Flash installed and Javascript enabled.  Their site suffers from the same usability problem of many corporate sites - if you don't enable every advanced feature, nothing works.

---

### Post by Rick O'Brien on 2007-03-23
> **dav3c said:**
> Hi tweedledee,

First of all, thanks for your installation guide, I was near to become crazy with my CLP 550...
I have done all points with success, but my printer still doesn't work.
When I print it goes always on pause, and nothing appens..

Do you know what it could be?

ps. this printer is on a network

Thanks,

dav3c

I had similar problems trying to get my new Samsung ML-2510 to work. It also is connected to a print server. I downloaded and installed the latest Samsung drivers. I tried a number of forums and CUPS sites without success. The printer would show as ready but jobs would show as stopped and I could not resume them.

I stumbled upon a solution using the CUPS web interface which is available from your browser at [http://localhost:631/admin](http://localhost:631/admin)

My printers were listed but the ML-2510 showed a message saying that the file rastertosamsungspl was unavailable due to a permissions problem. I checked two directories: /usr/lib/cups/filter and /etc/cups/ppd

In /etc/cups/ppd I noticed the following: 
/etc/cups/ppd # ls -l

-rw-r--r-- 1 cupsys lpadmin 17240 2005-12-04 18:37 DeskJet-692C.ppd
-rw-r--r-- 1 cupsys lp          10681 2007-03-22 20:49 ML-2510-Series.ppd

I issued the following command:
chgrp lpadmin ML-2510-Series.ppd

File details should now look like this:

-rw-r--r-- 1 cupsys lpadmin 17240 2005-12-04 18:37 DeskJet-692C.ppd
-rw-r--r-- 1 cupsys lpadmin 10681 2007-03-22 20:49 ML-2510-Series.ppd

In /usr/lib/cups/filter I noticed the following:
/usr/lib/cups/filter # ls -l

-rwxr-xr-x 1 root root   4856 2006-09-27 06:41 commandtocanon
-rwxr-xr-x 1 root root   5748 2006-09-27 06:41 commandtoepson
lrwxrwxrwx 1 root root     12 2006-11-05 16:57 cupsomatic -> foomatic-rip
lrwxrwxrwx 1 root root     25 2006-11-05 16:57 foomatic-rip -> ../../../bin/foomatic-rip
-rwxr-xr-x 1 root root   4692 2006-10-09 12:56 gziptoany
-rwxr-xr-x 1 root root  41808 2006-10-09 12:56 hpgltops
-rwxr-xr-x 1 root root  26512 2006-10-09 12:56 imagetops
-rwxr-xr-x 1 root root  53812 2006-10-09 12:56 imagetoraster
-rwxr-xr-x 1 root root   5628 2006-10-09 12:56 pdftops
-rw-r--r-- 1 rick rick  22085 2006-07-24 03:29 pscms
-rwxr-xr-x 1 root root  39040 2006-10-09 12:56 pstops
-rwxr-xr-x 1 root root   1904 2006-09-22 03:44 pstopxl
-rwxr-xr-x 1 root root   1872 2006-09-22 03:44 pstoraster
lrwxrwxrwx 1 root root     13 2006-11-05 16:52 rastertodymo -> rastertolabel
-rwxr-xr-x 1 root root  14044 2006-10-09 12:56 rastertoepson
-rwxr-xr-x 1 root root  27772 2006-09-27 06:41 rastertogutenprint.5.0
-rwxr-xr-x 1 root root  13092 2006-10-09 12:56 rastertohp
-rwxr-xr-x 1 root root  14384 2006-10-09 12:56 rastertolabel
-rw-r--r-- 1 rick rick 158306 2006-07-24 03:29 rastertosamsungpcl
-rw-r--r-- 1 rick rick 324826 2006-07-24 03:29 rastertosamsungspl
-rw-r--r-- 1 rick rick 406452 2006-07-24 03:29 rastertosamsungsplc
-rwxr-xr-x 1 root root  36724 2006-10-09 12:56 texttops

File ownerships and permissions were wrong for the samsung raster files.

I issued the following commands:

/usr/lib/cups/filter # chown root: rastertosamsung*
chmod a+x rastertosamsung*

Details for the affected files should now look like this:

-rwxr-xr-x 1 root root 158306 2006-07-24 03:29 rastertosamsungpcl
-rwxr-xr-x 1 root root 324826 2006-07-24 03:29 rastertosamsungspl
-rwxr-xr-x 1 root root 406452 2006-07-24 03:29 rastertosamsungsplc

I must have missed a step when installing the Samsung drivers. Hopefully this helps with your problem.

Rick

---

### Post by tweedledee on 2007-03-23
> **Rick O'Brien said:**
> I must have missed a step when installing the Samsung drivers.

I don't believe so - all my corresponding files for the CLP show up as you indicated before making the ownership changes, so apparently that's just how the installer works.  I'm not sure why you needed to change them to get it to work for your printer, but I'll note it in the original post.

---

### Post by Rick O'Brien on 2007-03-23
> **tweedledee said:**
> I don't believe so - all my corresponding files for the CLP show up as you indicated before making the ownership changes, so apparently that's just how the installer works.  I'm not sure why you needed to change them to get it to work for your printer, but I'll note it in the original post.

I forgot to mention that I also did the permissions and ownership changes on the file pscms

I'm guessing that the execute permissions were more important than the file ownership, but I just thought that everything should look consistant.

Rick

---

### Post by tweedledee on 2007-03-23
> **Rick O'Brien said:**
> I forgot to mention that I also did the permissions and ownership changes on the file pscms

I'm guessing that the execute permissions were more important than the file ownership, but I just thought that everything should look consistant.

Rick

Hm - I had missed that you changed the permissions as well (though it's rather clear in your message).  You are correct in that those files should have execute permissions, that was likely your problem.  Yet another quirk of the installer, I guess.  Thanks for posting the fix.

---

### Post by blackest_knight on 2007-03-28
Printer Samsung ML-2510/XEU

first off samsung don't admit to this variant however the couple of variants they did list seem to use the same driver. 
Second yes Samsungs website seems IE Centric I had to download the driver with IE in windows 

The driver file is 20070129102958984_UnifiedLinuxDriver.tar.gz

I downloaded it directly to my ubuntu desktop (you can get an ext3 driver for XP)
and entered the following instructions in a bash terminal.

tar xzf 20070129102958984_UnifiedLinuxDriver.tar.gz
cd cdroot
 sudo su
./autorun

This brought up the graphical installer followed the instructions on screen.
Printer works fine
I think the driver version is 2.00.92 or similar (the version on the cd was 2.00.62 and I got nowhere). I haven't tried network printing yet or seen a way to adjust the printer quality I have tried a couple of Jpegs and the quality was quite acceptable and very fast. 
This was on ubuntu Dapper connected via usb. (no parallel port on my laptop)

hope this helps someone else out the printer is currently available at PCWorld for £59.99
(if they have any in stock) Toners supposed to be good for 1000 pages the real toner cartridge which costs about the same as the printer is good for 3000 pages.

---

### Post by John Doe on 2007-04-01
Has anyone tried to install Samsung's Unified Printer Driver in Ubuntu 7.04 beta with any success?

---

### Post by nashjc on 2007-04-04
I've followed your suggestions and the /bin/sh -> /bin/bash did get the installer to fire. Thanks. 

Now I cannot seem to get the scanner detected properly. Printer prints test page fine, so I think that the print side is OK.

I found

sane-find-scanner

DID find the scanner, both on a Compaq Presario 1540 (Dapper 6.06) and on an Acer 5050 (Edgy 6.10). But 

scanimage -L 

says "no scanners identified". 

Anyone have suggestions?

I'll also post on another thread on this subject. Apologies for that, but this material seems scattered about.

JN

---

### Post by myke on 2007-04-04
You might want to try this suggestion which worked for me:

[I]
a: in a terminal, type "sudo chmod -s /usr/bin/xsane"
b: sudo edit /etc/sane.d/dll.conf, and comment out (add a "#") in front of the line that says "smfp" (probably the last line).
If you only do (a) and not (b), xsane will crash.
[/I]

Though I do not have a multi-function printer, my scanner quit being detected when I installed the Samsung unified driver.   My scanner is a Canon.   When I followed the 2 steps noted above that another fine forum member suggested, my scanner became detected and commenting out the "smfp" that the unified printer driver had put in didn't affect how the printer works.  Both now excellently.   This might work for you but I'm no expert.

---

### Post by nashjc on 2007-04-07
The problem appears to be found, but not the solution. At least not immediately.

I downloaded Samsung's (Linux) Unified Driver 2.0.93 for the SCX 4521 and installed it, or so I thought. However, when I look in /usr/lib/sane there are two bad links
libsane-smfp.so.1 and libsane-smfp.so

There don't seem to be any "real" library files of an appropriate name anywhere. I suspect someone forgot to pack them in the tarball. 

If anyone who has a working system can find the files these links are supposed to point to, maybe we can get them posted somewhere. (I have a server or two.) I can be contacted as nashjc  _at_ uottawa.ca.

JN

---

### Post by nashjc on 2007-04-07
Now have print and scan running (have not tested fax, but very unlikely to use it; copy works).

Solution was to uninstall SamsungUnifiedDriver (2.0.93 - 20070324101840703_UnifiedLinuxDriver.tar.gz) and re-install it. I also had tried a lot of the suggestions above and in links thereto and had to reset these e.g., the smfp line in dll.conf, and the root operation of xsane. None of these appear to be needed with new driver.

However, the libsane-smfp library file IS missing. I've sent a msg to Samsung, but will not hold my breath. Fortunately in some other Samsung files from related devices, notably 20070129124018750_UnifiedLinuxDriver.tar.gz, the cdroot/Linux/i386/at_root/usr/lib/sane/libsane-smfp.so.1.0.1 file (158Kb) can simply be copied to /usr/lib/sane/ 

With that, my scx-4521 is printing AND scanning.

Now if only Samsung would fix the Flash Crash mess on their website. (I got round this by using Konqueror that did NOT have Flash installed -- pages don't look quite right, but at least I can see them.)

JN

---

### Post by tweedledee on 2007-04-08
> **nashjc said:**
> Now have print and scan running (have not tested fax, but very unlikely to use it; copy works).

Thanks for providing those details.  I haven't tried the latest driver yet, I'm a firm believer in "if it ain't broke, don't fix it" when it comes to drivers.  I've updated the original post to highlight the recent problems.

---

### Post by nashjc on 2007-04-11
I'd echo "If it ain't broke ...".  I avoid driver updates except when there are problems.

JN

---

### Post by rdelfin on 2007-04-23
Hey TweedLedee!

Your instructions to edit the install.sh file and the executing it worked like a charm.  Now I'm finally printing in my Samsun ML-2510.  

Many many thanks man!!!

---

### Post by ahitchman on 2007-05-15
Does anyone have any idea what this problem reported in /var/log/cups/error_log is:

```

I [15/May/2007:22:11:19 +1000] Job 48 queued on "StudyColourLaser" by "avadmin".
I [15/May/2007:22:11:19 +1000] Started filter /usr/lib/cups/filter/pstops (PID 19928) for job 48.
I [15/May/2007:22:11:19 +1000] Started filter /usr/lib/cups/filter/rastertosamsungsplc (PID 19929) for job 48.
I [15/May/2007:22:11:19 +1000] Started backend /usr/lib/cups/backend/lpd (PID 19931) for job 48.
[B]E [15/May/2007:22:11:19 +1000] PID 19929 (/usr/lib/cups/filter/rastertosamsungsplc) stopped with status 5!
[/B]I [15/May/2007:22:11:19 +1000] Hint: Try setting the LogLevel to "debug" to find out more.
E [15/May/2007:22:11:19 +1000] [Job 48] Unable to open input
I [15/May/2007:22:11:21 +1000] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=19933)

```

I've followed this guide and the install (2007... drivers) seems to work correctly, but I can't get anything to print!

Andy.

---

### Post by komasoftware on 2007-05-18
This worked for me (7.04 Feisty) :

* download driver from Samsung (Unified driver)
* Simply choose add printer in System-> Administration -> Printing
* For me the printer is detected, choose install driver, select the PPD file from the downloaded archive

Next when you try to print, I got the error : rastertosamsungsplc failed

Now simply :

sudo cp ./cdroot/Linux/i386/at_root/usr/lib/cups/filter/rastertosamsungsplc /usr/lib/cups/filter/

to copy this filter to your cups filter directory. Try to print again. Success ! :)

PS : if you download the wrong driver (Linux instead of Unified), you will see : /usr/lib/cups/filter/ppmtosplc failed
Problem is that the interface will not allow you to install the Unified driver anymore (already install this PPD file message). You can fix this by 

cp /home/koen/samsung-printers/cdroot/Linux/noarch/at_opt/share/ppd/CLP-300splc.ppd  /usr/share/ppd/custom

to overwrite the PPD file with the Unified version.

Good luck

---

### Post by ahitchman on 2007-05-19
Just in case it helps someone else, I fixed my problem (two posts up). After many hours of mucking around, one, some or all of the following got things working:

[LIST]
[*]Installed foomatic, and recommended packages.
[*]Uninstalled and reinstalled the driver.
[*]Changed ownership and permissions as mentioned elsewhere in this thread.
[/LIST]

Andy.

---

### Post by johnzbesko on 2007-05-29
I have been able to print in the past and also with the latest unified driver. Unfortunately, I cannot scan, even though I have been able to in the past (Mandriva 2005?). Back then I had to muck around with a lib file and binary-edit a text reference within it.

Today, the Samsung GUI Unified Driver Configurator simply crashes when I select the scanner display. Also, the GIMP is hung loading the xsane plugin. Checking the system logs and other usual suspects reveals nothing to me.

I have an SCX-4100 (and Feisty) and any help is greatly appreciated.

---

### Post by nm newbie on 2007-06-09
i have a samsung scx-4725fn mfp.
everything worked ok except the root thing for the scanner.
i tried your idea:
a: in a terminal, type "sudo chmod -s /usr/bin/xsane"
b: sudo edit /etc/sane.d/dll.conf, and comment out (add a "#") in front of the line that says "smfp" (probably the last line).
If you only do (a) and not (b), xsane will crash.

my scanner is not detected anymore.

is there anyway to reverse command "a"?

command "b" i can change back. should there be " around the #?

i am not complaining.  any tip or help would be appreciated.

thank you

---

### Post by tweedledee on 2007-06-09
> **nm newbie said:**
> is there anyway to reverse command "a"?


sudo chmod +s /usr/bin/xsane

---

### Post by nm newbie on 2007-06-09
thanks for the quick reply tweedledee.

tried that but it didn't work.

uninstalled xsane and reinstalled xsane. still nothing. then went to configurator and clicked on scanner and there it was. then properites, can do basic scan from there, which will work for me at the present time. 

later a fresh install will get me back to the "root" problem, but for now all is well.

why is it a problem to run xsane in root?

thanks again for your help:popcorn:

nm newbie

---

### Post by tweedledee on 2007-06-09
> **nm newbie said:**
> why is it a problem to run xsane in root?

Running anything unnecessarily as root is potentially a security problem; in this case, it means that if xsane has a security bug that would normally only provide limited system access, running as root might give someone full access.  However, if you keep your system patched, this is probably minor.

It's more likely to be a pain because the resulting images are owned by root, so you have to change the owner to move/delete/change the files (or do all those things as root as well).

I'm glad it's working for you in some fashion.  I wish Samsung would spend less time on a "Unified" driver and more on a "simplified" driver.

---

### Post by reiki on 2007-07-17
I just got a Samsung CLP-300N and have it connected via network (it can connect either network or USB direct).

I downloaded the latest unified driver from Samsung's site :
20070424145947906_UnifiedLinuxDriver.tar.gz

I extracted it and the ONLY thing I did was change the permission so I could edit it and changed that first line to bin/bash instead of bin/sh

Then I did sudo ./install.sh and away we went. GUI came up and printer installed perfectly.

Maybe teh new unified driver is fixed?

---

### Post by tweedledee on 2007-07-18
All: as pointed out in other forums posts and on slashdot, this installer also changes permissions on some directoires that it should not.  This is not a huge deal, but should be changed back.

You will need to reset the following files and directories to be owned by root instead of by your user (sudo chown root:root ..., where ... is each of the paths below):
/usr/
/usr/lib
/usr/lib/cups
/usr/lib/cups/backend
/usr/lib/cups/filter
/usr/lib/cups/filter/pscms
/usr/lib/cups/filter/rastertosamsungpcl
/usr/lib/cups/filter/rastertosamsungspl
/usr/lib/cups/filter/rastertosamsungsplc
/usr/lib/sane
/usr/lib/sane/libsane-smfp.so.1.0.1
/usr/lib/libmfp.so.1.0.1
/usr/share/ppd/custom/CLP-550ps.ppd (you will have a different ppd file here for a different printer, use "ls -l /usr/shar/eppd/custom" to see the corret file (the one owned by you instead of root))
/etc/
/etc/sane.d
/etc/sane.d/smfp.conf


reiki: thanks for the update, I've noted it in the original post.

---

### Post by reiki on 2007-07-19
Confirming .:. I did have to reset those ownerships, even with this newest driver install.

---

### Post by Dragonslicer on 2007-07-21
I didn't see anyone else mention it, but the install script also sets OpenOffice to run as root, just like xsane. To undo the change to OpenOffice, run this command:

sudo chmod -s /usr/lib/openoffice/program/soffice.bin

---

### Post by tweedledee on 2007-07-23
> **Dragonslicer said:**
> I didn't see anyone else mention it, but the install script also sets OpenOffice to run as root, just like xsane. To undo the change to OpenOffice, run this command:

sudo chmod -s /usr/lib/openoffice/program/soffice.bin

I've not actually experienced this occuring, though I've seen other reports of it recently.  I'm not sure why some people seem to observe this, perhaps it's a "feature" of a newer version of the driver than I'm running.  I've added a note in the original post.

---

### Post by reiki on 2007-07-23
I just checked my machine regarding the openoffice thing and it is indeed +s.
I am checking to see if I have another ubuntu install where I haven't installed the samsung driver yet...

---

### Post by TheTinman on 2007-07-26
I just bought this printer today and have it working perfectly with Feisty without having to use the included software nor having to download anything.  Basically I installed the printer via System-->Administration-->Printing but chose Samsung ML-2010 as the model (that is AFTER the machine correctly detected that an ML-2510 was connected) and gdi as the driver.  

This was based on information I found via the Linux Foundation OpenPrinting initiative.  I posted my results on the ML-2510 page.

See [http://openprinting.org/show_printer.cgi?recnum=Samsung-ML-2510](http://openprinting.org/show_printer.cgi?recnum=Samsung-ML-2510).

---

### Post by tweedledee on 2007-07-28
Heavily revised guide, hopefully it will be a little easier to use now.  Also made notes relevant to the latest driver release, which is much easier to install than previous ones, and seems to have addressed essentially all complaints (except the security related ones).

Ooops, spoke too soon: NOW they have permission problems on the directories, which makes it impossible to directly delete the unpacked files.  Noted as step 10 in the main post.

---

### Post by reiki on 2007-07-28
I just installed the July 20 unified driver. On Ubuntu Feisty (32-bit)
My printer is a CLP-300N model and is connected to network only (not using the USB connection that is also on the printer).

Following this guide I changed permission on the install.sh file and then edited the first line changing /bin/sh to /bin/bash.

Then I used the ./autorun and install went as expected.

I do have some notes here related to teh network printer (as opposed to a directly connected printer)

At the printer select screen during driver install, no printers are detected since the local printer radio button is ticked. I choose the network printer radio button and then select Browse for Printers. Installer finds my CLP300N on the network and presents it for installation. 

After install completes I go to (in Gnome) System -> Administration -> Printing and the printer is already in there. I don't have to do anything further. The connection properties show it as being connected using IPP://-*IP_address_of_printer*- so IPP printing appears to be working fine here.

I have also made this printer available to my wife's laptop which is running WinXP. No issues. 

And since I have the printer set as a static IP I can easily log on to it using a web browser by using it's IP address. Lots of settings available in that interface as well.

My next quest is the SmartPanel application. It just plain didn't work and I see there is a new build for Linux. The previous build would ONLY work and show ink levels if you had the printer connected via USB. The Windows version of SmartPanel can see ink levels over the network. If the new SmartPanel build sees ink levels on a network-connected printer, then I will be one happy camper.

---

### Post by reiki on 2007-07-29
CLP-300N is working fine as a network printer. I can NOT get the SmartPanel application to work, however, as it asks me to install a supported driver or port. The Windows version of the driver/SmartPanel can see ink levels over the network, but the linux version seems unable to sort this out. I have installed the printer as IPP, LPD, TCP-HP JetDirect-Raw, and none of those options enables the SmartPanel aplication to work. 

While the printer does work quite nicely as a network printer and it does play nice with all of the computers on my network, I can only easily check ink levels from a Windows machine. I have instaled the driver successfully into a VirtualBox VM running WindowsXP and I can check the ink levels from there as SmartPanel works from the VM.

If Samsung would include ink level displays in there WebSync application from the printer, then this might be easier, however I am going to press my Samsung rep to pass on the information to Samsung regarding the general displeasure with their driver changing permissions and also getting this SmartPanel application to work with a network-connected printer in linux.

If anyone has gotten the SmartPanel application to work on a newtwork connected printer, I would be very interested in hearing about it.

---

### Post by bambou51 on 2007-07-30
I have another problem with this printer. Since the install everytime I start the printer cups-add open itself and I have to re-select the printer or cancel. Any idea on how to avoid this screen ?
But the bigger problem is that my usb external Hard drive mounted at startup crashed after I start my printer. I need to reboot my computer with the printer powered off in order to re-mount my hard drive !
When my hard drive crashed it doesn't appear anymore in /dev where previously ot was /dev/sda5 !
Any idea what the problem can be and how to solve it ?

I tried to use [http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian](http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian) tutorial but I was unable to apply the Fix for the MFP port issue section which seems to be my problem

I am using Feisty and Samsung 20070720 driver

---

### Post by wet_colored_arch on 2007-07-30
great work tweedledee but I am not there yet with my 2510.  Things work fine with a direct connection or as a network printer connected directly to my Mac.  The problem is that I can't get it to work when connected to my USRobotics with built in print server.

Couple of items:
I'm relatively new, and tried to follow the sudo commands, but not sure what I should see as feedback (should I see anything other than password request for sudo)... the only message I get back is with the last edit command:  
my terminal says
 sudo edit /etc/sane.d/dll.conf
Warning: unknown mime-type for "/etc/sane.d/dll.conf" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"

I think ownership was wrong, was at root, now with me when I send a job.  (My username under "owner" in print queue.)

With IPP (as to my working Mac connection) it sits there and says printing, with HP JetDirect it says "socket error" for status (seems to change the socket from 9100), and with LPD says "job hold until specified" in queue with  printer "offline" in properties information.

I did notice that the LPD doesn't preserve the router path as ipp://192.168.2.1:1631/printers/My_Printer ... it drops the 1631 from HOST and places printers/My_Printer as queue.  

One last observation.  When using the unified driver I can't manually enter anything.  If I add content to a path such as ipp://192.168.2.1:1631/printers/My_Printer  I don't receive a forward button.  I am forced to exit without entering anything and have been trying to create the printer from inside System>Admin>Printers as you suggest.

Any suggestions?

---

### Post by tweedledee on 2007-07-31
> **wet_colored_arch said:**
> I'm relatively new, and tried to follow the sudo commands, but not sure what I should see as feedback (should I see anything other than password request for sudo)... the only message I get back is with the last edit command:  
my terminal says
 sudo edit /etc/sane.d/dll.conf
Warning: unknown mime-type for "/etc/sane.d/dll.conf" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"

Replace "edit" with "gedit" or "mousepad" or whatever your favorite text editor is.  I'll clarify that in the main post.

> **wet_colored_arch said:**
> I think ownership was wrong, was at root, now with me when I send a job.  (My username under "owner" in print queue.)

This is normal - the print job will take on the user account from the program issuing the command.

> **wet_colored_arch said:**
> With IPP (as to my working Mac connection) it sits there and says printing, with HP JetDirect it says "socket error" for status (seems to change the socket from 9100), and with LPD says "job hold until specified" in queue with  printer "offline" in properties information.

I do not have personal experience, perhaps others can help.  All I can immediately suggest is to make sure (as much as you can) all user accounts are set correctly in the chain you have set up, so that you have rights to print with every device.

> **wet_colored_arch said:**
> I did notice that the LPD doesn't preserve the router path as ipp://192.168.2.1:1631/printers/My_Printer ... it drops the 1631 from HOST and places printers/My_Printer as queue.

LPD uses a different format from IPP; the two are not interchangeable, although they may both work with any given pair of devices if supported.

> **wet_colored_arch said:**
> One last observation.  When using the unified driver I can't manually enter anything.  If I add content to a path such as ipp://192.168.2.1:1631/printers/My_Printer  I don't receive a forward button.  I am forced to exit without entering anything and have been trying to create the printer from inside System>Admin>Printers as you suggest.

The driver has never worked for me to install the specific printer, so I just always use the Gnome interface, which should produce exactly the same end result.

---

### Post by wet_colored_arch on 2007-07-31
thanks for the clarification on the editing... but still no luck, tried CUPS too (instead of Gnome interface) and consistently getting "backend" failure with printer shown as "ready" and the message for the print job at "paused job hold until specified"

i thought the "paused job hold until" could be a cryptic message for wrong size paper, checked this and it was wrong but when I corrected the media size I had the same problem

i've worked on this off and on for 8 months or so,  but thought I should give it one more try...any other ideas are appreciated 

really ticks me off this can't be better, and have seen a few unresolved similar posting in different forums.... printing problems is THE main reasons I can't recommend linux to many more than I do - I kind of assume it is a problem with my router USR5461 but both the printer and router are supposed to be linux compatible

ss...

---

### Post by tweedledee on 2007-08-01
> **wet_colored_arch said:**
> i thought the "paused job hold until" could be a cryptic message for wrong size paper, checked this and it was wrong but when I corrected the media size I had the same problem.

No, this just seems to mean "can't communicate."  I get this trying to use IPP with my printer.

> **wet_colored_arch said:**
> really ticks me off this can't be better, and have seen a few unresolved similar posting in different forums.... printing problems is THE main reasons I can't recommend linux to many more than I do - I kind of assume it is a problem with my router USR5461 but both the printer and router are supposed to be linux compatible

Based on my quick survey of the USR site, I think you'll need to use the JetDirect/RAW connection when it is connected to your router, on port 9100(?).  And it sounds like both your devices meet the official criterea for Linux compatibility, the way most companies use: under at last 1 set of conditions, when used in isolation, the devices work.  I don't believe USR is supporting any of the *nix printing protocols (but someone with more experience can certainly correct me).  If in fact you are restricted to RAW, you should try some other test to see whether your printer can actually handle that input reliably; my CLP-550 is hit-or-miss with it (sometimes it prints, sometimes it doesn't, and it would never print a .pdf).  If you're restricted to one format for the router and a different one for the printer, the two simply won't work together.  When you say "as a network printer connected directly to your Mac," what do you mean?  Are you printing through the router on the Mac?  If so, then I think I'm out of ideas.

---

### Post by wet_colored_arch on 2007-08-01
what I meant by printing from MAC:

If I have it on router, I can print from MAC (but not from Ubuntu)
If I have the printer on the MAC, I can print from Ubuntu on the MAC by using the printer as a shared printer.

---

### Post by netimen on 2007-08-05
I have changed bin/sh to bin/bash but GUI installer still DOESN'T appear, and the guiinstaller.bin is not the last word

---

### Post by tweedledee on 2007-08-06
> **netimen said:**
> I have changed bin/sh to bin/bash but GUI installer still DOESN'T appear, and the guiinstaller.bin is not the last word

Which version of the driver, and do you get any error messages?

---

### Post by warpuck on 2007-08-07
I had to sudo as root.

then

./install.sh

The scanner & printer work fine,after I set the Samsung to slow USB.  

BUT now the neither the Epson R220 or Samsung will print correctly as default. Unless you count both spitting out blank paper at the same time until they decide to stop! U have 2 select one, then every thing works fine.

Fiesty on ASUS A8V AMD 64 (939) USB set to auto

---

### Post by wbsorsby on 2007-08-07
Thank you, thank you, thank you, Tweedledee.  I purchased a Samsung SCX-4725FN printer/scanner this weekend (on sale at Staples) specifically because it had built-in networking and was advertised as Linux ready.

I followed your entire instructions on my machine, but never had any problems so wasn't sure all the fuss about privileges was warranted.

Couldn't understand why I was having so much trouble with my daughter's machine installing first Crossover Office, then Microsoft Office.  That is, until I resorted to uninstalling Crossover Office when it told me that it wouldn't remove /opt/ directory because it wasn't empty.  Surprise - Samsung had installed in the /opt/ directory!  

My bad!  I hadn't bothered to fix the privileges in my daughter's machine.  Not doing so cost me a few hours of grief.

Everything's good now, though.  As soon as I fixed permissions as per your instructions, Crossover Office and Microsoft Office loaded and ran without further incident.

Funny, how much difference a little thing like permissions can make.

Again, thank you, thank you, thank you, Tweedledee. You reversed a disaster for me.  I think the Samsung SCX-4725FN is a great little printer for Linux now, but shudder to think how things would have gone had your instructions not been available to reverse the problems created by the Samsung unified driver.

---

### Post by tweedledee on 2007-08-08
> **warpuck said:**
> BUT now the neither the Epson R220 or Samsung will print correctly as default. Unless you count both spitting out blank paper at the same time until they decide to stop! U have 2 select one, then every thing works fine.

Fiesty on ASUS A8V AMD 64 (939) USB set to auto

I don't understand.  Do you mean you had both printers working, and one day they just stopped?  And do you mean they work as long as they aren't set to the default printer?  Which Samsung are you using?

---

### Post by reiki on 2007-08-15
tweedledee,

New samsung unified driver as of Aug 10, 2007. I'm at work, but when I get home I will install it and see if they've addressed the security problems. I have been communicating our concerns to high level support via my Samsung rep. This may be a chance to see if it's doing any good :)

OK the new driver still screws up permissions and ownerships. Had to fix them all again.

---

### Post by vyvee on 2007-08-16
Thank you so much!

I have a Fuji Xerox WorkCentre PE220, which should be a clone of Samsung SCX-4521F. Luckily the Samsung unified driver recognizes it. No special hack is required.

I found an easier way to set the ownership. ([http://www.vyvy.org/main/node/146](http://www.vyvy.org/main/node/146)) After untar & before running install.sh, I just do:
$ cd cdroot/
$ sudo chown -R root:root *

---

### Post by tweedledee on 2007-08-16
reiki, thanks for the tip.  It appears to be exactly the same driver, only with the lines that set +s on various programs commented out in the install.sh file.  I've made a note and updated my link.

vyvee, thanks for the tip, I'm sure many people will find that a useful shortcut.  I made a note in the original post.

---

### Post by adityavpratap on 2007-08-18
Hi I have been able to install the Unified Driver. However when I try to print a test page in the web fronted for  cups (localhost:631), the test page is not printed and the following message is displayed -
>  
/usr/lib/cups/filter/rastertosamsungsplc failed

I thought it must be a problem of ownership, so I did 
> 
$sudo chown -R root:root /usr/lib/cups/filter/

still, I am getting the same error message. 
Any suggestions?

---

### Post by tweedledee on 2007-08-19
> **adityavpratap said:**
> still, I am getting the same error message. 
Any suggestions?

What printer, and how is it connected to your computer?
I would suggest uninstalling and reinstalling the driver just to make sure everything worked correctly; once I know printer/connection, I may be able to offer more help.

---

### Post by Blown306 on 2007-08-30
My install went exactly the same way as below, except that I have a CLP-600N printer.  I was also getting file/path not found errors but those resolved when I moved /cdroot up in the tree.  Other than that, the install went as described.  I did need to change the permissions back to root on the various folders but OpenOffice did not seem to be affected as some have stated.

Many thanks for posting this thread....I am truly a NOOB when it comes to Linux.  Right now I'm evaluating Fiesty and getting my printer to work was one of the last roadblocks before I commit to ditching Winblows. Now to get VMware working and M$ is gone as my host.  Thanks again...you guys rock.

> **reiki said:**
> I just installed the July 20 unified driver. On Ubuntu Feisty (32-bit)
My printer is a CLP-300N model and is connected to network only (not using the USB connection that is also on the printer).

Following this guide I changed permission on the install.sh file and then edited the first line changing /bin/sh to /bin/bash.

Then I used the ./autorun and install went as expected.

I do have some notes here related to teh network printer (as opposed to a directly connected printer)

At the printer select screen during driver install, no printers are detected since the local printer radio button is ticked. I choose the network printer radio button and then select Browse for Printers. Installer finds my CLP300N on the network and presents it for installation. 

After install completes I go to (in Gnome) System -> Administration -> Printing and the printer is already in there. I don't have to do anything further. The connection properties show it as being connected using IPP://-*IP_address_of_printer*- so IPP printing appears to be working fine here.
<snip>
And since I have the printer set as a static IP I can easily log on to it using a web browser by using it's IP address. Lots of settings available in that interface as well.
<sinp>

---

### Post by reiki on 2007-09-05
Just wanted to post this in here for informational purposes. I am one of those for whom the Samsung unified driver is working. 

HOWEVER, I notice it prints plain text kinda blurry. And if I print plain text from the text editor, it comes out really large and the letters overlap horribly and it's generally unreadable. So it's not always formatting correctly.

There is an alternative.

I also installed the foo2qpdl driver
[http://foo2qpdl.rkkda.com/](http://foo2qpdl.rkkda.com/)

So I have my CLP-300N (connected network only... no USB connection) set up twice. Once as CLP-300N using the samsung unified driver (works fine for me as an IPP printer) and once as CLP-300N-foo using the foo2qpdl driver.

Why not pick one?  Because while the foo2qpdl driver does a MUCH nicer job on text, the samsung unified driver appears to do a much better job on complex color (photo or near-photo). Since most of my everyday printing is text or text with color highlights or simple color... the foo2qpdl is my default driver. When I need to print something with a bit more complex color in itr, then I use the samsung unified driver.

Different tools for different jobs.

---

### Post by sa-mejia on 2007-09-06
Using the drivers for ML-2010 and ML-2150 to install the ML 2510 did not work out for me... the test-pages were not printed properly: they were not printed in the center, and the magenta colour in them was not printing properly.

However, I managed to find a way around (I'm using Ubuntu Feisty).  

What I did was simply to do download the driver from samsung 
ML-2510/XAA (it seems that the driver that comes with the CD has some problems: [http://openprinting.org/show_printer.cgi?recnum=Samsung-ML-2510](http://openprinting.org/show_printer.cgi?recnum=Samsung-ML-2510)), and then simply to copy the following two files:

cdroot/Linux/i386/at_root/usr/lib/cups/filter/rastertosamsungspl 
(from the Samsung package (where cdroot is the root directory of the samsung ML-2510/XAA driver that I downloaded)) to /usr/lib/cups/filter/rastertosamsungspl.

And then cdroot/Linux/noarch/at_opt/share/ppd/ML-2510spl2.ppd (again from the Samsung package) to  /usr/share/cups/model/custom/ML-2510spl2.ppd 

I restarted the printer manager and I could find then my model in the list.  the test page now works perfectly, and the printer properties has many options that were not available when installing other printers instead.

I hope it might help other users.


> **TheTinman said:**
> I just bought this printer today and have it working perfectly with Feisty without having to use the included software nor having to download anything.  Basically I installed the printer via System-->Administration-->Printing but chose Samsung ML-2010 as the model (that is AFTER the machine correctly detected that an ML-2510 was connected) and gdi as the driver.  

This was based on information I found via the Linux Foundation OpenPrinting initiative.  I posted my results on the ML-2510 page.

See [http://openprinting.org/show_printer.cgi?recnum=Samsung-ML-2510](http://openprinting.org/show_printer.cgi?recnum=Samsung-ML-2510).

---

### Post by sa-mejia on 2007-09-06
a

---

### Post by st1ck3m_tux on 2007-09-15
I just thought that I would add my experiences with the Samsung ML2510.  I am running Gutsy on a Intel Dual Core proc with 2GB ram.  All that I did to install the printer was...   nothing!  After I connected the printer to power, and to the USB port on the computer, I turned the printer on.  A couple of seconds after I turned it on the print manager informed me that it had installed the printer, using a different driver.  I thought that this might be too good to be true, so I fired up OpenOffice, selected a document, selected the 2510 as the printer and presto it worked!  Gutsy has been excellent and stable on my hardware.  I am very impressed. As always the Ubuntu community has great information, and I thought that I would add to it.  :)

---

### Post by marf88 on 2007-09-18
I just did a fresh installation of Ubuntu Fiesty. I downloaded the drivers and extracted them to the folder. I didn't do anything beyond that. I try the command:

sudo ./cdroot/autorun 

and I Get this error

> 
me@mycomp-linux:~/My Downloads$ sudo cdroot/autorun
./i386/share/guiinstall.bin: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
****  It seems Qt library is not installed, or X display is not accessible.
****  Custom Qt library will be configured for use with this package.
export: 1376: Downloads/cdroot/Linux/i386/at_opt/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin: bad variable name


Do I have to boot in to recovery mode with root access and chown the directory cdroot or something?

Thanks for your help in advance.

---

### Post by david ly-gagnon on 2007-09-22
just bought the samsung ml-2510 and did copied the two files , and the printer worked perfectly ~~~ (on ubuntu feisty) 

just to let u guys know

---

### Post by tweedledee on 2007-09-23
> **marf88 said:**
> I just did a fresh installation of Ubuntu Fiesty. I downloaded the drivers and extracted them to the folder. I didn't do anything beyond that. I try the command:

sudo ./cdroot/autorun 

and I Get this error



Do I have to boot in to recovery mode with root access and chown the directory cdroot or something?

Thanks for your help in advance.

Make sure the package libqt3mt is installed on your computer.  I think it's a default package, but maybe not.  If it is, try a reinstall of the package, and make sure that /usr/lib is in your path (should be).

---

### Post by carltonb on 2007-09-28
Details Using Fiesty
Have a Samsung ML-6060 printer connected to a USB (at one time connected to pc by cable)

I tried the Unified driver approach would not print using a pcl setup but printed 50 plus pages of gigo data when using the ps set up. Using the unified driver it only recognized the printer as /dev/mfp4.

Tried the localhost route it displayed two possible printers ML-6060 (MFP USB Port #2) and Samsung ML-6060 (Samsung ML-6060 USB #3)

What is the difference?

Installed one then the other. Received errors about not having pstopcl. If selecting the pcl nothing if ps then it just prints garbage.

Any help would be greatly appreciated.

carltonb

---

### Post by roxy99 on 2007-10-10
First of all, if it wasn't for this thread we'd all be screwed.

I just ordered this printer and just wanted to know if anyone's had any success in getting ALL functionality working.  Printing, scanning and faxing.   This guide is starting to look more like a HOW-NOT-TO guide since there seems to be a lot of problems.  Doesn't Samsung provide the drivers for linux?  It should'nt be this difficult.  Its not brain surgery.  Are the drivers only half baked or what??

EDIT:  My beef is only with Samsung BTW and please don't mistake my tone as being directed towards the forum members and I want to thank Tweedleded for the excellent guide.

---

### Post by roxy99 on 2007-10-15
Success !  Fiesty Fawn with Samsung 4521F.

Here's how I did it:

1) Follow link to Samsung driver page[http://www.samsung.com/us/support/download/supportDownDetail.do?group=printersmultifunction&type=printersmultifunction&subtype=monochromelasermultifunctionprintersfaxes&model_nm=SCX-4521F&mType=DR&dType=D&vType=R&cttID=801111&prd_ia_cd=]("http://www.samsung.com/us/support/download/supportDownDetail.do?group=printersmultifunction&type=printersmultifunction&subtype=monochromelasermultifunctionprintersfaxes&model_nm=SCX-4521F&mType=DR&dType=D&vType=R&cttID=801111&prd_ia_cd=")

Notice that at the bottom of the driver download page is Ubuntu instructions.  Follow those instrutions. Funny how Samsung seems to be supporting Ubuntu now, even though you still need to jump thru hoops to get the scanner to work.  Printing is basically plug and play with the USB setup.  Scanning is the problem

To set up scanning:

2) Follow [http://www.elijahlofgren.com/ubuntu/#scx-4521f]("http://www.elijahlofgren.com/ubuntu/#scx-4521f").  Only follow steps 13-17 to get the Scanner to work.

3) Download hacked libmfp.so.1.0.1 driver for for versions 2.00.95 and 2.00.97 at this site:
[http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian]("http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian")

NB- This hack disables your lpt1 port which conlicts with the USB detection of the scanner.  Hopefully you won't need the parallel port for anything since it will no longer work.

You do not need to bother with adding yourself as a user to the lp group since you took care of that in step 2.
Reboot the system and scanning should work

---

### Post by reiki on 2007-10-22
Anyone get the control panel to work on a network installed Samsung printer? I have teh CLP-300N connected network only. I would LOVE to be able to see ink levels without having to run XP in a VM. 

WinXP can see ink levels on this printer when connected network only. I can't get it working on ubuntu. It would even be cool if they just had ink levels showing on the printer setup pages available with a browser, but not there either.

---

### Post by roxy99 on 2007-10-23
Ink levels?  Now you're asking for too much :)
Did you get it working otherwise?

---

### Post by vyvee on 2007-10-23
I've just upgraded my Ubuntu to 7.10 Gutsy Gibbon, and have [setup]("http://www.vyvy.org/main/node/146") my FujiXerox with the Samsung driver. The setup procedure is similar, but you need to do two more things to make it work:

(1) Before or after the installation, you need to disable the AppArmor CUPS protection to be able to access the printer. Do it with:
$ sudo aa-complain cupsd

(2) If the new automatic USB printer detection messes up the things... You may want to remove the package for USB printer detection with
$ sudo apt-get remove hal-cups-utils

Hope it helps!

---

### Post by reiki on 2007-10-24
> **roxy99 said:**
> Ink levels?  Now you're asking for too much :)
Did you get it working otherwise?

Get what working? The printer or the SmartPanel? :)
I can not get the SmartPanel to work at all on linux with a printer connected only to the network. I will not hook up via USB as last time I did that, the printer backfed power through the USB port and took out my motherboard. :)  So I'm a little leary. 

In a fresh Gutsy install, I did not need the unified driver. Gutsy found the printer on the network and used the foo2-qpdl driver. This works fine for me as the clp-300N is not an all-in-one. It's just a color laser. 

SmartPanel, however is not "smart" enough to deal with the network-connected printer in linux. Works fine in WinXP.

---

### Post by roxy99 on 2007-10-24
> **reiki said:**
> Get what working? The printer or the SmartPanel? :)
I can not get the SmartPanel to work at all on linux with a printer connected only to the network. I will not hook up via USB as last time I did that, the printer backfed power through the USB port and took out my motherboard. :)  So I'm a little leary. 

In a fresh Gutsy install, I did not need the unified driver. Gutsy found the printer on the network and used the foo2-qpdl driver. This works fine for me as the clp-300N is not an all-in-one. It's just a color laser. 

SmartPanel, however is not "smart" enough to deal with the network-connected printer in linux. Works fine in WinXP.

Thats interesting.  So with Gusty the detection was plug&play?  I wonder if its also plu&play cpnnecting the 4521 locally to usb.  I may have to upgrate to Gusty.  Did you just do a simple upgrade or did you wipe clean and reinstall the OS?

---

### Post by reiki on 2007-10-24
I did a clean install of Gutsy. The upgrade of Feisty didn't go smoothly for me although most everything works. It will still use the unified driver if you upgrade. On my system I generally install clean and as I get the fresh OS tweaked up the way I like it and get things installed, then I eventually format the old OS partition and use it for storage. As a new release gets closer, I clear the storage to an external, delete the partition and have room for the NEXT OS install.  

Probably sounds like a pain but it's really easy and linux makes it even easier to have parallel installs. In many cases I can just copy stuff from my old /home folder to the new one... like... copy the .Mozilla folder over and *poof!* all of my bookmarks and cookies and crap come over to the new install. Same with thunderbird and many other things.

---

### Post by tweedledee on 2007-10-24
Thanks to those posting updates on Gutsy, I will add them to the main page as new information comes in.  I won't be upgrading to Gutsy myself for a while (possibly a month or more), as I can't afford any hiccups in an upgrade right now and some of the known issues with Gutsy involve my hardware.

---

### Post by cooksterj4 on 2007-10-24
Thank You SO MUCH!!!!  

I am new to Linux and you made it very understandable.

I just got a SCX-4725 networked, first time no probs, You ROCK!!

Your effort and time means a great deal to me!

Joe

---

### Post by paulphillips on 2007-10-28
> **reiki said:**
> I just got a Samsung CLP-300N and have it connected via network (it can connect either network or USB direct).

I downloaded the latest unified driver from Samsung's site :
20070424145947906_UnifiedLinuxDriver.tar.gz

I extracted it and the ONLY thing I did was change the permission so I could edit it and changed that first line to bin/bash instead of bin/sh

Then I did sudo ./install.sh and away we went. GUI came up and printer installed perfectly.

Maybe teh new unified driver is fixed?

Yes driver fixed now.  No changes required - just run straight from download and works fine!  

I've got the CLP-300 (USB only), on Dapper.

I downloaded: 20070720163657500_UnifiedLinuxDriver.tar.gz

---

### Post by roxy99 on 2007-11-09
Funny.  I still had to do thos extra steps for the scanner to work.

---

### Post by seul on 2007-11-16
Thanks a lot tweedledee. I used your guide a couple of times now and it always worked with no trouble. Sometimes I encountered minor issues, but you always had the solution. Cheers!

---

### Post by metapaso on 2007-11-18
**Report on Gutsy and Samsung SCX-4200**

I had my SCX-4200 working perfectly under Feisty (both printing and scanning), thanks to the [binary patch]("http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian") supplied by Jacobo Tarrio and the 2.00.95 drivers 

When I upgraded to Gutsy, printing continued to work fine, but xsane could no longer find the scanner.

first, I tried the instructions from [http://ubuntuforums.org/showpost.php?p=3607254&postcount=73]("http://ubuntuforums.org/showpost.php?p=3607254&postcount=73") disabling the AppArmor with
```
$ sudo aa-complain cups
```
and then I uninstalled the USB printer detection by uninstalling the hal-cups-utils 
```
$ sudo apt-get remove hal-cups-utils

```

But neither strategy worked.

Then I completely uninstalled the existing 2.00.95 driver using the Samsung Uninstall GUI, and then rebooted before downloading and installing the most recent [Samsung Unified Driver]("http://www.samsung.com/ca/support/productsupport/download/FileView.aspx?cttfileid=828690&type=&typecode=300600&subtype=&subtypecode=300601&cmssubtypecode=&model=SCX-4200&filetype=DR&language="), listed as updated on 2007-11-15.  I made sure to follow the instructions from the beginning of this thread closely, including the chown command.

The driver configurator shows the following details:
Common 2.00.97
Printer 2.00.52
Scanner 2.00.61
Build 362

My printer was detected fine, and xsane also found it no problem.  Happily printing and scanning now!

---

### Post by LaneLester on 2007-11-30
I've installed my 2151N duplex printer with both the Gutsy-supplied drivers and the Samsung package. The second side of the sheet is always printed upside down, no matter what the settings.

I'm using the Foomatic hplj4d driver

What a nuisance! :(

Later: I found a solution: the 2150Postscript driver will print right-side-up second sides.

Lane

---

### Post by metapaso on 2007-12-08
Just wanted to alert Samsung printer users to a bug in Ghostscript under Gutsy and ask if anyone might have a solution:

[https://bugs.launchpad.net/gs-gpl/+bug/172264](https://bugs.launchpad.net/gs-gpl/+bug/172264)

The bug prevents printing of encrypted PDF files from acrobat reader and may affect other pdf printing/rendering engines that use ghostscript.

In the bug thread I'm listed as Lunomad, so you can follow the error logs of my SCX-4200 printer with the Unified driver.  If anyone out there can think of a workaround, I would greatly appreciate it.  There are a couple of sample pdf and ps files, inlcuding one I uploaded myself from the Canadian Immigration website.

Has anyone tried to configure an SCX-4200 to print using some other GPL'd drivers?  I would gladly give up my scanning functionality to be able to print these pdfs.  Thanks!

D

---

### Post by tweedledee on 2007-12-09
> **metapaso said:**
> Just wanted to alert Samsung printer users to a bug in Ghostscript under Gutsy and ask if anyone might have a solution:

[https://bugs.launchpad.net/gs-gpl/+bug/172264](https://bugs.launchpad.net/gs-gpl/+bug/172264)

The bug prevents printing of encrypted PDF files from acrobat reader and may affect other pdf printing/rendering engines that use ghostscript.

In the bug thread I'm listed as Lunomad, so you can follow the error logs of my SCX-4200 printer with the Unified driver.  If anyone out there can think of a workaround, I would greatly appreciate it.  There are a couple of sample pdf and ps files, inlcuding one I uploaded myself from the Canadian Immigration website.

Has anyone tried to configure an SCX-4200 to print using some other GPL'd drivers?  I would gladly give up my scanning functionality to be able to print these pdfs.  Thanks!

D

Thanks for the warning - I've still not upgraded to Gutsy, so haven't encountered this.  Once you recover your printing system completely (I just read the full bug report, but can't offer any assistance on that part), you should be able to set up the SCX-4200 as a standard postscript printer, then apply the Ghostscripts workarounds described in the bug thread to print the troublesome PDFs.  I believe you should be able to just add the SCX-4200 as a new printer with the PS driver and leave your existing one, so that you can print using the PS driver for problematic files and use the Samsung driver for everything else.

---

### Post by Tulip on 2008-01-04
Hello,
A quick thankyou for this howto, it worked without any trouble for me using a fresh install of Xubuntu and a network connected CLP-600N.

However, in the process I think I have somehow broken my desktop icons/desktop access. I had a single Firefox launcher on the desktop which has disappeared, but when I tried to recreate it I get a permission denied error.

Also, the Thunar File Manager shows the desktop icon in the left hand window with a cross over it. Attempting to open it generates a Failed to open directory "Desktop". Permission Denied error. 

Would this have anything to do with the 
> sudo chown -R root:root *
command?

Does anyone know how I can regain the correct desktop permissions I need to create desktop icons?

Cheers

---

### Post by tweedledee on 2008-01-05
> **Tulip said:**
> Hello,
A quick thankyou for this howto, it worked without any trouble for me using a fresh install of Xubuntu and a network connected CLP-600N.

However, in the process I think I have somehow broken my desktop icons/desktop access. I had a single Firefox launcher on the desktop which has disappeared, but when I tried to recreate it I get a permission denied error.

Also, the Thunar File Manager shows the desktop icon in the left hand window with a cross over it. Attempting to open it generates a Failed to open directory "Desktop". Permission Denied error. 

Would this have anything to do with the 

command?

Does anyone know how I can regain the correct desktop permissions I need to create desktop icons?

Cheers

I'm guessing you used the chown command on your entire home directory, not just the Samsung cdroot directory.  Execute "ls -l" in a terminal in your home folder; if files are owned by root, then just execute "sudo chown -R USER.USER *", where USER is your user name.  I've fixed the original guide to clarify where exactly you should execute that command.

---

### Post by mamat on 2008-01-06
hi,

i have a Samsung ML-1610 (simple one-sided usb laser printer with no scanner) which i once got working fine under ubuntu 6.06.

i have just upgraded to 7.10 and printing quit working. 

i tried reinstalling samsung's latest driver which didn't work as is. printing test sheet adds it to lpq and printer is "ready and printing" but then it goes back to just "ready" and the print job seems to have been indefinitely put aside.

if i use cups to change the uri from "mfp:/dev/mfp4" to "usb://Samsung/ML-1610", i have pages coming out of the printer. unfortunately the pages come out very slowly (pauses a few seconds in between every pages instead of spitting them out quite fast like it used to).

i REALLY do need to be able to print many pages faster than it is doing at the moment.

does someone have the same problem? any clue as to what i could try? is it due to using "usb" instead of "mfp" uri? is it due to newer cups or newer driver? 


PS: i've also tried foomatic. the quality of the printout is however much better with samsung's driver. (dithering of grays doesn't work great with foomatic)

---

### Post by Tulip on 2008-01-06
> **tweedledee said:**
> I'm guessing you used the chown command on your entire home directory, not just the Samsung cdroot directory.  Execute "ls -l" in a terminal in your home folder; if files are owned by root, then just execute "sudo chown -R USER.USER *", where USER is your user name.  I've fixed the original guide to clarify where exactly you should execute that command.

Absolutely correct, my desktop icons are now back and editable. Thanks very much for your help. 

Cheers

---

### Post by jamb on 2008-01-06
> **tweedledee said:**
> Mini-guide to installing Samsung printers & Unified Driver:
(Updated 17 December 2007)


  ML-2571n ([http://ubuntuforums.org/showpost.php?p=2313226&postcount=12](http://ubuntuforums.org/showpost.php?p=2313226&postcount=12))


I added an alternative howto post (and this is windows free) for the ML-2571N, this may be useful to link to?

[http://ubuntuforums.org/showthread.php?p=4086777#post4086777]("http://ubuntuforums.org/showthread.php?p=4086777#post4086777")

Big thanks for gathering all this information.

---

### Post by tweedledee on 2008-01-06
> **mamat said:**
> hi,

i have a Samsung ML-1610 (simple one-sided usb laser printer with no scanner) which i once got working fine under ubuntu 6.06.

i have just upgraded to 7.10 and printing quit working. 

i tried reinstalling samsung's latest driver which didn't work as is. printing test sheet adds it to lpq and printer is "ready and printing" but then it goes back to just "ready" and the print job seems to have been indefinitely put aside.

if i use cups to change the uri from "mfp:/dev/mfp4" to "usb://Samsung/ML-1610", i have pages coming out of the printer. unfortunately the pages come out very slowly (pauses a few seconds in between every pages instead of spitting them out quite fast like it used to).

i REALLY do need to be able to print many pages faster than it is doing at the moment.

does someone have the same problem? any clue as to what i could try? is it due to using "usb" instead of "mfp" uri? is it due to newer cups or newer driver? 


PS: i've also tried foomatic. the quality of the printout is however much better with samsung's driver. (dithering of grays doesn't work great with foomatic)

I'm also struggling a bit with my printer (CLP-550) with the newer drivers.  Some documents simply vanish and do not print.  I've found that if I configure the printer using a similar driver (e.g., for me the CLP-500), I can get difficult documents to print, albiet not quite as quickly as normal and with slightly off color.  You may have some luck if you play around in a similar fashion.  Right now I actually have two "printers" set up for my single physical printer; sometimes one works better, and sometimes the other.  Samsung isn't admitting to any significant changes to the drivers in nearly a year (just the installer scripts), so it's either an undocumented change or something to do with the newer files in Gutsy.

---

### Post by tweedledee on 2008-01-06
> **jamb said:**
> I added an alternative howto post (and this is windows free) for the ML-2571N, this may be useful to link to?

[http://ubuntuforums.org/showthread.php?p=4086777#post4086777]("http://ubuntuforums.org/showthread.php?p=4086777#post4086777")

Big thanks for gathering all this information.

Agreed, I added the link to the notes for that printer.

---

### Post by mamat on 2008-01-07
> **mamat said:**
> hi,

i have a Samsung ML-1610 (simple one-sided usb laser printer with no scanner) which i once got working fine under ubuntu 6.06.

i have just upgraded to 7.10 and printing quit working. 

i tried reinstalling samsung's latest driver which didn't work as is. printing test sheet adds it to lpq and printer is "ready and printing" but then it goes back to just "ready" and the print job seems to have been indefinitely put aside.

if i use cups to change the uri from "mfp:/dev/mfp4" to "usb://Samsung/ML-1610", i have pages coming out of the printer. unfortunately the pages come out very slowly (pauses a few seconds in between every pages instead of spitting them out quite fast like it used to).

i REALLY do need to be able to print many pages faster than it is doing at the moment.

does someone have the same problem? any clue as to what i could try? is it due to using "usb" instead of "mfp" uri? is it due to newer cups or newer driver? 


PS: i've also tried foomatic. the quality of the printout is however much better with samsung's driver. (dithering of grays doesn't work great with foomatic)

i just discovered in my /var/log/cups/error_log that the bug with samsung's default "mfp" driver gives a "crashed on signal 11!" error.

---

### Post by tweedledee on 2008-01-07
> **mamat said:**
> i just discovered in my /var/log/cups/error_log that the bug with samsung's default "mfp" driver gives a "crashed on signal 11!" error.

Based on what I can see regarding this error, you have two reasonable options: waiting until Samsung releases an updated driver, or trying a different printer model.  You might be able to trace down which parrticular library is causing the conflict, but even then you may not be able to address the problem.  Assuming you're willing to risk the loss of a little paper and toner, playing with related printer models to find one that works well is pretty easy.

EDIT: You may always want to try uninstalling the old driver completely, then reinstalling, just to see if something within Samsung's set of files is conflicting.  It's also possible, although unlikely, that the problem is apparmor; you can test this by using
```
sudo /etc/init.d/apparmor stop
```
to temporarily disable apparmor, then see if you can print.  If it does not help, then you should restart apparmor with
```
sudo /etc/init.d/apparmor start
```If it does help, permanently switch off apparmor for cups using
```
sudo aa-complain cups
```

---

### Post by pe3no on 2008-01-18
> **tweedledee said:**
> [...]
Printers with reported success:
[...]
Good luck, and let me know if you have success and/or failure, and I'll try to modify accordingly.

Hi, **tweedledee** and thank you for your Howto :)

I'm going to buy Samsung CLX-3160FN (color laser All-in-one).
Have you received a succes or non-success report for this model?

I was discussing this issue with another Ubuntu user and finally,
I have been directed to you :)

Thanks in advance and
BestRegards~~Piotrek~~pe3no.

---

### Post by tweedledee on 2008-01-19
> **pe3no said:**
> Hi, **tweedledee** and thank you for your Howto :)

I'm going to buy Samsung CLX-3160FN (color laser All-in-one).
Have you received a succes or non-success report for this model?

I was discussing this issue with another Ubuntu user and finally,
I have been directed to you :)

Thanks in advance and
BestRegards~~Piotrek~~pe3no.

I am not aware of any reports either way for this printer.  Looking at openprinting.org and the printer specs, I'm almost certain it should work fine as a printer, and it will probably work without hassle with the other functions, or at least no more hassle than for some of the other multifunction printers discussed in this thread.  You seem to have found the other threads in the forums that discuss it, but as they haven't posted in this thread I've not been following the progress at all.  You'll be taking a bit of a gamble with this printer (all Samsung printers, unfortunately) versus an HP, but if you're willing to risk spending some time getting it to work, you'll probably manage.

---

### Post by luke16 on 2008-01-20
I've run into some weird gui problem when trying to install the drivers. The gui window comes up, but will randomly lockup after hitting next. Occasionally it will launch a 2nd window, but that will be blank as well. I tried changing the /bin/sh to /bin/bash on the install.sh, but that does nothing. Any suggestions?

EDIT: Nevermind, I figured out how to force a text mode install via ctrl-alt-F1. My scx-4100 is working now. I have yet to try the scanner.

---

### Post by wkulecz on 2008-01-30
The "new"  Dec 2007 drivers worked perfectly for me following tweedledee's clear instructions at the top of this thread using  Ubuntu7.04 for our CLP-300 color laser printer.  

The GUI installer set everything up, automatically found the printer and printed a test page.  I then did a quick copy of a page using Xsane and all seemed well.

But I've two problems now.  First, Xsane seems to have stopped working, I get the "scanning devices" popup window, it goes away and then nothing.  Second and more important problem is printing pages it seems black text is blurry almost like its tryig to force bold print, color text is very sharp.  Basicaly the black text is not "laser quality" more like an inferiour inkjet, while color parts of a web page look fine.  A quick print of a color photo looked decent, and probably only needs a gamma adjustment to match what I get with our Dell color laser at work -- although nobody buys color lasers for their photo output.

Any settings I don't know about to address this? or did I get a defective printer?

Any idea as to why Xsane worked once and then stopped?  I did uninstall the Epson printer it had been using after the initial  test scan and exit of Xsane.

--wally.

---

### Post by M1GEO on 2008-02-06
Have just spent a little while trying to get the Samsung Installer Script to work with Ubuntu 7.10.  Turns out that they dont anticipate the install directory having spaces in the file name.  If you rename all folders in the path to single words (no space chars) it works fine for me.  Either that or modify the script. 

George

---

### Post by linuxfreakus on 2008-03-05
I just successfully setup my CLX-3160FN  the only thing which caused some trouble when I used the unified driver installer was that the GUI was not visible... it would draw the frame, but it was blank.

I turned off beryl and re-ran the installer, and it worked great... I'm not sure why but some programs do this with beryl.

---

### Post by demarshall on 2008-03-09
I have a problem with the Samsung Configurator as it sees my TV tuner card and not the scanner in my multifunction device - Samsung 4521F.

I followed the instructions given below but I still can't get the scanning part of the device to work. In fact when I tried to follow step 3, it broke my webcam.

Is there any hope of getting my Samsung 4521F to scan?

BTW I'm using Gutsy and didn't notice until now that these steps were for Fiesty.

> **roxy99 said:**
> Success !  Fiesty Fawn with Samsung 4521F.

Here's how I did it:

1) Follow link to Samsung driver page[http://www.samsung.com/us/support/download/supportDownDetail.do?group=printersmultifunction&type=printersmultifunction&subtype=monochromelasermultifunctionprintersfaxes&model_nm=SCX-4521F&mType=DR&dType=D&vType=R&cttID=801111&prd_ia_cd=]("http://www.samsung.com/us/support/download/supportDownDetail.do?group=printersmultifunction&type=printersmultifunction&subtype=monochromelasermultifunctionprintersfaxes&model_nm=SCX-4521F&mType=DR&dType=D&vType=R&cttID=801111&prd_ia_cd=")

Notice that at the bottom of the driver download page is Ubuntu instructions.  Follow those instrutions. Funny how Samsung seems to be supporting Ubuntu now, even though you still need to jump thru hoops to get the scanner to work.  Printing is basically plug and play with the USB setup.  Scanning is the problem

To set up scanning:

2) Follow [http://www.elijahlofgren.com/ubuntu/#scx-4521f]("http://www.elijahlofgren.com/ubuntu/#scx-4521f").  Only follow steps 13-17 to get the Scanner to work.

3) Download hacked libmfp.so.1.0.1 driver for for versions 2.00.95 and 2.00.97 at this site:
[http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian]("http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian")

NB- This hack disables your lpt1 port which conlicts with the USB detection of the scanner.  Hopefully you won't need the parallel port for anything since it will no longer work.

You do not need to bother with adding yourself as a user to the lp group since you took care of that in step 2.
Reboot the system and scanning should work

---

### Post by The Punisher on 2008-03-09
I have tried this procedure in 7.10 Gusty and 8.04 Hardy without success.
The scanner doesn't work.

---

### Post by tweedledee on 2008-03-10
As Samsung has not made a significant update to their driver in nearly a year, you may want to simply contact them ([http://www.samsung.com/us/info/contactus.html](http://www.samsung.com/us/info/contactus.html)).  I don't know if they will repsond or take action, but if multiple people are experiencing this, and the driver worked (even with hacks) in prior versions of Ubuntu, they may be willing to update the driver.

---

### Post by demarshall on 2008-03-14
Thanks tweedledee. I'll do that.

---

### Post by demarshall on 2008-03-14
I did contact Samsung just now but had to use the following URL because I'm in Canada.
[http://www.samsung.com/ca/info/contactus.html#](http://www.samsung.com/ca/info/contactus.html#)

---

### Post by demarshall on 2008-03-18
I thought that I'd let everyone know who may be following this thread that Samsung has decided that they do not support Linux. According to the Linux Counter there are only about 29 million Linux users in the world so that's a number of people to not provide service to.

Here is a message that I received in response to my asking them for assistance getting the scanner working in my SCX-4521F. 

>>  Sorry but we do not support Linux, please try your OS' forums.

I guess we're better off supporting HP in our future purchases of printers, scanners and perhaps even multifunction devices.

Does anybody know, in this age of multifunction devices, whether HP multifunction devices work with Linux and in particular Ubuntu?

---

### Post by tweedledee on 2008-03-18
> **demarshall said:**
> I thought that I'd let everyone know who may be following this thread that Samsung has decided that they do not support Linux. According to the Linux Counter there are only about 29 million Linux users in the world so that's a number of people to not provide service to.

Here is a message that I received in response to my asking them for assistance getting the scanner working in my SCX-4521F. 

>>  Sorry but we do not support Linux, please try your OS' forums.

I guess we're better off supporting HP in our future purchases of printers, scanners and perhaps even multifunction devices.

Does anybody know, in this age of multifunction devices, whether HP multifunction devices work with Linux and in particular Ubuntu?

Fascinating, although that perhaps explains why the two or three reports I've sent them have been entirely ignored.  HPLIP was specifically designed by HP to support Linux printing (and multifunction) and ships with Ubuntu by default, and although I've not tried a multifunction printer, the HP printers I have set up for various work machines have been a breeze compared to Samsung.  In all fairness to Samsung, some of the other printers I've worked with (e.g., Xerox/Tektronix) have required significantly more effort.

---

### Post by awilkins on 2008-04-02
Samsung are now listing a driver with a build date of 2008-03 (although the archive name is 200707...  )

It installed fine on my desktop (after editing the scripts to run from bash). The smart panel app works fine and even lists the toner levels, even if that's strictly unnecessary because you can get them from printers web server. I've not yet checked out the suid bit issues.

I had enormous trouble installing the driver on my laptop, but I think some unrelated problem was the cause ; the GUI installer got wedged, my printer config panel continually prompted me for sudo passwords, and nothing worked.

I reinstalled Gutsy in the end... whatever was wrong with my printer subsystem was stubborn.

I also installed the foo2qpdl drivers, which also work fine (for my model).
[http://foo2qpdl.rkkda.com/](http://foo2qpdl.rkkda.com/)

In addition, I got the networked scanning working. Start the perl script running as detailed, walk up to the printer, push "Scan to.." and follow the prompts to scan to the target.
[http://www.jon.demon.co.uk/dell1600n-net-scan/](http://www.jon.demon.co.uk/dell1600n-net-scan/)

---

### Post by tweedledee on 2008-04-05
> **awilkins said:**
> Samsung are now listing a driver with a build date of 2008-03 (although the archive name is 200707...  )

Odd.  I still the build dated November.  Even stranger is that is is not the same build I have previously downloaded, even though it has the same date, and it appears to actually be the July build based on file dates.  I'm not real sure what Samsung is doing at the moment.

---

### Post by reiki on 2008-04-12
> **awilkins said:**
> Samsung are now listing a driver with a build date of 2008-03 (although the archive name is 200707...  )

It installed fine on my desktop (after editing the scripts to run from bash). The smart panel app works fine and even lists the toner levels, even if that's strictly unnecessary because you can get them from printers web server. I've not yet checked out the suid bit issues

My CLP-300N does not show toner levels on it's web interface. I wish it did. I have it connected network-only and the smartpanel does not work unless I connect a USB cable.

---

### Post by tayroni on 2008-04-22
Samsung SCX-4200 scanner does not work on Ubuntu 8.04 Hardy Heron
Summary: I have installed the samsung unified driver in gutsy and on hardy. The scanner works on gutsy but NOT on HARDY.

Description: I've installed the driver first using the script provided by samsung, and manually. The manual installation was done because that the script allows /etc read and write by users (I really want to know the name of the programmer who did this mess!)

In both ways: installation by script or manually, the driver for the printer and scanner works on a clean install of gutsy. The same don't happen for hardy: the printer works but the scanner is not recognized by xsane.

Output of sane-find-scanner (both Gutsy and Hardy). Using sudo scanimage -L, the scanner is found on gutsy, but not on hardy.
__________________________________________________ __________________________________________________ __________________________________________________ _
found USB scanner (vendor=0x04e8 [Samsung], product=0x341b [SCX-4200 Series]) at libusb:002:003
__________________________________________________ __________________________________________________ __________________________________________________ _


On GUTSY (sudo xsane and sudo scanimage -L WORKS), the relevant lines of /var/log/syslog are
__________________________________________________ __________________________________________________ __________________________________________________ _
Apr 21 19:14:25 galileu rmmod: ERROR: Module ppdev does not exist in /proc/modules
Apr 21 19:14:25 galileu kernel: [ 1263.159257] pnp: Device 00:0b disabled.
Apr 21 19:14:25 galileu kernel: [ 1263.246583] pnp: Device 00:0b activated.
Apr 21 19:14:25 galileu kernel: [ 1263.246596] parport_pc 00:0b: reported by Plug and Play ACPI
Apr 21 19:14:25 galileu kernel: [ 1263.246662] parport0: PC-style at 0x378 (0x77, irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr 21 19:14:25 galileu kernel: [ 1263.352916] lp0: using parport0 (interrupt-driven).
Apr 21 19:14:25 galileu kernel: [ 1263.394944] pnp: Device 00:0b disabled.
Apr 21 19:14:25 galileu rmmod: ERROR: Module ppdev does not exist in /proc/modules
Apr 21 19:14:25 galileu kernel: [ 1263.450626] pnp: Device 00:0b activated.
Apr 21 19:14:25 galileu kernel: [ 1263.450638] parport_pc 00:0b: reported by Plug and Play ACPI
Apr 21 19:14:25 galileu kernel: [ 1263.450702] parport0: PC-style at 0x378 (0x77, irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr 21 19:14:25 galileu kernel: [ 1263.564420] lp0: using parport0 (interrupt-driven).
__________________________________________________ __________________________________________________ __________________________________________________ _


On HARDY (sudo xsane DOESN'T WORK and sudo scanimage -L don't find the scanner) the relevant lines of /var/log/syslog are
__________________________________________________ __________________________________________________ __________________________________________________ _
Apr 21 19:11:46 kepler kernel: [ 1166.177485] lp: driver loaded but no devices found
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.236853] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.253490] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.257871] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.275009] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632').
Apr 21 19:11:46 kepler rmmod: ERROR: Module ppdev does not exist in /proc/modules
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.282338] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.287454] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632').
Apr 21 19:11:46 kepler kernel: [ 1166.453319] lp: driver loaded but no devices found
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.511863] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.516347] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.562628] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.567925] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.589722] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.594256] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632').
Apr 21 19:17:01 kepler /USR/SBIN/CRON[7696]: (root) CMD ( cd / && run-parts --report /etc/cron.hourly)
__________________________________________________ __________________________________________________ __________________________________________________ _


So, please, help me to figure out what's happening with the samsung scx-4200 scanner on hardy. Any help is welcome.


PS: To install the driver manually (best way), only for reference:

1) Download 20070720152943906_UnifiedLinuxDriver.tar.gz from samsung, extract the files, go to new directory cdroot and type these commands
cp Linux/noarch/at_root/etc/sane.d/smfp.conf /etc/sane.d/
cp -r Linux/noarch/at_opt/share/ppd/* /usr/share/ppd/custom/
cp Linux/i386/at_root/usr/lib/libmfp.so.1.0.1 /usr/lib/
cp Linux/i386/at_root/usr/lib/sane/libsane-smfp.so.1.0.1 /usr/lib/sane/
cp Linux/i386/at_root/usr/lib/cups/backend/mfp /usr/lib/cups/backend/
cp Linux/i386/at_root/usr/lib/cups/filter/* /usr/lib/cups/filter/
cd /usr/lib
ln -s libmfp.so.1.0.1 libmfp.so.1
ln -s libmfp.so.1.0.1 libmfp.so
cd sane
ln -s libsane-smfp.so.1.0.1 libsane-smfp.so.1
ln -s libsane-smfp.so.1.0.1 libsane-smfp.so

2) Edit /etc/sane.d/dll.conf and add the line "smfp" to the end of file. Add yourself to the groups lp and scanner.

3) Reboot

---

### Post by tweedledee on 2008-04-22
> **tayroni said:**
> Samsung SCX-4200 scanner does not work on Ubuntu 8.04 Hardy Heron
Summary: I have installed the samsung unified driver in gutsy and on hardy. The scanner works on gutsy but NOT on HARDY.

Based on past problems, if you haven't already then you should disable AppArmor to see if the scanner works.  If not, then it's a bug. There are apparently major scanner regressions in Hardy due to changes in the entire sane system, so this likely isn't specific to your scanner or Samsung.  See [https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/205496](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/205496) as an example, though there are several additional bugs related to scanning in Hardy as well.  If you find a solution in one of those threads, please post here to help others; if not, then you are better off posting to a bug report to get the attention of developers.

---

### Post by tayroni on 2008-04-22
Thanks, tweedledee, for the quick answer.

Following your previous post. I disabled apparmor on hardy by using the command

sudo /etc/init.d/apparmor stop

and then, I plugued the scx4200. Neither xsane nor scanimage -L were able to detect the scanner. Printer works as well.

I will fill a new bug report on sane to tell the developers about the regression from Gutsy. If there are any news about the scanner, I will post here.

---

### Post by tayroni on 2008-04-23
I DID IT!!!!! The SAMSUNG SCX-4200 now works on HARDY HERON!!!!!!

The problem was the driver software by SAMSUNG looks for the usb device on

/proc/bus/usb/00*/00*

and 8.04 drops support to /proc/bus/usb/00*/00* and port all software to look only on /dev/bus/usb/00*/00*

To reenable support on /proc/bus/usb I edited 

/etc/init.d/mountdevsubfs.sh

and modify the lines

        #
        # Magic to make /proc/bus/usb work
        #
        #mkdir -p /dev/bus/usb/.usbfs
        #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
        #ln -s .usbfs/devices /dev/bus/usb/devices
        #mount --rbind /dev/bus/usb /proc/bus/usb

to
        
        #
        # Magic to make /proc/bus/usb work
        #
        mkdir -p /dev/bus/usb/.usbfs
        domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
        ln -s .usbfs/devices /dev/bus/usb/devices
        mount --rbind /dev/bus/usb /proc/bus/usb

and reboot.

ONE CAVEAT: Using patched /usr/lib/libmfp.so.1.0.1 from [http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian](http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian) allows me to use xsane with normal user.

---

### Post by tweedledee on 2008-04-24
> **tayroni said:**
> I DID IT!!!!! The SAMSUNG SCX-4200 now works on HARDY HERON!!!!!!

Thanks for sharing, I have updated the original post to refer to your solution.

---

### Post by luke16 on 2008-04-25
Where do you find the ppd file for the printer? I have an scx-4100, and while the install appears to work, I still need to find the ppd file for it.

EDIT: Nevermind. It was in /usr/share/cups/model/samsung/. I didn't expect it to be in a gzip file, so it wasn't showing up on my searches.

---

### Post by artkochermin on 2008-04-26
Hi

First, thanks for the guide. 

I have a question about the security of Samsung Unified Driver Utility. I usually scan using this utility. I go to:
-Application/Samsung Unified Driver/Samsung Unified Driver Configuration
-Select Scanner and click Properties
This provides me with scanning utility.

After I scan, an Image Manager comes up. Clicking on File/Open brings up a file browser. This file browser runs in superuser mode and I noticed that I can delete folders with root ownership. Now that's not very good considering that I was never even asked for the superuser password. So anyone using my computer or gaining remote access can mess up my system without even knowing the password...

Can anyone confirm this? Did I do something wrong with my installation. What can be done about it.

Thanks.

---

### Post by ajtomasik on 2008-04-26
> **dav3c said:**
> :lolflag:  I did it!!!!!!!
Finally is just like every time.... Just read....
I read the Unified Driver Help
 >Troubleshooting>If printer doesn't print> 

9. I can't print on IPP printer.
If your printer or MFP is one of the following models: 
Mono Laser Printers
ML-1450, ML-1510, ML-1520, ML-1610, ML-1710, ML-1740, ML-1750, ML-2010, ML-2150, ML-2150, ML-2250, ML-2550S, ML-2550, ML-2560, ML-3560, ML-6060, ML-7300 
Color Laser Printers
CLP-500, CLP-510, CLP-550, CLP-600, CLP-650 
Laser MFP
SCX-4100, SCX-4200, SCX-4x16, SCX-4x20, SCX-4x21, SCX-6x20, MFP-560, MFP-750 
you cannot use IPP protocol for network printing because of a known incompatibilty of the models with IPP implementation in CUPS. Please, use socket or LPD ports instead to connect to these models. 

I just change the socket from IPP to LPD (without "http://") and it prints!!!!

Thank you anyway for your help.
Regards

what is IPP and LPD? i am new to linux

---

### Post by Neovos on 2008-04-26
to tayroni:
Thank you, that got my scanner detected and working for the first time ever! (tried it in fiesty, then gutsy, and now successful with hardy).And the Jaccobo Tario fix for xsane worked like a charm.

edit:..until I restarted. The scanner stayed detected but the Jaccobo Tario fix didn't stay for some reason. I also noticed that even right after I did it and before I just restarted, sometimes xsane would load ok and other times it would look to the wrong device (v4l..my webcam) and fail to startup. Then I would just repeat the last steps of the Tario fix and it would work again. Really weird.

to artkochermin:
Same thing happens to me. The whole configurator and any thing it launches, (that image manager and file browser) all end up in root. Any saved scans also are root owned as well. Root access is needed for it all to work but I definitely agree that its not a good idea to go about business like that.

---

### Post by tweedledee on 2008-04-27
> **artkochermin said:**
> I have a question about the security of Samsung Unified Driver Utility. I usually scan using this utility.

The program is set to run as root using setuid (i.e., the +s permission is set); this is the same problem that Samsung was causing with Openoffice and xsane by default until a few months ago.  I'm not sure what the program is doing that may require such access (I don't have a scanning printer), but you can try:
```
sudo chmod -s /opt/Samsung/mfp/bin/Configurator
``` and adding "gksu" (for Ubuntu, I forget the Kubuntu equivalent at the moment) in front of the command on the menu (right-click on menu, navigate to it, insert gksu[space] before the command).  That will prompt for your password and still run the application as root, which should (but may not be) functionally equivalent.  You can also try just removing the setuid permission and not running as root to see what happens.  If it does work without root permissions, please report back and I'll update the original post to suggest changing those permissions.

---

### Post by tweedledee on 2008-04-27
> **ajtomasik said:**
> what is IPP and LPD? i am new to linux

Protocols for sending data to the printer that involve a great many details I'm not that familiar with myself.  In practice, all you really need to know is that when you set up the printer, you can choose several different protocols to talk to the printer, each of which uses a slightly different method and requires slightly different information, and that most printers only work with some subset of the avialable ones.  This is more-or-less equivalent to selecting a "port" when configuring a printer in Windows, which combines the the process of selecting a physical port (e.g., USB or network) with the protocol (e.g., Samsung has their own Windows network protocol instead of using TCP/IP).

---

### Post by ajtomasik on 2008-04-27
Also my computer will see the printer through the USB drive witch is good but when it prints it comes out with this error message...

INTERNAL ERROR-pub

i have the driver on the disk should i reinstall or do something else?

as i said i am new to Linux:confused:

---

### Post by artkochermin on 2008-04-27
> **tweedledee said:**
> The program is set to run as root using setuid (i.e., the +s permission is set); this is the same problem that Samsung was causing with Openoffice and xsane by default until a few months ago.  I'm not sure what the program is doing that may require such access (I don't have a scanning printer), but you can try:
```
sudo chmod -s /opt/Samsung/mfp/bin/Configurator
``` and adding "gksu" (for Ubuntu, I forget the Kubuntu equivalent at the moment) in front of the command on the menu (right-click on menu, navigate to it, insert gksu[space] before the command).  That will prompt for your password and still run the application as root, which should (but may not be) functionally equivalent.  You can also try just removing the setuid permission and not running as root to see what happens.  If it does work without root permissions, please report back and I'll update the original post to suggest changing those permissions.

Thanks for the solution. I ran ```
sudo chmod -s /opt/Samsung/mfp/bin/Configurator
``` If I open the Configurator it gives out segmentation fault when I try to access scanner properties. However it works fine with gksu(and sudo as well) in front of the command. I changed it in the menu and now I am asked for the password, which is much better than it was before.

---

### Post by tweedledee on 2008-04-28
> **ajtomasik said:**
> Also my computer will see the printer through the USB drive witch is good but when it prints it comes out with this error message...

INTERNAL ERROR-pub

i have the driver on the disk should i reinstall or do something else?

as i said i am new to Linux:confused:

Which printer & protocol are you using?  My guess is that you need to try a different protocol (e.g., try RAW if you have already tried LPD), or, if your model has multiple drivers (ppd files) available, try a different one from the same list.  Some printers appear to work better with drivers from closely related models rather than an exact match.

---

### Post by tayroni on 2008-04-28
@Neovos:

You can do a ls -alh /usr/lib/libmfp.so* and post here the result?

I know it's a silly thing, but ldconfig points links to last version of any library

If libmfp.so points to the original libmfp.so.1.0.1 renamed by you instead of patched version from Jacobo Tarrio, you have to repoint links to right version and move the original version of libmfp.so.1.0.1 to *another directory* (for example, your home directory) and leave in /usr/lib only the patched version.

Post here if works. If not work, you can undo moving back the original libmfp.so.1.0.1 renamed by you to /usr/lib.

---

### Post by Neovos on 2008-04-28
> **tayroni said:**
> @Neovos:

You can do a ls -alh /usr/lib/libmfp.so* and post here the result?

I know it's a silly thing, but ldconfig points links to last version of any library

If libmfp.so points to the original libmfp.so.1.0.1 renamed by you instead of patched version from Jacobo Tarrio, you have to repoint links to right version and move the original version of libmfp.so.1.0.1 to *another directory* (for example, your home directory) and leave in /usr/lib only the patched version.

Post here if works. If not work, you can undo moving back the original libmfp.so.1.0.1 renamed by you to /usr/lib.

Before (just as you said):

```
brian@Apollo:/usr/lib$ ls -alh /usr/lib/libmfp.so*
lrwxrwxrwx 1 root root  22 2008-04-26 23:17 /usr/lib/libmfp.so -> libmfp.so.1.0.1.backup
lrwxrwxrwx 1 root root  15 2008-04-12 14:27 /usr/lib/libmfp.so.1 -> libmfp.so.1.0.1
-rwxr-xr-x 1 root root 52K 2008-04-26 23:47 /usr/lib/libmfp.so.1.0.1
-rwxr-xr-x 1 root root 52K 2008-04-26 22:03 /usr/lib/libmfp.so.1.0.1.backup
```

After (I think when trying to repoint libmfp.so I deleted it how do I get it back? It showed up as a "broken link" after I moved the .backup file so I figured it was a symlink and safe to delete, but now I don't what to link to create a new one):

```
brian@Apollo:/usr/lib$ ls -alh /usr/lib/libmfp.so*
lrwxrwxrwx 1 root root  15 2008-04-12 14:27 /usr/lib/libmfp.so.1 -> libmfp.so.1.0.1
-rwxr-xr-x 1 root root 52K 2008-04-26 23:47 /usr/lib/libmfp.so.1.0.1

```

---

### Post by Neovos on 2008-04-29
Nevermind I got it. It works now. Good ol trash bin in "sudo nautilus."

that got libmfp.so back but it still pointed to my .backup file. 

Then as per Jacobo's directions, I reinstalled all the xsane stuff and that got it to repoint it correctly.

```
brian@Apollo:/usr/lib$  ls -alh /usr/lib/libmfp.so*
lrwxrwxrwx 1 root root  15 2008-04-28 23:55 /usr/lib/libmfp.so -> libmfp.so.1.0.1
lrwxrwxrwx 1 root root  15 2008-04-12 14:27 /usr/lib/libmfp.so.1 -> libmfp.so.1.0.1
-rwxr-xr-x 1 root root 52K 2008-04-28 23:46 /usr/lib/libmfp.so.1.0.1

```

and now xsane works and so far, has stuck. Thanks tayroni.

```
brian@Apollo:/usr/lib$ scanimage -L
device `smfp:SAMSUNG SCX-4100 Series on USB:0' is a SAMSUNG SCX-4100 Series on USB:0 Flatbed Scanner
device `v4l:/dev/video0' is a Noname USB2.0 1.3M UVC WebCam virtual device
brian@Apollo:/usr/lib$ xsane
brian@Apollo:/usr/lib$ 
```

---

### Post by tayroni on 2008-04-29
> **Neovos said:**
> Before (just as you said):

```
brian@Apollo:/usr/lib$ ls -alh /usr/lib/libmfp.so*
lrwxrwxrwx 1 root root  22 2008-04-26 23:17 /usr/lib/libmfp.so -> libmfp.so.1.0.1.backup
lrwxrwxrwx 1 root root  15 2008-04-12 14:27 /usr/lib/libmfp.so.1 -> libmfp.so.1.0.1
-rwxr-xr-x 1 root root 52K 2008-04-26 23:47 /usr/lib/libmfp.so.1.0.1
-rwxr-xr-x 1 root root 52K 2008-04-26 22:03 /usr/lib/libmfp.so.1.0.1.backup
```

After (I think when trying to repoint libmfp.so I deleted it how do I get it back? It showed up as a "broken link" after I moved the .backup file so I figured it was a symlink and safe to delete, but now I don't what to link to create a new one):

```
brian@Apollo:/usr/lib$ ls -alh /usr/lib/libmfp.so*
lrwxrwxrwx 1 root root  15 2008-04-12 14:27 /usr/lib/libmfp.so.1 -> libmfp.so.1.0.1
-rwxr-xr-x 1 root root 52K 2008-04-26 23:47 /usr/lib/libmfp.so.1.0.1

```

on console

cd /usr/lib
sudo ln -sf libmfp.so.1.0.1 libmfp.so.1

---

### Post by iains on 2008-05-05
I have just bought a new CLP-600N (unwisely maybe - to replace CLP-550N which was getting too expensive to maintain) to run on a home network. It seems to work fine with XP and standard drivers. On my Ubuntu PC I installed the standard driver (foo2qpdl). I had trouble with multipage colour documents - after 2-3 pages the text changes from black to pale blue, red, yellow with some lines across the page. It goes OK for some pages and then repeats the colour corruption. 

After reading this thread I downloaded the Samsung Unified Printer Driver and installed as per instructed with no difficulty. The driver seem to be the same and I am getting the same corruption printing from Open Office ofr Firefox. If I set the printer to print in monochrome everything seems OK. nb. The same document prints perfectly using Open Office 2.4 on XP. 

I am running on 8.04 (just upgraded), printer is on 192.168.10.101.
Is this a known problem or could it be hardware ?

(After a further experiment with a 26 page colour test document it seem that with Linux the blue component is not always being printed.)

---

### Post by tweedledee on 2008-05-06
> **iains said:**
> I have just bought a new CLP-600N (unwisely maybe - to replace CLP-550N which was getting too expensive to maintain) to run on a home network. It seems to work fine with XP and standard drivers. On my Ubuntu PC I installed the standard driver (foo2qpdl). I had trouble with multipage colour documents - after 2-3 pages the text changes from black to pale blue, red, yellow with some lines across the page. It goes OK for some pages and then repeats the colour corruption. 

After reading this thread I downloaded the Samsung Unified Printer Driver and installed as per instructed with no difficulty. The driver seem to be the same and I am getting the same corruption printing from Open Office ofr Firefox. If I set the printer to print in monochrome everything seems OK. nb. The same document prints perfectly using Open Office 2.4 on XP. 

I am running on 8.04 (just upgraded), printer is on 192.168.10.101.
Is this a known problem or could it be hardware ?

(After a further experiment with a 26 page colour test document it seem that with Linux the blue component is not always being printed.)

I'm not sure how much hardware/software the 600 shares with the 550, but the 550 has been a problem on Ubuntu since Fiesty, and practically useless since Gutsy.  When it would print at all, it behaved as you've just described.  I found that with the 550, switching to a an SPL-C based driver (e.g., the 500) instead of the PS based 550 helped somewhat, but the colors were so-so and the printer was horribly slow.  As the 600 is already SPL-C, you might try a related (e.g., 650) PS driver to see if that helps, but it may just make it worse.

I've recently discovered that switching to Debian made the 550 work perfectly!  It turns out that CUPS and the Gnome (and possibly KDE) printing interfaces have been customized in Ubuntu; although they add benefits to the user interface (e.g., in Debian with default Gnome interface it is not possible to change the default printer name when installing), something apparently also causes a breakdown in communication with certain Samsung printers - specifically the CLP series.  Unfortunately, that means your only real choice with Ubuntu is to keep trying related drivers (and generic postscript) until you find one that works.  Or switch to another distro, which may be overkill for the printer alone (I did it because Hardy nearly fried - literally - one of my computers).

---

### Post by iains on 2008-05-06
Thanks for comments

> I'm not sure how much hardware/software the 600 shares with the 550, but the 550 has been a problem on Ubuntu since Fiesty, and practically useless since Gutsy. When it would print at all, it behaved as you've just described. 


>  As the 600 is already SPL-C, you might try a related (e.g., 650) PS driver to see if that helps, but it may just make it worse.


Ironically I had no problem with the 550N as I defined it as a Postscript printer and it worked fine

> ... something apparently also causes a breakdown in communication with certain Samsung printers - specifically the CLP series. Unfortunately, that means your only real choice with Ubuntu is to keep trying related drivers (and generic postscript) until you find one that works.


>  Or switch to another distro, which may be overkill 

Or try and return it - but Samsung Linux documentation (2years old) does not refer to Ubuntu (or Debian) so buyer beware!

---

### Post by thewarlock on 2008-05-09
The upgrade from 7.10 to 8.04 completely wiped out my samsung printer install on one box. Reinstalling the drivers worked, but again, not right away.

Samsung finds the printer on mfp4, installs everything, but it won't work.

Using the default Printer tool from System/Administration, it finds the printer on a usb port, finds the driver, and printing works just fine.

No scanner though.

went to cdroot and ran the autorun script.

Kudos to Samsung for writing a native drive,  /bonks for doing it so badly though.

---

### Post by nik1979 on 2008-05-19
Does anyone else have printing problems, the samsung scx 4200 prints the test page ok but prints documents off page with open office docs, or zoomed in (enlarged) to the upper right portion of the document in pdf.

---

### Post by tweedledee on 2008-05-30
I updated the original post to reflect the fact that the installer writes a modprobe.conf that can cause problems.  While it seems not to be an issue for Ubuntu systems through Fiesty, it may be in the future (possibly including Hardy, I didn't spend enough time with it to check), and it is definitely a problem for Debian and other Debian-based distros.  (It's step #13 for the curious.)

Also, I should point out that I am no longer running Ubuntu at all, although I am running Debian, and so far everything relevant for this thread has applied to both.  I will continue to maintain this as needed, but can't promise that my experiences will align with the Ubuntu experience going forward.

---

### Post by MarcoPau on 2008-06-24
Thank you tayroni! I could use scx 4200 on dapper, then after the upgrade to feisty untill today with hardy I have never been able to have it back up. Just because of those few commented lines. Thanks again! You made my day :-)

---

### Post by okkadiroglu on 2008-06-27
Hi,

Many thanks for the information. I was struggling with it for sometime and asked Samsung and its distributor in Turkey for help but I got nothing. Thanks a million times. Now I have one less problem to think before I leave for the seaside. 

best Regards

---

### Post by jackbox on 2008-07-04
I did the Jacobo Tarrio fix as mentioned above. When I run the configurator for the SCX-4200 there is no dev/usb/lp0. The only ports are the MFP ports. When I copy over the modified libmfp.so.1.0.1 file and run XSANE it says no devices can be found. With the original file XSANE will only run as SUDO. When run as normal user it craps out. Is there another way to change the port used since my version of the configurator does not have this option? Or is there another modified version of the file that uses the standard MFP ports? I would really like to run XSANE in normal user mode instead of SUDO. Any help would be appreciated.

---

### Post by gizmobay on 2008-07-07
Does anyone have the SmartPanel working? I'm using a Samsung CLP-300. When I first installed Ubuntu, before I installed the Unified drivers, I installed SmartPanel and once the install was complete the SmartPanel Gui came up. I then uninstalled it and then installed the Unified Driver. I then re-installed the SmartPanel but now it doesn't work. When I try to start the snmpdemon, I get a seg fault.

---

### Post by RamonBianco on 2008-07-09
> **komasoftware said:**
> This worked for me (7.04 Feisty) :

* download driver from Samsung (Unified driver)
* Simply choose add printer in System-> Administration -> Printing
* For me the printer is detected, choose install driver, select the PPD file from the downloaded archive
...

sudo cp ./cdroot/Linux/i386/at_root/usr/lib/cups/filter/rastertosamsungsplc /usr/lib/cups/filter/
...Hello, all, and I hope I can find some help here.

I'm trying to install a new Samsung CLP-315 (non-network version) on my Fiesty box.  My intent was to use a minimal possible install, because the printer will be networked, so I don't want the Smart Panel.  [SIZE="1"][COLOR="DimGray"](I have tried to get it going on a Belkin print server which worked fine with a Sammy ML-2510 and a Canon inkjet, but not when I replaced the Canon with the CLP-315.  So, for now, I'm sharing the printer from a different PC running another OS [COLOR="Silver"][whose name I dare not mention][/COLOR].)[/COLOR][/SIZE]

At any rate, I got the printer "working", but only in a double-half way.  It prints two duplicate, identical, narrow columns, each a half-size version of the page, separated by a series of white bands every 3 mm or so.  I'm attaching a pic below, for your information and amusement.

Does anyone have any ideas on how to fix this?

Thanks in advance for any assistance.

---

### Post by RamonBianco on 2008-07-13
Interestingly, when I do the same kind of install of the ML-2510

[INDENT](GUI-install the New Printer using the Samsung ML-2510 driver from the "CDROM", then
> [FONT="Courier New"]sudo cp -i /media/cdrom1/Linux/i386/at_root/usr/lib/cups/filter/rastertosamsungspl /usr/lib/cups/filter/[/FONT])[/INDENT]

the newly installed ML-2510 printer works fine.

I would appreciate any possible fixes for the CLP-315 half-double problem I'm having.

Thanks.

---

### Post by djgregor97 on 2008-07-15
Hi there!

I am new to ubuntu.
I have ubuntu server 8.04. I have access only to terminal, no gui.
I have SCX-4321 printer.

I tried to install it, but obviously there was no option to choose printer (text installation).

Installation went ok, except that it installed SCX-4100 printer! (it should install scx-4x21 driver)

How to change printer manually? (somehow with lpadmin?)

PS I was able to print using lp command from terminal (with wrong driver)!

Many thanks!

Greg

---

### Post by djgregor97 on 2008-07-15
sorry, repeated message... :(

---

### Post by MattScout on 2008-07-17
It's late; sleep is terribly appealing at the moment; please forgive me for any probably-forgotten information.

I bought a Samsung CLP-315 today.  Installation did not go well.  After installing the unified driver, the printer was not detected and automagically installed (I am willing to consider that the problem may be elsewhere with my system, though it's unlikely).

dmesg included the following lines:
> [ 2615.480486] usb 4-2: new high speed USB device using ehci_hcd and address 4
[ 2625.811849] usb 4-2: unable to read config index 0 descriptor/start: -110
[ 2625.811863] usb 4-2: chopping to 0 config(s)
[ 2645.802736] usb 4-2: no configuration chosen from 0 choices

So I tried:
> modprobe -r ehci_hcd

Suddenly the printer was detected (CLP-310 Series).  I'm not certain whether I had to do this, or whether I'm just tired and had something stuck in my head after working on this for too long, but I then changed the device connection and URI:  connection device MFP USB Port #0 (which had not shown up prior to removing ehci_hcd), URI mfp:/dev/mfp/4.

The sound of the printer feeding paper and spitting out a test page was magical.

(Further note:  after running modprobe ehci_hcd to reinstall ehci_hcd, MFP USB Port #0 did not show up as a connection device.  Interesting, and something I may add more information about if I figure anything useful out, such as whether printing works with ehci_hcd installed, or whether printing with the original connection/URI works.)

---

### Post by tweedledee on 2008-07-17
> **djgregor97 said:**
> How to change printer manually? (somehow with lpadmin?)

Yes - lpadmin is the correct tool.  Not having used it, I can't give you exact instructions, but "man lpadmin" seemed fairly clear - you probably just need to delete the automatically installed printer and install a new one (the ppd directory is /usr/share/ppd/samsung).

---

### Post by tweedledee on 2008-07-17
> **MattScout said:**
> It's late; sleep is terribly appealing at the moment; please forgive me for any probably-forgotten information.

All the USB interfaces in Linux 2.6.24 are a bit odd (ehci_hcd, ohci_hcd, and uhci_hcd, depending on what USB type you have; computers more modern than mine are probably using entirely ehci_hcd).  I'm not entirely surprised to see the effect you describe, but I can't offer a better solution.

---

### Post by RamonBianco on 2008-07-17
Does anyone have any suggestions on other places I could pose my question on the Samsung CLP-315 driver install with the half/double printing problem, from a few [COLOR="LightBlue"](6-7)[/COLOR] posts back?
[CENTER]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=77696&d=1216033690[/IMG]
[/CENTER]

I've already re-posted it in [thread=859054]*_The Ubuntu Forum Community > Main Support Categories  > Hardware & Laptops_*[/thread].

I would appreciate any other suggestions on where to seek help for this issue.

Thanks.

[COLOR="green"]**PS:  I hope my inclusion of that image is acceptable; I will watch for negative feedback, and edit this post if I get any.**[/COLOR]

---

### Post by tweedledee on 2008-07-18
> **RamonBianco said:**
> Does anyone have any suggestions on other places I could pose my question on the Samsung CLP-315 driver install with the half/double printing problem, from a few [COLOR="LightBlue"](6-7)[/COLOR] posts back?

Not other locations, but have you tried the modprobe trick posted above by MattScout?  Since you are also using USB, it may be a related problem.  If it's not plugged into a USB 2.0 port, it's possible it will be the ohci or uhci instead of ehci driver.  It's not necessarily a solution, but may get you started.

Although you are unlikely to get a response, you could also try the Samsung support.

---

### Post by RamonBianco on 2008-07-18
Thanks for the response, tweedledee.  I did try Samsung, and haven't gotten a response.

The printer was detected okay when it was connected via USB, but now it's on a network print server.

In both cases, it could print, but the pages had the above half/double problem.

---

### Post by tweedledee on 2008-07-18
> **RamonBianco said:**
> Thanks for the response, tweedledee.  I did try Samsung, and haven't gotten a response.

The printer was detected okay when it was connected via USB, but now it's on a network print server.

In both cases, it could print, but the pages had the above half/double problem.

I've had limited success one case with trying different drivers: the generic postscript driver may work (with limited functions), or drivers for similar Samsung printers may also work (e.g., 310).  You want to be a little careful playing with different drivers, as you could theoretically damage your printer, but probably you're fine, especially if you don't wander too far (e.g., don't try M series drivers).  You can also try different network protocols, although in this case that seems unlikely to matter.

If they produce different results, you may be able to narrow down the problem, or even find something that is good enough for your purposes.

One final extreme option is to try a different Linux flavor; I've actually had somewhat better success with Samsung with pure Debian than Ubuntu, but it's still not perfect.  Many distros have live CDs that you could try installing the printer with to see if something works.

---

### Post by RamonBianco on 2008-07-20
> **tweedledee said:**
> I've had limited success one case with trying different drivers: the generic postscript driver may work (with limited functions), or drivers for similar Samsung printers may also work (e.g., 310) . . . If they produce different results, you may be able to narrow down the problem . . .Thanks, but I tried a couple of different Samsung drivers, the CLP-500 one that I believe is from splix, and the CLP-300 one from the Samsung Unified.  Both resulted in a printed page saying "SPC-ERROR - Please use the proper driver". [COLOR="Silver"] [/COLOR] The PostScript driver didn't produce anything; the CLP-315 unfortunately does not "natively" support PostScript (otherwise, I presumably wouldn't have any problem).

---

### Post by smolakian on 2008-08-11
I wasted a lot of time trying to get my scx4200 to print.

It is on a print server. But, the real problem is that the Samsung slpr.bin seemingly requires X to even run. I'm running a server and so I only have a command line.

Is there any way to use the Samsung drivers without installing X?

---

### Post by tweedledee on 2008-08-11
> **smolakian said:**
> I wasted a lot of time trying to get my scx4200 to print.

It is on a print server. But, the real problem is that the Samsung slpr.bin seemingly requires X to even run. I'm running a server and so I only have a command line.

Is there any way to use the Samsung drivers without installing X?

Probably not; you might be able to trace the actual calls/libraries slpr.bin is trying to access and just providing those, but I wouldn't expect much to result from that.  You may be able to get away with just install the xserver core; I don't have a machine to test with a server-only setup, but perhaps X doesn't actually need to be running?  If not, perhaps someone with more experience in the server versions can contribute.

---

### Post by yahs on 2008-08-20
Happy new Ubuntu user.

I have been using Ubuntu for 1 month now and I’m impressed. Wireless network, digital camera, webcam, music, movies, video all installed and working perfectly. 

My first effort at setting up printing was a complete failure, but yesterday I had another go after reading your post. I have a  Samsung SCX-4100 and thanks to your help and to the links below
[http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian](http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian)
[http://www.vyvy.org/main/node/146](http://www.vyvy.org/main/node/146)
I now have printing and scanning (still got a problem with gscan2pdf I get an error message “Unknown message: Segmentation fault” - more reading needed!! So apart from having to use XP to create image files using Acronis Trueimage I'm almost done.
many thanks
sk

---

### Post by lipinski on 2008-09-03
I have a Samsung CLP-610ND connected via network connection.

I installed the Unified Linux Printer Driver successfully, and everything works great (well, alomost everything).

The problem that I'm having is trying to print Envelopes from within OpenOffice Writer.  So, I don't know if the problem is OO or The Printer/Driver/Config.

What is happening is that when printing an Envelope, it attempts to duplex the Envelope and the printer Jams every single time.  The envelope is inserted in the Manual Feed Tray face down (as pictured on the feeder).  When the envelope jams, and I remove it, there is nothing printed on the front of the Envelope.  So, it seems that it is attempting to incorrectly print the content on the back of the envelope.
Note: When printing on paper, duplexing from OO Writer works fine.

I tried the same test with Windows & Word, and noticed that when printing Envelopes, the Envelope does not Duplex and everything is fine.  With the Envelope inserted in the same tray, same orientation, etc.  The envelope simply feeds through, without duplexing, and my content is correctly printed on the front of the envelope.

So, it seems that OO Writer or the Printer Config is trying to print onto the back side of the Envelope - which is not correct.

Any ideas?

[Found Solution/Workaround]:
I copied my CLP-610ND Printer in System->Administration->Printing and made a duplicate with the name CLP-610ND-Envelope.  In the Printer configuration, I specified the Correct Tray, Paper Type of Envelope, and Paper Size of Size 10 Env.  Now, I use that printer when printing Envelopes from OO Writer.  To save this functionality, I just created an Envelope in Writer, and saved the Template.  Works great.  Would be better if I didn't need a whole separate Printer Device instance, but whatever works...  Hope this helps someone.

---

### Post by bluelamp999 on 2008-09-03
Thanks Tweedeldee!

Your howto worked perfectly for me for the Samsung ML-2240.

I downloaded the Unified Printer Driver for Linux from (the hard to find)... [http://www.samsung.com/my/support/download/supportDown.do?group=printersmultifunction&type=printersmultifunction&subtype=monolaserprinter&model_nm=ML-2240/XSS&language=&cate_type=all&dType=D&mType=DR&vType=R&prd_ia_cd=06010400&disp_nm=ML-2240](http://www.samsung.com/my/support/download/supportDown.do?group=printersmultifunction&type=printersmultifunction&subtype=monolaserprinter&model_nm=ML-2240/XSS&language=&cate_type=all&dType=D&mType=DR&vType=R&prd_ia_cd=06010400&disp_nm=ML-2240)

It's now working like a charm.

Thanks Again

---

### Post by RamonBianco on 2008-09-05
> **RamonBianco said:**
>  . . .I'm trying to install a new Samsung CLP-315 (non-network version) on my Fiesty box.
 . . . At any rate, I got the printer "working", but only in a double-half way.  It prints two duplicate, identical, narrow columns, each a half-size version of the page, separated by a series of white bands every 3 mm or so.A few days ago, I upgraded from Feisty to Hardy, which went pretty well, but this CLP-315 2*½ problem persisted.

So instead of just adding the printer in Printer Config with the PPD file and then [SIZE="2"]```
sudo cp ./cdroot/Linux/i386/at_root/usr/lib/cups/filter/rastertosamsungsplc /usr/lib/cups/filter/
```[/SIZE]I did the "full install" as in the head of this thread.  That worked okay.

Thanks, tweedledee.

---

### Post by yosarian on 2008-09-06
I just got a Samsung SCX-4300. After several tries I have the printer running but I can't run the scanner.

When I try to open the Samsung Unified Driver Configurator I have this message

> 
Details: Failed to execute child process "/opt/Samsung/mfp/bin/Configurator" (Permission denied) 

The scanner is not recognize by the XSane Image Scanner or by the Scanner Utility.

Can someone help me to fix this?

---

### Post by yahs on 2008-09-06
Re: Samsung SCX-4300 Scanner Help

Hi, I'm a new user so bear with me.
I have a Samsung scx-4100 and the drivers are pretty much the same.
I read the thread HOWTO Install Samsung Unified Printer Driver by tweedeldee and used the link [http://www.vyvy.org/main/node/146](http://www.vyvy.org/main/node/146). I had good results. I have printing and scanning. The instructions from vyvy worked pretty good but not perfect. I have my own adapted instructions but not sure about posting etc, but more than happy to help if I can.There is also an important point in the following link about fixing the MFP port.
[http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian](http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian)
I think some of the problem is to do with permissions and ownership.
Hope this is of some use

---

### Post by confuseous on 2008-09-16
Success!
I got my CLP300N work with Hardy and KDE - many thanks for these excellent advices, Tweedledee!
With the 20070720163657500_UnifiedLinuxDriver.tar.gz, dated 9-11-2008, step 1 to 5 and 10 did the job to me.
In the graphical installer I selected 'network', then automatical detection of clp300 and ip-address was positive. 
The printer was instantaneously working with KDE in ipp-mode.
Character-printouts are nice 'n tidy due to black aftermarket-toner ([www.wticolor.de](www.wticolor.de)) - same in widows.

Thanks again for the good job.

---

### Post by jack frost on 2008-09-19
I have that printer.. are you using it on ubuntu as network printer and is windows able to see it?  that is what I am trying to do.
 
> **bektom said:**
> Dear tweedledee,
 
Thanks a lot for the howto, it worked for my network printer,
 
Samsung SCX-4521F
 
Additional comments:
during the Unified Linux Driver Installer gui one should select "manual select", then click on lpd:// (in the Network field) and write the IP address of the printer after ldp:// 
For the driver one should select Samsung SCX-4x21 Series
 
Thanks again
 
bektom

---

### Post by Ferb on 2008-10-03
> **yosarian said:**
> I just got a Samsung SCX-4300. After several tries I have the printer running but I can't run the scanner.

When I try to open the Samsung Unified Driver Configurator I have this message

The scanner is not recognize by the XSane Image Scanner or by the Scanner Utility.

Can someone help me to fix this?

Did you try the Linux drivers for the [Samsung Website]("http://www.samsung.com/us/support/download/supportDownDetail.do?group=printersmultifunction&type=printersmultifunction&subtype=monochromelasermultifunctionprintersfaxes&model_nm=SCX-4300/XAA&language=&cate_type=all&mType=DR&dType=D&vType=R&cttID=1857655&prd_ia_cd=06010300&disp_nm=SCX-4300") for the SCX-4300?

---

### Post by yahs on 2008-10-03
I have a Samsung SCX-4100 and thanks to the links below
[http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian](http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian)
[http://www.vyvy.org/main/node/146](http://www.vyvy.org/main/node/146)
I now have printing and scanning.

After many tries I found the following had to be done.

sudo gedit /etc/init.d/mountdevsubfs.sh

Look for the comment "# Magic to make /proc/bus/usb work" and uncomment its following four lines for making /proc/bus/usb work. After that, restart the script:

\$ sudo /etc/init.d/mountdevsubfs.sh stop
\$ sudo /etc/init.d/mountdevsubfs.sh start


Use the patched /usr/lib/libmfp.so.1.0.1. Use the fix for the driver version 2.00.97. ([http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian](http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian))

2. Log in to the group lp to access the scanner. This is required by the driver. So add yourself to the group lp

Hope this helps

---

### Post by fcastillo on 2008-10-16
Hi guys, I have a SCX-4725FN connected over the network to many computers. I downloaded the driver from the samsung webpage, installed it and my multifunction is working fine when i send something to print, but I'd like to use the scanner of the network. All the how-to I've read don't mention if the guide is for local, network or both. I'd really need to use my scanner over the network and don't know how.
I'm using Ubuntu Hardy 8.04.1 with kernel 2.6.24-21
Please, any help would be appreciated... Thanks!!

---

### Post by mario.campos on 2008-10-19
Hi, I am another newbie having problems to make SCX-4200 scanner to work with Xsane. I have the printer connected locally and I am running Ubunty Hardy with the latest (20070720152943906_UnifiedLinuxDriver.tar.gz) version of Samsung Unified Driver.

The printer ant the scanning through Samsung Configurator are OK, but Xsane crashes and gscan2pdf accuses missing scanner. Follows the description of what I did to try fixing it:

a) cd ~/cdroot
   sudo chown -R root:root *

b) sudo ./autorun

After finishing the graphical installer, I got the printer working and the scanning through Samsung Configurator. But Xsane is crashing and gscan2pdf not identifying the scanner in the system.

c) sudo chmod +s /usr/bin/xsane

d) sudo gedit /etc/modprobe.conf
    Edited to look as:
        options parport_pc io=0x378 irq=7 dma=3
        include /etc/modprobe.d/
  
e) sudo gedit /etc/init.d/mountdevsubfs.sh.
   edited:
   #
   # Magic to make /proc/bus/usb work
   #
   mkdir -p /dev/bus/usb/.usbfs
   domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
   ln -s .usbfs/devices /dev/bus/usb/devices
   mount --rbind /dev/bus/usb /proc/bus/usb

   sudo scanimage -L returns:
   device `smfp:SAMSUNG SCX-4200 Series on USB:0' is a SAMSUNG SCX-4200 Series on USB:0 Flatbed Scanner
   But Xsane is still crashing and gscan2pdf not identifying the scanner in the system.

f) sudo /etc/init.d/mountdevsubfs.sh stop
   sudo /etc/init.d/mountdevsubfs.sh start
   Still no change.
 
   I tried to get the patch from Jaccobo Tario, but his site if out.

Any suggestion?

---

### Post by mario.campos on 2008-10-23
The things got even more wierd. Yesterday I found gscan2pdf and xsane able to detect the scanner when running them as root from the Terminal ("sudo gscan2pdf" or "sudo xsane"). But today, that is not working anymore and "sudo scanimage -L" also returns no devices were detected. I opened mountdevsubfs.sh. with gedit and found the file is in blank. I would thank if someone could help me to restore it.

---

### Post by debernardis on 2008-10-24
Each version change brings new problems with this Samsung thingie. Now, I am using Intrepid - persistent - on a usb stick (Hardy has problems in my hands, too many errors on the casper-rw partition) and this, of course, makes difficult to connect my Samsung SCX-4100 multifunction printer.
The first post of this thread allowed me to fix the printer partg, but I am stuck with the scanner which is not recognized.

Will somebody help me look in this issue, please? Thamks :)

---

### Post by rek075 on 2008-10-25
> **tayroni said:**
> Samsung SCX-4200 scanner does not work on Ubuntu 8.04 Hardy Heron
Summary: I have installed the samsung unified driver in gutsy and on hardy. The scanner works on gutsy but NOT on HARDY.

Description: I've installed the driver first using the script provided by samsung, and manually. The manual installation was done because that the script allows /etc read and write by users (I really want to know the name of the programmer who did this mess!)

In both ways: installation by script or manually, the driver for the printer and scanner works on a clean install of gutsy. The same don't happen for hardy: the printer works but the scanner is not recognized by xsane.

Output of sane-find-scanner (both Gutsy and Hardy). Using sudo scanimage -L, the scanner is found on gutsy, but not on hardy.
__________________________________________________ __________________________________________________ __________________________________________________ _
found USB scanner (vendor=0x04e8 [Samsung], product=0x341b [SCX-4200 Series]) at libusb:002:003
__________________________________________________ __________________________________________________ __________________________________________________ _


On GUTSY (sudo xsane and sudo scanimage -L WORKS), the relevant lines of /var/log/syslog are
__________________________________________________ __________________________________________________ __________________________________________________ _
Apr 21 19:14:25 galileu rmmod: ERROR: Module ppdev does not exist in /proc/modules
Apr 21 19:14:25 galileu kernel: [ 1263.159257] pnp: Device 00:0b disabled.
Apr 21 19:14:25 galileu kernel: [ 1263.246583] pnp: Device 00:0b activated.
Apr 21 19:14:25 galileu kernel: [ 1263.246596] parport_pc 00:0b: reported by Plug and Play ACPI
Apr 21 19:14:25 galileu kernel: [ 1263.246662] parport0: PC-style at 0x378 (0x77, irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr 21 19:14:25 galileu kernel: [ 1263.352916] lp0: using parport0 (interrupt-driven).
Apr 21 19:14:25 galileu kernel: [ 1263.394944] pnp: Device 00:0b disabled.
Apr 21 19:14:25 galileu rmmod: ERROR: Module ppdev does not exist in /proc/modules
Apr 21 19:14:25 galileu kernel: [ 1263.450626] pnp: Device 00:0b activated.
Apr 21 19:14:25 galileu kernel: [ 1263.450638] parport_pc 00:0b: reported by Plug and Play ACPI
Apr 21 19:14:25 galileu kernel: [ 1263.450702] parport0: PC-style at 0x378 (0x77, irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr 21 19:14:25 galileu kernel: [ 1263.564420] lp0: using parport0 (interrupt-driven).
__________________________________________________ __________________________________________________ __________________________________________________ _


On HARDY (sudo xsane DOESN'T WORK and sudo scanimage -L don't find the scanner) the relevant lines of /var/log/syslog are
__________________________________________________ __________________________________________________ __________________________________________________ _
Apr 21 19:11:46 kepler kernel: [ 1166.177485] lp: driver loaded but no devices found
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.236853] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.253490] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.257871] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.275009] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632').
Apr 21 19:11:46 kepler rmmod: ERROR: Module ppdev does not exist in /proc/modules
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.282338] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.287454] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632').
Apr 21 19:11:46 kepler kernel: [ 1166.453319] lp: driver loaded but no devices found
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.511863] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.516347] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.562628] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.567925] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.589722] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.594256] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632').
Apr 21 19:17:01 kepler /USR/SBIN/CRON[7696]: (root) CMD ( cd / && run-parts --report /etc/cron.hourly)
__________________________________________________ __________________________________________________ __________________________________________________ _


So, please, help me to figure out what's happening with the samsung scx-4200 scanner on hardy. Any help is welcome.


PS: To install the driver manually (best way), only for reference:

1) Download 20070720152943906_UnifiedLinuxDriver.tar.gz from samsung, extract the files, go to new directory cdroot and type these commands
cp Linux/noarch/at_root/etc/sane.d/smfp.conf /etc/sane.d/
cp -r Linux/noarch/at_opt/share/ppd/* /usr/share/ppd/custom/
cp Linux/i386/at_root/usr/lib/libmfp.so.1.0.1 /usr/lib/
cp Linux/i386/at_root/usr/lib/sane/libsane-smfp.so.1.0.1 /usr/lib/sane/
cp Linux/i386/at_root/usr/lib/cups/backend/mfp /usr/lib/cups/backend/
cp Linux/i386/at_root/usr/lib/cups/filter/* /usr/lib/cups/filter/
cd /usr/lib
ln -s libmfp.so.1.0.1 libmfp.so.1
ln -s libmfp.so.1.0.1 libmfp.so
cd sane
ln -s libsane-smfp.so.1.0.1 libsane-smfp.so.1
ln -s libsane-smfp.so.1.0.1 libsane-smfp.so

2) Edit /etc/sane.d/dll.conf and add the line "smfp" to the end of file. Add yourself to the groups lp and scanner.

3) Reboot

I followed the manual instructions here and it worked for me on Ubuntu Server 8.04.  However, I have an AMD64 machine so I replaced i386 with x86_64 and lib with lib64.

---

### Post by tayroni on 2008-11-01
> **debernardis said:**
> Each version change brings new problems with this Samsung thingie. Now, I am using Intrepid - persistent - on a usb stick (Hardy has problems in my hands, too many errors on the casper-rw partition) and this, of course, makes difficult to connect my Samsung SCX-4100 multifunction printer.
The first post of this thread allowed me to fix the printer partg, but I am stuck with the scanner which is not recognized.

Will somebody help me look in this issue, please? Thamks :)

I'M BACK!!!

And today I'm installed intrepid ibex and I had problems (again) with the Samsung SCX-4200. On intrepid there is the same usb-related problem on hardy: The driver software by SAMSUNG looks for the usb device on /proc/bus/usb/00*/00*, but all software is ported to look only on /dev/bus/usb/00*/00*.

But, the same manual for hardy cannot be followed by intrepid because 
/etc/init.d/mountdevsubfs.sh was updated.

To reenable support on /proc/bus/usb/00*/00*, add yourself to the groups lp, lpadmin and scanner:

sudo adduser your_login_here lp
sudo adduser your_login_here lpadmin
sudo adduser your_login_here scanner

and edit the file /etc/init.d/mountdevsubfs.sh. ADD THE LINES:

#
# Magic to KEEP /proc/bus/usb working
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

right below the line

domount devpts "" /dev/pts devpts -onoexec,nosuid,gid=$TTYGRP,mode=$TTYMODE

Finally, reboot.

HAPPY INTREPID TO YOU!!!

---

### Post by chewearn on 2008-11-04
I just bought a Samsung CLP-315.  I got Intrepid amd64.  I didn't really follow the steps in first post to get it working.  But I did follow one advice, which is to run the Samsung installer in root terminal.

Here is the steps I gone thru:

1. Upon plugging in the printer, Intrepid automatically detect it and want to search for a driver.  I thought I will try that first.  After a long while searching, it installed a CLP-315 printer.  Unfortunately, test print came out with one page containing error message:
```
SPL-C ERROR - Including Corrupted Header Data
POSITION : 0X0 (0)
SYSTEM : src/xl_image
LINE : 811
VERSION : SPL-C 5.35 11-20-2007
```Since that was not working, I delete the printer from Administration > Printer.

2. Next, I pop in the CD that came with the printer.  There was a "Linux" subdirectory containing a file "install.sh".  Well, that was simple enough. :)  Based on the advice from OP, I opened a root terminal.  Then:
```
cd /media/cdrom/Linux/
./install.sh
```Install went smoothly, but upon completion, test print resulted in the same error printout as above.

3. Heck, just trying things randomly, I reboot.  The original printer installed by the Samsung installer still did not work.  But somehow, Intrepid autodetect and autoinstall a new printer during boot; "Samsung CLP-300 series" in Administration > Printer.  Hurray! This new printer worked perfectly.

Hope that helped.  ):P

---

### Post by gluxoid on 2008-11-05
Yesterday I plugged in my new CLP-315, Ubuntu popped up a dialog that let me search for the CLP-315 driver. Both color and monochrome test-pages printed correctly. However after setting the default paper size to A4, I get that error page printed (post #169) and independently of that, with duplex turned on I get one correct and one blank page.

---

### Post by gluxoid on 2008-11-06
Been reasonably stupid, I appear to have bought a CLP-310, not 315.

The unified drivers on the CD ROM work perfectly. GJ Samsung for not forgetting us Linux guys ;)

---

### Post by Anfanglir on 2008-11-14
Hi
I tried to install driver for Samsung SCX-4200 on Ubuntu Intrepid. Downloaded the latest driver from Samsung's US site (file dated to 2008-11-13). Tried both the method described in this thread (first post) and the instructions given by Samsung on their site:
([Ubuntu OS Installation]
1. Download and extract the driver 
2. Open ''Root Terminal'' 
3. Execute installation program. 
$ sudo cdroot/autorun
4. After intall, PPD path is set again.
$ sudo ln -s /usr/share/cups/model/samsung /usr/share/ppd/custom/samsung
5. Execute Configurator, and Add your printer model name by Add Printer.)

However, the driver installer hangs at c. 95%. After a long wait I tried to force shut it, that results in a lost GUI! Reebot leaves me at a ubuntu command line, no graphic interface. I had to reformat and reinstall to get Ubuntu running again. Tried it again with a freshly downloaded driver from Samsung. Same thing, OS dies. Installed Hardy, tried it again - GUI lost. Arghh.

My setup is a Toshiba Libretto U100-s213, pentium mobile 1.2 ghz, 1 gb ram. This is the first serious problem I've encountered in Ubuntu.

any advice appreciated / Anfanglir

---

### Post by tayroni on 2008-11-14
@Anfanglir: I installed the driver manually:

PS: To install the driver manually (best way), only for reference:

1) Download 20070720152943906_UnifiedLinuxDriver.tar.gz from samsung, extract the files, go to new directory cdroot and type these commands
sudo cp Linux/noarch/at_root/etc/sane.d/smfp.conf /etc/sane.d/
sudo cp -r Linux/noarch/at_opt/share/ppd/* /usr/share/ppd/custom/
sudo cp Linux/i386/at_root/usr/lib/libmfp.so.1.0.1 /usr/lib/
sudo cp Linux/i386/at_root/usr/lib/sane/libsane-smfp.so.1.0.1 /usr/lib/sane/
sudo cp Linux/i386/at_root/usr/lib/cups/backend/mfp /usr/lib/cups/backend/
sudo cp Linux/i386/at_root/usr/lib/cups/filter/* /usr/lib/cups/filter/
cd /usr/lib
sudo ln -s libmfp.so.1.0.1 libmfp.so.1
sudo ln -s libmfp.so.1.0.1 libmfp.so
cd sane
sudo ln -s libsane-smfp.so.1.0.1 libsane-smfp.so.1
sudo ln -s libsane-smfp.so.1.0.1 libsane-smfp.so

2) Edit /etc/sane.d/dll.conf and add the line "smfp" to the end of file.

as described on my first post. After installing the driver, I did all I wrote on the post #168:

To reenable support on /proc/bus/usb/00*/00*, add yourself to the groups lp, lpadmin and scanner:

sudo adduser your_login_here lp
sudo adduser your_login_here lpadmin
sudo adduser your_login_here scanner

and edit the file /etc/init.d/mountdevsubfs.sh. ADD THE LINES:

#
# Magic to KEEP /proc/bus/usb working
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

right below the line

domount devpts "" /dev/pts devpts -onoexec,nosuid,gid=$TTYGRP,mode=$TTYMODE

Finally, reboot.

---

### Post by Anfanglir on 2008-11-14
Thanx Tayroni!
will try that, although the driver Samsung got on their site now is called 20081028145509765 rather than 20070720152943906. Still worth a try :p

/ Anfanglir

---

### Post by Anfanglir on 2008-11-14
Hi again, the good news is that the gui is intact this time, the bad news is that printer is still not working. I repeated your instructions several times tayroni, but the printer still dont work.

I also tried to choose the scx4200.ppd file manually in the printer configuration, but that gives me an error saying rastertosamsungspl is not installed, and that /usr/lib/cups/filter/rastertosamsungspl failed

EDIT: checking /usr/lib/cups/filter/rastertosamsungspl using a filebrowser the file is there alright, but I dont have ownership to access it. I've typed in the commands sudo chown -R root:root *, sudo chown root.root/usr/lib/cups/filter/rastertosamsungspl, etc mentioned in post 1, but to no effect. Perhaps i did it in twe wrong sequence.

:confused:

---

### Post by Anfanglir on 2008-11-14
me again. I used gksudo nautilus to edit the ownership rights of the samsungtoraster files, and now I can print. Dont know if it is wise to do that though? do I introduce a security vulnerability to my system?

EDIT: also, the scanner is not recognised by XSane. :\

---

### Post by rybaxs on 2008-12-04
cd ~/cdroot
sudo chown -R root:root *


HELP!!!!  
This is what happened

user@user-desktop:/$ cd~/cdroot
bash: cd~/cdroot: No such file or directory
user@user-desktop:/$ sudo chown -R root:root *

   WHAT THE !!!!!!!!!

When my system hangs up!, when I restarted the OS, i can't login,
is there any recovery for the sudo chown -R root:root *

HELP!..

---

### Post by tweedledee on 2008-12-04
> **rybaxs said:**
> When my system hangs up!, when I restarted the OS, i can't login,
is there any recovery for the sudo chown -R root:root *

Use a Live CD to boot (any Ubuntu variety).  When up, mount your hard disk (if it isn't already, which it probably will be), and move to your home folder. Then execute the same "chown" command, only using "1000" (no quotes) instead of "root" in both places; that should convert all ownership back to the first user on your system.  If you aren't the first user, you'll need to use 1001 or 1002 or ... depending on which user number you are.

And in the future, don't execute command #2 if command #1 gave an error.

---

### Post by SimonJohnes on 2008-12-05
Thanks for sharing this information tweedledee,i have found this very informative and useful guide.I                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      also found a tutorial regarding installing Samsung Unified Printer Driver.Hope it will be also helpful for the people,

Installing a Samsung printer
November 1, 2006 — Matt Gordon

Updated: 8/3/07

This is a guide that should hopefully ease you through the stress of getting a Samsung printer working in Linux.
I made this guide with Ubuntu 6.10 and a Samsung SCX-4100 but most versions, distributions and models should be fairly similar.
I will also be updating the guide in the future hopefully if I manage to work out scanning as well.

Getting the driver:
To start off with you need to head to [www.samsung.com](www.samsung.com) and get the latest version of the driver. Look for the linux driver that ends in .tar.gz (at the time of writing 20070129124018750_UnifiedLinuxDriver.tar.gz was the file to look for). Save this file to your desktop and once it has finished extract it by right clicking on the file and selecting “extract here”.

Installing the driver via supplied instructions:
From here we install the drivers which should be as simple as moving to the correct directory and running the script:

    cd Desktop/cdroot/Linux
    sudo ./install.ch

If everything runs fine and dandy and the printer installs and you can use a test page, then wow your a lucky one. If your like the rest of us then it will not be so pain free. However with the release of the new unified Linux printer drivers for linux, it is only a quick task to get things going.

Editing the needed files:
The first thing we have to do it edit the install script, however it is currently read only file. This can be done by moving opening up the directory via the GUI: ‘Right click on install.sh > properties > permissions’ then change owner access to ‘read and write’.
Now we have the permissions to edit the file. Which we can do by opening the file with gedit:

    sudo gedit install.sh
    we then change the top line from
    #! /bin/sh
    to
    #! /bin/bash

apparently this is just something that is different between some versions of Linux.
Installing drivers:
We now try to install the drivers again

    cd Desktop/cdroot/Linux
    sudo ./install.sh

It should now work and an installation screen should pop up. Move through the install and another window will pop up trying to get you to install the printer. Do this, but chances are there will be no driver for the printer. This just seems to be a minor problem, we will fix that up now. “Cancel” out of the add window and click “finish” on the original installation window.

Adding your printer:

Go into ’system > administration > printing’ and then click on “New printer”. It might show a few printers connected, select the one that is like ‘Samsung SCX-4100 series’. Click ‘Install Driver’ and get the right driver from ‘Desktop/cdroot/Linux/noarch/at_opt/share/ppd’. Now the printer will not show up properly yet. If you head to the desktop and open up the program the initial installer put there and click “Add a printer” and follow the prompts, the printer should appear in the linux printers box.

Confirming your printer is properly installed:

Right click on your printers new flashy icon and click “Properties”, choose “Print test page” and it should now reward you with a hot freshly printed test page.

---

### Post by Ampul on 2008-12-21
Hi, 
since 3 days I have a problem with my samsung CLP-310 printer.
It started after an update of cups via the update manager.
(I'm on 8.10 and no probs so far with the printers.)

After the update, printing didn't work anymore.
I also have a Brother HL-1430. Same problem.

I uninstalled both printers, reinstalled them via cups ([http://localhost:631/admin](http://localhost:631/admin))
Now, the Brother is working again. The Samsung aint.

I am able to print a testpage, that works. 
When trying to print a document, I get a message that there was a problem with 'processing the document'.

Downloaded latest Samsung drivers, (unified), used them again, nothing works. Tested printing pdf, odt, pages from firefox,... :(

---

### Post by manixdk on 2008-12-29
> **gluxoid said:**
> Yesterday I plugged in my new CLP-315, Ubuntu popped up a dialog that let me search for the CLP-315 driver. Both color and monochrome test-pages printed correctly. However after setting the default paper size to A4, I get that error page printed (post #169) and independently of that, with duplex turned on I get one correct and one blank page.

Go to [http://foo2qpdl.rkkda.com/](http://foo2qpdl.rkkda.com/) and follow the instructions. Works like a charm. There's a problem with the Ubuntu supplied driver with A4.

---

### Post by ianwoodward on 2009-01-19
Hello Tweedledee

Firstly, I am new to Ubuntu (8.10) so please be patient with me. I have SOME Unix (SVr4) experience, but that was years ago.

My printer: Samsung CLP315W connected wirelessly in infrastructure mode.

What I have tried so far: Installing the printer using System/Administration/Printing
This worked, in so far as the PC tries to print to it (test page or an open office document) but what comes out says:

SPL-C ERROR - Including Corrupted Header Data
POSITION : 0x0 (0)
LINE :  811
SYSTEM : src/xl_image
VERSION : SPL-C 5.35 11-20-2007

So, I guess I need the proper Samsung driver. I doawnloaded it and tried unpacking using both the Ubuntu Archive manager, or the command line:

 sudo tar xzf 20081006172749281_UnifiedLinuxDriver.tar-1.gz

Both methods result in the error message:

tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Any idea what I should try next?

Regards, Ian

---

### Post by tweedledee on 2009-01-20
> **ianwoodward said:**
> Both methods result in the error message:

tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Any idea what I should try next?

Try emailing Samsung (not that it will likely generate a response), or finding a slightly different release of the same driver via a different printer (you apparently need the v3.00.28 drivers, not the 2.00.97, as your printer does not have a PPD with the 2.00.97 release).  It appears that many of their archives are simply badly packaged right now, as I get the same or similar errors with a couple of quick tests on different files.  The issue is not on your end.

If anyone else reading this thread happens to know of a working archive containing the v3 drivers (or v2, for that matter), please post which printer model it is linked to.

---

### Post by uggy on 2009-01-23
Dear all,


I also had some printer problems...
I have a CLP 310n connected on the network.. With Ubuntu 8.10.

I first installed driver using script provided on the CD with the printer... (full install)
Install seems to be fine.. but when I tried to print I had exactly the same problem reported by RamonBianco 6 months ago into this thread (page 15).

To make this post more "readable" here is how the print looks (RamonBianco pict). This problem is known as "half/double way"

[[img]http://img403.imageshack.us/img403/715/badprintme3.th.png[/img]](http://img403.imageshack.us/img403/715/badprintme3.png)


So next I used the "20081006172749281_UnifiedLinuxDriver" driver package... installed it running the install script, and IT WORKS !

My conclusion:
- drivers provided on the CD with the printer are NOT working.
- drivers provided on Internet are working !

In both cases the installer script runs without error.
I did exactly the same things for both.. So I'm 99.9% sure this is not something related to MY computer.

---

### Post by uggy on 2009-01-23
Ohh regarding driver package cuurently available by samsung....
They are looking "weird"...

- If you try to open the .tar.gz with FileRoller.. You will failed..

- If you try to "open" the .tar.gz with "tar" command..(Probably what FilreRoller use) You will got the folowing error: (as reported by tweedledee and ianwoodward)

$ tar zxf 20081006172749281_UnifiedLinuxDriver.tar.gz 
gzip: stdin: decompression OK, trailing garbage ignored
tar: Child returned status 2
tar: Des erreurs ont provoqué l'arrêt du programme
$

- If you try to open the .tar.gz with "gzip" and "tar".. You will have no error:

$ gzip -dc 20081006172749281_UnifiedLinuxDriver.tar.gz | tar xf -
gzip: 20081006172749281_UnifiedLinuxDriver.tar.gz: decompression OK, trailing garbage ignored
$


I don't know why yet ;)

---

### Post by albertz on 2009-01-25
> **tayroni said:**
> 
PS: To install the driver manually (best way), only for reference:

1) Download 20070720152943906_UnifiedLinuxDriver.tar.gz from samsung, extract the files, go to new directory cdroot and type these commands
cp Linux/noarch/at_root/etc/sane.d/smfp.conf /etc/sane.d/
cp -r Linux/noarch/at_opt/share/ppd/* /usr/share/ppd/custom/
cp Linux/i386/at_root/usr/lib/libmfp.so.1.0.1 /usr/lib/
cp Linux/i386/at_root/usr/lib/sane/libsane-smfp.so.1.0.1 /usr/lib/sane/
cp Linux/i386/at_root/usr/lib/cups/backend/mfp /usr/lib/cups/backend/
cp Linux/i386/at_root/usr/lib/cups/filter/* /usr/lib/cups/filter/
cd /usr/lib
ln -s libmfp.so.1.0.1 libmfp.so.1
ln -s libmfp.so.1.0.1 libmfp.so
cd sane
ln -s libsane-smfp.so.1.0.1 libsane-smfp.so.1
ln -s libsane-smfp.so.1.0.1 libsane-smfp.so

2) Edit /etc/sane.d/dll.conf and add the line "smfp" to the end of file. Add yourself to the groups lp and scanner.


Could perhaps somebody put this together in a deb-package?

I would like to do it myself but I am a bit too unexperienced with deb-files to do so. But should not be that hard to do.

To install this via apt-get would be a much better way than doing this by hand.

---

### Post by tweedledee on 2009-01-25
> **uggy said:**
> - If you try to open the .tar.gz with "gzip" and "tar".. You will have no error:

Thanks for sharing; I have updated the first post to reflect this information.

---

### Post by tweedledee on 2009-01-25
> **albertz said:**
> Could perhaps somebody put this together in a deb-package?

I would like to do it myself but I am a bit too unexperienced with deb-files to do so. But should not be that hard to do.

To install this via apt-get would be a much better way than doing this by hand.

Yes, but it would actually be a lot of work to maintain, as there are multiple versions of the binary driver (and it does matter for at least some printers), many versions of the installer scripts, and the "manual" instructions don't necessarily work for every model.  Not to mention the fact that printers with scanners need entirely different options than basic printers, and network vs. non-network is an issue.  On top of which, Samsung is not very clear on their new releases.

On the other hand, it would only take someone at Samsung with access to appropriate information a few weeks to simplify the system, build a few appropriate debs, and provide a proper GUI to select necessary options.  And then a few hours a week to maintain.  But apparently a few thousand dollars a year is not worth it to Samsung to increase their usability (and sales) to Linux users; they could be right, but it's a bit frustrating.

---

### Post by gizmobay on 2009-01-25
I just upgraded my Kubuntu 8.04 to Kubuntu 8.10. I had the CLP300 working under 8.04. The only issue is that I've lost my CLP300. One of the major problems I'm having is I can't see the text when I fire up the Samsung Unified Driver control panel as it flashes on and off when I move the mouse. I have GTK and Glibc per the Samsung docs. It feels like I missing another dependency. Can someone point me in the right direction?

---

### Post by gizmobay on 2009-01-25
It was compbiz messing up the text. I should be able to fix now that I can see the text.

---

### Post by albertz on 2009-01-25
> **tweedledee said:**
> Yes, but it would actually be a lot of work to maintain, as there are multiple versions of the binary driver (and it does matter for at least some printers), many versions of the installer scripts, and the "manual" instructions don't necessarily work for every model.  Not to mention the fact that printers with scanners need entirely different options than basic printers, and network vs. non-network is an issue.  On top of which, Samsung is not very clear on their new releases.


I would of course seperate the scanner driver from the printer drivers. That simplifies it already a bit.

And I am not sure if the printer driver for my SCX-4200 really changed that much in the last two years (the last time I checked it). And I would still be happy if there is a 2 years old deb-file I could install and even prefer this probably over this manual installation procedure (and running their install script is really not an option at all for me, it just messes too much around in my system).

Anyway, for the printer I find a very attractive alternative: Splix2 with a special patch for the SCX-4200. It is open source and has a deb-file for x86 and amd64 which can be downloaded here:
[http://www.openprinting.org/show_printer.cgi?recnum=Samsung-SCX-4200](http://www.openprinting.org/show_printer.cgi?recnum=Samsung-SCX-4200)
And it just works. One click for the deb download, some further clicks for the deb installation, again a few clicks for selecting the new printer-driver in the CUPS manager and that's all, just works fine. :)

I can live without the scanner for now, will check back in some month if there is a nice way to install the driver (and hopefully a working driver, not this crap which segfaults if it is not root).

> **tweedledee said:**
> 
On the other hand, it would only take someone at Samsung with access to appropriate information a few weeks to simplify the system, build a few appropriate debs, and provide a proper GUI to select necessary options.  And then a few hours a week to maintain.  But apparently a few thousand dollars a year is not worth it to Samsung to increase their usability (and sales) to Linux users; they could be right, but it's a bit frustrating.

And probably it would be even much easier to maintain for them than this really dirty hacky installer script. But it's the usual problem with maintainers which obviosly don't have much experiences with Linux.

Perhaps we should show them more how bad their installer is and how big the need is for a working package. Is there perhaps a repetition going on already? Or can somebody post an emailadress here where I (and others) can just leave some words?

Of course, Best would be if they would just release the sources (of pipsplus and other stuff which belongs to the driver). But that is perhaps too much to dream of.

---

### Post by albertz on 2009-01-25
> **uggy said:**
> Ohh regarding driver package cuurently available by samsung....
They are looking "weird"...

- If you try to open the .tar.gz with FileRoller.. You will failed..

- If you try to "open" the .tar.gz with "tar" command..(Probably what FilreRoller use) You will got the folowing error: (as reported by tweedledee and ianwoodward)

$ tar zxf 20081006172749281_UnifiedLinuxDriver.tar.gz 
gzip: stdin: decompression OK, trailing garbage ignored
tar: Child returned status 2
tar: Des erreurs ont provoqué l'arrêt du programme
$

- If you try to open the .tar.gz with "gzip" and "tar".. You will have no error:

$ gzip -dc 20081006172749281_UnifiedLinuxDriver.tar.gz | tar xf -
gzip: 20081006172749281_UnifiedLinuxDriver.tar.gz: decompression OK, trailing garbage ignored
$


I don't know why yet ;)

Is there an option for tar to ignore such child errors? (Status 2 looks like an error for tar.)

If not, fill in a feature request for tar.

And fill in a bug report about this not working with FileRoller.

The last method works because tar just gets the data and doesn't break of any error from gzip (because it does not know about them). So FileRoller could be fixed by just using this method (or by saying tar that it should ignore such errors; at least it should try).

---

### Post by gizmobay on 2009-01-25
I've got it work somewhat. I went to localhost 631 and setup a new printer and this comes up in the unified driver config. I can start and stop the printer from there as I just hit refresh in the cups browser to see if it worked. The problem I'm having is when I go to test in the UDC and it checks port it says failed. It can control the start and stop so I don't see why the port test fails. It won't print a test page from the UDC but I can from the Cups browser.

---

### Post by uggy on 2009-02-02
> **tweedledee said:**
> Thanks for sharing; I have updated the first post to reflect this information.

Hi tweedledee,

Thank you very much for keeping this thread up to date ;)

---

### Post by gluxoid on 2009-02-08
I once reported that the CLP-310 worked without issues, however after reinstalling Ubuntu 8.10 amd64 I ran into [Uggy's problem he posted two weeks ago]("http://ubuntuforums.org/showpost.php?p=6605540&postcount=184").

Here is my guide that works for me:

1. Go to the CLP-310 page of Samsung and download ALL driver archives:

  - The Unified Linux Driver (UnifiedLinuxDriver.tar.gz, version 3.00.28)
  - The smartpanel (smartpanel-2.00.34.tar.gz)
  - The printer setting utility (psu-2.00.12.tar.gz)

2. Unpack all

# sudo tar -xvzf UnifiedLinuxDriver.tar.gz
# sudo tar -xvzf smartpanel-2.00.34.tar.gz
# sudo tar -xvzf psu-2.00.12.tar.gz

3. Install

# cd cdroot
# sudo ./autorun

Every time when the printer is plugged, Ubuntu will install the printer with a new name. This should make Ubuntu "easier" to use, but the effect is the opposite.

4. Remove all CLP-310 printers

  - Go to System->Administration->Printing
  - Delete all CLP-310 printers

5. Replug the printer

Ubuntu presents a pop-up with a small "Configure" button

6. Click on "Configure"

7. Select the driver to use
  
  - Click on "Make and Model"
  - Select printer from database -> "Samsung" (click Next)
  - Select "Samsung CLP-310 Series (SPL-C)" (click Next)
  - Select "Use the new PPD" so all settings are renewed

8. Print a test page and/or configure the printer :)

My guide may work for other Samsung printers and versions as well. For me getting the psu and smartpanel archive may have been important to solve the problem as it is the only thing I remember I changed in my procedure. 

The smartpanel is hideous and annoying but it shows how much toner is left and if something is wrong, such as "paper mismatch" if you try to print A4 without configuring the printer :(


*PS: This tar/gzip problem is solved by Samsung. The new archives unpack as they should.*

---

### Post by albertz on 2009-02-08
Just some general important hint:

You really should be carefull which of these HOWTOs you will follow in which way. **Most of them will result in a messed up system!**

Most important is that you never run (or only if you really know what that means) the installer by Samsung.

In some of the HOWTOs which are posted here, that really should be pointed out.

---

### Post by gluxoid on 2009-02-08
Your post lacks an argument. Why would this be the case? I guess that those really long instructions that avoid using the Samsung installer are necessary only for *old* Samsung installers.

---

### Post by albertz on 2009-02-08
> **gluxoid said:**
> Your post lacks an argument. Why would this be the case? I guess that those really long instructions that avoid using the Samsung installer are necessary only for *old* Samsung installers.

The last time I checked the source of the installer, I have seen code that messed around in the system, for example set setuid flags randomly on some applications etc.

Anyway, it is always not a good choice to not use apt-get to install an application. If you use such a hand-made installer, you always have problems later to uninstall and clean the mess up.

---

### Post by carniola on 2009-02-19
> **gluxoid said:**
> Here is my guide that works for me

Thank you, gluxoid. That worked like a charm for me.

---

### Post by w4llet on 2009-02-19
> **tweedledee said:**
> Mini-guide to installing Samsung printers & Unified Driver:
(Updated 25 January 2008 - noted multiple drivers being released by Samsung and how to deal with poor packaging)



3. (...)  ```
sudo Linux/install.sh
```  (...)

**Printers with reported success**:
  CLP-300 ([http://ubuntuforums.org/showpost.php?p=3036870&postcount=35](http://ubuntuforums.org/showpost.php?p=3036870&postcount=35), [http://ubuntuforums.org/showpost.php?p=3094897&postcount=43](http://ubuntuforums.org/showpost.php?p=3094897&postcount=43), [http://ubuntuforums.org/showpost.php?p=3651256&postcount=79](http://ubuntuforums.org/showpost.php?p=3651256&postcount=79), [http://ubuntuforums.org/showpost.php?p=5801350&postcount=159](http://ubuntuforums.org/showpost.php?p=5801350&postcount=159))
  CLP-310 ([http://ubuntuforums.org/showpost.php?p=6117599&postcount=171](http://ubuntuforums.org/showpost.php?p=6117599&postcount=171), [http://ubuntuforums.org/showpost.php?p=6698222&postcount=195](http://ubuntuforums.org/showpost.php?p=6698222&postcount=195))
  CLP-315 ([http://ubuntuforums.org/showpost.php?p=5731280&postcount=156](http://ubuntuforums.org/showpost.php?p=5731280&postcount=156), [http://ubuntuforums.org/showpost.php?p=6103730&postcount=169](http://ubuntuforums.org/showpost.php?p=6103730&postcount=169))
  CLP-550 (me)
  CLP-600 ([http://ubuntuforums.org/showpost.php?p=3282722&postcount=61](http://ubuntuforums.org/showpost.php?p=3282722&postcount=61))
  CLP-610ND ([http://ubuntuforums.org/showpost.php?p=5719188&postcount=154](http://ubuntuforums.org/showpost.php?p=5719188&postcount=154))
  CLX-2160n ([http://ubuntuforums.org/showpost.php?p=4637063&postcount=108](http://ubuntuforums.org/showpost.php?p=4637063&postcount=108))
  CLX-3160FN ([http://ubuntuforums.org/showpost.php?p=4459156&postcount=100](http://ubuntuforums.org/showpost.php?p=4459156&postcount=100))
  ML-2240 ([http://ubuntuforums.org/showpost.php?p=5721210&postcount=155](http://ubuntuforums.org/showpost.php?p=5721210&postcount=155))
  ML-2510 ([http://ubuntuforums.org/showpost.php?p=2167697&postcount=5](http://ubuntuforums.org/showpost.php?p=2167697&postcount=5), [http://ubuntuforums.org/showpost.php?p=2341240&postcount=14](http://ubuntuforums.org/showpost.php?p=2341240&postcount=14), [http://ubuntuforums.org/showpost.php?p=2341298&postcount=16](http://ubuntuforums.org/showpost.php?p=2341298&postcount=16), [http://ubuntuforums.org/showpost.php?p=2518731&postcount=26](http://ubuntuforums.org/showpost.php?p=2518731&postcount=26), [http://ubuntuforums.org/showpost.php?p=3320343&postcount=63](http://ubuntuforums.org/showpost.php?p=3320343&postcount=63), [http://ubuntuforums.org/showpost.php?p=3368106&postcount=64](http://ubuntuforums.org/showpost.php?p=3368106&postcount=64))
  ML-2510/XEU ([http://ubuntuforums.org/showpost.php?p=2367964&postcount=18](http://ubuntuforums.org/showpost.php?p=2367964&postcount=18))
  ML-2571n ([http://ubuntuforums.org/showpost.php?p=2313226&postcount=12](http://ubuntuforums.org/showpost.php?p=2313226&postcount=12), and 2 complete guides at [http://ubuntuforums.org/showthread.php?p=4086777](http://ubuntuforums.org/showthread.php?p=4086777))
  SCX-4100 ([http://ubuntuforums.org/showpost.php?p=4175927&postcount=97](http://ubuntuforums.org/showpost.php?p=4175927&postcount=97), [http://ubuntuforums.org/showpost.php?p=5626900&postcount=153](http://ubuntuforums.org/showpost.php?p=5626900&postcount=153), [http://ubuntuforums.org/showpost.php?p=5898537&postcount=162](http://ubuntuforums.org/showpost.php?p=5898537&postcount=162))
  SCX-4200 ([http://ubuntuforums.org/showpost.php?p=2187170&postcount=10](http://ubuntuforums.org/showpost.php?p=2187170&postcount=10), [http://ubuntuforums.org/showpost.php?p=3794756&postcount=82](http://ubuntuforums.org/showpost.php?p=3794756&postcount=82), [http://ubuntuforums.org/showpost.php?p=4776310&postcount=114](http://ubuntuforums.org/showpost.php?p=4776310&postcount=114), [http://ubuntuforums.org/showpost.php?p=6080732&postcount=168](http://ubuntuforums.org/showpost.php?p=6080732&postcount=168))
  SCX-4521F ([http://ubuntuforums.org/showpost.php?p=2199517&postcount=11](http://ubuntuforums.org/showpost.php?p=2199517&postcount=11), [http://ubuntuforums.org/showpost.php?p=3198064&postcount=57](http://ubuntuforums.org/showpost.php?p=3198064&postcount=57), [http://ubuntuforums.org/showpost.php?p=3536994&postcount=70](http://ubuntuforums.org/showpost.php?p=3536994&postcount=70))

**Note to those with multifunction printers**: xsane (and the smfp protocol Samsung adds) appears to be a problem.  The above solution MIGHT work for you, I don't know.  You can also check these sites for possible solutions (if the posts here don't help):
[http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian](http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian)
[http://www.elijahlofgren.com/ubuntu/#scx-4521f](http://www.elijahlofgren.com/ubuntu/#scx-4521f)
[http://www.linuxprinting.org](http://www.linuxprinting.org)
[http://www.vyvy.org/main/node/146](http://www.vyvy.org/main/node/146)

Good luck, and let me know if you have success and/or failure, and I'll try to modify accordingly.

Worked like a glove for me.

You can add ML-1630w Printer in your list.

Wireless Printer working like a charm (printer is wireless connected to a wireless router and I have several computers (Linux and windows as well) sharing the printer via wifi/router.

And you were right: I have a monochrome laser printer. Instalation of this drive wasnt necessary. But, following your steps provide me Smart Panel in linux.

Thanks!

:D

---

### Post by djtronic on 2009-03-04
> **gluxoid said:**
> I once reported that the CLP-310 worked without issues, however after reinstalling Ubuntu 8.10 amd64 I ran into [Uggy's problem he posted two weeks ago]("http://ubuntuforums.org/showpost.php?p=6605540&postcount=184").

Here is my guide that works for me:

1. Go to the CLP-310 page of Samsung and download ALL driver archives:

  - The Unified Linux Driver (UnifiedLinuxDriver.tar.gz, version 3.00.28)
  - The smartpanel (smartpanel-2.00.34.tar.gz)
  - The printer setting utility (psu-2.00.12.tar.gz)

2. Unpack all

# sudo tar -xvzf UnifiedLinuxDriver.tar.gz
# sudo tar -xvzf smartpanel-2.00.34.tar.gz
# sudo tar -xvzf psu-2.00.12.tar.gz

3. Install

# cd cdroot
# sudo ./autorun

Every time when the printer is plugged, Ubuntu will install the printer with a new name. This should make Ubuntu "easier" to use, but the effect is the opposite.

4. Remove all CLP-310 printers

  - Go to System->Administration->Printing
  - Delete all CLP-310 printers

5. Replug the printer

Ubuntu presents a pop-up with a small "Configure" button

6. Click on "Configure"

7. Select the driver to use
  
  - Click on "Make and Model"
  - Select printer from database -> "Samsung" (click Next)
  - Select "Samsung CLP-310 Series (SPL-C)" (click Next)
  - Select "Use the new PPD" so all settings are renewed

8. Print a test page and/or configure the printer :)

My guide may work for other Samsung printers and versions as well. For me getting the psu and smartpanel archive may have been important to solve the problem as it is the only thing I remember I changed in my procedure. 

The smartpanel is hideous and annoying but it shows how much toner is left and if something is wrong, such as "paper mismatch" if you try to print A4 without configuring the printer :(


*PS: This tar/gzip problem is solved by Samsung. The new archives unpack as they should.*

Thank you very much.
Perfect

---

### Post by dmikulec on 2009-03-12
I just updated to Ubuntu 8.10 and installed the new Unified Linux Driver (ver.3.00.37).  I followed their instructions (including the Configurator) and installed thru 95% when a gif display window opened and installation stopped. Installation resumed when I closed that window.  The printer does not work.  System>Admin>Printing recognizes my ML-2010 but reports "Stopped - Filter "rasterospl2" for printer "ML-2010" not available: No such file or directory"

I would appreciate any direction on how to rectify this situation.

Thanks,

Don

---

### Post by owend on 2009-03-15
Possible solution, so stupid you've probably tried it already: I had "driver" problems with a ML-1510, but it turned out not to be the driver at all: try plugging the USB from the printer direct to the computer, or try a different direct USB connection. 

I have two printers running through a UB hub, and if the Samsung isn't in the FIRST outlet from the hub it says "...may not be connected" and usually won't print at all (sometimes gibberish!), but seems to pick up fine if it's the first. Being second doesn't seem to bother the other (HP Deskjet) printer.

---

### Post by mudman00 on 2009-03-26
I hope I am following the proper protocol by asking my question on this thread. If not, please let me know and I will make the needed correction.

I am a very recent convert to Ubuntu. I am using version Ubuntu32 8:10

I have a Samsung SCX-4100 printer. It is connected to the machine via a USB cable if that makes any difference. It is not recognized by Ubuntu.

I downloaded the unified driver from the Samsung site. Saved it to the desktop.

I extracted the driver to the desktop.....it is a file that says cdroot....to that point everything went well.

Then I ran into a wall.....please keep in mind that I am beginning user...am not familiar with code....but I am able to follow a procedure.

I was using terminal and typed in cd Desktop/cdroot/Linux./install.sh

It didn't work


I get a message that says no such file or directory exists.

So, I changed things up a bit thinking that I didn't have the string written correctly on the command line and entered the following 

cd Desktop/cdroot/Linux

This took me to

Desktop/cdroot/Linux#      which is correct I believe

Then I entered ./install.sh

This action resulted in the following

[: 636: ==: unexpected operator

Regardless of what I try with my limitied knowlege I keep getting the same thing.

Do you have any suggestions......

I was not able to copy and paste the command lines and the results from the terminal window (how to I do that BTW)...but I was careful to include all of the characters and the proper spacing or lack thereof.

Thank you for any and all help

Craig

---

### Post by yahs on 2009-03-26
Nearly there!

Open a terminal (Accessories-Terminal)
Change directory to /cdroot/Linux
Run this command - sudo ./install.sh (the full stop and forward slash are needed). Enter your password.
Follow the prompts, reboot and that's it.

---

### Post by ozp on 2009-03-26
I have a CLX-3160FN 

Ive tried 3 drivers and none are good

Do you know how to configure any driver in order to get better color print results?

here is what I get from those drivers. Is this the quality you get?


[IMG]http://farm4.static.flickr.com/3430/3388227249_0bafb7443c_b_d.jpg[/IMG]

The baby is my son

---

### Post by mudman00 on 2009-03-27
> **yahs said:**
> Nearly there!

Open a terminal (Accessories-Terminal)
Change directory to /cdroot/Linux
Run this command - sudo ./install.sh (the full stop and forward slash are needed). Enter your password.
Follow the prompts, reboot and that's it.

Yahs....thank you for the information. I think I did what you said, but ended  up with the same unexpected operator message again. I am copying the commands and result below

craig@benedictisanass:~$ /cdroot/Linux
bash: /cdroot/Linux: No such file or directory
craig@benedictisanass:~$ cd /cdroot/Linux
bash: cd: /cdroot/Linux: No such file or directory
craig@benedictisanass:~$ cd Desktop/cdroot/Linux
craig@benedictisanass:~/Desktop/cdroot/Linux$ sudo ./install.sh
[sudo] password for craig: 
[: 636: ==: unexpected operator
craig@benedictisanass:~/Desktop/cdroot/Linux$ 

Craig

---

### Post by yahs on 2009-03-27
I too have a scx-4100 and it works well both in 8.04 and 8.10, it is connected by usb. I am not familiar with the error message, so let's try again, I have re-read your original post and I noticed you said Ubuntu 8.10 doesn't recognise the printer.
Ubuntu recognises my printer but only installs a generic printer, so you have to download the Samsung Unified Driver to get everything working properly.
If you open a terminal and type lsusb you should see a reference to Samsung.

This is what I get when I type lsusb

Bus 005 Device 005: ID 0424:223a Standard Microsystems Corp. 8-in-1 Card Reader
Bus 005 Device 004: ID 05e3:0606 Genesys Logic, Inc. D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 04e8:3413 Samsung Electronics Co., Ltd 
Bus 001 Device 004: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000

So as long as your printer is switched on and plugged in Ubuntu will (should) find it.
I suggest you first check the lsusb command to see what you get.

One other point, as you say you're pretty new to Ubuntu.
When sudo asks for your password, have you entered your password and then completed a command.
For instance if you wanted to edit the boot loader you would type the command sudo gedit /boot/grub/menu.lst
You would then be prompted for your password and after you have entered it, the file menu.lst will appear on your screen. (Just exit without making any changes)
Just wondering if the error message is generated in response to your password or in response to the ./install.sh command.
Let me know how you get on.

---

### Post by mudman00 on 2009-03-27
> **yahs said:**
> I too have a scx-4100 and it works well both in 8.04 and 8.10, it is connected by usb. I am not familiar with the error message, so let's try again, I have re-read your original post and I noticed you said Ubuntu 8.10 doesn't recognise the printer.
Ubuntu recognises my printer but only installs a generic printer, so you have to download the Samsung Unified Driver to get everything working properly.
If you open a terminal and type lsusb you should see a reference to Samsung.

This is what I get when I type lsusb

Bus 005 Device 005: ID 0424:223a Standard Microsystems Corp. 8-in-1 Card Reader
Bus 005 Device 004: ID 05e3:0606 Genesys Logic, Inc. D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 04e8:3413 Samsung Electronics Co., Ltd 
Bus 001 Device 004: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000

So as long as your printer is switched on and plugged in Ubuntu will (should) find it.
I suggest you first check the lsusb command to see what you get.

One other point, as you say you're pretty new to Ubuntu.
When sudo asks for your password, have you entered your password and then completed a command.
For instance if you wanted to edit the boot loader you would type the command sudo gedit /boot/grub/menu.lst
You would then be prompted for your password and after you have entered it, the file menu.lst will appear on your screen. (Just exit without making any changes)
Just wondering if the error message is generated in response to your password or in response to the ./install.sh command.
Let me know how you get on.

Yahs....I typed the lsusb command into a terminal and got the following. It doen't look like what you have

 lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I down loaded the unified driver to the desktop and was able to extract the driver for the printer to the desktop...it in in a folder that says croot on the desktop. I have looked in it an found it. I just can't get the system to run the install....it is resulting in the unexpected user problem...

The printer is on and it is connected to the machine via a USB cable. It all worked great until....I installed Ubuntu. It still works when my spousal unit plugs the printer into her laptop, with that viral code from the evil empire up in Redmond Washington as an operating system, using the same cable. She is currently peeved with me about my change to Ubuntu and will not consider the very positive aspects of Linux in general until I am able to get her printer up and running on this system.

I typed the sudo gedit /boot/grub/menu.lst in and a menu list poped up in a separate window...I am pasting what came up below

 menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=693f4cd2-d2d0-4e06-9236-dbf6411547d4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=693f4cd2-d2d0-4e06-9236-dbf6411547d4

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

Is this what should have happened?

And yes, I know next to nothing about Ubuntu....don't be concerned about asking me if I have done the seemingly simplest of things. I will not be offended in any way, shape or form......
Craig

---

### Post by yahs on 2009-03-27
Looking at your results for lsusb, - this means you don't have anything plugged into any USB ports?

The sudo gedit /boot/grub/menu.lst command was just to check that your password is correct and active. The actual file is only really needed if you dual boot.

The fact that lsusb didn't show your printer is like Windows not recognising a piece of hardware, so trying to install software for that particular item isn't much use.

How about booting from a live Ubuntu Cd and then checking System, Administartion, Printing to see if your Samsung appears? (Printer plugged in and switched on).

---

### Post by mudman00 on 2009-03-27
> **yahs said:**
> Looking at your results for lsusb, - this means you don't have anything plugged into any USB ports?

The sudo gedit /boot/grub/menu.lst command was just to check that your password is correct and active. The actual file is only really needed if you dual boot.

The fact that lsusb didn't show your printer is like Windows not recognising a piece of hardware, so trying to install software for that particular item isn't much use.

How about booting from a live Ubuntu Cd and then checking System, Administartion, Printing to see if your Samsung appears? (Printer plugged in and switched on).

Yahs....I just went ahead and checked the sys admin printer....the printer is showing up as recognized. There is a little icon of the printer in the window with a Samsung scx-4100 under it....so Ubuntu is now seeing it. Just won't print. Still can't get the driver to run....

Craig

---

### Post by yahs on 2009-03-27
Craig,
If your printer is showing under sys, admin I'm not sure why lsusb doesn't have an entry for Samsung.

I'm not an expert but I have installed and helped to install a number of samsung printers. Before the latest Unified driver (ver 3.00.37) it was often a fairly complicated process particularly to get scanning working. Now it is usually just a case of download the driver, extract to desktop or home folder, open a terminal, switch to the /cdroot/Linux directory and type sudo ./install.sh Follow the prompts and it's done.

Can you try my suggestion of booting from a live Cd, check to see if the printer shows and if so download a fresh copy of the Unified driver and have another try at installing while you are still running the live Cd. If this doesn't work I'm not really sure what the fix is, though I'll try and find a solution.

---

### Post by yahs on 2009-03-27
Hi Craig - Last post for a while as I am away for a few days.

Just done a fresh install of Ubuntu 8.10

This is my listing from lsusb

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 005: ID 04e8:3413 Samsung Electronics Co., Ltd SCX-4100 Scanner
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 005: ID 0424:223a Standard Microsystems Corp. 8-in-1 Card Reader
Bus 005 Device 004: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Extracted Driver to the desktop

cd Desktop/cdroot/Linux

sudo ./install.sh

I get the following error message

libstdc++.so.5 (gcc 3.0.x .. 3.3.x) not found, install ... done
libtiff.so.3 not found, install ... done
****  It seems Qt library is not installed, or X display is not accessible.
****  Custom Qt library will be configured for use with this package.

However Ubuntu continues by loading the Unified Driver GUI installer.

Then it is just a question of following prommpts, reboot and everything works,

Ignore the point above trying to install from the live cd because when you get to the point where you need to do sudo ./install you haven't set up a supervisor password- it's obviously too late for my brain!
Hope you have success.

---

### Post by mudman00 on 2009-03-28
Thank you again for all of the help......there was, however, no joy when I tried to print after booting up from the disk. It did not even have a printer listed when I checked.

I'm betting that the unrecognized user message is key to this one.. I have my handy dandy Ubuntu Pocket Guide and Reference now (by Keir THomas)...I'll read it cover to cover....do a search around for the specific error after I am more fluent in the lingo of Ubunto...and see what i am able to come up with.

At the least, there is a Linux users group at my local ISP this coming Wednesday night and there are several folks there who have been using linux for years. If I am able to find the solution I will post it up for all to see.

Thank you again.

Craig

---

### Post by mudman00 on 2009-04-02
Update.....last night I was able to unzip unified driver package with the help of a few folks at our Linux computer users group at Hal-pc here in Houston.

I had my box with me, but didn't hook up the printer. After using the command that Tweddledee suggested.....gzip -dc <file>.tar.gz | tar xf -..............an install actually worked with what has been described. Yeah!!!!! That is the good news.

The bad news is that the printer, while fully recognized, will still not print anything.....

There is now a difference in the problem.....

When I go to System/Admin and then highlight and click on the printer icon, the window pops up...in the window are two icons. One is for the CLP 300-spic printer and the other is for the SCX-4100.....the clp-300 popped up and became the default printer when the integrated driver package was unzipped and the GUI prompts were followed. The trouble is that I do not have, nor have I ever had, a CLP 300-spic printer connected to the machine.

I changed things to make sure that the SCX-4100 is the default printer. It now will print, but not properly, when I do a test page. The result is the following

INTERNAL ERROR - pub
    POSITION: Ox16b296 (1487510)
    
    SYSTEM  : H6FW/os_hook

    LINE    : 1276

    VERSION : QPDL 1.22 12-02-2003

Does anyone know what this means?

Thank you,
Craig

---

### Post by mudman00 on 2009-04-02
> **tayroni said:**
> I'M BACK!!!

And today I'm installed intrepid ibex and I had problems (again) with the Samsung SCX-4200. On intrepid there is the same usb-related problem on hardy: The driver software by SAMSUNG looks for the usb device on /proc/bus/usb/00*/00*, but all software is ported to look only on /dev/bus/usb/00*/00*.

But, the same manual for hardy cannot be followed by intrepid because 
/etc/init.d/mountdevsubfs.sh was updated.

To reenable support on /proc/bus/usb/00*/00*, add yourself to the groups lp, lpadmin and scanner:

sudo adduser your_login_here lp
sudo adduser your_login_here lpadmin
sudo adduser your_login_here scanner

and edit the file /etc/init.d/mountdevsubfs.sh. ADD THE LINES:

#
# Magic to KEEP /proc/bus/usb working
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

right below the line

domount devpts "" /dev/pts devpts -onoexec,nosuid,gid=$TTYGRP,mode=$TTYMODE

Finally, reboot.

HAPPY INTREPID TO YOU!!!

I just went ahead and tried to follow these directions.......surprise, surprise...still not quite there. I am not sure how to really go about doing this.

I didn't have any difficulty adding myself to the groups listed. I was already part of two of them since I am root...

When it comes to the next step and editing the file I don't know how to do this.....

I am pasting what I did and the results below....

craig@benedictisanass:~$ sudo adduser craig lp
[sudo] password for craig: 
The user `craig' is already a member of `lp'.
craig@benedictisanass:~$ sudo adduser craig lpadmin
The user `craig' is already a member of `lpadmin'.
craig@benedictisanass:~$ sudo adduser craig scanner
Adding user `craig' to group `scanner' ...
Adding user craig to group scanner
Done.
craig@benedictisanass:~$ cd Desktop/UnifiedLinuxDriver.tar.gz
bash: cd: Desktop/UnifiedLinuxDriver.tar.gz: Not a directory
craig@benedictisanass:~$ cd Desktop
craig@benedictisanass:~/Desktop$ cd cdroot/
craig@benedictisanass:~/Desktop/cdroot$ ls
autorun  Linux
craig@benedictisanass:~/Desktop/cdroot$ linux
The program 'linux' is currently not installed.  You can install it by typing:
sudo apt-get install user-mode-linux
bash: linux: command not found
craig@benedictisanass:~/Desktop/cdroot$ 

Help Please......

Craig

---

### Post by mudman00 on 2009-04-02
I'll start with the funny icons....I have attempted to include, 31 according to the submission error message which I am now editing to 8...just trying to show my appreciation and excitment here..editing proceeding now......
                                   :guitar::
                                   \\:D/\\:D/\\:D/
                                   :biggrin::biggrin::

Now the language.........

Thank you, thank you thank you, thank you...for allllll of the help!!!!!!!!!!!!!!!!

It is up and running!!!!! Atleast the printer is.....I won't try the scanner for a few days and then I'm betting I will be back..

But, for the time being....I am a happy man....my spousal unit has promised to put away the lash for a few days.....

Booooooo    Yaaaaaaaaaahhhhhhhhhh

I'm not exactly sure what I did, since I really don't understand what it was that I did. I pretty much followed the advice of Tweedeldee and Yahs...then got some help in a local group....then re-read the entire thread.....then...finally.....as I was pulling my thinning hair out, I went back and read the directions about adding a new printer.

The printer had been recognized all along, so I thought that I didn't need to do anything else. The appearance of the printer that I don't have was also an issue that I did not understand.

So I went in and deleted both printers. Then, as per instructions (I know RTFM), I clicked the new printer button and Ubuntu immediately recognized the SCX-4100.

The little icon in the upper right side of the desk top popped down a little window that told me the printer was added and there was a configure button.....I clicked the button.

Then I just looked at everything in the configure window, which looked good enough, and I tried the good ole smoke test (I ran the test page)....badda bing badda boom.....It be workin....It be workin:):P

Thank you again to all who have contributed to this thread

I will redouble my efforts to learn about Ubuntu and look forward to being able to contribute to the community.

Craig Clark
Houston, Texas

---

### Post by |-|ans on 2009-04-04
Noticed the referral to the older printer driver at the Samsung site as well. Using a CLP-500 I started with the described way and had quite some issues doing so. Indeed unpacking was tricky and also the printer (although connected) was not found. At some point after trying a lot I did look at a newer printer (with the 3.x driver offered for download) and grabbed that Unified Printer Driver. To my suprise the CLP-500 (file CLP-500splc.ppd) and many more are in there as well. So I installed this (after removing the older one I picked up at Samsung) and everything worked fine fo me. Installed both the Splix and the SPL(C) version even to find in general the Splix looks better (but photos awful) and the SPL(C) gives a better result for photos (although very grainy). Tried the Smart Panel as well, but that did not work and seems mainly to give information about cartridge levels (?!). Printer works fine since (although picture quality stil somewhat disappointing and I do miss this print booklet option).

---

### Post by yahs on 2009-04-05
Craig,
Glad to see you have had success.
Can you post some info on your solution and the error message?

---

### Post by mudman00 on 2009-04-06
> **yahs said:**
> Craig,
Glad to see you have had success.
Can you post some info on your solution and the error message?In the words of my 7 year old...it must have been "majic"....lolol....

In all seriousness: Following tweedledees' directions properly, and the help of you and others provided the information necessary to fix the problem of printing.

I am so inexperienced at using command line script that I was not even properly entering the code to begin with. 

As you have noted, the difference with the problem specific to my machine and printer was the error message that remains a mystery....I will ask again about it at this Wednesday nights user group over at my ISP and see if anyone can come up with a reason. I will post up what we find and then try and post a step by step method and explanation of what I did so that everyone can see it.

In the end, as I said, the solution was pretty much contained in this thread. It boiled down to poking around, trial and error and persistence.

Perhaps tweedledee can explain the error message....I am thinking about sending him a PM, but he tells us not to do so in the intial post and he has been updating periodically. Thoughts?

Craig

---

### Post by tweedledee on 2009-04-09
> **mudman00 said:**
> Perhaps tweedledee can explain the error message....I am thinking about sending him a PM, but he tells us not to do so in the intial post and he has been updating periodically. Thoughts?

Your error from the install script could have arisen lots of ways (in my experience, the error is equivalent to saying "script tried to do something and it didn't work").   However, there are two more likely possibilites.  One (my personal bet) is that when you first extracted the archive, one or more files (not necessarily install.sh itself) was corrupted, especially given the apparent conflicts recently between Samsung's creation of the archive and the ability of programs to extract from it.  The other common cause is that soemwhere in all the steps you followed or advice you were given, you changed the shell you were running (e.g., from dash to bash).

It does appear you and yahs have brough to light a couple of points that I will incorporate into the initial post, including the need to clarify/re-emphasize the "delete auto-installed printers" steps.

---

### Post by tweedledee on 2009-04-09
> **ozp said:**
> I have a CLX-3160FN 

Ive tried 3 drivers and none are good

Do you know how to configure any driver in order to get better color print results?

here is what I get from those drivers. Is this the quality you get?

You may just want to try other related printer drivers.  I get large variations in printer quality (mainly color tones) depending on the exact configuration and driver I use, and have seen cases where the best output is to use a driver for a different printer altogther.  Unfortunately, I have not found any system for dealing with this other than trial and error, and occasionally an update to the printer backend (CUPS, etc.) that you are using will also have an effect (good or bad).

---

### Post by tweedledee on 2009-04-09
> **|-|ans said:**
> Noticed the referral to the older printer driver at the Samsung site as well. Using a CLP-500 I started with the described way and had quite some issues doing so. Indeed unpacking was tricky and also the printer (although connected) was not found. At some point after trying a lot I did look at a newer printer (with the 3.x driver offered for download) and grabbed that Unified Printer Driver. To my suprise the CLP-500 (file CLP-500splc.ppd) and many more are in there as well.

Thanks for the tip, I will look into this.

---

### Post by tweedledee on 2009-04-09
> **dmikulec said:**
> I just updated to Ubuntu 8.10 and installed the new Unified Linux Driver (ver.3.00.37).  I followed their instructions (including the Configurator) and installed thru 95% when a gif display window opened and installation stopped. Installation resumed when I closed that window.  The printer does not work.  System>Admin>Printing recognizes my ML-2010 but reports "Stopped - Filter "rasterospl2" for printer "ML-2010" not available: No such file or directory"

I would appreciate any direction on how to rectify this situation.

Thanks,

Don

Did you get this issue resolved by adjusting the USB port used (or something else)?  This could also be a case of the need to juts delete all installed printers and re-add them in the control panel.

---

### Post by yahs on 2009-04-09
Regarding HOWTO Install Samsung Unified Printer Driver

I started using Ubuntu 8.04 April 2008 and I have followed your excellent post many times with various installs using Drivers from Samsung.co.uk

I have separate partitions purely for installing and testing and since the release of Unified Driver ver 3.00.37 I have installed 8.04.1, 8.04.2, Linux mint 6, Intrepid and Jaunty beta all with 100% success.

If the printer is turned off, I usually get the following message after running sudo ./install.sh
 
libstdc++.so.5 (gcc 3.0.x .. 3.3.x) not found, install ... done
libtiff.so.3 not found, install ... done
GUI mode installer execution failed, proceeding in text mode
****  Running text mode install
****  Press Enter to continue or q and then Enter to quit: 

**** Non-priviliged users found:
nobody yahs
****  Are you going to use USB-connected devices ?
****  If yes, users allowed to scan or manage printers should be added to lp
****  group. The list of non-privileged users proposed for addition is shown above.
****  Press y and then Enter to add users or Enter to leave lp group intact: 

****  Print drivers for the following device models available:
CLP-300splc CLP-310splc CLP-350ps CLP-500splc CLP-510splc CLP-550ps CLP-600splc CLP-610splc CLP-650ps CLP-660ps CLP-770ps CLX-216xsplc CLX-3160splc CLX-3170splc CLX-6200ps CLX-6240ps CLX-8380ps mfp560 mfp750 ML-1450ps ML-1510spl2 ML-1520spl2 ML-1610spl2 ML-1630spl2 ML-1630wspl2 ML-1640spl2 ML-1710spl2 ML-1740spl2 ML-1750spl2 ML-2010spl2 ML-2150ps ML-2150spl2 ML-2240spl2 ML-2245spl2 ML-2250spl2 ML-2510spl2 ML-2550ps ML-2550Sps ML-2550Sspl2 ML-2560ps ML-2570ps ML-2850ps ML-2855ps ML-3050spl2 ML-3470ps ML-3560spl2 ML-4050DMVps ML-4050ps ML-4550ps ML-6060ps ML-7300ps ML-8x00ps scx4100 scx4200 scx4300 scx4500 scx4500w scx4725 scx4x16 scx4x20 scx4x21 scx4x24 scx4x26 scx4x28ps scx5312f scx5635ps scx5835ps scx5x30 scx6x20PCL scx6x20 scx6x20PS scx6x22ps scx6x45ps scx6x55ps sf531p
****  Please enter model to install and press Enter: scx4100
INFO: Installing MFP port and SANE backend libraries ...
cat: /etc/modprobe.conf: No such file or directory
INFO: Installing GUI lpr ...
INFO: Fixing file ownership and permissions ...
INFO: Registering SANE backend ...
INFO: Registering CUPS printer ...
 * Restarting Common Unix Printing System: cupsd                                                                                                                          [OK] 
INFO: CUPS restart OK
INFO: Creating menu entries ...
INFO: Finishing installation ...
****  Text mode install finished

Printing and Scanning now work perfectly.

If the printer is turned on, Ubuntu finds it and assigns a generic printer on usb://Samsung/SCX-4100%20Series which doesn't work as there is a limited choice of drivers to choose from.
Having downloaded and extracted the Unified Driver File and Run the command sudo ./install.sh 
I stil get the error messages
libstdc++.so.5 (gcc 3.0.x .. 3.3.x) not found, install ... done
libtiff.so.3 not found, install ... done
The installation then starts the gui interface. Follow the prompts and printing and scanning is provided. Printing on mfp:/dev/mfp4. Scanner comes up as flatbed scanner SCX-4100 Series on USB:0
You now have 2 printer icons in the Samsung Unifed Driver Configurator and if you select properties for the printer on usb://Samsung/SCX-4100%20Series and change the printer driver to, in my case SCX-4100 the printer works properly, so you have a choice of using either one.

Regarding your post

"General Note: Samsung is using different versions of the binary driver and installer script for different locales and printers; you probably need one fairly specific to your printer, but your mileage may vary, as switching from a more-or-less consistent framework to multiple releases seems to have reduced Samsung's file packaging reliability."

A while back, I was helping a user install a printer and after many tries he/she asked where I was downloading The Unified Driver from. I am working out of UK, using Isle of Man server. The user was using Chinese Samsung site so he/she downloaded from UK and had instant success. Since then I have tried downloading from different Samsung sites but I am unable to generate any errors in my installations. For me, (ver 3.00.37) is fantastic - download, open terminal, change directory, run sudo ./install.sh - perfect every time (So far!)
Many thanks for the post, I'm trying to find something similar for logitech quickcam communicate stx!!

---

### Post by truthfatal on 2009-04-14
Fantastic directions.  I just managed to install my SCX-4300 on my boyfriend(truthfatal)'s computer, after he had kind of tried to but given up. As a mac user with a broken power adapter, who desperately needs to print her art history slides for her final exam on Thursday, I thank you profusely.

---

### Post by vyvee on 2009-04-25
I have just installed the latest version 3.xx (3.00.37) driver on Ubuntu 9.04 (final), for my Fuji Xerox WorkCentre PE220 printer (~= Samsung SCX-4521). I have to say that it's **very easy** to install the driver now... just works out-of-box! The steps involved are:

**Step 1: Prepare the Driver**
Untar the tarball:

$ tar zxf UnifiedLinuxDriver.tar.gz

**Step 2: Run the Installer with Root Privilege**

$ cd cdroot
$ sudo ./autorun

This is simple. The installer will gently prompt you to run the installer with root privileges if you don't specify 'sudo'.

Simply follow the instructions in the graphical installer:
[LIST=1]
[*] Add users you allow to access the printer into the lp group. (To add future users, simply re-run the installer, use the 'Users and Groups' administration utility, or simply use the adduser command.)
[*] Select 'Samsung SCX-4x21 Series' for this printer model
[*] Test to print and it should work!
[/LIST]

For details (including a list of past problems): [http://www.vyvy.org/main/en/node/146](http://www.vyvy.org/main/en/node/146)

---

### Post by tweedledee on 2009-04-26
Question for anyone who has installed the version 3 driver: have you tried/managed to UNinstall it?  I was doing some testing, and managed to end up with a broken v2 and v3 at the same time.  I need to clean my system and start over with this, but as best as I can tell, the uninstaller is broken.

I've also determined that the major difference in all the installer scripts just has to do with what language and printer the installer tries to work with by default; since those often don't work, I don't think the variations in the installer script actually matter.

I'm going to do some more testing as time allows the next couple of weeks, mainly to determine how well the v3 driver works under various conditions and how many old bugs/issues still remain.  If the uninstall issues persist, and since I'll basically have worked through every step of the installer by that point, I may just go ahead and package a .deb for the installation.  At the very least, I will overhaul the main instructions to match the current status of the driver more closely.

If anyone has insight/experience with the install/uninstall/upgrade from v2 to v3 processes, or knows of significant differences in the install scripts beyond what I've determined, please share.

Also, as I do not have a MFP printer and so can't test scanning, can anyone enlighten me as to how useful the Samsung Unified Driver Configurator actually is?

---

### Post by yahs on 2009-04-26
Just seen your latest post so I thought I'd test the uninstall feature.

My main Ubuntu is 8.04.2 though I have other copies on different partitions. Clicking on the uninstall option from the Samsung Unified Driver generated a message that I needed supervisor privileges to run program. So I opened a terminal changed to this directory /opt/Samsung/mfp/uninstall and ran the command sudo ./uninstall.sh.

Surprise, suprise - GUI screen appeared asking if I wanted to uninstall, said yes and off it went. As far as I can tell everything has disappeared except a menu item in Other which reads Uninstall Samsung Unified Driver and clicking on it gives the error message
Could not launch menu item - Failed to execute child process "/opt/Samsung/mfp/uninstall/uninstall.sh" (No such file or directory). The Samsung Directory under opt has definitely gone and SCX-4100 has gone from System, Administration, Printing.  

The Samsung Unified Driver Configurator allows you to do a scan without needing any other program, such as Xsane. Other than that, you can check and change your printer settings, port settings and print a Samsung test page rather than the Ubuntu test page.

I'm in complete agreement with previous post from vyvee  - ver 3.00.37 works near perfectly. I have completed successful installations of my SCX-4100 on Hardy 8.04.1 and 8.04.2, Intrepid and Jaunty.

---

### Post by excbuntu on 2009-04-26
my ML-2850ND is missing the envelope size 10 in the 'paper size' of the printer properties. please help.

---

### Post by vyvee on 2009-04-27
Hi tweedledee,
I do not encounter the problem you face, as I reinstall my entire / before installing new Ubuntu and the driver version 3.xx (I still have my /home intact!). However I checked the uninstaller of version 2.xx before, and found that the installer of version 2.xx does not clean at least the following files:

/usr/lib/libstdc++-3-libc6.2-2-2.10.0.so
/usr/lib/libstdc++-libc6.2-2.so.3
/usr/lib/libtiff.so.3.6.1
/usr/lib/libtiff.so.3

These files are installed by install.sh when it fails to find them on your system. There is no efficient way to find out if these libraries are still required by other programs, so the uninstaller just leaves them there. (If the installer uses Debian package management then it's another story, but it doesn't.)  Such files that may be installed but will not be removed are packaged in ~/cdroot/Linux/noarch/lib*.tar.gz.

Hope that this can help you in fixing your problem.

---

### Post by braigetori on 2009-04-27
> **w4llet said:**
> Worked like a glove for me.

You can add ML-1630w Printer in your list.

Wireless Printer working like a charm (printer is wireless connected to a wireless router and I have several computers (Linux and windows as well) sharing the printer via wifi/router.

And you were right: I have a monochrome laser printer. Instalation of this drive wasnt necessary. But, following your steps provide me Smart Panel in linux.

Thanks!

:D

u can add the ML-1710 to the list. worked great... cheers !

;b


---------- 

oh.. problems did occur. the driver messed up the apt updates, and the driver proved to be a royal pain to un-install. but the problems were fixed: [http://ubuntuforums.org/showthread.php?p=7161815](http://ubuntuforums.org/showthread.php?p=7161815)

laters

;b

---

### Post by tweedledee on 2009-05-03
> **excbuntu said:**
> my ML-2850ND is missing the envelope size 10 in the 'paper size' of the printer properties. please help.

Which printer driver are you using?  Do you have other printers installed that can see this size (e.g., PDF printer?)?

---

### Post by tweedledee on 2009-05-03
vyvee and yahs - thanks for the input.  Even after extensively cleaning my system, I still can't run the uninstall gui, I get an error about conflicting qt libraries.  I've given up trying to resolve the issue and have finally worked through everything that the installer does.  It's actually a lot scary what the v2 installer does, the v3 is not so bad but it still puts a lot of garbage on the system and takes over CUPS pretty severely.  (In fact, simply purging the Samsung driver manually but missing some of the key symlinks will result in a system that is unable to print from most programs.)  There are also still some major permission issues, although not nearly as bad as when the v2 installer was setuid-ing lots of programs.  Neither uninstaller cleans out everything, although most of the remaining garbage is unimportant.  And there are still problems with the way Samsung deals with the parallel port.

I have mostly everything ready to go to make .debs, but it may be next weekend before I get to finishing them (there are some install/remove script issues that I have to work through to get them working correctly).  I will also update the main post with a breakdown of how to completely clean the driver off of a system.  My intent with the .debs is to a) allow for a way to cleanly uninstall, and b) fix a number of the issues with Samsung's approach to installing.  They will also have the side effect of being much smaller, since much of the download size from Samsung is related only to the installer, plus the need for dual-architecture in a single file.

---

### Post by alex777 on 2009-05-05
Hello guys! I need some help.

I have installed the Samsung Unified Printer Driver all-right, but the installation script has automatically chosen the wrong model: I have a WorkCentre PE220 (which is very similar to Samsung SCX-4521F: [http://www.vyvy.org/main/node/146](http://www.vyvy.org/main/node/146)), but the script has automatically configured CLP-300splc (which of course doesn't work).

The problem is:
- I was unable to choose the model during installation (it was a gui installation, and there wasn't such a screen at all);
- I can't change the driver in Samsung Unified Driver Configurator in the tab 'Printer Properties -> Drivers' (I can only browse through the list of models, since the buttons 'Ok' and 'Apply' are turned off);
- and finally I can't uninstall the Samsung Unified Printer Driver to try a fresh installation - I get the following error:
Failed to load widget from </home/alex/Documents/Downloads/Printer/Samsung/cdroot/Linux/i386/share/ui/uninstalldialogbase.ui>
QMutex::unlock: unlock from different thread than locker
                was locked by 0, unlock attempt from -1223518464

So here I am stuck with this beautiful driver which was supposed to make my life much easier :-)

---

### Post by tweedledee on 2009-05-05
> **alex777 said:**
> Hello guys! I need some help.

You should be able to add the printer you need through the Gnome (or KDE or whatever) standard print interface, without using the Samsung tool at all.

Your uninstall error is one I've seen, but haven't been able to identify the cause of; I think it has to do with a particular combination of QT libraries being installed.  I'm assuming from the error that you installed the version 3 driver.  Did you have an older version installed at any point?  And did you try to run the uninstall from the /opt/Samsung/mfp/uninstall folder instead of the cdroot folder?

---

### Post by mrdiego on 2009-05-15
I have the SCX 4521F Printer. In Jaunty (9.04) the driver is found and installed automaticly by the system. But Xsane don't work with and without "sudo". No scanning already. If Gusty, Hardy, ... always the same problem and differents solutions. :-/

But:

"sudo sane-find-scanner" gives me:

found USB scanner (vendor=0x04e8 [Samsung], product=0x3419 [SCX-4x21 Series]) at libusb:002:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

How I get it run now with JAUNTY? :)

---

### Post by tweedledee on 2009-05-15
> **mrdiego said:**
> How I get it run now with JAUNTY? :)

Hold on what will hopefully be < 24 hours, and possibly only 2-3.  At the moment I am in the process of finishing a complete rewrite of the guide and finalizing a repository to distribute .debs, which will greatly simplify this whole mess.  Although I didn't know that Jaunty automatically installs the printer, and will slightly change what I'm writing.

---

### Post by mrdiego on 2009-05-15
Oh ... a quick answer. :)

Yes. Only turn on the Printer. A window pops up and looks for a driver. Than it downloaded something and installed it. SCX-4100 was the name. It ask you if you want print a test-page. Clicked on yes and it was printing fine. ;)

But XSane already (like in Gusty, Hardy, Intrepid) don't find a Scanner and aport. :(

The earlier releases had solutions what made XSane run. But the HowTo isn't compatible with Jaunty, because things haved changed.

But it's fine you have a solution and you are going to publish it soon.
I stay tuned ... ;)

mrdiego

---

### Post by tweedledee on 2009-05-16
> **mrdiego said:**
> But it's fine you have a solution and you are going to publish it soon.

Finally have everything up.  You can see the completely new original post, and should scan through it, but I think you probably want to try approach IId.

---

### Post by tweedledee on 2009-05-16
For anyone following this who is interested: I have built a repository of .debs for the Samsung driver: [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/).  Using those basically eliminates all problems with install/uninstall process.  The driver bits themselves are the same, so should work as well (or as poorly).

Doing this took far longer than I expected, partly because I had to spend many hours working through exactly what the Samsung binaries were doing, and fighting with incredibly out-of-date path expectations used when they were compiled.  If I hadn't already been a strong supporter of open source, simply so I could recompile the binaries in a sane manner, I would be now.

I will provide what support I can for the packages, and the standard Samsung installer.  As of this post, I have tested the repository and packages on four computers, both i386 and AMD64.  However, alll are running Debian Testing, so please share how well they work for other systems.  They **should** work, but I can't promise anything.

---

### Post by mrdiego on 2009-05-16
Thank you :D :D :D

It's great. I included your repositories and your key. Installed the four packages (I choosed "samsung ... -scanner") and XSane works like a charme after it. :)

I don't now which driver do the job for printing - footmatic or your samsung...-driver from your package, but it's printing good like always. But the best notice is, that finally I can scan without any trouble ... only install your packages! :D

*You made my day* Thanks ...
mrdiego

---

### Post by tweedledee on 2009-05-16
> **mrdiego said:**
> It's great. I included your repositories and your key. Installed the four packages (I choosed "samsung ... -scanner") and XSane works like a charme after it. :)

Great, glad I could help.  The print functions are still being controlled by foomatic in your setup, unless you explicitly enable the CUPS/Samsung configuration.

---

### Post by mrdiego on 2009-05-16
> *snip* The print functions are still being controlled by foomatic in your setup, unless you explicitly enable the CUPS/Samsung configuration.

I think I don't need it. But maybe a little HowTo for it would be interesting. Only if not to complicate ...
This would be interesting for other peoples and me for try out if I have one day something of time. ;)

Cheers

---

### Post by demarshall on 2009-05-17
tweedledee, please give us your URL again.

Thanks

---

### Post by gluxoid on 2009-05-17
Upgrading to Jaunty broke the Samsung stuff.

Great job for making the .deb packages!

---

### Post by tweedledee on 2009-05-17
> **mrdiego said:**
> I think I don't need it. But maybe a little HowTo for it would be interesting. Only if not to complicate ...
This would be interesting for other peoples and me for try out if I have one day something of time. ;)

Cheers

All you'd have to do to switch drivers at this point would be to add the printer using the CUPS interface (through the normal system menus); you could even leave the foomatic simultaneously configured as long as you called the CUPS/Samsung one something different.

---

### Post by tweedledee on 2009-05-17
> **demarshall said:**
> tweedledee, please give us your URL again.

Thanks

I meant to include it in the post above, I have added it now.  It's also in the 1st post for this thread.  And also in this one: [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/).

---

### Post by mrdiego on 2009-05-17
> **tweedledee said:**
> All you'd have to do to switch drivers at this point would be to add the printer using the CUPS interface (through the normal system menus); you could even leave the foomatic simultaneously configured as long as you called the CUPS/Samsung one something different.

mhh, sounds simple, but I haven't any idea what you mean. :) Where is the CUPS interface? Maybe a screeny of this GUI would be more clear. ;)

The only what I saw was in change driver. So you can choose now two times the same driver. But one of them is marked with "(recommended)". ;)

Cheers

---

### Post by pPrdrm on 2009-05-18
I tried your debs and they work fine. The only problem I have left now is that I can't make the smartpanel utility to work with my printer. It's a CLP-300 USB only model. I've managed to install it (short of) after modifing the first line of the install.sh script from "**#!/bin/sh**" to "**#!/bin/bash**". During install it gave me these info:
> Installing...
Shutting down smartpanel: 
F   UID   PID  PPID PRI  NI    VSZ   RSS WCHAN  STAT TTY        TIME COMMAND
F   UID   PID  PPID PRI  NI    VSZ   RSS WCHAN  STAT TTY        TIME COMMAND
0     0  1641     1  20   0   3436  1356 msgrcv Ss   ?          0:00 /opt/Samsung/SmartPanel/bin/s
done
awk: cmd. line:1: { if ($3 == 0 || ($3 >= 100
awk: cmd. line:1:                            ^ unexpected newline or end of string
/home/user/cdroot/Linux/smartpanel/install.sh: line 344: /usr/lib/menu/Samsung_SM: No such file or directory
/home/user/cdroot/Linux/smartpanel/install.sh: line 348: /usr/lib/menu/Samsung_SM: No such file or directory
/home/user/cdroot/Linux/smartpanel/install.sh: line 348: /usr/lib/menu/Samsung_SM: No such file or directory
smartpanel (ver.1.01.73) has been installed successfully in /opt/Samsung/SmartPanel/
--------------------------------------------------------------------------------
starting smartpanel...

So I'm not sure if the installation went OK.
And when I run it, it says "**USB Printer status is not available**". I really want to know how much toner is left when I am printing and when it's time to order new toner. I wish there was a deb for smartpanel also. :-(

---

### Post by tweedledee on 2009-05-18
> **mrdiego said:**
> mhh, sounds simple, but I haven't any idea what you mean. :) Where is the CUPS interface? Maybe a screeny of this GUI would be more clear. ;)

The only what I saw was in change driver. So you can choose now two times the same driver. But one of them is marked with "(recommended)". ;)

Cheers

The CUPS interface (assuming you are using Gnome) is on the System -> Adminstration menu as "Printing", as opposed to the Foomatic interface (which on my Debian system is on the System Tools menu as "Printers" but could be elsewhere).

On my system  (which has a slightly older version of CUPS but same version of Foomatic as Jaunty) and prior to installing the Samsung drivers, I have to use the Foomatic interface to install/configure the CLP-, CLX-, and SCX- printers; CUPS only recognizes the ML- series.

After installing the Samsung drivers, I can see and configure all the Samsung printers through the CUPS setup.  When adding a printer through CUPS, the Foomatic drivers have "foomatic" somewhere in the printer driver name, whereas the Samsung drivers do not.

The fact that there are two drivers for many Samsung printers (as there is for my CLP-550N), one of which is marked "recommended", is something I haven't figured out; as near as I can tell, the two are identical if the only difference is the "recommended" flag.  I've played with it some, enough to know that there's no functional difference for my printer.  Both are associated with the Samung driver.

Through Foomatic, I don't believe the Samsung drivers ever appear, and all drivers listed there are strictly Foomatic.  However, I've not spent a lot of time with Foomatic, since it seems to help a lot with auto-configuration of USB connected printers but can otherwise be a pain.  Since my printer is network, I just use CUPS.

---

### Post by tweedledee on 2009-05-18
> **pPrdrm said:**
> I tried your debs and they work fine. The only problem I have left now is that I can't make the smartpanel utility to work with my printer. It's a CLP-300 USB only model. I've managed to install it (short of) after modifing the first line of the install.sh script from "**#!/bin/sh**" to "**#!/bin/bash**". During install it gave me these info:

So I'm not sure if the installation went OK.
And when I run it, it says "**USB Printer status is not available**". I really want to know how much toner is left when I am printing and when it's time to order new toner. I wish there was a deb for smartpanel also. :-(

My guess is that your installation went fine, the Samsung installers tend to want to write lots of menu files in non-existent locations, but that isn't a problem.

I will take another look at this, and see if there is some reasonable way to package it.  The initial problem I encountered was that, whereas the driver is merely decorated differently for each printer, there are real differences in the Smart Panel download for different printers.  If I poke around and it doesn't look too complex, I can probably put something together.  But it will be a couple of weeks before I have enough time to look at seriously; depending on packaging complexity (assuming it is reasonable to package), it could be another week or two after that before I get it together.  I'm also limited because my printer doesn't work with the Smart Panel, so I can't actually test anything; on the other hand, that's also true for scanning, and I apparently put that together correctly.

I'll let you know after I take a look.

---

### Post by demarshall on 2009-05-20
I followed the repository instructions on your web site tweedledee <http://www-personal.umich.edu/~tjwatt/suldr/> but the files (samsungmfp-*) that you say will then be available are not.

What should I do?

I have a Samsung SCX-4521F and have the configurator installed but have never been able to see the scanner there. Instead I see my TV tuner card.  :-(

---

### Post by tweedledee on 2009-05-21
> **demarshall said:**
> I followed the repository instructions on your web site tweedledee <http://www-personal.umich.edu/~tjwatt/suldr/> but the files (samsungmfp-*) that you say will then be available are not.

What should I do?

I have a Samsung SCX-4521F and have the configurator installed but have never been able to see the scanner there. Instead I see my TV tuner card.  :-(

I'm assuming that you refreshed the repository and did not receive any errors.  If that's wrong, let me know.  Otherwise, please post the output of the following two commands:
```
cat /etc/apt/sources.list
sudo apt-get -s install samsungmfp-conifgurator-qt3
```
The apt-get command will just simulate the installation, it won't actually install anything.

---

### Post by demarshall on 2009-05-22
> **tweedledee said:**
> I'm assuming that you refreshed the repository and did not receive any errors.  If that's wrong, let me know.  Otherwise, please post the output of the following two commands:
```
cat /etc/apt/sources.list
sudo apt-get -s install samsungmfp-conifgurator-qt3
```
The apt-get command will just simulate the installation, it won't actually install anything.

david@Dayspring-Computer-Educational-Services:~$ cat /etc/apt/sources.list
# deb cdrom:[Kubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.1)]/ intrepid main restricted                                                               
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to       
# newer versions of the distribution.                                           

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any  
## review or updates from the Ubuntu security team.                        
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty universe                   
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty universe               
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates universe           
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates universe       

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in      
## multiverse WILL NOT receive any review or updates from the Ubuntu        
## security team.                                                           
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty multiverse                  
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty multiverse              
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse          
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricteduniverse multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-proposed restricted main multiverse universe
deb [http://le-web.org/repository](http://le-web.org/repository) stable main
deb [http://www-personal.umich.edu/~tjwatt/suldr/](http://www-personal.umich.edu/~tjwatt/suldr/) debian extra
david@Dayspring-Computer-Educational-Services:~$ sudo apt-get -s install samsungmfp-conifgurator-qt3
[sudo] password for david:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package samsungmfp-conifgurator-qt3
david@Dayspring-Computer-Educational-Services:~$

---

### Post by tweedledee on 2009-05-22
> **demarshall said:**
> E: Couldn't find package samsungmfp-conifgurator-qt3

Okay, try this ```
sudo apt-get update | grep umich
``` and post any output.

---

### Post by demarshall on 2009-05-25
> **tweedledee said:**
> Okay, try this ```
sudo apt-get update | grep umich
``` and post any output.

david@Dayspring-Computer-Educational-Services:~$ sudo apt-get update | grep umich
[sudo] password for david:
Hit [http://www-personal.umich.edu](http://www-personal.umich.edu) debian Release.gpg
Ign [http://www-personal.umich.edu](http://www-personal.umich.edu) debian/extra Translation-en_CA
Hit [http://www-personal.umich.edu](http://www-personal.umich.edu) debian Release
Ign [http://www-personal.umich.edu](http://www-personal.umich.edu) debian/extra Packages
Hit [http://www-personal.umich.edu](http://www-personal.umich.edu) debian/extra Packages
david@Dayspring-Computer-Educational-Services:~$

---

### Post by dungcs on 2009-05-25
Can anybody help me to install driver for Samsung Receipt Printer SRP-275CP in Ubuntu Desktop 8.04?

Thank you!

---

### Post by tweedledee on 2009-05-25
> **demarshall said:**
> david@Dayspring-Computer-Educational-Services:~$ sudo apt-get update | grep umich

I'm not sure what to make of this.  Your system is obviously talked to the repository and obtaining the package lists, but something in your configuration must indicate to apt/dpkg that my packages are not installable on your system, so it simply doesn't "find" them at all.  If it were just a matter of dependencies (which it shouldn't be anyway), you'd get a different error.

You can try posting the output of```
apt-config dump
```and I'll look to see if there's something obvious set (such as wrong architecture, limited package priority, or similar), but I'd expect that if anything were obviously wrong, you'd have trouble with other repositories as well.  Alternatively, if you have the files```
/etc/apt/apt.conf
/etc/apt/preferences
``` you could try renaming those and seeing it if works (after another "apt-get update"), in case some there's some other customized configuration interfering.

Another option is to download the files locally, set up a local repository, and try installing them that way.  If you want to try this, go to [http://www-personal.umich.edu/~tjwatt/suldr/dists/debian/extra/](http://www-personal.umich.edu/~tjwatt/suldr/dists/debian/extra/) and the appropriate architecture (based on your sources.list, amd64), then download all the .debs to a local (empty) folder on your computer.  In that folder, execute```
dpkg-scanpackages binary | gzip -9c > Packages.gz
```, then add a repository line to your sources.list of ```
deb file:///<complete path to folder with debs>
```and run "apt-get update" to access it.  If you have gdebi installed, you can also open the download debs with it and see what errors it comes up with.

---

### Post by tweedledee on 2009-05-25
> **dungcs said:**
> Can anybody help me to install driver for Samsung Receipt Printer SRP-275CP in Ubuntu Desktop 8.04?

Thank you!

As far as I know, this printer (really manufactured by Bixolon, despite the branding) is not supported for Linux at all.  Bixolon has recently introduced a Linux driver for precisely one of their printers, and I don't see any evidence that there are other foomatic or CUPS options for these printers.  Not knowing any of the details of how the printer works, I don't want to recommend trying random drivers in the hopes that something works.

---

### Post by Pierre31 on 2009-05-26
Hi,

I'm using Ubuntu 9.04 x86_64 and Samsung SCX-4300

First thanks for your great job it was really handy.

I've noticed however a problem in the Samsung Unified Driver Configurator (data) package concerning libpng. (Hope this hasn't been yet noticed).
Problem is that it install with a symbolic link /usr/lib/libpng.so.3 linking to a non existing libpng.so library.
I fix this by installing   Samsung Unified Driver Configurator (data) package and after
cd /usr/lib; sudo ln -sf  libpng12.so.0 libpng.so.3

I noticed that a package exist for libpng.so.3 that symlink with libpng12.so.0. Maybe we could remove the libpng.so.3 from .deb and add a dependancy to libpng3 ?

---

### Post by tweedledee on 2009-05-26
> **Pierre31 said:**
> I noticed that a package exist for libpng.so.3 that symlink with libpng12.so.0. Maybe we could remove the libpng.so.3 from .deb and add a dependancy to libpng3 ?

Ask and ye shall receive.

Packages updated to version 3.00.37-2, the only change being directly depending on libpng3 rather than symlinking within my packages.  There is a slight difference in the way the libpng12 and libpng3 packages are prepared for Ubuntu and Debian, leading to the problem you noticed (which wasn't an issue for me), but this should work for both.

---

### Post by demarshall on 2009-05-27
> **tweedledee said:**
> You can try posting the output of```
apt-config dump
```and I'll look to see if there's something obvious set (such as wrong architecture, limited package priority, or similar), but I'd expect that if anything were obviously wrong, you'd have trouble with other repositories as well.  Alternatively, if you have the files```
/etc/apt/apt.conf
/etc/apt/preferences
``` you could try renaming those and seeing it if works (after another "apt-get update"), in case some there's some other customized configuration interfering.

Thanks tweedledee

david@Dayspring-Computer-Educational-Services:~$ apt-config dump                
APT "";                                                                         
APT::Architecture "amd64";                                                      
APT::Build-Essential "";                                                        
APT::Build-Essential:: "build-essential";                                       
APT::Install-Recommends "1";                                                    
APT::Install-Suggests "0";                                                      
APT::Acquire "";                                                                
APT::Acquire::Translation "environment";                                        
APT::Authentication "";                                                         
APT::Authentication::TrustCDROM "true";                                         
APT::NeverAutoRemove "";                                                        
APT::NeverAutoRemove:: "^linux-firmware$";                                      
APT::NeverAutoRemove:: "^linux-image.*";                                        
APT::NeverAutoRemove:: "^linux-restricted-modules.*";                           
APT::NeverAutoRemove:: "^linux-ubuntu-modules-.*";                              
APT::Never-MarkAuto-Sections "";                                                
APT::Never-MarkAuto-Sections:: "metapackages";                                  
APT::Never-MarkAuto-Sections:: "restricted/metapackages";                       
APT::Never-MarkAuto-Sections:: "universe/metapackages";                         
APT::Never-MarkAuto-Sections:: "multiverse/metapackages";                       
APT::Periodic "";                                                               
APT::Periodic::Update-Package-Lists "1";                                        
APT::Periodic::Download-Upgradeable-Packages "0";                               
APT::Periodic::AutocleanInterval "0";                                           
APT::Periodic::Unattended-Upgrade "0";                                          
APT::Update "";                                                                 
APT::Update::Post-Invoke-Success "";                                            
APT::Update::Post-Invoke-Success:: "touch /var/lib/apt/periodic/update-success-stamp 2>/dev/null || true";                                                      
APT::Update::Post-Invoke-Success:: "(sleep 60; /usr/bin/dbus-send --system --dest=org.freedesktop.PackageKit --type=method_call /org/freedesktop/PackageKit org.freedesktop.PackageKit.StateHasChanged string:'cache-update')&";                
APT::Archives "";                                                               
APT::Archives::MaxAge "30";                                                     
APT::Archives::MinAge "2";                                                      
APT::Archives::MaxSize "500";                                                   
Dir "/";
Dir::State "var/lib/apt/";
Dir::State::lists "lists/";
Dir::State::cdroms "cdroms.list";
Dir::State::mirrors "mirrors/";
Dir::State::userstatus "status.user";
Dir::State::status "/var/lib/dpkg/status";
Dir::Cache "var/cache/apt/";
Dir::Cache::archives "archives/";
Dir::Cache::srcpkgcache "srcpkgcache.bin";
Dir::Cache::pkgcache "pkgcache.bin";
Dir::Etc "etc/apt/";
Dir::Etc::sourcelist "sources.list";
Dir::Etc::sourceparts "sources.list.d";
Dir::Etc::vendorlist "vendors.list";
Dir::Etc::vendorparts "vendors.list.d";
Dir::Etc::main "apt.conf";
Dir::Etc::parts "apt.conf.d";
Dir::Etc::preferences "preferences";
Dir::Bin "";
Dir::Bin::methods "/usr/lib/apt/methods";
Dir::Bin::dpkg "/usr/bin/dpkg";
Dir::Log "var/log/apt";
Dir::Log::Terminal "term.log";
aptitude "";
aptitude::Keep-Unused-Pattern "^linux-image.*$ | ^linux-restricted-modules.*$ |^linux-ubuntu-modules.*$";
aptitude::Get-Root-Command "sudo:/usr/bin/sudo";
Unattended-Upgrade "";
Unattended-Upgrade::Allowed-Origins "";
Unattended-Upgrade::Allowed-Origins:: "Ubuntu jaunty-security";
DPkg "";
DPkg::Pre-Install-Pkgs "";
DPkg::Pre-Install-Pkgs:: "/usr/sbin/dpkg-preconfigure --apt || true";
DPkg::Post-Invoke "";
DPkg::Post-Invoke:: "if [ -d /var/lib/update-notifier ]; then touch /var/lib/update-notifier/dpkg-run-stamp; fi; if [ -e /var/run/updates-available ]; then echo > /var/run/updates-available; fi ";

---

### Post by tweedledee on 2009-05-27
> **demarshall said:**
> david@Dayspring-Computer-Educational-Services:~$ apt-config dump

Looks okay to me.  I'm pretty much at a loss to explain your problem.  Other than trying a local repository as described in my previous post, the only thing I can think of is that something in one of your other repositories is interfering.  You could try temporarily disabling most or all of your other repositories (comment them out in sources.list or turn them off in Synaptic), then refresh your listings and see if the packages appear.

---

### Post by tweedledee on 2009-05-27
> **pPrdrm said:**
> I wish there was a deb for smartpanel also. :-(

After looking into this some more, I will not be producing a package for the smart panel.  I would actually recommend that everyone stay away from it, as the installer creates a large number of security holes in your system, and turns out to be nearly as bad as the v2 unified drivers.  I have updated the original post to reflect this, and provided details on the repository webpage.

If Samsung updates the Smart Panel to avoid the setuid issues as they did the drivers, I may revisit the issue, but I doubt that will happen any time soon.

---

### Post by demarshall on 2009-05-30
I just went to Synaptic to turn the other repositories off and noticed that the repository key for your server didn't show as installed so I installed it. Now your packages are showing up in Synaptic. I'm sure that I installed it from the command line some time ago.

---

### Post by tweedledee on 2009-05-30
> **demarshall said:**
> I just went to Synaptic to turn the other repositories off and noticed that the repository key for your server didn't show as installed so I installed it. Now your packages are showing up in Synaptic. I'm sure that I installed it from the command line some time ago.

That is a odd, because you should have been getting authentication errors rather than complete failures.  But I'm glad it is now working for you.

---

### Post by pPrdrm on 2009-06-01
> **tweedledee said:**
> ...
If Samsung updates the Smart Panel to avoid the setuid issues as they did the drivers, I may revisit the issue, but I doubt that will happen any time soon.

That's too bad. Thanks for taking the time to look into this anyway and thank you for the drivers debs. You've really made my life with my printer a lot easier.

---

### Post by MarcusCarabas on 2009-06-05
Thanks tweedledee for this How-To, for packaging the drivers and for taking the time to answer questions and such. 

My Samsung ML 2240 monochrome laser printer worked "out of the box" with Gutsy, but died when I upgraded to Intrepid. I was able to get it up and running again only because of this How-to. I don't think I would have managed to make things work without your guide. So once again, sincere thanks.

:)
MarcusCarabas.

---

### Post by owl700 on 2009-06-06
Thanks tweedledee my clp-315 start to print now :)

---

### Post by sabmo on 2009-06-08
Just wanted to say thanks to whoever maintains the Samsung unified debian packages.

I just bought the Samsung ML-2240 Series monochrome laser printer.

Installed the debian packages and then added the printer using the printer wizard and everything worked right out of the box.

Good show!

---

### Post by metiu on 2009-07-14
Hi I'm on 9.04 with a brand new SCX 4300.
I installed the Unified Linux Driver with the provided installer and everything worked fine out of the box.

However, I get vertical thin white lines all over the scanned pictures, particularly in dark areas. I tried scanning in Windows Vista and the lines there are almost invisible if I don't enlarge the picture a lot, so it seems to be a driver issue.

---

### Post by tweedledee on 2009-07-16
> **metiu said:**
> Hi I'm on 9.04 with a brand new SCX 4300.
I installed the Unified Linux Driver with the provided installer and everything worked fine out of the box.

However, I get vertical thin white lines all over the scanned pictures, particularly in dark areas. I tried scanning in Windows Vista and the lines there are almost invisible if I don't enlarge the picture a lot, so it seems to be a driver issue.

Which version of the driver did you install?  If you used the one on the provided CD, it almost certainly is not the most current, so updating to a more recent driver may help if the driver is at fault.

---

### Post by coady on 2009-07-20
> **sabmo said:**
> I just bought the Samsung ML-2240 Series monochrome laser printer.

Installed the debian packages and then added the printer using the printer wizard and everything worked right out of the box.
Hi,
I am running this printer under Hardy 8.04. It would not print initially, but by selecting a different foomatic driver than the recommended one (automatically setup by CUPS), it does work 'out of the box'.

I selected "Samsung MML-2250 Foomatic/gdi [en]" instead of the recommended driver and it works fine. Note I did not need to go through the steps of the HOWTO but just used the basic CUPS system.

I hope this is useful to others...

---

### Post by AgenticState on 2009-07-21
Hi tweedledee,

I'm trying to get the scanner part of an SCX-4200 to work on Kubuntu 9.04 (printing is fine with SPLIX).

I've added your repo and key and installed the samsungmfp-scanner package along with its dependencies. Running scanimage -L shows the scanner and xsane finds it too but when I try to scan from xsane it gives the error "Error during read: Error during device I/O". This happens both as a normal user and as root.

Any idea what I am doing wrong?

Dylan.

---

### Post by Marcelo Fernández on 2009-07-23
I have the same problem but with Samsung's official drivers, and I got it working temporarily removing the USB 2.0 (EHCI) module to make scan working.

To do this, type into a terminal: "sudo rmmod ehci_hcd" and after that, try to scan again.

---

### Post by wstay on 2009-07-24
Can someone please explain how to install the GPG key for the repository related to my Samsung printer?
I click on a link to download and installthe GPG key. But what I get is as follow:

 -----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.9 (GNU/Linux)
mQGiBEoOI1QRBADrv7Qk8VmJRhz7IM4ney/U7lcXYjlvKDxphfXkJxcjOxSOaJXt
LO09GirJSD/vl/3rJ5KY1i8aln4Ji7ZsxEV9mdYSpXKmTIOZpW7Jp7kQE5fxehfX
hvbjTeDF2ZSGDMVPG6m0wffmXac+OwK/cI28s9dK7RH+O0dk1WQ3vMV7vwCgz6hq
OPgOxLqqaMFknqaYy71OflsEALAebD9KOTvIEtqiV+JFpehzTZM/zJFn0gpx8gLh
KrK4sauAxgBFo+Juhzjcq0zh4bG2jXkfX/Nwlgli9wucp9Yv60W2QACd4yin3574
7/FYElAcuykQCgzqY0cRCD2VPAFJLU4mVWCS4qfWJgLd9JR8zD/BZYLJFdIXHRD+
FxU4A/4leZ/WI1WUv+5g0AO5qDLoxKG7XjR5Wmu3L8STbXqB/XgN/msxogUxoJyc
ccxcMbp8ZqWp4iZ+gHEIyqcpFTC586lFrmtNgiLw+0g4eBSbvkjheHoU6miZXI5E
J6+iMiVw2Z1ma9yxpU4DmjbBcnbPK67GHBMm7hrz/vyvrYefYbQrU2Ftc3VuZyBV
bmlmaWVkIExpbnV4IERyaXZlciBSZXBvc2l0b3J5IEtleYhmBBMRAgAmBQJKDiNU
AhsDBQkFo5qABgsJCAcDAgQVAggDBBYCAwECHgECF4AACgkQ9eMmFuRoEKWMMACd
EvpR0bbt6dapsx0p3kJ/NnT7KRoAnRjIGfA8WkcJk2TpvuendZMQrbAAuQINBEoO
I1QQCADghwFR2w+c2Wy8cgmDkIcN1Sx/fM6U/e0LQbmGpYodvW0xw2oyOBXwDpok
G/TJ02ZbGMM9cGPfflOfztRYJQJ6olS6TMTieIlY/7898j3jEnnzh8P+d71bpH5d
58Rkdffaz6LVZX9vJZYErHlQK09Dgu3FYd0M8C38bpPAGf1CnX4e2LFgnk9TkJWA
ABgLzt6yUiHkcitmXwU8wWSspI7BhFulz6mYFfXdJzwWXTqBPDNl5yQydufnwBnv
42c83owOPitmnS//4nYDIhOFeBHzX2E7kaps0QI3nm5gCsLEwB9nKjb8ojyygAlS
gUUU8oYTjYRd+f/qIjTd0qHjqbOTAAMFB/0SES8+e5T0xm36ZooLdx68HXhSzvWE
EjUoFyuMydAToMI/XXAIZS8jrR7V9VS+51EiSbtVglU/FqjuLO48k4k1vAAp/GgT
7YhALFYyEHSdIF4Fx/NV/p2H9fEW4CQA/zslsLYVl/wrnYEf57j3A1wolFY5G0A+
cwv/RPwU6RysUEQxQWPVqxZ5rHaC2QJ+8QPTrZjkQgEsm+xwKtQ7OFKV05IBs5Cb
s4fF2rPfhyrwDolLbpYAA81lpiRlMY4TtNa+wIXXuJiD4KACdwHib24fZDTioX5Z
GaN/7597HIAb3TjFI0My1JDcYRVwiXdlx1kQ//3IdccyFpb3Fb+EXHdNiE8EGBEC
AA8FAkoOI1QCGwwFCQWjmoAACgkQ9eMmFuRoEKVFjwCeLokkRpcEL9WZmgILwN5r
GBU//IYAniVhb+EnOfIyLmy/d6EzaLai5/RW
=t8A/
-----END PGP PUBLIC KEY BLOCK-----

The problem is how I can get this to install on my Ubuntu system?

---

### Post by wstay on 2009-07-24
> **tweedledee said:**
> Guide to installing Samsung printers & the Unified Linux Driver:
..........
1. Download the driver from Samsung's website and save it to a folder that does not contain any spaces in the path.  For this example I will use ~, but ~/Desktop or similar will also work.

2. Unpack the file, which will create a folder *cdroot*.

3. In a terminal, navigate to the *cdroot* folder and then ```
find . -type d -exec chmod 755 {} \;
``` to ensure that all directories work correctly, frequently the ppd and/or cms directories (under Linux/noarch/at_opt/share) are incorrectly set, which can cause problems when trying to remove the *cdroot* folder.

4. Then, still in *cdroot*, execute: ```
sudo ./autorun
``` or ```
sudo Linux/install.sh
``` to start the graphical installer.



I got to this step and got an error message: root@wstay-desktop:/home/wstay/Desktop/SCX-4725F/UnifiedLinuxDriver/cdroot# ./autorun
Session management error: None of the authentication protocols specified are supported .
But the graphical Unified Linux Driver Installer does appear on screen.
Is it safe to continue with the install?

---

### Post by wstay on 2009-07-25
> Originally Posted by tweedledee  View Post
Guide to installing Samsung printers & the Unified Linux Driver:
..........
1. Download the driver from Samsung's website and save it to a folder that does not contain any spaces in the path. For this example I will use ~, but ~/Desktop or similar will also work.

2. Unpack the file, which will create a folder cdroot.

3. In a terminal, navigate to the cdroot folder and then
Code:

find . -type d -exec chmod 755 {} \;

to ensure that all directories work correctly, frequently the ppd and/or cms directories (under Linux/noarch/at_opt/share) are incorrectly set, which can cause problems when trying to remove the cdroot folder.

4. Then, still in cdroot, execute:
Code:

sudo ./autorun

or
Code:

sudo Linux/install.sh

to start the graphical installer.

Printer model: SAMSUNG MULTIFUNCTION SCX 4725F
Which driver I am using: Unified Linux Driver (ver.3.00.37)
How I installed the driver: Follow the steps you outline in IIc: Use the Samsung Unified Linux Driver repository and  when I cannot find the samsungmfp-* packages corresponding to the Samsung Unified Linux Driver in Synaptic, I switch to using step III: Installing the Samsung Unified Linux Driver directly
How it is connected: USB
The specific problem: When I post the command: sudo Linux/install.sh or /autorun to start the graphical installer I got an    error message - Session management error: None of the authentication protocols specified are supported .
My question is: Is it alright to continue with the install given this error message and the graphical Unified Linux Driver Installer does appear on screen?

On to another qiestion

> .....but the main purpose is distribute of .debs. The .deb packages should work fine in any recent Debian-based distribution (see below). It should also be possible for use alien to install these packages as .rpm or other formats for Fedora, Suse, etc., but I have not attempted to do so. (You can access the .deb files directly to try this here. 

the deb.files I download are just plain text documents and how do I use alien to install these packages as .rpm?

---

### Post by tweedledee on 2009-07-25
> **wstay said:**
> Printer model: SAMSUNG MULTIFUNCTION SCX 4725F
Which driver I am using: Unified Linux Driver (ver.3.00.37)
How I installed the driver: Follow the steps you outline in IIc: Use the Samsung Unified Linux Driver repository and  when I cannot find the samsungmfp-* packages corresponding to the Samsung Unified Linux Driver in Synaptic, I switch to using step III: Installing the Samsung Unified Linux Driver directly

You should be able to see the packages in Synaptic if the repository was added correctly and the package listed refreshed.  If the problem is the gpg key, you may have to right-click and "save as" before running apt-key as described in the first post.  Are you getting any errors when trying to reload the package list in Synaptic?  Try to solve whatever the problem is here first, before trying the Samsung installer.  (And I have no idea what the error you are getting means or if it is a problem.)

> **wstay said:**
> the deb.files I download are just plain text documents and how do I use alien to install these packages as .rpm?

You should not need to use alien, since you seem to be running Ubuntu.  If you download the packages directly because the repository doesn't work for your system, you can just use gdebi (as root, or alternatively dpkg -i on the command line) to install the .debs you downloaded.  The only problem will be that you will have to install in a particular order so that dependencies are satisfied: first the -data package, then the -driver package, then whichever -configurator package you want, if you want it at all.

---

### Post by tweedledee on 2009-07-25
> **Marcelo Fernández said:**
> I have the same problem but with Samsung's official drivers, and I got it working temporarily removing the USB 2.0 (EHCI) module to make scan working.

To do this, type into a terminal: "sudo rmmod ehci_hcd" and after that, try to scan again.

That seems rather odd, but I can't really help troubleshoot this since I don't have a multifunction printer.  I will make a note in the first post about this possible solution.

---

### Post by tweedledee on 2009-07-25
> **coady said:**
> Hi,
I am running this printer under Hardy 8.04. It would not print initially, but by selecting a different foomatic driver than the recommended one (automatically setup by CUPS), it does work 'out of the box'.

I selected "Samsung MML-2250 Foomatic/gdi [en]" instead of the recommended driver and it works fine. Note I did not need to go through the steps of the HOWTO but just used the basic CUPS system.

I hope this is useful to others...

I have added the suggestion to try alternate Foomatic/CUPS drivers when available to the main page.

---

### Post by wstay on 2009-07-26
>  Originally Posted by tweedledee
Guide to installing Samsung printers & the Unified Linux Driver:
You should be able to see the packages in Synaptic if the repository was added correctly and the package listed refreshed. If the problem is the gpg key, you may have to right-click and "save as" before running apt-key as described in the first post. Are you getting any errors when trying to reload the package list in Synaptic? Try to solve whatever the problem is here first, before trying the Samsung installer. (And I have no idea what the error you are getting means or if it is a problem.)

The gpg key I was using before was copy and paste and save into a text file and then added into Synaptic. However, as you pointed out, I use ´save page as´ to save the gpg key from the file menu in firefox and then add to Synaptic and then run the apt-key in the terminal. I can now see the samsungmfp-* packages. However, after installing 6 of the packages, leaving out the last 2 packages (samsungmf-configurator-qt3 and samsungmf-parallel), my printer status remain idle all the time even when I click Test print and Start. I restart the computer and try to Test print again and the problem remains the same. My Samsung Multifunction SCX 4725F printer is switch on all the time when I print.
When I click Test-Check Printer-Start from the Unified Driver configurator, it gives me an error message: Checking Driver .... Failed - Printer Stopped and Can´t Accept Jobs.

Another question is should I enable or disable ´Unsupported Updates (Intrepid Backports)´ in Synaptic for the Samsung Printer Driver?

---

### Post by tweedledee on 2009-07-26
> **wstay said:**
> When I click Test-Check Printer-Start from the Unified Driver configurator, it gives me an error message: Checking Driver .... Failed - Printer Stopped and Can´t Accept Jobs.

It sounds like the Samsung driver may not be in use for the printer.  Have you added the physical printer as a new printer in any printer administration software (Samsung Configurator or the normal Ubuntu tools) and selected the CUPS driver provided by Samsung?  The Samsung drivers would not have "Footmatic" or "gdi" in the description, and there may be several options for your printer that need to be tried.

> **wstay said:**
> Another question is should I enable or disable ´Unsupported Updates (Intrepid Backports)´ in Synaptic for the Samsung Printer Driver?

Backports shouldn't have any effect on this problem, unless there was a problem with the entire CUPS system (which I don't believe to be the case).

---

### Post by wstay on 2009-07-26
> **tweedledee said:**
> It sounds like the Samsung driver may not be in use for the printer.  Have you added the physical printer as a new printer in any printer administration software (Samsung Configurator or the normal Ubuntu tools) and selected the CUPS driver provided by Samsung?  The Samsung drivers would not have "Footmatic" or "gdi" in the description, and there may be several options for your printer that need to be tried.

My computer can find and add the physical printer SCX 4725F in the Unified Driver Configurator. My problem now is how and where can I selecte the CUPS driver provided by Samsung?

---

### Post by tweedledee on 2009-07-26
> **wstay said:**
> My computer can find and add the physical printer SCX 4725F in the Unified Driver Configurator. My problem now is how and where can I selecte the CUPS driver provided by Samsung?

If you select the printer in the Configurator, choose the "Properties" button, and then the "Driver" tab, you can see what driver the printer is using.  The Samsung driver is called "Samsung SCX-4725 Series"; if some other driver is selected, you should probably try changing it to this one.  If that's not the problem, it could be:
a) if you are connected via USB, it may be related to the same USB 2.0 driver issue recently reported for scanning with some printers, in which case you want to try the "modprobe -r ehci_hcd" advice near the bottom of the 1st post.
b) it could also be the particular connection method used.  In the Properties/Connection tab, you can try changing the particular method selected to see if something different helps.
c) if you don't have it installed, the samsungmfp-lpr package, to install the Samsung-specific lpr method, may help to at least get a test page to work.

You can also try running```
lp -d <printer name> <file name>
``` in a terminal, replaincg <printer name> with whatever your installed printer is called (as it appears in the Configurator) and <file name> is the path to something to try printing; this may work even if the test page fails (in which case most programs are probably okay to print), or perhaps generate error messages that will be helpful.

---

### Post by wstay on 2009-07-27
> **tweedledee said:**
> If you select the printer in the Configurator, choose the "Properties" button, and then the "Driver" tab, you can see what driver the printer is using.  The Samsung driver is called "Samsung SCX-4725 Series"; if some other driver is selected, you should probably try changing it to this one.  If that's not the problem, it could be:
a) if you are connected via USB, it may be related to the same USB 2.0 driver issue recently reported for scanning with some printers, in which case you want to try the "modprobe -r ehci_hcd" advice near the bottom of the 1st post.
b) it could also be the particular connection method used.  In the Properties/Connection tab, you can try changing the particular method selected to see if something different helps.
c) if you don't have it installed, the samsungmfp-lpr package, to install the Samsung-specific lpr method, may help to at least get a test page to work.

You can also try running```
lp -d <printer name> <file name>
``` in a terminal, replaincg <printer name> with whatever your installed printer is called (as it appears in the Configurator) and <file name> is the path to something to try printing; this may work even if the test page fails (in which case most programs are probably okay to print), or perhaps generate error messages that will be helpful.


I tried:
wstay@wstay-desktop:~/Desktop$ lp -d SCX-4725-Series testfax
lp: Destination "SCX-4725-Series" is not accepting jobs.
wstay@wstay-desktop:~/Desktop$ 

In Configurator-Properties-Driver Tab, all the Options..tab are grey-out except Samsung SCX-4725 Series.
In Configurator-Properties-Connection Tab, every item ( Parrallel, USB, Network, File) there is grey-out. But when I switch to MFP port control in the Unified Driver Configurator I see that my Printer and Scanner are connected to /dev/mfp4 and Port-type: USB.
I find that my Scanner can scan and I can save the document scanned. The problem is why the selected Samsung SCX-4725 Series (default) Printer, in the Unified Driver Configurator shows a message - Selected printer: Local printer(stopped).

I want to try:
 sudo modprobe -r ehci_hcd
<perform what scanning you need to do>
sudo modprobe ehci_hcd
but do not know how or what command to put into <perform what scanning you need to do>.
I can however use the Unified Driver Configurator - Scanner button - to scan and there is no problem scanning and saving the file scanned.

---

### Post by tweedledee on 2009-07-27
> **wstay said:**
> I tried:
wstay@wstay-desktop:~/Desktop$ lp -d SCX-4725-Series testfax
lp: Destination "SCX-4725-Series" is not accepting jobs.
wstay@wstay-desktop:~/Desktop$ 


Okay, most likely the problem is that the printer is "stopped" (which CUPS sometimes does when printing fails).  You can try either:
a) deleting all printers, then re-adding your printer as you've done previously, to clear that flag, or
b) go to the System -> Administration -> Printing tool, right-click on your printer and select "Edit", go to the Policies tab, and make sure both "Enabled" and "Accepting Jobs" have a check (turned on).  (This assumes you are using Ubuntu rather than K/X/some other version, in which case the printing tool may be different or a on a different menu, but the general idea will be the same.)

If this is the problem, it's not something you can fix in the Configurator (at least not without a bit of a workaround), so you will have to use the standard CUPS tools.  Since scanning is typically the hardest bit to get working, you should be very close to a working printer.

---

### Post by wstay on 2009-07-28
Thanks, tweedledee.
I can now print from an opened file. That is, open a file and click print and choose the printer to print. 
But, why choosing Test button from the Unified Driver Configurator to print a test page won´t print. The message from the lpr gui shows the status as: idle, accepting jobs and it would remains like that as if forever idle, accepting jobs.

---

### Post by tweedledee on 2009-07-28
> **wstay said:**
> Thanks, tweedledee.
I can now print from an opened file. That is, open a file and click print and choose the printer to print. 
But, why choosing Test button from the Unified Driver Configurator to print a test page won´t print. The message from the lpr gui shows the status as: idle, accepting jobs and it would remains like that as if forever idle, accepting jobs.

Glad to hear it's working.  The "idle" status may never change; how useful that status is varies a lot depending on printer manufacturer, specific model, and the particular method a program uses to print.

---

### Post by wstay on 2009-08-01
Hello again tweedledee,
Could you please explain the difference betweem samsungmfp-configurator-qt3 and samsungmfp-configurator-qt4 and which qt (qt3 or qt4) should I use?

---

### Post by tweedledee on 2009-08-01
> **wstay said:**
> Hello again tweedledee,
Could you please explain the difference betweem samsungmfp-configurator-qt3 and samsungmfp-configurator-qt4 and which qt (qt3 or qt4) should I use?

There is no practical difference, they offer exactly the same functions.  The only difference is the visual appearance and which libraries they depend on.  The Qt3 version is older and generally considered not as attractive.  The Qt4 version requires a linux distribution current to within a year or two, so Samsung still provides both; running Ubuntu, it should make no difference.

---

### Post by crystaldart on 2009-08-03
I tried to follow your STEP IV to uninstall the drivers. 

But it shows there is no such file has uninstall.sh.

Is there any other way?

---

### Post by tweedledee on 2009-08-03
> **crystaldart said:**
> I tried to follow your STEP IV to uninstall the drivers. 

But it shows there is no such file has uninstall.sh.

Is there any other way?

Try ```
find /opt/Samsung/ -name uninstall.sh
``` in a terminal to see if the uninstall script is hiding somewhere else.  If not, or if it doesn't work, just follow the later part of part IV of the first post, regarding what to do when uninstall fails (basically, manually remove all the files).  There aren't any other options.

---

### Post by crystaldart on 2009-08-05
No way. I tried to find install.sh as you told me. 

But its showing nothing. 

I re-installed all the samsung drivers from the synaptic Package Manager. 

Still the machines shows '***Printing.......'*** and then nothing happens.

Friends, am really at my ends... its so important for me to get start printing :confused: 
(Obviously :))

Thank you all.

---

### Post by Midahed on 2009-08-05
I have a Samsung CLP-610ND laser printer which was only delivered yesterday.  Before finding your excellent how-to, I'd already installed the Samsung Unified Driver from the CD provided with the printer.  The version information is "Common 3.00.31, Printer 3.00.20, build 128.  It looks like the CD was mastered in April this year.

Given that it looks reasonably recent I thought I'd try to get it working with the software on the CD before uninstalling and trying to follow your how-to.  However I'm confused as to which driver I should pick from the list that's provided by the installation wizard.  There are two for the CLP-610 - one is called "Samsung CLP-610 Series (SPL-C)" and the other is "Samsung CLP-610, 1.1.0"

There's not a clue provided by Samsung as to which one should be used.  I've picked the first one (with 'series' in the name), but what's the other one for?

The second problem I have is that the wizard doesn't find my printer automatically.  It's networked and I've set the printer up with a fixed IP address (the printer works fine from my Windows machine and I can ping it from my Linux box).  I expected the wizard to detect it but clicking the 'search' button fails to find it.  As a result I have to use the 'manual' option but, again, I'm guessing as to what's required.  I've tried setting it to use ipp://10.0.0.54 but the wizard doesn't seem to retain the IP address after I've entered it on the 'ports' page.  The wizard completes OK, but doesn't display the IP address in the configurator's printers page.  Instead, at the bottom it shows:-

Selected printer
Local printer (stopped)
Model: Samsung CLP-610 Series (SPL-C)
URI: ipp://

If I use the configurator's 'test' option to check the driver it says it's OK:-

'CLP610' (Samsung CLP-610 Series (SPL-C)) on ipp://

Checking driver... OK

However if I try to print a test page I get a window saying the printer status is not available and I'm referred to the troubleshooting guide.

So, the questions from this confused Samsung user are:-

Am I picking the right driver
By using ipp:// am I going the right way about setting-up my network printer
Why can I not see the printers IP address anywhere in the configurator
Why does the configurator refer to my printer as 'local' when it isn't

Marks for the Samsung installation software - 7/10
Marks for the Samsung documentation - 3/10

Mike

---

### Post by tweedledee on 2009-08-05
> **crystaldart said:**
> Friends, am really at my ends... its so important for me to get start printing :confused: 
(Obviously :))

Thank you all.

I'll need a lot more information to help you; many problems can give rise to this situation.  Did you install the driver directly from Samsung, via the packages, or both?  What model printer is it?  What is the exact name of the driver you selected to configure it with?  How is it connected?  If it is networked, how did you set that up?  Have you tried both printing a test page and printing an actual document?  Try also the "lp" command given in post 288, and share any output.  Did you configure the printer using the CUPS, foomatic, or Samsung interface?

---

### Post by tweedledee on 2009-08-05
> **Midahed said:**
> Given that it looks reasonably recent I thought I'd try to get it working with the software on the CD before uninstalling and trying to follow your how-to.
Not an unreasonable approach, but that particular version was only distributed by Samsung for about a week or two; I never used it, but suspect it had some bugs, so keep that in mind if you have problems later.

> **Midahed said:**
> So, the questions from this confused Samsung user are:-

Am I picking the right driver
By using ipp:// am I going the right way about setting-up my network printer
Why can I not see the printers IP address anywhere in the configurator
Why does the configurator refer to my printer as 'local' when it isn't
Your driver choice is probably fine.  Most printers end up with two choices, usually the first one listed is okay.  I've actually not seen any practical difference in a couple of trials, but it may vary by printer.  I don't really know why two usually appear, except that one may simply be a link to the other with a different name.

I find lpd to be much reliable with Samsung than ipp, and also much easier to configure (ipp requires an extra step or two to get working right, which I don't immediately recall).  I've never had any luck with autodiscovery of network printers.  I think that extra step, probably something to do with configuring a print queue, is why your IP address won't stick with ipp.

Network printers are often shown as local, non-local usually means that you are accessing a printer explicitly shared by another computer (i.e., not itself networked).  It varies for no apparent reason.

---

### Post by Midahed on 2009-08-05
Thanks, tweedledee, for your quick and comprehensive reply.

As it happens I've just been deleting everything I installed from the Samsung CD and will follow your how-to once I've cleaned up my system.

In the 'manual uninstall' part of your how-to there are the following commands:-

```
find /usr -type f -name Samsung\*.desktop
find /usr -type -f -name Samsung\*.directory
find /usr -type -f name Samsung\*.menu
find /etc -type -f name Samsung\*.desktop
find /etc -type -f name Samsung\*.directory
find /etc -type -f name Samsung\*.menu
```

Shouldn't they all be of the form '-type f -name...'?

Mike

---

### Post by tweedledee on 2009-08-05
> **Midahed said:**
> Shouldn't they all be of the form '-type f -name...'?

You are correct; I've fixed the typos in those commands in the first post.

---

### Post by Midahed on 2009-08-05
OK - I'm still struggling - probably due to my own ignorance!

I completed the removal of the software that I installed from the Samsung CD as defined in section 4 of your how-to and then installed the following from your repository:-

samsungmfp-configurator-data
samsungmfp-configurator-qt3
samsungmfp-driver
samsungmfp-lpr
samsungmfp-scanner

If I try to install a new printer via /usr/bin/system-config-printer and click 'new printer', select 'LPD/LPR Host or Printer', and specify the host and queue I'm presented with a short list of Samsung drives that doesn't include the CLP-610.  Also I noticed a reference to the 'foomatic printer database' on the previous screen.

It looks to me as if all I'm seeing is the driver list that's built into the 8.04.3. Hardy LTS distribution.

Any ideas as to what I'm doing wrong?

Also, how do you invoke the configurator?

Sorry to ask what are very basic questions - I have skimmed loads of the posts in this thread looking for inspiration but didn't find any answers - none that I could understand, anyway!

**[EDIT]**  I found out how the configurator is launched - the answer was in your how-to but I hadn't read that particular section <embarrassed>.  Even using the configurator, I'm still only being shown foomatic drivers and even those don't include one specifically for the CLP-610 - it just has the CLP-600.  And even if I configure it with that driver I still have the problem that when I specify the connection it doesn't seem to retain the IP address.  It's the same whether I specify the use of lpd or ipp.

Mike

---

### Post by tweedledee on 2009-08-05
> **Midahed said:**
> If I try to install a new printer via /usr/bin/system-config-printer and click 'new printer', select 'LPD/LPR Host or Printer', and specify the host and queue I'm presented with a short list of Samsung drives that doesn't include the CLP-610.  Also I noticed a reference to the 'foomatic printer database' on the previous screen.

It looks to me as if all I'm seeing is the driver list that's built into the 8.04.3. Hardy LTS distribution.

Any ideas as to what I'm doing wrong?


I believe you are correct; it sounds like you are just looking at the default foomatic database, and the version of foomatic that includes a driver supporting the 610 did not make it into 8.04.  I'm not sure what you are seeing as a reference to the foomatic database, but that's possibly the problem.  You can try a few of things, in any order:

1) Restarting cups (sudo /etc/init.d/cups restart), then trying again.

2) Reinstall cups (packages mark all packages in Synaptic starting with "cups" or "cupsys" and tell it to reinstall) in the event that some links or directories are broken.

3) Manually select the ppd to install (from /usr/share/ppd/samsung/, it will be something containing 610 and ending in .ppd.gz), although I've had poor success with that.

4) Check that /usr/share/ppd/samsung is a working link to /usr/share/cups/model/samsung, by "ls -l" in /usr/share/ppd; if not, share the output and I'll see if I can figure out what's wrong.

5) If there appears to be any way to select a non-foomatic database or broaden your selection in the printer config tool, try that.

---

### Post by Midahed on 2009-08-05
Mmmmm - it looks like I'm missing part of the installation.

/usr/share/ppd doesn't contain anything called samsung.

Also, /usr/share/cups/model is similarly devoid of anything samsung - in fact it's completely empty.

I should mention that I have at least managed to configure the printer in the sense that I can tell it to print a test page and it does print a sheet of paper.  The problem is that the printed text reads "SPL-C error - please use the proper driver".  That's to be expected because I only have access to the driver called "Samsung CLP-610, 1.1.0" which, I assume , doesn't support SPL-C.  You'll remember that before I uninstalled the Samsung CD-based software, I had access to two CLP-610 drivers - the one called "Samsung CLP-610, 1.1.0" and the one that referred to "CLP-610 Series (SPL-C)".  I guess only the latter one is SPL-C compatible.

My breakthrough in terms of being able to configure the printer at all was when I read a post referring to the use of [http://localhost:631](http://localhost:631) to get access to the CUPS control panel.  Configuring the printer there (instead of using /usr/bin/system-config-printer) works fine.

The only problem I have is that I appear to be missing part of the samsung-related installation - which, presumably, was supposed to be installed from your repository(?), and I'm missing the correct driver that supports SPL-C.

Here's the content of /usr/share/ppd

```
root@HomePC:/usr/share/ppd# ls -l
total 36
lrwxrwxrwx  1 root root      20 2008-07-29 13:34 1-local-admin -> /usr/local/sha                                         re/ppd
lrwxrwxrwx  1 root root      14 2008-07-29 13:34 2-third-party -> /opt/share/ppd
drwxr-xr-x  8 root root    4096 2009-06-04 09:18 cups-included
drwxr-xr-x  2 root root    4096 2008-07-29 13:34 cups-pdf
drwxrwsr-t  2 root lpadmin 4096 2008-04-21 21:17 custom
drwxr-xr-x  2 root root    4096 2008-11-22 16:25 foo2zjs
drwxr-xr-x  3 root root    4096 2008-07-29 13:33 ghostscript
drwxr-xr-x  3 root root    4096 2008-07-29 13:38 hpijs
drwxr-xr-x 11 root root    4096 2008-07-29 13:40 openprinting
drwxr-xr-x  2 root root    4096 2008-07-29 13:40 pxljr
drwxr-xr-x  5 root root    4096 2009-08-06 00:10 splix
root@HomePC:/usr/share/ppd#
```

Mike

---

### Post by tweedledee on 2009-08-05
> **Midahed said:**
> Mmmmm - it looks like I'm missing part of the installation.

Yes - now that I reread one of your previous posts, you also need the samsungmfp-data package; that's what contains all the ppd files you would need.  That one is recommended by the -driver package, and so is usually pulled in automatically, but if you've disabled automatic installation of recommends you'll have to grab it directly.  That package should clear up everything with respect to the driver.

I've no idea why you are having such difficulty with the system-config-printer tool, but if you have the web interface working you are good to go (I avoid it because I dislike activating a root account for entirely unrelated reasons, and the web interface is quirky without a root account).  The GUI tool is nice when it works, but when it fails is nearly impossible to troubleshoot.

---

### Post by Midahed on 2009-08-06
Installing the samsungmfp-data package fixed everything - thanks so much for your help.

The system-config-printer tool now works.  I tested this by deleting the printer that I'd set-up using the CUPS web interface and re-created it from scratch.  It all worked fine.

I've no logical explanation for why the samsungmfp-data package wasn't installed.  I don't have the automatic installation of recommended or dependent packages turned off.  For someone with my level of expertise, that would be courting disaster!  The only thing I can say is that, because most of the time I use the KDE desktop, I tend to use the Adept package manager rather than using a command-line tool like apt-get.  A few days ago I had problems getting apcupsd working with my UPS.  I eventually found that removing the Adept-based installation and re-installing using apt-get fixed the problems.  Maybe something similar was happening here?  Who knows.

Maybe when I get a spare five minutes I'll re-run the Samsung packages installation using Adept to see if the samsungmfp-data package goes missing again.  I could then separately try apt-get to see if that would have avoided all the problems.  Anyway, it's all working now.  Again, many thanks for your help.

**[Edit - results of further tests]**

OK - I've done a few checks using Adept and then apt-get to re-install the samsungmfp-driver package.  The result is that neither of them pick up samsungmfp-data as a dependency or a recommended additional package.  The original how-to says "...just installing the samsungmfp-driver package should enable full printing support..."

Therein lies the gottcha!  I took the instructions in the how-to literally and _just_ installed samsungmfp-driver and didn't look into the detail of what the other packages provided.

Mike

---

### Post by demarshall on 2009-08-06
I have been following this thread for some time now, having posted earlier in it at least once. I have a question. **Has anybody figured out how to fix a problem in which the scanner component of the scx-4521F does not appear in the configurator?** For some reason the only device that I see there is my TV tuner card which my machine sees but I have as yet been unable to install.

---

### Post by tweedledee on 2009-08-06
> **Midahed said:**
> I took the instructions in the how-to literally and _just_ installed samsungmfp-driver and didn't look into the detail of what the other packages provided.

I'll clarify that in the original guide, and probably change that recommends to a depends (even though in a strict packaging sense that is incorrect) the next time I update the packages to avoid problems like yours in the future.

---

### Post by Midahed on 2009-08-06
> **tweedledee said:**
> I'll clarify that in the original guide, and probably change that recommends to a depends (even though in a strict packaging sense that is incorrect) the next time I update the packages to avoid problems like yours in the future.
To be honest, in my ignorance of such things I hadn't looked at the information under the 'details' button on the Adept package manager.  I see now what you mean about 'recommends' and 'depends'.

As a novice user of Linux, my assumption was that if package x required package y in order for x to work, then installing x would always result in y being installed as well (if it wasn't already present).  If Linux package inter-dependency isn't actually defined like that, then I'd be inclined to leave it as it stands (rather than breaking with convention).  The clarification in the documentation should be more than enough to overcome any problem in the future - even for someone like me!

Mike

---

### Post by crystaldart on 2009-08-07
> **tweedledee said:**
> I'll need a lot more information to help you; many problems can give rise to this situation.  Did you install the driver directly from Samsung, via the packages, or both?  What model printer is it?  What is the exact name of the driver you selected to configure it with?  How is it connected?  If it is networked, how did you set that up?  Have you tried both printing a test page and printing an actual document?  Try also the "lp" command given in post 288, and share any output.  Did you configure the printer using the CUPS, foomatic, or Samsung interface?

THANK YOU VERY MUCH. 
As you asked me, I read your post 288. It helped me at last.

In Printing tools, I selected the Properties option of the Printer, there the Make and Model of My printer (SAMSUNG SCX-4521F) was shown set as Dot Matrix. I changed it back to SAMSUNG SCX-4500 series. And it worked like magic :P.

Hope my scan too is working.

It was great tut. Good Work

---

### Post by tweedledee on 2009-08-07
> **Midahed said:**
> As a novice user of Linux, my assumption was that if package x required package y in order for x to work, then installing x would always result in y being installed as well (if it wasn't already present).  If Linux package inter-dependency isn't actually defined like that, then I'd be inclined to leave it as it stands (rather than breaking with convention).

The issue is defining what "required" means.  As the samsungmfp packages are constructed, the -driver package provides everything needed to print to a Samsung printer, IF a ppd is available.  However, there is no "requirement" that the ppd come from another package; it could be installed manually, via some other package, etc.  And that is what "recommends" means: something that is most likely needed by most users, but isn't actually essential to the operation.  However, given that the point to the samsungmfp packages is to eliminate the need for other bits, I'll assume nobody is installing the ppd files externally and therefore the -data package will become "required" instead of "recommended."

This is one of the reasons that pacakaging is non-trivial.  It's all also complicated by the fact that Debian/Ubuntu/etc have for a couple of years defaulted to treating "recommended" packages as equally important to "depends" packages, unless specifically switched off.  However, that particular setting can still be quirky (as you discovered), so my reliance on it was probably not the best plan.

Anyway, it's an easy fix the next time I rebuild the packages.

---

### Post by tweedledee on 2009-08-07
> **crystaldart said:**
> THANK YOU VERY MUCH. 
As you asked me, I read your post 288. It helped me at last.

I'm glad you got it sorted out.  I'll extend the original post to include that as a trouble-shooting step, since it's clearly affecting multiple people.

---

### Post by sarang on 2009-08-23
Dear tweedledee, thanks a lot for this howto and for spending the time to properly package Samsung's improperly packaged drivers. 

I now have a completely functional (printing, scanning and OCR) SCX-4300. THANK YOU VERY MUCH!

In case these are useful for anyone else, the following firmware versions work well with the v.3.00.37-2 drivers from the [http://www-personal.umich.edu/~tjwatt/suldr/](http://www-personal.umich.edu/~tjwatt/suldr/) Samsung Unified Linux Driver repository:

Samsung SCX-4300
Printer Firmware Version:  1.18
Engine Version: V1.01.26
Emulation Version: QPDL 1.4 11-14-2005
Product Date: 200905

---

### Post by wstay on 2009-08-25
Hello tweedledee,
I have a working Samsung SCX-4725F printer installed on my ubuntu 8.10.
I wish to know if I can use this printer model to send fax?
If so, please advise on how or what command to use to send and receive fax?

---

### Post by tweedledee on 2009-08-26
> **wstay said:**
> Hello tweedledee,
I have a working Samsung SCX-4725F printer installed on my ubuntu 8.10.
I wish to know if I can use this printer model to send fax?
If so, please advise on how or what command to use to send and receive fax?

In short, I have no experience with this.  But if it's possible and straightforward, I would guess that you would need the Samsung Configurator installed and have your printer connected by USB, then see if there is some way using the Configurator to either configure a "fax" printer or just directly fax from that interface.  There are some indications on openprinting.org that other SCX printers can fax under linux, but I didn't look to see if there were any details.

---

### Post by bakra01 on 2009-08-29
I have a CLX-3175. Tried drivers from the website, from the CD that came with the printer, googled the internet and this forum but my problem stays the same: in Jaunty the colors are way too dark. Blue is sometimes black. Same goes for green. In Intrepid and Windows XP the colors are fine.
My PC's:
Desktop 32-bit Intrepid ==> colors are OK
Laptop 32-bit Jaunty ==> colors too dark
Laptop 64-bit Jaunty ==> colors too dark
Any of these PC's on Windows XP ==> colors are OK

The drivers I used on the different PC's are the same.
The only thing I noticed is that Intrepid uses Ghostscript 863 while  Jaunty uses 864.

Is Ghostscript the problem?

---

### Post by tweedledee on 2009-08-30
> **bakra01 said:**
> Is Ghostscript the problem?

Possibly, but it's more likely to be CUPS or a CUPS setting.  You should be able to test the ghostscript theory by installing the older ghostscript packages, or printing a PDF vs. non-PDF document and comparing (ghostscript is not used when printing from OpenOffice, for example).  However, I think it's more likely you'll improve the output by adjusting the CUPS color settings for the printer, which are part of the Image Options available under the Job Options section.  Unfortunately, I (a) can't guarantee that this will work, and (b) it could consume a significant amount of paper and ink depending on how many trial prints you end up performing.  I would start by ensuring that those options are the same on your two computers, and then adjust the gamma and/or saturation adjustments to try to lighten up the printed colors.

I've also seen a couple of cases where a particular program had trouble but others were fine, so you may want to try prints of multiple document types from multiple programs first to ensure that the problem is general and not application/document-type specific.

---

### Post by Nooki on 2009-09-10
Did someone got this printer up and running in Ubuntu 9.10 karmic? With the latest cups update, the printer can be installed fine (using Unified Driver, with your kind repository :), or using the included splix gpl driver ) but the scanner cannot be reached. It says "no scanners were identified" in the samsung configurator. Xsane doesn't detect it either. Any idea?

By the way, I did succeed some time ago to make it work. The method consisted of removing the cups package in synaptic, finding and removing any trace of cups on your system (you can use "sudo find / -name cups" to find them) and finally make installing cups from the sources. Then I could install the driver and the scanner would be detected. But Ubuntu's CUPS updates (or forced reinstallation) break it often, so it's a bit of a PITA. 

By the way, a big thanks for this detailed HOWTO and great info!

---

### Post by tweedledee on 2009-09-11
> **Nooki said:**
> It says "no scanners were identified" in the samsung configurator. Xsane doesn't detect it either. Any idea?

I would guess the problem relates to this new feature of CUPS 1.4 (from the official changes):> #58 USB printer support; the usb backend now uses libusb when available to allow it to better work with third-party scanning and printing solutions.

There are bug reports in Debian Sid regarding USB detection problems with the new CUPS, although they may not relate to your problem: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=545453](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=545453) and [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=545288](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=545288).

Off-hand, I would normally blame something in the Samsung driver for not talking to libusb properly, but working with the older usblp.  However, it's very strange that compiling your own CUPS solves the problem; if you can make some sort of guess as to what compilation options are apparently different for your manual compile vs. the packaged version, we might be able to narrow this down.

---

### Post by pja on 2009-09-15
tweedledee,

Your recommended option (IIc) works perfectly.  I have always had some issues getting my Samsung ML-1740 to work properly.  Now its fine.

I have one question; in the "Printing Configuration" dialog the printer's port is shown as "usb://Samsung/ML-1740" but in the "Unified Driver Configurator" there is a list of USB ports but none correspond to the one above.  The "Printing Configuration" dialogue CAN print a test page successfully but the "Unified Driver Configurator" dialog CAN'T.  Do you have any suggestions?

Thanks for the great help so far,
Peter

---

### Post by sucker4techno on 2009-09-15
Best Howto Ever!!!

---

### Post by tweedledee on 2009-09-26
> **pja said:**
> I have one question; in the "Printing Configuration" dialog the printer's port is shown as "usb://Samsung/ML-1740" but in the "Unified Driver Configurator" there is a list of USB ports but none correspond to the one above.  The "Printing Configuration" dialogue CAN print a test page successfully but the "Unified Driver Configurator" dialog CAN'T.  Do you have any suggestions?

Apart from installing the printer via the Configurator in the first place (I'm assuming you used the printer configuration tool instead), I can't immediately think of anything.  I don't have a lot of experience with the Configurator and USB ports, and it's always seemed a little weird to how how it dealt with the ports.

---

### Post by freek_zero on 2009-09-28
tweedledee, just wanted to offer my hearty thanks for this guide and your repository. Got my SCX-4500 working just fine (including scanning, which I was getting worried was just not going to work based on what I saw from other  posts). Rather annoying that the CD included is from 07. Not the current versions of their software.

---

### Post by wally83 on 2009-10-02
I can't get my scx-4200 working at all. **[SOLVED, see below!]**

I'm now using Ubuntu 9.10 Karmic (Alpha 6) amd64. I have had this scx-4200 working in my several previous Ubuntu installations including 32-bit 9.04 Jaunty in this very same machine. (except that I have NEVER got scx scanner working on Linux, but I rarely use it anyway.)

So I have now tried three different solutions: 
1. with splix, 
2. with manual installation of newest unified drivers and 
3. with tweedledee's repos (and yes, I did uninstall previous installations completely (IV)).

I have rebooted multiple times, purged cups-bsd and others and reinstalled them etc. etc.

I have tried to use Samsung's cli, qt3 and qt4 configurators and [http://localhost:631](http://localhost:631) and System->Administration->Printing (something like that, not using English language version ATM), but none of these detects my usb-connected scx-4200 at all. Samsung Configurator does not find a thing and none of the /dev/mfpX are used.

When I unplug&plug my printer, dmesg says:
```

[ 1267.218189] usb 1-3: USB disconnect, address 3
[ 1269.804034] usb 1-3: new high speed USB device using ehci_hcd and address 6
[ 1269.937862] usb 1-3: configuration #1 chosen from 1 choice

```

lsusb:
```

Bus 001 Device 006: ID 04e8:341b Samsung Electronics Co., Ltd SCX-4200 series

```

I also HAD the problem with:
```

Cannot mix incompatible Qt libraries

```

I solved this by installling qt3 version of the samsung configurator.

lpinfo -v:
```

serial serial:/dev/ttyS0?baud=115200
network beh
network smb
network http
network ipp
direct scsi
network socket
direct parallel:/dev/lp0
network lpd
direct hp
direct hpfax

```

No "direct usb:/Samsung/blahblah" anywhere.

**I think this has to be related to new CUPS version on Karmic, [S]but how to solve this?[/S] [COLOR="Red"]SOLVED BELOW[/COLOR]**

EDIT:
If someone knows any ways to manually configure this device, I could try that. Options I can see in System->Administration->Printing & add new printer are: "LPT #1, Serial port 1, Other and Network printer with sub-options such as "LPD/LPR-server or printer"". No USB seen anywhere.

EDIT2:
this CUPS thing may be fixed in version 1.4.1-4, but Ubuntu Karmic is still using version 1.4.1-2 (cups and cups-bsd)

**SOLVED:**
To solve this, you have to install 1.4.1-4. As of now, newest CUPS have not hit the repository. So the easiest way is to temporarily add Debian Sid (unstable) sources and install cups and its dependencies.

Step to step instructions:

1. edit apt sources:
```

gksu gedit /etc/apt/sources.list

```

2. add this line to the end of file and save it:
```

deb http://ftp.de.debian.org/debian sid main 

```

3. update sources and install:
```

sudo apt-get update
sudo apt-get install cups libpoppler4 libopenjpeg2
sudo apt-get -f install

```

(3b. you maybe should answer Y when installer asks for what to do with /etc/cups/cupsd.conf. I did that and it worked)

4. You should immeadedly see notice: "SCX-4200 new printer added" or something like that. So, it's working now!

EDIT: 
5. do not forget to **remove inserted line from /etc/apt/sources.list!** Unstable packets are not something you are looking for...
[B]
Thanks for tweedledee[/B] for his effort, excellent howto and repositories.

EDIT:
**Scanner is still not working**, but as I said, I have never got it working in Ubuntu anyways, so that was just what I expected...

---

### Post by tweedledee on 2009-10-03
> **wally83 said:**
> I can't get my scx-4200 working at all. **[SOLVED, see below!]**

Based on changelogs, it appears that 1.4.1-4 should fix all (or at least most) of the recent USB problems with 1.4.x CUPS reported in this thread, essentially by allowing either the new or the old USB interface so that printers that don't work with the new aren't left useless.

I'm still running 1.3.11 and don't use USB anyway, so hopefully this update gets everything working for the rest of you.

---

### Post by mrdiego on 2009-10-05
@ tweedledee: :( Always using your drivers for synaptic and it was wonderful. But with Karmic-Koala I have bad dependences if I choose driver and scanner for install by synaptic.

mhh okay, it's printing with footmac (4500), but scanning is impossible again. Any idea? :)

---

### Post by organsnyder on 2009-10-06
My SCX4521f stopped being listed by scanimage -L after upgrading from Jaunty to Karmic. I found out that it does work as root, however. I might just need to add my user to the appropriate group, but I decided that making /usr/bin/scanimage suid was acceptable for me. I do all of my scanning from the command-line. I'm using the drivers from the repository mentioned in the first message.

---

### Post by jpaisneto on 2009-10-10
Hi! I'm testing Karmic Koala and I can't install the driver from the repository... It seems  libstdc++5 has been removed and replaced by libstdc++6. Any way to solve this?

Thank you.

---

### Post by tweedledee on 2009-10-13
> **jpaisneto said:**
> Hi! I'm testing Karmic Koala and I can't install the driver from the repository... It seems  libstdc++5 has been removed and replaced by libstdc++6. Any way to solve this?

If that's the only dependency problem, then yes; I can upload a copy of the old libstdc++5 package to my repository.  The package has also been removed from Debian, but I have it around.  I'll look into this over the weekend, when I should hopefully have a little free time.

---

### Post by tweedledee on 2009-10-17
Libstdc++5 is now part of my repository, and the drivers should work with Karmic.

---

### Post by jpaisneto on 2009-10-18
> **tweedledee said:**
> Libstdc++5 is now part of my repository, and the drivers should work with Karmic.

Ok, thank you. It works now, although it shows a warning about authentication or something like that, but I have the key installed...

---

### Post by tweedledee on 2009-10-18
> **jpaisneto said:**
> Ok, thank you. It works now, although it shows a warning about authentication or something like that, but I have the key installed...

I was having difficulty with the keys, because my system has undergone a complete wipe and reinstall since I last updated the repository.  The problem should be fixed now, although you will need to download and add the public key again.

---

### Post by demarshall on 2009-10-18
I have a Samsung SCX-4521F that I can print with without problems. However, I have never been able to get the scanner to work. I have version common 3.00.37, printer 3.00.20, and scanner 3.00.05 - Build 152 installed. The scanner tab doesn't show the scanner but only my TV tuner card and my web cam. Should I upgrade the Samsung software? Will this solve the problem with the scanner? Any ideas?

Thanks

---

### Post by yahs on 2009-10-30
Tweedeldee

Been using your excellent post since Hardy.
Just want to share my knowledge and experience of latest upgrade.
I did a fresh install of Karmic Desktop on Friday Oct 30th 
Unlike Jaunty, Karmic did not recognise my Samsung scx4100 mfp.
Using system, administration, printing, new - karmic recognised the printer and offered scx4200 as the only available printer driver. I accepted this and printed a test page which printed okay. The device URI: was listed as usb://Samsung/SCX-4200%20Series using SpliX V.2.0.0
However no scanning available at this moment. On restarting the computer I noticed an error message:

error: hp-systray requires Qt4 GUI and DBus support. Exiting.
 
I downloaded Samsung unified driver ver 3.00.37, extracted and ran sudo ./install.sh
Normal GUI interface appeared and installed scx4100.
Device URI: was listed as mfp:/dev/mfp4 and test page printed using CUPS v 1.1.x.
However still no sign of a scanner, so another reboot still with the same error message.
Checked groups and opened a terminal; sudo xsane found the scanner but Samsung Unified Driver Configurator still not showing the scanner.
I then used Synaptic Package manager and searched for qt4 which brought up ibus-qt4. I installed this package and opened Samsung Unified Driver Configurator to find that the scanner was now recognised and worked. Two printers appear in the Configurator: samsung-scx-series on  usb://Samsung/SCX-4200%20Series and Samsung scx (default) on  mfp:/dev/mfp4. I changed the driver from scx-4200 to scx-4100 (after downloading Unified driver 3.00.37 there are lots more samsung drivers available) and I can print from either printer. I only need to keep one printer so I have deleted samsung-scx-series. Scanner comes up as flatbed scanner scx-4100 series on usb:0 and works perfectly. Finally another reboot and the error message has gone.
Very happy with Karmic. The installation of the scx-4100 with jaunty and the previous version of the Unified driver was extremely easy. This one needed a little more, but I'm not complaining. Hope this is helpful in some way

yahs

---

### Post by yahs on 2009-11-02
An update to my last post

Apologies for the typo Tweedledee

I have now done 4 fresh installs of Karmic Desktop to different partitions and disks, all with the printer attached by usb.

Unlike Jaunty, Karmic does not recognise my Samsung scx4100 mfp straight away. I have found the easiest way to install is to download the unified driver from Samsung (ver 3.00.37) as soon as Karmic has installed. 

Extract and run sudo ./install from the cdroot/Linux directory.

In the terminal the messages are as follows

[COLOR="Red"]libstdc ++.so.5 not found, install ... done
libstdc ++.so.3 not found, install ... done

It seems Qt library is not installed or X display is not accessible
Custom Qt library will be configured for use with this package.[/COLOR]

Samsung GUI installer then appears and runs, you are offered the option of adding users to the group lp and disabling parallel printing.

The printer is configured to use /dev/mfp4 and a test page can be printed using CUPS v 1.1.x.

The unified driver configurator appears on the desktop but when I select the scanner icon only my usb webcam shows.

However I checked the groups and added myself to the saned group, reboot and everything works perfectly.

Note: After the reboot, in the unified driver configurator there are now 2 printers showing.

SCX-4100-Series on usb://Samsung/SCX-4100%20Series
scx4100(default) on mfp:/dev/mfp4

Both work but as I only need 1, I delete SCX-4100-Series.

In Jaunty the printer SCX-4100-Series on usb://Samsung/SCX-4100%20Series appears immediately after the installation finishes and although you can use the printer you cannot (or at least I can't) use the scanner unless you download and install the unified driver from Samsung.

So apart from not being made a member of the saned group the installation works pretty well for me. No change of ownership and no workarounds needed; printing and scanning are exactly the same quality as XP. A considerable improvement since your original posting but many thanks as always and it's nice to see that Samsung are trying to help the process, even though they don't have your expertise!

---

### Post by vyvee on 2009-11-04
Hi tweedledee, thanks for your extreme hard work in maintaining this HOWTO and your easy-to-use repository setup!

I have updated my own howto ([http://www.vyvy.org/main/en/node/146](http://www.vyvy.org/main/en/node/146)) to reflect the even easier way of setting up my Xerox PE220 (~= Samsung SCX-4521) with your repository & the new Ubuntu 9.10. There are a few technical things you may be interested in:

* Ubuntu 9.10 includes the Splix package (([http://www.linuxprinting.org/show_driver.cgi?driver=splix](http://www.linuxprinting.org/show_driver.cgi?driver=splix)) now by default to support more Samsung printers out-of-box. (including some SCX- series...) 

* Can easily use this one-line command to download & import the GPG key of your repository:
```
wget -q http://www-personal.umich.edu/~tjwatt/suldr/suldr.gpg -O- | sudo apt-key add -
```
(Think we linux hackers will just use this. :))

That's all. Things are getting simpler now with the new Ubuntu & your repository. Cheer!

---

### Post by jis on 2009-11-07
Check the user notes about clp-315w: [http://www.openprinting.org/show_printer.cgi?recnum=Samsung-CLP-315](http://www.openprinting.org/show_printer.cgi?recnum=Samsung-CLP-315)

---

### Post by lightrush on 2009-11-08
Thank you very much for this HOWTO and the repository you have set up. It has helped me numerous times.

---

### Post by Olivier V on 2009-11-21
Hi,

Thank you very much for this good work.
I've tried to install the package provided by Samsung, but it hasn't work, specially in acroread and programs using lpr.
And unsinstalling didn't worked too ](*,)

The package provided here works fine !

But is the "Smart panel" provided too ?
I' didn't undestand how to make it working.

Thank you, and excuse my bad english.

Olivier V

---

### Post by reesje on 2009-11-22
> **tweedledee said:**
> Guide to installing Samsung printers & the... 
Instead of the rather complicated way of adding the key to the repository, could you add this line to your guide instead:
```
wget -O - http://www-personal.umich.edu/~tjwatt/suldr/suldr.gpg | sudo apt-key add -
```
It makes it a lot easier. Thanks for your guide, by the way!

BR,
René

---

### Post by demarshall on 2009-11-24
> **demarshall said:**
> I have a Samsung SCX-4521F that I can print with without problems. However, I have never been able to get the scanner to work. I have version common 3.00.37, printer 3.00.20, and scanner 3.00.05 - Build 152 installed. The scanner tab doesn't show the scanner but only my TV tuner card and my web cam. Should I upgrade the Samsung software? Will this solve the problem with the scanner? Any ideas?

Thanks
I'm still waiting patiently for some kind soul to help me to get my scanner working. I have no upgraded to Ubuntu 9.10 and did so mostly to get my scanner working.

---

### Post by vyvee on 2009-11-25
Hi demarshall, how did you install the Samsung driver? It's advised that you use the repository set up by tweedledee.
Another very important thing: You need to add users you allow to access the scanner into the 'lp' group. You can use System -> Users and Groups from the start menu to do this, or use the adduser command. Logout and re-login to take the effect.
To check if the scanner is properly detected, you can use 'scanimage -L' from a terminal too.

---

### Post by fish stinks on 2009-12-03
Hi I just bought a used samsung scx 4500 printer/scanner. (USB)

The printer worked out of the box ( no driver needed in ubuntu karmic )
Then I wanted to try the scanner and got stuck.
Finally i found this howto and added the drivers from the repo. of tweedledee. 
The scanner was now found, but xsane only worked running as root. 
I was just working further to the pages 4,5,6.... then it hit me to reverse my reading order to page 35 and back.... and guess what... the solution was right there.
THANKS! CHEERS!

---

### Post by helmut_hed on 2009-12-23
If anyone is interested, I'm finding some type of permissions issue with using scanning.  I have a SCX-4725FN and installed the drivers according to the IIc and IId directions.  Printing worked fine, but not scanning.  After some investigation I found that this command:

**sane-find-scanner**

works and finds my scanner:

**found USB scanner (vendor=0x04e8, product=0x341f) at libusb:001:005**

but this command:

**scanimage -L**

Finds nothing ("No scanners were identified").  However, if I do this:

**sudo scanimage -L**

It works.  From there I discovered that the GUI frontends (xsane, skanlite) will work only if I run them as root.  I don't have time to investigate further but if you have my symptoms you may want to try this approach.

---

### Post by vonkad on 2009-12-25
I've just successfully used the howto from the first page of this thread to get my scx4200 scanner to work on ubuntu 9.10 64bit. xsane does not complain anymore about not finding devices. I used IIc and IId.

Thanks a lot.

---

### Post by malibujohn on 2009-12-26
I am attempting to get my Samsung CLP 315 working on Linux. It works on my windows side, but I get the message "SPL-C ERROR" Please use the proper driver.
 I was following the instructions when the following displayed.

12:36:35 (162.99 KB/s) - `foo2zjs.tar.gz' saved [1588047/1588047]

malibujohn@malibujohn-desktop:~$ tar zxf foo2zjs.tar.gz
malibujohn@malibujohn-desktop:~$ cdfoo2zjs
bash: cdfoo2zjs: command not found
malibujohn@malibujohn-desktop:~$ cd foo2zjs
malibujohn@malibujohn-desktop:~/foo2zjs$ make
#
# Dependencies...
#
      ***
      *** Error: /usr/include/stdio.h is not installed!
      ***
      *** Install Software Development (gcc) package
      *** for Ubuntu: sudo apt-get install build-essential
      ***
make: *** [all-test] Error 1
malibujohn@malibujohn-desktop:~/foo2zjs$ 
malibujohn@malibujohn-desktop:~/foo2zjs$ sudo make install
[sudo] password for malibujohn: 

I realized the error with :cdfoo2zjs & made the correct entry
  After typing in my password, I could not continue.
 Any suggestions?
 Malibujohn

---

### Post by chewearn on 2009-12-26
> **malibujohn said:**
> I am attempting to get my Samsung CLP 315 working on Linux. It works on my windows side, but I get the message "SPL-C ERROR" Please use the proper driver.
 I was following the instructions when the following displayed.

12:36:35 (162.99 KB/s) - `foo2zjs.tar.gz' saved [1588047/1588047]

malibujohn@malibujohn-desktop:~$ tar zxf foo2zjs.tar.gz
malibujohn@malibujohn-desktop:~$ cdfoo2zjs
bash: cdfoo2zjs: command not found
malibujohn@malibujohn-desktop:~$ cd foo2zjs
malibujohn@malibujohn-desktop:~/foo2zjs$ make
#
# Dependencies...
#
      ***
      [B]*** Error: /usr/include/stdio.h is not installed!
      ***
      *** Install Software Development (gcc) package
      *** for Ubuntu: sudo apt-get install build-essential[/B]
      ***
make: *** [all-test] Error 1
malibujohn@malibujohn-desktop:~/foo2zjs$ 
malibujohn@malibujohn-desktop:~/foo2zjs$ sudo make install
[sudo] password for malibujohn: 

I realized the error with :cdfoo2zjs & made the correct entry
  After typing in my password, I could not continue.
 Any suggestions?
 Malibujohn

The highlighted lines (in bold) could be the problem.  Have you install build-essential package?

```
sudo apt-get install build-essential
```

---

### Post by malibujohn on 2009-12-26
# Now use your printer configuration GUI to create a new printer.
#
# On Redhat 7.2/7.3/8.0/9.0 and Fedora Core 1-5, run "printconf-gui".
# On Fedora Core 6 and Fedora 7/8/9/10/11, run "system-config-printer".
# On Mandrake, run "printerdrake"
# On Suse 9.x/10.x/11.x, run "yast"
# On Ubuntu 5.10/6.06/6.10/7.04, run "gnome-cups-manager"
# On Ubuntu 7.10/8.x/9.x, run "system-config-printer".
malibujohn@malibujohn-desktop:~/foo2zjs$ system-config-printer
fetchPPDs
queryPPDs
Lock acquired for PPDs thread
PPDs thread started
Connecting (PPDs)
Fetching PPDs
Closing connection (PPDs)
Releasing PPDs lock
Got PPDs
set PageSize = Letter
/usr/bin/foo2qpdl-wrapper: found
/usr/lib/cups/filter/foomatic-rip: found
Printing custom test page /usr/share/system-config-printer/testpage-
letter.ps

Thanks for the info. It got me to this point.
 I am using Ubuntu 8.04
 The printer DID NOT print the test page.
 What now?

A print command from "file" resulted in a printout of the original message:

SPL-C ERROR - Please use the proper driver

POSITION :  OxO (O)

System  : arc/xl_image

 LINE  :  606

VERSION  : SPL-C 5.35 11-20-2007

---

### Post by chewearn on 2009-12-27
It seemed the printer said you got the wrong driver install?

Perhaps you should start from the beginning.  Tell us where you got the driver and which instruction you are following to install it.

Go back and read the first post of this thread.

---

### Post by Sir_Patrick on 2009-12-28
Hi there,

This is a very nice HOWTO, very long too...
I bought a Samsung CLX-3175 this month and tried to get it working with ubuntu 9.10 Karmic.
The printer part worked fine and direct, just plug in the printer in the USB port and it was detected right away.
It installs the foomatic drivers which do not give the greatest results.
I also wanted to use the scanner but xsane could not find it.
I tried the drivers from the Samsung-site but it would not even find my printer automatically and also not the scanner part.
Read the post thru and decided to uninstall the Samsung drivers completely and make installation from the repo's in this post.
The printer does show a far better result with the CLX-3170 driver but the scanner is nowhere being detected.

If i do sane-find-scanner :```
patrick@patrick-desktop:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04e8 [Samsung Electronics Co., Ltd.], product=0x342a [CLX-3170 Series]) at libusb:001:003
found USB scanner (vendor=0x13d3 [Manufacturer Realtek ], product=0x3306 [RTL8191S WLAN Adapter ]) at libusb:002:005
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.



```[

then i do scanimage -L ```

patrick@patrick-desktop:~$ scanimage -L
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
]
```

Then is do sudo scanimage -L ```
patrick@patrick-desktop:~$ sudo scanimage -L
[sudo] password for patrick: 
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```So the sanner is detected by sane-find-scanner but with scanimage -L it doesn't detect it.
Anybody has the same problem or better a solution for this?

Thanks in advance.

Patrick

---

### Post by malibujohn on 2009-12-28
> **chewearn said:**
> It seemed the printer said you got the wrong driver install?

Perhaps you should start from the beginning.  Tell us where you got the driver and which instruction you are following to install it.

Go back and read the first post of this thread.



I read the post all the way through. Note IIb
highlights [http://foo2qpdl.rkkda.com](http://foo2qpdl.rkkda.com). for the CLP-315 Executing this results in a default to foo2zjs. A red warning suggests NOT using this from Ubuntu etc.
 I proceeded on to a $ wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz) command that found & downloaded the correct? driver. I proceeded from there.
I am not sure how to proceed now. There are suggestions that I should uninstall the driver & start again.
 I am relatively new to Linux (Ubuntu) commands & am losing confidence in my abilities

---

### Post by chewearn on 2009-12-29
> **malibujohn said:**
> I read the post all the way through. Note IIb
highlights [http://foo2qpdl.rkkda.com](http://foo2qpdl.rkkda.com). for the CLP-315 Executing this results in a default to foo2zjs. A red warning suggests NOT using this from Ubuntu etc.
 I proceeded on to a $ wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz) command that found & downloaded the correct? driver. I proceeded from there.
I am not sure how to proceed now. There are suggestions that I should uninstall the driver & start again.
 I am relatively new to Linux (Ubuntu) commands & am losing confidence in my abilities

You have three options:
1. Wait for someone else in this thread to respond (this beyond my knowledge now)
2. Get support for the foo2zjs driver here: [http://foo2zjs.rkkda.com/forum/](http://foo2zjs.rkkda.com/forum/)
3. Regard step IIb as failed, and proceed to step IIc

---

### Post by malibujohn on 2009-12-29
I am attempting to start over. I received information that driver SpliX version 2.0.0 works so I am attempting to uninstall the foo2zjs driver. Here is what I have so far:

malibujohn@malibujohn-desktop:~$ sudo /opt/Samsung/mfp/uninstall/uninstall.sh  (As per the instructions in section IV of How To Install Samsung Unified Printer Driver by Tweedledee)
[sudo] password for malibujohn: 
sudo: /opt/Samsung/mfp/uninstall/uninstall.sh: command not found
malibujohn@malibujohn-desktop:~$ sudo rm /usr/lib/libtiff.so3*
rm: cannot remove `/usr/lib/libtiff.so3*': No such file or directory
malibujohn@malibujohn-desktop:~$ sudo rm -r /opt/Samsung/mfp
rm: cannot remove `/opt/Samsung/mfp': No such file or directory
malibujohn@malibujohn-desktop:~$ 

 Where do I go from here? I do not want to install the SpliX until this other mess is cleaned up.
 Thanks.
 Malibujohn

---

### Post by chewearn on 2009-12-30
> **malibujohn said:**
> I am attempting to start over. I received information that driver SpliX version 2.0.0 works so I am attempting to uninstall the foo2zjs driver. Here is what I have so far:

malibujohn@malibujohn-desktop:~$ sudo /opt/Samsung/mfp/uninstall/uninstall.sh  (As per the instructions in section IV of How To Install Samsung Unified Printer Driver by Tweedledee)
[sudo] password for malibujohn: 
sudo: /opt/Samsung/mfp/uninstall/uninstall.sh: command not found
malibujohn@malibujohn-desktop:~$ sudo rm /usr/lib/libtiff.so3*
rm: cannot remove `/usr/lib/libtiff.so3*': No such file or directory
malibujohn@malibujohn-desktop:~$ sudo rm -r /opt/Samsung/mfp
rm: cannot remove `/opt/Samsung/mfp': No such file or directory
malibujohn@malibujohn-desktop:~$ 

 Where do I go from here? I do not want to install the SpliX until this other mess is cleaned up.
 Thanks.
 Malibujohn

Unfortunately, the instruction from Tweedledee was for uninstalling the **Samsung Unified Printer Driver**.

OTOH, the driver you had installed was the  **foo2zjs**, therefore, the instruction is bound to fail.  I am not familiar with foo2zjs driver including how to uninstall.

I have not heard of driver SpliX.  It is also not mentioned in first post of this thread.

For your info, I also owned a Samsung CLP-315.  I am using the Samsung Unified Printer Driver with success.

---

### Post by malibujohn on 2009-12-30
> **chewearn said:**
> Unfortunately, the instruction from Tweedledee was for uninstalling the **Samsung Unified Printer Driver**.

OTOH, the driver you had installed was the  **foo2zjs**, therefore, the instruction is bound to fail.  I am not familiar with foo2zjs driver including how to uninstall.

I have not heard of driver SpliX.  It is also not mentioned in first post of this thread.

For your info, I also owned a Samsung CLP-315.  I am using the Samsung Unified Printer Driver with success.

When I was following the instructions, Note 11b states:
Use Foomatic & there is a reference to [http://foo2qpdl.rkkda.com](http://foo2qpdl.rkkda.com). Clicking on this, I wound up with $ wget -O foo2zjs.tar.gz http:foo2zjs.rkkda.com/foo2zjs.tar.gz. I entered this & things started to happen.
 You mention this is not the Samsung Unified Driver. 
 I have downloaded the SpliX driver to my Desktop but it has not been activated. Can you suggest the steps to undo the foomatic instal to get back to the Unifies Driver install ?.
 I really appreciate your patience with this one. I am sure sometime in the future all this will become clear.
 Thanks again.
 Malibujohn

---

### Post by chewearn on 2009-12-30
> **malibujohn said:**
> When I was following the instructions, Note 11b states:
Use Foomatic & there is a reference to [http://foo2qpdl.rkkda.com](http://foo2qpdl.rkkda.com). Clicking on this, I wound up with $ wget -O foo2zjs.tar.gz http:foo2zjs.rkkda.com/foo2zjs.tar.gz. I entered this & things started to happen.
You mention this is not the Samsung Unified Driver. 
 

From the website:
"**foo2qpdl** is an open source printer driver for printers that use the QPDL wire protocol for their print data."

In other words, this is a driver developed by an open source community.  It's not the Samsung Unified Printer Driver (which is developed by Samsung).

> I have downloaded the SpliX driver to my Desktop but it has not been activated.As mentioned, I have not heard of the SpliX driver.  But for fun, I Google it and found the website: [http://splix.ap2c.org/](http://splix.ap2c.org/)
So, this is another third party reversed engineered driver.

> 
 Can you suggest the steps to undo the foomatic instal to get back to the Unifies Driver install ?.OK, I went a bit further and download the foo2zjs package.  Inside, there is a file "INSTALL.in" (please read it, there is some Ubuntu notes at line 157) which said that you could uninstall it by:

```

sudo make uninstall

```To install the Samsung Unified Printer Driver, go back to Step IIc in the first post.

> 
 I really appreciate your patience with this one. I am sure sometime in the future all this will become clear.
 Thanks again.
 MalibujohnNo problem. :)

---

### Post by tweedledee on 2009-12-30
Major update to the repository and guide.  Driver v3.00.65 are now the primary ones available, although 3.00.37 are still present if desired (there are some reasons the older driver might be preferred).

To all those having difficulty working with a scanner: have you added yourself to the "lp" group and logged out/back in?  If no, try that.  If yes, please let me know and I'll see if I can determine if there is something else you need to do.  Not having a Samsung scanner, I can't troubleshoot without significant input.

Also, I have been traveling extensively and working far too many hours the last couple of months to have been monitoring this thread.  I hope to be more active for the near future (meaning a response might only take a week, not two months).

---

### Post by malibujohn on 2009-12-31
> **chewearn said:**
> From the website:
"**foo2qpdl** is an open source printer driver for printers that use the QPDL wire protocol for their print data."

In other words, this is a driver developed by an open source community.  It's not the Samsung Unified Printer Driver (which is developed by Samsung).

As mentioned, I have not heard of the SpliX driver.  But for fun, I Google it and found the website: [http://splix.ap2c.org/](http://splix.ap2c.org/)
So, this is another third party reversed engineered driver.

OK, I went a bit further and download the foo2zjs package.  Inside, there is a file "INSTALL.in" (please read it, there is some Ubuntu notes at line 157) which said that you could uninstall it by:

```

sudo make uninstall

```To install the Samsung Unified Printer Driver, go back to Step IIc in the first post.

No problem. :)

1. Add the following line to your /etc/sources.list, by editing the file as root (or using sudo), or by using Synaptic or other GUI to add a repository.

I understand using sudo as a root command but, I have no idea where to locate "/etc/sources.list"
 Thanks
Malibujohn

---

### Post by jis on 2009-12-31
> **malibujohn said:**
> 
I understand using sudo as a root command but, I have no idea where to locate "/etc/sources.list"
 Thanks
Malibujohn

It should be /etc/apt/sources.list

---

### Post by malibujohn on 2009-12-31
> **jis said:**
> It should be /etc/apt/sources.list

I get the message permission denied.

 I appreciate the assistance of you guys/gals on this forum. I attempted to get my printer working as an intro to working with Linux/Ubunto.
 I do have a hard copy of the Ubuntu Pocket Guide & Reference but it does not go into specifics, Hence my requests for assistance.
 I will shelve this project for now.
 Thanks again
 Malibujohn:(

---

### Post by helmut_hed on 2010-01-02
malibujohn: try "sudo gedit /etc/apt/sources.list"

That will do it as root and you should not get any permissions errors.

---

### Post by helmut_hed on 2010-01-02
I'm having trouble installing the latest version of samsungmfp-driver.  It appears there is some conflict with another package:

sudo apt-get install samsungmfp-driver
...
The following packages will be upgraded:
  samsungmfp-driver
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
...
Preparing to replace samsungmfp-driver 3.00.37-2 (using .../samsungmfp-driver_3.00.65-1_amd64.deb) ...
Unpacking replacement samsungmfp-driver ...
dpkg: error processing /var/cache/apt/archives/samsungmfp-driver_3.00.65-1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libcups.so', which is also in package libcups2-dev 0:1.4.1-5ubuntu2.1

Any suggestions? Does libcups really need to be replaced?

Update: a new version 3.00.65-2 appeared and resolved this issue.  Thanks to the maintainer.

---

### Post by malibujohn on 2010-01-02
> **helmut_hed said:**
> malibujohn: try "sudo gedit /etc/apt/sources.list"

That will do it as root and you should not get any permissions errors.

Thanks Helmut.
 I will give it a try
 Malibujohn

---

### Post by tweedledee on 2010-01-02
> **helmut_hed said:**
> Does libcups really need to be replaced?

No.  Short answer: try it now, I've uploaded new packages that shouldn't conflict with the libcups2-dev package.

Long answer: Samsung was lazy when compiling 3.00.65, and made us of a link only present in the cups development packages.  I'm trying to work around that problem without having to pull in the development libraries (which aren't actually needed and pull in lots of unnecessary dependencies) or breaking the packaging system by artificially creating the link (as the Samsung installer does).  I think I've worked it out now.

---

### Post by jamb on 2010-01-03
I have lately used and tested tweedledee's excellent procedure on four diffrent releases 
(Ubuntu 8.10, 9.04, 9.10) and Debian Lenny (5.0) with great success, 
and on different machines connected to my Networked Samsung ML-2571N Laserjet. 
Since people may search for an exact P/N match I just updated my original post. 
For printer configuration I recommend the manufacturer tool. See:

[http://ubuntuforums.org/showthread.php?p=4086777#post4086777]("http://ubuntuforums.org/showthread.php?p=4086777#post4086777")
 
For the ML-2571N, start Samsung configurator (qt3), and bypass various desktop printer tools:
> 
cd /opt/Samsung/mfp/bin
sudo ./Configurator

The Configurator outputs one startup message: 
Needs cupsys-common, 
but when installed everything is fine. If this is a true dependence or not I do not know. 
There is a considerable delay after pushing the [ Add printer ] button in the application opening window.
The configurator must be started with sudo to make any configuration changes, like changing the default page size from Letter to A4.

Tweedledee, thanks for your great work!

---

### Post by martach on 2010-01-04
The new version (3.00.65-2) does not work with my CLX-3175. XSane cannot detect the scanner. In order to get the scanner working, I have to force and lock version 3.00.37-2.

I run Ubuntu 9.10 32bit and have added myself to the lp group.

---

### Post by Sir_Patrick on 2010-01-04
I removed myself from group lp and after a restart added myself again, after this i made a restart and tried again but no luck with xsane and my scanner (clx-3175).

Also i updated to the newest version in the repository but no luck either.
I also tried with the same computer to run a live cd of ubuntu 9.04 and added the repo's and it worked directly, the scanner directly worked with xsane.

For me it is an issue with Ubuntu 9.10 somehow something is changed with Karmic and it doesn't work for me.

I hope that i can solve this as i want to use my scanner with Ubuntu and not with the version of windows 7 that came with my pc (in wich the printer and scanner work flawlessly).

---

### Post by tweedledee on 2010-01-04
> **martach said:**
> The new version (3.00.65-2) does not work with my CLX-3175. XSane cannot detect the scanner. In order to get the scanner working, I have to force and lock version 3.00.37-2.

I run Ubuntu 9.10 32bit and have added myself to the lp group.

If you are inclined, could you please try the following:
1. copy /usr/lib/sane/libsane-mfp* to a temporary location
2. switch back to the new packages
3. copy (as root) the libsane-mfp* files back to /usr/lib/sane/
4. see if your scanner works

Either way, then remove the files you copied and revert back to the .37-2 packages.  If this fix works for you, I'll update the .65-2 packages to include those files, even though Samsung has removed them from their installer.

If it does not work, the problem is most likely something subtle with the new udev approach Samsung is using, and I'll see what I can figure out when I have a chance.  If anyone has a working scanner with the .65 packages, please let me know.

I've discovered some other (non-critical) problems with the latest driver, and so will be adapting the packages in the next few days anyway.  At that point, I may split the .37 packages into a "legacy" or some other path, which will simplify remaining at the old version when I package an update.

---

### Post by tweedledee on 2010-01-04
> **Sir_Patrick said:**
> I removed myself from group lp and after a restart added myself again, after this i made a restart and tried again but no luck with xsane and my scanner (clx-3175).

Also i updated to the newest version in the repository but no luck either.
I also tried with the same computer to run a live cd of ubuntu 9.04 and added the repo's and it worked directly, the scanner directly worked with xsane.

For me it is an issue with Ubuntu 9.10 somehow something is changed with Karmic and it doesn't work for me.

I hope that i can solve this as i want to use my scanner with Ubuntu and not with the version of windows 7 that came with my pc (in wich the printer and scanner work flawlessly).

I'm not immediately aware of anything that should lead to this problem.  Can (or have you) tried 9.10 with the .37-2 packages, using force version?  And if not, does that mean that you had success with the .65-2 packages with your scanner and the 9.04 live cd?

---

### Post by martach on 2010-01-05
> **tweedledee said:**
> If you are inclined, could you please try the following:
1. copy /usr/lib/sane/libsane-mfp* to a temporary location
2. switch back to the new packages
3. copy (as root) the libsane-mfp* files back to /usr/lib/sane/
4. see if your scanner works

Either way, then remove the files you copied and revert back to the .37-2 packages.  If this fix works for you, I'll update the .65-2 packages to include those files, even though Samsung has removed them from their installer.

If it does not work, the problem is most likely something subtle with the new udev approach Samsung is using, and I'll see what I can figure out when I have a chance.  If anyone has a working scanner with the .65 packages, please let me know.

I've discovered some other (non-critical) problems with the latest driver, and so will be adapting the packages in the next few days anyway.  At that point, I may split the .37 packages into a "legacy" or some other path, which will simplify remaining at the old version when I package an update.

After copying the files back, the scanner works again, even with the new drivers. However, the files I copied were /usr/lib/sane/libsane-smfp* (notice the extra s), since no files matching libsane-mfp* could be found in the above directory.

Thank you for your help.

---

### Post by tweedledee on 2010-01-05
> **martach said:**
> After copying the files back, the scanner works again, even with the new drivers. However, the files I copied were /usr/lib/sane/libsane-smfp* (notice the extra s), since no files matching libsane-mfp* could be found in the above directory.

Thank you for your help.

The most updated packages should now work fine.  Turns out the needed sane libraries are only sometimes present in the downloads from Samsung, and the particular download I grabbed for .65 was missing them.

---

### Post by jamb on 2010-01-06
> **tweedledee said:**
> The most updated packages should now work fine.  Turns out the needed sane libraries are only sometimes present in the downloads from Samsung, and the particular download I grabbed for .65 was missing them.

Hi, 
I updated my system with update-manager this morning, and got this error message when the latest samsungmfp-driver package was in the process being installed.
> 
E: /var/cache/apt/archives/samsungmfp-driver_3.00.65_amd64.deb: trying to overwrite ''/etc/udev/rules.d/99_smfpautoconf_samsung.rules', which is also in package samsungmfp-data 0 


Here is the complete screen output during the update:
> 
(Reading database ... 117466 files and directories currently installed.)
Preparing to replace libgssapi-krb5-2 1.7dfsg~beta3-1 (using .../libgssapi-krb5-2_1.7dfsg~beta3-1ubuntu0.1_amd64.deb) ...
Unpacking replacement libgssapi-krb5-2 ...
Preparing to replace libkrb5-3 1.7dfsg~beta3-1 (using .../libkrb5-3_1.7dfsg~beta3-1ubuntu0.1_amd64.deb) ...
Unpacking replacement libkrb5-3 ...
Preparing to replace libkrb5support0 1.7dfsg~beta3-1 (using .../libkrb5support0_1.7dfsg~beta3-1ubuntu0.1_amd64.deb) ...
Unpacking replacement libkrb5support0 ...
Preparing to replace libk5crypto3 1.7dfsg~beta3-1 (using .../libk5crypto3_1.7dfsg~beta3-1ubuntu0.1_amd64.deb) ...
Unpacking replacement libk5crypto3 ...
Preparing to replace samsungmfp-driver 3.00.65-2 (using .../samsungmfp-driver_3.00.65-3_amd64.deb) ...
Unpacking replacement samsungmfp-driver ...
dpkg: error processing /var/cache/apt/archives/samsungmfp-driver_3.00.65-3_amd64.deb (--unpack):
 trying to overwrite '/etc/udev/rules.d/99_smfpautoconf_samsung.rules', which is also in package samsungmfp-data 0:3.00.65-2
udev start/running, process 2295
Preparing to replace samsungmfp-scanner 3.00.65-2 (using .../samsungmfp-scanner_3.00.65-3_all.deb) ...
Unpacking replacement samsungmfp-scanner ...
Preparing to replace samsungmfp-configurator-qt3 3.00.65-2 (using .../samsungmfp-configurator-qt3_3.00.65-3_amd64.deb) ...
Unpacking replacement samsungmfp-configurator-qt3 ...
Preparing to replace samsungmfp-configurator-data 3.00.65-2 (using .../samsungmfp-configurator-data_3.00.65-3_all.deb) ...
Unpacking replacement samsungmfp-configurator-data ...
Preparing to replace samsungmfp-data 3.00.65-2 (using .../samsungmfp-data_3.00.65-3_all.deb) ...
Unpacking replacement samsungmfp-data ...
Processing triggers for desktop-file-utils ...
Errors were encountered while processing:
 /var/cache/apt/archives/samsungmfp-driver_3.00.65-3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up samsungmfp-data (3.00.65-3) ...
Setting up libkrb5support0 (1.7dfsg~beta3-1ubuntu0.1) ...

Setting up samsungmfp-scanner (3.00.65-3) ...

Setting up libk5crypto3 (1.7dfsg~beta3-1ubuntu0.1) ...

Setting up libkrb5-3 (1.7dfsg~beta3-1ubuntu0.1) ...

Setting up libgssapi-krb5-2 (1.7dfsg~beta3-1ubuntu0.1) ...

Setting up samsungmfp-configurator-data (3.00.65-3) ...
Setting up samsungmfp-configurator-qt3 (3.00.65-3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place


I hope this gives some usable information.

---

### Post by mpstevens_uk on 2010-01-06
I get the same problem as the previous poster - my system is a 32 bit debian 5.0 install.

---

### Post by tweedledee on 2010-01-06
> **mpstevens_uk said:**
> I get the same problem as the previous poster - my system is a 32 bit debian 5.0 install.

Uninstall exisiting packages, then reinstall rather than updating.  Depending on the order apt decides to process packages, it can lead to this error to some files moving between packages.

---

### Post by Sir_Patrick on 2010-01-06
> **tweedledee said:**
> I'm not immediately aware of anything that should lead to this problem.  Can (or have you) tried 9.10 with the .37-2 packages, using force version?  And if not, does that mean that you had success with the .65-2 packages with your scanner and the 9.04 live cd?

Yes i have tried the previous packages .37-2 (legacy) i had them installed before and i reinstalled them but again no result.
I also tried a Ubuntu 9.10 live-cd to try if this has any result but again no success.

I tried it on my laptop with ubuntu 9.10 but also no success with either the .37-2 nor the .65-2 package

The only people (on the dutch ubuntu forum) that had succes with this type of printer had the clx-3175n and had succes scanning over the network not directly via usb.

The Ubuntu 9.04 live-cd that i tried had trouble with the .65-2 package, when i forced the .37-2 package it was working fine again.

Are there people with the clx-3175 hooked-up via usb that have a working scanner with Ubuntu 9.10 (Karmic) on this forum?
Until now i have 1 desktop pc and one laptop with Ubuntu 9.10 installed, on both machines it does not work...

---

### Post by P-Man on 2010-01-06
I am new to Linux and am a novice at programming.

I am running Ubuntu 9.10 on an old compaq deskpro P2 with 750mb RAM.

I tried the solution outlined in the first thread and I used GUI to do everything, but I am still getting the same error message when printing just a test page:

SPL-C Error - Please use the proper driver
Position: 0x0 (0)
System: src/xl_image
Line: 606
Version: Spl-C 5.35 11-20-2007

Could you please instruct me keeping in mind my first statement?

Thanks very much.

---

### Post by tweedledee on 2010-01-06
> **Sir_Patrick said:**
> The only people (on the dutch ubuntu forum) that had succes with this type of printer had the clx-3175n and had succes scanning over the network not directly via usb.

Ah; that is an interesting point.  There have been issues in the past with apparmor blocking particular USB printers, and so that could be the issue (there are still several outstanding bugs in launchpad on this issue).  In a terminal try this:
```
sudo /etc/init.d/apparmor stop
```
Then try your printer/scanning again and see if you have any success.  After evaluating the issue, run
```
sudo /etc/init.d/apparmor start
```
to reactive apparmor.

If this is the problem, I can't really help besides telling you to turn apparmor off entirely, as it's not available for Debian (and I wouldn't be running it even if it were; apparmor is one of the things that caused me to stop using Ubuntu).  In this case, you can start here to try to decide what you might want to try to do: [https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor).

If stopping apparmor does not help, then I'll see if I can come up with any other ideas.

---

### Post by tweedledee on 2010-01-06
> **P-Man said:**
> I tried the solution outlined in the first thread and I used GUI to do everything, but I am still getting the same error message when printing just a test page:

Which solution did you use, my repository or a different approach?  What is your printer model?

I'm guessing that you in fact have the wrong driver installed, although it may seem to be correct.  I have this issue with foomatic, which is why I don't use it with my printer (among other reasons).  Try adding a new printer again and seeing if there are multiple driver options listed for your printer.  Depending on what you have installed, your printer may even appear in the list under a couple of very similar names, and hence different drivers.

---

### Post by martach on 2010-01-07
> **Sir_Patrick said:**
> Yes i have tried the previous packages .37-2 (legacy) i had them installed before and i reinstalled them but again no result.
I also tried a Ubuntu 9.10 live-cd to try if this has any result but again no success.

I tried it on my laptop with ubuntu 9.10 but also no success with either the .37-2 nor the .65-2 package

The only people (on the dutch ubuntu forum) that had succes with this type of printer had the clx-3175n and had succes scanning over the network not directly via usb.

The Ubuntu 9.04 live-cd that i tried had trouble with the .65-2 package, when i forced the .37-2 package it was working fine again.

Are there people with the clx-3175 hooked-up via usb that have a working scanner with Ubuntu 9.10 (Karmic) on this forum?
Until now i have 1 desktop pc and one laptop with Ubuntu 9.10 installed, on both machines it does not work...

For me CLX-3175N works fine via USB under Karmic, both printing and scanning. I first used the .37-2 packages, then upgraded to .65-2, and by using tweedledee's method (described on the previous page), the scanner began to work with .65-2 packages.

Later, I upgraded to .65-3, and my scanner keeps on working (via USB - I haven't tried scanning over a network).

---

### Post by Sir_Patrick on 2010-01-07
> **tweedledee said:**
> Ah; that is an interesting point.  There have been issues in the past with apparmor blocking particular USB printers, and so that could be the issue (there are still several outstanding bugs in launchpad on this issue).  In a terminal try this:
```
sudo /etc/init.d/apparmor stop
```Then try your printer/scanning again and see if you have any success.  After evaluating the issue, run
```
sudo /etc/init.d/apparmor start
```to reactive apparmor.

If this is the problem, I can't really help besides telling you to turn apparmor off entirely, as it's not available for Debian (and I wouldn't be running it even if it were; apparmor is one of the things that caused me to stop using Ubuntu).  In this case, you can start here to try to decide what you might want to try to do: [https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor).

If stopping apparmor does not help, then I'll see if I can come up with any other ideas.

Tried the scanner with apparmor turned off but no change, so far i tried it with both packages.
I don't have acces to my laptop right now but i wil give it a try on that machine also.

---

### Post by P-Man on 2010-01-07
> **tweedledee said:**
> Which solution did you use, my repository or a different approach? What is your printer model?
 
I'm guessing that you in fact have the wrong driver installed, although it may seem to be correct. I have this issue with foomatic, which is why I don't use it with my printer (among other reasons). Try adding a new printer again and seeing if there are multiple driver options listed for your printer. Depending on what you have installed, your printer may even appear in the list under a couple of very similar names, and hence different drivers.
 
 
Printer:
Samsung CLP-310N
connected over a network
 
First, I added your repository through software centre then I installed the drivers through Synaptic.
 
I've tried deleting and adding the printer several times and I'm not given a choice on drivers. All I get is a list of network printers then the next window allows me to name the printer. In these attempts I've tried:
- changing the connection from IPP to LPD. 
- adding the printer by using the IP address. 
- installing the legacy drivers. 
- installing your scanning and other printer drivers
 
It may be that, as i'm just learning, I didn't set something up correctly to allow the GUI to find your drivers.
 
Thanks for your interest and hopefully solution.

---

### Post by tweedledee on 2010-01-10
> **Sir_Patrick said:**
> Tried the scanner with apparmor turned off but no change, so far i tried it with both packages.
I don't have acces to my laptop right now but i wil give it a try on that machine also.

I'm not sure what the problem could be, except perhaps some more obscure configuration issue or a possible issue with the hardware itself (cable, connection, etc.).  Usually getting everything to work over the network is harder, and given martach's post about getting it to work directly on USB, I can't identify any obvious solution.

---

### Post by tweedledee on 2010-01-10
> **P-Man said:**
> I've tried deleting and adding the printer several times and I'm not given a choice on drivers. All I get is a list of network printers then the next window allows me to name the printer. In these attempts I've tried:
- changing the connection from IPP to LPD. 
- adding the printer by using the IP address. 
- installing the legacy drivers. 
- installing your scanning and other printer drivers

It's possible you are using a different GUI than I do.  I'm using system-config-printer, which appears as System > Administration > Printing.  When creating a new printer there, you should be able to select the connection type and specify the printer, then hit "next" (and not "verify" or anything else that would trigger auto-configuration) to select the driver, first from a manufacturer and then the specific one.  It may also help to have the printer off or not connected during this phase, so that none of the "helpful" automatic tools can kick in.  It sounds me to like something is auto-selecting a foomatic driver, which are hit-or-miss with the CLP printers.

If none of what I've described is at all relevant, describe what interface you are using and I'll see if I can identify the source of the problem.

---

### Post by Sir_Patrick on 2010-01-10
> **tweedledee said:**
> I'm not sure what the problem could be, except perhaps some more obscure configuration issue or a possible issue with the hardware itself (cable, connection, etc.).  Usually getting everything to work over the network is harder, and given martach's post about getting it to work directly on USB, I can't identify any obvious solution.

I also tried the scanner with my laptop but so far no luck in finding it, tried also both packages.
If my usb cable is defect then can i still print with my printer? because this part works fine.
I used the same usb cable as on my canon mp160 multifunctional which by the way works fine both the scanner as the printer part on 9.10.
But i will also try a new usb cable to see if that will make a difference.

Thanks tweedledee for your support.


p.s. i also tried virtualbox with winxp and the windows samsung drivers, it found the scanner right away and i scanned a document without a problem.
So the usb cable is fine.

---

### Post by erothoff on 2010-01-12
I have a Samsung SCX-4100, and am having problems getting the scanner to work.  (The printer works fine with Splix, where I selected the driver for the SCX-4200, and after it was installed, it reports to be for the SCX-4100.)  The Printer Configuration says that it is on port usb://Samsung/SCX-4100%20Series, but lsusb says that it is on usb/lp0. 

I have tried using your Deb files, and installing the files that were downloaded directly from the web site.  While I usually could get the printer to work, I could not get it to find the scanner. Most of the time, the Unified Printer Driver would install the printer at mfp:/dev/mfp/4 (which didn't work) or something like that.

I can get the scanner to work using Virtual Box with USB support and a windows scanner driver, so it has to be that the driver either isn't getting installed correctly, or more likely, the scanning program, Xsane is looking for the scanner in a different place than where the driver was installed.  I am running Ubuntu 9.10 amd64. (A clean install)

And suggestions would be greatly appreciated.

---

### Post by tweedledee on 2010-01-12
> **erothoff said:**
> I can get the scanner to work using Virtual Box with USB support and a windows scanner driver, so it has to be that the driver either isn't getting installed correctly, or more likely, the scanning program, Xsane is looking for the scanner in a different place than where the driver was installed.  I am running Ubuntu 9.10 amd64. (A clean install)

(Also directed to Sir_Patrick) If it works with Virtualbox, then it's either a permissions problem or an issue where the scanning software expects the scanner to be in a different location than the OS is putting it.  

Try adding yourself to the "lp", "scanner", and "saned" groups, loggin out and back in, and trying the scanner.  If it works, you can remove yourself one at a time from each group to see which one actually matters.

If that doesn't help, try scanimage or xsane as root; if that works, it's still just a permissions issue somewhere, although perhaps one the device itself rather than an issue with groups.

---

### Post by Sir_Patrick on 2010-01-13
> **tweedledee said:**
> (Also directed to Sir_Patrick) If it works with Virtualbox, then it's either a permissions problem or an issue where the scanning software expects the scanner to be in a different location than the OS is putting it.  

Try adding yourself to the "lp", "scanner", and "saned" groups, loggin out and back in, and trying the scanner.  If it works, you can remove yourself one at a time from each group to see which one actually matters.

If that doesn't help, try scanimage or xsane as root; if that works, it's still just a permissions issue somewhere, although perhaps one the device itself rather than an issue with groups.

I did not find the "scanner" group, i am already  activated in the "lp" and "saned"groups.

When i do scanimage this is the output:

```
patrick@patrick-desktop:~$ scanimage
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
scanimage: no SANE devices found

```

or scanimage -L :

```
patrick@patrick-desktop:~$ scanimage -L
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

Running xsane as root makes no difference for me.

---

### Post by tweedledee on 2010-01-16
> **Sir_Patrick said:**
> Running xsane as root makes no difference for me.

It's a long shot, but perhaps the permissions on the device file itself are wrong.  Can you you check what the permissions are on the "files" in /dev/bus/usb/XXX?  Here, XXX will be 001 if your output from sane-find-scanner is libusb:001:003, and the relevant device in the directory will be the "003" one.  Adjust accordingly.  If the permissions aren't rw for at least root (and perhaps the lp/some other group), then that could be the problem.

You might also have some luck with trying to force scan-image to use a particular device/port (you'll need to read the man page, I think the relevant option is --device).

Otherwise I'm currently out of ideas; perhaps it's worth looking for bug reports on libsane, scan-image, and/or xsane to see if there's some general bug at work here?

---

### Post by sixty2ndidiot on 2010-01-16
Samsung ML-1710 used to work with Gutsy/Cups.  The printer is connect via USB to an SMC router, so that it can be accessed as a network lpd printer.  Works from Windows. Used to work from Gutsy. Now I have a new install of 
"You are using Ubuntu 9.10 - the Karmic Koala - released in October 2009 and supported until April 2011." 
root@ub1:/etc# uname -a
Linux ub1 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux

Configured cups, attempt print test page. Works fine for my other network printer
Brother MFC-490cw.
I've tried both the included Samsung ML-1710 drivers, foomatic and Splx.  Also tried downloaded drivers from Samsung's site.  same result.  the relevant section of /var/log/cups/error_log is below, indicating the printer returns an error message, I've highlighted what i think is the main symptom.  Any suggestions? 

D [16/Jan/2010:15:31:55 -0800] [Job 27] STATE: -connecting-to-device
D [16/Jan/2010:15:31:55 -0800] cupsdMarkDirty(-----S)
I [16/Jan/2010:15:31:55 -0800] [Job 27] Connected to printer...
D [16/Jan/2010:15:31:55 -0800] [Job 27] Connected to 192.168.68.1:515 (IPv4) (local port 1023)...
D [16/Jan/2010:15:31:55 -0800] [Job 27] lpd_command 02
D [16/Jan/2010:15:31:55 -0800] [Job 27] Sending command string (2 bytes)...
D [16/Jan/2010:15:31:55 -0800] [Job 27] Reading command status...
D [16/Jan/2010:15:31:55 -0800] cupsdMarkDirty(-----S)
D [16/Jan/2010:15:31:55 -0800] Discarding unused job-progress event...
_**D [16/Jan/2010:15:31:56 -0800] [Job 27] lpd_command returning 108**_
D [16/Jan/2010:15:31:56 -0800] PID 3899 (/usr/lib/cups/backend/lpd) stopped with status 1!
I [16/Jan/2010:15:31:56 -0800] [Job 27] Backend returned status 1 (failed)
D [16/Jan/2010:15:31:56 -0800] set_hold_until: hold_until = 1263685016
D [16/Jan/2010:15:31:56 -0800

---

### Post by tweedledee on 2010-01-17
> **sixty2ndidiot said:**
> 
_**D [16/Jan/2010:15:31:56 -0800] [Job 27] lpd_command returning 108**_
D [16/Jan/2010:15:31:56 -0800] PID 3899 (/usr/lib/cups/backend/lpd) stopped with status 1!

When you get an error of status 1 almost immediately, it often means that the printer failed to print at some earlier point, and CUPS switched it to "stopped" status.  Unfortunately, this then means that all subsequent jobs will fail, and I don't really understand why this is default behavior.

If you go to the printer options, then the "policies" set of options, you should see whether or not the printer is enabled and accepting jobs (both should be checked/active).  If either is not correct, chances are that's your problem, and you may want to consider changing the default error policy (although if this is an infrequent occurence, you can just leave it as-is).

This may not be your problem, especially if you've been adding new printers rather than changing the options of a single printer each time you added a new driver.  If so, it's still almost certainly a CUPS configuration problem rather than anything to do with the printer or the driver, and you should try a Google search on the error message to see what turns up that is similar to your situtation.  CUPS errors are often difficult to interpret, but I find that someone has usually worked it out.

---

### Post by sixty2ndidiot on 2010-01-17
I checked the policies as suggested.  Everything looks fine.  I think cupsd is communicating with the printer at  192.168.68.1:515, it sends some bytes, reads back some,  status=108 which results in a return status of 1, which is its way of saying the backend failed.
So the printer is telling CUPSD that it doesn't like the command it sent, either because the command is bad, or the printer is no in a state to accept the command.......
Still doesn't help me to get past this problem.
Spent considerable time googling to no avail.
.....

---

### Post by Sir_Patrick on 2010-01-17
> **tweedledee said:**
> It's a long shot, but perhaps the permissions on the device file itself are wrong.  Can you you check what the permissions are on the "files" in /dev/bus/usb/XXX?  Here, XXX will be 001 if your output from sane-find-scanner is libusb:001:003, and the relevant device in the directory will be the "003" one.  Adjust accordingly.  If the permissions aren't rw for at least root (and perhaps the lp/some other group), then that could be the problem.

You might also have some luck with trying to force scan-image to use a particular device/port (you'll need to read the man page, I think the relevant option is --device).

Otherwise I'm currently out of ideas; perhaps it's worth looking for bug reports on libsane, scan-image, and/or xsane to see if there's some general bug at work here?

This is what i can see in dev/bus/usb/001/003 : see attachement

I changed the group to "saned" and "lp" but that makes no difference

The force scan-image i have to look up in the man pages of sane, i will try this option and see what happens.
I also am now out of options and i do not understand how other people can get their samsung scanner working in 9.10.
It doesn't work for me on 2 computers, thank you for your help so far.

---

### Post by tweedledee on 2010-01-18
> **sixty2ndidiot said:**
> I checked the policies as suggested.  Everything looks fine.  I think cupsd is communicating with the printer at  192.168.68.1:515, it sends some bytes, reads back some,  status=108 which results in a return status of 1, which is its way of saying the backend failed.
So the printer is telling CUPSD that it doesn't like the command it sent, either because the command is bad, or the printer is no in a state to accept the command.......
Still doesn't help me to get past this problem.
Spent considerable time googling to no avail.
.....

It still sounds like a CUPS problem rather than a printer driver issue to me.  You could try changing the permission options in /etc/cups/cupsd.conf to see if there's something odd there.  Otherwise, it's probably worth filing a bug in launchpad to see if anyone else has ideas.

---

### Post by tweedledee on 2010-01-18
> **Sir_Patrick said:**
> This is what i can see in dev/bus/usb/001/003 : see attachement

I changed the group to "saned" and "lp" but that makes no difference

The force scan-image i have to look up in the man pages of sane, i will try this option and see what happens.
I also am now out of options and i do not understand how other people can get their samsung scanner working in 9.10.
It doesn't work for me on 2 computers, thank you for your help so far.

If you can't force it, I'd suggest filing a bug in launchpad to see if anyone else has ideas, or knows of some configuration change from 9.04 to 9.10 that could cause this.

---

### Post by speedygeo on 2010-01-19
Please, have anyone a link or the files for Samsung SCX-4100/4200 or Xerox WC 3119?
I'm googling for them, but seems samsung and xerox removed them from their servers.
I'm looking for Samsung Unified Driver or WC3119 Linux Driver.
I know about the repo for the first. But I want the files too to help a friend with another distro.

---

### Post by sixty2ndidiot on 2010-01-19
> **tweedledee said:**
> It still sounds like a CUPS problem rather than a printer driver issue to me.  You could try changing the permission options in /etc/cups/cupsd.conf to see if there's something odd there.  Otherwise, it's probably worth filing a bug in launchpad to see if anyone else has ideas.

Finally solved the problem (by reviewing my older installation):
I needed to change the URL of the printer from
lpd://192.168.68.1

to
lpd://192.168.68.1/lpt1

I guess the SMC router needs the lpt1 to correctly connect the lpd request to the USB printer connected to it.

---

### Post by m10 on 2010-01-19
I have a **clx-3175** and am on Ubuntu **9.10** KK..

I'll tell you my story!

I found this howto (thank you!) only after having already downloaded and installed the drivers(3.00.65) from the samsung page.
I had the same problem as described in a post [here]("http://ubuntuforums.org/showpost.php?p=7866608&postcount=315") in this thread (printing is waaay to dark!).

I tried various color adjustments via the configuration tool provided by samsung getting only a slight improvement (barely noticeable).

I tried to adjust the brightness/darkness in the cups settings(%) and in the samsung tool(light-normal-dark) getting no change at all. (note: there is an option in samsung's tool to print a "configuration report" which prints out various settings and their values and the darkness is **always** set to normal no matter how it is set in the conf tools, while the other settings i changed(e.g.color) did print out correctly)

I also tried various programs and file formats confirming the same behavior with all of them (images,odf,pdf).
I still hadn't try the scanner, and i didn't expect it to work flawlessly having seen the issues that other people had..

Now there comes the **awesome** part (thank you!).

I added your **awesome** repository, downloaded the drivers (again version 3.00.65) from your **awesome **repository as it seemed the most suggested way of installing the drivers (i already uninstalled the 'official' samsung drivers following the **awesome** howto - note: some files did not exist that i should have removed + i found an entry(smartpanel) in the startup applications that was added by (one of) the installer(s) that wasn't mentioned in your **awesome** howto).

At this point I wanted to ask here for more help as I didn't expect any change at all..(even if i did re-change some saturation and brightness settings in the cups settings)
But it just occurred to me to print something out and **BANG!** superüber quality! no strange dark printings anymore!!
I thought "WOW!this repository indeed is **awesome**!";).
Next i wanted to get scanning working.
I fired up XSane and BANG! again! works flawlessly with your **awesome **repository!

So **THANK YOU! SO MUCH!**
Keep up with the great work!
It's because of people like you that using OSS is so **awesome**!

ps sorry for the maybe to many "**awesome**" but i am just so happy that i got my **awesome** multifunction to work flawlessly with your **awesome** repository and your **awesome** howto!!:p

---

### Post by tweedledee on 2010-01-19
> **speedygeo said:**
> Please, have anyone a link or the files for Samsung SCX-4100/4200 or Xerox WC 3119?
I'm googling for them, but seems samsung and xerox removed them from their servers.
I'm looking for Samsung Unified Driver or WC3119 Linux Driver.
I know about the repo for the first. But I want the files too to help a friend with another distro.

Download the drivers for one of the newer CLX printers, which all have recent Linux drivers provided.  It's the same thing, only the default installed printer changes.  (Note that the CLX series is important, as only the --X printers include the scanning part, the rest have a smaller driver file that leaves that out.)  The Xerox printers aren't officially supported by the Samsung drivers, but the SCX-42xx series should work for that one.

I will also upload my saved copies of the driver files to the repository in a couple of days, as I currently only have access to a slow connection.  You can look there if you don't want to wade through Samsung's site, I will provide the downloads on the main page.

---

### Post by tweedledee on 2010-01-19
> **sixty2ndidiot said:**
> Finally solved the problem (by reviewing my older installation):
I needed to change the URL of the printer from
lpd://192.168.68.1

to
lpd://192.168.68.1/lpt1

I guess the SMC router needs the lpt1 to correctly connect the lpd request to the USB printer connected to it.

I'm glad it was just something that little (but annoying).  Also an example of why I keep records of all my (extensive) customization I do to the base installs.

---

### Post by tweedledee on 2010-01-19
> **m10 said:**
> I have a **clx-3175** and am on Ubuntu **9.10** KK..

I'll tell you my story!

I'm glad it worked so well for you.  It sounds like one of the other Samsung utilties may actually be causing the color balance problems, not the driver itself.  That's a point I will add to my notes.

---

### Post by speedygeo on 2010-01-20
> **tweedledee said:**
> Download the drivers for one of the newer CLX printers  It's the same thing, only the default installed printer changes.  (Note that the CLX series is important, as only the --X printers include the scanning part, the rest have a smaller driver file that leaves that out.) 

Sincerely thank you, keep in touch! ;)

---

### Post by m10 on 2010-01-21
> **tweedledee said:**
> one of the other Samsung utilties may actually be causing the color balance problems, not the driver itself.
I'm not sure if that's the case because at the really beginning, before installing any driver, i tried to setup the printer (foomatic driver?) and it had the same problem..

If it would anyhow help I'm willing to do some testing..
PS: color balancing (saturation,hue,gamma,brightness) doesn't currently work at all

---

### Post by digibill on 2010-01-24
I have the Samsung CLP-315 and just wanted to say a **BIG THANK YOU** for this HOWTO!
By now I tried everything to make my printer work under Ubuntu 9.10 (foo2zjs, SPLIX, samsung cd, ubuntu driver) but none worked! The printer either did not work at all, or worked with lots of problems!
By following this tutorial ([that a member of the greek ubuntu forum pointed out to me]("http://forum.ubuntu-gr.org/viewtopic.php?f=16&t=9576&p=97832#p97832")), everything worked OK and the printer is setup ok!

Again, [SIZE=4][COLOR=Red]**THANKS A LOT!**[/COLOR][/SIZE] :D

---

### Post by clyrrad on 2010-01-26
**[SIZE="5"][COLOR="Red"]TRULY AMAZING - Better Support Than From Samsung!!![/COLOR][/SIZE]**

**WOW:** tweedledee you are a lifesaver.  I was literally going INSANE over this stupid lack of scanner support.

I have the Samsung SCX-4521F and was only ever able to get the printer working.  I installed your REPO's ran the apt-get install commands like you showed, logged out, logged back in and BAMN full scanner support!  No Segmentation Faults with xsane anymore and the printer and scanner are working beautifully.  Thank-you so much for this!!! :D :D :D

---

### Post by digibill on 2010-01-27
Also I would like to add that with this driver, the color management issues of the default samsung driver seem to be resolved! With the samsung driver the printing result seemed to be with lots of gamma! With this driver the result is very close to what you see in the monitor (maybe a little -very little- contrast low, but almost OK!)

---

### Post by tweedledee on 2010-01-27
> **m10 said:**
> I'm not sure if that's the case because at the really beginning, before installing any driver, i tried to setup the printer (foomatic driver?) and it had the same problem..

If it would anyhow help I'm willing to do some testing..
PS: color balancing (saturation,hue,gamma,brightness) doesn't currently work at all

Good to know; I've updated the repository information to reflect the possibility that color balance may improve with different installations for unclear reasons.  I'm guessing it's something subtle with libraries, but don't have a clear idea of what would make sense to test to sort it out.  Whatever it is, it's obviously not unique to you based on digibill's comment.  Hopefully nothing will break this benefit in the future.

And I can't help with the active color balancing at this point, either; regardless of installation type, it's never worked with my printer, so again I don't have a clear idea of what to start testing to identify the issue.  In your case, it may be that the inability to adjust the balance manually is linked to a reasonable default state (i.e., same underlying cause), but that's really just a guess.

---

### Post by rpaton on 2010-02-13
En realidad soy usuario de debian squeeze y he tenido la suerte de caer en este foro buscando una solución para poder ultilizar la función de escaner en una multifunción samsung SCX-4521F. Siguiendo las instrucciones de su tutorial y (creo que principalmente) utilizando los paquetes de su repositorio he llegado por fin a resolver el problema. ¡Muchas gracias!.

---

### Post by mu-omega on 2010-02-18
Congratulations and thanks a lot for a great installation recipe to Samsung devices. I have a Samsung SCX-4828FN combined printer and scanner, and have recently changed from Windows XP to Ubuntu 9.10.  As many others, I am still encountering the problem that the printer is well installed, but the scanner is not working. None of the previous suggestions (also in other forums) helped so far.  XSANE finds the scanner:  sane-find-scanner gives &quot;found USB scanner (vendor=0x04e8 [Samsung Electronics Co., Ltd.], product=0x342d [SCX-4x28 Series]) at libusb:001:013&quot;, but scanimage -L gives &quot;No scanners were identified.&quot;  However, XSANE scanning works well with Samsung scanners (same type), which are installed in the local network. Seems that there is a problem with the USB identification.  Any suggestions, how to solve the problem?

---

### Post by caiobarros on 2010-02-18
I registered at this forum just to say a big Thank You!
I was fighting against my SCX-4200 and this repository worked like a miracle!

---

### Post by tweedledee on 2010-02-18
> **mu-omega said:**
>  However, XSANE scanning works well with Samsung scanners (same type), which are installed in the local network. Seems that there is a problem with the USB identification.  Any suggestions, how to solve the problem?

As best as I can tell, something subtle changed in the USB system implemented by 9.10 that interferes with some (but not all) Samsung MFP scanners connected by USB.  It also appears to affect a few models by other manufacturers; it's possible that there is a solution out there for a different brand that will work, although I didn't see anything when I did a quick search a while ago.  I also think this is limited to Ubuntu 9.10 and not other Debian derivatives, in which case it's a pretty small thing that should be resolvable if it can be identified.  If a search doesn't turn up anything useful, the best I can suggest is to open a Launchpad bug against this to see if someone knows what changed, since it was not documented in the release notes.

It seems unlikely it's directly related to the Samsung driver since it works over the network, unless the driver expect a particular USB configuration and Ubuntu (not for the first time) decided to implement a different USB setup.

---

### Post by Jive Turkey on 2010-02-24
Kudos!  Worked great for me thanks! (samsung 2525w) via ethernet and wireless.

---

### Post by jis on 2010-03-03
I wonder how to install network printer using the IIc approach and system-config-printer 1.1.12? I am trying to install printer CLP-315W using wired network connection. See this video about what is seen in the dialog: [http://iki.fi/8/tmp/network-printer.ogv](http://iki.fi/8/tmp/network-printer.ogv)
I used ipp connection before, but it stopped working, thus reinstalling, and now I can not enable Forward button in the ipp dialog.
If I use the suggested topmost option, I get ab SPL-C Error printed in paper, when printing test page: please use the proper driver.

Edit: Oh, I had to use Samsung CLP-310 Series (SPL-C) driver instead of Foomatic for CLP-310 or CLP-315. This time lpd://192.168.0.103/PASSTHRU worked. I can alternatively install ipp connection, if I empty the Queue field and set 192.168.0.103 as host.

---

### Post by digibill on 2010-03-03
**Question:** In the "Advanced" section of the printer settings dialog when printing, there is an option called "Edge Control". What does this? I've tied printing with this to On and Off and saw no difference.....

Also, one more thing: when I send for printing a document from Openoffice, it seems that every page is spooled after the previous one has printed! So, if I have a document with eg 10 pages, the 1st one is sent to the printer, it is printed, the printer waits for the next page, then the 2nd one is sent to the printer, it's printed etc etc....
Is there a way to spool the whole document at once? ](*,)

---

### Post by masonnj on 2010-03-04
Having followed the guide in the 1st post on this thread I now have a fully working Samsung CLX-2160 printer/scanner so thank you to the OP for a comprehensive and very accurate tutorial. :KS

I only had one moment of panic and that was because I'd not added myself to the lp group. Rather than check I though lp group, line print, I must be a member as the printer works. Once corrected the scanner was there and fully functioning.

Nick

---

### Post by sirpuddingfoot on 2010-03-04
Just wanted to say thanks!

2c did the trick for my new ML-2525W (over the wireless interface).
I installed only the samsungmfp-driver and samsungmfp-data packages.

---

### Post by n3ck on 2010-03-05
Hi there!

I have some issues with my Samsung device (SCX 4521 series). Firstly i have downloaded Samsung Unified Driver v2 (20070720165133984_UnifiedLinuxDriver.tar.gz), installed it by  install.sh script, with almost all sane and cups packages. sane-find-scanner finds my scanner connected to USB, but scanimage -L says, that no scanners were identified, so i've tried to run 

```
scanimage -d smfp:libusb:003:002
```

it fails with segmentation fault error...

Same with v3 drivers (did v2 driver uninstall steps from first post). For now i ran out of ideas how to fix it. There is listing from syslog, and attached output of strace.
```

Mar  5 13:49:59 ubuntu kernel: [ 3034.366102] scanimage[17347]: segfault at 0 ip 00c9bdc4 sp bfcbfbd0 error 4 in libsane-smfp.so.1.0.1[c8a000+44000]
Mar  5 13:54:10 ubuntu kernel: [ 3285.450723] scanimage[17872]: segfault at 0 ip 00d35dc4 sp bfe2e090 error 4 in libsane-smfp.so.1.0.1[d24000+44000]
Mar  5 14:00:02 ubuntu kernel: [ 3637.138254] scanimage[18561]: segfault at 0 ip 00c17dc4 sp bfe0baf0 error 4 in libsane-smfp.so.1.0.1[c06000+44000]

```

My ubuntu is 9.10 server edition. Thanks in advance.

---

### Post by LeFinc on 2010-03-06
sane-find-scanner appears thinks my wireless usb adapter is a scanner.. Even though I've managed to get the wireless to work, scanimage -L comes back with nothing. Scanner used to work before installing this wireless usb adapter. Is there a way to blacklist my wireless adapter for the purposes of (x)sane?


Output below:

```
$ sudo sane-find-scanner -v
This is sane-find-scanner from sane-backends 1.0.20

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

searching for SCSI scanners:
checking /dev/scanner... failed to open (Invalid argument)
checking /dev/sg0... failed to open (Invalid argument)
checking /dev/sg1... failed to open (Invalid argument)
checking /dev/sg2... failed to open (Invalid argument)
checking /dev/sg3... failed to open (Invalid argument)
checking /dev/sg4... failed to open (Invalid argument)
checking /dev/sg5... failed to open (Invalid argument)
checking /dev/sg6... failed to open (Invalid argument)
checking /dev/sg7... failed to open (Invalid argument)
checking /dev/sg8... failed to open (Invalid argument)
checking /dev/sg9... failed to open (Invalid argument)
checking /dev/sga... failed to open (Invalid argument)
checking /dev/sgb... failed to open (Invalid argument)
checking /dev/sgc... failed to open (Invalid argument)
checking /dev/sgd... failed to open (Invalid argument)
checking /dev/sge... failed to open (Invalid argument)
checking /dev/sgf... failed to open (Invalid argument)
checking /dev/sgg... failed to open (Invalid argument)
checking /dev/sgh... failed to open (Invalid argument)
checking /dev/sgi... failed to open (Invalid argument)
checking /dev/sgj... failed to open (Invalid argument)
checking /dev/sgk... failed to open (Invalid argument)
checking /dev/sgl... failed to open (Invalid argument)
checking /dev/sgm... failed to open (Invalid argument)
checking /dev/sgn... failed to open (Invalid argument)
checking /dev/sgo... failed to open (Invalid argument)
checking /dev/sgp... failed to open (Invalid argument)
checking /dev/sgq... failed to open (Invalid argument)
checking /dev/sgr... failed to open (Invalid argument)
checking /dev/sgs... failed to open (Invalid argument)
checking /dev/sgt... failed to open (Invalid argument)
checking /dev/sgu... failed to open (Invalid argument)
checking /dev/sgv... failed to open (Invalid argument)
checking /dev/sgw... failed to open (Invalid argument)
checking /dev/sgx... failed to open (Invalid argument)
checking /dev/sgy... failed to open (Invalid argument)
checking /dev/sgz... failed to open (Invalid argument)
  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

searching for USB scanners:
checking /dev/usb/scanner... failed to open (Invalid argument)
checking /dev/usb/scanner0... failed to open (Invalid argument)
checking /dev/usb/scanner1... failed to open (Invalid argument)
checking /dev/usb/scanner2... failed to open (Invalid argument)
checking /dev/usb/scanner3... failed to open (Invalid argument)
checking /dev/usb/scanner4... failed to open (Invalid argument)
checking /dev/usb/scanner5... failed to open (Invalid argument)
checking /dev/usb/scanner5... failed to open (Invalid argument)
checking /dev/usb/scanner7... failed to open (Invalid argument)
checking /dev/usb/scanner8... failed to open (Invalid argument)
checking /dev/usb/scanner9... failed to open (Invalid argument)
checking /dev/usb/scanner10... failed to open (Invalid argument)
checking /dev/usb/scanner11... failed to open (Invalid argument)
checking /dev/usb/scanner12... failed to open (Invalid argument)
checking /dev/usb/scanner13... failed to open (Invalid argument)
checking /dev/usb/scanner14... failed to open (Invalid argument)
checking /dev/usb/scanner15... failed to open (Invalid argument)
checking /dev/usbscanner... failed to open (Invalid argument)
checking /dev/usbscanner0... failed to open (Invalid argument)
checking /dev/usbscanner1... failed to open (Invalid argument)
checking /dev/usbscanner2... failed to open (Invalid argument)
checking /dev/usbscanner3... failed to open (Invalid argument)
checking /dev/usbscanner4... failed to open (Invalid argument)
checking /dev/usbscanner5... failed to open (Invalid argument)
checking /dev/usbscanner6... failed to open (Invalid argument)
checking /dev/usbscanner7... failed to open (Invalid argument)
checking /dev/usbscanner8... failed to open (Invalid argument)
checking /dev/usbscanner9... failed to open (Invalid argument)
checking /dev/usbscanner10... failed to open (Invalid argument)
checking /dev/usbscanner11... failed to open (Invalid argument)
checking /dev/usbscanner12... failed to open (Invalid argument)
checking /dev/usbscanner13... failed to open (Invalid argument)
checking /dev/usbscanner14... failed to open (Invalid argument)
checking /dev/usbscanner15... failed to open (Invalid argument)
found USB scanner (vendor=0x04e8 [Samsung], product=0x3426 [SCX-4500 Series]) at libusb:001:002
found USB scanner (vendor=0x148f [Ralink], product=0x2573 [802.11 bg WLAN]) at libusb:001:005
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
done
``````
$ sudo scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
```

---

### Post by tweedledee on 2010-03-07
> **digibill said:**
> **Question:** In the "Advanced" section of the printer settings dialog when printing, there is an option called "Edge Control". What does this? I've tied printing with this to On and Off and saw no difference.....
I have no idea; I don't see this option with any printer I've personally used.  I do occasionally see other random options that apparently don't do anything, though.

> **digibill said:**
> Also, one more thing: when I send for printing a document from Openoffice, it seems that every page is spooled after the previous one has printed! So, if I have a document with eg 10 pages, the 1st one is sent to the printer, it is printed, the printer waits for the next page, then the 2nd one is sent to the printer, it's printed etc etc....
Is there a way to spool the whole document at once? ](*,)

This sounds like a problem with your printing system somewhere, as it should spool properly.  Assuming that this only occurs with Openoffice and not every program (it which case it could be the print driver not working well with your printer).  There are multiple "print" programs (lpr, lp, the samsung slpr, etc.), and I don't recall which one Openoffice uses, but if you wanted to pursue problem further you could try working directly with those.

---

### Post by tweedledee on 2010-03-07
> **n3ck said:**
> sane-find-scanner finds my scanner connected to USB, but scanimage -L says, that no scanners were identified,

I think this is the same problem several other users have reported with 9.10.  Something about the usb subsystem and/or kernel and/or something else (?) seems to cause a problem with many or all Samsung MFP scanners when run over USB (but not the network).  The same setups work fine in Debian, so it appears to be something Ubuntu has customized or the particular combination of libraries 9.10 is using.  All I can do is recommend that you open a bug in Launchpad, if one of the people I've recommended this to previously hasn't already done so, in the hopes that it gets resolved for 10.04.

---

### Post by tweedledee on 2010-03-07
> **LeFinc said:**
> sane-find-scanner appears thinks my wireless usb adapter is a scanner.. Even though I've managed to get the wireless to work, scanimage -L comes back with nothing. Scanner used to work before installing this wireless usb adapter. Is there a way to blacklist my wireless adapter for the purposes of (x)sane?

I don't think so, but you may be able to force it to pick up the scanner via a commandline parameter.  However, I'd recommend opening a bug in Launchpad about this; as with several previous posts in the last few months, this suggests there is a problem in the USB subsystem Ubuntu is using in 9.10.

---

### Post by digibill on 2010-03-08
> **tweedledee said:**
> 
This sounds like a problem with your printing system somewhere, as it should spool properly.  Assuming that this only occurs with Openoffice and not every program

With further testing I discovered that this happens with every program.... :(

---

### Post by n3ck on 2010-03-08
> **tweedledee said:**
> I think this is the same problem several other users have reported with 9.10.  Something about the usb subsystem and/or kernel and/or something else (?) seems to cause a problem with many or all Samsung MFP scanners when run over USB (but not the network).  The same setups work fine in Debian, so it appears to be something Ubuntu has customized or the particular combination of libraries 9.10 is using.  All I can do is recommend that you open a bug in Launchpad, if one of the people I've recommended this to previously hasn't already done so, in the hopes that it gets resolved for 10.04.

Okay, but this error caused by ubuntu 9.10 leads to segfault in libsane-smfp.so.1.0.1, or problem is somewhere else?

---

### Post by tweedledee on 2010-03-08
> **n3ck said:**
> Okay, but this error caused by ubuntu 9.10 leads to segfault in libsane-smfp.so.1.0.1, or problem is somewhere else?

The error may be directly arising from libsane-smfp (although the strace isn't conclusive about that; a definite test would require a debug library that isn't available), but the fact that the same library file works fine under Debian systems and Ubuntu 9.04 suggests that the problem is something that changed in Ubuntu, not Samsung.

---

### Post by n3ck on 2010-03-10
Hmm this is very strange. I have no idea what i've done, but it worked. I only remember, that i installed libsane-dbg and libsane-extras-dbg and scanner worked! I wanted to find problem, i've upgraded this packages:

```

cups [1.4.1-5ubuntu2.2 -> 1.4.1-5ubuntu2.4]  cups-common [1.4.1-5ubuntu2.2 -> 1.4.1-5ubuntu2.4]  libcups2 [1.4.1-5ubuntu2.2 -> 1.4.1-5ubuntu2.4]  
  libcupscgi1 [1.4.1-5ubuntu2.2 -> 1.4.1-5ubuntu2.4]  libcupsdriver1 [1.4.1-5ubuntu2.2 -> 1.4.1-5ubuntu2.4]  libcupsimage2 [1.4.1-5ubuntu2.2 -> 1.4.1-5ubuntu2.4]  
  libcupsmime1 [1.4.1-5ubuntu2.2 -> 1.4.1-5ubuntu2.4]  libcupsppdc1 [1.4.1-5ubuntu2.2 -> 1.4.1-5ubuntu2.4]  linux-generic-pae [2.6.31.19.32 -> 2.6.31.20.33]  
  linux-headers-generic-pae [2.6.31.19.32 -> 2.6.31.20.33]  linux-image-generic-pae [2.6.31.19.32 -> 2.6.31.20.33]  linux-libc-dev [2.6.31-19.56 -> 2.6.31-20.57]

```

reboot, and problem appeared again. Is it possible that newer cups or linux kernel is the problem?


Add:

I figured out, that when scanimage tries to access my scanner device, it gets error message: "Inappropriate ioctl for device".


Edit:

New kernel is compiled without CONFIG_USB_DEVICEFS set, and this is the only differ between these two kernels. It works now ;)

---

### Post by nuffy on 2010-03-10
Hi.... I have been having problems with CUPS and have searched and searched for weeks trying to sort the problem out.

Just came across this thread and I hope someone here can assist me?

I have an issue with CUPS in that each time I boot my pc the CUPS printer configuration is lost.

I have reinstalled everything I can find in Synaptic Update Manager relating to CUPS, the printer appears in CUPS and system-config-printer and I can print once again...... however, when I reboot or shutdown and boot up, CUPS is gone! 

BTW, I have a Samsung CLP300 colour laser connected to a Netgear wireless print server .... the print server is not operating wirelessly, I have it connected via wired network.  Printing works with this configuration for a WinXP laptop.

This issue has only surfaced in the past couple of weeks, so I guess it may have something to do with a recent update of some sort??

I have tried the tutorial on page one of this thread but I am sad to say the same problem persists.... CUPS somehow is uninstalled.

Waiting with bated breath.... Nuffy

---

### Post by tweedledee on 2010-03-10
> **n3ck said:**
> New kernel is compiled without CONFIG_USB_DEVICEFS set, and this is the only differ between these two kernels. It works now ;)

To clarify: does it work with CONFIG_USB_DEVICEFS set on or off (the -19 or -20 kernel release)?  It appears that Ubuntu developers have been flipping the setting back and forth during the 9.10 cycle, which explains much of the erratic behavior being reported.  If it works with the parameter off, then the problem is solved and should remain that way.  If it works with it on, then alternative options need to be explored.

For relevant launchpad discussions, see:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417748](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417748)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/488274](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/488274)

---

### Post by tweedledee on 2010-03-10
> **nuffy said:**
> I have an issue with CUPS in that each time I boot my pc the CUPS printer configuration is lost.

It sounds like you have a problem similar or identical to one of these reports in launchpad:
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/524186](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/524186)
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/530324](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/530324)

I would work through launchpad rather the forums, as it almost certainly is a bug introduced in a recent CUPS update and doesn't have anything to do with your printer in particular.

---

### Post by nuffy on 2010-03-11
yeah thanks tweedledee,

I found 'sudo service cups start' restarts CUPS and my printer is visible and I can use it.

Now all I have to figure out is how to automate this process.... any clues?

Ta......nuffy

---

### Post by tweedledee on 2010-03-11
> **nuffy said:**
> yeah thanks tweedledee,

I found 'sudo service cups start' restarts CUPS and my printer is visible and I can use it.

Now all I have to figure out is how to automate this process.... any clues?

Ta......nuffy

The simplest and crudest approach is to just add that line to your list of startup applications, so that you just enter your password when prompted after login and it is done.  The service should be automatically started by upstart during boot, so you can also look at those scripts or add a new one that runs at the end to trigger cups.  I've not used any recent versions of upstart, but there is plenty of information available from Ubuntu and via Google.  Based on the existing bug reports for this, I would also guess it will be resolved sometime soon, since it's probably just some strange conflict of services during boot.

---

### Post by n3ck on 2010-03-15
> **tweedledee said:**
> To clarify: does it work with CONFIG_USB_DEVICEFS set on or off (the -19 or -20 kernel release)?  It appears that Ubuntu developers have been flipping the setting back and forth during the 9.10 cycle, which explains much of the erratic behavior being reported.  If it works with the parameter off, then the problem is solved and should remain that way.  If it works with it on, then alternative options need to be explored.

For relevant launchpad discussions, see:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417748](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417748)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/488274](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/488274)

So, I've checked it and answer is simple: with option USB_DEVICEFS=y (kernel 2.6.30.10) scanner works well. Without this kernel option (newest generic ubuntu kernel package), scanimage does not detects my scanner.

---

### Post by tweedledee on 2010-03-15
> **n3ck said:**
> So, I've checked it and answer is simple: with option USB_DEVICEFS=y (kernel 2.6.30.10) scanner works well. Without this kernel option (newest generic ubuntu kernel package), scanimage does not detects my scanner.

To everyone who has posted with USB scanner difficulties over the last few months: this is your problem.  (And why they've always worked under Debian, which has this option enabled.)  I have updated the first post to include this information and indicate how you can work around it, but none of the solutions are trivial.  And please don't ask for assistance on how to compile your own kernel, there are many guides available.

---

### Post by ezekiel_quacks on 2010-03-18
> **tweedledee said:**
> To everyone who has posted with USB scanner difficulties over the last few months: this is your problem.  (And why they've always worked under Debian, which has this option enabled.)  I have updated the first post to include this information and indicate how you can work around it, but none of the solutions are trivial.  And please don't ask for assistance on how to compile your own kernel, there are many guides available.

I found an alternative workaround for this issue on my Samsung SCX-4300 yesterday, and thought I'd share the wealth. It turns out that the Xerox MFP driver in libsane seems to work with some other scanners, including the Samsung SCX-4200 and SCX-4300. The original post where I found out about this is [http://old.nabble.com/the-samsung-scx-4200-works-with-the-xerox-mfp-driver-td24196559.html](http://old.nabble.com/the-samsung-scx-4200-works-with-the-xerox-mfp-driver-td24196559.html).

With a little bit of tinkering, I got this to work on my SCX-4300. All I needed to do was edit /etc/sane.d/xerox_mfp.conf, adding these lines:

```
#Samsung SCX-4300 
usb 0x04e8 0x342e
```and then edit /lib/udev/rules.d/40-libsane.rules, inserting these lines toward the end of the file:

```
# Samsung SCX4300
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="342e", ENV{libsane_matched}="yes"
```I don't know if there are other issues that might arise from using this driver, but it's easier than recompiling my kernel! :)

---

### Post by tweedledee on 2010-03-22
> **ezekiel_quacks said:**
> I found an alternative workaround for this issue on my Samsung SCX-4300 yesterday, and thought I'd share the wealth.

Thanks for sharing.  I've updated the main guide to include this information.

---

### Post by n3ck on 2010-03-23
> **ezekiel_quacks said:**
> I found an alternative workaround for this issue on my Samsung SCX-4300 yesterday, and thought I'd share the wealth. It turns out that the Xerox MFP driver in libsane seems to work with some other scanners, including the Samsung SCX-4200 and SCX-4300. The original post where I found out about this is [http://old.nabble.com/the-samsung-scx-4200-works-with-the-xerox-mfp-driver-td24196559.html](http://old.nabble.com/the-samsung-scx-4200-works-with-the-xerox-mfp-driver-td24196559.html).

With a little bit of tinkering, I got this to work on my SCX-4300. All I needed to do was edit /etc/sane.d/xerox_mfp.conf, adding these lines:

```
#Samsung SCX-4300 
usb 0x04e8 0x342e
```and then edit /lib/udev/rules.d/40-libsane.rules, inserting these lines toward the end of the file:

```
# Samsung SCX4300
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="342e", ENV{libsane_matched}="yes"
```I don't know if there are other issues that might arise from using this driver, but it's easier than recompiling my kernel! :)


I've checked your advice, and scanner is working at the first time only. When i type scanimage -L at first time after reboot, scanner is found. But when i type scanimage -L again, scanner is now not found ;( I try to restart udev, saned, but nothing fixes the problem.

---

### Post by n3ck on 2010-03-24
Okay, i found another workaround. 

The thing is, you have to bind /dev/bus dir to /proc/bus, but in the way that do not overwrite /proc/bus data. So, i've wrote a little init.d script, that does all work for us. 

```

#! /bin/sh
# Samsung scanner procfs hack script 
#

case $1 in
        start)
            for dir in `ls /proc/bus`;
            do
                mkdir /dev/bus/$dir > /dev/null 2>&1;
                mount --bind /proc/bus/$dir /dev/bus/$dir ;
            done;
            mount --bind /dev/bus /proc/bus;
            ln -s /sys/kernel/debug/usb/devices /proc/bus/usb/devices;
            echo "procfs scanner hack is active \n";
        ;;
        stop)
            rm /proc/bus/usb/devices > /dev/null 2>&1;
            umount /proc/bus > /dev/null 2>&1;
            for dir in `ls /dev/bus`;
            do
                umount /dev/bus/$dir > /dev/null 2>&1;
            done;
            echo "procfs scanner hack is inactive \n";
        ;;

        *)
            echo "Usage (start | stop) \n";
        ;;
esac



```

And it's working on new kernel. Hope this will help ;)

---

### Post by tweedledee on 2010-03-25
> **n3ck said:**
> Okay, i found another workaround. 

The thing is, you have to bind /dev/bus dir to /proc/bus, but in the way that do not overwrite /proc/bus data. So, i've wrote a little init.d script, that does all work for us.

I've added this to the list of solutions.

---

### Post by ezekiel_quacks on 2010-04-02
> **n3ck said:**
> I've checked your advice, and scanner is working at the first time only. When i type scanimage -L at first time after reboot, scanner is found. But when i type scanimage -L again, scanner is now not found ;( I try to restart udev, saned, but nothing fixes the problem.

Hmm... I'm not sure what to say. I just typed scanimage -L five times in a row, and my computer had no problems seeing the scanner every time. But it looks like you found another workaround since, so I'm glad for you! :)

---

### Post by williamts99 on 2010-04-12
I just noticed a process running, smfpd that is using ~10% CPU at all times.  Is this related to the Samsung Unified Printer Driver that was recently, reluctantly installed?

---

### Post by tweedledee on 2010-04-12
> **williamts99 said:**
> I just noticed a process running, smfpd that is using ~10% CPU at all times.  Is this related to the Samsung Unified Printer Driver that was recently, reluctantly installed?

It is the parallel port daemon, and I have no idea why it would be using any measurable amount of cpu time, unless perhaps you actually have something connected to your parallel port.  If you used the samsung installer, you are stuck with it unless you want to manually deactivate the startup script in /etc/init.d/samsungmfp (although I don't know which set of commands cleanly does so with Ubuntu's upstart, unless it's the same as normal init.d) or delete the smfpd file itself from /usr/sbin.

If you used my repository, just uninstall the -parallel package.

Of course, all these solutions assume you don't actually have a printer connected via parallel port; if you do, you must (as far as I know) have this piece of the driver for it to work.

---

### Post by juniorx32 on 2010-04-15
Fellows, 

My CD got corrupted and I cannot find the driver anyhwere in the internet.
In the office I work we need that printer and its up to me to install it in a Ubuntu desktop to act as the printing server.

Im very glad that i see how to install, but i simply dont have the driver ](*,)
Please help.

---

### Post by tweedledee on 2010-04-15
> **juniorx32 said:**
> Fellows, 

My CD got corrupted and I cannot find the driver anyhwere in the internet.
In the office I work we need that printer and its up to me to install it in a Ubuntu desktop to act as the printing server.

Im very glad that i see how to install, but i simply dont have the driver ](*,)
Please help.

If you want to use the repository to install, you don't need the driver files at all.  If you wish to use the installer directly to replace what was on your CD, you can get the US version from the repository web page.  The localized versions (including the version I provide through the repository) can be downloaded at the appropriate Samsung country page, going to support -> downloads -> computer hardware -> printers & multifunction -> type & model of printer.  The color laser / CLP-770 combination will (currently) give you the most recent driver, and works for every printer.

---

### Post by williamts99 on 2010-04-21
> **tweedledee said:**
> It is the parallel port daemon, and I have no idea why it would be using any measurable amount of cpu time, unless perhaps you actually have something connected to your parallel port.  If you used the samsung installer, you are stuck with it unless you want to manually deactivate the startup script in /etc/init.d/samsungmfp (although I don't know which set of commands cleanly does so with Ubuntu's upstart, unless it's the same as normal init.d) or delete the smfpd file itself from /usr/sbin.

If you used my repository, just uninstall the -parallel package.

Of course, all these solutions assume you don't actually have a printer connected via parallel port; if you do, you must (as far as I know) have this piece of the driver for it to work.

I just removed /etc/init.d/smfpd and the printer driver still works.  It was installed from the samsung driver file from their support website.

Best Regards

---

### Post by mrdiego on 2010-04-27
@ tweedledee:

I have to thank you sooooo much.
I did a fresh install with Lucid RC and there was no autodedect for my SCX 4521f. I look for the original Samsung-Driver and I couldn't find it no more. What I found was that:
[http://www-personal.umich.edu/~tjwatt/suldr/](http://www-personal.umich.edu/~tjwatt/suldr/)

I included your source, key and installed than the driver, data and scanner... I did a restart and I tested printing and scanning with SimpleScan. And what can I say: It works perfect... so fine, so quick and without problems. Happy.

Thank you again... you made my day. Please hold it supported as long you can. Thanks to you, we poor souls have a solution for our samsung-scx-printer-frustrations in not well supported or neither supported Linux-drivers by Samsung.

Greetings mrdiego

---

### Post by Nooki on 2010-04-27
Yes, I hope this repository is a life-saver, especially since Samsung has long dropped (silently) Linux support in my case too (SCX-4200). Samsung does not ship free drivers and seem to not even care about supporting (yet distributing!) their binary blobs. Their help center is insulting to say the least. Suck less, Samsung. (Or keep sucking, I'll just buy elsewhere).

---

### Post by reg4thx on 2010-04-28
tweedledee - I reg'd just to thank you; "thank you" :)  

I use gentoo, just got an scx-4623, installed samsung's unified driver and thought "what a sloppy mess this installer is".  don't get me wrong - I love that they at least provide some linux support but the dumb thing put *desktop files/folders in /, /bin, etc., among other distasteful things.

I started poking around and found your thread.  compared to their top-heavy pkg, yours (just driver and data pkgs) are tidy and provide all that I need.

"thanks" again for your work, it's very useful regardless of distro.

---

### Post by Sir_Patrick on 2010-05-02
> **tweedledee said:**
> To everyone who has posted with USB scanner difficulties over the last few months: this is your problem.  (And why they've always worked under Debian, which has this option enabled.)  I have updated the first post to include this information and indicate how you can work around it, but none of the solutions are trivial.  And please don't ask for assistance on how to compile your own kernel, there are many guides available.


Hello Tweedledee, i recently upgraded my ubuntu version of 9.10 to 10.04 (lucid lynx).
Together with your repository everything works fine now on my samsung CLX3175.
The scanner part works with the simple scanner program as well with xsane.
If anyone else has problems with the usb bus on ubuntu 9.10 then i can recommend an upgrade to 10.04.
Thanks again for your help at this forum it has been a great help to me.

---

### Post by kimusan on 2010-05-03
I have been using the drivers and packages described in this thread for some time now and both printing and scanning have worked perfectly. 
Yesterday, however, I upgraded to ubuntu 10.04LTS which caused xsane to not be able to detect my multi-print-scanner device anymore. 
The device is a network printer/scanner and hence uses the netdiscovery mechanism. 
running xsane from the console reviles the following error:
$ xsane
netdiscovery: relocation error: /lib/tls/i686/cmov/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
netdiscovery: relocation error: /lib/tls/i686/cmov/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference

looks like the drivers are not compatible with the libc from ubuntu 10.04LTS :-(

anyone else have this problem and maybe know how to fix it?

---

### Post by lipinski on 2010-05-03
I'm still having a libpng3 problem with this...

I installed using your repository, and the install went fine.

However, all the tools under /opt/Samsung/mfp/bin do not work because of missing libpng3.so library.

Seems like a broken symlink was created under /usr/lib.
libpng3.so -> libpng12.so.0

But, I do not have a libpng12.so.0 under /usr/lib.

I have a libpng3.so under /usr/lib64...

Don't know why the Samsung tools can't find it...

---

### Post by tweedledee on 2010-05-03
> **lipinski said:**
> I have a libpng3.so under /usr/lib64...

Don't know why the Samsung tools can't find it...

Interesting.  It sounds (for both you and possibly kimusan) that Ubuntu has gone with a straight lib64 for 64-bit systems, instead of just symlinking lib64 -> lib and using lib.  If that is the case, the Samsung drivers will break, as the "/usr/lib" path is compiled in, and they won't look in /usr/lib64.  This can be solved by creating symlinks in /usr/lib to point to /usr/lib64.  If this is correct, then /usr/lib should probably just be a symlink to /usr/lib64, which would solve the problem as well, but that would break many universe/multiverse packages (i.e., the ones that Ubuntu doesn't customize) if they are already installed.

I don't have time now to look into this further, but if you can explore along those lines, it would help me when I do have some time to put into thinking of a solution, and one that doesn't simultaneously break everything for 64-bit Debian (which I run).  Alternatively, if my guess as to the problem is entirely wrong, that is also useful information.  If Sir_Patrick, mrdiego, or someone else with a working Lucid system happens to be reading this, could you please indicate whether your successful install was 32 or 64 bit, and whether or not you have tried scanning with xsane and/or used the Configurator?

---

### Post by Sheix on 2010-05-04
> **kimusan said:**
> I have been using the drivers and packages described in this thread for some time now and both printing and scanning have worked perfectly. 
Yesterday, however, I upgraded to ubuntu 10.04LTS which caused xsane to not be able to detect my multi-print-scanner device anymore. 
The device is a network printer/scanner and hence uses the netdiscovery mechanism. 
running xsane from the console reviles the following error:
$ xsane
netdiscovery: relocation error: /lib/tls/i686/cmov/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
netdiscovery: relocation error: /lib/tls/i686/cmov/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference

looks like the drivers are not compatible with the libc from ubuntu 10.04LTS :-(

anyone else have this problem and maybe know how to fix it?

Same problem, working on it for 2 days, inform me if you'll have success before me :)

Looks like netdiscovery is using dynamic link and something is changed in ubuntu libs in 10.4.

---

### Post by keturn on 2010-05-06
I'm getting the relocation error mentioned, and on my system (installed from karmic 9.10 disc and upgraded to 10.04), /usr/lib64 is a symlink to /usr/lib.

Actually, my relocation error is slightly different:

netdiscovery: relocation error: /lib/libnss_files.so.2: symbol __rawmemchr, version GLIBC_2.2.5 not defined in file libc.so.6 with link time reference

---

### Post by tweedledee on 2010-05-10
> **keturn said:**
> I'm getting the relocation error mentioned, and on my system (installed from karmic 9.10 disc and upgraded to 10.04), /usr/lib64 is a symlink to /usr/lib.

Actually, my relocation error is slightly different:

netdiscovery: relocation error: /lib/libnss_files.so.2: symbol __rawmemchr, version GLIBC_2.2.5 not defined in file libc.so.6 with link time reference

It will be at least one and probably two weeks before I can pull in the current libc libraries from Debian unstable and try to find a solution (or at least determine if it is the libraries or an Ubuntu configuration issue).  In the meantime, anyone else who learns anything more, please share.

---

### Post by robang on 2010-05-16
Executing /opt/Samsung/mfp/bin/Configurator from console it asks for cupsys-common but that package are not in the dependencies. I suggest you to add it to its dependencies.
A lot of thanks to mantain the support for scx-4100 and scx-4200.

---

### Post by robang on 2010-05-16
> **robang said:**
> Executing /opt/Samsung/mfp/bin/Configurator from console it asks for cupsys-common but that package are not in the dependencies. I suggest you to add it to its dependencies.
A lot of thanks to mantain the support for scx-4100 and scx-4200.

I was trying it on Ubuntu Karmic Koala 9.10 :-)

---

### Post by reg4thx on 2010-05-16
sorry if I missed something in the thread but I'm having a prob w/hi-res scanning.

I use gentoo, scx-4623f mfp and used tweedledee's pkg to install just *data and *driver.  everything in the printer works perfect including scanning up to 600 dpi.

I use up-to-date sane and xsane and no matter how I try it, scanning at 1200+ dpi starts the scan then generates "error during read: out of memory".  I have 4G ram, scanning 'home' has gigs of free disc space, did the 1200 dpi scan in win7 vm using samsung drivers and the image is only 340M.

tbh I don't really know why scanning in linux works at all - there is no "scx4623" in /etc/sane.d/smfp.conf ("smfp" is in dll.conf).  but it scans fine if I use 600dpi or less.  so all I can guess is that one of the other entries in smfp.conf is why scanning works for mine (I don't have this xerox backend anywhere I can find that I've seen others here mention as a working substitute).

I also notice that besides no 4623 in smfp.conf, no other entry there goes above 600 so:

1.  anyone know if I added "1200" to all the existing smfp.conf entries if mine would then work at 1200?  I read somewhere it's possible to do physical damage to a scanner by using the wrong settings so am afraid to try it :)

2.  how would I go about gathering all the parameters necessary to add scx4623 to smfp.conf myself?  again, I'm afraid to experiment for fear of damaging something.

I used "% ar vx deb_file" to untar tweedledee's deb files and when I do this to his scanning deb file, "data" ends up being a 0-byte file in ./.  the other necessary files in his scanning deb only seem to be a couple scripts; iow besides the "data" file it doesn't really look like there's anything in it I need.

thanks.

---

### Post by tweedledee on 2010-05-16
> **robang said:**
> Executing /opt/Samsung/mfp/bin/Configurator from console it asks for cupsys-common but that package are not in the dependencies. I suggest you to add it to its dependencies.
A lot of thanks to mantain the support for scx-4100 and scx-4200.

Actually, it is.  The configurator package depends on the driver, which depends on cups, which depends on the -common package.  A while back, Debian (and Ubuntu) renamed all the cups packages "cups-*" instead of "cupsys-*", and so the new name is preferred but it will pull in whichever is available.  (cupsys-* packages still exist, but do nothing except depend on the new packages.)  The Configurator error is an artifact of Samsung not keeping up with changes to CUPS and doesn't actually matter because the files it needs are present, just in a different package.

If you are actually encountering real problems with the Configurator and not just warnings, it may reflect more recent changes to CUPS and you should share further.

---

### Post by tweedledee on 2010-05-16
> **reg4thx said:**
> tbh I don't really know why scanning in linux works at all - there is no "scx4623" in /etc/sane.d/smfp.conf ("smfp" is in dll.conf).  but it scans fine if I use 600dpi or less.  so all I can guess is that one of the other entries in smfp.conf is why scanning works for mine (I don't have this xerox backend anywhere I can find that I've seen others here mention as a working substitute).

You could sort it by by commenting out all but one of the entries in /etc/saned.d/dll.conf at a time and see if scanning works (after possibly restarting saned each time, I don't remember if it catches changes to dll.conf without a restart).  But since I don't believe any of the open source drivers support that printer yet, it seems likely it is the Samsung driver.

> **reg4thx said:**
> I also notice that besides no 4623 in smfp.conf, no other entry there goes above 600 so:

1.  anyone know if I added "1200" to all the existing smfp.conf entries if mine would then work at 1200?  I read somewhere it's possible to do physical damage to a scanner by using the wrong settings so am afraid to try it :)

Not having tried it, I can't say.  But it seems reasonable, since your device can actually scan at that resolution.  It may also just be a limitation of the Samsung Linux driver; I don't recall that this issue has come up before.

> **reg4thx said:**
> 2.  how would I go about gathering all the parameters necessary to add scx4623 to smfp.conf myself?  again, I'm afraid to experiment for fear of damaging something.

Based on my reading of the smfp.conf file, you could probably guess everything except the "twainspec" value pretty easily, and only a couple of values will change compared to other SCX entries.  And I'd bet that the appropriate value for that is "3", based on the pattern of printer models.  Some things may also be found in the relevant ppd file, as the hwoption entries tend to be the same whether configuring the printer or the scanner.

> **reg4thx said:**
> I used "% ar vx deb_file" to untar tweedledee's deb files and when I do this to his scanning deb file, "data" ends up being a 0-byte file in ./.  the other necessary files in his scanning deb only seem to be a couple scripts; iow besides the "data" file it doesn't really look like there's anything in it I need.

The only thing that package does is add "smfp" to dll.conf, which is why it consists solely of install/remove scripts.  I should update it to use a file in /etc/sane.d/dll.d/ instead of modifying dll.conf directly, but that will wait until the next time I need to do significant repackaging.

---

### Post by Mr_Cynical on 2010-05-16
Is it possible to download the deb files manually? I'm on a Dellbuntu which uses lpia so APT won't download from the repository (it looks for an lpia release which obviously isn't there). If, however, I could download the debs I could install using dpkg --force-architecture : it's not as if printer drivers are something that I will be updating very often so not being able to update them via APT is no great loss.

---

### Post by tweedledee on 2010-05-16
> **Mr_Cynical said:**
> Is it possible to download the deb files manually? I'm on a Dellbuntu which uses lpia so APT won't download from the repository (it looks for an lpia release which obviously isn't there). If, however, I could download the debs I could install using dpkg --force-architecture : it's not as if printer drivers are something that I will be updating very often so not being able to update them via APT is no great loss.

Go to [http://www.bchemnet.com/suldr/dists/debian/extra/](http://www.bchemnet.com/suldr/dists/debian/extra/) and choose the appropriate architecture to see the files.  In general, choose the 3.00.65-3 versions instead of 3.00.37-3 unless you know you need the older ones.

---

### Post by Mr_Cynical on 2010-05-16
> **tweedledee said:**
> Go to [http://www-personal.umich.edu/~tjwatt/suldr/dists/debian/extra/](http://www-personal.umich.edu/~tjwatt/suldr/dists/debian/extra/) and choose the appropriate architecture to see the files.  In general, choose the 3.00.65-3 versions instead of 3.00.37-3 unless you know you need the older ones.

Thanks - the i386 debs will work fine, lpia is just x86 with some added power saving functions (but apt, having recognised correctly that the kernel is 'lpia' not 'i386' will not download from i386 repos :P)

---

### Post by reg4thx on 2010-05-17
thanks tweedledee.

> It may also just be a limitation of the Samsung Linux driverIf it's not that then I think it might be because the drivers are too old for my printer.

After looking at smpf.conf entries and scan specs on a couple of the printers, they all seem to be more or less the same.  I created an entry for mine, used a default dpi setting no other was and xsane came up showing it.  when I remove that entry and del ~/.sane, xsane starts with a different value.

but I still get the same xsane crash using my new smfp.conf entry.  I'm just guessing but because it scans at all I think it's mainly using /usr/lib/sane/*smfp for basic/generic scan settings and when I look at the timestamp for it from yours or the samsung pkg, it's dated mid-2009 which predates this printer.  

with "strings" I see the printers from smfp.conf but nothing for my series in the lib.  so it seems like I may have to wait for samsung to update the drivers to know if that will fix it.

---

### Post by suoko on 2010-05-19
your repo is working perfectly with lucid and samsung scx 4200:
both printer and scanner works

one question: can you add lexmark and canon debs to your repo ?

---

### Post by tweedledee on 2010-05-19
> **suoko said:**
> your repo is working perfectly with lucid and samsung scx 4200:
both printer and scanner works

one question: can you add lexmark and canon debs to your repo ?

I'm glad it works for you.

As far as Lexmark and Canon, I don't have printers by those manufacturers (and my standalone Canon scanner works with open source drivers), so I haven't looked into these at all.  Are there driver packages they provide for Linux?  Even if so, it would not be a project I could undertake soon due to time limitations, or necessarily at all depending on how the driver structure is since I wouldn't be able to directly test anything.

---

### Post by tweedledee on 2010-05-19
> **reg4thx said:**
> If it's not that then I think it might be because the drivers are too old for my printer.

You can stop at "because the drivers are too old", probably.  The drivers still rely on libraries that were last updated 5 years ago and are long since obselete.  Most of the changes during the last 3-4 years have not had anything to do with the core driver, but rather how it interacts with the rest of the O/S.  It's possibly a completely rewritten driver would be necessary, and it's not clear whether Samsung intends to release one.

So if you can't get it to work, I suggest you don't hold your breath waiting for an updated driver that will work.  Of course, should Samsung actually release one, I will package and distribute it.

---

### Post by reg4thx on 2010-05-20
> **tweedledee said:**
> You can stop at "because the drivers are too old", probably.  The drivers still rely on libraries that were last updated 5 years ago
ok, thanks for the update (and all your effort for the samsung drivers).

I had been simultaneously posting in the cnet samsung forums and the guy there says he'll share the info with his ppl but I'll heed your caution that nothing may come of that :)  

600 dpi works fine and if necessary 1200+ works fine in win vms so I can always use that if I have to.

---

### Post by drkia on 2010-05-20
[LEFT]
@tweedledee Thanks a lot for your post and for your repository. My SCX-4100 is working now properly. Both, scanning and printing.  
[/LEFT]

---

### Post by dwabot on 2010-05-31
I now have a working CLP-310 printer connected to a Debian Lenny box.

Thanks for providing these *.debs and clear instructions!

---

### Post by michaelnu on 2010-06-14
Hallo,

thanks for the *deb.
I use is since several versions of ubuntu.

But now, with the Ubuntu 10.04 x64, i have a problem with this driver/packages.

The best output for my CLP-300 brings the Foomatic-driver for gray-scale an the CLP-600 SPL-C driver for color.
In previous versions of ubuntu, i could choose between the different drivers.
But now, if i have installed the packages samsungmfp-data and samsungmfp-driver (3.00.63-3), i only cloud choose the SPL-C driver, the foomatic is hidden.

Is there a way to fix it?

---

### Post by tweedledee on 2010-06-14
> **michaelnu said:**
> Is there a way to fix it?

Maybe.  For some reason that I haven't had time to track down, x86-64 is a problem with Ubuntu 10.04.  I'll add this aspect to my list of things to check when I have time.  Unfortunately, it's entirely possible it will be a month or more before I do have time to work on this, as I have many urgent demands on my time right now (some of them pay me and so take precedence).  I'll post updates when I can.

---

### Post by jose1711 on 2010-06-29
hello guys,

i bought scx 4300 today. it prints okay, but it only scans in grayscale (using sane-xerox backend). anyone else experienced the same?

thank you,

joe

---

### Post by adi-ss on 2010-07-03
===================
It success also with my Ubuntu 10.4, Samsung SF-565PR, recognized by lsusb as MFP 560 Series.

The /etc/sane.d/xerox_mfp.conf added:
#Samsung MFP 560 
usb 0x04e8 0x340e 

and /lib/udev/rules.d/40-libsane.rules insert lines:
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="340e", ENV{libsane_matched}="yes"

I pull out the USB jack, put in again, run Xsane, try to scann, and success!!!! Thank you Thank you
:D

---

### Post by tweedledee on 2010-07-03
NEW HOME FOR THE REPOSITORY

Effective immediately, the repository has relocated.  Those of who getting errors trying to access it in synaptic or through the web, this is why.

The new home is: [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/)

Barring surprises or the occasional brief outage, I do not anticipate any additional service interruptions for at least another year.

---

### Post by WFdeVlam on 2010-07-08
Hi,

Thanks for the great repository!

[this is in the wrong forum. I'm leaving this by way of FYI. If you feel you can help me, [please respond here. much appreciated]("http://ubuntuforums.org/showthread.php?t=1527446")!]

setup: SCX-4500w multifunction on ubuntu 10.04 64bit via wifi network.

The printer works great, but the scanner is not recognized.

i have installed
samsungmfp-driver
samsungmfp-data

tested with and without
samsungmfp-scanner
splix
xsane

---

### Post by okkadiroglu on 2010-07-17
Hi,

I am having a major problem with my AMD64 computer, operating with Ubuntu 10.4, and Samsung clx-2160 printer/scanner. Before a major update in the beginning of June everything was working. Now when I turn the printer on I read a flashing error message on the screen of the printer saying "USB_CtrlEP.c 72 IDLE" and "Internal Error Power Off/On" The reply to lsusb command is "Bus 001 Device 019: ID 04e8:3425 Samsung Electronics Co., Ltd"  Even though I have Samsung Unified Driver Configurator installed and with CUPS I can not get a test page out. When I try the printer with a Compaq nx6110, again operating with Ubuntu 10.6, the printer works without a problem but scanner produces three parallel images of a single scanned image. I use the valuable information provided in [http://www.bchemnet.com/suldr/index.html](http://www.bchemnet.com/suldr/index.html) I have taken the printer to two certified repair shops and both proved that there is nothing wrong with the printer. I use a webcam and two large external hard disk on the same usb ports and they work without problems.

What is going on and how can I print and scan with clx-2160 connected to AMD64 computer running on Ubuntu 10.6?

Many thanks

---

### Post by tweedledee on 2010-07-17
To everyone who has reported problems with Ubuntu 10.04 and AMD64 systems:

The problem is definitely a conflict with the new (2.11) eglibc.  As this is a rather essential core library, work-arounds for this are not going to be easy.  If you are having trouble printing or scanning and need a working printer/scanner in the near future, your best bet is to switch to a earlier version of the library (Debian Stable, Ubuntu 9.10 or earlier) or switch to a 32-bit install (which seems to be working).  You MIGHT also have success using a virtual machine (VMWare, Virtualbox) to install a 32-bit version of Ubuntu 10.04 and use that for your printing/scanning needs, but I've not tested this.

My estimated time to having a couple of days to dedicate to solving this problem is mid-August, but it's possible that will slip even later.  And I can't promise that I will find a solution, because this is fundamentally a problem with the drivers Samsung is providing.  **If you are experiencing problems printing or scanning after updating to a recent Ubuntu and are using a 64-bit system, please contact Samsung** (although remember that they will only support installations from their installer, not my repository, so it is not to your advantage to mention that you are using my files instead of their installer directly even though they are the same binaries).  The more people that tell them this a problem, the greater the probability they will actually update their Linux drvier (or perhaps announce that they are halting Linux driver development, which would at least be useful to know).

In the meantime, anyone using a 64-bit system that has a problem OR a working printer, please post.  The more data that I have to work with, the more likely it is that I can find a solution if Samsung doesn't.

---

### Post by yahs on 2010-07-18
Update on how my old Samsung scx-4100 mfp is working in Ubuntu. As widely reported, since 9.10 it hasn't always been easy to get everything up and running. I am currently using Ubuntu 10.04 and I have printing and scanning available, though I have intermittent problems with CUPS needing a restart. (sudo service cups restart – run in a terminal is sometimes needed in response to an error message about CUPS not being started)
On Friday 2nd July I installed Ubuntu 10.10 (32-bit version) alongside 10.04 on a 160 GB disk 
The installation did not recognise my printer which was switched on and attached by USB. 
From previous experience, I know that I can go to system, admin, printing and add printer – Ubuntu will then find my SCX-4100 and install the Splix driver for SCX-4200 which provides printing. However this does not provide scanning, so I prefer to install my printer as follows. 
Download the Linux Unified Driver from samsung.co.uk, extract the files, then navigate to the folder cdroot/Linux and execute the command sudo ./install.sh
In the terminal I read the error messages as follows
libstdcc ++.so.5 (gcc 3.o.x) not found, install … done
libtiff.so.3 not found, install … done
	It seems that Qt library is not installed or X display is not accessible. Custom Qt library will be configured for use with this package.
The Samsung GUI installer then appears, prompts me to add myself to the group lp, suggests I disable parallel printing and that's it. The Samsung Unified Configurator appears on the desktop and printing is available using /dev/mfp4: scanning is available as a flatbed scanner on usb:0. Test page prints using CUPS v 1.1x. Scanner scans in colour using Samsung Configurator.
Following a reboot Ubuntu now recognises that there is a printer attached by USB and in the Samsung configurator there are 2 printers now showing - one on mfp4 as installed by the Unified Driver the other configured as usb://Samsung/SCX-4200%Series. Both printers work, though the test pages printed are different - mfp4 produces Colour wheels with the heading “Printer Test Page” and at the bottom it states printed using CUPS v 1.1.x the other one has “Ubuntu” as the heading  with horizontal lines demonstrating the colours (all black and grey for me) and at the bottom it states GPL Ghostscript version 3010.
I can print from all applications and I can scan (in colour – haven't tried anything higher than 600 as the scan is rather slow) using quickscan, Xsane, Picassa and OpenOffice. Both 10.04 and 10.10 work very well (skype and wireless connection both set-up with no problems). The SCX-4100 printer has been good - good quality text and very economical, though it can be noisy and does run hot if you do a lot of printing – probably time for a new one.

---

### Post by DHell on 2010-07-23
Thanks tweedledee for the terrific work putting together the tutorials and repositories! Just installed your deb packages following the instructions in the forum post and got my ML-1915 perfectly back to work (by the way, I use a 32-bit Athlon)
The printer used to work fine until I upgraded to 10.04 LTS, when it started to show several problems (most annoying of all being the constant "authentication" requests).
Keep up the good work!

---

### Post by tobiasly on 2010-08-08
Many thanks tweedledee for your work on this. I found this forum because I am also having the issue with scanning on 10.04 x86_64 (SCX-4826FN, networked). Let me know if you need any help testing potential fixes.

---

### Post by tweedledee on 2010-08-12
> **tobiasly said:**
> Many thanks tweedledee for your work on this. I found this forum because I am also having the issue with scanning on 10.04 x86_64 (SCX-4826FN, networked). Let me know if you need any help testing potential fixes.

Those with networked multifunction printers may want to try a modification of the solution given here: [http://ubuntuforums.org/showpost.php?p=9686903&postcount=5](http://ubuntuforums.org/showpost.php?p=9686903&postcount=5)

Please share whether or not this helps.  My bet is that it will solve the problem of not scanning over the network generally, but still won't solve the AMD64-specific problem.

As to a general solution, I'm still struggling to find time to dedicate to the problem.  My basic idea is to somehow force the Samsung driver to use a 32-bit libc while not disrupting everything else on the computer, but doing so without being able to recompile is non-trivial.  Anyone who wants to throw ideas/time into this are welcome to do so and share the results, as it doesn't require any special expertise with the Samsung driver.  The goal is to make the error messages when running /opt/Samsung/mfp/bin/netdiscovery and smfpscan go away.  You can install the 32-bit version using the package libc6-i386 (Debian) or libc6-i686 (Ubuntu), it's just a matter of getting the driver to use the /lib32 path instead of /lib .

Another approach may be to talk to the libc maintainers (via Ubuntu or directly) to see what's different about the 64-bit 2.11 version vs. previous ones that gives rise to the error messages, but I don't necessarily expect that to be productive.

---

### Post by tobiasly on 2010-08-13
> **tweedledee said:**
> Those with networked multifunction printers may want to try a modification of the solution given here: [http://ubuntuforums.org/showpost.php?p=9686903&postcount=5](http://ubuntuforums.org/showpost.php?p=9686903&postcount=5)

Please share whether or not this helps.  My bet is that it will solve the problem of not scanning over the network generally, but still won't solve the AMD64-specific problem.

I think you're right about that, I also tried connecting the scanner directly via USB and it didn't work, so because it's not working over USB I can't really test the network fix. If it worked just over USB that would be OK.

---

### Post by yahs on 2010-08-13
Since my last post, I have acquired a scx-4500w so I can now make a contribution to the current topic of network scanning. Hope this isn't too long!
The computer I use for testing is a Pentium D 2.8 Dual Core PC, so I use the 32-bit version. To satisfy my own curiosity I first installed a copy of Ubuntu 8.04 on a 160 GB hard disk and both scanning and printing worked perfectly.

Next I cleaned the hard drive and installed a fresh copy of Ubuntu 10.04 with both USB and network cables attached.
No printer found but System, Admin, Printing, Add Printer finds the scx-4500w and offers the driver scx 4500 using SpliX V 2.0.0. This is fine for printing but doesn't provide scanning. So it is easier to download the Unified driver and run the installer.
 
The Samsung Unified Driver sees both printer and scanner as long as USB cable attached, but removing the USB cable produces the following error message, when I execute xscan in a terminal.

netdiscovery: relocation error: /lib/tls/i686/cmov/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
netdiscovery: relocation error: /lib/tls/i686/cmov/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference

Next I installed Maverick 10.10 alpha 2 alongside Ubuntu 10.04 and repeated the above procedure with the same results except for a different error message as follows

netdiscovery: ../sysdeps/unix/sysv/linux/getpagesize.c:32: __getpagesize: Assertion `_rtld_global_ro._dl_pagesize != 0' failed.
Aborted
netdiscovery: ../sysdeps/unix/sysv/linux/getpagesize.c:32: __getpagesize: Assertion `_rtld_global_ro._dl_pagesize != 0' failed.
Aborted
netdiscovery: ../sysdeps/unix/sysv/linux/getpagesize.c:32: __getpagesize: Assertion `_rtld_global_ro._dl_pagesize != 0' failed.
Aborted

With both Ubuntu 10.04 and 10.10 I tried the suggestion of altering the file xerox_mfp.conf but it makes no difference to the results I get.

---

### Post by whych on 2010-08-15
Where are you downloading the driver from?
Samsung's sites no longer have linux downloads!

---

### Post by tweedledee on 2010-08-15
> **whych said:**
> Where are you downloading the driver from?
Samsung's sites no longer have linux downloads!

That depends on the printer, and whether you are using Samsung.com or a regional Samsung site.  For example, the CLP-770ND still provides the most recently released driver (now approaching a year old), at least at the primary Samsung site.  Other printers, such as my own CLP-550N, no longer list it.  It appears to be that printers first sold within the last 2-3 years usually have it listed, and others don't, but it's a little more random than that.  And since the only variation is the version number (because Samsung only arbitrarily updates each link as new version are released, it has nothing to do with whether or not a version works) and whether or not Samsung packages the multi-function specific parts, it doesn't really matter which printer the driver you download is officially associated with.  The exception being that if you want to scan, you need to download an archive from a multi-function printer (CLX or SCX models, and some CLP).

And although I don't want to direct too many people this direction, I do provide both the most recent (3.00.65) and most recent prior to the USB subsystem redesign (3.00.37) driver archives on my site ([www.bchemnet.com/suldr/](www.bchemnet.com/suldr/)).  Most of my monthly bandwidth already goes to people only downloading one of those two files, although the majority of the actual traffic is for the repository (which is obviously much more efficient for everyone).  Because Samsung hasn't completely cut off the Linux driver, my bandwidth load is currently acceptable; that may change if too many people are looking only for the driver files and not the repository or general information.

---

### Post by rutgerhendriks on 2010-08-27
When using the Samsung scan software for my CLX-3175FN the following error occurs (as stated previously):
```
netdiscovery: relocation error: /lib/libnss_files.so.2: symbol __rawmemchr, 
version GLIBC_2.2.5 not defined in file libc.so.6 with link time reference
```I found part of the solution for the error.

I renamed the file /lib/libnss_files.so.2 like so:
```
cd /lib
mv libnss_files.so.2 libnss_files.so.2-64bit
```and created a link to the 32-bit version:
```
cd /lib
ln -s ../lib32/libnss_files.so.2 .
```Now I don't have a problem running the Samsung scanner.

I'm guessing I will have problems now with other programs that do require the 64-bit version of libnss_files.so.2,
so I added this 'solution' to the bug at
[https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/576531](https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/576531)

Probably someone can come up with a solution to simply use the 32bit version from /lib32 without remove the 64-bit version.

---

### Post by tweedledee on 2010-08-27
> **rutgerhendriks said:**
> I renamed the file /lib/libnss_files.so.2 like so:

You could script this out to (mostly) avoid problems with other programs.  To do so, you'd need to rename the relevant Samsung binaries and replace them with scripts of the same name.  The scripts would trigger the rename of the library, call the renamed samsung binary directly, and then change the name of the library back after the Samsung piece quit.

I may have time to post a simple solution along these lines this weekend, we'll see; I wanted to get this idea out while I had a minute in case someone else wants to try it before I have a chance.  The major problems with this approach are:
(1) you need root access to rename the lib file, so either the Samsung binaries (and xsane) need to be run as root, or the scripts need setuid root access.
(2) anything else trying to access the library during the phase when the Samsung programs are active would have problems.  But that's (probably) no worse than a permanent rename.

I would associate the renaming scripts only with the few Samsung utilities that need it rather than xsane or the Configurator to minimize time that the 32-bit library is active.

---

### Post by rutgerhendriks on 2010-08-27
> **tweedledee said:**
> You could script this out to (mostly) avoid problems with other programs.I was kind of hoping this could be solved using some environment variables
so we could leave the files as is for other applications.

---

### Post by tweedledee on 2010-08-27
> **rutgerhendriks said:**
> I was kind of hoping this could be solved using some environment variables
so we could leave the files as is for other applications.

You'll need the scripts solution no matter what.  What may work, and I (again) haven't yet tried, is using LD_LIBRARY_PATH in a script (in place of renaming the libraries for the solution above) to point to the 32-bit library.

See [http://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html](http://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html) for more information, especially section 3.3.

For some reason I think this won't work, but it's been a while since I played with any of it and I can't immediately remember why it could fail (and I may be mistaken anyway).  But it's no worse to try than what you've already done.

---

### Post by janneknower on 2010-08-27
Hi,

the trick is, I guess, NOT to create a link to a 32 bit version of libnss_files.so.2 but to delete (or rather rename) the 64 bit library. For some reason, the sole existence of the 64 library makes scanning to fail.

-J

---

### Post by hodad on 2010-09-03
Thanks to Tweedledee for the help!

---

### Post by hodad on 2010-09-03
i

---

### Post by ftoral on 2010-09-05
> **rutgerhendriks said:**
> I found part of the solution for the error.

Hi, thanx for all to share your tries and tips here. This thread is a big help. 
Great thanx to tweedledee who work hard with the unofficial repos.

I've resolved by mistake the problem with the scanner over LAN for my CLX-3175N.

I've a fresh install of Lucid 10.04.1 on an old AMD64 system and only the printer was working (either with the official samsung drivers or the unofficials).

I tried rutgerhendriks solution. The scanner is not detected and i've the same error :

```
fabien@pc:/lib$ /opt/Samsung/mfp/bin/Configurator
netdiscovery: relocation error: /lib32/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
netdiscovery: relocation error: /lib32/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference

```**Then i made a mistake by deleting the files :**
```
/lib/libnss_files-2.11.1.so
/lib/libnss_files.so.2
```And now an occurrence of the relocation error is printed once only when accessing on 'Scanners Configuration' page : 
```
netdiscovery: relocation error: /lib32/libresolv.so.2: symbol strlen, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
```[B]The scanner is detected and operational :p
[/B] 
Previously i also made some modifications on the /etc/sane.d/smfp.conf by adding
```

    <model vendor="samsung" id="clx3170" modelstring="CLX-3170 Series">
[... copy of the clx3160 section ...]
    </model>

```And i've also modified the /etc/sane.d/xerox_mfp.conf according to the [post quoted by tweedledee.]("http://ubuntuforums.org/showpost.php?p=9686903&postcount=5")

Later i'll remove these last two modifications to see what happens.
Now i've to retrieve my libnss_files-2.11.1.so for 64bits in case of trouble with the deletion... :???:

---

### Post by hodad on 2010-09-09
Have followed all of the methods on the first page of this thread, and it seems like I'm almost there, but I've been almost there for several days now.

I've gotten to the point where I can run the configurator OK, but it gets to the port selection page, and I don't know which USB port to choose.  I have chosen several (most recently mfp4) and then continue on.  I then run the "test".  It says "driver found", but then "can't find devices on mfp:/dev/mfp4".

I then ran the Ubuntu printer app (under System-Admin) and went to the troubleshooter.  It gave:

"printer "scx4x21" not owned by root"  and "Printer 'scx4x21': none

Under lpr.log:
:add /devices/platform/parport_pc.888/printer/lp0
:Failed to get parent

Any help greatly appreciated!

---

### Post by okkadiroglu on 2010-09-15
> **okkadiroglu said:**
> Hi,

I am having a major problem with my AMD64 computer, operating with Ubuntu 10.4, and Samsung clx-2160 printer/scanner. Before a major update in the beginning of June everything was working. Now when I turn the printer on I read a flashing error message on the screen of the printer saying "USB_CtrlEP.c 72 IDLE" and "Internal Error Power Off/On" The reply to lsusb command is "Bus 001 Device 019: ID 04e8:3425 Samsung Electronics Co., Ltd"  Even though I have Samsung Unified Driver Configurator installed and with CUPS I can not get a test page out. When I try the printer with a Compaq nx6110, again operating with Ubuntu 10.6, the printer works without a problem but scanner produces three parallel images of a single scanned image. I use the valuable information provided in [http://www.bchemnet.com/suldr/index.html](http://www.bchemnet.com/suldr/index.html) I have taken the printer to two certified repair shops and both proved that there is nothing wrong with the printer. I use a webcam and two large external hard disk on the same usb ports and they work without problems.

What is going on and how can I print and scan with clx-2160 connected to AMD64 computer running on Ubuntu 10.6?

Many thanks


Hi,

After having extensive correspondence with Samsung (Turkey and Korea) I obtained the new drivers that are not open to distribution yet. I tried it with a 32 bit computer operating with Ubuntu 10.4 and it worked with out any problem. I got a test page out as well as scanned a page correctly. But with 64 bit computer, even the new drivers do not work properly. I still get the same errors as I mentioned in the quote. 

 
[http://hotfile.com/dl/69472725/f928be1/PSU_1.02.tar.gz.html](http://hotfile.com/dl/69472725/f928be1/PSU_1.02.tar.gz.html)
 
[http://hotfile.com/dl/69473256/cb3981e/Smartpanel_1.02.tar.gz.html](http://hotfile.com/dl/69473256/cb3981e/Smartpanel_1.02.tar.gz.html)
 
[http://hotfile.com/dl/69474136/c82bd1d/UnifiedLinuxDriver_1.02.tar.gz.html](http://hotfile.com/dl/69474136/c82bd1d/UnifiedLinuxDriver_1.02.tar.gz.html)
 
are the links for the new unpublished drivers. If you like please try them and tell me your experience so that I can transfer them to Samsung. I would be very pleased if tweedledee could comment on them. Samsung is eager to know what is going on and would like to have a feedback.

Best Regards

---

### Post by yahs on 2010-09-16
Network scanning in Ubuntu 10.04 (32 bit)

Downloaded and installed the Latest Unified Driver (as posted by okkadiroglu) on a clean 32 bit Ubuntu 10.04.1 installation. 

However the outcome is the same.

Using a scx-4500 wireless printer both printing and scanning are immediately available by USB.

Trying to scan over the network using xsane produces the following error message.

netdiscovery: relocation error: /lib/tls/i686/cmov/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
netdiscovery: relocation error: /lib/tls/i686/cmov/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference.

The “fix” posted by Rutgerhendriks worked for me, even though I still get an error message from xsane

netdiscovery: relocation error: /lib/libnss_mdns4_minimal_so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference

I also noticed that as the Samsung GUI installation completes it generates an infinite number of “Opening File Manager” which appear on the status bar and nautilus has to be killed (or a restart cures the problem).

---

### Post by bearymore on 2010-09-16
> **tweedledee said:**
> To everyone who has reported problems with Ubuntu 10.04 and AMD64 systems:

The problem is definitely a conflict with the new (2.11) eglibc.  As this is a rather essential core library, work-arounds for this are not going to be easy.  If you are having trouble printing or scanning and need a working printer/scanner in the near future, your best bet is to switch to a earlier version of the library (Debian Stable, Ubuntu 9.10 or earlier) or switch to a 32-bit install (which seems to be working).  You MIGHT also have success using a virtual machine (VMWare, Virtualbox) to install a 32-bit version of Ubuntu 10.04 and use that for your printing/scanning needs, but I've not tested this.

Do the new beta drivers posted by okkadiroglu  ([http://hotfile.com/dl/69474136/c82bd1d/UnifiedLinuxDriver_1.02.tar.gz.html](http://hotfile.com/dl/69474136/c82bd1d/UnifiedLinuxDriver_1.02.tar.gz.html), etc) solve this problem? I'm using a CLX-3175 over a network which worked fine with the old Samsung drivers before the OS update. After the update, I couldn't print though scanning worked. If the new drivers solve the printing problem, I'd love to update my operating system.

---

### Post by tweedledee on 2010-09-21
> **okkadiroglu said:**
> If you like please try them and tell me your experience so that I can transfer them to Samsung. I would be very pleased if tweedledee could comment on them. Samsung is eager to know what is going on and would like to have a feedback.

I'm completely swamped at work and don't have time to deal with this properly now.  However, I did download the beta driver and at least looked at the file structure, and it looks essentially unchanged.  Since they are still packing libstdc++5 and some other old libraries, I can't imagine they've updated enough of the core to begin to address the issue here, which is that the Samsung driver seems to be relying on fundamental linux libraries that were old years ago, and simply no longer reflect a modern linux distribution.  I've no idea what system Samsung is using for development and testing, but it needs an update.  Not even Red Hat enterprise, which makes Debian releases look speedy, has shipped that library in years.

---

### Post by foobard on 2010-09-23
hi there,

I'm having a problem I don't see documented anywhere else in this thread. I recently bought a Samsung ML-2851ND monochrome laser printer. I downloaded the Universal Print Driver from the Samsung web site. (It's the latest version. I've grepped through the entire directory structure, and don't find a version number anywhere.) I'm using the latest version of Ubuntu.

Cut to the chase: printer works fine. Total control over the options. Only one problem. As soon as I print, my gnome-panel goes crazy. You know the gutter bar that shows you which programs are currently in use? It explodes with hundreds, thousands of little squares. I kill-all gnome-panel, but it comes right back. I can't figure out what process is causing this, and it's driving me crazy.

any idea?

thanks
foo

---

### Post by hateregistering on 2010-09-24
> **yahs said:**
> Since my last post, I have acquired a scx-4500w so I can now make a contribution to the current topic of network scanning. Hope this isn't too long!
The computer I use for testing is a Pentium D 2.8 Dual Core PC, so I use the 32-bit version. To satisfy my own curiosity I first installed a copy of Ubuntu 8.04 on a 160 GB hard disk and both scanning and printing worked perfectly.

Next I cleaned the hard drive and installed a fresh copy of Ubuntu 10.04 with both USB and network cables attached.
No printer found but System, Admin, Printing, Add Printer finds the scx-4500w and offers the driver scx 4500 using SpliX V 2.0.0. This is fine for printing but doesn't provide scanning. So it is easier to download the Unified driver and run the installer.
 
The Samsung Unified Driver sees both printer and scanner as long as USB cable attached, but removing the USB cable produces the following error message, when I execute xscan in a terminal.

netdiscovery: relocation error: /lib/tls/i686/cmov/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
netdiscovery: relocation error: /lib/tls/i686/cmov/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference

Next I installed Maverick 10.10 alpha 2 alongside Ubuntu 10.04 and repeated the above procedure with the same results except for a different error message as follows

netdiscovery: ../sysdeps/unix/sysv/linux/getpagesize.c:32: __getpagesize: Assertion `_rtld_global_ro._dl_pagesize != 0' failed.
Aborted
netdiscovery: ../sysdeps/unix/sysv/linux/getpagesize.c:32: __getpagesize: Assertion `_rtld_global_ro._dl_pagesize != 0' failed.
Aborted
netdiscovery: ../sysdeps/unix/sysv/linux/getpagesize.c:32: __getpagesize: Assertion `_rtld_global_ro._dl_pagesize != 0' failed.
Aborted

With both Ubuntu 10.04 and 10.10 I tried the suggestion of altering the file xerox_mfp.conf but it makes no difference to the results I get.

Please let me know if you have solved the problem. I also have a Samsung SCX-4500W and can make the printer work on Ubuntu 10.04.1 LTS, but not the scanner.

---

### Post by yahs on 2010-09-24
I have had a similar problem while I have been experimenting with some installations of Ubuntu 10.04.(32 bit) and a Samsung SCX-4500W.
If I use the download file from Samsung (3.00.65), it gets to about 96/97% then pauses to set up the configurator. At this point an infinite number of "Open file manager" icons appear on the status bar at the bottom of the screen. If this is what you are getting you need to kill nautilus (or reboot). I am pretty certain that Ubuntu 10.04.1 doesn't have this problem or better still when I use the files from the repository provided by Tweedledee I don't see this happening.

---

### Post by yahs on 2010-09-24
Thoughts on Network scanning in Ubuntu 10.04 (32 bit)

Using a scx-4500 wireless printer and installing the Samsung Unified Driver (v 3.00.65) [COLOR="Red"]both printing and scanning are immediately available by USB and work correctly.[/COLOR]

However, as has been posted, trying to scan over the network is not available without some sort of fix. In his last post Tweedledee stated that there are fundamental issues with the Samsung Drivers and the (e)glibc package which is an ongoing problem.
 
I have been experimenting (clean install after each experiment) which some of the suggestions as follows.

The following relevant files are installed by Ubuntu 10.04.1. in the following directories.

libnss_files-2.11.1.so 		/lib 	(shared library)
libnss_files.so.2		/lib	(link to shared library)
libnss_files-2.11.1.so		/lib/tls/i686/cmov (shared library)
libnss_files.so.2		/lib/tls/i686/cmov (link to shared library)
libnss_files.so			/lib	(link to shared library)


I followed up the post by Ftoral who deleted the libnss_files.so.2.

I deleted /lib/tls/i686/cmov/libnss_files.so.2 as my error message when trying to scan using xsane from a terminal is 

netdiscovery: relocation error: /lib/tls/i686/cmov/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
netdiscovery: relocation error: /lib/tls/i686/cmov/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference.

xsane now reported a different error

netdiscovery: relocation error: /lib/libnss_mdns4_minimal_so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference

but I was able to scan and the scanner appears in the Samsung Configurator with the IP address.

I continued deleting the error files until eventually I had to reboot and reinstall.

Initially the post by Rutgerhendriks worked for me. I renamed /lib/libnss_files.so.2 libnss_files.so.2.old and created a link ln –s /lib/libnss_files.so.2.

The scanner appears in the configurator, Xsane runs and scans (still with an error message), simple-scan works and I can scan from OpenOffice and Picassa.

However all of the above is not consistent; for instance I can rename or remove /lib/libnss_files.so.2 but it reappears after reboot or after latest upgrade. This then prevents scanner from working until I do some renaming or deleting of the above mentioned files. Also I think the file /lib/tls/i686/cmov/libnss_files.so.2 has to be removed irrespective of the file /lib/libnss_files.so.2

I don't really use the feature of scanning over a network so it's not really a big issue for me, but it would be nice to get it working properly.

---

### Post by pdonadeo on 2010-09-25
Just to record the event and for future searches, yesterday I was able to make my Samsung SCX-3200 work properly.

My Linux box is an Ubuntu 10.04.1 LTS (Lucid Lynx), 64 bits. The multifunction printer is a [Samsung SCX-3200]("http://www.samsung.com/it/support/detail/supportPrdDetail.do?menu=SP01&prd_ia_cd=06010300&prd_mdl_cd=&prd_mdl_name=SCX-3200"), a black and white laser printer with scanner. What I did, in summary:

[LIST=1]
[*]I downloaded the official Samsung Unified Driver from [this page]("http://www.samsung.com/it/support/detail/supportPrdDetail.do?menu=SP01&prd_ia_cd=06010300&prd_mdl_cd=&prd_mdl_name=SCX-3200"), the version of the driver is 3.00.71;
[*]I installed the Samsung drivers accurately following the steps in the Samsung manual, [here]("http://downloadcenter.samsung.com/content/UM/201006/20100607163009421/EN/english/start_here.htm") (see the chapter "Getting started", section "Supplied software");
[*]following the [post 431 in this thread by ezekiel_quacks]("http://ubuntuforums.org/showpost.php?p=8986273&postcount=431"), but customizing it for my printer, I added in /etc/sane.d/xerox_mfp.conf these two lines:
```
# Samsung SCX-3200
usb 0x04e8 0x3441
```

and in /lib/udev/rules.d/40-libsane.rules these two lines:

```
# Samsung SCX-3200
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="3441", ENV{libsane_matched}="yes"
```
[/LIST]

That's all, printer and scanner work smoothly.

---

### Post by DeathFire on 2010-09-30
I installed a Samsung SXC-4600 today and both the printer and scanner worked perfectly.

I setup the repository and installed the *samsungmfp-driver*, *samsungmfp-data *and *samsungmfp-scanner* packages, plugges in the printer and everything worked.THank you so much!

---

### Post by SeePU on 2010-10-06
Samsung ML-2510 won't print in 10.04.   This printer isn't even listed in the database.  

Edit:  I googled and decided the easiest option here is to use the splix drivers.  I went to the splix website to compare the most recent driver with what is in the repository.  Fortunately, the splix driver is available and is up to date, ver. 2.0.  So, I installed the driver via Synaptic.  Then, I went back to the printer settings until I got it to show the ML-2510 printer as available using the splix driver.  'Installed that and printed out a test page.  Whew...

In case anyone is having trouble with this printer and driver (and wonders what to use).

---

### Post by marchar on 2010-10-06
Hi Tweedle..
Just want to thank you for the great work.  Went to your Unified Driver repository and followed your instructions..... and it worked!  I have a Samsung ML 1665 (that lil' laser), connected via USB and running Ubuntu 10.04 on an old Dell box.
Thanks again!

---

### Post by okkadiroglu on 2010-10-07
Any experience with Ubuntu 10.4 running on a AMD64 computer driving Samsung CLX-2160?

---

### Post by sulio on 2010-10-11
Hi everyone,
I installed today the new 10.10. So far it looks nice :) I have Samsung SCX-4100(USB device with laser printer and scanner). And the printer just works without installing anything. But.... :)   ... but the scanner don't. Xsane reports that it can't find device. Any ideas how to make it work ? It will be nice if I don't need to install the Samsung unified driver.
Thanks in advance !.

---

### Post by anthonymke on 2010-10-16
Hello all, 

I've upgraded to 10.10, and now trying to install the drivers for my Samsung printer (ML-2525 model) to get it to work, using the repository install instructions given on the first page of the thread. However, after entering the repository URL into Synaptic and refreshing it, I get this error message from Synaptic:

> Failed to fetch [http://www.bchemnet.com/suldr/dists/debian/Release](http://www.bchemnet.com/suldr/dists/debian/Release) 
Unable to find expected entry  extra/source/Sources in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

I've checked the spelling/instructions, but same results. Also tried installing generic Postscript drivers, as well as the ones for the more-documented ML-2510 and -2550 models, but no luck; it'll only work with 2525's driver.

Any suggestions? (Yes, there's downloading the driver from Samsung itself, but I don't want to install the accompanying Samsung-customized junk with it, just the driver).

Thanks...

---

### Post by uqbar on 2010-10-18
It didn't worked at first attempt: no printout, no error message.
Printing the test page from the system settings did work indeed.
By command line I could get this error:
```
~  lpr anyfile.pdf 
lpr: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory
```
The bug has been already filed at [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/libpng3/+bug/646636") (but none seems paying attention to it).
The workaround for me was:
```
# ln -s /lib/libpng12.so.0 /lib/libpng.so.3
# ls -l /lib/*png*
lrwxrwxrwx 1 root root     18 2010-10-18 08:15 libpng.so.3 -> /lib/libpng12.so.0
lrwxrwxrwx 1 root root     18 2010-10-14 09:18 libpng12.so.0 -> libpng12.so.0.44.0
-rw-r--r-- 1 root root 158736 2010-06-29 13:30 libpng12.so.0.44.0
```
Then I did the test again:
```
~  lpr anyfile.pdf 
**Package `cupsys-common' is not available.**
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
**WARNING: configuration file not found**
(12005) KSharedDataCache::Private::mapSharedMemory: Opening cache "/var/tmp/kdecache-enzo/icon-cache.kcache" page size is 4096
(12005) KSharedDataCache::Private::mapSharedMemory: Attached to cache, determining if it must be initialized
(12005) KSharedDataCache::Private::mapSharedMemory: Cache fully initialized -- attached to memory mapping
(12005) KSharedDataCache::Private::mapSharedMemory: 9203712 bytes available out of 10485760
ProcessEx::execute: <**/usr/bin/lpr.orig**|-#|1|-P|SCX-4623-Series|-h|-o|auth-info-required=none device-uri=usb://Samsung/SCX-4623%20Series finishings=3 job-hold-until=no-hold job-priority=50 marker-change-time=0 number-up=1 printer-commands=AutoConfigure,Clean,PrintSelfTestPage printer-info=Samsung SCX-4623 Series printer-is-accepting-jobs=true printer-is-shared=true printer-location=uqbar printer-make-and-model=Samsung SCX-4623 Series printer-state=3 printer-state-change-time=1287382072 printer-state-reasons=none printer-type=8523844 printer-uri-supported=ipp://localhost:631/printers/SCX-4623-Series scaling=100|anyfile.pdf>
**ProcessEx::execute: failed to launch**
```
So there seems to be two more issues (marked WITH bold).
I tried to fix the first one:
```
# apt-get install cupsys-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package cupsys-common
```
No way, then. It was reported as a warning so I tried just to skip it.
Then I went to the second issue:
```
# sudo find / -name lpr\*
/var/log/lpr.log.1
/var/log/lpr.log
/usr/bin/lpr
/usr/bin/lprm
/usr/local/bin/lpr
/usr/share/app-install/desktop/lprof.desktop
/usr/share/app-install/icons/lprof.png
/usr/share/doc/pnm2ppa/examples/sample_scripts/lprbw
/usr/share/doc/pnm2ppa/examples/sample_scripts/lprcolor
/usr/share/doc/pnm2ppa/examples/sample_scripts/lpreco
/usr/share/man/man1/lpr.1.gz
/usr/share/man/man1/lprm.1.gz
/usr/share/vim/vim72/syntax/lprolog.vim
/usr/share/vim/vim72/ftplugin/lprolog.vim
```
Let's try a quick workaround first.
```
# ln -s /usr/bin/lpr /usr/bin/lpr.orig
# lpr anyfile.pdf 
Package `cupsys-common' is not available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
WARNING: configuration file not found
(12042) KSharedDataCache::Private::mapSharedMemory: Opening cache "/var/tmp/kdecache-enzo/icon-cache.kcache" page size is 4096
(12042) KSharedDataCache::Private::mapSharedMemory: Attached to cache, determining if it must be initialized
(12042) KSharedDataCache::Private::mapSharedMemory: Cache fully initialized -- attached to memory mapping
(12042) KSharedDataCache::Private::mapSharedMemory: 9203712 bytes available out of 10485760
ProcessEx::execute: <**/usr/bin/lpr.orig**|-#|1|-P|SCX-4623-Series|-h|-o|auth-info-required=none device-uri=usb://Samsung/SCX-4623%20Series finishings=3 job-hold-until=no-hold job-priority=50 marker-change-time=0 number-up=1 printer-commands=AutoConfigure,Clean,PrintSelfTestPage printer-info=Samsung SCX-4623 Series printer-is-accepting-jobs=true printer-is-shared=true printer-location=uqbar printer-make-and-model=Samsung SCX-4623 Series printer-state=3 printer-state-change-time=1287382072 printer-state-reasons=none printer-type=8523844 printer-uri-supported=ipp://localhost:631/printers/SCX-4623-Series scaling=100|anyfile.pdf>
```
The print came out of my marvelous printer smoothly as expected.
I would say: that's it.
It would be indeed nicer if someone at the MOTU would make something to fix the first issue. The second one (the  missing lpr.orig) I think is up to the Samsung Unified Printer Driver maintainer.

---

### Post by ftoral on 2010-10-23
> **tweedledee said:**
> I'm completely swamped at work and don't have time to deal with this properly now.  However, I did download the beta driver and at least looked at the file structure, and it looks essentially unchanged.  Since they are still packing libstdc++5 and some other old libraries, I can't imagine they've updated enough of the core to begin to address the issue here, which is that the Samsung driver seems to be relying on fundamental linux libraries that were old years ago, and simply no longer reflect a modern linux distribution.  I've no idea what system Samsung is using for development and testing, but it needs an update.  Not even Red Hat enterprise, which makes Debian releases look speedy, has shipped that library in years.

It seem's that the question is about the static linking to the glibc.

An answer to a bug report on the debian bug tracker explain what is the cause of the problem: 
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=589143#10](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=589143#10)

i've reported this to a bug filled in launchpad about [netdiscovery: relocation error & segfault - Bug #576531]("https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/57653")

i'm not a C programmer, so i don't know if we could managed the proposed options without Samsung's source code.

---

### Post by tweedledee on 2010-10-23
> **anthonymke said:**
> However, after entering the repository URL into Synaptic and refreshing it, I get this error message from Synaptic:

It sounds like you may have entered the repository as a source repository rather than binary, or as both source and binary.  It is configured to work only as a binary repository.

---

### Post by tweedledee on 2010-10-23
> **uqbar said:**
> It didn't worked at first attempt: no printout, no error message.

I'm assuming you meant this errors arose using the installer from Samsung, which is known to have these (and many other) problems.  The repository files should not cause those problems.  If you were using repository files, let me know and I'll look into it.

---

### Post by tweedledee on 2010-10-23
> **ftoral said:**
> i'm not a C programmer, so i don't know if we could managed the proposed options without Samsung's source code.

We can't.  This is entirely on Samsung to resolve, or the eglibc programmers to accommodate this sort of static linking for all the various programs doing it.  I'm not optimistic the second will ever happen, nor the first any time soon.

---

### Post by anthonymke on 2010-10-24
> **tweedledee said:**
> It sounds like you may have entered the repository as a source repository rather than binary, or as both source and binary.  It is configured to work only as a binary repository.

I did enter it as binary... upon trying again a moment ago and refreshing in Synaptic, I got this error message:

> Failed to fetch [http://www.bchemnet.com/suldr/dists/debian/Release.gpg](http://www.bchemnet.com/suldr/dists/debian/Release.gpg)  Something wicked happened resolving ':http' (-5 - No address associated with hostname)
Failed to fetch [http://www.bchemnet.com/suldr/dists/debian/extra/i18n/Translation-en.bz2](http://www.bchemnet.com/suldr/dists/debian/extra/i18n/Translation-en.bz2)  Something wicked happened resolving ':http' (-5 - No address associated with hostname)
Failed to fetch [http://www.bchemnet.com/suldr/dists/debian/extra/i18n/Translation-en_US.bz2](http://www.bchemnet.com/suldr/dists/debian/extra/i18n/Translation-en_US.bz2)  Something wicked happened resolving ':http' (-5 - No address associated with hostname)
Failed to fetch [http://www.bchemnet.com/suldr/dists/debian/extra/binary-amd64/Packages.gz](http://www.bchemnet.com/suldr/dists/debian/extra/binary-amd64/Packages.gz)  Unable to connect to [www.bchemnet.com:http:]("http://www.bchemnet.com:http:")
Some index files failed to download, they have been ignored, or old ones used instead.I've checked the spelling (everything's spelled correctly)... not sure what else to do at this point.

---

### Post by tweedledee on 2010-10-24
> **anthonymke said:**
> I've checked the spelling (everything's spelled correctly)... not sure what else to do at this point.

Look at this bug report: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886)

There are various solutions proposed that work for some people in the discussion, all of which are related to network and/or router settings.  Other than the fact that my web host appeared to be really slow to respond around the time you posted your last message (consistent with the problems described in that bug), I can't think of what could be causing this to fail for you but work for me (and presumably most of the hundreds of users who reload it each day).

---

### Post by glixx on 2010-10-27
Hi tweedledee,

please help me, I can't add my printer to the Samsung Unified Driver Configurator (Qt4 interface).

Computer Processor: AMD 64-Bit

Linux-Distribution: Ubuntu 10.10, 32-Bit

Printer model: Samsung CLP-300N

Connection: Ethernet

Driver: samsungmfp-driver 3.00.65-3

Driver-Installation: your method *IIc: "Use the Samsung Unified Linux Driver repository"*


When I began with Linux (Ubuntu 9.04) the printer worked fine with the Samsung Unified Driver that I downloaded directly from Samsung's page. I also worked with 9.10. The first problem I got was when I installed 10.04. The printer was now only detected when I first booted the System and then switched on the CLP-300N.

Last week I did an update to 10.10 and now the printer is not detected anymore.

The error message when I try to start the Samsung Unified Driver Configurator:

> Server of CUPS printing system is not accessible at the moment.
As a result, you neither can print anything, nor even see your installed printers.
This situation might mean that your system is not configured properly and CUPS is not active printing system.
To resolve the problem, set CUPS printing system as default by means of your current Linux distribution.
Then you need to reboot your computer and try to run this application again.

Please refer to the documentation for details.
Then the Configurator started but I was not able to see the printer. Neither I couldn't install it. *Add printer* and the "Add printer wizard" started, then clicked *Next* and I could select a "Network Printer". Then clicked on search and the right IP was found. But when I then clicked *Next* there were no drivers shown.

So, I deinstalled this driver by following your instructions *IV. Uninstallation of the Driver* and then installed the Samsung driver by using the repository.

Now, I've installed:

samsungmfp-driver 3.00.65-3

samsungmfp-data 3.00.65-3

samsungmfp-scanner 3.00.65-3

samsungmfp-configuration-data 3.00.65-3

samsungmfp-configuration-qt4 3.00.65-3

**But exact the same problem is still there...** :confused:

What do I have do to, to make the printer work with Ubuntu 10.10?

**EDIT: Okay, one little step further...**

Because it was not possible to receive the CUPS Web-Interface by the adress *localhost:631* I deinstalled CUPS completly with Synaptic. Then I did a new installation of CUPS. And now there appears no error/warning message anymore.

And now the drivers will be shown in the Samsung Unified Driver Configurator. So I selected the only offered driver for the CLP-300N: *Samsung CLP-300 series (SPL-C)*

But when I try to print the test page by *Testing printer* nothing happens. *Checking driver* and *printing test page* report OK but the printer doesn't work. The Status in the printer spooler is *ausfuehren* (means run or execute)

(For testing reasons I installed this exactly on my Samsung n130 netbook and on my wife's notbook called ASUS X50R - both have the OS Ubuntu 10.04 - and it works fine on both!)

Thanks and regards

glixx

---

### Post by tweedledee on 2010-10-28
> **glixx said:**
> And now the drivers will be shown in the Samsung Unified Driver Configurator. So I selected the only offered driver for the CLP-300N: *Samsung CLP-300 series (SPL-C)*

Can you see, add, and/or test print when you install the printer using the Printing administration tool instead of the Samsung Configurator?

---

### Post by glixx on 2010-10-29
System -> Administration -> Print

1.) I can see the already installed printer

2.) I can click the "add" button

3.) When I'm searching for a network printer, I have the choice of two different ones: JetDirect (with the IP of the printer) and Samsung CLP-300 (current). further I can choose between LPD and IPP

4.) No matter which combination I choose, I can click on the button "print test page" but nothing happens

5.) And it is not possible to click on the button "add", but a new printer is shown in the printer admin tool...

---

### Post by karsta62 on 2010-10-31
With Samsung CLX-2160 USB, I have also the strange three parallel images problem on a fresh install of:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux

Drivers are installed by tweedledee's great instructions. Printing is ok. Scanning produces three black and whiteish stretched parallel images. The same happens with xSane, simplescan and the driver-gui's own scanning software. 

Any help much appreciated. Don't want to get back to winblows...

---

### Post by stumper on 2010-11-08
I get this when trying to install legacy scanner package. The newer one installs but does not work for me. The scanned image appears to be tripled.
```

http://www.bchemnet.com/suldr/dists/debian/extra/binary-amd64/samsungmfp-scanner_3.00.37-3.deb  404  Not Found
```

---

### Post by stumper on 2010-11-09
Hmmm...
I installed the i386 one and it works perfectly.

---

### Post by tweedledee on 2010-11-09
> **glixx said:**
> System -> Administration -> Print

1.) I can see the already installed printer

2.) I can click the "add" button

3.) When I'm searching for a network printer, I have the choice of two different ones: JetDirect (with the IP of the printer) and Samsung CLP-300 (current). further I can choose between LPD and IPP

4.) No matter which combination I choose, I can click on the button "print test page" but nothing happens

5.) And it is not possible to click on the button "add", but a new printer is shown in the printer admin tool...

I'm not sure what to make of this.  Perhaps a complete purge and reinstall of CUPS and then all the Samsung pieces?  If you have another printer you can try or if you can try the printer as USB to see if it's a general problem or specific to this printer?  It sounds to me more like a problem with the Ubuntu installation than the driver itself.

---

### Post by tweedledee on 2010-11-09
> **stumper said:**
> Hmmm...
I installed the i386 one and it works perfectly.

Odd; I'm not sure why the AMD64 file was missing.  I've re-uploaded it, so it should work now.

All versions of that package are actually the same, all they do is modify a configuration file.  I've simply never gotten around to constructing an "all architectures" pool in the repository.  So the i386 version should work, since the only difference is what architecture it claims to be.

---

### Post by tweedledee on 2010-11-09
> **karsta62 said:**
> Printing is ok. Scanning produces three black and whiteish stretched parallel images. The same happens with xSane, simplescan and the driver-gui's own scanning software. 

Any help much appreciated. Don't want to get back to winblows...

Try the legacy packages?

---

### Post by .zolder on 2010-11-11
Thank you very much tweedledee! I installed the needed drivers via the bchemnet repository. My USB connected CLP-300N got recognized and installed instantly by my 64bit 10.10.

cheers! \\:D/

---

### Post by Rodolfo Medina on 2010-11-11
Thank you for writing the guide.

Does the .deb packages give the possibilty to check the ink level?

Regards
Rodolfo

---

### Post by tweedledee on 2010-11-13
> **Rodolfo Medina said:**
> Thank you for writing the guide.

Does the .deb packages give the possibilty to check the ink level?

Regards
Rodolfo

The packages do not provide monitoring for ink levels; see part V of the main post for why, as the ability to do is part of utilities described there.

---

### Post by glixx on 2010-11-14
> **tweedledee said:**
> I'm not sure what to make of this.  Perhaps a complete purge and reinstall of CUPS and then all the Samsung pieces?  If you have another printer you can try or if you can try the printer as USB to see if it's a general problem or specific to this printer?  It sounds to me more like a problem with the Ubuntu installation than the driver itself.

I made a brand new installation of 10.10 and now it works fine. Thanks, tweedledee. :)

Regards

glixx

---

### Post by Rodolfo Medina on 2010-11-15
Many thanks to tweedledee for writing his guide.  I wrote the following
mini:

Howto: Samsung ML-1915 with Debian Lenny

Easy way to make Samsung ML-1915 printer work with Debian Lenny without
installing *any* package at all:

[http://forums.debian.net/viewtopic.php?f=16&t=57364](http://forums.debian.net/viewtopic.php?f=16&t=57364)

Bye.

---

### Post by DeathFire on 2010-11-19
Strange, the scanner on my Samsung SCX-4600 is not being recognized after an upgrade to 10.10.  The printing is still working fine.

I went to try installing the package again and am having problems.

When I try to add the repository and reload the package information I get this error.

```
Failed to fetch http://www.bchemnet.com/suldr/dists/debian/Release  Unable to find expected entry  extra/source/Sources in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.
```I started to do some looking on the [repository website]("http://www.bchemnet.com/suldr/index.html") and it looks like perhaps there is a website misconfiguration because when I try to [manually browse the packages I am getting a 403 error forbidden]("http://www.bchemnet.com/suldr/dists/debian/extra/"). 

Is anyone else experiencing a problem installing packages?

---

### Post by Menion on 2010-11-20
Same problem here, I'm unable to get the repository

---

### Post by yaq1 on 2010-11-20
Hi all,

me too:

W: Fehlschlag beim Holen von [http://www.bchemnet.com/suldr/dists/debian/Release](http://www.bchemnet.com/suldr/dists/debian/Release)  Unable to find expected entry  extra/source/Sources in Meta-index file (malformed Release file?)

Ubuntu 10.10, SCX 4521F

yaq1

---

### Post by karsta62 on 2010-11-21
> **tweedledee said:**
> Try the legacy packages?

That fixed the scanner indeed. Thank you so much!

---

### Post by tweedledee on 2010-11-21
> **yaq1 said:**
> W: Fehlschlag beim Holen von [http://www.bchemnet.com/suldr/dists/debian/Release](http://www.bchemnet.com/suldr/dists/debian/Release)  Unable to find expected entry  extra/source/Sources in Meta-index file (malformed Release file?)


I believe all of you having difficulty are trying to use the repository as a source repository, in addition to or instead of a binary.  This is binary-only, so the error is entirely appropriate: there are no source files to be found.

Let me know if difficulties continue after reconfiguring to binary-only, it works fine for me (and I can reproduce your error if I switch it to source).

Also, the 403 forbidden errors are not the issue; the server I'm currently using is configured to prevent directory listings, you can still access files if you know what to look for (which apt does).  I'd actually like to re-enable directory listings, but the host company doesn't seem to provide that option for the level of service I'm paying for.

---

### Post by tweedledee on 2010-11-21
> **Rodolfo Medina said:**
> Many thanks to tweedledee for writing his guide.  I wrote the following
mini:

Howto: Samsung ML-1915 with Debian Lenny

Easy way to make Samsung ML-1915 printer work with Debian Lenny without
installing *any* package at all:

[http://forums.debian.net/viewtopic.php?f=16&t=57364](http://forums.debian.net/viewtopic.php?f=16&t=57364)

Bye.
I added a note and link regarding this approach to the main guide.

---

### Post by Christian.Holland on 2010-11-21
Hi all, 
I found a solution for 
```
netdiscovery: relocation error: libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
```with adaptation of [http://darkswarm.org/whosyerdaddy-0.6.sh](http://darkswarm.org/whosyerdaddy-0.6.sh)
mentioned at [http://foldingforum.org/viewtopic.php?f=44&t=12939#p138466](http://foldingforum.org/viewtopic.php?f=44&t=12939#p138466)

Mainly it copies the whole /lib tree, adapts it according specific functions (strcmp) and a specific GLIBC (2.0). 
I dont know exactly what it does, but it works. 
The adapted lib tree is used aftwards with LD_LIBRARY_PATH. 
The script can be applied from any user, so it is harmless.

[LIST=1]
[*]Download and call the attached file ```
./whosyerdaddy-0.6+cho.sh
```The result is a script "/tmp/nostrcmp" and the tree "/tmp/nostrcmp.lib". Now the command ```
/tmp/nostrcmp xsane
``` works without the above error.
[*]The script "/tmp/nostrcmp" and the tree "/tmp/nostrcmp.lib" can be copied with sudo to /usr/local/bin for later usage. So any user can use ```
nostrcmp xsane
``` without any error message.
[*]Maybe create /usr/local/bin/xsane with the content: ```

#!/bin/bash
nostrcmp /usr/bin/xsane ${1:-"$@"}
```and chmod +x  /usr/local/bin/xsane. Now xsane can be called without error.
[/LIST]
   
Have fun,
Christian

---

### Post by tweedledee on 2010-11-21
> **Christian.Holland said:**
> Hi all, 
I found a solution for 
```
netdiscovery: relocation error: libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
```with adaptation of [http://darkswarm.org/whosyerdaddy-0.6.sh](http://darkswarm.org/whosyerdaddy-0.6.sh)
mentioned at [http://foldingforum.org/viewtopic.php?f=44&t=12939#p138466](http://foldingforum.org/viewtopic.php?f=44&t=12939#p138466)


It's not immediately obvious to me what it's doing either.  I may have some time in the next week or so (maybe) to look into this and possibly work it into another package to simplify use.  In the meantime, if anyone else uses and has success (or not), please share.

---

### Post by Menion on 2010-11-21
> **Christian.Holland said:**
> Hi all, 
I found a solution for 
```
netdiscovery: relocation error: libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
```with adaptation of [http://darkswarm.org/whosyerdaddy-0.6.sh](http://darkswarm.org/whosyerdaddy-0.6.sh)
mentioned at [http://foldingforum.org/viewtopic.php?f=44&t=12939#p138466](http://foldingforum.org/viewtopic.php?f=44&t=12939#p138466)

Mainly it copies the whole /lib tree, adapts it according specific functions (strcmp) and a specific GLIBC (2.0). 
I dont know exactly what it does, but it works. 
The adapted lib tree is used aftwards with LD_LIBRARY_PATH. 
The script can be applied from any user, so it is harmless.

[LIST=1]
[*]Download and call the attached file ```
./whosyerdaddy-0.6+cho.sh
```The result is a script "/tmp/nostrcmp" and the tree "/tmp/nostrcmp.lib". Now the command ```
/tmp/nostrcmp xsane
``` works without the above error.
[*]The script "/tmp/nostrcmp" and the tree "/tmp/nostrcmp.lib" can be copied with sudo to /usr/local/bin for later usage. So any user can use ```
nostrcmp xsane
``` without any error message.
[*]Maybe create /usr/local/bin/xsane with the content: ```

#!/bin/bash
nostrcmp /usr/bin/xsane ${1:-"$@"}
```and chmod +x  /usr/local/bin/xsane. Now xsane can be called without error.
[/LIST]
   
Have fun,
Christian

Hi, I tried your script but now I get this error:

xsane: symbol lookup error: /usr/local/bin/nostrcmp.lib/libc.so.6: undefined symbol: _IO_file_clos, version GLIBC_2.0

Ubuntu 10.10
Bye

---

### Post by yaq1 on 2010-11-21
> **tweedledee said:**
> I believe all of you having difficulty are trying to use the repository as a source repository, in addition to or instead of a binary.  This is binary-only, so the error is entirely appropriate: there are no source files to be found.

Let me know if difficulties continue after reconfiguring to binary-only, it works fine for me (and I can reproduce your error if I switch it to source).

Also, the 403 forbidden errors are not the issue; the server I'm currently using is configured to prevent directory listings, you can still access files if you know what to look for (which apt does).  I'd actually like to re-enable directory listings, but the host company doesn't seem to provide that option for the level of service I'm paying for.

yep, that did it for me! Funny enough, it seems, that Synaptic put in the "source"-repository by itself - I didn't enter one!?

OK, so now to the next step...

btw, thx!

---

### Post by DeathFire on 2010-11-22
> **tweedledee said:**
> I believe all of you having difficulty are trying to use the repository as a source repository, in addition to or instead of a binary.  This is binary-only, so the error is entirely appropriate: there are no source files to be found.

Let me know if difficulties continue after reconfiguring to binary-only, it works fine for me (and I can reproduce your error if I switch it to source).

Also, the 403 forbidden errors are not the issue; the server I'm currently using is configured to prevent directory listings, you can still access files if you know what to look for (which apt does).  I'd actually like to re-enable directory listings, but the host company doesn't seem to provide that option for the level of service I'm paying for.

Thank you.  I should have caught that myself!

Like the other poster, when I added the repository the source repository was created automatically.  It may be worth a note in the guide if this is something that changed between 10.04 and 10.10 as it will save many people headaches!

Again, thank you for the wonderful guide and work, this makes dealing with the MFP's so much easier!

---

### Post by cedric_tux on 2010-11-25
Tried the script from [Christian.Holland]("http://ubuntuforums.org/member.php?u=1191844").
There are any errors anymore when starting xsane or simple-scan. But i still can't scan from my network scanner. So the issue is not resolved, :-(

---

### Post by Rodolfo Medina on 2010-11-25
> **tweedledee said:**
> I added a note and link regarding this approach to the main guide.

Thanks!  :)

---

### Post by bishwa on 2010-11-27
Hi Tweedledee, thanks for this great resource. I have a samsung scx-4521f (multi function printer) running on a linux mint 9 box which I'm using as a workstation/soho server. I followed your recommended installation for the unified driver from the repository. All good, I can print to it now from the host and 3 clients. 

I want to get the scanner going as well (I installed that package via synaptic too). I tried to access the scanner with 'Simple Scan' but it isn't even detecting the scanner. I then tried to open your 'Samsung Unified Driver Configurator' to see if there were any settings I could adjust and nothing happens, nothing launches! I can see that the configurator executable is there in the opt/Samsung/mfp/bin directory. So I guess I have 2 questions:
1. is my software install corrupted or something in order to cause the configurator not to launch?
2. is this a connected issue with not being able to see the scanner in Simple Scan.

Any clues / advice please?

Cheers

---

### Post by Rodolfo Medina on 2010-11-27
Hi, Tweedledee:

would you please excuse this off-topic.  As far as you know, is it possible to
reduce the printer margins to a very small value at my pleasure?  I have some
pdf documents with very small margins and don't manage to avoid that the text
in them be partially cut off by my ML-1915.  I tried to edit the ppd file with
no result.

Thanks you for any reply
Rodolfo

---

### Post by tweedledee on 2010-11-29
> **bishwa said:**
> 1. is my software install corrupted or something in order to cause the configurator not to launch?
2. is this a connected issue with not being able to see the scanner in Simple Scan.


1. Try running /opt/Samsung/mfp/bin/Configurator and/or /opt/Samsung/mfp/bin/netdiscovery in a terminal and see if any errors are generated.

2. Yes.

---

### Post by tweedledee on 2010-11-29
> **Rodolfo Medina said:**
> Hi, Tweedledee:

would you please excuse this off-topic.  As far as you know, is it possible to
reduce the printer margins to a very small value at my pleasure?  I have some
pdf documents with very small margins and don't manage to avoid that the text
in them be partially cut off by my ML-1915.  I tried to edit the ppd file with
no result.

Thanks you for any reply
Rodolfo

No, but I haven't tried.  If you are trying to go much below ~0.2 in (0.5 cm), most printers have a physical limitation of being unable to print in those margins.  And usually one of the four edges is about twice that as a physical limit.  You are probably better off scaling down to 98% or similar with narrow margins to get everything to appear.

---

### Post by bishwa on 2010-11-30
Ok thanks I tried what you suggested and got the following:

bishwa@server ~ $ /opt/Samsung/mfp/bin/Configurator
/opt/Samsung/mfp/bin/Configurator: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory

and


bishwa@server ~ $ /opt/Samsung/mfp/bin/netdiscovery
netdiscovery: relocation error: /lib/libnss_files.so.2: symbol __rawmemchr, version GLIBC_2.2.5 not defined in file libc.so.6 with link time reference
netdiscovery: relocation error: /lib/libnss_files.so.2: symbol __rawmemchr, version GLIBC_2.2.5 not defined in file libc.so.6 with link time reference
netdiscovery: relocation error: /lib/libnss_files.so.2: symbol __rawmemchr, version GLIBC_2.2.5 not defined in file libc.so.6 with link time reference
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
# Total 0 printers found, 2s elapsed

---

### Post by tweedledee on 2010-11-30
> **bishwa said:**
> Ok thanks I tried what you suggested and got the following:

bishwa@server ~ $ /opt/Samsung/mfp/bin/Configurator
/opt/Samsung/mfp/bin/Configurator: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory


Odd.  That sounds like the libpng3 package is not installed, which should have been pulled in with the Configurator.  You can try to re-install it, download a deb from debian or Ubuntu to use, or simply create the link yourself (all the package installs) from libpng.so.3 to libpng12.so.3 using ln -s in /usr/lib.

> **bishwa said:**
> bishwa@server ~ $ /opt/Samsung/mfp/bin/netdiscovery
netdiscovery: relocation error: /lib/libnss_files.so.2: symbol __rawmemchr, version GLIBC_2.2.5 not defined in file libc.so.6 with link time reference
netdiscovery: relocation error: /lib/libnss_files.so.2: symbol __rawmemchr, version GLIBC_2.2.5 not defined in file libc.so.6 with link time reference
netdiscovery: relocation error: /lib/libnss_files.so.2: symbol __rawmemchr, version GLIBC_2.2.5 not defined in file libc.so.6 with link time reference
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
# Total 0 printers found, 2s elapsed

That is an ongoing error with recent 64-bit installations due to a library change, and what a good chunk of the 50-100 posts prior to yours discuss.  Summary: there isn't a good solution at the moment, although there is a script posted a little while ago that you can try, and that I'm hoping to adapt for use as soon as I find a few hours to spend on it.

---

### Post by bishwa on 2010-12-01
> **tweedledee said:**
> Odd.  That sounds like the libpng3 package is not installed, which should have been pulled in with the Configurator.  You can try to re-install it, download a deb from debian or Ubuntu to use, or simply create the link yourself (all the package installs) from libpng.so.3 to libpng12.so.3 using ln -s in /usr/lib.

Tried a reinstall, no joy. 
Tried to create the link as above: 
bishwa@server ~ $ ln -s in /usr/lib
ln: creating symbolic link `/usr/lib/in': File exists
Then tried opening the configurator, no joy again. Did I do this correctly?

> **tweedledee said:**
> 
That is an ongoing error with recent 64-bit installations due to a library change, and what a good chunk of the 50-100 posts prior to yours discuss.  Summary: there isn't a good solution at the moment, although there is a script posted a little while ago that you can try, and that I'm hoping to adapt for use as soon as I find a few hours to spend on it.

Ok, I'll keep an eye on this progress thanks. I'm new to linux, there's a lot to like and a lot to learn. However the printer/scanner here is essential to my small business operations. I'm thinking that if I need to upgrade to another mfp device in order to get full functionality, then I'd like to support a company that writes good and complete drivers for linux. Is there any particular (brand / model) mono laser mfp device, that you know of that works really well with linux?

---

### Post by tweedledee on 2010-12-01
> **bishwa said:**
> Tried a reinstall, no joy. 
Tried to create the link as above: 
bishwa@server ~ $ ln -s in /usr/lib
ln: creating symbolic link `/usr/lib/in': File exists
Then tried opening the configurator, no joy again. Did I do this correctly?

Run these commands in the terminal is this:```
ln /usr/lib/libpng* -ld
sudo ln -s /usr/lib/libpng12.so.3 /usr/lib/libpng.so.3
```

The first will just output all libpng-related files, mostly as a check so I don't have to ask you for more information in the event the second command fails to work.  If the Configurator fails to work after running the second command (which creates the necessary link), please post the output of the first command.

> **bishwa said:**
> Ok, I'll keep an eye on this progress thanks. I'm new to linux, there's a lot to like and a lot to learn. However the printer/scanner here is essential to my small business operations. I'm thinking that if I need to upgrade to another mfp device in order to get full functionality, then I'd like to support a company that writes good and complete drivers for linux. Is there any particular (brand / model) mono laser mfp device, that you know of that works really well with linux?

Your Samsung mfp might work if you use a 32-bit installation, this particular issue is only a problem for 64-bit.  As far as other brands, Brother offers Linux drivers in the same way Samsung does and I'm not sure how reliable they are.  There are many reports they work.  HP has very good Linux support for printing, I have no experience with the scanning part of a multifunction printer.  I rely on an old-fashion dedicated scanning for all my needs (which has always worked well), so have very limited experience with the multifunction aspect.

---

### Post by bishwa on 2010-12-03
Thanks again for your time with this. I ran the commands as you suggested:

bishwa@server ~ $ ln /usr/lib/libpng* -ld
ln: invalid option -- 'l'
Try `ln --help' for more information.
bishwa@server ~ $ sudo ln -s /usr/lib/libpng12.so.3 /usr/lib/libpng.so.3
ln: creating symbolic link `/usr/lib/libpng.so.3': File exists

Configurator still doesn't work.

I'm running 64 bit so I can utilise all the ram in this box and allow for expansion if needed later on, so I don't really want to go to a 32bit operating system. I'll look into an HP mfp as a fall back if I have no luck getting the scanner part of the Samsung mfp going. Pity though, it's been a good little work horse and cheap to run.

Cheers

---

### Post by tweedledee on 2010-12-03
> **bishwa said:**
> bishwa@server ~ $ ln /usr/lib/libpng* -ld
ln: invalid option -- 'l'

Oops.  I should have typed "ls" not "ln" for that command.

---

### Post by bishwa on 2010-12-04
No problem, it now returns:

bishwa@server ~ $ ls /usr/lib/libpng* -ld
lrwxrwxrwx 1 root root 13 2010-12-02 09:34 /usr/lib/libpng.so.3 -> libpng12.so.0

and then

bishwa@server ~ $ sudo ln -s /usr/lib/libpng12.so.3 /usr/lib/libpng.so.3
[sudo] password for bishwa: 
ln: creating symbolic link `/usr/lib/libpng.so.3': File exists

---

### Post by fedetxf on 2010-12-04
Just a small suggestion. The desktop file's category in 

/usr/share/applications/samsungUDC.desktop

should be something like 

Categories=Settings;HardwareSettings;Printing;Qt

The category Samsung used does not follow Freedesktop's standard ([http://standards.freedesktop.org/menu-spec/latest/apa.html](http://standards.freedesktop.org/menu-spec/latest/apa.html))

That change would make the icon appear with the rest of the settings applications.

---

### Post by Christian.Holland on 2010-12-04
Hi all,
sorry to answer a bit late. I am not always on.
To clarify some things about [http://ubuntuforums.org/showpost.php?p=10145034&postcount=536](http://ubuntuforums.org/showpost.php?p=10145034&postcount=536). I am using:
> 
$ cat  /etc/issue
Ubuntu 10.04.1 LTS \n \l
that is the reason for line 20 in whosyerdaddy-0.6+cho.sh.
> 
GLIBC=GLIBC_2.0
So eventally this line has to commented out of for GLIBC_2.2.5.
As well the symbol __rawmemchr has to be inserted.

Hi [yaq1]("http://ubuntuforums.org/member.php?u=1191456")
may be try to insert a row in line 13 of 
whosyerdaddy-0.6+cho.sh
> _IO_file_close[Hi cedric_tux]("http://ubuntuforums.org/member.php?u=1186340")
are there any error messages ?

---

### Post by tweedledee on 2010-12-05
> **bishwa said:**
> No problem, it now returns:

bishwa@server ~ $ ls /usr/lib/libpng* -ld
lrwxrwxrwx 1 root root 13 2010-12-02 09:34 /usr/lib/libpng.so.3 -> libpng12.so.0

Hm.  I think Ubuntu and/or Mint broke the libpng3 package; yet another one that I'll need to package up myself.  Anyway, try this in a terminal:```
ls /lib/libpng* -ld
```

If you get no files, make sure libpng12-0 is installed (but it should be).

If you get a list of several files, try this ```
sudo mv /usr/lib/libpng3.so.3 /usr/lib/libpng3.so.3-old
sudo ln -s /lib/libpng12.so.3 /usr/lib/libpng.so.3
``` then try the Configurator again.

---

### Post by tweedledee on 2010-12-05
> **fedetxf said:**
> Just a small suggestion. The desktop file's category in 

/usr/share/applications/samsungUDC.desktop

should be something like 

Categories=Settings;HardwareSettings;Printing;Qt

The category Samsung used does not follow Freedesktop's standard ([http://standards.freedesktop.org/menu-spec/latest/apa.html](http://standards.freedesktop.org/menu-spec/latest/apa.html))

That change would make the icon appear with the rest of the settings applications.

First, you are correct, the category Samsung used doesn't follow the standards at all.  The file shipped with my packages is created on the fly, not a Samsung file.

Second, the category for the file I created is arbitrary.  You obviously seem to use the Configuator as a settings program, which is perfectly reasonable.  Many others use is primarily as a scanning program, which matches where I currently have it assigned.  There's a third reasonable option that fits within the standards that escapes me at the moment, but I remember trying to deal with it when first packaging all this up.

The short version is that I could make it scanner-focused, settings-focused, or a mixture of both (with multiple menu entries).  I hate multiple menu entries for the same program, so I flipped a coin.  I could be persuaded to move it to settings if enough people indicate a bias toward that vs. scanning, or even multiple entries since I don't actually keep the Configuator installed and hence multiple menu entries doesn't really affect me.

So if anyone else has an opinion, express it and I'll consider all expressed opinions when I next update the packages.

---

### Post by bishwa on 2010-12-05
Ok I tried the following as suggested:

bishwa@server ~ $ ls /lib/libpng* -ld
lrwxrwxrwx 1 root root     18 2010-09-27 00:46 /lib/libpng12.so.0 -> libpng12.so.0.42.0
-rw-r--r-- 1 root root 158736 2010-07-06 03:55 /lib/libpng12.so.0.42.0

bishwa@server ~ $ sudo mv /usr/lib/libpng3.so.3 /usr/lib/libpng3.so.3-old
mv: cannot stat `/usr/lib/libpng3.so.3': No such file or directory
bishwa@server ~ $ sudo ln -s /lib/libpng12.so.3 /usr/lib/libpng.so.3
ln: creating symbolic link `/usr/lib/libpng.so.3': File exists

Still no luck launching the configurator.

---

### Post by tweedledee on 2010-12-05
> **bishwa said:**
> Still no luck launching the configurator.

I shouldn't give advice while sleep-deprived.  Do this ```
sudo mv /usr/lib/libpng.so.3 /usr/lib/libpng.so.3-old
sudo ln -s /lib/libpng12.so.0 /usr/lib/libpng.so.3
```

---

### Post by bishwa on 2010-12-05
Ha ha, still 100% better than I can manage, ok tried it and got this:

bishwa@server ~ $ sudo mv /usr/lib/libpng.so.3 /usr/lib/libpng.so.3-old
mv: cannot stat `/usr/lib/libpng.so.3': No such file or directory
bishwa@server ~ $ sudo ln -s /lib/libpng12.so.0 /usr/lib/libpng.so.3^C

Configurator no go.

---

### Post by tweedledee on 2010-12-06
> **bishwa said:**
> Ha ha, still 100% better than I can manage, ok tried it and got this:

bishwa@server ~ $ sudo mv /usr/lib/libpng.so.3 /usr/lib/libpng.so.3-old
mv: cannot stat `/usr/lib/libpng.so.3': No such file or directory
bishwa@server ~ $ sudo ln -s /lib/libpng12.so.0 /usr/lib/libpng.so.3^C

Configurator no go.

Odd.  Try this ```
sudo ln -s /lib/libpng12.so.0 /usr/lib/libpng12.so.0
ls /usr/lib/libpng* -ld
```

I don't know why the existing link is such a problem, but this essentially adds another link from the first link (libpng.so.3) to the actual file we're trying to find (/lib/libpng12.so.0, actually itself another link, but that's irrelevant).  So rather than repair the inappropriate link, we'll add another link to work around it.  The second command is just to verify what's going on.

Then try the Configurator again.

---

### Post by bishwa on 2010-12-07
Tricky one eh!

bishwa@server ~ $ sudo ln -s /lib/libpng12.so.0 /usr/lib/libpng12.so.0
ln: creating symbolic link `/usr/lib/libpng12.so.0': File exists

bishwa@server ~ $ ls /usr/lib/libpng* -ld
lrwxrwxrwx 1 root root 18 2010-12-07 16:42 /usr/lib/libpng12.so.0 -> /lib/libpng12.so.0
lrwxrwxrwx 1 root root 18 2010-12-06 14:13 /usr/lib/libpng.so.3-old -> /lib/libpng12.so.0

Still won't launch.

---

### Post by tweedledee on 2010-12-07
> **bishwa said:**
> Tricky one eh!

bishwa@server ~ $ sudo ln -s /lib/libpng12.so.0 /usr/lib/libpng12.so.0
ln: creating symbolic link `/usr/lib/libpng12.so.0': File exists

bishwa@server ~ $ ls /usr/lib/libpng* -ld
lrwxrwxrwx 1 root root 18 2010-12-07 16:42 /usr/lib/libpng12.so.0 -> /lib/libpng12.so.0
lrwxrwxrwx 1 root root 18 2010-12-06 14:13 /usr/lib/libpng.so.3-old -> /lib/libpng12.so.0

Still won't launch.

Odder still.  Apparently the error messages don't mean anything...  Try this ```

sudo mv /usr/lib/libpng.so.3-old /lusr/lib/libpng.so.3
ls /usr/lib/libpng* -l
``` and the Configurator again.

---

### Post by bishwa on 2010-12-08
Ok,

bishwa@server ~ $ sudo mv /usr/lib/libpng.so.3-old /lusr/lib/libpng.so.3
mv: cannot move `/usr/lib/libpng.so.3-old' to `/lusr/lib/libpng.so.3': No such file or directory
bishwa@server ~ $ ls /usr/lib/libpng* -l
lrwxrwxrwx 1 root root 18 2010-12-07 16:42 /usr/lib/libpng12.so.0 -> /lib/libpng12.so.0
lrwxrwxrwx 1 root root 18 2010-12-06 14:13 /usr/lib/libpng.so.3-old -> /lib/libpng12.so.0

no launch!

---

### Post by freerussianet on 2010-12-08
p { margin-bottom: 0.21cm; }  Sorry, I have an urgent problem during the installation. At the step 3, most likely. Printers found – and there is my printer – next. And than the page
 Driver for your printer
 Choose a driver that will convert output data  to printer specific format 
 And an empty field after it.
 

 The thing is what I am installing but the driver for the printer? :-)
 If I cancel the installation, than I have to remove it as it is written at the instruction? What should I do and how to settle the problem?
 

 I have CLX-2160 and Ubuntu 10.10 for 32bit.
 

 Thank you in advance

---

### Post by tweedledee on 2010-12-08
> **bishwa said:**
> Ok,

bishwa@server ~ $ sudo mv /usr/lib/libpng.so.3-old /lusr/lib/libpng.so.3
mv: cannot move `/usr/lib/libpng.so.3-old' to `/lusr/lib/libpng.so.3': No such file or directory
bishwa@server ~ $ ls /usr/lib/libpng* -l
lrwxrwxrwx 1 root root 18 2010-12-07 16:42 /usr/lib/libpng12.so.0 -> /lib/libpng12.so.0
lrwxrwxrwx 1 root root 18 2010-12-06 14:13 /usr/lib/libpng.so.3-old -> /lib/libpng12.so.0

no launch!

Try reinstalling the libpng3 package.

If it still doesn't work, I may have to give up.  I know the problem is that you are missing a key link (shortcut) from the name that the driver is looking for to the actual library file, but I've never had any system refuse to work with the links in quite this way, to the point of denying they exist yet obviously displaying them.

---

### Post by tweedledee on 2010-12-08
> **freerussianet said:**
>  If I cancel the installation, than I have to remove it as it is written at the instruction? What should I do and how to settle the problem?

You should be fine to cancel and then run the standard stystem tool or Configurator to install your printer later.  If it gets to the point of asking you to choose your printer, the driver is installed and should work.  Sometimes the installer interface is unreliable, although I'm not familiar with the particular problem you are describing.

---

### Post by freerussianet on 2010-12-09
p { margin-bottom: 0.21cm; }  Unfortunately, no. It does not work. It asks me for some driver. And in the Unified Driver Configuration's window there is no any printer. By the way the scanner is their &#8212; in the next tab. May be there is some problem with CUPS?

And I have the same problem in Add Printer menu...
 

 Sorry, I'm absolutely new to Linux system...

---

### Post by tweedledee on 2010-12-09
> **freerussianet said:**
> p { margin-bottom: 0.21cm; }  Unfortunately, no. It does not work. It asks me for some driver. And in the Unified Driver Configuration's window there is no any printer. By the way the scanner is their — in the next tab. May be there is some problem with CUPS?

And I have the same problem in Add Printer menu...
 

 Sorry, I'm absolutely new to Linux system...

I'd suggest cleaning out the failed installation and using my repository to more cleanly interface with the rest of your system.  You can also try re-installing CUPS, but that's not usually the issue, and can actually cause problems when you have a partial install of the Samsung driver from their installer.

---

### Post by bishwa on 2010-12-12
> **tweedledee said:**
> Try reinstalling the libpng3 package.

If it still doesn't work, I may have to give up.  I know the problem is that you are missing a key link (shortcut) from the name that the driver is looking for to the actual library file, but I've never had any system refuse to work with the links in quite this way, to the point of denying they exist yet obviously displaying them.
Ok, I uninstalled libpng 3 and it took the folowing with it:
samsungmfp-configurator-data
samsungmfp-configurator-qt3
samsungmfp-lpr
I then reinstalled libpn3 and the samsungmfp packages. That fixed the link to the configurator, it now launches. Thanks for all your help with this:)

My next step is to try and get the scanner going, in the configurator it's telling me that no scanners are identified. You mentioned that there's a lot of chat about this issue in previous posts, so I'll trawl through an see what I can glean, any recommended starting point (page)?

---

### Post by bishwa on 2010-12-12
My printing is still working fine. But interestingly, if I try to print a test page from the Samsung Configurator, it returns: checking driver...Ok. Printing test page... Failed.

But then I can print a test page ok from 'system-config-printer 1.2.0' with no problem?

---

### Post by tweedledee on 2010-12-12
> **bishwa said:**
> My printing is still working fine. But interestingly, if I try to print a test page from the Samsung Configurator, it returns: checking driver...Ok. Printing test page... Failed.

But then I can print a test page ok from 'system-config-printer 1.2.0' with no problem?

I think this is related to the scanner issue, but not in itself a problem.  See the first note (the big "Please note" near the very top) of the first post.  I recently updated it to refer specifically to posts that provide possible solutions.  Pretty much everything I could help you with is contained either in the note or in the posts referred to (which are generally not mine).

---

### Post by cedric_tux on 2010-12-15
@Christian Holland

Here my error messages

user:~/Downloads$ ./whosyerdaddy-0.6+cho.sh 
workaround for "netdiscovery: relocation error: libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference"
Copyright (c) 2010 by Christian Holland <mail@cholland.de> with adaptations of
whosyerdaddy 0.6, workaround for broken Folding@Home client 6.29 binaries
Copyright (c) 2010 by Kris Rusocki <kszysiu@gmail.com>
Licensed under GPLv2

Checking for awk bc cat chmod cut dd grep head od readelf sed tac tr ...done.
cp: cannot create special file `/tmp/nostrcmp.lib/udev/devices/net/tun': Operation not permitted
cp: cannot create special file `/tmp/nostrcmp.lib/udev/devices/ppp': Operation not permitted
cp: cannot create special file `/tmp/nostrcmp.lib/udev/devices/console': Operation not permitted
cp: cannot create special file `/tmp/nostrcmp.lib/udev/devices/loop0': Operation not permitted
cp: cannot create special file `/tmp/nostrcmp.lib/udev/devices/null': Operation not permitted
cp: cannot open `/lib/ufw/user.rules' for reading: Permission denied
cp: cannot open `/lib/ufw/user6.rules' for reading: Permission denied
analyse TARGET libc.so.6
WARNING: no STRTAB, going with 0x30 offset %-| and single-page size. YMMV.
DYNSYM at 0x00003c28
processing symbol strcmp
ERROR unable to find symbol, skipping
Rebranding shared objects... /tmp/nostrcmp.lib created
check it e.g. with '/tmp/nostrcmp xsane'
install it e.g. with 'sudo cp -a /tmp/nostrcmp /tmp/nostrcmp.lib /usr/local/bin'
done.
user:/Downloads$ /tmp/nostrcmp /usr/bin/simple-scan 
netdiscovery: relocation error: /tmp/nostrcmp.lib/libnss_files.so.2: symbol __rawmemchr, version GLIBC_2.2.5 not defined in file libc.so.6 with link time reference
netdiscovery: relocation error: /tmp/nostrcmp.lib/libnss_files.so.2: symbol __rawmemchr, version GLIBC_2.2.5 not defined in file libc.so.6 with link time reference
netdiscovery: relocation error: /tmp/nostrcmp.lib/libnss_files.so.2: symbol __rawmemchr, version GLIBC_2.2.5 not defined in file libc.so.6 with link time reference
/tmp/nostrcmp: line 4: type: nostrcmp: not found
install it e.g. with 'sudo cp -a /tmp/nostrcmp /tmp/nostrcmp.lib /usr/local/bin'

---

### Post by ldej on 2010-12-25
i have a ml-2525 and i'm new with ubuntu and linux altogether. i'm learning the language (spoken/ written) but don't have much help from anyone but a friend. i really needed my printer this morning and it didn't work. 

can you give a simple step by step for amateurs?? or a one-click solution??

thanks!!

---

### Post by tweedledee on 2010-12-26
> **ldej said:**
> can you give a simple step by step for amateurs?? or a one-click solution??

No.  The first post IS the list of "simple" options.  Take it up with Samsung if you don't like it.

If the only thing you've tried is plugging in and turning on the printer, the next thing to try is to open the administration -> printing tool (or equivalent if you are not using Gnome) and add a new printer that way (which may or may not autodetect your printer once you start it).

Probably the next simplest approach with the greatest probability of working is the "IIc" repository approach described in the first post.  Setting up the repository may seem complex at first but isn't really.  Install the samsungmfp-driver package and whatever else it drags in with it, then try to add a new printer and you should be able to find the appropriate driver (it most likely won't automatically match).

---

### Post by okkadiroglu on 2010-12-28
Hi,

I had many problems with Samsung CLX-2160 operating under Ubuntu 10.04 LTS (64 bits). Due to a disk problem I reinstalled the operating system and I am using Samsung Unified Linux Driver (Common 3.00.37, Printer 3.00.20, Scanner 3.00.06 Build 152) and everything works perfectly well without any problem.:D (For the time being until the new update) ;)

Happy New Year and Best Regards

---

### Post by BlueMoon75 on 2011-01-01
Hello experts,

I have a Samsung CLP-510N and I want to get it work under Ubuntu 10.10.

So I tried to "**IIc.** *Use the Samsung Unified Linux Driver repository" *from the first thread here, but I get an error while refreshing the repository listing: [http://www.bchemnet.com/suldr/dists/debian/Release](http://www.bchemnet.com/suldr/dists/debian/Release) Unable to find expected entry extra/source/Sources in Meta-index file.

As I tried to download the .deb-files directly from [http://www.bchemnet.com/suldr/dists/debian/extra/](http://www.bchemnet.com/suldr/dists/debian/extra/) I get the 403 Forbidden error-page:
**Forbidden**

 Access denied. Please click on the back button to return to the  former page. We cannot locate the page you are looking for. Please check  the address and make sure all letters are lowercased with no spaces.
 [www.bchemnet.com]("http://www.bchemnet.com") [http://www.bchemnet.com]("http://www.bchemnet.com/")

So I want to ask you, if the page is only temporarily down or is there another place to get the repository.

Many thanks in advance,

Michael

---

### Post by tweedledee on 2011-01-01
> **BlueMoon75 said:**
> Unable to find expected entry extra/source/Sources in Meta-index file.

As I tried to download the .deb-files directly from [http://www.bchemnet.com/suldr/dists/debian/extra/](http://www.bchemnet.com/suldr/dists/debian/extra/) I get the 403 Forbidden error-page:
**Forbidden**

Disable the source repository, leaving only the binary component enabled, and it should work fine.

The 403 error is due to a server configuration issue I'm stuck with unless I pay more for a different hosting service.  I will probably change the error page today to reflect that information, because I can at least control that.

---

### Post by BlueMoon75 on 2011-01-02
Perfect! 
Thanks for your help and also thank you for the very good tutorial!!!

---

### Post by bittner on 2011-01-06
> **okkadiroglu said:**
> Hi,

I had many problems with Samsung CLX-2160 operating under Ubuntu 10.04 LTS (64 bits). Due to a disk problem I reinstalled the operating system and I am using Samsung Unified Linux Driver (Common 3.00.37, Printer 3.00.20, Scanner 3.00.06 Build 152) and everything works perfectly well without any problem.:D (For the time being until the new update) ;)

Happy New Year and Best Regards

Printing *and* scanning both works for me too on Ubuntu 10.10 Maverick!

Note: Only the legacy packages work for me (I installed them via the repository as of [http://www.bchemnet.com/suldr/index.html]("http://www.bchemnet.com/suldr/index.html"), and [this thread's first page]("http://ubuntuforums.org/showthread.php?t=341621")). With the normal packages printing works fine but scanning does not: the scanned page is 3 times the original in the flatbed (squashed vertically and placed right next to each other three times).

Just for historical porposes, here is what *sane-find-scanner* and *scanimage* said with the normal packages: (I found the two commands in [this thread]("http://ubuntuforums.org/showthread.php?t=838580"))
```
~$ sudo sane-find-scanner -q 
found USB scanner (vendor=0x04e8 [Samsung Electronics Co., Ltd.], product=0x3425 [CLX-216x Series]) at libusb:001:007
~$ sudo scanimage -L
netdiscovery: relocation error: /lib/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
netdiscovery: relocation error: /lib/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
device `smfp:SAMSUNG CLX-216x Series on USB:0' is a SAMSUNG CLX-216x Series on USB:0 Flatbed Scanner
```
And here is what they say with the legacy packages: (... which looks much better!)
```
~$ sudo sane-find-scanner -q 
found USB scanner (vendor=0x04e8 [Samsung Electronics Co., Ltd.], product=0x3425 [CLX-216x Series]) at libusb:001:005
~$ sudo scanimage -L
device `smfp:SAMSUNG CLX-216x Series on USB:0' is a SAMSUNG CLX-216x Series on USB:0 Flatbed Scanner

```

This is how I installed the packages:
```
sudo apt-get install samsungmfp-legacy-data samsungmfp-legacy-driver samsungmfp-legacy-scanner samsungmfp-legacy-configurator-qt3 samsungmfp-legacy-configurator-data
```
Thanks so much everyone!!

---

### Post by przekop on 2011-01-13
Hi
Does scanning over the network works for anyone?
I intend to buy Samsung - CLX-3185FN.
I also consider HP LaserJet Pro CM1415FN.
I use 32 bit system.

---

### Post by mozkill on 2011-01-13
So glad I bought a Samsung CLP-315 and use the IPP protocol to connect to it.   Its easy and I can ignore this post.

---

### Post by cedric_tux on 2011-01-13
Hi [tweedledee]("http://ubuntuforums.org/member.php?u=207037")

Why the package samsungmfp-configurator-qt4_3.00.65-3_amd64.deb is creating an empty directory in /opt.
Is there a reason or is just a little bug? In case this is a bug, could you correct it?

Cédric

---

### Post by cedric_tux on 2011-01-14
Hi

Concerning Post #555, i agree with [fedetxf]("http://ubuntuforums.org/member.php?u=30454").
As the name of the link is "Samsung Configurator" i personnally think that Configuration is a setting program and not a Graphics Program.

Thanks a lot a have a nice weekend

---

### Post by cedric_tux on 2011-01-17
The solution for the libnss problem for the new glibc has been resolved by [COLOR=Black][]("https://launchpad.net/%7Ewolf-womaro")[/COLOR][Wolf Geldmacher]("https://launchpad.net/%7Ewolf-womaro") at:

[https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/576531](https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/576531)

to be able to use this workaround you have to install samsungmfp-configurator-qt4 (or qt3)

QUESTION to [tweedledee]("http://ubuntuforums.org/member.php?u=207037"), could you include this workaround in you packages?


I'll post the workaround here:

As a workaround to get the scanner working on lucid (until Samsung  gets around to fixing this): I found that performing the renaming game  for the libnss_* libraries above and then casting the result into a  replacement **netdiscovery**  shell procedure, followed by restoring the (no longer needed) libnss_*  libraries to their original state works fine for my (static!)  configuration (CLX-3185FW)
 i.e. (as root, after having installed the MFP software)
cd /opt/Samsung/mfp/bin
mv **netdiscovery** **netdiscovery**.orig
cd /lib
mkdir backup
mv libnss_* backup
cd /opt/Samsung/mfp/bin
./**netdiscovery** --all --scanner >/tmp/output
 (In my case this resulted in:
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
ip: 192.168.192.3   slp: 0,0,0,0 snmp: 0,0,0 dsc: "Samsung CLX-3180"
a8 00 43 10 53 61 6d 73 75 6e 67 20 53 61 6d 73
75 6e 67 20 43 4c 58 2d 33 31 38 30 20 53 65 72
69 65 73 20 19 33 86 2b 00 00 27 d8 00 00 41 a0
00 01 51 00 00 01 00 00 00 00 41 a0 00 00 36 d8
00 00 05 05 19 00
# Total 1 scanners found, 5s elapsed
)
 Edit /tmp/output to contain (replacing the text between '' by the output of the command above!):
#!/bin/sh
echo '# Network printers discovery utility'
echo '# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description'
echo 'ip: 192.168.192.3   slp: 0,0,0,0 snmp: 0,0,0 dsc: "Samsung CLX-3180"'
echo 'a8 00 43 10 53 61 6d 73 75 6e 67 20 53 61 6d 73'
echo '75 6e 67 20 43 4c 58 2d 33 31 38 30 20 53 65 72'
echo '69 65 73 20 19 33 86 2b 00 00 27 d8 00 00 41 a0'
echo '00 01 51 00 00 01 00 00 00 00 41 a0 00 00 36 d8'
echo '00 00 05 05 19 00'
echo '# Total 1 scanners found, 5s elapsed'
 mv /tmp/output **netdiscovery**
chmod 755 **netdiscovery**
cd /lib
mv backup/* .
rmdir backup



Have a nice scanning over network!!:popcorn:

---

### Post by tweedledee on 2011-01-21
> **cedric_tux said:**
> Hi [tweedledee]("http://ubuntuforums.org/member.php?u=207037")

Why the package samsungmfp-configurator-qt4_3.00.65-3_amd64.deb is creating an empty directory in /opt.
Is there a reason or is just a little bug? In case this is a bug, could you correct it?

Cédric

The directory structure is inherited from the Samsung installer, so that's ultimately where it comes from.  However, I think you are referring to /opt/smpf-common/lib/ ?  If so, then I can modify the next build to remove it.  (Assuming Samsung doesn't start utilizing that directory - I keep things as close as possible to the official installer because I only learn of changes Samsung makes by trial and error, and errors are reduced if I avoid too many deviations from the installer.)

---

### Post by tweedledee on 2011-01-21
> **cedric_tux said:**
> QUESTION to [tweedledee]("http://ubuntuforums.org/member.php?u=207037"), could you include this workaround in you packages?

In principle, yes, although it's not trivial because the package would have to generate the new "netdiscovery" module specific for every user.  This leads to (at least) 3 complications:
1. Moving the libraries out of the way while the install occurs; although it would be only for a brief period, if any other program needed the libraries during that interval it would be unable to find them.  And should the install fail/be aborted, the user could be left with the libraries in an undesired state.  I might need to go with a user-run post-install process to handle this safely, which adds complexity.

2. The output is specific per printer and IP address.  If either changes, the netdiscovery file would have be updated.  Since the whole point of this substitution is to disable the ability to detect these changes, it's not obvious to me how I could handle this.  Users could re-install the package or re-run the post-install script (depending on the implementation for #1), but I can see this heading to lots of confusion for people with non-fixed IP addresses or other cases.

3. Multiple printers/scanners being found.  This may not actually be an issue, but I'm unable to test it since I don't have a mfp (or even a single, but the launchpad reports seem to validate that).  This could potentially lead to bugs difficult to solve.

Mostly just thinking in public here, but feedback on any of the above is welcome.  I intend to update driver versions and builds in the near future, and will try to incorporate what I can of this.  No promises on when that will be available.

---

### Post by tweedledee on 2011-01-23
I have (finally) updated the drivers available in the repository, to the (I think) latest 3.00.80 / 1.10.  These probably don't solve any ongoing scanner issues for anyone, however.

I also made numerous other small packaging changes to resolve minor issues, and did some housecleaning on the files/directories included.

The Configurator menu item should generally show up as a System Tool or similar now instead of a Graphics program, as few people seem to be using it for that purpose.  (Feel free to express a desire to revert back.)

There is now an empty source repository, which should solve some of the issues with people having the source repository automatically installed.

At this point I have not included any of the various solutions for the scanning problems.  This is due to four factors:
1. I can't test them.
2. I did test that moving around the libnss* libraries can lead to an inability to authenticate or even identify users in your system.  If you move these files around, be very careful to restore them, and DO NOT REBOOT while they are out of position unless you have a recovery disk handy.
3. No one solution seems to work for everyone, and I can't see a clear path to handling them all.
4. If I waited until I had time to address this, the update would have been delayed additional months.

---

### Post by n.masarone on 2011-01-24
Just to confirm that a problem may arise moving libs around; see  [https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/576531/comments/18](https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/576531/comments/18)

---

### Post by ArnoraCom on 2011-01-28
**Hi!**

I've been using [http://www.bchemnet.com/suldr/debian](http://www.bchemnet.com/suldr/debian) extra repository for Samsung Unified Driver installation for quite a long time now. Thanks for the great work!

But, this week my printers (2x network connected Samsung CLX-3175FW) stopped working. Only reason I could come up with was the new driver version (3.00.80-1). 

Here are the error messages, after printing had failed.

Error from dmesg:
=======================
[ 8383.000467] rastertosamsung[4992]: segfault at 0 ip 00007f99cf6e4beb sp 00007fff4571b408 error 4 in libc-2.12.1.so[7f99cf65e000+17a000]

Error from Ubuntu's Printer Properties window:
================================================
Idle - Filter "/usr/lib/cups/filter/rastertosamsungsplc" for printer "MY-PRINTERS-NAME" not available: No such file or directory

The problem got fixed when I:
i) completely removed samsungmfp-driver, samsungmfp-data, samsungmfp-configurator-qt4, samsungmfp-configurator-data and samsungmfp-scanner (version 3.00.80-1) thru Synaptic Package Manager
ii) and installed samsungmfp-legacy-driver, samsungmfp-legacy-data, samsungmfp-legacy-configurator-qt4, samsungmfp-legacy-configurator-data and samsungmfp-legacy-scanner (version 3.00.37-4) thru Synaptic Package Manager.

My system: Ubuntu 10.10 Maverick Meerkat with all updates (28.Jan.2011), 64bit Desktop.

Cheers!
Jukka

---

### Post by Kempe on 2011-01-28
Hi,

I am also all of a sudden having problems with my Samsung printer (CLP-315). I had it working flawlessly, thanks to the [http://www.bchemnet.com/suldr/debian](http://www.bchemnet.com/suldr/debian) extra repository, up until a couple of days ago (I noticed the problem yesterday, thursday). I have tried to use the legacy version as ArnoraCom suggested but it did not resolve my problem(s). The error message I recieve is '/usr/lib/cups/filter/rastertosamsungsplc failed'. I am using 32-bit 10.04 Desktop with all the latest updates. 

By the way, the printer also continuously (well, maybe a couple of times per hour anyway) print out an SPL-C time out error saying -

> SPL-C ERROR - Incomplete Session by time out

POSITION : 0x0 (0)

SYSTEM   : src/os_hook

LINE     : 1646

VERSION  : SPL-C 5.35 11-20-2007


Thanks

---

### Post by tweedledee on 2011-01-28
Here's what I've observed this evening:

1. PS printing works flawlessly (which is my default).

2. When I forced my printer to use SPL-C, which has worked in the past, I encountered errors identical to the last two posts, as well as a variety of others under assorted circumstances.

3. I've narrowed the error down to either the -data or -driver packages (i.e., either the files that are apparently generating the errors or the ppd files).

4. There's nothing wrong with the packages; I get the same errors installing with the Samsung installer.

5. I have suddenly stopped getting the errors.  I believe the key factor was to delete the printer and create a new (identical) one, still using the 3.00.80-1 packages.  However, it's difficult to test because I no longer have the errors.  I do have a second computer I could use to test this, but I left it at my office for the weekend and don't plan to make a special trip just to test this.

So for those of you seeing this problem, please try to delete the printer and then create a new printer, using the latest packages.  Restarting CUPS (/etc/init.d/cups restart or a reboot) may also help, I mixed that into my process at one point.

If the problem still persists despite a package reinstall and a printer delete/reinstall, I will have to return to the 3.00.65 driver packages in the repository, because I don't have time to track down whatever obscure problem is causing this.  I think it's as much CUPS as the driver itself, but that's mostly a guess at this point.

Please share any results.

---

### Post by Kempe on 2011-01-29
Hi,

I can now confirm that after deletion of the printer, complete removal of the driver and re-installation, the legacy driver works for my CLP-315 after restarting cups. However I still get the same error when I try the same with the 3.00.80-1 driver.

Big thanks for the tips about restarting cups!

/Kempe

---

### Post by Menion on 2011-01-30
Hi
I can confirm that the procedure of the temporarily disabling of libnss to get the scanner detected, works on my Ubuntu 10.10 32bit.
However, I've installed a fresh and updated 64bit version of Ubuntu 10.10 and the results with the Samsung unified drivers  are quite bad, the configurator doesn't work, I can detect the printer in the administration/print but I can't print, I can send a job to the printer but it instantaneously answer with an "error".
Is there anyone who succeed in having the printer working under 64bit enviroment?
Bye

---

### Post by cedric_tux on 2011-01-30
to get the configurator work do the following

sudo ln -s /lib/libpng12.so.0 /usr/lib/libpng.so.3


On a 64bit system the commands are the same as for the 32bit

---

### Post by tweedledee on 2011-01-30
> **Kempe said:**
> Hi,

I can now confirm that after deletion of the printer, complete removal of the driver and re-installation, the legacy driver works for my CLP-315 after restarting cups. However I still get the same error when I try the same with the 3.00.80-1 driver.

Big thanks for the tips about restarting cups!

/Kempe

I've updated the driver packages (but not the others).  The 3.00.80-2 package is actually the set of 3.00.65 driver files, which seems to resolve the SPLC problems permanently, while working fine with the other parts of the 3.00.80 system (ppd files, configurator).  Please let me know if errors continue.

Both the 3.00.80-2 and the legacy 3.00.37-5 driver packages now force a restart of CUPS, which suddenly seems necessary because of the way the driver files sometimes changes between updates.

I also added a note about the libtiff3 link issue in the original post.

---

### Post by cedric_tux on 2011-01-30
The problem with the libtiff also exists in ubuntu 10.04

---

### Post by Menion on 2011-01-30
> **cedric_tux said:**
> to get the configurator work do the following

sudo ln -s /lib/libpng12.so.0 /usr/lib/libpng.so.3


On a 64bit system the commands are the same as for the 32bit

Thank you. I've solved my problems, the scanner works with the netdiscovery "trick", while for the pronter I had to change the driver from CLX-3170 to CLX-3175 which is my printer.
The GUI configurator is working but for some reason it doesn't find any printer, I still had to detect it by the Print menu of Ubuntu

---

### Post by tweedledee on 2011-01-30
> **cedric_tux said:**
> The problem with the libtiff also exists in ubuntu 10.04

I must be tired.  It's libpng, not libtiff; it has existed for a while; and there was an update just released that supposedly fixes the problem.

Also, apparently the libpng12-dev package contains a working link, so that is another solution.

Main page updated (again).

---

### Post by hokiejp on 2011-01-30
I have Ubuntu 10.10 amd64 and a Samsung SCX-4826FN.  I've installed the packaged drivers from the repository, and got printing working with no problem, so thanks for that!

Scanning, of course, does not work.  I've tried both the current and legacy drivers, and both fail with (different) relocation errors.  Neither the original nor cho versions of the whosyerdaddy script work for me.  As to the question of what it's doing, I think I've found the answer [in this post.]("http://foldingforum.org/viewtopic.php?f=44&t=13064&start=15#p127786")  As I believe has already been explained here, if you statically link to glibc, [it still needs to resolve certain dependencies]("http://www.akkadia.org/drepper/no_static_linking.html") (e.g. libnss) at run-time.  Thus it seems that such a binary includes a dynamic linker as well.  The version of ld-linux they're including is, of course, quite old, and it can't understand the symbol tables in modern libraries ([IFUNC symbols]("https://groups.google.com/group/generic-abi/browse_thread/thread/d12dc9b64f22b75") in particular).  I don't fully understand all the implications of that, but the whosyerdaddy script seems basically to be finding the needed symbols in glibc and translating them somehow to something else (presumably FUNCs).  Regardless, when I run the script and then run netdiscovery the errors go away, but it also doesn't find any printers or scanners.  I think this is because the glibc shipped with ubuntu is missing the STRTAB section, so whosyerdaddy can't figure out exactly how to do the translation and makes some educated guesses (this is basically stated in the script).  Whatever assumptions it made for 10.04 don't seem to work for 10.10.

My brilliant idea was to try building the glibc from karmic (eglibc 2.10.1, last one known to work I think) and forcing that with LD_LIBRARY_PATH.  This fails with the following error:

> sh: /opt/Samsung/tools/lib/libc.so.6: version `GLIBC_2.11' not found (required by sh)
sh: /opt/Samsung/tools/lib/libc.so.6: version `GLIBC_2.11' not found (required by sh)
sh: /opt/Samsung/tools/lib/libc.so.6: version `GLIBC_2.11' not found (required by sh)
sh: /opt/Samsung/tools/lib/libc.so.6: version `GLIBC_2.11' not found (required by sh)
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
# Total 0 printers found, 0s elapsed


Which I think means netdiscovery is trying to call sh, and I need to build an sh (really a whole binutils) against my eglibc 2.10.1 and run netdiscovery from a chroot.  I may try that, but I suspect it may want to exec other binaries as well.  Is there a simple way to figure out all its dependencies, other than to run it and look for error messages (which may not be reliable)?  Another option I guess would be to build a glibc2.12 without IFUNCs, or unstripped so that whosyerdaddy could find the information it needs.  None of these are good solutions of course, but they seem better than waiting for the vendor to fix their closed source, incorrectly built, and poorly packaged drivers.  Thoughts are welcome.

---

### Post by tweedledee on 2011-01-30
> **hokiejp said:**
> Which I think means netdiscovery is trying to call sh, and I need to build an sh (really a whole binutils) against my eglibc 2.10.1 and run netdiscovery from a chroot.  I may try that, but I suspect it may want to exec other binaries as well.  Is there a simple way to figure out all its dependencies, other than to run it and look for error messages (which may not be reliable)?

Not with 100% reliability.  However, strace ./netdiscovery implies that it only looks for a few libs, not other executables.

While reading your post, my first thought was that if you got it working in a chroot, I could probably package that and ship it out as a brute-force, giant package.

And then my brain engaged, along with the fact that the 32-bit version doesn't seem to have this problem.  So just for kicks, I ran the 32-bit netdiscovery file in the 3.00.80 installer blob from Samsung.  And it appears to work just fine.  Of course, I have the ia32-libs package installed for a different application, but that means the 32-bit netdiscovery found the 32-bit libnss.

So perhaps a perfectly obvious solution, which should have occurred to me months ago, is to simply ship the 32-bit netdiscovery with a dependency on ia32-libs, instead of the 64-bit netdiscovery.  Of course, it's possible a future eglibc update would break something.  I'm currently running libc6 2.11, whereas 10.10 is using 2.12.  (Although that may not matter, as I think the ia32-libs are still built with 2.11.)

So let me make a call for assistance to brave souls with scanner difficulties.  Please download the Samsung blob (you can get it here: [http://www.bchemnet.com/suldr/UnifiedLinuxDriver-3.00.80.tar.gz](http://www.bchemnet.com/suldr/UnifiedLinuxDriver-3.00.80.tar.gz)), extract, open cdroot/Linux/i386/at_opt/bin in a terminal, and execute ./netdiscovery.  I'm interested in the following combinations of test cases (from people who actually have a scanner to detect):
1. libc6 2.12, no ia32-libs installed
2. libc6 2.11, no ia32-libs installed
3. libc6 2.12, ia32-libs installed
4. libc6 2.11, ia32-libs installed
5. libc6 2.10, with or without ia32-libs - I expect this to work fine, 32-bit or 64-bit

If you can test one or more of the above, please report back.  Don't attempt to change your libc6 version, but please check it/report it or your Ubuntu version (10.10 has 2.12, 10.04 has 2.11, and 9.10 has 2.10).  Let me know what worked and didn't work.  If you find something that seems to work, try replacing the /opt/Samsung/mfp/bin/netdiscovery with the 32-bit one and see if everything works properly.

Finally, if anyone using 32-bit can please confirm whether or not they've ever had libnss errors related to finding the scanner, please share.  I'm under the impression this is strictly a 64-bit problem, but if that's wrong than this is probably not going to work.

---

### Post by hokiejp on 2011-01-30
With glibc 2.12 and ia32-libs I get:

> netdiscovery: relocation error: /lib32/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
netdiscovery: relocation error: /lib32/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
ip: 192.168.2.108   slp: 0,0,0,0 snmp: 0,0,0 dsc: " [SEC001599784BF4]"
# Total 1 printers found, 5s elapsed


which is the same error I get with the legacy packages.  Based on the symbol tables in glibc 2.12, support for glibc 2.0 has been dropped completely.  The 64-bit binary seems to have been built against glibc 2.2.5, for which there is still support, albeit in the form of indirect functions which the old linker can't understand.

As an aside, you probably don't need ia32-libs, but just libc6-i386, although I suspect people won't have one without the other.  I may try to pull an old version of that package and see if I can run the 32 bit netdiscovery with it using LD_LIBRARY_PATH.  That seems way safer than mucking around with my real glibc.

---

### Post by Kempe on 2011-01-31
Printing with the non-legacy drivers now work for me. Thanks for a great job Tweedledee.

---

### Post by urusha on 2011-01-31
It' would be nice to add strings like theese in the head of "Release" file in the repo:
```
Origin: suldr
Codename: stable
```Or some another values. The idea is to make unattended-upgrades work by adding next line to Allowed-Origins in /etc/apt/apt.conf.d/50unattended-upgrades:
```
"suldr stable";
```Values should be without spaces (to properly use it for releases earlier  then 10.10 or debian 6). We use your repo on many machines and so, automatic updates should work, I think...
Thanks for attantion and for the great repo.

---

### Post by cyrillo on 2011-02-05
A few days I've bought a Samsung CLX-3185 printer. As it has been suggested here, I have installed the unified driver and had some problems. Because I have nowhere found anything about this problem, I'd like to share my experience.

When you get the following error message:
  Stopping job because the scheduler could not execute a filter.

Then have a look in the error-log and you will find something like this:
 >  [Job 80] Started filter /usr/lib/cups/filter/pstops (PID 20165)
  Unable to execute /usr/lib/cups/filter/pstosecps: no execute    permissions (0100644)
  Unable to start filter "pstosecps" - Operation not permitted.
  Discarding unused job-state-changed event...
  [Job 80] Stopping job because the scheduler could not execute a filter.

It looks like that you just have to change the permission of /usr/lib/cups/filter/pstosecps but this filter-file is not there.

Copy the filter-file from the directory where you have unpacked the Unified-Printer-Driver to the cups filters.

 ```
 sudo cp ./cdroot/Linux/i386/at_root/usr/lib/cups/filter/pstosecps /usr/lib/cups/filter/
```

Then change the permission:
 ```
 sudo chmod 755 /usr/lib/cups/filter/pstosecps 
```

With this I brought the printer to work and I'm very happy with my CLX-3185.

I hope my contribution can help someone with the same problem.

---

### Post by tweedledee on 2011-02-05
> **cyrillo said:**
> A few days I've bought a Samsung CLX-3185 printer. As it has been suggested here, I have installed the unified driver and had some problems. Because I have nowhere found anything about this problem, I'd like to share my experience.

Just so I'm clear - how did you install the driver and which version?  I believe that file is only associated with the newest drivers, which suggests you installed the package directly from Samsung - and if so, the latest drivers from them appear to be very buggy.  (The file you mention is one I had to "fix" during the brief period I tried to package and distribute the latest drivers, for the reason you describe.)

---

### Post by tweedledee on 2011-02-05
> **urusha said:**
> It' would be nice to add strings like theese in the head of "Release" file in the repo:

Done.  Origin is "suldr" and codename remains "debian" as it has been.

---

### Post by miltondp on 2011-02-10
Hi guys. First of all, thank you very much for your work. It really was very useful for me. Now, I am facing with a problem I would like to share with you, maybe you can help me. 

I have two Samsung ML-1665 printers working, connected to the same PC. First, my problem was that Ubuntu couldn't distinguish them. So if I added one printer it works. Although the second was detected too, it had the same device URI, so all printing were send to the first one only. This are some post of people with the same problem:

[http://ubuntuforums.org/showthread.php?t=1232097](http://ubuntuforums.org/showthread.php?t=1232097)
[http://wwww.ubuntuforums.org/showthread.php?p=6715273](http://wwww.ubuntuforums.org/showthread.php?p=6715273)
[http://ubuntuforums.org/showthread.php?t=1390046](http://ubuntuforums.org/showthread.php?t=1390046)

Then I could fix it, changing the device URI in /etc/cups/printers.conf. Here there is a post explaining the fix:

[http://www.henningweiler.de/2009/01/20/cups-and-multiple-identical-printers/](http://www.henningweiler.de/2009/01/20/cups-and-multiple-identical-printers/)

The device URIs look like this: file:/dev/usblp0, etc.

Now, my problem is the following: although both printers are working, sometimes the system change the usb ports, and the usblp0 device points to the printer B, and the usblp1 one to the printer A. This happens randomly. It may be working two months without problems, and then it gets crazy again for a few days.

I saw that Ubuntu puts a "serial" parameter in the device URI for some EPSON and HP printers. Running lpusb -v, I see that my printers have a serial number, but it's not used by CUPS when they are installed. I will try to put it manually, and see what happens, but it does not seems to work, as someone said in some post.

So, any help? Did one of you guys have the same problem?

As I don't have direct access to the machine with these printers installed, what I will be trying as soon as I have the possibility is:

[LIST]
[*]Try to unload the usblp module, and installing the printers again.
[*]Update to the latest driver you have posted in the repositories.
[*]Try to use a different usb port for one of the printers. Right now, both are connected in the front of the PC.
[*]Try with serial parameter in the device URI.
[/LIST]
Thank you.

---

### Post by tweedledee on 2011-02-10
> **miltondp said:**
> [LIST]
[*]Try to unload the usblp module, and installing the printers again.
[*]Update to the latest driver you have posted in the repositories.
[*]Try to use a different usb port for one of the printers. Right now, both are connected in the front of the PC.
[*]Try with serial parameter in the device URI.
[/LIST]
Thank you.

The first won't be a permanent fix, the second won't help, the third might help depending on how the USB hubs are recognized internally, and the fourth I have no idea.

It sounds to me like what you are really looking for is a set of rules to add to udev so that the USB ports are always numbered exactly the same way, which isn't really something that has to do with printing or CUPS.  At one point in time I had to do some of that for a different problem (occasional random renaming of the wireless device upon boot), but the computer that required those modifications died a while back and I no longer seem to have the notes.  I would suggest looking for solutions along those lines rather than something specific to CUPS or printing.

---

### Post by hokiejp on 2011-02-12
Ok, I now have scanning working in 10.10 amd64.  Here's what I did:

[LIST=1]
[*] Download the source for eglibc 2.10.1 from packages.ubuntu.com
[*] Build a 32bit version of eglibc (roughly following the package rules for libc6-i386).  This is the hardest part, see my next post for detailed instructions.
[*] Installed the new libc in a folder I made called /opt/Samsung/tools/
[*] copied the 32 bit version of netdiscovery from the Samsung drivers package to /opt/Samsung/mfp/bin/netdiscovery32
[*] Backed up my old netdiscovery to netdiscovery64
[*] Wrote a script called /opt/Samsung/mfp/bin/netdiscovery, contents are:
```
LD_LIBRARY_PATH=/opt/Samsung/tools/lib /opt/Samsung/mfp/bin/netdiscovery32 $*
```
[/LIST]

Then I ran xsane and started scanning random things around my house, just because I finally could.  This solution will work as long as one can still build eglibc 2.10.1, has no implications for system stability, and merely wastes about 100MB of disk space.  That could probably be reduced by keeping only the files that were strictly required.

---

### Post by hokiejp on 2011-02-12
Build steps for eglibc 2.10.1 (from previous post)

[EDIT:  I have not done a careful careful check of the packages required to do this build, but tweedledee reports that build-essential, gcc-multilib, and gawk should be all that are required.  If you discover any other dependencies or if the build fails for you for any reason, please contact me and I will update these instructions.]

[LIST=1]
[*]Make a working folder and cd into it
[*]Download the sources: ```
wget http://archive.ubuntu.com/ubuntu/pool/main/e/eglibc/eglibc_2.10.1.orig.tar.gz
```
[*]Build a 32bit libc with the following steps.  This takes a fairly long time to compile.
```
tar -zxvf eglibc_2.10.1.orig.tar.gz
mkdir build
cd build
CC="gcc-4.4 -fno-stack-protector -U_FORTIFY_SOURCE -m32";export CC
CFLAGS="-O2 -pipe -fstrict-aliasing -march=i686 -mtune=generic"; export CFLAGS
../eglibc-2.10.1/configure --prefix=/opt/Samsung/tools/ --disable-profile --enable-multiarch --host=i686-linux-gnu
make

```
[*] Make the install folder and install with the following commands.  It's probably fine to `make install` as root since the prefix was set in the configure step, but it's definitely safer not to.
```
sudo mkdir /opt/Samsung/tools
sudo chown $USERNAME:$USERNAME /opt/Samsung/tools
make install

```
[/LIST]

---

### Post by tweedledee on 2011-02-13
> **hokiejp said:**
> Ok, I now have scanning working in 10.10 amd64.

This seems to be a solution I can safely package and distribute.  Over the next week or so I will look into doing so.

---

### Post by tweedledee on 2011-02-13
> **hokiejp said:**
> This solution will work as long as one can still build eglibc 2.10.1, has no implications for system stability, and merely wastes about 100MB of disk space.  That could probably be reduced by keeping only the files that were strictly required.

Would you be willing to test what is required?  Specifically by moving everything except lib/ out of the way, and also moving the .a files from lib/?  I believe both should be safe for this application, and that would reduce the install size to ~20 MB instead of ~90 MB.  Probably still twice what is necessary, but a significant improvement.

---

### Post by hokiejp on 2011-02-14
> **tweedledee said:**
> Would you be willing to test what is required?  Specifically by moving everything except lib/ out of the way, and also moving the .a files from lib/?  I believe both should be safe for this application, and that would reduce the install size to ~20 MB instead of ~90 MB.  Probably still twice what is necessary, but a significant improvement.

No problem.  I think you're right, and I should be able to confirm it later in the week.

---

### Post by a__l__a__n on 2011-02-15
I have a new SCX-4623FW set up as a wired network printer.  I installed the Samsung Unified Driver Configurator in my Ubuntu 10.04 (32 bit) and attempted to configure the printer by hand to point to my printer on the network.  I was getting the following error message on the print jobs:

     stopping job because the scheduler could not execute a filter

The troubleshooter tool led me to a filter with unsafe permissions:

   /usr/lib/cups/filter/pstosecps

-rwxrwxrwx 1 root root   70348 2010-01-18 08:58 pstosecps

I removed write permission for group and other:  

   chmod go-w /usr/lib/cups/filter/pstosecps

So the permissions are now

-rwxr-xr-x 1 root root   70348 2010-01-18 08:58 pstosecps

I then deleted the manually created printer in the Samsung Unified Driver Configurator, and found the printer on the network by searching.  And now printing works!

Hope that helps someone.

---

### Post by hokiejp on 2011-02-15
> **tweedledee said:**
> Would you be willing to test what is required?  Specifically by moving everything except lib/ out of the way, and also moving the .a files from lib/?  I believe both should be safe for this application, and that would reduce the install size to ~20 MB instead of ~90 MB.  Probably still twice what is necessary, but a significant improvement.

In looking at this again I noticed that I was building everything with -g, so all the libs were way bigger than they had to be.  Fixing that (previous post with build instructions updated), cut the size in half.

I then removed all non-lib directories, and all .a, .o, and .map files and found no effect on netdiscovery (remaining size was 9.1MB).  I got ambitious and removed the lib/gconv folder  and it still works fine for me (although maybe won't be portable to other locales?).  Total size is now 2.9MB, with 1.5MB of that just for libc itself.

---

### Post by tweedledee on 2011-02-16
> **hokiejp said:**
> In looking at this again I noticed that I was building everything with -g, so all the libs were way bigger than they had to be.  Fixing that (previous post with build instructions updated), cut the size in half.

I then removed all non-lib directories, and all .a, .o, and .map files and found no effect on netdiscovery (remaining size was 9.1MB).  I got ambitious and removed the lib/gconv folder  and it still works fine for me (although maybe won't be portable to other locales?).  Total size is now 2.9MB, with 1.5MB of that just for libc itself.

I have packaged this solution.  Everyone who has been having scanner issues with 64-bit installations should now have a working system if you update to the latest repository files.  Please let me know how it goes.

(I did change the "tools" directory to "eglibc32" and pruned the libc_pic directory as well, but otherwise this is identical to your solution and comes in under 2.8 MB.)

---

### Post by tweedledee on 2011-02-16
> **hokiejp said:**
> In looking at this again I noticed that I was building everything with -g, so all the libs were way bigger than they had to be.  Fixing that (previous post with build instructions updated), cut the size in half.

Oh, and you may want to mention in your build post that gcc-multilib is required for the build (at least on my system).  I'm pointing people who want to install/build manually to your posts, and that may eliminate some questions.

---

### Post by Azdour on 2011-02-17
Hi,

Just wanted to say thanks for the work in putting together this guide to getting Samsung printers to work and to also give some feedback.

I actually found your website ([http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/)) before discovering this thread. I have been using the guide to install samsungmfp-data, samsungmfp-driver and samsungmfp-lpr for about a year now.

We hit an issue with printing from Adobe Reader. It would show the usual print dialog and then the lpr print dialog. After the lpr print dialog we would get an error dialog with a large error and it would not print.

We found that to fix it, I just needed to go into the Synaptic Package Manager and remove samsungmfp-lpr. After that we could print.

---

### Post by tweedledee on 2011-02-17
> **Azdour said:**
> We hit an issue with printing from Adobe Reader. It would show the usual print dialog and then the lpr print dialog. After the lpr print dialog we would get an error dialog with a large error and it would not print.

We found that to fix it, I just needed to go into the Synaptic Package Manager and remove samsungmfp-lpr. After that we could print.

In the event you are interested in a somewhat cumbersome work-around, you can configure your printer using the dialogs, and then copy the command line that is generated (when you are viewing printer "properties").  Then select "custom" printer and paste the command, changing the "lpr" the beginning to "/usr/bin/lpr" to force Reader to use the CUPS lpr instead of the Samsung one (which I put in /usr/local/bin to allow this kind of work-around).

There used to be a way to change the default "lpr" used by Reader, but it appears that option has been removed.  The current work-around works fine if you rarely change printers or printer settings, or are willing to configure several custom printers containing your common settings.

---

### Post by hokiejp on 2011-02-17
> **tweedledee said:**
> Oh, and you may want to mention in your build post that gcc-multilib is required for the build (at least on my system).  I'm pointing people who want to install/build manually to your posts, and that may eliminate some questions.

Done.  Also, I got the new drivers from the repository today (including samsungmfp-eglibc32) and can confirm that scanning works for me.  Thanks again for all your hard working in making these available!

---

### Post by tweedledee on 2011-02-18
> **hokiejp said:**
> Thanks again for all your hard working in making these available!

Thank you for spending the time to find a viable solution to the scanning problems - there are at least several dozen people, and possibly a couple of hundred, who should now have fully functional scanners again.

---

### Post by gaboro on 2011-02-18
Hi,

Would this workaround work for a 32-bit system, too?  Under Ubuntu 10.10 I receive the same error message as you had on 64-bit systems:
 
```

netdiscovery: relocation error: /lib/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
netdiscovery: relocation error: /lib/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference

```

If I temporary rename the libnss_file.so.2 file, netdiscovery finds the scanner fine. So I guess it is a similar problem as you did have. 

Does it make sense to build a 32-package from eglibc?

cheers
gaboro

---

### Post by tweedledee on 2011-02-18
> **gaboro said:**
> Would this workaround work for a 32-bit system, too?

It should.  You can test by downloading the samsungmfp-eglibc32 package and installing using dpkg --force-architecure -i <package>, then invoking netdiscovery as: ```
LD_LIBRARY_PATH=/opt/Samsung/eglibc32/lib /opt/Samsung/mfp/bin/netdiscovery
```

If it works, I can implement the same solution for the 32-bit packages.  (I don't have a 32-bit installation handy at the moment to try this myself.)

---

### Post by gaboro on 2011-02-19
> **tweedledee said:**
> 
If it works, I can implement the same solution for the 32-bit packages.  (I don't have a 32-bit installation handy at the moment to try this myself.)
It did not work unfortunately...
```

LD_LIBRARY_PATH=/opt/Samsung/eglibc32/lib/ /opt/Samsung/mfp/bin/netdiscovery 
sh: /opt/Samsung/eglibc32/lib/libc.so.6: version `GLIBC_2.11' not found (required by sh)
sh: /opt/Samsung/eglibc32/lib/libc.so.6: version `GLIBC_2.11' not found (required by sh)
sh: /opt/Samsung/eglibc32/lib/libc.so.6: version `GLIBC_2.11' not found (required by sh)
sh: /opt/Samsung/eglibc32/lib/libc.so.6: version `GLIBC_2.11' not found (required by sh)
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
# Total 0 printers found, 0s elapsed

```
Do you have any clue how to solve this?
Thanks in advance

---

### Post by tweedledee on 2011-02-19
> **hokiejp said:**
> Done.  Also, I got the new drivers from the repository today (including samsungmfp-eglibc32) and can confirm that scanning works for me.  Thanks again for all your hard working in making these available!

FYI, gawk appears to be the only other requirement for building aside from build-essential and gcc-multilib.

---

### Post by tweedledee on 2011-02-19
> **gaboro said:**
> Do you have any clue how to solve this?
Thanks in advance

Yes - stop the Ubuntu developers from forcing the 32-bit sh (bash/dash) to depend on a particular version of libc.  I have no idea what the person who compiled that version was thinking, and it should probably be reported as a bug, because neither 64-bit nor 32-bit Debian has the same requirement.  And obviously 64-bit Ubuntu does not or the fix wouldn't work there, either, although I am going to do a test to confirm that as well.

I am also looking into other workarounds, since my virtual machine tests with a 32-bit 10.10 Ubuntu install today seem to indicate that only the latest update of eglibc causes the problem on 32-bit systems, so I may be able to get this to work with a 2.11 version.

More updates later, hopefully soon.

---

### Post by tweedledee on 2011-02-19
> **gaboro said:**
> Do you have any clue how to solve this?
Thanks in advance

Okay, try this: remove the current samsungmfp-eglibc32 package you have installed.  Download [http://www.bchemnet.com/suldr/eglibc32.tar.gz](http://www.bchemnet.com/suldr/eglibc32.tar.gz).  Unpack the file and move the folder to /opt/Samsung.  Then try again with the same command from above.

My preliminary tests suggest that this fixes the error you saw, but I'm not sure it will actually detect the scanner, which is why I'm not moving directly into a packaged solution.

---

### Post by gaboro on 2011-02-19
> **tweedledee said:**
> Okay, try this: remove the current samsungmfp-eglibc32 package you have installed.  Download [http://www.bchemnet.com/suldr/eglibc32.tar.gz](http://www.bchemnet.com/suldr/eglibc32.tar.gz).  Unpack the file and move the folder to /opt/Samsung.  Then try again with the same command from above.

My preliminary tests suggest that this fixes the error you saw, but I'm not sure it will actually detect the scanner, which is why I'm not moving directly into a packaged solution.
Like you though, errors are gone now but neither the scanner is not found nor the printer itself.
w/o LD_LIBRARY_PATH: 
```

/opt/Samsung/mfp/bin/netdiscovery.orig
netdiscovery.orignetdiscovery.orig: : relocation errorrelocation error: : /lib/libnss_files.so.2/lib/libnss_files.so.2: : symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time referencesymbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference

# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
ip: 192.168.0.50    slp: 0,0,0,0 snmp: 0,0,0 dsc: " [SEC0015997701B7] Apa HomeOffice"
# Total 1 printers found, 5s elapsed

```
w/ LD_LIBRARY_PATH:
```

 LD_LIBRARY_PATH=/opt/Samsung/eglibc32/lib/ /opt/Samsung/mfp/bin/netdiscovery.orig
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
# Total 0 printers found, 0s elapsed

```
I have tried to create a netdiscovery script to test scanimage -L but it also fails to find the scanner...

---

### Post by tweedledee on 2011-02-19
> **gaboro said:**
> Like you though, errors are gone now but neither the scanner is not found nor the printer itself.

Just for completeness, try running w/ and w/o the library path as ```
netdiscovery --all --scanner
```

If that doesn't work, I think the problem is the way the current 32-bit sh is linked during compilation in Ubuntu.  The 2.10.1 library files work fine with 64-bit Ubuntu, 32-bit Debian, and 64-bit Debian (Squeeze).  This would be something to report on launchpad.  However, whether the error is in bash/dash, libc6, or somewhere else, I'm not sure.  I'd guess libc6 based on my limited package updating done today.

You can try reverting to the original package version of libc6* that shipped with 10.10 to see if that helps (original versions 2.12.1-0ubuntu6, current 2.12.1-0ubuntu10.2), which would also strongly suggest an issue with the way some package is built for 32-bit systems.  Such a reversion might solve the problem even without the use of my eglibc build.

In the meantime, and on the small chance that it might work, I'm going to try to compile a version of the original 2.12.1 libraries to test.  If not, and if reverting the package doesn't help, then I think this has to be fixed through the Ubuntu packages.

---

### Post by tweedledee on 2011-02-19
> **gaboro said:**
> Like you though, errors are gone now but neither the scanner is not found nor the printer itself.

I've updated the eglibc32.targ.gz file - please download and test the same process.

If it works, I should be able to implement a solution, but it will take some thought on how best to reconstruct packages.  The 2.12.1 I compiled appears (with my limited testing ability) to work fine in Ubuntu 10.10, but fails completely with Debian Squeeze, I assume because the 2.12 is newer than the 2.11.  Which means I have to work out a series of dependencies for when someone actually needs the libraries I'm compiling and when those libraries would actually break a working installation....

---

### Post by gaboro on 2011-02-19
> **tweedledee said:**
> Just for completeness, try running w/ and w/o the library path as ```
netdiscovery --all --scanner
```

Same result, I'm afraid, no scanner found regardless of the library usage.

> **tweedledee said:**
> 
You can try reverting to the original package version of libc6* that shipped with 10.10 to see if that helps (original versions 2.12.1-0ubuntu6, current 2.12.1-0ubuntu10.2), which would also strongly suggest an issue with the way some package is built for 32-bit systems.  Such a reversion might solve the problem even without the use of my eglibc build.

Instead of forcing the old version of the libc6 to my "live" system I booted up a live cd Ubuntu 10.10 32-bit in a virtualbox session. Having installed the drivers I experienced negative results again.
[LIST]Using the default libc6 2.12.1-0ubuntu6 I received errors and dumps, printer found, scanner not (same result w/ --all --scanner).[/LIST]
```
./netdiscovery 
netdiscovery: ../sysdeps/unix/sysv/linux/getpagesize.c:32: __getpagesize: Assertion `_rtld_global_ro._dl_pagesize != 0' failed.
netdiscovery: ../sysdeps/unix/sysv/linux/getpagesize.c:32: __getpagesize: Assertion `_rtld_global_ro._dl_pagesize != 0' failed.
netdiscovery: ../sysdeps/unix/sysv/linux/getpagesize.c:32: __getpagesize: Assertion `_rtld_global_ro._dl_pagesize != 0' failed.
Aborted (core dumped)
Aborted (core dumped)
Aborted (core dumped)
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
ip: 10.0.2.2        slp: 0,0,0,0 snmp: 0,0,0 dsc: " [SEC0015997701B7] Apa HomeOffice"
# Total 1 printers found, 9s elapsed
```
[LIST]Using your eglibc package the result war the same as w/ the newer libc on my live system: lots of compains from sh not having the proper version of libc.
[/LIST]
```
LD_LIBRARY_PATH=/opt/Samsung/eglibc32/lib /opt/Samsung/mfp/bin/netdiscovery --all --scanner
sh: /opt/Samsung/eglibc32/lib/libc.so.6: version `GLIBC_2.11' not found (required by sh)
sh: /opt/Samsung/eglibc32/lib/libc.so.6: version `GLIBC_2.11' not found (required by sh)
sh: /opt/Samsung/eglibc32/lib/libc.so.6: version `GLIBC_2.11' not found (required by sh)
sh: /opt/Samsung/eglibc32/lib/libc.so.6: version `GLIBC_2.11' not found (required by sh)
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
# Total 0 scanners found, 0s elapsed

```
[LIST]Using your eglibc tar.gz file, printer will be found but no scanner.[/LIST]
```
LD_LIBRARY_PATH=/opt/Samsung/eglibc32_targz/lib /opt/Samsung/mfp/bin/netdiscovery --all --scanner
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
# Total 0 scanners found, 5s elapsed

```
Do you think it worth to try the old libc6 package on an installed system?

---

### Post by gaboro on 2011-02-19
> **tweedledee said:**
> I've updated the eglibc32.targ.gz file - please download and test the same process.
sorry, overseen this post, I test it right now

---

### Post by gaboro on 2011-02-19
> **tweedledee said:**
> I've updated the eglibc32.targ.gz file - please download and test the same process.

If it works, 

IT DOES WORK!!! I still cannot belive my eyes :-D
Thank you for your effort to solve this!

---

### Post by Peter Bell on 2011-02-19
> **mozkill said:**
> So glad I bought a Samsung CLP-315 and use the IPP protocol to connect to it.   Its easy and I can ignore this post.

Hmmm ... can you tell me how to do that?

I thought that IPP only worked over a network and the CLP-315 has no network interface.

I have not yet managed to get my CLP-315 working with Ubuntu 10.10.

Sometimes I can get the Ubuntu test page to print, but more often I get SPL-C ERROR - incomplete Session by time out.

I have tried the unified drivers package, both 3.00.80-2 and 3.00.37-5, both with foomatic and SPL-C (CLP-310 - I don't see a CLP-315 SPL-C choice) drivers.

I have never managed to print anything other than occasional test pages and much more frequent time out errors.

---

### Post by tweedledee on 2011-02-20
> **gaboro said:**
> IT DOES WORK!!! I still cannot belive my eyes :-D
Thank you for your effort to solve this!

All packages are updated to hopefully handle all of the various conflicts, etc.  gaboro, you should remove the /opt/Samsung/eglibc32 directory prior to updating, but after updating everything should still work.

Everyone else, please let me know if something breaks.  I believe that everyone who can print should also now have full scanning, regardless of installed libraries and distro version.

---

### Post by tweedledee on 2011-02-20
> **Peter Bell said:**
> Sometimes I can get the Ubuntu test page to print, but more often I get SPL-C ERROR - incomplete Session by time out.

I have tried the unified drivers package, both 3.00.80-2 and 3.00.37-5, both with foomatic and SPL-C (CLP-310 - I don't see a CLP-315 SPL-C choice) drivers.

The CLP-315 should use the -310 drivers, they are more or less the same printer.  If you have any errors in the log files, I might be able to help figure out what's going on.  You can also try the splix drivers, which supposedly work for this printer and have their own repository, see [http://www.linuxfoundation.org/collaborate/workgroups/openprinting/database/driverpackages](http://www.linuxfoundation.org/collaborate/workgroups/openprinting/database/driverpackages)

---

### Post by gaboro on 2011-02-20
> **tweedledee said:**
>  after updating everything should still work.

Having installed samsungmfp-netdiscovery-oldlibc works everything fine. The package 
samsungmfp-eglibc has been installed automatically.
I will try to test it on lucid as well.
Thanks indeed

---

### Post by gaboro on 2011-02-20
> **tweedledee said:**
>  I believe that everyone who can print should also now have full scanning, regardless of installed libraries and distro version.
I'm afraid, it does not work on lucid. 
The netdiscovery-oldlibc packages cannot be installed because of unresolved dependency from libc6 2.12. So the standard netdiscovery will be installed and it brings the well-known problems with the libnss_files.so.2. Having installed the eglibc package and applied the library path trick no errors are produced anymore but the scanner is not found.

---

### Post by tweedledee on 2011-02-20
> **gaboro said:**
> I'm afraid, it does not work on lucid. 
The netdiscovery-oldlibc packages cannot be installed because of unresolved dependency from libc6 2.12. So the standard netdiscovery will be installed and it brings the well-known problems with the libnss_files.so.2. Having installed the eglibc package and applied the library path trick no errors are produced anymore but the scanner is not found.

I somehow overlooked that Lucid 32-bit was also now acting up.  Does it work on lucid if you force-install the eglibc32-amd64 package?

This would be much simpler if there wasn't the stupid error with sh requiring particular versions of eglibc as well.  Please open a bug on launchpad about the sh errors you saw, as I am not looking forward to creating dozens of version of libraries to match every Ubuntu update because something is compiling wrong, when it all works fine on Debian.  (Well, actually, it'd all be much simpler if Samsung produced decent drivers, but I'm less optimistic about resolving that problem.)

---

### Post by tweedledee on 2011-02-20
> **gaboro said:**
> I'm afraid, it does not work on lucid.

I tried some additional tricks to get something working in 32-bit Lucid.  However, it appears that the 32-bit eglibc 2.11 does not work at all, even with a custom build.  The 2.12 libraries don't work on systems with the main 2.11 library files (not surprising).  And the 2.10 custom build doesn't work with 32-bit Lucid because of the sh dependency problem, which is Ubuntu-specific (or at least not present in Debian).

Therefore, I can't see any way to get 32-bit Ubuntu 10.04 to work with network scanning, at least with this approach.  And I've yet to see another that is viable for my repository.

---

### Post by Peter Bell on 2011-02-21
> **tweedledee said:**
> The CLP-315 should use the -310 drivers, they are more or less the same printer.  If you have any errors in the log files, I might be able to help figure out what's going on.  You can also try the splix drivers, which supposedly work for this printer and have their own repository, see [http://www.linuxfoundation.org/collaborate/workgroups/openprinting/database/driverpackages](http://www.linuxfoundation.org/collaborate/workgroups/openprinting/database/driverpackages)

Thank you for your interest in helping me (and everyone else!).  I only purchased this CLP-315 as an inexpensive, short-term, fix while I attempt to obtain toner cartridges for my LJ3800dtn (which was never sold here in Philippines).

I have followed your instructions for removal of the Unified driver, and then re-installed the 'current' driver from your repository.  I unplugged the usb connection to the printer, then reconnected it.  Within a few seconds I was told that the printer was installed and ready for use.  I went to printer properties and changed the driver to the Samsung CLP-310 Series (SPL-C) driver.  I then attempted a standard test page print.  Some minutes later, the printer is still blinking the green light and I know that it will end in a page being produced with th "SPL-C ERROR - Incomplete Session by time out" error report after a 15 minute time out.

The complete syslog entries for the duration of this process are:
```
Feb 21 14:38:31 Desktop udevd[443]: can not read '/etc/udev/rules.d/z80_user.rules'
Feb 21 14:38:32 Desktop udevd[14997]: can not read '/etc/udev/rules.d/z80_user.rules'
Feb 21 14:38:32 Desktop kernel: [ 6060.290448] udev[14998]: starting version 163
Feb 21 14:38:32 Desktop kernel: [ 6060.309453] type=1400 audit(1298270312.723:24): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=15006 comm="apparmor_parser"
Feb 21 14:38:32 Desktop kernel: [ 6060.310590] type=1400 audit(1298270312.723:25): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=15006 comm="apparmor_parser"
Feb 21 14:38:33 Desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0
Feb 21 14:38:33 Desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6
Feb 21 14:38:33 Desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/usb/lp0
Feb 21 14:38:33 Desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6
Feb 21 14:38:47 Desktop kernel: [ 6075.532809] usb 2-1.6: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
Feb 21 14:38:48 Desktop kernel: [ 6075.536784] usblp0: nonzero read bulk status received: -71
Feb 21 14:38:48 Desktop hp[15085]: io/hpmud/pp.c 627: unable to read device-id ret=-1
Feb 21 14:38:48 Desktop python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Feb 21 14:38:48 Desktop bluetoothd[1306]: Discovery session 0x7ffa15d678d0 with :1.53 activated
Feb 21 14:39:36 Desktop kernel: [ 6124.209733] usb 2-1.6: USB disconnect, address 12
Feb 21 14:39:36 Desktop kernel: [ 6124.209875] usblp0: removed
Feb 21 14:39:36 Desktop udev-configure-printer: remove /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6
Feb 21 14:39:36 Desktop udev-configure-printer: URI of print queue: dnssd://Brother%20MFC-7820N._printer._tcp.local/, normalized: dnssd brother mfc 7820n printer tcp local
Feb 21 14:39:36 Desktop udev-configure-printer: URI of detected printer: usb://Samsung/CLP-310%20Series, normalized: samsung clp 310 series
Feb 21 14:39:58 Desktop kernel: [ 6145.459743] usb 2-1.6: new high speed USB device using ehci_hcd and address 13
Feb 21 14:40:01 Desktop kernel: [ 6148.911208] hub 2-1:1.0: unable to enumerate USB device on port 6
Feb 21 14:40:01 Desktop kernel: [ 6149.150338] usb 2-1.6: new high speed USB device using ehci_hcd and address 14
Feb 21 14:40:01 Desktop kernel: [ 6149.262345] usblp0: USB Bidirectional printer dev 14 if 0 alt 0 proto 2 vid 0x04E8 pid 0x328E
Feb 21 14:40:01 Desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0
Feb 21 14:40:01 Desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6
Feb 21 14:40:01 Desktop udev-configure-printer: Device vendor/product is 04E8:328E
Feb 21 14:40:01 Desktop udev-configure-printer: failed to claim interface
Feb 21 14:40:01 Desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Feb 21 14:40:01 Desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/usb/lp0
Feb 21 14:40:01 Desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6
Feb 21 14:40:01 Desktop udev-configure-printer: MFG:Samsung MDL:CLP-310 Series SERN:- serial:147VBAZQ700113A
Feb 21 14:40:02 Desktop kernel: [ 6150.294913] usb 2-1.6: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
Feb 21 14:40:02 Desktop hp[15194]: io/hpmud/pp.c 627: unable to read device-id ret=-1
Feb 21 14:40:03 Desktop python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Feb 21 14:40:03 Desktop udev-configure-printer: URI matches without serial number: usb://Samsung/CLP-310%20Series
Feb 21 14:40:03 Desktop udev-configure-printer: No serial number URI matches so using those without
Feb 21 14:40:03 Desktop udev-configure-printer: Consider also queues with "/usb/lp0" or "/usblp0" in their URIs as matching
Feb 21 14:40:03 Desktop udev-configure-printer: URI of print queue: dnssd://Brother%20MFC-7820N._printer._tcp.local/, normalized: dnssd brother mfc 7820n printer tcp local
Feb 21 14:40:03 Desktop udev-configure-printer: URI of detected printer: usb://Samsung/CLP-310%20Series, normalized: samsung clp 310 series
Feb 21 14:40:03 Desktop udev-configure-printer: About to add queue for usb://Samsung/CLP-310%20Series
Feb 21 14:40:03 Desktop udev-add-printer: add_queue: URIs=['usb://Samsung/CLP-310%20Series']
Feb 21 14:40:05 Desktop udev-add-printer: PPD: lsb/usr/foo2zjs/Samsung-CLP-310.ppd.gz; Status: 0
Feb 21 14:40:26 Desktop dhclient: DHCPREQUEST of 10.2.1.15 on eth0 to 10.2.0.2 port 67
Feb 21 14:40:26 Desktop dhclient: DHCPACK of 10.2.1.15 from 10.2.0.2
Feb 21 14:40:26 Desktop dhclient: bound to 10.2.1.15 -- renewal in 1623 seconds.
Feb 21 14:41:19 Desktop kernel: [ 6226.698172] usblp0: nonzero write bulk status received: -71
Feb 21 14:41:19 Desktop kernel: [ 6226.698184] usblp0: nonzero read bulk status received: -71
```

I guess that the problem is those two last lines, but I have absolutely no idea how to interpret them, or what to do about them.

---

### Post by tweedledee on 2011-02-21
> **Peter Bell said:**
> I have followed your instructions for removal of the Unified driver, and then re-installed the 'current' driver from your repository.  I unplugged the usb connection to the printer, then reconnected it.  Within a few seconds I was told that the printer was installed and ready for use.

What you describe is foomatic-autoconfiguration, as also indicated in your log (if you search for "ppd" you will find that the selected driver is a foomatic ppd, not the samsung ppd).  Foomatic won't ever use the Samsung driver by default, because it provides its own (evidently buggy) driver.

You will need to uninstall the printer that was automatically configured and install a new one manually, making sure to select the Samsung ppd option instead of the foomatic one (usually in the printer list, the one that just says "CLP-310 Series" without any reference to foomatic).

If you are still having problems after setting up that driver, post a new log and I'll take a look.  Problems with foomatic drivers are beyond my experience - although you should open a foomatic bug report about the CLP-310/315 driver if you have the time/interest.

---

### Post by Peter Bell on 2011-02-21
I presume that you are identifying it as a foomatic driver because it has foo2zjs in the path.

> **tweedledee said:**
> You will need to uninstall the printer that was automatically configured and install a new one manually

Even though I do this, when I add the printer (selecting 'Samsung CLP-310' in the New Printer -> Select Device box), as soon as I click the forward button it automatically searches for a driver without even telling me which one it has chosen.  When I 'Apply' and then look at the printer properties, I see that it shows the 'Make and Model' as 'Samsung CLP-310 Foomatic/foo2qpdl (recommended)'.

The only option from here is to change the driver. I choose the driver by 'Select printer from database' and select one which describes itself simply as 'Samsung CLP-310 Series (SPL-C)' (no mention of foomatic).  However, when I look in the syslog, it still has foo2zjs in the path.

Should I be selecting different option in the 'Choose Driver' dialogue - 'Provide PPD file', or 'Search for a printer driver to download'?  If so, what should I enter in the ensuing dialogue?  Sorry to be so thick!

I'm beginning to think that I made a big mistake in buying a GDI printer - despite the expense, I usually use printers with network interface and embedded PS engine.  This was meant to be a cheap, quick and temporary fix to the problems in obtaining my HP toner cartridges.

---

### Post by tweedledee on 2011-02-21
> **Peter Bell said:**
> Even though I do this, when I add the printer (selecting 'Samsung CLP-310' in the New Printer -> Select Device box), as soon as I click the forward button it automatically searches for a driver without even telling me which one it has chosen.  When I 'Apply' and then look at the printer properties, I see that it shows the 'Make and Model' as 'Samsung CLP-310 Foomatic/foo2qpdl (recommended)'.

Sounds like foomatic has gotten even more obnoxious since the last time I used it (the last time I had Ubuntu installed for more than testing purposes, which is going on three years ago).

I can think of three possible solutions.  One is try selecting your own pdd, you'll find the Samsung one in /usr/share/cups/model/samsung.  However, foomatic may still decide it is smarter than you and reject that one in favor of its own.

Second, there may be a way to tell foomatic to stop auto-configuring printers.  However, given the trend in foomatic and Ubuntu, I doubt that's simple.  (You could also try uninstalling foomatic entirely, as you don't really need it for this purpose, but given Ubuntu package dependencies that may well trigger all kinds of additional uninstall requests.)

The third options is to let foomatic do its thing and install a worthless printer.  In parallel with that, install the Samsung Configurator package and add the printer through the Configurator interface instead, which should avoid the foomatic override.

Hopefully the problem is just that foomatic is a lousy piece of software, and there is no actual problem communicating with the printer once the correct driver is in use.

---

### Post by Peter Bell on 2011-02-21
Well, some good news ..... and some bad!  thank you for all your advice thus far!

> **tweedledee said:**
> You could also try uninstalling foomatic entirely, as you don't really need it for this purpose, but given Ubuntu package dependencies that may well trigger all kinds of additional uninstall requests.

Okay, I opted to do this.  I used Synaptic to find anything which referred to foomatic and did a complete removal.  This didn't appear to remove anything untoward.

I then deleted the printer as previously installed, and re-installed it.  This still selected a driver of its own choosing without any opportunity for human intervention.  However, it has chosen a genuine Samsung ppd.  I restarted CUPS and can now print test pages repeatedly and reliably.  I can print web pages from Firefox and I can print simple images from 'Eye of Gnome'.

However, if I attempt to print a large jpeg (a photo from a 10Mpix camera), I get the same two error lines in syslog and, after 15 minutes, the printed page with the time out error.
```
Feb 21 23:18:24 Desktop kernel: [37174.749667] usblp0: nonzero write bulk status received: -71
Feb 21 23:18:24 Desktop kernel: [37174.749684] usblp0: nonzero read bulk status received: -71

```

Also, if I attempt to print the same web page as earlier (but with background colours and images enabled), The queue status sticks at 'Processing', and there are repeated (every 5 seconds) messages in the syslog: 
```
Feb 21 23:38:20 Desktop kernel: [38367.529106] usblp0: nonzero read bulk status received: -71
Feb 21 23:38:20 Desktop kernel: [38367.529823] usb 2-1.5: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
Feb 21 23:38:25 Desktop kernel: [38372.521744] usblp0: nonzero read bulk status received: -71
Feb 21 23:38:25 Desktop kernel: [38372.522469] usb 2-1.5: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
Feb 21 23:38:30 Desktop kernel: [38377.514215] usblp0: nonzero read bulk status received: -71
Feb 21 23:38:30 Desktop kernel: [38377.514979] usb 2-1.5: usbfs: interface 0 claimed by usblp while 'usb' sets config #1

```

Well, as I've been writing this, I've continued to test - I have managed to print out one copy of my large jpeg, but not yet a copy of the web page with backgrounds .. so something is a little inconsistent.  However, the failures always seem to involve  the usblp0 errors (with or without the usbfs interface claimed .... error).

So, it would seem that I need to tackle the usblp0 -71 errors somehow.

---

### Post by Peter Bell on 2011-02-21
> **Peter Bell said:**
> So, it would seem that I need to tackle the usblp0 -71 errors somehow.

Well, these errors appear to have been resolved by moving the printer to a usb port connected directly to the mobo, rather than connecting through an internal (powered) hub.

I have achieved a print of the web page (with full backgrounds) and my 10Mpix photo in 'best' quality.

So, at the moment, it would appear that the printer is functioning well and reliably - thanks again for all your assistance.

My next experiment will be to try attaching the printer to the usb port on my router, and driving it over the network (to make it available to all computers in the house).

---

### Post by n.masarone on 2011-02-21
Just updated the Unified Driver to version 3.00.80-4 from Synaptic, with the following packages: samsungmfp-configurator-data, samsungmfp-configurator-qt4, samsungmfp-data, samsungmfp-driver, samsungmfp-netdiscovery-oldlibc, samsungmfp-scanner, samsungmfp-eglibc (this one is 2.12.1-1). Now my Samsung CLX-3170FN is fully functional with a wireless network: it can print and scan (!!!) via wireless network. Thanks to all developers !!!

---

### Post by gaboro on 2011-02-21
> **tweedledee said:**
> Therefore, I can't see any way to get 32-bit Ubuntu 10.04 to work with network scanning, at least with this approach. 
Yep, I have tried the amd64 package on lucid and like you wrote, it did not work. That's not that bad for me, since the only lucid maschine is the netbook of my wife and I can upgrade it to maverick anytime...

I would file the sh-problem as a bug but I need your help once again to understand what the problem really is. As far as I got it (not having too much experience in compiling c-programs), the dash package has been with dependency of libc6 2.11 compiled instead of leaving out the compile-time dependency and having package-level dependency only. Is that right that way?

---

### Post by yahs on 2011-02-21
I have a Samsung SCX-4500W and I have been following this thread for a long time. Just want to comment on my own recent experiences re scanning. I have similar issuses as gaboro while using Lucid, but just thought I'd report that I did a fresh install of Natty Narwhal (from index of dailylive 19/02/2011). I enabled the repositories and installed the following packages (all version 3.00.80-4) samsungmfp-configurator-data, samsungmfp-configurator-qt3, samsungmfp-data, samsungmfp-driver, samsungmfp-netdiscovery-oldlibc, samsungmfp-scanner, samsungmfp-lpr and samsungmfp-eglibc (samsung2.12.1-1). Instant success - I can print and scan via wireless network. Natty is not quite ready yet, but no doubt it will be come April. Thanks as always to Tweedledee for fantastic effort and expertise.

---

### Post by TheDevilYouKnow on 2011-02-21
I know this is a silly question as I have read most of this thread, however - Has anyone actually gleaned out a straightforward procedure to install this particular printer driver? I myself am an Ubuntu/Linux noob and am slowly but surely expanding my understanding bit by precious bit. It seems like there should be a thread/post somewhere describing a such a thing. I apologize if it sounds like I am being lazy - I assure you I am not. But judging by the size of the thread ( hours of reading ) this seems like a really big issue for at least the Samsung owners. I certainly appreciate the wealth of know-how displayed here.
 
 
TDYK.

---

### Post by Peter Bell on 2011-02-21
Another little problem! I want to investigate the configurator so I've used Synaptic to install samsungmfp-netdiscovery-oldlibc (which had a dependency: samsungmfp-eglibc32) and samsungmfp-configurator-data.

However, I don't know how to run the configurator - I don't see any new entries in the Applications or System menus .... so where does the executable go and what is it called?

---

### Post by winningthepowerball on 2011-02-21
This was very helpfull.
 
thanks

---

### Post by tweedledee on 2011-02-21
> **Peter Bell said:**
> Another little problem! I want to investigate the configurator so I've used Synaptic to install samsungmfp-netdiscovery-oldlibc (which had a dependency: samsungmfp-eglibc32) and samsungmfp-configurator-data.

However, I don't know how to run the configurator - I don't see any new entries in the Applications or System menus .... so where does the executable go and what is it called?

You'll need to install either the samsungmfp-configurator-qt3 or -qt4 package as well.  (Believe me - I'd love to simplify the complexity of the number of packages.)  Good luck with the router/USB hookup, but I think it should work at this point.  I'm not sure why the different port generated the usb errors; I used to see reports of issues like that with hubs all the time and had some bad experiences myself a long time ago, but less commonly in recent years.

---

### Post by tweedledee on 2011-02-21
> **yahs said:**
> I have similar issuses as gaboro while using Lucid, but just thought I'd report that I did a fresh install of Natty Narwhal (from index of dailylive 19/02/2011). I enabled the repositories and installed the following packages (all version 3.00.80-4) samsungmfp-configurator-data, samsungmfp-configurator-qt3, samsungmfp-data, samsungmfp-driver, samsungmfp-netdiscovery-oldlibc, samsungmfp-scanner, samsungmfp-lpr and samsungmfp-eglibc (samsung2.12.1-1). Instant success - I can print and scan via wireless network.

That's a relief.  I was worried that Natty would fail with the 2.12 build, since it's using 2.13.  Maybe I won't have to recompile the eglibc library for every release, just some....

---

### Post by tweedledee on 2011-02-21
> **gaboro said:**
> I would file the sh-problem as a bug but I need your help once again to understand what the problem really is. As far as I got it (not having too much experience in compiling c-programs), the dash package has been with dependency of libc6 2.11 compiled instead of leaving out the compile-time dependency and having package-level dependency only. Is that right that way?

You've explained as much as I really understand.  However, yahs' post suggests that the issue has been resolved (at least for now) with Natty, so there may not be much point.  I doubt the Ubuntu devs will release a fix for Lucid at this point, even though it is LTS.  It's still a valid bug, but if you can deal with it by upgrading to 10.10 and the problem does reappear, it's not likely to get much attention.

---

### Post by tweedledee on 2011-02-21
> **TheDevilYouKnow said:**
> I know this is a silly question as I have read most of this thread, however - Has anyone actually gleaned out a straightforward procedure to install this particular printer driver? I myself am an Ubuntu/Linux noob and am slowly but surely expanding my understanding bit by precious bit. It seems like there should be a thread/post somewhere describing a such a thing. I apologize if it sounds like I am being lazy - I assure you I am not. But judging by the size of the thread ( hours of reading ) this seems like a really big issue for at least the Samsung owners. I certainly appreciate the wealth of know-how displayed here.
 
 
TDYK.

The first post is a regularly updated summary of (nearly) everything important in all the other comments.  Basically, my recommend if the printer doesn't "just work" is to install the Samsung drivers via my repository as described in the first post.  All the caveats and whatnot are there only if you run into problems.

---

### Post by tapanit on 2011-02-21
There's one extra problem with the Samsung drivers: the scanner can only be used within the same network segment, it can't be reached from a machine behind a router or firewall. (Printing works fine, just enter the machine name/address manually.)

Here's a workaround for those in this situation (works for me): 
replace /opt/Samsung/mfp/bin/netdiscovery with this:

#!/bin/sh
if [ -f $HOME/.samsung.netdiscovery ]
then cat $HOME/.samsung.netdiscovery
else
  LD_LIBRARY_PATH=/opt/Samsung/eglibc32/lib /opt/Samsung/mfp/bin/netdiscovery32 $*
fi

Then, in some machine that *is* in the same network segment with the Samsung, do

/opt/Samsung/mfp/bin/netdiscovery >.samsung.netdiscovery

and copy the resulting .samsung.netdiscovery to the machine(s) in other network segments.

If you have several Samsung's in different network segments this obviously won't work, but I think simply appending netdiscovery results from each might do it (I don't have many of them son can't test this).

---

### Post by tapanit on 2011-02-21
> **tapanit said:**
> 
/opt/Samsung/mfp/bin/netdiscovery >.samsung.netdiscovery

Oops, that should have been

/opt/Samsung/mfp/bin/netdiscovery --all --scanner >.samsung.netdiscovery

Without those options it only finds printers.

---

### Post by hokiejp on 2011-02-22
> **tweedledee said:**
> I somehow overlooked that Lucid 32-bit was also now acting up.  Does it work on lucid if you force-install the eglibc32-amd64 package?

This would be much simpler if there wasn't the stupid error with sh requiring particular versions of eglibc as well.  Please open a bug on launchpad about the sh errors you saw, as I am not looking forward to creating dozens of version of libraries to match every Ubuntu update because something is compiling wrong, when it all works fine on Debian.  (Well, actually, it'd all be much simpler if Samsung produced decent drivers, but I'm less optimistic about resolving that problem.)

The main reason why I built a 32bit glibc to work around this problem was because I knew it wouldn't conflict with any of the native utilities on my system (i.e. the shell in this case).  It seems silly, but would it be possible to build a 64bit glibc for 32 bit systems and use the 64 bit version of netdiscovery?

I think another way to do it would be to build a shell against the new glibc and distribute the shell binary as well.

---

### Post by tweedledee on 2011-02-22
> **tapanit said:**
> Oops, that should have been

/opt/Samsung/mfp/bin/netdiscovery --all --scanner >.samsung.netdiscovery

Without those options it only finds printers.

I suspect this is a somewhat rare case, but I've added a note about this solution to the main post.

---

### Post by tweedledee on 2011-02-22
> **hokiejp said:**
> The main reason why I built a 32bit glibc to work around this problem was because I knew it wouldn't conflict with any of the native utilities on my system (i.e. the shell in this case).  It seems silly, but would it be possible to build a 64bit glibc for 32 bit systems and use the 64 bit version of netdiscovery?

No.  32-bit libraries will work on a 64-bit system, but not the other way around.  I agree it would probably solve the problem if it would work, but the actual implementation requires completely isolating the 64-bit processes and is a lot more involved.

> **hokiejp said:**
> I think another way to do it would be to build a shell against the new glibc and distribute the shell binary as well.

Actually, you probably could just compile a new shell, even without worrying about the new glibc.  However, I haven't figured out how to package such a solution.  I can't actually distribute a recompiled shell for general use, because installation would conflict too severely to be resolved.  And I haven't worked out a solution that would reliably isolate all the Samsung-related process to their own shell (or chroot, or other separate process area) and still be general enough to package up.  (If I ever have a few solid days to work on this, which seems unlikely, I might get it to work, in which case most of these other ongoing problems could also be dealt with.  But that's perhaps just wishful thinking and not realistic given my free time right now.)

---

### Post by urusha on 2011-02-24
It seems unattended-upgrades still doesn't work.
Well...
```
# unattended-upgrades -d
Initial blacklisted packages: 
Starting unattended upgrades script
Allowed origins are: ["['Ubuntu', 'lucid-security']", "['Ubuntu', 'lucid-updates']", "['Ubuntu', 'lucid-backports']", "['Ubuntu', 'lucid-proposed']", "['Ubuntu', 'lucid']", "['Medibuntu', 'lucid']", "['LP-PPA-ricotz', 'lucid']", "['LP-PPA-llyzs', 'lucid']", "['debian', 'suldr']"]
Checking: grub-pc (["<Origin component:'main' archive:'lucid-updates' origin:'Ubuntu' label:'Ubuntu' site:'ru.archive.ubuntu.com' isTrusted:True>"])
Checking: grub-common (["<Origin component:'main' archive:'lucid-updates' origin:'Ubuntu' label:'Ubuntu' site:'ru.archive.ubuntu.com' isTrusted:True>"])
Checking: samsungmfp-driver (["<Origin component:'extra' archive:'' origin:'suldr' label:'' site:'www.bchemnet.com' isTrusted:True>"])
Checking: samsungmfp-data (["<Origin component:'extra' archive:'' origin:'suldr' label:'' site:'www.bchemnet.com' isTrusted:True>"])
Checking: samsungmfp-scanner (["<Origin component:'extra' archive:'' origin:'suldr' label:'' site:'www.bchemnet.com' isTrusted:True>"])
pkgs that look like they should be upgraded: grub-pc
grub-common
Done downloading            
blacklist: []
Packages that are auto removed: ''
InstCount=0 DelCount=0 BrokenCout=0
Packages that are upgraded: grub-pc grub-common
...

``````
# head /var/lib/apt/lists/www.bchemnet.com_suldr_dists_debian_Release
Architectures: i386 amd64 all
Codename: debian
Components: extra
Date: Sun, 20 Feb 2011 15:44:47 UTC
Origin: suldr
MD5Sum:
 d41d8cd98f00b204e9800998ecf8427e                0 Release
 ba918d56a0f800fde76bdfcdf33d4d34             7983 extra/binary-all/Packages
 8d21f26d113d2b26fe66636fefc10256             2107 extra/binary-all/Packages.bz2
 552f10bb2412cc3487ea126ba73d957f             1911 extra/binary-all/Packages.gz
# head /var/lib/apt/lists/ru.archive.ubuntu.com_ubuntu_dists_lucid-updates_Release
Origin: Ubuntu
Label: Ubuntu
Suite: lucid-updates
Version: 10.04
Codename: lucid
Date: Wed, 23 Feb 2011 21:35:36 UTC
Architectures: amd64 armel i386 ia64 powerpc sparc
Components: main restricted universe multiverse
Description: Ubuntu Lucid Updates
MD5Sum:

```So, after comparing files, I think the "Release" file should contain:
```
Origin: debian
Label: debian
Suite: suldr
```This is for "debian suldr"; line in 50unattended-upgrades

Thanks.

---

### Post by tweedledee on 2011-02-24
> **urusha said:**
> So, after comparing files, I think the "Release" file should contain:
```
Origin: debian
Label: debian
Suite: suldr
```This is for "debian suldr"; line in 50unattended-upgrades

Thanks.

I did a little more reading on this and think you are correct.  However, I used an origin/label of "bchemnet" instead of "debian" to avoid any potential conflicts.  So if you substitute "bchemnet" for "debian" in the unattended updates config, I think it should work.  However, as I don't have unattended updates installed, I haven't tested, so let me know if it still fails.

---

### Post by urusha on 2011-02-24
Thanks,
```
"bchemnet suldr";
```now works exactly as it should.

---

### Post by cedric_tux on 2011-02-25
I'm getting error message when i try to upgrade to the latest version.
As it is showed there is a problem with the libc6
 
sudo aptitude full-upgrade 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following packages are BROKEN:
  samsungmfp-netdiscovery 
The following packages will be REMOVED:
  samsungmfp-eglibc32{u} 
The following packages will be upgraded:
  samsungmfp-configurator-qt4 
1 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 2 083kB of archives. After unpacking 2 832kB will be freed.
The following packages have unmet dependencies:
  samsungmfp-netdiscovery: Depends: libc6 (< 2.10) but 2.11.1-0ubuntu7.8 is installed.
The following actions will resolve these dependencies:

Remove the following packages:
samsungmfp-configurator-qt4

Keep the following packages at their current version:
samsungmfp-netdiscovery [Not Installed]

Score is 132

Accept this solution? [Y/n/q/?]

---

### Post by tweedledee on 2011-02-25
> **cedric_tux said:**
> I'm getting error message when i try to upgrade to the latest version.

I'm not sure what's triggering the problem, but removing samsungmfp-configurator-qt4, autoremoving all automatically installed packages, and then re-installing samsungmfp-configurator-qt4 should work.

---

### Post by SteveBBB on 2011-03-05
Several months ago, I installed the Samsung Unified Printer Driver repository and setup a Samsumg ML-1915 printer using method **IIc. **described on page 1 of this forum. I installed the basic driver set **Samsungmfp-driver **and **Samsungmfp-data** and everything worked fine, including automatic regular updates of the drivers from the Lucid Update Manager. However, for the last week or so, the Update Manager has not been able to access the repository and gives the following errors:

Failed to fetch [http://www.bchemnet.com/suldr/dists/debian/Release.gpg](http://www.bchemnet.com/suldr/dists/debian/Release.gpg)  Something wicked happened resolving ':http' (-5 - No address associated with hostname)
Failed to fetch [http://www.bchemnet.com/suldr/dists/debian/extra/i18n/Translation-en_CA.bz2](http://www.bchemnet.com/suldr/dists/debian/extra/i18n/Translation-en_CA.bz2)  Something wicked happened resolving ':http' (-5 - No address associated with hostname)
Failed to fetch [http://www.bchemnet.com/suldr/dists/debian/extra/binary-i386/Packages.gz](http://www.bchemnet.com/suldr/dists/debian/extra/binary-i386/Packages.gz)  Unable to connect to [www.bchemnet.com:http:]("http://www.bchemnet.com:http:")
Some index files failed to download, they have been ignored, or old ones used instead.

Is there a solution for this? Thanks in advance for assistance.

---

### Post by tweedledee on 2011-03-05
> **SteveBBB said:**
> Is there a solution for this? Thanks in advance for assistance.

It sounds like there is a problem with your configuration or sources.list.  Try removing the repository (delete, not disable) and then adding it again as a new one.

---

### Post by SteveBBB on 2011-03-06
> **tweedledee said:**
> It sounds like there is a problem with your configuration or sources.list.  Try removing the repository (delete, not disable) and then adding it again as a new one.

I tried this, but now when I add the following source to the source list in Ubuntu Software Center "deb [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian extra" I get an error saying cannot access the repository and to check my internet connection. All other sources are acting OK and can be accessed and updated. I have tried using "deb [http://www.bchemnet.com/suldr]("http://www.bchemnet.com/suldr/") debian extra" (without the final /) but this generates the same errors. 

Is everything OK on the repository side? Is this some kind of permission issue? I am using Lucid Lynx and the most recent linux kernel which went out just a few days ago version 2.6.32-29-generic.

---

### Post by tweedledee on 2011-03-06
> **SteveBBB said:**
> Is everything OK on the repository side? Is this some kind of permission issue? I am using Lucid Lynx and the most recent linux kernel which went out just a few days ago version 2.6.32-29-generic.

Your previous error was not related to a repository problem.  The current one is.  During the last 36-48 hours, connections have frequently been dropped when attempting to connect to the repository.  I'm not sure what's going on, as it's something to do with my hosting service, but I'm hopeful it will clear up soon.  In the meantime, I'm finding that about 1/4 of the time a connection will successfully be made, the rest of them time out.

---

### Post by SteveBBB on 2011-03-06
> **tweedledee said:**
> Your previous error was not related to a repository problem.  The current one is.  During the last 36-48 hours, connections have frequently been dropped when attempting to connect to the repository.  I'm not sure what's going on, as it's something to do with my hosting service, but I'm hopeful it will clear up soon.  In the meantime, I'm finding that about 1/4 of the time a connection will successfully be made, the rest of them time out.

Tweedledee:

Thanks. I will let the Update Manager do its thing and connect when it can until your internet service problem is resolved. By the way, this forum is by far the best resource on the web for Ubuntu and newer Samsung printers, better even than Samsung's own resources. Well done.

---

### Post by kp goin on 2011-03-07
Ubuntu 10.10 Maverick Meerkat
My Samsung SCX-4623F printer/copier/scanner needs the proper driver and I think these posts are the solution to installing it. But because I am new to Ubuntu I don't understand too much of the talk. Can someone put this in a step by step process and be open to questions along the way? I've downloaded the Unified Printer Driver from Samsung's web site but from there I need help from the people with experience.
   kp goin

---

### Post by SteveBBB on 2011-03-07
> **kp goin said:**
> Ubuntu 10.10 Maverick Meerkat
My Samsung SCX-4623F printer/copier/scanner needs the proper driver and I think these posts are the solution to installing it. But because I am new to Ubuntu I don't understand too much of the talk. Can someone put this in a step by step process and be open to questions along the way? I've downloaded the Unified Printer Driver from Samsung's web site but from there I need help from the people with experience.
   kp goin

Your best bet is not to install the Unified Printer Driver from Samsung's website since it will install extra programs and configurators that from my experience are no longer compatible with the current versions of Ubuntu. The cleanest method is to follow the recommended install procedure "IIc" from the very first page of this forum. You basically install the repository link following the step by step instructions provided. Then start the Ubuntu Software Center and then install the recommended packages for Samsung Printer-Scanners which are *samsungmfp-driver*, *samsungmfp-data* and *samsungmfp-scanner*. When you plug your usb cable into your computer (after installing these packages), the system should automatically recognize the device and install the drivers. If your printer-scanner is not automatically recognized, than follow the manual installation instructions also on page 1 of this forum.

Just a word of caution, the repository site has been not recognizing update requests lately, so this might prevent you from installing the repository and drivers. Tweedledee, the originator for this site and the developer of the drivers and the repo, has said this matter is being looked at, and it may even be already fixed.

---

### Post by 9koland on 2011-03-08
i just installed drivers for samsung 1665 mono laser printer using this guide: [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/)
thanks all of you :D

---

### Post by tweedledee on 2011-03-08
As the guide on this forum had grown into a true monster, I've radically simplified it to focus only on the repository solution.  Information about other solutions and troubleshooting information has been moved to the website, which has been very extensively revised.  Hopefully the new format will reduce confusion for new users and provide a simpler approach to solving problems.

Also, network connectivity issues to the repository are supposedly fixed.  (Apparently there was a DDoS attack on my provider.)  Please let me know if you continue to have problems.

---

### Post by kp goin on 2011-03-09
nOOb
Samsung: SCX-4623F
USB: 2.0
Unified Linux Driver version: not sure-downloaded from Samsung's web page approx 12/10-1/11.
Before beginning, how do I find and erase existing Unified Linux Driver files?
kp goin

---

### Post by tweedledee on 2011-03-09
> **kp goin said:**
> Before beginning, how do I find and erase existing Unified Linux Driver files?
kp goin

Look at the last section of this page (the uninstallation instructions): [http://www.bchemnet.com/suldr/smfpv3.html](http://www.bchemnet.com/suldr/smfpv3.html)

---

### Post by kp goin on 2011-03-10
nOOb
Samsung: SCX-4623F
USB: 2.0
Unified Linux Driver version: not sure-downloaded from Samsung's web page approx 12/10-1/11.
If I make a mistake after in-putting information or I don't like what's happened, is there a way to back up the step and return to the previous position?
kp goin

---

### Post by tweedledee on 2011-03-10
> **kp goin said:**
> If I make a mistake after in-putting information or I don't like what's happened, is there a way to back up the step and return to the previous position?

If you mean that you're following the manual uninstall steps, then no, not really.  But the only two commands that seem likely to do any "damage" to your system if you mistype would be the two involving "rm -r".  One of those directs to /opt, which is probably otherwise empty anyway.  And if you accidently delete more of the share/cups folder than necessary, a re-installation of cups will fix it (which I suggest you do anyway).  The vast majority of errors will just result in "file not found" and you can try again.

---

### Post by kp goin on 2011-03-21
nOOb
Samsung: SCX-4623F
USB: 2.0
Unified Linux Driver version: not sure-downloaded from Samsung's web page approx 12/10-1/11
As a matter of curiosity, what is the "*" as in "sudo rm /usr/lib/libtiff.so.3*" or "sudo rm /usr/lib/libstdc++.so.5*" or "sudo rm /usr/lib/libqt-mt.so*"?
This is a major leap forward so I have been learning, learning, learning before I start pushing those "apply" buttons.
             kp goin

---

### Post by tweedledee on 2011-03-21
> **kp goin said:**
> As a matter of curiosity, what is the "*" as in "sudo rm /usr/lib/libtiff.so.3*" or "sudo rm /usr/lib/libstdc++.so.5*" or "sudo rm /usr/lib/libqt-mt.so*"?
This is a major leap forward so I have been learning, learning, learning before I start pushing those "apply" buttons.

The "*" is a wildcard, meaning that the command should match anything in that space (at the end of a name, it means match anything from 0 to many additional characters at the end of the file name).  In the particular cases above, there are multiple files that begin with the same name but have slightly different endings.  For example, you will have both libstdc++.so.5 and libstdc++.so.5.0.7 (the first is actually a link [shortcut or alias] to the second).  "libstdc++.so.5*" matches (and removes) both of those in a single command, saving you from some typing by not requiring two separate commands.

---

### Post by kp goin on 2011-03-23
nOOb
Samsung: SCX-4623F
USB: 2.0
Unified Linux Driver version: not sure-downloaded from Samsung's web page approx 12/10-1/11

   I came across some "Permission" and "lock" issues for these files on the uninstall and install that are presenting difficulties (see below). All other files were not found in the searches.
   Also, when I start the "Print" wizard (I think a msf term - forgive me) a window shows 3 printers:
          - Laser
          - PDF
          - Samsung-SCX-4623-Series
   Which one are we working with?
                      kp goin

dukecity@dukecity-SX2801:~$ find /usr -type f -name Samsung\*.menu
dukecity@dukecity-SX2801:~$ find /etc -type f -name Samsung\*.desktop
find: `/etc/cups/ssl': Permission denied
find: `/etc/ssl/private': Permission denied
dukecity@dukecity-SX2801:~$ find /etc -type f -name Samsung\*.directory
find: `/etc/cups/ssl': Permission denied
find: `/etc/ssl/private': Permission denied
dukecity@dukecity-SX2801:~$ find /etc -type f -name Samsung\*.menu
find: `/etc/cups/ssl': Permission denied
find: `/etc/ssl/private': Permission denied
dukecity@dukecity-SX2801:~$ 

dukecity@dukecity-SX2801:~$ sudo apt-get update
[sudo] password for dukecity: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
dukecity@dukecity-SX2801:~$

---

### Post by diopteryx on 2011-03-23
Thank you for the work, dedication and files.

My ML-2525 worked perfectly with just the driver and data files you provide.

I did talk to a Samsung rep on live chat who couldn't be interested in the bugs or the misleading inferences about being able to use their software/UPD with Linux.

I doubt it made any impression, but I plonked them anyway.

Thanks again.

---

### Post by tweedledee on 2011-03-24
> **kp goin said:**
> I came across some "Permission" and "lock" issues for these files on the uninstall and install that are presenting difficulties (see below). All other files were not found in the searches.
The permission errors are no big deal; they just mean that the find tool was unable to search those directories because they are restricted to root only access.  If you ran the search again with "sudo" you wouldn't see those errors, but the files in question aren't in those locations anyway.  The lock error usually occurs because you have Synpatic or some other package management program open at the time you try to run apt-get.  Only one program that can manipulate packages is allowed to do so at a time to avoid conflicts.


> **kp goin said:**
> Also, when I start the "Print" wizard (I think a msf term - forgive me) a window shows 3 printers:
          - Laser
          - PDF
          - Samsung-SCX-4623-Series
   Which one are we working with?
The Samsung one is what the driver installation created.  PDF is now fairly standard on all Ubuntu systems.  I'm not sure what "Laser" would be; if you go to the print manager, and right-click on the printer to go to Properties, then check the Make & Model line, you can see what it actually is.

---

### Post by tweedledee on 2011-03-24
> **diopteryx said:**
> I did talk to a Samsung rep on live chat who couldn't be interested in the bugs or the misleading inferences about being able to use their software/UPD with Linux.

I doubt it made any impression, but I plonked them anyway.

Thanks for trying.

---

### Post by kp goin on 2011-03-25
nOOb
Samsung: SCX-4623F
USB: 2.0
Unified Linux Driver version: not sure-downloaded from Samsung's web page approx 12/10-1/11

Let's take the uninstallation first.

Below is a copy of the various commands that were submitted.
I reinstalled cups-bsd (correctly I hope) from Synaptic.
I did not reinstall /usr/lib/libqt-mt.so* and /usr/lib/libqui.so* If they need to be installed, please advise.
I don't know how to check if /usr/bin/lpr is functioning correctly.
From what I know about graphical windows I don't believe I saw one.
 
dukecity@dukecity-SX2801:~$ sudo /opt/Samsung/mfp/uninstall/uninstall.sh
sudo: /opt/Samsung/mfp/uninstall/uninstall.sh: command not found
dukecity@dukecity-SX2801:~$ sudo rm /usr/lib/libtiff.so.3*
rm: cannot remove `/usr/lib/libtiff.so.3*': No such file or directory
dukecity@dukecity-SX2801:~$ rm ~/.sshvfavs
rm: cannot remove `/home/dukecity/.sshvfavs': No such file or directory
dukecity@dukecity-SX2801:~$ rm ~/.sshvrc
rm: cannot remove `/home/dukecity/.sshvrc': No such file or directory
dukecity@dukecity-SX2801:~$ sudo rm /usr/lib/libstdc++.so.5*
rm: cannot remove `/usr/lib/libstdc++.so.5*': No such file or directory
dukecity@dukecity-SX2801:~$ sudo rm /usr/lib/libqt-mt.so*
rm: cannot remove `/usr/lib/libqt-mt.so*': No such file or directory
dukecity@dukecity-SX2801:~$ sudo rm /usr/lib/libqui.so*
rm: cannot remove `/usr/lib/libqui.so*': No such file or directory
dukecity@dukecity-SX2801:~$ sudo rm -r /opt/Samsung/mfp/
rm: cannot remove `/opt/Samsung/mfp/': No such file or directory
dukecity@dukecity-SX2801:~$ sudo rm /usr/sbin/smfpd
rm: cannot remove `/usr/sbin/smfpd': No such file or directory
dukecity@dukecity-SX2801:~$ sudo rm /usr/bin/lpr.orig
rm: cannot remove `/usr/bin/lpr.orig': No such file or directory
dukecity@dukecity-SX2801:~$ sudo rm /usr/bin/lpr
rm: cannot remove `/usr/bin/lpr': No such file or directory
dukecity@dukecity-SX2801:~$ sudo rm -r /usr/share/cups/model/samsung
rm: cannot remove `/usr/share/cups/model/samsung': No such file or directory
dukecity@dukecity-SX2801:~$ sudo rm /usr/lib/libmfp.so*
rm: cannot remove `/usr/lib/libmfp.so*': No such file or directory
dukecity@dukecity-SX2801:~$ sudo rm /usr/lib/cups/backend/mfp
rm: cannot remove `/usr/lib/cups/backend/mfp': No such file or directory
dukecity@dukecity-SX2801:~$ sudo rm /usr/lib/cups/filter/libscmss*.so
rm: cannot remove `/usr/lib/cups/filter/libscmss*.so': No such file or directory
dukecity@dukecity-SX2801:~$ sudo rm /usr/lib/cups/filter/rastertosamsung*
rm: cannot remove `/usr/lib/cups/filter/rastertosamsung*': No such file or directory
dukecity@dukecity-SX2801:~$ sudo rm /usr/lib/cups/filter/pscms
rm: cannot remove `/usr/lib/cups/filter/pscms': No such file or directory
dukecity@dukecity-SX2801:~$ sudo rm /usr/lib/cups/filter/smfpautoconf [only v3.00.43 and newer]
rm: cannot remove `/usr/lib/cups/filter/smfpautoconf': No such file or directory
rm: cannot remove `[only': No such file or directory
rm: cannot remove `v3.00.43': No such file or directory
rm: cannot remove `and': No such file or directory
rm: cannot remove `newer]': No such file or directory
dukecity@dukecity-SX2801:~$ sudo rm /usr/lib/sane/libsane-smfp.so*
rm: cannot remove `/usr/lib/sane/libsane-smfp.so*': No such file or directory
dukecity@dukecity-SX2801:~$ sudo rm /etc/sane.d/smfp.conf
rm: cannot remove `/etc/sane.d/smfp.conf': No such file or directory
dukecity@dukecity-SX2801:~$ sudo rm /etc/mfpcommon.modules.conf
rm: cannot remove `/etc/mfpcommon.modules.conf': No such file or directory
dukecity@dukecity-SX2801:~$ sudo rm /etc/init.d/smfpd
rm: cannot remove `/etc/init.d/smfpd': No such file or directory
dukecity@dukecity-SX2801:~$ sudo rm /etc/rc0.d/K07smfpd
rm: cannot remove `/etc/rc0.d/K07smfpd': No such file or directory
dukecity@dukecity-SX2801:~$ sudo rm /etc/rc1.d/K07smfpd
rm: cannot remove `/etc/rc1.d/K07smfpd': No such file or directory
dukecity@dukecity-SX2801:~$ sudo rm /etc/rc6.d/K07smfpd
rm: cannot remove `/etc/rc6.d/K07smfpd': No such file or directory
dukecity@dukecity-SX2801:~$ sudo rm /etc/udev/rules.d/9?_smfpautoconf.rules [only v3.00.43 and newer]
rm: cannot remove `/etc/udev/rules.d/9?_smfpautoconf.rules': No such file or directory
rm: cannot remove `[only': No such file or directory
rm: cannot remove `v3.00.43': No such file or directory
rm: cannot remove `and': No such file or directory
rm: cannot remove `newer]': No such file or directory
dukecity@dukecity-SX2801:~$ find /usr -type f -name Samsung\*.desktop
dukecity@dukecity-SX2801:~$ 
dukecity@dukecity-SX2801:~$ find /usr -type f -name Samsung\*.directory
dukecity@dukecity-SX2801:~$ 
dukecity@dukecity-SX2801:~$ find /usr -type f -name Samsung\*.menu
dukecity@dukecity-SX2801:~$ 
dukecity@dukecity-SX2801:~$ find /etc -type f -name Samsung\*.desktop
find: `/etc/cups/ssl': Permission denied
find: `/etc/ssl/private': Permission denied
dukecity@dukecity-SX2801:~$ find /etc -type f -name Samsung\*.directory
find: `/etc/cups/ssl': Permission denied
find: `/etc/ssl/private': Permission denied
dukecity@dukecity-SX2801:~$ find /etc -type f -name Samsung\*.menu
find: `/etc/cups/ssl': Permission denied
find: `/etc/ssl/private': Permission denied
dukecity@dukecity-SX2801:~$ 
Uninstalled? Yes/No?
kp goin

---

### Post by tweedledee on 2011-03-25
> **kp goin said:**
> I did not reinstall /usr/lib/libqt-mt.so* and /usr/lib/libqui.so* If they need to be installed, please advise.
I don't know how to check if /usr/bin/lpr is functioning correctly.
If you have the package libqt3-mt installed, you should re-install it; otherwise you do not need to do anything about those other files.  Reinstalling CUPS would have fixed any lpr issues.
> **kp goin said:**
> Uninstalled? Yes/No?
Yes.  If you set up the repository, install the packages, and configure the printer, you should be set.

---

### Post by kp goin on 2011-03-25
nOOb
Samsung: SCX-4623F
USB: 2.0
Unified Linux Driver version: not sure-downloaded from Samsung's web page approx 12/10-1/11

I have both libqt-mt.so* and libqui.so* installed. Okay?
I plan on installing samsungmfp-driver, samsungmfp-data and samsungmfp-scanner.
You mention a Qt4 interface. Should that also be installed and what is the correct file?
kp goin

---

### Post by tweedledee on 2011-03-26
> **kp goin said:**
> I have both libqt-mt.so* and libqui.so* installed. Okay?
I plan on installing samsungmfp-driver, samsungmfp-data and samsungmfp-scanner.
You mention a Qt4 interface. Should that also be installed and what is the correct file?

Based on your output in the previous message, it didn't appear that libqt-mt and libqui were present; however, they won't hurt anything if they are.

The three packages you list are the minimum you'll need.  You may also need either samsungmfp-configurator-qt3 or samsungmp-configurator-qt4 (either one, that's where the qt3 vs. qt4 comes in, and they have the same function).  The configurator will provide an alternate interface to add a printer and is needed if you plan to scan over the network instead of usb (you don't have to run the program, but some background bits it brings with it are needed for the driver to find a network-connected scanner).  Various other packages will be pulled in by all of those as needed.

---

### Post by kp goin on 2011-03-26
nOOb
Samsung: SCX-4623F
USB: 2.0
Unified Linux Driver version: not sure-downloaded from Samsung's web page approx 12/10-1/11

Started install of samsungmfp-driver and got the message:

"Failed to lock the package manager
Check if you are currently running another software management tool, e.g. Synaptic or aptitude. Only one tool is allowed to make changes at a time.
Details
The package indexes are currently changed by apt-get."

   I cleared everything out and had nothing left but the "bchemnet" repository up. And still the same message.
   The "apt-get" - this morning I was fooling around with the apt-get commands update and upgrade. Don't know if there's something there.
kp goin

---

### Post by kp goin on 2011-03-26
nOOb
Samsung: SCX-4623F
USB: 2.0
Unified Linux Driver version: not sure-downloaded from Samsung's web page approx 12/10-1/11

Disregard the previous message. I was not aware I had to restart to install the apt-get updates or upgrades (didn't I read some place that one didn't have to restart in linux?).
Did the restart, installed the discussed files, restarted again (just to be sure) and tried printing a page. The following message was printed out:

   INTERNAL ERROR - Please use the proper driver.
   Position : 0x0 (0)
   System : h6fw_5.5.35/xl_op
   Line : 167
   Version : SPL 5.35 06-03-2009
Kp goin

---

### Post by tweedledee on 2011-03-26
> **kp goin said:**
> Disregard the previous message. I was not aware I had to restart to install the apt-get updates or upgrades (didn't I read some place that one didn't have to restart in linux?).
Some other process must still have been running; a restart shouldn't be necessary.  And while it's true that you really NEED to restart a Linux machine, it is often the case that doing so is the simplest and fastest solution.  (I only restart my daily used and abused computers maybe a dozen times a year.)

> **kp goin said:**
> Did the restart, installed the discussed files, restarted again (just to be sure) and tried printing a page. The following message was printed out:

Did you set up a new printer, either through the Configurator or standard printing interface?  If you kept the one that had been installed earlier, you'll need to delete it and begin fresh.

---

### Post by kp goin on 2011-03-27
We have a printer! What a ride.
    Thank you to SteveBBB. Everyday I reviewed these posts looking for  anything I might have missed. I always started with your post and invariably I would find some bit of information in that post that I hadn't seen before that helped the cause.
Thank you.
    But to tweedledee goes the lion's share of the "thank you's". I'm sure there were many questions and statements on my part that made you roll your eyes. Thank you for your patience.
    It's the education, however, that I got from those two web pages of instructions that I am most thankful for. This was two plus weeks of an intense (5-6 hours a day - I'm retired) Linux education for which I am most grateful. I am a far more educated person in Linux today than I was at the start of this because of tweedledee. Thank you.
   And here's the kicker - this was fun...a lot of fun.
   My pleasure.   
kp goin.

---

### Post by tweedledee on 2011-03-27
> **kp goin said:**
> I'm sure there were many questions and statements on my part that made you roll your eyes. Thank you for your patience.
    It's the education, however, that I got from those two web pages of instructions that I am most thankful for. This was two plus weeks of an intense (5-6 hours a day - I'm retired) Linux education for which I am most grateful. I am a far more educated person in Linux today than I was at the start of this because of tweedledee. Thank you.
   And here's the kicker - this was fun...a lot of fun.
   My pleasure.   
kp goin.

You're welcome.  Education's what I do for a living.  Believe me, it takes a lot more than anything you said to reach eye-rolling stage - I get the occasional truly bizarre gem from the college students.

---

### Post by weslowsk on 2011-04-05
Hi,

Model: Samsung ML-1665
Connected by: USB
OS: Linux Mint 9
Driver: Installed using the repository as described on the first page of this thread (installed Apr. 4, 2011 so you know how recent the driver is)
What does work: printing any text file, any standard browser page (Firefox), using the print button from within a Flash game at [http://pbskids.org/curiousgeorge/games/snapshot/snapshot.html](http://pbskids.org/curiousgeorge/games/snapshot/snapshot.html)
What doesn't work: Trying to use a print button from within a Flash game at [http://www.pinkydinkydoo.com/storybox.html;](http://www.pinkydinkydoo.com/storybox.html;) the output is one page of all black ink (what an ink waste!)

Is this a bug with the driver or with the Firefox Flash plugin or both? Can anyone else replicate the same "black page printout" for either the same printer model at the same website or a different Samsung model at the same website? The OS is updated to the most recent patch levels of Firefox, etc.

---

### Post by tweedledee on 2011-04-05
> **weslowsk said:**
> Is this a bug with the driver or with the Firefox Flash plugin or both? Can anyone else replicate the same "black page printout" for either the same printer model at the same website or a different Samsung model at the same website? The OS is updated to the most recent patch levels of Firefox, etc.

I've never tried to print from Flash before today.  However, a quick test on various sites to my pdf printer was never particularly successful, and I've no reason to think any other printer driver would work better.  So at least on my system (which is 64-bit, and so occasionally quirky with Flash anyway), the issue would seem to be with Flash.  However, anyone else with a different experience should share.

---

### Post by nashjc on 2011-04-10
The drivers are very much appreciated. 

As a test for my wife's SCX 4521F I used an old Asus Eee 900 with Ubuntu 10.10 and managed to get both scanning and printing to work. 

Then ....
   I found that cups-pdf printer seems to work, but no output file is found.

I looked in /home/me/PDF and also /var/spool locations.

Is there a possible conflict or mis-setting. I note that sometimes the /System/Administration/Printing shows exclamation mark on printer, but it still fires.

I'll be happy to provide more info if this is a new problem. 

Best, JN

---

### Post by tweedledee on 2011-04-10
> **nashjc said:**
>    I found that cups-pdf printer seems to work, but no output file is found.

It's certainly new to me.  Which packages did you install, and for i386 or amd64?  From which program(s) have you tried to print to the cups-pdf printer?

If you installed the samsungmfp-lpr package, that would be my immediate guess, and you could try again without that piece.

---

### Post by nashjc on 2011-04-10
Thanks for quick reply. Will try to clean up then reinstall without the 'samsung-lpr' package. Probably a couple of days before I can report -- my wife uses her machine.

JN

Mon April 11, 2011

Have had a chance to experiment. Seems the Asus Eee 900 was "polluted" by earlier attempts to install Samsung drivers. 

Using an external HD with Ubuntu 10.04.1 on my wife's own Eee 1005HA, I easily did the sources.list update (and key import) and installed samsungmfp-driver (which pulled in samsungmfp-data) and samsungmfp-scanner. Rebooted. Printer seemed to be installed by this and worked fine. cups-pdf already there and seems fine. Scanning in simple-scan or xsane fine.

Then did same thing with the native Ubuntu 10.04 on the Eee 1005HA drive. 

Notice I do need to reboot after install. 

Thanks. JN

---

### Post by oblong on 2011-04-12
Ubuntu 10.10 32 bit. Samsung SCX-4216F.

When first plugged in, Ubuntu recognised the printer and installed the printer (using the SpliX V. 2.0.0 driver). Worked fine. But no scanner recognised. Installed xsane, still no scanner.

So I followed the first post of this thread, installing only samsungmfp-legacy-scanner. That worked fine. So thank you very much.

---

### Post by MZ250Supa5 on 2011-04-15
This thread has been of great help to me in setting up my Samsung CLP 315 printer using the Splix driver.  However, the printer does seem to want to produce reams of paper all with this kind of message:

SPL-C Error - Incomplete Session by time out

Position : 0x112db0 (1125808 )

SYSTEM    : src/os_hook

LINE     : 1646

VERSION : SPL-C 5.35 11-20-2007

Despite this, it does now print decent pictures in portrait format, but not in landscape, a small matter as I doubt I shall be printing many landscape orientation pictures, (though it would be nice to be able to, but I have a very nice Canon inkjet to do pictures).  I am more concerned about the amount of paper being used, so if anyone has any ideas I'd be pleased to know... I'm not really a fan of paper, preferring trees.

Not quite at the tearing out of hair stage... Oh, isn't Linux wonderful?

---

### Post by tweedledee on 2011-04-16
> **MZ250Supa5 said:**
> This thread has been of great help to me in setting up my Samsung CLP 315 printer using the Splix driver.
I've never had any success with the Splix driver - your error message pages are all I can get on a good day with it.  Perhaps someone else can help, otherwise all I can recommend is trying my repository.

> **MZ250Supa5 said:**
> Not quite at the tearing out of hair stage... Oh, isn't Linux wonderful?

While I understand your sentiment, I have work colleagues that can't print double-sided on a shared duplex printer because the Windows driver is incorrectly configured (I'm in the only person out of 30 that can actually use all the printer capabilities because I run Linux).  And I have other colleagues with printers connected to Macs that refuse to print, scan, or both 9 days out of 10.  At least with Linux there are alternative options when something doesn't work right the first time, and I don't have to put up with multifunction printers that disable scanning because the vendor Mac/Windows driver thinks the ink is low.

---

### Post by MZ250Supa5 on 2011-04-16
Thanks for the reply... yes, I have been tearing my hair out for about two and a half years now, ever since I started using Linux, though I have to say I do tend to tear less out now, and I would never consider a return to Windows. The frustration, if I can call it that, is due, more than anything, to the challenges presented; challenges that spur me on to seeking a solution rather than giving up, which was often the case when I used Windows.  

My question about Linux being wonderful, whilst rhetorical, was, if anything meant to have a reply in the affirmative.   

I tend to concur with that joke where computers are like air conditioning... works well until windows are opened.

As far as scanners are concerned, I have an Epson Perfection V200 Photo, which was a veritable swine to set up, but now works perfectly.

I shall try the drivers on your repository, and persevere until I get everything working as it should

---

### Post by paker on 2011-04-22
Reporting success

SCX-4623 printer/scanner

There was one glitch. After Steps 1 through 3, the driver (samsungmfp-driver) was sitting in Synaptic Package Manager, but not installed. I had to go to Synaptic, mark samsungmfp-driver, and install. I think it installed samsungmfp-data and one more automatically.

Without samsungmfp-driver installed, Add Printer led me to SCX-4200. Accepted it. Test page failed "Please use the proper driver." Deleted SCX-4200. Did above manual installation. Test page printed correctly.

Likewise, samsungmfp-scanner had to be check-marked and installed in Synaptic Package Manager.

Previously, I was using another Samsung printer (ML-1740). Maybe I should have deleted the printer first.

Thanks, tweedledee.

---

### Post by kowal256 on 2011-04-29
I installed Samsung Unified Driver for my CLX-2160, printer works OK, but scanner 
works correctly only for grayscale. Color images (16 million colors) are split into
3 parts (rgb), each one looks like grayscale img (see attached file).  
[]("http://img64.imageshack.us/i/outm.jpg/")[[IMG]http://img64.imageshack.us/img64/6919/outm.th.jpg[/IMG]]("http://img64.imageshack.us/i/outm.jpg/")

---

### Post by tweedledee on 2011-05-09
> **kowal256 said:**
> I installed Samsung Unified Driver for my CLX-2160, printer works OK, but scanner 
works correctly only for grayscale. Color images (16 million colors) are split into
3 parts (rgb), each one looks like grayscale img (see attached file).  

It's hard for me to troubleshoot scanning issues, and to even try I need to know if you used the Samsung installer or my repository, and which version of the driver.  If you used my repository, does it occur with both the -legacy and non-legacy versions?

---

### Post by Artorius89 on 2011-05-23
I thank you very much, Mr. Tweedledee, for your hard and very useful volunteer work, as I thank all the people who have contributed in collecting in this forum an abundance of answers and guides that is very useful to Linux newbies like me.
Unfortunately, I have a problem: your scanner driver doesn&#8217;t seem to work on Lubuntu 11.04 (which I have installed on an old computer I need to use the scanner with for work): whereas *sane-find-scanner* &#8220;sees&#8221; my Samsung SCX-4521F multifunction printer, no software (nor the *scanimage -L* command) manages to acknowledge its existence. I believe I have followed your guide faithfully and I have tried all the workarounds you suggest on  your website, but it hasn&#8217;t helped.
I hope you or some other gentleman can help me. I have tried setting up the printer-scanner on a Ubuntu 11.04 laptop, too, where it worked perfectly; so, since Lubuntu and Ubuntu are very closely connected, I&#8217;m hoping this could be something easy: maybe some packages the former lacks in comparison to the latter.
I hope I haven&#8217;t posted this request in the wrong place: should I have looked for a Lubuntu-specific section/forum?

---

### Post by Artorius89 on 2011-05-23
Nevermind: after several days of migration from one Linux distribution to the other, in search of the one that would support the device and, at the same time, be light enough for the old computer, I have finally solved the puzzle! The multifunction printer must not be connected to the PC through a USB hub but directly through a USB port. As I feared, it was subtle... Grrr! :mad:
Thank you anyway. :) I hope this post can help somebody facing the same maze.

---

### Post by tweedledee on 2011-05-23
> **Artorius89 said:**
> Nevermind: after several days of migration from one Linux distribution to the other, in search of the one that would support the device and, at the same time, be light enough for the old computer, I have finally solved the puzzle! The multifunction printer must not be connected to the PC through a USB hub but directly through a USB port. As I feared, it was subtle... Grrr! :mad:
Thank you anyway. :) I hope this post can help somebody facing the same maze.

I added this to the scanning trouble-shooting steps on the website.  Thanks for sharing the solution.

---

### Post by Jepic Phail on 2011-05-25
Here is the setup process I went through for my Samsung CLP-315W. Overall, the setup process was a breeze (thanks tweedledee!). Hope this is useful to some of you.

Note: I am using Linux Mint 10 and aptitude.

Printing via USB:

[LIST=1]
[*]Follow the instruction and get the samsungmfp- repository.
[*]Install **samsungmfp-driver** (**samsungmfp-data** will be installed automatically as a dependency).
[*]Go to **Administration** > **Printing** and delete previously created printer device(s) (I had to reboot here but I doubt it is necessary).
[*]Connect printer via USB.
[*]Once new device has been created, go to **Properties** and change the **Make and Model **to **Samsung CLP-310 Series (SPL-C)**.
[/LIST]
For wireless printing:

[LIST=1]
[*]Connect to your printer. To get the IP address of your printer:
[LIST=1]
[*]Hold down on the printer power button for about 5 seconds; light will start to flash and when it begins to flash even faster let it go. This will print out the Configuration and **Network Report**.
[*]Locate the IP address on the **Network Report** and type it into your web browser.
[/LIST]
 
[*]Once you are in the **SyncThru Web Service**, go to **Network Settings** and than to **Wireless**.
[*]Configure your **Wireless Setting** through the **Wizard** and follow the setup process (note that if your SSID contains space your network will not be displayed).
[*]Once the printer is connected to your LAN go to printer setting (**Administration** > **Printing**; **Properties**).
[*]Click the **Change** button for the **Device URI**.
[*]Go to **Network Printer** > **Find Network Printer** and type in the IP address of your printer.
[*]Apply the settings when it find the **PASSTHRU**. **Device URI** should looks something like this: **lpd://[IP Address]/PASSTHRU**.
[/LIST]
:popcorn:

---

### Post by lhamada on 2011-06-16
Hello Mr. tweedledee,

A SpliX driver source modified for CLP-315/CLP-310 needs to be tested on the SpliX forum, could you or anyone help?

[http://sourceforge.net/tracker/?func=detail&aid=3196609&group_id=175815&atid=874747](http://sourceforge.net/tracker/?func=detail&aid=3196609&group_id=175815&atid=874747)

Attached filename is splix.clp315.tar.bz2  (on splix.sf.net-->report -->Supports request tracker-->*needs more testing* - CLP-315/CLP-310 - Topic )

Happy testing to all

---

### Post by tweedledee on 2011-06-16
> **lhamada said:**
> Hello Mr. tweedledee,

A SpliX driver source modified for CLP-315/CLP-310 needs to be tested on the SpliX forum, could you or anyone help?

[http://sourceforge.net/tracker/?func=detail&aid=3196609&group_id=175815&atid=874747](http://sourceforge.net/tracker/?func=detail&aid=3196609&group_id=175815&atid=874747)

Attached filename is splix.clp315.tar.bz2  (on splix.sf.net-->report -->Supports request tracker-->*needs more testing* - CLP-315/CLP-310 - Topic )

Happy testing to all

I can't help (wrong printer), but certainly there are many people around who have posted regarding the CLP-31x.  For any of those users, there should not be any issues with testing this SpliX driver in parallel with my packages, except possibly the *-lpr package.  Testing in parallel having used the Samsung installer may work.

---

### Post by thatsallurspaceships on 2011-06-17
At first Linuxmint recognized printer CPL-300 with the foo2qpdl driver correctly. After finishing this tutorial there is foo2qpdl and SPL-C driver in the properties. Both drivers work with the printer. Should i use this Splix driver, which is now chosen automatically or do i still need to make other changes? The problem with dark colors still remains with both drivers.
There is also an ICM file available, but i cannot make the printer use it. [http://ubuntuforums.org/showthread.php?t=879902](http://ubuntuforums.org/showthread.php?t=879902)

Edit: It would be nice if someone could help me with CUPS too. I'm new to Linux and i don't understand if i need this for printing and how to use it. There is only one USB connected local printer, used by a single computer.

---

### Post by tweedledee on 2011-06-17
> **thatsallurspaceships said:**
> At first Linuxmint recognized printer CPL-300 with the foo2qpdl driver correctly. After finishing this tutorial there is foo2qpdl and SPL-C driver in the properties. Both drivers work with the printer. Should i use this Splix driver, which is now chosen automatically or do i still need to make other changes?
If the splix driver works, you do not need to do anything as described in this thread or with my repository.

> **thatsallurspaceships said:**
> The problem with dark colors still remains with both drivers.
There is also an ICM file available, but i cannot make the printer use it. [http://ubuntuforums.org/showthread.php?t=879902](http://ubuntuforums.org/showthread.php?t=879902)

Edit: It would be nice if someone could help me with CUPS too. I'm new to Linux and i don't understand if i need this for printing and how to use it. There is only one USB connected local printer, used by a single computer.

You have CUPS unless you've deliberately removed it and don't need to do anything special to use it.  As I understand the thread you reference, you need to download the zip file (last link provided) and install the ppd and icm files as described in post 20 of that thread.  Then it is just a matter of selecting which profile you want to use in the printer settings.  Neither of those modifications to your system is irreversible, although you should be aware that the ppd file will likely be overwritten if you switch your printer driver or have to re-add it as a new printer in the future.  (The /etc/cups/ppd location is for the ppd files of printers currently installed, whereas all original ppds are stored in various locations in /usr.  The ppd is just a schematic that describes the functions and capabilities of the printer in a way that the CUPS system can understand when it translates the printer instructions from programs to the format your printer actually uses.)

It is probably possible to adapt the solution in that thread to work with the Samsung SPL-C driver, but as currently constructed the color correction would only work with splix.

---

### Post by thatsallurspaceships on 2011-06-18
After installing foo2zjs (there was an missing foo2qpdl error) in Synaptic the printer uses the PLC-300 (custom) profile to print much brighter colors. It is still not optimal to print colors. The colored text is unclear and the color balance, the contrast in my opinion is too heavy. But it is fine for me. Some custom profiles, photos and text and graphics and text, can't be used. There is a CUPS error: client-error-document-format-not-supported choosing them.
If this isn't great what is it then?

P.S.: Thanks for helping

---

### Post by uqbar on 2011-06-25
Hi.
I've got a SCX-4623F MFP which is running very fine as a printer with your "solution".
And with Ubuntu 11.04 the change in the /etc/sane.d/xerox_mfp.conf is not needed any more.
I'm running Kubuntu variant with Skanlite application.
Is there any way to scan documents at resolutions higher than 600 DPIs?
Is there a way to exploit the FAX features from Linux?

---

### Post by vzdor on 2011-07-01
Hi everyone,

I have a problem with my scx3200. Sometimes if I send a document/1 page, I get a few pages of garbage/random characters, a few lines at the beginning of each printed page, instead of the text. If I restart the printer and send the same document, it is OK. 

Anyone had a similar problem? 

I'm using debian unstable and unified printer drivers from the repo. May be it is something else, not the driver?

---

### Post by tweedledee on 2011-07-02
> **vzdor said:**
> Hi everyone,

I have a problem with my scx3200. Sometimes if I send a document/1 page, I get a few pages of garbage/random characters, a few lines at the beginning of each printed page, instead of the text. If I restart the printer and send the same document, it is OK. 

Anyone had a similar problem? 

I'm using debian unstable and unified printer drivers from the repo. May be it is something else, not the driver?

Based on my experience, it's most likely the driver if restarting the printer fixes the problem.  Have you tried the legacy driver?  Samsung has also released a new driver, 3.00.90, that I will try to test sometime soon - and package for my repository if I don't see any obvious problems.

---

### Post by thatsallurspaceships on 2011-07-08
> **tweedledee said:**
> Based on my experience, it's most likely the driver if restarting the printer fixes the problem.  Have you tried the legacy driver?  Samsung has also released a new driver, 3.00.90, that I will try to test sometime soon - and package for my repository if I don't see any obvious problems.Could you please describe each step how to get the package. Sorry my bad english and nescience in Linux. :-&

---

### Post by tweedledee on 2011-07-08
> **thatsallurspaceships said:**
> Could you please describe each step how to get the package. Sorry my bad english and nescience in Linux. :-&

Just install the same packages as you have now (whichever those are), except choose the ones with -legacy in the name.

---

### Post by thatsallurspaceships on 2011-07-08
Just want to thank you for helping. :popcorn:

---

### Post by tweedledee on 2011-07-10
Hello everyone, especially brave folks willing to test a new version!

Attached to this message is the newest version of the netdiscovery tool from Samsung (32 and 64 bit both included).  Those of you who have network printers and/or scanners, please do the following:
1. In a terminal, run /opt/Samsung/mfp/bin/netdiscovery --all
2. In a terminal, run /opt/Samsung/mfp/bin/netdiscovery --all --scanner
3. Unpack the zip file and open a terminal in the directory you unpacked in
4. In the terminal, execute ./netdiscovery## --all (where ## is either 32 or 64, depending on your system)
5. In the terminal, execute ./netdiscovery## --all --scanner
6. Post the output from all runs
7. Post your libc6 version (viewable in Synaptic or other package managers) or your Ubuntu/Debina/other distro version (I can get the libc6 version from that)

I *think* that Samsung completely rewrote this tool and it now works with all modern libc6.  (The file size is radically different, it appears to be using libraries differently, and I don't generate any glib errors even when it is not using my custom eglibc.)  However, the tool has never worked correctly at detecting my network printer, and I don't have a scanner to detect at all, so it is difficult for me to be certain.  So before I package it up and eliminate the need for the custom eglibc and complex package scheme, I would appreciate some feedback.

I also believe that the associated driver version (3.00.90) in fact works (unlike 3.00.80) and adds support for a variety of newer printers.

---

### Post by yahs on 2011-07-11
Tweedledee,

I have a samsung SCX-4500 Wireless multi printer running on Unity in Natty 11.04 Linux Kernel 2.6.38-8 generic.
I used the repository to install the drivers and I have both printing and scanning working as normal.

The version of libc6 is 2.13-Oubuntu13

I enclose a copy of the print outs as requested

sk@Laptop:~$ /opt/Samsung/mfp/bin/netdiscovery --all
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
ip: 192.168.1.68    slp: 0,0,0,0 snmp: 0,0,0 dsc: "Samsung SCX-4500W [SEC001599622AE6]"
# Total 1 printers found, 5s elapsed


sk@Laptop:~$ /opt/Samsung/mfp/bin/netdiscovery --all --scanner
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
ip: 192.168.1.68    slp: 0,0,0,0 snmp: 0,0,0 dsc: "Samsung SCX-4500W"
a8 00 43 10 53 61 6d 73 75 6e 67 20 53 61 6d 73
75 6e 67 20 53 43 58 2d 34 35 30 30 57 20 53 65
72 69 65 73 1d 33 04 2b 00 00 27 d8 00 00 36 d8
00 01 51 00 00 01 00 00 00 00 36 d8 00 00 36 d8
01 00 05 05 00 00
# Total 1 scanners found, 5s elapsed

sk@Laptop:~$ cd Downloads
sk@Laptop:~/Downloads$ ls
netdiscovery.zip	netdiscovery32                   oneiric-desktop-i386.iso

sk@Laptop:~/Downloads$  ./netdiscovery32 --all 
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
ip: 0.0.0.0         slp: 0,0,0,0 snmp: 0,0,0 dsc: "Samsung SCX-4500W"
ip: 192.168.1.68    slp: 0,0,0,0 snmp: 0,0,0 dsc: " [SEC001599622AE6]"
# Total 2 printers found, 5s elapsed

sk@Laptop:~/Downloads$  ./netdiscovery32 --all --scanner
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
# Total 0 scanners found, 5s elapsed

Not sure where to find the driver 3.00.90, as Samsung UK still lists 3.00.65 for my search.

When I get a copy of 3.00.90, I will test with a clean install both for 10.04 and then 11.04

Many Thanks

---

### Post by tweedledee on 2011-07-11
> **yahs said:**
> When I get a copy of 3.00.90, I will test with a clean install both for 10.04 and then 11.04


I have 3.00.90 mostly packaged and just need to do some final testing - later this week I'll post the packages and you can test with those rather than dealing with Samsung.

Can you try one more combination?  Temporarily rename /opt/Samsung/mfp/bin/netdiscovery32, copy the new netdiscovery32 to /opt/Samsung/mfp/bin/, and re-run the first two tests?  You can then restore the original netdiscovery32.

---

### Post by yahs on 2011-07-11
Renamed /opt/Samsung/mfp/bin/netdiscovery32  /opt/Samsung/mfp/bin/netdiscovery_old
copied netdiscovery32 fron Download directory to /opt/Samsung/mfp/bin
copy of results as follows

sk@Laptop:~$ /opt/Samsung/mfp/bin/netdiscovery --all
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
ip: 0.0.0.0         slp: 0,0,0,0 snmp: 0,0,0 dsc: "Samsung SCX-4500W"
ip: 192.168.1.68    slp: 0,0,0,0 snmp: 0,0,0 dsc: " [SEC001599622AE6]"
# Total 2 printers found, 5s elapsed
sk@Laptop:~$ /opt/Samsung/mfp/bin/netdiscovery --all --scanner
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
# Total 0 scanners found, 5s elapsed
sk@Laptop:~$ 

if you need anything else just let me know

---

### Post by tweedledee on 2011-07-11
> **yahs said:**
> if you need anything else just let me know

Could you try scanning (using whatever program) when the new netdiscovery32 is in /opt (as just done)?  I'm concerned because it's not showing the scanner in the output, but that may not actually be a problem (my printer never shows up with netdiscovery but works fine anyway).

---

### Post by yahs on 2011-07-12
Unfortunately, when the new netdiscovery32 is in /opt scanning does not work.

As part of my installation I have found that Samsungmfp-netdiscovery-oldlibc (3.00.80-4) works but Samsungmfp-netdiscovery does not.

if the mfp is attached by usb instead of wireless then there are no problems, it is only the network scanning that appears to be the tricky bit.

---

### Post by tweedledee on 2011-07-12
> **yahs said:**
> Unfortunately, when the new netdiscovery32 is in /opt scanning does not work.

As part of my installation I have found that Samsungmfp-netdiscovery-oldlibc (3.00.80-4) works but Samsungmfp-netdiscovery does not.

if the mfp is attached by usb instead of wireless then there are no problems, it is only the network scanning that appears to be the tricky bit.

Thanks.  It will be a couple of days before I have time to try to track down the problem, but I have some ideas on how to keep everything working.

---

### Post by auss_troll on 2011-07-14
ok...have read the entire thread on this issue, tried all the tips/tricks and still can not get the scanner of my Samsung SCX-4521F to show up with "scanimage -L".

I am running Debian wheezy/sid with a 2.6.38 kernel. udev is version 171-3 (from synaptic listing).  All of the unified drivers are the latest on the site that I can install, and have also tried the legacy ones, but no joy.

I can use "usbip" to export the usb port for the Samsung, attach to it from a Windoze XP system and print and scan with no issues.

any ideas of where to look next or something else to try?

Thanks,

Mark

---

### Post by tweedledee on 2011-07-17
> **yahs said:**
> Unfortunately, when the new netdiscovery32 is in /opt scanning does not work.

As part of my installation I have found that Samsungmfp-netdiscovery-oldlibc (3.00.80-4) works but Samsungmfp-netdiscovery does not.

if the mfp is attached by usb instead of wireless then there are no problems, it is only the network scanning that appears to be the tricky bit.

Yahs - could you repeat the tests with the new netdiscovery after unpacking the attached file into /opt?  Scanner only tests are fine, I've figured out the printer issues.  Please test directly and when the older netdiscovery32 is replaced by this and invoking netdiscovery.  And if you see a scanner in the listing, also please try actually scanning.

---

### Post by tweedledee on 2011-07-17
> **auss_troll said:**
> ok...have read the entire thread on this issue, tried all the tips/tricks and still can not get the scanner of my Samsung SCX-4521F to show up with "scanimage -L".

I am running Debian wheezy/sid with a 2.6.38 kernel. udev is version 171-3 (from synaptic listing).  All of the unified drivers are the latest on the site that I can install, and have also tried the legacy ones, but no joy.

I can use "usbip" to export the usb port for the Samsung, attach to it from a Windoze XP system and print and scan with no issues.

any ideas of where to look next or something else to try?

Thanks,

Mark

Does printing work, or is it only scanning that fails?  I assume you've tried different USB ports?  If you use usbip, can your Debian box scan via the IP?

---

### Post by yahs on 2011-07-17
I was expecting something different!

When I unpack the file smfp-common.tar.gz, I get the folder smfp-common which has the folder lib64 which contains the files libnetsnmp.so.10 and libnetsnmp.so.10.0.2

I am running 32 bit natty.

I have libnetsnmp.so.10 in /usr/lib but no libnetsnmp.so.10.02

Can you clarify what I need to do

---

### Post by tweedledee on 2011-07-17
> **yahs said:**
> I was expecting something different!

When I unpack the file smfp-common.tar.gz, I get the folder smfp-common which has the folder lib64 which contains the files libnetsnmp.so.10 and libnetsnmp.so.10.0.2

I am running 32 bit natty.

I have libnetsnmp.so.10 in /usr/lib but no libnetsnmp.so.10.02

Can you clarify what I need to do

Put the whole chain in /opt/ so that you get /opt/smfp-common/lib/*.  Except use the archive attached to this post rather than the last one - I meant to post the 32-bit version for you.  The various netdiscovery files will preferentially invoke libnetsnmp.so.10 from /opt/smfp-common/lib/ rather than /usr/lib/, but otherwise this will have no effect on your system and can be removed after testing.

---

### Post by yahs on 2011-07-17
congratulations,

new netdiscovery32 now finds scanner. I did quick scans using simple scan, libre office and xsane. All worked okay

---

### Post by yahs on 2011-07-18
This might be of interest for users who have a samsung mfp and have problems with network scanning

I generally use the repositories provided by Tweedledee which have enabled me to have a working Samsung mfp with network printing and scanning.

I have a Dell Dimension 5100 for testing (Pentium 4, onboard graphics) with a 160GB hard disk.

Today I did a clean install of Ubuntu 11.10 (Oneiric Oceleot Alpha 2). 

My Printer is a Samsung SCX-4500w which is connected by wireless.

As an experiment, I downloaded the latest Samsung Unified driver (3.00.90), which I found under support for a Samsung CLP-315W/XAA.

I unpacked and extracted the files to the Downloads directory.

Using the terminal I moved to /Downloads/cdroot/Linux

Executed the command sudo./install.sh

The Samsung Unified GUI interface appeared, asked which users to add to the LP group, suggested disabling parallel printing and then started the process of installing a printer.

Unfortunately at this stage Ubuntu crashed. (Something to do with applets?)

On restarting, the Samsung Unified Driver icon appeared on the desktop and when I selected it the CLP-315W/XAA showed as being installed.

I deleted this printer and selected Add New Printer, chose the network option and instantly my SXC-4500w appeared.

I finished by testing and successfully printing a test page.

I then clicked on the scanner icon and very quickly the SCX-4500w showed up.

Agan I tested that it worked by scanning using simple scan and libre office.

This is a big improvement over Ubuntu 10.04, where I couldn't get network scanning without the netdiscovery packages from Tweedledee.

---

### Post by tweedledee on 2011-07-18
> **yahs said:**
> As an experiment, I downloaded the latest Samsung Unified driver (3.00.90), which I found under support for a Samsung CLP-315W/XAA.

Thanks for sharing - I am actually in the process of extensively testing this version now and hope to release updated packages within a week.  More confirmation that it works on different systems is helpful.

However, other users should be aware that I have encountered problems using the lastest driver with some versions of libc6.  The holdup in release the packages is identifying exactly which ones and under what conditions.  I'm fairly confident that the packages I'm finishing will work well for everyone and add support for the newest printers.

---

### Post by ftoral on 2011-07-19
> **tweedledee said:**
> Hello everyone, especially brave folks willing to test a new version!

Hi,

primarily, i've to say that i'm using a workaround posted here in launchpad : [https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/576531/comments/12](https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/576531/comments/12)
And my CLX-3175N printer and scanner works perfectly in network mode with that solution.

But this is only a workaround. I'm always interested to get the legacy or your modified driver version.
I've tested your package, and i've removed the workaround in order to get the original netdiscovery to run, so here are my outputs :
```

$ /opt/Samsung/mfp/bin/netdiscovery --all
netdiscovery: relocation error: /lib32/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
netdiscovery: relocation error: /lib32/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
ip: 192.168.0.10    slp: 0,0,0,0 snmp: 0,0,0 dsc: " [SEC0015996B9AD3]"
# Total 1 printers found, 5s elapsed

$ /opt/Samsung/mfp/bin/netdiscovery --all --scanner
netdiscovery: relocation error: /lib32/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
netdiscovery: relocation error: /lib32/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
# Total 0 scanners found, 5s elapsed

$ ./netdiscovery32 --all
./netdiscovery32: error while loading shared libraries: libnetsnmp.so.10: wrong ELF class: ELFCLASS64

$ ./netdiscovery64 --all
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
ip: 0.0.0.0         slp: 0,0,0,0 snmp: 0,0,0 dsc: "Samsung CLX-3170"
ip: 192.168.0.10    slp: 0,0,0,0 snmp: 0,0,0 dsc: " [SEC0015996B9AD3]"
# Total 2 printers found, 5s elapsed

```

I've recently updated to Natty 11.04 with libc6 version 2.13-0ubuntu13
Thanks for your work tweedledee.

---

### Post by tweedledee on 2011-07-24
The repository has been updated.  In addition to updating to the latest driver version, I made several substantial changes to the repository structure itself.  In brief:
1. The samsungmfp-legacy-* packages are gone; current packages with those names exist solely for upgrade purposes and can be removed after you update (if you remove all of them, you may need to tell your package manager to set one or more of the non-legacy packages as manual installed).
2. The -legacy-data and -legacy-driver packages still exist but have been renamed -data-legacy and -driver-legacy.  The -data-legacy package should generally not be needed.  The -driver-legacy package can be installed even with other non-legacy pieces, so switching driver versions should now be much simpler.
3. The netdiscovery packages are gone in favor of -network and -network-legacy.  I *think* that these two packages will work for everyone, even those running Ubuntu 10.04 32-bit that couldn't get network scanning to work under any circumstances.

I've done fairly extensive testing of all of this (also thanks to those who reported testing results!), but it's still possible you will encounter problems.  Please let me know if something stops working when you update and/or if you have problems updating (I think I worked through all the possible update scenarios/package replacements, but I may have missed something).

As best as I can determine, these packages render all the various network work-arounds for using a scanner irrelevant, and should work fine without any effort on your part.  And I have tried to construct the revised package system in such a way that maintenance of the packages in the future is less effort and has greater flexibility if needed, with the result that future updates may occur more regularly and should involve with less disurption.

---

### Post by auss_troll on 2011-07-25
> **tweedledee said:**
> Does printing work, or is it only scanning that fails?  I assume you've tried different USB ports?  If you use usbip, can your Debian box scan via the IP?
I have tried several USB ports, and still only the printer is detected and works.  with the usbip, i can get the printer online, but not the scanner...

with the usbip, i only see the printer, though it is showing that the scanner is shared out as well (I think) i have two devices on the bus (busid is 3)...devices are 3-1 and 3-2, with 2 being the printer...

mark

---

### Post by Jukka42343 on 2011-07-25
Thank You helping me to solve my scanner problem (would not scan)


[LIST]
[*]Samsung CLX 3175N
[/LIST]

[LIST]
[*]sitting on a fixed IP address on LAN
[/LIST]

[LIST]
[*]DISTRIB_ID=Ubuntu
[/LIST]

[LIST]
[*]DISTRIB_RELEASE=10.04
[/LIST]

[LIST]
[*]DISTRIB_CODENAME=lucid
[/LIST]

[LIST]
[*]DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
[/LIST]

Here is what I did to make it work (a compilation from various posts in this thread):

[PHP]
cd /opt/Samsung/mfp/bin/
mv  netdiscovery netdiscovery.orig
[/PHP][COLOR=#000000][FONT=Times New Roman][FONT=sans-serif] 
[/FONT][/FONT][/COLOR]Download zip from post  [COLOR=#000000][FONT=Times New Roman][FONT=sans-serif][http://ubuntuforums.org/showpost.php?p=11034804&postcount=721 ]("http://ubuntuforums.org/showpost.php?p=11034804&postcount=721")
[ and extract  ]("http://ubuntuforums.org/showpost.php?p=11034804&postcount=721")[/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][FONT=sans-serif]netdiscovery32 to [/FONT][/FONT][/COLOR]/opt/Samsung/mfp/bin


[PHP]
cd /opt/Samsung/mfp/bin/

./netdiscovery32  --all --scanner > ~/.samsung-netdiscovery
[/PHP][COLOR=#000000][FONT=Times New Roman][FONT=sans-serif] 

Create a script [/FONT][/FONT][/COLOR]/opt/Samsung/mfp/bin/netdiscovery to circuvent firewall problems
 [PHP]
#!/bin/bash
if [ -f ~/.samsung-netdiscovery ]; then
cat ~/.samsung-netdiscovery
else
./netdiscovery32 --all --scanner
fi
 [/PHP]

---

### Post by decoder_oh on 2011-07-25
> **tweedledee said:**
> Hello everyone, especially brave folks willing to test a new version!

Attached to this message is the newest version of the netdiscovery tool from Samsung (32 and 64 bit both included).  Those of you who have network printers and/or scanners, please do the following:
1. In a terminal, run /opt/Samsung/mfp/bin/netdiscovery --all
2. In a terminal, run /opt/Samsung/mfp/bin/netdiscovery --all --scanner
3. Unpack the zip file and open a terminal in the directory you unpacked in
4. In the terminal, execute ./netdiscovery## --all (where ## is either 32 or 64, depending on your system)
5. In the terminal, execute ./netdiscovery## --all --scanner
6. Post the output from all runs
7. Post your libc6 version (viewable in Synaptic or other package managers) or your Ubuntu/Debina/other distro version (I can get the libc6 version from that)


You are my hero. I tried your version of netdiscovery and can finally scan using my new printer/scanner. Here's the output of the commands if you need those:

```

decoder@mordor:~/Samsung$ ./netdiscovery32 --all
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
ip: 192.168.1.124   slp: 0,0,0,0 snmp: 0,0,0 dsc: "Samsung Samsung SCX-3200 [SEC001599812A7B]"
# Total 1 printers found, 5s elapsed
decoder@mordor:~/Samsung$ ./netdiscovery32 --all --scanner
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
ip: 192.168.1.124   slp: 0,0,0,0 snmp: 0,0,0 dsc: "Samsung Samsung SCX-3200"
a8 00 43 10 53 61 6d 73 75 6e 67 20 53 61 6d 73
75 6e 67 20 53 43 58 2d 33 32 30 30 20 53 65 72
69 65 73 20 19 33 84 2b 00 00 27 d8 00 00 36 d8
00 01 51 00 00 01 00 00 00 00 36 d8 00 00 36 d8
00 01 05 05 00 00
# Total 1 scanners found, 6s elapsed

```

This is Ubuntu 11.04 where no other workaround was successful so far. But now SANE works fine :) Thanks!

---

### Post by joneshenrys on 2011-07-25
Fortunately, a new configuration of Ubuntu, I wrote that the first ship with Gutsy 7.10 to replace the Samsung drivers without any scruples. Always updated and maintained by open source software is usually better.

---

### Post by cedric_tux on 2011-07-25
hi [COLOR=Black]tweedledee,

Thanks for the release.

I have one question, the installation of the new packages creates two directories under /opt:
-Samsung
- smfp-common

Is there a reason to create 2 directories? Would it be possible to modify the packages to copy all the necessary files under Samsung?

Thanks,
[/COLOR][]("http://ubuntuforums.org/member.php?u=207037")

---

### Post by tweedledee on 2011-07-25
> **cedric_tux said:**
> hi [COLOR=Black]
I have one question, the installation of the new packages creates two directories under /opt:
-Samsung
- smfp-common

Is there a reason to create 2 directories? Would it be possible to modify the packages to copy all the necessary files under Samsung?

Unfortunately, the /opt directory structure is imposed by hard links when the Samsung utilities were compiled.  Given any option at all, I would eliminate the /opt structure entirely and relocate everything to /usr.  It is technically possible to work around the need for smfp-common, but doing so sets up a potential conflict with standard packages and makes the network functions less reliable.  As usual, a large part of the problem is Samsung's insistence on compiling with libraries that have been obselete for years without the flexibility to use more current libraries.

---

### Post by tweedledee on 2011-07-25
> **auss_troll said:**
> I have tried several USB ports, and still only the printer is detected and works.  with the usbip, i can get the printer online, but not the scanner...

with the usbip, i only see the printer, though it is showing that the scanner is shared out as well (I think) i have two devices on the bus (busid is 3)...devices are 3-1 and 3-2, with 2 being the printer...

mark

Can root see the scanner?  I actually have the problem with my (non-Samsung) scanner that only root can access it by default, and have to use a custom udev rule so that all users or all "lp" users can use it.  This post (and others like it, I originally created my solution before this post existed) may help: [http://jay.sherby.net/2010/01/howto-modify-usb-device-user.html](http://jay.sherby.net/2010/01/howto-modify-usb-device-user.html)

If that is the problem, you just need to figure out which usb device refers to the scanner and create the appropriate rule.

If that's still not the issue, then I'm probably not able to help any further, although other users may be able to.

---

### Post by qirtaiba on 2011-07-31
> **tweedledee said:**
> Hello everyone, especially brave folks willing to test a new version!

Attached to this message is the newest version of the netdiscovery tool from Samsung (32 and 64 bit both included).  Those of you who have network printers and/or scanners, please do the following:

I have a Samsung SCX 6345N, and it doesn't work for me, I get "Total 0 scanners found, 5s elapsed", whether I use "netdiscovery32 --all --scanner" from the zipfile or the one in opt from the latest version of the package.

When I use just "netdiscovery32 --all" I get this:

ip: 192.168.30.249  slp: 0,0,0,0 snmp: 0,0,0 dsc: "Samsung SCX-6x45 [SEC001599057136]"
ip: 192.168.30.83   slp: 0,0,0,0 snmp: 0,0,0 dsc: "Samsung SCX-6x22 [SEC00159941EDA2]"
# Total 2 printers found, 5s elapsed

However, my scanner is one that requires you to run a "netscan" daemon on your workstation with a username and password.  It seems that the Samsung Unified Printer Driver doesn't support this mode of operation, does it?

---

### Post by tweedledee on 2011-08-01
> **qirtaiba said:**
> However, my scanner is one that requires you to run a "netscan" daemon on your workstation with a username and password.  It seems that the Samsung Unified Printer Driver doesn't support this mode of operation, does it?

That is correct - I believe the netscan approach is Windows-only (not even Mac supported), so unless someone has worked out what the scanner output from netdiscovery would need to be for this printer, I don't think the unified driver alone will work.

However, you may be able to install and run the netscan utility using WINE; I'm not sure if that would enable Linux scanning programs to access it or not.

---

### Post by qirtaiba on 2011-08-01
> **tweedledee said:**
> That is correct - I believe the netscan approach is Windows-only (not even Mac supported), so unless someone has worked out what the scanner output from netdiscovery would need to be for this printer, I don't think the unified driver alone will work.

I am working on that.  I found a Perl daemon here ([http://www.jon.demon.co.uk/dell1600n-net-scan/](http://www.jon.demon.co.uk/dell1600n-net-scan/)) which doesn't work out of the box, but could be adapted to do so.  I have captured the network traffic that I need to replicate and now just need to find the time to get it done.  Perhaps this little Perl daemon could be integrated into your package eventually, once working.

---

### Post by tweedledee on 2011-08-01
> **qirtaiba said:**
> I am working on that.  I found a Perl daemon here ([http://www.jon.demon.co.uk/dell1600n-net-scan/](http://www.jon.demon.co.uk/dell1600n-net-scan/)) which doesn't work out of the box, but could be adapted to do so.  I have captured the network traffic that I need to replicate and now just need to find the time to get it done.  Perhaps this little Perl daemon could be integrated into your package eventually, once working.

If you get it working, I don't see any problem with adding it to my repository.

---

### Post by pPrdrm on 2011-08-07
Hi **tweedledee**,
I have been using your debs for quite awhile now and I just wanted to say thank you for the time you spend in making them. I can use my CLP 315 (and before that my CLP 300) without any effort. So thank you again.
I have used your debs in Ubuntu but now am using the in Debian. They work OK. Just some small glitches but the printing process works with no problem. If you ask what are the glitches, I have found only two so far.
1) If I start the "Samsung Unified Driver Configurator" from a terninal I get a message:
[I]Package `cupsys-common' is not available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
ScannerPlugin - font = 9[/I]
2) If I click on  the "About" button on the Editor it crashes with a message:
[I]dynuiloader4.cpp:50: DynUiLoader4: unable to load library 'libquiloaderex.so.4' (libquiloaderex.so.4: cannot open shared object file: No such file or directory)
Aborted[/I]
Other than that all work.

---

### Post by StiltonSandwich on 2011-08-07
Thanks Tweedledee for your great repository and packages.

I recently (about 10-12 days ago) updated to 3.00.90 after it came up as an available update in my update notifier.

Prior to that, everything worked fine. Since then, I was having a problem printing.

Printer: CLP-310N
Connection: IP networking
OS: Kubuntu 10.04
Driver installation source: SULDR via package manager

I don't know which version of the driver I updated from.

What happened was that any and all empty white space at the top of the printout was removed and everything else was shunted up to fill the space, leaving about a 4mm margin. The gap between the top of the paper and the top of the page content always printed out the same size, regardless how big it was supposed to be.

So, for example, when I tried to print an image vertically centred in the middle of the page, it came out at the top of the page. When I tried to print my CV, it had no top margin. When I printed a test page with a line of text in the bottom half of the page and another line right at the bottom, both bits of text were moved up the page the same distance so that the uppermost one was right at the top of the page and the distance between the two lines remained the same.

I tried re-installing the driver and re-creating the printer, to no avail.

The problem now seems to have been solved simply by installing *samsungmfp-driver-legacy* and *samsungmfp-data-legacy* instead of *samsungmfp-driver* and *samsungmfp-data*.

I am posting in case anyone else has the same problem, and as a notification to Tweedledee that this seems to be a problem that's present with the newer driver. Hopefully I'm not repeating what someone has already said. I couldn't find anything about it, but it's such a long thread I can't be sure!

---

### Post by tweedledee on 2011-08-07
> **pPrdrm said:**
> 1) If I start the "Samsung Unified Driver Configurator" from a terninal I get a message:
[I]Package `cupsys-common' is not available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
ScannerPlugin - font = 9[/I]
2) If I click on  the "About" button on the Editor it crashes with a message:
[I]dynuiloader4.cpp:50: DynUiLoader4: unable to load library 'libquiloaderex.so.4' (libquiloaderex.so.4: cannot open shared object file: No such file or directory)
Aborted[/I]

1 - I can't do much about this one, but it's harmless anyway.  Samsung is looking for a package name that hasn't existed in Debian/Ubuntu for 3 years, but all the functions are provided by existing packages.  I could create a dummy package to eliminate the error, but it hasn't seemed worth the effort.

2 - This I was unaware of, and will fix in the next release.  I don't intend to release new packages just to address this, though, unless it shows up anywhere other than the "about" button.

---

### Post by tweedledee on 2011-08-07
> **StiltonSandwich said:**
> I tried re-installing the driver and re-creating the printer, to no avail.

The problem now seems to have been solved simply by installing *samsungmfp-driver-legacy* and *samsungmfp-data-legacy* instead of *samsungmfp-driver* and *samsungmfp-data*.


Did you try any printing with the combination of the legacy driver and standard data packages?  The problem could be in the actual driver or in the ppd file provided in the latest data package, and any fix to the packages is different depending on which it is.

---

### Post by rodrigo666 on 2011-08-10
I was able to successfully install my SCX-3200 laser printer on a Linux Mint following this thread, thanks for it all!

What I can't figure out, however, is how to change the dpi to a draft print, like let's say 300 dpi, since it's options allowed are only 600dpi and 1200dpi.

Any tips about that? I've goggled it a lot without success.

---

### Post by chb on 2011-08-11
Just tried with my CLP-600, footmatic driver works but with SUL I get 

```

[ 3833.133002] rastertosamsung[15831] general protection ip:41126d sp:7fffb3e9fc20 error:0 in rastertosamsungsplc[400000+1e000]

```

Kubuntu 11.04, 64bit

---

### Post by tweedledee on 2011-08-12
> **rodrigo666 said:**
> What I can't figure out, however, is how to change the dpi to a draft print, like let's say 300 dpi, since it's options allowed are only 600dpi and 1200dpi.

Any tips about that? I've goggled it a lot without success.

You can try extracting the ppd from /usr/share/cups/model/samsung for the printer, editing it, and saving it in a local location.  There is a section in the ppd for determining the available resolutions, you may be able to simply copy and change one of the exisiting resolution lines.  Then configure a new printer using the modified ppd file and see if it works.  Sometimes it works, sometimes not.

---

### Post by tweedledee on 2011-08-12
> **chb said:**
> Just tried with my CLP-600, footmatic driver works but with SUL I get 

```

[ 3833.133002] rastertosamsung[15831] general protection ip:41126d sp:7fffb3e9fc20 error:0 in rastertosamsungsplc[400000+1e000]

```

Kubuntu 11.04, 64bit

Using the latest repository packages?  Did it work previously with the unified driver?

Although it may be simplest just to use the foomatic if it works, since you don't have scanning or other complexities that the Samsung driver is better for.

---

### Post by chb on 2011-08-13
> **tweedledee said:**
> Using the latest repository packages?  Did it work previously with the unified driver?


last repo packages and no it didn't work before.


> 
Although it may be simplest just to use the foomatic if it works, since you don't have scanning or other complexities that the Samsung driver is better for.

yes that's what I'll do.

This bug is really strange, I had the same problem under archlinux before, also with the lastest unified drivers.

---

### Post by ket1 on 2011-08-13
Hi everyone,

I'm having the exact same issue as StiltonSandwich:

> **StiltonSandwich said:**
> 
What happened was that any and all empty white space at the top of the  printout was removed and everything else was shunted up to fill the  space, leaving about a 4mm margin. The gap between the top of the paper  and the top of the page content always printed out the same size,  regardless how big it was supposed to be.

My configuration is following:
Printer: CLX-3175N
Connection: IP networking
OS: Ubuntu 10.04

> **tweedledee said:**
> Did you try any printing with the combination of the legacy driver and standard data packages?  The problem could be in the actual driver or in the ppd file provided in the latest data package, and any fix to the packages is different depending on which it is.

Replacing only *samsungmfp-driver* with *samsungmfp-driver-legacy* makes the printing functional again. No need to replace the *samsungmfp-data *package as StiltonSandwich suggested. But that's a shame since the new driver seemed to be a lot better otherwise: scanner recognized and working on the network, ink levels, etc.

Thanks for all the great work so far. If there is a fix for this issue, that'd be awesome, if not then I guess I could live with it ;)

---

### Post by tweedledee on 2011-08-13
> **chb said:**
> This bug is really strange, I had the same problem under archlinux before, also with the lastest unified drivers.

I'll keep it in mind, but it is not obvious to me what I can do to address this particular bug without a lot more information and/or the actual source code for the driver.

---

### Post by tweedledee on 2011-08-13
> **ket1 said:**
> Replacing only *samsungmfp-driver* with *samsungmfp-driver-legacy* makes the printing functional again. No need to replace the *samsungmfp-data *package as StiltonSandwich suggested. But that's a shame since the new driver seemed to be a lot better otherwise: scanner recognized and working on the network, ink levels, etc.

Ink levels I can understand only working with the new driver.  But the scanner should be largely independent of the particular driver version, so I am surprised it does not work with the legacy driver.  I'll try to put together a working version of the 3.00.65 driver that works with the new package structure and make that available to test in the near future.

---

### Post by StiltonSandwich on 2011-08-14
> **tweedledee said:**
> Did you try any printing with the combination of the legacy driver and standard data packages?
> **ket1 said:**
> No need to replace the samsungmfp-data package as StiltonSandwich suggested.
I did not try this. I wrongly assumed I had to pair like with like. I have tried it now, and it does indeed work fine with the combination of legacy driver and standard data.

> **ket1 said:**
> ...the new driver seemed to be a lot better otherwise: scanner recognized and working on the network, ink levels, etc.
I did not know the new driver reported ink levels. How were they reported?

---

### Post by matt3970 on 2011-08-14
Thanks! This worked. I have am ML-2010 and Ubuntu 11.04. When I attempted to print from Google Maps with the map image present, it would take 10-15 minutes (approx never really timed it) for the printout. I followed the instructions and Google maps seems to work fine. 

In the directions, my system hung the first time on the "wget -O - [http://www.bchemnet.com/suldr/suldr.gpg](http://www.bchemnet.com/suldr/suldr.gpg) | sudo apt-key add -". I exited the first time and it did not work. On the second try, I was more patient and the command eventually timed out and the system requested my sudo password. After entering that, I retried the command and it worked fine. I am not sure if the command needs a tweak or not.

Thanks again![COLOR=#000000][FONT=Ubuntu][COLOR=#3C3C3C][/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu][COLOR=#3C3C3C][/COLOR][/FONT][/COLOR]

---

### Post by tweedledee on 2011-08-14
> **StiltonSandwich said:**
> I did not try this. I wrongly assumed I had to pair like with like. I have tried it now, and it does indeed work fine with the combination of legacy driver and standard data.
Only the latest update has allowed mixing the two; your assumption was not unreasonable.

> **StiltonSandwich said:**
> I did not know the new driver reported ink levels. How were they reported?
For many (most?) printers, you should now be able to see the levels by going to the printer properties from your printer administration tool - there will be a section for ink/toner levels.  Until the latest update, that section was non-functional for the large majority of printers.  Now it seems to be functional for many more, although there is still considerable variation in how reliable it is or whether it actually reports levels at all even though it claims to.  (In other words, it now works about as well as any Windows-based printer ink tool - marginally better than random.)

---

### Post by vickoxy on 2011-08-23
Just wanted to say that it works nice with Lubuntu 11.04 and Samsung SCX-4600. Thanks :popcorn:

---

### Post by Yeti can't ski on 2011-08-27
Thanks for the formidable work and thread!

I already wrote to Samsung to complain against their disregard of Linux users. 

I installed the repository and now I am able to print perfectly with my USB-connected SCX-3200, using my old Dell XPS M1330 running Linux Mint Debian Edition - LMDE.

The problem is that I cannot scan, even though the system seems to find the scanner. Output of "sane-find-scanner":

> found USB scanner (vendor=0x04e8 [Samsung Electronics Co., Ltd.], product=0x3441 [SCX-3200 Series]) at libusb:002:004


I already tried switching USB ports (I have only two of them and no hubs) and installed libpng12-dev following the official repository website: [http://www.bchemnet.com/suldr/scanning.html]("http://www.bchemnet.com/suldr/scanning.html")

No success. Any ideas? 

Many thanks in advance.

P.S. - Forgot to mention, my user profile is part of the "lp" group.

---

### Post by Yeti can't ski on 2011-08-28
> **rodrigo666 said:**
> I was able to successfully install my SCX-3200 laser printer on a Linux Mint following this thread, thanks for it all!



Dear rodrigo666, 

I am trying to set up the same printer on LMDE. 

Were you also able to use the scanner? If yes, how? 

Are you printing without any glitches or issues? My printer randomly prints single lines of symbols and codes once in a while...

Many thanks in advance.

---

### Post by Mishkin-Rayman on 2011-09-04
Hi, 

I had some serious problems with getting my **Samsung SCX-3200** to install correctly, and after a lot of banging my head against the wall I figured I'd try installing it as another printer to see if I (by pure luck) would come by a compatible driver. 

I did - on the first attempt! 

Below is an explanation for dummies such as myself as to how I did it. :D 

In ubuntu 10.10, chose **System >> Administration >> Printing**, in the window that pops up, (**Printing - localhost**) click the downwards facing arrow by **Add** (top left corner) and choose **printer** from the drop down menu. 

A new window pops up. Samsung SCX-3200 should be in the menu on the left hand side. Select it and click **forward**.

The computer will say "**Searching for drivers**", and after a little while a new window will pop up. In the **makes** list, choose **generic** and then (in the next window) choose **"PCL 5e printer"** under "**Models**" & **Generic PCL 5e Printer Foomatic/ljet4d** under the "**Drivers**" menu. Click "**forward**"

The driver installs. 

This allows me to both print and scan with great results. I don't know if this method has any drawbacks, but so far it works fine and for our office needs, it's more than adequate. 

Best Regards
/MR

---

### Post by rahuijts on 2011-09-05
Confirming ket1, I have a CLX-3175FN on Ubuntu 11.04

> **ket1 said:**
> Replacing only *samsungmfp-driver* with *samsungmfp-driver-legacy* makes the printing functional again. No need to replace the *samsungmfp-data *package as StiltonSandwich suggested. But that's a shame since the new driver seemed to be a lot better otherwise: scanner recognized and working on the network, ink levels, etc.

The new driver recognized my scanner over the network, but does not print correctly (wrong top margin). The legacy driver prints well, but does not find my scanner. Can I install both drivers at the same time?

---

### Post by tweedledee on 2011-09-05
> **Yeti can't ski said:**
> The problem is that I cannot scan, even though the system seems to find the scanner.

If root cannot scan, then your problem is beyond my ability to help.  If root can, I suggest playing with udev settings as per about 25 posts ago as suggested to another user.

There may also be a kernel setting that Mint and/or Ubuntu is using that causes problems with certain configurations, so you could try looking at what the build options were for your kernel with respect to USB (I don't know if Mint publishes those in an easily accessible place).  The recent reports have been too apparently random for me to see a pattern without a test system.

---

### Post by tweedledee on 2011-09-05
> **rahuijts said:**
> Confirming ket1, I have a CLX-3175FN on Ubuntu 11.04



The new driver recognized my scanner over the network, but does not print correctly (wrong top margin). The legacy driver prints well, but does not find my scanner. Can I install both drivers at the same time?

Unfortunately that is not possible, because many files and locations are (and must be) identical for both versions.  I will try to package a version of the 3.00.65 driver that works with the new system, in the hopes that it splits the difference in a good way (and not break both parts).  However, I'm swamped at work now and it will be at least a week (maybe much more) before I get to it.

---

### Post by doublekey on 2011-09-06
Hello! I use a Monochrome Multifunction Printer Samsung-SCX4321 connected to the Ubuntu 11.04 machine with the  2.6.38-11-generic kernel and the samsungmfp-scanner-3.00.90-1 driver.
This device scans properly in Black&White or Line Art modes with the resolution up to 600 dpi
```

scanimage --mode "Black and White - Halftone" --resolution 600 --format=tiff -vvv -p > test.tiff
scanimage: value for --resolution is: 600
scanimage: scanning image of size 4960x7015 pixels at 1 bits/pixel
scanimage: acquiring gray frame
scanimage: read 4349300 bytes in total
Closing device
Calling sane_exit
scanimage: finished

```But, if I attempt to scan in the Grayscale mode (or Color mode) even with 75 dpi resolution, the device moves the scanning head and then reboots my machine.
```

scanimage --mode "Grayscale - 256 Levels" --resolution 75 --format=tiff -vvv -p > test.tiff
scanimage: value for --resolution is: 75
scanimage: scanning image of size 620x876 pixels at 8 bits/pixel
scanimage: acquiring gray frame
<-- reboot after ~ 5 secs

```syslog doesn't show anything.
If I pick the -B1 parameter the reboot doesn't occur
```

scanimage --mode "Grayscale - 256 Levels" --resolution 75 --format=tiff -vvv -p -B1 > test.tiff
scanimage: value for --resolution is: 75
scanimage: scanning image of size 620x876 pixels at 8 bits/pixel
scanimage: acquiring gray frame
scanimage: min/max graylevel value = 112/255
scanimage: read 543120 bytes in total
Closing device
Calling sane_exit
scanimage: finished

``` but it still happens with 100 dpi and higher resolutions.
```

scanimage --mode "Grayscale - 256 Levels" --resolution 100 --format=tiff -vvv -p -B1 > test.tiff
scanimage: value for --resolution is: 100
scanimage: scanning image of size 826x1169 pixels at 8 bits/pixel
scanimage: acquiring gray frame
<-- reboot after ~ 5 secs

```
and with SANE_DEBUG_XEROX_MFP=4 and SANE_DEBUG_DLL=4
```

scanimage --mode "Grayscale - 256 Levels" --resolution 100 --format=tiff -vvv -p -B1 > test.tiff
[sanei_debug] Setting debug level of xerox_mfp to 4.
[xerox_mfp] sane_init: Xerox backend (build 12), version != null, authorize != null
[xerox_mfp] sane_xerox_mfp_get_devices: 0xbf8965cc, 0
scanimage: value for --resolution is: 100
scanimage: scanning image of size 826x1169 pixels at 8 bits/pixel
scanimage: acquiring gray frame
<-- reboot after ~ 5 secs

```
I changed an USB port I attached the device, but it haven't solved the problem.
How can I fix this this problem?

---

### Post by hakan_nilsson on 2011-09-17
> **tweedledee said:**
> Unfortunately that is not possible, because many files and locations are (and must be) identical for both versions.  I will try to package a version of the 3.00.65 driver that works with the new system, in the hopes that it splits the difference in a good way (and not break both parts).  However, I'm swamped at work now and it will be at least a week (maybe much more) before I get to it.

Thanks for all the great work!

I just want to report my findings:

I'm on a 64-bit Ubuntu 10.04, printing and scanning with a Samsung CLX-3185FW. I experience the same things as many others, i.e. top margin disappears when using the new driver. With the new driver, scanning and toner level works. With the legacy driver, the printing works but not the scanning (did not check toner level).

While trying to make it work with the new driver, I realized that even if I changed the format to A4, which is the paper size I use, the printer complained that it was not the correct paper size. Perhaps that is some useful information.

Also, adding a header with any character will push down the rest of the text, but not if I make that character white, so there is some automatic cropping of the top margin going on.

Best regards,
Håkan

---

### Post by doublekey on 2011-09-20
The problem was solved after a couple of spoiled capacitors were resoldered on the motherboard.

---

### Post by tweedledee on 2011-09-24
Another update to the repository.  I fixed a couple of very minor issues, including the need for the /opt/smfp-common/ directory (I think - there's a very small chance someone may run into installation problems with the samsungfmp-network package, in which case please post here).

I also added the samsungmfp-driver-3.00.65 package, which will work in place of the samsungmfp-driver and samsungmfp-driver-legacy packages.  Those who are having trouble with the latest driver can revert to that version if the legacy version doesn't work well.  I don't know if it will help or not with scanning and ink level issues.

---

### Post by WolverineFan on 2011-09-24
Thanks!  I can confirm that switching to the samsungmfp-driver-3.00.65 package fixes the top margin white space issue (for me anyway).

---

### Post by murcielago75 on 2011-09-25
Hi

this is my first post.

I just switched to Ubuntu** 11.04** from WinXP. Absolute beginner in Ubuntu (and Linux).

I like Ubuntu and accept the fact that there is a slow but steady learning curve.

I do have one big issue: 
my multi function printer (samsung scx4828 FN) won't work with Ubuntu and I might have to revert to Windows just because of this (i didn't make any partition, I installed ubuntu over XP :-))  

My system is:  2.6.38-11-generic-pae #50-Ubuntu SMP Mon Sep 12 22:21:04 UTC 2011 i686 i686 i386 GNU/Linux

My printer is: Samsung Scx 4828fn

There appear to be new  (as of Aug 31st 2011) Linux drivers for this printer on the samsung website: 

[http://www.samsung.com/ca/consumer/office/printer-multifunction/monochrome-multifunction/SCX-4828FN/XAA/index.idx?pagetype=prd_detail&tab=support](http://www.samsung.com/ca/consumer/office/printer-multifunction/monochrome-multifunction/SCX-4828FN/XAA/index.idx?pagetype=prd_detail&tab=support)

so I tried to install these

I was able to get the printer to work with the unified driver downloaded from samsung.com. but just in printing mode.  Ubuntu wouldn't recognize the scanner capabilities of the MFP. I read this thread and decided to reinstall Ubuntu from scratch. So now I have no drivers. 

I am hoping you could give me some step by step advice on how to  get the printer to regain it's full functionality with Ubuntu. 

Please keep in mind that I am an absolute newbie who hardly knows what the terminal is.:oops:

I don't know how to apply the stuff that's in the repository. 

I feel hopeless but am willing to learn. 

Am I better off buying a new (HP) MF printer? Do you think an absolute begnner in Linux can get his samsung MFP to work correctly?  

Any advice would be appreciated.

[-o<

M.

---

### Post by tweedledee on 2011-09-25
> **murcielago75 said:**
> There appear to be new  (as of Aug 31st 2011) Linux drivers for this printer on the samsung website:

The dates on the Samsung website cannot be trusted.  The driver they are providing for your printer is almost 2 years old, and corresponds to my samsungmfp-driver-3.00.65 package.

> **murcielago75 said:**
> I am hoping you could give me some step by step advice on how to  get the printer to regain it's full functionality with Ubuntu. 

Please keep in mind that I am an absolute newbie who hardly knows what the terminal is.:oops:

I don't know how to apply the stuff that's in the repository. 

I feel hopeless but am willing to learn. 

Am I better off buying a new (HP) MF printer? Do you think an absolute begnner in Linux can get his samsung MFP to work correctly?  
Just try to work through the repository guide in the first post and the website, it is less intimidating than it looks when you actually go through it.  If you get stuck at a specific point, feel free to post, but those instructions have already been refined several times and nearly every question is answered.

As for a new printer, I've never had any problems with HP printers and Linux - printing has always worked without any tricks, but I've also never needed to try scanning/faxing with one.  I'd certainly suggest you try to get the repository solutions working with your current printer first.

---

### Post by murcielago75 on 2011-09-25
Miracle or beginners' luck? 

Anyway, I did it!  :p

I can currently state that my Samsung SCX 4828 FN both copies and SCANS on Ubuntu 11.04! 

The  package that worked for my printer  (SCX 4828FN) was:

**samsungmfp-configurator-qt4 **

I had previously installed the   samsungmfp-driver-3.00.65 but it only worked for printing. 

I now have regained  multifunction printer functionality and can go on exploring Ubuntu without having to go back to Windows for printing. 

Thanks Tweedledee

M

---

### Post by pkg9991 on 2011-09-25
nice tutorial.. thank u

---

### Post by hdel on 2011-09-29
Hello,
I am on Debian squeeze 2.6.32-5-amd64
libc6 2.11.2-10
samsung 3.00.90-2 from [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/)
Having a french CLX-3175N
One year ago on other Debian all work fine.:)

I install this new one and can't scan.
with or without sudo the command /opt/Samsung/mfp/bin/...
give the same result:
pere@dbh:/opt/Samsung/mfp/bin$ ./netdiscovery --all
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
ip: 192.168.128.210 slp: 0,0,0,0 snmp: 0,0,0 dsc: " [CLX-3175] Direction"
# Total 1 printers found, 5s elapsed
pere@dbh:/opt/Samsung/mfp/bin$ ./netdiscovery --all --scanner
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
# Total 0 scanners found, 5s elapsed
:(
I try to install the legacy one but are only links for the 3.00.90-2 (debian synaptic):confused:
I try to install manually after downloading them from [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) repository but all claim for non legacy package for install so I can see the legacy only install : /. when viewing in synaptic.](*,)

So now Idon't know what I ca do. (Iread the entire post and test when possible without success) 
Perhaps I can add I am thinking to update squeeze -> to wheezy (unstable Debian.
Thanks for all you made for us
:)

---

### Post by Metal Hed on 2011-09-29
I am trying to get the unified driver and I can't seem to make any of it work? It's for a samsung scx 4828 fn. I thought I was following the directions proper, but every time I've tried it in the terminal it says no such file exists?   and in synaptic package manager it says the same thing? I'm ripping my hair out with this, I've made other devises run, but this i'm stumped on

Can any one explain what I'm doing wrong? Something in the instructions isn't clicking in my head

thanks

---

### Post by arcturus.red on 2011-09-29
Um, help? 

Using a Samsung SCX-3201 on Ubuntu 11.04. Got samsungmfp-data, samsungmfp-scanner, samsungmfp-driver and samsung-mfp-network installed from bchemnet. Scanner's working fine, but the printer doesn't work at all. 

Went through the recommendations on the [Troubleshooting page]("http://www.bchemnet.com/suldr/printing.html"), but they don't seem to work.

So.... when I try to print something, I get the message "There was a problem processing document 'whatever' (Job 2x)"

The error log is attached. (Split into parts because of filesize limits.)

Weird thing is, if the printer's idling, it goes into ready mode every time I try to print something. I still get the error, though.

If I try to print a test page, the message I get is "There was an error during the CUPS operation: 'client-error-document-format-not-supported'."

And when I run a self-test, it prints
```

%!
userdict dup(\004)cvn{}put (\004\004)cvn{}put

% You are using the wrong driver for your printer!
0 setgray
2 setlinewidth
initclip newpath clippath gsave stroke grestore pathbbox
exch pop exch pop exch 9 add exch 9 sub moveto
/Courier findfont 12 scalefont setfont
0 -12 rmoveto gsave product show grestore
0 -12 rmoveto gsave version show ( ) show revision 20 string cvs show grestore
0 -12 rmoveto gsave serialnumber 20 string cvs show grestore
showpage
&#9830;

```I checked the printer properties, and it's associated with the correct driver (SCX 3200 series). 

So.... what the hell is going wrong?

<Changing mode...>
> **Metal Hed said:**
> I thought I was following the directions  proper, but every time I've tried it in the terminal it says no such  file exists? 
Which step are you stuck at? As in, what are you typing into the terminal?

---

### Post by Metal Hed on 2011-09-30
> **arcturus.red said:**
> Um, help? 

Using a Samsung SCX-3201 on Ubuntu 11.04. Got samsungmfp-data, samsungmfp-scanner, samsungmfp-driver and samsung-mfp-network installed from bchemnet. Scanner's working fine, but the printer doesn't work at all. 

Went through the recommendations on the [Troubleshooting page]("http://www.bchemnet.com/suldr/printing.html"), but they don't seem to work.

So.... when I try to print something, I get the message "There was a problem processing document 'whatever' (Job 2x)"

The error log is attached. (Split into parts because of filesize limits.)

Weird thing is, if the printer's idling, it goes into ready mode every time I try to print something. I still get the error, though.

If I try to print a test page, the message I get is "There was an error during the CUPS operation: 'client-error-document-format-not-supported'."

And when I run a self-test, it prints
```

%!
userdict dup(\004)cvn{}put (\004\004)cvn{}put

% You are using the wrong driver for your printer!
0 setgray
2 setlinewidth
initclip newpath clippath gsave stroke grestore pathbbox
exch pop exch pop exch 9 add exch 9 sub moveto
/Courier findfont 12 scalefont setfont
0 -12 rmoveto gsave product show grestore
0 -12 rmoveto gsave version show ( ) show revision 20 string cvs show grestore
0 -12 rmoveto gsave serialnumber 20 string cvs show grestore
showpage
&#9830;

```I checked the printer properties, and it's associated with the correct driver (SCX 3200 series). 

So.... what the hell is going wrong?

<Changing mode...>

Which step are you stuck at? As in, what are you typing into the terminal?
I put in the code that you have in step 1 in the terminal using sudo, it says no such command. Also tried doing it manually in the repository via synaptic it puts the code in the repository but when I try then to get the right key it won't allow anything to happen, I've tried a bunch of times now and nothing seems to work, f'n frustrating. Hope you can help

---

### Post by tweedledee on 2011-09-30
> **hdel said:**
> I try to install the legacy one but are only links for the 3.00.90-2 (debian synaptic):confused:
I try to install manually after downloading them from [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) repository but all claim for non legacy package for install so I can see the legacy only install : /. when viewing in synaptic.](*,)

So now Idon't know what I ca do. (Iread the entire post and test when possible without success) 
Perhaps I can add I am thinking to update squeeze -> to wheezy (unstable Debian.
Thanks for all you made for us
:)

The package that is relevant to this is probably the samsungmfp-network(-legacy) one.  The -legacy version is tied to the libc version.  I am not aware of any issues with the 2.11 libc in Debian Squeeze, although there have been other difficulties with it.  You can try to force-install (using dpk on a command line) the samsungmfp-network-legacy package, even though it will complain that the dependencies are not met, and see if that helps.  You could also just extract the netdiscovery tool out of the -legacy package and run it manual (in the correct path in /opt) and see if it works, or if the 32-bit version of the -legacy does (assuming you have installed the ia32-libs package).  If one of those works, you can use it as a short term solution until I figure out what's going on.  Otherwise all I can say is that it works in my Squeeze virtual machine test system (I run Testing), but I don't have a scanner to check with.

---

### Post by tweedledee on 2011-09-30
> **arcturus.red said:**
> Um, help? 

Using a Samsung SCX-3201 on Ubuntu 11.04. Got samsungmfp-data, samsungmfp-scanner, samsungmfp-driver and samsung-mfp-network installed from bchemnet. Scanner's working fine, but the printer doesn't work at all. 

You tried alternate versions of the -driver package?  Although the error suggests the problem may be an issue with the ppd, in which case you might want to try the legacy data package (which requires the legacy driver unless you want to try force-installing it - there is a reason that I decided to make the newer drivers depend only on the newer data package, although what it was escapes me at the moment).

---

### Post by tweedledee on 2011-09-30
> **Metal Hed said:**
> I put in the code that you have in step 1 in the terminal using sudo, it says no such command. Also tried doing it manually in the repository via synaptic it puts the code in the repository but when I try then to get the right key it won't allow anything to happen, I've tried a bunch of times now and nothing seems to work, f'n frustrating. Hope you can help

Do you mean the line that begins with "deb"?  If so, that is not supposed to be executed as a command, you need to edit the sources.list file and add that line to the file.

---

### Post by hdel on 2011-10-01
I tried this solutions too.
Netdiscovery tool from 3.00.9; legacy (suldr); from samsung.com in 32bits (error libnss..) but same output and 64 bit.
./netdiscovery --all --scanner always return 0 scanner found!
To be sure I test with a windows XP and network scanning works fine.
I am now on squeeze and kernel 3.1-rc7 (the nouveau xorg driver don't function in 2.6.32.x).
Same tests, same results!

> **tweedledee said:**
> The package that is relevant to this is probably the samsungmfp-network(-legacy) one.  The -legacy version is tied to the libc version.  I am not aware of any issues with the 2.11 libc in Debian Squeeze, although there have been other difficulties with it.  You can try to force-install (using dpk on a command line) the samsungmfp-network-legacy package, even though it will complain that the dependencies are not met, and see if that helps.  You could also just extract the netdiscovery tool out of the -legacy package and run it manual (in the correct path in /opt) and see if it works, or if the 32-bit version of the -legacy does (assuming you have installed the ia32-libs package).  If one of those works, you can use it as a short term solution until I figure out what's going on.  Otherwise all I can say is that it works in my Squeeze virtual machine test system (I run Testing), but I don't have a scanner to check with.

---

### Post by arcturus.red on 2011-10-01
> **tweedledee said:**
> You tried alternate versions of the -driver package?  Although the error suggests the problem may be an issue with the ppd, in which case you might want to try the legacy data package (which requires the legacy driver unless you want to try force-installing it - there is a reason that I decided to make the newer drivers depend only on the newer data package, although what it was escapes me at the moment).

The legacy data package doesn't seem to support this particular model. (SCX 3200) 
The driver defaults to a generic PCL 5e Foomatic. 
And then I get the exact same errors when I try to print. ](*,)

**EDIT: **
Removed CUPS and then reinstalled it, and now printing works fine. :grin:
.... Well, at least for documents. I get random gibberish when I try to print pictures, but that's probably Shotwell's fault.

---

### Post by tweedledee on 2011-10-01
> **hdel said:**
> I tried this solutions too.
Netdiscovery tool from 3.00.9; legacy (suldr); from samsung.com in 32bits (error libnss..) but same output and 64 bit.
./netdiscovery --all --scanner always return 0 scanner found!
To be sure I test with a windows XP and network scanning works fine.
I am now on squeeze and kernel 3.1-rc7 (the nouveau xorg driver don't function in 2.6.32.x).
Same tests, same results!

Please post the output file from:
```
strace ./netdiscovery --all --scanner > ~/strace-out.txt
```

The other thing you can try is to create an /opt/smpf-common/lib64 folder and cp /usr/lib/libnetsnmp.so.10.* into it, then try netdiscovery again.  (This assumes you are not using any of the other work-arounds at present.)

---

### Post by tweedledee on 2011-10-01
> **arcturus.red said:**
> The legacy data package doesn't seem to support this particular model. (SCX 3200) 
The driver defaults to a generic PCL 5e Foomatic. 
And then I get the exact same errors when I try to print. ](*,)

If you are getting the same errors with the Foomatic driver, then the issue is not with the Samsung driver or packages.  You might want to try re-installing CUPS and/or the various foo* packages to see if something has been corrupted.

---

### Post by arcturus.red on 2011-10-01
> **tweedledee said:**
> If you are getting the same errors with the Foomatic driver, then the issue is not with the Samsung driver or packages.  You might want to try re-installing CUPS and/or the various foo* packages to see if something has been corrupted.

Ah, didn't see this comment before making my edit. 
Anyhow, yeah, it was CUPS. Reinstalled it, and everything's working fine now. (... well, almost. But images printing as gibberish is a problem for another day.)

Thanks for the help. :)

---

### Post by hdel on 2011-10-01
> **tweedledee said:**
> Please post the output file from:
```
strace ./netdiscovery --all --scanner > ~/strace-out.txt
```The other thing you can try is to create an /opt/smpf-common/lib64 folder and cp /usr/lib/libnetsnmp.so.10.* into it, then try netdiscovery again.  (This assumes you are not using any of the other work-arounds at present.)

I uninstall all related packages to samsung (suldr) nor cups and libs too. Then reboot and reinstall.
test -> same
create /opt/smpf-common/lib64 and cp /usr/lib/libnetsnmp.so.10.*
test -> same

~/strace-out.txt only contain:
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
# Total 0 scanners found, 5s elapsed

I also have a copy of the terminal but it's 240Kb

---

### Post by tweedledee on 2011-10-01
> **hdel said:**
> I also have a copy of the terminal but it's 240Kb

That's what I actually need to see if you can upload it as a file.  I always forget that strace output needs "2>" not ">" for the useful bits.

---

### Post by hdel on 2011-10-01
> **tweedledee said:**
> That's what I actually need to see if you can upload it as a file.  I always forget that strace output needs "2>" not ">" for the useful bits.

The >> only add new trace at the end of existant strace-out.txt.

Here a link I upload : [http://dl.free.fr/l8lwHMk43](http://dl.free.fr/l8lwHMk43) 

When I reinstall all related packages it claims that kernel haven't multicast build-in; perhaps?

Thank's

---

### Post by tweedledee on 2011-10-01
> **hdel said:**
> The >> only add new trace at the end of existant strace-out.txt.

Here a link I upload : [http://dl.free.fr/l8lwHMk43](http://dl.free.fr/l8lwHMk43) 

When I reinstall all related packages it claims that kernel haven't multicast build-in; perhaps?

Thank's

I actually meant a literal "2>" not ">>" - the "2" means stderr instead of stdout, because the strace output goes through the error output rather than the normal user output.

However, I don't see anything obvious in the strace.  I don't think multicast support is the issue, but some setting that results in dropping UDP packets (and therefore is possibly related) could well be the issue.  What I'm not sure about is why you would be using a Debian kernel that could cause these problems but I (and others) don't see them.  Perhaps you have a strange firewall rule, something odd in syscntl.conf, or some other system setting interfering with UDP?  Or maybe a router setting has changed?

I won't have time to look at this more for a week, but please post if you learn anything more and I'll work on it when I can if it hasn't been resolved.

---

### Post by hdel on 2011-10-02
> **tweedledee said:**
> I 
  What I'm not sure about is why you would be using a Debian kernel that could cause these problems but I (and others) don't see them.  Perhaps you have a strange firewall rule, something odd in syscntl.conf, or some other system setting interfering with UDP?  Or maybe a router setting has changed?

I won't have time to look at this more for a week, but please post if you learn anything more and I'll work on it when I can if it hasn't been resolved.

The 2.6.32 kernel have errors with  xorg-nouveau and falback with fbdev one, so try 2.6.38.xx and 2.6.39.xx and at least 3.1-rc7 and the same.

You graciously help me, I'll can't complain because your full for a week or a month.
At the moment I use an attached guillemot scsi scanner as a workaround.

I had put a network cross cable directly between my computer and the printer (CLX-3175N french one) and «strace ./netdiscovery --all 2> output.txt» give the same thing and no scanner found!

---

### Post by Hans9 on 2011-10-02
Hi, I have just bought and installed CLX-3185FW printer. I installed drivers using guide in the firtst post (samsungmfp-data, driver and scanner).

During adding a network printer I have written printer IP in the Host field (I have set printer IP on another comp with win) and it showed up three printers: CLX-3185 IPP via DNS-SD, CLX-3185 LPD via DNS-SD and JetDirect. I understand that IPP and LPD are protocols, but what's the diference, which one should I use?
I have tried to use IPP and so far it worked (well, test page worked to be exact, I haven't printed anything else since I'm not at home.  I will try scanning next weekend. ). And also what is JetDirect? Does it have something to do with ad-hoc mode?
I am connecting my printer through WiFi router with Static IP.

I am using Ubuntu 10.04LTS

And one last question - What's the difference between Driver and Driver-legacy?
Thanks guys.

---

### Post by Metal Hed on 2011-10-02
> **tweedledee said:**
> Do you mean the line that begins with "deb"?  If so, that is not supposed to be executed as a command, you need to edit the sources.list file and add that line to the file.
Yeah I thought I did that? Unless I have to go right into the source file and add the line right in it? But I thought that was done in synaptic- repository? PS thanks for walking me through it, my folks will be stoked once they get their scanner working heh

---

### Post by hdel on 2011-10-02
> **Hans9 said:**
> 

I understand that IPP and LPD are protocols, but what's the diference, which one should I use?
And also what is JetDirect? Does it have something to do with ad-hoc mode?

Thanks guys.

LPD is a daemon formaly you print in LPR mode that is the «historical» way to print from sixties.
IPP is more recent way, but for these two (if my memory is good) you send  your jobs in a queue so you can administr the rights for printing,  suspend...
You can use one or other, the only difference I had seen was the speed  the job gone on the printer on great networks (more often LPR speedy  than IPP) 

JetDirect
 Not sure but seem to be the same than «direct» for printer/copieur,  the job is printed directly, bypassing the queues without waiting and directly (must be) after the job  that actualy print out.

---

### Post by rlar on 2011-10-08
Hello,

  Running debian I had trouble to find the scanner of a CLX-3185FW via ethernet.
  Pressing the scanner button of the "Samsung Unified Printer Configurator"
       didn't show anything.
  Digging around I've found the following issue:
       /opt/Samsung/mfp/bin/netdiscovery --all --scanner
  responds with
    # Network printers discovery utility
    # Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
    # Total 0 scanners found, 5s elapsed
  
Running strace revealed the program executes itself several times with varying
       command lines to try different strategies to discover devices.
  One of them is
       /opt/Samsung/mfp/bin/netdiscovery -s --snmp
  and this one responds with
    # Mode snmp
    # ERROR: snmp_send failed, Network is unreachable
    # Network printers discovery utility
    # Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
    # Total 0 printers found, 0s elapsed
  
Using strace on this revealed a
  udp sendmsg()
   call to
         port 161 (snmp) and ip-addr 255.255.255.255
   and linux responds with
  ENETUNREACH (Network is unreachable)

  I guess, broadcasting to 255.255.255.255 is a bit too much,
  and seems to be disallowed.
    
  The following work around is possible though:
  route add -host 255.255.255.255 dev eth0
   
  With this 
   /opt/Samsung/mfp/bin/netdiscovery --all --scanner
  is successful for me,
and scanimage -L, xsane, and "Samsung Unified Printer Configurator"
       can all find this scanner.

  Cheers,
   Robert

---

### Post by hdel on 2011-10-09
Hello,
Thanks **rlar** for your workaround, but not good for me.
I do  «strace          /opt/Samsung/mfp/bin/netdiscovery -s --snmp 2> fichier.txt»
It refer to :
libnss_db.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
*/snmp", 0x7fff46aab120) = -1 ENOENT (No such file or directory)

research in diverse directories but never locate them.

I try with Ubuntu 11.04 (Natty Narwhal) live CD and so «no scanners found».

Perhaps something missing in my install?

---

### Post by rlar on 2011-10-09
Hello hdel,

  I've no libnss_db as well here,  that is not the problem.

  further
    netdiscovery -s --snmp
  does not report a found scanner here either.

  its just one step necessary for netdiscovery --all --scanner
  which then executes internally a
    netdiscovery -I 192.168.42.13
  which is my ip addr of the printer.
  at the end of the day, it is
     netdiscovery --all --scanner
  which has to report the scanner
  
  thus, what does
     strace -f -s1000 -v -o /tmp/strace.log /opt/Samsung/mfp/bin/netdiscovery  --all --scanner
  report in /tmp/strace.log ?
  there should be some sendmsg() calls,
     which return  ENETUNREACH  when the route isn' set
  and
     which return the positive small integer message length, when the route is set.

  check
    route -n
  to report a route to the correct eth interface where the printer is attached.

  double check your printer has already a valid ip address, for example try
     firefox http:your-printers-ip-address
  
Robert

---

### Post by hdel on 2011-10-12
I could print from my Debian.
I could print and scan from windows sytem.

Due to the remarks from **rlar**,  **tweetledee **and echec from live CD, I reinitialised completly my Samsung CLX-3175N, get back informations (IP, French langage...).

Now all works fine, scan and print with Debian.

So, I think, was a software problem on the printer itself.

Now first thing I do if have a new troubleshoot to do!

And again a great «thank you to **tweedldee** and **rlar**».

---

### Post by vickoxy on 2011-10-14
Hi,
i downloaded original Samsung driver-it works fine under Ubuntu 11.04 (Gnome). Wireless Printing works also fine.

BUT, my desktop Computer with LXDE (Lubuntu 11.04, 32 bit) doesn´t work good with any drivers. I tried downloaded and from repository (from this thread) - but no way i can have wireless (even with USB) working well. I choose driver for 3180, and tested some others-the best result was grayscale printing, and once in color but with some stripes. 

So, what should i install to make Lubuntu 11.04 work well with Samsung CLX 3185 and to enable wireless color printing? 

Thanks

---

### Post by vickoxy on 2011-10-15
Yesterday i installed Ubuntu 11.04 64bit Gnome Edition on my computer and the drivers following instruction here:
[http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/)

The Wifi and Scanner work immediately, but the quality is not as good as it should be-gray, green and yellow are very blurry changing nuances in almost in every letter (the cartridge is new).

Tested on MacOS-everything works fine. Is there any way to adjust these colors ant to make output better?

---

### Post by tweedledee on 2011-10-16
> **Metal Hed said:**
> Yeah I thought I did that? Unless I have to go right into the source file and add the line right in it? But I thought that was done in synaptic- repository? PS thanks for walking me through it, my folks will be stoked once they get their scanner working heh

If you are still having trouble, enter a terminal and type:```
cat /etc/apt/soures.list
```then look for this line:> deb [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian extra

If that line is not present, you do not have the repository configured.  If you can confirm that you've at least gotten that far, please share any other errors you are receiving.

---

### Post by tweedledee on 2011-10-16
> **Hans9 said:**
> And one last question - What's the difference between Driver and Driver-legacy?

The details are on the website, but the short version is that driver-legacy is an older version of the driver, needed for people running old distributions and when the current driver doesn't work with newer distributions.

---

### Post by tweedledee on 2011-10-16
> **vickoxy said:**
> So, what should i install to make Lubuntu 11.04 work well with Samsung CLX 3185 and to enable wireless color printing? 

Whatever packages are missing in Lubuntu compared to Ubuntu that relate to wireless/networking?  This sounds like an issue with Lubuntu rather than the driver.  I would suggest either submitting a bug report on Launchpad or doing a comparison yourself of the packages in the two installations, probably looking for a library installed in Ubuntu but not Lubuntu.

---

### Post by tweedledee on 2011-10-16
> **vickoxy said:**
> Tested on MacOS-everything works fine. Is there any way to adjust these colors ant to make output better?

Depends on the printer type and driver version.  Some allow it in printer settings, but not many.  You can try a different version of the driver package.  Or try installing the printer as a closely related model.  There are also ways to manually edit the PPD files (a few months ago there was some discussion of that in this thread), but I haven't actually done so myself.  Quality of color output is incredibly variable and sensitive to what seem to be minor changes, unfortunately.

---

### Post by tweedledee on 2011-10-16
> **rlar said:**
>   The following work around is possible though:
  route add -host 255.255.255.255 dev eth0
   

Good to know.  I will add that to the website as a possible solution the next time I update it.

---

### Post by tweedledee on 2011-10-16
I'm losing track of what problems have been resolved and what haven't with the new driver.  If I did not just reply to one of your messages and you are having trouble printing/scanning, please indicate that in a new post.  I still don't have much time to troubleshoot, but there's a reasonable chance that next weekend I will have some time to work on issues.

---

### Post by neel.d on 2011-10-16
Thanks a ton tweedledee!

I recently bought Samsung CLX-3185FN and your drivers worked like a charm! I got printing and scanning working over network on my 2 ubuntu boxes: one with 10.04 and one with 10.10

I just installed the package "menu", "acl", "xsane", "libsane-extras" and from then it was really easy to set up the printer and scanner over the network using Samsung Unified Driver Configurator.

Thanks again.. :)

P.S. I forgot to mention that after installing the packages above, I installed the drivers from your repository and after that everything was good..

---

### Post by actitudes on 2011-10-17
Bonjour,

sorry for my english. If someone has problem with clx3185 scanner and ubuntu 11.10 or debian wheezy (scanner not recognized), try this.

[http://forum.ubuntu-fr.org/viewtopic.php?id=632571](http://forum.ubuntu-fr.org/viewtopic.php?id=632571)

In
 /etc/sane.d/xerox_mfp.conf       add

#Samsung CLX-3185FW
usb 0x04e8 0x343d


and in :       /lib/udev/rules.d/40-libsane.rules     add


# Samsung CLX-3185FW
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="343d", ENV{libsane_matched}="yes"

---

### Post by etsah57 on 2011-10-17
Aaaaaahhhhhhh!
Updated to the latest version of Ubuntu (11.10) and the printer has stopped working.
Tried to follow the same patten as before, but the system is different and I can't follow it exactly. 
In the Synaptic package manage there is the file: samsungmfp-driver, but  it is not ticked. I can't tick it, but when I right click on the name I  have the option to mark for installation, or mark for deletion. 
When I click on Mark for installation I get this message:
Package samsungmfp-driver has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and  never uploaded, has been obsoleted or is not available with the contents  of sources.list
The other file: samsungmfp-data is not there at all
When I go into the dashboard, system, printing. The printer is there. It has both a green tick on it and a red exclamation mark.
When I right click properties, under Printer State: it says: Idle - File  "/usr/lib/cups/filter/rastertosamsungsplc" not available: No such file  or directory

What do I do?
Please

---

### Post by hdel on 2011-10-18
> **etsah57 said:**
> Aaaaaahhhhhhh!
Updated to the latest version of Ubuntu (11.10) and the printer has stopped working.
Tried to follow the same patten as before, but the system is different and I can't follow it exactly. 
In the Synaptic package manage there is the file: samsungmfp-driver, but  it is not ticked. I can't tick it, but when I right click on the name I  have the option to mark for installation, or mark for deletion. 
When I click on Mark for installation I get this message:
Package samsungmfp-driver has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and  never uploaded, has been obsoleted or is not available with the contents  of sources.list
The other file: samsungmfp-data is not there at all
When I go into the dashboard, system, printing. The printer is there. It has both a green tick on it and a red exclamation mark.
When I right click properties, under Printer State: it says: Idle - File  "/usr/lib/cups/filter/rastertosamsungsplc" not available: No such file  or directory

What do I do?
Please

Is «suldr» repository always mark on ?

---

### Post by etsah57 on 2011-10-18
Is «suldr» repository always mark on ?
Sorry, I am a novice, what is a <<suldr>> mark?

---

### Post by hdel on 2011-10-19
> **etsah57 said:**
> Is «suldr» repository always mark on ?
Sorry, I am a novice, what is a <<suldr>> mark?

Sorry,

before in the thread someone give it.
Go to [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) and see if you have all good.

---

### Post by tweedledee on 2011-10-19
> **actitudes said:**
> If someone has problem with clx3185 scanner and ubuntu 11.10 or debian wheezy (scanner not recognized), try this.

I'll include this in the troubleshooting.

---

### Post by tweedledee on 2011-10-19
> **etsah57 said:**
> What do I do?
Please

As hdel said, the error probably means that the suldr repository has been deactivated on your system.  In synaptic, it probably does not have a check mark to indicate being in use if you check the list of repositories, or (equivalently) in /etc/apt/sources.list it has been commented out with a "#".  Ubuntu updates sometimes change the active states of repositories.

If that's not the problem, just try to add it as a new repository again from the beginning.

---

### Post by okkadiroglu on 2011-10-20
How about clx-2160? After upgrading to 11.10 I had to do all the things I did last year. Printer works but scanner is not recognized by the software (Xsane, simple-scan). I tried Samsung but they are not knowledgeable in Linux. I did what **actitudes **said in message #813 but nothing happened. Out of desperation I used [SIZE="1"]#Samsung CLX-3185FW
usb 0x04e8 0x343d[/SIZE] for clx-2160. Is this correct if not where can I find the correct one.

---

### Post by hdel on 2011-10-20
> **okkadiroglu said:**
> How about clx-2160? After upgrading to 11.10 I had to do all the things I did last year. Printer works but scanner is not recognized by the software (Xsane, simple-scan). I tried Samsung but they are not knowledgeable in Linux. I did what **actitudes **said in message #813 but nothing happened. Out of desperation I used [SIZE=1]#Samsung CLX-3185FW
usb 0x04e8 0x343d[/SIZE] for clx-2160. Is this correct if not where can I find the correct one.

Hello,
A way to explore, see my #803, was ethernet scanner problem but... 
I spend several days for software hardware malfunction.

---

### Post by milandjupovac on 2011-10-20
After upgrade to 11.10 version of Ubuntu my scanner on samsung SCX-4521F doesn't work. I have used gscan2pdf program for scnnning of documents in pdf format and now shows message ''No device found''. Also I can not use printer.

Please help.

---

### Post by dek007 on 2011-10-21
Same problem. After upgrade to 11.10 version of Xubuntu scanner on Samsung SCX-4100 doesn't work. Simple Scan shows message ''No device found''. Printer work fine at same time.
P.S. Sorry for my english.

---

### Post by Artorius89 on 2011-10-21
> **milandjupovac said:**
> After upgrade to 11.10 version of Ubuntu my scanner on samsung SCX-4521F doesn't work. I have used gscan2pdf program for scnnning of documents in pdf format and now shows message ''No device found''. Also I can not use printer.

Please help.

I have a similar problem with this same device. My Samsung SCX-4521F multifunction printer was working perfectly under Ubuntu and Lubuntu 11.04, but now, after upgrading (on both machines) to Lubuntu 11.10, the scanner doesn't work anymore: *Simple Scan* and *gscan2pdf* report "No device found". (The printer, on the other hand, didn't stop working).
I have followed the troubleshooting on tweedledee's website, but none of the suggestions helped.
The *sane-find-scanner* command seems to recognize the device, as it reports:
```
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04e8 [Samsung], product=0x3419 [SCX-4x21 Series]) at libusb:002:002
found USB scanner (vendor=0x0402, product=0x5602) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```
I have no clue why the upgrade should have broken what was working perfectly... :(
I hope somebody can help.

---

### Post by kazeevn on 2011-10-21
Hello. I've run into the problem with SCX-3200 myself and that's how it has just been solved:
I've manually added my device to the list of supported:
```

echo "usb 0x04e8 0x3441" >> /etc/sane.d/xerox_mfp.conf

```After that it worked. Here you can find additional info: [URL="http://www.sane-project.org/man/sane-xerox_mfp.5.html"]http://www.sane-project.org/man/sane-xerox_mfp.5.html. 
[/URL] 
P. S.
Lots of thanks to [tweedledee]("http://ubuntuforums.org/member.php?u=207037") for packaging all the stuff.

---

### Post by yahs on 2011-10-21
Just for information regarding Ubuntu 11.10.
I have spent some time testing my Samsung scx-4500w wireless mfp with ubuntu 11.10
I always do a clean install rather than update and a clean install after each test.
Both Unified Driver driver packages (3.00.65 and 3.00.90) downloaded from samsung, installed and worked perfectly - scanning and printing as normal.
Then enabled the repository and installed necessary drivers - again both printing and scanning work as normal.
I can scan from libreoffice, picasa, simple scan and xsane.

---

### Post by okkadiroglu on 2011-10-22
Hi,

I did it! Thanks all for the help.

I installed, 

*samsungmfp-data, samsungmf--configurator-data, samsungmfdriver, samsungmfp-scanner* from* [http://ww.bchemnet.com/suldr](http://ww.bchemnet.com/suldr) debian extra.* 

Also, my user is in the *lp* and *saned* groups. After starting the CLX-2160, responce to the *lsusb* is:

*Bus 001 Device 007: ID 04e8:3425 Samsung Electronics Co., Ltd*

and for

*sane-find-scanner*

 I got:

[I]found USB scanner (vendor=0x0ac8, product=0x303b) at libusb:002:003
found USB scanner (vendor=0x04e8 [Samsung Electronics Co., Ltd.], product=0x3425 [CLX-216x Series]) at libusb:001:007[/I]

Inserting vendor and product numbers for CLX-2160 listed above into 

/ect/sane.d/xerox_mfp.conf 

I was able to scan.

Many thanks for all those helpers.

Bast Regards

---

### Post by Artorius89 on 2011-10-22
> **kazeevn said:**
> I've manually added my device to the list of supported:
```

echo "usb 0x04e8 0x3441" >> /etc/sane.d/xerox_mfp.conf

```
Thank you for the suggestion, but unfortunately this didn't work, in my case, as *Simple Scan*, *scanimage -L* and *gscan2pdf* still report finding no device.
Also, a clean install instead of an upgrade makes no difference in my case, as I have tried with both. (And I am part of the mentioned *lp*, *lpadmin*, *saned* and *scanner* groups).
I hope somebody has a clue. It had been working fine before the upgrade.

---

### Post by hdel on 2011-10-22
> **Artorius89 said:**
> T
Also, a clean install instead of an upgrade makes no difference in my case, as I have tried with both. (And I am part of the mentioned *lp*, *lpadmin*, *saned* and *scanner* groups).


What happen if you use a LiveCD? If you can't scan with, I suggest you initialize your Samsung product completly and configure for your need.

---

### Post by milandjupovac on 2011-10-22
> **Artorius89 said:**
> Thank you for the suggestion, but unfortunately this didn't work, in my case, as *Simple Scan*, *scanimage -L* and *gscan2pdf* still report finding no device.
Also, a clean install instead of an upgrade makes no difference in my case, as I have tried with both. (And I am part of the mentioned *lp*, *lpadmin*, *saned* and *scanner* groups).
I hope somebody has a clue. It had been working fine before the upgrade.

I have done all this and still there is not chance to run scanner on my Samsung SCX-4521F, printer now works fine.
 
 Does anybody has other recommendation?

---

### Post by Artorius89 on 2011-10-23
> **hdel said:**
> What happen if you use a LiveCD? If you can't scan with, I suggest you initialize your Samsung product completly and configure for your need.
I'm sorry, I don't understand what's meant by "initializing the product completely". The LiveCD doesn't help.
Thank you, anyway.

---

### Post by hdel on 2011-10-24
> **Artorius89 said:**
> I'm sorry, I don't understand what's meant by "initializing the product completely". The LiveCD doesn't help.
Thank you, anyway.

I am a french and I try to translate.
In a web navigator I type my printer address, I arrive on the Samsung «SyncThru Service» page.
Under «Machine settings» and «Network settings» I have on the left hand a line with «reset» I go in and clear all settings.
I switch off then on the printer.
For me it have now a different IP address so I first renew the one I want. And then with  «SyncThru Service», I put all my rules for the printer. After that all was good. (see 803) Like you nothing saw my scanner before that.

---

### Post by Artorius89 on 2011-10-27
I haven't been able to find my printer's IP address. Could you please tell me how you did it?
> **hdel said:**
> I am a french and I try to translate.
Actually, I was not criticizing your wording; the reason why I hadn't understood is that I'm not as experienced as you.
Thank you for your suggestions.

---

### Post by hdel on 2011-10-28
> **Artorius89 said:**
> I haven't been able to find my printer's IP address. Could you please tell me how you did it?

Actually, I was not criticizing your wording; the reason why I hadn't understood is that I'm not as experienced as you.
Thank you for your suggestions.

HI,
Translation was bad, I never think you critic my wording. Only was to explain why it isn't always easy to understand me!...

I have a CLX-3175N, and on it I have a menu button with «copy config» --> ok --> cycling for «system config» --> ok --> Network --> ok --> TCP/IP --> ok  then you type in the network address you want ( be careful to enter all numbers 0123 and not 123; 4 groups of four)

But only for «SynchThru» services, if you don't scan by network.

---

### Post by Artorius89 on 2011-10-29
Thank you. Unfortunately the "Network" settings are not in my printer's menu.
I give up. I guess the only chance I have now is reverting to the old release (11.04). I hope that will work.

---

### Post by Artorius89 on 2011-10-29
Finally! It worked: I can confirm that going back to the 11.04 release solves the problem with the Samsung SCX-4521F scanner component. However, I doubt this can be called an *ultimate* solution, as one needs to stick to an older release that soon won't be supported anymore. But to the necessary purposes of my work this will do.
I thank again *hdel*, who kindly tried to help me.

---

### Post by sbz123 on 2011-10-31
I also recently updated to the 11.10 kernel and lost all of the functionality of the scanner. It would seem to me that for some reason the printer is recognized as being hooked up to the USB port but the system is looking for the scanner on the DEV/MFP4 and such ports. I got the configurator up and running and it recognizes the printer on usb://Samsung/etc but when you look at the port configurator all it shows is the DEV/mfp options and I am unable to access them in any way.
Ideas anyone?:(

---

### Post by vince68 on 2011-11-01
A case is open for the no scanner detection :

[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/879619?comments=all](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/879619?comments=all)

Hope that the fix come soon

---

### Post by Artorius89 on 2011-11-01
Thank you. I added my testimony.

---

### Post by murcielago75 on 2011-11-03
I had successfully gotten my Samsung SCX-4828FN to work both scanning and printing on 11.04  (thanks Tweedledee!)

Now I installed 11.10, and followed the procedure:

1)  deb [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian extra    (through  synaptic)

2) sudo wget -O - [http://www.bchemnet.com/suldr/suldr.gpg](http://www.bchemnet.com/suldr/suldr.gpg) | sudo apt-key add - (in terminal)

3) installed packages (same ones that worked on 11.04) in synaptic


But now, in 11.10, I can't make the scanner work any more. Only the printer works. 

I am wondering if Tweedledee or anyone else is aware of an issue with 10.11 and the samsung unified drivers not being able to access their scanning functions in 11.10.
Is it a bug in 11.10? Why isn't this procedure working any more for me?

---

### Post by tweedledee on 2011-11-05
> **murcielago75 said:**
> I am wondering if Tweedledee or anyone else is aware of an issue with 10.11 and the samsung unified drivers not being able to access their scanning functions in 11.10.
Is it a bug in 11.10? Why isn't this procedure working any more for me?

Aware, yes.  Know how to fix it, no.  It appears to be related to a sane and/or library version difference associated with the 11.10 upgrade, but I don't know which, and without a scanner myself to test it is far more time-consuming than I can manage right now to try to track down the differences between 11.10 and 11.04.

However, this thread in the Arch Linux forums may provide some ideas for interested parties to try, as the changes to 11.10 causing the problem are almost certainly the same as the Arch users are seeing: [https://bbs.archlinux.org/viewtopic.php?id=123934](https://bbs.archlinux.org/viewtopic.php?id=123934)

It's not immediately obvious to me what has and has not been working for people in that thread, so if anyone tries something about gets it to work, please share.  If the solution is something I can incorporate into my packages, I will do so.

---

### Post by yahs on 2011-11-07
Tweedledee,

For information.

I posted 2 weeks ago (#826).

11.10 works for me using SCX-4500w on a wireless network.

Just to check, I did a fresh install this evening. Downloaded v3.00.90 from Samsung and ran sudo ./install.sh from cdroot/Linux.
Printing and scanning from apps as mentioned before.

I'm now running 11.10 on both laptop and desktop without any apparent problems

---

### Post by vyvee on 2011-11-16
Scanner WORKS for me on Ubuntu 11.10!

I have a Xerox WorkCentre PE220, which functions just like a -Samsung SCX-4521F. I've debugged for a few hours and the scanner function finally works!

1) Install samsungmfp-scanner.
2) Now try this! => sudo modprobe usblp
3) You can use 'xsane' or 'Simple Scan' to test... does it work now? :KS
4) If it works, then it means that 'usblp', which has been blacklisted, is the key. To un-blacklist it,
a) modify /etc/modprobe.d/blacklist-cups-usblp.conf
b) Comment the line by prefixing with a '#':
     #blacklist usblp
After this step, you don't need to 'sudo modprobe usblp' after starting your machine.

Well, it works for me, but I'm not sure if it can help to solve scanner problems faced by you all. Share you experience here!

---

### Post by vyvee on 2011-11-16
> **vyvee said:**
> 4) If it works, then it means that 'usblp', which has been blacklisted, is the key. To un-blacklist it,
a) modify /etc/modprobe.d/blacklist-cups-usblp.conf
b) Comment the line by prefixing with a '#':
     #blacklist usblp
After this step, you don't need to 'sudo modprobe usblp' after starting your machine.


By the way, I found that
a) 'usblp' was NOT blacklisted in 11.04. And
b) It was indeed loaded in 11.04 when a scanner is plugged to the machine.
So 'usblp' is probably the key to make scanner work here!

---

### Post by vince68 on 2011-11-17
Thank you vyvee ! It works for, but I had to delete and re create my printer because after comment the module my printer didnt work. After the re creation of the printer it worked again.
I found this about this module  : [https://wiki.archlinux.org/index.php/CUPS#Blacklisting_usblp](https://wiki.archlinux.org/index.php/CUPS#Blacklisting_usblp)

I hope that this modification continue to work in the newer version of ubuntu.for the 11.10 it's ok.

---

### Post by piccoloprincipe on 2011-11-17
> **vince68 said:**
> Thank you vyvee ! It works for, but I had to delete and re create my printer because after comment the module my printer didnt work. After the re creation of the printer it worked again.
I found this about this module  : [https://wiki.archlinux.org/index.php/CUPS#Blacklisting_usblp](https://wiki.archlinux.org/index.php/CUPS#Blacklisting_usblp)

I hope that this modification continue to work in the newer version of ubuntu.for the 11.10 it's ok.

I have a Samsung SCX-3200: the same for me, I reinstalled the printer after unblacklisting and now both it and the scanner work.

---

### Post by murcielago75 on 2011-11-18
> **vyvee said:**
> Scanner WORKS for me on Ubuntu 11.10!

I have a Xerox WorkCentre PE220, which functions just like a -Samsung SCX-4521F. I've debugged for a few hours and the scanner function finally works!

1) Install samsungmfp-scanner.
2) Now try this! => sudo modprobe usblp
3) You can use 'xsane' or 'Simple Scan' to test... does it work now? :KS
4) If it works, then it means that 'usblp', which has been blacklisted, is the key. To un-blacklist it,
a) modify /etc/modprobe.d/blacklist-cups-usblp.conf
b) Comment the line by prefixing with a '#':
     #blacklist usblp
After this step, you don't need to 'sudo modprobe usblp' after starting your machine.

Well, it works for me, but I'm not sure if it can help to solve scanner problems faced by you all. Share you experience here!

Hi vyvee,

"sudo modprobe usblp"  works for me too (SCX 4828FN)! 
However, being no IT expert and quite new to Ubuntu, I don't understand exactly what you mean when you say "modify"  /etc/modprobe.d/blacklist-cups-usblp.conf 

*Where* and *how* is that done? 

in the terminal? 

If you could explain step by step how you did this modification I am confident I could get my scanning functions back without having to type "sudo modprobe usblp" every time

Thanks for sharing.

**UPDATE**

i was able to do it myself :twisted: and it WORKS!!! 

For other newbies in Ubuntu, I found the info here: 

[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190) 

The thread in question is referred to a different printer but the work around is the same. Just type  :

$ sudo nano /etc/modprobe.d/blacklist-cups-usblp.conf

and then type # in front of "blacklist usblp" 

delete and re install your printer

re start your PC 

and your scanners returns to life! 


;)

Thanks to tweedledee and vyvee.

---

### Post by tweedledee on 2011-11-18
> **vyvee said:**
> Scanner WORKS for me on Ubuntu 11.10!

Thanks for sharing.  I've updated my initial post to point to your post as a fix, at least for now, since it seems to work for several people.  I'll think about how to incorporate it into a package later.

Just FYI for those who are applying the fix, it is possible that loading the usblp module will cause other (non-Samsung) printers connected to your computer to stop working.  Which probably isn't an issue for most people, and won't affect everyone with multiple printers.

---

### Post by retrokid on 2011-11-20
"modprobe usblp" works for me too with my Samsung SCX-3200

Thanks very much!

---

### Post by bionade on 2011-11-21
Hi, really really thank you for this post. Problem solved.

Running Ubuntu 11.10, 32bit (but had the same problem since... let me think... 10.04 (?).
Now, after replacing the old netdiscovery with the new one, everything is just fine.

netdiscovery (new) --all:
```
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
ip: 192.168.178.21  slp: 0,0,0,0 snmp: 0,0,0 dsc: "Samsung SCX-4500W [SEC0015996143D9]"
# Total 1 printers found, 5s elapsed
```netdiscovery (new) --all --scanner:
```
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
ip: 192.168.178.21  slp: 0,0,0,0 snmp: 0,0,0 dsc: "Samsung SCX-4500W"
a8 00 43 10 53 61 6d 73 75 6e 67 20 53 61 6d 73
75 6e 67 20 53 43 58 2d 34 35 30 30 57 20 53 65
72 69 65 73 1d 33 04 2b 00 00 27 d8 00 00 36 d8
00 01 51 00 00 01 00 00 00 00 36 d8 00 00 36 d8
01 00 05 05 00 00
# Total 1 scanners found, 5s elapsed
```netdiscovery (old, not working) --all:
```
netdiscovery.old: relocation error: /lib/i386-linux-gnu/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
netdiscovery.old: relocation error: /lib/i386-linux-gnu/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
ip: 192.168.178.21  slp: 0,0,0,0 snmp: 0,0,0 dsc: " [SEC0015996143D9]"
# Total 1 printers found, 5s elapsed
```netdiscovery (old, not working) --all --scanners:
```
netdiscovery.old: relocation error: /lib/i386-linux-gnu/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference

```Thanks again, finally I can scan using WiFi. :D

---

### Post by bionade on 2011-11-21
Hi, really really thank you for this post. Problem solved.

Problem was: 
Scanning with Samsung SCX-4500w using WiFi connection while printing worked just fine.

Running Ubuntu 11.10, 32bit (but had the same problem since... let me think... 10.04 (?)).
Now, after replacing the old netdiscovery with the new one, everything is just fine.

netdiscovery (new) --all:
```
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
ip: 192.168.178.21  slp: 0,0,0,0 snmp: 0,0,0 dsc: "Samsung SCX-4500W [SEC0015996143D9]"
# Total 1 printers found, 5s elapsed
```netdiscovery (new) --all --scanner:
```
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
ip: 192.168.178.21  slp: 0,0,0,0 snmp: 0,0,0 dsc: "Samsung SCX-4500W"
a8 00 43 10 53 61 6d 73 75 6e 67 20 53 61 6d 73
75 6e 67 20 53 43 58 2d 34 35 30 30 57 20 53 65
72 69 65 73 1d 33 04 2b 00 00 27 d8 00 00 36 d8
00 01 51 00 00 01 00 00 00 00 36 d8 00 00 36 d8
01 00 05 05 00 00
# Total 1 scanners found, 5s elapsed
```netdiscovery (old, not working) --all:
```
netdiscovery.old: relocation error:  /lib/i386-linux-gnu/libnss_files.so.2: symbol strcmp, version GLIBC_2.0  not defined in file libc.so.6 with link time reference
netdiscovery.old: relocation error:  /lib/i386-linux-gnu/libnss_files.so.2: symbol strcmp, version GLIBC_2.0  not defined in file libc.so.6 with link time reference
# Network printers discovery utility
# Legend: ip: address slp: detected,ipp,lpr,raw_tcp snmp: detected,devtype,description
ip: 192.168.178.21  slp: 0,0,0,0 snmp: 0,0,0 dsc: " [SEC0015996143D9]"
# Total 1 printers found, 5s elapsed
```netdiscovery (old, not working) --all --scanners:
```
netdiscovery.old: relocation error:  /lib/i386-linux-gnu/libnss_files.so.2: symbol strcmp, version GLIBC_2.0  not defined in file libc.so.6 with link time reference

```
Thanks again, finally I can scan using WiFi. :grin:

---

### Post by Metal Hed on 2011-11-22
Super stoked! I finally got my parents samsung scx-4826fn to scan with 11.04! I think it was tweedledee useful tips that helped me out so kudos! \\:D/

---

### Post by Artorius89 on 2011-11-23
Thank you very much indeed, vyvee!

---

### Post by _karo on 2011-12-04
I bought a Samsung ML-1675 laser printer and got it working on Ubuntu 11.04. I installed the Samsung Unified drivers following the instructions, but the printer worked even before I installed them...? Ubuntu just autodetected it and it works. But I'd like to use the manual duplex function of the printer and cannot get it to work. When I try to change the 'Sides' option in Ubuntu's built-in printer properties app (in 'Job options') to two-sided, it just reverts right back to one-sided when I click apply. The printer shows up in the Samsung Unified Driver Configurator app also, but when I try to change the driver options there it says nothing about one-sided or two-sided printing. I'm using the ML-1670 Series driver, tried to change it to ML-1710 Series with no luck.

What am I doing wrong? Will I ever be able to print two-sided documents from Ubuntu?

---

### Post by GarthPS on 2011-12-04
Hi all,
Thanks to tweedledee!
I just successfully installed my brand new samsung ml-1860 that I just received (after one or two hours of fight with the official samsung's bunch of **** driver ).
So thanks a lot for your work man!
I will post this howto in french for french users.
Thanks again!
++

---

### Post by tweedledee on 2011-12-06
> **_karo said:**
> What am I doing wrong? Will I ever be able to print two-sided documents from Ubuntu?

Not sure what's going on with the default driver.  The Samsung ppd files for many ML printers do not seem to allow for duplexing, auto or manual.  In theory you could probably find/make a modified ppd that would work, or try various ML- printers until one works and has the right options.  Alternatively, you could try creating a generic postscript printer and add the duplexer option - not sure if that will work the way you need it to or not.

---

### Post by huntkey on 2011-12-20
Thank you very much [vyvee]("http://ubuntuforums.org/member.php?u=305229"). You saved my day

---

### Post by GarthPS on 2011-12-23
I am have issue printing png file..
cups report
"/usr/lib/cups/filter/cpdftocps failed"
I tried this 
```
sudo ln -s /lib/x86_64-linux-gnu/libpng12.so.0.46.0 /usr/lib/libpng.so.3
```but it did not work..
I had to pinrt my png in pdf and then I was able to print it.
thx

---

### Post by nurchi on 2011-12-23
Hello everyone.

Sorry if this has been posted, I didn't read all the 86 pages, but here is what I did and it worked with my Samsung SCX-4828FN.

First of all, I would like to thank tweedledee (post #1) for great help.

It worked initially, but the problem was that we have a USB attached machine and an identical one in a different office that is connected to the same network.
Now, while the printer worked flawlessly, scanning utilitiy (simple scan) would take a second to detect the scanner(s) and by default would select the network scanner.
This was not the desireable behaviour, since people that use this computer do not know enough to switch to the USB attached one.

So I installed the Samsung Unified Driver, latest version I downloaded is 3.00.65:07
Then, unblacklist usblp as described above, but for completeness, I'll repeat (if you hate vi, use edit, nano, or anything you like):
sudo vi /etc/modprobe/blacklist-cups-usblp.conf

Put a '#' before blacklist usblp. It should look like:
#blacklist usblp

You may also remove the line altogether (but you should not do that).

Now comes the best part:
sudo modprobe usblp

You are done.
Run your favourite scanning program and scan...

Hope this helped someone.

---

### Post by tweedledee on 2011-12-25
> **GarthPS said:**
> I am have issue printing png file..
cups report
"/usr/lib/cups/filter/cpdftocps failed"

Does this happen with all versions of the driver (3.00.90, 3.00.65, and legacy?) or just one?

---

### Post by daldude on 2011-12-26
I'm confused by these instructions. I think I did step 1 properly but I don't understand step 2.
How do I do step 2? 
What does this mean?

2. Install the GPG key for the repository. You can either (i) excecute
Code:

wget -O - [http://www.bchemnet.com/suldr/suldr.gpg](http://www.bchemnet.com/suldr/suldr.gpg) | sudo apt-key add -

How do I do this? 
How do I "Install the GPG key for the repository. You can either (i) excecute
Code:?"

---

### Post by multivista on 2011-12-26
Thanks for your valuable guide...

---

### Post by tweedledee on 2011-12-26
> **daldude said:**
> wget -O - [http://www.bchemnet.com/suldr/suldr.gpg](http://www.bchemnet.com/suldr/suldr.gpg) | sudo apt-key add -

How do I do this? 


Copy the wget line and paste it into a terminal window, or manually type it in.

---

### Post by mastablasta on 2011-12-27
I am thinking about buying the Samsung SCX-3205. 

i will connect it to winXP maschine and then i will print to it via SAMBA from Kubuntu 10.10 (will upgrade to 12.04 later on) and Debian 6 (actually Chrunchbang stable). Will it work with these drivers?

---

### Post by mastablasta on 2012-01-02
The printer driver from the added repository works perfectly on both maschines. What i wonder now is can i scan from the linux maschines on it? And how to set it up? Printer is connected to WinXP maschine via USB cable.

---

### Post by Mateusz Ho&#322;ysz on 2012-01-03
> **vyvee said:**
> Scanner WORKS for me on Ubuntu 11.10!

I have a Xerox WorkCentre PE220, which functions just like a -Samsung SCX-4521F. I've debugged for a few hours and the scanner function finally works!

1) Install samsungmfp-scanner.
2) Now try this! => sudo modprobe usblp
3) You can use 'xsane' or 'Simple Scan' to test... does it work now? :KS
4) If it works, then it means that 'usblp', which has been blacklisted, is the key. To un-blacklist it,
a) modify /etc/modprobe.d/blacklist-cups-usblp.conf
b) Comment the line by prefixing with a '#':
     #blacklist usblp
After this step, you don't need to 'sudo modprobe usblp' after starting your machine.

Well, it works for me, but I'm not sure if it can help to solve scanner problems faced by you all. Share you experience here!

I have samsung scx 4828fn and un-blacklisting usblp module makes scanner work but printing is unavailable. I have ubuntu 11.10 64bit and scx 4828fn is connected via usb.

I`ve read previous posts but I was unable to recover printing.
How did you managed to recover printing after un-blacklisting usblp? Are there any special tricks to reinstall printer after un-blacklisting usblp?

Anybody help?

Best regards

MH

---

### Post by tweedledee on 2012-01-03
> **Mateusz Ho&#322 said:**
> I have samsung scx 4828fn and un-blacklisting usblp module makes scanner work but printing is unavailable. I have ubuntu 11.10 64bit and scx 4828fn is connected via usb.

I`ve read previous posts but I was unable to recover printing.
How did you managed to recover printing after un-blacklisting usblp? Are there any special tricks to reinstall printer after un-blacklisting usblp?

Anybody help?

Best regards

MH

First blacklist usblp again (remove the #).  Then ```
sudo modprobe -r usblp
``` should unload the module.  If that doesn't work, a reboot is probably the simplest way to ensure that the module is unloaded and CUPS restored to its previous state.  If you still can't print, you could try deleting the printer and setting it up again, although that shouldn't be necessary.  And if you still can't print at that point, it's almost certainly not related to usblp.

Just for reference, is your printer connected by USB or over the network?

---

### Post by tweedledee on 2012-01-03
> **mastablasta said:**
> The printer driver from the added repository works perfectly on both maschines. What i wonder now is can i scan from the linux maschines on it? And how to set it up? Printer is connected to WinXP maschine via USB cable.

As I understand it, you won't be able to scan on the Linux machine if the printer is connected by USB to the Windows machine.  The driver doesn't seem to have any way to recognize the scanner in that case.  You could probably get it to work if there was a way to share the USB port directly with the Linux machine (i.e., give the Linux machine hardware-level access to it so that it appeared as a port on the Linux machine and could be seen by the driver), but I'm not aware of any method for doing that in Windows.

Caveat: I don't have a scanner and the last version of Windows I actively used was Win2K, so it's possible that I'm incorrect and that someone else has gotten that kind of setup working.

---

### Post by Pradorey on 2012-01-04
I own a Samsung clx-6220fx. Everything is working fine with the unified printer driver. Also the scanner is working properly. But one problem gives me a lot of pain. And that is the color managment. I know that is not easy for the linux driver, but when I want to change the brightness, and set it very low, there is no effect noticable. Everything I do is ignored. Does anybody have similar problems with it? How can I solve this? I would apreciate un answer very much[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by Mateusz Ho&#322;ysz on 2012-01-04
> **tweedledee said:**
> First blacklist usblp again (remove the #).  Then ```
sudo modprobe -r usblp
``` should unload the module.  If that doesn't work, a reboot is probably the simplest way to ensure that the module is unloaded and CUPS restored to its previous state.  If you still can't print, you could try deleting the printer and setting it up again, although that shouldn't be necessary.  And if you still can't print at that point, it's almost certainly not related to usblp.

Just for reference, is your printer connected by USB or over the network?

Thank you for your response.

Printer is connected by usb.

Today I have managed to make my SCX 4828fn work without un-blacklisting usblp module. I followed instructions from:

[http://askubuntu.com/questions/88700/how-to-define-my-samsung-scx3200-multifunction-printer/90772#90772](http://askubuntu.com/questions/88700/how-to-define-my-samsung-scx3200-multifunction-printer/90772#90772)

I have get details of my printer by command "sane-find-scanner". Then I have added this details to /etc/sane.d/xerox_mfp.conf and /lib/udev/rules.d/40-libsane.rules.

It is now possible to scan and print.

Kind regards

MH

---

### Post by tweedledee on 2012-01-05
> **Pradorey said:**
> I own a Samsung clx-6220fx. Everything is working fine with the unified printer driver. Also the scanner is working properly. But one problem gives me a lot of pain. And that is the color managment. I know that is not easy for the linux driver, but when I want to change the brightness, and set it very low, there is no effect noticable. Everything I do is ignored. Does anybody have similar problems with it? How can I solve this? I would apreciate un answer very much[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

There has been some discussion on this issue a while back in this thread, maybe more than once.  The general consensus seemed to be that color management didn't work well except in perhaps a few special cases.

---

### Post by Pradorey on 2012-01-06
"There has been some discussion on this issue a while back in this  thread, maybe more than once.  The general consensus seemed to be that  color management didn't work well except in perhaps a few special cases."

Thank you tweedledee, for your response. So maybe there is hope, that anyone will have resources to find a solution? In Samsung I would not trust, because once they were very unpolitely talking with me, when I tould them, that I am a Linuxuser.

---

### Post by jommeke on 2012-01-06
Seem to work fine on Squeeze/amd64.  Many thanks !

---

### Post by tweedledee on 2012-01-06
> **Pradorey said:**
> Thank you tweedledee, for your response. So maybe there is hope, that anyone will have resources to find a solution? In Samsung I would not trust, because once they were very unpolitely talking with me, when I tould them, that I am a Linuxuser.

I don't have much hope for the official driver; the response you got from Samsung is pretty typical.  The foomatic driver might work now or in the future for what you need, but has other limitations.  You can install both simultaneously if needed, though.

---

### Post by Pradorey on 2012-01-07
How do I get the foomatic driver for my clx 6220fx ? If I try to install it in ubuntu, it shows me only the clx-6220-series PS. I want to try how it works with the foomatic driver. Many thanks!!

---

### Post by tweedledee on 2012-01-07
> **Pradorey said:**
> How do I get the foomatic driver for my clx 6220fx ? If I try to install it in ubuntu, it shows me only the clx-6220-series PS. I want to try how it works with the foomatic driver. Many thanks!!

It appears (from [http://www.openprinting.org](http://www.openprinting.org)) that your printer is not yet supported by foomatic, although if you look around that site for user comments, etc. you may find a way to get it to work.

---

### Post by 4romany on 2012-01-14
I'm running 11.10 64 and 11.10 32 and recently purchased a networked Samsung ML-2955ND.   I followed the steps at the beginning of this thead - worked like a charm:
deb [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian extra
Than
wget -O - [http://www.bchemnet.com/suldr/suldr.gpg](http://www.bchemnet.com/suldr/suldr.gpg) | sudo apt-key add -
apt-get install samsungmfp-data
apt-get install
apt-get install samsungmfp-scanner
apt-get install samsungmfp-configurator-qt4

Whoever provided these packages and help many thanks....

---

### Post by lipinski on 2012-01-23
Was able to get a Samsun CLP-610ND working with this procedure on 11.10 (Oneiric).  I had to select the CLP-610 SPL-C driver as the CLP-610 2.0.0 and CLP-610ND 2.0.0 drivers wouldn't work at all, and foomatic was problematic as well for some reason.

In any case, I can print standard documents and stuff.  However, I'm running into problems with Labels - when using the Multipurpose tray, the printer is not properly printing starting at the left-edge of the labels, but rather where the left-edge would be if the page was a full 8.5" wide.

I started a new thread but figured there may be some other Samsung users monitoring this thread that can help...
[http://ubuntuforums.org/showthread.php?t=1913865](http://ubuntuforums.org/showthread.php?t=1913865)

Also, this may be driver related as it works in Windows...

---

### Post by tweedledee on 2012-01-24
> **lipinski said:**
> In any case, I can print standard documents and stuff.  However, I'm running into problems with Labels - when using the Multipurpose tray, the printer is not properly printing starting at the left-edge of the labels, but rather where the left-edge would be if the page was a full 8.5" wide.

Have you tried either of the alternate driver versions available as packages?  There have been various reports with some printers that the latest driver seems to have trouble finding the edge of the page in some cases.  It's also possible, though less likely, that switching to the alternate data package could help.

I don't think the printer itself does any edge detection of the page (at least as far as determining where to print), so you should be able to create the same effect with a regular piece of paper through the manual feed in place of your labels.

---

### Post by lipinski on 2012-01-24
> **tweedledee said:**
> Have you tried either of the alternate driver versions available as packages?  There have been various reports with some printers that the latest driver seems to have trouble finding the edge of the page in some cases.  It's also possible, though less likely, that switching to the alternate data package could help.
Not sure what you mean by alternate driver versions...  Is this something from Samsung, or from the repositories?

I do know that this used to work for me at some point previously in Ubuntu - 09.XX maybe - because I do have some OO templates that I set up for printing consistent labels (font, size, etc.).  But, it definitely doesn't work on 11.10.  

> **tweedledee said:**
> I don't think the printer itself does any edge detection of the page (at least as far as determining where to print), so you should be able to create the same effect with a regular piece of paper through the manual feed in place of your labels.
Yes - no matter what size I stick in there, it always seems to assume that the left edge of the paper is aligned with the far-left edge of the input tray.  Yet, when smaller width paper is used, the sliders move the paper to center.

---

### Post by tweedledee on 2012-01-24
> **lipinski said:**
> Not sure what you mean by alternate driver versions...  Is this something from Samsung, or from the repositories?

In the repository.  You can replace samsungmfp-driver with samsungmfp-driver-3.00.65 or samsungmfp-driver-legacy, separately or in combination with replacing samsungmfp-data with samsungmfp-data-legacy.

If you were using the Samsung driver in the older version of Ubuntu (either my packages or directly), switching the driver version to an older one may well solve your problem.  If you were using foomatic or some other driver at that time, it's less likely but still possible one of the alternate packages will help.

---

### Post by lipinski on 2012-01-25
> **tweedledee said:**
> In the repository.  You can replace samsungmfp-driver with samsungmfp-driver-3.00.65 or samsungmfp-driver-legacy, separately or in combination with replacing samsungmfp-data with samsungmfp-data-legacy.

If you were using the Samsung driver in the older version of Ubuntu (either my packages or directly), switching the driver version to an older one may well solve your problem.  If you were using foomatic or some other driver at that time, it's less likely but still possible one of the alternate packages will help.

I tried every combination I could think of - to no avail.

Actually, the old drivers made the problem worse - instead of just printing based on the wrong left edge position, the printing also printed on the bottom of the page, which when using 4.25"x5" paper, means that nothing is printed at all.
Using the most recent driver brought it back to the top edge, but using the wrong left edge still.

Frustrating - I know this worked at one point in Ubuntu.  It's things like this that make me want to throw in the towel with Linux as a desktop alternative - something as simple as printing a few labels turns into hours/days of troubleshooting...

I appreciate the help.  If you have any other ideas, I'm willing to try anything.

---

### Post by lipinski on 2012-01-25
When trying to select the driver, how to I know which is which?  Or, specifically, which is from your reopsitory?

When using the CUPS administration webpage, I copied the source html for the related selections:

<OPTION VALUE="foomatic:Samsung-CLP-610-foo2qpdl.ppd" >Samsung CLP-610 Foomatic/foo2qpdl (en)
<OPTION VALUE="foo2zjs:0/ppd/foo2zjs/Samsung-CLP-610.ppd" >Samsung CLP-610 Foomatic/foo2qpdl (recommended) (en)
<OPTION VALUE="foo2zjs:1/ppd/foo2zjs/Samsung-CLP-610.ppd" >Samsung CLP-610 Foomatic/foo2qpdl (recommended) (en)

<OPTION VALUE="Samsung-CLP-610.ppd.gz" >Samsung CLP-610 Foomatic/foo2qpdl (recommended) (en)
<OPTION VALUE="samsung/CLP-610splc.ppd.gz" >Samsung CLP-610 Series (SPL-C) (en)
<OPTION VALUE="splix:0/ppd/splix/samsung/clp610.ppd" >Samsung CLP-610, 2.0.0 (en)
<OPTION VALUE="splix:0/ppd/splix/samsung/clp610fr.ppd" >Samsung CLP-610, 2.0.0 (fr)
<OPTION VALUE="splix:0/ppd/splix/samsung/clp610pt.ppd" >Samsung CLP-610, 2.0.0 (pt_BR)
<OPTION VALUE="splix:0/ppd/splix/samsung/clp610nd.ppd" >Samsung CLP-610ND, 2.0.0 (en)
<OPTION VALUE="splix:0/ppd/splix/samsung/clp610ndfr.ppd" >Samsung CLP-610ND, 2.0.0 (fr)
<OPTION VALUE="splix:0/ppd/splix/samsung/clp610ndpt.ppd" >Samsung CLP-610ND, 2.0.0 (pt_BR)

All the 2.0.0 drivers/models seems to cause the printer to print out an improper driver error. 
I don't notice much difference in the foomatic vs SPL-C ones.  
Are all the foomatic ones the same?

---

### Post by tweedledee on 2012-01-25
> **lipinski said:**
> When trying to select the driver, how to I know which is which?  Or, specifically, which is from your reopsitory?

The SPL-C ones (the ones that don't say foomatic or splix) are the official Samsung drivers.  I would guess that you were using an old version of a foomatic (or maybe splix) driver when your printer behaved as you expected, and something has broken it since then.  Although it's possibly that it's some change in CUPS that is the problem.

Short of removing one of the paper-size handles (which is probably irreversible) so that you can hold the labels in place all the way to left, or switching to a different label system on a larger sheet, I can't think of anything else for you to try.  Actually, it's possible this problem is common but only infrequently encountered - I'm sure it's been years since I tried to print on a reduced size piece of paper on my printer.  Samsung's support for printers on Linux is less than ideal, and since it's all proprietary there's not much that can be done about it.

However, I'm not saying there isn't a solution or that someone else following this thread might not have solved it - just that I don't know of one.

---

### Post by tranqui69 on 2012-01-26
> **okkadiroglu said:**
> Hi,

I did it! Thanks all for the help.

I installed, 

*samsungmfp-data, samsungmf--configurator-data, samsungmfdriver, samsungmfp-scanner* from* [http://ww.bchemnet.com/suldr](http://ww.bchemnet.com/suldr) debian extra.* 

Also, my user is in the *lp* and *saned* groups. After starting the CLX-2160, responce to the *lsusb* is:

*Bus 001 Device 007: ID 04e8:3425 Samsung Electronics Co., Ltd*

and for

*sane-find-scanner*

 I got:

[I]found USB scanner (vendor=0x0ac8, product=0x303b) at libusb:002:003
found USB scanner (vendor=0x04e8 [Samsung Electronics Co., Ltd.], product=0x3425 [CLX-216x Series]) at libusb:001:007[/I]

Inserting vendor and product numbers for CLX-2160 listed above into 

/ect/sane.d/xerox_mfp.conf 

I was able to scan.

Many thanks for all those helpers.

Bast Regards

I followed all your steps and i can't make it work. Can you give me a clue. This is your message, and my results

I installed,
samsungmfp-data, samsungmf--configurator-data, samsungmfdriver, samsungmfp-scanner from [http://ww.bchemnet.com/suldr](http://ww.bchemnet.com/suldr) debian extra.
[ME TOO - OK]

Also, my user is in the lp and saned groups. After starting the CLX-2160, responce to the lsusb is:

Bus 001 Device 007: ID 04e8:3425 Samsung Electronics Co., Ltd
[MINE]
Bus 008 Device 003: ID 04e8:3425 Samsung Electronics Co., Ltd 

and for

sane-find-scanner

I got:

found USB scanner (vendor=0x0ac8, product=0x303b) at libusb:002:003
found USB scanner (vendor=0x04e8 [Samsung Electronics Co., Ltd.], product=0x3425 [CLX-216x Series]) at libusb:001:007

[MINE]
found USB scanner (vendor=0x04e8 [Samsung Electronics Co., Ltd.], product=0x3425 [CLX-216x Series]) at libusb:008:003
(This is the only change, can be this?)


Inserting vendor and product numbers for CLX-2160 listed above into

/ect/sane.d/xerox_mfp.conf

[MINE]
/etc/sane.d/xerox_mfp.conf
(I added this lines based on your tutorial)
# Samsung CLX-216x Series
usb 0x0ac8 0x303b

# Samsung CLX-2160
usb 0x04e8 0x3425



I was able to scan.
[MINE]
I can't :confused:

Can anybody help me with the Samsung CLX-2160. 

Thank you very much for your attention. Best Regards

---

### Post by fongbt on 2012-01-27
I followed pdonadeo's instructions and printing worked. But scanning didn't. There are a couple of steps I took:

Removed the following files from /etc/udev/rules.d:
98_smfpautoconf_samsung.rules
99_smfpautoconf_samsung.rules

Power off the printer, remove usb cable, reconnect and power on.

Add my user account to lp and scanner group

Run xsane as root which successfully detected the Samsung SCX-3200 device. Then run xsane again as regular user to confirm it works after detection.

I got this printer for less than US$100. Can't complain the extra work required!

---

### Post by uqbar on 2012-01-30
Is there anyone able to send and/or receive faxes wirh an SCX-4623F?

---

### Post by tweedledee on 2012-01-31
> **fongbt said:**
> Removed the following files from /etc/udev/rules.d:
98_smfpautoconf_samsung.rules
99_smfpautoconf_samsung.rules

Was this actually necessary - meaning that if you restored those files now after the other steps you took, can you still scan?

I'm asking because I have been wondering for a while if those files were actually necessary/useful to include, but have no method for testing myself.

---

### Post by digibill on 2012-02-05
In a fresh system install of ubuntu 11.04, I install the unified driver  from the repository, as described in the first message. However, my  samsung clp-315 printer keeps using ubuntu's driver (spl-c) instead of the  new one, resulting in wrong colors (I remember having exactly the same  problem on a previous ubuntu installation, before using the unified  driver).

How can I force it to use the unified driver?

---

### Post by yahs on 2012-02-06
Information on some changes to Printing and Scanning in Ubuntu 12.04

I attached my Samsung SCX-4500W by USB today and ran a live installation of Ubuntu 12.04 Alpha 2.

Clicking on the system Settings Icon (Top Right Hand Corner) the entries are:

Systems Settings
Displays
StartUp applications
Software Up to Date

Attached devices (Greyed Out)

Printers: 
Scanner: 
Webcam: 

Suspend
Shut Down

Clicking on Printers brings up the add printer dialogue box, where the Samsung Scx-4500w is correctly identified and Splix Printer installs and works.

Clicking on Scanner (which I did before I added the printer) opens Simple Scan which runs and scans as normal.

Clicking on Webcam brings up the software centre to install cheese.

I repeated the above but this time with my Cannon MFP attached by USB. This time “Scanner” is replaced by “Canon Scanner” but again the scan runs and works without a printer being installed.

---

### Post by peterthevicar on 2012-02-07
Fabulous, thank you. I was tearing my hair out trying to get a CLP-620ND to work with CUPS in Ubuntu Natty 11.04. The Generic PCL 5c/hpjs driver worked pretty well but VERY slowly. I tried a manual install of the ppd from the Unified Driver package but that printed full width in draft, half width in normal and quarter width in best quality mode. Adding this repository and installing the samsungmfp-driver and samsungmfp-data packages gave me access to the Samsung drivers, I added the printer again and all was well.

The only issue I had was with page alignment: the printing was too high and too far to the right. I edited the /etc/cups/ppd/CLP-650ND.ppd adjusted the last two numbers in the ImagingArea for A4 and corrected it that way - not a pretty solution but it worked!

Hope this may help anyone struggling with the CLP-620ND.

One remaining issue is that sometimes left aligned plain text in my document gets right aligned in the printout - weird! Work around is to use a font not built into the printer.

---

### Post by luismanolo on 2012-02-08
Many thanks from Spain, my printer works fine.
Good work.
Thanks again.

---

### Post by tweedledee on 2012-02-10
> **digibill said:**
> In a fresh system install of ubuntu 11.04, I install the unified driver  from the repository, as described in the first message. However, my  samsung clp-315 printer keeps using ubuntu's driver (spl-c) instead of the  new one, resulting in wrong colors (I remember having exactly the same  problem on a previous ubuntu installation, before using the unified  driver).

How can I force it to use the unified driver?

If you manually configure the printer (using either Ubuntu's tools or the Samsung Configurator) and select the Samsung driver, it should not revert back to the default.  It will probably never pick up the Samsung driver otherwise, though.

---

### Post by flinkdeldinky on 2012-02-22
I'm on an AMD64 Debian testing system.  Using your deb packages I finally got my CLP-325 printing in color as well as the Windows drivers (it least in my limited testing).

Without your packages CUPS was able to detect and install a driver that gave me full printing functionality except that printing a photo was to dark (I'd describe it as muddy) and had a weird not quite horizontal banding.

I tried to install the Samsung Driver by hand but the configurator was uncooparitive.  Although if I ran it from the shell command (I think it was install.sh) it would install automatically the correct driver.  Except it would be attached to mfp4 and that didn't work.  And there was a deamon smfpd that would eat up 25% cpu nor more or less.  I found no way to change connection and the configurator wouldn't list anything I recognized as a USB connection.

I was able to reconfigure the connection using CUPS web interface but whenever I tried to print the printer would actually print a page complaining I was using the wrong driver.

So  I uninstalled it and I installed your debs.  Basically a variation of the above.  The mfp connection thing is a real problem on my system.  Then I saw on your site that I only needed the driver and data debs.  So I uninstalled everything and reinstalled just the driver and data debs.

Cups saw the clp-325 (as usual) and when I setup the printer I chose to use the Samsung CLP-320 Series (SPL-C) driver and not the foomatic driver.  Then when I configured the driver I got different options so I knew the foomatic driver wasn't being used.  I set the color to vivid and presto!, picture perfect photo prints.

So I recommend debian testing users (and everybody else!) just use the driver and data debs.  Then go into cups and a handful of clicks later you're good to go.  Samsungs configurator doesn't offer much and cups does everything fine (I assume kde/gnome interfaces work fine as well).

Thank you!

---

### Post by CalvinK on 2012-02-22
> **vyvee said:**
> Scanner WORKS for me on Ubuntu 11.10!

I have a Xerox WorkCentre PE220, which functions just like a -Samsung SCX-4521F. I've debugged for a few hours and the scanner function finally works!

1) Install samsungmfp-scanner.
2) Now try this! => sudo modprobe usblp
3) You can use 'xsane' or 'Simple Scan' to test... does it work now? :KS
4) If it works, then it means that 'usblp', which has been blacklisted, is the key. To un-blacklist it,
a) modify /etc/modprobe.d/blacklist-cups-usblp.conf
b) Comment the line by prefixing with a '#':
     #blacklist usblp
After this step, you don't need to 'sudo modprobe usblp' after starting your machine.

Well, it works for me, but I'm not sure if it can help to solve scanner problems faced by you all. Share you experience here!


Thank you very much. I works just fine for me too with a Samsung CLX 3185. I had that problem since the last update some weeks ago

---

### Post by Joseph Nickerson on 2012-02-23
I have a Samsung SCX-4828FN printer/scanner and I'm trying to set it up on a work network so that we can print wireless from a number of different printers. I currently have a number of desktop printers set-up and a version of "Samsung Universal Print Driver" installed, however I am only able to print from one machine that is connected via USB connection. Is there a step-by-step process that you might know of that would solve my problem of getting a wireless print option set-up for the various PC's in my work network?

We are all currently using windows vista home edition. Any ideas that would help?

Thanks,

Joe

---

### Post by tweedledee on 2012-02-23
> **Joseph Nickerson said:**
> We are all currently using windows vista home edition. Any ideas that would help?

If this is a printer connected to a Windows machine and you want other Windows machines to see it, this is probably not the right forum.  Any general guide on sharing printers in Windows will probably give you the information you need, it should not be Samsung specific.  I have no idea how printer sharing works in Vista.  At one point, Samsung had a "SyncThru" utility available for certain printers that helped with certain kinds of sharing under Windows (~2004 was the last time I dealt with this problem under Windows), I'm not sure if that is relevant or even still available.

---

### Post by MFonville on 2012-04-09
I do use the most recent version of this driver from the repository for my Samsung CLX-3185FN via the network. I recently upgraded one of my workstations to the beta of Ubuntu Precise. This did break the printerdriver, also after re-installing the driver and deleting+re-adding the printer in CUPS.

The printer GUI keeps reporting that the Toner/Ink is not in place and therefore printing jobs don't get executed. Meanwhile printing from the other workstations with Oneiric don't give any trouble.

Any chance to research the cause of this issue and prevent trouble when people will start upgrading to the final release Precise at the end of this month?

---

### Post by tweedledee on 2012-04-10
> **MFonville said:**
> Any chance to research the cause of this issue and prevent trouble when people will start upgrading to the final release Precise at the end of this month?

If you're willing, please try the 3.00.65 version driver available in the repository and see if that causes the same issues.  In addition, please share what protocol you are using (LPD, IPP, ?) over the network.  You also might want to check and see if there is a way to disable those checks in the printer configuration (with the most recent driver).

The version of CUPS in Precise is newer, and there is a comment in the changelog that may be relevant: "Fixed supply level reporting for some printers."  However, it's not linked to any references, so I'm not sure what the technical change was nor if it is relevant.  The only obvious way to test would be to install Precise and then force-downgrade the CUPS packages to the prior versions, or to see if any Debian testing/unstable users are seeing anything similar over the last few weeks.

It may also be something else entirely, but these are my initial guesses as to where to start.

---

### Post by MFonville on 2012-04-10
> **tweedledee said:**
> If you're willing, please try the 3.00.65 version driver available in the repository and see if that causes the same issues.  In addition, please share what protocol you are using (LPD, IPP, ?) over the network.  You also might want to check and see if there is a way to disable those checks in the printer configuration (with the most recent driver).
I did now try it with the 3.00.65 driver, exactly the same issues. I do use IPP over the network.
I will look into the possibility of disabling the toner level reporting, but that would (of course) be a regression (also for the other non-Precise workstations)

> **tweedledee said:**
> The version of CUPS in Precise is newer, and there is a comment in the changelog that may be relevant: "Fixed supply level reporting for some printers."  However, it's not linked to any references, so I'm not sure what the technical change was nor if it is relevant.  The only obvious way to test would be to install Precise and then force-downgrade the CUPS packages to the prior versions, or to see if any Debian testing/unstable users are seeing anything similar over the last few weeks.

It may also be something else entirely, but these are my initial guesses as to where to start.
Maybe it is possible to contact the person that did create the patch for the ink level reporting? The developer involved for sure would know whether it might be the cause of this issue. Meanwhile, force-downgrading is tricky for me, since multi-arch disabled the possibility of using aptitude to select my packages easily and I don't have the time at this very moment (maybe somewhere later coming weeks) to play around with different versions of the packages manually.

---

### Post by tweedledee on 2012-04-10
> **MFonville said:**
> Maybe it is possible to contact the person that did create the patch for the ink level reporting? The developer involved for sure would know whether it might be the cause of this issue.
If I have time, I'll look into tracking down the specific patch, etc., but it's fairly unlikely that I'll have a lot of time to spend on this in the next 3-4 weeks.  If anyone else feels inclined to do so and report back . . .

> **MFonville said:**
> Meanwhile, force-downgrading is tricky for me, since multi-arch disabled the possibility of using aptitude to select my packages easily and I don't have the time at this very moment (maybe somewhere later coming weeks) to play around with different versions of the packages manually.
Again if I find time, I'll set up an installation and adjust packages.  Because the 3.00.65 driver acts the same way, the change is almost certainly related to a change in CUPS.  It's possible there is also a CUPS setting somewhere that affects this.

Although I hope I'm wrong, my current gut feeling is that this will require yet another sort of hack to work around unless Samsung happens to release a new driver version soon that solves it.  (Which seems unlikely, as near as I can tell no activity at all has taken place with the Linux driver in the last 7 or 8 months, but maybe they have a surprise planned.)  And developing those requires a lot of input from other people and time on my part, so a fix is highly unlikely before the official Precise release.

If anyone else reading this has any experiences with Precise, either now or after final release, please share.  Or a current Debian testing/unstable system with the 1.5.2 CUPS package.  Particularly printers that report toner levels (mine doesn't).

---

### Post by MFonville on 2012-04-15
> **tweedledee said:**
> If I have time, I'll look into tracking down the specific patch, etc., but it's fairly unlikely that I'll have a lot of time to spend on this in the next 3-4 weeks.  If anyone else feels inclined to do so and report back . . .


Again if I find time, I'll set up an installation and adjust packages.  Because the 3.00.65 driver acts the same way, the change is almost certainly related to a change in CUPS.  It's possible there is also a CUPS setting somewhere that affects this.

Although I hope I'm wrong, my current gut feeling is that this will require yet another sort of hack to work around unless Samsung happens to release a new driver version soon that solves it.  (Which seems unlikely, as near as I can tell no activity at all has taken place with the Linux driver in the last 7 or 8 months, but maybe they have a surprise planned.)  And developing those requires a lot of input from other people and time on my part, so a fix is highly unlikely before the official Precise release.

If anyone else reading this has any experiences with Precise, either now or after final release, please share.  Or a current Debian testing/unstable system with the 1.5.2 CUPS package.  Particularly printers that report toner levels (mine doesn't).

Apparently the problem is solved by using the Socket:// protocol instead of the IPP protocol. And when looking at the CUPS logs, this bugreport looks related: [https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/973270](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/973270)

---

### Post by tweedledee on 2012-04-15
> **MFonville said:**
> Apparently the problem is solved by using the Socket:// protocol instead of the IPP protocol. And when looking at the CUPS logs, this bugreport looks related: [https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/973270](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/973270)

Interesting.  Does LPD also work?  Socket is far more limited than IPP, LPD is intermediate.

---

### Post by pinodd on 2012-04-15
What about aversion of Samsung Unified Printer Driver for PPC arch?

---

### Post by tweedledee on 2012-04-15
> **pinodd said:**
> What about aversion of Samsung Unified Printer Driver for PPC arch?

You'd have to ask Samsung directly for that.  And I rate the chances of it happening as zero - they are unlikely to build for an old architecture given that they barely invest any time at all in current architectures.

---

### Post by gaboro on 2012-04-21
> **MFonville said:**
> Apparently the problem is solved by using the Socket:// protocol instead of the IPP protocol. 
Thanks for this info, it works for me, too. The socket protocol is the only one that works with my CLX-3185FN on Precise.

cheers
gaboro

---

### Post by nigeldodd on 2012-04-21
Indeed, thanks Tweedledee for your post. It has made my Samsung usb ML-1865 work on Ubuntu 11.10 64bit.

There is one small issue which is that my usb scanner (an Epson 2450) will work until I turn the ML-1865 printer on. At that point Simple Scan reports that it cannot find a scanner.

---

### Post by uhappo on 2012-04-22
Anyone having problems with printing in 12.04? I'm using Samsung SCX-3205 printer/scanner and after first successful print operation (after turning on) printer goes abit crazy, prints blank pages or some miscallaneous letters in one line

---

### Post by nick4mony on 2012-04-26
Is this the right place to put general feedback for statistical purposes?
Set up my system to use the repository as instructed. Everything working well, but the configurator (scanning) program is a bit brain-damaged.

Details:
[list]
[*] Ubuntu 10.04 desktop, 64-bit, Australian settings.
[*] Samsung CLX3185FW, connected by Ethernet network (Wireless and fax not being used)
[*] It gets its IPv4 from the router's DHCP (as a fixed host).
[*] Installed from the repository: smsungmfp... -data, -driver, -scanner, -configurator-qt4, and dependencies. Shied away from samsungmfp-lpr for now.
[*] $ [font=courier]sudo ufw allow proto udp from 192.168.bla.bla[/font]
[*] Tested successfully: colour printing, flatbed scanning 1200dpi at A5 size, ADF scanning 600dpi of A4 pages, black photocopy, colour photocopy.
[/list]

Gotchas:
[list]
[*] If you use the ADF, put the pages in face up, and push the pages in a bit further until you hear a beep.
[*] The ufw command above (typed exactly as shown except for the IP address) puts an exemption into the firewall (both live, and in config so it survives a restart). And don't forget to add your users to the 'lp' group.
[*] If you use the ADF, don't attempt preview.
[*] If someone else attempts printing at the same time, someone will lose out.
[*] The install alters the default printer - alter it back as your admin user (if you want a different printer to be the default) - ruddy Samsung!
[/list]

---

### Post by jtsop on 2012-04-28
I have a problem with the top margin (no matter what I try there is no top margin, even if I have some newlines in my document, it starts printing on the top of the page) when using the samsungmfp-driver (3.00.90-2).

When I revert to samsungmfp-driver-legacy (3.00.37-8) printing is ok but the scanner is not found.

I use network printing and scanning.

PS: Using samsungmfp-driver-3.00.65 (which is reported as version 3.00.90-2) works fine

---

### Post by tweedledee on 2012-04-29
> **jtsop said:**
> I have a problem with the top margin (no matter what I try there is no top margin, even if I have some newlines in my document, it starts printing on the top of the page) when using the samsungmfp-driver (3.00.90-2).

When I revert to samsungmfp-driver-legacy (3.00.37-8) printing is ok but the scanner is not found.

I use network printing and scanning.

PS: Using samsungmfp-driver-3.00.65 (which is reported as version 3.00.90-2) works fine

I don't have a better solution than to use the 3.00.65 driver for now.  Which model printer is having this problem?

---

### Post by jtsop on 2012-04-29
> **tweedledee said:**
> I don't have a better solution than to use the 3.00.65 driver for now.  Which model printer is having this problem?

CLX 3175FN

Could you at least fix the version info for 3.00.65 (if yes could you post it here when it is done to downgrade to the correct package)?

---

### Post by tweedledee on 2012-04-29
> **jtsop said:**
> CLX 3175FN

Could you at least fix the version info for 3.00.65 (if yes could you post it here when it is done to downgrade to the correct package)?

As strange as it seems, the version info is correct.  The 3.00.65 package is actually a bit of a hybrid of the 3.00.90 and 3.00.65 driver files, so I have it versioned at 3.00.90 to reflect that.  This is in contrast to the -legacy driver, which is purely 3.00.37, and has different dependencies than the more recent versions.

---

### Post by Nick Payne on 2012-05-01
The drivers in this ppa don't seem to work with a freshly installed 12.04 amd64 and a Samsung ML-2165W printer on the network. When I install the drivers from the ppa, add the printer using config-system-printer, and print a test page, all I get out on the printer is five lines:
```
INTERNAL ERROR - Undefined Command
POSITION : 0x0 (0)
SYSTEM : h6fw_5.51/x1_pa_sim
LINE : 296
VERSION : SPL 5.51 03-28-2011

```
However, if I uninstall the drivers from the ppa, download UnifiedLinuxDriver_1.01.tar.gz from Samsung, manually install the drivers from the download, and perform the identical printer configuration, I get a successful test print.

BTW, I wasn't able to setup the printer using the Samsung Unified Driver Configurator that the Samsung install provided (it wouldn't let me add a printer), but I was able to get it working by running config-system-printer from a terminal.

---

### Post by nikoola on 2012-05-01
After upgrade to Ubuntu 12.04 my CLP 315 become very slow on image printing.
I use Samsung Unified Printer Driver.

---

### Post by tweedledee on 2012-05-02
> **Nick Payne said:**
> However, if I uninstall the drivers from the ppa, download UnifiedLinuxDriver_1.01.tar.gz from Samsung, manually install the drivers from the download, and perform the identical printer configuration, I get a successful test print.

BTW, I wasn't able to setup the printer using the Samsung Unified Driver Configurator that the Samsung install provided (it wouldn't let me add a printer), but I was able to get it working by running config-system-printer from a terminal.

This doesn't surprise me.  The ML-2165w is a new printer, and the latest drivers from Samsung in my repository were released prior to this printer being officially announced.  I'm actually surprised the option to use the packaged drivers with that printer even exists, apparently Samsung included a pre-release ppd that doesn't work well.  Even the driver you downloaded directly is almost as old, and probably still contains bugs they haven't bothered to fix.  I've been waiting for Samsung to provide updated drivers for their newest printers, but so far have not seen anything - although I was not aware of this particular update, and I will look at the differences and possibly package the version provided for this printer.  Although it is a major version change (4.00.35 vs. 3.00.90 most recent elsewhere), it's not immediately obvious to me there is actually any substantial difference.  The failure of the configurator to work correctly makes me hesistant to spend a lot of time with this version, because that implies there are some problems that may not show up until many people start installing it.

I'll have more time to deal with all these sorts of issues starting in a couple of weeks.

---

### Post by tweedledee on 2012-05-02
> **nikoola said:**
> After upgrade to Ubuntu 12.04 my CLP 315 become very slow on image printing.
I use Samsung Unified Printer Driver.

Probably related to the CUPS update in 12.04.  Testing issues with the latest CUPS is one of my goals for this month.  Which driver version are you using (3.00.90, 3.00.65, 3.00.37)?

---

### Post by dfreidus on 2012-05-03
> **uhappo said:**
> Anyone having problems with printing in 12.04? I'm using Samsung SCX-3205 printer/scanner and after first successful print operation (after turning on) printer goes abit crazy, prints blank pages or some miscallaneous letters in one line

I've got exactly the same problem. Has anyone got a fix for this?

---

### Post by tweedledee on 2012-05-03
> **dfreidus said:**
> I've got exactly the same problem. Has anyone got a fix for this?

More information is needed to help you and the previous poster: how are you connected (network/usb)?  Which printer driver version?  Have you tried other driver versions?

---

### Post by b1b1 on 2012-05-04
> **dfreidus said:**
> I've got exactly the same problem. Has anyone got a fix for this?

I had the same problem with my SCX-4825FN with Ubuntu Precise, CUPS-1.5.2 and every version of the Samsung drivers I tried.

I fixed it by downloading CUPS-1.5.0 from source, installing it then re-pointing /usr/sbin/cupsd to point to the new binary.

After this the latest driver (3.00.90) works.

---

### Post by uhappo on 2012-05-05
> **b1b1 said:**
> I had the same problem with my SCX-4825FN with Ubuntu Precise, CUPS-1.5.2 and every version of the Samsung drivers I tried.

I fixed it by downloading CUPS-1.5.0 from source, installing it then re-pointing /usr/sbin/cupsd to point to the new binary.

After this the latest driver (3.00.90) works.

Nice to know there is a solution. This sounds just too complicated to me..

---

### Post by b1b1 on 2012-05-05
> **uhappo said:**
> Nice to know there is a solution. This sounds just too complicated to me..

Well, you could install Ubuntu Oneiric instead, as this uses CUPS-1.5.0. But if you feel like having a crack at installing CUPS-1.5.0 on Precise, and you've already got CUPS and the 3.00.90 Samsung driver installed, you can download CUPS-1.5.0 from [http://www.cups.org/software.php](http://www.cups.org/software.php) and then:

```
sudo apt-get -y build-dep cups
tar xjvf cups-1.5.0-source.tar.bz2
cd cups-1.5.0
./configure --prefix=/opt/cups-1.5.0
make
sudo make install
sudo service cups stop
sudo mv /usr/sbin/cupsd /usr/sbin/cupsd.orig
sudo ln -s /opt/cups-1.5.0/sbin/cupsd /usr/sbin/cupsd
sudo cp /usr/lib/cups/filter/rastertosamsungspl /opt/cups-1.5.0/lib/cups/filter/
sudo service cups start
```

Then you can browse to localhost:631 and install the .ppd file from /usr/share/cups/model.

---

### Post by dfreidus on 2012-05-05
> **b1b1 said:**
> 

```
sudo apt-get -y build-dep cups
tar xjvf cups-1.5.0-source.tar.bz2
cd cups-1.5.0
./configure --prefix=/opt/cups-1.5.0
make
sudo make install
sudo service cups stop
sudo mv /usr/sbin/cupsd /usr/sbin/cupsd.orig
sudo ln -s /opt/cups-1.5.0/sbin/cupsd /usr/sbin/cupsd
sudo cp /usr/lib/cups/filter/rastertosamsungspl /opt/cups-1.5.0/lib/cups/filter/
sudo service cups start
```

Then you can browse to localhost:631 and install the .ppd file from /usr/share/cups/model.

This seems to have worked for me.

Thanks very much

---

### Post by uhappo on 2012-05-05
> **b1b1 said:**
> Well, you could install Ubuntu Oneiric instead, as this uses CUPS-1.5.0. But if you feel like having a crack at installing CUPS-1.5.0 on Precise, and you've already got CUPS and the 3.00.90 Samsung driver installed, you can download CUPS-1.5.0 from [http://www.cups.org/software.php](http://www.cups.org/software.php) and then:

```
sudo apt-get -y build-dep cups
tar xjvf cups-1.5.0-source.tar.bz2
cd cups-1.5.0
./configure --prefix=/opt/cups-1.5.0
make
sudo make install
sudo service cups stop
sudo mv /usr/sbin/cupsd /usr/sbin/cupsd.orig
sudo ln -s /opt/cups-1.5.0/sbin/cupsd /usr/sbin/cupsd
sudo cp /usr/lib/cups/filter/rastertosamsungspl /opt/cups-1.5.0/lib/cups/filter/
sudo service cups start
```

Then you can browse to localhost:631 and install the .ppd file from /usr/share/cups/model.

Thanks for info! Installing 11.04 or 11.10 is a no go for me, my system froze occasionally with those, 12.04 has been stable.

---

### Post by b1b1 on 2012-05-06
> **dfreidus said:**
> This seems to have worked for me.

Thanks very much

Well, it has allowed me to print the test page from the CUPS web page and print from other machines on the network to my CUPS server. However I'm still having problems printing locally ie. from the machine itself to its own CUPS daemon. Printing PDFs from evince causes crazy symbols etc., which can only be fixed by using lpr:

```
lpr something.pdf
```I think there's something else weird going on with Ubuntu 12.04.

---

### Post by Yetisaurus Akjas on 2012-05-08
Hello to all. :) (this is my first post on ubuntuforums - I've just registered) 

I hope this is the right place to post the following problem. If I'm wrong, I hope my excuses will be accepted. 

I have a Samsung SCX-4623 connected through USB to a computer (running Ubuntu 10.04.4) that doesn't print any PDF-1.5 files I really need to print. 

The return of "dpkg -l | grep samsung" is below : 

ii  samsungmfp-data 3.00.90-2 Samsung Unified Linux Driver (data)
ii  samsungmfp-driver 3.00.90-2 Samsung Unified Linux Driver (drivers)
ii  samsungmfp-network 3.00.90-2 Samsung Unified Driver Configurator (network
ii  samsungmfp-scanner 3.00.90-2 Samsung Unified Linux Driver (enable scannin

The content of the file /etc/cups/printers.conf is: 

# Printer configuration file for CUPS v1.4.3
# Written by cupsd
# DO NOT EDIT THIS FILE WHEN CUPSD IS RUNNING
<DefaultPrinter Samsung-SCX-4623>
Info Samsung SCX-4623
Location casierie Crasna
MakeModel Samsung SCX-4623 Series
DeviceURI usb://Samsung/SCX-4623%20Series
State Idle
StateTime 1336482836
Type 8392772
Filter application/vnd.cups-raw 0 -
Filter application/vnd.cups-postscript 0 rastertosamsungspl
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
Option orientation-requested 3
</Printer>

Thank you in advance for any help. :)

---

### Post by tweedledee on 2012-05-09
> **Yetisaurus Akjas said:**
> I have a Samsung SCX-4623 connected through USB to a computer (running Ubuntu 10.04.4) that doesn't print any PDF-1.5 files I really need to print.

This could be a lot of different things.

If you can print the same files to a different printer from the same computer connected the same way (which I realize you may or may not be able to test), then it is the Samsung driver at fault.  Try the 3.00.65 driver package.

If you can print non-PDF files fine but not any PDF, or some PDF files but not specific ones, it could be the Samsung driver but probably isn't - but try the solution above anyway because it is simpler than the alternatives.

Also try setting up the printer as a new printer, occasionally that clears out bizarre errors.

Most likely, though, it is a CUPS or ghostscript problem.  There are a LOT of bug reports open for both (on Debian, Ubuntu, all other distributions) regarding failure to print specific PDF files, and they tend to not be resolved because they are highly specific to certain combinations of printers, CUPS, and distributions.  Sometimes they go away with a CUPS or ghostscript upgrade, sometimes not.  Sometimes it is only true for specific printers, or methods of connecting the printers.  In a few cases it seems to be related to using specific locales (but not any English-based ones that I know of).  Sometimes it can be worked around by printing the pdf to a postscript file, then sending the postscript file to the printer.

If changing the Samsung driver doesn't help, and you have some time and interest, I would suggest getting a live CD of a more recent Ubuntu version (or any other distribution with a live CD), boot into it, configure the printer (using the repository), and see if you can print the problematic files.  If you can, then your only real fix will be to upgrade.  If you still can't, and you've tried some of the other suggestions, I may be able to at least help you narrow it down a little and determine if you should file a bug report.

---

### Post by johnfrith on 2012-05-10
I have an ML2525 on USB. 

It was working fine under the Unified Driver installed from the SAMSUNG website under 10.04

Did fresh install of 12.04. Before trying to do anything, I installed driver as per 1st page of this thread. Then "added printer", using appropriate foo driver. Don't know if this was necessary.

Printer worked ok for one print, then following prints just go to thin air. Can see the job on the print list, which disappears after a while, but no output and no error messages. Restarting machine allows me to print one time again.

Any ideas? TIA.

---

### Post by johnfrith on 2012-05-10
Don't know if it's relevant, but the User listed in the print queue is 'Unknown'.

Cheers.

---

### Post by makol1995 on 2012-05-10
> **johnfrith said:**
> Don't know if it's relevant, but the User listed in the print queue is 'Unknown'.

Cheers.

Hi all

I am using a Samsung CLX-3185FN and UBUNTU 12.04 LTS. The printer is connected on my Lan. Printing over the network works fine, but UBUNTU is not able to find the Scanner on the network.
I have XSane installed as well.

With "dpkg -l | grep samsung" I get:
ii  samsungmfp-configurator-data             3.00.90-2                               Samsung Unified Driver Configurator (data)
ii  samsungmfp-data                          3.00.90-2                               Samsung Unified Linux Driver (data)
rc  samsungmfp-driver-3.00.65                3.00.90-2                               Samsung Unified Linux Driver (drivers)
rc  samsungmfp-driver-legacy                 3.00.37-8                               Samsung Unified Linux Driver (legacy drivers)
ii  samsungmfp-netdiscovery                  3.00.90-2                               transitional package for samsungmfp-network
ii  samsungmfp-netdiscovery-oldlibc          3.00.90-2                               transitional package for samsungmfp-network
ii  samsungmfp-network                       3.00.90-2                               Samsung Unified Driver Configurator (network connectivity)

Does anybody has an idea how to fix this?

Thanks for your help.

---

### Post by uhappo on 2012-05-10
> **johnfrith said:**
> I have an ML2525 on USB. 

Printer worked ok for one print, then following prints just go to thin air. Can see the job on the print list, which disappears after a while, but no output and no error messages. Restarting machine allows me to print one time again.

Any ideas? TIA.

Does it say
```
Idle - sendin data to printer
```?

I can print one page/work just fine, after that I usually get blank pages or some figures on one line. So this is a common phenomena, I guess. Restarting (power on/off) printer allows me to print again with succesfull, after that it's blank pages again

---

### Post by tweedledee on 2012-05-10
ALL: Clearly something in Ubuntu 12.04 is causing widespread problems, and it isn't necessarily as simple as the CUPS update.  I strongly suspect this problem is beyond what I can diagnose and fix, although (as mentioned before) I will attempt to work on this as soon as I have any spare time.  (Unfortunately, that may have just been delayed until June.)

What I strongly suggest is that someone (or several someones) open bug reports on Launchpad regarding the various issues that have been raised.  It may be that all this has nothing at all to do with the Samsung driver, and is affecting many other printers - but you won't find that information here if so.

If individuals are feeling slightly more brave, you can also test the latest driver version from Samsung, installed using the Samsung installer.  I have only looked briefly at it, and do not yet know what the differences are.  You can find it by downloading the driver for the ML-2165w printer from the Samsung US website.  There may be one or two other printers that provide that version as the download link, but I haven't found any if so.

In the meantime, feel free to continue posting in this thread, but understand that doing so may not generate any response or fix in the short term.  The exchange of ideas in this thread has certainly been useful before, so I am not suggesting that everyone stop sharing or trying to find solutions.

---

### Post by Yetisaurus Akjas on 2012-05-11
Thank you for your answer, tweedledee. 

The way I see things, there are far more important problems around (compared to mine) and the Samsung multifunctional I mentioned doesn't seem to be used often enough to consider solving my problem and posting about it. :)) Although I will not continue to try to solve it, as I've replaced that SCX-4623 (with an HP 1132 MFP that works perfectly - including the sharing of the scanning services through the network), I will keep in mind your directions for future printing problems. 

Regards. :)

---

### Post by uhappo on 2012-05-11
> **tweedledee said:**
> 
If individuals are feeling slightly more brave, you can also test the latest driver version from Samsung, installed using the Samsung installer.  I have only looked briefly at it, and do not yet know what the differences are.  You can find it by downloading the driver for the ML-2165w printer from the Samsung US website.  There may be one or two other printers that provide that version as the download link, but I haven't found any if so.


I was able to print two operations using this latest 1.01-driver!!! So, I guess there's hope..

---

### Post by johnfrith on 2012-05-11
> **tweedledee said:**
>  I will attempt to work on this as soon as I have any spare time.  (Unfortunately, that may have just been delayed until June.)
Appreciate taking time to reply. My device is not multifunction, so I didn't think it was the same problem as those with multifunction were reporting, but maybe it is.

> **tweedledee said:**
> If individuals are feeling slightly more brave, you can also test the latest driver version from Samsung, installed using the Samsung installer.
I did consider this, but wondered if I should try and undo the install from the 1st page of this thread first? If yes, any suggestions on how I do it? I can use terminal, but need things spelling out.

Anyone have feedback on whether the Samsung installer resolves these problems?

uhappo: I don't get any kind of message re the printing. All I get is the printer icon for a few seconds, which I assume indicates it's printing, which disappears at the same time the job disappears from the print queue.

---

### Post by uhappo on 2012-05-11
@*johnfrith:

I'd say try to uninstall previous driver and try the new driver!

---

### Post by Yetisaurus Akjas on 2012-05-14
> **tweedledee said:**
> This could be a lot of different things.



Thank you for your answer, tweedledee. 

The way I see things, there are far more important problems around  (compared to mine) and the Samsung multifunctional I mentioned doesn't  seem to be used often enough to consider solving my problem and posting  about it. :smile:)  Although I will not continue to try to solve it, as I've replaced that  SCX-4623 (with an HP 1132 MFP that works perfectly - including the  sharing of the scanning services through the network), I will keep in  mind your directions for future printing problems. 

Regards. :smile:

---

### Post by scouser73 on 2012-05-14
The advice I followed for installing my Samsung Printer can be found here; [[COLOR="Red"]**Easy Linux Tips: Samsung Printers**[/COLOR]]("https://sites.google.com/site/easylinuxtipsproject/samsungprinters")

There's no need to add a repository, just download the Unified Driver from Samsung & copy and paste two commands into the Terminal.

---

### Post by tweedledee on 2012-05-15
I have done some investigating on the newest driver version from Samsung.  It appears to be completely rebuilt, apparently using a somewhat more modern system but still dependent on some very old libraries.  There are a number of subtle changes that will affect how I have to package everything, and I haven't worked through the implications of those yet (for example, all the PPD printer instruction files are renamed, so anyone updating the packages would end up having to reconfigure all printers if I simply update the driver versions).  It appears that the newest driver should work with any printer, but I can't be sure yet what surprises may be store.

Therefore, I will try to package it up soon (1-2 weeks), but will do so using new package names to avoid conflicts, and I need to think about the best way to handle the transition.

If you would like to test the new version in the meantime (only recommended for those having serious problems at the moment or those can follow the manual uninstall instructions on my website), the multifunction printer that has the newest driver is the SCX-3405FW, and you can get it here: [http://www.samsung.com/us/support/owners/product/SCX-3405FW/XAA](http://www.samsung.com/us/support/owners/product/SCX-3405FW/XAA)

It appears that the installer routine has been improved considerably, but it will still litter your system with several old libraries that will never be uninstalled (see the website regarding uninstalling version 3, the issues with the version 4 driver are identical).  Kind of silly, actually - the new installer has a package checking routine that looks for some packages, but they still don't check for the library files.  If they did that, and pushed this version of the driver out to all their printer download sections, there is a chance my repository would truly be unnecessary.

---

### Post by vargax on 2012-05-15
I have a SCX-4728FD working in 12.04... Right now I'm using it with the Generic PCL Laser Printer driver (you can find it under Generic in the driver picker dialog). You must also select 600dpi resolution in Printer Options. 

Print quality is not as good as the Samsung driver, but at least the machine works and doesn't write crazy things.

---

### Post by thatsallurspaceships on 2012-05-16
Following the guide on setting up foo2qpdl and the newest driver made it possible to get the 300-CPL working it didn't work with spliX or 2.0.0 driver. Only foo2qpdl with ./getweb 300 gives you the option to select the working foomatic fooqpdl driver all others are failing in not sending data or idleing or giving errors.

---

### Post by b1b1 on 2012-05-19
> **tweedledee said:**
> ALL: Clearly something in Ubuntu 12.04 is causing widespread problems, and it isn't necessarily as simple as the CUPS update.  I strongly suspect this problem is beyond what I can diagnose and fix, although (as mentioned before) I will attempt to work on this as soon as I have any spare time.  (Unfortunately, that may have just been delayed until June.)


**NOTE: I've got a better solution to this here: [http://ubuntuforums.org/showpost.php?p=11965390&postcount=952](http://ubuntuforums.org/showpost.php?p=11965390&postcount=952)**

I've just had a bit of a breakthrough with my Samsung SCX-4825FN on Ubuntu 12.04 and CUPS-1.5.0 (built from source). **Normal printing from desktop apps seems to work fine. CUPS "print test page" is still not working**, but this isn't such a big deal.

The fix: create a new "pdftops" filter which handles transparency in PDFs. After you've installed the Samsung drivers, create a new file "pdftops.sh":

```
#!/bin/sh
INFILE=${6:--}
MYDIR=`dirname $0`
pdftocairo -q -level3 -origpagesizes -ps $INFILE - | $MYDIR/pstops "$1" "$2" "$3" "$4" "$5"

```Now take a copy of the old "pdftops" and install the new one:

```
sudo mv /usr/lib/cups/filter/pdftops /usr/lib/cups/filter/pdftops.orig
sudo install -m 755 pdftops.sh /usr/lib/cups/filter/pdftops
```Replace the */usr* with */opt/cups-1.5.0* or wherever CUPS is installed.

The original pdftops was rasterising fonts (and perhaps doing something else dodgy?). The new one uses pdftocairo which seems to behave more nicely.

A bit more info here: [http://www.mail-archive.com/poppler@lists.freedesktop.org/msg06569.html](http://www.mail-archive.com/poppler@lists.freedesktop.org/msg06569.html)

**NOTE: I originally wrote that this worked with CUPS-1.5.2 -- but in fact this is still causing me problems from some PDFs.**

---

### Post by tweedledee on 2012-05-19
> **b1b1 said:**
> The fix: create a new "pdftops" filter which handles transparency in PDFs. After you've installed the Samsung drivers, create a new file "pdftops.sh":

Interesting.  I did some more searching on this, and it appears that the pdftops in CUPS 1.5.2 is causing widespread problems for many postscript printers from many manufacturers.  And that for some reason the developers are treating each case as "special" and hacking a workaround rather than addressing the underlying issue.

This also explains why only some people with Samsung printers are seeing issues, as only a few are true postscript printers.

In the short term, if you are essentially unable to print anything with CUPS 1.5.2 (Ubuntu 12.04 Precise) or it is extremely slow, and it worked fine with an earlier version, you should file a bug report on launchpad against the cups-filter package.  It is probably not an issue with the Samung driver.  The above post will probably work most of the time as a temporary fix, although hopefully the developers will resolve the issue and make the workaround unneeded.  (However, since this is not a "security" issue, it is not clear to me if the fix would be implemented in Ubuntu 12.04 - they might only implement it in 12.10.)

However, if you can print but it is sub-optimal, or print sometimes but not other times, then it may still be a Samsung issue, for which see my previous post.

---

### Post by b1b1 on 2012-05-20
> **tweedledee said:**
> This also explains why only some people with Samsung printers are seeing issues, as only a few are true postscript printers.

rastertosamsungspl takes postscript as input, at least in the ppds I've seen. You can look at:
 ```
grep rastertosamsung /etc/cups/ppd/*.ppd
```... and then rastertosamsungspl doesn't like the Postscript in some cases.

Under Ubuntu 12.04 there seem to be 3 types of problems:


[LIST]
[*]Printing problems from some applications (eg. evince) but not others. Caused by transparent PDFs. Can be fixed with a hack as above, or could be fixed by either cups-filter devs or by Samsung. See also [https://bugs.launchpad.net/ubuntu/+source/poppler/+bug/382379/comments/33](https://bugs.launchpad.net/ubuntu/+source/poppler/+bug/382379/comments/33)
[*]Some strange behaviour in CUPS-1.5.2. Can be fixed by reverting to CUPS-1.5.0, or may be fixed in the next CUPS update from Ubuntu.
[*]Other Samsung driver problems. Might be fixed by trying other releases of the drivers from Samsung.
[/LIST]

---

### Post by tweedledee on 2012-05-20
> **b1b1 said:**
> [LIST]
[*]Printing problems from some applications (eg. evince) but not others. Caused by transparent PDFs. Can be fixed with a hack as above, or could be fixed by either cups-filter devs or by Samsung. See also [https://bugs.launchpad.net/ubuntu/+source/poppler/+bug/382379/comments/33](https://bugs.launchpad.net/ubuntu/+source/poppler/+bug/382379/comments/33)
[*]Some strange behaviour in CUPS-1.5.2. Can be fixed by reverting to CUPS-1.5.0, or may be fixed in the next CUPS update from Ubuntu.
[*]Other Samsung driver problems. Might be fixed by trying other releases of the drivers from Samsung.
[/LIST]

See also this bug report, which indicates that there is a possible fix for cups-filter pending and available to test for Ubuntu Precise users: [https://bugs.launchpad.net/ubuntu/+source/ghostscript/+bug/668800](https://bugs.launchpad.net/ubuntu/+source/ghostscript/+bug/668800)

---

### Post by Dr Sean on 2012-05-22
I seem to be opening Pandoras box just trying to get my computer (Ubuntu 11.10) to work my printer (Samsung SCX-4825FN)!

Can some one please direct me to an easy to understand guild as to how to install this driver?

To give you an idea of what I mean by "easy to understand":

> *Add the following line to your /etc/apt/sources.list, by editing the  file as root (or using sudo), or by using Synaptic or other GUI to add a  repository: *

1. "[I]Add the following line to your /etc/apt/sources.list,"
[/I]I found the file but have no idea how to actually "add the line". Plus I'm not 100% sure what the line is? Is it the address that follows?

2. "by editing the file as root (or using sudo)"
What is root? I've used the sudo command in Terminal ... do I have to use Terminal now?

3. "or by using Synaptic or other GUI to add a repository"
Synaptic and adding a repository?

When I enter this command ...
deb [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian extra... into Terminal I get:

> No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
 Command 'xdeb' from package 'xdeb' (universe)
deb: command not found

I presume I'm not to be happy with this result from the negative punchline?

Help!

---

### Post by tweedledee on 2012-05-22
> **Dr Sean said:**
> I seem to be opening Pandoras box just trying to get my computer (Ubuntu 11.10) to work my printer (Samsung SCX-4825FN)!

Can some one please direct me to an easy to understand guild as to how to install this driver?

Open a terminal and enter:
```
sudo gedit /etc/apt/sources.list
```
then type or paste:
```
deb http://www.bchemnet.com/suldr/ debian extra
```
at the end of the file.

Then save and exit, and in the terminal enter:
```
sudo wget -O - http://www.bchemnet.com/suldr/suldr.gpg | sudo apt-key add -
```

At that point, you should be able to install the packages using whatever method you prefer for installing packages (you may need to refresh the package list or run "sudo apt-get update" in a terminal first, depending on what interface you are using).

---

### Post by Dr Sean on 2012-05-23
just 2 quick questions:

1. 
When I added the address to the list I got the following response after the "sudo apt-get update":

> E: Type 'http://www.bchemnet.com/suldr/' is not known on line 61 in source list /etc/apt/sources.list
E: The list of sources could not be read.

do I need a "deb" in front of the address in the list?

2.
my preferred method of installing packages is the software centre. Will the required drivers show up there when this address is correctly entered into the list?
and if not;
do you have a recommended way to install packages?

---

### Post by tweedledee on 2012-05-23
> **Dr Sean said:**
> just 2 quick questions:

1. 
When I added the address to the list I got the following response after the "sudo apt-get update":



do I need a "deb" in front of the address in the list?

2.
my preferred method of installing packages is the software centre. Will the required drivers show up there when this address is correctly entered into the list?
and if not;
do you have a recommended way to install packages?

1. Yes, I somehow left that out.

2. I'm not sure (I haven't used Ubuntu since they introduced software center).  If not, use "sudo apt-get install samsungmfp-driver samsungmfp-scanner" in a terminal to get the basic driver and scanner components.  At that point you should be able to add the printer through the regular Ubuntu interface and use it as a scanner.

---

### Post by Dr Sean on 2012-05-23
All the above seems to have been processed but when I go to the Printing  software the printer is not recognised. I'm connected via usb. 

Could you tell me if I'm doing anything obviously wrong or/and how I can  uninstall it all and try again. I looked at your uninstall page and but  I simply don't have enough of the terminology to get anywhere!

---

### Post by tweedledee on 2012-05-24
> **Dr Sean said:**
> All the above seems to have been processed but when I go to the Printing  software the printer is not recognised. I'm connected via usb. 

Could you tell me if I'm doing anything obviously wrong or/and how I can  uninstall it all and try again. I looked at your uninstall page and but  I simply don't have enough of the terminology to get anywhere!

I'm not sure I understand.  The printer will not be automatically installed because Ubuntu does not recognize the Samsung driver automatically, so you will have to tell your computer it is there.  You will need to go to the Settings menu, then Printers or Printing, and then create a new printer, selecting the correct driver.  If you need assistance with this process, you should look for guides to installing printers under recent Ubuntu versions, because I don't know where the Unity interface puts everything.

Another option is to "sudo apt-get install samsungmfp-configurator-qt4" in the terminal, which will install Samsung's printer configuration tool and put it on some menu (where I don't know) and you can install a new printer using that.

You should not need to uninstall anything.  In the event that you do, you just need to remove the packages, replacing "install" with "remove" in the apt-get commands.

---

### Post by b1b1 on 2012-05-24
> **tweedledee said:**
> See also this bug report, which indicates that there is a possible fix for cups-filter pending and available to test for Ubuntu Precise users: [https://bugs.launchpad.net/ubuntu/+source/ghostscript/+bug/668800](https://bugs.launchpad.net/ubuntu/+source/ghostscript/+bug/668800)

I tried this but it didn't work. The printer still prints garbage.

However I've been doing some more investigation, and I've found out how to make the standard Ubuntu 12.04 CUPS install work with my SCX-4825FN:

CUPS filters a job using these processes: *pdftopdf*->*pdftops*->*rastertosamsungspl*. But both pdftopdf and pdftops cause rastertosamgungspl to print garbage.

We can bypass both these filters by creating a new filter and a new rule. Create the file pdftosamsungps.sh:

```
#!/bin/sh
INFILE=${6:--}
MYDIR=`dirname $0`
pdftocairo -q -level3 -origpagesizes -ps $INFILE - | $MYDIR/pstops "$1" "$2" "$3" "$4" "$5"
```And create the rule file samsung.convs:

```
application/pdf application/vnd.cups-postscript 10 pdftosamsungps
```Now install these files and restart CUPS:

```
sudo install -m 755 pdftosamsungps.sh /usr/lib/cups/filter/pdftosamsungps
sudo install -m 644 samsung.convs /usr/share/cups/mime/
sudo service cups restart
```I like this fix because you don't have to rebuild CUPS or change existing files.

I'll do some more investigating of pdftopdf and pdftops, and maybe mail the cups-filters developers. But it might just be that they produce postscript just fine and there's a problem with Samsung's rastertosamsungspl.

---

### Post by Dr Sean on 2012-05-24
> **tweedledee said:**
> I'm not sure I understand.  The printer will not be automatically installed because Ubuntu does not recognize the Samsung driver automatically, so you will have to tell your computer it is there.  You will need to go to the Settings menu, then Printers or Printing, and then create a new printer, selecting the correct driver.  If you need assistance with this process, you should look for guides to installing printers under recent Ubuntu versions, because I don't know where the Unity interface puts everything.

Another option is to "sudo apt-get install samsungmfp-configurator-qt4" in the terminal, which will install Samsung's printer configuration tool and put it on some menu (where I don't know) and you can install a new printer using that.

You should not need to uninstall anything.  In the event that you do, you just need to remove the packages, replacing "install" with "remove" in the apt-get commands.
Problem solved - Thanks a huge amount for your time and knowledge.

---

### Post by tweedledee on 2012-05-28
New repository versions with many fixes coming soon!  I spent almost the entire weekend working on this, but there is still some additional testing to be done before I can safely release the packages.  In 1-2 days I am hoping to have packages that address nearly all the problems associated with Ubuntu 11.10 and 12.04, as well as some other ongoing issues dating back many months.  This includes package versions of all the widely-applicable fixes in this thread from the last six months or so.

---

### Post by tweedledee on 2012-05-28
> **b1b1 said:**
> I like this fix because you don't have to rebuild CUPS or change existing files.

So do I - I can easily package it up, and it's highly reversible if it proves to make things worse.

---

### Post by uhappo on 2012-05-28
> **tweedledee said:**
> New repository versions with many fixes coming soon!  I spent almost the entire weekend working on this, but there is still some additional testing to be done before I can safely release the packages.  In 1-2 days I am hoping to have packages that address nearly all the problems associated with Ubuntu 11.10 and 12.04, as well as some other ongoing issues dating back many months.  This includes package versions of all the widely-applicable fixes in this thread from the last six months or so.

Awesomeness!!!

---

### Post by b1b1 on 2012-05-28
> **tweedledee said:**
> So do I - I can easily package it up, and it's highly reversible if it proves to make things worse.

Indeed. I was thinking that an installable solution might provide patched PPDs which require MIME type "application/vnd.samsung-postscript". Then the conversion to this new MIME type won't interfere with the existing conversion to application/vnd.cups-postscript -- useful if you have more than one printer attached.

On the other hand, you might not like to change Samsung's PPDs. Just a thought.

---

### Post by b1b1 on 2012-05-28
I've been nosing around rastertosamsungspl trying to find out why the printer produces garbage in some cases (ie. when used with pdftopdf+pdftops from cups-filters). Here's what I found, in case someone is interested:

[LIST=1]
[*]You can put "LOG_LEVEL=9" in /tmp/rastertosamsungspl.lcf and it will dump output to /tmp/rastertosamsungspl.log
[*]It calls ghostscript to produce bitmap output: ```
gs -dNOPAUSE -dBATCH -dSAFER -q -sOutputFile=- -sstdout=%stderr -sDEVICE=pbmraw -r600x600 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -dFIXEDMEDIA -
```
[*]The QPDL output can theoretically be parsed by "qpdldecode" but in practice it doesn't understand the output I'm seeing.
[/LIST]

... but I haven't had any success with understanding the problem. Ho hum.

I will post some more if I find more time to tinker with all this.

---

### Post by tweedledee on 2012-05-28
> **b1b1 said:**
> I've been nosing around rastertosamsungspl trying to find out why the printer produces garbage in some cases (ie. when used with pdftopdf+pdftops from cups-filters).

Or it could be a ghostscript bug, of which there are a great many recent ones associated with converting pdf to ps:
[http://bugs.ghostscript.com/buglist.cgi?bug_status=REOPENED&bug_status=NEW&bug_status=ASSIGNED&bug_status=UNCONFIRMED&field0-0-0=product&field0-0-1=component&field0-0-2=short_desc&field0-0-3=status_whiteboard&field0-0-4=longdesc&query_format=advanced&type0-0-0=substring&type0-0-1=substring&type0-0-2=substring&type0-0-3=substring&type0-0-4=substring&value0-0-0=pdf&value0-0-1=pdf&value0-0-2=pdf&value0-0-3=pdf&value0-0-4=pdf&order=bug_id%20DESC&query_based_on=](http://bugs.ghostscript.com/buglist.cgi?bug_status=REOPENED&bug_status=NEW&bug_status=ASSIGNED&bug_status=UNCONFIRMED&field0-0-0=product&field0-0-1=component&field0-0-2=short_desc&field0-0-3=status_whiteboard&field0-0-4=longdesc&query_format=advanced&type0-0-0=substring&type0-0-1=substring&type0-0-2=substring&type0-0-3=substring&type0-0-4=substring&value0-0-0=pdf&value0-0-1=pdf&value0-0-2=pdf&value0-0-3=pdf&value0-0-4=pdf&order=bug_id%20DESC&query_based_on=)

For a long time, an ongoing conversion bug with gs prevented SpliX from working with my printer, so not everything is necessarily the fault of the Samsung files.  (If that gs bug had not existed, it's possible this whole repository would not exist, because I would not have needed to invest the time in the Samsung driver.  The bug was finally resolved last year but I haven't gone back and tried SpliX recently.)

Regarding your prior suggestion, modifying the ppds is an interesting idea but probably not worth the effort - if someone has multiple printers connected, chances are they can print to the non-Samsung printer to deal with the problematic file and don't need the fix at all.  For now I am just packaging a variation on your bypass solution, but I'll see what feedback comes in.

---

### Post by vyvee on 2012-05-28
I just installed the samsungmfp-scanner driver on Ubuntu 12.04, and it works for my Xerox Workcentre PE220 (+ Samsung 4521F) out-of-box!

In particular, you DO NOT need to do the following 'tricks' which are required for the previous Ubuntu versions:
- Blacklist the usblp module as mentioned [here]("http://ubuntuforums.org/showpost.php?p=11462268&postcount=843"). (It's not blacklisted now!)
- Add user into the lp group.

Thanks for the work!

---

### Post by tweedledee on 2012-05-28
> **vyvee said:**
> I just installed the samsungmfp-scanner driver on Ubuntu 12.04, and it works for my Xerox Workcentre PE220 (+ Samsung 4521F) out-of-box!

In particular, you DO NOT need to do the following 'tricks' which are required for the previous Ubuntu versions:
- Blacklist the usblp module as mentioned [here]("http://ubuntuforums.org/showpost.php?p=11462268&postcount=843"). (It's not blacklisted now!)
- Add user into the lp group.

Thanks for the work!

Good news, but I can't take any credit for it - I am just starting to upload updates now, so I'm not clear on why the work-around is no longer necessary.

---

### Post by tweedledee on 2012-05-28
Updated packages will be available in a few minutes, they are uploading now.  Please read the first couple of paragraphs of the first post of the thread regarding the changes.  Most people should have a seamless update and similar or improved performance.  If you continue to have problems, please read the updated printing/scanning troubleshooting sections of the website.

If you have NEW problems due to the updates, please post here and I will try to address them.  Be advised that I only have a short window before I may be unavailable for an extended period, so post quickly if you have problems.

I am also interested in feedback on the "fix" packages, for anyone who needs to try those - these address the lack of scanner recognition in several circumstances and printing postscript conversion problems.  For various reasons, I can't actually test these, so there's a bit of faith involved in those packages working.  Ideally nobody will need those packages, but if you do decide to try them out, please let me know how it goes.

---

### Post by MyMurry on 2012-05-29
Cool, now I can print with 1200dpi (Ubuntu12.04 and ML-1675) :P

Many Thanks,

MyMurry

---

### Post by engmex on 2012-05-30
Many thanks for your hard work, it's much appreciated.  My Samsung ml-2165 is now working perfectly with version 4.

---

### Post by Dr Sean on 2012-05-30
> **b1b1 said:**
> I tried this but it didn't work. The printer still prints garbage.

However I've been doing some more investigation, and I've found out how to make the standard Ubuntu 12.04 CUPS install work with my SCX-4825FN:

CUPS filters a job using these processes: *pdftopdf*->*pdftops*->*rastertosamsungspl*. But both pdftopdf and pdftops cause rastertosamgungspl to print garbage.

We can bypass both these filters by creating a new filter and a new rule. Create the file pdftosamsungps.sh:

```
#!/bin/sh
INFILE=${6:--}
MYDIR=`dirname $0`
pdftocairo -q -level3 -origpagesizes -ps $INFILE - | $MYDIR/pstops "$1" "$2" "$3" "$4" "$5"
```And create the rule file samsung.convs:

```
application/pdf application/vnd.cups-postscript 10 pdftosamsungps
```Now install these files and restart CUPS:

```
sudo install -m 755 pdftosamsungps.sh /usr/lib/cups/filter/pdftosamsungps
sudo install -m 644 samsung.convs /usr/share/cups/mime/
sudo service cups restart
```I like this fix because you don't have to rebuild CUPS or change existing files.

I'll do some more investigating of pdftopdf and pdftops, and maybe mail the cups-filters developers. But it might just be that they produce postscript just fine and there's a problem with Samsung's rastertosamsungspl.


This looks like the solution I require.
When I print a one page I get 20 pages of singular lines of garbage.

The problem is however I don't understand your instructions.

How do I create this file? Where do I create it? 
Please be aware I'm not using 12.04 but 11.10 ... should I upgrade? I'm worried about not being able to use various software that I need should I upgrade!

---

### Post by tweedledee on 2012-05-30
> **Dr Sean said:**
> This looks like the solution I require.
When I print a one page I get 20 pages of singular lines of garbage.

The problem is however I don't understand your instructions.

How do I create this file? Where do I create it? 
Please be aware I'm not using 12.04 but 11.10 ... should I upgrade? I'm worried about not being able to use various software that I need should I upgrade!

You would need to upgrade, because the solution requires a package that is not present in 11.10.  The new samsungmfp-driver-pdf-fix package does essentially the same thing with no effort on your part, but therefore also requires a system update.

I would suggest trying one of the other alternative solutions described in the repository web pages in the meantime, and then report back if it doesn't work and you want input on a new solution without having to update your system.

---

### Post by b1b1 on 2012-05-31
> **tweedledee said:**
> I would suggest trying one of the other alternative solutions described in the repository web pages in the meantime, and then report back if it doesn't work and you want input on a new solution without having to update your system.

Agreed. I didn't experience any problems on 11.10 (although I think I had to upgrade to the newest Samsung driver). I don't know whether my fix (or something like it) would work or not, even if the package it needs were available on 11.10.

Are you getting garbage output when you try to print from certain applications? Or from all applications?

---

### Post by uhappo on 2012-05-31
Installing driver from the repo didn't fix my problems with printing. Usually I can print one session after turning printer off and the on, after that session it usually prints garbage. Also ..pdf-fix didn't have any affect, problem still exists. I usually print pdf's and from libreoffice. My printer is scx-3205 via usb

---

### Post by Dr Sean on 2012-05-31
> You would need to upgrade, because the solution requires a package that  is not present in 11.10.  The new samsungmfp-driver-pdf-fix package does  essentially the same thing with no effort on your part, but therefore  also requires a system update.

Ok, so I've updated my system (12.04)

How do I create this file and where do I put it?

I get garbage from LibreOffice Writer. Now I read the following posts and worry that I have to start over :(

---

### Post by tweedledee on 2012-06-01
> **uhappo said:**
> Installing driver from the repo didn't fix my problems with printing. Usually I can print one session after turning printer off and the on, after that session it usually prints garbage. Also ..pdf-fix didn't have any affect, problem still exists. I usually print pdf's and from libreoffice. My printer is scx-3205 via usb

I'm not sure I understand - are you saying that you could print for one session before updating, but now it always prints garbage?  Or just that nothing has changed?

Two things that probably won't help but are easy to try:
1. Remove your printer and re-install it through the printer management interface.
2. Install the samsungmfp-scanner-usblp-fix and see if that makes any difference.  (Remove it if not.)

It appears that there is still something odd with CUPS going on.

---

### Post by tweedledee on 2012-06-01
> **Dr Sean said:**
> Ok, so I've updated my system (12.04)

How do I create this file and where do I put it?

I get garbage from LibreOffice Writer. Now I read the following posts and worry that I have to start over :(

In a terminal: sudo apt-get install samsungmfp-driver-pdf-fix

(And if it doesn't help: the same except "remove" instead of "install".)

You can also try the two steps I recommended in my previous post.

---

### Post by nick4mony on 2012-06-03
> 
If you have NEW problems due to the updates

I have upgraded and my scanning has stopped working. How do I downgrade?

Why are the older files not on the repository? Where do I get a copy of the older files?

Printer model: Samsung CLX-3185FW
Connection: by Ethernet cable
Distribution: Ubuntu Lucid 10.04
Driver packages: samsungmfp-... v4.00.35-1.  The ... is: -driver-4.00.35, -common, -driver, -data, -scanner, -configurator-data, -configurator-qt4, -network.
History: 
[list][*]Installed the binary from Samsung on 15-Apr-2012.
[*]Realised what a mistake that was, and uninstalled using the instructions on the SULDR website
[*]22 April 2012: Installed these packages: -data, -driver, -scanner, -configurator-qt4, and dependencies, from the SULDR repositories. And made related changes, such as reinstall cups-bsd, ufw allow proto udp from <IPv4 printer-ip>, add all human users to 'lp'.
[*]Printing and scanning works.
[*]Did an auto upgrade about two days ago.
[/list]
Specific problem:
The window containing the scanned image does not come up when scanning has finished.

I choose Applications -> System Tools -> Samsung Unified Driver Configurator, press the Scanner button, press Properties, and put the document on the flatbed. Preview works, but when I scan ... the device scans and beeps, and the Scanning Properties window shows progress, then indicates finished, but the window that should come up with the scanned image never comes up.

---

### Post by tweedledee on 2012-06-03
> **nick4mony said:**
> I have upgraded and my scanning has stopped working. How do I downgrade?

Why are the older files not on the repository? Where do I get a copy of the older files?

Install samsungmfp-driver-3.00.90.  All relevant old driver versions are available, and if you manually select a version (as opposed to the general -driver package), future updates will not change that version.

---

### Post by pschalkx on 2012-06-03
Hi all,

Here's how I could get my new Samsung ML-2165W (part of the ML-2160 family) to be discoverable as a wireless printer in Linux:

1) Installed the printer from Windows via USB, that way I could easily configure the wireless interface from the printer.

2) The printer is not discovered by System>Printing. To solve this, after tinkering a while, here's what I could do to solve it:

2a) Installed the Samsung unified printing driver as per the start of this thread. Note: I did this mostly via Synaptic, as I prefer the GUI.
I installed the following packages via Synaptic: The different samsungmfp files v4.00 35-1, including the samsungmfp-driver 4.00.35

2b) As it still didn't work, went back to Windows, checked the properties of the printerand found it's URL, something like SEC0015.....lan. Noted this name.

2c) Back in Linux, opened system>printing, clicked on add printer, then selected AppSocket/HP Jet DIrect, copied in the name above i.e. SEC0015....lan, left the port at 9100, and it installed beautifully.

I still need to check how I can get the printer to report toner levels via Linux.

Hope this helps

Rgds

Philip

---

### Post by nick4mony on 2012-06-03
> **tweedledee said:**
> Install samsungmfp-driver-3.00.90.

**Update 1: It didn't work. Another post below**

Thanks. [s]I'll give that a go tonight in about 6 hours[/s].

Perhaps a faq ("The latest upgrade broke my system!") should be put in [http://www.bchemnet.com/suldr/questions.html](http://www.bchemnet.com/suldr/questions.html) , although the 3rd bullet point of "Selecting Packages to Install" might have helped, but I found it a bit unclear.

Also, would leaving the (older) samsungmfp-driver_3.00.90-1_all.deb at [http://www.bchemnet.com/suldr/pool/debian/extra/s/](http://www.bchemnet.com/suldr/pool/debian/extra/s/) possibly help? In Ubuntu 10.04's synaptic, there is a Force Version menu item, but in this particular case it was greyed out, and I suspect that leaving that file there would enable that and give choices according to the first star of samsungmfp-driver_*_*.deb

Finally, it seems we have yet another excuse to have a go at Samsung :-(

---

### Post by nick4mony on 2012-06-04
> **tweedledee said:**
> Install samsungmfp-driver-3.00.90.  All relevant old driver versions are available

I've tried these things:
[list]
[*]I removed samsungmfp-driver, and installed samsungmfp-driver-3.00.90. The system implicitly removed samsungmfp-driver-4.00.35.
[*]Tried scanning, same symptom. Rebooted and retried.
[*]Removed all samsungmfp-... packages and rebooted, then
[*]installed samsungmfp-driver-3.00.90, -data -scanner -configurator-qt4 and dependencies ( -common -configurator-data -network )
[*]Tried scanning, same symptom. Rebooted and retried.
[/list]

**Question ...**
When I installed the various packages on 22-23 April 2012, the versions of all packages installed were 3.00.90-2. But now, the versions of all those packages are 4.00.35. How do I get all the other 3.00.90 files back?

To be exact,
[indent]samsungmfp-configurator-data (3.00.90-2)
samsungmfp-configurator-qt4 (3.00.90-2)
samsungmfp-data (3.00.90-2)
samsungmfp-driver (3.00.90-2)
samsungmfp-network (3.00.90-2)
samsungmfp-scanner (3.00.90-2)
+ dependencies, before.[/indent]

But now
[indent]samsungmfp-common (4.00.35-1)
samsungmfp-configurator-data (4.00.35-1)
samsungmfp-configurator-qt4 (4.00.35-1)
samsungmfp-data (4.00.35-1)
samsungmfp-driver-3.00.90 (3.00.90-3)
samsungmfp-network (4.00.35-1)
samsungmfp-scanner (4.00.35-1)[/indent]

and there's more: when I run up the Unified Driver Configurator, and press on **About**, it comes up with
[indent]Common 4.00.35
Printer 4.00.25
Scanner 4.00.14
Copyright (C) **2001**[/indent]

and when I look inside the repository, there's hardly any 3.00.90 version files. But I did see these:
[indent]samsungmfp-netdiscovery_3.00.90-3_all.deb
samsungmfp-netdiscovery-oldlibc_3.00.90-3_all.deb[/indent]

Should I use these files?

I do scratch my head about that copyright date ....? Anyway, how do I get the old version files?

---

### Post by tweedledee on 2012-06-04
> **nick4mony said:**
> Perhaps a faq ("The latest upgrade broke my system!") should be put in [http://www.bchemnet.com/suldr/questions.html](http://www.bchemnet.com/suldr/questions.html) , although the 3rd bullet point of "Selecting Packages to Install" might have helped, but I found it a bit unclear.

I plan to provide a little more clarification on this issue, but there are some aspects of it (not generally worth getting into publicly) that I need to deal with first.  Suffice to say that although it may be somewhat confusing, it's less confusing than it used to be.

> **nick4mony said:**
> Also, would leaving the (older) samsungmfp-driver_3.00.90-1_all.deb at [http://www.bchemnet.com/suldr/pool/debian/extra/s/](http://www.bchemnet.com/suldr/pool/debian/extra/s/) possibly help? In Ubuntu 10.04's synaptic, there is a Force Version menu item, but in this particular case it was greyed out, and I suspect that leaving that file there would enable that and give choices according to the first star of samsungmfp-driver_*_*.deb

Actually, no.  When I first set up the repository, I tried to make that work, and the gist of it is that it adds a huge administrative headache, confuses far more people than it benefits, and can lead to problems with mixed installations with different package versions.  As it is currently configured, if you pick a specific version, it will keep that one for you, and that seems to work for nearly everyone.  Relatively few people chose a prior version, I'm not clear on what causes some people to need to and that means coming up with a perfect solution is tough.

> **nick4mony said:**
> When I installed the various packages on 22-23 April 2012, the versions of all packages installed were 3.00.90-2. But now, the versions of all those packages are 4.00.35. How do I get all the other 3.00.90 files back?

I'm guessing the only one that matters is the -network package; most of the changes associated with the versions have nothing to do with the scanning.  However, I have placed these files in [www.bchemnet.com/suldr/temp/](www.bchemnet.com/suldr/temp/), and you can download them and install.  (Both architectures are present, use whichever you need.)

I would be interested in the results of force-installing just the old -network package and changing nothing else; you'll get a "broken package" warning about the -driver-3.00.90 package, but it won't actually affect anything (the only difference between the 3.00.90-2 and 3.00.90-3 driver packages is the dependencies and relationship to other packages, all the binary bits are exactly the same).  That network piece is the only component that seems at all likely to account for your situation.  To do this, "sudo dpkg -i --force samsungmfp-network.deb" in the folder containing the .deb file.  Or equivalently to force-installing, extracting the netdiscovery file from the old package and dropping it into /opt/Samsung/mfp/bin/ in place of the newer file would work as a test (and has the advantage that if it does solve your problem, you don't have to mess with any other packages).

However, if changing that single package doesn't help, uninstall all the samsungmfp packages, put all the packages you want installed into a single folder (without any other .debs, anything else is okay), then "sudo dpkg -i *.deb" in a terminal when inside that folder; that will restore all the 3.00.90-2 versions.

> **nick4mony said:**
> and there's more: when I run up the Unified Driver Configurator, and press on **About**, it comes up with
[indent]Common 4.00.35
Printer 4.00.25
Scanner 4.00.14
Copyright (C) **2001**[/indent]

I have no idea how Samsung decides to version things.  Just ignore those.  Another bit I'm planning to add to my webpage is an attempt to explain their versioning scheme and choice of copyright dates, but "random" is probably as good an explanation as any.

What all those different versions does indicate is what I'm dealing with when I put together a "version" of the driver on the repository.  It's not just one thing, and that's part of the reason that some people claim great success when downloading "a version" direct from Samsung and other people don't - even when labeled exactly the same, the parts inside are not.  For simplicity, I track the "common" version in the package numbers, but that doesn't necessarily indicate that anything that self-reports that version is in a particular package.

> **nick4mony said:**
> and when I look inside the repository, there's hardly any 3.00.90 version files. But I did see these:
[indent]samsungmfp-netdiscovery_3.00.90-3_all.deb
samsungmfp-netdiscovery-oldlibc_3.00.90-3_all.deb[/indent]

Should I use these files?

No, they are just there for historical reasons and contain no files.

Let me know what works so that I can put together a real fix.

---

### Post by tweedledee on 2012-06-04
> **pschalkx said:**
> I still need to check how I can get the printer to report toner levels via Linux.

You may need to set up the printer as IPP or LPD for that to work, or it may just not work at all - results vary.

---

### Post by nick4mony on 2012-06-04
> **tweedledee said:**
> I would be interested in the results of force-installing just the old -network package and changing nothing else ... Or equivalently to force-installing, extracting the netdiscovery file from the old package and dropping it into /opt/Samsung/mfp/bin/ in place of the newer file

Yes, I'll try that, but a question: 
> **tweedledee said:**
> Be advised that I only have a short window before I may be unavailable for an extended period, so post quickly if you have problems.

When is this? If it's close I'll do it tonight (in about 11 hours), otherwise I'll take a rest (going into the city tonight - it's an [_LUV talk for those in Melbourne_](http://luv.asn.au/2012/06/05)) and have a crack at it tomorrow night (in 33 hours).

Nick.

---

### Post by tweedledee on 2012-06-04
> **nick4mony said:**
> Yes, I'll try that, but a question: 


When is this? If it's close I'll do it tonight (in about 11 hours), otherwise I'll take a rest (going into the city tonight - it's an [_LUV talk for those in Melbourne_](http://luv.asn.au/2012/06/05)) and have a crack at it tomorrow night (in 33 hours).

Nick.

It was a false alarm.  I expect to be able to reply promptly (within a day or so) for the near future.

---

### Post by nick4mony on 2012-06-06
> **tweedledee said:**
> I would be interested in the results of force-installing just the old -network package and changing nothing else; ... Or equivalently to force-installing, extracting the netdiscovery file from the old package and dropping it into /opt/Samsung/mfp/bin/ in place of the newer file would work as a test

I did it by extracting the netdiscovery file (3.00.90's MD5SUM: b16e68ab9bd40788962226ba9dbf0245, and for completeness 4.00.35's MD5SUM: 68d0a32771207333a61099a133cef0ce) and replacing the file, but it didn't work (same symptom persists).

> **tweedledee said:**
> However, if changing that single package doesn't help, uninstall all the samsungmfp packages, put all the packages you want installed into a single folder (without any other .debs, anything else is okay), then "sudo dpkg -i *.deb" in a terminal when inside that folder; that will restore all the 3.00.90-2 versions.

I'm willing to bet that it's something to do with the /opt/Samsung/mfp/bin/smfpscan file. So what I'll do is to replace that file next, with the 3.00.90 version, then replace other files until I reach the state I would do with a complete 3.00.90 install. That way I'll know how many files I've replaced when it starts working.

I've got all the {amd64,all}.deb files on board, but it's a bit late now, so I'll resume tomorrow.

---

### Post by Togras on 2012-06-07
Maybe I can ofer some additional informations to this theme i test now several days my clp 620ND.
I try different ways...
first i use the standart printer menu
i get 3 error messages
paper jam (there is no paper jam)
ipp-conformance-error
ipp-missing-job history
and printer does nothink

2.i try to install the Samsung Unified Printer Driver from Source
works but i wasn't able to add a printer 

3. Then i test Fedora using the first way and again the same error messages, but the funny think about this, that fedora prints it anyway (using cups 1.5.2)

4. i find this repo and try this now i was able to add the printer fine
but booth ofered drivers doesn't print ;)
the errors ipp-conformance-error ipp-missing-job history stays but no paperjam anymore

tell me if there are some ideas to solve this ;)

---

### Post by tweedledee on 2012-06-07
> **Togras said:**
> ipp-conformance-error
ipp-missing-job history

I don't think these matter.  I have recently started getting ipp-<various things> errors when I work with my printer settings (Samsung and otherwise), but they don't seem to have any effect.  Something to do with a CUPS change.

> **Togras said:**
> 4. i find this repo and try this now i was able to add the printer fine
but booth ofered drivers doesn't print ;)
the errors ipp-conformance-error ipp-missing-job history stays but no paperjam anymore

tell me if there are some ideas to solve this ;)

How is your printer connected?  If by network, try a different protocol (raw or lpd).  If USB, does the computer auto-recognize the model when you go to configure it?  If not, there is a small chance the samsungmfp-scanner-usblp-fix package might help.

You could also try configuring the printer as a generic PCL printer, or selecting the CLP-600 or CLP-610 as the model (sometimes related models work).  Another approach is to set the error policy (in the printer configuration) to "retry job" instead of "stop printer" or similar.  I use an HP printer at work that went through a period of needing this - I was constantly getting spurious errors.  Never did figure it out, and it eventually went away.  It's possible that it is actually a configuration problem with the printer itself, and reseting it to factory defaults could potentially help.

---

### Post by atz6975 on 2012-06-08
Hi,
just reporting that this worked with SCX 3405W wifi printer.
I used 4.xx driver on ubuntu 12.04 x64 Desktop
While Samsung official driver worked for printing, netdiscovery never worked (missing acces to libnetsnmp-10.so) although the file was inside /opt/Samsung/....

Am I wrong or your package doesn't provide the Samsung GUI?
It is not really necessary but I was wondering.

You might want to add this printer reference to the first post listing network printers.

Most of all , thank you very very much.

---

### Post by nick4mony on 2012-06-09
> **nick4mony said:**
> ... then replace other files until I reach the state I would do with a complete 3.00.90 install. That way I'll know how many files I've replaced when it starts working.

I've got all the {amd64,all}.deb files on board, but it's a bit late now, so I'll resume tomorrow.

I have solved this problem. It was a missing symlink, which was in samsungmfp-configurator-data_3.00.90-2_all.deb, but not in samsungmfp-configurator-data_4.00.35-1_all.deb. The symlink is
```
/usr/lib/libtiff.so.3 -> libtiff.so.4
```So I've cleaned off everything, and installed the samsungmfp-driver-4.00.35 package and associates, and then manually created the symlink.

Feels like a shaggy dog story, doesn't it?

Many thanks to tweedledee for making the old files available. And yet another mark against Samsung whose software cannot have the decency to say "Error: cannot start /opt/Samsung/mfp/bin/ImageManager (errno=???)" (which is the name of the window that wasn't coming up).

So that leaves you with two things to do:
[list=1]
[*]Remake the samsungmfp-configurator-data_4.00.35-?_all.deb file with the symlink,
[*]Re-examine the samsungmfp-driver-3.00.90_3.00.90-3_amd64.deb package dependencies ... for some reason they're dragging in 4.00.35 version files, not 3.00.90 files. This needs to be put right, so that if an upgrade breaks people's systems, and you get run over by a bus, then people have a way out.
[/list]
Detailed information: the exact packages I have installed now are
[indent]samsungmfp-common (4.00.35-1)
samsungmfp-configurator-data (4.00.35-1)
samsungmfp-configurator-qt4 (4.00.35-1)
samsungmfp-data (4.00.35-1)
samsungmfp-driver-4.00.35 (4.00.35-1)
samsungmfp-network (4.00.35-1)
samsungmfp-scanner (4.00.35-1)
[/indent]
followed by creating the symlink like this (independent of current working directory)
```
sudo ln -s libtiff.so.4 /usr/lib/libtiff.so.3
[color=green]*## and to check ...*[/color]
ls -l /usr/lib/libtiff.so.3
[color=green]*## expect this output*[/color]
lrwxrwxrwx 1 root root 12 2012-06-09 21:58 [color=aqua]/usr/lib/libtiff.so.3[/color] -> libtiff.so.4
```

---

### Post by tweedledee on 2012-06-09
> **atz6975 said:**
> Am I wrong or your package doesn't provide the Samsung GUI?
It is not really necessary but I was wondering.

The samsungmfp-configurator-qt4 package provides the Samsung GUI; it is separate from the driver because most people don't actually need the GUI.

---

### Post by tweedledee on 2012-06-09
> **nick4mony said:**
> I have solved this problem. It was a missing symlink, which was in samsungmfp-configurator-data_3.00.90-2_all.deb, but not in samsungmfp-configurator-data_4.00.35-1_all.deb. The symlink is
```
/usr/lib/libtiff.so.3 -> libtiff.so.4
```So I've cleaned off everything, and installed the samsungmfp-driver-4.00.35 package and associates, and then manually created the symlink.

Feels like a shaggy dog story, doesn't it?

Grrr..... I did a lot of testing before I removed that link, and it appeared that Samsung had finally stopped compiling with the need for it.  I must have missed this particular case, though.  The problem (and my motivation for re-evalauting whether is was necessary) is that the libtiff.so.4 keeps moving around; most people using the 3.00.90-2 package have a broken link.  And with the introduction of libtiff5, it's getting worse.  So I have a question for you: does /usr/lib/libtiff.so.4 actually exist, or did you just make a broken link?  In Debian, there has not actually been a /usr/lib/libtiff.so.4 since before I released the 3.00.90-2 packages, which suggests many/most people already had a broken link.

> **nick4mony said:**
> Many thanks to tweedledee for making the old files available. And yet another mark against Samsung whose software cannot have the decency to say "Error: cannot start /opt/Samsung/mfp/bin/ImageManager (errno=???)" (which is the name of the window that wasn't coming up).

Useful to know.

> **nick4mony said:**
> So that leaves you with two things to do:
[list=1]
[*]Remake the samsungmfp-configurator-data_4.00.35-?_all.deb file with the symlink,

If the link needs to be correct, I'm going to have to add more complexity to the packaging to get this to work.  If it just needs to "exist", even if it's broken, then the solution is simple, and I can get it uploaded right away.

> **nick4mony said:**
> [*]Re-examine the samsungmfp-driver-3.00.90_3.00.90-3_amd64.deb package dependencies ... for some reason they're dragging in 4.00.35 version files, not 3.00.90 files. This needs to be put right, so that if an upgrade breaks people's systems, and you get run over by a bus, then people have a way out.

All the dependencies are correct.  *Only* the core driver is at version 3.00.90 (or .37 or .65); everything else really is 4.00.35.  I believe that your problem was just a fluke, not indicative of general problems with the upgrade process, and inherent in the all the warnings I provide about this mess.  However, I will look at adjusting dependencies so that every package is dependent on exact versions of the other packages, which would permit multiple versions co-existing in the repository.  (As long as they can't be co-installed - the troubleshooting would be exponentially more difficult, which is why I don't provide the option now.)  Versioning like that is considerably more work each time I update packages, but updates are infrequent enough that I should be able to keep up with it.

---

### Post by tweedledee on 2012-06-09
I have created a set of forums directly on the repository website, at [http://www.bchemnet.com/suldr/forum/](http://www.bchemnet.com/suldr/forum/) .   Please begin to transition to using those as a place to post for help, etc.  I will continue to monitor this thread, but it is over 5 years old and almost entirely full of information that is now irrelevant or available in a more organized fashion elsewhere, and I would like to eventually move all support away from this thread.

---

### Post by tweedledee on 2012-06-10
Updated packages are now available on the repository to address the libtiff issue.  The way they handle libtiff is the only functional change, so the vast majority of users should not notice any change from the the 4.00.35-1 packages.

---

### Post by raoulbhatia on 2012-06-11
there seems to be one bug in samsungmfp-scanner-usblp-fix: /etc/init.d/samsungmfp-usblp:

```
diff -r e66a4e171400 /etc/init.d/samsungmfp-usblp
--- /etc/init.d/samsungmfp-usblp    Mon Jun 11 13:43:05 2012 +0200
+++ /etc/init.d/samsungmfp-usblp    Mon Jun 11 13:43:26 2012 +0200
@@ -21,6 +21,7 @@
   restart)
     modprobe -r usblp
     modprobe usblp
+    ;;
   *)
     echo "Usage: samsungmfp-usblp {start|stop|restart}"
     ;;
```

---

### Post by tweedledee on 2012-06-11
> **raoulbhatia said:**
> there seems to be one bug in samsungmfp-scanner-usblp-fix: /etc/init.d/samsungmfp-usblp:

```
diff -r e66a4e171400 /etc/init.d/samsungmfp-usblp
--- /etc/init.d/samsungmfp-usblp    Mon Jun 11 13:43:05 2012 +0200
+++ /etc/init.d/samsungmfp-usblp    Mon Jun 11 13:43:26 2012 +0200
@@ -21,6 +21,7 @@
   restart)
     modprobe -r usblp
     modprobe usblp
+    ;;
   *)
     echo "Usage: samsungmfp-usblp {start|stop|restart}"
     ;;
```

I just uploaded a corrected package.

---

### Post by nick4mony on 2012-06-13
> **tweedledee said:**
> So I have a question for you: does /usr/lib/libtiff.so.4 actually exist, or did you just make a broken link?

It does exist, as another symlink to a real file as follows. 
```
$ **ls -l /usr/lib/libtiff.so.3**
lrwxrwxrwx 1 root root 12 2012-06-09 21:58 /usr/lib/libtiff.so.3 -> libtiff.so.4
$ **ls -l /usr/lib/libtiff.so.4**
lrwxrwxrwx 1 root root 16 2012-04-11 18:49 /usr/lib/libtiff.so.4 -> libtiff.so.4.3.2
$ **ls -l /usr/lib/libtiff.so.4.3.2**
-rw-r--r-- 1 root root 400592 2012-04-04 00:46 /usr/lib/libtiff.so.4.3.2
```

I must admit, I don't know the answer on how to address varying filesystem layouts. 

> **tweedledee said:**
> Grrr..... I did a lot of testing before I removed that link, and it appeared that Samsung had finally stopped compiling with the need for it *[libtiff.so.3*.  I must have missed this particular case, though.

But if I do **ldd** it lists libtiff.so.3, as follows:
```
$ **ldd /opt/Samsung/mfp/bin/ImageManager | grep tiff**
	libtiff.so.3 => /usr/lib/libtiff.so.3 (0x00007f2eddca3000)
$ **sudo rm /usr/lib/libtiff.so.3**
$ **ldd /opt/Samsung/mfp/bin/ImageManager | grep tiff**
	libtiff.so.3 => not found
[color=green]*## then put everything back*[/color]
```

It could be they've updated the 32-bit version to use this century's libraries, but left the 64-bit version to use 2-bit libraries!

---

### Post by Azdour on 2012-06-15
Hi,

In reply to post #902 and #903 there is a problem with IPP that makes it impossible to print to a networked Samsung printer. The suggested workaround is to change the connection type and not use IPP.

I've tried both 'LPD/LPR Host or Printer' or 'AppSocket/HP JetDirect' and I was able to print successfully to our clx6250 printer.

---

### Post by MFonville on 2012-06-15
> **Azdour said:**
> Hi,

In reply to post #902 and #903 there is a problem with IPP that makes it impossible to print to a networked Samsung printer. The suggested workaround is to change the connection type and not use IPP.

I've tried both 'LPD/LPR Host or Printer' or 'AppSocket/HP JetDirect' and I was able to print successfully to our clx6250 printer.

Look at this bug: [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/973270](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/973270) (there are also alike (not duplicate) bugs reported)
In the comments a developer responsible for CUPS in Ubuntu has posted a link to his PPA where he supports the 'ipp14' protocol which is the IPP implementation of CUPS 1.4.x
Using ipp14://xxxxx for the printer URL printing works perfectly again with the Samsung driver in Precise :-)

---

### Post by Azdour on 2012-06-15
Hi,

Thanks, I'm going to wait for a fix in CUPs or if I hit a problem with lpd then I will try the PPA that supports ipp14.

---

### Post by Togras on 2012-06-16
> **tweedledee said:**
> I don't think these matter.  I have recently started getting ipp-<various things> errors when I work with my printer settings (Samsung and otherwise), but they don't seem to have any effect.  Something to do with a CUPS change.



How is your printer connected?  If by network, try a different protocol (raw or lpd).  If USB, does the computer auto-recognize the model when you go to configure it?  If not, there is a small chance the samsungmfp-scanner-usblp-fix package might help.

You could also try configuring the printer as a generic PCL printer, or selecting the CLP-600 or CLP-610 as the model (sometimes related models work).  Another approach is to set the error policy (in the printer configuration) to "retry job" instead of "stop printer" or similar.  I use an HP printer at work that went through a period of needing this - I was constantly getting spurious errors.  Never did figure it out, and it eventually went away.  It's possible that it is actually a configuration problem with the printer itself, and reseting it to factory defaults could potentially help.

Thanks for your tips but it doesn't help :(
I reset also the printer...
But it stays the same, retry job doesn't help because i get the message all fine document was printed. But still no output at the printer i try all similar models :(
Now i use these gutenprint-drivers but there i can't use duplex mode :(

---

### Post by matza55 on 2012-06-26
I will also thank for the good tips! I use ```
sudo apt-get install samsungmfp-configurator-qt4
``` after "internal error-please use proper driver. The QT4 fix the thing! Hope I will remember, then installing next operatingsystem/upgrade?!  :p

---

### Post by matza55 on 2012-06-26
Have the printer-problem disapeared for you?

---

### Post by Togras on 2012-06-26
if you ask for me
no not really i can print (with a other driver package not the samsungs one)
the quality is okay but iam not able to use duplex :(

maybe a short overview what i have done
install following 
samsungmfp-data, configurator-data, driver-4.00.35.2, common, driver, scanner, network, configurator-qt4, legacy-configurator-qt4 and libtiff3-samsungmfp

after this i can add with the samsung configurator my printer (autodeteced in the network) 
but when i try to print nothink happens no error message and no print...

---

### Post by Ivan Azulgrana on 2012-07-29
Tweedledee, my printer Samsung ML-1865w work properly, and I owe it to you, thank you very much. Greetings from Argentina for a beginner in Ubuntu.

---

### Post by jmpoure on 2012-09-04
Thank you all for this great work on Samsung drivers. I am using two printers: Samsung ML-1670 and Samsung ML-1665 and they work great under my Debian station with custom DEBs. Event the PDF fix got it working!

Just one question: when trying to print to the ML-1670, it always proposes 2 side printing on a single A4. I mean that two pages are printed and I need to set manually only one page. Do you know how to fix this?

Kind regards,
Jean-Michel

---

### Post by tweedledee on 2012-09-06
> **jmpoure said:**
> Thank you all for this great work on Samsung drivers. I am using two printers: Samsung ML-1670 and Samsung ML-1665 and they work great under my Debian station with custom DEBs. Event the PDF fix got it working!

Just one question: when trying to print to the ML-1670, it always proposes 2 side printing on a single A4. I mean that two pages are printed and I need to set manually only one page. Do you know how to fix this?

Kind regards,
Jean-Michel
If you to to printer settings -> printer properties for that printer -> printer options, there is most likely a setting that says duplex or 2-sided printing or similar.  Changing it there would set the default.

---

### Post by mr.peeters@gmail.com on 2012-09-11
Hi, 

Thank you tweedledee! I bought myself a Samsung ML-2165W Printer, installed Samsung Unified Printer Driver according to your instructions.  

Now my computer seems to recognize the printer, but happily just says  'Document is Printing on ML-2160-Series' and a bit later 'Printing  Completed'. In reality however, apart from starting to blink the green  light a bit, my printer doesn't do a thing aaargh!

One weird thing maybe is that in my system settings / printers I have a printer called ML-2160-Series, but it mentions Samsung ML-2152WPS as the model...

Any help would be greatly appreciated!

Thanks a lot!
d.

---

### Post by tweedledee on 2012-09-15
> **mr.peeters@gmail.com said:**
> 
One weird thing maybe is that in my system settings / printers I have a printer called ML-2160-Series, but it mentions Samsung ML-2152WPS as the model...

Any help would be greatly appreciated!

Thanks a lot!
d.

I would try removing the printer and re-configuring it in the printer management interface.  The 2150 series is very different, so if for some reason the configuration is using that, the printer would not work.

---

### Post by Nognir on 2012-09-21
> **tweedledee said:**
> If you to to printer settings -> printer properties for that printer -> printer options, there is most likely a setting that says duplex or 2-sided printing or similar.  Changing it there would set the default.

I've got the ml-1670 as well, and it's stuck on one-sided printing. I'm using the 4.00.35-2 driver from the repos and running latest 12.04.1-x86_64

---

### Post by tweedledee on 2012-09-23
> **Nognir said:**
> I've got the ml-1670 as well, and it's stuck on one-sided printing. I'm using the 4.00.35-2 driver from the repos and running latest 12.04.1-x86_64

I am preparing new packages based on the 4.00.36 and 4.00.39 drivers.  They should be available within a week, and may solve this issue.

---

### Post by jis on 2012-10-02
> **tweedledee said:**
> I am preparing new packages based on the 4.00.36 and 4.00.39 drivers.  They should be available within a week, and may solve this issue.

I have problems with printer CLP-315W after I updated the driver lately: Update Manager offered partial upgrade for samsungmfp packages. After applying that printing does not finnish. The partial upgrade removed samsungmfp-driver package, installed samsungmfp-libmfp as new package, and updated some other samsungmfp packages. Printing images has always been very slow with these samsungmfp linux drivers, but this time I had to kill the processes that took all available CPU resources and I turned printer off. Printer may start printing poor quality image after you turn the printer back on and after that continue to pull blanks through, so you may have to turn the printer off again to continue. On my other PC I forced versions in Synaptic package manager to their "now" versions. I can't see the old version in Synaptic in the upgraded computer anymore. How to return to the better working previous state? 

BTW Can you switch wireless off from it and force it using wired network only?

---

### Post by tweedledee on 2012-10-03
> **jis said:**
> I have problems with printer CLP-315W after I updated the driver lately: Update Manager offered partial upgrade for samsungmfp packages. After applying that printing does not finnish. The partial upgrade removed samsungmfp-driver package, installed samsungmfp-libmfp as new package, and updated some other samsungmfp packages. Printing images has always been very slow with these samsungmfp linux drivers, but this time I had to kill the processes that took all available CPU resources and I turned printer off. Printer may start printing poor quality image after you turn the printer back on and after that continue to pull blanks through, so you may have to turn the printer off again to continue. On my other PC I forced versions in Synaptic package manager to their "now" versions. I can't see the old version in Synaptic in the upgraded computer anymore. How to return to the better working previous state? 

BTW Can you switch wireless off from it and force it using wired network only?

You can now use "force version" in synaptic to go back to the older packages.  However, Synaptic does not usually downgrade gracefully, so you may need to uninstall all the packages and then select the older versions to re-install.  You won't lose any settings do so.

I don't believe there is any software way of switching the wireless mode, I would assume that was limited to something directly through the hardware interface on the printer itself if it is an option.

---

### Post by jis on 2012-10-03
> **tweedledee said:**
> You can now use "force version" in synaptic to go back to the older packages.  However, Synaptic does not usually downgrade gracefully, so you may need to uninstall all the packages and then select the older versions to re-install.  You won't lose any settings do so.

I don't believe there is any software way of switching the wireless mode, I would assume that was limited to something directly through the hardware interface on the printer itself if it is an option.

Well, I removed all samsungmfp packages, and applied force version for samsungmfp-driver "4.00.35-2 (suldr)", and tried to install it, but Synaptic fails to install: > samsungmfp-driver:
 Depends: samsungmfp-driver-4.00.39 but it is not going to be installed

---

### Post by wjwh on 2012-10-03
I also have had problems after the partial upgrade offered by the Update Manager on Ubuntu 10.04.  I am using the Samsung SCX-4623F printer.  I scanned one document (using Simple Scan) immediately before the partial upgrade and another page of the same document immediately afterwards.  The first scan (A4 page size) was normal.  In the second scan the page size had changed to what I think must be Foolscap size and it cannot be changed.  Is there any way to correct this?

---

### Post by tweedledee on 2012-10-04
> **jis said:**
> Well, I removed all samsungmfp packages, and applied force version for samsungmfp-driver "4.00.35-2 (suldr)", and tried to install it, but Synaptic fails to install:

Install samsungmfp-common-4.00.35-2 first so synaptic stops trying to pull in the 4.00.39-1 version, then install the driver version you want.

---

### Post by Flanmaster on 2012-10-15
This information may already be here but rather than reading it all I am simply posting a link.

With later versions of linux/ubuntu most of the printers supported by the samsung unified printer driver are supported by default and nothing else is needed.  for usb connected computers both printing and scanning should work.   simply go into the relevant administrative/preferences/etc. for printers that is specific to your variant of ubuntu and "add printer" selecting local or network and scanning as necessary and selecting the relevant options.

If you have a networked printer then simply select the proper options and scan, then select your printer. this should enable printing. (static ip for printer works best in this scenario)

For networked printers:
To get scanning working all you have to do is (as super user) modify the "/etc/sane.d/xerox_mfp.conf" file to comment out the relevant usb and add the relevant ip address of your scanner.  this assumes you have a static ip address for your samsung printer (mine is specifically clx-3175fw) and sane/xsane installed.  here is the original link I found that gives this info that includes examples:

[http://www.pclinuxos.com/forum/index.php?topic=101096.0](http://www.pclinuxos.com/forum/index.php?topic=101096.0)

no need for installing or modifying tons of files, support. etc. real simple solutions.

If you are having trouble, perhaps try a fresh install of linux then add your printer and modify the scanning as necessary.

---

### Post by jis on 2012-10-17
> **tweedledee said:**
> Install samsungmfp-common-4.00.35-2 first so synaptic stops trying to pull in the 4.00.39-1 version, then install the driver version you want.

I did not downgrade, but re-installed the printer, and now it prints at least the ubuntu test page successfully and does not print blank pages afterwards in (L)ubuntu 12.04.

---

### Post by jis on 2012-10-17
> **jis said:**
> I did not downgrade, but re-installed the printer, and now it prints at least the ubuntu test page successfully and does not print blank pages afterwards in (L)ubuntu 12.04.

I tried the same in my notebook that has Lubuntu 11.04, but it did not succeed to print test page. Samsung-CLP-310-Series and cupsd took all available CPU resources anyway. After I killed the former, printer printed the test page followed by unlimited number of blank pages; this I terminated by switching printer power off. That is, if I used IPP or LPD connection. If I had AppSocket/JetDirect connection for the printer, I did not have to kill the process. Note that in 11.04 the printer adding wizard installs Foomatic driver by default and you have to change it manually later to use SLP-C driver in printer properties.

I don't know why this did not work better in 11.04. At least the cupsd version is different than in later releases. 
Anyway, I suppose I have to upgrade this otherwise well working release 11.04, since it is not supported anymore in next month.

---

### Post by jis on 2012-10-17
> **tweedledee said:**
> Install samsungmfp-common-4.00.35-2 first so synaptic stops trying to pull in the 4.00.39-1 version, then install the driver version you want.

I tried that. I tried installing samsungmfp-driver-4.00.35 then, but it could not install in Synaptic:
> samsungmfp-driver-4.00.35:
 Depends: samsungmfp-network but it is not going to be installed or
 	samsungmfp-network-legacy but it is not going to be installed
 Depends: samsungmfp-libmfp but it is not going to be installed
 Recommends: samsungmfp-data but it is not going to be installed


I suppose I had better try to upgrade ubuntu first and see if the up-to-date driver works there.

---

### Post by tweedledee on 2012-10-19
> **jis said:**
> I tried that. I tried installing samsungmfp-driver-4.00.35 then, but it could not install in Synaptic:


I suppose I had better try to upgrade ubuntu first and see if the up-to-date driver works there.

This happens if you do not use force version each time to install the packages you select.  If Synaptic still refuses to resolve the dependencies, you can download the 4.00.35-2 packages directly and then use dpkg -i to install them.

But, as you pointed, 11.04 is almost at end of life, so an upgrade may make sense anyway.

---

### Post by tweedledee on 2012-10-19
> **Flanmaster said:**
> With later versions of linux/ubuntu most of the printers supported by the samsung unified printer driver are supported by default and nothing else is needed.  for usb connected computers both printing and scanning should work.   simply go into the relevant administrative/preferences/etc. for printers that is specific to your variant of ubuntu and "add printer" selecting local or network and scanning as necessary and selecting the relevant options.

Theoretically, yes.  (In fact, there is a page of the website on this topic devoted specifically to the idea of how to avoid installing anything extra.)  5,000+ users of these packages, many (most?) of whom have tried the direct approach first, suggests that there are still many cases where the alternatives don't work.  The day all the printers do work with all features will be a great day, and I will happily retire the repository.

---

### Post by sufehmi on 2012-10-25
Hi there, 

First, thank you very much for making this (Samsung Unified Printer Driver) much easier for us. Your efforts are much appreciated ! 

Now, to the issue - a newbie friend of mine ended up confused trying to follow the instruction posted here. 

So here's a version of the guide, which does not need thinking :) just ability to copy-paste to the Terminal :D

```
sudo bash -c 'echo "deb http://www.bchemnet.com/suldr/ debian extra" >> /etc/apt/sources.list'

wget -O - http://www.bchemnet.com/suldr/suldr.gpg | sudo apt-key add -

sudo apt-get update

sudo apt-get install  samsungmfp-driver  samsungmfp-configurator-qt4

/opt/Samsung/mfp/bin/Configurator&
```

Hopefully someone else will find this usefull as well.

Again, thanks for making these much easier for us.


cheers, HS

---

### Post by cedric_tux on 2012-10-28
Hi tweedledee,

I'm having the same problem as wjwh with my CLX-3170 printer.
I have tried to resolve this issue by replacing both files:

libmfp.so.1.0.1
libsane-smfp.so.1.0.1

with the version from 4.00.35-1

Would it be possible to create a new package in your script to create a metapackage
samsungmfp-scanner pointing to the newest version
and a package samsungmfp-scanner-4.00.35-1 for those who having problems with the new package

---

### Post by tweedledee on 2012-10-28
> **cedric_tux said:**
> Would it be possible to create a new package in your script to create a metapackage
samsungmfp-scanner pointing to the newest version
and a package samsungmfp-scanner-4.00.35-1 for those who having problems with the new package

Possible?  Yes.  But that isn't the solution for everyone who is having trouble with the latest drivers.  Sometime in the next couple of weeks I hope to have time to address the various issues that have come up in a reasonably coherent manner.

---

### Post by sudenna on 2012-11-20
> **flinkdeldinky said:**
> I'm on an AMD64 Debian testing system.  Using your deb packages I finally got my CLP-325 printing in color as well as the Windows drivers (it least in my limited testing).

Without your packages CUPS was able to detect and install a driver that gave me full printing functionality except that printing a photo was to dark (I'd describe it as muddy) and had a weird not quite horizontal banding.

I tried to install the Samsung Driver by hand but the configurator was uncooparitive.  Although if I ran it from the shell command (I think it was install.sh) it would install automatically the correct driver.  Except it would be attached to mfp4 and that didn't work.  And there was a deamon smfpd that would eat up 25% cpu nor more or less.  I found no way to change connection and the configurator wouldn't list anything I recognized as a USB connection.

I was able to reconfigure the connection using CUPS web interface but whenever I tried to print the printer would actually print a page complaining I was using the wrong driver.

So  I uninstalled it and I installed your debs.  Basically a variation of the above.  The mfp connection thing is a real problem on my system.  Then I saw on your site that I only needed the driver and data debs.  So I uninstalled everything and reinstalled just the driver and data debs.

Cups saw the clp-325 (as usual) and when I setup the printer I chose to use the Samsung CLP-320 Series (SPL-C) driver and not the foomatic driver.  Then when I configured the driver I got different options so I knew the foomatic driver wasn't being used.  I set the color to vivid and presto!, picture perfect photo prints.

So I recommend debian testing users (and everybody else!) just use the driver and data debs.  Then go into cups and a handful of clicks later you're good to go.  Samsungs configurator doesn't offer much and cups does everything fine (I assume kde/gnome interfaces work fine as well).

Thank you!

Hi

i read in your thread that you have a CLP-325, i have the same one
what do you mean with "I set the color to vivid and presto! (in cups)"
and where do you do this?

i also whant to print in color with my printer


Thanks Ruben

---

### Post by sudenna on 2012-11-20
hi

i want to add my printer in CUPS, i chose the brand and than the model name, i take the CLP-320 series (SPL-C). Than cups ask of i whant to take the new PPD settings whit it, or use the old and the new one's togther. i chose want i want, and than i want to click on apply to go further... but it do nothing, the apply button is not click a bell
please help me, ist the finally step to have a color printer working.


Ruben

---

### Post by Nognir on 2013-01-14
[CENTER][/CENTER]> **tweedledee said:**
> I am preparing new packages based on the 4.00.36 and 4.00.39 drivers.  They should be available within a week, and may solve this issue.

Been a while since I checked the state of the drivers. But I still can't choose two-sided printing (running Ubuntu 12.04.1 amd64). It's necessary to me, is there a modification I can do to enable it?

---

### Post by tweedledee on 2013-01-19
> **Nognir said:**
> [CENTER][/CENTER]

Been a while since I checked the state of the drivers. But I still can't choose two-sided printing (running Ubuntu 12.04.1 amd64). It's necessary to me, is there a modification I can do to enable it?

Maybe.  You could modify the ppd file for your printer.  If you want to try that, it may help to also look at ppd files for related printers that support 2-sided printing to see what the particular setting is.

Even if you enable it, it may not work, but then again it might since the printer does support the mode.

---

### Post by Smika on 2013-04-08
Thanks for this great topic. It saved me a lot of time. There is only one thing that doesn't work with the SCX-4623F. I can print and scan from my PC, but is it also possible to scan from the scanner to the PC? At this moment the scanner gives the error that there is no PC available. I tried some configuration with samba, but I can't get it work. Hopefully someone here can help me or can tell me that this is not possible.

Smika

---

### Post by tweedledee on 2013-04-08
> **Smika said:**
> Thanks for this great topic. It saved me a lot of time. There is only one thing that doesn't work with the SCX-4623F. I can print and scan from my PC, but is it also possible to scan from the scanner to the PC? At this moment the scanner gives the error that there is no PC available. I tried some configuration with samba, but I can't get it work. Hopefully someone here can help me or can tell me that this is not possible.

Smika

You can try this: [http://www.bchemnet.com/suldr/forum/index.php?topic=73.0](http://www.bchemnet.com/suldr/forum/index.php?topic=73.0)

---

### Post by newbymick on 2013-04-22
> **sufehmi said:**
> Hi there, 

First, thank you very much for making this (Samsung Unified Printer Driver) much easier for us. Your efforts are much appreciated ! 

Now, to the issue - a newbie friend of mine ended up confused trying to follow the instruction posted here. 

So here's a version of the guide, which does not need thinking :) just ability to copy-paste to the Terminal :D

```
sudo bash -c 'echo "deb http://www.bchemnet.com/suldr/ debian extra" >> /etc/apt/sources.list'

wget -O - http://www.bchemnet.com/suldr/suldr.gpg | sudo apt-key add -

sudo apt-get update

sudo apt-get install  samsungmfp-driver  samsungmfp-configurator-qt4

/opt/Samsung/mfp/bin/Configurator&
```

Hopefully someone else will find this usefull as well.

Again, thanks for making these much easier for us.


cheers, HS

Thank you so much for this real easy how to.  I was about to rip the HD out of my laptop and stick my Win 7 HD back in when I found you real easy way to install the UPD. 

I've been using Linux for years (since FC1) and have always floated between Windows and Linux....most falling back on Windows when works requires it....but never bothered with getting all sudo bashing in the CLI.  I like my computing to just work and Linux really is getting there...just.    

BTW ...tried Unity.  Don't like it so went back to the old main stay Gnome with Mint Maya

---

### Post by tweedledee on 2013-05-05
FYI for anyone still using this thread instead of the [SULDR website](http://www.bchemnet.com/suldr/): I have made major changes to the repository that render all instructions in this thread obselete.  I no longer plan to read or reply to any posts in this thread; use the new forums instead.

---

### Post by Nityanandi on 2013-05-07
Grateful. Still dubious about buying [TABLE="class: my_itl-iT"]
[TR="class: my_itl-itR"]
[TD="class: dt-rowSeptr dt-alignLft my_itl-alT"][CENTER][/CENTER]
[/TD]
[TD="class: dt-rowSeptr dt-alignLft my_itl-alT"][Samsung SCX-3405F]("http://www.ebay.com.au/itm/330897471725?ssPageName=STRK:MEWAX:IT&_trksid=p3984.m1438.l2649")[/TD]
[/TR]
[/TABLE]


for upcoming Ubuntu 13.04 uprade. But grateful for ubuntu in Ubuntu. Felicitations.

---

### Post by johnaaronrose on 2013-05-15
I thought I'd post on here as well as the suld forum since this is still active & I'm using Ubuntu. I've tried to print a test page & a page using LibreOffice Writer.  Ubuntu seemed to send the pages to the printer but nothing happened.  I've tried both suld-driver-4.00.35 & suld-driver-4.00.36  (recommended driver versions on the list of supported printers) with the  same lack of success. Synaptic installed suld-driver-common-1 &  suld-driver-network-2 packages when I selected the driver.

I have  the printer connected by ethernet cable to my router. I've made the  router give the printer (i.e. its MAC address of 00:15:99:D2:24:5B with  DeviceName of SamsungPrintergives it a static ip address of 192.168.1.20  on my LAN. When I add the printer, it sees the printer as   SamsungSCX-472X (SEC001599D2245B, 192.168.1.20). I'd expect it to be  SamsungPrinter rather than SEC001599D2245B but that shouldn't make any  difference? I'm able to select either of: AppSocket/JetDirect network  printer via DNS-SD, LPD network printer via DNS-SD, IPP network printer  via DNS-SD. I've tried them all (they all lead to automatic driver  installation) with the same lack of success when printing is attempted:  also, the printer is shown with a no entry symbol presumably implying it  cannot be found. 

With my previous Brother printer, this DNS-SD  method did not work due to a bug in Ubuntu. So I tried the workaround,  which is to use the option of 'Find network printer' supplying a Device  URI of 192.168.1.20:631. This then asks me to Choose Driver with options  of Select printer from database, Provide PPD file, Search for a printer  driver to download. I selected the first option followed by Samsung followed by 472x printer but it then gave me a popup with title of  "CUPS Server Error" with details of "There was an error during the CUPS  operation: 'client-error-not-possible'".

I've just deleted the printer from Ubuntu's Printer list & installed  the Linux Unified Printer Driver as per the instructions given by  Samsung and it worked fine from the PC it's attached to by USB. However,  when I try to install it on another PC (i.e. both PC's are linked  through my router), I add the printer by using ipp with a URI of  ipp://192.168.1.11:631/printer (this being the same method that I used  for an existing HP inkjet printer that I attached to the 2nd PC by USB  & then installed it to the 1st PC) but it fails with the status  shown as "Stopped - The printer URI is incorrect or no longer exists.".

I want the Samsung printer to be accessible by both PCs. I'm at a loss what to do next.

---

### Post by spryte on 2013-05-27
> **johnaaronrose said:**
> I thought I'd post on here as well ... snip .... I'm at a loss what to do next.

I'm no expert, more linux newbie,  but what I read in your post sounded very familiar wrt my SCX-3405W. I have 3 suggestions.
1) URI of ipp://192.168.1.20           (not sure why u changed from ....20 to ...11 in your post)
2) **ipp14**://192.168.1.20 or**  ipp14**://192.168.1.11 
I never needed the ":631/printer" you could try with or without. ipp14 got me printing but not scanning, with the samsung original driver.
3) Install suld-driver-4.00.39 
Although not "a recommended driver version on the list of supported printers". I tried the recommended ones, as you did, with limited success. So I took the chance and it worked perfectly for me with "LPD network printer via DNS-SD". Which was the 1st option I tried, so I didn't bother with the rest :P

---

### Post by coffeecat on 2013-05-27
In view of this in OP:

> **tweedledee said:**
> 
**[color=blue]4 May 2013:  This thread is now completely out of date.  I no longer plan to update or maintain any aspect of it, or to reply to future posts.[/color]**

Thread closed.

*And moved to Outdated Tutorials and Tips.*

---

