---
title: "How To Get Ndiswrapper working in Edgy Eft Release Candidate!"
date: 2006-10-28
forum: Outdated Tutorials &amp; Tips
---

### Post by TFrog on 2006-10-28
How To Get Broadcom 4318 working with Edgy Eft Release Candidate and Ndiswrapper


1.)Remove all forms and versions of ndiswrapper.  Best if you can backup your important information and start with a clean install of Edgy Eft Release Candidate.

2.)Blacklist the already installed Broadcom driver:

	Code:  echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

Also:

	Code:  sudo rmmod bcm43xx

3.)DO NOT DO:

	Code:  sudo apt-get install ndiswrapper-utils

THE PACKAGES IN THE REPOSITORIES ARE BROKEN AND IT APPEARS THE DEVELOPERS ARE NOT ATTEMPTING TO FIX THEM.

4.)DOWNLOAD NDISWRAPPER SOURCE CODE FROM HERE:

	[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

	Personally, I used 1.27 stable  if this won't compile for you with the following instructions download a different version.

5.)Compile ndiswrapper.  (The first step is where you'll run into an error with Edgy Eft.)

	Code:  cd /home/yourhomefolder/whereyoudownloadedandextractedndiswrapper	

	Code:  sudo make uninstall (must have root access or it won't delete files or folders properly)

THIS STEP IS REQUIRED!!!!!!!!!!!  This is where you'll get an error and it tells you to repeat the step as many times as necessary to get NO errors.  This will FAIL unless you:

	Code:  sudo konqueror (or your file manager as root)

Then browse your way to the folder listed below and manually DELETE it:

/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper

This is the way Ubuntu and all of it's variants structure the file folder tree and ndiswrapper will not delete the folder when issuing the &#8220;make uninstall&#8221; command.  It seems all versions of ndiswrapper including those in the repositories have an issue with this folder and it's contents which has only one file named ndiswrapper.ko appropriately.  The file is deleted but you have to manually delete the file folder.  (Note to developers:  This may be why we are having such a mess with ndiswrapper.)

6.)Now run:

	Code:  sudo make
        Code:  sudo make install

If all goes well ndiswrapper will compile and install ndiswrapper.ko into /lib/modules/2.6.17-10-generic/misc/ with no errors.

7.)NOW run:

	Code:  sudo ndiswrapper -i /home/frog/windowsdriverfolder/bcmwl5.inf

8.)Verify installation:

	Code: ndiswrapper -l

This will return:

	Code:  bcmwl5	driver installed, hardware (14E4:4324(this numbering may vary) present (alternate driver: bcm43xx)

This is OK.

9.)Now do the following step by step:

		A.)	sudo depmod -a

		B.)	sudo modprobe ndiswrapper

                C.)     sudo ndiswrapper -m

                D.)     sudo kate /etc/modules (use your chosen text editor here with root access of course.)

                E.)     add "ndiswrapper" at the end of file followed by a carriage return.

                F.)     After this it varies depending on Ubuntu variant, but for Kubuntu do:

	Code:	sudo apt-get install knetworkmanager

                G.)     If necessary reboot then open knetworkmanager and connect to your network.  It may or may not ask for WPA/WEP security.  Once you submit this then kdewalletmanager might ask you to select a password.  Do so and then you should be surfing.

AS WITH ALL HOW TO'S YOUR MILEAGE MAY VARY!!!!!!!!!!!!!!!!

---

### Post by GStubbs43 on 2006-10-28
I'm assuming this works for Edgy Eft **final** as well. Right? Anyway, I would try it... but I got my wireless working through another howto (not using ndiswrapper.) ;)

---

### Post by r76 on 2006-10-28
I did the following:

(my setup =  Dell Inspiron 8500 Laptop)
(Dell truemobile 1300 802.11g wireless mini-PCI)
(D-link D264 router)

THIS GUIDE FOR USE WITH **CLEAN INSTALL** OF EDGY AND EXISTING WIRED CONNECTION  TO GET YOU STARTED.
**[COLOR="Red"]EDIT: THIS METHOD DOES NOT WORK IN FEISTY[/COLOR]**
Takes 5 mins if you already have the replacement driver you need (see end).
If installing over an older version you will need to remove the old version as above.  Also this only works with WEP not WPA wireless signal encryption for me (I'm not that bothered), just remember to set your router to WEP and set your password first from an existing wireless connection e.g. in windows (if dual-booting) or another pc (if like me you are lucky enough) or using a wired connection.

Disable the faulty bcm43xx driver which is stopping your connection from working by blacklisting it.  To add to the kernel module blacklist:
1) Open terminal (in applications, accessories)
2) Type gedit sudo /etc/modprobe.d/blacklist
This opens the blacklist in the text editor 'gedit' with sudo (superuser) privileges.  You'll need your password.
3) Ignore the error message in terminal and go to the end of the text document you just opened and in a new line type blacklist bcm43xx
Close and save changes.  Then reboot and check that the card has now disappeared from System - Administration - Networking

Connect to internet using your wired connection.
Enable universe and multiverse repositories to get ndiswrapper:
1) in Synaptic package manager (System - Admin - Synaptic Package Manager), in settings - repositories, check all boxes (to include universe and multiverse repos), then close
2) press reload to see the additional packages you added, and then 'search' for ndis
3) mark (right-click in check-box on left-hand side of program name)
ndisgtk
ndiswrapper-utils-1.8
Most other things with ndis should be added automatically as they are 'dependencies' i.e. needed by ndisgtk.  Ndisgtk is a graphical interface for installing ndiswrapper and works for me everytime.  I'm no console purist I just want it to work!
4) apply and close synaptic

Run ndisgtk and install drivers
1) open terminal and type sudo ndisgtk
2) in the ndisgtk window load your driver (* see below) by browsing to it
3) then go to configure
4) enter your settings, remember you probably want to enter router password in ASCII (not the default hexadecimal) unless you do things that way.

At this point I disable the wired connection a) by unchecking the box and b) pulling the wire out of the back of my laptop.  Make sure you set the wifi as the active connection (mine is eth1, for example in connection properties i.e. the system tray icon)

* - I already found a driver that I know works for me from my Dapper setup (called bcmwl5.inf) which if anyone has the same setup as me I will send you.  It took me ages to identify the right one by going to the Dell website, searching on my pc, looking on the ndiswrapper wiki.  Can't remember now where I found it but all I can say is it works great, and I never had to use the broadcom cutter tool that's out there.
Useful links:
[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

edit - the broadcom 4306 driver I used was dell's driver R74092 (as suggested by linuxant [http://www.linuxant.com/driverloader/](http://www.linuxant.com/driverloader/) and downloaded from the Dell website) - I got it by unzipping the .exe in Windows and copying the files to my ubuntu laptop.  The bcmwl5.inf file I used was in folder AR)

---

### Post by hortimech on 2006-10-28
worked for me, I just had to download linux-headers and you left out a stage, after 'make' you have to 'make install'.

---

### Post by crthomas on 2006-10-28
Thank you so much.  I have installed several different Ubuntu versions, and every time I upgrade, I have had to reinstall and reconfigure ndiswrapper.  This was by far the easiest attempt.  I had to do:
sudo apt-get install linux-headers-2.6.17-10-386 linux-headers-2.6.17-10-generic
before I could do:
sudo make

Other than that, this was spot on.  Thanks again.

---

### Post by PixelCloud on 2006-10-28
the 1.8 release on the repos works

---

### Post by TFrog on 2006-10-28
To those that posted.  Sorry I didn't include the "make install" for the ndiswrapper compile step.  To the gentleman that said the repo's 1.8 worked, well it didn't work for me or others.  Of course I'm using the drivers from HP/Compaq and not any others.  I'm actually typing this on the laptop with everything working properly with the same drivers I was using in Dapper now on Edgy.  I've seen several different posts and methods on this and I only posted this for those that have tried the other methods and had not had success.

---

### Post by thedamner on 2006-11-14
I just wanted to share my experience and solution on my Acer Ferrari 4000 Laptop.  LSPCI reports my wireless card as:

06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I have been following all the guides laying around and was having no luck getting it working, regardless of the version of Ndiswrapper I used, or what version of the bcmwl5 driver.

I did manage to stumble across [this]("http://www.ubuntuforums.org/showthread.php?t=197102") forum topic, about a script designed to install ndiswrapper and set everything up for you automagically.  While this still wasn't the magic bullet, I didn't really expect it to be, there was a very important insight.  His script complains if you are not running the 2.6.17.7 kernel.  I was running 2.6.17.10, so it kept complaining.

Running with that I found some other information about people having problems with this kernel.  Further along I found the same poster explaining that his script will work if you compile the new 2.6.18 kernel, so I went ahead and followed [another guide]("http://ubuntuforums.org/showthread.php?t=217657&highlight=compile+kernel") on compiling this 2.6.18 kernel.

After having updated to the new kernel, I then compiled and installed Ndiswrapper 1.28 from source.  After which everything finally started working again.  I also noticed that my battery meter started working again as well (it wasn't showing up previously.)

I hope this helps other users still having problems.  I am very pleased to have my Ferrari up and running as normal again, I was beginning to become very frustrated at the breakage.

Cheers,
thedamner.

---

### Post by moktod on 2006-12-30
Just an FYI, I fumbled around with these instructions on my Acer Ferrari 4005 for a while.  These instructions worked fine for me ONLY after I added 'irqpoll' option to the kernel line.

-moktod

---

