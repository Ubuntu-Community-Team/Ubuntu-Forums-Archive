---
title: "[SOLVED] (8.04) update error"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by Stratos01 on 2008-11-17
Hi everyone, I tried searching for this but maybe I might have missed it. 
I currently have this problem:

When I try to install updates, I have this return error message;

error exit status 123

The files or directories could not be found:
/var/cache/fonts
/var/cache/anthy
/var/lib/locales

I am not sure if this has got to do with my uninstallation of evolution, but I am unable to reinstall it when I guessed that it may be the problem through 'add & remove'

Anyone have any idea what I should do?

Thank you!

---

### Post by stephanvaningen on 2008-11-17
The first two are also not in my disk-tree, yet I don't get update-errors...

---

### Post by Stratos01 on 2008-11-17
> **stephanvaningen said:**
> The first two are also not in my disk-tree, yet I don't get update-errors...

That is strange, so the problem lies somewhere else?

---

### Post by philinux on 2008-11-17
From a terminal.

sudo apt-get update

Post the errors if any

Then

sudo apt-get upgrade

---

### Post by Zill on 2008-11-17
> **Stratos01 said:**
> ...I am not sure if this has got to do with my uninstallation of evolution, but I am unable to reinstall it when I guessed that it may be the problem through 'add & remove'...
AIUI, Evolution is a required application and its removal *may* be the cause of your problem!

I suggest you reinstall the ubuntu-desktop metapackage to ensure that evolution and all associated dependencies are reinstalled correctly.

---

### Post by Stratos01 on 2008-11-17
> **philinux said:**
> From a terminal.

sudo apt-get update

Post the errors if any

Then

sudo apt-get upgrade

Thank you for your reply, i have done both and the following occurred:

~$ sudo apt-get update
[sudo] password for user: 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages [1178kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources
Fetched 1178kB in 1min9s (16.8kB/s)
Reading package lists... Done
user@Intel1800A:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  alacarte dbus dbus-x11 foo2zjs libdbus-1-3 libsmbclient login
  module-init-tools passwd samba-common smbclient update-notifier
  update-notifier-common
13 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/11.9MB of archives.
After this operation, 20.5kB disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Setting up base-files (4.0.1ubuntu5.8.04.3) ...
find: /var/cache/fonts: No such file or directory
find: /var/cache/anthy: No such file or directory
find: /var/lib/locales: No such file or directory
chgrp 0 /etc/dictionaries-common/default.aff /etc/dictionaries-common/default.hash /etc/dictionaries-common/words 
chgrp: cannot dereference `/etc/dictionaries-common/default.aff': No such file or directory
chgrp: cannot dereference `/etc/dictionaries-common/default.hash': No such file or directory
chgrp: cannot dereference `/etc/dictionaries-common/words': No such file or directory
dpkg: error processing base-files (--configure):
 subprocess post-installation script returned error exit status 123
Errors were encountered while processing:
 base-files
E: Sub-process /usr/bin/dpkg returned an error code (1)


Looks like a similar reply when i did the right click and install updates..

---

### Post by philinux on 2008-11-17
Try this
sudo dpkg --configure -a

and also open synaptic click custom filters then have a look under broken.

---

### Post by Stratos01 on 2008-11-17
> **philinux said:**
> Try this
sudo dpkg --configure -a

and also open synaptic click custom filters then have a look under broken.

When I typed the first option i got this:

~$ sudo dpkg --configure -a
[sudo] password for user: 
Setting up base-files (4.0.1ubuntu5.8.04.3) ...
find: /var/cache/fonts: No such file or directory
find: /var/cache/anthy: No such file or directory
find: /var/lib/locales: No such file or directory
chgrp 0 /etc/dictionaries-common/default.aff /etc/dictionaries-common/default.hash /etc/dictionaries-common/words 
chgrp: cannot dereference `/etc/dictionaries-common/default.aff': No such file or directory
chgrp: cannot dereference `/etc/dictionaries-common/default.hash': No such file or directory
chgrp: cannot dereference `/etc/dictionaries-common/words': No such file or directory
dpkg: error processing base-files (--configure):
 subprocess post-installation script returned error exit status 123
Errors were encountered while processing:
 base-files


Also in Synaptic it says:

I went to settings> filters> broken
and checked only 'broken'

25031 packages listed, 1166 installed, 0 broken, 0 to install/upgrade
in the status bar

Is this what you mean?
Thank you!

---

### Post by philinux on 2008-11-17
sudo apt-get -f install

---

### Post by philinux on 2008-11-17
Woah, just re-read those errors and found this.

[https://bugs.launchpad.net/ubuntu/+source/base-files/+bug/292116](https://bugs.launchpad.net/ubuntu/+source/base-files/+bug/292116)

---

### Post by Stratos01 on 2008-11-17
> **philinux said:**
> Woah, just re-read those errors and found this.

[https://bugs.launchpad.net/ubuntu/+source/base-files/+bug/292116](https://bugs.launchpad.net/ubuntu/+source/base-files/+bug/292116)

That is so strange, it is the same error!
However my processor is an Intel 1.8 Ghz
and I am still using Ubuntu 8.04, I think?

---

### Post by Stratos01 on 2008-11-17
> **Stratos01 said:**
> That is so strange, it is the same error!
However my processor is an Intel 1.8 Ghz
and I am still using Ubuntu 8.04, I think?

But I am using an nVidia VGA card, it is a geforce 4 ti..

---

### Post by Stratos01 on 2008-11-17
> **Zill said:**
> AIUI, Evolution is a required application and its removal *may* be the cause of your problem!

I suggest you reinstall the ubuntu-desktop metapackage to ensure that evolution and all associated dependencies are reinstalled correctly.

Thank you Zill, does this mean to format and reinstall ubuntu from the live-cd? sorry I do not follow how to reinstall the meta package. Thank you!

---

### Post by philinux on 2008-11-17
Hardware is irrelevant to this bug I think. Not sure how to fix it either. Back soon.

---

### Post by philinux on 2008-11-17
sudo apt-get check

---

### Post by Stratos01 on 2008-11-17
> **philinux said:**
> sudo apt-get -f install

I did that and it looks like the same thing;

~$ sudo apt-get -f install
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up base-files (4.0.1ubuntu5.8.04.3) ...
find: /var/cache/fonts: No such file or directory
find: /var/cache/anthy: No such file or directory
find: /var/lib/locales: No such file or directory
chgrp 0 /etc/dictionaries-common/default.aff /etc/dictionaries-common/default.hash /etc/dictionaries-common/words 
chgrp: cannot dereference `/etc/dictionaries-common/default.aff': No such file or directory
chgrp: cannot dereference `/etc/dictionaries-common/default.hash': No such file or directory
chgrp: cannot dereference `/etc/dictionaries-common/words': No such file or directory
dpkg: error processing base-files (--configure):
 subprocess post-installation script returned error exit status 123
Errors were encountered while processing:
 base-files
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Zill on 2008-11-17
> **Stratos01 said:**
> Thank you Zill, does this mean to format and reinstall ubuntu from the live-cd? sorry I do not follow how to reinstall the meta package. Thank you!
No - that's far too drastic at this stage. ;-)

To reinstall a package simply open Synaptic and search for the required application (ubuntu-desktop).  Then right click on the name and select "Mark for Reinstallation".  Click "Apply" to reinstall.

---

### Post by philinux on 2008-11-17
The app in question is base-files.
Nor sure if this will fix it.

[FONT=Arial]sudo apt-get --reinstall install base-files[/FONT]

---

### Post by Stratos01 on 2008-11-17
> **Zill said:**
> No - that's far too drastic at this stage. ;-)

To reinstall a package simply open Synaptic and search for the required application (ubuntu-desktop).  Then right click on the name and select "Mark for Reinstallation".  Click "Apply" to reinstall.

Ok it is downloading now, thank you! will let you know what happens after this.

Very sleepy, going to bed now, thank you both for your help so far!

---

### Post by Stratos01 on 2008-11-17
> **Zill said:**
> No - that's far too drastic at this stage. ;-)

To reinstall a package simply open Synaptic and search for the required application (ubuntu-desktop).  Then right click on the name and select "Mark for Reinstallation".  Click "Apply" to reinstall.

I could not get to sleep so i woke up and checked on the computer to see if it had finished downloading. but when I came back it was unresponsive and then when I pressed cntl alt delete it kept getting unstable and rebooted something like 6 times in 90 seconds, There was an error screen and then I rebooted and got back in, looking normal,

I tried to go into the package manager again to install ubuntu desktop but it said the same exit error 123 again.

I will try to install the base files now..

---

### Post by Stratos01 on 2008-11-17
> **philinux said:**
> The app in question is base-files.
Nor sure if this will fix it.

[FONT=Arial]sudo apt-get --reinstall install base-files[/FONT]

oops got the same error:

user@Intel1800A:~$ sudo apt-get --reinstall install base-files
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 13 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up base-files (4.0.1ubuntu5.8.04.3) ...
find: /var/cache/fonts: No such file or directory
find: /var/cache/anthy: No such file or directory
find: /var/lib/locales: No such file or directory
chgrp 0 /etc/dictionaries-common/default.aff /etc/dictionaries-common/default.hash /etc/dictionaries-common/words 
chgrp: cannot dereference `/etc/dictionaries-common/default.aff': No such file or directory
chgrp: cannot dereference `/etc/dictionaries-common/default.hash': No such file or directory
chgrp: cannot dereference `/etc/dictionaries-common/words': No such file or directory
dpkg: error processing base-files (--configure):
 subprocess post-installation script returned error exit status 123
Errors were encountered while processing:
 base-files
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by philinux on 2008-11-17
sudo dpkg-reconfigure base-files
If that fails. 
[http://ubuntuforums.org/showthread.php?p=6183704](http://ubuntuforums.org/showthread.php?p=6183704) Post #6
If that fails either wait for bug to be fixed. Or reinstall.

---

### Post by philinux on 2008-11-17
sudo dpkg-reconfigure base-files
If that fails. 
[http://ubuntuforums.org/showthread.php?p=6183704](http://ubuntuforums.org/showthread.php?p=6183704) Post #6
If that fails either wait for bug to be fixed. Or reinstall.

Double post Forums clogged up I think. Really slow today.

---

### Post by Stratos01 on 2008-11-17
> **philinux said:**
> sudo dpkg-reconfigure base-files
If that fails. 
[http://ubuntuforums.org/showthread.php?p=6183704](http://ubuntuforums.org/showthread.php?p=6183704) Post #6
If that fails either wait for bug to be fixed. Or reinstall.

Thank you, I tried posting last night but I could not load page.

dpkg-reconfigure base files returned the same error, but I have the same description of 

Status: install ok half-configured

from the post #6 as you pointed out, so I followed the instructions but I am unable to save the file as it says that I do not have permissions. this must be really basic, but, how to I get permission? :lolflag:

---

### Post by Stratos01 on 2008-11-17
> **philinux said:**
> sudo dpkg-reconfigure base-files
If that fails. 
[http://ubuntuforums.org/showthread.php?p=6183704](http://ubuntuforums.org/showthread.php?p=6183704) Post #6
If that fails either wait for bug to be fixed. Or reinstall.

it worked!!!
I can now update without the error.
Thank you :)

But on restart there was a new error:

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.



I guess this might be a one time thing? hope so!

---

