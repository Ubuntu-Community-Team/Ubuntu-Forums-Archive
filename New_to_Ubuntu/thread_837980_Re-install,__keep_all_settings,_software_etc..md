---
title: "Re-install,  keep all settings, software etc."
date: 2008-06-23
forum: New to Ubuntu
---

### Post by laffinet on 2008-06-23
Howdy, might be a stupid question but I was wandering about this for quite a while:

I have a separate /home partition. If I was to re-install Ubuntu, mounting the existing /home partition, does that mean I keep all my settings, installed software etc. ???

---

### Post by paulderol on 2008-06-23
software no, settings yes.

if you create an apt-on-cd for the machine, it will collect all of your packages and let you install them as a repository, which would restore your programs.

---

### Post by alienexplorers on 2008-06-23
How do you go about creating an apt-on-cd disk.  I would like to create one for my system.

---

### Post by hyper_ch on 2008-06-23
just make a list of the installed software. That way you can easily fetch it again with a script

---

### Post by paulderol on 2008-06-23
there is a package in synaptic [it may also be in the "add-remove" menu] called apt on cd or aptoncd or apt-on-cd or something like that, which will let you make a cd repository out of your current package lists. just install the package like any other, and start it up. it should be pretty self-contained, and then burn that cd, test it, and go about your business. the /home folder should keep all of your settings, unless you manually modified a file not in the /home directory in order to make anything work. if so, save any such file too.

---

### Post by forestpixie on 2008-06-23
Apt-on cd only keeps the packages it doesn't keep installed software. You still have to reinstall things not installed by default.

It would be no use if you were changing versions unless the new and old packages were the same and it doesn't always work properly I've found. Personally I find it a lot easier just to copy the packages with a stick and do an apt-get update.

@hyper_ch +1  would be the easiest way to reinstall software that you want.

---

### Post by fatality_uk on 2008-06-23
One thing I do is use a master_software_install_script.sh

1. If I use Synaptec Package Manager to install software, after I have selected the software I require, I go into the file menu and then select "Generate package download script". For want of a better phrase, this gives you the command line Ububntu to download the software you have just selected. I then add this to a master script. If I need ti install all the base software again, I just run my script.

---

