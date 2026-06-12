---
title: "scripts for repackaging debian packages"
date: 2008-06-04
forum: Packaging and Compiling Programs
---

### Post by udit99 on 2008-06-04
Hi
Im trying to build an automated python script to generate a repackaged deb and I thought that maybe Im reinventing the wheel here.

What I need to do is to make custom changes to a debian source package and repackage it to make a deb. My script would 

1. copy the contents of the source package and put it into a temporary location 
2. apply all existing patches to source package in temp location.
3. diff this temp source package folder with my customized source package folder
4. Output diff to a patch file that goes into the tmpfolder/debian/patches folder
5. Repackage the whole temp folder into a deb using debuild.


Now this process just seems too obvious and generic enough to not have been made a script out of. So my question is, is there a script\utility that will do this for me ??

---

### Post by ssam on 2008-06-14
have you had a look though [https://wiki.ubuntu.com/PackagingGuide/PatchSystems](https://wiki.ubuntu.com/PackagingGuide/PatchSystems)

simple-patchsys might be close to what you want

---

