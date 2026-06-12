---
title: "HOWTO: Lexmark Z611 (and possibly other 600 series) in Hardy Heron"
date: 2008-06-27
forum: Outdated Tutorials &amp; Tips
---

### Post by chapterthree on 2008-06-27
I used the steps below to get my Lexmark Z611 working under **Ubuntu 8.04 Hardy Heron and Ubuntu 8.10 Intrepid Ibex** (I'm running 64-bit, but I don't think that should matter for these steps).

This HOWTO was derived from [http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)

**Step 1: Install Supporting Packages**
```
sudo apt-get install alien libstdc++5
```
Yes, you want to install that specific version of libstdc, even if you have a newer version.

**Step 2: Activate the USB Filesystem**
I found it was necessary to add the following line to /etc/fstab in order to get this working.  Do something like
```
sudo nano /etc/fstab
```
and add the following line
```
usbfs				/proc/bus/usb		usbfs		devgid=14 0 0
```
Then you'll want to mount the USB Filesystem
```
sudo mount usbfs
```

**Step 3: Download Driver from Lexmark**
Because websites change so much, I won't try to list/maintain a direct link to the Lexmark drivers.  You will want to grab the Red Hat Linux driver for the Z611, which should be named CJLZ600LE-CUPS-1.0-1.TAR.gz.  I would recommend creating a folder somewhere and download this file into that folder.

**Step 4: Extract and Install the Driver**
Execute the following commands exactly as listed, no modifications or tweaks should be necessary for the average user.  (You don't need to execute the comment lines however)
```
## Extracting the driver
tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz

## The shell script doesn't work out of the box
tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz

## Extracting the contents from the above command
tar -xvzf install.tar.gz

## Convert RPM to TGZ (alien may complain about --scripts not being used, you can ignore that warning)
sudo alien -t z600cups-1.0-1.i386.rpm

## Convert RPM to TGZ (alien may complain about --scripts not being used, you can ignore that warning)
sudo alien -t z600llpddk-2.0-1.i386.rpm

## Extracting the contents of the TGZ into the appropriate locations
sudo tar xvzf  z600llpddk-2.0.tgz -C / 

## Extracting the contents of the TGZ into the appropriate locations
sudo tar xvzf z600cups-1.0.tgz -C /

## Tell Ubuntu to refresh to see the new libraries
sudo ldconfig

## Move to location of PPDs
cd /usr/share/cups/model

## gunzip the PPD
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz

## The driver installation is now complete, restart cupsys
sudo /etc/init.d/cupsys restart 

```

**Step 5: Activate Printer and Driver**
Execute the following command
```
/usr/lib/cups/backend/z600
```

If all is well you should see something similar to the following:
```
user@hostname:/usr/share/cups/model$ /usr/lib/cups/backend/z600
direct z600:/dev/usb/lp0 "Lexmark  Lexmark Z600 Series" "Lexmark Printer"
```

If that doesn't work, check to see if usbfs is listed in 'cat /proc/mounts'.

**Step 6: Setup Printer**
If you are using GNOME:
[LIST=1]
[*]Click on System -> Administration -> Printing
[*]Click 'New Printer'
[*]Select 'Lexmark Printer' from the list, which should have something like 'z600:/dev/usb/lp0' for Device URI.  Click Forward.
[*]Select 'Lexmark' from the manufacturer list and click Forward.
[*]Click on 'Z600' in the model list.  Driver should show as 'Lexmark Z600 v1.0-1'
[*]Setup your preferred Printer Name, Description and Location and click Apply
[/LIST]

At this point you should have a working printer.

---

### Post by llandoverysurfer on 2008-07-02
im stuck on step 2 when i try to insert that line it comes up with i havnt got yhe right permissions can you help?

---

### Post by Eastisle on 2008-07-02
Open it with an editor under sudo level, this way you can save the changes.

Something like this (or your file location):

sudo gedit /etc/fstab/

---

### Post by chapterthree on 2008-07-02
Thanks for the feedback, added to the original post.

---

### Post by Temposs on 2008-07-10
Are you sure you meant to mount smbfs? You say you're wanting to mount **usbfs**

Also, you forgot to add an editor command for editing fstab. That's gonna be confusing to a beginner.

Is there a reason you're using alien to transform into .tgz as opposed to .deb? .deb has a more friendly native interface...

Thanks for consolidating this updated howto.

---

### Post by chapterthree on 2008-07-10
> **Temposs said:**
> Are you sure you meant to mount smbfs? You say you're wanting to mount **usbfs**

Nice catch, corrected in the original post.  Thanks!

> **Temposs said:**
> Also, you forgot to add an editor command for editing fstab. That's gonna be confusing to a beginner.

Same here, thanks!  I inserted nano into the original post as I'm guessing beginners might not be familiar with vi.

> **Temposs said:**
> Is there a reason you're using alien to transform into .tgz as opposed to .deb? .deb has a more friendly native interface...

The tutorial is based on a previous tried-and-true procedure, so I didn't deviate from it.  But in this particular case I'm not sure if building a .deb would be the correct solution?  I think the alien lines are simply meant to extract out the contents so that they can be installed in the correct location.  Much hunch is that if you made a .deb the install would not go very well (but I'm not sure).

Thanks for the feedback!

---

### Post by Temposs on 2008-07-12
I decided to give it my deb idea a shot, so I made an all inclusive [deb installer for the lexmark z600 series]("http://temposs.googlepages.com/lexmark-z600.deb").

I don't actually have this printer(though someone I know does), so I can't test it.

If someone could test the efficacy and sanity of this installer, that would be great. It approximates the steps 1 through 5 of the tutorial laid out by the OP. 

You'd still have to do step 6, which is reasonable, I think. It should add the fstab line on install and comment it out on uninstall. It should install and uninstall pretty gracefully. This is my first time making a package so tell me how I did.

It seems to work on my machine, except again I don't have the printer to see if it actually has the desired effect, which is to enable a lexmark z600 type printer to work.

Enjoy!

---

### Post by Donshyoku on 2008-07-13
I just wanted to confirm that Temposs's deb does work for the X1240.  The X1240 shares the same driver as the Z600 when it comes to printing (but not scanning) and works perfectly from install.  All you need to do is configure the driver per Temposs's instructions in GNOME and you will be set with this printer.  Thumbs up! :guitar:

---

### Post by Temposs on 2008-07-14
Thanks for testing my package, Donshyoku! You rock!

I've made a new version of the package that cleans up some formalities but is otherwise the same: [http://temposs.googlepages.com/liblexz600core0.deb](http://temposs.googlepages.com/liblexz600core0.deb)

The name of the package is changed to reflect the shared library pertaining to the z600.

---

### Post by TXMUSICTRUCKER on 2008-07-25
I was able to install drivers. At: /usr/lib/cups/backend/z600 response was: missing libstdc++.so.5 . Any help would be appreciated. I am using Unbuntu 8.04 with KDE desktop. Thanks for the help. TXMUSICTRUCKER

---

### Post by Mr Weasel on 2008-11-09
I am using Mandriva Spring 2008. This process worked like a charm for my Lexmark x1240 all-in-one printer. I had to install sudo during the process because it is not a Mandriva standard program. I also had some trouble downloading nano so I used Krusader-root-mode to add lines to fstab. the 'sudo /etc/init.d/cupsys restart' command did not work in my console so I just rebooted the system to restart cups. I then used the 'KDE print' 'add printer wizard' to install the printer. Thanks for ending a week long nightmare.

---

### Post by C0p3rn1c on 2008-12-17
Apparently this driver also works for the z510 series.
To install the lexmark z515 I used the following commands:

mkdir installfiles
cd installfiles
## Extracting the driver
tar -xvzf ../CJLZ600LE-CUPS-1.0-1.TAR.gz
## The shell script doesn't work out of the box
tail -n +143 z600cups-1.0-1.gz.sh >> install.tar.gz
## Extracting the contents from the above command
tar -xvzf install.tar.gz
## Convert RPM to TGZ (alien may complain about --scripts not being used, you can ignore that warning)
alien -t z600cups-1.0-1.i386.rpm
## Convert RPM to TGZ (alien may complain about --scripts not being used, you can ignore that warning)
alien -t z600llpddk-2.0-1.i386.rpm
## Extracting the contents of the TGZ into the appropriate locations
sudo tar xvzf z600llpddk-2.0.tgz -C /
## Extracting the contents of the TGZ into the appropriate locations
sudo tar xvzf z600cups-1.0.tgz -C /
## Tell Ubuntu to refresh to see the new libraries
sudo ldconfig
## Move to location of PPDs
cd /usr/share/cups/model
## gunzip the PPD
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz
## Installed the required library to run the z600 install application
sudo apt-get install libstdc++5
## Running the z600 install application
cd /usr/lib/cups/backend
./z600
## The driver installation is now complete, restart cupsys
sudo /etc/init.d/*cup* restart

---

### Post by milio1401 on 2009-03-13
:lolflag:  I'm using ubuntu 8.10  64-bit version and this method worked for me i was able to install  the drivers for my lexmark z611  and now it works fine,thanks a lot.
By the way the command 
## The driver installation is now complete, restart cupsys
sudo /etc/init.d/cupsys restart

didn't work for me i had  to use 
## The driver installation is now complete, restart cupsys
sudo /etc/init.d/*cup* restart

---

