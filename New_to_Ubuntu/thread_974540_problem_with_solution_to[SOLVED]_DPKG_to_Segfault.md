---
title: "problem with solution to[SOLVED] DPKG to Segfault"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by kenley on 2008-11-07
i have a problem like the one described in this thread.  i took the information that i thought was the solution and started working with it.

 Re: DPKG to Segfault
Since you don't seem to be making much progress , here is a final suggestion (at least from me). Try renaming /var/lib/dpkg/libc6.postrm and libc6.postinst and try running the apt-get commands again. Rename to the original if it doesn't work. If it does, reinstall libc6 to reset the .postrm and .postinst files to the correct status.
__________________

i went looking for libc6.postrm.  i went to the directory below. and did not find the file.

root@ubuntu:/var/lib/dpkg# ls
alternatives   cmethopt        info   statoverride      status-old
available      diversions      lock   statoverride-old  triggers
available-old  diversions-old  parts  status            updates
root@ubuntu:/var/lib/dpkg# 

since i did not find the file i tried what the apt-get commands.  the solution given did not indicate which apt-get commands to do but i tried several of the commands listed previously in the thread.  

root@ubuntu:/var/lib/dpkg# Apt-get/dpkg
bash: Apt-get/dpkg: No such file or directory

root@ubuntu:/var/lib/dpkg# sudo apt-get install libc6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 32 not upgraded.
7 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
dpkg: error processing hal-info (--configure):
 package hal-info is not ready for configuration
 cannot configure (current status `triggers-awaited')
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly


root@ubuntu:/var/lib/dpkg# sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 32 not upgraded.
7 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
dpkg: error processing hal-info (--configure):
 package hal-info is not ready for configuration
 cannot configure (current status `triggers-awaited')
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

does anyone have an idea what can fix this problem?  i installed with xubi.  i am new to linux. and know little of the commands to run from the command prompt.  i have familiarity with command line commands from other os's  i am running ubuntu 8.10.

thanks for any help.

Kenley

---

