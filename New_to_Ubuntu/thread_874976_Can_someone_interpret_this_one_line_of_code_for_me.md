---
title: "Can someone interpret this one line of code for me?"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by swarup on 2008-07-30
I compiled and installed the latest version of KOffice's database program (Kexi) in Ubuntu. And it works great. :) 

Now I am going to install Kexi's "MS Access Migration Driver", so I can import a database into it from MS Access in my Window's partition. 

The Kexi website ([http://kexi-project.org/wiki/wikiview/index.php%40UsingSubversion.html](http://kexi-project.org/wiki/wikiview/index.php%40UsingSubversion.html)) has a set of instructions for installing its MS Access Migration Driver. 

Here is the first line of the instructions:

```
svn co -N svn://anonsvn.kde.org/home/kde/trunk/kdenonbeta/
```

Can someone translate into English what is going to be done by this line? 

From what I understand, in the above line the code for Kexi's "MS Access Migration Driver" will be downloaded and placed in the above-designated place in one's home folder (home/kde/trunk/kdenonbeta). If this is correct, then it seems to be that this line assumes one is using KDE and therefore has has such a set of directories in one's home folder (kde/trunk). But because I am using Ubuntu, it seems this will not apply to me. So I want to clarify what the above code line is going to try to do, before trying it. Once I understand clearly what the line means, I will adapt it as needed to fit my home folder.

Thanks!

---

### Post by Steveway on 2008-07-30
Not exactly, it means that svn will download from that adress and it will create a new folder in your current directory called kdenonbeta.

---

### Post by swarup on 2008-07-30
I see, great. I guess, "svn" will then be placed in the new folder "kdenonbeta".

So just to specify a bit further so I can understand in detail--

```
svn co -N svn://anonsvn.kde.org/home/kde/trunk/kdenonbeta/
```

So here above it says that svn (subversion) will be downloaded from the site "anonsvn.kde.org", right? And a folder named "kdenonbeta" will then be created in my directory "home/kde/trunk", right? So, what if I don't have a directory named "home/kde/trunk"? Is it going to create all those new folders ie "kde", and then "trunk", and then "kdenonbeta"?

Right now, all my kexi compiling work has been done in /home/swarup/koffice. So I was thinking perhaps I should direct "kdenonbeta" to be created there instead? After all, that is where "Kexi" and "lib", etc, are located.

---

### Post by steveneddy on 2008-07-30
To use SVN repositories, you have to have subversion installed

```

sudo aptitude install subversion
```

then run that command in terminal.

Basically it says that the information or software will be installed from that web site to your machine, where it can be updated automatically from this one source repo.

---

### Post by swarup on 2008-07-30
Yes, thanks-- I've already got "subversion" installed, as about a month ago I installed the latest subversion of Kexi.

Here are the steps I did at that time to install Kexi:

```
apt-get install subversion
apt-get install build-essential kdelibs4-dev automake1.7 libreadline5-dev
apt-get install debhelper cdbs
&#65279;apt-get install automake
svn co -N svn://anonsvn.kde.org/home/kde/branches/koffice/1.6/koffice/
cd koffice
svn co svn://anonsvn.kde.org/home/kde/branches/KDE/3.5/kde-common/admin
svn up kexi
svn up lib
export DO_NOT_COMPILE="kchart kdgantt kformula koshell krita kugar kword"
make -f Makefile.cvs
./configure --enable-debug=full --prefix=`kde-config --prefix`
 perl admin/am_edit  # shouldn't be necessary - why is it needed sometimes?
cd lib && make && sudo make install
cd ../kexi && make && sudo make install

```

The above worked great.

Given that the above worked fine, does it look like the below code should work with it well to install Kexi's MS Access import tool for me in Ubuntu? Or are the lines made for someone having KDE, and I have to adjust some of the lines for Ubuntu ie given that this is a Debian install and not a KDE install?


```
 svn co -N svn://anonsvn.kde.org/home/kde/trunk/kdenonbeta/
 cd kdenonbeta
 svn co svn://anonsvn.kde.org/home/kde/branches/KDE/3.5/kde-common/admin
 svn up keximdb
 make -f Makefile.cvs
 ./configure --enable-debug=full --prefix=`kde-config --prefix`
 make
 sudo make install

```

---

### Post by InfinityCircuit on 2008-07-30
I think you are a bit confused:

> So here above it says that svn (subversion) will be downloaded from the site "anonsvn.kde.org", right? And a folder named "kdenonbeta" will then be created in my directory "home/kde/trunk", right? So, what if I don't have a directory named "home/kde/trunk"? Is it going to create all those new folders ie "kde", and then "trunk", and then "kdenonbeta"?

Right now, all my kexi compiling work has been done in /home/swarup/koffice. So I was thinking perhaps I should direct "kdenonbeta" to be created there instead? After all, that is where "Kexi" and "lib", etc, are located.

It won't download subversion, subversion will download the source code from that site.  It will just create the last directory in the sequence.  If you want it to download into another directory then just add that directory at the end of the pull code (svn co [http://...whatever](http://...whatever)... <new directory here>).

You should already have the necessary libraries installed to compile kdenonbeta without putting it in the koffice directory.  make isn't smart enough to dynamically link those development libraries from a specific working directory automatically.

> Given that the above worked fine, does it look like the below code should work with it well to install Kexi's MS Access import tool for me in Ubuntu? Or are the lines made for someone having KDE, and I have to adjust some of the lines for Ubuntu ie given that this is a Debian install and not a KDE install?


The code you posted should work fine.  If you already installed koffice in ubuntu you should have the needed libraries.  The notion of a "debian not a kde install" makes no sense, as Debian is just apt/dpkg and can have either kde or gnome or e17 or wmii or dwm or twm or just console.

---

### Post by swarup on 2008-07-30
I see. What you've explained makes a lot of sense. I just need to get a little bit more of the vocabulary under my belt. It all makes sense if you know what the terms mean.

Anyhow, I went ahead and tried the first line of the install procedure. Here is what happened:

```
swarup@swarup-laptop:~$ svn co -N svn://anonsvn.kde.org/home/kde/trunk/kdenonbeta/
svn: URL 'svn://anonsvn.kde.org/home/kde/trunk/kdenonbeta' doesn't exist
```

So I guess the download site address isn't up-to-date or something? Have I worded the command wrong somehow? 

I tried to communicate with the maintainer but he seems to be out of station, has been for quite some days. Unless anyone has any suggestion as to why it is saying the URL "doesn't exist", I guess I'll have to wait till he gets back.

add: I have been on the Kexi IRC channel. Someone replied to me there, that "just looked in the source, appears the mdb driver isnt ported yet to trunk/koffice 2 that is". So perhaps that is why it is saying the URL doesn't exist.

---

