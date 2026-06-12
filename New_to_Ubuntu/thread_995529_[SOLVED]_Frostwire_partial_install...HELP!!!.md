---
title: "[SOLVED] Frostwire partial install...HELP!!!"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by sillyboy on 2008-11-27
I downloaded Frostwire from their site and it installed...partially.  SPM says it is installed: version 4.17.1 for Ubuntu.  When I go to Applications>
Internet>Frostwire, there is no "real" icon there, but a box.  It says in SPM that I might need some kind of Java script??:confused:  How do I get Frostwire to work?
I am using 8.04.

Many Thanks

SB

---

### Post by taurus on 2008-11-27
Have you tried to run it from a terminal?

```
frostwire
```

---

### Post by alwayshere on 2008-11-27
To install frostwire in terminal put 

sudo apt-get install frostwire

----------------------------------------------

to install java 

sudo apt-get install sun-java6-jre
-----------------------------------------------
then  

sudo apt-get update 
----------------------------------------------

---

### Post by sillyboy on 2008-11-27
I typed in "sudo apt-get install sun-java6-jre", and the window that it is in says:  Configuring sun-java6-jre.  Is this right?

Does this take a long time to configure, or is it stuck??

Thanks

---

### Post by alwayshere on 2008-11-28
try these

sudo apt-get install sun-java6-bin

sudo apt-get install sun-java6-plugin

sudo apt-get update


---------------------------------------

---

### Post by sillyboy on 2008-11-28
When I type in the first command, this comes up:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by sillyboy on 2008-11-28
Does anyone know approximately how long Java bin takes to configure?  I need some kind of response here folks.:confused:

Thanks

---

### Post by alwayshere on 2008-11-28
it seems you must have another update application running that is why commands are not working 

you shouldnt have to conf anything

your just having bad luck the hole deal should be sorted in 20 min tops

---

### Post by alwayshere on 2008-11-28
you may have buggered the update/install manager to fix it run this command in terminal 

sudo dpkg --configure -a

---

### Post by sillyboy on 2008-11-28
OK, I ran: sudo dpkg --configure -a.  It took about 3 seconds and then the start prompt came back up. Now what do I do?

---

### Post by alwayshere on 2008-11-28
run the install commands again if it still doesnt work i guess you have a major problem with update manager not working which im not much good to you for .

good luck

---

