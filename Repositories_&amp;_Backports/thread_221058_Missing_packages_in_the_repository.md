---
title: "Missing packages in the repository?"
date: 2006-07-22
forum: Repositories &amp; Backports
---

### Post by Newbie123 on 2006-07-22
According to:
[http://packages.ubuntu.com/dapper/python/python-opengl](http://packages.ubuntu.com/dapper/python/python-opengl)

There is a pyopengl package for python 2.4

After running sudo apt-get update and sudo apt-cache search, I can't seem to find this package at all using the search, I have tried the following terms:

python
open
opengl
gl

Is it possible that my local repository somehow became corrupted? How can I check?

Or am I completely wrong, and this package does not exist for python 2.4.

I am using ubuntu 6.06.

---

### Post by moma on 2006-07-22
$ [COLOR="Green"]apt-cache search python-opengl[/COLOR]
python-opengl - Python binding to OpenGL
python2.4-opengl - Python binding to OpenGL

$ [COLOR="Green"]apt-cache show python2.4-opengl[/COLOR]
...
Filename: pool/universe/p/pyopengl/python-opengl_2.0.1.09-1.1ubuntu3_all.deb

As you can see  it's in the Universe repository.
Edit your /etc/apt/sources.list and uncomment universe repository lines. 

Or fix your /etc/apt/sources.list by following this guide.
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories")

Then 
$ [COLOR="Green"]sudo apt-get update[/COLOR]
and search again.

// moma
   [http://www.futuredesktop.com/ubuntu6.06.html]("http://www.futuredesktop.com/ubuntu6.06.html")

---

### Post by Newbie123 on 2006-07-22
I think that I have already uncommented the universe part. Could there be some other reason why it is not working? Could you post your sources.list here?


Here is my sources.list file:

-------------------

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted 
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe 
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by moma on 2006-07-22
Here is my /etc/apt/sources.list 
[http://www.futuredesktop.com/dapper/sources.list]("http://www.futuredesktop.com/dapper/sources.list")

Take backup-copy of yours and replace it. 
And refresh the package list (index) in your PC.
$ [COLOR="Green"]sudo apt-get update [/COLOR]

PS. Read also this thread
[http://ubuntuforums.org/showthread.php?p=1287973#post1287973]("http://ubuntuforums.org/showthread.php?p=1287973#post1287973")

---

### Post by Newbie123 on 2006-07-22
Ok, I figured out the problem.

I was having problems with adept. I tracked it down to having us.archive.urbuntu.com as my repository. The US servers are apparently flaky.

I stripped out the 'us' part, ran apt-get update, and then I could search for all of the packages.

Previously, it looked like apt-get had only done a partial update, and hence was missing some specific packages.

---

