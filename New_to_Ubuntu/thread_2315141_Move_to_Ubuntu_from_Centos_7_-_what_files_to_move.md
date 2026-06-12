---
title: "Move to Ubuntu from Centos 7 - what files to move?"
date: 2016-02-26
forum: New to Ubuntu
---

### Post by louarnold on 2016-02-26
I have to move one of the computers here to Ubuntu from CentOS 7.  What files have to be saved and moved to the Ubuntu system to retain what services they have in common?

The Ubuntu computer will be used for software development and not as a server, although a Samba service will be maintained. Otherwise, I may establish a VPN server at a future time (there was none under CentOS).

There is also the matter of a large hard drive that holds all Samba files. I don't want this drive touched by the installation of Ubuntu, but I need to know what to do to avoid that. I can, of course, simply disconnect the drive until after the installation. Anything better?

Note that I don't really want a dual boot system at this time.

Any suggestions for the flavour of Ubuntu?
Lou.

---

### Post by grahammechanical on 2016-02-26
Installing any OS in the partition used by another OS will over-write everything on the partition. We can direct the Ubuntu installer to install Ubuntu onto a particular hard disk & into particular partitions. We use the Something Else option for doing that.

The default install of Ubuntu will use two partitions. One for / and one for swap. The installer will use an existing swap partition. A lot depends on the existing partition layout of Centos. You are more familiar with that than I am. I would not want to assume that Ubuntu & Centros use an identical partition layout. Or, even that 2 users have the same partition layout.

Regards.

---

### Post by Frogs Hair on 2016-02-26
The flavor depends on desktop preference. For a light traditional desktop Xubuntu or Lubuntu are good choices. Ubuntu Mate is based on the Gnome 2 desktop. Ubuntu currently  uses the Debian package system rather than RPM and this changes the configuration and package handling commands. Samba is available in Ubuntu , but I can't address setting up a share for a different drive because I've not done it.

---

### Post by louarnold on 2016-02-26
> **grahammechanical said:**
> Installing any OS in the partition used by another OS will over-write everything on the partition. We can direct the Ubuntu installer to install Ubuntu onto a particular hard disk & into particular partitions. We use the Something Else option for doing that.

The default install of Ubuntu will use two partitions. One for / and one for swap. The installer will use an existing swap partition. A lot depends on the existing partition layout of Centos. You are more familiar with that than I am. I would not want to assume that Ubuntu & Centros use an identical partition layout. Or, even that 2 users have the same partition layout.

Regards.
Keep in mind that there are two hard drives - the main one with the OS on it and the Samba drive which holds only files. I could just let the installer repartition the entire main drive with whatever it wants. That's why I asked what it likes to save that may help. I don't know that much about any Linux system, so reconfiguring anything is rather a drag. I assume then that the Samba drive will be disconnected, then reconnected after installation and then Ubuntu will be set up to auto-mount it.

---

### Post by louarnold on 2016-02-26
> **Frogs Hair said:**
> The flavor depends on desktop preference. For a light traditional desktop Xubuntu or Lubuntu are good choices. Ubuntu Mate is based on the Gnome 2 desktop. Ubuntu currently  uses the Debian package system rather than RPM and this changes the configuration and package handling commands. Samba is available in Ubuntu , but I can't address setting up a share for a different drive because I've not done it.
Gnome 2 on CentOS was OK, but it looks like its out as Gnome 3 comes in. MATE was a disaster. There is a laptop here with Mint on it; that is easy to use and takes Ubuntu apps and that's why it was suggested. I just don't know how good/easy the SW development tools are for it.

---

### Post by ecaep on 2016-02-26
This is not really  an answer, but more of a suggestion. 

If you are not sure which Ubuntu flavor to go with I would recommend trying a few out in a VM environment such as Vbox or VMplayer to make sure that Ubuntu is going to meet your expectations and requirements.

---

### Post by louarnold on 2016-02-26
> **ecaep said:**
> This is not really  an answer, but more of a suggestion. 

If you are not sure which Ubuntu flavor to go with I would recommend trying a few out in a VM environment such as Vbox or VMplayer to make sure that Ubuntu is going to meet your expectations and requirements.
Do I install the VM environment on top of CentOS or wipe out CentOS altogether and install the VM. I have no experience with VM environments.

---

### Post by ecaep on 2016-02-26
> **louarnold said:**
> Do I install the VM environment on top of CentOS or wipe out CentOS altogether and install the VM. I have no experience with VM environments.


The VM software is just an app that will run on Centos

With no experience with VMs I would recommend going with Virtualbox it's pretty user friendly for the task you are trying to accomplish.


Here is the link for the guide on how to get it installed.

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

Let me know if you have any questions.

---

### Post by louarnold on 2016-02-26
> **ecaep said:**
> The VM software is just an app that will run on Centos

With no experience with VMs I would recommend going with Virtualbox it's pretty user friendly for the task you are trying to accomplish.


Here is the link for the guide on how to get it installed.

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

Let me know if you have any questions.
OK. Thanks. What flavour of Ubuntu do you suggest for S/W development?

---

### Post by ecaep on 2016-02-26
> **louarnold said:**
> OK. Thanks. What flavour of Ubuntu do you suggest for S/W development?


Honestly I really don't have an answer I'm not a developer.

You should start with the standard one then give a few other a couple of try. 

Best place to get Linux distros is "http://distrowatch.com/". The site has pretty good explanations for all of the Linux OS's and their purposes.

---

### Post by louarnold on 2016-02-26
Hmmmm.....There is a "standard" Ubuntu, which begs the question, why didn't I see it before. Distrowatch lists it in the right hand pane under "http://distrowatch.com/" Page Hit Ranking. At the top of that list is Mint! That's a surprise.

The download page is at "http://www.ubuntu.com/download/", oddly enough.

Thanks very much and I will get back to you if I need help with VBox.
Lou.

---

