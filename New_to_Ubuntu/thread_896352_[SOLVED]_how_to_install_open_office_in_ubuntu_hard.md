---
title: "[SOLVED] how to install open office in ubuntu hardy ?"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by imgkg on 2008-08-21
hi guys i was having some errors with previously installed open office so i removed it now i downloaded a new tar file from open office site extracted it on desktop but cant figure out how to install it can you please help

---

### Post by Orlsend on 2008-08-21
No Idea...Why not Use the **Synaptic Package Manager**? or even better the **Add/remove** the update one are in the Repo.

---

### Post by fiddledd on 2008-08-21
Open Office should be available from Add Remove Programs. Install it from there.

EDIT: I posted 30 seconds too late.:)

---

### Post by imgkg on 2008-08-21
i tried it by synaptic way but its showing some dependency errors

---

### Post by tarps87 on 2008-08-21
If it is the .deb download right click extract and then just run the .deb file and it will install

---

### Post by imgkg on 2008-08-21
anf this is the error its giving by ad/remove program method 
> Cannot install 'openoffice.org'

This application conflicts with other installed software. To install 'openoffice.org' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

---

### Post by imgkg on 2008-08-21
its a tar file not deb

---

### Post by tarps87 on 2008-08-21
Got to system -> admin -> package manager and select open office, this should show you what programs are conflicting

---

### Post by t0p on 2008-08-21
If trying to use Add/Remove shows software conflicts, you should do what it says and use Synaptic!  Using Synaptic will resolve those conflicts, but if you decide to do it yourself and install it from source, you will just compound the difficulty.

Use Synaptic.

---

### Post by t0p on 2008-08-21
deleted my post

---

### Post by imgkg on 2008-08-21
i have tried both the ways even by synaptic way its showing error some dependency errors

---

### Post by t0p on 2008-08-21
> **imgkg said:**
> i have tried both the ways even by synaptic way its showing error some dependency errors

What does Synaptic suggest you do?

---

### Post by tarps87 on 2008-08-21
This is the download I was looking at which is a compressed .deb file:
[http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.4.1](http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.4.1)
//I agree that Synaptic will be easier and cleaner, try using it and see what happens
Edit: Just read your last post

---

### Post by imgkg on 2008-08-21
it is showing some dependency errors i am force installing it will let you know whats if its works in few mins

---

### Post by imgkg on 2008-08-21
thanks for giving that link i am downloading it too

---

### Post by imgkg on 2008-08-21
now i guess i have tried everything still not able to install openoffice

---

### Post by imgkg on 2008-08-21
this is the error synaptic is giving me > openoffice.org:
 Depends: openoffice.org-core but it is not going to be installed
 Depends: openoffice.org-writer but it is not going to be installed
 Depends: openoffice.org-calc but it is not going to be installed
 Depends: openoffice.org-impress but it is not going to be installed
 Depends: openoffice.org-draw but it is not going to be installed
 Depends: openoffice.org-math but it is not going to be installed
 Depends: openoffice.org-base but it is not going to be installed
 Depends: openoffice.org-officebean but it is not going to be installed



---

### Post by tarps87 on 2008-08-21
This might now work but try:
```

sudo apt-get autoremove

```
and then
```

sudo apt-get purge openoffice

```
this one will probably as open office is not installed

---

### Post by imgkg on 2008-08-21
its still giving that same error

---

### Post by Elfy on 2008-08-21
If youa re trying to install the openoffice from the oo site - all of the ubuntu openoffice has to be removed completely - if you are using synaptic - right click - Mark for complete removal - also check that you have no residual configs left - if so - Mark them for complte removal as well.

Once you have done that you should be able to install the version you got from the oo site.

[http://ubuntuforums.org/showpost.php?p=5616155&postcount=2](http://ubuntuforums.org/showpost.php?p=5616155&postcount=2)

---

### Post by forger on 2008-08-21
1) Are you trying to download/install openoffice.org version 3 beta?

2) Head to Applications > Accessories > Terminal and execute:
```
sudo apt-get update
sudo apt-get -f install
```

reply with the full output of the above

---

### Post by imgkg on 2008-08-21
i have removed every instance of openoffice from my system only hope left is that debian package than i am downloading

---

### Post by imgkg on 2008-08-21
its not the update version its stable version i am trying to install

---

### Post by Elfy on 2008-08-21
version 2.4 - follow the post link I gave you - it should work - if there are errors at any point stop and post them, did this a few dayts ago with someone else.

---

### Post by lswest on 2008-08-21
to answer your original question, you would go to the folder you extracted it in, then run ```
./configure
make
sudo make install
``` (essentially, but it may be missing a step or two, check the readme that should be included in the archive)

Compiling from source may take a while, requires you to keep the source folder, and makes a mess of your machine, so I'd suggest, as the others have, to fix the error that is occuring before trying to compile from source.

To uninstall, running ```
sudo make uninstall
``` in the source folder should suffice.  It may be different for OO.o source, I haven't checked.  Basically that's how it's done in 90% of the cases.

---

### Post by unutbu on 2008-08-21
imgkg,
You might want to try
```
dpkg --get-selections | grep openoffice | cut -f 1 | xargs apt-cache policy
```
This will print all the openoffice packages currently installed on your system, as well as their version number.

I don't know if you *need* to remove all of these packages to re-install openoffice, but if you did give your computer a completely clean slate
(by using Synaptic to remove each of the packages listed), it seems to me there is a good chance your dependency problem would be solved.

Once you've removed every openoffice package, then run
```

sudo apt-get update
sudo apt-get install openoffice.org # all needed dependencies will be drawn in

```

---

### Post by Elfy on 2008-08-21
> It may be different for OO.o source, I haven't checked. Basically that's how it's done in 90% of the cases.I haven't actually seen source package, but if it was donwloaded from the fornt page it isn't a source package - just an archived debs package.

---

### Post by imgkg on 2008-08-21
this is the out put i got 
 
```
-desktop:~$ dpkg --get-selections | grep openoffice | cut -f 1 | xargs apt-cache policy
openoffice.org-common:
  Installed: (none)
  Candidate: 1:2.4.1-3~bpo40+1
  Version table:
     1:2.4.1-3~bpo40+1 0
        500 http://www.backports.org etch-backports/main Packages
        100 /var/lib/dpkg/status
     1:2.4.1-1ubuntu2 0
        500 http://in.archive.ubuntu.com hardy-updates/main Packages
     1:2.4.0-3ubuntu6 0
        500 http://in.archive.ubuntu.com hardy/main Packages
        500 http://us.archive.ubuntu.com hardy/main Packages
openoffice.org-core:
  Installed: (none)
  Candidate: 1:2.4.1-3~bpo40+1
  Version table:
     1:2.4.1-3~bpo40+1 0
        500 http://www.backports.org etch-backports/main Packages
     1:2.4.1-1ubuntu2 0
        500 http://in.archive.ubuntu.com hardy-updates/main Packages
        100 /var/lib/dpkg/status
     1:2.4.0-3ubuntu6 0
        500 http://in.archive.ubuntu.com hardy/main Packages
        500 http://us.archive.ubuntu.com hardy/main Packages
openoffice.org-draw:
  Installed: (none)
  Candidate: 1:2.4.1-3~bpo40+1
  Version table:
     1:2.4.1-3~bpo40+1 0
        500 http://www.backports.org etch-backports/main Packages
     1:2.4.1-1ubuntu2 0
        500 http://in.archive.ubuntu.com hardy-updates/main Packages
        100 /var/lib/dpkg/status
     1:2.4.0-3ubuntu6 0
        500 http://in.archive.ubuntu.com hardy/main Packages
        500 http://us.archive.ubuntu.com hardy/main Packages
openoffice.org-filter-binfilter:
  Installed: (none)
  Candidate: 1:2.4.1-3~bpo40+1
  Version table:
     1:2.4.1-3~bpo40+1 0
        500 http://www.backports.org etch-backports/main Packages
     1:2.4.1-1ubuntu2 0
        500 http://in.archive.ubuntu.com hardy-updates/main Packages
        100 /var/lib/dpkg/status
     1:2.4.0-3ubuntu6 0
        500 http://in.archive.ubuntu.com hardy/main Packages
        500 http://us.archive.ubuntu.com hardy/main Packages
openoffice.org-hyphenation-en-us:
  Installed: (none)
  Candidate: 2.3.1-2ubuntu1
  Version table:
     2.3.1-2ubuntu1 0
        500 http://in.archive.ubuntu.com hardy/main Packages
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
openoffice.org-impress:
  Installed: (none)
  Candidate: 1:2.4.1-3~bpo40+1
  Version table:
     1:2.4.1-3~bpo40+1 0
        500 http://www.backports.org etch-backports/main Packages
     1:2.4.1-1ubuntu2 0
        500 http://in.archive.ubuntu.com hardy-updates/main Packages
        100 /var/lib/dpkg/status
     1:2.4.0-3ubuntu6 0
        500 http://in.archive.ubuntu.com hardy/main Packages
        500 http://us.archive.ubuntu.com hardy/main Packages
openoffice.org-math:
  Installed: (none)
  Candidate: 1:2.4.1-3~bpo40+1
  Version table:
     1:2.4.1-3~bpo40+1 0
        500 http://www.backports.org etch-backports/main Packages
     1:2.4.1-1ubuntu2 0
        500 http://in.archive.ubuntu.com hardy-updates/main Packages
        100 /var/lib/dpkg/status
     1:2.4.0-3ubuntu6 0
        500 http://in.archive.ubuntu.com hardy/main Packages
        500 http://us.archive.ubuntu.com hardy/main Packages
openoffice.org-thesaurus-en-au:
  Installed: (none)
  Candidate: 2.1-3ubuntu1
  Version table:
     2.1-3ubuntu1 0
        500 http://in.archive.ubuntu.com hardy/main Packages
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
openoffice.org-thesaurus-en-us:
  Installed: (none)
  Candidate: 1:2.4.0~m240-1ubuntu1
  Version table:
     1:2.4.0~m240-1ubuntu1 0
        500 http://in.archive.ubuntu.com hardy/main Packages
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
openoffice.org-writer:
  Installed: (none)
  Candidate: 1:2.4.1-3~bpo40+1
  Version table:
     1:2.4.1-3~bpo40+1 0
        500 http://www.backports.org etch-backports/main Packages
     1:2.4.1-1ubuntu2 0
        500 http://in.archive.ubuntu.com hardy-updates/main Packages
        100 /var/lib/dpkg/status
     1:2.4.0-3ubuntu6 0
        500 http://in.archive.ubuntu.com hardy/main Packages
        500 http://us.archive.ubuntu.com hardy/main Packages
-desktop:~$ sudo apt-get install openoffice.org
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openoffice.org: Depends: openoffice.org-core (= 1:2.4.1-3~bpo40+1) but it is not going to be installed
                  Depends: openoffice.org-writer but it is not going to be installed
                  Depends: openoffice.org-calc but it is not going to be installed
                  Depends: openoffice.org-impress but it is not going to be installed
                  Depends: openoffice.org-draw but it is not going to be installed
                  Depends: openoffice.org-math but it is not going to be installed
                  Depends: openoffice.org-base but it is not going to be installed
                  Depends: openoffice.org-officebean but it is not going to be installed
E: Broken packages
desktop:~$ 


```

---

### Post by unutbu on 2008-08-21
Note this line:
```

  openoffice.org: Depends: openoffice.org-core (= [COLOR="Red"]1:2.4.1-3~bpo40+1[/COLOR]) but it is not going to be installed
```

Then note that 1:2.4.1-3~bpo40+1 is the version offered by etch-backports, not hardy.
```

openoffice.org-core:
  Installed: (none)
  Candidate: 1:2.4.1-3~bpo40+1
  Version table:
     [COLOR="Red"]1:2.4.1-3~bpo40+1[/COLOR] 0
        500 http://www.backports.org [COLOR="Red"]etch-backports[/COLOR]/main Packages
     1:2.4.1-1ubuntu2 0
        500 http://in.archive.ubuntu.com hardy-updates/main Packages
        100 /var/lib/dpkg/status
     1:2.4.0-3ubuntu6 0
        500 http://in.archive.ubuntu.com hardy/main Packages
        500 http://us.archive.ubuntu.com hardy/main Packages

```
It looks to me that you should turn off etch-backports. 
I think there is a way to turn off repositories by going to System>Administration>Software Sources.

After turning off etch-backports, run
```
sudo apt-get update
``` to refresh your APT system's view of available packages. Then try reinstalling openoffice.org.

---

### Post by imgkg on 2008-08-21
oh thank you so much its working i disabled "http://www.backports.org etch-backports" as you said and ran ```
sudo apt-get update
sudo apt-get install openoffice.org # all needed dependencies will be drawn in
``` its going to get installed now i guess will take like 1 hr to download all that and install will let you know when its done but i guess its working thank you everyone, anyways one question what is this "etch-backports"

---

### Post by imgkg on 2008-08-21
one mentioned by forestpixie is also good method

---

### Post by forger on 2008-08-21
Be sure to reinstall the -desktop package, there might be packages you have removed that perhaps you'll need afterwards
if you have ubuntu:
```
sudo apt-get install ubuntu-desktop
```

or if you have kubuntu:
```
sudo apt-get install kubuntu-desktop
```

P.S. the apt-get update command I asked a while back would show the "bad" deb source :P

---

### Post by ByteJuggler on 2008-08-21
> **imgkg said:**
>  anyways one question what is this "etch-backports"

"Etch-backports" is [Debian Linux]("http://www.debian.org/")'s "backports" repository.  As you probably know, Ubuntu is based on Debian, but the 2 are distinct operating systems with their own repositories etc.  Sometimes it's possible to use a repository intended for Debian with Ubuntu, but sometimes doing so will cause problems due to dependencies which would be satisfied on a Debian system but isn't on Ubuntu etc.  Something like this happened on your system, which is what caused your Open office problems.  By removing the Debian Etch repository from your sources list, you've then forced your packages to install totally from Ubuntu repositories, hence you had no further dependency problems.

---

### Post by imgkg on 2008-08-21
thanks to everyone i am gonna summerize it before marking this thread as solved either you can download tar file from [open office ]("http://download.openoffice.org/") and follow the instructions given [here]("http://news.softpedia.com/news/Install-OpenOffice-org-2-1-in-Ubuntu-Kubuntu-46182.shtml") 
 or
you can download from [here]("http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.4.1") and follow the instructions given [here]("http://ubuntuforums.org/showpost.php?p=5616155&postcount=2")
 or follow the instructions given by "unutbu" in this post:guitar:

---

### Post by Kyle1981 on 2008-08-21
I think you should use a .deb ball not a .tar ball. you must know ubuntu is a debian system, not other system

---

### Post by tarps87 on 2008-08-21
.tar is a compressed file, like a .rar or .zip The file inside the .tar is a deb file, so a bit like openoffice.deb.tar

---

