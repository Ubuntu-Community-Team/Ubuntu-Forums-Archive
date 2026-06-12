---
title: "Crosstool-NG build error"
date: 2014-04-28
forum: Packaging and Compiling Programs
---

### Post by Elastic_Potential on 2014-04-28
As I'm hoping to build Firefox for ARM (I'm aware that Iceweasel is available for Raspbian), I've installed crosstool-ng following [this guide](http://www.bootc.net/archives/2012/05/26/how-to-build-a-cross-compiler-for-your-raspberry-pi/).  I am past the make && sudo make install part for crosstool-ng itself, and I've added /opt/cross/bin to my $PATH.  However, I've hit a wall when I go to run "ct-ng build"
```

[INFO ]  Performing some trivial sanity checks
[ERROR]  Build failed in step '<none>'
[ERROR]  Error happened in '/opt/cross/lib/ct-ng-1.9.3/scripts/functions' in function 'CT_DoExecLog' (line unknown, sorry)
[ERROR]        called from '/opt/cross/lib/ct-ng-1.9.3/scripts/crosstool-NG.sh' at line # 65 in function 'main'
[ERROR]  Look at '' for more info on this error.
[ERROR]  (elapsed: 23312039:54.47)
[00:00] / make: *** [build] Error 1

```
Error 1 seems like an ambiguous error message, and I'm at a loss as to where to go from here.  Any thoughts?

---

### Post by Elastic_Potential on 2014-04-28
As context (I should have included this earlier), I ran "ct-ng build" as root for the above because, with normal permissions, the command produced this error:
```

[INFO ]  Performing some trivial sanity checks
[INFO ]  Build started 20140428.183722
[INFO ]  Building environment variables
[ERROR]  Destination directory '/opt/cross/x-tools/arm-unknown-linux-gnueabi' is not removable
[00:00] / make: *** [build] Error 1

```
I interpreted the error here as, "you need permissions to manipulate files and folders in your /opt directory" and thought that running it as root might yield something productive.  My apologies for not posting this earlier.

---

### Post by Elastic_Potential on 2014-04-30
As I was using a more recent version of crosstool-ng, I used the version referenced in the article and it worked fine.  I did have to compile it as root/sudo.

---

