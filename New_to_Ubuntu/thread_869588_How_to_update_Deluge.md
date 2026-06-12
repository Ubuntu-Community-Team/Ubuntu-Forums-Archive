---
title: "How to update Deluge"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by wariskampar on 2008-07-25
When I open Deluge, update notification pop up "There is a newer version of Deluge. Would you like to be taken to Deluge website". From that site, I downloaded a newer deb package, 0.9.03-1 (right now I'm using 0.5.8.9). When I run the package, I got error message about localepurge not configured and can not remove the old version. What should I do? I thought, if I just run the newer package, it will automatically get rid the old/current one. About locale-purge, how do I configure it

---

### Post by BGFG on 2008-07-25
I read that the older version needs to be removed first. try
```

sudo apt-get purge deluge-torrent

```
then re-install the new version. I have the new version also but i have a pretty big file coming down. Will upgrade when it's done. Good luck.

---

### Post by iaculallad on 2008-07-25
> **wariskampar said:**
> When I open Deluge, update notification pop up "There is a newer version of Deluge. Would you like to be taken to Deluge website". From that site, I downloaded a newer deb package, 0.9.03-1 (right now I'm using 0.5.8.9). When I run the package, I got error message about localepurge not configured and can not remove the old version. What should I do? I thought, if I just run the newer package, it will automatically get rid the old/current one. About locale-purge, how do I configure it

Remove the installed version of deluge:

```
sudo apt-get remove deluge-torrent
```

While on the terminal, change directory to the location of the new version of deluge you downloaded (.deb)

```
cd location_of_deb_file
```

And, install the file:

```
sudo dpkg -i deluge_package_name.deb
```

---

### Post by wariskampar on 2008-07-25
aznan@aznan-laptop:~/Desktop$ sudo dpkg -i *.deb
Selecting previously deselected package deluge-torrent.
dpkg: considering removing deluge-torrent-common in favour of deluge-torrent ...
dpkg: no, cannot proceed with removal of deluge-torrent-common (--auto-deconfigure will help):
 deluge-torrent depends on deluge-torrent-common (= 0.5.8.9-0ubuntu1)
  deluge-torrent-common is to be removed.
dpkg: regarding deluge-torrent_0.9.03-1_i386.hardy.deb containing deluge-torrent:
 deluge-torrent conflicts with deluge-torrent-common
  deluge-torrent-common (version 0.5.8.9-0ubuntu1) is present and installed.
dpkg: error processing deluge-torrent_0.9.03-1_i386.hardy.deb (--install):
 conflicting packages - not installing deluge-torrent
Errors were encountered while processing:
 deluge-torrent_0.9.03-1_i386.hardy.deb

I already remove old version using apt-get remove. Why the installation still conflict

---

### Post by wolfen69 on 2008-07-25
good luck. i've tried everything humanly imaginable to "fix" deluge, but for me, i have to jump through hoops to get it to work right. the only reason i stay with it is because i rarely reboot. even then, i have a few extra clicks to get it going again. awesome torrent client.

---

### Post by madjr on 2008-07-25
> **wariskampar said:**
> aznan@aznan-laptop:~/Desktop$ sudo dpkg -i *.deb
Selecting previously deselected package deluge-torrent.
dpkg: considering removing deluge-torrent-common in favour of deluge-torrent ...
dpkg: no, cannot proceed with removal of deluge-torrent-common (--auto-deconfigure will help):
 deluge-torrent depends on deluge-torrent-common (= 0.5.8.9-0ubuntu1)
  deluge-torrent-common is to be removed.
dpkg: regarding deluge-torrent_0.9.03-1_i386.hardy.deb containing deluge-torrent:
 **deluge-torrent [COLOR="Red"]conflicts[/COLOR] with [COLOR="Red"]deluge-torrent-common[/COLOR]**
  deluge-torrent-common (version 0.5.8.9-0ubuntu1) is present and installed.
dpkg: error processing deluge-torrent_0.9.03-1_i386.hardy.deb (--install):
 conflicting packages - not installing deluge-torrent
Errors were encountered while processing:
 deluge-torrent_0.9.03-1_i386.hardy.deb

I already remove old version using apt-get remove. Why the installation still conflict

**apt-get** command is not good for removing.

you should use **aptitude** command

or better yet open **synaptic**, search for the package and "**select complete removal**"

search this and remove it: **deluge-torrent-common**

then double click your .**deb**

---

### Post by kostkon on 2008-07-25
> **wariskampar said:**
> aznan@aznan-laptop:~/Desktop$ sudo dpkg -i *.deb
Selecting previously deselected package deluge-torrent.
dpkg: considering removing deluge-torrent-common in favour of deluge-torrent ...
dpkg: no, cannot proceed with removal of deluge-torrent-common (--auto-deconfigure will help):
 deluge-torrent depends on deluge-torrent-common (= 0.5.8.9-0ubuntu1)
  deluge-torrent-common is to be removed.
dpkg: regarding deluge-torrent_0.9.03-1_i386.hardy.deb containing deluge-torrent:
 deluge-torrent conflicts with deluge-torrent-common
  deluge-torrent-common (version 0.5.8.9-0ubuntu1) is present and installed.
dpkg: error processing deluge-torrent_0.9.03-1_i386.hardy.deb (--install):
 conflicting packages - not installing deluge-torrent
Errors were encountered while processing:
 deluge-torrent_0.9.03-1_i386.hardy.deb

I already remove old version using apt-get remove. Why the installation still conflict
There is a package called deluge-torrent-common that is part of deluge. Remove this before trying to install the deb package you have.

Nevertheless, there is a way for you to get automatic updates every time there is a new version of *Deluge*. You just need to add the *PPA* (Personal Package Archive) for it that you will find [here]("https://launchpad.net/~deluge-team/+archive"). 

You just need to select the Ubuntu version you have in this page and then add the two url lines that you will be given (or only the first, the second is not so necessary) to your software sources list. You can access your sources list from *System -> Administration -> Software Sources*. In the *Third-Party Software* tab you'll need to select *Add* to add the repository url.

---

### Post by forger on 2008-07-25
That's the part I hate. Ubuntu maintainers for the deluge package have separated it into deluge-torrent and deluge-torrent-common.
If you try to update it from the website, you will face the errors above, because the package from the website is not the same as the package in the repositories.

You have to choose, either to update using the repositories (apt-get update; apt-get upgrade), or download the deb from the website ([www.deluge-torrent.org]("www.deluge-torrent.org")). I purged deluge-torrent and deluge-torrent-common packages and installed deluge-torrent from the website, since the application has been improved a lot!

---

### Post by forger on 2008-07-25
Related bugs:
[https://bugs.launchpad.net/ubuntu/+source/deluge-torrent/+bug/248809](https://bugs.launchpad.net/ubuntu/+source/deluge-torrent/+bug/248809)
[https://bugs.launchpad.net/ubuntu/+source/deluge-torrent/+bug/208621](https://bugs.launchpad.net/ubuntu/+source/deluge-torrent/+bug/208621)

---

### Post by wariskampar on 2008-07-25
OK, problem solved. Remove deluge-torrent-common manually using Synaptic and then run deb package. Repair broken package in Synaptic. Thanks guys!

Now, I'm just curious, how does Ubuntu update the other programs. Is it automatically or I need to do like the above steps..

---

### Post by andersja on 2008-07-25
All, this forum thread is related to bug report number 248809 on Launchpad. Visit [https://bugs.launchpad.net/ubuntu/+source/deluge-torrent/+bug/248809]("https://bugs.launchpad.net/ubuntu/+source/deluge-torrent/+bug/248809") and add your comments there for the developers to take into account (they rarely read the forums, unfortunately)

---

### Post by forger on 2008-07-25
the repositories, once a release is out, are not updated unless it's an important bug fix. I'm really not sure, but I think the universe applications are updated in backports (system > administration > software sources > updates > check the -backports) after a quick revision (it doesn't mean they're thoroughly tested as other updates).

Some applications get better each month, so it's better to update those manually if there's a ubuntu-specific deb package for them

---

### Post by h!v on 2008-09-10
Welcome

Frankly now it's pretty easy.
I fought with deluge cuz it ain't downloaded right parts of whole torrent - what I exactly needed.

Go to website. Download file for your system.
Via Browser or command.

```

wget -c http://download.deluge-torrent.org/ubuntu/hardy/0.9.08/deluge-torrent_0.9.08-1_i386.hardy.deb

```

Just remove all prevoius versions of deluge
```

sudo apt-get purge deluge-torrent

```

Now let's try to install it via dpkg -i
```

sudo depkg -i deluge-torrent_0.9.08-1_i386.hardy.deb

```

We will get erros. Thou have no fear!

```

sudo apt-get -f install

```

We are done. Dependecies are fixed and good libraries installed with our new torrent client.

Hope helps.

---

