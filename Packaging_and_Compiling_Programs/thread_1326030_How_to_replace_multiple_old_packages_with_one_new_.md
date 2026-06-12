---
title: "How to replace multiple old packages with one new one?"
date: 2009-11-14
forum: Packaging and Compiling Programs
---

### Post by ssalley on 2009-11-14
There exists two packages: likewise-open (based on v4.1) and likewise-open5 (based on v5.0).

I want to create the package likewise-open (will be v5.4) and if the system has any older version of likewise-open or likewise-open5,migrate them to the new version.

I have done the work for the likewise-open package, but I'm not sure if there is a way of handling the upgrade from likewise-open5 in an unobtrusive manner.

Note that I'm not asking how to actually convert files/databases/etc used in these packages (I already know how to do that and have written the code for it), but I'm trying to figure out if I can make the maintainer scripts do the right thing with packages of different names.

Also note that 'likewise-open' is the Ubuntu gods' chosen name for the new package.

[And for the clever, I don't suggest installing likewise-open from my PPA]

---

### Post by SevenMachines on 2009-11-15
Assuming your sure likewise-open is definitely the package you want to create based on 5.4 rather than an upgrade of the likewise-open5 packages?
then, if i understand correctly, you want to
* upgrade likewise-open from version 4 to 5.4
* remove likewise-open5 but not break any other packages dependencies on this and instead 'redirect them' to the new likewise-open package

to do this, in debian/control, 
* add likewise-open5 to Conflicts: and Replaces:  (you'll probably want to add other likewise-open5 packages here as well) 
* add likewise-open5 to Provides: so that any external packages dependency on that will be satisfied by your new package (again you probably want to add other likewise-open5 packages here).

obviously the original likewise-open package based on v4 will be removed anyway when it is replaced by your new one.

just to add though, if upgrading the likewise-open5 packages is acceptable then it'll be a lot simpler

---

### Post by ssalley on 2010-01-15
I did get this working and likewise-open is currently in alpha2 of Lucid Lynx.
 
There were enough issues that I had a hard time seeing what was working and what wasn't, so I'll summarize the control file.
 
likewise-open5 had a large number of packages (likewise-open5, likewise-open5-lsass, likewise-open5-libs, ...) but likewise-open (the oldest version and the new version I was/am working on) have only 2 or 3 packages.
 
The new control file mentions each of the likewise-open5 packages and marks that they depend on 'likewise-open'.  These likewise-open5 packages have no files associated with them and are often referred to as 'transitional' or 'dummy' packages in web documentation I found.
 
The likewise-open package is marked as conflicting and replacing each of the likewise-open5 packages (along with version information in case some future likewise-open5 package comes out). The likewise-open package is also marked providing likewise-open and likewise-open5.
 
Even though the likewise-open5 packages don't have files, they do still run the maintainer scripts. After determining the order all maintainer scripts run under a variety of conditions and with what arguments (I used print statements), I was able to properly script an upgrade through all combinations of installs and upgrades [I hope].

---

