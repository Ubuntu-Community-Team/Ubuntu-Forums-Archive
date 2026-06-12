---
title: "errors with repos"
date: 2006-07-22
forum: Repositories &amp; Backports
---

### Post by visvak on 2006-07-22
i've always had this problem since i screwed up my orignal sources.list and got a new one from source-o-matic. i'm not complaining. the extra repos are great. but i hate seeing an error message everytime i hit reload. can someone help me fix them ? here are the errors - 

```
http://people.ubuntu.com/~jbailey/snapshot/bzr/./Release: No MD5Sum entry in Release file /var/lib/apt/lists/people.ubuntu.com_%7ejbailey_snapshot_bzr_._Release
ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz: Unable to fetch file, server said 'Failed to open file.  '
ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz: Unable to fetch file, server said 'Failed to open file.  '
ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/source/Sources.gz: Unable to fetch file, server said 'Failed to open file.  '
ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/source/Sources.gz: Unable to fetch file, server said 'Failed to open file.  '
```

---

### Post by warbread on 2006-07-22
Comment out those repos.  I don't think that's a client side problem, or anything you can fix.

---

### Post by greenstar on 2006-07-23
I agree with warbread. If you need the PLF repos, use these:

```
# Penguin Liberation Front (PLF)

# PLF primary repository HTTP 100mbit/s mirror provided thanks to OVH (http://ovh.com)
deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free

# PLF secondary repo. Use if primary repo is offline. FTP mirror from http://free.fr (french ISP)
# deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free
# deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free

# PLF Mirrors: Use if primary and secondary are offline

# PLF mirror 1
# deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ dapper free non-free
 
# PLF mirror 2
# deb http://theli.free.fr/packages/dapper/ ./

``` 
If you'd like to see my entire sources.list, here it is:

```
# Hand-Customized variant of:
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY wit# gpg --keyserver subkeys.pgp.net --recv KEYh the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Backports 
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
# deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main
# deb-src ftp://cipherfunk.org/pub/packages/ubuntu dapper main

# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
# deb http://kubuntu.org/packages/kde-latest dapper main
# deb-src http://kubuntu.org/packages/kde-latest dapper main

# kubuntu.org packages for the latest Koffice version (packages, GPG key: DD4D5088)
# deb http://kubuntu.org/packages/koffice-latest dapper main
# deb-src http://kubuntu.org/packages/koffice-latest dapper main

# kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
# deb http://kubuntu.org/packages/amarok-latest dapper main
# deb-src http://kubuntu.org/packages/amarok-latest dapper main

# Penguin Liberation Front (PLF)

# PLF primary repository HTTP 100mbit/s mirror provided thanks to OVH (http://ovh.com)
deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free

# PLF secondary repo. Use if primary repo is offline. FTP mirror from http://free.fr (french ISP)
# deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free
# deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free

# PLF Mirrors: Use if primary and secondary are offline

# PLF mirror 1
# deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ dapper free non-free
 
# PLF mirror 2
# deb http://theli.free.fr/packages/dapper/ ./

# Wine Official (Non-Ubuntu)
# deb http://wine.sourceforge.net/apt binary/
# deb-src http://wine.sourceforge.net/apt source/

# Wine Bleeding Edge
# deb http://wine.budgetdedicated.com/apt dapper main
# deb-src http://wine.budgetdedicated.com/apt dapper main

# Dapper-commercial by canonical
# currently has realplay (realplayer 10) and opera (opera 9)
deb http://archive.canonical.com/ubuntu dapper-commercial main

# The Opera browser (packages)
# deb http://deb.opera.com/opera etch non-free

# Automatix (packages, GPG key: 521A9C7C)
# deb http://www.getautomatix.com/apt dapper main

# Repository for Skype
deb http://download.skype.com/linux/repos/debian/ stable non-free

# Google Picasa for Linux repository
deb http://dl.google.com/linux/deb/ stable non-free

# Cinelerra: Choose your Architecture
# i686:
# deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/ ./
# athlonxp:
deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/ ./
# pentium4:
# deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/ ./

# mjpegtools ubuntu backport (for Cinelerra)
deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools ./

```

---

### Post by visvak on 2006-07-23
thanks for the sources.list greenstar. BTW, what is cinelerra ? is that mjpeg tools backport only for cinelarra ?

EDIT : ummm... error again dude. this time its -

```
Err http://us.archive.ubuntu.com dapper Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (146.137.96.7), connection timed out
Err http://us.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (146.137.96.7), connection timed out
Fetched 6B in 8m0s (0B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Could not connect to us.archive.ubuntu.com:80 (146.137.96.7), connection timed outFailed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Could not connect to us.archive.ubuntu.com:80 (146.137.96.7), connection timed out
```

ok that was stupid of me to post without checking the rest of the forum. i saw ur other post and changed to the UK repos. working fine now. thanks. this is the first time since i got my source-o-matic list that i havent seen errors.

---

### Post by greenstar on 2006-07-23
> **visvak said:**
> thanks for the sources.list greenstar.

You're welcome.

> **visvak said:**
>   BTW, what is cinelerra ? is that mjpeg tools backport only for cinelarra ?

Cinelerra is a professional grade NLE Video Editor for Linux. Yes, the mjpegtools are required by Cinelerra. I use it when I need to do something that's beyond Kino's capabilities.

> **visvak said:**
>   i saw ur other post and changed to the UK repos. working fine now. thanks. this is the first time since i got my source-o-matic list that i havent seen errors.

If the US repos stay down, the UK repos might feel some heat from the extra traffic, so I'm currently on the Brazilian repos with no problems.

Greenstar

---

### Post by luckylucky on 2006-07-24
I've changed over my repos list to now have Brazil (br) and that part now seems to work (thanks) but for some strange reason at the end of the downloading it keeps trying to connect to [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com)   

I errased all instances of ca. in my sources list replacing with br.  I don't understand why it keeps insisting to check [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) (other than the fact that I'm canadian eh?).  It keeps getting hung on it as that repos is also broken.  Is there some other file (similar to sources.list) that perhaps also could be edited???

Help please... & thanks!

---

### Post by greenstar on 2006-07-25
Did you: 
```
sudo apt-get update
```

As far as I know, sources.list is it for repos. Have you tried the Find function in gedit in the Search menu? Use Find to identify all occurences of "ca" and replace them with "br" or "uk". If you can't find it, post your sources.list.

---

### Post by nekr0z on 2006-07-29
PLF repository is nice, but what GPG key do they have and how can I add it so that aptitude stops bugging me about non-verified packages?

---

### Post by pomegranate on 2006-08-03
I've got a rather more basic problem in this area. Sources.list is read-only, and the file properties says that 'You are not the owner, so you can't change the permissions'. I've made a copy of the file to my desktop, changed the permissions to that, but then I seem unable to copy it to the apt folder. Can someone tell me what I should do, but also explain the basic reasons for this problem. I'm a noob but I'm trying to understand all of this...

Additionally, my sources.list has references to gb rather than uk, is this out of date or something? I've had a patchy time of updating stuff, and can never fully download packages when installing programs. I'm running Breezy.

---

### Post by coltey on 2006-08-03
I was on another site called LinuxWatch and read some posts regarding ubunto and they had mentioned something about the US archives were having problems keeping up so I was wondering about changing my repositories and want to say thanks to luckylucky and greenstar for bringing up Brazil. I changed my repos to point to br instread of us and viola, updated successfully. Many thanks again...

sgc

---

### Post by nekr0z on 2006-08-03
No problem, pomegranate! This is solved quite simply.

In Linux (as well as UNIX and BSDs) the important system settings and files are not allowed to be modified by the ordinary user, this is for security. The only way to make things work is to provide ownership to the system files not to user (you), but to some administrator, or, as we in Linux-world say, Superuser, also called "root".

If you go to console and try to look at the /etc/apt directory with```
ls -Al /etc/apt
``` you'll see something like:> -rw-r--r-- 1 root root  5535 2006-07-30 02:41 sources.list

This means, that file "sources.list" is owned by user "root" and belongs to group "root". "-rw-r--r--" means that the owner (root) can Read and Write this file, the group (root) can only Read, and everybody else (this includes users like yourself) can only Read the file.

Luckily, there is a way to give a command to the system as if you were root. For example, if you enter```
nano /etc/apt/sources.list
```in console to edit the file, you do it as yourself and are not allowed to write what you have modified. But if you do```
sudo nano /etc/apt/sources.list
```this means that the command is issued by root, so you will be allowed to write the file. For security reasons, you will have to enter your password when doing something "sudo".

---

