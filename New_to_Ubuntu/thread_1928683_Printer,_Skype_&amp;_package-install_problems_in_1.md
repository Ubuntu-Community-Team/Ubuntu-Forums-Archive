---
title: "Printer, Skype &amp; package-install problems in 10.04"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by BlueAZ on 2012-02-20
[SIZE=3]Hi,  Thanks again for help with earlier problems!  Again, I'm running ubuntu 11.04 because installing 11.10 wouldn't work.  I still have a few nagging problems:
1)  Can't print on my Canon MP250.  It's not listed in the offered drivers thru Ubuntu, but I was able to download a driver package from Canon for Linux.  It's version 340.1, an rpm file containing 3 folders: Packages, Resources & Install.sh.   When I dbl-click on Install, it asks me if I want to Run or Run in Terminal.  Either way, nothing happens.  I've tried Open With... various apps, but can't select Synaptic PM.  In Synaptic PM, I've tried to Add the file from the folder it's in, but that doesn't work either.  How to install this driver?  Info on how to install packages in general would be helpful - ones not listed in Repositories...
2)  Have downloaded Skype several times, but it won't recognize my USB webcam.  Finally got sound settings worked out, but no video.  Cheese & Empathy use this webcam just fine.  Skype also shows no File, Edit, etc. menu in the top bar when hovered, so can't access some of its settings.
Also posted in Firefox section:  FF 10.0.2 & T-Bird both suffer from rough uneven scrolling in Ubuntu 11.04, but not when running in W-XP.  And their File, Edit, etc. menu appears, but things don't drop down when clicked, or flicker in & out, or take several clicks.
Finally, coming from Windows, I keep looking for Linux software to 'disk-clean' & 'defrag' -- do these things need doing in Ubuntu??  And anti-virus protection...  I downloaded ClamAV using Synaptic PM, but can't find it in my computer, even with Terminal command....??
Peace & Thanks!!



[/SIZE]

---

### Post by Rodney9 on 2012-02-20
Printer Help - 

[http://ubuntuforums.org/showthread.php?t=1314209&page=3](http://ubuntuforums.org/showthread.php?t=1314209&page=3)

Skype Video Help = 

[https://help.ubuntu.com/community/SkypeTroubleshooting#Video_Problems](https://help.ubuntu.com/community/SkypeTroubleshooting#Video_Problems)

You don't need defrag, Linux file systems work differently, antivirus only if your coping files to Windows.

Rodney

---

### Post by BlueAZ on 2012-02-20
Thanks, but....   I really am an Absolute Beginner per forum header.  I can't find System > Administration, even though I am logged in as Administrator...   Where is it??  Most of the rest is garbledy-gook to me!

---

### Post by BlueAZ on 2012-02-27
:confused:  Sorry, but these solutions have not worked.  I have tried everything suggested 2 or 3 times.  I still can't install my downloaded driver rpm file for my Canon mp250 printer.  in T, it just keeps saying it can't find the file, or no such file exists.  

Please help me.  Without being able to print, I'm forced to go back to Windows.  I really want Ubuntu to work.

---

### Post by Miljet on 2012-02-27
You downloaded the wrong file for Ubuntu. RPM files are for distributions that use the Red Hat Package Management system. You need to find a file with a .deb extension. Those are made for Debian based systems, like Ubuntu.

---

### Post by BlueAZ on 2012-02-29
Just in case anyone else needs the info, I finally got my Canon MP250 printer to work in Ubuntu 11.04!!!!!  Another search online found this site:   [http://www.itlure.com/2011/07/install-canon-mp250-drivers-in-linux.html](http://www.itlure.com/2011/07/install-canon-mp250-drivers-in-linux.html)     This kind person posted a video of how to install, plus a 'direct link' to the right driver.  When I clicked it, the .deb driver started downloading automatically.  When I opened it & clicked on Packages, the Ubuntu Get Software utility opened (!! a first for me !!) and actually installed it!!  Still printer didn't work, but I opened Printing in App's & when I checked Settings, & Change on driver choice, it found the installed correct driver.  I selected it, & finally was able to print a perfect test page!!!
Excuse my exuberance -- I've been working on this for months...:KS

---

