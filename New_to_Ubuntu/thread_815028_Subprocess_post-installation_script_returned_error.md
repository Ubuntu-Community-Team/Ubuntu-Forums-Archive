---
title: "Subprocess post-installation script returned error..."
date: 2008-06-01
forum: New to Ubuntu
---

### Post by sjmacewan on 2008-06-01
Hey guys,
I'm pretty new to linux, so I'd like to first of all request that any help be given in complete steps. Thanks.

Ok, so anytime I try to install or remove anything I get errors of the following form. Note that the following is a result from using sudo apt-get upgrade

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up foomatic-filters (3.0.2-20071204-0ubuntu2.1) ...
Use of uninitialized value in exists at /usr/share/perl5/Debconf/Template.pm line 80.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/Template.pm line 80, <GEN1> line 9.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 9.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/Template.pm line 80, <GEN1> line 10.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 10.
Can't call method "i18n" on an undefined value at /usr/share/perl5/Debconf/Element/Noninteractive/Select.pm line 13, <GEN1> line 10.
dpkg: error processing foomatic-filters (--configure):
 subprocess post-installation script returned error exit status 9
Setting up gdm (2.20.6-0ubuntu2) ...
Use of uninitialized value in exists at /usr/share/perl5/Debconf/Template.pm line 80.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/Template.pm line 80, <GEN1> line 1.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 1.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/Template.pm line 80, <GEN1> line 1.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 1.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/Template.pm line 80, <GEN1> line 3.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 3.
Can't call method "choices" on an undefined value at /usr/share/perl5/Debconf/Question.pm line 106, <GEN1> line 3.
dpkg: error processing gdm (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 foomatic-filters
 gdm
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas?

---

### Post by sayakb on 2008-06-01
Try these command at a terminal:
```
sudo apt-get purge foomatic-filters
sudo apt-get install foomatic-filters
```

Do you really need foomatic?

---

### Post by sdennie on 2008-06-01
That seems like it might be more fundamental than just removing foomatic-filters.  Maybe there is a dependency problem that isn't installing the proper i18n perl packages or DebConf has been broken.

---

### Post by sjmacewan on 2008-06-01
no, I suppose I don't need foomatic, but if I try that purge command I get a similar error:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  foomatic-db-engine* foomatic-db-hpijs* foomatic-filters* hpijs*
  ubuntu-desktop*
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 4256kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 143112 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing foomatic-db-hpijs ...
Removing hpijs ...
Removing foomatic-db-engine ...
Removing foomatic-filters ...
Purging configuration files for foomatic-filters ...
Use of uninitialized value in exists at /usr/share/perl5/Debconf/Template.pm line 80.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/Template.pm line 80, <GEN0> line 2.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN0> line 2.
Can't call method "description" on an undefined value at /usr/share/perl5/Debconf/Question.pm line 93, <GEN0> line 2.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/Template.pm line 80.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39.


Use of uninitialized value in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 2.
^^^^this line is repeated about 200 times^^^^


Setting up gdm (2.20.6-0ubuntu2) ...
Use of uninitialized value in exists at /usr/share/perl5/Debconf/Template.pm line 80.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/Template.pm line 80, <GEN1> line 1.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 1.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/Template.pm line 80, <GEN1> line 1.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 1.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/Template.pm line 80, <GEN1> line 3.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 3.
Can't call method "choices" on an undefined value at /usr/share/perl5/Debconf/Question.pm line 106, <GEN1> line 3.
dpkg: error processing gdm (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 gdm
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by sdennie on 2008-06-01
The output of the commands you typed are fairly worrying.  Doing the following my fix things and isn't likely to make it worse:

```

sudo apt-get install -f

```

---

### Post by sjmacewan on 2008-06-01
hey,
thanks for replying so fast. Unfortunately, I've tried this already with the same results:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up gdm (2.20.6-0ubuntu2) ...
Use of uninitialized value in exists at /usr/share/perl5/Debconf/Template.pm line 80.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/Template.pm line 80, <GEN1> line 1.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 1.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/Template.pm line 80, <GEN1> line 1.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 1.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/Template.pm line 80, <GEN1> line 3.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 3.
Can't call method "choices" on an undefined value at /usr/share/perl5/Debconf/Question.pm line 106, <GEN1> line 3.
dpkg: error processing gdm (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 gdm
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by sdennie on 2008-06-01
The output of every command you've posted is very scary.  I have no idea how to fix what you've done but, if the fix ends up being, "reinstall" (which, if gdm is fundamentally broken, it may be), I would recommend not installing foomatic-filters again...

---

### Post by sjmacewan on 2008-06-01
Yeah,
I've had to reinstall so many times already that one more really couldn't hurt...but I'll wait it out to see if anyone else has a suggestion.

Also, I didn't manually install foomatic-filters, these error messages were the first I'd even heard of it.

---

### Post by shifty_powers on 2008-06-01
the foomatic-filters are part of cups iirc.

did you try

```
sudo dpkg --configure -a
```?

---

### Post by sjmacewan on 2008-06-01
I did, similar output:
> Setting up gdm (2.20.6-0ubuntu2) ...
Use of uninitialized value in exists at /usr/share/perl5/Debconf/Template.pm line 80.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/Template.pm line 80, <GEN1> line 1.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 1.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/Template.pm line 80, <GEN1> line 1.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 1.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/Template.pm line 80, <GEN1> line 3.
Use of uninitialized value in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 3.
Can't call method "choices" on an undefined value at /usr/share/perl5/Debconf/Question.pm line 106, <GEN1> line 3.
dpkg: error processing gdm (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 gdm


---

