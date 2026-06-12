---
title: "Please help!!!"
date: 2012-07-04
forum: New to Ubuntu
---

### Post by ctpuckett on 2012-07-04
I installed icoGEN 0.3.1.. It did not work. Now, after trying to uninstall it, I cannot update anything. I found some "solutions" abroad that did not work at all. I tried to reinstall the software to no avail, and I cannot install anything otherwise. Please help

---

### Post by anewguy on 2012-07-04
What kind of error message(s) are you getting when you try to install something else?  Are you using the package manager to do it?

---

### Post by ctpuckett on 2012-07-04
synaptic:
E: icogen: subprocess installed post-removal script returned error exit status 1

Ubuntu Software Center:
installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 219612 files and directories currently installed.) 
Removing icogen ... 
rm: cannot remove `/usr/share/icoGEN/data/': No such file or directory 
dpkg: error processing icogen (--remove): 
 subprocess installed post-removal script returned error exit status 1 
Errors were encountered while processing: 
 icogen 
 
      You have to configure "localepurge" with the command 
 
          dpkg-reconfigure localepurge 
 
      to make /usr/sbin/localepurge actually start to function. 
 
      Nothing to be done, exiting ... 
 
 
      You have to configure "localepurge" with the command 
 
          dpkg-reconfigure localepurge 
 
      to make /usr/sbin/localepurge actually start to function. 
 
      Nothing to be done, exiting ... 


(tried to localpurge and honestly, I do not understand it. It is telling me to get rid of files that do not start with a double letter, so on and forth.....I hate to be lacking in knowledge, but damn - this is a real *** pain)
 
Here was a suggestion which failed as well:
[http://ubuntuforums.org/showthread.php?t=1566679](http://ubuntuforums.org/showthread.php?t=1566679)

---

### Post by ctpuckett on 2012-07-05
[B][SIZE=2]I figured out what to do. It was really not that difficult.

In terminal:
[/SIZE][/B][B][B][SIZE=2]*gksudo gedit /var/lib/dpkg/status*

find the package and delete it. Make sure a space is left between the previous and following entries and save it. That is all!
 Now all updates are working fine and synaptic is working as normal.:p
[/SIZE][/B][/B]

---

### Post by codingman on 2012-07-05
Set this thread as solved from the drop-down list in the top right corner marked "Thread Tools"

---

