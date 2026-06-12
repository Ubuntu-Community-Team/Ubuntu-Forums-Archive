---
title: "Installing vlc on Ubuntu"
date: 2012-01-27
forum: New to Ubuntu
---

### Post by swavijay on 2012-01-27
Hi All,

I'm a new bie to Linux so please bear with me if this is a silly question. This is my first post in this forum.

I have installed Ubuntu 10.04 on my desktop today which is AMD Athlon 64 bit processor.

I'm planning to install vlc on my desktop and I searched the rpm file from the site [http://rpmfind.net/](http://rpmfind.net/)

I did find rpm for vlc but most of them are for Fedora. I could not find any for Ubuntu,.

Just curious to know if i can install the fedora rpm in Ubuntu

Please advice.

I was referring to this link.. 

[http://rpmfind.net//linux/RPM/rpmfusion/free/fedora/devel/x86_64/vlc-1.2.0-0.7_pre4.fc17.x86_64.html](http://rpmfind.net//linux/RPM/rpmfusion/free/fedora/devel/x86_64/vlc-1.2.0-0.7_pre4.fc17.x86_64.html)

-Vijay

---

### Post by Grenage on 2012-01-27
Isn't remote desktop (by VNC) installed by default, still?

---

### Post by swavijay on 2012-01-27
> **Grenage said:**
> Isn't remote desktop (by VNC) installed by default, still?
[http://www.videolan.org/](http://www.videolan.org/)

---

### Post by Grenage on 2012-01-27
> **swavijay said:**
> [http://www.videolan.org/](http://www.videolan.org/)

I'm sorry, I miss-read your post:

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

---

### Post by haqking on 2012-01-27
> **Grenage said:**
> Isn't remote desktop (by VNC) installed by default, still?

VNC is not the VLC media player ;-)

Easy mistake to make though

> **swavijay said:**
> [http://www.videolan.org/](http://www.videolan.org/)


RPM is for red hat systems.

In ubuntu we use .deb though you can use .rpm with alien.

However VLC should be in the software centre, you can add a PPA or download a .deb

here are instruction for ubuntu on their website

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

Edit: Ninja'd by Grenage above ;-)

Peace

---

### Post by Double.J on 2012-01-27
> **swavijay said:**
> Hi All,

I'm a new bie to Linux so please bear with me if this is a silly question. This is my first post in this forum.

I have installed Ubuntu 10.04 on my desktop today which is AMD Athlon 64 bit processor.

I'm planning to install vlc on my desktop and I searched the rpm file from the site [http://rpmfind.net/](http://rpmfind.net/)

I did find rpm for vlc but most of them are for Fedora. I could not find any for Ubuntu,.

Just curious to know if i can install the fedora rpm in Ubuntu

Please advice.

I was referring to this link.. 

[http://rpmfind.net//linux/RPM/rpmfusion/free/fedora/devel/x86_64/vlc-1.2.0-0.7_pre4.fc17.x86_64.html](http://rpmfind.net//linux/RPM/rpmfusion/free/fedora/devel/x86_64/vlc-1.2.0-0.7_pre4.fc17.x86_64.html)

-Vijay

Hi there, welcome to the forums!

Just a couple of things - firstly that VLC is already in the repos and has been version .13 for ages. open a terminal with CTRL+ALT+T and paste in
```
sudo apt-get install vlc
```

If there happens to be a reason for getting the .rpm version, you would first need to install a program called alien to convert the .rpm to a .deb binary that ubuntu can use :)

```
sudo apt-get install alien dpkg-dev debhelper build-essential
``` (Just installing alien worked for me, but [this how to]("http://www.howtogeek.com/howto/ubuntu/install-an-rpm-package-on-ubuntu-linux/") recommends this.)

To convert from .RPM to .deb with alien:
```
 sudo alien vlc.rpm
``` (use the actual package name as it appears in the directory)

To install .deb packages
```
 sudo dpkg -i vlc.deb
``` (again exact package name of VLC is required :) )

Alternatively, you may want to try the latest version of VLC from the upcoming version 2? These are not yet listed as stable but seem to be working pretty much without error. to do this you'd need to add a new repository with
```
 sudo add-apt-repository ppa:videolan/stable-daily && sudo apt-get update
```

Then just install it as in the first option
```
sudo apt-get install vlc
``` 

if apt-get install generates some missing packages, just add those and try again ;)

Hope it helps!

:)

---

### Post by swavijay on 2012-01-27
Thanks a lot for all your help..

I was able to get the vlc installed on my PC with the command 
sudo apt-get install vlc


However just curious to know..

if I find a rpm package for fedora can I convert that rpm to deb using alien and then install that on Ubuntu?

-Vijay

---

### Post by haqking on 2012-01-27
> **swavijay said:**
> Thanks a lot for all your help..

I was able to get the vlc installed on my PC with the command 
sudo apt-get install vlc


However just curious to know..

if I find a rpm package for fedora can I convert that rpm to deb using alien and then install that on Ubuntu?

-Vijay

yes but better to find a .deb or other native way in the first place, before anything search in the software centre/repos first

---

### Post by swavijay on 2012-01-27
> **haqking said:**
> yes but better to find a .deb or other native way in the first place, before anything search in the software centre/repos first
One more question.sorry again if it sounded silly...

I have installed Ubuntu in my PC. I did not know that it was a flavor of Red hat / debian systems? is there a way fo find that out through some command..?

-Vijay

---

### Post by swavijay on 2012-01-27
> **gnu/mirow said:**
> Hi there, welcome to the forums!

Just a couple of things - firstly that VLC is already in the repos and has been version .13 for ages. open a terminal with CTRL+ALT+T and paste in
```
sudo apt-get install vlc
```

If there happens to be a reason for getting the .rpm version, you would first need to install a program called alien to convert the .rpm to a .deb binary that ubuntu can use :)

```
sudo apt-get install alien dpkg-dev debhelper build-essential
``` (Just installing alien worked for me, but [this how to]("http://www.howtogeek.com/howto/ubuntu/install-an-rpm-package-on-ubuntu-linux/") recommends this.)

To convert from .RPM to .deb with alien:
```
 sudo alien vlc.rpm
``` (use the actual package name as it appears in the directory)

To install .deb packages
```
 sudo dpkg -i vlc.deb
``` (again exact package name of VLC is required :) )

Alternatively, you may want to try the latest version of VLC from the upcoming version 2? These are not yet listed as stable but seem to be working pretty much without error. to do this you'd need to add a new repository with
```
 sudo add-apt-repository ppa:videolan/stable-daily && sudo apt-get update
```

Then just install it as in the first option
```
sudo apt-get install vlc
``` 

if apt-get install generates some missing packages, just add those and try again ;)

Hope it helps!

:)
Few Questions....

1. How do I find if an application already exists in the repos?
2. I understand that you are adding the latest version of VLC to the repository and then installing vlc from repository..
correct me if I'm techincally wrong.

sudo add-apt-repository ppa:videolan/stable-daily && sudo apt-get update

Are there any pointers such as link which explains the process of adding an app to the repository? that would help me on a longer run

Thanks
-Vijay

---

### Post by Grenage on 2012-01-27
> **swavijay said:**
> Few Questions....

1. How do I find if an application already exists in the repos?
2. I understand that you are adding the latest version of VLC to the repository and then installing vlc from repository..
correct me if I'm techincally wrong.

sudo add-apt-repository ppa:videolan/stable-daily && sudo apt-get update

Are there any pointers such as link which explains the process of adding an app to the repository? that would help me on a longer run

Thanks
-Vijay

```
apt-cache search *whatyouwant*
```

Indeed you are adding a repository, but you generally want to be careful about what you add; you need to trust it.

---

### Post by haqking on 2012-01-27
> **swavijay said:**
> One more question.sorry again if it sounded silly...

I have installed Ubuntu in my PC. I did not know that it was a flavor of Red hat / debian systems? is there a way fo find that out through some command..?

-Vijay

Ubuntu is not in any way related to redhat other than it is Linux.  

It is a Debian spin off.

Find out what through terminal ?

---

### Post by dave0109 on 2012-01-27
@haqking - I think he meant "find out if a particular version of Linux is based on RedHat or Debian (or something else)".

@swavijay - As well as the command line given for searching repos, if you want to use a GUI, then there's the Ubuntu Software Centre, or Synaptic Package Manager.  Both of which have a text field for entering a search string, which will filter the results shown when you stop typing.

---

### Post by haqking on 2012-01-27
> **dave0109 said:**
> @haqking - I think he meant "find out if a particular version of Linux is based on RedHat or Debian (or something else)".


not sure about from terminal, i doubt it not universally anyways.

[http://www.debian.org/misc/children-distros](http://www.debian.org/misc/children-distros)

this shows the debian based distros.

But if it requires a .rpm then it is redhat based or spin off such as fedora/centOS etc

If it requires or works with .deb then it is debian based usually.

As a guideline, there are some others also

---

### Post by Double.J on 2012-01-27
> **swavijay said:**
> Few Questions....

1. How do I find if an application already exists in the repos?
2. I understand that you are adding the latest version of VLC to the repository and then installing vlc from repository..
correct me if I'm techincally wrong.

sudo add-apt-repository ppa:videolan/stable-daily && sudo apt-get update

Are there any pointers such as link which explains the process of adding an app to the repository? that would help me on a longer run

Thanks
-Vijay
Hi there vijay, sorry really world in the way!

Just to clear it up a bit- that command doesn't add anything to the repos, it adds a repository. As I'm sure you can guess the repository is an online collection of packages designed for your system. Only the owner of a repository, or someone given access by them can add to the repo - this helps increase security. 

Grenage was quite correct you should only add a repo you are sure of - in this instance I gave you the official repository of the company behind VLC and checked that they have a lucid repo. 

Very easy way to have a look at what repo's you've got and turn them on or off is in the synaptic package manager. The list of repo's is stored in /etc/apt/sources.list - but be very careful not to view this with root privileges in case you messed it up - as with any configuration file in linux - always make a copy before you edit ;)


As for the which linux is which question, have a look at [this image on Wikipedia]("http://upload.wikimedia.org/wikipedia/commons/8/8c/Gldt.svg") The thing to remember with linux is that it's all distros - every "OS" has to share it's code back into the collective, to at it's most basic, every linux system is  the same in that it has a linux kernel compiled from the same set of source, with the same GNU userland. What differs is what options the distributions build into their kernels, what package management system they use, and what software they bundle with them; any program's source package (one ending in .tar.gz or .tar.bz2) can be built and run on any Linux system :)

---

