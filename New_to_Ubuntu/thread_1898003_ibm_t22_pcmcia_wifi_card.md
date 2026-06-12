---
title: "ibm t22 pcmcia wifi card"
date: 2011-12-20
forum: New to Ubuntu
---

### Post by jonezy8873 on 2011-12-20
ok so i had this problem

 [http://ubuntuforums.org/showthread.php?t=1895828](http://ubuntuforums.org/showthread.php?t=1895828)
(basicly couldn't connect to WiFi)

so i installed the 3.1 kernel. now when i boot up with the wifi card in slot my computer (ibm thinkpad t22) it crashes and flashes the caps and scroll lock indicators.

if i plug the card (EDUP wireless lan card model TER/GCBA-E) it workes for a few minits then the caps/scroll lights flash and i have no responce got to do a hard reset??????????

it didnt crash before i installed that kernel.

any idears????????

---

### Post by jonezy8873 on 2011-12-21
Come on for **** sake someone should know something.

---

### Post by anewguy on 2011-12-22
(1) You only waited 12 hours????????  Check the forum code of conduct - no bumping threads (that is, you had nothing to add) before 24 hours.  Give you a hint??  Wait at least 24 hours to see if someone replies.

(2) If you haven't gotten a reply, or at least a reply that you think you want, DON'T post things like in your 2nd post.  

You'll quickly find that between (1) and your attitude and implied language in (2), help will be hard to find.

Be patient (it is a VOLUNTEER forum) and be polite.  If you can't be those 2 things, you probably don't belong on the forum.

In regards to your problem - I don't know.  I can try looking into it, but it's not going to be tonight and maybe not even tomorrow.  I have other things to do.

---

### Post by anewguy on 2011-12-23
I haven't found anything promising.  It looks like we may be able to just use ndiswrapper in this case to see if we can get it working.

IF you have a wired connection, do the following:

- open a terminal window (click on the top button of the Unity menu, then put ter in the search string and terminal will be ther)

- in that terminal window do the following:

sudo apt-get install synaptic <press enter> 

and wait for that to completely finish

- in that terminal window do the following:

sudo synaptic <press enter>

This should start the synaptic package manager.  Once started, put ndiswrapper in the search string - you want to mark the ndiswrapper-common and the ndiswrapper-utilities for installation.  Then put ndisgtk in the search string and mark ndisgtk for installation.  Click apply and wait for everything to finish.

- exit synaptic package manager

- go to COMMON STEPS further down in this post

If you do NOT have a wired connection (i.e, you have no internet connection available) then do the following:

- boot up Ubuntu as normal

- put the livecd in the drive - cancel when it says a software source has been detected

- via "Home Folder" on the Unity menu, go to the livecd and navigate to the /pool/main/n folder.  You will find 2 folders there.

- open the ndiswrapper folder

- click on the ndiswrapper-common file.  It should come up in the software center and ask if you want to install it.  Let it install and wait for it to finish, then exit the software center.

- click on the ndiswrapper-utilities file.  It should come up in the software center and ask if you want to install it.  Let it install and wait for it to finish, then exit the software center.

- navigate back to the /pool/main/n folder

- open the ndisgtk folder

- click on the ndisgtk file.  It should come up in the software center and ask if you want to install it.  Let it install and wait for it to finish, then exit the software center.

COMMON STEPS

At this point you should have used one of the above methods to install ndiswrapper and utilities as well as ndisgtk.

Now you need the Windows XP drivers for you adapter.  Specifically you need the .inf and .sys files.  Copy these to your desktop.  If the driver is a packed file or a Windows exe file, post back here with the exact name and model of your adapter and I'll try to get those files for you.

- click on the top button on the Unity menu.  Enter ndisgtk in the search string (if that doesn't return anything try putting windows wireless drivers in the search string).  Click on the returned item to start it.  Ndisgtk is a graphical front-end to ndiswrapper and makes life much easier.

- once ndisgtk has started request add or new, whatever the wording is.

- point it to the .inf file for your driver on your desktop

- click the ok,add, whatever the wording is button.  It should do it's thing and then show the network adapter.

- exit ndisgtk.

Now open network manager and be sure enable wireless is checked.  Then look to see if any wireless networks show.  If yours is there try connecting to it.

---

### Post by anewguy on 2011-12-27
If they are not already installed, you will probably need to install the following packages as well:

pcmciautls

wireless-tools

libiw30



These are normally needed to work with pcmcia cards in Ubuntu, with the wireless-tools package helping with wireless pcmcia adapters.

---

