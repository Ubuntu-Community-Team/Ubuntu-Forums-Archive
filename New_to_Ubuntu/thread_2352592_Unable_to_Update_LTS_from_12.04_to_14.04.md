---
title: "Unable to Update LTS from 12.04 to 14.04"
date: 2017-02-13
forum: New to Ubuntu
---

### Post by rothbr on 2017-02-13
Hello Everyone,
I have a group Ubuntu LTS servers that are not upgrading to 14.04. Below are some screenshots of what is happening when I attempt to update.

```
root@Core-Plus-Plainfield:~# sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
Reading package lists... Done
root@Core-Plus-Plainfield:~# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@Core-Plus-Plainfield:~# sudo do-release-upgrade
Checking for a new Ubuntu release
No new release found
root@Core-Plus-Plainfield:~#
```

I have tried doing the "do-release-upgrade" command with the -p and -d tag with no change in outcome. 
I have also tried to rebuild the apt update list with sudo rm -vf /var/lib/apt/lists/* with no changes as well. 

Please let me know if other info is wanted. 

Thanks in advance everyone!

---

### Post by QIII on 2017-02-13
Hello!

Please try doing 

```
sudo apt-get dist-upgrade
```

before trying 

```
do-release-upgrade
```

This will ensure that the kernel is fully upgraded.

---

### Post by deadflowr on 2017-02-13
look in the file /etc/update-manager/release-upgrades
then look at the line prompt=
if it says anything but lts it'll need to be changed to that option.
so
prompt=normal >> needs to be changed to prompt=lts
prompt=never >> needs to be changed to prompt=lts
prompt=lts >> what you want to see, no need to change that

then save and re-run the update commands again.

if that was the problem...

---

### Post by rothbr on 2017-02-15
Hello Q,
I ran the following commands in this order:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
do-release-upgrade and was still given the prompt that states no upgrade is available. 

Checking for a new Ubuntu release
No new release found

---

### Post by rothbr on 2017-02-15
Deadflowr,
I checked the release update as suggested and it is set to pull lts update only.

[DEFAULT]
# Default prompting behavior, valid options:
#
#  never  - Never check for a new release.
#  normal - Check to see if a new release is available.  If more than one new
#           release is found, the release upgrader will attempt to upgrade to
#           the release that immediately succeeds the currently-running
#           release.
#  lts    - Check to see if a new LTS release is available.  The upgrader
#           will attempt to upgrade to the first LTS release available after
#           the currently-running one.  Note that this option should not be
#           used if the currently-running release is not itself an LTS
#           release, since in that case the upgrader won't be able to
#           determine if a newer release is available.
Prompt=lts

---

### Post by ian-weisser on 2017-02-15
@rothbr, your output in Post #1 shows you using 'sudo' at a root prompt. Why?

---

### Post by rothbr on 2017-02-15
Hello Ian,
I have just always done that to ensure the command was done with root authority. Running through the update process without using sudo is not making a difference in the outcome.

---

### Post by deadflowr on 2017-02-15
Perhaps check that you have update-manager-core installed.
And maybe look at it's version:
```
apt-cache policy update-manager-core
```

---

### Post by rothbr on 2017-02-16
Deadflowr,
It looks like update manager is installed.
```
root@Core-Plus-Plainfield:~# apt-cache policy update-manager-core
update-manager-core:
  Installed: 1:0.156.14.21
  Candidate: 1:0.156.14.21
  Version table:
 *** 1:0.156.14.21 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main i386 Packages
        100 /var/lib/dpkg/status
     1:0.156.14.5 0
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main i386 Packages
     1:0.156.14 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main i386 Packages
```

Now, I took a closer look at the upgrade and update process when I found something that might be useful.
When running the ap-get upgrade command I get the following:
```
root@Core-Plus-Plainfield:~# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  bind9-host dnsutils libbind9-80 libdns81 libgc1c2 libisc83 libisccc80
  libisccfg82 liblwres80
9 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,264 kB of archives.
After this operation, 4,096 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main bind9-host i386 1:9.8.1.dfsg.P1-4ubuntu0.21 [54.0 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main dnsutils i386 1:9.8.1.dfsg.P1-4ubuntu0.21 [143 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libisc83 i386 1:9.8.1.dfsg.P1-4ubuntu0.21 [161 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libdns81 i386 1:9.8.1.dfsg.P1-4ubuntu0.21 [707 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libisccc80 i386 1:9.8.1.dfsg.P1-4ubuntu0.21 [18.0 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libisccfg82 i386 1:9.8.1.dfsg.P1-4ubuntu0.21 [40.2 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main liblwres80 i386 1:9.8.1.dfsg.P1-4ubuntu0.21 [38.5 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libbind9-80 i386 1:9.8.1.dfsg.P1-4ubuntu0.21 [24.4 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libgc1c2 i386 1:7.1-8ubuntu0.12.04.3 [77.6 kB]
Fetched 1,264 kB in 4s (302 kB/s)
(Reading database ... 150204 files and directories currently installed.)
Preparing to replace bind9-host 1:9.8.1.dfsg.P1-4ubuntu0.20 (using .../bind9-host_1%3a9.8.1.dfsg.P1-4ubuntu0.21_i386.deb) ...
Unpacking replacement bind9-host ...
Preparing to replace dnsutils 1:9.8.1.dfsg.P1-4ubuntu0.20 (using .../dnsutils_1%3a9.8.1.dfsg.P1-4ubuntu0.21_i386.deb) ...
Unpacking replacement dnsutils ...
Preparing to replace libisc83 1:9.8.1.dfsg.P1-4ubuntu0.20 (using .../libisc83_1%3a9.8.1.dfsg.P1-4ubuntu0.21_i386.deb) ...
Unpacking replacement libisc83 ...
Preparing to replace libdns81 1:9.8.1.dfsg.P1-4ubuntu0.20 (using .../libdns81_1%3a9.8.1.dfsg.P1-4ubuntu0.21_i386.deb) ...
Unpacking replacement libdns81 ...
Preparing to replace libisccc80 1:9.8.1.dfsg.P1-4ubuntu0.20 (using .../libisccc80_1%3a9.8.1.dfsg.P1-4ubuntu0.21_i386.deb) ...
Unpacking replacement libisccc80 ...
Preparing to replace libisccfg82 1:9.8.1.dfsg.P1-4ubuntu0.20 (using .../libisccfg82_1%3a9.8.1.dfsg.P1-4ubuntu0.21_i386.deb) ...
Unpacking replacement libisccfg82 ...
Preparing to replace liblwres80 1:9.8.1.dfsg.P1-4ubuntu0.20 (using .../liblwres80_1%3a9.8.1.dfsg.P1-4ubuntu0.21_i386.deb) ...
Unpacking replacement liblwres80 ...
Preparing to replace libbind9-80 1:9.8.1.dfsg.P1-4ubuntu0.20 (using .../libbind9-80_1%3a9.8.1.dfsg.P1-4ubuntu0.21_i386.deb) ...
Unpacking replacement libbind9-80 ...
Preparing to replace libgc1c2 1:7.1-8ubuntu0.12.04.1 (using .../libgc1c2_1%3a7.1-8ubuntu0.12.04.3_i386.deb) ...
Unpacking replacement libgc1c2 ...
Processing triggers for man-db ...
Setting up libisc83 (1:9.8.1.dfsg.P1-4ubuntu0.21) ...
Setting up libdns81 (1:9.8.1.dfsg.P1-4ubuntu0.21) ...
Setting up libisccc80 (1:9.8.1.dfsg.P1-4ubuntu0.21) ...
Setting up libisccfg82 (1:9.8.1.dfsg.P1-4ubuntu0.21) ...
Setting up libbind9-80 (1:9.8.1.dfsg.P1-4ubuntu0.21) ...
Setting up liblwres80 (1:9.8.1.dfsg.P1-4ubuntu0.21) ...
Setting up bind9-host (1:9.8.1.dfsg.P1-4ubuntu0.21) ...
Setting up dnsutils (1:9.8.1.dfsg.P1-4ubuntu0.21) ...
Setting up libgc1c2 (1:7.1-8ubuntu0.12.04.3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@Core-Plus-Plainfield:~#
```

The line "ldconfig deferred processing now taking place" seems like a potential issue. Could this be related to the release upgrade issue?

---

