---
title: "Extracting and repacking linux binary installer"
date: 2014-11-10
forum: Packaging and Compiling Programs
---

### Post by akimb0 on 2014-11-10
Dear community,

i have a *.run file which installs an application. 
After extracting the files from the run file there are the following files inside:

```
$PATH/lib/some_sort_of_libs_needed
$PATH/install.sh
$PATH/InstallBinary
```

I dumped the files from ```
$PATH/InstallBinary
``` to my /home path by adding the --dump-binary-data flag which brings up some packed *.7z files and their sha1 checksums.
After changing the script inside i would like to repack them again to ```
$PATH/InstallBinary
```
Is there a simple way i could do that?
Maybe im bet a complete wrong horse and this is not possible like i try to do...

---

