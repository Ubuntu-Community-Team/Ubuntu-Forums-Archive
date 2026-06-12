---
title: "Using Picasa in Linux - How do I open a new user acct. to begin learning Picasa?"
date: 2013-08-09
forum: New to Ubuntu
---

### Post by Sandra_Shimko on 2013-08-09
I am trying to learn Linux, I have always used Microsoft Windows.  Gimp is too confusing, so I am attempting to learn Picassa.  The first instructions say to make a new Windows user account for practice.  This is unclear to me!  Is the new users account I just made in Ubuntu something I will be able to use for this?  

Thank you,   Sandy

---

### Post by deadflowr on 2013-08-09
I don't understand your question, but Picasa is a Windows program.
It's not linux, and never has been.
When you install Picasa on Ubuntu, you also install the program wine.
Wine allows you to run SOME Windows programs inside Ubuntu/Linux.

---

### Post by oldfred on 2013-08-09
I have a full install of the Windows Picasa version in my .wine. I did not create a new user, just installed it. 

[http://www.webupd8.org/2012/01/install-picasa-39-in-linux-and-fix.html](http://www.webupd8.org/2012/01/install-picasa-39-in-linux-and-fix.html)
[http://www.ubuntugeek.com/howto-install-picasa-3-5-in-ubuntu.html#more-2019](http://www.ubuntugeek.com/howto-install-picasa-3-5-in-ubuntu.html#more-2019)
[http://www.omgubuntu.co.uk/2009/09/picasa-35-linux-install.html](http://www.omgubuntu.co.uk/2009/09/picasa-35-linux-install.html)

&#65279;sudo apt-get update
sudo apt-get upgrade
sudo apt-get install wine winetricks

Configure Wine to set up directory,  Applications, Wine, Configure

Then download picasa for windows
 ([http://dl.google.com/picasa/picasa39-setup.exe](http://dl.google.com/picasa/picasa39-setup.exe))
cd && wget [http://dl.google.com/picasa/picasa39-setup.exe](http://dl.google.com/picasa/picasa39-setup.exe)
Move it into .wine/drive_c/Program Files
wine picasa39-setup.exe


Not sure if picasa39 is still the most current version.

---

