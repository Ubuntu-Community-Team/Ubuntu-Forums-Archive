---
title: "Screwed up my computer trying to download Sun-Java6-JDK need help!"
date: 2012-02-12
forum: New to Ubuntu
---

### Post by DrVini42 on 2012-02-12
After failing at downloading Sun-Java6 through the terminal I tried to download openJDK6 on Ubuntu Software Center. Now I receive a pop-up that says:
 
"There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks."

Detail: 

"Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the sun-java6-jre package. This might mean you need to manually fix this package."

Please help! I am a beginner.

---

### Post by androssofer on 2012-02-12
> **DrVini42 said:**
> After failing at downloading Sun-Java6 through the terminal I tried to download openJDK6 on Ubuntu Software Center. Now I receive a pop-up that says:
 
"There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks."

Detail: 

"Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the sun-java6-jre package. This might mean you need to manually fix this package."

Please help! I am a beginner.

open synaptec package manager, then search for openjdk, right click and select 'mark for complete removal', then try installing it again...

---

### Post by DrVini42 on 2012-02-12
> **androssofer said:**
> open synaptec package manager, then search for openjdk, right click and select 'mark for complete removal', then try installing it again...

I don't have synaptec package manager. Can you tell me how to do it through the terminal?

---

### Post by mastablasta on 2012-02-12
synaptic was removed in 11.10, btu you can install it from software center.

otherwise you will need to use purge command, though i guess it's safer to do it with synaptic if you are not good with commands.

---

### Post by DrVini42 on 2012-02-12
> **mastablasta said:**
> synaptic was removed in 11.10, btu you can install it from software center.

otherwise you will need to use purge command, though i guess it's safer to do it with synaptic if you are not good with commands.

Due to my current technical issue, I am unable to download anything from the software center.

---

### Post by drdos2006 on 2012-02-12
The command to purge the files would be:

sudo apt-get purge  openjdk-6-jre  openjdk-6-jre-headless openjdk-6-jre-lib openjdk-6-doc openjdk-6-jdk

You might also have default-jre and default-jdk, therefore try:

sudo apt-get purge default-jre  default-jdk  default-jre-headless  default-jre-doc

Icedtea-6-jre-cacao is associated with Firefox so I do not think I would remove iced tea.


regards

---

### Post by DrVini42 on 2012-02-12
> **drdos2006 said:**
> The command to purge the files would be:

sudo apt-get purge  openjdk-6-jre  openjdk-6-jre-headless openjdk-6-jre-lib openjdk-6-doc openjdk-6-jdk

You might also have default-jre and default-jdk, therefore try:

sudo apt-get purge default-jre  default-jdk  default-jre-headless  default-jre-doc

Icedtea-6-jre-cacao is associated with Firefox so I do not think I would remove iced tea.


regards

I typed all that in. The terminal was unable to locate openjdk-jre-headless and default-jre-doc. I still get the same error when I try to download something on Software Center.

---

### Post by drdos2006 on 2012-02-12
Try :
sudo apt-get install synaptic

regards

---

### Post by matt_symes on 2012-02-12
Hi

> pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the **sun-java6-jre** package. 
This might mean you need to manually fix this package."

Try to purge sun-java as that is giving you the error.

Copy and paste the command below into a terminal (including the last *) and enter your password

```
sudo apt-get remove --purge sun-java*
```

Kind regards

---

### Post by DrVini42 on 2012-02-12
> **drdos2006 said:**
> Try :
sudo apt-get install synaptic

regards

No luck. It says it's missing dependencies: sun-java6-bin and libept1

---

### Post by DrVini42 on 2012-02-12
> **matt_symes said:**
> Hi



Try to purge sun-java as that is giving you the error.

Copy and paste the command below into a terminal (including the last *) and enter your password

```
sudo apt-get remove --purge sun-java*
```

Kind regards

I did that and it said:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'sun-java6-jre' for regex 'sun-java*'
Note, selecting 'sun-java5-jre' for regex 'sun-java*'
Note, selecting 'sun-java6-fonts' for regex 'sun-java*'
Note, selecting 'sun-java6-jdk' for regex 'sun-java*'
Note, selecting 'sun-javadb-client' for regex 'sun-java*'
Note, selecting 'sun-javadb-common' for regex 'sun-java*'
Note, selecting 'sun-javadb-core' for regex 'sun-java*'
Note, selecting 'sun-javadb-doc' for regex 'sun-java*'
Note, selecting 'sun-javadb-javadoc' for regex 'sun-java*'
Note, selecting 'sun-javadb-demo' for regex 'sun-java*'
Note, selecting 'sun-java6-bin' for regex 'sun-java*'
Note, selecting 'sun-java6-plugin' for regex 'sun-java*'
Note, selecting 'sun-java6-demo' for regex 'sun-java*'
Note, selecting 'sun-java6-source' for regex 'sun-java*'
Note, selecting 'ia32-sun-java6-bin' for regex 'sun-java*'
Note, selecting 'ia32-sun-java6-plugin' for regex 'sun-java*'
Note, selecting 'sun-java6-src' for regex 'sun-java*'
Note, selecting 'sun-java6-javadb' for regex 'sun-java*'
Package sun-javadb-client is not installed, so not removed
Package sun-javadb-common is not installed, so not removed
Package sun-javadb-core is not installed, so not removed
Package sun-javadb-demo is not installed, so not removed
Package sun-javadb-doc is not installed, so not removed
Package sun-javadb-javadoc is not installed, so not removed
Package sun-java6-bin is not installed, so not removed
Package sun-java6-plugin is not installed, so not removed
Package sun-java6-jdk is not installed, so not removed
Package sun-java6-demo is not installed, so not removed
Package sun-java6-fonts is not installed, so not removed
Package sun-java6-source is not installed, so not removed
Package sun-java6-javadb is not installed, so not removed
The following packages were automatically installed and are no longer required:
  openjdk-7-jre-headless wine1.3-gecko ttf-dejavu-extra java-common
  openjdk-6-jre-headless tzdata-java openjdk-6-jre-lib default-jre-headless
  ca-certificates-java openjdk-7-jre-lib
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  sun-java6-jre*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: error processing sun-java6-jre (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 sun-java6-jre
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by matt_symes on 2012-02-12
Hi

> Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.

Lets follow the advice then

```
sudo apt-get install --reinstall sun-java6-jre
```

If it installs correctly then uninstall as before if required.

BTW: To auto remove the packages no longer required then

```
sudo apt-get autoremove
```

Kind regards

---

### Post by QIII on 2012-02-12
The Sun Java in the repos, if you can still find it, is dangerously out of date.  Furthermore, there will be no updates because Oracle has withdrawn licenses for having it in various distributions' repositories.

If Sun Java is needed (which it may be because OpenJDK is NOT universally recognized by the world at large) then, again, I recommend the following:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

I strongly recommend AGAINST using what is in the repos because it is out of date and has security issues that have been fixed in more recent updates.  If you install it to get around the instability you are encountering, uninstall it immediately thereafter.

---

### Post by DrVini42 on 2012-02-12
> **matt_symes said:**
> Hi



Lets follow the advice then

```
sudo apt-get install --reinstall sun-java6-jre
```

If it installs correctly then uninstall as before if required.

BTW: To auto remove the packages no longer required then

```
sudo apt-get autoremove
```

Kind regards

I tried to "reinstall":

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 sun-java6-jre : Depends: sun-java6-bin (>= 6.26-2lucid1) but it is not going to be installed or
                          ia32-sun-java6-bin (>= 6.26-2lucid1) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by QIII on 2012-02-13
Try to install the dependency first:

```
sudo apt-get install --reinstall sun-java6-bin sun-java6-jre
```

That error is telling you that the jre cannot be installed because the bin is not present or not going to be installed.

If that doesn't work, try to do what is suggested in the last sentence of the advice given in the terminal.

---

### Post by DrVini42 on 2012-02-13
Today when I turned on my computer Sun Java6 JRE was listed in the Update Manager and downloaded successfully. I proceeded to successfully download Synaptic Package Manager from Software Center. It seems this problem sorted itself out even though restarting the machine didn't solve anything yesterday. Thank you so much to everyone who offered their wisdom. I'll stay far away from the terminal from now on ;)

---

