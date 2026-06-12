---
title: "Anjuta IDE"
date: 2007-12-20
forum: Programming Talk
---

### Post by twiceasworn on 2007-12-20
Ok, so I love Anjuta, however when I am trying to save a file to my flash drive the IDE tells me that the directory does not exist, even though that is clearly not the case since I could open the file from the same place.  Has anyone else had this issue?  If anyone knows how to remedy this it would be great.  right now I have to save to my home directory and then cp the files to my jump drive, which is a bit silly.  Thanks in advance :)

---

### Post by donatell0 on 2007-12-29
I suppose you've tried to file a bug by now and found that it already exists or something. Anyways which version of Anjuta are you using?

---

### Post by melopsittacus on 2008-01-01
Hi!

I have just installed Anjuta 2.2.0. I have two problems with creating new items:

First if I try to create a new glade file, Anjuta just quits without any error messages. Is it a bug or am I doing something wrong?

Second, if I try to create a new project, Anjuta says it needs autogen package. I could not find this package under Ubuntu's add/remove applications. Do I have to install this package manually?

---

### Post by donatell0 on 2008-01-01
I dont know about the glade file, but you can install autogen easily using the command 

sudo apt-get install autogen

or you can also use synaptic package manager under System->Administration.

[EDIT]: Actually, the same thing happened to me when I opened a glade file, and I have glade3 and everything installed. So my guess is that its a bug.

---

### Post by melopsittacus on 2008-01-02
Thanks donatell0, I installed autogen, but I cannot use Anjuta yet. Now it says it needs glib, which I cannot find neither in the Add/Remove Programs nor in the Synaptic package manager, and apt-get install glib also says it cannot find glib. It seems important because I cannot build the project without it (Build/Build is grey...)

---

### Post by donatell0 on 2008-01-03
I am not at my Gutsy Gibbon comp anymore. But a little bit hunting, let me find a number of packages: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=glib&searchon=names&subword=1&version=gutsy&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=glib&searchon=names&subword=1&version=gutsy&release=all")

Look for the package **libglib** in synaptic.

---

