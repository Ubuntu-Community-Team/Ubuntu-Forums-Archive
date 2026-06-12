---
title: "Apt-Get broken, can't install anything"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by dvddecrypter on 2008-07-07
I wanted some software that was only available at:

deb [http://debian.lcs.mit.edu/debian](http://debian.lcs.mit.edu/debian) lenny main

so I added it to my sources list. To the best of my knowledge that's when bad things started happening with APT.  I can't install anything, it seems that versions do not match up EG Pidgin:

```

fzero@ubuntu:~$ sudo apt-get install pidgin
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
  pidgin: Depends: libpurple0 (>= 1:2.4.1-1ubuntu2.1) but it is not going to be installed
          Depends: perlapi-5.8.8
E: Broken packages
fzero@ubuntu:~$ sudo apt-get install libpur
libpurelibc0      libpurelibc1      libpurple0        libpurple-dev
libpurelibc0-dev  libpurelibc-dev   libpurple-bin     
fzero@ubuntu:~$ sudo apt-get install libpurple0
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
  libpurple0: Depends: libperl5.8 (>= 5.8.8) but it is not going to be installed
              Depends: perlapi-5.8.8
E: Broken packages
fzero@ubuntu:~$ sudo apt-get install libperl5.8
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
  libperl5.8: Depends: perl-base (= 5.8.8-12) but 5.10.0-11 is to be installed
E: Broken packages
fzero@ubuntu:~$ sudo apt-get install perl-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
perl-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 815 not upgraded.
fzero@ubuntu:~$ sudo apt-cache policy perl-base
perl-base:
  Installed: 5.10.0-11
  Candidate: 5.10.0-11
  Version table:
 *** 5.10.0-11 0
        500 http://debian.lcs.mit.edu lenny/main Packages
        100 /var/lib/dpkg/status
     5.8.8-12 0
        500 http://us.archive.ubuntu.com hardy/main Packages


```

Whoops?  Everything I install seems to have these problems.  Can I recover from this?

---

### Post by billgoldberg on 2008-07-07
Remove the repository and do "sudo apt-get update".

Then try to install something and see if it works.

---

### Post by Foster Grant on 2008-07-07
Since your problems started when you added the Debian repository, try taking it off your sources list. You're not using Debian; you're using Ubuntu, which has its own development team and software repository. Yes, Ubuntu is based on Debian, but that doesn't mean it's the same thing.

And I doubt that the software you're looking for is "only available at Debian." Have you checked out [GetDeb.net](http://www.getdeb.net/)?

---

### Post by dvddecrypter on 2008-07-07
Same problems, I think the problem is that I have NEWER software installed than the requirements.

---

### Post by Kevbert on 2008-07-07
Remove that from your sources.lst and then try
```
sudo apt-get install -f
```
If this doesn't work try replacing apt-get with aptitude:
```
sudo aptitude install -f
```
This should repair any damaged packages.

---

### Post by rogier.de.groot on 2008-07-07
Remove that line from your sources list! Ubuntu is based on debian, and you added the whole debian lenny main repo to your list - conflicts all over the place I'd bet. Remove that line. Do "apt-get update". It'll work again.
BTW, Pidgin is in the regular repos...

---

### Post by dvddecrypter on 2008-07-07
Removed the Deb repository and updated then tried apt which did not work, aptitude dosen't seem to work but has no error message

```
fzero@ubuntu:~$ sudo aptitude install -f pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  libperl5.8 libpurple0 pidgin 
The following NEW packages will be automatically installed:
  libpurple-bin 
The following NEW packages will be installed:
  libpurple-bin 
0 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 2509kB of archives. After unpacking 7680kB will be used.
The following packages have unmet dependencies:
  libpurple0: Depends: perlapi-5.8.8 which is a virtual package.
  libperl5.8: Depends: perl-base (= 5.8.8-12) but 5.10.0-11 is installed.
  pidgin: Depends: perlapi-5.8.8 which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
libperl5.8 [Not Installed]
libpurple0 [Not Installed]
pidgin [Not Installed]

Score is 137

Accept this solution? [Y/n/q/?] Y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
fzero@ubuntu:~$ pidgin
The program 'pidgin' is currently not installed.  You can install it by typing:
sudo apt-get install pidgin

```

Initially I think I was trying to install DVD:RIP

---

### Post by rogier.de.groot on 2008-07-08
Open up synaptic, it has a filter for broken packages, so you can select them and remove them. I think that'll work.

---

### Post by aktiwers on 2008-07-08
Or try:
```
sudo apt-get install -f
sudo dpkg --configure -a 
sudo apt-get autoremove
sudo apt-get upgrade
sudo apt-get update
```One at a time.

---

### Post by aktiwers on 2008-07-08
Or try this:
```
sudo apt-get --reinstall install libperl5.8 && sudo apt-get --reinstall install  libpurple0 && sudo apt-get --reinstall install pidgin 
```

---

