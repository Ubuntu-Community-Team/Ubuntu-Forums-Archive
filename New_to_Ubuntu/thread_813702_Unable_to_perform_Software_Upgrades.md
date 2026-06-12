---
title: "Unable to perform Software Upgrades"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by electroblaze1989 on 2008-05-31
Hi.

I tried to perform the Software Upgrade for the first time after installing this OS...but i get an error message that asks me to run a command.

sudo dpkg --configire -a


but after running this command i have no idea what to do...plz help!!

---

### Post by ramjet_1953 on 2008-05-31
Hi! Welcome aboard!

All you have to do is what it says.

1. Navigate to Applications>Accessories>Terminal

2. When the terminal opens, type this in: [COLOR="Red"]sudo dpkg --configire -a[/COLOR]

If this doesn't cure the problem come back and we'll help.

Regards,
Roger :cool:

---

### Post by electroblaze1989 on 2008-05-31
well i've done that much if you will see my post above... what should i do after this??

---

### Post by Sef on 2008-05-31
Are you using Hardy, Gutsy, etc. and ubuntu, kubuntu, other?

---

### Post by NikoC on 2008-05-31
> **electroblaze1989 said:**
> well i've done that much if you will see my post above... what should i do after this??

So you've managed the dpkg part? This means you 're also able to access and work with Terminal so to update your software type in a terminal:
sudo apt-get update
sudo apt-get upgrade

This will perform a checkup on new packages and will ask you if you want to install any new ones...

Or you good go to System > Administration > Update Manager
Cheers

---

### Post by electroblaze1989 on 2008-05-31
i'm really sorry...i'm using Ubuntu for sure...but i have no idea about Hardy, Gutsy...i did this install using Wubi from Windows...i don't know what package it downloaded..

---

### Post by electroblaze1989 on 2008-05-31
> **NikoC said:**
> So you've managed the dpkg part? This means you 're also able to access and work with Terminal so to update your software type in a terminal:
sudo apt-get update
sudo apt-get upgrade

This will perform a checkup on new packages and will ask you if you want to install any new ones...

Or you good go to System > Administration > Update Manager
Cheers

dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
amey@amey-laptop:~$ 


i get this error....i know about the Update Manager but that is not working..plz help..

---

### Post by kaboodle_fish on 2008-05-31
Hi 

All you need to do is open a terminal by going to Applications then Accessories and then selecting Terminal (If you are used to Windows this looks like the command prompt)

Once there type 'sudo dpkg --configure -a' without the quote marks and you will be asked for your password. Enter this but do not worry if you see nothing on the screen as this is normal and correct.

Then press enter and once it has completed it will return back to saying amey@amey-laptop:~$ 

Then enter 'apt-get update' and press enter. This will update the repositories which is where thousands of different software packages that have been tested and approved for and by Ubuntu are stored. (This may be an over simplified explanation but it will do for now) 

Next enter 'apt-get upgrade' and this will upgrade all the software on your computer to ensure you are up to date. 

Once this is done and you are back to amey@amey-laptop:~$ just type exit and this will close the terminal for you. 

Hope this helps

---

### Post by ramjet_1953 on 2008-05-31
OK, this is what you can do next:

1. Open Nautilus in Super-user mode by typing this in a terminal:
      gksu nautilus
2. Navigate to /var/lib/dpkg/status

3. Before doing anything else make a backup of this file.

3. If you don't know the name of the offending file, you will have to patiently work your way through the list, taking note at the top of each listing, as it tells you if the package has been installed successfully.

4. When you find the offending package delete the listing.

5. Re-boot and hopefully, you will be able to now install packages.

Please note that this procedure is the last thing that you do, when nothing else works.

Please also note that playing with system files in Super User mode can potentially hose your system, so make sure you backup any file first and take it slowly and carefully.

Regards,
Roger :cool:

---

### Post by electroblaze1989 on 2008-05-31
i'll try this and tell u if i succeed..thanks guys..

---

### Post by electroblaze1989 on 2008-05-31
i am sorry i couldn't reply for some time..i was at work.. now i am getting this message..

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory


why is this happening? i am logged in as the administrator of the computer..

plz help..

---

### Post by electroblaze1989 on 2008-05-31
now i have got a blue screen in the terminal window that asks me if i want to install sun-java something...it shows me the licence agreement
what should i do to proceed? hitting Enter Key doesn't work...plz tell me..

---

### Post by Adahn on 2008-05-31
I'm having similar issues, and am getting this:


update-initramfs: Generating /boot/initrd.img-2.6.25.2
Cannot find /lib/modules/2.6.25.2
update-initramfs: failed for /boot/initrd.img-2.6.25.2

I found this in var/lib/dpkg/status

Package: linux-headers-2.6.25.2
Status: purge ok not-installed
Priority: optional
Section: devel

---

### Post by electroblaze1989 on 2008-05-31
ok i hit the enter key about 5 times in frustration and closed the terminal window, the next time i opened it and tried it again, it started downloading the updates..its still downloading now...will wait and see...

---

### Post by electroblaze1989 on 2008-05-31
okay i'm again stuck on the confuguring sun-java 6.bin screen in the terminal...how do i proceed?? plz help...

---

### Post by forestpixie on 2008-05-31
Simple once you know how - use tab to get to the ok and then enter.

Hope that helps

---

### Post by electroblaze1989 on 2008-05-31
yes...finally i have managed to complete the upgrades...a million thanks to all of you ppl...you are great..

---

