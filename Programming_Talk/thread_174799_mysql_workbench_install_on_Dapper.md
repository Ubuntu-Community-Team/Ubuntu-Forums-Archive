---
title: "mysql workbench install on Dapper"
date: 2006-05-12
forum: Programming Talk
---

### Post by slimfitstyle on 2006-05-12
Hello everyone.  I can't get mysql workbench beta to install on Dapper.  When I start it up I get a ton of errors and nothing happens.  I found some threads on the mysql forums with people having the same problems but no resolutions.  Has anyone got this to work? Thanks for any help!  BTW I'm a kind of  a n00b.

---

### Post by slimfitstyle on 2006-05-15
Anybody?  I would really like to use this.

Thanks again!

---

### Post by svdesign on 2006-05-18
[QUOTE=slimfitstyle]Anybody?  I would really like to use this.

Thanks again![/QUOTE]

I download the RPM for Red Hat Enterprise Linux 4 (x86)
Then:
sudo alien mysql-workbench-1.0.6beta-1.rhel4.i386.rpm

sudo dpkg -i mysql-workbench_1.0.6beta-2_i386.deb

And now mysql-workbench looks like try to work but doesn't. It show two empty windows and popups error "GRT environment for the Workbench could not been initialized. Please verify your installation."
and shows warning in console:
** (mysql-workbench-bin:9218): WARNING **: Error getting color presets.

Well, it still not working. I try to compile it from sources.

---

### Post by slimfitstyle on 2006-05-18
I tried it with alien as well and got similar results.  I didn't even get a window though.  Let me know if you have any luck with the sources.

---

### Post by aboel3zz on 2006-07-26
i have this error 

/usr/local/bin/mysql-workbench: line 18: 26053 Segmentation fault      $PRG-bin $*

---

### Post by dudus on 2006-07-28
No luck here either. Man this is taking years to be done

---

### Post by skaboss on 2006-10-20
Hello guys,

Several monthes has passed, and i have the same problem : did you find a solution ?

---

### Post by bibstha on 2006-10-21
Hey Finally Mysql workbench works on my edgy

Steps
Download the tar x86 binary from one of the mirrors
(not the sources)
[http://mysql.mirrors.pair.com/Downloads/MySQLGUITools/mysql-gui-tools-5.0r4-linux-i386.tar.gz]("http://mysql.mirrors.pair.com/Downloads/MySQLGUITools/mysql-gui-tools-5.0r4-linux-i386.tar.gz")
thats the url i downloaded from

You shouldnot extract it anywhere, it will give you error saying 
```
$ ./mysql-workbench
Error starting ./mysql-workbench.
The actual installation path of mysql-workbench is different from the
expected one. Please run ./mysql-workbench --update-paths (as the root
user, if needed) to have the installation directory updated.
```
Solution:
```
extract the tar in /opt and then run 
mysql-workbench
```.
Hope that helps

Cheers
bibstha

---

### Post by skaboss on 2006-10-21
Thanks a lot for the tip, bibstha.

Unfortunately, it still doesn't work for me, i get the following message : 

The GRT environment for the Workbench could not be initialized.
Please verify your installation.

---

### Post by rayworld on 2006-10-24
try this:

unset LANG
unset LC_ALL
./mysql-workbench

i have done a very powerful and complex script to run it:


```
#!/bin/bash
unset LANG
unset LC_ALL
/opt/mysql-gui-tools-5.0/mysql-workbench
```


copy, create a file, paste on it and give execution permissions to your new powerful file!.:p

---

### Post by Bizmac on 2006-10-24
Workbench works, if you extract it in opt/. its an alpha version.
The script is not necessary...
It is not usable, I try to create 2 columns within a table and workbench exit as I applied, with this error message:


(mysql-workbench-bin:26748): Gtk-WARNING **: Unable to locate theme engine in module_path: "qtengine",
** CRITICAL **: myx_grt_dict_item_set_by_path: assertion `dict != NULL' failed
aborting... ./mysql-workbench: line 103: 26748 Aborted  $PRG-bin $args


Is there another modeling solution (working) to create mysql database?

---

### Post by LinuxFab on 2006-11-14
by the way, this script DID work !
I might have the same variables, locales and all the stuff--> Im using a french environment too ;) 
That might explain why 'unsetting' LANG and LC_ALL worked for me.

---

