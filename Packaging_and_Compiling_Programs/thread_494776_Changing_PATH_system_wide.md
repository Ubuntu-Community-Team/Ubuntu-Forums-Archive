---
title: "Changing PATH system wide"
date: 2007-07-07
forum: Packaging and Compiling Programs
---

### Post by filo_kg on 2007-07-07
I'm packaging [AFNI]("http://afni.nimh.nih.gov/afni/") (a neuroimaging software) and according to developers [guide to system wide installation]("http://afni.nimh.nih.gov/pub/dist/HOWTO//howto/ht00_inst/html/linux_inst_root.shtml") I should copy all binaries (with companion files and libraries) to one catalog and update the PATH.

First, minor, question is which catalog would be best for such software (it is compiled from source so probably not /opt/afni maybe /usr/lib/afni) ?

Second question is how to update PATH system wide during postint in a clean way that would allow to reinstall and completely uninstall this package (is there something like Gentoo's env.d in Ubuntu?)

Thanks in advance.

---

### Post by meatpan on 2007-07-07
> **filo_kg said:**
> 
First, minor, question is which catalog would be best for such software (it is compiled from source so probably not /opt/afni maybe /usr/lib/afni) ?


This ultimately comes down to personal preference.  I prefer to use /opt for manually compiled packages.  In my opinion, grouping all manual builds in a common folder makes dependency checking and application maintenence a bit easier.  This includes the other tasks you mentioned , such as re-installation.   Here is an example of a directory setup I am suggesting:

/opt
___/afni
_______/build  (location of source, configure/make scripts)
_______/default -> (a soft link to main version. this makes user env config a bit easier)
_______/afni-x.x  (installed location for bin, doc, lib, etc...)

---

### Post by po0f on 2007-07-08
filo_kg,

Install it wherever you want and just put a small start-up script or a symlink to the main binary in /usr/loca/bin.  Problem solved.  :)

---

### Post by filo_kg on 2007-07-11
> **po0f said:**
> filo_kg,

Install it wherever you want and just put a small start-up script or a symlink to the main binary in /usr/loca/bin.  Problem solved.  :)
The problem is there are plenty of binaries in this package (which all should reside in same directory according to AFNI developers). Do you recommend making start-up script for each one?

---

### Post by filo_kg on 2007-07-11
> **meatpan said:**
> This ultimately comes down to personal preference.  I prefer to use /opt for manually compiled packages.

Yes, but this package wont be for my personal use only. I would like it to fit with the whole system in the best possible way. Aren't there any Debian/Ubuntu recommendations where to put such things?

---

