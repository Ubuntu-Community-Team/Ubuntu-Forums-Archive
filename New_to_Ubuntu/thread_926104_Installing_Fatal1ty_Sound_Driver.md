---
title: "Installing Fatal1ty Sound Driver"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by hitmanhogan on 2008-09-21
I'm new to linux and have been having trouble installing the new Creative Labs Fatality Champion Series Driver. Many Linux users complained that this card was not supported and Creative just released the driver.  

OK, here is what I did:

I have downloaded the driver to my desktop

I unzipped the files to my desktop

NOW WHAT DO I DO?

in the help file, here is what Creative advises:

Quick install

=============


1) You must have the fully configured source for the Linux kernel and 
   ALSA which you
 want to use for this device driver. Partial installed 
   kernels (e.g. From distribution makers) may be unusable for this 
   action.



2) Run one of the following commands as root in the terminal:



   ./installer
   


   OR


   ./installer --with-alsainc=<ALSA_include_directory>



  * ALSA Source Tree

---

### Post by phidia on 2008-09-21
I think you need to install the build-essential package have your install cd ready because the package manager will ask for it. You can install the kernel source that matches the output to "uname -r" entered in a terminal.

---

### Post by markbuntu on 2008-09-21
If you are having problems getting your Creative X-FI card to work you probably need to use OSS4: 

[http://ubuntuforums.org/showthread.php?t=780961](http://ubuntuforums.org/showthread.php?t=780961)

---

### Post by hitmanhogan on 2008-09-21
build essential package is installed.  I just don't know how to install the driver.  It's a tar.bz2 file and the folder has an installer file also.

---

### Post by phidia on 2008-09-21
If you have extracted the bz2 file then (from the terminal app) cd into the directory created from unpacking and enter this > sudo ./installer

---

