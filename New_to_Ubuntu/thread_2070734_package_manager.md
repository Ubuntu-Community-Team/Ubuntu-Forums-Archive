---
title: "package manager"
date: 2012-10-13
forum: New to Ubuntu
---

### Post by 32bits on 2012-10-13
Hello wonderful people. please help me fix this error.

I get an error message anytime i try to install updates. I get the same error message when i try to run package manager. Please the error below:
*****************************************************************
E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.
*****************************************************************

Please help me fix this error thanks

---

### Post by philinux on 2012-10-13
> **32bits said:**
> Hello wonderful people. please help me fix this error.

I get an error message anytime i try to install updates. I get the same error message when i try to run package manager. Please the error below:
*****************************************************************
E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.
*****************************************************************

Please help me fix this error thanks

See post #7. make sure you copy and paste this command. If u type it wrong it could bork your system
[http://ubuntuforums.org/showthread.php?t=1750755](http://ubuntuforums.org/showthread.php?t=1750755)


Other wise use gksu nautilus and navigate to the directory and remove the file manually with the gui.

---

### Post by NikTh on 2012-10-13
Hi , 

Open a terminal and copy-paste from here bellow commands 

```
sudo rm /var/lib/apt/lists* -vf 
sudo apt-get update 
sudo apt-get dist-upgrade
``` 
[[COLOR=#DD4814]**philinux**[/COLOR]]("http://ubuntuforums.org/member.php?u=353083") you forgot to give the link :P 
Thanks

---

