---
title: "I used to use a personal repository for offline updates now it fails"
date: 2016-04-25
forum: New to Ubuntu
---

### Post by Timberlandnut on 2016-04-25
On 15.10 I used to create a personal repository with the dpkg scanpackagres command
In 16.04 on update of repositories I get a wack of errors

Almost exactly like the user in this thread

[http://ubuntuforums.org/showthread.php?t=2321662](http://ubuntuforums.org/showthread.php?t=2321662)


With pretty much exactly the same errors except for the file path.


How do you create a personal repository in 16.04 ?
the documentation for older distributions now fail.

---

### Post by Timberlandnut on 2016-04-28
How do I create a repository on the hard drive I'm 16.04?



I used to use the directions below to create a repository so I could upgrade offline computers. But now I get a whole bunch of errors when apt-get update.


Creating a Personal Repository

There are 4 steps to setting up a simple repository for yourself

    Install dpkg-dev
    Put the packages in a directory

    Create a script that will scan the packages and create a file apt-get update can read
    Add a line to your sources.list pointing at your repository 

Install dpkg-dev

Type in a terminal

sudo apt-get install dpkg-dev

The Directory

Create a directory where you will keep your packages. For this example, we'll use /usr/local/mydebs.

sudo mkdir -p /usr/local/mydebs

Now move your packages into the directory you've just created.

Previously downloaded Packages are generally stored on your system in the /var/cache/apt/archives directory. If you have installed apt-cacher you will have additional packages stored in its /packages directory.

The Script update-mydebs

It's a simple three liner:

 #! /bin/bash
 cd /usr/local/mydebs
 dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz

Cut and paste the above into gedit, and save it as update-mydebs in ~/bin. (the tilde '~' means your home directory. If ~/bin does not exist, create it: Ubuntu will put that directory in your PATH. It's a good place to put personal scripts). Next, make the script executable:

chmod u+x ~/bin/update-mydebs

How the script works:

dpkg-scanpackages looks at all the packages in mydebs, and the output is compressed and written to a file (Packages.gz) that apt-get update can read (see below for a reference that explains this in excruciating detail). /dev/null is an empty file; it is a substitute for an override file which holds some additional information about the packages, which in this case is not really needed. See deb-override(5) if you want to know about it.

Sources.list

add the line

deb file:/usr/local/mydebs ./

to your /etc/apt/sources.list, and you're done.

---

### Post by QIII on 2016-04-28
Threads merged.

---

