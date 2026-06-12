---
title: "Program to backup &amp; restore programs"
date: 2017-01-25
forum: New to Ubuntu
---

### Post by waltd on 2017-01-25
Is there a way to backup and restore all my installed programs?  For example, if I want to test a new Ubuntu flavor distro is there a program that will automate the backup and restore of all programs?  In this way I can automatically restore the programs into the new distro without having to install each one, one at a time.  
      I'm using Grsync to backup my Home folder.  This backup will contain all my data and configurations.  Thanks.

---

### Post by RobGoss on 2017-01-25
Hello and welcome, you can try **Aptik**, from what I hear it's a great tool for backing up your applactions, I believe it's  also available in the Ubuntu Repository as well  

Aptik
[https://launchpad.net/apt-toolkit](https://launchpad.net/apt-toolkit)

You can also read about it here
[http://www.teejeetech.in/2016/04/upgrade-to-ubuntu-1604-with-aptik.html?m=1](http://www.teejeetech.in/2016/04/upgrade-to-ubuntu-1604-with-aptik.html?m=1)

---

### Post by oldrocker99 on 2017-01-25
I use grsync myself.

---

### Post by SeijiSensei on 2017-01-25
You can use the --get-selections and --set-selections feature of dpkg.  Use the first to create a list of the installed packages on the machine.  Then use the latter to tell the new machine to install the same set of packages.  See the [manual page for dpkg]("http://manpages.ubuntu.com/manpages/xenial/man1/dpkg.1.html") by typing "man dpkg" at the prompt.

---

### Post by oldfred on 2017-01-25
I use dpkg and include it as a command in my rsync script, so my backup includes the latest list of apps.

 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade
#IF you get this error:
dpkg: warning: package not in database
sudo apt-get install dselect
sudo dselect 
   -> Update
   -> Install 
   and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings'

---

