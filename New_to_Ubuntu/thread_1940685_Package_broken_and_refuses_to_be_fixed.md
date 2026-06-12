---
title: "Package broken and refuses to be fixed"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by DisappearingOak on 2012-03-14
I noticed for the last couple of days that Muon Software Center wouldn't install any software properly. The progress bar showed that it was installing but then it would refresh and the package would be listed as not installed. So I tried apt-get through the terminal and when trying to install anything it says that libc6 package is broken with unmet dependencies. I tried the autoremove and '-f install commands but the problem isn't being fixed.

```

oak@oak-GA-880GM-D2H:~$ sudo apt-get install synaptic
[sudo] password for oak: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.13-20ubuntu5)
 libc6:i386 : Depends: libc-bin:i386 (= 2.13-20ubuntu5)
 synaptic : Depends: libvte9 (>= 1:0.24.0) but it is not going to be installed
            Recommends: libgtk2-perl (>= 1:1.130) but it is not going to be installed
            Recommends: rarian-compat but it is not going to be installed
            Recommends: software-properties-gtk but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
oak@oak-GA-880GM-D2H:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libecore1 libeina1 libxcb-image0 libeet1 libept1 libembryo1
  libecore-con1 libecore-fb1 e17-data libc-ares2 libecore-file1
  libembryo-bin libefreet1 libecore-ipc1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc-bin libc6 libc6:i386
Suggested packages:
  glibc-doc glibc-doc:i386 locales:i386
The following NEW packages will be installed:
  libc-bin
The following packages will be upgraded:
  libc6 libc6:i386
2 upgraded, 1 newly installed, 0 to remove and 154 not upgraded.
Need to get 0 B/8,943 kB of archives.
After this operation, 3,441 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Preconfiguring packages ...
dpkg: warning: 'ldconfig' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
oak@oak-GA-880GM-D2H:~$ sudo apt-get install libc6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.13-20ubuntu5.1)
         Breaks: libc6:i386 (!= 2.13-20ubuntu5.1) but 2.13-20ubuntu5 is to be installed
 libc6:i386 : Depends: libc-bin:i386 (= 2.13-20ubuntu5)
              Breaks: libc6 (!= 2.13-20ubuntu5) but 2.13-20ubuntu5.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
oak@oak-GA-880GM-D2H:~$ sudo apt-get install libc-bin libc6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6 : Breaks: libc6:i386 (!= 2.13-20ubuntu5.1) but 2.13-20ubuntu5 is to be installed
 libc6:i386 : Depends: libc-bin:i386 (= 2.13-20ubuntu5)
              Breaks: libc6 (!= 2.13-20ubuntu5) but 2.13-20ubuntu5.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
oak@oak-GA-880GM-D2H:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libecore1 libeina1 libxcb-image0 libeet1 libept1 libembryo1
  libecore-con1 libecore-fb1 e17-data libc-ares2 libecore-file1
  libembryo-bin libefreet1 libecore-ipc1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc-bin libc6 libc6:i386
Suggested packages:
  glibc-doc glibc-doc:i386 locales:i386
The following NEW packages will be installed:
  libc-bin
The following packages will be upgraded:
  libc6 libc6:i386
2 upgraded, 1 newly installed, 0 to remove and 154 not upgraded.
Need to get 0 B/8,943 kB of archives.
After this operation, 3,441 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Preconfiguring packages ...
dpkg: warning: 'ldconfig' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
oak@oak-GA-880GM-D2H:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.13-20ubuntu5)
 libc6:i386 : Depends: libc-bin:i386 (= 2.13-20ubuntu5)
E: Unmet dependencies. Try using -f.
oak@oak-GA-880GM-D2H:~$ sudo apt-get -f autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc-bin libc6 libc6:i386
Suggested packages:
  glibc-doc glibc-doc:i386 locales:i386
The following packages will be REMOVED:
  e17-data libc-ares2 libecore-con1 libecore-fb1 libecore-file1
  libecore-ipc1 libecore1 libeet1 libefreet1 libeina1 libembryo-bin
  libembryo1 libept1 libxcb-image0
The following NEW packages will be installed:
  libc-bin
The following packages will be upgraded:
  libc6 libc6:i386
2 upgraded, 1 newly installed, 14 to remove and 154 not upgraded.
Need to get 0 B/8,943 kB of archives.
After this operation, 4,588 kB disk space will be freed.
Do you want to continue [Y/n]? y
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Preconfiguring packages ...
dpkg: warning: 'ldconfig' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
oak@oak-GA-880GM-D2H:~$ sudo apt-get install libc-bin libc6 libc6:i386Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libecore1 libeina1 libxcb-image0 libeet1 libept1 libembryo1
  libecore-con1 libecore-fb1 e17-data libc-ares2 libecore-file1
  libembryo-bin libefreet1 libecore-ipc1
Use 'apt-get autoremove' to remove them.
Suggested packages:
  glibc-doc glibc-doc:i386 locales:i386
The following NEW packages will be installed:
  libc-bin
The following packages will be upgraded:
  libc6 libc6:i386
2 upgraded, 1 newly installed, 0 to remove and 154 not upgraded.
Need to get 0 B/8,943 kB of archives.
After this operation, 3,441 kB of additional disk space will be used.
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Preconfiguring packages ...
dpkg: warning: 'ldconfig' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
oak@oak-GA-880GM-D2H:~$ 


```

I tried uninstalling libc6 package through muon package manager but nothing happens and it keeps saying Broken.

---

### Post by raja.genupula on 2012-03-14
[http://ubuntuforums.org/archive/index.php/t-1266104.html](http://ubuntuforums.org/archive/index.php/t-1266104.html)

---

