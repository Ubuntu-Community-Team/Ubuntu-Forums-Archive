---
title: "LibreOffice on Ubuntu 10.04"
date: 2011-12-22
forum: New to Ubuntu
---

### Post by flurospar on 2011-12-22
I am currently using Ubuntu 10.04.2. In the default repositories, LibreOffice isn't there, so how do I install it?

Thanks in advance.

---

### Post by P05TMAN on 2011-12-22
> **flurospar said:**
> I am currently using Ubuntu 10.04.2. In the default repositories, LibreOffice isn't there, so how do I install it?

Thanks in advance.

Here's the site for the ppa along with instructions

[http://www.ubuntugeek.com/install-libreoffice-in-ubuntu-11-0410-1010-04-using-ppa.html](http://www.ubuntugeek.com/install-libreoffice-in-ubuntu-11-0410-1010-04-using-ppa.html)

---

### Post by flurospar on 2011-12-22
I get version 3.3.2 after adding the PPA. Is that the latest? I dont think so

---

### Post by P05TMAN on 2011-12-22
> **flurospar said:**
> I get version 3.3.2 after adding the PPA. Is that the latest? I dont think so

Current release is 3.4; you're right. I think that you can download and install from the site though

[http://www.libreoffice.org/](http://www.libreoffice.org/)

---

### Post by mastablasta on 2011-12-22
no you can't. the deb file found on libre office will not install. i also tried it. at the moment i have 3.3.2
 
so much for Long Term SUPPORT...

---

### Post by crazy bird on 2011-12-22
> **mastablasta said:**
> so much for Long Term SUPPORT...
 
Long Term Support is only applicable for Ubuntu 10.04. Not for external programs/tools. Long Term Support only means that the LTS version will be supported for 3 years (desktop) and 5 years (server) by Canonical. It has nothing to do with LibreOffice or other programs.
 
If you can't install LibreOffice on your system, the fault should be found on your system. Do you get any error messages during/after your attempt to install LibreOffice? If so, please post them here.

---

### Post by mastablasta on 2011-12-22
> **crazy bird said:**
> Long Term Support is only applicable for Ubuntu 10.04. Not for external programs/tools. Long Term Support only means that the LTS version will be supported for 3 years (desktop) and 5 years (server) by Canonical. It has nothing to do with LibreOffice or other programs.

 
I know but this also means that bugfixes (Libre office has plenty bug fixes of OOo) don't get in the software which is part fo distribution. again no point instaying with LTS if same bugs will stay for the duration of the term.
> 
If you can't install LibreOffice on your system, the fault should be found on your system. Do you get any error messages during/after your attempt to install LibreOffice? If so, please post them here.
 
i used .deb file. dependencies were not met. I plan to do full post (new topic) when i find the time. for the moment i used PPA which again is only 3.3.2 available for 10.10 version. 
 
to the OP if you have a bit more time than me during this for me hectic month please post the error output. if you used .deb files from LO site then you likely have same issue as me.
:D

---

### Post by crazy bird on 2011-12-23
And when you use [this PPA]("https://launchpad.net/~libreoffice/+archive/ppa"), don't you get the latest updates for LibreOffice?

---

### Post by mastablasta on 2011-12-23
I will check again at home but i think it will give this libreoffice 1:3.3.2-1ubuntu2~maverick1 
 
1:3.3.2-1ubuntu2~maverick1 
 
for 10.10. and i think this PPA is what i use. As i understand only newer versions of Ubuntu get newer package. 
 
Also 3.4.4 is latest version, however i have issues with it when i conver documents from MS Word 2003. I actually need previous version stable 3.3.4
 
installing whatever version to a 2001 OS (winXP) is so easy :) , why can't it be so easy for 2010 OS?
 
ah, in April/May 2012 the Linux box get's an upgrade to new version...

---

### Post by crazy bird on 2011-12-23
That link i gave you, provides repo's from Ubuntu 10.04 up to 11.04. So selecting the correct version and you get the correct PPA.

---

### Post by ricotz on 2011-12-26
> **flurospar said:**
> I am currently using Ubuntu 10.04.2. In the default repositories, LibreOffice isn't there, so how do I install it?

Thanks in advance.

 I desperately needed an updated version of LibreOffice on Lucid for myself and figured it is probably of use in a PPA too. I have uploaded 3.4.4 for Lucid to [https://launchpad.net/~ricotz/+archive/ppa](https://launchpad.net/~ricotz/+archive/ppa)

---

### Post by mastablasta on 2012-01-05
Thanks for the PPA ricotz.
 
The previous PPA really does give a bit older version of LO.
 
However, i found out now how to inmstall it form the .deb files available on their website. I need 3.3.4 version as it seems to work with documents i need. anyway you download the tar.gz file, extract it and then there is a folder with one readme file in it. in that readme there are instructions and all you need to do is copy 2 or 3 commands into terminal. and it get's installed. same instructions include also how to install the language packs and help files (each need 1 command to be copied to terminal).
 
so eventhoguh this is not the preffered way to install programmes in linux i would suggest using it if oyu need a newer version. i installed the version i need like this on Debian 6 (#! actually). Next is Kubuntu 10.10..

---

