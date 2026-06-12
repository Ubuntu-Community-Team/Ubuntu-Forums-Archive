---
title: "HowTo: LAN Repo.. or backups"
date: 2006-06-28
forum: Outdated Tutorials &amp; Tips
---

### Post by noob_Lance on 2006-06-28
Well As we all know... one great benifit of using ubuntu or any distro built upon debian.. is the easy way to install programs using apt-get. BUT it has one downfall.. you must be connected to the internet at all times to use it. 

But Now if you take the time.... you can now backup every package in the ubuntu repo's. While this DOES take an absolutly large amount of time. At this moment i have been going for atleast 13 hours downloaded all of them... and i still have some time to go.

I was searching alot and asking questions and finally came across 2 articles.. And by piecing them togather... i have come up with the perfect way to build your self a repository using All or just some of the .deb's that we will download.


*WARNING!* There Is relativly 12 gigs worth of files that will be downloaded.... so be sure you have the time AND the space to do this *END WARNING!*

_Step 1_

To start our process, we will create a local mirror.. 

```

$ sudo aptitude install debmirror

```

_Step 2_

Next We Will download all the files from main, multiverse and universe sections of the i386 arch. You can change to whatever arch you decide to. And download only the sections you wish. Its very easy to see how this little code works.

```

$ debmirror --nosource -m --passive --host=archive.ubuntulinux.org \
--root=ubuntu/ --method=ftp --progress --dist=dapper \
--section=main,multiverse,universe --arch=i386 ubuntu/ --ignore-release-gpg

```

*Note-- Above the "/" just seperates the command into lines... the command itself is on one line.

Make yourself comfortable, grab a drink and a snack... or hell even go to bed because this is going to take some time to run thru. 

*STEPS 3 THRU 7 ARE FOR DVD BACKUP ONLY!* 
*IF MAKING A LAN REPO... SKIP TO STEP 8*
_Step 3_
We will now go through the steps to create your dvd backups of all the files you just downloaded... which is alot lol

We Will now install another program.
```

$ sudo aptitude install debpartial

```
This program will seperate the repos we just downloaded into dvd sized volumes.

_Step 4_
We Will now create the directory we will create the volumes in.

```

$mkdir ubuntu-dvd

```

_Step 5_
and we make it to construct the package descriptors to every volume.

```

$ debpartial --nosource --dirprefix=ubuntu --section=main,universe,multiverse \
--dist=dapper --size=DVD ubuntu/ ubuntu-dvd/

```

_Step 6_
Now we have to put the packages into the directories debpartial have just created. The script debcopy  which also comes with the debpartial package will do it.

```

$ ruby debcopy ubuntu/ ubuntu-dvd/ubuntu0
$ ruby debcopy ubuntu/ ubuntu-dvd/ubuntu1
$ ruby debcopy ubuntu/ ubuntu-dvd/ubuntu2

```

Where *ubuntu/* is the directory with the complete repository created with debmirror and *ubuntu-dvd/** are the directories ready to host the new DVD-ready repository.

_Step 7_
To get the directories ubuntu0, ubuntu1, ubuntu2 into an iso image ready to burn we can use mkisofs:

```

$ mkisofs -f -J -r -o ubuntu-dvd-0.iso ubuntu-dvd/ubuntu0
$ mkisofs -f -J -r -o ubuntu-dvd-1.iso ubuntu-dvd/ubuntu1
$ mkisofs -f -J -r -o ubuntu-dvd-2.iso ubuntu-dvd/ubuntu2

```

And Once those ISO's are completed you are ready to pop in a dvd and burn yourself your repo dvd backups ^_^


*NOW FOR THE LAN SECTION!*
Ok this section is NOT be proven by myself.. but is mostly taken from [this](http://www.ubuntuforums.org/showthread.php?t=42862) thread

Before We Start there are some things to consider. 
1- Will this repo  be local or remote. 
   --Local being on the machine you are looking at this on.
   --Remote. a machine running ubuntu on your LAN. This requires Apache to be installed

_Step 8_
Most installs come with these programs... but to be sure.. we will run apt-get just to be sure

```

sudo apt-get install apt-utils
sudo apt-get install dpkg-dev

```

_Step 9_
Now Create your Repo Directory if you havnt already created it. Now... again consider if its local or remote. if it is going to be a remote repo... use /var/www. If its local.. then anywhere is good.

```

mkdir /home/your repo dir/

```

_Step 10_
Fill your Repo directory with your .deb's. 

_Step 11_
Now to make a program that will make these .deb's apt-able

```

cd /bin/
sudo nano autorepo

```

Now insert this into the new file:

```

#!/bin/bash
sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz
sudo dpkg-scansources . /dev/null | gzip -9c > Sources.gz

```

and finally make it executable

```

sudo chmod +x autorepo

```

_Step 12_
Now to create your repo packages.gz and sources.gz

```

cd /home/your repo name/
autorepo

```

_Step 13_
Editing your sources list.

```

sudo nano /etc/apt/sources.list

```

Then add your repo into your sources list.

```

##My Repo
deb file:///path/to/repository/ reponame/

#example:
deb file:///home/ repo/

#and for remote:
deb http://host name or ip/ repo/

```

*Note... Its important to remember that you need to add your repo dir with a space and then "/" otherwise apt will not beable to read the files correctly.

That is All Folks. You are now ready to go!

But I know people will ask "why would you do this?", "no one has the time to do this", ect..! I will give you an example of when something such as this would be useful. If you have a network at home or even an office and would like to control the packages the employees install... Edit there sources list to have only your server in it. and only put the .deb's you approve of into there. 
Or even if you dont want to have all the packages... this is a great way to set up a repo for the ubuntu community!



*It has now been 15 hours and the repos are still downloading... so beware! this isnt a small venture!.

~Lance

---

### Post by profediego on 2006-09-23
Hi Lance, 

Excelent how to, just what i was lookin for, just one question, how do i maintain my repos up to date with the ubuntu repos?

Thanks

---

### Post by SgtDude on 2007-06-11
To update your repo, just execute step 2 again.  Don't worry, it'll only download new packages (but scanning the local repo will probably take 10 minutes or so, so don't fret).

---

