---
title: "Cmake does not work Kubuntu 15.04"
date: 2015-05-07
forum: Packaging and Compiling Programs
---

### Post by GregPayne on 2015-05-07
Ever since upgrading to 15.04 i have been unable to use Cmake at all and i have no idea why. 

[COLOR=#000000][FONT=monospace]greg@Payne-MS-7522:~$ cmake[/FONT][/COLOR]
[FONT=monospace]Inconsistency detected by ld.so: dl-version.c: 224: _dl_check_map_versions: Assertion `needed != ((void *)0)' failed![/FONT]
[FONT=monospace]greg@Payne-MS-7522:~$ [/FONT]

[FONT=monospace]This same output comes from any attempt to use any Cmake function leaving me unable to compile anything which requires cmake. [/FONT]

In some cases it also tells me it is unable to find cmake, yet Cmake is installed.

I have tired fully removing cmake and then reinstalling it only to get the same results. 

[FONT=monospace]any ideas will be gratefully received.

Finally resolved by reinstalling libcurl3[/FONT]

---

### Post by GregPayne on 2015-05-22
well i gave up and reinstalled kubuntu and everything worked.  Then the plasma desktop crashed requiring me to delete the .cache folder.   I also installed wine1.7, openshot, simple screen recorder and virtual box. Now once again cmake is borked and simply removing these packages and reinstalling cmake does not help.

---

### Post by oldos2er on 2015-05-23
I would consider filing a bug against cmake.

---

### Post by GregPayne on 2015-05-23
[https://bugs.launchpad.net/ubuntu/+source/cmake/+bug/1458197](https://bugs.launchpad.net/ubuntu/+source/cmake/+bug/1458197)

Filed

---

### Post by GregPayne on 2015-05-25
reinstalling libcurl3 fixes this

---

