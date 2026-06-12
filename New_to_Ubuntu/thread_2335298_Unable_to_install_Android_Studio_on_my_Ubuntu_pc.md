---
title: "Unable to install Android Studio on my Ubuntu pc"
date: 2016-08-27
forum: New to Ubuntu
---

### Post by walterwhite on 2016-08-27
i followed this ppa and getting these errors while installing Android Studio:(

```
user@walter-white:~$ sudo /opt/android-studio
[sudo] password for user: 
sudo: /opt/android-studio: command not found
user@walter-white:~$ clear
```

```
user@walter-white:~$ sudo add-apt-repository ppa:paolorotolo/android-studio
 Automatic builds for Android Studio by Google packaged for Ubuntu.
 More info: [https://launchpad.net/~paolorotolo/+archive/ubuntu/android-studio](https://launchpad.net/~paolorotolo/+archive/ubuntu/android-studio)
Press [ENTER] to continue or ctrl-c to cancel adding it


gpg: keyring `/tmp/tmptfcrwrqv/secring.gpg' created
gpg: keyring `/tmp/tmptfcrwrqv/pubring.gpg' created
gpg: requesting key 7B9B74AA from hkp server keyserver.ubuntu.com
gpg: /tmp/tmptfcrwrqv/trustdb.gpg: trustdb created
gpg: key 7B9B74AA: public key "Launchpad PPA for Paolo Rotolo" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
user@walter-white:~$ sudo apt-get update
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:2 [http://ppa.launchpad.net/notepadqq-team/notepadqq/ubuntu](http://ppa.launchpad.net/notepadqq-team/notepadqq/ubuntu) xenial InRelease
Hit:3 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial InRelease          
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [94.5 kB]
Hit:5 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:6 [http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu](http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu) xenial InRelease
Get:7 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial-updates InRelease [95.7 kB]   
Hit:9 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial-backports InRelease           
Get:10 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [378 kB]
Get:11 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [373 kB]
Fetched 941 kB in 14s (63.9 kB/s)                                              
Reading package lists... Done
user@walter-white:~$ sudo apt-get install android-studio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
android-studio is already the newest version (5.2.1-ubuntu0).
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 android-studio : Depends: java-sdk or
                           oracle-java7-installer but it is not installable or
                           oracle-java8-installer but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
user@walter-white:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
user@walter-white:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  openjdk-9-jdk
Suggested packages:
  openjdk-9-demo openjdk-9-source visualvm
The following NEW packages will be installed:
  openjdk-9-jdk
0 upgraded, 1 newly installed, 0 to remove and 104 not upgraded.
31 not fully installed or removed.
Need to get 0 B/16.6 kB of archives.
After this operation, 58.4 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 178140 files and directories currently installed.)
Preparing to unpack .../openjdk-9-jdk_9~b114-0ubuntu1_amd64.deb ...
Unpacking openjdk-9-jdk:amd64 (9~b114-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/openjdk-9-jdk_9~b114-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/jvm/java-9-openjdk-amd64/include/linux/jawt_md.h', which is also in package openjdk-9-jdk-headless:amd64 9~b114-0ubuntu1
Errors were encountered while processing:
 /var/cache/apt/archives/openjdk-9-jdk_9~b114-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by tchinmai7 on 2016-08-27
It looks like you have an issue with installing openjdk on your device. try installing Oracle Java from this PPA
```

[COLOR=#303336]sudo apt[/COLOR][COLOR=#303336]-[/COLOR][COLOR=#303336]add[/COLOR][COLOR=#303336]-[/COLOR][COLOR=#303336]repository ppa[/COLOR][COLOR=#303336]:[/COLOR][COLOR=#303336]webupd8team[/COLOR][COLOR=#303336]/[/COLOR][COLOR=#303336]java
sudo apt[/COLOR][COLOR=#303336]-[/COLOR][COLOR=#303336]get update
sudo apt[/COLOR][COLOR=#303336]-[/COLOR][COLOR=#303336]get install oracle[/COLOR][COLOR=#303336]-[/COLOR][COLOR=#303336]java8[/COLOR][COLOR=#303336]-[/COLOR][COLOR=#303336]installer[/COLOR]
```
Now try installing android-studio again.

---

### Post by grahammechanical on 2016-08-27
You might have better success using ubuntu-make to install Android Studio. Ubuntu Make will not only install several IDEs but keep then up to date.

[URL="https://wiki.ubuntu.com/ubuntu-make"]https://wiki.ubuntu.com/ubuntu-make
[/URL]
Before going the ubuntu-make way it would be best to purge the PPA that you have already installed.

[URL="http://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them/91660#91660"]http://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them/91660#91660

[/URL]Regards

---

### Post by Bucky Ball on 2016-08-27
You probably missed the instructions for installing it on the [Android Studio page where you downloaded the app here]("https://developer.android.com/studio/install.html").

---

### Post by walterwhite on 2016-08-27
but i have already installed java

---

### Post by mc4man on 2016-08-27
There is a bug with openjdk-9* that doesn't let it all install - 
[https://bugs.launchpad.net/ubuntu/+source/openjdk-9/+bug/1550950](https://bugs.launchpad.net/ubuntu/+source/openjdk-9/+bug/1550950)
No matter as I don't think android-studio will work with the -9 version anyway.

Maybe you should remove the ppa, remove any openjdk-9 packages installed & follow this - 
[http://askubuntu.com/questions/634082/how-to-install-android-studio-on-ubuntu](http://askubuntu.com/questions/634082/how-to-install-android-studio-on-ubuntu)

---

### Post by walterwhite on 2016-08-27
i did what this page says 

```
user@walter-white:~$ sudo apt-get install lib32z1 lib32ncurses5 lib32stdc++6
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 android-studio : Depends: java-sdk or
                           oracle-java7-installer but it is not installable or
                           oracle-java8-installer but it is not installable
 lib32ncurses5 : Depends: lib32tinfo5 (= 6.0+20160213-1ubuntu1) but it is not going to be installed
                 Depends: libc6-i386 (>= 2.4) but it is not going to be installed
 lib32stdc++6 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.2) but 5.4.0-6ubuntu1~16.04.1 is to be installed
                Depends: lib32gcc1 (>= 1:4.2) but it is not going to be installed
                Depends: libc6-i386 (>= 2.18) but it is not going to be installed
 lib32z1 : Depends: libc6-i386 (>= 2.4) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

> **mc4man said:**
> There is a bug with openjdk-9* that doesn't let it all install - 
[https://bugs.launchpad.net/ubuntu/+source/openjdk-9/+bug/1550950](https://bugs.launchpad.net/ubuntu/+source/openjdk-9/+bug/1550950)
No matter as I don't think android-studio will work with the -9 version anyway.

Maybe you should remove the ppa, remove any openjdk-9 packages installed & follow this - 
[http://askubuntu.com/questions/634082/how-to-install-android-studio-on-ubuntu](http://askubuntu.com/questions/634082/how-to-install-android-studio-on-ubuntu)

so you are saying i have to all that again? man there's no other way?

[B]now i did this , and i am getting an error "unable to run mksdcard tool"


[/B][COLOR=#b22222]```
cd /opt
cd android-studio
cd bin
./studio.sh
```[/COLOR]

---

### Post by Geoffrey_Arndt on 2016-08-28
Perhaps thinking outside the box will help (e.g., an alternative program that accomplishes the same thing)

[http://alternativeto.net/](http://alternativeto.net/)

---

### Post by mc4man on 2016-08-28
No clue where you're at with jdk/java/whatever  but you need to resolve this - 
> lib32stdc++6 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.2) but 5.4.0-6ubuntu1~16.04.1 is to be installed
Make sure in Software & Updates  that under the Updates tab that the 1st two are enabled (security, updates). You want gcc-5-base installed/available to install  at 5.4.0-6ubuntu1~16.04.2 .

If you actually need more than lib32stdc++6 installed than one of those packages is now named differently, (blue) as in  - 
```
sudo apt-get install lib32z1 lib32ncurses5 [COLOR="#0000CD"]libbz2-1.0:i386[/COLOR] lib32stdc++6
```

One should also reboot after installing the above libs, then try to run the ./studio.sh command

---

### Post by walterwhite on 2016-08-30
Problem solved guys thank you so much for your support , i just installed Java again (though i still can't figure out why i had to do that if someone could tell me i'll give him a free hug man!) and then all my problems are gone thanks guys you all are so much good for noobs like me :P

---

### Post by Bucky Ball on 2016-08-30
Great news. Please help other noobs and others by marking thread as 'solved', Thread Tools at top of page. Have fun. :)

---

