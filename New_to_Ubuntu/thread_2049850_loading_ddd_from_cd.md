---
title: "loading ddd from cd"
date: 2012-08-29
forum: New to Ubuntu
---

### Post by mark allyn on 2012-08-29
Hello everyone,
 
I am brand spanking new to Ubuntu and Linux generally. I have installed 12.04 on a rather old HP box that has NO INTERNET connectivity. I would like to install DDD GDB frontend via a cd-rom. I have copied a download of DDD onto a CD. I cannot figure out how to load the CD copy into the APPS folder. 
 
Any help would be much appreciated.
 
Thanks,
 
Mark Allyn

---

### Post by androssofer on 2012-08-29
> **mark allyn said:**
> Hello everyone,
 
I am brand spanking new to Ubuntu and Linux generally. I have installed 12.04 on a rather old HP box that has NO INTERNET connectivity. I would like to install DDD GDB frontend via a cd-rom. I have copied a download of DDD onto a CD. I cannot figure out how to load the CD copy into the APPS folder. 
 
Any help would be much appreciated.
 
Thanks,
 
Mark Allyn

Humm... when you put in the disk, can you access it from your the folder browser?

if so you should be able to copy the files from it.. 

what is the file type u downloaded?

---

### Post by mark allyn on 2012-08-29
**Hi, and thanks.**
 
**The download from the DDD site was named ddd_3.3.11-1i386.deb.  This is recognized by 7-zip as a data.tar.  If it is extracted there are some 57 files in it.  **
 
**I'll try putting the unzipped folder into a window as you suggest.  I'm a bit uncertain how to proceed from there.**
 
**Thanks for your help,**
 
**Mark Allyn**

---

### Post by Bashing-om on 2012-08-29
mark ; Hi !

   Welcome to ubuntu in general and this forum in particular.

I am not familiar withe ddd.... but here is the general guideline for .tar files.

I suggest from your home directory ...make a working directory for data.tar:
```
mkdir data-tar
```can be any name I use this for clarity.
now copy your ** ddd_3.3.11-1i386.deb. **to your working directory.
if it is in the downloads directory code:
```
cp ~/** ddd_3.3.11-1i386.deb. data-tar**
```change directory into your working directory:
```
cd data-tar
```now extract the files (as it is a deb file may be able to double click the file and extract/install automatically) else: go ahead and extract the .tar and follow the readme file for installation.

[INDENT]hth <==BDQ

[/INDENT]

---

### Post by cortman on 2012-08-29
If it's actually a .deb file you shouldn't need to extract it ( .deb IS a form of compressing/packaging files but it's executable by dpkg). Just copy it from the cd into your home directory, open a terminal and run

```
sudo dpkg -i ddd_3.3.11-1i386.deb
```

And that will install it. If there are dependencies missing dpkg will tell you right then.

---

### Post by mark allyn on 2012-08-29
Good afternoon, Bashing-Om and Cortman,
 
Thanks very much for your help on this.  I have not yet had a chance to try your methods.  What I did do before reading your replies was to right click on the .deb file on the window that opens showing the cd files.  This brought me to a window from ubuntu package manager and I felt good.  But, nothing happened when I clicked on the install button (which made sense since it was grayed-out).
 
I'm quite hopeful that your suggestions will work.  Yes, I figured out that I didn't need to do the extraction with 7-Zip.  
 
This forum is very helpful and to date most friendly.  
 
Cheers,
Mark Allyn

---

### Post by Bashing-om on 2012-08-29
mark;

 Not a problem at all... use cortman's advise in this instance.
let us know how it goes and:
If Successful please mark thread as solved (to aid others searching for answers).

[INDENT]we are all in this together <==BDQ 
[/INDENT]

---

### Post by mark allyn on 2012-08-29
Hi Bashing-Om,
 
Sorry I was slow to reply.  Had to go teach some eager MBAs.  Yes, Cortman's advice worked beautifully and I feel quite EMPOWERED.
 
BUT, I would like to pursue your suggestion a bit more, if you will.  Last I knew (several years ago I messed around with OS software and autoconfig etc.) there was a process of decompressing a tarball and then ./configure, make, make-install.  Were you suggesting that I should follow this approach to install DDD on Ubuntu?  
 
I'd really like to understand how the tarball decompression and subsequent steps work under Ubuntu.
 
This really is a wonderful forum.  Only one I know that comes close is the MASM32 forum.... (Excuse me, please).  If you could spare a moment on this, I'd appreciate it.
 
Cheers,
Mark

---

