---
title: "Using the terminal to uninstall PPA repositories? Really need help!"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by iceytina on 2012-04-07
I've been reading how to do this... among numerous rather Linux-geekery ways above me, I have installed a PPA purging program so I can use the terminal to get rid of packages.

Like ppa-purge -p packagehere

I really need to get rid of the matthaeus gimp 2.7 package on my system in /etc/apt/sources.list.d/matthaeus123-mrw-gimp-svn-oneiric.list. I had installed this following instructions on how to upgrade to unstable GIMP 2.7 version.

Apparently I'm not listing the path right because I can't get ppa-purge to work right.

I'm unable to run updates, install new programs, or access the package manager while matthaeus123-mrw-gimp-svn-oneiric sits hostile on my system.

How do I get rid of it?
I'm on Ubuntu 11.10 32-bit.

---

### Post by SeijiSensei on 2012-04-07
Some PPAs would modify the file /etc/apt/sources.list and add an entry to the bottom of that file.  However it now appears the proper method is to add files to /etc/apt/sources.list.d/.  Take a look in both places for the entry that points to the PPA you'd like to remove.

---

### Post by Curtis6767 on 2012-04-07
I needed to remove a repo a while back and[ this is the thread I started]("http://ubuntuforums.org/showthread.php?t=1950136&highlight=removing+repository").


Look at post # 13 for directions on how to go about this.

Not done through Terminal, but it worked for me.

Your mileage may vary.

---

### Post by iceytina on 2012-04-07
> **SeijiSensei said:**
> Some PPAs would modify the file /etc/apt/sources.list and add an entry to the bottom of that file.  However it now appears the proper method is to add files to /etc/apt/sources.list.d/.  Take a look in both places for the entry that points to the PPA you'd like to remove.

I've never added entries into the sources.list file so I don't know how.
There's no entry in entries.list for the matthaeus PPA however... there are 5 files for it in the entries.list.d directory.

When I'm in that directory (cd /etc/apt/sources.list.d/) and then run the ppa-purge command, here's what I get.

First dir:
matthaeus123-mrw-gimp-svn-natty.list
matthaeus123-mrw-gimp-svn-natty.list.distUpgrade
matthaeus123-mrw-gimp-svn-natty.list.save
matthaeus123-mrw-gimp-svn-oneiric.list
matthaeus123-mrw-gimp-svn-oneiric.list.save

Second:
[EMAIL="christina@christina-PC:/etc/apt/sources.list"]christina@christina-PC:/etc/apt/sources.list[/EMAIL].d$ sudo ppa-purge ppa:matthaeus123-mrw-gimp-svn-oneiric.list
Updating packages lists
E: Type 'src' is not known on line 2 in source list /etc/apt/sources.list.d/matthaeus123-mrw-gimp-svn-oneiric.list
E: The list of sources could not be read.
Warning:  apt-get update failed for some reason
PPA to be removed: ppa:matthaeus123-mrw-gimp-svn-oneiric.list 
ppa:matthaeus123-mrw-gimp-svn-oneiric.list
Warning:  Could not find package list for PPA: 
ppa:matthaeus123-mrw-gimp-svn-oneiric.list 
ppa:matthaeus123-mrw-gimp-svn-oneiric.list
[EMAIL="christina@christina-PC:/etc/apt/sources.list"]christina@christina-PC:/etc/apt/sources.list[/EMAIL].d$ sudo ppa-purge ppa:matthaeus123-mrw-gimp-svn-natty.list
Updating packages lists
E: Type 'src' is not known on line 2 in source list /etc/apt/sources.list.d/matthaeus123-mrw-gimp-svn-oneiric.list
E: The list of sources could not be read.
Warning:  apt-get update failed for some reason
PPA to be removed: ppa:matthaeus123-mrw-gimp-svn-natty.list 
ppa:matthaeus123-mrw-gimp-svn-natty.list
Warning:  Could not find package list for PPA: 
ppa:matthaeus123-mrw-gimp-svn-natty.list 
ppa:matthaeus123-mrw-gimp-svn-natty.list

> **Curtis6767 said:**
> I needed to remove a repo a while back and[ this is the thread I started]("http://ubuntuforums.org/showthread.php?t=1950136&highlight=removing+repository").
Look at post # 13 for directions on how to go about this.
Not done through Terminal, but it worked for me.
Your mileage may vary.

Thanks for the forum suggestion Curtis. However, since I can't open the update manager, software center, or repositories GUI interfaces, I can't really do anything that was listed in the threads. My only hope (lols) is via terminal.

Or just re-installing Linux which I don't want to do, since I had a friend compile a Genius stylus tablet driver for me and he's since moved to another state. I can't lose that functionality.

---

### Post by stinkeye on 2012-04-07
Try y-ppa-manager.
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=11805378&postcount=4").

---

### Post by oldos2er on 2012-04-07
> **iceytina said:**
> I've never added entries into the sources.list file so I don't know how.
There's no entry in entries.list for the matthaeus PPA however... there are 5 files for it in the entries.list.d directory.

When I'm in that directory (cd /etc/apt/sources.list.d/) and then run the ppa-purge command, here's what I get.

First dir:
matthaeus123-mrw-gimp-svn-natty.list
matthaeus123-mrw-gimp-svn-natty.list.distUpgrade
matthaeus123-mrw-gimp-svn-natty.list.save
matthaeus123-mrw-gimp-svn-oneiric.list
matthaeus123-mrw-gimp-svn-oneiric.list.save


If you want to delete the matthaeus123 PPA, run ```
sudo rm /etc/apt/sources.list.d/matthaeus123*

sudo apt-get update
```

---

### Post by iceytina on 2012-04-07
> **oldos2er said:**
> If you want to delete the matthaeus123 PPA, run ```
sudo rm /etc/apt/sources.list.d/matthaeus123*

sudo apt-get update
```

You are my hero. I can't believe something that simple worked, but it did. Thanks my friend----soooo much!!!!

---

### Post by oldos2er on 2012-04-07
You're welcome.

---

