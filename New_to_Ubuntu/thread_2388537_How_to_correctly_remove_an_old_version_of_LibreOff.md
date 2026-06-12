---
title: "How to correctly remove an old version of LibreOffice"
date: 2018-04-04
forum: New to Ubuntu
---

### Post by jobtmp on 2018-04-04
Hello,

I've managed to install the current version of the LO (6....) but the old one (5....) still exists. 

**Q1:** What is the correct way to remove the old version? 
Comm.: I know about command 

'[COLOR=#111111][FONT=Consolas]sudo apt-get remove <application_name>[/FONT][/COLOR]'

...but am not sure what exactly the  "[COLOR=#111111][FONT=Consolas]application_name" is in this case. [/FONT][/COLOR]

**Q2: **In the newly installed LibreOffice I cannot see the "Recent documents" list of the previous version. Can the list be restored before I remove the previous version or at all?

Thanks in advance,
jobtmp

---

### Post by vanadium on 2018-04-04
sudo apt-get remove libreoffice or using your software center or synaptic.

---

### Post by jobtmp on 2018-04-04
thanks for your prompt answer. Please note that I have 2 versions of the LO installed: #5 and #6. My question is how to insure removing exactly #5 and not #6. Please advise.

---

### Post by deadflowr on 2018-04-04
How did you install version #6?

---

### Post by jobtmp on 2018-04-04
> **deadflowr said:**
> How did you install version #6?

It was messy. First I downloaded the archive from the LO depository and unpacked all .deb files which installed the modules (writer , calc,  etc). After this I have discovered a launcher, sort of, which has started the Software installation procedure. The installation was done again. NB: after the second installation all the "recent documents" list has gone but LO #5 still exist as well as #6 witch sems to work ok, except the  "recent documents" list loss.

So my questions are:

1. How to remove the #5 correctly (what is the "application name" that I should remove).
2. Is it possible to return the list of documents from #5: i.e. where it might be stored.

---

### Post by deadflowr on 2018-04-04
Then version 5 should already be gone. Since 6 should've/would've have overwritten 5.

look at
```
dpkg -l | grep libreoffice | awk '{print $1,$2,$3}'
```
post back the results.

---

### Post by jobtmp on 2018-04-04
```
sergey@home-X200CA:~$ dpkg -l | grep libreoffice | awk '{print $1,$2,$3}'
ii libreoffice-avmedia-backend-gstreamer 1:5.4.5-0ubuntu0.17.10.5
ii libreoffice-base 1:5.4.5-0ubuntu0.17.10.5
ii libreoffice-base-core 1:5.4.5-0ubuntu0.17.10.5
ii libreoffice-base-drivers 1:5.4.5-0ubuntu0.17.10.5
ii libreoffice-calc 1:5.4.5-0ubuntu0.17.10.5
ii libreoffice-common 1:5.4.5-0ubuntu0.17.10.5
ii libreoffice-core 1:5.4.5-0ubuntu0.17.10.5
ii libreoffice-draw 1:5.4.5-0ubuntu0.17.10.5
ii libreoffice-gnome 1:5.4.5-0ubuntu0.17.10.5
ii libreoffice-gtk3 1:5.4.5-0ubuntu0.17.10.5
ii libreoffice-help-en-gb 1:5.4.5-0ubuntu0.17.10.1
ii libreoffice-help-en-us 1:5.4.5-0ubuntu0.17.10.1
ii libreoffice-help-ru 1:5.4.5-0ubuntu0.17.10.1
ii libreoffice-impress 1:5.4.5-0ubuntu0.17.10.5
ii libreoffice-java-common 1:5.4.5-0ubuntu0.17.10.5
ii libreoffice-l10n-en-gb 1:5.4.5-0ubuntu0.17.10.1
ii libreoffice-l10n-en-za 1:5.4.5-0ubuntu0.17.10.1
ii libreoffice-l10n-ru 1:5.4.5-0ubuntu0.17.10.1
ii libreoffice-math 1:5.4.5-0ubuntu0.17.10.5
ii libreoffice-ogltrans 1:5.4.5-0ubuntu0.17.10.5
ii libreoffice-pdfimport 1:5.4.5-0ubuntu0.17.10.5
ii libreoffice-sdbc-hsqldb 1:5.4.5-0ubuntu0.17.10.5
ii libreoffice-style-breeze 1:5.4.5-0ubuntu0.17.10.5
ii libreoffice-style-galaxy 1:5.4.5-0ubuntu0.17.10.5
ii libreoffice-style-tango 1:5.4.5-0ubuntu0.17.10.5
ii libreoffice-writer 1:5.4.5-0ubuntu0.17.10.5
ii libreoffice6.0 6.0.2.1-1
ii libreoffice6.0-base 6.0.2.1-1
ii libreoffice6.0-calc 6.0.2.1-1
ii libreoffice6.0-debian-menus 6.0.2-1
ii libreoffice6.0-dict-en 6.0.2.1-1
ii libreoffice6.0-dict-es 6.0.2.1-1
ii libreoffice6.0-dict-fr 6.0.2.1-1
ii libreoffice6.0-draw 6.0.2.1-1
ii libreoffice6.0-en-us 6.0.2.1-1
ii libreoffice6.0-impress 6.0.2.1-1
ii libreoffice6.0-math 6.0.2.1-1
ii libreoffice6.0-ure 6.0.2.1-1
ii libreoffice6.0-writer 6.0.2.1-1
```

---

### Post by deadflowr on 2018-04-04
Ah, I see.
Seems they've made it so the new 6 version is actually called libreoffice6 instead of just libreoffice in the packaging from the LibreOffice Document foundation webpage downloads.

Now what I would do is instead of trying to remove libreoffice 5 would be to to instead try to  purge libreoffice6
see what 
```
sudo apt purge -s libreoffice6*
```
 does. (The -s stands for simulate, which will run the command but not actually do the command. Which will allow you to see what would be removed.
This will prevent errant package removals.)
If it looks like it only lists the libreoffice6 packages then run the comand without the -s flag.

After that command is run, do this
```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt update
```
and then install libreoffice
```
sudo apt install libreoffice
```
this will pull in the version 6 from Ubuntu libreoffice packaging team:
[https://launchpad.net/~libreoffice/+archive/ubuntu/ppa]("https://launchpad.net/~libreoffice/+archive/ubuntu/ppa")
(This will also allow you to keep getting newer versions as they come along automatically, just like normal updates)

Feel free to post back the *apt purge -s libreoffice6* *output if you are not sure what it says.

---

### Post by jobtmp on 2018-04-04
Thanks for your advise. Will try it tomorrow.

---

### Post by monkeybrain20122 on 2018-04-04
you should remove all your LO junks (#5 and #6) and then use the LO [ ppa ]("https://launchpad.net/~libreoffice/+archive/ubuntu/ppa")to install LO (it is LO6) , this will keep your system clean and tidy.

---

### Post by jobtmp on 2018-04-08
Please advise the correct commands to remove "the junk". I am really fresh to Linux.

---

### Post by vanadium on 2018-04-08
These commands were already provided. A safe approach I guess would be
```

sudo apt-get purge libreoffice*

```
to remove all packets and config files related to libreoffice, and assuming that will remove both versions, including the 6 which you installed through deb files.
Then add the PPA of libreoffice and install:
```

sudo add-apt-repository ppa:libreoffice/ppa
sudo apt update
sudo apt install libreoffice

```

---

