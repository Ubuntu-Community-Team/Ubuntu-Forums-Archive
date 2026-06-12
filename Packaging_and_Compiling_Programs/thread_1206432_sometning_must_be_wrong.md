---
title: "sometning must be wrong"
date: 2009-07-07
forum: Packaging and Compiling Programs
---

### Post by wangfeng3769 on 2009-07-07
[SIZE=2]wangfeng@wangfeng-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up libwmf0.2-7 (0.2.8.4-6ubuntu1.1) ...
E: /var/lib/defoma/locked exists.
E: Another defoma process seems running, or you aren't root.
E: If you are root and defoma process isn't running undoubtedly,
E: it is possible that defoma might have aborted.
E: Please run defoma-reconfigure -f to fix its broken status.
dpkg: error processing libwmf0.2-7 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gimp:
 gimp depends on libwmf0.2-7 (>= 0.2.8.4); however:
  Package libwmf0.2-7 is not configured yet.
dpkg: error processing gimp (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of libmagickcore1:
 libmagickcore1 depends on libwmf0.2-7 (>= 0.2.8.4); however:
  Package libwmf0.2-7 is not configured yet.
dpkg: error processing libmagickcore1 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of libmagickwand1:
 libmagickwand1 depends on libmagickcore1; however:
  Package libmagickcore1 is not configured yet.
dpkg: error processing libmagickwand1 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libwmf0.2-7-gtk:
 libwmf0.2-7-gtk depends on libwmf0.2-7 (= 0.2.8.4-6ubuntu1.1); however:
  Package libwmf0.2-7 is not configured yet.
dpkg: error processing libwmf0.2-7-gtk (--configure):
[/SIZE][SIZE=2] [/SIZE][SIZE=2][COLOR=Red]dependency problems - leaving unconfigured[/COLOR][/SIZE][SIZE=2]
[/SIZE][FONT=Arial Black][SIZE=2][COLOR=Red]No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libwmf0.2-7
 gimp
 libmagickcore1
 libmagickwand1
 libwmf0.2-7-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR][/SIZE][/FONT]
[SIZE=4][COLOR=Blue]the red part always apear on my screen ,what happend ,I hope who knows the answer give me a reply 
.very urgently 
thanks[/COLOR][/SIZE]:lolflag:[SIZE=5] have a try [/SIZE]

---

### Post by badeagle on 2009-07-09
dunno what's wrong, but i'd try this:

CTRL+ALT+F1, then login at that terminal. then run the commands

sudo /etc/init.d/gdm stop
[SIZE=2]sudo defoma-reconfigure -f[/SIZE]
sudo aptitude update
sudo aptitude upgrade
sudo /etc/init.d/gdm start

you may want to write those down cause gnome (and your browser) are gonna disappear until you run the last command

---

### Post by wangfeng3769 on 2009-07-12
many thanks

---

