---
title: "Problem with repository and update"
date: 2013-10-27
forum: New to Ubuntu
---

### Post by acodea on 2013-10-27
I have installed a get-deb repository and because I got errors removed it, and now I gen an error, and I believe am not able to update/some programs it wont find in repositories. I am running Ubuntu Precise.

The culprit is located at the getdeb.org repository. I installed it using the instructions.


     deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) precise-getdeb apps
Add the repository GPG key, open a terminal window and type:
     wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -

I saw there is no key in the second line. I began to get errors concerning the missing key. Afterwards, 
I uninstalled and purged the repository and did all normal maintenance, but I still get the error when I run update. 


    N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
    N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

I would like to install this repository [http://www.getdeb.net/updates/Ubuntu/12.04/](http://www.getdeb.net/updates/Ubuntu/12.04/)


To help with this analysis:

$ ls /etc/apt/sources.list.d/



freyja-dev-unity-tweak-tool-daily-precise.list
freyja-dev-unity-tweak-tool-daily-precise.list.save
getdeb.list.bck
glasen-intel-driver-precise.list
glasen-intel-driver-precise.list.save
nae-team-ppa-precise.list
nae-team-ppa-precise.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_allvideodownloader_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_allvideodownloader_ubuntu.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_brightness-controller_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_implosion_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_implosion_ubuntu.list.save
wfg-0ad-precise.list
wfg-0ad-precise.list.save

I am wondering when the last time I saw an automatic update, received a positive apt-get update reply...

---

### Post by acodea on 2013-10-27
I ran:
    sudo dpkg --configure -a && sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

---

### Post by fantab on 2013-10-27
> **acodea said:**
> 


    N: Ignoring file '**getdeb.list.bck**' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
    N: Ignoring file '**getdeb.list.bck**' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

I would like to install this repository [http://www.getdeb.net/updates/Ubuntu/12.04/](http://www.getdeb.net/updates/Ubuntu/12.04/)

$ ls /etc/apt/sources.list.d/

freyja-dev-unity-tweak-tool-daily-precise.list
freyja-dev-unity-tweak-tool-daily-precise.list.save
**getdeb.list.bck**
glasen-intel-driver-precise.list
glasen-intel-driver-precise.list.save
nae-team-ppa-precise.list
nae-team-ppa-precise.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_allvideodownloader_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_allvideodownloader_ubuntu.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_brightness-controller_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_implosion_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_implosion_ubuntu.list.save
wfg-0ad-precise.list
wfg-0ad-precise.list.save

Delete "**getdeb.list.bck**" from the file and save it.
and run:
```
sudo apt-get update
```

If no errors are reported then re-install the repository. Remember to add the GPG key immediately after adding the repository... and run 'sudo apt-get update'.

---

### Post by acodea on 2013-10-27
Hoe do I edit the file? Remember I am a newbie and that gedit and all the language is in fact, new to me.

---

### Post by fantab on 2013-10-27
My bad. 

```
gksu nautilus
```
This will open the file-browser as root.
Navigate to Computer/filesystem/etc/apt/sources.list.d 
In the folder you will find the file "**getdeb.list.bck**" delete it. 
Close the file-browser.

Or

```
sudo rm /etc/apt/sources.list.d/getdeb.list.bck
```


then run:
```
sudo apt-get update
```

---

### Post by acodea on 2013-10-27
lol thanks. Nautilus allows me to edit the files. How is that like gksudo gedit?

any  info on the missing apt-key?

wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -?

---

### Post by fantab on 2013-10-27
I am not sure. The website list two methods try both again. I am not on Ubuntu machine, so can't check.

---

### Post by acodea on 2013-10-27
> **fantab said:**
> I am not sure. The website list two methods try both again. I am not on Ubuntu machine, so can't check.


Both methods are broken; but i am also have high paranoia from the number of repositories (which are) causing so many a bad experience in Ubuntu(from the number of repeats of like problems to mine.) and I wont install it again unless the key is given to me. 

But thanks a freaking lot.

BL

---

### Post by acodea on 2013-10-28
> **fantab said:**
> I am not sure. The website list two methods try both again. I am not on Ubuntu machine, so can't check.

I sent along an error report to Christopher Korn@ getdeb.info. He says he knows about the problem, and he has been good enough to send a repository mirror, so downloads are available. This is a big mirror and the problem is amplified by it's size. I am passing this along, perhaps it will explain and prevent some of the Ubuntu Forums thread on this subject.

**Christoph Korn (c_korn@gmx.de) sez:**

Hello,


the provider currently has problems with package drops.


Please download the packages from one of the mirrors:
e.g.:
[http://mirror.informatik.uni-mannheim.de/pub/mirrors/getdeb/ubuntu/pool/apps/](http://mirror.informatik.uni-mannheim.de/pub/mirrors/getdeb/ubuntu/pool/apps/)


[http://mirror.informatik.uni-mannheim.de/pub/mirrors/getdeb/ubuntu/dists/precise-getdeb/](http://mirror.informatik.uni-mannheim.de/pub/mirrors/getdeb/ubuntu/dists/precise-getdeb/)

---

### Post by acodea on 2013-10-28
> **fantab said:**
> I am not sure. The website list two methods try both again. I am not on Ubuntu machine, so can't check.

I sent along an error report to Christopher Korn@ getdeb.info. He says he knows about the problem, and he has been good enough to send a repository mirror, so downloads are available. This is a big mirror and the problem is amplified by it's size times the number of sites promoting getdeb. I am passing this along, perhaps it will explain and prevent some of the Ubuntu Forums thread on this subject.

**Christoph Korn (c_korn@gmx.de) sez:**

Hello,


the provider currently has problems with package drops.


Please download the packages from one of the mirrors:
e.g.:
[http://mirror.informatik.uni-mannheim.de/pub/mirrors/getdeb/ubuntu/pool/apps/](http://mirror.informatik.uni-mannheim.de/pub/mirrors/getdeb/ubuntu/pool/apps/)


[http://mirror.informatik.uni-mannheim.de/pub/mirrors/getdeb/ubuntu/dists/precise-getdeb/](http://mirror.informatik.uni-mannheim.de/pub/mirrors/getdeb/ubuntu/dists/precise-getdeb/)

---

### Post by acodea on 2013-10-28
> **fantab said:**
> I am not sure. The website list two methods try both again. I am not on Ubuntu machine, so can't check.

I sent along an error report to Christopher Korn@ getdeb.info. He says he knows about the problem, and he has been good enough to send a repository mirror, so downloads are available. This is a big mirror and the problem is amplified by it's size times the number of sites promoting getdeb. I am passing this along, perhaps it will explain and prevent some of the Ubuntu Forums thread on this subject.

**Christoph Korn (email address removed) sez:**

Hello,


the provider currently has problems with package drops.


Please download the packages from one of the mirrors:
e.g.:
[http://mirror.informatik.uni-mannheim.de/pub/mirrors/getdeb/ubuntu/pool/apps/](http://mirror.informatik.uni-mannheim.de/pub/mirrors/getdeb/ubuntu/pool/apps/)


[http://mirror.informatik.uni-mannheim.de/pub/mirrors/getdeb/ubuntu/dists/precise-getdeb/](http://mirror.informatik.uni-mannheim.de/pub/mirrors/getdeb/ubuntu/dists/precise-getdeb/)

---

