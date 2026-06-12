---
title: "need help with steam??"
date: 2015-07-16
forum: New to Ubuntu
---

### Post by kenneth18 on 2015-07-16
when ever i open steam to run it i always get this code:     Steam needs to install these additional packages: 
Code:
   >  libgl1-mesa-dri:i386, libgl1-mesa-glx:i386, libc6:i386
[sudo] password for mrragequit:

then after i enter my password i end up getting this code:    Steam needs to install these additional packages: 
Code:
   >  libgl1-mesa-dri:i386, libgl1-mesa-glx:i386, libc6:i386
[sudo] password for mrragequit: 
................................................................................................
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.4)
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
Press return to continue: 


what do i do??

---

### Post by slickymaster on 2015-07-16
Hi kenneth18, welcome to the forums.

Can you please provide us the output of:```
lsb_release -a && uname -a
```

---

### Post by kenneth18 on 2015-07-16
sorry in kinda new what is that exactly

---

### Post by howefield on 2015-07-16
> **kenneth18 said:**
> sorry in kinda new what is that exactly

Are you using Ubuntu ? If so, open the dash and search for and open a terminal... type in or paste the above command.

Then copy and paste the output in to a post back here, using code tags, eg...

```
hugh@lubuntu:~$ lsb_release -a && uname -a
LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:cxx-3.0-amd64:cxx-3.0-noarch:cxx-3.1-amd64:cxx-3.1-noarch:cxx-3.2-amd64:cxx-3.2-noarch:cxx-4.0-amd64:cxx-4.0-noarch:cxx-4.1-amd64:cxx-4.1-noarch:desktop-3.1-amd64:desktop-3.1-noarch:desktop-3.2-amd64:desktop-3.2-noarch:desktop-4.0-amd64:desktop-4.0-noarch:desktop-4.1-amd64:desktop-4.1-noarch:graphics-2.0-amd64:graphics-2.0-noarch:graphics-3.0-amd64:graphics-3.0-noarch:graphics-3.1-amd64:graphics-3.1-noarch:graphics-3.2-amd64:graphics-3.2-noarch:graphics-4.0-amd64:graphics-4.0-noarch:graphics-4.1-amd64:graphics-4.1-noarch:languages-3.2-amd64:languages-3.2-noarch:languages-4.0-amd64:languages-4.0-noarch:languages-4.1-amd64:languages-4.1-noarch:multimedia-3.2-amd64:multimedia-3.2-noarch:multimedia-4.0-amd64:multimedia-4.0-noarch:multimedia-4.1-amd64:multimedia-4.1-noarch:printing-3.2-amd64:printing-3.2-noarch:printing-4.0-amd64:printing-4.0-noarch:printing-4.1-amd64:printing-4.1-noarch:qt4-3.1-amd64:qt4-3.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 15.04
Release:	15.04
Codename:	vivid
Linux lubuntu 3.19.0-22-generic #22-Ubuntu SMP Tue Jun 16 17:15:15 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
hugh@lubuntu:~$ 
```

---

### Post by kenneth18 on 2015-07-16
Code:
> mrragequit@mrragequit-HP-G62-Notebook-PC:~$ lsb_release -a && uname -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty
Linux mrragequit-HP-G62-Notebook-PC 3.16.0-43-generic #58~14.04.1-Ubuntu SMP Mon Jun 22 10:21:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
mrragequit@mrragequit-HP-G62-Notebook-PC:~$ 

---

### Post by slickymaster on 2015-07-16
> **kenneth18 said:**
> sorry in kinda new what is that exactly

That command, executed in a terminal window will tell us your exact release name and system information.

All you have to do is to copy/past that command into a terminal window, which you can open by hitting the Ctrl+Alt+T keys or searching for 'terminal' in the dash.

Once executed please post back here in the thread the output you get from it.

---

### Post by slickymaster on 2015-07-16
> **kenneth18 said:**
> ```
mrragequit@mrragequit-HP-G62-Notebook-PC:~$ lsb_release -a && uname -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 14.04.2 LTS
Release: 14.04
Codename: trusty
Linux mrragequit-HP-G62-Notebook-PC 3.16.0-43-generic #58~14.04.1-Ubuntu SMP Mon Jun 22 10:21:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
mrragequit@mrragequit-HP-G62-Notebook-PC:~$
```
Let's try this (again in a terminal window)```
sudo apt-get -s install libgl1-mesa-glx-lts-utopic:i386
```and please post back here again all the output you get.

---

### Post by kenneth18 on 2015-07-16
this is what came out
Code:
> mrragequit@mrragequit-HP-G62-Notebook-PC:~$ 
mrragequit@mrragequit-HP-G62-Notebook-PC:~$ 
mrragequit@mrragequit-HP-G62-Notebook-PC:~$ sudo apt-get -s install libgl1-mesa-glx-lts-utopic:i386
[sudo] password for mrragequit: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgl1-mesa-glx-lts-utopic:i386 is already the newest version.
libgl1-mesa-glx-lts-utopic:i386 set to manually installed.
The following packages were automatically installed and are no longer required:
  account-plugin-windows-live libupstart1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
mrragequit@mrragequit-HP-G62-Notebook-PC:~$ 


---

### Post by kenneth18 on 2015-07-16
geez thank you so much for the help i really needed that...finally its working!!!

---

### Post by kenneth18 on 2015-07-16
but if you dont mind could you tell me how to install league of legends??

---

### Post by kenneth18 on 2015-07-16
hey can you help me install league of legends?

---

### Post by howefield on 2015-07-16
You do not have to repeat yourself.

I'd suggest opening a new thread for this separate issue in the [Gaming and Leisure]("http://ubuntuforums.org/forumdisplay.php?f=93") section, assuming it isn't a game run via [Wine]("http://ubuntuforums.org/forumdisplay.php?f=313").

---

### Post by slickymaster on 2015-07-16
> **kenneth18 said:**
> this is what came out
```
mrragequit@mrragequit-HP-G62-Notebook-PC:~$ 
mrragequit@mrragequit-HP-G62-Notebook-PC:~$ 
mrragequit@mrragequit-HP-G62-Notebook-PC:~$ sudo apt-get -s install libgl1-mesa-glx-lts-utopic:i386
[sudo] password for mrragequit: 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
libgl1-mesa-glx-lts-utopic:i386 is already the newest version.
libgl1-mesa-glx-lts-utopic:i386 set to manually installed.
The following packages were automatically installed and are no longer required:
account-plugin-windows-live libupstart1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
mrragequit@mrragequit-HP-G62-Notebook-PC:~$
```

> **kenneth18 said:**
> geez thank you so much for the help i really needed that...finally its working!!!
That's odd.

Did you, afterwards, run the command without the **-s** option? With that option you just did a simulation of what would occur, but not actually installing the **libgl1-mesa-glx-lts-utopic:i386** package in your system.

---

