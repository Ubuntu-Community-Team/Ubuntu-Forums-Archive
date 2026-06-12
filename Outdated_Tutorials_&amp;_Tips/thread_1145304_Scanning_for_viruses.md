---
title: "Scanning for viruses"
date: 2009-05-01
forum: Outdated Tutorials &amp; Tips
---

### Post by nucleuskore on 2009-05-01
Hi everyone
I am often plagued by complaints from Windows users about viruses, and many a time, with the current class of worms around, simply updating their antivirus and doing a full system scan isn't enough. I usually recommend that they use **UBCD4Win** to clean up their system or an antivirus running on Linux if they dual boot. 

This tutorial should enable novices to set up Avira antivirus on their Ubuntu and scan their Windows partitions or pendrives for Windows viruses.

[size=+2]Installation[/size]

*Step 1:* Download Avira for Unix from here
[http://www.free-av.com/en/download/download_servers.php](http://www.free-av.com/en/download/download_servers.php)
Download the Linux / Solaris version (Zip file)

Download the IVDF from here
[http://www.avira.com/en/support/vdf_update.html](http://www.avira.com/en/support/vdf_update.html)

*Step 2:*
Click on Applications->Accessories->Terminal

If you have downloaded it to your Desktop type
**tar zxvf Desktop/antivir** and press the TAB key to autocomplete and press ENTER

or if it's in your home folder
**tar zxvf antivir** and press the TAB key to autocomplete and press ENTER

The files will get extracted to a folder named antivir-workstation-pers-3.0.2-5
This will vary with the version of the file downloaded.

Type 

**cd antivir-** and press the TAB key to autocomplete

The shell prompt will now look something like this
neville@neville-desktop:~/antivir-workstation-pers-3.0.2-5$

*Step 3:*
Now type

**sudo ./install**

and press ENTER

You will see the following message
-----------------------------------------------------------------
Starting AVIRA AntiVir Workstation (UNIX) 3.0.2-5 installation...
 
Before installing this software, you must agree to the terms
of the license.
 
Use the arrow keys to scroll through the license. When you
are finished reading, press 'q' to exit the viewer.
 
Press <ENTER> to view the license.
------------------------------------------------------------------

Press the ENTER key slowly and repeatedly. You will see the license page scroll down. Watch the percentage completed at the bottom. When it reaches 95 % go real slow. This is to prevent the install from aborting because the default answer is n (NO)

When you reach the end this is what you'll see

--------------------------------------
AVIRA GmbH, 
  Customer Service
  Lindauer Str. 21
  D-88069 Tettnang
  Germany
 
Do you agree to the license terms? [n]
--------------------------------------
Type 

**y**

and press ENTER

The program will now install

*Step 4:*
This is the configuration step where you'll be asked a dozen questions, so look sharp :) You may simply press ENTER for the default specified in square brackets, unless I've specified otherwise.

Would you like to create a link in /usr/sbin for avupdate ? [y]
-----------------------------------------------------------------------
Would you like to setup Engine and Signature updates as cron task ? [y] 
-----------------------------------------------------------------------
Please specify the interval to check.
Recommended values are daily or 2 hours.
 
available options: d [2]

Type

**d**

and press ENTER
-----------------------------------------
What time should updates be done [00:15]?

Type the time in the specified 24 hr format. For example, I wanted to check at 8 p.m., so I typed

**20:00**

and pressed ENTER
-----------------------------------------------------------
Would you like to check for Guard updates once a week ? [n]

Type

**y**

and press ENTER 
---------------------------------------------
Would you like to install dazukofs now ? [y]
-------------------------------------------------------
Please specify at least one directory to be protected
by Guard to add in /etc/fstab : [/home]
------------------------------------------------------
Would you like to create /home/quarantine ? [y] 
-------------------------------------------------------------
Would you like to install the AVIRA Guard GNOME plugin ? [n]
--------------------------------------------------------------
Would you like to create a link in /usr/sbin for avguard ? [y]
--------------------------------------------------------------
Please specify if boot scripts should be set up.
Set up boot scripts [y]: 
--------------------------------------------------------------
Would you like to activate SMC support? [y] 
-------------------------------------------------------------
Would you like to start AVIRA Guard now? [y]

Type

**n**

and press ENTER
----------------------------------------------------------
Type

**cd ~**

and press ENTER
----------------------------------------------------------

Congratulations !! You have successfully completed the installation of Avira antivirus. Minimise the terminal to the taskbar.

[size=+2]Updating your antivirus[/size]

Extract the contents of the IVDF file you downloaded in the begining by right-clicking on it and selecting the **Extract here** option. A folder by the same name will be created. Note the vdf files there, antivir0.vdf,antivir1.vdf,antivir2.vdf and antivir3.vdf.

Maximise the terminal, and navigate to the IVDF folder. If your IVDF folder is on your Desktop and the folder name is ivdf_fusebundle_nt_en, then the comman to navigate to that will be

**cd Desktop/ivdf** and press the TAB key to autocomplete and press ENTER

If it is in your home folder then

**cd ivdf** and press the TAB key to autocomplete and press ENTER

Type

**sudo cp -v *.vdf /usr/lib/AntiVir/**

and press ENTER

Then type

**sudo avupdate --product=Guard**

and press ENTER

This will check for all updates including the scan engine. After the update you'll get back the prompt.

[b]*Note: I asked you to download the IVDF file and manually load the definitions (vdfs) and the update through the program is painfully slow. Downloading the vdfs manually also enables you to save bandwidth when installing across multiple systems. You can share your vdfs with friends too.*[b]

[size=+2]Scanning for viruses[/size]
Now for some action. The first command you'll have to issue is 

**sudo avguard start**

While this might seem odd, especially to users of Avira till the last version, this is very much a prerequisite for even a manual scan (try it without this command and see)

Now, after you get back the prompt, type

**sudo avscan -s --scan-mode=all --scan-in-archive=yes --alert-action=del *<location>***

You have to specify where you'd like to scan in <location>. 

Before you do this, try and understand what the above parameters mean. We are invoking avscan as root, and asking it to scan sub-directories (-s), scan all files (not smart scan), in archives, and delete the viruses it finds. Alternatively, you can ask for a quarantine by replacing the word **del** in **--alert-action=del** with quarantine, so that the option looks like **--alert-action=quarantine**. Files quarantined can be found in the /home/quarantine folder. If you want to specify a quarantine folder say in your home folder add this option **--quarantine-dir=<dir>** before <location> So if your quarantine folder is the folder quarantine in your home folder, and your login name is james, then the option will read as **--quarantine-dir=/home/james/quarantine**
To study all options type 
**sudo avscan --help** 
and press ENTER

Now coming back to what is to be entered in the location field. You have to enter the path to the directory you want to scan. For example, if you want to scan your pendrives, the easiest **(laziest)** would be to plug them in (as many as you want) and type the location as /media, so that the complete command looks like this

**sudo avscan -s --scan-mode=all --scan-in-archive=yes --alert-action=del /media**

This is because ALL REMOVABLE MEDIA, namely, pendrives, usb hard disks, and cd/dvds get mounted at /media
If you are an intermediate or advanced user, you can specify the complete path to the drive.

Scanning windows folders is a little different. I do not know the default mount points for windows c,d,etc. Although I do suspect it is /media
[color=red]I request other forum members to enlighten me on this one.[/color]
If it is, then the above command will not only scan your pendrive/external drives but also your windows partitions, and this will take hell of a lot of time.

So the best thing to do would be
1. Plug in your pendrive(s), hard drives
2. Note the name of the drive in the title bar of nautilus file browser as it opens automatically, does it read **disk**, or **disk-1**, or **disk-2**, etc.?
If it is, for example, if it reads **disk**, then modify the above command as 
**sudo avscan -s --scan-mode=all --scan-in-archive=yes --alert-action=del /media/disk**

If you have a pendrive/hard disk with multiple partitions, each of these will open as disk, disk-1, disk-2, etc. You'll have to scan each of the above separately by modifying the location parameter appropriately.

I hope this tutorial is simple enough to understand. Any feedback and criticism, negative or positive, is welcome.

---

