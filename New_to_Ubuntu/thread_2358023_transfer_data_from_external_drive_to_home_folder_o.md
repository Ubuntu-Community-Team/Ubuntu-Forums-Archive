---
title: "transfer data from external drive to home folder on sda drive."
date: 2017-04-08
forum: New to Ubuntu
---

### Post by jaxom98 on 2017-04-08
My original computer was dieing and wouldn't back up,(mobo and hdd at once) so I had a professional retrieve my data (got most), and store it on an external hdd I provided. I can access the data if I plug the external drive into the computer ,but I want to copy the edubuntu files to the "home" folder on the sda drive for conveniance.
I don't know how. Can some one explain in simple terms how to?
System:
quad core amd
6Gb ram
OS win7/edubuntu14.04 on 120Gb ssd
win7 data is sent to 2nd hdd and edubuntu data is sent to a 3rd hdd
This machine is an ex gaming hand-me-down.

---

### Post by yancek on 2017-04-08
Doing that should not be any problem.  You can use the cp (copy) command to copy from a source location to a destination.
You can use the file manager and go to the source (external drive) and open a second instance of the filemanager to copy the file to your /home directory.  This is pretty basic stuff.  What exactly are you having difficulty with.  You should not have any ownership or permissions problems copying 'from' the external and you are copying to your home directory.

---

### Post by jaxom98 on 2017-04-13
Excuse the slow reply.
This should be in the absolute beginners section.  Just not familier with shifting files at all.  Local computer classes are windows only. When I ask about linux their reaction is "what is that???"   My knowledge starts and stops at browsing.

---

### Post by yancek on 2017-04-13
If Edubuntu is similar to Ubuntu and it's other derivatives, the partitions on any drive attached should be available under the /media/user directory (insert your actual 'user' name) which you can access either from a terminal or from a file manager.  I don't know what file manager Edubuntu uses but you can probably access it from a folder icon on the Desktop.  Use the UP and BACK/FORWARD arrows in the file manager to navigate to the location you want. 

 If you open a terminal, you can list the files from your various partitions with:  ls /media/user (again substitute your actual user name)  There should be a number of folder icons showing with UUIDs which are long combinations of letters/number.  Change to any of them and again list the files with ls to see what's in them until you find the partition with the files you want.  You do this with the cd command:  cd /media/user/UUID  as an example, using the actual UUID you see.

I found the link below which is a Quick Guide to using Edubuntu.  Hopefully that will help.  I don't know any simpler way to explain it.  

[http://static.xubuntu.org/news/ComputerReach%20Edubuntu%2014.04%20-%20Xubuntu%20-%20QuickGuide%20(mod).pdf](http://static.xubuntu.org/news/ComputerReach%20Edubuntu%2014.04%20-%20Xubuntu%20-%20QuickGuide%20(mod).pdf)

---

### Post by jaxom98 on 2017-04-14
Hello yancek, problem solved ,thank you for your time.

---

