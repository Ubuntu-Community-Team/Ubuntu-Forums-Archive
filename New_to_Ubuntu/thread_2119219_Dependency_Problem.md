---
title: "Dependency Problem"
date: 2013-02-23
forum: New to Ubuntu
---

### Post by prohank on 2013-02-23
Hey guys,
Running into a problem here and as always looking for some support from you guys.
I have a dependency problem and it won't let me install any new programs.
I had reinstalled Ubuntu on the same partition few days back because of some serious problems.And ran Deja vu Backup after re-installation that restored data of the non installed programs too.
So while running sudo apt-get install -f
I get the following errors.
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gstreamer0.10-plugins-ugly libaccess-bridge-java libmjpegtools-1.9 libzbar0
The following packages will be upgraded:
  gstreamer0.10-plugins-ugly libaccess-bridge-java libmjpegtools-1.9 libzbar0
4 upgraded, 0 newly installed, 0 to remove and 86 not upgraded.
7 not fully installed or removed.
Need to get 0 B/1,095 kB of archives.
After this operation, 249 kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of libmjpegtools-1.9:
 libmjpegtools-1.9 depends on libjpeg62 (>= 6b1); however:
  Package libjpeg62 is not installed.
dpkg: error processing libmjpegtools-1.9 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-bad-multiverse:
 gstreamer0.10-plugins-bad-multiverse depends on libmjpegtools-1.9 (>= 1:1.9.0); however:
  Package libmjpegtools-1.9 is not configured yet.
dpkg: error processing gstreamer0.10-plugins-bad-multiverse (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-ugly:
 gstreamer0.10-plugins-ugly depends on libcdio10; however:
  Package libcdio10 is not installed.
dpkg: error processing gstreamer0.10-plugins-ugly (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libaccess-bridge-java:
 libaccess-bridge-java depends on default-jre | openjdk-6-jre | sun-java6-jre; however:
  Package default-jre is not installed.
  Package openjdk-6-jre is not installed.
  Package sun-java6-jre is not installed.
dpkg: error processing libaccess-bridge-java (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libaccess-bridge-java-jni:
 libaccess-bridge-java-jni depends on libaccess-bridge-java (>= 1.26.2-6); however:
  Package libaccess-bridge-java is not configured yet.
dpkg: error processing libaccess-bridge-java-jni (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libzbar0:
 libzbar0 depends on libjpeg62 (>= 6b1); however:
  Package libjpeg62 is not installed.
dpkg: error processing libzbar0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-bad:
 gstreamer0.10-plugins-bad depends on libzbar0 (>= 0.10); however:
  Package libzbar0 is not configured yet.
dpkg: error processing gstreamer0.10-plugins-bad (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libmjpegtools-1.9
 gstreamer0.10-plugins-bad-multiverse
 gstreamer0.10-plugins-ugly
 libaccess-bridge-java
 libaccess-bridge-java-jni
 libzbar0
 gstreamer0.10-plugins-bad
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

To make it short:
 "Errors were encountered while processing:
 libmjpegtools-1.9
 gstreamer0.10-plugins-bad-multiverse
 gstreamer0.10-plugins-ugly
 libaccess-bridge-java
 libaccess-bridge-java-jni
 libzbar0
 gstreamer0.10-plugins-bad
E: Sub-process /usr/bin/dpkg returned an error code (1)"

Done a lot of searching.
May be you guys can help.

---

### Post by tartalo on 2013-02-23
Do you have any unofficial source in your sources.list?

---

### Post by prohank on 2013-02-23
No,I haven't added any sources as of now.

---

### Post by schragge on 2013-02-23
Try
```

sudo apt-get dist-upgrade

```

---

### Post by prohank on 2013-02-25
Nah:(.
That didn't help.Still same error.

---

### Post by cortman on 2013-02-25
Try

```
sudo dpkg --configure -a
```

---

### Post by prohank on 2013-02-25
Nope that didn't work too..:(:(
Can't we remove those packages from the system?
I found one thing that all those errors were because of the packages I installed from  ubuntu restricted extras that was for oneric.
Will this be solved?
What are other options?

---

### Post by cortman on 2013-02-25
> **prohank said:**
> Nope that didn't work too..:(:(
Can't we remove those packages from the system?
I found one thing that all those errors were because of the packages I installed from  ubuntu restricted extras that was for oneric.
Will this be solved?
What are other options?

And you're running (I take it) 12.04 Precise?
Then that's definitely a problem.

There may be a way to fix it but if you've not devoted much time to rebuilding your system yet, I'd say reinstall Ubuntu and don't use backups of the old programs.
What you install in Ubuntu *must* match the version. Otherwise you wind up with dependency problems like you're experiencing.

---

### Post by prohank on 2013-02-25
Yeah I am using precisely what u said.:)
I haven't spend much time on Ubuntu also I am learning the command line along with  college stuff so don't get enough time to do all this.
Can you please say what do u mean by "rebuilding the system"?
I will reinstall it again but as I said those errors were from ubuntu restricted extras and not from the backed up data so will it cause any harm if I restore previous backups,because they contain some important data.
and there was no other option to save the data files.
Thanks for the help.

---

### Post by sandyd on 2013-02-25
Hi, what is the output of
```

sudo apt-get install libjpeg62
```
libjpeg62 doesn't depend on anything so something must be blocking it

---

### Post by cortman on 2013-02-25
> **prohank said:**
> Yeah I am using precisely what u said.:)
I haven't spend much time on Ubuntu also I am learning the command line along with  college stuff so don't get enough time to do all this.
Can you please say what do u mean by "rebuilding the system"?
I will reinstall it again but as I said those errors were from ubuntu restricted extras and not from the backed up data so will it cause any harm if I restore previous backups,because they contain some important data.
and there was no other option to save the data files.
Thanks for the help.

I meant if you haven't put a lot of time into installing new programs, arranging your data, etc., then a reinstall is the easiest.
You should be able to just restore your data, and not the old programs and settings.


> **sandyd said:**
> Hi, what is the output of
```

sudo apt-get install libjpeg62
```
libjpeg62 doesn't depend on anything so something must be blocking it

Is apt going to go through and function in spite of all the package issues? I'm not sure.

---

### Post by schragge on 2013-02-25
IIRC, apt always tries to configure already downloaded and unpacked packages, but
```

sudo apt-get -d install libjpeg62
sudo dpkg -i /var/cache/apt/archives/libjpeg62*.deb

```should work.

---

### Post by prohank on 2013-02-26
> **schragge said:**
> IIRC, apt always tries to configure already downloaded and unpacked packages, but
```

sudo apt-get -d install libjpeg62
sudo dpkg -i /var/cache/apt/archives/libjpeg62*.deb

```should work.

I found no libjpeg62 file at the above directory.Also I found that none of the other dependency files were in there.
So I manually downloaded it and going to report if it solves the problem.
Thanks!

---

### Post by prohank on 2013-02-27
okay guys that did the trick.
Only one problem, I just want it to confirm.
I restored the backups from deja vu  and ran the update(sudo apt-get update) before installing ubuntu-restricted-extras(oneric).
Could that be the cause for dependency problem?
If I had installed it first and then restored the backups and ran the update would it still be a problem?
Because I don't know how many times I would have to reinstall Ubuntu in future and run into trouble again :p.
It would again need downloading the packages which is very time consuming.
Thank you for all the support
:)

---

