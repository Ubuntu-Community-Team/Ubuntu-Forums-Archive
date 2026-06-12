---
title: "trying to upgrade ... unmet dependencies"
date: 2019-04-18
forum: New to Ubuntu
---

### Post by rrlangly2 on 2019-04-18
I'm trying to run the following command in order to upgrade from 16.04 to 18.04.

    $ sudo apt upgrade 
    

I did run 'sudo apt update' before.

Now I get the following error ...

```
$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 python3-aptdaemon.pkcompat : Conflicts: packagekit
                              Conflicts: packagekit:i386
E: Broken packages
```

Another way I try is ... I have a red circle with a line through it in the task bar. If I click on it, the software updater comes up and I click "show updates". There's nothing to install or remove, but it says 1959.4MB will be downloaded. I click "install now" and I get the following error.

```

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
Transaction failed: Package dependencies cannot be resolved
 The following packages have unmet dependencies:

libpython2.7-stdlib: Depends: libpython2.7-minimal (= 2.7.15~rc1-1ubuntu0.1) but 2.7.15~rc1-1ubuntu0.1 is to be installed
                     Depends: libc6 (>= 2.15) but 2.27-3ubuntu1 is to be installed
                     Depends: libffi6 (>= 3.0.4) but 3.2.1-8 is to be installed
                     Depends: libncursesw5 (>= 6) but 6.1-1ubuntu1.18.04 is to be installed
                     Depends: libreadline7 (>= 7.0~beta) but 7.0-3 is to be installed
                     Depends: libsqlite3-0 (>= 3.5.9) but 3.22.0-1 is to be installed
                     Depends: libtinfo5 (>= 6) but 6.1-1ubuntu1.18.04 is to be installed

```

Thanks for any help.

---

### Post by thetechkid on 2019-04-18
have you tried ```
do-release-upgrade
```?

---

### Post by rrlangly2 on 2019-04-18
I get the following:

```
$ do-release-upgrade 
Checking for a new Ubuntu release
No new release found.

```

---

### Post by Bashing-om on 2019-04-18
rrlangly2; Hummm ...

Looks to me like you are now on release 18.04, from the outputs versions of the libs.

confirm 18.04:
```

uname -r
lsb_release -a
cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

then we look at the failure, starting with:
```

apt policy libpython2.7-stdlib libpython2.7-minimal libc6 libffi6 libncursesw5 libreadline7 libsqlite3-0 libtinfo5

```

see where this points us to.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by rrlangly2 on 2019-04-18
Whoa! You're right, it's 18.04. Problem is, my desktop is all screwed up. I don't have the menu bar, nor can I seem to get one.

So I ran 'apt update', then 'apt upgrade', and I get this ...
```

 $ sudo apt upgrade                                              

 Reading package lists... Done                                                  

 Building dependency tree                                                       

 Reading state information... Done                                              

 Calculating upgrade... Done                                                    

 Some packages could not be installed. This may mean that you have

 requested an impossible situation or if you are using the unstable

 distribution that some required packages have not yet been created

 or been moved out of Incoming.

 The following information may help to resolve the situation:

  

 The following packages have unmet dependencies:

  python3-aptdaemon.pkcompat : Conflicts: packagekit

                               Conflicts: packagekit:i386

 E: Broken packages
```


Any thoughts on what I should do next?

---

### Post by Bashing-om on 2019-04-18
rrlangly2; well ,,, 

what results:
```

sudo apt update
sudo apt full-upgrade
sudo apt -f install
sudo dpkg -C

```
Make sure here that the package manager is in a happy happy state,

then see what the GUI is up to.

[INDENT][INDENT]make a firm foundation, and then push
[/INDENT][/INDENT]

---

### Post by rrlangly2 on 2019-04-18
When doing 'full-upgrade', I get the following:
```

$ sudo apt full-upgrade                                         
Reading package lists... Done                                                  
Building dependency tree                                                       
Reading state information... Done                                              
Calculating upgrade... Error!                                                  
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 dpkg-dev : Breaks: debhelper (< 10.10.1~) but 9.20160115ubuntu3 is to be installed
            Breaks: debhelper:i386 (< 10.10.1~)
 libpython2.7-stdlib : Breaks: python-scipy (< 0.18.1-2ubuntu3) but 0.17.0-1 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

---

### Post by Bashing-om on 2019-04-18
rrlangly2; Well - not -

What shows:
```

apt policy dpkg-dev debhelper libpython2.7-stdlib python-scipy

```

Looking as got to be a reason

---

### Post by rrlangly2 on 2019-04-18
```

 $ sudo apt policy dpkg-dev debhelper libpython2.7-stdlib python-scipy                                                                           
dpkg-dev:                                                                      
  Installed: 1.18.4ubuntu1.5
  Candidate: 1.19.0.5ubuntu2.1
  Version table:
     1.19.0.5ubuntu2.1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages
     1.19.0.5ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu bionic/main i386 Packages
 *** 1.18.4ubuntu1.5 100
        100 /var/lib/dpkg/status
debhelper:
  Installed: 9.20160115ubuntu3
  Candidate: 11.1.6ubuntu2
  Version table:
     11.1.6ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages
     11.1.6ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu bionic/main i386 Packages
 *** 9.20160115ubuntu3 100
        100 /var/lib/dpkg/status
libpython2.7-stdlib:
  Installed: 2.7.12-1ubuntu0~16.04.4
  Candidate: 2.7.15~rc1-1ubuntu0.1
  Version table:
     2.7.15~rc1-1ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages
     2.7.15~rc1-1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
 *** 2.7.12-1ubuntu0~16.04.4 100
        100 /var/lib/dpkg/status
python-scipy:
  Installed: 0.17.0-1
  Candidate: 0.19.1-2ubuntu1
  Version table:
     0.19.1-2ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
 *** 0.17.0-1 100
        100 /var/lib/dpkg/status                     

```

---

### Post by Bashing-om on 2019-04-18
rrlangly2; Uh huh //

Do not know the why but /var/lib/dpkg/status file contains stale info. a couple of ways we can approach this - edit the file and regenerate with current info - ouch !
or 
try and remove the stubborn packages that are stuck on 16.04. As both are "optional", how about we purge them from the system as a better course ?

```

sudo apt remove --purge dpkg-dev libpython2.7-stdlib
sudo apt update
sudo apt full-upgrade

```


Now, can we move on ?

[INDENT]maybe yes
[/INDENT]

---

### Post by rrlangly2 on 2019-04-18
I did that and now get the following ...
```

 $ sudo apt remove --purge dpkg-dev libpython2.7-stdlib
Reading package lists... Done                                                  
Building dependency tree                                                       
Reading state information... Done                                              
Some packages could not be installed. This may mean that you have              
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnupg : Breaks: software-properties-common (<= 0.96.24.3) but 0.96.20.8 is to be installed
 libboost-iostreams-dev : Depends: libboost-iostreams1.58-dev but it is not going to be installed
 libboost-regex-dev : Depends: libboost-regex1.58-dev but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

---

### Post by Bashing-om on 2019-04-18
rrlangly2 -

Pandora's box ?

What does :
```

sudo apt install --reinstall gnupg

```
reveal.

[INDENT][INDENT]how deep is the water, papa [/INDENT][/INDENT]

---

### Post by #&amp;thj^% on 2019-04-18
if Bashing-om's suggestion dose not yield results, show us this also:
Looks like something went wonky with these packages below;
```
apt-cache policy gnupg
apt-cache policy libboost-iostreams1.58-dev
apt-cache policy libboost-regex1.58-dev 
```

---

### Post by rrlangly2 on 2019-04-18
Thanks guys, it's all correct now.

---

### Post by #&amp;thj^% on 2019-04-18
Bashing-om did ALL the heavy lifting.
But as the old saying goes "All's Well that Ends Well"

---

### Post by Bashing-om on 2019-04-19
rrlangly2; Great :)

> 
Thanks guys, it's all correct now.


If this matter is now concluded to your satisfaction:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

