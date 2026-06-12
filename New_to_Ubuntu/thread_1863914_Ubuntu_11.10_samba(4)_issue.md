---
title: "Ubuntu 11.10 samba(4) issue"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by devilskull on 2011-10-18
Hello to all,
I'm kinda new to linux.(ubuntu 11.10 - 64bit)
As I was messing around with my samba install, i can no longer get samba to start. Already tried in the terminal , shows that samba4 isn't installed. So I did install it trough "sudo apt-get install samba4
", but with no result.
Also I cant acces my network folders anymore, I get a warning something like "Could not display "network:///"." and "Nautilus cannot handle "network" locations.
I also tried in synaptic package manager to delete all files related to samba, and re-installing samba, but the problems remain.:(
What should I do?
Any help is appreciated, I really want to learn all about linux

Greetz;)

---

### Post by devilskull on 2011-10-20
nobody....?:o

---

### Post by kemtnbkr on 2011-10-20
From what I see, Samba4 is an alpha release still...

Unless you're planning to help look for bugs on the alpha of samba4, I'd recommend just using 'normal' samba-
```
sudo apt-get install samba
```

Will that work?  Also, what do you want to install the Samba package for?  the package 'samba' is the samba server- it allows you to set up a network-shared folder.  From your issues with Nautilus not displaying the desired network location, I think you'd need 'smbclient', which is the client-side of the samba, eg. getting the files.  I'm still not 100% sure what you're wanting to do, but try this if you're attempting to get and not receive files over samba:
```
sudo apt-get install smbclient
```

Good luck!  I'm not by any means an expert on samba, btw.  All I know of it is from setting up a samba share on my Linux box.  So take my advice with a grain of salt;)

---

### Post by kemtnbkr on 2011-10-20
Also, just out of curiosity, could you run these 2 commands and post the output?

```
dpkg -l | grep samba
```

```
dpkg -l | grep smb
```

dpkg -l lists all your installed packages; the | 'feeds' the output to grep, which searches through it for instances of the supplied term.  So, this will show exactly what you have installed for samba, along with support files, and smbclient.

---

### Post by devilskull on 2011-10-20
> **kemtnbkr said:**
> Also, just out of curiosity, could you run these 2 commands and post the output?

```
dpkg -l | grep samba
``````
dpkg -l | grep smb
```dpkg -l lists all your installed packages; the | 'feeds' the output to grep, which searches through it for instances of the supplied term.  So, this will show exactly what you have installed for samba, along with support files, and smbclient.

output of "dpkg -l | grep samba":
wouter@wouter-Aspire-6935:~$ dpkg -l | grep samba
ii  gadmin-samba                           0.2.9-3                                  GTK+ configuration tool for samba
ii  libsamba-hostconfig0                   4.0.0~alpha17~git20110807.dfsg1-1ubuntu1 Samba host configuration library
ii  libsamba-policy0                       4.0.0~alpha17~git20110807.dfsg1-1ubuntu1 Samba policy management
ii  libsamba-util0                         4.0.0~alpha17~git20110807.dfsg1-1ubuntu1 Samba utility function library
ii  python-samba                           4.0.0~alpha17~git20110807.dfsg1-1ubuntu1 Python bindings for Samba
ii  samba                                  2:3.5.11~dfsg-1ubuntu2                   SMB/CIFS file, print, and login server for Unix
ii  samba-common                           2:3.5.11~dfsg-1ubuntu2                   common files used by both the Samba server and client
ii  samba-common-bin                       2:3.5.11~dfsg-1ubuntu2                   common files used by both the Samba server and client
ii  samba-dsdb-modules                     4.0.0~alpha17~git20110807.dfsg1-1ubuntu1 Samba Directory Services Database
rc  samba4                                 4.0.0~alpha17~git20110807.dfsg1-1ubuntu1 SMB/CIFS file, NT domain and active directory server (version 4)
ii  samba4-common-bin                      4.0.0~alpha17~git20110807.dfsg1-1ubuntu1 Samba 4 common files used by both the server and the client
ii  system-config-samba                    1.2.63-0ubuntu4                          GUI for managing samba shares and users

output of "dpkg -l | grep smb"
wouter@wouter-Aspire-6935:~$ dpkg -l | grep smb
ii  libsmbclient                           2:3.5.11~dfsg-1ubuntu2                   shared library for communication with SMB/CIFS servers
ii  smbclient                              2:3.5.11~dfsg-1ubuntu2                   command-line SMB/CIFS clients for Unix


I mainly want to use samba for setting op a little sharing/printing network between my ubuntu machine and 2 windows machines.

When I try to start samba trough the icon or trough the terminal, I have to give my administrator-password, but after that nothing happens....

Thanks alot for the help already...:D

---

### Post by kemtnbkr on 2011-10-20
As I already mentioned, I'm no Samba expert.  

However, a quick perusal of your packages reveals no glaring errors other than the fact that your samba4 package isn't installed (that's what the 'rc' means , where all the others have 'ii'), but you still have 'samba4-common-bin' installed. That may be causing some of your problems, but I don't think that would have caused Nautilus to be unable to display the network locations.  However, there is a bug with nautilus and SMB/CIFS- just be warned.

Also, I see you have some GUI Samba tools, but Samba isn't too difficult to configure with the command line: just google it, there's tons of tutorials out there; good way to learn linux :)

Here is a (outdated) thread on how to setup samba, which looks like it will roughly meet your requirements:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Good luck!  Looks difficult, especially with this being your first major adventure with learning Linux.

---

