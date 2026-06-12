---
title: "Can't get Dell 720 Printer to work...."
date: 2008-10-09
forum: New to Ubuntu
---

### Post by azbobc on 2008-10-09
Greetings.... I'm new to linux so I'm still struggling some with some very basic stuff. And because of that I may not always use the proper term but I'll do my best. I'm running Ubuntu 8.04, for the most part it's been pretty user friendly. I've got a Dell 720 printer hooked to it that I'm trying to get to work. From what I understand I need to get the drivers loaded up and that my best route is to use the Lexmark z600 drivers as described in this post:[http://ubuntuforums.org/showthread.php?t=215657](http://ubuntuforums.org/showthread.php?t=215657) I've done my best to follow what is being posted but I still don't get any results. (well except an error message) The files have been downloaded in my temp file but I noticed they are still compressed. Don't they need to be uncompressed (or unzipped) to be of any use? If so how are files uncompressed in Ubuntu? 
Thx....

---

### Post by phidia on 2008-10-09
As the guide you linked states: > In a terminal, untar the files you just downloaded using
Code:

tar -xvzf CJLZ600LE_CUPS_1_0_1.TAR.gz



You can also right click the archieve and select "Extract here" from the menu that right clicking produces.

There is more info on your printer at the openprinting site [here]("http://openprinting.org/show_printer.cgi?recnum=Dell-Photo_Printer_720").

---

### Post by azbobc on 2008-10-10
Well, I wish I could get it to do something other than this....
Type following:
tar -xvzf CJLZ600LE-CUPS-1.0-1

Get this:
tar: CJLZ600LE-CUPS-1.0-1: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

None of the downloaded files shows in the Synaptic Package Manager either.

---

### Post by phidia on 2008-10-10
This: > Cannot open: No such file or directory usually means you are not issuing the tar command in the correct place. You need to be in the directory that contains the compressed files.

As I said there is a gui way to unpack-look at my previous response.

If you are having lots of problems with the command line/terminal you may need to work on your basic skills first. Two Forum members have put together a good (but rather lengthy) guide [here]("http://ubuntuforums.org/showthread.php?t=781352").

The Ubuntu wiki has a guide for using the terminal [here]("https://help.ubuntu.com/community/UsingTheTerminal").

---

