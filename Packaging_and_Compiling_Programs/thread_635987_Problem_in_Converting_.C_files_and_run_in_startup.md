---
title: "Problem in Converting .C files and run in startup"
date: 2007-12-09
forum: Packaging and Compiling Programs
---

### Post by nemtech on 2007-12-09
Hello there!

1st, sry for my bad english! =")

ok, i have a C file with file name Process.c
i have to run this program @ startup when my ubuntu comes up!

i think i have to compile that to a binary and the i can put it in init.d and rcS.d

so can someone help how i can compile it? or how i can run in in startup without compile? is it posibble or no ?

is there any shell script for this job ? (runing a C file with out compile in startup)

thnx 

sry for my bad eng again!

---

### Post by meatpan on 2007-12-10
You will need to use a compiler to create an executable that can be run at startup.

I suggest using gcc.  You might need to run 'sudo apt-get build-essential' to install a copy of gcc, as well as the necessary utilities.   

Also, consider creating a script that wraps your c program.  You can copy the format of some of the programs in /etc/init.d.  This will make your setup more flexible, particularly if you plan to stop and restart the service outside of init.  Once you have created the script in /etc/init.d, take a look at the 'update-rc.d' command.

---

### Post by rbprogrammer on 2007-12-15
> **nemtech said:**
> Hello there!

1st, sry for my bad english! =")

ok, i have a C file with file name Process.c
i have to run this program @ startup when my ubuntu comes up!

i think i have to compile that to a binary and the i can put it in init.d and rcS.d

so can someone help how i can compile it? or how i can run in in startup without compile? is it posibble or no ?

is there any shell script for this job ? (runing a C file with out compile in startup)

thnx 

sry for my bad eng again!
meatpan is right.  a C program needs to be compiled.  then when you compile it, move it somewhere on your system.  does not really matter where, but a good place to put it would be in either a directory in your home directory, or in /usr/bin... then if you use GNOME, go to the menu at the top, System->Preferences->Sessions, and in there you can add the program to the start up list.

i see you have a just a few beans.  if you need help with moving the file ( b/c of permission errors ) just say so..

---

