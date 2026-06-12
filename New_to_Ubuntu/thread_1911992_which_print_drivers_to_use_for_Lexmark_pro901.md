---
title: "which print drivers to use for Lexmark pro901"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by tahafisaka6 on 2012-01-19
I am trying to install the print drivers for a lexmark pro901 onto a netbook which is loaded with Ubuntu 11.10.  I looked onto Lexmarks site and found several linux drivers and trying to decide which is the one I am suppose to choose.  I have 32-bit installed so that I know. 

Debian-based or RPM-based?

with JRE or without JRE?

Also, off topic for this subject, this is my first run with a linux operating system.  I installed Ubuntu, but wonder if there is a different version that would make more sense.  I have this installed onto a gateway LT1004U netbook.  I do intend to load several more machines as well which will include desktops and laptops.

Thank you for your advise.

---

### Post by tahafisaka6 on 2012-01-20
ok so I tried the Debian-based without JRE.  Either that is the wrong one, or most likely I have no clue how to install the driver.  I double clicked the .sh file and it asked the the root (Administrative) password, I tried the one I have for the user account, but it did not accept it, said it was not correct.  I then tried the directions on lexmarks site for the install command in terminal, but it said it was not a valid command.

I have tried searches in google and on here on how to install the print drivers, but I am not finding any directions on how to do the scripts.

Any help would be greatly appreciated.

Thank You,

---

### Post by tahafisaka6 on 2012-01-21
ok, so I finally figured this out being a total nub with anything Linux. 

Here is the solution for anyone else who searches and finds this thread.

In order for me to install this driver, I downloaded the tar file from Lexmark and uncompressed it.

The next steps was where I was having an issue.  CTRL-ALT-T to open terminal

At this point I needed to get to the folder where the file was uncompressed at, so in my case I just needed to go to the Downloads folder by typing   cd Downloads

Once here I typed in   sudo ./lexmark-inkjet-legacy-1.0-1.i386.deb.sh

If you have a different file name to install just type that in to replace from lemark on.

Hope this helps.

---

### Post by Johan-Steyn on 2013-02-20
You mean:

  sudo [COLOR=Red]**sh**[/COLOR] ./lexmark-inkjet-legacy-1.0-1.i386.deb.sh

or 

sudo sh lexmark-inkjet-09-driver-1.0-1.i386_ts.deb.sh

for the latest driver file.

Regards,


Johan

---

