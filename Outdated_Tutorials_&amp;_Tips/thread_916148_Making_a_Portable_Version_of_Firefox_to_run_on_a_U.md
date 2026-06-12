---
title: "Making a Portable Version of Firefox to run on a USB Stick"
date: 2008-09-10
forum: Outdated Tutorials &amp; Tips
---

### Post by niccholaspage on 2008-09-10
First of all,I got these steps from my blog that no one really reads:sanassar.blogspot.com
It is very simple to make A Portable Firefox for Linux.Though This may not run so well on an old USB Stick.So lets get started.

1.Go to firefox.com and download the Linux version in a tar.gz format(Should download this automatically)

2.Create a New Directory called Firefox Portable

3.In the Firefox Portable Directory,Create a Sub Directory called AppLinux

4.Now extract the tar.bz2 and paste all of the files into the AppLinux Folder.

5.Create a .sh file in the Firefox Portable directory of the Folder.Open it with some text editing program.Put in the following code:

#!/bin/sh
check=`ps -ef|grep firefox|grep -v grep`
if [ $? -eq 0 ]
then
zenity --info --text "Please Close any Firefox Proccesses"
else
./AppLinux/run-mozilla.sh ./AppLinux/firefox-bin -profile ./Data/profile
fi



6.Now in the Firefox Portable directory,Create another Sub Directory called Data.In Data,Create a folder called profile.



7.Run the Shell Script we made.This should launch firefox and use the profile in the Data Folder.


8.Right click the shell script than click Properties.Now go to the Permissions Tab and click "Allow Executing file as a program"



Oh and by the way,The Portable Version will not run if the normal version is running.

---

### Post by niccholaspage on 2008-09-12
BUMP!

I am wondering of anyone tried this,So I can see if there is anything I can do so it is more lightweight on different USB sticks than mine.

---

### Post by eldragon on 2008-09-12
hmmm, firefox writes heavily on the hdd while loading pages, not a good idea to use a usb flash drive for the profile :(

---

### Post by triphazard on 2008-09-12
just to make the tutorial a bit more complete, you'd need to do a chmod +x on the newly created .sh file for it to do anything.

---

### Post by niccholaspage on 2008-09-12
@triphazard:I added a step
@eldragon:Well,It might not be that good with some USB Sticks,But the USB stick I had could handle it.

---

### Post by maxmilli0n on 2008-10-22
> **niccholaspage said:**
> First of all,I got these steps from my blog that no one really reads:sanassar.blogspot.com
It is very simple to make A Portable Firefox for Linux.Though This may not run so well on an old USB Stick.So lets get started.

1.Go to firefox.com and download the Linux version in a tar.gz format(Should download this automatically)

2.Create a New Directory called Firefox Portable

3.In the Firefox Portable Directory,Create a Sub Directory called AppLinux

4.Now extract the tar.bz2 and paste all of the files into the AppLinux Folder.

5.Create a .sh file in the Firefox Portable directory of the Folder.Open it with some text editing program.Put in the following code:

#!/bin/sh
check=`ps -ef|grep firefox|grep -v grep`
if [ $? -eq 0 ]
then
zenity --info --text "Please Close any Firefox Proccesses"
else
./AppLinux/run-mozilla.sh ./AppLinux/firefox-bin -profile ./Data/profile
fi



6.Now in the Firefox Portable directory,Create another Sub Directory called Data.In Data,Create a folder called profile.



7.Run the Shell Script we made.This should launch firefox and use the profile in the Data Folder.


8.Right click the shell script than click Properties.Now go to the Permissions Tab and click "Allow Executing file as a program"



Oh and by the way,The Portable Version will not run if the normal version is running.

this method worked fine for me, however there was no internet connection. on the other hand, Firefox from Ubuntu had internet connection!!

---

### Post by niccholaspage on 2008-10-23
What? You should get a connection. The only difference than My Portable Version And Mozilla's Firefox is one simple script.

---

### Post by zarnivop2 on 2011-07-11
I tried this with firefox 5. The result: Error message "profile is missing or invalid". It seems something must be in the data/profile folder for this to work?

---

