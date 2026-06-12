---
title: "Issue while trying to install chrome on UBUNTU 12.10"
date: 2013-06-25
forum: New to Ubuntu
---

### Post by fashaikh on 2013-06-25
Hi, 

I am trying to install chrome in UBUNTU 12.10 but I am getting the following error when running the command ```
 sudo dpkg -i google-chrome-stable_current_i386.deb
```:
**dpkg: error processing google-chrome-stable_current_i386.deb (--install):  package architecture (i386) does not match system (amd64)**

I also ran the following command 
```
 UNAME -mpi
``` and got the result** x86_64 x86_64 x86_64**.

Please note that I am on a 32-bit machine. Kindly help. 



Thanks, 
Fahad

---

### Post by Frogs Hair on 2013-06-25
Most computers have 64 bit architecture, but can run a 32 or 64 bit operating system. I have a 64 bit operating system installed and get the same output from the command .  ```
 uname -mpix86_64 x86_64 x86_64

``` Please try the following command and post the output .   ```
uname -a
``` Below is mine for 13.04 and you can see the kernel is  x86_64.```
 uname -aLinux ubuntu 3.8.0-26-generic #38-Ubuntu SMP Mon Jun 17 21:43:33 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

``` If you happened to have used Wubi/Windows installer it installs 64 bit by default.

---

### Post by fashaikh on 2013-06-25
Hi Frogs, 

Thanks for your reply. Please find below the output:

**```
Linux ubuntu 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux** 
```

Also, yes I installed via Wubi/Windows installer. I guess that explains it, however can you please tell me what's the solution as I just tried to install skype and faced the same issue. 


Thanks, 
Fahad

---

### Post by deadflowr on 2013-06-25
Easy, your system is 64-bit.
Download the 64-bit versions of chrome and skype.(amd64)

Since you're running wubi, you have Windows installed.
And that version of Windows is 32-bit.(I assume from post #1)
But that has nothing to do with the machine's architecture.

A 64-bit OS can only run on a 64-bit system.

Edit: Chrome download tends to default to the 32-bit version, like when you download Ubuntu the default image is the 32-bit version.
Just reselect the 64-bit version.

As far as skype, don't know if you're using the one you get the repos (you need to enable the partners repos) or from skype's site.
It might be a matter of getting the multiarch package.

---

### Post by Frogs Hair on 2013-06-25
You have a 64 bit OS so  select the 64 bit package from the Chrome website . You can install with the software center by double clicking the package after down loading or feel free to use the terminal. You would need a 64 bit package for Skype also (multiarch) but I see no 12.10 package and can't tell you if it works properly. Skype seems to provide packages for the long term support releases. Search Skype on Ubuntu 12.10 and see what comes up.   [https://www.google.com/intl/en/chrome/browser/](https://www.google.com/intl/en/chrome/browser/)

---

