---
title: "Error: BrokenCount &gt; 0, can't install python-pip"
date: 2018-10-19
forum: New to Ubuntu
---

### Post by angel-cake on 2018-10-19
Hello, this error appeared when i tried to update ubuntu. Ubuntu crashed  and my laptop even failed to boot it up again. When i finally booted up  ubuntu again this error appeared. I didn't mind it until now. I'm  trying to install python-pip but it doesn't let me. This error appears:  You might want to run 'apt --fix-broken install' to correct these. And  then it shows a list of packages that have unmet dependencies.
I don't know what is going on, please help.
I have Ubuntu 18.04.

---

### Post by again? on 2018-10-19
Run
```
sudo apt update 
sudo apt upgrade
```
and post your result using [code blocks]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168").
Have you installed third party repositories?
This will show all enabled repositories.
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list | nl
```

---

### Post by angel-cake on 2018-10-19
hi @guber2 thanks for replying, so here is what i got:
this is for the update command:
```

Hit:1 http://do.archive.ubuntu.com/ubuntu bionic InRelease
Get:2 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]    
Get:3 http://do.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]   
Hit:4 http://ppa.launchpad.net/linuxuprising/java/ubuntu bionic InRelease      
Get:5 https://download.docker.com/linux/ubuntu bionic InRelease [64.4 kB]      
Get:6 http://do.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB] 
Get:7 http://do.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [406 kB]
Get:8 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages [186 kB]
Get:9 http://do.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [366 kB]
Get:10 http://do.archive.ubuntu.com/ubuntu bionic-updates/main Translation-en [152 kB]
Get:11 http://do.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [185 kB]
Get:12 http://security.ubuntu.com/ubuntu bionic-security/main i386 Packages [147 kB]
Get:13 http://do.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 48x48 Icons [41.2 kB]
Get:14 http://do.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons [86.2 kB]
Get:15 http://do.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [560 kB]
Get:16 http://security.ubuntu.com/ubuntu bionic-security/main Translation-en [72.1 kB]
Get:17 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [204 B]
Get:18 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [9,388 B]
Get:19 http://security.ubuntu.com/ubuntu bionic-security/universe DEP-11 48x48 Icons [9,088 B]
Get:20 http://security.ubuntu.com/ubuntu bionic-security/universe DEP-11 64x64 Icons [16.3 kB]
Get:21 http://do.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [565 kB]
Get:22 http://do.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [191 kB]
Get:23 http://do.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 48x48 Icons [187 kB]
Get:24 http://do.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64 Icons [312 kB]
Get:25 http://do.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:26 http://do.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [5,100 B]
Fetched 3,809 kB in 4s (854 kB/s)                                        
Reading package lists... Done
Building dependency tree       
Reading state information... Done
24 packages can be upgraded. Run 'apt list --upgradable' to see them.

```

And this is for the upgrade command:
```

Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:6.0.6) but 1:6.0.3-0ubuntu1 is installed
 libreoffice-pdfimport : Depends: libreoffice-common (= 1:6.0.6-0ubuntu0.18.04.1) but 1:6.0.3-0ubuntu1 is installed
 libreoffice-style-breeze : Depends: libreoffice-common (= 1:6.0.6-0ubuntu0.18.04.1) but 1:6.0.3-0ubuntu1 is installed
 libreoffice-style-galaxy : Depends: libreoffice-common (= 1:6.0.6-0ubuntu0.18.04.1) but 1:6.0.3-0ubuntu1 is installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

---

### Post by again? on 2018-10-20
On my 18.04 install ...
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] apt policy libreoffice-common**
libreoffice-common:
  Installed: 1:6.0.6-0ubuntu0.18.04.1
  Candidate: 1:6.0.6-0ubuntu0.18.04.1
  Version table:
 *** 1:6.0.6-0ubuntu0.18.04.1 500
        500 http://ftp.iinet.net.au/pub/ubuntu bionic-updates/main amd64 Packages
        500 http://ftp.iinet.net.au/pub/ubuntu bionic-updates/main i386 Packages
        100 /var/lib/dpkg/status
     1:6.0.3-0ubuntu1 500
        500 http://ftp.iinet.net.au/pub/ubuntu bionic/main amd64 Packages
        500 http://ftp.iinet.net.au/pub/ubuntu bionic/main i386 Packages
```

Can only offer standard recovery procedure.
```
sudo apt install -f
sudo dpkg --configure -a
sudo apt update && sudo apt full-upgrade
```

---

### Post by angel-cake on 2018-10-20
@guber2, it seems i can't run the
```

sudo apt install -f

```
because some errors appeared
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  ca-certificates-java fonts-dejavu-extra gdebi-core libatk-wrapper-java
  libatk-wrapper-java-jni libgif7
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libreoffice-common libreoffice-style-tango
Suggested packages:
  tango-icon-theme
The following packages will be upgraded:
  libreoffice-common libreoffice-style-tango
2 upgraded, 0 newly installed, 0 to remove and 22 not upgraded.
16 not fully installed or removed.
Need to get 0 B/26.0 MB of archives.
After this operation, 414 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 175591 files and directories currently installed.)
Preparing to unpack .../libreoffice-style-tango_1%3a6.0.6-0ubuntu0.18.04.1_all.deb ...
Unpacking libreoffice-style-tango (1:6.0.6-0ubuntu0.18.04.1) over (1:6.0.3-0ubuntu1) ...
dpkg-deb (subprocess): cannot copy archive member from '/var/cache/apt/archives/libreoffice-style-tango_1%3a6.0.6-0ubuntu0.18.04.1_all.deb' to decompressor pipe: failed to read (Input/output error)
dpkg-deb (subprocess): decompressing archive member: lzma error: unexpected end of input
dpkg-deb: error: <decompress> subprocess returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/libreoffice-style-tango_1%3a6.0.6-0ubuntu0.18.04.1_all.deb (--unpack):
 cannot copy extracted data for './usr/share/libreoffice/share/config/images_tango.zip' to '/usr/share/libreoffice/share/config/images_tango.zip.dpkg-new': unexpected end of file or stream
Preparing to unpack .../libreoffice-common_1%3a6.0.6-0ubuntu0.18.04.1_all.deb ...
Unpacking libreoffice-common (1:6.0.6-0ubuntu0.18.04.1) over (1:6.0.3-0ubuntu1) ...
dpkg-deb (subprocess): cannot copy archive member from '/var/cache/apt/archives/libreoffice-common_1%3a6.0.6-0ubuntu0.18.04.1_all.deb' to decompressor pipe: failed to read (Input/output error)
dpkg-deb (subprocess): decompressing archive member: lzma error: unexpected end of input
dpkg-deb: error: <decompress> subprocess returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/libreoffice-common_1%3a6.0.6-0ubuntu0.18.04.1_all.deb (--unpack):
 cannot copy extracted data for './usr/lib/libreoffice/share/autocorr/acor_en-AU.dat' to '/usr/lib/libreoffice/share/autocorr/acor_en-AU.dat.dpkg-new': unexpected end of file or stream
rmdir: failed to remove '/var/lib/libreoffice/share/prereg/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice/share/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice/program/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice': No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-style-tango_1%3a6.0.6-0ubuntu0.18.04.1_all.deb
 /var/cache/apt/archives/libreoffice-common_1%3a6.0.6-0ubuntu0.18.04.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

thanks for tryiing to help me, last time this happened i had to re-install ubuntu and lost everything, and that's what i'm avoiding

---

### Post by dino99 on 2018-10-20
You probably get that issue due to the java ppa.
Let it active, then install  'ppa-purge', and do:  >  sudo ppa-purge ppa:linuxuprising/java 
This will set back the genuine packages.

---

### Post by again? on 2018-10-21
The java ppa only appears to have an installer in it.
Look in **/etc/apt/sources.list.d** for ppas that may contain extra unwanted packages you may have inadvertently installed.
As dino99 said, a ppa you have previously used must be renabled before using ppa-purge on that ppa.
This will show enabled launchpad repositories in ppa-purge form...
```
for PPA_FILE in $(ls /etc/apt/sources.list.d/*.list); do cat ${PPA_FILE} | egrep -v '^#|^ *$' | grep "ppa.launchpad.net" | cut -d "/" -f4-5; done
```

Couple of links on ppa-purge.
[**How to use ppa-purge**]("https://ubuntuforums.org/showthread.php?t=2264416&p=13224880#post13224880")
[**HOW TO USE A LAUNCHPAD PPA (ADD, REMOVE, PURGE, DISABLE) IN UBUNTU**]("http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html")

---

### Post by Impavidus on 2018-10-21
Besides the usual caution with PPAs (yes, they can cause all kinds of issues with the package manager), I wonder about this:
> **angel-cake said:**
> 
```

Unpacking libreoffice-style-tango (1:6.0.6-0ubuntu0.18.04.1) over (1:6.0.3-0ubuntu1) ...
dpkg-deb (subprocess): cannot copy archive member from '/var/cache/apt/archives/libreoffice-style-tango_1%3a6.0.6-0ubuntu0.18.04.1_all.deb' to decompressor pipe: failed to read (Input/output error)
dpkg-deb (subprocess): decompressing archive member: lzma error: unexpected end of input

```
Unpacking the latest version of libreoffice-style-tango, which is indeed the latest version from the official repositories, results in an I/O error during decompression. Sounds like a corrupt file to me. What do you get from these commands? Showing the output om my own system:```
$ ls -l /var/cache/apt/archives/libreoffice-style-tango_1%3a6.0.6-0ubuntu0.18.04.1_all.deb 
-rw-r--r-- 1 root root 1308456 sep 19 00:23 /var/cache/apt/archives/libreoffice-style-tango_1%3a6.0.6-0ubuntu0.18.04.1_all.deb
$ md5sum /var/cache/apt/archives/libreoffice-style-tango_1%3a6.0.6-0ubuntu0.18.04.1_all.deb 
7d122663f453b612891e19068d6e927d  /var/cache/apt/archives/libreoffice-style-tango_1%3a6.0.6-0ubuntu0.18.04.1_all.deb
```It should show the same output on your system. The most worrying thing is that the files should be checked automatically after download, which suggests that if they are corrupt, it happened after download, while on your hard drive.

---

### Post by angel-cake on 2018-10-24
@impavidus @guber2 @dino99 sorry for not replying soon, i got really frustrated so i asked my dad to help me and he said it was a probem with the hard drive (it may have some bad sectors) so i re-intalled ubuntu but this time i entered the single mode and run the badblocks command to fix the bad sectors. Turns out it had 60 bad sectors. Thanks for taking yout time to help, if the error happens again when i update i'll let you know.

---

### Post by Impavidus on 2018-10-24
Well, that explains the file corruption. If you're satisfied, could you mark this thread as solved?

---

### Post by angel-cake on 2018-10-28
of course

---

