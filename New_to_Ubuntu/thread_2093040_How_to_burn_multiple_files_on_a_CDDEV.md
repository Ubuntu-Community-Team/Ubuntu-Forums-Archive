---
title: "How to burn multiple files on a CD/DEV"
date: 2012-12-09
forum: New to Ubuntu
---

### Post by mark allyn on 2012-12-09
Hello everyone,
 
I am trying to burn multiple individual files (not necessarily .iso files, just plain old text files and folders) to a CD using the command line and linux-only commands.  Brasero (and other) burners have no problem doing this task.  I would like to understand how to do it without the assistance of an app like Brasero or the Disk Creator.  Would someone be kind enough to walk me through the details.
 
Cheers,
Mark Allyn

---

### Post by TheFu on 2012-12-09
> **mark allyn said:**
> Hello everyone,
 
I am trying to burn multiple individual files (not necessarily .iso files, just plain old text files and folders) to a CD using the command line and linux-only commands.  Brasero (and other) burners have no problem doing this task.  I would like to understand how to do it without the assistance of an app like Brasero or the Disk Creator.  Would someone be kind enough to walk me through the details.

Google found these:
* [http://www.nijhuis.net/technet/Unix/UnixHowto.htm#BurnCD](http://www.nijhuis.net/technet/Unix/UnixHowto.htm#BurnCD)
* [http://www.nijhuis.net/technet/Unix/UnixHowto.htm#BurnDVD](http://www.nijhuis.net/technet/Unix/UnixHowto.htm#BurnDVD)

You will want to avoid the GUI tools and stay with 100% pure CLI tools.

---

### Post by mark allyn on 2012-12-10
Hello TheFu,
 
Thanks for replying to my question.  I may be mistaken, but it seems to me as if the code you sent will create burn just ONE image and not MULTIPLE images.  In order to burn another image I would have to erase the first one.  Perhaps I am mistaken....I think I need some way to "stack up" a bunch of individual images in a single file and then burn the "stacked" file.
 
Cheers,
Mark Allyn

---

### Post by Zill on 2012-12-10
mark allyn:  Could you simply [tar]("http://packages.ubuntu.com/lucid/tar") the files into a single file?
> Tar is a program for packaging a set of files as a single archive in tar format.

---

### Post by TheFu on 2012-12-10
> **mark allyn said:**
> Hello TheFu,
 
Thanks for replying to my question.  I may be mistaken, but it seems to me as if the code you sent will create burn just ONE image and not MULTIPLE images.  In order to burn another image I would have to erase the first one.  Perhaps I am mistaken....I think I need some way to "stack up" a bunch of individual images in a single file and then burn the "stacked" file.

**From the DVD instructions:**
Create your own DVD from fs tree on current directory
 Step 1: "mkisofs -R -J -o somefile ."
Step 2: "cdrecord dev=b,t,l -v somefile*"


Step 1 - This creates an ISO file (somefile) containing all the files in the current working directory. You can place 1 or many thousands of files in the directory.

Step 2 - this writes that ISO file to the optical device for the system. You can write this file (somefile) once or 5,000,000 times.


If you want more details, the man pages for these commands should explain everything AND many other options. On my box, mkisofs is connected to the **genisoimage** command and cdrecord points to **wodim**. The man pages for those appear to be complete. It did seem odd that cdrecord and mkisofs were not the commands with man pages, but ... whatever.



The "dev" specification might be different for every PC. You'll need to understand it and get the correct one. My box has a /etc/wodim.conf with that data. The device is "cdrom" on mine. Since I didn't create that file, I guess it was created when the OS or DVD writer was installed into the system?


With a little scripting, it shouldn't be too difficult to accomplish whatever you require.

---

### Post by mark allyn on 2012-12-10
Hi TheFu.
 
Thanks, I got it. Don't know why it didn't dawn on me that you could burn a directory!
 
Thanks also for the suggestion re Tarring. I'll try it just for fun.
 
Regards to both,
 
Mark

---

