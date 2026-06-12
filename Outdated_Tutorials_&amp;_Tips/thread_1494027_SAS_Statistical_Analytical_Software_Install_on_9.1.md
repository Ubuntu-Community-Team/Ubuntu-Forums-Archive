---
title: "SAS: Statistical Analytical Software Install on 9.10/ Karmic"
date: 2010-05-26
forum: Outdated Tutorials &amp; Tips
---

### Post by oaxacamatt1 on 2010-05-26
Greetings All,
I recently had the need to install **SAS 9.2 TS1M0** on my Toshiba Laptop which is running Ubuntu 9.10 and thought I would share the results.

I know SAS is not a hugely popular piece of software for 'open-sourcers' since it is so expensive BUT it ubiquitous to business and statistics people.  SAS supports SUSE and RedHat but they will help if you say you are also using OpenSuse and Fedora Core. ;))

My laptop (Satellite L305-S5919) is a unremarkable sytem, intel GL40 Express chipset, a Celeron 2.16 GHz processor (single core), 2 gig DDR2 sdram and 160 gig sata hd.  I have kept up with the bios updates and that's it.  The laptop is running Ubuntu 9.10 / Karmic with no major hitches to speak of.  I mention this only to give some of you a reference point.

**What you'll need:**
**1)** SAS tarball, sometimes called the depot (See Note A)
**2)** md5sum checksum file (Nice but not necessary)
**3)** file-roller (Nice but not necessary, however I use it here)
**4)** Java 1.5 Update 14 (See Note B)
**5)** SAS registration txt file (Integral to have)
**6)** ~7 gig hd storage: ~2.5 gig for basic installation & ~4.1 gig for the tarball.

_Note A:_ My university had SAS 9.2 TS1M0 for Linux ONLY available over the web. Therefore the biggest pain was downloading it (>4.1 gig). Since it took >60 minutes for me to download the program (from campus) it was VERY nice to have the md5sum file to compare at the end of downloading.  Interestingly, an install that includes the basic features I needed was only ~2.4 gig.

_Note B:_ [http://support.sas.com/resources/thirdpartysupport/v92/jres.html](http://support.sas.com/resources/thirdpartysupport/v92/jres.html)  - lists the current Java recommendations, for SAS.

**Instructions:**
**1)** First download Java 1.5 update 14. (See Note C)

_Note C:_ The reason I have had you install Java 1.5 Update 14 first is because SAS calls for you to point to the Java directory that you will use for the course of your work.  It was easier for me to set up SAS this way 'before the fact' than have to point SAS to Java 'after the fact'. I believe all SAS packages come with Java as mine 'came with' 1.5 Update 12 so in my case, SAS loaded ...Update 12 as default.  But changing which Java to use 'after the fact' is outside the focus of this tutorial.

**2)** sudo mkdir /usr/local/Java_1.5.14  ## Make a directory for Java

**3)** sudo mkdir /usr/local/SAS  ## Make a directory for SAS

**4)** cd /home/user/Download  ## Assuming you downloaded the Java to 'Downloads'

**5)** sudo cp jre-1_5_0_14-linux-i586.bin /usr/local/Java_1.5.14  ## Copy Java

**6)** sudo chmod +x jre-1_5_0_14-linux-i586.bin   ## **Note**: You may need to use **sudo chown 'user'...** and/or **sudo chmod 777...** depending on how you downloaded Java and its permissions. This Change permissions on Java.

**7)** ./jre-1_5_0_14-linux-i586.bin  ##  **Note**: you may need to use '**sudo**.' This installs / configures and installs Java, then you may delete the .bin files.

**8)** Type: /bin/sh  ## NOW, Make sure your default shell is BASH! 'Else it aint gonna' work. Let's test it.
***)* If you get 'illegal option -p' then you need to set up bash as your default.

**9)** ls -l /bin/sh  ##  List the directory contents of /bin/sh in long form. 

**10)** After entering this line you should get something like: '/bin/sh -> /bin/bash'

**11)** if it just ends in sh, or something like sh -> /bin/dash, you need to replace it with a symbolic link to bash. 

**12)** sudo rm /bin/sh  ## Execute these two lines 

**13)** sudo ln -s  /bin/bash  /bin/sh  ## Make a link between your shell and bash

**14)** gksu file-roller  ## type in your password and up will pop a gui for File-Roller (Here is where I break from the true techies... haha) without that password you will not be able to extract the SAS tarball into /usr/local/SAS. 

**15)** find the SAS tarball, (most probably in your /home/user/Downloads folder) highlight it and press 'OPEN'.

**16)** On file-roller press 'Extract' to the /usr/local/SAS folder you made in step three.

**17)** cd /usr/local/SAS/Depot  ## Now go back to the command line

**18)** sudo ./setup.sh   ## Watch the fireworks fly.  

**19)** At this point you should get the familiar startup splash logo. Then it will prompt you for the options you want as well as the location of our Java version 1.5 update 14 in /usr/local/Java_1.5.14.  As I said, the basic install without the Java macros (I believe) was ~2.4 gig.

**Running SAS requires a few more steps:**
**20a)** sudo mkdir /tmp   ## Make a directory as root. This is /tmp file is needed for the 'Work' folder (found inside the SAS Explorer window) that SAS uses for its temp files. 

**21a)** /usr/local/SAS/SASFoundation/SAS92/9.2/sas -work tmp  ## This command starts up SAS from the command using your /tmp file for 'Work' 

*Conversely,*

**20b)** You can start up SAS using an icon on your top panel.  Right-click on the top panel and goto 'Add to Panel...' use the 'Custom Application Launcher' and in the command line use the line above, /usr/local/SAS/SASFoundation/SAS92/9.2/sas -work tmp

**21b)** You can even find a SAS icon in the /usr/local/SAS folder if you snoop around.

**Helpful Hints For Using SAS:**
**1)**  "Lines wider than 384 will be truncated." : The largest difference between SAS for Windows and for Linux is the Program Editor limits.  For some reason (tech support didn't even elaborate, most probably historical) the program editor is limited to only 384 characters wide, while the windows version is several meg (so I have been told).  The upshot of this is that if you get code from your buddy who uses Windows you may need to shorten your code so it does not bump up against this limit.  Otherwise you will get an error message on running a SAS program of "Lines wider than 384 will be truncated."

**2)** Session Manager:  ...is a small window that allows one to 'break' into the SAS while it is running code.  This is helpful if your computer (like mine) is underpowered and freezes with very large data sets. To turn this function on go to: Tools/Options/Preferences/ tick the 'Start Session Manager'.

**3)** Insert Vs. Overtype: The default behavior for the program editor is to Overtype lines.  If you are used to the Windows version of SAS the default is Insert.  To change go to: 'Tools/Options/Preferences...' Use the 'Editing Tab' and on the bottom is the Cursor box with the two options.  Tick the box you prefer.

**4)** Line Numbers with the Program Editor: Default is to have line numbers showing on the Program Editor window, to shut this off, go to: 'Program Editor Window/Tools/Options/Program Editor' Use the Editing tab and un-check 'Display line numbers'.  WHILE you are at this page un-check "Clear text on submit'. This allows you to make small changes to the previously run program without calling it back up or re-typing it.

**5)** Keys: SAS has the ability to set your own 'Hotkeys'.  To get to this window go to: the Toolbox and on its command line type: keys  Voila'

**6)** rbrowser:  There is one last option that some might find valuable but I have found a major hinderance. I should say that I have not spent the time to get this working, since I use the SAS error messages on the Log Window.  The 'rbrowser' is primarily for server/client setups.  You can use the rbrowser to shunt error messages to firefox or Google-Chrome.  Go to Ubuntu's /Preferences/Startup Applications  in the 'Startup Programs' tab press 'Add' to the command line add '/usr/local/SAS/SASFoundation/9.2/utilities/bin/rbrowser'  Then go to: Tools/Options/Preferences...' Use the 'DMS Tab' and in the middle is the 'Documentation...' box. Here you can use 'firefox &U' or the path for Google-Chrome.

Happy Number Crunching

P.S. I am no expert but I will answer questions, IF I can.

---

### Post by useResa on 2010-06-04
Nice and clear HowTo.
My compliments!

---

### Post by oaxacamatt1 on 2010-06-30
Hi All,

As of June 30, 2010, I have gotten SAS to work on Linux Mint 9 (Isadora) and Ubuntu 10.04.  There are no modifications that I found I needed.  
Cheers,
M

---

### Post by Statistics on 2010-07-07
Dear oaxacamatt1,
 
i'm trying to install 64bit SAS9.2 to 64bit ubuntu 10.04 following your instructions but still unsuccessful.
 
The deployment wizard does not start. Nothing starts at all. Tried everything...very frustrated.
 
[EMAIL="statistics@workstation"]statistics@workstation[/EMAIL] ~/SAS92$ sudo sh ./setup.sh
Preparing the **[COLOR=#ff0000]SAS[/COLOR]** Deployment Wizard...
Launching the **[COLOR=#ff0000]SAS[/COLOR]** Deployment Wizard...
[EMAIL="statistics@workstation"]statistics@workstation[/EMAIL] ~/SAS92$
 
Any other possibilities?

---

### Post by Statistics on 2010-07-08
Oh, i forgot to mention though. i'm trying to install  **SAS 9.2 TS2M3 64bit**. 

Would it be the latest version of SAS causing the problem...

---

### Post by mörgæs on 2010-07-15
Check the thread
[http://ubuntuforums.org/showpost.php?p=8421276](http://ubuntuforums.org/showpost.php?p=8421276)
from post 51 onwards

---

### Post by oaxacamatt1 on 2010-08-02
Hey Stats,
Sorry for the long delay in getting to you.  It seems as if your CLI is using dash and not bash.  This the only thing that I can think of that makes sense.  Try the from the CLI: ls -l /bin/sh 
If you don't see: /bin/sh -> /bin/bash 
then you are not using bash and SAS will not start up.
HTH,
M

---

