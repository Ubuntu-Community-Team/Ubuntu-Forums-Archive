---
title: "Making Epson AcuLaser C3000 work in Gutsy"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by UgniusS on 2008-05-06
Hi,

I've wanted to ask a question about making it work, but until I've finished writing I've managed to fix this myself. So this is just an experience or little guide how to make it work in ubuntu gutsy (fluxbuntu). This may be applicable to other Epson printers which use avasys drivers.

By the way I'm pretty new to linux and especially ubuntu, so there may be some better ways to do one thing or another, and please do not ask me too complicated questions.

My Epson AcuLaser C3000 uses drivers from [http://avasys.jp/](http://avasys.jp/) site, I've successfully used them in Fedora 6, and 8, so I thought there would be no problem using them in ubuntu.

I assume you have cups installed, and you can access cups configuration by entering [http://localhost:631/](http://localhost:631/) in your browser.

The first thing i've bumped into was that on avasys site you can download only *.rpm or source *.tar.bz driver packages. To fix this I've simply downloaded driver cups rpm for my printer (Epson-ALC3000-filter-cups-1.0-0.i386.rpm in my case) and used:
```
$sudo alien -i Epson-ALC3000-filter-cups-1.0-0.i386.rpm
```
this installed the driver.

**EDIT:** Credits to joshtt for spotting my error. It seems you also have to download core package (Epson-ALC3000-filter-1.0-0.i386.rpm) from the same site and install it using alien. This package contains pstoalc3000.sh file mentioned later in this how-to, anyways without this file printer won't work.
Also tried this on Ubuntu Hardy Heron, I had no errors and printer worked fine just after installing core and cups rpm's from avasys.  

If you dont have alien, to get it use:
```
sudo apt-get install alien
```

Then you have to restart cups by
```
$sudo /etc/init.d/cupsys restart
```

You may now add your printer using [http://localhost:631/](http://localhost:631/) cups configuration utility (later "cups site"), I will not explain how to do this. Just make sure you select correct printer driver (<EPSON AL-C3000, ESC/PageS Filter> in my case).

You may try to print test page now, if it works you're lucky and that's it. For trouble shooting you should set tick to "Save debugging information for troubleshooting" in cups site->Administration->Basic Server Settings and press "Change Settings". Very usefull information about the troubles cups is experiencing is stored in /var/log/cups/error_log file (you can view it in cups site->Administration->View Error Log). Try to look closely at error_log file, all errors I've encountered were mentioned few lines before entry "Process dying with "Caught termination signal: Job canceled"".

As for me, the first problem was error reported about:
[Job 1] /usr/lib/cups/filter/foomatic-rip: No such file or directory
To fix this you have to download foomatic-rip and foomatic-gswrapper to /usr/bin and make symlink to foomatic-rip in /usr/lib/cups/filter/ directory.
Info here:
[http://www.linux-foundation.org/en/OpenPrinting/Database/CUPSDocumentation](http://www.linux-foundation.org/en/OpenPrinting/Database/CUPSDocumentation)
Look at 4. Install the Foomatic scripts
```
cd /usr/bin
wget http://www.linuxprinting.org/foomatic-rip
wget http://www.linuxprinting.org/foomatic-gswrapper
chmod 755 foomatic-rip foomatic-gswrapper
ln -s /usr/bin/foomatic-rip /usr/lib/cups/filter/foomatic-rip
```

The second error was complaint about permissions:
[Job 12] /bin/bash: /usr/local/bin/pstoalc3000.sh: Permission denied

To fix this you have to disable AppArmor by issuing:
```
sudo aa-complain cupsd
```
This got me past the second error.
This bug report helped: [https://bugs.launchpad.net/ubuntu/+bug/145214](https://bugs.launchpad.net/ubuntu/+bug/145214) 

The third error was something like this "arith: syntax error: "Copies""
The problem was actually with */usr/local/bin/pstoalc3000.sh* script (for other printer models script name may be different ex. *pstoalcx11.sh*). To fix it you actually have to edit the script.
```
sudo gedit /usr/local/bin/pstoalc3000.sh
```
You'll have to find all lines containing text like this "$((" and replase it with "$(($" so that for ex. "$((Copies +1))" becomes "$(($Copies +1))".
This thread helped in finding how to fix last error: [http://ubuntuforums.org/showthread.php?t=278404](http://ubuntuforums.org/showthread.php?t=278404)

After last fix my printer actually started working.

I hope this experience will help someone trying to install printer with avasys drivers.

---

### Post by joshtt on 2008-10-20
Hi UgniusS,

I followed all your directions to install the C3000 in Ubuntu 8.04.
And it got stuck at printing the test page. The debug info says:

[20/Oct/2008:10:47:26 +0200] [Job 189] Starting process 20116: "pstoalc3000.sh  PageSize=a4 XY600=4720x6776 MediaType=normal TonerSave=false InputSlot=autoselection..."
[20/Oct/2008:10:47:26 +0200] [Job 189] /bin/sh: pstoalc3000.sh: not found
[20/Oct/2008:10:47:26 +0200] [Job 189] Process 20116 ending: "pstoalc3000.sh  PageSize=a4 XY600=4720x6776 MediaType=normal TonerSave=false InputSlot=autoselection..."
[20/Oct/2008:10:47:26 +0200] [Job 189] renderer return value: 127
[20/Oct/2008:10:47:26 +0200] [Job 189] renderer received signal: 127
[20/Oct/2008:10:47:26 +0200] [Job 189] tail process done writing data to STDOUT
[20/Oct/2008:10:47:26 +0200] [Job 189] KID4 finished
[20/Oct/2008:10:47:26 +0200] [Job 189] Process dying with "Caught termination signal: Job canceled", exit stat: 0

So it seems like the pstoalc3000.sh script isn't even there ...?

Any thought on this one maybe? Would be a great help.

Thanks!

Joshtt

---

### Post by joshtt on 2008-10-20
Ok, already found the solution to my problem.

I downloaded the source files from the avasys site and those included these two files:

pstoalc3000.sh
alc3000

Copying these two to /usr/local/bin solved my problem.

Thanks UgniusS for getting me started on the right foot!

J.

---

### Post by dsozi on 2009-05-30
Hi UgniusS,

tried to follow your instructions to install the Epson AL C-3000 unter Kubuntu 9.04. But unfortunately it didn't work: After having installed the driver with
$sudo alien -i Epson-ALC3000-filter-cups-1.0-0.i386.rpmand trying to print a test page, I get the error 
**"/usr/lib/cups/filter/foomatic-rip failed"**

The error_log says:
E [30/May/2009:10:39:54 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [30/May/2009:10:40:48 +0200] Pause-Printer: Unauthorized
E [30/May/2009:10:41:02 +0200] Resume-Printer: Unauthorized
E [30/May/2009:10:41:23 +0200] PID 3823 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 11!
E [30/May/2009:10:41:23 +0200] [Job 11] Job stopped due to filter errors.
E [30/May/2009:10:44:14 +0200] CUPS-Delete-Printer: Unauthorized
E [30/May/2009:10:45:02 +0200] PID 4098 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 11!
E [30/May/2009:10:45:03 +0200] [Job 12] Job stopped due to filter errors.
E [30/May/2009:10:56:07 +0200] PID 3599 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 11!
E [30/May/2009:10:56:07 +0200] [Job 13] Job stopped due to filter errors.
I already used your tips regarding foomatic-rip and foomatic-gswrapper, both is installed and linked to /usr/bin/

Any idea what the '/usr/lib/cups/filter/foomatic crashed on signal 11' could mean?

---

