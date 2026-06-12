---
title: "Wireless Not Saved When Re-Boot+The Need For Firewall &amp; Virus Checkers"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by paulm2008 on 2008-07-26
Good Morning,

I have a couple of questions regarding installation and wireless security

My first question is basically a fundamental querie

  

Initially ensuring that the software sources were disabled to only allow code from the installation CD to be defined i follows the following instructions to install the wireless adapter:



Code:
wget [http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.49.tar.gz](http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.49.tar.gz)
wget [http://www.avengergear.com/upload/WG111v3.tar.bz2](http://www.avengergear.com/upload/WG111v3.tar.bz2)
tar xvvf ndiswrapper-1.49.tar.gz
tar xvvf WG111v3.tar.bz2For others use the same ndiswrapper code but you will need to find your own .inf and .sys files requires for your USB adapter.

Step 2 - Installing the drivers

This code for WG111v3:

Code:
cd ndiswrapper-1.53
sudo make
sudo apt-get remove ndiswrapper-common
sudo apt-get install build-essential
sudo make install
sudo ndiswrapper -i ../WG111/WG111v3.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
exit


This is good - it worked [when I disabled software source].

However when I re-boot the system I have to go through the same process every time to install the driver to get online - some how the installation is not stored - its a bit of a pain - Any information on this issue would be gratefully received.

My second issue a quick one - About internet security

In windows there are virus scanners and firewalls etc... is there any similar software which should/must be used for Linux ?

Regards

Paul

---

### Post by lisati on 2008-07-26
Secirty: have a look here: [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

### Post by paulm2008 on 2008-07-26
Thank you very much - it's a real monster thread !!

Regards

Paul

---

### Post by lisati on 2008-07-26
I just realised I posted the wrong link after clicking on the wrong bookmark. It should have been [http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421) - sorry about that!

---

### Post by Paqman on 2008-07-26
> **paulm2008 said:**
> Thank you very much - it's a real monster thread !!


Quick answer re: antivirus/firewalls

Antivirus: Not required for a desktop system. The virus threat is minute, and taken care of by staying current with your security updates.

Firewall: Default install is pretty secure, there are no services listening and therefore no vulnerabilities. If you install any server-type packages you may want to look into Firestarter (GUI) or ufw (CLI) to check your settings.

---

### Post by paulm2008 on 2008-07-26
lisati : No problem - and thank you for the update - The long thread I think is worth a read too
Cheers
Paul

---

### Post by paulm2008 on 2008-07-26
> **Paqman said:**
> 
Firewall: Default install is pretty secure, there are no services listening and therefore no vulnerabilities. If you install any server-type packages you may want to look into Firestarter (GUI) or ufw (CLI) to check your settings.

Thank You - I realised Ubuntu Linux was probably more secure than Windows - I just wanted to make sure I was not leaving myself open to abuse

Regards

Paul

---

### Post by paulm2008 on 2008-07-26
> **paulm2008 said:**
> Good Morning,


Questions regarding installation and wireless security

My first question is basically a fundamental querie

  

Initially ensuring that the software sources were disabled to only allow code from the installation CD to be defined i follows the following instructions to install the wireless adapter:



Code:
wget [http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.49.tar.gz](http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.49.tar.gz)
wget [http://www.avengergear.com/upload/WG111v3.tar.bz2](http://www.avengergear.com/upload/WG111v3.tar.bz2)
tar xvvf ndiswrapper-1.49.tar.gz
tar xvvf WG111v3.tar.bz2For others use the same ndiswrapper code but you will need to find your own .inf and .sys files requires for your USB adapter.

Step 2 - Installing the drivers

This code for WG111v3:

Code:
cd ndiswrapper-1.53
sudo make
sudo apt-get remove ndiswrapper-common
sudo apt-get install build-essential
sudo make install
sudo ndiswrapper -i ../WG111/WG111v3.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
exit


This is good - it worked [when I disabled software source].

However when I re-boot the system I have to go through the same process every time to install the driver to get online - some how the installation is not stored - its a bit of a pain - Any information on this issue would be gratefully received.

Regards

Paul


Re-Issue

---

### Post by eightmillion on 2008-07-26
paulm2008, do a 'sudo gedit /etc/modules'. Make sure that ndiswrapper is listed. If it's not, add it on its own separate line.

---

### Post by paulm2008 on 2008-07-26
> **eightmillion said:**
> paulm2008, do a 'sudo gedit /etc/modules'. Make sure that ndiswrapper is listed. If it's not, add it on its own separate line.

Thank you I will give it a go.  

Regards

Paul

---

### Post by paulm2008 on 2008-08-20
Good Afternoon, I was hoping I could sort this problem out myself and hence have not been on the forum for a couple of week's - but alas, I have been defeated !!

I'm still having difficulty setting up my wireless adapter.  Essentially I have to go through the re-install process every time I boot into Ubuntu.  Even so this is a real hit and miss process [i.e. numerous re-boots, re-install's [Network Driver], wireless configuration [via system-administration-network]].

Is this the expected mode of operation or would one expect the system to be correctly configured on Boot ?

To answer a previous question I have looked at the file modules in /etc/ and indeed it does reference ndiswrapper.  But do I need to set something up in my .bash file?

Any help would be most appreciated

Regards

Paul

---

### Post by paulm2008 on 2008-08-23
Issue - unresolved - can anyone assist please ?
Regards
Paul

---

### Post by paulm2008 on 2008-09-10
Unresolved - Any Ideas - Thank you

---

### Post by stooshbunutu on 2008-12-09
seeing as these queries were based on my tutorial have a look at the revied version with a different version of ndiswrapper, maybe that will help.

see my tutorial:
[On My Website]("http://helpbuntu.mstrutt.co.uk/wireless.html")
[On Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=732827&highlight=wg111v3")

---

