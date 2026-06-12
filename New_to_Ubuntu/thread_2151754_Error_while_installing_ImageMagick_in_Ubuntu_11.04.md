---
title: "Error while installing ImageMagick in Ubuntu 11.04"
date: 2013-06-05
forum: New to Ubuntu
---

### Post by cspc on 2013-06-05
[COLOR=#757575][FONT=Arial]While running  "sudo apt-get install imagemagick" in my Ubuntu 11.04[/FONT][/COLOR]
[COLOR=#757575][FONT=Arial]It tends to install the following packages: [/FONT][/COLOR]
[COLOR=#757575][FONT=Arial]"libcdt4 libgraph4 libgvc5 liblqr-1-0 libmagickcore3 libmagickcore3-extra[/FONT][/COLOR]
[COLOR=#757575][FONT=Arial]libmagickwand3 libnetpbm10 libpathplan4 netpbm[/FONT][/COLOR][COLOR=#757575][FONT=Arial]"[/FONT][/COLOR]
[COLOR=#757575][FONT=Arial]After authentication none of the packages where installed and it throws [/FONT][/COLOR]
[COLOR=#757575][FONT=Arial]"Err [/FONT][/COLOR][http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)[COLOR=#757575][FONT=Arial] natty-updates/main libmagickcore3 i386 7:6.6.2.6-1ubuntu4.2[/FONT][/COLOR]
[COLOR=#757575][FONT=Arial]404 Not Found [IP: 91.189.91.13 80][/FONT][/COLOR][COLOR=#757575][FONT=Arial]" for all packages. [/FONT][/COLOR]
[COLOR=#757575][FONT=Arial]Since my Ubuntu version is not supported by Ubuntu they removed all their package repositories and so i get this error. 

My question is that whether can i find those packages any where on the web so that i can manually download it and put on my server?
[/FONT][/COLOR]

[COLOR=#757575][FONT=Arial]Kindly help me with the answer..[/FONT][/COLOR]

[COLOR=#757575][FONT=Arial]Thanks in advance[/FONT][/COLOR]

---

### Post by deadflowr on 2013-06-05
It's more common than one would think.
Look at this on how to change the repos to point to the old release repos.
[http://superuser.com/questions/339537/where-can-i-get-therepositories-for-old-ubuntu-versions](http://superuser.com/questions/339537/where-can-i-get-therepositories-for-old-ubuntu-versions)
Note, the packages in these repos get absolutely no support and any bugs or problems will not be dealt with.

---

### Post by cspc on 2013-06-08
Thanks. Yeah that helps.
I did that but out eight packages that weren't previously installed, i got four of them installed now.
And finally it shows:
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty/main libcdt4 i386 2.26.3-5ubuntu1
  404  Not Found [IP: 91.189.92.156 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty/main libgraph4 i386 2.26.3-5ubuntu1
  404  Not Found [IP: 91.189.92.156 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty/main libpathplan4 i386 2.26.3-5ubuntu1
  404  Not Found [IP: 91.189.92.156 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty/main libgvc5 i386 2.26.3-5ubuntu1
  404  Not Found [IP: 91.189.92.156 80]

Can you figure out from where these packages can be fetched now?

---

### Post by deadflowr on 2013-06-08
What is the output of

```
cat /etc/apt/sources.list
```

---

### Post by cspc on 2013-06-08
This was the output:

prem@cspc:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb [http://old-releases.ubuntu.com/ubuntu/natty](http://old-releases.ubuntu.com/ubuntu/natty) main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/natty](http://old-releases.ubuntu.com/ubuntu/natty) main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) natty-updates main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) natty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) natty-security main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) natty-security main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

---

### Post by deadflowr on 2013-06-08
You need to comment out every line that is not an old-release line.
So this (as an example)
```
[COLOR=#000000]deb [/COLOR][http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)[COLOR=#000000] natty-security main restricted[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)[COLOR=#000000] natty-security main restricted[/COLOR]
[COLOR=#000000]deb [/COLOR][http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)[COLOR=#000000] natty-security universe[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)[COLOR=#000000] natty-security universe[/COLOR]
[COLOR=#000000]deb [/COLOR][http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)[COLOR=#000000] natty-security multiverse[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)[COLOR=#000000] natty-security multiverse[/COLOR]
```

Should look like this
```
#[COLOR=#000000]deb [/COLOR][http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)[COLOR=#000000] natty-security main restricted[/COLOR]
[COLOR=#000000]#deb-src [/COLOR][http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)[COLOR=#000000] natty-security main restricted[/COLOR]
[COLOR=#000000]#deb [/COLOR][http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)[COLOR=#000000] natty-security universe[/COLOR]
[COLOR=#000000]#deb-src [/COLOR][http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)[COLOR=#000000] natty-security universe[/COLOR]
[COLOR=#000000]#deb [/COLOR][http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)[COLOR=#000000] natty-security multiverse[/COLOR]
[COLOR=#000000]#deb-src [/COLOR][http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)[COLOR=#000000] natty-security multiverse[/COLOR]
```

Open your favorite text editor as root to edit the file
```
gksu gedit /etc/apt/sources.list
```
(as an example)

The reason to comment these lines out is because they don't exist anywhere, anymore.
Only the repos in the old-releases.

After saving the newly edited file. run
```
sudo apt-get update
```
Then try to install the packages.

---

### Post by cspc on 2013-06-08
I commented out all those and tried "sudo apt-get update" but even then some fails:

output:
> 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main InRelease                              
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-updates InRelease
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-security InRelease          
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports InRelease         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main Release.gpg
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release     
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-updates Release.gpg
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-security Release.gpg
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports Release.gpg
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-updates Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-security Release             
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports Release            
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/multiverse TranslationIndex   
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/restricted TranslationIndex
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/universe TranslationIndex
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-updates/main Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-updates/restricted Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-updates/universe Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-updates/multiverse Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-updates/main i386 Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-updates/restricted i386 Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-updates/universe i386 Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-updates/multiverse i386 Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-updates/main TranslationIndex
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-updates/universe TranslationIndex
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-security/main Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-security/restricted Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-security/universe Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-security/multiverse Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-security/main i386 Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-security/restricted i386 Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-security/universe i386 Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-security/multiverse i386 Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-security/main TranslationIndex
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-security/multiverse TranslationIndex
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-security/restricted TranslationIndex
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-security/universe TranslationIndex
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/main Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/restricted Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/universe Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/multiverse Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/main i386 Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/restricted i386 Packages
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources
  404  Not Found
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/universe i386 Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/multiverse i386 Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/main TranslationIndex
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages
  404  Not Found
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/multiverse TranslationIndex
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/restricted TranslationIndex
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/universe TranslationIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_IN
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/restricted Sources
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/universe Sources
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/multiverse Sources
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/restricted i386 Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/universe i386 Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/multiverse i386 Packages
  404  Not Found
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/multiverse Translation-en_IN
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/multiverse Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/restricted Translation-en_IN
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/restricted Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/universe Translation-en_IN
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/universe Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-updates/main Translation-en_IN
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-updates/main Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-updates/multiverse Translation-en_IN
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-updates/restricted Translation-en_IN
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-updates/universe Translation-en_IN
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-updates/universe Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-security/main Translation-en_IN
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-security/main Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-security/multiverse Translation-en_IN
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-security/restricted Translation-en_IN
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-security/restricted Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-security/universe Translation-en_IN
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-security/universe Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/main Translation-en_IN
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/main Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/multiverse Translation-en_IN
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/multiverse Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/restricted Translation-en_IN
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/restricted Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/universe Translation-en_IN
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) natty-backports/universe Translation-en
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources)  404  Not Found


W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/natty/dists/main/restricted/source/Sources](http://old-releases.ubuntu.com/ubuntu/natty/dists/main/restricted/source/Sources)  404  Not Found


W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/natty/dists/main/universe/source/Sources](http://old-releases.ubuntu.com/ubuntu/natty/dists/main/universe/source/Sources)  404  Not Found


W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/natty/dists/main/multiverse/source/Sources](http://old-releases.ubuntu.com/ubuntu/natty/dists/main/multiverse/source/Sources)  404  Not Found


W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/natty/dists/main/restricted/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/natty/dists/main/restricted/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/natty/dists/main/universe/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/natty/dists/main/universe/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/natty/dists/main/multiverse/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/natty/dists/main/multiverse/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.




and when i tried to install my package it told:

> 
prem@cspc:~$ sudo apt-get install imagemagick
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 imagemagick : Depends: liblqr-1-0 (>= 0.1.0) but it is not installable
               Depends: libmagickcore3 (>= 7:6.6.2.6) but it is not going to be installed
               Depends: libmagickwand3 (>= 7:6.6.2.6) but it is not going to be installed
               Recommends: libmagickcore3-extra but it is not going to be installed
               Recommends: netpbm but it is not installable
E: Broken packages


---

### Post by deadflowr on 2013-06-08
You need to also comment out the extras.ubuntu.com lines.

As far as the sources errors, not much I can help with that except maybe try running
```
sudo apt-get clean
```
Which will clear the package listings you have, then run sudo apt-get update again.

---

### Post by cspc on 2013-06-09
Thanks deadflowr.
Your are so down to earth, i will try running my software in any of the new releases.
Thanks for the info you provided me.

---

### Post by cspc on 2013-06-14
Is there any possibility of some one(third-party) having all ubuntu 11.04 packages in their server/Hard drive?
 if so from where can i get it....?
please help.

---

### Post by howefield on 2013-06-14
> **cspc said:**
> "libcdt4 libgraph4 libgvc5 liblqr-1-0 libmagickcore3 libmagickcore3-extra libmagickwand3 libnetpbm10 libpathplan4 netpbm. 

My question is that whether can i find those packages any where on the web so that i can manually download it and put on my server?

Try searching your favourite search engine for each package eg..

```
libcdt4 ubuntu 11.04 
```

will get you the following link which will likely contain the other packages also..

[http://www.ubuntuupdates.org/package/super_os/natty/main/base/libcdt4](http://www.ubuntuupdates.org/package/super_os/natty/main/base/libcdt4)

---

### Post by cspc on 2013-06-14
yeah me too did the same ...
I went to ubuntuupdates.org and downloaded it...
And then i installed the packages using [COLOR=#333333][FONT=UbuntuMono]sudo dpkg -i[/FONT][/COLOR] command...
while installing one particular package it shows dependency on other.
so i went on doing that, in the meantime some packages for ubuntu11.04 hasbeen removed from the ubuntuupdates.org itself thus forcing me to use ubuntu11.10 packages
and likewise it goes like a chain with almost a never ending process.

so only i'm looking for a kinda repository that contains all ubuntu 11.04 packages.

Any solution for this?

Thanks.

---

### Post by cspc on 2013-06-17
Does any other method exists to do this?

---

