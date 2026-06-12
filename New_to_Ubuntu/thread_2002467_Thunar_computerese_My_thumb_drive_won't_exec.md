---
title: "Thunar computerese? My thumb drive won't exec?"
date: 2012-06-12
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2012-06-12
I have started using LastPass with the 2-step authenticator Sesame. Sesame has to be installed on a thumb drive to work. After the install, the sesame executable would not run. 

I use XFCE (and Thunar). I went to the Thunar site, looking for help and found in the FAQ section:

Why doesn't Thunar execute files marked as executable?

For security reasons Thunar only executes files of type application/x-desktop, application/x-executable and application/x-shellscript. For desktop files the execution feature will only be enabled if the desktop file is of type Application and a valid Exec line is given. For the other types the feature is available if the file is marked executable for the current user.
Also note that for application/x-executable and application/x-shellscript, the types of the file don't really need to match these types exactly, but it is suffice if the detected type has a parent that matches one of the two types listed above, or if the MIME-type is an alias for one of the above.

So is my sesame, on my usb thumb (synonyms: flash, pen) drive not executable because of the foregoing?

It's useless to have security, if the drive can't be removed from the OS. And it can't be removed unless the 'puter is turned off, as there is no Eject option as the drive is now mounted in such a way as it doesn't appear in the list of devices in Thunar.

Here is where I got help making the sesame executable work:

[http://ubuntuforums.org/showthread.php?t=1992379](http://ubuntuforums.org/showthread.php?t=1992379)

---

### Post by Mark_in_Hollywood on 2012-07-19
MY BAD! I had no idea that a drive formatted for NTFS would not be able to run Linux executables. Sorry.

---

