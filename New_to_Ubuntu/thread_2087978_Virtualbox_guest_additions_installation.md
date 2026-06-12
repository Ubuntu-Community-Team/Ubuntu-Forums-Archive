---
title: "Virtualbox guest additions installation"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by svee on 2012-11-25
I have ubuntu 12.10 server in virtualbox 4.2.4.  My host OS is lubuntu.

I have installed guest addition but when I ask for sharing folder, virtual box complains that it is not installed.
[INDENT]
The VirtualBox Guest Additions do not appear to be available on this virtual machine, and shared folders cannot be used without them. To use shared folders inside the virtual machine, please install the Guest Additions if they are not installed, or re-install them if they are not working correctly, by selecting Install Guest Additions from the Devices menu. If they are installed but the machine is not yet fully started then shared folders will be available once it is.[/INDENT]

I went through the installation already which seemed successful.
[INDENT]
$ sudo apt-get install virtualbox-guest-additions
[sudo] password for vee: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox-guest-additions is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
vee@ubuntu:~$
[/INDENT]

For installation, I mainly used instructions in following two links :

[http://virtualboxes.org/doc/installing-guest-additions-on-ubuntu/](http://virtualboxes.org/doc/installing-guest-additions-on-ubuntu/)

[https://sites.google.com/site/iancharestphd/aide-memoire/installingubuntu1204ltswithguestadditionsinvirtualbox](https://sites.google.com/site/iancharestphd/aide-memoire/installingubuntu1204ltswithguestadditionsinvirtualbox)


Reason I am installing from command line is that I have error when I try virtualbox guest additions from the VM menu :

[INDENT]Unable to mount the CD/DVD image /usr/share/virtualbox/VBoxGuestAdditions.iso on the machine Ubuntu Server. Would you like to force mounting of this medium?
Could not mount the media/drive '/usr/share/virtualbox/VBoxGuestAdditions.iso' (VERR_PDM_MEDIA_LOCKED).[/INDENT]


My main reason for guest additions was to be able to share clipboard and to share some downloaded packages as wget was not able to fetch apache solr files..
 
But I am wondering if guest additions itself is an overhead for server in virtualbox which I would have liked to keep lean. If I only do remote management through ssh, does guest addition add much value at all compared to overhead (additional packages installed)...??

---

### Post by HereInOz on 2012-11-25
It sounds like you are running a command line only server as the VM.  Is that correct?  If so, I am wondering if that is the problem with guest additions.  It may be wanting a GUI to do what it needs to do.

I have no experience with running a command line server in a VM but my understanding of guest additions is that it is mainly for the GUI performance of the VM

---

### Post by pkadeel on 2012-11-25
Guest Additions are used for two main purposes I guess
1. client's graphic appearance adjustment
2. shared folder access / clip board

Now although you are not using the GUI on your client yet you will need it for your shared folders requirement.

As you are saying that when you tried to install, you got the message that it is already installed, then the most probable thing is that you just need to add your user on the client OS to be a member of "vboxsf" group (this is what i recall. it might be slightly different but will most likely contain "vbox" a starting 4 characters). This group will already be present on your client OS after the installation of guest additions.

---

### Post by svee on 2012-11-25
There is no vboxfs or similar group on my ubuntu server guest. May be some part of setup has not happened ??

  [I] $ cat /etc/group | grep vbox
   vboxusers: x:116:
   $ [/I]


I am using server without GUI. Plan to use ssh to configure remotely.

---

### Post by mansonfan78 on 2012-11-26
Try this:  open a run dialog (or a terminal) and type "gksu nautilus" without the quotes (or the name of whatever file manager you have).  Enter your password and find the iso file in the directory mentioned, right-click and select properties.  Go to "permissions" and make sure your user is allowed read/write/execute access (this shouldn't be necessary, but it might help).

---

### Post by coldraven on 2012-11-26
You have to download the guest additions to the host.
Then just double click the package.

---

### Post by coldraven on 2012-11-26
It should look like this in your file manager.
Downloaded from the VirtualBox web-site

---

### Post by mastablasta on 2012-11-26
download to host but install is in guest from mounted image: 
[http://www.virtualbox.org/manual/ch04.html#idp12082384](http://www.virtualbox.org/manual/ch04.html#idp12082384)

---

### Post by jlf2 on 2013-08-06
Has anyone seen with their OWN eyes an Ubuntu Guest on an Ubuntu host in VirtualBox that could share folders with host/guest in Host-Only network mode?  

I've been trying to do this for 20+ hours and have looked at over 100 posts, lots with good ideas, but none that say they actually got it to work.  So at this point I lean towards the idea that this is not actually possible.  

Please only reply if you yourself have actually seen this work.

Thanks.

---

