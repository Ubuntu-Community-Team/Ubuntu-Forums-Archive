---
title: "problems installing dell printer driver"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by jmg on 2008-05-20
If you run a debian-based distro, like Knoppix or Ubuntu, read on.

   1. download CJLZ600LE-CUPS-1.0-1.TAR.gz from Lexmark.com - it is the CUPS driver for RedHat 9.0

[COLOR="Red"]downloaded to desktop[/COLOR]

   2. Untar and unzip this file using
      $ tar -zxvf CJLZ600LE-CUPS-1.0-1.TAR.gz
[COLOR="Red"]did this [/COLOR]
   3. You will end up with a file called
      z600cups-1.0-1.gz.sh

   4. Extract the .rpm part of this file using
      sh z600cups-1.0-1.gz.sh -target temp_lex

[COLOR="Red"]how do i extract this?  these commands are terminal commands and i get "can't open" when i use this command.  What am i doing wrong?
Ubuntu 8.04
[/COLOR]
      this will create a sub-directory called "temp_lex" under the current directory, and put a whole lot of files in it. Ignore any errors you might get - if the two .rpm files are in temp_lex you are fine.
   5. In the newly created directory temp_lex you will find, amongst others, the files:
      z600cups-1.0-1.i386.rpm, and
      z600llpddk-2.0-1.i386.rpm
   6. To install to a debian system (or Ubuntu or Knoppix) you need to convert these two files to the .deb equivalent. The program to use is called "alien" and you run it as follows:
      $ alien z600cups-1.0-1.i386.rpm

      $ alien z600llpddk-2.0-1.i386.rpm
   7. You will now find the dpkg packages:
      z600cups-1.0-1.i386.deb
      z600llpddk-2.0-1.i386.deb
   8. Now install the driver with:
      dpkg -i z600cups-1.0-1.i386.deb
      dpkg -i z600llpddk-2.0-1.i386.deb
   9. Now use CUPS or the Printer configuration tool in Ubuntu to add the printer

---

### Post by Xiong Chiamiov on 2008-05-21
By default, shell scripts are not executable.  To make it so, you'll have to 
```

sudo chmod +x [filename]

```
then try to run it.

---

### Post by jmg on 2008-05-21
Thanks Xiong for your reply.  i guess i need to read some more.  Still cannot extract the needed file.  Thanks again

---

