---
title: "ClamAV - Viruses found: 4"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by personal-data-removed on 2008-08-14
Hi

I am running ClamAV with clamtk frontend, and after 2 hours scan, it says viruses found: 4.

?! Linux shouldnt have virus...
what is happening ?

I can see any option in the Clamtk frontend, to see or to delete the infect
files.

Is this is a bug in the anti virus ?
The 4 viruses found are false positives ?
Any one already did a full scan with the clamav/tk ?

What can i do to have sure, that my linux system as no virus ?

It would be ridiculous to go back to windows because of a ubuntu virus infestation... :confused:

HELP!

---

### Post by benny bronx on 2008-08-14
Are you sure it said virus or did it say suspicious files.  I believe clam gives that warning when unable to scan a file due to it being locked or archived.  It would help if you could post the results you received, but I would not worry about being infected.  If you feel you need an antivirus, you may want to try avast free for linux.  It is easy to install, and does not scare users with cryptic warning messages.

---

### Post by t0p on 2008-08-14
Does ClamAV say they are *Linux* viruses?  I don't use av software, but I believe ClamAV tests for Windoze viruses.  Maybe you've unwittingly downloaded some Windoze virus off the internet?

---

### Post by Thelasko on 2008-08-14
There are no viruses in the wild that can harm your Ubuntu install.  However, this doesn't mean it's impossible for there to be a virus on your machine.  You may have downloaded four viruses, but since they are written for Windows, they couldn't do anything.  If there are viruses on your machine, they are just sitting there, harmlessly.

How did you install ClamAV?  Did you use the repositories?  Did you install it in Wine? (installing it in Wine will cause false positives).

---

### Post by billgoldberg on 2008-08-14
Clam AV scans for Windows viruses.

You have downloaded those viruses.

They won't be able to actually do anything to your computer, but you could pass them to your less lucky windows using friends.

---

### Post by nicedude on 2008-08-15
From what I have read the only way a Virus can effect your Ubuntu PC in any way while you are running Ubuntu is if you opened it in wine it could infect itself onto a USB stick and then sit there dormant waiting for you to stick it in a windows box, I used to think it couldn't do anything period but then I read about a linux virus with the behavior I just mentioned. But even in that worst case it still can't effect your linux install at all.

I saw a funny statement about why linux viruses don't exist. Because its too hard to trick someone into typing "./configure" then "make" then "make install" and that rings quite true since Virus writers are trying to get control of as many boxes as possible and they know trying to target the hardest OS with the most technically skilled users is pointless when Windows has plenty of holes and its user base is non-technically oriented and therefore easy prey. 

So when your in Ubuntu you can literally forget that the word VIRUS exists ( outside of its original usage -> a problem with your body :-) ). As you can still catch the FLU while using linux :-)

---

### Post by iaculallad on 2008-08-15
You could have posted the name of the virus and the files it had infected so we could track if it really had infiltrated your Ubuntu system.

---

### Post by billgoldberg on 2008-08-15
> **iaculallad said:**
> You could have posted the name of the virus and the files it had infected so we could track if it really had infiltrated your Ubuntu system.

:lolflag:

Nice way to scare a new user.

---

### Post by personal-data-removed on 2008-08-15
Hi all
Thanks for the help.
I will answer the questions, the best i can.

"You could have posted the name of the virus and the files it had infected"
I dont know the files infected.
The Clamtk frontend only says 4 viruses found, dont show list of infected files, because of that i am suspicious of being false positives.
The Clamav virus dont specify if they are linux or windows virus, its the 1st time i used that thing, and it seams to dont have options to check those or delete the files.

"How did you install ClamAV? Did you use the repositories? Did you install it in Wine?"
I dont use Wine, i think this application its not good enough and as security issues. 
I prefer to have a 2nd partition to play games.

The repositories i tested for ClamAV are:

#Etch/volatile - CLAMAV
deb [http://ppa.launchpad.net/ubuntu-clamav/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/ubuntu-clamav/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ubuntu) hardy main
deb [http://ftp.uk.debian.org/debian-volatile](http://ftp.uk.debian.org/debian-volatile) etch/volatile main contrib  non-free
deb-src [http://ftp.uk.debian.org/debian-volatile](http://ftp.uk.debian.org/debian-volatile) etch/volatile main contrib non-free
deb [http://ftp.uk.debian.org/debian/](http://ftp.uk.debian.org/debian/) etch main contrib non-free
deb-src [http://ftp.uk.debian.org/debian/](http://ftp.uk.debian.org/debian/) etch main contrib non-free
deb [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib non-free
deb-src [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib non-free
deb [http://ftp.uk.debian.org/debian-volatile](http://ftp.uk.debian.org/debian-volatile) etch/volatile main contrib  non-free
deb-src [http://ftp.uk.debian.org/debian-volatile](http://ftp.uk.debian.org/debian-volatile) etch/volatile main contrib non-free
deb [http://www.backports.org/debian](http://www.backports.org/debian) etch-backports main contrib non-free
deb-src [http://www.backports.org/debian](http://www.backports.org/debian) etch-backports main contrib non-free

I cant install the clamav last version (0.93), but i have the virus database updated and version 0.92.

"You have downloaded those viruses"
Doubt it. I have a HD only for Linux/Ubuntu, and the only thing i downloaded to this HD was some themes, icons, backgrounds, and Freecolonization game. There is no virus on those downloaded files. 
This HD was the only one scanned with ClamAV. 

I installed ClamAV because i have downloaded a linux program (with other OS), and i detected a windows virus attached to it. But that program was deleted, and was never passed to the Ubuntu HD. So i installed clam to check if in future downloads of linux programs, they could have other win virus attached. 

The other HD i have on the machine, has other OS, and is scanned with 3 top security programs everyday, and as no virus.

"avast free for linux" (and avg)
Avasts needs a 12 months key and AVG as problems, not the ideal solution. I installed those before testing the Clamav, and i didnt found them very good, i like the AVG version for windows, but the linux version is older, i dont like how AVG uninstallation and updates work in linux. If not i would use the LinuxAVG.

"Are you sure it said virus or did it say suspicious files." 
Message at the bottom screen: Viruses found: 4

Someone told me that ClamAV gives 4 falses positives, its because of that i was asking if someone already did a full scan with it.

Those 4 virus are false positives ?

---

### Post by aysiu on 2008-08-15
> **nicedude said:**
> 
I saw a funny statement about why linux viruses don't exist. Because its too hard to trick someone into typing "./configure" then "make" then "make install" and that rings quite true since Virus writers are trying to get control of as many boxes as possible and they know trying to target the hardest OS with the most technically skilled users is pointless when Windows has plenty of holes and its user base is non-technically oriented and therefore easy prey. That's what we have gDebi for, though. If you can trick someone into downloading and double-clicking a "cool" application in the form of a .deb file, you can easily compromise her Ubuntu system. No ./configure and all that business needed at all.

---

### Post by wolfen69 on 2008-08-15
you have 4 windows virii that cant hurt your ubuntu install. carry on.

---

### Post by aimpau on 2008-08-15
If one time you open your USB stick and found these certain items:

desktop.exe
My Documents.exe
Bill Gates is my idol.msi <<<---TAKE NOTE! These kinds of files are executable nonetheless.

Just click on them and press delete. Make sure your on Linux though.

---

### Post by fatality_uk on 2008-08-15
> **aimpau said:**
> If one time you open your USB stick and found these certain items:

desktop.exe
My Documents.exe
Bill Gates is my idol.msi <<<---TAKE NOTE! These kinds of files are executable nonetheless.

Just click on them and press delete. Make sure your on Linux though.

bear in mind that a usual default Windows install might not let you view known file types

---

