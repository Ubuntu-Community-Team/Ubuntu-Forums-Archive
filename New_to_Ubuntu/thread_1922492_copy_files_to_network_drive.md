---
title: "copy files to network drive"
date: 2012-02-08
forum: New to Ubuntu
---

### Post by cliuari on 2012-02-08
I am using Ubuntu 11.04. In the file manager, I can copy files from network drive to a folder in my home. But I cannot copy files back to the network drive, even though I set the permissions to the files and the folders in the two sides to read/write (even full) permission. I can do two-way communication with the network drive in windows system. 
 
Majority of my work and data are in windows system. I need to move the results from linux to the windows system so that I can do further analysis.
 
Anyone can help on this? Thanks.

---

### Post by papibe on 2012-02-08
What version of Windows are you using?
What kind of sharing did you set on Windows?

Regards.

---

### Post by cliuari on 2012-02-08
> **papibe said:**
> What version of Windows are you using?
What kind of sharing did you set on Windows?
 
Regards.
 
 
Thanks very much for your reply. My windows is XP. I set the folder in the network drive to "full control" permissions for "everyone". 
 
The problem may be in the Ubuntu side. After I "copy" a file (even a simplr xxx.txt file, which can be opened with gedit), when I go to the destination network drive folder and "paste" it, it says:
 
Error while copying.
There was an error getting information about "xxx.txt".
Error stating file '/home/cl17/unicor/xxx.txt': No such file or directory.
 
When I change other files to copy, similar problem also occurs.
 
I also set the files in my ubuntu home to read/write perssions for both groups sys and adm. The problem still occurs.
 
Any further suggestions? Thanks.

---

### Post by cliuari on 2012-02-09
> **papibe said:**
> What version of Windows are you using?
What kind of sharing did you set on Windows?
 
Regards.
 
 
Further background information about my problem:
 
Ubuntu is installed in a server, which is run as a virtual machine. I login to the virtual machine with my username from my PC. I also access network drive from my PC.

---

### Post by cliuari on 2012-02-09
> **cliuari said:**
> Further background information about my problem:
 
Ubuntu is installed in a server, which is run as a virtual machine. I login to the virtual machine with my username from my PC. I also access network drive from my PC.
 
 
The problem has been solved. I changed to another drive, it works. But the previous drive still doesn't work. Probably it's a permission problem. Anyway, working in one drive is ok for me since I can fully control all the drives in windows.

---

