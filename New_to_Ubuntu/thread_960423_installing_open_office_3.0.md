---
title: "installing open office 3.0"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by dreadh3ad on 2008-10-27
How do you install open office 3.0 from source?  I am running ubuntu 7.10.  The packages are .rpms and not .debs...

---

### Post by GumboLinux on 2008-10-27
[http://www.associatedcontent.com/article/1077716/how_to_run_an_rpm_file_in_ubuntu_linux.html]("http://www.associatedcontent.com/article/1077716/how_to_run_an_rpm_file_in_ubuntu_linux.html")

there ya go mate have fun

---

### Post by dreadh3ad on 2008-10-27
There are at least 20 different packages that I need to convert.  Is there a way to recursively apply this process to each package in a subfolder?

---

### Post by GumboLinux on 2008-10-27
I believe so. What I would do is go to terminal [PHP]cd (wherever-installed-by-default-desktop)[/PHP] [PHP]mkdir (folder-name-that-you-want-them-to-be-put-in)[/PHP]
now move all of them in there and convert the entire directory

---

### Post by dreadh3ad on 2008-10-27
Thanks.  I guess my final question is more about the structure of the ubuntu file system.  How exactly do I find out where the program has been installed?

---

### Post by gjoellee on 2008-10-27
there is a nice tutorial here: [http://kshoster.net/node/56](http://kshoster.net/node/56)

---

### Post by waspbr on 2008-10-27
just go to system>Administration>software sources

go to the third party tab

click on add

then add the following line

```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
```

this applies only to hardy, if you are on intrepid substitute the word "hardy" by "intrepid" in the code above

update and upgrade your system

OOo should be now listed as one of the upgrades

---

### Post by dreadh3ad on 2008-10-27
Ive already installed it from source, i just need to figure out where exactly the executable is.

---

### Post by swisscow on 2008-10-27
I think in /opt

---

### Post by dfreer on 2008-10-27
> **dreadh3ad said:**
> How do you install open office 3.0 from source?  I am running ubuntu 7.10.  The packages are .rpms and not .debs...

From source is not .rpms/.debs, source would involve compiling the code. And they OFFER .debs, why would anyone recommend converting .rpms when you could just download the .debs? The above post recommending adding a repository is a much better solution than manually downloading .rpms OR .debs, but if it's important to install it manually:

[http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US)

---

### Post by dreadh3ad on 2008-10-27
Well ive already installed the rpms what can i do from here?  OO is not in /opt

---

### Post by gjoellee on 2008-10-27
A lot of people a mistake when installing OOo 3. I have therefore made this tutorial you find here: [http://kshoster.net/node/56](http://kshoster.net/node/56) where it explains how to inststall OOo 3 both from source and repo's

---

### Post by CoreyB. on 2008-10-27
> **gjoellee said:**
> A lot of people a mistake when installing OOo 3. I have therefore made this tutorial you find here: [http://kshoster.net/node/56](http://kshoster.net/node/56) where it explains how to inststall OOo 3 both from source and repo's

Yeah, this link says the same thing as gjollee, but only for Intrepid.  [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml")

---

### Post by dfreer on 2008-10-27
> **dreadh3ad said:**
> Well ive already installed the rpms what can i do from here?  OO is not in /opt

You can try:
```
whereis openoffice
sudo updatedb
locate openoffice
```

---

### Post by jeremy on 2008-11-04
> **waspbr said:**
> just go to system>Administration>software sources

go to the third party tab

click on add

then add the following line

```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
```

this applies only to hardy, if you are on intrepid substitute the word "hardy" by "intrepid" in the code above

update and upgrade your system

OOo should be now listed as one of the upgrades

I have added the repositories as above, sudo apt-get update then sudo apt-get upgrade , but - 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Has anyone else had this problem? Solutions?

---

### Post by TCWriter on 2008-11-06
Yow. After reading this, I think I'll wait for the package version, though I have to ask: Typically speaking, how long before OpenOffice 3.0 is available via Synaptics? 

I thought I'd get it with 8.10 (I've upgraded), but no dice.

---

### Post by dfreer on 2008-11-06
If it's not in 8.10, it'll probably be in 9.04. So about 6 months.

---

### Post by stevebond001 on 2008-11-06
For what it's worth, here's the way I did it.
[http://ubuntuforums.org/showthread.php?t=947388](http://ubuntuforums.org/showthread.php?t=947388) (**Post #9**)


This allowed me to remove OpenOffice 2.4 (which came bundled with Hardy) and install OpenOffice 3.0 (downloaded from the OpenOffice Website).

The instructions are quite simple (they must be, 'cos I followed them...)	:rolleyes:

Hope this helps

Good luck

---

### Post by eolson on 2008-11-06
For what it's worth, 30 years of messing around with this stuff has taught me that any software that ends in .0  should be avoided.  Wait for the .1 version.   Doesn't keep me from trying every .0 that comes out,   but it should.

---

