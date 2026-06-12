---
title: "labview install errors"
date: 2009-01-23
forum: Programming Talk
---

### Post by octopusfinley on 2009-01-23
Hey there. I'm trying to install labview into ubuntu by following instructions I found here [http://ubuntuforums.org/newthread.php?do=newthread&f=39](http://ubuntuforums.org/newthread.php?do=newthread&f=39)

My problem is that I forgot to put the command --scripts while I was running an rpm file through alien, so I got this:

finley@squid:~/LV8pkg$ sudo alien -k labview85-core-8.5-1.i386.rpm 
Warning: Skipping conversion of scripts in package labview85-core: postinst postrm prerm
Warning: Use the --scripts parameter to include the scripts.

so then i tried this:
finley@squid:~/LV8pkg$ sudo alien -k --scripts labview85-core-8.5-1.i386.rpm 

and got

mkdir: cannot create directory `labview85-core-8.5': File exists
unable to mkdir labview85-core-8.5:  at /usr/share/perl5/Alien/Package.pm line 257.
 
So basically I need to fix this problem without completely killing my previous efforts and my computer. Any ideas?

---

### Post by dmitriyp13 on 2009-03-17
Easiest thing is just to start over and delete that folder.

---

