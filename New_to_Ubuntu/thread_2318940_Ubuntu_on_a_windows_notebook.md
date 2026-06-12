---
title: "Ubuntu on a windows notebook"
date: 2016-03-30
forum: New to Ubuntu
---

### Post by Clifford_Sarokoff on 2016-03-30
I've been asked to help install Ubuntu, most likely the final edition of 16.04 but 14.4 is also a possibility.   If I boot-up Ubuntu from the install disk and all is well, is this an indication that the install should go smoothly?
CliffordS

---

### Post by yancek on 2016-03-30
>    If I boot-up Ubuntu from the install disk and all is well, is this an indication that the install should go smoothly?

No, it's an indication that you are able to boot the Ubuntu installation medium.  When you say "windows notebook", do you mean a notebook which came with some unknown version of windows pre-installed on it?  If that's the case, before anyone here can give you any realistic advice, you would at least have to let us know which windows version that might be.  Since the release of windows 8, a different system of booting is used.  If you use the older MBR with the newer UEFI, one of your systems will not boot and it can be very problematic to get it fixed, especially if you are not familiar with the various bootloader so, which windows you are using is a good starting point and whether you have windows using UEFI or MBR is also important.

---

### Post by Clifford_Sarokoff on 2016-03-30
Thanks for the reply.  Windows 7 is on the computer.  We do not intend to dual-boot. Ubuntu will be the only OS on the notebook.  I plan a new install, overwriting the hard drive.

---

### Post by Bucky Ball on 2016-03-30
If you have a look for 'replace windows with ubuntu' you'll get some ideas. You'll need to check in the BIOS and see if you are using UEFI in Windows and decide whether you want to go with UEFI or not.

14.04 LTS is a long-term support release supported until 2019 so safe to install that as you can upgrade LTS to LTS. 14.04 upgrades to 16.04 LTS anytime until 2019 via the net so that allows you to leave it til the dust settles with 16.04 before you install.

---

### Post by RobGoss on 2016-03-30
Hello and welcome, I have an HP Netbook and it's currently running Ubuntu 16.04, It seems to run ok with only 1.5 GB of Ram and a 60 GB hard drive. It really depends on the specs that determine how your machine will preform.

---

### Post by yancek on 2016-03-30
The first link below is to instructions on the Ubuntu site to install Ubuntu 14.04 as the only operating system on the computer.  Simplest way in that case is to select the option to "Erase Disk and install Ubuntu".   If you have any personal data on the hard drive, get it off and copy it elsewhere before beginning.  If you want more details on installing and Linux in general, the second link below is much more detailed and informative.

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by RobGoss on 2016-03-30
If you're installing only Ubuntu then it's pretty straight forward there's not really much you can mess up. Installing Ubuntu is a learning process and a good one by the way. Just make sure you remember your login details if you intend to use any.

---

### Post by howefield on 2016-03-31
> **Clifford_Sarokoff said:**
> Thanks for the reply.  Windows 7 is on the computer.  We do not intend to dual-boot. Ubuntu will be the only OS on the notebook.  I plan a new install, overwriting the hard drive.

A word of caution, ensure that you have recovery media for the Windows install.. you just never know if you might need it :)

---

