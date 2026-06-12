---
title: "New Printer Does Not Print"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by peaksails on 2012-05-10
Newbie here.

Purchased a new network HP Laserjet M1217 MFP.

The printer found the network router with no problem and Ubunty found a driver and I installed it.

Whenever I try to print something I can see the computer sent the file to the printer, however, it does not print.

I checked the print job attributes and the only thing I can see that may be the problem is the following:

/usr/lib/cups/filter/gstorastor failed

Can anyone please help me?

---

### Post by Bucky Ball on 2012-05-10
Wired or wireless? Have you tried looking in CUPS?

 [http://localhost:631/](http://localhost:631/)

The user name and password are the ones you use to login to your machine. Have you looked in 'Printing' and the properties of the printer and that is all good?

---

### Post by peaksails on 2012-05-10
It is wireless.

What am I supposed to do while in CUPS?

---

### Post by Bucky Ball on 2012-05-10
> **peaksails said:**
> It is wireless.

What am I supposed to do while in CUPS?

Add that printer. You'll need to login. You need to set an IP address on the printer and put in some other network related details. 

Once you've added and set up the details on the printer, go to 'Printing' (on the menu of your local machine, not in CUPS), right click the printer and go to 'Properties' or, if the printers not there, 'Add Printer', click 'Network Printer' and wait a bit. It should find your printer and the IP you set should be appended to its name. 

Let us know how you went.

---

### Post by agillator on 2012-05-10
I have found the best way to set up an HP printer is HPLIP. I gave rather detailed instructions here:  [http://ubuntuforums.org/showthread.php?t=1898845](http://ubuntuforums.org/showthread.php?t=1898845), message #9. A couple of things to be careful of: first, if the printer is stand alone and I assume it is if it is wireless, make sure it has a static IP; second, when you are ready to install HPLIP, purge the version Ubuntu has installed. I don't know why, but I always have trouble with it, but no trouble with the version you get from HP. When running hp-setup, be sure you look for a network printer, NOT a wireless printer. The wireless option is for something else. If it doesn't find the printer during the initial search, then check the 'manual' box and enter the printer's ip. It will find it without problem then.

---

### Post by peaksails on 2012-05-11
Okay-

I removed the existing HPLIP.

Went over and downloaded the new file as instructed.

Went to run it when I type in cd desktop all I get in response is no such file or directory.

Chromium downloaded the file in the downloads folder.

Help!

---

### Post by Shadius on 2012-05-11
> **peaksails said:**
> Okay-

I removed the existing HPLIP.

Went over and downloaded the new file as instructed.

Went to run it when I type in cd desktop all I get in response is no such file or directory.

Chromium downloaded the file in the downloads folder.

Help!

Since the downloaded file is in the Downloads folder you have to use **cd ~/Downloads** instead of **cd ~/Desktop**, or you can move the file from the Downloads folder to the Desktop and use **cd ~/Desktop**.

This link will help you install it:  [Installer Walkthrough]("http://hplipopensource.com/hplip-web/install/install/index.html")

---

### Post by peaksails on 2012-05-11
Yay!

We are up and printing!

Had to install a few times because the HP plug-in download would freeze. But it finally downloaded.

Thanks!!!!!!!!

---

### Post by Bucky Ball on 2012-05-11
Excellent. Please mark thread as 'Solved' to help others (Thread Tools, top right).

---

