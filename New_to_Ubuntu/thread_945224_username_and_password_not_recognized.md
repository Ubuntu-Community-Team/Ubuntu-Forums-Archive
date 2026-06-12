---
title: "username and password not recognized"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by jerry scott on 2008-10-12
I made a CD of the ubuntu-8.04.1-desktop-i386.iso image and it seemed to run just fine,  but would not respond to my username and password after rebooting.

I have an HP Pavilion a12310n computer with nothing on the 200G hard drive, 512MB memory and a DVD-RW drive that will support bootable CDs.

I run the above iso with no apparent issues, initilizing the userneame and password, and then reboot.  Of course, the system first asks for the username/password and I enter them.  The screen clears and then (with no explanation) again asks for the username/password.  After entering them a second time, the screen clears and then again asks for the username/password - this time indicating that the inputs must be in order and are case sensitive.

I ame a bit frustrated and not certain how I should proceed since I'm not getting to a place that I can check log files or proper installation.

---

### Post by hyper_ch on 2008-10-12
if you run the desktop cd nothing is stored on your computer... so next time you run it, it will load everything again into ram without touching your harddisk.

As long as you don't install it, the changes won't stick.

---

### Post by jerry scott on 2008-10-12
When it ran, it partationed the hard disk and I had it format the entire disk.  It then told me it was installing the system onto the hard disk.  It then ejected the CD and did not require it when it rebooted, thus confirming files had been copied to the hard disk as the hard disk was not bootable previously.

Sorry for not speaking clearly.

---

### Post by hyper_ch on 2008-10-12
ah.... well, username and passwords are case sensitiv.

e.g. use "jerry" as username and not "Jerry".. by default it suggests username all in lower case.

---

### Post by jerry scott on 2008-10-12
All uername and passwods are entered in lower case.

---

### Post by hyper_ch on 2008-10-12
you may want to reset the password then:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

(and you shouldn't have a lower-case only password)

---

