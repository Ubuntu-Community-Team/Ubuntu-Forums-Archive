---
title: "problems installing the new virtualbox 1.6"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-05-04
im trying to install the new virtualbox 1.6 on ubuntu hardy heron but keep getting an error (in screenshot below)

---

### Post by HotShotDJ on 2008-05-04
You'll need to completely remove your installation of VirtualBox-OSE before installing VirtualBox 1.6 from Sun.

---

### Post by john lee on 2008-05-05
Yes I get exactly the same error message, running latest beta heron. BTW I have removed all previous Virtualboxes installations that I'd tried eg ose so that isn't the problem as suggested by previous reply. 

Any ideas for a fix? Any additional diagnostics needed? 

Regards John

---

### Post by Liv3dN8as on 2008-05-05
is there a reason you haven't installed the LTS of hardy yet?

just make sure you make a restore point.

---

### Post by HotShotDJ on 2008-05-05
> **john lee said:**
> I have removed all previous Virtualboxes installations that I'd tried eg ose so that isn't the problem as suggested by previous replyUnless you use the --purge option from the command line, or the "Mark for Completel Removal" option from within synaptic, certain files may be left behind.  Also, with VirtualBox-OSE, the virtualbox-ose-modules may need to be removed separately.  Once you've confirmed that you've removed all the old stuff, and if you are still getting that error, you may have to manually remove (as root) the offending module.

---

### Post by john lee on 2008-05-05
Do not understand the 'install the hardy lts' point from Liv3dN8at all! I'm running the latest hardy release 8.04, with the very few  updates since.   

I'm afraid that, when I was (unsuccessfully!) trying to get Virtualbox (ose & not ose) working with my heron beta, & having problems with getting the right kernel module, I tried installing all sort of modules stuff as advised by various people from ubuntu & virtualbox sites. I'm not a linux or ubuntu guru- just started, so it isn't clear what I need to remove & how to do it. I've just downloaded the v1.6 .deb & done an install from the gui hpoing that latest version would fix my problems. 

So any suggestions as to what exactly I should delete/uninstall & how, from which places in system, via terminal would be good. 

The fact that I got exactly the same error screen as kamitsukai, the original fault reporter suggets that there may be fault/omission in the install script anyway, since I guess he didn't do all the crazed things that I tried to get Virtualbox working with heron!

---

### Post by HotShotDJ on 2008-05-05
> **john lee said:**
> So any suggestions as to what exactly I should delete/uninstall & how, from which places in system, via terminal would be good.Open Synaptic.  Search for "virtualbox".  Completely remove all items that are installed using the "Mark for Complete Removal" option.

If, after making sure everything is removed, you still get the above error while trying to install the new 1.6.0 version, you'll need to remove the offending module manually from the command line.  Use the following command WITH EXTREME CARE!```
sudo rm /lib/modules/2.6.24-16-generic/misc/vboxdrv.ko
```Before running this, make SURE this is the correct path for your system. Copy the path displayed in the error message that you are getting on your system.

---

### Post by Liv3dN8as on 2008-05-05
> **john lee said:**
> Yes I get exactly the same error message, running latest beta heron. 

Sorry, you said beta. I assumed I guess.

---

### Post by john lee on 2008-05-05
update... I'd been using the ubuntu app manager to check for virtualbox stuff installed. When I used synaptic as suggested, I found some more virtualbox stuff installed. Removed these. Not sure why synaptric gives different results to the ubuntu app manager... 

Anyway, the 1.6 install now finishes ok & installs the virtualbox gui etc. If I  try to start a VM it fails with a 'driver missing' message. During the installation I get a problem (again!) compiling the kernel interface ie: 

quote VirtualBox will not start until this problem is fixed. Please consult /var/log/vbox-install.log to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them and execute
  /etc/init.d/vboxdrv setup
as root. 
unquote

If I look at the log I get
more vbox*.*
Makefile:127: *** Error: unable to find the sources of your current Linux kernel
. Specify KERN_DIR=<directory> and run Make again. Stop.
which confirms that it can't find source. 

How/from where do I get the kernel sources it's looking for so that this works? From where? Why doesn't this work properly as part of the heron installation? Why is all so hard? 

Regards John

---

### Post by graben3 on 2008-05-05
> **john lee said:**
> update... I'd been using the ubuntu app manager to check for virtualbox stuff installed. When I used synaptic as suggested, I found some more virtualbox stuff installed. Removed these. Not sure why synaptric gives different results to the ubuntu app manager... 

Anyway, the 1.6 install now finishes ok & installs the virtualbox gui etc. If I  try to start a VM it fails with a 'driver missing' message. During the installation I get a problem (again!) compiling the kernel interface ie: 

quote VirtualBox will not start until this problem is fixed. Please consult /var/log/vbox-install.log to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them and execute
  /etc/init.d/vboxdrv setup
as root. 
unquote

If I look at the log I get
more vbox*.*
Makefile:127: *** Error: unable to find the sources of your current Linux kernel
. Specify KERN_DIR=<directory> and run Make again. Stop.
which confirms that it can't find source. 

How/from where do I get the kernel sources it's looking for so that this works? From where? Why doesn't this work properly as part of the heron installation? Why is all so hard? 

Regards John


Just go in synaptic. search for virtualbox

Youll see packages for kernel modules.
Choose the meta package 'virtualbox-ose-modules-generic' (this is a meta package that will choose the good one for you)

---

### Post by Oldsoldier2003 on 2008-05-05
The OSE version is not as good as the peul version you get from the sun download site. once you've removed the ose version completely download the deb from sun and install it, upgrading from peul versions doesn't seem to require uninstalling, you'll just have to remove the old guest additions and install the new ones.

---

### Post by kyphi on 2008-05-05
What is missing in the OSE version is USB support.

I installed VBox-OSE first (in Hardy Heron) by

sudo apt-get install virtualbox-ose virtualbox-ose-modules-2.6.24-16-generic

followed by

sudo usermod -G vboxusers -a <my name>

This will install VBox-OSE and adjust your kernel.

You can remove it via Synaptic.  Don't forget to also delete the hidden file .VitualBox in your home folder.

After removal, install VirtualBox 1.6.0 from Sun.


(I cannot get the Code tags to work here)

---

### Post by HotShotDJ on 2008-05-05
> **john lee said:**
> How/from where do I get the kernel sources it's looking for so that this works? From where? Why doesn't this work properly as part of the heron installation? Why is all so hard?Install the package "build-essential" ... that will pull in everything you need.  Then you can run "sudo /etc/init.d/vboxdrv setup"

It's really not that hard once you get used to it.  When you start using packages from outside of the main ubuntu repositories, things can get goofy from time to time.  Although, I tend to agree that there are unnecessary hurdles to getting virtualbox set up that could be corrected by setting up the dependencies a little better.  But, not being a developer, I don't know what other considerations may have contributed to the way they package it.

---

### Post by MystaMax on 2008-05-09
The steps above worked for me. First, I went into add/remove, unchecked VirtualBox OSE, and applied changes. I then launched Synaptic, and removed the Virtualbox kernel modules (search for Virtualbox and mark modules for removal). Then I went to sun.com, downloaded the 1.6 PUEL version and installed the deb package.

[http://www.sun.com/software/products/virtualbox/get.jsp](http://www.sun.com/software/products/virtualbox/get.jsp)

This all started with me not being able to install 8.04 LTS server on Virtualbox OSE 1.5.6. I ended up uninstalling VB OSE, and installing PUEL version 1.6

Thanks for the tips!

---

