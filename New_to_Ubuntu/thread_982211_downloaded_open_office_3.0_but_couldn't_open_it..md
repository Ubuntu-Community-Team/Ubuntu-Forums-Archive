---
title: "downloaded open office 3.0 but couldn't open it."
date: 2008-11-14
forum: New to Ubuntu
---

### Post by the ig on 2008-11-14
yep - downloaded it 3 days ago.
went into recent documents but was notified 'file does not exist'.
could it be my version of ubuntu too old?
i don't even know how to find my basic system specifications to work that out!
or, some shield needs to be deactivated?
sorry, really basic stuff - just got this computer passed on by friend and am completely at sea!
thanks,
l.

---

### Post by wolfen69 on 2008-11-14
did you download the .deb version? if not, go [here]("http://download.openoffice.org/other.html#en-US") and download the linux deb version. then just double click to install.

---

### Post by canadianwriterman on 2008-11-14
If you downloaded the .deb version from the OpenOffice website, it creates a folder containing a directory called "RPMS." You will need to convert those RPMS to .deb files and then install them. If you've already done this, but just can't find the file that runs OpenOffice, you'll find it in the directory called "opt" in a folder for OOo 3.0. Run the file called "soffice."

---

### Post by the ig on 2008-11-14
ok - so downloaded the deb file from the page suggested by wolfen69. however,
it didn't automatically install when i double clicked it. it just broke down into it's component folders.
neither could i see a file called RMPS, where would this be?
best,
l.

---

### Post by shifty_powers on 2008-11-14
> **canadianwriterman said:**
> If you downloaded the .deb version from the OpenOffice website, it creates a folder containing a directory called "RPMS." You will need to convert those RPMS to .deb files and then install them. If you've already done this, but just can't find the file that runs OpenOffice, you'll find it in the directory called "opt" in a folder for OOo 3.0. Run the file called "soffice."

sorry but no you don't need to do any conversion.........


just uninstall all oo2.4 components in synaptic.

download the archive file, and extract it to the desktop. (right click and extract here, assuming you have downloaded to desktop)

```
sudo dpkg --install --recursive ./DEBS
```

(assuming you have 8.10)

---

### Post by LowSky on 2008-11-14
i hope these instructions make sense

[http://tnerd.com/2008/10/26/open-office-3-install-open-office-3-on-ubuntu-in-4-easy-steps/](http://tnerd.com/2008/10/26/open-office-3-install-open-office-3-on-ubuntu-in-4-easy-steps/)

---

### Post by shifty_powers on 2008-11-14
if you uninstall oo2.4 completely first, then wehn you install oo3 it will create all the launchers for you...

---

### Post by shifty_powers on 2008-11-14
[http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.0](http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.0)

is the link for the ubuntu installers btw.

then just follow my instructions in above...

---

### Post by cliffm on 2008-11-15
hope this is the place to ask?
I am having the same problem with OOo3
I have followed shifty_powers steps.
un-installed OOo2.4 using synaptic package manager
down loaded OOo3 from [http://openoffice.bouncer.osuosl.org...&version=3.0.0](http://openoffice.bouncer.osuosl.org...&version=3.0.0)
to my desktop
in terminal ran sudo dpkg --install --recursive ./DEBS
password
dpkg: find for --recursive returned unhandled error -1
i am using Ubuntu 8.04

---

### Post by shifty_powers on 2008-11-15
heh. yep, that why i wrote i was assuming that the op was using 8.10, which treats the desktop differently. You need to download to desktop then,

```
cd ~/Desktop
```

then

```
sudo dpkg --install --recursive ./DEBS
```

---

### Post by cliffm on 2008-11-15
> **shifty_powers said:**
> heh. yep, that why i wrote i was assuming that the op was using 8.10, which treats the desktop differently. You need to download to desktop then,

```
cd ~/Desktop
```

then

```
sudo dpkg --install --recursive ./DEBS
```


still no joy. this is the result

cliffm@cliffm-desktop:~$ cd ~/Desktop
cliffm@cliffm-desktop:~/Desktop$ sudo dpkg --install --recursive ./DEBS
find: ./DEBS: No such file or directory
dpkg: find for --recursive returned unhandled error -1
cliffm@cliffm-desktop:~/Desktop$ ls
EPSON Scan.desktop                    Photo Impression 6.desktop
OOO300_m9_native_packed-1_en-US.9358
cliffm@cliffm-desktop:~/Desktop$ 

Guess i'll wait for the next release
Thanks shifty_powers
Cliffm

---

### Post by shifty_powers on 2008-11-15
well the other way is to go into the folder in nautilus and just double click on each deb to install it... annoying but it should work

edit:

```
cd ~/Desktop/OOO300_m9_native_packed-1_en-US.9358
```

and

```
sudo dpkg --install --recursive ./DEBS
```

should also work D:

---

### Post by ugm6hr on 2008-11-15
I would recommend just following the advice given here:
[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

It works fine if you follow it step by step.

Remember to download the correct .deb (32 vs 64-bit) tar package (and extract it).

---

