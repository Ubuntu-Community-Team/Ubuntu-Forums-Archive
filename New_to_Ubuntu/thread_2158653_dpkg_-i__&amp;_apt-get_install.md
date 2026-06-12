---
title: "dpkg -i  &amp; apt-get install"
date: 2013-06-29
forum: New to Ubuntu
---

### Post by bdss on 2013-06-29
Hello All,

I am learning Linux and waned to install a package  **hv3_3.0~fossil20110109-2_all.deb**

Came to know about two command available dpkg -i  & apt-get install , Of which later one is better 

[B]But when i am trying to install it with dpkg -i Its  getting installed although not completely ( iu )but with apt-get no progress ( un )
[/B]
Please advise

  root@ubuntu:/home/bdss/Downloads# ls 
hv3_3.0~fossil20110109-2_all.deb
root@ubuntu:/home/bdss/Downloads# **dpkg -i hv3_3.0~fossil20110109-2_all.deb**
Selecting previously deselected package hv3.
(Reading database ... 123283 files and directories currently installed.)
Unpacking hv3 (from hv3_3.0~fossil20110109-2_all.deb) ...
dpkg: dependency problems prevent configuration of hv3:
 hv3 depends on tk (>= 8.5.0-1); however:
  Package tk is not installed.
 hv3 depends on tk-html3; however:
  Package tk-html3 is not installed.
 hv3 depends on libsqlite3-tcl; however:
  Package libsqlite3-tcl is not installed.
 hv3 depends on tcllib; however:
  Package tcllib is not installed.
dpkg: error processing hv3 (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for man-db ...
Errors were encountered while processing:
 hv3
root@ubuntu:/home/bdss/Downloads# **dpkg -l hv3**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
[B]||/ Name                          Version                       Description
+++-=============================-=============================-==========================================================================
[COLOR=#ff0000]iU[/COLOR]  hv3                           3.0~fossil20110109-2          Lightweight web browser[/B]

root@ubuntu:/home/bdss/Downloads# **dpkg -P hv3**
(Reading database ... 123339 files and directories currently installed.)
Removing hv3 ...
Purging configuration files for hv3 ...
Processing triggers for man-db ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...

root@ubuntu:/home/bdss/Downloads# **dpkg -l hv3**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
[B]||/ Name                          Version                       Description
+++-=============================-=============================-==========================================================================
un  hv3                           <none>                        (no description available)[/B]
root@ubuntu:/home/bdss/Downloads# **apt-get install hv3_3.0~fossil20110109-2_all.deb**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package hv3_3.0~fossil20110109-2_all.deb
E: Couldn't find any package by regex 'hv3_3.0~fossil20110109-2_all.deb'
root@ubuntu:/home/bdss/Downloads# **dpkg -l hv3**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
[B]||/ Name                          Version                       Description
+++-=============================-=============================-==========================================================================
[COLOR=#ff0000]un[/COLOR]  hv3                           <none>                        (no description available)[/B]

Thanks In Advance

---

### Post by bdss on 2013-06-30
Hi ,

What needs to be done for enable aptitude and use it 

root@ubuntu:/home/bdss/Downloads# aptitude install hv3_3.0~fossil20110109-2_all.deb
The program 'aptitude' can be found in the following packages:
 * aptitude
 * aptitude-gtk

Thanks In Advance

---

### Post by lisati on 2013-06-30
aptitude hasn't been included by default for a couple of releases now, you will need to install it before using it:
```

sudo apt-get install aptitude

```

---

### Post by claracc on 2013-06-30
what ubuntu are you using?

In 12.04, aptitude is in the repositories, not need to download from other sites.

In a xterm, simply run ```
sudo apt-get install aptitude
```
you are asked for your pass, introduce it and it is all.

---

### Post by newb85 on 2013-06-30
For that matter, there's probably no reason the OP needs to use aptitude.  
Bdss, I'm guessing you copied that install command from somewhere. Would you mind telling us where? The instructions you have are probably out-of-date or sub-optimal.

---

### Post by newb85 on 2013-06-30
Just did a Google search for the package you were trying to install with aptitude. It's in the Ubuntu repositories, so you should be able to install it with the Software Center or apt-get. No web browser download needed. No aptitude needed.

---

### Post by claracc on 2013-06-30
What for do you want the package hv3_3.0~fossil20110109-2_all.deb ?

Where have you downloaded from?.

running the command:

```
dpkg -i hv3_3.0~fossil20110109-2_all.deb
```

advice you that there is a dependency problem between the package and the software in your system. For this reason, it is not installed.

I recommend you look for the appropriate package for your ubuntu release. You can look for it through software center or synaptic.

---

### Post by newb85 on 2013-06-30
There are major differences between dpkg and apt-get.  Apt-get installs packages from the software sources you have set up in your machine (the repos by default), while dpkg installs from specified files.  Apt-get takes care of dependencies. Dpkg does not. 

Also, it's not really good practice to run as root. It's better to use sudo.

Try this:
```
 sudo apt-get install hv3 
```

---

### Post by bdss on 2013-06-30
> **newb85 said:**
> There are major differences between dpkg and apt-get.  Apt-get installs packages from the software sources you have set up in your machine (the repos by default), while dpkg installs from specified files.  Apt-get takes care of dependencies. Dpkg does not. 

Also, it's not really good practice to run as root. It's better to use sudo.

Try this:
```
 sudo apt-get install hv3 
```


Thanks for the reply :)

Actually i downloaded it from "[http://www.debian.org/distrib/packages#view](http://www.debian.org/distrib/packages#view) " 

& this is URL not included in /etc/apt/sources.list file 

Is that the reason , why its not getting installed using apt-get ?

Also if I want to install new software using apt-get , do i have to add it url ( ex "[http://www.debian.org/distrib/packages#view](http://www.debian.org/distrib/packages#view) " ) to my sources.list file

---

### Post by bdss on 2013-06-30
> **claracc said:**
> what ubuntu are you using?

In 12.04, aptitude is in the repositories, not need to download from other sites.

In a xterm, simply run ```
sudo apt-get install aptitude
```
you are asked for your pass, introduce it and it is all.

Thanks for the reply.

Mine is Ubuntu 11.10 ,

Do i need to install aptitude before being able to use it ?

Also i downloaded hv3_3.0~fossil20110109-2_all.deb from  [http://www.debian.org/distrib/packages#view](http://www.debian.org/distrib/packages#view) to my local disk and now is trying to install  it.Will the installation of hv3 using aptitude work ?

*Its not there in my /etc/apt/sources.list file

---

### Post by bdss on 2013-06-30
> **newb85 said:**
> For that matter, there's probably no reason the OP needs to use aptitude.  
Bdss, I'm guessing you copied that install command from somewhere. Would you mind telling us where?** The instructions you have are probably out-of-date or sub-optimal.**

Just did a Google search for the package you were trying to install with  aptitude. It's in the Ubuntu repositories, so you should be able to  install it with the Software Center or apt-get. No web browser download  needed. No aptitude needed.



Thanks for the reply.

I got it from internet and it was written aptitude is the higher version of apt-get , dpkg etc

Please let me know if its incorrect

---

### Post by Cheesemill on 2013-06-30
If you are still using 11.10 then you won't be able to install anything from the repositories any more (using apt-get or aptitude).

This is because 11.10 reached end-of-life in April meaning that the repositories have been taken off line. It will also receive no more security updates or bug fixes.

I would seriously reccomend upgrading to a version of Ubuntu that is still supported such as 12.04 or 13.04.

---

### Post by ikt on 2013-06-30
> **bdss said:**
> Also if I want to install new software using apt-get , do i have to add it url ( ex "[http://www.debian.org/distrib/packages#view](http://www.debian.org/distrib/packages#view) " ) to my sources.list file

By default ubuntu comes with huge software repositories by default.

[https://apps.ubuntu.com/cat/applications/quantal/hv3/](https://apps.ubuntu.com/cat/applications/quantal/hv3/)

Looks like hv3 is already packaged in Ubuntu 12.10 and 13.04.

So if you install 12.10 or 13.04 then to install hv3 all you have to do is:

```
sudo apt-get install hv3
```

With regard to your initial issue:

```
root@ubuntu:/home/bdss/Downloads# dpkg -i hv3_3.0~fossil20110109-2_all.deb
Selecting previously deselected package hv3.
(Reading database ... 123283 files and directories currently installed.)
Unpacking hv3 (from hv3_3.0~fossil20110109-2_all.deb) ..
.
[B]dpkg: dependency problems prevent configuration of hv3:

hv3 depends on tk (>= 8.5.0-1); however:
Package tk is not installed.

hv3 depends on tk-html3; however:
Package tk-html3 is not installed.

hv3 depends on libsqlite3-tcl; however:
Package libsqlite3-tcl is not installed.

hv3 depends on tcllib; however:
Package tcllib is not installed.[/B]

dpkg: error processing hv3 (--install):

dependency problems - leaving unconfigured

Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for man-db ...
Errors were encountered while processing:
hv3
```

Was the correct way to install the .deb package, however when ubuntu tried to install it came across this issue:

**Package tcllib is not installed.**

And so it couldn't install.

if you're coming from windows there's a lot less fluidity with linux and programs, in windows you can install whatever whenever but you can't keep control of all of them, you have to manually update etc. and this out of date software is a large part of why windows is more vulnerable than linux. You can manually install on linux by compiling programs, but it's a pain to do.

On linux you might want to install Package A but it relies on Package B version 1 and Package C version 2.

Package A v1:
Requires:
> Package B v1
> Package C v2

But if it can't find Package C v2 then it fails to install, like yours did.

This is a downside, but on the upside you can keep every application and library on your computer up to date with 1 command.

I'd just upgrade to 13.04, and install as first suggested, not like it costs anything.


(merged both threads since we were discussing the same topic)

---

### Post by bdss on 2013-06-30
Thanks Cheesemill & jkt 

Can you please guide me how can I upgrade from **command line**

Found the post in Forum " [http://askubuntu.com/questions/110477/how-do-i-upgrade-from-10-04-or-11-10-to-12-04](http://askubuntu.com/questions/110477/how-do-i-upgrade-from-10-04-or-11-10-to-12-04) "

[h=2]Backup[/h]"If you're using Wubi, why don't you just boot into Windows and copy the root.disk file
  Then restoring is as easy as renaming root.disk to something else, and renaming the copy to root.disk"

 

But is confused about [h=2]Graphics & PPA[/h]  , what needs to be done for 
[h=2][/h]Fyi , 

bdss@ubuntu:/$ ls /etc/X11/xorg.conf
ls: cannot access /etc/X11/xorg.conf: No such file or directory

Please advise

Thanks in advance

---

