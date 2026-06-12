---
title: "synaptic repository vs tomcat5 and java-packages"
date: 2006-04-14
forum: Repositories &amp; Backports
---

### Post by slshults on 2006-04-14
So, I've been following the [ApacheMySQLPHP]("https://wiki.ubuntu.com/ApacheMySQLPHP") HowTo in the wiki.  I'm working with a fresh install of Breezy.  

All has been going swimmingly well until I get to this command:

```
sudo apt-get install tomcat5 tomcat5-admin tomcat5-webapps
```

the results i get are:

```
:~$ sudo apt-get install tomcat5 tomcat5-admin tomcat5-webapps
Reading package lists... Done
Building dependency tree... Done
Package tomcat5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package tomcat5 has no installation candidate
```
So right away you're probably thinking "add universe and multiverse repositories and try again."   But alas, that has already been done (multiple attempts.)  Synaptic goes through the motions, but after all is said an done, there's no change in the tomcat5 issue.  Here's the contents of my /etc/apt/sources.list 
```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

The problem is wider than tomcat5:

```
sudo apt-get install java-packages
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-packages
```

any suggestions to help me get the extra repositories working?

(I'm trying to build a new ubuntu box to use as a server to replace an old redhat8 box which needs to go away.)

---

### Post by bryanl on 2006-04-14
did you do an apt-get update before trying the install and after modifying sources.list?

---

### Post by slshults on 2006-04-14
thanks bryan, yes, I should have mentioned that.

---

### Post by slshults on 2006-04-14
update: I'm trying with this sources.list below now, which has given me the java-packages, but tomcat5 remains elusive.

```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://us.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse

# Seveas' packages (packages, GPG key: 1135D466)
deb http://mirror.ubuntulinux.nl breezy-seveas all

# Ubuntu backports project (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://us.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse

# Seveas' packages (packages, GPG key: 1135D466)
deb http://mirror.ubuntulinux.nl breezy-seveas all

# Ubuntu backports project (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

# Penguin Liberation Front (packages)
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

```

---

### Post by 146lily on 2006-04-14
I have tomcat5.0.30-9 showing in synaptic using  fr   instead of  us  in your source.list  , I don't trust US and UK repositories.....sorry I'm paranoid and maybe stupid.

Make a new list using fr as your country or whatever...

---

### Post by slshults on 2006-04-14
interesting.  are the comments in the files you get written in french or in english?  are any language configs set to french for default instead of english?

---

### Post by 146lily on 2006-04-14
All my software is added by synaptic and comes from France, all in English, lang. must be set by my operating system. It's easy to try France or any other country which is politically friendly to linux. How about New Zealand.....

Here's a link for countries to try near you

[http://en.wikipedia.org/wiki/Country_code_top-level_domain](http://en.wikipedia.org/wiki/Country_code_top-level_domain)

---

### Post by slshults on 2006-04-14
Thanks.  I tried ca, uk and fr, and no tomcat on any of them.  (i did a "sudo apt-get update" between each, no errors in update output)

](*,)

---

### Post by 146lily on 2006-04-14
How about using synaptic gui....its there for me now.

---

### Post by 146lily on 2006-04-14
_my list_

# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)

# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper main restricted 
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper-updates main restricted 
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted 

# Ubuntu supported packages (sources, GPG key: 437D05B5)
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper main restricted  
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper-updates main restricted  
# deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted  

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper universe multiverse 
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper-updates universe multiverse 
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe multiverse 

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper universe multiverse  
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper-updates universe multiverse  
# deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe multiverse  

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
# deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main  

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
# deb-src [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

I'm using Dapper....will switch to Breezy and check again.

---

### Post by 146lily on 2006-04-14
tomcat5 is not in main breezy archive.

---

### Post by slshults on 2006-04-14
[QUOTE=146lily]tomcat5 is not in main breezy archive.[/QUOTE]

thanks for the confirmation.  i'll email the author of [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP) to let him know.

in the meantime, I got tomcat up and running with help from [this thread over here]("http://ubuntuforums.org/showthread.php?t=44006&highlight=tomcat").

---

