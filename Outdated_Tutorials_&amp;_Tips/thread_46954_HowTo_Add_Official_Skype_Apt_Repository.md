---
title: "HowTo: Add Official Skype Apt Repository"
date: 2005-07-06
forum: Outdated Tutorials &amp; Tips
---

### Post by lotusleaf on 2005-07-06
According to this thread on the Skype forums:

["yum/apt repositories - please test"](http://forum.skype.com/viewtopic.php?t=29679) posted by 'terminus', a member of the 'Skype staff'

They now have an official Skype apt source for Skype for Linux. From the above linked post, here's the details on the apt repository:

> Using Skype's apt repository

Simply add the following line to your sources.list file (usually /etc/apt/sources.list):

```
deb http://download.skype.com/linux/repos/debian/ stable non-free
``` Now you can use apt-get update to sync to latest repository and then apt-get install skype to install Skype on your machines.

Edit: I just added it to my sources.list and it works fine.

---

### Post by manicka on 2005-07-06
Thanks for this lotusleaf. Works well :)

P.S. Nice to see you around this forum. I wondered where you'd disappeared to :D

---

### Post by Caboto on 2005-07-07
Worked perfectly for me. Big thanks! I always forgot to update my skype... ;)

---

### Post by Hex on 2005-07-07
Works for me too, updating as we speak :) Thanks!

p.s. Nice website :)

---

### Post by kb00heda on 2005-07-07
I'll second that --- nice tip for us who always forget to manually check for updates! Also, as for now, I'm only using Skype for telephony, via SkypeOut and SkypeIn. So far so good ... :)

---

### Post by mbirkis on 2005-07-09
Hi...

Just thought i should mention that this does not work on 64bit installs of ubuntu.  :-x

---

### Post by bungopolis on 2005-07-16
Using the official Skype repository is now the method included in the Ubuntu Wiki guide at [https://wiki.ubuntu.com/SkypeHowto](https://wiki.ubuntu.com/SkypeHowto)

---

### Post by xodeus on 2005-08-04
[QUOTE=lotusleaf]According to this thread on the Skype forums:

["yum/apt repositories - please test"](http://forum.skype.com/viewtopic.php?t=29679) posted by 'terminus', a member of the 'Skype staff'

They now have an official Skype apt source for Skype for Linux. From the above linked post, here's the details on the apt repository:



Edit: I just added it to my sources.list and it works fine.[/QUOTE]
 This really works.
Great.

---

### Post by agm642 on 2005-10-02
I have a problem with this. It tells me:
```
The following packages have unmet dependencies:
skype: Depends: libqt3c102-mt (>= 3:3.3.3.2) but 3:3.3.3-7ubuntu3 is to be installed
E: Broken packages
```
Can somebody help me?

Edit: I'm REALLY sorry, I forgot I mustn't post questions here... Sorry...:oops: ](*,)

---

### Post by foxy123 on 2005-10-02
[QUOTE=agm642]I have a problem with this. It tells me:
```
The following packages have unmet dependencies:
skype: Depends: libqt3c102-mt (>= 3:3.3.3.2) but 3:3.3.3-7ubuntu3 is to be installed
E: Broken packages
```
Can somebody help me?
Edit: I'm REALLY sorry, I forgot I mustn't post questions here... Sorry...:oops: ](*,)[/QUOTE]
it's a skype bug. For some reasons their Debian version on which they built the package has 3:3.3.3.2, not 3:3.3.3-x as Ubuntu and some other distros (including Debian) have. Search a forum and you will find the solution. You need actually install a previous version which is compiled fine or use another method.

---

### Post by bugi on 2005-10-02
[QUOTE=foxy123]it's a skype bug. For some reasons their Debian version on which they built the package has 3:3.3.3.2, not 3:3.3.3-x as Ubuntu and some other distros (including Debian) have. Search a forum and you will find the solution. You need actually install a previous version which is compiled fine or use another method.[/QUOTE]

Static binary version of Skype 1.2.0.17 works really good on Hoary.

---

### Post by majikstreet on 2005-10-02
**TESTED IN BREEZY** **MAY NOT WORK IN HOARY**


I have the solution to the depenancy issue.

First step: download the libqt deb from here: [http://http.us.debian.org/debian/pool/main/q/qt-x11-free/libqt3c102-mt_3.3.4-3_i386.deb](http://http.us.debian.org/debian/pool/main/q/qt-x11-free/libqt3c102-mt_3.3.4-3_i386.deb)

Second step: sudo apt-get remove libqt3-mt

Third Step: sudo dpkg -i libqt3c102-mt_3.3.4-3_i386.deb

Fourth Step: sudo apt-get install skype

Skype works fine!

Note: If you have "gnomeified skype" you have to re-do it :(

---

### Post by peirthies on 2005-10-02
** Tested in hoary **
Download the packages first
libfontconfig1 is here: [http://http.us.debian.org/debian/pool/main/f/fontconfig/libfontconfig1_2.3.1-2_i386.deb]("http://http.us.debian.org/debian/pool/main/f/fontconfig/libfontconfig1_2.3.1-2_i386.deb")

libfontconfig1-dev is here:
[http://http.us.debian.org/debian/pool/main/f/fontconfig/libfontconfig1-dev_2.3.1-2_i386.deb]("http://http.us.debian.org/debian/pool/main/f/fontconfig/libfontconfig1-dev_2.3.1-2_i386.deb")

libqt is here:
[http://http.us.debian.org/debian/pool/main/q/qt-x11-free/libqt3c102-mt_3.3.4-3_i386.deb]("http://http.us.debian.org/debian/pool/main/q/qt-x11-free/libqt3c102-mt_3.3.4-3_i386.deb")

remove QT:
sudo apt-get remove libqt3-mt

Install the packages now
sudo dpkg -i libfontconfig1_2.3.1-2_i386.deb
sudo dpkg -i libfontconfig1-dev_2.3.1-2_i386.deb
sudo dpkg -i libqt3c102-mt_3.3.4-3_i386.deb

Finally install skype:
sudo apt-get install skype

---

### Post by majikstreet on 2005-10-03
[QUOTE=peirthies]** Tested in hoary **
Download the packages first
libfontconfig1 is here: [http://http.us.debian.org/debian/pool/main/f/fontconfig/libfontconfig1_2.3.1-2_i386.deb]("http://http.us.debian.org/debian/pool/main/f/fontconfig/libfontconfig1_2.3.1-2_i386.deb")

libfontconfig1-dev is here:
[http://http.us.debian.org/debian/pool/main/f/fontconfig/libfontconfig1-dev_2.3.1-2_i386.deb]("http://http.us.debian.org/debian/pool/main/f/fontconfig/libfontconfig1-dev_2.3.1-2_i386.deb")

libqt is here:
[http://http.us.debian.org/debian/pool/main/q/qt-x11-free/libqt3c102-mt_3.3.4-3_i386.deb]("http://http.us.debian.org/debian/pool/main/q/qt-x11-free/libqt3c102-mt_3.3.4-3_i386.deb")

remove QT:
sudo apt-get remove libqt3-mt

Install the packages now
sudo dpkg -i libfontconfig1_2.3.1-2_i386.deb
sudo dpkg -i libfontconfig1-dev_2.3.1-2_i386.deb
sudo dpkg -i libqt3c102-mt_3.3.4-3_i386.deb

Finally install skype:
sudo apt-get install skype[/QUOTE]
I am verifying that Skype from the APT offical repo's on breezy with gnomeified settings works!

I had to reboot before it would work, but it did :)

---

### Post by Foaming Draught on 2005-10-04
Thanks majikstreet, you're a hero, I was tearing my hair out trying to find a way to update Skype.

---

### Post by majikstreet on 2005-10-04
you are welcome :)

Unfortunatly, I f***ed up my install so I still have to get the gnome'ish skype to be on again lol

---

### Post by Pander on 2005-12-01
What whould be a good way of persuading Skype to build .deb package for Ubuntu Hoary and Breeze?

---

### Post by flamel2000 on 2006-08-15
Hello!

I'm a beginner in linux field.
I don't know how to install skype in a proper manner.I tried adding the repository to my manager(synaptic).But it said that that repository is no longer in use.Please help me installing skype in a step by step guide.

Thankyou.

---

### Post by dietkinnie on 2006-08-30
Hi,

Thanks for this post, it worked fine for me :)

//Robert

---

### Post by Argard on 2008-12-29
Thanks for the tip :)

Previous I did instalations getting the .deb from skype website, now , just apt-get :)

---

### Post by fanxiong on 2009-12-20
I have downloaded and installed the skype of version 2.1.0.47. but I found that the quality of audio input was very bad, it's always noisely.
Any body know how can i fix that ? Thanks very much!

---

### Post by Linuxforall on 2009-12-20
Gives a not found 404 error in Karmic.

---

### Post by Earendil1982 on 2010-01-25
> **Linuxforall said:**
> Gives a not found 404 error in Karmic.

Works fine in my Karmic installation. Just upgraded to:
% LC_ALL=C apt-cache policy skype
skype:
  Installed: 2.1.0.81-1
  Candidate: 2.1.0.81-1
  Version table:
 *** 2.1.0.81-1 0
        500 [http://download.skype.com](http://download.skype.com) stable/non-free Packages
        100 /var/lib/dpkg/status

---

### Post by fofftorrent on 2010-02-14
does

deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

still work? i get 

Err [http://download.skype.com](http://download.skype.com) stable/non-free Packages
  404 Not Found [IP: 212.72.53.130 80]

---

### Post by Angelos72 on 2010-02-14
> **fofftorrent said:**
> does

deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

still work? i get 

Err [http://download.skype.com](http://download.skype.com) stable/non-free Packages
  404 Not Found [IP: 212.72.53.130 80]

No, it does not seem to work for me either. But, what do we need it anyway. Skype checks for updates by itself. It does not depend on the repository for updates.

---

### Post by bgrolleman on 2010-02-22
One of the main reasons I like Ubuntu is because I don't get reminded to update all the time. So I'll take apt any day.

---

### Post by amaz1ng on 2010-12-15
Anyone have a quick terminal command for how to add the repositories in one go with sudo add-apt-repository?

Actually, it looks like Skype is already in the Partner repositories: [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

How can I use add-apt to add them? I'm doing this and it's not working:

```


sudo add-apt-repository ppa:tualatrix/ppa
sudo add-apt-repository ppa:chromium-daily
sudo add-apt-repository "deb http://archive.canonical.com/ natty partner"
sudo apt-get update
sudo apt-get install gimp tweak skype gnome-do wine nautilus-open-terminal chromium-browser ubuntu-restricted-extras


```

pops out:
```
Ign http://ppa.launchpad.net maverick/main i386 Packages
Err http://ppa.launchpad.net maverick/main Sources
  404  Not Found
Err http://ppa.launchpad.net maverick/main i386 Packages
  404  Not Found
Fetched 6,142B in 0s (7,095B/s)
W: Failed to fetch http://ppa.launchpad.net/skype/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/skype/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```
and also:
```
Package skype is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'skype' has no installation candidate

```

---

