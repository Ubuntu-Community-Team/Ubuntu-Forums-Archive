---
title: "Getting and error + Software centre instantly crashing 14.04"
date: 2014-05-25
forum: New to Ubuntu
---

### Post by Egulston on 2014-05-25
--SOLVED--

Hi all,

Ive been getting this problem right after installing ubuntu 14.04. The error message is

'Unknown Error:'<class'SystemError'>'(E:Malformed line 58 in source list /etc/apt/sources.list(dist parse))'.



Software center is also having problems as it is crashing as soon as I open it.

Does anyone have any ideas on how to fix this? I really need to get some software onto my desktop.

Thanks in advance.

---

### Post by deadflowr on 2014-05-25
Open the program "gedit" and then click "Open"
Go to the side pane and click on "file system".
Then in the main window go to etc, then to apt, then to sources.list (NOT sources.list.d)
then copy it and paste it here, using [code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

The file should look something like this, for reference
```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirror.anl.gov/pub/ubuntu/ precise main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.anl.gov/pub/ubuntu/ precise-updates main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.anl.gov/pub/ubuntu/ precise universe
deb-src http://mirror.anl.gov/pub/ubuntu/ precise universe
deb http://mirror.anl.gov/pub/ubuntu/ precise-updates universe
deb-src http://mirror.anl.gov/pub/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.anl.gov/pub/ubuntu/ precise multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ precise multiverse
deb http://mirror.anl.gov/pub/ubuntu/ precise-updates multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.anl.gov/pub/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ precise-backports main restricted universe multiverse

deb http://mirror.anl.gov/pub/ubuntu/ precise-security main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ precise-security main restricted
deb http://mirror.anl.gov/pub/ubuntu/ precise-security universe
deb-src http://mirror.anl.gov/pub/ubuntu/ precise-security universe
deb http://mirror.anl.gov/pub/ubuntu/ precise-security multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

```

---

### Post by Egulston on 2014-05-25
Here you go!

```
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://au.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://au.archive.ubuntu.com/ubuntu/ trusty universe
deb http://au.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://au.archive.ubuntu.com/ubuntu/ trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://au.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner


## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu trusty main
deb http://archive.canonical.com/trusty partner
deb-src http://archive.canonical.com/trusty partner
# deb-src http://extras.ubuntu.com/ubuntu trusty main

```

---

### Post by claracc on 2014-05-25
These two lines: 
```
deb http://archive.canonical.com/trusty partner
deb-src http://archive.canonical.com/trusty partner
```

The two ones before the last one, don't correspond with a correct url, so you can disable them writing a # sign in the begining of the lines, ( in order to edit the sources.list file you have to run the command 
```
gksudo gedit /etc/apt/sources.list
```, then write the commnet sign as addresses) then, save the file and try again:

```
sudo apt-get update
```

---

### Post by claracc on 2014-05-25
Well, I am going to add more information to my before post.

I hace tried all the https addresses you have in your sources.list file and all of them return a 404 not found error:

```
The requested URL /ubuntu/ trusty main restricted was not found on this server.
Apache/2.2.15 (Red Hat) Server at 127.0.0.1 Port 8080
```

In you software sources, what server have you selected to obtain the ubuntu updates?

---

### Post by Egulston on 2014-05-25
It worked! Thank you.

---

### Post by claracc on 2014-05-26
Glad you got fixed your problem.

Please, mark the thread as solved with thread tools menu in the upper right part of the page.

Thanks.

---

### Post by deadflowr on 2014-05-26
> **claracc said:**
> 
I hace tried all the **https** addresses you have in your sources.list file and all of them return a 404 not found error:


Are we looking at the same sources.list?
I don't see any entries for https.

Or was that a different thread?

Edit: OH, and good fix, by the way.(For this thread)

---

### Post by claracc on 2014-05-26
I am referring to the url addresses written in sources .list, as for example:

```
http://au.archive.ubuntu.com/ubuntu/ trusty universe
http://au.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
```

Perhaps I had to write http's, what I mean, I wanted to write it in plural, not referring to other technical definitions.
As you can see, english language is sometimes a bit difficult for me.

---

### Post by deadflowr on 2014-05-26
> **claracc said:**
> I am referring to the url addresses written in sources .list, as for example:

```
http://au.archive.ubuntu.com/ubuntu/ trusty universe
http://au.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
```

Perhaps I had to write http's, what I mean, I wanted to write it in plural, not referring to other technical definitions.
As you can see, english language is sometimes a bit difficult for me.


8-)
That makes sense, then.

And your English writing is fine.

---

